# Radiative transfer modelling of W33A MM1: 3D structure and dynamics of a complex massive star-forming region

`2018MNRAS.478.2505I` | Monthly Notices of the Royal Astronomical Society 2018 | first author: Izquierdo, Andrés F. | arXiv: 1804.09204 | DOI: 10.1093/mnras/sty1096

Card schema 1.0 | model claude-sonnet-5-5 | depth full | type archival_reuse

## Science

- Fields: star_formation
- Question: Can a composite 3D radiative transfer model (disc-envelope systems, envelopes and filaments) reproduce the ALMA CH3CN and dust continuum emission of W33A MM1 and reveal its structure and dynamics?  
  > "we present a multiple-component radiative transfer model that aims at reproducing the main features observed with ALMA in the high-mass star formation core W33A MM1" (Introduction)
- Target **W33A MM1**: coordinates _not stated_; z/distance 2.4 (+0.17/-0.15) kpc  
  > "Its parallax distance to the Sun has been measured to be $2.4^{+0.17}_{-0.15}$ kpc (cite: Immer13)." (Introduction); distance from parallax (Immer13)  
  > "Its parallax distance to the Sun has been measured to be $2.4^{+0.17}_{-0.15}$ kpc (cite: Immer13)." (Introduction)

## Data provenance

- ALMA projects: 2012.1.00784.S
- bands: Band 7 (0.8 mm) and Band 6 (1.3 mm) continuum; CH3CN J=19-18 K=4 and K=8 in Band 7  
  > "we selected the CH$_3$CN $J=19-18$ $K=4$ and $K=8$ lines, as well as the 0.8 mm (Band 7) continuum." (2 Observational Data)
- frequencies and spectral setup: _not stated_
- continuum bandwidth: _not stated_
- arrays: _not stated_
- configurations: _not stated_
- baselines: _not stated_
- angular resolution: 0.21x0.14 arcsec (0.86 mm); 0.33x0.24 arcsec (1.36 mm); 0.20x0.14 arcsec (CH3CN)  
  > "The 0.86 mm (349.454 GHz) continuum image has an FWHM $=0.21\times0.14$ arcsec, PA $=-80.9^\circ$" (2 Observational Data)
- max recoverable scale: _not stated_
- sensitivity: continuum rms 112 uJy/beam (1.3 mm), 177 uJy/beam (0.8 mm); K4 3.7 mJy/beam, K8 2.1 mJy/beam in 0.42 km/s channels  
  > "Their noise levels are $\sigma_\mathrm{rms,K4} \approx 3.7~$mJy beam$^{-1}$ (1.28 K) and $\sigma_\mathrm{rms,K8} \approx 2.1~$mJy beam$^{-1}$ (0.73 K)" (2 Observational Data)
- time on source: _not stated_
- observing dates: executed June 2015  
  > "they were not successfully executed until June 2015" (2 Observational Data)
- pi or archival as stated: PI M. G. Hoare; data previously presented in Maud+17  
  > "For more details of the data set we refer to (cite: Maud+17)." (2 Observational Data)
- Line: CH3CN J=19-18 K=4 (349.3463 GHz)
- Line: CH3CN J=19-18 K=8 (349.0249 GHz)
- Other facility **SMA**: Earlier sub-arcsecond observations and disc/mass estimates for comparison  
  > "Previous sub-arcsecond Submillimeter Array (SMA) observations pointed toward the existence of a massive gaseous disc of a few $M_\odot$" (Introduction)
- Other facility **Herschel**: SED-fit images of W33 (Lin16) used to measure bolometric luminosity  
  > "We requested their W33 images and measured the bolometric luminosity within one beam area around the W33A peak" (5.3 The protostellar objects)
- External data: Parallax distance 2.4 kpc  
  > "Its parallax distance to the Sun has been measured to be $2.4^{+0.17}_{-0.15}$ kpc (cite: Immer13)." (Introduction) [from Immer13]
- External data: Temperature map and ALMA observational constraints for MM1  
  > "consistent with the temperature map presented in (cite: Maud+17)" (3.5 Determination of model parameters) [from Maud+17]
- External data: 7 mm source fluxes used to subtract free-free emission  
  > "extrapolating the fluxes of the 7 mm sources in (cite: vdTMenten05)" (4.2 (Sub)millimeter dust continuum) [from vdTMenten05]
- External data: Dust opacity normalization kappa0=0.5 cm2/g at 220 GHz  
  > "a normalization $\kappa_0 = 0.5$ cm$^2$ g$^{-1}$ at 220 GHz as in (cite: GM10)" (4.2 (Sub)millimeter dust continuum) [from GM10]

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

- task: CASA simobserve then clean applied to model images (models only)  
  > "The task ‘simobserve’ was first used to generate visibilities from the model images." (3.3 Radiative transfer simulations)
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

- ALMA data reduction and imaging  
  > "For more details of the data set we refer to (cite: Maud+17)." (2 Observational Data) [from Maud+17]
- Disc-envelope prescription (Ulrich envelope plus flared disc)  
  > "We implemented a standard YSO modelling for the four disc-envelope sources, following the approach of (cite: KetoZhang10)." (3.1.1 Compact Sources) [from KetoZhang10]
- Envelope temperature law T ∝ r^-0.33  
  > "For the temperature of the envelope we follow (cite: Whitney03) and assume $T_{\rm env}(r)\propto r^{-0.33}$." (3.1.1 Compact Sources) [from Whitney03]
- Dust opacity law normalization  
  > "a normalization $\kappa_0 = 0.5$ cm$^2$ g$^{-1}$ at 220 GHz as in (cite: GM10)" (4.2 (Sub)millimeter dust continuum) [from GM10]

### Not stated but needed to reproduce (our reading)

- Calibrated measurement sets or imaging parameters (robust, cleaning, masks) for the ALMA cubes; deferred to Maud+17
- LIME settings: number of grid points (pIntensity values), sink points, image pixel sizes and channel setup
- simobserve array configurations, integration times, PWV values
- Exact apertures' pixel definitions and centres for spectra extraction
- Stellar parameters beyond table (e.g. density/profile for source E)
- Criteria for the 'good match' since fitting was by trial and error

## Analysis recipe

1. **Select data and estimate initial source parameters**: Inspect channel maps, fit Gaussians to spectra, estimate Keplerian mass M=Δv²r/G  
  > "we made a first estimation of the central mass assuming Keplerian rotation as in $M_\star = \Delta v^2 r / G$." (3.5 Determination of model parameters)
   - parameter: Initial inclination 45 deg for sources without prior constraint  
  > "we started with the assumption of $i=45^\circ$ and varied it until we achieved a line-width that matched the observed." (3.5 Determination of model parameters)
   - fitting: _not stated_
   - validation: _not stated_
2. **Build composite 3D physical model on global grid**: Superpose Ulrich envelopes, Pringle discs, cylindrical and parabolic filaments on a 301^3 cubic grid over 7000 au  
  > "it has 301 nodes distributed in equal steps over 7000 au in each direction" (3.2.1 Global grid)
   - software: Python model library
   - parameter: Grid resolution 23.3 au  
  > "its linear resolution is 23.3 au" (3.2.1 Global grid)
   - assumption: Gas-to-dust mass ratio 100; dust opacity kappa=0.5 (nu/220 GHz)^1.7 cm2/g; LTE  
  > "The gas-to-dust mass ratio was set to 100 in the entire global grid." (3.3 Radiative transfer simulations)
   - fitting: _not stated_
   - validation: _not stated_
3. **Radiative transfer of line and continuum**: LIME LTE calculation of CH3CN and dust; ten continuum images median-combined  
  > "we generated ten images with the same set of parameters. Then we extracted the median of the intensity for each pixel" (3.3 Radiative transfer simulations)
   - software: LIME 1.6.1
   - assumption: LTE justified by n_crit ~1e7 cm-3  
  > "We use LTE calculations for our modelling." (3.3 Radiative transfer simulations)
   - fitting: _not stated_
   - validation: _not stated_
4. **Simulate ALMA observations of model**: simobserve then clean with matched configuration and conditions  
  > "The simulated and observed images have noise levels and beam sizes matching each other within a few percent." (3.3 Radiative transfer simulations)
   - software: CASA 4.4.0
   - fitting: _not stated_
   - validation: _not stated_
5. **Iterate parameters by trial and error against data**: Intuition-guided trial and error, primarily comparing CH3CN K=4 and 0.8 mm continuum; K=8 and 1.3 mm as a-posteriori checks  
  > "We emphasize that our method was intuition-guided trial and error." (3.5 Determination of model parameters)
   - fitting: No formal fit, sampler or likelihood  
  > "We emphasize that the final model is not unique nor a best fit" (3.1 Physical models)
   - validation: Compare spectra, moment maps, channel maps and continuum intensities; K=8 and 1.3 mm as checks  
  > "whereas the $K=8$ line and 1.3 mm continuum were just used as a-posteriori checks." (3.5 Determination of model parameters)
6. **Derive spectral indices, luminosity and virial state**: Model and observed fluxes at 1.3 and 0.8 mm after free-free subtraction; accretion plus stellar luminosity; escape and rms velocity  
  > "Thus, the obtained model dust spectral indices are: $\alpha_\mathrm{spiral}=2.3$, $\alpha_\mathrm{central}=2.9$, and $\alpha_\mathrm{MM1}=2.5$." (4.2 (Sub)millimeter dust continuum)
   - assumption: Teff ~1e4 K for the bloated protostar; free-free spectral index 1  
  > "Considering $T_{eff} \approx 10^4$ K, the corresponding stellar luminosity is $L_\star \approx 7.9 \times 10^3~L_\odot$." (5.3 The protostellar objects)
   - fitting: _not stated_
   - validation: Compared Main luminosity with W33A luminosity from literature and Herschel-based MM1+MM2  
  > "We obtain $L_\mathrm{MM1+MM2} \approx 1.8\times10^4~L_\odot$." (5.3 The protostellar objects)

## Software

- **LIME** 1.6.1: 3D line and dust radiative transfer of model  
  > "We use version 1.6.1 of the Line Modelling Engine code (cite: Brinch+10)" (3.3 Radiative transfer simulations)
- **CASA** 4.4.0: simobserve and clean to apply ALMA response  
  > "using version 4.4.0 of CASA (cite: McMullin07)" (3.3 Radiative transfer simulations)
- **LAMDA database** : molecular data for CH3CN  
  > "LIME retrieves molecular data from the LAMDA database (cite: Schoier+05)." (3.3 Radiative transfer simulations)
- **Python (Numpy, Matplotlib, Astropy, IPython, Pandas); star-forming-regions package** : model-generation libraries and plotting  
  > "we used specific Python packages to achieve the modelling: Numpy (cite: Numpy), Matplotlib (cite: Matplotlib), Astropy (cite: Astropy), IPython (cite: IPython) and Pandas (cite: Pandas)." (Additional software)

## Numeric results

| quantity | value | uncertainty | units | step | quote |
|---|---|---|---|---|---|
| Main stellar mass | 7 | not stated | Msun | 5 | Stellar mass ($M_*$) \[M$_{\odot}$\] / 7.0 |
| Main total gas mass (disc+envelope) | 0.393 | not stated | Msun | 5 | Total mass of gas ($M_{\rm gas}$) \[M$_{\odot}$\] / 0.393 |
| Main centrifugal/disc radius | 152 | not stated | au | 5 | Centrifugal radius ($R_{\rm d}$) \[AU\] / 152 |
| Main total luminosity | 1.1e4 | not stated | Lsun | 6 | Thus, our model gives a total luminosity for Main $L_\mathrm{Main} \approx 1.1 \times 10^4~L_\odot$. |
| Spiral filament gas mass | 0.41 | not stated | Msun | 5 | The total gas mass in the model ‘feeding’ filament is 0.41 $M_\odot$, and its average flow rate is $4.75\times10^{-5}~M_\odot$ yr$^{-1}$. |
| Spiral filament mass inflow rate | 4.75e-5 | not stated | Msun/yr | 5 | its average flow rate is $4.75\times10^{-5}~M_\odot$ yr$^{-1}$ |
| Model dust spectral indices (spiral, central, MM1) | 2.3, 2.9, 2.5 | ±0.3 | dimensionless | 6 | $\alpha_\mathrm{spiral}=2.3$, $\alpha_\mathrm{central}=2.9$, and $\alpha_\mathrm{MM1}=2.5$ |
| Observed dust spectral indices (spiral, central, MM1) | 2.0, 2.3, 2.2 | ±0.3 | dimensionless | 6 | The observational spectral indices are: $\alpha_\mathrm{spiral}=2.0$, $\alpha_\mathrm{central}=2.3$, and $\alpha_\mathrm{MM1}=2.2$. |
| 1D rms velocity dispersion of source systemic velocities | 1.5 | not stated | km/s | 6 | is $\approx 1.5$ km s$^{-1}$ |
| Escape velocity of MM1 core (radius 3500 au) | 1.3 | not stated | km/s | 6 | the 1D escape velocity of the MM1 core is $\approx 1.3$ km s$^{-1}$ |
| Stellar density | 1.8e5 | not stated | pc^-3 | 6 | an average (proto)stellar density of $1.8\times10^5$ pc$^{-3}$ |

## Qualitative findings

- The north spiral-like feature is consistent with a filamentary accretion flow on a parabolic trajectory with radial infall.  
  > "The spiral-like filament converging to MM1 from the northwest can be convincingly interpreted as an accretion flow feeding the nascent stellar association." (6 Conclusions)

## Claim tuples

- H: Is MM1 a single massive star with a large disc or a multiple system? | E: Composite radiative transfer model compared with ALMA CH3CN and continuum | R: Six compact sources within ~1000 au; Main has 7 Msun and 0.4 Msun of gas with ~150 au disc | F: MM1 is a forming stellar association with a lower Main mass than earlier estimates | **supported**
- H: Does the spiral-like feature feed MM1 as an accretion flow? | E: Parabolic cylinder model with focus at the centre of mass plus radial infall | R: Reproduces velocity pattern; needs extra radial component for dispersion | F: Spiral-like feature is an accretion flow | **supported**
- H: Do gas flows exist between pairs of compact sources? | E: Added five cylindrical filaments to the model | R: Improved match to continuum elongations and line emission | F: Small flows proposed; two diagonal ones uncertain | **partially**
- H: Is the forming association virialized? | E: Compare escape velocity and dispersion of source systemic velocities | R: 1.3 km/s vs 1.5 km/s | F: Appears virialized | **supported**

## Reasoning

- Why this data: Chose less morphologically confused data and unblended lines  
  > "we modelled only the data that are less morphologically confused, and lines that do not appear to be spectroscopically blended or contaminated by others." (2 Observational Data)
- Why this method: _not stated_
- Alternative: Pure Keplerian disc and pure envelope for Main and S were rejected (double peaks or wrong intensities)  
  > "To model Main we first considered the simplest case of a pure Keplerian disc, but such model always produces double-peaked profiles" (4.1.1)
- How they decided it was enough: _not stated_
- Limitation (authors): Model is not unique nor a best fit  
  > "We emphasize that the final model is not unique nor a best fit" (3.1 Physical models)
- Limitation (authors): Model lacks extended emission and filaments are homogeneous  
  > "Our small model filaments are homogeneous and do not reproduce the clumpiness suggested by the data." (4.1.2)
- Caveat (inferred, ours): No formal fitting or uncertainties on parameters; degeneracies (inclination, cavity) acknowledged but not quantified
- Caveat (inferred, ours): Line-of-sight depth of filaments assumed equal to projected length
- Caveat (inferred, ours): Mass estimates depend on assumed CH3CN abundance and gas-to-dust ratio
- Caveat (inferred, ours): Resolution of 400 au cannot test the 150 au disc

## Reproducibility

- Data public (paper): Project code given; model code on GitHub  
  > "The package and its documentation are available through GitHub (<https://github.com/andizq/star-forming-regions>)." (Model Library)
- Products in archive: _not stated_
- Code: Model library at github.com/andizq/star-forming-regions  
  > "The package and its documentation are available through GitHub (<https://github.com/andizq/star-forming-regions>)." (Model Library)
- Missing: Reduced ALMA images/cubes (reduction in Maud+17)
- Missing: LIME and simobserve run parameters
- Missing: No objective fit criteria
- Data volume (inferred): ~tens of GB (Band 6 and 7 long-baseline measurement sets) or use of calibrated products
- Score (inferred): 3/5, Model code released and parameters tabulated, but the match was done by trial and error and the data processing is inherited.
- Rediscovery candidate: no, Results come from subjective trial-and-error modelling, not a deterministic recipe.

## Links

- Method: Brinch+10 (LIME code)
- Method: KetoZhang10 (disc-envelope model prescription)
- Companion: Maud+17 (original presentation of the ALMA data)

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
 "numeric_results": 11,
 "numeric_problems": 0,
 "fill": {
  "facts": 85,
  "stated": 44,
  "rate": 0.518
 },
 "evidence_ok": true
}
```
