---
layout: page
prev: structs
next: classes-2
---

# Classes

## Illustration

![Classes Model Real-World Entities: What it is & How it interacts with other entities](/class-illustration.svg)

## Syntax

```cpp
class Name {
  // attributes
  int number_field;
  int sometimes_called_properties;
  int or_fields;
  vector<string> or_attributes;

public:
  // attributes
  int count;

  // functions
  void public_member_function() { cout << "Hello"; }
  int sometimes_called_methods() { return number_field; }
  string longer_body(int count) {
    string out;
    for (int i = 0; i < count; ++i) {
      out += generate_string() + " ";
    }
    return out;
  }

private:
  // Turns back into private again below here
  int another_number;
  string generate_string() { return "Secret"; }
};

```

## Example

```cpp
class Pokemon {
public:
  // What it is
  int number;
  string name;
  string type;
  string cry;

  // What it does
  void print_cry() { cout << cry << endl; }
  void launch() { cout << "GO! " << name << ". " << cry << endl; }
};

int main() {
    Pokemon bulbasaur;
    bulbasaur.number = 1;
    bulbasaur.name = "Bulbasaur";
    bulbasaur.type = "Grass/Poison";
    bulbasaur.cry = "Bulbaaa";

    bulbasaur.print_cry(); // Bulbaaa
    bulbasaur.launch();    // Go Bulbasaur! Bulbaaa
}
```

## History

C++ was designed to be an enhanced C language, and included classes as one of its core features. [Wikipedia Link](https://en.wikipedia.org/wiki/C++)

## Classes Define Objects

1. **Object** — An code entity which encapsulates data and functions together.
1. **Class** — The definition of an object's data & functions. The class is a data type, like `int` or `struct`.

```cpp
class Tree {         // The Class
    int height;
    string genus;
    string species;
};

int main() {
    Tree tree;       // The object
    tree.height = 1; // Using the object
}

```

## Public & Private Keywords

- **Public** — Public data & functions can be accessed outside the class definition.
- **Private** — Private data & functions can only be accessed within the class definition.

## Example of `public` & `private` keywords

This Tree class uses a private variable to ensure that the tree's height can only increase by calling the `.grow()` function. This is about the programmer's _intention_, not a technical requirement.

```cpp
class Tree {
  // This attribute is private
  int height_in_meters = 0;

public:
  double grow_rate;

  void grow() { height_in_meters = 2 * (1 + grow_rate); }

  void print() {
    cout << "  ___  " << endl;
    cout << " /   \\ " << endl;
    cout << "|     |" << endl;
    cout << " \\___/ " << endl;
    for (int i = 0; i < height_in_meters; ++i) {
      cout << "   |  " << endl;
    }
    cout << "   |  " << endl;
    cout << "~~~~~~~~" << endl;
  }
};

int main() {
    Tree tree;
    tree.grow_rate = 0.5;

    cout << "Start" << endl;
    tree.print();

    // Tree grows!
    cout << "After Year 1" << endl;
    tree.grow();
    tree.print();

    // Tree grows!
    cout << "After Year 2" << endl;
    tree.grow();
    tree.print();
}
```

## Mutator & Accessor

- A **mutator** method changes the value of a class's data member. A **setter** is a subset of mutator which directly corresponds to a specific data member.
- An **accessor** method returns the value of a class's data member, but _does not change it_. A **getter** is a subset of accessor which directly corresponds to a specific data member. Usually marked `const`.

### `const`

Methods may be marked `const` to prevent the function from modifying the class at all. The compiler will enforce this. (This is different from returning a `const` data type.)

```cpp
class Example {
public:
// ...
  int get_num() const { return number; } // const goes after the parameter list
// ...
};
```

|          | Can it Modify a Class? | Does it Return a Value? | Does it Match a Single Property? | Usually `const`? |
| :------: | :--------------------: | :---------------------: | :------------------------------: | ---------------- |
| Accessor |           ✕            |           ✔︎           |                ✕                 | ✔︎              |
|  Getter  |           ✕            |           ✔︎           |               ✔︎                | ✔︎              |
| Mutator  |          ✔︎           |            ✕            |                ✕                 | ✕                |
|  Setter  |          ✔︎           |            ✕            |               ✔︎                | ✕                |

![Accessors are a superset of Getters, and Mutators are a superset of Setters](/mutator-accessor.svg)

## Example of Getter & Setter

This version of Pokemon class has a set of up to four moves. This setter prevents too many from being added, which would not be possible if the `.moves` data member was `public`, since the caller could simply use `.moves.push_back("another")`

```cpp
const int MAX_MOVES = 4;

class Pokemon {
public:
  int number;
  string name;
  string type;
  string cry;

  void print_cry() { cout << cry << endl; }
  void launch() { cout << "GO! " << name << ". " << cry << endl; }

  // New
  // Prevents more than 4 Moves from being added
  void set_move(int position, string move_name) {
    // Ignore invalid positions
    if (position < 0 || position > MAX_MOVES - 1) {
      return;
    }
    moves.at(position) = move_name;
  }

  string get_move(int position) const { // `const` ensures no mutations occur
    // Ignore invalid positions
    if (position < 0 || position > MAX_MOVES - 1) {
      return "";
    }
    return moves.at(position);
  }

private:
  // New
  vector<string> moves = {};
};
```

## Private Helper Function

A **private helper function** is simply a `private` function that is used within the class by other public or private methods.

```cpp
class RightTriangle {
    public:
        void set_base(double length) { base = length; }
        void set_height(double length) { height = length; }
        // Only concerned with "getting"
        double area() { return calculate_area(); }
    private:
        double base;
        double height;
        // Only concerned with "calculating"
        double calculate_area() {
            return (base * height) / 2
        };
};
```

## Class Property Initialization

Class data members can have a default value provided in the class definition.

If the property is **initialized** in the class, every object's data member will have the provided value when the object is declared.

```cpp

class Tree {
public:
    string genus;
    string species;
    double height_in_meters = 0; // initialized to 0

    // ...
};

int main() {
    Tree tree1;                           // height is 0
    Tree tree2 = {"Quercus", "rubra", 2}; // height is 2
    Tree tree3 = {"Quercus", "rubra"};    // height is 0
    tree1.height_in_meters = 100;         // height is 100
}
```

## Example Program: Toward a Pokémon Battle Clone

_Work in Progress_

```cpp

class Pokemon {

public:
  int number;
  string name;
  string type;
  string cry;

  void print_cry() { cout << cry << endl; }
  void launch() { cout << "GO! " << name << ". " << cry << endl; }
};

class PokemonTeam {

public:
  vector<Pokemon> team;

  // Print each Pokemon in the team with a number prefix
  void print() {
    for (int i = 0; i < team.size(); i++) {
      cout << i + 1 << ". " << team.at(i).name << endl;
    }
  }

  Pokemon get_user_pokemon_selection() {
    // Print
    print();

    // Accept input (integer)
    int user_selection;
    cin >> user_selection;

    // Return selection
    Pokemon selected_pokemon = team.at(user_selection - 1);
    return selected_pokemon;
  }
};

int main() {
  PokemonTeam brock;
  brock.team.push_back({1, "bulbasaur", "grass/poison", "bulbaaaaaaaa"}); // 1
  brock.team.push_back({13, "Weedle", "Bug/Poison", "dllllllll"});        // 2
  brock.team.push_back({2, "Ivysaur", "Grass/Poison", "Iiiiivy-saur"});   // 3
  brock.team.push_back({11, "Caterpie", "Bug", "cater-cater"});           // 4
  brock.team.push_back({4, "charmander", "fire", "char-char"});           // 5

  // Show menu & Launch
  Pokemon selected = brock.get_user_pokemon_selection();
  selected.launch();
  // Or
  brock.get_user_pokemon_selection().launch();
}
```
