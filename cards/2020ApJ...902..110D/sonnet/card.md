# The ALMA Spectroscopic Survey in the Hubble Ultra Deep Field: Multiband Constraints on Line-luminosity Functions and the Cosmic Density of Molecular Gas

`2020ApJ...902..110D` | The Astrophysical Journal 2020 | first author: Decarli, Roberto | arXiv: 2009.10744 | DOI: 10.3847/1538-4357/abaa3b

Card schema 1.0 | model claude-sonnet-5-5 | depth full | type large_program_or_survey

## Science

- Fields: high_z_galaxies, milky_way_ism
- Question: What are the CO and atomic-line luminosity functions in the ASPECS 1.2 mm cube combined with the 3 mm results, and how does the cosmic molecular gas density rho_H2 evolve with redshift?  
  > "we capitalize on the completed ASPECS dataset in order to constrain the luminosity functions and average cosmic content of molecular gas in galaxies throughout cosmic time." (Introduction)
- Target **Hubble Ultra Deep Field (XDF) mosaic**: coordinates _not stated_; z/distance line candidates at z~0.3-8  
  > "a mosaic of 85 pointings in the eXtremely Deep Field (XDF" (2.1 ALMA data); distance from MUSE and ancillary catalog redshifts; bootstrap for sources without counterparts  
  > "a mosaic of 85 pointings in the eXtremely Deep Field (XDF" (2.1 ALMA data)

## Data provenance

- ALMA projects: 2016.1.00324.L
- bands: Band 6 (1.2 mm) new; Band 3 (3 mm) from earlier work  
  > "comprising two bands, at 3 mm and 1.2 mm." (2.1 ALMA data)
- frequencies and spectral setup: eight frequency tunings covering 212-272 GHz  
  > "The observations sampled eight different frequency tunings, continuously encompassing the entire 212–272 GHz window" (2.1 ALMA data)
- continuum bandwidth: _not stated_
- arrays: _not stated_
- configurations: C40-1 or C40-2  
  > "The array was in compact, C40-1 or C40-2 configurations, with baselines in the range 15 m–320 m." (2.1 ALMA data)
- baselines: 15 m-320 m  
  > "The array was in compact, C40-1 or C40-2 configurations, with baselines in the range 15 m–320 m." (2.1 ALMA data)
- angular resolution: ~1.5'' x 1.1''  
  > "The resulting beam is $\sim1.5''\times1.1''$." (2.1 ALMA data)
- max recoverable scale: _not stated_
- sensitivity: ~0.5 mJy/beam per 15.627 MHz channel  
  > "We reach a sensitivity of $\sim 0.5$ mJy beam$^{-1}$ per 15.627 MHz channel" (2.1 ALMA data)
- time on source: _not stated_
- observing dates: 2017 March-April and 2018 May-July  
  > "a first pass in 2017, March – April (roughly 20% of the total data volume spread among all of the requested frequency settings) and the remainder in 2018, May – July." (2.1 ALMA data)
- pi or archival as stated: _not stated_
- Line: CO J=3-2 to 11-10 (1.2 mm) (not stated)
- Line: [CI] 1-0 and 2-1 (not stated)
- Line: [CII] 158 um (not stated)
- Other facility **HST/3D-HST catalog, CANDELS**: photometric catalog and redshifts for counterparts  
  > "We employ the 3D-*HST* photometric catalog by (cite: skelton14)" (2.2 Ancillary data)
- Other facility **MUSE HUDF**: spectroscopic redshifts  
  > "More than $1500$ galaxies have secured redshifts from MUSE (cite: inami17)" (2.2 Ancillary data)
- External data: CO excitation ratios r_J1 for CO(J-(J-1))-to-CO(1-0)  
  > "with $r_{J1}=\{0.75\pm0.11$, $0.46\pm0.07$, $0.31\pm0.07\}$, for $J_{\rm up}$=$\{$2, 3, 4$\}$." (3.4) [from (cite: boogaard20)]
- External data: ASPECS 3 mm line search and luminosity functions  
  > "We also correct the results from ASPECS LP 3 mm (cite: decarli19) accordingly for galaxies at $z<2$." (3.4) [from (cite: decarli19)]
- External data: [CI] excitation temperature T_ex=29+-6 K  
  > "In our analysis, we assume $T_{\rm ex}=29\pm6$ K (cite: walter11)." (3.4) [from (cite: walter11)]
- External data: alpha_CO=3.6  
  > "we adopt $\alpha_{\rm CO}$=3.6 M$_\odot$ (K km s$^{-1}$ pc$^2$)$^{-1}$ (cite: daddi10a)" (3.4) [from (cite: daddi10a)]
- Simulation/model as data: Data-driven simulations used for cosmic variance  
  > "we follow the latter method by capitalizing on data–driven simulations presented in (cite: popping20)." (Cosmic variance)

## Processing

### Calibration

- pipeline or manual: CASA calibration pipeline, no additional flagging  
  > "We processed the raw data using the casa calibration pipeline for ALMA (cite: mcmullin07). No additional flagging was applied." (2.1 ALMA data)
- casa version: _not stated_
- pipeline version: _not stated_
- archive products used as is: _not stated_
- flux calibrator: _not stated_
- flux scale uncertainty: _not stated_
- self calibration: _not stated_

### Imaging

- task: tclean  
  > "We inverted the visibilities using the task tclean, and adopting natural weighting." (2.1 ALMA data)
- deconvolver: _not stated_
- weighting robust: natural  
  > "adopting natural weighting" (2.1 ALMA data)
- uv taper: _not stated_
- cell size: _not stated_
- image size: _not stated_
- masking: clean boxes on sources with continuum S/N>5; clean to 2 sigma per channel  
  > "Cleaning was performed down to 2-$\sigma$ per channel after putting cleaning boxes on all the sources with S/N$>$5 in their continuum emission." (2.1 ALMA data)
- multiscale scales: _not stated_
- continuum subtraction: cube with brightest line channels excluded  
  > "after identifying and excluding the channels with the brightest emission lines (see (cite: gonzalezlopez20) for details)" (2.1 ALMA data)
- line free channels: _not stated_
- primary beam correction: _not stated_
- array combination: _not stated_
- smoothing: tapered cube restoringbeam=2'' for 1D spectra  
  > "we degrade the angular resolution by setting the restoringbeam=$2''$ in the task tclean." (2.1 ALMA data)
- final beam: ~1.5'' x 1.1''  
  > "The resulting beam is $\sim1.5''\times1.1''$." (2.1 ALMA data)
- final rms: _not stated_

### Inherited from earlier work

- Continuum-subtracted cube and bright continuum source list  
  > "(see (cite: gonzalezlopez20) for details)" (2.1 ALMA data) [from (cite: gonzalezlopez20)]
- 1D spectrum extraction from tapered cube  
  > "We use this tapered cube to extract 1D spectra of the detected galaxies, following (cite: gonzalezlopez19)." (2.1 ALMA data) [from (cite: gonzalezlopez19)]
- Luminosity function construction approach  
  > "In the construction of the CO luminosity functions, we follow the approach adopted in (cite: decarli19)." (3.5) [from (cite: decarli19)]
- Bootstrap line identification for sources without counterpart  
  > "is done via a bootstrap approach, following, e.g., (cite: decarli19)." (3.3.2) [from (cite: decarli19)]

### Not stated but needed to reproduce (our reading)

- Observing details (executions, integration time, project calibrator details)
- FINDCLUMPS kernel widths and code availability
- Priors and chain settings of the custom MCMC line-fit
- CASA version
- Exact line-free channels used for continuum subtraction
- Fidelity fit parameter values
- Final cube and catalog of 234 line candidates (not given in the paper)

## Analysis recipe

1. **Line search**: FINDCLUMPS with floating channel average; positive and negative peaks, S/N>4  
  > "We search for emission lines in the original and the continuum-subtracted ASPECS LP 1.2 mm cubes using FINDCLUMPS" (3.1)
   - software: FINDCLUMPS
   - fitting: Gaussian noise tails plus power-law signal fitted to negative then positive distributions  
  > "we fit the observed distribution of the noise peaks with the tails of a Gaussian function centered at zero, and the additional signal due to real sources as a power law." (3.1)
   - validation: Fidelity from negative/positive peak ratio treated as an upper limit  
  > "we conservatively treat these estimates of the fidelity as upper limits" (3.1)
2. **Completeness**: Inject 8000 mock 3D Gaussian lines, rerun search  
  > "A total of 8000 mock lines were injected, $>3000$ of which reside within the area with $>50$% primary beam response." (3.1)
   - parameter: FWHM 0-800 km/s, peak 0-3 mJy; drop completeness<0.2  
  > "We drop all line candidates with a completeness of $<0.2$ from our analysis." (3.1)
   - fitting: _not stated_
   - validation: _not stated_
3. **Line fluxes**: Fit 1D spectrum with continuum and Gaussian, Bayesian MCMC with FINDCLUMPS priors  
  > "We then fit the extracted spectrum with a continuum and a Gaussian profile, using our custom Bayesian Monte Carlo Markov Chain procedure" (3.2)
   - fitting: custom MCMC  
  > "We then fit the extracted spectrum with a continuum and a Gaussian profile, using our custom Bayesian Monte Carlo Markov Chain procedure" (Line fluxes)
   - validation: Flux boosting tested with mocks, deemed negligible  
  > "we consider flux boosting negligible for the purpose of our analysis." (3.2)
4. **Line identification**: Cross-match within 1'' to catalogs with |dz|<0.1; bootstrap with weights for others  
  > "with a redshift separation of $|\delta z|=|z_{\rm cat}-z_{\rm line}|/(1+z_{\rm line}) < 0.1$ ($0.01$ for sources with a spectroscopic redshift)" (3.3.1)
   - fitting: _not stated_
   - validation: Chance association probability ~4.3%  
  > "we find that the probability of chance association is $\sim 4.3$%" (3.3.1)
5. **Luminosities and gas masses**: L' formula, r_J1 conversion to CO(1-0), M_H2 = alpha_CO L'; no CMB correction  
  > "we opt not to apply any CMB–related correction in the remainder of our analysis." (3.4)
   - assumption: alpha_CO=3.6 Msun/(K km/s pc2)  
  > "we adopt $\alpha_{\rm CO}$=3.6 M$_\odot$ (K km s$^{-1}$ pc$^2$)$^{-1}$ (cite: daddi10a)" (3.4)
   - fitting: _not stated_
   - validation: _not stated_
6. **Luminosity functions and rho_H2**: 5000 realizations; keep lines by fidelity; 0.5 dex bins; Gehrels Poisson errors; completeness and volume correction; sum over detections for rho_H2  
  > "we create 5000 realizations of the luminosity functions, folding in all of the uncertainties" (3.5)
   - fitting: _not stated_
   - validation: Compared with alternative treatments of lines without counterparts and cosmic variance simulations  
  > "To first order, the $\rho_{\rm H2}$ evolution is unaffected by our treatment of the sources without a counterpart in the catalog." (Identification of line candidates without near-infrared counterparts)

## Software

- **CASA (pipeline, tclean)** : calibration and imaging  
  > "We inverted the visibilities using the task tclean" (2.1 ALMA data)
- **FINDCLUMPS** : line candidate search  
  > "using FINDCLUMPS (cite: walter16; decarli19; gonzalezlopez19)" (3.1)

## Numeric results

| quantity | value | uncertainty | units | step | quote |
|---|---|---|---|---|---|
| Line candidates with fidelity>0.2 | 234 | not stated | count | 1 | The final catalog from the line search consists of 234 line candidates with fidelity $>0.2$, 75 with fidelity $>0.5$, and 35 with fidelity $>0.8$. |
| Fraction of 1.2 mm line flux from CO J=3-6 | 62% | ~25% | percent | 4 | more than half of the total flux measured in lines (62%) in the ASPECS LP 1.2 mm mosaic comes from intermediate–J CO transitions |
| [CI] fraction of 1.2 mm line flux | 12% | ~50% | percent | 4 | 12% from \[C i\]; and less than 1% from \[C ii\] |
| 3 mm line flux from CO(2-1) | 53% | not stated | percent | 4 | dominated by CO(2-1) (53%) and CO(3-2) (27%) |
| Decline in rho_H2 from z~1.5 to present | ~6 | not stated | factor | 6 | followed by a $\sim 6\times$ decline to the present day |
| CO luminosity function offset CO(2-1) vs CO(5-4) at z~1.43 | ~0.5 | not stated | dex | 6 | The inferred CO luminosity functions show an offset of about 0.5 dex in luminosity for a fixed number density. |

## Qualitative findings

- [CII] intensity mapping at reionization will face a significant CO foreground.  
  > "implies significant challenges for intensity mapping experiments of \[C ii\] emission in the epoch of reionization" (3.3.1)

## Claim tuples

- H: Which lines dominate the line flux in the two ASPECS bands? | E: Fidelity-corrected flux budget of line candidates with counterparts | R: CO(2-1)+CO(3-2) 80% at 3 mm; CO J=3-6 62%, [CI] 12%, [CII] <1% at 1.2 mm | F: CO is a major foreground for [CII] intensity mapping | **supported**
- H: Is gas in typical galaxies thermalized? | E: Compare CO LFs of different transitions at same redshift | R: 0.5 dex offset between CO(2-1) and CO(5-4) | F: Sub-thermal excitation on average up to z~4 | **supported**
- H: How does rho_H2 evolve and relate to SFR density? | E: Sum of gas mass of detections in redshift bins | R: Increase to z~1.5 then ~6x drop | F: Depletion time approximately constant | **supported**

## Reasoning

- Why this data: _not stated_
- Why this method: _not stated_
- Alternative: Four alternative schemes for lines without counterparts tested; results consistent within uncertainties  
  > "Discrepancies are always well within the uncertainties." (Identification of line candidates without near-infrared counterparts)
- How they decided it was enough: _not stated_
- Limitation (authors): Constant alpha_CO may be invalid at z>3  
  > "The arguments presented in Sec. [3.4] for a Galactic value may not be valid at $z\mathrel{\rlap{\lower 3pt \hbox{$\sim$}} \raise 2.0pt \hbox{$>$}}3$" (4.3)
- Caveat (inferred, ours): Many results depend on the excitation ratios from Boogaard+20
- Caveat (inferred, ours): Fidelity and identification of faint sources without counterparts are prior-dependent
- Caveat (inferred, ours): Cosmic variance not included in the error budget

## Reproducibility

- Data public (paper): ALMA Large Program data cited by project code; public status not explicitly stated  
  > "ALMA data: 2016.1.00324.L." (Acknowledgments)
- Products in archive: _not stated_
- Missing: FINDCLUMPS code and settings
- Missing: Custom MCMC code
- Missing: Line candidate catalog and fidelity fit parameters
- Data volume (inferred): Large; 85-pointing mosaic over 60 GHz, likely hundreds of GB to TB raw
- Score (inferred): 3/5, Data are an ALMA LP and the recipe is outlined, but the key codes, the catalog, and the inherited excitation/continuum inputs are not given.
- Rediscovery candidate: no, Depends on unreleased custom codes and several inherited analysis products.

## Links

- Method: (cite: decarli19) (3 mm analysis and LF methodology)
- Method: (cite: gonzalezlopez19) (line search and spectrum extraction)
- Companion: (cite: boogaard20) (CO excitation)
- Companion: (cite: magnelli20) (dust-based rho_H2)
- Related: ASPECS
- Related: VLASPECS
- Related: COLDz
- Related: PHIBSS2
- Related: ALMACAL

## Checks

```json
{
 "quotes": 62,
 "quotes_ok": 62,
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
  "facts": 79,
  "stated": 48,
  "rate": 0.608
 },
 "evidence_ok": true
}
```
