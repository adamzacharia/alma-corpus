# First M87 Event Horizon Telescope Results. IV. Imaging the Central Supermassive Black Hole

`2019ApJ...875L...4E` | The Astrophysical Journal Letters 2019 | first author: Event Horizon Telescope Collaboration | arXiv: 1906.11241 | DOI: 10.3847/2041-8213/ab0e85

Card schema 1.0 | model claude-sonnet-5-5 | depth light | type multi_facility_alma_minor

## Science

- Fields: agn_and_quasars, nearby_galaxies
- Question: What does the 1.3 mm EHT 2017 data of M87 look like when imaged, and how robust are the ring diameter and asymmetry to the imaging method and parameters?  
  > "We describe the EHT imaging procedures, the primary image features in M87, and the dependence of these features on imaging assumptions." (abstract)
- Target **M87**: coordinates decl. +12°23′28″ (J2000)  
  > "M87 (J2000 decl. of +12°23′28″)" (1. Introduction); "( _D_ = 16.8 Mpc; Blakeslee et al. 2009; Bird et al. 2010; Cantiello et al. 2018" (1. Introduction); z/distance D = 16.8 Mpc  
  > "M87 (J2000 decl. of +12°23′28″)" (1. Introduction); "( _D_ = 16.8 Mpc; Blakeslee et al. 2009; Bird et al. 2010; Cantiello et al. 2018" (1. Introduction); distance from Blakeslee et al. 2009; Bird et al. 2010; Cantiello et al. 2018  
  > "M87 (J2000 decl. of +12°23′28″)" (1. Introduction); "( _D_ = 16.8 Mpc; Blakeslee et al. 2009; Bird et al. 2010; Cantiello et al. 2018" (1. Introduction)
- Target **3C 279**: coordinates _not stated_; z/distance _not stated_; distance from _not stated_

## Data provenance

- ALMA projects: 2016.1.01154.V
- bands: 1.3 mm (two 2 GHz bands centered on 227.1 and 229.1 GHz)  
  > "All sites recorded two 2 GHz bands centered on 227.1 and 229.1 GHz (henceforth, low and high band, respectively)." (3.1 EHT Observations and Data)
- frequencies and spectral setup: _not stated_
- continuum bandwidth: _not stated_
- arrays: Phased ALMA (37 antennas as a 73 m telescope) as one station of the EHT VLBI array  
  > "37 telescopes of the Atacama Large Millimeter/submillimeter Array (ALMA) coherently combined to act as a single 73 m diameter telescope" (1. Introduction)
- configurations: _not stated_
- baselines: _not stated_
- angular resolution: ~20 μas (minimum fringe spacing 24.8 μas)  
  > "Minimum Fringe Spacing 1 ∣∣ _**u**_ max (All Baselines) April 5–11 24.8" (Table 1)
- max recoverable scale: _not stated_
- sensitivity: _not stated_
- time on source: _not stated_
- observing dates: 2017 April 5, 6, 10, 11  
  > "The EHT observed M87 with seven stations at five geographic sites on 2017 April 5, 6, 10, and 11." (3.1 EHT Observations and Data)
- pi or archival as stated: _not stated_
- Other facility **EHT stations (APEX, JCMT, SMA, SMT, PV, LMT, SPT)**: VLBI baselines at 1.3 mm; ALMA gives the sensitive baselines  
  > "The addition of baselines to ALMA significantly increases the sensitivity of the entire EHT array." (3.1 EHT Observations and Data)
- Other facility **EAVN and KVN**: 22–129 GHz quasi-simultaneous VLBI flux densities for compact flux constraint  
  > "M87 at 22 and 43 GHz with the East Asian VLBI Network" (B.2)
- External data: Calibration, correlation and reduction of EHT 2017 data  
  > "details of the 2017 observations, correlation, and calibration are given in EHT Collaboration et al. (2019c, hereafter Paper III)." (1. Introduction) [from EHT Collaboration et al. 2019c (Paper III)]
- External data: GMVA 86 GHz compact flux densities 2004–2015  
  > "around the peak of the GMVA images from 2004 to 2015, but excluding the 2009" (Section 4 (86 GHz compact flux density)) [from Kim et al. 2018a]
- Simulation/model as data: Synthetic data from four geometric models (ring, crescent, disk, double) plus jet, and a GRMHD snapshot, generated with eht-imaging  
  > "We generated synthetic data from each image using the eht-imaging software library." (6.1 Synthetic Source Models and Data)

## Processing

### Calibration

- pipeline or manual: EHT–Haystack HOPS pipeline (Paper III); a priori plus network calibration  
  > "Haystack Observatory Processing System (HOPS) pipeline" (3.1. EHT Observations and Data)
- casa version: _not stated_
- pipeline version: _not stated_
- archive products used as is: _not stated_
- flux calibrator: _not stated_
- flux scale uncertainty: _not stated_
- self calibration: Iterative imaging and self-calibration in all pipelines  
  > "require multiple consecutive iterations of CLEAN followed by self-calibration" (2.2.1)

### Imaging

- task: DIFMAP CLEAN scripted; eht-imaging and SMILI RML  
  > "we designed scripted imaging pipelines in three software packages: DIFMAP, eht-imaging, and SMILI." (6.2 Imaging Pipelines and Parameter Survey Space)
- deconvolver: _not stated_
- weighting robust: Uniform (u,v) weighting, scaled by σ^κ, κ=0,−1,−2 surveyed  
  > "A uniform (u, v) density weighting function is used for gridding the visibilities." (6.2.1 DIFMAP)
- uv taper: _not stated_
- cell size: _not stated_
- image size: _not stated_
- masking: Disk-shaped CLEAN windows, diameters 40–100 μas tested  
  > "different diameters from 40 to 100 μas were tested in the parameter search" (6.2.1 DIFMAP)
- multiscale scales: _not stated_
- continuum subtraction: _not stated_
- line free channels: _not stated_
- primary beam correction: _not stated_
- array combination: _not stated_
- smoothing: _not stated_
- final beam: Circular 20 μas Gaussian restoring beam for CLEAN  
  > "we adopt a circular Gaussian restoring beam with 20 μas FWHM for all CLEAN reconstructions." (Table 1)
- final rms: _not stated_

### Inherited from earlier work

- Data reduction pipeline, calibration and validation of EHT 2017 data  
  > "Paper III outlines the correlation, calibration, and validation of these data." (3.1 EHT Observations and Data) [from Paper III (EHT Collaboration et al. 2019c)]
- Distance and black-hole mass translation of the ring diameter  
  > "We perform this analysis separately, in Paper VI." (9.3 Results for M87) [from Paper VI (EHT Collaboration et al. 2019e)]

### Not stated but needed to reproduce (our reading)

- Exact script parameters and random seeds for the DIFMAP, eht-imaging and SMILI pipelines (scripts are only on the EHT data portal)
- ALMA-specific phasing and calibration details (in Paper III and Matthews et al. 2018)
- Software versions for DIFMAP and SMILI

## Analysis recipe

1. **Estimate compact flux density**: Constraints from LMT–SMT amplitudes, crossing-track gain correction and multi-wavelength VLBI extrapolation  
  > "Taken together, the EHT constraints give _F_ cpct = 0.64" (B.1)
   - fitting: _not stated_
   - validation: _not stated_
2. **Blind imaging by four teams**: Four teams imaged April 11 data independently (two RML, two CLEAN)  
  > "Teams 1 and 2 focused on RML methods, while Teams 3 and 4 primarily used CLEAN." (5.1 Imaging Procedure and Team Structure)
   - software: DIFMAP, eht-imaging, SMILI
   - fitting: _not stated_
   - validation: Blind comparison with normalized cross-correlation  
  > "After ensuring image consistency through a variety of blind metrics (including normalized cross-correlation, Equation (15))" (5.2 First M87 Imaging Results)
3. **Parameter surveys on synthetic data to select fiducial parameters**: Grid surveys of imaging parameters; Top Set requires χ²<2 on M87 and α_char below nominal resolution on synthetic data  
  > "the Top Set includes all imaging parameter combinations with _a_ char < 1 ∣∣ _**u**_ max" (6.3.1)
   - software: DIFMAP, eht-imaging, SMILI
   - fitting: _not stated_
   - validation: Cross-validation withholding one geometric model; GRMHD test  
  > "we repeat the parameter selection process after withholding a specified geometric source model from the training set" (6.3.2)
4. **Measure ring parameters**: Ring center from minimizing radial peak dispersion; diameter, width, orientation, asymmetry, central brightness  
  > "The measured diameter d is then twice _r_ ¯ pk measured from the identified center" (9.1 Ring Parameter Definitions)
   - fitting: _not stated_
   - validation: Tests on crescent and GRMHD synthetic reconstructions  
  > "We tested the analysis methods described in Section 9.1 on synthetic data from a crescent model" (9.2)

## Software

- **DIFMAP** : CLEAN imaging and self-calibration  
  > "For the CLEAN imaging in this Letter, we used the DIFMAP software" (2.2.1)
- **eht-imaging** v1.1.0: RML imaging and synthetic data generation  
  > "eht-imaging: v1.1.0: Imaging interferometric data with regularized maximum likelihood" (References)
- **SMILI** : RML imaging with sparsity regularizers  
  > "we used two open-source software libraries that have been developed specifically for the EHT" (2.2.2)
- **MeqSilhouette+rPICARD** : Independent synthetic data generation and CASA-based calibration check  
  > "we compared our generated synthetic data and reconstructed images to results from another VLBI data simulator, MeqSilhouette+rPICARD" (6.1)
- **PolConvert** : Convert ALMA linear to circular basis  
  > "ALMA recorded dual linear polarization that was later converted to a circular basis via PolConvert" (3.1)

## Numeric results

| quantity | value | uncertainty | units | step | quote |
|---|---|---|---|---|---|
| Total compact flux density (EHT + multi-wavelength) | 0.66 | +0.16/−0.10 | Jy | 1 | Combining them, we obtain _F_ cpct,230 = 0.66 -+ 0.100.16 Jy . |
| Image dynamic range | ~50 | not stated | dimensionless | 3 | these variations indicate that our images achieve a dynamic range of ∼50 |

## Qualitative findings

- Ring is persistent across four days and all methods, brighter in the south; some day-to-day evolution but not tied to a specific feature  
  > "we cannot unambiguously associate the variability with evolution of a specific image feature." (10. Summary and Conclusions)

## Claim tuples

- H: Does the M87 image show a ring robust to imaging method? | E: Blind four-team imaging plus scripted pipelines on three software packages | R: All images show ~40 μas asymmetric ring brighter in south | F: Ring diameter and asymmetry are stable against imaging choices | **supported**
- H: Are LMT gain corrections imaging artifacts? | E: Compare residual gains from M87 and 3C 279 images | R: Gain trends consistent between sources and pipelines | F: Corrections not due to imaging artifacts | **supported**

## Reasoning

- Why this data: _not stated_
- Why this method: Two-stage blind and synthetic-data approach to avoid shared bias and select parameters objectively  
  > "This stage allowed us to avoid shared human bias and to assess common features among independent reconstructions." (abstract)
- How they decided it was enough: _not stated_
- Limitation (authors): Ring width only an upper limit; central brightness only a limit; knots may be artifacts  
  > "these features should be interpreted with caution." (7.2 Image Uncertainties)
- Caveat (inferred, ours): Synthetic training models have fixed compact flux 0.6 Jy and simple morphology, possibly biasing fiducial parameters
- Caveat (inferred, ours): Fidelity limited by sparse uv coverage

## Reproducibility

- Data public (paper): SR1 data and analysis software accessible via EHT data portal  
  > "Information about accessing SR1 data and the software used for analysis can be found on the Event Horizon Telescope website’s data portal." (3.1 EHT Observations and Data)
- Products in archive: _not stated_
- Code: eht-imaging and SMILI are open source; DIFMAP public  
  > "we used two open-source software libraries that have been developed specifically for the EHT" (2.2.2)
- Missing: Upstream correlation/calibration is in Paper III
- Missing: Full scripts and parameter files not in text
- Data volume (inferred): Small (calibrated, averaged VLBI visibilities, MBs) from the EHT data portal; raw data not needed
- Score (inferred): 4/5, Parameters, grids and fiducials largely tabulated, data and software public; ALMA role is only a phased station.
- Rediscovery candidate: yes, Public calibrated visibilities, stated fiducial parameters, numeric ring results; but ALMA is minor and scripts are external.

## Links

- Method: Chael et al. 2016, 2018 (eht-imaging) (RML imaging method)
- Method: Akiyama et al. 2017a, 2017b (SMILI) (RML sparse modeling imaging)
- Companion: EHT Collaboration et al. 2019c (Paper III) (Observations, correlation, calibration)
- Companion: EHT Collaboration et al. 2019e (Paper VI) (Black hole mass and model fitting)
- Companion: EHT Collaboration et al. 2019d (Paper V) (GRMHD models)
- Related: Event Horizon Telescope 2017 campaign
- Related: ALMA Phasing Project

## Checks

```json
{
 "quotes": 47,
 "quotes_ok": 47,
 "quote_pass_rate": 1.0,
 "quotes_too_long": 0,
 "unsupported_facts": 0,
 "project_codes": 1,
 "codes_not_in_text": [],
 "codes_not_in_obscore": [],
 "obscore_codes_not_in_card": [],
 "codes_printed_but_missing": [],
 "numeric_results": 2,
 "numeric_problems": 0,
 "fill": {
  "facts": 73,
  "stated": 38,
  "rate": 0.521
 },
 "evidence_ok": true
}
```
