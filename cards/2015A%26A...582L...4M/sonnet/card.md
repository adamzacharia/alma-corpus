# Detection of extragalactic argonium, ArH<SUP>+</SUP>, toward PKS 1830-211

`2015A&A...582L...4M` | Astronomy and Astrophysics 2015 | first author: Müller, Holger S. P. | arXiv: 1509.06917 | DOI: 10.1051/0004-6361/201527254

Card schema 1.0 | model claude-sonnet-5-5 | depth full | type observational_alma_primary

## Science

- Fields: nearby_galaxies, astrochemistry, milky_way_ism
- Question: Can ArH+ be detected in extragalactic sources as a tracer of the almost purely atomic diffuse ISM, and what is the 36Ar/38Ar isotopic ratio at z=0.89?  
  > "We attempted to detect ArH$^+$ in extragalactic sources to evaluate its diagnostic power as a tracer of the almost purely atomic ISM in distant galaxies." (abstract)
- Target **PKS 1830-211 (foreground galaxy, SW and NE images)**: coordinates _not stated_; z/distance z = 0.88582  
  > "The unnamed foreground galaxy at $z = 0.88582$ (cite: redshift_1996) in the direction of the blazar PKS 1830$-$211" (Introduction); distance from Wiklind & Combes 1996 (cite: redshift_1996)  
  > "The unnamed foreground galaxy at $z = 0.88582$ (cite: redshift_1996) in the direction of the blazar PKS 1830$-$211" (Introduction)

## Data provenance

- ALMA projects: 2013.1.00296.S
- bands: Band 7, tuned to ~327 GHz  
  > "with receivers tuned to $\sim$327 GHz (Band 7)" (Observations and spectroscopic data)
- frequencies and spectral setup: ArH+ isotopologs in one 1.875 GHz window; two more windows at ~337 GHz (H2O+) and ~339 GHz (continuum)  
  > "The three ArH$^+$ isotopologs were observed simultaneously in the same 1.875 GHz wide spectral window." (Observations and spectroscopic data)
- continuum bandwidth: _not stated_
- arrays: _not stated_
- configurations: _not stated_
- baselines: _not stated_
- angular resolution: ~0.5 arcsec synthesized beam  
  > "well resolved by the synthesized beam of $\sim$0.5$\ensuremath{''}$" (Observations and spectroscopic data)
- max recoverable scale: _not stated_
- sensitivity: _not stated_
- time on source: ~20 min  
  > "in about 20 min on-source time under very good atmospheric conditions" (Observations and spectroscopic data)
- observing dates: 2015 May 19 (Cycle 2)  
  > "Observations reported here were obtained with ALMA on 2015 May 19 (Cycle 2)" (Observations and spectroscopic data)
- pi or archival as stated: _not stated_
- Line: 36ArH+ J=1-0 (617525.23(15) MHz)
- Line: 38ArH+ J=1-0 (616648.76(8) MHz)
- Line: 40ArH+ J=1-0 (615858.15(5) MHz)
- Line: H2O+ 1_10-1_01, J=0.5-1.5 (634.27 GHz)
- External data: Spectroscopic data for ArH+ transitions  
  > "Spectroscopic data of ArH$^+$ transitions were taken from the CDMS" (Observations and spectroscopic data) [from CDMS (cite: CDMS_1; CDMS_2)]
- External data: Solar 36Ar/38Ar value 5.50±0.01  
  > "significantly lower than the solar value $5.50 \pm 0.01$ (cite: Ar-Kr_Xe_2011)" (The 36Ar/38Ar isotopic ratio) [from Vogel et al. 2011 (cite: Ar-Kr_Xe_2011)]
- External data: Terrestrial 36Ar/38Ar 5.305±0.068  
  > "the terrestrial value of $5.305 \pm 0.068$ (cite: composition_elements_2009)" (The 36Ar/38Ar isotopic ratio) [from Berglund & Wieser (cite: composition_elements_2009)]

## Processing

### Calibration

- pipeline or manual: Standard ALMA pipeline plus one step of self-calibration  
  > "The overall standard calibration was applied by the ALMA pipeline. One more step of self-calibration was performed" (Observations and spectroscopic data)
- casa version: _not stated_
- pipeline version: _not stated_
- archive products used as is: _not stated_
- flux calibrator: _not stated_
- flux scale uncertainty: _not stated_
- self calibration: One step of self-calibration  
  > "One more step of self-calibration was performed" (Observations and spectroscopic data)

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
- smoothing: Hanning smoothing, 1.0 km/s velocity resolution  
  > "The velocity resolution is 1.0 km s$^{-1}$ after Hanning smoothing." (Observations and spectroscopic data)
- final beam: _not stated_
- final rms: _not stated_

### Inherited from earlier work

- Presentation of ALMA Cycle 0 survey toward PKS 1830-211 and overall results  
  > "see (cite: NH2_in_pks_etc_2014) for the presentation of the ALMA Cycle 0 survey and overall results" (Introduction) [from (cite: NH2_in_pks_etc_2014)]
- Isotopic invariant fit of spectroscopic data similar to earlier work  
  > "was carried out, similar to (cite: ArD+\_rot_1999)" (Observations and spectroscopic data) [from (cite: ArD+\_rot_1999)]

### Not stated but needed to reproduce (our reading)

- Flux calibrator and flux scale uncertainty
- CASA/pipeline version
- Self-calibration solution interval and reference model
- UVMULTIFIT model details (point-source positions/fluxes)
- Continuum normalization used to convert spectra to optical depth
- Line-free channels for continuum
- Spectral window/baseline details and configuration

## Analysis recipe

1. **Extract spectra toward SW and NE images**: Fit calibrated visibilities with UVMULTIFIT to point-like SW and NE images  
  > "calibrated visibilities were then fit with the task UVMULTIFIT (cite: mar14) to extract the spectra toward the point-like SW and NE images" (Observations and spectroscopic data)
   - software: UVMULTIFIT
   - fitting: _not stated_
   - validation: Atmospheric O3 lines identified as appearing at same frequency in SW and NE spectra  
  > "they occur at the same frequency in both SW and NE spectra" (Observations and spectroscopic data)
2. **Fit absorption profiles and integrate opacities**: Single Gaussian fit with common width and velocity offset for all isotopologs toward SW; also integrate optical depth over channel ranges  
  > "a simple fit with one Gaussian velocity component and the same width and velocity offset for both isotopologs" (Column densities and abundances)
   - parameter: Integration range -80 to +110 km/s (SW); -280 to -80 km/s (NE)  
  > "integrated over channels from $-$280 to $-$80 km s$^{-1}$" (Table 1)
   - fitting: _not stated_
   - validation: _not stated_
3. **Derive column densities and isotopic ratios**: Optically thin column densities from integrated opacities, then ratio of 36ArH+ to 38ArH+  
  > "the lines are optically thin, the total column densities of $^{36}$ArH$^+$ along the SW and NE lines of sight are" (Column densities and abundances)
   - assumption: Excitation temperature equals CMB temperature at z=0.89, 5.14 K; optically thin lines  
  > "the rotational excitation temperature is equal to the radiation temperature of the cosmic microwave background at $z=0.89$, 5.14 K" (Column densities and abundances)
   - fitting: _not stated_
   - validation: Ratio from integrated opacity compared with Gaussian-fit ratio (3.46 vs 3.50)  
  > "$3.50 \pm 0.14$ from the Gaussian fit" (The 36Ar/38Ar isotopic ratio)

## Software

- **UVMULTIFIT** : Fit visibilities to extract spectra toward SW and NE images  
  > "fit with the task UVMULTIFIT (cite: mar14) to extract the spectra" (Observations and spectroscopic data)
- **ALMA pipeline** : Standard calibration  
  > "The overall standard calibration was applied by the ALMA pipeline." (Observations and spectroscopic data)
- **CDMS** : Spectroscopic data of ArH+  
  > "Spectroscopic data of ArH$^+$ transitions were taken from the CDMS" (Observations and spectroscopic data)

## Numeric results

| quantity | value | uncertainty | units | step | quote |
|---|---|---|---|---|---|
| 36Ar/38Ar toward SW (integrated -80 to +110 km/s) | 3.46 | 0.16 | dimensionless | 3 | The $^{36}$Ar/$^{38}$Ar ratio is $3.46 \pm 0.16$ |
| 36Ar/38Ar toward NE | 4.53 | 0.33 | dimensionless | 3 | toward the NE image is $4.53 \pm 0.33$ |
| SW Gaussian FWHM | 57.3 | 0.8 | km/s | 2 | a full width at half maximum of $57.3 \pm 0.8$ km s$^{-1}$ |
| 36ArH+ column density SW | 2.7e13 | not stated | cm^-2 | 3 | are $2.7 \times 10^{13}$ cm$^{-2}$ and $1.3 \times 10^{13}$ cm$^{-2}$, respectively |
| 36ArH+ column density NE | 1.3e13 | not stated | cm^-2 | 3 | are $2.7 \times 10^{13}$ cm$^{-2}$ and $1.3 \times 10^{13}$ cm$^{-2}$, respectively |
| 40ArH+ opacity upper limit SW (3 sigma) | 0.42 | not stated | km/s | 2 | only an upper limit of 0.42 km s$^{-1}$ (at 3$\sigma$ confidence level) |

## Qualitative findings

- ArH+ absorption is relatively enhanced toward the more diffuse NE line of sight compared with other molecules; ArH+ and H2O+ are poorly correlated  
  > "The argonium absorption is clearly enhanced on the more diffuse line of sight (NE) compared to other molecular species." (abstract)

## Claim tuples

- H: ArH+ is detectable extragalactically and traces diffuse atomic ISM at z=0.89 | E: ALMA Band 7 absorption spectra toward the SW and NE images of PKS 1830-211 | R: 36ArH+ and 38ArH+ detected toward both images; NE/SW column density ratio ~2 versus ~10 lower H2 toward NE | F: ArH+ is suitable as a tracer of almost purely atomic diffuse ISM in distant galaxies | **supported**
- H: The 36Ar/38Ar ratio at z=0.89 differs from solar | E: Ratio of integrated opacities of 36ArH+ and 38ArH+ | R: 3.46±0.16 toward SW versus solar 5.50 | F: Significantly lower than solar toward SW; NE compatible with either | **supported**

## Reasoning

- Why this data: _not stated_
- Why this method: _not stated_
- How they decided it was enough: _not stated_
- Limitation (authors): Metallicity of the foreground galaxy cannot be determined precisely; nucleosynthesis models have uncertain assumptions  
  > "There is no evidence for low metallicity in the foreground galaxy, but the exact value cannot be determined at present." (The 36Ar/38Ar isotopic ratio)
- Caveat (inferred, ours): Optically thin assumption and Tex=TCMB not tested
- Caveat (inferred, ours): No explicit continuum covering-factor treatment stated
- Caveat (inferred, ours): Uncertainties may not include systematics from non-Gaussian profile

## Reproducibility

- Data public (paper): ALMA project data cited in acknowledgements  
  > "This paper makes use of the following ALMA data: ADS/JAO.ALMA$\#$2013.1.00296.S." (Acknowledgements)
- Products in archive: _not stated_
- Missing: Self-calibration and UVMULTIFIT settings
- Missing: Continuum level normalization
- Missing: CASA/pipeline versions
- Data volume (inferred): ~10-50 GB raw
- Score (inferred): 3/5, Short letter; data public but processing and fitting details sparse.
- Rediscovery candidate: no, Recipe lacks key calibration and fitting details.

## Links

- Method: Martí-Vidal et al. 2014 (cite: mar14) (UVMULTIFIT used for visibility fitting)
- Companion: (cite: NH2_in_pks_etc_2014) (ALMA Cycle 0 survey of PKS 1830-211)
- Companion: (cite: H2Cl+\_extragal_2014) (H2Cl+ detection toward PKS 1830-211)
- Related: ALMA Cycle 0 survey toward PKS 1830-211

## Checks

```json
{
 "quotes": 43,
 "quotes_ok": 43,
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
  "facts": 64,
  "stated": 29,
  "rate": 0.453
 },
 "evidence_ok": true
}
```
