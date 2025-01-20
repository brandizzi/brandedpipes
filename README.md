
# Branded Pipes

Branded Pipes is a Python library inspired by the `%>%` pipe operator from R's **dplyr** package.

### Installation

Install it using `pip`:

```bash
pip install brandedpipes
```

### Usage

To get started, import the `_` object:

```python
>>> from brandedpipes import _
>>> _ >> [2, 1, 3, 9, 8, 2]>> reversed  >> sorted  >> _
[1, 2, 2, 3, 8, 9]
>>> _ >> [2, 1, 3, 3, 2] >> set >> sum >> _
6

```

### Handling Functions with Multiple Parameters

If a function takes more than one parameter, you can refer to the current value using `_._`:

```python
>>> _ >> [2, 1, 9, 3, 5] >> max >> divmod(_._, 3) >> _
(3, 0)
>>> _ >> [1, 3] >> _._[1] >> _._ * 2 >> _
6

```

In case this syntax does not appeal to you, you may also call the pipe:

```python
>>> _ >> [2, 1, 9, 3, 5] >> max >> divmod(_(), 3) >> _
(3, 0)
>>> _ >> [1, 3] >> _()[1] >> _() * 2 >> _
6

```

### What if I Use `_` as a Variable Name?

No problem! Since [`_` is commonly used by many conventions in Python](https://docs.python.org/3/reference/lexical_analysis.html#reserved-classes-of-identifiers), the library also provides `__` as an alternative: 

```python
>>> from brandedpipes import __
>>> __ >> "plan 9" >> __._[4:] >> int >> __
9

```

For more flexibility, you can import the pipe operator with any name of your choice:

```python
>>> from brandedpipes import _ as P
>>> P >> "plan 9" >> P._[4:] >> int >> P
9

```

### Why Is It Called "Branded Pipes" if It Doesn’t Use Pipes?

Good question! It _does_ support pipes as well:

```python
>>> import math
>>> _| [-3, 0, 1] | sum | abs |_
2

```
