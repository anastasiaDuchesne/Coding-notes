# Quick study of FA1.2 template - Fungible assets

## init smart-contract
[[SmartPy#^1ebe27]]

```python
def __init__(self, **extra_storage):
        self.init(balances = sp.big_map(tvalue = sp.TRecord(approvals = sp.TMap(sp.TAddress, sp.TNat), balance = sp.TNat)), 
                totalSupply = 0, **extra_storage)
```

inits a contract storage with a big map that reprensents balances:
- total supply: 0
- trecord: 
	- approvals: record of address/value
	- balance

## Entrypoints
[[SmartPy#^78f607]]
### transfer


#SmartPy  #Tezos #Code #Python