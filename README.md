# INT-IDS-DataReduction
Pipeline to reduce long-slit spectra taken using IDS on the Isaac Newton Telescope, La Palma

## Pre requisites
This pipeline is based on Python 3, and works best in a Jupyter Notebook environment. Installation instructions for Jupyter Notebook can be found here: https://jupyter.org/install

The following Python packages are needed for this pipeline to function
- numpy
- matplotlib
- astropy
- scipy
- ccdproc
- mpdaf

## Functions

This pipeline performs all the basic CCD data reduction. This is done using the Python package ccdproc, which can be downloaded using `pip install ccdproc` for python2 or `pip3 install ccdproc` for python3

The data reduction steps performed are:
- create a master bias frame
- create a master lamp flat frame
- create a master sky flat frame

- reduce individual science frames. Perform gain correction, bias subtraction, flat fielding and sky subtraction
- median combine reduced science frames into a deep spectrum

- reduce arc frames for wavelength calibration

- wavelength calibrate the 2D science spectrum
- extract and save 1D spectrum from a given position and aperture size. This feature requires the python package mpdaf. This can be downloaded using `pip install mpdaf` for python2 or `pip3 install mpdaf` for python3.

To add: flux calibration

The following reduction code works directly from the full set of images in a given night's observations. As observations are added during the evening, the ImageFileCollection object defined at the beginning needs to be refreshed.

ftp where frames are stored: rsync -av intobs@intdrpc1:/obsdata/inta/20190405/ .
