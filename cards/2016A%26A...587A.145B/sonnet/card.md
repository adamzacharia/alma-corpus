# A young bipolar outflow from IRAS 15398-3359

`2016A&A...587A.145B` | Astronomy and Astrophysics 2016 | first author: Bjerkeli, P. | arXiv: 1601.06947 | DOI: 10.1051/0004-6361/201527310

Card schema 1.0 | model claude-sonnet-5-5 | depth light | type multi_facility_alma_minor

## Science

- Fields: star_formation, astrochemistry
- Question: Determine the spatial distribution and kinematics of species toward IRAS 15398-3359, the nature of infalling and outflowing gas, and the physical properties of the outflow  
  > "From the kinematical information of the emission lines we aim at determining the nature of the infalling and outflowing gas in the system. We also aim at determining the physical properties of the outflow." (abstract)
- Target **IRAS 15398-3359**: coordinates phase centre RA(J2000) 15h43m02.16s, Dec -34d09m09.0s (SMA)  
  > "is located in the Lupus I cloud (cite: Jorgensen:2013lr) at a distance of 155 pc (cite: Lombardi:2008lr)" (1 Introduction); "The phase centre of the observations was in both cases, $\alpha_{2000}$ = +15$^{\rm h}$43$^{\rm m}$02$\stackrel{^{\rm" (2 Observations); z/distance 155 pc  
  > "is located in the Lupus I cloud (cite: Jorgensen:2013lr) at a distance of 155 pc (cite: Lombardi:2008lr)" (1 Introduction); "The phase centre of the observations was in both cases, $\alpha_{2000}$ = +15$^{\rm h}$43$^{\rm m}$02$\stackrel{^{\rm" (2 Observations); distance from Lombardi et al. 2008  
  > "is located in the Lupus I cloud (cite: Jorgensen:2013lr) at a distance of 155 pc (cite: Lombardi:2008lr)" (1 Introduction); "The phase centre of the observations was in both cases, $\alpha_{2000}$ = +15$^{\rm h}$43$^{\rm m}$02$\stackrel{^{\rm" (2 Observations)

## Data provenance

- ALMA projects: 2011.0.00628.S
- bands: ALMA: C2H N=4-3 at 349.4 GHz; SMA setups around 230 and 267 GHz  
  > "Those observations provide maps of the C$_2$H $N=4-3$ emission at 349.4 GHz with an angular resolution of approximately 0.5$^{\prime \prime}$." (2 Observations)
- frequencies and spectral setup: _not stated_
- continuum bandwidth: _not stated_
- arrays: _not stated_
- configurations: _not stated_
- baselines: _not stated_
- angular resolution: ALMA ~0.5 arcsec; SMA beams 2.4-4.5 arcsec  
  > "resulting in beam sizes of 2.4 – 4.5$^{\prime \prime}$" (2 Observations)
- max recoverable scale: _not stated_
- sensitivity: _not stated_
- time on source: _not stated_
- observing dates: SMA: 2009 April 29 and 2009 May 12  
  > "in 2009 April 29 and 2009 May 12, covering spectral setups at around 230 and 267 GHz, respectively" (2 Observations)
- pi or archival as stated: _not stated_
- Line: C2H N=4-3 (ALMA) (349.4 GHz)
- Line: 12CO 2-1 (SMA) (not stated)
- Other facility **Submillimeter Array (SMA)**: Primary dataset: CO isotopologues, HCO+, N2H+, N2D+ maps from archive  
  > "The data for IRAS 15398–3359 were obtained from the archive of the Submillimeter Array" (2 Observations)
- External data: Envelope density/velocity structure from best-fit model  
  > "The structure of the infalling envelope is based on the best-fit model presented in (cite: Mottram:2013qy)" (3.2.1 The model components) [from Mottram et al. 2013 (cite: Mottram:2013qy)]
- External data: Envelope temperature power law  
  > "the temperature at 175 AU is set to 30 K and follows a power-law with an exponent of 1.5 (cite: Jorgensen:2013lr)" (3.2.1 The model components) [from Jorgensen et al. 2013 (cite: Jorgensen:2013lr)]
- External data: Outflow inclination 20 deg  
  > "has an inclination angle of, $i$ = 20$^{\circ}$ (cite: Oya:2014kx) with respect to the plane of the sky" (3.2.1 The model components) [from Oya et al. 2014 (cite: Oya:2014kx)]

## Processing

### Calibration

- pipeline or manual: SMA data calibrated with standard recipes using IDL/MIR  
  > "calibrated using the standard recipes using the IDL/MIR software" (2 Observations)
- casa version: _not stated_
- pipeline version: _not stated_
- archive products used as is: _not stated_
- flux calibrator: _not stated_
- flux scale uncertainty: _not stated_
- self calibration: _not stated_

### Imaging

- task: Imaged with Miriad (SMA data)  
  > "imaged using Miriad (cite: Sault:1995jk)" (2 Observations)
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
- final beam: ~3 arcsec for CO (2-1)  
  > "The spatial resolution of the CO (2$-$1) observations presented here ($\sim$3$^{\prime \prime}$)" (3.2 Morphology)
- final rms: _not stated_

### Inherited from earlier work

- Details of ALMA C2H data taken from earlier paper  
  > "For further details about the ALMA data we refer to that paper." (2 Observations) [from Jorgensen et al. 2013 (cite: Jorgensen:2013lr)]
- Energetics method  
  > "When inferring the energetic parameters, we use the method suggested by (cite: Downes:2007lr)." (5.3 Physical properties) [from Downes & Cabrit 2007 (cite: Downes:2007lr)]

### Not stated but needed to reproduce (our reading)

- Miriad weighting, robust, cell and image size, clean parameters for SMA
- SMA gain/flux calibrators and flux uncertainty
- Line-free channels and continuum subtraction
- ALMA calibration and imaging details (in Jorgensen 2013)
- Velocity ranges for line wings and integration
- LIME settings beyond grid points and iterations (random seed, line width/turbulence)

## Analysis recipe

1. **Calibrate and image SMA archive data**: Calibrate with IDL/MIR, image with Miriad  
  > "calibrated using the standard recipes using the IDL/MIR software[^1] and imaged using Miriad" (2 Observations)
   - software: IDL/MIR, Miriad
   - fitting: _not stated_
   - validation: _not stated_
2. **3D LIME radiative transfer model of 12CO (2-1)**: Analytic envelope, outflow shell, bow shocks and cloud models run in LIME; synthetic cubes sampled with observed visibilities, inverted, cleaned and restored in Miriad; compared with observed profiles by eye  
  > "The synthetic images of the $^{12}$CO emission, are sampled with the observed visibilities, inverted, cleaned and finally restored, using Miriad." (4.2.2)
   - software: LIME, Miriad
   - parameter: 250 000 grid points, 16 iterations, image resolution 0.25 arcsec  
  > "For each model, 250 000 grid points are used and the number of iterations is set to 16 to ensure convergence of the level populations." (4.2.2)
   - assumption: CO abundance 1e-4; H2 ortho-to-para ratio 3  
  > "The CO abundance is set to 1$\,\times\,10^{-4}$ in all components in the model" (4.2.2)
   - fitting: No chi-square fit; models varied component by component  
  > "a full chi-square analysis is impracticable" (4.2.2)
   - validation: Qualitative comparison of spectra at central and one outflow position, and maps  
  > "The aim of this study is, therefore, not to reproduce the exact shape of the line profiles in every position of the map" (4.2.2)
3. **Derive outflow mass and energetics**: Optically thin LTE column density from line wings; dynamical time, momentum, kinetic energy, mechanical luminosity, mass-loss rate  
  > "In the optically thin regime, the integrated emission in the line wings can be converted to a column density, assuming LTE conditions and using standard techniques" (5.3)
   - assumption: Tex = 100 K, CO/H2 = 1e-4, inclination 20 deg  
  > "If we assume a typical excitation temperature of 100 K in the outflow (cite: van-Kempen:2009rw), and a CO/H$_2$ ratio of $10^{-4}$" (5.3)
   - fitting: _not stated_
   - validation: Compared with Yildiz et al. 2015 and Dunham et al. 2014  
  > "The inferred value is consistent with the estimates presented by (cite: Dunham:2014fk) and (cite: Yildiz:2015jk)" (5.3)

## Software

- **Miriad** : Imaging SMA data and processing synthetic LIME cubes  
  > "imaged using Miriad (cite: Sault:1995jk)" (2 Observations)
- **IDL/MIR** : SMA calibration  
  > "calibrated using the standard recipes using the IDL/MIR software" (2 Observations)
- **LIME** : 3D Monte-Carlo line radiative transfer model  
  > "we construct a 3D model of IRAS 15398–3359, using the Monte-Carlo code LIME (cite: Brinch:2010rm)" (4.2 Radiative transfer modeling)

## Numeric results

| quantity | value | uncertainty | units | step | quote |
|---|---|---|---|---|---|
| Outflow mass (total) | 3e-4 | not stated | Msun | 3 | these numbers correspond to a total outflow mass of 3$\,\times\,10^{-4}$ $M_{\odot}$ |
| Dynamical time-scale | 400-500 | not stated | yr | 3 | This gives a dynamical time-scale of the outflow between 400 and 500 years. |
| Systemic velocity | 5.5 | not stated | km/s | 0 | $\upsilon_{\rm{sys}}$ = +5.5 $\mathrm{km \, s^{-1}}$ |
| Mass-loss rate | ~7e-8 | not stated | Msun/yr | 3 | we derive a mass-loss rate, $\sim$7$\,\times\,10^{-8}$ $M_{\odot}$ yr$^{-1}$ |
| Mechanical luminosity | ~1e-3 | not stated | Lsun | 3 | the mechanical luminosity is estimated at a slightly lower value, $\sim$1$\,\times\,10^{-3}$ $L_{\odot}$ |

## Qualitative findings

- N2D+ is found in a ridge not associated with the outflow; N2H+ is absent toward the protostar  
  > "N$_2$D$^+$ is detected in a ridge south-west from the protostellar condensation and is not associated with the outflow." (abstract)

## Claim tuples

- H: Is the source very young? | E: Outflow extent, knots and dynamical time from SMA CO | R: Dynamical time 400-500 yr; knots spaced ~100 yr | F: Source younger than ~1000 years | **supported**
- H: Which components explain the 12CO line profiles? | E: LIME models M1-M4 with varied components | R: Infall plus outflow (M3) reproduces central absorption and morphology | F: Infalling envelope plus outflow needed; cloud and shocks minor | **supported**

## Reasoning

- Why this data: _not stated_
- Why this method: _not stated_
- Alternative: Pure infall (M1) and pure outflow (M2) cannot explain the line profiles  
  > "On the other hand, a pure outflow scenario (where no infall of gas is present) cannot explain the observed line profiles either." (4.2.2)
- How they decided it was enough: _not stated_
- Limitation (authors): Lack of single-dish data prevents quantifying short-spacing loss  
  > "the lack of single-dish data prevents us from putting quantitative numbers on the effect of loss of short-spacings" (4.1)
- Caveat (inferred, ours): Model parameters are hand-tuned without a goodness-of-fit metric
- Caveat (inferred, ours): Mass is a lower limit and depends on assumed Tex
- Caveat (inferred, ours): Main data are SMA; ALMA is only used for C2H shell thickness

## Reproducibility

- Data public (paper): SMA data from the SMA archive; ALMA Cycle 0 project cited  
  > "The data for IRAS 15398–3359 were obtained from the archive of the Submillimeter Array" (2 Observations)
- Products in archive: _not stated_
- Missing: Miriad imaging parameters
- Missing: Exact velocity ranges for mass/momentum
- Missing: LIME input scripts
- Data volume (inferred): small (<10 GB SMA plus optional ALMA band 7 C2H)
- Score (inferred): 3/5, Model parameters are tabulated, but imaging and analysis details are sparse and the model comparison is qualitative.
- Rediscovery candidate: no, Data are mainly SMA and the recipe is incomplete; results are comparison by eye.

## Links

- Method: Brinch & Hogerheijde 2010 (cite: Brinch:2010rm) (LIME code)
- Companion: Jorgensen et al. 2013 (cite: Jorgensen:2013lr) (Original presentation of the ALMA C2H data)
- Companion: Oya et al. 2014 (cite: Oya:2014kx) (ALMA Cycle 0 H2CO, inclination and disk)

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
 "numeric_results": 5,
 "numeric_problems": 0,
 "fill": {
  "facts": 67,
  "stated": 32,
  "rate": 0.478
 },
 "evidence_ok": true
}
```
