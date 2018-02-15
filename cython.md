# Cython talk

Can easily use other languages such as C, lua... in python
Can also import standardlib's function (`malloc`, etc.)

## Performances

Crazy.

Simply doing:
```python
%%cython
# your code below
```
 in ipython grants a 25% performances increase.


## Ranking

As for the differents possibilities about optimisation and
considering that raw Python code is the slowest (usually is.)

We have the following:

- Python
- Compiled
- ufunc
- numpy
- typed


## Syntax

Define variable using `cdef`

`%%cython` will create a lot of optimized code

Can include raw C code.

`cdef`
`cpdef`
`cimport`

## Future

Comprehensions into C++ containers?


# Personnal notes

Cython is therefore a really nice option when speed and performances are
starting to have to be taken in account in an application.

I don't think starting a program from scratch using Cython has an interest,
but I may be wrong.

Other alternatives:

Write program in lower level languages
**OR**
Write some parts of the program in lower languages.
i.e.:
- Rust
- C/C++
- Go
