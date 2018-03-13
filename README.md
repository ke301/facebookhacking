## Secure Software Engineering: Week 7 - WordPress Hacking Report
## Exploits

1. Enumerating users and brute forcing the password with wpscan

For this attack, I was able to enumerate users by typing:

wpscan –-url http://wpdistillery.vm –-enumerate u

![alt text][logo]

[logo]: https://github.com/ke301/facebookhacking/blob/Week-7/enumerateusernames.PNG

Although I could have used the default "admin" to login, I wanted to experiment with this exploit. I created a new user with a password that might be used in a word list. I created a small word list to test wpscan's ability to do the brute forcing. Once I had the user name, I started the brute forcing with the following command:

wpscan –-url http://wpdistillery.vm –-word list /root/Desktop/wordlist.txt –-username newbie –threads 1

![alt text][logo]

[logo]: https://github.com/ke301/facebookhacking/blob/Week-7/enumerateusernames.PNG

