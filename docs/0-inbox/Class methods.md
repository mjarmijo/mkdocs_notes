## Links
[[python]]
[[oop]]

## 3 Key Points



## Summary
-  Class methods work with the entire class, not the individual instance. We may want to update the training level of all superheros at once in the for the superhero instances we created earlier. 
- Class methods are shared by all instances of the class, they do not use the `self` keyword because they do not have access to the instance attributes. 
- Instead of `self`, class methods use the `cls` parameter  for access, and the `@classmethod` decorator
```python
class Superhero:
    training_level = 1  # Class attribute

    def __init__(self, name: str, power: str):
        self.name = name         # Instance attribute
        self.power = power       # Instance attribute

    @classmethod
    def upgrade_training(cls) -> None:
        cls.training_level += 1
        print(f"All heroes now at training level {cls.training_level}")
        
Superhero.upgrade_training()     # Recommend way to use class method
print(Superhero.training_level)  # 2
```

```python
class Library:
books_available = 100 # Total books in library

@classmethod
def lend_books(cls, number: int) -> None:
cls.books_available -= number

@classmethod
def return_books(cls, number: int) -> None:
cls.books_available += number
```
## Further Reading


## Tags


2026-02-23-1700