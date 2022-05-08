# [Crypto] No Kidding

<p align="center"><img src="https://github.com/greedpanda/ez-ctf-2022/blob/main/assets/challenge-cards/No-kidding.jpg"/></p>

## Writeup

The first thing to do is identify the cipher that produced the ciphertext:

    8/44/444/7777\\\444/7777\\\8/44/33\\\555/2/6/33/7777/8\\\222/8/333\\\333/555/2/4\\\33/888/33/33/33/33/777 

I have used the tool [Cipher Identifier](https://www.dcode.fr/cipher-identifier) that found Multi-tap Phone (SMS) as cipher. Since **No Kidding** reminds the name Nokia, it seemed correct, hence I tried the tool provided by the same site [Multi-tap Phone (SMS)](https://www.dcode.fr/multitap-abc-cipher), obtaining the flag for the challenge only after substituting `\\\` with `_` adn removing the whitespaces:

<p align="center"><img src="https://github.com/greedpanda/ez-ctf-2022/blob/main/assets/No-kidding-flag.png"/></p>

## Flag

    EZ-CTF{THIS_IS_THE_LAMEST_CTF_FLAG_EVEEEER}
