# **File Handling in Python for DevOps: Comprehensive Guide**

File operations are fundamental to DevOps for configuration management, log processing, and infrastructure automation. This guide covers all aspects of file handling with practical DevOps examples.

## **1. File Opening Modes**

### **Common Modes**
| Mode | Description | DevOps Use Case |
|------|-------------|-----------------|
| `'r'` | Read (default) | Read configuration files |
| `'w'` | Write (truncate) | Create new configs/logs |
| `'a'` | Append | Add to log files |
| `'r+'` | Read+Write | Modify existing files |
| `'b'` | Binary mode | Process binary logs/artifacts |

```python
# Open a config file
with open('/etc/app/config.yaml', 'r') as f:
    config = f.read()
```

## **2. Reading Files**

### **Methods**
1. **`read()`** - Entire content as string
   ```python
   with open('deployment.log', 'r') as f:
       log_data = f.read()  # For small files
   ```

2. **`readline()`** - Single line at a time
   ```python
   with open('config.ini', 'r') as f:
       while True:
           line = f.readline()
           if not line: break
           if 'timeout' in line:
               print(line)
   ```

3. **`readlines()`** - List of all lines
   ```python
   with open('hosts.txt', 'r') as f:
       servers = f.readlines()  # ['server1\n', 'server2\n']
   ```

4. **Iteration (Memory Efficient)**
   ```python
   # Process large log files
   with open('nginx.log', 'r') as f:
       for line in f:  # Reads line-by-line
           if 'ERROR' in line:
               alert(line)
   ```

### **DevOps Example: Parse JSON Config**
```python
import json

with open('aws_config.json', 'r') as f:
    config = json.load(f)
    print(config['region'])  # us-east-1
```

## **3. Writing Files**

### **Methods**
1. **`write()`** - Write strings
   ```python
   with open('new_config.cfg', 'w') as f:
       f.write('[DEFAULT]\n')
       f.write('timeout=30\n')
   ```

2. **`writelines()`** - Write sequence of strings
   ```python
   config_lines = ['[DB]\n', 'host=db.example.com\n']
   with open('database.ini', 'w') as f:
       f.writelines(config_lines)
   ```

### **DevOps Example: Create Terraform File**
```python
tf_content = """
resource "aws_instance" "web" {
  ami           = "ami-123456"
  instance_type = "t2.micro"
}
"""

with open('main.tf', 'w') as f:
    f.write(tf_content)
```

## **4. Advanced File Operations**

### **1. Handling Different Encodings**
```python
# Read Windows-created files
with open('legacy_config.txt', 'r', encoding='utf-16') as f:
    content = f.read()

# Write with specific encoding
with open('output.log', 'w', encoding='ascii', errors='ignore') as f:
    f.write(log_data)
```

### **2. Binary Files (Artifacts/Logs)**
```python
# Read binary log
with open('app.binlog', 'rb') as f:
    data = f.read(1024)  # Read first 1KB

# Write binary backup
with open('backup.tar.gz', 'wb') as f:
    f.write(binary_data)
```

### **3. File Position Handling**
```python
with open('large.log', 'r') as f:
    f.seek(100)  # Jump to byte 100
    chunk = f.read(50)  # Read next 50 bytes
    print(f.tell())  # Current position (150)
```

## **5. File System Operations**

### **1. Check File Existence**
```python
import os
import pathlib

# Method 1 (os)
if os.path.exists('/var/log/nginx.log'):
    print("Log file exists")

# Method 2 (pathlib - Python 3.4+)
config_path = pathlib.Path('/etc/app/config.yaml')
if config_path.is_file():
    print(f"Config size: {config_path.stat().st_size} bytes")
```

### **2. Directory Operations**
```python
# List log files
for file in os.listdir('/var/log'):
    if file.endswith('.log'):
        print(f"Found log: {file}")

# Recursive search (Python 3.5+)
for root, dirs, files in os.walk('/etc'):
    for file in files:
        if file == 'nginx.conf':
            print(os.path.join(root, file))
```

## **6. Real-World DevOps Examples**

### **1. Log Rotation**
```python
import shutil
from datetime import datetime

log_file = '/var/log/app.log'
if os.path.getsize(log_file) > 1_000_000:  # 1MB
    timestamp = datetime.now().strftime('%Y%m%d_%H%M%S')
    shutil.move(log_file, f'/var/log/archive/app_{timestamp}.log')
    open(log_file, 'w').close()  # Create new empty file
```

### **2. Configuration Templating**
```python
# Render config from template
template = """
DB_HOST={db_host}
DB_PORT={db_port}
"""

with open('config.env', 'w') as f:
    f.write(template.format(
        db_host='db.example.com',
        db_port=5432
    ))
```

### **3. Secure File Handling**
```python
import tempfile

# Create secure temp file
with tempfile.NamedTemporaryFile(mode='w', delete=False) as tf:
    tf.write("Sensitive temporary data")
    temp_path = tf.name

# Process and securely delete
process_temp_file(temp_path)
os.unlink(temp_path)  # Secure deletion
```

## **7. Best Practices for DevOps**

1. **Always use `with` statements** - Ensures proper file closing
2. **Handle encodings explicitly** - Especially with cross-platform files
3. **Process large files line-by-line** - Avoid memory issues
4. **Validate file paths** - Check existence and permissions
5. **Use atomic writes** for critical configs:
   ```python
   import os
   temp_path = 'config.tmp'
   final_path = 'config.cfg'
   
   with open(temp_path, 'w') as f:
       f.write(new_config)
   os.replace(temp_path, final_path)  # Atomic operation
   ```
6. **Leverage `pathlib`** for modern path handling (Python 3.4+)
7. **Monitor file descriptors** in long-running processes

## **8. Performance Considerations**

### **1. Buffering Strategies**
```python
# Adjust buffer size for large files (bytes)
with open('huge.log', 'r', buffering=1_000_000) as f:  # 1MB buffer
    for line in f:
        process(line)
```

### **2. Memory Mapping (mmap)**
```python
import mmap

with open('large.data', 'r+b') as f:
    with mmap.mmap(f.fileno(), 0) as mm:
        if mm.find(b'ERROR') != -1:
            print("Error found in binary data")
```

## **Conclusion**

Mastering file handling enables DevOps engineers to:
- **Process logs and metrics** efficiently
- **Manage configuration files** dynamically
- **Implement atomic deployments**
- **Handle binary artifacts** (Docker images, packages)
- **Build reliable automation** scripts

Key takeaways:
1. **Prefer context managers (`with`)** for resource safety
2. **Choose the right method** (`read()` vs line iteration)
3. **Handle encodings properly** - UTF-8 for text, binary for artifacts
4. **Use atomic operations** for critical writes
5. **Leverage Python's stdlib** (`os`, `pathlib`, `tempfile`)

This comprehensive file handling knowledge is essential for building robust DevOps tools and automation pipelines.
