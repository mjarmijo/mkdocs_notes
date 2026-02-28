## Links
[[python]]
[[OOP]]

## 3 Key Points



## Summary
-  Inheritance allows you to create one class from another
-  The new class is known as the child class, the original is the parent class/super class
-  The child inherits properties and methods from the parent/super. It enables code reuse and allows us to expand an existing class.

```python
class Superhero:
    def __init__(self, name: str, power: str):
        self.name = name
        self.power = power

class Avenger(Superhero):
    def fly(self) -> None:
        print(f"{self.name} can fly using {self.power}")

iron_man = Avenger("Iron Man", "repulsor beams")
iron_man.fly() # Iron Man can fly using repulsor beams
```

- Avenger inherits the superhero name and power attributes, and expands them with a fly method. 
- The constructor `__init__` of the parent class is called when an instance of the child class is created. 
- 
## Further Reading


## Tags


2026-02-26-2136