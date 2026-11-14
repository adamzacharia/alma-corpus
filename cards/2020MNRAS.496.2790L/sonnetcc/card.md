# ATOMS: ALMA Three-millimeter Observations of Massive Star-forming regions - I. Survey description and a first look at G9.62+0.19

`2020MNRAS.496.2790L` | Monthly Notices of the Royal Astronomical Society 2020 | first author: Liu, Tie | arXiv: 2006.01549 | DOI: 10.1093/mnras/staa1577

Card schema 1.0 | model claude-sonnet-5-5-claude-code | depth full | type large_program_or_survey

## Science

- Fields: star_formation, milky_way_ism, astrochemistry
- Question: Survey paper: map the spatial distribution of dense gas tracers in Galactic massive clumps, study stellar feedback and characterize filaments; G9.62+0.19 used as a case study  
  > "aiming to systematically investigate the spatial distribution of various dense gas tracers in a large sample of Galactic massive clumps, to study the roles of stellar feedback in star formation, and to characterize filamentary structures inside massive clumps" (abstract)
- Target **G9.62+0.19 (I18032-2032, ATOMS source 108)**: coordinates RA 18:06:14.99, Dec -20:31:35.4 (sample table, ID 108)  
  > "which is an active high-mass star forming region located at a distance of 5.2$_{-0.6}^{+0.6}$ kpc (cite: san09)" (The sample of ATOMS); "18:06:14.99 | -20:31:35.4" (Table of ATOMS sample); z/distance 5.2 (+0.6/-0.6) kpc  
  > "which is an active high-mass star forming region located at a distance of 5.2$_{-0.6}^{+0.6}$ kpc (cite: san09)" (The sample of ATOMS); "18:06:14.99 | -20:31:35.4" (Table of ATOMS sample); distance from (cite: san09)  
  > "which is an active high-mass star forming region located at a distance of 5.2$_{-0.6}^{+0.6}$ kpc (cite: san09)" (The sample of ATOMS); "18:06:14.99 | -20:31:35.4" (Table of ATOMS sample)
- Target **ATOMS sample of 146 massive star-forming clumps**: coordinates per-source coordinates in the sample table  
  > "The distances of the sample clouds range from 0.4 kpc to 13.0 kpc with a mean value of 4.5 kpc." (The sample of ATOMS); z/distance 0.4 to 13.0 kpc, mean 4.5 kpc  
  > "The distances of the sample clouds range from 0.4 kpc to 13.0 kpc with a mean value of 4.5 kpc." (The sample of ATOMS); distance from parameters adopted from (cite: Urquhart2018) for 122 clumps and (cite: Faundez2004) for the rest  
  > "The distances of the sample clouds range from 0.4 kpc to 13.0 kpc with a mean value of 4.5 kpc." (The sample of ATOMS)

## Data provenance

- ALMA projects: 2019.1.00685.S
- bands: Band 3 (3 mm), dual polarization  
  > "The observations employed the Band 3 receivers in dual-polarization mode." (ALMA Observations)
- frequencies and spectral setup: 8 SPWs covering 11 lines: SPWs 1-6 are 58.59 MHz wide (0.2-0.4 km/s resolution), SPWs 7-8 are 1875 MHz wide (~3 km/s)  
  > "Eight spectral windows (SPWs) were configured to cover 11 commonly-used lines including the dense gas tracers" (ALMA Observations); "Two wide SPWs, each one having 1875 MHz bandwidth" (ALMA Observations)
- continuum bandwidth: two wide SPWs of 1875 MHz each used for continuum and line scan  
  > "are used for continuum emission and line scan survey" (ALMA Observations)
- arrays: ACA (7 m) and 12-m array  
  > "with both the Atacama Compact 7 m Array (ACA; Morita Array) and the 12-m array" (ALMA Observations)
- configurations: 12-m array C43-2 or C43-3  
  > "the 12-m array (C43-2 or C43-3 configurations)" (ALMA Observations)
- baselines: _not stated_
- angular resolution: 12-m ~1.2''-1.9'' (G9.62+0.19 continuum beam 1.56''x1.38''); ACA ~13.1''-13.8''  
  > "The angular resolution and maximum recovering angular scale for the 12-m array observations are $\sim1.2\ensuremath{''}-1.9\ensuremath{''}$ and $\sim14.5\ensuremath{''}-20.3\ensuremath{''}$, respectively." (ALMA Observations)
- max recoverable scale: 12-m ~14.5''-20.3'' (sensitive to scales smaller than ~20''); ACA ~53.8''-76.2'' (smaller than ~60'')  
  > "These ACA and 12-m array observations are sensitive to angular scales smaller than $\sim60\ensuremath{''}$ and $\sim20\ensuremath{''}$, respectively." (ALMA Observations)
- sensitivity: 12-m 3.7 to 9.6 mJy/beam per 0.122 MHz channel across the survey; G9.62+0.19 continuum 1 sigma 0.2 mJy (12-m) and 4 mJy (ACA)  
  > "The obtained sensitivity in 12-m array observations ranges from 3.7 to 9.6 mJy beam per 0.122 MHz channel." (ALMA Observations); "reaches a 1$\sigma$ rms noise of 0.2 mJy in a synthesized beam of 1.56$\ensuremath{''}\times1.38\ensuremath{''}$ (P.A.=87.62$\ensuremath{^\circ}$)" (ALMA Observations)
- time on source: typical 12-m ~3 minutes, typical ACA ~8 minutes per source  
  > "The typical 12-m array time on source is $\sim$ 3 minutes, while typical ACA observing time per source is $\sim$ 8 minutes." (ALMA Observations)
- observing dates: late September to mid November 2019; G9.62+0.19: ACA 1 and 13 October 2019 (two executions), 12-m 31 October 2019  
  > "were conducted from late September to mid November 2019" (ALMA Observations); "were conducted on the 1st and 13th October, 2019, with two executions." (ALMA Observations); "The 12-m array observations of G9.62+0.19 were conducted on the 31st October, 2019." (ALMA Observations)
- pi or archival as stated: Own project, PI Tie Liu (single-pointing observations)  
  > "with band 3 (Project ID: 2019.1.00685.S; PI: Tie Liu)" (ALMA Observations); "We conducted single-pointing observations with ALMA." (ALMA Observations)
- Line: H13CN 1-0 (86.339918 GHz)
- Line: H13CO+ 1-0 (86.754288 GHz)
- Line: CCH 1-0 (87.316898 GHz)
- Line: SiO 2-1 (86.84696 GHz)
- Line: HCN 1-0 (88.631847 GHz)
- Line: HCO+ 1-0 (89.188526 GHz)
- Line: CH3OH 2(1,1)-1(1,0)A (97.582798 GHz)
- Line: CS 2-1 (97.980953 GHz)
- Line: SO 3(2)-2(1) (99.29987 GHz)
- Line: H recombination line H40alpha (99.022952 GHz)
- Line: HC3N 11-10 (100.07639 GHz)
- External data: Parent sample: CS J=2-1 survey of UC HII region candidates (SEST)  
  > "The ATOMS sample of 146 sources were selected from the CS $J=2-1$ survey of (cite: Bronfman1996)" (The sample of ATOMS) [from (cite: Bronfman1996)]
- External data: Basic clump parameters (distance, T_dust, L_bol, M_clump, radius) for 122 clumps with ATLASGAL and HiGAL counterparts  
  > "The basic parameters for these 122 clumps are adopted from (cite: Urquhart2018)." (The sample of ATOMS) [from (cite: Urquhart2018)]
- External data: Basic clump parameters for the remaining clumps  
  > "The basic parameters for the remaining clumps are adopted from (cite: Faundez2004)." (The sample of ATOMS) [from (cite: Faundez2004)]
- External data: Distance to G9.62+0.19 of 5.2 kpc  
  > "located at a distance of 5.2$_{-0.6}^{+0.6}$ kpc (cite: san09)" (The sample of ATOMS) [from (cite: san09)]
- External data: Critical density and effective excitation density of the lines  
  > "The critical density and effective excitation density are from (cite: Shirley2015)." (Table spws) [from (cite: Shirley2015)]
- External data: Electron temperature ~6760 K for the free-free estimate  
  > "An electron temperature of $\sim$6760 K is adopted, which is derived from the electron temperature gradient in the Galactic disk (cite: Quireza2006)." (Filaments and dense cores) [from (cite: Quireza2006)]
- External data: 12 dense cores in G9.62+0.19 with total mass ~400 Msun at average dust temperature 35 K  
  > "(cite: Liu2017) identified 12 dense cores in G9.62+0.19." (Fraction of line fluxes from filaments and cores); "assuming an average dust temperature of 35 K (cite: Liu2017)" (Fraction of line fluxes from filaments and cores) [from (cite: Liu2017)]
- External data: Median L'mol-to-M_dense conversion factors for CS 2-1, CS 7-6, HCN 1-0, HCN 3-2 (20, 39, 16, 19 Msun per K km/s pc2)  
  > "found that the median conversion factors from line luminosity to dense gas masses" (Fraction of line fluxes from filaments and cores) [from (cite: Wu2010)]

## Processing

### Calibration

- pipeline or manual: _not stated_
- casa version: CASA 5.6  
  > "Calibration and imaging were carried out using the CASA software package version 5.6 (cite: McMullin2007)." (ALMA Observations)
- pipeline version: _not stated_
- archive products used as is: _not stated_
- flux calibrator: _not stated_
- flux scale uncertainty: _not stated_
- self calibration: _not stated_

### Imaging

- task: _not stated_
- deconvolver: _not stated_
- weighting robust: _not stated_
- uv taper: _not stated_
- cell size: 0.27'' pixel size (as used in the FellWalker source extraction)  
  > "The minimum number of contiguous pixels (pixel size=0.27" (Filaments and dense cores)
- image size: _not stated_
- masking: moment maps made with a 3 sigma cutoff; line integration over 1.5 to 6.5 km/s  
  > "The moment maps were constructed from the data after imposing a cutoff of 3$\sigma$." (Moment maps in 12-m array observations); "we integrate their intensity in the same velocity interval that is from 1.5 to 6.5 km s$^{-1}$ above a threshold of 3$\sigma$." (Moment maps in 12-m array observations)
- multiscale scales: _not stated_
- continuum subtraction: _not stated_
- line free channels: continuum visibilities built from line-free channels; channel ranges not given  
  > "We construct continuum visibility data using the line-free spectral channels for G9.62+0.19." (ALMA Observations)
- primary beam correction: _not stated_
- array combination: ACA and 12-m calibrated and imaged separately, not combined for the science case study; a feather test (HCO+, H13CO+) was shown in Figure 4  
  > "The ACA data and 12-m array data were calibrated and imaged separately." (ALMA Observations); "we simply combine the 12-m array data and ACA data of G9.62+0.19 in Fourier space with the CASA task" (ALMA Observations); "Hence, in this paper, the ACA data and 12-m array data were not combined for the case study of G9.62+0.19" (ALMA Observations)
- smoothing: maps smoothed and re-gridded to a common resolution and pixel size before PCA  
  > "These maps are firstly smoothed and re-gridded to ensure that they have the same resolution and pixel size." (Principal component analysis)
- final beam: 12-m continuum 1.56''x1.38'' (PA 87.62 deg); lines 1.9''x1.7'' (SPWs 1-6) and 1.6''x1.4'' (SPWs 7-8); ACA continuum 17.23''x9.46''  
  > "The typical synthesized beam is 1.9$\ensuremath{''}\times1.7\ensuremath{''}$ for lines at lower band (SPWs 1-6)" (ALMA Observations); "reaches a 1$\sigma$ rms noise of 0.2 mJy in a synthesized beam of 1.56$\ensuremath{''}\times1.38\ensuremath{''}$ (P.A.=87.62$\ensuremath{^\circ}$)" (ALMA Observations)
- final rms: 12-m: continuum 0.2 mJy; lines ~8 mJy/beam per 0.122 MHz channel (SPWs 1-4), ~10 mJy/beam (SPWs 5-6), ~3 mJy/beam (wide SPWs); ACA continuum 4 mJy  
  > "The 1$\sigma$ rms noise is about 8 mJy beam$^{-1}$ at SPWs 1-4 per 0.122 MHz channel." (ALMA Observations)

### Inherited from earlier work

- Properties of the 3 mm continuum sources in G9.62+0.19 (not re-derived)  
  > "Since the properties of all the continuum sources have been well discussed in (cite: Liu2017), we will not derive any other parameters from the 3 mm continuum emission in this work." (Filaments and dense cores) [from (cite: Liu2017)]
- Source extraction algorithm (FellWalker in Starlink CUPID)  
  > "we apply the FellWalker algorithm in the Starlink CUPID package (cite: Berry2007; Berry2015), for source extraction" (Filaments and dense cores) [from (cite: Berry2007; Berry2015)]
- Minimum core size definition of half a synthesized beam  
  > "which was used to define the smallest structures, i.e., "cores" (cite: Sanhueza2019)" (Filaments and dense cores) [from (cite: Sanhueza2019)]
- Free-free contribution from line-to-continuum ratio of the recombination line  
  > "by deriving the line-to-continuum intensity ratio (cite: Condon2016; Liu2019)" (Filaments and dense cores) [from (cite: Condon2016; Liu2019)]
- PCA procedure  
  > "following a provider similar to that adopted in these previous works" (Principal component analysis) [from (cite: Lo2009; Jones2012; Jones2013; Spezzano2017; Nagy2019)]
- HOG analysis procedure and definitions of r, V and AM  
  > "we performed a HOGs analysis on the integrated intensity maps of various gas tracers following the procedure in (cite: Soler2019)" (Histogram of oriented gradients analysis); "The definitions of these parameters are given in (cite: Soler2019)." (Histogram of oriented gradients analysis) [from (cite: Soler2019)]
- Conversion of line flux to line luminosity  
  > "We can convert the total flux densities of these lines into their line luminosity following (cite: Solomon1997)." (Fraction of line fluxes from filaments and cores) [from (cite: Solomon1997)]
- Proper ACA plus 12-m data combination deferred to a later paper  
  > "We will more properly combine the ACA data and 12-m array data in future studies and discuss the data combination issue in a forthcoming paper (Wang et al. 2020, in preparation)." (ALMA Observations) [from Wang et al. 2020, in preparation]

### Not stated but needed to reproduce (our reading)

- CASA calibration route (pipeline vs manual) and pipeline version; calibrators and flux-scale uncertainty
- tclean parameters: weighting and robust, deconvolver, niter and threshold, cell and image size, masking, uv taper
- Which channels were considered line-free for the continuum and how the line cubes were continuum subtracted
- Channel width and velocity resolution of the line cubes actually imaged, and primary-beam correction
- Whether ACA data were imaged with the same parameters as the 12-m data and how the ACA 2D Gaussian fits were bounded
- How the integrated-intensity maps were smoothed and re-gridded for PCA and HOG (common beam, pixel size, regions, noise handling), and the HOG kernel/gradient settings
- FellWalker configuration beyond the 3 sigma threshold and 12-pixel minimum (e.g. noise estimate, merging parameters)
- Spectral extraction apertures for the H40alpha and SiO spectra and the Gaussian-fit initial guesses
- Exact free-free formula (line-to-continuum ratio equation, line frequency, helium abundance) used for Table continuumpara
- Sky region or polygon used for the filament mask (1% of peak 3 mm contour) and how total fluxes were summed

## Analysis recipe

1. **Calibrate and image ACA and 12-m data separately**: Calibrated and imaged separately in CASA; continuum visibilities built from line-free channels; line cubes imaged for SPWs 1-8  
  > "The ACA data and 12-m array data were calibrated and imaged separately." (ALMA Observations); "We construct continuum visibility data using the line-free spectral channels for G9.62+0.19." (ALMA Observations)
   - software: CASA 5.6
   - fitting: _not stated_
   - validation: _not stated_
2. **Test flux recovery of 12-m data versus ACA and a combined image**: Feathered 12-m and ACA data of G9.62+0.19 for HCO+ and H13CO+ and compared spectra and integrated maps  
  > "we simply combine the 12-m array data and ACA data of G9.62+0.19 in Fourier space with the CASA task" (ALMA Observations)
   - software: CASA feather
   - fitting: _not stated_
   - validation: 12-m alone recovers more than 90% of HCO+ and H13CO+ flux; integrated maps nearly identical to combined  
  > "We found that 12-m array data alone has recovered more than 90% of the flux in both H$^{13}$CO$^{+}$ and HCO$^{+}$ emission." (ALMA Observations)
3. **Extract 3 mm continuum cores**: FellWalker clump finding on the 3 mm continuum, then 2D Gaussian fit with beam deconvolution  
  > "The detected sources were fitted with a 2D Gaussian profile and de-convolved with the beam size." (Filaments and dense cores)
   - software: Starlink CUPID FellWalker
   - parameter: detection threshold 3 sigma  
  > "Source extraction was conducted in regions above a threshold of 3$\sigma$." (Filaments and dense cores)
   - parameter: minimum 12 contiguous pixels (half the synthesized beam)  
  > "was set at 12, equaling to those contained in half of the synthesized beam" (Filaments and dense cores)
   - fitting: 2D Gaussian profile fitted to detected sources  
  > "The detected sources were fitted with a 2D Gaussian profile and de-convolved with the beam size." (Filaments and dense cores)
   - validation: Tested larger minimum pixel numbers 16 and 25; results unchanged  
  > "We also tested FellWalker with larger minimum number (16 and 25) of contiguous pixels and found that the results were not changed." (Filaments and dense cores)
4. **Estimate free-free contribution to the 3 mm continuum**: Fitted H40alpha spectra with Gaussians and used the line-to-continuum ratio to estimate free-free emission for B, MM1/C, MM11/D  
  > "radio recombination line (RRL) to estimate the contribution of free-free emission in continuum by deriving the line-to-continuum intensity ratio" (Filaments and dense cores); "The spectra were fitted with gaussian profiles" (Filaments and dense cores)
   - assumption: Electron temperature ~6760 K from the Galactic-disk gradient  
  > "An electron temperature of $\sim$6760 K is adopted, which is derived from the electron temperature gradient in the Galactic disk (cite: Quireza2006)." (Filaments and dense cores)
   - fitting: Gaussian profiles to source-averaged H40alpha spectra  
  > "The spectra were fitted with gaussian profiles" (Filaments and dense cores)
   - validation: Compared with earlier work that suggested free-free dominance; no independent cm-wave check  
  > "is dominated by free-free emission, as suggested in previous works" (Filaments and dense cores)
5. **Fit ACA clump emission and make 12-m moment maps**: 2D Gaussian fits to ACA integrated-intensity maps within the 20% contour; 12-m moment 0, 1 and 2 maps over 1.5-6.5 km/s with 3 sigma cutoff  
  > "We performed 2D Gaussian fitting in the gas emission regions bounded by the 20% contour of their peak values." (Gas clumps in ACA observations of G9.62+0.19); "The moment maps were constructed from the data after imposing a cutoff of 3$\sigma$." (Moment maps in 12-m array observations)
   - software: CASA
   - parameter: velocity interval 1.5 to 6.5 km/s, chosen from the H13CO+ line width to avoid outflow contamination  
  > "This velocity interval is chosen based on the line width of H$^{13}$CO$^{+}$ to avoid contamination from outflow emission." (Moment maps in 12-m array observations)
   - fitting: 2D Gaussian fits (ACA); Gaussian fits to spectra giving Vlsr ~4 km/s and width ~5 km/s for H13CO+  
  > "From gaussian fits to the spectra, we find a systemic velocity of $\sim$4 km s$^{-1}$." (Moment maps in 12-m array observations)
   - validation: 12-m recovers more than 92% of the ACA H13CO+ flux  
  > "The 12-m array observation recovers more than 92% of H$^{13}$CO$^{+}$ flux in ACA observations." (Moment maps in 12-m array observations)
6. **Characterise widespread narrow SiO emission**: Extracted SiO spectra averaged over 5'' at nine positions and fitted single or double Gaussians  
  > "The SiO spectra were obtained by averaging over 5$\ensuremath{''}$ area at each position." (Widespread shocked gas emission); "Spectra at positions 1, 4 and 9 can be well fitted with a single gaussian profile, while spectra at positions 2, 3, 7, and 8 are better fitted with two gaussians including one narrow component and one broad component." (Widespread shocked gas emission)
   - fitting: Gaussian profiles (one or two components)  
  > "We fit the spectra with gaussian profiles" (Widespread shocked gas emission)
   - validation: _not stated_
7. **Principal component analysis of integrated-intensity maps**: PCA on the integrated emission maps of ten molecules (smoothed, re-gridded, pixel values exported to SPSS)  
  > "We performed PCA on the integrated emission maps of various gas tracers" (Principal component analysis); "We then export their pixel values to SPSS software platform" (Principal component analysis)
   - software: SPSS
   - parameter: components with eigenvalues larger than 0.5 retained (PCs 1-3)  
  > "We identified three main principal components (or PCs 1-3) that have eigenvalues larger than 0.5." (Principal component analysis)
   - fitting: _not stated_
   - validation: Cross-checked against the HOG results, with the same molecule groups showing strongest correlations  
  > "Molecules in the same group defined by the PCA analysis in Figure [14](#PCA-plt) show the strongest correlations in the HOGs analysis." (Histogram of oriented gradients analysis)
8. **Histogram of oriented gradients analysis**: HOG on integrated-intensity maps giving r, V and AM for each pair of tracers; relative-orientation histograms between continuum and lines in the filament region  
  > "Three statistical evaluation parameters are derived: mean resultant vector length ($r$), the projected Rayleigh statistic ($V$), and the alignment measurement ($AM$)." (Histogram of oriented gradients analysis); "We only performed HOGs analysis in the massive filament region." (Histogram of oriented gradients analysis)
   - fitting: _not stated_
   - validation: Consistency with the PCA groups  
  > "The HOGs analysis is also consistent with the previous PCA analysis." (Histogram of oriented gradients analysis)
9. **Fraction of line flux from the dense filament**: Ratio of 12-m integrated intensity inside the filament mask (1% of peak 3 mm contour) to ACA 2D-Gaussian total integrated intensity, over 1.5-6.5 km/s  
  > "measured within the massive filament region that is bounded by the 1% of peak flux density contour" (Fraction of line fluxes from filaments and cores); "We did not perform 2D Gaussian fitting on 12-m array data because the massive filament is far from a 2D Gaussian shape." (Fraction of line fluxes from filaments and cores)
   - fitting: 2D Gaussian for ACA only  
  > "are derived from a 2D gaussian fitting" (Fraction of line fluxes from filaments and cores)
   - validation: Ratios correlate with the HOG AM values  
  > "There is a clear trend between the ratios and the $AM$ values." (Fraction of line fluxes from filaments and cores)
10. **Line luminosity and conversion to dense-core mass**: Converted total ACA line fluxes to line luminosities and divided the ~400 Msun total core mass by them  
  > "We can convert the total flux densities of these lines into their line luminosity following (cite: Solomon1997)." (Fraction of line fluxes from filaments and cores)
   - assumption: Total core mass ~400 Msun from earlier work at average dust temperature 35 K; distance 5.2 kpc  
  > "assuming an average dust temperature of 35 K (cite: Liu2017)" (Fraction of line fluxes from filaments and cores)
   - fitting: _not stated_
   - validation: _not stated_

## Software

- **CASA** 5.6: calibration and imaging; feather combination test  
  > "Calibration and imaging were carried out using the CASA software package version 5.6 (cite: McMullin2007)." (ALMA Observations)
- **FellWalker (Starlink CUPID)** : source extraction in the 3 mm continuum  
  > "we apply the FellWalker algorithm in the Starlink CUPID package (cite: Berry2007; Berry2015), for source extraction" (Filaments and dense cores)
- **XCLASS** : line identification and LTE spectral simulation of MM8/F (illustration only)  
  > "We will identify spectral line transitions using the eXtended CASA Line Analysis Software Suite (cite: Moller2017)" (Chemical differentiation among dense cores)
- **SPSS** : principal component analysis  
  > "We then export their pixel values to SPSS software platform" (Principal component analysis)

## Numeric results

| quantity | value | uncertainty | units | step | quote |
|---|---|---|---|---|---|
| Number of continuum components found by FellWalker in G9.62+0.19 | 6 | not stated | dimensionless | 3 | we identified six main components in the 3 mm continuum emission of G9.62+0.19 |
| 3 mm flux density of HII region B and free-free flux | S_nu = 437 mJy; S_free-free = 359 mJy | not stated | mJy | 4 | 4.6 / 437 / 359 |
| 3 mm flux density of MM1/C and free-free flux | S_nu = 32.6 mJy; S_free-free = 32 mJy | not stated | mJy | 4 | 8.17 / 32.6 / 32 |
| 3 mm flux density of MM11/D and free-free flux | S_nu = 98.8 mJy; S_free-free = 73 mJy | not stated | mJy | 4 | 71.6 / 98.8 / 73 |
| H13CO+ systemic velocity of G9.62+0.19 | ~4 | not stated | km/s | 5 | From gaussian fits to the spectra, we find a systemic velocity of $\sim$4 km s$^{-1}$. |
| Width of the narrow SiO components | 2 to 6 | not stated | km/s | 6 | The line widths of the narrow components range from 2 km s$^{-1}$ to 6 km s$^{-1}$. |
| PCA variance fraction of PC1, PC2, PC3 | 73.62, 9.40, 6.22 | not stated | per cent | 7 | These three PCs describe 73.62, 9.40 and 6.22 per cent, respectively, of the variance in the data. |
| HOG r, V, AM for HC3N versus H13CN | r = 0.43, V = 1770, AM = 0.61 | not stated | dimensionless | 8 | The strongest correlation occurs between HC$_3$N and H$^{13}$CN with $r$ of 0.43, $V$ of 1770 and $AM$ of 0.61. |
| HOG r, V, AM for HC3N versus 3 mm continuum | r = 0.32, V = 1138, AM = 0.53 | not stated | dimensionless | 8 | The $r$, $V$ and $AM$ for the HC$_3$N and 3 mm continuum correlation are 0.32, 1138 and 0.53, respectively. |
| HOG r, V, AM for SiO versus 3 mm continuum | r = 0.08, V = 119, AM = 0.32 | not stated | dimensionless | 8 | The $r$, $V$ and $AM$ for the SiO and 3 mm continuum correlation are 0.08, 119 and 0.32, respectively |
| 12-m to ACA flux ratio, H13CN | 0.42 | not stated | dimensionless | 9 | 15.3 / 32.3 / 13.5 / 0.42 |
| 12-m to ACA flux ratio, H13CO+ | 0.29 | not stated | dimensionless | 9 | 15.0 / 38.1 / 11.2 / 0.29 |
| 12-m to ACA flux ratio, CCH | 0.23 | not stated | dimensionless | 9 | 13.0 / 38.7 / 8.7 / 0.23 |
| 12-m to ACA flux ratio, SiO | 0.22 | not stated | dimensionless | 9 | 10.3 / 20.7 / 4.6 / 0.22 |
| 12-m to ACA flux ratio, HCN | 0.18 | not stated | dimensionless | 9 | 12.1 / 46.4 / 8.5 / 0.18 |
| 12-m to ACA flux ratio, HCO+ | 0.17 | not stated | dimensionless | 9 | 23.6 / 89.3 / 15.3 / 0.17 |
| 12-m to ACA flux ratio, CH3OH | 0.59 | not stated | dimensionless | 9 | 10.6 / 17.2 / 10.1 / 0.59 |
| 12-m to ACA flux ratio, CS | 0.23 | not stated | dimensionless | 9 | 53.9 / 166.3 / 38.1 / 0.23 |
| 12-m to ACA flux ratio, SO | 0.31 | not stated | dimensionless | 9 | 28.8 / 62.2 / 19.4 / 0.31 |
| 12-m to ACA flux ratio, HC3N | 0.51 | not stated | dimensionless | 9 | 34.5 / 70.2 / 35.9 / 0.51 |
| Line luminosities of H13CN, H13CO+, HCN, HCO+ (1-0) | 10, 5, 29, 19 | not stated | K km/s pc^2 (paper writes K km^-1 pc^2) | 10 | The line luminosity of the J=1-0 transitions of H$^{13}$CN, H$^{13}$CO$^+$, HCN and HCO$^+$ of the G9.62+0.19 clump are 10, 5, 29 and 19 K km$^{-1}$ pc$^2$, respectively. |
| L'mol-to-M_cores conversion factors for H13CN, H13CO+, HCN, HCO+ (1-0) | about 40, 80, 14, 21 | not stated | Msun (K km/s pc^2)^-1 | 10 | Therefore, the conversion factors L$^{\prime}_{mol}$-to-M$_{cores}$ in G9.62+0.19 are about 40, 80, 14, and 21 |

## Qualitative findings

- H13CN, HC3N, SO and CH3OH reveal the dense cores and filament and resemble the 3 mm continuum  
  > "SO, CH$_3$OH, H$^{13}$CN and HC$_3$N show similar morphologies in their spatial distributions and reveal well the dense cores." (abstract)
- Hii region B has carved a cavity in the molecular clump and shows velocity gradients indicating expansion  
  > "indicating that the Hii region "B" is expanding into its surrounding molecular gas and is reshaping its natal clump" (Extended gas emission)
- CCH-to-H13CO+ and H13CN-to-H13CO+ ratios enhanced at the Hii region/filament interface, interpreted as PDR  
  > "The enhanced CCH-to-H$^{13}$CO$^+$ intensity ratio is likely caused by the PDR of the Hii region “B"." (Tracers for photodissociation regions)

## Claim tuples

- H: Do the commonly used dense-gas tracers CS 2-1, HCN 1-0 and HCO+ 1-0 trace dense structures in a bound clump? | E: Compared ACA total line flux with 12-m flux inside the continuum-defined filament, plus PCA and HOG comparison of the maps | R: Only 17-23% of the HCN, CS and HCO+ flux (and CCH 23%) comes from the dense filament; PCA/HOG place them with extended gas | F: These lines mostly trace extended low-density gas, not dense cores, in G9.62+0.19 | **supported**
- H: Which tracers best follow dense cores and filaments? | E: PCA and HOG relative to the 3 mm continuum | R: SO, CH3OH, H13CN and HC3N group together and align with the continuum (HC3N highest) | F: These four lines are good dense-core and filament tracers | **supported**
- H: What produces the widespread narrow SiO emission? | E: Gaussian fits of SiO spectra at nine positions and Moment 2 map | R: Narrow components (2-6 km/s) away from outflows; positions 7 and 8 show a ~5 km/s projected velocity difference | F: Slow shocks from large-scale colliding flows or Hii regions are the likely cause (inferred, not tested directly) | **partially**
- H: Does stellar feedback from the Hii region B reshape the natal clump? | E: Moment 0/1 maps of CCH, H13CO+, H13CN, SO, HC3N and SiO around region B | R: Cavity in molecular emission, SW-NE velocity gradient with more redshifted gas near B, low-velocity SiO around the Hii regions | F: Expansion of Hii region B reshapes the clump and may account for sequential high-mass star formation | **supported**
- H: Is the 3 mm continuum of the Hii regions dominated by free-free emission? | E: H40alpha line-to-continuum ratio with Te ~6760 K | R: Free-free is 359 of 437 mJy (B), 32 of 32.6 mJy (MM1/C) and 73 of 98.8 mJy (MM11/D) | F: Continuum of B, MM1/C and MM11/D is dominated by free-free; other sources negligible | **supported**

## Reasoning

- Why this data: ALMA needed to separate cores from filaments in distant clumps at <0.1 pc, which needs <2'' resolution  
  > "Only with ALMA, such a systemic high-resolution observational study is possible." (The role of filaments in star formation)
- Why this method: PCA and HOG used to quantify similarities and differences in the spatial distribution of tracers  
  > "we could figure out the best tracers for different structures inside molecular clouds, e.g., filaments, dense cores and extended cloud envelopes." (Similarities and differences in the spatial distributions of gas tracers)
- Alternative: ACA and 12-m data combination (feather) was tested but not used; proper combination deferred to a later paper  
  > "Hence, in this paper, the ACA data and 12-m array data were not combined for the case study of G9.62+0.19" (ALMA Observations)
- Alternative: FellWalker with larger minimum pixel numbers (16, 25) gave unchanged results  
  > "We also tested FellWalker with larger minimum number (16 and 25) of contiguous pixels and found that the results were not changed." (Filaments and dense cores)
- How they decided it was enough: 12-m data alone judged sufficient for the tracer-distribution analysis  
  > "The 12-m array data alone are good enough for this purpose." (ALMA Observations)
- Limitation (authors): Combined data still lack zero-spacing (Total Power) information, so missing flux remains  
  > "The combined data, however, also suffer a non trivial missing flux problem without zero-spacing information from Total-Power (TP) observations." (ALMA Observations)
- Limitation (authors): No cm-wavelength continuum for all targets to remove free-free; electron temperature uncertain  
  > "Higher electron temperature will lead to higher free-free emission contributions." (Filaments and dense cores)
- Limitation (authors): Analysis applies only to G9.62+0.19  
  > "is only applicable to this particular source." (The sample of ATOMS)
- Caveat (inferred, ours): Single source case study: the dense-gas-tracer conclusions (<25% from filament) are not demonstrated for the 146-source sample
- Caveat (inferred, ours): Flux ratio uses a 2D Gaussian ACA total versus a 12-m sum in a continuum-defined mask; differing missing-flux and geometry may bias the ratios
- Caveat (inferred, ours): Filament mask is defined from the continuum, which contains free-free emission in parts, and the ratio depends on the 1% contour choice
- Caveat (inferred, ours): No uncertainties are given for ratios, HOG statistics, luminosities and conversion factors
- Caveat (inferred, ours): Optical depth of HCN, HCO+ and CS is argued qualitatively, not measured in this paper
- Caveat (inferred, ours): Shock origin of narrow SiO is argued from kinematics only

## Reproducibility

- Data public (paper): _not stated_
- Products in archive: _not stated_
- Missing: tclean imaging parameters and cube/continuum definitions
- Missing: Calibration route and product versions
- Missing: Masks and apertures for filament flux sums and spectra
- Missing: HOG and PCA preprocessing details (common beam, regions, gradient kernel)
- Missing: Free-free calculation formula and inputs
- Data volume (inferred): G9.62+0.19 alone (two ACA executions plus one 12-m execution, 8 SPWs): roughly tens of GB raw; full 146-source survey several TB
- Score (inferred): 3/5, Project code, CASA version, array setup, line list, extraction thresholds and many numeric results are given, but imaging parameters, masks and the HOG/PCA preprocessing are not, and public availability of the data is not stated.
- Rediscovery candidate: no, Imaging recipe and analysis settings are too incomplete to redo, and data availability is not stated in the paper.

## Links

- Method: (cite: Soler2019) (HOG analysis method and statistic definitions)
- Method: (cite: Berry2007; Berry2015) (FellWalker source extraction)
- Method: (cite: Moller2017) (XCLASS line identification and modelling)
- Method: (cite: McMullin2007) (CASA software)
- Companion: (cite: Liu2017) (earlier ALMA study of G9.62+0.19 whose core properties and outflows are reused)
- Companion: (cite: Liu2020) (companion work on star formation scaling relations with the ATOMS ACA data)
- Companion: Wang et al. 2020, in preparation (ACA plus 12-m data combination)
- Companion: Peng, Y.-P. et al., 2020, in preparation (detailed chemical analysis of G9.62+0.19)
- Related: MALT90
- Related: Orion B
- Related: EMPIRE
- Related: ALMA_IMF
- Related: ALMAGAL

## Checks

```json
{
 "quotes": 151,
 "quotes_ok": 151,
 "quote_pass_rate": 1.0,
 "quotes_too_long": 0,
 "unsupported_facts": 0,
 "project_codes": 1,
 "codes_not_in_text": [],
 "codes_not_in_obscore": [],
 "obscore_codes_not_in_card": [],
 "codes_printed_but_missing": [],
 "numeric_results": 22,
 "numeric_problems": 0,
 "fill": {
  "facts": 110,
  "stated": 85,
  "rate": 0.773
 },
 "evidence_ok": true
}
```
