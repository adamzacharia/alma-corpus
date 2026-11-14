# A benchmark for extreme conditions of the multiphase interstellar medium in the most luminous hot dust-obscured galaxy at z = 4.6

`2024A&A...682A.166F` | Astronomy and Astrophysics 2024 | first author: Fernández Aranda, Román | arXiv: 2401.01871 | DOI: 10.1051/0004-6361/202347869

Card schema 1.0 | model claude-sonnet-5-5 | depth full | type observational_alma_primary

## Science

- Fields: agn_and_quasars, high_z_galaxies, milky_way_ism
- Question: What are the multiphase ISM conditions in the hot dust-obscured galaxy W2246-0526, as constrained by eight FIR fine-structure lines compared with CLOUDY models?  
  > "A comparison of the data to a large grid of CLOUDY radiative transfer models reveals that a high hydrogen density" (abstract)
- Target **W2246-0526 (WISE J224607.6-052634.9)**: coordinates _not stated_; z/distance z = 4.601  
  > "is a Hot DOG at $z_{\mathrm{[CII]}} = 4.601$" (1 Introduction); "in this cosmology, $1\ensuremath{''}$ is equivalent to 6.54 kpc at $z=4.601$" (1 Introduction); distance from [CII] redshift (Díaz-Santos 2016)  
  > "is a Hot DOG at $z_{\mathrm{[CII]}} = 4.601$" (1 Introduction); "in this cosmology, $1\ensuremath{''}$ is equivalent to 6.54 kpc at $z=4.601$" (1 Introduction)

## Data provenance

- ALMA projects: 2017.1.00899.S, 2021.1.00726.S, 2016.1.00668.S, 2013.1.00576.S, 2015.1.00883.S, 2018.1.00119.S
- bands: Bands 3, 4, 6, 7, 8, 9, 10  
  > "We present observations with the Atacama Large Millimeter/submillimeter Array (ALMA) in seven bands, including band 10" (abstract)
- frequencies and spectral setup: _not stated_
- continuum bandwidth: _not stated_
- arrays: ALMA main 12-m array, six projects, Cycles 3-9  
  > "six different ALMA projects observed during Cycles 3 through 9, with a total on-source observation time of 19 hours with the ALMA main 12-m array" (2 Observations)
- configurations: _not stated_
- baselines: _not stated_
- angular resolution: synthesized beams ~0.3'' to 0.5''  
  > "synthesized beams (ranging from $\sim0.3\ensuremath{''}$ to $0.5\ensuremath{''}$ in the different observations)" (2 Observations)
- max recoverable scale: smallest ~2.7'' (Bands 9 and 10)  
  > "The smallest maximum recoverable scale in our observations is $\sim2.7\ensuremath{''}$ for ALMA Bands 9 and 10" (2 Observations)
- sensitivity: _not stated_
- time on source: _not stated_
- observing dates: June 2016 to October 2022 (Table 2 lists 2014-2022)  
  > "These observations were conducted between June 2016 and October 2022" (2 Observations)
- pi or archival as stated: _not stated_
- Line: [OI] 3P1-3P2 (63 um) (4744.8 GHz)
- Line: [OIII] 3P1-3P0 (88 um) (3393.0 GHz)
- Line: [NII] 3P2-3P1 (122 um) (2459.4 GHz)
- Line: [OI] 3P0-3P1 (145 um) (2060.1 GHz)
- Line: [CII] 3P3/2-3P1/2 (158 um) (1900.5 GHz)
- Line: [NII] 3P1-3P0 (205 um) (1461.1 GHz)
- Line: [CI] 3P2-3P1 (370 um) (809.34 GHz)
- Line: [CI] 3P1-3P0 (609 um) (492.16 GHz)
- Line: CO J=7-6 (not stated)
- Other facility **XMM-Newton**: X-ray non-detection upper limit (2-10 keV) from Vito et al. 2018  
  > "reported a non-detection of X-rays in W2246–0526, as part of a study of X-ray properties in Hot DOGs" (4.2.2 X-ray non-detection)
- Other facility **JVLA**: CO(2-1) observations from Díaz-Santos 2018  
  > "used JVLA to observe the CO(2–1) emission line transition and reported the existence of large amounts of molecular gas" (4.3.1 Cold molecular gas)
- External data: CO(2-1) derived M(H2) = 7±1.5e10 Msun with alpha_CO = 0.8  
  > "They estimate a $M(H_2)=7\pm1.5\times10^{10}$ M$_{\odot}$" (4.3.2) [from Díaz-Santos et al. 2018 (cite: diaz2018)]
- External data: XMM-Newton 3 sigma upper limit L(2-10 keV) < 6.9e45 erg/s  
  > "is $<6.9\times10^{45}$ erg s$^{-1}$" (4.2.2) [from (cite: 2018MNRAS.474.4528V)]
- External data: Compilation of high-z quasars, local AGN/ULIRGs/LIRGs line data for comparison  
  > "we show a sample of high-z quasars gathered from the literature" (3.1.7) [from weiss2003; uzgil2016; lu2017; venemans2017; walter2018; lee2019; novak2019; li2020; pensabene2021; meyer2022; farrah2013; pereira2013; rossenberg2015; pereira2017; herrera2018a; diaz2017]
- External data: Bolometric luminosity 3.6e14 Lsun  
  > "bolometric luminosity of $3.6\times10^{14} \ \mathrm{L_{\odot}}$" (1 Introduction) [from (cite: tsai2015; 2018ApJ...868...15T)]
- Simulation/model as data: Grid of CLOUDY v17.00 models over A_V, Z, n_H, alpha_ox, log U (pure AGN SED, constant density, closed geometry)  
  > "grids of photoionization models built using the spectral synthesis code CLOUDY v17.00" (3.2 ISM models)

## Processing

### Calibration

- pipeline or manual: ScriptForPI.py with the observatory pipeline version per cycle; no manual intervention  
  > "We note that the automatic pipeline was run without the need for manual intervention in all bands." (2 Observations)
- casa version: _not stated_
- pipeline version: _not stated_
- archive products used as is: _not stated_
- flux calibrator: Various per execution (J2253+1608, J1924-2914, J2148+0657, Pallas, J2232+117, J0006-0623)  
  > "J2243-0609 | Pallas | 2015.1.00883.S" (Table 2)
- flux scale uncertainty: _not stated_
- self calibration: _not stated_

### Imaging

- task: tclean in CASA v6.4.3  
  > "using the `tclean` task of CASA v6.4.3" (2 Observations)
- deconvolver: Hogbom, threshold 2x rms of each cube  
  > "We run the Hogbom cleaning algorithm (cite: 1974A&AS...15..417H) to a flux density threshold of two times the root mean square of each cube" (2 Observations)
- weighting robust: Briggs, robust = 2.0  
  > "Briggs weighting mode set to a robustness = 2.0 (close to natural weighting)" (2 Observations)
- uv taper: 0.3'' taper tested in appendix; not adopted  
  > "applying a tapering of the visibilities with a value of $0.3\ensuremath{''}$ no extra emission is recovered" (ALMA data reduction)
- cell size: 0.05''  
  > "We adopted a uniform pixel scale of 0.05$\ensuremath{''}$" (2 Observations)
- image size: _not stated_
- masking: radius 1.25'' mask centered on peak pixel (~8.2 kpc)  
  > "using a mask with radius $1.25\ensuremath{''}$ centered at the peak luminosity pixel" (2 Observations)
- multiscale scales: _not stated_
- continuum subtraction: continuum from neighboring line-free channels, uvcontsub  
  > "select the continuum from neighboring line-free channels and subtracting it using the CASA task `uvcontsub`" (2 Observations)
- line free channels: _not stated_
- primary beam correction: _not stated_
- array combination: _not stated_
- smoothing: _not stated_
- final beam: _not stated_
- final rms: _not stated_

### Inherited from earlier work

- Line luminosity formula  
  > "The line luminosities are calculated following (cite: solomon1992):" (2 Observations) [from (cite: solomon1992)]
- Neutral carbon mass formula  
  > "Following (cite: weiss2003), we can derive the neutral carbon mass from the \[CI\]$_{370 \upmu \mathrm{m}}$ line luminosity" (4.3.3) [from (cite: weiss2003)]
- Default CLOUDY grains/PAH size distribution  
  > "with the default grains and polycyclic aromatic hydrocarbons (PAH) size distribution from (cite: 2008ApJ...686.1125A)" (3.2 ISM models) [from (cite: 2008ApJ...686.1125A)]
- CMB heating neglected  
  > "Therefore, following (cite: 2013ApJ...766...13D), we can neglect the CMB heating in the models." (3.2 ISM models) [from (cite: 2013ApJ...766...13D)]
- L_IR = 6.3 x L_FIR scaling  
  > "the scaling used for W2246–0526 in (cite: 2016ApJ...816L...6D)" (3.1.7) [from (cite: 2016ApJ...816L...6D)]

### Not stated but needed to reproduce (our reading)

- Line-free channel ranges and spectral channel widths for each cube
- Continuum uvcontsub fit order
- Exact phase centre/aperture centre coordinates
- Pipeline versions per cycle
- Flux calibration uncertainty
- How errors on fluxes were computed
- Priors and grid-interpolation details of the Bayesian fit, and which ratios entered the fit
- CLOUDY input files/scripts
- Source coordinates

## Analysis recipe

1. **Calibrate and image line cubes**: ScriptForPI pipeline restore, tclean Hogbom cubes, uvcontsub continuum subtraction  
  > "We processed the data with the `ScriptForPI.py` provided through the ALMA science archive" (2 Observations)
   - software: CASA, tclean, uvcontsub
   - parameter: robust 2.0, 0.05'' pixels, threshold 2 rms, 1.25'' mask  
  > "Briggs weighting mode set to a robustness = 2.0 (close to natural weighting)" (2 Observations)
   - fitting: _not stated_
   - validation: Alternative robust=0.5 and taper tested on [CII]  
  > "extended emission is missed when using a robust parameter of $r=0.5$" (ALMA data reduction)
2. **Extract spectra and fit lines**: 0.7'' diameter aperture at peak pixel; single Gaussian fit (center, peak, FWHM free); moment 0 over ±2.75 sigma  
  > "To perform the photometry and extract the spectra we used an aperture of diameter $0.7\ensuremath{''}$ centered at the peak emission pixel" (2 Observations)
   - parameter: upper limits: Gaussian with FWHM 600 km/s and 1 sigma peak  
  > "calculated as the integrated luminosity of a Gaussian assuming a FWHM of 600 km s$^{-1}$ and a peak of $1\upsigma$ detection" (2 Observations)
   - assumption: Aperture contains 99% of flux for the largest beam; no aperture correction  
  > "This aperture size ensures that 99% of the line flux is included" (2 Observations)
   - fitting: single Gaussian  
  > "The continuum-subtracted spectra were then fitted with a single Gaussian" (2 Observations)
   - validation: Non-detections checked with different apertures and channel binning  
  > "we extracted the spectra using different aperture sizes and channel averaging. The lines were not detected in any case." (2 Observations)
3. **Compute line luminosities and ratios**: L_line = 1.04e-3 S dv nu_rest (1+z)^-1 D_L^2; line ratios from Gaussian fits and fixed FWHM  
  > "L_{line}[\mathrm{L_{\odot}}] = 1.04\times10^{-3}\times S_{line}\Delta\upsilon \ \nu_{rest}(1+z)^{-1}D_{\mathrm{L}}^{2}" (2 Observations)
   - assumption: Flat LCDM, H0=70, Omega_M=0.3  
  > "we assume a flat $\Lambda$CDM cosmology with $H_0 = 70$ km s$^{-1}$ Mpc$^{-1}$ and $\Omega_{\mathrm{M}}=0.3$" (1 Introduction)
   - fitting: _not stated_
   - validation: Ratios also computed with FWHM fixed to 600 km/s  
  > "We also report the observed line ratios when the FWHM is fixed to 600 km s$^{-1}$ for all the lines" (3.1)
4. **Fit CLOUDY grid to line ratios**: Bayesian comparison of all line ratios (relative to [CII]) with CLOUDY grid, P = exp(-chi2/2), marginalized posteriors  
  > "we compare all the observed lines with our CLOUDY model grid using a Bayesian framework" (3.4 Best-fit model)
   - software: CLOUDY
   - parameter: grid: A_V 10^1-10^4 mag, Z 0.05-2, nH 10^2-10^5, alpha_ox -1.4 to -0.4, log U -3 to 0.5; 15% model-ratio uncertainty  
  > "An uncertainty of 15% is assumed for the model ratios to account for the sparsity of the parameter grid." (3.4 Best-fit model)
   - assumption: Pure AGN radiation, spherical covering factor unity, constant density, T_BB=1e6 K, alpha_uv=-0.5, alpha_x=-1, cosmic-ray background included  
  > "we thus selected a pure AGN as the source of radiation for the CLOUDY models" (3.2 ISM models)
   - fitting: chi2 over ratios; grid posterior  
  > "we use the $\chi^2$ statistic defined as" (4.2.1)
   - validation: BIC model comparison of fixed alpha_ox=-1.4 vs free; alternative density profile and stellar SEDs tested  
  > "The probability of model $A$ over $B$ is $p(A)=0.15$, and of model $B$ over $A$ is $p(B)=0.85$." (4.2.1)
5. **Derive X-ray, gas mass and neutral carbon implications**: Compare model X-ray flux with XMM limit; estimate cloud hydrogen mass from shell volume; CI mass from Weiss formula with Tex from CI ratio  
  > "we estimate $T_{ex}>37$ K, and therefore $M_{CI}<1.3\times10^7 \ M_{\odot}$" (4.3.3)
   - assumption: optically thin CI lines  
  > "assuming both lines are optically thin" (4.3.3)
   - fitting: _not stated_
   - validation: _not stated_

## Software

- **CASA** v6.4.3: calibration and imaging  
  > "using the `tclean` task of CASA v6.4.3" (2 Observations)
- **CLOUDY** v17.00: photoionization model grids  
  > "CLOUDY v17.00 (cite: 2017RMxAA..53..385F)" (3.2 ISM models)

## Numeric results

| quantity | value | uncertainty | units | step | quote |
|---|---|---|---|---|---|
| [CII] 158um line flux (observed) | 10.5 | 0.4 | Jy km/s | 2 | / \[CII\]$_{158\upmu \mathrm{m}}$ / $10.5 \pm 0.4$ / $11.1 \pm 0.5$ |
| [OI] 63um line flux (observed) | 20.6 | 2.9 | Jy km/s | 2 | / \[OI\]$_{63\upmu \mathrm{m}}$ / $20.6 \pm 2.9$ |
| [NII]122/[NII]205 ratio (Gaussian fit) | 13.8 | 4.2 | dimensionless | 3 | \[NII\]$_{122\upmu \mathrm{m}}$/\[NII\]$_{205 \upmu \mathrm{m}}=13.8 \pm 4.2$ |
| [CII]/[CI]370 ratio | 58 | 29 | dimensionless | 3 | \[CII\]$_{158\upmu \mathrm{m}}$/\[CI\]$_{370 \upmu \mathrm{m}} = 58\pm29$ |
| [OI]63/[CII] ratio | 4.7 | 1.0 | dimensionless | 3 | our observed ratio of $4.7\pm1.0$ |
| Best-fit log nH (posterior mean) | 3.5 (3.44) | 0.37 | log cm^-3 | 4 | $log(n_{\mathrm{H}}) = 3.5 \ \mathrm{cm}^{-3}\ (3.44\pm0.37)$ |
| Best-fit log U | -0.5 (-0.47) | 0.62 | dimensionless | 4 | $log(U) = -0.5 \ (-0.47\pm0.62)$ |
| Best-fit A_V | 316 (222) | +546/-158 | mag | 4 | $A_{\mathrm{V}} = 316 \ \mathrm{mag}\ (222_{-158}^{+546})$ |
| Best-fit alpha_ox | -0.8 (-0.78); lower limit >= -0.8 | 0.29 | dimensionless | 4 | $\alpha_{\mathrm{ox}} = -0.8 \ (-0.78\pm0.29)$ |
| Best-fit metallicity | 0.5 (0.49) | +0.67/-0.29 | Zsun | 4 | $Z = 0.5 \ Z_{\odot}\ (0.49_{-0.29}^{+0.67})$ |
| Reduced chi-square of best fit | 3.34 | not stated | dimensionless | 4 | reduced chi-square $\chi_{\nu}^{2}=3.34$ |
| Model B probability (BIC) | 0.85 | not stated | dimensionless | 4 | $p(B)=0.85$ |
| Hydrogen column density | 1.2e24 | +3.1/-0.8 e24 | cm^-2 | 5 | $N_{\mathrm{H}}=(1.2_{-0.8}^{+3.1})\times10^{24}$ cm$^{-2}$ |
| Neutral carbon mass upper limit | <1.3e7 | not stated | Msun | 5 | $M_{CI}<1.3\times10^7 \ M_{\odot}$ |
| Cloud hydrogen mass upper limit | <0.6e11 | not stated | Msun | 5 | $M_{H}<0.6\times10^{11} M_{\odot}$ |
| CO(7-6) luminosity | 0.59 | 0.04 | 1e9 Lsun | 3 | with a luminosity of $0.59\pm0.04\times10^9$ L$_{\odot}$ |

## Qualitative findings

- [OIII]88 non-detection is explained by XDR conditions suppressing it  
  > "this component explains the a priori very surprising non-detection of the \[OIII\]$_{88\upmu \mathrm{m}}$ emission line" (abstract)

## Claim tuples

- H: Can a single AGN-driven CLOUDY component reproduce the line ratios? | E: Bayesian grid fit of line ratios | R: nH~3e3, A_V~300, log U=-0.5, alpha_ox>=-0.8, chi2_nu=3.34 | F: Extreme ionization and X-ray dominated region needed | **supported**
- H: Why is [OIII]88 not detected? | E: CLOUDY ionization structure | R: Oxygen in higher ionization states in XDR | F: [OIII] suppressed in XDRs | **supported**
- H: Is the model consistent with X-ray and CO observations? | E: Compare model predictions with XMM limit and JVLA CO(2-1) | R: Model predicts 2x more X-rays and much less CO | F: Additional extended molecular gas component likely obscures X-rays | **partially**

## Reasoning

- Why this data: _not stated_
- Why this method: alpha_ox introduced as free parameter to find a more physical solution  
  > "we introduced $\alpha_{\mathrm{ox}}$ as an additional parameter in order to search for a more physical solution" (4.2.1)
- Alternative: Constant pressure and stellar SEDs rejected; none matched observed ratios  
  > "none of the test grids fall in the region of the parameter space where the observed emission ratios lay" (CLOUDY modeling)
- How they decided it was enough: _not stated_
- Limitation (authors): Simple geometry and single homogeneous cloud; continuum and CO SLED not modeled  
  > "we do not attempt to fit the continuum emission" (3.2 ISM models)
- Caveat (inferred, ours): Single-zone AGN-only model ignores star formation and multiphase mixing
- Caveat (inferred, ours): chi2_nu of 3.3 with few ratios and few dof, parameters degenerate
- Caveat (inferred, ours): Different resolutions/apertures across bands; flux calibration uncertainties not propagated
- Caveat (inferred, ours): Unknown flux scale uncertainty at Band 9/10

## Reproducibility

- Data public (paper): Data from archival ALMA projects acknowledged  
  > "This paper makes use of the following ALMA data: ADS/JAO.ALMA#2013.1.00576.S" (Acknowledgements)
- Products in archive: _not stated_
- Missing: Line-free channels and spectral setup
- Missing: Fitting priors/interpolation details
- Missing: CLOUDY input scripts
- Data volume (inferred): ~100-300 GB raw across six projects
- Score (inferred): 3/5, Imaging parameters and grid ranges are stated, but cube spectral details, fit details and CLOUDY inputs are missing.
- Rediscovery candidate: yes, Archival data, stated imaging recipe, numeric line fluxes and model parameters.

## Links

- Method: (cite: 2017RMxAA..53..385F) (CLOUDY v17)
- Method: (cite: solomon1992) (line luminosity formula)
- Companion: (cite: diaz2018) (CO(2-1) and dusty merger of W2246-0526)
- Companion: (cite: 2016ApJ...816L...6D) ([CII] discovery)

## Checks

```json
{
 "quotes": 91,
 "quotes_ok": 91,
 "quote_pass_rate": 1.0,
 "quotes_too_long": 0,
 "unsupported_facts": 0,
 "project_codes": 6,
 "codes_not_in_text": [],
 "codes_not_in_obscore": [],
 "obscore_codes_not_in_card": [],
 "codes_printed_but_missing": [],
 "numeric_results": 16,
 "numeric_problems": 0,
 "fill": {
  "facts": 82,
  "stated": 54,
  "rate": 0.659
 },
 "evidence_ok": true
}
```
