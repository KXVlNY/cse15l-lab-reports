# Week 10: Lab report 5 

## How I Found the Tests with Different Results

First, I get the `result.txt` from the lab 9 repository and compare that to a representative implementation from my group using `diff` command. In particular, I run:

```bash
diff -u my-result.txt other-result.txt
```

The result would look like this

```bash
--- my_results.txt      2022-03-10 11:48:49.357747200 -0800
+++ other_results.txt   2022-03-10 11:50:04.441919000 -0800
@@ -209,7 +209,7 @@
 test-files/193.md
 []
 test-files/194.md
-[]
+[url]
 test-files/195.md
 []
 test-files/196.md
@@ -227,7 +227,7 @@
 test-files/200.md
 []
 test-files/201.md
-[]
+[baz]
 test-files/202.md
 []
 test-files/203.md
@@ -539,7 +539,7 @@
 test-files/341.md
 []
 test-files/342.md
-[]
+[/foo`]
 test-files/343.md
 []
 test-files/344.md
```

From this, I can see there are difference in the result in test file `194.md` and test file `201.md`

## Test 1: `194.md`

This is the content of the file itself

```markdown
[foo*bar\]]: my_(url) "title (with parens)"

[Foo*bar\]]
```

My group implementation output

```bash
[]
```

Lab 9 implementation output

```bash
[url]
```

The correct answer should be

```bash
[title (with parens)]
```

So both implementation are incorrect. I think I need to watch out for special case of what is considered to be link. In particular, the part I have to fix is:

```java
final String regex = "(?<!!)(?<!`)\\[(?>[[a-zA-Z0-9 ]&&[^\\n]])+\\]\\((\\S+)\\)";
```

## Test 2: `201.md`

This is the content of the file itself

```txt
[foo]: <bar>(baz)

[foo]
```

My group implementation output

```bash
[]
```

Lab 9 implementation output

```bash
[baz]
```

The correct answer should be

```bash
[]
```

And my group implementation is correct