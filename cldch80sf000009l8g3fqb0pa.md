# Solidity Smart Contract Structure

Solidity contracts are extremely similar to classes in object-oriented programming languages such as Java. State variables, functions, modifiers, events, structs, and enums are all included in contracts.

## Step 1: Pragma statement

The pragma statement is the first line in any solidity file. It displays the compiler version that is compatible with the smart contract. Changes in compiler versions can have an impact on how your smart contract behaves.

```solidity
// SPDX-License-Identifier: MIT
pragma solidity ^0.8.17;
```

## Step 2: Declaring a Contract

The contract declaration comes after the pragma statement. It is essential to capitalize the contract name and name the file similarly to the contract. The contract is then placed between the curly braces. The state variable declaration follows this.

```solidity
// SPDX-License-Identifier: MIT
pragma solidity ^0.8.17; 

contract SimpleStorage {
uint value;
}
```

## Step 3: Events

Following the Storage Declaration, we define events. Events are user-friendly interfaces to the EVM's logging capabilities.

```solidity
// SPDX-License-Identifier: MIT
pragma solidity ^0.8.17; 

contract SimpleStorage {
uint value;
event Logchange (uint newStorage);
}
```

## Step 4: Function Modifiers

Modifiers can be used declaratively to change the behaviour of functions. For example, you can use a modifier to check a condition before executing a function.

```solidity
// SPDX-License-Identifier: MIT
pragma solidity ^0.8.17; 

contract SimpleStorage {
uint value;

event Logchange (uint newStorage);

modifier onlyIfZero{
require(value == 0 );

}
```

## Step 5: Functions

A function is declared by using the function keyword, followed by the name and a list of parameters enclosed in parenthesis. You have the option of specifying contract accessibility which includes.

* Internal ( can only be accessed within the contract or any function in a contract derived from the contract )
    
* Private ( can only be accessed from this contract )
    
* External ( can only be accessed from outside the contract, unless you use **<mark>this </mark> )**
    
* Public ( No restrictions )
    

```solidity
// example of external functiom
function addUser(address _addr) external {
        users[_addr] = true;
        emit UserCreated(_addr, block.timestamp);
    }


// example of public function
function withdraw() public {
        uint amount = address(this).balance;
        (bool success, ) = Delibra.call{value: amount}("");
        require(success, "failed to send matic");
    }

// example of private function
  function _addNumber(uint _number) private {
    savedNumbers.push(_number);
  }
```

A constant/view function, on the other hand, does not modify any state. State modification Includes,

* Writing to state variable
    
* Emitting events
    
* Creating other contracts
    
* Using self destruct
    
* Sending ether via calls
    
* Calling any function not marked view or pure
    
* Using low-level calls
    
* Using inline assembly that contains certain opcodes
    

Because constant functions do not modify the state, they read from the blockchain and require no gas cost.

```solidity
string name = khadijah

function getName()
  constant
return (string) {
  return name;
}
```

A pure function, on the other hand, neither modifies nor reads the state. They are self-contained functions that do not require any lookups or changes to the system; they simply modify the input to produce consistent output.

```solidity
function f (uint a, uint b)
   pure
returns (uint) {
returns a * (b + 42);
}
```

## Step 5: Structs Types

Structs are custom-defined types that can group several variables, you can learn more about structs in my previous [***article***](https://khadeeejah.hashnode.dev/reference-types-in-solidity)

```solidity
// SPDX-License-Identifier: MIT
pragma solidity ^0.8.17; 

 //  stores relevant information for an NFT listed in the marketplace
   
contract MarketPlace {
 struct NFT {
        address payable seller;
        uint256 price;
        bool listed;
        uint256 quantity;
        address[] owners;
        string tokenId;
     }

}
```

To summarize, I'd like to provide a complete smart contract example that maintains users' wallet addresses after connecting to a DAAP as a way of authentication or onboarding.

```solidity
// SPDX-License-Identifier: GPL-3.0

pragma solidity ^0.8.17;

contract DelibraUserAuth {
    // User is able to identify as a reader or author
    // we need to know users that have been onboarded
    // users that have their delibra names
    //extras
    //for readers: genre []
    //for authors: username, displayname, profile url

    enum UserType {
        Reader, // returns 0
        Author, // returns 1
        Admin // returns 2
    }

    struct User {
        string userName;
        bool onboarded;
        UserType userType;
        string profileUrl;
    }

    mapping(address => User) public users;
    address[] UsersAddress;

    event UserCreated(address _addr, uint timestamp);
    event UserUpdated(address _addr, uint timestamp);

    function getUserInfo() public view returns (User memory){
        require(isDelibraUser(msg.sender) == true, "Not a delibra user");
        return users[msg.sender];
    }

    function isDelibraUser(address _addr) public view returns (bool){
        for(uint i=0; i<UsersAddress.length; ++i){
            if(UsersAddress[i] == _addr){
                return true;
            } 
        }
        return false;
    }

    function setUserInfo(
        string calldata _username, 
        bool _onboarded, 
        UserType _usertype,
        string calldata _profileUrl) public returns (bool){
        users[msg.sender] = User(_username, _onboarded, _usertype, _profileUrl);
        if(isDelibraUser(msg.sender) == false){
            UsersAddress.push(msg.sender);
            emit UserCreated(msg.sender, block.timestamp);
        } else{
            emit UserUpdated(msg.sender, block.timestamp);
        }
        return true;
    }
}
```

In my next article, we will delve deeper into solidity functions and discuss exceptions, fallback functions, overloading functions, and so on. Subscribe to my newsletter to be notified when the article is published.

Was this article helpful to you? Please let me know in the comments area.☺️