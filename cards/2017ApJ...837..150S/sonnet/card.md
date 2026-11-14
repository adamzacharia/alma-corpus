# Evolution of Interstellar Medium, Star Formation, and Accretion at High Redshift

`2017ApJ...837..150S` | The Astrophysical Journal 2017 | first author: Scoville, N. | arXiv: 1702.04729 | DOI: 10.3847/1538-4357/aa61a0

Card schema 1.0 | model claude-sonnet-5-5 | depth full | type large_program_or_survey

## Science

- Fields: high_z_galaxies
- Question: How do ISM masses (from ALMA RJ dust continuum), star formation efficiency and gas accretion rates depend on redshift, stellar mass and sSFR relative to the main sequence for 708 COSMOS galaxies at z=0.3-4.5?  
  > "ALMA observations of the long wavelength dust continuum are used to estimate the interstellar medium (ISM) masses in a sample of 708 galaxies at z = 0.3 to 4.5 in the COSMOS field." (abstract)
- Target **708 Herschel-selected IR-bright galaxies in COSMOS within ALMA pointings**: coordinates _not stated_; z/distance z = 0.3 to 4.5 (spectroscopic for 38%, otherwise photometric)  
  > "Spectroscopic redshifts were used for 5066 of these sources; the remainder had photometric redshifts from Ilbert et al. (2009) and Laigle et al. (2016)" (3.3 Redshifts, Stellar Masses and Star Formation Rates); distance from Ilbert et al. 2009; Laigle et al. 2016; spectroscopic redshifts  
  > "Spectroscopic redshifts were used for 5066 of these sources; the remainder had photometric redshifts from Ilbert et al. (2009) and Laigle et al. (2016)" (3.3 Redshifts, Stellar Masses and Star Formation Rates)

## Data provenance

- ALMA projects: 2011.0.00097.S, 2011.0.00964.S, 2012.1.00076.S, 2012.1.00323.S, 2012.1.00523.S, 2012.1.00978.S, 2013.1.00034.S, 2013.1.00118.S, 2013.1.00151.S, 2013.1.00208.S, 2013.1.00276.S, 2013.1.00668.S, 2013.1.00815.S, 2013.1.00884.S, 2013.1.01258.S, 2013.1.01292.S, 2015.1.00137.S, 2015.1.00695.S, 2013.1.00111.S
- bands: Band 6 (240 GHz) and Band 7 (345 GHz) continuum  
  > "The galaxy sample used here has ALMA continuum observations in Band 6 (240 GHz) and Band 7 (345 GHz)" (1. Galaxy Evolution at High Redshift)
- frequencies and spectral setup: _not stated_
- continuum bandwidth: _not stated_
- arrays: 12m telescopes  
  > "The maximum correction is a factor 2 when the source is near the HPBW radius for the 12m telescopes." (3.5 Source Measurements)
- configurations: _not stated_
- baselines: _not stated_
- angular resolution: synthesized beams typically ~1 arcsec  
  > "The synthesized beams for most of these observations were ∼ 1′′" (3.5 Source Measurements)
- max recoverable scale: _not stated_
- sensitivity: per-project rms 0.017-0.300 mJy (Table 1)  
  > "2013.1.00815.S Willott 6 263 1 0.97 0.017" (Table 1)
- time on source: ~2 min per galaxy  
  > "relatively short dust continuum measurements ( ∼ 2 min per galaxy with ALMA)" (12. Comparison with Previous Work)
- observing dates: _not stated_
- pi or archival as stated: 18 projects: public archival data plus own proprietary observations; 1011 pointings, 102.9 arcmin^2  
  > "The total number of pointings in these datasets is 1011, covering a total area 0.0286 deg 2 or 102.9 arcmin 2 within the Half-Power Beam Width" (3.1 ALMA Band 6 and 7 Continuum Data)
- Other facility **Herschel PACS/SPIRE (PEP, HerMES)**: Far-infrared catalog used as positional priors and for IR luminosities/SFRs  
  > "Our source finding used a positional prior: the Herschel-based catalog of far-infrared sources in the COSMOS field" (3.2 IR Source Catalog)
- Other facility **COSMOS photometric catalogs**: Photometric redshifts and stellar masses  
  > "The stellar masses of the galaxies are taken from the photometric redshift catalogs (Ilbert et al. 2009; Laigle et al. 2016)" (3.3 Redshifts, Stellar Masses and Star Formation Rates)
- External data: Herschel-based IR source catalog of COSMOS (13597 objects), fluxes and LIR  
  > "the Herschel-based catalog of far-infrared sources in the COSMOS field (Lee et al. 2013, 2015, 13597 objects" (3.2 IR Source Catalog) [from Lee et al. 2013, 2015]
- External data: Photometric redshifts and stellar masses  
  > "the remainder had photometric redshifts from Ilbert et al. (2009) and Laigle et al. (2016)" (3.3 Redshifts, Stellar Masses and Star Formation Rates) [from Ilbert et al. (2009); Laigle et al. (2016)]
- External data: Main-sequence definition (z dependence, model #49)  
  > "The MS locus (SFR(z,M ∗ )) evolves to higher SFRs at earlier epochs as shown in Figure 1-Left (Speagle et al. 2014, their favored model #49)." (2.1 Evolution of the MS with redshift) [from Speagle et al. 2014]
- External data: MS mass-dependence shape at z=1.2  
  > "Here, we use the shape of the MS from Lee et al. (2015) at z = 1.2 for the stellar mass dependence of the MS," (2.2 Shape of the MS with M∗) [from Lee et al. 2015]
- External data: Galaxy stellar mass functions used for cosmic ISM density  
  > "Using the mass functions (MF) of SF and passive galaxies (Ilbert et al. 2013), we estimate the total cosmic mass density of ISM" (10. Cosmic Evolution of ISM and Stellar Mass) [from Ilbert et al. 2013]

## Processing

### Calibration

- pipeline or manual: _not stated_
- casa version: _not stated_
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
- cell size: _not stated_
- image size: _not stated_
- masking: _not stated_
- multiscale scales: _not stated_
- continuum subtraction: _not stated_
- line free channels: _not stated_
- primary beam correction: all fluxes corrected for primary beam attenuation (max factor 2)  
  > "All measured fluxes were corrected for primary beam attenuation." (3.5 Source Measurements)
- array combination: _not stated_
- smoothing: _not stated_
- final beam: _not stated_
- final rms: _not stated_

### Inherited from earlier work

- Dust-continuum-to-ISM-mass calibration (alpha_850 = 6.7e19, beta=1.8, T=25 K, Gamma_RJ)  
  > "applying the calibration of this technique, developed in Scoville et al. (2016)" (1. Galaxy Evolution at High Redshift) [from Scoville et al. (2016)]
- Prior-based Herschel flux extraction and selection function  
  > "it is necessary to extract fluxes using prior-based methods, as described in Lee et al. (2013)." (3.2 IR Source Catalog) [from Lee et al. (2013)]
- Redshift evolution and mass shape of the MS  
  > "We used the combination of Speagle et al. (2014) and Lee et al. (2015)" (2.2 Shape of the MS with M∗) [from Speagle et al. 2014; Lee et al. 2015]

### Not stated but needed to reproduce (our reading)

- Calibration/pipeline, CASA version and calibrators for the 18 projects
- Imaging parameters (weighting, robust, cell, clean) for the continuum maps
- Aperture size used for integrated fluxes and the detailed beam correction
- Per-source table of fluxes, redshifts, M*, SFRs (only to be released via IRSA)
- MCMC settings: chain length, priors, burn-in for linmix_err
- Treatment of Band 6 vs 7 duplicates among the 772 measurements
- Exact selection producing the 575-galaxy fitting sample from z, M* cuts

## Analysis recipe

1. **Measure ALMA continuum fluxes at Herschel positions**: Search for >2 sigma source within 2'' of IR position; peak and integrated flux (beam-corrected), adopt maximum if SNR>2; noise from 50 random apertures; primary beam correction  
  > "we searched for a significant emission source ( >2 σ ) within 2 ′′ radius of the IR source position." (3.5 Source Measurements); "The noise for both the integrated and peak flux measures was estimated by placing 50 randomly positioned apertures" (3.5 Source Measurements)
   - parameter: detection threshold 2 sigma; 3 and 4 sigma tested, <10% change in fit coefficients  
  > "did not find significant changes in the fitting coefficients in the analysis below, that is less than 10% change" (3.5 Source Measurements)
   - fitting: _not stated_
   - validation: About 4 of ~240 2-3 sigma detections expected false  
  > "Since there are ∼ 240 galaxies detected at 2-3 σ, we can expect ∼ 4 of the detections could be false." (3.5 Source Measurements)
2. **Convert fluxes to ISM masses**: Rayleigh-Jeans dust-to-mass calibration (Eq. A1)  
  > "The measured ALMA fluxes were converted to estimates of the ISM masses using Equation A1." (5. Observational Results)
   - parameter: alpha_850 = 6.7±1.7e19 erg/s/Hz/Msun  
  > "α 850 = 6 . 7 ± 1 . 7 × 10 [19] erg sec [−] [1] Hz [−] [1] M ⊙− 1 is the derived calibration constant" (Appendix A)
   - assumption: constant mass-weighted T_D = 25 K  
  > "Here we have adopted a constant value for the massweighted temperature of the ISM dust" (4.3.2 Adopted constant T_D = 25 K)
   - assumption: dust opacity index beta = 1.8; Galactic alpha_CO = 6.5 Msun/(K km/s pc2) incl. 1.36 He factor  
  > "We have adopted a dust opacity spectral index β = 1 . 8" (Appendix A)
   - assumption: sample restricted to M*>2e10 (fit M*>3e10) for near-solar metallicity  
  > "we restrict our sample further to z = 0.3 to 3 and M ∗ > 3 × 10 [10] M ⊙" (6. Dependence of M ISM and SFR)
   - fitting: _not stated_
   - validation: Band 7/Band 6 flux ratio of 19 sources 2.52±0.03 matches expected 2.52  
  > "The SNR-weighted mean value of the Band 7 / Band 6 flux ratio is 2 . 52 ± 0 . 03" (B. Dust Emission Spectral Index and Dust Temperature)
3. **Fit power-law dependence of M_ISM on z, M*, MS-ratio**: Power law constant×P1^α×P2^β×P3^γ fit by Bayesian linear regression MCMC with measurement errors and intrinsic scatter  
  > "A Monte Carlo Markov Chain (MCMC) routine (MLINMIX ~~E~~ RR) (in IDL) was used for the fitting." (6. Dependence of M ISM and SFR)
   - software: linmix_err
   - parameter: 575 galaxies at z=0.3-3, M*>3e10  
  > "The final sample used for fitting the dependencies has 575 distinct galaxies." (6. Dependence of M ISM and SFR)
   - fitting: Gibbs-sampling MCMC, Kelly (2007)  
  > "The Markov chain Monte Carlo algorithm (with Gibbs sampling) is used to randomly sample the posterior distribution (Kelly 2007)." (6. Dependence of M ISM and SFR)
   - validation: Posteriors smooth and non-degenerate; residuals show no systematic offsets in z or MS ratio  
  > "The posterior distributions of the different parameters in the MCMC fitting are single-valued (i.e., non-degenerate) and smooth." (6.1 M ISM)
4. **Fit SFR efficiency dependencies**: Impose linear dependence on M_ISM taken from Eq. 6 and fit SFR with power laws in z, MS-ratio, M*  
  > "we impose a linear dependence of the SFR on M ISM, using M ISM taken from Equation 6 rather than going back to the observed M ISM values." (6.2 SFR)
   - software: linmix_err
   - fitting: same MCMC  
  > "The uncertainties in each of the fit parameters were derived from the MCMC fitting (see Appendix C)." (6.2. SFR)
   - validation: Dispersion distributed around unity, no systematic offsets  
  > "the dispersion in the fit is distributed around unity and there appear to be no systematic offsets with respect to redshift or MS-Ratio." (6.2 SFR)
5. **Derive accretion rates via MS continuity**: Lagrangian rate balance dM_ISM/dt = Macc - (1-f_return) SFR along MS tracks; power-law fit to results  
  > "the rate balance must be given by:" (8. Accretion Rates)
   - parameter: f_mass_return = 0.3  
  > "taken to be 0.3 here (Leitner & Kravtsov 2011)" (8. Accretion Rates)
   - assumption: major mergers rare; continuity of MS evolution  
  > "assuming that major merging events are rare." (8. Accretion Rates)
   - fitting: _not stated_
   - validation: Integrate tracks with 2nd-order Runge-Kutta; MS tracks match those from pure MS relations  
  > "The evolution was integrated in time using a 2nd order Runge Kutta method." (11. A Self-Consistency Test)
6. **Cosmic ISM density evolution**: Apply Eq. 6 to SF galaxy stellar mass functions, M*=1e10-1e12, z=0-4, x1.1 for starbursts  
  > "to include the SB population we multiplied the ISM mass of the normal SF population by a factor of 1.1." (10. Cosmic Evolution of ISM and Stellar Mass)
   - fitting: _not stated_
   - validation: _not stated_

## Software

- **linmix_err (MLINMIX_ERR, IDL)** : Bayesian MCMC linear regression for fits of M_ISM and SFR  
  > "A Monte Carlo Markov Chain (MCMC) routine (MLINMIX ~~E~~ RR) (in IDL) was used for the fitting." (6. Dependence of M ISM and SFR)
- **XID** : SPIRE flux extraction (catalog from earlier work)  
  > "the SPIRE 250, 350, and 500 µ m fluxes were measured using the XID code of Roseboom et al. (2010, 2012)" (3.2 IR Source Catalog)

## Numeric results

| quantity | value | uncertainty | units | step | quote |
|---|---|---|---|---|---|
| M_ISM normalization (z=0, M*=1e10) | 7.07e9 | ±0.88e9 | Msun | 3 | M ISM =7 . 07 ± 0 . 88 × 10 [9] M ⊙ |
| M_ISM exponent of (1+z) | 1.84 | ±0.14 | dimensionless | 3 | (1 + z ) [1] [.] [84] [±] [0] [.] [14] |
| M_ISM exponent of sSFR/sSFR_MS | 0.32 | ±0.06 | dimensionless | 3 | (sSFR / sSFR MS ) [0] [.] [32] [±] [0] [.] [06] |
| M_ISM exponent of M* | 0.30 | ±0.04 | dimensionless | 3 | 0 . 30 ± 0 . 04 |
| SFR per ISM mass normalization | 0.31 | ±0.01 | Msun/yr per 1e9 Msun | 4 | SFR=0 . 31 ± 0 . 01 M ⊙ yr [−] [1] |
| SFR efficiency exponent of sSFR/sSFR_MS | 0.70 | ±0.02 | dimensionless | 4 | (sSFR / sSFR MS ) [0] [.] [70] [±] [0] [.] [02] |
| SFR efficiency exponent of (1+z) | 1.05 | ±0.05 | dimensionless | 4 | (1 + z ) [1] [.] [05] [±] [0] [.] [05] |
| Depletion time normalization | 3.23 | ±0.10 | Gyr | 4 | =3 . 23 ± 0 . 10 Gyr × (1 + z) [−] [1] [.] [05] [±] [0] [.] [05] |
| Accretion rate normalization | 2.27 | ±0.24 | Msun/yr | 5 | ˙M acc =2 . 27 ± 0 . 24 M ⊙ yr [−] [1] × (1 + z) [3] [.] [60] [±] [0] [.] [26] |
| Accretion rate at z=2, M*=5e10 | 73 | not stated | Msun/yr | 5 | The value of the accretion rate at z = 2 and M ∗ = 5 × 10 [10] M ⊙ is 73 M ⊙ yr [−] [1] |
| Band 7/Band 6 flux ratio | 2.52 | ±0.03 | dimensionless | 2 | The SNR-weighted mean value of the Band 7 / Band 6 flux ratio is 2 . 52 ± 0 . 03 |
| Galaxies with >2 sigma and >7 sigma detections | 708 and 182 | not stated | objects | 1 | the measurements yielded 708 and 182 objects with > 2 and > 7 σ detections, respectively. |

## Qualitative findings

- Elevated SFRs at high z and above the MS are due to both increased gas contents and increased star formation efficiency.  
  > "the elevated rates of SF activity at both high redshift and above the MS are due to both increased gas contents and increased efficiencies for converting the gas to stars." (6.2 SFR)
- Gas fractions >50% at z>2, decreasing with stellar mass  
  > "The gas mass fractions shown in Figure 10-Right are very high ( >50%) at z >2 for SF galaxies, systematically decreasing at later epochs." (7.1 Gas Depletion Timescales and Gas Mass Fraction)

## Claim tuples

- H: Is elevated SF at high z and above the MS driven by more gas or higher efficiency? | E: Power-law MCMC fits of M_ISM and SFR/M_ISM versus z, M*, sSFR/sSFR_MS for 575 galaxies | R: M_ISM ∝ (1+z)^1.84 (sSFR/sSFR_MS)^0.32 M*^0.30; efficiency ∝ (1+z)^1.05 (MS ratio)^0.70 | F: Both increased ISM mass and increased SF efficiency contribute | **supported**
- H: What gas accretion rates are required to maintain MS evolution? | E: MS continuity principle with M_ISM relation | R: Net accretion >100 Msun/yr at z>2.5; Macc ∝ (1+z)^3.60 | F: Galaxy evolution at early epochs is driven by accretion | **supported**

## Reasoning

- Why this data: _not stated_
- Why this method: RJ dust continuum is optically thin, linear in mass-weighted T and avoids CO excitation uncertainty; needs far fewer observations than CO  
  > "our analysis involving the RJ dust continuum avoids the issue of variable excitation which causes uncertainty when using different CO transitions across galaxy samples." (3.4 Complete Sample of ALMA-detected IR-bright Galaxies)
- Alternative: Using SED-fit variable T_D was rejected as it gives luminosity-weighted rather than mass-weighted temperature  
  > "we believe that using a T D derived from the SED fits yields a luminosityweighted T D , not the physically correct mass-weighted T D ." (4.3.2 Adopted constant T_D = 25 K)
- How they decided it was enough: _not stated_
- Limitation (authors): Sample biased to IR-bright, massive galaxies; not representative of the high-z SF population  
  > "the sample is not representative of the high redshift SF galaxy population." (3.2 IR Source Catalog)
- Limitation (authors): Calibration gives ~factor 2 accuracy; fit uncertainties exclude calibration uncertainties  
  > "they do not account for possible calibration uncertainties such as the conversion from L IR to SFR." (6.1 M ISM)
- Caveat (inferred, ours): Constant T_D=25 K and alpha_850 calibrated on low-z and SMG samples may bias high-z masses
- Caveat (inferred, ours): Photometric redshifts and M* for ~62% of sources; 2-sigma threshold with Herschel priors
- Caveat (inferred, ours): Fits ignore Malmquist bias and selection effects; extrapolation for cosmic density
- Caveat (inferred, ours): Fixed alpha_CO=6.5 vs 4.3 shifts all masses by a factor 2/3

## Reproducibility

- Data public (paper): Most projects public; some proprietary; images to be released via IRSA COSMOS in 2017  
  > "we make use of all those data which are publicly available, in addition to our own still proprietary observations." (3.1 ALMA Band 6 and 7 Continuum Data)
- Products in archive: _not stated_
- Missing: Reduction/imaging parameters for all 18 projects
- Missing: Final per-source flux and ancillary catalog
- Missing: Exact definition of apertures and selection of 575 sample
- Data volume (inferred): Large: 18 ALMA projects, ~1000 pointings; likely hundreds of GB raw, tens of GB images
- Score (inferred): 5/5, Public data and explicit equations and fit results, but imaging/calibration details and catalogs are not given and the dataset is large and heterogeneous.
- Rediscovery candidate: no, Recipe for fluxes and ancillary catalogs is incomplete and requires many projects and external catalogs, though final fit numbers are explicit.

## Links

- Method: Scoville et al. (2016) (Calibration of RJ dust continuum to ISM mass)
- Method: Kelly (2007) (Linmix MCMC regression)
- Method: Lee et al. (2013) (Herschel prior-based flux extraction)
- Companion: Scoville et al. (2016) (Calibration and initial application)
- Companion: Schinnerer et al. (2016) (ALMA 240 GHz dataset included here)
- Related: COSMOS
- Related: PEP
- Related: HerMES

## Checks

```json
{
 "quotes": 85,
 "quotes_ok": 85,
 "quote_pass_rate": 1.0,
 "quotes_too_long": 0,
 "unsupported_facts": 0,
 "project_codes": 19,
 "codes_not_in_text": [],
 "codes_not_in_obscore": [],
 "obscore_codes_not_in_card": [],
 "codes_printed_but_missing": [],
 "numeric_results": 12,
 "numeric_problems": 0,
 "fill": {
  "facts": 86,
  "stated": 50,
  "rate": 0.581
 },
 "evidence_ok": true
}
```
