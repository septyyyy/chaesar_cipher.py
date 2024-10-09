# chaesar_cipher.py
def caesar_cipher(message, shift, mode='encrypt'):
    result = ""
    
    # Menentukan arah pergeseran
    if mode == 'decrypt':
        shift = -shift
    
    for char in message:
        if char.isalpha():  # Memeriksa apakah karakter adalah huruf
            shift_base = ord('A') if char.isupper() else ord('a')
            shifted_char = chr((ord(char) - shift_base + shift) % 26 + shift_base)
            result += shifted_char
        else:
            result += char  # Menambahkan karakter non-huruf tanpa perubahan
    
    return result

# Contoh penggunaan
if __name__ == "__main__":
    message = input("Masukkan pesan yang ingin dienkripsi: ")
    shift = int(input("Masukkan jumlah pergeseran: "))
    
    encrypted_message = caesar_cipher(message, shift, mode='encrypt')
    print("Pesan terenkripsi:", encrypted_message)
    
    decrypted_message = caesar_cipher(encrypted_message, shift, mode='decrypt')
    print("Pesan terdekripsi:", decrypted_message)
