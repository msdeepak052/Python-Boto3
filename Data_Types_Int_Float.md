# Int and Float Data Types
---

## 🔢 `int` – Integer Numbers

Used to represent **whole numbers**.

```python
cpu_cores = 4
instance_count = int("5")  # convert from string
```

---

## 🌊 `float` – Floating Point Numbers

Used for **decimal values**.

```python
cpu_utilization = 78.5
price = float("42.75")
```

---

## 📚 Common Inbuilt Functions for `int` and `float`

---

### ✅ 1. `type()`

Get the data type.

```python
print(type(5))          # <class 'int'>
print(type(3.14))       # <class 'float'>
```

---

### 🔄 2. `int()` & `float()` – Type Conversion

```python
x = "100"
print(int(x))           # 100

y = "98.6"
print(float(y))         # 98.6
```

✔️ **Use case:** Reading numeric input from JSON, files, or CLI (which are strings by default).

---

### ➕ 3. Arithmetic Operations

```python
a = 10
b = 3
print(a + b)    # 13
print(a - b)    # 7
print(a * b)    # 30
print(a / b)    # 3.333...
print(a // b)   # 3   (floor division)
print(a % b)    # 1   (modulo)
print(a ** b)   # 1000 (exponentiation)
```

✔️ Use in **resource allocation**, **percentages**, **threshold checks**, etc.

---

### 🧠 4. `abs()`, `round()`

```python
print(abs(-20))         # 20 (absolute value)
print(round(3.1415, 2)) # 3.14 (rounded to 2 decimal places)
```

✔️ **Use case:** Round metrics like CPU or disk usage, or clean negative deltas.

---

### 🧮 5. `pow(x, y)` – Power Calculation

```python
print(pow(2, 4))  # 16 (2^4)
```

Equivalent to `2 ** 4`, but `pow()` is a built-in function.

---

### ⬆️ 6. `max()`, `min()` – Find Extremes

```python
values = [23, 17, 89, 45]
print(max(values))  # 89
print(min(values))  # 17
```

✔️ **Use case:** Get peak usage, highest memory, longest duration from a list.

---

### 📏 7. `sum()` – Add All Values

```python
usage = [20.5, 30.0, 49.5]
print(sum(usage))  # 100.0
```

✔️ **Use case:** Total CPU or memory used across multiple nodes.

---

### 🚨 8. `is_integer()` (for `float` only)

```python
val = 5.0
print(val.is_integer())  # True
```

✔️ Helps determine if a float is equivalent to an integer.

---

## 💼 DevOps Examples

### ✅ Validate Number of EC2 Instances

```python
instance_str = "3"
instances = int(instance_str)
if instances > 0:
    print("Instances to launch:", instances)
```

---

### ✅ Calculate Resource Thresholds

```python
cpu_util = 87.6
threshold = 80.0

if cpu_util > threshold:
    print("Scale up: CPU is above threshold!")
```

---

### ✅ Round Off Costs

```python
cost = 12.9765
print("Monthly cost:", round(cost, 2))  # Monthly cost: 12.98
```

---

## 🔚 Summary Table

| Function        | Purpose                         | Example                     |
| --------------- | ------------------------------- | --------------------------- |
| `int()`         | Convert to integer              | `int("5")` → `5`            |
| `float()`       | Convert to float                | `float("3.14")` → `3.14`    |
| `abs()`         | Absolute value                  | `abs(-10)` → `10`           |
| `round()`       | Round float                     | `round(3.456, 2)` → `3.46`  |
| `pow(x, y)`     | Power of x to y                 | `pow(2, 3)` → `8`           |
| `max()`/`min()` | Largest / smallest from list    | `max([2, 5])` → `5`         |
| `sum()`         | Sum of list                     | `sum([1, 2, 3])` → `6`      |
| `is_integer()`  | Checks if float is integer-like | `5.0.is_integer()` → `True` |

---
