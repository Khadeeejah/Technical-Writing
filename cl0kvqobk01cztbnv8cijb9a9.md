# Reference Types In Solidity

Last week I published an article on \[INTRODUCTION TO VALUE TYPES IN SOLIDITY\]((https://khadeeejah.hashnode.dev/introduction-to-value-types-in-solidity) . Do check it out if you haven't. In this article, I'll be explaining reference types in solidity.

Reference types have to be handled more carefully than value types. This is because it is crucial to clearly indicate the data area where the reference type is stored. Reference types comprises of structs, arrays, and mappings. If you use a reference type, you always have to explicitly provide the data area where the type is stored:

```plaintext
MEMORY: whose lifetime is limited to an external function call.
Storage: the location where the state variables are stored. It is limited to the lifetime of a contract.
CALLDATA: is a special data location that contains the function arguments.
```

# Data location and assignment behaviour

Set location is important for the semantics of assignments, not only for the persistence of data:

* Assignments between \*Storage \*and *Memory* (or from *Calldata*) always create an independent copy.
    
* Assignments from *memory* to *memory*only create references. This means that changes to one memory variable are also visible in all other memory variables that refer to the same data.
    
* Assignments from *storage* to a local storage variable also only assign a reference.
    
* All other assignments to storage always copy
    

## ARRAYS

Arrays can either have a compile-time fixed size, or they can have a dynamic size. In general, you should be careful with operations on dynamically sized arrays, because they can lead to all sorts of bugs and lost funds as we will see later.

### STRUTS

Solidity allows users to create and define their own type in the form of structures. The structure is a group of different types even though it’s not possible to contain a member of its own type. The structure is a reference type variable which can contain both value type and reference type.

### MAPPING

Mapping is a most used reference type, that stores the data in a key-value pair where a key can be any value types. It is like a hash table or dictionary as in any other programming language, where data can be retrieved by key.

Check out the illustration below.

```plaintext
// SPDX-License-Identifier: MIT
pragma solidity >=0.4.22 <0.9.0;

contract ReferenceType{
    // - storage
    // - memory
    // - calldata

    // Arrays

    // Dynamic array
    uint[] public testArrayDyn;
    string[] public testStringArray;
    // []

    // Static Array
    uint[3] public testArrayStatic;
    // [0, 0, 0]
    // [1, 2, 3] 
    // pop(3) instead of [1,2]
    // [1, 2, 0]

    // push - add a value to the end of the array
    // pop - removes a value from an array
    // length - gets the size
    // delete - removes

    function useStaticArray(uint _value) external returns(uint, uint[3] memory){
        // Push doesn't work here
        testArrayStatic[2] = _value;
        // Pop doesn't work here
        delete testArrayStatic[2];
        uint length = testArrayStatic.length;
        return (length, testArrayStatic);
    }

    function useDynArrayPush(uint _value) external {
        testArrayDyn.push(_value);
    }

    function useDynArrayPop() external {
        // testArrayDyn.pop();
        delete testArrayDyn[1];
    }

    struct User{
        string name;
        uint age;
        string stateOfOrigin;
        string gender;
    }

    User[] public arrayOfUsers;

    function alterStruct
    (
        string memory _name,
        uint _age,
        string memory _stateOfOrigin,
        string memory _gender
    )
    external
    {
        User memory user = User(_name, _age, _stateOfOrigin, _gender);
        arrayOfUsers.push(user);
    }

    // Mapping
    // Bytes
}
```

If you have any questions feel free to drop a comment i would be happy to help, and please do not forget to check out my last atrticle on value types in solidity. Thanks for reading.