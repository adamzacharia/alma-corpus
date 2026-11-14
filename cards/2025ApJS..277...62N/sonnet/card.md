# Evidence of Galactic Interaction in the Small Magellanic Cloud Probed by Gaia-selected Massive Star Candidates

`2025ApJS..277...62N` | The Astrophysical Journal Supplement Series 2025 | first author: Nakano, Satoya | arXiv: 2502.12251 | DOI: 10.3847/1538-4365/adb8de

Card schema 1.0 | model claude-sonnet-5-5 | depth light | type multi_facility_alma_minor

## Science

- Fields: nearby_galaxies, star_formation
- Question: Can Gaia DR3 CMD-selected massive stars in the SMC trace the ISM and reveal the galaxy's kinematics (rotation versus tidal/ram-pressure stretching by the LMC)?  
  > "By uniformly selecting massive star candidates across the entire galaxy, we characterize their spatial distribution and kinematics, and identify evidence of galaxy interactions that may have induced the formation of massive stars." (1 Introduction)
- Target **Small Magellanic Cloud**: coordinates Gaia query region RA=00h-03h, Dec=-76 to -69 deg  
  > "In this study, we assume a distance modulus to the SMC of 19.06 mag, corresponding to a distance of 65 kpc." (1 Introduction); z/distance 65 kpc (distance modulus 19.06 mag)  
  > "In this study, we assume a distance modulus to the SMC of 19.06 mag, corresponding to a distance of 65 kpc." (1 Introduction); distance from assumed  
  > "In this study, we assume a distance modulus to the SMC of 19.06 mag, corresponding to a distance of 65 kpc." (1 Introduction)

## Data provenance

- ALMA projects: 2018.1.01115.S, 2018.1.01319.S, 2017.A.00054.S
- bands: _not stated_
- frequencies and spectral setup: _not stated_
- continuum bandwidth: _not stated_
- arrays: _not stated_
- configurations: _not stated_
- baselines: _not stated_
- angular resolution: _not stated_
- max recoverable scale: _not stated_
- sensitivity: _not stated_
- time on source: _not stated_
- observing dates: _not stated_
- pi or archival as stated: archival ALMA CO(J=2-1) data  
  > "pronounced anti-correlation between massive star candidates and CO ($J=2\text{--}1$) emissions in archival data from ALMA (ID: 2018.1.01115.S and 2018.1.01319.S)." (3.5.2 Reddening)
- Line: CO J=2-1 (not stated)
- Other facility **Gaia DR3**: photometry, parallax, proper motions and radial velocities of the SMC stars used for the whole analysis  
  > "we select non-embedded massive stars ($\mathrm{\geq}8M_{\odot}$) throughout the SMC using *Gaia* Data Release 3" (1 Introduction)
- Other facility **ASKAP & Parkes**: H I velocity components for comparison with stellar RVs  
  > "observed with ASKAP & Parkes" (4.3 Properties of the RVs)
- External data: B10 spectroscopic massive star catalog (5,324 stars) for validation  
  > "reporting a total of 5,324 massive stars in the catalog (hereafter referred to as the B10 catalog)" (3.5 Comparison) [from (cite: 2010AJ....140..416B)]
- External data: OGLE-IV classical Cepheids used for distances  
  > "classical Cepheids in the SMC from the fourth phase of the Optical Gravitational Lensing Experiment" (5.2 Three-dimensional Motions) [from (cite: 2015AcA....65....1U; 2015AcA....65..297S)]
- Simulation/model as data: PARSEC v1.2S isochrones (Z=0.1 Zsun, Kroupa IMF) define the massive-star CMD region  
  > "The definition of the region on the CMD where massive stars are located is based on the theoretical models of stellar evolutionary tracks from PARSEC (version 1.2S;" (3.1)

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

- Orthographic projection transformation for proper motions  
  > "we perform a transformation to an orthographic projection, similar to the method used by (cite: 2018A&A...616A..12G)." (4.1) [from (cite: 2018A&A...616A..12G)]

### Not stated but needed to reproduce (our reading)

- ALMA data processing, imaging parameters and CO contour levels are not given
- Which ALMA project corresponds to which region or CO map is not specified

## Analysis recipe

1. **Select massive star candidates**: Gaia G vs BP-RP CMD cut from PARSEC isochrones with parallax < 0.1 mas  
  > "In the CMD of Figure 2, we selected 7,426 stars as massive star candidates located in the region above the magenta line." (3.1)
   - software: dustapprox
   - parameter: AV = 0.15 mag foreground; distance modulus 19.06  
  > "we added a reddening correction of $A_{V} = 0.15~\mathrm{mag}$" (3.1)
   - fitting: _not stated_
   - validation: Compared with H-alpha/ISM and B10 catalog  
  > "Since H$\alpha$ emission arises from the radiation of H II regions formed by massive stars, the spatial distribution of our massive star candidates matching the H$\alpha$ emission supports the validity of our selection method." (Comparison of the Spatial Distribution of the ISM and Massive Star Candidates)
2. **Internal proper motions**: 2-sigma clip, subtract systemic PM within 3 deg of H I center  
  > "we selected 7,261 massive star candidates that fall within $\pm2\sigma$ of both $\mu_{\alpha}$ and $\mu_{\delta}$." (4.1)
   - fitting: _not stated_
   - validation: _not stated_
3. **Identify superstructures**: DBSCAN, eps=100 pc, minPts=80 (bar), 40 (wing)  
  > "we set $\epsilon = 100~\mathrm{pc}$ and $minPts = 80$ for the identification of superstructures in the bar" (5.1)
   - software: DBSCAN
   - fitting: _not stated_
   - validation: _not stated_

## Software

- **DBSCAN** : clustering superstructures  
  > "We use the density-based clustering algorithm `DBSCAN`" (5.1)
- **dustapprox** : extinction applied to PARSEC tracks in Gaia bands  
  > "to the outputted PARSEC tracks using `dustapprox`" (3.1)
- **CASA** : listed in software section  
  > "CASA (cite: 2007ASPC..376..127M)" (Software)

## Numeric results

| quantity | value | uncertainty | units | step | quote |
|---|---|---|---|---|---|
| Massive star candidates | 7426 | not stated | stars | 1 | we selected 7,426 stars as massive star candidates |
| Mean PM of clipped sample (RA, Dec) | (0.801, -1.251) | not stated | mas/yr | 2 | $(\mu_\alpha,\,\mu_\delta)=(0.801,\,-1.251)~\mathrm{mas~yr^{-1}}$ |
| Detection rate of B0/O stars in B10 | approximately 85% | not stated | percent | 0 | the detection rate of OB0 stars in the B10 catalog within our sample is approximately 85% |

## Qualitative findings

- East and west superstructures move oppositely in PM and RV, inconsistent with rotation  
  > "The stellar superstructures defined by the surface density have opposite mean proper motions in the east and west, moving away from each other." (abstract)

## Claim tuples

- H: Massive stars selected from the Gaia CMD trace the ISM | E: Compare with H-alpha, H I and the B10 catalog | R: Spatial match and ~85% recovery of B10 OB0 stars | F: Selection is valid | **supported**
- H: The SMC young stars show galactic rotation | E: Internal PMs and RVs of superstructures | R: Opposite east-west motions; RV gradient orthogonal to H I | F: Rotation rejected; tidal/ram-pressure stretching by LMC | **supported**

## Reasoning

- Why this data: _not stated_
- Why this method: _not stated_
- Alternative: Ram pressure misaligning the gas rotation axis ~90 deg judged unlikely  
  > "it is unlikely that ram pressure has caused a significant misalignment of the gas rotation axis by as much as $\approx$90$^{\circ}$ in the SMC" (5.3)
- How they decided it was enough: _not stated_
- Limitation (authors): No individual distances to massive star candidates  
  > "A precise discussion would require distance measurements for the massive star candidates, which we currently lack." (5.2)
- Caveat (inferred, ours): Common 65 kpc distance affects PM directions
- Caveat (inferred, ours): ALMA role is minor and qualitative

## Reproducibility

- Data public (paper): Gaia DR3 public; catalog released  
  > "The massive star candidates we selected are catalogued and made publicly available to anyone using *Gaia* DR3." (1 Introduction)
- Products in archive: _not stated_
- Missing: ALMA CO processing details
- Data volume (inferred): Gaia catalog queries (~2 million stars); small. ALMA archival data not needed to reproduce main results.
- Score (inferred): 3/5, Gaia analysis is well described, but ALMA part is only qualitative.
- Rediscovery candidate: no, Main results are Gaia-based, not ALMA.

## Links

- Companion: (cite: 2024AJ....168..255H) (Gaia/AstroSat young stellar structure comparison)
- Related: Gaia DR3
- Related: OGLE-IV

## Checks

```json
{
 "quotes": 33,
 "quotes_ok": 33,
 "quote_pass_rate": 1.0,
 "quotes_too_long": 0,
 "unsupported_facts": 0,
 "project_codes": 3,
 "codes_not_in_text": [],
 "codes_not_in_obscore": [],
 "obscore_codes_not_in_card": [],
 "codes_printed_but_missing": [],
 "numeric_results": 3,
 "numeric_problems": 0,
 "fill": {
  "facts": 65,
  "stated": 23,
  "rate": 0.354
 },
 "evidence_ok": true
}
```
