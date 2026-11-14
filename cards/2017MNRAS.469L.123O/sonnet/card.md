# ALMA polarization observations of the particle accelerators in the hotspot of the radio galaxy 3C 445

`2017MNRAS.469L.123O` | Monthly Notices of the Royal Astronomical Society 2017 | first author: Orienti, M. | arXiv: 1705.06465 | DOI: 10.1093/mnrasl/slx067

Card schema 1.0 | model claude-sonnet-5-5 | depth full | type observational_alma_primary

## Science

- Fields: agn_and_quasars
- Question: Does the polarization of the 3C 445 South hot spot at 97.5 GHz favour multiple shocks or turbulent second-order Fermi acceleration as the origin of the extended optical emission?  
  > "a clear evidence in support of either the multiple/complex shock scenario or the turbulence model requires deep polarimetric observations in the mm regime" (Introduction)
- Target **3C 445 South hot spot**: coordinates _not stated_; z/distance z = 0.0558, D_L = 252 Mpc  
  > "At the redshift of the target, $z$ = 0.0558, the luminosity distance $D_{\rm L}$ is 252 Mpc, and 1 arcsecond = 1.09 kpc." (Introduction); distance from derived from redshift with H0=71, OmegaM=0.27, OmegaL=0.73  
  > "At the redshift of the target, $z$ = 0.0558, the luminosity distance $D_{\rm L}$ is 252 Mpc, and 1 arcsecond = 1.09 kpc." (Introduction)

## Data provenance

- ALMA projects: 2013.1.00286.S
- bands: Band 3 (97.5 GHz), full polarization  
  > "using the Band 3 receiver (97.5 GHz) in full polarization" (2 Observations and Data Reduction)
- frequencies and spectral setup: _not stated_
- continuum bandwidth: _not stated_
- arrays: _not stated_
- configurations: _not stated_
- baselines: _not stated_
- angular resolution: 0.6 arcsec  
  > "The resolution is 0.6 arcsecond." (2 Observations and Data Reduction)
- max recoverable scale: _not stated_
- sensitivity: rms 15 uJy/beam Stokes I; 12 uJy/beam Stokes Q and U  
  > "Final images have an rms of 15 $\mu$Jy/beam in Stokes I, and 12 $\mu$Jy/beam in Stokes Q and U." (2 Observations and Data Reduction)
- time on source: 2 hr on source, 3 hr total  
  > "The target on-source observing time was 2 hr, for a total observing time of 3 hr" (2 Observations and Data Reduction)
- observing dates: 2015 September 3, Cycle 2  
  > "The observations were performed on 2015 September 3 and 32 good antennas participated in the observing run." (2 Observations and Data Reduction)
- pi or archival as stated: _not stated_
- Other facility **VLA**: 8.4 GHz A-configuration data for spectral index  
  > "we made use of VLA observations at 8.4 GHz in A-configuration to perform the spectral index analysis." (2 Observations and Data Reduction)
- External data: Calibrated VLA 8.4 GHz data  
  > "Calibration and data reduction of VLA data can be found in (cite: mo12)." (2 Observations and Data Reduction) [from (cite: mo12)]
- External data: Phase calibrator flux 1.322 Jy at 97.5 GHz from ALMA catalogue  
  > "taking the flux from the ALMA catalogue (1.322 Jy at 97.5 GHz)" (2 Observations and Data Reduction) [from ALMA calibrator catalogue]

## Processing

### Calibration

- pipeline or manual: _not stated_
- casa version: CASA 4.7.0  
  > "Calibration and data reduction was done using Common Astronomical Software Applications (CASA) version 4.7.0." (2 Observations and Data Reduction)
- pipeline version: _not stated_
- archive products used as is: _not stated_
- flux calibrator: Ceres inaccurate; phase calibrator 3C 446 used with 1.322 Jy  
  > "it has been found out that Ceres gives an inaccurate flux calibration, so the phase calibrator has been used instead" (2 Observations and Data Reduction)
- flux scale uncertainty: 3 per cent assumed amplitude scale uncertainty  
  > "assuming a 3 per cent uncertainty on the amplitude scale at both frequencies" (2 Observations and Data Reduction)
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
- primary beam correction: not needed, target on-axis  
  > "No primary beam correction was needed since the target was on-axis." (2 Observations and Data Reduction)
- array combination: _not stated_
- smoothing: _not stated_
- final beam: 0.6 arcsec resolution  
  > "The resolution is 0.6 arcsecond." (2 Observations and Data Reduction)
- final rms: 15 uJy/beam (I), 12 uJy/beam (Q, U)  
  > "Final images have an rms of 15 $\mu$Jy/beam in Stokes I, and 12 $\mu$Jy/beam in Stokes Q and U." (2 Observations and Data Reduction)

### Inherited from earlier work

- ALMA polarization calibration procedure  
  > "Details of ALMA polarization data calibration can be found in (cite: nagai16)." (2 Observations and Data Reduction) [from (cite: nagai16)]
- Polarization error computation  
  > "Errors on the polarization parameters were computed following (cite: fanti04)" (2 Observations and Data Reduction) [from (cite: fanti04)]
- VLA calibration and reduction  
  > "Calibration and data reduction of VLA data can be found in (cite: mo12)." (2 Observations and Data Reduction) [from (cite: mo12)]

### Not stated but needed to reproduce (our reading)

- Imaging task, weighting/robust, cell and image size, cleaning parameters
- uv-range and common resolution used for the spectral index maps
- Polygon regions used for flux extraction
- Whether self-calibration was applied
- Which VLA datasets and their calibration/imaging
- Bandwidth and spectral windows

## Analysis recipe

1. **Calibrate ALMA polarization data and image Stokes I, Q, U**: CASA calibration with polarization calibrator J2134-0153 for D-terms and cross-hand delay/phase; flux scale from phase calibrator  
  > "J2134-0153 was observed for calibration of the instrumental polarization (D-terms), cross-hand delay, and cross-hand phase." (2 Observations and Data Reduction)
   - software: CASA
   - fitting: _not stated_
   - validation: _not stated_
2. **Make polarization intensity, angle and fractional polarization maps**: Combine Q and U images; blank fractional polarization where total intensity below 3 times off-source rms  
  > "Blanking on the fractional polarization image was done by clipping the pixels of the total intensity image with values below three times the rms measured on the off-source image plane." (2 Observations and Data Reduction)
   - fitting: _not stated_
   - validation: _not stated_
3. **Make 97.5-8.4 GHz spectral index map**: Matched ALMA and VLA images with same uv-range, resolution, sampling; registered on brightest optically-thin component; 3 sigma blanking  
  > "We produced another set of VLA and ALMA images with the same *uv*-range, resolution and image sampling." (2 Observations and Data Reduction)
   - assumption: S_nu ∝ nu^-alpha  
  > "we define the spectral index $\alpha$ as $S_{\nu} \propto \nu^{- \alpha}$" (Footnotes)
   - fitting: _not stated_
   - validation: _not stated_
4. **Extract component fluxes**: Polygonal regions for flux densities and polarized flux; errors by propagation with 3% amplitude uncertainty  
  > "are extracted from the same region by selecting polygonal areas." (2 Observations and Data Reduction)
   - fitting: _not stated_
   - validation: _not stated_
5. **Estimate turbulent cell size**: Analytic relation l_t ~ (p_obs/p_int)^(2/3)(A_b phi/...)^(1/3) with p_int ~70% and p_obs <4%  
  > "If in Eq. [\[equation\]](#equation) we consider $p_{\rm int} \sim 70$ per cent and $p_{\rm obs} < 4$ per cent, we obtain $l_{\rm t} \sim$ 160 pc." (5 Discussion and conclusions)
   - assumption: turbulent field produces random polarization orientation; turbulent region size 4 kpc  
  > "assuming a simple picture where the turbulent magnetic field produces random polarization orientation" (5 Discussion and conclusions)
   - fitting: _not stated_
   - validation: _not stated_

## Software

- **CASA** 4.7.0: ALMA calibration and data reduction  
  > "Calibration and data reduction was done using Common Astronomical Software Applications (CASA) version 4.7.0." (2 Observations and Data Reduction)

## Numeric results

| quantity | value | uncertainty | units | step | quote |
|---|---|---|---|---|---|
| Total fractional polarization of hot spot | 27 | not stated | per cent | 4 | / Tot  / 99.3$\pm$3.0 / 20.4$\pm$0.61 / 5.61$\pm$0.17 / 27  / 0.64$\pm$0.02 / |
| Spectral index E component | 0.70 | 0.02 | dimensionless | 3 | The spectral index of the E and W components is $\alpha =0.70\pm 0.02$ and 0.62$\pm$0.02, respectively. |
| Integrated spectral index 97.5-8.4 GHz | 0.64 | 0.02 | dimensionless | 3 | $\alpha =$ 0.64$\pm$0.02 |
| Upper limit on fractional polarization between E and W | <4 | not stated | per cent | 2 | we could set a tight upper limit on the fractional polarization of about 4 per cent |
| Offset between total intensity and polarized peak in W | 0.5 | not stated | kpc | 2 | There is a clear offset of about 0.5 arcsec (0.5 kpc) |
| Turbulent cell size | ~160 | not stated | pc | 5 | we obtain $l_{\rm t} \sim$ 160 pc |

## Qualitative findings

- Strong polarization in E and W (30-40%) indicates shocks; no polarization in diffuse emission implies tangled field  
  > "Both components show fractional polarization between 30 and 40 per cent, suggesting the presence of shocks." (abstract)

## Claim tuples

- H: Are E and W components sites of shock acceleration? | E: ALMA 97.5 GHz polarimetry | R: 30-40% fractional polarization, EVPA perpendicular to structures | F: Multiple shock fronts, W polarization may trace front shock | **supported**
- H: Is diffuse emission produced by turbulent Fermi-II acceleration? | E: Search for polarization in diffuse emission and spectral index | R: No polarization <4%, flatter spectral index 0.60 | F: Disordered field with cells ~160 pc consistent with Fermi-II | **partially**

## Reasoning

- Why this data: _not stated_
- Why this method: mm polarimetry minimizes steep-spectrum lobe and Faraday rotation contributions  
  > "in the mm regime where contributions from the steep-spectrum lobe and from the Faraday rotation are marginal" (Introduction)
- How they decided it was enough: _not stated_
- Limitation (authors): Low SNR in the ridge limits constraint on polarization; edge gradients in spectral index maps  
  > "although the low SNR prevents a tight constraint of its value" (5 Discussion and conclusions)
- Caveat (inferred, ours): Single short observation; flux scale from phase calibrator after Ceres failure
- Caveat (inferred, ours): Turbulent cell size estimate rests on assumed intrinsic polarization and region size
- Caveat (inferred, ours): Beam depolarization not separately tested

## Reproducibility

- Data public (paper): ALMA project cited; public status not explicitly stated  
  > "This paper makes use of the following ALMA data: ADS/JAO.ALMA#2013.1.00286.S." (Acknowledgments)
- Products in archive: _not stated_
- Missing: Imaging parameters
- Missing: Polarization calibration details (in Nagai16)
- Missing: VLA data details (in Orienti12)
- Missing: Region definitions
- Data volume (inferred): ~20-50 GB raw for the ALMA dataset
- Score (inferred): 4/5, Short letter with limited imaging details, relying on cited papers for calibration.
- Rediscovery candidate: no, Imaging and VLA recipe incomplete.

## Links

- Method: (cite: nagai16) (ALMA polarization calibration)
- Method: (cite: fanti04) (polarization error computation)
- Companion: (cite: mo12) (VLA data and multiwavelength study of 3C 445 South)
- Companion: (cite: prieto02) (turbulence model for diffuse optical emission)

## Checks

```json
{
 "quotes": 42,
 "quotes_ok": 42,
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
  "facts": 69,
  "stated": 32,
  "rate": 0.464
 },
 "evidence_ok": true
}
```
