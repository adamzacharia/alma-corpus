# Modelling the carbon AGB star R Sculptoris. Constraining the dust properties in the detached shell based on far-infrared and sub-millimeter observations

`2018A&A...614A..17B` | Astronomy and Astrophysics 2018 | first author: Brunner, M. | arXiv: - | DOI: 10.1051/0004-6361/201732065

Card schema 1.0 | model claude-sonnet-5-5 | depth light | type multi_facility_alma_minor

## Science

- Fields: evolved_stars
- Question: What are the dust properties in the detached shell of R Scl, and how do they affect the SED and the derived dust shell mass?  
  > "We study the properties of dust grains in the detached shell around the carbon AGB star R Scl and aim to quantify the influence of the dust grain properties on the shape of the spectral energy distribution (SED) and the derived dust shell mass." (abstract)
- Target **R Scl**: coordinates _not stated_; z/distance 370 pc  
  > "We adopt a distance of 370 pc, which is derived from the P – L relationship for semi-regular variables" (1. Introduction); distance from P-L relationship for semi-regular variables (Knapp et al. 2003)  
  > "We adopt a distance of 370 pc, which is derived from the P – L relationship for semi-regular variables" (1. Introduction)

## Data provenance

- ALMA projects: 2011.0.00131.S
- bands: Bands 3, 6, and 7  
  > "with 16 antennas in the main array in ALMA Bands 3, 6, and 7" (2.2 Continuum observations from ALMA)
- frequencies and spectral setup: _not stated_
- continuum bandwidth: _not stated_
- arrays: main array, 16 antennas, Cycle 0  
  > "with 16 antennas in the main array in ALMA Bands 3, 6, and 7" (2.2 Continuum observations from ALMA)
- configurations: _not stated_
- baselines: _not stated_
- angular resolution: _not stated_
- max recoverable scale: _not stated_
- sensitivity: _not stated_
- time on source: _not stated_
- observing dates: _not stated_
- pi or archival as stated: _not stated_
- Other facility **Herschel PACS/SPIRE**: FIR photometry at 70, 160, 250, 350, 500 µm  
  > "We additionally included Herschel/PACS photometry at 70 and 160 µm, and Herschel/SPIRE photometry at 250, 350 and 500 µm" (2.1 Spectral energy distribution towards R Scl)
- Other facility **APEX/LABOCA**: 870 µm map, archival data re-reduced with CRUSH  
  > "The data were re-reduced using CRUSH (Kovács 2008)." (2.3 APEX/LABOCA observations)
- External data: Optical to 100 µm photometry (Kerschbaum & Hron 1994, IRAS) for the SED  
  > "0.44 0.16 0.20 Kerschbaum & Hron (1994)" (Table 1) [from Kerschbaum & Hron (1994); IRAS]
- External data: Optical constants of amorphous carbon  
  > "used the optical constants derived by Suh (2000), unless otherwise mentioned." (3.6 Dust properties) [from Suh (2000)]

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
- smoothing: ALMA Band 7 convolved with the LABOCA beam and subtracted from the LABOCA map  
  > "We convolved the ALMA Band 7 observations with the LABOCA beam, and subtracted the emission from the LABOCA map." (2.3 APEX/LABOCA observations)
- final beam: _not stated_
- final rms: _not stated_

### Inherited from earlier work

- Details of the ALMA observations  
  > "for more details on the observations, we refer to Maercker et al. 2012, 2016" (2.2 Continuum observations from ALMA) [from Maercker et al. 2012, 2016]

### Not stated but needed to reproduce (our reading)

- ALMA calibration and imaging details and continuum flux extraction method
- CASA version
- Band 7 continuum image used for stellar subtraction
- Opacity tables and grid steps for MCMax

## Analysis recipe

1. **Fit stellar blackbody**: Grid of blackbodies fit by chi-square to SED points shorter than 4 µm  
  > "we calculated a small grid of black bodies with varying T eff,⋆ and L ⋆ to determine the best-fitting parameters to our observational data, shorter than 4 µm" (3.3 Stellar parameters and contribution)
   - assumption: Distance 370 pc  
  > "The best-fitting parameters are T eff,⋆ = 2250 K and L ⋆ = 7000 L ⊙ for a distance of D = 370 pc." (3.3 Stellar parameters and contribution)
   - fitting: _not stated_
   - validation: ALMA points reproduced by stellar contribution alone  
  > "It is evident that the ALMA observations do not represent any detached-shell contribution but are reproduced by the stellar contribution alone." (3.3 Stellar parameters and contribution)
2. **Model wind and shell SED, fit mass-loss and shell mass**: MCMax radiative transfer grids of 50-150 models, chi-square minimisation, then fine scaled grid of 1000 models for shell mass and 1σ error  
  > "we calculated MCMax radiative transfer model grids with typical sizes of 50–150 models and varying step sizes" (3.8 Model grid and refinement)
   - software: MCMax
   - parameter: Grain size 0.1 µm, density 1.8 g cm-3, condensation temperature 1500 K, Suh (2000) optical constants  
  > "We adopted a grain size of 0.1 µm and a grain density of 1.8 g cm −3" (3.6 Dust properties)
   - assumption: Optically thin dust, full gas-dust coupling  
  > "We assumed that the dust emission is optically thin." (3.2 General assumptions and modelling strategy)
   - fitting: chi-square minimisation; scaling factor 0.05 to 2 in 1000 steps; 1σ confidence interval  
  > "multiplied the shell spectrum by a scaling factor, ranging from 0.05 to 2 in 1000 steps" (3.8 Model grid and refinement)
   - validation: Compared with Schöier et al. (2005)  
  > "our best-fitting shell mass is consistent with their published (3.2 ± 2.0) × 10 −5 M ⊙" (4.1 Best-fitting standard model for present-day wind and detached shell)
3. **Vary dust properties**: Repeat fits for different optical constants, MgS/SiC mixtures, large grains, DHS and fluffy grains  
  > "We explore the effect on the model SED of the assumed optical constants, grain composition, grain size, and geometrical grain model." (4.2 Changing the dust grain properties)
   - software: MCMax, DDSCAT
   - fitting: _not stated_
   - validation: _not stated_

## Software

- **MCMax** : Monte Carlo dust radiative transfer SED models  
  > "We used the Monte Carlo dust radiative transfer code MCMax (Min et al. 2009)" (3.1 SED models with MCMax)
- **CRUSH** : Reduction of LABOCA data  
  > "The data were re-reduced using CRUSH (Kovács 2008)." (2.3 APEX/LABOCA observations)
- **DDSCAT** : Opacities of the example fluffy aggregate grain  
  > "used for calculating opacities with DDSCAT (Draine & Flatau 1994)" (Figure 11 caption)

## Numeric results

| quantity | value | uncertainty | units | step | quote |
|---|---|---|---|---|---|
| Detached shell dust mass (best fit) | 2.9e-5 | 0.3e-5 | Msun | 2 | a detached shell dust mass of (2.9 ± 0.3) × 10 −5 M ⊙ |
| Present-day dust mass-loss rate | 2e-10 | not stated | Msun/yr | 2 | a present-day dust mass-loss rate of 2 × 10 −10 M ⊙ yr −1 |
| Stellar effective temperature | 2250 | not stated | K | 1 | T eff,⋆ = 2250 K and L ⋆ = 7000 L ⊙ |
| Shell mass with DHS grains | 1.3e-5 | 0.2e-5 | Msun | 3 | the best-fitting detached-shell mass is (1.3 ± 0.2) × 10 −5 M ⊙ |
| LABOCA map rms | 4.5 | not stated | mJy | 0 | The final map has an rms noise of 4.5 mJy |

## Qualitative findings

- A significant sub-millimeter excess cannot be reproduced by any model and is likely not thermal  
  > "we find a significant sub-millimeter excess that cannot be reproduced by any of the models, but is most likely not of thermal origin." (abstract)

## Claim tuples

- H: How do dust properties affect shell mass and SED? | E: MCMax model grids varying opacities, composition, grain size and geometry | R: Grain size dominates SED shape; geometry most affects shell mass (DHS needs 40% of mass) | F: Grain geometry is the largest uncertainty in dust return | **supported**

## Reasoning

- Why this data: _not stated_
- Why this method: _not stated_
- Alternative: Cold dust explanation for the sub-mm excess rejected (needs T<5 K)  
  > "This corresponds to temperatures lower than 5 K (Fig. 12)." (4.3 Sub-millimeter excess)
- How they decided it was enough: _not stated_
- Limitation (authors): Present-day mass-loss rate is poorly constrained and should be interpreted with care  
  > "The determined value for the present-day mass-loss rate should therefore be interpreted with some care." (3.4 Present-day wind description)
- Caveat (inferred, ours): Chi-square values are high (3.7) and the sub-mm excess is excluded from the fit
- Caveat (inferred, ours): 1D spherical model ignores shell clumpiness

## Reproducibility

- Data public (paper): Archival LABOCA data retrieved; ALMA data from Cycle 0 project  
  > "We retrieved archival data of R Scl observed with LABOCA" (2.3 APEX/LABOCA observations)
- Products in archive: _not stated_
- Missing: ALMA flux extraction details
- Missing: MCMax input files
- Data volume (inferred): Small for ALMA continuum; LABOCA archival data tens of GB or less
- Score (inferred): 3/5, The SED data are tabulated and the modelling is well described, but ALMA processing is deferred to other papers.
- Rediscovery candidate: no, ALMA plays a minor role; the main results are from MCMax modelling with incompletely specified inputs.

## Links

- Method: Min et al. 2009 (MCMax code)
- Companion: Maercker et al. 2012, 2016 (Source of the ALMA observations)
- Related: MESS

## Checks

```json
{
 "quotes": 35,
 "quotes_ok": 35,
 "quote_pass_rate": 1.0,
 "quotes_too_long": 1,
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
  "stated": 27,
  "rate": 0.409
 },
 "evidence_ok": true
}
```
