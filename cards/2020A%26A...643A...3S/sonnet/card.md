# The ALPINE-ALMA [C II] survey. Little to no evolution in the [C II]-SFR relation over the last 13 Gyr

`2020A&A...643A...3S` | Astronomy and Astrophysics 2020 | first author: Schaerer, D. | arXiv: 2002.00979 | DOI: 10.1051/0004-6361/202037617

Card schema 1.0 | model claude-sonnet-5-5 | depth full | type large_program_or_survey

## Science

- Fields: high_z_galaxies
- Question: Does the [C II] 158 micron luminosity trace SFR at z>4 as in local galaxies, i.e. is there evolution in the L([CII])-SFR relation?  
  > "it is unclear if the \[C ii\] 158 $\mu$m line remains a good tracer of star formation at $z> 4$ or if there is a quantitative change compared to the observations at low redshift." (Introduction)
- Target **ALPINE sample of 118 star-forming galaxies**: coordinates _not stated_; z/distance 4.4 < z < 5.9  
  > "has observed 118 ‘normal’ star-forming galaxies with known spectroscopic redshifts at $4.4 < z< 5.9$." (2 Observations and derived quantities); distance from known spectroscopic redshifts  
  > "has observed 118 ‘normal’ star-forming galaxies with known spectroscopic redshifts at $4.4 < z< 5.9$." (2 Observations and derived quantities)

## Data provenance

- ALMA projects: 2017.1.00428.L
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
- Line: [C II] 158 micron (not stated)
- Other facility **Keck DEIMOS and VLT VIMOS**: rest-UV spectra giving Lyα equivalent widths (via Cassata et al.)  
  > "which were obtained during earlier spectroscopic observations with DEIMOS and VIMOS on the Keck and VLT telescopes." (2 Observations and derived quantities)
- External data: ALPINE [C II] luminosities, upper limits and dust continuum measurements  
  > "Details of the ALPINE data reduction and statistical source properties are described in (cite: Bethermin2020The-ALPINE-ALMA)" (2 Observations and derived quantities) [from (cite: Bethermin2020The-ALPINE-ALMA)]
- External data: IRX-beta relation from stacking, used for L_IR  
  > "we also used $L_{\rm IR}$ values derived from the IRX–$\beta$ relation obtained by stacking of the ALPINE sources, as described in (cite: Fudamoto2020The-ALPINE-ALMA)." (2 Observations and derived quantities) [from (cite: Fudamoto2020The-ALPINE-ALMA)]
- External data: Lyα equivalent widths  
  > "The Ly$\alpha$ measurements, available for 98 sources, are taken from (cite: Cassata2020The-ALPINE-ALMA)" (2 Observations and derived quantities) [from (cite: Cassata2020The-ALPINE-ALMA)]
- External data: Local L([CII])-SFR reference relation  
  > "It includes 184 galaxies, shows a linear scaling between $L({\rm [CII]})$ and SFR, and a scatter of 0.27 dex" (3.1) [from (cite: De-Looze2014The-applicabili)]
- External data: Compilation of 25 z=6-7.2 [C II] observations  
  > "we use the recent compilation of (cite: Matthee2019Resolved-UV-and), which includes 25 reported ALMA \[C ii\] observations of galaxies" (3.3) [from (cite: Matthee2019Resolved-UV-and)]
- External data: 11 additional z=6-9.11 measurements  
  > "we add 11 measurements (6 detections, 5 upper limits) of galaxies between $z=6.0$ and 9.11 from (cite: Harikane2019Large-Populatio)" (3.3) [from (cite: Harikane2019Large-Populatio)]
- External data: SED-fit SFRs and UV data  
  > "We also used estimates of the total SFR, SFR(SED), obtained from the multi-band SED fits of (cite: Faisst2020The-ALPINE-ALMA)." (2 Observations and derived quantities) [from (cite: Faisst2020The-ALPINE-ALMA)]

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

- ALPINE data reduction, [C II] luminosities, limits and L_IR conversion  
  > "The 158 $\mu$m rest-frame continuum fluxes have been" (2 Observations and derived quantities) [from (cite: Bethermin2020The-ALPINE-ALMA)]
- SFR calibrations for UV and IR taken from De Looze et al., rescaled to Chabrier IMF  
  > "we adopted the same conversion factors between $L_{\rm UV}$, $L_{\rm IR}$, and SFR as the ones used in their paper." (2 Observations and derived quantities) [from (cite: De-Looze2014The-applicabili)]
- Bayesian censored linear fit method  
  > "We follow the method of (cite: Kelly2007Some-Aspects-of) implemented in the python package *linmix*" (3.2 footnote) [from (cite: Kelly2007Some-Aspects-of)]

### Not stated but needed to reproduce (our reading)

- linmix settings (iterations, priors, chains)
- Exact per-source catalog values (ALPINE database release version)
- Exact rescaling procedure for literature SFRs to common IMF
- Which ALPINE sources were excluded from fits (74 vs 75 detections)

## Analysis recipe

1. **Assemble [C II], L_IR and SFR for ALPINE**: Use published ALPINE [C II] luminosities and continuum; convert 158um continuum to L_IR with an empirical template; compute SFR(UV), SFR(IR), SFR(tot), with 3 sigma upper limits rescaled to FWHM=150 km/s  
  > "we adopted FWHM $= 150$ km s$^{-1}$, instead of the median of $252$ km s$^{-1}$ of the \[C ii\]-detected ALPINE galaxies" (2 Observations and derived quantities)
   - parameter: SFR(UV)=1.59e-10 L_UV/Lsun; SFR(IR)=1.40e-10 L_IR/Lsun (Chabrier)  
  > "SFR(IR)/(M$_{\odot}$ yr$^{-1}$)$=1.40 \times 10^{-10} L_{\rm IR} /L_{\odot}$." (2 Observations and derived quantities)
   - assumption: Template similar to modified blackbody T_d=42 K, beta=1.5  
  > "a dust temperature of $T_d = 42$ K, a dust opacity at 850 $\mu$m of $k_{850} = 0.077 ~ {\rm m^2 ~kg^{-1}}$, and a grey-body power-law exponent $\beta = 1.5$" (2 Observations and derived quantities)
   - fitting: _not stated_
   - validation: _not stated_
2. **Correct for hidden star formation**: Apply mean IRX-beta relation to continuum-undetected sources; compare also SED-based SFRs and stacks  
  > "We applied their mean IRX–$\beta$ relations to each individual source for which the dust continuum had not been detected" (3.2)
   - fitting: _not stated_
   - validation: Compared with SED-based and stacking corrections  
  > "it corresponds to the average correction obtained from multi-band SED fitting of the rest-UV-to-optical SED" (4 Discussion)
3. **Fit L([CII])-SFR relation with censored data**: Bayesian linear fit log L = a + b log SFR including upper limits, for ALPINE and ALPINE+z>6 compilation  
  > "fitted using a Bayesian fit including censored data following the method of (cite: Kelly2007Some-Aspects-of), which is implemented in the *linmix* python package." (Appendix)
   - software: linmix
   - fitting: _not stated_
   - validation: _not stated_

## Software

- **linmix** : Bayesian linear regression with censored data  
  > "implemented in the python package *linmix*" (3.2 footnote)

## Numeric results

| quantity | value | uncertainty | units | step | quote |
|---|---|---|---|---|---|
| Offset of ALPINE [C II] detections from local relation using UV+IRX SFR | -0.05 | scatter 0.28 dex | dex | 2 | showing a very small offset from the local relation ($-0.05$ dex) and a scatter of 0.28 dex around it |
| Slope, ALPINE, UV+IRX, aggressive limits | 1.17 | 0.12 | dimensionless | 3 | / ALPINE / UV+IRX / 3-$\sigma$ / 6.61 / 0.20 / 1.17 / 0.12 / 4 / |
| Slope, ALPINE, UV+IRX, secure limits | 0.96 | 0.09 | dimensionless | 3 | our fits including censored data yields a slope of $0.96 \pm 0.09$ |
| Slope, ALPINE + z>6 | 1.28 | 0.1 | dimensionless | 3 | somewhat steeper (super-linear) slope ($1.28 \pm 0.1$) |
| L([CII])/L_IR of continuum-detected ALPINE | (1-3)e-3 | not stated | dimensionless | 0 | show a ratio $L({\rm [CII]})$/$L_{\rm IR}$$\sim (1-3) \times 10^{-3}$ |
| Mean offset using SED SFRs | 0.06 | scatter 0.40 dex | dex | 2 | is then reduced to 0.06 dex, although the scatter around the local relation is quite large (0.40 dex) |

## Qualitative findings

- No strong evidence for a [C II] deficit at z~4-8 once hidden SF is accounted for; no strong dependence on Lyα EW  
  > "the currently available data show no strong evidence for a deficit of \[C ii\] from $z \sim 4$ to 8" (5 Conclusions)

## Claim tuples


## Reasoning

- Why this data: _not stated_
- Why this method: _not stated_
- How they decided it was enough: _not stated_
- Limitation (authors): Slope depends on assumptions for [C II] upper limits and on the dust-obscured SFR, which depends on the IR template and dust temperature  
  > "the exact slope of the relation depends in part on the \[C ii\]-undetected sources, and hence on the detailed assumptions on the upper limits" (4 Discussion)
- Caveat (inferred, ours): Dust temperature and IR template choice shifts SFR(IR) systematically
- Caveat (inferred, ours): Mixed literature samples with heterogeneous selection
- Caveat (inferred, ours): Censored fit sensitive to upper-limit definition

## Reproducibility

- Data public (paper): ALPINE database where data will be made public  
  > "The different SFR measurements are all included in the ALPINE database[^2], where the data will be made public." (2 Observations and derived quantities)
- Products in archive: _not stated_
- Missing: Catalogs from companion ALPINE papers
- Missing: linmix settings
- Data volume (inferred): Catalog-level; raw ALPINE data are hundreds of GB but not needed
- Score (inferred): 3/5, Analysis is catalog-based and simple, but depends on companion-paper tables and unspecified fit settings.
- Rediscovery candidate: no, Relies on derived catalogs from other papers, not a self-contained ALMA reduction.

## Links

- Method: (cite: Bethermin2020The-ALPINE-ALMA) (Data reduction and source properties)
- Method: (cite: Fudamoto2020The-ALPINE-ALMA) (IRX-beta relation)
- Companion: (cite: Le-Fevre2019The-ALPINE-ALMA) (ALPINE survey description)
- Companion: (cite: Faisst2020The-ALPINE-ALMA) (Ancillary data and SED fits)
- Companion: (cite: Cassata2020The-ALPINE-ALMA) (Lyα properties)
- Related: ALPINE

## Checks

```json
{
 "quotes": 33,
 "quotes_ok": 33,
 "quote_pass_rate": 1.0,
 "quotes_too_long": 0,
 "unsupported_facts": 0,
 "project_codes": 1,
 "codes_not_in_text": [],
 "codes_not_in_obscore": [],
 "obscore_codes_not_in_card": [],
 "codes_printed_but_missing": [],
 "numeric_results": 6,
 "numeric_problems": 0,
 "fill": {
  "facts": 68,
  "stated": 24,
  "rate": 0.353
 },
 "evidence_ok": true
}
```
