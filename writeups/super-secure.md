# [Web] Super Secure

<p align="center"><img src="https://github.com/greedpanda/ez-ctf-2022/blob/main/assets/challenge-cards/Super-Secure.jpg"/></p>

## Writeup

The web address provided returns the login page to the super safe website.

<p align="center"><img src="https://github.com/greedpanda/ez-ctf-2022/blob/main/assets/super-secure0.png"/></p>
<br/><br/>

Since the hint provided is `Did you get your Covid Injection?`, the first thing to try is inserting `'` in both the field.
The page returned is the following:

<p align="center"><img src="https://github.com/greedpanda/ez-ctf-2022/blob/main/assets/super-secure1.png"/></p>
<br/><br/>

Hence, it is possible to understand that I am dealing with a MySQL database where injection is possible. 

The first payload injection `admin' OR '1=1'` by playbook to insert in both field worked, providing the flag for the challenge:

## Flag

    EZ-CTF{N0t_S0_S4f3_4ft3r_411}

## Vulnerability

[A03:2021-Injection](https://owasp.org/Top10/A03_2021-Injection/) of class **Inbound** since the data is extracted using the same channel that is used to inject the SQL code. This is the most straightforward kind of attack, in which the retrieved data is presented directly in the application web page.

## Mitigation

Two layers of defense should be used within software in order to prevent attacks:

1. Parameterization - If available, use structured mechanisms that automatically enforce the separation between data and command. These mechanisms can help to provide the relevant quoting, encoding.
2. Input validation - the values for commands and the relevant arguments should be both validated. There are different degrees of validation for the actual command and its arguments:
    - When it comes to the commands used, these must be validated against a list of allowed commands.
    - In regards to the arguments used for these commands, they should be validated using the following options:
        - Positive or "allow list" input validation - where are the arguments allowed explicitly defined
        - Allow-list Regular Expression: where is explicitly defined a list of good characters allowed and the maximum length of the string. Ensure that metacharacters like `& | ; $ > < \ / ! `` `  and white-spaces are not part of the Regular Expression. For example, the following regular expression only allows lowercase letters and numbers, and does not contain metacharacters. The length is also being limited to 3-10 characters: `^[a-z0-9]{3,10}$`
