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

---

## Step 1: Setting Up the Script
📌 **Create a directory and script file:**

```bash
mkdir rsa_decryption
cd rsa_decryption
nano decrypt_rsa.py
```

---

## Step 2: Installing gmpy2
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

