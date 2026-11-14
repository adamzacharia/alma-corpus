# Carbon Monoxide in the Cold Debris of Supernova 1987A

`2013ApJ...773L..34K` | The Astrophysical Journal Letters 2013 | first author: Kamenetzky, J. | arXiv: 1307.6561 | DOI: 10.1088/2041-8205/773/2/L34

Card schema 1.0 | model claude-sonnet-5-5 | depth full | type multi_facility_alma_minor

## Science

- Fields: star_formation, astrochemistry, stellar_physics
- Question: Is cold molecular gas (rotational CO and SiO) present in the ejecta of SN1987A, and what mass, temperature and filling factor does it have?  
  > "These observations, along with a partial observation of SiO, confirm the presence of cold molecular gas within supernova remnants" (abstract)
- Target **SN 1987A**: coordinates _not stated_; z/distance 50 kpc  
  > "Luminosities are calculated using a distance of 50 kpc throughout this work (cite: Panagia1999)." (Table 2); distance from Panagia 1999  
  > "Luminosities are calculated using a distance of 50 kpc throughout this work (cite: Panagia1999)." (Table 2)

## Data provenance

- ALMA projects: 2011.0.00273.S
- bands: Band 3 (2.6 mm) and Band 6 (1.3 mm)  
  > "SN 1987A was observed with ALMA at wavelengths of 2.6 mm (Band 3) and 1.3 mm (Band 6) between April and August 2012." (2.1 ALMA)
- frequencies and spectral setup: FDM, 488 kHz channels averaged to 50 km/s; 1.875 GHz per spectral window  
  > "Both bands were observed using Frequency Division Mode (FDM), i.e. 488 kHz channels" (2.1 ALMA); "The bandwidth per spectral window was 1.875 GHz." (2.1 ALMA)
- continuum bandwidth: _not stated_
- arrays: _not stated_
- configurations: _not stated_
- baselines: _not stated_
- angular resolution: ~1.6x1.5" (Band 3), 0.6x0.5" (Band 6)  
  > "could already obtain synthesized beam spatial resolutions of $\sim$ 1.6 $\times$ 1.5$''$ and 0.6 $\times$ 0.5$''$, respectively" (2.1 ALMA)
- max recoverable scale: _not stated_
- sensitivity: RMS 0.09-0.20 mJy/beam per 100 km/s  
  > "RMS (root mean square) noise is measured over a width of 100 km s$^{-1}$" (Table 1)
- time on source: 12-25 min per execution block  
  > "A002/X45f1dd/Xd13 | 6 | 15 Jul | 16/19 | 1.3 | 12 | 0.14 | 213 | 402" (Table 1)
- observing dates: April-August 2012 (5 execution blocks)  
  > "A002/X494155/X8be | 6 | 10 Aug | 22/23 | 1.4 | 25 | 0.09 | 194 | 402" (Table 1)
- pi or archival as stated: _not stated_
- Line: 12CO J=1-0 (115.3 GHz)
- Line: 12CO J=2-1 (230.6 GHz)
- Line: 28SiO J=5-4 (217.11 GHz)
- Other facility **APEX (SHeFI)**: 12CO J=3-2 upper limit of 94 mJy  
  > "obtained an upper limit on the $^{12}$CO J=3-2 line of 94 mJy" (2.2 APEX)
- Other facility **Herschel SPIRE FTS**: CO J=6-5 and 7-6 detections; upper limits for J=4-13  
  > "We detected two lines, J=7-6 and J=6-5" (2.3 SPIRE)
- External data: Far-IR luminosity of debris 8.45e35 erg/s  
  > "the far-IR luminosity of the debris of SN1987A was measured to be 8.45 $\times 10^{35}$ erg s$^{-1}$" (Discussion and Conclusions) [from Matsuura2011]
- External data: C/O clump mass 0.58 Msun and filling factor 0.02 at t=8 yr  
  > "the carbon/oxygen clumps have a mass of carbon plus oxygen of 0.58 M$_{\odot}$ and a filling factor $f_{C/O} = 0.02$" (Discussion and Conclusions) [from Jerkstrand2011]

## Processing

### Calibration

- pipeline or manual: _not stated_
- casa version: _not stated_
- pipeline version: _not stated_
- archive products used as is: _not stated_
- flux calibrator: Callisto; quasar flux densities bootstrapped to X352 and X1c blocks  
  > "Callisto was observed as an absolute flux calibrator" (2.1 ALMA)
- flux scale uncertainty: 15% (CO 1-0), 10% (CO 2-1)  
  > "a 15% (10%) absolute flux calibration error for $^{12}$CO 1-0 (2-1)" (Table 2)
- self calibration: _not stated_

### Imaging

- task: _not stated_
- deconvolver: _not stated_
- weighting robust: robust = 0  
  > "the robust parameter was set to 0, midway between natural and uniform weighting" (2.1 ALMA)
- uv taper: _not stated_
- cell size: _not stated_
- image size: _not stated_
- masking: _not stated_
- multiscale scales: _not stated_
- continuum subtraction: _not stated_
- line free channels: _not stated_
- primary beam correction: _not stated_
- array combination: _not stated_
- smoothing: channels averaged to 50 km/s  
  > "later averaged to 50 km s$^{-1}$ spectral resolution" (2.1 ALMA)
- final beam: _not stated_
- final rms: _not stated_

### Not stated but needed to reproduce (our reading)

- CASA version and whether manual or pipeline calibration
- Imaging task, cell and image size, masking, deconvolution settings
- Continuum subtraction method and line-free channels
- Spectrum extraction region
- Line fitting procedure (Gaussian fits) details
- CO collision rates / LTE model code and parameter grids
- Flux bootstrapping details

## Analysis recipe

1. **Calibrate and image ALMA data**: Standard bandpass, gain calibration with Callisto flux scale, robust=0 imaging, averaged to 50 km/s  
  > "System temperature and precipitable water vapor (PWV) calibrations were applied before standard bandpass and complex gain (phase) calibration." (2.1 ALMA)
   - fitting: _not stated_
   - validation: _not stated_
2. **Fit CO line profiles**: Fit line profile of central spectrum to get FWHM, velocity, flux, luminosity  
  > "Uncertainties are one standard deviation." (Table 2)
   - parameter: 10% continuum subtraction error added in quadrature  
  > "we added in quadrature a 10% continuum subtraction error" (Table 2)
   - assumption: distance 50 kpc  
  > "Luminosities are calculated using a distance of 50 kpc throughout this work (cite: Panagia1999)." (Table 2)
   - fitting: _not stated_
   - validation: _not stated_
3. **Derive SPIRE upper limits**: Inject broadened artificial CO spectrum into SPIRE spectra with scaling 1-10; detection if flux within 30% of input  
  > "as judged by a line flux measurement that yielded a line flux within 30% of the input value" (2.3 SPIRE)
   - software: HIPE
   - fitting: _not stated_
   - validation: _not stated_
4. **Model CO mass, temperature and filling factor**: Sobolev escape probability LTE model of uniform clumps in freely expanding sphere; compare SLED to ALMA, APEX, SPIRE  
  > "We calculate the luminosities using the Sobolev escape probability approximation (cite: Castor1970)" (3 Interpretation)
   - parameter: R = 2000 km/s x 25 years  
  > "defined by radius $R = vt = 2000$ km s$^{-1} \times$ 25 years" (3 Interpretation)
   - assumption: LTE, excitation temperature equals kinetic temperature  
  > "we assume that the lines are in Local Thermodynamic Equilibrium (LTE) with their surroundings" (3 Interpretation)
   - fitting: _not stated_
   - validation: Critical densities compared to modeled clump density  
  > "The critical densities for the J=2-1 line are one to two orders of magnitude below the modeled density of the O/C clumps" (3 Interpretation)

## Software

- **CLASS** : APEX baseline subtraction  
  > "We subtracted the baseline after combining all the spectra using the CLASS software" (2.2 APEX)
- **HIPE** v11: SPIRE data reduction  
  > "reduced in HIPE v11" (2.3 SPIRE)

## Numeric results

| quantity | value | uncertainty | units | step | quote |
|---|---|---|---|---|---|
| CO 1-0 integrated flux | 11.6 | 1.2 | Jy km/s | 2 | 2270 $\pm$ 190 / 300 $\pm$ 100 / 4.8 $\pm$ 0.3 / 11.6 $\pm$ 1.2 / 1.33 $\pm$ 0.14 |
| CO 2-1 integrated flux | 46.0 | 1.9 | Jy km/s | 2 | 2150 $\pm$ 50 / 390 $\pm$ 20 / 20.0 $\pm$ 0.7 / 46.0 $\pm$ 1.9 / 10.5 $\pm$ 0.4 |
| L(2-1)/L(1-0) | 7.9 | 2.0 | dimensionless | 4 | the line luminosity ratio $L_{2-1}/L_{1-0} = 7.9 \pm 2.0$ |
| CO mass lower limit | 0.01 | 3 sigma lower limit | Msun | 4 | the minimum mass is 0.01 M$_{\odot}$ (3$\sigma$ lower limit) |
| T_CO x V_CO | 5.3e52 | not stated | cm^3 K | 4 | The product of $T_{CO}$ and $V_{CO}$ is $5.3 \times 10^{52}$ cm$^3$ K. |
| CO contribution to FIR luminosity | at most 8.4% | not stated | percent | 4 | with $^{12}$CO contributing at most 8.4% |

## Qualitative findings

- CO emission located within 1" of central debris, FWHM ~2200 km/s, from expanding ejecta  
  > "The line profiles are broad (FWHM $\sim 2200$ km s$^{-1}$, Table [2](#table:fit))" (2.1 ALMA)

## Claim tuples

- H: Cold rotational CO exists in SN1987A ejecta | E: ALMA Band 3 and 6 imaging spectroscopy | R: CO 1-0 and 2-1 detected, centrally located | F: Cold molecular gas confirmed in ejecta | **supported**
- H: Constrain CO mass, temperature and filling factor | E: LTE Sobolev model vs ALMA, APEX, SPIRE SLED | R: M>=0.01 Msun, T>14 K, f<0.35 | F: Lower limits only; lines optically thick | **partially**

## Reasoning

- Why this data: _not stated_
- Why this method: _not stated_
- Alternative: Dust remains the most viable explanation for the FIR excess rather than CO  
  > "emission from dust grains is still the most viable explanation for the excess FIR emission detected with *Herschel*" (Discussion and Conclusions)
- How they decided it was enough: _not stated_
- Limitation (authors): Collision rates unknown; LTE SLEDs for J>3-2 are upper limits; SPIRE limits cannot constrain model  
  > "This means that the current SPIRE upper limits cannot constrain the physical parameters of our model" (3 Interpretation)
- Caveat (inferred, ours): Single-zone uniform clump model; degenerate mass/temperature/filling factor
- Caveat (inferred, ours): Unresolved emission and continuum subtraction uncertain
- Caveat (inferred, ours): Early Science data with few antennas

## Reproducibility

- Data public (paper): _not stated_
- Products in archive: _not stated_
- Missing: CASA version and scripts
- Missing: Model code and grids
- Missing: Spectrum extraction aperture
- Data volume (inferred): Tens of GB for 5 Early Science execution blocks
- Score (inferred): 3/5, ALMA data are archival and calibration is described, but imaging details and the model code are missing.
- Rediscovery candidate: no, Imaging and fitting recipes are incomplete, and the modeling code is not provided.

## Links

- Companion: Matsuura2011 (Herschel dust mass and FIR luminosity of SN1987A)
- Companion: Jerkstrand2011 (Ejecta model with C/O clump properties)
- Related: MESS (Herschel)

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
 "numeric_results": 6,
 "numeric_problems": 0,
 "fill": {
  "facts": 68,
  "stated": 31,
  "rate": 0.456
 },
 "evidence_ok": true
}
```
