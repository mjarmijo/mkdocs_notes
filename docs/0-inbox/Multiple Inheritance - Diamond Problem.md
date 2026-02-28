## Links
[[python]]
[[OOP]]
[Multiple Inheritance](Multiple%20Inheritance.md)


## 3 Key Points



## Summary
```python
class A:
    def print_method(self) -> None:
        print("A")

class B(A):
    def print_method(self) -> None:
        print("B")

class C(A):
    def print_method(self) -> None:
        print("C")

class D(B, C):
    pass

d = D()
d.print_method()  # Which method will be called? (B)
```

This inheritance structure creates a diamond shape, as illustrated below:

```text
   A
  / \
 B   C
  \ /
   D
```

Python uses Method Resolution Order (MRO) to determine which method to call when dealing with multiple inheritance. Here's how it works:

- First, Python looks for the method in the current class `D`
- If not found, it checks the first parent class `B` as it is the first parent class passed to the `D` class
- Then the second parent class `C` as it is the second parent class passed to the `D` class
- Finally, it checks the base class `A`

You can view this order using the `__mro__` attribute:

```python
print(D.__mro__)
# Output: [<class '__main__.D'>, <class '__main__.B'>, <class '__main__.C'>, <class '__main__.A'>, <class 'object'>
```

The MRO is `[D, B, C, A]`.
## Further Reading


## Tags


2026-02-28-0656