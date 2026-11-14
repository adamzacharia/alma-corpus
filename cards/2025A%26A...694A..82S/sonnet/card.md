# The ALPINE-ALMA [CII] Survey: Unveiling the baryon evolution in the interstellar medium of z ∼ 5 star-forming galaxies

`2025A&A...694A..82S` | Astronomy and Astrophysics 2025 | first author: Sawant, P. | arXiv: 2412.02505 | DOI: 10.1051/0004-6361/202451542

Card schema 1.0 | model claude-sonnet-5-5 | depth light | type archival_reuse

## Science

- Fields: high_z_galaxies
- Question: Which processes of gas and dust production, consumption and destruction (outflows, inflows, SN dust, AGB dust, ISM dust growth, IMF) reproduce the observed gas and dust content of 98 ALPINE z~5 galaxies?  
  > "We make use of chemical evolution models to simultaneously reproduce the observed dust and gas content of our galaxies, as obtained from spectral energy distribution fitting and ionized carbon measurements, respectively." (abstract)
- Target **ALPINE sample (98 of 118 galaxies in COSMOS and ECDFS)**: coordinates _not stated_; z/distance 4.4<z<5.9 (excluding 4.6<z<5.1)  
  > "The ALPINE sample comprises 118 star-forming galaxies observed in [CII] emission line and far-infrared (FIR) continuum at redshifts $4.4<z<5.9$" (2 Data); distance from spectroscopic redshifts from previous campaigns (Le Fevre15, Tasca17, Hasinger18)  
  > "The ALPINE sample comprises 118 star-forming galaxies observed in [CII] emission line and far-infrared (FIR) continuum at redshifts $4.4<z<5.9$" (2 Data)

## Data provenance

- ALMA projects: _none stated_
- bands: Band 7 (275-373 GHz)  
  > "The ALPINE targets were observed for $\sim70$h during Cycles 5 and 6 in ALMA Band 7 (275-373 GHz)." (2 Data)
- frequencies and spectral setup: _not stated_
- continuum bandwidth: _not stated_
- arrays: _not stated_
- configurations: _not stated_
- baselines: _not stated_
- angular resolution: beam size ~1 arcsec  
  > "line-only cubes with channel width of $\sim25$ km/s and beam size $\sim1''$" (2 Data)
- max recoverable scale: _not stated_
- sensitivity: _not stated_
- time on source: ~70 h in Cycles 5 and 6  
  > "The ALPINE targets were observed for $\sim70$h during Cycles 5 and 6" (2 Data)
- observing dates: _not stated_
- pi or archival as stated: _not stated_
- Line: [CII] 158 um fine-structure line (not stated)
- Other facility **Multiwavelength ancillary data (UV to radio, COSMOS/ECDFS)**: UV-optical-NIR photometry for SED fitting  
  > "as determined through SED fitting (cite: Faisst20) of their multi-wavelength data, encompassing UV to X-ray and radio bands" (2 Data)
- External data: [CII] luminosities of each galaxy  
  > "where $L_{\mathrm{[CII]}}$ is the [CII] luminosity of each galaxy computed by (cite: Bethermin20)" (3.4 Estimates of the total gas mass) [from (cite: Bethermin20)]
- External data: L[CII]-Mgas calibration  
  > "we utilize the prescription by (cite: Zanella18) to estimate the molecular gas mass" (3.4 Estimates of the total gas mass) [from (cite: Zanella18)]
- External data: Composite IR dust template  
  > "we utilize the composite infrared (IR) template constructed by (cite: Burgarella22) using a sample of 27 ALMA-detected galaxies at $4<z<6$" (3.1.1 Dust emission) [from (cite: Burgarella22)]
- External data: Outflow mass-loading constraint eta_out~1 (factor 3 uncertainty)  
  > "who found $\eta_{out}\sim1$ from the stacked [CII] spectrum of the ALPINE sources, with a factor 3 of uncertainty" (3.2.1 Gas evolution) [from (cite: Ginolfi20b)]

## Processing

### Calibration

- pipeline or manual: standard CASA pipeline  
  > "Data reduction and calibration were performed using the standard Common Astronomy Software Applications (CASA; (cite: McMullin07)) pipeline." (2 Data)
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
- continuum subtraction: each cube continuum-subtracted; channel ~25 km/s, pixel ~0.15 arcsec  
  > "Each data cube was continuum-subtracted to produce line-only cubes with channel width of $\sim25$ km/s" (2 Data)
- line free channels: _not stated_
- primary beam correction: _not stated_
- array combination: _not stated_
- smoothing: _not stated_
- final beam: _not stated_
- final rms: _not stated_

### Inherited from earlier work

- ALPINE observation and data processing  
  > "We refer to (cite: LeFevre20), (cite: Bethermin20), and (cite: Faisst20) for a detailed description" (2 Data) [from (cite: LeFevre20), (cite: Bethermin20)]
- Sample selection (>5 UV-optical data points, S/N>2.5)  
  > "Following (cite: Burgarella22), we selected only the ALPINE galaxies with more than 5 data points in the UV-optical coverage" (2 Data) [from (cite: Burgarella22)]
- Delayed SFH with tau=500 Myr, no burst  
  > "a delayed SFH with $\tau_{main} = 500$ Myr and without burst was slightly favored over other SFHs by statistical tests, and hence we adopt the same SFH." (3.1.2 SFH) [from (cite: Burgarella22)]
- Chemical evolution model formalism  
  > "The evolution of baryons in the ISM of galaxies, i.e., the gas, metals, and dust, are followed as explained in (cite: Nanni20)." (3.2 Chemical evolution model) [from (cite: Nanni20)]

### Not stated but needed to reproduce (our reading)

- Exact CASA version and ALMA project codes
- Photometric catalog used as SED input (from Faisst20) and detection/upper-limit treatment in CIGALE
- Chemical model code availability
- Full CIGALE module grid beyond the parameter table
- Per-galaxy best-fit values

## Analysis recipe

1. **SED fitting for M*, SFR, age, dust mass**: CIGALE with delayed SFH, modified Calzetti attenuation, Draine14-based composite IR template; Chabrier and top-heavy IMF  
  > "We use the Code Investigating GALaxy Emission (CIGALE; (cite: Burgarella05; Noll09; Boquien19)) to model the SEDs of our galaxies." (3.1 SED fitting)
   - software: CIGALE
   - parameter: tau_main=500 Myr; q_PAH=0.47; THIMF slope xi=1.8 adopted  
  > "we adopt a fixed THIMF slope of $\xi$ = 1.8 throughout this paper" (4.1 SED fitting with different IMFs)
   - assumption: Dust masses from CIGALE divided by 2 to match carbon/silicate composition (70%/30%) and Draine07 opacities  
  > "we divide the dust masses derived from CIGALE by a factor of 2 for subsequent analysis" (3.3 Estimates of the dust masses)
   - fitting: Bayesian estimates  
  > "CIGALE is a modeling and fitting tool that operates on the principle of energy balance between the energy absorbed in the rest-frame UV-NIR part of the total SED of galaxy" (Methodology, SED fitting and dust emission models)
   - validation: Mock CIGALE analysis, r^2>0.85, with and without IR template  
  > "simulated and input parameters lie mostly along the $\mathrm{1:1}$ relation, with a strong positive correlation (i.e., $\mathrm{r^2>0.85}$" (Appendix: Reliability of stacked IR template)
2. **Derive gas mass from [CII]**: Zanella18 L[CII]-Mgas relation  
  > "$$\mathrm{log_{10}}(L_{\mathrm{[CII]}}/L_{\odot}) = (-1.28\pm0.21) + (0.98\pm0.02)~\mathrm{log_{10}}(M_{\mathrm{gas}}/M_{\odot}),$$" (3.4 Estimates of the total gas mass)
   - fitting: _not stated_
   - validation: _not stated_
3. **Fit chemical evolution models to gas and dust**: Grid of OMEGA-based gas, metal and dust evolution tracks; reduced chi-square over Mgas, L160, SFR, age; chi2-probability-weighted mean of model parameters  
  > "We minimize the reduced chi-square for each source ($\chi^2_{\rm gal,m}$)" (3.5 Estimation of optimal model parameters)
   - software: OMEGA
   - parameter: eta_out 0-3, eta_in 0-10, SN condensation 5-100%, growth efficiency 0, 0.5, 1, eps_SN 0.1-1  
  > "Dust growth efficiency in the ISM | 0.0, 0.5, 1" (Model parameter table)
   - assumption: Terminal metallicity 12+log(O/H)~9.0; primordial inflow  
  > "We adopt the value $\mathrm{12 + 1og(O/H)} \sim 9.0$ to constrain the terminal metallicity of the models" (4.2 Constraining the gas content)
   - fitting: Chi2 minimization with chi2-probability weighting  
  > "We minimize the reduced chi-square for each source ($\chi^2_{\rm gal,m}$) by finding the residual between the "$n^{th}$" predicted galaxy’s physical parameter" (Estimation of optimal model parameters)
   - validation: Compared tracks to sMgas, sMdust, DTG vs sSFR; Chabrier vs THIMF  
  > "We present the observed specific mass of gas (i.e., $\mathrm{sM_{Gas}} \equiv \mathrm{M_{Gas}/M_{*}}$) as a function of specific star formation rate" (Constraining the gas content)

## Software

- **CASA** : ALMA data reduction (pipeline)  
  > "standard Common Astronomy Software Applications (CASA; (cite: McMullin07)) pipeline" (2 Data)
- **CIGALE** : SED fitting  
  > "We use the Code Investigating GALaxy Emission (CIGALE; (cite: Burgarella05; Noll09; Boquien19)) to model the SEDs of our galaxies." (3.1 SED fitting)
- **OMEGA** : Gas ejection and astration terms in chemical evolution  
  > "calculated with the One-zone Model for the Evolution of GAlaxies (OMEGA) code (cite: Cote17)" (3.2.1 Gas evolution)

## Numeric results

| quantity | value | uncertainty | units | step | quote |
|---|---|---|---|---|---|
| Median log stellar mass (Chabrier) | 9.57 | +0.38/-0.29 | log Msun | 1 | $\log_{10}(M_{*}/M_{\odot}) = 9.57_{-0.29}^{+0.38}$ |
| Median log dust mass (Chabrier) | 7.2 | +0.27/-0.51 | log Msun | 1 | $\log_{10}(M_{\text{Dust}}/M_{\odot}) = 7.2_{-0.51}^{+0.27}$ |
| Fraction of galaxies reproduced (Chabrier / THIMF) | 65% / 93% | not stated | percent | 3 | We find that $65\%$ of our galaxies can be reproduced with a canonical Chabrier IMF. The fraction increases to $93\%$ when adopting a THIMF. |
| Mean optimal initial gas mass (Chabrier / THIMF) | 3.3 / 4.4 x M_star,fin | not stated | M_star,fin | 3 | M$_{\rm Gas, ini}$ [M$_\odot$] (THIMF) / 4.4 $\times M_{\rm star, fin}$ |

## Qualitative findings

- Outflows (eta_out~2) are needed; SNII dominate dust in older galaxies, ISM growth matters for intermediate ages; top-heavy IMF helps but youngest dusty galaxies remain unreproduced  
  > "Outflow efficiencies of the order of $\sim2$ are especially needed for galaxies $\gtrsim300~$Myr old" (6 Conclusions)

## Claim tuples

- H: Can chemical evolution models reproduce gas and dust of z~5 galaxies, and does a top-heavy IMF help? | E: Fit model grids to CIGALE and [CII]-derived quantities for 98 galaxies with both IMFs | R: 65% reproduced with Chabrier, 93% with THIMF | F: THIMF alleviates the tension, but the youngest dusty sources remain unexplained | **partially**

## Reasoning

- Why this data: _not stated_
- Why this method: _not stated_
- Alternative: Delayed plus burst SFH did not fix the youngest galaxies' too-large sMdust  
  > "Despite these variations, the $\mathrm{sM_{Dust}}$ derived for the youngest galaxies remains too large to be reproduced by the current models." (5.2)
- How they decided it was enough: _not stated_
- Limitation (authors): Dust masses uncertain by ~factor 3 depending on opacity and method  
  > "the estimates of the dust masses can vary approximately a factor of $\sim$3" (3.3)
- Caveat (inferred, ours): Results depend on assumed SFH and dust opacity
- Caveat (inferred, ours): Gas mass from the [CII] conversion is uncertain
- Caveat (inferred, ours): Model degeneracies among condensation, outflow and growth
- Caveat (inferred, ours): The ALMA data enter only through published [CII] luminosities

## Reproducibility

- Data public (paper): High-level products public via ALMA archive and collaboration website  
  > "All high-level data products are publicly available to the community through ALMA archive and the collaboration website" (2 Data)
- Products in archive: _not stated_
- Missing: Chemical model code and grid
- Missing: Photometric inputs
- Missing: CIGALE configuration details
- Data volume (inferred): small (published catalogs)
- Score (inferred): 3/5, Methods and parameter grids are described, but the code and inputs are not released and the work relies on external catalogs.
- Rediscovery candidate: no, The results depend on a custom chemical evolution model and external catalogs that are not fully specified.

## Links

- Method: (cite: Burgarella22) (IR template and SED setup)
- Method: (cite: Nanni20) (Chemical evolution model)
- Method: (cite: Bethermin20) (ALPINE data processing and [CII] luminosities)
- Companion: (cite: LeFevre20) (ALPINE survey description)
- Related: ALPINE
- Related: REBELS

## Checks

```json
{
 "quotes": 42,
 "quotes_ok": 42,
 "quote_pass_rate": 1.0,
 "quotes_too_long": 0,
 "unsupported_facts": 0,
 "project_codes": 0,
 "codes_not_in_text": [],
 "codes_not_in_obscore": [],
 "obscore_codes_not_in_card": [
  "2017.1.00428.L"
 ],
 "codes_printed_but_missing": [],
 "numeric_results": 4,
 "numeric_problems": 0,
 "fill": {
  "facts": 71,
  "stated": 35,
  "rate": 0.493
 },
 "evidence_ok": true
}
```
