# Interstellar Plunging Waves: ALMA Resolves the Physical Structure of Nonstationary MHD Shocks

`2019ApJ...881L..42C` | The Astrophysical Journal Letters 2019 | first author: Cosentino, Giuliana | arXiv: 1908.09743 | DOI: 10.3847/2041-8213/ab38c5

Card schema 1.0 | model claude-sonnet-5-5 | depth full | type observational_alma_primary

## Science

- Fields: milky_way_ism, star_formation, astrochemistry
- Question: Can the internal physical structure of a non-stationary MHD shock be spatially resolved in SiO toward IRDC G034 where the SNR W44 pushes molecular gas into the cloud?  
  > "In this Letter, we report the first images of the internal physical structure of a non-stationary CJ-type shock." (Introduction)
- Target **IRDC G034.77-00.55 (G034)**: coordinates phase centre RA(J2000)=18h56m41.7s, Dec=+1d23m25s  
  > "which is located at 2.9$\,$kpc in a highly dynamical environment between the HII region G034.8-00.7 and the supernova remnant (SNR) W44" (Introduction); "phase centre $\alpha$(J2000)=18$^h$56$^m$41.7$^s$, $\delta$(J2000)=1$^{\circ}$23$^{\prime}$25$^{\prime\prime}$" (2 Observations); z/distance 2.9 kpc  
  > "which is located at 2.9$\,$kpc in a highly dynamical environment between the HII region G034.8-00.7 and the supernova remnant (SNR) W44" (Introduction); "phase centre $\alpha$(J2000)=18$^h$56$^m$41.7$^s$, $\delta$(J2000)=1$^{\circ}$23$^{\prime}$25$^{\prime\prime}$" (2 Observations); distance from _not stated_

## Data provenance

- ALMA projects: 2016.1.01363.S
- bands: Band 3  
  > "We used ALMA Band 3 during Cycle 4 (P.I. I. Jimenez-Serra)" (2 Observations)
- frequencies and spectral setup: SiO J=2-1 at 86.85 GHz, 58.594 MHz bandwidth, dual polarization  
  > "using a spectral bandwidth of 58.594$\,$MHz" (2 Observations)
- continuum bandwidth: _not stated_
- arrays: ACA (11 antennas) plus 45 antennas of the 12m array  
  > "ALMA Compact Array (11 antennas) plus 45 antennas of the 12m-array (baseline 15$\,$m-331$\,$m; uv distance 4.3-9.6$\,$k$\lambda$)" (2 Observations)
- configurations: _not stated_
- baselines: _not stated_
- angular resolution: 3.5'' x 2.5'', PA=84.27 deg  
  > "synthesised beam of 3.5$''$$\times$2.5$''$, PA= 84.27$^{\circ}$" (2 Observations)
- max recoverable scale: _not stated_
- sensitivity: 10 mJy/beam (line cube); continuum 1 sigma = 66 uJy/beam  
  > "noise level 10$\,$mJy$\,$beam$^{-1}$" (2 Observations)
- time on source: _not stated_
- observing dates: _not stated_
- pi or archival as stated: Cycle 4, PI I. Jimenez-Serra  
  > "We used ALMA Band 3 during Cycle 4 (P.I. I. Jimenez-Serra)" (2 Observations)
- Line: SiO J=2-1 (86.85 GHz)
- Line: C18O J=1-0 and J=2-1 (IRAM 30m) (109.78 GHz and 219.56 GHz)
- Other facility **IRAM 30m**: C18O(1-0) and (2-1) OTF maps; also SiO comparison spectra for missing flux  
  > "were carried out with the IRAM 30m telescope in July 2012" (2 Observations)
- External data: Visual extinction map (Av=20 mag level)  
  > "superimposed on the A$_{\rm v}$=20$\,$mag visual extinction level of the cloud (cite: kainulainen2013)" (3.1) [from (cite: kainulainen2013)]
- External data: Dust opacity at 3 mm extrapolated, 0.0237 m2/kg  
  > "Dust opacity at 3$\,$mm is extrapolated to k$_\nu$=0.0237$\,$m$^2$$\,$kg$^{-1}$ (cite: hennings1994)" (3.3 3 mm Continuum Emission) [from (cite: hennings1994)]
- External data: Kinetic temperature 15 K  
  > "We assume kinetic temperature of 15$\,$K (cite: pillai2007)" (3.2) [from (cite: pillai2007)]
- Simulation/model as data: Grid of MHD_VODE 1D shock models compared to SiO PV diagrams  
  > "We have run a grid of models with shock speeds between $v_s$=5-30$\,$km s$^{-1}$" (4 Modelling the SiO PV diagrams)

## Processing

### Calibration

- pipeline or manual: Reran original pipeline reduction scripts  
  > "We reproduced the two calibrated datasets by running the original pipeline reduction scripts" (2 Observations)
- casa version: CASA 4.7.2  
  > "CASA version 4.7.2" (2 Observations)
- pipeline version: _not stated_
- archive products used as is: _not stated_
- flux calibrator: _not stated_
- flux scale uncertainty: _not stated_
- self calibration: _not stated_

### Imaging

- task: clean  
  > "We generated the SiO line-only final image using the task *clean*" (2 Observations)
- deconvolver: _not stated_
- weighting robust: Briggs, robust 0.5  
  > "Briggs weighting (robust parameter 0.5)" (2 Observations)
- uv taper: _not stated_
- cell size: _not stated_
- image size: _not stated_
- masking: _not stated_
- multiscale scales: _not stated_
- continuum subtraction: uvcontsub from line-free channels  
  > "used the task *uvcontsub* in CASA version 4.7.2[^1] to subtract the continuum emission previously estimated from line-free channels" (2 Observations)
- line free channels: _not stated_
- primary beam correction: _not stated_
- array combination: concat of the two continuum-subtracted datasets (12m+ACA)  
  > "The two continuum-subtracted datacubes were combined using the task *concat*." (2 Observations)
- smoothing: _not stated_
- final beam: 3.5'' x 2.5'', PA 84.27 deg  
  > "synthesised beam of 3.5$''$$\times$2.5$''$, PA= 84.27$^{\circ}$" (2 Observations)
- final rms: 10 mJy/beam  
  > "noise level 10$\,$mJy$\,$beam$^{-1}$" (2 Observations)

### Inherited from earlier work

- Mass, momentum and energy of SiO emission estimated following Dierickx et al.  
  > "following (cite: dierickx2015), we have estimated the mass (M), linear momentum (P) and kinetic energy (E)" (5.1) [from (cite: dierickx2015)]

### Not stated but needed to reproduce (our reading)

- Line-free channels used for continuum estimation
- Cell size, image size, clean threshold and masks
- Velocity range/method for moment maps and PV cut positions and widths
- Which pipeline version/CASA used for original reductions
- Details of RADEX inputs (SiO collision setup, background) and N(SiO) derivation assumptions (Tex, linewidth)
- Selection of MHD_VODE grid steps and fit criterion for PV models
- Assumptions used for mass/momentum/energy (abundance, inclination)

## Analysis recipe

1. **Image SiO cube**: Rerun pipeline, uvcontsub, concat, clean with Briggs weighting  
  > "The two continuum-subtracted datacubes were combined using the task *concat*." (2 Observations)
   - software: CASA
   - parameter: robust 0.5, 0.1 km/s channels  
  > "velocity resolution 0.1$\,$km s$^{-1}$$\,$($\sim$30 kHz)" (2 Observations)
   - fitting: _not stated_
   - validation: Compared ALMA and IRAM 30m SiO spectra; no significant flux missing  
  > "we find that no significant flux is missing in the 12m+ACA SiO image" (2 Observations)
2. **Moment maps and PV diagrams of SiO**: Integrated intensity (36.6-47.6 km/s), moment 1, PV cuts perpendicular to SiO elongations  
  > "integrated intensity map (black contours; velocity range 36.6$-$47.6 km s$^{-1}$$\,$)" (3.1)
   - fitting: _not stated_
   - validation: _not stated_
3. **Pre/post-shock density from C18O**: RADEX modelling of C18O 1-0 and 2-1 IRAM spectra  
  > "By using the radiative transfer code RADEX (cite: tak2007), we can infer the H$_2$ gas volume density" (3.2)
   - software: RADEX, CLASS/GILDAS
   - assumption: Tkin = 15 K, linewidth 2 km/s  
  > "We assume kinetic temperature of 15$\,$K (cite: pillai2007) and mean linewidth of 2$\,$km s$^{-1}$" (3.2)
   - fitting: _not stated_
   - validation: _not stated_
4. **Upper limit on protostellar envelope mass**: Optically thin dust equation with 3-sigma continuum limit  
  > "we derive a proto-stellar envelope mass $\leq$0.45$\,$M$_{\odot}$." (3.3 3 mm Continuum Emission)
   - parameter: F=0.2 mJy  
  > "We assume $d$=2.9$\,$kpc, T$_{dust}$=15$\,$K, M$_{gas}$/M$_{dust}$=100, and F$_\nu$=0.2$\,$mJy." (3.3 3 mm Continuum Emission)
   - assumption: d=2.9 kpc, Tdust=15 K, gas-to-dust 100  
  > "We assume $d$=2.9$\,$kpc, T$_{dust}$=15$\,$K, M$_{gas}$/M$_{dust}$=100, and F$_\nu$=0.2$\,$mJy." (3.3 3 mm Continuum Emission)
   - fitting: _not stated_
   - validation: _not stated_
5. **Model PV diagrams with MHD shock code**: Grid of 1D time-dependent MHD_VODE models over vs, n(H), zeta, B, with visual comparison to PV North/South  
  > "We have used the 1D MHD shock code MHD$\_$VODE (cite: flowerpineau2015) to reproduce the SiO velocity structure" (4 Modelling the SiO PV diagrams)
   - software: MHD_VODE
   - parameter: vs=5-30 km/s; n(H)=1e4-1e5 cm-3; zeta=1e-17-5e-15 s-1; B=100-1000 uG; T=15 K  
  > "magnetic field strengths B$_{mag}$=100-1000$\,$$\mu$G" (4 Modelling the SiO PV diagrams)
   - fitting: _not stated_
   - validation: _not stated_

## Software

- **CASA** 4.7.2: uvcontsub, concat, clean  
  > "used the task *uvcontsub* in CASA version 4.7.2" (2 Observations)
- **GILDAS/CLASS** : IRAM 30m data cubes  
  > "created using the CLASS software within GILDAS" (2 Observations)
- **RADEX** : C18O radiative transfer, densities  
  > "By using the radiative transfer code RADEX (cite: tak2007)" (3.2)
- **MHD_VODE** : 1D MHD shock models of SiO PV diagrams  
  > "We have used the 1D MHD shock code MHD$\_$VODE (cite: flowerpineau2015)" (4 Modelling the SiO PV diagrams)

## Numeric results

| quantity | value | uncertainty | units | step | quote |
|---|---|---|---|---|---|
| Pre-shock n(H2) | ~1e4 | not stated | cm-3 | 3 | n(H$_2$)$\sim$10$^4$$\,$cm$^{-3}$ |
| Post-shock n(H2) | >1e5 | not stated | cm-3 | 3 | n(H$_2$)$>$10$^5$$\,$cm$^{-3}$ |
| N(SiO) post-shock | 1.6e12 | not stated | cm-2 | 3 | the derived N(SiO) is 1.6$\times$10$^{12}$$\,$cm$^{-2}$ |
| SiO abundance enhancement | >=500 | not stated | dimensionless | 3 | the abundance of SiO has been enhanced by a factor $\geq$500 |
| Protostellar envelope mass upper limit | <=0.45 | not stated | Msun | 4 | we derive a proto-stellar envelope mass $\leq$0.45$\,$M$_{\odot}$. |
| PV North best-fit B and vs | B=850 uG, vs=22.5 km/s, tdyn=16000 yr | not stated | uG, km/s, yr | 5 | B$_{mag}$=850$\,$$\mu$G and t$_{dyn}$=16000$\,$years |
| SiO outflow-like mass | 12.2 | not stated | Msun | 0 | M=12.2$\,$M$_{\odot}$, P$\,$=$\,$18.8$\,$M$_{\odot}$$\,$km s$^{-1}$$\,$and E$\,$=$\,$3.8$\times$10$^{41}$$\,$ergs |

## Qualitative findings

- SiO is in two plane-parallel structures; velocity decelerates in two steps resembling CJ shock  
  > "the deceleration of the gas is occurring in two steps" (3.1)

## Claim tuples

- H: SiO in G034 traces a resolved non-stationary CJ-type MHD shock from W44 interaction | E: ALMA SiO PV diagrams compared to MHD_VODE models | R: Fast ~2-3 km/s drop within <=2.5'' then ~4-5 km/s over 10-20''; North fitted by vs=22.5 km/s, B=850 uG | F: Time-dependent CJ shock resolved; South fit poorer | **supported**
- H: SiO is not caused by protostellar outflows | E: 3 mm continuum limit and outflow energetics | R: Envelope mass <=0.45 Msun; kinetic energy inconsistent with high-mass outflows | F: Unlikely associated with star formation | **supported**

## Reasoning

- Why this data: _not stated_
- Why this method: _not stated_
- Alternative: Protostellar outflows rejected as SiO origin  
  > "It is thus unlikely that SiO in G034 is associated with star formation activity." (5.1)
- How they decided it was enough: _not stated_
- Limitation (authors): MHD_VODE is 1D idealised, lacks shattering; cannot reproduce SiO column or PV South  
  > "We also caution that the MHD$\_$VODE code only provides 1D highly idealised models" (5.2)
- Caveat (inferred, ours): Model fits judged by eye with no quantitative goodness-of-fit or uncertainties
- Caveat (inferred, ours): Single-dish C18O at 12-24'' used to infer densities in ~3'' shock
- Caveat (inferred, ours): Degeneracy among model parameters not explored

## Reproducibility

- Data public (paper): _not stated_
- Products in archive: _not stated_
- Missing: Imaging parameters (cell, size, mask, threshold)
- Missing: PV cut geometry
- Missing: Model selection criterion and full grid
- Data volume (inferred): ~10-50 GB
- Score (inferred): 3/5, Public ALMA data and clear main steps, but imaging details and model-fitting criteria are missing.
- Rediscovery candidate: no, Key result is qualitative/model comparison by eye with incomplete recipe.

## Links

- Method: (cite: flowerpineau2015) (MHD_VODE shock code)
- Method: (cite: tak2007) (RADEX)
- Companion: (cite: cosentino2018) (Earlier SiO/IRAM survey of the cloud)

## Checks

```json
{
 "quotes": 56,
 "quotes_ok": 56,
 "quote_pass_rate": 1.0,
 "quotes_too_long": 0,
 "unsupported_facts": 0,
 "project_codes": 1,
 "codes_not_in_text": [],
 "codes_not_in_obscore": [],
 "obscore_codes_not_in_card": [],
 "codes_printed_but_missing": [],
 "numeric_results": 7,
 "numeric_problems": 0,
 "fill": {
  "facts": 76,
  "stated": 41,
  "rate": 0.539
 },
 "evidence_ok": true
}
```
