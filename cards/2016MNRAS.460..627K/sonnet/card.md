# The winds from HL Tau

`2016MNRAS.460..627K` | Monthly Notices of the Royal Astronomical Society 2016 | first author: Klaassen, P. D. | arXiv: 1604.07285 | DOI: 10.1093/mnras/stw989

Card schema 1.0 | model claude-sonnet-5-5 | depth full | type archival_reuse

## Science

- Fields: star_formation, protoplanetary_disks
- Question: What are the properties (morphology, opening angle, velocity, energetics) of the outflowing molecular gas from HL Tau, in context with the optical jet and the disk?  
  > "We aim to place these motions in context with the optically detected jet, and the disk." (abstract)
- Target **HL Tau**: coordinates _not stated_; z/distance 140 pc  
  > "HL Tau, at a distance of 140 pc (cite: Kwon11), is a young protostar of between $0.55-1.3$ M$_\odot$ (cite: Stephens14; Brogan15)." (Introduction); distance from Kwon11  
  > "HL Tau, at a distance of 140 pc (cite: Kwon11), is a young protostar of between $0.55-1.3$ M$_\odot$ (cite: Stephens14; Brogan15)." (Introduction)

## Data provenance

- ALMA projects: 2011.0.00015.SV
- bands: Band 3 (CO J=1-0 and continuum)  
  > "We used unmodified versions of the released reference images of the Band 3 continuum and CO emission." (Observations)
- frequencies and spectral setup: _not stated_
- continuum bandwidth: _not stated_
- arrays: _not stated_
- configurations: _not stated_
- baselines: 15.5 m to 15238 m (min 15.2 m in some executions)  
  > "| X5fa          | 30             | J0431+2037 | J0510+1800 | J0510+1800 | 2014-10-28     | 15238    | 15.5     |" (Table 1)
- angular resolution: CO tapered beam 0.98 x 0.90 arcsec, PA -9 deg  
  > "| CO (J=1-0)  | 115.271   | 0.98      | 0.90      | -9         | 8.1       |" (Table 1)
- max recoverable scale: approximately 41 arcsec  
  > "The shortest baselines were 15.5 m, which means the largest angular scale to which these observations could be sensitive is approximately 41$''$." (Observations)
- sensitivity: CO rms 8.1 mJy/beam per 1 km/s channel; continuum 0.01 mJy/beam  
  > "rms noise levels have units of mJy/beam per 1 km s$^{-1}$ channel for the CO line emission, and mJy/beam for the continuum." (Table 1)
- time on source: _not stated_
- observing dates: 2014-10-28 to 2014-11-14  
  > "| X306          | 30             | J0431+2037 | J0423-0120 | J0423-0120 | 2014-11-14     | 15238    | 15.2     |" (Table 1)
- pi or archival as stated: _not stated_
- Line: CO J=1-0 (115.271 GHz)
- Other facility **HST ACS**: Halpha and [NII] image of the region  
  > "we make use of archival HST ACS data for this region, showing the H$\alpha$ and \[Nii\] image first presented in (cite: Krist08)." (Other Archival Data)
- External data: Disk inclination 46±0.2 deg from continuum uv fitting  
  > "(cite: Brogan15) fit the $uv$ plane visibilities of the dust continuum emission, and found an inclination angle of $46\pm0.2^\circ$" (4.1 flow inclination angle) [from Brogan15]

## Processing

### Calibration

- pipeline or manual: _not stated_
- casa version: _not stated_
- pipeline version: _not stated_
- archive products used as is: Unmodified released reference images used  
  > "We used unmodified versions of the released reference images of the Band 3 continuum and CO emission." (Observations)
- flux calibrator: _not stated_
- flux scale uncertainty: _not stated_
- self calibration: _not stated_

### Imaging

- task: _not stated_
- deconvolver: _not stated_
- weighting robust: _not stated_
- uv taper: Released line data tapered to highlight larger scales (parameters not given)  
  > "The released spectral line data were tapered to highlight the larger scale structures, which results in a larger synthesised beam." (Observations)
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

### Inherited from earlier work

- Data details and reduction  
  > "Details about the data, and reduction can be found in (cite: Brogan15)." (Observations) [from Brogan15]

### Not stated but needed to reproduce (our reading)

- Taper parameters used for the released CO cube
- CASA version
- Systemic LSR velocity value used
- Beam counts/areas and exact method for flux to K conversion
- Wind and counter-flow peak velocities read from spectra
- Mask details beyond 3 sigma

## Analysis recipe

1. **Make moment maps**: Zeroth and first moment maps clipped at 3 and 5 sigma, integrated over 0-5.5 (blue) and 7-20 km/s (red)  
  > "These maps were clipped at 3 and 5 $\sigma$ respectively, using the noise level quoted in Table [1](#tab:observations)" (3 Results)
   - software: CASA
   - fitting: _not stated_
   - validation: _not stated_
2. **Measure opening angle**: Limb-brightened red lobe decomposed into 90 deg small-scale and 60 deg larger-scale opening angles  
  > "one with a small scale opening angle of 90$^\circ$, and a larger scale (collimated) opening angle of of 60$^\circ$" (3.3 Opening angle)
   - assumption: Conical 3D morphology  
  > "we expect this limb brightened morphology to be representative of a conical morphology in 3D." (3.3 Opening angle)
   - fitting: _not stated_
   - validation: _not stated_
3. **Derive flow mass, momentum, energy**: Per-channel LTE column density and mass, momentum, energy summed; luminosity and mass loss rate from dynamical age  
  > "assuming LTE and a temperature of 50 K, this was then scaled using the partition function to calculate the total column density of CO we are observing" (Calculating Physical Quantities)
   - software: uncertainties
   - parameter: Velocity integration limits 9-20 km/s red, -4 to 6 km/s blue  
  > "| Velocity Integration Limits                         | 9$\sim$ 20    | -4 $\sim$ 6     |" (Table 2)
   - assumption: Optically thin CO, T=50 K, CO abundance 1e-4, distance 140 pc  
  > "X is the abundance of CO, which we assume to be 10$^{-4}$" (Calculating Physical Quantities)
   - fitting: _not stated_
   - validation: Mass compared with Lumbreras14; temperature varied by 20 K changes mass by ~35%  
  > "Changing our assumed temperature by 20 K up or down changes our mass estimates by $\sim 35\%$." (3.4 Flow Energetics)
4. **Deproject flow velocity**: Solve two trigonometric equations using red and blue peak velocities of counter-flow components with inclination and opening angle  
  > "we can estimate the true velocities of the red and blue flows solving:" (4.1 flow inclination angle)
   - assumption: Flow axis perpendicular to disk; inclination 44 deg to line of sight  
  > "If the fow axis is perpendicular to the disk axis, then it should have an inclination angle of 44$^\circ$ with respect to the line of sight." (4.1 flow inclination angle)
   - fitting: _not stated_
   - validation: Counter-flow emission in 5.5 and 7.5 km/s channels confirms large opening angle  
  > "This shows that there is ‘rs blue’ and ‘bs red’ emission in this fow, which confirms that the opening angle is large" (4.1 flow inclination angle)

## Software

- **CASA** : Imaging and analysis  
  > "Data were imaged and analysed in casa (cite: CASA)." (Observations)
- **uncertainties** : Uncertainty propagation  
  > "we used the python package `uncertainties` to propagate the measured uncertainties through our calculations." (Data Processing)
- **APLpy** : Plotting  
  > "APLpy, an open-source plotting package for Python" (Acknowledgements)
- **Astropy** : Core Python package used  
  > "Astropy, a community-developed core Python package for Astronomy (cite: astropy)" (Acknowledgements)

## Numeric results

| quantity | value | uncertainty | units | step | quote |
|---|---|---|---|---|---|
| Red lobe opening angle, small scale | 90 | not stated | deg | 2 | one with a small scale opening angle of 90$^\circ$ |
| Red lobe opening angle, large scale | 60 | not stated | deg | 2 | a larger scale (collimated) opening angle of of 60$^\circ$ |
| Deprojected wind velocities (red, blue) | 2.5 and -2.3 | not stated | km/s | 4 | we find red and blue shifted wind velocities of 2.5 and -2.3 km s$^{-1}$. |
| Red flow mass | 0.73 | below quoted precision | 1e-4 Msun | 3 | / Mass            / ($\times 10^{-4}$ M$_\odot$)      / 0.73  / 0.00  / 11.14  / 0.00   / |
| Blue flow mass | 11.14 | below quoted precision | 1e-4 Msun | 3 | / Mass            / ($\times 10^{-4}$ M$_\odot$)      / 0.73  / 0.00  / 11.14  / 0.00   / |
| Outflow dynamical age | approximately 2650 | not stated | yr | 3 | we derive an outflow age of approximately 2650 yrs. |

## Qualitative findings

- Red lobe is limb brightened with hourglass morphology suggestive of magnetic collimation; blue lobe is less collimated, likely due to interaction with the XZ Tau bubble  
  > "The blue-shifted emission is not as collimated as the red, probably due to a combination of effects including the interaction with the XZ Tau bubble" (3.2 Blue-shifted emission)

## Claim tuples

- H: Is there a wide-angle wind perpendicular to the HL Tau disk crossing the plane of the sky? | E: Moment and channel maps of CO J=1-0 with spectra at counter-flow positions | R: Counter-flow emission at 5.5 and 7.5 km/s; opening angle 90 deg, inclination 44 deg | F: The flow is perpendicular to the disk with a large opening angle | **supported**
- H: What is the characteristic flow velocity? | E: Deprojection using inclination, opening angle and spectral peak velocities | R: 2.5 and -2.3 km/s | F: Characteristic wind velocity ~2.4 km/s in both lobes | **supported**

## Reasoning

- Why this data: _not stated_
- Why this method: _not stated_
- How they decided it was enough: _not stated_
- Limitation (authors): Missing flux from lack of short spacings; masses are lower limits; age is an extreme lower limit  
  > "there is likely missing flux from the largest scale structures in these data, therefore our column density and mass estimates are lower limits." (3.4 Flow Energetics)
- Caveat (inferred, ours): Missing flux strongly affects blue lobe and energetics
- Caveat (inferred, ours): Deprojection assumes flow perpendicular to disk and symmetric cone
- Caveat (inferred, ours): Velocity peaks read by eye from spectra, no uncertainties

## Reproducibility

- Data public (paper): Data from the ALMA archive (Science Verification)  
  > "The observations presented here come from the ALMA archive" (Observations)
- Products in archive: _not stated_
- Missing: Taper details
- Missing: Systemic velocity
- Missing: Spectrum peak velocities
- Missing: Exact masks and channel selection
- Data volume (inferred): Tens of GB if re-imaging; a few GB using released images
- Score (inferred): 3/5, Public data with released images and clear formulae, but several parameters unstated.
- Rediscovery candidate: yes, Public data, simple recipe, numeric results.

## Links

- Method: Brogan15 (Data and reduction details)
- Companion: Lumbreras14 (Earlier SMA CO outflow results compared)
- Related: ALMA Science Verification long baseline campaign

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
 "codes_printed_but_missing": [
  "2011.0.00015.S"
 ],
 "numeric_results": 6,
 "numeric_problems": 0,
 "fill": {
  "facts": 68,
  "stated": 31,
  "rate": 0.456
 },
 "evidence_ok": true
}
```
