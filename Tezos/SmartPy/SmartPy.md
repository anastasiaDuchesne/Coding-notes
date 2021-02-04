# SmartPy

[TOC]

## History

| Incidence                                                    | Loss of funds in $    |
| ------------------------------------------------------------ | --------------------- |
| Infamous hack of [The DAO](https://hackingdistributed.com/2016/06/18/analysis-of-the-dao-exploit/) | $150,000,000          |
| [Bug in Parity’s Mulit-Sig Wallet exploited](https://cointelegraph.com/news/parity-multisig-wallet-hacked-or-how-come) | $154,000,000 (approx) |
| [dForce smart contracts drained](https://www.coindesk.com/attacker-drains-decentralized-protocol-dforce-of-25m-in-weekend-attack) | $25,000,000           |
| [dForce smart contracts drained](https://www.coindesk.com/attacker-drains-decentralized-protocol-dforce-of-25m-in-weekend-attack) | $25,000,000           |
| [bZx smart contracts attacked twice](https://cointelegraph.com/news/decentralized-lending-protocol-bzx-hacked-twice-in-a-matter-of-days) | $954,000              |

## Definitions

### Contract storage

Contract's personal database. Records the current state of the smart contract.

Once the smart-contract deployed, its storage becomes part of the "global storage" (=storage of all the contracts in the world)

### Entrypoints

Methods that can modify a contract's local storage. They can modify a contract's state by altering state variables values after the contract deployment.

### Smart contract state

Current status of the smart contract like a visual screenshot. Changes every time the contract does anything.

### State variables

Single slot in the contract storage = records the current state of the smart contract

*ex: name & money_in_all_accounts are state variables*

```python
bank_contract_storage = {
  'name': "World Bank"
  'money_in_all_accounts': 10000000
}
```

## Code

### Class

```python
class Name(sp.Contract):
	pass
```

### Initialization of the contract storage

```python
def __init__(self):
	self.init(<name> = "<value>")
```

1. `__init__` defines an initialization method for the class in which it is called during the contract origination
2. `self.init(<name> = "<value>")` assigns to "name" a state variable "value" and stores it inside the contract storage

### Testing environment

```python
​```python

​```
```
1. Init a testing environment:

```python
@sp.add_test(name=<name>)
def test():
    <code>
```
2. Add a new scenario

`sp.test_scenario`: functionality offered by `smartpy` library

```python
@sp.add_test(name=<name>)
def test():
    scenario = sp.test_scenario()
```

3. Simulate the init of a contract

```python
@sp.add_test(name=<name>)
def test():
    scenario = sp.test_scenario()
    <test_contract_var_name> = <Contract_Class_Name>
    scenario += <test_contract_var_name>
```

### Entrypoints

Add an entrypoint:

```python
@sp.entry_point
def <entrypoint_function_name>(self, <param_name>):
    self.data.<state_variable> = <param_name>
```

Everytime you need to access anything from the contract storage, you need to use `self.data` 

Testing an entrypoint:

```python
scenario += <contract_var_name>.<entrypoint_function_name>(<new_param>)
```

### Explicitly assign types

```python
# string
sp.string("...")

#boolean
sp.bool("true")
sp.bool("false")

#negative integers
sp.int(...)
#non-negative integers
sp.nat(...)

#maps
sp.map({...})
```

### Verify condition in tests

```python
scenario.verify(<condition>)
```

