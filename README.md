# Circuit Palladium Labs - Automated Staking Script

This script automates the staking process on Circuit Palladium Labs by interacting with a smart contract. The script sends multiple transactions to the `provideToSP()` method, allowing you to stake random amounts of assets to the smart contract.

## Website:
[https://circuit.palladiumlabs.org/](https://circuit.palladiumlabs.org/)

---

## Steps A: Manual Process

1. **Get Testnet BTC**
   - First, you need to get testnet BTC. Follow the instructions here: [How to Use the Botanix EVM](https://docs.botanixlabs.xyz/botanix-labs/how-to-use-the-botanix-evm/step-2-get-test-funds#option-3-mutinynet-faucet--botanix-bridge)

2. **Mint WBTC**
   - Go to the WBTC minting page on the Circuit website: [Mint WBTC](https://circuit.palladiumlabs.org/trove)

3. **Select WBTC Trove**
   - Once on the page, select your WBTC Trove and click the "GET WBTC" button.

4. **Deposit WBTC & Borrow PUSD**
   - Click on "Details" and proceed to deposit WBTC and borrow PUSD. Ensure that your loan value remains within the safe range.

5. **Stake WBTC**
   - Go to the stake menu on the website: [Stake WBTC](https://circuit.palladiumlabs.org/stake)
   - Verify that you can stake without any issues.

6. **Proceed to Step B for Automatic Staking**
   - If everything looks good, move to Step B to automate the staking process via a smart contract.

---

## Steps B: Automate Staking via Smart Contract

### 1. **Install Dependencies**
Open your terminal and install the required node modules:

```
npm install
```

### 2. **Configure .env File**
Create a .env file in your project root and add the following environment variables:

```
RPC_URL=your_rpc_url
PRIVATE_KEY=your_private_key
PROXY_ADDRESS=your_proxy_contract_address
```

* Replace your_rpc_url with https://node.botanixlabs.dev
* Replace your_private_key with your wallet's private key.
* Replace your_proxy_contract_address with 0x56984Cc217B0a72DE3f641AF387EdD21164BbE78

### 3. **Run the Script**
To stake, run the following command:
```
node provideToSP.js
```

If you want to withdraw, run:
```
node withdrawFromSP.js
```

### 4. **Script Overview**
* Random Amount Generation: The script generates a random staking amount between 0.5 and 1 USD (you can adjust the range in the script). This amount is sent to the smart contract.
* Transaction Process: The script uses the ethers.js library to interact with the Ethereum network. It sends a transaction to the provideToSP() function on the specified proxy contract address.
* Gas Price Calculation: The script automatically retrieves the current gas price and sends the transaction with the appropriate gas settings.
* Multiple Transactions: The script allows for multiple staking transactions to be sent. You can specify the maximum number of transactions (maxTransaction) in the script, and it will wait for a random amount of time (between 5 and 15 seconds) before sending the next transaction.

### 5. **Modify the Script (Optional)**
You can modify the script to adjust the following parameters:

* randomAmount(): Adjust the minimum, maximum, and decimal places for the amount to be staked.
* maxTransaction: Set the number of transactions to be sent.
* delay(): Adjust the waiting time (in seconds) between each transaction.

Notes:
* This script currently supports only staking functionality.
* Each successful stake or unstake action earns 50 points.
* Ensure you have sufficient testnet BTC to interact with the smart contract.

Happy staking!
