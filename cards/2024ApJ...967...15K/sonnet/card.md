# Infall Motions in the Hot Core Associated with the Hypercompact H II Region G345.0061+01.794 B

`2024ApJ...967...15K` | The Astrophysical Journal 2024 | first author: Komesh, Toktarkhan | arXiv: 2307.07459 | DOI: 10.3847/1538-4357/ad3e7b

Card schema 1.0 | model claude-sonnet-5-5 | depth full | type observational_alma_primary

## Science

- Fields: star_formation, astrochemistry
- Question: What are the physical and kinematical characteristics of the hot molecular core around the HC HII region G345.0061+01.794 B, and is it rotating and infalling?  
  > "in order to investigate the physical and kinematical characteristics of its surroundings." (abstract)
- Target **G345.0061+01.794 B (G345.01 B)**: coordinates phase center (J2000) 16h56m47s, -40d14m25s  
  > "In this study, we adopt the spectrophotometric distance of 2.38 kpc" (1 Introduction); "The phase center of the array was (RA, Dec, J2000) = (16$^h$56$^m$47$^s$, –40$^\circ$14$^\prime$25$\ensuremath{''}$)." (2 Observations); z/distance 2.38 kpc  
  > "In this study, we adopt the spectrophotometric distance of 2.38 kpc" (1 Introduction); "The phase center of the array was (RA, Dec, J2000) = (16$^h$56$^m$47$^s$, –40$^\circ$14$^\prime$25$\ensuremath{''}$)." (2 Observations); distance from spectrophotometric distance (Moisés et al. 2011)  
  > "In this study, we adopt the spectrophotometric distance of 2.38 kpc" (1 Introduction); "The phase center of the array was (RA, Dec, J2000) = (16$^h$56$^m$47$^s$, –40$^\circ$14$^\prime$25$\ensuremath{''}$)." (2 Observations)

## Data provenance

- ALMA projects: 2015.1.01371.S
- bands: Band 6, 256.3-259.6 GHz  
  > "We observed, using ALMA in Band 6 between 256.3 and 259.6 GHz" (2 Observations)
- frequencies and spectral setup: Four spectral windows centered at 256.302035 (1875 MHz), 258.388716, 259.599448 (234.38 MHz each), 257.325 GHz (468.75 MHz)  
  > "We observed four spectral windows in dual polarization mode." (2 Observations)
- continuum bandwidth: _not stated_
- arrays: 12-m array  
  > "using the 12-m array" (2 Observations)
- configurations: _not stated_
- baselines: _not stated_
- angular resolution: about 0.52x0.40 arcsec, PA -65 deg  
  > "0.52$\times$0.40" (Table 1)
- max recoverable scale: _not stated_
- sensitivity: rms 3.8-4.4 mJy/beam per line; continuum sigma 0.3 mJy/beam  
  > "with $\sigma$ being 0.3 mJy/beam" (3.3 Dust continuum)
- time on source: 35 minutes  
  > "The integration time on source was 35 minutes." (2 Observations)
- observing dates: 21 May 2016, Cycle 3  
  > "The observations were carried out, as part of ALMA Cycle 3, during 21 May 2016" (2 Observations)
- pi or archival as stated: _not stated_
- Line: CH3CN J=14-13 ladder (~257.1-257.5 GHz)
- Line: SO2 30(4,26)-30(3,27) (259.599 GHz)
- Line: SO2 32(4,28)-32(3,29) (258.389 GHz)
- Line: H29alpha RRL (256.302 GHz (window center))
- External data: Free-free continuum parameters (EM and size) from fit to lower-frequency radio continuum, used to estimate S_ff  
  > "We estimate it using the parameters of the HC HII region (Emission Measure (EM) and size) derived by (cite: 2012ApJ...753...51G)" (3.2 Ionized gas) [from (cite: 2012ApJ...753...51G)]
- External data: Dust grain emissivity k_1.1mm = 0.0078 cm2/g  
  > "we adopt a grain emissivity, $k_\mathrm{1.1mm}$ = 0.0078 cm$^2$ g$^{-1}$" (3.3 Dust continuum) [from (cite: 1994A&A...291..943O)]
- External data: He+/H+ ratio 0.096  
  > "adopting a value of 0.096 for the $He^+$ to $H^+$ abundance ratio (cite: 1994ApJS...91..713M)" (3.2 Ionized gas) [from (cite: 1994ApJS...91..713M)]
- External data: Spectrophotometric distance 2.38 kpc  
  > "we adopt the spectrophotometric distance of 2.38 kpc (cite: 2011MNRAS.411..705M)" (1 Introduction) [from (cite: 2011MNRAS.411..705M)]

## Processing

### Calibration

- pipeline or manual: Calibration and reduction in CASA; details not given  
  > "Calibration and reduction of these data were done using the Common Astronomy and Software Applications" (2 Observations)
- casa version: _not stated_
- pipeline version: _not stated_
- archive products used as is: _not stated_
- flux calibrator: J1617-5848 (bandpass J1427-4206, phase J1717-3342)  
  > "J1427-4206 was used as bandpass calibrator, J1717-3342 was observed as phase calibrator, and J1617-5848 was measured as flux calibrators." (2 Observations)
- flux scale uncertainty: _not stated_
- self calibration: _not stated_

### Imaging

- task: tclean  
  > "These line-free channels in turn were used to create the continuum images directly in tclean." (2 Observations)
- deconvolver: _not stated_
- weighting robust: _not stated_
- uv taper: _not stated_
- cell size: _not stated_
- image size: _not stated_
- masking: _not stated_
- multiscale scales: _not stated_
- continuum subtraction: uvcontsub on line-free channels; continuum imaged in tclean  
  > "The continuum was subtracted by selecting the line free channels from the visibilities using the CASA task uvcontsub." (2 Observations)
- line free channels: _not stated_
- primary beam correction: _not stated_
- array combination: _not stated_
- smoothing: _not stated_
- final beam: 0.51-0.52 x 0.40 arcsec  
  > "0.52$\times$0.40" (Table 1)
- final rms: _not stated_

### Inherited from earlier work

- Infall model for central mass, infall velocity and radius from first-moment profile  
  > "we use the hallmark model of (cite: 2019A&A...626A..84E)" (4.3 Infall motions) [from (cite: 2019A&A...626A..84E)]
- Electron temperature formula under LTE  
  > "can be derived from the following expression (cite: 2002ASSL..282.....G) assuming local thermodynamic equilibrium (LTE) conditions" (3.2 Ionized gas) [from (cite: 2002ASSL..282.....G)]

### Not stated but needed to reproduce (our reading)

- CASA version and whether the pipeline or manual calibration was used
- Line-free channels chosen for uvcontsub
- Weighting/robust, cleaning threshold, masks, cell and image size
- Flux scale uncertainty
- Moment integration ranges and clipping for CH3CN and SO2
- MADCUBA fit settings (source size, linewidth, priors)
- Fitting procedure and free parameters of the infall model; fit weights
- How S_ff at 256 GHz was extrapolated from Guzmán et al. 2012

## Analysis recipe

1. **Image continuum and lines**: uvcontsub then tclean imaging; moment 0 and 1 maps, channel maps and PV diagrams  
  > "The continuum was subtracted by selecting the line free channels from the visibilities using the CASA task uvcontsub." (2 Observations)
   - software: CASA
   - fitting: _not stated_
   - validation: Blue spot present in all K components  
  > "The "blue spot" feature is present in all K components shown in Figure [2](#fig:mom345), confirming that its detection is a robust result." (3.1 CH3CN)
2. **Rotational temperature of CH3CN and SO2**: LTE rotational diagrams at the blue spot and in half-rings of width 0.15 arcsec; power-law fit of T_rot vs distance  
  > "The rings are centered at the peak position and have widths of 0$\,.\!\!^{\prime\prime}$15." (4.1 Rotational temperature)
   - software: MADCUBA
   - assumption: LTE  
  > "derived from the MAdrid Data CUBe Analysis (cite: 2019A&A...631A.159M) software assuming LTE." (4.1 Rotational temperature)
   - fitting: Power law T_rot = 154 r^(-0.35±0.19)  
  > "A power law fit to the observed dependence gives $T_\mathrm{rot} = 154\,r^{-0.35\pm0.19}$." (4.1 Rotational temperature)
   - validation: _not stated_
3. **Ionized gas properties from H29alpha**: Gaussian fits to H29alpha map and spectrum; T_e from line-to-continuum ratio; Mezger-Henderson equations for n_e, EM, mass, Lyman photons  
  > "Assuming that the HII region is spherical and homogeneous, using the values of the continuum flux density at 256 GHz (325$\pm$65 mJy)" (3.2 Ionized gas)
   - assumption: Spherical homogeneous HII region, LTE, He+/H+=0.096  
  > "Assuming that the HII region is spherical and homogeneous" (3.2 Ionized gas)
   - fitting: Gaussian fits  
  > "A Gaussian fit to the line profile gives a linewidth of 33.7$\pm$2.3 km s$^{-1}$" (3.2 Ionized gas)
   - validation: _not stated_
4. **Dust mass**: Optically thin dust mass after subtracting free-free from total continuum  
  > "We estimate the dust continuum flux of 565$\pm$112 mJy by subtracting the contribution of the free-free emission of 325$\pm$65 mJy" (3.3 Dust continuum)
   - assumption: T_dust = 250 K, gas-to-dust 100, k=0.0078 cm2/g, D=2.38 kpc  
  > "Adopting $T_\text{dust}$ = 250 K (see Section [4.1](#sec:T_rot)), we derive a dust mass of $\sim$4 M$_{\odot}$" (3.3 Dust continuum)
   - fitting: _not stated_
   - validation: _not stated_
5. **Central mass from infall model**: Fit Estalella et al. 2019 model to first-moment radial profiles in 0.05 arcsec rings around the blue spot, for unblended K components  
  > "obtained for the unblended K components of the J=14–13 transition of $\rm CH_3CN$  by averaging the first-order moment in concentric rings of width 0$\,.\!\!^{\prime\prime}$05" (4.3 Infall motions)
   - assumption: Distance 2.38 kpc; also tested 1.7 kpc  
  > "we also fit this model using the near distance of 1.7 kpc" (4.3 Infall motions)
   - fitting: Best fit for infall radius much larger than beam; fit algorithm not stated  
  > "The best fit is obtained for an infall radius much larger than the beam size" (4.3 Infall motions)
   - validation: Compared with dynamical mass from velocity gradient (51 Msun)  
  > "it implies a dynamical mass within a 0.023 pc radius of 51 $M_{\odot}$" (3.1 CH3CN)

## Software

- **CASA** : Calibration, reduction, uvcontsub, tclean  
  > "Calibration and reduction of these data were done using the Common Astronomy and Software Applications" (2 Observations)
- **MADCUBA** : Rotational diagrams of CH3CN and SO2  
  > "we obtain the rotational temperature of the envelope with `MADCUBA`" (4.2 Rotational temperature of SO2)
- **astropy** : Listed in software section  
  > "astropy (cite: 2013A&A...558A..33A; 2018AJ....156..123A)" (Software)

## Numeric results

| quantity | value | uncertainty | units | step | quote |
|---|---|---|---|---|---|
| CH3CN T_rot at peak | 252 | ±24 | K | 2 | being 252$\pm24$ Kelvin at the peak position |
| CH3CN T_rot at edge | 166 | ±16 | K | 2 | 166$\pm16$ Kelvin at the edge |
| SO2 T_rot | 40 | ±6 | K | 2 | A linear fit to the observed trend implies a temperature of 40$\pm$6 Kelvin. |
| Electron temperature | 8094 | ±1534 | K | 3 | we get an electron temperature $T^*_e$=8094$\pm$1534 Kelvin |
| Emission measure | 4.6e8 | ±0.9e8 | pc cm^-6 | 3 | an emission measure of (4.6$\pm$0.9)$\times$10$^8$ pc cm$^{-6}$ |
| Ionized gas mass | 3.6e-3 | ±0.3e-3 | Msun | 3 | a mass of ionized gas (3.6$\pm$0.3)$\times$10$^{-3}$ $M_{\odot}$ |
| Dust mass | ~4 | not stated | Msun | 4 | we derive a dust mass of $\sim$4 M$_{\odot}$ (for a distance of 2.38 kpc) |
| Central mass from infall (2.38 kpc) | 172.8 | ±8.8 | Msun | 5 | a central mass of 172.8$\pm8.8 M_{\odot}$ (for a distance of 2.38 kpc |
| Central mass from infall (1.7 kpc) | 126.0 | ±8.7 | Msun | 5 | a central mass of 126.0$\pm8.7 M_{\odot}$ |
| H29alpha linewidth | 33.7 | ±2.3 | km/s | 3 | gives a linewidth of 33.7$\pm$2.3 km s$^{-1}$ |

## Qualitative findings

- Blueshifted spot at the zeroth-moment peak, a signature of infall, in all CH3CN K components and SO2 lines  
  > "show a central spot of blueshifted emission, with respect to the systemic velocity of the cloud, located at the peak of the zero-order moment" (5 Conclusion)

## Claim tuples

- H: Is the HC HII region surrounded by a hot, rotating, infalling molecular core? | E: CH3CN and SO2 moment maps, channel maps, PV diagrams, rotational diagrams and infall model fit | R: Velocity gradient 1.1 km/s/arcsec, blue spot, T_rot 252 to 166 K, central mass 172.8 Msun | F: A compact hot molecular core is rotating and infalling toward a central mass, likely confining the ionized gas | **supported**
- H: Is the molecular core internally heated? | E: CH3CN rotational diagrams in rings | R: T_rot falls with distance as r^-0.35 | F: Hot core internally excited by the central star | **supported**

## Reasoning

- Why this data: _not stated_
- Why this method: _not stated_
- Alternative: Far distance 14.7 kpc rejected as implausible  
  > "Choosing the far distance not only results in an unrealistically massive cluster" (1 Introduction)
- How they decided it was enough: _not stated_
- Limitation (authors): Errors do not include distance uncertainty or density gradients  
  > "The errors do neither include the distance uncertainty nor potentially strong density gradients" (3.2 Ionized gas)
- Caveat (inferred, ours): Central mass of ~170 Msun is much larger than the Lyman-photon mass and the dynamical mass; the model is a single-parameter-family fit to blended moments
- Caveat (inferred, ours): Beam of 0.5 arcsec (~1200 AU) barely resolves the blue spot
- Caveat (inferred, ours): Continuum free-free subtraction relies on extrapolation of the 2012 fit
- Caveat (inferred, ours): Lack of an explicit fitting method and error treatment

## Reproducibility

- Data public (paper): ALMA project data acknowledged; public status not explicitly stated  
  > "This paper makes use of the following ALMA data: ADS/JAO.ALMA#2015.1.01371.S." (Acknowledgements)
- Products in archive: _not stated_
- Missing: CASA version and imaging parameters
- Missing: Infall model fitting details
- Missing: MADCUBA configuration
- Missing: Line-free channel ranges
- Data volume (inferred): ~20-50 GB raw single execution block
- Score (inferred): 3/5, Public data and clear target, but imaging parameters and fitting details are missing
- Rediscovery candidate: no, Imaging and infall-fit recipe is incomplete.

## Links

- Method: (cite: 2019A&A...626A..84E) (Infall model for first-moment profile)
- Method: (cite: 2019A&A...631A.159M) (MADCUBA)
- Companion: (cite: 2012ApJ...753...51G) (Earlier radio continuum observations of G345.01 B)
- Related: Spitzer-GLIMPSE

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
 "numeric_results": 10,
 "numeric_problems": 0,
 "fill": {
  "facts": 74,
  "stated": 43,
  "rate": 0.581
 },
 "evidence_ok": true
}
```
