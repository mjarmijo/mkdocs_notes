## Links
[[python]]
[[OOP]]


## 3 Key Points



## Summary
- Similar to class methods, they are regular functions that live inside a class for organizational purposes
- They do not have access to self, cls, or instance attributes, but they can access class attributes
```python
class CurrencyConverter:
    rates = {  
        'EUR': 1.20,  # 1 EUR = 1.20 USD
        'JPY': 0.01   # 1 JPY = 0.01 USD
    } # Class attribute

    @staticmethod
    def to_usd(amount: float, code: str) -> float:
        if code not in CurrencyConverter.rates:
            raise ValueError(f"Invalid currency code: {code}")
        return amount * CurrencyConverter.rates[code]
    

print(f"100 EUR = {CurrencyConverter.to_usd(100, 'EUR')} USD")     # 120 USD
print(f"100 JPY = {CurrencyConverter.to_usd(100, 'JPY')} USD")     # 1 USD

```


## Further Reading


## Tags


2026-02-23-1859