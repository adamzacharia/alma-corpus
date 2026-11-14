# Detection of the Far-infrared [O III] and Dust Emission in a Galaxy at Redshift 8.312: Early Metal Enrichment in the Heart of the Reionization Era

`2019ApJ...874...27T` | The Astrophysical Journal 2019 | first author: Tamura, Yoichi | arXiv: 1806.04132 | DOI: 10.3847/1538-4357/ab0374

Card schema 1.0 | model claude-sonnet-5-5 | depth full | type observational_alma_primary

## Science

- Fields: high_z_galaxies
- Question: Can ALMA Band 7 spectroscopically confirm the z~8.3 Y-dropout LBG MACS0416_Y1 via [O III] 88 um, and what do its dust and metal content imply for early enrichment?  
  > "How and when metal enrichment happened in the epoch of reionization (EoR) is one of the most fundamental questions in modern astronomy." (1 Introduction)
- Target **MACS0416_Y1**: coordinates ICRS (04h16m09.415s, -24d05m35.54s)  
  > "The phase tracking center was set to the LBG position" (4.1 Observations); "MACS0416_Y1 lies behind the MACS J0416.1$-$2403 cluster, one of the *Hubble* Frontier Fields" (2 Target); z/distance z = 8.3118 ± 0.0003 (from [O III])  
  > "The phase tracking center was set to the LBG position" (4.1 Observations); "MACS0416_Y1 lies behind the MACS J0416.1$-$2403 cluster, one of the *Hubble* Frontier Fields" (2 Target); distance from [O III] 88 um line detected with ALMA  
  > "The phase tracking center was set to the LBG position" (4.1 Observations); "MACS0416_Y1 lies behind the MACS J0416.1$-$2403 cluster, one of the *Hubble* Frontier Fields" (2 Target)

## Data provenance

- ALMA projects: 2016.1.00117.S, 2013.1.00999.S
- bands: Band 7, four tunings (T1-T4), 340.0-366.4 GHz  
  > "Four different tunings were assigned to cover contiguous frequency range between 340.0 and 366.4 GHz." (3.1 ALMA Observations and Reduction)
- frequencies and spectral setup: LO at 347.80, 351.40, 355.00, 358.60 GHz; frequency-division mode, 4 SPWs, channel spacing 7.8125 MHz  
  > "The correlator was configured with the frequency-division mode, in which the four spectral windows (SPWs) cover 7.5 GHz with respect to the central frequencies with a channel spacing of 7.8125 MHz." (3.1 ALMA Observations and Reduction)
- continuum bandwidth: _not stated_
- arrays: _not stated_
- configurations: _not stated_
- baselines: 15-2647 m across the 13 executions  
  > "2017-07-03 12:28:53 | 21–2647 | 40 | 358.60 (T4) | 30.23 | 0.24" (Table 1)
- angular resolution: continuum beam 0.26'' x 0.21'' (natural weighting); cube beam 0.38'' x 0.36'' (tapered)  
  > "The resulting synthesized beam size in full width at half maximum (FWHM) is $0.26\ensuremath{''} \times 0.21\ensuremath{''}$ (position angle PA = $-82\ensuremath{^\circ}$)." (3.1 ALMA Observations and Reduction)
- max recoverable scale: _not stated_
- sensitivity: continuum rms 10.9 uJy/beam; cube rms 0.5 mJy/beam at 364 GHz (31.25 MHz channels)  
  > "The r.m.s. noise level after combining all of the SPWs is $\sigma = 10.9$ $\mu$Jy beam$^{-1}$" (4.1 Detection of 850 um Dust Continuum)
- time on source: 436 min in total  
  > "The on-source time was 436 min in total." (3.1 ALMA Observations and Reduction)
- observing dates: 2016 October to December and 2017 May to July  
  > "The ALMA observations were carried out from 2016 October to December and 2017 May to July as a Cycle 4 program" (3.1 ALMA Observations and Reduction)
- pi or archival as stated: _not stated_
- Line: [O III] 88 um (not stated)
- Other facility **VLT/X-shooter**: 10 h of near-IR/optical spectroscopy; no UV lines detected, giving 5 sigma limits  
  > "We observed MACS0416_Y1 with VLT/X-shooter (cite: Vernet11) for a total of 10 hours on target." (3.3 X-shooter Observations and Reduction)
- Other facility **HST and Spitzer**: UV-to-optical photometry for SED fitting and astrometry  
  > "All of the photometry are obtained in this work; see (cite: Laporte15) (*HST* and *Spitzer*)" (Table 4)
- Other facility **Gaia DR1**: astrometric correction of HST images  
  > "we use four positions of objects (3 stars and 1 cluster elliptical) accurately measured in the *Gaia* first data release (DR1) catalog" (3.2 ALMA and Hubble Astrometry)
- External data: Previous 1.14 mm imaging of the cluster (ALMA Band 6), giving a 2 sigma upper limit of 116 uJy  
  > "We also retrieve a previous 1.14 mm imaging result obtained for the MACS J0416.1$-$2403 cluster (cite: Gonzalez-Lpez17)." (4.1 Detection of 850 um Dust Continuum) [from (cite: Gonzalez-Lpez17)]
- External data: Lensing magnification mu_g = 1.43 ± 0.04  
  > "The value is corrected for lensing magnification of $\mu_\mathrm{g} = 1.43 \pm 0.04$ (cite: Kawamata16)" (Table 2) [from (cite: Kawamata16)]

## Processing

### Calibration

- pipeline or manual: Standard pipeline plus manual flagging of some outlier antennas  
  > "manual flagging was needed for some outlier antennas" (3.1 ALMA Observations and Reduction)
- casa version: CASA 4.7.2  
  > "The calibration and flagging were made using a standard pipeline running on CASA (cite: McMullin07) version 4.7.2" (3.1 ALMA Observations and Reduction)
- pipeline version: _not stated_
- archive products used as is: _not stated_
- flux calibrator: J0522-3627 (T2, T3) and J0334-4008 (T1, T4)  
  > "Flux was scaled using J0522$-$3627 (for the tunings T2 and T3, $S_\mathrm{850\,\mu m} \simeq 3$–4 Jy) and J0334-4008" (3.1 ALMA Observations and Reduction)
- flux scale uncertainty: better than 10%  
  > "yielding an absolute accuracy better than 10%." (3.1 ALMA Observations and Reduction)
- self calibration: _not stated_

### Imaging

- task: CASA clean  
  > "Four tuning data are combined to make the continuum image using the CASA task, `clean`, with the natural weighting." (3.1 ALMA Observations and Reduction)
- deconvolver: _not stated_
- weighting robust: natural weighting  
  > "Four tuning data are combined to make the continuum image using the CASA task, `clean`, with the natural weighting." (3.1 ALMA Observations and Reduction)
- uv taper: 0.35'' Gaussian taper for cubes  
  > "we optimally-taper the image with a $0.35\ensuremath{''}$ Gaussian kernel to maximize the signal-to-noise ratio" (3.1 ALMA Observations and Reduction)
- cell size: _not stated_
- image size: _not stated_
- masking: [O III] line channels excluded from continuum imaging; deconvolution down to 2 sigma  
  > "Synthesized beam deconvolution is made down to $2\sigma$." (3.1 ALMA Observations and Reduction)
- multiscale scales: _not stated_
- continuum subtraction: _not stated_
- line free channels: _not stated_
- primary beam correction: _not stated_
- array combination: _not stated_
- smoothing: cubes with 31.25 MHz (~26 km/s) channels  
  > "Each tuning data set was also imaged to produce a cube with a frequency resolution of 31.25 MHz ($\approx 26$ km s$^{-1}$)" (3.1 ALMA Observations and Reduction)
- final beam: 0.38'' x 0.36'' (PA = -79 deg) for cube  
  > "The resulting beam size and r.m.s. noise level measured at 364 GHz are $0.38\ensuremath{''} \times 0.36\ensuremath{''}$ (PA = $-79\ensuremath{^\circ}$)" (3.1 ALMA Observations and Reduction)
- final rms: _not stated_

### Inherited from earlier work

- SED model prescription (PANHIT)  
  > "The model is based on the prescription presented by (cite: Mawatari16) and Mawatari et al. in preparation" (5.1 Spectral Energy Distribution Model) [from (cite: Mawatari16)]
- [O III] 88 um emissivity vs metallicity relation  
  > "we use the prescription of (cite: Inoue14), where the [O III] emissivity for a unit SFR" (5.1 Spectral Energy Distribution Model) [from (cite: Inoue14)]
- Monte Carlo error estimation of SED parameters  
  > "estimated from probability distribution functions (PDFs) on the basis of a Monte Carlo technique following the prescription presented by (cite: Hashimoto18)" (Table 5) [from (cite: Hashimoto18)]
- Dust evolution model and ISM phase fractions  
  > "We assume the mass fractions of WNM, CNM and MC to be $(\eta_\mathrm{WNM},\,\eta_\mathrm{CNM},\,\eta_\mathrm{MC}) = (0.5,\, 0.3,\, 0.2)$ following (cite: Nozawa15)." (6.1 Dust mass evolution model) [from (cite: Asano13a; Asano13b; Asano14; Nozawa15)]

### Not stated but needed to reproduce (our reading)

- Number of clean iterations, threshold, mask and cell/image size
- Line-free channel ranges used for continuum imaging
- Whether archive pipeline products or reprocessed data were used
- Role of project 2013.1.00999.S in this paper
- Details of the imfit regions and the line-integration velocity range
- SED fitting code details (PANHIT unpublished); photometric aperture details
- Dust evolution model code and full parameter set

## Analysis recipe

1. **Calibrate and image ALMA Band 7 data**: Standard pipeline calibration in CASA with manual flagging; continuum imaged with clean excluding line channels; cubes tapered  
  > "Note that spectral channels where the [O III] line is detected were not used for continuum imaging." (3.1 ALMA Observations and Reduction)
   - software: CASA
   - parameter: natural weighting; 0.35'' taper; 31.25 MHz channels  
  > "we optimally-taper the image with a $0.35\ensuremath{''}$ Gaussian kernel to maximize the signal-to-noise ratio" (3.1 ALMA Observations and Reduction)
   - fitting: _not stated_
   - validation: _not stated_
2. **Align HST and ALMA astrometry**: Shift HST images to the Gaia DR1 frame using IRAF ccsetwcs; compare ALMA and Gaia phase calibrator positions  
  > "All of the *HST* images are corrected for astrometry on the basis of the *Gaia* coordinates using the IRAF (cite: Tody93) task, `ccsetwcs`" (3.2 ALMA and Hubble Astrometry)
   - software: IRAF
   - fitting: _not stated_
   - validation: ALMA-Gaia offsets < 10 mas; HST-Gaia frames agree to <~30 mas  
  > "We find that the relative offsets between the ALMA and *Gaia* coordinates are typically $< 10$ mas." (3.2 ALMA and Hubble Astrometry)
3. **Measure continuum flux and size**: 2D Gaussian fit to the 850 um continuum image  
  > "The flux density and the image component size deconvolved with the synthesized beam are measured using a CASA task `imfit` with an assumption that the source is 2-dimensional Gaussian" (4.1 Detection of 850 um Dust Continuum)
   - software: CASA imfit
   - fitting: 2D Gaussian via imfit  
  > "measured using a CASA task `imfit` with an assumption that the source is 2-dimensional Gaussian" (4.1 Detection of 850 um Dust Continuum)
   - validation: _not stated_
4. **Derive L_IR and dust mass**: Modified blackbody (8-1000 um) with CMB heating correction, de-lensed  
  > "The IR luminosity is derived from a modified blackbody defined in the range of 8–1000 $\ensuremath{\mu}m$." (Table 2)
   - assumption: T_dust = 50 K (40 K), beta = 1.5, kappa_d(850um) = 0.15 m^2/kg, nu0 = 353 GHz, mu_g = 1.43  
  > "$\kappa_\mathrm{d}(850~\ensuremath{\mu}m) = 0.15$ m$^2$ kg$^{-1}$ (cite: Weingartner01; Dunne03) and $\beta = 1.5$" (Table 2)
   - fitting: _not stated_
   - validation: _not stated_
5. **Detect and characterise [O III] line**: Blind search in cubes; Gaussian fit to spectrum; integrated intensity image  
  > "The line width is estimated by a Gaussian fit (Figure 3) and is found to be $\Delta V_\mathrm{[O\,III]} = 141 \pm 21$ km s$^{-1}$ in FWHM" (4.2 Blind Detection of [O III] 88 um)
   - software: CASA
   - fitting: Gaussian line fit  
  > "The line width is estimated by a Gaussian fit" (4.2 Blind Detection of [O III] 88 um)
   - validation: X-shooter UV lines not detected; redshift consistent with photo-z  
  > "At the redshift of [O III] 88 $\mu$m from ALMA ($z=8.3118$) no rest-frame UV emission lines were detected." (4.3 UV emission line detection limits)
6. **SED fitting with [O III] emissivity**: Template grid fit of UV-to-FIR photometry plus 850 um and [O III] with stellar, nebular and dust components  
  > "we characterize the SED to investigate the physical properties of MACS0416_Y1 by template fits where stellar populations, UV-to-FIR nebular emission, and dust thermal emission are taken into account." (5.1 Spectral Energy Distribution Model)
   - software: PANHIT
   - parameter: tau_SFH = ±0.01, ±0.1, ±1, ±10 Gyr; Z = 0.0001-0.02; A_V = 0-5; f_esc free  
  > "We also explore five metallicity values of $Z = 0.0001$, 0.0004, 0.004, 0.008, and 0.02" (5.1 Spectral Energy Distribution Model)
   - assumption: Bruzual & Charlot 2003, Chabrier IMF 0.1-100 Msun; Calzetti/SMC/MW extinction; Inoue14b IGM transmission  
  > "We use the stellar population synthesis model from (cite: Bruzual03) with the Chabrier initial mass function (IMF) defined in the range of 0.1–100" (5.1 Spectral Energy Distribution Model)
   - fitting: chi^2 grid fit with Monte Carlo PDFs (68% intervals)  
  > "The error bars represent the 68$\%$ confidence interval estimated from probability distribution functions (PDFs) on the basis of a Monte Carlo technique" (Table 5)
   - validation: Three extinction laws compared via chi^2 (7.1, 6.8, 8.4; 3 dof)  
  > "$\chi^2$ | 7.1 | 6.8 | 8.4" (Table 5)
7. **Compare dust mass with a dust evolution model**: Analytic dust evolution model of Asano/Nozawa with three ISM phases, single star-formation episode, then adding an old stellar component  
  > "Here we employ a dust formation model developed by (cite: Asano13a; Asano13b; Asano14) and (cite: Nozawa15)" (6.1 Dust mass evolution model)
   - parameter: tau_SFH = 0.3 Gyr; M_tot = 2e10 Msun; (eta_WNM, eta_CNM, eta_MC) = (0.5, 0.3, 0.2)  
  > "The total baryon mass is scaled to $M_\mathrm{tot} = 2 \times 10^{10}~M_{\ensuremath{\odot}}$" (6.1 Dust mass evolution model)
   - assumption: Chabrier IMF; no parameter optimisation except baryon mass scaling  
  > "Note that except this scaling, we made no parameter optimization nor fine-tuning with respect to the best-fitting values obtained by the SED fits." (6.1 Dust mass evolution model)
   - fitting: _not stated_
   - validation: Model stellar mass and SFR at 4 Myr roughly match SED values  
  > "are well aligned with the results from the SED analysis" (6.1 Dust mass evolution model)

## Software

- **CASA** 4.7.2: calibration, clean imaging, imfit  
  > "The calibration and flagging were made using a standard pipeline running on CASA (cite: McMullin07) version 4.7.2" (3.1 ALMA Observations and Reduction)
- **IRAF** : HST astrometry correction with ccsetwcs  
  > "using the IRAF (cite: Tody93) task, `ccsetwcs`" (3.2 ALMA and Hubble Astrometry)
- **esorex** : X-shooter data reduction  
  > "The data were reduced with esorex scripts (cite: Modigliani10)" (3.3 X-shooter Observations and Reduction)
- **Molecfit** : telluric correction of X-shooter spectra  
  > "Corrections for telluric absorption lines were applied from models with Molecfit (cite: Kausch15)" (3.3 X-shooter Observations and Reduction)
- **PANHIT** : SED modelling tool  
  > "Panchromatic Analysis for Nature of HIgh-$z$ galaxies Tool (PANHIT)" (5.1 Spectral Energy Distribution Model)

## Numeric results

| quantity | value | uncertainty | units | step | quote |
|---|---|---|---|---|---|
| 850 um continuum flux density | 137 | 26 | uJy | 3 | $S_\mathrm{850\,\mu m} = 137 \pm 26$ $\mu$Jy |
| Continuum significance | 7.6 | not stated | sigma | 3 | yielding the significance of $7.6\sigma$ on the resulting image |
| Spectroscopic redshift | 8.3118 | 0.0003 | dimensionless | 5 | $z = 8.3118 \pm 0.0003$ |
| [O III] flux | 0.66 | 0.16 | Jy km/s | 5 | $F_\mathrm{[O\,III]} = 0.66 \pm 0.16$ Jy km s$^{-1}$ |
| [O III] line FWHM | 141 | 21 | km/s | 5 | $\Delta V_\mathrm{[O\,III]} = 141 \pm 21$ km s$^{-1}$ in FWHM |
| [O III] luminosity (de-lensed) | 1.2e9 | 0.3e9 | Lsun | 5 | $L_\mathrm{[O\,III]} = (1.2 \pm 0.3) \times 10^{9} L_{\ensuremath{\odot}}$ |
| L_IR (T_dust=50 K, de-lensed) | 1.7e11 | 0.3e11 | Lsun | 4 | $1.7 \pm 0.3$ / $3.6 \pm 0.7$ |
| Dust mass (T_dust=50 K, de-lensed) | 3.6e6 | 0.7e6 | Msun | 4 | a dust mass of $M_\mathrm{dust}= (3.6 \pm 0.7) \times 10^{6} M_\ensuremath{\odot}$ |
| Spectral index upper limit 1.14 mm to 850 um | >0.6 | 2 sigma limit | dimensionless | 3 | $\alpha > 0.6$ (2$\sigma$) |
| SED stellar mass (MW law) | 2.4e8 | +0.6/-0.3 e8 | Msun | 6 | $2.4 ^{+0.6}_{-0.3}$ |
| SED metallicity | 0.2 | +0.17/-0.18 (MW) | Zsun | 6 | $0.20 ^{+0.17}_{-0.18}$ |
| SED age (MW law) | 4.2 | +0.3/-3.0 | Myr | 6 | $4.2  ^{+0.3}_{-3.0}$ |

## Qualitative findings

- The line and dust together imply a young starburst with already substantial metals and a large dust mass that requires an underlying evolved stellar component.  
  > "suggesting a pre-existing evolved stellar component with $M_\mathrm{star} \sim 3 \times 10^9~M_{\ensuremath{\odot}}$ and $\tau_\mathrm{age} \sim 0.3$ Gyr as the origin of the dust mass." (abstract)

## Claim tuples

- H: Is MACS0416_Y1 a z~8.3 galaxy detectable in [O III] 88 um? | E: Band 7 four-tuning scan covering z 8.3-8.7 | R: Line at 364.377 GHz, 6.3 sigma | F: Spectroscopic redshift z = 8.3118 | **supported**
- H: Does the galaxy contain a large dust mass? | E: 850 um continuum imaging and modified blackbody | R: 137 uJy, M_dust ~ 4e6 Msun | F: Fast dust assembly at 600 Myr age of Universe | **supported**
- H: Can a single young star-formation episode explain the metallicity and dust mass? | E: Dust evolution model compared with SED results | R: Model metallicity and dust mass too low at 4 Myr | F: An evolved older stellar population (~3e9 Msun, ~0.3 Gyr) is suggested | **supported**

## Reasoning

- Why this data: Bright z~8 candidate with accurate photo-z accessible from ALMA; four Band 7 tunings cover the likely redshift range  
  > "The most-likely redshift interval $8.3 < z < 8.7$ can be covered by four tunings of ALMA Band 7" (2 Target)
- Why this method: _not stated_
- Alternative: Low-z non-thermal interloper disfavoured by spectral index limit  
  > "this could rule out a low-$z$ interloper with non-thermal emission from an active galactic nucleus" (4.1 Detection of 850 um Dust Continuum)
- How they decided it was enough: _not stated_
- Limitation (authors): Photometric constraints are weak (large K_S uncertainty) and the metallicity uncertainty is large  
  > "The best-fitting metallicity already reaches $Z \approx 0.2 Z_\ensuremath{\odot}$ at $z = 8.3$ despite a large uncertainty" (5.2 Results)
- Caveat (inferred, ours): Dust mass and L_IR depend on assumed T_dust and beta with only a single continuum point
- Caveat (inferred, ours): SED fit has few data points (3 dof) with degenerate parameters
- Caveat (inferred, ours): Old stellar component is a plausible solution, not a constrained detection
- Caveat (inferred, ours): Dust model not fitted to data

## Reproducibility

- Data public (paper): ALMA project codes cited; public status not stated explicitly  
  > "This paper makes use of the following ALMA data: ADS/JAO.ALMA #2016.1.00117, ADS/JAO.ALMA #2013.1.00999.S." (Acknowledgments)
- Products in archive: _not stated_
- Missing: clean parameters (niter, threshold, mask, image size)
- Missing: line-free channel selection
- Missing: unpublished SED code details (PANHIT in prep.)
- Missing: dust evolution model code
- Data volume (inferred): ~100-300 GB raw for 13 Band 7 executions
- Score (inferred): 3/5, Data and main imaging steps are described and the numbers are explicit, but clean parameters are missing and the SED and dust models rely on unreleased or inherited code.
- Rediscovery candidate: no, The ALMA measurements could be redone, but the SED and dust modelling are not specified well enough.

## Links

- Method: (cite: Inoue14) ([O III] emissivity model)
- Method: (cite: Mawatari16) (SED model prescription)
- Method: (cite: Nozawa15) (dust evolution model)
- Companion: (cite: Hashimoto18) (MACS1149-JD1 [O III] at z=9.11, similar analysis)
- Companion: (cite: Laporte17) (A2744_YD4 [O III] and dust detection)
- Related: Hubble Frontier Fields
- Related: CLASH
- Related: Herschel Dwarf Galaxy Survey

## Checks

```json
{
 "quotes": 82,
 "quotes_ok": 82,
 "quote_pass_rate": 1.0,
 "quotes_too_long": 0,
 "unsupported_facts": 0,
 "project_codes": 2,
 "codes_not_in_text": [],
 "codes_not_in_obscore": [],
 "obscore_codes_not_in_card": [],
 "codes_printed_but_missing": [],
 "numeric_results": 12,
 "numeric_problems": 0,
 "fill": {
  "facts": 87,
  "stated": 60,
  "rate": 0.69
 },
 "evidence_ok": true
}
```
