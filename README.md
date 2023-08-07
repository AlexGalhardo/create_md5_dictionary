
<div align="center">
<h1 align="center">Creating MD5 Hashs Dictionary</h1>
</div>

<https://github.com/AlexGalhardo/Software-Engineering/assets/19540357/7432ddc0-6fae-478b-a4e8-a86dc2e89285>

## SUMMARY MD5

- MD5 is a cryptographic hash function, designed to be a one-way function, which means that it is not possible to directly decrypt an MD5 value to get the original input.
- The MD5 algorithm is no longer considered secure for password encryption as it is vulnerable to collision attacks and other hash cracking techniques. We recommend using stronger hashing algorithms such as SHA-256 or bcrypt instead. Therefore, it is quite common to find MD5 hash dictionaries on the internet to decrypt.

## INTRODUCTION

- To create a password, the algorithm uses 91 characters as follows:
- lowerCaseChars = 'abcdefghijklmnopqrstuvwxyzç';
- upperCaseChars = 'ABCDEFGHIJKLMNOPQRSTUVWXYZÇ';
- specialChars = '!@#$%^&*()-_+=<>?/,.:;{}[]|';
- numericChars = '0123456789';
- Totaling 91 different characters.

- Let's say I want to make a password with 6 characters with these 91 characters, remembering that characters can be repeated.
- So, we have an exponentiation: 91^6 = 91 x 91 x 91 x 91 x 91 = 567,869,252,041 (billion) possible password combinations.

## ESTIMATING TIME

- Imagine that 1 current CPU of my i5 here can do 100 passwords per second. I did some calculations here:
- 1 second = 100 passwords
- 1 minute = 6000 passwords
- 1 hour = 6000 x 60 = 360,000 passwords
- 1 day = 24 x 360,000 = 8,640,000 passwords
- 567,869,252,041 possible password combinations / 8,640,000 passwords per day = ~65725 days
- 65725 days / 365 days = it would take on average ~180 years to create all possible password combinations of length 6 using those 91 characters!

## ALGORITHM

- In this algorithm, using parallelism, the algorithm uses the 8 CPUs available in parallel that I have here on my machine.
- I had each worker create 8 possible password/dictionary combinations:
- 1 worker makes passwords with 6 characters
- 1 worker makes passwords with 7 characters
- Until the last worker, making passwords with 13 characters
- The 8 workers creating the passwords at the same time, in parallel.
- Each worker saves the possible combinations in a different JSON format dictionary, both with plain password along with its MD5 hashed password.

## CONCLUSION

- I made this algorithm for didactic purposes, and for pure curiosity/technical interest.
