# Qiskit Metal 
[![License](https://img.shields.io/github/license/Qiskit/qiskit-metal.svg?style=popout-square)](https://opensource.org/licenses/Apache-2.0)<!--- long-description-skip-begin -->[![Release](https://img.shields.io/github/release/Qiskit/qiskit-metal.svg?style=popout-square)](https://github.com/Qiskit/qiskit-metal/releases)<!--- long-description-skip-begin -->[![DOI](https://zenodo.org/badge/DOI/10.5281/zenodo.4618153.svg)](https://doi.org/10.5281/zenodo.4618153)
>  Quantum hardware design and analysis
![Welcome to Qiskit Metal!](docs/images/zkm_banner.png 'Welcome to Qiskit Metal')
Qiskit is an open-source framework for working with noisy quantum computers at the level of pulses, circuits, and algorithms.
While much of Qiskit is made up of elements that each work together to enable quantum computing, this element, Metal, is an open-source framework for engineers and scientists to design superconducting quantum devices with ease.
## Installation
We encourage installing Qiskit Metal via the pip tool (a python package manager).
```bash
pip install qiskit-metal
```
PIP will handle all dependencies automatically and you will always install the latest (and well-tested) version.
To install from source, follow the instructions in the [documentation](https://qiskit.org/documentation/metal/installation.html).
My First 
## Creating Your First Quantum Component (A Transmon Qubit) in Qiskit Metal:
Now that Qiskit Metal is installed, it's time to begin working with it.
We are ready to try out a quantum chip example, which is simulated locally using
the Qiskit MetalGUI element. This is a simple example that makes a qubit.
```
$ python
```
from qiskit_metal import MetalGUI, Dict, open_docs
%metal_heading Welcome to Qiskit Metal!
```python
>>> from qiskit_metal import designs, draw
>>> from qiskit_metal import MetalGUI, Dict, open_docs
>>> design = designs.DesignPlanar()
>>> design.overwrite_enabled = True
>>> design.chips.main
>>> design.chips.main.size.size_x = '11mm'
>>> design.chips.main.size.size_y = '9mm'
>>> gui = MetalGUI(design)
```
Launch the Qiskit Metal GUI to interactively view, edit, and simulate a QDesign:
```python
>>> gui = MetalGUI(design)
```
A script is available [here](https://qiskit.org/documentation/metal/tut/overview/1.1%20High%20Level%20Demo%20of%20Qiskit%20Metal.html), where we also show the overview of Qiskit Metal.
### Creating Your First Quantum Component (A Transmon Qubit) in Qiskit Metal:
You can create a ready-made transmon qubit from the QComponent Library, qiskit_metal.qlibrary.qubits. transmon_pocket.py is the file containing our qubit so transmon_pocket is the module we import. The TransmonPocket class is our transmon qubit. Like all quantum components, TransmonPocket inherits from QComponent
#### Let's create a new qubit by creating an object of this class.
```python
>>> from qiskit_metal.qlibrary.qubits.transmon_pocket import TransmonPocket
>>> q1 = TransmonPocket(design, 'Q1', options=dict(connection_pads=dict(a=dict())))
>>> gui.rebuild()
>>> gui.edit_component('Q1')
>>> gui.autoscale()
```
#### Change options.
```python
>>> q1.options.pos_x = '0.5 mm'
>>> q1.options.pos_y = '0.25 mm'
>>> q1.options.pad_height = '225 um'
>>> q1.options.pad_width  = '250 um'
>>> q1.options.pad_gap    = '50 um'
```
#### Update the component geoemtry, since we changed the options.
```python
>>> gui.rebuild()
```
#### Get a list of all the qcomponents in QDesign and then zoom on them.
```python
>>> all_component_names = design.components.keys()
>>> gui.zoom_on_components(all_component_names)
```
#### Closing the Qiskit Metal GUI.
```python
>>> gui.main_window.close()
```
## Contribution Guidelines
If you'd like to contribute to Qiskit Metal, please take a look at our
[contribution guidelines](CONTRIBUTING.md). This project adheres to Qiskit's [code of conduct](CODE_OF_CONDUCT.md). By participating, you are expected to uphold this code.
We use [GitHub issues](https://github.com/Qiskit/qiskit-metal/issues) for tracking requests and bugs. Please
[join the Qiskit Slack community](https://ibm.co/joinqiskitslack)
and use our [Qiskit Slack channel](https://qiskit.slack.com) for discussion and simple questions.
For questions that are more suited for a forum we use the Qiskit tag in the [Stack Exchange](https://quantumcomputing.stackexchange.com/questions/tagged/qiskit).
## Next Steps
Now you're set up and ready to check out some of the other examples from our
[Qiskit Metal Tutorials](https://github.com/Qiskit/qiskit-metal/tutorials/) repository or [Qiskit Metal Documentation](https://qiskit.org/documentation/metal/tut/).
## Authors and Citation
Qiskit Metal is the work of [many people](https://github.com/Qiskit/qiskit-metal/pulse/monthly) who contribute to the project at different levels. Metal was conceived and developed by [Zlatko Minev](zlatko-minev.com) at IBM; then co-led with Thomas McConkey. If you use Qiskit Metal, please cite as per the included [BibTeX file](https://github.com/Qiskit/qiskit-metal/blob/main/Qiskit_Metal.bib). For icon attributions, see [here](/qiskit_metal/_gui/_imgs/icon_attributions.txt).
## Changelog and Release Notes
The changelog for a particular release is dynamically generated and gets
written to the release page on Github for each release. For example, you can
find the page for the `0.0.3` release here:
https://github.com/Qiskit/qiskit-metal/releases/tag/0.0.3
The changelog for the current release can be found in the releases tab:
[![Releases](https://img.shields.io/github/release/Qiskit/qiskit-metal.svg?style=popout-square)](https://github.com/Qiskit/qiskit-metal/releases)
The changelog provides a quick overview of notable changes for a given
release.
Additionally, as part of each release detailed release notes are written to
document in detail what has changed as part of a release. This includes any
documentation on potential breaking changes on upgrade and new features.
## License
[Apache License 2.0](LICENSE.txt)
