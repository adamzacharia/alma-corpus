# GOALS-JWST: The Warm Molecular Outflows of the Merging Starburst Galaxy NGC 3256

`2024ApJ...977...36B` | The Astrophysical Journal 2024 | first author: Bohn, Thomas | arXiv: 2403.14751 | DOI: 10.3847/1538-4357/ad87d3

Card schema 1.0 | model claude-sonnet-5-5 | depth light | type multi_facility_alma_minor

## Science

- Fields: nearby_galaxies, agn_and_quasars
- Question: What are the mass, temperature, kinematics and energetics of the warm outflowing H2 gas in the merging LIRG NGC 3256, and how does it affect the ISM and PAHs?  
  > "The primary focus of this article is to obtain robust mass estimates and temperatures of the warm outflowing H$_2$ gas, as well as analyze its kinematics and energetics." (Methods of Analysis)
- Target **NGC 3256**: coordinates _not stated_; z/distance z=0.0094 (40.4 Mpc)  
  > "At the redshift of NGC 3256, $z=0.0094$ (40.4 Mpc), $1.0\ensuremath{''}$ subtends $\sim$190 pc." (Introduction); distance from redshift with H0=70, OmegaL=0.72, Omegam=0.28  
  > "At the redshift of NGC 3256, $z=0.0094$ (40.4 Mpc), $1.0\ensuremath{''}$ subtends $\sim$190 pc." (Introduction)

## Data provenance

- ALMA projects: 2015.1.00902.S, 2011.0.00525.S
- bands: _not stated_
- frequencies and spectral setup: _not stated_
- continuum bandwidth: _not stated_
- arrays: _not stated_
- configurations: _not stated_
- baselines: _not stated_
- angular resolution: CO(2-1) beam 1.03"x0.56"  
  > "The spatial resolution of the CO (2-1) data is $1.03\ensuremath{''}\times0.56\ensuremath{''}$" (Footnote 1)
- max recoverable scale: _not stated_
- sensitivity: _not stated_
- time on source: _not stated_
- observing dates: _not stated_
- pi or archival as stated: archival, PI Yiping Ao  
  > "archival CO (2-1) ALMA data (project code: 2015.1.00902.S, PI: Yiping Ao)" (5.2 Outflow Mass Comparisons of MIR to NIR and Submillimeter Measurements)
- Line: CO J=2-1 (not stated)
- Other facility **JWST NIRSpec and MIRI MRS**: Primary IFU data (ERS 1328), warm H2 lines and gas excitation  
  > "Observations of NGC 3256 were taken as part of the Early Release Science (ERS) Program 1328" (Observations and Data Reduction)
- Other facility **VLT/SINFONI**: H2 2.12 um outflow flux map (Emonts2014) for hot-gas mass  
  > "we use the H$_2$ 1-0 S(1) 2.12 $\mu$m outflow flux map created by (cite: Emonts2014)" (5.2 Outflow Mass Comparisons of MIR to NIR and Submillimeter Measurements)
- External data: Outflow inclination ~20 deg  
  > "we adopt the outflow inclination as calculated by (cite: Sakamoto2014) and (cite: Emonts2014), $i_{\rm{out}}\sim20^\circ$" (5.1 Outflow Characteristics) [from (cite: Sakamoto2014), (cite: Emonts2014)]
- External data: SFR 1-6.8 Msun/yr  
  > "estimated the SFR to be 1 - 6.8 M$_{\odot}$ yr$^{-1}$ based on hydrogen recombination line calibrations" (5.2 Outflow Mass Comparisons of MIR to NIR and Submillimeter Measurements) [from (cite: Emonts2014), (cite: Michiyama2018)]

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

- CO(2-1)/CO(1-0) luminosity ratio set to unity  
  > "Following (cite: Michiyama2018), we set L$\rm{_{CO(2-1)}}$/L$\rm{_{CO(1-0)}}$ as unity." (5.2 Outflow Mass Comparisons of MIR to NIR and Submillimeter Measurements) [from (cite: Michiyama2018)]
- Power-law warm H2 temperature model  
  > "we use the power-law model described in (cite: Togi2016)" (4.3 Temperatures and Masses) [from (cite: Togi2016)]

### Not stated but needed to reproduce (our reading)

- ALMA calibration, CASA version and imaging parameters for the CO(2-1) cube
- how CO spectra were extracted (primary beam correction, continuum subtraction)
- ALMA flux scale uncertainty
- ALMA observing setup and sensitivity

## Analysis recipe

1. **Extract CO(2-1) spectra in outflow apertures**: Spectra from archival ALMA CO(2-1) in the same two r=0.8" apertures, fit with two Gaussian components  
  > "Using the same two r=$0.8\ensuremath{''}$ apertures for our H$_2$ mass calculations, we extracted spectra of the CO (2-1) emission." (5.2 Outflow Mass Comparisons of MIR to NIR and Submillimeter Measurements)
   - fitting: two-component Gaussian fit  
  > "Based on a two-component Gaussian fit, we measured line fluxes" (5.2 Outflow Mass Comparisons of MIR to NIR and Submillimeter Measurements)
   - validation: velocity offsets compared with warm H2 outflow mean velocities  
  > "These are consistent with the mean velocities measured in the warm H$_2$ outflow" (5.2 Outflow Mass Comparisons of MIR to NIR and Submillimeter Measurements)
2. **Derive cold outflow H2 mass**: Convert CO(2-1) luminosity to mass with alpha_CO  
  > "we assume a value of 0.8 $M_\odot$ (K km s$^{-1}$ pc$^2$)$^{-1}$, which is typically used for ULIRGs" (5.2 Outflow Mass Comparisons of MIR to NIR and Submillimeter Measurements)
   - assumption: alpha_CO=0.8, L'CO(2-1)/L'CO(1-0)=1  
  > "we set L$\rm{_{CO(2-1)}}$/L$\rm{_{CO(1-0)}}$ as unity." (5.2 Outflow Mass Comparisons of MIR to NIR and Submillimeter Measurements)
   - fitting: _not stated_
   - validation: alternative alpha_CO 2.1 and 0.62 tested  
  > "Setting $\alpha\rm{_{CO}}$ as 0.62 reduces our combined cold gas mass to (1.8$\pm$0.3)$\times$10$^7\;M_{\odot}$" (5.2 Outflow Mass Comparisons of MIR to NIR and Submillimeter Measurements)

## Software

- **BADASS** : MCMC multicomponent emission-line fits of JWST spaxels  
  > "BADASS performs simultaneous multicomponent fits to emission-line spectra." (Methods of Analysis)
- **JWST Calibration Pipeline** 1.12.5: reduction of JWST data  
  > "The data were processed through the standard *JWST* Calibration Pipeline (cite: Bushouse2023)." (Observations and Data Reduction)
- **CAFE/CRETA** : PAH feature fitting and grid extractions  
  > "we opted to use the Continuum And Feature Extraction (CAFE[^3], Diaz-Santos et al., *in prep.*) code" (5.4.2 Feedback on Star Formation)

## Numeric results

| quantity | value | uncertainty | units | step | quote |
|---|---|---|---|---|---|
| CO(2-1) flux, blueshifted aperture | 20.6 | 2.1 | Jy km/s | 1 | we measured line fluxes of 20.6$\pm$2.1 and 8.6$\pm$1.9 Jy km s$^{-1}$ |
| CO(2-1) flux, redshifted aperture | 8.6 | 1.9 | Jy km/s | 1 | we measured line fluxes of 20.6$\pm$2.1 and 8.6$\pm$1.9 Jy km s$^{-1}$ |
| Cold outflow mass | 2.3e7 | 0.2e7 | Msun | 2 | M$\rm{_{cold,out}}$ = (2.3$\pm$0.2)$\times$10$^7\;M_{\odot}$ |
| Warm outflow mass | 1.4e6 | 0.2e6 | Msun | 0 | $M\rm{_{warm,out}}=(1.4\pm0.2)\times10^6\;\rm{M}_{\odot}$ |

## Qualitative findings

- Warm H2 outflow from the S nucleus is collimated, with none detected from the N nucleus  
  > "We detect collimated outflowing warm H$_2$ gas originating from the southern nucleus" (abstract)

## Claim tuples

- H: How large is the warm H2 mass relative to the cold outflowing gas? | E: Compare JWST H2 masses with ALMA CO(2-1) masses in the same apertures | R: Mwarm/Mcold about 6% | F: Warm gas is a small but non-negligible fraction of the outflow mass | **supported**

## Reasoning

- Why this data: CO(2-1) has higher resolution than the CO(1-0) map  
  > "which has higher spatial resolution than the CO (1-0) map[^1] of (cite: Sakamoto2014)" (5.2 Outflow Mass Comparisons of MIR to NIR and Submillimeter Measurements)
- Why this method: _not stated_
- How they decided it was enough: _not stated_
- Limitation (authors): Cold mass rate is a lower limit due to the 0.8" aperture  
  > "our value here should be considered a lower limit due to our use of a r = $0.8\ensuremath{''}$ aperture" (5.2 Outflow Mass Comparisons of MIR to NIR and Submillimeter Measurements)
- Caveat (inferred, ours): alpha_CO uncertain by factor ~3, directly affects the warm/cold fraction
- Caveat (inferred, ours): ALMA reduction undocumented

## Reproducibility

- Data public (paper): ALMA data are archival  
  > "we opted to use archival CO (2-1) ALMA data" (5.2 Outflow Mass Comparisons of MIR to NIR and Submillimeter Measurements)
- Products in archive: _not stated_
- Missing: ALMA processing details
- Missing: exact aperture centers for CO extraction
- Data volume (inferred): ALMA CO(2-1) cube a few GB; JWST cubes a few GB
- Score (inferred): 3/5, JWST analysis is well described, but the ALMA part is only a brief comparison without processing details.
- Rediscovery candidate: no, ALMA role is minor and processing is not described.

## Links

- Method: (cite: Togi2016) (power-law H2 temperature and mass model)
- Method: (cite: Sexton2021) (BADASS fitting code)
- Companion: (cite: Sakamoto2014) (ALMA CO(1-0) outflows in NGC 3256)
- Companion: (cite: Michiyama2018) (ALMA outflow study)
- Related: GOALS
- Related: JWST ERS 1328

## Checks

```json
{
 "quotes": 34,
 "quotes_ok": 34,
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
  "facts": 61,
  "stated": 24,
  "rate": 0.393
 },
 "evidence_ok": true
}
```
