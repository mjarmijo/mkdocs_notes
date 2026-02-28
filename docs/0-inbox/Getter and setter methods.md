## Links
[OOP](OOP.md)
[Getter and setter methods](Getter%20and%20setter%20methods.md)
## 3 Key Points
- getter and setters often include validation to make sure private/protected methods are not set to invalid values
- names always begin with get/set_attribute

## Summary
- Methods that get/set a value of a private/protected method. 
```python
class SuperHero:
    def __init__(self, name: str, power_level: int):
        self.__name = name                # private attribute
        self.__power_level = power_level  # private attribute

    # Getter method to get power_level
    def get_power_level(self) -> int:
        return self.__power_level
        
	def set_power_level(self, new_level: int) -> None:  # Setter method to set power_level
	    if 0 <= new_level <= 100:          # validation
	        self.__power_level = new_level
	    else:
	        print("Power level must be between 0 and 100!")

```

- Includes validation to make sure we never set a private method to an invalid value. We could also raise an error like `raise ValueError("Power level must be between 0 and 100)` instead of printing an error
-  always use the name get_(attribute) and set(attribute) for getter and setter methods

## Further Reading


## Tags


2026-02-21-0651