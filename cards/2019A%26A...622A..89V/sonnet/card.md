# The Fornax 3D project: dust mix and gas properties in the centre of early-type galaxy FCC 167

`2019A&A...622A..89V` | Astronomy and Astrophysics 2019 | first author: Viaene, S. | arXiv: 1812.07582 | DOI: 10.1051/0004-6361/201834465

Card schema 1.0 | model claude-sonnet-5-5 | depth light | type multi_facility_alma_minor

## Science

- Fields: nearby_galaxies
- Question: Whether combining ISM geometry constraints (MUSE ionised gas, ALMA CO) with 3D radiative transfer modelling can reveal the kind of dust in the dust-lane early-type galaxy FCC 167 and the origin of its ISM  
  > "The goal of this paper is to explore whether it is possible to infer qualitative information about the kind of dust in a galaxy by combining constraints on the geometry of the ISM and advanced radiative transfer modeling." (1 Introduction)
- Target **FCC 167 (NGC 1380)**: coordinates RA 03h36m27.55s, Dec -34d58m33.88s (J2000)  
  > "FCC 167 ($\alpha_{J2000}=03^h36^m27.55^s$, $\delta_{J2000}=-34\degree58^{\prime}33.88^{\prime\prime}$, $D=18.8$ Mpc) is part of the Fornax Cluster" (2 Observations and Data); "Distances based on surface brightness fluctuations measured by (cite: Ferrarese2000) indicate that FCC 167 ($18.8$ Mpc) is closer to us than NGC 1399 ($20.5$ Mpc)." (6.2 Origin of the ISM); z/distance D = 18.8 Mpc  
  > "FCC 167 ($\alpha_{J2000}=03^h36^m27.55^s$, $\delta_{J2000}=-34\degree58^{\prime}33.88^{\prime\prime}$, $D=18.8$ Mpc) is part of the Fornax Cluster" (2 Observations and Data); "Distances based on surface brightness fluctuations measured by (cite: Ferrarese2000) indicate that FCC 167 ($18.8$ Mpc) is closer to us than NGC 1399 ($20.5$ Mpc)." (6.2 Origin of the ISM); distance from surface brightness fluctuations (Ferrarese et al. 2000)  
  > "FCC 167 ($\alpha_{J2000}=03^h36^m27.55^s$, $\delta_{J2000}=-34\degree58^{\prime}33.88^{\prime\prime}$, $D=18.8$ Mpc) is part of the Fornax Cluster" (2 Observations and Data); "Distances based on surface brightness fluctuations measured by (cite: Ferrarese2000) indicate that FCC 167 ($18.8$ Mpc) is closer to us than NGC 1399 ($20.5$ Mpc)." (6.2 Origin of the ISM)

## Data provenance

- ALMA projects: 2015.1.00497.S
- bands: _not stated_
- frequencies and spectral setup: _not stated_
- continuum bandwidth: _not stated_
- arrays: _not stated_
- configurations: _not stated_
- baselines: _not stated_
- angular resolution: ~4 arcsec beam  
  > "The ALMA morphology is broader than the dust or ionised gas maps due to the $\sim4^{\prime\prime}$ beam." (4.2 Molecular gas)
- max recoverable scale: _not stated_
- sensitivity: _not stated_
- time on source: _not stated_
- observing dates: _not stated_
- pi or archival as stated: ALMA Fornax Cluster Survey (PI: T. Davis); details in Zabel et al. 2018  
  > "ALMA observations from the ALMA Fornax Cluster Survey (PI: T. Davis)." (2 Observations and Data); "For details of the survey including moment maps we refer to (cite: Zabel2018)." (2 Observations and Data)
- Line: CO J=1-0 (not stated)
- Other facility **VLT/MUSE (Fornax 3D)**: Integral-field optical data cube used for attenuation curve, ionised gas and stellar models  
  > "This is a Director’s Discretionary Time program on the Multi Unit Spectroscopic Explorer (MUSE" (2 Observations and Data)
- Other facility **Chandra**: Archival X-ray spectrum to derive hot gas properties  
  > "we investigate archival X-ray data from the *Chandra* X-ray Observatory." (2 Observations and Data)
- Other facility **Herschel (PACS, SPIRE via DustPedia)**: FIR/submm fluxes for energy balance  
  > "These fluxes were measured from the PACS (cite: PACS) and SPIRE (cite: SPIRE) images provided by the DustPedia (cite: Davies2017) database." (2 Observations and Data)
- External data: ALMA CO(1-0) survey data and moment maps for FCC 167  
  > "For details of the survey including moment maps we refer to (cite: Zabel2018)." (2 Observations and Data) [from Zabel et al. 2018 (cite: Zabel2018)]
- External data: Stellar dynamical inclination of 77.6 deg  
  > "The inclination angle is perfectly consistent with the value of $77.6\degree$ obtained from the stellar dynamical modeling presented in (cite: Sarzi2018)." (5.1 FitSKIRT ring model) [from Sarzi et al. 2018 (cite: Sarzi2018)]

## Processing

### Calibration

- pipeline or manual: _not stated_
- casa version: _not stated_
- pipeline version: _not stated_
- archive products used as is: _not stated_
- flux calibrator: _not stated_
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

- Dust-free MGE attenuation-curve technique  
  > "The same technique as in (cite: Viaene2017) is used, which we briefly summarise here." (3 Spectrally resolved optical attenuation) [from (cite: Viaene2017)]
- MUSE observing strategy and data reduction, per-spaxel gas fitting  
  > "For more information on the observing strategy and data reduction process, we refer to the F3D survey paper (cite: Sarzi2018)." (2 Observations and Data) [from (cite: Sarzi2018)]
- Dust lifetime estimate from hot gas  
  > "These hot gas properties can also be used to estimate the dust lifetime following (cite: Jones2004)." (6.1 Dust distribution and survival) [from (cite: Jones2004)]

### Not stated but needed to reproduce (our reading)

- ALMA calibration, imaging, and cube parameters (beam, channel width, rms) are all deferred to Zabel et al. 2018
- KinMS ring model parameterisation, priors and MCMC settings (chain length, convergence)
- FitSKIRT genetic algorithm settings, photon numbers and PSF handling
- Mask ellipses defining the dust lane
- Aperture photometry apertures for Herschel
- X-ray extraction region, abundances and column density
- Modified blackbody fit details (temperature, beta)

## Analysis recipe

1. **Fit ring model to ALMA CO(1-0) cube**: KinMS data cube model compared to ALMA cube with adamet MCMC; ring and exponential disk tried  
  > "We use Markov chain Monte Carlo (MCMC) methods, in particular the `adamet` Python package of (cite: Cappellari2013)" (4.2 Molecular gas)
   - software: KinMS, adamet
   - parameter: Inclination fixed at 76.3 deg from dust lane models  
  > "The inclination was fixed at $76.3 \degree$, based on our models of the dust lane" (4.2 Molecular gas)
   - fitting: Adaptive Metropolis MCMC (Haario et al. 2001); priors not stated  
  > "which implements the Adaptive Metropolis algorithm of (cite: Haario2001)" (4.2 Molecular gas)
   - validation: Only a ring-shaped model gives a good fit  
  > "Both exponential disks and ring morphologies were fitted to the data, only a ring-shaped model results in a good fit." (4.2 Molecular gas)

## Software

- **KinMS** : Kinematic models of ionised and molecular gas  
  > "We constructed a dynamical model for the molecular gas again using KinMS (cite: Davis2013)." (4.2 Molecular gas)
- **adamet** : MCMC fitting of the CO model  
  > "in particular the `adamet` Python package of (cite: Cappellari2013)" (4.2 Molecular gas)
- **FitSKIRT** : Optimising 3D dust ring radiative transfer models  
  > "with their code FitSKIRT, an optimizer for the radiative transfer code SKIRT" (5 3D radiative transfer models)
- **SKIRT** : Radiative transfer and panchromatic SED  
  > "The transfer of radiation is then simulated in 3D with SKIRT." (5.2 Panchromatic model and energy balance)
- **pPXF** : Stellar kinematics and population fits  
  > "The F3D analysis pipeline produces a pPXF (cite: Cappellari2004; Cappellari2017) and GandALF (cite: Sarzi2006) best-fit spectral model" (4.1 Ionised gas)
- **photutils** : Aperture photometry of Herschel images  
  > "We performed our own aperture photometry using the Python `photutils` package (cite: photutils)" (2 Observations and Data)
- **XSPEC** : X-ray spectral fit  
  > "XSPEC (cite: XSPEC) was used to fit a two-component (`wa*po+mekal`) model to the observed spectrum." (6.1 Dust distribution and survival)

## Numeric results

| quantity | value | uncertainty | units | step | quote |
|---|---|---|---|---|---|
| ALMA CO ring log mass | 7.67 | 0.06 | log(M/Msun) | 1 | / ALMA CO / $7.67 \pm 0.06$ / $151 \pm 62$ / $223 \pm 12$ / $223 \pm 8$ / $76.3$ (fixed) / |
| ALMA CO ring radius | 151 | 62 | pc | 1 | / ALMA CO / $7.67 \pm 0.06$ / $151 \pm 62$ / $223 \pm 12$ / $223 \pm 8$ / $76.3$ (fixed) / |
| Dust mass from observed SED | 8.3e5 | +2.2/-1.8 e5 | Msun | 0 | which is $8.3^{+2.2}_{-1.8} \times 10^5 M_\odot$ |
| Gas-to-dust ratio | ~80 | not stated | dimensionless | 0 | The gas-to-dust ratio of $\sim80$ in FCC 167 |

## Qualitative findings

- CO(1-0) is strong, regularly rotating (up to 250 km/s), more compact than the dust lane and ring-like  
  > "The molecular gas exhibits regular rotation, with line-of-sight rotational velocities up to $250$ km s$^{-1}$." (4.2 Molecular gas)

## Claim tuples

- H: Is the molecular gas distributed as an exponential disk or a ring? | E: KinMS plus MCMC fit to ALMA CO(1-0) cube | R: Only the ring gives a good fit, with ring radius 151 pc | F: Molecular gas is ring-like, perhaps carved by AGN | **supported**
- H: Does Milky Way dust reproduce the attenuation curve? | E: FitSKIRT ring models with THEMIS MW vs bare silicate dust | R: Silicate model matches the slope; MW is too steep | F: Dust lacks small carbonaceous grains | **supported**

## Reasoning

- Why this data: _not stated_
- Why this method: _not stated_
- Alternative: Exponential dust disk gave no good fits  
  > "We explored the possibility of an exponential dust disk, but this provided no good fits to the data." (5.1 FitSKIRT ring model)
- How they decided it was enough: _not stated_
- Limitation (authors): Dust scale heights are below the MUSE PSF, which limits the parameters  
  > "The uncertain values for the scale height may be linked to the resolution limit of the data." (5.1 FitSKIRT ring model)
- Caveat (inferred, ours): The ALMA analysis is thin and relies on Zabel et al. 2018
- Caveat (inferred, ours): The coarse 4 arcsec beam limits the comparison with the dust ring
- Caveat (inferred, ours): Dust masses from the radiative transfer models are inconsistent with the Herschel-derived masses

## Reproducibility

- Data public (paper): ALMA data cited by project code and survey; ESO programme given for MUSE  
  > "Based on observations collected at the European Organisation for Astronomical Research in the Southern Hemisphere under ESO programme 296.B-5054(A)." (Acknowledgements)
- Products in archive: _not stated_
- Missing: ALMA reduction details
- Missing: KinMS and MCMC priors
- Missing: FitSKIRT run settings
- Data volume (inferred): ALMA cube about 1 GB; MUSE cube a few GB
- Score (inferred): 2/5, ALMA is a minor ingredient and its processing is deferred to another paper; the main results are radiative transfer models on MUSE data.
- Rediscovery candidate: no, The ALMA recipe is incomplete and the main results rely on MUSE and radiative transfer modelling.

## Links

- Method: Zabel et al. 2018 (ALMA Fornax Cluster Survey data description)
- Method: Davis et al. 2013 (KinMS) (Kinematic modelling)
- Companion: Sarzi et al. 2018 (Fornax 3D survey paper)
- Companion: Viaene et al. 2017 (NGC 5626 attenuation curve)
- Related: ALMA Fornax Cluster Survey
- Related: Fornax 3D

## Checks

```json
{
 "quotes": 43,
 "quotes_ok": 43,
 "quote_pass_rate": 1.0,
 "quotes_too_long": 0,
 "unsupported_facts": 0,
 "project_codes": 1,
 "codes_not_in_text": [],
 "codes_not_in_obscore": [],
 "obscore_codes_not_in_card": [],
 "codes_printed_but_missing": [],
 "numeric_results": 4,
 "numeric_problems": 0,
 "fill": {
  "facts": 65,
  "stated": 29,
  "rate": 0.446
 },
 "evidence_ok": true
}
```
