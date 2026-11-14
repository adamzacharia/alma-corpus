# ALMA and MUSE observations reveal a quiescent multi-phase circumgalactic medium around the z ≃ 3.6 radio galaxy 4C 19.71

`2021A&A...645A.120F` | Astronomy and Astrophysics 2021 | first author: Falkendal, Theresa | arXiv: 2007.10061 | DOI: 10.1051/0004-6361/201935237

Card schema 1.0 | model claude-sonnet-5-5 | depth full | type observational_alma_primary

## Science

- Fields: high_z_galaxies, agn_and_quasars
- Question: What are the kinematics, ionization and molecular gas content of the multi-phase circumgalactic medium around the z≃3.6 radio galaxy 4C 19.71, probed with ALMA [CI](1-0) and MUSE rest-frame UV lines?  
  > "The combination allowed us to probe the ionized gas and the molecular gas of the host galaxy, as well as of the surrounding CGM." (Conclusions)
- Target **4C 19.71**: coordinates 21:44:7.45, +19:29:14.60 (J2000)  
  > "Ra(J2000), Dec (J2000) | 21:44:7.45, +19:29:14.60" (Table 1); "which implies a scale of 7.427 kpc arcsec$^{-1}$ at $z=3.59$." (1 Introduction); z/distance z_sys = 3.5895  
  > "Ra(J2000), Dec (J2000) | 21:44:7.45, +19:29:14.60" (Table 1); "which implies a scale of 7.427 kpc arcsec$^{-1}$ at $z=3.59$." (1 Introduction); distance from [CI](1-0) line at the core, this work  
  > "Ra(J2000), Dec (J2000) | 21:44:7.45, +19:29:14.60" (Table 1); "which implies a scale of 7.427 kpc arcsec$^{-1}$ at $z=3.59$." (1 Introduction)

## Data provenance

- ALMA projects: 2015.1.00530.S
- bands: Band 3  
  > "The Atacama Large Millimeter/submillimeter Array (ALMA) cycle 3 observations in band 3 were carried out on UT 2016 March 6" (2.1 ALMA observations)
- frequencies and spectral setup: four 3.875 GHz wide bands covering 94.6–98.4 GHz and 106.5–110.3 GHz, tuned to [CI](1-0) and 13CO(4-3)  
  > "The four 3.875 GHz wide bands were tuned to include the \[C i\] $^3$P$_1$-$^3$P$_0$ (\[C i\](1–0) hereafter) and $^{13}{\rm CO}\,J=4 \rightarrow 3$ lines" (2.1 ALMA observations)
- continuum bandwidth: _not stated_
- arrays: _not stated_
- configurations: _not stated_
- baselines: _not stated_
- angular resolution: 1.8"×1.9" synthesized beam (continuum)  
  > "This results in a continuum image with synthesized beam 1.8"$\times$1.9" and a root mean square (RMS) of 14 $\mu$Jy." (2.1 ALMA observations)
- max recoverable scale: _not stated_
- sensitivity: continuum rms 14 μJy; cube rms 0.3 mJy per 50 km/s channel  
  > "we binned the data to 50 km s$^{-1}$, which resulted in an RMS noise of 0.3 mJy" (2.1 ALMA observations)
- time on source: 38 min on-source, 38 antennas  
  > "with 38 min on-source integration and 38 operating antennas" (2.1 ALMA observations)
- observing dates: UT 2016 March 6  
  > "were carried out on UT 2016 March 6" (2.1 ALMA observations)
- pi or archival as stated: _not stated_
- Line: [CI] 3P1-3P0 (492.16 GHz)
- Line: 13CO J=4-3 (440.77 GHz)
- Other facility **VLT/MUSE**: Rest-frame UV lines (Lyα, C IV, He II, C III]) over 1x1 arcmin; program 097.B-0323(B), 5 h on source  
  > "program ID 097.B-0323(B)) were carried out over four nights between 2016 June 7 and 2016 September 2, with a total of five hours on source integration time" (2.2 MUSE observations)
- Other facility **VLA, Chandra, Spitzer, Herschel, K-band**: Supporting multiwavelength images and SED-based properties from previous observations  
  > "Galaxy 4C 19.71 has an extensive set of observations, spanning from X-ray to radio frequencies" (2.3 Previous supporting observations)
- External data: Stellar mass log(M*/Msun)=11.13  
  > "the stellar mass has been estimated to be log (M$_\star$/ M$_{\odot}$)=11.13 (cite: DeBreuck2010)" (2.3 Previous supporting observations) [from (cite: DeBreuck2010)]
- External data: SFR 84 Msun/yr and L_IR, from SED fitting  
  > "Star-formation rate (SFR) | 84$_{-62}^{+172}$ M$_{\odot}$ yr$^{-1}$ | (cite: Falkendal2019)" (Table 1) [from (cite: Falkendal2019)]
- External data: ALMA band 3 continuum flux density S(103 GHz)=0.07 mJy  
  > "$S_{\rm 103 GHz}=0.07$ mJy (cite: Falkendal2019)" (4.3 Molecular gas mass) [from (cite: Falkendal2019)]
- Simulation/model as data: Cloudy 17.01 photoionization/PDR model grids (isochoric and isobaric) with power-law ionizing spectrum  
  > "we modeled the ionization front with Cloudy 17.01, most recently described by (cite: Ferland2013)" (4.4.1 photoionization)

## Processing

### Calibration

- pipeline or manual: Observatory-supplied calibration script in CASA  
  > "We calibrated the data with the Common Astronomy Software Applications (CASA) using the observatory-supplied calibration script." (2.1 ALMA observations)
- casa version: _not stated_
- pipeline version: _not stated_
- archive products used as is: _not stated_
- flux calibrator: _not stated_
- flux scale uncertainty: _not stated_
- self calibration: _not stated_

### Imaging

- task: _not stated_
- deconvolver: _not stated_
- weighting robust: natural weighting (robust = 2)  
  > "A natural weighting (robust parameter of 2) was applied since the data has low signal-to-noise." (2.1 ALMA observations)
- uv taper: _not stated_
- cell size: _not stated_
- image size: _not stated_
- masking: _not stated_
- multiscale scales: _not stated_
- continuum subtraction: uv-plane first-order polynomial over all spectral windows excluding expected line channels  
  > "we first subtracted the continuum in the $uv$-plane by fitting a first-order polynomial over all the spectral window" (2.1 ALMA observations)
- line free channels: _not stated_
- primary beam correction: _not stated_
- array combination: _not stated_
- smoothing: binned to 50 km/s  
  > "we binned the data to 50 km s$^{-1}$" (2.1 ALMA observations)
- final beam: 1.8"×1.9"  
  > "synthesized beam 1.8"$\times$1.9"" (2.1 ALMA observations)
- final rms: 14 μJy continuum; 0.3 mJy per 50 km/s channel  
  > "a root mean square (RMS) of 14 $\mu$Jy" (2.1 ALMA observations)

### Inherited from earlier work

- Molecular gas mass formula for [CI]  
  > "following (cite: PapadopoulosGreve2004; Wagg2006; Alaghband-Zadeh2013; Gullberg2016), as:" (4.3 Molecular gas mass) [from (cite: PapadopoulosGreve2004; Wagg2006; Alaghband-Zadeh2013; Gullberg2016)]
- Ionized gas mass relation from Lyα  
  > "The ionized gas mass can be estimated from the Ly$\alpha$ emission using the relation from (cite: DeBreuck2003):" (4.4.4 Gas masses) [from (cite: DeBreuck2003)]

### Not stated but needed to reproduce (our reading)

- Exact CASA version and the tclean parameters (cell, image size, mask, niter, threshold)
- Line-free channel ranges used for the continuum fit
- Aperture/region definitions (pixel boundaries) for regions A, B, C
- Flux calibrator and flux scale uncertainty
- Details of Cloudy inputs (ionizing luminosity normalisation, abundances, dust)
- Method for computing inclination from dynamical mass in detail

## Analysis recipe

1. **Calibrate and image ALMA data**: CASA calibration script; natural-weighted cube binned to 50 km/s; uv continuum subtraction; moment-0 maps over narrow frequency ranges  
  > "We then collapsed the cube over the frequency range 107.21–107.27 GHz and 96.007–96.067 GHz for the \[C i\](1–0) and $^{13}$CO(4–3) moment–0 maps" (2.1 ALMA observations)
   - software: CASA
   - fitting: _not stated_
   - validation: _not stated_
2. **Reduce MUSE data**: MUSE pipeline 1.6.2 on each exposure without sky subtraction, ZAP 2.0 sky subtraction with default parameters, MPDAF 2.5 merge; moment-0 maps with continuum from first-order polynomial  
  > "Finally, we merged all ten individual 30 min exposures into one combined cube using the python package MPDAF 2.5" (2.2 MUSE observations)
   - software: MUSE pipeline, ZAP, MPDAF
   - fitting: _not stated_
   - validation: _not stated_
3. **Detect and fit lines**: Blind search of binned cube for [CI] and 13CO; Gaussian fits to [CI] and double-Gaussian to CIV; Lyα and HeII constrained using C IV/[CI] redshift and widths  
  > "We used the non-linear least square method to fit a Gaussian function to the spectrum using the RMS=0.3 mJy as one sigma uncertainty in the flux." (3.1 Molecular and atomic emission lines)
   - parameter: CIV doublet ratio fixed to 2:1, common width, red component fixed 2.6 Å from blue  
  > "we fixed the C iv $\lambda$1548/C iv $\lambda$1550 doublet ratio to the theoretical ratio of 2:1" (3.2 Ionized gas)
   - fitting: non-linear least squares; 1σ from variance of parameter estimates  
  > "The reported errors are the square root of the variance, one sigma, of the parameter estimate for the Gaussian fits." (3.1 Molecular and atomic emission lines)
   - validation: Lyα flux estimated by two independent methods (integration of unaffected channels and Gaussian fit)  
  > "To estimate the Ly$\alpha$ $\lambda$1215.7 Å integrated line flux, we used two independent methods." (3.2 Ionized gas)
4. **Derive molecular gas mass, SFE and depletion time**: [CI]-based H2 mass equation; cross-check with Scoville2016 continuum method  
  > "we compared it with the molecular gas mass estimated from the observed continuum flux density in ALMA band 3 (cite: Scoville2016)" (4.3 Molecular gas mass)
   - parameter: X_[CI]=3e-5, Q10=0.48, A10=7.93e-8 s^-1  
  > "we assumed the median value of $Q_{10}$=0.48" (4.3 Molecular gas mass)
   - assumption: Tdust=40 K for the continuum cross-check; X_[CI]=1e-5 for region A  
  > "assuming $T_{\rm dust}$=40 K" (4.3 Molecular gas mass)
   - fitting: _not stated_
   - validation: Continuum-based mass 6e10 Msun within a factor of two of [CI] mass  
  > "we find a molecular gas mass of $M_{\rm mol}= 6 \times 10^{10}$  M$_{\odot}$" (4.3 Molecular gas mass)
5. **Photoionization/PDR modeling of CGM cloud**: Cloudy 17.01 grids of isochoric and isobaric models compared with [CI]/CIV and CIV/HeII ratios  
  > "The density, for the isochoric models, varied from log n$_H$ (cm$^{-3}$)=0 to 3 in steps of 1 dex" (4.4.1 photoionization)
   - software: Cloudy
   - parameter: power-law slope -1 over 0.01–12 Ryd; log U from -4 to -1; AV=2  
  > "a simple hard power-law with a slope of $-$1 over the energy range of 0.01 to 12 Ryd" (4.4.1 photoionization)
   - assumption: Standard ISM abundance ratios scaled to a range of metallicities  
  > "Grids of models were made assuming the standard ISM abundance ratios scaled to a range of metallicities." (4.4.1 photoionization)
   - fitting: _not stated_
   - validation: tested slopes -1.5 and -2.0 show modest differences  
  > "The resulting line ratios show only modest differences compared to our fiducial model" (4.4.1 photoionization)
6. **Estimate ionized gas mass and AGN ionization budget**: DeBreuck2003 relation with filling factor from case B recombination; ionizing photon budget from ionization parameter  
  > "We find that the volume filling factors of the two clouds must be very small." (4.4.4 Gas masses)
   - assumption: gas completely photoionized, equal proton and electron densities, little dust absorption of Lyα  
  > "we assumed the gas is completely photoionized, that the proton and electron densities are equal" (4.4.4 Gas masses)
   - fitting: _not stated_
   - validation: _not stated_

## Software

- **CASA** : ALMA calibration, imaging, moment maps  
  > "The data cube and moment-0 maps were also produced using CASA." (2.1 ALMA observations)
- **MUSE pipeline** 1.6.2: MUSE data reduction  
  > "We reduced the data using the MUSE instrument pipeline version 1.6.2." (2.2 MUSE observations)
- **ZAP** 2.0: sky subtraction  
  > "we sky-subtracted each exposure by using ZAP 2.0" (2.2 MUSE observations)
- **MPDAF** 2.5: merging exposures  
  > "using the python package MPDAF 2.5" (2.2 MUSE observations)
- **AIPS** : astrometric solution of K-band image with XTRAN  
  > "We used AIPS (Astronomical Image Processing System) and the task `XTRAN`" (2.3 Previous supporting observations)
- **Cloudy** 17.01: photoionization and PDR modeling  
  > "we modeled the ionization front with Cloudy 17.01" (4.4.1 photoionization)

## Numeric results

| quantity | value | uncertainty | units | step | quote |
|---|---|---|---|---|---|
| Systemic redshift | 3.5895 | not stated | dimensionless | 3 | $z_{\rm sys}$=3.5895 |
| [CI](1-0) FWHM, core | 87 | 23 | km/s | 3 | FWHM of 87$\pm$23 km s$^{-1}$ |
| [CI](1-0) FWHM, region A | 108 | 54 | km/s | 3 | it has an FWHM of 108$\pm$54 km s$^{-1}$ |
| CIV FWHM region A | 179 | 27 | km/s | 3 | an FWHM of 179$\pm$27 km s$^{-1}$ |
| M_H2 core | 3.06e10 | 1.11e10 | Msun | 4 | M$_{\rm H_2}^{\rm Core}$=(3.06$\pm$1.11)$\times$10$^{10}$  M$_{\odot}$ |
| M_H2 region A | 1.42e10 | 0.95e10 | Msun | 4 | M$_{\rm H_2}^{\rm north}$=(1.42$\pm$0.95)$\times$10$^{10}$  M$_{\odot}$ |
| Star formation efficiency | 2.74 | +5.57/-0.99 | Gyr^-1 | 4 | SFE$\equiv$SFR/M$_{\rm H_2}$=2.74$^{+5.57}_{-0.99}$ Gyr$^{-1}$ |
| Gas depletion time | 0.36 | +1.08/-0.18 | Gyr | 4 | t_{\rm depl}\equiv$SFE$^{-1}$=0.36$^{+1.08}_{-0.18}$ Gyr |
| Gas fraction | 0.19 | 0.07 | dimensionless | 4 | $f_{\rm gas}$=0.19$\pm 0.07$ |
| [CI]/CIV flux ratio, region A | 0.017 | 0.011 | dimensionless | 5 | flux ratios of \[C i\]/C iv=0.017$\pm$0.011 |
| Inclination from dynamical mass | ~3 | not stated | deg | 0 | This results in an inclination of $i\sim 3^{\circ}$ |

## Qualitative findings

- Narrow, dynamically quiescent [CI](1-0) at the host and ~75 kpc north, overlapping weak CIV emission  
  > "We weakly detect \[C i\](1–0) emission $\sim$75 kpc away from the host galaxy." (5 Conclusions)
- Simple Cloudy models suggest low metallicity, low ionization, low density gas photoionized by the AGN  
  > "The photoionization and PDR modeling suggests that the observed multi-phase region has a low metallicity, low ionization, and low density." (5 Conclusions)

## Claim tuples

- H: Is the CGM of 4C 19.71 dynamically quiescent in both ionized and molecular phases? | E: Gaussian fits to ALMA [CI] and MUSE CIV spectra in regions A, B, C | R: [CI] FWHM 108±54 km/s and CIV 179±27 km/s in region A with low velocity offsets | F: The gas is dynamically cold compared to gas between the radio lobes | **supported**
- H: Can simple photoionization/PDR models explain the observed line ratios? | E: Cloudy grids compared with [CI]/CIV and CIV/HeII | R: Matches for low metallicity (~0.1–0.03 solar) and n_H~10–100 cm^-3 | F: Consistent with an AGN-illuminated PDR-like cloud, though poorly constrained | **partially**
- H: Molecular gas dominates the CGM mass over ionized gas | E: Compare [CI]-derived H2 mass with Lyα-derived HII mass in region A | R: M_H2 ≲1e10 Msun vs M_HII up to ~1e8 Msun | F: Molecular mass is 2-4 orders of magnitude larger | **supported**
- H: Is the host galaxy disk misaligned with the nuclear launching region? | E: Compare narrow [CI] width with broad Lyα and estimate inclination from dynamical mass | R: i~3 deg | F: Face-on disk with radio jets in the sky plane implies misalignment | **partially**

## Reasoning

- Why this data: _not stated_
- Why this method: [CI] used as H2 tracer in absence of other molecular lines; Cloudy modeling kept simple as proof of concept  
  > "The modeling was not intended to be exhaustive but only to determine whether or not we could reproduce the observed line ratios" (4.4.1 photoionization)
- Alternative: He II not used for systemic redshift because of sky-line contamination; [CI] used instead  
  > "In the case of 4C 19.71, we instead relied on the \[C i\](1–0) line to determine the systemic redshift" (3.2 Ionized gas)
- How they decided it was enough: _not stated_
- Limitation (authors): Low S/N; Lyα and HeII severely affected by night sky lines  
  > "We are limited to low signal-to-noise and the source is at an unfortunate redshift" (5 Conclusions)
- Limitation (authors): Mass uncertainty excludes errors on X_[CI], Q10, A10  
  > "without additional errors arising from from uncertainties in $X_{\rm [C\textsc{i}]}$, $Q_{10}$, or $A_{10}$" (4.3 Molecular gas mass)
- Caveat (inferred, ours): [CI] detections are marginal (~3σ), so region A detection and masses are uncertain
- Caveat (inferred, ours): Assumed Q10 and X_[CI] dominate mass uncertainty but are not propagated
- Caveat (inferred, ours): Cloudy modeling is coarse with a degenerate parameter space
- Caveat (inferred, ours): Inclination of ~3 deg from a crude dynamical mass assumption

## Reproducibility

- Data public (paper): ALMA project acknowledged; MUSE program ID given; K-band image publicly available  
  > "The K-band image shown in Fig. 1 is publicly available" (2.3 Previous supporting observations)
- Products in archive: _not stated_
- Missing: Exact CASA imaging commands and version
- Missing: Cloudy input files
- Missing: Region masks for spectral extraction
- Data volume (inferred): ALMA single-track Band 3 dataset, ~tens of GB raw; MUSE cube a few GB
- Score (inferred): 3/5, Data public and recipe mostly described, but imaging parameters, region definitions and Cloudy inputs are missing and detections are marginal.
- Rediscovery candidate: no, Key imaging and extraction details are unstated, and results rely on low-S/N detections and MUSE data.

## Links

- Method: (cite: Soto2016) (ZAP sky subtraction)
- Method: (cite: Ferland2013) (Cloudy)
- Companion: (cite: Falkendal2019) (SED fitting giving SFR, L_IR and ALMA continuum flux)
- Related: MUSE program 097.B-0323(B)

## Checks

```json
{
 "quotes": 75,
 "quotes_ok": 75,
 "quote_pass_rate": 1.0,
 "quotes_too_long": 0,
 "unsupported_facts": 0,
 "project_codes": 1,
 "codes_not_in_text": [],
 "codes_not_in_obscore": [],
 "obscore_codes_not_in_card": [],
 "codes_printed_but_missing": [],
 "numeric_results": 11,
 "numeric_problems": 0,
 "fill": {
  "facts": 86,
  "stated": 53,
  "rate": 0.616
 },
 "evidence_ok": true
}
```
