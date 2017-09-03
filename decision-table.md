# Decision tables

The decision tables are organized by use case. Each decision table consists of a list of _conditions_ (marked with a "C" in the first column of the table) and a list of _actions_ (marked with an "A").

Each column apart from the first two constitute a rule. The condition for a rule can be:

* "Y" if the condition must be true for this rule to apply
* "N" if the condition must be false for the rule to apply
* blank/unmarked if the condition is irrelevant for this rule, i.e. it could be either true or false.

The action for a rule can be marked:

* "X" if the action is to be taken when the rule applies
* blank/unmarked if the action is not to be taken when the rule applies.

Note: Not all rules have to be implemented in the first version of the system. Rules that are not going to be implemented have their numbers put in parentheses, e.g. "(5)".

## Use case: Take inventory

Rules are applied for each updated item.

|   | Conditions and Actions | 1 | 2 | 3 | (4) | (5) | (6) | (7) |
|---|------------------------|---|---|---|-----|-----|-----|-----|
| C | Item type has minimum inventory level | N | Y | Y | | | | |
| C | Item quantity under minimum inventory level | | N | Y | | | | |
| C | Item has expiry date | | | | N | Y | Y | Y |
| C | Item near expiry date | | | | | N | Y | |
| C | Item over expiry date | | | | | N | N | Y |
| A | Add item to shopping list | | | X | | | | | 
| A | Add item to _close to expiry_ list | | | | | | X | | 
| A | Advise user to discard expired item | | | | | | | X | 

## Use case: Add delivery to inventory

Rules are applied for each item in the delivery as it is added to the inventory.

|   | Conditions and Actions | 1 | 2 | 3 | 4 | 5 |
|---|------------------------|---|---|---|---|---|
| C | Item was ordered | N | Y | Y | Y | |
| C | Quantity matches order | | N | Y | Y | |
| C | Quantity is too large or too small | | Y | N | N | |
| C | Price matches price list | | Y | Y | N | |
| C | Quality is ok | Y | Y | Y | Y | N |
| A | Add item to complaints | X | X | | X | X |
| A | Update item quantity in inventory | X | X | X | X | |
| A | Return/discard item | | | | | X |

After all items in the delivery have been processed, the following rules are applied.

|   | Conditions and Actions          | 1 | 2 | 3 | 4 | 5 | 6 | 7 | 8 |
|---|---------------------------------|---|---|---|---|---|---|---|---|
| C | All items from order delivered? | N | N | N | N | Y | Y | Y | Y |
| C | Any complaints?                 | N | N | Y | Y | N | N | Y | Y |
| C | Order prepaid?                  | N | Y | N | Y | N | Y | N | Y |
| A | Pay delivered items             | X |   | X |   | X |   | X |   |
| A | Contact supplier                | X | X | X | X |   |   |   | X |


## Use case: Place order

TODO

## Use case: Check pending orders

TODO
