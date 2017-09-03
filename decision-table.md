# Decision tables

The decision tables are organized by use case. Each decision table consists of a list of _conditions_ (marked with a "C" in the first column of the table) and a list of _actions_ (marked with an "A").

Each column apart from the first two constitute a rule. The condition for a rule can be:

* "Y" if the condition must be true for this rule to apply
* "N" if the condition must be false for the rule to apply
* "*" (asterisk) if the condition is irrelevant for this rule, i.e. it could be either true or false.

The action for a rule can be marked:

* "X" if the action is to be taken when the rule applies
* "-" if the action is not to be taken when the rule applies.

Note: Not all rules have to be implemented in the first version of the system.

## Use case: Take inventory

|   | Conditions and Actions | 1 | 2 | 3 | 4 | 5 | 6 | 7 |
|---|------------------------|---|---|---|---|---|---|---|
| C | Item type has minimum inventory level | N | Y | Y | * | * | * | * |
| C | Item quantity under minimum inventory level | * | N | Y | * | * | * | * |
| C | Item has expiry date | * | * | * | N | Y | Y | Y |
| C | Item near expiry date | * | * | * | * | N | Y | N |
| C | Item over expiry date | * | * | * | * | N | N | Y |
| A | Add item to shopping list | - | - | X | - | - | - | - | 
| A | Add item to _close to expiry_ list | - | - | - | - | - | X | - | 
| A | Advise user to discard expired item | - | - | - | - | - | - | X | 

## Use case: Add delivery to inventory

TODO

## Use case: Send order to supplier

TODO

## Use case: Check pending orders

TODO
