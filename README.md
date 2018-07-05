
# Verifying Points on a Curve


```python
# Verify curve Example

prime = 137
x, y = 73, 128

print(y**2 % prime == (x**3 + 7) % prime)
```

### Try it

Find out which points are valid on the curve \\( y^2 = x^3 + 7: F_{223} \\)

```
(192,105), (17,56), (200,119), (1,193), (42,99)
```


```python
from ecc import FieldElement, Point

prime = 223
a = FieldElement(0, prime)
b = FieldElement(7, prime)

points = ((192,105), (17,56), (200,119), (1,193), (42,99))

# iterate over points
for x_raw, y_raw in points:
    # Initialize points this way:
    # x = FieldElement(x_raw, prime)
    # y = FieldElement(y_raw, prime)
    # try initializing, RuntimeError means not on curve
    # p = Point(x, y, a, b)
```

### Test Driven Exercise


```python
# from ecc import FieldElement, Point

# class Point(Point):

#     def __init__(self, x, y, a, b):
#         self.a = a
#         self.b = b
#         self.x = x
#         self.y = y
#         # x being None and y being None represents the point at infinity
#         # Check for that here since the equation below won't make sense
#         # with None values for both.
#         if self.x is None and self.y is None:
#             return
#         # make sure that the elliptic curve equation is satisfied
#         # y**2 == x**3 + a*x + b
#         if self.y**2 != self.x**3 + a*x + b:
#         # if not, throw a RuntimeError
#             raise RuntimeError('({}, {}) is not on the curve'.format(self.x, self.y))
```
