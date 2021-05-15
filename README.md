# radio_transients


[![Issues](https://img.shields.io/github/issues/josephwkania/radio_transients?style=flat-square)]()
[![Forks](https://img.shields.io/github/forks/josephwkania/radio_transients?style=flat-square)]()
[![Stars](https://img.shields.io/github/stars/josephwkania/radio_transients?style=flat-square)]()
[![License](https://img.shields.io/github/license/josephwkania/radio_transients?style=flat-square)]()
[![https://www.singularity-hub.org/static/img/hosted-singularity--hub-%23e32929.svg](https://www.singularity-hub.org/static/img/hosted-singularity--hub-%23e32929.svg)](https://singularity-hub.org/collections/5231)


## Overview

These are my Singularity Recipes for common radio transient software.
There are three containers

### radio_transients
Contains everything (CPU+GPU)
 
    CUDA 10.2
    FETCH          https://github.com/devanshkv/fetch  -- In Conda environment `FE`
    heimdall       https://sourceforge.net/p/heimdall-astro/wiki/Use/
    - dedisp       https://github.com/ajameson/dedisp
    htop           https://htop.dev/
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

Get with
`singularity pull shub://josephwkania/radio_transients`

*One of FETCH's dependencies causes PRESTO's Python scripts to fail. 
This necessitated putting them in different environments. 
Everything except for PRESTO is in `RT`, which is loaded by default.
PRESTO is in `PE`, in the shell you can activate this 
with `conda activate PE`. If you need access outside the container,
you should use radio_transients:cpu, which has PRESTO in the default environment. 

### radio_transients_cpu
Contains CPU based programs

    htop
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

Get with
`singularity pull shub://josephwkania/radio_transients:cpu`  
There is an arm version `Singularity.arm`, you can build yourself.

### radio_transients_gpu
Contains gpu based programs

    CUDA 10.2
    FETCH      
    jupyterlab
    heimdall
    - dedisp
    htop 
    psrdada 
    psrdada-python
    your

Get with
`singularity pull shub://josephwkania/radio_transients:gpu`

### How to use
Your `$HOME` automatically gets mounted.
You can mount a directory with `-B /dir/on/host:/mnt`, which will mount `/dir/on/host` to `/mnt` in the container. 

For the gpu processes, you must pass `--nv` when running singularity.

`singularity shell --nv -B /data:/mnt radio_transients_gpu.sif` 
will mount `/data` to `/mnt`, give you GPU access, and drop you into the interactive shell. 

`singularity exec --nv -B /data:/mnt radio_transients_gpu.sif your_heimdall.py -f /mnt/data.fil` 
will mount `/data` to `/mnt`, give you GPU access, and run your_heimdall.py without entering the container.

All the Python scripts are installed in a Conda environment `RT`, this environment is automatically loaded.

You can see the commits and corresponding dates by running `singularity inspect radio_transients.sif`

### shub
These are built on commit by Singularity Hub at: https://singularity-hub.org/collections/5231
They where last built on 15-May-2021

### Improvements
If you come accross bug or have suggestions for improvements, let me know or submit a pull request.

### Thanks
To Kshitij Aggarwal for bug reports and suggestions.
