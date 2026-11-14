# ORion Alma New GEneration Survey (ORANGES). I. Dust continuum and free-free emission of OMC-2/3 filament protostars

`2021A&A...653A.117B` | Astronomy and Astrophysics 2021 | first author: Bouvier, M. | arXiv: 2107.10743 | DOI: 10.1051/0004-6361/202141157

Card schema 1.0 | model claude-sonnet-5-5 | depth full | type observational_alma_primary

## Science

- Fields: star_formation
- Question: Are the small-scale dust properties and evolutionary status of solar-type protostars in the OMC-2/3 filament affected by nearby HII regions and UV illumination?  
  > "we aim to understand whether there is an evolutionary trend along the filament and whether the nearby massive star can affect the dust properties of the protostars." (Introduction)
- Target **OMC-2/3 filament protostars (CSO33, FIR6c, FIR2, FIR1a, MMS9, MMS5, MMS2, CSO3, SIMBA-a)**: coordinates field centres e.g. CSO33 05:35:19.5 -05:15:35.0 (J2000), Table 1  
  > "The OMC-2/3 filament is located at a distance of (393 $\pm$ 25) pc from the Sun (cite: grosschedl2018)" (3.2 Source sample); "| CSO33   | 0.32 $\times$ 0.27 | -77            | 44               | 05:35:19.5   | $-$05:15:35.0   |" (Table 1); z/distance 393 ± 25 pc  
  > "The OMC-2/3 filament is located at a distance of (393 $\pm$ 25) pc from the Sun (cite: grosschedl2018)" (3.2 Source sample); "| CSO33   | 0.32 $\times$ 0.27 | -77            | 44               | 05:35:19.5   | $-$05:15:35.0   |" (Table 1); distance from Grosschedl et al. 2018  
  > "The OMC-2/3 filament is located at a distance of (393 $\pm$ 25) pc from the Sun (cite: grosschedl2018)" (3.2 Source sample); "| CSO33   | 0.32 $\times$ 0.27 | -77            | 44               | 05:35:19.5   | $-$05:15:35.0   |" (Table 1)

## Data provenance

- ALMA projects: 2016.1.00376.S, 2015.1.00041.S
- bands: Band 6 (~250 GHz, 246.2 GHz); archival 333 GHz ALMA and 32.9 GHz VLA  
  > "in Band 6 ($\sim 250$ GHz)" (4.1 ALMA observations at 246.2 GHz)
- frequencies and spectral setup: continuum spw ~2 GHz bandwidth centred at 246.2 GHz, 0.977 MHz resolution  
  > "the continuum spectral window was centred at 246.2 GHz and with a spectral resolution of 0.977 MHz ($\sim$ 1.2 km/s)" (4.1 ALMA observations at 246.2 GHz)
- continuum bandwidth: _not stated_
- arrays: 12m array, 42 antennas  
  > "A total of 42 antennas of the 12m array were used" (4.1 ALMA observations at 246.2 GHz)
- configurations: _not stated_
- baselines: 18.6 m - 1100 m (246.2 GHz); 15-3700 m ALMA 333 GHz; 0.68-36.4 km VLA  
  > "a baseline length range of 18.6m - 1100m" (4.1 ALMA observations at 246.2 GHz)
- angular resolution: 0.25'' (~100 au); beams 0.32x0.27''  
  > "Thanks to the achieved angular resolution of 0.25$''$ ($\sim 100$ au)" (5.1 Maps)
- max recoverable scale: ~9'' (3500 au) at 246.2 GHz  
  > "Whilst the MRS of our ALMA observations is $\sim 9''$ (3500 au)" (5.1 Maps)
- sensitivity: rms 44-80 uJy/beam at 246.2 GHz  
  > "| MMS5    | 0.32 $\times$ 0.28 | -76            | 80               | 05:35:22.5   | $-$05:01:15.0   |" (Table 1)
- time on source: ~19 min per source  
  > "The integration time on source is $\sim$ 19 min for each source." (4.1 ALMA observations at 246.2 GHz)
- observing dates: October 27-29, 2016 (Cycle 4)  
  > "performed on October 27–29, 2016, during Cycle 4" (4.1 ALMA observations at 246.2 GHz)
- pi or archival as stated: _not stated_
- Line: C18O J=2-1 (not stated)
- Other facility **VANDAM ALMA 333 GHz**: archival 0.87 mm continuum images  
  > "we used archival data from the VANDAM Survey (cite: tobin2020) at 333 GHz (0.87mm) from ALMA" (4.2 Archival data at 333 and 32.9 GHz)
- Other facility **VANDAM VLA 32.9 GHz**: archival 9 mm A-configuration continuum images  
  > "we used the data at 32.9 GHz (9mm) from the VLA observations" (4.2 Archival data at 333 and 32.9 GHz)
- External data: 333 GHz and 32.9 GHz cleaned images (robust=2) from Harvard Dataverse  
  > "We used the *robust*=2 (equivalent to natural weighting) cleaned images, for both the ALMA and the VLA data." (4.2 Archival data at 333 and 32.9 GHz) [from (cite: tobin2019a; tobin2019b)]
- External data: Deconvolved source sizes for sources with point-source or unsatisfactory fits  
  > "We thus used the deconvolved sizes given in (cite: tobin2020)." (5.3 Specific cases) [from (cite: tobin2020)]
- External data: HOPS Lbol, Tbol, Menv and classifications  
  > "HOPS provided estimates of the sources evolutionary classification based on their bolometric luminosity, $L_{\text{bol}}$" (3.3 Previous continuum studies on the sample sources) [from (cite: megeath2012; fischer2013; furlan2016)]

## Processing

### Calibration

- pipeline or manual: CASA used for calibration  
  > "We used the Common Astronomy Software Application (CASA; (cite: mccmullin2007)) for the data calibration." (4.1 ALMA observations at 246.2 GHz)
- casa version: _not stated_
- pipeline version: _not stated_
- archive products used as is: _not stated_
- flux calibrator: J0510+1800 and J0522-3627 (band-pass and flux)  
  > "The band-pass and flux calibrators used were J0510+1800 and J0522-3627" (4.1 ALMA observations at 246.2 GHz)
- flux scale uncertainty: better than 10%  
  > "The flux calibration error is estimated to be better than 10%." (4.1 ALMA observations at 246.2 GHz)
- self calibration: phase self-cal for S/N>100 sources, three rounds, solints 300-60 s  
  > "We applied three successive rounds of calibration with solution intervals in the range 300-60s." (4.1 ALMA observations at 246.2 GHz)

### Imaging

- task: CLEAN in GILDAS MAPPING  
  > "We then exported the calibrated visibility tables to the GILDAS [^4] format, and performed the imaging in MAPPING." (4.1 ALMA observations at 246.2 GHz)
- deconvolver: _not stated_
- weighting robust: natural weighting  
  > "We produced the continuum images using natural weighting (via the CLEAN procedure)." (4.1 ALMA observations at 246.2 GHz)
- uv taper: _not stated_
- cell size: _not stated_
- image size: _not stated_
- masking: _not stated_
- multiscale scales: _not stated_
- continuum subtraction: continuum from averaging line-free channels in the visibility plane  
  > "We produced continuum images by averaging line-free channels in the visibility plane." (4.1 ALMA observations at 246.2 GHz)
- line free channels: _not stated_
- primary beam correction: maps not PB corrected; correction applied for flux measurement; PB 25.6''  
  > "The maps shown in this paper are not corrected for the primary beam, but we took into account the correction to measure the flux densities." (4.1 ALMA observations at 246.2 GHz)
- array combination: _not stated_
- smoothing: _not stated_
- final beam: 0.32x0.27'' typical  
  > "| FIR2    | 0.32 $\times$ 0.27 | -76            | 54               | 05:35:24.4   | $-$05:08:34.0   |" (Table 1)
- final rms: _not stated_

### Inherited from earlier work

- Further observational details of VANDAM data  
  > "More observational details are given in (cite: tobin2020)." (4.2 Archival data at 333 and 32.9 GHz) [from (cite: tobin2020)]
- Dust opacity kappa0=0.9 cm2/g at 230 GHz  
  > "$\kappa_0=0.9$ cm$^2$g$^{-1}$ is the emissivity of the dust grain at the reference frequency of $\nu_0=230$ GHz (cite: OH94)" (6.2 Method) [from (cite: OH94)]
- Trad formula for optically thick spherical envelope  
  > "provides a good approximate value of $T_{\text{rad}}$ (cite: ceccarelli2000a)" (6.2 Step 6) [from (cite: ceccarelli2000a)]

### Not stated but needed to reproduce (our reading)

- Solution intervals and number of channels per source for self-calibration
- Line-free channel selection for continuum
- CLEAN mask, threshold, cell and image size
- CASA version
- Exact fit starting parameters and which sources use point vs Gaussian in uv_fit
- Weighting scheme for averaging beta and N_H2 across frequencies
- Arbitrary sizes chosen for FIR1a-a and CSO33-b beyond Table values

## Analysis recipe

1. **Fit source sizes and measure flux densities**: uv-plane fit with point source or 2D Gaussian; size convolved with each beam, flux measured in image plane in that ellipse  
  > "We used the ORANGES data set to perform a fit of the 16 sources in the visibility plane with the task *uv_fit* in MAPPING from the GILDAS package." (5.2 Flux densities)
   - software: GILDAS MAPPING
   - parameter: theta_obs = sqrt(theta_beam^2 + theta_source^2); 10% calibration error in flux  
  > "The flux density uncertainties include a 10% amplitude calibration error." (5.2 Flux densities)
   - fitting: _not stated_
   - validation: uv-fit and image-plane fluxes consistent within 30% at 246.2 GHz (up to 50% for some)  
  > "consistent within  30% at 246.2 GHz" (5.2 Flux densities)
2. **Derive beta and T_SED, tau, N_H2, mass, free-free fraction**: SED method: F=B(Td)(1-exp(-tau))Omega with beta from flux ratios for Td 10-200 K; free-free identified when beta_333-246.2 exceeds beta with 32.9 GHz  
  > "we derived the indexes for $T_{\text{SED}}$ ranging from 10 to 200 K, with steps of 10 K between 10 and 100 K and steps of 20 K between 100 and 200 K" (6.2 Step 1)
   - parameter: beta constrained to 0-2 to bound T_SED  
  > "we took into account that $\beta$ should range between 0 and 2" (6.3 T_SED)
   - assumption: mu=2.8, dust-to-gas R=0.01, kappa0=0.9 cm2/g at 230 GHz, d=393 pc, no free-free at 246.2/333 GHz  
  > "R=0.01 is the mass dust-to-gas ratio" (6.2 Method)
   - fitting: analytic inversion over temperature grid; error propagation  
  > "we use error propagation." (11.2 Derivation of uncertainties)
   - validation: Model SEDs overplotted on measured fluxes as self-consistency check  
  > "as a self-consistency check, we added the latter on the dust SED plots." (6.2 Step 7)
3. **Compute Trad and compare with Tbol**: Trad = 101 K (Lbol/10Lsun)^1/4 (r/50 au)^-1/2 for single sources  
  > "$$\begin{equation}
\label{eq:Trad}
    T_{\text{rad}}=101\ \text{K}\left(\frac{L_{\text{bol}}}{10\text{\,L$_\odot$}}\right)^{1/4}\left(\frac{r}{50 \ \text{au}}\right)^{-1/2}" (6.2 Step 6)
   - fitting: _not stated_
   - validation: _not stated_
4. **Reassess evolutionary classification and test environment dependence**: Combine beta, Td/Tbol, outflow, radio continuum criteria; Pearson correlations vs filament position  
  > "we propose here to determine the source’s evolutionary stage, using the criteria summarised in Table [\ref{tab:criteria}]" (7.3 Evolutionary status)
   - fitting: _not stated_
   - validation: _not stated_

## Software

- **CASA** : data calibration  
  > "We used the Common Astronomy Software Application (CASA; (cite: mccmullin2007)) for the data calibration." (4.1 ALMA observations at 246.2 GHz)
- **GILDAS MAPPING** : imaging, CLEAN, uv_fit, flux measurement  
  > "performed the imaging in MAPPING" (4.1 ALMA observations at 246.2 GHz)

## Numeric results

| quantity | value | uncertainty | units | step | quote |
|---|---|---|---|---|---|
| Number of sources detected / analysed | 28 detected; 16 analysed | not stated | sources | 1 | In total, we detected 28 sources, of which 18 are located inside the primary beam |
| Free-free emission sources | 5 of 16 (~31%) | not stated | sources | 2 | We clearly found evidence of free-free emission at 32.9 GHz towards 5 out of 16 sources |
| Sources with beta<1 | 9/16 | not stated | sources | 2 | The majority of the sources (9/16) have a dust emissivity spectral index $< 1$. |
| Free-free fraction at 32.9 GHz | 47-100% in free-free sources; <=24% otherwise | not stated | % | 2 | the derived free-free emission ranges between 47% and 100% |
| Envelope+disk mass range | 2e-4 to 0.1 | not stated | Msun | 2 | the derived (envelope + disk) masses range between $2\times10^{-4}$ M$_\odot$ and 0.1 M$_\odot$ |
| Multiplicity fraction | 67 | 33% | % | 1 | which is 67% of the source sample (with a statistical error of 33%) |
| Pearson coefficient beta vs free-free % | 0.81 | not stated | dimensionless | 4 | with a Pearson correlation coefficient of 0.81 (corresponding to a probability of 66%) |

## Qualitative findings

- Dust properties show no dependence on position in filament, implying near-simultaneous star formation along it  
  > "This would tend to suggest an almost simultaneous star formation along the OMC-2/3 filament" (7.4 Environment influence)

## Claim tuples

- H: Is free-free emission present and does it contaminate dust SED at cm wavelengths? | E: Compared beta between 333, 246.2 and 32.9 GHz | R: 5 of 16 sources show cm excess | F: Free-free emission is present in a minority of sources | **supported**
- H: Do protostar dust properties depend on position in filament / UV illumination? | E: Compared beta, Td, mass, FF with filament position | R: No correlation of beta or mass with position; temperature inconclusive | F: Small-scale dust properties not affected by HII regions | **partially**
- H: Are previous evolutionary classifications correct? | E: Combine beta, T, outflow and radio criteria | R: Ten confirmed, others modified | F: Six Class 0, four Class I, one Class II, one Class II/background, four undecided | **supported**

## Reasoning

- Why this data: _not stated_
- Why this method: _not stated_
- How they decided it was enough: _not stated_
- Limitation (authors): Low statistics and poorly constrained temperatures hamper strong conclusions  
  > "the low statistics and relatively large errors in the parameters of the sources where the dust temperature is not well constrained hamper very strong conclusions" (7.4 Environment influence)
- Caveat (inferred, ours): Mass depends on opacity uncertain by ~10x
- Caveat (inferred, ours): Arbitrary source sizes for FIR1a-a and CSO33-b
- Caveat (inferred, ours): Different resolutions and MRS between datasets, and the beta-T degeneracy
- Caveat (inferred, ours): Correlation significance is low

## Reproducibility

- Data public (paper): Archival VANDAM images from Harvard Dataverse; ALMA ORANGES from project 2016.1.00376.S  
  > "Both sets of archival data are taken from the Harvard Dataverse[^5] (cite: tobin2019a; tobin2019b)." (4.2 Archival data at 333 and 32.9 GHz)
- Products in archive: _not stated_
- Missing: Self-calibration solints per source
- Missing: CLEAN parameters
- Missing: Exact adopted sizes
- Missing: Weighting details
- Data volume (inferred): ~50-100 GB raw for 9 fields; archival images small
- Score (inferred): 3/5, Data public and equations given, but imaging/self-cal parameters and some sizes are arbitrary or unstated.
- Rediscovery candidate: yes, Public data, analytic method with stated assumptions, numeric tables of results.

## Links

- Method: (cite: tobin2020) (VANDAM data and source sizes)
- Companion: (cite: bouvier2020) (single-dish precursor study of same sources)
- Related: ORANGES
- Related: VANDAM
- Related: HOPS

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
 "codes_not_in_obscore": [],
 "obscore_codes_not_in_card": [],
 "codes_printed_but_missing": [],
 "numeric_results": 7,
 "numeric_problems": 0,
 "fill": {
  "facts": 70,
  "stated": 45,
  "rate": 0.643
 },
 "evidence_ok": true
}
```
