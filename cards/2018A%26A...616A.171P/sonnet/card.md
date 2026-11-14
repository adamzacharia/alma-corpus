# Spatially resolved cold molecular outflows in ULIRGs

`2018A&A...616A.171P` | Astronomy and Astrophysics 2018 | first author: Pereira-Santaella, M. | arXiv: 1805.03667 | DOI: 10.1051/0004-6361/201833089

Card schema 1.0 | model claude-sonnet-5-5 | depth full | type observational_alma_primary

## Science

- Fields: nearby_galaxies
- Question: Are the cold molecular outflows in three local ULIRGs spatially resolved, what are their properties (mass, rate, energy, momentum), and what powers them and how do they affect star formation?  
  > "the cold molecular outflow phase is spatially resolved on scales of $\sim$500 pc. This provides a direct measurement of the outflow size" (1 Introduction)
- Target **IRAS 12112+0305**: coordinates SW 12h13m45.939s +2d48m39.10s; NE 12h13m46.056s +2d48m41.53s (ICRS)  
  > "| SW | 12h13m45.939s | 2d48m39.10s | 21167 |" (Table 1 (sample)); z/distance z=0.0731, d_L=330 Mpc  
  > "| 12112$+$0305 |  |  |  |  | 0.0731 | 330 | 1390 | 11.4 | 12.19 |" (Table 1 (sample)); distance from _not stated_
- Target **IRAS 14348-1447**: coordinates SW 14h37m38.280s -15d00m24.24s; NE 14h37m38.396s -15d00m21.29s (ICRS)  
  > "| SW | 14h37m38.280s | –15d00m24.24s | 23766 |" (Table 1 (sample)); z/distance z=0.0825, d_L=375 Mpc  
  > "| 14348$-$1447 |  |  |  |  | 0.0825 | 375 | 1554 | 11.6 | 12.27 |" (Table 1 (sample)); distance from _not stated_
- Target **IRAS 22491-1808**: coordinates E 22h51m49.348s -17d52m24.12s (ICRS)  
  > "| E | 22h51m49.348s | –17d52m24.12s | 22412 |" (Table 1 (sample)); z/distance z=0.0778, d_L=353 Mpc  
  > "| 22491$-$1808 |  |  |  |  | 0.0778 | 353 | 1469 | 11.5 | 12.03 |" (Table 1 (sample)); distance from cosmology H0=70, Om=0.3, OL=0.7  
  > "Throughout this article we assume the following cosmology: $H_{\rm 0} = 70$ km s$^{-1}$ Mpc$^{-1}$, $\Omega_{\rm m}=0.3$, and $\Omega_{\rm \Lambda}=0.7$." (Introduction)

## Data provenance

- ALMA projects: 2015.1.00263.S, 2016.1.00170.S
- bands: Band 6 (CO(2-1) 230.5 GHz and ~248 GHz continuum)  
  > "We obtained Band 6 ALMA CO(2–1) 230.5 GHz and continuum observations for these three local ULIRGs" (2.2 ALMA data)
- frequencies and spectral setup: Two 1.875 GHz spws on 12CO(2-1) and CS(5-4), plus continuum spw at ~248 GHz  
  > "Two spectral windows of 1.875 GHz bandwidth (0.976 MHz $\equiv\sim$1.3 km/s channels) were centered at the sky frequency of the $^{12}$CO(2–1) and CS(5–4) transitions" (2.2 ALMA data)
- continuum bandwidth: _not stated_
- arrays: _not stated_
- configurations: _not stated_
- baselines: 15-1100 m  
  > "The baseline lengths range between 15 and 1100 m" (2.2 ALMA data)
- angular resolution: ~0.3''-0.4'' (400-500 pc)  
  > "synthesized beam full-width at half-maximum (FWHM) of $\sim0.3\ensuremath{''}-0.4\ensuremath{''}$" (2.2 ALMA data)
- max recoverable scale: ~4''  
  > "maximum recoverable scale ($\sim4\ensuremath{''}$)" (2.2 ALMA data)
- sensitivity: CO(2-1) 310-450 uJy/beam per channel; continuum 30-45 uJy/beam  
  > "the 1$\sigma$ sensitivity is $\sim310-450$ $\mu$Jy beam$^{-1}$ per channel and $\sim30-45$ $\mu$Jy beam$^{-1}$ for the continuum images" (2.2 ALMA data)
- time on source: ~30-40 min per source, two scheduling blocks  
  > "The total on-source integration times per source were $\sim30-40$ min split into two scheduling blocks." (2.2 ALMA data)
- observing dates: June 2016 - May 2017  
  > "The observations were carried out between June 2016 and May 2017." (2.2 ALMA data)
- pi or archival as stated: PI: Pereira-Santaella (own proposals)  
  > "(PI: Pereira-Santaella)" (2.2 ALMA data)
- Line: 12CO J=2-1 (230.5 GHz)
- Other facility **HST/NICMOS**: F160W and F222M images used for comparison and alignment  
  > "We downloaded the near-IR *HST*/NICMOS F160W" (2.3 Near-IR HST imaging)
- Other facility **Spitzer and Herschel**: 24-500 um fluxes for L_IR SED fits  
  > "We fit a single temperature gray body model to the 24 $\mu$m to 500 $\mu$m fluxes from *Spitzer* and *Herschel*" (3.4.1 IR luminosity)
- External data: 1.49 and 8.44 GHz radio fluxes  
  > "we use the available interferometric radio (1.49 and 8.44 GHz) observations for these systems" (3.1.2 248 GHz continuum) [from (cite: Condon1990; Condon1991)]
- External data: Escape velocities at 2 kpc  
  > "We use the escape velocities at 2 kpc calculated by (cite: Emonts2017) for these systems" (3.3.2 Derived properties) [from (cite: Emonts2017)]
- External data: Hot H2 outflow velocities and masses from near-IR data  
  > "For the hot molecular phase, we have maps at higher angular resolution (cite: Emonts2017)." (4.4.1 Hot and cold molecular phase) [from (cite: Emonts2017)]
- External data: AGN luminosities, v/sigma ULIRG sample  
  > "(cite: GarciaMarin06) and (cite: Bellocchi2013) measured the v$\slash\sigma$ ratios in a sample of 25 ULIRGs" (3.2.1 Nuclear disks and molecular outflows) [from (cite: GarciaMarin06; Bellocchi2013)]

## Processing

### Calibration

- pipeline or manual: _not stated_
- casa version: CASA v4.7  
  > "The data were calibrated using the ALMA reduction software CASA (v4.7; (cite: McMullin2007))." (2.2 ALMA data)
- pipeline version: _not stated_
- archive products used as is: _not stated_
- flux calibrator: J1229+0203, J1517-2422, Pallas (Butler)  
  > "| 22491$-$1808 | 2016-06-21 | 213.92 | 29 | 4.0$''$ | 0.48$''$$\times$0.34$''$, –84$^\circ$ | Pallas     | Butler$^{d}$  | 450/46" (Table 3)
- flux scale uncertainty: about 10%  
  > "The absolute flux calibration uncertainty is about 10%." (Table 5 notes)
- self calibration: _not stated_

### Imaging

- task: _not stated_
- deconvolver: _not stated_
- weighting robust: Briggs, robust = 0.5  
  > "we used the Briggs weighting with a robustness parameter of 0.5" (2.2 ALMA data)
- uv taper: _not stated_
- cell size: 0.08''  
  > "300$\times$300 spatial pixels of 0.08$''$ and 220 spectral channels of 7.81 MHz" (2.2 ALMA data)
- image size: 300x300 pixels, 220 channels of 7.81 MHz (~10 km/s)  
  > "300$\times$300 spatial pixels of 0.08$''$ and 220 spectral channels of 7.81 MHz ($\sim10$ km/s)" (2.2 ALMA data)
- masking: _not stated_
- multiscale scales: _not stated_
- continuum subtraction: constant level from line-free channels, subtracted in uv plane  
  > "a constant continuum level was estimated using the line free channels and then subtracted in the $uv$ plane" (2.2 ALMA data)
- line free channels: _not stated_
- primary beam correction: applied, FWHM~20''  
  > "A primary beam correction (FWHM$\sim$20$''$) was applied to the data." (2.2 ALMA data)
- array combination: _not stated_
- smoothing: _not stated_
- final beam: 0.36x0.27, 0.32x0.26, 0.48x0.34 arcsec  
  > "0.36$''$$\times$0.27$''$, –82$^\circ$" (Table 3)
- final rms: _not stated_

### Inherited from earlier work

- Gray-body SED fitting for L_IR  
  > "following (cite: Pereira2016b)" (3.4.1 IR luminosity) [from (cite: Pereira2016b)]
- Centroid-per-channel method for nuclear kinematics  
  > "Similar to (cite: GarciaBurillo2015), we derive the centroid of the CO(2–1) emission in each velocity channel" (3.2.1 Nuclear disks and molecular outflows) [from (cite: GarciaBurillo2015)]
- alpha_CO and r21 values  
  > "a ratio between the CO(2–1) and CO(1–0) transitions, $r_{21}$, of 0.91 (cite: Bolatto2013)" (3.3.2 Derived properties) [from (cite: Bolatto2013)]
- SFR calibrations  
  > "we converted these nuclear IR luminosities into SFR using the (cite: Kennicutt2012) calibration" (3.4.1 IR luminosity) [from (cite: Kennicutt2012); (cite: Murphy2011)]

### Not stated but needed to reproduce (our reading)

- Line-free channel ranges for continuum subtraction
- Exact tclean parameters (niter, threshold, masks, deconvolver)
- Whether data were calibrated with the delivered pipeline or manual scripts
- Regions and criteria used to define high-velocity gas apertures and the two-Gaussian fit initial conditions
- Formulae for t_dep, P_out and L_out (only referenced to GarciaBurillo2015)
- Fitting method details for linear fits and arctan rotation curves
- SNe momentum and energy injection prescriptions
- Self-calibration not mentioned

## Analysis recipe

1. **Measure CO(2-1) integrated flux and size**: Integrate line flux over contiguous pixels with line peak >6 sigma; effective radius from half-flux area  
  > "selecting all the contiguous pixels where the CO(2–1) line peak is above 6$\sigma$" (3.1.1 Molecular gas)
   - software: CASA
   - parameter: R_eff = sqrt(A/pi)  
  > "$R_{\rm eff} = \sqrt{A/\pi}$" (3.1.1 Molecular gas)
   - fitting: _not stated_
   - validation: _not stated_
2. **Fit 248 GHz continuum in uv plane**: 2D circular Gaussian, plus delta function for two sources, fit to visibilities  
  > "First, we tried a 2D circular Gaussian model which provided a good fit for all the sources except two (I12112 NE and I22491 E)." (3.1.2 248 GHz continuum)
   - software: uvmultifit, CASA
   - fitting: simultaneous fit to visibility data  
  > "This library can simultaneously fit various models to the visibility data." (3.1.2 248 GHz continuum)
   - validation: Compared visibilities with best-fit models (Appendix)  
  > "compares the real part of the continuum visibilities for each source with the best fit model" (6 Continuum visibility fits)
3. **Non-thermal fraction at 248 GHz**: Power-law fit to 1.49 and 8.44 GHz fluxes extrapolated to 248 GHz  
  > "we fit a power-law to the 1.49 and 8.44 GHz fluxes and obtain spectral indexes between 0.42 and 0.72" (3.1.2 248 GHz continuum)
   - assumption: Radio and 248 GHz emission come from same regions  
  > "we assume that the radio and the 248 GHz emissions are produced in the same regions" (3.1.2 248 GHz continuum)
   - fitting: _not stated_
   - validation: _not stated_
4. **Disk kinematics, PA, systemic velocity and inclination**: Per-channel centroids; linear fit of low-velocity centroids for disk PA; arctan rotation curve; inclination from observed v/sigma vs intrinsic 1.5+/-0.6  
  > "we compare the observed dynamical ratios in each galaxy with this intrinsic ratio to estimate their inclinations ($15-40$$^\circ$)" (3.2.1 Nuclear disks and molecular outflows)
   - assumption: Mean ULIRG inclination 57 deg (sin i=0.79)  
  > "Assuming a mean inclination of 57$^\circ$($\sin i = 0.79$; see (cite: Law2009))" (3.2.1 Nuclear disks and molecular outflows)
   - fitting: arctan model; linear fit  
  > "fit an arctan model (e.g., (cite: Courteau1997)) to determine the curve semi-amplitude" (3.2.1 Nuclear disks and molecular outflows)
   - validation: Centroid astrometric accuracy ~25 mas (SNR>10)  
  > "The astrometric accuracy for the frequency and array configuration of these observations is $\sim$25 mas for channels with a SNR higher than 10." (3.2.1 Nuclear disks and molecular outflows)
5. **Outflow geometry and flux**: Centroid clusters of red/blue high-velocity gas give outflow PA and R_c; spectrum of region fit with two Gaussians, residual wings are outflow flux  
  > "We fitted a two Gaussian model to the CO(2–1) line profile. This model reproduces well the core of the observed line profile." (3.3.1 Observed properties)
   - assumption: Outflow perpendicular to disk  
  > "assuming that they are perpendicular to the rotating disk" (3.3.2 Derived properties)
   - fitting: two-Gaussian line profile  
  > "We fitted a two Gaussian model to the CO(2–1) line profile." (3.3.1 Observed properties: PA, size, flux, and velocity)
   - validation: Trailing spiral arms identify near/far disk side to confirm outflow rather than inflow  
  > "the blue-shifted high-velocity emission appears on the far side of the disk and the red-shifted emission on the near side. This is a clear signature of outflowing gas." (3.3.1 Observed properties)
6. **Outflow mass, rate, momentum, energy, escape fraction**: Mass from CO flux with alpha_CO; v and R deprojected by cos i and sin i; t_dyn=R/v; Mdot=M/t_dyn; escape from v>v_esc  
  > "we calculate the dynamical time as $t_{\rm dyn} = R_{\rm out}\slash {\rm v}_{\rm out}$" (3.3.2 Derived properties)
   - assumption: alpha_CO=0.78 Msun/(K km/s pc^2), r21=0.91; 0.4 dex uncertainty  
  > "we assume a ULIRG-like $\alpha_{\rm CO}$ conversion factor of 0.78 $M_{\rm \odot}$(K km s$^{-1}$ pc$^{-2}$)$^{-1}$" (3.3.2 Derived properties)
   - fitting: _not stated_
   - validation: _not stated_
7. **Nuclear SFR**: Gray-body L_IR, minus AGN, apportioned by 248 GHz thermal continuum, Kennicutt2012 SFR; cross-check with radio 1.4 GHz SFR (Murphy2011)  
  > "we estimated the rest-frame 1.4 GHz continuum and applied the (cite: Murphy2011) SFR calibration" (3.4.2 Radio continuum)
   - assumption: All L_IR produced in central 300-1000 pc; 248 GHz scales with L_IR  
  > "we assume that all the $L_{\rm IR}$ is produced in the central $300-1000$ pc" (3.4.1 IR luminosity)
   - fitting: single-temperature gray body  
  > "We fit a single temperature gray body model to the 24 $\mu$m to 500 $\mu$m fluxes from *Spitzer* and *Herschel*" (3.4.1 IR luminosity)
   - validation: IR and radio SFR agree within 0.2 dex on average  
  > "The average difference between the two estimates is 0.2 dex with a maximum of 0.4 dex." (3.4.2 Radio continuum)
8. **Outflow cycle duration and scaling relations**: Numerical integration of radial equations of motion with potential from v_esc; linear fits of eta-v, Pdot-SFR, L-SFR  
  > "Integrating these equations numerically, we can determine when $r$ becomes 0, and obtain an estimate of the outflow cycle duration." (4.2 Outflow effects on the star-formation)
   - assumption: Radial motion, no dynamical friction  
  > "assuming that the outflowing gas moves radially and that it is not affected by any dynamical friction" (4.2 Outflow effects on the star-formation)
   - fitting: linear fits  
  > "The best linear fit to the starbursts data is:" (4.3 Outflow launching mechanism in starbursts)
   - validation: _not stated_

## Software

- **CASA** 4.7: Calibration and imaging  
  > "The data were calibrated using the ALMA reduction software CASA (v4.7; (cite: McMullin2007))." (2.2 ALMA data)
- **uvmultifit** : Fitting continuum models to visibilities  
  > "we used the uvmultifit library (cite: MartiVidal2014) within CASA" (3.1.2 248 GHz continuum)

## Numeric results

| quantity | value | uncertainty | units | step | quote |
|---|---|---|---|---|---|
| Outflow mass range | (0.3-5)x10^8 | not stated | Msun | 6 | massive molecular outflows ($M_{\rm out}\sim(0.3-5)\times$10$^{8}$ $M_{\rm \odot}$) |
| Outflow rates | 12-400 | 0.4 dex | Msun/yr | 6 | the outflow rates between 12 and 400 $M_{\rm \odot}$ yr$^{-1}$ |
| Mass loading factor | 0.8-2 | not stated | dimensionless | 7 | the mass loading factors are 0.8 to $\sim$2 |
| Escape fraction | 15-30% | not stated | percent | 6 | obtain that $15-30$% of the high-velocity gas will escape to the intergalactic medium |
| Outflow cycle duration | 5-10 | not stated | Myr | 8 | we find cycle durations of $5-10$ Myr |
| eta-v slope | -0.3 | 0.2 | dimensionless | 8 | $\log\,\eta = (0.8 \pm 0.4) - (0.3 \pm 0.2) \log {\rm v_{out}} ({\rm km\,s^{-1}})$ |
| Mean hot-to-cold H2 mass ratio | 2.6e-5 | 1.0e-5 | dimensionless | 0 | The average hot-to-cold molecular gas mass ratio is (2.6$\pm$1.0)$\times$10$^{-5}$. |

## Qualitative findings

- High-velocity CO gas decoupled from disk rotation in 5 of 6 nuclei, consistent with outflows  
  > "we presented the detection of high-velocity gas in 5 out of 6 ULIRG nuclei" (3.3.1 Observed properties)

## Claim tuples

- H: Cold molecular outflows in ULIRGs can be spatially resolved on ~500 pc scales | E: ALMA CO(2-1) at 0.3-0.4'' with centroid analysis | R: Outflows resolved in 4 of 5 nuclei, R_c 0.1-0.24'' | F: Direct outflow sizes yield more accurate rates | **supported**
- H: Outflows are powered by star formation or AGN | E: Compare eta, energy, momentum, velocity, geometry with SNe expectations | R: All consistent with SF; IRAS 14348 SW possible AGN | F: Outflows compatible with SF-powered | **supported**
- H: Outflows quench nuclear star formation | E: Depletion time, escape fraction and return-time modelling | R: Depletion 15-80 Myr, 15-30% escape, return in 5-10 Myr | F: Delay but not quench star formation | **supported**
- H: Molecular outflows are momentum-driven (eta~v^-1) | E: Add new points to eta-v relation | R: Slope -0.3+/-0.2 | F: Shallower slope; may be explained by higher optical depth or SNe driving | **partially**

## Reasoning

- Why this data: _not stated_
- Why this method: _not stated_
- Alternative: Coplanar bar-like geometry for high-velocity gas rejected because of extreme radial velocities up to 400 km/s  
  > "because of the extremely high radial velocities implied by this geometry, up to 400 km s$^{-1}$, in the following, we only discuss the out-of plane outflow possibility." (3.2.1 Nuclear disks and molecular outflows)
- How they decided it was enough: _not stated_
- Limitation (authors): Uncertainties dominated by alpha_CO and outflow geometry; angular resolution too coarse for radial profiles  
  > "The uncertainties on the outflow rate, and the quantities derived from it, are dominated by the uncertainty in the value of the $\alpha_{\rm CO}$ conversion factor" (3.3.2 Derived properties)
- Caveat (inferred, ours): Outflow rate relies on t_dyn=R/v with a single R_c, sensitive to definitions
- Caveat (inferred, ours): Inclination from v/sigma has large errors (10-30 deg), propagating to deprojection
- Caveat (inferred, ours): Wing/core separation by two Gaussians is model dependent
- Caveat (inferred, ours): Possible missing extended flux not tested
- Caveat (inferred, ours): AGN contribution to outflow not excluded

## Reproducibility

- Data public (paper): _not stated_
- Products in archive: ALMA data from projects 2015.1.00263.S and 2016.1.00170.S  
  > "This paper makes use of the following ALMA data: ADS/JAO.ALMA#2015.1.00263.S, ADS/JAO.ALMA#2016.1.00170.S." (Acknowledgements)
- Missing: Line-free channels
- Missing: Cleaning masks and thresholds
- Missing: Aperture definitions for high-velocity gas
- Missing: Formulae for momentum and energy rates
- Missing: Data-release status/embargo
- Data volume (inferred): ~10-50 GB raw for 6 execution blocks
- Score (inferred): 3/5, Data are archival-accessible and main steps are described, but many imaging and extraction parameters are missing.
- Rediscovery candidate: no, Key recipe details (apertures, line-free channels, formulae) are not specified enough.

## Links

- Method: (cite: MartiVidal2014) (uvmultifit used for visibility fits)
- Method: (cite: GarciaBurillo2015) (centroid and outflow property method)
- Companion: (cite: Emonts2017) (near-IR H2 outflow data for same galaxies)

## Checks

```json
{
 "quotes": 81,
 "quotes_ok": 81,
 "quote_pass_rate": 1.0,
 "quotes_too_long": 0,
 "unsupported_facts": 0,
 "project_codes": 2,
 "codes_not_in_text": [],
 "codes_not_in_obscore": [],
 "obscore_codes_not_in_card": [],
 "codes_printed_but_missing": [],
 "numeric_results": 7,
 "numeric_problems": 0,
 "fill": {
  "facts": 95,
  "stated": 66,
  "rate": 0.695
 },
 "evidence_ok": true
}
```
