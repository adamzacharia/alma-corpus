# ALMA [C II] 158 μm Detection of a Redshift 7 Lensed Galaxy behind RXJ1347.1-1145

`2017ApJ...836L...2B` | The Astrophysical Journal Letters 2017 | first author: Bradač, Maruša | arXiv: 1610.02099 | DOI: 10.3847/2041-8213/836/1/L2

Card schema 1.0 | model claude-sonnet-5-5 | depth full | type observational_alma_primary

## Science

- Fields: high_z_galaxies
- Question: Is [C II] 158 um detected in a lensed, intrinsically faint z~7 Lyman-alpha emitter, and how do its luminosity and Lya-[C II] velocity offset compare with other z~7 and local galaxies?  
  > "We report the detection of [C II] 158$~\mu\mbox{m}$ line fully consistent with the Lyman-$\alpha$ redshift and with the peak of the optical emission." (abstract)
- Target **RXJ1347:1216**: coordinates RA 13:47:36.214, Dec -11:45:15.20 (ALMA)  
  > "R.A. | 13:47:36.214" (Table 1); "Lyman-$\alpha$ emission at $z_{\rm Ly\alpha}=6.7659 ^{+0.0030}_{-0.0005}$" (Introduction); z/distance z_Lya = 6.7659 (+0.0030/-0.0005); z_[CII] = 6.7655 +/- 0.0005  
  > "R.A. | 13:47:36.214" (Table 1); "Lyman-$\alpha$ emission at $z_{\rm Ly\alpha}=6.7659 ^{+0.0030}_{-0.0005}$" (Introduction); distance from Keck DEIMOS Lya (Huang et al.) and ALMA [C II]  
  > "R.A. | 13:47:36.214" (Table 1); "Lyman-$\alpha$ emission at $z_{\rm Ly\alpha}=6.7659 ^{+0.0030}_{-0.0005}$" (Introduction)

## Data provenance

- ALMA projects: 2015.1.00091.S
- bands: Band 6  
  > "We observed RXJ1347:1216 with ALMA on July 21 2016 in Band 6 with 38 12-m antennae on a configuration of 15-700m baselines." (2 Observations and data reduction)
- frequencies and spectral setup: SPW0 FDM centred at 244.85 GHz sky frequency (USB), 9.5 km/s resolution after averaging by 16; three TDM continuum SPWs (31.25 MHz resolution)  
  > "SPW0 was set to Frequency Division Mode and its center tuned to the [C II] 158$~\mu\mbox{m}$ rest-frame frequency" (2 Observations and data reduction); "The other three spectral windows were used for continuum in Time Division Mode ($31.25\mbox{MHz}$ spectral resolution) at lower frequencies." (2 Observations and data reduction)
- continuum bandwidth: _not stated_
- arrays: _not stated_
- configurations: _not stated_
- baselines: 15-700 m  
  > "38 12-m antennae on a configuration of 15-700m baselines" (2 Observations and data reduction)
- angular resolution: 0.58'' x 0.41'' at PA 288 deg  
  > "The FWHM beam size of the final image is $0.58\ensuremath{''} \times 0.41\ensuremath{''}$ at a position angle of $288\deg$." (2 Observations and data reduction)
- max recoverable scale: _not stated_
- sensitivity: line 250 uJy/beam per 30 km/s channel; continuum <15 uJy (1 sigma)  
  > "$\sigma_{\rm line} = 250\mu \mbox{Jy beam}^{-1}$ at $244.7424
\mbox{GHz}$ over a channel width of 30${\rm \:km\:s}^{-1}$" (2 Observations and data reduction)
- time on source: 74 minutes  
  > "The total time on-source was 74 minutes" (2 Observations and data reduction)
- observing dates: July 21 2016  
  > "We observed RXJ1347:1216 with ALMA on July 21 2016 in Band 6" (2 Observations and data reduction)
- pi or archival as stated: _not stated_
- Line: [C II] 158 um (1900.54 GHz)
- Other facility **HST**: Photometry, astrometry, GLASS grism, magnification model context  
  > "We have spectroscopically confirmed its redshift using Keck DEIMOS data (cite: huang15a) and *HST* grism data from GLASS (cite: treu15; schmidt16)." (Introduction)
- Other facility **Spitzer**: Deep SURFSUP photometry for stellar properties  
  > "we also measured its integrated stellar properties using deep *Spitzer* SURFSUP data" (Introduction)
- Other facility **Keck DEIMOS**: Lyman-alpha spectroscopy and redshift  
  > "spectroscopy of Lyman-$\alpha$ from Keck DEMOS from (cite: huang15a)" (Table 1)
- External data: HST and Spitzer photometry and SED fitting results  
  > "Stellar population modeling results for RXJ 1347:1216 using HST and Spitzer photometry from (cite: huang15a)" (Table 1) [from (cite: huang15a)]
- External data: Characteristic M_UV* at z~7 = -20.87 +/- 0.26  
  > "assuming characteristic magnitude at $z\sim 7$ of $M_{UV}^*=-20.87\pm 0.26$ from (cite: bouwens15)" (Introduction) [from (cite: bouwens15)]
- Simulation/model as data: Lensing magnification model giving mu = 5.0 +/- 0.3 (details not given)  
  > "Our magnification model shows that the massive foreground galaxy cluster RX J1347.1$-$1145 magnifies RXJ1347:1216 by a factor $5.0\pm 0.3$." (Introduction)
- Simulation/model as data: Vallini et al. 2015 simulations compared in L_[CII]-SFR plot  
  > "We include results from simulations by (cite: vallini15) as well as results for $z>5$ galaxies from the literature." (Results)

## Processing

### Calibration

- pipeline or manual: Standard procedures in CASA  
  > "The data reduction followed the standard procedures in the Common Astronomy Software Applications (CASA) package." (2 Observations and data reduction)
- casa version: _not stated_
- pipeline version: _not stated_
- archive products used as is: _not stated_
- flux calibrator: J1337-1257 (bandpass and absolute flux); phase calibrator J1354-1041  
  > "We used J1337$-$1257 for bandpass and absolute flux scale calibrators and J1354$-$1041 for a phase calibrator." (2 Observations and data reduction)
- flux scale uncertainty: ~5%  
  > "Flux calibration errors ($\sim 5\%$) are included in all measurements." (2 Observations and data reduction)
- self calibration: _not stated_

### Imaging

- task: _not stated_
- deconvolver: _not stated_
- weighting robust: Briggs, robust = 0.5  
  > "The data cube was cleaned using Briggs weighting and ROBUST $=$ 0.5." (2 Observations and data reduction)
- uv taper: _not stated_
- cell size: _not stated_
- image size: _not stated_
- masking: _not stated_
- multiscale scales: _not stated_
- continuum subtraction: Continuum image from all line-free channels of the four SPWs  
  > "The continuum image was extracted using all the line-free channels of the four spectral windows" (2 Observations and data reduction)
- line free channels: _not stated_
- primary beam correction: _not stated_
- array combination: _not stated_
- smoothing: _not stated_
- final beam: 0.58'' x 0.41'', PA 288 deg  
  > "The FWHM beam size of the final image is $0.58\ensuremath{''} \times 0.41\ensuremath{''}$ at a position angle of $288\deg$." (2 Observations and data reduction)
- final rms: 250 uJy/beam per 30 km/s channel; continuum <15 uJy  
  > "resulting in a continuum sensitivity of $<15\mu
\mbox{Jy}$ ($1\sigma$)" (2 Observations and data reduction)

### Inherited from earlier work

- UV slope measurement and SED fitting details  
  > "(see (cite: huang15a) for details)" (Results) [from (cite: huang15a)]
- Dynamical mass estimator approach  
  > "Following (cite: pentericci16) and (cite: wang13), we can also estimate the dynamical mass within the [C II]-emitting region of the galaxy." (Results) [from (cite: pentericci16); (cite: wang13)]

### Not stated but needed to reproduce (our reading)

- CASA version
- Number of channels/clean threshold and masks, cell and image size
- Line-free channel ranges and how continuum was subtracted
- Spectrum extraction aperture
- Conversion of line flux to L_[CII] and lensing-model details
- FIR luminosity to SFR conversion calibration
- Lya redshift remeasurement procedure

## Analysis recipe

1. **Image the [C II] cube and continuum**: CASA cleaning with Briggs weighting; continuum from line-free channels  
  > "The data cube was cleaned using Briggs weighting and ROBUST $=$ 0.5." (2 Observations and data reduction)
   - software: CASA
   - parameter: robust = 0.5; 30 km/s channels  
  > "over a channel width of 30${\rm \:km\:s}^{-1}$ ($24.5\mbox{MHz}$)" (2 Observations and data reduction)
   - fitting: _not stated_
   - validation: _not stated_
2. **Measure line properties**: Extract spectrum at native resolution and fit a Gaussian  
  > "We fit the line using a Gaussian and estimate peak flux of $S_{\rm line,g} = 0.82\pm 0.26 \mbox{mJy}$" (Results)
   - parameter: native channel width 9.6 km/s  
  > "We extract the spectrum using native spectral resolution with channel width of $9.6~{\rm \:km\:s}^{-1}$" (Results)
   - fitting: Gaussian line profile  
  > "The integrated values do not critically depend upon the assumption of a Gaussian profile within the uncertainties." (Results)
   - validation: Integrated values checked to be insensitive to Gaussian assumption  
  > "The integrated values do not critically depend upon the assumption of a Gaussian profile within the uncertainties." (Results)
3. **Derive FIR-based SFR limit and compare with SED**: Continuum upper limit converted to SFR_FIR; SED refit with SMC dust curve and constant SFH  
  > "we derive $\rm{SFR}_{\rm{FIR}}<3~M_{\odot}~\rm{yr}^{-1}$ (assuming spectral index $\beta = 1.5$ and conservatively a dust temperature of $45~\mbox{K}$)" (Results)
   - assumption: beta = 1.5, T_dust = 45 K  
  > "assuming spectral index $\beta = 1.5$ and conservatively a dust temperature of $45~\mbox{K}$" (Results)
   - fitting: BC03 0.2 Zsun templates; SMC (Pei92) attenuation refit  
  > "Re-fitting the SED assuming a constant star formation history and a steeper SMC dust attenuation curve (cite: pei92)" (Results)
   - validation: _not stated_
4. **Estimate dynamical and gas mass**: M_dyn = 1.16e5 V_cir^2 D with V_cir = 0.75 FWHM/sin(i); i from axis ratio; Kennicutt-Schmidt gas mass  
  > "We use $M_{\rm dyn} =
 1.16\times10^5V^2_{\rm cir}D$" (Results)
   - parameter: disk diameter ~0.6''; b/a = 0.6  
  > "With $b/a=0.6$ measured from the [C II] emission, we get $i=50^{\circ}$" (Results)
   - assumption: Axisymmetric thin disk; dark matter negligible  
  > "For an intrinsically axisymmetric, infinitesimally thin disk, inclination is related to ellipticity via $\cos i = b/a$" (Results)
   - fitting: _not stated_
   - validation: Authors note approximation is very uncertain  
  > "Note that this approximation is very uncertain, as $z\sim 7$ galaxies might not have ordered motion." (Results)

## Software

- **CASA** : Data reduction and imaging  
  > "The data reduction followed the standard procedures in the Common Astronomy Software Applications (CASA) package." (2 Observations and data reduction)
- **SExtractor** : MAG_AUTO F160W magnitude  
  > "Lensed total magnitude (`MAG_AUTO` as defined by SExtractor (cite: sextractor)) in F160W." (Table 1)

## Numeric results

| quantity | value | uncertainty | units | step | quote |
|---|---|---|---|---|---|
| [C II] peak line flux (30 km/s) | 1.25 | 0.25 | mJy/beam | 2 | peak line flux $S_{\rm line} = 1.25\pm 0.25 \mbox{mJy}$ using $30{\rm \:km\:s}^{-1}$ resolution |
| z_[CII] | 6.7655 | 0.0005 | dimensionless | 2 | measure [C II] redshift of $z_{\rm [C \sc{II}]} = 6.7655\pm 0.0005$ |
| Gaussian FWHM | 75 | 25 | km/s | 2 | FWHM of $75 \pm 25~{\rm \:km\:s}^{-1}$ |
| Integrated line flux | 67 | 12 | mJy km/s | 2 | the integrated line flux of $S_{\rm
  line}\Delta v = 67\pm 12\mbox{mJy kms}^{-1}$ |
| L_[CII] (intrinsic) | 1.5e7 | +0.2/-0.4 | Lsun | 2 | $L_{\rm [C \sc{II}]} = 1.5^{+0.2}_{-0.4} \times 10^7L_{\odot}$ |
| Lya-[CII] velocity offset | 20 | +140/-40 | km/s | 0 | $\Delta v =
 20_{-40}^{+140}{\rm \:km\:s}^{-1}$ (68% confidence |
| SFR_FIR upper limit | <3 | not stated | Msun/yr | 3 | we derive $\rm{SFR}_{\rm{FIR}}<3~M_{\odot}~\rm{yr}^{-1}$ |
| M_dyn | 2.0e9 | 0.9e9 | Msun | 4 | $M_{\rm{dyn}}=(2.0\pm0.9)\times10^9\,M_\odot$ |
| Stellar mass | 8.0e7 | +6.5/-0.9 | Msun | 3 | $M_{\text{stellar}} =
 8.0^{+6.5}_{-0.9} \times 10^7~M_\odot$ |

## Qualitative findings

- ALMA [C II] position agrees with HST UV counterpart within astrometric uncertainty (offset 0.1'')  
  > "The [C II] line is spatially consistent (measured offset is $0.1\ensuremath{''}$) with the rest-frame UV emission" (Results)

## Claim tuples

- H: Is [C II] detectable in a sub-L* lensed z~7 LAE? | E: ALMA Band 6 observation of RXJ1347:1216 | R: 5 sigma detection, L_[CII]~1.5e7 Lsun, ~5x fainter than other z~7 detections | F: [C II] detected at the Lya redshift and UV position | **supported**
- H: Is [C II] weak relative to SFR at z~7 compared to local galaxies? | E: Compare L_[CII] and SFR with local relation and simulations | R: Low L_[CII] given SFR | F: Consistent with low metallicity <~0.2 Zsun, with possible feedback | **partially**
- H: Does Lya show a large velocity offset from systemic? | E: Compare Lya (Keck) and [C II] redshifts | R: Delta v = 20 (+140/-40) km/s | F: Small offset, possibly implying escape routes for ionizing photons | **partially**

## Reasoning

- Why this data: [C II] gives redshifts and ISM information where Lya is suppressed; lensing allows probing typical galaxies  
  > "Due to gravitational lensing we reach lower intrinsic flux limits (factor of $\sim 5$) than similar observations of field galaxies" (Conclusions)
- Why this method: _not stated_
- How they decided it was enough: _not stated_
- Limitation (authors): No other sources in the field for relative astrometric calibration  
  > "Unfortunately, we do not detect any other sources in our small field-of-view to perform relative astrometric calibration." (Results)
- Limitation (authors): Dynamical mass is very uncertain  
  > "Note that this approximation is very uncertain, as $z\sim 7$ galaxies might not have ordered motion." (Results)
- Caveat (inferred, ours): Single marginal (5 sigma) detection
- Caveat (inferred, ours): Large Lya velocity offset error
- Caveat (inferred, ours): Magnification model not described in detail
- Caveat (inferred, ours): Single galaxy limits generality

## Reproducibility

- Data public (paper): ALMA project code given; public status not stated  
  > "This paper makes use of the following ALMA data: ADS/JAO.ALMA#2015.1.00091.S." (Acknowledgments)
- Products in archive: _not stated_
- Missing: CASA version and imaging details
- Missing: Lens model
- Missing: Keck/HST/Spitzer data and SED fitting code details
- Data volume (inferred): ~10-50 GB raw (single Band 6 execution)
- Score (inferred): 3/5, ALMA project code and key imaging parameters given and numbers are explicit, but many processing and SED/lensing details are missing.
- Rediscovery candidate: no, Recipe incomplete (masks, extraction aperture, lensing model) though numeric results are clear.

## Links

- Method: (cite: huang15a) (Stellar population SED fitting and Lya redshift)
- Companion: (cite: schmidt16) (GLASS Lya detection of the same object)
- Related: CLASH
- Related: GLASS
- Related: SURFSUP

## Checks

```json
{
 "quotes": 66,
 "quotes_ok": 66,
 "quote_pass_rate": 1.0,
 "quotes_too_long": 0,
 "unsupported_facts": 0,
 "project_codes": 1,
 "codes_not_in_text": [],
 "codes_not_in_obscore": [],
 "obscore_codes_not_in_card": [],
 "codes_printed_but_missing": [],
 "numeric_results": 9,
 "numeric_problems": 0,
 "fill": {
  "facts": 74,
  "stated": 47,
  "rate": 0.635
 },
 "evidence_ok": true
}
```
