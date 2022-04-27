# FRED-Swap
Overview of FRED Swap, a Stellar to BSC bridge app


**Introduction**

FRED Swap is a bridge to swap between FRED tokens on the Stellar network and bFREDX tokens on the BSC (Binance smart chain) network, and vice versa. 
Tokens are swapped in a ratio of 1:1, with a pool fee of 0.5XLM to cover BSC gas fees (when swapping from FRED to bFREDX only).

**Rationale for method used**

Due to the current lack of smart contracts on the Stellar blockchain, rather than minting new wrapped tokens for the corresponding asset, a swap pool is used containing a number of each asset available to be swapped. 

The idea is that a project can create the assets on each blockchain and use the bridge to swap 1-1 between assets and blockchains. 

This could be considered an interim solution until smart contracts for the Stellar blockchain are developed and mature.

**Benefits**

A Stellar based project bridging to and from other blockchains can create greater awareness of their project, bring new users to the Stellar ecosystem and provide access to further DeFi offerings of other blockchains.

In addition, supply and demand is adjusted as assets are bridged to and from the various blockchains. This is only true when a project has a maximum supply across all chains (see FRED Energy example).

FRED Energy set out this vision in January 2021 with the initial idea to bridge to Ethereum, however, due to rising gas costs, BSC was chosen as a lower cost alternative. Our bridge can be configured to the Ethereum blockchain, BSC and with a little more development, many other blockchains.

**Example of our supply;**

FRED Energy has a combined maximum supply of 808 Million tokens across all blockchains. 

404 Million tokens are allocated to the Stellar Blockchain (FRED) (initially 808M tokens were created with 404M later being burned)

404 Million tokens are allocated to the BSC and ETH blockchains, initially 808M ETH tokens were created with 404M later being burned. The current total is 100M bridged to BSC and 304M on Ethereum.

The swap pool holds 10M of FRED (Stellar) and 10M of bFREDx (BSC) exclusively for the bridge tool.

Although now outdated, our YouTube explainer from 2021 https://www.youtube.com/watch?v=eY3hkwfTk8A gives the idea of what we set out to do and why.

**How It Works**

The swap process begins with inputting the amount of tokens you want to swap, which displays the corresponding amount of tokens to receive. When this happens, two checks occur in real time: 
1. The apps checks if the swap pool has enough tokens for the swap. 
2. The app checks if the connected wallet has enough tokens for the swap (if connected to your wallet, otherwise this check would be done whenever you connect to your wallet). If any of these checks fail, they are displayed to the user and the swap process can not continue until input values are adjusted to pass both checks. The receiving address is also a required input (BSC or Stellar address)
3. If all is good from step 1, swapping starts and the first action is to confirm that the receiving address exists and was correctly inputted. If this check fails, it stops the swap process, (to avoid a failed transaction from the server to the user).
When the check in step 2 is complete (and successful), the connected wallet (Rabet or MetaMask), prompts the user to sign and confirm the transaction.
4. Next, the wallet begins the process of sending the tokens to the swap pool and the server monitors the process, awaiting a successful transfer of tokens from the user's wallet to the swap pool.
5. Once the transfer from step 4 is successful, the server instantly sends the correct amount of tokens to the receiving address (provided in step 1).
6. When both transfers are finished (and successful), a "swap success" message is displayed to the user and this ends the swap process.

**Technologies Used:**

FRED Swap was largely built with React on the front-end and Nodejs for the back-end of the application. Other notable technologies used are;

Rabet (extension) - for integrating a Stellar wallet connection into the app.

MetaMask (extension) - for integrating a BSC wallet connection into the app.

Express - to set up the server for the application.

Socket.io - for fast, realtime communication between the front-end and the server.

MongoDB - the database of choice for the application.

**Security**

Without giving too much away at this point, secret keys for the pool accounts are not stored on the server. The app is hosted on a secure server and several security measures are put in place to prevent cyber attacks and further secure the application.

Video https://www.youtube.com/watch?v=u7SCH3r7CJw&list=PLT42cs8i5DsG5oPuJKCo53Rp3OkCF66lb&index=1

FRED Swap can be found at https://swap.fredenergy.org

