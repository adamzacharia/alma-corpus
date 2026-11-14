# The multiple merger assembly of a hyperluminous obscured quasar at redshift 4.6

`2018Sci...362.1034D` | Science 2018 | first author: Díaz-Santos, T. | arXiv: 1811.05992 | DOI: 10.1126/science.aap7605

Card schema 1.0 | model claude-sonnet-5-5 | depth full | type observational_alma_primary

## Science

- Fields: agn_and_quasars, high_z_galaxies
- Question: Is the hyper-luminous obscured quasar W2246−0526 (z=4.6) undergoing a multiple merger, with dusty bridges and tidal tails connecting it to companion galaxies?  
  > "We report spectroscopic imaging of a multiple merger event in the most luminous known galaxy, WISE J224607.56−052634.9 (W2246−0526), a dustobscured quasar at redshift 4.6" (abstract)
- Target **W2246−0526**: coordinates 22h 46m 07.55s, −05° 26′ 35.0″  
  > "whose coordinates are: 22h 46m 07.55s, −05° 26′ 35.0″" (Figure 1 caption); "At the redshift of W2246−0526, z = 4.601, the angular scale is 1′′ = 6.68 kpc." (Cosmology); z/distance z = 4.601  
  > "whose coordinates are: 22h 46m 07.55s, −05° 26′ 35.0″" (Figure 1 caption); "At the redshift of W2246−0526, z = 4.601, the angular scale is 1′′ = 6.68 kpc." (Cosmology); distance from [C II] redshift from ALMA (Diaz-Santos et al. 2016), matched by Keck Lyα  
  > "whose coordinates are: 22h 46m 07.55s, −05° 26′ 35.0″" (Figure 1 caption); "At the redshift of W2246−0526, z = 4.601, the angular scale is 1′′ = 6.68 kpc." (Cosmology)

## Data provenance

- ALMA projects: 2015.1.00883.S
- bands: Band 6 (211–275 GHz)  
  > "were obtained in Band 6 (211–275 GHz) during 3 execution blocks" (ALMA 212µm Dust Continuum Data)
- frequencies and spectral setup: four SPWs; SPW0 centred at ~260.929 GHz (rest ~205 µm), SPW3 rest ~219 µm  
  > "central observed frequency υ obs ~ 260.929 GHz; rest wavelength λ rest ~ 205 µm" (ALMA 212µm Dust Continuum Data)
- continuum bandwidth: _not stated_
- arrays: _not stated_
- configurations: _not stated_
- baselines: 15.1 to 704.1 m  
  > "The minimum and maximum baseline lengths were 15.1 and 704.1 m." (ALMA 212µm Dust Continuum Data)
- angular resolution: 0.54″ × 0.46″ average (0.52×0.44 to 0.56×0.48), PA ~80°  
  > "with an average of 0.54″ × 0.46″ at an effective λ rest ~ 212 µm" (ALMA 212µm Dust Continuum Data)
- max recoverable scale: _not stated_
- sensitivity: ~125 µJy/beam/channel in 48 km/s channels; 11.5 µJy/beam in moment-0 map  
  > "reaching a r.m.s. = 11.5 µJy beam [-1] ." (ALMA 212µm Dust Continuum Data)
- time on source: 49 min per block, 2.5 hours total  
  > "The on-source integration time was 49 min per block, for a total of 2.5 hours." (ALMA 212µm Dust Continuum Data)
- observing dates: 2016 June 20 (two blocks) and 2016 July 13  
  > "two on 2016 June 20 and" (ALMA 212µm Dust Continuum Data)
- pi or archival as stated: _not stated_
- Line: CO J=2-1 (VLA) (230.538 GHz)
- Other facility **VLA**: CO(2-1) map, D-configuration, Q-band, project 15B-192  
  > "The observations were taken in Dconfiguration with 27 antennas, using the Q-band receivers" (VLA CO(2→1) Data)
- Other facility **Keck/LRIS**: Optical spectra confirming Lyα redshift and C3  
  > "We observed W2246−0526 multiple times with the dual-beam Low Resolution Imaging Spectrometer (LRIS)" (Keck/LRIS spectrum)
- Other facility **HST**: F160W rest-frame near-UV image  
  > "The UV image was obtained with the Hubble Space Telescope (HST) using the near-IR F160W filter" (abstract)
- External data: Earlier ALMA [C II] data: redshift, companions, 7.4 mJy flux density at 158 µm, line luminosities  
  > "ALMA observations showed that the dust continuum flux density at rest-frame ~ 158 µm is 7.4 mJy" (Materials and Methods) [from Diaz-Santos et al., ApJL 816, 6 (2016)]
- External data: Photometry for SED: Spitzer, WISE, Herschel SPIRE, Ks  
  > "Herschel at 250, 350 and 500 µm with the Spectral and Photometric Imaging Receiver (SPIRE)" (Materials and Methods) [from Tsai et al. 2015; Griffith et al. 2012; Wright et al. 2010; Assef et al. 2015]

## Processing

### Calibration

- pipeline or manual: _not stated_
- casa version: CASA v.5.1.1  
  > "We used the Common Astronomy Software Application (CASA; v.5.1.1)" (ALMA 212µm Dust Continuum Data)
- pipeline version: _not stated_
- archive products used as is: _not stated_
- flux calibrator: Pallas and QSO J2148+0657 (amplitude)  
  > "The sources Pallas and QSO J2148+0657 were used for amplitude calibration" (ALMA 212µm Dust Continuum Data)
- flux scale uncertainty: _not stated_
- self calibration: _not stated_

### Imaging

- task: tclean, parallelized; EBs concatenated  
  > "The cleaning algorithm was run using the task tclean in parallelized process" (ALMA 212µm Dust Continuum Data)
- deconvolver: hogbom  
  > "a hogbom deconvolver" (ALMA 212µm Dust Continuum Data)
- weighting robust: briggs, robust = 2  
  > "a robust parameter set to = 2 (similar to natural weighting)" (ALMA 212µm Dust Continuum Data)
- uv taper: taper giving FWHM ~1″ (check map)  
  > "We also cleaned the image of W2246−0526 using a uv -tapering resulting in a FWHM ~ 1″." (ALMA 212µm Dust Continuum Data)
- cell size: _not stated_
- image size: _not stated_
- masking: single circular aperture of radius 1″ on the core; clean to 2×rms  
  > "A single circular aperture of radius = 1″ was used to mask the core of W2246−0526, cleaning each window down to a depth of 2 times the r.m.s.." (ALMA 212µm Dust Continuum Data)
- multiscale scales: _not stated_
- continuum subtraction: _not stated_
- line free channels: _not stated_
- primary beam correction: _not stated_
- array combination: _not stated_
- smoothing: _not stated_
- final beam: 0.54″ × 0.46″  
  > "The angular resolution (beam size FWHM) of the observations is 0.54″ × 0.46″" (Figure 1 caption)
- final rms: _not stated_

### Inherited from earlier work

- Stellar mass SED fitting approach  
  > "To estimate the stellar mass of W2246−0526 we follow the same approach as (10)" (Materials and Methods) [from Assef et al. 2015 (cite 10)]

### Not stated but needed to reproduce (our reading)

- Line-free channels / how continuum cube was built from SPWs and which channels were discarded
- Flux calibration details (pipeline vs manual) and flux scale uncertainty
- Mask for extended emission/companions during cleaning
- Aperture photometry method for companions and tail
- Image size and cell size
- Self-calibration use

## Analysis recipe

1. **Image ALMA 212 µm continuum**: Concatenate EBs and clean with tclean, collapse four SPWs to moment-0 map  
  > "we collapsed the dust continuum emission of all four SPWs after discarding bad channels at the edges of the SPWs" (ALMA 212µm Dust Continuum Data)
   - software: CASA, tclean
   - parameter: briggs robust=2, hogbom, 1″ mask, 2σ clean depth  
  > "cleaning each window down to a depth of 2 times the r.m.s.." (ALMA 212µm Dust Continuum Data)
   - fitting: _not stated_
   - validation: Each EB imaged separately, check source imaged, uv-tapered map made  
  > "we processed and analyzed each execution block independently" (ALMA 212µm Dust Continuum Data)
2. **Image VLA CO(2-1)**: AIPS/CASA calibration, tclean with briggs robust=2, hogbom, primary beam corrected  
  > "The data were imaged using the tclean algorithm in CASA. All images were primary beam corrected." (VLA CO(2→1) Data)
   - software: AIPS, CASA
   - fitting: Gaussian fit to CO spectrum  
  > "The blue line is a Gaussian model fitted to the CO(2→1) spectrum, which results in a FWHM = 615 km s [-1] ." (Figure S3. caption)
   - validation: _not stated_
3. **Derive dust and gas masses**: Optically thin modified blackbody scaled to continuum flux; gas = 100 × dust; CO-based gas with alpha_CO  
  > "we use a modified blackbody function scaled to the continuum flux density of each source" (Calculation of Dust and Gas Masses)
   - parameter: Tdust 50–100 K for W2246, 25–50 K for companions/extended  
  > "we adopt a reasonable temperature range of T dust = 50–100 K for the Rayleigh-Jeans tail emission" (Calculation of Dust and Gas Masses)
   - assumption: beta=1.8, kappa(850µm)=0.0484 m2/kg, gas-to-dust 100, alpha_CO,MW=4.6 and ULIRG=0.8  
  > "We further assume that the dust emission is optically thin, with an emissivity index β = 1.8" (Calculation of Dust and Gas Masses)
   - fitting: _not stated_
   - validation: Dust-based gas compared with CO-based gas and dynamical mass  
  > "which slightly favors an α CO conversion factor closer to the ULIRG regime" (Calculation of Dust and Gas Masses)
4. **Stellar mass and SFR via SED fitting**: Empirical AGN + galaxy templates (Assef 2010), mass-to-light via ezgal/Galaxev  
  > "we follow (10) and derive the mass-to-light ratio of the host using the code ezgal (52) and the Galaxev stellar population SED models (53)" (Materials and Methods)
   - software: ezgal, Sextractor
   - assumption: Z=0.008, Chabrier IMF, exponentially declining SFHs  
  > "with a metallicity Z = 0.008 (≡ 0.4 Z ¤, where Z ¤ is the metallicity of the Sun) and a Chabrier IMF" (Materials and Methods)
   - fitting: non-negative combination of E, Sbc, Im and AGN templates  
  > "An object is modeled as a non-negative combination of an old stellar population (E template), an intermediate stellar population (Sbc template), a young stellar population (Im template) and an AGN." (Materials and Methods)
   - validation: Tested contamination and host reddening  
  > "the change in M ★ would be well within the error of a factor of two quoted below" (Materials and Methods)
5. **Dynamical mass, free-fall time and accretion rate**: Dispersion-supported Mdyn from [C II] FWHM and size; tff at C3 distance; dMgas/dt = gas mass / tff  
  > "by assuming that it is dispersionsupported" (Calculation of the Dynamical Mass and Accretion Rate)
   - fitting: _not stated_
   - validation: Mbar compared with Mdyn within factor 2  
  > "agrees with M dyn within a factor of ~ 2" (Calculation of the Dynamical Mass and Accretion Rate)

## Software

- **CASA** 5.1.1: ALMA and VLA processing and tclean imaging  
  > "We used the Common Astronomy Software Application (CASA; v.5.1.1)" (ALMA 212µm Dust Continuum Data)
- **AIPS** : VLA calibration  
  > "The data were calibrated using the Astronomical Image Processing System (AIPS)" (VLA CO(2→1) Data)
- **Sextractor** : Spitzer photometry  
  > "the Spitzer photometry was obtained with a 6″-diameter circular aperture using Sextractor" (Materials and Methods)
- **ezgal** : Mass-to-light ratio  
  > "using the code ezgal (52)" (Materials and Methods)

## Numeric results

| quantity | value | uncertainty | units | step | quote |
|---|---|---|---|---|---|
| Dust mass of W2246−0526 (central 1″) | 5.6–17 × 10^8 | not stated | Msun | 3 | This corresponds to a dust mass in the range M dust ~ 5.6–17 × 10 [8 ] M ¤ ( T dust = 100–50 K, respectively). |
| 212 µm flux density of W2246−0526 (1″ aperture) | 2.3 | 0.1 | mJy | 1 | is 2.3 ± 0.1 mJy |
| Total gas mass of system from dust | 1.2–3.6 × 10^11 | not stated | Msun | 3 | the entire system could contain as much as M gas = 1.2–3.6 × 10 [11 ] M ¤ . |
| Dynamical mass of W2246−0526 | 0.8 | 0.4 | 1e11 Msun | 5 | We obtain M dyn = 0.8 (± 0.4) 10 [11] M ¤ |
| CO(2-1) luminosity | 3.3 | 0.7 | 1e7 Lsun | 3 | L CO(2→1) = 3.3 (±0.7) × 10 [7 ] L ¤ |
| Average gas accretion rate | ~550–900 | not stated | Msun/yr | 5 | the average accretion rate of gas towards the center of W2246−0526 could be as high as dM gas / dt ~ 550–900 M ¤ yr [-1] |

## Qualitative findings

- Dust bridges and a ≥35 kpc tidal tail connect W2246−0526 to companions C1–C3, implying accretion of neighbours.  
  > "The detection of tidal dusty bridges shows that W2246−0526 is accreting its neighbors" (abstract)

## Claim tuples

- H: W2246−0526 is interacting with companions | E: Deep ALMA 212 µm continuum imaging at 0.5″ | R: Dust bridges and a tidal tail over at least 35 kpc connect the quasar to C1–C3 | F: The system is undergoing a multiple merger and accreting neighbours | **supported**
- H: Dust-based and CO-based gas masses agree | E: Modified blackbody dust mass with gas-to-dust 100 vs CO(2-1) from VLA | R: 1.2–3.6e11 vs 1.5e11 Msun | F: Consistent, favouring ULIRG alpha_CO | **supported**
- H: Tail dust is heated by in-situ star formation rather than the AGN | E: Compare AGN heating, UV counterpart, cooling arguments | R: K1 has UV counterpart; AGN heating needs complex geometry | F: In-situ star formation favoured | **partially**

## Reasoning

- Why this data: _not stated_
- Why this method: _not stated_
- Alternative: AGN heating and passive cooling of tail dust considered; cooling called highly unlikely  
  > "However, this case is highly unlikely since dust is a very efficient coolant." (Possible Heating Mechanisms for the Dust in the Tidal Tail)
- How they decided it was enough: _not stated_
- Limitation (authors): U1 may be at a different redshift; stellar mass and SFR uncertain by factor of 2  
  > "both with an uncertainty of a factor of 2" (Materials and Methods)
- Caveat (inferred, ours): Tail significance is low (2–3σ contours) at natural weighting
- Caveat (inferred, ours): Dust temperature assumptions drive mass estimates
- Caveat (inferred, ours): Companion redshifts for tail features not confirmed
- Caveat (inferred, ours): Single-pointing, no kinematic modelling of bridges

## Reproducibility

- Data public (paper): ALMA project 2015.1.00883.S and VLA 15B-192 available from archives  
  > "This work is based on ALMA observations available from http://almascience.nrao.edu/aq/ under project 2015.1.00883.S" (Data and materials availability)
- Products in archive: _not stated_
- Missing: Cell/image size
- Missing: Aperture and mask definitions for photometry
- Missing: Line-free channel selection
- Missing: Exact SED fitting inputs
- Data volume (inferred): ~20-50 GB for ALMA raw plus VLA data
- Score (inferred): 3/5, Imaging recipe mostly given, but photometry and many setup details are unstated.
- Rediscovery candidate: yes, Public data, clear imaging parameters and numeric fluxes and masses.

## Links

- Method: Assef et al. 2015 (cite 10) (Stellar-mass SED fitting approach)
- Companion: Diaz-Santos et al. 2016, ApJL 816, 6 (Earlier ALMA [C II] observations of W2246−0526)
- Related: WISE
- Related: Hot DOGs

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
 "numeric_results": 6,
 "numeric_problems": 0,
 "fill": {
  "facts": 75,
  "stated": 48,
  "rate": 0.64
 },
 "evidence_ok": true
}
```
