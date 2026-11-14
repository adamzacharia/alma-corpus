# The SCUBA-2 Cosmology Legacy Survey: Multi-wavelength Properties of ALMA-identified Submillimeter Galaxies in UKIDSS UDS

`2017ApJ...839...58S` | The Astrophysical Journal 2017 | first author: Simpson, J. M. | arXiv: 1611.03084 | DOI: 10.3847/1538-4357/aa65d0

Card schema 1.0 | model claude-sonnet-5-5 | depth full | type observational_alma_primary

## Science

- Fields: high_z_galaxies
- Question: What are the multi-wavelength properties (redshifts, FIR luminosity, dust temperature, optical depth, attenuation) of ALMA-identified bright SMGs in the UDS field?  
  > "Here, we use the available photometric imaging of the UDS field to study the properties of these 52 ALMA–identified SMGs at optical to radio wavelengths" (1 Introduction)
- Target **52 ALMA-identified SMGs in 30 SCUBA-2 sources in UKIDSS UDS**: coordinates e.g. UDS47.0 02:19:24.84 -05:09:20.7 (J2000)  
  > "UDS47.0 | 02:19:24.84 | $-$05:09:20.7" (Table 1); z/distance photometric z median 2.65 ± 0.13  
  > "UDS47.0 | 02:19:24.84 | $-$05:09:20.7" (Table 1); distance from photometric redshifts from UKIDSS UDS (Hartley13)  
  > "UDS47.0 | 02:19:24.84 | $-$05:09:20.7" (Table 1)

## Data provenance

- ALMA projects: 2012.1.00090.S
- bands: Band 7 (870 um) continuum  
  > "identified using targeted ALMA Band 7 continuum imaging of 30 bright single-dish–detected sub-mm sources" (2 Sample Selection)
- frequencies and spectral setup: _not stated_
- continuum bandwidth: _not stated_
- arrays: _not stated_
- configurations: _not stated_
- baselines: _not stated_
- angular resolution: 0.35'' x 0.25'' (high-res); 0.80'' x 0.65'' (tapered)  
  > "a median synthesized beam of 0.80$''$ $\times$ 0.65$''$" (2 Sample Selection)
- max recoverable scale: _not stated_
- sensitivity: median 1-sigma 0.21 mJy/beam (high-res), 0.26 mJy/beam (tapered)  
  > "median 1–$\sigma$ depth of 0.21 mJy beam$^{-1}$" (2 Sample Selection)
- time on source: _not stated_
- observing dates: 2013 November 1  
  > "observed with ALMA on 2013 November 1 with 26 12 m antennae" (2 Sample Selection)
- pi or archival as stated: _not stated_
- Other facility **UKIDSS/WFCAM, CFHT, Subaru, Spitzer**: U to 4.5 um photometry for photometric redshifts  
  > "The DR8 UKIDSS catalog contains the $U$–to–4.5 $\mu$m photometry for $\sim$ 140,000 sources" (3.1 Optical and Near-Infrared Imaging)
- Other facility **Herschel SPIRE (HerMES)**: 250/350/500 um deblended fluxes  
  > "The UDS field was observed at 250, 350, and 500 $\mu$m with the Spectral and Photometric Imaging Receiver (SPIRE)" (3.2 Far-infrared Imaging)
- Other facility **VLA 1.4 GHz (UDS20)**: radio counterparts, 27/52 detected  
  > "in total 27 / 52 ALMA–identified SMGs are detected in the deep 1.4 GHz imaging" (3.3 Radio)
- Other facility **SCUBA-2 S2CLS**: parent 850 um sub-mm sources  
  > "The initial sample of 30 sub-mm sources was detected in wide-field SCUBA–2 850 $\mu$m imaging of the UDS field" (2 Sample Selection)
- External data: ALMA catalog, sizes of the 52 SMGs  
  > "(cite: Simpson15b) construct a source catalog of 52 SMGs ($S_{870}$ = 1.3-12.9 mJy)" (2 Sample Selection) [from (cite: Simpson15b); (cite: Simpson15)]
- External data: UKIDSS UDS photometric redshifts  
  > "The analysis was presented in (cite: Hartley13) and (cite: Mortlock13)" (3.1.1 Photometric Redshifts) [from (cite: Hartley13); (cite: Mortlock13)]
- External data: ALESS photometry and redshifts for comparison  
  > "we show the magnitude distributions for the 96 ALESS SMGs ((cite: Simpson14))" (4.1) [from (cite: Simpson14); (cite: Swinbank13)]

## Processing

### Calibration

- pipeline or manual: calibrated and imaged with CASA; details in Simpson15b  
  > "the data were calibrated and imaged using the Common Astronomy Software Application (; version 4.2.1)" (2 Sample Selection)
- casa version: 4.2.1  
  > "(; version 4.2.1)" (2 Sample Selection)
- pipeline version: _not stated_
- archive products used as is: _not stated_
- flux calibrator: _not stated_
- flux scale uncertainty: _not stated_
- self calibration: _not stated_

### Imaging

- task: _not stated_
- deconvolver: _not stated_
- weighting robust: Briggs robust = 0.5  
  > "using Briggs weighting with robust = 0.5" (2 Sample Selection)
- uv taper: uv-tapered detection images, beam 0.80'' x 0.65''  
  > "a set of $uv$–tapered “detection” images" (2 Sample Selection)
- cell size: _not stated_
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

- ALMA data reduction and source extraction  
  > "For a detailed description of the data reduction and analysis we refer the reader to (cite: Simpson15b)." (2 Sample Selection) [from (cite: Simpson15b)]
- SPIRE deblending procedure  
  > "we deblend the UDS maps following the procedure presented in (cite: Swinbank13)" (3.2 Far-infrared Imaging) [from (cite: Swinbank13)]
- gas-to-dust ratio 90±25  
  > "We follow (cite: Swinbank13), who present a comparison of the dust masses" (5.4 Dust Correction) [from (cite: Swinbank13)]
- 870 um source sizes  
  > "Intrinsic source size, corrected for synthesized beam, at observed 870 $\mu$m (see (cite: Simpson15))" (Table 2) [from (cite: Simpson15)]

### Not stated but needed to reproduce (our reading)

- CLEAN parameters, cell/image size, masks (in Simpson15b)
- ALMA calibrators and flux scale
- Herschel prior catalog and deblending code details
- Redshift PDFs needed for MCMC prior
- Method for bootstrap errors and median uncertainties
- Dust temperature prior range and SED normalisation details for optically thick fit

## Analysis recipe

1. **match ALMA SMGs to K-band catalog**: positional match within 1'' after astrometric alignment; false-match test with 50,000 random positions  
  > "A matching radius of 1$''$ was adopted" (4.1)
   - fitting: _not stated_
   - validation: random positions false matching rate  
  > "we first construct a catalog of 50,000 random positions within the area of the UKIDSS $K$–band image" (4.1)
2. **photometric redshifts**: eazy template fitting to eleven-band photometry (from Hartley13)  
  > "The template fitting code eazy (cite: Brammer08) was used to fit a library of seven template spectral energy distributions" (3.1.1)
   - software: eazy, SExtractor
   - fitting: zero-point calibration with 2146 spec-z  
  > "First, a subset of 2146 spectroscopically-confirmed sources (excluding AGN) were used to calibrate the photometric redshifts, and correct for any zero-point offsets between the template SEDs and the UDS photometry." (Photometric Redshifts)
   - validation: median dz/(1+z)=0.020, dispersion 0.031  
  > "median ($z_{\rm phot}$-$z_{\rm spec}$) / (1+$z_{\rm spec}$) = 0.020, with a 1–$\sigma$ dispersion of 0.031" (3.1.1)
3. **deblend SPIRE**: chi2 beam fitting at prior positions (24 um + ALMA)  
  > "The SPIRE maps are then deblended by fitting the appropriate beam at the position of each source in the prior catalog and minimizing the $\chi^{2}$ statistic." (3.2)
   - fitting: _not stated_
   - validation: simulations for upper limits  
  > "Upper limits for non-detections and appropriate error bars are determined through simulations (see (cite: Swinbank13))." (Far-infrared Imaging)
4. **optically thin FIR SED fit**: modified blackbody with beta=1.8, redshift PDF prior, Sawicki12 chi2 for limits  
  > "The MCMC code is run using 50 “walkers” for a total 10$^6$ steps, following an initial, and conservative, burn–in phase of 10$^4$ steps." (3.2.1)
   - software: emcee
   - parameter: 50 walkers, 10^6 steps, 10^4 burn-in  
  > "The MCMC code is run using 50 “walkers” for a total 10$^6$ steps, following an initial, and conservative, burn–in phase of 10$^4$ steps." (Far-infrared SED Fitting)
   - assumption: beta = 1.8  
  > "In our analysis we adopt $\beta$ = 1.8" (3.2.1)
   - fitting: emcee; flat prior on Td above CMB limit; redshift PDF prior  
  > "we place an additional, flat prior on the characteristic dust temperature of each source" (3.2.1)
   - validation: chain well-mixed from time series  
  > "An analysis of the time-series data indicates that for each source the burn-in phase is complete and the chain is well–mixed." (Far-infrared SED Fitting)
5. **brightness temperature and optical depth**: solve for T_B from 870um size; optically thick SED with size as prior, assuming same half-light radius at all FIR wavelengths  
  > "we assume that half-light radius of the observed emission at all far–infrared wavelengths is the same as that measured at 870 $\mu$m" (5.3)
   - software: emcee
   - assumption: same size at all wavelengths (lower limits on tau)  
  > "our assumption of a constant source size over-estimates the fraction of observed 250, 350 and 500 $\mu$m flux density that is located within the observed 870–$\mu$m half–light radius, and the optical depth and the true dust temperature derived in our analysis should be considered lower limits." (Luminosity Density, Brightness Temperature and Optical Depth)
   - fitting: as step 4  
  > "The emission from each SMG is modeled using Eqn. [\[eqn:tb\]](#eqn:tb) and the fitting procedure described in § [3.2.1](#subsubsec:firfitting)." (Luminosity Density, Brightness Temperature and Optical Depth)
   - validation: beta 1.5 and 2.0 tests  
  > "we repeat our analysis at a fixed value of $\beta$ = 1.5 and 2.0" (footnote 2)
6. **dust mass, N_H and A_V**: dust mass with kappa; gas-to-dust 90; N_H=2.21e21 Av  
  > "we assume a dust opacity of $\kappa_{850{\mu}\mathrm{m}}$ = 0.07 m$^2$kg$^{-1}$ ((cite: James02))" (5.4)
   - assumption: gas-to-dust 90±25; uniform dust within half-light radius  
  > "Adopting a gas–to-dust ratio of $\delta_{gdr}$ = 90 $\pm$ 25" (5.4)
   - fitting: _not stated_
   - validation: _not stated_

## Software

- **CASA** 4.2.1: calibration and imaging of ALMA data  
  > "(; version 4.2.1)" (2 Sample Selection)
- **emcee** : MCMC SED fitting  
  > "affine-invariant, Markov Chain Monte Carlo (MCMC) sampler (emcee; (cite: EMCEE13))" (3.2.1)
- **eazy** : photometric redshifts  
  > "The template fitting code eazy (cite: Brammer08)" (3.1.1)
- **SExtractor** : dual-image photometry  
  > "running Sextractor (cite: Bertin96) in “dual-image” mode" (3.1)

## Numeric results

| quantity | value | uncertainty | units | step | quote |
|---|---|---|---|---|---|
| median photometric redshift (35 SMGs) | 2.65 | 0.13 | dimensionless | 2 | have a median redshift of $z_{\mathrm{phot}}$ = 2.65 $\pm$ 0.13 |
| median redshift incl. unconstrained at z=3-6 | 2.9 | 0.2 | dimensionless | 2 | $z$ = 2.9 $\pm$ 0.2 |
| median L_FIR (24 SMGs, thin) | 3.4e12 | +0.2/-0.2 | Lsun | 4 | $L_{\mathrm{FIR}}$ = $3.4^{+0.2}_{-0.2}$ $\times$10$^{12}$ |
| median characteristic Td | 32.9 | +0.4/-1.6 | K | 4 | $T_{\mathrm{d}}$ = $32.9^{+0.4}_{-1.6}$ K |
| median brightness temperature | 25 | 1-sigma range 20-32 K | K | 5 | median brightness temperature for the A2SUDS SMGs of 25 K, with a 1–$\sigma$ range of 20–32 K |
| lambda_0 (tau=1) | >=75 | 1-sigma dispersion 55-90 um | um | 5 | median optical depth of unity at $\lambda_0$ (= $c$ / $\nu_0$) $\ge$ 75 $\mu$m |
| median dust mass (thick) | 6.3e8 | +1.1/-0.8 | Msun | 6 | $M_{d}$ = 6.3$_{-0.8}^{+1.1}$$\times$10$^8$ |
| median N_H | 9.8e23 | +1.4/-0.7 | cm^-2 | 6 | $N_{H}$ = 9.8$_{-0.7}^{+1.4}$$\times$10$^{23}$ cm$^{-2}$ |
| median A_V | 540 | +80/-40 | mag | 6 | $A_\mathrm{v}$ = 540$^{+80}_{-40}$ mag |

## Qualitative findings

- SMGs are cooler than local ULIRGs at fixed luminosity  
  > "appear to be significantly cooler at a fixed luminosity" (5.2)

## Claim tuples

- H: Dust emission in SMGs is optically thin | E: Compare sizes, brightness temperatures and SEDs | R: lambda_0 >= 75 um | F: Dust is optically thick at long wavelengths | **supported**
- H: Optical SED fitting captures SMG obscuration | E: Derive A_V from dust mass and gas-to-dust ratio | R: A_V = 540 mag vs ~2 mag from SED fitting | F: Stellar properties from SED fitting are unreliable | **supported**
- H: SMGs are high-z ULIRG analogues | E: Compare Td vs L_FIR with Symeonidis13 | R: ~8 K cooler | F: SMGs are not scaled-up ULIRGs | **supported**

## Reasoning

- Why this data: _not stated_
- Why this method: _not stated_
- How they decided it was enough: _not stated_
- Limitation (authors): Constant size assumption makes optical depth and true Td lower limits  
  > "the optical depth and the true dust temperature derived in our analysis should be considered lower limits" (5.3)
- Caveat (inferred, ours): Gas-to-dust ratio and opacity uncertain (factor ~3)
- Caveat (inferred, ours): Photometric redshifts of SMGs may be less accurate
- Caveat (inferred, ours): Equal-size assumption across FIR wavelengths

## Reproducibility

- Data public (paper): data available from ALMA archive, CADC, WSA  
  > "All data used in this analysis can be obtained from either the ALMA archive, the Canadian Data Archive Center (CADC / JCMT), or the WFCAM Science Archive (WSA / UKIDSS)." (Acknowledgements)
- Products in archive: _not stated_
- Missing: ALMA imaging details (in Simpson15b)
- Missing: UKIDSS photometric redshift PDFs
- Missing: Herschel prior catalogs
- Data volume (inferred): ~tens of GB (30 pointings, one ALMA Cycle 1 execution) plus ancillary catalogs
- Score (inferred): 3/5, Downstream analysis is well described but depends on earlier papers for ALMA reduction and on catalogs.
- Rediscovery candidate: no, Requires multi-survey catalogs and previous-paper products not given here.

## Links

- Method: (cite: Simpson15b) (ALMA data reduction and catalog)
- Method: (cite: Swinbank13) (SPIRE deblending and gas-to-dust ratio)
- Method: (cite: Hartley13) (photometric redshifts)
- Companion: (cite: Simpson15) (far-infrared sizes of SMGs)
- Related: ALESS
- Related: S2CLS
- Related: UKIDSS UDS
- Related: HerMES

## Checks

```json
{
 "quotes": 62,
 "quotes_ok": 62,
 "quote_pass_rate": 1.0,
 "quotes_too_long": 1,
 "unsupported_facts": 0,
 "project_codes": 1,
 "codes_not_in_text": [],
 "codes_not_in_obscore": [],
 "obscore_codes_not_in_card": [],
 "codes_printed_but_missing": [],
 "numeric_results": 9,
 "numeric_problems": 0,
 "fill": {
  "facts": 82,
  "stated": 48,
  "rate": 0.585
 },
 "evidence_ok": true
}
```
