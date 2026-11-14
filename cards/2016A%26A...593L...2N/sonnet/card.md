# Planck's Dusty GEMS. II. Extended [CII] emission and absorption in the Garnet at z = 3.4 seen with ALMA

`2016A&A...593L...2N` | Astronomy and Astrophysics 2016 | first author: Nesvadba, N. | arXiv: 1610.01169 | DOI: 10.1051/0004-6361/201629037

Card schema 1.0 | model claude-sonnet-5-5 | depth full | type observational_alma_primary

## Science

- Fields: high_z_galaxies
- Question: What do spatially resolved ALMA [CII] observations of the lensed galaxy G045.1+61.1 reveal about the gas, including emission, absorption and possible winds?  
  > "Our ALMA data resolve the [CII] emission into two clouds at different velocities, around an intensely star-forming clump, against which [CII] is seen in absorption." (Introduction)
- Target **G045.1+61.1 (the Garnet)**: coordinates _not stated_; z/distance z=3.427 (systemic, from [CI])  
  > "The Garnet consists of four counter-images seen behind a small group of galaxies at a spectroscopic redshift of z$=$0.56" (Introduction); "The average magnification at the position of the bright star-forming clump is $\mu=10$" (Observed morphologies and spectrum); distance from [CI](1-0) detection with IRAM 30m EMIR  
  > "The Garnet consists of four counter-images seen behind a small group of galaxies at a spectroscopic redshift of z$=$0.56" (Introduction); "The average magnification at the position of the bright star-forming clump is $\mu=10$" (Observed morphologies and spectrum)

## Data provenance

- ALMA projects: 2013.1.01230.S
- bands: Band 8  
  > "obtained 27 min of band 8 data in the C34-3 configuration" (Observations and data reduction)
- frequencies and spectral setup: [CII] at 428.775 GHz in one spw, three more spws on line-free continuum; 15.6 MHz channels, 1.856 GHz per window  
  > "tuned to the [CII] line (428.775 GHz sky frequency) in one spectral window. Three more windows were placed on the line-free continuum." (Observations and data reduction)
- continuum bandwidth: _not stated_
- arrays: _not stated_
- configurations: C34-3, 37 antennae  
  > "ALMA observed our Cycle 2 project with 37 antennae on 6 June, 2015" (Observations and data reduction)
- baselines: _not stated_
- angular resolution: 0.41''x0.27'' PA=13.5 deg  
  > "The major and minor axis size of the beam is 0.41$''$$\times$0.27$''$ along PA$=$13.5$^\circ$" (Observations and data reduction)
- max recoverable scale: 3.9''  
  > "The largest angular scale is 3.9$''$" (Observations and data reduction)
- sensitivity: 1.3 mJy per 50 km/s channel; continuum 0.46 µJy  
  > "The rms is 1.3 mJy in each 50 km s$^{-1}$ channel" (Observations and data reduction)
- time on source: 27 min  
  > "obtained 27 min of band 8 data" (Observations and data reduction)
- observing dates: 6 June 2015  
  > "with 37 antennae on 6 June, 2015" (Observations and data reduction)
- pi or archival as stated: _not stated_
- Line: [CII] 158 µm (not stated)
- Other facility **IRAM 30m EMIR**: [CI](1-0) and CO(4-3) lines  
  > "which we observed during the same campaign with EMIR on the IRAM 30 m telescope with a 20$''$ beam" (Observations and data reduction)
- Other facility **SMA**: 850 µm imaging of all counter-images  
  > "which contributes 46 % of the total flux at 850 $\mu$m seen with the SMA" (Introduction)
- External data: CO(4-3) luminosity  
  > "the CO(4-3) luminosity of , and the [CI] 1-0 luminosity" (Astrophysical nature of [CII] in the Garnet) [from not stated (citation missing in text)]
- External data: PDR models  
  > "We used the PDR models of (cite: kaufman99) to derive the average gas properties" (Astrophysical nature of [CII] in the Garnet) [from (cite: kaufman99)]

## Processing

### Calibration

- pipeline or manual: standard manual ALMA scripts with CASA  
  > "We used the standard manual scripts for ALMA reduction with the Common Astronomy Software Application `CASA`" (Observations and data reduction)
- casa version: _not stated_
- pipeline version: _not stated_
- archive products used as is: _not stated_
- flux calibrator: _not stated_
- flux scale uncertainty: _not stated_
- self calibration: _not stated_

### Imaging

- task: CLEAN in CASA  
  > "and `CLEAN` to construct the synthesized beam-deconvolved images of the frequency data cubes" (Observations and data reduction)
- deconvolver: _not stated_
- weighting robust: _not stated_
- uv taper: _not stated_
- cell size: _not stated_
- image size: _not stated_
- masking: _not stated_
- multiscale scales: _not stated_
- continuum subtraction: continuum from line-free spws 1 and 2 subtracted per spaxel, with 2% dust brightening correction  
  > "subtracted this value from every spectral bin" (Observed morphologies and spectrum)
- line free channels: _not stated_
- primary beam correction: _not stated_
- array combination: _not stated_
- smoothing: rebinned to 50 km/s channels  
  > "The spectral channels were rebinned to a width of 50 km s$^{-1}$." (Observations and data reduction)
- final beam: _not stated_
- final rms: _not stated_

### Inherited from earlier work

- Lens image positions from earlier paper  
  > "from the positions of the four images seen in Fig. 2 of" (Observed morphologies and spectrum) [from Paper I (citation missing in text)]

### Not stated but needed to reproduce (our reading)

- CASA version
- robust/weighting, cell and image size, clean threshold and masks
- line-free channels and continuum spw frequencies
- flux calibrator and calibration uncertainty
- lens model parameters
- how the 2% correction and spectrum normalization were done
- absorption fit procedure

## Analysis recipe

1. **image cubes and subtract continuum**: CLEAN in CASA, rebin to 50 km/s, subtract line-free continuum  
  > "We used the line-free continuum image from spectral windows 1 and 2 to estimate the continuum flux density in each spaxel" (Observed morphologies and spectrum)
   - software: CASA
   - fitting: _not stated_
   - validation: absorption checked in dirty maps, different apertures, continuum spws, check source and phase calibrator  
  > "It is also apparent in the dirty maps." (Observed morphologies and spectrum)
2. **lens model and magnification**: Lenstool model from four image positions  
  > "We used `Lenstool` (cite: kneib96; jullo07) to construct a gravitational lens model" (Observed morphologies and spectrum)
   - software: Lenstool
   - assumption: all four are multiple images of the same region  
  > "assuming that all four are multiple images of the same region" (Observed morphologies and spectrum)
   - fitting: _not stated_
   - validation: _not stated_
3. **gas properties from PDR models and line ratios**: Kaufman99 PDR models with [CII]/[CI] and [CII]/CO ratios  
  > "we estimate that the gas in the Garnet is on average exposed to a radiation field $200$ times greater than in the solar neighborhood" (Astrophysical nature of [CII] in the Garnet)
   - parameter: CI and CO luminosities scaled by 0.46 for beam contamination  
  > "we corrected the [CI] 1-0 and CO(4-3) luminosities by a factor of 0.46" (Astrophysical nature of [CII] in the Garnet)
   - assumption: CO optically thick  
  > "we assumed that the gas probed by the CO line emission is optically thick" (Astrophysical nature of [CII] in the Garnet)
   - fitting: _not stated_
   - validation: _not stated_
4. **absorber column density and wind test**: Gerin15 optical-depth relation for N(C+), Heckman15 momentum criterion  
  > "we find $N(C^+)=8.2\times 10^{18}$ cm$^{-2}$" (Astrophysical nature of [CII] in the Garnet)
   - assumption: Galactic carbon abundance 1.4e-4; v_c=400 km/s  
  > "adopting the Galactic carbon abundance of $1.4\times 10^{-4}$" (Astrophysical nature of [CII] in the Garnet)
   - fitting: _not stated_
   - validation: _not stated_

## Software

- **CASA** : calibration and imaging  
  > "Common Astronomy Software Application `CASA`" (Observations and data reduction)
- **Lenstool** : lens model  
  > "We used `Lenstool` (cite: kneib96; jullo07)" (Observed morphologies and spectrum)

## Numeric results

| quantity | value | uncertainty | units | step | quote |
|---|---|---|---|---|---|
| Blue EELR [CII] flux | 52.4 | 0.6 | Jy km/s | 1 | Blue EELR / 52.4$\pm$0.6 / -467$\pm$15 / 202$\pm$20 |
| Absorption depth | -0.60 | 0.15 | dimensionless | 1 | The depth of the absorption trough was measured from the normalized spectrum to be $-0.60\pm 0.15$ |
| Star-formation intensity of clump | 220 | not stated | Msun/yr/kpc^2 | 0 | this implies an average star-formation intensity of 220 M$_{\odot}$ yr$^{-1}$ kpc$^{-2}$ |
| N(C+) of absorber | 8.2e18 | not stated | cm^-2 | 4 | we find $N(C^+)=8.2\times 10^{18}$ cm$^{-2}$ |
| [CII]/[CI] luminosity ratio | 72.5 | 13 | dimensionless | 3 | $L_{{\rm CII}}/L_{{\rm CI}}=72.5\pm$13 |

## Qualitative findings

- No strong evidence for an escaping wind; redshifted absorption implies inflow  
  > "we did not detect strong evidence for a wind that would regulate star formation" (Implications for high-z galaxies and conclusions)

## Claim tuples

- H: Is [CII] absorption present in a high-z galaxy and real? | E: Checked dirty maps, apertures, continuum spws, calibrators | R: Absorption at +350 km/s, depth -0.60±0.15 | F: Feature not spurious; infalling gas | **supported**
- H: Is the clump driving an escaping wind? | E: Heckman15 momentum criterion | R: Momentum input 1.9e36 dyn vs critical 2e36 dyn | F: Wind unlikely to escape | **supported**

## Reasoning

- Why this data: _not stated_
- Why this method: _not stated_
- Alternative: Wind explanation disfavoured relative to overlapping clouds or merger  
  > "alternative explanations, such as overlapping gas clouds in a star-forming region or merger, are more realistic" (Astrophysical nature of [CII] in the Garnet)
- How they decided it was enough: _not stated_
- Limitation (authors): Lens model preliminary, awaiting HST imaging  
  > "We will present a more detailed analysis of the lensing configuration when our scheduled Hubble Space Telescope imaging has been taken" (Observed morphologies and spectrum)
- Caveat (inferred, ours): Single short observation; absorption significance modest
- Caveat (inferred, ours): Magnification uncertainties not propagated
- Caveat (inferred, ours): Many derived quantities lack uncertainties

## Reproducibility

- Data public (paper): _not stated_
- Products in archive: _not stated_
- Missing: Calibration and imaging parameters
- Missing: Lens model
- Missing: Companion paper data (CO(4-3), SED)
- Data volume (inferred): ~10-30 GB
- Score (inferred): 3/5, Data public in principle but imaging parameters and lens model are not given.
- Rediscovery candidate: no, Imaging recipe incomplete and lens model unstated.

## Links

- Method: (cite: kaufman99) (PDR models)
- Method: (cite: gerin15) (absorption column density method)
- Method: (cite: heckman15) (wind momentum criterion)
- Companion: (cite: canameras15) (ground-based observations of the Garnet)
- Companion: (cite: planck15a) (Planck discovery)
- Related: Planck's Dusty GEMS

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
  "facts": 69,
  "stated": 34,
  "rate": 0.493
 },
 "evidence_ok": true
}
```
