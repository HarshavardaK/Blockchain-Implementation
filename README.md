# Blockchain-Implementation
# Blockchain and Its Implementation  
*By Harshavarda Kumarasamy*

---

## Introduction to Blockchain

Blockchain is a decentralized digital ledger technology that records transactions across multiple computers securely and transparently. Unlike traditional databases, blockchain ensures immutability, meaning once data is recorded, it cannot be altered without consensus from the network. This makes blockchain an ideal solution for applications that require transparency, security, and decentralization, such as cryptocurrency, supply chain management, and digital identity verification.

### Core Components of Blockchain

- **Blocks**: Units of data that store transaction information.  
- **Cryptographic Hashing**: Ensures the integrity of data in each block.  
- **Consensus Mechanisms**: Validate transactions and maintain synchronization across the network.  
- **Decentralization**: Removes the need for a central authority by distributing control among participants.

One of the key cryptographic methods used in blockchain technology is the **SHA-256 hashing algorithm**, which ensures data integrity and security.

In this whitepaper, a basic blockchain implementation with 3 users/miners is discussed.

---

## Bitwise Operations (Pre-requisite to SHA-256)

- **RotateRight**: Moves bits of a binary number to the right, wrapping the rightmost bits to the leftmost positions.  
- **ShiftRight**: Moves bits to the right by a specified number of positions, discarding the rightmost bits and filling the left with zeros.  
- **XOR**: Compares corresponding bits of two binary numbers and returns 1 if they differ, else 0.

---

## SHA-256 Functions

### Ch (Choice Function)

- **Purpose**: Selects bits from y where x is 1 and from z where x is 0.  
- **Operations Involved**: Bitwise AND, NOT, and XOR.

### Maj (Majority Function)

- **Purpose**: Determines the majority bit for each position among x, y, and z.  
- **Operations Involved**: Bitwise AND and XOR combinations.

---

## Overview of SHA-256

SHA-256 is a cryptographic hashing algorithm that maps any input to a fixed-length 256-bit hash. It is widely used for data integrity and cryptographic applications.

### Key Steps in SHA-256 Implementation

1. **Message Preprocessing**
   - Convert input to binary (using ASCII).
   - Apply padding to fit 512-bit blocks.
   - Split into 32-bit words.

2. **Message Schedule Construction**
   - Extend the first 16 words to 64 words using bitwise operations.

3. **Compression Function**
   - Initialize with predefined constants.
   - Apply 64 rounds of computation using hash functions and round constants.
   - All arithmetic done modulo 2^32.

4. **Final Hash Computation**
   - Update variables added to initial values to get final hash.

---

## Blockchain Methodology

This section explains the blockchain simulation implemented using Proof of Work (PoW), concurrent mining with threading, and miner rewards.

### Conditions to Mine a Block

- Mining is triggered when pending transactions reach a threshold (e.g., 20 coins).
- PoW requires miners to find a valid hash matching a given difficulty.

### Proof of Work (PoW)

- Uses a hash function with a changing nonce.
- A valid hash must have a specific number of leading zeros.
- The nonce is iterated until the hash meets this condition.

### Threading in Mining

- Each miner runs in its own thread, simulating real-world competition.
- Threads work concurrently to solve the PoW challenge.
- The first valid hash found determines the winning miner.

### Time Library Usage

- Adds unique timestamps to blocks.
- Simulates realistic mining delays.

### Reward Mechanism

- The winning miner receives 5 coins as an incentive.

---

## Blockchain System Overview

A simulation of a blockchain environment with multiple miners competing to validate transactions using SHA-256 and Proof of Work.

### Core Components

1. **Miner Class**
   - Each miner has a name, wallet, and thread lock for safety.
   - The mining method solves the PoW by hashing block data and a nonce.
   - Includes a method to display wallet balance.

2. **Block Class**
   - Contains index, list of transactions, previous hash, and the resulting hash.
   - Records mining results from different miners.

3. **Blockchain Class**
   - Maintains the full blockchain.
   - Manages transactions, mining process, and consensus.

#### Key Methods

- **initialize_miners**: Sets up the list of participating miners.
- **add_transaction**: Validates and queues a transaction; checks balances and triggers mining.
- **mine_block**: Initiates mining; spawns threads for each miner; adds mined block to chain.
- **select_winner**: Chooses the miner with the lowest hash and rewards them.

---

## Example Workflow

1. **Add Transactions**  
   - Users initiate transactions that are stored in a pending list.

2. **Mine a Block**  
   - Once the threshold is met, miners start mining to add a new block.

3. **Check Wallet Balances**  
   - Miners’ rewards can be observed post-mining.

---

## Conclusion

This blockchain implementation is a simplified yet comprehensive simulation of real-world blockchain systems. It incorporates:

- Cryptographic foundations like SHA-256  
- Proof of Work mining  
- Multithreaded mining competition  
- Miner incentives for validation  

By combining these elements, the simulation captures the essence of decentralized, secure, and consensus-driven systems. It serves as an accessible and educational model for blockchain enthusiasts and learners.
