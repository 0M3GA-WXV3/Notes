# Day 1

<hr>

## SSH

WINDOWS:
10.50.24.165

LINUX:
10.50.35.203

```ssh student@10.x.x.x -X```

Command:
terminator

## Links

### Setup

https://cctc.cybbh.io/students/students/latest/Day_0_Setup.html

### VMs

https://vta.cybbh.space

### Python Testing
https://runestone.academy/ns/books/published/fopp/Files/ChapterAssessment.html

### Python Handbook

https://git.cybbh.space/programming/python/public/-/blob/master/activities/Python_Student_Handbook/PyStuHBK.adoc?ref_type=heads


## Python

### For loop

```
thing = ["thing1", "thing2"]
for x in thing:
    print(x)
```


# Day 2

<hr>

### Types

str() 

float() 

int() 

bool() 

tuple() 

list()

### Basic Functions

print() 
type() 
split() 
append()
replace()
len()
ord()

### Basic Methods

''.join()

variable.split('')

variable.append('')

variable.format('')


### Email Splitters
```
email = 'rahkill@marines.mil'
email2 = email.split('@')
email3 = '.'.join(email2)
email4 = email3.split('.')
print(email4)
```
```
blank = []
email = 'chesty@marines.mil'
email2 = email.split('@')
blank.append(email2[0])
blank.append(email2[1].split('.')[0])
blank.append(email2[1].split('.')[1])
print(blank)
```
### Type Casting

```
int(input("Give a number:\n"))
```
### If Else

```
a = int(input('Give me a number:\n'))
b = 35
if b > a:
     print('It is less than 35')
elif a == b:
    print('You gave 35?')
elif a > b:
    print('Dang dude, that is more than 35')
```
### Fizz/Buzz activity
```
#!/usr/bin/env python3
a = int(input('Give me something: '))
if a % 3 == 0 and a % 5 == 0:
    print('Fizzbuzz')
elif a % 3 == 0:
    print('Fizz')
elif a % 5 == 0:
    print('Buzz')
print(a)

```
<hr>

# Day 3


### While loop example
```
#!/usr/bin/env python3
def guess_number(n):
    pass
b = 23
while b == 23: 
    n = int(input('Give me a number:\n'))
    if n < b:
        print('too low')
        n == 0
        continue
    elif n == b:
        print('WIN')
        break
    elif n > b:
        print('too high')
        n == 0
        continue
guess_number(23)
```

### Iterating through list items with While Loop
```
i = 0
list = ['thing1 ', 'thing2 ', 'thing3 ', 'thing4 ', 'thing5 ', 'thing6 ', 'thing7 ', 'thing8 ', 'thing9 ', 'thing10 ']
while i < len(list):
  print(list[i])
  i += 1
```

## Reading/Writing to a file

### Writing

```
with open('test.txt', 'w') as fp:
fp.write('')
```

### Reading

```
with open('test.txt', 'r') as outfile:
outfile.read('')
```

### Appending

Example

```
with open('test.txt', 'a') as fp:
fp.writelines('')
```

List by every 3rd word

```
three = []
with open('school_prompt.txt') as fp:
    for line in fp:
        three.append(line.split()[2])
```

List by every word with certain character

```
p_words = []
with open('school_prompt.txt') as fp:
    for line in fp:
            for words in line.split():
                for char in words:
                    if char == 'p':
                        p_words.append(words)
                        break
```

### Args & Kwargs

Args will have 1 * and will be treated like a normal variable without *

Kwargs will have 2 * and be formatted as a variable length argument
