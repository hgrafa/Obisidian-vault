
- Wrappers
- Embrulhadores de funções
- [[High Orders Functions (HOFs)]]

```python
from functools import cache

def foo(a, b):
	return a*a + b/2
	
@cache
def cached_foo(a, b):
	return a*a + b/2
```

## Com Cache decorator

```python
print(
	  foo(2, 2), foo(4, 4),
	  foo(2, 2), foo(4, 4)
)
```

```bash
$ time python decorators.py
5 18 5 18

real    0m0.114s
```

## Sem Cache decorator

```python
print(
	  cached_foo(2, 2), cached_foo(4, 4),
	  cached_foo(2, 2), cached_foo(4, 4)
)
```

```bash
$ time python decorators.py
5.0 18.0 5.0 18.0

real    0m0.068s
```