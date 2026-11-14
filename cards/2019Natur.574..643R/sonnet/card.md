# A 100-kiloparsec wind feeding the circumgalactic medium of a massive compact galaxy

`2019Natur.574..643R` | Nature 2019 | first author: Rupke, David S. N. | arXiv: 1910.13507 | DOI: 10.1038/s41586-019-1686-1

Card schema 1.0 | model claude-sonnet-5-5 | depth light | type multi_facility_alma_minor

## Science

- Fields: nearby_galaxies, high_z_galaxies
- Question: How far does the multiphase galactic wind of the compact massive merger Makani extend, and does it feed the circumgalactic medium?  
  > "Winds from compact starbursts have been observed to flow to distances somewhat greater than ten kiloparsecs" (abstract)
- Target **Makani (SDSS J211824.06+001729.4)**: coordinates _not stated_; z/distance z = 0.459  
  > "At redshift z = 0.459, Makani is a compact but massive galaxy" (Main text); distance from _not stated_

## Data provenance

- ALMA projects: 2016.1.01072.S, 2017.1.01318.S
- bands: Band 4, representative frequency 158.01 GHz  
  > "We used the Band 4 receivers with a representative frequency of 158.01 GHz to detect CO(2–1) at the redshift of the target." (Methods)
- frequencies and spectral setup: _not stated_
- continuum bandwidth: _not stated_
- arrays: 12-m array  
  > "Makani was observed by the ALMA 12-m array" (Methods)
- configurations: _not stated_
- baselines: C40-1 (15–287 m), C43-3 (15–500 m), C43-6 (15–2517 m)  
  > "lines 15–500 m) and C43–6 (baselines 15–2517 m) respectively." (Methods, ALMA observations)
- angular resolution: natural 0.39"x0.31"; tapered 1.15"x1.08"; restored 0.6"  
  > "0.39″ × 0.31″ (position angle PA = −73◦ east of north) and 1.15″ × 1.08″ (PA = −79◦) respectively." (Methods)
- max recoverable scale: _not stated_
- sensitivity: rms per 30 km/s channel: 0.13 (natural), 0.20 (tapered), 0.15 (restored) mJy/beam  
  > "is 0.13 mJy beam−1, 0.20 mJy beam−1 and 0.15 mJy beam−1 respectively." (Methods)
- time on source: 212 min  
  > "The total integration time on source was 212 min." (Methods)
- observing dates: 11 March 2017, 10 April 2018, 15 December 2017  
  > "on 11 March 2017, 10 April 2018 and 15 December 2017" (Methods)
- pi or archival as stated: _not stated_
- Line: CO J=2-1 (not stated)
- Other facility **Keck/KCWI**: Optical IFU observations of [O II], Mg II nebula  
  > "we observed Makani with the Keck Cosmic Web Imager (KCWI)" (Main text)
- Other facility **HST WFC3**: Stellar morphology imaging  
  > "The Hubble Space Telescope observations described here were obtained from the Hubble Legacy Archive" (Data Availability)
- Other facility **SDSS, MMT, Keck/NIRSPEC**: Ancillary spectra for line ratios and stellar populations  
  > "The second is a spectrum acquired with Keck/NIRSPEC" (Methods)
- External data: HST morphology, Sersic fit (Re = 2.24 kpc, n=4) and X-ray luminosity  
  > "A S´ersic fit to the Hubble Space Telescope image of Makani yields an effec" (Methods, Size measurements) [from Sell et al. 2014 (ref 14)]

## Processing

### Calibration

- pipeline or manual: ALMA pipeline-calibrated quality-checked products  
  > "We use the quality-checked ALMA pipeline-calibrated products, concatenating the observations into a single measurement set." (Methods)
- casa version: _not stated_
- pipeline version: _not stated_
- archive products used as is: yes, pipeline-calibrated products concatenated  
  > "We use the quality-checked ALMA pipeline-calibrated products" (Methods)
- flux calibrator: Neptune among calibrators (J2148+0657, J2134-0153)  
  > "included the sources J2148+0657, J2134-0153 and Neptune." (Methods)
- flux scale uncertainty: _not stated_
- self calibration: _not stated_

### Imaging

- task: CASA clean, CASA 5.1.0-74  
  > "We image the data using CASA (version 5.1.0-74)" (Methods)
- deconvolver: _not stated_
- weighting robust: naturally weighted  
  > "producing three versions of the data cube: naturally weighted, 1″ tapered and 0.6″ restored." (Methods)
- uv taper: 1 arcsec taper  
  > "naturally weighted, 1″ tapered and 0.6″ restored" (Methods)
- cell size: _not stated_
- image size: _not stated_
- masking: clean threshold 3 sigma from dirty-cube rms  
  > "we set a cleaning threshold of 3σ" (Methods)
- multiscale scales: 0, 0.4, 0.8, 1.6 arcsec  
  > "We use multi-scale cleaning with scales of 0″, 0.4″, 0.8″ and 1.6″." (Methods)
- continuum subtraction: continuum image averaged 143.5–146.5 GHz subtracted from CO channels  
  > "By collapsing the cube over this frequency range we construct a continuum image that is subtracted from the channels spanning the CO(2–1) line." (Methods)
- line free channels: _not stated_
- primary beam correction: _not stated_
- array combination: _not stated_
- smoothing: restored with circular 0.6" Gaussian beam to match KCWI seeing  
  > "uses a circular Gaussian restoring beam with a full-width at half-maximum (FWHM) of 0.6″ to match the seeing of the KCWI data" (Methods)
- final beam: _not stated_
- final rms: _not stated_

### Inherited from earlier work

- CO-to-H2 conversion alpha = 0.34 Msun/(K km/s pc2)  
  > "previous works [7], we adopt _α_ = 0 _._ 34 _M_ _⊙_ (K km s _[−]_ [1] pc [2] ) _[−]_ [1], lower than both the standard Galactic" (Methods, ALMA observations) [from Geach et al. 2014 (ref 7)]

### Not stated but needed to reproduce (our reading)

- cell size and image size
- robust/taper uv-range details
- CO rest frequency used
- number of channels/line-free channel ranges beyond continuum window
- exact flux mask definition for aperture integration
- uncertainty derivation for CO masses

## Analysis recipe

1. **Image CO(2-1) cubes**: CASA clean of concatenated pipeline-calibrated data into natural, 1" tapered and 0.6" restored cubes at 30 km/s  
  > "We produce data cubes with a spectral resolution of 30 km s−1 (16 MHz)" (Methods)
   - software: CASA
   - parameter: 3 sigma threshold, multiscale 0,0.4,0.8,1.6 arcsec  
  > "We use multi-scale cleaning with scales of 0″, 0.4″, 0.8″ and 1.6″." (Methods)
   - fitting: _not stated_
   - validation: _not stated_
2. **Subtract continuum and integrate CO line flux**: Average tapered cube over ±1500 km/s, 3 sigma mask, integrate spectrum; second mask excluding >15 sigma core/tidal arm for extended CO  
  > "define a 3σ mask for the source extent, based on the noise in the channel-averaged map." (Methods)
   - software: CASA
   - fitting: _not stated_
   - validation: _not stated_
3. **Derive line luminosity and molecular gas mass and outflow rate**: L' = 3.25e7 DL^2 (1+z)^-1 nu_rest^-2 S dV; M_H2 = alpha L'; dM/dt ≈ Mv/r  
  > "CO line luminosities are converted to estimates of the molecular gas mas through MH2 = αL′." (Methods)
   - assumption: alpha = 0.34 Msun (K km/s pc2)^-1, conservative, optically thin outflow  
  > "lower than both the standard Galactic and ULIRG conversionsbecause high-velocity extended and/or CO emission might be optically thin" (Methods)
   - fitting: _not stated_
   - validation: _not stated_

## Software

- **CASA** 5.1.0-74: imaging ALMA data  
  > "We image the data using CASA (version 5.1.0-74)" (Methods)
- **IFSRED** : KCWI data reduction  
  > "We reduced the data using the KCWI data reduction pipeline and the IFSRED library" (Methods)
- **IFSFIT** : spectral fitting of KCWI cubes  
  > "We fit the core spectrum, the full data cube, and the Voronoi binned data cube with IFSFIT" (Methods)
- **Prospector** : stellar mass SED fitting  
  > "using the Bayesian stellar population synthesis modeling code Prospector" (Methods)
- **pPXF** : stellar continuum fitting  
  > "We perform the fit with the Penalized Pixel-Fitting (pPXF) code" (Methods)

## Numeric results

| quantity | value | uncertainty | units | step | quote |
|---|---|---|---|---|---|
| 2 mm continuum flux (143.5–146.5 GHz) | 26 | ±10 | mJy | 2 | averaged over 143.5–146.5 GHz, with a total S2mm = 26(±10) mJy. |
| Molecular gas mass in |v|=500–1500 km/s flow | 2.4e9 | +0.6/-0.6 | Msun | 3 | the mass of the molecular gas in the /v/ = 500–1500 km s−1 flow (that is, episode II) is substantial |
| Molecular episode II mass flow rate | 245 | not stated | Msun/yr | 3 | dM/dt ≈ Mv/r = 245M⊙ yr−1 for v = 1,000 km s−1 and r = 10 kpc |

## Qualitative findings

- [O II] nebula spans ~100x80 kpc; molecular outflow compact within ~10 kpc with high velocities; low-velocity CO extends to <20 kpc  
  > "both blueshifted at -500 to -1,500 km s−1 and redshifted at 500–1,500 km s−1, from the nucleus 10 kpc northward" (Main text)

## Claim tuples

- H: Galactic winds from compact starbursts can reach CGM scales (>100 kpc) | E: KCWI [O II] IFU mapping plus ALMA CO(2-1) and Mg II | R: Ionized nebula extends to 50 kpc N-S/40 kpc E-W; CO outflow within 10 kpc at ±500–1500 km/s | F: Multi-phase two-episode wind is depositing metals into the CGM | **supported**

## Reasoning

- Why this data: _not stated_
- Why this method: Tapered image to maximise sensitivity to extended weak CO  
  > "We produce a tapered image in order to maximise sensitivity to potentially extended but weak CO emission around the target." (Methods)
- How they decided it was enough: _not stated_
- Limitation (authors): Ionized gas mass has unquantified systematics (density, ionization state); nebula may be larger than KCWI FOV  
  > "with unquantified systematic errors (electron density ne and ionization state) likely exceeding the measurement error" (Main text)
- Caveat (inferred, ours): Low alpha=0.34 is a strong assumption for mass and outflow rate
- Caveat (inferred, ours): Outflow rate uses crude Mv/r
- Caveat (inferred, ours): Low-velocity CO attribution to outflow is inferential
- Caveat (inferred, ours): AGN contribution not excluded

## Reproducibility

- Data public (paper): ALMA data in ALMA Science Archive  
  > "which are available at the ALMA Science Archive" (Data Availability)
- Products in archive: _not stated_
- Missing: cell/image size, robust, channel selection
- Missing: flux mask files
- Missing: uncertainty method
- Data volume (inferred): ~50-100 GB
- Score (inferred): 5/5, ALMA part is described moderately; some imaging parameters missing; ALMA is secondary to KCWI.
- Rediscovery candidate: no, Main results rely heavily on KCWI data not public; ALMA recipe incomplete.

## Links

- Companion: Diamond-Stanic et al. 2012; Sell et al. 2014 (Earlier study of sample and morphology)

## Checks

```json
{
 "quotes": 47,
 "quotes_ok": 47,
 "quote_pass_rate": 1.0,
 "quotes_too_long": 0,
 "unsupported_facts": 0,
 "project_codes": 2,
 "codes_not_in_text": [],
 "codes_not_in_obscore": [],
 "obscore_codes_not_in_card": [],
 "codes_printed_but_missing": [],
 "numeric_results": 3,
 "numeric_problems": 0,
 "fill": {
  "facts": 66,
  "stated": 38,
  "rate": 0.576
 },
 "evidence_ok": true
}
```
