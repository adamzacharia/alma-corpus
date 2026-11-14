# SPT 0538-50: Physical Conditions in the Interstellar Medium of a Strongly Lensed Dusty Star-forming Galaxy at z = 2.8

`2013ApJ...779...67B` | The Astrophysical Journal 2013 | first author: Bothwell, M. S. | arXiv: 1309.3275 | DOI: 10.1088/0004-637X/779/1/67

Card schema 1.0 | model claude-sonnet-5-5 | depth light | type multi_facility_alma_minor

## Science

- Fields: high_z_galaxies
- Question: What are the intrinsic physical properties and ISM conditions of the lensed DSFG SPT 0538-50 after de-blending from the foreground lens and de-lensing with an ALMA-based lens model?  
  > "With this lens model in hand we present a range of multi-wavelength observations of the source, and derive the intrinsic luminosity, star formation rate, stellar mass, molecular gas mass, and physical conditions of this interesting galaxy." (Introduction)
- Target **SPT 0538-50 (SPT-S J053816-5030.8)**: coordinates RA 05:38:16.83, DEC 50:30:52.0 (ALMA coordinates)  
  > "SPT 0538$-$50 (ALMA co-ordinates RA: 05:38:16.83, DEC: 50:30:52.0)" (2 Observations and results); "a gravitationally-lensed dusty star forming galaxy (DSFG) at $z=2.7817$" (abstract); z/distance z = 2.7817 (lens at z = 0.441)  
  > "SPT 0538$-$50 (ALMA co-ordinates RA: 05:38:16.83, DEC: 50:30:52.0)" (2 Observations and results); "a gravitationally-lensed dusty star forming galaxy (DSFG) at $z=2.7817$" (abstract); distance from CO lines (Z-Spec, SMA, ATCA); lens z from VLT/X-SHOOTER Ca H+K  
  > "SPT 0538$-$50 (ALMA co-ordinates RA: 05:38:16.83, DEC: 50:30:52.0)" (2 Observations and results); "a gravitationally-lensed dusty star forming galaxy (DSFG) at $z=2.7817$" (abstract)

## Data provenance

- ALMA projects: 2011.0.00958.S
- bands: Band 7 (LO 343.8 GHz)  
  > "The Band 7 local oscillator was tuned to 343.8 GHz" (2.1.2 ALMA)
- frequencies and spectral setup: four 1.875 GHz spectral windows at 336.8, 338.675, 348.925, 350.8 GHz; 7.5 GHz total  
  > "with four correlator spectral windows configured to receive 1.875 GHz wide bands in two polarizations each at central frequencies of 336.8, 338.675, 348.925, and 350.8 GHz" (2.1.2 ALMA)
- continuum bandwidth: _not stated_
- arrays: _not stated_
- configurations: _not stated_
- baselines: 20–150 kλ, 16 antennas  
  > "Baselines extended from 20–150k$\lambda$, creating a beam with a full width at half maximum (FWHM) of $\sim1.4''$." (2.1.2 ALMA)
- angular resolution: ~1.4'' FWHM  
  > "creating a beam with a full width at half maximum (FWHM) of $\sim1.4''$" (2.1.2 ALMA)
- max recoverable scale: _not stated_
- sensitivity: rms 1.0 mJy/beam; S/N ~50  
  > "have an rms noise of 1.0 mJy/beam. SPT 0538$-$50 is detected with a S/N ratio of $\sim 50$" (2.1.2 ALMA)
- time on source: 60 s  
  > "for a total on-source integration time of 60 seconds" (2.1.2 ALMA)
- observing dates: 2011 November 16  
  > "on 2011 November 16 for a total on-source integration time of 60 seconds" (2.1.2 ALMA)
- pi or archival as stated: Cycle 0, PI D. Marrone; previously published by the group  
  > "(2011.0.00958.S; PI: D. Marrone)" (2.1.2 ALMA)
- Line: 12CO 7-6 (SMA) (806.7 GHz)
- Line: [C I] 3P2-3P1 (SMA) (809.3 GHz)
- Line: 12CO 1-0 (ATCA) (115.3 GHz)
- Other facility **SMA**: CO(7-6) and [C I](2-1) line fluxes  
  > "SPT 0538$-$50 was observed by the Submillimeter Array (SMA) in the compact configuration on 2010 November 9 and 27." (2.2.2 SMA)
- Other facility **Herschel PACS/SPIRE**: far-IR photometry and SPIRE-FTS line limits  
  > "Data were recorded simultaneously at 100 and 160 $\mu$m." (2.1.5 Herschel)
- Other facility **HST WFC3**: high-resolution lens model  
  > "We use the F110W and F160W filters, the reddest high-throughput filters available." (2.1.8 HST WFC3-IR)
- Other facility **Spitzer IRAC**: 3.6 and 4.5 micron photometry  
  > "SPT 0538$-$50 was also observed at 3.6$\mu$m and $4.5\mu$m by the Infrared Array Camera" (2.1.6 Spitzer IRAC)
- Other facility **APEX Z-Spec**: redshift and high-J CO  
  > "Observations of SPT 0538-50 were obtained from APEX on 3 and 6 November 2010 with a total of 352 minutes on-source" (2.2.1 Z-Spec)
- Other facility **ATCA**: CO(1-0) and 35 GHz continuum  
  > "was well detected in both $^{12}$CO(1$\to$0)and the 35 GHz continuum" (2.1.3 ATCA)
- External data: ALMA lens model, magnification mu=21±4  
  > "SPT 0538$-$50 was modeled in detail by (cite: hezaveh13), based on our Cycle 0 ALMA Band 7 imaging." (3.3 Lens Model) [from (cite: hezaveh13)]
- External data: CO(1-0) flux and luminosity from ATCA  
  > "They report a de-lensed[^1] $^{12}$CO(1$\to$0) flux of $I_{CO(1-0)} = 1.20 \pm 0.20$ Jy km s$^{-1}$" (5.2.1 Molecular gas properties) [from (cite: aravena13)]
- External data: APEX SABOCA/LABOCA fluxes  
  > "S$_{350\mu m} = 336 \pm 88$ mJy, and S$_{870\mu m} = 125 \pm 7$ mJy" (2.1.4 APEX) [from (cite: greve12)]

## Processing

### Calibration

- pipeline or manual: _not stated_
- casa version: _not stated_
- pipeline version: _not stated_
- archive products used as is: _not stated_
- flux calibrator: Callisto (flux); J0538-440 bandpass; J0519-4546 gain  
  > "Absolute flux calibration was determined using observations of Callisto." (2.1.2 ALMA)
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
- smoothing: _not stated_
- final beam: _not stated_
- final rms: _not stated_

### Inherited from earlier work

- ALMA observation and processing details  
  > "The ALMA observations are described in (cite: hezaveh13) – here we provide a summary." (2.1.2 ALMA) [from (cite: hezaveh13)]
- Lens modeling technique  
  > "Details of the modeling technique can be found in that work." (3.3 Lens Model) [from (cite: hezaveh13)]

### Not stated but needed to reproduce (our reading)

- ALMA imaging parameters (weighting, cell, CLEAN settings)
- CASA version and calibration details
- lens model parameter files and source-plane priors
- CIGALE module configuration and parameter grid
- alpha_CO-based M(H2) calculation details
- SMA continuum-subtraction and line extraction specifics

## Analysis recipe

1. **Model lens galaxy in HST**: GALFIT fit of lens plus nine neighbors, three-component model  
  > "A three-component model, including a central point source, provided a superior fit, with physically-plausible parameters for each component and little residual structure." (4.2.1 Modelling the foreground lens)
   - software: GALFIT
   - fitting: _not stated_
   - validation: No DSFG trace in HST residuals  
  > "We see no trace of the DSFG (the structure seen by ALMA) in these residuals" (4.2.1 Modelling the foreground lens)
2. **De-blend IRAC photometry**: Convolve HST lens model with IRAC PSF, normalize with chi2 fit including dummy ring at 1.8'', subtract, aperture photometry  
  > "We varied the normalization of each component separately, using simultaneous $\chi^2$ fitting to find the optimum values, determined by comparing to the true IRAC image." (4.2.2 De-blending)
   - parameter: 4'' radius aperture  
  > "extracting the flux within a circular aperture of radius 4$''$" (4.2.2 De-blending)
   - fitting: chi2 minimization  
  > "We varied the normalization of each component separately, using simultaneous $\chi^2$ fitting to find the optimum values, determined by comparing to the true IRAC image." (Analysis, De-blending the source/lens emission)
   - validation: Ring residuals recovered with cruder normalization methods  
  > "ring-shaped residuals spatially matching the ALMA submm emission are not an artefact" (4.2.2 De-blending)
3. **De-lens and fit SED**: CIGALE fit with fixed ages 2 Gyr/20 Myr, solar metallicity, burst fraction 0.3  
  > "The fit was achieved assuming a solar metallicity, an old stellar population with a mean age of 2 Gyr, and a young stellar population with a mean age of 20 Myr" (4.4 SED fitting to IR data)
   - software: CIGALE
   - assumption: mu = 21±4; Kroupa IMF  
  > "results in a large magnification factor, $\mu = 21 \pm 4$" (3.3 Lens Model)
   - fitting: _not stated_
   - validation: Compared with greybody IR luminosity of greve12  
  > "These values are in line with those calculated by fitting a simple greybody to the far-IR points alone" (4.4 SED fitting to IR data)
4. **Derive molecular gas mass and excitation**: M(H2) from CO(1-0) with alpha_CO=0.8; L'CO(7-6)/L'CO(1-0) ratio  
  > "the standard value for starburst galaxies, which we adopt here, is $\alpha_{CO} = 0.8$" (5.2.1 Molecular gas properties)
   - assumption: alpha_CO = 0.8  
  > "the standard value for starburst galaxies, which we adopt here, is $\alpha_{CO} = 0.8$ M$_{\ensuremath{\odot}}$ (K km s$^{-1}$ pc$^{2})^{-1}$" (Physical Properties, Molecular gas properties (footnote))
   - fitting: _not stated_
   - validation: _not stated_

## Software

- **MIRIAD** : SMA data reduction  
  > "The SMA data were reduced using the MIRIAD software package (cite: sault95)." (2.2.2 SMA)
- **GALFIT** 3: lens galaxy modelling  
  > "we chose the fitting code GALFIT 3 (cite: peng10)" (4.2.1 Modelling the foreground lens)
- **CIGALE** : SED fitting  
  > "We use the galaxy SED fitting code CIGALE ((cite: burgarella05); (cite: noll09)) to fit the near- and far-IR photometric data." (4.4 SED fitting to IR data)
- **HIPE** v9.0: SPIRE reduction  
  > "HIPE v9.0" (2.1.5 Herschel)

## Numeric results

| quantity | value | uncertainty | units | step | quote |
|---|---|---|---|---|---|
| Magnification | 21 | ±4 | dimensionless | 0 | results in a large magnification factor, $\mu = 21 \pm 4$ |
| L_IR (8-1000 um) | 3.4e12 | ±0.3e12 | Lsun | 3 | $(3.4 \pm 0.3) \times 10^{12}$ L$_{\ensuremath{\odot}}$ |
| SFR | 760 | ±100 | Msun/yr | 3 | star formation rate of $760 \pm 100$ M$_{\ensuremath{\odot}}$/yr |
| Stellar mass | 3.3e10 | ±1.5e10 | Msun | 3 | stellar mass of $(3.3 \pm 1.5) \times10^{10} \; {\rm M}_{\ensuremath{\odot}}$ |
| Molecular gas mass | 1.7e10 | ±0.5e10 | Msun | 4 | molecular gas mass of $1.7 \pm 0.5 \times 10^{10}$ M$_{\ensuremath{\odot}}$ |
| L'CO(7-6)/L'CO(1-0) | 0.44 | ±0.08 | dimensionless | 4 | We find a ratio of $L'_{CO(7-6)} / L'_{CO(1-0)} = 0.44 \pm 0.08$ |
| Sigma_SFR compact | 630 | ±240 | Msun/yr/kpc^2 | 3 | $\Sigma_{SFR} = 630 \pm 240$ M$_{\ensuremath{\odot}}$ yr$^{-1}$ kpc$^{-2}$ |
| SMA CO(7-6) flux | 26.6 | ±4.5 | Jy km/s | 0 | $S_{CO(7-6)} = 26.6 \pm 4.5$ Jy km s$^{-1}$ |

## Qualitative findings

- Compact, merger-driven star formation similar to local starbursts; double-peaked lines suggest merger  
  > "we are witnessing compact, merger-driven star formation in SPT 0538$-$50, similar to local starburst galaxies" (abstract)

## Claim tuples

- H: Is SPT 0538-50 a compact merger-driven starburst? | E: Lens-model source sizes, SFR density, sSFR, line asymmetry | R: Sigma_SFR 630 for compact component; sSFR ~25 Gyr^-1; asymmetric CO/CI lines | F: Consistent with major merger starburst | **supported**
- H: Is the ISM highly excited? | E: CO(7-6)/CO(1-0) luminosity ratio | R: 0.44 vs 0.12 Eyelash and 0.18 DSFG average | F: High excitation, but cause (starburst, AGN, differential lensing) is uncertain | **partially**

## Reasoning

- Why this data: _not stated_
- Why this method: _not stated_
- Alternative: Single-component source model rejected (>6 sigma residuals)  
  > "Fits using just a single component model in the source plane resulted in a significant ($>6 \sigma$) residual structure" (3.3 Lens Model)
- How they decided it was enough: _not stated_
- Limitation (authors): No high-resolution kinematics; firm conclusions on source structure difficult  
  > "in the absence of high-resolution kinematic observations it is difficult to draw firm conclusions about the source structure" (5.1 Source Structure)
- Caveat (inferred, ours): Gaussian source components oversimplify
- Caveat (inferred, ours): Differential lensing may bias the SLED
- Caveat (inferred, ours): Only 2 IRAC points constrain the stellar mass
- Caveat (inferred, ours): Low-J CO is poorly sampled

## Reproducibility

- Data public (paper): _not stated_
- Products in archive: _not stated_
- Missing: lens model outputs
- Missing: CIGALE configuration
- Missing: HST/IRAC reduction details
- Data volume (inferred): Small ALMA Cycle 0 dataset (~ few GB)
- Score (inferred): 3/5, ALMA minor, with the lens model inherited and several multi-wavelength steps loosely described.
- Rediscovery candidate: no, ALMA role is minor and the analysis depends on non-ALMA data and an inherited lens model.

## Links

- Method: (cite: hezaveh13) (ALMA observation and lens model)
- Companion: (cite: aravena13) (ATCA CO(1-0))
- Companion: (cite: greve12) (APEX photometry)
- Related: South Pole Telescope survey

## Checks

```json
{
 "quotes": 60,
 "quotes_ok": 60,
 "quote_pass_rate": 1.0,
 "quotes_too_long": 0,
 "unsupported_facts": 0,
 "project_codes": 1,
 "codes_not_in_text": [],
 "codes_not_in_obscore": [],
 "obscore_codes_not_in_card": [
  "2011.0.00957.S"
 ],
 "codes_printed_but_missing": [],
 "numeric_results": 8,
 "numeric_problems": 0,
 "fill": {
  "facts": 76,
  "stated": 42,
  "rate": 0.553
 },
 "evidence_ok": true
}
```
