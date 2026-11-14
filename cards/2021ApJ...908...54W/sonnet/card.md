# ALMA Measures Rapidly Depleted Molecular Gas Reservoirs in Massive Quiescent Galaxies at z ∼ 1.5

`2021ApJ...908...54W` | The Astrophysical Journal 2021 | first author: Williams, Christina C. | arXiv: 2012.01433 | DOI: 10.3847/1538-4357/abcbf6

Card schema 1.0 | model claude-sonnet-5-5 | depth full | type observational_alma_primary

## Science

- Fields: nearby_galaxies, high_z_galaxies
- Question: How much molecular gas (CO(2–1)) do massive quiescent galaxies at z~1.5 retain, and what does this imply for quenching, depletion times and models?  
  > "we conduct the first survey targeting molecular gas traced by CO(2–1) in a sample of quiescent galaxies above $z>1$." (1 Introduction)
- Target **Six massive quiescent galaxies in COSMOS (22260, 20866, 34879, 34265, 21434, 307881)**: coordinates e.g. 22260: RA 149.818229, Dec 2.561610 (Table 1 lists all six)  
  > "| 22260 | 149.818229 | 2.561610 | 1.240 |" (Table 1); "Our final sample includes five galaxies in the COSMOS field" (2 Sample and Data); z/distance z_spec 1.240-1.582 (Table 1)  
  > "| 22260 | 149.818229 | 2.561610 | 1.240 |" (Table 1); "Our final sample includes five galaxies in the COSMOS field" (2 Sample and Data); distance from spectroscopic redshifts from Keck/LRIS and Subaru/MOIRCS literature (Bezanson2013; vandeSande2013; Belli2014a; Belli2015; Onodera2012)  
  > "| 22260 | 149.818229 | 2.561610 | 1.240 |" (Table 1); "Our final sample includes five galaxies in the COSMOS field" (2 Sample and Data)

## Data provenance

- ALMA projects: 2018.1.01739.S, 2015.1.00853.S
- bands: Band 3 (3 mm)  
  > "using the Band 3 (3 mm) receivers" (2.2 ALMA observations)
- frequencies and spectral setup: CO(2–1) in a 1.875 GHz spectral window (~5500 km/s), ≈89.3–102.9 GHz; three additional continuum windows  
  > "The correlator was configured to center the CO(2–1) line within a spectral window of 1.875 GHz width" (2.2 ALMA observations); "Three additional spectral windows were used for continuum observations." (2.2 ALMA observations)
- continuum bandwidth: _not stated_
- arrays: _not stated_
- configurations: compact configuration  
  > "The array was in a compact configuration yielding synthesized beam sizes $\sim$1.5–2.5” so as not to spatially resolve the target galaxies." (2.2 ALMA observations)
- baselines: _not stated_
- angular resolution: ~1.5–2.5 arcsec synthesized beams  
  > "yielding synthesized beam sizes $\sim$1.5–2.5”" (2.2 ALMA observations)
- max recoverable scale: _not stated_
- sensitivity: 50-65 uJy/beam per 400 km/s channel; continuum ~5-9 uJy/beam  
  > "The spectral cubes have a typical noise of 50-65$\mu$Jy/beam in a 400km/s channel" (2.2 ALMA observations)
- time on source: ~90–100 min for 20866, 22260, 307881; about twice as long for 34265 and 34879  
  > "were observed for a total of $\sim$90–100 min on-source, while 34265 and 34879 were each observed for about twice as long." (2.2 ALMA observations)
- observing dates: December 18, 2018 to January 17, 2019  
  > "from December 18, 2018 to January 17, 2019" (2.2 ALMA observations)
- pi or archival as stated: _not stated_
- Line: CO J=2-1 (not stated)
- Other facility **HST (WFC3/F160W, ACS/F814W)**: high-resolution imaging for morphology (GALFIT sizes)  
  > "These include WFC3/F160W imaging from programs 12167, 14114, 12440, and ACS F814W imaging from programs 10092 and 9822." (2.1.2 Hubble Space Telescope imaging)
- Other facility **NMBS / UltraVISTA photometry**: UV to near-IR photometry for SED fitting  
  > "We use the NMBS photometric catalog that includes medium band near-infrared photometry for all galaxies" (2.1 Optical and infrared data)
- Other facility **Keck/LRIS and Subaru/MOIRCS**: spectroscopic confirmation and redshifts from literature  
  > "using deep spectroscopy from Keck/LRIS" (2 Sample and Data)
- External data: Pilot galaxy 21434 CO(2–1) ALMA data, rescaled to r21=0.8  
  > "We combine the results from this program with ALMA data for one similar galaxy from a previous pilot program" (2.2 ALMA observations) [from (cite: Bezanson2019)]
- External data: UV+IR SFRs from the UltraVISTA catalog  
  > "SFR$_{\rm UV+IR}$ values correspond to those published by the ULTRAVISTA survey" (Table 1) [from (cite: Muzzin2013)]
- External data: Literature gas fractions (PHIBSS, ASPECS, local surveys, Gobat2018 stack, etc.) for comparison  
  > "we compile measurements of molecular gas using CO as a tracer from the literature across redshifts." (3 Results) [from (cite: Tacconi2018; Gobat2018; Spilker2018; Saintonge2017)]
- Simulation/model as data: SIMBA cosmological simulation snapshot at z~1.5 and Dave2012 analytic bathtub models compared with observed f_H2  
  > "We select quiescent galaxies from a snapshot at $z\sim1.5$ to match our ALMA target selection criteria" (4.4 Comparison to cosmological simulations)

## Processing

### Calibration

- pipeline or manual: standard ALMA pipeline, reductions checked manually  
  > "The data were reduced using the standard ALMA pipeline and the reductions checked manually." (2.2 ALMA observations)
- casa version: _not stated_
- pipeline version: _not stated_
- archive products used as is: _not stated_
- flux calibrator: J1058+0133 (bandpass and flux); J0948+0022 (gain)  
  > "Bandpass and flux calibrations were performed using J1058+0133 and gain calibration using J0948+0022." (2.2 ALMA observations)
- flux scale uncertainty: _not stated_
- self calibration: _not stated_

### Imaging

- task: _not stated_
- deconvolver: _not stated_
- weighting robust: natural weighting  
  > "were created using natural weighting of the visibilities to maximize sensitivity" (2.2 ALMA observations)
- uv taper: _not stated_
- cell size: pixels chosen to give 5–10 pixels across the beam  
  > "with pixel sizes chosen to yield 5–10 pixels across the synthesized beam" (2.2 ALMA observations)
- image size: _not stated_
- masking: mask clearly detected emission (S/N>5), clean to 3x image rms  
  > "first masking regions with clearly-detected emission (S/N $>$ 5) and then we used a stopping criterion of 3$\times$ the image rms." (2.2 ALMA observations)
- multiscale scales: _not stated_
- continuum subtraction: _not stated_
- line free channels: _not stated_
- primary beam correction: _not stated_
- array combination: _not stated_
- smoothing: _not stated_
- final beam: _not stated_
- final rms: cubes 50-65 uJy/beam in 400 km/s; continuum ~5-9 uJy/beam  
  > "reach a typical sensitivity of $\sim5-9\mu$Jy/beam, calculated as the rms of the non-primary-beam corrected image" (2.2 ALMA observations)

### Inherited from earlier work

- Pilot galaxy 21434 observations and results taken from earlier paper  
  > "we combine these five targets with one galaxy from our pilot observation published in (cite: Bezanson2019)." (2 Sample and Data) [from (cite: Bezanson2019)]
- r21 = 0.8 excitation assumption  
  > "For our analysis we assume r$_{21}=0.8$ following (cite: Spilker2018)" (2.3 Molecular gas measurements) [from (cite: Spilker2018)]
- Stellar masses/ages literature SED fits used for selection; Prospector-alpha framework for refit  
  > "We fit using the PROSPECTOR-$\alpha$ model framework (cite: Leja2017)" (2.1 Optical and infrared data) [from (cite: Leja2017)]

### Not stated but needed to reproduce (our reading)

- Exact tclean/CASA version and task parameters (robust, niter, threshold per source)
- Precise line-free channels and continuum subtraction method
- Positions of offset sources fixed in uvmultifit for 22260 and 34879
- Exact velocity widths used per galaxy for upper limits
- Prospector configuration details beyond default priors
- Model parameters for the bathtub and toy-model calculations
- SIMBA selection details and halo mass assignments

## Analysis recipe

1. **Refit SEDs for stellar mass, SFR, age**: Prospector (modified Prospector-alpha, non-parametric SFH, no AGN or dust emission) on UV–near-IR photometry  
  > "we augment the PROSPECTOR-$\alpha$ model by removing emission due to active galactic nuclei" (2.1 Optical and infrared data)
   - software: Prospector, FSPS
   - parameter: default priors; NMBS photometry (UltraVISTA for 307881)  
  > "using the modified PROSPECTOR-$\alpha$ model and default priors" (2.1 Optical and infrared data)
   - assumption: Chabrier IMF; flat LCDM H0=70, Om=0.3  
  > "We assume a $\Lambda$CDM cosmology with H$_0$=70 km s$^{-1}$ Mpc$^{-1}$, $\Omega_M$ = 0.3, $\Omega_\Lambda$ = 0.7" (1 Introduction)
   - fitting: _not stated_
   - validation: compared with exponentially declining SFH; stellar mass effect on f_H2 <1.5x  
  > "which affect our measurements of $f_{\rm{H_{2}}}$ by less than a factor of 1.5." (2.1 Optical and infrared data)
2. **Extract CO(2–1) spectra from visibilities**: fit point sources to visibilities with channels averaged to 50–800 km/s; position fixed at phase center; two point sources for 22260 and 34879  
  > "we used the `uvmultifit` package (cite: MartiVidal2014) to fit pointlike sources to the visibilities" (2.3 Molecular gas measurements)
   - software: uvmultifit
   - assumption: point-like source approximation valid  
  > "the point-like source approximation is likely valid" (2.3 Molecular gas measurements)
   - fitting: flux density per channel as free parameter  
  > "leaving only the flux density at each channel as a free parameter" (2.3 Molecular gas measurements)
   - validation: _not stated_
3. **Measure line flux or upper limits and convert to L'CO and M_H2**: Gaussian fit for detection; upper limits from channel noise with FWHM 500–600 km/s; convert with r21=0.8 and alpha_CO=4.4  
  > "We use these line widths and the channel noise to set upper limits on the integrated line fluxes of each target." (2.3 Molecular gas measurements)
   - parameter: r21 = 0.8, alpha_CO = 4.4  
  > "assuming r$_{21}$ = 0.8 in temperature units, alpha$_{CO}$ = 4.4" (Table 2)
   - assumption: stellar velocity dispersion sets gas linewidth; Milky Way alpha_CO  
  > "we assume similar line widths for the stars as any molecular gas" (2.3 Molecular gas measurements)
   - fitting: Gaussian fit to 22260 spectrum  
  > "we measure the line flux by fitting a simple Gaussian to the CO(2–1) spectrum" (2.3 Molecular gas measurements)
   - validation: _not stated_
4. **Stack the five non-detections**: weighted mean of 400 km/s channel maps (non-PB-corrected) at CO(2–1) rest frequency of each galaxy  
  > "We calculate the weighted average (mean) to account for the slight differences in map rms" (2.4 Stack of non-detections in CO(2–1))
   - parameter: mean z=1.476; 400 km/s bins  
  > "We use the mean redshift of the non-detected galaxies ($<z>$=1.476)" (2.4 Stack of non-detections in CO(2–1))
   - fitting: _not stated_
   - validation: _not stated_
5. **Compare gas fractions with scaling relations, toy models, bathtub models and SIMBA**: closed-box toy models with constant and varying t_dep (Tacconi2018, Liu2019); Dave2012 equilibrium model with Behroozi2010 halo mass via HALOTOOLS; SIMBA selection at z~1.5  
  > "we construct a closed-box toy model for a log$_{10}\ensuremath{M_{\rm{*}}}/\ensuremath{\rm{M}_\odot}\sim11$ main sequence galaxy that stops gas accretion" (4.2.1 Closed-box toy model)
   - software: HALOTOOLS
   - parameter: 30% mass return to ISM in constant-t_dep model; none in varying model  
  > "stellar mass loss will return $\sim30\%$ of that mass back to the interstellar medium" (4.2.1 Closed-box toy model)
   - fitting: _not stated_
   - validation: _not stated_

## Software

- **Prospector** : SED fitting for stellar mass, SFR, age  
  > "we re-fit the UV to near-IR photometry uniformly using the SED-fitting code PROSPECTOR" (2.1 Optical and infrared data)
- **FSPS** : stellar population synthesis within Prospector  
  > "which uses the Flexible Stellar Populations Synthesis (FSPS) code" (2.1 Optical and infrared data)
- **grizli** : HST imaging processing and astrometry  
  > "We process all available *HST* imaging covering the ALMA sources with the grizli software" (2.1.2 Hubble Space Telescope imaging)
- **DrizzlePac / AstroDrizzle** : combining HST exposures  
  > "we combine exposures in a given filter (from one or more associations) using DrizzlePac / AstroDrizzle" (2.1.2 Hubble Space Telescope imaging)
- **GALFIT** : HST half-light radii  
  > "Measured with GALFIT (cite: Peng2002)" (Table 1)
- **uvmultifit** : fitting point sources to visibilities to extract spectra  
  > "we used the `uvmultifit` package (cite: MartiVidal2014) to fit pointlike sources to the visibilities" (2.3 Molecular gas measurements)
- **HALOTOOLS** : stellar-to-halo mass relation of Behroozi2010  
  > "using the stellar mass to halo mass relation of (cite: Behroozi2010) as implemented in HALOTOOLS" (4.3 Comparison to analytic bathtub models)
- **ALMA pipeline** : data reduction  
  > "The data were reduced using the standard ALMA pipeline" (2.2 ALMA observations)

## Numeric results

| quantity | value | uncertainty | units | step | quote |
|---|---|---|---|---|---|
| CO(2–1) line flux of 22260 | 90 | 19 | mJy km/s | 3 | / 22260$^d$ / 180 $\pm$ 38 / 90$\pm$ 19 / 19 $\pm$ 4 / 10.5 $\pm$ 2.2 / 3.2 $\pm$ 0.7 / |
| M_H2 of 22260 | 10.5 | 2.2 | 1e9 Msun | 3 | / 22260$^d$ / 180 $\pm$ 38 / 90$\pm$ 19 / 19 $\pm$ 4 / 10.5 $\pm$ 2.2 / 3.2 $\pm$ 0.7 / |
| f_H2 of 22260 | 3.2 | 0.7 | % | 3 | / 22260$^d$ / 180 $\pm$ 38 / 90$\pm$ 19 / 19 $\pm$ 4 / 10.5 $\pm$ 2.2 / 3.2 $\pm$ 0.7 / |
| f_H2 3sigma upper limits of non-detections | <4.3, <2.6, <3.0, <5.5, <2.1 | not stated | % | 3 | / 20866 / 47.4 / 23.7 / 7.5 / 12.3 / $<$ 4.3 / |
| Stack f_H2 (3sigma) | <1.6 | not stated | % | 4 | this puts a 3$\sigma$ upper limit on the molecular gas fraction of 1.6% |
| Stack M_H2 (3sigma) | <4.7e9 | not stated | Msun | 4 | $M_{\rm{H_{2}}}$$<4.7\times10^{9}$$\rm{M}_\odot$(3$\sigma$) |
| Stack rms | 25.6 | not stated | uJy/beam | 4 | an rms noise limit of 25.6$\mu$Jy/beam for the 400 km/s channel width of the stack |
| Limiting depletion time | <0.6 | not stated | Gyr | 5 | We estimate an upper limit to the typical depletion time of $t_{\rm{dep}}$$<0.6$ Gyr |

## Qualitative findings

- No variation of f_H2 with size or stellar density within the sample  
  > "we do not observe any variation with size or stellar density across the large dynamic range of the structural properties within our sample." (5 Conclusions)

## Claim tuples

- H: Do massive quiescent galaxies at z~1.5 retain molecular gas comparable to star-forming galaxies? | E: ALMA Band 3 CO(2–1) of 6 galaxies, stacking | R: One 4 sigma detection; others with f_H2<2-6% | F: Gas fractions are very low, 1-2 dex below star-forming galaxies | **supported**
- H: Do empirical scaling relations extrapolate to low sSFR? | E: Closed-box toy models with Tacconi2018 and Liu2019 t_dep relations | R: Extrapolation implies f_H2~10% (Tacconi) or ~6% (Liu) | F: Depletion must be rapid; extrapolations disagree | **supported**
- H: Are low gas fractions explained by massive halos halting accretion early? | E: Compare with Dave2012 bathtub model and SIMBA | R: Consistent with 10^14 Msun halos and with SIMBA | F: Plausible but not conclusive; lower-mass halos with stronger feedback not excluded | **partially**

## Reasoning

- Why this data: _not stated_
- Why this method: Natural weighting for sensitivity; compact configuration to avoid resolving sources  
  > "using natural weighting of the visibilities to maximize sensitivity" (2.2 ALMA observations)
- Alternative: Higher r21=1 would give even lower gas fractions; r21=0.8 adopted as conservative  
  > "which results in more conservative (higher) molecular gas mass measurements and limits than the assumption of thermalized emission" (2.3 Molecular gas measurements)
- How they decided it was enough: _not stated_
- Limitation (authors): Mostly upper limits on M_H2 and SFR preclude robust depletion time measurement  
  > "our dataset precludes a robust measurement of (current) depletion times" (4.2 Timescales for gas consumption or destruction)
- Limitation (authors): alpha_CO uncertainty of factor >=2  
  > "a factor of $\gtrsim$2 uncertainty due to the assumed value of the CO-H$_{2}$ conversion factor" (2.3 Molecular gas measurements)
- Caveat (inferred, ours): Upper limits rely on assumed linewidths from stellar dispersion
- Caveat (inferred, ours): Point-source assumption at 2 arcsec resolution
- Caveat (inferred, ours): 22260 detection is offset from the galaxy and may not be associated
- Caveat (inferred, ours): Halo-mass interpretation is qualitative
- Caveat (inferred, ours): Small sample

## Reproducibility

- Data public (paper): ALMA project codes cited in acknowledgments  
  > "This paper makes use of the following ALMA data: ADS/JAO.ALMA #2018.1.01739.S, ADS/JAO.ALMA #2015.1.00853.S." (Acknowledgments)
- Products in archive: _not stated_
- Missing: Exact imaging parameters and CASA version
- Missing: Details of toy-model and bathtub implementations
- Missing: SIMBA data selection details
- Data volume (inferred): tens of GB (two small Band 3 programs, 6 fields)
- Score (inferred): 3/5, Public data and simple analysis, but imaging and modelling details are thin.
- Rediscovery candidate: yes, Public data, simple point-source extraction, numeric limits; but some settings missing.

## Links

- Method: (cite: MartiVidal2014) (uvmultifit visibility fitting)
- Method: (cite: Leja2017) (Prospector-alpha model)
- Companion: (cite: Bezanson2019) (pilot ALMA CO observation of galaxy 21434)
- Companion: (cite: Williams2019) (serendipitous 3 mm sources in these data)
- Companion: (cite: Spilker2018) (similar CO study of quiescent galaxies at z~0.7)
- Related: PHIBSS
- Related: ASPECS
- Related: NMBS
- Related: UltraVISTA

## Checks

```json
{
 "quotes": 75,
 "quotes_ok": 75,
 "quote_pass_rate": 1.0,
 "quotes_too_long": 0,
 "unsupported_facts": 0,
 "project_codes": 2,
 "codes_not_in_text": [],
 "codes_not_in_obscore": [],
 "obscore_codes_not_in_card": [],
 "codes_printed_but_missing": [],
 "numeric_results": 8,
 "numeric_problems": 0,
 "fill": {
  "facts": 87,
  "stated": 56,
  "rate": 0.644
 },
 "evidence_ok": true
}
```
