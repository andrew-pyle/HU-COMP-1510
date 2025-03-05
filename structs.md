---
layout: page
prev: files
---

# Structs

Structs are a collection of data which represent a single entity.

Struct, short for "structure", is a single variable with multiple fields. It can represent something more complex than a single integer or string, etc. Structs are **composed** from multiple fields, each with its own type.

You can think of a struct as a collection of other data types.

## Syntax

```cpp
struct NameOfStruct { // Name is capitalized by convention
    type field1_name; // semicolon after each attribute
    type field2_name;
    // ...            // Can have any number of attributes
    type fieldN_name;
};                    // semicolon at the end!

// Example
struct Pokemon {
    int number;
    string name;
    string type;
    int attack;
    int defense;
}

// Declare a Pokemon struct
Pokemon bulbasaur;
// Assign values to it
bulbasaur.number = 1;
bulbasaur.name = "Bulbasaur";
bulbasaur.type = "Grass/Poision";
bulbasaur.attack = 50;
bulbasaur.defense = 20;

// Initialize a Pokemon struct with an initializer list
Pokemon charmander = { 
    // The order of the values in the Initializer list matches the declaration
    2, 
    "Charmander", 
    "Grass/Poision", 
    70, 
    10 
};

// To-do
// - Copy a struct
// - Function with struct parameter
// - Function which returns struct
```
### To Do

1. Purpose & History
1. Terminology
  - Data Members
  - Attributes/Properties
  - Access Operator
  - Conventions: Capital name, defined after `#include`s and before functions
1. Declaration
1. Aggregate Initialization
1. Copying
1. Output (can't)
1. Structs & Functions
  - Parameter Signature
  - Return type
1. Nesting
1. Structs & Vectors
  - Vector of structs
  - Struct with vector property
