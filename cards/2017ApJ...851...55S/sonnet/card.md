# ALMA Reveals Transition of Polarization Pattern with Wavelength in HL Tau’s Disk

`2017ApJ...851...55S` | The Astrophysical Journal 2017 | first author: Stephens, Ian W. | arXiv: 1710.04670 | DOI: 10.3847/1538-4357/aa998b

Card schema 1.0 | model claude-sonnet-5-5 | depth full | type observational_alma_primary

## Science

- Fields: protoplanetary_disks
- Question: What mechanism produces (sub)millimeter polarization in the HL Tau disk, and does the polarization pattern change with wavelength (870 um, 1.3 mm, 3.1 mm)?  
  > "In this paper, we present ALMA polarization observations of HL Tau for two more wavelengths: 870 $\mu$m and 1.3 mm." (abstract)
- Target **HL Tau**: coordinates _not stated_; z/distance ~140 pc  
  > "Given a distance to HL Tau of $\sim$140 pc (cite: Rebull2004), the spatial resolution is 64, 42, and 55 au, respectively." (Observations); distance from Rebull et al. 2004  
  > "Given a distance to HL Tau of $\sim$140 pc (cite: Rebull2004), the spatial resolution is 64, 42, and 55 au, respectively." (Observations)

## Data provenance

- ALMA projects: 2016.1.00162.S, 2016.1.00115.S
- bands: Band 7 (870 um), Band 6 (1.3 mm); Band 3 (3.1 mm) from earlier paper  
  > "we observed polarized emission toward HL Tau at 870 $\mu$m (Band 7) and at 1.3 mm (Band 6)" (Observations)
- frequencies and spectral setup: Four 1.75 GHz spws; Band 7: 336.5, 338.6, 348.5, 350.5 GHz; Band 6: 224, 226, 240, 242 GHz  
  > "the correlator was tuned to four 1.75 GHz spectral windows at center sky frequencies of 336.5, 338.6, 348.5, and 350.5 GHz, and for 1.3 mm at center frequencies of 224, 226, 240, and 242 GHz" (Observations)
- continuum bandwidth: _not stated_
- arrays: _not stated_
- configurations: C40-4 (870 um), C40-5 (1.3 mm)  
  > "The ALMA configurations for 870 $\mu$m and 1.3 mm observations were C40-4 and C40-5, respectively." (Observations)
- baselines: _not stated_
- angular resolution: 3.1 mm: 0.51x0.41 arcsec; 1.3 mm: 0.37x0.24 arcsec; 870 um: 0.44x0.35 arcsec  
  > "0$\ensuremath{''}$37$\times$0$\ensuremath{''}$24 at –44$\ensuremath{^\circ}$1; and 0$\ensuremath{''}$44$\times$0$\ensuremath{''}$35 at –17$\ensuremath{^\circ}$9, respectively." (Observations)
- max recoverable scale: _not stated_
- sensitivity: _not stated_
- time on source: _not stated_
- observing dates: 2016 Dec 4 (870 um); 2017 Jul 12 (1.3 mm)  
  > "on 2016 December 4and 2017 July 12, respectively" (Observations)
- pi or archival as stated: _not stated_
- Other facility **ALMA Band 3 data (Kataoka et al. 2017)**: 3.1 mm polarization data, re-imaged identically  
  > "We also include 3.1 mm (Band 3) data which were from (cite: Kataoka2017), except we re-imaged in the identical way described above." (Observations)
- External data: HL Tau disk major axis position angle 138.02 +/- 0.07 deg  
  > "The major axis of HL Tau's disk is 138$\ensuremath{^\circ}$02 $\pm$ 0$\ensuremath{^\circ}$07 (cite: ALMA2015)" (Results) [from ALMA Partnership 2015 (cite: ALMA2015)]
- Simulation/model as data: Radiative/scattering model similar to Model A of Yang et al. 2017 with reduced dust scale height; oblate grains, 1% intrinsic polarization, 30 um effective grain size  
  > "The intrinsic polarization fraction of the non-spherical grains is set to 1%, and the effective grain size is 30 $\mu$m." (1.3 mm Morphological Model of HL Tau)

## Processing

### Calibration

- pipeline or manual: _not stated_
- casa version: CASA 4.7.2 (imaging)  
  > "performed imaging with CASA version 4.7.2" (Observations)
- pipeline version: _not stated_
- archive products used as is: Delivered calibrated uv-data used  
  > "We used the delivered calibrated uv-data and performed imaging with CASA version 4.7.2." (Observations)
- flux calibrator: J0510+1800 (bandpass and flux); phase J0431+1731; polarization J0522–3627  
  > "the bandpass and flux calibrator was J0510+1800, the phase calibrator was J0431+1731, and the polarization calibrator was J0522–3627." (Observations)
- flux scale uncertainty: _not stated_
- self calibration: Phase-only, progressively shorter solution intervals; Stokes I first, final round on all four Stokes  
  > "we performed a series of phase-only self calibration, and images were cleaned after each self calibration iteration with progressively shorter solution intervals." (Observations)

### Imaging

- task: CASA tclean  
  > "We used the CASA `tclean` task using a Briggs weighting parameter of robust=1." (Observations)
- deconvolver: _not stated_
- weighting robust: Briggs robust=1  
  > "We used the CASA `tclean` task using a Briggs weighting parameter of robust=1." (Observations)
- uv taper: _not stated_
- cell size: _not stated_
- image size: _not stated_
- masking: _not stated_
- multiscale scales: _not stated_
- continuum subtraction: _not stated_
- line free channels: _not stated_
- primary beam correction: Images primary-beam corrected  
  > "Images were primary-beam corrected." (Observations)
- array combination: _not stated_
- smoothing: _not stated_
- final beam: 3.1 mm 0.51x0.41 (PA -67.6); 1.3 mm 0.37x0.24 (PA -44.1); 870 um 0.44x0.35 (PA -17.9)  
  > "0$\ensuremath{''}$37$\times$0$\ensuremath{''}$24 at –44$\ensuremath{^\circ}$1; and 0$\ensuremath{''}$44$\times$0$\ensuremath{''}$35 at –17$\ensuremath{^\circ}$9, respectively." (Observations)
- final rms: _not stated_

### Inherited from earlier work

- Polarization intensity and P de-biasing method  
  > "The polarization intensity and $P$ was de-biased via the method described in (cite: Hull2014) and (cite: Hull2015)." (Observations) [from (cite: Hull2014); (cite: Hull2015)]
- 3.1 mm Band 3 data taken from earlier paper  
  > "We also include 3.1 mm (Band 3) data which were from (cite: Kataoka2017), except we re-imaged in the identical way described above." (Observations) [from (cite: Kataoka2017)]
- Polarized-intensity model based on Model A of Yang et al. 2017; electrostatic approximation per Yang 2016b  
  > "The direct emission and scattering by such grains are computed under the electrostatic approximation (see (cite: Yang2016b) for details)." (1.3 mm Morphological Model of HL Tau) [from (cite: Yang2017); (cite: Yang2016b)]

### Not stated but needed to reproduce (our reading)

- Self-calibration solution intervals and number of rounds
- Clean threshold, masks, niter, cell and image size
- Whether the two Band 6/7 execution blocks or the 2016.1.00115.S data were combined and which were used
- Exact method for computing central polarization vector angles and P profiles
- Details of the polarized intensity disk model (inclination, density, scale height)
- Spectral windows/channels used for continuum
- Polarization calibration details

## Analysis recipe

1. **Image Stokes I,Q,U,V with self-calibration**: tclean on delivered calibrated data, phase-only self-cal on Stokes I then all Stokes, primary beam correction  
  > "We first performed several rounds of self calibration to the Stokes $I$ image only, and then did self calibration a final round of self calibration on all four Stokes parameters." (Observations)
   - software: CASA
   - parameter: robust=1  
  > "We used the CASA `tclean` task using a Briggs weighting parameter of robust=1." (Observations)
   - fitting: _not stated_
   - validation: _not stated_
2. **Derive debiased polarization maps and uncertainties**: Compute P and polarization intensity, de-biased; 0.1% instrumental error floor  
  > "In cases where the measured $P$ rms was less than this value, we used 0.1% as our error." (Observations)
   - parameter: instrumental P error 0.1%  
  > "The ALMA instrumental error on $P$ is expected to be about 0.1%." (Observations)
   - fitting: _not stated_
   - validation: _not stated_
3. **Compare morphology across wavelengths and measure vector angles and P asymmetry**: Compare polarization vectors, Stokes Q/U at three wavelengths; measure central vector angle and P along major axis  
  > "The central polarization vectors for 1.3 mm and 870 $\mu$m are 55$\ensuremath{^\circ}$4 $\pm$0$\ensuremath{^\circ}$96 and 55$\ensuremath{^\circ}$3 $\pm$0$\ensuremath{^\circ}$41, respectively." (Results)
   - fitting: _not stated_
   - validation: _not stated_
4. **Build 1.3 mm morphological models**: 50–50 mix of azimuthal and uniform minor-axis patterns by averaging Q and U; scattering plus aligned-grain disk model for polarized intensity  
  > "We created the model by averaging the Stokes $Q$ and $U$ of the two patterns separately." (1.3 mm Morphological Model of HL Tau)
   - parameter: intrinsic polarization 1%, grain size 30 um  
  > "The intrinsic polarization fraction of the non-spherical grains is set to 1%, and the effective grain size is 30 $\mu$m." (1.3 mm Morphological Model of HL Tau)
   - assumption: Oblate grains with shortest axes aligned radially  
  > "The grains are assumed to be oblate spheroids with their shortest axes aligned radially" (1.3 mm Morphological Model of HL Tau)
   - fitting: _not stated_
   - validation: Visual comparison with observations  
  > "The two match remarkably well, which strengthens the notion that the 1.3 mm emission is a transition case between 3.1 mm and 870 $\mu$m." (1.3 mm Morphological Model of HL Tau)

## Software

- **CASA** 4.7.2: Imaging (tclean) and self-calibration  
  > "We used the delivered calibrated uv-data and performed imaging with CASA version 4.7.2." (Observations)

## Numeric results

| quantity | value | uncertainty | units | step | quote |
|---|---|---|---|---|---|
| Central polarization vector angle, 1.3 mm | 55.4 | 0.96 | deg | 3 | The central polarization vectors for 1.3 mm and 870 $\mu$m are 55$\ensuremath{^\circ}$4 $\pm$0$\ensuremath{^\circ}$96 and 55$\ensuremath{^\circ}$3 $\pm$0$\ensuremath{^\circ}$41, respectively. |
| Central polarization vector angle, 870 um | 55.3 | 0.41 | deg | 3 | The central polarization vectors for 1.3 mm and 870 $\mu$m are 55$\ensuremath{^\circ}$4 $\pm$0$\ensuremath{^\circ}$96 and 55$\ensuremath{^\circ}$3 $\pm$0$\ensuremath{^\circ}$41, respectively. |
| P difference between peaks along major axis, 1.3 mm | 0.0013 | 0.0014 | dimensionless | 3 | For 1.3 mm, the absolute difference between the two $P$ peaks along the major axis is 0.0013 $\pm$ 0.0014, which is not statistically significant. |
| P peak northwest, 870 um | 0.0077 | 0.0010 | dimensionless | 3 | The $P$ peak toward the northwest is 0.0077 $\pm$ 0.0010. |
| P at mirrored southeast position, 870 um | 0.0094 | 0.0010 | dimensionless | 3 | at the same radius on the southeast side, $P$ = 0.0094 $\pm$ 0.0010. |
| P asymmetry along major axis, 870 um | ~0.002–0.004 | not stated | dimensionless | 3 | Therefore, the $P$ asymmetry along the major axis for 870 $\mu$m is $\sim$0.002–0.004. |

## Qualitative findings

- 870 um polarization is uniform and parallel to the minor axis (consistent with self-scattering); 3.1 mm azimuthal; 1.3 mm a mix  
  > "For 870 $\mu$m, the polarization morphology is extremely uniform and parallel with the minor axis of the disk." (Results)

## Claim tuples

- H: The dominant polarization mechanism in HL Tau changes with wavelength | E: ALMA polarimetry at 870 um, 1.3 mm, and re-imaged 3.1 mm | R: Uniform minor-axis pattern at 870 um, azimuthal at 3.1 mm, superposition at 1.3 mm | F: Polarization mechanism transitions with wavelength | **supported**
- H: The 1.3 mm pattern is a transition between scattering and radiation-anisotropy alignment | E: 50–50 mix model and scattering model with aligned grains | R: Models match observed pattern broadly | F: 1.3 mm can plausibly be explained by direct emission plus scattering by aligned grains | **partially**
- H: Grains are settled and disk is non-axisymmetric | E: Measure P asymmetry along major and minor axes at 870 um | R: Asymmetry along major axis, none along minor axis | F: Large grains settled into thin layer; disk not perfectly axisymmetric (tentative) | **partially**

## Reasoning

- Why this data: _not stated_
- Why this method: _not stated_
- Alternative: Toroidal magnetic field alignment is not consistent with observations  
  > "These observations are not consistent with polarized emission from grains aligned with a toroidal magnetic field." (Summary)
- How they decided it was enough: _not stated_
- Limitation (authors): Stokes V detection may be spurious and not discussed  
  > "Stokes $V$ has not been well characterized for ALMA, so its detection could be spurious and will not be discussed in detail in this paper." (Results)
- Limitation (authors): Model is not unique and does not match all details  
  > "This model is not unique and does not match all details of the data" (1.3 mm Morphological Model of HL Tau)
- Caveat (inferred, ours): Imaging and self-cal parameters are sparse, so images may not be reproducible exactly
- Caveat (inferred, ours): Single source, so generality of the wavelength transition is untested
- Caveat (inferred, ours): 7 deg offset of vectors from perpendicular is unexplained
- Caveat (inferred, ours): Radiative model not fit, only illustrative

## Reproducibility

- Data public (paper): _not stated_
- Products in archive: _not stated_
- Missing: Self-calibration intervals, clean parameters, masks
- Missing: Model disk parameters
- Missing: Data selection between the two linked project codes
- Data volume (inferred): ~100–300 GB raw for the two Cycle 4 polarization datasets (delivered calibrated products smaller)
- Score (inferred): 3/5, Data are archival-type with CASA workflow named, but self-cal and imaging details and modeling are underspecified.
- Rediscovery candidate: no, Recipe lacks key imaging/self-cal parameters and public status is not stated in the paper.

## Links

- Method: (cite: Hull2014); (cite: Hull2015) (Polarization de-biasing method)
- Method: (cite: Yang2016b) (Electrostatic approximation scattering calculations)
- Companion: (cite: Kataoka2017) (3.1 mm ALMA polarization of HL Tau)
- Companion: (cite: Stephens2014b) (CARMA 1.25 mm polarization of HL Tau)
- Companion: (cite: Yang2017) (Scattering-polarization models for inclined disks)

## Checks

```json
{
 "quotes": 48,
 "quotes_ok": 48,
 "quote_pass_rate": 1.0,
 "quotes_too_long": 0,
 "unsupported_facts": 0,
 "project_codes": 2,
 "codes_not_in_text": [],
 "codes_not_in_obscore": [],
 "obscore_codes_not_in_card": [],
 "codes_printed_but_missing": [],
 "numeric_results": 6,
 "numeric_problems": 0,
 "fill": {
  "facts": 70,
  "stated": 36,
  "rate": 0.514
 },
 "evidence_ok": true
}
```
