# Web3-Script-for-Checking-Token-Balance
Web3 script that allows you to check the balance of a specific token in an Ethereum wallet
const Web3 = require('web3');
const tokenABI = require('token-abi');

// Connect to the Ethereum network
const web3 = new Web3('https://mainnet.infura.io/v3/YOUR_INFURA_PROJECT_ID');

// Contract address for the token
const contractAddress = '0xYOUR_TOKEN_CONTRACT_ADDRESS';

// Wallet address to check the token balance
const walletAddress = '0xYOUR_WALLET_ADDRESS';

// Get token balance
async function getTokenBalance() {
  try {
    const contract = new web3.eth.Contract(tokenABI, contractAddress);
    const balance = await contract.methods.balanceOf(walletAddress).call();
    return balance;
  } catch (error) {
    console.error('Failed to retrieve token balance:', error);
    return null;
  }
}

// Usage example
(async () => {
  const balance = await getTokenBalance();
  console.log(`Token balance: ${balance}`);
})();
