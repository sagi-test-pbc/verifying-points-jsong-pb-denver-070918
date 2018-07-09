
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
    x = FieldElement(x_raw, prime)
    y = FieldElement(y_raw, prime)
    # try initializing, RuntimeError means not on curve
    # p = Point(x, y, a, b)
    try:
        p = Point(x, y, a, b)
        print('({},{}) is on the curve'.format(x_raw, y_raw))
    except RuntimeError:
        print('({},{}) is not on the curve'.format(x_raw, y_raw))
```
