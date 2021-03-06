# radio_transients


[![Issues](https://img.shields.io/github/issues/josephwkania/radio_transients?style=flat-square)]()
[![Forks](https://img.shields.io/github/forks/josephwkania/radio_transients?style=flat-square)]()
[![Stars](https://img.shields.io/github/stars/josephwkania/radio_transients?style=flat-square)]()
[![License](https://img.shields.io/github/license/josephwkania/radio_transients?style=flat-square)]()

## Overview

These are my Singularity Recipes for common radio transiet software.
There are three containers

### radio_transients
Contains everything (CPU+GPU)
 
    CUDA 10.2
    fetch          https://github.com/devanshkv/fetch
    heimdall       https://sourceforge.net/p/heimdall-astro/wiki/Use/
    - dedisp       https://github.com/ajameson/dedisp
    iqrm_apollo    https://gitlab.com/kmrajwade/iqrm_apollo
    jupyterlab     https://jupyter.org/
    PRESTO         https://www.cv.nrao.edu/~sransom/presto/
    psrdada        http://psrdada.sourceforge.net/
    psrdada-python https://github.com/TRASAL/psrdada-python
    psrcat         https://www.atnf.csiro.au/people/pulsar/psrcat/download.html
    pysigproc      https://github.com/devanshkv/pysigproc
    riptide        https://github.com/v-morello/riptide
    sigproc        https://github.com/SixByNine/sigproc
    Tempo          http://tempo.sourceforge.net/
    RFIClean       https://github.com/ymaan4/RFIClean
    YAPP           https://github.com/jayanthc/yapp
    your           https://github.com/thepetabyteproject/your


### radio_transients_cpu
Contains CPU based programs

    iqrm_apollo
    jupyterlab   
    PRESTO
    psrcat
    pysigproc
    riptide
    sigproc
    Tempo 
    RFIClean
    YAPP  
    your  

### radio_transients_gpu
Contains gpu based programs

    CUDA 10.2
    fetch      
    jupyterlab
    heimdall
    - dedisp 
    psrdada 
    psrdada-python
    your

### How to use
You can mount a directory with `-B /dir/on/host:/mnt`, which will mount `/dir/on/host` to `/mnt` in the container. 
Your `$HOME` automatically gets mounted.

For the gpu processes, you must pass `--nv` when running singularity.

`singularity shell --nv -B /data:/mnt radio_transients_gpu.simg` 
will mount `/data` to `/mnt`, give you GPU access, and drop you into the interactive shell. 

`singularity exec --nv -B /data:/mnt radio_transients_gpu.simg your_heimdall.py -f /mnt/data.fil` 
will mount `/data` to `/mnt`, give you GPU access, and run your_heimdall.py without entering the container.
If the data is in your `$HOME` of a subdirectory, you should need to mount. 

### shub
These are build by singularity hub at: 

