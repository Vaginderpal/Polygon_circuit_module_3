## Circuit Deployment on Polygon
This repository contains the imlementation of the given circuit diagram using circom and also demonstrates how to deploy it on Polygon Mumbai Testnet.

## Description
This project implements a logical gate circuit using the circom programming language. The circuit implements the following truth table:

![image](https://github.com/Vaginderpal/Polygon_circuit_module_3/assets/137271458/fe2ebb38-ada0-45e4-afff-2c6b6b073d85)

The goal of the project is to prove that you know the inputs A=0 and B=1 that yield a 0 output.

## Usage
To generate and verify zero-knowledge proofs for your circuits, follow these steps:

Define your circuit in the circuits folder.

Create an input.JSON file in the Proof folder, specifying the inputs to your circuit.

Run the genProof.js script:

node genProof.js

This will compile our circuit, calculate the witness, and generate the proof and public signals.

## Compile
1. npm i
2. npx hardhat circom :- This will generate the out file with circuit intermediaries and geneate the MultiplierVerifier.sol contract.

## Deploy
npx hardhat run scripts/deploy.ts This script does 4 things

1. Deploys the MultiplierVerifier.sol contract.
2. Generates a proof from circuit intermediaries with generateProof().
3. Generates calldata with generateCallData().
4. Calls verifyProof() on the verifier contract with calldata.   

## Steps for Deployment to Mumbai Testnet 
1. Create a file named .env in the root directory of your project.
2. add you account address private key which is on Polygon mumbai testnet and has test matics.
3. inside your hardhat.config.ts file add the following  networks:{   mumbai: { url :`https://polygon-mumbai.g.alchemy.com/v2/xYD2bZsKa0S4r-a6-UcCkGOPdyCRhZXe` ,   accounts: [process.env.POLYGONMUMBAIPRIVATEKEY]  } }, NOTE : Replace YOUR_PRIVATE_KEY_HERE with the private key of your Ethereum account on the Polygon Mumbai Testnet, which has test MATIC tokens.
4. import dotenv/config.
5. Now run the following command in your Terminal npx hardhat run scripts/deploy.ts --network mumbai This will compile the solidity file.

# Author
Vaginderpal Singh Brar
