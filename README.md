# zgoubi-metadata

Useful metadata for creating zgoubi interfaces (see for example [Zgoubidoo](https://github.com/ulb-metronu/zgoubidoo) 
and [pyzgoubi](https://github.com/pyzgoubi)). Currently provides description of zgoubi elements in a `YAML` format.

## Definition of Zgoubi elements in YAML

The [`YAML` format](https://yaml.org) ("YAML is a human friendly data serialization standard for all programming 
languages.") has been chosen for its simplicity and for its ability to be read from any other language. Great 
libraries and support exists in `C`, `C++`, `Javasript`, [many others](https://yaml.org), and of course `python`.

Each Zgoubi element is defined in a `YAML` *document*. A `YAML` file consists either of a single (implicit) document or 
of multiple documents. For simplicity, this repository describes each element in a separate `YAML` file with a single 
implicit document. The document contains a *mapping* with the following keys:

- **zgoubi_name**: the keyword of the element as defined by Zgoubi
- **params**: the parameters of the element. See below.
- **template**:
- **cond_sections**:
- **subelements**:
- **doc**: documentation relevant to the Zgoubi element. The documentation is extracted from the Zgoubi manual and 
formatted as *reStructuredText* (`rst`) (for compatibility wit the `sphinx` documentation generator).

### Definition of parameters

The parameters mapping contains a nested mapping. Each key is the name of a parameter while the values are in turn 
mappings that represent properties of the parameters. The required keys are:

- **type**: identifies the parameter's type: `E` for floating point number, `I` for integers and `X` for strings.
- **unit**: the unit provides the dimensionality of the parameter as well as the unit that is used in the Zgoubi 
input file.
- **default**: the default value provided for the parameter. Sensible values for the default parameters should allow a 
Zgoubi input with elements defined with default values to run without errors.
- **doc**: `docstring` provided for the parameter.

### Definition of conditional sections

Some elements require different input formats depending on the value of some (previously) defined parameters. The 
conditional sections allow to define these *sections* for the Zgoubi element. Each conditional section has a `key` 
which defines the parameter on which the conditional expression applies. 

### Definition of sub-elements

## Using the `zgoubi-metadata` Python module

Can be used by importing the module and using function that will return a dictionary of elements.

```python
from zgoubi_metadata import elements

es_yaml = elements.get_raw_yaml()
es_parsed = elements.get_parsed()

```

Also the data files can be accessed through the `pkg_resources` interface.

```python
import pkg_resources

pkg_resources.resource_listdir("zgoubi_metadata", "data/elements_yaml/")

drift_yaml = pkg_resources.resource_string("zgoubi_metadata", "data/elements_yaml/DRIFT.yaml")
```