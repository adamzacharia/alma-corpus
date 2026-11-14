# The effect of active galactic nuclei on the cold interstellar medium in distant star-forming galaxies

`2021A&A...654A.165V` | Astronomy and Astrophysics 2021 | first author: Valentino, F. | arXiv: 2109.03842 | DOI: 10.1051/0004-6361/202141417

Card schema 1.0 | model claude-sonnet-5-5 | depth light | type archival_reuse

## Science

- Fields: high_z_galaxies, agn_and_quasars
- Question: What is the effect of mid-IR- and X-ray-detected AGN on the molecular gas reservoirs, excitation (CO, [CI] SLEDs) and dust of IR-selected main-sequence and starburst galaxies at z~1-1.7?  
  > "Our goal is to gauge the effect of accreting SMBHs on the global SFR, the mass, and the excitation conditions of the cold gas and dust in a large sample of homogeneously IR-selected galaxies." (1 Introduction)
- Target **55 IR-selected galaxies in COSMOS at z~1.2**: coordinates _not stated_; z/distance median z~1.2  
  > "Here we focus on the sample of 55 galaxies with a robust spectroscopic redshift from submillimeter lines (at least one line with $Flag=1$ in V20a)" (2.1 ALMA observations and far-IR modeling); distance from ALMA submillimeter spectroscopic redshifts (V20a)  
  > "Here we focus on the sample of 55 galaxies with a robust spectroscopic redshift from submillimeter lines (at least one line with $Flag=1$ in V20a)" (2.1 ALMA observations and far-IR modeling)

## Data provenance

- ALMA projects: 2015.1.00260.S, 2016.1.00171.S, 2018.1.00635.S, 2016.1.01040.S, 2019.1.01702.S
- bands: _not stated_
- frequencies and spectral setup: _not stated_
- continuum bandwidth: _not stated_
- arrays: _not stated_
- configurations: _not stated_
- baselines: _not stated_
- angular resolution: 0.8-1.4"  
  > "the ALMA observations were carried out at a spatial resolution of $0.8-1.4\ensuremath{''}$ (Table 1 in V20a)" (2.1 ALMA observations and far-IR modeling)
- max recoverable scale: _not stated_
- sensitivity: _not stated_
- time on source: _not stated_
- observing dates: _not stated_
- pi or archival as stated: _not stated_
- Line: CO J=2-1, 4-3, 5-4, 7-6 (not stated)
- Line: [CI] 3P1-3P0, 3P2-3P1 (not stated)
- Other facility **Chandra**: 2-10 keV X-ray luminosities for AGN detection (threshold 1e43 erg/s)  
  > "fixed a minimum threshold of $L_{\rm 2-10\, keV}=10^{43}$ erg s$^{-1}$ for a significant AGN detection, which we found in 18/55 sources" (2.2 Ancillary data)
- Other facility **Herschel/PACS and Spitzer/MIPS**: far-IR/mid-IR photometry for SED modeling  
  > "We imposed a detection in *Herschel*/PACS 100 or 160 $\mu$m from the PACS Evolutionary Probe survey" (2.1 ALMA observations and far-IR modeling)
- External data: De-blended far-IR photometric catalog  
  > "The modeling of the SED was performed on the de-blended far-IR catalog by (cite: jin_2018)" (2.1 ALMA observations and far-IR modeling) [from (cite: jin_2018)]
- External data: Chandra X-ray luminosities (column #50)  
  > "2-10 keV rest frame logarithmic luminosity (column #50 in (cite: marchesi_2016); negative values: upper limits)" (Data table) [from (cite: marchesi_2016)]
- External data: ASPECS and Liu+21 CO compilations used for comparison and fit  
  > "we also added the literature compilation from (cite: liu_2021) who applied an SED modeling similar to and consistent with ours" (3.2 The effect on CO line luminosities) [from (cite: boogaard_2020; liu_2021)]

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

- Observation details, line fluxes, continuum and sizes taken from the survey master catalog  
  > "we refer the reader interested in the details of the observations to V20a for a complete description." (1 Introduction) [from V20a (cite: valentino_2020c)]
- Remodeling of UV-near-IR photometry for AGN hosts  
  > "we remodeled the UV to near-IR photometry from (cite: laigle_2016) as in (cite: circosta_2018)" (2.2 Ancillary data) [from (cite: circosta_2018)]

### Not stated but needed to reproduce (our reading)

- ALMA calibration and imaging details (all deferred to V20a)
- Line flux extraction method
- Exact Kaplan-Meier and Kendall tau implementations
- Modified MLINMIX_ERR code details and priors

## Analysis recipe

1. **SED fit for L_IR, f_AGN, Mdust, U**: chi2 minimization with Draine & Li templates plus Mullaney AGN templates on far-IR catalog plus ALMA continuum  
  > "We used the customized $\chi^2$ minimization tool STARDUST (cite: kokorev_2021)" (2.1 ALMA observations and far-IR modeling)
   - software: STARDUST
   - parameter: 4/55 extreme-f_AGN cases refit with U fixed to redshift average, 30% variation  
  > "we thus fixed $\langle U \rangle$ to the average value for galaxies at the same redshift and we allowed for a 30% variation" (2.1 ALMA observations and far-IR modeling)
   - fitting: uncertainties from 10,000 randomized realizations  
  > "computed as the 16th-84th percentile confidence intervals over 10,000 randomized realizations of the fitting process" (2.1 ALMA observations and far-IR modeling)
   - validation: consistent with MICHI2 reanalysis of part of sample  
  > "the $f_{\rm AGN}$ from our decomposition are consistent with the reanalysis of the full UV-to-radio SED modeling of part of our sample with MICHI2" (2.1 ALMA observations and far-IR modeling)
2. **Mean CO/[CI] SLEDs**: Kaplan-Meier mean including robust upper limits, split by f_AGN=20% and X-ray detection  
  > "We computed the mean SLEDs using the Kaplan-Meier estimator (cite: kaplan-meier_1958) and we included robust upper limits ($Flag=0.5$ in V20a)." (3.4 Average CO spectral line energy distributions)
   - fitting: _not stated_
   - validation: _not stated_
3. **Dust optical depth wavelength lambda0**: tau = kappa850 (nu/nu850)^beta Mdust/(2 pi R^2) with ALMA sizes; kendall tau and KS tests  
  > "We used $\kappa_{\rm 850\,\mu m}=0.43\,\mathrm{cm^{-2}g^{-1}}$ and $\beta=2$ (cite: li_2001)" (3.6 A point about dust masses, opacities, and sizes)
   - fitting: _not stated_
   - validation: _not stated_
4. **Fit L'CO(5-4) as linear combination of L_IR,SFR and L_IR,AGN**: Bayesian multiple linear regression with upper limits, zero intercept  
  > "adopting the Bayesian multiple linear regression code MLINMIX_ERR.PRO by (cite: kelly_2007), which we modified in a minor way to impose a zero constant $\alpha$ intercept" (4.2 Nuclear activity as a factor contributing)
   - software: MLINMIX_ERR.PRO
   - fitting: parameters are posterior median and 16-84% range  
  > "where the parameters are the median and the range enclosing the 16-84% of the posterior probability distribution." (4.2 Nuclear activity as a factor contributing)
   - validation: free intercept gives alpha=0.04±0.02, consistent with zero  
  > "obtaining $\alpha=0.04\pm0.02$, which does not significantly deviate from our physically motivated choice of $\alpha=0$" (4.2 Nuclear activity as a factor contributing)

## Software

- **STARDUST** : SED fitting  
  > "We used the customized $\chi^2$ minimization tool STARDUST (cite: kokorev_2021)" (2.1 ALMA observations and far-IR modeling)
- **MLINMIX_ERR.PRO** : Bayesian linear regression with upper limits  
  > "Bayesian multiple linear regression code MLINMIX_ERR.PRO by (cite: kelly_2007)" (4.2 Nuclear activity as a factor contributing)
- **CIGALE** : stellar mass refit including AGN templates  
  > "a refit with CIGALE that includes AGN templates as in (cite: circosta_2018)" (B.2 Stellar masses)

## Numeric results

| quantity | value | uncertainty | units | step | quote |
|---|---|---|---|---|---|
| X-ray detected AGN fraction (L2-10keV>1e43) | 18/55 | not stated | dimensionless | 0 | which we found in 18/55 sources |
| CO(5-4) fit coefficient for L_IR,SFR | 0.28 | ±0.01 | 1e10 K km/s pc2 per 1e12 Lsun | 4 | (0.28\pm0.01) \times \frac{L_{\rm IR,\,SFR}}{10^{12}L_\odot} + (0.05\pm0.03) |
| CO(5-4) fit coefficient for L_IR,AGN | 0.05 | ±0.03 | 1e10 K km/s pc2 per 1e12 Lsun | 4 | (0.28\pm0.01) \times \frac{L_{\rm IR,\,SFR}}{10^{12}L_\odot} + (0.05\pm0.03) |
| Mean lambda0, X-ray detected | 51 | ±8 | micron | 3 | $\langle \lambda_0 \rangle_{\rm X-ray} = 51\pm 8$ $\mu$m and $\langle \lambda_0 \rangle_{\rm SFG} = 27\pm 3$ $\mu$m |
| Intrinsic scatter of CO(5-4) fit | 0.16 | not stated | dex | 4 | We also estimate an intrinsic scatter of 0.16 dex. |

## Qualitative findings

- AGN have only marginal effects on CO, [CI] luminosities, excitation, gas and dust fractions  
  > "we find only marginal effects of the presence and strength of AGN on the carbon monoxide CO ($J=2,4,5,7$) or neutral carbon" (abstract)

## Claim tuples

- H: AGN alter gas excitation and reservoirs in IR-selected z~1.2 galaxies | E: Compare CO/[CI] luminosities, ratios and mean SLEDs of AGN hosts vs star-forming galaxies | R: No significant differences except higher CO(7-6) tied to starbursts | F: AGN have minimal effects on gas | **supported**
- H: AGN contribute to CO(5-4) beyond star formation | E: Linear fit of L'CO(5-4) with L_IR,SFR and L_IR,AGN | R: AGN term 0.05±0.03; scatter reduced by 17% | F: AGN may explain a few outliers | **partially**

## Reasoning

- Why this data: _not stated_
- Why this method: _not stated_
- How they decided it was enough: _not stated_
- Limitation (authors): ~1 arcsec resolution cannot resolve nuclear regions; f_AGN depends on templates  
  > "our observations are not able to resolve the central regions of the galaxies down to the 100-500 pc scales" (4.1)
- Caveat (inferred, ours): Low number statistics for CO(7-6) and [CI]
- Caveat (inferred, ours): f_AGN depends on templates and photometric coverage
- Caveat (inferred, ours): Heterogeneous literature compilations in fit

## Reproducibility

- Data public (paper): Master catalog and updated table publicly available  
  > "The master catalog containing all the measurements necessary to reproduce this analysis is publicly available (V20a)." (1 Introduction)
- Products in archive: _not stated_
- Code: STARDUST on GitHub  
  > "<https://github.com/VasilyKokorev/stardust>" (footnote 3)
- Missing: Raw ALMA processing deferred to V20a
- Missing: Private Herschel/SED remodeling of ASPECS sources
- Data volume (inferred): Reproducing from released tables is small (<1 GB); raw ALMA data would be tens of GB
- Score (inferred): 4/5, Released catalog and public code enable reproduction of statistics, but observational details are inherited.
- Rediscovery candidate: yes, Public catalog, stated tests and fit, numeric results.

## Links

- Method: (cite: kokorev_2021) (STARDUST SED code)
- Method: (cite: kelly_2007) (Bayesian linear regression)
- Companion: (cite: valentino_2020c) (V20a survey and master catalog)
- Companion: (cite: puglisi_2021) (far-IR sizes)
- Related: COSMOS
- Related: PEP
- Related: ASPECS

## Checks

```json
{
 "quotes": 42,
 "quotes_ok": 42,
 "quote_pass_rate": 1.0,
 "quotes_too_long": 0,
 "unsupported_facts": 0,
 "project_codes": 5,
 "codes_not_in_text": [],
 "codes_not_in_obscore": [],
 "obscore_codes_not_in_card": [],
 "codes_printed_but_missing": [],
 "numeric_results": 5,
 "numeric_problems": 0,
 "fill": {
  "facts": 69,
  "stated": 27,
  "rate": 0.391
 },
 "evidence_ok": true
}
```
