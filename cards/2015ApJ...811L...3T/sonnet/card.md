# SXDF-ALMA 1.5 arcmin<SUP>2</SUP> Deep Survey: A Compact Dusty Star-forming Galaxy at z = 2.5

`2015ApJ...811L...3T` | The Astrophysical Journal Letters 2015 | first author: Tadaki, Ken-ichi | arXiv: 1508.05950 | DOI: 10.1088/2041-8205/811/1/L3

Card schema 1.0 | model claude-sonnet-5-5 | depth full | type observational_alma_primary

## Science

- Fields: high_z_galaxies
- Question: What are the 1.1 mm dust continuum properties, gas fractions and dust sizes of Halpha-selected star-forming galaxies at z~2.2-2.5, and do compact dusty starbursts link to compact quiescent galaxies?  
  > "In this letter, we present 1.1 mm properties of SFGs at $z\sim2$, along with the discovery of a galaxy with an extremely compact, dusty star-forming component." (Introduction)
- Target **NB2315-02**: coordinates 02 17 40.53 -05 13 10.7 (J2000)  
  > "NB2315-02 | 02 17 40.53 | $-$05 13 10.7 | 2.53$\pm$0.02" (Table 1); z/distance z = 2.53±0.02  
  > "NB2315-02 | 02 17 40.53 | $-$05 13 10.7 | 2.53$\pm$0.02" (Table 1); distance from Halpha narrow-band selection  
  > "NB2315-02 | 02 17 40.53 | $-$05 13 10.7 | 2.53$\pm$0.02" (Table 1)
- Target **NB2315-07**: coordinates 02 17 42.67 -05 13 58.4 (J2000)  
  > "NB2315-07 | 02 17 42.67 | $-$05 13 58.4 | 2.53$\pm$0.02" (Table 1); z/distance z = 2.53±0.02  
  > "NB2315-07 | 02 17 42.67 | $-$05 13 58.4 | 2.53$\pm$0.02" (Table 1); distance from Halpha narrow-band selection  
  > "NB2315-07 | 02 17 42.67 | $-$05 13 58.4 | 2.53$\pm$0.02" (Table 1)
- Target **NB2315-12**: coordinates 02 17 41.11 -05 13 15.2 (J2000)  
  > "NB2315-12 | 02 17 41.11 | $-$05 13 15.2 | 2.53$\pm$0.02" (Table 1); z/distance z = 2.53±0.02  
  > "NB2315-12 | 02 17 41.11 | $-$05 13 15.2 | 2.53$\pm$0.02" (Table 1); distance from Halpha narrow-band selection  
  > "NB2315-12 | 02 17 41.11 | $-$05 13 15.2 | 2.53$\pm$0.02" (Table 1)

## Data provenance

- ALMA projects: 2012.1.00756.S
- bands: Band 6 (~1.1 mm)  
  > "The band 6 receivers were used in frequency range of 255–259, 271–275 GHz ($\sim$1.1 mm)." (Sample and Data)
- frequencies and spectral setup: _not stated_
- continuum bandwidth: _not stated_
- arrays: _not stated_
- configurations: _not stated_
- baselines: _not stated_
- angular resolution: 0.53"x0.41" synthesized beam  
  > "The synthesized beamsize and the rms level before the primary beam correction are 0$''$.53$\times$0$''$.41 and 55 $\mu$Jy/beam, respectively." (Sample and Data)
- max recoverable scale: _not stated_
- sensitivity: 55 uJy/beam rms before primary beam correction  
  > "The map reaches a 1$\sigma$ depth of $55~\mu$Jy/beam" (abstract)
- time on source: _not stated_
- observing dates: _not stated_
- pi or archival as stated: _not stated_
- Other facility **HST (CANDELS, 3D-HST)**: High-resolution images and 18-band photometry for SEDs  
  > "where *Hubble Space Telescope (HST)* high resolution images are available" (Introduction)
- Other facility **Subaru**: Halpha narrow-band selected sample  
  > "identified by a H$\alpha$ narrow-band imaging survey with Subaru Telescope" (Introduction)
- Other facility **Herschel PACS**: 160 um detection of NB2315-02 (archival)  
  > "We detect one source NB2315-02 at $S_{160\mu \mathrm{m}}=7.2\pm1.1$ mJy" (Sample and Data)
- External data: 3D-HST photometric catalog (18 bands) used for SED fitting  
  > "using the 3D-HST catalog with photometries at 18 bands" (Sample and Data) [from (cite: 2014ApJS..214...24S)]
- External data: Halpha-selected sample and NB redshifts  
  > "are not included in our sample (cite: 2013ApJ...778..114T)" (Sample and Data) [from (cite: 2013ApJ...778..114T)]
- External data: F160W effective radius of NB2315-07  
  > "effective radius of $R_e=1.43\pm0.03$ kpc at $F160W$-band (cite: 2014ApJ...788...28V)" (Discussion) [from (cite: 2014ApJ...788...28V)]

## Processing

### Calibration

- pipeline or manual: Calibration in CASA (details not given)  
  > "The data calibration are made using the Common Astronomy Software Application package (CASA;" (Sample and Data)
- casa version: _not stated_
- pipeline version: _not stated_
- archive products used as is: _not stated_
- flux calibrator: _not stated_
- flux scale uncertainty: _not stated_
- self calibration: _not stated_

### Imaging

- task: _not stated_
- deconvolver: _not stated_
- weighting robust: natural weighting  
  > "We reconstruct a 1.1 mm continuum map with natural weighting." (Sample and Data)
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
- final beam: 0.53"x0.41"  
  > "0$''$.53$\times$0$''$.41 and 55 $\mu$Jy/beam" (Sample and Data)
- final rms: _not stated_

### Inherited from earlier work

- 2-sigma detection criterion  
  > "We adopt a $2\sigma$ detection criterion in the same manner as (cite: 2014ApJ...783...84S)." (Results) [from (cite: 2014ApJ...783...84S)]
- Survey design and source catalog  
  > "Survey design and source catalog of the ALMA observations are described in detail in Kohno et al. in preparation." (Introduction) [from Kohno et al. in preparation]

### Not stated but needed to reproduce (our reading)

- CASA version and calibration details
- tclean parameters (cell, image size, cleaning threshold, mask)
- Number of ALMA pointings' integration time and array configurations
- uv annuli binning for uvamp
- Dust temperature scaling relation application details

## Analysis recipe

1. **SED fitting**: UVJ colours with EAZY; stellar mass with FAST fitting  
  > "The SED fitting is done using the `FAST` code (cite: 2009ApJ...700..221K)" (Sample and Data)
   - software: EAZY, FAST
   - parameter: minimum e-folding time 300 Myr  
  > "we adopt a minimum $e$-folding time of 300 Myr" (Sample and Data)
   - assumption: Solar metallicity, exponentially declining SFH, Calzetti attenuation, BC03, Chabrier IMF  
  > "with a solar metallicity, exponentially declining star formation histories (SFHs)" (Sample and Data)
   - fitting: _not stated_
   - validation: _not stated_
2. **Measure 1.1 mm fluxes and detections**: Flux in 1.5" apertures; noise from 2000 random apertures; stacking of non-detections  
  > "we measure the flux densities within the 1$''$.5 apertures and estimate the noise from 2000 random apertures" (Results)
   - software: CASA
   - parameter: 2 sigma detection criterion  
  > "We adopt a $2\sigma$ detection criterion" (Results)
   - fitting: _not stated_
   - validation: Spurious detection rate estimated (0.5% at 2.6 sigma)  
  > "The spurious detection rates of 2.6$\sigma$ sources is 0.5%." (Results)
3. **Derive gas masses**: Modified blackbody single-band dust continuum to gas mass  
  > "We estimate the gas mass of our sample using a modified blackbody radiation model" (Gas mass estimates)
   - parameter: kappa_ISM,850um = 4.84e-3 g^-1 cm^2, beta = 1.8  
  > "$\kappa_{\mathrm{ISM, 850\mu m}}=4.84\times10^{-3}$ g$^{-1}$cm$^2$ and $\beta=1.8$ are adopted" (Gas mass estimates)
   - assumption: Dust temperature from Genzel+15 scaling relation  
  > "This scaling relation of dust temperatures is used for better estimates of the rest-frame 850 $\mu$m fluxes" (Gas mass estimates)
   - fitting: _not stated_
   - validation: _not stated_
4. **Measure dust sizes in uv plane**: Visibility amplitudes averaged in uv annuli, fit with circular Gaussian vs point source  
  > "Then, we assume two models, a circular Gaussian component and a point source." (Size measurements of dust emission)
   - software: MIRIAD uvamp, MIRIAD uvmodel
   - fitting: Chi-square fitting; reduced chi2 0.61 vs 5.76 (NB2315-02)  
  > "The gaussian fitting shows reduced chi-square values of 0.61 for NB2315-02 and 1.62 for NB2315-12" (Size measurements of dust emission)
   - validation: Phase calibrator shows constant amplitude (point source)  
  > "The phase calibrator, J0215-0222, shows constant amplitudes as a function of $uv$ distance" (Size measurements of dust emission)

## Software

- **CASA** : Calibration and imaging  
  > "The data calibration are made using the Common Astronomy Software Application package" (Sample and Data)
- **MIRIAD** : uv-plane size fitting (uvamp, uvmodel)  
  > "The `uvamp` task in MIRIAD" (Size measurements of dust emission)
- **EAZY** : Rest-frame UVJ colours  
  > "and the `EAZY` code" (Sample and Data)
- **FAST** : Stellar mass SED fitting  
  > "The SED fitting is done using the `FAST` code" (Sample and Data)
- **UNIMAP** : Herschel PACS map making  
  > "We have also applied UNIMAP" (Sample and Data)

## Numeric results

| quantity | value | uncertainty | units | step | quote |
|---|---|---|---|---|---|
| Size of NB2315-02 dust emission (Re) | 0.66 | +0.11/-0.08 | kpc | 4 | FWHM=0$''$.16$^{+0.03}_{-0.02}$ ($R_e=0.66\pm^{+0.11}_{-0.08}$ kpc) for NB2315-02 |
| SFR surface density NB2315-02 | 126 | +27/-30 | Msun/yr/kpc^2 | 4 | the SFR surface density could be 126$^{+27}_{-30}~M_\odot$ yr$^{-1}$kpc$^{-2}$ |
| Gas fraction NB2315-02 | 44 | +20/-8 | % | 3 | 10.3$^{+1.7}_{-1.5}$ / 44$^{+20}_{-8}$ |
| 1.1 mm flux NB2315-02 | 2.06 | 0.13 | mJy | 2 | 2.06$\pm$0.13 |
| Stacked upper limit for non-detections | <100 | 2 sigma limit | uJy | 2 | gives the $2\sigma$ upper limit of $S_{1.1\mathrm{mm}}<100~\mu$Jy |
| Gas depletion timescale NB2315-02 | 207 | +78/-44 | Myr | 3 | is 207$^{+78}_{-44}$ Myr |

## Qualitative findings

- Detected 1.1 mm SFGs are red and massive; blue main-sequence SFGs are undetected  
  > "The 1.1 mm-detected SFGs are redder in the rest-frame optical and more massive than the non-detected sample" (Detections in 1.1 mm continuum map)

## Claim tuples

- H: Do compact dusty starbursts exist that can build compact stellar cores? | E: uv-plane size fit of 1.1 mm emission for NB2315-02 | R: Re=0.66 kpc, SFR surface density 126 Msun/yr/kpc^2 | F: The starburst could build stellar surface density of compact QGs within ~50 Myr | **supported**
- H: Are main-sequence SFGs detectable at 1.1 mm? | E: Aperture photometry and stacking | R: Upper limits <290 uJy individually, <100 uJy stacked | F: Non-detections explained by uncertain dust properties | **partially**

## Reasoning

- Why this data: _not stated_
- Why this method: _not stated_
- Alternative: Point source model rejected in favour of Gaussian  
  > "Therefore, we adopt the gaussian model which is the same approach as previous studies" (Size measurements of dust emission)
- How they decided it was enough: _not stated_
- Limitation (authors): Gas masses depend on dust opacity, dust-to-gas ratio and temperature assumptions  
  > "although there are uncertainties associated with dust temperature variations" (Gas mass estimates)
- Caveat (inferred, ours): Single-band gas masses rely on calibrated kappa from outlier populations
- Caveat (inferred, ours): Size measured for only two sources with limited S/N
- Caveat (inferred, ours): Marginal 2.6 sigma detection of NB2315-07 drives conclusions

## Reproducibility

- Data public (paper): _not stated_
- Products in archive: _not stated_
- Missing: CASA version and imaging parameters
- Missing: Observation log and configurations
- Missing: Kohno et al. survey paper details
- Data volume (inferred): ~50-100 GB raw for 19 pointings
- Score (inferred): 3/5, Recipe outline is given but imaging and calibration details are sparse and rely on a companion paper.
- Rediscovery candidate: no, Public status is not stated and imaging details are missing.

## Links

- Method: (cite: 2014ApJ...783...84S) (Dust opacity and gas mass method and detection criterion)
- Method: (cite: 2015ApJ...800...20G) (Dust temperature scaling relations)
- Companion: Kohno et al. in preparation (Survey design and source catalog)
- Companion: (cite: 2013ApJ...778..114T) (Halpha narrow-band sample)
- Related: SXDF-UDS-CANDELS
- Related: 3D-HST

## Checks

```json
{
 "quotes": 54,
 "quotes_ok": 54,
 "quote_pass_rate": 1.0,
 "quotes_too_long": 0,
 "unsupported_facts": 0,
 "project_codes": 1,
 "codes_not_in_text": [],
 "codes_not_in_obscore": [],
 "obscore_codes_not_in_card": [],
 "codes_printed_but_missing": [],
 "numeric_results": 6,
 "numeric_problems": 0,
 "fill": {
  "facts": 82,
  "stated": 44,
  "rate": 0.537
 },
 "evidence_ok": true
}
```
