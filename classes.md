# Classes

## Illustration

## Syntax

```cpp
class Pokemon {
    public:
        void setNumber(int n) {
            number = n;
        }
        void setName(string n) {
            name = n;
        }
        void setType(string t) {
            type = t;
        }
        void setCry(string c) {
            cry = c;
        }

        void print_cry() {
          cout << cry << endl;
        }

        void launch() {
          cout << "Go " << name << "! " << cry << endl;
        }

        void evolve() {
            if (number == 1) {
                number = 2;
                name = "Ivysaur";
                cry = "Iiiiivy-saur";
            }
            else if (number == 2) {
                number = 3;
                name = "Venusaur";
                cry = "veeeena-saur";
            }
            // Add other evolutions ...
            else {
                cout << "No Evolution" << endl;
            }
        }

    private:
        int number;
        string name;
        string type;
        string cry;
};

int main() {
    Pokemon bulbasaur;
    bulbasaur.setNumber(1);
    bulbasaur.setName("Bulbasaur");
    bulbasaur.setType("Grass/Poison");
    bulbasaur.setCry("Bulbaaa");

    bulbasaur.print_cry(); // Bulbaaa
    bulbasaur.launch();    // Go Bulbasaur! Bulbaaa

    // Mutates data members
    bulbasaur.evolve();

    bulbasaur.launch(); // Go Ivysaur! Iiiiivy-saur
}
```

## History

C++ was designed to be an enhanced C language, and included classes as one of its core features. [Wikipedia Link](https://en.wikipedia.org/wiki/C++)

## Terminology

### Object

An code entity which encapsulates data and functions together.

### Class

The definition of an object's data & functions. The class is a data type, like `int` or `struct`.

### Public

Public data & functions can be accessed outside the class definition.

### Private

Private data & functions can only be accessed within the class definition.

### Public Member Function (Method)

A **public member function** is a function in a class which is declared `public`. It is usually called a **method**.

### Private Data Members

A **private data member** is a property of a class which is not accessible outside the class definition.

### Scope Resolution Operator (`::`)

The **scope resolution operator** distinguishes entities by the location of their definition (library, namespace, class, etc.).

### Inline Member Function

An **inline member function** is a function in a class definition that is within the class declaration.

### Mutator

A **mutator** is a method which changes the value of a class's data member. A **setter** is a subset of mutator which directly corresponds to a specific data member.

### Accessor

An **accessor** is a method which returns the value of a class's data member. A **getter** is a subset of accessor which directly corresponds to a specific data member. Often declared `const`.

### Private Helper Function

A **private helper function** is a class's function which is not accessible outside the class definition (private). It is used within the class by other public or private methods.

## Usage

## Example Program: ??
