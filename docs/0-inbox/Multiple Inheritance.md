## Links
[[python]]
[[OOP]]

## 3 Key Points



## Summary
- A child class can also inherit methods and attributes from more than one parent, hence multiple inheritance
- This is generally considered an antipattern
```python
class Swimmer:
    def swim(self):
        print("Swimming")

class Flyer:
    def fly(self):
        print("Flying")

# Ducks inherits from both Swimmer and Flyer
class Duck(Swimmer, Flyer):
    pass
    
duck = Duck()
duck.swim() # Should print "Swimming"
duck.fly()  # Should print "Flying"
```
- Use `pass` to indicate we are not adding any new methods to Duck. It will automatically have the fly and swim methods
- Note that python's method resolution order (MRO) defaults to the first parent. So if one parent has a different `__init__` method, it may be ignored or modified. 
```python
class ElectronicDevice:
	def __init__(self, brand: str, model: str):
		self.brand = brand
		self.model = model
	def turn_on(self) -> None:
		print("Device is turning on")
	def turn_off(self) -> None:
		print("Device is turning off")

class HealthDevice:
	def __init__(self, brand: str, model: str, cost: int):
		self.brand = brand
		self.model = model
		self.cost = cost
	def measure_heart_rate(self) -> None:
		print("Measuring heart rate")

## This works but SmartWatch(ElectronicDevice, HealthDevice) would not inherit "cost" attribute  
class SmartWatch(HealthDevice, ElectronicDevice):
	pass

# Do not modify the code below
smart_watch = SmartWatch("Apple", "Watch Series 6")
smart_watch.turn_on()
smart_watch.measure_heart_rate()
smart_watch.turn_off()
print(smart_watch.cost)
```
- Most of the time multiple inheritance should not be used because it can lead to complexity and conflicts, but you may see it in a code base.  

## Further Reading

```python
class Hero:
	def __init__(self, name: str, power_level: int, health: int):
		self.name = name
		self.power_level = power_level
		self.health = health

	def use_power(self) -> str:
		return f"{self.name} uses their power!"

# TODO: Implement the FlightHero and StrengthHero classes
class FlightHero(Hero):
	def __init__(self, name: str, power_level: int, health: int, flight_speed: int):
		super().__init__(name, power_level, health)
		self.flight_speed = flight_speed

	def use_power(self) -> str:
		return f"{self.name} flies at {self.flight_speed} mph!"

class StrengthHero(Hero):
	def __init__(self, name: str, power_level: int, health: int, lifting_capacity: int):
		super().__init__(name, power_level, health)
		self.lifting_capacity = lifting_capacity
  
	def use_power(self) -> str:
		return f"{self.name} lifts {self.lifting_capacity} pounds!"

# Don't change the code below
flight_hero = FlightHero("Superman", 10, 100, 1000)
strength_hero = StrengthHero("Hulk", 10, 100, 1000)
print(flight_hero.name)
print(flight_hero.power_level)
print(flight_hero.health)
print(flight_hero.flight_speed)
print(flight_hero.use_power())
print(strength_hero.name)
print(strength_hero.power_level)
print(strength_hero.health)
print(strength_hero.lifting_capacity)
print(strength_hero.use_power())

```

## Tags


2026-02-28-0639