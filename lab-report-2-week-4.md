# Lab Report 2: When Tests Accumulate

## **Implementation of First Test**
![Example 1](Infinity.jpg)

[Error-Causing Test](https://github.com/KXVlNY/markdown-parse/commit/491fedb66d3d9288a52c1fb68ce2626ebdc6445e)

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

In this first example, **underlying bug was detected by the symptoms of the failure-inducing input**. 

In other words, the only way to detect if there was an underlying problem in the code was to first check if such problem-inducing inputs can cause an issue, where in this case the infinite loop between `-1` and `Current index is: 36` was the resulting symptom from that input. 

It shows that there is an underlying issue *(a bug!)* with the code that causes these symptoms.
***
