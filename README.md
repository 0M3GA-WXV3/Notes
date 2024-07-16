### Day 1
-----------{SSH}----------

WINDOWS:
10.50.24.165

LINUX:
10.50.35.203

```ssh student@10.x.x.x -X```

Command:
terminator

------------{Links}---------

***Setup

https://cctc.cybbh.io/students/students/latest/Day_0_Setup.html

***VMs

https://vta.cybbh.space

***Python Handbook

https://git.cybbh.space/programming/python/public/-/blob/master/activities/Python_Student_Handbook/PyStuHBK.adoc?ref_type=heads

--------{Python}------------

***For loop

```
thing = ["thing1", "thing2"]
for x in thing:
    print(x)
```
-+=+-======================-+=+-

### Day 2

*** Types

str() float() int() bool() tuple() list()

*** Basic Functions

print() type() split() len()

*** Basic Functions

''.join()
variable.split('')
variable.append('')
variable.format('')

-----------{Email Splitters}------------
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
*** Type Casting

```
int(input("Give a number:\n"))
```
*** If Else

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
