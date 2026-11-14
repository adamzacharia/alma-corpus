# ALMA full polarization observations of PKS 1830-211 during its record-breaking flare of 2019

`2020A&A...638L..13M` | Astronomy and Astrophysics 2020 | first author: Marti-Vidal, I. | arXiv: 2006.06044 | DOI: 10.1051/0004-6361/202038094

Card schema 1.0 | model claude-sonnet-5-5 | depth full | type observational_alma_primary

## Science

- Fields: agn_and_quasars
- Question: How do the polarization properties of the lensed blazar PKS 1830-211 differ between its two lensed images and vary on intra-hour timescales during its 2019 gamma-ray flare, and can differential polarimetry be validated with full-polarization data?  
  > "Here we report full polarization radio-millimeter observations of PKS 1830$-$211 obtained with ALMA close in time to this exceptional peak of the $\gamma$-ray activity." (Introduction); "The full-polarization calibration allows us to validate the technique of differential polarimetry." (Conclusions)
- Target **PKS 1830-211**: coordinates _not stated_; z/distance absorber at z=0.89 (molecular absorber in front of the blazar)  
  > "The source has two bright and compact images (hereafter labelled NE and SW), separated by 1$''$ and delayed in time by $\sim$26 days" (Introduction); distance from _not stated_

## Data provenance

- ALMA projects: 2018.1.00692.S
- bands: Band 6  
  > "The Band 6 receivers were used" (Observations)
- frequencies and spectral setup: four 1.875 GHz spectral windows at ~234, 236, 247, 249 GHz, 1.95 MHz channels  
  > "the correlator was configured to cover four independent 1.875 GHz wide spectral windows, centered at $\sim 234$, 236, 247, and 249 GHz, with a spectral resolution of 1.95 MHz per channel." (Observations)
- continuum bandwidth: _not stated_
- arrays: _not stated_
- configurations: _not stated_
- baselines: _not stated_
- angular resolution: 0.47'' x 0.31'', PA -83 deg  
  > "The resulting beam is $0.47 ''\times 0.31''$, with a position angle $-83^\circ$." (Results)
- max recoverable scale: _not stated_
- sensitivity: _not stated_
- time on source: _not stated_
- observing dates: 2019 April 11, two consecutive executions over ~2 h  
  > "Observations were done in two consecutive executions over a time span of about two hours." (Observations)
- pi or archival as stated: _not stated_
- Other facility **Fermi-LAT**: gamma-ray light curve of the flare  
  > "see Fig. [3](#fig:gamma-lc), generated from Fermi-LAT observations" (Discussion)

## Processing

### Calibration

- pipeline or manual: CASA, two-step: standard calibration then full-polarization calibration  
  > "The data calibration was done within the Common Astronomy Software Applications (CASA[^1]) package, following a two-step procedure." (Observations)
- casa version: _not stated_
- pipeline version: _not stated_
- archive products used as is: _not stated_
- flux calibrator: J2000-1748 as absolute flux calibrator; bootstrapped to J1832-2039  
  > "The quasar J2000-1748 was also used as absolute flux calibrator." (Observations)
- flux scale uncertainty: better than 10%  
  > "We estimate a flux accuracy better than 10%, based on the ALMA monitoring data of this source." (Observations)
- self calibration: phase-only, 6 s solint, all four spws combined, on Stokes I continuum  
  > "applying phase-only gain corrections at each 6 s integration and combining all four spectral windows to a common solution." (Observations)

### Imaging

- task: tclean for Stokes I, Q, U separately; immath for m and EVPA  
  > "The CASA task `tclean` was executed to reconstruct the images of PKS 1830$-$211 in Stokes I, Q, and U, separately." (Results)
- deconvolver: _not stated_
- weighting robust: uniform  
  > "Uniform visibility weighting was used in the image deconvolution." (Results)
- uv taper: _not stated_
- cell size: _not stated_
- image size: _not stated_
- masking: same mask for Q and U as for Stokes I  
  > "The CLEANing of Stokes Q and U was executed using the same mask as in the CLEANing of Stokes I." (Results)
- multiscale scales: _not stated_
- continuum subtraction: _not stated_
- line free channels: _not stated_
- primary beam correction: _not stated_
- array combination: _not stated_
- smoothing: _not stated_
- final beam: 0.47'' x 0.31'', PA -83 deg  
  > "The resulting beam is $0.47 ''\times 0.31''$, with a position angle $-83^\circ$." (Results)
- final rms: _not stated_

### Inherited from earlier work

- Full-polarization calibration follows standard ALMA procedure  
  > "following the standard ALMA calibration procedure (cite: Nagai)" (Observations) [from (cite: Nagai)]
- Visibility model-fitting approach with uvmultifit  
  > "For a thorough discussion of the advantages of visibility model-fitting in this case, see (cite: mar14)." (Results) [from (cite: mar14)]
- Differential polarimetry formalism (Eq. 11)  
  > "derived from Eq. 11 of (cite: mar16), which is the exact expression for differential polarimetry" (Discussion) [from (cite: mar16)]

### Not stated but needed to reproduce (our reading)

- tclean cell size, image size, iteration/threshold and mask definition
- CASA version
- line-free channel selection and flagged absorption/atmospheric ranges
- polarization calibrator model/reference antenna details
- uvmultifit source-model settings and error estimation
- fit method for Faraday RM and the NE/SW flux ratio function

## Analysis recipe

1. **Calibrate and self-calibrate**: Standard calibration, flagging of absorption lines, polarization calibration with J1924-2914, phase-only self-cal on Stokes I  
  > "The quasar J 1924$-$2914 was observed as the polarization calibrator." (Observations)
   - software: CASA
   - parameter: self-cal solint 6 s, all spws combined  
  > "applying phase-only gain corrections at each 6 s integration and combining all four spectral windows to a common solution." (Observations)
   - fitting: _not stated_
   - validation: Dynamic range improved by factor 2-3 after self-cal, reaching >~1000  
  > "the dynamic range (DR; i.e., the ratio of peak flux to rms noise level in the image) improved by a factor 2–3 after self-calibration" (Observations)
2. **Image Stokes I,Q,U and derive m and EVPA**: tclean per Stokes, immath pixel-wise m and phi  
  > "The images of the degree of linear polarization, $m$, and EVPA, $\phi$, were computed pixel-wise from the Stokes Q and U images with the CASA task `immath`" (Results)
   - software: CASA
   - fitting: _not stated_
   - validation: _not stated_
3. **Intra-observation variability via visibility fitting**: Each ~410 s scan split in three segments; Stokes I, Q, U of both images fitted independently with uvmultifit; differential NE/SW approach  
  > "Each ALMA scan (with a typical duration of 410 seconds) was divided into three segments of equal length and the Stokes parameters I, Q, and U of PKS 1830$-$211 were fitted independently to each scan subdivision." (Results)
   - software: uvmultifit
   - assumption: Both lensed images point-like within the beam  
  > "Since both lensed images of the blazar are point-like within the ALMA beam" (Results)
   - fitting: _not stated_
   - validation: Differential approach removes residual instrumental effects common to both images  
  > "we search for relative changes between the NE and SW polarization states, in order to remove any possible residual instrumental effect" (Results)
4. **Validate differential polarimetry**: Fit XX and YY flux ratios in 15 segments per scan, compute Rpol=(rho_X/rho_Y-1)/2 vs source rotation, compare with prediction from full-pol Stokes parameters  
  > "In these fits, we divided each scan into 15 segments of equal duration to perform an intra-observation analysis" (Discussion)
   - software: uvmultifit
   - parameter: feed rotation beta = 45 deg in Band 6  
  > "which are rotated by $\beta = 45^\circ$ with respect to the horizontal coordinates in Band 6" (Discussion)
   - fitting: _not stated_
   - validation: Good agreement; chi2 decreases 10-15% by rotating SW image 2-5 deg  
  > "the fit improves slightly (a decrease of 10–15% in the $\chi^2$) by rotating the SW image by 2$-$5 degrees" (Discussion)
5. **Faraday rotation fit of differential EVPA**: Thin Faraday screen (phi ∝ lambda^2) fit to NE-SW EVPA difference at each time bin  
  > "we used a model of thin Faraday screen (i.e., $\phi \propto \lambda^2$ law) to fit the EVPA difference between the two images at each time bin." (Faraday rotation)
   - fitting: _not stated_
   - validation: _not stated_

## Software

- **CASA** : calibration, tclean imaging, immath  
  > "The data calibration was done within the Common Astronomy Software Applications (CASA[^1]) package" (Observations)
- **uvmultifit** : visibility-domain fitting of Stokes parameters  
  > "The fitting was performed with the Python-based task `uvmultifit` (cite: mar14)" (Results)

## Numeric results

| quantity | value | uncertainty | units | step | quote |
|---|---|---|---|---|---|
| Peak fractional polarization SW | 14 | not stated | % | 2 | a fractional polarization peak of 14% (in the SW image, with a flux density of 2.34 Jy) |
| Peak fractional polarization NE | 5.4 | not stated | % | 2 | 5.4% (in the NE image, with a flux density of 2.10 Jy) |
| NE EVPA | -24 | not stated | degrees | 2 | its EVPA ($-24$ degrees) is rotated $\sim$15 degrees with respect to that of the SW |
| Rate of differential EVPA increase | ~2 | not stated | degrees per hour | 3 | a clear linear increase in the EVPA difference between the two images (see Fig. [2](#fig:curves)A) at a rate of about two degrees per hour |
| Delta alpha change | -0.19 to -0.05 | not stated | dimensionless | 3 | we estimate a variation from $\Delta\alpha \sim -0.19$ to $\Delta\alpha \sim -0.05$ between the start and end of the observations |
| Weighted mean RM of differential NE-SW | 3.4e4 | 1.7e4 | rad m^-2 | 5 | The weighted average of all the RM measurements is $(3.4 \pm 1.7)\times 10^4$ rad m$^{-2}$. |
| Maximum Rpol | ~0.1 | not stated | dimensionless | 4 | The maximum $R_{pol}$ measured in our 2019 observations ($\sim 0.1$; Fig. [4](#fig:diffpol)) |

## Qualitative findings

- Polarization intensity appears suppressed during the gamma-ray flare; consistent with stronger magnetic turbulence  
  > "the polarization intensity of the blazar was somehow suppressed during the $\gamma$-ray flare" (Discussion)

## Claim tuples

- H: Do the NE and SW images show different polarization reflecting intrinsic evolution? | E: Full-pol imaging of both images | R: NE fractional polarization ~3 times lower than SW; EVPA offset ~15 deg | F: Intrinsic polarization evolved within the ~26 day delay; polarization suppressed during flare | **supported**
- H: Is there intra-hour polarization variability? | E: uvmultifit on scan segments | R: EVPA difference rising ~2 deg/h; relative fractional polarization changed ~10% | F: Significant variability on ~1 h timescales, consistent with magnetic turbulence | **supported**
- H: Does full-pol calibration validate differential polarimetry? | E: Compare Rpol from XX/YY fits to full-pol prediction | R: Good agreement | F: Technique validated | **supported**

## Reasoning

- Why this data: _not stated_
- Why this method: _not stated_
- How they decided it was enough: _not stated_
- Limitation (authors): Faraday rotation analysis is limited; RM only tentative and consistent with zero at 2 sigma  
  > "All the fitted values are compatible with zero at a 2$\sigma$ level" (Faraday rotation)
- Caveat (inferred, ours): Turbulent-cell interpretation rests on a single epoch
- Caveat (inferred, ours): Cannot tell which lensed image changes its spectral index
- Caveat (inferred, ours): Time-delay comparison assumes negligible differential effects from microlensing or the lens

## Reproducibility

- Data public (paper): ALMA project data cited with project code  
  > "This paper makes use of the following ALMA data: ADS/JAO.ALMA#2018.1.00692.S." (Acknowledgements)
- Products in archive: _not stated_
- Missing: CASA version and tclean parameters
- Missing: uvmultifit configuration and error treatment
- Missing: Fermi-LAT light-curve processing
- Data volume (inferred): ~10-50 GB raw (two-hour full-pol Band 6 observation)
- Score (inferred): 5/5, Short letter; steps described qualitatively with many imaging/fit parameters missing, though data are a single public project.
- Rediscovery candidate: yes, Public single-project data, simple recipe, numeric results (polarization fractions, EVPA rate).

## Links

- Method: (cite: mar14) (uvmultifit visibility fitting)
- Method: (cite: mar16) (differential polarimetry formalism)
- Method: (cite: Nagai) (ALMA full-polarization calibration)
- Companion: (cite: mar15) (earlier ALMA differential polarimetry and Faraday rotation of PKS 1830-211)
- Related: Fermi-LAT

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
 "numeric_results": 7,
 "numeric_problems": 0,
 "fill": {
  "facts": 69,
  "stated": 34,
  "rate": 0.493
 },
 "evidence_ok": true
}
```
