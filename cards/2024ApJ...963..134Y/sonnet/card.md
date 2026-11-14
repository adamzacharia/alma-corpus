# Turbulent Vortex with Moderate Dust Settling Probed by Scattering-induced Polarization in the IRS 48 System

`2024ApJ...963..134Y` | The Astrophysical Journal 2024 | first author: Yang, Haifeng | arXiv: 2402.12662 | DOI: 10.3847/1538-4357/ad2346

Card schema 1.0 | model claude-sonnet-5-5 | depth full | type observational_alma_primary

## Science

- Fields: protoplanetary_disks
- Question: What are the dust scale heights (settling) in the IRS 48 crescent, as probed by the displacement between polarized and total intensity from scattering-induced polarization?  
  > "There is a relative displacement between the polarized flux and the total flux, which holds the key to understanding the dust scale heights in this system." (abstract)
- Target **Oph IRS 48**: coordinates _not stated_; z/distance 136 pc  
  > "which is $15\,\mathrm{au}\times 10\,\mathrm{au}$ (at a distance of 136 pc; (cite: GaiaDR3))" (2.1 Observations); distance from Gaia DR3  
  > "which is $15\,\mathrm{au}\times 10\,\mathrm{au}$ (at a distance of 136 pc; (cite: GaiaDR3))" (2.1 Observations)

## Data provenance

- ALMA projects: 2019.1.01059.S
- bands: Band 7 (0.87 mm)  
  > "using ALMA Band 7 (0.87 mm) under the project code 2019.1.01059.S (PI: H. Yang)" (2.1 Observations)
- frequencies and spectral setup: _not stated_
- continuum bandwidth: _not stated_
- arrays: _not stated_
- configurations: _not stated_
- baselines: _not stated_
- angular resolution: 0.11" x 0.072" (15 au x 10 au)  
  > "The synthesized beam is $0\ensuremath{''}{11}\times 0\ensuremath{''}{072}$, which is $15\,\mathrm{au}\times 10\,\mathrm{au}$" (2.1 Observations)
- max recoverable scale: _not stated_
- sensitivity: rms 14 uJy (Stokes I), 12 uJy (Stokes QUV and linear polarized intensity)  
  > "The rms noise level measured in the Stokes I image is 14 $\mu$Jy, whereas the rms noise level in Stokes QUV images is 12 $\mu$Jy." (2.1 Observations)
- time on source: _not stated_
- observing dates: June 7, June 14, and July 19, 2021  
  > "The observations were carried out in June 7, June 14, and July 19, 2021" (2.1 Observations)
- pi or archival as stated: PI: H. Yang  
  > "under the project code 2019.1.01059.S (PI: H. Yang)" (2.1 Observations)
- External data: Disk inclination 50 deg and position angle 100 deg  
  > "The inclination of the disk was constrained as $50^\circ$ with a position angle of $100^\circ$ (cite: Bruderer2014)." (2.1 Observations) [from (cite: Bruderer2014)]
- External data: Distance 136 pc  
  > "at a distance of 136 pc; (cite: GaiaDR3))" (2.1 Observations) [from (cite: GaiaDR3)]
- External data: Dust composition (mass fractions of water ice, silicate, troilite, organics) giving n=2.3, k=0.023 at 870 um  
  > "We adopt a dust composition that is the same as the one adopted by (cite: Birnstiel2018)" (3 Modeling) [from (cite: Birnstiel2018)]

## Processing

### Calibration

- pipeline or manual: _not stated_
- casa version: CASA v6.2.1.7  
  > "*Software:* CASA (v6.2.1.7; (cite: casa))" (Software)
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
- final beam: 0.11" x 0.072"  
  > "The synthesized beam is $0\ensuremath{''}{11}\times 0\ensuremath{''}{072}$" (2.1 Observations)
- final rms: 14 uJy (I); 12 uJy (QUV, PI)  
  > "The rms noise level of the (linearly) polarized intensity is $12\rm\, \mu Jy$." (2.1 Observations)

### Inherited from earlier work

- Observation details and data reduction  
  > "The details of the observation and the data reduction were presented in detail in (cite: paper1)." (2.1 Observations) [from (cite: paper1)]
- Dust column density profile form  
  > "we assume a column density of dust grains similar to that adopted by (cite: vanderMarel2015) and (cite: Ohashi2020)" (3 Modeling) [from (cite: vanderMarel2015), (cite: Ohashi2020)]
- Temperature profile normalisation  
  > "similar to the one adopted by (cite: Ohashi2020), which was inspired by the physical-chemical model developed by (cite: Bruderer2014)" (3 Modeling) [from (cite: Ohashi2020); (cite: Bruderer2014)]

### Not stated but needed to reproduce (our reading)

- Calibration and imaging details (robust, polarization calibration, self-calibration) are only in Paper I
- Number of RADMC-3D scattering and polarization settings (e.g. scattering mode, opacity calculation code)
- Exact procedure for locating peaks in the radial and azimuthal profiles
- Source coordinates
- Disk aspect-ratio (gas scale height) normalization and flaring law
- Grain size distribution slope

## Analysis recipe

1. **Measure displacement between PI and I**: Integrate fluxes in a deprojected wedge to get radial and azimuthal profiles and compare peak positions  
  > "We then integrate the fluxes along the azimuthal direction to obtain the radial profile, shown in the lower left panel of Figure [2](#fig:displacement)" (2.1 Observations)
   - software: CASA
   - parameter: wedge 0.25"-0.6" radial, 60-150 deg azimuthal in disk frame  
  > "defined with $0.25\ensuremath{''}-0.6\ensuremath{''}$ in the radial direction and $60^\circ-150^\circ$ in the azimuthal angle in the disk frame" (2.1 Observations)
   - assumption: inclination 50 deg, PA 100 deg for deprojection  
  > "The inclination of the disk was constrained as $50^\circ$ with a position angle of $100^\circ$" (2.1 Observations)
   - fitting: _not stated_
   - validation: Compared with astrometric accuracy of 0.012" (0.019" deprojected)  
  > "which is about $0.012\ensuremath{''}$ or $1.6$ au and is deprojected as $0.019\ensuremath{''}$ or $2.5$ au in the disk plane" (2.1 Observations)
2. **Radiative transfer models with varying settling**: Monte Carlo radiative transfer in full polarization mode with RADMC-3D for f_settle = 1, 2, 10, convolved with the beam  
  > "We then conduct Monte Carlo radiation transfer imaging with the assumed temperature structure in full polarization mode with $1.6\times 10^8$ photons" (3 Modeling)
   - software: RADMC-3D
   - parameter: spherical grid 300x128x128 in r, theta, phi; r 1-300 au log; 1.6e8 photons  
  > "The grid is spherical polar with 300, 128, and 128 points in the $r$, $\theta$, and $\phi$ directions, respectively." (3 Modeling)
   - parameter: a_max=140 um, a_min=0.1 um, Sigma_0=1 g/cm2, rc=61 au, rw=10 au, phic=109 deg, phiw=30 deg, T60=60 K  
  > "$\Sigma_0$ | $1.0\rm\, g/cm^2$ |     $T_{60}$     |   $60\rm\, K$" (Table 1)
   - assumption: Dust composition giving n=2.3, k=0.023; T=T60 (r/60 au)^-0.5; only self-scattering  
  > "At the wavelength of $870\rm\, \mu m$, this dust grain has a complex refractory index $m = n+ik$, with $n=2.3$ and $k=0.023$." (3 Modeling)
   - fitting: No formal fit; manual comparison across f_settle  
  > "We constructed a series of models with different values of $f_\mathrm{settle}$ and analyzed their corresponding polarized intensity, total intensity, polarization fraction, and angle." (Modeling: Settling of dust grains)
   - validation: Photon number checked by convergence test  
  > "which is adequate according to the convergence test" (3 Modeling)
3. **Compare model and observed displacements**: Same profile-integration applied to models; radial displacement vs f_settle; azimuthal profile morphology  
  > "This procedure was carried out following the same methodology that was used to generate the observed total and polarized intensities" (3.2 Analysis of the radial profiles)
   - fitting: _not stated_
   - validation: Best model chosen by reproducing radial shift and azimuthal profile asymmetry  
  > "On the basis of our analysis, the $f_\mathrm{settle}=2$ model provides the best explanation for our observation." (3.3 Analysis of the azimuthal profiles)
4. **Infer turbulence alpha**: Use Youdin & Lithwick dust scale-height relation with f_settle=2 giving alpha ~ St/3, with St=rho_s a/Sigma_g, for G/D 3-100  
  > "For a G/D between $3$ and $100$, we have the turbulence parameter as $\alpha = 0.0001\sim 0.005$." (Discussion: Dust settling and level of turbulence)
   - parameter: a=140 um, rho_s=3 g/cm3, Sigma_d=1 g/cm2  
  > "$\alpha = 0.0014 \times \left(\frac{\rho_s}{3\rm\, g/cm^3}\right)" (4.1 Dust settling and level of turbulence)
   - assumption: Compact spherical grains; gas-to-dust ratio 3-100  
  > "This estimate assumes compact spherical dust grains." (4.1 Dust settling and level of turbulence)
   - fitting: _not stated_
   - validation: _not stated_

## Software

- **CASA** 6.2.1.7: data reduction (details in Paper I)  
  > "*Software:* CASA (v6.2.1.7; (cite: casa))" (Software)
- **RADMC-3D** : Monte Carlo radiative transfer polarization models  
  > "we perform radiative transfer simulations using RADMC-3D[^3]" (3 Modeling)
- **Matplotlib** : plotting (listed in software)  
  > "Matplotlib (cite: Matplotlib), Scipy (cite: scipy)" (Software)
- **Scipy** : listed in software  
  > "Matplotlib (cite: Matplotlib), Scipy (cite: scipy)" (Software)

## Numeric results

| quantity | value | uncertainty | units | step | quote |
|---|---|---|---|---|---|
| Radial displacement of PI peak inward of I peak | 0.047 (6.4 au) | astrometric accuracy 0.012" (0.019" deprojected) | arcsec | 1 | the peak of PI is inward of the peak of I by $0.047\ensuremath{''}$, or $6.4$ au |
| Azimuthal displacement | 34 | not stated | deg | 1 | The azimuthal displacement is $34^\circ$. |
| Model radial shift f_settle=10 | 2.9 | not stated | au | 3 | the shift is relatively small, measuring approximately $2.9$ au. |
| Model radial shift f_settle=1 and 2 | 3.3 and 4.7 | not stated | au | 3 | the radial shift is significantly larger, measuring approximately $3.3$ au and $4.7$ au, respectively. |
| Effective turbulence alpha | 0.0001-0.005 | range from G/D 3-100 | dimensionless | 4 | we have the turbulence parameter as $\alpha = 0.0001\sim 0.005$. |
| Best-fit gas-to-dust scale height ratio f_settle | 2 | not stated | dimensionless | 3 | To reproduce the observed radial shift, we find that $f_\mathrm{settle}$ should be approximately $2$. |

## Qualitative findings

- Polarization is mostly uniform, perpendicular to the disk major axis, consistent with inclination-induced scattering; east side more polarized (up to 3% or more).  
  > "The east side is more polarized than the west side, with a polarization fraction that reaches $3\%$ or higher." (5 Summary)
- No signs of grain alignment found.  
  > "We did not find signs of grain alignment in our observation." (5 Summary)

## Claim tuples

- H: Dust in the IRS 48 crescent is neither fully settled nor well mixed | E: RADMC-3D polarization models with f_settle=1, 2, 10 compared with observed displacements | R: f_settle=2 reproduces radial shift and the east-west azimuthal asymmetry | F: Moderate dust settling, gas-to-dust scale height ratio ~2 | **supported**
- H: The observed polarization arises from scattering rather than aligned grains | E: Compare patterns with scattering models and expected alignment patterns | R: Uniform pattern matches inclination-induced scattering | F: Scattering dominates at 870 um | **supported**
- H: Turbulence level implied by moderate settling | E: Apply the dust scale-height relation for f_settle=2 | R: alpha ~ 0.0001-0.005 | F: Turbulent vortex with moderate settling | **partially**

## Reasoning

- Why this data: _not stated_
- Why this method: Focus on spatial profiles of polarization rather than absolute fractions, so a_max was fixed  
  > "we focus on the spatial distribution and profiles of the polarization fractions, as opposed to the absolute polarization fractions." (3 Modeling)
- Alternative: Toroidal magnetic fields, eddy fields, aerodynamic and radiative alignment rejected since they would give radial, complicated or azimuthal patterns  
  > "Grains aligned with toroidal magnetic fields would produce polarization vectors that all point towards the central star." (4.2 Grain alignment)
- How they decided it was enough: _not stated_
- Limitation (authors): True nature of moderate settling cannot be determined; alpha limited by gas column uncertainty  
  > "The greatest uncertainty comes from the gas column density." (4.1 Dust settling and level of turbulence)
- Caveat (inferred, ours): Only three f_settle values explored, no formal fit or uncertainty on f_settle
- Caveat (inferred, ours): Single parametric disk geometry; a_max, temperature and Sigma_0 fixed
- Caveat (inferred, ours): Peak-displacement measure sensitive to noise, beam and wedge choice

## Reproducibility

- Data public (paper): Data cited by ALMA project code; public status not explicitly stated  
  > "This paper makes use of the following ALMA data: ADS/JAO.ALMA#2019.1.01059.S." (Acknowledgement)
- Products in archive: _not stated_
- Missing: Calibration/imaging recipe (in Paper I)
- Missing: RADMC-3D input details such as scale height normalization
- Data volume (inferred): ~100 GB to 1 TB for three Band 7 polarization execution blocks
- Score (inferred): 3/5, Model setup is mostly specified, but data reduction is deferred to Paper I and the model comparison is qualitative.
- Rediscovery candidate: no, Data reduction recipe is not given and the key comparison is partly qualitative.

## Links

- Method: Yang, H., et al. 2023, arXiv:2304.02937 (cite: paper1) (Observation and data reduction details)
- Companion: (cite: Ohashi2020) (Earlier polarimetric observations of IRS 48 and model setup)

## Checks

```json
{
 "quotes": 53,
 "quotes_ok": 53,
 "quote_pass_rate": 1.0,
 "quotes_too_long": 0,
 "unsupported_facts": 0,
 "project_codes": 1,
 "codes_not_in_text": [],
 "codes_not_in_obscore": [],
 "obscore_codes_not_in_card": [],
 "codes_printed_but_missing": [],
 "numeric_results": 6,
 "numeric_problems": 0,
 "fill": {
  "facts": 76,
  "stated": 42,
  "rate": 0.553
 },
 "evidence_ok": true
}
```
