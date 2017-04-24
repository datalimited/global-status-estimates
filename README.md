# Stock status estimates from an ensemble of catch-only models 

This repository contains data and code for the paper:

Rosenberg, A. A., K. M. Kleisner, J. Afflerbach, S. C. Anderson, M. Dickey-Collas, A. B. Cooper, M. J. Fogarty, E. A. Fulton, N. L. Gutiérrez, K. J. W. Hyde, E. Jardim, O. P. Jensen, T. Kristiansen, C. Longo, C. V. Minte-Vera, C. Minto, I. Mosqueira, G. C. Osio, D. Ovando, E. R. Selig, J. T. Thorson, J. C. Walsh, and Y. Ye. 2017. Applying a new ensemble approach to estimating stock status of marine fisheries around the world. Conservation Letters. <https://doi.org/10.1111/conl.12363>

The superensemble method used to derive the estimates is described in this paper:

Anderson, S. C., A. B. Cooper, O. P. Jensen, C. Minto, J. T. Thorson, J. C. Walsh, J. Afflerbach, M. Dickey-Collas, K. M. Kleisner, C. Longo, G. C. Osio, D. Ovando, I. Mosqueira, A. A. Rosenberg, and E. R. Selig. 2017. Improving estimates of population status and trend with superensemble models. Fish and Fisheries. <https://doi.org/10.1111/faf.12200>

The superensemble method combines estimates from up to 4 individual catch-only models. The individual models are described and fit as part of this report:

Rosenberg, A. A., M. J. Fogarty, A. B. Cooper, M. Dickey-Collas, E. A. Fulton, N. L. Gutierrez, K. J. W. Hyde, K. M. Kleisner, C. Longo, C. V. Minte-Vera, C. Minto, I. Mosqueira, G. C. Osio, D. Ovando, E. R. Selig, J. T. Thorson, and Y. Ye. 2014. Developing new approaches to global stock status assessment and fishery production potential of the seas. FAO Fisheries and Aquaculture Circular, Rome, Italy.

## Data description 

The generated data file `data-generated/ensemble-estimates.csv` ([link to raw data](https://raw.githubusercontent.com/datalimited/global-status-estimates/master/data-generated/ensemble-estimates.csv?token=AABLlWL4pzOWoHz2yBxWrNJx3vyY_ikPks5ZA5rywA%3D%3D)) is the primary output of interest. It contains the following:

`stock` The FAO stock name

`CMSY` The CMSY method estimate of B/Bmsy 

`mPRM` The modified panel regression method estimate of B/Bmsy

`COMSIR` The COMSIR method estimate of B/Bmsy

`SSCOM` The SSCOM method estimate of B/Bmsy

`spec_freq_0.05` and `spec_freq_0.02` Spectral densities of the catch timeseries at frequencies of 0.05 and 0.02

`ensemble_method` The version of the superensemble model used. `full_ensemble` Is the full ensemble including all 4 individual estimates. `fao_cmsy`, for example, excludes CMSY because it did not converge or was not available. 

`ensemble` contains the superensemble estimate of B/Bmsy.

The raw input data files are in the folder `data-raw`. This folder can be mostly ignored and is there so that the R code is reproducible.

The file `fit-ensemble.Rmd` generates the ensemble model based on a simulated data set and fit this model to the FAO data.

## Caveats

All estimates are for the average of the last 5 years of data: 2006-2010.

Any catch-only stock status model may not be particularly accurate on a stock-by-stock basis — particularly given that the individual models were not tuned for the unique circumstances of each stock in the paper cited above. Here they were used to determine aggregate status across multiple stocks. For individual stock estimates, these catch only models should only be used if a fuller stock assessment with addition sources of data cannot be performed.

The training dataset was based on 3 life-history types, and may not be reliable for a wider range of species. The superensemble was trained on the simulated fish stock data described in the Rosenberg et al. (2014) FAO technical report cited above.  
