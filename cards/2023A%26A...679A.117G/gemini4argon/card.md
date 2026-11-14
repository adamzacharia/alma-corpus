# MINDS. Abundant water and varying C/O across the disk of Sz 98 as seen by JWST/MIRI

`2023A&A...679A.117G` | Astronomy and Astrophysics 2023 | first author: Gasman, Danny | arXiv: 2307.09301 | DOI: 10.1051/0004-6361/202347005

Card schema 1.0 | model gemini-4-argon | depth light | type multi_facility_alma_minor

## Science

- Fields: protoplanetary_disks, astrochemistry
- Question: Explain the JWST MIRI/MRS observations of the Sz 98 inner disk, put it in context with other disks focusing on H2O ro-vibrational and pure rotational emission, and compare the chemical findings with outer disk ALMA observations.  
  > "We aim to explain the observations and put the disk of Sz 98 in context with other disks, with a focus on the emission through both its ro-vibrational and pure rotational emission." (abstract); "Furthermore, we compare our chemical findings with those obtained for the outer disk from Atacama Large Millimeter/submillimeter Array (ALMA) observations." (abstract)
- Target **Sz 98**: coordinates _not stated_; z/distance 156 pc  
  > "It has a luminosity $L_*=1.5$ $L_{\ensuremath{\odot}}$ and a mass $M_*=0.74$ $M_{\ensuremath{\odot}}$ (cite: ref:17AlMaNa) at a *Gaia* distance of approximately 156 pc (cite: ref:gaia1; ref:gaia2)" (Introduction); distance from (cite: ref:gaia1; ref:gaia2)  
  > "It has a luminosity $L_*=1.5$ $L_{\ensuremath{\odot}}$ and a mass $M_*=0.74$ $M_{\ensuremath{\odot}}$ (cite: ref:17AlMaNa) at a *Gaia* distance of approximately 156 pc (cite: ref:gaia1; ref:gaia2)" (Introduction)

## Data provenance

- ALMA projects: 2018.1.01458.S, 2018.0.01458.S
- bands: _not stated_
- frequencies and spectral setup: continuum spectral window centred at 232.984 GHz (1286.75 um)  
  > "The continuum image shown in Fig. 6 has been created using the continuum spectral window (centred at 232.984 GHz, 1286.75 \mu m) contained in the ALMA archival data set 2018.1.01458.S (PI: Hsi-Wei Jen)." (Sz 98 from ALMA data)
- continuum bandwidth: _not stated_
- arrays: _not stated_
- configurations: _not stated_
- baselines: _not stated_
- angular resolution: 0.079" x 0.063" (-27.135 deg)  
  > "The cleaned image has a resolving beam of 0.079"$\times$0.063" (-27.135$\degree$)." (Sz 98 from ALMA data)
- max recoverable scale: _not stated_
- sensitivity: 0.071 mJy beam^-1  
  > "The emission peaks at 2.167 mJy beam$^{-1}$ and the image has a root mean square of 0.071 mJy beam$^{-1}$." (Sz 98 from ALMA data)
- time on source: _not stated_
- observing dates: _not stated_
- pi or archival as stated: archival (PI: Hsi-Wei Jen)  
  > "The continuum image shown in Fig. 6 has been created using the continuum spectral window (centred at 232.984 GHz, 1286.75 \mu m) contained in the ALMA archival data set 2018.1.01458.S (PI: Hsi-Wei Jen)." (Sz 98 from ALMA data)
- Other facility **JWST MIRI/MRS**: Mid-infrared spectroscopy (4.9 to 28.1 um) of Sz 98 (PID: 1282) and reference A star HD 163466 (PID: 1050)  
  > "Sz 98 was observed with MIRI/MRS as part of the MIRI mid-INfrared Disk Survey (MINDS) JWST GTO Programme (PID: 1282, PI: T. Henning)." (Data acquisition and reduction); "The reference files exploit the repeatability of the fringes when the pointing is consistent between the science observation and the reference target, and are extracted from the A star HD 163466 (PID: 1050)." (Data acquisition and reduction)
- Other facility **Gaia**: Distance of approximately 156 pc to Sz 98  
  > "It has a luminosity $L_*=1.5$ $L_{\ensuremath{\odot}}$ and a mass $M_*=0.74$ $M_{\ensuremath{\odot}}$ (cite: ref:17AlMaNa) at a *Gaia* distance of approximately 156 pc (cite: ref:gaia1; ref:gaia2)" (Introduction)
- Other facility **Spitzer IRS**: Low resolution mid-infrared spectrum of Sz 98 and comparison sample line fluxes  
  > "Sz 98 was previously observed with *Spitzer*/IRS in 2008, but in its low resolution mode only." (Introduction); "We plot the same line fluxes from these *Spitzer*/IRS spectra compared to the accretion luminosity in Fig. 7, where in the top panel only the line flux is shown, and the bottom panel the /-ratio." (H2O and OH line fluxes)
- External data: Disk inclination (47.1 deg) and position angle (111.6 deg)  
  > "The inclination of the disk is 47.1$\degree$ with a position angle of 111.6$\degree$ (cite: ref:17TaTeNa)." (Sz 98 from ALMA data) [from Tazzari et al. 2017 (cite: ref:17TaTeNa)]
- External data: Outer disk volatile C/O ratio > 1 and depletion in volatile gaseous carbon and oxygen  
  > "(cite: ref:19MiFaVa) suggest that the outer disk is depleted in volatile gaseous carbon and oxygen, and find signs for a gaseous C/O ratio larger than unity based on bright and faint emission seen in Atacama Large Millimeter/submillimeter Array (ALMA) observations." (Introduction) [from Miotello et al. 2019 (cite: ref:19MiFaVa)]
- External data: Spitzer/IRS H2O and OH line fluxes of a comparison sample of disks  
  > "(cite: ref:17BaPoSa) examine the line fluxes of the 12.52 \mu m and the tentatively detected 12.6 \mu m and lines, respectively, of a sample of disks observed with *Spitzer*." (H2O and OH line fluxes) [from Banzatti et al. 2017 (cite: ref:17BaPoSa)]
- Simulation/model as data: Local thermodynamic equilibrium (LTE) slab models for molecular spectra  
  > "In order to model the molecular features in the spectrum, the continuum was subtracted and local thermodynamic equilibrium (LTE) slab models were fitted." (abstract)
- Simulation/model as data: Radiative transfer model fitting the spectral energy distribution, mm dust radial profiles and JWST continuum to estimate snowline locations  
  > "The location of the , , and snow lines are estimated from a radiative transfer model that fits the spectral energy distribution, mm dust radial profiles and the *JWST* continuum." (Sz 98 from ALMA data)

## Processing

### Calibration

- pipeline or manual: pipeline  
  > "The data set was calibrated using the provided pipeline scripts and the specified *Common Astronomy Software Applications* (*CASA*) (cite: ref:07McWaSc)." (Sz 98 from ALMA data)
- casa version: _not stated_
- pipeline version: _not stated_
- archive products used as is: _not stated_
- flux calibrator: _not stated_
- flux scale uncertainty: _not stated_
- self calibration: _not stated_

### Imaging

- task: TCLEAN  
  > "The continuum image was created using *CASA* version 6.5.2.26 and the TCLEAN-task, where we have used the Briggs weighting scheme and a robust parameter of +1.0." (Sz 98 from ALMA data)
- deconvolver: _not stated_
- weighting robust: Briggs, robust = +1.0  
  > "The continuum image was created using *CASA* version 6.5.2.26 and the TCLEAN-task, where we have used the Briggs weighting scheme and a robust parameter of +1.0." (Sz 98 from ALMA data)
- uv taper: _not stated_
- cell size: _not stated_
- image size: _not stated_
- masking: _not stated_
- multiscale scales: _not stated_
- continuum subtraction: _not stated_
- line free channels: _not stated_
- primary beam correction: _not stated_
- array combination: _not stated_
- smoothing: _not stated_
- final beam: 0.079" x 0.063" (-27.135 deg)  
  > "The cleaned image has a resolving beam of 0.079"$\times$0.063" (-27.135$\degree$)." (Sz 98 from ALMA data)
- final rms: 0.071 mJy beam^-1  
  > "The emission peaks at 2.167 mJy beam$^{-1}$ and the image has a root mean square of 0.071 mJy beam$^{-1}$." (Sz 98 from ALMA data)

### Inherited from earlier work

- JWST MIRI/MRS point-source defringing and flux calibration method  
  > "We followed the methods described in (cite: ref:23GaArSl) that are specific to point sources to defringe and flux calibrate the data." (Data acquisition and reduction) [from (cite: ref:23GaArSl)]
- JWST MIRI/MRS aperture correction factors  
  > "The aperture correction factors applied are the same as those in (cite: ref:23ArGlLa), and account for the fraction of the signal of the Point Spread Function (PSF) outside of the aperture, and inside the annulus." (Data acquisition and reduction) [from (cite: ref:23ArGlLa)]
- Mutual shielding from adjacent lines for densely packed Q-branches in LTE slab models  
  > "For molecules with densely packed lines, in other words the and $Q$-branches, we included mutual shielding from adjacent lines as described in (cite: ref:23TaBeDi)." (Slab models and fitting procedure) [from (cite: ref:23TaBeDi)]
- Iterative slab model fitting procedure and reduced chi^2 definition  
  > "Similarly to (cite: ref:23GrDiTa), we first identified relatively bright and isolated lines, used these to find the best fitting slab model, subtracted the model, and moved on to other molecular features." (Slab models and fitting procedure); "Similarly to (cite: ref:23GrDiTa), the reduced $\chi^2$ is then defined using:" (Slab models and fitting procedure) [from (cite: ref:23GrDiTa)]
- Disk inclination and position angle for ALMA continuum deprojection  
  > "The inclination of the disk is 47.1$\degree$ with a position angle of 111.6$\degree$ (cite: ref:17TaTeNa)." (Sz 98 from ALMA data) [from (cite: ref:17TaTeNa)]

### Not stated but needed to reproduce (our reading)

- Exact code/software and molecular spectroscopic databases (e.g., HITRAN) used to generate the LTE slab models
- Specific radiative transfer code and dust opacity parameters used to model the SED, mm radial profiles, and snowline locations in Appendix D
- Exact wavelength knot positions used for the cubic spline continuum subtraction in the MIRI/MRS spectrum
- Cell size, image size, and masking parameters used in CASA TCLEAN for the ALMA continuum image

## Analysis recipe

1. **Reduce JWST MIRI/MRS data and extract 1D spectrum**: Process exposure of all twelve bands with JWST pipeline, defringe and flux calibrate using on-sky reference A star HD 163466, sum signal in a 2.5xFWHM aperture with background estimated from an annulus, skip spec3 outlier detection, and mask spurious artefacts.  
  > "The data were processed using version 1.9.4 of the *JWST* pipeline (cite: ref:22BuEiDe). We followed the methods described in (cite: ref:23GaArSl) that are specific to point sources to defringe and flux calibrate the data." (Data acquisition and reduction); "In order to extract the spectrum, the signal in an aperture of 2.5$\times$FWHM centred on the source was summed." (Data acquisition and reduction)
   - software: JWST pipeline
   - parameter: Aperture = 2.5 x FWHM; background annulus = 5xFWHM to 7.5xFWHM (shortest wavelengths) to 3xFWHM to 3.75xFWHM (longest wavelengths)  
  > "In order to extract the spectrum, the signal in an aperture of 2.5$\times$FWHM centred on the source was summed. The background was estimated from an annulus that linearly grows between 5$\times$FWHM and 7.5$\times$FWHM in the shortest wavelengths, and 3$\times$FWHM to 3.75$\times$FWHM in the longest wavelengths." (Data acquisition and reduction)
   - fitting: _not stated_
   - validation: No rescaling of sub-bands was required to stitch the spectrum.  
  > "No rescaling of sub-bands was required to stitch the spectrum." (Data acquisition and reduction)
2. **Subtract continuum and fit LTE slab models to molecular emission across four spectral regions**: Subtract continuum by fitting a cubic spline through iteratively selected line-free sections; divide spectrum into 4 wavelength regions; convolve LTE slab models to constant MRS resolution per region and resample with spectres; iteratively fit column density N, excitation temperature T, and emitting radius R per molecule via reduced chi^2 minimization.  
  > "We subtracted the continuum from the spectrum by fitting a cubic spline through the line-free sections, in order to fit local thermodynamic equilibrium (LTE) slab models." (Slab models and fitting procedure); "Subsequently, three parameters were varied in order to fit the features in the observation: the column density $N$, the excitation temperature $T$, and the emitting area $\pi R^2$." (Slab models and fitting procedure); "The slab models were convolved to a constant resolution per region in the same order as that of the MRS in the relevant bands (ranging from a resolving power $\lambda / \Delta \lambda \approx 3500$ at shorter wavelengths to $\lambda / \Delta \lambda \approx 1500$ at the longer wavelengths, specific values given in Table 6 (cite: ref:23JoAlSl)), and resampled with `spectres` (cite: ref:17Ca) to the same wavelength grid." (Slab models and fitting procedure)
   - software: spectres
   - parameter: Spectral regions: 5-6.5 um (R~3500), 13.6-16.3 um (R~2500), 17-23 um (R~1500), 23 um onwards (R~1500)  
  > "By dividing the spectrum into the 5-6.5 \mu m region, the $\sim$13.6-16.3 \mu m region, the $\sim$17-23 \mu m region, and 23 \mu m and onwards, regions of similar excitation conditions were addressed separately." (Slab models and fitting procedure)
   - parameter: Grid spacing: Delta T = 25 K, Delta log10(N) = 0.16 cm^-2, Delta log10(R) = 0.02 au  
  > "The spacing of the grid is consistent between molecules ($\Delta T=25$ K, $\Delta \log_{10}{(N)}=0.16$ cm$^{-2}$, and $\Delta \log_{10}{(R)}=0.02$ au), but the range was varied depending on how hot or cold the excitation is expected to be." (Slab models and fitting procedure)
   - assumption: LTE excitation; Gaussian line profiles with broadening Delta V = 4.7 km s^-1 (sigma = 2 km s^-1); mutual line shielding for CO2 and HCN Q-branches; ISM H2(16)O/H2(18)O ratio of 550  
  > "The line profiles were assumed to be Gaussian, with a broadening of $\Delta V=4.7$ km s$^{-1}$ ($\sigma = 2$ km s$^{-1}$), similarly to (cite: ref:11SaPoBl)." (Slab models and fitting procedure); "Assuming the integrated flux of the H$_\text{2}^{\text{18}}$O feature is in this upper limit on the line flux, the maximum column density of is 3.5$\times$10$^{19}$ cm$^{-2}$ when assuming the ISM H$_\text{2}^{\text{16}}$O/H$_\text{2}^{\text{18}}$O ratio of 550." (H2O)
   - fitting: Grid search minimizing reduced chi^2 with 1, 2, and 3 sigma confidence intervals defined as chi^2_min + 2.3, + 6.2, and + 11.8  
  > "The confidence intervals are defined as $\chi^2_{min} + 2.3$, $\chi^2_{min} + 6.2$, and $\chi^2_{min} + 11.8$; for $1\sigma$, $2\sigma$, and $3\sigma$, respectively (cite: ref:76Av; ref:92PrTeVe)." (Slab models and fitting procedure)
   - validation: Assess correctness of chi^2 fit results for H2O column density by comparing flux ratios of line pairs with the same upper energy levels but different Einstein A_ul coefficients, and by checking the H2(18)O non-detection upper limit.  
  > "In order to assess the correctness of the $\chi^2$ fit results, we compare the fluxes of pairs of lines with the same upper energy levels, but different Einstein $A_{ul}$ coefficients." (H2O)
3. **Image ALMA continuum, extract radial profile to locate rings and gaps, and model snowline locations**: Calibrate ALMA archival data set 2018.1.01458.S with pipeline scripts, image continuum at 232.984 GHz with CASA TCLEAN, extract deprojected azimuthally averaged radial profile to locate rings and gaps, and run a radiative transfer model fitting SED, mm dust radial profiles, and JWST continuum to find snowlines.  
  > "The continuum image was created using *CASA* version 6.5.2.26 and the TCLEAN-task, where we have used the Briggs weighting scheme and a robust parameter of +1.0." (Sz 98 from ALMA data); "We have estimated the locations of the rings and gaps (displayed in Fig. 6) using a deprojected, azimuthally averaged radial profile." (Sz 98 from ALMA data); "The location of the , , and snow lines are estimated from a radiative transfer model that fits the spectral energy distribution, mm dust radial profiles and the *JWST* continuum." (Sz 98 from ALMA data)
   - software: CASA, TCLEAN
   - parameter: Briggs robust = +1.0; clean threshold ~ 1x RMS of dirty image; radial profile bin size = half the width of beam minor axis  
  > "We cleaned down to a threshold of $\sim1\times$ the RMS in the initial, dirty image." (Sz 98 from ALMA data); "The radial profile was created using bin sizes of half the width of the beam’s minor axis." (Sz 98 from ALMA data)
   - assumption: Disk inclination = 47.1 deg, position angle = 111.6 deg; freeze-out temperatures of 150 K (H2O), 72 K (CO2), and 20 K (CO)  
  > "The inclination of the disk is 47.1$\degree$ with a position angle of 111.6$\degree$ (cite: ref:17TaTeNa)." (Sz 98 from ALMA data); "Assuming that these molecules freeze-out at temperatures of, respectively, 150 K, 72 K, and 20 K (cite: ref:04CoAnCh), the model suggests that the H$_2$O snowline is located between approximately 1.05 and 1.11 au, the CO$_2$ snowline between approximately 2.17 and 2.29 au, and the CO snowline between approximately 20.64 and 21.40 au." (Sz 98 from ALMA data)
   - fitting: _not stated_
   - validation: _not stated_

## Software

- **JWST pipeline** 1.9.4: Processing JWST MIRI/MRS data  
  > "The data were processed using version 1.9.4 of the *JWST* pipeline (cite: ref:22BuEiDe)." (Data acquisition and reduction)
- **spectres** : Resampling convolved slab models to the observed wavelength grid  
  > "The slab models were convolved to a constant resolution per region in the same order as that of the MRS in the relevant bands (ranging from a resolving power $\lambda / \Delta \lambda \approx 3500$ at shorter wavelengths to $\lambda / \Delta \lambda \approx 1500$ at the longer wavelengths, specific values given in Table 6 (cite: ref:23JoAlSl)), and resampled with `spectres` (cite: ref:17Ca) to the same wavelength grid." (Slab models and fitting procedure)
- **CASA** 6.5.2.26: Calibrating ALMA archival data and creating the continuum image  
  > "The data set was calibrated using the provided pipeline scripts and the specified *Common Astronomy Software Applications* (*CASA*) (cite: ref:07McWaSc). The continuum image was created using *CASA* version 6.5.2.26 and the TCLEAN-task, where we have used the Briggs weighting scheme and a robust parameter of +1.0." (Sz 98 from ALMA data)
- **TCLEAN** : Creating the ALMA continuum image  
  > "The continuum image was created using *CASA* version 6.5.2.26 and the TCLEAN-task, where we have used the Briggs weighting scheme and a robust parameter of +1.0." (Sz 98 from ALMA data)

## Numeric results

| quantity | value | uncertainty | units | step | quote |
|---|---|---|---|---|---|
| H2O column density N (5-6.5 um, Region 1) | 3.7e18 | +3.1/-1.5 (log-space) | cm^-2 | 2 | 3.7$\times$10$^{18}$ $_{-1.5}^{+3.1}$ |
| H2O excitation temperature T (5-6.5 um, Region 1) | 950 | +513/-620 | K | 2 | 950 $_{-620}^{+513}$ |
| H2O emitting radius R (5-6.5 um, Region 1) | 0.07 | +0.46/-0.03 | au | 2 | 0.07 $_{-0.03}^{+0.46}$ |
| H2O column density N (13.6-16.3 um, Region 2) | 7.9e18 | +0.8/-0.5 (log-space) | cm^-2 | 2 | 7.9$\times$10$^{18}$ $_{-0.5}^{+0.8}$ |
| H2O excitation temperature T (13.6-16.3 um, Region 2) | 650 | +88/-91 | K | 2 | 650 $_{-91}^{+88}$ |
| H2O emitting radius R (13.6-16.3 um, Region 2) | 0.28 | +0.07/-0.04 | au | 2 | 0.28 $_{-0.04}^{+0.07}$ |
| H2O column density N (17-23 um, Region 3) | 7.5e19 | +1.1/-4.2 (log-space) | cm^-2 | 2 | 7.5$\times$10$^{19}$ $_{-4.2}^{+1.1}$ |
| H2O excitation temperature T (17-23 um, Region 3) | 300 | +182/-41 | K | 2 | 300 $_{-41}^{+182}$ |
| H2O emitting radius R (17-23 um, Region 3) | 1.00 | +8.33/-0.39 | au | 2 | 1.00 $_{-0.39}^{+8.33}$ |
| H2O column density N (23 um onwards, Region 4) | 1.7e19 | +0.1/-2.0 (log-space) | cm^-2 | 2 | 1.7$\times$10$^{19}$ $_{-2.0}^{+0.1}$ |
| H2O excitation temperature T (23 um onwards, Region 4) | 250 | +147/-44 | K | 2 | 250 $_{-44}^{+147}$ |
| H2O emitting radius R (23 um onwards, Region 4) | 1.42 | +2.9/-0.66 | au | 2 | 1.42 $_{-0.66}^{+2.9}$ |
| CO best-fit column density, temperature, and radius (Region 1) | 1.4e15 cm^-2, 1675 K, 1.00 au | not stated | cm^-2, K, au | 2 | The best-fit parameters for the emission in the disk are 1675 K, with a radius of 1.00 au, and a column density of 1.4$\times$10$^{15}$ cm$^{-2}$. |
| CO2 best-fit column density, temperature, and radius (Region 2, including hot band) | 2.4e19 cm^-2, 125 K, 1.63 au | not stated | cm^-2, K, au | 2 | The best-fit temperature when including the hot band around 13.8 \mu m is relatively cold, with 125 K from an emitting radius of 1.63 au, and a column density of $\sim$2.4$\times 10^{19}$ cm$^{-2}$. |
| HCN best-fit column density, temperature, and radius (Region 2) | 4.3e16 cm^-2, 1075 K, 0.76 au | not stated | cm^-2, K, au | 2 | While can be fit with both an optically thin and optically thick solution, we find a best fit for a temperature of 1075 K, with a radius of 0.76 au, and a column density of 4.3$\times$10$^{16}$ cm$^{-2}$. |
| Maximum H2O column density from H2(18)O non-detection | 3.5e19 | not stated | cm^-2 | 2 | Assuming the integrated flux of the H$_\text{2}^{\text{18}}$O feature is in this upper limit on the line flux, the maximum column density of is 3.5$\times$10$^{19}$ cm$^{-2}$ when assuming the ISM H$_\text{2}^{\text{16}}$O/H$_\text{2}^{\text{18}}$O ratio of 550. |
| C2H2 line flux upper limit (13.65-13.72 um, normalised to 140 pc) | 0.3e-14 | not stated | erg s^-1 cm^-2 | 2 | After subtracting the best-fit slab models, we find an upper limit for in the 13.65-13.72 \mu m region of $\sim$0.3$\times 10^{-14}$ erg s$^{-1}$ cm$^{-2}$ normalised to a distance of 140 pc. |
| HCN (13.9 um) to H2O (17.23 um) line flux ratio | 1.7 | not stated | dimensionless | 2 | After subtracting the slab model fits presented in Fig. 2 to get a ‘clean’ feature, the flux ratio is $\sim$1.7. |
| ALMA 232.984 GHz continuum peak emission | 2.167 | 0.071 | mJy beam^-1 | 3 | The emission peaks at 2.167 mJy beam$^{-1}$ and the image has a root mean square of 0.071 mJy beam$^{-1}$. |
| ALMA millimeter dust ring locations | 27, 103 | not stated | au | 3 | As displayed in Fig. 6, we infer the millimetre emission to consist of an inner compact core, surrounded by two rings at approximately 27 and 103 au, respectively. |
| ALMA millimeter dust gap locations | 16, 88 | not stated | au | 3 | The gaps are expected to be located at approximately 16 and 88 au. |
| Estimated snowline locations (H2O, CO2, CO) | 1.05-1.11 (H2O), 2.17-2.29 (CO2), 20.64-21.40 (CO) | not stated | au | 3 | Assuming that these molecules freeze-out at temperatures of, respectively, 150 K, 72 K, and 20 K (cite: ref:04CoAnCh), the model suggests that the H$_2$O snowline is located between approximately 1.05 and 1.11 au, the CO$_2$ snowline between approximately 2.17 and 2.29 au, and the CO snowline between approximately 20.64 and 21.40 au. |

## Qualitative findings

- CO, H2O, OH, CO2, HCN, and HI (6-5) are detected in the inner disk of Sz 98, while H2(18)O, 13CO2, C2H2, C2H4, CH4, NH3, [NeII], and H2 are not detected.  
  > "On top of the continuum, we detect around 5 \mu m, , , from $\sim$13 \mu m and onwards; and, most strikingly, we see features from 5 \mu m up to 27 \mu m." (Results); "We report the detection of a hydrogen recombination line. The strongest hydrogen recombination line, HI (6-5) at" (Hydrogen); "As mentioned above, while is easily visible in the spectrum, its isotopologue H$_\text{2}^{\text{18}}$O is not." (Non-detections)
- H2O emission traces a radial gradient across the inner disk surface, with excitation temperature decreasing and emitting radius increasing toward longer wavelengths.  
  > "The best-fit temperature and emitting radius change as we move to longer wavelengths. The temperatures slowly decrease from 950 to 250 K, indicating that we are gradually probing colder and/or less excited gas." (H2O)
- H2O in the inner disk of Sz 98 is not significantly photodissociated due to self-shielding and/or UV shielding by small dust grains, and OH lines are not primarily excited by prompt emission.  
  > "It is likely that is not significantly photodissociated, either due to self-shielding against the stellar irradiation, or UV shielding from small dust particles." (abstract); "We therefore conclude that lines are not primarily excited by photodissociation." (OH prompt emission)
- The inner disk of Sz 98 has a sub-solar volatile C/O ratio (< 0.5, potentially <= 0.14), contrasting with the outer disk gas C/O > 1 inferred from ALMA.  
  > "In general, the inferred composition points to a sub-solar C/O ratio ($<$0.5) in the inner disk, in contrast with the larger than unity C/O ratio in the gas in the outer disk found with ALMA." (abstract); "The lack of other organic molecules, most notably , in the spectrum of the inner disk of Sz 98 is indicative of a low volatile elemental C/O ratio, potentially 0.14 or lower." (Conclusions)

## Claim tuples

- H: Water emission across the wide MIRI/MRS wavelength range (5 to 27 um) probes radially distinct regions of the inner disk from warmer inner parts to colder outer parts. | E: Divided the continuum-subtracted MIRI/MRS spectrum into four wavelength regions (5-6.5, 13.6-16.3, 17-23, and >23 um) and fitted LTE slab models individually per region. | R: Best-fit H2O excitation temperatures decrease from 950 K to 250 K while equivalent emitting radii increase from 0.07 au to 1.42 au from Region 1 to Region 4; a single slab cannot fit the entire range. | F: H2O emission traces a large radial surface region of the inner disk with gradually changing excitation temperatures and emitting radii. | **supported**
- H: H2O in the inner disk of Sz 98 is shielded against UV photodissociation. | E: Measured H2O column densities and OH, CO2, and H2O line fluxes, and searched for highly excited OH prompt emission lines shortwards of 14 um (at ~10 and 12.65 um) and quadruplet asymmetries. | R: H2O column densities exceed 10^18 cm^-2 (well above the ~2e17 cm^-2 self-shielding threshold), CO2 and OH emission are weak relative to H2O, and expected brighter OH prompt emission lines at 12.65 um and quadruplet asymmetries are absent. | F: H2O is not significantly photodissociated due to self-shielding and/or UV attenuation by small dust grains, and OH is not primarily excited by prompt emission. | **supported**
- H: The inner disk of Sz 98 has a low volatile elemental C/O ratio despite its large millimeter dust disk with substructures and a C/O > 1 in the outer disk. | E: Searched for organic molecules (including C2H2), measured the HCN (13.9 um) to H2O (17.23 um) flux ratio, and compared snowline locations from a radiative transfer model with ALMA continuum dust ring and gap positions. | R: No organic molecules other than CO, CO2, and HCN are detected (C2H2 upper limit ~0.3e-14 erg s^-1 cm^-2), the HCN/H2O flux ratio is ~1.7, the H2O snowline is at ~1.1 au, and the CO snowline (~20 au) lies inside the first dust ring (~27 au) beyond a gap at ~16 au. | F: The inner disk has a sub-solar C/O ratio (< 0.5, potentially <= 0.14), likely because H2O-ice pebbles drifted inward to the central core before gap formation or through leaky traps while CO-ice remained trapped outside the 16 au gap. | **supported**

## Reasoning

- Why this data: JWST MIRI/MRS provides higher sensitivity and spectral resolving power (R ~ 1500-3500 from 4.9 to 28.1 um) than previous low-resolution Spitzer/IRS observations, enabling detection of H2O across all bands to probe inner disk planet-forming regions.  
  > "Sz 98 was previously observed with *Spitzer*/IRS in 2008, but in its low resolution mode only. The higher sensitivity and spectral resolving resolution of the MRS ranging from a resolving power $\lambda / \Delta \lambda \approx 3500$ at shorter wavelengths to $\lambda / \Delta \lambda \approx 1500$ at the longer wavelengths (cite: ref:23JoAlSl) now allows us to detect in all of its bands." (Introduction)
- Why this method: On-sky reference star defringing was chosen over the standard pipeline residual_fringe step because the latter can alter molecular line shapes; LTE slab models were fitted separately across four wavelength regions because spectral resolution and disk excitation conditions vary with wavelength.  
  > "This method is adopted mainly for the advantages related to defringing, since the standard pipeline fringe flats require the additional `residual_fringe` step to defringe the spectrum. As shown by (cite: ref:23GaArSl), the latter step may change the shape of molecular features, which would affect the derived excitation properties." (Data acquisition and reduction); "Additionally, the regions of the disk probed by the different wavelengths and their excitation conditions are not expected to be constant throughout, hence we treated the shorter wavelengths separately from the longer wavelengths (cite: ref:23BaPoPe)." (Slab models and fitting procedure)
- Alternative: Standard JWST pipeline fringe flats with the residual_fringe step and spec3 outlier detection were rejected because residual_fringe can change molecular feature shapes and spec3 outlier detection produces spurious results due to PSF undersampling.  
  > "This method is adopted mainly for the advantages related to defringing, since the standard pipeline fringe flats require the additional `residual_fringe` step to defringe the spectrum. As shown by (cite: ref:23GaArSl), the latter step may change the shape of molecular features, which would affect the derived excitation properties." (Data acquisition and reduction); "Additionally, the outlier detection step of `spec3` was skipped, since this has spurious results for the data taken with the MRS due to undersampling of the PSF." (Data acquisition and reduction)
- Alternative: Fitting a single LTE slab model across the entire MIRI/MRS wavelength range or using complex thermo-chemical models was rejected in favor of per-region LTE slab fits.  
  > "This indicates that one slab cannot be used to fit the entire MIRI/MRS range, and future work must accommodate for a temperature and emitting area gradient in the fitting procedure." (H2O); "While more detailed thermo-chemical models could result in a better representation of the spectrum, the increased complexity introduces more uncertainties in the fits, and this is left for future work, along with fits of temperature gradients." (H2O)
- How they decided it was enough: _not stated_
- Limitation (authors): Significant pointing offset in MIRI/MRS channel 2 (~7.5-11.7 um) and noisy artefacts at >24 um from low signal in the reference A star HD 163466 increase continuum and line flux uncertainties in those regions.  
  > "In the Sz 98 case a more significant pointing offset is seen in channel 2 ($\sim$7.5-11.7 \mu m), which is dominated by the silicate feature, but we do not analyse this region in detail." (Data acquisition and reduction); "Especially in the region of 24 \mu m and beyond, the data become noisy and filled with artefacts caused by the low signal in the reference A star HD 163466." (Slab models and fitting procedure)
- Limitation (authors): LTE assumption is less accurate for high-energy lines around 6.5 um and for OH.  
  > "For the lines longwards of $\sim$10 \mu m, LTE is a good first estimate, though this assumption is less accurate for the lines around 6.5 \mu m (cite: ref:09MePoBl; ref:22BoBeCaa)." (Slab models and fitting procedure)
- Limitation (authors): Parameter degeneracies between column density, temperature, and emitting radius result in poorly constrained fits for CO, OH, CO2, and HCN.  
  > "**Note.** The fits are poorly constrained, and the best-fit parameters are likely not representative." (Table 1); "However, we note a degeneracy between the three parameters, causing the confidence intervals to be relatively wide." (CO); "The constraints on the fit are poor due to the degeneracy between the column density and the emitting radius for low column density, and the degeneracy between the column density and temperature for high column density." (HCN)
- Limitation (authors): Diagnostic H2O line pairs used to test optical depth are part of line clusters and affected by line blending.  
  > "However, we note that these lines are part of a cluster of lines, and the ratios are likely affected by line blending." (H2O)
- Caveat (inferred, ours): The radiative transfer model in Appendix D used to derive the H2O, CO2, and CO snowline locations is not described in sufficient detail (code, dust properties, vertical structure) to evaluate its systematic uncertainties.
- Caveat (inferred, ours): Inferring the inner disk elemental C/O ratio from the HCN/H2O flux ratio relies heavily on external fiducial thermochemical models (Anderson et al. 2021) that were not specifically tailored to Sz 98.

## Reproducibility

- Data public (paper): JWST data obtained from MAST (programs #1282 and #1050) and ALMA archival data 2018.1.01458.S used.  
  > "The data were obtained from the Mikulski Archive for Space Telescopes at the Space Telescope Science Institute, which is operated by the Association of Universities for Research in Astronomy, Inc., under NASA contract NAS 5-03127 for JWST. These observations are associated with program #1282 and #1050." (Acknowledgements); "The continuum image shown in Fig. 6 has been created using the continuum spectral window (centred at 232.984 GHz, 1286.75 \mu m) contained in the ALMA archival data set 2018.1.01458.S (PI: Hsi-Wei Jen)." (Sz 98 from ALMA data)
- Products in archive: _not stated_
- Missing: Exact spline knot wavelengths used for continuum subtraction of the MIRI/MRS spectrum
- Missing: Specific LTE slab modeling code and molecular line list database version
- Missing: Details and parameters of the radiative transfer code used in Appendix D to compute snowline radii
- Missing: Exact wavelength windows used to compute reduced chi^2 for each molecule within the 4 broader spectral regions
- Data volume (inferred): ~10-50 GB (one ALMA archival execution block 2018.1.01458.S and two JWST MIRI/MRS pointings)
- Score (inferred): 65/5, Both JWST and ALMA datasets are publicly identified in archives, CASA/JWST pipeline versions and masked wavelength intervals are explicitly listed, and slab model grid spacings are given, but continuum spline knots, exact fitting windows, slab code identity, and radiative transfer model details are omitted.
- Rediscovery candidate: yes, Public archival JWST and ALMA data with quantitative, well-defined numeric results (ALMA continuum peak, RMS, ring/gap radii, and MIRI/MRS LTE slab parameters per region).

## Links

- Method: Gasman et al. 2023 (cite: ref:23GaArSl) (Point-source defringing and spectrophotometric calibration method for JWST MIRI/MRS using HD 163466)
- Method: Argyriou et al. 2023 (cite: ref:23ArGlLa) (Aperture correction factors for JWST MIRI/MRS spectrum extraction)
- Method: Tabone et al. 2023 (cite: ref:23TaBeDi) (Mutual line shielding treatment for densely packed Q-branches in LTE slab models)
- Method: Grant et al. 2023 (cite: ref:23GrDiTa) (Iterative LTE slab model fitting procedure and reduced chi^2 definition)
- Companion: Grant et al. 2023 (cite: ref:23GrDiTa) (MINDS survey companion paper on GW Lup used as primary comparison and methodology reference)
- Companion: Tabone et al. 2023 (cite: ref:23TaBeDi) (MINDS survey companion paper)
- Companion: Kospal et al. 2023 (cite: ref:23KoAbDi) (MINDS survey companion paper on EX Lup compared in text)
- Companion: Perotti et al. 2023 (cite: ref:23PeChHe) (MINDS survey companion paper)
- Related: MIRI mid-INfrared Disk Survey (MINDS) JWST GTO Programme (PID: 1282)

## Checks

```json
{
 "quotes": 112,
 "quotes_ok": 112,
 "quote_pass_rate": 1.0,
 "quotes_too_long": 11,
 "unsupported_facts": 0,
 "project_codes": 2,
 "codes_not_in_text": [],
 "codes_not_in_obscore": [
  "2018.0.01458.S"
 ],
 "obscore_codes_not_in_card": [],
 "codes_printed_but_missing": [],
 "numeric_results": 22,
 "numeric_problems": 0,
 "fill": {
  "facts": 85,
  "stated": 54,
  "rate": 0.635
 },
 "evidence_ok": true
}
```
