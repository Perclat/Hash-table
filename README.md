# Hash Tables

This repository contains a minimal implementation of a <i>hash table</i> in Python using separate chaining for collision handling. The <i>H</i> class is designed to demonstrate the basic functionality of hash tables with very compact naming conventions, where all variable and method names are reduced to single-letter identifiers for simplicity and minimalism. Inside the class, the <i>init</i> method initializes the table with a fixed size, the <i>_h</i> method computes the hash index for a given key using Python’s built-in <i>hash()</i> function modulo the table size, the <i>i</i> method inserts key-value pairs at the computed index, and the <i>f</i> method searches for a value by its key. Keys are stored as strings representing hashes, and values represent categories such as <i>Trojan</i>, <i>Rootkit</i>, or <i>Bootkit</i>. The example usage shows how to create a table, insert elements, and perform lookups, returning either the stored value if the key exists or <i>None</i> if the key is not found. This repository is intended as an educational example to show the mechanics of hashing and collision resolution in Python, highlighting how simple structures can be reduced to their essential form while remaining functional and clear.

## Native implementation in Python

```python
class H:
    def __init__(s, n):
        s.n = n
        s.t = [[] for _ in range(n)]

    def _h(s, k):
        return hash(k) % s.n

    def i(s, k, v):
        idx = s._h(k)
        s.t[idx].append((k, v))

    def f(s, k):
        idx = s._h(k)
        for x, y in s.t[idx]:
            if x == k:
                return y
        return None


# create a hash table and insert some key-value pairs:
h = H(n=10)
h.i("d41d8cd98f00b204e9800998ecf8427e", "Trojan")
h.i("098f6bcd4621d373cade4e832627b4f6", "Rootkit")
h.i("1f0e3dad99908345f7439f8ffabdffc4", "Bootkit")

# search for values using keys:
print(h.f("d41d8cd98f00b204e9800998ecf8427e"))
print(h.f("098f6bcd4621d373cade4e832627b4f6"))
print(h.f("1f0e3dad99908345f7439f8ffabdffc4"))
print(h.f("c4ca4238a0b923820dcc509a6f75849b"))
``` 

```text
Output:
Trojan
Rootkit
Bootkit
None
```

## References

- <i>Paul A. Gagniuc. Antivirus Engines: From Methods to Innovations, Design, and Applications. Cambridge, MA: Elsevier Syngress, 2024. pp. 1-656.</i>

***

