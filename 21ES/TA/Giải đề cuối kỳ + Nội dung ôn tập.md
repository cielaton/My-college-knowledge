**Problem 1**: Define class Vehicle having the following members:
- Variables ID (natural number), name (string), weight (kilogram), accessors and mutators for all the variables.
- Constructor accepts some arguments, it throws an exception if one of the following cases happens: ID is negative; weight is negative; name is empty.
- Operator (\=\=) compares two vehicles if their weight are equal.
Define class Car inherits from class Vehicle. It has the following member:
- Variable nbSeats (an integer), accessor and mutator for this variable. Mutator throws an exception if nbSeats is negative.
- Constructor throws an exception if nbSeats is negative.
Write tg