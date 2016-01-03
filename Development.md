# Python development

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

## Get version

pyscca utilizes date-based version identifiers; the get_version() method returns a unicode object:

```
pyscca.get_version()
u'20151226'
```

## Open file

```
scca_file = pyscca.file()

scca_file.open("CMD.EXE-087B4001.pf")

scca_file.close()
```

The explicit call to scca_file.close() is not required.

## Open file using a file-like object
```
file_object = open("CMD.EXE-087B4001.pf", "rb")

scca_file = pyscca.file()

scca_file.open_file_object(file_object)

scca_file.close()
```

The explicit call to scca_file.close() is not required.
