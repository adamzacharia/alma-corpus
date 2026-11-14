# The fine line between normal and starburst galaxies

`2017MNRAS.471.2124L` | Monthly Notices of the Royal Astronomical Society 2017 | first author: Lee, Nicholas | arXiv: 1710.02757 | DOI: 10.1093/mnras/stx1753

Card schema 1.0 | model claude-sonnet-5-5 | depth full | type observational_alma_primary

## Science

- Fields: nearby_galaxies, high_z_galaxies
- Question: Is the elevated SFR of galaxies between the main sequence and starbursts driven by higher gas content or by higher star formation efficiency?  
  > "examine whether these galaxies on the upper envelope of the main sequence have elevated SFRs because of increased gas content (like MS galaxies) or enhanced SFE (like starbursts)." (Introduction)
- Target **20 COSMOS LIRGs (ALMA01-ALMA20)**: coordinates Table gives COSOPT IDs, e.g. COSOPT J095936.95+014659.8 (ALMA01)  
  > "20 Luminous Infrared Galaxies (LIRGs) in the COSMOS field at redshifts $z = 0.25$–0.65" (Introduction); "choose from galaxies that have previously known, secure spectroscopic redshifts (cite: 2007ApJS..172...70L)." (2.1 Sample Selection); z/distance z_spec 0.267-0.617  
  > "20 Luminous Infrared Galaxies (LIRGs) in the COSMOS field at redshifts $z = 0.25$–0.65" (Introduction); "choose from galaxies that have previously known, secure spectroscopic redshifts (cite: 2007ApJS..172...70L)." (2.1 Sample Selection); distance from COSMOS spectroscopic redshifts (Lilly et al. 2007)  
  > "20 Luminous Infrared Galaxies (LIRGs) in the COSMOS field at redshifts $z = 0.25$–0.65" (Introduction); "choose from galaxies that have previously known, secure spectroscopic redshifts (cite: 2007ApJS..172...70L)." (2.1 Sample Selection)

## Data provenance

- ALMA projects: _none stated_
- bands: Band 6; CO(3-2)  
  > "The CO $J=3\rightarrow2$ transition falls in ALMA Band 6 for our sample of $z = 0.25$-0.65 LIRGs." (2.2 ALMA Observations)
- frequencies and spectral setup: TDM mode, 2000 MHz bandwidth, 31.25 MHz effective resolution, 34-44 km/s; four spectral windows per Science Goal  
  > "used the TDM correlator mode (2000 MHz bandwidth, 31.25 MHz effective resolution), which gives a velocity resolution of 34-44 km s$^{-1}$." (2.2 ALMA Observations)
- continuum bandwidth: _not stated_
- arrays: _not stated_
- configurations: most compact configuration in Cycle 1, single pointing  
  > "observed in single-pointing mode using the most compact configuration available in Cycle 1" (2.2 ALMA Observations)
- baselines: _not stated_
- angular resolution: ~1.3 arcsec  
  > "low spatial resolution appropriate for detection experiments ($\theta_{\mathrm{FWHM}} \sim 1.3$$''$)" (2.2 ALMA Observations)
- max recoverable scale: _not stated_
- sensitivity: _not stated_
- time on source: 6.6-48.3 min per target (Table)  
  > "CO(3-2)SG5a$^\mathrm{d}$ | A14,A20 | 01-Jan | 2.6, 3.1 | 48.3" (Table 2)
- observing dates: 1 January to 25 February 2014  
  > "These Cycle 1 data were carried out between January 1 to February 25 2014." (2.2 ALMA Observations)
- pi or archival as stated: _not stated_
- Line: CO J=3-2 (345.796 GHz)
- Other facility **Herschel PACS/SPIRE**: far-IR photometry for L_IR, dust SED  
  > "COSMOS has deep far-infrared imaging with *Herschel* PACS and SPIRE from 100–500 $\mu$m" (3.1 COSMOS multiwavelength data)
- Other facility **HST/ACS**: F814W morphologies and half-light radii  
  > "$R_{half}$ is the galaxy’s half light radius as measured in the optical by *HST* ACS" (6.3)
- Other facility **Hectospec on MMT**: emission lines, metallicities, AGN identification  
  > "12 of the 20 LIRGs in our sample were observed in the Hectospec campaign." (3.2 Optical lines)
- Other facility **GALEX**: UV luminosity for SFR  
  > "unobscured UV radiation in COSMOS from GALEX" (6.1)
- External data: R31 = 0.625 ± 0.335 (median of 70 local (U)LIRGs)  
  > "This conversion factor is the median value from a sample of 70 (U)LIRGs in the local universe" (2.4 CO Intensities) [from (cite: 2012MNRAS.426.2601P)]
- External data: Main-sequence definition (Eq. 9) and parameters  
  > "we use the definition of the main sequence provided in Equation 9 of (cite: 2015A&A...575A..74S)" (3.4) [from (cite: 2015A&A...575A..74S)]
- External data: Comparison samples of L_CO and L_IR at z~0.1-0.6  
  > "we compare our results to the subset of galaxies in the literature at a similar redshift range to our sample (cite: 2011A&A...528A.124C; 2013ApJ...768..132B; 2014ApJ...796...63M)" (3.3) [from (cite: 2011A&A...528A.124C; 2013ApJ...768..132B; 2014ApJ...796...63M)]
- External data: Metallicity-dependent alpha_CO prescription  
  > "we adopt the metallicity dependent $\alpha_{\mathrm{CO}}$ conversion factor from (cite: 2015ApJ...800...20G)" (6.2) [from (cite: 2015ApJ...800...20G)]

## Processing

### Calibration

- pipeline or manual: Calibrated by Nordic ARC staff using standard procedures (WVR/Tsys, flagging, bandpass, phase)  
  > "Calibration of these data was carried out by ALMA staff at the Nordic Regional ALMA Centre using standard procedures" (2.3 ALMA Imaging)
- casa version: CASA 4.7  
  > "These data were calibrated and imaged using CASA Version 4.7." (2.3 ALMA Imaging)
- pipeline version: _not stated_
- archive products used as is: _not stated_
- flux calibrator: ALMA quasar monitoring (phase/bandpass calibrators) via getALMAflux and fluxscale, since solar-system objects were inaccurate  
  > "we opted to perform our absolute flux-density calibration using the ALMA quasar monitoring." (2.3 ALMA Imaging)
- flux scale uncertainty: 10% systematic  
  > "include a 10% systematic absolute flux uncertainty" (2.4 CO Intensities)
- self calibration: _not stated_

### Imaging

- task: CLEAN in CASA, Cotton-Schwab, frequency mode  
  > "We imaged the spectral line data using Cotton-Schwab cleaning in frequency mode, using the native spectral resolution of 31.25 MHz." (2.3 ALMA Imaging)
- deconvolver: _not stated_
- weighting robust: natural weighting  
  > "natural weighting in order to maximize the signal-to-noise (S/N)" (2.3 ALMA Imaging)
- uv taper: _not stated_
- cell size: five pixels per beam minor axis (0.13-0.20 arcsec)  
  > "five pixels per beam (minor axis; 0.13-0.20$''$)" (2.3 ALMA Imaging)
- image size: 256x256 or 216x216 pixels  
  > "maps are either 256$\times$256 or 216$\times$216 pixels$^2$" (2.3 ALMA Imaging)
- masking: interactive clean boxes on line emission, clean to 1 sigma, iterate until rms decreases by <=5%  
  > "run CLEAN again in interactive mode, drawing clean boxes to select only the line emission and cleaning down to a threshold of $1\sigma$" (2.3 ALMA Imaging)
- multiscale scales: _not stated_
- continuum subtraction: continuum made with MFS using all four spws excluding CO channels; continuum subtraction applied in line flux measurement  
  > "multi-frequency synthesis mode in CLEAN and all four spectral windows, excluding channels containing the CO $J=3\rightarrow2$ line" (2.3 ALMA Imaging)
- line free channels: _not stated_
- primary beam correction: _not stated_
- array combination: _not stated_
- smoothing: _not stated_
- final beam: _not stated_
- final rms: _not stated_

### Inherited from earlier work

- Cosmology and Chabrier IMF adopted  
  > "we use a cosmology with $\Omega_{m} = 0.28$, $\Lambda = 0.72$, and $H_{0} = 70$ km s$^{-1}$ Mpc$^{-1}$ (cite: 2013ApJS..208...19H)." (Introduction) [from (cite: 2013ApJS..208...19H)]
- Optical emission line fluxes measured as in earlier work  
  > "Emission line fluxes are measured as described in (cite: 2011ApJ...730..137Z)." (3.2 Optical lines) [from (cite: 2011ApJ...730..137Z)]
- CO luminosity from Eq. 3 of Solomon & Vanden Bout  
  > "using Equation 3 from (cite: 2005ARA&A..43..677S)" (2.4 CO Intensities) [from (cite: 2005ARA&A..43..677S)]

### Not stated but needed to reproduce (our reading)

- Line-free channels and channel ranges used per galaxy for the continuum
- Exact clean thresholds/rms values and the final beams per target beyond the table
- Details of the Herschel SPIRE Stan-based extraction and DL07 SED fit settings
- Priors/settings of the Kelly linear-regression fits
- Mass-metallicity relation and chi(Z) details to reproduce alpha_CO
- ALMA science-goal to MOUS mapping needed to retrieve the data
- Half-light radii values used for surface densities

## Analysis recipe

1. **Image CO(3-2) cubes and continuum**: CASA CLEAN with natural weighting and iterative interactive masking  
  > "We imaged each science target using the CLEAN task in CASA." (2.3 ALMA Imaging)
   - software: CASA
   - fitting: _not stated_
   - validation: _not stated_
2. **Measure integrated CO line flux and luminosity**: Integrate spectral profiles in a bounding box over line channels, continuum subtraction, then L'CO via Solomon & Vanden Bout; convert to CO(1-0) with R31  
  > "We measure this by integrating the spectral line profiles over the channels containing the line emission, which we identify by eye from the 3D spectral cubes" (2.4 CO Intensities)
   - parameter: bounding box: >=5 sigma pixels in moment 0 extended by 2.5 sigma_maj  
  > "extending the box boundaries to include all pixels within $2.5\sigma_{\mathrm{maj}}$ of the bright pixels" (2.4 CO Intensities)
   - assumption: R31 = 0.625 ± 0.335  
  > "we adopt a conversion factor of $R_{31} = 0.625 \pm 0.335$" (2.4 CO Intensities)
   - fitting: _not stated_
   - validation: Uncertainty from rms in line-free channels plus 10% flux systematic, because channels are correlated (0.65-0.75)  
  > "we compute the rms from the flux density profiles in the channels free of line emission and include a 10% systematic absolute flux uncertainty" (2.4 CO Intensities)
3. **Derive L_IR, dust properties, SFR and distance to main sequence**: Fit IR photometry to Draine & Li dust models; SFR_total = 8.6e-11 (L_IR + 2.3 nuL_nu(2300A)); Delta SFR_MS relative to Schreiber+15 MS  
  > "$SFR_{\rm{Total}} = (8.6 \times 10^{-11}) \times (L_{\rm{IR}}+ 2.3 \times \nu L_{\nu}(2300 \rm{\AA}))$" (6.1 Star Formation Rates)
   - assumption: Chabrier IMF; Salpeter-to-Chabrier conversions of 0.24 dex in mass and 1.7 in SFR  
  > "$\mathrm{log}(M_{*, \mathrm{Chab}}) = \mathrm{log}(M_{*, \mathrm{Sal}}) - 0.24$" (3.4)
   - fitting: _not stated_
   - validation: Greybody plus power-law fits give no significant differences; single power-law MS gives no significant change  
  > "do not find significant differences in our results" (3.1)
4. **Derive molecular gas masses**: M_mol = alpha_CO(Z) x L'CO(1-0) with metallicity-dependent alpha_CO from Genzel+15  
  > "set $\alpha_{\mathrm{CO, MW}} = 4.36~M_{\odot}/($K km s$^{-1}$ pc$^{2}$)" (6.2 Gas Masses from CO)
   - assumption: metallicity from Hectospec lines (KK04 scale converted to PP04) or mass-metallicity relation  
  > "Sources without direct metallicity measurements have their metallicity estimated using the mass-metallicity relationship" (6.2 Gas Masses from CO)
   - fitting: _not stated_
   - validation: MW alpha_CO, Z-dependent alpha_CO and dust-continuum gas masses agree within <~0.05 dex  
  > "all result in a consistent measurement of the gas mass, with typical differences of $\lesssim 0.05$ dex" (10.4 Comparison of Gas Masses)
5. **Test correlations and fit scaling relations**: Spearman rank with permutation test (10^6 permutations); Bayesian linear regression (Kelly 2007) with errors in both variables  
  > "we use a Bayesian method of linear regression described in (cite: 2007ApJ...665.1489K)" (3.5)
   - software: SciPy, Kelly (2007) Gibbs sampler
   - parameter: N_perm = 10^6  
  > "In this paper, we sample $N_{perm} = 10^{6}$ permutations." (3.5)
   - fitting: MCMC Gibbs sampler with intrinsic scatter; priors not stated  
  > "uses a Markov Chain Monte Carlo (MCMC) algorithm (specifically a Gibbs sampler)" (3.5)
   - validation: Removing ALMA19 or ALMA20 does not change results  
  > "Removing this galaxy from our samples does not change the correlations found (or not found)" (7 Discussion)

## Software

- **CASA** 4.7: calibration and imaging (CLEAN, fluxscale)  
  > "These data were calibrated and imaged using CASA Version 4.7." (2.3 ALMA Imaging)
- **analysis utils (getALMAflux)** : quasar flux density from ALMA monitoring  
  > "we can use the special “getALMAflux” function from the ARC analysis utils" (2.3 ALMA Imaging)
- **SciPy** : Spearman rank correlation  
  > "as implemented in the SciPy package" (3.5)
- **Stan** : prior-based SPIRE source extraction  
  > "new prior-based source extraction tool based on the Bayesian inference tool Stan" (3.1)

## Numeric results

| quantity | value | uncertainty | units | step | quote |
|---|---|---|---|---|---|
| Spearman correlation Sigma_SFR vs Sigma_gas | rho = 0.83, p = 8e-6 | not stated | dimensionless | 5 | Spearman Rank correlation coefficient of $\rho = 0.83$ and $p = 8 \times 10^{-6}$ |
| KS law exponent beta | 1.07 | 0.25 | dimensionless | 5 | best-fit exponent is $\beta = 1.07 \pm 0.25$ |
| SFE vs Delta SFR_MS Spearman | rho = 0.133, p = 0.2987 | not stated | dimensionless | 5 | correlation coefficient of $\rho = 0.133$ with a $p$-value of 0.2987 |
| gas fraction vs Delta SFR_MS Spearman | rho = 0.546, p = 0.0104 | not stated | dimensionless | 5 | $\rho = 0.546$ and a $p$-value of 0.0104 |
| Gas fraction scaling exponent M_gas/M* ∝ (SFR/SFR_MS)^beta | 0.58 | 0.23 | dimensionless | 5 | find a best-fit exponent of $\beta = 0.58 \pm 0.23$ |
| Number of galaxies with continuum detected >3 sigma at 1 mm | 7 of 20 | not stated | galaxies | 1 | Only 7/20 of our targets are detected above $3\sigma$ at 1 mm. |

## Qualitative findings

- All 20 LIRGs detected in CO(3-2); mostly disk-like morphologies, ~10% interacting  
  > "The majority of the sample has disk-like morphologies, with only $\sim 10$% showing signs of interaction." (Summary)

## Claim tuples

- H: Elevated SFR above the MS is due to higher SFE | E: Spearman test of SFE vs Delta SFR_MS for 20 LIRGs | R: rho = 0.133, p = 0.2987 | F: No evidence that SFE changes with distance to the MS | **supported**
- H: Elevated SFR is due to higher gas content | E: Spearman test and fit of gas fraction vs Delta SFR_MS | R: rho = 0.546, p = 0.0104; slope 0.58 ± 0.23 | F: Gas fraction drives Delta SFR_MS for Delta SFR_MS <~ 0.6 | **supported**
- H: Two separate KS relations for normal and starburst | E: Fit Sigma_SFR-Sigma_gas with metallicity-dependent alpha_CO | R: beta = 1.07 ± 0.25, no two sequences | F: No evidence for two relations within this sample | **partially**

## Reasoning

- Why this data: _not stated_
- Why this method: Metallicity-dependent alpha_CO adopted to avoid artificial dichotomy of a bimodal alpha_CO  
  > "We avoid introducing artificial dichotomy in the data from a bimodal $\alpha_{\mathrm{CO}}$ conversion factor" (Introduction)
- Alternative: Bimodal alpha_CO rejected as inappropriate for the sample with Delta SFR_MS <~ 0.6-0.8  
  > "These all suggest that a bimodal $\alpha_{\mathrm{CO}}$ is inappropriate" (10.4 Comparison of Gas Masses)
- How they decided it was enough: _not stated_
- Limitation (authors): Few sources at Delta SFR_MS > 0.6, so no strong conclusions there; sample insensitive to extreme starbursts  
  > "we are limited in sample size and are unable to draw strong conclusions for galaxies in the range $0.6 \lesssim \Delta SFR_{MS} \lesssim 0.8$." (7 Discussion)
- Limitation (authors): ALMA data not spatially resolved; HST optical sizes used for surface densities  
  > "our ALMA data are not spatially resolved, and the HST-based measurements provide the best size estimates for our sample." (6.3)
- Caveat (inferred, ours): Assumed R31 with large scatter propagates strongly into gas masses
- Caveat (inferred, ours): Only 20 sources and a narrow dynamic range in Delta SFR_MS
- Caveat (inferred, ours): Hectospec metallicities only for part of sample; alpha_CO from mass-metallicity relation otherwise
- Caveat (inferred, ours): Flux calibration relied on quasar monitoring after problematic solar-system calibrators

## Reproducibility

- Data public (paper): ALMA Cycle 1 project 2012.1.00076 cited; no explicit statement on public access  
  > "This paper makes use of the following ALMA data: ADS/JAO.ALMA#2012.1.00076." (Acknowledgements)
- Products in archive: _not stated_
- Missing: Re-reduced Nordic ARC calibration scripts
- Missing: Per-source channel ranges and bounding boxes
- Missing: Cortzen thesis compilation of literature L_CO/L_IR
- Missing: SPLASH and Hectospec data products
- Data volume (inferred): ~20-50 GB raw (7 science goals, short compact-array Band 6 observations)
- Score (inferred): 6/5, Clear tabulated measurements and simple method, but non-standard flux calibration and several inherited/uncited choices.
- Rediscovery candidate: yes, Archival Cycle 1 data, simple line-flux extraction and numeric tables allow checking L'CO and correlations.

## Links

- Method: (cite: 2015A&A...575A..74S) (Main sequence definition)
- Method: (cite: 2015ApJ...800...20G) (Metallicity-dependent alpha_CO)
- Method: (cite: 2007ApJ...665.1489K) (Bayesian linear regression)
- Companion: (cite: Cortzen_Thesis) (Compilation of literature L_CO and L_IR)
- Related: COSMOS
- Related: HerCULES
- Related: SPLASH

## Checks

```json
{
 "quotes": 70,
 "quotes_ok": 70,
 "quote_pass_rate": 1.0,
 "quotes_too_long": 0,
 "unsupported_facts": 0,
 "project_codes": 0,
 "codes_not_in_text": [],
 "codes_not_in_obscore": [],
 "obscore_codes_not_in_card": [
  "2012.1.00076.S"
 ],
 "codes_printed_but_missing": [],
 "numeric_results": 6,
 "numeric_problems": 0,
 "fill": {
  "facts": 82,
  "stated": 56,
  "rate": 0.683
 },
 "evidence_ok": true
}
```
