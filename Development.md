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

**The explicit call to scca.close() is not required.**

## Open File Object

```
>>> with open("LS.EXE-4B79138E.pf", "rb") as f:
...     scca = pyscca.open_file_object(f)
...     print scca.get_executable_filename()
...     print scca.run_count
... 
LS.EXE
5
```

**The explicit call to scca.close() is not required.**

# Filenames

The ```filenames``` object lists the resources which the executable in question loaded during its first 10 seconds of execution. This is an iterable object:

```
>>> for i in scca.filenames:
...     print i
... 
\VOLUME{01d11b57aa4f5b10-e8aabf9f}\WINDOWS\SYSTEM32\NTDLL.DLL
\VOLUME{01d11b57aa4f5b10-e8aabf9f}\WINDOWS\SYSTEM32\KERNEL32.DLL
\VOLUME{01d11b57aa4f5b10-e8aabf9f}\WINDOWS\SYSTEM32\KERNELBASE.DLL
\VOLUME{01d11b57aa4f5b10-e8aabf9f}\WINDOWS\SYSTEM32\LOCALE.NLS
...
...
...
```

Additionally, a bit of meta related to the filenames structure is available via the ```number_of_filenames``` attribute:

```
>>> print scca.number_of_filenames
25
```

## Further Help

Obtain more help by utilizing introspection functionality on the pyscca object itself:

```
>>> dir(scca)
['__class__', '__delattr__', '__doc__', '__format__', '__getattribute__', '__hash__', '__init__', '__new__',
'__reduce__', '__reduce_ex__', '__repr__', '__setattr__', '__sizeof__', '__str__', '__subclasshook__', 'close',
'executable_filename', 'file_metrics_entries', 'filenames', 'format_version', 'get_executable_filename',
'get_file_metrics_entry', 'get_filename', 'get_format_version', 'get_last_run_time', 'get_last_run_time_as_integer',
'get_number_of_file_metrics_entries', 'get_number_of_filenames', 'get_number_of_volumes', 'get_prefetch_hash',
'get_run_count', 'get_volume_information', 'number_of_file_metrics_entries', 'number_of_filenames', 'number_of_volumes',
'open', 'open_file_object', 'prefetch_hash', 'run_count', 'signal_abort', 'volumes']

```
