# The ALMA survey to Resolve exoKuiper belt Substructures (ARKS): X. Interpreting the peculiar dust rings around HD 131835

`2026A&A...705A.204J` | Astronomy and Astrophysics 2026 | first author: Jankovic, M. R. | arXiv: 2601.11732 | DOI: 10.1051/0004-6361/202556637

Card schema 1.0 | model claude-sonnet-5-5 | depth light | type theory_or_simulation_compared_to_alma

## Science

- Fields: debris_disks
- Question: Why is the inner dust ring of HD 131835 brighter than the outer ring in ALMA thermal emission but fainter in SPHERE scattered light: two planetesimal belts with different properties, or gas-driven outward migration of small dust from a single belt?  
  > "We explore two scenarios that could explain these observations: the two dust rings might represent distinct planetesimal belts with different collisional properties" (abstract)
- Target **HD 131835**: coordinates _not stated_; z/distance 130 pc  
  > "an A-type star located at a distance of 130 pc (cite: Gaia2023) in the 15–16-Myr-old (cite: Mamajek2002; Pecaut2012) Upper Centaurus Lupus moving group" (Introduction); distance from Gaia (cite: Gaia2023)  
  > "an A-type star located at a distance of 130 pc (cite: Gaia2023) in the 15–16-Myr-old (cite: Mamajek2002; Pecaut2012) Upper Centaurus Lupus moving group" (Introduction)

## Data provenance

- ALMA projects: 2022.1.00338.L, 2012.1.00142.S
- bands: Band 7, 0.89 mm  
  > "The disc was observed in band 7, centred at the wavelength of 0.89 mm, with a resolution (beam size) of 17 au (0.13")." (2.2 ALMA)
- frequencies and spectral setup: _not stated_
- continuum bandwidth: _not stated_
- arrays: _not stated_
- configurations: _not stated_
- baselines: _not stated_
- angular resolution: 17 au (0.13")  
  > "with a resolution (beam size) of 17 au (0.13")" (2.2 ALMA)
- max recoverable scale: _not stated_
- sensitivity: _not stated_
- time on source: _not stated_
- observing dates: _not stated_
- pi or archival as stated: _not stated_
- Line: 12CO and 13CO J=3-2 (not stated)
- Other facility **VLT/SPHERE**: 1.6 μm total-intensity scattered light image of the disc (Feldt et al. 2017)  
  > "HD 131835 has been previously observed in the near-infrared (at $\sim$ 1.6 μm), in total-intensity scattered light, with SPHERE (cite: Feldt2017)." (2.1 SPHERE)
- External data: ALMA radial brightness profiles (frank, rave, parametric) of HD 131835; frank peaks 8.9±0.6 mJy/arcsec2 at 65.4 au and 1.3±0.2 at 96.5 au  
  > "(cite: Han_ARKS) fitted models of the de-projected radial brightness profiles to all of the ARKS targets." (2.2 ALMA) [from (cite: Han_ARKS)]
- External data: Scattered-light model constraints: outer ring peak 0.679±0.041 mJy/arcsec2, inner/outer ring ratio upper limit ~1  
  > "This model has a peak surface brightness of $0.679\pm0.041$ mJy/arcsec$^2$ at around 100 au, measured along the disc semi-major axis." (2.1 SPHERE) [from (cite: Milli_ARKS)]
- External data: Disc aspect ratios 0.022, 0.039, 0.058 from parametric, frank, rave  
  > "Values of the aspect ratio obtained are $0.022^{+0.007}_{-0.006}$, $0.039^{+0.006}_{-0.006}$ and $0.058^{+0.038}_{-0.037}$ from a parametric approach, code `frank` and code `rave`, respectively." (4.5 Effect of collisions) [from (cite: Zawadzki_ARKS)]
- External data: CO gas masses and dust mass 0.45 Mearth from ARKS continuum  
  > "we adopt $M_{\rm dust}=0.45$ M$_\oplus$, which is estimated based on the ARKS continuum emission (cite: Marino_ARKS)" (4.5 Effect of collisions) [from (cite: Marino_ARKS); (cite: Cataldi2023); (cite: MacManamon_ARKS)]

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

- ALMA observations, data reduction and imaging  
  > "All details of the observations, data reduction and imaging are presented in (cite: Marino_ARKS)." (2.2 ALMA) [from (cite: Marino_ARKS)]
- Simple empirical model approach  
  > "Following (cite: Pawellek2024), we assumed that the surface brightness profile inferred from the ALMA data reflects the spatial distribution of dust-producing planetesimals in the system." (3.1 Approach) [from (cite: Pawellek2024)]
- Dust dynamics approach  
  > "we followeded the approach of (cite: Krivov2009)" (4.2 Model of dust grain dynamics) [from (cite: Krivov2009)]

### Not stated but needed to reproduce (our reading)

- ACE input parameters beyond those listed (belt masses, size grid, age, run time)
- Dust optical constants details and size range for Mie calculations
- How colours of the inner ring lower limit were computed exactly
- Radial grid and binning for dynamical models

## Analysis recipe

1. **empirical collisional-cascade test**: Planetesimal profile from frank ALMA profile, fixed q=3.5 size distribution with radiation pressure, simulate 890 μm and 1.6 μm profiles  
  > "We calculated a normalized surface density radial profile of planetesimals from the `frank` surface brightness radial profile assuming a black-body temperature profile" (3.1 Approach)
   - parameter: q=3.5; M*=1.7 Msun; L*=9 Lsun; scattering angle 90 deg  
  > "We adopt a stellar mass of $M_*=1.7$ M$_\odot$ and a stellar luminosity of $L_*=9$ L$_\odot$ (cite: Marino_ARKS)." (3.1 Approach)
   - assumption: Spherical astrosilicate grains, Mie theory, circular planetesimal orbits  
  > "we assume dust grains are perfect spheres with a simple astrosilicate composition (cite: draine-2003) and we calculate the optical properties of the dust using Mie theory" (3.1 Approach)
   - fitting: _not stated_
   - validation: Compared with SPHERE profile; fails to reproduce outer ring  
  > "It fails to reproduce the one inferred from SPHERE observations completely." (3.1 Results)
2. **two-belt collisional modelling**: ACE simulations of belts at 65 and 100 au (10% width), varying e_max or strength Q_D*, comparing ALMA/SPHERE colours  
  > "We used the state-of-the art numerical code ACE (cite: krivov-et-al-2005; krivov-et-al-2006; loehne-et-al-2007; loehne-et-al-2017)" (3.2 Approach)
   - software: ACE
   - parameter: sin(eps)=e_max/2; Q_D,g*=5e6 erg/g, b_g=1.38; Q_D,s* values in Table 1; e_max=0.1 in strength runs  
  > "For the gravity regime all models assume $Q_{\rm D,g}^*=5 \cdot 10^6$ erg/g and $b_{\rm g}=1.38$ (cite: benz-asphaug-1999)." (3.2 Results)
   - assumption: Belts independent; interaction between belts ignored  
  > "A caveat of our current model is that any interaction between the two belts is ignored." (3.2 Results)
   - fitting: _not stated_
   - validation: Grid comparison to observed colours  
  > "To compare our models against the observations, we calculated the colours of the two rings of HD 131835 using the peak surface brightnesses from the `frank` profile" (3.2 Numerical models of collisional evolution, Approach)
3. **gas-drag dust dynamics**: Integrate 500 grains (2 μm to 1 cm) for 10 Myr in Gaussian gas disc with drag and radiation pressure; vary rho_g0, sigma_g, mu, q; rescale to frank peak  
  > "We integrated equations of motion of individual dust grains of various sizes (500 particles log-spaced from 2 μm to 1 cm, corresponding to a range of $\beta=0.5$ to $\beta=0.0001$)" (4.2 Model of dust grain dynamics)
   - parameter: r_g=65 au; mu=28 or 2.3; rho_s=3.3 g/cm3; Q_pr=1  
  > "We assumed grain material density of $\rho_{\rm s}=3.3$ g cm$^{-3}$ and we calculated particle $\beta$ parameters assuming $Q_{\rm pr}=1$." (4.2 Model of dust grain dynamics)
   - assumption: Black-body gas temperature, vertical hydrostatic equilibrium, Gaussian gas profile  
  > "For all models we assume the gas to have a black-body temperature profile" (4.1 Model of gas disc)
   - fitting: _not stated_
   - validation: Comparison of ring location, brightness ratio and peak brightness to observations  
  > "Considering only the peak brightness of both rings and at both wavelengths, the two most favourable models are:" (4.4 Application to HD 131835)
4. **collisional lifetime versus drift time**: Particle-in-a-box lifetime of 10 μm grains compared to drift time out of a 10 au belt  
  > "The collisional lifetime of particles while they are still in the belt, $t_{\rm coll}$, can be estimated using a simple particle-in-a-box model." (4.5 Effect of collisions)
   - parameter: M_dust=0.45 Mearth; aspect ratio 0.016-0.096; Q_D* 1e7-1e9 erg/g  
  > "we considered a range of aspect ratios encompassing all three confidence intervals (0.016–0.096)" (4.5 Effect of collisions)
   - fitting: _not stated_
   - validation: _not stated_
5. **synthetic CO profile**: RADMC3D LTE 12CO cube for sigma_g=15 au, rho_g0=1e-19, convolved and profile extracted as in MacManamon  
  > "we used RADMC3D (cite: Dullemond2012) to perform radiative transfer calculations and to produce a data cube of $^{12}$CO line emission." (5.1.2 Migration of small dust due to gas)
   - software: RADMC3D
   - fitting: _not stated_
   - validation: Compared with observed CO radial profile; model narrower  
  > "We find that the radial profile of our synthetic observation is indeed narrower than the observed radial profile" (5.1.2 Migration of small dust due to gas)

## Software

- **ACE** : Collisional evolution of planetesimal belts  
  > "We used the state-of-the art numerical code ACE" (3.2 Approach)
- **RADMC3D** : Synthetic 12CO line cube  
  > "we used RADMC3D (cite: Dullemond2012) to perform radiative transfer calculations" (5.1.2 Migration of small dust due to gas)

## Numeric results

| quantity | value | uncertainty | units | step | quote |
|---|---|---|---|---|---|
| ratio of 890 μm to 1.6 μm brightness for model outer belt (e_max=0.9) vs observed | about 3.5 times higher | not stated | dimensionless | 2 | the ratio of the surface brightnesses at 890 μm and at 1.6 μm is about 3.5 times higher than that measured for the outer ring in HD 131835 |
| Q_D* difference needed between belts | two to three orders of magnitude | not stated | dimensionless | 2 | The total difference between the materials would need to amount to about two to three orders of magnitude in $Q_\text{D}^*$ at a given dust size. |
| best gas model total gas mass (mu=28, sigma_g=10 au, rho_g0=1e-17) | 0.26 | not stated | Mearth | 3 | $\mu=28$, $\sigma_{\rm g}=10$ au and $\rho_{\rm g, 0}=10^{-17}$ g cm$^{-3}$ (total gas mass of 0.26 M$_\oplus$) |
| best gas model total gas mass (mu=28, sigma_g=15 au, rho_g0=1e-19) | 0.004 | not stated | Mearth | 3 | $\sigma_{\rm g}=15$ au and $\rho_{\rm g, 0}=10^{-19}$ g cm$^{-3}$ (total gas mass of 0.004 M$_\oplus$) |
| required size distribution exponent q | ≳3.75 | not stated | dimensionless | 3 | both with $q \gtrsim 3.75$ |

## Qualitative findings

- Gas-driven scenario gives outer ring too faint in both scattered light and sub-mm; observed CO profile is wider than model gas profiles.  
  > "the resulting outer ring is too faint overall in both scattered light and sub-millimetre emission." (abstract)

## Claim tuples

- H: A standard collisional cascade traced by ALMA explains both rings | E: Empirical model with fixed q=3.5 and radiation pressure | R: No outer ring in scattered light | F: Simple cascade is inconsistent with observations | **supported**
- H: Two planetesimal belts with different excitation or strength explain the colours | E: ACE grids varying e_max and Q_D* | R: Outer belt colour not matched by e_max alone; needs extremely weak material | F: Possible only with extreme differences | **partially**
- H: Gas drag creates the outer ring from dust of the inner belt | E: Dynamical grid over gas density, width, mu and q | R: Ring location and scattered-light ratio matched, but outer ring too faint | F: Plausible but insufficient in the simple model | **partially**

## Reasoning

- Why this data: _not stated_
- Why this method: _not stated_
- Alternative: Giant impact, inverted gas scenario, and extended planetesimal belt discussed as other possibilities  
  > "Yet another possibility is that the inner belt hosts a collisional cascade, while the outer belt, or at least its peculiar colour, was formed more recently by a giant impact." (5.1.3 Other possibilities)
- How they decided it was enough: _not stated_
- Limitation (authors): Dynamical model omits collisions, gas evolution, dust feedback and assumes Gaussian gas profile  
  > "This purely dynamical model does not account for particle lifetimes which could be both shorter and size-dependent due to destructive collisions" (4.2 Model of dust grain dynamics)
- Caveat (inferred, ours): Outer ring existence is uncertain since only the frank profile shows it
- Caveat (inferred, ours): Colours depend on a single astrosilicate optical model
- Caveat (inferred, ours): Results rely on ARKS products from a companion paper

## Reproducibility

- Data public (paper): ARKS data in the ARKS dataverse  
  > "The ARKS data used in this paper can be found in the [ARKS dataverse](https://dataverse.harvard.edu/dataverse/arkslp)." (Data availability)
- Products in archive: _not stated_
- Missing: ACE code access and full parameter files
- Missing: Dynamical model code
- Missing: Exact frank profile data
- Data volume (inferred): small (derived profiles); ALMA raw data not reprocessed
- Score (inferred): 3/5, Models well described but ALMA reduction is delegated and code not released.
- Rediscovery candidate: no, Theory-focused; relies on external profiles and unreleased codes.

## Links

- Method: (cite: Marino_ARKS) (ARKS observations and data reduction)
- Method: (cite: Han_ARKS) (radial profile fitting)
- Method: (cite: takeuchi-artymowicz-2001) (dust-gas interaction theory)
- Companion: (cite: Milli_ARKS) (scattered-light vs mm offset)
- Companion: (cite: MacManamon_ARKS) (CO gas of HD 131835)
- Companion: (cite: Zawadzki_ARKS) (vertical structure)
- Related: ARKS

## Checks

```json
{
 "quotes": 47,
 "quotes_ok": 47,
 "quote_pass_rate": 1.0,
 "quotes_too_long": 0,
 "unsupported_facts": 0,
 "project_codes": 2,
 "codes_not_in_text": [],
 "codes_not_in_obscore": [],
 "obscore_codes_not_in_card": [
  "2012.1.00198.S",
  "2015.1.01260.S",
  "2016.1.00104.S",
  "2016.1.00195.S",
  "2016.1.00907.S",
  "2017.1.00167.S",
  "2017.1.00825.S",
  "2018.1.01222.S",
  "2019.1.00189.S"
 ],
 "codes_printed_but_missing": [
  "2012.1.00198.S",
  "2015.1.01260.S",
  "2016.1.00104.S",
  "2016.1.00195.S",
  "2016.1.00907.S",
  "2017.1.00167.S",
  "2017.1.00825.S",
  "2018.1.01222.S",
  "2019.1.00189.S"
 ],
 "numeric_results": 5,
 "numeric_problems": 0,
 "fill": {
  "facts": 78,
  "stated": 35,
  "rate": 0.449
 },
 "evidence_ok": true
}
```
