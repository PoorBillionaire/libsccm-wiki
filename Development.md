# Python development

This page describes a few short snippets of Python code which can be used to get up and running with pyscca quickly.

## Import

The remaining documentation assumes you have built and imported the pyscca module:

```
import pyscca
```

## Get version
```
pyscca.get_version()
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

## Also see
```
help(pyscca)
help(pyscca.file)
```

