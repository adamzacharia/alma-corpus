# ALMA Observations of Multiple CO and C Lines toward the Active Galactic Nucleus of NGC 7469: An X-Ray-dominated Region Caught in the Act

`2020ApJ...898...75I` | The Astrophysical Journal 2020 | first author: Izumi, Takuma | arXiv: 2006.09406 | DOI: 10.3847/1538-4357/ab9cb1

Card schema 1.0 | model claude-sonnet-5-5 | depth full | type observational_alma_primary

## Science

- Fields: nearby_galaxies, agn_and_quasars, astrochemistry
- Question: Does the [C I](1-0) to CO/13CO line ratio at ~100 pc scale distinguish the AGN (XDR) from the starburst ring in NGC 7469, and what are the gas conditions and CO/CI-to-H2 conversion factors?  
  > "We thus need high resolution comprehensive observations of C$^0$ and CO lines to faithfully measure line flux (or abundance) ratios in XDRs" (1 Introduction)
- Target **NGC 7469**: coordinates 23h03m15.617s, +08d52m26.00s (ICRS)  
  > "NGC 7469 is an active barred spiral galaxy located at $D = 71.2$ Mpc ($z = 0.01641$ and 1$\ensuremath{''}$ = 334 pc)" (The Target Galaxy NGC 7469); z/distance D = 71.2 Mpc, z = 0.01641  
  > "NGC 7469 is an active barred spiral galaxy located at $D = 71.2$ Mpc ($z = 0.01641$ and 1$\ensuremath{''}$ = 334 pc)" (The Target Galaxy NGC 7469); distance from NED  
  > "NGC 7469 is an active barred spiral galaxy located at $D = 71.2$ Mpc ($z = 0.01641$ and 1$\ensuremath{''}$ = 334 pc)" (The Target Galaxy NGC 7469)

## Data provenance

- ALMA projects: 2017.1.00078.S
- bands: Bands 3, 6, 7, 8  
  > "using the Band 3, 6, 7, and 8 receivers, from 2017 December to 2018 September" (2 Observations and data reduction)
- frequencies and spectral setup: 2 sidebands, 2 spectral windows each, 1.875 GHz per window, ~7.5 GHz total  
  > "Each spectral window has a bandwidth of 1.875 GHz, and two windows were placed to each sideband (upper and lower) to achieve a total frequency coverage of $\sim 7.5$ GHz." (2 Observations and data reduction)
- continuum bandwidth: _not stated_
- arrays: 12m array (two configurations, Bands 3-7); ACA in Band 8; no total power  
  > "The Atacama Compact Array (ACA) was employed in the Band 8 observations for the same purpose: we did not include the total power array observations in this program." (2 Observations and data reduction)
- configurations: _not stated_
- baselines: _not stated_
- angular resolution: ~0.34-0.37 arcsec (~100-120 pc)  
  > "which resulted in angular resolutions of $\sim 0\ensuremath{''}.34-0\ensuremath{''}.37$" (2 Observations and data reduction)
- max recoverable scale: larger than 10 arcsec  
  > "These result in the nominal maximum recoverable scales of our observations larger than 10$\ensuremath{''}$." (2 Observations and data reduction)
- sensitivity: _not stated_
- time on source: _not stated_
- observing dates: 2017 Dec to 2018 Sep  
  > "using the Band 3, 6, 7, and 8 receivers, from 2017 December to 2018 September" (2 Observations and data reduction)
- pi or archival as stated: Cycle 5, PI T. Izumi  
  > "Cycle 5 (project ID: #2017.1.00078.S, PI = T. Izumi)" (2 Observations and data reduction)
- Line: 12CO J=1-0 (115.2712 GHz)
- Line: 13CO J=2-1 (220.3987 GHz)
- Line: 12CO J=2-1 (230.5380 GHz)
- Line: 12CO J=3-2 (345.7960 GHz)
- Line: [C I] 3P1-3P0 (492.1607 GHz)
- Other facility **HST (WFC3/UVIS F547M, ACS/WFC F814W)**: Maps used for stellar mass profile  
  > "we used *HST* WFC3/UVIS F547M map and ACS/WFC F814W map to estimate an $M_\star$ profile" (4.2 Impact on H2 mass measurements)
- External data: Single-dish [CI], CO(2-1), 13CO(2-1) line fluxes of galaxy sample and NGC 7469 SD ratios  
  > "we again compiled line flux data of \[C I\](1–0), CO(2–1), and $^{13}$CO(2–1) from (cite: 2015A&A...578A..95I)." (3.3 The [C I](1-0) diagnostics) [from (cite: 2015A&A...578A..95I)]
- External data: BH mass 1.06e7 Msun  
  > "$M_{\rm BH} = 1.06 \times 10^7~M_\odot$ (cite: 2014ApJ...795..149P)" (4.2 Impact on H2 mass measurements) [from (cite: 2014ApJ...795..149P)]
- External data: Line excitation parameters from LAMDA  
  > "Values are adopted from the LAMDA database (cite: 2005AA...432..369S)." (Table 2) [from (cite: 2005AA...432..369S)]
- Simulation/model as data: One-zone XDR chemical model of Maloney et al. 1996 compared for N_C0/N_CO and T at log xi_eff ~ -2.5  
  > "According to the one-zone dense ($n_{\rm H2} = 10^5$ cm$^{-3}$) XDR chemical model of (cite: 1996ApJ...466..561M)" (4.1.3 What causes the CI-enhancement?)

## Processing

### Calibration

- pipeline or manual: CASA pipeline, standard manner  
  > "The reduction and calibration were done with CASA version 5.4 (cite: 2007ASPC..376..127M) in the standard manner by using the CASA pipeline." (2 Observations and data reduction)
- casa version: CASA 5.4  
  > "CASA version 5.4" (2 Observations and data reduction)
- pipeline version: _not stated_
- archive products used as is: _not stated_
- flux calibrator: _not stated_
- flux scale uncertainty: ~10%  
  > "the absolute flux calibration uncertainty is $\sim 10\%$ according to the Cycle 5 ALMA Proposer’s Guide." (2 Observations and data reduction)
- self calibration: _not stated_

### Imaging

- task: CASA clean, Briggs weighting; concat to combine  
  > "All of the images presented in this paper were reconstructed using the task `clean` with the Briggs weighting." (2 Observations and data reduction)
- deconvolver: _not stated_
- weighting robust: robust = 0.0 for Bands 6,7,8; robust = +0.5 for Band 3  
  > "We applied the `robust` parameter of 0.0 to the Band 6, 7, and 8 datasets" (2 Observations and data reduction); "we instead adopted `robust` = $+$0.5 with further tapering" (2 Observations and data reduction)
- uv taper: outertaper = 0.2 arcsec (Band 3)  
  > "`outertaper` = 0$\ensuremath{''}$.2" (2 Observations and data reduction)
- cell size: 0.06 arcsec  
  > "The pixel scale of ALMA images is set to 0$\ensuremath{''}$.06" (2 Observations and data reduction)
- image size: _not stated_
- masking: _not stated_
- multiscale scales: _not stated_
- continuum subtraction: in uv-plane per visibility set  
  > "The continuum emission was identified and subtracted in the $uv$-plane for each visibility set of different array configuration" (2 Observations and data reduction)
- line free channels: _not stated_
- primary beam correction: applied  
  > "we use line intensities corrected for the primary beam attenuation for quantitative discussion" (2 Observations and data reduction)
- array combination: concat of configurations  
  > "the resultant visibilities were properly combined by the task `concat`" (2 Observations and data reduction)
- smoothing: common 0.38 arcsec resolution for ratios; 10 km/s channels (20 km/s for 13CO)  
  > "after convolving the resolutions to a common 0$\ensuremath{''}$.38" (3.1 Spatial distributions)
- final beam: ~0.34-0.37 arcsec (Table 4)  
  > "0.36 $\times$ 0.29 ($-$72.5$\ensuremath{^\circ}$)" (Table 4)
- final rms: _not stated_

### Inherited from earlier work

- Phase-tracking center from previous ALMA Band 7 observations  
  > "which was based on our previous ALMA observations at Band 7 (cite: 2015ApJ...811...39I)" (2 Observations and data reduction) [from (cite: 2015ApJ...811...39I)]
- Conversion-factor scheme (dynamical mass minus stellar mass minus BH)  
  > "we followed the scheme of (cite: 2004ApJ...602..148D)" (4.2 Impact on H2 mass measurements) [from (cite: 2004ApJ...602..148D)]
- LTE optically thin line ratio formula  
  > "From equations (1) and (2) of (cite: 1995A&A...297..567T)" (4.1.1 LTE perspective) [from (cite: 1995A&A...297..567T)]
- Stellar M/L from V-I color  
  > "an empirical relation between the stellar continuum color and the mass-to-light ratio ($M/L$) developed by (cite: 2001ApJ...550..212B)" (4.2 Impact on H2 mass measurements) [from (cite: 2001ApJ...550..212B)]
- HST stellar mass details deferred  
  > "Details of the *HST* data analysis and $M_\star$ measurements will also be presented in D. Nguyen et al. (in preparation)." (4.2 Impact on H2 mass measurements) [from D. Nguyen et al. (in preparation)]

### Not stated but needed to reproduce (our reading)

- Line-free channels used for continuum subtraction and rms
- clean threshold, masking, niter and image size
- Whether Band 7 compact-configuration data exclusion detail and flagging beyond pipeline
- Exact aperture/spectrum extraction procedure and Gaussian-fit initial guesses
- 3DBarolo settings (mask, normalization, weighting) beyond ring geometry
- MGE fitting details and HST stellar mass profile (deferred to Nguyen et al.)
- RADEX line-width and grid details beyond parameter lists, and how models were compared with observed ratios
- Band 8 phase-offset correction procedure

## Analysis recipe

1. **Calibrate and image cubes**: CASA pipeline calibration, uv-plane continuum subtraction, concat, clean with Briggs weighting  
  > "The continuum emission was identified and subtracted in the $uv$-plane for each visibility set of different array configuration" (2 Observations and data reduction)
   - software: CASA
   - parameter: robust 0.0 (Bands 6-8); robust 0.5 with outertaper 0.2'' (Band 3); dV = 10 km/s (20 for 13CO)  
  > "we created cubes of $^{12}$CO and \[C I\](1–0) lines with a common velocity resolution of $dV = 10$ km s$^{-1}$" (2 Observations and data reduction)
   - fitting: _not stated_
   - validation: Band 8 position offset (~0.08'') corrected using calibrator  
  > "This is due to a phase error in the Band 8 dataset, as confirmed by inspecting the position of a dedicated calibration source (quasar)." (2 Observations and data reduction)
2. **Make moment maps and measure line fluxes/spectra**: Moment-0 over 4650-5200 km/s; spectra at positions A-D with 0.38'' aperture; single/double Gaussian fits; luminosities  
  > "we used a double Gaussian profile for those at the position-A, by taking the observed profiles into account" (3.2 Spectra and Channel maps)
   - software: MIRIAD
   - parameter: Positions A-D defined from Band 7 860 um continuum peaks  
  > "which defines four representative positions (A–D) to measure line fluxes and extract spectra" (3.1 Spatial distributions)
   - assumption: Missing flux ignored  
  > "we do not consider effect of missing flux in this work" (2 Observations and data reduction)
   - fitting: Gaussian fits  
  > "We determine the line peak flux density, centroid velocity, full-width at half-maximum (FWHM), line flux, and line luminosity, by fitting a Gaussian function to the observed spectra." (Spectra and Channel maps)
   - validation: _not stated_
3. **Compute line ratios and compare with single-dish sample**: T_B ratios of [CI]/CO(2-1) and [CI]/13CO(2-1) at A-D; compared with Israel et al. 2015 sample  
  > "We express line ratios in the brightness temperature ($T_{\rm B}$) unit with the Rayleigh-Jeans approximation." (3.3 The [C I](1-0) diagnostics)
   - fitting: _not stated_
   - validation: _not stated_
4. **LTE analysis and rotation diagrams**: Optically thin LTE R_CI/13CO as function of Tex and NC/NCO; CO rotation diagrams for Tex  
  > "we may roughly estimate the $T_{\rm ex}$ at the positions A–D by constructing rotation diagrams" (4.1.1 LTE perspective)
   - assumption: CO/13CO isotopic ratio = 40  
  > "we assume $A^{12}_{13} = 40$ hereafter" (4.1.1 LTE perspective)
   - fitting: Straight-line fit to rotation diagram  
  > "If we fit the data points by straight lines, inferred $T_{\rm ex}$ are 18.5 $\pm$ 3.2 K (A)" (4.1.1 LTE perspective)
   - validation: _not stated_
5. **Non-LTE modeling**: RADEX grid over Tkin, nH2, C0/CO, N_CO/dV compared with observed ratios  
  > "Our non-LTE radiative transfer modelings are performed with the RADEX code (cite: 2007A&A...468..627V) for spherical geometry" (4.1.2 Non-LTE perspective)
   - software: RADEX
   - parameter: Tkin 50,100,200,300,500 K; nH2 1e3,1e4,1e5 cm-3; [C0]/[CO] 1,3,10; N_CO/dV 3e16,1e17,3e17  
  > "The cases of 50, 100, 200, 300, and 500 K are investigated." (4.1.2 Non-LTE perspective)
   - assumption: [CO]/[H2] = 1e-4; Tbg = 2.73 K; [CO]/[13CO] = 40  
  > "we fix this to the cosmic microwave background temperature of 2.73 K in this work for simplicity" (4.1.2 Non-LTE perspective)
   - fitting: Grid comparison, no formal fit  
  > "Comparison of the model results in Figure [9](#fig9) with the observed line ratios in Figure [6](#fig6) therefore gives us an insight on the prevailing physical/chemical conditions of the C I-enhancement." (Non-LTE perspective)
   - validation: _not stated_
6. **Tilted-ring kinematics and dynamical mass**: 3DBarolo tilted-ring fits to [CI](1-0) and CO(2-1) cubes; Mdyn = r Vrot^2/G  
  > "we fitted concentric tilted rings to the data cubes by using the $^{\rm 3D}$Barolo code (cite: 2015MNRAS.451.3021D)" (4.2 Impact on H2 mass measurements)
   - software: 3DBarolo
   - parameter: 50 rings, dr = 0.05'' from r = 0.10''; Vsys fixed 4920 km/s; center fixed to AGN; initial i = 45, PA = 128  
  > "We modeled 50 concentric rings with $\Delta r = 0\ensuremath{''}.05$ starting from $r = 0\ensuremath{''}.10$." (4.2 Impact on H2 mass measurements)
   - fitting: Minimizing residual amplitude |model-observed|; fifth-order polynomial interpolation of Mdyn  
  > "The fitting was evaluated by minimizing the residual amplitude, $|$model–observed data$|$." (4.2 Impact on H2 mass measurements)
   - validation: Residuals <~20 km/s; CI and CO(2-1) Mdyn agree  
  > "Most of the residual components are minor with $\lesssim 20$ km s$^{-1}$ over the modeled region" (4.2 Impact on H2 mass measurements)
7. **Stellar mass and conversion factors**: HST color-based M/L with MGE deprojection; Mmol = Mdyn - Mstar - MBH; alpha = Mmol/L'  
  > "Then we obtained a total molecular mass as $M_{\rm mol} = M_{\rm dyn}-M_\star-M_{\rm BH}$" (4.2 Impact on H2 mass measurements)
   - software: MGE
   - assumption: H2 dominates gas mass in CND; hydrogen nuclei fraction 71%; no dark matter  
  > "we provisionally assume the dominance of H$_2$ (or molecular gas) in the mass budget of the region of our interest." (4.2 Impact on H2 mass measurements)
   - fitting: _not stated_
   - validation: Uncertainty ~0.3 dex dominated by Mstar color variation  
  > "which are then $\sim 0.3$ dex" (4.2 Impact on H2 mass measurements)

## Software

- **CASA** 5.4: Calibration with pipeline, concat, clean imaging  
  > "CASA version 5.4" (2 Observations and data reduction)
- **MIRIAD** : Further analysis incl. moment task  
  > "These data products were further analyzed with the MIRIAD software" (2 Observations and data reduction)
- **RADEX** : Non-LTE radiative transfer modeling  
  > "performed with the RADEX code (cite: 2007A&A...468..627V)" (4.1.2 Non-LTE perspective)
- **3DBarolo** : Tilted-ring fitting of data cubes  
  > "by using the $^{\rm 3D}$Barolo code (cite: 2015MNRAS.451.3021D)" (4.2 Impact on H2 mass measurements)
- **MGE** : Multiple Gaussian expansion of HST stellar light  
  > "with the multiple Gaussian expansion model (cite: 1994A&A...285..723E; 2002MNRAS.333..400C)" (4.2 Impact on H2 mass measurements)

## Numeric results

| quantity | value | uncertainty | units | step | quote |
|---|---|---|---|---|---|
| R_CI/13CO at position A | 19.5 | 3.3 | dimensionless | 3 | /       A       /   0.53 $\pm$ 0.08    /       19.5 $\pm$ 3.3        / |
| R_CI/CO(2-1) at position A | 0.53 | 0.08 | dimensionless | 3 | /       A       /   0.53 $\pm$ 0.08    /       19.5 $\pm$ 3.3        / |
| R_CI/13CO at position A, channel 4900 km/s | 25.1 | 4.4 | dimensionless | 3 | / A (ch)$^\dag$ /   0.78 $\pm$ 0.11    /       25.1 $\pm$ 4.4        / |
| R_CI/13CO in SB ring (B,C,D) | 2.68, 1.81, 2.22 | 0.39, 0.26, 0.32 | dimensionless | 3 | /       B       /   0.21 $\pm$ 0.03    /       2.68 $\pm$ 0.39       / |
| Central concentration of [CI](1-0) flux (r<0.5'' / r<3'') | 20.0 | 0.7 | % | 2 | but 20.0 $\pm$ 0.7% for \[C I\](1–0), respectively |
| CO rotation temperature at A | 18.5 | 3.2 | K | 4 | inferred $T_{\rm ex}$ are 18.5 $\pm$ 3.2 K (A) |
| Dynamical mass within r=0.19'' | 2.3e8 | ~15% | Msun | 6 | we find $M_{\rm dyn} = 2.3 \times 10^8~M_\odot$ after averaging \[C I\](1–0)-based and CO(2–1)-based values, which has $\sim 15\%$ uncertainty. |
| Stellar mass within r=0.19'' | 1.3e8 | ~0.2 dex | Msun | 7 | The enclosed $M_\star$ within the $r = 0\ensuremath{''}.19$ is $1.3 \times 10^8~M_\odot$. |
| Total molecular mass within r<=0.19'' | 9.5e7 | not stated | Msun | 7 | we derive the total gas mass at $r \leq 0\ensuremath{''}.19$ as $M_{\rm mol} = 9.5 \times 10^7~M_\odot$ |
| alpha_CO | 4.1 | ~0.3 dex | Msun (K km/s pc^2)^-1 | 7 | $\alpha_{\rm CO}$ = 4.1 $M_\odot$ (K km s$^{-1}$ pc$^2$)$^{-1}$ and $\alpha_{\rm CI}$ = 4.4 |
| alpha_CI | 4.4 | ~0.3 dex | Msun (K km/s pc^2)^-1 | 7 | $\alpha_{\rm CI}$ = 4.4 $M_\odot$ (K km s$^{-1}$ pc$^2$)$^{-1}$ |
| X_CO and X_CI | 1.9e20 and 2.1e20 | ~0.3 dex | cm^-2 (K km/s)^-1 | 7 | $X_{\rm CO} = 1.9 \times 10^{20}$ cm$^{-2}$ (K km s$^{-1}$)$^{-1}$ and $X_{\rm CI} = 2.1 \times 10^{20}$ |
| [CI](1-0) luminosity at A | 8.2e4 | 0.2e4 | Lsun | 2 | $L_{\rm line}$ of \[C I\](1–0) is $(8.2 \pm 0.2) \times 10^4~L_\odot$ |

## Qualitative findings

- [CI](1-0) peaks on the AGN while CO lines have two knots ~0.2'' north and south of it  
  > "The \[C I\](1–0) distribution clearly peaks at the exact AGN position, whereas CO lines have two bright knots at $\sim 0\ensuremath{''}.2$ north and south to the AGN." (3.1 Spatial distributions)
- AGN ratios are far above starburst values and consistent with XDR models  
  > "The unique abundance ratios and high gas temperature are well in accord with the scenario that the AGN influences the surrounding physical and chemical structures of the ISM in the form of XDR." (5 Summary)

## Claim tuples

- H: High-resolution [CI]/CO ratios isolate the AGN influence from starburst | E: Measured line ratios at four continuum peaks with common 0.38'' aperture | R: R_CI/13CO ~20 at AGN vs ~2 in SB ring | F: C I enhancement is a potential AGN marker | **supported**
- H: The enhancement arises from elevated C0/CO abundance and temperature (XDR) | E: LTE and RADEX modeling of line ratios | R: C0/CO ~3-10 and T ~100-500 K at AGN vs ~1 and <100 K in SB ring | F: Consistent with XDR | **supported**
- H: Conversion factors in the central ~100 pc can be measured dynamically | E: 3DBarolo dynamical mass minus HST stellar mass and BH mass | R: alpha_CO = 4.1, alpha_CI = 4.4 | F: Dedicated conversion factors derived, assuming H2 dominance | **partially**

## Reasoning

- Why this data: _not stated_
- Why this method: Single-dish data cannot isolate XDRs of size <~100 pc, so high-resolution ALMA needed  
  > "This could be due to their insufficient resolution to isolate XDRs" (1 Introduction)
- Alternative: Faint 13CO at CND attributed to low optical depth, not selective photodissociation or nucleosynthesis  
  > "we consider this faintness of $^{13}$CO(2–1) in NGC 7469 is due to a low optical depth of the emission" (3.1 Spatial distributions)
- How they decided it was enough: _not stated_
- Limitation (authors): Dominance of H2 in the CND is assumed; HI/HII may contribute  
  > "One big assumption is about the dominant phase of the circumnuclear gas in terms of mass." (4.2 Impact on H2 mass measurements)
- Limitation (authors): RADEX assumes single homogeneous medium though real structure is complex; single transition limits Tex  
  > "we need to assume that all lines observed are emitted from the same volume, although as we revealed in § 3 the real structures are quite complex" (4.1.2 Non-LTE perspective)
- Caveat (inferred, ours): Only one galaxy; the diagnostic claim is not statistically tested
- Caveat (inferred, ours): Ratios compared with single-dish sample at very different spatial scales
- Caveat (inferred, ours): Non-LTE results degenerate in density, temperature and abundance
- Caveat (inferred, ours): Isotopic ratio fixed at 40 and linearly affects ratios
- Caveat (inferred, ours): Missing flux ignored in ratios
- Caveat (inferred, ours): Conversion factors rely on uncertain stellar mass (0.2 dex) and assumed H2 dominance

## Reproducibility

- Data public (paper): ALMA project 2017.1.00078.S cited; public status not stated explicitly  
  > "This paper makes use of the following ALMA data: ADS/JAO.ALMA#2017.1.00078.S." (Acknowledgments)
- Products in archive: _not stated_
- Missing: Clean parameters and masks
- Missing: Line-free channel ranges
- Missing: HST stellar mass profile (in prep paper)
- Missing: Exact RADEX grid comparison method
- Missing: 3DBarolo configuration details
- Data volume (inferred): Several hundred GB to ~1 TB raw across 5 bands and many execution blocks
- Score (inferred): 3/5, Data identified and many key steps given, but imaging and modeling details and HST stellar mass are incomplete.
- Rediscovery candidate: yes, Data from a single Cycle 5 project, line fluxes and ratios are numeric, and the Gaussian-fit/ratio recipe is largely specified.

## Links

- Method: (cite: 2004ApJ...602..148D) (Dynamical conversion-factor scheme)
- Method: (cite: 2015MNRAS.451.3021D) (3DBarolo)
- Method: (cite: 2007A&A...468..627V) (RADEX)
- Companion: D. Nguyen et al. (in preparation) (HST stellar mass and BH mass modeling)
- Companion: S. Nakano et al. in preparation (Chemical model comparison)
- Companion: (cite: 2015ApJ...811...39I) (Earlier ALMA Band 7 observations of NGC 7469)

## Checks

```json
{
 "quotes": 91,
 "quotes_ok": 91,
 "quote_pass_rate": 1.0,
 "quotes_too_long": 0,
 "unsupported_facts": 0,
 "project_codes": 1,
 "codes_not_in_text": [],
 "codes_not_in_obscore": [],
 "obscore_codes_not_in_card": [],
 "codes_printed_but_missing": [],
 "numeric_results": 13,
 "numeric_problems": 0,
 "fill": {
  "facts": 92,
  "stated": 67,
  "rate": 0.728
 },
 "evidence_ok": true
}
```
