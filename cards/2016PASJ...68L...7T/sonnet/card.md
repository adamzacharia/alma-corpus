# Galactic center mini-spiral by ALMA: Possible origin of the central cluster

`2016PASJ...68L...7T` | Publications of the Astronomical Society of Japan 2016 | first author: Tsuboi, Masato | arXiv: 1602.05325 | DOI: 10.1093/pasj/psw031

Card schema 1.0 | model claude-sonnet-5-5 | depth full | type archival_reuse

## Science

- Fields: milky_way_ism, star_formation
- Question: Does the dust continuum of the Galactic Center Mini-spiral trace star formation, and how did the Central cluster originate (in-situ vs infall of a star-forming cloud)?  
  > "Therefore, it is still an open question how the Central cluster has formed." (Introduction)
- Target **Sgr A* Mini-spiral**: coordinates RA 17h45m40.04s, Dec -29d00m28.10s (J2000)  
  > "The fields of view (FOVs) are centered at Sgr A$^{\ast}$, $\alpha_{\rm J2000}=17^h45^m40^s.04$, $\delta_{\rm J2000}=-29^\circ 00\ensuremath{'}28\ensuremath{''}.10$." (Data Analysis and Results); "Throughout this paper, we adopt 8.5 kpc as the distance to the Galactic center." (Introduction); z/distance 8.5 kpc  
  > "The fields of view (FOVs) are centered at Sgr A$^{\ast}$, $\alpha_{\rm J2000}=17^h45^m40^s.04$, $\delta_{\rm J2000}=-29^\circ 00\ensuremath{'}28\ensuremath{''}.10$." (Data Analysis and Results); "Throughout this paper, we adopt 8.5 kpc as the distance to the Galactic center." (Introduction); distance from adopted  
  > "The fields of view (FOVs) are centered at Sgr A$^{\ast}$, $\alpha_{\rm J2000}=17^h45^m40^s.04$, $\delta_{\rm J2000}=-29^\circ 00\ensuremath{'}28\ensuremath{''}.10$." (Data Analysis and Results); "Throughout this paper, we adopt 8.5 kpc as the distance to the Galactic center." (Introduction)

## Data provenance

- ALMA projects: 2011.0.00887.S
- bands: 100, 250, 340 GHz bands  
  > "We analyze the Cy.0 data of the Sgr A$^{\ast}$ region in 100-, 250-, and 340-GHz bands" (Data Analysis and Results)
- frequencies and spectral setup: Four spectral windows per band, 1.875 GHz each; centers 93/95/105/107, 245/247/257/259, 336/338/348/350 GHz  
  > "Each frequency band has four spectral windows. The band width of the spectral window is 1.875 GHz." (Data Analysis and Results)
- continuum bandwidth: _not stated_
- arrays: Nineteen 12-m antennas  
  > "Nineteen 12-m antennas were available." (Data Analysis and Results)
- configurations: _not stated_
- baselines: _not stated_
- angular resolution: 1.57"x1.33" (100 GHz), 0.63"x0.53" (250 GHz), 0.44"x0.38" (340 GHz)  
  > "$0.44\ensuremath{''}\times0.38\ensuremath{''}$ in the 340 GHz band" (abstract)
- max recoverable scale: Resolved out above 38" (100 GHz), 15" (250 GHz), 11" (340 GHz)  
  > "Features with spatial scales larger than $11\ensuremath{''}$, or 0.46 pc, were resolved out." (Data Analysis and Results)
- sensitivity: rms 0.33 (100 GHz), 0.13 (250 GHz), 0.15 (340 GHz) mJy/beam  
  > "The rms noise level at the map center is $S_\nu =0.15$ mJy beam$^{-1}$ at 340 GHz." (Data Analysis and Results)
- time on source: time span longer than 7 hrs (03:30:47-10:52:16 UT)  
  > "the time span of the observation is longer than 7 hrs (from 03:30:47 UT to 10:52:16 UT)" (Data Analysis and Results)
- observing dates: May 18, 2012  
  > "the epoch, May 18, 2012, was suitable for imaging observation" (Data Analysis and Results)
- pi or archival as stated: Archival Cy.0 data  
  > "which was acquired from the ALMA archive" (Data Analysis and Results)
- External data: Positions of OB/WR stars/IRS sources compared to dust peaks  
  > "we show the positions of the stars on the emission maps at 250 and 340 GHz" (Discussion) [from (cite: Genzel), (cite: Paumard), (cite: Zhao)]
- External data: Dust mass absorption coefficient kappa=0.1(nu/1200 GHz)^beta  
  > "$\kappa_\nu=0.1\times(\nu/1200 GHz)^{\beta}$" (Discussion) [from (cite: Hildebrand)]

## Processing

### Calibration

- pipeline or manual: Manual in AIPS: FRING for residual fringe rates/delays, then self-calibration  
  > "First we removed residual fringe rates and delays of the raw visibility by the task FRING" (Data Analysis and Results)
- casa version: _not stated_
- pipeline version: _not stated_
- archive products used as is: _not stated_
- flux calibrator: Titan and Neptune  
  > "The flux density scale was determined using Titan and Neptune." (Data Analysis and Results)
- flux scale uncertainty: _not stated_
- self calibration: Self-calibration minimized residual complex gain errors in AIPS  
  > "the residual complex gain errors of the data were minimized using the “self-calibration" method in the software" (Data Analysis and Results)

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
- primary beam correction: Not applied  
  > "The correction for the primary beam attenuation is not applied to the map." (Data Analysis and Results)
- array combination: _not stated_
- smoothing: _not stated_
- final beam: 1.57"x1.33" PA=74 deg; 0.63"x0.53" PA=-84; 0.44"x0.38" PA=-89  
  > "The resultant FWHM beam at 340 GHz is $0.44\ensuremath{''}\times0.38\ensuremath{''} (PA=-89^\circ)$" (Data Analysis and Results)
- final rms: 0.33, 0.13, 0.15 mJy/beam  
  > "The rms noise level is $S_\nu =0.33$ mJy beam$^{-1}$ (4ch-combined) at the map center." (Data Analysis and Results)

### Not stated but needed to reproduce (our reading)

- Which scans/sources were used as self-cal models, solution intervals and number of iterations
- Weighting/robust, cell size, image size, deconvolution settings
- Whether ALMA data were converted to AIPS format and how
- Clumpfind thresholds/levels and clump radius definition
- Flux density scale values for Titan/Neptune
- How the CMF was binned and fit

## Analysis recipe

1. **Calibrate and self-calibrate archival visibilities**: AIPS FRING then self-calibration  
  > "Further data calibration and imaging of the archival data were done by classic VLBA AIPS(NRAO) using the “self-calibration” method." (Data Analysis and Results)
   - software: AIPS
   - fitting: _not stated_
   - validation: Different UV coverage in two bands used to argue small structures are real  
  > "Because the data in the two bands have different UV coverage, these small objects are real substructures rather than artifacts caused by the side lobes." (Data Analysis and Results)
2. **Make continuum maps combining four spws per band**: Combined four spectral window maps per band to improve sensitivity  
  > "we combined the four spectral window maps of $f_c=93, 95, 105,$ and $107$ GHz in the 100 GHz band to improve the sensitivity" (Data Analysis and Results)
   - software: AIPS
   - fitting: _not stated_
   - validation: _not stated_
3. **Identify dust clumps at 340 GHz**: clumpfind algorithm on 340 GHz map  
  > "we search dust clumps in the 340 GHz continuum map using the *clumpfind* algorithm ((cite: Williams1994))" (Discussion)
   - software: clumpfind
   - fitting: _not stated_
   - validation: _not stated_
4. **Derive clump masses and densities**: Optically thin dust emission M=F d^2/(kappa B(Td)); mean density from sphere  
  > "$M_c=F_\nu d^2/\kappa_\nu B_\nu(T_d)$" (Discussion)
   - assumption: Td=20 K, beta=2, Z/Z0=1, mu=2.3, d=8.5 kpc  
  > "We assume here the dust temperature of $T_d = 20$ K as a conservative value, $\beta=2$, and the metallicity of $Z/Z_0 = 1$." (Discussion)
   - fitting: _not stated_
   - validation: _not stated_
5. **Fit clump mass function**: Power-law fit to the three most massive points of dN/dM  
  > "The solid line in the figure shows the best-fit function for massive three data points, $dN/dM\propto M^{-1.5\pm0.4}$." (Discussion)
   - fitting: _not stated_
   - validation: _not stated_

## Software

- **AIPS** : Calibration (FRING), self-calibration and imaging  
  > "done by classic VLBA AIPS(NRAO) using the “self-calibration” method" (Data Analysis and Results)
- **clumpfind** : Dust clump identification at 340 GHz  
  > "using the *clumpfind* algorithm ((cite: Williams1994))" (Discussion)

## Numeric results

| quantity | value | uncertainty | units | step | quote |
|---|---|---|---|---|---|
| Sgr A* flux density 100 GHz | 2.35 | 0.19 | Jy | 2 | $S_\nu=2.35\pm0.19$ Jy at 100 GHz |
| Sgr A* flux density 250 GHz | 3.55 | 0.35 | Jy | 2 | $S_\nu=3.55\pm0.35$ Jy at 250 GHz |
| Sgr A* flux density 340 GHz | 3.44 | 0.51 | Jy | 2 | $S_\nu=3.44\pm0.51$ Jy at 340 GHz |
| Dynamic range 250 GHz | 2.7e4 | not stated | dimensionless | 2 | high dynamic range of $2.7\times10^4$ in the resultant map |
| Dynamic range 340 GHz | 2.3e4 | not stated | dimensionless | 2 | The dynamic range in the resultant map reaches to $2.3\times10^4$ |
| Number of clumps at 340 GHz | 18 | not stated | dimensionless | 3 | We detected 18 clumps within the FOV at 340 GHz. |
| Most massive clump mass | ~170 | not stated | Msun | 4 | The most massive core has $\sim170$ M$_\odot$. |
| CMF high-mass slope | -1.5 | 0.4 | dimensionless | 5 | $dN/dM\propto M^{-1.5\pm0.4}$ on the high-mass side |
| Northern-arm width 340 GHz | 1.15 | 0.05 | arcsec | 0 | $\theta=1.15\pm0.05\ensuremath{''}$ at 340 GHz |

## Qualitative findings

- Dust emission peaks in the Northern-arm and Bar coincide with OB/WR stars  
  > "There seems to be tight correlation between the dust emission peaks and the OB/WR stars in the Northern-arm and the Bar." (Discussion)

## Claim tuples

- H: Dust peaks in the Mini-spiral correlate with OB/WR stars | E: Overlay IR star positions on 250/340 GHz maps | R: More than 10 early type stars lie on or within 0.5" of dust peaks | F: Tight correlation in Northern-arm and Bar | **supported**
- H: Clump mass function resembles disk-region CMFs | E: clumpfind on 340 GHz map, mass estimate, power-law fit | R: dN/dM ∝ M^-1.5±0.4 at high mass | F: Supports infall of a star-forming cloud as origin of the Central cluster | **partially**

## Reasoning

- Why this data: _not stated_
- Why this method: _not stated_
- Alternative: In-situ star formation near Sgr A* (JVLA bow-shock sources) not necessarily supported  
  > "the JVLA-detected sources do not necessarily support the first scenario of the current in-situ star formation near Sgr A$^{\ast}$" (Introduction)
- How they decided it was enough: _not stated_
- Limitation (authors): Eastern-arm correlation unclear due to FOV limit  
  > "is not clear because of the limitation of the FOV" (Discussion)
- Caveat (inferred, ours): Dust temperature fixed at 20 K; masses scale as 1/Td
- Caveat (inferred, ours): CMF fit uses only three points, large uncertainty
- Caveat (inferred, ours): 250/340 GHz contamination by free-free and Sgr A* variability
- Caveat (inferred, ours): Star-peak correlation lacks chance-coincidence test in a crowded field
- Caveat (inferred, ours): No primary beam correction applied

## Reproducibility

- Data public (paper): Data from ALMA archive  
  > "which was acquired from the ALMA archive (ADS/JAO.ALMA#2011.0.00887.S)" (Data Analysis and Results)
- Products in archive: _not stated_
- Missing: Self-cal parameters and imaging settings
- Missing: clumpfind parameters
- Missing: Binning of CMF
- Data volume (inferred): ~50-200 GB raw
- Score (inferred): 3/5, Public data and clear mass formula, but AIPS self-cal and clumpfind settings unspecified.
- Rediscovery candidate: no, Key processing steps (AIPS self-cal, clumpfind parameters) are not specified.

## Links

- Method: (cite: Williams1994) (clumpfind algorithm)
- Companion: (cite: Tsuboi2015) (tidal shear stability density limit)

## Checks

```json
{
 "quotes": 50,
 "quotes_ok": 50,
 "quote_pass_rate": 1.0,
 "quotes_too_long": 0,
 "unsupported_facts": 0,
 "project_codes": 1,
 "codes_not_in_text": [],
 "codes_not_in_obscore": [],
 "obscore_codes_not_in_card": [],
 "codes_printed_but_missing": [],
 "numeric_results": 9,
 "numeric_problems": 0,
 "fill": {
  "facts": 66,
  "stated": 34,
  "rate": 0.515
 },
 "evidence_ok": true
}
```
