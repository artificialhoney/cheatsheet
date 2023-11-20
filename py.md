---
layout: default
title: py
parent: Cheatsheet
nav_order: 2
---

# py

## [How to ignore deprecation warnings in Python](https://stackoverflow.com/questions/879173/how-to-ignore-deprecation-warnings-in-python)

```py
import warnings
warnings.filterwarnings("ignore", category=DeprecationWarning)
```

## [Map an array into another array](https://stackoverflow.com/questions/56386503/map-an-array-into-another-array)

```py
[x for ticket in raw for x in transform(ticket)]
```


## [How do I concatenate two lists](https://stackoverflow.com/questions/1720421/how-do-i-concatenate-two-lists-in-python)

```py
listone = [1, 2, 3]
listtwo = [4, 5, 6]

joinedlist = listone + listtwo
```

## [How to split by comma and strip white spaces](https://stackoverflow.com/questions/4071396/how-to-split-by-comma-and-strip-white-spaces-in-python)

```py
my_string = "blah, lots  ,  of ,  spaces, here "
result = [x.strip() for x in my_string.split(',')]
```

## [Get difference between two lists with Unique Entries](https://stackoverflow.com/questions/3462143/get-difference-between-two-lists-with-unique-entries)

```py
s = set(temp2)
temp3 = [x for x in temp1 if x not in s]
```

## [What does enumerate() mean?](https://stackoverflow.com/questions/22171558/what-does-enumerate-mean)

```py
for count, elem in enumerate(elements):
    print(count, elem)
```

## [How do I convert a PIL Image into a NumPy array](https://stackoverflow.com/questions/384759/how-do-i-convert-a-pil-image-into-a-numpy-array)

```py
I = numpy.asarray(PIL.Image.open('test.jpg'))
```

## [What is a cross-platform way to get the home directory?](https://stackoverflow.com/questions/4028904/what-is-a-cross-platform-way-to-get-the-home-directory)

```py
from pathlib import Path
home = str(Path.home())
```

## [How do I make a python script executable](https://stackoverflow.com/questions/27494758/how-do-i-make-a-python-script-executable)

```py
from setuptools import setup
setup(
    name='myscript',
    version='0.0.1',
    entry_points={
        'console_scripts': [
            'myscript=myscript:run'
        ]
    }
)
```

## [How do I create a directory, and any missing parent directories?](https://stackoverflow.com/questions/273192/how-do-i-create-a-directory-and-any-missing-parent-directories)

```py
from pathlib import Path
Path("/my/directory").mkdir(parents=True, exist_ok=True)
```


## [Random hash in Python](https://stackoverflow.com/questions/976577/random-hash-in-python)

```py
import random

hash = random.getrandbits(128)

print("hash value: %032x" % hash)
```


## [How to delete the contents of a folder](https://stackoverflow.com/questions/185936/how-to-delete-the-contents-of-a-folder)

```py
import shutil
shutil.rmtree('/path/to/folder')
```


## [How to set default value for variable](https://stackoverflow.com/questions/36321344/how-to-set-default-value-for-variable)

```py
string = string or "defaultValue"
```


## [How to fill default parameters in yaml file](https://stackoverflow.com/questions/36831998/how-to-fill-default-parameters-in-yaml-file-using-python)

```py
value = a.get('key', 'default')
```

## [What does ** (double star/asterisk) and * (star/asterisk) do for parameters?](https://stackoverflow.com/questions/36901/what-does-double-star-asterisk-and-star-asterisk-do-for-parameters)

```py
def foo(bar, lee):
    print(bar, lee)

baz = [1, 2]

foo(*baz)
```


## [Call function without optional arguments if they are None](https://stackoverflow.com/questions/52494128/call-function-without-optional-arguments-if-they-are-none)

```py
kwargs = dict(p1='FOO', p2=None)

alpha(**{k: v for k, v in kwargs.items() if v is not None})
```


## [How can I merge two Python dictionaries in a single expression?](https://stackoverflow.com/questions/38987/how-do-i-merge-two-dictionaries-in-a-single-expression-in-python)

```py
z = x | y
```

## [Glob multiple filetypes](https://stackoverflow.com/questions/4568580/python-glob-multiple-filetypes)

```py
import glob
types = ('*.pdf', '*.cpp')
files_grabbed = []
for files in types:
    files_grabbed.extend(glob.glob(files))
```

## [Generating an MD5 checksum of a file](https://stackoverflow.com/questions/3431825/generating-an-md5-checksum-of-a-file)

```py
import hashlib
def md5(fname):
    hash_md5 = hashlib.md5()
    with open(fname, "rb") as f:
        for chunk in iter(lambda: f.read(4096), b""):
            hash_md5.update(chunk)
    return hash_md5.hexdigest()
```


## [How to merge dictionaries of dictionaries](https://stackoverflow.com/questions/7204805/how-to-merge-dictionaries-of-dictionaries)

```py
def merge(a: dict, b: dict, path=[]):
    for key in b:
        if key in a:
            if isinstance(a[key], dict) and isinstance(b[key], dict):
                merge(a[key], b[key], path + [str(key)])
            elif a[key] != b[key]:
                raise Exception('Conflict at ' + '.'.join(path + [str(key)]))
        else:
            a[key] = b[key]
    return a
```

## [What is the right way to treat Python argparse.Namespace() as a dictionary?](https://stackoverflow.com/questions/16878315/what-is-the-right-way-to-treat-python-argparse-namespace-as-a-dictionary)

```py
d = vars(args)
```

## [File as command line argument for argparse](https://stackoverflow.com/questions/11540854/file-as-command-line-argument-for-argparse-error-message-if-argument-is-not-va)

```py
from argparse import ArgumentParser
import os.path


def is_valid_file(parser, arg):
    if not os.path.exists(arg):
        parser.error("The file %s does not exist!" % arg)
    else:
        return open(arg, 'r')  # return an open file handle


parser = ArgumentParser(description="ikjMatrix multiplication")
parser.add_argument("-i", dest="filename", required=True,
                    help="input file with two matrices", metavar="FILE",
                    type=lambda x: is_valid_file(parser, x))
args = parser.parse_args()

A, B = read(args.filename)
C = ikjMatrixProduct(A, B)
printMatrix(C)
```
