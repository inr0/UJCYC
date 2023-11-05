# Description
#Steganography
![[Pasted image 20231105232703.png]]
[Dont_Click.zip](http://139.59.212.68/files/d54cd94125227bdabb639718ea2e7b7d/Dont_Click.zip?token=eyJ1c2VyX2lkIjoxMTQsInRlYW1faWQiOjUsImZpbGVfaWQiOjd9.ZUf6SA.6s15T-9bz0Rh4qAjvyhQJLlvWWU)

---
First we unzip the file.
`unzip Dont_Click.zip`
The file contains 248 JPEG pictures
![[Pasted image 20231105235347.png]]
Since there is 248 pictures we need to differentiation them in some way.
first I tried to differentiation them by opening the pictures but they looked fairly similar.
![[Pasted image 20231106000054.png]]
So I needed to find another way.
# Foothold
`ls -al`
![[Pasted image 20231106000503.png]]
I found that some pictures have different size / length , so I made another directory and moved all the different sized pictures to that directory. 
![[Pasted image 20231106001017.png]]
There was 6 pictures with different size. 
I tried `strings | grep "UJCYC"` since flag start with UJCYC but that did not get me anywhere.
then I tried `steghide info 1.jpg` 
![[Pasted image 20231106004625.png]]
and we can see that there is embedded data indeed. 
I used `stegseek 1.jpg /usr/share/wordlists/rockyou.txt` to brute force the passphrase with `rockyou.txt` wordlist since I don't know the passphrase and we found the passphrase.
![[Pasted image 20231106005052.png]]
`cat 1.jpg.out`
![[Pasted image 20231106005242.png]]
we found a flag but its a fake one. i tried the same method to for all 6 pictures and I found the real flag in 189.jpg
![[Pasted image 20231106005440.png]]
```
FLAG : UJCYC{N0T_1NV1S1BL3_3N0UGH}
```
