# High-velocity extended molecular outflow in the star-formation dominated luminous infrared galaxy ESO 320-G030

`2016A&A...594A..81P` | Astronomy and Astrophysics 2016 | first author: Pereira-Santaella, M. | arXiv: 1607.03674 | DOI: 10.1051/0004-6361/201628875

Card schema 1.0 | model claude-sonnet-5-5 | depth full | type observational_alma_primary

## Science

- Fields: nearby_galaxies
- Question: Characterize the resolved massive molecular outflow in the star-formation dominated LIRG ESO 320-G030 and establish the nature of its obscured nucleus that drives it  
  > "The main goals of this work are: characterize the resolved massive molecular outflow detected in this object and establish the nature of the extremely obscured nucleus which produces the massive molecular outflow." (Conclusions)
- Target **ESO 320-G030 (IRAS F11506-3851)**: coordinates _not stated_; z/distance d = 48 Mpc  
  > "local ($d=48$ Mpc; scale of 240 pc arcsec$^{-1}$) LIRG ESO 320-G030 ($\log L_{\rm IR}\slash \hbox{$L_{\rm \odot}$}= 11.3$; also known as IRAS F11506-3851)" (Introduction); distance from _not stated_

## Data provenance

- ALMA projects: 2013.1.00271.S
- bands: Band 6 (~1.3 mm)  
  > "Band 6 ALMA observations of ESO 320-G030 were obtained on 8 December 2014 and 18 July 2015" (2.1 12CO(2–1) ALMA data)
- frequencies and spectral setup: Two 1.875 GHz spectral windows at CO(2–1) (228.2 GHz) and CS(5–4) (242.4 GHz), 0.49 MHz channels; continuum windows at 230.4 and 245.2 GHz  
  > "Two spectral windows of 1.875 GHz bandwidth (0.49 MHz $\sim$ 0.6 km/s channels) were centered at the sky frequencies of $^{12}$CO(2–1) (228.2 GHz) and CS(5–4) (242.4 GHz)." (2.1 12CO(2–1) ALMA data)
- continuum bandwidth: _not stated_
- arrays: _not stated_
- configurations: compact (35 antennas) and extended (39 antennas)  
  > "using compact and extended array configurations with 35 and 39 antennas, respectively" (2.1 12CO(2–1) ALMA data)
- baselines: extended 15.1 m–1.6 km; compact 15.0–348 m  
  > "The extended configuration had baselines between 15.1 m and 1.6 km while for the compact configuration the baselines ranged between 15.0 m and 348 m." (2.1 12CO(2–1) ALMA data)
- angular resolution: 0.25"x0.23" (~60x55 pc), PA 89 deg  
  > "which provided a beam with a full-width half-maximum (FWHM) of 0.25$''$$\times$0.23$''$ ($\sim$60 pc$\times$55 pc) with a position angle (PA) of 89$^\circ$" (2.1 12CO(2–1) ALMA data)
- max recoverable scale: ~10 arcsec  
  > "For these configurations the maximum recoverable scales are $\sim$10$''$." (2.1 12CO(2–1) ALMA data)
- sensitivity: ~1 mJy/beam per 4 MHz channel; ~100 uJy/beam continuum  
  > "The achieved 1$\sigma$ sensitivity is $\sim$1 mJy beam$^{-1}$ in the CO(2–1) cube for the 4 MHz channels and $\sim$100 $\mu$Jy beam$^{-1}$ in the continuum images." (2.1 12CO(2–1) ALMA data)
- time on source: 8 and 17 min  
  > "On-source integration times were 8 and 17 min, respectively." (2.1 12CO(2–1) ALMA data)
- observing dates: 8 December 2014 and 18 July 2015  
  > "Band 6 ALMA observations of ESO 320-G030 were obtained on 8 December 2014 and 18 July 2015" (2.1 12CO(2–1) ALMA data)
- pi or archival as stated: PI: L. Colina  
  > "as part of the project 2013.1.00271.S (PI: L. Colina)" (2.1 12CO(2–1) ALMA data)
- Line: 12CO J=2-1 (not stated)
- Other facility **HST NICMOS/ACS**: Paα, F160W, F814W and FR656N images for morphology, SFR and extinction  
  > "We used these images to map the global morphology of ESO 320-G030." (2.2.1 Optical and near-IR HST imaging)
- Other facility **VLT/SINFONI**: near-IR IFS: Brγ/Brδ extinction, H2 1-0 S(1) hot gas, [Fe II]  
  > "the H$_2$ 1–0 S(1) 2.12 $\mu$m transition to trace the presence of hot molecular gas" (2.2.2 Near-IR VLT/SINFONI IFS)
- Other facility **Herschel PACS/SPIRE**: 70–500 um far-IR photometry for SED  
  > "We downloaded the PACS (cite: Poglitsch2010PACS) 70, 100, and 160 $\mu$m images as well as the SPIRE (cite: Griffin2010SPIRE) 250, 350, and 500 $\mu$m images." (2.2.3 Far-IR Herschel imaging)
- Other facility **ATCA**: 36 GHz flux (private communication)  
  > "This galaxy was recently observed with the Australia Telescope Compact Array (ATCA) at 36 GHz (B. Emonts 2016, private communication)" (6.1 Spectral energy distribution)
- External data: CO(1–0) flux of 180 Jy km/s (SEST)  
  > "A CO(1–0) flux of 180 Jy km s$^{-1}$ was reported by (cite: Mirabel1990) using the 15 m SEST telescope" (2.1 12CO(2–1) ALMA data) [from (cite: Mirabel1990)]
- External data: VLA radio fluxes and Spitzer MIPS 24um flux in SED tables  
  > "In addition, to the radio and IR data already published, we measured the ALMA continuum fluxes at 230 and 242 GHz" (6.1 Spectral energy distribution) [from not stated]
- External data: Neutral atomic outflow mass 10^8.5±0.9 Msun from NaD  
  > "The derived neutral atomic gas mass of the outflow is 10$^{8.5\pm0.9}$ $M_{\rm \odot}$." (5.2 Hot molecular, ionized, and neutral atomic gas) [from (cite: Cazzoli2014)]

## Processing

### Calibration

- pipeline or manual: Standard ALMA reduction with CASA  
  > "The two datasets were calibrated using the standard ALMA reduction software CASA (v4.2.2; (cite: McMullin2007))." (2.1 12CO(2–1) ALMA data)
- casa version: CASA 4.2.2  
  > "CASA (v4.2.2; (cite: McMullin2007))" (2.1 12CO(2–1) ALMA data)
- pipeline version: _not stated_
- archive products used as is: _not stated_
- flux calibrator: J1147-3812 (0.817 Jy at 236.5 GHz) for extended; Ganymede (Butler-JPL-Horizons 2012) for compact  
  > "we used J1147-3812, assuming a flux density of 0.817 Jy at 236.5 GHz, and Ganymede, using the Butler-JPL-Horizons 2012 model, for the extended and compact configurations, respectively" (2.1 12CO(2–1) ALMA data)
- flux scale uncertainty: about 15%  
  > "is 640 Jy km s$^{-1}$ with a flux calibration uncertainty about 15%" (2.1 12CO(2–1) ALMA data)
- self calibration: _not stated_

### Imaging

- task: _not stated_
- deconvolver: _not stated_
- weighting robust: Briggs, robust = 0.5  
  > "we used the Briggs weighting with a robustness parameter of 0.5" (2.1 12CO(2–1) ALMA data)
- uv taper: _not stated_
- cell size: 0.06 arcsec  
  > "we used 4 MHz channels ($\sim$5 km s$^{-1}$) to increase the signal-to-noise ratio and 256$\times$256 pixels of 0.06$''$" (2.1 12CO(2–1) ALMA data)
- image size: 256x256 pixels  
  > "256$\times$256 pixels of 0.06$''$" (2.1 12CO(2–1) ALMA data)
- masking: mask from observed CO(2–1) emission in each channel  
  > "A mask derived from the observed CO(2–1) emission in each channel was used during the clean process." (2.1 12CO(2–1) ALMA data)
- multiscale scales: _not stated_
- continuum subtraction: constant fit to line-free channels, subtracted in uv plane  
  > "the continuum was fitted with a constant using the line free channels and subtracted in the $uv$ plane" (2.1 12CO(2–1) ALMA data)
- line free channels: _not stated_
- primary beam correction: applied, FWHM=27 arcsec  
  > "We applied the primary beam (FWHM=27$''$) correction to the data." (2.1 12CO(2–1) ALMA data)
- array combination: visibilities converted to LSRK and combined in uv  
  > "The $uv$ visibilities of each observation were converted to a common frequency reference frame (kinematic local standard of rest; LSRK) and then combined." (2.1 12CO(2–1) ALMA data)
- smoothing: _not stated_
- final beam: 0.25"x0.23", PA 89 deg  
  > "0.25$''$$\times$0.23$''$ ($\sim$60 pc$\times$55 pc) with a position angle (PA) of 89$^\circ$" (2.1 12CO(2–1) ALMA data)
- final rms: ~1 mJy/beam (4 MHz channels)  
  > "$\sim$1 mJy beam$^{-1}$ in the CO(2–1) cube for the 4 MHz channels" (2.1 12CO(2–1) ALMA data)

### Inherited from earlier work

- Herschel data reduction details  
  > "More details on the data reduction can be found in (cite: Pereira2015not)." (2.2.3 Far-IR Herschel imaging) [from (cite: Pereira2015not)]
- Far-IR gray-body fit and dust mass method  
  > "Following (cite: Kovacs2010), we fitted the far-IR emission between 70 and 500 $\mu$m using a single temperature gray body" (6.1.2 Far-IR continuum) [from (cite: Kovacs2010)]
- SINFONI observations analyzed previously  
  > "These observations have been analyzed by (cite: Piqueras2012; Piqueras2016) and (cite: Cazzoli2014)." (2.2.2 Near-IR VLT/SINFONI IFS) [from (cite: Piqueras2012; Piqueras2016; Cazzoli2014)]
- Galactic CO-to-H2 factor appropriate for SF regions in LIRGs  
  > "using the Galactic CO-to-H$_2$ conversion factor which is appropriate for SF regions in LIRGs (cite: Pereira2016)" (6.2 Nuclear and circumnuclear star-formation) [from (cite: Pereira2016)]

### Not stated but needed to reproduce (our reading)

- Line-free channel ranges for continuum subtraction
- Clean threshold, number of iterations, deconvolver
- Region definitions (apertures) of outflow clumps A–G and how fluxes/FWHM were extracted
- Velocity ranges used for channel integration of each clump
- Details of the kinematic model fit (algorithm, uncertainties)
- Phase/bandpass calibrators and any self-calibration
- Exact SINFONI H2 mass calculation (temperature, thermalization)
- Whether the pipeline or manual scripts were used for calibration

## Analysis recipe

1. **Calibrate and image CO(2-1) cube and continuum**: CASA calibration, uv combination of two configs, uv continuum subtraction, Briggs clean with mask  
  > "For the cleaning of both the CO(2–1) and continuum data, we used the Briggs weighting with a robustness parameter of 0.5" (2.1 12CO(2–1) ALMA data)
   - software: CASA
   - parameter: 4 MHz channels (~5 km/s), 0.06" pixels, robust 0.5  
  > "we used 4 MHz channels ($\sim$5 km s$^{-1}$) to increase the signal-to-noise ratio and 256$\times$256 pixels of 0.06$''$" (2.1 12CO(2–1) ALMA data)
   - fitting: _not stated_
   - validation: Compared total CO(2-1) flux with expected from SEST CO(1-0) assuming r21=0.9  
  > "this similarity suggests that we recover the majority of the CO(2–1) flux combining both the compact and the extended ALMA array configurations" (2.1 12CO(2–1) ALMA data)
2. **Model the rotating-disk velocity field**: Pixel-wise Gaussian fit to CO profiles, reject poor fits (reduced chi2>1.4), fit simple kinematic model to first-moment map  
  > "we fitted the CO(2–1) profiles pixel by pixel using a Gaussian and rejected all those pixels where the quality of the fit was poor (reduced $\chi^2>1.4$)" (4 Global kinematics)
   - parameter: inclination fixed at 43 deg; other parameters free  
  > "all the parameters were left free to vary, except the inclination that was fixed at the value derived from the elliptical isophote fitting (43$^\circ$; see Section [3]" (4 Global kinematics)
   - assumption: v = Omega(r) cos(theta-theta0) sin i + vsys  
  > "v(r,\theta) = \Omega(r)\times \cos(\theta - \theta_0)\times \sin i + v_{\rm sys}" (4 Global kinematics)
   - fitting: _not stated_
   - validation: Residual standard deviation 14 km/s  
  > "The residuals standard deviation is 14 km s$^{-1}$" (4 Global kinematics)
3. **Identify outflow clumps**: Find regions with secondary CO(2-1) emission offset >200 km/s from modeled velocity  
  > "we identified some regions with secondary CO(2–1) emission separated by $>$200 km s$^{-1}$ from the local modeled velocity" (5 Resolved molecular outflow)
   - assumption: Outflow perpendicular to disk for deprojection  
  > "we assume that the outflow is perpendicular to the galaxy disk when we calculate the deprojected distances and velocities of the outflow regions" (5.1 Physical properties of the clumps)
   - fitting: _not stated_
   - validation: Compared with dust lane in HST F814W/F160W ratio; excluded two regions along major axis  
  > "We excluded them from the analysis because the rotation and high velocity dispersion of the gas in the inner 400 pc" (5 Resolved molecular outflow)
4. **Derive clump masses, energies and dynamical times**: Molecular masses from CO(2-1) flux via Solomon & Vanden Bout Eqs. 3,4; kinetic energy 1/2 M (v sec i)^2; momentum M v sec i  
  > "The molecular gas masses were calculated using Equations 3 and 4 of (cite: Solomon2005) which account for the He mass." (5.1 Physical properties of the clumps)
   - assumption: ULIRG-like alpha_CO ~0.78 Msun (K km/s pc2)^-1 and r21=0.9  
  > "we used the ULIRG-like factor ($\alpha_{\rm CO}\sim0.78$ $M_{\rm \odot}$ (K km s$^{-1}$ pc$^{-2}$)$^{-1}$)" (5.1 Physical properties of the clumps)
   - fitting: _not stated_
   - validation: _not stated_
5. **Nuclear SED, SFR and SN rate**: Gray-body far-IR fit, radio power-law fit, Brγ and IR-luminosity SFRs, SN rates from radio and [Fe II]  
  > "The best fit parameters are $T=49\pm2$ K, $\tau_{350\mu m}=0.30\pm0.04$, and $\Omega=(2.4\pm0.3)\times 10^{-11}$ sr." (6.1.2 Far-IR continuum)
   - parameter: beta=1.8, kappa350=1.92 cm2/g, Te=10000 K  
  > "with $\beta=1.8$ (cite: Planck2011)" (6.1.2 Far-IR continuum)
   - fitting: _not stated_
   - validation: Total nuclear LIR agrees with IRAS-derived value  
  > "This value is in very good agreement with the 8–1000 $\mu$m IR luminosity derived using the *IRAS* fluxes" (6.1.2 Far-IR continuum)
6. **Energetics of outflow vs SNe**: Compare outflow kinetic energy and momentum with SN output (1e51 erg/SN, 2.8e4 Msun km/s per SN)  
  > "The radial momentum per SN is 2.8$\times$10$^4$ $M_{\rm \odot}$ km s$^{-1}$ (cite: Walch2015)" (7.3 Power source and energetics)
   - fitting: _not stated_
   - validation: _not stated_

## Software

- **CASA** 4.2.2: ALMA calibration and imaging  
  > "CASA (v4.2.2; (cite: McMullin2007))" (2.1 12CO(2–1) ALMA data)
- **HIPE** : Herschel data processing  
  > "We processed the data using the standard *Herschel* pipeline environment software (HIPE)" (2.2.3 Far-IR Herschel imaging)
- **Scanamorphos** : Herschel map making  
  > "created the maps using Scanamorphos (cite: Roussel2012)" (2.2.3 Far-IR Herschel imaging)
- **pPXF** : Stellar continuum subtraction in SINFONI K-band  
  > "we subtracted the stellar continuum spaxel by spaxel using the penalized pixel-fitting method (cite: Cappellari2004)" (5.2 Hot molecular, ionized, and neutral atomic gas)

## Numeric results

| quantity | value | uncertainty | units | step | quote |
|---|---|---|---|---|---|
| Integrated CO(2-1) flux in ALMA FoV | 640 | 15% | Jy km/s | 1 | is 640 Jy km s$^{-1}$ with a flux calibration uncertainty about 15% |
| Kinematic major axis PA | 133 | ±2 | deg | 2 | the PA of the major kinematic axis (133$\pm$2$^\circ$) and the systemic velocity (3080$\pm$4 km s$^{-1}$ in the LSRK frame) |
| Systemic velocity | 3080 | ±4 | km/s | 2 | the systemic velocity (3080$\pm$4 km s$^{-1}$ in the LSRK frame) |
| Rotation curve amplitude (inclination corrected) | ~270 | not stated | km/s | 2 | the amplitude of the rotation curve corrected for inclination is $\sim$270 km s$^{-1}$ |
| Total molecular mass in outflow clumps | 10^6.8 | not stated | Msun | 4 | We measured a molecular gas mass of 10$^{6.8}$ $M_{\rm \odot}$ in the outflow clumps. |
| Mean molecular mass outflow rate | 1.7 | not stated | Msun/yr | 4 | the molecular mass outflow rate is $\dot{M}_{\rm out}=$1.7 $M_{\rm \odot}$ yr$^{-1}$ (assuming a 3 Myr dynamical time) |
| Mass loading factor | ~0.1 (0.5 with Galactic alpha_CO) | not stated | dimensionless | 4 | This corresponds to a loading factor ($\dot{M}_{\rm out}\slash {\rm SFR}$) $\sim$0.1 (or 0.5 using the Galactic CO conversion factor). |
| Hot-to-cold molecular gas ratio | 7e-5 | not stated | dimensionless | 4 | The ratio of hot-to-cold molecular gas is 7$\times$10$^{-5}$ |
| Dust temperature (gray body) | 49 | ±2 | K | 5 | The best fit parameters are $T=49\pm2$ K |
| Radio spectral index | 0.7 | ±0.1 | dimensionless | 5 | The spectral index, $\alpha$, is 0.7$\pm$0.1 |
| Nuclear SFR | 15 | ±2 | Msun/yr | 5 | that is, 15$\pm$2 $M_{\rm \odot}$ yr$^{-1}$ |
| Nuclear extinction A_K | 4.6 | not stated | mag | 5 | This gives an extinction of $A_{\rm K} = 4.6$ mag |
| Nuclear molecular gas mass | 10^9.1 | not stated | Msun | 5 | corresponds to a molecular gas mass of 10$^{9.1}$ $M_{\rm \odot}$ |
| Nuclear depletion time | ~80 | not stated | Myr | 5 | The depletion time ($t_{\rm dep}=M_{\rm H_2}\slash {\rm SFR}$) of the nucleus is $\sim$80 Myr. |
| Outflow kinetic energy fraction of SN energy | ~2% | not stated | percent | 6 | the kinetic energy associated with this molecular outflow is $\sim$2% of the total available energy |
| Outflow momentum fraction of SN momentum | ~20% | not stated | percent | 6 | so about 20% of the momentum due to SNe is deposited in the outflowing molecular gas |

## Qualitative findings

- CO(2-1) in the outflow is clumpy along a dust lane, with blue- and red-shifted clumps roughly symmetric about the nucleus  
  > "the CO(2–1) emission is concentrated in few clumps along the lane" (5 Resolved molecular outflow)
- No evidence for an AGN in this galaxy  
  > "Therefore, there is no evidence for an AGN in this object." (6 Nature of the central source)

## Claim tuples

- H: Is there a resolved massive molecular outflow in ESO 320-G030? | E: Search for CO(2-1) emission deviating >200 km/s from a rotating-disk model | R: Seven clumps, sizes 60–150 pc, masses 10^5.5–10^6.4 Msun, velocities ~370–540 km/s, total 10^6.8 Msun | F: A ~2.5 kpc clumpy molecular outflow originates in the nucleus | **supported**
- H: Is the nucleus powered by star formation rather than an AGN? | E: Multiwavelength SED, radio spectral index, SFR and SN rates | R: alpha=0.7, nuclear SFR ~15 Msun/yr, no AGN indicators | F: Highly obscured intense star formation powers the nucleus | **supported**
- H: Can supernovae power the molecular outflow? | E: Compare outflow kinetic energy and momentum with SN output | R: ~2% of energy and ~20% of momentum | F: SNe can power the outflow | **supported**
- H: Does the outflow quench star formation or escape the galaxy? | E: Loading factor and comparison with escape velocity | R: Loading factor ~0.1–0.5; velocities below escape velocity 530 km/s | F: Quenching not efficient; gas likely returns to the disk | **supported**

## Reasoning

- Why this data: _not stated_
- Why this method: ULIRG-like CO conversion factor adopted since the factor for outflows is poorly known, giving lower limits  
  > "The CO-to-H$_2$ conversion factor for outflows is poorly known." (5.1 Physical properties of the clumps)
- Alternative: Blue/red regions could be coplanar non-circular (radial) motions, rejected since velocity is too high for density-wave-driven flows  
  > "the high velocity of this gas (comparable to the rotation curve half amplitude) is much higher than that expected for density-wave-driven gas flows" (5 Resolved molecular outflow)
- How they decided it was enough: _not stated_
- Limitation (authors): Factor ~5 systematic uncertainty in mass from alpha_CO; masses are lower limits  
  > "The uncertainty in the mass determination is dominated by the factor of $\sim$5 systematic uncertainty in the CO-to-H$_2$ conversion factor." (5.1 Physical properties of the clumps)
- Limitation (authors): Origin of outflowing molecular gas unclear from available data  
  > "is not clear from the available data" (Conclusions)
- Caveat (inferred, ours): Outflow geometry (perpendicular to disk) is assumed, affecting deprojected velocities and energies
- Caveat (inferred, ours): Clump identification relies on a simple disk model; bar non-circular motions could contaminate
- Caveat (inferred, ours): Hot H2 mass depends strongly on assumed extinction
- Caveat (inferred, ours): Mass loading rate relies on a single assumed dynamical time

## Reproducibility

- Data public (paper): ALMA project code given and data acknowledged; public status not explicitly stated  
  > "This paper makes use of the following ALMA data: ADS/JAO.ALMA#2013.1.00271.S." (Acknowledgements)
- Products in archive: _not stated_
- Missing: Clump region definitions and velocity windows
- Missing: Clean parameters and line-free channels
- Missing: Private ATCA 36 GHz flux
- Missing: SINFONI reduced cubes not public in paper
- Data volume (inferred): ~10-30 GB (two Band 6 execution blocks, raw)
- Score (inferred): 3/5, ALMA data identified and imaging parameters mostly given, but clump extraction details and some ancillary data are not reproducible from the text.
- Rediscovery candidate: no, Clump selection and ancillary (SINFONI, ATCA private) data make a full redo incomplete, though ALMA CO cube analysis is feasible.

## Links

- Method: (cite: Kovacs2010) (far-IR gray-body fit and dust mass)
- Method: (cite: Solomon2005) (CO luminosity to molecular mass)
- Companion: (cite: Pereira2016) (ALMA study of LIRG IC 4687 at similar resolution)
- Companion: (cite: Cazzoli2014) (neutral atomic outflow in the same galaxy)
- Companion: (cite: Piqueras2012) (SINFONI IFS of the galaxy)

## Checks

```json
{
 "quotes": 86,
 "quotes_ok": 86,
 "quote_pass_rate": 1.0,
 "quotes_too_long": 0,
 "unsupported_facts": 0,
 "project_codes": 1,
 "codes_not_in_text": [],
 "codes_not_in_obscore": [],
 "obscore_codes_not_in_card": [],
 "codes_printed_but_missing": [],
 "numeric_results": 16,
 "numeric_problems": 0,
 "fill": {
  "facts": 87,
  "stated": 63,
  "rate": 0.724
 },
 "evidence_ok": true
}
```
