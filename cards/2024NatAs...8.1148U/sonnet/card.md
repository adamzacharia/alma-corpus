# Support for fragile porous dust in a gravitationally self-regulated disk around IM Lup

`2024NatAs...8.1148U` | Nature Astronomy 2024 | first author: Ueda, Takahiro | arXiv: 2406.07427 | DOI: 10.1038/s41550-024-02308-6

Card schema 1.0 | model claude-sonnet-5-5 | depth light | type theory_or_simulation_compared_to_alma

## Science

- Fields: protoplanetary_disks
- Question: Can a gravitationally self-regulated disk model with fragile, porous dust and accretion heating explain the IM Lup disk observations from near-infrared to millimeter wavelengths?  
  > "we develop a theoretical model of dust evolution in the gravitationally self-regulated (GSR) disk around IM Lup." (Introduction)
- Target **IM Lup**: coordinates _not stated_; z/distance _not stated_; distance from _not stated_

## Data provenance

- ALMA projects: _none stated_
- bands: MAPS: Band 6 (1.15 mm) and Band 3 (3.00 mm); DSHARP 1.25 mm; polarization at Bands 6 and 7  
  > "The MAPS observations are at $\lambda=1.15$ (ALMA Band 6) and 3.00 mm (Band 3)" (3.1 Millimeter dust thermal emission)
- frequencies and spectral setup: _not stated_
- continuum bandwidth: _not stated_
- arrays: _not stated_
- configurations: _not stated_
- baselines: _not stated_
- angular resolution: MAPS 0.24" (~38 au); DSHARP ~0.044" (~7 au)  
  > "have angular resolution of 0$\mbox{$.\!\!^{\prime\prime}$}$24, corresponding to the spatial resolution of $\sim38$ au." (3.1 Millimeter dust thermal emission)
- max recoverable scale: _not stated_
- sensitivity: _not stated_
- time on source: _not stated_
- observing dates: _not stated_
- pi or archival as stated: _not stated_
- Other facility **VLT/SPHERE**: H-band polarized scattered light image of IM Lup  
  > "polarized scattered light obtained from our models and the observation with VLT/SPHERE (cite: Avenhaus+18)" (3.3 Infrared scattered light)
- External data: ALMA MAPS multiwavelength continuum (Bands 6 and 3)  
  > "Fig. [2](#fig:fiducial) compares our models with porous ($f=0.2$) dust and the ALMA MAPS observations (cite: Sierra+21)." (3.1 Millimeter dust thermal emission) [from Sierra+21]
- External data: ALMA DSHARP 1.25 mm continuum  
  > "taken by the ALMA DSHARP program ($\lambda=1.25$ mm) (cite: Andrews+18)" (3.1 Millimeter dust thermal emission) [from Andrews+18]
- External data: ALMA polarization observations Band 6 and Band 7  
  > "have been taken at Bands 6 (cite: Stephens+20) and 7 (cite: Hull+18)." (3.2 Millimeter polarized emission) [from Stephens+20; Hull+18]
- External data: 13CO brightness temperature  
  > "brightness temperature of the $^{13}{\rm CO}$ $J=$ 2–1 line emission measured by (cite: Law+21)" (3.4 Validity of our temperature model) [from Law+21]

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

- DSHARP dust opacity composition  
  > "The dust composition is based on the DSHARP model (cite: Birnstiel+18)" (4.3 Opacity model) [from Birnstiel+18]
- Gas exponential cutoff radius 385 au  
  > "We set the exponential cutoff radius of 385 au for the gas surface density (cite: Tazaki+23)." (4.1 Disk model) [from Tazaki+23]
- Inclination 47.5 deg, PA 144.5 deg  
  > "set to $47.5^{\circ}$ and $144.5^{\circ}$, respectively (cite: Huang+18)" (4.4 Imaging simulations) [from Huang+18]

### Not stated but needed to reproduce (our reading)

- Distance to IM Lup
- Exact stellar luminosity/temperature for stellar irradiation in thermal RT
- DustPy version and initial conditions details
- Stellar parameters for NIR imaging
- Observational image data products used for comparison are not identified by project code

## Analysis recipe

1. **Build gas disk model**: Gravitationally self-regulated surface density with Q=1.4; temperature from accretion heating plus external radiation  
  > "We assume that the overall temperature profile is determined as $$\begin{equation}T^{4}=T_{\rm GSR,acc}^4+T_{\rm ext}^{4}" (4.1 Disk model)
   - parameter: Mdot=10^-7.9 Msun/yr, M*=1.1 Msun, Text=15 K, kappa_R=0.5 cm2/g  
  > "We assume $\dot{M}=10^{-7.9}M_{\odot}~{\rm yr^{-1}}$ and $M_{*}=1.1M_{\odot}$" (4.1 Disk model)
   - fitting: _not stated_
   - validation: Compared with DSHARP brightness temperature  
  > "the brightness temperature obtained by the high angular resolution observation in the ALMA DSHARP Program (cite: Andrews+18) is higher than the midplane temperature obtained from the radiative transfer simulation considering only stellar irradiation" (Methods, Disk model)
2. **Dust evolution simulations**: DustPy with vf as free parameter, porosity 0 or 0.8, 1 Myr  
  > "The simulations are performed up to $1~{\rm Myr}$, corresponding to the age of IM Lup." (4.2 Simulations of dust evolution)
   - software: DustPy
   - parameter: 1-1000 au in 100 radial bins; 1e-12 to 1e8 g, 10 bins per decade  
  > "The simulated domain ranges from 1 to 1000 au in the radial direction, with logarithmically separated into 100 bins." (4.2 Simulations of dust evolution)
   - assumption: alpha_turb = alpha_acc; dust-to-gas 0.01  
  > "We assume $\alpha_{\rm turb}=\alpha_{\rm acc}$ and $\alpha_{\rm z}=\alpha_{\rm acc}/3$." (Parameter uncertainties, Ratio between alpha_acc, alpha_turb and alpha_z)
   - fitting: _not stated_
   - validation: _not stated_
3. **Synthetic images and comparison**: RADMC-3D Monte Carlo imaging with Optool opacities (DSHARP composition, Bruggeman, DHS fmax=0.8), smoothed to the observing beam, compared to ALMA and SPHERE  
  > "The obtained synthetic images are smoothed by a Gaussian function corresponding to the observing beam of the actual observation." (4.4 Imaging simulations)
   - software: RADMC-3D, Optool
   - parameter: 1e7 photon packages (continuum), 1e9 (ALMA polarization), 1e11 (NIR)  
  > "For the ALMA polarization images and NIR images, we use $10^{9}$ and $10^{11}$ photon packages, respectively." (4.4 Imaging simulations)
   - fitting: _not stated_
   - validation: Tested temperature model with thermal radiative transfer  
  > "we investigate the validity of our temperature model by performing thermal radiative transfer simulations based on the dust distribution obtained from our numerical simulations." (Comparison with observations, Validity of our temperature model)

## Software

- **DustPy** : dust evolution simulations  
  > "We perform simulations of dust evolution based on the analytical disk model using Dustpy (cite: Stammler+22)." (4.2 Simulations of dust evolution)
- **RADMC-3D** : synthetic images and thermal radiative transfer  
  > "We conduct radiative transfer simulations using RADMC-3D (cite: RADMC) to generate synthetic images" (4.3 Opacity model)
- **Optool** : dust opacities  
  > "dust opacities are calculated with Optool (cite: Optool)" (4.3 Opacity model)

## Numeric results

| quantity | value | uncertainty | units | step | quote |
|---|---|---|---|---|---|
| Observed polarized-to-total NIR flux ratio vs model (vf=0.3) | 0.65 | observed 0.66±0.05% | percent | 3 | is 0.65, 0.67, 0.47 and 0.26% for $v_{\rm f}=0.3$, 1, 3 and $10~{\rm m~s^{-1}}$ |
| Total gas mass within 385 au | ~0.44 | not stated | Msun | 1 | The total gas mass within 385 au is $\sim0.44 M_{\odot}$ ($\sim0.4 M_{*}$) |
| Model alpha_acc at >30 au | ~2e-3 | not stated | dimensionless | 1 | Our theoretical model predicts $\alpha_{\rm acc}\sim2\times10^{-3}$ at $\gtrsim30$ au |

## Qualitative findings

- Fragile dust (vf ≲ 1 m/s) and moderate porosity (f~0.2) explain mm and polarization data; accretion heating explains inner brightness and 100 au shadow.  
  > "Our findings underscore the importance of dust fragility in retaining the observed millimeter emission" (abstract)

## Claim tuples

- H: Dust must be fragile to reproduce mm emission in a GSR disk | E: Compare DustPy+RADMC-3D models with MAPS/DSHARP intensity | R: vf ≲ 1 m/s within 70% up to 200 au; 130% for 3 and ~1000% for 10 m/s | F: dust is fragile | **supported**
- H: Dust is moderately porous | E: Compare synthetic polarization with Band 6/7 data | R: Porous 0.85-0.40% at Band 7 vs compact 0.42-0.10%; observed ~1% | F: f~0.2 favored | **supported**
- H: Pebble accretion can form a planet at 100 au | E: Pebble accretion growth timescale for 3 Earth-mass | R: ≳1e7 yr for vf ≲ 1 m/s | F: unlikely in smooth disk | **supported**

## Reasoning

- Why this data: _not stated_
- Why this method: _not stated_
- How they decided it was enough: _not stated_
- Limitation (authors): Dust composition uncertain; MRI/wind accretion not modeled; model underestimates intensity beyond 200 au  
  > "Our model underestimates the millimeter intensity at $\gtrsim200$ au" (5.3 Implications for disk chemistry)
- Caveat (inferred, ours): Model is tuned (kappa_R, Text) to match data
- Caveat (inferred, ours): Parameter degeneracies with composition
- Caveat (inferred, ours): No quantitative fit statistics

## Reproducibility

- Data public (paper): Observational data published in cited refs; simulation outputs and code on request  
  > "The observational data used in this work are published in refs (cite: Andrews+18; Avenhaus+18; Oberg+21; Hull+18; Stephens+20)." (Data availability)
- Products in archive: _not stated_
- Code: Available on reasonable request  
  > "The numerical codes are available from the corresponding author upon reasonable request." (Code availability)
- Missing: Model code
- Missing: Stellar irradiation parameters
- Missing: Exact image products
- Data volume (inferred): small (published images); simulations heavy
- Score (inferred): 3/5, Model well described but code not public and ALMA data are only comparison.
- Rediscovery candidate: no, Theory paper requiring unreleased code.

## Links

- Method: Stammler+22 (DustPy)
- Method: Birnstiel+18 (DSHARP opacity model)
- Companion: Sierra+21 (MAPS continuum)
- Related: DSHARP
- Related: MAPS

## Checks

```json
{
 "quotes": 34,
 "quotes_ok": 34,
 "quote_pass_rate": 1.0,
 "quotes_too_long": 0,
 "unsupported_facts": 0,
 "project_codes": 0,
 "codes_not_in_text": [],
 "codes_not_in_obscore": [],
 "obscore_codes_not_in_card": [
  "2016.1.00484.L",
  "2016.1.00712.S",
  "2018.1.01055.L",
  "2018.1.01172.S"
 ],
 "codes_printed_but_missing": [],
 "numeric_results": 3,
 "numeric_problems": 0,
 "fill": {
  "facts": 70,
  "stated": 27,
  "rate": 0.386
 },
 "evidence_ok": true
}
```
