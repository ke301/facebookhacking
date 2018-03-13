## Secure Software Engineering: Week 7 - WordPress Hacking Report

### Exploit 1. Enumerating users and brute forcing the password with wpscan

For this attack on WordPress version 4.1, I was able to enumerate users by typing:

wpscan –-url http://wpdistillery.vm –-enumerate u

![alt text][logo1]

[logo1]: https://github.com/ke301/facebookhacking/blob/Week-7/enumerateusernames.PNG

Although I could have used the default "admin" to login, I wanted to experiment with this exploit. I created a new user with a password that might be used in a word list. I created a small word list to test wpscan's ability to do the brute forcing. For a password in the wild, a much longer word list would have to be used. Once I had the user name, I started the brute forcing with the following command:

wpscan –-url http://wpdistillery.vm –-word list /root/Desktop/wordlist.txt –-username newbie –threads 1

![alt text][logo2]

[logo2]: https://github.com/ke301/facebookhacking/blob/Week-7/bruteforce.PNG

![alt text][logo6]

[logo6]: https://github.com/ke301/facebookhacking/blob/Week-7/bruteforce.gif

Reference: https://www.drchaos.com/hacking-wordpress-with-wpscan/



### Exploit 2: Stored XSS

For this attack on Wordpress version 4.1, I was able to post a malicious comment that would trigger an XSS alert. The catch is that the comment has to be larger than the MySQL TEXT type size limit, which is 64 kb. This causes it to be truncated when the comment is inserted into the database, creating malformed HTML. That allows for anything to be in the HTML tags.

This is showing a photo of the Javascript injected comment with a bunch of A's to give it a size over 64 bytes:

![alt text][logo3]

[logo3]: https://github.com/ke301/facebookhacking/blob/Week-7/ahh1.gif

Reference:  https://klikki.fi/adv/wordpress2.html


### Exploit 3: Authenticated Shortcode Tags XSS

For this attack on Wordpress version 4.1, I was able to create a malicious post, which has a hyperlink that when hovered over, will trigger an XSS alert.

Here is a screenshot of the hyperlink after it was posted in on the Wordpress site:

![alt text][logo5]

[logo5]: https://github.com/ke301/facebookhacking/blob/Week-7/clickme.gif

Reference: https://wpvulndb.com/vulnerabilities/8186
