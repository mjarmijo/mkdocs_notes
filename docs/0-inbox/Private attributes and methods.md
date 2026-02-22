## Links
[Protected attributes and methods](Protected%20attributes%20and%20methods.md)

## 3 Key Points
Private methods:
-  should not be directly accessed using normal dot notation from outside the class.
- are meant to be used only within the defining class itself.
-  provides the strongest form of information hiding in Python. Use for sensitive info. But remember private attributes can still be accessed!! 

## Summary
- **Private** attributes and methods are prefixed with a double underscore `__` and should not be accessed from outside the class.  Use these for sensitive info. 
- Private attributes are not accessible from child classes, but protected attribute are accessible from children
```python
class SuperHero:
    def __init__(self, name: str, power_level: int):
        self.__name = name                # private attribute
        self.__power_level = power_level  # private attribute

    # private method
    def __secret_power(self) -> str:
        return f"Using {self.__name}'s secret power!"

    # public method to access private method
    def use_power(self) -> str:
        return self.__secret_power()

    # public method to access private attribute
    def get_power_level(self) -> int:
        return self.__power_level
```

- Use public methods to access private methods and attributes
- 
## Further Reading


## Tags


2026-02-21-0638