# The shadow of the Flying Saucer: A very low temperature for large dust grains

`2016A&A...586L...1G` | Astronomy and Astrophysics 2016 | first author: Guilloteau, S. | arXiv: 1601.01548 | DOI: 10.1051/0004-6361/201527620

Card schema 1.0 | model claude-sonnet-5-5 | depth full | type observational_alma_primary

## Science

- Fields: protoplanetary_disks
- Question: Can the temperature of large mm-emitting dust grains in the edge-on Flying Saucer disk be measured directly from its silhouette against background CO cloud emission?  
  > "We attempt a direct determination of the temperature of large grains emitting at mm wavelengths." (abstract)
- Target **Flying Saucer**: coordinates _not stated_; z/distance 120 pc  
  > "resolved the light scattered by (micron) dust grains in near-infrared with the NTT and the VLT and estimated a disk radius of $2.15''$, which is about 260 au for the adopted distance of 120 pc (cite: Loinard+etal_2008)." (Introduction); distance from Loinard et al. 2008  
  > "resolved the light scattered by (micron) dust grains in near-infrared with the NTT and the VLT and estimated a disk radius of $2.15''$, which is about 260 au for the adopted distance of 120 pc (cite: Loinard+etal_2008)." (Introduction)

## Data provenance

- ALMA projects: 2013.1.00387.S
- bands: _not stated_
- frequencies and spectral setup: channel spacing 15 kHz, effective velocity resolution 40 m/s  
  > "channel spacing of 15 kHz (and an effective velocity resolution of 40 m/s)" (ALMA)
- continuum bandwidth: _not stated_
- arrays: _not stated_
- configurations: _not stated_
- baselines: shortest baseline 21 m  
  > "with our shortest baselines of 21 m" (Results and analysis)
- angular resolution: circular beam 0.5 arcsec  
  > "yields a circular beamsize of 0.5$''$" (ALMA)
- max recoverable scale: 7.6 arcsec  
  > "($>7.6''$ with our shortest baselines of 21 m)" (Results and analysis)
- sensitivity: _not stated_
- time on source: _not stated_
- observing dates: 17 and 18 May 2015  
  > "performed with ALMA on 17 and 18 May 2015 under excellent weather (Cycle 2, 2013.1.00387.S)" (ALMA)
- pi or archival as stated: _not stated_
- Line: CO J=2-1 (not stated)
- Other facility **IRAM 30-m**: CO J=2-1 spectrum giving background cloud brightness T_c(v)  
  > "We obtained a CO J=2-1 spectrum of the Flying Saucer with the IRAM 30-m to measure the brightness of the (foreground or background) emission." (IRAM 30-m)
- Other facility **FCRAO CO J=1-0 survey**: selection of low-emission reference position  
  > "in a region of low emission selected with the FCRAO CO J=1-0 wide field survey" (IRAM 30-m)
- External data: 850 micron SCUBA flux of 58 mJy in 15'' beam  
  > "report a flux of 58 mJy in the 15$''$ beam of SCUBA at 850$\mu$m" (Results and analysis) [from (cite: vanKempen+etal_2009)]
- External data: stellar luminosity ~0.10 Lsun from J,H,Ks images  
  > "require a stellar luminosity of $\sim 0.10 L_\odot$" (Discussion) [from (cite: Grosso+etal_2003)]

## Processing

### Calibration

- pipeline or manual: standard ALMA calibration script in CASA  
  > "Data was calibrated via the standard ALMA calibration script in the CASA software package." (ALMA)
- casa version: _not stated_
- pipeline version: _not stated_
- archive products used as is: _not stated_
- flux calibrator: Titan  
  > "Titan was used as a flux calibrator." (ALMA)
- flux scale uncertainty: 5% continuum calibration uncertainty  
  > "The total continuum flux is 35 mJy at 242 GHz (with 5% calibration uncertainty)." (ALMA)
- self calibration: none  
  > "No self-calibration was performed." (ALMA)

### Imaging

- task: _not stated_
- deconvolver: _not stated_
- weighting robust: robust weighting (value not given)  
  > "With robust weighting, the $uv$ coverage" (ALMA)
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
- final beam: 0.5 arcsec circular  
  > "yields a circular beamsize of 0.5$''$" (ALMA)
- final rms: _not stated_

### Inherited from earlier work

- Temperature law exponent T=T0 (r/100 au)^-0.4 for disk model  
  > "We assumed $T = T_0 (r/100 \mathrm{au})^{-0.4}$, following (cite: Guilloteau+etal_2011)." (Results and analysis) [from (cite: Guilloteau+etal_2011)]

### Not stated but needed to reproduce (our reading)

- robust parameter value
- imaging cell and image size
- how the 30-m and ALMA cubes were aligned/resampled in velocity
- coordinates of the source and 30-m pointing
- priors and likelihood for the MCMC
- model fitting software for the disk model
- how T_d and T_l were extracted per pixel
- stellar mass and source of the 0.57 Msun value

## Analysis recipe

1. **Image ALMA CO cube and continuum**: Calibrated data exported via UVFITS to GILDAS for imaging and analysis  
  > "exported through UVFITS format to the GILDAS package for imaging and data analysis" (ALMA)
   - software: CASA, GILDAS
   - fitting: _not stated_
   - validation: _not stated_
2. **Derive dust temperature from absorption**: Use J_nu(Tdust) ≈ Td/(Td−Tl(v)) Tc(v), with Tc from the 30-m spectrum, applied per pixel and channel  
  > "Eq. [\[eq:tdust\]](#eq:tdust) can be applied for each pixel and velocity channel, allowing us to derive a datacube of dust temperatures." (Results and analysis)
   - software: GILDAS
   - assumption: Extended cloud emission filtered out by the interferometer; disk in front of the cloud  
  > "A smooth extended CO emission is filtered out by the interferometer whatever its opacity, leading to a null brightness." (Results and analysis)
   - fitting: _not stated_
   - validation: Consistency across velocities; effect of cloud structure tested with maximum filling-factor correction (Tc x1.9)  
  > "This would increase $T_c(\mathrm{v})$ by a factor 1.9." (Results and analysis)
3. **Fit dust disk model to the continuum**: Vertically isothermal truncated power-law disk model fitted to the 242 GHz continuum, T exponent fixed at 0.4  
  > "We analyzed the 242 GHz continuum with a simple disk model that is vertically isothermal, using truncated power laws for temperature and surface density and no dust settling" (Results and analysis)
   - software: emcee
   - parameter: 40 walkers, 5000 steps, last 1000 retained  
  > "with 40 walkers and 5000 steps, retaining only the last 1000 steps for the error analysis" (Results and analysis)
   - fitting: emcee affine-invariant MCMC  
  > "We ran an MCMC, using the “emcee” tool of (cite: Foreman-Mackey+etal_2013)" (Results and analysis)
   - validation: Tapered-edge viscous profiles gave a poorer fit  
  > "tapered edge viscous profiles yielded a poorer fit" (Results and analysis)

## Software

- **CASA** : standard ALMA calibration  
  > "Data was calibrated via the standard ALMA calibration script in the CASA software package." (ALMA)
- **GILDAS** : imaging and data analysis  
  > "exported through UVFITS format to the GILDAS package for imaging and data analysis" (ALMA)
- **emcee** : MCMC disk model fitting  
  > "We ran an MCMC, using the “emcee” tool of (cite: Foreman-Mackey+etal_2013)" (Results and analysis)

## Numeric results

| quantity | value | uncertainty | units | step | quote |
|---|---|---|---|---|---|
| Dust temperature (average) | 5 to 8 | not stated | K | 2 | we thus derive (average) dust temperatures as low as 5 to 8 K |
| Temperature law | T(r)=7 K (r/100 au)^-0.4 | not stated | K | 2 | consistent with $T(r)= 7\,\mathrm{K}\,(r/100\,\mathrm{au})^{-0.4}$ |
| Total continuum flux at 242 GHz | 35 | 5% | mJy | 1 | The total continuum flux is 35 mJy at 242 GHz (with 5% calibration uncertainty). |
| Scale height at 100 au H0 | 12.7 | 0.3 | au | 3 | $H_0$            / $12.7 \pm 0.3$   / au |
| Outer radius | 187.0 | 0.1 | au | 3 | $R_\mathrm{out}$ / $187.0 \pm 0.1$  / au |
| Surface density exponent p | -0.49 | 0.02 | dimensionless | 3 | $p$              / $-0.49 \pm 0.02$ |
| Inclination | 90.8 | 0.4 | deg | 3 | $i$              / $90.8 \pm 0.4$   / $^\circ$ |

## Qualitative findings

- Dust disk is very flat, indicating settling in outer parts  
  > "However, the dust disk is very flat (flaring index -0.35), which is indicative of dust settling in the outer parts." (abstract)

## Claim tuples

- H: Large mm dust grains can have their temperature measured directly via absorption of background CO | E: ALMA CO 2-1 silhouette plus IRAM 30-m cloud brightness | R: Dust temperature 5-8 K, T(r)=7 K (r/100 au)^-0.4 | F: Dust is much colder than most model predictions | **supported**
- H: Disk is vertically thin and settled | E: MCMC fit of the continuum | R: H0 = 12.7 au, flaring index -0.34 | F: Dust settling in outer disk | **supported**

## Reasoning

- Why this data: Edge-on disks maximize line-of-sight opacity and expected silhouette signal  
  > "Edge-on disks are the best targets for this because their larger line-of-sight opacity maximizes the expected signal." (Introduction)
- Why this method: _not stated_
- Alternative: Tapered-edge viscous profiles rejected for poorer fit  
  > "tapered edge viscous profiles yielded a poorer fit" (Results and analysis)
- How they decided it was enough: _not stated_
- Limitation (authors): Missing short spacings and cloud structure on 7-10'' scales may bias temperatures; inner <40 au may be biased  
  > "the inner regions ($< 40$ au) may be biased because of residual emission from the (warm) CO disk itself" (Results and analysis)
- Limitation (authors): Spectral index could not be constrained, degeneracy between temperature and surface density  
  > "leave a strong degeneracy between the dust temperature and surface density, so no reliable value could be found" (Results and analysis)
- Caveat (inferred, ours): Foreground/background geometry of the clouds is assumed
- Caveat (inferred, ours): Tc at the disk position relies on a 10.7'' beam spectrum
- Caveat (inferred, ours): Temperature exponent fixed rather than fitted

## Reproducibility

- Data public (paper): _not stated_
- Products in archive: _not stated_
- Missing: robust value and imaging parameters
- Missing: 30-m spectrum data and Gaussian decomposition
- Missing: exact procedure for measuring Td and Tl
- Missing: MCMC priors and model code
- Data volume (inferred): ~50-200 GB raw for a high-spectral-resolution Cycle 2 CO dataset
- Score (inferred): 3/5, ALMA project code given and method equations clear, but imaging and fitting details and 30-m data are missing.
- Rediscovery candidate: no, Requires IRAM 30-m data and unstated imaging settings.

## Links

- Method: (cite: Gueth+etal_1997) (Foreground cloud interferometric absorption effects)
- Method: (cite: Boehler+etal_2013) (Edge-on settled disk fitted without settling gives low flaring and negative p)
- Companion: (cite: Grosso+etal_2003) (NIR scattered-light imaging of the Flying Saucer)
- Related: COMPLETE FCRAO Ophiuchus CO cubes

## Checks

```json
{
 "quotes": 47,
 "quotes_ok": 47,
 "quote_pass_rate": 1.0,
 "quotes_too_long": 0,
 "unsupported_facts": 0,
 "project_codes": 1,
 "codes_not_in_text": [],
 "codes_not_in_obscore": [],
 "obscore_codes_not_in_card": [],
 "codes_printed_but_missing": [],
 "numeric_results": 7,
 "numeric_problems": 0,
 "fill": {
  "facts": 66,
  "stated": 35,
  "rate": 0.53
 },
 "evidence_ok": true
}
```
