Software
===========

Here you can find the list of currently available software packages and some specific manuals if relevant.

List
--------------------

| ants (neurodebian)
| docker (official repo)
| singularity (neurodebian)
| matlab + matlab-support dep: libxt6
| python 2.7
| python 3.6
| fsl (fslinstaller.py)
| dti-tk dep: libgl1
| mrtrix3 dep: git g++ python python-numpy libeigen3-dev zlib1g-dev libqt4-opengl-dev libgl1-mesa-dev libfftw3-dev libtiff5-dev (neurodebian)

ANTs
--------------------

..  caution:: The most updated version (clone of github repository) is located in /opt/software/ants_scripts/.
  Use absolute path if you want to be sure that there are no bugs in the ANTs scripts.
  However, default paths are set to neurodebian's installation (scripts & binaries) for better compatibility.

Parallelization and multithreading
^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^

ANTs enables parallel computation on 2 different levels - parallel execution of ANTs scripts and multithreaded executables of ITK library. Additionally, you can easily parallelize your scripts with GNU parallel [1]_ on top of it (eg. in case of multiple subjects). Make sure whether it is still true for current ANTs implementation. Here is the list of available options:

* bash global ``ITK_GLOBAL_DEFAULT_NUMBER_OF_THREADS`` (default: 8)
* buildtemplateparallel parameters ``-j`` & ``-c`` (paralell execution of max 2 scripts with j=2 & c=2)
* GNU parallel

It is highly advisable not to exceed 16 (physical) or 32 (hyperthreaded) number of available cores on Calcus. For example you can run 2 parallel jobs in buildtemplateparallel.sh with ``-j 2 -c 2`` with default ITK_GLOBAL...=8. The script will be executed on 8-16 cores depending on how many ANTs were prepared by btp.sh at the moment. Optionally, one can parallelize 2 subjects on top of it with GNU parallel resulting in 16-32 cores occupation.

.. [1] O. Tange (2018): GNU Parallel 2018, March 2018, https://doi.org/10.5281/zenodo.1146014.
