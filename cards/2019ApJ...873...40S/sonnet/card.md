# ALMA CO Observations of Supernova Remnant N63A in the Large Magellanic Cloud: Discovery of Dense Molecular Clouds Embedded within Shock-ionized and Photoionized Nebulae

`2019ApJ...873...40S` | The Astrophysical Journal 2019 | first author: Sano, H. | arXiv: 1809.02481 | DOI: 10.3847/1538-4357/ab02fd

Card schema 1.0 | model claude-sonnet-5-5 | depth full | type observational_alma_primary

## Science

- Fields: star_formation, milky_way_ism
- Question: Are dense molecular clouds associated with the shock-ionized and photoionized optical nebulae of LMC SNR N63A, and what do they imply for shock-cloud interaction, X-ray absorption and cosmic-ray energy?  
  > "In the present paper, we show the first detection of dense molecular clouds associated with the optical nebula in N63A" (1 Introduction)
- Target **SNR N63A (LMC)**: coordinates ALMA mosaic center ~ (05h35m46.37s, -66d02m04.8s) J2000  
  > "whose size is $81'' \times 67''$ or $\sim$18 pc in diameter assuming a distance of 50 kpc" (1 Introduction); z/distance ~50 kpc (LMC)  
  > "whose size is $81'' \times 67''$ or $\sim$18 pc in diameter assuming a distance of 50 kpc" (1 Introduction); distance from literature (Dickel 1993; Warren 2003; Bozzetto 2017)  
  > "whose size is $81'' \times 67''$ or $\sim$18 pc in diameter assuming a distance of 50 kpc" (1 Introduction)

## Data provenance

- ALMA projects: 2015.1.01130.S
- bands: Band 3 (86–116 GHz)  
  > "using ALMA Band 3 (86–116 GHz) as a Cycle 3 project $\#$2015.1.01130.S" (2.1 CO)
- frequencies and spectral setup: bandwidth 58.59 MHz, 152.5 km/s velocity coverage, dual polarization  
  > "The correlator was set up in dual polarization mode with a bandwidth of 58.59 MHz, corresponding to the velocity coverage of 152.5 km s$^{-1}$." (2.1 CO)
- continuum bandwidth: _not stated_
- arrays: 12-m array, 38 antennas, mosaic of 100''x100''  
  > "The observations were conducted by using 38 antennas of the 12-m array." (2.1 CO)
- configurations: _not stated_
- baselines: 13.7–1551.1 m (4.6–596.0 kλ)  
  > "The baseline length ranges from 13.7 to 1551.1 m, corresponding to *u-v* distances from 4.6 to 596.0 $k\lambda$." (2.1 CO)
- angular resolution: 1.93'' x 1.71'', PA 66.6 deg (~0.4 pc)  
  > "The beam size of final datsets is $1.93\ensuremath{''} \times 1.71\ensuremath{''}$ with a position angle of $66.6\ensuremath{^\circ}$" (2.1 CO)
- max recoverable scale: _not stated_
- sensitivity: ~0.84 K at 0.4 km/s  
  > "Typical noise fluctuation is $\sim$0.84 K at a velocity resolution of 0.4 km s$^{-1}$." (2.1 CO)
- time on source: _not stated_
- observing dates: 31 January and 27 August 2016  
  > "carried out in 31 January and 27 August 2016 using ALMA Band 3" (2.1 CO)
- pi or archival as stated: _not stated_
- Line: 12CO J=1-0 (ALMA) (not stated)
- Line: 12CO J=3-2 (ASTE) (not stated)
- Other facility **ASTE**: 12CO(3-2) large-scale map, 3'x3', beam ~25''  
  > "After applying two-dimensional Gaussian smoothing, the final beam size is to be $\sim$$25''$." (2.1 CO)
- Other facility **Chandra ACIS-S (ObsID 777)**: archival X-ray images and spectra, 43.4 ks  
  > "The total effective exposure time is 43.4 ks." (2.2 X-rays)
- Other facility **ATCA**: archival radio continuum and polarisation images  
  > "We make use of archival Australia Telescope Compact Array (ATCA) data obtained from the Australia Telescope Online Archive (ATOA)." (2.3 Radio Continuum)
- Other facility **HST WFPC2**: Halpha, [S II], [O III] images  
  > "The observations were carried out using the F656N (H$\alpha$), F673N (\[S ii\]), and F502N (\[O iii\]) filters" (2.4 Other wavelengths)
- Other facility **Mopra**: 12CO(1-0) used to estimate ALMA missing flux  
  > "To estimate the missing flux, we used the $^{12}$CO($J$ = 1–0) datasets obtained with Mopra" (2.1 CO)
- External data: HI data from ATCA+Parkes, ~1' resolution  
  > "We also use the archived Hi data obtained with the Australia Telescope Compact Array (ATCA) & the Parkes radio telescope" (2.4 Other wavelengths) [from (cite: 2003ApJS..148..473K)]
- External data: CO-to-H2 conversion factor X = 7.0e20 cm-2 (K km/s)-1  
  > "We used the conversion factor $X = 7.0 \times 10^{20}$ cm$^{-2}$ (K km s$^{-1}$$)^{-1}$ (cite: 2008ApJS..178...56F)." (3.2 Detailed CO Distribution with ALMA) [from (cite: 2008ApJS..178...56F)]
- External data: Gamma-ray flux 1–10 GeV from Fermi-LAT  
  > "The gamma-ray flux ($E$: 1–10 GeV) was estimated to be 6–$12 \times 10^{-7}$ MeV cm$^{-2}$ s$^{-1}$" (4.3) [from (cite: 2018Ap&SS.363..144C)]
- External data: LMC elemental abundances  
  > "O = 0.21, Ne = 0.28, Mg = 0.33, Si = 0.69, Fe = 0.35; (cite: 2016A&A...585A.162M)" (3.3) [from (cite: 2016A&A...585A.162M); (cite: Russell1992)]

## Processing

### Calibration

- pipeline or manual: CASA calibration; pipeline vs manual not stated  
  > "The data reduction including the calibration was made by the Common Astronomy Software Application (cite: 2007ASPC..376..127M) package version 5.1.0." (2.1 CO)
- casa version: CASA 5.1.0  
  > "package version 5.1.0" (2.1 CO)
- pipeline version: _not stated_
- archive products used as is: _not stated_
- flux calibrator: _not stated_
- flux scale uncertainty: _not stated_
- self calibration: _not stated_

### Imaging

- task: _not stated_
- deconvolver: multiscale CLEAN in CASA  
  > "We utilized the multiscale CLEAN algorithm implemented in the CASA package" (2.1 CO)
- weighting robust: _not stated_
- uv taper: _not stated_
- cell size: _not stated_
- image size: _not stated_
- masking: _not stated_
- multiscale scales: _not stated_
- continuum subtraction: _not stated_
- line free channels: _not stated_
- primary beam correction: _not stated_
- array combination: 12-m only; missing flux ~10% or less versus Mopra, deemed negligible  
  > "We obtain the missing flux of $\sim$$10\%$ or less, and hence the missing flux is considered to be negligible." (2.1 CO)
- smoothing: _not stated_
- final beam: 1.93'' x 1.71'', PA 66.6 deg  
  > "The beam size of final datsets is $1.93\ensuremath{''} \times 1.71\ensuremath{''}$" (2.1 CO)
- final rms: ~0.84 K at 0.4 km/s  
  > "Typical noise fluctuation is $\sim$0.84 K at a velocity resolution of 0.4 km s$^{-1}$." (2.1 CO)

### Inherited from earlier work

- X-ray spectral modelling approach (two-component NEI) following N49 analyses  
  > "Following their approach, we tried the two-component NEI model" (3.3) [from (cite: 2003ApJ...586..210P; 2012ApJ...748..117P)]
- Initial NEI fit of NE spectrum following earlier N63A X-ray study  
  > "Following the previous X-ray study in N63A (cite: 2003ApJ...583..260W), we first fitted the NE spectrum" (3.3) [from (cite: 2003ApJ...583..260W)]

### Not stated but needed to reproduce (our reading)

- tclean/CLEAN parameters (robust, scales, threshold, mask, cell, image size)
- Spectral window layout and continuum handling for the CO(1-0) cube
- CASA calibration procedure (pipeline vs manual) and calibrator assignment clarity
- Cloud identification and Gaussian fitting procedure details
- Extraction region definitions for X-ray spectra
- How the 5 sigma contour was defined (rms in integrated intensity)

## Analysis recipe

1. **Image ALMA CO(1-0) and ASTE CO(3-2)**: CASA multiscale CLEAN; ASTE OTF with Gaussian smoothing  
  > "We utilized the multiscale CLEAN algorithm implemented in the CASA package" (2.1 CO)
   - software: CASA
   - fitting: _not stated_
   - validation: missing flux vs Mopra ~10% or less  
  > "We obtain the missing flux of $\sim$$10\%$ or less" (2.1 CO)
2. **Derive molecular cloud masses**: M = mH mu Omega D^2 sum N(H2), N(H2)=X W(CO), for regions above ~5 sigma  
  > "The physical properties of GMCs are estimated for the regions that are significantly detected by CO with a $\sim$5$\sigma$ or higher." (3.2)
   - parameter: X = 7.0e20 cm-2 (K km/s)-1; mu = 2.72; D ~50 kpc  
  > "$\mu = 2.72$ is the mean molecular weight relative to atomic hydrogen" (3.2)
   - fitting: Gaussian fitting for cloud properties  
  > "Cols. (2–7): Properties of CO emission obtained by Gaussian fitting." (Table 1)
   - validation: _not stated_
3. **Ionized gas density from radio continuum**: Brightness temperature -> optical depth -> emission measure -> n_p  
  > "We estimate the number density of ionized protons $n_\mathrm{p}$ using the radio continuum data and following equation" (3.2)
   - software: MIRIAD
   - parameter: L1~5 pc, Te=14743 K (shock-ionized); L1~1 pc, Te=14620 K (photoionized)  
  > "assuming $L_1 \sim$5 pc and $T_\mathrm{e} = 14743$ K for the shock-ionized lobe" (3.2)
   - fitting: _not stated_
   - validation: compared with X-ray (~250 cm-3) and optical (~50–300 cm-3) estimates  
  > "These values are roughly consistent with estimates of $\sim$250 cm$^{-3}$ by the X-ray spectroscopy" (3.2)
4. **X-ray spectral fitting for absorbing column**: XSPEC fits to Chandra spectra of NE, W, SE regions with CIE+NEI, +PL or +2NEI models  
  > "We applied the same CIE+NEI model as NE to the W and SE spectra." (3.3)
   - software: CIAO, XSPEC, HEASOFT
   - parameter: 0.4–6.0 keV, 90% errors, NH,MW fixed 6.0e20, TBabs  
  > "We fit the spectrum in the energy band form 0.4–6.0 keV and the errors of model fit are quoted at 90% confidence levels." (2.2 X-rays)
   - fitting: chi-square minimisation; F-test between models  
  > "this improvement is not statistically significant with a F-test probability of 0.097" (3.3)
   - validation: _not stated_
5. **Compare X-ray absorption with total ISM column**: N_H(H2+HI) = 2N(H2)+N_H(HI), W(HI) assumed 300–500 K km/s  
  > "Then, we assume $W$(Hi) = 300–500 K km s$^{-1}$ of the SNR from its surroundings." (3.4)
   - fitting: _not stated_
   - validation: _not stated_
6. **Cosmic-ray proton energy**: Wp ~ t_pp x L_gamma with n = ionized + neutral atomic ISM density  
  > "The total energy of cosmic-ray protons is then estimated to be $\sim$0.3–$1.4 \times 10^{49}$ erg" (4.3)
   - fitting: _not stated_
   - validation: _not stated_

## Software

- **CASA** 5.1.0: ALMA calibration and multiscale CLEAN imaging  
  > "package version 5.1.0" (2.1 CO)
- **CIAO** 4.10: Chandra reprocessing, imaging, spectra  
  > "software version 4.10 with CALDB 4.7.8" (2.2 X-rays)
- **XSPEC** 12.10.0c: X-ray spectral fitting  
  > "including spectral fitting with XSPEC (version 12.10.0c)" (2.2 X-rays)
- **MIRIAD** : ATCA reduction and imaging  
  > "Data reduction and imaging were accomplished by using MIRIAD" (2.3 Radio Continuum)
- **KARMA** : ATCA imaging/display  
  > "MIRIAD[^1] (cite: 1995ASPC...77..433S) and KARMA[^2]" (2.3 Radio Continuum)

## Numeric results

| quantity | value | uncertainty | units | step | quote |
|---|---|---|---|---|---|
| Total molecular cloud mass, shock-ionized region (G–K) | ~800 | not stated | Msun | 2 | $\sim$800 $M_{\ensuremath{\odot}}$ for the shock-ionized region (G–K) |
| Total molecular cloud mass, photoionized region (A–F) | ~1700 | not stated | Msun | 2 | $\sim$1700 $M_{\ensuremath{\odot}}$ for the photoionized region (A–F) |
| GMC masses (NE, E, W) | ~6400, ~3600, ~2600 | not stated | Msun | 2 | $\sim$6400 $M_{\ensuremath{\odot}}$ for the NE cloud, $\sim$3600 $M_{\ensuremath{\odot}}$ for the E cloud |
| Ionized proton density, shock-ionized / photoionized | 280±110 / 560±100 | as given | cm-3 | 3 | $\sim$$280 \pm 110$ cm$^{-3}$ for the shock-ionized region and $\sim$$560 \pm 100$ cm$^{-3}$ for the photoionized region |
| X-ray absorbing column N_H,LMC (NE, SE, W) | (1.5–2.4), (4.7–6.0), (1.9–2.7) e21 | 90% range | cm-2 | 4 | (1.5–2.4$) \times 10^{21}~\rm cm^{-2}$ for the NE region, (4.7–6.0$) \times 10^{21}~\rm cm^{-2}$ for the SE region |
| Total ISM proton column (NE, SE, W) | ~3e21, ~7e21, ~3e22 | not stated | cm-2 | 5 | $\sim$$3 \times 10^{21}$ cm$^{-2}$ for the NE region, $\sim$$7 \times10^{21}$ cm$^{-2}$ for the SE region |
| Total ISM proton density | 190±90 | ±90 | cm-3 | 6 | the total ISM proton density of $\sim$$190 \pm 90$ cm$^{-3}$ |
| Cosmic-ray proton energy | ~0.3–1.4e49 | range | erg | 6 | The total energy of cosmic-ray protons is then estimated to be $\sim$0.3–$1.4 \times 10^{49}$ erg |

## Qualitative findings

- Clumpy dense CO clouds are embedded in both shock-ionized and photoionized lobes; clouds A, B, D coincide with an optical dark lane.  
  > "The densest molecular clouds, named A, B, and D, show a good spatial correspondence with the optical dark lane" (3.2)

## Claim tuples

- H: Dense molecular clouds exist within the optical nebula of N63A | E: ALMA 12CO(1-0) mosaic compared with HST, Chandra, ATCA | R: Eleven clouds A–K, ~800 Msun (shock-ionized) and ~1700 Msun (photoionized) | F: First detection of dense molecular clouds embedded in the optical nebula | **supported**
- H: Clouds have been engulfed by shocks | E: Compare X-ray absorbing column with total ISM proton column | R: X-ray columns ~1.5–15 times lower | F: X-rays are produced in front of the clouds; clouds engulfed but survive | **supported**
- H: Hard X-rays in SE arise from shock-cloud interaction | E: Fit SE spectrum with PL or 2NEI models | R: Both fit comparably (F-test p=0.097) | F: Cannot discriminate synchrotron from high-T plasma | **partially**

## Reasoning

- Why this data: _not stated_
- Why this method: _not stated_
- Alternative: Two-component plasma model rejected for SE due to residuals above 4 keV  
  > "hence, a two-component plasma model is rejected because the residuals left above 4 keV band" (3.3)
- How they decided it was enough: _not stated_
- Limitation (authors): HI column cannot be derived directly due to strong absorption; assumed from surroundings  
  > "it is difficult to derive both the $N_\mathrm{H}$(Hi) and $W$(Hi) owing to the strong absorption of Hi" (3.4)
- Caveat (inferred, ours): Single CO-to-H2 factor from literature applied to dense LMC clumps
- Caveat (inferred, ours): Assumed line-of-sight depths for density estimates
- Caveat (inferred, ours): Hard X-ray origin degenerate

## Reproducibility

- Data public (paper): ALMA, Chandra, ATCA archival data cited  
  > "This paper makes use of the following ALMA data: ADS/JAO.ALMA $\#$2015.1.01130.S." (Acknowledgments)
- Products in archive: _not stated_
- Missing: CLEAN parameters
- Missing: region definitions
- Missing: cloud identification details
- Data volume (inferred): ~10–50 GB for ALMA plus Chandra/ATCA archival
- Score (inferred): 3/5, Public data and clear mass equations, but imaging parameters are largely unspecified.
- Rediscovery candidate: no, Imaging recipe incomplete and multi-facility analysis needed.

## Links

- Companion: (cite: 2003ApJ...583..260W) (Previous Chandra analysis of N63A)

## Checks

```json
{
 "quotes": 65,
 "quotes_ok": 65,
 "quote_pass_rate": 1.0,
 "quotes_too_long": 0,
 "unsupported_facts": 0,
 "project_codes": 1,
 "codes_not_in_text": [],
 "codes_not_in_obscore": [],
 "obscore_codes_not_in_card": [],
 "codes_printed_but_missing": [],
 "numeric_results": 8,
 "numeric_problems": 0,
 "fill": {
  "facts": 83,
  "stated": 50,
  "rate": 0.602
 },
 "evidence_ok": true
}
```
