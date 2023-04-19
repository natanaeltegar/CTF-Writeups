# Hidden Message

## Alat
* text editor

## Steps
1. Pertama kita analisis kode enkripsinya terlebih dahulu pada chall.py

```python
#!/usr/bin/python
import binascii

FLAG = 'REDACTED'
KEY = # DELETED

def encrypt(plaintext):
    enc = []
    for s in plaintext:
        enc.append(ord(s) ^ key)
    return bytes(enc)

with open('encrypted.txt', 'wb') as f:
    f.write(b'FLAG: ' + binascii.hexlify(encrypt(FLAG)))

```
2. Kasarnya, chall.py akan melakukan ini pada flag:
   1. Untuk tiap karakter pada flag, ubah ke dalam unicode number dan di-XOR dengan key, lalu append ke list enc.
   2. List enc diconvert ke bytes.
   3. Lalu value bytes tersebut diconvert ke hexadecimal dan di write pada encrypt.txt

3. Kalau begitu, kita tinggal reverse logika pada algoritmanya:
   1. Encrypted flag, yang berbentuk hexadecimal, kita convert ke bytes.
   2. Value bytes tersebut kita ubah menjadi struktur data list.
   3. Tiap integer di dalam list, kita XOR dengan key, lalu ubah ke kembali karakter unicode.

4. Masalahnya adalah kita tidak tau key enkripsinya. Bruteforce adalah jawabannya.

5. Setelah beberapa penyesuaian, saya membuat decrypt codenya seperti ini

```python
#!/usr/bin/python
import binascii

raw = 'f4e3f091f0dbc2f2d5d493c690d2c393ffc394ceffc293fff5d393c6d5ececffd390cd93d491cd93d3dd'

rawList = list(binascii.unhexlify(raw))

for i in range (1024):
        dec = []
        for j in rawList:
                dec.append(chr(j^i))
        if dec[0] == "T":
                for j in dec:
                        print(j,end="")
                print()
```

6. Perulangan i in range(1024) ini adalah bentuk brueforcenya, jadi kita akan coba keynya dari 0 hingga 1023. Code tersebut juga mengecek hasilnya untuk tiap key, bila karakter pertamanya adalah "T" (karena format flagnya TCP1P{.*}) maka akan kita tampilkan hasilnya.

7. Dengan begitu kita sudah bisa mendapatkan flagnya.
