# Interpreting high spatial resolution line observations of planet-forming disks with gaps and rings: the case of HD 163296

`2020A&A...642A.165R` | Astronomy and Astrophysics 2020 | first author: Rab, Ch. | arXiv: 2008.05941 | DOI: 10.1051/0004-6361/202038712

Card schema 1.0 | model claude-sonnet-5-5 | depth light | type theory_or_simulation_compared_to_alma

## Science

- Fields: protoplanetary_disks, astrochemistry
- Question: How important are thermo-chemical processes and dust gaps for interpreting high-resolution gas (CO) observations of gaps and rings in the HD 163296 disk, and for derived gas properties?  
  > "We want to investigate the importance of thermo-chemical processes for the interpretation of high-spatial-resolution gas observations of planet-forming disks and their impact on the derived gas properties." (abstract)
- Target **HD 163296**: coordinates _not stated_; z/distance 101 pc  
  > "We updated the DIANA HD 163296 model considering the new GAIA distance ($d=101\,\mathrm{pc}$)" (2.2 HD 163296 model); distance from GAIA  
  > "We updated the DIANA HD 163296 model considering the new GAIA distance ($d=101\,\mathrm{pc}$)" (2.2 HD 163296 model)

## Data provenance

- ALMA projects: 2013.1.00366.S, 2013.1.00601.S, 2016.1.00484.L
- bands: _not stated_
- frequencies and spectral setup: 1.25 mm continuum; 12CO J=2-1 channel width 0.32 km/s, resolution 0.64 km/s (Hanning)  
  > "a channel width of $0.32\,\mathrm{km\,s^{-1}}$ (but the spectral resolution is $0.64\,\mathrm{km\,s^{-1}}$ due to Hanning smoothing)" (2.3 Observational dataset and synthetic observables)
- continuum bandwidth: _not stated_
- arrays: _not stated_
- configurations: _not stated_
- baselines: _not stated_
- angular resolution: Continuum 0.038"x0.048" (~4.3 au); 12CO 0.104"x0.095" (~10 au)  
  > "The beam size of the dust continuum observations at 1.25mm is $0.038\ensuremath{''}\times0.048\ensuremath{''}$ ($\sim4.3\,\mathrm{au}$)" (2.3 Observational dataset and synthetic observables)
- max recoverable scale: _not stated_
- sensitivity: continuum rms 0.023 mJy/beam; CO rms 0.84 mJy/beam per channel  
  > "a rms noise per channel of $0.84\,\mathrm{mJy/beam}$" (2.3 Observational dataset and synthetic observables)
- time on source: _not stated_
- observing dates: _not stated_
- pi or archival as stated: _not stated_
- Line: 12CO J=2-1 (not stated)
- External data: DSHARP HD 163296 1.25 mm continuum and 12CO J=2-1 data  
  > "we focus on the HD 163296 DSHARP dataset (cite: Andrews2018) that is described in detail in (cite: Isella2018)." (2.3 Observational dataset and synthetic observables) [from (cite: Andrews2018); (cite: Isella2018)]
- External data: Disk mass ~0.2 Msun from 13C17O  
  > "the disk mass of $\sim0.2\,M_\mathrm{\ensuremath{\odot}}$ as derived by (cite: Booth2019) from $^{13}\mathrm{C}^{17}\mathrm{O}$ observations" (2.2 HD 163296 model) [from (cite: Booth2019)]
- Simulation/model as data: DIANA HD 163296 model as starting point, updated  
  > "we used an existing model from the DIANA project (DIsc ANAlysis) that matches the SED and line fluxes from near-infrared to millimetre wavelengths within a factor of about two" (2.2 HD 163296 model)

## Processing

### Calibration

- pipeline or manual: _not stated_
- casa version: _not stated_
- pipeline version: _not stated_
- archive products used as is: Published DSHARP data products used  
  > "For this work we focus on the HD 163296 DSHARP dataset (cite: Andrews2018)" (2.3 Observational dataset and synthetic observables)
- flux calibrator: _not stated_
- flux scale uncertainty: _not stated_
- self calibration: _not stated_

### Imaging

- task: CASA convolve2d and regrid applied to model images  
  > "using the image functions `convolve2d` and `regrid`, respectively." (2.3 Observational dataset and synthetic observables)
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

- Radial profile extraction approach  
  > "we produced azimuthally averaged radial intensity profiles for the dust and the gas emission following the approach of (cite: Huang2018)." (2.3 Observational dataset and synthetic observables) [from (cite: Huang2018)]
- Dust gap introduction by fitting radial dust intensity profile  
  > "we follow the approach used by (cite: Pinte2016) for HL Tau and (cite: Muro-Arena2018) for HD 163296." (2.4 Fiducial models) [from (cite: Pinte2016); (cite: Muro-Arena2018)]
- Gas gap shape (Gaussian wings and flat bottom)  
  > "The shape of the gaps are a combination of Gaussian wings and a flat bottom (for details see (cite: Oberg2020))." (2.4 Fiducial models) [from (cite: Oberg2020)]

### Not stated but needed to reproduce (our reading)

- PRODIMO code version and run settings (grid, photon numbers)
- Exact gap locations/widths for gas and dust gaps
- Fitted dust surface density profile values
- Aperture/annulus details of radial profiles beyond one-third beam width
- Emission layer height used for Keplerian masks
- Stellar UV/X-ray spectrum

## Analysis recipe

1. **Build baseline thermo-chemical disk model**: Update DIANA HD 163296 model with Gaia distance, new stellar parameters and disk mass; run PRODIMO  
  > "We updated the DIANA HD 163296 model considering the new GAIA distance ($d=101\,\mathrm{pc}$), adapted stellar parameters" (2.2 HD 163296 model)
   - software: PRODIMO
   - assumption: Parameterized vertical structure, not hydrostatic  
  > "We therefore do not self-consistently calculate the hydrostatic equilibrium structure." (7 Disk model)
   - fitting: _not stated_
   - validation: Matches SED and line fluxes to similar quality as DIANA model  
  > "still matches the SED and line fluxes to a similar quality as the original DIANA model" (2.2 HD 163296 model)
2. **Measure observed radial profiles**: Azimuthally averaged elliptical apertures on continuum and 12CO moment 0, i=46.7, PA=133.3  
  > "The width of the aperture is about one third of the beam width." (2.3 Observational dataset and synthetic observables)
   - fitting: _not stated_
   - validation: Nearly identical dust profile to Huang et al. 2018  
  > "This procedure gives a nearly identical dust radial profile as derived by (cite: Huang2018)" (2.3 Observational dataset and synthetic observables)
3. **Introduce dust and gas gaps**: Iteratively adapt dust surface density to fit continuum profile; parameterized gas gaps with fixed depletion factors  
  > "We fit the radial dust intensity profile by adapting the dust surface density via an iterative procedure but keep all other dust properties" (2.4 Fiducial models)
   - software: PRODIMO
   - parameter: GASGAPS depletion 1000, 20, 5; GASGAPS S factor 3  
  > "we use gas depletion factors of 1000, 20, and 5 for DG1 to DG3" (2.4 Fiducial models)
   - fitting: Gas profiles not fitted  
  > "We emphasize that we did not fit the gas data to produce the gas surface density profiles" (2.4 Fiducial models)
   - validation: _not stated_
4. **Synthetic observables and front/back separation**: PRODIMO line radiative transfer, convolve with beam and regrid; Keplerian masks to separate sides  
  > "we applied the `CLEAN_mask` routine from the python package `imgcube`" (8 Separating the back and front side)
   - software: PRODIMO, CASA, imgcube
   - fitting: _not stated_
   - validation: _not stated_
5. **Derive rotation velocity deviations in model**: Vertically average v_rot over layer between 15% and 85% of integrated flux  
  > "define the top and bottom border of the region where the flux reaches 15% and 85% of the total flux, respectively" (4 Impact of thermo-chemical processes)
   - software: PRODIMO
   - assumption: Self-gravity neglected  
  > "We neglect here the impact of self-gravity" (4 Impact of thermo-chemical processes)
   - fitting: _not stated_
   - validation: _not stated_

## Software

- **PRODIMO** : Thermo-chemical disk modelling and line radiative transfer  
  > "we used the radiation thermo-chemical disk code PRODIMO" (2.1)
- **CASA** : convolve2d and regrid of synthetic images  
  > "using the image functions `convolve2d` and `regrid`" (2.3)
- **imgcube** : Keplerian masks  
  > "we applied the `CLEAN_mask` routine from the python package `imgcube`" (8)

## Numeric results

| quantity | value | uncertainty | units | step | quote |
|---|---|---|---|---|---|
| Dust gap depths DG1, DG2, DG3 | ~1700, 50, 3 | not stated | dimensionless | 3 | We find gap depths of roughly $\Delta_\mathrm{gap}\sim1700$, 50 and 3 |
| Dust epsilon_d of model | 0.14 | not stated | dimensionless | 1 | we get $\epsilon_d=0.14$ for our dust model |

## Qualitative findings

- CO radial peaks at dust gaps mainly arise from absorption of back-side emission by dust rings  
  > "are mainly caused by the absorption of line emission from the back side of the disk by the dust rings" (abstract)

## Claim tuples


## Reasoning

- Why this data: _not stated_
- Why this method: _not stated_
- How they decided it was enough: _not stated_
- Limitation (authors): Dust model overestimates ring optical depth and temperature in DG1; no precise gas fit  
  > "This indicates that our dust model overestimates the extinction properties of the dust and the optical depth in the rings" (3.2)
- Caveat (inferred, ours): Models not fitted to gas data
- Caveat (inferred, ours): Single-disk, single-line study
- Caveat (inferred, ours): Dust model lacks radial variation of grain sizes

## Reproducibility

- Data public (paper): DSHARP data public via project website  
  > "https://almascience.eso.org/almadata/lp/DSHARP" (footnote)
- Products in archive: _not stated_
- Missing: PRODIMO version and gap parameters
- Missing: Model output not provided
- Data volume (inferred): ~10-50 GB (DSHARP products)
- Score (inferred): 3/5, Public data and a described model, but PRODIMO setup incompletely specified.
- Rediscovery candidate: no, Main results are model-based and qualitative with incomplete model parameters.

## Links

- Method: (cite: Isella2018) (DSHARP HD 163296 data description)
- Method: (cite: Woitke2016) (PRODIMO methods)
- Related: DSHARP
- Related: DIANA

## Checks

```json
{
 "quotes": 38,
 "quotes_ok": 38,
 "quote_pass_rate": 1.0,
 "quotes_too_long": 0,
 "unsupported_facts": 0,
 "project_codes": 3,
 "codes_not_in_text": [],
 "codes_not_in_obscore": [],
 "obscore_codes_not_in_card": [],
 "codes_printed_but_missing": [],
 "numeric_results": 2,
 "numeric_problems": 0,
 "fill": {
  "facts": 72,
  "stated": 31,
  "rate": 0.431
 },
 "evidence_ok": true
}
```
