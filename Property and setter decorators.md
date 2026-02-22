## Links
[Python OOP](Python%20OOP.md)
[Getter and setter methods](Getter%20and%20setter%20methods.md)
## 3 Key Points



## Summary
- Use decorators `@property` and `@setter` for the most pythonic way of using getters and setters. 
```python
class Hero:
    def __init__(self, name: str):
        self.__name = name    # private attribute

    # Getter
    @property
    def name(self) -> str:
        return self.__name

    # Setter
    @name.setter
    def name(self, new_name: str) -> None:
        if new_name != "":
            self.__name = new_name
        else:
            print("Name cannot be empty!")
```

- The property `__name` is still private, but the getter and setter method are not
- Use the decorates because it makes code cleaner/less verbose. 

```python
class SuperHero:

def __init__(self, name: str, health: int, power_level: int):
	self.name = name
	self.__health = health
	self.__power_level = power_level

@property
def health(self) -> int:
	return self.__health

@property
def power_level(self) -> int:
	return self.__power_level

@health.setter
def health(self, health: int) -> None:
	if health < 0:
	print("You can't set the health to less than 0")
	elif health > 100:
	print("You can't set the health to more than 100")
	else:
	self.__health = health

@power_level.setter
def power_level(self, power_level: int) -> None:
	if power_level < 1:
	print("You can't set the power level to less than 1")
	elif power_level > 10:
	print("You can't set the power level to more than 10")
	else:
	self.__power_level = power_level


super_hero = SuperHero("Batman", 80, 9)
print(super_hero.health) # this should print 80
super_hero.health = 110 # this should print You can't set the health to more than 100
print(super_hero.power_level) # this should print 9
super_hero.power_level = 100 # this should print You can't set the power level to more than 10
super_hero.power_level = 0 # this should print You can't set the power level to less than 1

print(f"{super_hero.name} has {super_hero.health} health and {super_hero.power_level} power level")
```
## Further Reading


## Tags


2026-02-21-0705