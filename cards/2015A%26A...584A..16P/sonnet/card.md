# Testing particle trapping in transition disks with ALMA

`2015A&A...584A..16P` | Astronomy and Astrophysics 2015 | first author: Pinilla, P. | arXiv: 1509.03040 | DOI: 10.1051/0004-6361/201526655

Card schema 1.0 | model claude-sonnet-5-5 | depth full | type observational_alma_primary

## Science

- Fields: protoplanetary_disks
- Question: Do ALMA Band 7 and Band 9 morphology and spectral index of SR 21 and HD 135344B support particle trapping (radial or vortex) as the origin of cavities and asymmetries?  
  > "With the new ALMA observations of SR 21 and HD 135344B, it is possible to test whether radial/azimuthal trapping is the cause of disk structures (cavities and asymmetries)." (Discussion)
- Target **SR 21**: coordinates _not stated_; z/distance 120 pc  
  > "SR 21 is a G3 star located in the Ophiuchus star-forming region at a distance of $d=120$ pc (cite: loinard2008)." (Targets and observations); distance from loinard2008  
  > "SR 21 is a G3 star located in the Ophiuchus star-forming region at a distance of $d=120$ pc (cite: loinard2008)." (Targets and observations)
- Target **HD 135344B**: coordinates _not stated_; z/distance 140 pc  
  > "HD 135344B is an F4 star located in the Sco OB2-3 star-forming region at a distance of $d=140$ pc (cite: boekel2005)." (Targets and observations); distance from boekel2005  
  > "HD 135344B is an F4 star located in the Sco OB2-3 star-forming region at a distance of $d=140$ pc (cite: boekel2005)." (Targets and observations)

## Data provenance

- ALMA projects: 2011.0.00724.S, 2012.1.00158.S
- bands: Band 9 (689 GHz, ~450 um) and Band 7 (336 GHz, ~870 um)  
  > "taken in Band 9 and Band 7, respectively" (Targets and observations)
- frequencies and spectral setup: _not stated_
- continuum bandwidth: _not stated_
- arrays: _not stated_
- configurations: _not stated_
- baselines: _not stated_
- angular resolution: 0.27" common beam  
  > "which is the best possible beam size corresponding to both the Band 7 and Band 9 observations (0.27”)" (Targets and observations)
- max recoverable scale: _not stated_
- sensitivity: rms 0.08 and 2.0 mJy (SR 21 B7, B9); 0.13 and 2.5 mJy (HD 135344B B7, B9)  
  > "| HD 135344B | $7$ | $336$ | $3.2$ | $69.1$ | 636 | $0.13$ | 27/07/2014 |" (Table 1)
- time on source: _not stated_
- observing dates: Band 9: July 2012; Band 7: July 2014 (Table 1)  
  > "| SR 21 | $7$ | $336$ | $3.2$ | $42.4$ | 349 | $0.08$ | 26/07/2014 |" (Table 1)
- pi or archival as stated: Cycle 0 PI Pérez; Cycle 1 PI van Dishoeck  
  > "Cycle 0 program 2011.0.00724.S (P.I. Pérez) and Cycle 1 program 2012.1.00158.S (P.I. van Dishoeck)" (Targets and observations)
- External data: Disk inclination and PA for deprojection (SR 21 i=15 deg, PA=14 deg; HD 135344B i=20 deg, PA=63 deg)  
  > "as derived in (cite: pontoppidan2008) and (cite: marel2015)" (3.1 Visibilities and disk morphology) [from pontoppidan2008; marel2015]
- External data: Proper motions of the stars  
  > "The proper motion is -12,-24 mas yr$^{-1}$ for SR 21 (cite: Makarov2007) and -20,-24 mas yr$^{-1}$ for HD 135344B (cite: Hog2000)." (Targets and observations) [from Makarov2007; Hog2000]
- External data: Disk masses and gas surface density near cavity from CO isotopologues  
  > "the disk mass of SR 21 has been inferred to be ${\sim}12~M_{\rm{Jup}}$, and the average value of the gas surface density close to the cavity is ${\sim}80~\rm{g~cm}^{-2}$ (cite: marel2015)" (Discussion) [from marel2015]
- Simulation/model as data: Hydrodynamic simulation of a 1 M_Jup planet at 20 AU plus dust evolution models (alpha_visc=1e-3), used to predict intensity and alpha_mm profiles at 1 and 5 Myr  
  > "The gas surface density is obtained from hydrodynamical simulations of a $1~M_{\rm{Jup}}$ planet embedded in the disk at 20 AU distance from the star as in (cite: pinilla2012)." (4 Theoretical predictions of particle trapping)

## Processing

### Calibration

- pipeline or manual: _not stated_
- casa version: _not stated_
- pipeline version: _not stated_
- archive products used as is: _not stated_
- flux calibrator: _not stated_
- flux scale uncertainty: ~20% Band 9, ~10% Band 7  
  > "calibration uncertainties (${\sim}$20% and ${\sim}$10% in Band 9 and 7, respectively)" (3.2 Spectral index)
- self calibration: _not stated_

### Imaging

- task: _not stated_
- deconvolver: _not stated_
- weighting robust: Briggs, robust = 0.5  
  > "the images were obtained using Briggs weighting with a robust parameter of 0.5" (Targets and observations)
- uv taper: _not stated_
- cell size: _not stated_
- image size: _not stated_
- masking: _not stated_
- multiscale scales: _not stated_
- continuum subtraction: _not stated_
- line free channels: _not stated_
- primary beam correction: _not stated_
- array combination: _not stated_
- smoothing: Images convolved to same beam in post-processing  
  > "the beam is set to be the same at both bands by the post-processing of the images" (Targets and observations)
- final beam: 0.27"  
  > "(0.27”)" (Targets and observations)
- final rms: _not stated_

### Inherited from earlier work

- Calibration of the data  
  > "The details of the calibration are described in (cite: perez2014) and van der Marel et al. (submitted)." (Targets and observations) [from (cite: perez2014); van der Marel et al. (submitted)]
- Ring and ring+vortex morphological models and MCMC fitting approach  
  > "we used the same morphological models described in (cite: perez2014)" (3.1 Visibilities and disk morphology) [from (cite: perez2014)]
- Inclination and PA fixed to Pérez et al. values in MCMC  
  > "the inclination and P.A. are fixed to the values found by (cite: perez2014) for both disks" (3.1 Visibilities and disk morphology) [from (cite: perez2014)]

### Not stated but needed to reproduce (our reading)

- CASA version and calibration details (deferred to other papers)
- MCMC sampler, priors, walkers and chains
- How the pixel-by-pixel spectral index maps were regridded/aligned
- Band 7 and 9 flux calibrators
- Dust opacity assumptions for Stokes number estimates and the model intensity computation
- Model parameters beyond those in the text (temperature, stellar parameters)

## Analysis recipe

1. **Image continuum at matched resolution**: Briggs weighted imaging, convolved to common 0.27" beam; Band 7 centre shifted for proper motion  
  > "the centre of the 2014 data was shifted before overlaying the images to compensate for the proper motion of the stars" (Targets and observations)
   - parameter: robust = 0.5  
  > "Briggs weighting with a robust parameter of 0.5" (Targets and observations)
   - fitting: _not stated_
   - validation: Gain calibrator position shifts ≲0.1 mas, so azimuthal shift not due to calibration  
  > "The position of the gain calibrator (the same for both observations) shifts $\lesssim$0.1 mas" (Targets and observations)
2. **Deprojected, binned visibility profiles**: Real and imaginary visibilities deprojected and binned in 20 kλ bins with ≥5 points per bin; null location compared  
  > "The data are binned by taking the mean of the available data points in bins of 20 k$\lambda$, with a minimum of five data points per bin." (3.1 Visibilities and disk morphology)
   - parameter: SR 21 i=15 deg, PA=14 deg; HD 135344B i=20 deg, PA=63 deg  
  > "$i=15^{\circ}$ and position angle P.A.=14$^{\circ}$ for SR 21, and $i=20^{\circ}$ and P.A.=63$^{\circ}$" (3.1 Visibilities and disk morphology)
   - fitting: _not stated_
   - validation: _not stated_
3. **Fit ring and ring+vortex models to visibilities**: Minimise chi^2 with MCMC for Gaussian ring and ring+azimuthal-Gaussian vortex models  
  > "The parameters of the best-fit model are found by minimising $\chi^2$ using the same Markov Chain Monte Carlo (MCMC) approach implemented by (cite: perez2014)." (3.1 Visibilities and disk morphology)
   - assumption: Inclination and PA fixed  
  > "the inclination and P.A. are fixed to the values found by (cite: perez2014) for both disks" (3.1 Visibilities and disk morphology)
   - fitting: chi^2 minimisation via MCMC; sampler and priors not stated  
  > "The parameters of the best-fit model are found by minimising $\chi^2$ using the same Markov Chain Monte Carlo (MCMC) approach implemented by (cite: perez2014)." (Data analysis, Visibilities and disk morphology)
   - validation: Residual maps after subtracting best-fit models  
  > "The residuals obtained by subtracting the best-fit model from the data in Band 7 are shown for both targets in Appendix [7]" (3.1 Visibilities and disk morphology)
4. **Compute spectral index map**: alpha_mm = ln(F_B7/F_B9)/ln(nu_B7/nu_B9) per pixel, F<5 sigma excluded; error propagation including calibration  
  > "All data with $F<5\sigma$ are excluded." (3.2 Spectral index)
   - parameter: 5 sigma cut; calibration uncertainty 20% and 10%  
  > "All data with $F<5\sigma$ are excluded." (3.2 Spectral index)
   - fitting: _not stated_
   - validation: Images shifted by 20 mas to test robustness of azimuthal variations  
  > "Figure [7](#shifts) shows $\alpha_{\rm{mm}}$ by shifting 20 mas in both vertical and horizontal direction." (Uncertainties in the azimuthal variations of the spectral index)
5. **Compare with particle-trapping model predictions**: Model intensity and alpha_mm profiles at 450 and 870 um at 1 and 5 Myr convolved with 35 AU Gaussian; Stokes numbers estimated  
  > "convolved with a 2D Gaussian profile of 35 AU diameter" (4 Theoretical predictions of particle trapping)
   - parameter: 1 M_Jup planet at 20 AU, alpha_visc=1e-3  
  > "the disk viscosity is taken to be $\alpha_{\rm{visc}}=10^{-3}$" (4 Theoretical predictions of particle trapping)
   - assumption: Grains of maximum size ≲3λ traced at each wavelength  
  > "Assuming that at each wavelength, particles with a maximum size of $\lesssim3\lambda$ are traced (cite: draine2006)" (Discussion)
   - fitting: _not stated_
   - validation: Optically thick alternative tested via brightness temperature argument  
  > "the ring must be very narrow ($\lesssim$3 AU in width)" (Discussion)

## Software


## Numeric results

| quantity | value | uncertainty | units | step | quote |
|---|---|---|---|---|---|
| SR 21 visibility null Band 9 | ~220 | not stated | kλ | 2 | The nulls for SR 21 are ${\sim}$220 k$\lambda$ at Band 9 and ${\sim}$250 k$\lambda$ at Band 7. |
| SR 21 visibility null Band 7 | ~250 | not stated | kλ | 2 | The nulls for SR 21 are ${\sim}$220 k$\lambda$ at Band 9 and ${\sim}$250 k$\lambda$ at Band 7. |
| HD 135344B visibility null | ~190 (both bands) | not stated | kλ | 2 | For HD 135344B the null is almost at the same position at both wavelengths (${\sim}$190 k$\lambda$). |
| SR 21 ring peak radius Band 7 vs Band 9 | ~41 vs ~36 | not stated | AU | 3 | $r_R{\sim}41$ AU at 870 $\mu$m vs. $r_R{\sim}36$ AU at 450 $\mu$m |
| SR 21 ring width Band 7 vs Band 9 | ~12 vs ~15 | not stated | AU | 3 | $\sigma_R{\sim}12$ AU at 870 $\mu$m vs. $\sigma_R{\sim}15$ AU at 450 $\mu$m |
| HD 135344B vortex aspect ratio Band 9 to Band 7 | 7.1 to 3.3 | not stated | dimensionless | 3 | decreases from 7.1 in Band 9 to 3.3 in Band 7 |
| SR 21 alpha_mm inside ~0.3" (35 AU) | 3.8-4.2 | ~0.3 systematic | dimensionless | 4 | $\alpha_{\rm{mm}}{\sim}3.8-4.2$ within ${\sim}$0.3” radius |
| SR 21 alpha_mm outside | 2.6-3.0 | ~0.3 systematic | dimensionless | 4 | $\alpha_{\rm{mm}}{\sim}2.6-3.0$ outside |
| HD 135344B alpha_mm range | 2.6-3.2 | not stated | dimensionless | 4 | the values remain within a range of $2.6-3.2$ |

## Qualitative findings

- Vortex scenario disfavoured for both disks; radial trapping supported for SR 21  
  > "suggest that anti-cyclonic vortices are not the origin of their low contrast azimuthal asymmetries" (Discussion)

## Claim tuples

- H: Is SR 21 cavity/ring consistent with radial particle trapping? | E: Compare Band 7/9 visibility nulls, ring fits and alpha_mm maps with trapping models | R: Ring narrower and further out at 870 um; alpha_mm ~3.8-4.2 inside 35 AU vs 2.6-3.0 outside | F: Consistent with radial trapping, formed ≲1 Myr ago | **supported**
- H: Are the azimuthal asymmetries vortices? | E: Compare ring vs vortex fits and vortex widths at two wavelengths | R: SR 21 best fit by ring; HD 135344B vortex widens at longer wavelength | F: Asymmetries likely not caused by vortices | **supported**
- H: Do radial alpha_mm variations in HD 135344B indicate trapping? | E: Spectral index map | R: No significant radial variation | F: Does not exclude trapping; could be older trap or finer structure | **partially**

## Reasoning

- Why this data: Two bands trace different grain sizes, allowing morphology and spectral index comparison  
  > "to compare the morphological structures at the two frequencies and calculate $\alpha_{\rm{mm}}$ throughout the disk" (Introduction)
- Why this method: _not stated_
- Alternative: Optically thick emission alone rejected: would require ring ≲3 AU wide  
  > "Thus, the radial variations of $\alpha_{\rm{mm}}$ cannot be due to optically thick emission alone." (Discussion)
- How they decided it was enough: _not stated_
- Limitation (authors): Azimuthal alpha_mm variations uncertain, depend on image alignment  
  > "any azimuthal variation within a range of $\alpha_{\rm{mm}}{\sim}eq 2.6-3.2$ remains uncertain" (3.2 Spectral index)
- Caveat (inferred, ours): Band 9 marginally optically thick, affecting alpha_mm
- Caveat (inferred, ours): Model is generic, not tuned to each disk
- Caveat (inferred, ours): MCMC details absent; errors omitted
- Caveat (inferred, ours): Resolution of 0.27" limits radial alpha_mm tests

## Reproducibility

- Data public (paper): Data cited by ALMA project codes (acknowledgement); public status not explicitly stated  
  > "This paper makes use of the following ALMA data: ADS/JAO.ALMA#2012.1.00158.S and #2011.0.00724.S." (Acknowledgements)
- Products in archive: _not stated_
- Missing: Calibration scripts/CASA version
- Missing: MCMC configuration
- Missing: Model simulation inputs and opacity details
- Missing: Image alignment procedure for alpha_mm maps
- Data volume (inferred): tens to hundreds of GB raw (two bands, two targets)
- Score (inferred): 3/5, Data identified and key settings given, but calibration, MCMC and model details are deferred or missing.
- Rediscovery candidate: no, Recipe relies on unpublished/inherited calibration and fitting details.

## Links

- Method: (cite: perez2014) (Morphological models, MCMC and calibration)
- Companion: (cite: marel2015) (Disk properties, CO masses, Band 7 data calibration)

## Checks

```json
{
 "quotes": 57,
 "quotes_ok": 57,
 "quote_pass_rate": 1.0,
 "quotes_too_long": 0,
 "unsupported_facts": 0,
 "project_codes": 2,
 "codes_not_in_text": [],
 "codes_not_in_obscore": [],
 "obscore_codes_not_in_card": [],
 "codes_printed_but_missing": [],
 "numeric_results": 9,
 "numeric_problems": 0,
 "fill": {
  "facts": 77,
  "stated": 42,
  "rate": 0.545
 },
 "evidence_ok": true
}
```
