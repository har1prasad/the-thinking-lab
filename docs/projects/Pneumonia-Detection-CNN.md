# Pneumonia Detection from Chest X-Rays [CNN]

---

## Live Links & Repository

* **GitHub Repository:** [Pneumonia-Detection-CNN](https://github.com/har1prasad/Pneumonia-Detection-CNN)
* **Live Streamlit App:** [pneumonia-detection-cnn-har1prasad.streamlit.app](https://pneumonia-detection-cnn-har1prasad.streamlit.app/)

![Pneumonia-Detection-CNN](./demo/CNN.png)

---

I used to think that the golden rule of computer vision was to always use a pre-trained model like ResNet, but in medical imaging, using a network trained on pictures of cats and dogs actually introduces irrelevant spatial biases that can lead to dangerous diagnostic errors.

Let's look at the core issue.

When we build a model to detect **pneumonia** from chest X-rays, the stakes are completely asymmetrical. If a model predicts that a healthy patient has pneumonia (a **false positive**), it leads to a follow-up test and some temporary stress. But if the model misses an actual case of pneumonia (a **false negative**), a patient goes untreated and their life is put at risk.

So.

Our primary goal isn't just high overall accuracy. We must maximize **recall**—also known as **sensitivity**—which is the percentage of actual sick patients that our model correctly identifies. In a clinical screening scenario, we want this number as close to 100% as possible. 

Here's the first hurdle: the **class imbalance**.

In the benchmark chest X-ray dataset, we have roughly 74% pneumonia scans and only 26% normal scans. If we train a model on this directly, it quickly learns a lazy shortcut: guess "pneumonia" almost every time and it will get 74% accuracy without actually learning how to read a radiograph.

To fix this, we use dynamic **class weighting**.

We assign a higher penalty to the model when it misclassifies the minority class (Normal). Specifically, we calculate the weights like this:

$$w_c = \frac{N_{\text{total}}}{N_{\text{classes}} \times N_c}$$

For our dataset, this gives a weight of 1.88 for Normal scans and 0.68 for Pneumonia scans. Now, the model gets penalized nearly three times as much for making a mistake on a healthy lung scan, forcing it to treat both classes with equal clinical importance.

Let's walk through the architecture.

Instead of a massive pre-trained model, we design a custom **convolutional neural network (CNN)** from scratch. This keeps the model size under 5 MB with just 423,000 parameters, meaning we can run it on a cheap CPU in under 60 milliseconds.

```python
def build_pneumonia_cnn(input_shape=(224, 224, 3)):
    inputs = layers.Input(shape=input_shape, name="input_image")
    x = layers.Rescaling(scale=1.0 / 255.0, name="rescaling")(inputs)

    x = layers.Conv2D(32, kernel_size=(3, 3), padding="same", name="conv2d_1")(x)
    x = layers.BatchNormalization(name="bn_1")(x)
    x = layers.Activation("relu", name="relu_1")(x)
    x = layers.MaxPooling2D(pool_size=(2, 2), name="pool_1")(x)
    x = layers.Dropout(0.2, name="dropout_1")(x)

    x = layers.GlobalAveragePooling2D(name="global_avg_pool")(x)
    x = layers.Dense(128, name="dense_fc")(x)
    x = layers.BatchNormalization(name="bn_fc")(x)
    x = layers.Activation("relu", name="relu_fc")(x)
    x = layers.Dropout(0.5, name="dropout_fc")(x)

    outputs = layers.Dense(1, activation="sigmoid", name="output_classification")(x)
    return Model(inputs=inputs, outputs=outputs, name="Pneumonia_Custom_CNN")
```

Notice what's happening here.

First, we rescale the pixels to a 0–1 range. Then, we pass the image through convolutional blocks. Each block extracts features like lung boundaries and fluid opacities. 

After each convolution, we apply **batch normalization** to stabilize training and accelerate convergence. Then we use **max pooling** to shrink the spatial dimensions, and **dropout** to randomly disable neurons so the network doesn't overfit to specific training images.

Look at the end of the feature extractor: we use **global average pooling (GAP)** instead of flattening the tensor into a massive 1D vector. Flattening creates millions of connections and leads to severe overfitting. GAP simply averages each feature map, compressing our data from 3D to 1D while keeping the parameter count low.

To help the model generalize even further, we use **data augmentation**.

But we have to be careful. In natural images, you can flip pictures of cats upside down and they are still cats. In radiology, patients don't get scanned upside down. So we disable vertical flips. We only use safe, non-destructive augmentations: horizontal flips, slight rotations, zoom, and translations.

When we evaluate the final model, we look at the **confusion matrix** on our isolated test set.

Out of 624 test images, the model achieves 90.38% overall accuracy. But more importantly, it achieves a recall of 96.84%. It correctly identifies 378 pneumonia cases and only misses 12.

---

!!! tip "The one-line takeaway"
    In clinical machine learning, maximizing sensitivity through custom architectures and class weighting is the difference between a helpful screening tool and a dangerous diagnostic liability.
