---
next: streams.md
---

# Streams

---

## Metaphors

- **Email Inbox:** There is something in there now, and more may be added later. You can observe the stream to see new emails.
- **Water Pipe:** The pipe represents a future flow of water. Water flows out of a supply pipe or flows into a drain pipe.

---

## Operators

- `<<` — Insertion `cout << "data"`
- `>>` — Extraction `cin >> variable`

---

## Buffers

Where does the content go once it is inserted into a stream? _Into a Buffer_

Is the programmer in control of flushes? _No_

## Some Stream Instances

| Name            | Type   | Example                         |
| --------------- | ------ | ------------------------------- |
| `cin`           | Input  | Keyboard Input                  |
| `ifstream`      | Input  | File                            |
| `ostringstream` | Output | Creating a string incrementally |
| `cout`          | Output | Console Screen                  |

## Manipulators

Affect how the insertion `<<` and extraction `>>` operators work.

Manipulators work by overloading the `<<` &`>>` operators.

### Decimal Manipulators

See [zyBook Table 10.2.1: Floating-point manipulators](https://learn.zybooks.com/zybook/HARDINGCOMP1510McCownSpring2025/chapter/10/section/2?content_resource_id=108375002)

### Text Manipulators

See [zyBook Table 10.2.2: Text-alignment manipulators](https://learn.zybooks.com/zybook/HARDINGCOMP1510McCownSpring2025/chapter/10/section/2?content_resource_id=108375008)

### Exercise

```
Table of Contents

1. Alphabet..................10
2. Numbers...................15
3. Biographies...............25
4. Theory of Everything......50
5. Conclusion..............1000

Index......................1001
```

- Page numbers are aligned in their final digit
- Each line is 30 characters wide
- Empty lines after "Table of Contents" and before "Index"

## Buffer Manipulators

See [zyBook Table 10.2.3: Buffer manipulators](https://learn.zybooks.com/zybook/HARDINGCOMP1510McCownSpring2025/chapter/10/section/2?content_resource_id=108375012)
