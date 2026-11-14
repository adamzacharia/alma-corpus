# Suppression of Star Formation in NGC 1266

`2015ApJ...798...31A` | The Astrophysical Journal 2015 | first author: Alatalo, Katherine | arXiv: 1410.4556 | DOI: 10.1088/0004-637X/798/1/31

Card schema 1.0 | model claude-sonnet-5-5 | depth full | type observational_alma_primary

## Science

- Fields: nearby_galaxies, agn_and_quasars
- Question: Is star formation in the dense molecular gas of NGC 1266 suppressed by the AGN-driven outflow, and how much?  
  > "In order to make a detailed study the of suppression of SF in an AGN of moderate luminosity, we used the Atacama Large Millimeter Array (ALMA)" (1 Introduction)
- Target **NGC 1266**: coordinates _not stated_; z/distance 29.9 Mpc  
  > "The distance to NGC 1266 is taken from ATLAS$^{\rm 3D}$ (cite: cappellari+11) to be 29.9 Mpc, for which 1$''$ = 145 pc." (1 Introduction); distance from ATLAS3D (cappellari+11)  
  > "The distance to NGC 1266 is taken from ATLAS$^{\rm 3D}$ (cite: cappellari+11) to be 29.9 Mpc, for which 1$''$ = 145 pc." (1 Introduction)

## Data provenance

- ALMA projects: 2011.0.00511.S
- bands: Band 7 (870 um continuum), Band 6 (H13CN), also Band 3 continuum  
  > "ALMA | Band 3 | 3476" (Table 1)
- frequencies and spectral setup: _not stated_
- continuum bandwidth: _not stated_
- arrays: _not stated_
- configurations: extended Cycle 0 configuration  
  > "The ALMA observations of NGC 1266 were made in the extended Cycle 0 configuration" (2.2 ALMA observations)
- baselines: _not stated_
- angular resolution: natural 0.51x0.47 arcsec; uniform 0.49x0.36 arcsec (870 um)  
  > "Both naturally-weighted (with a $0.51^{''} \times 0.47^{''}$ beam) and uniformly-weighted (with a $0.49^{''} \times 0.36^{''}$ beam) images were made." (2.2 ALMA observations)
- max recoverable scale: _not stated_
- sensitivity: _not stated_
- time on source: _not stated_
- observing dates: _not stated_
- pi or archival as stated: _not stated_
- Line: H13CN J=3-2 (259.0118 GHz)
- Other facility **CARMA**: CS(2-1) and HCN(1-0) dense gas maps  
  > "CARMA was used to map the J=2–1 transition of carbon monosulphide (CS) and J=1–0 transition of hydrogen cyanide (HCN)." (1 Introduction)
- Other facility **XMM-Newton and Chandra**: X-ray spectra of the nucleus  
  > "NGC 1266 was observed for 29.65 ks on 2009 September 20 (ObsID 11578)" (2.3)
- External data: VLBA radio point source and VLA fluxes  
  > "Radio fluxes from the Very Large Array (VLA), described in (cite: nyland+13) were also derived using the $15''$ aperture." (3.2) [from (cite: nyland+13)]
- External data: Original CO outflow mass 2.4e7 Msun, rate 13 Msun/yr, I_CO=45.4 Jy km/s  
  > "the original estimate of the molecular outflow mass, $M_{\rm out} = 2.4\times10^7~M_\odot$ (cite: alatalo+11), is too low" (4) [from (cite: alatalo+11)]

## Processing

### Calibration

- pipeline or manual: standard ALMA Cycle 0 reduction CASA script run by ALMA staff  
  > "processed through the standard ALMA Cycle 0 reduction CASA[^1] script by ALMA staff" (2.2 ALMA observations)
- casa version: _not stated_
- pipeline version: _not stated_
- archive products used as is: calibrated measurement set product used  
  > "We used the calibrated measurement set product to image the continuum at 344.7 GHz" (2.2 ALMA observations)
- flux calibrator: _not stated_
- flux scale uncertainty: _not stated_
- self calibration: single iteration phase-only for continuum; none for H13CN cube  
  > "A single iteration of self-calibration in phase only was applied to the dataset." (2.2 ALMA observations)

### Imaging

- task: _not stated_
- deconvolver: _not stated_
- weighting robust: natural and uniform weighting  
  > "Both naturally-weighted (with a $0.51^{''} \times 0.47^{''}$ beam) and uniformly-weighted" (2.2 ALMA observations)
- uv taper: _not stated_
- cell size: _not stated_
- image size: _not stated_
- masking: _not stated_
- multiscale scales: _not stated_
- continuum subtraction: continuum imaged excluding bright molecular lines  
  > "excluding any bright molecular lines" (2.2 ALMA observations)
- line free channels: _not stated_
- primary beam correction: _not stated_
- array combination: _not stated_
- smoothing: H13CN cube natural weighting, channel width 2.44 MHz (3.34 km/s)  
  > "imaged the datacube using natural weighting and a channel width of 2.44 MHz (3.34 km s$^{-1}$)" (2.2 ALMA observations)
- final beam: _not stated_
- final rms: _not stated_

### Inherited from earlier work

- CARMA data reduction  
  > "The data were reduced as described in (cite: alatalo+13)." (2.1 CARMA observations) [from (cite: alatalo+13)]

### Not stated but needed to reproduce (our reading)

- tclean/clean parameters (cell, image size, masks, threshold, CASA version)
- line-free channel selection for continuum
- identity of the other ALMA execution blocks/bands and frequencies for lower-frequency continuum
- flux calibrator and flux scale uncertainty
- SED fit details and free-free/synchrotron fit priors
- imfit region and aperture specifics

## Analysis recipe

1. **Measure 870um continuum flux and decompose compact/diffuse**: Naturally weighted image; CASA imfit of central source with zero-point offset; aperture 4.0 arcsec using CS moment0 region  
  > "used the CASA imfit task to fit the central source (allowing a zero-point offset to account for the diffuse emission)" (2.2 ALMA observations)
   - software: CASA
   - fitting: _not stated_
   - validation: simdata/simanalyse of CARMA CS map recovered 70% flux; diffuse flux corrected upward by 30%  
  > "The simulation recovered 70% of the flux in the CS(2–1) image." (2.2 ALMA observations)
2. **Dense gas surface density from CS, HCN and H13CN**: Optically thin LTE masses at Tex=90 K; virial mass from H13CN size  
  > "we assumed that the CS gas is optically thin and in local thermal equilibrium (LTE) with an excitation temperature of 90 K" (2.1 CARMA observations)
   - assumption: CS abundance ~1e-9; HCN abundance 1e-8  
  > "we assumed a HCN to H$_2$ abundance of 10$^{-8}$" (2.1 CARMA observations)
   - fitting: _not stated_
   - validation: compared with Lada+94 CS-to-H2 relation and CO-derived value  
  > "The gas column was also calculated to be $1.13\times10^4$ M$_\odot$ pc$^{-1}$" (2.1 CARMA observations)
3. **Estimate SFR from free-free emission**: Fit synchrotron plus free-free power-law model to ALMA and VLA continuum; Murphy+12 eq. 6  
  > "Using the standard relation between SFR and free-free emission (equation 6 in (cite: murphy+12)), we derived a SFR of 0.87$\pm 0.1$ $M_\odot$ yr$^{-1}$." (3.3)
   - fitting: power-law synchrotron + free-free; sampler not stated  
  > "Continuum emission was measured at 86.3 GHz, 217.2 GHz, 257.6 GHz, and 301.8 GHz with ALMA and 1.4 GHz, 5 GHz and 33 GHz with the VLA and fit to a model consisting of power-law synchrotron and free-free components." (Star formation rate derived from millimeter free-free emission)
   - validation: compared with PAH+UV lower limit and [Ne II] and total IR upper limits  
  > "The \[Ne ii\] and \[Ne iii\] emission from the nucleus of NGC 1266 (cite: dudik+09) indicates a SFR of $\approx 1.5$" (3.2)
4. **Revise outflow mass and rate**: Apply ULIRG alpha_CO ~ 1 to original CO wing flux  
  > "with $\alpha_{\rm CO} \approx 1$ using $M_{\rm mol} = \alpha_{\rm CO} L_{\rm CO}$" (4)
   - fitting: _not stated_
   - validation: _not stated_
5. **Compare Sigma_SFR vs Sigma_gas to K-S relation and test turbulence support**: Toomre Q, free-fall velocity and turbulent dissipation estimates  
  > "Using the parameters above, $Q\approx0.4$" (6.1)
   - fitting: _not stated_
   - validation: _not stated_

## Software

- **CASA** : imaging, imfit, simdata/simanalyse  
  > "we used the simdata and simanalyse tasks in CASA" (2.2 ALMA observations)
- **CIAO sherpa** CIAO 4.5: X-ray spectral fitting  
  > "Spectral modeling was done using the sherpa packages of ciao" (2.3)
- **PAHFIT** : fit Spitzer IRS PAH spectrum  
  > "The *Spitzer* Infrared Spectrograph (IRS; (cite: spitzer_irs)) spectrum was fitted using PAHFIT" (3.1)

## Numeric results

| quantity | value | uncertainty | units | step | quote |
|---|---|---|---|---|---|
| 870um integrated flux density (4.0 arcsec aperture) | 32.6 | 0.1 | mJy | 1 | We found an integrated flux density of 32.6$\pm 0.1$ mJy up to an aperture of 4.0$''$ diameter |
| SFR from free-free | 0.87 | 0.1 (factor of ~2 overall) | Msun/yr | 3 | we derived a SFR of 0.87$\pm 0.1$ $M_\odot$ yr$^{-1}$ |
| Molecular outflow rate | 110 | not stated | Msun/yr | 4 | This also up-converts the molecular mass outflow rate, $\dot{M}_{\rm out}$ to $110~M_\odot$ yr$^{-1}$. |
| Escape rate | 2 | not stated | Msun/yr | 4 | ($\dot{M}_{\rm esc}\approx 2~M_\odot$ yr$^{-1}$) |
| Toomre Q | 0.4 | not stated | dimensionless | 5 | Using the parameters above, $Q\approx0.4$ |

## Qualitative findings

- Dense gas kinematics do not match a rotating disk; turbulence injected by the outflow plausibly suppresses SF  
  > "Figure [10](#fig:cs) demonstrates that there is a severe kinematic mismatch between the stellar kinematics and the dense gas kinematics" (6.1)

## Claim tuples

- H: SF in the dense gas is suppressed relative to the K-S relation | E: Compare SFR surface density from free-free with CS-derived gas surface density | R: Suppressed by at least a factor of 50 (Scenario 1) or 150 in outskirts (Scenario 2) | F: SF in the majority of dense gas is suppressed by 50-150 | **supported**
- H: The outflow is larger than previously thought | E: Dense gas line wings and updated alpha_CO | R: Mout rate 110 Msun/yr, only 2 Msun/yr escapes | F: Most outflowing gas falls back | **supported**
- H: Turbulence from the outflow suppresses SF | E: Energetic and timescale estimates | R: Dissipation 1.3e41 erg/s can power warm H2 | F: Turbulent injection is a reasonable explanation | **partially**

## Reasoning

- Why this data: _not stated_
- Why this method: _not stated_
- Alternative: Photon momentum driving of outflow rejected (zeta ~65)  
  > "Therefore, this molecular outflow likely cannot be driven by photons, no matter the source" (4)
- How they decided it was enough: _not stated_
- Limitation (authors): Cannot distinguish AGN from ultra-compact starburst  
  > "they are not able to definitively identify the source of the radiation" (5.3)
- Caveat (inferred, ours): Surface densities rest on assumed abundances and Tex
- Caveat (inferred, ours): alpha_CO choice drives outflow rate
- Caveat (inferred, ours): Many assumptions in SFR limits

## Reproducibility

- Data public (paper): ALMA project cited; public availability not explicitly stated  
  > "This paper makes use of the following ALMA data: ADS/JAO.ALMA#2011.0.00511.S." (Acknowledgments)
- Products in archive: _not stated_
- Missing: imaging parameters
- Missing: other band frequencies/execution blocks
- Missing: CARMA data reduction details
- Missing: SED fit specifics
- Data volume (inferred): ~10-50 GB (Cycle 0 Bands 3,6,7)
- Score (inferred): 3/5, ALMA part is modest and imaging details are sparse; many results use external and literature numbers.
- Rediscovery candidate: no, Key results depend on CARMA, X-ray and literature inputs and unstated parameters.

## Links

- Companion: (cite: alatalo+11) (Original molecular outflow discovery)
- Companion: (cite: nyland+13) (VLBA and VLA radio data)
- Related: ATLAS3D

## Checks

```json
{
 "quotes": 45,
 "quotes_ok": 45,
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
  "stated": 34,
  "rate": 0.486
 },
 "evidence_ok": true
}
```
