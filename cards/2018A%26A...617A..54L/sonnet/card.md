# Molecular gas and dark neutral medium in the outskirts of Chamaeleon

`2018A&A...617A..54L` | Astronomy and Astrophysics 2018 | first author: Liszt, H. | arXiv: 1807.02210 | DOI: 10.1051/0004-6361/201833167

Card schema 1.0 | model claude-sonnet-5-5 | depth full | type observational_alma_primary

## Science

- Fields: milky_way_ism
- Question: Can molecular gas, traced by HCO+ absorption, be detected in the outskirts of Chamaeleon where DNM was inferred but CO emission was not detected, and does it account for the DNM?  
  > "To see if molecular gas can be detected in Chamaeleon where gas column densities in the DNM were inferred and CO emission was not detected." (abstract)
- Target **13 background continuum sources (J0942-7731, J1058-8003, J1136-6827, J1145-6954, J1147-6753, J1152-8344, J1224-8313, B1251-7138, J1312-7724, J1550-8258, J1617-7717, J1723-7713, J1733-7935)**: coordinates Table 1 lists RA/Dec (J2000) and l,b for each source  
  > "J0942-7731 09.424275 -77.311158 293.321 -18.329" (Table 1); z/distance _not stated_; distance from _not stated_

## Data provenance

- ALMA projects: 2016.1.00714.S
- bands: lambda 3 mm (about 89 GHz)  
  > "We took λ3mm absorption profiles of HCO + and other molecules toward thirteen background quasars" (abstract)
- frequencies and spectral setup: 1919 channels of 61 kHz (0.205 km/s) at HCO+ 89.189 GHz  
  > "Each spectrum consisted of 1919 semi-independent channels spaced 61 kHz corresponding to 0.205 km s −1 at the 89.189 GHz rest frequency of HCO +" (2.1 New ALMA absorption measurements and H 2 column densities)
- continuum bandwidth: _not stated_
- arrays: _not stated_
- configurations: _not stated_
- baselines: _not stated_
- angular resolution: approximately 1 arcsec instrumental  
  > "the instrumental resolution, approximately 1 ′′ during the observing, does not determine this." (3 Molecules and Dark Neutral Medium)
- max recoverable scale: _not stated_
- sensitivity: _not stated_
- time on source: _not stated_
- observing dates: Cycle 4; pipeline products delivered 2017 Feb and March  
  > "pipeline data products were delivered in 2017 February and March" (2.1 New ALMA absorption measurements and H 2 column densities)
- pi or archival as stated: _not stated_
- Line: HCO+ J=1-0 (89.189 GHz)
- Line: HCN J=1-0 (not stated)
- Line: C2H not stated (not stated)
- Other facility **GASS III**: HI 21cm emission spectra  
  > "H I column densities were derived for all directions from Galactic All-Sky Survey GASS III λ21 cm H I emission spectra" (2.2 H I column densities)
- Other facility **NANTEN / Planck Type 2 CO**: CO J=1-0 emission maps  
  > "used NANTEN maps of J=1-0 CO emission from Mizuno et al. (2001)" (2.4 CO emission)
- External data: N(DNM) values along sightlines  
  > "Specific values of N(DNM) along the present sightlines were extracted from that work for the present use" (2.3 DNM) [from Planck Collaboration et al. (2015)]
- External data: Reddening E(B-V) from dust maps  
  > "The 6 ′ resolution dust-emission maps scaled to optical reddening E B−V by Schlegel et al. (1998) are cited in Tables 1 and 2." (2.5 Reddening and dust optical depth) [from Schlegel et al. (1998)]
- External data: N(HI) associated with Chamaeleon from pseudo-Voigt decomposition of GASS III  
  > "These were derived following the methodology described by Planck Collaboration et al. (2015) and Remy et al. (2018)." (2.2 H I column densities) [from Planck Collaboration et al. (2015); Remy et al. (2018)]

## Processing

### Calibration

- pipeline or manual: ALMA pipeline-processed data products  
  > "Spectra were extracted from the continuum-subtracted pipeline-processed data cubes" (2.1 New ALMA absorption measurements and H 2 column densities)
- casa version: _not stated_
- pipeline version: _not stated_
- archive products used as is: delivered pipeline products used  
  > "whose pipeline data products were delivered in 2017 February and March" (2.1 New ALMA absorption measurements and H 2 column densities)
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
- continuum subtraction: cubes continuum-subtracted in pipeline  
  > "Spectra were extracted from the continuum-subtracted pipeline-processed data cubes" (2.1 New ALMA absorption measurements and H 2 column densities)
- line free channels: _not stated_
- primary beam correction: _not stated_
- array combination: _not stated_
- smoothing: _not stated_
- final beam: _not stated_
- final rms: _not stated_

### Inherited from earlier work

- HCO+ column density conversion N(HCO+)=1.10e12 cm-2 ∫τdv  
  > "N(HCO + ) = 1.10 × 10 12 cm −2 [ �] τ dv with the profile integral in units of km s −1 (Ando et al., 2016; Gerin & Liszt, 2017)" (2.1 New ALMA absorption measurements and H 2 column densities) [from Ando et al., 2016; Gerin & Liszt, 2017]
- N(HCO+)/N(H2)=3e-9 abundance assumed as before  
  > "We derived the H 2 column density assuming N(HCO + )/N(H 2 )= 3 × 10 −9 as before." (abstract) [from Liszt & Lucas 1996; Liszt & Gerin 2016; Gerin & Liszt 2017]
- HI decomposition methodology  
  > "These were derived following the methodology described by" (2.2 H I column densities) [from Planck Collaboration et al. (2015); Remy et al. (2018)]

### Not stated but needed to reproduce (our reading)

- Imaging parameters (weighting, cell, deconvolver) of the pipeline products
- Pipeline/CASA version
- Spectral window setup and line-free channels used for continuum
- Integration velocity ranges for tau integrals
- How optical depth was computed (saturation, noise handling)
- Observing times, configurations, calibrators
- HCN hyperfine treatment for N(HCN)
- Details of pseudo-Voigt HI fits

## Analysis recipe

1. **Extract absorption spectra**: Extract spectra at the peak continuum pixel from continuum-subtracted pipeline cubes and divide by continuum flux in that spectral window  
  > "Spectra were extracted from the continuum-subtracted pipeline-processed data cubes at the pixel of peak continuum flux in the continuum map made from the spectral window containing each line" (2.1 New ALMA absorption measurements and H 2 column densities)
   - fitting: _not stated_
   - validation: _not stated_
2. **Derive N(HCO+) and N(H2)**: Integrate optical depth; N(HCO+)=1.10e12 W; N(H2)=N(HCO+)/3e-9  
  > "N(H 2 ) = N(HCO + )/3 × 10 −9" (Table 2)
   - assumption: Excitation temperature equals CMB; N(HCO+)/N(H2)=3e-9  
  > "N(HCO + ) is derived under the assumption that the rotational excitation temperature is that of the cosmic microwave background" (2.1 New ALMA absorption measurements and H 2 column densities)
   - fitting: _not stated_
   - validation: Error bars assume ±50% in N(HCO+)/N(H2) and W_CO  
  > "The error bars assume ±50% errors in W CO and N(HCO + )/N(H 2 )." (Figure 6 caption)
3. **HI column densities**: Optically thin N(HI)=1.823e18 ∫T_B dv from GASS III; Chamaeleon part from pseudo-Voigt decomposition within the Chamaeleon velocity range  
  > "GASS III H I emission profiles were decomposed into pseudoVoigt profiles" (2.2 H I column densities)
   - assumption: optically thin limit  
  > "again in the optically thin limit that provided the best fit in the analysis of Planck Collaboration et al. (2015)" (2.2 H I column densities)
   - fitting: pseudo-Voigt components  
  > "gaussian cores with the possibility of co-centered Lorentzian wings" (2.2 H I column densities)
   - validation: _not stated_
4. **Compare H2, DNM, HI and CO; group sightlines**: Group sightlines by N(DNM) (8 vs 5), compute group means, compare N(H) from CO vs HCO+, predict W_CO with X_CO=2e20  
  > "grouped according to whether N(DNM) >∼ 2 × 10 20 H cm −2 (8 sources) or N(DNM) < 0.5 × 10 20 H cm −2 (5 sources)" (3.1 General properties)
   - assumption: X_CO = 2e20 H2 cm-2 (K km/s)-1; W_CO=0 except J1723  
  > "A null CO signal, W CO = 0, was therefore taken in all directions except J1723" (3.4 CO emission, observed and expected)
   - fitting: _not stated_
   - validation: _not stated_

## Software


## Numeric results

| quantity | value | uncertainty | units | step | quote |
|---|---|---|---|---|---|
| mean 2N(H2), high-DNM group | 5.6 | std 3.6 | 1e20 cm-2 | 4 | high DNM 3.3(1.3) 5.6(3.6) 6.6(2.0) 0.46 |
| mean 2N(H2), low-DNM group | 0.8 | std 0.6 | 1e20 cm-2 | 4 | low DNM 0.14(0.21) 0.8(0.6) 5.6(1.5)) 0.13 |
| molecular fraction of H nuclei, high/low/all | 0.46 / 0.13 / 0.38 | not stated | dimensionless | 4 | all 2.1(1.9) 3.8(3.7) 6.2(1.8) 0.38 |
| N(H2)/W_CO toward J1723 | 2.3e20 | not stated | H2 cm-2 (K km/s)-1 | 4 | gives N(H 2 )/W CO = 2.3 × 10 20 H 2 cm −2 (Kkm s −1 ) −1 |
| mean E(B-V), high vs low DNM | 0.33 vs 0.18 | std 0.11, 0.10 | mag | 4 | mean(σ) 0.33(0.11) 12.7(6.3) 6.6(2.0) 3.3(1.3) 5.6(3.6) 5.4(1.4) 1.4(0.9) |

## Qualitative findings

- HCO+ absorption detected in nearly all directions; C2H in 8, HCN in 4  
  > "HCO + absorption was detected in all directions, C 2 H in 8 directions and HCN in 4 directions." (abstract)
- Molecular absorption in low-DNM group confined to v<~2 km/s; more positive velocities enriched in molecules and DNM  
  > "The gas at more positive velocities is enriched in molecules and DNM." (abstract)

## Claim tuples

- H: H2 traced by HCO+ absorption accounts for the DNM in outskirts of Chamaeleon | E: HCO+ absorption toward 13 quasars, N(H2) compared with Planck N(DNM) | R: Mean 2N(H2)=3.8e20 vs mean N(DNM)=2.1e20 cm-2 | F: DNM is mostly molecular; no reservoir of dark gas undetected | **supported**
- H: HI saturation explains some DNM | E: Compare 2N(H2) with N(DNM) per sightline | R: Shortfall of H2 in 3 of 4 highest-DNM sightlines | F: Saturation may occur in 3 sightlines but is small overall | **partially**

## Reasoning

- Why this data: HCO+ absorption is more widespread than CO emission and a reliable H2 tracer  
  > "HCO + absorption is the more reliable tracer of H 2 along the lines of sight observed here" (3 Molecules and Dark Neutral Medium)
- Why this method: _not stated_
- Alternative: Small X_CO (<0.7e20) from dust/gamma-ray rejected for these diffuse sightlines  
  > "For this reason we use X CO = X 0 CO for the weakly-emitting diffuse molecular gas detected in the outskirts of Chamaeleon" (3.5 The CO-H 2 conversion factor)
- How they decided it was enough: _not stated_
- Limitation (authors): Planck CO maps are masked near some sightlines; weak CO detections may be missed  
  > "the Planck CO maps have been hashed over small regions in the immediate vicinity of several of our sightlines" (2.4 CO emission)
- Caveat (inferred, ours): Result depends on assumed constant N(HCO+)/N(H2)=3e-9
- Caveat (inferred, ours): N(DNM) taken from a prior analysis with its own systematics
- Caveat (inferred, ours): Only 13 sightlines; grouping by N(DNM) is post hoc
- Caveat (inferred, ours): Optical depth saturation not discussed

## Reproducibility

- Data public (paper): ALMA project data cited in acknowledgements  
  > "This paper makes use of the following ALMA data: ADS/JAO.ALMA#2016.1.00714.S" (Acknowledgements)
- Products in archive: _not stated_
- Missing: Spectral integration ranges
- Missing: Optical depth derivation details
- Missing: Pseudo-Voigt HI fit results
- Missing: Imaging script details
- Data volume (inferred): tens of GB
- Score (inferred): 3/5, Public data and simple formulae with numeric tables, but processing and integration details are sparse.
- Rediscovery candidate: yes, Public data, simple recipe from pipeline cubes, and numeric table results.

## Links

- Method: Gerin & Liszt 2017 (HCO+ column density relation)
- Companion: Planck Collaboration et al. (2015) (source of DNM maps)
- Companion: Remy et al. (2018) (gamma-ray DNM analysis)
- Related: Planck
- Related: Fermi
- Related: NANTEN
- Related: GASS III

## Checks

```json
{
 "quotes": 44,
 "quotes_ok": 44,
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
  "facts": 70,
  "stated": 32,
  "rate": 0.457
 },
 "evidence_ok": true
}
```
