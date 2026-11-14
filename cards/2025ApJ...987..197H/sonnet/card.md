# The ALMA-ATOMS Survey: Exploring Protostellar Outflows in HC<SUB>3</SUB>N

`2025ApJ...987..197H` | The Astrophysical Journal 2025 | first author: Hoque, Ariful | arXiv: 2505.04164 | DOI: 10.3847/1538-4357/add928

Card schema 1.0 | model claude-sonnet-5-5 | depth full | type large_program_or_survey

## Science

- Fields: star_formation, astrochemistry
- Question: Can HC3N (J=11-10) serve as an outflow tracer in massive star-forming clumps, and how do its outflows compare with SiO and depend on clump mass and luminosity?  
  > "whether HC$_3$N can be used as an outflow tracer in all kinds of star-forming clumps, how similar or different are HC$_3$N outflows in comparison to known outflow tracers like SiO" (1 Introduction)
- Target **146 ATOMS massive star-forming clumps (45 HC3N outflows)**: coordinates per-clump RA/Dec listed in Table 4 (e.g. I12320-6122: 12:34:53.38 -61:39:46.9)  
  > "I12320-6122_O1 | I12320-6122 | 12:34:53.38 | -61:39:46.9 | -42.5 | 3.43" (Table 4); z/distance 1.34-12.96 kpc (Table 4)  
  > "I12320-6122_O1 | I12320-6122 | 12:34:53.38 | -61:39:46.9 | -42.5 | 3.43" (Table 4); distance from Liu et al. 2020 (ATOMS survey)  
  > "I12320-6122_O1 | I12320-6122 | 12:34:53.38 | -61:39:46.9 | -42.5 | 3.43" (Table 4)

## Data provenance

- ALMA projects: 2019.1.00685.S, 2017.1.00545.S
- bands: 3 mm  
  > "ALMA three-millimeter observations of massive star-forming regions (ATOMS) survey" (1 Introduction)
- frequencies and spectral setup: 8 SPWs; SPWs 1-6 ~0.2-0.4 km/s resolution, SPWs 7-8 ~1.6 km/s; HC3N from SPW 8, H13CO+ from SPW 2  
  > "The correlator setup includes 8 spectral windows (SPWs), where SPWs 1-6 have a high spectral resolution ($\sim 0.2 - 0.4$ km s$^{-1}$)" (2 Observations and Data)
- continuum bandwidth: _not stated_
- arrays: 12-m array  
  > "we used 12-m array data that have an angular resolution of $\sim$1.2$''$–1.9$''$" (2 Observations and Data)
- configurations: _not stated_
- baselines: _not stated_
- angular resolution: ~1.2''-1.9''  
  > "we used 12-m array data that have an angular resolution of $\sim$1.2$''$–1.9$''$" (2 Observations and Data)
- max recoverable scale: _not stated_
- sensitivity: ~3-10 mJy/beam per 0.122 MHz channel; continuum rms ~0.2 mJy/beam  
  > "sensitivity of $\sim$3–10 mJy beam$^{-1}$ per 0.122 MHz channel" (2 Observations and Data); "The ATOMS 3 mm continuum images have a rms noise of $\sim$0.2 mJy beam$^{-1}$ for most of the sources." (2 Observations and Data)
- time on source: _not stated_
- observing dates: _not stated_
- pi or archival as stated: _not stated_
- Line: HC3N J=11-10 (not stated)
- Line: H13CO+ J=1-0 (not stated)
- Line: SiO J=2-1 (not stated)
- External data: Dust core catalogue and HMC/UCHII associations  
  > "details of the dust cores were adopted from (cite: HLiu2021)" (3.1 Identification of Outflows) [from (cite: HLiu2021)]
- External data: Clump L_bol, M_clump, distance, dust temperature  
  > "The values of $L_{\text{bol}}$ and $M_{\text{clump}}$ are adapted from (cite: liu2020)." (4.1 Outflow parameters with clump properties) [from (cite: liu2020)]
- External data: HC3N spectroscopic constants (Qrot, gu, Aul, El)  
  > "are obtained from the Cologne Database for Molecular Spectroscopy (cite: muller2001)" (3.3 Column Density of HC3N) [from (cite: muller2001)]
- External data: SiO outflow catalogue of the same ATOMS targets (153 outflows)  
  > "Baug et al.(private communication) identified a total of 153 outflows in 146 sources of ATOMS survey." (4.2.2 Comparison with a traditional shock tracer) [from Baug et al. (private communication)]
- External data: HC3N/H2 abundance of 5e-9, mean of literature values  
  > "adopted as $5\times10^{-9}$ i.e., the mean of the values $1.4\times10^{-8}$(cite: mendoza2018), $5.1\times10^{-11}$ (cite: taniguchi2018b), $5\times10^{-10}$ (cite: Yu2019)" (3.4 Estimation of Outflow Parameters) [from (cite: mendoza2018); (cite: taniguchi2018b); (cite: Yu2019)]
- External data: Mean outflow inclination 53.7 deg  
  > "we assumed a mean inclination angle, $\theta$, of 53.7$^{\circ}$ (cite: dunham2014)" (3.4 Estimation of Outflow Parameters) [from (cite: dunham2014)]
- External data: SiO outflow parameters for comparison  
  > "We compared our outflow parameters to the SiO outflows identified by (cite: towner2024) in 15 massive protoclusters." (4.1 Outflow parameters with clump properties) [from (cite: towner2024)]

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

- Observation details and data reduction  
  > "More details of the observations and data reduction can be found elsewhere in (cite: liu2020; HLiu2021; HLiu2022)." (2 Observations and Data) [from (cite: liu2020; HLiu2021; HLiu2022)]
- Column density equation  
  > "We calculated the HC$_3$N column density in each pixel of the data cube using the following equation (cite: Garden1991; Sanhueza2012)." (3.3 Column Density of HC3N) [from (cite: Garden1991; Sanhueza2012)]
- Outflow parameter equations  
  > "Outflow parameters were derived using the following equations given in (cite: lopez2009; Wang2011)." (3.4 Estimation of Outflow Parameters) [from (cite: lopez2009; Wang2011)]
- Position angle sign convention  
  > "similar to the convention used earlier by (cite: baug2020)" (3.6 Outflow Position Angles) [from (cite: baug2020)]

### Not stated but needed to reproduce (our reading)

- Imaging parameters (weighting, robust, cell, image size, deconvolver) for the HC3N and H13CO+ cubes
- Continuum subtraction method and line-free channels
- Exact velocity ranges and Gaussian fit results per source for the cloud component
- Calibration details and flux-scale uncertainty
- The SiO outflow catalogue (private communication) is not available
- How lobe extent and terminal velocity were measured, and per-source distance values used
- Rest frequencies of lines
- Fitting method for the log-log relations

## Analysis recipe

1. **Identify outflow candidates**: Fit Gaussian to H13CO+ spectra to define cloud velocity (VLSR±FWHM); make blue/red wing maps outside it; also make moment 0/1/2 maps with spectral-cube; confirm with PV diagrams along outflow axes (Hubble-law)  
  > "We fit Gaussian profiles to the H$^{13}$CO$^+$ (J=1–0) spectra, and considered $V_{\text{LSR}}\pm$FWHM as the velocity of the central cloud." (3.1 Identification of Outflows)
   - software: spectral-cube, astropy
   - fitting: _not stated_
   - validation: Classified as Confirmed (31) or Probable (14) from wing maps, moment maps and PV diagrams  
  > "A total of 31 outflows are marked as ‘Confirmed’ and 14 outflows are marked as ‘Probable’ outflows." (3.1 Identification of Outflows)
2. **Assign host cores**: Match outflows to ATOMS 3 mm dust cores and HMC/UCHII catalogues  
  > "We identified outflow host cores using the catalogue of 3 mm ALMA dust cores of (cite: HLiu2021)." (3.2 Outflow host cores)
   - fitting: _not stated_
   - validation: _not stated_
3. **HC3N column density per pixel**: LTE, optically thin column density equation  
  > "we assumed the gas is in local thermodynamic equilibrium (LTE) and also considered the HC$_3$N emission to be optically thin." (3.3 Column Density of HC3N)
   - parameter: Tex = 50 K; Qrot=686.7, gu=21, Aul=2.567e-5, El=24.01 K  
  > "The values of $Q_{\text{rot}}$($=kT_{\text{ex}}/hB\,+\,1/3$=686.7), $g_{\text{u}}(=21)$, $A_{\text{ul}}(=2.567\times10^{-5})$, $E_{\text{l}}(=24.01$ K)" (3.3 Column Density of HC3N)
   - assumption: Constant Tex = 50 K for outflowing gas  
  > "We assumed a $T_{\text{ex}}$ of 50 K for the outflow materials" (3.3 Column Density of HC3N)
   - fitting: _not stated_
   - validation: Column density variation with Tex tested; max ~50% uncertainty  
  > "the maximum uncertainty due to the assumption of constant excitation temperature in the outflow parameters estimated with $T_{\text{ex}}$= 50 K would be $\sim50\%$." (3.4 Estimation of Outflow Parameters)
4. **Derive outflow mass, momentum, energy, dynamical time, rates**: Per-lobe 5 sigma masks, exclude cloud velocity channels, sum over channels; correct for inclination  
  > "Emission above a signal-to-noise ratio of 5$\sigma$ is considered to define the outflow mask." (3.4 Estimation of Outflow Parameters)
   - parameter: [HC3N/H2]=5e-9; mu_H=2.8; inclination 53.7 deg  
  > "$\mu_{\text{H}}$ is the mean molecular weight (adopted as 2.8)" (3.4 Estimation of Outflow Parameters)
   - assumption: Constant HC3N abundance relative to H2; optically thin  
  > "(v) the assumption of a constant relative abundance of HC$_3$N with respect to H$_2$." (3.4 Estimation of Outflow Parameters)
   - fitting: _not stated_
   - validation: ~30% uncertainty from 10% distance and flux errors  
  > "the uncertainty in the estimation of outflow parameters would be $\sim$30%." (3.4 Estimation of Outflow Parameters)
5. **Opening angles and position angles**: Visually mark two vectors along 5 sigma lobe edges in ds9 and measure angle; PA by visual axis  
  > "We visually marked two ‘vectors’ to denote the outer edges of 5$\sigma$ emission for each individual outflow lobes" (3.5 Outflow Opening Angle)
   - software: SAOds9
   - fitting: _not stated_
   - validation: Typical uncertainty ~10 deg  
  > "The typical uncertainty in estimated opening angle is $\sim$10$^{\circ}$." (3.5 Outflow Opening Angle)
6. **Correlate outflow parameters with clump properties and compare to SiO**: Spearman correlations, linear fits in log-log, KS tests of HC3N vs SiO PA, extent, terminal velocity and line widths  
  > "We also fit a linear function to find the linear dependency of outflow parameters on clump luminosity and mass in log–log scale." (4.1 Outflow parameters with clump properties)
   - fitting: Linear fit in log-log; sampler/likelihood not stated  
  > "We also fit a linear function to find the linear dependency of outflow parameters on clump luminosity and mass in log–log scale." (Discussion: Outflow parameters with clump properties)
   - validation: _not stated_

## Software

- **CASA** 5.6: Data reduction  
  > "Data reduction was performed using the CASA software package version 5.6 (cite: McMullin2007)." (2 Observations and Data)
- **spectral-cube** : Moment 0, 1, 2 maps  
  > "we also utilized the `spectral-cube` package from the `astropy` project (cite: astropy2013)" (3.1 Identification of Outflows)
- **SAOds9** : Measuring outflow opening angles  
  > "We examined the outflow lobes (i.e the blue-shifted and red-shifted wing emission maps) using SAOds9 software (cite: ds9)" (3.5 Outflow Opening Angle)
- **APLpy** : Plotting (listed in Software)  
  > "astropy (cite: astropy2013), spectral-cube (cite: spectralcube2019), APLpy (cite: aplpy2012), SAOds9 (cite: ds9)" (Software)

## Numeric results

| quantity | value | uncertainty | units | step | quote |
|---|---|---|---|---|---|
| Outflows identified in HC3N | 45 (44 bipolar, 1 explosive; 31 confirmed, 14 probable) | not stated | count | 1 | We identified a total of 45 outflows within the 146 ATOMS targets. Among them, 44 are bipolar in nature, and one is explosive outflows |
| Outflows also detected in SiO | 38 of 45 | not stated | count | 1 | Among the 45 outflows, 38 are also detected in SiO (J=2–1) emission |
| Dust cores hosting outflows | 36 | not stated | count | 2 | A total of 36 dust cores were assigned with outflows as their host cores |
| Spearman correlation of outflow parameters with clump properties | 0.5-0.6 (p<1e-4) | not stated | dimensionless | 6 | We found a moderate correlation (Spearman $\rho$ $\sim$0.5–0.6, p $<10^{-4}$ ) between outflow parameters and clump properties |
| log(Mout) vs log(Lbol) slope | 0.5 | 0.1 | dimensionless | 6 | \log(M_{\text{out}})= (0.5\pm0.1)\, \log(L_{\text{bol}}) -2.4\pm0.4 |
| log(Mout) vs log(Mclump) slope | 0.7 | 0.1 | dimensionless | 6 | \log(M_{\text{out}})= (0.7\pm0.1)\, \log(M_{\text{clump}}) -2.6\pm0.4 |
| Mean outflow mass, blue / red lobes | 0.46 / 0.59 | not stated | Msun | 4 | $M_{\text{out,Blue}}$ $[\text{M}_{\odot}]$ / 8.5$\times10^{-3}$ / 7.5 / 0.46 |
| KS test HC3N vs SiO line widths | statistic 0.31, p=0.087 | not stated | dimensionless | 6 | The estimated KS-test statistics is 0.31, with an associated p-value of 0.087. |
| Outflows with fast jet and slow wide components | 10 of 45 | not stated | count | 0 | Among the 45 sources, such components have been identified in 10 sources. |

## Qualitative findings

- HC3N outflows occur at all clump evolutionary stages (no correlation with Lbol/Mclump), so HC3N is an unbiased tracer  
  > "The non-correlation of HC$_3$N outflows with clump evolutionary stages also implies that HC$_3$N is an unbiased tracer of outflows." (Summary)

## Claim tuples

- H: HC3N traces outflows in massive clumps at any evolutionary stage | E: Compare outflow parameters with Lbol/Mclump | R: Spearman rho<~0.2, p~0.5 | F: HC3N outflows are not tied to a specific stage | **supported**
- H: Outflow parameters scale with clump mass and luminosity | E: Spearman correlation and log-log fits | R: Moderate correlations rho~0.5-0.6 | F: More massive/luminous clumps drive more powerful outflows | **supported**
- H: HC3N detects lower-velocity outflow components than SiO | E: KS tests and cumulative distributions vs SiO | R: Slightly larger fraction at low velocity; KS p=0.225 for velocity | F: HC3N slightly better for low-velocity components | **partially**
- H: HC3N also traces fast collimated flows | E: PV diagrams across lobes | R: Two components in 10 of 45 sources | F: HC3N can detect high-velocity collimated flows | **supported**

## Reasoning

- Why this data: _not stated_
- Why this method: Moment maps used because wing maps miss outflows away from dust cores or blended with cloud  
  > "identification of outflows using this method lacks the ability to detect those outflows away from 3 mm dust continuum cores" (3.1 Identification of Outflows)
- How they decided it was enough: _not stated_
- Limitation (authors): Single Tex, constant abundance, optical thinness, and cloud blending of low-velocity gas cause large uncertainties; core masses not estimated  
  > "the low-velocity outflowing gas always mixes with the cloud component and it is next to impossible to disentangle such emission." (3.4 Estimation of Outflow Parameters)
- Limitation (authors): HC3N detects fewer outflows than SiO (45 vs 153) because of weaker emission and survey sensitivity  
  > "HC$_3$N showed comparatively lower detection of outflows (identifying 45 bipolar outflows among 146 sources) than SiO" (4.2.4 Limitations in detecting HC3N outflows)
- Caveat (inferred, ours): Constant Tex=50 K and abundance 5e-9 (literature values span 3 orders of magnitude) make absolute masses uncertain
- Caveat (inferred, ours): SiO comparison relies on an unavailable private catalogue
- Caveat (inferred, ours): Visual identification of outflows and angles is subjective
- Caveat (inferred, ours): Cloud-velocity masking removes low-velocity gas, undermining the low-velocity advantage claim

## Reproducibility

- Data public (paper): ALMA project codes cited; no explicit public statement  
  > "This paper utilizes the following ALMA data: ADS/JAO.ALMA 2019.1.00685.S and 2017.1.00545.S." (Acknowledgements)
- Products in archive: _not stated_
- Missing: Imaging parameters and calibrated cubes (rely on ATOMS papers)
- Missing: SiO outflow catalogue
- Missing: Per-source velocity masks and lobe lengths
- Missing: Visual selection criteria
- Data volume (inferred): Large: 146 fields, 12-m cubes; likely several hundred GB raw, ~tens of GB calibrated products
- Score (inferred): 3/5, Data and equations are largely given, but identification is visual, imaging is inherited, and the SiO comparison is private.
- Rediscovery candidate: no, Outflow identification is subjective and imaging/reduction settings are deferred to earlier papers; SiO catalogue is private.

## Links

- Method: (cite: liu2020) (ATOMS survey description and data reduction)
- Method: (cite: HLiu2021) (ATOMS dust core, HMC and UCHII catalogues)
- Method: (cite: lopez2009; Wang2011) (outflow parameter equations)
- Companion: (cite: HLiu2022) (further ATOMS observation and reduction details)
- Companion: (cite: towner2024) (SiO outflow parameters used for comparison)
- Related: ATOMS survey

## Checks

```json
{
 "quotes": 64,
 "quotes_ok": 64,
 "quote_pass_rate": 1.0,
 "quotes_too_long": 0,
 "unsupported_facts": 0,
 "project_codes": 2,
 "codes_not_in_text": [],
 "codes_not_in_obscore": [],
 "obscore_codes_not_in_card": [],
 "codes_printed_but_missing": [],
 "numeric_results": 9,
 "numeric_problems": 0,
 "fill": {
  "facts": 83,
  "stated": 44,
  "rate": 0.53
 },
 "evidence_ok": true
}
```
