# More Sense

<p align="center"><img src="https://github.com/greedpanda/ez-ctf-2022/blob/main/assets/challenge-cards/More-sense.jpg"/></p>

## Writeup

The first thing to do is identify the cipher that produced the ciphertext:

    BB BBBBB ABA AAA AAABB AABBAB BABB BBBBB AAB ABA AABBAB ABB AAAAB BABB AABBAB BBBBB AAB BBAAA AABBAB BBBBB AABA AABBAB AAAA AAABB ABA AAABB 

I have used the tool [Cipher Identifier](https://www.dcode.fr/cipher-identifier) that found Morse Code as cipher. Since **More Sense** sounds like Morse seemed correct, hence I tried to substitute the two letters with dot and dash, done in a convenient way with the tool [Morse Code](https://www.dcode.fr/morse-code), obtaining the flag for the challenge:

<p align="center"><img src="https://github.com/greedpanda/ez-ctf-2022/blob/main/assets/Morse-flag.png"/></p>

## Flag

    EZ-CTF{M0RS3_Y0UR_W4Y_0U7_0F_H3R3}
