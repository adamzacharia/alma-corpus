# MAGAZ3NE: Far-IR and Radio Insights into the Nature and Properties of Ultramassive Galaxies at z ≳ 3

`2026ApJ..1001..131C` | The Astrophysical Journal 2026 | first author: Chang, Wenjun | arXiv: 2508.08460 | DOI: 10.3847/1538-4357/ae4ede

Card schema 1.0 | model claude-sonnet-5-5 | depth light | type archival_reuse

## Science

- Fields: high_z_galaxies, agn_and_quasars
- Question: Do FIR-to-radio data change the inferred nature (quiescent vs dusty star-forming), gas content and AGN activity of two spectroscopically confirmed MAGAZ3NE ultramassive galaxies at z>~3?  
  > "This comprehensive UV-to-radio analysis enables a more complete characterization of their star formation, gas content, and AGN activity, and provides new insights into their evolutionary pathways." (Introduction)
- Target **COS-DR3-195616**: coordinates _not stated_; z/distance z_spec = 3.255  
  > "COS-DR3-195616 ($z_{\rm spec} = 3.255$)" (abstract); distance from Keck/MOSFIRE K-band spectroscopy (MAGAZ3NE)  
  > "COS-DR3-195616 ($z_{\rm spec} = 3.255$)" (abstract)
- Target **COS-DR1-209435**: coordinates _not stated_; z/distance z_spec = 2.481  
  > "COS-DR1-209435 ($z_{\rm spec} = 2.481$)" (abstract); distance from Keck/MOSFIRE K-band spectroscopy (MAGAZ3NE)  
  > "COS-DR1-209435 ($z_{\rm spec} = 2.481$)" (abstract)

## Data provenance

- ALMA projects: 2016.1.00463.S, 2015.1.00137.S
- bands: Band 7 (872 um)  
  > "This search identifies two matches in Band 7 (872 $\mu$m) exceeding the 3$\sigma$ threshold" (3.2 ALMA A$^{3}$COSMOS Catalog and Sample Selection)
- frequencies and spectral setup: _not stated_
- continuum bandwidth: _not stated_
- arrays: _not stated_
- configurations: _not stated_
- baselines: _not stated_
- angular resolution: 0.69'' (195616), 0.78'' (209435)  
  > "angular resolution 0.78$''$" (3.2 ALMA A$^{3}$COSMOS Catalog and Sample Selection)
- max recoverable scale: _not stated_
- sensitivity: RMS 0.13 mJy/beam for 195616  
  > "Its RMS (0.13 mJy/beam) does not reflect an atypical observational depth" (5.3 UMG Nature and Evolutionary Path)
- time on source: _not stated_
- observing dates: _not stated_
- pi or archival as stated: Public archival data via A3COSMOS catalog (PIs Matsuda, Scoville)  
  > "we combine public FIR-to-radio observations in the COSMOS/UltraVISTA field" (1 Introduction)
- Other facility **Keck/MOSFIRE**: K-band spectra, spectroscopic redshifts and emission lines  
  > "Figure [2](#fig: Ks_img_spectra) shows the $K_{s}$-band images and Keck/MOSFIRE 1D and 2D $K$-band spectra for 195616 and 209435." (3.3 Spectroscopic Observations)
- Other facility **Herschel, Spitzer, JCMT, VLA (Jin18 catalog)**: FIR-to-radio photometry (MIPS 24um, PACS, SPIRE, SCUBA2, VLA 3 GHz and 1.4 GHz)  
  > "FIR-to-radio passbands utilized in this work." (Table 1)
- Other facility **Chandra COSMOS-Legacy**: X-ray counterpart for 195616  
  > "identifying only 195616 as an X-ray source within a search radius of $1\ensuremath{''}$" (5.1.2 X-ray and Radio AGNs)
- External data: A3COSMOS prior-extracted ALMA photometric catalog (Dataset 20200310) and molecular gas masses for comparison galaxies  
  > "we cross-match the 15 MAGAZ3NE UMGs with the A$^3$COSMOS (Dataset 20200310[^2]) prior-extracted photometric catalog" (3.2 ALMA A$^{3}$COSMOS Catalog and Sample Selection) [from (cite: Liu2019; Liu2019b)]
- External data: Super-deblended 15-band FIR/radio COSMOS photometry (Jin18)  
  > "(cite: Jin2018) applied the “super-deblending” technique developed by (cite: Liu2018) to create a 15-passband COSMOS catalog" (3.4 FIR/Radio Observations) [from (cite: Jin2018)]
- External data: UV-to-NIR UltraVISTA DR1/DR3 photometry and FAST++ results  
  > "Firstly, we utilize the results from (cite: Forrest2020a; Forrest2024b), which employed FAST$++$" (4.1 SED Fitting) [from (cite: Muzzin2013a; Marsan2022; Forrest2020b; Forrest2024b)]

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

- Spectroscopic redshift and emission-line fitting with slinefit and FAST++  
  > "(see §4 in (cite: Forrest2020b) for details)." (3.3 Spectroscopic Observations) [from (cite: Forrest2020b)]
- Molecular gas mass calibration alpha_nu from dust continuum RJ tail  
  > "we adopt the empirically derived luminosity-to-mass ratio ($\alpha_\nu$) from (cite: Scoville2016)" (4.3.1 Molecular Gas Mass) [from (cite: Scoville2016)]

### Not stated but needed to reproduce (our reading)

- CIGALE parameter values beyond Table 6 (defaults of v2022.1 assumed, but the nebular U grid differs between text and table)
- How ALMA flux density and uncertainties were extracted/used in the SED fit beyond the A3COSMOS catalog
- CIGALE upper-limit treatment and any systematic error floor
- Exact stellar mass and SFR for A3COSMOS comparison galaxies (source and fitting)
- Coordinates of targets

## Analysis recipe

1. **Build UV-to-radio photometric catalogs**: Cross-match 15 MAGAZ3NE UMGs with A3COSMOS within 0.5'' and add Jin18 FIR/radio photometry to UltraVISTA UV-NIR catalogs  
  > "Within a search radius of 0.5$''$, we cross-match the 15 MAGAZ3NE UMGs with the A$^3$COSMOS" (3.2 ALMA A$^{3}$COSMOS Catalog and Sample Selection)
   - parameter: MIPS 24um from Jin18, IRAC from UltraVISTA  
  > "we have determined to utilize the 24 $\mu$m photometry from the Jin18 catalog" (3.4 FIR/Radio Observations)
   - fitting: _not stated_
   - validation: Compared IRAC and MIPS fluxes between catalogs  
  > "we cross-match galaxies from the UltraVISTA and Jin18 catalogs and compare the extracted IRAC and MIPS 24 $\mu$m fluxes for all matched sources." (3.4 FIR/Radio Observations)
2. **SED fitting for stellar mass, SFR, dust, AGN**: CIGALE fits of UV-NIR and UV-radio photometry at z_spec with delayed SFH, BC03, nebular, modified starburst attenuation, DL2014, SKIRTOR, radio module  
  > "We use six modules (sfhdelayed, bc03, nebular, dustatt_modified_starburst, dl2014, skirtor2016)" (4.1.3)
   - software: CIGALE, FAST++
   - parameter: Radio: power-law index alpha = 0.7, q_IR grid 2.4-2.7, R_AGN grid 0.1-100  
  > "SF radio-IR correlation parameter (q$_{\rm IR}$) | 2.4, 2.5, 2.6, 2.7" (Table 6)
   - assumption: Chabrier IMF, Calzetti-modified starburst attenuation  
  > "we apply the modified dust attenuation model from (cite: Calzetti2000)" (4.1.3)
   - fitting: Bayesian estimates over parameter grid (CIGALE)  
  > "The resulting Bayesian-estimated properties are shown in the fourth column of Tables" (4.1.3)
   - validation: Compared with MAGPHYS high-z and Charlot & Fall attenuation; found similar SM/SFR  
  > "We obtained similar estimates for SM and SFR as when we utilized `CIGALE`." (4.2 Stellar Mass and Star Formation Rate)
3. **Molecular gas mass and depletion time**: RF 850um luminosity from CIGALE SED with temperature correction, converted with Scoville16 alpha_nu; compared with Hughes17 and gas-to-dust ratio methods; t_dep = M_mol/SFR  
  > "we estimated the RF 850$\mu$m luminosity ($L_{\nu_{850,\mu{\rm m}}}$) directly from the `CIGALE` fit." (4.3.1 Molecular Gas Mass)
   - software: CIGALE
   - parameter: Temperature correction B_nu(850,25K)/B_nu(850,T_dust): 0.77 (195616), 1.06 (209435)  
  > "This correction factor is 0.77 for 195616 and 1.06 for 209435." (4.3.1 Molecular Gas Mass)
   - assumption: alpha_nu = 6.7 +/- 1.7e19 erg/s/Hz/Msun; 25 K calibration  
  > "6.7 \pm 1.7 \times 10^{19} \, \text{erg} \, \text{s}^{-1} \, \text{Hz}^{-1} \, M_\odot^{-1}" (4.3.1 Molecular Gas Mass)
   - fitting: _not stated_
   - validation: Alternative methods consistent within 0.2 dex  
  > "showing consistency within 0.2 dex." (4.3.1 Molecular Gas Mass)
4. **Predict stellar mass growth and diagnose AGN**: Constant SFR over 0.5 t_dep; AGN from SED fraction, X-ray, radio loudness, emission lines  
  > "we assume a constant SFR over one half of the depletion timescale (0.5$\times t_{\rm dep}$)." (4.4 Predicted Stellar Mass Evolution)
   - software: CIGALE
   - assumption: Photon index 1.4 for X-ray; radio spectral index -0.8  
  > "assuming a photon index of $\Gamma = 1.4$ (cite: Marsan2022)" (5.1.2 X-ray and Radio AGNs)
   - fitting: _not stated_
   - validation: _not stated_

## Software

- **CIGALE** v2022.1: UV-to-radio SED fitting  
  > "we use the default values from `CIGALE v2022.1`." (Table 6 notes)
- **FAST++** : UV-NIR SED fitting at z_phot and z_spec  
  > "We next employ FAST$++$ (cite: Kriek2009; Schreiber2018b_UVJ_FAST)" (4.1.2)
- **slinefit** : Spectroscopic redshift and emission line fluxes  
  > "using the combination of `slinefit`[^3] and FAST$++$" (3.3 Spectroscopic Observations)
- **MAGPHYS** : Sanity-check SED fits  
  > "we also estimated parameters using modified `MAGPHYS` with “high-$z$” expansion" (4.2)

## Numeric results

| quantity | value | uncertainty | units | step | quote |
|---|---|---|---|---|---|
| SFR of 195616 (CIGALE UV-radio) | 62.5 | ±9.6 | Msun/yr | 2 | 62.5 $^{\rm +9.6}_{\rm -9.6}$ |
| SFR of 209435 (CIGALE UV-radio) | 389.1 | ±83.4 | Msun/yr | 2 | intense star formation at a rate of $389.1 \pm 83.4$ $M_{\odot}$yr$^{-1}$ |
| log M_star 195616 / 209435 (CIGALE UV-radio) | 11.36 / 11.38 | +0.04/-0.05 ; +0.10/-0.12 | log Msun | 2 | 11.36$^{\rm +0.04}_{\rm -0.05}$ |
| AGN fraction 195616 / 209435 | 0.60 / 0.31 | ±0.03 / ±0.10 | dimensionless | 2 | frac$_{\rm AGN}$ = 0.60 $\pm$ 0.03 |
| log M_mol 195616 / 209435 | 10.43 / 11.75 | ±0.11 / +0.10/-0.13 | log Msun | 3 | $10.43^{+0.11}_{-0.11}$ |
| Depletion time 195616 / 209435 | 0.43 / 1.44 | ±0.13 / ±0.48 | Gyr | 3 | $0.43 \pm 0.13$ |
| Predicted log M_star,final 209435 | 11.72 (+0.34 dex over 0.72 Gyr) | +0.09/-0.12 | log Msun | 4 | reaching a stellar mass of $\log (M_{\star}/M_{\odot})$ = 11.72 over the course of the next 0.72 Gyr. |
| 195616 rest-frame 2-10 keV luminosity | 2.17e44 | ±0.23e44 | erg/s | 4 | $L_{\rm 2-10 keV, rest} = 2.17 \pm 0.23 \times 10^{44}$ erg s$^{-1}$ |

## Qualitative findings

- 195616 is an unobscured, quenching galaxy with low gas fraction; 209435 is a heavily obscured, actively star-forming, gas-rich UMG; both host AGN  
  > "our analysis reveals that 195616 is an unobscured galaxy undergoing quenching, and 209435 is a heavily obscured, actively star-forming UMG." (abstract)

## Claim tuples

- H: UV-NIR-only classification of the two UMGs as quiescent is correct | E: Add ten FIR-to-radio bands and refit with CIGALE | R: 209435 SFR rises from <=14 to 389 Msun/yr; 195616 SFR 62.5 Msun/yr | F: 209435 is a dusty star-forming UMG, 195616 is quenching | **supported**
- H: The two UMGs differ in gas content | E: RJ-tail dust continuum gas masses compared to A3COSMOS | R: Mmol/Mstar = 0.12 vs 2.33 | F: 195616 is gas-poor, 209435 gas-rich with t_dep 1.44 Gyr | **supported**
- H: Both UMGs host AGN | E: SED AGN fractions, X-ray, radio, emission lines | R: MIR AGN fractions >70%; 195616 X-ray AGN; both radio-quiet | F: AGN in both; feedback may have depleted gas in 195616 | **partially**

## Reasoning

- Why this data: Public FIR-to-radio data needed to distinguish quiescent from dust-obscured star-forming galaxies  
  > "To conclusively distinguish quiescent galaxies from dust-obscured starbursts and to assess the role of AGN, it is essential to incorporate longer wavelength observations." (1 Introduction)
- Why this method: _not stated_
- Alternative: Charlot & Fall attenuation gives 0.5 dex higher stellar mass for 209435; deferred to future work  
  > "the (cite: CharlotFall2000) attenuation model resulted in an estimate of stellar mass 0.5 dex higher" (4.1.4)
- How they decided it was enough: _not stated_
- Limitation (authors): A3COSMOS gas masses do not include AGN contribution; AGN may bias gas mass of 195616  
  > "the (cite: Liu2019b) approach does not include any possible AGN contribution, which may lead to overestimates of both SFR and molecular gas mass." (4.3.1)
- Caveat (inferred, ours): Only two galaxies; conclusions not statistical
- Caveat (inferred, ours): ALMA used only via catalog photometry, no re-imaging
- Caveat (inferred, ours): Large systematic uncertainty in gas masses from 206 um rest-frame extrapolation and AGN contamination
- Caveat (inferred, ours): Results depend on attenuation law choice

## Reproducibility

- Data public (paper): Public A3COSMOS catalog and public FIR/radio catalogs  
  > "we adopt the public A$^{3}$COSMOS catalog" (3.2)
- Products in archive: _not stated_
- Missing: Photometry tables for the two galaxies
- Missing: Full CIGALE configuration beyond Table 6
- Missing: UV-NIR catalogs from MAGAZ3NE (Forrest et al.)
- Data volume (inferred): <1 GB (catalog-level)
- Score (inferred): 3/5, Catalog-level photometry and public codes with a parameter table, but photometric inputs and some settings are not given.
- Rediscovery candidate: no, Analysis is catalog-based SED fitting on two sources with inputs not tabulated.

## Links

- Method: (cite: Boquien2019) (CIGALE SED fitting code)
- Method: (cite: Scoville2016) (Dust continuum gas mass calibration)
- Method: (cite: Liu2019) (A3COSMOS catalog)
- Companion: (cite: Forrest2020b) (MAGAZ3NE phase 1 UV-NIR analysis of 195616)
- Companion: (cite: Forrest2024b) (MAGAZ3NE S-UMG spectroscopy)
- Related: MAGAZ3NE
- Related: A3COSMOS
- Related: UltraVISTA
- Related: COSMOS

## Checks

```json
{
 "quotes": 54,
 "quotes_ok": 54,
 "quote_pass_rate": 1.0,
 "quotes_too_long": 0,
 "unsupported_facts": 0,
 "project_codes": 2,
 "codes_not_in_text": [],
 "codes_not_in_obscore": [],
 "obscore_codes_not_in_card": [],
 "codes_printed_but_missing": [],
 "numeric_results": 8,
 "numeric_problems": 0,
 "fill": {
  "facts": 79,
  "stated": 40,
  "rate": 0.506
 },
 "evidence_ok": true
}
```
