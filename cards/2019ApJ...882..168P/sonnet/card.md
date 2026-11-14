# Low Star Formation Efficiency in Typical Galaxies at z = 5-6

`2019ApJ...882..168P` | The Astrophysical Journal 2019 | first author: Pavesi, Riccardo | arXiv: 1812.00006 | DOI: 10.3847/1538-4357/ab3a46

Card schema 1.0 | model claude-sonnet-5-5 | depth full | type observational_alma_primary

## Science

- Fields: high_z_galaxies
- Question: What are the molecular gas content, star formation efficiency and ionized-gas ([NII]/[CII]) properties, and hence metallicity hints, of normal Main Sequence galaxies at z=5-6?  
  > "We here present NSF’s Karl G. Jansky Very Large Array (VLA) observations of the CO(2–1) transition from the FIR-brightest “normal" galaxy of the (cite: C15) sample" (Introduction)
- Target **HZ10**: coordinates _not stated_; z/distance z = 5.6543 ± 0.0003 ([CII])  
  > "CO(2–1) line transition from HZ10 ($z\sim5.7$)" (Introduction); distance from [CII] line, Table of line properties  
  > "CO(2–1) line transition from HZ10 ($z\sim5.7$)" (Introduction)
- Target **LBG-1 (HZ6)**: coordinates _not stated_; z/distance z = 5.29359 ± 0.00015 ([CII])  
  > "LBG-1 ($z\sim5.3$; also named HZ6; (cite: Riechers14; C15))" (Introduction); distance from [CII] line, Table of line properties  
  > "LBG-1 ($z\sim5.3$; also named HZ6; (cite: Riechers14; C15))" (Introduction)
- Target **HZ9**: coordinates _not stated_; z/distance _not stated_; distance from _not stated_
- Target **HZ4**: coordinates _not stated_; z/distance _not stated_; distance from _not stated_

## Data provenance

- ALMA projects: 2012.1.00523.S, 2015.1.00928.S, 2015.1.00388.S, 2011.0.00064.S
- bands: ALMA Band 7 ([CII], Cycle 1) and Band 6 ([NII], Cycle 3); VLA Ka band  
  > "These observations were taken on 2013 November 4-16 in band 7" (2.2 ALMA observations); "were taken on 2016 January 1 and 5 in band 6" (2.2 ALMA observations)
- frequencies and spectral setup: [NII]: two 1.875 GHz spectral windows per sideband, 15.6 MHz (~20 km/s) channels, TDM  
  > "to cover two spectral windows of 1.875 GHz bandwidth each at $15.6\,$MHz ($\sim20\,$km s$^{-1}$) resolution (dual polarization) in Time Division Mode (TDM), in each sideband" (2.2 ALMA observations)
- continuum bandwidth: _not stated_
- arrays: _not stated_
- configurations: [NII] Cycle-3: compact configuration, max. baseline ~300 m  
  > "taken in a compact configuration (max. baseline $\sim300\,$m)" (2.2 ALMA observations)
- baselines: _not stated_
- angular resolution: [NII] beams ~1.5-1.7" x 1.1-1.2"; [CII] HZ4 0.8"x0.5", HZ9 0.6"x0.5"; VLA CO ~3.0"x2.3"  
  > "Imaging the [Nii] data for HZ4 results in a synthesized beam size of $1.6^{\prime\prime} \times 1.1^{\prime\prime}$" (2.2 ALMA observations)
- max recoverable scale: _not stated_
- sensitivity: [NII] continuum rms 13-19 uJy/beam over 7.5 GHz; VLA CO rms ~45 uJy/beam per 35 km/s channel at HZ10  
  > "The final rms noise when averaging over the line free spectral windows (i.e. over a total $7.5\,$GHz of bandwidth) is $\sim 13\, \mu$Jy beam$^{-1}$." (2.2 ALMA observations)
- time on source: [CII]: HZ4 20 min, HZ9 38 min; [NII]: LBG-1 64+18 min, HZ4 30 min, HZ9 47 min; VLA HZ10 19.8 hr, LBG-1 14 hr  
  > "The HZ4 pointing resulted in $20\,$min on source with 28 usable antennae." (2.2 ALMA observations); "The total observing time was 19.8 hrs, on source." (2.1 VLA observations)
- observing dates: _not stated_
- pi or archival as stated: _not stated_
- Line: CO J=2-1 (not stated)
- Line: [CII] 158 um (not stated)
- Line: [NII] 205 um (not stated)
- Other facility **VLA**: CO(2-1) observations of HZ10 (17A-011) and LBG-1 (COLDz) in Ka band  
  > "We observed the CO(2–1) transition in HZ10 using the VLA in Ka band (project ID: 17A-011, PI: Pavesi)." (2.1 VLA observations)
- External data: Stellar masses of sample galaxies  
  > "were measured by (cite: C15) and (cite: Laigle16) for the entire parent sample" (Footnote 6) [from (cite: C15); (cite: Laigle16)]
- External data: Earlier [CII] data for LBG-1 and HZ10  
  > "Our observations of the \[Cii\] line, data reduction and imaging for LBG-1 and HZ10 were previously described by (cite: Riechers14; C15), and (cite: Pavesi16)." (2.2 ALMA observations) [from (cite: Riechers14; C15; Pavesi16)]

## Processing

### Calibration

- pipeline or manual: _not stated_
- casa version: CASA 4.5 (ALMA), 4.7 (VLA)  
  > "We used casa version 4.5 for data reduction and analysis." (2.2 ALMA observations)
- pipeline version: _not stated_
- archive products used as is: _not stated_
- flux calibrator: Ganymede ([CII]); J0854+2006 / J1058+0133 ([NII] bandpass and flux)  
  > "Ganymede was observed as flux calibrator" (2.2 ALMA observations)
- flux scale uncertainty: ~10%  
  > "We estimate the overall accuracy of the flux calibration to be within $\sim10\%$." (2.2 ALMA observations)
- self calibration: _not stated_

### Imaging

- task: CASA clean  
  > "produced all images with the clean algorithm, using natural weighting for maximal point source sensitivity" (2.2 ALMA observations)
- deconvolver: _not stated_
- weighting robust: natural weighting  
  > "using natural weighting for maximal point source sensitivity" (2.2 ALMA observations)
- uv taper: _not stated_
- cell size: _not stated_
- image size: _not stated_
- masking: _not stated_
- multiscale scales: _not stated_
- continuum subtraction: _not stated_
- line free channels: _not stated_
- primary beam correction: _not stated_
- array combination: Combined data from all observations (tracks)  
  > "We combined data from all observations" (2.2 ALMA observations)
- smoothing: _not stated_
- final beam: _not stated_
- final rms: _not stated_

### Inherited from earlier work

- VLA observation details for HZ10  
  > "A complete description of these observations may be found in (cite: CRLE)" (2.1 VLA observations) [from (cite: CRLE)]
- COLDz observations and imaging of LBG-1  
  > "A complete description of these observations and of the imaging may be found in (cite: Pavesi_COLDz)." (2.1 VLA observations) [from (cite: Pavesi_COLDz)]
- Dynamical mass method from visibility modeling  
  > "following the method previously described by (cite: CRLE)" (Analysis) [from (cite: CRLE)]

### Not stated but needed to reproduce (our reading)

- Line-free channel ranges and aperture-spectrum extraction details
- Cell/image sizes, clean thresholds and masks
- emcee walkers/steps and likelihood for SED fit
- Exact Scoville16 assumptions applied to Rayleigh-Jeans gas masses
- CASA version for the Cycle-1 flux scale and calibration details beyond calibrator names

## Analysis recipe

1. **Measure dust continuum**: Image line-free channels with natural weighting and fit 2D Gaussian with imfit  
  > "by imaging all line-free channels using natural baseline weighting, and using the casa task imfit to fit a 2D Gaussian model to the emission" (3.1 Dust continuum)
   - software: CASA
   - fitting: _not stated_
   - validation: _not stated_
2. **Fit FIR SED and derive L_FIR and SFR**: Modified blackbody joined to mid-IR power law, Bayesian MCMC; L_FIR integrated 42.5-122.5 um  
  > "We derive far-infrared (FIR) luminosities by integrating between 42.5 and 122.5 $\mu$m" (3.1 Dust continuum)
   - software: emcee
   - parameter: Gaussian priors: beta 1.7±0.5, T_dust 60±15 K, mid-IR index 2.0±0.5, transition wavelength 60±20 um  
  > "for the dust temperature ($60\pm15$ K), for the mid-IR power law index ($2.0\pm0.5$)" (3.1 Dust continuum)
   - assumption: FIR luminosity taken as total IR estimate  
  > "we follow the standard practice of adopting the FIR luminosities as an estimate of total IR" (3.1 Dust continuum)
   - fitting: MCMC with emcee, Gaussian priors  
  > "employ a Markov Chain Monte-Carlo technique through `emcee`" (3.1 Dust continuum)
   - validation: _not stated_
3. **Measure CO line properties and size**: Aperture spectrum for HZ10, single-pixel spectrum for LBG-1; uvmodelfit circular Gaussian for size  
  > "We use casa uvmodelfit to fit a circular Gaussian model to the line visibilities in HZ10" (3.2 CO measurements)
   - software: CASA
   - assumption: R21 = 1; CMB effect absorbed into alpha_CO  
  > "we therefore assume a brightness temperature ratio of $R_{21}=1$" (3.2 CO measurements)
   - fitting: _not stated_
   - validation: CO size compared with [CII]  
  > "use it to validate that CO and \[Cii\] emission sizes for our target are consistent within the relative uncertainties" (3.2 CO measurements)
4. **Gas mass from Rayleigh-Jeans dust and dynamical mass**: Scoville16 Eqs 10 and 13 for dust; Daddi10a empirical dynamical mass with 25% dark matter and stellar mass subtracted  
  > "We here adopt Equations 10 and 13 in (cite: Scoville16) to derive gas mass estimates" (3.1 Dust continuum)
   - assumption: Fixed alpha_CO = 4.5 for gas masses  
  > "we assume a fixed value of $\alpha_{\rm CO}=4.5$ for definiteness" (3.3 Dynamical mass)
   - fitting: _not stated_
   - validation: Compared with visibility-based disk model and Jones17  
  > "The inferred dynamical mass estimates are in agreement with those derived by (cite: Jones17)" (3.3 Dynamical mass)
5. **Measure [NII] and [CII]/[NII]**: Aperture spectra, uvmodelfit sizes, line ratio and PDR fraction assuming ionized-gas ratio 3±0.5  
  > "We follow (cite: Tanio17) and assume a line ratio of $3\pm0.5$ in the ionized gas" (3.5 [NII] measurements)
   - software: CASA
   - fitting: _not stated_
   - validation: _not stated_
6. **Visibility-based dynamical modeling (Appendix B)**: KinMS rotating disk fit to [CII] visibilities of HZ9 and HZ10 with GALARIO and Multinest  
  > "We simultaneously fit a rotating disk model generated by KinMS (cite: KinMS) to the line emission and a simple continuum model" (B. Dynamical Modeling)
   - software: KinMS, GALARIO, Multinest
   - parameter: 18 free parameters HZ10, 12 for HZ9  
  > "We fit a total of 18 parameters for HZ10" (B. Dynamical Modeling)
   - fitting: _not stated_
   - validation: Residuals inspected  
  > "non-negligible residual structure after model fitting" (B. Dynamical Modeling)

## Software

- **CASA** 4.5 (ALMA), 4.7 (VLA): Calibration, imaging, imfit, uvmodelfit  
  > "We used casa version 4.5 for data reduction and analysis." (2.2 ALMA observations)
- **emcee** : MCMC SED fitting  
  > "employ a Markov Chain Monte-Carlo technique through `emcee`" (3.1 Dust continuum)
- **KinMS** : Rotating disk model  
  > "rotating disk model generated by KinMS" (B. Dynamical Modeling)
- **GALARIO** : Visibility modeling  
  > "using `GALARIO` (cite: GALARIO) and `Multinest` (cite: Multinest)" (B. Dynamical Modeling)
- **Multinest** : Nested sampling of dynamical model  
  > "using `GALARIO` (cite: GALARIO) and `Multinest` (cite: Multinest)" (B. Dynamical Modeling)

## Numeric results

| quantity | value | uncertainty | units | step | quote |
|---|---|---|---|---|---|
| L'_CO(2-1) HZ10 | 2.9 | ±0.6 | 1e10 K km/s pc^2 | 3 | $L'_{\rm CO}$ ($10^{10}$ K km s$^{-1}$ pc$^2$) / — / $<0.44$ / — / $2.9\pm0.6$ |
| Molecular gas mass HZ10 | 13 | ±3 | 1e10 Msun | 4 | $M_{\rm gas}$ ($10^{10}\,M_\odot$)$^b$ / — / $<2$ / — / $13\pm3$ |
| Gas depletion time HZ10 | 960 | +1200/-470 | Myr | 4 | yields a gas depletion timescale (the inverse of the star formation efficiency) of $960^{+1200}_{-470}\,$Myr |
| alpha_CO HZ10 from dynamical mass | 4.2 | +2/-1.7 | Msun (K km/s pc^2)^-1 | 4 | $4.2^{+2}_{-1.7}$ for HZ10 |
| L_[CII]/L_[NII] HZ10 | 17 | +7/-4 | dimensionless | 5 | $L_{\rm [CII]}/L_{\rm [NII]}$ / $>24$ / $41^{+20}_{-10}$ / $61^{+40}_{-17}$ / $17^{+7}_{-4}$ |
| L_[CII]/L_[NII] LBG-1 | 41 | +20/-10 | dimensionless | 5 | $L_{\rm [CII]}/L_{\rm [NII]}$ / $>24$ / $41^{+20}_{-10}$ / $61^{+40}_{-17}$ / $17^{+7}_{-4}$ |
| L_FIR HZ10 | 13 | +11/-7 | 1e11 Lsun | 2 | $L_{\rm FIR}$ ($10^{11}\,L_\odot$) / $5.2^{+4.6}_{-2.6}$ / $4.9^{+4.4}_{-2.6}$ / $12^{+10}_{-6}$ / $13^{+11}_{-7}$ |
| Dynamical mass HZ10 from disk model | 6.1 | ±0.7 | 1e10 Msun | 6 | We obtain $\sim(6.1\pm0.7)\times10^{10}\,M_\odot$ for HZ10 |

## Qualitative findings

- CO(2-1) detected in HZ10 at z~5.7, the highest-redshift low-J CO detection from an LBG; LBG-1 has only a deep upper limit  
  > "We report the highest redshift detection of low-$J$ CO emission from a Lyman Break Galaxy, at $z\sim5.7$." (abstract)

## Claim tuples

- H: Do normal z~6 galaxies have starburst-like star formation efficiency? | E: CO(2-1) with VLA and FIR from ALMA continuum for HZ10 | R: Gas depletion time ~960 Myr | F: Efficiency is low, like lower-z Main Sequence disks | **supported**
- H: Do z=5-6 normal galaxies show faint [NII] relative to [CII], implying low metallicity? | E: ALMA [NII] 205um in four galaxies | R: High [CII]/[NII] in HZ9, LBG-1, HZ4; low in HZ10 | F: Low metallicity or harder radiation fields common in less IR-luminous galaxies | **supported**
- H: Is LBG-1's CO faintness due to a high alpha_CO? | E: CO upper limit vs gas mass from dust and dynamics | R: Dynamics gives no significant constraint; dust gives alpha_CO >~5.7 | F: Suggestive of higher alpha_CO at low metallicity, not conclusive | **partially**

## Reasoning

- Why this data: _not stated_
- Why this method: _not stated_
- Alternative: Lower nitrogen abundance relative to carbon as alternative explanation of faint [NII]  
  > "an alternative interpretation for the low \[Nii\] luminosity in our high redshift sample may invoke lower nitrogen abundance, relative to carbon" (3.5 [NII] measurements)
- How they decided it was enough: _not stated_
- Limitation (authors): Rayleigh-Jeans gas masses dominated by systematic uncertainty from extrapolation to high z  
  > "These estimates are dominated by the systematic uncertainty inherent in extrapolating the Rayleigh-Jeans method to very high redshift" (3.2 CO measurements)
- Caveat (inferred, ours): Only two CO targets; small sample
- Caveat (inferred, ours): alpha_CO fixed at 4.5 and CMB effect unconstrained
- Caveat (inferred, ours): FIR SED poorly constrained with only 2 ALMA points
- Caveat (inferred, ours): Natural weighting with coarse VLA beams limits size measurements

## Reproducibility

- Data public (paper): ALMA data acknowledged via project codes  
  > "This paper makes use of the following ALMA data: ADS/JAO.ALMA#2015.1.00928.S, 2015.1.00388.S, 2012.1.00523.S, 2011.0.00064.S." (Acknowledgments)
- Products in archive: _not stated_
- Code: Visibility disk-modeling code at github.com/pavesiriccardo/UVmodeldisk  
  > "Python code available at https://github.com/pavesiriccardo/UVmodeldisk" (Footnote 13)
- Missing: Imaging parameters (cell, size, masks)
- Missing: Line-free channel selection
- Missing: VLA data are not an ALMA project
- Missing: Exact priors for dynamical fits
- Data volume (inferred): ~100-300 GB for ALMA raw data across four projects
- Score (inferred): 5/5, Public ALMA data and clear high-level recipe, but many inherited choices and missing imaging details.
- Rediscovery candidate: no, Key CO result needs VLA data and inherited processing; imaging settings are incomplete.

## Links

- Method: (cite: CRLE) (Full VLA description and visibility dynamical modeling method)
- Method: (cite: Pavesi_COLDz) (COLDz observations and imaging)
- Companion: (cite: C15) (Original ALMA [CII] and continuum sample)
- Companion: (cite: Pavesi16) (Earlier [NII] study of HZ10 and LBG-1)
- Related: COLDz
- Related: ALPINE

## Checks

```json
{
 "quotes": 69,
 "quotes_ok": 69,
 "quote_pass_rate": 1.0,
 "quotes_too_long": 0,
 "unsupported_facts": 0,
 "project_codes": 4,
 "codes_not_in_text": [],
 "codes_not_in_obscore": [],
 "obscore_codes_not_in_card": [],
 "codes_printed_but_missing": [],
 "numeric_results": 8,
 "numeric_problems": 0,
 "fill": {
  "facts": 90,
  "stated": 48,
  "rate": 0.533
 },
 "evidence_ok": true
}
```
