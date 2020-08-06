# zgoubi-metadata

Useful metadata for creating zgoubi interfaces

Currently provides description of zgoubi elements in a yaml format.

Can be used by importing the module and using function that will return a dictionary of elements.

```
from zgoubi_metadata import elements

es_yaml = elements.get_raw_yaml()
es_parsed = elements.get_parsed()

```

Also the data files can be accessed through the `pkg_resources` interface.

```
import pkg_resources

pkg_resources.resource_listdir("zgoubi_metadata", "data/elements_yaml/")

drift_yaml = pkg_resources.resource_string("zgoubi_metadata", "data/elements_yaml/DRIFT.yaml")
```

## Definition of Zgoubi elements in YAML

The [`YAML` format, https://yaml.org] ("YAML is a human friendly data serialization standard for all programming languages.") has been chosen for its simplicity and for its ability to be read from any other language. Great 
libraries and support exists in `C`, `C++`, `Javasript`, many others, and of course `python`.

Each Zgoubi element is defined in a `YAML` *document*. A `YAML` file consists either of a single (implicit) document or 
of multiple documents. For simplicity, this repository describes each element in a separate `YAML` file with a single 
implicit document. The document contains a mapping with the following keys:

- **zgoubi_name**: the keyword of the element as defined by Zgoubi
- **params**: the parameters of the element. See below.
- **template**:
- **cond_sections**:
- **subelements**:
- **doc**: 


It contains a nested mapping. Each key is the name of a parameter while 
the values are mappins 