# IAlf

A configuration change to the [IJava](https://github.com/SpencerPark/IJava) kernel to enable it to execute the [reference implementation](https://github.com/ModelDriven/Alf-Reference-Implementation) of the [Action Language for Foundational UML (Alf)](https://www.omg.org/spec/ALF/About-ALF/). The requirements, installation, configuration and functionality inherits from IJava as applicable to Alf.

### Requirements

1. All requirements of [IJava](https://github.com/SpencerPark/IJava#requirements), including Java JDK >= 9 (tested with [OpenJDK 11](https://jdk.java.net/11/)).

2. [Alf Reference Implementation](https://github.com/ModelDriven/Alf-Reference-Implementation), specifically:
    1. `alfi.jar` found in the `research` branch under `org.modeldriven.alf.interactive/dist/alfi.jar` (at time of writing; subject to change)
    2. `Models` folder found inside `dist/alf.zip`
    3. `Libraries` folder found inside `dist/alf.zip`
        
### Installing

Same as [IJava](https://github.com/SpencerPark/IJava#installing), but with the following **required** environment variables:

1. `IJAVA_CLASSPATH` must include the path to `alfi.jar`.
2. `ALF_LIBRARY_PATH` must be specified as the path to the `Libraries` folder.
3. `ALF_MODEL_PATH` must be specified as the path to the `Models` folder.

Configuring the kernel can be done via environment variables. These can be set on the system or inside the `kernel.json`.  The configuration can be done at install time, which may be repeated as often as desired. The parameters are listed with `python3 install.py -h` as well as below in the list of options. Configuration done via the installer (or `gradlew installKernel --param ...:...`) should use the names in the _Parameter name_ column.

### Configuring

Same as [IJava](https://github.com/SpencerPark/IJava#configuring), but with additional **required** configuration options.

#### List of additional options

| Environment variable | Parameter name | Default | Description |
|----------------------|----------------|---------|-------------|
| `ALF_LIBRARY_PATH` | `alf-library-path` | `""` | Path to the Alf library folder |
| `ALF_PATH_PATH` | `alf-path-path` | `""` | Path to the Alf model folder. |

#### Example
`./gradlew installKernel --user --param classpath:/path/to/alfi.jar --param alf-library-path:/path/to/Libraries --param alf-model-path:/path/to/Models`

### Run

Open a notebook as you normally would and select the Alf kernel.

#### Example
```
activity hello() {
    WriteLine("Hello world!");
}
```
```
hello();
```
```
Hello world!
```