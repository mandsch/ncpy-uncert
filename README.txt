ncpy-uncert
===========

A library that wraps the netcdf4-python library to 'uncertainty-enable' NetCDF files.

This library was written in the context of the UncertWeb project (www.uncertweb.org) and tries to implement
functionality to read and write NetCDF4-U files that comply with the proposed UW convention 
(http://www.uncertweb.org/uploads/presentations/4ac90c10039c39c22b9321badfbe612c1f755318.pdf).

Dependency
==========

- netcdf4-python: http://code.google.com/p/netcdf4-python/

Usage
=====

	>>> import netcdfUWDS as ncuw
	>>> ds = ncuw.ncUncertDS('/home/webuser/testing/netcdf-u4-python/tests/testuncert.nc',keepOriginal = False)
	>>> ds.rootgrp.Conventions
	u'CF-1.4'
	>>> ds.updateConventions()
	True
	>>> ds.rootgrp.Conventions
	u'CF-1.5 UW-1.0'		
	>>> mean = ncuw.uwSummaryVariable(ds.rootgrp,'Min_temperature_mean','f4',('lat','lon'),'mean','Min_temperature',missing_value=999.0)