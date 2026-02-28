## Links

[[python]]
[[oop]]

## 3 Key Points



## Summary
- class attributes share info across all instances of a class
- Instance attributes a specific to that particular instance of a class
- We don't need `self` to access class attributes. They should be declared within the class, but not as part of init or other methods
- Use the Class name, not instance name to access the class attributes, i.e. `Superhero.hero_count`
- You can update them outside of the class, too. 

```python
class SmartDevice:
# Add your class attributes here
total_devices = 0
active_devices = 0

def __init__(self, name: str):
self.name = name
SmartDevice.total_devices += 1 # Each new device adds to total
# Implement these methods
def turn_on(self) -> None:
SmartDevice.active_devices += 1

def turn_off(self) -> None:
SmartDevice.active_devices -= 1
```


## Further Reading


## Tags


2026-02-22-1553