# Snippet

```
     <form name="gaswarriorform">
          <select class="numPick" name="numberPick" id="numberPick" form="gaswarriorform">
          <option value="1">1 Gas Warrior</option>
           <option value="2">2 Gas Warriors</option>
          <option value="3">3 Gas Warriors</option>
          <option value="4">4 Gas Warriors</option>
            <option value="5">5 Gas Warriors</option>
            <option value="6">6 Gas Warriors</option>
            <option value="7">7 Gas Warriors</option>
            <option value="8">8 Gas Warriors</option>
            <option value="9">9 Gas Warriors</option>
            <option value="10">10 Gas Warriors</option>
            <option value="11">11 Gas Warriors</option>
            <option value="12">12 Gas Warriors</option>
            <option value="13">13 Gas Warriors</option>
            <option value="14">14 Gas Warriors</option>
            <option value="15">15 Gas Warriors</option>
          </select>
        </form>
    <br><br>
    <div id="initial">
      <button class="web3btn" id="btn-connect" style="font-size: 20px; padding: 20px; margin: 5px; width: 125px; color: #fff; background-color: #6fb3ab; border-color: #6fb3ab;">Connect Wallet</button>
    </div>
    <div class="web3btn" id="mint" style="display: none">
      <button id="btn-mint" style="font-size: 20px; padding: 20px; margin: 5px; width: 125px; color: #fff; background-color: #6fb3ab; border-color: #6fb3ab;">Mint</button>
    </div>
    <!-- web3 and web3modal packages -->
    <script src="https://ajax.googleapis.com/ajax/libs/jquery/3.6.0/jquery.min.js"></script>
    <script type="text/javascript" src="https://unpkg.com/web3@1.2.11/dist/web3.min.js"></script>
    <script type="text/javascript" src="https://unpkg.com/web3modal@1.9.0/dist/index.js"></script>
    <script type="text/javascript" src="https://unpkg.com/@walletconnect/web3-provider@1.2.1/dist/umd/index.min.js"></script>
    <!-- web3 functionality code -->
    <script type="module">
    const CONTRACT_ABI = [ { "inputs": [], "stateMutability": "nonpayable", "type": "constructor" }, { "anonymous": false, "inputs": [ { "indexed": true, "internalType": "address", "name": "owner", "type": "address" }, { "indexed": true, "internalType": "address", "name": "approved", "type": "address" }, { "indexed": true, "internalType": "uint256", "name": "tokenId", "type": "uint256" } ], "name": "Approval", "type": "event" }, { "anonymous": false, "inputs": [ { "indexed": true, "internalType": "address", "name": "owner", "type": "address" }, { "indexed": true, "internalType": "address", "name": "operator", "type": "address" }, { "indexed": false, "internalType": "bool", "name": "approved", "type": "bool" } ], "name": "ApprovalForAll", "type": "event" }, { "anonymous": false, "inputs": [ { "indexed": false, "internalType": "address", "name": "to", "type": "address" }, { "indexed": false, "internalType": "uint256", "name": "id", "type": "uint256" }, { "indexed": false, "internalType": "string", "name": "uri", "type": "string" } ], "name": "Minted", "type": "event" }, { "anonymous": false, "inputs": [ { "indexed": true, "internalType": "address", "name": "previousOwner", "type": "address" }, { "indexed": true, "internalType": "address", "name": "newOwner", "type": "address" } ], "name": "OwnershipTransferred", "type": "event" }, { "anonymous": false, "inputs": [ { "indexed": false, "internalType": "uint256", "name": "newPrice", "type": "uint256" } ], "name": "PriceUpdated", "type": "event" }, { "anonymous": false, "inputs": [ { "indexed": true, "internalType": "address", "name": "from", "type": "address" }, { "indexed": true, "internalType": "address", "name": "to", "type": "address" }, { "indexed": true, "internalType": "uint256", "name": "tokenId", "type": "uint256" } ], "name": "Transfer", "type": "event" }, { "anonymous": false, "inputs": [ { "indexed": false, "internalType": "address", "name": "newAddress", "type": "address" } ], "name": "UpdatedDAOAddress", "type": "event" }, { "inputs": [], "name": "DAOaddressMultisig", "outputs": [ { "internalType": "address", "name": "", "type": "address" } ], "stateMutability": "view", "type": "function" }, { "inputs": [ { "internalType": "address", "name": "_daoAddress", "type": "address" } ], "name": "DAOupdateDAOaddress", "outputs": [], "stateMutability": "nonpayable", "type": "function" }, { "inputs": [], "name": "OwnerMoveFundsToDAO", "outputs": [], "stateMutability": "nonpayable", "type": "function" }, { "inputs": [ { "internalType": "address", "name": "to", "type": "address" }, { "internalType": "uint256", "name": "tokenId", "type": "uint256" } ], "name": "approve", "outputs": [], "stateMutability": "nonpayable", "type": "function" }, { "inputs": [ { "internalType": "address", "name": "owner", "type": "address" } ], "name": "balanceOf", "outputs": [ { "internalType": "uint256", "name": "", "type": "uint256" } ], "stateMutability": "view", "type": "function" }, { "inputs": [], "name": "baseUri", "outputs": [ { "internalType": "string", "name": "", "type": "string" } ], "stateMutability": "view", "type": "function" }, { "inputs": [ { "internalType": "uint256", "name": "numberOfMints", "type": "uint256" } ], "name": "earlyMint", "outputs": [ { "internalType": "uint256", "name": "", "type": "uint256" } ], "stateMutability": "payable", "type": "function" }, { "inputs": [], "name": "fee", "outputs": [ { "internalType": "uint256", "name": "", "type": "uint256" } ], "stateMutability": "view", "type": "function" }, { "inputs": [ { "internalType": "uint256", "name": "tokenId", "type": "uint256" } ], "name": "getApproved", "outputs": [ { "internalType": "address", "name": "", "type": "address" } ], "stateMutability": "view", "type": "function" }, { "inputs": [], "name": "getFee", "outputs": [ { "internalType": "uint256", "name": "", "type": "uint256" } ], "stateMutability": "view", "type": "function" }, { "inputs": [], "name": "hasBeenRevealed", "outputs": [ { "internalType": "bool", "name": "", "type": "bool" } ], "stateMutability": "view", "type": "function" }, { "inputs": [ { "internalType": "address", "name": "owner", "type": "address" }, { "internalType": "address", "name": "operator", "type": "address" } ], "name": "isApprovedForAll", "outputs": [ { "internalType": "bool", "name": "", "type": "bool" } ], "stateMutability": "view", "type": "function" }, { "inputs": [], "name": "maximumMintable", "outputs": [ { "internalType": "uint256", "name": "", "type": "uint256" } ], "stateMutability": "view", "type": "function" }, { "inputs": [ { "internalType": "uint256", "name": "numberOfMints", "type": "uint256" } ], "name": "mint", "outputs": [ { "internalType": "uint256", "name": "", "type": "uint256" } ], "stateMutability": "payable", "type": "function" }, { "inputs": [], "name": "name", "outputs": [ { "internalType": "string", "name": "", "type": "string" } ], "stateMutability": "view", "type": "function" }, { "inputs": [], "name": "numberOfOwnerMints", "outputs": [ { "internalType": "uint256", "name": "", "type": "uint256" } ], "stateMutability": "view", "type": "function" }, { "inputs": [], "name": "owner", "outputs": [ { "internalType": "address", "name": "", "type": "address" } ], "stateMutability": "view", "type": "function" }, { "inputs": [ { "internalType": "address[]", "name": "supporters", "type": "address[]" } ], "name": "ownerAddSupporters", "outputs": [], "stateMutability": "nonpayable", "type": "function" }, { "inputs": [ { "internalType": "uint256", "name": "numberOfMints", "type": "uint256" } ], "name": "ownerMint", "outputs": [ { "internalType": "uint256", "name": "", "type": "uint256" } ], "stateMutability": "nonpayable", "type": "function" }, { "inputs": [ { "internalType": "uint256", "name": "tokenId", "type": "uint256" } ], "name": "ownerOf", "outputs": [ { "internalType": "address", "name": "", "type": "address" } ], "stateMutability": "view", "type": "function" }, { "inputs": [ { "internalType": "string", "name": "_uri", "type": "string" } ], "name": "ownerReveal", "outputs": [], "stateMutability": "nonpayable", "type": "function" }, { "inputs": [], "name": "publicMintingTime", "outputs": [ { "internalType": "uint256", "name": "", "type": "uint256" } ], "stateMutability": "view", "type": "function" }, { "inputs": [], "name": "renounceOwnership", "outputs": [], "stateMutability": "nonpayable", "type": "function" }, { "inputs": [ { "internalType": "address", "name": "from", "type": "address" }, { "internalType": "address", "name": "to", "type": "address" }, { "internalType": "uint256", "name": "tokenId", "type": "uint256" } ], "name": "safeTransferFrom", "outputs": [], "stateMutability": "nonpayable", "type": "function" }, { "inputs": [ { "internalType": "address", "name": "from", "type": "address" }, { "internalType": "address", "name": "to", "type": "address" }, { "internalType": "uint256", "name": "tokenId", "type": "uint256" }, { "internalType": "bytes", "name": "_data", "type": "bytes" } ], "name": "safeTransferFrom", "outputs": [], "stateMutability": "nonpayable", "type": "function" }, { "inputs": [ { "internalType": "address", "name": "operator", "type": "address" }, { "internalType": "bool", "name": "approved", "type": "bool" } ], "name": "setApprovalForAll", "outputs": [], "stateMutability": "nonpayable", "type": "function" }, { "inputs": [ { "internalType": "bytes4", "name": "interfaceId", "type": "bytes4" } ], "name": "supportsInterface", "outputs": [ { "internalType": "bool", "name": "", "type": "bool" } ], "stateMutability": "view", "type": "function" }, { "inputs": [], "name": "symbol", "outputs": [ { "internalType": "string", "name": "", "type": "string" } ], "stateMutability": "view", "type": "function" }, { "inputs": [ { "internalType": "uint256", "name": "_id", "type": "uint256" } ], "name": "tokenURI", "outputs": [ { "internalType": "string", "name": "", "type": "string" } ], "stateMutability": "view", "type": "function" }, { "inputs": [ { "internalType": "address", "name": "from", "type": "address" }, { "internalType": "address", "name": "to", "type": "address" }, { "internalType": "uint256", "name": "tokenId", "type": "uint256" } ], "name": "transferFrom", "outputs": [], "stateMutability": "nonpayable", "type": "function" }, { "inputs": [ { "internalType": "address", "name": "newOwner", "type": "address" } ], "name": "transferOwnership", "outputs": [], "stateMutability": "nonpayable", "type": "function" }, { "inputs": [ { "internalType": "uint256", "name": "newFee", "type": "uint256" } ], "name": "updateFee", "outputs": [], "stateMutability": "nonpayable", "type": "function" } ]

const Web3Modal = window.Web3Modal.default;
const WalletConnectProvider = window.WalletConnectProvider.default;
let web3, web3Modal, userAddress;

var numOfMints = 1;

$("#numberPick").on('change',function(){
          numOfMints=$(this).val();
});

function init() {
  console.log("Initializing example");
  console.log("WalletConnectProvider is", WalletConnectProvider);

  // Check that the web page is run in https (MetaMask won't be available)
  if(location.protocol !== 'https:') {
    document.querySelector("#btn-connect").setAttribute("disabled", "disabled")
    return;
  }

  const providerOptions = {
    walletconnect: {
      package: WalletConnectProvider,
      options: {
        infuraId: "a7ca739399d546a0a44d65c7ec14954e",
      }
    },
  };

  web3Modal = new Web3Modal({
    cacheProvider: false,
    providerOptions, // required
    disableInjectedProvider: false, 
  });
}

async function onConnect() {
  let provider;

  console.log("opening web3modal", web3Modal);

  try {
    provider = await web3Modal.connect();
  } catch(e) {
    console.log("Could not get a wallet connection", e);
    return;
  }

  console.log('connected');
  document.querySelector("#initial").style.display = "none";
  document.querySelector("#mint").style.display = "block";

  web3 = new Web3(provider);
  const accounts = await web3.eth.getAccounts();
  userAddress = accounts[0];
}

async function onMint() {  
  const contract = new web3.eth.Contract(CONTRACT_ABI, "0x2d9a757e4b5a3a9dd7e21f5842eb746766525a9d");

  console.log("minting...");

  try {
    await contract.methods.mint(numOfMints).send({from: userAddress});
  } catch(e) {
    console.log(e);
  }
}

window.addEventListener('load', async () => {
  init();
  document.querySelector("#btn-connect").addEventListener("click", onConnect);
  document.querySelector("#btn-mint").addEventListener("click", onMint);
});
</script>
```
