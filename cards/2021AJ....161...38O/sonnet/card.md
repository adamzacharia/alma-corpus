# The TW Hya Rosetta Stone Project. I. Radial and Vertical Distributions of DCN and DCO<SUP>+</SUP>

`2021AJ....161...38O` | The Astronomical Journal 2021 | first author: Öberg, Karin I. | arXiv: 2011.06774 | DOI: 10.3847/1538-3881/abc74d

Card schema 1.0 | model claude-sonnet-5-5 | depth full | type observational_alma_primary

## Science

- Fields: protoplanetary_disks, astrochemistry
- Question: Which parts of the TW Hya disk host active deuterium fractionation chemistry, as traced by the radial, vertical and temperature distributions of DCO+ and DCN?  
  > "Yet it is unclear which parts of the Solar Nebula hosted an active deuterium fractionation chemistry." (abstract)
- Target **TW Hya**: coordinates _not stated_; z/distance _not stated_; distance from _not stated_

## Data provenance

- ALMA projects: 2016.1.00311.S, 2017.1.00769.S, 2016.1.00440.S
- bands: _not stated_
- frequencies and spectral setup: _not stated_
- continuum bandwidth: _not stated_
- arrays: _not stated_
- configurations: _not stated_
- baselines: 15–1398 m  
  > "15–1398" (Table 1)
- angular resolution: 0.2''–0.4'' (nominal 0.20–0.89'' per execution)  
  > "we present 0.2$''$–0.4$''$ ALMA observations of DCO$^+$ and DCN 2–1, 3–2 and 4–3" (abstract)
- max recoverable scale: _not stated_
- sensitivity: _not stated_
- time on source: _not stated_
- observing dates: Oct 2016 – Sep 2018 (nine executions)  
  > "Oct 22, 2016" (Table 1); "Sep 20, 2018" (Table 1)
- pi or archival as stated: Rosetta Stone (PI Cleeves) for 3–2 and 4–3; 2016.1.00440.S (PI Teague) for 2–1  
  > "Observations of DCO$^+$ and DCN 2–1 were obtained as part of project 2016.1.00440.S (PI: Teague) in three separate executions." (2 Observational Details)
- Line: DCO+ J=2–1, 3–2, 4–3 (144.077285, 216.112582, 288.143858 GHz)
- Line: DCN J=2–1, 3–2, 4–3 (144.827996, 217.238537, 289.644917 GHz)
- External data: Line catalogue data (frequencies, Aij, Eu, partition functions)  
  > "Line catalogue data from CDMS (cite: Muller05)" (Table 2) [from (cite: Muller05)]
- External data: DCO+ molecular file for radiative transfer  
  > "We used the DCO$^+$ molecular file from LAMDA (cite: Schoier05)" (4 Exploratory parametric models) [from (cite: Schoier05)]

## Processing

### Calibration

- pipeline or manual: Initial calibration by JAO staff, then phase-only self-calibration on line-free continuum (30 s integrations) for Rosetta data  
  > "Phase-only self calibration was conducted on the line free continuum using 30 second integrations and averaging both polarizations." (2 Observational Details)
- casa version: CASA 4.5 (self-calibration)  
  > "Additional self calibration was applied to the pipeline calibrated data for the TW Hya Rosetta Stone observations using CASA 4.5." (2 Observational Details)
- pipeline version: _not stated_
- archive products used as is: _not stated_
- flux calibrator: _not stated_
- flux scale uncertainty: 10%  
  > "Uncertainty does not include 10% flux calibration uncertainty." (Table 2)
- self calibration: _not stated_

### Imaging

- task: uvcontsub, CLEAN (Högbom)  
  > "The line data were continuum subtracted using *uvcontsub* and imaged with the CLEAN algorithm (cite: Hogbom74)." (2 Observational Details)
- deconvolver: _not stated_
- weighting robust: Briggs 0.5  
  > "a Briggs parameter of 0.5 for the fiducial image cubes" (2 Observational Details)
- uv taper: _not stated_
- cell size: _not stated_
- image size: _not stated_
- masking: Manual per-channel masks; cleaned to 2×rms  
  > "we employed a mask, constructed by manually identifying areas with emission in each channel" (2 Observational Details)
- multiscale scales: _not stated_
- continuum subtraction: _not stated_
- line free channels: _not stated_
- primary beam correction: _not stated_
- array combination: _not stated_
- smoothing: imsmooth to circular 0.5'' beam  
  > "smoothed using *imsmooth* in CASA with a circular 0.5$''$ beam" (2 Observational Details)
- final beam: _not stated_
- final rms: 1.1–3.4 mJy/beam per channel  
  > "DCO$^+$ J=3–2 | 216.112582$^{d}$ | -3.12 | 20.74 | 7 | $0.49\ensuremath{''}\times0.31\ensuremath{''}$ ($88^{\circ}$) | 3.4" (Table 2)

### Inherited from earlier work

- Rotational diagram MCMC procedure  
  > "we follow the MCMC procedure outlined in (cite: Loomis18b), using the `emcee` package" (3.2 Rotational diagram analysis) [from (cite: Loomis18b)]
- Gas surface density and scale height model  
  > "to mimic the surface density model presented in (cite: Cleeves15)" (4 Exploratory parametric models) [from (cite: Cleeves15)]
- Midplane temperature power law  
  > "using the normalization factor and power-law index derived in (cite: Zhang17)" (4 Exploratory parametric models) [from (cite: Zhang17)]
- Atmosphere temperature prescription  
  > "using the common prescription from (cite: Dartois03)" (4 Exploratory parametric models) [from (cite: Dartois03)]
- Keplerian masks for spectra  
  > "using Keplerian masks (cite: Pegues20) to enhance the SNR" (3.1 DCN and DCO$^+$ emission maps and spectra) [from (cite: Pegues20)]

### Not stated but needed to reproduce (our reading)

- Line-free channels and uvcontsub fit order
- Image size and cell size
- Self-calibration details beyond solint, and whether 2016.1.00440.S data were self-calibrated
- Radial bin widths for rotational diagrams, and MCMC priors and walker settings
- Keplerian mask parameters, stellar mass and emission surface used
- Source distance adopted for au conversions
- Details of the 2017.1.00769.S data (not linked by archive)
- Exact model grids, inner-hole depletion factor and molecular file for DCN

## Analysis recipe

1. **Image line cubes and moment maps**: Continuum subtraction, CLEAN with manual masks, Briggs 0.5; second set smoothed to 0.5'' circular beam; moment-0 from channels above 3σ  
  > "The maps are constructed by integrating emission across all channels that show signal above 3$\sigma$" (3.1 DCN and DCO$^+$ emission maps and spectra)
   - software: CASA
   - fitting: _not stated_
   - validation: _not stated_
2. **Radial profiles and integrated fluxes**: Azimuthal averaging of deprojected moment-0 maps in narrow rings  
  > "azimuthally integrating the inclination-corrected maps ($i=7^\circ$ and P.A.=$155^\circ$) in narrow rings" (3.1 DCN and DCO$^+$ emission maps and spectra)
   - assumption: i = 7 deg, PA = 155 deg  
  > "($i=7^\circ$ and P.A.=$155^\circ$)" (3.1 DCN and DCO$^+$ emission maps and spectra)
   - fitting: _not stated_
   - validation: Inclination and PA chosen by visual fit of Keplerian model to channel maps  
  > "they provided the best visual fit to the data when overplotting a Keplerian model on top of channel maps" (3.1 DCN and DCO$^+$ emission maps and spectra)
3. **Disk-averaged and radial rotational diagrams**: LTE rotational diagram with optical depth correction on fluxes within 100 au (0.5'' cubes); DCN 2–1 excluded  
  > "We exclude the DCN 2–1 emission from the rotational diagram analysis because it is likely underestimated" (3.2 Rotational diagram analysis of DCO$^+$)
   - software: emcee
   - assumption: LTE  
  > "the rotational diagram analysis, as well as the parametric models below assume LTE" (3.2 Rotational diagram analysis of DCO$^+$)
   - fitting: MCMC with emcee; 10% flux calibration uncertainty added in quadrature  
  > "The main flux uncertainty is a 10% absolute flux calibration uncertainty, which is added in quadrature" (3.2 Rotational diagram analysis of DCO$^+$)
   - validation: _not stated_
4. **Parametric abundance toy models**: Power-law disk density and temperature structure; RADMC-3D radiative transfer, vis_sample, tclean; compare radial profiles by eye  
  > "we simulate noise-less ALMA observations for the 2–1 and 4–3 lines using `RADMC-3D` (cite: Dullemond12), for the radiative transfer, `vis_sample` for the visibility sampling" (4 Exploratory parametric models)
   - software: RADMC-3D, vis_sample, CASA
   - parameter: Sigma(20au)=35 g cm-2, gamma=-1.3, H(20au)=2 au, p=0.3, mean molecular weight 2.37, T_atm=125 K at 10 au  
  > "set to 35 g cm$^{-2}$, and $-1.3$, respectively" (4 Exploratory parametric models)
   - fitting: Abundances estimated by eye  
  > "The abundance exterior to 25 au is estimated by eye to fit the 4–3 lines." (4.1 Radial boundary models)
   - validation: Simulated observations analyzed identically to data  
  > "The simulated observations are analyzed using the same procedure as applied to our ALMA observations" (4 Exploratory parametric models)

## Software

- **CASA** 4.5 (self-cal): Self-calibration, uvcontsub, CLEAN, imsmooth, tclean  
  > "using CASA 4.5" (2 Observational Details)
- **emcee** : MCMC rotational diagrams  
  > "using the `emcee` package (cite: Foreman-Mackey13)" (3.2 Rotational diagram analysis of DCO$^+$)
- **RADMC-3D** : Radiative transfer of toy models  
  > "using `RADMC-3D` (cite: Dullemond12), for the radiative transfer" (4 Exploratory parametric models)
- **vis_sample** : Visibility sampling of model images  
  > "`vis_sample` for the visibility sampling (cite: Loomis18a)" (4 Exploratory parametric models)
- **Astropy** : Listed in software section  
  > "Astropy (cite: astropy13; astropy18)" (Software)

## Numeric results

| quantity | value | uncertainty | units | step | quote |
|---|---|---|---|---|---|
| Disk-averaged DCO+ column density | 3.9e12 | not stated | cm^-2 | 3 | 2.6 and 3.9$\times10^{12}$ cm$^{-2}$, respectively for DCN and DCO$^+$ |
| Disk-averaged DCN column density | 2.6e12 | not stated | cm^-2 | 3 | 2.6 and 3.9$\times10^{12}$ cm$^{-2}$, respectively for DCN and DCO$^+$ |
| Disk-averaged excitation temperature DCO+ vs DCN | 33 K vs 66 K | not stated | K | 3 | DCO$^+$ appears colder than DCN (33 vs 66 K) |
| DCO+ excitation temperature 25–70 au | 37–39.5 | not stated | K | 3 | Between 25–70 au, the best-fit DCO$^+$ excitation temperatures are 37–39.5 K |
| DCO+ J=4–3 flux within 2.5'' | 3622 | 33 (excl. 10% calibration) | mJy km/s | 2 | 3622$\pm$33 |
| DCN J=4–3 flux within 2.5'' | 1344 | 29 (excl. 10% calibration) | mJy km/s | 2 | 1344$\pm$29 |

## Qualitative findings

- DCN and DCO+ both show inner cavities; DCN is a narrow ring near 30 au with a halo, DCO+ a broad structured ring extending beyond the pebble disk  
  > "most DCN emission originates from a narrow ring peaking around 30 au" (abstract)

## Claim tuples

- H: DCO+ emits from cold midplane near the CO snow surface | E: Multi-line rotational diagrams in radial bins | R: Tex ~37–39.5 K at 25–70 au | F: DCO+ originates in an elevated, warmer layer | **supported**
- H: DCN is warmer than DCO+ | E: Disk-averaged rotational diagram without DCN 2–1 | R: 66 K vs 33 K, DCN poorly constrained | F: Tentative evidence DCN is warmer | **partially**
- H: Simple abundance/temperature-boundary models explain the emission | E: Toy models A1–A3, B1–B2 | R: DCN fit by 25 au hole and constant abundance where T>20 K; DCO+ needs increasing abundance or a second cold reservoir | F: DCO+ abundance rises with radius | **supported**

## Reasoning

- Why this data: _not stated_
- Why this method: _not stated_
- Alternative: Continuum opacity alone as the cause of central cavities, rejected since optically thin 13C18O is centrally peaked  
  > "Continuum opacity cannot be the whole explanation for these central cavities, however" (3.1 DCN and DCO$^+$ emission maps and spectra)
- How they decided it was enough: _not stated_
- Limitation (authors): DCN 2–1 underestimated, making DCN temperature uncertain; LTE assumed; toy models are qualitative  
  > "The DCN 2–1 line emission is likely underestimated due to low SNR" (Table 2)
- Caveat (inferred, ours): Models tuned by eye with no formal fit or uncertainties
- Caveat (inferred, ours): Different resolutions and UV coverage across lines; smoothing to 0.5'' limits radial resolution
- Caveat (inferred, ours): LTE and single-layer assumption in rotational diagrams

## Reproducibility

- Data public (paper): ALMA project codes given; archival data used  
  > "augmented with archival data" (abstract)
- Products in archive: _not stated_
- Missing: Radial binning and MCMC priors
- Missing: Exact clean/mask choices and channel selection
- Missing: Model grids and DCN molecular file
- Data volume (inferred): ~100–300 GB raw across nine executions
- Score (inferred): 3/5, Public data and a reasonable but incompletely specified recipe; toy modelling is by eye.
- Rediscovery candidate: yes, Public data and numeric rotational-diagram results can be redone, though settings are partly missing.

## Links

- Method: (cite: Loomis18b) (MCMC rotational diagram procedure)
- Method: (cite: Pegues20) (Keplerian masks)
- Companion: (cite: Huang18) (TW Hya continuum structure and geometry)
- Related: TW Hya Rosetta Stone project

## Checks

```json
{
 "quotes": 56,
 "quotes_ok": 56,
 "quote_pass_rate": 1.0,
 "quotes_too_long": 0,
 "unsupported_facts": 0,
 "project_codes": 3,
 "codes_not_in_text": [],
 "codes_not_in_obscore": [
  "2017.1.00769.S"
 ],
 "obscore_codes_not_in_card": [],
 "codes_printed_but_missing": [],
 "numeric_results": 6,
 "numeric_problems": 0,
 "fill": {
  "facts": 73,
  "stated": 40,
  "rate": 0.548
 },
 "evidence_ok": true
}
```
