# Enhanced Gas-phase Metallicities and Suppressed Outflows for Galaxies in a Rich Cluster Core at Cosmic Noon

`2025ApJ...994....4A` | The Astrophysical Journal 2025 | first author: Adachi, Kota | arXiv: 2506.01088 | DOI: 10.3847/1538-4357/ae057f

Card schema 1.0 | model claude-sonnet-5-5 | depth light | type multi_facility_alma_minor

## Science

- Fields: high_z_galaxies, galaxy_clusters_and_sz
- Question: Do metallicities and outflows of galaxies in the X-ray cluster XCS2215 (z=1.46) differ from field galaxies at the same stellar mass?  
  > "to investigate the environmental dependence of gaseous flows and metallicities" (abstract)
- Target **XCS2215 (XMMXCS J2215.9-1738)**: coordinates Member galaxies at RA ~333.96-334.06 deg, Dec ~ -17.60 to -17.68 deg (Table of physical properties)  
  > "we focus on an X-ray cluster XMMXCS J2215.9-1738 at $z=1.46$ as our target." (1 Introduction); "| 2 | $333.9562426$ | $-17.6494988$ | $1.4639$ |" (Physical properties); z/distance z=1.46  
  > "we focus on an X-ray cluster XMMXCS J2215.9-1738 at $z=1.46$ as our target." (1 Introduction); "| 2 | $333.9562426$ | $-17.6494988$ | $1.4639$ |" (Physical properties); distance from Cluster redshift; member redshifts from Halpha in MOSFIRE spectra  
  > "we focus on an X-ray cluster XMMXCS J2215.9-1738 at $z=1.46$ as our target." (1 Introduction); "| 2 | $333.9562426$ | $-17.6494988$ | $1.4639$ |" (Physical properties)

## Data provenance

- ALMA projects: 2011.1.00623.S, 2015.1.00779.S
- bands: ALMA band 3 (CO(2-1)) and band 7 (dust continuum), from previous observations  
  > "CO(J=2-1) emission lines and dust continua were obtained by past ALMA band-3 and band-7 observations" (2.1 Previous observations for XCS2215)
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
- pi or archival as stated: Previously published ALMA data (Hayashi et al. 2017, 2018); gas masses taken from them  
  > "For 18 central member galaxies, CO(J=2-1) emission lines and dust continua were obtained by past ALMA band-3 and band-7 observations (cite: hayashi_evolutionary_2017; hayashi_molecular_2018)." (2.1 Previous observations for XCS2215)
- Line: CO J=2-1 (not stated)
- Other facility **Keck/MOSFIRE**: New J- and H-band NIR spectroscopy of 23 Halpha-detected members (metallicity, SFR)  
  > "we conduct NIR spectroscopic observation using the MOSFIRE spectrograph (cite: McLean2010-se; McLean2012-mj) on the Keck I telescope." (2.2 Keck/MOSFIRE J/H-band spectroscopy)
- Other facility **Subaru, CFHT, HST, UKIRT, Spitzer photometry**: UV-to-mid-IR photometry for SED fitting (stellar mass, E(B-V))  
  > "numerous photometric data in the wavelength range from UV to mid-IR are obtained for these cluster members" (2.1 Previous observations for XCS2215)
- Other facility **VLT/KMOS**: Literature H-band metallicities for six additional members with ALMA gas  
  > "for which the gas-phase metallicities are obtained using VLT/KMOS $H$-band spectroscopy (cite: maier_cluster_2019)" (5.1 Gaseous outflow rate estimated by chemical evolution model)
- External data: CO(2-1)-derived molecular gas masses and f_gas of members from ALMA band 3  
  > "Derived from CO(J=2-1) emission lines measured by ALMA band-3 observation (cite: hayashi_evolutionary_2017)." (Physical properties) [from (cite: hayashi_evolutionary_2017)]
- External data: Photometric catalog (2 arcsec aperture, 0.43 mag aperture correction)  
  > "Photometry of these images was conducted by (cite: hayashi_molecular_2018) with a 2 arcsec diameter aperture" (3.3 SED fitting) [from (cite: hayashi_molecular_2018)]
- External data: Field MZR at 1.4<z<1.7 (FMOS-COSMOS)  
  > "We compare our result with the MZR in the general field at a similar redshift by (cite: kashino_fmos-cosmos_2017)" (4.2 Chemical enrichment) [from (cite: kashino_fmos-cosmos_2017)]
- External data: Field FMR with alpha=0.60 (SDSS+MOSDEF)  
  > "we adopt $\alpha = 0.60$ from (cite: sanders_mosdef_2021)" (4.3 FMR) [from (cite: sanders_mosdef_2021)]
- External data: Higher-z protocluster metallicities (PKS1138, USS1558)  
  > "two higher redshift clusters, PKS1138 ($z\sim2.16$) and USS1558 ($z\sim2.53$) (cite: perez-martinez_signs_2023; perez-martinez_enhanced_2024)" (4.2 Chemical enrichment) [from (cite: perez-martinez_signs_2023; perez-martinez_enhanced_2024)]
- External data: Cluster sigma_v = 1128 km/s and R200 = 1.23 Mpc  
  > "normalized to velocity dispersion $\sigma_v = 1128 \mathrm{\,km/s}$ and virial radius $R_{200} = 1.23 \mathrm{\,Mpc}$ of the cluster (cite: maier_cluster_2019)" (3.4 Phase-space diagram) [from (cite: maier_cluster_2019)]
- External data: Field galaxies at z~1.4 (SFR, metallicity, gas fractions)  
  > "the sample of field galaxies at $z\sim1.4$ from (cite: seko_properties_2016)" (4.1 Star formation activities) [from (cite: seko_properties_2016)]
- Simulation/model as data: Gas regulator chemical evolution model tracks with eta=0.0-3.0 (step 0.5) in the Z vs f_gas plane  
  > "Figure [8](#fig:z_fgas) illustrates the gas regulator model with values of the mass-loading factor $\eta$ ranging from 0.0 to 3.0 with a step of 0.5" (5.1 Gaseous outflow rate estimated by chemical evolution model)

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

- ALMA data reduction, CO fluxes and gas masses taken from earlier papers  
  > "CO(J=2-1) emission lines and dust continua were obtained by past ALMA band-3 and band-7 observations (cite: hayashi_evolutionary_2017; hayashi_molecular_2018)." (2.1 Previous observations for XCS2215) [from (cite: hayashi_evolutionary_2017; hayashi_molecular_2018)]
- Gas regulator model parameters and initial conditions  
  > "We follow (cite: suzuki_dust_2021) for the assumption of parameters and initial conditions of the model." (5.1 Gaseous outflow rate estimated by chemical evolution model) [from (cite: suzuki_dust_2021)]
- Stacking method  
  > "We followed (cite: shimakawa_early_2015) for the stacking method." (3.2 Spectral stacking) [from (cite: shimakawa_early_2015)]
- AGN criteria  
  > "we define the sources satisfying at least one of the following criteria as AGN following (cite: kashino_fmos-cosmos_2017)" (3.1 Emission line fitting) [from (cite: kashino_fmos-cosmos_2017)]

### Not stated but needed to reproduce (our reading)

- ALMA CO(2-1) to H2 conversion factor (alpha_CO), CO excitation ratio r21, and how gas masses were derived (only in Hayashi et al. 2017)
- How f_gas and its errors were computed for the model plots
- Gas regulator model equations/implementation and metallicity for Z_sun (solar 12+log(O/H))
- Exact inclusion of cluster members and the field-FMR comparison procedure for offset errors
- Phase-space boundary values defining the core
- Aperture/slit-loss treatment beyond scaling to WIRCam H-band photometry
- Visual or numeric criteria used to mask OH residuals and the continuum fitting method

## Analysis recipe

1. **Fit emission lines and derive metallicity and SFR**: Monte Carlo (1000 realizations) simultaneous triple-Gaussian fit of Halpha+[N II] and Hbeta+[O III]; N2 calibration for metallicity; Halpha with Calzetti attenuation for SFR  
  > "We perform 1000 realizations of the following fitting procedure on each spectrum" (3.1 Emission line fitting); "12 + \log (\mathrm{O/H}) = 8.90 + 0.57 \times \mathrm{N2}" (3.1 Emission line fitting)
   - software: MOSFIRE DRP
   - parameter: Common FWHM for three lines; wavelength offset limited to +/-5 A; doublet ratios fixed to 3  
  > "allowing $\pm 5 \mathrm{\,\AA}$ variation from the central wavelength in the observed-frame" (3.1 Emission line fitting)
   - assumption: E(B-V)_stellar/E(B-V)_nebular = 0.83; Kennicutt (1998) SFR relation modified for Chabrier IMF  
  > "defined as $E(B-V)_{\mathrm{stellar}} / E(B-V)_{\mathrm{nebular}} = 0.83$ (cite: kashino_fmos-cosmos_2013)" (3.1 Emission line fitting)
   - fitting: Median of Monte Carlo distribution as value; mean of 16th/84th percentile offsets as 1 sigma  
  > "We take the median of the posterior distributions as the estimated line flux and take the average of the 16th and 84th percentiles as the 1 $\sigma$ flux error." (3.1 Emission line fitting)
   - validation: _not stated_
2. **Stack spectra by mass and environment**: Inverse-variance weighted stacking of rest-frame aligned continuum-subtracted spectra with 3 sigma clipping, AGN excluded; bins by mass (split at logM*=10.0) and core/outskirts  
  > "$3\sigma$ clipping for each wavelength is performed when stacking along with weighting by the observed error." (3.2 Spectral stacking)
   - fitting: _not stated_
   - validation: _not stated_
3. **SED fitting for stellar mass and E(B-V)**: CIGALE with BC03, Chabrier IMF, exponentially declining SFH, Calzetti law  
  > "we conduct SED fitting for the photometric catalog constructed by (cite: hayashi_molecular_2018) (see Section [2.1](#sec:data_past)) using Code Investigating GALaxy Emission" (3.3 SED fitting)
   - software: CIGALE
   - parameter: log tau_SF = 8.5-10.0 step 0.1; log age = 8.0-9.7 step 0.1; A_V = 0.0-3.0 step 0.3; stellar metallicity 0.02; extra error 0.1  
  > "Star-forming time scale | $\log (\tau_\mathrm{SF}/\mathrm{[yr]}) = 8.5-10.0$ with steps of 0.1 |" (3.3 SED fitting)
   - fitting: Bayesian CIGALE  
  > "It is the Bayesian approach SED fitting code which takes into account the energy balance" (3.3 SED fitting)
   - validation: Reduced chi2 0.2-4.2, ID 48 (28.6) excluded  
  > "The reduced $\chi^2$ ranges for $0.2 < \chi^2 < 4.2$ in our sample except for ID: 48" (3.3 SED fitting)
4. **Compare metallicity offsets with field MZR and FMR**: Compare N2 metallicities and stacks with Kashino+2017 MZR and Sanders+2021 FMR (alpha=0.60) at matched mass or mu_alpha  
  > "Figure [7](#fig:FMR_mu_060) shows the gas-phase metallicity of the cluster galaxies as a function of $\mu_{\alpha} \equiv \log M_* - \alpha \times \log \mathrm{SFR}$" (4.3 FMR)
   - fitting: _not stated_
   - validation: _not stated_
5. **Estimate mass-loading factor with gas regulator model**: Place galaxies with ALMA f_gas and metallicity on Z vs f_gas diagram against model tracks of eta  
  > "the normalization of gas-phase metallicities for a given gas mass fraction $f_\mathrm{gas} = M_\mathrm{gas} / (M_\mathrm{gas} + M_\mathrm{stellar})$ depends mainly on the mass-loading factor" (5.1 Gaseous outflow rate estimated by chemical evolution model)
   - parameter: R=0.4, y=1.5 Zsun, Z0=0, tau_dep=1/epsilon=0.8 Gyr  
  > "We set star formation efficiency $\epsilon$ and the gas consumption timescale $\tau_{\mathrm{dep}}$ to be $\tau_{\mathrm{dep}}= 1/\epsilon = 0.8 \mathrm{Gyr}$." (5.1 Gaseous outflow rate estimated by chemical evolution model)
   - assumption: Metal-free inflow  
  > "Gaseous inflow into the system is assumed to be metal free ($Z_0=0$)." (5.1 Gaseous outflow rate estimated by chemical evolution model)
   - fitting: _not stated_
   - validation: _not stated_

## Software

- **MOSFIRE Data Reduction Pipeline** : Flat normalization, background subtraction, wavelength calibration, 1D extraction  
  > "The obtained data are reduced using MOSFIRE Data Reduction Pipeline[^1] for flat normalization, background subtraction, wavelength calibration, and 1D spectra extraction." (2.2 Keck/MOSFIRE J/H-band spectroscopy)
- **CIGALE** : SED fitting for stellar mass and dust attenuation  
  > "using Code Investigating GALaxy Emission (CIGALE; (cite: boquien_cigale_2019) (cite: boquien_cigale_2019))" (3.3 SED fitting)
- **astropy** : General analysis  
  > "astropy (cite: astropy:2013; astropy:2018; astropy:2022), Numpy (cite: Harris2020-ra), SciPy (cite: Virtanen2020-zv)" (Software)
- **NumPy/SciPy** : General analysis  
  > "astropy (cite: astropy:2013; astropy:2018; astropy:2022), Numpy (cite: Harris2020-ra), SciPy (cite: Virtanen2020-zv)" (Software)

## Numeric results

| quantity | value | uncertainty | units | step | quote |
|---|---|---|---|---|---|
| Metallicity offset, lower-mass stack (cluster minus field) | 0.14 | 0.06 | dex | 4 | / Lower mass / 11 / $9.1 - 9.8$ / 9.6 / -0.67$\pm$0.07 / 8.52$\pm$0.04 / $0.14 \pm 0.06$ / |
| Metallicity offset, higher-mass stack | 0.08 | 0.05 | dex | 4 | / Higher mass / 7 / $10.0 - 10.6$ / 10.3 / -0.43$\pm$0.04 / 8.65$\pm$0.02 / $0.08 \pm 0.05$ / |
| Metallicity offset, core stack | 0.09 | 0.05 | dex | 4 | / Core / 5 / $9.6 - 10.6$ / 10.1 / -0.46$\pm$0.05 / 8.64$\pm$0.02 / $0.09\pm0.05$ / |
| Metallicity offset, outskirts stack | 0.15 | 0.06 | dex | 4 | / Outskirts / 13 / $9.1 - 10.6$ / 9.7 / -0.62$\pm$0.06 / 8.55$\pm$0.03 / $0.15\pm0.06$ / |
| Offset from field FMR (mean, AGN excluded) | 0.13 | 0.07 | dex | 4 | The difference between the mean value of the cluster galaxies excluding AGN candidates and the field FMR is significant with $\Delta(\mathrm{O/H}) = 0.13 \pm 0.07$. |
| Halpha-detected galaxies (S/N>=2) among 45 H-band targets | 23 | not stated | galaxies | 1 | H$\alpha$ is detected with $\mathrm{S/N} \geq 2$ for 23 objects out of the 45 MOSFIRE *H*-band targets. |
| Mass-loading factor range for five core galaxies | 0.0 < eta < 1.0 | not stated | dimensionless | 5 | the five galaxies located in the central virialized region of the cluster have smaller values, $0.0 < \eta < 1.0$. |

## Qualitative findings

- Cluster galaxies at z=1.46 are more metal-rich than field at fixed mass, and more than higher-z protocluster galaxies  
  > "gaseous metallicities in XCS2215 ($z\sim1.46$) are on average higher than those of the higher redshift clusters ($z\sim2$)" (6 Conclusion)

## Claim tuples

- H: Cluster galaxies at z=1.46 have enhanced gas-phase metallicity compared to field galaxies of the same mass | E: N2 metallicities from MOSFIRE and stacked spectra compared with the FMOS-COSMOS field MZR and the FMR | R: Offsets of 0.08-0.15 dex in stacks (~2 sigma); 0.13+-0.07 dex vs. FMR | F: Metallicity is enhanced, plausibly from inefficient gas accretion in the hot ICM | **partially**
- H: Outflows from core galaxies are weaker than in the field | E: Compare ALMA-based f_gas and metallicity with gas regulator model tracks of mass-loading factor | R: Core galaxies have 0<eta<1, while field and others span 0<eta<2 | F: Outflows are suppressed in the cluster core, likely by ICM confinement | **partially**
- H: Environmental dependence changes with redshift reflecting transition of gas accretion mode | E: Compare XCS2215 offsets to PKS1138 and USS1558 | R: Positive offset at z=1.5, none or negative at z>2 for low mass | F: Transition from cold-stream to hot-mode accretion around cosmic noon | **partially**

## Reasoning

- Why this data: Targets with ALMA band-3/7 data were given highest priority to allow combined metallicity and gas fraction analysis  
  > "giving the highest priorities to the 15 objects which have available ALMA band-3/7 data" (2.2 Keck/MOSFIRE J/H-band spectroscopy)
- Why this method: _not stated_
- How they decided it was enough: _not stated_
- Limitation (authors): Small sample, N2 selection bias toward high metallicity and high gas fraction  
  > "the sample may be biased toward high metallicity and high gas fraction because here we exclude the galaxies for which \[N II\] or CO emission line is not detected." (5.1 Gaseous outflow rate estimated by chemical evolution model)
- Limitation (authors): Metallicity calibration differs from that of the FMR  
  > "A larger sample size with a unified calibration method is needed to provide a more robust indication of the environmental dependence of chemical evolution." (4.3 FMR)
- Caveat (inferred, ours): Only ~2 sigma significance for the offsets
- Caveat (inferred, ours): Outskirts offset larger than core offset conflicts with environment-driven interpretation
- Caveat (inferred, ours): Only five core galaxies in the outflow analysis; eta read off model grid without uncertainties
- Caveat (inferred, ours): Flux calibration via WIRCam photometry instead of standard stars
- Caveat (inferred, ours): Model has fixed tau_dep and yield; eta degenerate with these

## Reproducibility

- Data public (paper): ALMA data cited by project code; Keck data program S20A0075N  
  > "This paper makes use of the following ALMA data: ADS/JAO.ALMA#2011.1.00623.S and ADS/JAO.ALMA#2015.1.00779.S." (Acknowledgments)
- Products in archive: _not stated_
- Missing: Reduced MOSFIRE spectra not released
- Missing: ALMA gas masses only via Hayashi+2017
- Missing: Gas regulator model code not given
- Data volume (inferred): ALMA role is minor; reproducing from tabulated gas masses needs negligible data (<1 GB); reprocessing the ALMA data would be tens of GB
- Score (inferred): 3/5, Analysis of tabulated quantities is largely reproducible with a table in the paper, but MOSFIRE spectra are not provided, ALMA processing is in earlier papers, and the model is described only briefly.
- Rediscovery candidate: no, ALMA data are secondary and the main results depend on Keck/MOSFIRE spectra and external model tracks.

## Links

- Method: (cite: suzuki_dust_2021) (Gas regulator model parameters)
- Method: (cite: shimakawa_early_2015) (Stacking method)
- Method: (cite: pettini_o_2004) (N2 metallicity calibration)
- Companion: (cite: hayashi_evolutionary_2017) (ALMA band-3 CO(2-1) observations and gas masses)
- Companion: (cite: hayashi_molecular_2018) (ALMA data and photometric catalog)
- Companion: (cite: maier_cluster_2019) (KMOS metallicities for XCS2215)
- Related: MAHALO-Subaru
- Related: FMOS-COSMOS
- Related: MOSDEF

## Checks

```json
{
 "quotes": 62,
 "quotes_ok": 62,
 "quote_pass_rate": 1.0,
 "quotes_too_long": 0,
 "unsupported_facts": 0,
 "project_codes": 2,
 "codes_not_in_text": [],
 "codes_not_in_obscore": [
  "2011.1.00623.S"
 ],
 "obscore_codes_not_in_card": [
  "2012.1.00623.S"
 ],
 "codes_printed_but_missing": [],
 "numeric_results": 7,
 "numeric_problems": 0,
 "fill": {
  "facts": 85,
  "stated": 43,
  "rate": 0.506
 },
 "evidence_ok": true
}
```
