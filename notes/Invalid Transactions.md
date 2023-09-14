---
id: fdijtxmof3yplp6508bmfnu
title: invalid transactions
desc: ''
updated: 1694712021537
created: 1694692445037
---

_thought: "could named tuples or objects simplify the code?"_
```python
class Solution:
    def invalidTransactions(self, transactions: List[str]) -> List[str]:
        class Transaction:
            def __init__(self, txn_str):
                self.name, s_time, s_amount, self.loc = txn_str.split(',')
                self.time = int(s_time)
                self.amount = int(s_amount)
        
        t_transactions = []

        for txn_str in transactions:
            t_transactions.append(Transactions(txn_str))
```
