# Extremely Dense Cores Associated with Chandra Sources in Ophiuchus A: Forming Brown Dwarfs Unveiled?

`2018ApJ...866..141K` | The Astrophysical Journal 2018 | first author: Kawabe, Ryohei | arXiv: 1810.00573 | DOI: 10.3847/1538-4357/aae153

Card schema 1.0 | model claude-sonnet-5-5 | depth full | type observational_alma_primary

## Science

- Fields: star_formation
- Question: Are the two compact dust cores SM1-A and Source-X in Oph-A, both with Chandra X-ray counterparts, extremely young protostars or proto-brown dwarfs close to the first hydrostatic core phase?  
  > "Here we propose that these two protostellar candidates are bona fide protostars or proto-brown dwarfs." (Introduction)
- Target **SM1-A**: coordinates 16:26:27.83 -24:23:59.2 (ALMA Cycle-0 field centre, Table 1)  
  > "Recent VLBA observations have provided an accurate distance to the $\rho$ Oph star-forming region (Lynds 1688) of 137 $\pm$ 1.2 pc (cite: ortiz17)." (Introduction); z/distance 137 pc  
  > "Recent VLBA observations have provided an accurate distance to the $\rho$ Oph star-forming region (Lynds 1688) of 137 $\pm$ 1.2 pc (cite: ortiz17)." (Introduction); distance from VLBA parallax (Ortiz-Leon et al. 2017)  
  > "Recent VLBA observations have provided an accurate distance to the $\rho$ Oph star-forming region (Lynds 1688) of 137 $\pm$ 1.2 pc (cite: ortiz17)." (Introduction)
- Target **Source-X**: coordinates _not stated_; z/distance 137 pc  
  > "a dust continuum source (hereafter, referred to as Source-X) located between SM1-A and VLA 1623" (Introduction); distance from VLBA parallax (Ortiz-Leon et al. 2017)  
  > "a dust continuum source (hereafter, referred to as Source-X) located between SM1-A and VLA 1623" (Introduction)

## Data provenance

- ALMA projects: 2011.0.00396.S, 2013.1.01004.S, 2013.1.00839.S
- bands: Band 6 (226 GHz mosaic, 219 GHz) and Band 7 (359/372 GHz)  
  > "We also analyzed ALMA archive data, which were Cycle-0 Band-7 and Cycle-2 Band-6 data" (Observations and Data Analysis)
- frequencies and spectral setup: _not stated_
- continuum bandwidth: _not stated_
- arrays: Mosaic: 12-m Array 150 pointings plus ACA 58 pointings; Band 7: 26 12-m antennas  
  > "using the 12-m Array with 150 pointings and ACA with 58 pointings to cover 2$\ensuremath{'}$ $\times$ 3$\ensuremath{'}$ region of Oph-A" (Cycle-2 Mosaic Observations)
- configurations: _not stated_
- baselines: Band 7: 26-500 m; mosaic uv 12.5-348 kλ (12-m), 8.1-48 kλ (7-m)  
  > "The $uv$ ranges sampled in the 12-m Array and 7-m Array data were 12.5 $-$ 348 k$\lambda$ and 8.1 $-$ 48 k$\lambda$, respectively." (Cycle-2 Mosaic Observations)
- angular resolution: _not stated_
- max recoverable scale: ~3 arcsec for the Cycle-0 Band 7 data  
  > "sensitive to maximum angular scales of $\sim$ $3''$" (Band-7 Observations in Cycle-0)
- sensitivity: _not stated_
- time on source: 2400 s (Cycle-0 Band 7)  
  > "the total on-source integration time was 2400 seconds" (Band-7 Observations in Cycle-0)
- observing dates: Cycle-0: 2012 Aug 24-25; Cycle-2 219 GHz: 2014 Aug 17 (Table 1); mosaic 2015 Mar 01 (Table 1)  
  > "were performed on 2012 August 24$-$25 in ALMA Cycle-0" (Band-7 Observations in Cycle-0)
- pi or archival as stated: Mosaic is the authors' Cycle-2 program; Band 7 and 219 GHz data from archive  
  > "We obtained 219 GHz continuum data from the ALMA archive." (Band-6 Observations in Cycle-2)
- Line: 12CO J=2-1 (230.538000 GHz)
- Line: 13CO J=2-1 (220.398684 GHz)
- Line: C18O J=2-1 (219.560358 GHz)
- Other facility **JVLA 41 GHz**: 7.3 mm continuum of SM1-A  
  > "The 7.3 mm continuum image was made with natural weighting to maximize the signal-to-noise ratio" (JVLA 41 GHz Observations)
- Other facility **Chandra ACIS-I**: X-ray detections; merged 2000 and 2014 data  
  > "We merged the data taken in 2000 and 2014 to improve the signal-to-noise ratios" (Chandra Observations)
- Other facility **SMA**: 870 um continuum and CO  
  > "SM1-A was observed with the SubMillimeter Array (SMA) on 2007 July 29 in its compact-north configuration" (SMA Observations)
- Other facility **Spitzer/Herschel/IRSF**: NIR-FIR photometry and upper limits  
  > "We have also analyzed the recent *Herschel* 70 $\mu$m data from the Herschel Science Archive" (Spitzer IRAC/MIPS Data and Herschel Data)
- External data: 3 mm ALMA detection of Source-X (core No. 10) and its mass/size  
  > "The latter source was recently detected in 3-mm with ALMA by (cite: kirk17) as core No. 10." (Introduction) [from (cite: kirk17)]
- External data: First-core RHD model SEDs and visibilities  
  > "We also compared the 359 GHz and 41 GHz visibility distributions with those expected for the first core model (Tomida et al. 2010)." (Source Size Analysis) [from Tomida et al. 2010]
- External data: Brown dwarf model outflow properties  
  > "Quantities listed here are taken from Machida et al. (2009)" (Table 5) [from (cite: machi09)]
- External data: JVLA 6.6 cm and 4 cm photometry of SM1-A  
  > "JVLA | 40000 | 0.125$\pm$0.056" (Table 3) [from Dzib et al. 2013]

## Processing

### Calibration

- pipeline or manual: Mosaic: CASA pipeline scripts modified (shadowing 7 m to 6 m), then own calibration; Band 7 standard calibration plus phase self-cal  
  > "We modified the scripts prepared by the ALMA observatory in which the shadowing criterion for the bandpass data was reduced from 7 m to 6 m" (Cycle-2 Mosaic Observations)
- casa version: CASA 4.2.2 (Band 7 and 12-m mosaic); 4.5.3 (7-m)  
  > "calibrated and imaged using the CASA pipeline version 4.2.2 and version 4.5.3, respectively" (Cycle-2 Mosaic Observations)
- pipeline version: _not stated_
- archive products used as is: _not stated_
- flux calibrator: Titan (12-m), Mars (7-m); Butler-JPL-Horizons 2012 model  
  > "We used Titan and Mars for the flux calibrations of the 12-m Array and the 7-m Array observations, respectively." (Cycle-2 Mosaic Observations)
- flux scale uncertainty: ~10% for 219 GHz  
  > "Uncertainty of the absolute flux density scale is $\sim$ 10 $\%$." (Band-6 Observations in Cycle-2)
- self calibration: Phase-only self-calibration on Band 7 and 219 GHz data; S/N >600 at 835 um  
  > "Only phase self-calibration was done for the data set." (Band-7 Observations in Cycle-0)

### Imaging

- task: _not stated_
- deconvolver: _not stated_
- weighting robust: natural weighting for Band 7 835 um  
  > "By applying the self-calibaration with natural weighting, we could achieve the rms noise level of 0.39 mJy beam$^{-1}$" (Band-7 Observations in Cycle-0)
- uv taper: _not stated_
- cell size: _not stated_
- image size: _not stated_
- masking: _not stated_
- multiscale scales: _not stated_
- continuum subtraction: Band 7 continuum from summed line-free channels (~256 MHz)  
  > "The line-free channels were summed to form continuum visibility data of $\sim$ 256 MHz in bandwidth each" (Band-7 Observations in Cycle-0)
- line free channels: _not stated_
- primary beam correction: _not stated_
- array combination: 12-m and 7-m data combined for the 226 GHz mosaic  
  > "we present the combined 12-m Array and 7-m Array 1.3-mm continuum image of Oph A" (Cycle-2 Mosaic Observations)
- smoothing: _not stated_
- final beam: 219 GHz: 0.6 x 0.34 arcsec; 226 GHz continuum: 1.4 x 0.92 arcsec  
  > "The obtained beam size is 0$\ensuremath{''}$6 $\times 0.34\ensuremath{''}$" (Band-6 Observations in Cycle-2)
- final rms: 0.39 mJy/beam (359 GHz); 0.084 mJy/beam (219 GHz); 0.024 mJy/beam (226 GHz)  
  > "the rms noise achieved is $\sim$ 0.084 mJy beam$^{-1}$ at the center of the FOV" (Band-6 Observations in Cycle-2)

### Inherited from earlier work

- Mosaic observing parameters and reference position same as Oph B2  
  > "The observation parameters are the same as those of the Oph B2 observations (cite: kama18)." (Cycle-2 Mosaic Observations) [from (cite: kama18)]
- Cycle-0 Band 7 data first published  
  > "observations toward SM1-A were performed on 2012 August 24$-$25 in ALMA Cycle-0 (cite: frie14)" (Band-7 Observations in Cycle-0) [from (cite: frie14)]
- SMA observing details and continuum data  
  > "The continuum data were first published in our previous paper (cite: naka12), which describes the details of the observing parameters." (SMA Observations) [from (cite: naka12)]
- Fixed X-ray plasma temperature and abundance  
  > "The metal abundances and the plasma temperatures were fixed to 0.3 solar and 5 keV, respectively, based on the previously derived values for Young Stellar Objects" (X-ray Properties; N_H and L_X) [from Imanishi et al. 2001]

### Not stated but needed to reproduce (our reading)

- tclean/clean parameters (deconvolver, cell, image size, masks, robust for mosaic)
- self-calibration solution intervals and number of iterations
- line-free channels and velocity ranges for outflow integration
- aperture/Gaussian fitting details for photometry
- how the 12-m and 7-m mosaic were combined (weights)
- unpublished single-dish 12CO/13CO(3-2) data used for tau ~10
- exact Source-X coordinates
- fitting method and uncertainty treatment for the SED fit

## Analysis recipe

1. **Calibrate and image ALMA data**: CASA calibration with phase self-calibration for Band 7 and 219 GHz; combined 12-m+7-m mosaic imaging  
  > "we tried self-calibration for each of the 810 $\mu$m and 835 $\mu$m continuum datasets" (Band-7 Observations in Cycle-0)
   - software: CASA
   - fitting: _not stated_
   - validation: rms of 0.39 mJy/beam close to thermal noise  
  > "which is very close to the theoretical thermal noise expectation" (Band-7 Observations in Cycle-0)
2. **Measure multiwavelength photometry**: Gaussian fitting for ALMA/JVLA fluxes; 3 sigma upper limits in non-detections  
  > "Integrated and peak flux densities for images with ALMA and JVLA were obtained with Gaussian fitting to the sources." (Table 3)
   - software: CASA, MOPEX, IRAF, DAOPHOT
   - fitting: _not stated_
   - validation: _not stated_
3. **Derive source sizes**: Beam deconvolution and Gaussian visibility amplitude fitting  
  > "Another method to determine size is visibility fitting assuming that the source intensity has an axisymmetric Gaussian distribution." (Source Size Analysis)
   - fitting: _not stated_
   - validation: visibility sizes agree with image-domain deconvolved sizes  
  > "The source diameters derived from the visibility analysis agree well with the beam-deconvolved sizes in the image domain at the same frequencies." (Source Size Analysis)
4. **SED fit for Td, tau, beta, mass, luminosity of SM1-A**: Uniform-temperature source model fitted to 7.3 mm and 835 um fluxes plus 24/70 um upper limits; opacity-corrected mass  
  > "gives us $T_{\rm d} = 40$ K, $\beta$ = 1.5 $-$ 2, and $\tau _{41} =$ 0.18" (SED Fit and Derivation of Physical Properties)
   - parameter: radius 21 au, Omega = 2.4e-12 sr, T_bg = 2.7 K  
  > "$\Omega$ is the source solid angle for SM1-A, which is assumed to be 2.4 $\times$ 10$^{-12}$ $sr$" (SED Fit and Derivation of Physical Properties)
   - assumption: kappa = 0.1 (nu/1e12 Hz)^beta cm2/g; 7.3 mm emission is thermal dust with no free-free; D = 137 pc  
  > "The 7.3-mm continuum emission is assumed to arise from the thermal dust emission, without free-free contamination." (SED Fit and Derivation of Physical Properties)
   - fitting: _not stated_
   - validation: mass agrees with Friesen et al. 2014  
  > "This is in good agreement with that of (cite: frie14)." (SED Fit and Derivation of Physical Properties)
5. **Estimate Source-X mass**: Assume Td = 20 K and beta = 1.5-2 instead of modelling  
  > "Instead of modelling, we assume $T_{\rm d}$ = 20 K" (Source-X)
   - assumption: Td = 20 K, beta = 1.5-2  
  > "we assume $\beta=1.5-2$ since the spectral index between 218 GHz and 41 GHz is larger than 3.4" (Source-X)
   - fitting: _not stated_
   - validation: consistent with Kirk et al. 2017 mass given different parameters  
  > "but it is consistent with each other, taking into account the effects of the different parameters" (Source-X)
6. **Outflow mass, dynamical time and mass-loss rate**: LTE CO mass from integrated intensities; dynamical time from length/velocity  
  > "Here, we assumed LTE condition, the CO fractional abundance of $10^{-4}$, and the excitation temperature of 20 K." (SM1-A)
   - assumption: inclination i = 45 deg; tau ~10 for wing  
  > "and the velocity is $3/\sin i$ km s$^{-1}$ ($i$ is measured from the plane of sky) and $i$ = 45$\ensuremath{^\circ}$" (SM1-A)
   - fitting: _not stated_
   - validation: _not stated_
7. **X-ray spectral fit for NH and LX**: APEC thin thermal plasma with WABS absorption on merged Chandra spectra; kT = 5 keV and 0.3 solar fixed  
  > "We fitted the spectra using the thin thermal plasma model (the Astrophysical Plasma Emission Code, Smith et al. 2001)" (X-ray Properties; N_H and L_X)
   - software: CIAO
   - fitting: errors at 90% confidence  
  > "with the errors for them in 90% confidence level" (X-ray Properties; N_H and L_X)
   - validation: _not stated_

## Software

- **CASA** 4.2.2 (also 4.5.3 for 7-m): ALMA calibration and imaging  
  > "Data reduction was conducted on the Common Astronomy Software Applications package (CASA) version 4.2.2." (Band-7 Observations in Cycle-0)
- **MIRIAD** : SMA imaging  
  > "the calibrated visibility data were Fourier-transformed and CLEANed with MIRIAD" (SMA Observations)
- **MIR** : SMA calibration  
  > "calibrated with an IDL-based reduction package, MIR" (SMA Observations)
- **CIAO** : Chandra data processing  
  > "using the Chandra Interactive Analysis of Observations (CIAO) software" (Chandra Observations)
- **MOPEX** : Spitzer mosaicking  
  > "mosaicing using the MOPEX (MOsaicker and Point source EXtractor) software" (Spitzer IRAC/MIPS Data and Herschel Data)
- **IRAF/DAOPHOT** : NIR reduction and photometry  
  > "Identification and photometry of point sources in all frames were performed with using the DAOPHOT packages in IRAF." (Analysis of J, H, and Ks Band Data)

## Numeric results

| quantity | value | uncertainty | units | step | quote |
|---|---|---|---|---|---|
| SM1-A dust temperature | 40 | not stated | K | 4 | $T_{\rm d} = 40$ K |
| SM1-A optical depth at 41 GHz | 0.18 | not stated | dimensionless | 4 | $\tau _{41} =$ 0.18 |
| SM1-A mass | 0.054-0.27 (text); 0.028-0.14 (Table 4) | range for beta=1.5-2 | Msun | 4 | we estimate to be 0.054$-$0.27 $M_\odot$ for $T_{\rm d} =$ 40 K, $\beta=$ 1.5 $-$ 2, and $D = 137$ pc |
| SM1-A luminosity | 0.035 | not stated | Lsun | 4 | The luminosity of SM1-A calculated so is 0.035 $L_\odot$ |
| Source-X mass | 0.018-0.039 | range | Msun | 5 | yield a mass range of $M=0.018-0.039$ $M_\odot$ |
| SM1-A 12CO(2-1) outflow intensity | 7.34 | 0.28 | Jy km/s | 6 | 7.34 $\pm$ 0.28 |
| SM1-A outflow dynamical time | 434 | not stated | yr | 6 | Dynamical Time / yr / 434 |
| SM1-A NH | 3.0e23 | +2.2/-1.2 e23 (90%) | cm-2 | 7 | $(3.0^{+2.2} _{-1.2}$ $\times 10^{23}$ cm$^{-2}$, $0.75^{+1.0}_{-0.5} \times10^{29}$ erg s$^{-1}$) |
| SM1-A LX (0.5-10 keV) | 0.75e29 | +1.0/-0.5 e29 (90%) | erg/s | 7 | $0.75^{+1.0}_{-0.5} \times10^{29}$ erg s$^{-1}$ |
| SM1-A source diameter at 359 GHz | 0.3 arcsec (41 au) | not stated | arcsec | 3 | 0.3$''$ (= 41 au) and 0.17$''$ (= 23 au) for 359 GHz and 41 GHz |

## Qualitative findings

- Both sources are nearly invisible from NIR to FIR but detected in X-rays; compact CO outflows found for both  
  > "Both sources are very dim in NIR to FIR." (Detection of Compact Cores Associated with Chandra Sources)

## Claim tuples

- H: SM1-A and Source-X are extremely young protostars/proto-BDs near first-core phase | E: SED, size, CO outflow and Chandra analysis | R: Densities ~1e11-12 cm-3, masses ~0.01-0.1 Msun, X-ray detections, compact outflows | F: They are proto-BD or very early protostar candidates consistent with first-core models | **supported**
- H: The sources have outflows with short dynamical times | E: 12CO(2-1) and (3-2) maps | R: Blue-shifted compact CO in SM1-A; faint lobes in Source-X; ~430 yr | F: Ages are short (<~500 yr) | **partially**
- H: The two objects may have been ejected from VLA 1623A binary | E: Travel-time estimate at 3 km/s | R: 4000-8000 yr | F: Consistent with ejection scenario, tentative | **partially**

## Reasoning

- Why this data: _not stated_
- Why this method: Source-X lacks data for SED modelling so assumed Td and beta  
  > "Source-X is lacking data to constrain its physical nature due to its limited detection at 100/219/226 GHz." (Source-X)
- How they decided it was enough: _not stated_
- Limitation (authors): Source-X has too little visibility data for size analysis; Td assumed  
  > "For Source-X, we do not have enough visibility data to do the same analysis as done for SM1-A." (Source Size Analysis)
- Limitation (authors): Lack of redshifted counterpart for SM1-A outflow is puzzling  
  > "The lack of a redshifted counter part is puzzling" (SM1-A)
- Caveat (inferred, ours): Mass depends on assumed opacity law and Td; SM1-A is optically thick at 359 GHz
- Caveat (inferred, ours): Free-free contamination at 41 GHz assumed absent
- Caveat (inferred, ours): Source-X outflow association tentative
- Caveat (inferred, ours): Mass range in text (0.054-0.27) differs from Table/summary (0.028-0.14)
- Caveat (inferred, ours): X-ray fits fix kT and abundance with few counts (23 and 35)

## Reproducibility

- Data public (paper): ALMA data obtained from archive; project codes given  
  > "We obtained 219 GHz continuum data from the ALMA archive." (Band-6 Observations in Cycle-2)
- Products in archive: _not stated_
- Missing: Imaging parameters
- Missing: Self-cal details
- Missing: SED fitting procedure
- Missing: Unpublished single-dish data
- Data volume (inferred): ~100-300 GB for the three ALMA projects (mosaic dominant), plus Chandra/Spitzer
- Score (inferred): 3/5, Data are public and the physical modelling is simple and equation-based, but imaging and calibration details are sparse.
- Rediscovery candidate: no, Imaging recipe is incomplete and several inputs come from other papers or unpublished data.

## Links

- Method: (cite: kama18) (Same Cycle-2 mosaic observing and reduction setup)
- Companion: (cite: frie14) (Earlier Cycle-0 Band 7 analysis of SM1-A)
- Companion: (cite: kirk17) (3 mm ALMA detection of Source-X)
- Related: Oph B2 ALMA mosaic (Kamazaki et al. 2018)

## Checks

```json
{
 "quotes": 82,
 "quotes_ok": 82,
 "quote_pass_rate": 1.0,
 "quotes_too_long": 0,
 "unsupported_facts": 0,
 "project_codes": 3,
 "codes_not_in_text": [],
 "codes_not_in_obscore": [],
 "obscore_codes_not_in_card": [],
 "codes_printed_but_missing": [],
 "numeric_results": 10,
 "numeric_problems": 0,
 "fill": {
  "facts": 92,
  "stated": 62,
  "rate": 0.674
 },
 "evidence_ok": true
}
```
