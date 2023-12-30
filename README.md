# All function Swap Overview

In this tutorial you will write a cross-chain swap contract that allows users to swap a native gas or ERC-20 token from one of the connected chains for a token on another chain.

The swap process involves depositing a token from a connected chain to ZetaChain, triggering a swap omnichain contract to swap between ZRC-20 representations of the tokens and then withdrawing the swapped token to the recipient address on the destination chain.

## Prerequisites

Before getting started, ensure that you have
[Node.js](https://nodejs.org/en/download) and [Yarn](https://yarnpkg.com/)
installed on your system.

## Set Up Your Environment 

Clone the Hardhat contract template:

```bash
git clone https://github.com/zeta-chain/template
```

Install dependencies:

```bash
cd template
yarn
```

## Create the contract

Run the following command to create a new omnichain contract called Swap.

```bash 
npx hardhat omnichain Swap targetToken:address recipient
``` 

## Omnichain Contract 

Create Swap.sol   (Look at the [contracts](contracts/) folder for more details.)


## Tasks/interact.ts

[Task](interact.ts/)


## Tasks/deploy.ts

Task](deploy.ts/)


## Compile and Deploy the Contract

```bash
npx hardhat compile --force

```
```bash
npx hardhat deploy --network zeta_testnet
```

```bash 
🔑 Using account: 0x2cD3D070aE1BD365909dD859d29F387AA96911e1

🚀 Successfully deployed contract on ZetaChain.
📜 Contract address: 0xf6CDd83AB44E4d947FE52c2637ee4A04F330328E
🌍 Explorer: https://athens3.explorer.zetachain.com/address/0xf6CDd83AB44E4d947FE52c2637ee4A04F330328E
``` 

## Swap Native Gas Tokens Between EVM Chains

```bash 
npx hardhat interact --contract 0xf6CDd83AB44E4d947FE52c2637ee4A04F330328E --amount 0.01 --network goerli_testnet --target-token 0x48f80608B672DC30DC7e3dbBd0343c5F02C738Eb --recipient 0x2cD3D070aE1BD365909dD859d29F387AA96911e1
``` 

```bash 
🔑 Using account: 0x2cD3D070aE1BD365909dD859d29F387AA96911e1

🚀 Successfully broadcasted a token transfer transaction on goerli_testnet network.
📝 Transaction hash: 0x6b4156c195d955d1325a5e6275214db63ff2e3642838607333e74abd74b8fc13
``` 

Track your cross-chain transaction:

```bash 
npx hardhat cctx 0x6b4156c195d955d1325a5e6275214db63ff2e3642838607333e74abd74b8fc13
```  

## Swap ERC-20 Tokens Between EVM Chains 

```bash  
npx hardhat interact --contract 0xf6CDd83AB44E4d947FE52c2637ee4A04F330328E --amount 10 --token 0x07865c6e87b9f70255377e024ace6630c1eaa37f --network goerli_testnet --target-token 0x48f80608B672DC30DC7e3dbBd0343c5F02C738Eb --recipient 0x2cD3D070aE1BD365909dD859d29F387AA96911e1 
```  

```bash  
🔑 Using account: 0x2cD3D070aE1BD365909dD859d29F387AA96911e1

🚀 Successfully broadcasted a token transfer transaction on goerli_testnet
network. 📝 Transaction hash:
0xff32dd2391c4f62694cc99afd0da1c2a1352c8caf29846cc366aab54a631e8f8
```   

```bash 
npx hardhat cctx
0xff32dd2391c4f62694cc99afd0da1c2a1352c8caf29846cc366aab54a631e8f8 
```

```bash

✓ CCTXs on ZetaChain found.

✓ 0xa4cb698122916f10c932e146c45517b4f47de1e16be493ea66f28b5a34c7bfb5: 5 → 7001: OutboundMined (Remote omnichain contract call completed)
✓ 0xad18c759713ce5604683aeb389fc9a1a91f537c0abbb8d9f9fc6cfc11e55fdc7: 7001 → 80001: PendingOutbound  → OutboundMined

```

## Swap from Bitcoin

Use the send-btc task to send Bitcoin to the TSS address with a memo. The memo should contain the following:

Omnichain contract address on ZetaChain: f6CDd83AB44E4d947FE52c2637ee4A04F330328E

Target token address: 48f80608B672DC30DC7e3dbBd0343c5F02C738Eb

Recipient address: 2cD3D070aE1BD365909dD859d29F387AA96911e1

```bash 
npx hardhat send-btc --amount 0.001 --memo f6CDd83AB44E4d947FE52c2637ee4A04F330328E48f80608B672DC30DC7e3dbBd0343c5F02C738Eb2cD3D070aE1BD365909dD859d29F387AA96911e1 --recipient tb1qy9pqmk2pd9sv63g27jt8r657wy0d9ueeh0nqur
``` 

```bash  
npx hardhat cctx 3c2eeee38fafbfbcdceca0d595c1433c48c738aaa6e1df407a681aeeeb1da3d6
```  

```bash  
✓ CCTXs on ZetaChain found.

✓ 0xa7d4a46545806a5aff4d4fc20cb37295f426b70f0f6b2a123f67cbdb3014c995: 18332 → 7001: OutboundMined (Remote omnichain contract call completed)

✓ 0x963cf8890b3da9e84379eca06a2e4835aba3a027bca6560e76d19945b75b2c39: 7001 → 80001:
```  