# Ex--12---Elgamal
## AIM: 
To implement ElGamal encryption and decryption for securing a message using public-key cryptography.

## ALGORITHM:

### STEP 1:
Input a large prime number p and a generator 𝑔 from the user.

### STEP 2:
Alice inputs her private key.

### STEP 3:
Calculate ALice's public key as Public_key=g^privatekeyA mod p

### STEP 4:
Bob inputs the message to be encrypted and selects a random number 𝑘
### STEP 5:
Bobcomputes the ciphertext (c1,c2) using the following:
  1.c1=g^k mod p
  2.c2=(message×publicKeyA^𝑘)mod p
### STEP 6:
Alice decrypts the message using the formula:
   1.decryptedMessage= (c2×c1^(p−1−privateKeyA))modp
## PROGRAM:
```py
# Function to compute modular exponentiation (base^exp % mod)
def mod_exp(base, exp, mod):
    result = 1
    while exp > 0:
        if exp % 2 == 1:
            result = (result * base) % mod
        base = (base * base) % mod
        exp = exp // 2
    return result

def main():
    # Step 1: Input a large prime number (p) and a generator (g)
    p = int(input("Enter a large prime number (p): "))
    g = int(input("Enter a generator (g): "))

    # Step 2: Alice inputs her private key
    private_key_a = int(input("Enter Alice's private key: "))

    # Step 3: Compute Alice's public key (public_key = g^privateKeyA mod p)
    public_key_a = mod_exp(g, private_key_a, p)
    print(f"Alice's public key: {public_key_a}")

    # Step 4: Bob inputs the message to be encrypted and selects a random k
    message = int(input("Enter the message to encrypt (as a number): "))
    k = int(input("Enter a random number k: "))

    # Step 5: Bob computes ciphertext (c1 = g^k mod p, c2 = (message * publicKeyA^k) mod p)
    c1 = mod_exp(g, k, p)
    c2 = (message * mod_exp(public_key_a, k, p)) % p
    print(f"Encrypted message (c1, c2): ({c1}, {c2})")

    # Step 6: Alice decrypts the message (decryptedMessage = (c2 * c1^(p-1-privateKeyA)) mod p)
    decrypted_message = (c2 * mod_exp(c1, p - 1 - private_key_a, p)) % p
    print(f"Decrypted message: {decrypted_message}")

if __name__ == "__main__":
    main()

```
## Output:
![image](https://github.com/user-attachments/assets/05444ec4-32bf-4a9c-85c5-28ac73f86f19)
## Result:
The program for ElGamal encryption and decryption was successfully implemented and executed. The decrypted message matches the original message, ensuring correct encryption and decryption.
