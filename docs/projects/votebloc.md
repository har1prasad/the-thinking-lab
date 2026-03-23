# VoteBloc 🗳️

A blockchain-based voting platform built as our final year BCA project — combining a web interface, an Android app, and a python backend integrating blockchain to conduct secure, tamper-proof elections.

**Type:** Academic Group Project (Team of 4) | BCA Final Year, 2024  
**My Role:** Backend (Python/Django) & Documentation

---

## What this project is

VoteBloc was the most complex system I had been part of building.

Not complex because of any single feature — but because it had real moving parts that needed to work together: a Django backend, a Flutter Android app, a web frontend, a MySQL database, and a blockchain layer for recording votes.

Four people. Four different areas. One system that had to function as a whole.

My job was the backend and the documentation. I wrote the Django views, handled the database interactions, and was responsible for making sure the system's logic was correctly described and structured in the project report.

---

## What it does

VoteBloc supports four roles — Admin, Subadmin, Election Coordinator, and User — each with different levels of access and responsibility.

- **Admin** manages subadmins, verifies political parties and nominees, schedules elections
- **Subadmin** manages election coordinators and adds political parties
- **Election Coordinator** manages and verifies users, views results
- **User** registers, nominates, votes, and views results

Votes are recorded on a local blockchain using Web3.py and Ganache, making each vote tamper-proof and traceable by block number.

---

## Tech stack

- **Backend:** Python, Django
- **Frontend:** HTML, CSS
- **Android:** Flutter (Dart)
- **Database:** MySQL
- **Blockchain:** Solidity, Web3.py, Ganache
- **IDE:** PyCharm, Android Studio

---

## System design

The system was designed around four modules with clearly separated responsibilities. This was one of the first times I worked with a multi-role access system, where what you see and what you can do depends entirely on who you are.

The database had nine tables with proper normalization up to 3NF, covering login, users, subadmins, election coordinators, parties, nominees, complaints, elections, and results.

---

## What I actually learned

**Backend work taught me that logic lives in the middle.**

The frontend sends a request. The database stores the result. But everything that decides *whether* something should happen — validation, role checks, business rules — lives in the backend. Writing those views in Django made that responsibility feel real for the first time.

**Documentation taught me that understanding and explaining are different skills.**

I wrote the full software requirement specification, system design sections, and testing documentation. To write them clearly, I had to understand every part of the system — including the blockchain layer, which I didn't build.

Understanding a complex component through its integration points — what it receives, what it returns, what breaks when it fails — is a different kind of understanding than building it. It taught me to ask better questions and read code more carefully.

**The blockchain integration was the hardest part to understand.**

Our teammate handled the Solidity contract and Web3.py integration. My job was to make the Django backend call it correctly and handle what came back. That boundary — where Python hands off to a blockchain and waits for a response — required me to understand enough about how the contract worked without having written it myself.

That's a skill I didn't expect to develop from a college project.

---

## What I'd do differently now

The role-based access was implemented through session checks in each view — which works, but isn't clean. A proper permission system or middleware would handle this more reliably and be easier to maintain.

The blockchain layer ran on a local Ganache instance, which means it was only ever tested in a controlled environment. Real deployment would require a proper network — testnet or mainnet — which is a significantly different problem.

If I rebuilt this today I'd also push for better separation between the Android and web backends. Right now they share the same Django endpoints, which worked for a college project but would become a maintenance problem at scale.

---

## Project report

This was a formally submitted academic project. The full report covers system analysis, ER diagrams, use case diagrams, data flow diagrams, database design, testing methodology, and future enhancements.

---
