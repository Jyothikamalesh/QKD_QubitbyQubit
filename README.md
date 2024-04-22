# QKD_QubitbyQubit

General Approach: 
The Quantum Message Encryption Program implements a secure method for encrypting and decrypting messages using a combination of Quantum Key Distribution (QKD) and the Advanced Encryption Standard (AES) algorithm. The program provides a user-friendly interface for encrypting and decrypting messages and utilizes various functions to achieve this functionality.

  Key Generation:  The program generates a random key of the specified length using the `generate_key(length)` function. This key is used for both the QKD process and AES encryption.

  QKD Process:  
  - Alice generates a random key and basis using `generate_key(key_length)` for the key and `generate_key(key_length)` for the basis.
  - Bob generates a basis using `generate_key(key_length)`.
  - Alice measures her qubits in her basis using `measure_in_basis(alice_key[i], alice_bases[i])` and stores the results in `alice_measurements`.
  - Bob measures the qubits in his basis using `measure_in_basis(alice_key[i], bob_bases[i])` and stores the results in `bob_measurements`.
  - Both parties discard the measurements where their bases do not match and extract a final shared key from the matching measurements.

-  Encryption:  
  - The program encrypts the message using the AES encryption algorithm in Cipher Block Chaining (CBC) mode with the shared key.
  - The `encrypt_message(message, key)` function takes the message and shared key as input, encodes the message as bytes, pads it to the AES block size, and encrypts it using the AES cipher object. It returns a tuple containing the initialization vector (IV) and the ciphertext.

-  Decryption:  
  - The program decrypts the message using the AES decryption algorithm with the shared key and IV.
  - The `decrypt_message(iv, ciphertext, key)` function takes the IV, ciphertext, and shared key as input, creates an AES cipher object with the key and IV, decrypts the ciphertext, and removes the padding from the decrypted message. It returns the decrypted message as a string.

-  Saving Encrypted Message:  
  - The `save_encrypted_message(iv, ciphertext, key, file_path)` function saves the encrypted message, IV, and key to a file. It opens a file at the specified path in binary write mode and writes the key, IV, and ciphertext to the file.

-  User Interface:  
  - The program provides a menu-driven interface for the user to select whether to encrypt or decrypt a message.
  - The user can input a message to be encrypted, and the program performs the encryption process and saves the encrypted message to a file.
  - If the user chooses to decrypt a message, the program reads the encrypted message from the file, decrypts it, and displays the decrypted message to the user.

