# Dust in the Reionization Era: ALMA Observations of a z = 8.38 Gravitationally Lensed Galaxy

`2017ApJ...837L..21L` | The Astrophysical Journal Letters 2017 | first author: Laporte, N. | arXiv: 1703.02039 | DOI: 10.3847/2041-8213/aa62aa

Card schema 1.0 | model claude-sonnet-5-5 | depth full | type observational_alma_primary

## Science

- Fields: high_z_galaxies
- Question: Is the ALMA Band 7 continuum and line detection associated with the z=8.38 lensed Y-dropout A2744_YD4, and what dust mass, SFR and stellar mass does it imply?  
  > "The association with the ALMA detection is confirmed by the presence of \[OIII\] 88$\mu$m emission at the same redshift." (abstract)
- Target **A2744_YD4**: coordinates RA=00:14:24.9, DEC=-30:22:56.1 (J2000)  
  > "at RA= 00:14:24.9, DEC=$-$30:22:56.1(2000) first identified by (cite: 2014ApJ...795...93Z)" (2.1 Deep ALMA band 7 observations); z/distance z=8.38 (Lyman alpha); [OIII] z=8.382  
  > "at RA= 00:14:24.9, DEC=$-$30:22:56.1(2000) first identified by (cite: 2014ApJ...795...93Z)" (2.1 Deep ALMA band 7 observations); distance from X-Shooter Lyman alpha line; [OIII] 88um in ALMA  
  > "at RA= 00:14:24.9, DEC=$-$30:22:56.1(2000) first identified by (cite: 2014ApJ...795...93Z)" (2.1 Deep ALMA band 7 observations)

## Data provenance

- ALMA projects: _none stated_
- bands: Band 7 (0.84 mm, 356 GHz)  
  > "centered at 0.84mm ($f_c$=356 GHz)" (2.1 Deep ALMA band 7 observations)
- frequencies and spectral setup: _not stated_
- continuum bandwidth: _not stated_
- arrays: _not stated_
- configurations: _not stated_
- baselines: _not stated_
- angular resolution: _not stated_
- max recoverable scale: _not stated_
- sensitivity: peak 9.9±2.3e-5 Jy/beam, >4.0 sigma; rms over ~2x2 arcmin field  
  > "a peak flux of 9.9$\pm$2.3 $\times$10$^{-5}$ Jy/beam (uncorrected for magnification)" (2.1 Deep ALMA band 7 observations)
- time on source: 2.5 hr  
  > "was observed on July 2016 during 2.5hrs" (2.1 Deep ALMA band 7 observations)
- observing dates: July 2016  
  > "was observed on July 2016 during 2.5hrs" (2.1 Deep ALMA band 7 observations)
- pi or archival as stated: PI: Laporte  
  > "(ID 2015.1.00594, PI: Laporte)" (2.1 Deep ALMA band 7 observations)
- Line: [OIII] 88 um (not stated)
- Other facility **HST (ACS, WFC3) Frontier Fields**: Photometry for SED and identification  
  > "we examined the final version of the reduced HST data of Abell 2744 (ACS and WFC3)" (2.1 Deep ALMA band 7 observations)
- Other facility **VLT X-Shooter**: Lyman alpha spectroscopy at z=8.38  
  > "we undertook a spectroscopic campaign using X-Shooter/VLT (ID: 298.A-5012 – PI: Ellis)" (3.1 X-Shooter Observations)
- Other facility **HAWK-I and Spitzer IRAC**: Ks and 3.6/4.5 um photometry  
  > "Deep $K_s$ data is also available from a 29.3 hrs HAWK-I image" (2.2 Other Imaging Data)
- External data: Lens magnification from CATS, Johnson, Merten/Zitrin, GLAFIC models  
  > "We took the average value with error bars corresponding to the standard deviation: $\mu$=1.8$\pm$0.3." (4.1 Magnification) [from (cite: 2014MNRAS.444..268R), (cite: 2014ApJ...797...48J), (cite: 2011MNRAS.417..333M), (cite: 2015ApJ...799...12I)]
- External data: Comparison source A1689-zD1 properties  
  > "M$_{dust}$=4 $^{+4}_{-2} \times$ 10$^{7}$ M$_{\odot}$" (4.2 The Star Formation Rate and Stellar and Dust Masses) [from (cite: 2015Natur.519..327W)]

## Processing

### Calibration

- pipeline or manual: CASA pipeline  
  > "The data was reduced using the CASA pipeline (cite: 2007ASPC..376..127M)" (2.1 Deep ALMA band 7 observations)
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
  > "with a natural weighting and a pixel size of 0.04”" (2.1 Deep ALMA band 7 observations)
- uv taper: _not stated_
- cell size: 0.04 arcsec  
  > "with a natural weighting and a pixel size of 0.04”" (2.1 Deep ALMA band 7 observations)
- image size: _not stated_
- masking: _not stated_
- multiscale scales: _not stated_
- continuum subtraction: _not stated_
- line free channels: _not stated_
- primary beam correction: _not stated_
- array combination: _not stated_
- smoothing: _not stated_
- final beam: _not stated_
- final rms: _not stated_

### Inherited from earlier work

- Spitzer data reduction as in earlier paper  
  > "The Spitzer data was reduced as described in Laporte et al (2014)" (2.2 Other Imaging Data) [from Laporte et al (2014)]

### Not stated but needed to reproduce (our reading)

- CASA version and pipeline version
- Flux calibrator and flux scale uncertainty
- Spectral setup, channel widths, array configuration and beam
- Continuum bandwidth and line-free channels for continuum
- Line extraction aperture and search method for the 4 sigma line
- MAGPHYS priors and model grid details
- Modified blackbody fitting details and CMB correction

## Analysis recipe

1. **Image ALMA Band 7 and measure continuum**: CASA pipeline reduction, natural weighting; rms from ~2x2 arcmin field  
  > "The uncertainty and significance level was computed from the rms measured across a representative $\approx$2$\times$2 arcmin field." (2.1 Deep ALMA band 7 observations)
   - software: CASA
   - parameter: pixel size 0.04 arcsec  
  > "with a natural weighting and a pixel size of 0.04”" (2.1 Deep ALMA band 7 observations)
   - fitting: _not stated_
   - validation: Split exposure in halves gives 3.2 and 3.4 sigma  
  > "Dividing the exposure into two independent halves, the significances of 3.2 and 3.4 are consistent with that of the total exposure." (2.1 Deep ALMA band 7 observations)
2. **Search for [OIII] 88um line and fit Gaussian**: Search in frequency space; Gaussian fit to line  
  > "Fitting the emission line with a Gaussian profile we derive a modest FWHM=49.8 $\pm$ 4.2 km s$^{-1}$" (3.2 ALMA Observations)
   - fitting: Gaussian profile  
  > "Fitting the emission line with a Gaussian profile" (3.2 ALMA Observations)
   - validation: Half-exposure detections at 2.8 and 3.2 sigma  
  > "Dividing the exposure time in half, the line is detected with independent significances of 2.8 and 3.2" (3.2 ALMA Observations)
3. **Photometric redshift from SED fitting**: Hyperz and EAZY fits to HST, HAWK-I, Spitzer photometry  
  > "In each case we fit all the available photometric data (HST-ACS, HST-WFC3, VLT HAWKI, Spitzer)." (2.3 SED Fitting)
   - software: Hyperz, EAZY, SExtractor, GALFIT
   - parameter: 0<z<10, 0<Av<3 for Hyperz  
  > "We permitted a range in redshift (0 $< z <$ 10) and extinction (0 $< A_v <$ 3)" (2.3 SED Fitting)
   - fitting: chi2 minimization  
  > "found the best solution at $z_{phot}$=8.42$^{+0.09}_{-0.32}$ ($\chi^2\sim$1), with no acceptable solution at lower redshift." (SED Fitting)
   - validation: Low-z solution has worse chi2 ~9  
  > "but with a significantly worse $\chi^2$ $\sim$9" (2.3 SED Fitting)
4. **Derive dust mass and FIR luminosity from continuum**: Modified blackbody, T=35-55 K, beta~2, corrected for magnification and CMB heating  
  > "using a simple modified black body SED with the dust temperatures ranging from 35 to 55K and the dust emissivity fixed at $\beta$$\sim$2" (4.2 The Star Formation Rate and Stellar and Dust Masses)
   - assumption: magnification mu=1.8±0.3  
  > "$\mu$=1.8$\pm$0.3" (4.1 Magnification)
   - fitting: _not stated_
   - validation: Consistent with MAGPHYS full-SED values  
  > "These values estimated with MAGPHYS using the full SED are consistent with those deduced solely from the ALMA continuum flux." (4.2 The Star Formation Rate and Stellar and Dust Masses)
5. **Full SED fit for SFR, stellar and dust mass**: MAGPHYS high-z version with ~9 million models in 11 bands incl. synthetic ALMA band 7  
  > "We generated a total of about 9 million models, including $\approx$25,000 IR dust emission models." (4.2 The Star Formation Rate and Stellar and Dust Masses)
   - software: MAGPHYS
   - fitting: Likelihood distribution of each parameter from comparison with model library  
  > "MAGPHYS then derives the likelihood distribution of each physical parameter by comparing the observed SED with all the models in the library." (4.2 The Star Formation Rate and Stellar and Dust Masses)
   - validation: _not stated_

## Software

- **CASA** : ALMA data reduction (pipeline)  
  > "The data was reduced using the CASA pipeline" (2.1 Deep ALMA band 7 observations)
- **SExtractor** v2.19.5: HST photometry in double image mode  
  > "using *SExtractor* (cite: 1996A&AS..117..393B) v2.19.5 in double image mode" (2.2 Other Imaging Data)
- **GALFIT** : Deblending IRAC fluxes  
  > "We used GALFIT (cite: 2002AJ....124..266P) to deblend the two sources" (2.2 Other Imaging Data)
- **Hyperz** updated version: Photometric redshift  
  > "we used an updated version of *Hyperz*" (2.3 SED Fitting)
- **EAZY** : Photometric redshift  
  > "We also made use of the Easy and Accurate Zphot from Yale" (2.3 SED Fitting)
- **MAGPHYS** updated version for high-z: SED fitting for physical properties  
  > "We also ran an updated version of MAGPHYS" (4.2 The Star Formation Rate and Stellar and Dust Masses)
- **ESO Reflex / X-Shooter pipeline** v2.8 / v2.8.4: X-Shooter reduction  
  > "v2.8 of the ESO Reflex software combined with X-Shooter pipeline recipes v2.8.4" (3.1 X-Shooter Observations)

## Numeric results

| quantity | value | uncertainty | units | step | quote |
|---|---|---|---|---|---|
| ALMA peak continuum flux | 9.9e-5 | 2.3e-5 | Jy/beam | 1 | a peak flux of 9.9$\pm$2.3 $\times$10$^{-5}$ Jy/beam |
| [OIII] 88um line frequency | 361.641 | not stated | GHz | 2 | at a frequency of 361.641 GHz |
| [OIII] redshift | 8.382 | not stated | dimensionless | 2 | the redshift would be $z$=8.382 |
| [OIII] FWHM | 49.8 | 4.2 | km/s | 2 | FWHM=49.8 $\pm$ 4.2 km s$^{-1}$ |
| [OIII] luminosity (uncorrected) | 1.40e8 | 0.35e8 | Lsun | 2 | 1.40$\pm$0.35$\times$10$^8$L$_{\odot}$ |
| Magnification | 1.8 | 0.3 | dimensionless | 0 | $\mu$=1.8$\pm$0.3 |
| MAGPHYS SFR | 20.4 | +17.6/-9.5 | Msun/yr | 5 | SFR=20.4$^{+17.6}_{-9.5}$ M$_{\odot}$ yr$^{-1}$ |
| MAGPHYS stellar mass | 1.97e9 | +1.45/-0.66 e9 | Msun | 5 | M$_{\star}$=(1.97$^{+1.45}_{-0.66}$)$\times$10$^{9}$ M$_{\odot}$ |
| MAGPHYS dust mass | 5.5e6 | +19.6/-1.7 e6 | Msun | 5 | M$_{dust}$=(5.5$^{+19.6}_{-1.7}$)$\times$10$^6$ M$_{\odot}$ |
| Modified blackbody dust mass range | 1.8-10.4e6 | not stated | Msun | 4 | a dust mass ranging from 1.8 to 10.4$\times$10$^{6}$ M$_{\odot}$ |

## Qualitative findings

- Dust mass of order 6e6 Msun exists only ~200 Myr after onset of reionization, roughly consistent with SN dust yields assuming 0.5 Msun per SN.  
  > "over 200 Myr this would yield around 4$\times$ 10$^6$ M$_{\odot}$ of dust in apparent agreement with the observations" (5 Discussion)

## Claim tuples

- H: The ALMA 1mm detection is physically associated with the z~8.4 dropout A2744_YD4 | E: Compare ALMA, HST and X-Shooter positions and redshifts, and search for [OIII] 88um | R: 4 sigma continuum, 4 sigma Lyman alpha at z=8.38, 4 sigma [OIII] at z=8.382, offsets 0.2-0.35 arcsec | F: Joint detections confirm association | **partially**
- H: A2744_YD4 contains a substantial dust mass | E: Modified blackbody and MAGPHYS SED fits | R: Mdust ~5.5e6 Msun, M* ~2e9, SFR ~20 | F: Large dust mass at z=8.38, SN dust could explain it | **supported**

## Reasoning

- Why this data: _not stated_
- Why this method: _not stated_
- Alternative: Line at 11408 Å as [OII] at z~2.06 disfavored by non-detection of the second doublet component  
  > "greater than the range of 0.35-1.5 from theoretical studies" (3.1 X-Shooter Observations)
- How they decided it was enough: _not stated_
- Limitation (authors): Uncertainties in physical properties are large; speculations limited by uncertainties  
  > "Although the uncertainties in these physical properties are large" (4.2 The Star Formation Rate and Stellar and Dust Masses)
- Caveat (inferred, ours): Both line detections only ~4 sigma; line offset 0.35 arcsec and narrow width
- Caveat (inferred, ours): Single-band continuum so dust temperature poorly constrained
- Caveat (inferred, ours): Dust mass depends on assumed T and beta

## Reproducibility

- Data public (paper): ALMA data cited by project ID 2015.1.00594; no explicit public statement  
  > "on the following ALMA data: ADS/JAO.ALMA #\[2015.1.00594\]" (Acknowledgments)
- Products in archive: _not stated_
- Missing: CASA version, spectral setup, array configuration, beam
- Missing: Line search procedure and aperture
- Missing: MAGPHYS configuration
- Data volume (inferred): ~5-20 GB for one Band 7 execution block set
- Score (inferred): 3/5, Public ALMA data and clear outline, but sparse processing and line-search details.
- Rediscovery candidate: no, Key imaging and line search settings missing, and results are low-significance.

## Links

- Method: (cite: 2008MNRAS.388.1595D); (cite: 2015ApJ...806..110D) (MAGPHYS and its high-z version)
- Companion: (cite: 2014ApJ...795...93Z) (First identification of A2744_YD4)
- Related: Frontier Fields
- Related: GLASS

## Checks

```json
{
 "quotes": 58,
 "quotes_ok": 58,
 "quote_pass_rate": 1.0,
 "quotes_too_long": 0,
 "unsupported_facts": 0,
 "project_codes": 0,
 "codes_not_in_text": [],
 "codes_not_in_obscore": [],
 "obscore_codes_not_in_card": [
  "2015.1.00594.S"
 ],
 "codes_printed_but_missing": [],
 "numeric_results": 10,
 "numeric_problems": 0,
 "fill": {
  "facts": 77,
  "stated": 44,
  "rate": 0.571
 },
 "evidence_ok": true
}
```
