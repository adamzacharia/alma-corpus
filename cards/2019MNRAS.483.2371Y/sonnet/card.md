# Does HL Tau disc polarization in ALMA band 3 come from radiatively aligned grains?

`2019MNRAS.483.2371Y` | Monthly Notices of the Royal Astronomical Society 2019 | first author: Yang, Haifeng | arXiv: 1811.11897 | DOI: 10.1093/mnras/sty3263

Card schema 1.0 | model claude-sonnet-5-5 | depth light | type theory_or_simulation_compared_to_alma

## Science

- Fields: protoplanetary_disks
- Question: Can radiatively aligned grains (or aerodynamically aligned grains) explain the HL Tau ALMA Band 3 (~3 mm) polarization pattern?  
  > "We conclude that neither of these two mechanisms alone can explain the data and the origin of the 3 mm polarization remains a mystery." (abstract)
- Target **HL Tau**: coordinates _not stated_; z/distance _not stated_; distance from _not stated_

## Data provenance

- ALMA projects: 2011.0.00015.SV, 2016.1.00115.S, 2016.1.00162.S
- bands: Band 3 (~3 mm) polarization; Band 7 for comparison  
  > "HL Tau by ALMA in Band 3 ($\sim 3$ mm; (cite: Kataoka2017)" (Introduction)
- frequencies and spectral setup: _not stated_
- continuum bandwidth: _not stated_
- arrays: _not stated_
- configurations: _not stated_
- baselines: _not stated_
- angular resolution: Band 3 polarization beam 0.445"x0.294"; high-resolution Band 3 continuum 0.0853"x0.0611"  
  > "the beam used for the Band 3 polarization observation ($0_\cdot^{\prime\prime}445\times 0_\cdot^{\prime\prime}294$)" (4.2 Neither radiative nor aerodynamic alignment)
- max recoverable scale: _not stated_
- sensitivity: _not stated_
- time on source: _not stated_
- observing dates: _not stated_
- pi or archival as stated: _not stated_
- External data: HL Tau Band 3 polarization data (observed pattern, 21 sigma peak)  
  > "the signal-to-noise ratio was reported to be $21~\sigma$ (cite: Kataoka2017)" (3.3 Differences between circular and elliptical patterns) [from (cite: Kataoka2017)]
- External data: HL Tau high-resolution Band 3 continuum used as Stokes I model; inclination 46.72 deg  
  > "we use the much higher resolution ($0_{\cdot}^{\prime\prime}0853\times 0_\cdot^{\prime\prime}0611$) ALMA Band 3 continuum data from (cite: ALMA2015) as the Stokes I model" (4.1 The model) [from (cite: ALMA2015)]
- External data: HL Tau Band 7 polarization (~0.6%)  
  > "well above the $\sim 0.6\%$ polarization detected in Band 7 and has a completely different pattern (cite: Stephens2017)" (4.4 Polarization spectrum) [from (cite: Stephens2017)]
- Simulation/model as data: Analytic models of polarization from radiative and aerodynamic alignment, beam-convolved, with p0=2%  
  > "assume a maximum (or intrinsic) polarization degree of $p_0=2\%$, comparable to the maximum observed value" (4.1 The model)

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

### Not stated but needed to reproduce (our reading)

- Exact polarization data products and reduction used (from Kataoka et al. 2017)
- Disk position angle used for the models
- Normalization procedure of modelled polarized intensity
- Which of the three ALMA projects supply which dataset

## Analysis recipe

1. **Derive analytic polarization patterns**: Geometric/dipole-approximation formulae for polarization angle and degree vs azimuth for radiative, aerodynamic, magnetic alignment  
  > "The azimuthal variation of the polarization degree is then computed based on equations ([\[eq:pinc_o\]](#eq:pinc_o)) and ([\[eq:pinc_p\]](#eq:pinc_p))" (4.1 The model)
   - parameter: p0 = 2%, i = 46.72 deg  
  > "assume a maximum (or intrinsic) polarization degree of $p_0=2\%$" (4.1 The model)
   - assumption: Optically and geometrically thin disk; radiation flux radial; Stokes I from high-resolution Band 3 image  
  > "under the assumption of a optically and geometrically thin (dust) disk" (3.3 Differences between circular and elliptical patterns)
   - fitting: _not stated_
   - validation: _not stated_
2. **Convolve and compare with data**: Convolve model Stokes I, Q, U with the polarization beam; compare angle differences at >=5 sigma locations and polarized intensity maps  
  > "at all locations on the disk where the polarization is detected at at least $5\sigma$ level" (4.2 Neither radiative nor aerodynamic alignment)
   - fitting: _not stated_
   - validation: _not stated_

## Software

- **Astropy** : acknowledged as used in research  
  > "This research made use of Astropy (cite: Astropy) and matplotlib (cite: Matplotlib)." (Acknowledgement)
- **matplotlib** : acknowledged as used in research  
  > "This research made use of Astropy (cite: Astropy) and matplotlib (cite: Matplotlib)." (Acknowledgement)

## Numeric results

| quantity | value | uncertainty | units | step | quote |
|---|---|---|---|---|---|
| Max polarization angle difference elliptical vs circular, i=45 deg | ~20 (19.5) | not stated | deg | 1 | close to the maximum values ($\pm 19.5^\circ$) expected between the elliptical and circular pattern |
| Major-axis polarization, aerodynamic alignment, i=45, p0=2% | 1.1 | not stated | % | 1 | the polarization degree on the major axis is $p=1.1\%$ (for the adopted $p_0=2\%$) |
| Disk-averaged polarization fraction, i=45, uniform case | 0.172 p0 | not stated | dimensionless | 1 | ${\bar p}=(\sqrt{2}-1)/(\sqrt{2}+1) p_0\approx 0.172\,p_0$ for $i=45^\circ$ |

## Qualitative findings

- Radiative alignment gives circular, not elliptical, pattern; aerodynamic alignment gives elliptical pattern matching orientations better, but both predict azimuthal variation of polarized intensity not seen.  
  > "However, a strong azimuthal variation in polarized intensity is expected for both the radiative and aerodynamic alignment, but not observed in the HL Tau disk in ALMA Band 3." (abstract)

## Claim tuples

- H: Radiative alignment explains HL Tau Band 3 polarization | E: Compared beam-convolved circular-pattern model to data | R: Angle differences bimodal near +/-19.5 deg; wrong azimuthal intensity variation | F: Radiative alignment disfavoured | **refuted**
- H: Aerodynamic alignment explains the data | E: Beam-convolved elliptical model compared with data | R: Orientations better matched but polarized intensity distribution poor | F: Not sufficient alone | **refuted**

## Reasoning

- Why this data: _not stated_
- Why this method: _not stated_
- Alternative: Magnetic alignment rejected because it predicts polarization perpendicular to elliptical iso-intensity contours  
  > "magnetic alignment is the least likely possibility for producing the Band 3 polarization observed in HL Tau disk" (4.1 The model)
- How they decided it was enough: _not stated_
- Limitation (authors): No self-consistent computation of emission plus scattering; optical depth effects not quantified  
  > "A self-consistent computation of the polarization from both direct emission and scattering by aerodynamically aligned grains is beyond the scope of this work." (4.3)
- Caveat (inferred, ours): Only qualitative models; no fitting or uncertainties
- Caveat (inferred, ours): Optically thin assumption may fail in HL Tau
- Caveat (inferred, ours): Intrinsic p0 fixed at 2%

## Reproducibility

- Data public (paper): _not stated_
- Products in archive: _not stated_
- Missing: Model code not released
- Missing: Data reduction details deferred to Kataoka et al. 2017 and ALMA 2015
- Data volume (inferred): ~50-100 GB if raw data reprocessed; published images suffice
- Score (inferred): 3/5, Analytic formulae given, but data products and comparison details are from other papers and no code is released.
- Rediscovery candidate: no, Mainly theory; data processing is not described.

## Links

- Companion: (cite: Kataoka2017) (Source of HL Tau Band 3 polarization data)
- Companion: (cite: Stephens2017) (HL Tau Band 7 polarization)

## Checks

```json
{
 "quotes": 26,
 "quotes_ok": 26,
 "quote_pass_rate": 1.0,
 "quotes_too_long": 0,
 "unsupported_facts": 0,
 "project_codes": 3,
 "codes_not_in_text": [],
 "codes_not_in_obscore": [],
 "obscore_codes_not_in_card": [],
 "codes_printed_but_missing": [],
 "numeric_results": 3,
 "numeric_problems": 0,
 "fill": {
  "facts": 60,
  "stated": 16,
  "rate": 0.267
 },
 "evidence_ok": true
}
```
