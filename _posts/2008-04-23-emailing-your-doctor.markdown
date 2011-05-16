---
layout: default
title: Emailing Your Doctor
published: true
categories:
  - security
tags:
  - computer
  - security
---

It seems here in BC, there are doctors conversing with their patients via 
[email][ref-1], instead of the more traditional in-person style meetings. I love 
the use of technology to make processes more efficient, and I am fully 
behind the use of email as a medium between doctors and patients. But the 
security of email leaves me shaking in my booties.

Many people don’t realize the insecurities in email. First, the connection 
to send and receive email is not encrypted by default. Certain hosting 
companies, like [Joyent][ref-2], require encrypted connections by default. Of 
course, this makes setting up email clients a bit trickier, hence why the 
average joe-sick citizen is not going to configure their client to use it. 
With the connection left unencrypted, anyone eavesdropping on the wireless 
signal or over a wired hub connection (like some cable companies use) will 
be able to pick up the username and password credentials for your email 
account. They can then get into your account, read your email, or send 
email from your name. Some people don’t see this as a privacy concern. I 
say those people need to wake up and listen to identity theft stories.

The second problem with email is that the transmission of the email content 
itself is not encrypted. If you solved the first problem I mentioned, that 
secures the connection and transmission of the email content between 
yourself and your hosting company. The second part of the transmission is 
between the hosting company and the rest of the Internet until it reaches 
the target host. The problem here gets a bit technical, but a simple 
explanation is that there is no one path to a target host over the Internet. 
Remember, the Internet was developed to withstand a nuclear war, so your 
data will travel is any direction as long as it makes its way to the host 
in a reasonable amount of time. When the data is traveling through the 
Internet, bouncing around different intermediary hosts, that data is 
unencrypted and anyone can view the data if they have the technical skill 
(it doesn’t take much). So all of your information sent between your doctor 
and yourself is now being broadcast to everyone on your continent. That’s 
not violating doctor-client confidentiality but it’s getting pretty close. 
If you don’t think this is a privacy problem, then why did you 
traditionally go to the doctor and speak to them personally in a small room 
with no one else around?

The solution to the second problem is difficult and requires a lot of 
technical skill, especially with today’s email clients. You need to 
configure your email client to encrypt and sign your messages with a 
digital certificate (also known as public key cryptography). The problem 
with this is two-fold: first is that the sender’s email client needs to 
configure correctly, which is often difficult to do because each client is 
configured differently. The second problem is that the receiver’s email 
client needs to be configured correctly to check the signature and decrypt 
the data with their own private key. If your eyes are going sideways now, 
just wait until you set it all up. Email cryptography is still too difficult 
for the average person to configure, so by default people are not going to 
use it. That is going to leave a lot of people with medical conversations 
out in the open.

[ref-1]: http://www.news1130.com/news/local/article.jsp?content=20080423_075746_12064
[ref-2]: http://www.joyent.com/

