🟢 Python math Module — Detailed Explanation

The math module provides mathematical functions and constants for performing numeric operations. It is part of Python’s standard library and works with floating-point numbers and integers.

⚠️ Note: For more advanced operations with arrays and vectors, use NumPy, but for basic math, the math module is sufficient.

🔹 1. Importing the math Module
import math

🔹 2. Constants in math
Constant	Description	Example
math.pi	π (pi) ≈ 3.14159	math.pi
math.e	Euler’s number ≈ 2.71828	math.e
math.tau	2π (tau) ≈ 6.28318	math.tau
math.inf	Positive infinity	math.inf
math.nan	Not-a-Number	math.nan
🔹 3. Numeric Functions
a) Absolute Value
x = -7
print(math.fabs(x))  # Output: 7.0


math.fabs() always returns a float. Use abs() for integers/floats.

b) Ceiling and Floor
print(math.ceil(4.2))   # Output: 5
print(math.floor(4.8))  # Output: 4


ceil(x) → smallest integer ≥ x

floor(x) → largest integer ≤ x

c) Rounding
print(math.trunc(4.9))  # Output: 4


math.trunc() truncates the decimal part, similar to typecasting to int.

d) Power and Square Root
print(math.pow(2, 3))   # Output: 8.0
print(math.sqrt(16))    # Output: 4.0


math.pow() always returns a float.

e) Exponential and Logarithmic Functions
print(math.exp(2))      # e^2 ≈ 7.389
print(math.log(8, 2))   # log base 2 of 8 = 3
print(math.log10(100))  # log base 10 = 2


exp(x) → e^x

log(x, base) → logarithm

log10(x) → base-10 logarithm

f) Trigonometric Functions
print(math.sin(math.pi/2))  # 1.0
print(math.cos(0))          # 1.0
print(math.tan(math.pi/4))  # 1.0


Input in radians.

Use math.radians(deg) and math.degrees(rad) for conversion.

math.radians(180)  # π
math.degrees(math.pi)  # 180

g) Hyperbolic Functions
print(math.sinh(0))   # 0.0
print(math.cosh(0))   # 1.0
print(math.tanh(0))   # 0.0

h) Factorial, GCD, and LCM
print(math.factorial(5))  # 120
print(math.gcd(24, 36))   # 12
print(math.lcm(12, 15))   # 60  (Python 3.9+)

i) Rounding Functions

math.isclose(a, b, rel_tol=1e-9) → Check approximate equality

math.isfinite(x) → True if x is not inf or NaN

math.isnan(x) → True if x is NaN

math.isinf(x) → True if x is infinite

j) Other Useful Functions
Function	Description
math.modf(x)	Returns fractional and integer parts as a tuple
math.fsum(iterable)	Accurate floating-point sum
math.prod(iterable)	Product of all elements (Python 3.8+)
math.comb(n, k)	Number of combinations (n choose k)
math.perm(n, k)	Number of permutations
🔹 4. Examples of Using math Module
import math

# Hypotenuse
a, b = 3, 4
c = math.hypot(a, b)  # 5.0
print(c)

# Rounding example
print(math.floor(7.8))  # 7
print(math.ceil(7.2))   # 8

# Logarithms
print(math.log(32, 2))  # 5

# Trigonometry
angle_deg = 45
angle_rad = math.radians(angle_deg)
print(math.sin(angle_rad))  # 0.7071067811865475

🔹 5. Summary

The math module provides fast, precise mathematical operations.

Includes constants, numeric functions, trigonometry, logarithms, and combinatorics.

Works with integers and floats, but not directly with complex numbers (use cmath for that).

✅ Tip: Use math module for mathematical precision instead of writing custom functions.