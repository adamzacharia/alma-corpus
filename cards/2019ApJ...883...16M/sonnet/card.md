# An Observational Study for Grain Dynamics in the AS 209 Disk with Submillimeter Polarization

`2019ApJ...883...16M` | The Astrophysical Journal 2019 | first author: Mori, Tomohiro | arXiv: 1907.10229 | DOI: 10.3847/1538-4357/ab3575

Card schema 1.0 | model claude-sonnet-5-5 | depth full | type observational_alma_primary

## Science

- Fields: protoplanetary_disks
- Question: What are the origins of the 870 um polarization in the AS 209 disk (self-scattering vs grain alignment), and what do they imply for grain size and grain dynamics?  
  > "In this work, we perform 870 $\mu$m ALMA polarization observations of the disk around AS 209 and discuss the origins of the polarization." (Introduction)
- Target **AS 209**: coordinates _not stated_; z/distance 121 ± 2 pc  
  > "AS 209 is a Classical T Tauri star in the Ophiuchus star forming region at a distance of 121 $\pm$ 2 pc (cite: gaia2018)." (Introduction); distance from Gaia (gaia2018)  
  > "AS 209 is a Classical T Tauri star in the Ophiuchus star forming region at a distance of 121 $\pm$ 2 pc (cite: gaia2018)." (Introduction)

## Data provenance

- ALMA projects: 2017.1.00124.S
- bands: 870 um continuum polarization  
  > "The continuum polarization observations at 870 $\mu$m were carried out on 2018 May 16 during ALMA Cycle 5 operation." (Observations)
- frequencies and spectral setup: four TDM spws centered at 336.5, 338.4, 348.5, 350 GHz  
  > "Those four spws were centered at the central frequencies of 336.5, 338.4, 348.5 and 350 GHz." (Observations)
- continuum bandwidth: ~7.5 GHz (4 x 1.875 GHz)  
  > "The effective bandwidth of each spw is 1.875 GHz, providing the bandwidth of $\sim$7.5 GHz." (Observations)
- arrays: _not stated_
- configurations: C43-2, 43 antennas  
  > "The antenna configurations were C43-2 with 43 antennas." (Observations)
- baselines: _not stated_
- angular resolution: 0.94" x 0.62" (~114 x 75 au)  
  > "The beam size in the final product is 0.$''$94 $\times$ 0.$''$62 which corresponds to $\sim$114 $\times$ 75 au at the distance of 121 pc." (Observations)
- max recoverable scale: _not stated_
- sensitivity: _not stated_
- time on source: 30.89 minutes  
  > "The total integration times for the target were 30.89 minutes in the observation." (Observations)
- observing dates: 2018 May 16 (Cycle 5)  
  > "The continuum polarization observations at 870 $\mu$m were carried out on 2018 May 16 during ALMA Cycle 5 operation." (Observations)
- pi or archival as stated: _not stated_
- External data: Disk major axis PA 85.76 deg, minor axis PA -4.24 deg, inclination 34.88 deg  
  > "We use the major axis position angle (PA) of 85.76$^\circ$ and minor axis PA of $-$4.24$^\circ$ with reference to (cite: guzman2018)." (Results) [from (cite: guzman2018)]
- External data: Previous SMA flux density 577 ± 58 mJy  
  > "which is consistent with the previously obtained value, 577 $\pm$ 58 mJy within the uncertainty (cite: andrews2009)." (Results) [from (cite: andrews2009)]

## Processing

### Calibration

- pipeline or manual: Reduction and calibration following Nagai et al. 2016 process  
  > "We follow the data reduction process given by (cite: nagai2016)." (Observations)
- casa version: CASA 5.1.1  
  > "The reduction and calibration of the data were done with the CASA version 5.1.1 (cite: mcmullin2007)." (Observations)
- pipeline version: _not stated_
- archive products used as is: _not stated_
- flux calibrator: Bandpass J1751-0939, gain J1733-1304, polarization J1924-2914 (flux calibrator not stated)  
  > "The bandpass, complex gain, and polarization calibrators were J1751-0939, J1733-1304 and J1924-2914, respectively." (Observations)
- flux scale uncertainty: _not stated_
- self calibration: _not stated_

### Imaging

- task: interactive tclean  
  > "we perform the interactive CLEAN deconvolution by using the CASA task `tclean`." (Observations)
- deconvolver: _not stated_
- weighting robust: Briggs, robust = 0.5  
  > "We employ Briggs weighting with a robust parameter of 0.5." (Observations)
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
- final beam: 0.94" x 0.62"  
  > "The beam size in the final product is 0.$''$94 $\times$ 0.$''$62" (Observations)
- final rms: _not stated_

### Inherited from earlier work

- Data reduction process and instrumental angle error estimate  
  > "We follow the data reduction process given by (cite: nagai2016)." (Observations) [from (cite: nagai2016)]
- Debiasing of polarized intensity  
  > "We thus derive the debiased polarized intensity with the following equation presented in (cite: vaillancourt2006) and (cite: hull2015)" (Observations) [from (cite: vaillancourt2006); (cite: hull2015)]

### Not stated but needed to reproduce (our reading)

- Flux calibrator and flux scale
- Stokes I, Q, U rms values and clean thresholds/masks
- Image size and cell size
- Polarization calibration details (leakage, angle)
- Self-calibration usage
- Exact regions/pixels used for histograms and the eight positions in the chi2 analysis

## Analysis recipe

1. **Derive polarization quantities**: Debiased PI from Stokes Q,U, PF=PI/I, angle theta=0.5 arctan(U/Q), with error propagation; keep >3 sigma_PI  
  > "All of these values presented above are derived only where the detection is above the threshold 3$\sigma_{PI}$." (Observations)
   - software: CASA
   - parameter: sigma_PI = 2.7e-5 Jy/beam  
  > "$\sigma_{PI}$ = 2.7 $\times$ $10^{-5}$ Jy beam$^{-1}$" (Observations)
   - fitting: _not stated_
   - validation: Systematic angle error 2 deg/sqrt(N)=0.3 deg  
  > "thus $\Delta\chi$ $\sim$ 2$^\circ$/$\sqrt{43}$ = 0.3$^\circ$ in this observation." (Observations)
2. **Compare angles with circular vs elliptical tangents and find systematic offset**: Histograms of deviations with Gaussian fits; weighted mean and chi2 test at eight independent positions  
  > "we select the eight positions in the outer region, where the contamination from the central emission likely weak." (Appendix A)
   - parameter: major axis PA 85.76 deg, inclination 34.88 deg  
  > "the inclination of $34.88\ensuremath{^\circ}$ (cite: guzman2018)" (Results)
   - fitting: _not stated_
   - validation: chi2 = 25 (circle) vs 10 (ellipse)  
  > "each of which corresponds to $\chi^2$ = 25 and 10, respectively." (Appendix A)

## Software

- **CASA** 5.1.1: calibration and tclean imaging  
  > "The reduction and calibration of the data were done with the CASA version 5.1.1 (cite: mcmullin2007)." (Observations)

## Numeric results

| quantity | value | uncertainty | units | step | quote |
|---|---|---|---|---|---|
| Integrated flux density | 489 | 50 | mJy | 0 | The integrated flux density is 489 $\pm$ 50 mJy |
| Mean angular deviation from elliptical tangents | -4.5 | 1.6 | deg | 2 | weighted mean of $\Delta$$\theta_{ellipse}$ = $-$$4.5\ensuremath{^\circ}$ $\pm$ $1.6\ensuremath{^\circ}$ |
| Polarization fraction inner region | ~0.20 | rms ~0.01% | % | 1 | the polarization fractions are almost uniform at $\sim$0.20$\%$. |
| Polarization fraction outer region | ~1.0 | not stated | % | 1 | the typical polarization fraction in the outer region is likely $\sim$1.0% |
| delta v_phi / delta v_r | 0.08 | 0.03 | dimensionless | 2 | tan($\Delta$$\theta_{ellipse}$) = 0.08 $\pm$ 0.03 |

## Qualitative findings

- Inner polarization parallel to minor axis, consistent with self-scattering; outer polarization near-azimuthal (elliptical) with offset of opposite sign to the helicity-alignment prediction for clockwise rotation.  
  > "the directions of the observed angular deviations are opposite to what is predicted under the fact that the disk rotates clockwise." (abstract)

## Claim tuples

- H: Inner-disk polarization arises from self-scattering | E: Compare angles with minor axis and measure PF | R: Vectors along minor axis; PF ~0.2%, below the 2-3% expected for a_max~140 um | F: Self-scattering dominates; grain size distribution differs (a_max ~50 or ~400 um or two populations) | **supported**
- H: Outer polarization comes from mechanically aligned drifting grains | E: Angle analysis vs circular/elliptical tangents | R: Elliptical preferred; offset -4.5±1.6 deg | F: Mechanical alignment needed but the sign of the offset is inconsistent with the helicity model for clockwise rotation | **partially**

## Reasoning

- Why this data: _not stated_
- Why this method: _not stated_
- Alternative: Gold mechanism considered but requires St>~10 where emission is inefficient; grain diffusion gives the same pattern as accumulation  
  > "it is uncertain whether the observed orientations can be explained by the possible grain dynamics." (Discussion)
- How they decided it was enough: _not stated_
- Limitation (authors): Large beam limits angle analysis; beam dilution effects  
  > "the large beam size effects are not negligible." (Conclusions)
- Caveat (inferred, ours): Small sample (8 independent positions) and marginal S/N
- Caveat (inferred, ours): Beam dilution not modeled
- Caveat (inferred, ours): Sign convention of angles could affect the key conclusion

## Reproducibility

- Data public (paper): _not stated_
- Products in archive: _not stated_
- Missing: Calibration details and flux calibrator
- Missing: Imaging mask/size
- Missing: Pixel selection for statistics
- Data volume (inferred): ~10-20 GB raw (single short polarization execution)
- Score (inferred): 5/5, Short recipe with the key imaging parameters and formulas, but several calibration and selection details are missing.
- Rediscovery candidate: no, Public data likely but the paper does not state it, and calibration details are missing.

## Links

- Method: (cite: nagai2016) (Polarization data reduction procedure)
- Companion: (cite: kataoka2019) (Helicity-induced alignment model predictions)
- Companion: (cite: guzman2018) (High-resolution AS 209 disk structure)

## Checks

```json
{
 "quotes": 39,
 "quotes_ok": 39,
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
  "facts": 59,
  "stated": 30,
  "rate": 0.508
 },
 "evidence_ok": true
}
```
