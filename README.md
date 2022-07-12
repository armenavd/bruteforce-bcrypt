# bruteforce-bcrypt

The National Cyber Security Centre (NCSC) has published a [list of the 100,000 most common passwords](https://ncsc.gov.uk/static-assets/documents/PwnedPasswordsTop100k.txt).


```bash
py main.py
````
to start the 8threads program

There is the code, if you want to use it:

```python
#!/usr/bin/env python3

import bcrypt
import hashlib
import threading

def splitlist(inputlist):
  n=len(lines)
  return inputlist[:n//8],inputlist[n//8:2*n//8],inputlist[2*n//8:3*n//8],inputlist[3*n//8:4*n//8],inputlist[4*n//8:5*n//8],inputlist[5*n//8:6*n//8],inputlist[6*n//8:7*n//8],inputlist[7*n//8:n]

def find(lines):
    count = 0
    for line in lines :
        count = (count +1)
        t = line.replace("\n", "")
        print(t , " " , count*8)
        global stop_threads
        if (bcrypt.hashpw(t.encode('utf-8'), hashed)) == hashed:
            stop_threads = True
            print("The password is :   " + t)
            break;
        if stop_threads:
            break

f=open("fr2.txt","r",encoding='utf-8')
lines=f.readlines()
f.close()

password = input("Enter hashed password, example: $2y$10$JcHq2SY9FFk2ngaQ9ZuXTOaGaHNhj8fWYR2E.tv0LLIBBspaYEOA. \nYour turn now: ")
hashed = bytes(password.encode('utf-8'))

first,sec,three,four, five, six, seven , eight =splitlist(lines)

stop_threads = False

t1 = threading.Thread(target=find, args=(first,))
t2 = threading.Thread(target=find, args=(sec,))
t3 = threading.Thread(target=find, args=(three,))
t4 = threading.Thread(target=find, args=(four,))
t5 = threading.Thread(target=find, args=(five,))
t6 = threading.Thread(target=find, args=(six,))
t7 = threading.Thread(target=find, args=(seven,))
t8 = threading.Thread(target=find, args=(eight,))

t1.start()
t2.start()
t3.start()
t4.start()
t5.start()
t6.start()
t7.start()
t8.start()
```

