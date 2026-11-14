# Rapidly star-forming galaxies adjacent to quasars at redshifts exceeding 6

`2017Natur.545..457D` | Nature 2017 | first author: Decarli, R. | arXiv: 1705.08662 | DOI: 10.1038/nature22358

Card schema 1.0 | model claude-sonnet-5-5 | depth full | type observational_alma_primary

## Science

- Fields: high_z_galaxies, agn_and_quasars
- Question: Are there [CII]-bright, rapidly star-forming companion galaxies near z>6 quasars, and how common are they?  
  > "We find such close companions in four out of twenty-five z >6 quasars surveyed" (abstract)
- Target **SDSS J0842+1218 and companion**: coordinates 08:42:29.43 +12:18:50.4 (quasar)  
  > "08:42:29.43|08:42:28.95" (Table 1); z/distance z[CII]=6.0760 (quasar), 6.0656 (companion)  
  > "08:42:29.43|08:42:28.95" (Table 1); distance from [CII] line Gaussian fit  
  > "08:42:29.43|08:42:28.95" (Table 1)
- Target **CFHQJ2100-1715 and companion**: coordinates 21:00:54.70 -17:15:21.9 (quasar)  
  > "21:00:54.70|21:00:55.45" (Table 1); z/distance z[CII]=6.0806 (quasar), 6.0796 (companion)  
  > "21:00:54.70|21:00:55.45" (Table 1); distance from [CII] line Gaussian fit  
  > "21:00:54.70|21:00:55.45" (Table 1)
- Target **PSO J231-20 and companion**: coordinates 15:26:37.84 -20:50:00.8 (quasar)  
  > "15:26:37.84|15:26:37.87" (Table 1); z/distance z[CII]=6.58651 (quasar), 6.5900 (companion)  
  > "15:26:37.84|15:26:37.87" (Table 1); distance from [CII] line Gaussian fit  
  > "15:26:37.84|15:26:37.87" (Table 1)
- Target **PSO J308-21 and companion**: coordinates 20:32:10.00 -21:14:02.4 (quasar)  
  > "20:32:10.00|20:32:10.17" (Table 1); z/distance z[CII]=6.2342 (quasar), 6.2485 (companion)  
  > "20:32:10.00|20:32:10.17" (Table 1); distance from [CII] line Gaussian fit  
  > "20:32:10.00|20:32:10.17" (Table 1)

## Data provenance

- ALMA projects: 2015.1.01115.S
- bands: Band 6 (1.2 mm)  
  > "for which the redshifted [CII] line would fall in ALMA band" (main text)
- frequencies and spectral setup: _not stated_
- continuum bandwidth: _not stated_
- arrays: _not stated_
- configurations: compact array configuration  
  > "The ALMA observations were carried out in compact array configuration between January 27 and March 27 2016" (Figure 1 caption)
- baselines: _not stated_
- angular resolution: beams 0.63-1.24 arcsec (natural weighting)  
  > "yielding beams of 1.20”x1.06”, 0.74”x0.63”, 1.24”x0.89”, 0.85”x0.65” (left to right)" (Figure 1 caption)
- max recoverable scale: _not stated_
- sensitivity: 0.6-0.9 mJy per beam per 30 km/s channel  
  > "all in single pointings with similar depth (0.6-0.9 mJy per beam per 30 km s [-1] channel)" (main text)
- time on source: about 10 min per observation  
  > "with onsource integration times of about 10 min" (Figure 1 caption)
- observing dates: 27 January - 27 March 2016  
  > "between January 27 and March 27 2016" (Figure 1 caption)
- pi or archival as stated: _not stated_
- Line: [CII] 158 um fine-structure (not stated)
- Other facility **HST/WFC3, LBT/LUCI, NTT/SofI, MPG/ESO 2.2m GROND**: near-infrared images of the fields  
  > "obtained with (left to right) the WFC3 instrument on the Hubble Space Telescope, the LUCI camera on the Large Binocular Telescope (LBT)" (Figure 1 caption)
- External data: Dust temperature 47 K and beta=1.6  
  > "dust opacity index of β =1.6 and dust temperature of T dust =47 K (ref. 20)" (main text) [from Beelen et al. 2006 (ref 20)]
- External data: [CII] luminosity function constraints at z>6  
  > "on the [CII] luminosity function at z >6 (refs. 25, 26)" (main text) [from Aravena et al. 2016; Swinbank et al. 2012]
- External data: Quasar-LBG clustering r0=8.83 h^-1 Mpc, gamma=2.0 at z~4  
  > "fitted for quasar-galaxy pairs at z ~4 at a fixed slope γ =2.0 (ref. 27; orange shaded area)" (Figure 3 caption) [from Garcia-Vergara et al. 2017]

## Processing

### Calibration

- pipeline or manual: _not stated_
- casa version: _not stated_
- pipeline version: _not stated_
- archive products used as is: _not stated_
- flux calibrator: nearby radio quasars used for calibration  
  > "Nearby radio quasars were used for calibration." (Figure 1 caption)
- flux scale uncertainty: _not stated_
- self calibration: _not stated_

### Imaging

- task: _not stated_
- deconvolver: _not stated_
- weighting robust: natural weighting  
  > "The images were obtained with natural weighting" (Figure 1 caption)
- uv taper: _not stated_
- cell size: _not stated_
- image size: _not stated_
- masking: _not stated_
- multiscale scales: _not stated_
- continuum subtraction: continuum-subtracted [CII] maps; spectra modelled as flat continuum plus Gaussian  
  > "The spectra are modelled as a flat continuum plus a Gaussian line (red lines)." (Figure 1 caption)
- line free channels: _not stated_
- primary beam correction: _not stated_
- array combination: _not stated_
- smoothing: _not stated_
- final beam: _not stated_
- final rms: _not stated_

### Inherited from earlier work

- Source detection algorithm and strategy for cube search  
  > "The detection algorithm and strategy follows previous work with ALMA data [18] ." (main text) [from Walter et al. 2016 (ref 18)]

### Not stated but needed to reproduce (our reading)

- CASA version and calibration procedure
- Calibrator names
- Line-free channels and channel width used for maps
- Detection algorithm details and completeness
- Spectral setup frequencies
- Image size/cell size
- Size deconvolution method details

## Analysis recipe

1. **search cubes for companions**: Search data cubes in sky position and frequency following Walter et al. 2016, with 7 sigma threshold  
  > "We imposed a conservative significance threshold of 7σ (corresponding to a [CII] luminosity of L [CII] ~10 [9] L sun" (main text)
   - fitting: _not stated_
   - validation: Chance alignment of low-z CO emitters >20 times rarer  
  > "chance alignments of low-redshift CO emitters are expected to be more than 20 times rarer at these fluxes [18]" (main text)
2. **measure line and continuum properties**: 2D Gaussian fits of maps; Gaussian line fit on spectra  
  > "refer to the two-dimensional Gaussian fit of the continuum-subtracted [CII] maps" (Table 1)
   - fitting: _not stated_
   - validation: _not stated_
3. **derive IR luminosity, SFR, dust and dynamical mass**: Modified blackbody scaled to continuum; SFR_CII=3.0e-9 L^1.18, SFR_IR=1.49e-10 L_IR; Mdyn=size sigma^2/G  
  > "The dynamical mass is computed as M dyn = size σ [CII]2 / G" (Table 1)
   - assumption: Tdust=47 K, beta=1.6, CMB-corrected, gas-to-dust ~100, LCDM H0=70, Om=0.3  
  > "Hubble constant H 0 =70 km s [-1] Mpc [-1], mass density Ω m =0.3 and vacuum density Ω Λ =0.7" (main text)
   - fitting: _not stated_
   - validation: Caution that velocity field may be perturbed and emission marginally resolved  
  > "We caution however that the velocity field of these galaxies might be perturbed" (Table 1)

## Software


## Numeric results

| quantity | value | uncertainty | units | step | quote |
|---|---|---|---|---|---|
| Companions detected | 4 of 25 quasars | not stated | dimensionless | 1 | four out of twenty-five z >6 quasars surveyed |
| SFR_IR range | 80 to ~2000 | not stated | Msun/yr | 3 | between 80 M sun yr [-1] (for the |
| L_CII of PJ231-20 companion | 4.47 | 0.53 | 1e9 Lsun | 3 | 4.47±0.53 |

## Qualitative findings

- Companion [CII] in PJ308-21 spans ~25 kpc and ~1000 km/s, suggesting tidal disruption/merger  
  > "suggesting that the companion is undergoing a tidal disruption due to interaction or merger with the quasar host" (main text)

## Claim tuples

- H: Quasar fields contain star-forming companions at z>6 | E: [CII] cube search in 25 quasar fields | R: 4 companions, SFR>100 Msun/yr | F: Companions are similar to quasar hosts but show no AGN evidence | **supported**
- H: Counts consistent with field luminosity function | E: Compare counts with LF and clustering | R: Orders of magnitude excess | F: Needs quasar-galaxy clustering | **partially**

## Reasoning

- Why this data: _not stated_
- Why this method: _not stated_
- Alternative: Lines being low-z CO rejected based on frequency offsets, line/continuum brightness, no counterparts  
  > "imply that the detected lines are also [CII]" (main text)
- How they decided it was enough: _not stated_
- Limitation (authors): [CII] only marginally resolved; dust mass lower limit if not optically thin  
  > "the [CII] emission is only marginally resolved in our observations" (Table 1)
- Caveat (inferred, ours): Redshift identification relies on [CII] without confirming second line
- Caveat (inferred, ours): Dynamical masses from marginally resolved sizes are uncertain
- Caveat (inferred, ours): Assumed Tdust drives IR luminosity and SFR

## Reproducibility

- Data public (paper): Datasets available from corresponding author on request  
  > "are available from the corresponding author on reasonable request." (Data availability statement)
- Products in archive: _not stated_
- Missing: Reduction and imaging details
- Missing: Search algorithm specifics
- Missing: Spectral setup
- Data volume (inferred): ~10-50 GB
- Score (inferred): 3/5, Short Nature letter; recipe formulas given but processing details absent.
- Rediscovery candidate: no, Processing and detection details insufficient.

## Links

- Method: Walter et al. 2016 (cite: 18) (detection algorithm)
- Related: Pan-STARRS1 distant quasar survey

## Checks

```json
{
 "quotes": 45,
 "quotes_ok": 45,
 "quote_pass_rate": 1.0,
 "quotes_too_long": 0,
 "unsupported_facts": 0,
 "project_codes": 1,
 "codes_not_in_text": [],
 "codes_not_in_obscore": [],
 "obscore_codes_not_in_card": [],
 "codes_printed_but_missing": [],
 "numeric_results": 3,
 "numeric_problems": 0,
 "fill": {
  "facts": 70,
  "stated": 37,
  "rate": 0.529
 },
 "evidence_ok": true
}
```
