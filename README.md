# csc519-cm-special

| Team Member   | Unity ID | 
| ------------- | ----------- |
| Seth Butler      | scbutle2 |  
| Akshit Patel     | aapatel8 |
| Kunal Kulkarni | krkulkar |   
| Rezvan Mahdavi Hezaveh  |  rmahdav |

# Police Monkey

The Police monkey acts a the sentinel who determines whether an IP is a human user or a bot. This is determined using a text / image based captcha. Once an IP has been determined to be a human user any redirects to this Police Monkey will automatically be proxied to the Checkbox server. When an ip has reached a predetermined threshold of captcha failures the IP will be automatically blocked for a predetermined amount of time. Even if they successfully and correctly complete the captcha during this period they will still be blocked. When an ip correctly completes a captcha and they are not in a blocked state they will be redirected to the Checkbox server and any subsequent connections will as well. Redis is being used to store an IP's valid user boolean / captcha failure count, and the current correct captcha for that IP.

## What is DDoS attak?

A Denial-of-Service attack (DoS attack) is a cyber-attack in which the perpetrator seeks to make a machine or network resource unavailable to its intended users by temporarily or indefinitely disrupting services of a host connected to the Internet. Denial of service is typically accomplished by flooding the targeted machine or resource with superfluous requests in an attempt to overload systems and prevent some or all legitimate requests from being fulfilled.

In a Distributed Denial-of-Service attack (DDoS attack), the incoming traffic flooding the victim originates from many different sources. This effectively makes it impossible to stop the attack simply by blocking a single source.

## What is the functionality of Police Monkey?

The architecture of the system is as follows:

![police monkey](https://media.github.ncsu.edu/user/8135/files/434c57ea-4fea-11e8-8ebc-d9dfd3b79e05)

The proxy check the IP address of the source of recieved request, if the number of requests of that IP is less that threshold the proxy send the request to the main server. In the case that the number of requests of that IP is more that threshold the proxy send the request to the Police Monkey.

Police monkey checks the IP and if it is in the black list it detects attack and block the request but if it is not in the black list the proxy shows a CAPTCHA to the user and if the user gives the correct answer the request will be sent to the main server. If the request is an attack so it cannot pass the CAPTCHA question and that IP address will be added to the black list and the request will be blocked.

# Project Screencast
