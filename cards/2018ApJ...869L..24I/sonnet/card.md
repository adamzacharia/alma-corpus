# G11.92-0.61 MM 1: A Fragmented Keplerian Disk Surrounding a Proto-O Star

`2018ApJ...869L..24I` | The Astrophysical Journal Letters 2018 | first author: Ilee, J. D. | arXiv: 1811.05267 | DOI: 10.3847/2041-8213/aaeffc

Card schema 1.0 | model claude-sonnet-5-5 | depth full | type observational_alma_primary

## Science

- Fields: star_formation
- Question: Is the massive protostar G11.92-0.61 MM 1 surrounded by a Keplerian disk, and is there evidence of disk fragmentation producing a companion?  
  > "we report high spatial and spectral resolution line and continuum ALMA observations of G11.92$-$0.61 MM 1 that were designed to further characterise the circumstellar environment of this massive young stellar object, and search for evidence of disk fragmentation." (Introduction)
- Target **G11.92-0.61 MM 1**: coordinates 18:13:58.111 -18:54:20.205 (MM 1a, J2000)  
  > "its distance is 3.37$^{+0.39}_{-0.32}$ kpc (cite: sato_2014)" (Introduction); z/distance 3.37 (+0.39/-0.32) kpc  
  > "its distance is 3.37$^{+0.39}_{-0.32}$ kpc (cite: sato_2014)" (Introduction); distance from Sato et al. 2014 (maser parallax)  
  > "its distance is 3.37$^{+0.39}_{-0.32}$ kpc (cite: sato_2014)" (Introduction)

## Data provenance

- ALMA projects: 2016.1.01147.S
- bands: Band 6 (230 GHz, 1.3 mm)  
  > "We observed in Band 6 (230 GHz, 1.3 mm) with four SPWs" (Observations)
- frequencies and spectral setup: four SPWs: 220.26–220.73, 221.00–221.94, 235.28–236.22, 238.35–239.29 GHz  
  > "four SPWs (220.26–220.73, 221.00–221.94, 235.28–236.22 and 238.35–239.29 GHz)" (Observations)
- continuum bandwidth: 0.38 GHz  
  > "resulting in a continuum bandwidth of 0.38 GHz and sensitivity of 0.05 mJy beam$^{-1}$" (Observations)
- arrays: _not stated_
- configurations: C40-7, 46 antennas  
  > "in configuration C40-7 with 46 antennas" (Observations)
- baselines: ~15–2800 kλ  
  > "The projected baselines ranged from $\sim$15–2800 k$\lambda$." (Observations)
- angular resolution: 0.106"x0.079" (360x270 au), PA=-63.7 deg  
  > "synthesised beamsize of $0.106\ensuremath{''}\times0.079\ensuremath{''}$ ($360\times270$ au)" (Observations)
- max recoverable scale: 0.58 arcsec (1955 au)  
  > "a largest recoverable scale of $0.58\ensuremath{''}$ (1955 au)" (Observations)
- sensitivity: 0.05 mJy/beam continuum; 1.2 mJy/beam per channel (0.7 km/s)  
  > "achieving a typical per-channel sensitivity of 1.2 mJy beam$^{-1}$" (Observations)
- time on source: 93 mins  
  > "for an on-source time of 93 mins" (Observations)
- observing dates: 2017 Aug 07  
  > "Our ALMA observations were taken on 2017 Aug 07" (Observations)
- pi or archival as stated: Own program, PI J. D. Ilee  
  > "project ID 2016.1.01147.S, PI: J. D. Ilee" (Observations)
- Line: CH3CN v8=1 K=(1,-1) (221.625 GHz)
- Line: CH3CN J=12-11 K=3 (220.709 GHz)
- External data: Free-free component position and flux density fixed to cm position and spectral index  
  > "its position and flux density are fixed to the cm position and spectral index from (cite: ilee_2016)" (Table 1) [from (cite: ilee_2016)]
- External data: Dust temperature 150–230 K for main disk from earlier CH3CN modelling  
  > "we take 150–230 K based on the modelling of the CH$_3$CN $J=12$–11 emission toward MM 1 in (cite: ilee_2016)" (4.3 Mass estimates from the dust emission) [from (cite: ilee_2016)]
- External data: Distance 3.37 kpc  
  > "its distance is 3.37$^{+0.39}_{-0.32}$ kpc (cite: sato_2014)" (Introduction) [from (cite: sato_2014)]
- External data: Dust opacity 1.1 cm2/g at 1.3 mm  
  > "a dust opacity of $\kappa_{\rm  1.3\,mm}=1.1$ cm$^{2}$ g$^{-1}$" (4.3 Mass estimates from the dust emission) [from (cite: ossenkopf_1994)]

## Processing

### Calibration

- pipeline or manual: Calibration with CASA; details not given  
  > "Calibration, imaging and analysis were performed with CASA version 5.1.1" (Observations)
- casa version: CASA 5.1.1  
  > "CASA version 5.1.1 (cite: mcmullin_2007)" (Observations)
- pipeline version: _not stated_
- archive products used as is: _not stated_
- flux calibrator: _not stated_
- flux scale uncertainty: _not stated_
- self calibration: Iterative continuum self-cal, phase and amplitude solution times 6 and 54 s, S/N 569 (improvement 1.4); applied to line data  
  > "phase and amplitude solution times of 6 and 54 seconds, respectively, with a resulting S/N of 569 (an improvement factor of 1.4)" (Observations)

### Imaging

- task: _not stated_
- deconvolver: _not stated_
- weighting robust: Briggs, robust = 0  
  > "Imaging with Briggs weighting with a robust parameter of 0" (Observations)
- uv taper: _not stated_
- cell size: _not stated_
- image size: _not stated_
- masking: _not stated_
- multiscale scales: _not stated_
- continuum subtraction: Following Brogan et al. 2018  
  > "Continuum subtraction was performed following the method of (cite: brogan_2018)" (Observations)
- line free channels: _not stated_
- primary beam correction: _not stated_
- array combination: _not stated_
- smoothing: Line data resampled to 0.7 km/s  
  > "re-sampled to a common velocity resolution of 0.7 km s$^{-1}$" (Observations)
- final beam: 0.106"x0.079", PA -63.7 deg  
  > "$0.106\ensuremath{''}\times0.079\ensuremath{''}$ ($360\times270$ au), PA$=-63.7^{\circ}$" (Observations)
- final rms: _not stated_

### Inherited from earlier work

- Continuum subtraction method  
  > "Continuum subtraction was performed following the method of (cite: brogan_2018)" (Observations) [from (cite: brogan_2018)]
- PV-space Keplerian plus infall model  
  > "Following (cite: cesaroni_2011), the expected shape of the region in PV space from which emission will originate can be expressed as" (4.1 Mass estimates from the gas kinematics) [from (cite: cesaroni_2011)]
- MCMC settings for CASSIS fitting  
  > "Markov-Chain Monte Carlo minimisation with 10$^{4}$ iterations, a cut-off parameter of 5000, and an acceptance rate of 0.5 (cite: ilee_2016)" (4.2 Physical conditions toward MM 1b) [from (cite: ilee_2016)]
- Isothermal dust mass model corrected for opacity  
  > "a simple model of isothermal dust emission, corrected for dust opacity (cite: cyganowski_2011sma)" (4.3 Mass estimates from the dust emission) [from (cite: cyganowski_2011sma)]

### Not stated but needed to reproduce (our reading)

- Line-free channels and continuum-subtraction details
- Self-calibration reference antenna, spw choice and number of iterations
- Image size, cell size, deconvolver, masks, clean threshold
- Primary beam correction details
- PV extraction width and intensity contour threshold used for by-eye fit
- CASSIS fit priors/likelihood details, number of lines, fixed parameters
- Calibrator names and flux scale uncertainty
- Integration ranges for moment maps

## Analysis recipe

1. **Fit continuum components**: Image-plane fit of four simultaneous 2D Gaussians to MM 1a; separate fit to MM 1b  
  > "requires four individual 2D Gaussian components" (3.1 1.3 mm continuum emission)
   - software: CASA
   - parameter: PA of main component fixed from initial single-component fit; free-free component fixed  
  > "with the position angle of ($i$) fixed to the value obtained from an initial single-component fit" (Table 1)
   - fitting: _not stated_
   - validation: Peak residuals at 2 sigma (0.1 mJy/beam)  
  > "Peak residuals from the combination of these fits lie at the 2$\sigma$ level (0.1 mJy beam$^{-1}$)." (3.1 1.3 mm continuum emission)
2. **Enclosed mass from CH3CN v8=1 PV diagram**: By-eye fit of Keplerian + infall PV model, varying outer radius and mass  
  > "We then perform a by-eye fit to the offset and velocity by altering the outer radius of the emission" (4.1 Mass estimates from the gas kinematics)
   - parameter: R_in = 270 au fixed; R_out steps of ~150 au; mass steps of 5 Msun; infall at 40% of free-fall  
  > "we fix the inner radius to the beamsize, $R_{\rm in} = 270$ au." (4.1 Mass estimates from the gas kinematics)
   - assumption: Inclination ~70±10 deg from continuum aspect ratio of flat disk  
  > "corresponds to an inclination $i \sim 70$$^{\circ}$ to the line of sight" (4.1 Mass estimates from the gas kinematics)
   - fitting: _not stated_
   - validation: Models with M=40±5 for i=70∓10 deg also fit; beam convolution not accounted for  
  > "similarly best fitting models can be obtained with $M_{\rm enc} = 40\pm5$ M$_{\odot}$ for $i=70\mp10$$^{\circ}$" (4.1 Mass estimates from the gas kinematics)
3. **LTE modelling of CH3CN ladder at MM 1b**: CASSIS LTE radiative transfer with MCMC over six free parameters  
  > "We utilise the CASSIS local thermodynamic equilibrium (LTE) radiative transfer package." (4.2 Physical conditions toward MM 1b)
   - software: CASSIS
   - parameter: N 1e16–1e19 cm-2; Tex 10–450 K; dv 1–10 km/s; size 0.02–0.2 arcsec; v -5 to 5 km/s; 12C/13C 55–85  
  > "excitation temperature: $10 <  T_{\mathrm{ex}} <  450$ K" (4.2 Physical conditions toward MM 1b)
   - assumption: LTE  
  > "We utilise the CASSIS local thermodynamic equilibrium (LTE) radiative transfer package." (4.2 Physical conditions toward MM 1b)
   - fitting: MCMC, 10^4 iterations, cut-off 5000, acceptance rate 0.5  
  > "Fitting was performed using Markov-Chain Monte Carlo minimisation with 10$^{4}$ iterations" (4.2 Physical conditions toward MM 1b)
   - validation: _not stated_
4. **Dust masses of components**: Isothermal optically thin dust emission from 1.3 mm integrated flux with two bracketing temperatures  
  > "For each component, we utilise two temperature estimates to bracket the plausible range for the circumstellar material." (4.3 Mass estimates from the dust emission)
   - parameter: T: main disk 150–230 K; SW/W excess 65–150 K; MM 1b 20–128 K  
  > "In MM 1b, we take 20 – 128 K" (4.3 Mass estimates from the dust emission)
   - assumption: gas-to-dust 100; kappa(1.3mm)=1.1 cm2/g; 99.5% of flux is dust  
  > "assuming a gas-to-dust mass ratio of 100 and a dust opacity of $\kappa_{\rm  1.3\,mm}=1.1$ cm$^{2}$ g$^{-1}$" (4.3 Mass estimates from the dust emission)
   - fitting: _not stated_
   - validation: _not stated_
5. **Dynamical mass and stability of MM 1b**: M_enc = R (V/sin i)^2/G with fitted size and CH3CN velocity; Hill sphere check  
  > "$M_{\rm enc} = R (V / \sin i)^2 / G =  116\,{\rm au} (2.1\,{\rm km}\,{\rm s}^{-1} / \sin i)^2 / G = 0.57 / \sin^{2} i \,\mathrm{M}_{\odot}$" (4.3 Mass estimates from the dust emission)
   - assumption: MM 1b kinematics dominated by Keplerian disk  
  > "Under the assumption that the gas kinematics around MM 1b are also dominated by a Keplerian disk" (4.3 Mass estimates from the dust emission)
   - fitting: _not stated_
   - validation: _not stated_

## Software

- **CASA** 5.1.1: Calibration, imaging, analysis  
  > "Calibration, imaging and analysis were performed with CASA version 5.1.1" (Observations)
- **CASSIS** : LTE radiative transfer and MCMC fit of CH3CN ladder  
  > "We utilise the CASSIS local thermodynamic equilibrium (LTE) radiative transfer package." (4.2 Physical conditions toward MM 1b)
- **Astropy** : listed in acknowledgments/software  
  > "ASTROPY (cite: astropy_2013), APLPY (cite: aplpy_2012), CASA (cite: mcmullin_2007), CASSIS" (Software)
- **APLpy** : plotting  
  > "APLpy, an open-source plotting package for Python" (Acknowledgments)

## Numeric results

| quantity | value | uncertainty | units | step | quote |
|---|---|---|---|---|---|
| MM 1a main disk size | 0.141 x 0.050 | 0.002 | arcsec | 1 | $0.141\times0.050$ ($0.002$) \[+129.4 (0.1)\] |
| MM 1a main disk integrated flux density | 53.2 | 0.6 | mJy | 1 | 53.2 (0.6) |
| MM 1b integrated flux density | 2.5 | 0.2 | mJy | 1 | 2.5 (0.2) |
| MM 1a–1b separation | 0.57 (1920 au) | not stated | arcsec | 1 | Situated 0.57$''$ (1920 au) to the South-East of MM 1a |
| Enclosed mass MM 1a | 40 | ±5 | Msun | 2 | the total enclosed mass in MM 1a is $40\pm5$ M$_{\odot}$ |
| Best-fit outer radius | 850 | not stated | au | 2 | $R_{\rm out} = 850$ au and $M_{\rm enc} = 40$ M$_{\odot}$ |
| CH3CN Tex at MM 1b | 128 | not stated | K | 3 | $T_{\mathrm{ex}} = 128$ K |
| CH3CN column density at MM 1b | 3e16 | not stated | cm^-2 | 3 | $N_{\rm mol}  =  3\times10^{16}$ cm$^{-2}$ |
| Disk mass components i–iii | 2.2–5.8 | not stated | Msun | 4 | the total mass of continuum components $i$–$iii$ ranges from 2.2 – 5.8 M$_{\odot}$ |
| MM 1b mass | 0.06–0.6 | not stated | Msun | 4 | the mass of MM 1b ranges from 0.06 – 0.6 M$_{\odot}$ |
| Mass ratio MM1b/MM1a | ~0.015 | not stated | dimensionless | 5 | unequal mass ratio ($q \sim 0.015$) |
| Hill radius of MM 1b | ~330 | not stated | au | 5 | \sim 330\,{\rm au} |

## Qualitative findings

- K=3 line traces rotating gas in the outflow cavity, while v8=1 shows Keplerian rotation  
  > "the $v$8=1 line shows a clearly-resolved Keplerian rotation signature" (abstract)

## Claim tuples

- H: MM 1a hosts a Keplerian disk around a proto-O star | E: PV diagram of CH3CN v8=1 compared with Keplerian+infall model, inclination from continuum | R: Menc = 40±5 Msun with R_out=850 au; disk mass 2.2–5.8 Msun | F: Keplerian disk around ~34 Msun central object | **supported**
- H: MM 1b formed by disk fragmentation | E: Continuum and CH3CN modelling of MM 1b, mass ratio, Hill sphere, orbital sense | R: MM 1b <0.6 Msun, q~0.015, orbits in same sense, within Hill sphere | F: MM 1b is likely a disk-fragmentation companion | **partially**

## Reasoning

- Why this data: _not stated_
- Why this method: _not stated_
- Alternative: Fragmentation of turbulent cores gives close binaries without extreme mass ratios (q≳0.3)  
  > "these binaries do not possess extreme mass ratios ($q \gtrsim 0.3$, (cite: bate_2002))" (4.4 The MM 1a & b system: a result of disk fragmentation?)
- How they decided it was enough: _not stated_
- Limitation (authors): By-eye PV fit cannot account for beam convolution  
  > "We note that this process is unable to account for beam convolution effects" (4.1 Mass estimates from the gas kinematics)
- Caveat (inferred, ours): Mass of MM 1a rests on by-eye fit with inclination from assumed flat disk
- Caveat (inferred, ours): Dust temperatures and opacity bracketed, strongly affecting disk masses
- Caveat (inferred, ours): MM 1b kinematics from a single LTE fit and assumed Keplerian disk
- Caveat (inferred, ours): No formal uncertainty on CASSIS fit

## Reproducibility

- Data public (paper): ALMA project ID cited; public status not explicitly stated  
  > "This paper makes use of the following ALMA data: ADS/JAO.ALMA#2016.1.01147.S." (Acknowledgments)
- Products in archive: _not stated_
- Missing: Imaging parameters (cell, size, masks, threshold)
- Missing: Line-free channels and Brogan method specifics
- Missing: PV model by-eye criteria
- Missing: CASSIS input setup
- Data volume (inferred): ~50-200 GB raw for one C40-7 execution with four SPWs
- Score (inferred): 3/5, Data identified and many numbers given, but imaging details and by-eye fitting limit exact reproduction.
- Rediscovery candidate: no, Key mass result depends on a by-eye fit and unstated imaging settings.

## Links

- Method: (cite: brogan_2018) (continuum subtraction method)
- Method: (cite: cesaroni_2011) (PV Keplerian model)
- Companion: (cite: ilee_2016) (earlier SMA study of MM 1)
- Companion: (cite: forgan_2016) (fragmentation models for MM 1)

## Checks

```json
{
 "quotes": 72,
 "quotes_ok": 72,
 "quote_pass_rate": 1.0,
 "quotes_too_long": 0,
 "unsupported_facts": 0,
 "project_codes": 1,
 "codes_not_in_text": [],
 "codes_not_in_obscore": [],
 "obscore_codes_not_in_card": [],
 "codes_printed_but_missing": [],
 "numeric_results": 12,
 "numeric_problems": 0,
 "fill": {
  "facts": 81,
  "stated": 54,
  "rate": 0.667
 },
 "evidence_ok": true
}
```
