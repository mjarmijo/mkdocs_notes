## Tags
[[python]]
[[oop]]
[Private attributes and methods](Private%20attributes%20and%20methods.md)
[Public attribute and methods](Public%20attribute%20and%20methods.md)

## 3 Key Points
- Public attributes are accessible everywhere


## Summary
- public attributes and methods can be used or modified from outside the class, by default all are public

```python
class SuperHero:
    def __init__(self, name: str, power_level: int):
        self.name = name                # public attribute
        self.power_level = power_level  # public attribute

    # Public method
    def display_power_level(self) -> None:
        print(f"{self.name} has a power level of {self.power_level}")
```

- When a method or attribute is public we can access it via dot notation, modify it or call it from outside the class

```python
# Creating a superhero
spider_man = SuperHero("Spider-Man", 85)

# Accessing public attributes/methods
print(spider_man.name)
spider_man.display_power_level()

# Modifying public attributes
spider_man.power_level = 90
```



## Further Reading


## Links:



2026-02-20-0639