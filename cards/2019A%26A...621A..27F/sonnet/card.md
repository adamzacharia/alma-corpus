# Massive galaxies on the road to quenching: ALMA observations of powerful high redshift radio galaxies

`2019A&A...621A..27F` | Astronomy and Astrophysics 2019 | first author: Falkendal, Theresa | arXiv: 1809.09427 | DOI: 10.1051/0004-6361/201732485

Card schema 1.0 | model claude-sonnet-5-5 | depth full | type observational_alma_primary

## Science

- Fields: agn_and_quasars, high_z_galaxies
- Question: What are the star-formation rates of powerful high-z radio galaxy hosts once synchrotron contamination and spatially resolved components are separated using ALMA data, and how do they compare with the main sequence and SMBH growth?  
  > "It is therefore essential to disentangle the thermal dust and synchrotron components." (Introduction)
- Target **25 HzRGs from the HeRGÉ sample (e.g. MRC 0114-211, MRC 0943-242, PKS 0529-549)**: coordinates per-source positions in results table  
  > "Our sample consists of 25 HzRGs over the redshift range 1$<$$z$$<$5.2." (2.1 Sample); z/distance 1<z<5.2  
  > "Our sample consists of 25 HzRGs over the redshift range 1$<$$z$$<$5.2." (2.1 Sample); distance from _not stated_

## Data provenance

- ALMA projects: 2012.1.00039.S, 2013.1.00521.S, 2015.1.00530.S, 2012.1.00242.S
- bands: Cycle 2 Band 6 (Band 4 for TN J2007-1316); Cycle 3 Band 3 (Band 4 for MRC 0943-242)  
  > "ALMA Cycle 2 band 6 (and band 4 for source TN J2007-1316) observations were carried out from June 2014 to September 2015" (2.2 ALMA Observations)
- frequencies and spectral setup: four 1.875 GHz spectral windows  
  > "We used four 1.875 GHz spectral windows, tuned to cover molecular lines at the specific redshift of each source" (2.2 ALMA Observations)
- continuum bandwidth: _not stated_
- arrays: _not stated_
- configurations: _not stated_
- baselines: _not stated_
- angular resolution: ~0.3 arcsec in band 6 (beams 0.26-0.68 arcsec); band 3 beams ~1.6-1.9 arcsec  
  > "With 0.3$''$ resolution mm ALMA data" (Conclusions)
- max recoverable scale: _not stated_
- sensitivity: _not stated_
- time on source: _not stated_
- observing dates: Cycle 2: June 2014 to September 2015; Cycle 3: March 2016 to September 2016  
  > "observations were conducted from March 2016 to September 2016" (2.2 ALMA Observations)
- pi or archival as stated: _not stated_
- Other facility **ATCA 7 mm and 3 mm**: radio continuum photometry  
  > "we combine our ALMA data with 7 mm and 3 mm observations from the Australia Telescope Compact Array" (Introduction)
- Other facility **VLA**: published radio maps/fluxes for synchrotron  
  > "we use the available radio maps from the Very Large Array" (Introduction)
- Other facility **Herschel, Spitzer, LABOCA, SCUBA**: MIR-submm photometry for SED  
  > "The parent sample has complete 12-band 3.6 to 850  $\mu$m photometry from *Spitzer*, *Herschel* SCUBA/LABOCA" (2.1 Sample)
- External data: Stellar masses of the sources  
  > "All stellar masses used in this paper are based on those estimated in (cite: Seymour2007; DeBreuck2010; Drouart2016)." (4.5 Notes on the Stellar Masses) [from (cite: DeBreuck2010; Drouart2016)]
- External data: Previous Herschel SED-based IR luminosities for comparison  
  > "we now make a direct comparison of our results with those of (cite: Drouart2014)." (4.4 IR luminosity model comparison) [from (cite: Drouart2014)]
- External data: 4C 23.56 ALMA band 3 and 6 continuum data  
  > "we use the ALMA band 3 and 6 continuum data presented in (cite: Lee2017)." (2.2 ALMA Observations) [from (cite: Lee2017)]

## Processing

### Calibration

- pipeline or manual: CASA with observatory-supplied calibration scripts (MRC 2224-273 script modified)  
  > "The data was calibrated in CASA (Common Astronomy Software Application) with the supplied calibration script" (2.2 ALMA Observations)
- casa version: _not stated_
- pipeline version: _not stated_
- archive products used as is: _not stated_
- flux calibrator: _not stated_
- flux scale uncertainty: _not stated_
- self calibration: phase self-cal for MRC 0114-211 only, RMS 87 to 59 uJy  
  > "For the brightest source MRC 0114-211, a phase self-calibration was done which decreased the RMS noise in the final image from 87  $\mu$Jy to 59  $\mu$Jy." (2.2 ALMA Observations)

### Imaging

- task: mode mfs, BARY frame  
  > "barycentric reference frame (BARY), and the mode “mfs” (multi-frequency synthesis emulation)" (2.2 ALMA Observations)
- deconvolver: _not stated_
- weighting robust: natural weighting  
  > "we decided to optimize the sensitivity by using natural weighting to construct images" (2.2 ALMA Observations)
- uv taper: _not stated_
- cell size: 0.06 arcsec (Cycle 2); 0.28 arcsec (Cycle 3)  
  > "cell size of 0.06 arcsec (roughly five times smaller than the beam size)" (2.2 ALMA Observations)
- image size: _not stated_
- masking: channels affected by atmospheric absorption excluded  
  > "we excluded the affected channels from the final images" (2.2 ALMA Observations)
- multiscale scales: _not stated_
- continuum subtraction: _not stated_
- line free channels: _not stated_
- primary beam correction: _not stated_
- array combination: _not stated_
- smoothing: _not stated_
- final beam: _not stated_
- final rms: _not stated_

### Inherited from earlier work

- 4C 23.56 observations and reduction  
  > "Please see (cite: Lee2017) for details of the observations and data reduction." (2.2 ALMA Observations) [from (cite: Lee2017)]
- SFR and AGN accretion conversions, bolometric correction  
  > "we follow the analysis of (cite: Drouart2014) quite closely, that is, we use the same conversion factors between IR luminosities and SFR and AGN accretion rates" (5 Relationship between radio galaxies and their SMBHs) [from (cite: Drouart2014)]
- ATCA data reduction strategy  
  > "The observing and data reduction strategy, as well as the basic data products, were previously described in (cite: Emonts2011) and (cite: Emonts2014)." (2.3 ATCA 7 mm and 3 mm data) [from (cite: Emonts2011; Emonts2014)]

### Not stated but needed to reproduce (our reading)

- Number of walkers, steps and burn-in for emcee
- Exact line-free/flagged channels per source
- CASA version used for imaging
- Image size and clean threshold/masks
- Flux calibrator and flux-scale uncertainty
- How ALMA band 3/4 photometry was extracted per source in detail (regions, apertures)
- Prior treatment of normalisations in MR-MOOSE

## Analysis recipe

1. **Image ALMA continuum and measure fluxes**: Natural-weighted mfs continuum images; integrated fluxes over regions >1.5 sigma; 3 sigma upper limits over one beam; blended sources deblended with two Gaussians  
  > "Integrated fluxes are determined over regions where the signal has a significance $>$1.5$\sigma$." (Table 3 notes)
   - software: CASA
   - fitting: _not stated_
   - validation: _not stated_
2. **Fit MIR-radio SEDs with three components**: MR-MOOSE Bayesian MCMC fit of AGN power-law with cutoff, modified blackbody for SF dust, and synchrotron power law, with multi-resolution component assignment  
  > "The code fits simultaneously all pre-selected analytic models and uses Bayesian statistics to find the most likely solution given the set of observed fluxes." (3 MR-MOOSE)
   - software: MR-MOOSE, emcee
   - parameter: lambda_cut=33 um fixed; T prior [20,70] K; gamma [0,6]; alpha [-4,0]  
  > "N$_\text{BB}$, T \[20,70K\]" (Table 2)
   - assumption: beta=2.5, nu0=1.5 GHz; uniform priors; synchrotron without cutoff (maximum contribution)  
  > "A value of $\beta=2.5$ has been adopted in this paper." (3.1.2 Star-formation model)
   - fitting: emcee MCMC, chi2 likelihood with upper-limit treatment of Sawicki2012, uniform priors  
  > "it uses Bayesian parameter estimation to find posterior distributions of the free parameters which are determined based on the prior distribution (uniform) and the likelihood function." (3.2 Fitting procedure)
   - validation: lambda_cut calibrated on 4C 23.56; comparison with Drouart2014 luminosities  
  > "This value was determined by letting $\lambda_\text{cut}$ be a free parameter for one galaxy and finding the best fit value." (3.1.1 AGN model)
3. **Integrate IR luminosities and uncertainties; derive SFR**: Integrate models over rest-frame 8-1000 um for each MCMC sample; percentiles give uncertainties; upper limits by scaling modified BB (beta=2.5, T=50 K) to ALMA; SFR from Kennicutt1998 divided by 1.5 for Kroupa  
  > "This is done by scaling a modified BB (with fixed $\beta = 2.5$ and T=$50$ K) to the ALMA data point." (4.1 SF and AGN IR luminosities)
   - assumption: SFR = 1.72e-10 L_IR_SF, Salpeter IMF then /1.5 to Kroupa  
  > "${\rm SFR} = 1.72 \times 10^{-10} \times {\rm L}_{\rm SF}^{\rm IR},$" (5.1)
   - fitting: _not stated_
   - validation: _not stated_
4. **Compare with main sequence and SMBH growth**: Compare SFR and stellar mass with Schreiber2015 and Santini2017 MS; compare L_AGN-derived accretion rate (eps=0.1, kappa=6) with SFR  
  > "where the efficiency factor $\epsilon =0.1$ and the bolometric correction factor $\kappa^{\rm Bol}_{\rm AGN} = 6$." (5.1)
   - fitting: _not stated_
   - validation: _not stated_

## Software

- **CASA** 4.5.0 (stated for two-Gaussian deblending): calibration, imaging, deblending  
  > "The flux of these sources is deblended by fitting two Gaussian profiles using CASA 4.5.0." (Table 3 notes)
- **MR-MOOSE** : multi-component SED fitting  
  > "MR-MOOSE is a new SED fitting code, developed with the goal of being able to handle multi-resolution photometric data" (3 MR-MOOSE)
- **emcee** : MCMC sampling  
  > "MR-MOOSE uses the Monte Carlo Markov Chain (MCMC) core provided in the Python package, *Emcee*" (3.2 Fitting procedure)
- **MIRIAD** : ATCA data calibration  
  > "The data were calibrated using the software package, MIRIAD" (2.3 ATCA)
- **AIPS** : radio map flux estimation  
  > "Flux estimated using AIPS from original radio map, convolved to the resolution of the VLA C band." (MRC 0037-258)

## Numeric results

| quantity | value | uncertainty | units | step | quote |
|---|---|---|---|---|---|
| median SFR of sample | 110 | not stated | Msun/yr | 3 | with a median[^3] value of 110  M$_{\odot}$ yr$^{-1}$ |
| SFR reduction factor vs Drouart2014 | ~7 | not stated | dimensionless | 3 | Our star-formation rates are seven times lower than previously estimated by (cite: Drouart2014) for the same sources. |
| ratio L_IR_SF to Drouart2014 (detections only) | ~0.5 | not stated | dimensionless | 3 | our estimates of L$^\mathrm{IR}_\mathrm{SF}$ are only $\sim$50% of those estimated in (cite: Drouart2014) |
| sources vs Schreiber2015 MS (above/within/below) | 2 / 14 / 9 | not stated | sources | 4 | we find two sources lie above, 14 sources lie within the 0.3 dex scatter of the MS, and nine lie below the MS. |
| extra duration of star formation needed vs previous | >50 times longer than SMBH activity | not stated | dimensionless | 4 | now implies that the star formation must last over a factor of 50 longer. |

## Qualitative findings

- Synchrotron dominates mm emission in nine of 25 sources' components, so ignoring it overestimates SFR  
  > "For nine out of 25 sources, the best-fit SEDs of specific spatial components are consistent with a power-law extrapolation from radio frequencies." (6.3)

## Claim tuples

- H: HzRG SFRs from Herschel were overestimated | E: MR-MOOSE SED fits including ALMA and ATCA data | R: median SFR ~7 times lower | F: HzRG star formation is much lower than previously thought | **supported**
- H: HzRGs lie on the star-forming main sequence | E: Compare SFR vs stellar mass with Schreiber2015 and Santini2017 | R: most on or below the MS | F: many are on the road to quenching | **supported**
- H: Radio source size correlates with SFR suppression | E: SFR vs LAS | R: possible trend, not significant | F: no clear relation | **partially**

## Reasoning

- Why this data: _not stated_
- Why this method: Simple analytic models because only ~10 IR data points  
  > "we are still limited to $\sim$10 data points in the infrared." (3.1 Analytic models)
- How they decided it was enough: _not stated_
- Limitation (authors): Upper limits dominate many SFRs; no intermediate-frequency data to determine synchrotron steepening  
  > "without a data point at an intermediate frequency between the radio and ALMA data, it is not possible to make a final conclusion" (MRC 1017-220)
- Caveat (inferred, ours): Fixed beta=2.5 and T=50 K for upper limits drive SFR limits
- Caveat (inferred, ours): Main-sequence comparison depends on chosen MS parametrisation and mass range
- Caveat (inferred, ours): Stellar masses inherited and may be AGN-contaminated
- Caveat (inferred, ours): Low-resolution band 3 maps limit component separation

## Reproducibility

- Data public (paper): MR-MOOSE open source; SED plots available online  
  > "MR-MOOSE[^1] is open source and the current version operates in MIR to radio wavelengths" (3 MR-MOOSE)
- Products in archive: _not stated_
- Code: https://github.com/gdrouart/MrMoose  
  > "https://github.com/gdrouart/MrMoose" (footnote 1)
- Missing: MCMC chain settings
- Missing: Imaging masks and image sizes
- Missing: Exact flux extraction apertures
- Missing: Stellar masses and photometry from external catalogs
- Data volume (inferred): ~100-300 GB raw for four ALMA projects (25 sources)
- Score (inferred): 3/5, Data and code public with photometry tables given, but imaging and MCMC details are sparse.
- Rediscovery candidate: no, Multi-wavelength photometry compiled from many external sources and MCMC settings missing.

## Links

- Method: (cite: drouart18) (MR-MOOSE SED fitting code)
- Method: (cite: Sawicki2012) (likelihood with upper limits)
- Companion: (cite: Drouart2014) (parent Herschel HeRGÉ SED study)
- Companion: (cite: Lee2017) (4C 23.56 ALMA data)
- Related: HeRGÉ (Herschel radio galaxy evolution)

## Checks

```json
{
 "quotes": 54,
 "quotes_ok": 54,
 "quote_pass_rate": 1.0,
 "quotes_too_long": 0,
 "unsupported_facts": 0,
 "project_codes": 4,
 "codes_not_in_text": [],
 "codes_not_in_obscore": [],
 "obscore_codes_not_in_card": [],
 "codes_printed_but_missing": [],
 "numeric_results": 5,
 "numeric_problems": 0,
 "fill": {
  "facts": 75,
  "stated": 41,
  "rate": 0.547
 },
 "evidence_ok": true
}
```
