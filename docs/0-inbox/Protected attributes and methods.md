## Links

[python](python)
[oop](oop)

## 3 Key Points
- Use public methods/attributes to access protected methods/attributes
-  Protected (single underscore `_` ): Should only be accessed within class and subclasses



## Summary

- Protected attributes and methods should not be access from outside the class, but they can be access inside the class **and** it's children. They are still available outside the class but they should not be accessed directly.
- Define a protected attribute by prefixing the name with a single `_`. This is not enforced by the interpreter - it is a convention to warn developers not to use it directly. 
```python
class SuperHero:
    def __init__(self, name: str, power_level: int):
        self._name = name                # protected attribute
        self._power_level = power_level  # protected attribute

    def get_name(self) -> str: # public method
        return self._name

    def _some_protected_method(self) -> None: # protected method
        pass
        
    def some_public_method(self) -> None:
        self._some_protected_method()
```

- Access private attributes only via public methods
```python
spider_man = SuperHero("Spider-Man", 85)

print(spider_man._name)      # Allowed but discouraged
print(spider_man.get_name()) # Recommended

spider_man._some_protected_method() # Allowed but discouraged
spider_man.some_public_method()     # Recommended
```

## Further Reading


## Tags



2026-02-20-0653