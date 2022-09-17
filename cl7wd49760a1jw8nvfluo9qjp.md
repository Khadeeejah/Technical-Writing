## My Latest Project....

# Introduction

Snap is a new feature released by metamask to enhance developers experience on their wallet. A "snap"  is used to alter the wallet experience in a private setting. For instance, utilizing internal APIs, MetaMask may easily add new APIs, support for various blockchain protocols, or change the functionality of already existing features. By altering MetaMask in ways that were previously not conceivable, Snaps offers a new method for developing web3 end user experiences.

 Snaps connect with MetaMask using JSON-RPC, same like with the Ethereum Provider RPC API provided by MetaMask. I would be explaining the how i built my token snap and explain what it also does.

##  Prerecruisite


- Google Chrome
- [MetaMask Flask](https://metamask.io/flask)
- Node.js
- Yarn
- A text editor or IDE like Visual Studio Code


I built a Snap that fetches token price from Uniswap V3 pool and also checks if a token is either ERC20, ERC721 and ERC1155 token.


![Screen Shot 2022-09-08 at 12.48.09 AM.png](https://cdn.hashnode.com/res/hashnode/image/upload/v1662839786858/PY_78JxfR.png align="left")

In order to use the snap i used a restricted method called  ***snap_confirm***. Calling this method causes a confirmation to be displayed in the MetaMask UI.



![Screen Shot 2022-09-11 at 12.01.34 AM.png](https://cdn.hashnode.com/res/hashnode/image/upload/v1662840112613/TpxxJBhR3.png align="left")

you  can either approve or reject the confirmation, which will be indicated by the method's return value.


### Tools i used 


1. Web.eth

2. Uniswapv3sdk

3. Infura api key 

4. Openzeppelin Contract

5. ABIs from Etherscan

6.HTML, CSS and Javascript for my UI


You can check out the [Repo](https://github.com/Khadeeejah/token-snap) on Github and also test it [Token Snap](https://khadeeejah.github.io/token-snap/)













 






