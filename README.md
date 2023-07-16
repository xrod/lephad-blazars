# lephad-blazars
Results from numerical leptohadronic simulations of 324 gamma-ray blazars.

Based on the publication:

X Rodrigues, V S Paliya, S Garrappa, A Omeliukh, A Franckowiak and W Winter, 
*Leptohadronic Multimessenger Modeling of 324 Gamma-ray Blazars* (2023)

## Example notebook

The notebook `example.ipynb` (Python 3.10) illustrates the usage of the tables in this repository. 

Below we describe in detail the variables and units in each table.

## Model parameters

The file `model_parameters.csv` contains the best-fit parameters of the model. Each line of the table referes to a source in the sample.

It also lists the corresponding flux of neutrinos frome ach source predicted by the model, as well as the peak neutrino energy and event rate in IceCube. 

The table can be loaded, for example, in Python using Pandas: 

```python
import pandas as pd
model_paramters = pd.read_csv('git_directory/model_parameters.csv')
```

This generates a pandas DataFrame with the following columns:


- `'Association'`: Name of associated source
- `'Fermi Name'`: Source denomination in the Fermi *LAC catalogs ([Abdo 2010](https://iopscience.iop.org/article/10.1088/0004-637X/715/1/429), [Ackermann et al 2011](https://iopscience.iop.org/article/10.1088/0004-637X/743/2/171), [Acero et al 2015](https://iopscience.iop.org/article/10.1088/0067-0049/218/2/23))
- `'CGRABS Name'`: Source denomination in the CGraBS catalog ([Healey et al 2007](https://inspirehep.net/literature/760558))
- `'Class'`: Blazar sub-class (FSRQ, LBL, IBL, or HBL)
- `'dec'`: Source declination [deg]
- `'RA'`: Source right ascention [deg]
- `'Redshift'`: Source redshift
- `'Fermi-LAT Flux'`: Gamma-ray flux in the Fermi-LAT range, provided in the respective *LAC catalog [erg/cm2/s]
- `'Disk Luminosity'`: Accretion disk luminsity deduced by [Paliya et al 2017](https://iopscience.iop.org/article/10.3847/1538-4357/aa98e1) [erg/s]
- `'BLR Radius'`: Broad line region radius deduced by [Paliya et al 2017](https://iopscience.iop.org/article/10.3847/1538-4357/aa98e1) [erg/s]
- `'Black Hole Mass'`: Black hole mass estimated by [Paliya et al 2017](https://iopscience.iop.org/article/10.3847/1538-4357/aa98e1) [solar mass units]
- `'Muon Neutrino Flux Best Fit'`: Total muon neutrino flux in the observer's frame predicted by the model [erg/cm2/s]
- `'Muon Neutrino Flux Min'`: Minimum muon neutrino flux in the observer's frame predicted by the model within 1σ of the best fit [erg/cm2/s]
- `'Muon Neutrino Flux Max'`: Maximum muon neutrino flux in the observer's frame predicted by the model within 1σ of the best fit [erg/cm2/s]
- `'IceCube Event Rate Best Fit'`: Number of muon neutrino events per year in IceCube predicted by the model
- `'IceCube Event Rate Min'`: Minimum number of muon neutrino events per year in IceCube predicted by the model, within 1σ of the best fit
- `'IceCube Event Rate Max'`: Maximum number of muon neutrino events per year in IceCube predicted by the model, within 1σ of the best fit
- `'Neutrino Peak Energy Best Fit'`: Peak energy of the predicted neutrino spectrum in the observer's frame (in IceCube terms, "xreal" neutrino energy) [PeV]
- `'Blob Radius Best Fit'`: Best-fit value of the radius of the emission region in the rest frame of the relativitic jet [cm]
- `'B-Field Best Fit'`: Best-fit value of the magnetic field strength in the jet [gauss]
- `'Bulk Lorentz Best Fit'`: Best-fit value of the bulk Lorentz factor of the emitting region 
- `'Dissipation Radius Best Fit'`: Best-fit value of the dissipation radius in the black-hole frame (i.e., the distance between the black hole and the emission region). In the case of BL Lacs, a `0` is listed because the model is not sensitive to this parameter (see Fig. 2 of Rodrigues et al 2023) [cm]
- `'Electron Luminosity Best Fit'`: Best-fit value of the power injected into cosmic-ray electrons, before radiative losses, in the jet rest frame [erg/s]
- `'Electron Min Lorentz Factor Best Fit'`: Best-fit value of the minimum Lorentz factor of the accelerated cosmic-ray electrons, before radiative losses, in the jet rest frame
- `'Electron Max Lorentz Factor Best Fit'`: Best-fit value of the maximum Lorentz factor of the accelerated cosmic-ray electrons, before radiative losses, in the jet rest frame
- `'Electron Spectral Index Best Fit'`: Best-fit value of the spectral index of the accelerated cosmic-ray electrons (assumed to be a power law), before radiative losses
- `'Proton Luminosity Best Fit'`: Best-fit value of the power injected into cosmic-ray protons, before radiative losses, in the jet rest frame. A value of `0` means that the best-fit result is purely leptonic  [erg/s]
- `'Proton Luminosity Min'`: Minimum value of the power injected into cosmic-ray protons, before radiative losses, in the jet rest frame, within 1σ of the best fit. A value of `0` means that the best-fit result is compatible with a purely leptonic solution within 1σ of the best fit [erg/s]
- `'Proton Luminosity Max'`: Maximum value of the power injected into cosmic-ray protons, before radiative losses, in the jet rest frame, within 1σ of the best fit [erg/s]
- `'Proton Max Lorentz Factor Best Fit'`: Best-fit value of the maximum Lorentz factor of the accelerated cosmic-ray protons, before radiative losses, in the jet rest frame.
- `'Proton Min Lorentz Factor Fixed'`: Value of the minimum Lorentz factor of the accelerated cosmic-ray protons, before radiative losses, in the jet rest frame. Fixed to 100 for all sources
- `'Proton Spectral Index Fixed'`: Value of the spectral index of the accelerated cosmic-ray protons (assumed to be a power law), before radiative losses. Fixed to 1 for all sources

## Model results

The `model_results` directory contains one sub-directory for each source, each containing five files:

- `sourcename_flux_components.pdf`: Plot of the SED components separted by their emission mechanism. The color code follows that in Fig. 4 of Rodrigues et al 2023

- `sourcename_flux_total.pdf`: Plot of the total predicted multi-wavelength and neutrino emitted by each source, in the style of Fig. 6 of Rodrigues et al 2023

- `sourcename_flux_photons`: Comma-separated table with the best-fit photon fluxes predicted by the model. When imported the same way as shown above, this generates a data frame with the folowing columns:

    - `Energy`: Photon energy grid given in the observer's frame [eV]

    - `Total Flux`: Best-fit multi-wavelength fluxes resulting from the self-consistent interaction model. This corresponds to the blue curve in the respective figure in `sourcename_flux_total.pdf`   [Observer's frame, *accounting* for EBL attenuation, erg/cm2/s]
    
    - 11 individual components of the SED, labeled by the radiative process from which they originate (see Fig. 4 of Rodrigues et al 2023). The label of each column corresponds to the process responsible for the emission, as plotted in `sourcename_flux_components.pdf`. For example, the column `Compton Bethe Heitler Pairs` contains the spectrum of photons emitted through inverse Compton scattering by electron-positron pairs from Bethe-Heitler pair production (p gamma -> p e+ e-). To see the names of all the components, print `df.columns.tolist()` or see the first line of the csv file [Observer's frame, *not* accounting for EBL attenuation, erg/cm2/s]

    - The column total flux, as well as each of the 11 individual components, have a corresponding column `Min Total Flux`, `Min Compton Bethe Heitler Pairs`, etc, correpsonding to the minimum fluxes of the respective spectum within 1σ of the best fit (uncertainty band of each component in `sourcename_flux_components.pdf`). Likewise, there are also columns with `Max Total Flux`, `Max Compton Bethe Heitler Pairs`, etc, representing the maximum of the emission within 1σ of the best fit. Note that for the purely leptonic components (`Synchrotron Primary Electrons` and `Compton Primary Electrons`) the minimum and maximum fluxes are the same as the best fit, because we obtain the error bands by varying only the proton injection. [Observer's frame, erg/cm2/s]

    - `Disk`: Thermal emission from the accretion disk normalized to the total disk luminosity estimated by [Paliya et al 2017](https://iopscience.iop.org/article/10.3847/1538-4357/aa98e1) [Observer's frame, erg/cm2/s]

    - `Torus`: Infrared thermal emission from a dust torus that reprocesses a fraction of the disk emission and re-emits it in the infrared regime. This is normalized to the disk luminosity estimated by [Paliya et al 2017](https://iopscience.iop.org/article/10.3847/1538-4357/aa98e1) multiplied by the covering factor of the dust, fixed to 0.5 [Observer's frame, erg/cm2/s]


- `sourcename_flux_neutrinos`: A comma-separated table with the best-fit neutrino fluxes predicted by the model, as shown in orange in the respective figure `sourcename_flux_total.pdf`. When imported the same way as shown above, this generates a data frame with the folowing columns:

    - `Energy`: Neutrino energy grid given in the observer's frame [eV]
    - `Neutrino Flux Best Fit`: Best-fit all-flavor neutrino fluxes resulting from the self-consistent interaction model. This corresponds to the orange curve in `sourcename_flux_total.pdf`   [Observer's frame, *accounting* for EBL attenuation, erg/cm2/s]
    - `Neutrino Flux Min`: Minimum all-flavor neutrino fluxes resulting from the self-consistent interaction model, within 1σ of the best fit. This corresponds to the minimum fluxes of the orange band in `sourcename_flux_total.pdf` [Observer's frame, *accounting* for EBL attenuation, erg/cm2/s]
    - `Neutrino Flux Max`: Maximum all-flavor neutrino fluxes resulting from the self-consistent interaction model, within 1σ of the best fit. This corresponds to the maximum fluxes of the orange band in `sourcename_flux_total.pdf`. In the case where the best fit result yields no neutrino emission, this corresponds to the upper limit on the neutrino flux [Observer's frame, *accounting* for EBL attenuation, erg/cm2/s]

- `sourcename_mw_data`: A comma-separated table with the multi-wavelength data used to fit the model, as shown as black data points in the plots. These data are obtained from different catalogs, as described in Rodrigues et al 2023 and [Paliya et al 2017](https://iopscience.iop.org/article/10.3847/1538-4357/aa98e1). The gamma-ray data are *not* corrected for EBL attenuation -- the modeled fluxes were attenuated after each simulation before comparing to data. When imported the same way as shown above, this generates a data frame with the folowing columns:

    - `Energy`: Energy of the data points [Observer's frame, eV]
    - `Flux Value`: Observed flux [Observer's frame, erg/cm2/s]
    - `Flux Error`: Error on the observed flux [Observer's frame, erg/cm2/s]
    - `Is Upper Limit`: `0` if the data point is a measurement, `1` if it is an upper limit. 
    

## Cite as 

If you use the flux predictions or the best-fit parameter values from the leptohadronic model, you may cite the original paper by Rodrigues et al 2023.

All multi-wavelength data used to fit the model were adopted from public catalogs. If using those data, please cite the respective catalog (see [Paliya et al 2017](https://iopscience.iop.org/article/10.3847/1538-4357/aa98e1)  and references therein).

## References

[Abdo, A. A. 2010, Astrophys. J., 715, 429](https://iopscience.iop.org/article/10.1088/0004-637X/715/1/429)

[Acero, F. et al. 2015, Astrophys. J. Suppl., 218, 23](https://iopscience.iop.org/article/10.1088/0067-0049/218/2/23)

[Ackermann, M., Ajello, M., Allafort, A., et al. 2011, ApJ, 743, 171](https://iopscience.iop.org/article/10.1088/0004-637X/743/2/171)

[Healey, S. E., Romani, R. W., Cotter, G., et al. 2008, Astrophys. J. Suppl., 175, 97](https://inspirehep.net/literature/760558)

[Paliya, V. S., Marcotulli, L., Ajello, M., et al. 2017, Astrophys. J., 851, 33](https://iopscience.iop.org/article/10.3847/1538-4357/aa98e1)

Rodrigues, X., Paliya, V. S., Garrappa, S. et al. 2023, submitted to A&A
