Troubleshooting
===============

This part of the document will address FAQs, known issues, and work arounds.
Please do report to us of issues not listed here, and we will try to keep this document up-to-date.


Conda related
-----------------

Known issues related to conda based installation/execution.

* Library not loaded (libgfortran.3) *
^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^

This issue was encountered in the following scenario: ::

	Conda version: 4.6.2
	OSX version: 10.14.4

	Error:

	Abort trap: 6
	dyld: Library not loaded: @rpath/libgfortran.3.dylib
  	Referenced from: /Users/...../rapid08/lib/R/lib/libRblas.dylib
  	Reason: image not found

This seems to be an issue with MacOS, and conda usage after recent updates. For some reason these fortran libraries are getting disabled when you activate the conda environment. The workaround is to change the order of PATH variable to access /usr/local/bin, and /usr/bin folders before the Conda environments bin folder.

For instance, the following PATH variable: ::

	/Users/xxx/miniconda2/envs/rapid/bin:/Users/xxx/miniconda2/condabin:/Users/xxx/miniconda2/bin:/usr/local/bin:/usr/bin:/bin:/usr/sbin:/sbin:/opt/X11/bin

Should be changed to: ::

	export PATH=/Users/xxx/miniconda2/condabin:/Users/xxx/miniconda2/bin:/usr/local/bin:/usr/bin:/bin:/usr/sbin:/sbin:/opt/X11/bin:/Users/xxx/miniconda2/envs/rapid/bin


R - related
-------------

If there are some errors with R modules, Open R by staying in the conda environment, and update the R modules: ::

    update.packages(ask = FALSE, checkBuilt = TRUE)
