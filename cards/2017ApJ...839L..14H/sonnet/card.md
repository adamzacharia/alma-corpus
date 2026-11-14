# Detection of Submillimeter-wave [C I] Emission in Gaseous Debris Disks of 49 Ceti and β Pictoris

`2017ApJ...839L..14H` | The Astrophysical Journal Letters 2017 | first author: Higuchi, Aya E. | arXiv: 1703.06661 | DOI: 10.3847/2041-8213/aa67f4

Card schema 1.0 | model claude-sonnet-5-5 | depth light | type multi_facility_alma_minor

## Science

- Fields: debris_disks, astrochemistry
- Question: Is atomic carbon [C I] present in gaseous debris disks of 49 Ceti and beta Pic, and what does the C/CO ratio imply about the gas origin?  
  > "This result suggests that atomic carbon (C) coexists with CO in the debris disks, and is likely formed by the photodissociation of CO." (abstract)
- Target **49 Ceti**: coordinates 01:34:37.78 -15:40:34.9 (J2000)  
  > "| 49 Ceti | 01:34:37.78 | -15:40:34.9 | 61$\pm$3 | A1V | 23 | 300 | 90$\pm$5 | \(1\) |" (Table 1); z/distance 61±3 pc  
  > "| 49 Ceti | 01:34:37.78 | -15:40:34.9 | 61$\pm$3 | A1V | 23 | 300 | 90$\pm$5 | \(1\) |" (Table 1); distance from Hughes et al. (2008)  
  > "| 49 Ceti | 01:34:37.78 | -15:40:34.9 | 61$\pm$3 | A1V | 23 | 300 | 90$\pm$5 | \(1\) |" (Table 1)
- Target **beta Pictoris**: coordinates 05:47:17.09 -51:03:59.4 (J2000)  
  > "| $\beta$ Pictoris | 05:47:17.09 | -51:03:59.4 | 19.3$\pm$0.2 | A5V(A6V) | 40 | 130 | 88 | \(2\) |" (Table 1); z/distance 19.3±0.2 pc  
  > "| $\beta$ Pictoris | 05:47:17.09 | -51:03:59.4 | 19.3$\pm$0.2 | A5V(A6V) | 40 | 130 | 88 | \(2\) |" (Table 1); distance from Dent et al. (2014)  
  > "| $\beta$ Pictoris | 05:47:17.09 | -51:03:59.4 | 19.3$\pm$0.2 | A5V(A6V) | 40 | 130 | 88 | \(2\) |" (Table 1)

## Data provenance

- ALMA projects: 2011.0.00087.S, 2012.1.00195.S
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
- pi or archival as stated: _not stated_
- Line: [C I] 3P1–3P0 (492.161 GHz)
- Line: CO J=3–2 (345.796 GHz)
- Other facility **ASTE 10 m**: [C I] and CO(3-2) spectra (primary data)  
  > "with the 10 m telescope of the Atacama Submillimeter Telescope Experiment (ASTE)" (Observations)
- Other facility **ALMA (archival)**: CO(3-2) spectra for comparison  
  > "Figure 1(b) shows the ALMA spectrum of CO($J$=3–2) (dotted lines) toward 49 Ceti" (3.1 CO(J=3–2) and [C I] spectra)
- External data: CO disk extent used for the beam filling factor; disk parameters  
  > "assuming that the extent of the [C I] emission is identical to that of the CO disk observed by SMA and ALMA" (Optical Depth of the [C I] Emission and Column Density of C) [from Hughes et al. 2008; Dent et al. 2014]
- External data: Dust temperatures of 62 K and 60 K from SED fitting  
  > "the dust temperature derived from the model fitting of the spectral energy distribution is 62 K for 49 Ceti and 60 K for $\beta$ Pictoris" (Optical Depth of the [C I] Emission and Column Density of C) [from Roberge et al. 2013; Cataldi et al. 2014]
- Simulation/model as data: Toy chemical model with UMIST rate coefficients  
  > "we used the rate coefficients tabulated in the UMIST database for astrochemistry (McElroy et al. 2013)" (Origin of the high C/CO ratio)

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

- Column density equations  
  > "derived using the equations reported by Oka et al. (2001) and Tsukagoshi et al. (2015)" (Optical Depth of the [C I] Emission and Column Density of C) [from Oka et al. (2001); Tsukagoshi et al. (2015)]

### Not stated but needed to reproduce (our reading)

- ALMA calibration/imaging of archival CO data, including how the spectra were extracted
- Baseline order and reduction details in NEWSTAR
- Disk solid angles used for f_d
- Chemical toy model network and parameters
- Partition function Q(Tex) formula

## Analysis recipe

1. **Reduce ASTE spectra**: Position-switched spectra reduced with NEWSTAR  
  > "The observation data were reduced using the software package NEWSTAR developed by the Nobeyama Radio Observatory." (Observations)
   - software: NEWSTAR
   - fitting: _not stated_
   - validation: Compared CO spectra with ALMA and SMA/JCMT  
  > "The spectral features and the systemic velocities of the two spectra are consistent." (3.1 CO(J=3–2) and [C I] spectra)
2. **Derive optically thin column densities**: LTE optically thin N(C), N(CO) with beam filling factor, Tex 30–100 K  
  > "we assumed the range of ${T}_{\rm{ex}}$ to be from 30 to 100 K." (Optical Depth of the [C I] Emission and Column Density of C)
   - assumption: Optically thin, LTE  
  > "we thus adopted the optically thin condition in the following analysis" (Optical Depth of the [C I] Emission and Column Density of C)
   - fitting: _not stated_
   - validation: _not stated_

## Software

- **NEWSTAR** : ASTE data reduction  
  > "The observation data were reduced using the software package NEWSTAR developed by the Nobeyama Radio Observatory." (Observations)

## Numeric results

| quantity | value | uncertainty | units | step | quote |
|---|---|---|---|---|---|
| N(C) 49 Ceti | 2.2e17 | 0.2e17 | cm^-2 | 2 | (2.2$\pm$0.2)$\times$10$^{17}$ and (2.5$\pm$0.7)$\times$10$^{16}$ cm$^{-2}$ for 49 Ceti and $\beta$ Pictoris |
| N(C) beta Pic | 2.5e16 | 0.7e16 | cm^-2 | 2 | (2.2$\pm$0.2)$\times$10$^{17}$ and (2.5$\pm$0.7)$\times$10$^{16}$ cm$^{-2}$ for 49 Ceti and $\beta$ Pictoris |
| C/CO ratio 49 Ceti | 54 | 19 | dimensionless | 2 | 54$\pm$19 and 69$\pm$42 for 49 Ceti and $\beta$ Pictoris |
| C/CO ratio beta Pic | 69 | 42 | dimensionless | 2 | 54$\pm$19 and 69$\pm$42 for 49 Ceti and $\beta$ Pictoris |

## Qualitative findings

- [C I] line profiles resemble CO(3-2)  
  > "The line profiles of [C I] are found to resemble those of CO($J$=3–2)" (abstract)

## Claim tuples

- H: [C I] is present and co-located with CO in debris disks | E: ASTE [C I] and CO(3-2) spectra compared with ALMA CO | R: Similar line profiles; [C I] detected at 10.2σ (49 Ceti), 5.1σ (β Pic) | F: First [C I] detection; C coexists with CO | **supported**
- H: C/CO is anomalous | E: Optically thin column densities | R: C/CO 54 and 69 | F: An order of magnitude higher than clouds; low H2, secondary gas contribution | **partially**

## Reasoning

- Why this data: _not stated_
- Why this method: _not stated_
- How they decided it was enough: _not stated_
- Limitation (authors): Chemical model is preliminary; beta Pic detection marginal  
  > "Although the chemical model is preliminary" (Origin of the high C/CO ratio)
- Caveat (inferred, ours): Single-dish beam dilution corrected with assumed CO disk extent
- Caveat (inferred, ours): Low S/N for beta Pic
- Caveat (inferred, ours): Tex assumed, not measured

## Reproducibility

- Data public (paper): ALMA data used are archival projects; ASTE data not stated as public  
  > "This paper makes use of ALMA data ADS/JAO.ALMA$\#$2011.0.00087.S and ADS/JAO.ALMA$\#$2012.1.00195.S." (Acknowledgments)
- Products in archive: _not stated_
- Missing: ASTE raw data availability
- Missing: ALMA processing details
- Data volume (inferred): small for ASTE; ALMA archival cubes ~tens of GB
- Score (inferred): 2/5, Main data are ASTE spectra, not public; ALMA role minor
- Rediscovery candidate: no, Main results rely on ASTE data and unspecified disk solid angles.

## Links

- Method: Oka et al. 2001 (column density equations)

## Checks

```json
{
 "quotes": 33,
 "quotes_ok": 33,
 "quote_pass_rate": 1.0,
 "quotes_too_long": 0,
 "unsupported_facts": 0,
 "project_codes": 2,
 "codes_not_in_text": [],
 "codes_not_in_obscore": [],
 "obscore_codes_not_in_card": [],
 "codes_printed_but_missing": [],
 "numeric_results": 4,
 "numeric_problems": 0,
 "fill": {
  "facts": 62,
  "stated": 21,
  "rate": 0.339
 },
 "evidence_ok": true
}
```
