# The diffuse molecular component in the nuclear bulge of the Milky Way

`2018A&A...610A..43R` | Astronomy and Astrophysics 2018 | first author: Riquelme, D. | arXiv: 1709.02464 | DOI: 10.1051/0004-6361/201730602

Card schema 1.0 | model claude-sonnet-5-5 | depth full | type observational_alma_primary

## Science

- Fields: milky_way_ism, astrochemistry
- Question: Is there diffuse, low-density molecular gas in the Galactic bulge, detectable via 3-mm molecular absorption against the quasar J1744-312, and what is its chemistry and mass?  
  > "We aim to observe and characterize diffuse and low density gas using observations of 3-mm molecular transitions seen in absorption." (abstract)
- Target **J1744-312 (quasar behind Galactic bulge)**: coordinates RA 17h44m23.5782s, Dec -31d16'36.287'' (J2000); (l,b)=(-2.13,-1.00) deg  
  > "The coordinates for the quasar used for the observations were $\alpha$(J2000): $17^{\rm h}44^{\rm m}23.5782^{\rm s}$, $\delta$(J2000): $-31\deg16'36''.287$." (3 Observations); "J1744-312 is at $(l, b) = (-2{^\circ}.13, -1{^\circ}.00)$ i.e., behind the Galactic bulge" (2.1 The quasar J1744-312); z/distance not stated (GC distance assumed 8.5 kpc)  
  > "The coordinates for the quasar used for the observations were $\alpha$(J2000): $17^{\rm h}44^{\rm m}23.5782^{\rm s}$, $\delta$(J2000): $-31\deg16'36''.287$." (3 Observations); "J1744-312 is at $(l, b) = (-2{^\circ}.13, -1{^\circ}.00)$ i.e., behind the Galactic bulge" (2.1 The quasar J1744-312); distance from _not stated_

## Data provenance

- ALMA projects: 2012.1.00119.S
- bands: Band 3 spectral survey, 84.114-114.616 GHz  
  > "We performed a spectral survey of the ALMA band 3, covering a frequency range from 84.114 to 114.616 GHz using five spectral setups" (3 Observations)
- frequencies and spectral setup: 5 setups, each 4x1.875 GHz, channel 2.584 MHz (~10 km/s)  
  > "each of them covering 4x1.875 GHz bandwidth with a channel separation of $2.584$ MHz corresponding to $\sim 10$ km s$^{-1}$" (3 Observations)
- continuum bandwidth: _not stated_
- arrays: 29 12-m antennas  
  > "using 29 12-m antennas during 5 observing periods" (3 Observations)
- configurations: _not stated_
- baselines: _not stated_
- angular resolution: synthesized beams ~1.2-1.9 arcsec  
  > "| 1 | 0 | 91.483-93.355 | 92.416 | 2.56 | 8.42 | 66.87 | 1.55x1.36 | 2014-06-29 |" (Table 1)
- max recoverable scale: _not stated_
- sensitivity: rms 1.35-4.01 mJy per ~10 km/s channel depending on window  
  > "| 5 | 0 | 84.114-85.994 | 85.067 | 1.35 | 12.04 | 72.65 | 1.70x.140 | 2014-05-02, 2014-07-21 |" (Table 1)
- time on source: _not stated_
- observing dates: 2014 May 02; Jun 29; Jul 01, 02, 03, 21  
  > "(May 02; Jun 29; Jul 01, 02, 03, and 21, 2014)" (3 Observations)
- pi or archival as stated: _not stated_
- Line: HCN 1-0 (88.6316022 GHz)
- Line: HCO+ 1-0 (89.1885247 GHz)
- Line: 13CO 1-0 (110.2013543 GHz)
- External data: Quasar flux density 0.571 Jy at 103 GHz, 0.563 Jy at 91.5 GHz  
  > "The quasar has a flux density of 0.571 Jy at 103 GHz and 0.563 Jy at 91.5 GHz in the ALMA-Band 3 calibrator source catalog" (2.1 The quasar J1744-312) [from ALMA Calibrator Source Catalogue]
- External data: CN vs H2 power-law relation (slope 1.31) used to infer N(H2)  
  > "The relation between N(CN) and N(H$_2$) is non-linear with a power-law slope of 1.31." (4.3 Mass) [from (cite: Liszt_Lucas_2001); (cite: Federman_et_al_1994)]
- External data: Comparison column densities of cyanogen/HCO+/CnHm families from earlier absorption studies  
  > "We include the data from (cite: Liszt_Lucas_2001), (cite: Godard_et_al_2010), (cite: Muller_et_al_2011), and the present work." (4.2 Detected molecules) [from (cite: Liszt_Lucas_2001); (cite: Godard_et_al_2010); (cite: Muller_et_al_2011)]

## Processing

### Calibration

- pipeline or manual: Calibration performed by the ALMA team (North America Arc node)  
  > "The calibration was performed by the ALMA team at the North America Arc node." (3 Observations)
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

- Column density derivation from absorption lines  
  > "The derivation of the column density from absorption lines, from single dish observations, has been discussed by (cite: Linke_et_al_1981) and (cite: Nyman_1984)." (3.2 Physical properties) [from (cite: Linke_et_al_1981); (cite: Nyman_1984)]

### Not stated but needed to reproduce (our reading)

- Excitation temperature used explicitly (T_ex=T_bg=2.73 K implied by Q_2.73)
- CASA version and pipeline version
- Extraction aperture/pixel for the spectrum and continuum-level definition
- Which four lines were stacked
- How the 3-sigma upper limits were computed
- Geometry details for the mass estimate

## Analysis recipe

1. **Extract spectrum and continuum**: Single spectrum toward quasar centre; line-to-continuum ratio  
  > "We extract a single spectrum toward the center of the quasar." (3 Results and analysis)
   - software: GILDAS (GREG, CLASS)
   - fitting: _not stated_
   - validation: _not stated_
2. **Identify lines and fit Gaussians/HFS**: CDMS and JPL catalogs for identification; Gaussian fits to continuum-subtracted spectra; CLASS HFS method for HCO, CN, CCH  
  > "The absorption profiles were fitted with Gaussian functions" (3.1); "These lines were modeled using the HFS method of CLASS assuming optically thin emission, and the same excitation temperature and linewidth for all components of the multiplet." (3.1)
   - software: CLASS, CDMS, JPL catalog
   - parameter: Linewidths fixed to values from isolated-component Gaussian fit when fits did not converge  
  > "in those cases we fixed the linewidths to the value given by the Gaussian fit isolating each corresponding velocity component" (3.1)
   - assumption: Optically thin LTE for HFS  
  > "These results indicate that we can assume that CCH, CN and HCO are optically thin following LTE conditions" (3.1)
   - fitting: Gaussian fit; no sampler  
  > "The absorption profiles were fitted with Gaussian functions" (Results and analysis, Line identification and line fit)
   - validation: HFS line ratios compared with theoretical LTE optically thin ratios  
  > "We compared the observed with the predicted line intensity (S$_l$, flux density peak) ratios of different HFS components in the optically thin case" (3.1)
3. **Optical depth and column density**: tau = -ln(1+S_l/S_c); N from integrated tau with Gaussian integral  
  > "$\int \tau dV = \sqrt{\frac{\pi}{4 ln(2)}}\tau_{\rm peak} \Delta V$" (3.2)
   - assumption: T_ex = T_bg, covering factor ~1  
  > "the absorption covers the entire background source" (3.2)
   - fitting: _not stated_
   - validation: _not stated_
4. **Estimate N(H2) and mass of diffuse gas**: N(H2) from N(CN)-N(H2) relation and from HCO+ abundance; mass for spherical geometry with radius equal to projected distance to GC  
  > "Considering a distance of 8.5 kpc for the GC, the total mass of the diffuse component could be as high as $1.9\times 10^{7}$ M$_{\odot}$." (4.3 Mass)
   - assumption: GC distance 8.5 kpc; N(HCO+)/N(H2)=3e-9  
  > "using N(HCO$^+$)/N(H$_2$)$=3\times 10^{-9}$ (the local value for solar metallicity)" (4.3 Mass)
   - fitting: _not stated_
   - validation: Compared with Gerin & Liszt 2017 N(H2)  
  > "These results are in good agreement with the recent work by (cite: Gerin_Liszt_2017)" (4.3 Mass)

## Software

- **GILDAS (GREG, CLASS)** : Data analysis, Gaussian and HFS fitting  
  > "The analysis of the data was done with the GREG and CLASS packages of the GILDAS software" (3 Results and analysis)

## Numeric results

| quantity | value | uncertainty | units | step | quote |
|---|---|---|---|---|---|
| N(H2) at ~0 km/s | 1.12e22 | not stated | cm^-2 | 4 | we can infer a molecular hydrogen column of $1.12\times 10^{22}$ cm$^{-2}$ for the potentially local gas (0 km s$^{-1}$) |
| N(H2) at -153 km/s | 2.71e21 | not stated | cm^-2 | 4 | $2.71\times 10^{21}$ cm$^{-2}$ for the velocity component at $-153$ km s$^{-1}$ |
| Mass of diffuse bulge gas (upper estimate) | 1.9e7 | not stated | Msun | 4 | the total mass of the diffuse component could be as high as $1.9\times 10^{7}$ M$_{\odot}$ |
| HCN column density at -154 km/s | 3.039e12 | 0.438e12 | cm^-2 | 3 | / -154.2 (0.4) / 10.8 (1.1) / -0.08517 / 0.65866 / 2.953 / 0.138 (0.014) / $3.039 (0.438) \times 10^{12}$ / |
| 12C/13C from HCO+/H13CO+ at 0 km/s | 65 | not stated | dimensionless | 3 | translating into a $^{12}$C/$^{13}$C isotopic ratio of 65 (HCO$^+$/H$^{13}$CO$^+$) and 80 (HCN/H$^{13}$CN) |

## Qualitative findings

- Three velocity components at ~0, -153, -192 km/s; 12 molecules detected, 7 in the -153 km/s bulge component, 3 at -192 km/s  
  > "From the 12 species observed in this study, 7 molecules were detected in the velocity component at $-153$ km s$^{-1}$" (4.2)

## Claim tuples

- H: Low-excitation diffuse molecular gas exists along a bulge sightline outside the CMZ | E: ALMA Band 3 absorption survey toward J1744-312 | R: Absorption at -153 and -192 km/s with no CO emission counterpart | F: Components arise from low-excitation bulge gas | **supported**
- H: Diffuse bulge gas is a substantial fraction of GC gas mass | E: Extrapolate N(H2) over spherical volume | R: Up to 1.9e7 Msun | F: About 1/3 of total CMZ gas, tentatively | **partially**
- H: Chemistry of bulge diffuse gas resembles local and Galactic plane diffuse gas | E: Column density correlations compared with literature | R: Data follow established relations | F: Chemistry may be similar | **supported**

## Reasoning

- Why this data: _not stated_
- Why this method: _not stated_
- How they decided it was enough: _not stated_
- Limitation (authors): Low spectral resolution (~10 km/s) prevents linewidth analysis; T_ex=T_bg assumption untested; mass based on single sightline  
  > "this analysis is not possible with our data because of the lower spectral resolution of our survey ($\sim 10$ km s$^{-1}$)" (4.2)
- Caveat (inferred, ours): Quasar continuum variability up to 14% between epochs
- Caveat (inferred, ours): Single sightline extrapolated to bulk mass
- Caveat (inferred, ours): N(H2) indirect, relies on non-linear CN-H2 relation from local gas
- Caveat (inferred, ours): Gaussian fits with fixed widths at low resolution

## Reproducibility

- Data public (paper): Project code given; public status not explicitly stated  
  > "The observations were carried out during the ALMA Early Science Cycle 1 (ALMA project 2012.1.00119.S)" (3 Observations)
- Products in archive: _not stated_
- Missing: CASA version
- Missing: continuum level definition
- Missing: stacking details
- Missing: exact extraction region
- Data volume (inferred): ~tens of GB (5 setups, 4 spectral windows each, Cycle 1)
- Score (inferred): 3/5, Single project code and simple analysis with equations, but several settings unstated.
- Rediscovery candidate: yes, ALMA data from a single project, simple analysis, numeric table of tau and N.

## Links

- Companion: (cite: Gerin_Liszt_2017) (Independent detection of diffuse molecular gas toward same quasar)

## Checks

```json
{
 "quotes": 45,
 "quotes_ok": 45,
 "quote_pass_rate": 1.0,
 "quotes_too_long": 0,
 "unsupported_facts": 0,
 "project_codes": 1,
 "codes_not_in_text": [],
 "codes_not_in_obscore": [],
 "obscore_codes_not_in_card": [],
 "codes_printed_but_missing": [],
 "numeric_results": 5,
 "numeric_problems": 0,
 "fill": {
  "facts": 66,
  "stated": 29,
  "rate": 0.439
 },
 "evidence_ok": true
}
```
