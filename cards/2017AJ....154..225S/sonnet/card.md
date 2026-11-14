# ALMA 1.3 mm Map of the HD 95086 System

`2017AJ....154..225S` | The Astronomical Journal 2017 | first author: Su, Kate Y. L. | arXiv: 1709.10129 | DOI: 10.3847/1538-3881/aa906b

Card schema 1.0 | model claude-sonnet-5-5 | depth full | type observational_alma_primary

## Science

- Fields: debris_disks, exoplanets
- Question: Where is the Kuiper-belt analog (cold planetesimal disk) of HD 95086 located and how broad is it; what is the nature of the bright source near the ring; what constraints follow for planet b  
  > "The location of the Kuiper-belt analog is resolved for the first time." (abstract); "We set constraints on the orbital properties of planet b assuming co-planarity with the observed disk." (abstract)
- Target **HD 95086**: coordinates RA 10:57:02.91 Dec –68:40:02.27 (J2000), phase center  
  > "phase center RA: 10:57:02.91 Dec: –68:40:02.27 (J2000)" (Observations); "the Gaia DR1 catalog gives a slightly closer distance, 83.8$\pm$1.9 pc (cite: gaia16), which we adopt throughout the paper." (Introduction); z/distance 83.8±1.9 pc  
  > "phase center RA: 10:57:02.91 Dec: –68:40:02.27 (J2000)" (Observations); "the Gaia DR1 catalog gives a slightly closer distance, 83.8$\pm$1.9 pc (cite: gaia16), which we adopt throughout the paper." (Introduction); distance from Gaia DR1 (cite: gaia16)  
  > "phase center RA: 10:57:02.91 Dec: –68:40:02.27 (J2000)" (Observations); "the Gaia DR1 catalog gives a slightly closer distance, 83.8$\pm$1.9 pc (cite: gaia16), which we adopt throughout the paper." (Introduction)

## Data provenance

- ALMA projects: 2013.1.00773.S, 2013.1.00612.S
- bands: Band 6 (1.3 mm)  
  > "We observed HD 95086 with ALMA in Band 6 (1.3 mm) under two projects" (Observations)
- frequencies and spectral setup: 3840 channels over 1.875 GHz covering 12CO J=2-1; basebands at 215, 217, 230, 232.5 GHz (set A) and 231.87, 232.55, 245, 247 GHz (set B)  
  > "The four basebands were centered at 215, 217, 230 and 232.5 GHz for data set A, but at 231.87, 232.55, 245, 247 GHz for data set B." (Observations)
- continuum bandwidth: _not stated_
- arrays: 12 single-pointing executions, 35–39 antennae  
  > "The observations consist of 12 single pointing block executions centered at HD 95086" (Observations)
- configurations: _not stated_
- baselines: 15.1–348.5 m  
  > "15.1 – 348.5" (Table 1)
- angular resolution: combined beam 1.22"×1.03", P.A. 77.4°  
  > "The combined continuum map has a synthesized beam of 1.22$''$$\times$1.03$''$ and a P.A. of 77.4$^\circ$" (3.1 Continuum Emission)
- max recoverable scale: _not stated_
- sensitivity: rms 8.7 (A), 11.0 (B), 7.5 (combined) μJy/beam  
  > "and a rms of 7.5 $\mu$Jy beam$^{-1}$" (3.1 Continuum Emission)
- time on source: 4.58 h (A), 4.54 h (B)  
  > "The total on-source integration time is 4.58 hours for data set A, and 4.54 hours for data set B." (Observations)
- observing dates: Jan 2015 and April/May 2015  
  > "The majority of the observations were obtained in April/May 2015, while one was done in January 2015." (Observations)
- pi or archival as stated: Two projects, PI Su (A) and PI Booth (B)  
  > "#2013.1.00773.S, PI: Su (referred to as data set A)" (Observations)
- Line: 12CO J=2-1 (230.538 GHz)
- Other facility **APEX/LABOCA**: re-reduced 870 μm archive data giving 3σ upper limit of 33 mJy  
  > "Due to the large offset, we consider it as a non-detection and use 33 mJy as the 3 $\sigma$ upper limit." (4.1 Revised 3-Component SED Model)
- Other facility **Herschel / Spitzer**: far- and mid-infrared photometry used in the SED  
  > "(cite: su15) examined the resolved disk images of HD 95086 from *Herschel*" (4.1 Revised 3-Component SED Model)
- External data: Distance 83.8±1.9 pc  
  > "the Gaia DR1 catalog gives a slightly closer distance, 83.8$\pm$1.9 pc (cite: gaia16)" (Introduction) [from (cite: gaia16)]
- External data: Planet b orbital parameters  
  > "The most recent orbital parameters for HD 95086 b are from (cite: rameau16)" (4.4 Constraints for the HD 95086 b from the Disk Perspective) [from (cite: rameau16)]
- External data: Schechter function parameters for background galaxy counts  
  > "Using the parameters of the Schechter function in (cite: carniani15)" (4.3.4 Alignment of a Background Galaxy) [from (cite: carniani15)]
- External data: CO upper limits and gas mass limits  
  > "(Booth et al. in prep.)" (4.3.1 Debris Phase of a Circumplanetary Disk?) [from Booth et al. in prep.]

## Processing

### Calibration

- pipeline or manual: Calibrated with ALMA-provided scripts; processed by ARCs  
  > "We generated the calibrated measurement sets using the scripts provided by the ALMA project for each of the data sets." (3.1 Continuum Emission)
- casa version: CASA 4.2.2 (set A), 4.3.1 (set B)  
  > "CASA package (ver. 4.2.2 for data set A and ver. 4.3.1 for data set B)" (Observations)
- pipeline version: _not stated_
- archive products used as is: _not stated_
- flux calibrator: Quasars (J1107), Callisto, Ganymede, Titan  
  > "Nearby quasars and solar system objects (Callisto and Ganymede) were used for flux calibration" (Observations)
- flux scale uncertainty: ≲10%  
  > "resulting in an absolute flux uncertainty $\lesssim$10 %" (Observations)
- self calibration: _not stated_

### Imaging

- task: MIRIAD invert/clean/restore  
  > "Visibilities were then inverted with natural weighting, deconvolved, and restored to generate a final synthesized map using the standard procedures in MIRIAD." (3.1 Continuum Emission)
- deconvolver: _not stated_
- weighting robust: natural weighting  
  > "Visibilities were then inverted with natural weighting" (3.1 Continuum Emission)
- uv taper: _not stated_
- cell size: 0.2" per pixel  
  > "(0.2$''$ per pixel)" (3.3 Imaging Plane Modeling Approach)
- image size: _not stated_
- masking: _not stated_
- multiscale scales: _not stated_
- continuum subtraction: _not stated_
- line free channels: _not stated_
- primary beam correction: _not stated_
- array combination: _not stated_
- smoothing: time binned to 30 s, spectral channels averaged by 128  
  > "binning the time sampling to 30 s and averaging the spectral channels with a width of 128 channels" (3.1 Continuum Emission)
- final beam: 1.22"×1.03" PA 77.4° (combined)  
  > "synthesized beam of 1.22$''$$\times$1.03$''$ and a P.A. of 77.4$^\circ$" (3.1 Continuum Emission)
- final rms: 7.5 μJy/beam  
  > "a rms of 7.5 $\mu$Jy beam$^{-1}$" (3.1 Continuum Emission)

### Inherited from earlier work

- Visibility MCMC fitting approach  
  > "adopting the MCMC approach outlined in (cite: macgregor13)" (3.2 Visibilities Modeling Approach) [from (cite: macgregor13)]
- Image-plane fitting approach  
  > "Details about this approach can be found in (cite: booth16)." (3.3 Imaging Plane Modeling Approach) [from (cite: booth16)]
- SED grain parameters and approach  
  > "Using similar approaches and grain parameters as in (cite: su15)" (4.1 Revised 3-Component SED Model) [from (cite: su15)]
- APEX/LABOCA re-reduction technique  
  > "using the techniques described in (cite: phillips11)" (4.1 Revised 3-Component SED Model) [from (cite: phillips11)]
- Chaotic zone formulas  
  > "We adopt the numerically derived formula from (cite: morrison15)" (4.4 Constraints for the HD 95086 b from the Disk Perspective) [from (cite: morrison15)]

### Not stated but needed to reproduce (our reading)

- MCMC sampler details, number of walkers/steps, burn-in
- Details of the image-plane noise-correlation factor
- uv-range and weighting in the MIRIAD imaging beyond natural
- Flux scale handling when combining sets A and B
- Whether uvmodelfit initial guesses were used
- SED model code and photometry table
- Spectral index map method
- CO data processing (deferred to Booth et al. in prep.)

## Analysis recipe

1. **Produce continuum images**: Split, bin to 30 s and 128 channels, export to FITS, MIRIAD invert with natural weighting, clean, restore; sets A, B and combined  
  > "These averaged, binned $uv$ visibilities were then exported to FITS format for further analysis using the MIRIAD software" (3.1 Continuum Emission)
   - software: CASA, MIRIAD
   - fitting: _not stated_
   - validation: _not stated_
2. **Fit disk and point source in visibilities**: MCMC fit of two-boundary power-law disk or Gaussian ring plus point source to both data sets simultaneously, with model-minus-data residual imaging  
  > "We model the visibilities for both data sets simultaneously." (3.2 Visibilities Modeling Approach)
   - software: MIRIAD
   - parameter: 8/9 free parameters; disk centered on star  
  > "there are a total of eight/nine free parameters to describe the system in both axi-symmetric disk models" (3.2 Visibilities Modeling Approach)
   - assumption: Optically and geometrically thin disk; Td = 278.3 L*^0.25 r^-0.5; L* = 6 Lsun; d = 83.8 pc  
  > "we expect the dust temperatures follow $T_d(r) = 278.3 L_{\ast}^{0.25}
r^{-0.5}$" (3.1 Continuum Emission)
   - fitting: MCMC, uniform priors, flux>0 and Rout>Rin  
  > "For all parameters, we assume uniform priors and require that the model be physically plausible" (3.2 Visibilities Modeling Approach)
   - validation: Residual maps within ±3σ for main disk; reduced chi-squared  
  > "Overall, the residuals are within $\pm$3$\sigma$ for the main disk." (3.2 Visibilities Modeling Approach)
3. **Fit disk in image plane**: MCMC fit to combined dirty map with ring center free; correlated-noise factor sqrt(beam pixels)  
  > "A factor equivalent to the square root of the beam size in pixels is included to mitigate the correlated noise" (3.3 Imaging Plane Modeling Approach)
   - fitting: MCMC  
  > "We use the combined synthesized map for the MCMC search." (3.3 Imaging Plane Modeling Approach)
   - validation: Compared with visibility results  
  > "the best-fit parameters agree with the ones derived from the visibilities method within the uncertainties" (3.3 Imaging Plane Modeling Approach)
4. **Characterize point sources and minimize contamination**: Long-baseline (>80 kλ) map, uvmodelfit of two point sources, subtraction to make disk-only map, refit with fixed sources, masking >0.1 mJy/beam, or Gaussian source  
  > "The properties (offset and flux density) of the two point sources are determined using ’uvmodelfit’ in CASA" (3.4 Best-Fit Disk Parameters by Minimizing Other Contamination)
   - software: CASA
   - fitting: _not stated_
   - validation: Tested thresholds 60–80 kλ; compared per-data-set fluxes  
  > "we also generated the long baseline maps with different thresholds between 60 to 80 $k\lambda$" (3.4 Best-Fit Disk Parameters by Minimizing Other Contamination)
5. **Radial and azimuthal profiles and SED, bright source nature, planet constraints**: Elliptical annuli of 0.4" and 27° wedges; revised SED model; background galaxy probabilities from Schechter function; chaotic zone width formulas  
  > "we first created a series of elliptical rings with a width of 2 pixels (0.4$''$) centered at the star" (4.2 Ring Width and Azimuthal Asymmetry)
   - assumption: Dust opacity 2.3 cm2/g at 1.3 mm, Td 30–60 K for CPD; M*=1.6 Msun  
  > "$\kappa_{1.3mm}$= 2.3 cm$^2$g$^{-1}$ (cite: beckwith90) and dust temperatures of 30–60 K" (4.3.1 Debris Phase of a Circumplanetary Disk?)
   - fitting: _not stated_
   - validation: _not stated_

## Software

- **CASA** 4.2.2 / 4.3.1: ARC calibration, splitting, uvmodelfit  
  > "determined using ’uvmodelfit’ in CASA" (3.4 Best-Fit Disk Parameters by Minimizing Other Contamination)
- **MIRIAD** : imaging of visibilities and residuals  
  > "using the standard procedures in MIRIAD" (3.1 Continuum Emission)

## Numeric results

| quantity | value | uncertainty | units | step | quote |
|---|---|---|---|---|---|
| Total disk flux density at 1.3 mm | 2.79 | 0.1 | mJy | 4 | The disk has a total flux density of 2.79$\pm$0.1 mJy at 1.3 mm |
| Disk inclination | 30 | 3 | deg | 4 | is inclined by 30$^\circ$$\pm$3$^\circ$ from face-on with a P.A. of 97$^\circ$$\pm$3$^\circ$ |
| Disk position angle | 97 | 3 | deg | 4 | with a P.A. of 97$^\circ$$\pm$3$^\circ$ |
| Two-boundary Rin | 106 | 5 | au | 4 | $R_{in}=$106$\pm$5 au and $R_{out}=$320$\pm$10 au |
| Two-boundary Rout | 320 | 10 | au | 4 | $R_{in}=$106$\pm$5 au and $R_{out}=$320$\pm$10 au |
| Surface density index | –0.5 | 0.3 | dimensionless | 4 | surface density power index of –0.5$\pm$0.3 |
| Gaussian ring peak radius | 200 | 6 | au | 4 | $R_p=$200$\pm$6 au with a width of $R_w=$168$\pm$7 au |
| Gaussian ring FWHM | 168 | 7 | au | 4 | $R_p=$200$\pm$6 au with a width of $R_w=$168$\pm$7 au |
| Reduced chi-squared (two-boundary / Gaussian ring) | 1.20 / 1.15 | not stated | dimensionless | 4 | The reduced chi-squared ($\chi^2$) is 1.20 for the two-boundary model, but 1.15 for the Gaussian ring model |
| Bright point source flux (long baseline) | 0.81 | 0.03 | mJy | 4 | 0.81 $\pm$0.03 |
| Faint source flux | 0.10 | 0.02 | mJy | 4 | 0.10$\pm$0.02 |
| Bright source spectral index | 3.0–4.0 | not stated | dimensionless | 5 | The bright source has a spectral index of 3.0$\sim$4.0 derived from the combined data. |
| Eccentricity limit for shepherding planet | <0.17 | not stated | dimensionless | 5 | The non-detection of an offset suggests $e<0.17$ for the shepherding planet |

## Qualitative findings

- Bright source is most likely a background dusty galaxy, not physically associated  
  > "more likely due to chance alignment of a background source" (Conclusion)
- Apparent east-west disk asymmetry not significant  
  > "the apparent asymmetry is not significant" (4.2 Ring Width and Azimuthal Asymmetry)

## Claim tuples

- H: Can the cold planetesimal disk be resolved and located at mm wavelengths | E: MCMC fits of two disk models to visibilities and image | R: Rin=106±5, Rout=320±10 au; ring peak 200±6 au; i=30±3° | F: Broad ring resolved for the first time | **supported**
- H: Is the bright source associated with the system | E: Compared CPD, impact, resonance clump and background galaxy scenarios using flux, CO limits, spectral index, SED | R: Steep index 3–4, SED consistent with z=2 DSFG, chance alignment probability small but nonzero | F: Likely background galaxy | **partially**
- H: Can planet b shepherd the disk inner edge | E: Chaotic zone calculation with coplanarity | R: Outer chaotic zone edge 70–82 au vs disk edge 106 au; e~0.29 needed | F: Needs eccentric orbit, non-coplanarity, or an additional 0.2–1.5 MJup planet | **partially**

## Reasoning

- Why this data: _not stated_
- Why this method: Both visibility and image-plane fitting used; image-plane uncertainties considered less robust  
  > "we caution against relying on the robustness of the uncertainties using imaging plane fitting" (3.3 Imaging Plane Modeling Approach)
- Alternative: Circumplanetary disk, giant impact clump, resonant planetesimal clump rejected as origin of bright source  
  > "it is unlikely to have resulted from a structure physically assocated with the system (the first three scenarios)" (Conclusion)
- How they decided it was enough: _not stated_
- Limitation (authors): Disk width only resolved by ~1.7 beams so density distribution and star-disk offset cannot be determined  
  > "As a result, we cannot determine the exact disk density distribution nor the offset between the star and disk center." (3.4 Best-Fit Disk Parameters by Minimizing Other Contamination)
- Limitation (authors): Bright source cannot be cleanly separated from the disk  
  > "The subtraction of the bright source is far from perfect." (3.4 Best-Fit Disk Parameters by Minimizing Other Contamination)
- Caveat (inferred, ours): Disk parameter uncertainties depend on how the bright source is treated
- Caveat (inferred, ours): Background-galaxy identification rests on statistics and sparse SED, no redshift
- Caveat (inferred, ours): Two data sets combined with different spectral setups
- Caveat (inferred, ours): Model comparison by chi-squared with correlated parameters is weak

## Reproducibility

- Data public (paper): Data from ALMA projects acknowledged with ADS/JAO.ALMA codes  
  > "This paper makes use of the following ALMA data: ADS/JAO.ALMA #2013.1.00773.S and #2013.1.00612.S." (Acknowledgments)
- Products in archive: _not stated_
- Missing: MCMC code and settings
- Missing: SED model code and photometry
- Missing: Details of CO analysis
- Data volume (inferred): ~100–200 GB raw for 12 executions; tens of GB calibrated
- Score (inferred): 3/5, Public data and clear model definitions, but MCMC setup and codes are not given.
- Rediscovery candidate: yes, Public data, recipe mostly specified, numeric disk parameters; some details missing.

## Links

- Method: (cite: macgregor13) (Visibility MCMC fitting)
- Method: (cite: booth16) (Image-plane fitting)
- Companion: (cite: su15) (Previous SED and Herschel analysis)
- Companion: Booth et al. in prep. (CO gas analysis)

## Checks

```json
{
 "quotes": 80,
 "quotes_ok": 80,
 "quote_pass_rate": 1.0,
 "quotes_too_long": 0,
 "unsupported_facts": 0,
 "project_codes": 2,
 "codes_not_in_text": [],
 "codes_not_in_obscore": [],
 "obscore_codes_not_in_card": [],
 "codes_printed_but_missing": [],
 "numeric_results": 13,
 "numeric_problems": 0,
 "fill": {
  "facts": 79,
  "stated": 56,
  "rate": 0.709
 },
 "evidence_ok": true
}
```
