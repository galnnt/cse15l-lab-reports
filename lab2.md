# Lab Report 2

## Part 1
Here is the first add operation:\
![Image](images/add1.png)\
For the first add operation, the `handleRequest()` method is called with value `url=http://localhost:6480/add-message?s=cse15l`. Before the method call, the string `s` that is being displayed on the screen in empty. As the URL is passed in, it falls into the `else` clause of the `handleRequest()` method as the `.contains()` method found a substring in the path of the URL containing `\add-message`.
Here is the second add operation:\
![Image](images/add2.png)\
For the second add operation, the `handleRequest()` method is called with value `url=http://localhost:6480/add-message?s=slay_the_spire`. Before the method call, the string `s` has value `1. cse15l\n`.

## Part 2
My images look like this because I accidentally cleared the log when doing the lab tasks so I had to fetch the command from accessing the history of the terminal.\
Screenshot for private ssh key:\
![Image](images/private.png)\
Screenshot for public ssh key:\
![Image](images/public.png)\
Screenshot for accessing ieng6 server without password:\
![Image](images/noLogin.png)

## Part 3
In lab 2, I learned to access the UCSD ieng6 server by using the `ssh` command, and also learned how to login to my UCSD server account by creating a secure copy of my public key into the UCSD ieng6 server in lab 3. Moreover, I also learned how to create my own server on my local machine using the built in java packages such as URI.
