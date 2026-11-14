# Investigating the Nested Structure of the Outflow from the Low Luminosity Protostar IRAS 16253-2429 Using JWST and ALMA

`2026ApJ..1000..184N` | The Astrophysical Journal 2026 | first author: Narang, Mayank | arXiv: 2602.09837 | DOI: 10.3847/1538-4357/ae4354

Card schema 1.0 | model claude-sonnet-5-5 | depth light | type multi_facility_alma_minor

## Science

- Fields: star_formation
- Question: How do the morphology, excitation and kinematics of the H2 outflow, jet and cavity of the low-luminosity Class 0 protostar IRAS 16253-2429 (JWST plus ALMA 12CO) constrain the outflow launching mechanism?  
  > "The nested excitation and velocity structure of the collimated jet and wide angle wind suggest a magnetohydrodynamic wind as a likely launching mechanism" (abstract)
- Target **IRAS 16253-2429**: coordinates ALMA pointing 16h28m21.60s -24d36m23.40s  
  > "At a distance of only $\sim$140 pc (adopted from (cite: 2020A&A...633A..51Z))" (Introduction); "| 52–10540 m               | 16h28m21.60s | -24d36m23.40s | 2021 October 5, 26, 27, & 28" (Table 1); z/distance ~140 pc  
  > "At a distance of only $\sim$140 pc (adopted from (cite: 2020A&A...633A..51Z))" (Introduction); "| 52–10540 m               | 16h28m21.60s | -24d36m23.40s | 2021 October 5, 26, 27, & 28" (Table 1); distance from (cite: 2020A&A...633A..51Z)  
  > "At a distance of only $\sim$140 pc (adopted from (cite: 2020A&A...633A..51Z))" (Introduction); "| 52–10540 m               | 16h28m21.60s | -24d36m23.40s | 2021 October 5, 26, 27, & 28" (Table 1)

## Data provenance

- ALMA projects: 2019.1.00261.L, 2019.A.00034.S
- bands: 1.3 mm continuum; 12CO J=2-1 (Band 6 not named explicitly)  
  > "the 1.3 mm continuum emission was obtained from the line-free channels of the spectral windows" (2.2 ALMA Observations)
- frequencies and spectral setup: _not stated_
- continuum bandwidth: _not stated_
- arrays: _not stated_
- configurations: C-8 and C-5 antenna configurations, Cycle 8  
  > "observed with ALMA in Cycle 8 using the C-8 (with projected baseline lengths spanning from 52 to 10540 m) and C-5" (2.2 ALMA Observations)
- baselines: 52–10540 m (C-8); 14–1290 m (C-5)  
  > "C-5 (with projected baseline lengths ranging from 14 to 1290 m)" (2.2 ALMA Observations)
- angular resolution: Continuum 0.073'' x 0.048'' (robust 0); 12CO 0.17'' x 0.13'' (robust 0.5), 0.32 km/s  
  > "The continuum image has a spatial resolution of 0.073$''$ $\times$ 0.048$''$ for a robust factor of 0." (2.2 ALMA Observations)
- max recoverable scale: _not stated_
- sensitivity: _not stated_
- time on source: _not stated_
- observing dates: 2021 Oct 5, 26, 27, 28; 2022 Jun 14, 15  
  > "| 14–1290 m                | 16h28m21.60s | -24d36m23.40s | 2022 June 14 & 15" (Table 1)
- pi or archival as stated: _not stated_
- Line: 12CO J=2-1 (not stated)
- Other facility **JWST NIRSpec IFU and MIRI MRS (program 1802, IPA)**: 2.87-28 micron IFU spectral cubes: H2 lines, scattered-light continuum, [Fe II] jet  
  > "spectral imaging by combining Integral Field Unit spectra of the Mid-InfraRed Instrument (MIRI) Medium Resolution Spectroscopy (MRS)" (2.1 JWST Observations)
- External data: ALMA disk properties: inclination 64 deg, Keplerian disk radius 16±3 au, dynamical mass 0.12-0.17 Msun, ALMA continuum position  
  > "The inclination angle of 64$^\circ$, was estimated based on disk fitting (cite: 2023ApJ...954..101A)" (Introduction) [from (cite: 2023ApJ...954..101A)]
- External data: Jet velocity 169±15 km/s  
  > "The H$_2$ velocity in turn is much slower than the jet velocity of 169 $\pm$ 15 km s$^{-1}$ (cite: 2023arXiv231014061N)." (3.5 Velocity Structure) [from (cite: 2023arXiv231014061N)]
- External data: H2 line wavelengths, A coefficients, Eup  
  > "The wavelength, Einstein A coefficient $A_{ul}$, and upper state energy are from (cite: 2022JQSRT.27707949G)." (Table 2 caption) [from (cite: 2022JQSRT.27707949G)]

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
- weighting robust: robust 0 (continuum); 0.5 (12CO)  
  > "for a robust factor of 0. For the $^{12}$CO emission" (2.2 ALMA Observations)
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
- final beam: continuum 0.073'' x 0.048''; 12CO 0.17'' x 0.13''  
  > "a velocity resolution of 0.32 km s$^{-1}$ at a angular resolution of 0.$''$17 $\times$ 0.$''$13 was achieved with a robust factor of 0.5." (2.2 ALMA Observations)
- final rms: _not stated_

### Inherited from earlier work

- ALMA data reduction and imaging follow eDisk papers  
  > "(see also (cite: 2023ApJ...951....8O) and (cite: 2023ApJ...954..101A))" (2.2 ALMA Observations) [from (cite: 2023ApJ...951....8O); (cite: 2023ApJ...954..101A)]
- Cavity edge method via second-derivative inflection points  
  > "We adopted a method similar to that of (cite: 2021ApJ...911..153H)" (3.6 Opening angle) [from (cite: 2021ApJ...911..153H)]
- Outflow width via Gaussian slices  
  > "we adopt a method similar to (cite: 2023arXiv231014061N)" (3.7 Width) [from (cite: 2023arXiv231014061N)]

### Not stated but needed to reproduce (our reading)

- ALMA CASA version and imaging parameters (cell, size, masks, deconvolver)
- Spectral setup frequencies
- Disk PA modelling details (Narang et al. in prep)
- Exact JWST apertures/PSF used for deconvolution

## Analysis recipe

1. **Measure H2 line maps**: Local continuum subtraction then per-pixel Gaussian fit to each line; flux from Gaussian area  
  > "At every pixel, a local (line-free) continuum was subtracted, then a Gaussian fit to the continuum subtracted line profile was made" (3.3 H2 Emission)
   - software: JWST pipeline
   - fitting: _not stated_
   - validation: _not stated_
2. **Opening angle of outflow**: Rotate image by 23 deg; second derivative inflection gives cavity edges; fit straight line to half-width vs height; deconvolve in quadrature  
  > "We computed a second-order differential along the x-axis, and the inflection points (where the second-order derivative equals zero) delineate the edge of the cavity." (3.6 Opening angle)
   - parameter: S/N > 7 sigma; inner 1'' masked  
  > "The inner 1$''$ on both sides of the protostellar position was masked to exclude the outflow neck." (3.6 Opening angle)
   - assumption: PA disk 113 deg  
  > "the PA of the disk, 113$^\circ$, was determined by modeling the disk" (3.6 Opening angle)
   - fitting: straight-line fit  
  > "we determined the half-width of the cavity as a function of distance from the central protostar (indicated as offset along the height in Figure [12](#Figure11)) by fitting a straight line." (Opening angle of the outflow)
   - validation: _not stated_
3. **H2 velocity from PV diagrams**: Subtract ambient cloud component, extract PV from 5''x4'' region along PA=23 deg, subtract mean flow velocity, correct for inclination 64 deg  
  > "we extracted velocities from a rectangular region that was 5$''$ long and 4$''$ wide and aligned along the outflow direction (PA = 23$^\circ$)" (3.5 Velocity Structure)
   - assumption: inclination 64 deg  
  > "correct for inclination (with inclination angle of 64$^\circ$)" (3.5 Velocity Structure)
   - fitting: Gaussian fit for cloud component  
  > "We fit a gaussian to this emission and derive the cloud emission, which we subtract from the data-cube pixel-by-pixel to remove the cloud component and derive the true velocity." (Velocity Structure of the H$_2$ flow)
   - validation: _not stated_
4. **Outflow width at protostar**: Gaussian FWHM of 2-pixel-wide slices perpendicular to axis in H2 S(11); deconvolve NIRSpec PSF  
  > "We deconvolve the outflow width using the NIRSpec IFU average PSF and obtain a deconvolved outflow width of $\sim 0.25$$''$." (3.7 Width)
   - assumption: distance 140 pc  
  > "At a distance of only $\sim$140 pc (adopted from (cite: 2020A&A...633A..51Z)), IRAS 16253$-$2429 is the lowest luminosity source in the IPA sample" (Introduction)
   - fitting: Gaussian per slice  
  > "Subsequently, each slice was fitted with a Gaussian, and the Full Width at Half Maximum (FWHM) of the Gaussian was measured as the width of the outflow in that slice." (Width of the Outflow at the the Protostar)
   - validation: treated as upper limit  
  > "the derived width represents a conservative upper bound rather than a precise physical measurement." (3.7 Width)

## Software

- **JWST pipeline** 1.9.5.dev7 (NIRSpec); 1.11.3 (MIRI): NIRSpec IFU and MIRI MRS reduction  
  > "The MIRI MRS data reduction was carried out using the JWST pipeline version 1.11.3" (2.1 JWST Observations)

## Numeric results

| quantity | value | uncertainty | units | step | quote |
|---|---|---|---|---|---|
| Deconvolved H2 S(11) outflow width at protostar | 0.25 (35 au) | upper limit | arcsec | 4 | obtain a deconvolved outflow width of $\sim 0.25$$''$. At the distance of IRAS 16253$-$2429 this translates into 35 au. |
| Opening angle S(11) N/S | 21 / 19 | ±3 / ±2 | deg | 2 | / S(11)           / $21 \pm 3$       / $19 \pm 2$       / |
| Opening angle 12CO N/S | 38 / 40 | ±0.3 | deg | 2 | / $^{12}$CO J=2–1 / 38 $\pm$ 0.3     / 40 $\pm$ 0.3     / |
| Inclination-corrected velocity S(1),S(2) / S(5),S(7) | 12.5 / 28.5 | not stated | km/s | 3 | has a velocity of $\sim$12.5 km s$^{-1}$, while the hotter component as traced by H$_2$ 0-0 S(5) and S(7) has a velocity of 28.5 km s$^{-1}$ |
| JWST-ALMA position offset | 0.27 (38 au) | not stated | arcsec | 0 | We observe an offset of $\sim$0.$''$27 (38 au) |

## Qualitative findings

- Higher-excitation H2 is more collimated and faster, consistent with nested MHD disk wind; CO is slower entrained gas  
  > "The lower velocity mm CO may be gas from the infalling envelope accelerated outwards by the wide angle wind along the cavity walls." (abstract)

## Claim tuples

- H: Outflow opening angle depends on excitation | E: Measured cavity edges of H2 S(J) and 12CO | R: 40–35 deg for low-J and CO to 28–19 deg for S(7)–S(11) | F: Nested structure | **supported**
- H: Higher-excitation H2 moves faster | E: PV diagrams of S(1)–S(7) | R: 12.5 vs 28.5 km/s | F: Consistent with MHD disk wind over X-wind/photoevaporation | **supported**
- H: H2 outflow base width compared to disk | E: S(11) slice width | R: ≤35 au vs ~30 au disk, 20–23 au jet | F: Wind wider than jet, comparable to disk | **supported**

## Reasoning

- Why this data: _not stated_
- Why this method: _not stated_
- Alternative: Photoevaporative wind disfavoured (low molecular fraction, velocities <10 km/s, weak UV in quiescent phase)  
  > "IRAS 16253-2429 is currently in a quiescent phase and is therefore unlikely to possess a sufficiently strong UV field to drive photoevaporation." (4)
- How they decided it was enough: _not stated_
- Limitation (authors): Width is an upper limit; large velocity uncertainties  
  > "this width should be regarded as an upper limit for several reasons." (3.7)
- Caveat (inferred, ours): Different JWST resolutions across lines may bias opening angles
- Caveat (inferred, ours): ALMA only used as published eDisk products; no independent analysis

## Reproducibility

- Data public (paper): JWST from MAST; ALMA eDisk project codes given  
  > "All of the JWST data presented in this article were obtained from the Mikulski Archive for Space Telescopes (MAST)" (Data availability)
- Products in archive: _not stated_
- Missing: ALMA imaging scripts
- Missing: JWST PSF and aperture details
- Missing: Disk PA modelling (in prep)
- Data volume (inferred): ~100 GB (JWST cubes plus eDisk ALMA)
- Score (inferred): 3/5, Public data and moderately described JWST measurements, but ALMA reduction inherited and several settings unstated.
- Rediscovery candidate: no, Main results rely on JWST processing and ALMA parameters from other papers; recipe incomplete.

## Links

- Method: (cite: 2023ApJ...954..101A) (eDisk source analysis of IRAS 16253)
- Method: (cite: 2023ApJ...951....8O) (eDisk survey data reduction)
- Companion: (cite: 2024ApJ...966...41F) (JWST NIRSpec study of the source)
- Companion: (cite: 2023arXiv231014061N) (MIRI jet study)
- Related: eDisk
- Related: JWST IPA (program 1802)

## Checks

```json
{
 "quotes": 51,
 "quotes_ok": 51,
 "quote_pass_rate": 1.0,
 "quotes_too_long": 0,
 "unsupported_facts": 0,
 "project_codes": 2,
 "codes_not_in_text": [],
 "codes_not_in_obscore": [],
 "obscore_codes_not_in_card": [],
 "codes_printed_but_missing": [],
 "numeric_results": 5,
 "numeric_problems": 0,
 "fill": {
  "facts": 70,
  "stated": 35,
  "rate": 0.5
 },
 "evidence_ok": true
}
```
