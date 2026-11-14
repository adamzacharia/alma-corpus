# The Disk Substructures at High Angular Resolution Project (DSHARP). VI. Dust Trapping in Thin-ringed Protoplanetary Disks

`2018ApJ...869L..46D` | The Astrophysical Journal Letters 2018 | first author: Dullemond, Cornelis P. | arXiv: 1812.04044 | DOI: 10.3847/2041-8213/aaf742

Card schema 1.0 | model claude-sonnet-5-5 | depth full | type large_program_or_survey

## Science

- Fields: protoplanetary_disks
- Question: Are the narrow high-contrast dust rings in DSHARP disks caused by dust trapping in radial pressure bumps, and what does this constrain about turbulence and grain size?  
  > "In this paper we test the hypothesis that these dust rings are caused by dust trapping in radial pressure bumps, and if confirmed, put constraints on the physics of the dust trapping mechanism." (abstract)
- Target **AS 209**: coordinates _not stated_; z/distance 121 pc  
  > "AS 209 |   121   |     0.83      |     1.41      |   35    | 38$\times$36, 68 |" (Table 1); distance from dsharp:andrews (cite)  
  > "AS 209 |   121   |     0.83      |     1.41      |   35    | 38$\times$36, 68 |" (Table 1)
- Target **Elias 24**: coordinates _not stated_; z/distance 136 pc  
  > "Elias 24  |  136   |     0.78      |      6.0      |   29    | 37$\times$24, 82 |" (Table 1); distance from dsharp:andrews (cite)  
  > "Elias 24  |  136   |     0.78      |      6.0      |   29    | 37$\times$24, 82 |" (Table 1)
- Target **HD 163296**: coordinates _not stated_; z/distance 101 pc  
  > "HD 163296 |  101   |     2.04      |     17.0      |   47    | 48$\times$38, 82 |" (Table 1); distance from dsharp:andrews (cite)  
  > "HD 163296 |  101   |     2.04      |     17.0      |   47    | 48$\times$38, 82 |" (Table 1)
- Target **GW Lup**: coordinates _not stated_; z/distance 155 pc  
  > "GW Lup   |  155   |     0.46      |     0.33      |   39    | 45$\times$43, 1  |" (Table 1); distance from dsharp:andrews (cite)  
  > "GW Lup   |  155   |     0.46      |     0.33      |   39    | 45$\times$43, 1  |" (Table 1)
- Target **HD 143006**: coordinates _not stated_; z/distance 165 pc  
  > "HD 143006 |  165   |     1.78      |     3.80      |   19    | 46$\times$45, 51 |" (Table 1); distance from dsharp:andrews (cite)  
  > "HD 143006 |  165   |     1.78      |     3.80      |   19    | 46$\times$45, 51 |" (Table 1)

## Data provenance

- ALMA projects: _none stated_
- bands: Band 6 (1.3 mm, 0.125 cm)  
  > "Planck function at $T_{\mathrm{d}}$ in band 6." (Table 1 notes)
- frequencies and spectral setup: _not stated_
- continuum bandwidth: _not stated_
- arrays: _not stated_
- configurations: _not stated_
- baselines: _not stated_
- angular resolution: Beams ~24-48 mas (Table 1)  
  > "HD 163296 |  101   |     2.04      |     17.0      |   47    | 48$\times$38, 82 |" (Table 1)
- max recoverable scale: _not stated_
- sensitivity: _not stated_
- time on source: _not stated_
- observing dates: _not stated_
- pi or archival as stated: _not stated_
- External data: Radial intensity profiles and ring names for DSHARP disks  
  > "The procedure used to extract these radial profiles from the continuum maps is described by (cite: dsharp:huangrings)." (2 The high-contrast rings) [from (cite: dsharp:huangrings)]
- External data: Stellar parameters, distances, inclinations  
  > "More details, as well as references and uncertainty estimates, can be found in (cite: dsharp:andrews)." (Table 1 notes) [from (cite: dsharp:andrews)]
- External data: DSHARP dust opacity model, kappa_abs=2.0 cm^2/g at a=0.1 cm  
  > "we use the DSHARP dust opacity model (cite: dsharp:birnstiel) for a grain radius of $a=0.1\,\mathrm{cm}$" (Table 1 notes) [from (cite: dsharp:birnstiel)]
- Simulation/model as data: 1-D viscous disk evolution model with single dust species and Gaussian gap, applied to HD 163296 ring 2  
  > "Our model is a 1-D viscous disk evolution model with a single dust component added, which can radially drift and will be prone to radial turbulent mixing." (Planet gaps as dust traps)

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
- final beam: see Table 1 beams (e.g. 38x36 mas AS 209)  
  > "AS 209   |  121   |     0.83      |     1.41      |   35    | 38$\times$36, 68 |" (Table 1)
- final rms: _not stated_

### Inherited from earlier work

- Radial profile extraction (ellipse fit, deprojection, azimuthal averaging)  
  > "The radial intensity profiles were extracted from the images using a procedure similar to that described by (cite: dsharp:huangrings)." (Gauss fitting procedure) [from (cite: dsharp:huangrings)]
- Observations, imaging and source parameters  
  > "For an overview of the ALMA Large Programme we refer to (cite: dsharp:andrews)" (2 The high-contrast rings) [from (cite: dsharp:andrews)]

### Not stated but needed to reproduce (our reading)

- Exact radial profile data files and per-source geometry (PA, center) used
- ALMA project code, observing dates, configurations in this paper
- Imaging parameters (robust, tclean settings) of DSHARP images
- Exact prior ranges and likelihood form for the emcee fit
- Opacity table for DSHARP model vs grain size for a_max limits
- Parameters of the 1-D evolution code (grid, code name) and w_max definition per ring details

## Analysis recipe

1. **Fit Gaussians to ring profiles**: MCMC fit of Gaussian A, r0, sigma to azimuthally averaged deprojected radial intensity profile in a by-eye radial domain  
  > "We use the code emcee (cite: 2013PASP..125..306F) to perform a Markov Chain Monte Carlo (MCMC) procedure to find the set of parameters $(A,r_0,\sigma)$ which have the highest likelihood." (Gauss fitting procedure)
   - software: emcee
   - parameter: 100 walkers, 500 steps, last 250 used; errors multiplied by sqrt(70)  
  > "We use 100 walkers with 500 steps, and use the last 250 steps for our statistics." (Gauss fitting procedure)
   - assumption: Gaussian ring shape; domain chosen by eye  
  > "We choose by eye a radial domain around the bump where we believe a Gaussian description is justified." (Gauss fitting procedure)
   - fitting: emcee MCMC, three parameters  
  > "find the set of parameters $(A,r_0,\sigma)$ which have the highest likelihood" (Gauss fitting procedure)
   - validation: Mock ring test through DSHARP imaging pipeline; comparison with uv-plane widths  
  > "simulate the ALMA visibilities, put these data through the DSHARP imaging pipeline, and extract the radial profile." (Mock ring test)
2. **Deconvolve beam and estimate temperature, scale height**: w_d = sqrt(sigma^2 - sigma_b^2) with effective beam; T_d from irradiated flaring disk; h_p from T_d  
  > "w_d=\sqrt{\sigma^2-\sigma_b^2}" (3 Fitting a Gaussian)
   - parameter: flaring angle phi=0.02, mu=2.3  
  > "We take the flaring angle to be $\varphi=0.02$ which is an estimate based on typical values from models." (3 Fitting a Gaussian)
   - assumption: Gas temperature equals dust temperature  
  > "Assuming that the gas temperature is equal to the dust temperature" (3 Fitting a Gaussian)
   - fitting: _not stated_
   - validation: _not stated_
3. **Optical depth and dust mass**: tau_peak=-ln(1-A_dec/B_nu(T_d)); M_thin from Gaussian; optical depth correction via Gaussian mimicry factor  
  > "\tau_\nu^{\mathrm{peak}} = -\ln\left(1-\frac{A_{\mathrm{dec}}}{B_{\nu}(T_d)}\right)" (4.1 Optically thin approximation)
   - software: SciPy
   - parameter: kappa_abs = 2.0 cm^2/g at 0.125 cm for a=0.1 cm  
  > "yields a dust opacity of $\kappa_\nu^{\mathrm{abs}}(\lambda=0.125\,\mathrm{cm})=2.0{}\,\mathrm{cm}^2/\mathrm{g}$" (4.1 Optically thin approximation)
   - assumption: Zero albedo, no background intensity  
  > "Let us assume that the dust has zero albedo." (4.2 Optical depth corrections)
   - fitting: scipy.optimize.minimize Gaussian fit to mimicked profile  
  > "We use the ` scipy.optimize.minimize()` function of the SciPy library of Python" (Computing dust mass including mild optical depth effects)
   - validation: Compared with CO absorption optical depth of HD 163296 from Isella et al.  
  > "independent evidence from the absorption of CO line emission from the back side of the disk that the optical depth in the two prominent rings is around 0.7" (4.1 Optically thin approximation)
4. **Constrain trapping parameters (alpha/St, w, Sigma_g, grain size)**: Analytic steady-state Gaussian trap model w_d=w(1+psi^-2)^-1/2; alpha/St=[(w/w_d)^2-1]^-1 for w_min and w_max; Toomre Q>2 upper limit on Sigma_g  
  > "\frac{\alpha_{\mathrm{turb}}}{\mathrm{St}} \equiv \psi^{2} = \left[\left(\frac{w}{w_{\mathrm{d}}}\right)^2-1\right]^{-1}" (5.3 Application to the observed rings)
   - parameter: Sc=1; xi_dust=1.67 g/cm^3; example a=0.02 cm  
  > "the average material density of the dust aggregates is $\xi_{\mathrm{dust}}\simeq 1.67{}\,\mathrm{g}/\mathrm{cm}^3$" (5.3 Application to the observed rings)
   - assumption: Perfect trapping, fixed Gaussian pressure bump, no back-reaction  
  > "The pressure bump is assumed to be so strong that the dust trapping in these rings is perfect: no dust escapes." (5 The rings as dust traps)
   - fitting: _not stated_
   - validation: Compared to 1-D numerical drift-diffusion model of a planet gap  
  > "We see that the width of the numerical profile of the dust surface density is more or less consistent with the analytic result" (6 Planet gaps)

## Software

- **emcee** : MCMC fitting of Gaussian ring profiles  
  > "We use the code emcee (cite: 2013PASP..125..306F)" (Gauss fitting procedure)
- **SciPy** : scipy.optimize.minimize to fit mimicked Gaussian  
  > "We use the ` scipy.optimize.minimize()` function of the SciPy library of Python" (Computing dust mass including mild optical depth effects)

## Numeric results

| quantity | value | uncertainty | units | step | quote |
|---|---|---|---|---|---|
| Peak absorption optical depth range | 0.2-0.5 (0.19-0.52) | factor ~2 from T_d | dimensionless | 3 | The rings have peak absorption optical depth in the range between 0.2 and 0.5. |
| AS 209 ring 1 sigma | 3.976 | +0.119/-0.108 | au | 1 | AS 209 / 1 / $0.141_{-0.002}^{+0.002}$ / $74.180_{-0.074}^{+0.072}$ / $3.976_{-0.108}^{+0.119}$ / |
| AS 209 ring 1 w_d/h_p | 0.6 | not stated | dimensionless | 2 | AS 209 / 1 / B74 / 40 / 69 – 79 / 0.14 / 0.17 / 74.2 / 3.98 / 3.38 / 15.8 / 0.45 / 0.6 / 1.9 / 0.46 / 27.0 / 31.5 / |
| AS 209 ring 1 dust mass (optical-depth corrected) | 31.5 | factor ~10 from opacity | Earth masses | 3 | AS 209 / 1 / B74 / 40 / 69 – 79 / 0.14 / 0.17 / 74.2 / 3.98 / 3.38 / 15.8 / 0.45 / 0.6 / 1.9 / 0.46 / 27.0 / 31.5 / |
| Minimum w_d/w (AS 209 ring 1, w=w_max) | 0.17 | not stated | dimensionless | 4 | we find that the strongest dust trapping occurs in AS 209, with $w_d/w$ ratios of 0.17 and 0.21 for rings 1 and 2, respectively. |
| Resolution ratio sigma/sigma_b range | 1.6 to 3.2 | not stated | dimensionless | 2 | All rings are radially resolved, by factors $\sigma/\sigma_b$ ranging from 1.6 (ring B41 of HD 143006) to 3.2 (ring B67 of HD 163296). |
| Grain-size upper limits from opacity | 1 cm to half a meter | not stated | cm | 4 | from opacity arguments we can put strong upper limits on the grain size of 1 cm to half a meter, depending on the ring. |

## Qualitative findings

- Rings in AS 209, Elias 24, GW Lup and outer ring of HD 163296 are narrower than the estimated pressure scale height, evidence for dust trapping  
  > "This is strong evidence for dust trapping being at work." (Conclusions)

## Claim tuples

- H: The narrow DSHARP rings are caused by dust trapping in axisymmetric pressure bumps | E: Gaussian fits to deprojected radial profiles, comparison of w_d to h_p and to the analytic trap model | R: Several rings have w_d < h_p; all have w_d < w_max | F: All rings consistent with dust trapping; no evidence against it | **supported**
- H: Rings may be optically thin | E: Estimated tau_peak from deconvolved amplitude and Planck function with assumed T_d | R: tau_peak 0.2-0.5 | F: Rings are moderately optically thick; dust masses are tens of Earth masses, opacity-limited | **supported**
- H: Combination of very low turbulence and large grains is allowed | E: Derived lower limit alpha_turb >= (a/0.02 cm) alpha_exmp | R: alpha_exmp 1e-4 to few 1e-3 | F: alpha << 5e-4 with a >> 0.1 cm is excluded | **supported**
- H: Dust in rings may reach streaming instability conditions | E: Volume density ratio criterion for AS 209 ring 1 | R: Triggered if Sigma_g <~ 1.4 g/cm^2, vs gravitational instability above 16 | F: Plausible but unproven | **partially**

## Reasoning

- Why this data: _not stated_
- Why this method: Image-plane fitting allows selecting individual rings independently of other emission  
  > "because that allows us to select an individual ring, and study it independently of the emission elsewhere" (3 Fitting a Gaussian)
- Alternative: Grain size distribution as origin of wing excess: model is symmetric so cannot explain asymmetric excess  
  > "However, the model is symmetric, so it cannot explain the asymmetric excess of most rings." (5.4 Including a grain size distribution)
- How they decided it was enough: _not stated_
- Limitation (authors): Dust opacity uncertain by a factor of 10; temperature only estimated  
  > "can easily be wrong by a factor of $10$ upward or downward, with correspondingly large changes in the derived dust mass" (4.1 Optically thin approximation)
- Limitation (authors): Results not definitive; starting point for more complex modeling  
  > "This paper is therefore not meant to give definitive numbers or conclusions." (7.3 Caveats of the models)
- Caveat (inferred, ours): Midplane temperature relies on a fixed flaring angle of 0.02 for all disks
- Caveat (inferred, ours): Gaussian domain chosen by eye; width differs 8-30% from uv-plane fits
- Caveat (inferred, ours): Results depend strongly on opacity model and single grain size
- Caveat (inferred, ours): Rings only 1.6-3 beams wide so deconvolution is delicate

## Reproducibility

- Data public (paper): Not explicitly stated in this paper; data are from DSHARP Large Programme  
  > "The data from the ALMA Large Programme DSHARP (cite: dsharp:andrews) offers an exciting new opportunity" (Introduction)
- Products in archive: _not stated_
- Missing: Radial profile arrays (from Huang et al. 2018a)
- Missing: Per-disk geometry and ring domains beyond Table 1
- Missing: Numerical disk-evolution code details
- Data volume (inferred): Small if starting from published radial profiles; tens to hundreds of GB if from raw DSHARP visibilities
- Score (inferred): 4/5, Equations, tables and fit settings are largely given, but profiles and some parameters come from companion papers.
- Rediscovery candidate: yes, DSHARP data are public, the analytic recipe is explicit, and results are numeric in tables.

## Links

- Method: (cite: dsharp:huangrings) (Radial profile extraction and ring identification)
- Method: (cite: dsharp:birnstiel) (DSHARP opacity model)
- Companion: (cite: dsharp:andrews) (DSHARP overview and stellar parameters)
- Companion: (cite: dsharp:guzman) (uv-plane fits for AS 209)
- Companion: (cite: dsharp:isella) (uv-plane fits and CO optical depth for HD 163296)
- Companion: (cite: dsharp:perez) (uv-plane fits for HD 143006)
- Companion: (cite: dsharp:zhang) (Planet-disk hydrodynamic simulations)
- Related: DSHARP (ALMA Large Programme, 2016.1.00484.L per archive)

## Checks

```json
{
 "quotes": 57,
 "quotes_ok": 57,
 "quote_pass_rate": 1.0,
 "quotes_too_long": 0,
 "unsupported_facts": 0,
 "project_codes": 0,
 "codes_not_in_text": [],
 "codes_not_in_obscore": [],
 "obscore_codes_not_in_card": [
  "2016.1.00484.L"
 ],
 "codes_printed_but_missing": [],
 "numeric_results": 7,
 "numeric_problems": 0,
 "fill": {
  "facts": 87,
  "stated": 45,
  "rate": 0.517
 },
 "evidence_ok": true
}
```
