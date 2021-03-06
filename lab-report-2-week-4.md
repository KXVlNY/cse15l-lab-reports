# Lab Report 2: When Tests Accumulate

## **Implementation of First Test**
![Example1](update1.png)

[Error-Causing Test1](https://github.com/KXVlNY/markdown-parse/commit/491fedb66d3d9288a52c1fb68ce2626ebdc6445e)

### **Output/Symptom of the Error:**
```
-1
Current index is: 36
-1
Current index is: 36
-1
Current index is: 36
# ... infinite loop

```

In this first example, underlying bug was detected by the symptoms of the **failure-inducing input**. 

In other words, the only way to detect if there was an underlying problem in the code was to first check if such problem-inducing inputs can cause an issue, where in this case the infinite loop between `-1` and `Current index is: 36` was the resulting symptom from that input. 

It reveals that there is an underlying issue (a bug!) with the code that causes these symptoms, which I tried to prevent by checking for negative values
***

## **Implementation of Second Test**

![Example2](example2.jpg)

[Error-Causing Test2](https://github.com/KXVlNY/markdown-parse/commit/41d634f0afecf7263cce77f26aaa640fc9871ba2)

### **Output/Symptom of the Error:**

```
PS C:\Users\dsk81\OneDrive\Documents\GitHub\markdown-parse> javac -cp ".;lib\junit-4.13.2.jar;lib\hamcrest-core-1.3.jar" MarkdownParseTest.java
MarkdownParseTest.java:16: error: unreported exception IOException; must be caught or declared to be thrown
            String contents = Files.readString(fileName);
                                              ^
1 error

```

In this second example, the JUnit tester was implemented in order to improve efficiency with testing, and tried to use the markdown files as the test. However, implemented the tester ended up being part of one of the tests as well. **In attempt to fix our bug, we found another bug!**

The bug's symptoms were indicated by the error messages caused by implementing those testing methods, saying that those methods must be caught/thrown. As a result, the bug was then detected *(we did not throw IOException for the method)*.

***

## **Implementation of Third Test**

![Example3](example3.jpg)

But then quickly changed to: 

![Example4](update2.png)

[Error-Causing Test](https://github.com/KXVlNY/markdown-parse/commit/9f13c4b9a703ef8374aef408b1e8cb28cb5fc71f)

### **Output/Symptom of the Error:**

```
-1
-1
-1
-1
-1
-1
-1
# ... infinite loop
```

In this last example, we tried to fix the bug discovered in the *first problem*. We tried a more comprehensive test in test-file2.md, where it had parentheses inside the link. 

We believed that the **symptom** (infinite -1 loop) was because currentIndex would end up not being found, returning -1 for currentIndex and then adding +1 would make it = 0, therefore never breaking from the while loop. Therefore, we tried to check if currentIndex was <0, then to break away from the loop. 

However, the same symptoms appeared (with an infinite loop) as a result from *this test*, therefore leaving us to believe that the **same bug still remained** from the first test implementation.
