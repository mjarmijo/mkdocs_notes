## Links
[[python]]
[[OOP]]


## 3 Key Points



## Summary
- Method overriding allows you to change the behavior of an inherited function in the child class
```python
class Superhero:
    def __init__(self, name: str):
        self.name = name

    def fight(self) -> None:
        print("Superhero fights with advanced weapons!")

class Avenger(Superhero):
    # Override the fight method
    def fight(self) -> None:
        print("Avenger fights with advanced weapons!")
```



## Further Reading


## Tags


2026-02-27-0855