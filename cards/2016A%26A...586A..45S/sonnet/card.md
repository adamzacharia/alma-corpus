# Star formation efficiency along the radio jet in Centaurus A

`2016A&A...586A..45S` | Astronomy and Astrophysics 2016 | first author: Salomé, Q. | arXiv: 1511.04310 | DOI: 10.1051/0004-6361/201526409

Card schema 1.0 | model claude-sonnet-5-5 | depth light | type multi_facility_alma_minor

## Science

- Fields: nearby_galaxies, agn_and_quasars, star_formation
- Question: Does the radio jet of Centaurus A trigger or quench star formation in the molecular gas of the outer northern filament?  
  > "Our goal was to compare the local star formation rate to the amount of molecular gas detected in the same region" (Conclusion)
- Target **Centaurus A (NGC 5128) outer northern filament, shell S1**: coordinates ALMA field centre RA 13h26m16.1s, Dec -42:46:55.7 (J2000)  
  > "RA (J2000) & $13^h 25^m 27^s.6$ & $13^h 26^m 18^s.9$" (Table 1); "The centre of this ALMA field is the same as for our ATCA observations: $\alpha=13^h 26^m 16^s.1$, $\delta=-$42:46:55.7" (4 Clumpy CO emission highlighted by ALMA); z/distance z=0.001826; filament ~13.5 kpc from the galaxy  
  > "RA (J2000) & $13^h 25^m 27^s.6$ & $13^h 26^m 18^s.9$" (Table 1); "The centre of this ALMA field is the same as for our ATCA observations: $\alpha=13^h 26^m 16^s.1$, $\delta=-$42:46:55.7" (4 Clumpy CO emission highlighted by ALMA); distance from _not stated_

## Data provenance

- ALMA projects: 2011.0.00454.S
- bands: Band 6, CO(2-1)  
  > "These early science (cycle 0) observations were made in band 6 with 16 antennas" (Clumpy CO emission highlighted by ALMA)
- frequencies and spectral setup: _not stated_
- continuum bandwidth: _not stated_
- arrays: _not stated_
- configurations: _not stated_
- baselines: _not stated_
- angular resolution: 2.3'' x 1.3'', PA -36.8 deg  
  > "reached a spatial resolution of $2.3''\times 1.3''$, PA -36.8 deg" (Clumpy CO emission highlighted by ALMA)
- max recoverable scale: _not stated_
- sensitivity: rms ~5 mJy in ~4 MHz channels (~5 km/s)  
  > "The rms reached is $\sim 5\: mJy$ in $\sim 4\: MHz$-channels ($\sim 5\: km.s^{-1}$)." (Clumpy CO emission highlighted by ALMA)
- time on source: ~7.25 min on-source for six regions  
  > "Six regions of the northern filament were pointed at during $\sim 7.25\: min$ on-source." (Clumpy CO emission highlighted by ALMA)
- observing dates: _not stated_
- pi or archival as stated: archival Cycle 0 data  
  > "We retrieved ALMA data from the science archive" (Clumpy CO emission highlighted by ALMA)
- Line: CO 2-1 (not stated)
- Other facility **SEST**: CO(1-0) and CO(2-1) maps of shell S1 from Charmandaris et al. 2000  
  > "made CO observations in May 1999 with the 15m SEST" (Single-dish CO observations from the SEST)
- Other facility **ATCA**: HCN(1-0) and HCO+(1-0) search and 3mm continuum, June 2014  
  > "have been searched for with the ATCA in June 2014 in the outer filament" (Dense molecular gas fraction from HCN observations)
- Other facility **GALEX**: FUV map for SFR  
  > "We only used the FUV here, which we took from the MAST archive." (SFR from TIR and FUV data)
- Other facility **Herschel PACS/SPIRE**: 70-500 micron fluxes for dust SED and TIR/FIR  
  > "The observation were made with the PACS instrument (cite: PACS) at wavelengths 70 and $160\: \mu m$" (SFR from TIR and FUV data)
- Other facility **VLT/MUSE**: optical emission lines for oxygen abundance  
  > "Optical observations have been carried on both the inner and outer filaments with MUSE on the VLT" (Filament oxygen abundances as deduced from MUSE data)
- External data: SEST CO observations and line fluxes of shell S1  
  > "made CO observations in May 1999 with the 15m SEST" (Single-dish CO observations from the SEST) [from (cite: Charmandaris_2000)]
- External data: MUSE data of the inner and outer filaments  
  > "((cite: Hamer_2015) for the inner filament, (cite: Santoro_2015b) for the outer filament)" (Filament oxygen abundances as deduced from MUSE data) [from (cite: Hamer_2015); (cite: Santoro_2015b)]

## Processing

### Calibration

- pipeline or manual: Re-calibrated in CASA with the supplied script  
  > "We used the Common Astronomy Software Applications (CASA) and the supplied script to re-calibrate the data" (Clumpy CO emission highlighted by ALMA)
- casa version: _not stated_
- pipeline version: _not stated_
- archive products used as is: _not stated_
- flux calibrator: _not stated_
- flux scale uncertainty: _not stated_
- self calibration: _not stated_

### Imaging

- task: Datacubes produced in GILDAS from uvfits uv-tables  
  > "The data were then transferred into GILDAS to produce datacubes and perform the imaging analysis." (Clumpy CO emission highlighted by ALMA)
- deconvolver: _not stated_
- weighting robust: _not stated_
- uv taper: _not stated_
- cell size: _not stated_
- image size: _not stated_
- masking: _not stated_
- multiscale scales: _not stated_
- continuum subtraction: _not stated_
- line free channels: _not stated_
- primary beam correction: fluxes scaled by primary beam factor x3.73  
  > "all fluxes were scaled with the appropriate primary beam factor ($\times 3.73$)" (Clumpy CO emission highlighted by ALMA)
- array combination: _not stated_
- smoothing: _not stated_
- final beam: _not stated_
- final rms: _not stated_

### Inherited from earlier work

- Herschel flux extraction method  
  > "The fluxes of the filament were extracted following the method of (cite: Remy_2013)." (SFR from TIR and FUV data) [from (cite: Remy_2013)]
- MUSE line fitting procedure  
  > "this procedure is described in detail in (cite: Hamer_2014)" (Filament oxygen abundances as deduced from MUSE data) [from (cite: Hamer_2014)]
- alpha_CO metallicity correction  
  > "Following (cite: Leroy_2013), the correction to $\alpha_{CO}$ can be expressed as" (Molecular gas mass) [from (cite: Leroy_2013)]

### Not stated but needed to reproduce (our reading)

- Line-free channels and continuum subtraction in GILDAS
- Imaging weighting, cell and image size, and clean parameters
- CASA version and the data reduction script details
- How the clump positions, fluxes and widths were measured (fit method)
- Details of the uv-table to cube step

## Analysis recipe

1. **Image ALMA CO(2-1)**: Recalibrate in CASA, export uvfits, make cubes in GILDAS, scale for primary beam  
  > "The data were then transferred into GILDAS to produce datacubes and perform the imaging analysis." (Clumpy CO emission highlighted by ALMA)
   - software: CASA, GILDAS
   - parameter: primary beam factor x3.73  
  > "all fluxes were scaled with the appropriate primary beam factor ($\times 3.73$)" (Clumpy CO emission highlighted by ALMA)
   - fitting: _not stated_
   - validation: _not stated_
2. **Convert CO flux to molecular gas mass of clumps**: Standard alpha_CO of 4.6 Msun/(K km/s pc^2) and a metallicity-corrected factor  
  > "A standard Milky Way conversion factor of $4.6\: M_\odot.(K.km.s^{-1}. pc^2)^{-1}$ (cite: Solomon_1997) was used" (Molecular gas mass)
   - assumption: Sigma_100=1 for the CO-dark correction; O/H 8.3-8.6 from MUSE  
  > "In the following, we assume $\Sigma_{100}=1$" (Molecular gas mass)
   - fitting: _not stated_
   - validation: _not stated_
3. **Virial parameter and depletion time**: alpha_vir=5 sigma^2 R/(GM); t_dep = M_H2/SFR with SFR from FUV  
  > "The clumps found in the filaments have $\alpha_{vir}\sim 10-16$ ($8\: km.s^{-1}$, 20 pc, $4\times 10^4\: M_\odot$)" (Clumpy CO emission highlighted by ALMA)
   - assumption: clump radius ~20 pc  
  > "Using spherical clouds of $\sim 20\: pc$ as a typical radius" (Clumpy CO emission highlighted by ALMA)
   - fitting: _not stated_
   - validation: _not stated_

## Software

- **CASA** : recalibration of ALMA data  
  > "We used the Common Astronomy Software Applications (CASA) and the supplied script to re-calibrate the data" (Clumpy CO emission highlighted by ALMA)
- **GILDAS** : ALMA datacubes and imaging  
  > "The data were then transferred into GILDAS to produce datacubes" (Clumpy CO emission highlighted by ALMA)
- **miriad** : ATCA calibration  
  > "Data calibration was made with miriad using the standard techniques for ATCA observations." (Dense molecular gas fraction from HCN observations)

## Numeric results

| quantity | value | uncertainty | units | step | quote |
|---|---|---|---|---|---|
| Total integrated CO(2-1) flux of three ALMA clumps | 3.0 | not stated | Jy km/s | 1 | The total integrated flux of the clumps is $S_{CO}\Delta v\sim 3.0\: Jy.km.s^{-1}$. |
| Molecular gas mass of clumps (standard alpha_CO) | 8.7e4 | not stated | Msun | 2 | this leads to a molecular gas mass of $M_{H_2}\sim 8.7\times 10^4\: M_\odot$ |
| Virial parameter of clumps | 10-16 | not stated | dimensionless | 3 | The clumps found in the filaments have $\alpha_{vir}\sim 10-16$ |
| Molecular depletion time of ALMA clumps | 5.7 | not stated | Gyr | 3 | leading to a molecular depletion time of $\sim 5.7\: Gyr$ |
| Average depletion time, SEST positions (standard alpha_CO) | 7.0 | not stated | Gyr | 0 | we find an average depletion time of 7.0 Gyr for all SEST positions |

## Qualitative findings

- ATCA did not detect HCN or HCO+ or 3mm continuum at the S1 position  
  > "HCN and $HCO^+$ were not detected with ATCA at the intersection of the outer filament with the H@ shell." (Dense molecular gas fraction from HCN observations)

## Claim tuples

- H: Does jet-cloud interaction quench star formation in filament molecular gas? | E: ALMA CO(2-1) clumps, SEST CO, GALEX/Herschel SFR, alpha_CO corrections | R: alpha_vir ~10-16, depletion times 7-16 Gyr | F: Star formation is inefficient along the jet, perhaps from turbulence injected by the jet or wind | **partially**

## Reasoning

- Why this data: _not stated_
- Why this method: _not stated_
- How they decided it was enough: _not stated_
- Limitation (authors): Clumps are unresolved and the metallicity at the ALMA position is unknown  
  > "there is no measurement of the true metallicity at the scale of the ALMA observations." (Clumpy CO emission highlighted by ALMA)
- Caveat (inferred, ours): Only one ALMA field and three clumps; detection outside primary beam gives large flux scaling
- Caveat (inferred, ours): Virial analysis depends strongly on alpha_CO choice
- Caveat (inferred, ours): Galactic cirrus contaminates the IR SFR

## Reproducibility

- Data public (paper): ALMA data retrieved from the archive  
  > "We retrieved ALMA data from the science archive" (Clumpy CO emission highlighted by ALMA)
- Products in archive: _not stated_
- Missing: GILDAS imaging parameters
- Missing: Clump extraction method
- Data volume (inferred): small (<5 GB for ALMA; plus Herschel, GALEX, ATCA)
- Score (inferred): 3/5, ALMA part is brief with missing imaging details; archival data are public.
- Rediscovery candidate: no, ALMA processing details are insufficient and the main results rely on several other data sets.

## Links

- Method: (cite: Leroy_2013) (alpha_CO metallicity correction and depletion-time scatter)
- Companion: (cite: Charmandaris_2000) (SEST CO observations of shells)
- Companion: (cite: Santoro_2015b) (MUSE data of the outer filament)

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
  "stated": 33,
  "rate": 0.471
 },
 "evidence_ok": true
}
```
