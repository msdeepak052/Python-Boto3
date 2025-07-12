## 🧠 What Are Command Line Arguments?

**Command line arguments** allow you to **pass values to your Python script at runtime**, directly from the terminal, without hardcoding them in the code.

For example:

```bash
python deploy.py dev ap-south-1
```

* `"dev"` and `"ap-south-1"` are **command line arguments**.

---

## ✅ Why Are They Useful in DevOps?

| Use Case                | Description                                     |
| ----------------------- | ----------------------------------------------- |
| 🔁 Reuse Scripts        | Run the same script with different environments |
| 🧪 Parametrize Tests    | Pass region, instance type, user, etc.          |
| 🛠️ Trigger Deployments | Use CLI args in Jenkins, GitHub Actions         |
| 📦 Integrate with tools | Use arguments to feed automation from pipelines |

---

## ✅ 3 Ways to Handle CLI Arguments in Python

| Method     | Description                                 |
| ---------- | ------------------------------------------- |
| `sys.argv` | Basic argument access                       |
| `argparse` | Recommended for structured CLI tools        |
| `click`    | External package for elegant CLI (optional) |

We'll focus on `sys.argv` and `argparse` — most relevant for DevOps.

---

## ✅ 1. Using `sys.argv` (Basic & Fast)

### 🔧 Example

```python
# script.py
import sys

print("All args:", sys.argv)
print("Script name:", sys.argv[0])
print("Environment:", sys.argv[1])
print("Region:", sys.argv[2])
```

### ▶️ Run:

```bash
python script.py dev ap-south-1
```

### ✅ Output:

```
All args: ['script.py', 'dev', 'ap-south-1']
Script name: script.py
Environment: dev
Region: ap-south-1
```

### ⚠️ Limitation:

* No type checking
* No help messages
* Manual error handling

---

## ✅ 2. Using `argparse` (Most Powerful & Recommended)

Python’s built-in module to create **user-friendly CLI tools**.

---

### ✅ Step-by-Step Example

```python
# deploy.py
import argparse

parser = argparse.ArgumentParser(description="Deploy to AWS environment")

# Add arguments
parser.add_argument("--env", help="Environment name", required=True)
parser.add_argument("--region", help="AWS Region", default="us-east-1")
parser.add_argument("--type", help="Instance type", choices=["t2.micro", "t2.small"], default="t2.micro")

# Parse them
args = parser.parse_args()

print(f"Environment: {args.env}")
print(f"Region: {args.region}")
print(f"Instance Type: {args.type}")
```

### ▶️ Run:

```bash
python deploy.py --env dev --region ap-south-1 --type t2.small
```

### ✅ Output:

```
Environment: dev
Region: ap-south-1
Instance Type: t2.small
```

---

## 🔍 `argparse` Parameters Explained

| Parameter       | Description                                      |
| --------------- | ------------------------------------------------ |
| `help`          | Shown when user adds `-h` or `--help`            |
| `required=True` | Argument must be provided                        |
| `default=`      | Default value if not passed                      |
| `choices=[]`    | Restricts input to valid options                 |
| `type=`         | Convert input to type (int, str, float)          |
| `nargs=`        | Accepts multiple arguments (e.g., list of files) |

---

## 🧪 Advanced Example: Multiple Types

```python
parser.add_argument("--port", type=int, help="Port to use", default=8080)
parser.add_argument("--tags", nargs='+', help="List of tags")
```

### ▶️ Run:

```bash
python deploy.py --env dev --tags alpha beta gamma
```

✅ `args.tags` will be: `['alpha', 'beta', 'gamma']`

---

## 🧰 DevOps Use Case Example: EC2 Automation

```python
# ec2_deploy.py
import argparse

parser = argparse.ArgumentParser(description="EC2 Automation CLI")

parser.add_argument("--action", required=True, choices=["start", "stop", "status"])
parser.add_argument("--instance-id", required=True)
parser.add_argument("--region", default="us-east-1")

args = parser.parse_args()

print(f"Performing {args.action} on {args.instance_id} in {args.region}")
```

### ▶️ Run:

```bash
python ec2_deploy.py --action start --instance-id i-12345 --region ap-south-1
```

---

## 📦 Combine with `venv`, `logging`, `boto3`, etc.

✅ Build your own CLI tools for:

* Deployments
* Monitoring
* Cloud config push
* Status dashboards

---

## 🧪 Extra: Add `--version` and `--verbose`

```python
parser.add_argument('--version', action='version', version='DevOps CLI 1.0')
parser.add_argument('--verbose', action='store_true', help='Enable verbose mode')
```

---

## 📚 Summary Table

| Feature       | `sys.argv`    | `argparse`            |
| ------------- | ------------- | --------------------- |
| Easy to use   | ✅             | ✅✅✅                   |
| Help messages | ❌             | ✅                     |
| Validation    | ❌             | ✅ (`choices`, `type`) |
| DevOps ready  | ⚠️ Basic only | ✅ Recommended         |

---

Would you like me to:

* Bundle a full **DevOps CLI automation project** with `argparse`, `logging`, `venv`, and modular structure?
* Or walk through **building your own CLI tool** for EC2/S3/K8s step-by-step?

Let me know what you'd like to build next!
