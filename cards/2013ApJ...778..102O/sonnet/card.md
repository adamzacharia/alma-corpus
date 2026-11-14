# An Intensely Star-forming Galaxy at z ~ 7 with Low Dust and Metal Content Revealed by Deep ALMA and HST Observations

`2013ApJ...778..102O` | The Astrophysical Journal 2013 | first author: Ouchi, Masami | arXiv: 1306.3572 | DOI: 10.1088/0004-637X/778/2/102

Card schema 1.0 | model claude-sonnet-5-5 | depth full | type observational_alma_primary

## Science

- Fields: high_z_galaxies
- Question: Does the z=6.595 galaxy Himiko contain detectable cold dust continuum and [CII] 158um emission, and what do these limits plus HST/Spitzer data imply for its dust, metallicity, morphology and Lya nebula?  
  > "We seek to use the cold dust continuum and measures from ALMA to understand its dust content and gas phase metallicity." (1 Introduction)
- Target **Himiko**: coordinates _not stated_; z/distance z=6.595  
  > "We targeted Himiko’s line of rest-frame 1900.54 GHz (157.74$\mu$m) which is redshifted to 250.24 GHz (1.198mm) at a redshift of $z_{\rm Ly\alpha}=6.595$." (2.1 ALMA); distance from Lya redshift, Keck/DEIMOS spectroscopy (Ouchi et al. 2009a)  
  > "We targeted Himiko’s line of rest-frame 1900.54 GHz (157.74$\mu$m) which is redshifted to 250.24 GHz (1.198mm) at a redshift of $z_{\rm Ly\alpha}=6.595$." (2.1 ALMA)

## Data provenance

- ALMA projects: 2011.0.00115.S
- bands: Band 6  
  > "we carried out deep ALMA Band 6 observations in 2012 July 15, 18, 28, and 31" (2.1 ALMA)
- frequencies and spectral setup: 4 spectral windows centred 250.24 and 252.11 GHz (LSB), 265.90 and 267.78 GHz (USB), 1875 MHz bandwidth each  
  > "set the central frequency of the 4 spectral windows are 250.24 and 252.11 GHz in LSB, and 265.90 and 267.78 GHz in USB with a bandwidth of 1875 MHz" (2.1 ALMA)
- continuum bandwidth: 19.417 GHz total, 7.5 GHz sampled  
  > "over the the total bandwidth of $19.417$ GHz whose $7.5$ GHz is sampled" (2.1 ALMA)
- arrays: 16 12m antennas  
  > "with 16 12m-antenna array under the the extended configuration of 36-400m baseline" (2.1 ALMA)
- configurations: _not stated_
- baselines: 36-400 m  
  > "with 16 12m-antenna array under the the extended configuration of 36-400m baseline" (2.1 ALMA)
- angular resolution: 0.82 x 0.58 arcsec, PA 79.5 deg  
  > "The FWHM beam size of the final image is $0''.82 \times 0''.58$ with a position angle of $79^{\circ}.5$." (2.1 ALMA)
- max recoverable scale: _not stated_
- sensitivity: continuum 17.4 uJy/beam; line 83.3 uJy/beam per 200 km/s channel  
  > "259.007 | 250.239 | 17.4 | 83.3 | $<52.1$ | $<250.0$ | $<8.0$ | $<5.4$" (Table 1)
- time on source: 3.17 hours  
  > "The total on-source integration time was 3.17 hours." (2.1 ALMA)
- observing dates: 2012 July 15, 18, 28, 31  
  > "in 2012 July 15, 18, 28, and 31" (2.1 ALMA)
- pi or archival as stated: _not stated_
- Line: [CII] 158 um (1900.54 GHz)
- Other facility **HST/WFC3-IR**: F098M, J125, H160 imaging for morphology, SED and Lya mapping  
  > "We carried out deep *HST*/WFC3-IR broad-band ($J_{125}$ and $H_{160}$)" (2.2 HST)
- Other facility **Spitzer/IRAC SEDS**: 3.6 and 4.5 um photometry  
  > "we use the very deep *Spitzer*/IRAC SEDS data" (2.3 Spitzer)
- External data: Optical, SpUDS Spitzer and ground-based photometry and earlier Lya properties of Himiko  
  > "$^{3}$ Measurements obtained in (cite: ouchi2009a)." (Table 3) [from (cite: ouchi2009a)]
- External data: local [CII]-SFR scaling relation  
  > "the correlation with the star formation rate (SFR) (cite: delooze2011)" (3.2 ISM metallicity) [from (cite: delooze2011)]

## Processing

### Calibration

- pipeline or manual: Reduced with CASA; details not given  
  > "Our data were reduced with Common Astronomy Software Applications (CASA) package." (2.1 ALMA)
- casa version: _not stated_
- pipeline version: _not stated_
- archive products used as is: _not stated_
- flux calibrator: Neptune and Callisto (flux); 3c454.3, J0423-013 bandpass; J0217+017 phase  
  > "The absolute flux scale was established by observations of Neptune and Callisto." (2.1 ALMA)
- flux scale uncertainty: _not stated_
- self calibration: _not stated_

### Imaging

- task: _not stated_
- deconvolver: _not stated_
- weighting robust: _not stated_
- uv taper: _not stated_
- cell size: _not stated_
- image size: _not stated_
- masking: _not stated_
- multiscale scales: _not stated_
- continuum subtraction: _not stated_
- line free channels: continuum averaged over 249.30-253.05 GHz and 264.96-268.71 GHz  
  > "We averaged fluxes over the two spectral windows of LSB (249.30-253.05 GHz or 1.203-1.185mm) and USB (264.96-268.71 GHz or 1.131-1.116mm)" (2.1 ALMA)
- primary beam correction: _not stated_
- array combination: _not stated_
- smoothing: rebinned to 166 MHz (200 km/s)  
  > "We rebin our data to a resolution of 166 MHz (200 km$^{-1}$)." (2.1 ALMA)
- final beam: 0.82 x 0.58 arcsec  
  > "The FWHM beam size of the final image is $0''.82 \times 0''.58$" (2.1 ALMA)
- final rms: 17.4 uJy/beam continuum; 83.3 uJy/beam line  
  > "The $1\sigma$ noise of continuum image is $\sigma_{cont}=17.4$ $\mu$Jy beam$^{-1}$" (2.1 ALMA)

### Inherited from earlier work

- SED fitting done in same manner as earlier work  
  > "undertake $\chi^2$ fitting of a range of stellar synthesis models in the same manner as (cite: ono2010b)" (3.3) [from (cite: ono2010b)]
- Nebular emission prescriptions  
  > "following the metallicity-dependent prescriptions presented in (cite: schaerer2009; ono2010b)" (3.3) [from (cite: schaerer2009; ono2010b)]

### Not stated but needed to reproduce (our reading)

- CASA version and calibration/flagging scripts
- imaging task, weighting, cell and image size, cleaning
- how upper limits were converted to luminosity (line width assumed)
- target coordinates
- flux calibration uncertainty
- HST photometry/PSF-matching details beyond what is given

## Analysis recipe

1. **ALMA continuum and line upper limits**: Average line-free channels for continuum; search 600 km/s channel maps at 200 km/s; 3 sigma limits  
  > "We searched for a signal of over 600 km $^{-1}$ around the frequency corresponding to $z_{\rm Ly\alpha}=6.595$." (2.1 ALMA)
   - software: CASA
   - fitting: _not stated_
   - validation: Noise peaks near 3 sigma judged not reliable counterparts; negative pixels nearby  
  > "However, neither of these sources is a reliable counterpart of Himiko." (2.1 ALMA)
2. **FIR luminosity limit**: Optically thin graybody scaled to 1.2mm limit  
  > "Assuming an optically thin graybody of modified blackbody radiation with a dust emissivity power-law spectral index of $\beta_{\rm d}=1.5$ and a dust temperature of $T_d=40$K" (3.1 Far Infrared SED)
   - assumption: beta_d=1.5, T_d=40 K (range 20-40 K considered)  
  > "it is appropriate to consider a range of $T_d\simeq 20-40$ K with $\beta_{\rm d}\simeq 1.5$." (3.1 Far Infrared SED)
   - fitting: _not stated_
   - validation: Varied T_d and beta_d  
  > "For $T_d=25$K and $T_d=60$K, the $3\sigma$ upper limit luminosities in $8-1000\mu$m are $<2.7\times 10^{10}$ and $<3.0\times 10^{11}L_\odot$, respectively." (3.1 Far Infrared SED)
3. **Stellar population SED fitting**: chi2 fitting of Bruzual&Charlot models with Calzetti attenuation, with/without nebular emission, to HST, Spitzer, UKIDSS photometry  
  > "using the stellar synthesis models of (cite: bruzual2003) with dust attenuation formulate given by (cite: calzetti2000)." (3.3)
   - parameter: E(B-V)=0-1, age=1-810 Myr, Z=0.02-1.0 Zsun  
  > "we search for the best-fit model in a parameter space of $E(B-V)=0-1$ and age$=1-810$ Myr" (3.3)
   - assumption: Salpeter IMF 0.1-100 Msun; constant or exponentially decaying SFH  
  > "We adopt Salpeter initial mass function (IMF; (cite: salpeter1955)) with lower and upper mass cutoffs of 0.1 and 100 $M_{\odot}$, respectively." (3.3)
   - fitting: chi2 minimization on grid  
  > "undertake $\chi^2$ fitting of a range of stellar synthesis models in the same manner as (cite: ono2010b) using the stellar synthesis models of (cite: bruzual2003)" (Section 3.3 Improved Physical Properties from the Near-Infrared SED)
   - validation: Reduced chi2 3.1 pure stellar vs 1.6 with nebular  
  > "the best fit has a more satisfactory reduced $\chi^2$, $1.6$" (3.3)
4. **UV slopes of clumps**: beta from J125-H160 colour  
  > "We estimated the UV slope, $\beta$, from the $J_{125}$ and $H_{160}$ photometry" (3.4)
   - fitting: _not stated_
   - validation: compared with LBG average and Raiter models  
  > "we compare $\beta$ and $EW_0$ for the entire Himiko system and the various clumps with the stellar and nebular models of (cite: raiter2010), where Salpeter IMF is assumed." (Section 3.4 UV Spectral Slopes on the Spatially Resolved Images)

## Software

- **CASA** : ALMA data reduction  
  > "Our data were reduced with Common Astronomy Software Applications (CASA) package." (2.1 ALMA)
- **MULTIDRIZZLE/PyRAF** : HST WFC3 image reduction  
  > "The various WFC3 images were reduced with WFC3 and MULTIDRIZZLE packages on PyRAF." (2.2 HST)

## Numeric results

| quantity | value | uncertainty | units | step | quote |
|---|---|---|---|---|---|
| 1.2mm continuum 3 sigma upper limit | <52.1 | not stated | uJy | 1 | $<52.1$ |
| [CII] line 3 sigma limit | <250.0 | not stated | uJy per 200 km/s | 1 | The corresponding $3\sigma$ upper limit for is $250.0\mu$Jy in a channel width of 200 km s$^{-1}$. |
| L_[CII] upper limit | <5.4e7 | not stated | Lsun | 1 | The associated luminosity limit is $<5.4 \times 10^{7} L_\odot$. |
| L_FIR (8-1000um) upper limit | <8.0e10 | not stated | Lsun | 2 | we adopt a conservative $3\sigma$ upper limit of $L_{\rm FIR}<8.0\times 10^{10} L_\odot$ |
| Stellar mass (stellar+nebular) | 1.5e10 | +/-0.2e10 | Msun | 3 | $1.5^{+0.2}_{-0.2} \times 10^{10}$ |
| SFR (SED) | 100 | +/-2 | Msun/yr | 3 | $100\pm 2$ |
| UV slope clump A | -2.84 | 0.32 | dimensionless | 4 | Clump A presents a very blue UV slope, $\beta=-2.84\pm 0.32$. |
| [CII] deficit relative to local relation | ~30 | not stated | factor | 0 | the deficit amounts to a factor $\simeq\times$30 |

## Qualitative findings

- HST reveals three L* clumps, suggesting a triple merger; no lensing or AGN evidence.  
  > "the system comprises 3 bright clumps of starlight surrounded by a vast Ly$\alpha$ nebula" (2.2 HST)

## Claim tuples

- H: Does Himiko have substantial cold dust? | E: ALMA 1.2mm continuum | R: <52.1 uJy, L_FIR<8e10 Lsun | F: Very low dust content | **supported**
- H: Does Himiko follow the local [CII]-SFR relation? | E: [CII] line search | R: L_[CII]<5.4e7 Lsun, factor ~30 below | F: Likely very low metallicity | **supported**
- H: Origin of the Lya nebula | E: HST morphology and Raiter models | R: Three clumps; beta-EW fall on photoionization tracks | F: Star formation in a triple merger powers nebula | **partially**

## Reasoning

- Why this data: _not stated_
- Why this method: _not stated_
- Alternative: Lensing, hidden AGN, single virialized galaxy, cold accretion, shocks all discussed; lensing and AGN rejected.  
  > "Thus, we conclude that Himiko is not a gravitational lensed system." (4.2)
- How they decided it was enough: _not stated_
- Limitation (authors): UL on FIR luminosity depends on assumed T_d and beta_d.  
  > "Note that these upper limits depend upon the assumed dust temperature and $\beta_{\rm d}$." (3.1 Far Infrared SED)
- Caveat (inferred, ours): Non-detections only; conclusions about metallicity depend on model-dependent interpretations
- Caveat (inferred, ours): Weak 2 sigma peak and negative pixels near the target
- Caveat (inferred, ours): SFR from SED depends on assumed dust law and SFH

## Reproducibility

- Data public (paper): ALMA project cited; public status not stated  
  > "This paper makes use of the following ALMA data: ADS/JAO.ALMA#2011.0.00115.S." (Acknowledgments)
- Products in archive: _not stated_
- Missing: CASA version and scripts
- Missing: imaging parameters
- Missing: target coordinates
- Missing: exact SED fitting code
- Data volume (inferred): ~10-50 GB (Cycle 0, 4 spws, 3 h)
- Score (inferred): 3/5, Simple non-detections from Cycle 0 data, but imaging and calibration parameters are largely unstated.
- Rediscovery candidate: no, Imaging recipe incomplete and results are mostly upper limits.

## Links

- Method: (cite: ono2010b) (SED fitting procedure)
- Companion: (cite: ouchi2009a) (Discovery of Himiko with Subaru)
- Related: Subaru UKIDSS/UDS LAE survey
- Related: Spitzer SEDS

## Checks

```json
{
 "quotes": 56,
 "quotes_ok": 56,
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
  "facts": 69,
  "stated": 42,
  "rate": 0.609
 },
 "evidence_ok": true
}
```
