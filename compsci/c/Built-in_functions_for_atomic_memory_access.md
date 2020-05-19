# [Built-in functions for atomic memory access](https://gcc.gnu.org/onlinedocs/gcc-4.1.1/gcc/Atomic-Builtins.html)

Using a semaphore requires an atomic operation, so that a deadlock cannot occur. The **Intel Itanium Processor-specific Application Binary Interface** specifies some built-ins that are atomic operations...
There are built-ins for a few functionalities, but these are the most imporant:

- add, sub, or, and, xor, nand
- compare and swap

The first of the two can be called in **gcc** by using the following built-in functions:

- Type 1:
	- `type __sync_fetch_and_add(type *ptr, type value, ...)`
	- `type __sync_fetch_and_sub (type *ptr, type value, ...)`
	- `type __sync_fetch_and_or (type *ptr, type value, ...)`
	- `type __sync_fetch_and_and (type *ptr, type value, ...)`
	- `type __sync_fetch_and_xor (type *ptr, type value, ...)`
	- `type __sync_fetch_and_nand (type *ptr, type value, ...)`
- Type 2:
	- `type __sync_add_and_fetch (type *ptr, type value, ...)`
	- `type __sync_sub_and_fetch (type *ptr, type value, ...)`
	- `type __sync_or_and_fetch (type *ptr, type value, ...)`
	- `type __sync_and_and_fetch (type *ptr, type value, ...)`
	- `type __sync_xor_and_fetch (type *ptr, type value, ...)`
	- `type __sync_nand_and_fetch (type *ptr, type value, ...)`

Type 1 and 2 are only different in the sense, that Type 1 returns the value that had previously been in memory, and Type 2 returns the new value.

The second of the two are atomic operations for comparing and swapping 

- Type 1:
	- `bool __sync_bool_compare_and_swap (type *ptr, type oldval, type newval, ...)`
- Type 2:
	- `type __sync_val_compare_and_swap (type *ptr, type oldval, type newval, ...)`

These functions take 3 arguments:

- a pointer `ptr` to the value that needs changing
- a value `oldval` which is the value before the swap
- and a value `newval` which is the new value after swapping

These functions compare the current value of `ptr` to `oldval` and if they are the same, `newval` is being written to `ptr`...
The two types are different in the way that the first type returns a `bool` if the comparison is successful and `newval` is written into `ptr` and the second type returns the content of `ptr` before the operation.
