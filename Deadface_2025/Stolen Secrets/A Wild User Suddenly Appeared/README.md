# A Wild User Suddenly Appeared

## Description
Which user did DEADFACE create for persistence? What was that user’s first name and password?

## Flag
deadface{Dorla_SuP3RS3cr3tD34DF4C3#}

## Steps
1. Pada challenge ini, kita diminta mencari akun yang dibuat oleh DEADFACE. bila kita analisis packet-packet setelah DEADFACE mendapatkan compromised user, kita bisa melihat DEADFACE melakukan pembuatan akun baru melalui endpoint `/admin.php?page=create-user`.
![a-wild-user-suddenly-appeared01](a-wild-user-suddenly-appeared01.png)

2. bila kita buka paket tersebut, maka bisa kita dapatkan informasi akun yang dibuat oleh DEADFACE.
![a-wild-user-suddenly-appeared02](a-wild-user-suddenly-appeared02.png)
