# Caesar Cipher Program


## Overview

The Caesar Cipher Program is a simple command-line application that allows users to encrypt and decrypt messages using the Caesar cipher algorithm. The program prompts the user for a message and a shift value, then performs the desired operation (encryption or decryption) and displays the result.

## Features

Encrypt and decrypt messages using the Caesar cipher algorithm.
Supports both uppercase and lowercase letters.
Non-alphabetic characters are preserved in the output.
User-friendly command-line interface.


## Requirements
Python 3.x

## How to Use the Program:

Run the program.
Choose whether you want to encrypt or decrypt a message by entering 'E' or 'D'.
Input the message you want to encrypt or decrypt.
Enter the shift value (a positive integer).
The program will display the encrypted or decrypted message.
You can choose to perform another operation or exit the program.

## Program Code

def caesar_cipher_encrypt(text, shift):
    encrypted_text = ""
    for char in text:
        if char.isalpha():  # Check if the character is a letter
            shift_base = ord('A') if char.isupper() else ord('a')
            # Shift the character and wrap around the alphabet
            encrypted_char = chr((ord(char) - shift_base + shift) % 26 + shift_base)
            encrypted_text += encrypted_char
        else:
            encrypted_text += char  # Non-alphabetic characters are not changed
    return encrypted_text

def caesar_cipher_decrypt(text, shift):
    return caesar_cipher_encrypt(text, -shift)  # Decrypting is just encrypting with the negative shift

def main():
    print("Caesar Cipher Program")
    while True:
        choice = input("Would you like to (E)ncrypt or (D)ecrypt a message? (E/D): ").strip().upper()
        if choice not in ['E', 'D']:
            print("Invalid choice. Please enter 'E' to encrypt or 'D' to decrypt.")
            continue
        
        message = input("Enter your message: ")
        shift = int(input("Enter the shift value (positive integer): "))
        
        if choice == 'E':
            encrypted_message = caesar_cipher_encrypt(message, shift)
            print(f"Encrypted message: {encrypted_message}")
        else:
            decrypted_message = caesar_cipher_decrypt(message, shift)
            print(f"Decrypted message: {decrypted_message}")
        
        another = input("Would you like to perform another operation? (Y/N): ").strip().upper()
        if another != 'Y':
            break

if __name__ == "__main__":
    main()



  

    
