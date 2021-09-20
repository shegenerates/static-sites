# Snippet

```
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
    await contract.methods.mint(numOfMints).send({from: userAddress, value: wei});
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
