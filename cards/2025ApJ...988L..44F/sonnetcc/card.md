# A Deep Search for Ethylene Glycol and Glycolonitrile in the V883 Ori Protoplanetary Disk

`2025ApJ...988L..44F` | The Astrophysical Journal Letters 2025 | first author: Fadul, Abubakar M. A. | arXiv: 2507.14905 | DOI: 10.3847/2041-8213/adec6e

Card schema 1.0 | model claude-sonnet-5-5-claude-code | depth full | type observational_alma_primary

## Science

- Fields: astrochemistry, protoplanetary_disks
- Question: Are ethylene glycol and glycolonitrile, molecular precursors of nucleic acids, present in the V883 Ori protoplanetary disk, and how do their abundances relative to methanol compare with hot cores and comets?  
  > "How much of this complexity endures to the planet formation stage, and thus is already present when planets form, remains largely unknown." (abstract); "Comparing the abundance of EG and GN relative to methanol in V883 Ori with other objects, V883 Ori falls between hot cores and comets in terms of increasing complexity." (abstract)
- Target **V883 Ori**: coordinates _not stated_; z/distance d = 400 pc (Analysis); 388 pc (Appendix D Band 6 check)  
  > "$d=400$ pc is the distance to the star" (3 Analysis); "a distance of 388 pc, and a stellar mass of 1.29 $\mathrm{M\odot}$ ((cite: Cieza2016Natur; Lee_2019; Tobin23; Yamato2024AJ))" (Appendix D); distance from not stated for 400 pc; 388 pc taken with other parameters from Cieza2016Natur; Lee_2019; Tobin23; Yamato2024AJ  
  > "$d=400$ pc is the distance to the star" (3 Analysis); "a distance of 388 pc, and a stellar mass of 1.29 $\mathrm{M\odot}$ ((cite: Cieza2016Natur; Lee_2019; Tobin23; Yamato2024AJ))" (Appendix D)

## Data provenance

- ALMA projects: 2021.1.00452.S
- bands: Band 7, spectral scanning mode  
  > "Observations were done in Band 7 in spectral scanning mode, covering the frequency range 348-366 GHz." (2 Observations and Data Reduction)
- frequencies and spectral setup: 348-366 GHz; spectral resolution 488.281 kHz (about 0.42 km/s)  
  > "covering the frequency range 348-366 GHz. The spectral resolution was set to 488.281 kHz" (2 Observations and Data Reduction)
- continuum bandwidth: _not stated_
- arrays: _not stated_
- configurations: _not stated_
- baselines: _not stated_
- angular resolution: 0.48'' x 0.29'' beam, PA -68 deg (final continuum-subtracted line cube)  
  > "The final continuum subtracted line cube has a $0.48\ensuremath{''} \times 0.29\ensuremath{''}$ beam with a position angle of $-68^{\circ}$." (2 Observations and Data Reduction)
- max recoverable scale: _not stated_
- sensitivity: RMS 5.97 mJy/beam  
  > "The RMS noise level is 5.97 mJy beam$^{-1}$." (2 Observations and Data Reduction)
- time on source: _not stated_
- observing dates: six execution blocks, 30 December 2021 to 19 September 2022  
  > "over six execution blocks between 30 December, 2021 and 19 September, 2022" (2 Observations and Data Reduction)
- pi or archival as stated: _not stated_
- Line: Ethylene glycol (g'Gg-(CH2OH)2) 15 transitions tentatively identified (18 listed in Table); v=0 and v=1, Eu about 114-708 K (Appendix A) (multiple transitions, see Appendix A)
- Line: Glycolonitrile (HOCH2CN) 6 transitions tentatively identified (9 listed in Table); Eu about 205-545 K (Appendix A) (multiple transitions, see Appendix A)
- Line: Glycolaldehyde (CH2(OH)CHO) searched, only upper limit; two matching transitions overlap H2CO (not stated)
- Other facility **ALMA Band 6 data (Lee2025ApJ)**: Archive Band 6 spectrum used to check the model prediction for EG  
  > "plotted on top of ALMA Band 6 data published by (cite: Lee2025ApJ). The data have been downloaded from the ALMA archive" (Appendix D)
- Other facility **CDMS via Splatalogue**: Spectroscopic parameters of EG, GN, GA and other species  
  > "were taken from the Cologne Database for Molecular Spectroscopy (CDMS; (cite: CDMS2001A&A; CDMSEndres_2016)) using “Splatalogue[^1]” online database." (3 Analysis)
- External data: Emitting area (R = 0.3'') and line FWHM (2 km/s) from earlier higher-resolution COM observations of V883 Ori  
  > "The emitting area and FWHM are both based on previous higher spatial resolution observations of COMs in V883 Ori (cite: Lee_2019)." (3 Analysis) [from (cite: Lee_2019)]
- External data: CH3OH column density, from 13CH3OH times canonical 12C/13C of 60  
  > "The $\mathrm{CH_3OH}$ column density is taken from (cite: Fadul25)." (4.5 Uncertainty in the measured abundances); "Instead we use the $\mathrm{^{13}CH_3OH}$ column density multiplied by the canonical ISM $\mathrm{^{12}C/^{13}C}$ ratio of 60 (cite: Langer93ApJ)." (4.5 Uncertainty in the measured abundances) [from (cite: Fadul25); (cite: Langer93ApJ)]
- External data: Column densities of other molecules identified in V883 Ori and subtracted before fitting EG and GN  
  > "We subtracted all the molecules (shown in blue in Figure [1](#results)) identified by (cite: Fadul25) from the data before fitting EG and then GN." (3 Analysis) [from (cite: Fadul25)]
- External data: Disk geometry and stellar mass for Band 6 spectrum extraction: PA 32 deg, inclination 38.3 deg, 388 pc, 1.29 Msun  
  > "a position angle of $32^\circ$, an inclination angle of $38.3^\circ$, a distance of 388 pc, and a stellar mass of 1.29 $\mathrm{M\odot}$ ((cite: Cieza2016Natur; Lee_2019; Tobin23; Yamato2024AJ))" (Appendix D) [from (cite: Cieza2016Natur; Lee_2019; Tobin23; Yamato2024AJ)]
- External data: EG and GN abundances relative to methanol in other objects (hot cores, protostellar envelopes, comets) used for the comparison; individual sources and values not itemized in the text  
  > "Comparing the abundance of EG and GN relative to methanol in V883 Ori with other objects, V883 Ori falls between hot cores and comets in terms of increasing complexity." (abstract) [from not stated in text (see Figure 4)]

## Processing

### Calibration

- pipeline or manual: standard ALMA calibration pipeline  
  > "Data reduction was carried out using the standard ALMA calibration pipeline in the Common Astronomy Software Applications (CASA) package, version 6.4.1.12." (2 Observations and Data Reduction)
- casa version: CASA 6.4.1.12  
  > "Common Astronomy Software Applications (CASA) package, version 6.4.1.12." (2 Observations and Data Reduction)
- pipeline version: _not stated_
- archive products used as is: _not stated_
- flux calibrator: _not stated_
- flux scale uncertainty: _not stated_
- self calibration: _not stated_

### Imaging

- task: tclean  
  > "Imaging was carried out using *tclean* with Briggs weighting and a robust factor of 0.5." (2 Observations and Data Reduction)
- deconvolver: _not stated_
- weighting robust: Briggs, robust = 0.5  
  > "Briggs weighting and a robust factor of 0.5" (2 Observations and Data Reduction)
- uv taper: _not stated_
- cell size: _not stated_
- image size: _not stated_
- masking: _not stated_
- multiscale scales: _not stated_
- continuum subtraction: final cube is continuum subtracted (method not stated)  
  > "The final continuum subtracted line cube has a" (2 Observations and Data Reduction)
- line free channels: _not stated_
- primary beam correction: _not stated_
- array combination: _not stated_
- smoothing: _not stated_
- final beam: 0.48'' x 0.29'', PA -68 deg  
  > "$0.48\ensuremath{''} \times 0.29\ensuremath{''}$ beam with a position angle of $-68^{\circ}$" (2 Observations and Data Reduction)
- final rms: 5.97 mJy/beam  
  > "The RMS noise level is 5.97 mJy beam$^{-1}$." (2 Observations and Data Reduction)

### Inherited from earlier work

- Observation and calibration details  
  > "For additional details on the observations and calibration see (cite: Fadul25)." (2 Observations and Data Reduction) [from (cite: Fadul25)]
- Spectral line fitting tool used for identification and analysis of lines  
  > "The identification and analysis of these lines was carried out with the spectral line fitting tool developed by (cite: Fadul25)." (3 Analysis) [from (cite: Fadul25)]
- Fitting and identification processes and the LTE model are described in the earlier paper  
  > "The fitting and identification processes, as well as the model has been used is described in detail by (cite: Fadul25)." (3 Analysis) [from (cite: Fadul25)]
- Emitting area and line FWHM adopted from earlier higher-resolution observations  
  > "The emitting area and FWHM are both based on previous higher spatial resolution observations of COMs in V883 Ori (cite: Lee_2019)." (3 Analysis) [from (cite: Lee_2019)]
- Methanol column density used for abundance ratios  
  > "The $\mathrm{CH_3OH}$ column density is taken from (cite: Fadul25)." (4.5 Uncertainty in the measured abundances) [from (cite: Fadul25)]
- GA fit and expected GA transitions shown in the earlier paper  
  > "but were unable to secure a robust detection, see Appendix D in (cite: Fadul25)." (3 Analysis) [from (cite: Fadul25) Appendix D]
- Uncertainties from dust opacity and constant source size are discussed in the earlier paper  
  > "All of these factors have been discussed in detail in (cite: Fadul25)." (4.5 Uncertainty in the measured abundances) [from (cite: Fadul25)]
- Spectrum extraction with Gofish in Band 6 check  
  > "(for more details see (cite: Fadul25) Section 3)" (Appendix D) [from (cite: Fadul25) Section 3]

### Not stated but needed to reproduce (our reading)

- Array configurations, baselines, time on source, and calibrators for the six execution blocks
- Self-calibration, if any, and how the six execution blocks were combined
- Continuum subtraction method and line-free channels
- Image size, cell size, deconvolver, masking and cleaning threshold for the cubes
- Spectrum extraction aperture/region used for the V883 Ori spectrum (given only in Fadul25 and for Band 6)
- Priors, parameter bounds (the highest allowed temperature for EG), initial walker positions and likelihood noise treatment of the emcee fit
- Column densities and temperatures of the other molecules from Fadul25 that are subtracted before fitting EG and GN
- Source of the abundance ratios plotted for other objects in the methanol comparison (Figure 4)
- The spectral line fitting code itself (described only by reference to Fadul25)
- Coordinates and source velocity (LSRK) of V883 Ori

## Analysis recipe

1. **Calibrate and image the Band 7 data**: ALMA pipeline calibration, then tclean imaging into a continuum-subtracted line cube  
  > "Data reduction was carried out using the standard ALMA calibration pipeline in the Common Astronomy Software Applications (CASA) package, version 6.4.1.12." (2 Observations and Data Reduction); "Imaging was carried out using *tclean* with Briggs weighting and a robust factor of 0.5." (2 Observations and Data Reduction)
   - software: CASA 6.4.1.12, tclean
   - parameter: Briggs weighting, robust = 0.5; beam 0.48'' x 0.29'', RMS 5.97 mJy/beam  
  > "The RMS noise level is 5.97 mJy beam$^{-1}$." (2 Observations and Data Reduction)
   - fitting: _not stated_
   - validation: _not stated_
2. **Build the LTE line emission model**: LTE model of line flux from emitting area, line width, Planck function and optical depth at line center, with spectroscopy from CDMS via Splatalogue  
  > "The model line emission is generated assuming local thermodynamic equilibrium (LTE) conditions using the formula" (3 Analysis); "were taken from the Cologne Database for Molecular Spectroscopy (CDMS; (cite: CDMS2001A&A; CDMSEndres_2016)) using “Splatalogue[^1]” online database." (3 Analysis)
   - software: spectral line fitting tool of Fadul25, CDMS, Splatalogue
   - parameter: emission radius R = 0.3''  
  > "$R = 0.3\ensuremath{''}$ is the emission radius" (3 Analysis)
   - parameter: distance d = 400 pc  
  > "$d=400$ pc is the distance to the star" (3 Analysis)
   - parameter: line FWHM = 2 km/s  
  > "$\Delta V = 2 \mathrm{ km\; s^{-1}}$ is the full width at half maximum (FWHM) of the line" (3 Analysis)
   - assumption: LTE; fixed emitting area and FWHM based on earlier higher-resolution COM observations  
  > "The emitting area and FWHM are both based on previous higher spatial resolution observations of COMs in V883 Ori (cite: Lee_2019)." (3 Analysis)
   - fitting: _not stated_
   - validation: _not stated_
3. **Fit EG and GN column density and temperature by MCMC**: emcee MCMC for Ntot and Tex of each molecule, one molecule at a time; previously identified molecules (Fadul25) subtracted first, then EG, then GN  
  > "is used to identify the best fit combination of $N_{tot}$ and $T_{ex}$ for each molecule." (3 Analysis); "Fitting is done one molecule at a time, with the best fit model subtracted from the spectra before fitting subsequent species." (3 Analysis)
   - software: emcee
   - parameter: 100 walkers, 10,000 steps, first 2,000 discarded as burn-in (stated for the GN posterior)  
  > "We ran an MCMC with 100 walkers for 10,000 steps. We discarded the first 2,000 steps as burn-in" (Appendix B)
   - parameter: EG temperature fixed to 300 K because it always approached the highest allowed temperature  
  > "For EG, $T_{ex}$ was not well constrained by the model, instead always approaching the highest allowed temperature." (3 Analysis); "We fixed the temperature to 300 K where we have a best fit from the model." (3 Analysis)
   - assumption: single temperature; two-temperature model gave no improvement  
  > "However, we find that using a two temperature model neither improves the fit nor provides a better constraint on the temperature(s)." (3 Analysis)
   - fitting: chi-squared evaluated at frequencies with emission above 5 sigma matching known transitions of the fitted molecule (priors not stated)  
  > "The goodness of fit is determined by calculating the $\chi^2$ at frequencies where emission is detected above $5\sigma$ corresponding to known transitions of the fitted molecule." (3 Analysis)
   - validation: GN Tex and Ntot judged well constrained from the posterior (Appendix B); EG Tex unconstrained  
  > "$\mathrm{T_{ex}}$ and $\mathrm{N_{tot}}$ are well constrain for GN by the model (see Appendix [7](#AppendixB))." (3 Analysis)
4. **Cross-check with isolated Gaussian line fits**: Fit multiple Gaussian profiles to all lines overlapping the target molecule, isolate the EG and GN Gaussians, then rerun the MCMC on the isolated Gaussians  
  > "we utilize a multiple Gaussian fitting approach in the region where transitions from EG or GN are present" (3 Analysis); "Subsequently, we run our MCMC model on the isolated Gaussian fits to identify the best-fit parameters." (3 Analysis)
   - software: emcee
   - fitting: _not stated_
   - validation: No significant improvement over fitting the observed data directly  
  > "No significant improvement was observed in the fit compared to the best-fit model applied directly to the observed data." (3 Analysis)
5. **Check for blending molecules**: Searched Splatalogue for molecules emitting at similar frequencies and modeled likely blenders (acetic acid, glycine, aminoacetonitrile, ethanol, propenal, methoxymethanol, vinyl alcohol, others from Fadul25)  
  > "We modeled the emission of molecules that are highly likely to blend with EG and GN, but none were found to overlap with these two species." (3 Analysis)
   - software: Splatalogue
   - fitting: _not stated_
   - validation: none of the tested molecules overlap EG or GN lines  
  > "none were found to overlap with these two species" (3 Analysis)
6. **Make moment maps of isolated EG and GN lines**: Moment 0 sums 4 EG and 2 GN transitions; moment 1 maps are averages; velocity gradient checked for disk rotation  
  > "The integrated intensity maps sum the emission from 4 transitions of EG and 2 transitions of GN respectively, while the intensity weighted velocity maps are averages." (3 Analysis)
   - assumption: emission from a Keplerian disk  
  > "This pattern supports our assumption of emission from a Keplerian disk centered at these frequencies." (3 Analysis)
   - fitting: _not stated_
   - validation: Moment 1 shows red-to-blue shift along the semi-major axis, consistent with a rotating disk  
  > "The moment 1 maps show a clear shift from red-shifted to blue-shifted across the disk semi-major axis, consistent with emission from a rotating disk." (3 Analysis)
7. **Derive GA upper limit**: Searched for GA; only two matching transitions blend with H2CO, so the best-fit model column density is taken as an upper limit  
  > "Therefore, we take column density from our best fit model as an upper limit." (4.2 Upper limits of GA)
   - parameter: gas temperature of 300 K for the EG/GA ratio  
  > "The non-detection of GA in our observations is consistent with $\mathrm{(CH_2OH)_2} /\ \mathrm{CH_2(OH)CHO} \leq 1.6$ for a gas temperature of 300 K." (4.4 Formation routes)
   - fitting: _not stated_
   - validation: _not stated_
8. **Compare abundances relative to methanol with other sources**: Ratio of derived EG and GN column densities to methanol column density (13CH3OH times 60), compared with other environments  
  > "To compare the abundances across sources, we take the ratio of the derived EG and GN column density to that of methanol" (4.1 Comparison to other sources); "Instead we use the $\mathrm{^{13}CH_3OH}$ column density multiplied by the canonical ISM $\mathrm{^{12}C/^{13}C}$ ratio of 60 (cite: Langer93ApJ)." (4.5 Uncertainty in the measured abundances)
   - assumption: canonical ISM 12C/13C = 60 used for CH3OH  
  > "multiplied by the canonical ISM $\mathrm{^{12}C/^{13}C}$ ratio of 60 (cite: Langer93ApJ)" (4.5 Uncertainty in the measured abundances)
   - fitting: _not stated_
   - validation: _not stated_
9. **Test the EG model against Band 6 archival data**: Predict EG spectrum at Tex = 300 K, Ntot = 3.6e16 cm-2 and overplot on archival Band 6 data; spectrum extracted with GoFish integrated_spectrum()  
  > "The data have been downloaded from the ALMA archive, and the spectrum was extracted using the function" (Appendix D); "The main parameters used to extract the spectrum are an inner radius of $0\ensuremath{''}$, an outer radius of $0.21\ensuremath{''}$, a position angle of $32^\circ$, an inclination angle of $38.3^\circ$" (Appendix D)
   - software: GoFish
   - parameter: inner radius 0'', outer radius 0.21'', PA 32 deg, inclination 38.3 deg, 388 pc, 1.29 Msun  
  > "a distance of 388 pc, and a stellar mass of 1.29 $\mathrm{M\odot}$ ((cite: Cieza2016Natur; Lee_2019; Tobin23; Yamato2024AJ))" (Appendix D)
   - fitting: _not stated_
   - validation: Model appears consistent with Band 6 observations; predicted EG emission weak, which could explain the earlier non-detection  
  > "our model appears consistent with the observations in this Band." (4.3 Previous non-detections of EG in V883 Ori)

## Software

- **CASA** 6.4.1.12: ALMA pipeline calibration and imaging  
  > "Data reduction was carried out using the standard ALMA calibration pipeline in the Common Astronomy Software Applications (CASA) package, version 6.4.1.12." (2 Observations and Data Reduction)
- **tclean** : Imaging with Briggs weighting, robust 0.5  
  > "Briggs weighting and a robust factor of 0.5" (2 Observations and Data Reduction)
- **emcee** : MCMC fit of Ntot and Tex for each molecule  
  > "is used to identify the best fit combination of $N_{tot}$ and $T_{ex}$ for each molecule." (3 Analysis)
- **Spectral line fitting tool (Fadul25)** : Identification and analysis of molecular lines  
  > "The identification and analysis of these lines was carried out with the spectral line fitting tool developed by (cite: Fadul25)." (3 Analysis)
- **GoFish** : Extracting the Band 6 integrated spectrum with integrated_spectrum()  
  > "The data have been downloaded from the ALMA archive, and the spectrum was extracted using the function" (Appendix D)
- **CDMS / Splatalogue** : Spectroscopic parameters and search for blending species  
  > "we checked the Splatalogue database to search for molecules that emit at similar frequencies" (3 Analysis)
- **Astropy** : Listed in the Software section; specific use not stated  
  > "Astropy (cite: 2013A&A...558A..33A; 2018AJ....156..123A; astropy:2022)" (Software)
- **Numpy** : Listed in the Software section; specific use not stated  
  > "Numpy (cite: numpyharris2020array)" (Software)
- **Matplotlib** : Listed in the Software section; specific use not stated  
  > "Matplotlib (cite: matplotlibHunter:2007)" (Software)
- **corner.py** : Listed in the Software section; presumably posterior plots (use not stated)  
  > "corner.py (cite: corner)" (Software)
- **Pandas** : Listed in the Software section; specific use not stated  
  > "Pandas (cite: pandasmckinney-proc-scipy-2010)" (Software)

## Numeric results

| quantity | value | uncertainty | units | step | quote |
|---|---|---|---|---|---|
| EG column density (Ntot) | 3.63e16 in abstract and conclusions (3.62e16 in results table) | +0.11/-0.12 e16 | cm^-2 | 3 | We find the observations are best fit by a model of EG with a column density $3.63^{+0.11}_{-0.12}\times10^{16}$ cm$^\mathrm{-2}$, where the temperature has been fixed to 300 K. |
| EG excitation temperature (Tex) | 300 (fixed; at least 300 K per abstract) | not stated | K | 3 | and a temperature of at least 300 K |
| GN column density (Ntot) | 3.37e16 | +0.09/-0.09 e16 | cm^-2 | 3 | GN is best fit by a column density of $3.37^{+0.09}_{-0.09}\times10^{16}$ cm$^\mathrm{-2}$ and a temperature of $88^{+1.2}_{-1.2}$ K. |
| GN excitation temperature (Tex) | 88 | +1.2/-1.2 | K | 3 | and a temperature of $88^{+1.2}_{-1.2}$ K. |
| Number of tentatively identified transitions (EG, GN) | 15 EG, 6 GN in text (table lists 18 and 9) | not stated | dimensionless | 3 | We tentatively identify 15 transitions of EG and 6 transitions of GN |
| EG/GA column density ratio upper limit (T = 300 K) | <= 1.6 | not stated | dimensionless | 7 | The non-detection of GA in our observations is consistent with $\mathrm{(CH_2OH)_2} /\ \mathrm{CH_2(OH)CHO} \leq 1.6$ for a gas temperature of 300 K. |
| Final cube RMS noise | 5.97 | not stated | mJy/beam | 1 | The RMS noise level is 5.97 mJy beam$^{-1}$. |

## Qualitative findings

- EG abundance relative to methanol in V883 Ori is above Class 0 protostellar envelopes and below comets  
  > "The abundance of EG relative to methanol in V883 Ori is greater than that seen in Class 0 protostellar envelopes but less than that of comets." (4.1 Comparison to other sources)
- GN/methanol in V883 Ori is orders of magnitude above less evolved environments  
  > "The abundance ratio of GN relative to methanol in V883 Ori is several orders of magnitude higher than the ratio in less evolved environments." (4.1 Comparison to other sources)
- Moment 1 maps of EG and GN show a rotation pattern consistent with a disk  
  > "consistent with emission from a rotating disk" (3 Analysis)

## Claim tuples

- H: Are EG and GN present in the V883 Ori protoplanetary disk? | E: Band 7 (348-366 GHz) spectral scan modelled with an LTE MCMC fit after subtracting previously identified molecules | R: 15 EG and 6 GN transitions tentatively identified; EG N=3.63e16 cm-2 (T fixed 300 K), GN N=3.37e16 cm-2, T=88 K | F: Tentative first detection of EG and GN in a protoplanetary disk | **partially**
- H: Does complexity persist and grow from envelopes to disks? | E: EG/CH3OH and GN/CH3OH ratios in V883 Ori compared with other sources | R: EG/CH3OH above Class 0 envelopes and below comets; GN/CH3OH orders of magnitude above less evolved sources | F: Disks inherit complex molecules from envelopes and COM formation continues in the disk | **partially**
- H: Is GA detected, and does EG form from GA? | E: Search for GA in the same spectrum and model upper limit | R: No robust GA detection; EG/GA <= 1.6 at 300 K | F: Formation mechanism of EG cannot be determined | **partially**
- H: Is the Band 7 EG model consistent with earlier Band 6 non-detections? | E: Overplot Band 7 best-fit EG prediction on archival Band 6 spectrum | R: Predicted EG emission is relatively weak and consistent with Band 6 data | F: Band 6 data appear to support EG in V883 Ori, though a more detailed analysis is needed | **partially**

## Reasoning

- Why this data: Frequency range not previously explored for V883 Ori and promising for prebiotic molecules and GA  
  > "Our observations cover a frequency range not yet explored for this object, but which has yielded tentative detections of pre-biotic molecules in less evolved sources." (1 Introduction); "Our observations focus on a higher frequency range in part because this regime should provide the highest signal-to-noise ratio for GA emission" (4.2 Upper limits of GA)
- Why this method: _not stated_
- Alternative: Two-temperature model for EG rejected: no better fit or constraint  
  > "However, we find that using a two temperature model neither improves the fit nor provides a better constraint on the temperature(s)." (3 Analysis)
- Alternative: Possible blending species (acetic acid, glycine, aminoacetonitrile, ethanol, propenal, methoxymethanol, vinyl alcohol) tested and found not to overlap  
  > "The molecules tested include: Acetic acid, Glycine, Aminoacetonitrile, Ethanol, Propenal, Methoxymethanol, Vinyl alcohol, among others already examined by (cite: Fadul25)." (3 Analysis)
- How they decided it was enough: Chi-squared evaluated at frequencies with emission above 5 sigma at known transitions  
  > "The goodness of fit is determined by calculating the $\chi^2$ at frequencies where emission is detected above $5\sigma$ corresponding to known transitions of the fitted molecule." (3 Analysis)
- Limitation (authors): EG temperature not constrained and a more complex temperature structure is possible  
  > "However, it is possible that the data would be better fit by a model with a more complex temperature structure." (3 Analysis)
- Limitation (authors): Significant line blending at 0.42 km/s resolution; detections tentative  
  > "there is significant line blending at the current spectral resolution of 0.42 km" (4.5 Uncertainty in the measured abundances)
- Limitation (authors): CH3OH column density not reliably measured; canonical 12C/13C may overestimate it  
  > "Since $\mathrm{CH_3OH}$ column density is not reliably measured, its difficult to constrain from the main isotopologue." (4.5 Uncertainty in the measured abundances)
- Limitation (authors): Further higher spectral resolution observations needed to confirm  
  > "Further observations of this protoplanetary disk at higher spectral resolution are required to resolve blended lines and to confirm these tentative detection." (abstract)
- Caveat (inferred, ours): Text, abstract and table disagree: 15/6 vs 18/9 lines, EG N 3.63e16 vs 3.62e16, so the key numbers are ambiguous
- Caveat (inferred, ours): Fixed single emitting radius (0.3'') and 2 km/s FWHM from a different dataset drive derived column densities; the beam (0.48'' x 0.29'') does not resolve the emission
- Caveat (inferred, ours): Detections rest on heavily blended lines at 0.42 km/s resolution with a T = 300 K fixed EG model; a confirmed detection is not shown
- Caveat (inferred, ours): Abundance ratios depend on a CH3OH column estimated from 13CH3OH with an assumed 12C/13C = 60 and on literature ratios not tabulated here
- Caveat (inferred, ours): The 100 per cent dependence on the unreleased Fadul25 fitting tool and prior subtraction of other molecules hinders independent checks

## Reproducibility

- Data public (paper): Band 6 comparison data were downloaded from the ALMA archive; public status of project 2021.1.00452.S not stated  
  > "The data have been downloaded from the ALMA archive" (Appendix D)
- Products in archive: _not stated_
- Missing: Spectral line fitting code and settings (only referenced to Fadul25)
- Missing: Column densities and temperatures of all other molecules subtracted before EG and GN fits
- Missing: Continuum subtraction, line-free channels, cleaning parameters, spectrum extraction region
- Missing: MCMC priors and parameter bounds
- Missing: Source of literature abundance ratios in the methanol comparison
- Data volume (inferred): Six execution blocks of Band 7 spectral scan data; likely tens to a few hundred GB raw (rough guess)
- Score (inferred): 2/5, The equations, MCMC setup and key numeric results are given, but the fitting tool and the other-molecule model are in a previous paper; imaging details are sparse; the project's public status is not stated; table and text numbers disagree.
- Rediscovery candidate: no, The recipe depends on an unreleased tool and subtraction of other molecules from a companion paper, and the data's public status is not stated.

## Links

- Method: (cite: Fadul25) (Describes the spectral line fitting tool, the LTE model, calibration and observation details, and the other molecules subtracted)
- Companion: (cite: Fadul25) (Companion paper on the molecular line spectrum of V883 Ori from the same data)
- Companion: (cite: Lee2025ApJ) (Band 6 data in which EG was not detected, used for the consistency check)
- Companion: (cite: Lee_2019) (Source of emitting area and line FWHM from higher-resolution COM observations of V883 Ori)
- Related: 2021.1.00452.S

## Checks

```json
{
 "quotes": 108,
 "quotes_ok": 108,
 "quote_pass_rate": 1.0,
 "quotes_too_long": 0,
 "unsupported_facts": 0,
 "project_codes": 1,
 "codes_not_in_text": [],
 "codes_not_in_obscore": [],
 "obscore_codes_not_in_card": [],
 "codes_printed_but_missing": [],
 "numeric_results": 7,
 "numeric_problems": 0,
 "fill": {
  "facts": 117,
  "stated": 80,
  "rate": 0.684
 },
 "evidence_ok": true
}
```
