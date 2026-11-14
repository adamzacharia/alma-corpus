# Outflow of hot and cold molecular gas from the obscured secondary nucleus of NGC 3256: closing in on feedback physics

`2014A&A...572A..40E` | Astronomy and Astrophysics 2014 | first author: Emonts, B. H. C. | arXiv: 1409.4468 | DOI: 10.1051/0004-6361/201423805

Card schema 1.0 | model claude-sonnet-5-5 | depth light | type multi_facility_alma_minor

## Science

- Fields: nearby_galaxies, agn_and_quasars
- Question: Do the near-IR H2 kinematics (VLT/SINFONI) reveal a molecular outflow from the obscured secondary nucleus of NGC 3256, what are its properties, and what drives it?  
  > "In this paper, we perform a kinematic and morphological analysis of the near-IR H$_{2}$ emission from molecular gas associated with the deeply buried secondary nucleus of NGC 3256" (Introduction)
- Target **NGC 3256**: coordinates _not stated_; z/distance z=0.009354; D = 44.6 Mpc  
  > "we assume $z=0.009354$ (which is the redshift of the Br$\gamma$ peak emission at the location of the secondary nucleus) and D = 44.6 Mpc (1$''$ = 216 pc), as per (cite: piq12)." (1.1 NGC 3256); distance from as per Piqueras López et al. 2012 (cite: piq12)  
  > "we assume $z=0.009354$ (which is the redshift of the Br$\gamma$ peak emission at the location of the secondary nucleus) and D = 44.6 Mpc (1$''$ = 216 pc), as per (cite: piq12)." (1.1 NGC 3256)

## Data provenance

- ALMA projects: _none stated_
- bands: _not stated_
- frequencies and spectral setup: _not stated_
- continuum bandwidth: _not stated_
- arrays: _not stated_
- configurations: _not stated_
- baselines: _not stated_
- angular resolution: 1.2'' x 0.7'' (PA = 23 deg)  
  > "These data have a spatial resolution of $1.2'' \times 0.7''$ (PA = 23$^{\circ}$) and channel width of 10 km s$^{-1}$" (2 Data)
- max recoverable scale: _not stated_
- sensitivity: _not stated_
- time on source: _not stated_
- observing dates: _not stated_
- pi or archival as stated: Archival ALMA cycle-0 data, PI K. Sakamoto  
  > "We also used archival ALMA cycle-0 data to compare the morphology and kinematics of certain H$_{2}$ features with those observed in CO(3-2)" (2 Data)
- Line: CO J=3-2 (not stated)
- Other facility **VLT/SINFONI**: Near-IR integral-field H2 data, main dataset, from Piqueras López et al. 2012  
  > "We use near-IR data obtained with VLT/SINFONI previously presented in (cite: piq12)" (2 Data)
- Other facility **HST NICMOS2/WFPC2**: Optical/near-IR comparison images from the Hubble Legacy Archive  
  > "were extracted through the Hubble Legacy Archive." (2 Data)
- External data: High-velocity CO(3-2) maps, CO(1-0) comparison, outflow geometry and inclinations  
  > "as observed with ALMA by (cite: sak14)" (3.2 Cold molecular counterpart) [from (cite: sak14)]
- External data: Supernova rate in secondary nucleus ~0.3 SN/yr  
  > "derive a supernova-rate in the secondary nucleus of $R_{\rm SN}$ $\sim$ 0.3 SN yr$^{-1}$" (4.3 Outflow mechanism: AGN vs. starburst) [from (cite: kot96); (cite: nor95)]
- External data: X-ray luminosity of secondary nucleus L_X ~3e40 erg/s  
  > "The $0.5-10$ keV X-ray luminosity from the secondary nucleus is $L_{\rm X} \sim 3 \times 10^{40}$ erg s$^{-1}$ (cite: lir02)." (4.3 Outflow mechanism: AGN vs. starburst) [from (cite: lir02)]

## Processing

### Calibration

- pipeline or manual: Standard ALMA archival pipeline reduction  
  > "with the standard ALMA achival pipeline-reduction applied" (2 Data)
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

- ALMA CO data calibration and analysis refer to Sakamoto et al.  
  > "present these CO data (and other molecular gas tracers) using additional calibration and analysis techniques, hence we refer to their work for further details" (2 Data) [from (cite: sak14)]
- SINFONI data and distance/redshift  
  > "We use near-IR data obtained with VLT/SINFONI previously presented in (cite: piq12)" (2 Data) [from (cite: piq12)]
- Extinction from Brgamma/Brdelta following Piqueras López 2013  
  > "we calculate A$_{\rm V}$ from the Br$\gamma$/Br$\delta$ ratio in our spectra in regions A, B and C, following (cite: piq13)." (3.1.2 Mass of the hot molecular gas) [from (cite: piq13)]

### Not stated but needed to reproduce (our reading)

- ALMA CASA/pipeline version and imaging parameters (robust, cell, mask)
- How CO(3-2) high-velocity channel ranges were defined for the intensity maps
- Aperture and method for CO intensities of 23.5 and 39.7 Jy km/s
- Flux calibration details of ALMA data
- Astrometric alignment of ALMA and SINFONI

## Analysis recipe

1. **Two-component Gaussian fit of H2 lines**: IDL/MPFIT chi2 fit of narrow+broad Gaussians to H2 1-0 S(1), maps of flux, velocity, dispersion, 3-pixel boxcar smoothing  
  > "This routine was compiled for the Interactive Data Language (IDL) and uses the MPFIT package for the $\chi^{2}$ minimization (cite: mar09)." (2 Data)
   - software: IDL, MPFIT
   - fitting: No constraints on fit parameters; Monte Carlo of 500 realizations for flux errors  
  > "we construct a total of 500 independent simulations/realizations of the spectra, where the lines are again fitted." (6.1 Method)
   - validation: All fits visually inspected  
  > "No constrains were placed on the fitting parameters and all fits were visually inspected to ensure their validity." (2 Data)
2. **Excitation temperature of hot H2**: LTE level-population fits to seven H2 transitions and line-ratio diagram following Mouri 1994  
  > "we fit LTE models to the relative population levels across the range of H$_{2}$ transitions for the various components" (3.1.1 Temperature and excitation mechanism)
   - assumption: Single-temperature LTE  
  > "We therefore here adopt the temperature of T $\sim$ $1900\pm300$ K for the broad-component emission-line gas in regions A and B." (3.1.1 Temperature and excitation mechanism)
   - fitting: _not stated_
   - validation: _not stated_
3. **Hot and cold molecular gas masses**: Hot mass from 1-0S(1) intensity (Scoville 1982 formula) with A_2.2=0.1 A_V; cold mass from CO(3-2) luminosity with L'(3-2)/L'(1-0)=1 and alpha_CO=0.8  
  > "By adopting a standard conversion factor for ULIRGs of $\alpha_{\rm CO} = {\rm M}_{\rm H2}/L'_{\rm CO} = 0.8$ (cite: dow98)" (3.2 Cold molecular counterpart)
   - assumption: A_V=4.3 in regions A and B; D=44.6 Mpc; 34% of CO(3-2) in B excluded as contamination  
  > "If we assume A$_{\rm V} = 4.3$ in both region A and B, then A$_{2.2\mu \rm m} \approx 0.1 \times$ A$_{\rm V} \sim 0.43$." (3.1.2 Mass of the hot molecular gas)
   - fitting: _not stated_
   - validation: Compared with Sakamoto et al. CO(1-0) mass  
  > "the two approaches agree to a mass of at least M$_{\rm cold-H2} \sim 2$ $\times$ 10$^{7}$ M$_{\odot}$" (3.2 Cold molecular counterpart)
4. **Outflow rate, energetics and driving mechanism**: De-project velocity and radius with i_outfl~20 deg; compute mass outflow rate, kinetic energy; compare with AGN, jet and supernova energy budgets  
  > "the average mass outflow rate is Ṁ$_{\rm outfl} \sim 20$ M$_{\odot}$ yr$^{-1}$" (4.2 Detailed physical properties of the outflow)
   - assumption: Outflow perpendicular to nuclear disk, i_outfl~20 deg  
  > "If we assume that the outflow is perpendicular to the nuclear disk, this would render the molecular outflow close to the plane of the sky ($i_{\rm outfl} \sim 20^{\circ}$)." (4.1 Nature of the broad-component H2 emission)
   - fitting: _not stated_
   - validation: _not stated_

## Software

- **IDL** : Line-fitting routine  
  > "This routine was compiled for the Interactive Data Language (IDL)" (2 Data)
- **MPFIT** : chi2 minimization for Gaussian fits  
  > "uses the MPFIT package for the $\chi^{2}$ minimization (cite: mar09)" (2 Data)

## Numeric results

| quantity | value | uncertainty | units | step | quote |
|---|---|---|---|---|---|
| Hot H2 excitation temperature (broad component) | 1900 | 300 | K | 2 | T $\sim$ $1900\pm300$ K |
| Hot H2 mass, regions A+B | ~1200 | not stated | Msun | 3 | M$_{\rm hot-H_2} \sim 1200$ M$_{\odot}$. |
| Cold H2 mass, regions A+B | ~2e7 | not stated | Msun | 3 | M$_{\rm cold-H2} \sim 2$ $\times$ 10$^{7}$ M$_{\odot}$ |
| Mass outflow rate | ~20 | not stated | Msun/yr | 4 | Ṁ$_{\rm outfl} \sim 20$ M$_{\odot}$ yr$^{-1}$ |
| Outflow total kinetic energy | ~2e56 | not stated | erg | 4 | is $E_{\rm tot} \sim 2 \times 10^{56}$ erg |
| Mass loading factor | ~10 | not stated | dimensionless | 4 | the mass-loading factor could be as high as $\eta$ = Ṁ$_{\rm out}$/SFR $\sim$ 10 |
| CO(3-2) intensity region A / B | 23.5 / 39.7 | not stated | Jy km/s | 3 | We measure CO intensities of $I_{\rm CO(3-2)}$ = 23.5 and 39.7 Jy km s$^{-1}$ in region A and B |

## Qualitative findings

- Hot H2 outflow has a cold CO(3-2) counterpart with similar morphology and kinematics  
  > "The H$_{2}$ and CO show a *similar morphology and kinematics*" (3.2 Cold molecular counterpart)

## Claim tuples

- H: Is the broad H2 component a biconical molecular outflow from the secondary nucleus? | E: Two-Gaussian H2 fitting, comparison with HST and ALMA CO(3-2), geometry argument vs. disk and tidal scenarios | R: Blue/red broad components south/north of nucleus, FWZI~1200 km/s, CO counterpart | F: A kpc-scale biconical molecular outflow best explains the data | **supported**
- H: What drives the outflow? | E: Compare outflow energy with AGN, jet and supernova budgets | R: eta~10; Compton-thick AGN or starburst energetics sufficient; jet insufficient | F: Hidden Compton-thick AGN may contribute, starburst also possible | **partially**

## Reasoning

- Why this data: _not stated_
- Why this method: _not stated_
- Alternative: Edge-on rotating disk/ring rejected (Mgas/Mdyn too low, unstable); tidal features disfavored  
  > "We thus argue that a rotating disk or ring is not a likely alternative explanation" (4.1 Nature of the broad-component H2 emission)
- How they decided it was enough: _not stated_
- Limitation (authors): Cold mass and outflow rate are lower limits; H2 excitation more complex than single-T LTE  
  > "This value for Ṁ$_{\rm outfl}$ is likely a lower limit" (4.2 Detailed physical properties of the outflow)
- Caveat (inferred, ours): ALMA used only through a figure and CO intensities; details deferred to Sakamoto et al.
- Caveat (inferred, ours): Mass and energetics depend on assumed inclination, alpha_CO and extinction

## Reproducibility

- Data public (paper): Archival ALMA cycle-0 data  
  > "We also used archival ALMA cycle-0 data" (2 Data)
- Products in archive: _not stated_
- Missing: ALMA CO(3-2) imaging parameters and moment definitions
- Missing: SINFONI reduced cubes from earlier paper
- Data volume (inferred): ~10 GB ALMA plus SINFONI cube
- Score (inferred): 3/5, Main results are SINFONI-based and ALMA part is deferred to another paper.
- Rediscovery candidate: no, ALMA recipe incomplete and the main analysis relies on VLT data.

## Links

- Method: (cite: piq12) (SINFONI data and fitting routine)
- Companion: (cite: sak14) (ALMA CO data and outflow analysis)

## Checks

```json
{
 "quotes": 41,
 "quotes_ok": 41,
 "quote_pass_rate": 1.0,
 "quotes_too_long": 0,
 "unsupported_facts": 0,
 "project_codes": 0,
 "codes_not_in_text": [],
 "codes_not_in_obscore": [],
 "obscore_codes_not_in_card": [
  "2011.0.00525.S"
 ],
 "codes_printed_but_missing": [],
 "numeric_results": 7,
 "numeric_problems": 0,
 "fill": {
  "facts": 71,
  "stated": 30,
  "rate": 0.423
 },
 "evidence_ok": true
}
```
