### A simple, complete DAPP hello world howto

I wanted to have all the steps from [here](https://medium.com/@mvmurthy/full-stack-hello-world-voting-ethereum-dapp-tutorial-part-1-40d2d0d807c2) in a succinct, convenient, pasteable format.

NO ORIGINAL CONTRIBUTIONS HERE. All glory to [Mahesh Murthy](https://medium.com/@mvmurthy?source=post_header_lockup)

In a bash shell:

```bash
npm install ganache-cli web3@0.20.2 solc
./node_modules/.bin/ganache-cli # <-- stays running
```

In a JS shell:

```javascript
code = fs.readFileSync('Voting.sol').toString()
solc = require('solc')
compiledCode = solc.compile(code)
abiDefinition = JSON.parse(compiledCode.contracts[':Voting'].interface)
Web3 = require('web3')
web3 = new Web3(new Web3.providers.HttpProvider("http://localhost:8545"));
VotingContract = web3.eth.contract(abiDefinition)
VotingContract = web3.eth.contract(abiDefinition)
byteCode = compiledCode.contracts[':Voting'].bytecode
deployedContract = VotingContract.new(['Rama','Nick','Jose'],{data: byteCode, from: web3.eth.accounts[0], gas: 4700000})
deployedContract.address
contractInstance = VotingContract.at(deployedContract.address)
```

Modify `index.js` as required:

```javascript
// In your nodejs console, execute contractInstance.address to get the address at which the contract is deployed and change the line below to use your deployed address
contractInstance = VotingContract.at('0x2a9c1d265d06d47e8f7b00ffa987c9185aecf672');
```

Open `index.html` in a browser.

Done!