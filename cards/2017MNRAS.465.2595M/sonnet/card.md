# ALMA observations of the η Corvi debris disc: inward scattering of CO-rich exocomets by a chain of 3-30 M<SUB>⊕</SUB> planets?

`2017MNRAS.465.2595M` | Monthly Notices of the Royal Astronomical Society 2017 | first author: Marino, S. | arXiv: 1611.01168 | DOI: 10.1093/mnras/stw2867

Card schema 1.0 | model claude-sonnet-5-5 | depth full | type observational_alma_primary

## Science

- Fields: debris_disks
- Question: What is the structure of the eta Corvi outer belt, and does it favour an LHB-like instability or a stable planetary configuration feeding the hot dust? Is CO gas present, and what planets could sculpt the belt?  
  > "Thus, we are interested in studying the structure of the outer belt to look for features that can hint at one of the three possible planet-driven scenarios described above to explain the hot dust." (Introduction)
- Target **eta Corvi**: coordinates _not stated_; z/distance 18.3 pc  
  > "located 18.3 pc away (cite: vanLeeuwen2007)" (Introduction); distance from van Leeuwen 2007  
  > "located 18.3 pc away (cite: vanLeeuwen2007)" (Introduction)

## Data provenance

- ALMA projects: 2012.1.00385.S
- bands: Band 7 (340 GHz)  
  > "ALMA band 7 observations (340 GHz) of $\eta$ Corvi were carried out from 2013 Dec 15 to 2015 Jan 1" (2 Observations)
- frequencies and spectral setup: Four spectral windows: three continuum (335.744, 337.644, 347.455 GHz; 128 channels of 14 km/s) and one with 12CO 3-2 (3840 channels of 0.42 km/s, 1.9 GHz)  
  > "The fourth included the $^{12}$CO 3–2 line at 345.798 GHz and was set with 3840 finer channels, each one with a width of 0.42 km s$^{-1}$" (2 Observations)
- continuum bandwidth: 7.9 GHz effective  
  > "The four together provided an effective bandwidth of 7.9 GHz to study the continuum emission." (2 Observations)
- arrays: _not stated_
- configurations: _not stated_
- baselines: 15 m to 445 m (5th-95th percentile 26-240 m)  
  > "baselines ranging from 15 m to 445 m, with the 5th and 95th percentiles equal to 26 m and 240 m" (2 Observations)
- angular resolution: 1.18" x 0.65" natural weights  
  > "we obtain an elongated beam of size $1.18\ensuremath{''}\times0.65\ensuremath{''}$" (2.1 Continuum emission)
- max recoverable scale: 1" up to 7"  
  > "This allows to recover angular scales from $1\ensuremath{''}$ up to $7\ensuremath{''}$." (2 Observations)
- sensitivity: _not stated_
- time on source: _not stated_
- observing dates: 2013 Dec 15 to 2015 Jan 1, 6 executions  
  > "2014 Dec 29 | 66-81 | 37 | 48 | 15 | 50 | Titan" (Table 1)
- pi or archival as stated: PI: M. C. Wyatt  
  > "under the project 2012.1.00385.S (PI: M. C. Wyatt)" (2 Observations)
- Line: 12CO J=3-2 (345.798 GHz)
- Other facility **SCUBA-2/JCMT**: Total flux 15.5±1.4 mJy at 0.85 mm for comparison  
  > "SCUBA-2/JCMT observed $\eta$ Corvi  measuring a total flux of $15.5\pm1.4$ mJy." (2.1 Continuum emission)
- Other facility **Herschel**: 70 micron images used for comparison of disc geometry and asymmetry  
  > "Compared with the PACS image at 70 $\mu$m obtained by *Herschel* (previous best image of the outer belt)" (2.1 Continuum emission)
- External data: Hot dust 70 micron excess and SED model, fractional luminosities  
  > "higher than the 44$\mu$Jy extrapolated from the 70 $\mu$m flux excess detected with *Herschel* (cite: Duchene2014)" (2.1 Continuum emission) [from Duchene2014]
- External data: Hot dust mass loss rate ~3e-9 Mearth/yr  
  > "The first was estimated to be $\sim3\times
10^{-9}$ M$_\oplus$ yr$^{-1}$ (cite: Wyatt2010)." (4.1.2) [from Wyatt2010]
- External data: LHB N-body simulation of Nice model run (t=880 Myr)  
  > "obtained from N-body simulations from one of the Nice model runs (cite: Gomes2005)" (3.3 Late Heavy Bombardment) [from Gomes2005]
- Simulation/model as data: Scaled Nice-model LHB planetesimal surface density used as disc model  
  > "we linearly scale the semi-major axis of the planetesimals orbits to match the location of the mean radius of $\eta$ Corvi" (3.3 Late Heavy Bombardment)

## Processing

### Calibration

- pipeline or manual: _not stated_
- casa version: _not stated_
- pipeline version: _not stated_
- archive products used as is: _not stated_
- flux calibrator: Pallas, Ceres, 3c279, Ganymede, Titan  
  > "Pallas, Ceres, 3c279, Ganymede and Titan were used as flux calibrators and observed for 2.6 min" (2 Observations)
- flux scale uncertainty: ~10%  
  > "does not take into account the uncertainty on the absolute flux calibration, $\sim$10%" (2.1 Continuum emission)
- self calibration: _not stated_

### Imaging

- task: CLEAN in CASA 4.4  
  > "The image reconstruction of the dust continuum is performed with the *CLEAN* algorithm and task in CASA 4.4" (2.1 Continuum emission)
- deconvolver: _not stated_
- weighting robust: natural weights  
  > "using natural weights, and combining the four spectral windows" (2.1 Continuum emission)
- uv taper: Gaussian taper FWHM 1.2" giving 1.5"x1.3" beam  
  > "tapering the visibilities with the Fourier transform of a Gaussian of FWHM of $1.2\ensuremath{''}$" (2.1 Continuum emission)
- cell size: 0.1" pixel  
  > "radial widths of $0.1\ensuremath{''}$ (pixel size of the deconvolved image)" (2.1 Continuum emission)
- image size: _not stated_
- masking: clean stellar emission first, then outer belt  
  > "we first clean the stellar emission and then the outer belt" (2.1 Continuum emission)
- multiscale scales: _not stated_
- continuum subtraction: uvcontsub  
  > "After subtracting the continuum emission from the visibilities using the CASA task *uvcontsub*" (2.2 CO (3-2))
- line free channels: _not stated_
- primary beam correction: applied after cleaning; noise 22-30 uJy/beam around belt  
  > "The image noise around the outer belt varies from 22 $\mu$Jy beam$^{-1}$ near the disc major axis up to 30 $\mu$Jy beam$^{-1}$ close to the minor axis." (2.1 Continuum emission)
- array combination: _not stated_
- smoothing: _not stated_
- final beam: _not stated_
- final rms: 20 uJy/beam before primary beam correction (natural)  
  > "The image noise level before correcting by the primary beam is 20 $\mu$Jy beam$^{-1}$" (2.1 Continuum emission)

### Inherited from earlier work

- Azimuthal-averaging dirty-channel-map CO search method  
  > "As shown by (cite: Matra2015) and (cite: Marino2016), the detection limits can be improved by azimuthally averaging the dirty channel maps and integrating in frequency." (2.2 CO (3-2)) [from (cite: Matra2015); (cite: Marino2016)]
- Non-LTE CO excitation code  
  > "We use the code developed by (cite: Matra2015) that computes the population of the rotational levels in the non-LTE regime" (3.7 CO mass constraints) [from (cite: Matra2015)]
- Grain composition matched to earlier work  
  > "to match the composition used in (cite: Duchene2014)" (3 Disc modelling) [from (cite: Duchene2014)]
- Self-stirred disc parametrization  
  > "we considered a second model that consists of a parametric self-stirred disc based on the work by (cite: Kennedy2010)" (3.2 Self-stirred disc) [from (cite: Kennedy2010)]

### Not stated but needed to reproduce (our reading)

- Number of CLEAN iterations, threshold and mask definitions
- Exact line-free channels and velocity ranges for uvcontsub
- Whether pipeline or manual calibration was used and CASA calibration version
- Flux calibrator models used per execution
- Exact fixvis phase-centre offsets per execution
- Grid size and resolution of the RADMC-3D model
- Prior ranges for each parameter
- uvsim tool configuration for model visibilities
- Statistic details for the 1% false-alarm probability simulation

## Analysis recipe

1. **Correct pointing and combine executions**: Fix mosaic pointing errors with fixvis, align and combine  
  > "These errors were corrected using the CASA task fixvis (cite: McMullin2007) and subsequently aligning and combining the data prior to the image synthesis." (2 Observations)
   - software: CASA
   - fitting: _not stated_
   - validation: _not stated_
2. **Image continuum and measure flux and radial profile**: CLEAN with natural weights, tapered version, elliptical aperture photometry and azimuthal averages  
  > "We measure a total disc flux of $9.2\pm0.5$ mJy, integrating the continuum emission inside an elliptic mask" (2.1 Continuum emission)
   - software: CASA
   - fitting: _not stated_
   - validation: Compared with SCUBA-2 flux  
  > "we find that the total emission measured in the ALMA Clean image is lower by $2-3\sigma$" (2.1 Continuum emission)
3. **Search for CO emission**: Azimuthally average continuum-subtracted dirty channel maps, integrate over Keplerian velocities, vary stellar velocity, extract spectrum  
  > "Therefore, we vary $v_\star$ between -10 to 10 km s$^{-1}$ to search for any significant CO disc emission that could be present in the data." (2.2 CO (3-2))
   - software: CASA
   - assumption: Inclination 37 deg, same as outer belt  
  > "assuming the same inclination as the outer belt (37$^{\circ}$)" (2.2 CO (3-2))
   - fitting: _not stated_
   - validation: Probability of a 4 sigma false detection in search ~1%  
  > "We find that this has a probability of 1%." (2.2 CO (3-2))
4. **Fit parametric disc models to visibilities**: Four models (Gaussian belt, self-stirred, LHB/double power law, eccentric belt) with RADMC-3D images, simulated visibilities, MCMC  
  > "A Bayesian approach is used to constrain the different parameters of the disc models (details below), sampling the parameter space to recover the posterior distribution" (3 Disc modelling)
   - software: RADMC-3D, emcee, CASA, uvsim
   - parameter: Visibilities averaged to 3 min and 2 GHz bins; 300-1000 steps, 50-180 walkers  
  > "We run emcee for 300-1000 steps using 50-180 *walkers*, depending on the model" (3 Disc modelling)
   - assumption: Astrosilicate/amorphous carbon/water ice 70/15/15%, Dohnanyi size distribution q=-3.5, 1 um-1 cm, kappa_abs=3.8 cm2/g at 0.88 mm  
  > "This leads to a mass-weighted absorption opacity $\kappa_{\mathrm{abs}}=3.8$ cm$^{2}$ g$^{-1}$ at 0.88 mm" (3 Disc modelling)
   - fitting: emcee; likelihood proportional to exp(-chi2/2); uniform priors; weights from statwt  
  > "The likelihood function is defined proportional to $\exp(-\chi^2/2)$" (3 Disc modelling)
   - validation: Model comparison with BIC; residual dirty maps  
  > "We find that the belt model’s BIC is lower by $\sim40$ compared to the self-stirred best model’s BIC, and lower by 20 compared to the double power law model." (3.5 Model comparison)
5. **Constrain hidden cavity emission**: Analytic 3-sigma limit plus added power-law second component fit to visibilities  
  > "we added a second component to the simple belt model described in Sec. 3.1 and we fit this to the observed visibilities" (3.6)
   - software: RADMC-3D, emcee
   - assumption: T(r)=42(r/150 AU)^-0.5 K  
  > "We also assumed $T(r)=42 (r/150
 \ \mathrm{AU})^{-0.5}$ K" (3.6)
   - fitting: alpha free between -5 and 5  
  > "where we leave $\alpha$ as a free parameter that can vary between -5 and 5" (3.6)
   - validation: _not stated_
6. **Derive CO masses**: Non-LTE excitation with electron collisions, optically thin, linking n_e to M_CO for secondary origin  
  > "assuming the emission is optically thin" (3.7 CO mass constraints)
   - parameter: Tk 20-300 K at 20 AU; 10-150 K outer belt; 100-2000 K inner  
  > "considering different $T_\mathrm{k}$ (10-150 K, a more appropiate range for $T_\mathrm{k}$ at 150 AU)" (3.7 CO mass constraints)
   - assumption: nC/nC+=1, nCO/nC=1/100 as in beta Pic; vertical aspect ratio 0.1  
  > "we assume $n_\mathrm{C}/n_\mathrm{C^{+}}=1$ (cite: Cataldi2014) and $n_\mathrm{CO}/n_\mathrm{C}=1/100$ (cite: Roberge2000)" (3.7 CO mass constraints)
   - fitting: _not stated_
   - validation: _not stated_
7. **Constrain hidden planet**: Combine forced eccentricity, chaotic zone width, clearing timescale, ejection and diffusion mass limits  
  > "Combining the four equations above we can define a region in $M_\mathrm{plt}$ vs $a_\mathrm{plt}$ space where the putative planet is most likely to be found." (4.1.4)
   - assumption: Stellar mass 1.4 Msun, age 1.4 Gyr, planet density 1.6 g/cm3, disc inner edge 106 AU  
  > "where $a_\mathrm{in}=r_0-\Delta r=106$ AU, $M_\star\sim1.4\ M_\odot$" (4.1.3)
   - fitting: _not stated_
   - validation: _not stated_

## Software

- **CASA** 4.4: fixvis, CLEAN, uvcontsub, statwt  
  > "calculated based on the intrinsic dispersion of the visibilities over one scan with the task *statwt* from CASA 4.4" (3 Disc modelling)
- **RADMC-3D** 0.39: Thermal equilibrium and synthetic images  
  > "Using RADMC-3D (cite: RADMC3D0.39) we solve the thermal equilibrium of the mean dust species" (3 Disc modelling)
- **emcee** : MCMC sampling of model parameters  
  > "public python module *emcee* that implements the Goodman & Weare’s Affine Invariant MCMC Ensemble sampler" (3 Disc modelling)
- **uvsim** : Simulating model visibilities  
  > "providing us the tool uvsim to simulate model visibilities" (Acknowledgements)

## Numeric results

| quantity | value | uncertainty | units | step | quote |
|---|---|---|---|---|---|
| Total disc flux (CLEAN image) | 9.2 | 0.5 | mJy | 2 | We measure a total disc flux of $9.2\pm0.5$ mJy |
| Belt mean radius | 152 | 3 | AU | 4 | $r_{0}$ \[AU\]           /      $152\pm3$ |
| Belt radial FWHM | 46 | 5 | AU | 4 | $\Delta r$ \[AU\]        /      $46\pm5$ |
| Inclination | 35 | 2 | deg | 4 | $i$ \[$^{\circ}$\]       /      $35\pm2$ |
| Position angle | 117 | 4 | deg | 4 | PA \[$^{\circ}$\]        /      $117\pm4$ |
| Belt model total flux | 13.3 | 1.0 | mJy | 4 | The total flux of the best fit model is $13.3\pm1.0$ mJy |
| Belt dust mass | 0.014 | 0.001 | Mearth | 4 | $M_{d}$ \[M$_{\oplus}$\] /   $0.014\pm0.001$ |
| Double power law inner slope | 6.2 | +2.0/-1.3 | dimensionless | 4 | We find $\alpha_\mathrm{in}=6.2^{+2.0}_{-1.3}$, with a $3\sigma$ lower limit of 3.3. |
| Belt eccentricity 99.7% upper limit | 0.05 | not stated | dimensionless | 4 | we derive a 99.7% upper limit of 0.05 |
| CO integrated flux at ~20 AU | 38 | 9 | mJy km/s | 3 | The total line flux between -2.7 km s$^{-1}$and 6.3 km s$^{-1}$is $38\pm9$ mJy km s$^{-1}$($4\sigma$). |
| CO peak radius | 22 | 6 | AU | 3 | The peak of the emission corresponds to a radius of $22\pm6$ AU |
| CO mass at ~20 AU (secondary origin) | ~3e-7 | factor of a few | Mearth | 6 | i.e. $M_\mathrm{CO}\sim3\times10^{-7}$ M$_\oplus$. |
| Hidden cavity dust mass limit (3 sigma) | 2.7e-3 | not stated | Mearth | 5 | We find an $3\sigma$ upper limit of $2.7\times10^{-3}$ M$_\oplus$ for $M_{d2}$ and 3.2 mJy |
| Hidden planet semi-major axis | 75-100 | not stated | AU | 7 | roughly defined by $a_\mathrm{plt}$ in the range $\sim$ 75-100 AU and $M_\mathrm{plt}$ between 3-30 $M_{\oplus}$ |

## Qualitative findings

- Outer belt is consistent with axisymmetric; apparent asymmetries are image-reconstruction artefacts  
  > "thus, the observed asymmetries are likely an artefact of the image reconstruction caused by a low S/N in the visibilities and the uv-sampling" (3.1)

## Claim tuples

- H: The hot dust results from an LHB-like instability scattering a broad outer disc | E: Fit LHB-scaled and double power law surface densities to visibilities | R: Belt is narrower; inner slope steeper than r^1.5 (>3.3 at 3 sigma); eccentricity <0.05 | F: LHB-like instability unlikely; stable configuration favoured | **supported**
- H: The belt is a self-stirred disc | E: Self-stirred model fit and derived planetesimal mass | R: Implied mass 3e4 Mearth, BIC higher by ~40 than belt model | F: Self-stirring unlikely unless belt initially narrow or planet-truncated | **supported**
- H: CO gas is present in the system | E: Azimuthally averaged dirty channel map search | R: 4 sigma tentative CO at ~22 AU; no detection in belt or inner disc | F: Tentative CO possibly released in situ at ice lines; needs confirmation | **partially**
- H: A planet sculpting the inner edge can be constrained | E: Chaotic zone, clearing time, eccentricity and ejection arguments | R: a=75-100 AU, M=3-30 Mearth, e<0.08 | F: A chain of 3-30 Mearth planets may scatter material inwards | **partially**

## Reasoning

- Why this data: _not stated_
- Why this method: Model fitting in visibility space because CLEAN images have strong artefacts from sparse short baselines  
  > "As the image reconstruction suffers from strong artefacts, we analyse the ALMA observations in the uv space" (3 Disc modelling)
- Alternative: Hot dust from in situ collisional cascade, P-R drag, eccentric planetesimals ruled out; LHB and self-stirring disfavoured  
  > "The first can deliver small grains from the outer disc to the inner regions, but this mechanism is not efficient enough to explain the hot dust in $\eta$ Corvi" (Introduction)
- How they decided it was enough: _not stated_
- Limitation (authors): Missing short baselines; no ACA; CO detection tentative and morphology inconsistent with simple Keplerian ring  
  > "This shows the importance of having a complete uv-coverage that includes baselines that can capture the angular size of the observed source" (2.1 Continuum emission)
- Caveat (inferred, ours): Single-pointing-rate 4 sigma CO detection from dirty maps with a freely varied stellar velocity; 1% false-alarm estimate is post hoc
- Caveat (inferred, ours): Model comparison relies on opacity and size distribution assumptions and emcee with few steps
- Caveat (inferred, ours): Planet constraints assume a single planet and analytic formulae
- Caveat (inferred, ours): LHB model is a crude linear rescaling of the Solar System

## Reproducibility

- Data public (paper): Project code given; ALMA archive data (acknowledgement of ADS/JAO.ALMA#2012.1.00385.S)  
  > "This paper makes use of the following ALMA data: ADS/JAO.ALMA#2012.1.00385.S." (Acknowledgements)
- Products in archive: _not stated_
- Missing: Model code and uvsim not released
- Missing: CLEAN parameters and calibration script details
- Missing: Priors bounds and MCMC convergence details
- Data volume (inferred): ~50-100 GB raw for 6 executions
- Score (inferred): 3/5, Public data and a clear modelling approach, but the custom RADMC-3D+uvsim+MCMC pipeline and imaging details are not provided.
- Rediscovery candidate: no, Main results depend on a custom visibility-fitting pipeline whose setup is incomplete.

## Links

- Method: Matra et al. 2015 (cite: Matra2015) (Non-LTE CO mass code and CO search method)
- Method: Marino et al. 2016 (cite: Marino2016) (Dirty channel map CO search and vertical structure constraints)
- Method: Kennedy et al. 2010 (cite: Kennedy2010) (Self-stirred disc model)
- Companion: Duchene et al. 2014 (cite: Duchene2014) (Herschel resolved observations of eta Corvi)
- Companion: Lebreton et al. 2016 (cite: Lebreton2016) (Herschel and Keck Interferometer constraints on hot dust)
- Related: DEBRIS

## Checks

```json
{
 "quotes": 80,
 "quotes_ok": 80,
 "quote_pass_rate": 1.0,
 "quotes_too_long": 0,
 "unsupported_facts": 0,
 "project_codes": 1,
 "codes_not_in_text": [],
 "codes_not_in_obscore": [],
 "obscore_codes_not_in_card": [],
 "codes_printed_but_missing": [],
 "numeric_results": 14,
 "numeric_problems": 0,
 "fill": {
  "facts": 88,
  "stated": 59,
  "rate": 0.67
 },
 "evidence_ok": true
}
```
