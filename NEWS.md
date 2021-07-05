# epicrop 0.0.0.9006

# epicrop 0.0.0.9005

## Minor changes

* Only import _data.table_ functions as necessary, don't import whole package.

## Bug fixes

* Convert `wth` (weather input object) to a data.table type object internally if it is not already one.
Prior, if the object was not a data.table, `SEIR()` would fail with a message that the dates did not align.
This should fix that issue and any data.frame type object including a tibble can be provided now.
Thanks to Jean Fabrice Adanve for helping me find this bug.

# epicrop 0.0.0.9004

## Bug fixes

* Fixes bug where the relative humidity checks in SEIR() only checked if the daily RH value was equal to (`==`) not equal to or greater than (`>=`) the set parameter for `rhlim` (default is 90%).

* Example for `SEIR()` in roxygen section now works properly when executed by the user.

## Major changes

* Any default parameter values are moved from `SEIR()` to the `predict_()` functions themselves, so any calls directly to `SEIR()` must specify all parameters.

* Deleted `inst/alt_versions/tungrov2.R` file.

* Deleted `inst/workflows/spatsim.R` file. 

## Minor changes

* Edit documentation for better clarity

* Better commenting in code for self and others' reference

* `SEIR()` is simplified and further optimised
  * In some cases in the `for()` loop, the value of `day + 1` was repeatedly calculated and assigned to a new object. This has been corrected with a single object, `d1` being created at the beginning of each loop instance.
  * In some cases where RH, TEMP or RAIN are repeatedly checked against, vectors of these three values are created outside the loop to save time when checking or extracting values.
  * Redundant code and other unused objects are cleaned up and removed.
  
* Standardise library loading calls to use standard evaluation in documentation.

* Standardise italics to use "_" rather than "*".

* Use `ggplot2::theme_classic()` for example figures in README and epicrop vignette.

# epicrop 0.0.0.9003

* Added a `NEWS.md` file to track changes to the package.