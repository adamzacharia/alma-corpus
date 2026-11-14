# High Molecular Gas Masses in Absorption-selected Galaxies at z ≍ 2

`2020ApJ...901L...5K` | The Astrophysical Journal Letters 2020 | first author: Kanekar, N. | arXiv: 2009.04001 | DOI: 10.3847/2041-8213/abb4e1

Card schema 1.0 | model claude-sonnet-5-5 | depth full | type observational_alma_primary

## Science

- Fields: high_z_galaxies
- Question: Do high-metallicity z~2 DLAs host CO-emitting galaxies with high molecular gas masses, and do absorption-selected galaxies match emission-selected samples?  
  > "we report the results of an ALMA search for redshifted CO emission from the fields of 12 high-metallicity DLAs at $z \approx 2$." (Introduction)
- Target **12 high-metallicity DLA fields (e.g. J0016-0012, B0551-366, J2225+0527, B1228-113, J0918+1636)**: coordinates _not stated_; z/distance z_abs ≈ 1.7250-2.5832 (Table 1)  
  > "search for redshifted CO emission from the fields of 12 DLAs at $z \approx 1.66 - 2.58$" (Observations, Data analysis, and Results); distance from DLA absorption redshifts; CO redshifts measured here  
  > "search for redshifted CO emission from the fields of 12 DLAs at $z \approx 1.66 - 2.58$" (Observations, Data analysis, and Results)

## Data provenance

- ALMA projects: 2016.1.00628.S, 2017.1.01558.S
- bands: Bands 3 and 4  
  > "The ALMA bands 3 and 4 were used to search for redshifted CO emission" (Observations, Data analysis, and Results)
- frequencies and spectral setup: Four 1.875 GHz spectral windows; one with 3840 channels covering CO(3-2) or CO(4-3), three with 120 channels for continuum  
  > "Four 1.875 GHz spectral windows were used for all observations, with one spectral window, sub-divided into 3840 channels" (Observations, Data analysis, and Results)
- continuum bandwidth: _not stated_
- arrays: _not stated_
- configurations: compact array configurations  
  > "The observations were carried out in compact array configurations" (Observations, Data analysis, and Results)
- baselines: _not stated_
- angular resolution: beams ~1.6-3.6 arcsec (Table 1)  
  > "$3.5 \times 2.7$" (Table 1)
- max recoverable scale: _not stated_
- sensitivity: _not stated_
- time on source: 0.2-2.4 hours  
  > "total on-source times of $0.2 - 2.4$ hours" (Observations, Data analysis, and Results)
- observing dates: 2017 January to 2018 August  
  > "from 2017 January to 2018 August" (Observations, Data analysis, and Results)
- pi or archival as stated: _not stated_
- Line: CO 3-2 or 4-3 (not stated)
- External data: DLA metallicities, N_HI, Delta V90 and references per DLA  
  > "References: (1) (cite: berg15); (2) (cite: neeleman13), (3) (cite: krogager16), (4) (cite: petitjean02)" (Table 2) [from berg15; neeleman13; krogager16; petitjean02; fynbo10; fynbo13]
- External data: Emission metallicity vs stellar mass of UV-selected galaxies  
  > "the stellar mass for the (binned) UV-selected galaxies of (cite: erb06)" (Discussion) [from erb06]

## Processing

### Calibration

- pipeline or manual: Standard ALMA pipeline in CASA; self-calibration for three sources in AIPS or CASA  
  > "The initial calibration used the standard ALMA pipeline in the casa package" (Observations, Data analysis, and Results)
- casa version: _not stated_
- pipeline version: _not stated_
- archive products used as is: _not stated_
- flux calibrator: _not stated_
- flux scale uncertainty: ≲10%  
  > "The typical error on the flux density scale is expected to be $\lesssim 10$%." (Observations, Data analysis, and Results)
- self calibration: B1228-113, B1230-101, J2225+0527, using QSO continuum  
  > "In three sources (B1228-113, B1230-101, J2225+0527), the quasar continuum flux density was sufficient to perform self-calibration" (Observations, Data analysis, and Results)

### Imaging

- task: _not stated_
- deconvolver: _not stated_
- weighting robust: natural weighting  
  > "the final spectral cubes were created using natural weighting" (Observations, Data analysis, and Results)
- uv taper: _not stated_
- cell size: _not stated_
- image size: _not stated_
- masking: _not stated_
- multiscale scales: _not stated_
- continuum subtraction: uvsub after subtracting detected continuum  
  > "After subtracting out any detected continuum emission (using the casa task uvsub)" (Observations, Data analysis, and Results)
- line free channels: _not stated_
- primary beam correction: _not stated_
- array combination: _not stated_
- smoothing: velocity resolution ≈50-200 km/s; 200 km/s for limits  
  > "at velocity resolutions of $\approx 50-200$ km s$^{-1}$" (Observations, Data analysis, and Results)
- final beam: _not stated_
- final rms: _not stated_

### Inherited from earlier work

- B1228-113 and J0918+1636 detections previously reported; data re-analysed here  
  > "The data were re-analysed here, for consistency" (Table 1) [from neeleman18; fynbo18]
- CO line excitation ratios R13≈1.8, R14≈2.4  
  > "valid for galaxies near the main sequence at $z \approx 0-3$ (cite: tacconi20)" (Observations, Data analysis, and Results) [from (cite: tacconi20)]

### Not stated but needed to reproduce (our reading)

- Line-free channels and continuum-fit details
- Self-calibration solution intervals
- Image size and cell size, CLEAN depth/masking
- CASA version and pipeline version
- Flux, bandpass calibrators per run
- How CO FWHM and integrated flux and uncertainties were measured (fit form)
- QSO and DLA galaxy coordinates

## Analysis recipe

1. **calibrate and image**: ALMA pipeline calibration, self-cal for three sources, uvsub continuum subtraction, natural-weighted cubes  
  > "the final spectral cubes were created using natural weighting" (Observations, Data analysis, and Results)
   - software: CASA, AIPS
   - fitting: _not stated_
   - validation: _not stated_
2. **detect and measure CO line**: Spectrum from cut through dirty cube at peak pixel of velocity-integrated emission (unresolved); limits from 200 km/s cubes  
  > "the final CO spectrum was hence obtained from a cut through the “dirty” cube at the location of the peak pixel" (Observations, Data analysis, and Results)
   - fitting: _not stated_
   - validation: Detections required >5 sigma  
  > "Line emission was clearly detected (at $> 5\sigma$ significance)" (Observations, Data analysis, and Results)
3. **derive molecular gas masses**: Convert CO flux to L'CO, apply R13/R14 to CO(1-0), multiply by alpha_CO  
  > "We will also assume $\alpha_{\rm CO}= 4.36 \; \textrm{M}_\odot$ (K km s$^{-1}$ pc$^{2}$)$^{-1}$" (Observations, Data analysis, and Results)
   - assumption: alpha_CO=4.36; R13≈1.8, R14≈2.4; flat LCDM H0=67.4, Om=0.315  
  > "We will assume sub-thermal excitation of the higher-J levels, with $R_{13} \approx 1.8$ and $R_{14} \approx 2.4$" (Observations, Data analysis, and Results)
   - fitting: _not stated_
   - validation: _not stated_
4. **compare with mass-metallicity relation**: Assume Mmol/M*≈1 to get stellar mass; plot DLA metallicity vs M* against Erb06  
  > "plots the DLA metallicity versus the inferred stellar mass for the DLA galaxies, assuming $\rm{M_{mol}}/\rm{M_{\star}}\approx 1$" (Discussion)
   - fitting: _not stated_
   - validation: _not stated_

## Software

- **CASA** : pipeline calibration, uvsub, imaging, self-cal  
  > "The initial calibration used the standard ALMA pipeline in the casa package" (Observations, Data analysis, and Results)
- **AIPS** : self-calibration in some sources  
  > "this was carried out in either the aips (cite: greisen03) or the casa packages" (Observations, Data analysis, and Results)

## Numeric results

| quantity | value | uncertainty | units | step | quote |
|---|---|---|---|---|---|
| Molecular gas masses of five CO detections | (1.3-20.7) x (alpha_CO/4.36) x 10^10 | not stated | Msun | 3 | M_{mol}}\approx (1.3 - 20.7) |
| 3 sigma upper limits on Mmol for non-detections | (0.6-2.3) x (alpha_CO/4.36) x 10^10 | not stated | Msun | 3 | $(0.6 - 2.3) \times (\alpha_{\rm CO}/4.36) 10^{10} \; \textrm{M}_\odot$ |
| B1228-113 integrated CO(3-2) flux | 0.726 | 0.031 | Jy km/s | 2 | $0.726 \pm 0.031$ |
| J0918+1636 Mmol | 20.7 | 1.3 | 1e10 Msun | 3 | $20.7 \pm 1.3$ |
| CO emitter impact parameters | 5.6-100 | not stated | kpc | 0 | $b \approx 5.6-100$ kpc |

## Qualitative findings

- No CO detections overlap with galaxies found by optical/near-IR searches and vice versa  
  > "None of the DLA galaxies detected in CO emission were identified in earlier optical or near-IR searches and vice-versa" (abstract)

## Claim tuples

- H: High-metallicity z~2 DLAs are associated with CO-emitting massive galaxies | E: ALMA CO(3-2)/(4-3) search in 12 DLA fields | R: Five confirmed detections, three new, Mmol 1.3-20.7e10 Msun | F: DLA galaxies with high molecular gas masses are identified via CO | **supported**
- H: High masses are explained by mass-metallicity relation and high gas-to-stars ratio | E: Plot DLA metallicity vs M* assuming Mmol/M*≈1 against Erb06 | R: All but one consistent with emission-selected relation | F: Plausible explanation, but simplistic | **partially**
- H: CO and optical/near-IR searches trace different DLA galaxies | E: Compare with earlier searches in five fields | R: No overlap | F: Complementary methods | **supported**

## Reasoning

- Why this data: High-metallicity targets have lower alpha_CO, so CO is easier to detect  
  > "it is easier to detect CO emission from high-metallicity galaxies than from low-metallicity ones" (Introduction)
- Why this method: _not stated_
- How they decided it was enough: _not stated_
- Limitation (authors): Data cannot rule out mergers; lower alpha_CO or higher excitation would lower masses  
  > "our present ALMA data do not have the resolution or sensitivity to rule out the possibility of merging galaxies" (Discussion)
- Caveat (inferred, ours): Mass depends on assumed alpha_CO and excitation, questionable for the lowest-metallicity detection
- Caveat (inferred, ours): Mmol/M*≈1 assumption is simplistic
- Caveat (inferred, ours): Small sample; tentative detections at ~4.5 sigma
- Caveat (inferred, ours): Association between CO emitter and DLA absorber not proven

## Reproducibility

- Data public (paper): Available through the ALMA archive  
  > "The data reported in this paper are available though the ALMA archive" (Acknowledgments)
- Products in archive: _not stated_
- Missing: Imaging parameters
- Missing: Line-fitting procedure for flux and FWHM
- Missing: L'CO conversion details beyond cited formula
- Data volume (inferred): ~100-300 GB raw for 12 fields
- Score (inferred): 3/5, Public data and simple, numeric recipe, but imaging and line measurement details are sparse.
- Rediscovery candidate: yes, Public data, natural-weighted cubes, numeric flux and mass results in tables.

## Links

- Method: (cite: carilli13) (CO luminosity relations)
- Method: (cite: tacconi20) (excitation ratios and alpha_CO)
- Companion: (cite: neeleman18) (earlier B1228-113 detection)
- Companion: (cite: fynbo18) (earlier J0918+1636 detection)

## Checks

```json
{
 "quotes": 43,
 "quotes_ok": 43,
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
  "facts": 64,
  "stated": 31,
  "rate": 0.484
 },
 "evidence_ok": true
}
```
