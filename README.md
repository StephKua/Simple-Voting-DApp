# Simple-Voting-DApp

Basic voting DApp to understand the flow of DApp

## Prerequisites

```
npm install web3 ganache-cli solc
```

## Usage

### 1. Use web3 and ganache-cli to interact with our contract

```
steph:~/simple_voting_dapp$ node
> Web3 = require('web3')
> gcli = require('ganache-cli')
> web3 = new Web3(new Web3.providers.HttpProvider("http://localhost:8545"));
> web3.setProvider(gcli.Provider());
```

### 2. Compile Contract

```
> code = fs.readFileSync('voting.sol').toString()
> solc = require('solc')
> compiledCode = solc.compile(code)
```

### 3. Deploy Contract

```
> abi = JSON.parse(compiledCode.contracts[':Voting'].interface)
> VotingContract = new web3.eth.Contract(abi)
> byteCode = compiledCode.contracts[':Voting'].bytecode
> web3.eth.getAccounts().then(e=>{firstAccount=e[0];})
> Rama = web3.utils.asciiToHex("Rama");
> Nick = web3.utils.asciiToHex("Nick");
> Jose = web3.utils.asciiToHex("Jose");
> deployedContract = VotingContract.deploy({ data: byteCode, arguments: [[Rama, Nick, Jose]]}).send({from: firstAccount, gas: 4700000}).on('receipt', function(receipt){console.log(receipt.contractAddress)})
> deployedContract.address
> contractInstance = VotingContract.at(deployedContract.address)
```

### 4. Open up the html file and interact with it.

## Credits

look into the original [tutorial](https://medium.com/@mvmurthy/full-stack-hello-world-voting-ethereum-dapp-tutorial-part-1-40d2d0d807c2) for more details
