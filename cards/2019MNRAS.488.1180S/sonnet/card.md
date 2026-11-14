# No signs of star formation being regulated in the most luminous quasars at z ∼ 2 with ALMA

`2019MNRAS.488.1180S` | Monthly Notices of the Royal Astronomical Society 2019 | first author: Schulze, Andreas | arXiv: 1906.04290 | DOI: 10.1093/mnras/stz1746

Card schema 1.0 | model claude-sonnet-5-5 | depth full | type observational_alma_primary

## Science

- Fields: agn_and_quasars, high_z_galaxies
- Question: Is star formation in hosts of the most luminous z~2 quasars enhanced or suppressed (regulated), as judged from the intrinsic SFR distribution from ALMA 850um continuum?  
  > "Here, we present ALMA observations to establish the intrinsic SFR-distribution of 20 luminous quasars at $z\sim2$, around the peak of AGN and SF activity." (Introduction)
- Target **20 luminous SDSS DR7 type-1 quasars at 1.9<z<2.1 (e.g. SDSS J1149+0151, SDSS J2313+0034)**: coordinates Table 1 lists J2000 R.A./Decl. for each (e.g. SDSS J1149+0151: 11:49:00.344 +01:51:17.07)  
  > "We focus on a narrow range in redshift $1.9<z<2.1$ to avoid any uncertainties due to redshift evolution within our sample." (2.1 Sample selection); "(4) Redshift taken from (cite: Hewett:2010)" (Table 1); z/distance z = 1.903-2.095; H0=70, Om=0.3, OL=0.7  
  > "We focus on a narrow range in redshift $1.9<z<2.1$ to avoid any uncertainties due to redshift evolution within our sample." (2.1 Sample selection); "(4) Redshift taken from (cite: Hewett:2010)" (Table 1); distance from Redshifts from Hewett & Wild 2010  
  > "We focus on a narrow range in redshift $1.9<z<2.1$ to avoid any uncertainties due to redshift evolution within our sample." (2.1 Sample selection); "(4) Redshift taken from (cite: Hewett:2010)" (Table 1)

## Data provenance

- ALMA projects: 2017.1.00102.S
- bands: Band 7  
  > "in May 2018 in Band 7." (2.2 ALMA Observations)
- frequencies and spectral setup: 350.5 GHz (854um) representative frequency, four base bands each 1875 MHz wide  
  > "The representative frequency was set to 350.5 GHz (854$\mu$m) with four base bands, each with a band width of 1875 MHz." (2.2 ALMA Observations)
- continuum bandwidth: _not stated_
- arrays: 12 m array, 40 antennas  
  > "The observations were carried out using 40 antennas in the 12 m array with baselines 15m – 313m (configuration C43-2)." (2.2 ALMA Observations)
- configurations: C43-2  
  > "baselines 15m – 313m (configuration C43-2)" (2.2 ALMA Observations)
- baselines: 15 m - 313 m  
  > "baselines 15m – 313m (configuration C43-2)" (2.2 ALMA Observations)
- angular resolution: ~0.9 arcsec average major beam (7.5 kpc at z=2)  
  > "The average major beam size achieved is $\sim 0.9$$''$, corresponding to 7.5 kpc at $z=2$" (2.2 ALMA Observations)
- max recoverable scale: ~6.5 arcsec  
  > "The maximum recoverable scale is $\sim6.5\ensuremath{''}$" (2.2 ALMA Observations)
- sensitivity: requested 0.12 mJy/beam (3 sigma); achieved mean ~0.09 mJy/beam; flux error ~0.1 mJy  
  > "Our achieved sensitivities are always below this value, with a mean around $0.09$ mJy beam$^{-1}$." (2.2 ALMA Observations)
- time on source: _not stated_
- observing dates: May 2018  
  > "in May 2018 in Band 7." (2.2 ALMA Observations)
- pi or archival as stated: Cycle 5 program, PI A. Schulze  
  > "(2017.1.00102.S; PI: A. Schulze)" (2.2 ALMA Observations)
- Other facility **SDSS DR7/DR14 (BOSS) spectra**: Optical spectra for Mg II/C IV fits, black hole masses, L3000, L_bol; photometry  
  > "Optical spectra, covering the Mg II and C IV broad line region, are available for all 20 objects from SDSS DR7" (2.4 Optical spectral properties, black hole masses and bolometric luminosities)
- Other facility **2MASS and WISE**: JHK and 3.4-22um photometry for AGN SED fitting  
  > "mid-IR data from the Wide-Field Infrared Survey (cite: Wright:2010) at $3.4, 4.6, 12$ and $22 \mu$m" (3.1 AGN spectral energy distribution)
- Other facility **Herschel**: Archival PACS/SPIRE for 5 objects; only non-constraining upper limits, not used  
  > "None of the targets are detected in either the *PACS* or *SPIRE* bands." (2.3 Herschel data)
- Other facility **Nordic Optical Telescope**: K-band spectrum of SDSS J2313+0034 to check Halpha-based MBH  
  > "We used the Nordic Optical Telescope (NOT) on August 19 2018 under good seeing condition ($\sim0.75\ensuremath{''}$) to obtain a K-band spectrum" (Optical spectral measurements)
- External data: Quasar sample and bolometric luminosities from SDSS DR7 quasar catalog  
  > "We draw our sample from the Sloan Digital Sky Survey (SDSS) DR7 quasar catalog (cite: Schneider:2010; Shen:2011), with $\delta<+15$ deg." (2.1 Sample selection) [from (cite: Schneider:2010; Shen:2011)]
- External data: Median host stellar mass log M*=11.1 (range 10.5-11.5) adopted for the sample  
  > "reporting a median stellar mass of $\log \ensuremath{M_\ast}\,/ M_\odot=11.1$, which we here adopt as the average $M_\ast$ of our sample." (4.1 The intrinsic SFR distribution of luminous quasars) [from (cite: Mechtley:2016)]
- External data: AGN SED templates (standard, WDD, HDD)  
  > "we use a simple approach by fitting with a library of SEDs consisting of the three AGN SED temples provided in (cite: Lyu:2017)" (3.1 AGN spectral energy distribution) [from (cite: Xu:2015; Lyu:2017)]
- External data: MBB parameters beta=1.6, Td=47 K  
  > "We fix the emissivity index to $\beta=1.6$ and the dust temperature to $T_{\rm d}=47$ K (cite: Beelen:2006)" (3.2 FIR luminosities and Star formation rates) [from (cite: Beelen:2006)]
- External data: MS galaxy IR SED template at z~2  
  > "The second approach uses a characteristic IR SED template of MS galaxies at $z\sim 2$ as provided in (cite: Bethermin:2015)." (3.2 FIR luminosities and Star formation rates) [from (cite: Bethermin:2015; Magdis:2012)]
- External data: Hickox et al. model SFR distribution (mean 2.58, dispersion 0.31) and Magneticum simulation SFRs at z=2  
  > "Their SFR distribution has a mean of 2.58 and a dispersion of 0.31." (4.3 Comparison with models) [from (cite: Hickox:2014; Hirschmann:2014)]
- Simulation/model as data: Magneticum Pathfinder (500 Mpc)^3 box, z=2 snapshot, 77 AGN with log Lbol>46.9, eta=0.1  
  > "Figure [8](#fig:SFRdist_comp) shows the distribution of SFR for the 77 AGN in the simulation box with $\log L_{\rm bol}>46.9$." (4.3 Comparison with models)

## Processing

### Calibration

- pipeline or manual: Reproduced observatory calibration with the observatory script, CASA-based  
  > "we processed the ALMA data ourselves by reproducing the observatory calibration with their custom-made script based on Common Astronomy Software Application package (cite: McMullin:2007)." (2.2 ALMA Observations)
- casa version: CASA 5.1.1 (for delivered pipeline images)  
  > "These images are based on the delivered data products using the ALMA pipeline (CASA version 5.1.1), applying a shallow clean." (2.2 ALMA Observations)
- pipeline version: _not stated_
- archive products used as is: _not stated_
- flux calibrator: _not stated_
- flux scale uncertainty: _not stated_
- self calibration: _not stated_

### Imaging

- task: Fluxes measured by uv-plane model fitting in GILDAS; images (shallow clean of pipeline products) only for visualisation  
  > "We measured the 850$\mu$m fluxes and galaxy sizes by fitting the sources with models directly in the uv space." (2.2 ALMA Observations)
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

- uv-plane flux measurement method  
  > "For more details on the method and for discussions on the advantages of the uv space analysis rather than imaging and cleaning the products we refer to (cite: Valentino:2018)" (2.2 ALMA Observations) [from (cite: Valentino:2018); (cite: Rujopakarn:2019)]
- Herschel reprocessing method  
  > "reprocessed them following the method in (cite: Liu:2015), but with the latest calibration in Herschel Interactive Processing Environment (HIPE) version 14" (2.3 Herschel data) [from (cite: Liu:2015)]
- IR luminosity to SFR conversion  
  > "We convert $L_{\rm IR}$  into a SFR using the relation by (cite: Kennicutt:1998), corrected to a (cite: Chabrier:2003) initial mass function" (3.2 FIR luminosities and Star formation rates) [from (cite: Kennicutt:1998; Chabrier:2003)]
- Mg II black hole mass relation  
  > "Specifically, we use the relation from (cite: Shen:2011)" (2.4 Optical spectral properties, black hole masses and bolometric luminosities) [from (cite: Shen:2011)]

### Not stated but needed to reproduce (our reading)

- Number and selection of uv-fit components for the extra sources in the beam
- Phase/flux/bandpass calibrators and flux-scale uncertainty
- Details of the shallow clean (weighting, cell size, masks) for the displayed images
- Exact AGN SED extrapolation to 850um and normalisation procedure for the AGN contribution
- Bayesian log-normal fit priors (Oliphant 2006 approach) details
- Treatment of non-detections in the log-normal fit

## Analysis recipe

1. **Measure 850um fluxes and sizes**: Fit point-source or Gaussian (if resolved >3 sigma) models directly to visibilities  
  > "Gaussian models were used when the emission was found to be resolved at more than 3$\sigma$, while point source models were fit otherwise." (2.2 ALMA Observations)
   - software: CASA, GILDAS
   - fitting: _not stated_
   - validation: _not stated_
2. **Black hole mass and bolometric luminosity from SDSS spectra**: Multi-Gaussian + power-law + Fe template fits to Mg II and C IV; virial MBH from Mg II; Lbol = 3.2 L3000  
  > "we adopt a constant bolometric correction factor $f_{\rm bol}=3.2$ for our sample." (2.4 Optical spectral properties, black hole masses and bolometric luminosities)
   - software: MPFIT
   - fitting: Custom line fitting code based on MPFIT  
  > "We use our custom line fitting code (cite: Schulze:2018b) based on MPFIT (cite: Markwardt:2009)" (Optical spectral measurements)
   - validation: Halpha-based MBH for J2313+0034 agrees with Mg II  
  > "in excellent agreement with the Mg ii result of $\log \ensuremath{M_{\rm{BH}}}=9.73\pm0.04$." (Optical spectral measurements)
3. **Estimate AGN contribution at 850um**: Chi2 fit of three AGN templates (standard, WDD, HDD; only normalisation free) to UV-mid-IR photometry; best template subtracted from ALMA luminosity  
  > "For each template, the absolute normalization is the only free parameter in our $\chi^2$ minimization routine." (3.1 AGN spectral energy distribution)
   - assumption: Host galaxy negligible in UV-mid-IR; ALMA and Herschel excluded from fit  
  > "We do not consider the host galaxy contribution to the UV to mid-IR emission" (3.1 AGN spectral energy distribution)
   - fitting: _not stated_
   - validation: Results independent of template choice (mean difference 0.08 dex)  
  > "we find a mean difference between them of 0.08 dex in $\log L_{850\mu\mathrm{m},{\rm CD}}$ or SFR." (3.2 FIR luminosities and Star formation rates)
4. **Derive LIR and SFR**: Modified blackbody normalised to AGN-subtracted 850um flux; alternative MS-galaxy SED template; Kennicutt conversion  
  > "determine the normalization $N_{\rm mbb}$ from the ALMA continuum flux measurement." (3.2 FIR luminosities and Star formation rates)
   - parameter: beta=1.6, Td=47 K (30-50 K range for uncertainty)  
  > "We use this temperature range to derive lower and upper limits on $L_{\rm IR}$." (3.2 FIR luminosities and Star formation rates)
   - assumption: Chabrier IMF; 8-1000um LIR; SFR = LIR/1e10 Lsun  
  > "SFR$/M_\odot \, {\rm yr}^{-1} = \ensuremath{L_{\rm IR}}/ 10^{10} L_\odot$" (3.2 FIR luminosities and Star formation rates)
   - fitting: _not stated_
   - validation: MBB and template LIR tightly correlated, offset 0.27 dex  
  > "However, the latter are lower by 0.27 dex, consistent with the assumption of a lower dust temperature in the MBB model of $T_{\rm d}\sim40$ K." (3.2 FIR luminosities and Star formation rates)
5. **Fit log-normal SFR distribution and compare with MS and models**: Bayesian log-normal fit; Monte Carlo with Td~N(47,6 K), 1000 realisations; Shapiro-Wilk test; KS test vs Magneticum; MS from Speagle 2014 at assumed M*  
  > "We derive the SFR distribution from 1000 random realizations." (4.1 The intrinsic SFR distribution of luminous quasars)
   - assumption: Host log M* = 11.1 (10.5-11.5) from Mechtley 2016  
  > "For an expected $M_\ast$ range of our sample of $\log \ensuremath{M_\ast}\,=10.5-11.5$ (cite: Mechtley:2016), we find $\log {\rm SFR}=1.78-2.54$." (4.1 The intrinsic SFR distribution of luminous quasars)
   - fitting: Bayesian approach (Oliphant 2006)  
  > "We derive the mean, standard deviation and their confidence intervals for a log-normal SFR distribution using a Bayesian approach (cite: Oliphant:2006)." (4.1 The intrinsic SFR distribution of luminous quasars)
   - validation: Shapiro-Wilk consistent with log-normal  
  > "The observed SFR distribution in all three cases is fully consistent with a log-normal distribution, according to a Shapiro-Wilk test for normality." (4.1 The intrinsic SFR distribution of luminous quasars)

## Software

- **CASA** 5.1.1: Calibration script and pipeline images  
  > "(CASA version 5.1.1), applying a shallow clean." (2.2 ALMA Observations)
- **GILDAS** : uv-plane model fitting of fluxes  
  > "We converted the data into uvfits format to perform further analysis with the IRAM GILDAS tool working on the uv-space (visibility) data." (2.2 ALMA Observations)
- **HIPE** 14: Herschel data reprocessing  
  > "Herschel Interactive Processing Environment (HIPE) version 14" (2.3 Herschel data)
- **MPFIT** : Optical spectral line fitting  
  > "based on MPFIT (cite: Markwardt:2009)" (Optical spectral measurements)

## Numeric results

| quantity | value | uncertainty | units | step | quote |
|---|---|---|---|---|---|
| Detections at 850um | 19/20 (16 at >5 sigma) | not stated | dimensionless | 1 | In total 19 of the 20 targets are detected at $850\mu$m at more than $3\sigma$ at the optical QSO position, 16 of them at more than $5\sigma$. |
| Mean log SFR (MBB, Td=47 K) | 2.15 | 0.11 | log Msun/yr | 5 | MBB ($T_{\rm d}=47$ K)         /   $2.15\pm0.11$    /    $0.49\pm0.08$ |
| SFR dispersion (MBB, Td=47 K) | 0.49 | 0.08 | dex | 5 | MBB ($T_{\rm d}=47$ K)         /   $2.15\pm0.11$    /    $0.49\pm0.08$ |
| Mean log SFR (MS template) | 1.89 | 0.11 | log Msun/yr | 5 | MS galaxy template             /   $1.89\pm0.11$    /    $0.49\pm0.08$ |
| SFR range (MBB) | 35-1513 | not stated | Msun/yr | 4 | The SFRs span a range of $35-1513\, M_\odot$ yr$^{-1}$, with a median value of $180\, M_\odot$ yr$^{-1}$. |
| AGN contribution to L850 | 3-59% (median 14%) | not stated | percent | 3 | we find an AGN contribution to $L_{850\mu\mathrm{m}}$ in the range of $3-59\%$, with a median value of 14%. |
| KS p-values vs Magneticum | 0.14 (single Td), 0.46 (Td distribution) | not stated | dimensionless | 5 | a Kolmogorov-Smirnov test gives p-values of $p_{\rm KS}=0.14$ and $p_{\rm KS}=0.46$ |
| Spearman r, SFR vs log Lbol | -0.48 (p=0.03) | not stated | dimensionless | 5 | $\log\, L_{\rm bol}$                    / $-0.48$ / 0.03  / $-0.35$ /   0.03 |

## Qualitative findings

- SFR distribution of luminous z~2 quasars is consistent with the star-forming main sequence; no systematic enhancement or suppression.  
  > "Thus, there is no evidence for a systematic enhancement or suppression (i.e., regulation or quenching) of star formation in the hosts of the most luminous quasars at $z\sim2$." (abstract)
- Only a weak relation between SFR and accretion rate.  
  > "there is only a weak relation between SFR and accretion rate onto their supermassive black holes both for average and individual measurements." (abstract)

## Claim tuples

- H: Star formation is regulated (quenched or enhanced) in hosts of the most luminous z~2 quasars | E: ALMA Band 7 continuum of 20 quasars, AGN subtraction, MBB SFRs, log-normal fit, comparison with MS | R: Log-normal SFR mean ~140 Msun/yr, dispersion 0.5 dex; consistent with MS | F: No evidence for systematic regulation of SF | **supported**
- H: Models reproduce the SFR distribution of the most luminous quasars | E: Compared with Hickox et al. phenomenological model and Magneticum simulation | R: Observed mean ~0.4 dex lower and broader than Hickox; KS consistent with Magneticum | F: Consistent with Magneticum, not with Hickox model | **supported**
- H: SFR correlates with AGN properties | E: Spearman and Kendall tests vs Lbol, MBH, lambda_Edd, CIV properties | R: No significant correlations | F: Weak/no relation, though limited dynamic range | **partially**

## Reasoning

- Why this data: _not stated_
- Why this method: Band 7 850um minimises AGN contamination and avoids source confusion  
  > "in the sub-mm regime AGN contamination is minimized, and in most cases negligible." (Introduction)
- Alternative: Symeonidis AGN template rejected since measured 850um flux is below its prediction in 18/20 cases  
  > "In 18/20 cases our measured 850$\mu$m flux is below the expectation from the template by (cite: Symeonidis:2016)" (Footnote 3)
- How they decided it was enough: _not stated_
- Limitation (authors): Stellar masses are inferred, not measured; position relative to MS uncertain  
  > "However, direct stellar mass or dynamical mass measurements will be needed to reliably pinpoint our sample with respect to the SF-MS." (4.1 The intrinsic SFR distribution of luminous quasars)
- Caveat (inferred, ours): SFR relies on a single flux point with fixed Td=47 K; 0.27 dex systematic offset between methods
- Caveat (inferred, ours): Stellar masses assumed from other sample
- Caveat (inferred, ours): Small sample, restricted dynamic range in Lbol, MBH
- Caveat (inferred, ours): Dust heating by AGN not excluded

## Reproducibility

- Data public (paper): Project code cited in acknowledgements; public status not explicitly stated  
  > "This paper makes use of the following ALMA data: ADS/JAO.ALMA#2017.1.00102.S." (Acknowledgements)
- Products in archive: _not stated_
- Missing: Calibrator details and exact uv-fit procedure
- Missing: SED fitting normalisation details
- Missing: Hickox and Magneticum model outputs (Magneticum not public in paper)
- Data volume (inferred): ~20-50 GB raw for 20 Band 7 continuum-ish targets
- Score (inferred): 3/5, Simple measurements and tabulated results but uv-fitting and AGN subtraction details sparse.
- Rediscovery candidate: yes, Data are from an ALMA archive project; recipe is simple and results are numeric (fluxes, SFRs, distribution parameters).

## Links

- Method: (cite: Valentino:2018) (uv-plane flux fitting)
- Method: (cite: Lyu:2017) (AGN SED templates)
- Companion: (cite: Hatziminaoglou:2018) (ALMA study of Herschel-selected quasars)
- Related: SDSS DR7 quasar catalog
- Related: FIRST
- Related: H-ATLAS

## Checks

```json
{
 "quotes": 73,
 "quotes_ok": 73,
 "quote_pass_rate": 1.0,
 "quotes_too_long": 0,
 "unsupported_facts": 0,
 "project_codes": 1,
 "codes_not_in_text": [],
 "codes_not_in_obscore": [],
 "obscore_codes_not_in_card": [],
 "codes_printed_but_missing": [],
 "numeric_results": 8,
 "numeric_problems": 0,
 "fill": {
  "facts": 85,
  "stated": 57,
  "rate": 0.671
 },
 "evidence_ok": true
}
```
