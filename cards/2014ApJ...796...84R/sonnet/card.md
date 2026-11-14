# ALMA Imaging of Gas and Dust in a Galaxy Protocluster at Redshift 5.3: [C II] Emission in "Typical" Galaxies and Dusty Starbursts ≈1 Billion Years after the Big Bang

`2014ApJ...796...84R` | The Astrophysical Journal 2014 | first author: Riechers, Dominik A. | arXiv: 1404.7159 | DOI: 10.1088/0004-637X/796/2/84

Card schema 1.0 | model claude-sonnet-5-5 | depth full | type observational_alma_primary

## Science

- Fields: high_z_galaxies
- Question: What are the gas (CII, OH) and dust properties of the SMG AzTEC-3 and of 'typical' Lyman-break galaxies in the z=5.3 protocluster?  
  > "Here we report 158 $\mu$m [CII]($^2P_{3/2}$$\to$$^2P_{1/2}$), 163 $\mu$m OH($^2\Pi_{1/2}\,J$=3/2$\to$1/2), and rest-frame 157.7 $\mu$m dust continuum imaging toward the center of the galaxy protocluster" (1 Introduction)
- Target **AzTEC-3**: coordinates _not stated_; z/distance z=5.2988±0.0001 ([CII])  
  > "redshifted to 301.72 GHz, or 994 $\mu$m, at $z$=5.299" (Observations); distance from [CII] line fit (this work)  
  > "redshifted to 301.72 GHz, or 994 $\mu$m, at $z$=5.299" (Observations)
- Target **LBG-1**: coordinates _not stated_; z/distance z=5.2950±0.0002 ([CII])  
  > "peaks at a central redshift of $z$=5.2950$\pm$0.0002" (2.2 [CII] Line Emission); distance from [CII] line fit (this work); optical z_spec=5.300  
  > "peaks at a central redshift of $z$=5.2950$\pm$0.0002" (2.2 [CII] Line Emission)
- Target **LBG-2 and LBG-3**: coordinates _not stated_; z/distance photometric z consistent with protocluster; undetected  
  > "LBG-3 has a photometric redshift of $z_{\rm phot}$=5.269 (C11)" (Results); distance from C11 photometric redshifts  
  > "LBG-3 has a photometric redshift of $z_{\rm phot}$=5.269 (C11)" (Results)

## Data provenance

- ALMA projects: 2011.0.00064.S
- bands: ~994 µm (301.72 GHz), 870 µm weather conditions  
  > "redshifted to 301.72 GHz, or 994 $\mu$m, at $z$=5.299" (Observations)
- frequencies and spectral setup: Spectral windows of 1.875 GHz at 0.488 MHz resolution in each sideband; [CII] in upper sideband, OH and CO(16-15) in lower  
  > "The correlator was set up to target two spectral windows of 1.875 GHz bandwidth each at 0.488 MHz (0.48 kms$^{-1}$) resolution (dual polarization) in each sideband." (Observations)
- continuum bandwidth: _not stated_
- arrays: 12 m antennas, 16-24 usable  
  > "Observations were carried out with 16–24 usable 12 m antennas" (Observations)
- configurations: Cycle 0 extended (4 tracks) and compact (1 track)  
  > "for 4 tracks in the cycle 0 extended configuration (longest baseline: 402 m)" (Observations)
- baselines: 21 m to 402 m  
  > "for 1 track in the cycle 0 compact configuration[^4] (shortest baseline: 21 m)" (Observations)
- angular resolution: 0.63" x 0.55" at [CII]  
  > "resulting in a synthesized beam size of 0.63 $''$$\times$0.55 $''$ at the redshifted [CII] line frequencies" (Observations)
- max recoverable scale: _not stated_
- sensitivity: ~50 µJy/beam over 7.5 GHz  
  > "is $\sim$50 $\mu$Jy beam$^{-1}$ in the phase centers of both pointings" (Observations)
- time on source: 125 min, split over two pointings  
  > "This resulted in 125 min on-source time, which was evenly split over two (slightly overlapping) pointings" (Observations)
- observing dates: 2012 April 11 to May 17 (extended), 2012 November 18 (compact)  
  > "between 2012 April 11 and May 17, and for 1 track in the cycle 0 compact configuration[^4] (shortest baseline: 21 m) on 2012 November 18" (Observations)
- pi or archival as stated: _not stated_
- Line: [CII] 2P3/2→2P1/2 (1900.5369 GHz)
- Line: OH 2Π1/2 J=3/2→1/2 doublet (1834.74735 and 1837.81682 GHz)
- Line: CO J=16→15 (1841.345506 GHz)
- Other facility **VLA**: CO(2-1) data toward LBG-1 (non-detection)  
  > "we have used a recent data set (PI: Riechers) from the Karl G. Jansky Very Large Array (VLA) to search for CO($J$=2$\to$1) line emission toward LBG-1" (3.3 OH and CO Line Emission)
- Other facility **HST/ACS**: F814W imaging for sizes of LBGs  
  > "Based on their small sizes in *HST*/ACS F814W imaging data" (3.1 Continuum)
- External data: AzTEC-3 continuum photometry 100 µm-8.2 mm used in SED fit  
  > "continuum data between observed-frame 100 $\mu$m and 8.2 mm (R10; C11; Huang et al. (cite: hua14); Smolčić et al. (cite: smo14))" (3.4 SED, AzTEC-3) [from R10; C11; Huang et al. (cite: hua14); Smolčić et al. (cite: smo14)]
- External data: CO(2-1), (5-4), (6-5) line fluxes of AzTEC-3  
  > "\[1\] Riechers et al. ((cite: rie10))" (Table 4) [from Riechers et al. (cite: rie10)]
- External data: COSMOS photometry and photometric/spectroscopic redshifts, UV SED fitting of LBGs  
  > "Given the detailed available photometry from COSMOS, we match galaxy templates to the observed SED of LBG-1" (3.4 SED, LBGs) [from C11; Ilbert et al. (cite: ilb09)]
- Simulation/model as data: Nearby galaxy SED templates (spiral, starburst, dust-obscured, dwarf) compared to LBG-1  
  > "we match galaxy templates to the observed SED of LBG-1" (3.4 SED, LBGs)

## Processing

### Calibration

- pipeline or manual: AIPS and CASA used independently for reduction  
  > "The Astronomical Image Processing System (AIPS) and Common Astronomy Software Applications (CASA) packages were used independently for data reduction and analysis" (Observations)
- casa version: _not stated_
- pipeline version: _not stated_
- archive products used as is: _not stated_
- flux calibrator: Titan or Callisto; J1058+015 for pointing, bandpass, amplitude, phase  
  > "Fluxes were derived relative to Titan or Callisto." (Observations)
- flux scale uncertainty: ~20%  
  > "We estimate the overall accuracy of the calibration to be accurate within $\sim$20%." (Observations)
- self calibration: _not stated_

### Imaging

- task: CLEAN; FLATN in AIPS for primary-beam-corrected mosaics  
  > "Primary beam-corrected mosaics were created using the FLATN task in AIPS." (Observations)
- deconvolver: _not stated_
- weighting robust: natural weighting  
  > "All data were mapped using the CLEAN algorithm with “natural” weighting" (Observations)
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
- final beam: 0.63" x 0.55" ([CII]); 0.63" x 0.56" line-free continuum  
  > "0.63 $''$$\times$0.56 $''$ when averaging over the three [CII] line-free spectral windows" (Observations)
- final rms: ~50 µJy/beam over 7.5 GHz  
  > "The final rms noise when averaging over all spectral windows (i.e., over a total of 7.5 GHz of bandwidth) is $\sim$50 $\mu$Jy beam$^{-1}$" (Observations)

### Inherited from earlier work

- MCMC modified blackbody SED fitting method  
  > "employing the method described by Riechers et al. ((cite: rie13)) and Dowell et al. ((cite: dow14))" (3.4 SED, AzTEC-3) [from Riechers et al. (cite: rie13); Dowell et al. (cite: dow14)]
- UV SFR via SED fitting methods  
  > "using the SED fitting methods outlined by C11" (4.2 LBGs) [from C11]
- Source size errors determined following Condon  
  > "Errors are determined as described by Condon ((cite: con97))." (3.1 Continuum) [from Condon (cite: con97)]
- Isotropic virial estimator for dynamical mass  
  > "we then use an isotropic virial estimator (e.g., Engel et al. (cite: eng10)) to derive dynamical masses" (3.5 Derivation of Further Galaxy Properties) [from Engel et al. (cite: eng10)]

### Not stated but needed to reproduce (our reading)

- CASA/AIPS versions
- CLEAN mask, threshold, cell and image size
- Line-free channels and continuum subtraction method
- Which processing (AIPS vs CASA) produced the final maps and fluxes
- Aperture/extraction regions for spectra of LBG components
- MCMC priors on T_dust, alpha, lambda0 and run settings beyond beta prior
- Which dwarf templates were used and their normalisation
- Exact virial coefficient and radius definition for M_dyn
- Flux calibrator choice per track

## Analysis recipe

1. **Calibrate and image the ALMA data**: AIPS and CASA reduction; natural-weighted CLEAN; AIPS FLATN mosaics  
  > "Primary beam-corrected mosaics were created using the FLATN task in AIPS." (Observations)
   - software: AIPS, CASA
   - parameter: natural weighting; beam 0.63"x0.55"  
  > "All data were mapped using the CLEAN algorithm with “natural” weighting" (Observations)
   - fitting: _not stated_
   - validation: Two packages used independently to quantify calibration uncertainty  
  > "used independently for data reduction and analysis to better quantify potential uncertainties in the calibration" (Observations)
2. **Measure continuum and line sizes and fluxes**: 2D Gaussian fits for sizes; four-parameter Gaussian fits to line plus continuum spectra  
  > "were determined with four parameter Gaussian fits to the line and continuum emission spectra" (3.2 [CII] Line Emission)
   - parameter: upper limits are 3σ; LBG-2/3 limits assume LBG-1 line width and redshift  
  > "Assuming the same line width and redshift as measured for LBG-1." (Table 1)
   - fitting: Gaussian fits; errors following Condon (1997)  
  > "Errors are determined as described by Condon ((cite: con97))." (3.1 Continuum)
   - validation: _not stated_
3. **Fit dust SED of AzTEC-3**: Affine-invariant MCMC modified blackbody joined to a power law; optically thin and thick models  
  > "We used an affine-invariant Markov Chain Monte-Carlo (MCMC) approach" (3.4 SED, AzTEC-3)
   - software: mbb_emcee
   - parameter: Gaussian prior beta = 1.9±0.3; normalization at observed 500 µm  
  > "A weak Gaussian prior of 1.9$\pm$0.3 is adopted for $\beta$." (3.4 SED, AzTEC-3)
   - assumption: kappa_nu = 2.64 m^2/kg at 125 µm (Dunne et al. 2003)  
  > "a dust absorption coefficient of $\kappa_\nu$=2.64 m$^2$kg$^{-1}$ at 125 $\mu$m" (3.4 SED, AzTEC-3)
   - fitting: affine-invariant MCMC; chi2 19.44/10 dof (thin), 14.63/9 dof (thick)  
  > "The best fit solution has a $\chi^2$ of 14.63 for 9 degrees of freedom" (3.4 SED, AzTEC-3)
   - validation: Compared chi2 of optically thin vs thick models  
  > "suggesting a significantly better fit than in the optically-thin case" (3.4 SED, AzTEC-3)
4. **Constrain FIR luminosity, SFR and dust mass of LBGs**: Normalise nearby galaxy templates to Subaru i-band; integrate dwarf templates over 42.5-122.5 µm; scale to ALMA limit  
  > "we thus integrated the dwarf galaxy templates over their infrared peaks." (3.4 SED, LBGs)
   - parameter: T_dust=30 K, beta=1.5 for dust mass limit  
  > "Assuming a dust temperature of $T_{\rm dust}$=30 K and an opacity power law index of $\beta$=1.5" (3.4 SED, LBGs)
   - assumption: Chabrier IMF for SFR from L_FIR; LBG-2/3 share LBG-1 redshift and SED shape  
  > "We assume a Chabrier ((cite: cha03)) stellar initial mass function (IMF) to derive star formation rates from $L_{\rm FIR}$." (3.5 Derivation of Further Galaxy Properties)
   - fitting: template matching  
  > "Given the detailed available photometry from COSMOS, we match galaxy templates to the observed SED of LBG-1" (Spectral Energy Distribution, Lyman-Break Galaxies)
   - validation: UV-based SFR of 22 Msun/yr compared with FIR limit  
  > "This is comparable to the best SFR$_{\rm FIR}$ limit, and again consistent with low dust extinction." (4.2 LBGs)
5. **Derive line luminosities, dynamical masses, SFR surface density**: Standard line luminosity relations; isotropic virial estimator using line width and major-axis size; Sigma_SFR from SFR and FIR continuum size  
  > "For AzTEC-3, we use the measured continuum size to estimate the average star formation rate surface density." (3.5 Derivation of Further Galaxy Properties)
   - assumption: alpha_CO=0.8 Msun (K km/s pc^2)^-1 for gas mass (R10)  
  > "Using $\alpha_{\rm CO}$$=$0.8 ($<$1.3) $M_{\odot}$ (K kms$^{-1}$ pc$^2$)$^{-1}$" (4.1 AzTEC-3)
   - fitting: _not stated_
   - validation: _not stated_

## Software

- **AIPS** : data reduction, FLATN mosaics  
  > "Primary beam-corrected mosaics were created using the FLATN task in AIPS." (Observations)
- **CASA** : independent data reduction and analysis  
  > "The Astronomical Image Processing System (AIPS) and Common Astronomy Software Applications (CASA) packages were used independently" (Observations)
- **mbb_emcee** : MCMC modified blackbody SED fitting  
  > "https://github.com/aconley/mbb_emcee" (Footnote 8)

## Numeric results

| quantity | value | uncertainty | units | step | quote |
|---|---|---|---|---|---|
| AzTEC-3 1.0 mm continuum flux density | 6.20 | 0.25 | mJy | 2 | we find a continuum flux density of 6.20$\pm$0.25 mJy |
| AzTEC-3 [CII] integrated flux | 8.21 | 0.29 | Jy km/s | 2 | corresponding to an integrated line flux of 8.21$\pm$0.29 Jy kms$^{-1}$ |
| AzTEC-3 [CII] FWHM | 421 | 19 | km/s | 2 | at a line FWHM of 421$\pm$19 kms$^{-1}$ |
| AzTEC-3 [CII] redshift | 5.2988 | 0.0001 | dimensionless | 2 | peaks at a redshift of $z$=5.2988$\pm$0.0001 |
| LBG-1 [CII] integrated flux | 2.08 | 0.18 | Jy km/s | 2 | corresponding to an integrated line flux of 2.08$\pm$0.18 Jy kms$^{-1}$ |
| LBG-1 [CII] FWHM | 218 | 24 | km/s | 2 | at a line FWHM of 218$\pm$24 kms$^{-1}$ |
| AzTEC-3 OH integrated flux | 1.44 | 0.13 | Jy km/s | 2 | This corresponds to an integrated line flux of 1.44$\pm$0.13 Jy kms$^{-1}$ |
| OH velocity shift relative to [CII] | -109 | 19 | km/s | 2 | The central velocity of the feature is shifted by –109$\pm$19 kms$^{-1}$ relative to the [CII] line. |
| AzTEC-3 [CII] deconvolved size | 3.9 x 2.1 | 0.63"+0.09/-0.09 x 0.34"+0.10/-0.15 | kpc^2 | 2 | we find a deconvolved [CII] source size of 0.63$''$$^{+0.09''}_{-0.09''}$$\times$0.34$''$$^{+0.10''}_{-0.15''}$ (3.9$\times$2.1 kpc$^2$ |
| AzTEC-3 L_FIR | 1.10e13 | +0.22/-0.21 e13 | Lsun | 3 | (1.10$^{+0.22}_{-0.21}$)$\times$10$^{13}$ $L_{\odot}$ |
| AzTEC-3 T_dust (optically thick) | 88.4 | +9.8/-9.6 | K | 3 | $T_{\rm dust}$=88.4$^{+9.8}_{-9.6}$ K |
| AzTEC-3 dust mass | 2.66e8 | +0.74/-0.80 e8 | Msun | 3 | $M_{\rm dust}$=2.66$^{+0.74}_{-0.80}$$\times$10$^8$ $M_{\odot}$ |
| AzTEC-3 Sigma_SFR | 530 | not stated | Msun/yr/kpc^2 | 5 | we find a high star formation rate surface density of $\Sigma_{\rm SFR}$=530 $M_{\odot}$ yr$^{-1}$ kpc$^{-2}$ |
| AzTEC-3 [CII] dynamical mass | 9.7e10 | not stated | Msun | 5 | implying a dynamical mass of 9.7$\times$10$^{10}$ $M_{\odot}$ |
| LBG-1 FIR SFR upper limit | <18–54 | not stated | Msun/yr | 4 | suggesting far-infrared SFRs of $<$18–54 $M_{\odot}$ yr$^{-1}$ |
| LBG-1 UV SFR | 22 | not stated | Msun/yr | 4 | This yields SFR$_{\rm UV}$=22 $M_{\odot}$ yr$^{-1}$. |
| LBG-1 [CII] size | 7.5 x 5.9 | not stated | kpc^2 | 2 | (7.5$\times$5.9 kpc$^2$; Tab. [2](#t2)) |
| AzTEC-3 dust optical depth at 157.7 µm | 1.28 | 0.04 | dimensionless | 3 | $\tau_{\rm 157.7\,{\mu}m}$=1.28$\pm$0.04 |

## Qualitative findings

- OH emission slightly blueshifted relative to [CII], possibly a molecular outflow  
  > "We find that the OH emission is slightly blueshifted relative to the \[CII\] line, which may indicate a molecular outflow" (abstract)
- LBG-1 SED resembles dwarf galaxies, not spirals/starbursts  
  > "The spectral energy distribution of these galaxies is inconsistent with nearby spiral and starburst galaxies, but resembles those of dwarf galaxies." (abstract)

## Claim tuples

- H: Is AzTEC-3 a compact maximum starburst? | E: Measure [CII] and continuum sizes and L_FIR | R: [CII] 3.9 kpc, Sigma_SFR=530 Msun/yr/kpc^2 | F: Star formation approaches the Eddington limit for radiation-pressure supported disks | **supported**
- H: Can ALMA detect [CII] in 'typical' z>5 galaxies? | E: Image [CII] and continuum toward the LBGs | R: [CII] resolved over 7.5 kpc in LBG-1, no continuum | F: ALMA can detect ISM in typical galaxies at z>5 | **supported**
- H: Does AzTEC-3 host an outflow? | E: Compare OH and [CII] velocities | R: OH shifted by -109±19 km/s | F: May indicate molecular outflow; better data needed | **partially**

## Reasoning

- Why this data: _not stated_
- Why this method: [CII] is an ideal tracer of ISM distribution, dynamics and enrichment out to the most distant galaxies  
  > "It thus is an ideal tracer for the distribution, dynamics, and enrichment of the ISM out to the most distant galaxies" (1 Introduction)
- Alternative: Optically thin SED fit rejected in favour of optically thick (better chi2)  
  > "suggesting a significantly better fit than in the optically-thin case" (3.4 SED, AzTEC-3)
- How they decided it was enough: _not stated_
- Limitation (authors): Spatial resolution insufficient to resolve structure; higher resolution needed  
  > "Observations at higher spatial resolution are required to further resolve the detailed structure of the interstellar medium in this massive starburst galaxy." (3.2 [CII] Line Emission)
- Limitation (authors): Photometric uncertainties near the SED peak are large  
  > "the uncertainties on the photometry close to the peak of the SED are $>$30%–50%" (3.4 SED, AzTEC-3)
- Caveat (inferred, ours): Dynamical masses rely on virial coefficient and size definitions with large size uncertainties
- Caveat (inferred, ours): L_FIR for LBGs depends on template choice and scaling
- Caveat (inferred, ours): Dust optical depth effects on L_CII not corrected
- Caveat (inferred, ours): Tentative velocity gradients are near beam scale

## Reproducibility

- Data public (paper): ALMA project 2011.0.00064.S acknowledged; Cycle 0 data  
  > "This paper makes use of the following ALMA data: ADS/JAO.ALMA# 2011.0.00064.S." (Acknowledgments)
- Products in archive: _not stated_
- Code: SED fitting code mbb_emcee on GitHub  
  > "https://github.com/aconley/mbb_emcee" (Footnote 8)
- Missing: Imaging parameters (mask, threshold, cell, size)
- Missing: Software versions
- Missing: Details of spectral extraction regions
- Missing: SED templates and photometry tables not included
- Missing: MCMC settings
- Data volume (inferred): ~50-100 GB raw for 5 Cycle 0 tracks
- Score (inferred): 3/5, Data are public and the analysis is moderately described, but imaging and fitting details are missing and photometry comes from other papers.
- Rediscovery candidate: no, Imaging settings and SED inputs are incompletely stated, so the recipe cannot be redone from the paper alone.

## Links

- Method: Riechers et al. (cite: rie13); Dowell et al. (cite: dow14) (MCMC SED fitting method)
- Companion: Riechers et al. 2010 (R10) (CO detections of AzTEC-3)
- Companion: Capak et al. 2011 (C11) (Discovery of the protocluster and optical properties)
- Related: COSMOS
- Related: AzTEC 1.1 mm COSMOS survey

## Checks

```json
{
 "quotes": 88,
 "quotes_ok": 88,
 "quote_pass_rate": 1.0,
 "quotes_too_long": 0,
 "unsupported_facts": 0,
 "project_codes": 1,
 "codes_not_in_text": [],
 "codes_not_in_obscore": [],
 "obscore_codes_not_in_card": [],
 "codes_printed_but_missing": [],
 "numeric_results": 18,
 "numeric_problems": 0,
 "fill": {
  "facts": 90,
  "stated": 62,
  "rate": 0.689
 },
 "evidence_ok": true
}
```
