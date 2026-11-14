# The MUSE Ultra Deep Field (MUDF). V. Characterizing the Mass─Metallicity Relation for Low-mass Galaxies at z ∼ 1─2

`2024ApJ...966..228R` | The Astrophysical Journal 2024 | first author: Revalski, Mitchell | arXiv: 2403.17047 | DOI: 10.3847/1538-4357/ad382c

Card schema 1.0 | model claude-sonnet-5-5 | depth light | type multi_facility_alma_minor

## Science

- Fields: nearby_galaxies, high_z_galaxies
- Question: What is the gas-phase mass-metallicity relation of low-mass galaxies at z~1-2 (down to M*~10^7.5 Msun), and how does it depend on SFR and environment, using HST WFC3 grism and VLT MUSE spectroscopy in the MUDF  
  > "we extend the gas-phase mass-metallicity relation (MZR) at $z\approx\,$1$\,$–$\,$2 down to stellar masses of M$_{\star}$ $\approx$ 10$^{7.5}$ M$_{\odot}$." (abstract)
- Target **MUSE Ultra Deep Field (MUDF)**: coordinates _not stated_; z/distance galaxies at z = 0.23 - 2.39; two quasars at z ~ 3.22  
  > "The MUDF is a unique $\approx$ 2$'$ $\times$ 2$'$ legacy field because it contains two closely-spaced quasars at $z\approx$ 3.22" (Introduction); distance from spectroscopic redshifts from MUSE and WFC3 emission line fits  
  > "The MUDF is a unique $\approx$ 2$'$ $\times$ 2$'$ legacy field because it contains two closely-spaced quasars at $z\approx$ 3.22" (Introduction)

## Data provenance

- ALMA projects: 2021.1.00285.S
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
- Other facility **VLT MUSE**: 142 hours of optical IFU spectroscopy (4600-9350 A, R~2000-4000)  
  > "consist of 142 hours of integral field unit spectroscopy in the optical (4600 $-$ 9350 Å) with a spectral resolution of $R\approx$ 2000 $-$ 4000." (2.1 Survey Overview)
- Other facility **HST WFC3/IR G141 grism and F140W imaging**: 90 orbits of near-infrared grism spectroscopy and imaging (PID 15637)  
  > "We obtained 90 orbits of WFC3/IR G141 grism spectroscopy (1.0 $-$ 1.7 $\mu$m) and F140W imaging in HST Cycle 26" (2.1 Survey Overview)
- Other facility **HST F336W, WFPC2 F702W and F450W**: Photometry for SED modeling  
  > "that provide five-filter photometry of the field for detailed SED modeling." (2.1 Survey Overview)
- External data: Local MZR/FMR calibrations (Table 5 gamma vs SFR) used to extrapolate low-mass slope  
  > "we use the values provided in Table 5 of (cite: Curti2020) to extrapolate $\gamma$ to the lower SFRs covered by our observations" (4.3 The Mass-Metallicity-SFR Relation) [from (cite: Curti2020)]
- External data: Group catalog from Friends-of-Friends algorithm  
  > "We used our group catalog developed in (cite: Dutta2023) to separate galaxies by environment" (4.4 The Role of Environment) [from (cite: Dutta2023)]

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

- Emission line fitting routine and Bayesian metallicity method with Curti2017 calibrations  
  > "We started with the emission line identification and [fitting routine](https://github.com/HSTWISP/wisp_analysis/tree/ahenry_mzr) described in (cite: Henry2021)" (2.2 Spectral Fitting) [from (cite: Henry2021)]
- HST grism custom calibration and photometric catalog  
  > "The observing strategy and custom-calibration for the HST imaging and grism spectroscopy are detailed extensively in (cite: Revalski2023)" (2.1 Survey Overview) [from (cite: Revalski2023)]

### Not stated but needed to reproduce (our reading)

- ALMA data are not used in this paper
- Priors in the Bayesian metallicity model beyond reference to Henry2021
- Best-fit MZR parameter values (in figure only)
- Details of SPS fitting (Fossati et al. in prep)

## Analysis recipe

1. **fit emission lines in MUSE+WFC3 spectra**: Continuous wavelet transform detection, spline continuum, simultaneous Gaussian line fits with doublet ratio and redshift constraints  
  > "a cubic spline is first fit to the continuum of the WFC3 and MUSE spectra simultaneously, making an initial guess of the source redshift based on the strongest emission line." (2.2 Spectral Fitting)
   - software: SciPy, wisp_analysis
   - parameter: minimum 4 sigma integrated line detection; delta z up to 0.00334 between line groups  
  > "These sets of lines are allowed to vary from one another by up to $\delta z$ = 0.00334 (1000 km s$^{-1}$)" (2.2 Spectral Fitting)
   - assumption: [N II] 6585 fixed to 10% of Halpha when in grism  
  > "we fix the flux of \[N II\] $\lambda$6585 to 10% of H$\alpha$ in the fitting procedure" (2.2 Spectral Fitting)
   - fitting: _not stated_
   - validation: Visual inspection; 97% recovery of sources found by other methods  
  > "recovers 97% of sources that were identified by visual inspection or through other automated line finding routines." (2.2 Spectral Fitting)
2. **derive stellar masses and SFRs**: SED fitting of photometry and MUSE spectra with MC-SPF, BC03 models, Chabrier IMF, exponentially declining SFH, stellar metallicity iterated  
  > "simultaneously fitting the multiwavelength photometry and the MUSE spectra (when available) with the Monte Carlo Spectro-Photometric Fitter (MC-SPF) code" (3.1 Stellar Population Synthesis Models)
   - software: MC-SPF
   - assumption: double Calzetti attenuation, young stars 2.27 x A_V  
  > "while the same curve is normalised by 2.27 $\times A_V$ for stars younger than 10 Myr" (3.1 Stellar Population Synthesis Models)
   - fitting: _not stated_
   - validation: _not stated_
3. **select star-forming sample and stack spectra**: [O III] S/N>=3, MEx AGN removal, S/N>=5 samples binned in six mass bins, median stacks with bootstrap errors  
  > "A median spectrum is then calculated for each mass bin, and the uncertainties are determined using bootstrap resampling (cite: Henry2021)." (3.3 Subsample Construction)
   - fitting: _not stated_
   - validation: Individual galaxies compared with stacks; adding next highest-mass targets changes metallicity by <0.04 dex  
  > "the derived metallicities agree to within 0.04 dex, which is the size of our Bayesian grid interval, in all three cases." (5 Discussion)
4. **derive metallicities (strong-line Bayesian and direct method)**: Bayesian Curti2017 R2, R3, O32 calibrations; direct Te method with PyNeb for [O III]4363 and 1666 sources  
  > "We then use PyNeb (v1.1.17; (cite: Luridiana2015)) to convert the \[O III\] $\lambda$4363 / $\lambda$5007 and $\lambda$1666 / $\lambda$5007 ratios to electron temperatures" (3.5.2 Direct Method)
   - software: PyNeb
   - parameter: n_e = 250 cm^-3  
  > "We assume an electron density of n$_e =$ 250 cm$^{-3}$" (3.5.2 Direct Method)
   - assumption: solar 12+log(O/H)=8.69  
  > "adopt a solar value of 12 + log(O/H)$_{\odot}$ = 8.69 $\pm$ 0.05" (Introduction)
   - fitting: Bayesian framework with mostly flat priors  
  > "In most cases the priors have flat distributions except when informed by emission line diagnostics" (3.5.1 Bayesian Method)
   - validation: Strong-line vs direct method comparison for 12 sources  
  > "systematic offset of only 0.03 dex and a dispersion of 0.17 dex between the two methods" (4.1 Validating Strong-line Calibrations with the T$_{e}$ Method)
5. **fit MZR and M-Z-SFR relation**: Curti2020 functional form fit with LMFIT jointly with Henry2021 data; gamma as function of SFR  
  > "We used the [LMFIT](https://lmfit.github.io//lmfit-py/) package (cite: Newville2023) to simultaneously fit our results with those of (cite: Henry2021)" (4.2 The Mass-Metallicity Relation)
   - software: LMFIT
   - fitting: _not stated_
   - validation: Comparison to Henry2021, Sanders, He2024  
  > "These results are also very consistent with the recent study by (cite: He2024) at similar redshifts." (4.2 The Mass-Metallicity Relation)

## Software

- **SciPy** v1.2.1: CWT emission line detection  
  > "within the [SciPy](https://www.scipy.org) (v1.2.1) [signal](https://docs.scipy.org/doc/scipy/reference/signal.html) package" (2.2 Spectral Fitting)
- **PyNeb** v1.1.17: direct-method temperatures and abundances  
  > "We then use PyNeb (v1.1.17; (cite: Luridiana2015))" (3.5.2 Direct Method)
- **LMFIT** : fitting MZR  
  > "We used the [LMFIT](https://lmfit.github.io//lmfit-py/) package (cite: Newville2023)" (4.2 The Mass-Metallicity Relation)
- **Cloudy** : photoionization models for doublet ratio limits  
  > "based on atomic physics and Cloudy photoionization models (cite: Ferland2017)" (2.2 Spectral Fitting)
- **MC-SPF** : stellar mass and SFR from SED fitting  
  > "Monte Carlo Spectro-Photometric Fitter (MC-SPF) code (cite: Fossati2018)" (3.1 Stellar Population Synthesis Models)

## Numeric results

| quantity | value | uncertainty | units | step | quote |
|---|---|---|---|---|---|
| MZR metallicity at log M*~7.5, z~1-2 | 7.8 | 0.1 | 12+log(O/H) | 5 | log(O/H) + 12 $\approx$ 7.8 $\pm$ 0.1 (15% solar) at log(M$_{\star}$/M$_{\odot}$) $\approx$ 7.5 |
| Strong-line vs direct offset | 0.03 | dispersion 0.17 dex | dex | 4 | systematic offset of only 0.03 dex and a dispersion of 0.17 dex between the two methods |
| MZR offset from local | ~0.3 | not stated | dex | 5 | We confirm that the MZR resides $\sim$0.3 dex lower in metallicity than local galaxies |

## Qualitative findings


## Claim tuples

- H: Strong-line calibrations are valid at z~2.3 | E: Compare Bayesian strong-line and direct Te metallicities for 12 sources | R: offset 0.03 dex, dispersion 0.17 dex | F: Calibrations valid up to z~2.5 | **supported**
- H: The MZR turns over at low mass at z~1-2 | E: Stacked spectra in six mass bins | R: metallicity decreases to 7.8 at 10^7.5 | F: no turnover | **supported**
- H: Group galaxies are more metal rich than isolated | E: FoF groups, KS test | R: 0.1-0.2 dex enhancement | F: not statistically significant | **partially**

## Reasoning

- Why this data: _not stated_
- Why this method: _not stated_
- How they decided it was enough: _not stated_
- Limitation (authors): Small number of galaxies with individual metallicities limits environment comparison  
  > "there are a small number of galaxies with individual metallicity measurements between the environments" (6 Conclusions)
- Caveat (inferred, ours): ALMA plays no role in the analysis
- Caveat (inferred, ours): Stacks in lowest mass bin contain only 9 galaxies

## Reproducibility

- Data public (paper): _not stated_
- Products in archive: _not stated_
- Code: Analysis code at github.com/mrevalski/mudf_analysis and wisp_analysis  
  > "<https://github.com/mrevalski/mudf_analysis>" (Software)
- Missing: SPS fitting details (in preparation)
- Missing: Extinction priors from Henry2021
- Data volume (inferred): Not applicable for ALMA; HST and MUSE products of tens of GB
- Score (inferred): 3/5, Public HST/MUSE data and code, but ALMA unused and some methods deferred to other papers.
- Rediscovery candidate: no, ALMA data is not part of the analysis.

## Links

- Method: (cite: Henry2021) (Bayesian metallicity method and line fitting)
- Method: (cite: Revalski2023) (HST data calibration)
- Companion: (cite: Fossati2019) (MUDF MUSE survey)
- Related: MUDF
- Related: WISP

## Checks

```json
{
 "quotes": 40,
 "quotes_ok": 40,
 "quote_pass_rate": 1.0,
 "quotes_too_long": 0,
 "unsupported_facts": 0,
 "project_codes": 1,
 "codes_not_in_text": [],
 "codes_not_in_obscore": [],
 "obscore_codes_not_in_card": [],
 "codes_printed_but_missing": [],
 "numeric_results": 3,
 "numeric_problems": 0,
 "fill": {
  "facts": 77,
  "stated": 32,
  "rate": 0.416
 },
 "evidence_ok": true
}
```
