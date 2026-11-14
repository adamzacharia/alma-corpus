# First Subarcsecond Submillimeter-wave [C I] Image of 49 Ceti with ALMA

`2019ApJ...883..180H` | The Astrophysical Journal 2019 | first author: Higuchi, Aya E. | arXiv: 1908.07032 | DOI: 10.3847/1538-4357/ab3d26

Card schema 1.0 | model claude-sonnet-5-5 | depth full | type observational_alma_primary

## Science

- Fields: debris_disks
- Question: What is the spatial distribution of [C I], CO(J=3-2) and dust continuum in the gaseous debris disk 49 Ceti, and what does the [C I]/CO intensity ratio imply about the origin of the gas and the UV radiation?  
  > "it is necessary to resolve the spatial distribution of the disk in order to understand the effect of UV radiation from the central star and from interstellar space." (Introduction)
- Target **49 Ceti**: coordinates _not stated_; z/distance d = 57±0.3 pc  
  > "located at d = 57$\pm$0.3 pc (cite: gai18)" (Introduction); distance from Gaia (cite: gai18)  
  > "located at d = 57$\pm$0.3 pc (cite: gai18)" (Introduction)

## Data provenance

- ALMA projects: 2017.0.00467.S, 2012.1.00195.S
- bands: Band 8 (614 um continuum and [C I]); CO(3-2) archival  
  > "49 Ceti was observed with ALMA during Cycle 5 in its compact configuration by using the Band 8 receivers." (Observations and Imaging)
- frequencies and spectral setup: _not stated_
- continuum bandwidth: _not stated_
- arrays: _not stated_
- configurations: _not stated_
- baselines: 15 m to 500 m, 43 12-m antennas, 7 execution blocks  
  > "The minimum and maximum baseline lengths achieved during the observation were 15 m and 500 m, respectively." (Observations and Imaging)
- angular resolution: continuum 0.51"x0.43"; [C I] 0.50"x0.42"; CO 0.56"x0.45"  
  > "The synthesized beam for the 614 $\ensuremath{\mu}m$ dust continuum is 0.51$''$$\times$0.43$''$ with P.A.= $-$ 84.8$^{\circ}$" (Observations and Imaging)
- max recoverable scale: _not stated_
- sensitivity: _not stated_
- time on source: 5.9 hours  
  > "On-source integration time was 5.9 hours." (Observations and Imaging)
- observing dates: _not stated_
- pi or archival as stated: CO(3-2) from ALMA archival data, described in Hughes et al. 2017  
  > "we employed the ALMA archival data of the CO($J$=3–2) line emission observed toward this source." (Observations and Imaging)
- Line: [C I] 3P1-3P0 (492.161 GHz)
- Line: CO J=3-2 (not stated)
- External data: 12CO(2-1)/13CO(2-1) flux ratio 2.3±0.2 from ALMA ACA  
  > "the flux ratio ($r$) of $^{12}$CO($J$=2–1)/$^{13}$CO($J$=2–1) is 2.3$\pm$0.2." (4 Interpretation) [from Moór et al. 2019 (cite: moo19)]
- External data: Dust temperature 57 K from SED fitting  
  > "The dust temperature derived from the model fitting of the spectral energy distribution is 57 K (cite: hol17)" (614 um continuum) [from (cite: hol17)]
- External data: Stellar mass 2.1 Msun  
  > "The stellar mass of 2.1 $M_\odot$ is taken from (cite: hug17)." (Table 1) [from (cite: hug17)]

## Processing

### Calibration

- pipeline or manual: not stated; calibrators listed  
  > "The quasars J2258-2758, J0141-0928, J2253+1608. and J0423-0120 were employed to calibrate amplitude, bandpass, and complex gain fluctuations" (Observations and Imaging)
- casa version: CASA 5.3.0  
  > "Data reduction was performed by using version 5.3.0 of the Common Astronomy Software Applications (CASA) package" (Observations and Imaging)
- pipeline version: _not stated_
- archive products used as is: _not stated_
- flux calibrator: _not stated_
- flux scale uncertainty: _not stated_
- self calibration: _not stated_

### Imaging

- task: tclean, 0.10 km/s velocity interval  
  > "The CASA task $\it{tclean}$ was used to Fourier-transform the visibility data and to deconvolve the dirty images at a velocity interval of 0.10 km s$^{-1}$." (Observations and Imaging)
- deconvolver: _not stated_
- weighting robust: natural weighting  
  > "\[C I\] and CO images were obtained by using natural weighting." (Observations and Imaging)
- uv taper: _not stated_
- cell size: _not stated_
- image size: _not stated_
- masking: _not stated_
- multiscale scales: _not stated_
- continuum subtraction: _not stated_
- line free channels: continuum from all line-free channels  
  > "The 614 $\ensuremath{\mu}m$ continuum map was obtained from a combination of all the line-free channels" (Observations and Imaging)
- primary beam correction: _not stated_
- array combination: _not stated_
- smoothing: _not stated_
- final beam: _not stated_
- final rms: _not stated_

### Inherited from earlier work

- CO observation details  
  > "Detailed information of the CO observation is described in (cite: hug17)." (Observations and Imaging) [from (cite: hug17)]
- Broad-ring/power-law disk model and temperature structure  
  > "As in (cite: hug17), the temperature structure is assumed as:" (Size Estimation) [from (cite: hug17)]
- Dust opacity law  
  > "with $\beta$ of 0.7 (cite: moo17)" (614 um continuum) [from (cite: moo17)]

### Not stated but needed to reproduce (our reading)

- CLEAN threshold, masks, image size and cell size
- Line-free channel ranges
- Flux calibrator flux values and calibration pipeline/manual choice
- Which MOUS/execution blocks used
- Grid ranges and chi2 definition of the model fit
- Noise rms values for 5 sigma cuts
- Details of hug17 CO data processing

## Analysis recipe

1. **image continuum and lines**: tclean with natural weighting; continuum from line-free channels; 0.10 km/s channels  
  > "The CASA task $\it{tclean}$ was used to Fourier-transform the visibility data and to deconvolve the dirty images at a velocity interval of 0.10 km s$^{-1}$." (Observations and Imaging)
   - software: CASA
   - fitting: _not stated_
   - validation: _not stated_
2. **measure fluxes and moment maps**: integrated intensity over -6 to 11.5 km/s; fluxes above 5 sigma with Polyline tool in CASA viewer; PV with impv  
  > "the velocity range for integration is from $-$6 to 11.5 km s$^{-1}$." ([C I] and CO)
   - software: CASA viewer, impv
   - fitting: _not stated_
   - validation: _not stated_
3. **fit disk sizes**: cut-off single power-law disk model with grid search of chi2 for Rin, Rout, p, h0, i  
  > "A grid-based search is conducted to find the minimum $\chi^{2}$ (Figure [7](#figB))." (Size Estimation)
   - assumption: T(R)=40 (R/100au)^-0.5; M*=2.1 Msun; optically thin  
  > "Assuming the optically thin condition, we use the spectrally integrated intensity in the analysis." (Size Estimation)
   - fitting: grid search minimizing chi2  
  > "A grid-based search is conducted to find the minimum $\chi^{2}$ (Figure [7](#figB))." (Size Estimation)
   - validation: reduced chi2 3.32 (dust), 5.55 ([C I]), 4.50 (CO); residual maps  
  > "This best fit result in the reduced $\chi^{2}$ is calculated to be 3.32 for the dust continuum, 5.55 for \[C I\], and 4.50 for CO, respectively." (Size Estimation)
4. **dust mass and CO optical depth**: optically thin dust mass for T=30-100 K; 12CO/13CO ratio gives tau  
  > "we estimate the total dust mass to be less than 0.15 $M_\oplus$." (614 um continuum)
   - assumption: kappa=2.3(nu/230GHz)^beta cm2/g, beta=0.7; 12C/13C=77  
  > "the elemental $^{12}$C/$^{13}$C ratio of 77 (cite: wil94) is assumed" (4 Interpretation)
   - fitting: _not stated_
   - validation: _not stated_
5. **[C I]/CO intensity ratio along major axis**: intensity profiles along P.A.=-72 deg; qualitative interpretation  
  > "Figure [3](#fig2) shows the intensity profiles of the \[C I\], CO, and continuum emission along the major axis (P.A.= $-$ 72$^{\circ}$)" (Intensity distribution)
   - fitting: _not stated_
   - validation: _not stated_

## Software

- **CASA** 5.3.0: data reduction, tclean imaging, impv  
  > "Data reduction was performed by using version 5.3.0 of the Common Astronomy Software Applications (CASA) package" (Observations and Imaging)

## Numeric results

| quantity | value | uncertainty | units | step | quote |
|---|---|---|---|---|---|
| 614 um continuum peak flux | 1.1 | 0.1 | mJy/beam | 2 | The peak flux is obtained to be 1.1$\pm$0.1 mJy beam$^{-1}$ |
| 614 um integrated flux | 24.4 | 0.1 | mJy | 2 | the integrated flux to be 24.4$\pm$0.1 mJy |
| [C I] integrated flux | 15.3 | 1.0 | Jy km/s | 2 | the integrated flux to be 15.3$\pm$1.0 Jy km s$^{-1}$ |
| CO(3-2) integrated flux | 5.7 | 0.3 | Jy km/s | 2 | the integrated flux to be 5.7$\pm$0.3 Jy km s$^{-1}$ |
| Dust ring Rin / Rout | 60 / 250 | 10 / 20 | au | 3 | / $R_{\rm{out}}$ \[au\] / 250 $\pm$ 20 / 195 $\pm$ 20 / 145 $\pm$ 10 / |
| [C I] Rin / Rout | 30 / 195 | 5 / 20 | au | 3 | 30$\pm$5 au and 195$\pm$20 au, respectively |
| Total dust mass | <0.15 | not stated | Earth masses | 4 | we estimate the total dust mass to be less than 0.15 $M_\oplus$. |
| 12CO(2-1) optical depth | 43 | 7 | dimensionless | 4 | the optical depth of the $^{12}$CO($J$=2–1) emission ($\tau$) is derived to as high as be 43$\pm$7 |
| Minimum [C I]/CO(3-2) ratio | 1.8 | not stated | dimensionless | 5 | The ratio takes the minimum value of 1.8 around the dust peak position |

## Qualitative findings

- [C I] and CO show double-peaked structure inside the dust ring; [C I] total flux exceeds CO  
  > "The \[C I\] distribution has a double-peaked structure inside the broad ring distribution of the dust continuum emission." ([C I] and CO)

## Claim tuples

- H: Is the dust distribution a broad ring and is gas extended similarly? | E: Band 8 imaging and disk model fits | R: Dust ring 60-250 au; [C I] 30-195 au; CO 35-145 au | F: Gas is co-extended with dust and located inside the dust peak | **supported**
- H: Does the [C I]/CO ratio vary spatially, tracing UV radiation? | E: Intensity profiles along major axis | R: Minimum 1.8 at dust peak, ~3 near star, ~10 in outer disk | F: Enhancement from stellar and interstellar UV | **partially**

## Reasoning

- Why this data: _not stated_
- Why this method: _not stated_
- How they decided it was enough: _not stated_
- Limitation (authors): Optical depth problem prevents quantitative column density and C/CO abundance derivation  
  > "the optical depth problem hampers quantitative discussions on the C/CO abundance ratio." (4 Interpretation)
- Caveat (inferred, ours): Interpretation of the ratio is qualitative with degenerate excitation vs abundance effects
- Caveat (inferred, ours): Single power-law fit has high reduced chi2 (3-5.5)
- Caveat (inferred, ours): Fluxes measured with GUI polyline tool, not reproducible precisely

## Reproducibility

- Data public (paper): _not stated_
- Products in archive: _not stated_
- Missing: Clean parameters, masks, image sizes
- Missing: Model fit grid details
- Missing: Explicit calibration details
- Data volume (inferred): ~100-300 GB raw for the Band 8 and archival Band 7 data
- Score (inferred): 3/5, Data identified by project codes and imaging is simple, but many imaging and fitting parameters are unstated.
- Rediscovery candidate: no, Recipe lacks key parameters and public status is not explicitly stated.

## Links

- Method: (cite: hug17) (Disk model and CO data description)
- Companion: (cite: hig17) (Earlier ASTE [C I] detection and abundance equations)

## Checks

```json
{
 "quotes": 47,
 "quotes_ok": 47,
 "quote_pass_rate": 1.0,
 "quotes_too_long": 0,
 "unsupported_facts": 0,
 "project_codes": 2,
 "codes_not_in_text": [],
 "codes_not_in_obscore": [
  "2017.0.00467.S"
 ],
 "obscore_codes_not_in_card": [
  "2017.1.00467.S"
 ],
 "codes_printed_but_missing": [],
 "numeric_results": 9,
 "numeric_problems": 0,
 "fill": {
  "facts": 69,
  "stated": 31,
  "rate": 0.449
 },
 "evidence_ok": true
}
```
