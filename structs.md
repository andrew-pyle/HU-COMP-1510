---
layout: page
prev: files
next: classes
---

# Structs

Structs are a collection of data which represent a single entity.

Struct, short for "structure", is a single variable with multiple fields. It can represent something more complex than a single integer or string, etc. Structs are **composed** from multiple fields, each with its own type.

You can think of a struct as a collection of other data types.

## Syntax

```cpp
// Syntax
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
    string cry;
};

  // Declare a Pokemon struct


  // Create a Pokemon via Declaration, then Assignment
  Pokemon bulbasaur;
  bulbasaur.number = 1;
  bulbasaur.name = "Bulbasaur";
  bulbasaur.type = "Grass/Poison";
  bulbasaur.cry = "Bulbaaa";

  // Create a Pokemon via Initialization
  Pokemon charmander = {4, "Charmander", "Fire", "char-char"};


  // Access Operator (.)
  Pokemon pikachu;
  pikachu.name = "Pikachu";     // Assign to data member
  cout << pikachu.name << endl; // Read data member

```

## History

`struct`s come from the C programming language. `struct`s in C++ can often be used with C code.

## Terminology

### Data Members

A `struct` is composed of one or more **data members**, each having a type of its own. Also known as **attribute** or **property**.

```cpp
// This struct has two data members
struct Student {
  string name; // ← data members
  double gpa;  // ←
};
```

### Access Operator

The **access operator** is the dot `.`. It is used to access a data member of a struct, either for reading or assigning.

```cpp
Student s = {"Alice", 2.5};

cout << s.gpa;
//       ↑ access operator
```

### Aggregate Initialization

`struct`s can be initialized with an initializer list. This is called **aggregate initialization**

```cpp
Student s = {"Bob", 2.5}; // ← aggregate initialization
```

## Conventions

### Struct Names Begin with a Capital Letter

```cpp
struct Tree { // ✅ Follows naming convention
  string species;
  string genus;
};

struct tree { // ❌ Does not follow naming convention
  string species;
  string genus;
};

```

### Structs are defined after `#include`s, and before functions

```cpp
#include <iostream>

// ✅ Follows definition convention
struct Club {
  string greek_name;
  string latin_name;
};

void print_latin(Club c) {
  cout << c.latin_name;
}

// ❌ Does not follows definition convention — below functions
struct Computer {
  string os;
  int memory;
  double storage;
};

int main() {
  Club dxd = {"ΔΧΔ", "Delta Chi Delta"};
  print_latin(dxd);
  return 0;
}
```

## Usage

### Copy a `struct`

`struct`s can be copied via assignment. There are two techniques for copying structs:

1. Copy the entire struct
1. Copy one attribute of the struct

#### Copy the entire struct

```cpp
Pokemon charmander = {4, "Charmander", "Fire", "char-char"};

// This assignment copies all attributes
Pokemon another_charmander = charmander;

cout << another_charmander.type << endl; // Prints "Fire"
```

#### Copy One Attribute

```cpp
Pokemon bulbasaur = {1, "Bulbasaur", "Grass/Poison", "bulbaaa"};

// Declare another struct
Pokemon another_bulbasaur;

// One data member is copied with each assignment to the new struct
another_bulbasaur.number = bulbasaur.number;
another_bulbasaur.name = bulbasaur.name;
another_bulbasaur.type = bulbasaur.type;
another_bulbasaur.cry = bulbasaur.cry;

cout << another_bulbasaur.type << endl; // Prints "Grass/Poison"
```

### Functions

#### `structs` can be passed by value

```cpp
void print_cry(Pokemon pokemon) {
  cout << pokemon.cry << endl;
}
```

#### `structs` can be passed by reference, too

```cpp
void evolve(Pokemon &pokemon) {
  if (pokemon.number == 2) {
    pokemon.number = 3;
    pokemon.name = "Venusaur";
    pokemon.type = "Grass/Poison";
    pokemon.cry = "veeeena-saur";
  }
  // ...
}
```

#### Functions can return a `struct`

```cpp
Pokemon ivysaur_factory(string name) {
  Pokemon evolution = {2, name, "Grass/Poison", "Iiiiivy-saur"};
  return evolution;
}
```

### Output

`struct`s **cannot** be output directly to `cout`.

```cpp
struct Tree {
  string species;
  string genus;
};

int main()
{
  Tree red_oak = {"Quercus", "rubra"};

  // ❌ Wrong — structs cannot be output directly
  cout << red_oak << endl;

  // ✅ Right — struct attributes can be output directly
  cout << red_oak.genus << " " << red_oak.species << endl;
}

```

### `struct`s Can Contain Other `structs`

The attributes of a `struct` can be any type, including other `struct`s. This is called **nested** structs.

```cpp
struct PokemonType {
  string primary;
  string secondary;
};

struct Pokemon {
  int number;
  string name;
  string cry;
  PokemonType type;
};

int main() {
  PokemonType grass_poison = {"Grass", "Poison"};
  Pokemon bulbasaur = {1, "Bulbasaur", "Bulbaaa", grass_poison};

  // Prints "Grass/Poison"
  cout << bulbasaur.type.primary << "/" << bulbasaur.type.secondary << endl;
}
```

## Structs & Vectors

`structs` and vectors can be used together in two main ways:

1. A vector of `struct1s
1. A struct with a `vector` attribute

### Vector of `struct`s

```cpp
struct Pokemon {
  string name;
  string cry;
};

int main() {
  // Declare a Vector of structs
  vector<Pokemon> trainer_team;

  // Add existing Pokemon
  Pokemon bulbasaur = {"Bulbasaur", "Bulbaaa"};
  trainer_team.push_back(bulbasaur);

  // Add new Pokemon from initializer list
  trainer_team.push_back({"Caterpie", "cater-cater"});
  trainer_team.push_back({"Rattata", "snarl"});
  trainer_team.push_back({"Pidgey", "pidgeee"});
  trainer_team.push_back({"Ekans", "sssss"});
  trainer_team.push_back({"Nidoran♀", "chomp"});

  // Prints "Go Caterpie! cater-cater"
  cout << "Go "
       << trainer_team.at(1).name << "! "
       << trainer_team.at(1).cry << endl;
}
```

### `struct` with Vector Attribute

`struct`s can have attributes which are themselves a vector of something.

```cpp

struct Pokemon {
  string name;
  string type;
  vector<string> moves;
};

void print_pokemon(Pokemon &pokemon) {
  cout << pokemon.name << " — " << pokemon.type << endl;
  cout << "Moves:" << endl;
  for (int i = 0; i < pokemon.moves.size(); ++i) {
    cout << '\t' << i + 1 << ") " << pokemon.moves.at(i) << endl;
  }
}

int main() {
  Pokemon weedle = {"Weedle", "Bug/Poison"}; // Partially assign values

  // Add values to the moves vector
  weedle.moves.push_back("tackle");
  weedle.moves.push_back("string shot");
  weedle.moves.push_back("poison sting");
  weedle.moves.push_back("bug bite");

  // Or use Aggregate Initialization
  Pokemon caterpie = {
      "Caterpie", "Bug", {"tackle", "string shot", "bug bite"}};

  // Print formatted Pokemon
  print_pokemon(weedle);
  cout << endl;
  print_pokemon(caterpie);
}
```

Output

```txt
Weedle — Bug/Poison
Moves:
        1) tackle
        2) string shot
        3) poison sting
        4) bug bite

Caterpie — Bug
Moves:
        1) tackle
        2) string shot
        3) bug bite
```

## Example Program: Pokémon Team

1. Create a team of Pokémon
1. "Launch" each Pokémon in the team
1. Evolve some Pokémon

```cpp
#include <iostream>
#include <string>
#include <vector>
using namespace std;

// Definition

struct Pokemon {
  int number;
  string name;
  string type;
  string cry;
};

// Functions

void launch(Pokemon &pokemon) {
  cout << "Go "
       << pokemon.name << "! "
       << pokemon.cry << endl;
}

void evolve(Pokemon &pokemon) {
  if (pokemon.number == 1) {
    string old_name = pokemon.name;

    pokemon.number = 2;
    pokemon.name = "Ivysaur";
    pokemon.cry = "Iiiiivy-saur";
  }
  // Add other evolutions ...
  else {
    cout << "No Evolution" << endl;
  }
}

Pokemon ivysaur_factory(string name) {
  Pokemon evolution = {2, name, "Grass/Poison", "Iiiiivy-saur"};
  return evolution;
}

// Main

int main() {
  vector<Pokemon> team;

  Pokemon bulbasaur = {1, "Bulbasaur", "Grass/Poison", "Bulbaaa"};
  Pokemon ivysaur = ivysaur_factory("Ralph");
  Pokemon weedle = {13, "Weedle", "Bug/Poison", "dllllllll"};

  team.push_back(bulbasaur);
  team.push_back(ivysaur);
  team.push_back(weedle);

  for (auto p : team) {
    launch(p);
  }

  evolve(bulbasaur);             // Mutated its attributes
  cout << bulbasaur.cry << endl; // Prints "Iiiiivy-saur"
}
```
