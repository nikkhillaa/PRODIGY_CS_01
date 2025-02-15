# PRODIGY_CS_01
##PROGRAM 
def caesar_cipher_encrypt(text, shift): 
    encrypted_text = "" 
    for char in text: 
        if char.isalpha():  # Check if the character is a letter 
            shift_base = ord('A') if char.isupper() else ord('a') 
            # Perform the shift and wrap around using modulo 
            encrypted_char = chr((ord(char) - shift_base + shift) % 26 + shift_base) 
            encrypted_text += encrypted_char 
        else: 
            encrypted_text += char  # Non-alphabetic characters are not changed 
    return encrypted_text 
  
def caesar_cipher_decrypt(text, shift): 
    return caesar_cipher_encrypt(text, -shift)  # Decrypting is just encrypting with the negative shift 
 
def main(): 
    print("Caesar Cipher Encryption and Decryption") 
    while True: 
        choice = input("Would you like to (E)ncrypt, (D)ecrypt, or (Q)uit? ").strip().upper() 
        if choice == 'Q': 
            print("Goodbye!") 
            break  
        elif choice in ['E', 'D']: 
            message = input("Enter your message: ") 
            shift = int(input("Enter the shift value (0-25): ")) 
            if choice == 'E': 
                encrypted_message = caesar_cipher_encrypt(message, shift) 
                print(f"Encrypted message: {encrypted_message}") 
            elif choice == 'D': 
                decrypted_message = caesar_cipher_decrypt(message, shift) 
                print(f"Decrypted message: {decrypted_message}") 
        else: 
            print("Invalid choice. Please choose E, D, or Q.") 
 
if __name__ == "__main__": 
    main() 
    
