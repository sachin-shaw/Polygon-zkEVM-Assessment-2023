# Zardkat 🐱

Welcome to Zardkat, a powerful template for generating zero-knowledge circuits, proofs, and Solidity verifiers using the hardhat-circom framework. With Zardkat, you can build privacy-preserving applications by leveraging zero-knowledge proofs to verify computations without revealing sensitive data. Let's embark on a journey to explore the capabilities of Zardkat and get started with the following steps:

## Quick Start

To begin, let's dive into the essential steps to compile a circuit, generate a proof, deploy a verifier contract, and verify the proof. This will give you a taste of what Zardkat can accomplish!

### Installation

First, clone the Zardkat repository to your local machine:

```bash
https://github.com/sachin-shaw/Polygon-zkEVM-Assessment-2023.git
```

Next, install the project dependencies:

```bash
npm install
```

### Circuit Implementation

Now, let's take a closer look at the core of Zardkat - the circuits themselves. Open the `MyCircuit/circuit.circom` file, and you'll find an intriguing circuit template that checks whether the output signal `q` is the multiplication of the input signals `a` and `b`. You have the freedom to customize this circuit according to your specific needs. Feel free to explore the circuit logic and constraints to adapt it for your use case.

### In this circuit implementation:

1. The circuit template MyCircuit checks whether the output signal q is the multiplication of input signals a and b.
2. The AND, NOT, and OR gates are defined as separate templates to perform the respective logical operations.
3. The AND gate multiplies the input signals a and b.
4. The NOT gate subtracts twice the input signal in from 1 to perform the logical negation.
5. The OR gate adds the input signals a and b and subtracts their product to perform the logical OR operation.
6. The main component represents the entire circuit and is set as MyCircuit.
7. This circuit can be used as a template to build more complex circuits and perform zero-knowledge proofs.

### Compile the Circuit

With the circuit defined, it's time to compile it into its intermediary representations. Execute the following command:

```bash
npx hardhat circom
```

This command triggers the compilation process and generates the necessary files, including the `MyCircuitVerifier.sol` contract.

### Generate Proof and Deploy

Now, let's generate a proof, deploy the verifier contract, and verify the proof. Run the following command:

```bash
npx hardhat run scripts/deploy.ts --network goerli
```

This script orchestrates multiple tasks:

1. Deploys the MyCircuitVerifier.sol contract, which serves as the verifier for the proof.
2. Generates a proof using the circuit's intermediary files by invoking the `generateProof()` function.
3. Generates calldata required for the verification process by using the `generateCallData()` function.
4. Calls the `verifyProof()` method on the deployed verifier contract with the calldata.

Congratulations! You have successfully compiled a zero-knowledge proof, deployed a verifier contract, and verified the proof using Zardkat.

## Configuration

Let's explore the configuration options available with Zardkat to customize your zero-knowledge circuits and deployment settings.

### Directory Structure

Zardkat follows a well-organized directory structure that promotes clarity and modularity. Here's an overview:

```
├── circuits
│   ├── MyCircuit
│   │   ├── circuit.circom
│   │   ├── input.json
│   │   └── out
│   │       ├── circuit.wasm
│   │       ├── MyCircuit.r1cs
│   │       ├── MyCircuit.vkey
│   │       └── MyCircuit.zkey
│   ├── new-circuit
│   └── powersOfTau28_hez_final_12.ptau
└── contracts
    └── MyCircuitVerifier.sol
```

Each circuit resides in its own directory within the `circuits` folder. The `out` directory stores the compiled outputs, keys, and proofs. Additionally, the `powersOfTau28_hez_final_12.ptau` file, obtained from the Polygon Hermez ceremony, eliminates the need for a new ceremony.

## Authors

Sachin kumar

## License

This project is licensed under the MIT License. See the LICENSE file for details.
