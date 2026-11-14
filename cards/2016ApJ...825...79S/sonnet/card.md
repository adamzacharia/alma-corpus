# Survey Observations of a Possible Glycine Precursor, Methanimine (CH2NH)

`2016ApJ...825...79S` | The Astrophysical Journal 2016 | first author: Suzuki, Taiki | arXiv: 1605.02161 | DOI: 10.3847/0004-637X/825/1/79

Card schema 1.0 | model claude-sonnet-5-5 | depth light | type multi_facility_alma_minor

## Science

- Fields: astrochemistry, star_formation
- Question: Which star-forming regions show CH2NH, what distinguishes CH2NH-rich sources, and how is CH2NH formed (gas phase vs dust surface)?  
  > "in order to increase number of CH$_2$NH sources and to better understand the characteristics of CH$_2$NH sources." (abstract)
- Target **Orion KL (ALMA SV data)**: coordinates 05 35 14.5 -05 22 30.6  
  > "| Orion KL | 05 35 14.5 | -05 22 30.6 | 6 | 0.4 | M | H | confirm | 1, 8 |" (Table 3); z/distance 0.4 kpc  
  > "| Orion KL | 05 35 14.5 | -05 22 30.6 | 6 | 0.4 | M | H | confirm | 1, 8 |" (Table 3); distance from Menten07 (Table reference 8)  
  > "| Orion KL | 05 35 14.5 | -05 22 30.6 | 6 | 0.4 | M | H | confirm | 1, 8 |" (Table 3)

## Data provenance

- ALMA projects: _none stated_
- bands: _not stated_
- frequencies and spectral setup: _not stated_
- continuum bandwidth: _not stated_
- arrays: _not stated_
- configurations: _not stated_
- baselines: _not stated_
- angular resolution: synthesized beam ~2" (ALMA SV Orion KL Band 6 data)  
  > "This data have the spectral resolution of 488 kHz and the synthesized beam size of $\sim$2"." (Derivation of Abundance)
- max recoverable scale: _not stated_
- sensitivity: _not stated_
- time on source: _not stated_
- observing dates: _not stated_
- pi or archival as stated: _not stated_
- Line: CH2NH 1_11-0_00 (225.55455 GHz)
- Other facility **NRO 45 m**: CH2NH 4_04-3_13 at 105 GHz toward 14 sources  
  > "The 4$_{ 0 4}$-3$_{ 1 3}$ transition at 105 GHz was observed." (Observations)
- Other facility **SMT (ARO)**: CH2NH lines at 225, 245, 255 GHz  
  > "the 1$_{ 1 1}$-0$_{ 0 0}$, 4$_{ 1 4}$-3$_{ 1 3}$, and 4$_{ 2 3}$-3$_{ 2 2}$ lines at 225, 245, and 255 GHz regions, respectively, were observed." (Observations)
- External data: 0.8 mm dust continuum map of Orion KL for comparison  
  > "CH$_2$NH distributions are compared with the 0.8 mm dust continuum emission in Figure 4 of (cite: Hirota15)." (Derivation of Abundance) [from (cite: Hirota15)]
- External data: Past CH2NH transitions for rotation diagrams of Orion KL and W51  
  > "for Orion KL and W51 e1/e2, we made rotation diagrams by including other CH$_2$NH transitions reported by (cite: Dickens97)." (Derivation of Abundance) [from (cite: Dickens97)]
- Simulation/model as data: NAUTILUS gas-grain models A-D with collapse plus warm-up  
  > "the NAUTILUS gas-grain chemical model (cite: Semenov10; Reboussin14) has been used with the similar physical model used in (cite: Garrod13)" (The Nautilus Chemical Model)

## Processing

### Calibration

- pipeline or manual: _not stated_
- casa version: _not stated_
- pipeline version: _not stated_
- archive products used as is: calibrated Science Verification data used  
  > "using the calibrated Science Verification data of ALMA cycle 0" (Derivation of Abundance)
- flux calibrator: _not stated_
- flux scale uncertainty: _not stated_
- self calibration: _not stated_

### Imaging

- task: CASA CLEAN  
  > "The channel maps of CH$_2$NH 1$_{1 1}$-0$_{ 0 0}$ distribution were made by the CASA task, CLEAN." (Derivation of Abundance)
- deconvolver: _not stated_
- weighting robust: equal weighting of uv  
  > "We employed the equal weighting of uv, and set the threshold value to stop CLEAN task at 72 mJy" (Derivation of Abundance)
- uv taper: _not stated_
- cell size: _not stated_
- image size: _not stated_
- masking: _not stated_
- multiscale scales: _not stated_
- continuum subtraction: uvcontsub in uv domain with line-free channels  
  > "We selected line-free channels for continuum subtraction in the (u, v) domain using the CASA task, uvcontsub." (Derivation of Abundance)
- line free channels: _not stated_
- primary beam correction: _not stated_
- array combination: _not stated_
- smoothing: _not stated_
- final beam: _not stated_
- final rms: _not stated_

### Inherited from earlier work

- NAUTILUS physical model and initial abundances follow Garrod13 fast warm-up model  
  > "The physical conditions used as input to the chemical model are based on the "fast warm-up model" from (cite: Garrod13)." (The Physical Model) [from (cite: Garrod13)]
- Rotation-diagram method  
  > "we calculated column densities of CH$_2$NH using the rotation-diagram method described in (cite: Turner91)" (Derivation of Abundance) [from (cite: Turner91)]

### Not stated but needed to reproduce (our reading)

- ALMA SV project code and CASA version
- line-free channels and cell/image size for the Orion KL cube
- moment-map integration details
- beam coupling factor formulae

## Analysis recipe

1. **Map CH2NH in Orion KL from ALMA SV data**: uvcontsub, CLEAN channel maps, integrated intensity 225.55348-225.55641 GHz  
  > "we made the integrated intensity map from 225.55348 to 225.55641 GHz, corresponding to the V$_{\rm LSR}$ range from 6.5 to 10.4 km s$^{-1}$." (Derivation of Abundance)
   - software: CASA
   - parameter: CLEAN threshold 72 mJy  
  > "set the threshold value to stop CLEAN task at 72 mJy considering the r.m.s level." (Derivation of Abundance)
   - fitting: _not stated_
   - validation: compared with 0.8 mm continuum of Hirota15 to justify using continuum size as source size  
  > "Since the distribution of CH$_2$NH and dust continuum emission look similar to each other, dust continuum emissions would be good indicators to estimate the source sizes of CH$_2$NH." (Derivation of Abundance)
2. **Derive column densities and abundances**: rotation diagrams least-squares, with Trot fixed at 40 K for single lines  
  > "we assumed that the excitation temperature is similar to that of HCOOH (40 K) reported by (cite: Ikeda01)" (Derivation of Abundance)
   - parameter: source size from continuum, else 10"  
  > "If continuum data are not available, we assume a source size of 10" in the derivation." (Derivation of Abundance)
   - assumption: Tex uncertainty +-20 K changes N by 40%  
  > "we assumed that the excitation temperatures can be changed within $\pm$20 K, which can change the column densities by 40$\%$." (Derivation of Abundance)
   - fitting: least-squares fit of rotation diagram  
  > "The column density and the excitation temperature can be derived by utilizing the least-squares fitting." (Derivation of Abundance)
   - validation: compared with Dickens97 column densities  
  > "which agrees within a factor of 2." (CH2NH Abundances)
3. **Chemical modelling of CH2NH formation**: NAUTILUS gas-grain models A-D, collapse then warm-up  
  > "We have run four different models (A, B, C and D) with different peak density and/or temperature as listed in Table [\[models\]]" (The Physical Model)
   - software: NAUTILUS
   - fitting: _not stated_
   - validation: _not stated_

## Software

- **CASA** : imaging ALMA SV Orion KL data  
  > "The data were imaged with the Common Astronomy Software Applications (CASA) package." (Derivation of Abundance)
- **NAUTILUS** : gas-grain chemical simulations  
  > "To simulate the abundance of CH$_2$NH in hot cores, the NAUTILUS gas-grain chemical model" (The Nautilus Chemical Model)

## Numeric results

| quantity | value | uncertainty | units | step | quote |
|---|---|---|---|---|---|
| CH2NH fractional abundance Orion KL (compact) | 3.3e-8 | 0.5e-8 | dimensionless | 2 | 5.5 ($\pm$0.8) $\times$ 10$^{15}$ cm$^{-2}$ and 3.3 ($\pm$0.5) $\times$ 10$^{-8}$ |
| CH2NH fractional abundance G10.47+0.03 | 3.1e-8 | 1.1e-8 | dimensionless | 2 | In G10.47+0.03, the fractional abundance is 3.1 ($\pm$1.1) $\times$ 10$^{-8}$. |
| Upper limit desorption temperature of CH2NH | 160 | not stated | K | 0 | the upper limit to the desorption temperature can be calculated to be 160 K |

## Qualitative findings

- CH2NH detected in eight sources including four new; rich sources have less evolved HII regions  
  > "CH$_2$NH was detected in eight sources, including four new sources." (abstract)

## Claim tuples

- H: CH2NH is mainly gas-phase formed rather than evaporated | E: NAUTILUS models A-D | R: dust-surface CH2NH is <1e-12, NH + CH3 dominant | F: gas-phase neutral-neutral formation | **supported**
- H: CH2NH richness is tied to HII region evolution | E: H54beta comparison | R: weak/absent in rich sources | F: less evolved HII regions in CH2NH-rich sources | **partially**

## Reasoning

- Why this data: _not stated_
- Why this method: _not stated_
- Alternative: Distance and temperature differences rejected as explanations  
  > "temperature differences among hot core sources could not explain our observational results." (Characteristics of CH2NH-rich Sources)
- How they decided it was enough: _not stated_
- Limitation (authors): Large error in G31.41+0.3 abundance due to scatter in rotation diagram  
  > "The large error of the fractional abundance in G31.41+0.3 is due to scattering of the plots in its rotation diagram" (CH2NH Abundances)
- Caveat (inferred, ours): ALMA is used only for source size justification
- Caveat (inferred, ours): Recombination line comparison covers few sources
- Caveat (inferred, ours): Single-dish beam dilution and Tex assumptions

## Reproducibility

- Data public (paper): ALMA SV data from public URL  
  > "(https://almascience.eso.org/almadata/sciver/OrionKLBand6/)" (Derivation of Abundance)
- Products in archive: _not stated_
- Missing: Single-dish spectra not public
- Missing: Chemical network files from Garrod/Herbst
- Missing: ALMA processing parameters
- Data volume (inferred): ~10-50 GB for ALMA SV Orion KL Band 6
- Score (inferred): 2/5, ALMA part is minor; main results are single-dish and modelling with incomplete details.
- Rediscovery candidate: no, Main results rely on non-public single-dish data and a private chemical network.

## Links

- Method: (cite: Turner91) (rotation-diagram method)
- Method: (cite: Ruaud15) (NAUTILUS model details)
- Companion: (cite: Dickens97) (earlier CH2NH survey that this work extends)
- Related: ALMA Cycle 0 Science Verification Orion KL Band 6

## Checks

```json
{
 "quotes": 39,
 "quotes_ok": 39,
 "quote_pass_rate": 1.0,
 "quotes_too_long": 0,
 "unsupported_facts": 0,
 "project_codes": 0,
 "codes_not_in_text": [],
 "codes_not_in_obscore": [],
 "obscore_codes_not_in_card": [
  "2011.0.00009.SV"
 ],
 "codes_printed_but_missing": [],
 "numeric_results": 3,
 "numeric_problems": 0,
 "fill": {
  "facts": 67,
  "stated": 31,
  "rate": 0.463
 },
 "evidence_ok": true
}
```
