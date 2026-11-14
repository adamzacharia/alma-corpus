# The ALMA Spectroscopic Survey in the Hubble Ultra Deep Field: Molecular Gas Reservoirs in High-redshift Galaxies

`2016ApJ...833...70D` | The Astrophysical Journal 2016 | first author: Decarli, Roberto | arXiv: 1607.06771 | DOI: 10.3847/1538-4357/833/1/70

Card schema 1.0 | model claude-sonnet-5-5 | depth full | type large_program_or_survey

## Science

- Fields: high_z_galaxies
- Question: What are the molecular gas properties (CO luminosities, excitation, gas masses, depletion times, gas fractions, CO- vs dust-based masses) of IR-luminous (L_IR>1e11 Lsun) spectroscopic-redshift galaxies in the ASPECS UDF field?  
  > "In the present paper, we study the molecular gas properties of galaxies in ASPECS, the ALMA Spectroscopic Survey in the Hubble Ultra Deep Field (UDF)." (Introduction)
- Target **ASPECS UDF field (11 galaxies with L_IR>1e11 Lsun)**: coordinates RA 03:32:37.900, Dec -27:46:25.00 (J2000), 3mm pointing center  
  > "we obtained a single pointing centered at RA = 03:32:37.900, Dec = –27:46:25.00 (J2000.0), close to the Northern corner of the Hubble eXtremely Deep Field" (2.1 The ALMA dataset); z/distance z = 0.895–2.543 (spectroscopic)  
  > "we obtained a single pointing centered at RA = 03:32:37.900, Dec = –27:46:25.00 (J2000.0), close to the Northern corner of the Hubble eXtremely Deep Field" (2.1 The ALMA dataset); distance from spectroscopic redshifts from literature, MUSE, 3D-HST grism, and ASPECS CO lines  
  > "we obtained a single pointing centered at RA = 03:32:37.900, Dec = –27:46:25.00 (J2000.0), close to the Northern corner of the Hubble eXtremely Deep Field" (2.1 The ALMA dataset)

## Data provenance

- ALMA projects: _none stated_
- bands: Band 3 (3 mm, 84–115 GHz) and Band 6 (1 mm, 212–272 GHz) frequency scans  
  > "The dataset consists of two frequency scans in ALMA band 3 (3 mm, 84–115 GHz) and in band 6 (1 mm, 212–272 GHz)." (2.1 The ALMA dataset)
- frequencies and spectral setup: _not stated_
- continuum bandwidth: _not stated_
- arrays: _not stated_
- configurations: _not stated_
- baselines: _not stated_
- angular resolution: 1mm continuum 1.5'' x 1.0''  
  > "the 1 mm dust continuum is unresolved at $1.5''\times1.0''$ resolution" (4.2 Size of the CO-emitting region in ID.2)
- max recoverable scale: _not stated_
- sensitivity: 3mm: 0.18 mJy/beam per 50 km/s; 1mm: 0.44 mJy/beam per 50 km/s; 1mm continuum 12.7 uJy/beam  
  > "The typical noise rms is 0.44 mJy beam$^{-1}$ per 50 km s$^{-1}$ channel. The resulting 1mm continuum image reaches a noise rms of $12.7$ $\mu$Jy beam$^{-1}$ at the center of the mosaic" (2.1 The ALMA dataset)
- time on source: _not stated_
- observing dates: _not stated_
- pi or archival as stated: _not stated_
- Line: CO J=2-1 to 8-7 (not stated)
- Other facility **HST, Spitzer, Herschel, Chandra, VLT/MUSE, 3D-HST**: Photometry, spectroscopic/grism redshifts, X-ray data for SED fitting and source characterization  
  > "We complement the ALMA data with X-ray–to–far-IR photometry from public catalogs of this field, as well as optical/near-IR spectroscopic information where available." (2.2 Ancillary Data)
- External data: CO excitation ladder r21=0.76, r31=0.42, r41=0.31  
  > "we adopt the recent CO excitation ladder of main–sequence galaxies derived by (cite: daddi15): $r_{21}$=$0.76\pm0.09$, $r_{31}=0.42\pm0.07$, and $r_{41}=0.31\pm0.06$" (4.1 CO luminosities and associated H$_2$ masses) [from (cite: daddi15)]
- External data: Photometric catalogs of the UDF/XDF  
  > "The main sources for the photometry are the compilations by (cite: coe06) and (cite: skelton14)." (2.2 Ancillary Data) [from (cite: coe06); (cite: skelton14)]
- External data: Effective radii from HST imaging  
  > "We thus use the information from the stellar morphology derived by (cite: vanderwel12) and reported in Tab. [\[tab_sample\]](#tab_sample)" (5.2.2 Average surface densities: SFR vs. gas mass) [from (cite: vanderwel12)]

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

- ALMA observations and data reduction  
  > "The details of the ALMA dataset (observations and data reduction) are presented in Paper I of this series." (2.1 The ALMA dataset) [from Paper I, Walter et al.]
- 1mm continuum image  
  > "The resulting 1mm continuum image reaches a noise rms of $12.7$ $\mu$Jy beam$^{-1}$ at the center of the mosaic (see Paper II)." (2.1 The ALMA dataset) [from Paper II, Aravena et al.]
- alpha_CO = 3.6  
  > "We adopt $\alpha_{\rm CO}$=3.6 M$_\odot$ (K km s$^{-1}$ pc$^{2}$)$^{-1}$ (cite: daddi10b)." (4.1 CO luminosities and associated H$_2$ masses) [from (cite: daddi10b)]

### Not stated but needed to reproduce (our reading)

- ALMA project codes, CASA version, calibration and imaging parameters (all deferred to Paper I)
- Cube/image products used for spectral extraction (aperture, extraction method at optical positions)
- MAGPHYS configuration details (priors, redshift handling, templates)
- Details of the mock velocity-map models for ID.2 (beam, noise, fitting procedure)
- Source of 1mm flux densities for the continuum-detected sources (from Paper II)

## Analysis recipe

1. **SED fitting of all galaxies**: Fit SEDs with high-z MAGPHYS using 26 filters plus ASPECS 1mm photometry where >2 sigma  
  > "We use the high-$z$ extension of MAGPHYS (cite: dacunha08; dacunha15) to fit the Spectral Energy Distributions (SEDs) of all of them." (2.2 Ancillary Data)
   - software: MAGPHYS
   - parameter: 14% and 86% quartiles of posterior as uncertainties plus 10% systematics  
  > "We take the 14% and 86% quartiles of the posterior distributions as the uncertainties in the parameters, and we account for an additional fiducial 10% uncertainty due to systematics" (2.2 Ancillary Data)
   - fitting: _not stated_
   - validation: Compared with FAST SFRs of Skelton et al. (footnote)  
  > "We note that the FAST analysis by (cite: skelton14) yields consistent SFRs for ID.1, ID.3, and ID.10 but different values (by a factor $2\times$ or more) for ID.2" (footnote 4)
2. **Select sample**: Spectroscopic redshift, brighter than 27.5 mag, CO J=2-1,3-2 or 4-3 covered, MAGPHYS L_IR>1e11 Lsun at >1 sigma gives 11 galaxies  
  > "From these galaxies, we select the 11 galaxies for which the MAGPHYS SED analysis yields an IR luminosity $L_{\rm IR}>10^{11}$ L$_\odot$ at $>1$-$\sigma$ significance." (3 The sample)
   - fitting: _not stated_
   - validation: _not stated_
3. **Measure CO line fluxes**: Extract spectra at optical positions; gaussian fit of lowest-J line; higher-J lines with same width; detection if flux >3x uncertainty; upper limits with 300 km/s width at 3 sigma  
  > "If the line is not detected, we assume a fiducial line width of 300 km s$^{-1}$ and we use the upper boundary of the 3-$\sigma$ confidence range on the flux as upper limit." (4.1 CO luminosities and associated H$_2$ masses)
   - fitting: Gaussian profile  
  > "We fit the lowest-J transitions accessible with ASPECS data with a gaussian profile" (4.1 CO luminosities and associated H$_2$ masses)
   - validation: _not stated_
4. **Derive molecular gas masses**: Convert to L'CO(1-0) via r_J1, then M_H2 = alpha_CO/r_J1 * L'  
  > "The molecular gas masses are then derived as:" (4.1 CO luminosities and associated H$_2$ masses)
   - assumption: alpha_CO=3.6 Msun (K km/s pc^2)^-1; Daddi+15 excitation ladder  
  > "We adopt $\alpha_{\rm CO}$=3.6 M$_\odot$ (K km s$^{-1}$ pc$^{2}$)$^{-1}$ (cite: daddi10b)." (4.1 CO luminosities and associated H$_2$ masses)
   - fitting: _not stated_
   - validation: _not stated_
5. **Dynamical mass of ID.2**: Mock velocity maps for disk with M_dyn ∝ R^gamma (gamma=1,2,3), compared with CO(2-1) line profile  
  > "We then generated mock velocity maps for these three cases, assuming that the CO light traces the mass distribution; and we inferred expected line profiles" (4.2 Size of the CO-emitting region in ID.2)
   - assumption: PA=-55 deg, inclination=60 deg from HST  
  > "(PA=-55$^\circ$, inclination=60$^\circ$ with respect to the line of sight)" (4.2 Size of the CO-emitting region in ID.2)
   - fitting: _not stated_
   - validation: Compared with H-alpha dynamical mass of 1.2e11 Msun  
  > "This yields a dynamical mass of $1.2\times 10^{11}$ M$_\odot$, roughly consistent with our estimate" (Size of the CO-emitting region in ID.2)
6. **Dust-based gas masses**: Groves+15 500um luminosity relation, Scoville+14 eq. 12, and MAGPHYS dust mass with DGR=1/100  
  > "For simplicity, in our analysis we thus assume a fixed DGR=1/100." (5.5 CO vs. Dust-based ISM masses)
   - software: MAGPHYS
   - assumption: Modified blackbody T_dust=25 K, beta=1.6 for k-correction  
  > "we adopt a modified black body with $T_{\rm dust}$=25 K and $\beta$=$1.6$ (cite: beelen06)" (5.5 CO vs. Dust-based ISM masses)
   - fitting: _not stated_
   - validation: Compared with CO-based masses  
  > "They also correlate well with the CO-based H$_2$ mass estimates over one and a half dex of dynamic range. However, systematic offsets are observed." (CO vs. Dust-based ISM masses)

## Software

- **MAGPHYS** high-z extension: SED fitting for M*, SFR, L_IR, M_dust  
  > "We use the high-$z$ extension of MAGPHYS (cite: dacunha08; dacunha15) to fit the Spectral Energy Distributions (SEDs) of all of them." (2.2 Ancillary Data)

## Numeric results

| quantity | value | uncertainty | units | step | quote |
|---|---|---|---|---|---|
| Median CO flux of detections | 0.19 | not stated | Jy km/s | 3 | The detected sources in our sample have a median CO flux of 0.19 Jy km s$^{-1}$ |
| M_H2 of ID.1 | 206e9 | ±34e9 | Msun | 4 | / 1 / 2.543 / 3 / $24.03_{-0.10}^{+0.10}$ / $57_{-10}^{+10}$ / $206_{-34}^{+34}$ / $12_{-2}^{+2}$ / $3.3_{-0.6}^{+0.7}$ / |
| M_dyn of ID.2 at R=8.3 kpc | 2e11 | not stated | Msun | 5 | The implied dynamical mass is $M_{\rm dyn}\approx 2\times 10^{11}$ M$_\odot$ at $R$=8.3 kpc |
| Groves-based masses relative to CO | 1.5x lower | not stated | dimensionless | 6 | The (cite: groves15) estimates are on average $1.5\times$ lower than those based on CO. |

## Qualitative findings

- No CO-detected source shows starburst-like excitation; excitation is often at or below Milky Way level  
  > "In no case do we find starburst-like CO excitation, comparable with the center of M82" (4.3 CO excitation)

## Claim tuples

- H: Do IR-luminous UDF galaxies show CO emission as expected from L_IR-L'CO? | E: CO fits at known positions of 11 galaxies with L_IR>1e11 | R: 7 detected at various significance, 4 undetected | F: Most lie on the low-L_IR envelope of the relation with exceptions | **supported**
- H: Are dust-based gas masses consistent with CO-based masses? | E: Compare three dust recipes with CO masses for six continuum-detected galaxies | R: Dust-based masses smaller by factor ~2-5 | F: Systematic offset not resolved by tuning CO assumptions | **supported**

## Reasoning

- Why this data: _not stated_
- Why this method: _not stated_
- Alternative: Lower alpha_CO=0.8 or M82 excitation considered to reconcile CO and dust masses but disfavored  
  > "such a high CO excitation scenario is ruled out by our 1mm line observations" (5.5 CO vs. Dust-based ISM masses)
- How they decided it was enough: _not stated_
- Limitation (authors): Dust SED poorly sampled; dynamical mass highly model-dependent  
  > "Our dust SED is only poorly sampled." (5.5 CO vs. Dust-based ISM masses)
- Caveat (inferred, ours): Small sample of 11 galaxies selected by expected CO brightness
- Caveat (inferred, ours): r41 extrapolated with assumed 20% error
- Caveat (inferred, ours): Optical positions and fixed line widths for upper limits affect limits
- Caveat (inferred, ours): Dust and CO sizes differ, so masses may trace different components

## Reproducibility

- Data public (paper): _not stated_
- Products in archive: _not stated_
- Missing: Reduced ASPECS cubes and continuum maps (Papers I, II)
- Missing: Project codes and calibration details
- Missing: MAGPHYS setup and photometric catalogs
- Data volume (inferred): Large (frequency scans in Band 3 and 6, ~100s GB raw); reproduction of this paper's analysis needs the Paper I cubes
- Score (inferred): 3/5, Analysis is simple and described but depends on Paper I/II data products and the MAGPHYS setup, and no project codes are printed.
- Rediscovery candidate: no, Data processing is deferred to companion papers and no project codes are stated in the text.

## Links

- Method: Paper I, Walter et al. (ALMA observations, data reduction and blind CO catalog)
- Companion: Paper II, Aravena et al. (1.2mm continuum sources)
- Companion: Paper III, Decarli et al. (CO luminosity functions)
- Related: ASPECS
- Related: 3D-HST
- Related: PHIBSS

## Checks

```json
{
 "quotes": 40,
 "quotes_ok": 40,
 "quote_pass_rate": 1.0,
 "quotes_too_long": 0,
 "unsupported_facts": 0,
 "project_codes": 0,
 "codes_not_in_text": [],
 "codes_not_in_obscore": [],
 "obscore_codes_not_in_card": [
  "2013.1.00146.S",
  "2013.1.00718.S"
 ],
 "codes_printed_but_missing": [],
 "numeric_results": 4,
 "numeric_problems": 0,
 "fill": {
  "facts": 76,
  "stated": 32,
  "rate": 0.421
 },
 "evidence_ok": true
}
```
