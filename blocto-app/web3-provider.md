---
description: >-
  Blocto injects web3 provider to web context so dApps can interact with
  blockchain
---

# Web3 Provider

### Injection

Blocto injects web3 provider to web context as `window.bloctoProvider` and `window.BLOCKCHAIN` where BLOCKCHAIN is either 

* ethereum
* tron
* tangerine

You can use the provider with your web3.js like

```javascript
import Web3 from 'web3';

// use the provider to instantiate web3 onject
const web3 = new Web3(window.ethereum);

console.log(window.ethereum.isBlocto);
// prints True
```

You can use all the web3.js functionalities and Blocto will handle all the wallet operations and blockchain interactions for you.

For more documentation for what you can do with web3.js, check out 

* [web3.js 1.2.x docs](https://web3js.readthedocs.io/en/v1.2.11/index.html)
* [web3.js 0.2x.x docs](https://github.com/ethereum/web3.js/blob/0.20.7/DOCUMENTATION.md)

### Sign Transaction

For dApps relying on `signTransaction` for off-chain authentication, Blocto follows [EIP-1654](https://github.com/ethereum/EIPs/issues/1654). To verify the signature, you need to call method on the wallet contract to check if the signature came from a rightful owner of the wallet contract.

Dapper Labs has built the tools to carry out this verification:

* [Golang implementation](https://github.com/dapperlabs/dappauth)
* [JavaScript implementation](https://github.com/dapperlabs/dappauth.js)
