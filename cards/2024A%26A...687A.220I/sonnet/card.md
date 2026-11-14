# Rotational spectroscopy of CH<SUB>3</SUB>OD with a reanalysis of CH<SUB>3</SUB>OD toward IRAS 16293-2422

`2024A&A...687A.220I` | Astronomy and Astrophysics 2024 | first author: Ilyushin, V. V. | arXiv: 2406.08236 | DOI: 10.1051/0004-6361/202449918

Card schema 1.0 | model claude-sonnet-5-5 | depth light | type multi_facility_alma_minor

## Science

- Fields: astrochemistry, star_formation
- Question: Improve CH3OD rotational spectroscopy (v_t=0,1,2) and use it to redetermine the CH3OD column density and D/H in the hydroxy group of methanol toward IRAS 16293-2422 B  
  > "We generated a line list that is based on our present results, which we applied to a reanalysis of CH$_3$OD in ALMA data of the Protostellar Interferometric Line Survey" (Introduction)
- Target **IRAS 16293-2422 B**: coordinates RA 16h32m22.58s, Dec -24d28m32.80s (J2000), one beam offset from B  
  > "Toward a position slightly offset from the "B" component of the system (RA, Dec (J2000) of $16^{\text{h}}32^{\text{m}}22.58^{\text{s}}$, $-24^{\circ}28\ensuremath{'}32.80\ensuremath{''}$)" (5 CH3OD in IRAS 16293-2422); z/distance _not stated_; distance from _not stated_

## Data provenance

- ALMA projects: 2013.1.00278.S
- bands: _not stated_
- frequencies and spectral setup: 329-363 GHz; spectral resolution ~0.2 km/s  
  > "covering the frequency range from $329$ to $363$ GHz" (5 CH3OD in IRAS 16293-2422); "at an angular resolution of $\sim0.5''$ and a spectral resolution of $\sim0.2$ km s$^{-1}$" (5 CH3OD in IRAS 16293-2422)
- continuum bandwidth: _not stated_
- arrays: _not stated_
- configurations: _not stated_
- baselines: _not stated_
- angular resolution: ~0.5 arcsec  
  > "at an angular resolution of $\sim0.5''$" (5 CH3OD in IRAS 16293-2422)
- max recoverable scale: _not stated_
- sensitivity: _not stated_
- time on source: _not stated_
- observing dates: _not stated_
- pi or archival as stated: PILS, PI Jes K. Jørgensen  
  > "project-id: 2013.1.00278.S, PI: Jes K. Jørgensen" (5 CH3OD in IRAS 16293-2422)
- External data: Methanol column density (1.0±0.2)e19 cm-2 for D/H  
  > "the adopted methanol column densities is $(1.0\pm0.2)\times10^{19}$ cm$^{-2}$" (Table 1) [from (cite: deuteration_16293_2018)]
- External data: Earlier CH3OD N=1.8e17 cm-2, Tex=300 K (for comparison)  
  > "of $N=1.8\times10^{17}$ cm$^{-2}$ and $T_{\text{ex}}=300$ K" (5 CH3OD in IRAS 16293-2422) [from (cite: deuteration_16293_2018)]
- External data: Methyl group deuteration (2.4±0.72)% incl. statistical correction of three  
  > "Including the statistical correction of three, the methyl group deuteration is $(2.4\pm0.72)\%$" (5 CH3OD in IRAS 16293-2422) [from (cite: deuteration_16293_2018)]

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

- PILS dataset and its reduction  
  > "The full details on the PILS dataset and its reduction are available in (cite: PILS_2016)." (5 CH3OD in IRAS 16293-2422) [from (cite: PILS_2016)]
- MCMC fitting methodology with emcee  
  > "its application is described in detail in Section $2.3$ of (cite: CHD2OH_catalog_2022)" (5 CH3OD in IRAS 16293-2422) [from Section 2.3 of (cite: CHD2OH_catalog_2022)]
- Number of walkers and parameter space setup  
  > "The number of walkers and the parameter space setup used here match what was used for the analysis of CHD$_{2}$OH in (cite: CHD2OH_catalog_2022)." (5 CH3OD in IRAS 16293-2422) [from (cite: CHD2OH_catalog_2022)]

### Not stated but needed to reproduce (our reading)

- Priors and ranges of Tex and N in MCMC
- Spectral extraction method/aperture and continuum subtraction for PILS data
- Exact list of 97 lines used and blending criteria details
- Partition function values used
- Whether PILS reduced data products are the ones used

## Analysis recipe

1. **Select unblended optically thin CH3OD lines**: Remove blended and optically thick lines (tau>0.1 at Tex 50 or 300 K, N=4.5e16) from 485 covered lines, leaving 97 unique frequencies  
  > "After the removal of the blended and optically thick lines, $97$ unique line frequencies remained" (5 CH3OD in IRAS 16293-2422)
   - fitting: _not stated_
   - validation: _not stated_
2. **Fit LTE synthetic spectra for Tex and N**: MCMC fit of LTE synthetic spectra including non-detected lines  
  > "The fitting methodology is based on the MCMC Python package EMCEE" (5 CH3OD in IRAS 16293-2422)
   - software: emcee
   - parameter: Beam and source size fixed to 0.5"; FWHM 1 km/s; vLSR 2.7 km/s; 300 walkers; 1500 steps for joint fit  
  > "Beam size and source size were both fixed to $0.5''$ and were both assumed to have Gaussian distributions" (5 CH3OD in IRAS 16293-2422)
   - assumption: LTE excitation  
  > "assume that the excitation of the molecule is characterized by local thermodynamical equilibrium (LTE)" (5 CH3OD in IRAS 16293-2422)
   - fitting: emcee MCMC, mean acceptance fraction 70-71%  
  > "the mean acceptance fraction of the $300$ walkers is $70-71\%$" (5 CH3OD in IRAS 16293-2422)
   - validation: Corner plot convergence; compared with old spectroscopy  
  > "the quality of the convergence is illustrated in the corner plot" (5 CH3OD in IRAS 16293-2422)
3. **Derive D/H of methanol hydroxy group**: N(CH3OD)/N(CH3OH), statistical correction one  
  > "the statistical correction on the D/H ratio for the case of deuteration in the hydroxy group is one" (Table 1)
   - fitting: _not stated_
   - validation: _not stated_

## Software

- **emcee** : MCMC fitting of synthetic spectra  
  > "The fitting methodology is based on the MCMC Python package EMCEE" (5 CH3OD in IRAS 16293-2422)
- **RAM36** : Fitting torsion-rotation Hamiltonian and predicting CH3OD line list  
  > "We employed the RAM36 code (cite: Ilyushin:2010; Ilyushin:2013)" (3 Spectroscopic properties)

## Numeric results

| quantity | value | uncertainty | units | step | quote |
|---|---|---|---|---|---|
| Tex (v_t=0,1 together) | 190 | ±19 | K | 2 | $T_{\text{ex}}$ (K) / $190\pm19$ |
| N(CH3OD) (v_t=0,1) | 3.25e16 | ±0.65e16 | cm-2 | 2 | $(3.25\pm0.65)\times10^{16}$ |
| D/H of CH3OH (hydroxy) | 0.32% | ±0.09% | percent | 3 | The newly determined best-fitting D/H ratio for CH$_{3}$OD is $(0.32\pm0.09)\%$. |
| Spectroscopic fit wrms | 0.85 | not stated | dimensionless | 0 | A Hamiltonian model consisting of 134 parameters provided a fit with a weighted root mean square (wrms) deviation of 0.85 |

## Qualitative findings

- Hydroxy-group D/H is ~7.5 times lower than methyl-group D/H, the lowest of measured molecules in IRAS 16293B  
  > "the newly determined hydroxy group deuteration is a factor of $\sim$7.5 lower" (5 CH3OD in IRAS 16293-2422)

## Claim tuples

- H: Do new spectroscopy change CH3OD N and Tex toward IRAS 16293B? | E: LTE MCMC fit of 97 lines in PILS using new line list | R: N=3.25e16 cm-2, Tex=190 K; N lower by ~5.5 | F: Earlier column density was overestimated, partly due to a partition function factor-of-four error | **supported**
- H: Does OD D/H match CH3 D/H in methanol? | E: Compare new D/H with earlier methyl value | R: 0.32% vs 2.4% | F: They do not match | **supported**

## Reasoning

- Why this data: _not stated_
- Why this method: _not stated_
- Alternative: Fitting v_t=0 and 1 separately judged unnecessary  
  > "there is no reason to fit the $\varv_{\rm t}=0$ and $1$ states of CH$_{3}$OD separately in the PILS data" (5 CH3OD in IRAS 16293-2422)
- How they decided it was enough: _not stated_
- Limitation (authors): Temperature/column gradients and compact emission of high-excitation lines may bias fit; no higher resolution constraints  
  > "it is likely that there are gradients in temperatures, column densities, and extents of the emission along the line of sight" (5 CH3OD in IRAS 16293-2422)
- Caveat (inferred, ours): Errors on N and Tex are assumed 20% and 10%, not MCMC-derived
- Caveat (inferred, ours): Single-component LTE with fixed 0.5" source size
- Caveat (inferred, ours): D/H depends on adopted methanol column from earlier work

## Reproducibility

- Data public (paper): PILS data and line list (Zenodo, CDMS) available  
  > "Electronic supplementary material for this work can be found at https://doi.org/10.5281/zenodo.11460242" (Footnote 1)
- Products in archive: _not stated_
- Missing: Extraction and priors details deferred to other papers
- Missing: Exact line list of 97 lines
- Data volume (inferred): ~tens of GB (PILS B-position spectra)
- Score (inferred): 3/5, Astronomical part relies on earlier papers for reduction and fit setup; line list is provided.
- Rediscovery candidate: no, Key recipe details are inherited from other papers and the main results are partly laboratory.

## Links

- Method: (cite: PILS_2016) (PILS data and reduction)
- Method: (cite: CHD2OH_catalog_2022) (MCMC fitting setup)
- Companion: (cite: deuteration_16293_2018) (earlier CH3OD analysis being revised)
- Companion: (cite: CD3OD_rot_2023) (previous methanol isotopolog study)
- Related: PILS

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
 "numeric_results": 4,
 "numeric_problems": 0,
 "fill": {
  "facts": 65,
  "stated": 24,
  "rate": 0.369
 },
 "evidence_ok": true
}
```
