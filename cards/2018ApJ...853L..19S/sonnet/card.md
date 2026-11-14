# The Detection of Hot Cores and Complex Organic Molecules in the Large Magellanic Cloud

`2018ApJ...853L..19S` | The Astrophysical Journal Letters 2018 | first author: Sewiło, Marta | arXiv: 1801.10275 | DOI: 10.3847/2041-8213/aaa079

Card schema 1.0 | model claude-sonnet-5-5 | depth full | type observational_alma_primary

## Science

- Fields: astrochemistry, star_formation, nearby_galaxies
- Question: Are complex organic molecules and hot cores present in the low-metallicity LMC N 113 region, and how do their abundances compare with Galactic hot cores?  
  > "In this Letter, we report the first extragalactic detection of the COMs dimethyl ether (CH$_3$OCH$_3$) and methyl formate (CH$_3$OCHO) in the N 113 region of the LMC." (Introduction)
- Target **N 113 (sources A1 and B3)**: coordinates _not stated_; z/distance 50.0±1.1 kpc (LMC)  
  > "The Large Magellanic Cloud (LMC) is a nearby dwarf galaxy ($50.0\pm1.1$ kpc; (cite: pietrzynski2013))" (Introduction); distance from Pietrzynski et al. 2013  
  > "The Large Magellanic Cloud (LMC) is a nearby dwarf galaxy ($50.0\pm1.1$ kpc; (cite: pietrzynski2013))" (Introduction)

## Data provenance

- ALMA projects: 2015.1.01388.S
- bands: Band 6 (1.3 mm)  
  > "N 113 was observed with ALMA in Band 6 as part of project 2015.1.01388.S." (3 ALMA Observations of N 113)
- frequencies and spectral setup: 12CO, 13CO, C18O (2-1) narrow windows plus 2 GHz windows centered on 231.7 and 216.9 GHz  
  > "additional 2 GHz windows centered on 231.7 and 216.9 GHz." (3 ALMA Observations of N 113)
- continuum bandwidth: _not stated_
- arrays: 12m array and 7m ACA  
  > "It was also observed 19 times with the 7m Atacama Compact Array (ACA) array" (3 ALMA Observations of N 113)
- configurations: _not stated_
- baselines: 15 to 704 m (12m array)  
  > "on baselines from 15 to 704 m." (3 ALMA Observations of N 113)
- angular resolution: continuum beam 0.87x0.54 arcsec (~0.21x0.13 pc)  
  > "Sensitivity of 0.1 mJy per 0\rlap.^{''}87$\times$0$\rlap.^{''}$54 ($\sim$0.21$\times$0.13 pc) beam was achieved in the continuum." (3 ALMA Observations of N 113)
- max recoverable scale: _not stated_
- sensitivity: continuum 0.1 mJy/beam; 3.8 mJy/beam (216.9 GHz cube, 1.5 km/s); 2.9 mJy/beam (231.7 GHz, 2.6 km/s)  
  > "Sensitivity of 3.8 mJy per 0\rlap.^{''}98$\times$0$\rlap.^{''}$62" (3 ALMA Observations of N 113)
- time on source: 13.1 min per mosaic pointing (12m); 247 min per pointing (ACA)  
  > "for a total of 13.1 min per mosaic pointing over most of the map" (3 ALMA Observations of N 113)
- observing dates: 12m: 10 March and 16 June 2016; ACA: 2 Nov-17 Dec 2015  
  > "on March 10 and June 16, 2016" (3 ALMA Observations of N 113)
- pi or archival as stated: _not stated_
- Line: CH3OH six transitions, Eu~56-508 K (216.9-232.8 GHz)
- Line: CH3OCH3 13(0,13)-12(1,12) EE (231.98782 GHz)
- Line: CH3OCHO 18-17 and 20-19 (216.83-216.97 GHz)
- Other facility **Spitzer/Herschel**: Infrared data identifying YSOs and context  
  > "Based on the *Spitzer* Space Telescope and the *Herschel* Space Observatory data, confirmed and candidate Stage 0–II YSOs down to $\sim$3 M$_{\odot}$ were identified" (2 The N 113 Star-Forming Region)
- Other facility **VLT/SINFONI**: K-band source identification  
  > "*K*-band observations obtained with VLT/SINFONI with 0$\rlap.{''}$1 resolution" (2 The N 113 Star-Forming Region)
- External data: LMC dust emissivity N(H2)/tau_dust = 1.8e26 cm^-2  
  > "$N({\rm H}_2)/\tau_{\rm dust}$ = $1.8\times10^{26}$ cm$^{-2}$" (4.1 1.3 mm Continuum Emission) [from Galliano et al. 2011 (cite: galliano2011)]

## Processing

### Calibration

- pipeline or manual: ALMA pipeline in CASA, versions 4.7 through 5.0  
  > "The data were calibrated with versions 4.7 through 5.0 of the ALMA pipeline in CASA" (3 ALMA Observations of N 113)
- casa version: _not stated_
- pipeline version: _not stated_
- archive products used as is: _not stated_
- flux calibrator: Uranus, J0538-4405, J0519-4546, Callisto (varies by date)  
  > "Amplitude was calibrated using Uranus, J0538–4405, J0519–4546, and Callisto" (3 ALMA Observations of N 113)
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
- continuum subtraction: in the uv domain from each line spectral window  
  > "Continuum was subtracted in the uv domain from each line spectral window" (3 ALMA Observations of N 113)
- line free channels: _not stated_
- primary beam correction: _not stated_
- array combination: 7m and 12m data simultaneously imaged and deconvolved interactively  
  > "the 7m and 12m data were simultaneously imaged and deconvolved interactively" (3 ALMA Observations of N 113)
- smoothing: _not stated_
- final beam: _not stated_
- final rms: _not stated_

### Not stated but needed to reproduce (our reading)

- tclean parameters (robust, cell, image size, masks, threshold)
- line-free channels for continuum subtraction
- source/spectrum extraction apertures
- line width and velocity priors in MADCUBA fits
- exact continuum image frequencies/bandwidth
- flux calibration uncertainty
- source coordinates

## Analysis recipe

1. **Measure continuum brightness and H2 column density**: Gaussian fits and brightest pixel at 224.6 GHz; dust optical depth with Td = CH3OH temperature; N(H2) from LMC emissivity  
  > "We measured the continuum surface brightness for A1 and B3 in the continuum image centered at 224.6 GHz by fitting the sources with Gaussians" (4.1 1.3 mm Continuum Emission)
   - assumption: N(H2)/tau_dust = 1.8e26 cm^-2 (Galliano 2011); spherical symmetry  
  > "under the assumption of spherical symmetry" (4.1 1.3 mm Continuum Emission)
   - fitting: _not stated_
   - validation: _not stated_
2. **Identify molecular lines**: LTE synthetic spectra with JPL and CDMS databases  
  > "We have carried out the line identification with the madcubaij software" (4.2 Spectral Line Analysis)
   - software: MADCUBA
   - assumption: LTE  
  > "under local thermodynamic equilibrium (LTE) conditions" (4.2 Spectral Line Analysis)
   - fitting: _not stated_
   - validation: Detected lines must have relative intensities consistent with LTE analysis  
  > "with the relative intensities of the different transitions consistent with the LTE analysis." (4.2 Spectral Line Analysis)
3. **Derive Trot and N from CH3OH**: Rotational diagram of six CH3OH lines as initial parameters, then MADCUBA least-squares fit  
  > "We used the results of the rotational diagram analysis (e.g., (cite: goldsmith1999)) of CH$_3$OH as the initial parameters" (4.2 Spectral Line Analysis)
   - software: MADCUBA
   - assumption: LTE, optically thin  
  > "This analysis assumes the gas is in LTE and the lines are optically thin." (4.2 Spectral Line Analysis)
   - fitting: Least-squares fits in MADCUBA; formal uncertainties  
  > "formal fit uncertainties from the least-square fits performed by madcubaij" (4.2 Spectral Line Analysis)
   - validation: _not stated_
4. **Column densities of other species and abundances**: Use methanol Trot for other species; test Trot of 100-250 K; abundances relative to H2, scaled by 2.5 for metallicity  
  > "we calculated column densities for $T_{\rm rot}$ of 100, 150, 200, and 250 K." (4.2 Spectral Line Analysis)
   - software: MADCUBA
   - parameter: Z_LMC = 0.4 Zsun, scaling factor 2.5  
  > "assuming $Z_{\rm LMC}=0.4\,Z_{\odot}$" (5 Discussion)
   - assumption: All species co-spatial with methanol  
  > "Assuming that all molecular species observed toward A1/B3 are located in the same region as methanol" (4.2 Spectral Line Analysis)
   - fitting: _not stated_
   - validation: Column density at 250 K at most ~2x; at 100 K ~20% lower  
  > "At 100 K, column densities are in general up to $\sim$20% lower." (4.2 Spectral Line Analysis)

## Software

- **CASA** 4.7-5.0 (pipeline): Calibration with ALMA pipeline  
  > "versions 4.7 through 5.0 of the ALMA pipeline in CASA" (3 ALMA Observations of N 113)
- **MADCUBA** : Line identification and LTE spectral modeling  
  > "We have carried out the line identification with the madcubaij software" (4.2 Spectral Line Analysis)

## Numeric results

| quantity | value | uncertainty | units | step | quote |
|---|---|---|---|---|---|
| CH3OH Trot, A1 | 134 | 6 | K | 3 | ($134\pm6~{\rm K}, 1.6\pm0.1\times10^{16}~{\rm cm}^{-2}$) |
| CH3OH Trot, B3 | 131 | 15 | K | 3 | ($131\pm15~{\rm K}, 6.4\pm0.8\times10^{15}~{\rm cm}^{-2}$) |
| CH3OH column density A1 | 1.6e16 | 0.1e16 | cm^-2 | 3 | $1.6\pm0.1\times10^{16}~{\rm cm}^{-2}$ |
| N(H2) A1 | 8.0e23 | 1.2e23 | cm^-2 | 1 | $(8.0\pm1.2)\times10^{23}$ cm$^{-2}$ |
| N(H2) B3 | 7.0e23 | 0.9e23 | cm^-2 | 1 | $(7.0\pm0.9)\times10^{23}$ cm$^{-2}$ |
| CH3OH fractional abundance A1 | 2.0e-8 | 0.3e-8 | dimensionless | 4 | $(2.0\pm0.3)\times10^{-8}$ and $(9.1\pm1.7)\times10^{-9}$ for A1 and B3 |
| CH3OH fractional abundance B3 | 9.1e-9 | 1.7e-9 | dimensionless | 4 | $(2.0\pm0.3)\times10^{-8}$ and $(9.1\pm1.7)\times10^{-9}$ for A1 and B3 |
| CH3OCH3/CH3OH, A1 | 0.11 | 0.03 | dimensionless | 4 | $(0.11\pm0.03, 0.07\pm0.01)$ |

## Qualitative findings

- A1 and B3 are classified as hot cores; B3 appears younger than A1 based on DCN.  
  > "all these properties support the classification of A1 and B3 as hot cores." (5 Discussion)

## Claim tuples

- H: COMs form in the low-metallicity LMC | E: ALMA Band 6 spectra of N 113 with LTE modeling | R: CH3OCH3 and CH3OCHO detected with CH3OH toward A1 and B3 | F: First extragalactic ALMA detection of these COMs | **supported**
- H: The COM sources are hot cores | E: Rotational temperature, density and maser association | R: Trot ~130 K, N ~1e16 cm^-2, H2O/OH masers | F: A1 and B3 are hot cores | **supported**
- H: COM abundances in LMC are comparable to Galactic | E: Abundances scaled by 2.5 for metallicity | R: Comparable to lower end of Galactic hot cores | F: COM chemistry similar to Galaxy | **supported**

## Reasoning

- Why this data: _not stated_
- Why this method: _not stated_
- How they decided it was enough: _not stated_
- Limitation (authors): Dust emissivity uncertain; coagulation on small scales could lower N(H2) and raise abundances  
  > "If dust has coagulated on the small scales probed by ALMA, the dust emissivity could be higher" (4.1 1.3 mm Continuum Emission)
- Caveat (inferred, ours): Single-temperature LTE with co-spatial assumption for all species
- Caveat (inferred, ours): Dust temperature set equal to methanol temperature
- Caveat (inferred, ours): Emissivity from 10 pc scales applied to 0.2 pc cores
- Caveat (inferred, ours): Few lines for CH3OCH3 and CH3OCHO

## Reproducibility

- Data public (paper): ALMA project cited; public status not explicitly stated  
  > "This paper makes use of the following ALMA data: ADS/JAO.ALMA#2015.1.01388.S." (Acknowledgments)
- Products in archive: _not stated_
- Missing: tclean imaging parameters
- Missing: extraction regions
- Missing: MADCUBA fit settings and line widths
- Missing: source coordinates
- Data volume (inferred): hundreds of GB (12m plus ACA mosaic, raw)
- Score (inferred): 3/5, Data are identifiable and analysis simple, but imaging and extraction details are missing.
- Rediscovery candidate: no, Imaging and extraction recipe incomplete; relies on MADCUBA specifics.

## Links

- Method: Martin et al. 2011; Rivilla et al. 2016 (MADCUBA line analysis)
- Method: Goldsmith & Langer 1999 (rotational diagram method)
- Companion: Nishimura et al. 2016a (single-dish LMC molecular survey with non-detections)
- Related: 2015.1.01388.S

## Checks

```json
{
 "quotes": 51,
 "quotes_ok": 51,
 "quote_pass_rate": 1.0,
 "quotes_too_long": 0,
 "unsupported_facts": 0,
 "project_codes": 1,
 "codes_not_in_text": [],
 "codes_not_in_obscore": [],
 "obscore_codes_not_in_card": [],
 "codes_printed_but_missing": [],
 "numeric_results": 8,
 "numeric_problems": 0,
 "fill": {
  "facts": 67,
  "stated": 35,
  "rate": 0.522
 },
 "evidence_ok": true
}
```
