# Using gmpy2 to Decrypt RSA Keys

## What is gmpy2?
`gmpy2` is a Python library that provides high-performance mathematical functions using:
- **GMP (GNU Multiple Precision)** – Arbitrary precision integer arithmetic  
- **MPFR (Multiple Precision Floating-Point)** – High-precision floating-point operations  
- **MPC (Complex Numbers)** – Complex number calculations  

### Common Uses:
✅ Arbitrary precision arithmetic  
✅ Modular arithmetic (useful for cryptography and RSA decryption)  
✅ Number theory operations (e.g., gcd, modular inverses, primality testing)  

### Example Using in Python
```bash
import gmpy2

# Define two large numbers
a = gmpy2.mpz(12345678901234567890)
b = gmpy2.mpz(9876543210987654321)

# Perfom arithmaetic operations
print("Addition:", gmpy2.add(a, b))
print("Multiplication:", gmpy2.mul(a, b))

# Compute modular inverse
mod_inverse = gmpy2.invert(3, 7) # 3^(-1) mod 7
print("Modular Inverse of 3 mod 7:", mod_inverse)
```

---

## Step 1: Setting Up the Script
-**I Recommend creating a directory and a script file.**
-**TO create the scipt file use vim or nano.** 
-**I originally started with vim but changed to nano.**

**Directory and Script file:**

```bash
#This creates the Directory. 
mkdir PythonCode
#This takes you to Pythoncode Directory.
cd PythonCode
#This creates Script file. 
nano decrypt.py. 
```

---

## Step 2: Installing gmpy2
You can install `gmpy2` with the following prompt: 
If `gmpy2` is not installed, you might encounter an error.  

🚨 **Error:**
```
ModuleNotFoundError: No module named 'gmpy2'
```

### 💡 Solutions:
**Option 1: Install via pip (Preferred)**
```bash
pip install gmpy2
```

**Option 2: Use a Virtual Environment (Fixes 'externally managed' error)**
```bash
python3 -m venv myenv
source myenv/bin/activate
pip install gmpy2
```

**Option 3: Install via APT (For Kali/Debian Users)**
```bash
sudo apt update
sudo apt install python3-gmpy2
```

---

## Step 3: Running the RSA Decryption Script
```python
import gmpy2

n = 1079
e = 43
c_values = [996, 894, 379, 631, 894, 82, 379, 852, 631, 677, 677, 194, 893]

p, q = 83, 13
phi = (p - 1) * (q - 1)

d = gmpy2.invert(e, phi)

plaintext = [chr(gmpy2.powmod(c, d, n)) for c in c_values]
print("Decrypted message:", "".join(plaintext))
```

✅ **Output:**
```
Decrypted message: SKY-KRYG-
```

---

