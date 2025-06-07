# password-cracker
the main idea is to develop a code to crack password using python
import hashlib

def hash_password(password):
    """Hash a password using SHA-256."""
    return hashlib.sha256(password.encode()).hexdigest()

def crack_password(hash_to_crack, dictionary_file):
    with open(dictionary_file, 'r') as file:
        for line in file:
            word = line.strip()
            hashed_word = hash_password(word)
            if hashed_word == hash_to_crack:
                print(f" Password found: {word}")
                return
            else:
                print(f" Tried: {word}")
    print(" Password not found in dictionary.")

# Example SHA-256 hash for password 'secret123'
hash_to_crack = "84d961568a65073a3bcf0eb216b2a57613f8c59a3fefaf1fdcd1181b9cfa6d1b"

# Provide the path to your password dictionary file
crack_password(hash_to_crack, 'passwords.txt')
