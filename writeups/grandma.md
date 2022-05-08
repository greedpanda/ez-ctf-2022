# Grandma

<p align="center"><img src="https://github.com/greedpanda/ez-ctf-2022/blob/main/assets/challenge-cards/Grandma.jpg"/></p>

## Writeup

After downloading the provided zip file and extracted its content, it was obvious that the file was corrupted.

<p align="center"><img src="https://github.com/greedpanda/ez-ctf-2022/blob/main/assets/grandma0.jpg"/></p>

Following the hint `You really need to use your head on this one!` I have investigated the header of the file, that highlighted the presence of padding in the beginning of the header with some mussing bytes and the JPG extension, but strangely the IHDR bytes were also present (typical of a PNG file). Therefore, I proceeded to remove the initial padding and altered the extension to PNG changing the `X` values to the ones typical of a PNG header (`89 50 4E`).

<p align="center"><img src="https://github.com/greedpanda/ez-ctf-2022/blob/main/assets/grandma1.jpg"/></p>

At this point I only needed to reconstruct the image from the hexadecimal file, using the following python script.

```py
with open('hex.txt') as file:
    data = file.read()

data = bytes.fromhex(data)

with open('grandma-flag.png', 'wb') as file:
    file.write(data)
```
that produced the following image that contains the flag:

<p align="center"><img src="https://github.com/greedpanda/ez-ctf-2022/blob/main/assets/grandma-flag.png"/></p>

## Flag

    EZ-CTF{W3LL_AINT_7HA7COOL}