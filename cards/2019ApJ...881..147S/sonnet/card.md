# Positive and Negative Feedback of AGN Outflows in NGC 5728

`2019ApJ...881..147S` | The Astrophysical Journal 2019 | first author: Shin, Jaejin | arXiv: 1907.00982 | DOI: 10.3847/1538-4357/ab2e72

Card schema 1.0 | model claude-sonnet-5-5 | depth full | type archival_reuse

## Science

- Fields: nearby_galaxies, agn_and_quasars
- Question: Do AGN-driven ionized gas outflows in NGC 5728 enhance (positive feedback) or suppress (negative feedback) star formation, as seen in MUSE ionized gas and ALMA CO(2-1) molecular gas?  
  > "We present a spatially-resolved analysis of ionized and molecular gas in a nearby Seyfert 2 galaxy NGC 5728, using the VLT/MUSE and ALMA data." (abstract)
- Target **NGC 5728**: coordinates _not stated_; z/distance 40.3 Mpc  
  > "we focus on a nearby Seyfert 2 galaxy NGC 5728 at a distance of 40.3 Mpc" (INTRODUCTION); distance from _not stated_

## Data provenance

- ALMA projects: 2015.1.00086.S
- bands: _not stated_
- frequencies and spectral setup: _not stated_
- continuum bandwidth: _not stated_
- arrays: _not stated_
- configurations: _not stated_
- baselines: _not stated_
- angular resolution: 0.55'' x 0.47'' synthesized beam  
  > "The synthesized beam of the final cube is 0.55$''$ $\times$ 0.47 $''$ with a 1-$\sigma$ rms of $\sim$0.65 mJy per beam per channel." (Data)
- max recoverable scale: _not stated_
- sensitivity: 1-sigma rms ~0.65 mJy/beam/channel  
  > "The synthesized beam of the final cube is 0.55$''$ $\times$ 0.47 $''$ with a 1-$\sigma$ rms of $\sim$0.65 mJy per beam per channel." (Data)
- time on source: _not stated_
- observing dates: _not stated_
- pi or archival as stated: archival, P.I. N. Nagar  
  > "we also utilized the ALMA archival data of the 12 CO (2-1) line from Project 2015.1.00086 (P.I. N. Nagar)." (Data)
- Line: 12CO J=2-1 (not stated)
- Other facility **VLT/MUSE (TIMER survey)**: Optical IFU cube for ionized gas and stellar kinematics, SFR  
  > "NGC 5728 was observed with the VLT/MUSE in 2016 Apr 3 and Jun 3 as a part of the Time Inference with MUSE in Extragalactic Rings (TIMER) survey" (Data)
- External data: Star formation ring geometry (PA 20 deg, inclination 50 deg) used in bicone model  
  > "the position angle of the major axis of the ring: 20$^\circ$, and the inclination of the minor axis: 50$^\circ$ based on the previous work by (cite: Son2009a)" (4.4 Bicone model) [from (cite: Son2009a)]
- External data: Bolometric AGN luminosity 1.46e44 erg/s  
  > "the bolometric luminosity of AGN is $1.46\times\ 10^{44}\ \rm erg/s$ estimated from X-ray luminosity ((cite: Durre2019)" (Discussion) [from (cite: Durre2019)]

## Processing

### Calibration

- pipeline or manual: Re-calibrated with the pipeline  
  > "The raw data were re-calibrated and re-imaged using the pipeline, CASA 4.7.0." (Data)
- casa version: CASA 4.7.0  
  > "The raw data were re-calibrated and re-imaged using the pipeline, CASA 4.7.0." (Data)
- pipeline version: _not stated_
- archive products used as is: _not stated_
- flux calibrator: Titan (amplitude); J1517-2422 bandpass; J1448-1620 phase  
  > "Phase, bandpass and amplitude were calibrated using J1448-1620, J1517-2422 and Titan, respectively." (Data)
- flux scale uncertainty: _not stated_
- self calibration: _not stated_

### Imaging

- task: _not stated_
- deconvolver: _not stated_
- weighting robust: robust = 0  
  > "the robust weighting was set to be the robust 0 to optimize the data in sensitivity and resolution" (Data)
- uv taper: _not stated_
- cell size: _not stated_
- image size: _not stated_
- masking: _not stated_
- multiscale scales: _not stated_
- continuum subtraction: _not stated_
- line free channels: _not stated_
- primary beam correction: _not stated_
- array combination: _not stated_
- smoothing: 10 km/s channels  
  > "The channel was sampled into 10 km $\rm s^{-1}$ width" (Data)
- final beam: 0.55'' x 0.47''  
  > "The synthesized beam of the final cube is 0.55$''$ $\times$ 0.47 $''$" (Data)
- final rms: ~0.65 mJy/beam/channel  
  > "1-$\sigma$ rms of $\sim$0.65 mJy per beam per channel" (Data)

### Inherited from earlier work

- Ionizing-source separation via linear mixing sequence in BPT diagrams  
  > "as similarly performed by (cite: Davies2016)" (3.1/4.2.3) [from (cite: Davies2016)]
- Outflow size method from [O III] velocity dispersion  
  > "we estimate the size of the AGN gas outflows by adopting the method of (cite: Kang2018)" (4.2.2 Kinematics) [from (cite: Kang2018)]
- Bicone model extended with seeing  
  > "we build a three dimensional bicone model by including a point spread function in the model of (cite: Bae2016)" (4.4 Bicone model) [from (cite: Bae2016)]

### Not stated but needed to reproduce (our reading)

- Which spectral window/channels define the CO line and how the continuum was subtracted
- Exact 5-sigma masking procedure and moment-0 velocity range
- Region A-D apertures (arbitrarily chosen, no coordinates)
- Primary beam correction
- Whether pipeline products were used or manual scripts; imaging cell size and image size
- Details of ALMA flux scale uncertainty
- Bicone model best-fit values of all 11 parameters (model unpublished)

## Analysis recipe

1. **Make CO(2-1) intensity map and molecular gas mass**: Line intensity map with data above ~5 sigma; M_H2 from Eq. 3 of Bolatto2013  
  > "we made a CO (2-1) line intensity map only with the data above $\sim$5$\sigma$ in order to be conservative." (3.2 ALMA analysis)
   - software: CASA
   - parameter: Xco = 2e20 cm^-2 (K km/s)^-1; CO(2-1)/(1-0) ~0.8  
  > "The mean CO (2-1) to CO (1-0) line ratio was assumed to be $\sim$0.8 (cite: Braine1992)." (3.2 ALMA analysis)
   - assumption: Milky Way Xco and line ratio 0.8; comparisons relative within the area  
  > "all comparisons are made relatively within the area of interest, and hence our interpretation is robust regardless of the choice of those values." (3.2 ALMA analysis)
   - fitting: _not stated_
   - validation: _not stated_
2. **Derive SFR from MUSE Halpha after AGN separation**: BPT AGN fraction, SFR = 5.37e-42 L_Halpha, dust corrected using Balmer decrement  
  > "calculate SFR based on Eq. 4 of (cite: Murphy2011)" (4.2.3)
   - software: pPXF, MPFIT
   - assumption: Intrinsic Balmer decrement 2.86, R_V 4.5  
  > "with the Balmer decrement (i.e., H$\alpha$/H$\beta$) of 2.86 and $R^{A}_{V}$ of 4.5" (4.2.3)
   - fitting: Gaussian fits with A/N>3, Monte Carlo errors with 100 mock spectra  
  > "The uncertainties were measured based on Monte-Carlo simulations with 100 mock spectra" (3.1 MUSE analysis)
   - validation: Consistent with Davies2016 separation  
  > "our AGN-star formation separation is consistent with that of (cite: Davies2016)" (4.2.3)
3. **Compute SFE and depletion time in regions A-D**: SFE = SFR/M_Mol, compare Region A to B, C, D  
  > "star formation efficiency (SFE=SFR/$M_{\rm Mol}$)" (4.3 Molecular gas)
   - fitting: _not stated_
   - validation: _not stated_
4. **Model bicone outflow geometry**: 3D bicone model with seeing, chi-square comparison of 1D radial profiles to [O III]  
  > "which represents the observation with the minimum chi-square value" (4.4 Bicone model)
   - parameter: 11 free parameters; seeing 0.66''  
  > "The updated model requires 11 free parameters" (4.4 Bicone model)
   - fitting: minimum chi-square  
  > "which represents the observation with the minimum chi-square value" (4.4 Bicone model)
   - validation: Qualitative comparison of simulated maps  
  > "the simulated maps qualitatively represent the flux distribution and kinematics of \[O III\]" (4.4 Bicone model)

## Software

- **CASA** 4.7.0: Recalibration and imaging of ALMA data  
  > "re-calibrated and re-imaged using the pipeline, CASA 4.7.0" (Data)
- **pPXF** : Stellar continuum fitting  
  > "using the Penalized Pixel-Fitting code (cite: Cappellari2017)" (3.1 MUSE analysis)
- **MPFIT** : Emission line fitting  
  > "using the MPFIT package (cite: Markwardt2009)" (3.1 MUSE analysis)
- **ESOREFLEX** MUSE version 2.4.2: MUSE reduction  
  > "reduced with the standard ESO reduction pipeline, ESOREFLEX (MUSE version of 2.4.2)" (Data)

## Numeric results

| quantity | value | uncertainty | units | step | quote |
|---|---|---|---|---|---|
| SFR surface density Region A (avg) | 1.82 | not stated | Msun/yr/kpc^2 | 2 | Region A / $1.82$ / $1.70$ |
| SFE Region A (avg) | 1.62e-8 | not stated | yr^-1 | 3 | 1.62$\times \rm 10^{-8}$ |
| Depletion time Region A (avg) | 0.062 | not stated | Gyr | 3 | 0.062 |
| AGN contribution to Halpha in Regions A,B,C,D | 10, 5, 3, 2 | 6, 6, 1, 2 | % | 2 | 10$\pm$6, 5$\pm$6, 3$\pm$1, and 2$\pm$2 % for Region A, B, C, and D |
| Best bicone inclination | 20 | not stated | deg | 4 | an inclination of 20$^\circ$ and an outer opening angle of $\pm$28$^\circ$ |
| Outflow size | ~600 | not stated | pc | 0 | Our estimated outflow size is $\sim600$ pc |

## Qualitative findings

- CO(2-1) barely detected in Region A, with SFE 3-5 times higher than in other ring regions  
  > "CO emission is barely detected at Region A." (4.3 Molecular gas)

## Claim tuples

- H: AGN outflows enhance star formation where they meet the ring | E: Compare SFR and CO-derived SFE of Region A with B-D | R: Region A SFR high, CO weak, SFE 3-5x higher | F: Consistent with positive feedback | **supported**
- H: Outflows impact global star formation | E: Compare Region A SFR to total SFR | R: Region A ~10% of the ~2 Msun/yr | F: Overall impact limited | **supported**

## Reasoning

- Why this data: _not stated_
- Why this method: _not stated_
- Alternative: CO deficit may be due to X-ray excitation or shock dissociation rather than gas consumption  
  > "Another scenario is that CO is excited by X-ray photons from AGN" (Discussion)
- How they decided it was enough: _not stated_
- Limitation (authors): Xco and CO line ratio assumptions may not apply to AGN hosts  
  > "it is arguable whether our assumptions for Xco and CO (2-1) to (1-0) line ratio are applicable for AGN hosts" (3.2 ALMA analysis)
- Caveat (inferred, ours): CO weakness could reflect excitation or dissociation rather than efficient star formation
- Caveat (inferred, ours): Regions were chosen arbitrarily, selection bias
- Caveat (inferred, ours): Single galaxy, Xco uncertain, dust correction failed in SE

## Reproducibility

- Data public (paper): ALMA archival data; MUSE from ESO archive  
  > "The data was retrieved from the ESO archive" (Data)
- Products in archive: _not stated_
- Code: _not stated_
- Missing: Region A-D definitions
- Missing: Bicone model code and best-fit parameters
- Missing: Imaging scripts and line channel selection
- Data volume (inferred): ~10-50 GB (ALMA) plus ~few GB MUSE
- Score (inferred): 3/5, Public data and numeric tables, but region definitions and several processing details are missing.
- Rediscovery candidate: no, Region selection and the unpublished model make a full redo difficult.

## Links

- Method: (cite: Davies2016) (AGN/SF mixing separation)
- Method: (cite: Bae2016) (Bicone model)
- Companion: (cite: Durre2018; Durre2019) (Previous MUSE/SINFONI studies of NGC 5728)
- Related: TIMER survey

## Checks

```json
{
 "quotes": 49,
 "quotes_ok": 49,
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
  "facts": 73,
  "stated": 38,
  "rate": 0.521
 },
 "evidence_ok": true
}
```
