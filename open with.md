simple example:
``` 
import sys
try:
    #if "open with" has been used
    print(sys.argv[1])
except:
    #do nothing
    pass
```
usage example:
``` 
import sys
from tkinter import filedialog

filetypes = (('Text files', '*.txt'),('All files', '*.*'))

#if filename is not specified, ask for a file
def openfile(filename = ''):
    #print contents of file
    if filename == '':
        filename = filedialog.askopenfilename(title='Open A File',filetypes=filetypes)
    with open(filename,'r', encoding="utf-8") as file:
        read = file.read()
    print(read)



try:
    #if "open with" has been used
    openfile(filename = sys.argv[1].encode('unicode_escape'))
except:
    #ask for a file
    openfile()

```
then compile it to exe with nuitka (or whatever tool you use),<br>
and try it. 
<br>or (for testing, without having to compile it every time you make a change):<br>
make a .py file 
```
from subprocess import call
from sys import argv
call(f'py print.py {argv[1]}')
```
then compile *that* to exe,<br>
so you dont have to compile the actual program every time.
