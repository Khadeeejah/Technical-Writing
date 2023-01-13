# Introduction To Value Types In Solidity

Solidity is an object-oriented, high-level language for creating smart contracts. Smart contracts are small computer programs that are replicated and processed on all computers on the Ethereum network without a central coordinator. There are various data types in solidity, and the value type is one of them. In this blog, we will be looking at some of the value types in solidity.

# What is a Value Type?

Value type is a type that holds the data directly in the memory owned by it. Variables of these types are always passed by value, meaning that they are always copied when assigned to another variable or passed into a function. The following types are value types in solidity:

* Booleans
    
* Integers
    
* Unsigned Integers
    
* Addresses
    
* Fixed- size byte arrays(bytes1 to bytes32)
    
* Enums
    
* Fixed point numbers
    

## Booleans

Booleans are represented by ***bool*** and can hold two values: true or false.

`bool testBool = true; bool testBool1 = false;`

Solidity supports all your regular boolean operators, such as

1. ! (logical negation)
    
2. && (logical conjunction, AND)
    
3. || (logical disjunction, OR)
    
4. \== (equality)
    
5. != (inequality)
    

They only take up 1 byte of storage.

### Integers

There are two main Solidity types of integers of differing sizes which are \*\*\*int \*\*\*- signed integers. ***uint*** - unsigned integers.

According of size, you have keywords such as ***uint8*** up to ***uint256***, that is, of 8 to 256 bits. The simple ***uint*** and\*\*\* int \*\*\*are similar to uint256 and int256, respectively.

```plaintext
int age = 20;
    int temp = -37;
    int8 temp1 = -2;
    int256 temp2 = -55;

    int public min256 = type(int).min;   
    int public max256 = type(int).max;

    int8 public min8 = type(int8).min;   
    int8 public max8 = type(int8).max;
// unsigned integer
    uint age = 20;
    uint8 score1 = 255;
    // (2 ** 8) - 1 = 256 - 1 = 255
    uint16 score2 = 40;
    uint24 score3 = 56;
    uint256 score4 = 45;
```

uint is an alias for uint256

### Address

The address solidity value type has two similar kinds, namely address and address payable. It is a data type to store a 20-byte value representing the Ethereum address. The main difference between these two types is that an address payable is an address you can send ether to, while a plain address cannot be sent ether. We can implicitly convert from address payable to address, whereas conversions from address to address payable must be explicitly done via payable ( address &gt;).

```plaintext
address testAddr = 0x5B38Da6a701c568545dCfcB03FcB875f56beddC4;
    address payable testAddr2 = payable(0xAb8483F64d9C6d1EcF9b849Ae677dD3315835cb2);
```

### Fixed Point Numbers

Fixed point numbers are similar to float data type but the main difference is that we need to specify the number of bits required for the integer part and fractional part in fixed-point numbers whereas, in float, it is not necessary.

We use fixed/ufixed keywords to specify fixed-point numbers of various sizes. We need to specify the fixed-point numbers in the following manner – fixedMxN and ufixedMxN. Here M represents the number of bits taken by the type and N represents how many decimal points are available.

Solidity does not fully support Fixed Point numbers yet, hence we can declare Fixed Point numbers but we cannot assign them to or from them.

The operations available for fixed-point numbers are –

> Comparisons: &lt;=, &lt;, ==, !=, &gt;=, &gt; Arithmetic operators: +, -, unary -, \*, /, %

### Enums

Enums in Solidity are a way to create user-defined types. Enums are explicitly convertible to integer types, but not implicitly. Enum values are numbered in the order they are defined, starting from 0.They are also part of the ABI( Application binary interface)

```plaintext
enum UserType {
        ADMIN,
        SUBADMIN,
        NORMALUSER
    }
```

### Fixed Size Byte

Fixed-size byte arrays contain a sequence of bytes. The length of the array must always be specified in the type declaration. They are declared in the following way bytes1, bytes2, bytes3 all the way up to bytes32. byte is an alias for bytes1. You can use your regular boolean operators, comparison operators, and bitwise operators on this type too. for example,

```plaintext
bytes1 public testBytes = "W"; 
    bytes2 public testBytes1 = "er";
    bytes32 public testBytes32 = "FGGGSS";
```

In this article, I did a short summary on value types in solidity, and as a beginner in web3 I'mlooking forward to writing more articles and sharing my journey. feel free to drop a comment and watch out for my next article on my first solidity smart contract.