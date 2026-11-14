# High-z [OI] emission lines: COLDSIM simulations and ALMA observations

`2026A&A...705A..39P` | Astronomy and Astrophysics 2026 | first author: Parente, M. | arXiv: 2510.26885 | DOI: 10.1051/0004-6361/202557033

Card schema 1.0 | model claude-sonnet-5-5 | depth light | type theory_or_simulation_compared_to_alma

## Science

- Fields: high_z_galaxies, milky_way_ism
- Question: How do [OI] 63 and 145 micron emission lines in high-z galaxies relate to SFR and H2 content, and how much does foreground self-absorption of [OI]63 matter?  
  > "We investigate the connection between [OI] emission lines and key galaxy properties, such as star formation rate (SFR) and H$_2$ content." (abstract)
- Target **A1689-zD1**: coordinates _not stated_; z/distance z = 7.132  
  > "A1689$-$zD1 | $7.132$" (Table 1); distance from _not stated_
- Target **SPT0346-52**: coordinates _not stated_; z/distance z = 5.656  
  > "SPT0346$-$52 | $5.656$" (Table 1); distance from _not stated_
- Target **J204314-214439**: coordinates _not stated_; z/distance z = 4.680  
  > "multiple images in which we also detect [OI] and [CII] emission at $z=4.680$" (3.1 New z>4.7 observations); distance from _not stated_
- Target **J2054-0005**: coordinates _not stated_; z/distance z = 6.038  
  > "J2054$-$0005 | $6.038$" (Table 1); distance from _not stated_

## Data provenance

- ALMA projects: 2023.1.01450.S, 2021.1.00265.S
- bands: _not stated_
- frequencies and spectral setup: _not stated_
- continuum bandwidth: _not stated_
- arrays: _not stated_
- configurations: _not stated_
- baselines: _not stated_
- angular resolution: [CII] ACA map 7.3x5.2 arcsec2; continuum map 0.75x0.65 arcsec2; [OI] beams 0.75-1.41 arcsec (Table 2)  
  > "angular resolution 7.3$\times$5.2 arcsec$^2$" (3.1 New z>4.7 observations)
- max recoverable scale: _not stated_
- sensitivity: _not stated_
- time on source: _not stated_
- observing dates: _not stated_
- pi or archival as stated: Archival; 2023.1.01450.S (P.I. C. Ferkinhoff), 2021.1.00265.S (P.I. D. Riechers)  
  > "ADS/JAO.ALMA#2023.1.01450.S (P.I. C. Ferkinhoff) and ADS/JAO.ALMA#2021.1.00265.S (P.I. D. Riechers)" (Acknowledgements)
- Line: [OI] 3P0-3P1 (145.5 um)
- Line: [CII] 158 um (not stated)
- External data: Compilation of FIR line observations (0<=z<~6.5)  
  > "We consider the compilation of (cite: RP23) and references therein" (3.2 Existing literature) [from (cite: RP23)]
- External data: J2054-0005 [OI]63 detection  
  > "We include the recent ${\rm [OI]}\, 63 {\mu \rm{m}}$ detection in the bright QSO J2054-0005 at $z=6.04$ by (cite: Ishii2025)." (3.2 Existing literature) [from (cite: Ishii2025)]
- External data: REBELS [OI]145 detections  
  > "for which ${\rm [OI]}\, 145 {\mu \rm{m}}$ were reported by (cite: Fudamoto25)" (3.2 Existing literature) [from (cite: Fudamoto25)]
- Simulation/model as data: COLDSIM box 50 Mpc/h, 2x1000^3 particles, post-processed with DESPOTIC  
  > "The box has a comoving size of $50\,{\rm Mpc} / h$ initialized with $2 \times 1000^3$ particles." (2.1 COLDSIM cosmological simulations)

## Processing

### Calibration

- pipeline or manual: Standard ALMA observatory calibration with default calibrators  
  > "Visibilities were calibrated using the standard calibration provided by the ALMA observatory and the default phase, bandpass and flux calibrators." (8 ALMA maps)
- casa version: _not stated_
- pipeline version: _not stated_
- archive products used as is: _not stated_
- flux calibrator: _not stated_
- flux scale uncertainty: _not stated_
- self calibration: _not stated_

### Imaging

- task: CASA tclean  
  > "A continuum-subtracted datacube was created using CASA task $tclean$" (8 ALMA maps)
- deconvolver: hogbom  
  > "with the $hogbom$ cleaning algorithm in non-interactive mode, a threshold equal to two times the rms sensitivity" (8 ALMA maps)
- weighting robust: natural  
  > "a natural weighting of the visibilities" (8 ALMA maps)
- uv taper: _not stated_
- cell size: _not stated_
- image size: _not stated_
- masking: _not stated_
- multiscale scales: _not stated_
- continuum subtraction: uv-plane first-order polynomial fit  
  > "performed a fit in the $uv$ plane to channels with $|v|>700$ km s$^{-1}$, using a first-order polynomial continuum" (8 ALMA maps)
- line free channels: |v|>700 km/s  
  > "channels with $|v|>700$ km s$^{-1}$" (8 ALMA maps)
- primary beam correction: _not stated_
- array combination: _not stated_
- smoothing: _not stated_
- final beam: _not stated_
- final rms: _not stated_

### Inherited from earlier work

- DESPOTIC parameters not specified adopted from earlier papers  
  > "from which we adopt parameters not explicitly specified here (see their Table 1)" (2.2.1 DESPOTIC set-up) [from (cite: Narayanan2017); (cite: Garcia2024)]
- IR modified blackbody fit approach, Td=37 K, beta=1.70  
  > "following the approach in (cite: Tripodi24), by assuming a dust temperature of $T_{\rm d}=37 \, {\rm K}$ and $\beta=1.70$ (cite: Zavala2015)" (3.1 New z>4.7 observations) [from (cite: Tripodi24); (cite: Zavala2015)]

### Not stated but needed to reproduce (our reading)

- Spectral windows and channel ranges used for moment-0 integration
- Gaussian fit details and aperture for flux measurement
- Line-integration velocity limits
- Magnification values for lens sources and sources of each literature value beyond table footnotes
- Details of galaxy sample selection and DESPOTIC grid for training
- Simulation initial conditions/code access

## Analysis recipe

1. **Measure [OI]145 fluxes from archival ALMA data**: Continuum subtraction in uv, tclean cube, moment-0, 2D Gaussian fit  
  > "Velocity-integrated line intensities were measured from 2D Gaussian fit of the 0$^{th}$ moment maps" (8 ALMA maps)
   - software: CASA
   - parameter: 30 km/s channel width  
  > "We adopted a 30 km s$^{-1}$ channel width." (8 ALMA maps)
   - fitting: _not stated_
   - validation: Compared with Fudamoto25 flux for A1689-zD1: consistent  
  > "We measure a consistent ${\rm [OI]}\, 145 {\mu \rm{m}}$ flux." (3.1 New z>4.7 observations)
2. **Model line luminosities with DESPOTIC and Random Forest**: DESPOTIC on ~1e5 gas particles, RF regressor predicts remaining particles  
  > "We run DESPOTIC on a representative subset of gas particles ($\approx 10^5$), randomly selected from galaxies spanning the full range of stellar masses." (2.2.2 Extrapolating results with Machine Learning)
   - software: DESPOTIC, scikit-learn
   - parameter: RandomForestRegressor, 200 trees, 80/20 train/test split  
  > "with $200$ estimators (trees), and no maximum tree depth constraint." (2.2.2 Extrapolating results with Machine Learning)
   - assumption: Uniform spherical clouds, 40 shells; GOW chemistry; CR rate from depletion time  
  > "Clouds (i.e., particles) are treated as spheres of uniform density $n_{\rm H}$ divided into $N_{\rm zones}=40$ concentric shells" (2.2.1 DESPOTIC set-up)
   - fitting: _not stated_
   - validation: R^2 ~0.996 on test set  
  > "For the model presented here $R^2 \approx 0.996$." (7 RF accuracy)
3. **Apply foreground [OI]63 self-absorption**: Sum OI column density of velocity-overlapping particles in cylinder; attenuate by (1-exp(-tau))/tau  
  > "The line intensity is then attenuated by a factor of $(1-e^{-\tau_{\rm fore}})/\tau_{\rm fore}$." (2.2.3 self-absorption)
   - assumption: Absorbing gas cold (Tex<~50 K), only ground state populated  
  > "which is assumed to be cold ($T_{\rm ex} \lesssim 50 \, {\rm K}$), such that only the ground state is significantly populated" (4.1 Predictions of self-absorption)
   - fitting: _not stated_
   - validation: Compared with empirical 2-4 correction factors and observed line ratios  
  > "our model yields attenuation factors that are broadly consistent with the empirically adopted corrections of $2-4$" (4.1 Predictions of self-absorption)
4. **Fit scaling relations and compare with observations**: Linear fits in log space of L_[OI] vs SFR etc.; compare with literature and new data  
  > "The extrapolation is obtained by fitting our results with the relation" (4.3 Scaling relations)
   - assumption: SFR from IR luminosity with 1.73e-10 Msun/yr/Lsun (Salpeter); H2 from [CII] conversion  
  > "SFRs are inferred from IR luminosities using the conversion coefficient $1.73 \times 10^{-10} \, \rm M_\odot \, {\rm yr^{-1}} / L_\odot$" (3 Observational dataset)
   - fitting: _not stated_
   - validation: _not stated_

## Software

- **CASA** : tclean imaging of ALMA/ACA data  
  > "A continuum-subtracted datacube was created using CASA task $tclean$" (8 ALMA maps)
- **DESPOTIC** : Post-processing of cloud thermal/chemical/line emission  
  > "Line luminosities are obtained by coupling the output of our simulation with DESPOTIC" (2.2.1 DESPOTIC set-up)
- **scikit-learn** : RandomForestRegressor  
  > "We use the `RandomForestRegressor` from the `scikit-learn` Python library" (2.2.2 Extrapolating results with Machine Learning)
- **P-GADGET3** : Cosmological hydrodynamic simulations  
  > "carried out with an extended version of the P-GADGET3 code" (2.1 COLDSIM cosmological simulations)

## Numeric results

| quantity | value | uncertainty | units | step | quote |
|---|---|---|---|---|---|
| [OI]145 flux A1689-zD1 | 0.567 | 0.058 | Jy km/s | 1 | A1689$-$zD1 / 1.41$\times$1.18 / 0.22 / 0.567$\pm$ 0.058 |
| [OI]145 flux SPT0346-52 | 7.28 | 0.70 | Jy km/s | 1 | SPT0346$-$52 / 1.10$\times0.65$ / 0.45 / $7.28 \pm 0.70$ |
| [OI]145 flux J204314-214439 | 3.28 | 0.30 | Jy km/s | 1 | J204314$-$214439 / 0.75$\times$0.65 / 0.42 / $3.28\pm0.30$ |
| [OI]145 flux J2054-0005 | 0.847 | 0.028 | Jy km/s | 1 | J2054$-$0005 / 1.18$\times$0.96 / 0.23 / 0.847$\pm$0.028 |
| [CII] flux J204314-214439 (ACA) | 25.62 | 1.07 | Jy km/s | 1 | $S_{\rm [CII]}=25.62\pm1.07$ Jy km s$^{-1}$ |
| 362.7 GHz continuum J204314-214439 | 24.47 | 1.17 | mJy | 1 | we measure $S_{\rm 3.7}=24.47\pm1.17$ mJy |
| L_[OI]63-SFR fit (a,b) | (0.76, 7.11) | not stated | dimensionless | 4 | $(a_{{\rm [OI]}\, 63 {\mu \rm{m}}}, b_{{\rm [OI]}\, 63 {\mu \rm{m}}}) = (0.76, 7.11)$ |
| L_[OI]145-SFR fit (a,b) | (0.89, 6.40) | not stated | dimensionless | 4 | $(a_{{\rm [OI]}\, 145 {\mu \rm{m}}}, b_{{\rm [OI]}\, 145 {\mu \rm{m}}}) = (0.89, 6.40)$ |
| [OI]145/[CII] predicted ratio | ≈0.15 | factor <~2 scatter | dimensionless | 4 | Our model predicts a constant ${\rm [OI]}\, 145 {\mu \rm{m}}/ {\rm [CII]}\, 158 {\mu \rm{m}}$ value of $\approx 0.15$ |

## Qualitative findings

- Self-absorption reduces [OI]63 by factor 2-4; needed to match observed line ratios  
  > "modeling self-absorption is essential to reproduce the observed line ratios successfully." (6 Conclusions)

## Claim tuples

- H: Foreground self-absorption of [OI]63 is needed to match high-z line ratios | E: COLDSIM+DESPOTIC with self-absorption model compared to observations | R: [OI]63/[CII]≈1 and [OI]145/[CII]≈0.2 consistent with z>~6 data only with self-absorption | F: Self-absorption is important | **supported**
- H: [OI] lines trace SFR and molecular gas | E: Scaling relations from simulations | R: Both lines correlate with SFR and H2 mass with flattening at high Mstar/metallicity | F: Good tracers in normal star-forming galaxies | **supported**

## Reasoning

- Why this data: _not stated_
- Why this method: _not stated_
- Alternative: Self-absorption model without velocity condition overestimates absorption (~90%) at high SFR  
  > "where the effect is likely overestimated ($\approx 90 \, \%$ of the flux is self-absorbed)" (4.3 Scaling relations)
- How they decided it was enough: _not stated_
- Limitation (authors): Simulation volume cannot sample SFR>~100 Msun/yr systems typical of observed high-z sources  
  > "Due to the limited volume of our simulation, we cannot sample highly star-forming systems ($\gtrsim 100 \, M_\odot/{\rm yr}$)" (4.3 Scaling relations)
- Caveat (inferred, ours): ALMA analysis is minimally documented and uses natural weighting with Gaussian fits only
- Caveat (inferred, ours): Self-absorption model is simplified and not validated against [OI]63 detections beyond one object
- Caveat (inferred, ours): H2 masses from [CII] conversion introduce circularity

## Reproducibility

- Data public (paper): Archival ALMA data  
  > "We include archival data from ALMA project 2023.1.01450.S" (3.1 New z>4.7 observations)
- Products in archive: _not stated_
- Missing: Simulation snapshots and post-processing code
- Missing: Moment-map integration ranges
- Missing: Exact magnification and lens-model values
- Data volume (inferred): ~tens of GB for ALMA/ACA MS; simulation data large
- Score (inferred): 3/5, Theory dominates; ALMA reduction brief but public data
- Rediscovery candidate: no, Main results derive from non-public simulations; only the ALMA flux part is reproducible.

## Links

- Method: (cite: Krumholz2014) (DESPOTIC code)
- Method: (cite: Maio22) (COLDSIM simulations)
- Companion: (cite: Fudamoto25) (Earlier [OI]145 observation of A1689-zD1)
- Related: REBELS

## Checks

```json
{
 "quotes": 55,
 "quotes_ok": 55,
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
  "facts": 82,
  "stated": 39,
  "rate": 0.476
 },
 "evidence_ok": true
}
```
