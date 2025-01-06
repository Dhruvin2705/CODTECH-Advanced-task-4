# CODTECH-Advanced-task-4

**Name :** Sangani Dhruvin

**college :** Silver oak university

**Task :** Encryption Tool

**Intern ID :** CT08DAV

**Key Features:**
AES-256 Encryption: This is one of the strongest encryption algorithms widely used for securing data.
User-Friendly Command-Line Interface (CLI): A simple CLI where users can encrypt or decrypt files with just a few commands.
Secure Key Management: The encryption key will be derived from a password provided by the user, ensuring no sensitive key is hardcoded in the application.

**Libraries Used:**
cryptography: Provides easy-to-use encryption tools like AES-256.
argparse: For creating a simple CLI for the application.

**Step-by-Step Approach:**
Generate Key from Password: Using PBKDF2 (Password-Based Key Derivation Function 2) to securely derive an AES-256 key from a password.
AES-256 Encryption/Decryption: Encrypt files using AES-256 and decrypt them with the same password.
IV (Initialization Vector): Use a unique IV for each file to ensure that encrypting the same file twice results in different ciphertexts.
User Interface: Command-line interface to easily interact with the tool.

**Installation:**
Make sure you have the cryptography library installed

**Key Elements of the Tool:**
Password-Based Key Derivation:
The AES-256 key is derived from the password using PBKDF2HMAC, which securely hashes the password with a random salt. This makes it resistant to brute-force attacks.

**AES-256 Encryption:**
We use AES in CBC mode (Cipher Block Chaining) for encryption. This mode ensures that the encryption of identical data will produce different ciphertexts because each encryption uses a unique initialization vector (IV).
**File Encryption and Decryption:**
The tool encrypts a file by first padding the data (using PKCS7 padding) to make sure the data length is a multiple of the block size.
For decryption, the tool extracts the salt, IV, and encrypted data from the file, derives the key, and decrypts the content while removing the padding.

**User Interface:**
The tool uses the argparse library to provide a simple CLI, allowing users to easily select between encryption and decryption.
The password is securely collected from the user using the getpass() function, ensuring it is not visible during input.

**Security Considerations:**
Key Management: The password provided by the user is used to generate the AES key. The salt ensures that the same password will produce a different key each time.
Random Salt and IV: The tool uses a random salt and IV for each encryption, ensuring that even if the same file is encrypted multiple times, the ciphertext will be different.

**Further Enhancements:**
GUI (Graphical User Interface): You could integrate this with a GUI using libraries such as Tkinter or PyQt for a more user-friendly experience.
Support for Different File Formats: Extend the tool to handle other file types and include functionality for batch file encryption/decryption.
Key Import/Export: Allow users to import/export keys securely.
Error Handling: Improve error handling to handle various edge cases, such as incorrect password or corrupted files.
