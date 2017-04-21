# Stock status estimates from an ensemble of catch-only models 

This repository contains data and code for the paper:

Rosenberg, A. A., K. M. Kleisner, J. Afflerbach, S. C. Anderson, M. Dickey-Collas, A. B. Cooper, M. J. Fogarty, E. A. Fulton, N. L. Gutiérrez, K. J. W. Hyde, E. Jardim, O. P. Jensen, T. Kristiansen, C. Longo, C. V. Minte-Vera, C. Minto, I. Mosqueira, G. C. Osio, D. Ovando, E. R. Selig, J. T. Thorson, J. C. Walsh, and Y. Ye. 2017. Applying a new ensemble approach to estimating stock status of marine fisheries around the world. Conservation Letters. <https://doi.org/10.1111/conl.12363>

The superensemble method used to derive the estimates is described in this paper:

Anderson, S. C., A. B. Cooper, O. P. Jensen, C. Minto, J. T. Thorson, J. C. Walsh, J. Afflerbach, M. Dickey-Collas, K. M. Kleisner, C. Longo, G. C. Osio, D. Ovando, I. Mosqueira, A. A. Rosenberg, and E. R. Selig. 2017. Improving estimates of population status and trend with superensemble models. Fish and Fisheries. <https://doi.org/10.1111/faf.12200>

The superensemble method combines estimates from up to 4 individual catch-only models. The individual models are described and fit as part of this report:

Rosenberg, A. A., M. J. Fogarty, A. B. Cooper, M. Dickey-Collas, E. A. Fulton, N. L. Gutierrez, K. J. W. Hyde, K. M. Kleisner, C. Longo, C. V. Minte-Vera, C. Minto, I. Mosqueira, G. C. Osio, D. Ovando, E. R. Selig, J. T. Thorson, and Y. Ye. 2014. Developing new approaches to global stock status assessment and fishery production potential of the seas. FAO Fisheries and Aquaculture Circular, Rome, Italy.

## Data description 

The raw input data files are in the folder `data-raw`. This folder can be mostly ignored. 

The file `fit-ensemble.Rmd` generates the ensemble model based on a simulated data set and fit this model to the FAO data.

The generated data `data-generated/ensemble-estimates.csv` is the primary output of interest. It contains the following:

`stock` The FAO stock name

`CMSY` The CMSY method estimate of B/Bmsy

`mPRM` The modified panel regression method estimate of B/Bmsy

`COMSIR` The COMSIR method estimate of B/Bmsy

`SSCOM` The SSCOM method estimate of B/Bmsy

`spec_freq_0.05` and `spec_freq_0.02` Spectral densities at frequencies of 0.05 and 0.02

`ensemble_method` The version of the superensemble model used. `full_ensemble` Is the full including all 4 individual estimates. `fao_cmsy`, for example, excludes CMSY because it did not converge or was not available. 

`ensemble` contains the superensemble estimate of B/Bmsy.

## Caveats 

The training dataset was based on 3 life-history types, and may not be reliable for a wider range of species.

The ensemble uses the average B/Bmsy estimates from catch-only models  from the last 5 years of catch data. In other words: B/Bmsy is estimated using 4 catch-only models. These B/Bmsy estimates from the 5 years of data from each model are averaged and then fed into the ensemble model. 

