# Giveback-dapp

## Overview
Giveback-dapp is a decentralized fundraising application built using the Hedera Hashgraph network. It enables users to create fundraising campaigns, donate using HBAR, and track donations with real-time transparency and security through the blockchain.

## Technology Stack
- **Frontend**: React.js
- **Backend**: Node.js, Express.js
- **Blockchain**: Hedera Hashgraph (Smart Contracts and HBAR cryptocurrency)

---

## Steps to Deploy and Run the Project

- ### Step 1: Install Dependencies

   1. Navigate to the `web3` directory and install the necessary dependencies:
      ```bash
      cd web3
      npm install
      ```
   2. Navigate to the `backend` and `client` directories and install their respective dependencies:
      ```bash
      cd ../backend
      npm install
      cd ../client
      npm install
      ```
- ### Step 2: Set Up Hardhat for Hedera
   There is an `.env.example` file in the `web3` folder which should look like this, Update it with Hedera Testnet ECDSA hex encoded private key which you created in hedera portal:
   ```=
   # For Hedera Testnet
   # The operator private keys start with "0x" and are in hexadecimal format
   # Your testnet account ECDSA hex-encoded private key (Ex: 0xb46751179bc8aa9e129d34463e46cd...)
   TESTNET_OPERATOR_PRIVATE_KEY=0xb46751179bc8aa9e129d34463e46cd924055112eb30b31637b5081b56ad96129
   # Your testnet JSON-RPC Relay endpoint URL (ex: 'https://testnet.hashio.io/api')
   TESTNET_ENDPOINT='https://testnet.hashio.io/api'

   ```
   Save and rename the file as just `.env`
- ### Step 3: Deploy the Contract
   Go into web3 directory
  ```bash
   cd ../web3
   ```
   The deployment script is already present. You just need to run the following command to deploy the contract to the Hedera Testnet:
   ```bash
   npx hardhat run scripts/deployContract.js --network hedera
   ```

- ### Step 4: Add Contract Address to Backend

   1. Open the `index.js` file in the **backend** directory.
   2. Replace the placeholder contract address with the actual contract address you obtained after deploying the contract:
   ```javascript
   const contractAddress = 'Your_Contract_Address';  // Replace with the actual contract address
   ```

- ### Step 5: Locate the ABI and Bytecode

   After deploying the contract, you can find the **ABI** and **Bytecode** in the following locations:
   
   - **ABI**: Navigate to the `artifacts/contracts/CrowdFunding.json` file. The ABI (Application Binary Interface) can be found under the `abi` section of the JSON file.
   
   - **Bytecode**: In the same `CrowdFunding.json` file, you can find the **bytecode** under the `bytecode` section.
   
   You will need both the **ABI** and the **contract address** to integrate with your backend and frontend.

- ### Step 6: Copy ABI to Backend

   1. Navigate to the `artifacts/contracts/CrowdFunding.json` file in the `web3` folder.
   2. Copy the **ABI** section from this JSON file.
   3. Create a new file in the **backend** directory called `abi.js`.
   4. Paste the copied **ABI** into this `abi.js` file.

   You can refer to a sample `abi.js` file already available in the repository for guidance on how to format and structure this file.
- ### Step 7: Run the Backend

   1. Once you've added the ABI and updated the contract address in `index.js`, you can now run the backend server.
   2. Navigate to the **backend** directory:
   ```bash
   cd backend
   npm run dev
   ```
   For the following steps, leave this terminal running and use a new terminal
- ### Step 8: Add ABI and Bytecode in the Frontend (Client Directory)

   1. Navigate to the `client/src/hedera/contracts/` folder inside the **client** directory.
   2. Replace the contents of `abi.js` with the **ABI** that you copied from the `artifacts/contracts/CrowdFunding.json` file in the `web3` folder.
   3. Similarly, replace the contents of `bytecode.js` with the **bytecode** from the same `CrowdFunding.json` file.
   
   These files in the **client** directory are crucial for interacting with the deployed contract on the frontend. Ensure that both the ABI and Bytecode are updated correctly for the frontend to communicate properly with the smart contract.

- ### Step 9: Add Contract Address in the Frontend (Client/src Directory)

   1. Open the `constants.js` file located in the `client/src/` directory.
   2. Update the `contractAddress` value with the actual contract address obtained during deployment:
   ```javascript
   const APP_CONSTANTS = {
       backendURL: "http://localhost:3000",
       contractAddress: "Your_Contract_Address"  // Replace with your actual contract address
   };

   export default APP_CONSTANTS;
   ```

- ### Step 10: Run the Frontend
   1. In the newly opened terminal, after updating the contract address and ABI, you can now run the frontend.
   2. Navigate to the **client** directory:
   ```bash
   cd client
   npm run dev
   ```
   3. Open the localhost link in browser and connect to your wallet.





   
