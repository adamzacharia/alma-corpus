# Disks and outflows in the S255IR area of high mass star formation from ALMA observations

`2018RAA....18...93Z` | Research in Astronomy and Astrophysics 2018 | first author: Zinchenko, Igor | arXiv: 1801.10331 | DOI: 10.1088/1674-4527/18/8/93

Card schema 1.0 | model claude-sonnet-5-5 | depth full | type observational_alma_primary

## Science

- Fields: star_formation
- Question: What is the overall structure of the S255IR high-mass star-forming region (clumps, filament, outflows, disks) as seen by ALMA?  
  > "Here we describe the overall structure of the S255IR region as revealed by ALMA." (Introduction)
- Target **S255IR (SMA1, SMA2, SMA3)**: coordinates _not stated_; z/distance 1.78 (+0.12/-0.11) kpc  
  > "located at a distance of $1.78^{+0.12}_{-0.11}$ kpc (cite: Burns16)" (Introduction); distance from Burns16 (cite: Burns16)  
  > "located at a distance of $1.78^{+0.12}_{-0.11}$ kpc (cite: Burns16)" (Introduction)

## Data provenance

- ALMA projects: 2015.1.00500.S
- bands: Band 7  
  > "carried out with ALMA in Band 7 at two epochs in 2016 during Cycle 4" (Observations)
- frequencies and spectral setup: four spectral windows at ~335.4, 337.3, 349.0, 346.6 GHz; bandwidths 1875.0, 234.4, 937.5, 1875.0 MHz  
  > "four spectral windows were observed, centered at around 335.4 GHz, 337.3 GHz, 349.0 GHz, and 346.6 GHz, with bandwidths of 1875.0 MHz, 234.4 MHz, 937.5 MHz, and 1875.0 MHz." (Observations)
- continuum bandwidth: _not stated_
- arrays: _not stated_
- configurations: _not stated_
- baselines: _not stated_
- angular resolution: 0.10" x 0.15"  
  > "The resulting images achieve an angular resolution of $0{\ensuremath{''}}10\times 0{\ensuremath{''}}15$" (Observations)
- max recoverable scale: _not stated_
- sensitivity: _not stated_
- time on source: _not stated_
- observing dates: two epochs in 2016 (Cycle 4)  
  > "at two epochs in 2016 during Cycle 4" (Observations)
- pi or archival as stated: _not stated_
- Line: CO 3-2 (not stated)
- Line: C34S 7-6 (not stated)
- Other facility **SMA**: previous observations of clumps SMA1, SMA2, SMA3 and 225 GHz flux comparison  
  > "Previous SMA observations showed here two rather isolated clumps (SMA1 and SMA2)" (Results)
- External data: 225 GHz SMA flux measurement of SMA3 for spectral slope comparison  
  > "when compared with the measurements at 225 GHz (cite: Wang11)" (Discussion) [from Wang11]

## Processing

### Calibration

- pipeline or manual: ALMA manual or pipeline calibration  
  > "Data were first calibrated through the ALMA manual or pipeline calibration process." (Observations)
- casa version: _not stated_
- pipeline version: _not stated_
- archive products used as is: _not stated_
- flux calibrator: _not stated_
- flux scale uncertainty: _not stated_
- self calibration: self-calibration applied  
  > "We further employed self-calibration to improve the imaging quality and dynamical range." (Observations)

### Imaging

- task: _not stated_
- deconvolver: _not stated_
- weighting robust: Briggs, robust = 0.5  
  > "with Briggs weighting with a robust parameter of 0.5" (Observations)
- uv taper: _not stated_
- cell size: _not stated_
- image size: _not stated_
- masking: _not stated_
- multiscale scales: _not stated_
- continuum subtraction: _not stated_
- line free channels: continuum from wide 335.4 GHz window with obvious spectral contamination removed  
  > "using visibilities in the wide low-resolution (continuum) spectral window at 335.4 GHz with obvious spectral contamination removed" (Observations)
- primary beam correction: _not stated_
- array combination: _not stated_
- smoothing: _not stated_
- final beam: _not stated_
- final rms: _not stated_

### Inherited from earlier work

- Observation details  
  > "Details of the observations are given in (cite: Zin17)." (Observations) [from (cite: Zin17)]

### Not stated but needed to reproduce (our reading)

- CASA version and calibration details
- self-calibration solints and iterations
- channel ranges excluded from continuum
- cell and image size, deconvolver, masks
- velocity ranges for red/blue CO outflow maps
- how fluxes were integrated, PV cut position/angle
- synthesized beam and rms values

## Analysis recipe

1. **make continuum image and estimate clump fluxes**: Briggs-weighted continuum image at 335 GHz; fluxes by integrating area or 2D Gaussian fits  
  > "The fluxes of these clumps can be estimated either by integrating their emission over some area or by fitting 2D Gaussians." (Results)
   - fitting: _not stated_
   - validation: _not stated_
2. **map outflows in CO(3-2)**: red- and blue-shifted high velocity CO(3-2) maps overlaid on continuum  
  > "The maps of the red- and blue-shifted high velocity CO(3–2) emission are presented in Fig. [2]" (Results)
   - fitting: _not stated_
   - validation: _not stated_
3. **estimate central mass of SMA2 from rotation**: position-velocity diagram in C34S(7-6), Keplerian-like, crude mass estimate  
  > "A crude estimate of the central mass gives a value $M\sin^2i \sim 1$ M$_\odot$" (Results)
   - assumption: inclination unknown  
  > "where $i$ is the unknown inclination angle" (Results)
   - fitting: _not stated_
   - validation: _not stated_

## Software


## Numeric results

| quantity | value | uncertainty | units | step | quote |
|---|---|---|---|---|---|
| SMA1 continuum flux density | ~1 | not stated | Jy | 1 | $\sim 1$ Jy for SMA1, $\sim 0.5$ Jy for SMA2, and $\sim 50$ mJy for SMA3 |
| SMA2 continuum flux density | ~0.5 | not stated | Jy | 1 | $\sim 1$ Jy for SMA1, $\sim 0.5$ Jy for SMA2, and $\sim 50$ mJy for SMA3 |
| SMA3 continuum flux density | ~50 | not stated | mJy | 1 | $\sim 1$ Jy for SMA1, $\sim 0.5$ Jy for SMA2, and $\sim 50$ mJy for SMA3 |
| Filament length | ~10 arcsec (~20000 AU) | not stated | arcsec | 1 | The apparent length of the filament is about $10^{\prime\prime}$, which corresponds to $\sim 20000$ AU. |
| SMA2 central mass M sin^2 i | ~1 | not stated | Msun | 3 | $M\sin^2i \sim 1$ M$_\odot$ |
| Filament column density | ~1e24 | not stated | cm^-2 | 1 | The gas column density, roughly estimated from the continuum brightness, is $\sim 10^{24}$ cm$^{-2}$ |

## Qualitative findings

- Two outflows from SMA1 and SMA2; SMA2 outflow is collimated, extended, bent; no outflow from SMA3  
  > "There is no sign of any outflow from SMA3." (Results)

## Claim tuples

- H: Is the SMA2 clump a rotating disk driving the extended outflow? | E: CO(3-2) outflow maps and C34S(7-6) PV diagram | R: Collimated outflow from SMA2 and Keplerian-like rotation, M sin^2 i ~ 1 Msun | F: SMA2 likely hosts a disk around a lower-mass protostar driving the outflow | **partially**

## Reasoning

- Why this data: _not stated_
- Why this method: _not stated_
- How they decided it was enough: _not stated_
- Limitation (authors): Flux estimates are caveated by area selection and complicated structure  
  > "Both approaches have shortcomings" (Results)
- Caveat (inferred, ours): Qualitative, no uncertainties
- Caveat (inferred, ours): Inclination unconstrained so mass is crude
- Caveat (inferred, ours): Disk claim from a single PV diagram

## Reproducibility

- Data public (paper): _not stated_
- Products in archive: _not stated_
- Missing: Full calibration and imaging parameters
- Missing: Outflow velocity ranges
- Missing: PV extraction details
- Data volume (inferred): ~100-200 GB raw for two Band 7 epochs
- Score (inferred): 2/5, Short letter-style paper; few parameters and no uncertainties.
- Rediscovery candidate: no, Recipe incomplete and results approximate.

## Links

- Method: (cite: Zin17) (Observation details)
- Companion: (cite: Zin17a) (Earlier ALMA study of SMA1)

## Checks

```json
{
 "quotes": 31,
 "quotes_ok": 31,
 "quote_pass_rate": 1.0,
 "quotes_too_long": 0,
 "unsupported_facts": 0,
 "project_codes": 1,
 "codes_not_in_text": [],
 "codes_not_in_obscore": [],
 "obscore_codes_not_in_card": [],
 "codes_printed_but_missing": [],
 "numeric_results": 6,
 "numeric_problems": 0,
 "fill": {
  "facts": 58,
  "stated": 20,
  "rate": 0.345
 },
 "evidence_ok": true
}
```
