# Extreme Dust Disks in Arp 220 as Revealed by ALMA

`2014ApJ...789L..36W` | The Astrophysical Journal Letters 2014 | first author: Wilson, C. D. | arXiv: 1406.4530 | DOI: 10.1088/2041-8205/789/2/L36

Card schema 1.0 | model claude-sonnet-5-5 | depth full | type observational_alma_primary

## Science

- Fields: nearby_galaxies, agn_and_quasars
- Question: What are the dust temperature, optical depth, size and luminosity surface density of the two Arp 220 nuclei at 434 um, and do they require an AGN or hot starburst?  
  > "We use these new data to derive more precise measurements of the dust temperature, source size, and luminosity for each nucleus" (Introduction)
- Target **Arp 220 (eastern and western nuclei)**: coordinates East (15:34:57.29, +23:30:11.3); West (15:34:57.22, +23:30:11.5) J2000  
  > "which at the redshift of Arp 220 (0.01813) corresponds to a rest frequency of 691.061 GHz (434 $\mu$m)" (Observations); "(15:34:57.29, +23:30:11.3)" (Table 1); "$D_L = 77.4$ Mpc, $D_A = 74.5$ Mpc" (Introduction); z/distance z = 0.01813; D_L = 77.4 Mpc, D_A = 74.5 Mpc  
  > "which at the redshift of Arp 220 (0.01813) corresponds to a rest frequency of 691.061 GHz (434 $\mu$m)" (Observations); "(15:34:57.29, +23:30:11.3)" (Table 1); "$D_L = 77.4$ Mpc, $D_A = 74.5$ Mpc" (Introduction); distance from _not stated_

## Data provenance

- ALMA projects: _none stated_
- bands: Band 9, CO J=6-5 and adjacent continuum  
  > "with the Band 9 receivers tuned to cover the CO J=6-5 transition and adjacent continuum" (Observations)
- frequencies and spectral setup: _not stated_
- continuum bandwidth: Two line-free regions: 1.375 GHz at 680.90 GHz and 1.6875 GHz at 676.75 GHz  
  > "We combined two line-free regions of the spectrum centered at 680.90 GHz ($\Delta\nu = 1.375$ GHz) and 676.75 GHz ($\Delta\nu = 1.6875$ GHz)" (Observations)
- arrays: _not stated_
- configurations: _not stated_
- baselines: 13 to 374 m projected  
  > "The observations covered projected baselines from 13 to 374 m." (Observations)
- angular resolution: 0.363x0.199 arcsec, PA 28.3 deg  
  > "has a beam of $0.363\times 0.199^{\prime\prime}$ at position angle 28.3$^o$" (Observations)
- max recoverable scale: _not stated_
- sensitivity: 1 sigma = 11 mJy/beam (0.41 K)  
  > "with a 1$\sigma$ noise level of 11 mJy beam$^{-1}$ (0.41 K)" (Observations)
- time on source: _not stated_
- observing dates: 2012 December 31  
  > "Arp 220 was observed with ALMA on 2012 December 31" (Observations)
- pi or archival as stated: _not stated_
- Line: CO J=6-5 (not stated)
- Other facility **Herschel**: Extrapolated global flux 5.9 +/- 0.9 Jy at 691 GHz (from Rangwala et al. 2011)  
  > "the extrapolated flux from the *Herschel* data is $5.9 \pm 0.9$ Jy (cite: r11)" (Optical depth, source size, and dust temperature)
- External data: 230 GHz nuclear fluxes  
  > "comparing our fluxes with previous measurements at 230 GHz from (cite: s99) and at 345 GHz from (cite: s08)" (Optical depth, source size, and dust temperature) [from (cite: s99)]
- External data: 345 GHz nuclear fluxes  
  > "Flux density (345 GHz)$^{d}$ | 191 | 370 | mJy" (Table 1) [from (cite: s08)]
- External data: Inclination 53.5 +/- 0.1 deg from 33 GHz fit  
  > "we also adopt the (deconvolved) inclination angle of $53.5^\circ \pm 0.1^\circ$ obtained by (cite: b14)" (Optical depth, source size, and dust temperature) [from (cite: b14)]
- External data: Synchrotron and free-free contamination of 230 GHz flux (west 2.7 and 10 mJy)  
  > "For the western nucleus, these fluxes are estimated to be 2.7 mJy and 10 mJy, respectively (cite: de07)" (Optical depth, source size, and dust temperature) [from (cite: de07)]
- External data: Dynamical masses of the nuclei from CO disk models  
  > "(cite: e11) model the CO emission as a thin rotating disk to obtain masses of $1.6 \times 10^9$ M$_\odot$ for the western nucleus within 100 pc" (Discussion) [from (cite: e11)]
- External data: Global luminosity log L = 11.95 +/- 0.03  
  > "giving a global luminosity $\log L = 11.95
\pm 0.03$ (cite: r11)" (Discussion) [from (cite: r11)]
- External data: Dust emissivity index 1.8 and tau250/N_H = 2.32e-25 cm^2  
  > "using the value of $\tau_{250\mu m}/N_H = 2.32
\times 10^{-25}$ cm$^2$ derived from Planck data (cite: p11)" (Gas and star formation in the Arp 220 nuclei) [from (cite: p11)]

## Processing

### Calibration

- pipeline or manual: _not stated_
- casa version: _not stated_
- pipeline version: _not stated_
- archive products used as is: _not stated_
- flux calibrator: Bandpass calibrator 3C279 (6.0 Jy measured during another observation within one day) used to set flux scale  
  > "the absolute flux scale had to be set using observations of the bandpass calibrator (3C279, measured to be 6.0 Jy during another observation taken within one day)" (Observations)
- flux scale uncertainty: no better than 15%  
  > "we estimate the absolute calibration accuracy to be no better than 15%." (Observations)
- self calibration: Two rounds of phase-only followed by one round of phase and amplitude  
  > "We applied two rounds of phase-only self-calibration followed by a final round of phase and amplitude self-calibration." (Observations)

### Imaging

- task: _not stated_
- deconvolver: _not stated_
- weighting robust: uniform weighting  
  > "The final image (Figure  [1](#image)) made using uniform weighting and $0.04^{\prime\prime}$ pixels" (Observations)
- uv taper: _not stated_
- cell size: 0.04 arcsec  
  > "made using uniform weighting and $0.04^{\prime\prime}$ pixels" (Observations)
- image size: _not stated_
- masking: _not stated_
- multiscale scales: _not stated_
- continuum subtraction: _not stated_
- line free channels: _not stated_
- primary beam correction: _not stated_
- array combination: _not stated_
- smoothing: 0.5 arcsec resolution image for flux comparison with Sakamoto et al. 2008  
  > "using an image with 0.5$^{\prime\prime}$ resolution to match the data from (cite: s08)" (Optical depth, source size, and dust temperature)
- final beam: 0.363x0.199 arcsec, PA 28.3 deg  
  > "has a beam of $0.363\times 0.199^{\prime\prime}$ at position angle 28.3$^o$" (Observations)
- final rms: 11 mJy/beam  
  > "1$\sigma$ noise level of 11 mJy beam$^{-1}$" (Observations)

### Inherited from earlier work

- Observation and calibration details  
  > "Further details of the observations and calibration are given in (cite: r14)." (Observations) [from (cite: r14) Rangwala et al. 2014, in prep]
- Uniform disk diameter = 1.60 x gaussian FWHM  
  > "the disk diameter is equal to 1.60 times the deconvolved gaussian full-width half-maximum (FWHM) diameter (cite: s08)" (Optical depth, source size, and dust temperature) [from (cite: s08)]

### Not stated but needed to reproduce (our reading)

- Calibrator list (phase, bandpass) and CASA version
- Task, deconvolver, clean threshold and masks
- Self-calibration solution intervals and reference model
- Exact line-free channel ranges
- Method of the elliptical Gaussian fit (software)
- Dust emissivity normalisation kappa_0 and the error propagation method
- Uniform-disk luminosity formula details

## Analysis recipe

1. **Fit nuclei with elliptical Gaussians**: 1x1 arcsec region around each peak fitted with an elliptical gaussian; deconvolved from beam analytically  
  > "A $1\times 1^{\prime\prime}$ region centered on the peak pixel of each nucleus was fit with an elliptical gaussian to obtain the observed size and total flux density." (Optical depth, source size, and dust temperature)
   - assumption: West nucleus: major axis 0.21 arcsec at PA 118 deg and inclination 53.5 deg  
  > "for the western nucleus we assume a major axis of $0.21^{\prime\prime}$ at a position angle of 118$^\circ$" (Optical depth, source size, and dust temperature)
   - fitting: _not stated_
   - validation: _not stated_
2. **Convert to peak brightness temperature**: T_obs = T_B,peak theta_source^2/theta_obs^2 for gaussian source coupled to gaussian beam  
  > "$T_{obs} = T_{B,peak} \theta_{source}^2/\theta_{obs}^2$" (Optical depth, source size, and dust temperature)
   - fitting: _not stated_
   - validation: _not stated_
3. **Derive optical depth and dust temperature**: Compare 691 and 345 GHz fluxes (0.45 arcsec radius, 0.5 arcsec images) with flux ratio equation; iterate with brightness-temperature equation for east; 230 GHz as check  
  > "For the eastern nucleus, we iterated between the two equations to find consistent solutions for the two parameters" (Optical depth, source size, and dust temperature)
   - assumption: Dust emissivity index beta = 1.8; constant optical depth across each source  
  > "we assume a constant optical depth for each source, which in turn implies a constant mass surface density across each source." (Optical depth, source size, and dust temperature)
   - fitting: _not stated_
   - validation: 230 GHz measurements used as consistency check  
  > "We use the lower signal-to-noise 230 GHz measurements as a consistency check on the fits." (Optical depth, source size, and dust temperature)
4. **Compute luminosity, surface density and L/M**: L = (pi theta_maj^2 / 8 ln2) sigma T_D,peak^4 for a thin inclined disk with gaussian temperature distribution; combine with dynamical masses  
  > "the total luminosity of a thin inclined disk with a gaussian temperature distribution is $L = (\pi \theta_{maj}^2)/8 \ln 2) \sigma
T_{D,peak}^4$" (Discussion)
   - fitting: _not stated_
   - validation: _not stated_
5. **Estimate gas column and volume density**: N_H from tau using tau250/N_H = 2x the Planck value; spherical model for lower limits on volume density  
  > "Adopting $\tau_{250\mu m}/N_H = 2 (\tau_{250\mu m}/N_H)_{Planck} =  4.6
\times 10^{-25}$ cm$^2$" (Gas and star formation in the Arp 220 nuclei)
   - assumption: Factor 2 above Planck value because Planck value gives gas mass twice the dynamical mass  
  > "this surface density results in a gas mass for the western nucleus that is twice as large as the dynamical mass within the same radius" (Gas and star formation in the Arp 220 nuclei)
   - fitting: _not stated_
   - validation: _not stated_

## Software


## Numeric results

| quantity | value | uncertainty | units | step | quote |
|---|---|---|---|---|---|
| Western nucleus tau_434um | 5.3 | +9.0/-1.7 | dimensionless | 3 | $5.3^{+9.0}_{-1.7}$ |
| Eastern nucleus tau_434um | 1.7 | +1.1/-0.7 | dimensionless | 3 | $1.7^{+1.1}_{-0.7}$ |
| Eastern nucleus T_D,peak | 80 | +30/-17 | K | 3 | $80^{+30}_{-17}$ |
| Western nucleus T_D,peak | 197 | +/-27, +0/-55 (systematic) | K | 3 | $197 \pm 27 ^{+0}_{-55}$ |
| Western nucleus log(sigma T^4) | 14.3 | +/-0.2, +0/-0.7 | L_sun kpc^-2 | 4 | $14.3\pm 0.2 ^{+0}_{-0.7}$ |
| Fraction of total luminosity in two nuclei | 83% | +65/-38 (calibration), +0/-34 (systematic) | % | 4 | The two nuclei together account for $83^{+65,+0}_{-38,-34}$% of the total luminosity of Arp 220. |
| Western nucleus gas surface density | 1.8e25 | not stated | H cm^-2 | 5 | $1.8 \times 10^{25}$ |
| Western nucleus L/M_dyn | 540 | +360/-240 | L_sun/M_sun | 4 | $540^{+360,+0}_{-240,-240}$ |
| Total 691 GHz flux of two nuclei | 3.32 | 0.50 | Jy | 3 | The 691 GHz flux attributed to the two nuclei is $3.32 \pm 0.50$ Jy |

## Qualitative findings

- Any AGN in Arp 220 must be Compton-thick given the gas columns  
  > "any AGN in Arp 220 must be Compton-thick" (abstract)

## Claim tuples

- H: Are the nuclear dust disks warm and optically thick at 434 um? | E: Gaussian fits and flux-ratio solutions combining ALMA 691 GHz with 345 and 230 GHz data | R: West: T_D~200 K, tau=5.3; East: ~80 K, tau=1.7 | F: The western nucleus is warmer and more opaque than the eastern | **supported**
- H: Does the western nucleus luminosity surface density require an AGN or hot starburst? | E: Computed sigma T^4 from size and T_D | R: log = 14.3, excludes ordinary starburst at ~3 sigma but depends on geometry | F: AGN or hot starburst needed, though uncertain | **partially**

## Reasoning

- Why this data: _not stated_
- Why this method: _not stated_
- Alternative: Uniform elliptical disk model gives lower temperatures (55 K east, 79 K west)  
  > "the dust temperatures are somewhat lower (55 K for the eastern nucleus and 79 K for the western nucleus)" (Footnote 2)
- How they decided it was enough: _not stated_
- Limitation (authors): Western nucleus poorly resolved along beam major axis; minor axis unknown  
  > "The western nucleus is not well resolved along the beam major axis, with a deconvolved diameter just 55% of the beam" (Optical depth, source size, and dust temperature)
- Caveat (inferred, ours): Results depend strongly on assumed source geometry and the unresolved western minor axis
- Caveat (inferred, ours): Flux scale from bandpass calibrator only (15%)
- Caveat (inferred, ours): Gas-to-dust and tau/N_H factor of 2 tuned to match dynamical mass
- Caveat (inferred, ours): Comparison of different-epoch/different-instrument fluxes assumes matched apertures

## Reproducibility

- Data public (paper): _not stated_
- Products in archive: _not stated_
- Missing: Full calibration and imaging details (deferred to Rangwala et al. 2014 in prep)
- Missing: Software names and versions
- Data volume (inferred): ~10-50 GB (single Band 9 execution)
- Score (inferred): 3/5, Data from one archive project and the analytic recipe is clear, but calibration/imaging details are deferred and software is unnamed.
- Rediscovery candidate: no, Calibration and imaging details are not given and rely on external fluxes and an unpublished paper.

## Links

- Companion: (cite: r14) Rangwala et al. 2014 (Observation and calibration details; CO 6-5 data)
- Companion: (cite: b14) Barcos-Muñoz et al. 2014 (Inclination from 33 GHz continuum)

## Checks

```json
{
 "quotes": 56,
 "quotes_ok": 56,
 "quote_pass_rate": 1.0,
 "quotes_too_long": 0,
 "unsupported_facts": 0,
 "project_codes": 0,
 "codes_not_in_text": [],
 "codes_not_in_obscore": [],
 "obscore_codes_not_in_card": [
  "2011.0.00403.S"
 ],
 "codes_printed_but_missing": [],
 "numeric_results": 9,
 "numeric_problems": 0,
 "fill": {
  "facts": 74,
  "stated": 39,
  "rate": 0.527
 },
 "evidence_ok": true
}
```
