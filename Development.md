# Python development

## Get version
```
import pyscca

pyscca.get_version()
```

## Open file
```
import pyscca


scca_file = pyscca.file()

scca_file.open("CMD.EXE-087B4001.pf")

scca_file.close()
```

The explicit call to scca_file.close() is not required.

## Open file using a file-like object
```
import pyscca


file_object = open("CMD.EXE-087B4001.pf", "rb")

scca_file = pyscca.file()

scca_file.open_file_object(file_object)

scca_file.close()
```

The explicit call to scca_file.close() is not required.

## Also see
```
import pyscca

help(pyscca)
help(pyscca.file)
```

