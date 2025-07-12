## First Hello World Python Script

```python
print("Hello, World!")
```

<img width="911" height="140" alt="image" src="https://github.com/user-attachments/assets/56599da9-f274-453d-85af-29a7ac6429ae" />

---

## Python Data Types

---

## 🔢 **1. Numeric Types**

### a) `int` (Integer)

Whole numbers, positive or negative.

```python
x = 10
y = -25
print(type(x))  # <class 'int'>
```

### b) `float` (Floating point number)

Decimal numbers.

```python
pi = 3.1415
salary = 9999.99
print(type(pi))  # <class 'float'>
```

### c) `complex` (Complex numbers)

Numbers with a real and imaginary part.

```python
z = 2 + 3j
print(z.real, z.imag)  # 2.0 3.0
```

---

## 🔤 **2. `str` (String)**

Sequence of characters enclosed in `' '` or `" "`.

```python
name = "Deepak"
greeting = 'Hello!'
print(name.upper())     # DEEPAK
print(greeting[0])      # H
```

---

## ✅ **3. `bool` (Boolean)**

Only two values: `True` or `False`. Often used in conditions.

```python
is_active = True
is_logged_in = False
print(5 > 3)  # True
```

---

## 📦 **4. `list` (Ordered, Mutable Collection)**

Can contain elements of any data type, including other lists.

```python
fruits = ['apple', 'banana', 'cherry']
fruits.append('mango')
print(fruits[1])  # banana
```

---

## 📚 **5. `tuple` (Ordered, Immutable Collection)**

Similar to lists but **cannot be modified**.

```python
dimensions = (1920, 1080)
print(dimensions[0])  # 1920
```

---

## 🔑 **6. `dict` (Dictionary)**

Key-value pairs. Keys must be unique.

```python
person = {
    "name": "Deepak",
    "age": 30,
    "is_admin": True
}
print(person["name"])  # Deepak
```

---

## 📋 **7. `set` (Unordered, Unique Elements)**

No duplicates, and order is not guaranteed.

```python
colors = {"red", "green", "blue"}
colors.add("red")   # No effect; already exists
print(colors)
```

---

## 🚫 **8. `NoneType`**

Represents the absence of a value.

```python
result = None
print(type(result))  # <class 'NoneType'>
```

---

## 🧪 Bonus: Type Checking & Conversion

```python
x = 5
print(type(x))  # int

# Convert int to float
y = float(x)   # 5.0

# Convert string to int
z = int("123")  # 123
```

---

## Summary Table:

| Type       | Example              | Description                   |
| ---------- | -------------------- | ----------------------------- |
| `int`      | `42`, `-1`           | Whole numbers                 |
| `float`    | `3.14`, `-0.99`      | Decimal numbers               |
| `complex`  | `2 + 3j`             | Complex numbers               |
| `bool`     | `True`, `False`      | Boolean logic                 |
| `str`      | `"Deepak"`, `'abc'`  | Textual data                  |
| `list`     | `[1, "a", 3.0]`      | Ordered, mutable collection   |
| `tuple`    | `(1, 2)`             | Ordered, immutable collection |
| `dict`     | `{"name": "Deepak"}` | Key-value pairs               |
| `set`      | `{"a", "b", "c"}`    | Unique unordered elements     |
| `NoneType` | `None`               | Represents null / no value    |

---

## 🧵 Python `str` Inbuilt Methods – with Examples & Use Cases

Below is a categorized list of **common and DevOps-relevant** string methods:

---

### ✅ **1. Basic String Info**

| Method                    | Description                        | Example                                           |
| ------------------------- | ---------------------------------- | ------------------------------------------------- |
| `.lower()`                | Converts to lowercase              | `'HOSTNAME'.lower()` → `'hostname'`               |
| `.upper()`                | Converts to uppercase              | `'devops'.upper()` → `'DEVOPS'`                   |
| `.capitalize()`           | Capitalizes first character        | `'server down'.capitalize()` → `'Server down'`    |
| `.title()`                | Capitalizes every word             | `'disk space full'.title()` → `'Disk Space Full'` |
| `.strip()`                | Removes whitespace (start & end)   | `'  log.txt  '.strip()` → `'log.txt'`             |
| `.lstrip()` / `.rstrip()` | Removes whitespace from left/right | `'   file  '.lstrip()` → `'file  '`               |

---

### 🔍 **2. Search and Match**

| Method               | Description                              | Example                                           |
| -------------------- | ---------------------------------------- | ------------------------------------------------- |
| `.startswith('str')` | Checks if string starts with             | `'ERROR: Disk full'.startswith('ERROR')` → `True` |
| `.endswith('str')`   | Checks if ends with                      | `'report.log'.endswith('.log')` → `True`          |
| `.find('str')`       | Index of first match (`-1` if not found) | `'backup failed'.find('fail')` → `7`              |
| `.count('str')`      | Number of occurrences                    | `'abc abc abc'.count('abc')` → `3`                |
| `'str' in string`    | Check presence                           | `'ERROR' in log_line`                             |

---

### 🔁 **3. Replace and Modify**

| Method               | Description             | Example                                                       |
| -------------------- | ----------------------- | ------------------------------------------------------------- |
| `.replace(old, new)` | Replace all occurrences | `'prod-server'.replace('prod', 'dev')` → `'dev-server'`       |
| `.split('delim')`    | Split into list         | `'10.0.0.1,10.0.0.2'.split(',')` → `['10.0.0.1', '10.0.0.2']` |
| `'delim'.join(list)` | Join list into string   | `','.join(['a', 'b'])` → `'a,b'`                              |

---

### 🔠 **4. Validation / Checks**

| Method                      | Description        | Example                       |
| --------------------------- | ------------------ | ----------------------------- |
| `.isalpha()`                | Letters only       | `'abc'.isalpha()` → `True`    |
| `.isdigit()`                | Digits only        | `'1234'.isdigit()` → `True`   |
| `.isalnum()`                | Letters and digits | `'abc123'.isalnum()` → `True` |
| `.isspace()`                | Whitespace only    | `'   '.isspace()` → `True`    |
| `.isupper()` / `.islower()` | All upper/lower    | `'CMD'.isupper()` → `True`    |

---

### 📋 **5. Formatting Strings**

| Method      | Description                       | Example                        |
| ----------- | --------------------------------- | ------------------------------ |
| `.format()` | Substitutes values                | `"Server: {}".format('web01')` |
| `f"{}"`     | f-string formatting (recommended) | `f"User: {user}, IP: {ip}"`    |
| `.zfill(n)` | Pads number with leading zeros    | `'7'.zfill(3)` → `'007'`       |

---

### 🔧 **6. DevOps Use Case Examples**

#### 🔍 Extracting IPs from a log line

```python
line = "Connected from 10.0.0.7 to port 22"
ip = line.split()[2]
print(ip)  # 10.0.0.7
```

#### 🔁 Replace environment in script

```python
cmd = "kubectl apply -f prod.yaml"
print(cmd.replace("prod", "dev"))  # kubectl apply -f dev.yaml
```

#### 🧪 Checking if a line is an error

```python
log = "ERROR: Disk quota exceeded"
if log.startswith("ERROR"):
    print("🔴 Log is an error")
```

---

### 🧠 Summary Table

| Category      | Key Functions                            |
| ------------- | ---------------------------------------- |
| Case Handling | `.lower()`, `.upper()`, `.title()`       |
| Cleanup       | `.strip()`, `.replace()`, `.zfill()`     |
| Matching      | `.startswith()`, `.find()`, `in`         |
| Splitting     | `.split()`, `.join()`                    |
| Validation    | `.isdigit()`, `.isalpha()`, `.isspace()` |
| Formatting    | `f""`, `.format()`                       |

---

## ✅ 1. `lower()`, `upper()`, `title()`

Used for **case normalization** (e.g., CLI tools, tags, names).

```python
env = "PROD"
print(env.lower())        # 'prod'

resource = "aws lambda function"
print(resource.title())   # 'Aws Lambda Function'
```

---

## 🧹 2. `strip()`, `lstrip()`, `rstrip()`

Used to **clean strings** like input from CLI or logs.

```python
bucket = "  my-s3-bucket  "
print(bucket.strip())     # 'my-s3-bucket'
```

---

## 🔍 3. `startswith()`, `endswith()`

Check if logs/commands start or end with specific strings.

```python
log = "ERROR: Volume not found"
print(log.startswith("ERROR"))    # True

filename = "backup.tar.gz"
print(filename.endswith(".gz"))   # True
```

---

## 🔎 4. `find()`, `count()`

Used to **locate or count substrings** in a string.

```python
region_info = "aws-region: us-west-2"
print(region_info.find("us"))     # 12

error_log = "ERROR: Disk full"
print(error_log.count("ERROR"))   # 1
```

---

## 🔁 5. `replace()`

Used to modify values (e.g., switch env names).

```python
cmd = "deploy to prod"
print(cmd.replace("prod", "dev"))  # 'deploy to dev'
```

---

## 📤 6. `split()`, `join()`

Useful for **parsing** and **assembling** strings (paths, IPs, instances).

```python
instance_ids = "i-0123,i-0456"
print(instance_ids.split(","))    # ['i-0123', 'i-0456']

parts = ['dev', 'us-west-2', 'ec2']
print("-".join(parts))            # 'dev-us-west-2-ec2'
```

---

## ✔️ 7. `isdigit()`, `isalpha()`, `isalnum()`

Used to **validate inputs** or IDs.

```python
print("1234".isdigit())     # True
print("uswest2".isalpha())  # False (has digit)
print("dev123".isalnum())   # True
```

---

## 🔧 8. `format()`, f-strings

Used to **dynamically build CLI commands**, filenames, templates.

```python
instance = "i-12345"
print("Instance ID: {}".format(instance))     # Old style
print(f"Instance ID: {instance}")             # New f-string style
```

---

## 🧮 9. `zfill()`

Pad with zeros (e.g., for logs, ticket numbers, IDs).

```python
print("7".zfill(3))   # '007'
```

---

## 🧪 10. DevOps Example – Parsing Logs

```python
log = "Connection from 10.0.0.7 to port 22"
ip = log.split()[2]
print(ip)             # '10.0.0.7'
```

---

## 🛡️ 11. DevOps Example – Check Log Type

```python
log_line = "ERROR: Pod crashed"
if "ERROR" in log_line:
    print("🔴 Issue detected!")   # This will print
```

---

## 🔚 Summary Table

| Method          | Usage Example                            |
| --------------- | ---------------------------------------- |
| `.lower()`      | Normalize env names like `PROD` → `prod` |
| `.strip()`      | Clean up extra spaces in bucket names    |
| `.split()`      | Parse instance IDs or IPs                |
| `.startswith()` | Check if log starts with `ERROR`         |
| `.replace()`    | Change `prod` to `dev` in commands       |
| `.join()`       | Assemble resource names with `-`         |
| `f"{}"`         | Build dynamic CLI strings or logs        |

---

## 📏 `len()` – Get Length of Strings, Lists, etc.

### ✅ **Syntax:**

```python
len(object)
```

It returns the **number of characters** in a string, or the **number of items** in a list, tuple, dict, etc.

---

### 🧵 **1. For Strings (Character Count)**

```python
bucket_name = "my-s3-bucket"
print(len(bucket_name))  # 12
```

✔️ **Use case in DevOps:**
Check if a name exceeds AWS S3 bucket naming limit (63 characters max).

---

### 📋 **2. For Lists (Number of Items)**

```python
instances = ["i-001", "i-002", "i-003"]
print(len(instances))  # 3
```

✔️ **Use case:**
Count the number of EC2 instances in a list for scaling or automation scripts.

---

### 🧰 **3. For Dictionaries (Number of Keys)**

```python
env_vars = {
    "DB_HOST": "localhost",
    "DB_PORT": "5432"
}
print(len(env_vars))  # 2
```

✔️ **Use case:**
Validate the number of environment variables loaded in a config.

---

### 📁 **4. For Files (Check Length of Each Line)**

```python
log_line = "ERROR: Disk full at 90%"
if len(log_line) > 30:
    print("Trim or wrap the line")
```

✔️ **Use case:**
Detect and clean long log lines before saving to a file.

---

## 💡 Summary:

| Data Type | `len()` Returns           | Use Case Example            |
| --------- | ------------------------- | --------------------------- |
| `str`     | Character count           | Validate tag or name length |
| `list`    | Number of items           | Count EC2 or S3 buckets     |
| `dict`    | Number of key-value pairs | Validate config keys        |
| `tuple`   | Number of elements        | Iterate over command steps  |

---



