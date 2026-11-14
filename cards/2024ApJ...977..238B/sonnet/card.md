# SAUNAS. II. Discovery of Cross-shaped X-Ray Emission and a Rotating Circumnuclear Disk in the Supermassive S0 Galaxy NGC 5084

`2024ApJ...977..238B` | The Astrophysical Journal 2024 | first author: Borlaff, Alejandro S. | arXiv: 2408.10449 | DOI: 10.3847/1538-4357/ad7c4b

Card schema 1.0 | model claude-sonnet-5-5 | depth light | type multi_facility_alma_minor

## Science

- Fields: nearby_galaxies, agn_and_quasars
- Question: What is the multi-wavelength structure of the S0 galaxy NGC 5084 (X-ray halo, circumnuclear disk, radio lobes) and what formation scenario explains it?  
  > "Three formation scenarios are considered to explain these multi-wavelength archival observations" (abstract)
- Target **NGC 5084**: coordinates 200.0701 deg, -21.8272 deg (ellipse centre of circumnuclear disk)  
  > "At a distance of $D=  29.91\pm2.12$ Mpc (cite: koribalski+2004aj128_16)" (2.2 Hubble Space Telescope Imaging); z/distance D = 29.91 +/- 2.12 Mpc  
  > "At a distance of $D=  29.91\pm2.12$ Mpc (cite: koribalski+2004aj128_16)" (2.2 Hubble Space Telescope Imaging); distance from Koribalski et al. 2004  
  > "At a distance of $D=  29.91\pm2.12$ Mpc (cite: koribalski+2004aj128_16)" (2.2 Hubble Space Telescope Imaging)

## Data provenance

- ALMA projects: 2015.1.00598.S
- bands: Band 6 (228.273 - 248.12 GHz)  
  > "A total of 544.32 s worth of data in Band 6 (228.273 - 248.12 GHz) were obtained" (2.3 ALMA observations)
- frequencies and spectral setup: _not stated_
- continuum bandwidth: _not stated_
- arrays: 12m  
  > "| 2015.1.00598.S | 12m       | 544      | 6      | 228.3-248.1  | 2016/04 |" (Table 1)
- configurations: _not stated_
- baselines: _not stated_
- angular resolution: 0.508 arcsec (83 pc)  
  > "with a spatial resolution of 0.508 arcsec (83 pc), and a velocity resolution of 1.272 km s$^{-1}$" (2.3 ALMA observations)
- max recoverable scale: _not stated_
- sensitivity: _not stated_
- time on source: 544.32 s  
  > "A total of 544.32 s worth of data in Band 6" (2.3 ALMA observations)
- observing dates: 2016/04  
  > "| 2015.1.00598.S | 12m       | 544      | 6      | 228.3-248.1  | 2016/04 |" (Table 1)
- pi or archival as stated: Archival; observed as part of WISDOM project  
  > "NGC 5084 was observed with ALMA as part of the WISDOM project" (2.3 ALMA observations)
- Line: CO J=2-1 (230.538 GHz)
- Other facility **Chandra/ACIS**: Archival 9.92 ks X-ray imaging, processed with SAUNAS  
  > "A total of 9.92 ks of Chandra observations, using the `VFAINT` mode, have been archived for NGC 5084" (2.1 Chandra X-ray Observatory)
- Other facility **HST (WFPC2, WFC3)**: Imaging revealing the circumnuclear dust disk  
  > "All observations were retrieved from MAST as level 3" (2.2 Hubble Space Telescope Imaging)
- Other facility **EVLA (CHANG-ES)**: 6 cm and 20 cm radio continuum showing lobes  
  > "L (20 cm) and C-band (6 cm) radio observations in the B, C, and D configurations are available as part of the CHANG-ES data archive" (2.4 CHANG-ES EVLA radio observations)
- Other facility **APO/DIS**: New optical slit spectra, 1200 s  
  > "we obtained 1200 s of slit-spectra observations using the Dual Imaging Spectrograph (DIS) at the 3.5m-Apache Point Observatory" (2.5 Optical spectroscopic observations)
- External data: Distance 29.91 +/- 2.12 Mpc  
  > "At a distance of $D=  29.91\pm2.12$ Mpc (cite: koribalski+2004aj128_16)" (2.2 Hubble Space Telescope Imaging) [from (cite: koribalski+2004aj128_16)]
- External data: M_BH-W50-inclination relation (Eq. 6)  
  > "we use the definition in (cite: smith+2021mnras500_1933) to measure the mass of the central SMBH based on their fitted relation with the line width at the half-maximum W$_{50}$" (3.3 ALMA CO(2-1) emission line observations) [from (cite: smith+2021mnras500_1933)]

## Processing

### Calibration

- pipeline or manual: _not stated_
- casa version: _not stated_
- pipeline version: _not stated_
- archive products used as is: Calibrated exposures downloaded from archive; both ALMA and ARI-L cubes available, results compatible  
  > "The calibrated exposures were downloaded from the NRAO ALMA Science Archive Data Portal" (2.3 ALMA observations)
- flux calibrator: _not stated_
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
- smoothing: Spectral rebinning to 12.9 km/s  
  > "After rebinning the datacube in the spectral axis to a velocity resolution of 12.9 km s$^{-1}$, emission lines with SNR$>3$ are detected." (3.3 ALMA CO(2-1) emission line observations)
- final beam: _not stated_
- final rms: _not stated_

### Inherited from earlier work

- W50 rotation-amplitude procedure and M_BH relation  
  > "following a similar procedure as in (cite: smith+2021mnras500_1933)" (3.3 ALMA CO(2-1) emission line observations) [from (cite: smith+2021mnras500_1933)]
- X-ray reduction via SAUNAS pipeline  
  > "Chandra/ACIS observations are reduced following the `SAUNAS` pipeline, a methodology presented in `SAUNAS I`" (2.1 Chandra X-ray Observatory) [from (cite: borlaff+2024apj967_169)]

### Not stated but needed to reproduce (our reading)

- ALMA CASA/pipeline version and whether the archive or ARI-L cube was used for the quoted numbers
- Beam, rms, image size and cell size of the cube
- Continuum subtraction and line-free channels
- Exact region and mask used when summing spectra, and what the 95% confidence masking threshold is relative to
- Distance of the HST ellipse reference points (SAODS9 selection) not reproducible exactly
- Inclination assumed in the M_BH formula (HST-derived) and how W50 was corrected for instrumental broadening

## Analysis recipe

1. **Fit disk geometry from HST dust lane**: Reference points along the F702W dust arc defined in SAODS9 and fit with an ellipse, with 1000 bootstrap/Monte Carlo realisations displacing points within the PSF FWHM  
  > "reference points across the arc dust lane using `SAODS9` were defined and then fit to an ellipse using $N=1000$ bootstrapping and Monte Carlo simulations" (3.2 Hubble Space Telescope imaging)
   - software: SAODS9
   - assumption: Distance 29.9 Mpc  
  > "corresponds to a physical area of $1.82\times1.82$ kpc$^2$ at 29.9 Mpc" (3.2 Hubble Space Telescope imaging)
   - fitting: _not stated_
   - validation: _not stated_
2. **Detect CO(2-1) and make moment maps**: Spectral rebinning to 12.9 km/s, per-pixel Gaussian fits for intensity, centroid and dispersion; pixels below 95% confidence masked  
  > "We fit Gaussian models along the spectral direction for each pixel in the cube, identifying the intensity, centroid, and dispersion of the CO(2-1) emission lines (moments 0, 1, and 2)." (3.3 ALMA CO(2-1) emission line observations)
   - fitting: Gaussian per pixel  
  > "We fit Gaussian models along the spectral direction for each pixel in the cube" (3.3 ALMA CO(2-1) emission line observations)
   - validation: Results compatible for ALMA and ARI-L cube versions  
  > "These are compatible regardless of the version of the cubes analyzed." (2.3 ALMA observations)
3. **Measure rotation velocity from summed spectrum**: Sum spectra of significant pixels, measure half-maximum velocities by interpolation, 1000 Monte Carlo realisations displacing points by noise  
  > "This process is repeated using $N=1000$ Monte Carlo simulations, with each data point being displaced by its spectral flux uncertainty (noise level)." (3.3 ALMA CO(2-1) emission line observations)
   - fitting: _not stated_
   - validation: _not stated_
4. **Derive SMBH mass**: Apply Smith et al. 2021 W50-inclination relation, propagating uncertainties of relation, inclination and spectra with Monte Carlo  
  > "The uncertainties in their fitted relation are propagated using the Monte Carlo simulations, together with those in the inclination of the disk" (3.3 ALMA CO(2-1) emission line observations)
   - assumption: Inclination from HST ellipse fit  
  > "together with those in the inclination of the disk (see Sec. [3.2](#subsec:results_hst))" (3.3 ALMA CO(2-1) emission line observations)
   - fitting: _not stated_
   - validation: Compared with local SMBH mass distribution  
  > "The measured SMBH mass is compatible with the SMBH mass distribution in the local Universe" (4.1 Main formation scenarios)

## Software

- **SAUNAS** : Chandra X-ray PSF deconvolution and adaptive binning  
  > "`SAUNAS` comprises several steps for calibration including: 1) standard pre-calibration using `CIAO`" (2.1 Chandra X-ray Observatory)
- **CIAO** : Chandra pre-calibration  
  > "standard pre-calibration using `CIAO`" (2.1 Chandra X-ray Observatory)
- **MARX** : Chandra PSF models  
  > "following the prescriptions from `MARX`" (2.1 Chandra X-ray Observatory)
- **SAODS9** : Defining dust-lane reference points  
  > "reference points across the arc dust lane using `SAODS9` were defined" (3.2 Hubble Space Telescope imaging)

## Numeric results

| quantity | value | uncertainty | units | step | quote |
|---|---|---|---|---|---|
| CO(2-1) rotation velocity | 249.1 | +12.8/-9.6 | km/s | 3 | V$_{\rm rot} = 249.1^{+12.8}_{-9.6}$ km s$^{-1}$ (W$_{50}=498^{+26}_{-19}$ km s$^{-1}$) |
| W50 | 498 | +26/-19 | km/s | 3 | W$_{50}=498^{+26}_{-19}$ km s$^{-1}$ |
| log10 M_BH/Msun | 7.66 | +0.21/-0.15 | dex | 4 | A total mass of $\log_{10}\left( \frac{M_{\rm BH}}{M_{\odot}} \right) = 7.66^{+0.21}_{-0.15}$ is determined for the SMBH of NGC 5084. |
| Circumnuclear disk inclination | 71.2 | +1.8/-1.7 | deg | 1 | with a median inclination of $i=71.2^{+1.8}_{-1.7}$ degrees |
| Circumnuclear disk diameter | 304 | +10/-11 | pc | 1 | The disk diameter is $D=304^{+10}_{-11}$ pc |

## Qualitative findings

- CO(2-1) shows edge-on rotation, north edge approaching and south receding, with emission peaks at the disk edges  
  > "The results show an unmistakable edge-on rotation pattern, with the north (south) edge of the disk moving towards (away from) the observer along the line of sight." (3.3 ALMA CO(2-1) emission line observations)

## Claim tuples

- H: Does NGC 5084 host a rotating molecular circumnuclear disk allowing an SMBH mass estimate? | E: Rebinned archival ALMA CO(2-1) cube, per-pixel Gaussian fits, W50 and inclination from HST in the Smith+2021 relation | R: V_rot = 249.1 km/s, log M_BH = 7.66 | F: A polar rotating circumnuclear disk exists with SMBH mass of about 4.6e7 Msun | **supported**

## Reasoning

- Why this data: Archival multi-wavelength data enable discovery; WISDOM ALMA data had no published NGC 5084 results  
  > "none of the papers from the WISDOM project has published any result from the NGC 5084 observations analyzed in the present work" (2.3 ALMA observations)
- Why this method: _not stated_
- How they decided it was enough: _not stated_
- Limitation (authors): Original-resolution cube has insufficient per-pixel emission; detection only after rebinning to 12.9 km/s  
  > "Initial inspection of the calibrated cube did not show sufficient emission per spaxel at the original spectral resolution of 1.3 km s$^{-1}$." (3.3 ALMA CO(2-1) emission line observations)
- Caveat (inferred, ours): Line detection is marginal (SNR>3 after heavy rebinning) and the automatic archive pipeline found no lines
- Caveat (inferred, ours): Mass from W50 scaling relation calibrated on other samples; inclination from dust lane is a model assumption
- Caveat (inferred, ours): Abstract V_rot (242.7) differs from text (249.1)

## Reproducibility

- Data public (paper): Archival public ALMA data downloaded from the ALMA Science Archive  
  > "The calibrated exposures were downloaded from the NRAO ALMA Science Archive Data Portal" (2.3 ALMA observations)
- Products in archive: _not stated_
- Missing: Moment-map masking details and summed-region definition
- Missing: Cube imaging parameters and rms
- Data volume (inferred): ~1-5 GB for the ALMA cube
- Score (inferred): 4/5, ALMA part is simple and archival with explicit method, but key settings are unstated.
- Rediscovery candidate: yes, Public archival data, short recipe, numeric results (V_rot, W50, M_BH).

## Links

- Method: (cite: smith+2021mnras500_1933) (W50 rotation measurement and M_BH relation)
- Method: (cite: borlaff+2024apj967_169) (SAUNAS X-ray pipeline)
- Companion: (cite: borlaff+2024apj967_169) (SAUNAS I)
- Related: WISDOM
- Related: CHANG-ES

## Checks

```json
{
 "quotes": 46,
 "quotes_ok": 46,
 "quote_pass_rate": 1.0,
 "quotes_too_long": 0,
 "unsupported_facts": 0,
 "project_codes": 1,
 "codes_not_in_text": [],
 "codes_not_in_obscore": [],
 "obscore_codes_not_in_card": [],
 "codes_printed_but_missing": [],
 "numeric_results": 5,
 "numeric_problems": 0,
 "fill": {
  "facts": 71,
  "stated": 37,
  "rate": 0.521
 },
 "evidence_ok": true
}
```
