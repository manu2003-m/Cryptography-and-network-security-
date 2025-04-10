from collections import Counter

def decrypt_caesar(cipher_text, shift):
    decrypted = ''
    for char in cipher_text:
        if char.isalpha():
            shifted = ord(char.lower()) - shift
            if shifted < ord('a'):
                shifted += 26
            decrypted += chr(shifted)
        else:
            decrypted += char
    return decrypted

def caesar_cryptanalysis(cipher_text):

  letters_only = ''.join(filter(str.isalpha, cipher_text.lower()))
    freq = Counter(letters_only)

   most_common = freq.most_common(1)[0][0]

  is 'e', so guess the shift
    assumed_shift = (ord(most_common) - ord('e')) % 26
    print(f"Most common letter in ciphertext: '{most_common}'")
    print(f"Assumed Caesar shift (based on 'e'): {assumed_shift}")
    
  decrypted_text = decrypt_caesar(cipher_text, assumed_shift)
    return decrypted_text


cipher = "Wklv lv d vhfuhw phvvdjh"  
decrypted = caesar_cryptanalysis(cipher)

print("\nDecrypted message:")
print(decrypted)
