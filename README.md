# DistributedBanking
A Simulation Framework for Distributed Banking Systems Using Java RMI and Socket-Oriented Client Branch Architecture
This project presents the design and simulation of a heterogeneous distributed banking system operating over a multi-tiered client–server model. The architecture leverages Java RMI to establish inter-branch interoperability and enforce consistent state synchronization across distributed nodes, while socket-level client communication introduces remote transactional accessibility at the network layer.

At the system’s core lies a MySQL-backed persistence layer, functioning as the centralized data repository for transaction logs, account states, and operational metadata. A central orchestration server mediates the transactional flow, invoking atomic operations on the persistence layer while concurrently exposing a branch service abstraction to distributed branch modules. Each branch module operates as a service daemon, bound to the central server’s RMI interface, and encapsulates localized banking operations while delegating global state reconciliation tasks upstream.

Client nodes, on the other hand, dynamically bind to remote branch IP endpoints and execute socket-based invocation stubs, thereby simulating real-time inter-branch connectivity in a distributed environment without cryptographic guarantees. The overall model thus emphasizes inter-process communication, concurrency control, and distributed consistency enforcement, demonstrating how a banking system would function in a non-monolithic, decentralized deployment scenario.


System Architecture

The system is designed using a layered, distributed architecture:

Database (Core Layer):

Acts as the backbone of the application.

Stores all customer, transaction, and banking data.

Central Server:

Contains the main methods that handle the business logic and database interactions.

Manages communication between branches and ensures system consistency.

Branch Modules (Distributed Components):

Each branch runs as an RMI (Remote Method Invocation) server module.

Distributed across different physical or logical branches.

Interact with the central server to process banking operations.

Client Application:

Connects to a specified branch’s IP using Socket programming.

Provides the end-user interface to perform banking transactions remotely.

How to Run the Application
1. Database Setup

Install MySQL.

Run the provided DBinit.sql script to initialize the database and create necessary tables.

2. Start the Central Server

Open a terminal.

Run the Central Server program.

This connects to the initialized database.

3. Start a Branch Module

Open another terminal.

Run any branch module code.

The branch connects to the central server via RMI.

4. Configure the Client

Find your device’s network IP using the command:

ipconfig


Replace the Host name in the client code with this IP.

Run the client code from the same device or any other device on the network.
