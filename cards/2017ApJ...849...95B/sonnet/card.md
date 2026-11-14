# Fermi Non-detections of Four X-Ray Jet Sources and Implications for the IC/CMB Mechanism

`2017ApJ...849...95B` | The Astrophysical Journal 2017 | first author: Breiding, Peter | arXiv: 1710.04250 | DOI: 10.3847/1538-4357/aa907a

Card schema 1.0 | model claude-sonnet-5-5 | depth light | type multi_facility_alma_minor

## Science

- Fields: agn_and_quasars
- Question: Do Fermi/LAT gamma-ray upper limits for the kpc-scale X-ray jets of four quasars violate the gamma-ray flux predicted by the IC/CMB model?  
  > "This paper follows these works for four more MSC jets where the X-ray emission has been previously modeled as due to IC/CMB." (Using the Fermi/LAT to test the IC/CMB model)
- Target **PKS 1136-135**: coordinates _not stated_; z/distance z = 0.560  
  > "| 1136-135 | 0.560 | 6.26 | 8.45$^{b}$ |" (Table 1); distance from literature (as noted in Table 1)  
  > "| 1136-135 | 0.560 | 6.26 | 8.45$^{b}$ |" (Table 1)
- Target **PKS 1229-021**: coordinates _not stated_; z/distance z = 1.05  
  > "| 1229-021 | 1.05 | 7.91 | 8.70$^{b}$ |" (Table 1); distance from literature (as noted in Table 1)  
  > "| 1229-021 | 1.05 | 7.91 | 8.70$^{b}$ |" (Table 1)
- Target **PKS 1354+195**: coordinates _not stated_; z/distance z = 0.720  
  > "| 1354+195 | 0.720 | 7.03 | 9.44$^{a}$ |" (Table 1); distance from literature (as noted in Table 1)  
  > "| 1354+195 | 0.720 | 7.03 | 9.44$^{a}$ |" (Table 1)
- Target **PKS 2209+080**: coordinates _not stated_; z/distance z = 0.480  
  > "| 2209+080 | 0.480 | 5.80 | ... |" (Table 1); distance from literature (as noted in Table 1)  
  > "| 2209+080 | 0.480 | 5.80 | ... |" (Table 1)

## Data provenance

- ALMA projects: 2015.1.00932.S, 2016.1.01481.S, 2016.1.01250.S
- bands: Band 3 and Band 6  
  > "Both programs included observations at band 3 and 6" (2.4 ALMA)
- frequencies and spectral setup: _not stated_
- continuum bandwidth: _not stated_
- arrays: _not stated_
- configurations: _not stated_
- baselines: _not stated_
- angular resolution: _not stated_
- max recoverable scale: _not stated_
- sensitivity: _not stated_
- time on source: 66-454 s per source/band (Table 3)  
  > "| 2209+080 |  3   |  3,4  | 97.5  |  375  |    246    | 0.52$\times$0.35$''$ |" (Table 3)
- observing dates: _not stated_
- pi or archival as stated: PKS 1136-135 band 3 data from a calibrator observation of another project (PI C. Peroux), provided by the PI  
  > "this data was kindly made available to us by the PI" (2.4 ALMA)
- Other facility **Fermi/LAT**: gamma-ray upper limits  
  > "Here we present *Fermi*/LAT flux density upper limits for the X-ray jets of four additional sources" (abstract)
- Other facility **VLA**: archival radio imaging of jet knots  
  > "we used the deepest available archival *VLA* imaging of sufficient quality in bands L, C, X, and U" (2.2 VLA)
- Other facility **HST**: new optical/IR imaging of PKS 2209+080 (GO-13676)  
  > "PKS 2209+080 was observed as part of our *HST* program GO-13676 (PI: Meyer)" (2.5 HST)
- Other facility **VLBA (MOJAVE)**: archival 15 GHz images for proper motions of PKS 1354+195  
  > "We downloaded the fully-reduced `fits` images from the MOJAVE website" (2.3 VLBI)
- External data: HST knot flux densities for 1354+195  
  > "Archival *HST* flux densities for the individual knots of 1354+195 were taken from (cite: sambruna2004)" (2.5 HST) [from (cite: sambruna2004)]
- External data: HST flux densities for 1136-135  
  > "from (cite: cara2013) for 1136-136" (2.5 HST) [from (cite: cara2013)]
- External data: HST flux densities for 1229-021  
  > "from (cite: tavecchio2007) for 1229-021" (2.5 HST) [from (cite: tavecchio2007)]
- External data: 2209+080 X-ray flux density  
  > "where we used their X-ray flux density in our SED" (4.4 PKS 2209+080) [from (cite: jorstad2006)]

## Processing

### Calibration

- pipeline or manual: Reduced with the provided scriptForPI.py, then self-calibration  
  > "the data was first reduced using the provided `scriptForPI.py` script, which produces a calibrated measurement set appropriate for imaging with `clean`" (2.4 ALMA)
- casa version: _not stated_
- pipeline version: _not stated_
- archive products used as is: _not stated_
- flux calibrator: _not stated_
- flux scale uncertainty: _not stated_
- self calibration: Several rounds of phase-only self-cal, then a final amplitude and phase round  
  > "several rounds of phase-only (non-cumulative) self-calibration were applied before a final (cumulative) round of amplitude and phase self-calibration" (2.4 ALMA)

### Imaging

- task: clean in mfs mode, nterms=1  
  > "`clean` was used in `mfs` mode, with `nterms=1` and briggs weighting with `robust=0.5`." (2.4 ALMA)
- deconvolver: _not stated_
- weighting robust: Briggs, robust=0.5  
  > "`clean` was used in `mfs` mode, with `nterms=1` and briggs weighting with `robust=0.5`." (2.4 ALMA)
- uv taper: _not stated_
- cell size: _not stated_
- image size: _not stated_
- masking: _not stated_
- multiscale scales: _not stated_
- continuum subtraction: _not stated_
- line free channels: _not stated_
- primary beam correction: RMS from PB-corrected image; uncorrected images in figures  
  > "The final RMS measurements correspond to the primary-beam-corrected image, though we use the uncorrected images in the figures." (2.4 ALMA)
- array combination: For 2209+080, cycle 4 and cycle 3 data combined after core subtraction  
  > "we combined together and imaged the somewhat lower-resolution cycle 4 data with the cycle 3 data, after core subtraction" (2.4 ALMA)
- smoothing: _not stated_
- final beam: _not stated_
- final rms: _not stated_

### Inherited from earlier work

- Radio core/lobe SED decomposition and synchrotron peak fitting  
  > "we decomposed the radio spectrum of these sources into the extended (isotropic) “lobe” component and beamed “core” component as in (cite: meyer2011)" (2.1 Sample Properties) [from (cite: meyer2011)]
- Procedure for finding new Fermi point sources via TS residual maps  
  > "following the procedure outlined in (cite: meyer2015)" (2.6 Fermi) [from (cite: meyer2015)]
- IC/CMB shifting equations  
  > "first derived in (cite: georganopoulos2006)" (Appendix) [from (cite: georganopoulos2006)]

### Not stated but needed to reproduce (our reading)

- Which ALMA execution blocks, calibrators and self-cal solution intervals were used
- Cell size, image size, masking, clean threshold
- Method and parameters of core subtraction in the ALMA images
- How knot fluxes were measured in ALMA images (apertures)
- Fermi MET end for PKS 1354+195 is garbled

## Analysis recipe

1. **Reduce and image ALMA data**: scriptForPI calibration, self-calibration, clean mfs imaging  
  > "`clean` was used in `mfs` mode, with `nterms=1` and briggs weighting with `robust=0.5`." (2.4 ALMA)
   - software: CASA
   - parameter: robust=0.5, nterms=1  
  > "`clean` was used in `mfs` mode, with `nterms=1` and briggs weighting with `robust=0.5`." (2.4 ALMA)
   - fitting: _not stated_
   - validation: _not stated_
2. **Fermi upper limits**: Binned likelihood with target added at fixed photon index; limits per five energy bands  
  > "our target source of interest was added to the model file with a fixed photon index" (2.6 Fermi)
   - software: make3FGLxml.py
   - parameter: ROI 10 deg (7 deg for PKS 1136-135), 100 MeV-100 GeV  
  > "a $10^{\circ}$ region of interest (ROI), an energy cut of 100 MeV-100 GeV" (2.6 Fermi)
   - assumption: Photon index derived from the IC/CMB model  
  > "These photon indices were derived from the implied gamma-ray index of the IC/CMB model." (2.6 Fermi)
   - fitting: maximum likelihood  
  > "After obtaining converged fits following the maximum likelihood optimizations with the initial model, Test Statistic (TS) residuals maps with $1^{\circ}$ spatial binning were created" (Data Analysis, Fermi)
   - validation: _not stated_
3. **Compare IC/CMB prediction with limits**: Fit synchrotron power law with exponential cutoff, shift in frequency and luminosity by B/delta to match X-rays, combine bands with inverse normal method  
  > "Combining the individual band results using the inverse normal method, we find the IC/CMB model is ruled out" (3 Results)
   - assumption: Equipartition magnetic field for delta limit  
  > "the upper limit on the Doppler factor assuming an equipartition magnetic field" (3 Results)
   - fitting: _not stated_
   - validation: _not stated_

## Software

- **CASA** 4.7.0: VLA and ALMA reduction and imaging; HST flux measurement with viewer  
  > "All sources were analyzed using `CASA` version `4.7.0`." (2.2 VLA)
- **WISE** : VLBI proper motion analysis  
  > "used the publicly available Wavelet Image Segmentation and Evaluation (WISE) code" (2.3 VLBI)
- **make3FGLxml.py** : Fermi model file construction  
  > "using the publicly available `make3FGLxml.py` script" (2.6 Fermi)
- **iraf** : ellipse/bmodel galaxy models (unsuccessful)  
  > "models produced by `iraf` tasks `ellipse` and `bmodel` left large residual errors" (2.5 HST)

## Numeric results

| quantity | value | uncertainty | units | step | quote |
|---|---|---|---|---|---|
| IC/CMB rejection significance PKS 1136-135 | 14.3 | not stated | sigma | 3 | ruled out at the $14.3\sigma$, $6.1\sigma$, $4.7\sigma$, and $>15.2\sigma$-levels |
| IC/CMB rejection significance PKS 1229-021 | 6.1 | not stated | sigma | 3 | ruled out at the $14.3\sigma$, $6.1\sigma$, $4.7\sigma$, and $>15.2\sigma$-levels |
| IC/CMB rejection significance PKS 1354+195 | 4.7 | not stated | sigma | 3 | ruled out at the $14.3\sigma$, $6.1\sigma$, $4.7\sigma$, and $>15.2\sigma$-levels |
| IC/CMB rejection significance PKS 2209+080 | >15.2 | not stated | sigma | 3 | ruled out at the $14.3\sigma$, $6.1\sigma$, $4.7\sigma$, and $>15.2\sigma$-levels |
| PKS 1354+195 apparent proper motions | 4.00, 4.95, 6.1 | 0.24, 0.24, 4.7 | c | 0 | apparent proper motions of 4.00$\pm$0.24$c$, 4.95$\pm$0.24$c$ and 6.1$\pm$4.7$c$ |

## Qualitative findings

- PKS 2209+080 shows a newly detected optical jet and a host with tidal tail suggesting a merger  
  > "our *HST* observations for PKS 2209+080 show a newly detected optical jet with possible tidal tails in the host galaxy" (Summary & Conclusions)

## Claim tuples

- H: Does the IC/CMB model explain the X-ray jets? | E: Fermi/LAT upper limits compared with IC/CMB predictions fixed by X-ray flux | R: Limits lie below predictions at 4.7 to >15.2 sigma | F: IC/CMB ruled out for all four jets | **supported**
- H: Are the jets highly aligned as IC/CMB requires? | E: Radio core dominance versus crossing frequency, and X-ray dominance | R: Sources not in blazar region | F: Jets fairly misaligned | **partially**

## Reasoning

- Why this data: _not stated_
- Why this method: _not stated_
- Alternative: Second synchrotron component or hadronic models remain possible alternatives  
  > "we must consider alternative emission mechanisms such as a second population of electrons producing a second synchrotron component or hadronic emission models" (Summary & Conclusions)
- How they decided it was enough: _not stated_
- Limitation (authors): Only ~40% of Cycle 3 program completed; not all Cycle 4 data released  
  > "only about 40% of the C-rated cycle 3 program was completed" (2.4 ALMA)
- Limitation (authors): PKS 1354+195 knot A X-ray flux in dispute  
  > "knot A is in fact not detectable separate from the bright quasar core" (4.3 PKS 1354+195)
- Caveat (inferred, ours): ALMA used only for SED constraints; fluxes without apertures
- Caveat (inferred, ours): Tests depend on the assumed synchrotron model and equipartition
- Caveat (inferred, ours): 1354+195 conclusion weaker given knot A dispute

## Reproducibility

- Data public (paper): ALMA project codes listed; 1136-135 data provided by PI  
  > "this data was kindly made available to us by the PI" (2.4 ALMA)
- Products in archive: _not stated_
- Missing: Image cell/size and masking
- Missing: Aperture definitions for knot fluxes
- Missing: Fermi tool versions
- Data volume (inferred): Tens of GB for ALMA plus Fermi and VLA archival data
- Score (inferred): 4/5, ALMA role minor and imaging details sparse; Fermi analysis well described.
- Rediscovery candidate: no, Main results rely on Fermi analysis and external SED data rather than ALMA; ALMA recipe incomplete.

## Links

- Method: (cite: meyer2015) (Fermi analysis procedure)
- Method: (cite: georganopoulos2006) (IC/CMB shifting equations)
- Method: (cite: meyer2011) (radio SED decomposition)
- Companion: (cite: meyer2014) (3C 273 Fermi limits)
- Companion: (cite: meyer17) (PKS 0637-752 Fermi limits)
- Related: MOJAVE
- Related: Fermi 3FGL

## Checks

```json
{
 "quotes": 58,
 "quotes_ok": 58,
 "quote_pass_rate": 1.0,
 "quotes_too_long": 0,
 "unsupported_facts": 0,
 "project_codes": 3,
 "codes_not_in_text": [],
 "codes_not_in_obscore": [],
 "obscore_codes_not_in_card": [],
 "codes_printed_but_missing": [],
 "numeric_results": 5,
 "numeric_problems": 0,
 "fill": {
  "facts": 84,
  "stated": 46,
  "rate": 0.548
 },
 "evidence_ok": true
}
```
