# Lab Report 2
## Part 1
Here is the first add operation:\
![Image](images/add1.png)\
For the first add operation, the `handleRequest()` method is called with value `url=http://localhost:6480/add-message?s=cse15l`. Before the method call, the string `s` that is being displayed on the screen in empty. As the URL is passed in, it falls into the `else` clause of the `handleRequest()` method as the `.contains()` method found a substring in the path of the URL containing `\add-message`.
Here is the second add operation:\
![Image](images/add2.png)\
