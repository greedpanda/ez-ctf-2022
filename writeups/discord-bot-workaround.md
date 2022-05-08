# Discord Bot Workaround

<p align="center"><img src="https://github.com/greedpanda/ez-ctf-2022/blob/main/assets/challenge-cards/Discord-bot-workaround.jpg"/></p>

## Writeup

For this challenge a good knowledge of how discord bots work was needed. 
Discord developer mode need to be activated to retrieve the `ID code` of the `Cafe Bot#8770` to be able to invite it into a Discord server were I am admin, so i can access the commands restricted to admin only.

The ID retrieved: `971520199515836456`

Following the link advertised to [invite a bot into a discord server](https://discordjs.guide/preparations/adding-your-bot-to-servers.html#bot-invite-links), I can alter the URL to invite the CafeBot:

    https://discord.com/api/oauth2/authorize?client_id=971520199515836456&permissions=0&scope=bot%20applications.commands

then after granting admin privileges to it I can finally redeem the flag:

<p align="center"><img src="https://github.com/greedpanda/ez-ctf-2022/blob/main/assets/Discord-flag.png"/></p>

## Flag

    EZ-CTF{D1SC0RD_1S_L1T}