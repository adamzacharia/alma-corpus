# Measuring turbulence in TW Hydrae with ALMA: methods and limitations

`2016A&A...592A..49T` | Astronomy and Astrophysics 2016 | first author: Teague, R. | arXiv: 1606.00005 | DOI: 10.1051/0004-6361/201628550

Card schema 1.0 | model claude-sonnet-5-5 | depth full | type observational_alma_primary

## Science

- Fields: protoplanetary_disks
- Question: To obtain a spatially resolved measurement of velocity dispersions in the disk of TW Hya.  
  > "To obtain a spatially resolved measurement of velocity dispersions in the disk of TW Hya." (abstract)
- Target **TW Hya**: coordinates _not stated_; z/distance d ≈ 54 pc  
  > "With a near face-on inclination of only $i \approx 7\ensuremath{^\circ}$ (cite: Qi_ea_2004) and as the nearest protoplanetary disk at $d \approx 54$ pc" (Introduction); distance from _not stated_

## Data provenance

- ALMA projects: 2013.1.00387.S
- bands: _not stated_
- frequencies and spectral setup: CO 2-1, CS 5-4 at 15 kHz channels (40 m/s effective); CN 2-1 hyperfines at 30 kHz (80 m/s)  
  > "a channel spacing of 15 kHz (and an effective velocity resolution of 40 m s$^{-1}$) for the CO J=(2-1) and CS J=(5-4) lines, and 30 kHz (80 m s$^{-1}$) for the CN N=(2-1) transition." (Observations)
- continuum bandwidth: _not stated_
- arrays: _not stated_
- configurations: _not stated_
- baselines: 21-550 m, ~34 antennas  
  > "which have baselines between 21 and 550 m, provided by the $\sim 34$ antennas" (Observations)
- angular resolution: 0.50'' x 0.42'' at PA 80 deg (robust weighting)  
  > "yields a beamsize of $0.50\ensuremath{''} \times 0.42\ensuremath{''}$ at position angle of $80\ensuremath{^\circ}$." (Observations)
- max recoverable scale: _not stated_
- sensitivity: rms 6-7 mJy/beam per 30.5 kHz channel (0.5-0.7 K)  
  > "we have a typical rms noise of order 6 - 7 mJy/beam which translates to about 0.5 - 0.7 K" (Appendix Error Derivations)
- time on source: _not stated_
- observing dates: May 13, 2015  
  > "The observations were performed using ALMA on May 13, 2015 under excellent weather conditions" (Observations)
- pi or archival as stated: _not stated_
- Line: CO J=2-1 (not stated)
- Line: CS J=5-4 (not stated)
- Line: CN N=2-1 hyperfine components (226659-226905 MHz (Table, hyperfines))
- External data: Physical model of TW Hya (density, temperature) used for beam-smear LIME simulations and density guidance  
  > "the physical model of TW Hya from (cite: Gorti_ea_2011) was used." (3.2 Keplerian shear correction) [from (cite: Gorti_ea_2011)]
- External data: CN N=2-1 laboratory hyperfine frequencies (CDMS fits)  
  > "CN N=2-1 line frequencies were measured in laboratory by (cite: Skatrud_ea_1983)" (Table notes) [from (cite: Skatrud_ea_1983)]
- Simulation/model as data: LIME synthetic observations of CO 2-1 and C18O 2-1 from Gorti model without turbulence, inclinations 0-9 deg, to calibrate Keplerian beam smearing  
  > "Both CO J=(2-1) and C$^{18}$O (2-1) lines were modelled, allowing us to sample both an optically thick and thin case." (3.2 Keplerian shear correction)

## Processing

### Calibration

- pipeline or manual: standard ALMA calibration script in CASA  
  > "Data was calibrated using the standard ALMA calibration script in the `CASA` software package" (Observations)
- casa version: _not stated_
- pipeline version: _not stated_
- archive products used as is: _not stated_
- flux calibrator: Ganymede; phase calibrator J1037-2934 0.72 Jy at 228 GHz  
  > "The absolute flux calibration was referred to Ganymede." (Observations)
- flux scale uncertainty: about 7%  
  > "We hence estimate that the calibration uncertainty is about 7%." (Observations)
- self calibration: Self-calibration on continuum, phase solution applied to line data  
  > "Self-calibration was performed on the continuum data, and the phase solution applied to all spectral line data." (Observations)

### Imaging

- task: Imaging in GILDAS after UVFITS export; CLASS for analysis  
  > "exported through UVFITS format to the `GILDAS`[^2] package for imaging and data analysis." (Observations)
- deconvolver: _not stated_
- weighting robust: robust weighting (value not given)  
  > "With robust weighting, the $uv$ coverage" (Observations)
- uv taper: _not stated_
- cell size: _not stated_
- image size: _not stated_
- masking: _not stated_
- multiscale scales: _not stated_
- continuum subtraction: _not stated_
- line free channels: _not stated_
- primary beam correction: applied after deconvolution; reaches 7% at map edge  
  > "After deconvolution and primary beam correction, the data cubes were imported into `CLASS` for further analysis" (Observations)
- array combination: _not stated_
- smoothing: _not stated_
- final beam: _not stated_
- final rms: _not stated_

### Inherited from earlier work

- Parametric disk model description and fitting methodology  
  > "refer the reader to (cite: Dartois_ea_2003) and (cite: Pietu_ea_2007) for a thorough model description and fitting methodology." (3.5 Parametric Model Fitting) [from (cite: Dartois_ea_2003); (cite: Pietu_ea_2007)]
- Height above midplane included in velocity field  
  > "Following (cite: Rosenfeld_ea_2013), we account for the height above the midplane in the calculation of the velocity field." (3.2 Keplerian shear correction) [from (cite: Rosenfeld_ea_2013)]
- Line fit uncertainty formula  
  > "The uncertainty of a Gaussian line parameter $X$ is derived from Eq. 1 from (cite: Lenz+Ayres_1992)" (Appendix Error Derivations) [from (cite: Lenz+Ayres_1992)]

### Not stated but needed to reproduce (our reading)

- Robust parameter, cell size, image size, clean masks, and velocity gridding for GILDAS imaging
- CASA version and exact calibration pipeline version
- Continuum/line-free channels and continuum subtraction
- Parametric model fitting algorithm, priors and likelihood details
- LIME setup parameters (photons, grid, abundances) and C18O abundance
- Archive data access/calibrated products details

## Analysis recipe

1. **Fit line profiles per pixel and azimuthal average**: Fit saturated-core opacity profile for CO, hyperfine Gaussian fit in CLASS for CN, Gaussian for CS; spectra shifted by local Keplerian velocity before azimuthal averaging  
  > "Using the ‘hyperfine’ mode in `CLASS` the hyperfine components were simultaneously fit with Gaussian profiles." (3.1 Line width measurements)
   - software: CLASS
   - parameter: Keplerian model with M*=0.69 Msun, i=7 deg for shifting  
  > "We used for this the best fit Keplerian model assuming a stellar mass of $0.69~M_{\ensuremath{\odot}}$ and $i = 7\ensuremath{^\circ}$" (Observations)
   - assumption: CN hyperfine components from same region, main component optically thick  
  > "Under the assumption that all hyperfine components arise from the same region in the disk and that the main component is optically thick" (3.1 Line width measurements)
   - fitting: _not stated_
   - validation: Channel resolution bias estimated ~2% (CO, CN) and 3.5% (CS) and corrected  
  > "we estimate that the bias on the measured $\Delta V$ would be $\approx 2~\%$ for CO and CN and $\approx 3.5~\%$ for CS." (3.1 Line width measurements)
2. **Correct Keplerian beam smearing**: LIME models of Gorti disk without turbulence at several inclinations, synthetic observations in CASA, power-law fit to linewidth difference  
  > "Differences in the resulting line width at each pixel between an inclined disk and a face on disk were attributed to Keplerian broadening." (3.2 Keplerian shear correction)
   - software: LIME, CASA
   - parameter: Direct methods only for r>40 au; inclinations 0,5,6,7,8,9 deg  
  > "In the following ‘direct’ methods we only consider the disk outside 40 au." (3.2 Keplerian shear correction)
   - fitting: Power law ΔV_Kep = (2.6±0.5)(r/100)^(-3.2±0.1) m/s  
  > "the radial distribution of differences in linewidths was well fit by a power law outside of 40 au" (3.2 Keplerian shear correction)
   - validation: 12CO and C18O differences smaller than quoted uncertainties  
  > "The differences between the $^{12}$CO and C$^{18}$O cases were smaller than these quoted uncertainties." (3.2 Keplerian shear correction)
3. **Single-molecule direct v_turb**: Subtract thermal width from corrected linewidth using Tex from line profile  
  > "With a known $T_{\rm kin}$ a simple subtraction of the thermal broadening component leaves $v_{\rm turb}$." (3.3 Single Molecule Approach)
   - assumption: CO and CN thermalised, Tex = Tkin  
  > "we make the assumption that both CO and CN lines are thermalised so that $T_{\rm ex}$ = $T_{\rm kin}$ $= T$." (3.3 Single Molecule Approach)
   - fitting: _not stated_
   - validation: CN beyond ~140 au excluded due to supra-thermal Tex > Tkin^max  
  > "Outside of $r \sim 140$ au, CN shows signs of non-LTE effects" (3.3 Single Molecule Approach)
4. **Co-spatial two-molecule v_turb and Tkin**: Solve linewidth equations simultaneously for CN and CS  
  > "Solving Equation [\[eq:linewidth\]](#eq:linewidth) simultaneously for two molecules, $A$ and $B$ with respective molecular masses" (3.4 Co-Spatial Approach)
   - parameter: mu = 26 (CN), 44 (CS)  
  > "where $\mu = 26$ for CN and $\mu = 44$ for CS" (4.2.2 Co-Spatial Approach)
   - assumption: CN and CS emit from same location  
  > "assuming the lines from these molecules emit from the same location in the disk." (3.4 Co-Spatial Approach)
   - fitting: _not stated_
   - validation: No solution where mu-scaled CS width < CN width, so assumption fails  
  > "In this situation there is no solution to Eqs. [\[eq:simtkin\]](#eq:simtkin) and [\[eq:simvturb\]](#eq:simvturb), thus the assumption of CN and CS being cospatial fails." (3.4 Co-Spatial Approach)
5. **Parametric power-law disk model fit**: Power-law disk with Gaussian vertical density; fit either v_turb power law or total linewidth power law  
  > "we fit two models, firstly one used previously in the literature where $v_{\rm turb}$ is described as a radial power-law, and secondly where we fit for the total linewidth" (3.5 Parametric Model Fitting)
   - parameter: i≈6 deg, PA≈240 deg, VLSR≈2.82 km/s  
  > "$i \approx 6\ensuremath{^\circ}$, ${\rm PA} \approx 240\ensuremath{^\circ}$ and $V_{\rm LSR} \approx 2.82$ km s$^{-1}$" (3.5 Parametric Model Fitting)
   - assumption: Lines fully thermalised  
  > "it was assumed all lines were fully thermalised so that the excitation temperature recovered the full thermal width of the line." (3.5 Parametric Model Fitting)
   - fitting: _not stated_
   - validation: Compared with direct methods and literature values  
  > "All three molecules display similar ranges of $v_{\rm turb}$, $\sim 50 - 150 \, {\rm m\,s^{-1}}$" (4.2.3 Parametric Model Fitting)
6. **Error and detectability analysis**: Analytic error propagation of Tkin/flux calibration uncertainty onto v_turb; two-zone temperature bias test  
  > "We derive in Appendix [7](#sec:derivation) the impact of the uncertainty on the kinetic temperature on the derivation of the turbulence," (4.3 Limits on the Detectability of v_turb)
   - fitting: _not stated_
   - validation: _not stated_

## Software

- **CASA** : Standard calibration and synthetic observations  
  > "Data was calibrated using the standard ALMA calibration script in the `CASA` software package" (Observations)
- **GILDAS** : Imaging and data analysis  
  > "to the `GILDAS`[^2] package for imaging and data analysis." (Observations)
- **CLASS** : Line profile fits including CN hyperfine structure  
  > "the data cubes were imported into `CLASS` for further analysis, in particular line profile fits including the hyperfine structure for CN lines." (Observations)
- **LIME** : Radiative transfer for beam smear estimate  
  > "The model was run through the `LIME` radiative transfer code (cite: Brinch_ea_2010)" (3.2 Keplerian shear correction)

## Numeric results

| quantity | value | uncertainty | units | step | quote |
|---|---|---|---|---|---|
| Keplerian shear linewidth power law amplitude at 100 au | 2.6 | 0.5 | m/s | 2 | \Delta V_{\rm Kep} = \Big(2.6 \pm 0.5\Big) \times \left(\frac{r}{100} \right)^{\,-3.2 \pm 0.1} |
| Keplerian shear power-law index | -3.2 | 0.1 | dimensionless | 2 | \Delta V_{\rm Kep} = \Big(2.6 \pm 0.5\Big) \times \left(\frac{r}{100} \right)^{\,-3.2 \pm 0.1} |
| Parametric T100 CO (total linewidth fit) | 35.51 | 0.09 | K | 5 | / CO J=2-1    / $262.7 \pm 0.2$   / $0.535 \pm 0.001$ / $160.0 \pm 0.5$ / $0.187 \pm 0.001$ / 35.51 $\pm$ 0.09 / |
| Parametric T100 CS (total linewidth fit) | 12.16 | 0.08 | K | 5 | / CS J=5-4    / $261.0 \pm 0.8$   / $0.53 \pm 0.02$   / $95 \pm 2$      / $0.06 \pm 0.01$   / 12.16 $\pm$ 0.08 / |
| v_turb direct range | ~130 m/s at 40 au dropping to ~50 m/s outer disk (~0.2-0.4 cs) | not stated | m/s | 3 | The direct method found $v_{\rm turb}$ ranging from $\approx$ 130 m s$^{-1}$ at 40 au, dropping to $\approx$ 50 m s$^{-1}$ in the outer disk |
| ALMA upper limit on v_turb from calibration | <0.16 cs | not stated | cs | 6 | only imply $v_{\rm turb}$ $< 0.23 c_s$ (SMA data) or $< 0.16 c_s$ (our ALMA data). |
| Absolute flux calibration uncertainty | 7% | not stated | percent | 0 | We hence estimate that the calibration uncertainty is about 7%. |

## Qualitative findings

- Co-spatial CN/CS assumption fails beyond ~100 au; CO, CN, CS likely trace different vertical layers  
  > "These pieces of evidence suggest CO, CN and CS each trace distinct vertical regions in the disk" (4.5)

## Claim tuples

- H: Can turbulence in TW Hya be directly measured with ALMA line widths? | E: Single-molecule and co-spatial direct methods on CO, CN, CS beyond 40 au | R: v_turb ~50-150 m/s, ~0.2-0.4 cs | F: Turbulence is comparable to or below MRI predictions; values best treated as upper limits | **partially**
- H: Are CN and CS co-spatial? | E: Solve simultaneous linewidth equations | R: No solution between ~100 and 180 au; parametric temperatures differ | F: Co-spatial assumption fails over much of disk | **refuted**
- H: What limits single-molecule turbulence detection? | E: Error propagation of Tkin uncertainty | R: 7-10% calibration gives sensitivity ≳0.2 cs; 3% gives ≳0.07 cs | F: Absolute flux calibration is the limiting factor | **supported**

## Reasoning

- Why this data: Face-on, nearest disk minimizes Keplerian shear  
  > "TW Hya provides the best opportunity to directly detect turbulent broadening as the impact of Keplerian shear for such face-on disks is minimized" (Introduction)
- Why this method: _not stated_
- How they decided it was enough: _not stated_
- Limitation (authors): Direct methods limited to r>40 au by beam smear; CN non-LTE beyond ~140 au  
  > "The two direct methods were limited to the outer $r > 40$ au disk due to beam smear." (abstract)
- Caveat (inferred, ours): Tex=Tkin assumption biases v_turb
- Caveat (inferred, ours): Parametric fit uncertainties are formal and underestimated
- Caveat (inferred, ours): Single epoch with 7% flux scale uncertainty

## Reproducibility

- Data public (paper): ALMA data cited by project code and acknowledgement  
  > "This paper makes use of the following ALMA data: ADS/JAO.ALMA#2013.1.00387.S." (Acknowledgements)
- Products in archive: _not stated_
- Missing: Imaging parameters
- Missing: Parametric fitting code and settings
- Missing: LIME configuration
- Data volume (inferred): ~50-200 GB raw
- Score (inferred): 3/5, Public data and clear equations, but imaging and fitting details are missing.
- Rediscovery candidate: no, Imaging and fitting settings are unstated and rely on GILDAS and earlier model code.

## Links

- Method: (cite: Pietu_ea_2007) (Parametric model fitting method)
- Method: (cite: Dartois_ea_2003) (Parametric model description)
- Companion: (cite: Hughes_ea_2011) (Previous SMA turbulence limit in TW Hya)

## Checks

```json
{
 "quotes": 63,
 "quotes_ok": 63,
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
  "facts": 81,
  "stated": 48,
  "rate": 0.593
 },
 "evidence_ok": true
}
```
