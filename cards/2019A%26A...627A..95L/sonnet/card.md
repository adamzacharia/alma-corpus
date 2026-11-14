# Standing in the shadow of dark gas: ALMA observations of absorption from dark CO in the molecular dark neutral medium of Chamaeleon

`2019A&A...627A..95L` | Astronomy and Astrophysics 2019 | first author: Liszt, H. | arXiv: 1905.05369 | DOI: 10.1051/0004-6361/201935436

Card schema 1.0 | model claude-sonnet-5-5 | depth full | type observational_alma_primary

## Science

- Fields: milky_way_ism, astrochemistry
- Question: Why did CO emission fail to represent the molecular gas (HCO+-traced H2) in the dark neutral medium in the outskirts of Chamaeleon: inadequate CO excitation or very small CO column densities?  
  > "Here we ask why CO emission did not represent the molecular gas component adequately: perhaps as the result of inadequate rotational excitation of the CO, or perhaps as the result of there being only very small CO column densities" (1. Introduction)
- Target **J0942-7731, J1058-8003, J1136-6827, J1145-6954, J1224-8313, B1251-7138 (background continuum sources toward Chamaeleon outskirts)**: coordinates e.g. J0942-7731: 09.424275 -77.311158 (hh.mmssss, dd.mmssss), l=293.321 b=-18.329  
  > "J0942-7731 09.424275 -77.311158 293.321 -18.329 0.33 9.1" (Table 1); z/distance _not stated_; distance from _not stated_

## Data provenance

- ALMA projects: 2017.1.00227.S
- bands: _not stated_
- frequencies and spectral setup: 12CO J=1-0 at 115.271 GHz; 1919 channels of 30.503 kHz (0.079 km/s), half the spectral resolution  
  > "Each spectrum consisted of 1919 semi-independent channels spaced by 30.503 kHz corresponding to 0.079 km s−1 at the 115.271 GHz rest frequency of 12CO." (2.2 New ALMA absorption measurements)
- continuum bandwidth: _not stated_
- arrays: _not stated_
- configurations: _not stated_
- baselines: _not stated_
- angular resolution: _not stated_
- max recoverable scale: _not stated_
- sensitivity: _not stated_
- time on source: _not stated_
- observing dates: _not stated_
- pi or archival as stated: _not stated_
- Line: 12CO J=1-0 (115.271 GHz)
- Other facility **NANTEN**: CO J=1-0 emission spectra used by Planck for DNM  
  > "Fig. 1 shows the NANTEN CO J=1-0 emission spectra used by Planck Collaboration et al. (2015) to derive the column density of DNM" (2.3 Other observational data)
- Other facility **GASS III**: HI 21 cm emission spectra  
  > "optically thin H I column densities derived from Galactic All-Sky Survey (GASS) III λ21 cm H I emission spectra (Kalberla & Haud, 2015)" (2.3 Other observational data)
- External data: HCO+ integrated optical depths and column densities from Paper I  
  > "In Table 1 we quote the integrated HCO+ optical depths from Paper I" (2.3 Other observational data) [from Liszt et al. (2018) (Paper I)]
- External data: N(CO)-Υ_CO relation from CO emission and absorption  
  > "Fig. 3 shows the N(CO)-Υ CO relation derived from the prior observations of J=1-0 and J=2-1 CO emission and absorption by Liszt & Lucas (1998)" (2.3 Other observational data) [from Liszt & Lucas (1998)]
- External data: UV absorption N(H2), N(CO) toward stars  
  > "Stellar quantities from Sheffer et al. (2008)" (Table 4) [from Sheffer et al. (2008); Burgh et al. (2007); Sonnentrucker et al. (2007)]
- External data: Reddening E(B-V) from dust maps  
  > "dust-emission maps scaled to optical reddening E(B-V) by Schlegel et al. (1998) are used in Tables 1 and 4" (2.4 Reddening and dust optical depth) [from Schlegel et al. (1998)]

## Processing

### Calibration

- pipeline or manual: ALMA pipeline-processed data products used  
  > "The spectra discussed here were extracted from the pipeline-processed, continuum-subtracted data cubes" (2.2 New ALMA absorption measurements)
- casa version: _not stated_
- pipeline version: _not stated_
- archive products used as is: Delivered pipeline products used; no further baselining  
  > "No (further) baselining of any of the spectra was performed." (2.2 New ALMA absorption measurements)
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
- continuum subtraction: Pipeline continuum-subtracted cubes; spectra divided by continuum flux at peak pixel  
  > "extracted from the pipeline-processed, continuum-subtracted data cubes at the pixel of peak continuum flux in the continuum map made from each spectral window, and divided by the continuum flux" (2.2 New ALMA absorption measurements)
- line free channels: _not stated_
- primary beam correction: _not stated_
- array combination: _not stated_
- smoothing: _not stated_
- final beam: _not stated_
- final rms: _not stated_

### Inherited from earlier work

- HCO+/H2 abundance 3e-9 used to derive N(H2)  
  > "As in Paper I we use the relative abundance N(HCO+)/N(H2) = 3 × 10−9 to derive N(H2)" (2.6 The relative abundance of HCO+) [from Paper I (Liszt et al. 2018)]
- N(HCO+) from Υ_HCO+ assuming CMB excitation  
  > "Column densities of HCO+ are taken from Paper I as derived assuming rotational excitation in equilibrium with the cosmic microwave background" (2.3 Other observational data) [from Paper I]
- DNM column densities from dust/gamma-ray analysis  
  > "is the quantity fitted in the global DNM analysis (Planck Collaboration et al., 2015)" (Fig. 8 caption) [from Planck Collaboration et al. (2015)]

### Not stated but needed to reproduce (our reading)

- Pipeline/CASA version
- Array configuration, baselines, observing dates and time on source
- Details of the continuum maps and any imaging parameters
- Velocity range used for integrating optical depths
- Procedure for Gaussian decomposition fits
- Software used for spectra extraction and fitting

## Analysis recipe

1. **Extract optical depth spectra**: Extract spectra at peak continuum pixel from pipeline continuum-subtracted cubes and divide by continuum flux  
  > "extracted from the pipeline-processed, continuum-subtracted data cubes at the pixel of peak continuum flux in the continuum map made from each spectral window, and divided by the continuum flux" (2.2 New ALMA absorption measurements)
   - fitting: _not stated_
   - validation: _not stated_
2. **Convert integrated CO optical depth to N(CO)**: Power-law N(CO)=1.861e15 Υ_CO^1.131 from Liszt & Lucas (1998) regression  
  > "N(CO) = 1.861 × 10 15 cm −2 Υ CO 1.131" (4.1)
   - assumption: Roughly equivalent to Tex of 4.4-4.5 K for the stronger lines  
  > "this is roughly equivalent to assuming an excitation temperature of 4.4-4.5 K for the stronger lines observed here" (2.5)
   - fitting: _not stated_
   - validation: Compared with UV absorption N(CO), N(H2) in Fig. 4  
  > "As a check on this procedure, Fig. 4 compares the present and prior mm-wave results for N(CO) and N(H2)" (4.1)
3. **Derive N(H2) and CO/H2, CO-H2 conversion factor**: N(H2)=N(HCO+)/3e-9; N(CO)/N(H2); X_CO from W_CO = N(CO)/1e15  
  > "W CO /(1 K-km s −1 ) = N(CO)/10 15 cm −2 over a wide range of hydrogen number density in diffuse molecular gas" (4.2)
   - assumption: HCO+/H2 uncertain by ±0.2 dex  
  > "The overall uncertainty in the abundance of HCO+ relative to H2 was estimated by Gerin et al. (2019) to be ±0.2 dex" (2.6)
   - fitting: _not stated_
   - validation: _not stated_
4. **Gaussian decomposition of CO and HCO+ profiles**: Gaussian fits; FWHM corrected by quadrature differencing of velocity resolution  
  > "have been corrected by quadrature differencing of the FWHM and velocity resolution" (4.3)
   - fitting: _not stated_
   - validation: _not stated_

## Software


## Numeric results

| quantity | value | uncertainty | units | step | quote |
|---|---|---|---|---|---|
| CO column density range | 4e13 to 1.2e15 | not stated | cm-2 | 2 | the observed CO column densities were found to lie in the range 4 × 10 13 cm −2 ∼< N(CO) <∼ 1.2 × 10 15 cm −2 |
| Mean N(CO)/N(H2) (six components) | 2.27 | 2.15 (std dev) | 1e-6 | 3 | 3.4(1.8) 0.80(0.45) 2.68(1.35) 0.59(0.47) 2.27(2.15) |
| Mean FWHM of HCO+ | 0.87 | 0.24 | km s-1 | 4 | 0.87 ± 0.24 km s −1 for HCO+ and 0.72 ± 0.22 km s −1 for CO |
| Mean FWHM of CO | 0.72 | 0.22 | km s-1 | 4 | 0.87 ± 0.24 km s −1 for HCO+ and 0.72 ± 0.22 km s −1 for CO |
| CO-H2 conversion factor toward J1723 overall | 2.4 | 0.3 | 1e20 H2 cm-2 (K km/s)-1 | 3 | N(H2)/W CO = 2.4 ± 0.3 × 10 20 H2 cm −2 (K-km s −1 ) −1 overall |
| HCO+ minus CO velocity difference | 0.10 | 0.40 (dispersion) | km s-1 | 4 | The mean difference and its dispersion are 0.10 km s −1 ± 0.40 km s −1 |

## Qualitative findings

- CO absorption detected toward all five high-DNM sightlines but not B1251  
  > "CO absorption was detected along all five of sightlines in the high-DNM group and not toward B1251." (3. Observational results)

## Claim tuples

- H: CO emission missed molecular DNM gas because of very small CO column densities rather than weak excitation | E: 12CO J=1-0 absorption toward six sightlines, converted to N(CO) with empirical relation | R: N(CO) 4e13-1.2e15 cm-2, below CO emission detectability | F: Molecular DNM arises from small CO columns at the onset of CO formation near the HI/H2 transition | **supported**
- H: CO and HCO+ line widths are similar | E: Gaussian decompositions of CO and HCO+ profiles | R: CO FWHM about 20% smaller | F: Linewidth difference likely from chemistry-dynamics interplay | **supported**

## Reasoning

- Why this data: _not stated_
- Why this method: _not stated_
- How they decided it was enough: _not stated_
- Limitation (authors): CO data in Chamaeleon are too limited for firm kinematic conclusions  
  > "The CO data in Chamaeleon are too limited to draw firm conclusions" (4.3)
- Caveat (inferred, ours): N(CO) depends on an empirical relation from other sightlines, with an implicit Tex assumption
- Caveat (inferred, ours): N(H2) relies on a fixed HCO+/H2 abundance with ±0.2 dex uncertainty
- Caveat (inferred, ours): Only six sightlines; one non-detection

## Reproducibility

- Data public (paper): ALMA project listed in acknowledgements; public status not explicitly stated  
  > "This paper makes use of the following new ALMA data: ADS/JAO.ALMA#2017.1.00227.S" (Acknowledgements)
- Products in archive: _not stated_
- Missing: Integration velocity ranges
- Missing: Gaussian fitting details
- Missing: Pipeline version
- Data volume (inferred): <5 GB (six short single-line absorption observations)
- Score (inferred): 6/5, Simple recipe with published conversion formulas and tables, but fit details and velocity ranges are not given.
- Rediscovery candidate: yes, Data from a single project, simple spectrum extraction and a closed-form conversion with numeric results in tables.

## Links

- Method: Liszt & Lucas (1998) (N(CO)-Υ_CO relation)
- Companion: Liszt et al. (2018) (Paper I) (HCO+ absorption observations of the same sightlines)
- Related: Planck DNM analysis
- Related: NANTEN CO survey
- Related: GASS III

## Checks

```json
{
 "quotes": 36,
 "quotes_ok": 36,
 "quote_pass_rate": 1.0,
 "quotes_too_long": 0,
 "unsupported_facts": 0,
 "project_codes": 1,
 "codes_not_in_text": [],
 "codes_not_in_obscore": [],
 "obscore_codes_not_in_card": [],
 "codes_printed_but_missing": [],
 "numeric_results": 6,
 "numeric_problems": 0,
 "fill": {
  "facts": 68,
  "stated": 25,
  "rate": 0.368
 },
 "evidence_ok": true
}
```
