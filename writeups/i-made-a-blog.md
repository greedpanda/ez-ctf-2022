# [Web] I made a blog!

<p align="center"><img src="https://github.com/greedpanda/ez-ctf-2022/blob/main/assets/challenge-cards/I-made-a-blog.jpg"/></p>

## Writeup

The web address provided returns the web page to the blog.

<p align="center"><img src="https://github.com/greedpanda/ez-ctf-2022/blob/main/assets/blog1.png"/></p>
<br/><br/>

Since the hint provided is `robots will rule the world!`, the first thing to try is navigate to `/robots.txt` where it is possible to find the following:

<img src="https://github.com/greedpanda/ez-ctf-2022/blob/main/assets/blog2.png" width="500px" />
<br/><br/>

Hence, navigate to `/flag.php` address to find: 

<img src="https://github.com/greedpanda/ez-ctf-2022/blob/main/assets/blog3.png" width="500px" />
<br/><br/>

Given that the site uses **PHP**, the word filter found above suggested a **Local File Inclusion (LFI)** vulnerability of the type `php://filter`.
Therefore, navigating to the Blog page and inserting `http://ez.ctf.cafe:9999/blog-posts.php?file=php://filter/convert.base64-encode/resource=flag.php` produces the base64 encoded text at the top of the rendered page. Decoding the string with the following commands provides the flag for the challenge.

<p align="center"><img src="https://github.com/greedpanda/ez-ctf-2022/blob/main/assets/blog4.png"/></p>

## Flag

    EZ-CTF{LFI_1S_3Z}

## Vulnerability

The vulnerability faced is a combination of [A01:2021 – Broken Access Control](https://owasp.org/Top10/A01_2021-Broken_Access_Control/) and [A05:2021 – Security Misconfiguration](https://owasp.org/Top10/A05_2021-Security_Misconfiguration/) that permitted to access the hidden flag. The **Local File Inclusion (LFI)** vulnerability can be a serious threat on information disclosure, directory traversal and remote code execution.

## Mitigation

Starting from the `/robots.txt` file, that tells search engine crawlers which URLs the crawler can access on your site. This is used mainly to avoid overloading your site with requests; it is not a mechanism for keeping a web page out of Google. To keep a web page out of Google, block indexing with `noindex` or password-protect the page.

Regarding LFI there are a few ways to prevent LFI attacks:
- ID assignation: saving your file paths in a secure database and giving an ID for every single one, this way users only get to see their ID without viewing or altering the path.
- Whitelisting: using verified and secured whitelist files and ignore everything else.
- Use databases: do not include files on a web server that can be compromised, use a database instead.
- Proper server configuration: making the server send download headers automatically instead of executing files in a specified directory.
