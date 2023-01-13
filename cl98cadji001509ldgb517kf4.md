# Understanding zkEVM

# Introduction

One of the most visible and potentially scaleable approaches to Ethereum is through zero-knowledge (ZK) technology. A zkEVM (zero-knowledge Ethereum Virtual Machine) is a common way to scale Ethereum using ZK proofs . So, what exactly is a zkEVM, and how can it help us make Ethereum more affordable and efficient to use?

## What is EVM

All Ethereum accounts and smart contracts exist within the Ethereum Virtual Machine (EVM). At any given block in the chain, Ethereum has one and only one "canonical" state, and the EVM is what provides the criteria for computing a new valid state from block to block. The Ethereum Virtual Machine (EVM) aggregates the input from all individual nodes in the Ethereum network and creates the conditions for us to transact and install smart contracts. As a result, the EVM is the super-computer that offers the functionality that Ethereum users appreciate.

![zkevm.png](https://cdn.hashnode.com/res/hashnode/image/upload/v1665741190236/0nQXrXTrC.png align="center")

*A diagram showing how programs are executed in the ethereum virtual machine* [*source*](https://assets-global.website-files.com/5f973c97cf5aea614f93a26c/62ab70cbe22441cfabf32f84_UFYWVmuqn8yWzAX0bhaf4RMas6VXLX08waszXy6EWoxZS-HqHkdlud_b2eS5dT3h7Gh7SZOQZp8zU2HDV_zjNMwFAxjBBHZ1OYcWACITjj6mC8rRsQxxME8ij80LX62R_HaQhUpJ2HVCVFhrlw.png)

### What is zkEVM

zkEVM is an open-source ZK-Rollup that supports EVM opcode compatibility for an easy user interface and Ethereum security. The underlying protocol of zkEVM uses a validity proof to guarantee that the state transitions are accurate. Polygon has built its own first zero-knowledge scaling solution that is fully equivalent to an EVM.

### How does zkEVM works

To validate various components of each computation, the zkEVM generates zero-knowledge proofs.

* Bytecode access:
    
* Read-write operation
    
* Computation
    

### Advantages of zkEVM

The development of a fully functional zkEVM will promote the creation of ZK-rollup projects that are EVM-compatible. This offers the following benefits:

* Secure scalability
    
* Cheaper costs
    
* Faster finality and capital efficiency
    
* Network effects
    

While there are advantages, it is also difficult to develop a zkEVM because the EVM was not designed with zk-proof computation in mind and as a result, it has features that make it difficult to prove circuits. Four factors that make creating zkEVMs challenging are briefly described below:

* Special opcodes
    
* Stack-based architecture
    
* Storage overhead
    
* Proving costs
    

On zkEVM, building dApps is exactly like creating them on Ethereum. Just switch to the zkEVM RPC to begin developing on a network with significantly faster throughput and reduced costs. Both developers and users may enjoy a full EVM-like experience thanks to **Polygon** zkEVM. So you don't need new wallets or specialized tools to construct or communicate with zkEVM.

### Connecting to Polygon zkEVM

The following information must be entered in order to add the Polygon zkEVM network to your wallet:

```plaintext
Network Name: Polygon zkEVM Testnet
RPC URL: https://public.zkevm-test.net:2083
Chain ID: 1402
Currency Symbol: ETH
Block Explorer URL: https://public.zkevm-test.net:8443
```

For more about polygon's zkEVM check out their [docs](https://polygon.technology/solutions/polygon-zkevm/).

Aside Polygon there are also different zkEVM protocols such as [zkSync zkEVM](https://docs.zksync.io/zkevm/), [AppliedZKP zkEVM](https://github.com/privacy-scaling-explorations/zkevm-specs)and [Scroll zkEVM](https://scroll.io/blog/zkEVM)