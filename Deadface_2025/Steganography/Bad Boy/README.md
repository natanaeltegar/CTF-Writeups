# Bad Boy

## Description
DEADFACE left this image on a victim’s machine with a hidden message. See if you can discover the flag hidden in this image.

## Flag
deadface{th3_b4dd3st_B0i_al1V3}

## Steps
1. Kita coba melihat metadata dari file gambar yang diberikan menggunakan exiftool.
![badboy01](badboy01.png)

2. Dari metadata yang didapat, terdapat warning `[minor] Trailer data after PNG IEND chunk`. Ini artinya, ada data yang tertulis setelah chunk IEND. Kita bisa coba mengubah ekstensi file menjadi .txt, lalu melihat ke baris paling akhir karena siapa tahu itu adalah clue selanjutnya dari challenge ini.
![badboy02](badboy02.png)

3. Ternyata data dicurigai adalah flag challenge ini.