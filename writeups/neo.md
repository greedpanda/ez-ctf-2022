# [Steganography] Neo

<p align="center"><img src="https://github.com/greedpanda/ez-ctf-2022/blob/main/assets/challenge-cards/Neo.jpg"/></p>

## Writeup

The first thing to do is analyse the image provided:

<p align="center"><img src="https://github.com/greedpanda/ez-ctf-2022/blob/main/assets/NEO.png"/></p> 
<br/><br/>

I have used the tool [Aperi'Solve](https://aperisolve.fr/e2dd98608a2865608ed268f23b3af73e) and immediately it was possible to recover the flag from the layer 0 and 1 of the color channels, more obvious in the red one:

<p align="center"><img src="https://github.com/greedpanda/ez-ctf-2022/blob/main/assets/NEO-flag.png"/></p>

## Flag

    EZ-CTF{Y0U_T00K_TH3_R3D_P1LL_D1DNT_Y0U}