# Sub-kpc star formation law in the local luminous infrared galaxy IC 4687 as seen by ALMA

`2016A&A...587A..44P` | Astronomy and Astrophysics 2016 | first author: Pereira-Santaella, M. | arXiv: 1601.02427 | DOI: 10.1051/0004-6361/201527693

Card schema 1.0 | model claude-sonnet-5-5 | depth full | type observational_alma_primary

## Science

- Fields: nearby_galaxies, star_formation
- Question: How does the sub-kpc (250 pc) and integrated star formation law of the local LIRG IC 4687 compare with normal nearby galaxies and high-z galaxies?  
  > "In this paper, we present one of the first sub-kpc analyses of the SF law in a local extreme starburst." (1 Introduction)
- Target **IC 4687**: coordinates _not stated_; z/distance d = 74 Mpc (345 pc/arcsec)  
  > "we study the local ($d$=74 Mpc; 345 pc arcsec$^{-1}$) luminous IR galaxy (LIRG) IC 4687." (1 Introduction); distance from _not stated_

## Data provenance

- ALMA projects: 2013.1.00271.S
- bands: Band 6  
  > "We obtained band 6 observations of IC 4687 with ALMA on August 28 2014 and April 5 2015" (2.1 12CO(2–1) ALMA data)
- frequencies and spectral setup: Two 1.875 GHz spws at CO(2–1) (226.4 GHz) and CS(5–4) (240.7 GHz), 0.48 MHz channels; continuum spws at 228.6 and 243.4 GHz  
  > "Two spectral windows of 1.875 GHz bandwidth (0.48 MHz $\sim$ 0.6 km/s channels) were centered at the sky frequencies of $^{12}$CO(2–1) (226.4 GHz) and CS(5–4) (240.7 GHz)." (2.1 12CO(2–1) ALMA data)
- continuum bandwidth: _not stated_
- arrays: Extended and compact configurations with 35 and 39 antennas  
  > "using extended and compact antenna array configurations with 35 and 39 antennas, respectively" (2.1 12CO(2–1) ALMA data)
- configurations: _not stated_
- baselines: 33.7 m–1.1 km (extended); 15.1–328 m (compact)  
  > "The extended configuration had baselines between 33.7 m and 1.1 km, while the baselines ranged between 15.1 m and 328 m for the compact configuration." (2.1 12CO(2–1) ALMA data)
- angular resolution: 0.31"x0.39" (~100x130 pc), PA 35 deg  
  > "a beam with a full width half maximum (FWHM) of 0.31$''$$\times$0.39$''$ ($\sim$100 pc$\times$130 pc) with a position angle (PA) of 35$^\circ$" (2.1 12CO(2–1) ALMA data)
- max recoverable scale: 4.9" and 10.9"  
  > "the maximum recoverable scales are 4.9$''$ and 10.9$''$, respectively." (2.1 12CO(2–1) ALMA data)
- sensitivity: ~1 mJy/beam per 4 MHz channel  
  > "For the final 4 MHz channels, the achieved 1$\sigma$ sensitivity is $\sim$1 mJy beam$^{-1}$." (2.1 12CO(2–1) ALMA data)
- time on source: 18 and 9 min (extended, compact)  
  > "The on-source integration times were 18 and 9 min, respectively." (2.1 12CO(2–1) ALMA data)
- observing dates: 28 August 2014 and 5 April 2015  
  > "on August 28 2014 and April 5 2015" (2.1 12CO(2–1) ALMA data)
- pi or archival as stated: _not stated_
- Line: 12CO J=2-1 (226.4 GHz (sky frequency))
- Other facility **HST/NICMOS**: Paα narrowband map used for SFR  
  > "We used the continuum subtracted narrowband Pa$\alpha$ *HST*/NICMOS image of IC 4687 (cite: AAH06s) to determine the resolved SFR." (2.2 Ancillary HST/NICMOS and VLT/SINFONI data)
- Other facility **VLT/SINFONI**: Near-IR IFS extinction maps (Brγ/Brδ)  
  > "we used the 2D extinction maps of this galaxy derived with near-IR VLT/SINFONI integral field spectroscopy (cite: Piqueras2013; Piqueras2015)" (2.2 Ancillary HST/NICMOS and VLT/SINFONI data)
- External data: Single-dish SEST CO(2-1) flux 480 Jy km/s and R21=0.7  
  > "the single-dish CO(2–1) flux measured with the 15 m SEST telescope (24$''$ beam size) is 480 Jy km s$^{-1}$ (cite: Albrecht2007)" (2.1 12CO(2–1) ALMA data) [from (cite: Albrecht2007)]
- External data: Brγ/Brδ extinction map and Paα HST/NICMOS image  
  > "we used the Br$\gamma$/Br$\delta$ ratio map of (cite: Piqueras2013)" (3.2 Characterization of the regions) [from (cite: Piqueras2013)]
- External data: Rotation curve, inclination 47 deg  
  > "($i=47$ $^\circ$; (cite: Bellocchi2013))" (3.2 Characterization of the regions) [from (cite: Bellocchi2013)]
- External data: Comparison resolved SF-law data of nearby galaxies  
  > "we compare the spatially resolved (200–500 pc) SFR and molecular gas surface densities of nearby galaxies presented by (cite: Leroy2008) and (cite: Casasola2015)" (4 Comparison with local galaxies) [from (cite: Leroy2008); (cite: Casasola2015)]

## Processing

### Calibration

- pipeline or manual: Standard ALMA reduction with CASA  
  > "The two datasets were calibrated using the standard ALMA reduction software CASA (v4.2.2; (cite: McMullin2007))." (2.1 12CO(2–1) ALMA data)
- casa version: CASA 4.2.2  
  > "CASA (v4.2.2; (cite: McMullin2007))" (2.1 12CO(2–1) ALMA data)
- pipeline version: _not stated_
- archive products used as is: _not stated_
- flux calibrator: J1617-5848 (0.651 Jy at 226.4 GHz) and Titan (Butler-JPL-Horizons 2012) for extended and compact  
  > "We used J1617-5848 for the amplitude calibration, assuming a flux density of 0.651 Jy at 226.4 GHz, and Titan, using the Butler-JPL-Horizons 2012 model" (2.1 12CO(2–1) ALMA data)
- flux scale uncertainty: ~15%  
  > "with a flux calibration uncertainty about 15%" (2.1 12CO(2–1) ALMA data)
- self calibration: _not stated_

### Imaging

- task: _not stated_
- deconvolver: _not stated_
- weighting robust: Briggs, robust = 0.5  
  > "we used the Briggs weighting with a robustness parameter of 0.5" (2.1 12CO(2–1) ALMA data)
- uv taper: _not stated_
- cell size: 0.07"  
  > "we used 4 MHz channels ($\sim$5 km s$^{-1}$) and 256$\times$256 pixels of 0.07$''$" (2.1 12CO(2–1) ALMA data)
- image size: 256x256 pixels  
  > "256$\times$256 pixels of 0.07$''$" (2.1 12CO(2–1) ALMA data)
- masking: Mask from observed CO(2-1) emission in each channel  
  > "A mask derived from the observed CO(2–1) emission in each channel was used during the clean process." (2.1 12CO(2–1) ALMA data)
- multiscale scales: _not stated_
- continuum subtraction: Fit with line-free channels, subtracted in uv plane  
  > "the continuum (0.15-0.05 mJy beam$^{-1}$) was fitted with the line free channels and subtracted in the $uv$ plane" (2.1 12CO(2–1) ALMA data)
- line free channels: _not stated_
- primary beam correction: Applied to cubes  
  > "We applied the primary beam correction to the data cubes." (2.1 12CO(2–1) ALMA data)
- array combination: uv visibilities combined after converting to LSRK  
  > "converted to a common frequency reference frame (kinematic local standard of rest; LRSK) and then combined" (2.1 12CO(2–1) ALMA data)
- smoothing: _not stated_
- final beam: 0.31"x0.39", PA 35 deg  
  > "FWHM) of 0.31$''$$\times$0.39$''$" (2.1 12CO(2–1) ALMA data)
- final rms: ~1 mJy/beam per 4 MHz channel  
  > "the achieved 1$\sigma$ sensitivity is $\sim$1 mJy beam$^{-1}$" (2.1 12CO(2–1) ALMA data)

### Inherited from earlier work

- Rotation curve from kinemetry, inclination and PA  
  > "the rotation curve derived by (cite: Bellocchi2013) using kinemetry" (4.4 Local dynamical time) [from (cite: Bellocchi2013)]
- SFR calibration for Hα  
  > "converted into SFR following the (cite: Kennicutt2012) calibration for H$\alpha$" (3.2 Characterization of the regions) [from (cite: Kennicutt2012)]
- Extinction maps from SINFONI  
  > "2D extinction maps of this galaxy derived with near-IR VLT/SINFONI integral field spectroscopy (cite: Piqueras2013; Piqueras2015)" (2.2 Ancillary HST/NICMOS and VLT/SINFONI data) [from (cite: Piqueras2013; Piqueras2015)]

### Not stated but needed to reproduce (our reading)

- Line-free channels used for continuum fit
- Number of clean iterations and threshold
- Phase center coordinates
- Exact smoothing kernel for Paα and alignment offsets
- Aperture photometry background treatment
- Fitting method for SF law power-law (N=1.6)
- Uncertainty derivation for regions

## Analysis recipe

1. **Calibrate and image CO(2-1) cube**: CASA calibration, combine extended and compact data, uv continuum subtraction, clean with Briggs weighting and mask, primary beam correction  
  > "The two datasets were calibrated using the standard ALMA reduction software CASA (v4.2.2; (cite: McMullin2007))." (2.1 12CO(2–1) ALMA data)
   - software: CASA
   - parameter: robust 0.5; 4 MHz channels; 0.07" pixels  
  > "we used 4 MHz channels ($\sim$5 km s$^{-1}$) and 256$\times$256 pixels of 0.07$''$" (2.1 12CO(2–1) ALMA data)
   - fitting: _not stated_
   - validation: Compared ALMA flux (460 Jy km/s) with SEST single-dish (480 Jy km/s)  
  > "we are able to recover most of the CO(2–1) flux of this source" (2.1 12CO(2–1) ALMA data)
2. **Align and match ancillary maps**: Convolve Paα to ALMA resolution; align stellar peak with CO dynamical center from the velocity-field directional derivative  
  > "The original Pa$\alpha$ map (0.15$''$ resolution) was convolved with a Gaussian kernel to match the angular resolution of the ALMA map." (2.2 Ancillary HST/NICMOS and VLT/SINFONI data)
   - fitting: _not stated_
   - validation: _not stated_
3. **Define regions and measure CO and Paα**: 10 sigma peaks in CO and Paα maps; 0.7" (250 pc) apertures; 81 regions, 54 with Brγ and Brδ >6 sigma  
  > "Emission peaks above a 10$\sigma$ level were considered." (3.2 Characterization of the regions)
   - parameter: Match radius 0.35"; spectra integrated over 5000–5400 km/s above 3 sigma  
  > "we extracted their spectra and integrated all the channels above a 3$\sigma$ level within the velocity range of the CO(2–1) emission in this object (5000–5400 km s$^{-1}$)" (3.2 Characterization of the regions)
   - fitting: _not stated_
   - validation: _not stated_
4. **Derive gas mass and SFR surface densities**: H2 mass from CO(2-1) with alpha_CO=4.35 and R21=0.7; extinction-correct Paα using Brγ/Brδ, convert to SFR; correct by cos 47 deg  
  > "using the Galactic CO-to-H$_2$ conversion factor, $\alpha_{\rm CO}^{1-0}=4.35$" (3.2 Characterization of the regions)
   - assumption: Intrinsic Brγ/Brδ=1.52, F99 extinction law, Hα/Paα=8.58, Kroupa IMF, i=47 deg  
  > "assumed an intrinsic Br$\gamma$/Br$\delta$ ratio of 1.52 (cite: Hummer1987) and the (cite: Fitzpatrick1999) extinction law" (3.2 Characterization of the regions)
   - fitting: _not stated_
   - validation: Compared with Calzetti law, average extinction, AK vs NH2 relation, and IMF sampling via Starburst99  
  > "We also tried the (cite: Calzetti2000) extinction law." (3.3.2 Extinction correction and SFR tracer)
5. **Compare with local and high-z SF laws and compute integrated properties**: Compare with Leroy2008 and Casasola2015 data; power-law fit; integrated values over 3x3 kpc using Brγ-based SFR  
  > "a nonlinear SF law fits the data with a power-law index of $N=1.6$" (4.3 Higher star formation efficiency?)
   - fitting: _not stated_
   - validation: _not stated_

## Software

- **CASA** 4.2.2: Calibration, combination, imaging  
  > "CASA (v4.2.2; (cite: McMullin2007))" (2.1 12CO(2–1) ALMA data)
- **STARBURST 99** : Cluster ionizing radiation vs time to estimate young stellar masses  
  > "the STARBURST 99 code (cite: Leitherer1999) provides the ionizing radiation produced by a cluster as a function of time" (4.3 Dispersion of tdep in IC 4687)

## Numeric results

| quantity | value | uncertainty | units | step | quote |
|---|---|---|---|---|---|
| Integrated CO(2-1) flux in ALMA FOV | 460 | 15% calibration | Jy km/s | 1 | is 460 Jy km s$^{-1}$ with a flux calibration uncertainty about 15% |
| Mean log Sigma_H2 | 2.9 | 0.2 | log Msun/pc^2 | 4 | $\log \Sigma_{\rm H_2}{\rm (M_{\odot}\,pc^{-2})} = 2.9\pm0.2$ |
| Mean log Sigma_SFR | 0.7 | 0.4 | log Msun/yr/kpc^2 | 4 | $\log \Sigma_{\rm SFR}{\rm (M_{\odot}\,yr^{-1}\,kpc^{-2})} = 0.7\pm0.4$ |
| Depletion time of regions | 160 | +750/-140 | Myr | 4 | the $t_{\rm dep}$ of the IC 4687 regions is 160$^{+750}_{-140}$ Myr |
| Integrated SFR | 43 | 4 | Msun/yr | 5 | The total SFR, 43$\pm$4 $M_{\rm \odot}$ yr$^{-1}$ |
| Integrated cold molecular gas mass | 5.5e9 | not stated | Msun | 5 | we derive a total cold molecular gas mass of 5.5$\times$10$^9$ $M_{\rm \odot}$ |
| Power-law index of SF law | 1.6 | not stated | dimensionless | 5 | a nonlinear SF law fits the data with a power-law index of $N=1.6$ |
| tdep scatter | 0.4 | not stated | dex | 4 | the $t_{\rm dep}$ scatter within IC 4687 regions is relatively high, at 0.4 dex |
| Median AK of regions | 1.3 | not stated | mag | 4 | with a median $A_{\rm K}$ of 1.3 mag |

## Qualitative findings

- IC 4687 regions have depletion times about an order of magnitude shorter than nearby galaxies assuming Galactic alpha_CO  
  > "This is approximately one order of magnitude shorter than in nearby galaxies, which is 1–2 Gyr" (4 Comparison with local galaxies)

## Claim tuples

- H: Does IC 4687 follow the SF law of nearby galaxies at 250 pc scales? | E: Compared ALMA CO and Paα-based SFR in 54 regions with Leroy2008 and Casasola2015 | R: Σ_SFR ~10 times higher at similar Σ_H2; tdep 160 Myr vs 1–2 Gyr | F: SF is more efficient in IC 4687, consistent with a bimodal SF law | **supported**
- H: Is the local SF relation tight within IC 4687? | E: Spearman correlation of Σ_H2 and Σ_SFR | R: r_S=0.24, p=0.08 | F: The SF law breaks down at 250 pc or is hidden by scatter | **partially**

## Reasoning

- Why this data: _not stated_
- Why this method: Galactic alpha_CO preferred since IC 4687 is a weakly interacting rotating spiral  
  > "Therefore, we consider the Galactic $\alpha_{\rm CO}$ factor preferred for IC 4687." (4.1 Systematic uncertainties)
- Alternative: ULIRG-like alpha_CO rejected as it would make IC 4687 an extreme starburst  
  > "In principle, we do not expect such extreme behavior in a weakly interacting spiral galaxy such as IC 4687." (4.1 Systematic uncertainties)
- How they decided it was enough: _not stated_
- Limitation (authors): Extinction and alpha_CO systematics; evolutionary state of regions cannot be tested  
  > "With the current observations, however, it is not possible to establish the evolutionary state of the regions in IC 4687, so we cannot test this hypothesis." (4.4 Dispersion of tdep in IC 4687)
- Caveat (inferred, ours): Conclusions depend strongly on the adopted alpha_CO
- Caveat (inferred, ours): Single galaxy
- Caveat (inferred, ours): Weak Σ_H2–Σ_SFR correlation with p~0.08
- Caveat (inferred, ours): Mixed resolution of NICMOS, SINFONI and ALMA

## Reproducibility

- Data public (paper): ALMA project cited, archive data  
  > "This paper makes use of the following ALMA data: ADS/JAO.ALMA#2013.1.00271.S." (Acknowledgements)
- Products in archive: _not stated_
- Missing: SINFONI extinction maps and NICMOS Paα image from other papers
- Missing: Fitting method for SF law
- Missing: Region catalog
- Data volume (inferred): ~10-50 GB raw for two Band 6 executions
- Score (inferred): 3/5, ALMA processing is described, but the ancillary maps come from external works and the region and fitting details are incomplete.
- Rediscovery candidate: no, The SFR depends on external SINFONI and NICMOS maps not in the paper, so full reproduction is blocked.

## Links

- Method: (cite: Piqueras2013) (Brγ/Brδ extinction maps)
- Method: (cite: Kennicutt2012) (SFR calibration)
- Companion: (cite: Bellocchi2013) (Kinematics and inclination of the IC 4686/4687/4689 system)

## Checks

```json
{
 "quotes": 64,
 "quotes_ok": 64,
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
  "facts": 75,
  "stated": 50,
  "rate": 0.667
 },
 "evidence_ok": true
}
```
