# The Strikingly Uniform, Highly Turbulent Interstellar Medium of the Most Luminous Galaxy in the Universe

`2016ApJ...816L...6D` | The Astrophysical Journal Letters 2016 | first author: Díaz-Santos, T. | arXiv: 1511.04079 | DOI: 10.3847/2041-8205/816/1/L6

Card schema 1.0 | model claude-sonnet-5-5 | depth full | type observational_alma_primary

## Science

- Fields: high_z_galaxies, agn_and_quasars
- Question: What are the ISM kinematics and [C II]/FIR conditions in the Hot DOG W2246-0526, and is its AGN driving gas out of the system?  
  > "Here we present spatially resolved ALMA \[C ii\]157.7$\,\mu$m  observations of W2246-0526, providing unique insight into the kinematics of its interstellar medium (ISM)." (abstract)
- Target **W2246-0526**: coordinates _not stated_; z/distance z = 4.601 ± 0.001  
  > "At a redshift z = 4.601 ± 0.001, it is the most luminous galaxy known in the Universe" (Introduction); distance from [C II] line (optical redshift from Wu et al. 2012 used for spectral setup)  
  > "At a redshift z = 4.601 ± 0.001, it is the most luminous galaxy known in the Universe" (Introduction)

## Data provenance

- ALMA projects: 2013.1.00576.S
- bands: Band 7  
  > "were carried out on 2014-06-29 and 2014-12-07 in band 7 using four spectral windows in the largest bandwidth mode (1.875 GHz)" (2 Observations and Analysis)
- frequencies and spectral setup: four spectral windows of 1.875 GHz; [CII] centered in spw0, other three on continuum  
  > "The [C ii] line was placed at the center of the reference spectral window (spw0)" (2 Observations and Analysis)
- continuum bandwidth: _not stated_
- arrays: _not stated_
- configurations: C34-4  
  > "The on-source integration time was 956 s in array configuration C34-4." (2 Observations and Analysis)
- baselines: _not stated_
- angular resolution: 0.386'' x 0.356'', P.A. 47 deg  
  > "The angular resolution of the observations (clean beam FWHM) is 0.386$''$ $\times$ 0.356$''$, with a major-axis position angle (P.A.) of 47$^{\circ}$" (2 Observations and Analysis)
- max recoverable scale: _not stated_
- sensitivity: 0.6 mJy/beam rms in 35 km/s channels  
  > "The r.m.s. of the observations is 0.6 mJy/beam, measured in 35 km$\,$s$^{-1}$ channel bins." (2 Observations and Analysis)
- time on source: 956 s  
  > "The on-source integration time was 956 s in array configuration C34-4." (2 Observations and Analysis)
- observing dates: 2014-06-29 and 2014-12-07  
  > "were carried out on 2014-06-29 and 2014-12-07 in band 7" (2 Observations and Analysis)
- pi or archival as stated: _not stated_
- Line: [C II] 2P3/2 -> 2P1/2 (157.7 μm)
- Other facility **HST WFC3**: Rest-frame UV image (F160W)  
  > "W2246-0526 is also detected in Hubble Space Telescope (HST) WFC3 rest-frame UV images (F160W" (3 Results)
- External data: Optical-line redshift used to set the spectral window  
  > "assuming the redshift derived from optical lines (cite: Wu2012)" (2 Observations and Analysis) [from (cite: Wu2012)]
- External data: SED-based IR and FIR luminosities (interpolated photometry)  
  > "See (cite: Eisenhardt2012) and (cite: Tsai2015) for more details." (Footnote 2) [from (cite: Eisenhardt2012); (cite: Tsai2015)]
- External data: Mrk 231 [CII] luminosity and velocity dispersion comparison  
  > "the velocity dispersion is $>\,$2 times larger (cite: Fischer2010)" (4.1 The [C ii]/FIR Deficit) [from (cite: Fischer2010)]

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

- task: CASA clean  
  > "We used the CASA software to process and clean the data." (2 Observations and Analysis)
- deconvolver: _not stated_
- weighting robust: natural weighting  
  > "The cleaning algorithm was run using a natural weighting for the u-v visibility plane" (2 Observations and Analysis)
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
- final beam: 0.386'' x 0.356'', P.A. 47 deg  
  > "clean beam FWHM) is 0.386$''$ $\times$ 0.356$''$" (2 Observations and Analysis)
- final rms: 0.6 mJy/beam in 35 km/s channels  
  > "The r.m.s. of the observations is 0.6 mJy/beam" (2 Observations and Analysis)

### Inherited from earlier work

- Rotational shear contamination of velocity dispersion computed following De Breuck et al.  
  > "following (cite: DeBreuck2014), we calculated that rotational shear can contaminate the velocity dispersion by only $<\,10$%." (4.2) [from (cite: DeBreuck2014)]

### Not stated but needed to reproduce (our reading)

- CASA version and calibration procedure (pipeline or manual), calibrators, flux scale
- Cell size, image size, clean threshold and masks
- Continuum subtraction and line-free channels
- Method and tool for moment maps and velocity dispersion
- Details of SED fit for L_IR and L_FIR
- Gas fraction and efficiency adopted in stability argument

## Analysis recipe

1. **Image cube and extract spectrum**: CASA cleaning with natural weighting; spectrum in 1'' circular aperture; Gaussian line fit  
  > "The total Gaussian flux measured from a spectrum extracted with a 1$''$ diameter circular aperture centered on W2246-0526 is 9.3 $\pm$ 0.3 Jy km$\,$s$^{-1}$." (2 Observations and Analysis)
   - software: CASA
   - fitting: Gaussian line profile  
  > "A Gaussian fits the emission profile well" (2 Observations and Analysis)
   - validation: 7% of line flux outside window  
  > "consistent with only 7% of the total line flux lying outside of the observed window" (2 Observations and Analysis)
2. **Measure sizes**: 2-D asymmetric Gaussian fits to line and continuum, beam deconvolved  
  > "Using an asymmetric, 2-D Gaussian function to fit the observed widths of the [C ii] line and dust continuum emission" (2 Observations and Analysis)
   - fitting: _not stated_
   - validation: _not stated_
3. **Subtract unresolved central component**: Scaled clean beam subtracted from line and continuum images  
  > "The beam was scaled to minimize the dispersion in the central 0.5$''$ region of the residual map" (3 Results)
   - fitting: _not stated_
   - validation: _not stated_
4. **[CII]/FIR ratio and kinematics**: Ratio of L[CII] to SED-derived L_FIR; moment maps; compare L_bol to momentum- and energy-driven wind luminosity limits  
  > "cannot be stable in terms of the radiation pressure of photons on dust grains alone" (4.3)
   - assumption: f_g ~ 1 extreme case; cosmology Omega_M=0.3, Omega_L=0.7, H0=70  
  > "Even for an unrealistic extreme $f_{\rm g}\,\approx\,$1" (4.3)
   - fitting: _not stated_
   - validation: _not stated_

## Software

- **CASA** : processing and cleaning data  
  > "We used the CASA software to process and clean the data." (2 Observations and Analysis)

## Numeric results

| quantity | value | uncertainty | units | step | quote |
|---|---|---|---|---|---|
| [CII] line flux | 9.3 | 0.3 | Jy km/s | 1 | is 9.3 $\pm$ 0.3 Jy km$\,$s$^{-1}$ |
| continuum flux density | 7.4 | 0.6 | mJy | 1 | The observed-frame continuum flux density underlying the emission line is 7.4 $\pm$ 0.6 mJy. |
| [CII] intrinsic size FWHM | 2.5 | 0.3 | kpc | 2 | the intrinsic size (FWHM) of the resolved [C ii] emission is 2.5 $\pm$ 0.3 kpc |
| continuum size | 1.3 | 0.5 | kpc | 2 | the continuum emission is only 1.3 $\pm$ 0.5 kpc wide |
| L[CII] | 6.1e9 | 0.4e9 | Lsun | 4 | $L_{\rm [C\,{\sc II}]}$ = 6.1 ($\pm$ 0.4) $\times\,10^9\,\hbox{$L_\odot$}$ |
| [CII]/FIR ratio | ~2e-4 | not stated | dimensionless | 4 | This results in an integrated [C ii]/FIR ratio of $\sim\,2\,\times\,10^{-4}$ |
| [CII] velocity dispersion FWHM | 500-600 | not stated | km/s | 4 | FWHM $\simeq\,500-600$ km$\,$s$^{-1}$ |

## Qualitative findings

- Velocity dispersion is uniform across the host with modest shear, implying a turbulent ISM  
  > "the high dispersion-to-shear ratio suggests an extremely turbulent ISM" (4.2)

## Claim tuples

- H: Is the ISM of W2246-0526 turbulent and uniform? | E: [CII] moment maps | R: FWHM 500-600 km/s across region, shear ~150 km/s | F: highly turbulent, not a relaxed disk | **supported**
- H: Does W2246-0526 show a [CII] deficit? | E: L[CII]/L_FIR | R: ~2e-4 | F: comparable only to the most obscured local nuclei | **supported**
- H: Is the AGN blowing out the gas isotropically? | E: Compare L_bol with momentum- and energy-driven limits | R: L_bol at least twice threshold even for f_g~1 | F: gas likely blown away isotropically | **partially**

## Reasoning

- Why this data: _not stated_
- Why this method: _not stated_
- How they decided it was enough: _not stated_
- Limitation (authors): Line window missed part of the red wing  
  > "was observed in a spectral window that missed part of the red wing of the line" (2 Observations and Analysis)
- Caveat (inferred, ours): Single short observation; blow-out inference relies on an assumed gas fraction and efficiency
- Caveat (inferred, ours): No kinematic modelling; sigma may include beam smearing and unresolved AGN-driven components
- Caveat (inferred, ours): Clean-beam PSF subtraction is simplistic

## Reproducibility

- Data public (paper): _not stated_
- Products in archive: _not stated_
- Missing: CASA version and calibration details
- Missing: Moment-map and clipping procedure
- Missing: SED fit details
- Data volume (inferred): ~10-30 GB raw
- Score (inferred): 4/5, Single public dataset and simple analysis, but processing details are sparse.
- Rediscovery candidate: no, Imaging and moment-map settings are not given, so the recipe is incomplete.

## Links

- Method: (cite: DeBreuck2014) (shear contamination of velocity dispersion)
- Companion: (cite: Tsai2015) (W2246-0526 SED and luminosity)
- Related: WISE Hot DOGs

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
 "codes_printed_but_missing": [],
 "numeric_results": 7,
 "numeric_problems": 0,
 "fill": {
  "facts": 64,
  "stated": 29,
  "rate": 0.453
 },
 "evidence_ok": true
}
```
