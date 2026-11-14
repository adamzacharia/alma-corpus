# Compact Ionized Gas Region Surrounded by Porous Neutral Gas in a Dusty Lyman Break Galaxy at Redshift z = 8.312

`2025ApJ...990...29H` | The Astrophysical Journal 2025 | first author: Hagimoto, Masato | arXiv: 2506.20734 | DOI: 10.3847/1538-4357/ade87e

Card schema 1.0 | model claude-sonnet-5-5 | depth light | type theory_or_simulation_compared_to_alma

## Science

- Fields: high_z_galaxies
- Question: What are the ionization parameter, gas density and neutral gas (PDR) covering fraction of the ISM in the z=8.312 LBG MACS0416_Y1, derived by fitting CLOUDY multi-phase photoionization models to ALMA line/continuum and HST luminosities?  
  > "We construct a multi-phase ISM model incorporating the neutral gas covering fraction ($cov_\mathrm{PDR}$). The best-fit model reveals a $cov_\mathrm{PDR}\approx25 \%$" (abstract)
- Target **MACS0416_Y1**: coordinates _not stated_; z/distance z = 8.312  
  > "Follow-up observations with ALMA identified the spectroscopic redshift to be $z=8.312$" (3 Target); "moderately gravitationally magnified ($\mu_\mathrm{g}=1.43\pm0.04$" (2 Target: MACS0416_Y1); distance from ALMA [O III]88 and [C II]158 detections (Tamura2019; Bakx2020CII)  
  > "Follow-up observations with ALMA identified the spectroscopic redshift to be $z=8.312$" (3 Target); "moderately gravitationally magnified ($\mu_\mathrm{g}=1.43\pm0.04$" (2 Target: MACS0416_Y1)

## Data provenance

- ALMA projects: 2016.1.00117.S, 2017.1.00225.S, 2017.1.00486.S, 2018.1.01241.S
- bands: _not stated_
- frequencies and spectral setup: _not stated_
- continuum bandwidth: _not stated_
- arrays: _not stated_
- configurations: _not stated_
- baselines: _not stated_
- angular resolution: _not stated_
- max recoverable scale: _not stated_
- sensitivity: _not stated_
- time on source: _not stated_
- observing dates: _not stated_
- pi or archival as stated: _not stated_
- Line: [O III] 88 μm (not stated)
- Line: [C II] 158 μm (not stated)
- Other facility **HST/WFC3**: F140W photometry (via Ma2024) used for UV luminosity and SED normalization  
  > "We calculate the UV luminosity based on the photometry of HST/F140W (rest-frame $1500$ Å) provided by (cite: Ma2024)." (Table 2)
- Other facility **JWST**: NIRCam photometry and NIRSpec MSA optical line luminosities (from literature) used to validate the model  
  > "which were obtained from the JWST/NIRSpec MSA observations (Table 2 of (cite: Harshan2024))" (4.2)
- External data: [O III]88 and [C II]158 fluxes converted to luminosities  
  > "We calculate the line luminosities of \[O III\]$~88~\mathrm{\mu m}$ and \[C II\]$~158~\mathrm{\mu m}$ from the fluxes reported by (cite: Tamura2019) and (cite: Bakx2020CII), respectively." (Table 2 footnote) [from (cite: Tamura2019); (cite: Bakx2020CII)]
- External data: HST/F140W photometry and JWST/HST SED photometry  
  > "We calculate the UV luminosity based on the photometry of HST/F140W (rest-frame $1500$ Å) provided by (cite: Ma2024)." (Table 2) [from (cite: Ma2024)]
- External data: Magnification factor 1.43  
  > "Here, we assume the magnification factor of $1.43$ (cite: Kawamata2016; Tamura2019)." (3.2 Comparison with observations) [from (cite: Kawamata2016; Tamura2019)]
- External data: Dust temperature 80 K  
  > "We adopt the dust temperature of $80~\mathrm{K}$ in the fiducial model based on (cite: Bakx2020CII)." (Table 1) [from (cite: Bakx2020CII)]
- External data: JWST NIRSpec optical line luminosities  
  > "which were obtained from the JWST/NIRSpec MSA observations (Table 2 of (cite: Harshan2024))" (4.2) [from (cite: Harshan2024)]
- Simulation/model as data: Grid of CLOUDY 17.03 models with BPASS v2.0 binary stellar populations, varying log n_H,c (1.0-4.0), log U (-4.0-0.0), cov_PDR (0-1)  
  > "We generated a grid of models by varying the above three parameters within the range below" (3.1 Model parameters)

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

- Two-phase (HII + PDR) model with depth-dependent density law and A_V=5 PDR stopping  
  > "Our model calculations for PDRs were stopped where the $V$-band dust extinction, $A_\mathrm{V}$ magnitude, is five to go sufficiently in depth, following (cite: Cormier2019)." (3.1 Model parameters) [from (cite: Cormier2019; Ramambason2022)]
- Stellar age 4 Myr, continuous SF, Z=0.2 Zsun, CMB at z=8.3118  
  > "We assume a continuous star formation for $4~\mathrm{Myr}$ and a stellar metallicity of $0.2~\mathrm{Z_\odot}$, which were obtained by the rest-frame UV to FIR SED fits (cite: Tamura2019)." (3.1 Model parameters) [from (cite: Tamura2019)]

### Not stated but needed to reproduce (our reading)

- ALMA calibration and imaging details (all from earlier papers)
- Measured [O III], [C II] and continuum fluxes (only luminosities given)
- Exact rest frequencies and cosmology-to-luminosity conversion details
- Exact CLOUDY input scripts and the way PDR-only and HII-only models are combined
- Which three luminosity ratios define the chi2 (ratios with [O III]88 as denominator: [C II], UV, IR assumed)
- Random seed for Monte Carlo

## Analysis recipe

1. **Compile observed luminosities**: Convert literature ALMA line fluxes, HST UV photometry, and a modified blackbody IR luminosity into magnification-corrected luminosities  
  > "We obtain the infrared luminosity (rest-frame $8$–$1000~\mathrm{\mu m}$) based on the single dust continuum detection at $\lambda_\mathrm{rest}\approx 90~\mathrm{\mu m}$" (Table 2)
   - software: Astropy
   - parameter: beta_d = 2.0, Td = 80 K, mu = 1.43, L_IR error 50%  
  > "We assume the error of the infrared luminosity to be $50~\%$, corresponding to a dust temperature uncertainty of $\sim\pm10~\mathrm{K}$." (Table 2)
   - fitting: _not stated_
   - validation: _not stated_
2. **Build CLOUDY model grid**: Spherical HII region + PDR models; L_out=(1-cov)L_HII + cov L_HII+PDR  
  > "$L_\mathrm{out} = \left(1-cov_\mathrm{PDR}\right)L_\mathrm{\textsc{H\,ii}}+cov_\mathrm{PDR}L_\mathrm{\textsc{H\,ii}+PDR}$" (3.1 Model parameters)
   - software: CLOUDY, BPASS
   - parameter: log n_H,c 1.0-4.0 step 0.1; log U -4.0-0.0 step 0.1; cov_PDR 0-1 step 0.01  
  > "$\log U$ | \[-4.0:0.0, 0.1 intervals\]" (Table 1)
   - assumption: Zgas=Zstar=0.2 Zsun, solar abundances except He, MW grains, HII stop at H+/Htot=0.01, PDR stop at A_V=5  
  > "$Z_\mathrm{gas}=0.2~\mathrm{Z_\odot}(=Z_\mathrm{star})$" (Table 1)
   - fitting: _not stated_
   - validation: _not stated_
3. **Fit model to luminosity ratios**: chi2 minimization over the grid with 3 luminosity ratios; 10,000 Monte Carlo perturbations; median and 34th percentiles  
  > "we repeated the fitting procedure $10,000$ times, each time perturbing the observed ratios by adding random Gaussian noise" (3.2 Comparison with observations)
   - software: Scipy, NumPy
   - fitting: Chi2 minimization on grid, Gaussian noise Monte Carlo; no priors stated  
  > "We searched for the best-fit parameter sets by minimizing the $\chi^2$" (3.2 Comparison with observations)
   - validation: Predicted SED and optical line luminosities compared with HST/JWST data; seven models with varied fixed parameters  
  > "Figure [6](#fig:resultcomparison) summarizes the best-fit value with the central $68$ percent confidence interval of each parameter predicted for a total of seven models" (5.3)
4. **Derive HII region size**: Stromgren radius from CLOUDY where H0/Htot=0.5, D=2 r_s  
  > "In the CLOUDY code, $r_\mathrm{s}$ is defined as the point where the neutral hydrogen fraction reaches $\mathrm{H^0}/\mathrm{H_\mathrm{tot}}=0.5$." (5.2)
   - software: CLOUDY
   - fitting: _not stated_
   - validation: Compared with local compact HII size-density relation (Kim2001)  
  > "follow the local size–density relation presented in (cite: Kim2001)" (5.2)

## Software

- **CLOUDY** 17.03: Photoionization modeling of HII region and PDR  
  > "We used the photoionization code CLOUDY version 17.03 (cite: Ferland2017) to construct the multi-phase ISM model of Y1." (3.1 Model parameters)
- **BPASS** 2.0: Binary stellar population incident spectra  
  > "The stellar component is modeled using the Binary Population and Spectral Synthesis (BPASS) code version 2.0" (3.1 Model parameters)
- **Astropy, matplotlib, NumPy, pandas, SciPy, xarray** : general analysis and plotting (listed in Software section)  
  > "Cloudy (cite: Ferland2017), Astropy (cite: astropy2013; astropy2018; Astropy2022), matplotlib (cite: Hunter07), NumPy (cite: Harris20)" (Software)

## Numeric results

| quantity | value | uncertainty | units | step | quote |
|---|---|---|---|---|---|
| cov_PDR | 0.25 | +0.19/-0.14 | dimensionless | 3 | $cov_\mathrm{PDR}=0.25^{+0.19}_{-0.14}$, $\log n_\mathrm{H,c}/\mathrm{cm^{-3}}=2.7^{+0.2}_{-0.55}$, and $\log U=-1.9\pm0.2$ |
| log n_H,c | 2.7 | +0.2/-0.55 | log cm^-3 | 3 | $\log n_\mathrm{H,c}/\mathrm{cm^{-3}}=2.7^{+0.2}_{-0.55}$ |
| log U | -1.9 | ±0.2 | dimensionless | 3 | $\log U=-1.9\pm0.2$ |
| HII region diameter | 0.90 | not stated | pc | 4 | Our model estimates $r_\mathrm{s}=0.45~\mathrm{pc}$, corresponding to the H II region size of $D=0.90~\mathrm{pc}$ in diameter. |
| cov_PDR for Td=100 K | 0.55 | not stated | dimensionless | 3 | Although the obtained $cov_\mathrm{PDR}=0.55$ is consistent with the fiducial model due to the large error |
| Model Te from [O III]4364/5008 | 13200 | not stated | K | 3 | is $T_\mathrm{e}\approx13200~\mathrm{K}$, which is lower than (cite: Harshan2024) |

## Qualitative findings

- Fully covered PDR (cov_PDR=1) is ruled out, even for Td=100 K  
  > "the $cov_\mathrm{PDR}$ distribution clearly rules out a fully covered scenario ($cov_\mathrm{PDR}=1$)" (4.1)
- Model underestimates 2000-4000 Å photometry by ~70% and [O III]4364 and [O II] lines by ~2x, suggesting an additional low-ionization component  
  > "our model underestimates the flux densities at $2000\lesssim\lambda_\mathrm{rest}/\mathrm{\AA}\lesssim4000$ (JWST/F200W, 277W, F356W, F410M) by $\sim 70\%$." (4.2)

## Claim tuples

- H: Is the neutral gas around the ionized region in Y1 porous, enabling ionizing photon escape? | E: Fit CLOUDY two-phase models to L[OIII], L[CII], L_UV, L_IR ratios | R: cov_PDR = 0.25 (+0.19/-0.14) | F: About 75% of the HII region surface is exposed to intercloud space | **supported**
- H: Does the conclusion depend on fixed parameters? | E: Varied SFH, age, metallicity, C/O, and Td | R: All variants consistent within errors; cov_PDR=1 rejected in all | F: Porous structure is robust | **supported**
- H: Are the HII regions young/compact? | E: Stromgren radius from best-fit parameters | R: D = 0.90 pc | F: Comparable to local compact HII regions, so early evolutionary stage | **partially**

## Reasoning

- Why this data: _not stated_
- Why this method: Multi-phase modeling can break degeneracy between ionizing sources and gas conditions  
  > "The key to resolving the degeneracy between ionizing sources and gas physical conditions lies in performing more detailed modeling of the ISM properties." (1 Introduction)
- Alternative: Density-bounded HII region omitted to reduce free parameters  
  > "we omit the density-bounded H II region (cite: Beckman2000; Nakajima-Ouchi2014) in our model to decrease the number of free parameters." (3.1 Model parameters)
- How they decided it was enough: _not stated_
- Limitation (authors): Only three free parameters due to few observables; single-phase ionized gas cannot reproduce [O II]  
  > "our modeling assumes a single-phase ionized gas component characterized by a single set of gas density and ionization parameter." (4.2)
- Caveat (inferred, ours): Only 3 observables constrain 3 free parameters, so the fit is nearly saturated
- Caveat (inferred, ours): Td and L_IR rely on a single continuum point
- Caveat (inferred, ours): Inferred cov_PDR depends on assumed Td and metallicity
- Caveat (inferred, ours): Magnification of integrated galaxy applied uniformly across components

## Reproducibility

- Data public (paper): ALMA projects listed in acknowledgments; HST from MAST  
  > "HST data presented in this paper was obtained from the Mikulski Archive for Space Telescopes (MAST) at the Space Telescope Science Institute (STScI)." (Acknowledgments)
- Products in archive: _not stated_
- Missing: Observed flux values and exact luminosity conversion
- Missing: CLOUDY input scripts
- Missing: Exact BPASS spectra files used
- Missing: Tamura2019/Bakx2020CII flux numbers
- Data volume (inferred): Negligible (<1 GB); uses published luminosities, no ALMA reprocessing
- Score (inferred): 4/5, Model is well described with grid and chi2 definition, but needs literature fluxes and CLOUDY scripts; no ALMA data reduction.
- Rediscovery candidate: no, Analysis uses published luminosities and a CLOUDY grid rather than public ALMA data reduction; the recipe is incomplete in details.

## Links

- Method: (cite: Cormier2019) (Multi-phase ISM model with PDR porosity, density law)
- Method: (cite: Ferland2017) (CLOUDY code)
- Companion: (cite: Tamura2019) (ALMA [O III] and continuum detection)
- Companion: (cite: Bakx2020CII) (ALMA [C II] and Td constraint)
- Companion: (cite: Harshan2024) (JWST NIRSpec spectrum for validation)
- Related: CANUCS
- Related: PEARLS
- Related: Herschel Dwarf Galaxy Survey

## Checks

```json
{
 "quotes": 51,
 "quotes_ok": 51,
 "quote_pass_rate": 1.0,
 "quotes_too_long": 0,
 "unsupported_facts": 0,
 "project_codes": 4,
 "codes_not_in_text": [],
 "codes_not_in_obscore": [],
 "obscore_codes_not_in_card": [],
 "codes_printed_but_missing": [],
 "numeric_results": 6,
 "numeric_problems": 0,
 "fill": {
  "facts": 75,
  "stated": 32,
  "rate": 0.427
 },
 "evidence_ok": true
}
```
