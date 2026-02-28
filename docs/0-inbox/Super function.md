## Links
[[python]]
[[OOP]]

## 3 Key Points



## Summary
-  Super is a built-in function that allows you to  call methods from the parent class
-  Sometimes we need to extend, and not replace the parent behavior such as adding extra steps to the initialization `__init__` method, access parent  class properties, or add functionality to a method.
- `Super()`doesn't take any arguments, it is just used to call parent class properties and methods. 

```python
class ParentClass:
    def parent_method(self) -> None:
        print("This is the parent class method")

class ChildClass(ParentClass):
    def child_method(self) -> None:
        super().parent_method()
        print("This is the child class method")
        
## Syntax
super().parent_method() # Call parent class's instance method

super().__init__() # Call parent class __init__ method

super().parent_property # Access parent class property
```

```python
class SuperHero:
	def __init__(self, name: str, power: str):
		self.name = name
		self.power = power

	def attack(self) -> None:
		print(f"{self.name} is attacking with {self.power}")

class Avenger(SuperHero):
	def __init__(self, name: str, power: str, team: str):
		super().__init__(name, power)
		self.team = team

# Don't change the code below
avenger = Avenger("Iron Man", "repulsor beams", "Avengers")
print(avenger.name)
print(avenger.power)
print(avenger.team)
avenger.attack()
```

## Further Reading


## Tags


2026-02-27-0901