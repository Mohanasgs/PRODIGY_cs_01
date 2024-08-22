def caesar_cipher(text, shift, mode='encrypt'):
    # Define the alphabet
    alphabet = 'abcdefghijklmnopqrstuvwxyz'
    result = ''

    # Adjust shift for decryption
    if mode == 'decrypt':
        shift = -shift

    # Process each character in the text
    for char in text:
        if char.lower() in alphabet:
            # Find the position of the character
            old_index = alphabet.index(char.lower())
            # Calculate the new position
            new_index = (old_index + shift) % 26
            # Get the new character
            new_char = alphabet[new_index]
            # Preserve the case (upper or lower)
            if char.isupper():
                new_char = new_char.upper()
            result += new_char
        else:
            # Non-alphabetical characters remain unchanged
            result += char

    return result


# User input
text = input("Enter the message: ")
shift = int(input("Enter the shift value: "))
mode = input("Choose mode (encrypt/decrypt): ").lower()

# Perform encryption or decryption
output = caesar_cipher(text, shift, mode)
print(f"Output: {output}")
