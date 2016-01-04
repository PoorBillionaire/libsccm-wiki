# Python Development

This page describes a few snippets of Python code which can be used to get up and running with pyscca quickly.

## Import

The remainder of this page assumes you have [built](https://github.com/libyal/libscca/wiki/Building) and imported the pyscca module in to your script, using the ```import``` declaration above your Python code:

```import pyscca```

## Introspection

General assistance can be obtained by utilizing Python's builtin introspection features:

```
>>>help(pyscca)

CLASSES
    __builtin__.object
        file
        file_metrics
        volume_information    
...
...
...

```

```
>>>help(pyscca.file)

class file(__builtin__.object)
 |  pyscca file object (wraps libscca_file_t)
 |  
 |  Methods defined here:
 |  
 |  __init__(...)
 |      x.__init__(...) initializes x; see help(type(x)) for signature
 |  
 |  close(...)
 |      close() -> None
 |      
 |      Closes a file.

...
...
...
```

## Get Version

pyscca utilizes date-based version identifiers; the get_version() method returns a unicode object:

```
pyscca.get_version()
u'20151226'
```

## Open File

By utilizing the open() and open_file_object() methods, the Developer creates a pyscca.file() object which serves as the entry point to various Prefetch file attributes. Instantiate this object like so:

```
>>> scca = pyscca.open("LS.EXE-4B79138E.pf")

>>> print scca.get_executable_filename()
LS.EXE

>>> print scca.run_count
5
```

**The explicit call to scca_file.close() is not required.**

## Open File Object

```
>>> with open("/home/adam/Prefetch_10/LS.EXE-4B79138E.pf", "rb") as f:
...     scca = pyscca.open_file_object(f)
...     print scca.get_executable_filename()
...     print scca.run_count
... 
LS.EXE
5
```
'''

**The explicit call to scca_file.close() is not required.**
