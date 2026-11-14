# Bimodal morphologies of massive galaxies at the core of a protocluster at z = 3.09 and the strong size growth of a brightest cluster galaxy

`2017MNRAS.469.2235K` | Monthly Notices of the Royal Astronomical Society 2017 | first author: Kubo, M. | arXiv: 1704.05962 | DOI: 10.1093/mnras/stx920

Card schema 1.0 | model claude-sonnet-5-5 | depth light | type multi_facility_alma_minor

## Science

- Fields: high_z_galaxies, galaxy_clusters_and_sz
- Question: What are the rest-frame optical morphologies and sizes of massive galaxies in the dense SSA22-AzTEC14 group at z=3.09, and what do they imply for BCG formation?  
  > "Wide morphological variety of them suggests their on-going dramatic evolutions." (abstract)
- Target **SSA22-AzTEC14 group**: coordinates _not stated_; z/distance z=3.09  
  > "The SSA22 protocluster at $z=3.09$ is a rare density peak of galaxies" (1 Introduction); "Our target is an extremely dense group of galaxies found at the core of the SSA22 protocluster at $z=3.09$, called the SSA22-AzTEC14 group" (2 Observation); distance from spectroscopic redshifts (Kubo et al. 2016)  
  > "The SSA22 protocluster at $z=3.09$ is a rare density peak of galaxies" (1 Introduction); "Our target is an extremely dense group of galaxies found at the core of the SSA22 protocluster at $z=3.09$, called the SSA22-AzTEC14 group" (2 Observation)

## Data provenance

- ALMA projects: 2013.1.00162.S
- bands: 1.1 mm (sub-mm) continuum  
  > "The 1.1 mm fluxes of five sub-mm sources detected in the AzTEC14 group range from $S_{\rm 1.1~mm} = 0.6$ to $2.0$ mJy." (2 Observation)
- frequencies and spectral setup: _not stated_
- continuum bandwidth: _not stated_
- arrays: _not stated_
- configurations: _not stated_
- baselines: _not stated_
- angular resolution: synthesized beam 0.70"x0.59"  
  > "with a synthesized beam of $0''.70\times0''.59$ and a typical rms level of 60 $\mu$Jy beam$^{-1}$" (2 Observation)
- max recoverable scale: _not stated_
- sensitivity: typical rms 60 uJy/beam  
  > "with a synthesized beam of $0''.70\times0''.59$ and a typical rms level of 60 $\mu$Jy beam$^{-1}$" (2 Observation)
- time on source: _not stated_
- observing dates: _not stated_
- pi or archival as stated: _not stated_
- Other facility **Subaru IRCS+AO188**: K'-band high-resolution imaging, 2.8 h, PSF FWHM ~0.16"  
  > "The exposure time was 2.8 hours in total." (2 Observation)
- Other facility **Subaru MOIRCS**: Ks-band imaging and spectroscopy  
  > "The zero-point magnitude of our IRCS-AO $K'$-band image is calibrated to that of our MOIRCS $K_s$-band image." (2 Observation)
- Other facility **HST/ACS**: archival F814W image  
  > "We also show the archival $I_{\rm F814W}$-band image taken with the Advanced Camera for Surveys (ACS) on the *HST* (PID 9760; PI Roberto Abraham)." (2 Observation)
- External data: ALMA 1.1 mm observations and source fluxes/sizes of the AzTEC14 sub-mm sources  
  > "we carried out deep observations of this region at sub-mm by using Atacama Large Millimeter/submillimeter Array (ALMA) with a synthesized beam of $0''.70\times0''.59$" (2 Observation) [from Umehata et al. 2015 (cite: 2015ApJ...815L...8U); (cite: 2017ApJ...835...98U)]
- External data: Spectroscopic redshifts, stellar masses, SEDs of members  
  > "In (cite: 2016MNRAS.455.3333K), we spectroscopically confirmed that seven galaxies belong to one group at $z_{\rm spec}\approx3.09$." (2 Observation) [from (cite: 2016MNRAS.455.3333K)]

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
- primary beam correction: _not stated_
- array combination: _not stated_
- smoothing: _not stated_
- final beam: _not stated_
- final rms: _not stated_

### Inherited from earlier work

- Aperture-corrected photometry done as in earlier work  
  > "Aperture corrected photometries of each galaxies are performed by the way same as that in (cite: 2013ApJ...778..170K)" (3.1 Morphologies and stellar populations) [from (cite: 2013ApJ...778..170K)]

### Not stated but needed to reproduce (our reading)

- ALMA data reduction and imaging settings (done in Umehata papers)
- Exact coordinates of targets

## Analysis recipe

1. **Fit Sérsic morphologies to K' image**: GALFIT 2D Sérsic fits with a star PSF reference  
  > "We fit the Sérsic models (cite: 1968adga.book.....S) with effective radii $r_e=0.2-12$ kpc and Sérsic index $n=0.5-10$." (3.1 Morphologies and stellar populations)
   - software: GALFIT, SExtractor
   - parameter: initial r_e = 1 kpc, n=1.4; fit region 2 arcsec square  
  > "Fittings are performed for within two arcsec square regions of each object." (3.1 Morphologies and stellar populations)
   - fitting: _not stated_
   - validation: Mock galaxies injected in blank fields and refit (1000 iterations); PSF reference test  
  > "We performed a thousand simulations for each model and see deviations of re-estimated values from inputs." (Reproducibility of morphological parameters)

## Software

- **GALFIT** : Sérsic profile fitting  
  > "Following previous studies, we evaluate morphological properties by using the GALFIT" (3.1 Morphologies and stellar populations)
- **SExtractor** : magnitudes, Kron fluxes, detection completeness  
  > "extracting them by using the SExtractor" (Detection Completeness)
- **IRAF** : IRCS data reduction  
  > "We reduced the data using the IRAF data reduction tasks following the data reduction manual for the IRCS" (2 Observation)

## Numeric results

| quantity | value | uncertainty | units | step | quote |
|---|---|---|---|---|---|
| Az14-K15a effective radius (single Sérsic) | 1.37 | 0.75 | kpc | 1 | / Az14-K15a / $22.50\pm0.10$ / $8.0_{- 2.9 }^{+ 5.7 }$ / $1.37\pm0.75$ / $9.5\pm4.5$ / |
| Az14-K15c effective radius | 1.01 | 0.04 | kpc | 1 | / Az14-K15c / $21.55\pm0.04$ / $25.4_{- 5.8 }^{+ 7.3}$ / $1.01\pm0.04$ / $2.5\pm0.2$ / |
| Az14-K15a AGN-subtracted effective radius | 4.26 | 0.60 | kpc | 1 | / Az14-K15a (AGN-subtracted) /  /  / $4.26\pm0.60$ / $2.2\pm0.6$ / |

## Qualitative findings

- No new group members detected in the deeper K' image  
  > "we found no candidate new members." (abstract)

## Claim tuples

- H: Is the most massive QG a compact elliptical supporting two-phase formation? | E: GALFIT fit of AO K' image | R: r_e = 1.37±0.75 kpc (Az14-K15a); Az14-K15c r_e=1.01±0.04 kpc | F: Compact QG supports two-phase formation and strong size growth to a BCG | **supported**
- H: Are massive SFGs in the group larger than field SFGs? | E: Size-mass comparison and stacked radial profile | R: larger than field SFGs | F: two to three times larger | **supported**

## Reasoning

- Why this data: _not stated_
- Why this method: _not stated_
- How they decided it was enough: _not stated_
- Limitation (authors): Large uncertainties in morphological parameters for faint members  
  > "Since there are large uncertainties in the morphological parameters estimated with the GALFIT except for those of the brightest one" (3.1 Morphologies and stellar populations)
- Caveat (inferred, ours): ALMA is only context; results rest on Subaru imaging
- Caveat (inferred, ours): Sérsic fits of faint sources are poorly constrained

## Reproducibility

- Data public (paper): _not stated_
- Products in archive: _not stated_
- Missing: Subaru IRCS reduced images
- Missing: ALMA reduction details
- Data volume (inferred): small (<10 GB for ALMA part)
- Score (inferred): 2/5, ALMA plays a minor role; main data are Subaru images not described as public.
- Rediscovery candidate: no, Main results come from Subaru AO imaging, not ALMA.

## Links

- Companion: Umehata et al. 2017 (cite: 2017ApJ...835...98U) (ALMA observations of the SSA22 field)
- Companion: Kubo et al. 2016 (cite: 2016MNRAS.455.3333K) (spectroscopy and SEDs of the AzTEC14 group)
- Related: SSA22 protocluster

## Checks

```json
{
 "quotes": 29,
 "quotes_ok": 29,
 "quote_pass_rate": 1.0,
 "quotes_too_long": 1,
 "unsupported_facts": 0,
 "project_codes": 1,
 "codes_not_in_text": [],
 "codes_not_in_obscore": [],
 "obscore_codes_not_in_card": [],
 "codes_printed_but_missing": [],
 "numeric_results": 3,
 "numeric_problems": 0,
 "fill": {
  "facts": 58,
  "stated": 20,
  "rate": 0.345
 },
 "evidence_ok": true
}
```
