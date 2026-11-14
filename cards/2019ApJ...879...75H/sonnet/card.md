# Jet-driven Galaxy-scale Gas Outflows in the Hyperluminous Quasar 3C 273

`2019ApJ...879...75H` | The Astrophysical Journal 2019 | first author: Husemann, Bernd | arXiv: 1905.10387 | DOI: 10.3847/1538-4357/ab24bc

Card schema 1.0 | model claude-sonnet-5-5 | depth light | type multi_facility_alma_minor

## Science

- Fields: agn_and_quasars
- Question: What are the morphology and kinematics of the ionized (ENLR) and molecular gas around the hyper-luminous quasar 3C 273, and is the outflow jet- or radiation-driven?  
  > "We present an unprecedented view on the morphology and kinematics of the extended narrow-line region (ENLR) and molecular gas around the prototypical hyper-luminous quasar 3C 273" (abstract)
- Target **3C 273**: coordinates _not stated_; z/distance z=0.158 (systemic z=0.15850±0.00005 from stellar fit); 2.73 kpc/arcsec  
  > "hyper-luminous quasar 3C 273 ($L_\mathrm{bol}\sim10^{47}\mathrm{erg\,s}^{-1}$ at $z=0.158$)" (abstract); "corresponding to 2.73kpc/$''$ at the redshift of 3C 273." (Introduction); distance from flat LCDM H0=70, Om=0.3, OL=0.7  
  > "hyper-luminous quasar 3C 273 ($L_\mathrm{bol}\sim10^{47}\mathrm{erg\,s}^{-1}$ at $z=0.158$)" (abstract); "corresponding to 2.73kpc/$''$ at the redshift of 3C 273." (Introduction)

## Data provenance

- ALMA projects: 2015.1.00329.S, 2015.1.00587.S, 2015.1.01012.S, 2016.1.00972.S, 2016.1.01308.S
- bands: _not stated_
- frequencies and spectral setup: 2 GHz window (15.625 MHz raw resolution) over redshifted CO(1-0) in all but one case; one 1850 MHz window with 3.906 MHz resolution  
  > "In all but one case a 2 GHz correlator window (with a raw spectral resolution of 15.625 MHz) was present over the redshifted frequency of CO(1-0)." (2.2 ALMA observations)
- continuum bandwidth: _not stated_
- arrays: _not stated_
- configurations: _not stated_
- baselines: _not stated_
- angular resolution: 0.78" x 0.75" beam at PA 37 deg (~2.1 kpc), natural weighting  
  > "yielding a synthesized beam of 0.78$''$ $\times$ 0.75$''$ at a position angle of 37$^{\circ}$ (a physical resolution of $\approx$2.1 kpc)" (2.2 ALMA observations)
- max recoverable scale: _not stated_
- sensitivity: 0.18 mJy/beam per 30 km/s channel  
  > "with a RMS noise levels 0.18 mJy beam$^{-1}$ in each 30 km s$^{-1}$ channel." (2.2 ALMA observations)
- time on source: 8 tracks, ~5 min each on 3C 273 (bandpass calibrator)  
  > "This included 8 different tracks from 5 different ALMA projects, all of which observed 3C 273 for $\approx$5 minutes in order to use it as a bandpass calibrator." (2.2 ALMA observations)
- observing dates: _not stated_
- pi or archival as stated: archival data, 3C 273 used as ALMA calibrator  
  > "ALMA uses 3C 273 as a calibrator so that a large number of short observations of this source are available." (2.2 ALMA observations)
- Line: 12CO J=1-0 (not stated)
- Other facility **VLT-MUSE**: Optical IFU data cube (ESO program 097.B-0080(A)) for ionized gas  
  > "MUSE data of 3C 273 were obtained under ESO program 097.B-0080(A) on 31 March 2016" (2.1 MUSE observations)
- Other facility **HST**: Literature images used for comparison with molecular arc  
  > "It seems consistent with the dust lane identified in coronagraphic images presented by (cite: Martel:2003)" (2.2 ALMA observations)
- External data: Jet axis ~20 deg from line of sight and jet age 1e5 yr  
  > "the well-constrained jet axis about $\sim20^\circ$ away from our line-of-sight (cite: Stawarz:2004)" (3.2) [from (cite: Stawarz:2004)]
- External data: M_BH ~5e9 Msun  
  > "adopting $M_\mathrm{BH}\sim5\times10^9\,M_\odot$ (cite: Kaspi:2000)" (3.1) [from (cite: Kaspi:2000)]

## Processing

### Calibration

- pipeline or manual: standard ALMA pipeline in CASA plus additional flagging  
  > "The raw ALMA data for each track were calibrated using the standard ALMA pipeline in the `Common Astronomy Software Applications` (`CASA)` package." (2.2 ALMA observations)
- casa version: _not stated_
- pipeline version: _not stated_
- archive products used as is: _not stated_
- flux calibrator: _not stated_
- flux scale uncertainty: _not stated_
- self calibration: three iterations of self-calibration on bright continuum  
  > "Three iterations of self calibration were used to improve the phase and amplitude calibration of the data on the bright continuum in 3C 273." (2.2 ALMA observations)

### Imaging

- task: _not stated_
- deconvolver: _not stated_
- weighting robust: natural weighting  
  > "The data presented here were produced using natural weighting" (2.2 ALMA observations)
- uv taper: _not stated_
- cell size: 0.2 arcsec pixels, 30 km/s channels  
  > "We use data with a channel width of 30 km s$^{-1}$, and pixels of 0.2$''$" (2.2 ALMA observations)
- image size: _not stated_
- masking: interactive clean regions; threshold 1.5x RMS of dirty channels  
  > "The continuum-subtracted dirty cubes were cleaned in regions of source emission (identified interactively) to a threshold equal to 1.5 times the RMS noise of the dirty channels." (2.2 ALMA observations)
- multiscale scales: _not stated_
- continuum subtraction: uvcontsub in uv plane  
  > "We subtracted the continuum emission from the data in the $uv$ plane using the `CASA` task `uvcontsub`." (2.2 ALMA observations)
- line free channels: _not stated_
- primary beam correction: _not stated_
- array combination: _not stated_
- smoothing: _not stated_
- final beam: clean components restored with Gaussian equal to dirty beam FWHM  
  > "The clean components were then added back and re-convolved using a Gaussian beam of full-width-at-half-maximum (FWHM) equal to that of the dirty beam." (2.2 ALMA observations)
- final rms: 0.18 mJy/beam per 30 km/s channel  
  > "with a RMS noise levels 0.18 mJy beam$^{-1}$ in each 30 km s$^{-1}$ channel." (2.2 ALMA observations)

### Not stated but needed to reproduce (our reading)

- CASA version and pipeline version
- Which tracks/execution blocks were combined and the exact combination procedure
- Line-free channels and continuum fit order for uvcontsub
- Self-calibration solution intervals
- Flux calibration scheme/scale uncertainty
- Rest frequency and velocity reference used for the CO moment maps
- Hanning smoothing width and masking details
- MUSE-ALMA kinematic comparison details and the 3-sigma/inclination derivation steps

## Analysis recipe

1. **Calibrate, self-calibrate and image CO(1-0) cube**: Standard pipeline, extra flagging, self-cal on continuum, natural weighting, uvcontsub, interactive cleaning to 1.5 sigma  
  > "Additional flagging was carried out where necessary to improve the data quality." (2.2 ALMA observations)
   - software: CASA
   - parameter: 30 km/s channels, 0.2" pixels  
  > "We use data with a channel width of 30 km s$^{-1}$, and pixels of 0.2$''$" (2.2 ALMA observations)
   - fitting: _not stated_
   - validation: _not stated_
2. **Derive H2 mass from CO intensity**: Integrated intensity converted with alpha_CO  
  > "This corresponds to an H$_2$ mass of (1.7$\pm$0.3)$\times10^9$ M$_{\odot}$ assuming an $\alpha_{\rm CO}$ = 0.8" (2.2 ALMA observations)
   - assumption: alpha_CO = 0.8 Msun (K km/s pc^2)^-1; Galactic value would raise mass by 5.5  
  > "If we were instead to use a Galactic $\alpha_{CO}$ then the derived H$_2$ mass in this system would increase by a factor of 5.5." (2.2 ALMA observations)
   - fitting: _not stated_
   - validation: _not stated_
3. **Make masked moment maps**: Cube smoothed spatially (beam FWHM) and Hanning in velocity; 3D mask at 1.5 sigma; moments from unsmoothed cube within mask  
  > "A three-dimensional mask was then defined by selecting all pixels above a fixed flux threshold of 1.5 $\sigma$" (2.2 ALMA observations)
   - fitting: _not stated_
   - validation: threshold adjusted to recover flux while minimizing noise  
  > "adjusted to recover as much flux as possible in the moment maps while minimizing the noise" (2.2 ALMA observations)

## Software

- **CASA** : ALMA calibration, uvcontsub, cleaning  
  > "We subtracted the continuum emission from the data in the $uv$ plane using the `CASA` task `uvcontsub`." (2.2 ALMA observations)
- **QDEBLEND3D** : AGN-host deblending of MUSE data  
  > "We use the software QDEBLEND${}^{\mathrm{3D}}$ (cite: Husemann:2013a; Husemann:2014) to estimate the point-spread function" (2.1 MUSE observations)
- **PYPARADISE** : stellar continuum fit of MUSE data  
  > "We modelled the stellar continuum by fitting stellar templates from the INDO U.S. library (cite: Valdes:2004) using the PYPARADISE software" (2.1 MUSE observations)

## Numeric results

| quantity | value | uncertainty | units | step | quote |
|---|---|---|---|---|---|
| CO(1-0) integrated intensity | 1.82 | 0.02 | Jy km/s | 1 | an integrated intensity of 1.82$\pm$0.02 Jy km s$^{-1}$ |
| H2 mass | 1.7e9 | 0.3e9 | Msun | 2 | an H$_2$ mass of (1.7$\pm$0.3)$\times10^9$ M$_{\odot}$ |
| CO line width (FWHM) | ~490 | not stated | km/s | 3 | with an integrated line width of $\approx$490 km s$^{-1}$ (FWHM) |
| Continuum flux | 12.9 | 0.02 | Jy | 1 | Bright point source continuum emission with a flux of 12.9$\pm$0.02 Jy was detected |
| R_ENLR | 12.1 | 0.2 | kpc | 0 | we determine a characteristic ENLR size of $R_\mathrm{ENLR}=12.1\pm0.2$ kpc |
| R_KDR | 6.1 | 1.5 | kpc | 0 | we measure $R_\mathrm{KDR}=6.1\pm1.5$ kpc, adopting $W_{80}>600\,\mathrm{km\,s}^{-1}$ |

## Qualitative findings

- Molecular gas forms an arc ~1.8" SW of nucleus, perpendicular to jet, kinematically quiescent (dispersion <=45 km/s, gradient ±160 km/s)  
  > "appears as an “arc”-like feature about $\sim1.8\ensuremath{''}$ away from the nucleus towards the south-west almost exactly perpendicular to the jet axis" (2.2 ALMA observations)

## Claim tuples

- H: Does the ENLR size-luminosity relation show a break at ~6-10 kpc? | E: MUSE ENLR size at fixed surface brightness limit after AGN deblending | R: R_ENLR=12.1±0.2 kpc, 2.7 sigma above proposed break | F: No break or a much larger break radius | **supported**
- H: Is the disturbed gas radiatively driven radially? | E: Compare ionized gas velocity field with jet orientation | R: Receding gas on the approaching jet side | F: Jet-driven cocoon acting on inclined disk is favored | **partially**

## Reasoning

- Why this data: _not stated_
- Why this method: _not stated_
- Alternative: Molecular gas may be bound to a stellar over-density from a recent merger rather than a density wave  
  > "it is unclear whether the molecular gas is bound to a stellar over-density formed in a recent galaxy interaction or is currently forming in-situ" (2.2 ALMA observations)
- How they decided it was enough: _not stated_
- Limitation (authors): No outflow energetics computed since densities and cloud velocities cannot be measured  
  > "we refrain from computing gas outflow energetics to distinguish between a mechanically or radiatively-driven outflow" (3.2)
- Caveat (inferred, ours): ALMA data are a minor, low-resolution part; CO arc interpretation is speculative
- Caveat (inferred, ours): alpha_CO uncertain by factor 5.5
- Caveat (inferred, ours): Inclination estimate relies on scaling-relation stellar mass

## Reproducibility

- Data public (paper): archival ALMA data  
  > "CO(1-0) mapping with archival ALMA observations" (2.2 ALMA observations)
- Products in archive: _not stated_
- Missing: CASA version
- Missing: exact tracks and EBs
- Missing: line-free channels
- Missing: MUSE data reduction details beyond ESO pipeline
- Data volume (inferred): ~50-100 GB for 8 ALMA tracks (raw); MUSE cube separate
- Score (inferred): 3/5, ALMA part is described but key parameters are missing; main results are MUSE-based.
- Rediscovery candidate: no, Main numeric results derive from MUSE data; ALMA recipe incomplete.

## Links

- Method: (cite: Husemann:2013a; Husemann:2014) (QDEBLEND3D AGN-host deblending)
- Related: WISSH
- Related: KASHz
- Related: SUPER

## Checks

```json
{
 "quotes": 50,
 "quotes_ok": 50,
 "quote_pass_rate": 1.0,
 "quotes_too_long": 0,
 "unsupported_facts": 0,
 "project_codes": 5,
 "codes_not_in_text": [],
 "codes_not_in_obscore": [],
 "obscore_codes_not_in_card": [],
 "codes_printed_but_missing": [],
 "numeric_results": 6,
 "numeric_problems": 0,
 "fill": {
  "facts": 64,
  "stated": 33,
  "rate": 0.516
 },
 "evidence_ok": true
}
```
