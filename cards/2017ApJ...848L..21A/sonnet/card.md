# The Electromagnetic Counterpart of the Binary Neutron Star Merger LIGO/Virgo GW170817. VI. Radio Constraints on a Relativistic Jet and Predictions for Late-time Emission from the Kilonova Ejecta

`2017ApJ...848L..21A` | The Astrophysical Journal Letters 2017 | first author: Alexander, K. D. | arXiv: 1710.05457 | DOI: 10.3847/2041-8213/aa905d

Card schema 1.0 | model claude-sonnet-5-5 | depth light | type multi_facility_alma_minor

## Science

- Fields: transients, high_z_galaxies
- Question: Do radio/mm observations of GW170817 constrain a relativistic SGRB jet (on- or off-axis) and what late-time radio emission is expected from the kilonova ejecta?  
  > "we use the radio data to place tight constraints on the presence of an on- or off-axis jet." (Introduction)
- Target **GW170817 optical counterpart (AT2017gfo) and host NGC 4993**: coordinates _not stated_; z/distance 39.5 Mpc  
  > "corresponding to $\lesssim 40$ pc at a distance of 39.5 Mpc" (Observations); distance from _not stated_

## Data provenance

- ALMA projects: 2016.A.00043.T, 2016.A.00046.T
- bands: Band 3  
  > "we used the Band 3 receiver system in wideband continuum mode" (Observations)
- frequencies and spectral setup: two spectral windows of 4 GHz width centered at 91.5 and 103.5 GHz  
  > "we used the Band 3 receiver system in wideband continuum mode, with two spectral windows of 4 GHz width centered at frequencies of 91.5 and 103.5 GHz" (Observations)
- continuum bandwidth: _not stated_
- arrays: _not stated_
- configurations: _not stated_
- baselines: _not stated_
- angular resolution: beam 0.21" in ALMA data (Table: 0.3x0.2 to 0.2x0.1 arcsec)  
  > "with a beam size of 0.21"" (Observations)
- max recoverable scale: _not stated_
- sensitivity: image RMS 8.5 uJy for combined data at the transient position  
  > "with an image RMS of 8.5 $\mu$Jy at that position" (Observations)
- time on source: 30 min, 30 min, 1 hr, 1 hr (epochs at 2.4, 9.4, 15.3, 30.3 d)  
  > "The first two observations each lasted 30 min, while the second two lasted 1 hr each." (Observations)
- observing dates: 2017 Aug 19.9, Aug 27.0, Sep 1.8, Sep 16.9  
  > "ALMA & 2017 Sep 16.9 & 30.34 & 97.5" (Table 1)
- pi or archival as stated: PI: Alexander  
  > "programs 2016.A.00043.T and 2016.A.00046.T; PI: Alexander" (Observations)
- Other facility **VLA**: cm-band (4-18 GHz) observations from 0.57 to 39 d  
  > "We initiated radio observations of the position of the optical counterpart with the Karl G. Jansky Very Large Array" (Observations)
- External data: X-ray light curve used jointly with radio to constrain afterglow models  
  > "which match the X-ray light curve (cite: DECamPaper5)" (Off-axis Afterglow Models) [from (cite: DECamPaper5) Margutti et al. 2017]
- External data: Kilonova ejecta masses and velocities from UV/optical/NIR modeling  
  > "a “blue” component with $M_{\rm ej}\approx 0.02$ M$_{\odot}$ and $v_{\rm ej}\approx 0.3c$" (Predictions) [from (cite: DECamPaper2; DECamPaper3; DECamPaper4)]
- Simulation/model as data: BOXFIT v2 off-axis afterglow light curves over grids of E_K, n, theta_obs, epsilon_B  
  > "we use the afterglow modeling code `BOXFIT` (v2; (cite: vzm+10; vm12))" (Off-axis Afterglow Models)

## Processing

### Calibration

- pipeline or manual: custom pipeline based on CASA  
  > "We calibrated and imaged the data using a custom pipeline based on CASA" (Observations)
- casa version: _not stated_
- pipeline version: _not stated_
- archive products used as is: _not stated_
- flux calibrator: B1334-127 (bandpass and flux)  
  > "using the quasar B$1334-127$ as the bandpass and flux density calibrator" (Observations)
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
- final rms: 8.5 uJy (all ALMA data combined); per-epoch 13-25 uJy/beam  
  > "with an image RMS of 8.5 $\mu$Jy at that position" (Observations)

### Inherited from earlier work

- Afterglow modeling setup (BOXFIT parameter grids) as in X-ray paper  
  > "as described in (cite: DECamPaper5); we fix $\epsilon_e=0.1$" (Off-axis Afterglow Models) [from (cite: DECamPaper5)]
- Median SGRB p=2.4 and epsilon_B=0.01  
  > "the median values for SGRBs (cite: fbm+15)" (Off-axis Afterglow Models) [from (cite: fbm+15)]

### Not stated but needed to reproduce (our reading)

- ALMA phase and gain calibrators, CASA version, and custom pipeline details
- Imaging parameters (weighting, robust, cell/image size, deconvolver)
- Parameter grid ranges and fitting/comparison criteria for BOXFIT
- Kilonova radio emission model and equations used for Figure 4
- ALMA flux scale uncertainty

## Analysis recipe

1. **Calibrate and image ALMA Band 3 data; measure flux at transient position**: Custom CASA-based pipeline; combine both subbands and all four epochs to test for emission  
  > "We combined the data in both subbands and all four epochs and we do not detect emission at the optical transient position" (Observations)
   - software: CASA
   - fitting: _not stated_
   - validation: _not stated_
2. **Compare radio limits/detections with on-axis afterglow models**: Standard afterglow synchrotron model in constant density medium  
  > "we utilize the standard afterglow synchrotron model in a constant density medium (cite: gs02)" (Afterglow constraints)
   - assumption: epsilon_e=0.1, eta_gamma=0.1  
  > "(assuming an efficiency of $\eta_\gamma=0.1$)" (On-axis Afterglow Models)
   - fitting: _not stated_
   - validation: _not stated_
3. **Constrain off-axis jet parameters**: BOXFIT grid over E_K, n, theta_j, theta_obs, epsilon_B; compare with radio and X-ray  
  > "for a wide range of kinetic energies, densities, jet opening angles, observer orientations, and $\epsilon_B$" (Off-axis Afterglow Models)
   - software: BOXFIT
   - parameter: p=2.2 adopted; epsilon_e=0.1  
  > "All simulations discussed for the remainder of this paper assume $p=2.2$" (Off-axis Afterglow Models)
   - fitting: _not stated_
   - validation: _not stated_
4. **Predict kilonova ejecta radio emission**: Blue and red ejecta components with fiducial n=1e-3 cm^-3 and range from jet modeling  
  > "for a fiducial density of $n=1\times10^{-3}$ cm$^{-3}$ (solid lines)" (Predictions)
   - fitting: _not stated_
   - validation: _not stated_

## Software

- **CASA** : VLA and ALMA calibration and imaging  
  > "We analyzed and imaged the VLA data using standard CASA routines" (Observations)
- **pwkit** : imtool fitting of flux density and position for detections  
  > "we fit the flux density and position of the emission using the imtool program within the pwkit package" (Observations)
- **BOXFIT** v2: off-axis afterglow modeling  
  > "we use the afterglow modeling code `BOXFIT` (v2; (cite: vzm+10; vm12))" (Off-axis Afterglow Models)
- **Numpy** : listed in software section  
  > "CASA, Numpy, pwkit" (Software)

## Numeric results

| quantity | value | uncertainty | units | step | quote |
|---|---|---|---|---|---|
| ALMA combined image RMS at transient position | 8.5 | not stated | uJy | 1 | with an image RMS of 8.5 $\mu$Jy at that position |
| VLA 6 GHz flux at 19.47 d | 19 | 6 | uJy | 0 | with a flux density of $19\pm 6$ $\mu$Jy ($3.1\sigma$ significance) |
| VLA 6 GHz flux at 39.23 d | 27 | 6 | uJy | 0 | with a flux density of $27\pm6$ $\mu$Jy |
| Observer viewing angle (jet+X-ray) | 20-40 | not stated | deg | 3 | tightens the viewing angle constraint to $20^{\circ}\lesssim\theta_{\rm obs}\lesssim40^{\circ}$ |
| Circumbinary density | 1e-4 to 1e-2 | not stated | cm^-3 | 3 | low densities $n\sim 10^{-4}-10^{-2}$ cm$^{-3}$ |

## Qualitative findings

- No cm/mm emission at the counterpart position until faint 6 GHz detections at ~19 and ~39 d  
  > "We detect faint emission at 6 GHz at 19.47 and 39.23 days after the merger, but not in an earlier observation at 2.46 d." (abstract)

## Claim tuples

- H: Is an on-axis SGRB jet consistent with the data? | E: Compare radio limits with on-axis afterglow models | R: All on-axis jets with E_K,iso >~1e48 erg are ruled out | F: On-axis jet excluded | **supported**
- H: Can an off-axis jet explain radio and X-ray data? | E: BOXFIT grids compared to radio and X-ray | R: E ~1e49-1e50 erg, n ~1e-4-1e-2, theta_obs 20-40 deg | F: Data consistent with an off-axis SGRB afterglow | **supported**
- H: Will kilonova ejecta produce detectable late radio emission? | E: Predict emission from blue/red ejecta components | R: Blue component detectable with VLA ~5 yr for n=1e-2; otherwise needs ngVLA/SKA | F: Long-term monitoring is warranted | **partially**

## Reasoning

- Why this data: _not stated_
- Why this method: _not stated_
- Alternative: p=2.4 models over-predict radio emission, so p=2.2 adopted  
  > "consistently over-predict the radio emission at a comparable epoch" (Off-axis Afterglow Models)
- How they decided it was enough: _not stated_
- Limitation (authors): Bad weather may cause flux decorrelation at high frequency in the Sep 5 epoch  
  > "these data may suffer from flux decorrelation" (Observations)
- Caveat (inferred, ours): Only p, epsilon_e fixed; no formal posterior or fit statistics
- Caveat (inferred, ours): Marginal 3.1 sigma 6 GHz detection
- Caveat (inferred, ours): ALMA processing details sparse

## Reproducibility

- Data public (paper): _not stated_
- Products in archive: _not stated_
- Code: pwkit available at github  
  > "Available at <https://github.com/pkgw/pwkit>." (footnote 2)
- Missing: ALMA imaging parameters
- Missing: BOXFIT grid definitions and likelihood criteria
- Missing: KN radio model details
- Data volume (inferred): ~10-50 GB for four ALMA Band 3 epochs
- Score (inferred): 3/5, ALMA part is brief non-detection; model fitting loosely specified.
- Rediscovery candidate: no, ALMA contribution is a non-detection and modeling recipe is incomplete.

## Links

- Method: (cite: vzm+10; vm12) (BOXFIT afterglow code)
- Companion: (cite: DECamPaper5) Margutti et al. 2017 (X-ray analysis used jointly)
- Companion: (cite: DECamPaper8) Blanchard et al. 2017 (host galaxy radio emission)
- Related: VLA/17A-218
- Related: TTRA0001
- Related: VLA 17A-231

## Checks

```json
{
 "quotes": 44,
 "quotes_ok": 44,
 "quote_pass_rate": 1.0,
 "quotes_too_long": 0,
 "unsupported_facts": 0,
 "project_codes": 2,
 "codes_not_in_text": [],
 "codes_not_in_obscore": [],
 "obscore_codes_not_in_card": [],
 "codes_printed_but_missing": [],
 "numeric_results": 5,
 "numeric_problems": 0,
 "fill": {
  "facts": 71,
  "stated": 32,
  "rate": 0.451
 },
 "evidence_ok": true
}
```
