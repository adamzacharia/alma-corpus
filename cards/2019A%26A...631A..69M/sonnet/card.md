# Bright C<SUB>2</SUB>H emission in protoplanetary discs in Lupus: high volatile C/O &gt; 1 ratios

`2019A&A...631A..69M` | Astronomy and Astrophysics 2019 | first author: Miotello, A. | arXiv: 1909.04477 | DOI: 10.1051/0004-6361/201935441

Card schema 1.0 | model claude-sonnet-5-5 | depth full | type observational_alma_primary

## Science

- Fields: protoplanetary_disks, astrochemistry
- Question: Are low CO fluxes in Lupus disks caused by volatile carbon/oxygen depletion or by fast gas dissipation, as probed by C2H emission?  
  > "The goal of this work is to employ C$_2$H observations to understand whether low CO fluxes are caused by volatile depletion, or by fast gas dissipation." (abstract)
- Target **Nine Lupus disks (Sz 98, Sz 71, J16070854-3914075, Sz 114, MY Lup, J16090141-3925119, Sz 129, J16070384-3911113, Sz 68)**: coordinates Table 1 lists RA/Dec per source, e.g. Sz 71 15:46:44.716 -34:30:36.057  
  > "(c): Distance measured by GAIA (cite: GAIA). Typical errors on the distance are 1-2% of the measured distance for these sources." (Table 1); z/distance 150.0-175.8 pc (Gaia)  
  > "(c): Distance measured by GAIA (cite: GAIA). Typical errors on the distance are 1-2% of the measured distance for these sources." (Table 1); distance from Gaia DR2 (Gaia Collaboration 2018)  
  > "(c): Distance measured by GAIA (cite: GAIA). Typical errors on the distance are 1-2% of the measured distance for these sources." (Table 1)

## Data provenance

- ALMA projects: 2017.1.00495.S
- bands: continuum centred on 246 GHz; C2H window centred on 262.006 GHz  
  > "one spectral window devoted to the continuum emission centred on 246 GHz" (Observations)
- frequencies and spectral setup: C2H window 262.006 GHz, bandwidth 117 MHz, channel width 0.14 MHz, velocity resolution 0.16 km/s  
  > "whose spectral window was centred on $262.006$ GHz, with bandwidth of 117 MHz, channel width of 0.14 MHz, and velocity resolution of 0.16 km s$^{-1}$" (Observations)
- continuum bandwidth: _not stated_
- arrays: _not stated_
- configurations: _not stated_
- baselines: 16.7-2700 m (49 antennas, 12 July); 18.6-1500 m (42 antennas, 15 July)  
  > "observed on 2017 July 12 with 49 antennas (16.7-2700 m baselines)" (Observations); "observed on 2017 July 15 with 42 antennas (18.6-1500 m baselines)" (Observations)
- angular resolution: ~0.2 x 0.3 arcsec (~30 au)  
  > "the achieved beam size is $\sim$ 0.2 $\times$ 0.3 arcseconds" (Observations)
- max recoverable scale: _not stated_
- sensitivity: rms 5-10 mJy km/s  
  > "The typical achieved rms is between 5 and 10 mJy km s$^{-1}$." (Observations)
- time on source: ~20 minutes per source  
  > "The typical integration time was approximatively 20 minutes on source." (Observations)
- observing dates: 2017 July 12 and 2017 July 15  
  > "were observed on 2017 July 12 with 49 antennas" (Observations)
- pi or archival as stated: Cycle 4, PI Miotello  
  > "under the project code 2017.1.00495.S (PI: Miotello A.)" (Observations)
- Line: C2H N=3-2, J=7/2-5/2, F=4-3 and F=3-2 (not stated)
- Other facility **Gaia**: distances and stellar properties  
  > "(c): Distance measured by GAIA (cite: GAIA)." (Table 1)
- Other facility **ALMA Lupus survey (Ansdell et al. 2016)**: 13CO fluxes and 890 um continuum flux densities  
  > "together with $^{13}$CO integrated fluxes and continuum flux densities, taken from (cite: Ansdell16)" (Observations)
- External data: 13CO integrated fluxes and 890 um continuum flux densities  
  > "together with $^{13}$CO integrated fluxes and continuum flux densities, taken from (cite: Ansdell16)" (Observations) [from (cite: Ansdell16)]
- External data: CO-based gas masses and dust masses  
  > "Our Lupus C$_2$H observations are also reported, as a function of their dust masses, derived from their continuum emission (cite: Miotello17)." (Comparison with models) [from (cite: Miotello17)]
- External data: C2H data for other disks  
  > "Recently, (cite: Bergner19) have published C$_2$H observations of a set of 14 disks" (C2H emission in other sources) [from (cite: Bergner19)]
- External data: CN (N=4-3) line luminosities for the nine disks  
  > "The nine Lupus disks targeted in this paper have also been detected by (cite: vanTerwisga18) in CN ($N=4-3$) emission." (Appendix) [from (cite: vanTerwisga18)]
- Simulation/model as data: DALI physical-chemical models, T Tauri-like, Teff=4000 K, Lbol=1 Lsun, disk masses 1e-5 to 1e-1 Msun, with C/O 0.3-1.5 and gas/dust=1 variants  
  > "we chose T Tauri like disk models, where the central star emission is described by a black body at $T_{\rm eff}=4000$ K" (Comparison with models)

## Processing

### Calibration

- pipeline or manual: pipeline calibrated, then phase-only self-calibration on continuum  
  > "From the pipeline calibrated data we performed (only phase and not amplitude) self-calibration using each source’s continuum emission." (Observations)
- casa version: CASA 4.7.2 (imaging)  
  > "The data were imaged using the `clean` task in CASA version 4.7.2" (Observations)
- pipeline version: _not stated_
- archive products used as is: _not stated_
- flux calibrator: _not stated_
- flux scale uncertainty: 10%  
  > "We estimate a flux calibration error of 10% based on variations in the flux calibrators." (Observations)
- self calibration: phase-only, using each source's continuum  
  > "(only phase and not amplitude) self-calibration using each source’s continuum emission" (Observations)

### Imaging

- task: CASA clean  
  > "The data were imaged using the `clean` task in CASA version 4.7.2 using natural weighting" (Observations)
- deconvolver: _not stated_
- weighting robust: natural weighting  
  > "using natural weighting" (Observations)
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
- final beam: ~0.2 x 0.3 arcsec  
  > "the achieved beam size is $\sim$ 0.2 $\times$ 0.3 arcseconds" (Observations)
- final rms: 5-10 mJy km/s  
  > "The typical achieved rms is between 5 and 10 mJy km s$^{-1}$." (Observations)

### Inherited from earlier work

- Aperture synthesis method for disk-integrated fluxes on moment 0 maps  
  > "using an aperture synthesis method on the moment 0 maps, similar to that used by (cite: Ansdell16)" (Integrated fluxes) [from (cite: Ansdell16)]
- Derotating and deprojecting images for azimuthally averaged radial profile  
  > "computed after derotating and deprojecting the images following (cite: vanTerwisga18)" (Ring-like structures) [from (cite: vanTerwisga18)]
- DALI model grid design and settling/grain parameters  
  > "This is a similar set of models as presented by (cite: Cazzoletti18) for CN" (Comparison with models) [from (cite: Cazzoletti18); (cite: Visser18) for chemistry]
- Linear regression with Bayesian method including upper limits  
  > "We compute the linear regression coefficients using the fully Bayesian method by (cite: Kelly07)" (C2H and CN line luminosity in Lupus) [from (cite: Kelly07)]

### Not stated but needed to reproduce (our reading)

- Line-free channels / continuum subtraction approach for the C2H cube
- Velocity range or channels used for moment 0 and aperture size/shape
- Self-calibration solution intervals and reference sources
- Clean threshold, masking, image size and cell size
- Rest frequencies adopted for C2H hyperfine components
- Priors and chain settings of the Kelly (2007) fit; the CN luminosities used
- DALI model grid details (full parameter table, chemical network version, line radiative transfer settings)
- Whether the continuum data of the other targets were imaged identically; continuum flux/rms values at 1.2 mm

## Analysis recipe

1. **Calibrate and image C2H and continuum**: Pipeline calibration, phase-only self-calibration on continuum, imaging with CASA clean with natural weighting  
  > "From the pipeline calibrated data we performed (only phase and not amplitude) self-calibration using each source’s continuum emission." (Observations)
   - software: CASA
   - parameter: natural weighting; beam ~0.2 x 0.3 arcsec  
  > "using natural weighting and the achieved beam size is $\sim$ 0.2 $\times$ 0.3 arcseconds" (Observations)
   - fitting: _not stated_
   - validation: _not stated_
2. **Measure disk-integrated C2H fluxes and luminosities**: Moment 0 maps from all channels with detected signal; aperture flux on image plane; luminosity = flux x 4 pi d^2  
  > "The line luminosity is obtained by multiplying the integrated flux by $4 \pi d^2$" (Integrated fluxes)
   - software: CASA
   - parameter: 3 sigma upper limits for non-detections  
  > "(d): 3$\sigma$ upper limits." (Table 1)
   - assumption: Gaia distances  
  > "where $d$ is the distance of the target in parsecs as measured by GAIA" (Integrated fluxes)
   - fitting: _not stated_
   - validation: _not stated_
3. **Radial profiles of C2H and continuum**: Azimuthally averaged profiles after deprojection, compared with continuum rings from Huang et al. 2018  
  > "The C$_2$H azimuthally averaged intensity radial profile is computed after derotating and deprojecting the images following (cite: vanTerwisga18)" (Ring-like structures)
   - fitting: _not stated_
   - validation: _not stated_
4. **Correlate C2H with CN luminosity**: Bayesian linear regression in log-log space with errors on both axes, upper limits and intrinsic scatter  
  > "which allows the inclusion of uncertainties on both axes, upper limits and intrinsic dispersion in the fitting procedure" (C2H and CN line luminosity in Lupus)
   - fitting: Kelly (2007) Bayesian method; median of chains adopted  
  > "The best representative set of parameters, which we adopt as the median of the results of the chains" (C2H and CN line luminosity in Lupus)
   - validation: _not stated_
5. **Compare with DALI models**: Compare observed C2H luminosities with simulated luminosities vs gas mass for ISM abundances, depleted C and O with C/O=0.3-1.5, and gas/dust=1 models  
  > "A subsample of models has been run reducing the carbon abundance by two orders of magnitude and the oxygen abundance by slightly larger factors" (Comparison with models)
   - software: DALI
   - parameter: [C]/[H]=1e-4, [O]/[H]=3.5e-4 baseline; f_large=0.99; chi=0.2  
  > "more precisely \[C\]/\[H\]=$1\times 10^{-4}$ and \[O\]/\[H\]=$3.5\times 10^{-4}$" (Comparison with models)
   - assumption: CO-based gas masses from Miotello et al. 2017 assume ISM [C] and [O]  
  > "the total gas mass based on CO for ISM \[C\] and \[O\]" (Comparison with models)
   - fitting: _not stated_
   - validation: Comparison to Bergin16, Kama16 and Cleeves18 model behaviour  
  > "With \[C\]/\[O\]=1 the simulation comes closer to the data, but \[C\]/\[O\]\>1 is needed to approach the observed values" (Comparison with models)

## Software

- **CASA** 4.7.2: imaging with clean  
  > "The data were imaged using the `clean` task in CASA version 4.7.2" (Observations)
- **DALI** : physical-chemical disk models  
  > "a grid of physical-chemical disk models run with the code DALI (cite: Bruderer12) was employed" (Comparison with models)

## Numeric results

| quantity | value | uncertainty | units | step | quote |
|---|---|---|---|---|---|
| C2H-CN regression intercept | -12.6 | ±4 | dimensionless | 4 | The intercept and the slope of the linear regression are $\alpha= -12.6\pm 4$ and $\beta = 2.4\pm0.4$. |
| C2H-CN regression slope | 2.4 | ±0.4 | dimensionless | 4 | The intercept and the slope of the linear regression are $\alpha= -12.6\pm 4$ and $\beta = 2.4\pm0.4$. |
| Correlation coefficient | 0.96 | ±0.04 | dimensionless | 4 | The best representative model has a correlation coefficient of $0.96\pm0.04$. |
| C2H flux Sz 98 | 1101 | ±57 | mJy km/s | 2 | / 1-10 Sz 98 / 16:08:22.481 / -39:04:46.812 / 0.67 / 1.53 / -0.71 / 1101$\pm$57 |
| C2H flux Sz 71 | 1101 | ±46 | mJy km/s | 2 | / Sz 71 / 15:46:44.716 / -34:30:36.057 / 0.41 / 0.33 / -2.17 / 1101$\pm$46 |
| C2H flux Sz 129 (faintest detection) | 107 | ±16 | mJy km/s | 2 | / Sz 129 / 15:59:16.458 / -41:57:10.662 / 0.78 / 0.43 / -1.13 / 107$\pm$16 |
| C2H ring peak radius Sz 71 and Sz 114 | 40 au and 27 au | not stated | au | 3 | The peak of C$_2$H emission is located at 40 au and 27 au respectively in these two sources. |
| Continuum ring radius Sz 98 | 90 | not stated | au | 3 | only Sz 98 shows the presence of a ring in continuum emission located at 90 au |

## Qualitative findings

- Seven of nine disks detected in C2H, bimodal distribution of line intensities  
  > "Seven out of nine disks are detected in C$_2$H, whose line emission is almost as bright as $^{13}$CO." (abstract)
- C2H rings and continuum rings are not connected; Sz 71 C2H and CN peaks coincide  
  > "Sz 71 shows ring shaped emission in both C$_2$H and CN with the location of the peak intensity coinciding, within our 30 au resolution." (abstract)

## Claim tuples

- H: Faint CO in Lupus disks is due to volatile C and O depletion with C/O>1 rather than fast gas dispersal | E: Compared observed C2H luminosities with DALI models with ISM abundances, depleted C/O, and gas/dust=1 | R: ISM models underpredict C2H by 1-2 orders of magnitude; depleted C/O>1 models match; gas/dust=1 models fail | F: Volatile C and O depletion with [C]/[O]>1 favoured for most disks | **supported**
- H: C2H emission is bimodal in the sample | E: Plotted C2H luminosity vs 13CO/continuum ratio and added literature disks | R: Detections well above sensitivity, non-detections otherwise | F: Step-like behaviour, limited by small-number statistics | **partially**
- H: C2H and CN luminosities correlate and C2H depends more strongly on [C]/[O] | E: Bayesian regression of log luminosities | R: slope 2.4±0.4, correlation 0.96±0.04 | F: C2H depends more strongly than CN on some parameter, interpreted as [C]/[O] | **supported**

## Reasoning

- Why this data: Targets selected among brightest Lupus continuum disks detected in CO isotopologues and CN, with CO-based g/d from 100 to 0.1  
  > "The targets were selected among the brightest Lupus disks in continuum emission as those detected in CO isotopologues and in CN" (Observations)
- Why this method: _not stated_
- Alternative: Fast gas dispersal (gas/dust=1 models) fails to reproduce bright C2H, though not ruled out for J16070854-3914075  
  > "This however does not necessarily rule out fast gas dispersal (see e.g., J16070854-3914075)" (Summary and conclusion)
- How they decided it was enough: _not stated_
- Limitation (authors): Small-number statistics limit the study; UV and disk size may add scatter; no source-by-source modelling  
  > "The small number statistics however limits the study" (Summary and conclusion)
- Caveat (inferred, ours): Only a first-order comparison with a generic model grid, not source-specific
- Caveat (inferred, ours): Sample of nine with non-uniform selection
- Caveat (inferred, ours): Models fix depletion factor and compare with CO-based masses that depend on assumed carbon
- Caveat (inferred, ours): Flux sensitivity to aperture and channel choices not described

## Reproducibility

- Data public (paper): Data cited by project code; public status not explicitly stated  
  > "This paper makes use of the following ALMA data: ADS/JAO.ALMA#2017.1.00495.S." (Acknowledgements)
- Products in archive: _not stated_
- Missing: Moment-0 channel ranges and aperture definition
- Missing: Self-calibration parameters
- Missing: DALI model grid and outputs
- Missing: CN luminosities and Ansdell16 values handling
- Missing: Manifest links project 2016.1.00459.S but paper prints 2017.1.00495.S
- Data volume (inferred): ~50-100 GB raw for ten sources in two executions
- Score (inferred): 3/5, Data and basic imaging are described and fluxes tabulated, but key imaging and flux extraction parameters and DALI grid are missing.
- Rediscovery candidate: no, Imaging and aperture details are incomplete and model comparison relies on an unreleased DALI grid.

## Links

- Method: (cite: Ansdell16) (aperture flux method and 13CO/continuum data)
- Method: (cite: Kelly07) (Bayesian linear regression)
- Method: (cite: Cazzoletti18) (DALI model setup)
- Companion: (cite: vanTerwisga18) (CN observations of the same disks)
- Companion: (cite: Bergner19) (C2H survey of 14 other disks)
- Related: ALMA Lupus survey (Ansdell et al. 2016)
- Related: DSHARP

## Checks

```json
{
 "quotes": 66,
 "quotes_ok": 66,
 "quote_pass_rate": 1.0,
 "quotes_too_long": 0,
 "unsupported_facts": 0,
 "project_codes": 1,
 "codes_not_in_text": [],
 "codes_not_in_obscore": [
  "2017.1.00495.S"
 ],
 "obscore_codes_not_in_card": [
  "2016.1.00459.S"
 ],
 "codes_printed_but_missing": [],
 "numeric_results": 8,
 "numeric_problems": 0,
 "fill": {
  "facts": 80,
  "stated": 51,
  "rate": 0.637
 },
 "evidence_ok": true
}
```
