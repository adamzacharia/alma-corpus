# A Dwarf Transitional Protoplanetary Disk around XZ Tau B

`2016ApJ...825L..10O` | The Astrophysical Journal Letters 2016 | first author: Osorio, Mayra | arXiv: 1606.03118 | DOI: 10.3847/2041-8205/825/1/L10

Card schema 1.0 | model claude-sonnet-5-5 | depth full | type archival_reuse

## Science

- Fields: protoplanetary_disks
- Question: Is the 1.3 mm continuum source XZ Tau B a resolved, very small transitional disk with a central cavity, and what are its properties?  
  > "Here we present a detailed analysis of the 1.3 mm continuum observations that angularly resolve the source." (Introduction)
- Target **XZ Tau B**: coordinates not stated (~24'' from the HL Tau phase center, ~0.3'' NW of XZ Tau A/C)  
  > "XZ Tau B is a young M2 dwarf star (see stellar properties in Table 1) in the L1551 molecular cloud." (Introduction); "Distance (pc) | 140 | Adopted | 1" (Table 1); z/distance 140 pc  
  > "XZ Tau B is a young M2 dwarf star (see stellar properties in Table 1) in the L1551 molecular cloud." (Introduction); "Distance (pc) | 140 | Adopted | 1" (Table 1); distance from Torres et al. 2009  
  > "XZ Tau B is a young M2 dwarf star (see stellar properties in Table 1) in the L1551 molecular cloud." (Introduction); "Distance (pc) | 140 | Adopted | 1" (Table 1)

## Data provenance

- ALMA projects: 2011.0.00015.SV
- bands: 1.3 mm and 2.9 mm  
  > "was observed at 2.9 mm and 1.3 mm" (Introduction)
- frequencies and spectral setup: 1.3 mm: 4 spectral windows of 2000 MHz, 128 channels each; 2.9 mm: continuum plus HCO+(1-0), HCN(1-0), CO(1-0), CN(1-0)  
  > "configured in 4 spectral windows of 2000 MHz and 128 channels each" (Observations)
- continuum bandwidth: _not stated_
- arrays: _not stated_
- configurations: _not stated_
- baselines: 12 to 15,240 m, 42 antennas  
  > "using 42 antennas of ALMA, with baselines from 12 to 15,240 m" (Observations)
- angular resolution: _not stated_
- max recoverable scale: _not stated_
- sensitivity: _not stated_
- time on source: _not stated_
- observing dates: Campaign 2014 Oct 14 - Nov 14; 1.3 mm data 2014 Oct 24-31  
  > "The 1.3 mm data were obtained from 2014 October 24 to 31" (Observations)
- pi or archival as stated: _not stated_
- Line: HCO+ 1-0 (not stated)
- Other facility **Spitzer, WISE, Akari, IRAS**: photometry and spectroscopy for the SED  
  > "we compiled photometric and spectroscopic data from the Spitzer, WISE, Akari, and IRAS databases" (Modeling)
- External data: 2.9 mm continuum image/flux density 1.83±0.12 mJy  
  > "with a flux density of $1.83\pm0.12$ mJy (AP2015a; Zapata et al. 2015)" (Observations) [from ALMA Partnership et al. 2015a (cite: 2015ApJ...808L...3A)]
- External data: Stellar parameters (distance, extinction, spectral type, age, Teff, mass)  
  > "Table notes: (1) Torres et al. 2009; (2) Hartigan & Kenyon 2003" (Table 1) [from Torres et al. 2009; Hartigan & Kenyon 2003]

## Processing

### Calibration

- pipeline or manual: _not stated_
- casa version: CASA 4.2.2 (imaging)  
  > "Images at 1.3 mm were obtained with the task *clean* of CASA (version 4.2.2)." (Observations)
- pipeline version: _not stated_
- archive products used as is: _not stated_
- flux calibrator: _not stated_
- flux scale uncertainty: 5% absolute flux calibration  
  > "the absolute flux density calibration uncertainty (5%)" (Observations)
- self calibration: not applied; it blurred XZ Tau images  
  > "Since we are interested in XZ Tau, we did not apply self-calibration in our final images." (Observations)

### Imaging

- task: CASA clean  
  > "Images at 1.3 mm were obtained with the task *clean* of CASA (version 4.2.2)." (Observations)
- deconvolver: _not stated_
- weighting robust: natural weighting (flux image)  
  > "Measured in a natural-weight image" (Footnote 1)
- uv taper: _not stated_
- cell size: _not stated_
- image size: _not stated_
- masking: _not stated_
- multiscale scales: _not stated_
- continuum subtraction: _not stated_
- line free channels: _not stated_
- primary beam correction: applied; response at XZ Tau only 1/19 (~24'' off-center, FWHM ~27'')  
  > "where the response of the primary beam (FWHM $\simeq27''$ at 1.3 mm) is only 1/19" (Observations)
- array combination: _not stated_
- smoothing: _not stated_
- final beam: _not stated_
- final rms: _not stated_

### Inherited from earlier work

- Observational setup and calibration  
  > "A description of the observational setup and the calibration process is given in AP2015a, AP2015b." (Observations) [from AP2015a, AP2015b]
- Flux uncertainty calculation  
  > "Uncertainties in flux densities have been calculated as in AP2015a" (Observations) [from AP2015a; Dzib et al. (2014)]
- Hydrodynamical simulations method  
  > "we have carried out gas-dust two fluid hydrodynamical simulations as in Zhu et al. (2012)" (Modeling) [from Zhu et al. (2012)]
- Dust grain mixture composition  
  > "The grain mixture composition is the same as in Osorio et al. (2014)" (Modeling) [from Osorio et al. (2014)]

### Not stated but needed to reproduce (our reading)

- clean parameters (robust/weighting for the images, cell, image size, masks, threshold)
- how HL Tau was cleaned and subtracted
- uv-range and visibility recentering/binning details for Fig 1b
- fitting statistic and criteria for the SED and radial-profile fit
- model grid values
- flux calibrator
- pipeline vs manual calibration

## Analysis recipe

1. **Image the 1.3 mm continuum**: Clean HL Tau and subtract it from the uv data, then clean the XZ Tau field and apply primary beam correction; no self-calibration  
  > "we first cleaned the HL Tau emission and subtracted it from the uv data." (Observations)
   - software: CASA
   - fitting: _not stated_
   - validation: bandwidth and time smearing estimated negligible (0.0016'' and 0.0035'')  
  > "the expected bandwidth and time smearing are negligible at the position of XZ Tau" (Observations)
2. **Detect the central cavity via visibility profile**: Real part of the visibility profile; null at 5-8 Mlambda gives hole radius ~1 au  
  > "The null falls around 5-8 M$\lambda$, corresponding to hole radii of 0.6-0.9 au to 1.4-2.2 au" (Observations)
   - assumption: visibilities recentered but not deprojected  
  > "Visibilities have been recentered on XZ Tau B, but not deprojected to account for the disk inclination." (Footnote 2)
   - fitting: _not stated_
   - validation: consistent with SED and image modeling  
  > "we estimate a radius of the hole $\sim$1 au, consistent with the value obtained from our modeling of the SED and image ($\S3$)" (Observations)
3. **Model SED and radial intensity profile**: Irradiated alpha-accretion disk models with dust settling and cavity wall; grid of 40 models; chose highest allowed viscosity  
  > "We have run a grid of 40 models with parameters in the above-mentioned ranges." (Modeling)
   - software: CASA
   - parameter: epsilon explored 0.001-0.1; Mdot_disk between Mdot_* and 10 Mdot_*  
  > "we explored values of $\dot M_{\rm disk}$ in the range $\dot M_*<\dot M_{\rm disk}<10\,\dot M_*$" (Modeling)
   - assumption: dust-to-gas ratio 0.0085; grains up to 1 mm in the midplane  
  > "resulting in a dust-to-gas ratio of 0.0085" (Modeling)
   - assumption: initial inclination 47 deg from orbital plane  
  > "the B and A/C orbital plane ($i=47^\circ$; Carrasco-González et al. in preparation)" (Modeling)
   - fitting: grid of models compared by eye to SED and normalized intensity profile  
  > "modeling and fitting the observed SED and the normalized radial intensity profile of the 1.3 mm image" (Modeling)
   - validation: CASA simulated image of the model compared with observation  
  > "Figure 3d shows a CASA simulated image of the model emission at 1.3 mm" (Modeling)
4. **Hydrodynamic simulations of planet-opened cavity**: Gas-dust two-fluid simulations for alpha=1e-2 and 1e-3  
  > "multiple planets could account for the observed cavity in XZ Tau B as long as the viscosity is small enough ($\alpha\le10^{-3}$)." (Modeling)
   - fitting: _not stated_
   - validation: _not stated_

## Software

- **CASA** 4.2.2: clean imaging and simulated model image  
  > "Images at 1.3 mm were obtained with the task *clean* of CASA (version 4.2.2)." (Observations)

## Numeric results

| quantity | value | uncertainty | units | step | quote |
|---|---|---|---|---|---|
| 1.3 mm flux density | 7 | 2 | mJy | 1 | a size of $\sim0.05''$ and a flux density of $7\pm2$ mJy |
| Disk outer radius | 3.4 | 0.1 | au | 3 | Outer Radius (au) / 3.4$\pm$0.1 / Fitted |
| Cavity (inner) radius | 1.30 | 0.05 | au | 3 | Inner Radius (au) / 1.30$\pm$0.05 / Fitted |
| Disk total mass | 9 | not stated | M_J | 3 | Total Mass ($M_J$) / 9 / Calculated |
| Disk mass accretion rate | 7.0e-8 | not stated | Msun/yr | 3 | Mass Accretion Rate ($M_{\odot}$ yr$^{-1}$) / 7.0$\times$10$^{-8}$ / Fitted |
| Dust mass | 25 | not stated | M_earth | 3 | Dust Mass ($M_\oplus$) / 25 / Calculated |

## Qualitative findings

- The SE side is ~30% brighter than the NW, suggesting a possible dust trap, needing confirmation  
  > "with the flux density in the southeast region $\sim30\%$ higher than in the northwest one" (Discussion)

## Claim tuples

- H: XZ Tau B hosts a resolved, small transitional disk | E: 1.3 mm imaging, visibility profile, SED and profile modeling | R: Size ~0.05'', visibility null at 5-8 Mlambda, model cavity 1.3 au and outer radius 3.4 au | F: A dwarf transitional disk with a central cavity | **supported**
- H: The cavity can be created by planets | E: Two-fluid hydro simulations | R: ~0.1 M_J planets open a deep cavity if alpha<=1e-3 | F: Compact planetary system plausible | **partially**

## Reasoning

- Why this data: _not stated_
- Why this method: _not stated_
- Alternative: Disk size smaller than tidal truncation; eccentric orbit disfavored by >20 yr of relative positions  
  > "the analysis of the relative positions of the stars over $>$20 yr favors a nearly circular orbit" (Discussion)
- How they decided it was enough: _not stated_
- Limitation (authors): Gas disk size unconstrained; asymmetry needs higher-sensitivity data  
  > "Unfortunately, the sensitivity of our line observations is insufficient to set a tight constraint to the gas disk size." (Discussion)
- Caveat (inferred, ours): The source lies far off-axis (primary beam 1/19), so the flux and image fidelity are uncertain
- Caveat (inferred, ours): Marginal resolution (~0.05'') with no formal fit uncertainties
- Caveat (inferred, ours): Model degeneracies; the choice of highest viscosity is assumed
- Caveat (inferred, ours): No self-calibration; the HL Tau subtraction could leave residuals

## Reproducibility

- Data public (paper): ALMA Science Verification data, project 2011.0.00015.SV  
  > "This paper makes use of the following ALMA data: ADS/JAO.ALMA#2011.0.00015.SV." (Acknowledgments)
- Products in archive: _not stated_
- Missing: clean parameters
- Missing: D'Alessio disk model code and updated version
- Missing: fit criteria
- Data volume (inferred): ~100s of GB (long-baseline SV band 6 dataset)
- Score (inferred): 3/5, Public data, but imaging parameters and the modeling code and fit procedure are sparse.
- Rediscovery candidate: no, Imaging recipe incomplete and the modeling uses a non-public code.

## Links

- Method: D'Alessio et al. 2006 (cite: 2006ApJ...638..314D) (disk model)
- Method: Zhu et al. 2012 (cite: 2012ApJ...755....6Z) (hydro simulations)
- Companion: ALMA Partnership et al. 2015a (cite: 2015ApJ...808L...3A) (HL Tau campaign data and 2.9 mm image)
- Related: ALMA Long Baseline Campaign Science Verification (HL Tau)

## Checks

```json
{
 "quotes": 53,
 "quotes_ok": 53,
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
  "facts": 70,
  "stated": 38,
  "rate": 0.543
 },
 "evidence_ok": true
}
```
