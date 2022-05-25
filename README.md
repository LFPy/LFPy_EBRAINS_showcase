# LFPy showcase

This Lab contains various examples on how `LFPy` (https://github.com/LFPy/LFPy, https://LFPy.rtfd.io) can be utilized in jupyter notebooks running on cloud infrastructure such as EBRAINS (https://wiki.ebrains.eu/bin/view/Collabs/), 
as well  HPC infrastructure via EBRAINS and Unicore (https://www.unicore.eu/about-unicore/case-studies/the-human-brain-flagship/). 

## Collab URL: 
https://wiki.ebrains.eu/bin/view/Collabs/lfpy-showcase


## Using these files on EBRAINS: 
We recommend choosing the kernel named `EBRAINS_experimental_release`, 
as this provides a virtual environment wherein `LFPy` and it's dependencies
are already installed.


## Installation of LFPy
In other environments where `LFPy` is not preinstalled such as Google Colab (https://colab.research.google.com), installation can be done by issuing in a notebook:
```
!pip install LFPy
```

After installation, the package can be imported as
```
import LFPy
```

The suite of unit tests can be executed by issuing
```
LFPy.run_tests()
```

### Troubleshooting
In case a number of tests fail a likely cause is that NEURON NMODL (.mod) files were not compiled during installation because the 
NEURON-provided `nrnivmodl` script and other binaries was not in `PATH`. 
This issue may be fixed by restarting the kernel, updating `PATH` and reinstalling `LFPy`:
```
import os
import neuron
binpath = os.path.join(neuron.__path__[0].split('lib')[0], 'bin')
os.environ['PATH'] = f"{binpath}:{os.environ['PATH']}"
```

Followed by:
```
!pip install --upgrade --no-deps --force-reinstall --no-cache LFPy
```
