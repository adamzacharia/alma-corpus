# Mapping Circumstellar Magnetic Fields of Late-type Evolved Stars with the Goldreich-Kylafis Effect: CARMA Observations at λ1.3 mm of R Crt and R Leo

`2020ApJ...899..152H` | The Astrophysical Journal 2020 | first author: Huang, Ko-Yun | arXiv: 2007.00215 | DOI: 10.3847/1538-4357/aba122

Card schema 1.0 | model claude-sonnet-5-5 | depth light | type multi_facility_alma_minor

## Science

- Fields: evolved_stars
- Question: Can Goldreich-Kylafis linear polarization of thermal CO J=2-1 be detected with CARMA toward R Crt and R Leo, and is it consistent with G-K model predictions for the circumstellar magnetic field?  
  > "In this section we describe numerical modeling to determine if this linear polarization can be ascribed to the G-K effect." (Analysis and Discussion)
- Target **R Crt**: coordinates 11:00:33.85 -18:19:29.85 (J2000)  
  > "| R Crt | 11:00:33.85 | -18:19:29.85 | O-rich$^{(a)}$ | SRb$^{(a)}$ | 160$^{(a)}$ | $236^{(b)}$ |" (Table 1); z/distance 236 pc  
  > "| R Crt | 11:00:33.85 | -18:19:29.85 | O-rich$^{(a)}$ | SRb$^{(a)}$ | 160$^{(a)}$ | $236^{(b)}$ |" (Table 1); distance from Gaia DR2 parallax  
  > "| R Crt | 11:00:33.85 | -18:19:29.85 | O-rich$^{(a)}$ | SRb$^{(a)}$ | 160$^{(a)}$ | $236^{(b)}$ |" (Table 1)
- Target **R Leo**: coordinates 09:47:33.49 +11:25:43.67 (J2000)  
  > "| R Leo | 09:47:33.49 | +11:25:43.67 | O-rich$^{(a)}$ | Mira$^{(a)}$ | 309.95$^{(a)}$ | $95^{(c)}$ |" (Table 1); z/distance 95 pc  
  > "| R Leo | 09:47:33.49 | +11:25:43.67 | O-rich$^{(a)}$ | Mira$^{(a)}$ | 309.95$^{(a)}$ | $95^{(c)}$ |" (Table 1); distance from P-L distance from Matthews et al. 2018  
  > "| R Leo | 09:47:33.49 | +11:25:43.67 | O-rich$^{(a)}$ | Mira$^{(a)}$ | 309.95$^{(a)}$ | $95^{(c)}$ |" (Table 1)

## Data provenance

- ALMA projects: _none stated_
- bands: _not stated_
- frequencies and spectral setup: Narrow windows 62.2 MHz, 191 channels (0.453 and 0.423 km/s); two 489.6 MHz continuum windows  
  > "Both lines were observed in narrow-band (line) spectral windows of bandwidth $\triangle \nu = 62.2$ MHz each sampled over $191$ frequency channels" (Observation)
- continuum bandwidth: _not stated_
- arrays: CARMA E-configuration (not ALMA)  
  > "The observations of R Crt and R Leo were performed in the CARMA E-configuration ($8.5 - 66$ m baseline lengths)." (Observation)
- configurations: _not stated_
- baselines: _not stated_
- angular resolution: 5.73'' x 4.21'' (R Crt), 5.07'' x 3.58'' (R Leo) at 230 GHz  
  > "At $230$ GHz, the beam size is $5.73'' \times 4.21''$ (at PA $=29.7^{\circ}$) for the calibrated R Crt data and $5.07'' \times 3.58''$ (at PA = $80.1^{\circ}$) for the calibrated R Leo data." (Data reduction)
- max recoverable scale: _not stated_
- sensitivity: _not stated_
- time on source: _not stated_
- observing dates: 16 Nov 2014 (R Crt), 11 Nov 2014 (R Leo)  
  > "Two observing runs were performed, on November 16, 2014 and November 11, 2014 respectively, with each run of total duration 3.7 hours." (Observation)
- pi or archival as stated: _not stated_
- Line: CO J=2-1 (230.538 GHz)
- Line: SiO v=1, J=5-4 (215.596 GHz)
- Other facility **CARMA**: Full-Stokes 1.3 mm observations of CO and SiO  
  > "The correlator was configured in full Stokes mode to observe the SiO $v=1, J=5-4$ line in the lower sideband (LSB) and the CO $J = 2-1$ line in the upper sideband (USB)" (Observation)
- Other facility **ALMA calibrator catalogue**: Band 6 flux densities of gain calibrators  
  > "The resulting flux densities were $8.38 \pm 0.39$ Jy (3C279) and $3.04 \pm 0.17$ Jy (OJ287)." (Data reduction)
- External data: CSE parameters for R Leo (Mdot, v_inf, Rc, beta) from Danilovich et al. 2015  
  > "We adopt an inner dust condensation radius $R_{c} \sim 1.6 \times 10^{14}\ \rm{cm}$ from SED modeling (cite: success15)." (CSE parameters) [from (cite: success15)]
- External data: External EVPA values of calibrators from MOJAVE, VLBA-BU-BLAZAR, POLAMI  
  > "Applicable external EVPA values were obtained from the MOJAVE project (cite: majove), the VLBA-BU-BLAZAR program (cite: jorstad16; jorstad17), and the POLAMI project[^6] (cite: agudo_2018; agudo_2018a)." (Polarization and calibration quality assurance) [from (cite: majove); (cite: jorstad17); (cite: agudo_2018)]

## Processing

### Calibration

- pipeline or manual: CADRE (MIRIAD-based) extended for full polarization; MIRIAD xyauto, mfcal, gpcal  
  > "The $\mathtt{CADRE}$ pipeline was extended to support full-polarization reduction." (Data reduction)
- casa version: _not stated_
- pipeline version: _not stated_
- archive products used as is: _not stated_
- flux calibrator: Gain calibrator flux from ALMA Band 6 catalogue: 3C279 8.38±0.39 Jy, OJ287 3.04±0.17 Jy  
  > "The resulting flux densities were $8.38 \pm 0.39$ Jy (3C279) and $3.04 \pm 0.17$ Jy (OJ287)." (Data reduction)
- flux scale uncertainty: _not stated_
- self calibration: _not stated_

### Imaging

- task: MIRIAD invert for IQUV; impol for polarized intensity  
  > "The IQUV images were formed from the fully calibrated visibilities by $\mathtt{MIRIAD}$ task $\mathtt{invert}$ using natural visibility gridding weighting." (Data reduction)
- deconvolver: _not stated_
- weighting robust: natural weighting  
  > "using natural visibility gridding weighting" (Data reduction)
- uv taper: _not stated_
- cell size: _not stated_
- image size: _not stated_
- masking: Masked below 5σ in Stokes I and 4σ in P  
  > "were masked below $5 \sigma$ in Stokes $I$ and $4 \sigma$ in $P$." (Data reduction)
- multiscale scales: _not stated_
- continuum subtraction: _not stated_
- line free channels: _not stated_
- primary beam correction: _not stated_
- array combination: _not stated_
- smoothing: Channels averaged to 1 km/s  
  > "The spectral channels were averaged over 1 km s$^{-1}$ in both the CO and SiO channel maps." (Data reduction)
- final beam: _not stated_
- final rms: _not stated_

### Inherited from earlier work

- G-K modeling code framework  
  > "We use the G-K modeling framework developed independently by (cite: yl10)." (G-K modeling) [from (cite: yl10)]
- CSE temperature and density profile forms  
  > "Following (cite: bowen88) as cited by (cite: cherchneff92), the kinetic temperature dependence on radius is approximated as a power-law" (CSE parameters) [from (cite: bowen88); (cite: cherchneff92)]

### Not stated but needed to reproduce (our reading)

- Magnetic field and G-K code input grids (optical depth range, geometry details) not tabulated
- Exact Stokes I/P noise values per cube used for masking
- Calibrator-specific flagging details
- Image size and cell size

## Analysis recipe

1. **Calibrate full-Stokes CARMA data**: CADRE parallel-hand calibration, then R-L phase and D-term calibration  
  > "The $\mathtt{MIRIAD}$ task $\mathtt{xyauto}$ solves for the R-L phase corrections for all the 10-m antennas using this method" (Data reduction)
   - software: CADRE, MIRIAD
   - parameter: gpcal with options=qusolve  
  > "The $\mathbf{D}_{m}$ terms were solved for using the $\mathtt{MIRIAD}$ task $\mathtt{gpcal}$ with $\mathtt{options=qusolve}$." (Data reduction)
   - fitting: _not stated_
   - validation: Compared calibrator EVPAs with MOJAVE/VLBA-BU/POLAMI; leakage rank correlation with archival data  
  > "The resulting 14-day averaged EVPA for 3C279 thus obtained is $42.88^{\circ} \pm 10.83^{\circ}$" (Polarization and calibration quality assurance)
2. **Image and measure polarization**: invert IQUV, debias P with impol, measure peak P, I, m_l, error-weighted EVPA  
  > "The synthesized maps of linearly polarized intensity $P$ were de-biased (cite: wardle_kronberg_74) using $\mathtt{MIRIAD}$ task $\mathtt{impol}$" (Data reduction)
   - software: MIRIAD
   - fitting: _not stated_
   - validation: _not stated_
3. **Build R Leo CSE model**: Power-law temperature, beta-law velocity, continuity ODE solved for n(r)  
  > "We used the SciPy[^7] package $\mathtt{odeint}$ to solve the differential equation in Equation [\[eq:ode_tosolve\]](#eq:ode_tosolve)" (CSE parameters)
   - software: SciPy
   - parameter: R*=1.4 AU, T*=1800 K, Rc=10.7 AU, v_inf=8.5 km/s, Mdot=1.1e-7 Msun/yr, beta=0-5  
  > "$R_*=1.4\ \rm{AU}$ (cite: debeck10), $T_*=1800\ \rm{K}$, (cite: schoier13), $R_c=10.7\ \rm{AU}$ (cite: success15)" (CSE parameters)
   - assumption: alpha=0.6 temperature exponent; R0~R*  
  > "where the exponent index, $\alpha$, is often adopted to be $0.6$" (CSE parameters)
   - fitting: _not stated_
   - validation: Density ranges compared across literature CO mass-loss models  
  > "these density ranges are broadly consistent." (CSE parameters)
4. **Predict G-K fractional polarization**: Yang & Lai G-K code with mixed 1-D/2-D LVG geometry, optionally with anisotropic radiation from central star  
  > "A mixed LVG velocity gradient geometry (Fig. [8](#fig:COpol_model_LVGs)(iii)) was adopted in the G-K modeling" (Observed linear polarization and the G-K model predictions)
   - software: G-K code of Yang & Lai 2010, LAMDA
   - assumption: Uniform magnetic field and velocity gradient in constant-density slab  
  > "The model used here considers an uniform magnetic field and uniform velocity gradient through the slab of material with constant thickness and density, as a first-order approximation." (G-K modeling)
   - fitting: _not stated_
   - validation: Compared predicted m_l with observed CO polarization  
  > "Our G-K model predicts $m_l \sim 3\%$ (Fig. [7](#fig:COpol_model)) which is consistent with our observational result for the CO emission toward R Crt." (Observed linear polarization and the G-K model predictions)

## Software

- **CADRE** : Calibration pipeline  
  > "CADRE (cite: cadre), MIRIAD (cite: miriad), SciPy (cite: Scipy)" (Software)
- **MIRIAD** : Calibration and imaging  
  > "based on the Multichannel Image Reconstruction, Image Analysis and Display analysis package ($\mathtt{MIRIAD}$)" (Data reduction)
- **SciPy** : ODE solving and correlation statistics  
  > "were computed using SciPy[^5] for both the R Crt and R Leo data" (Polarization and calibration quality assurance)

## Numeric results

| quantity | value | uncertainty | units | step | quote |
|---|---|---|---|---|---|
| CO J=2-1 peak fractional linear polarization, R Crt | 3.13 | 7.2 sigma detection | % | 2 | / R Crt / SiO (J=5-4, v=1) / 12.0 / 0.778 / 4.52 / 17.2 (17.3 $\sigma$) / $-15.4$ / |
| CO J=2-1 peak fractional linear polarization, R Leo | 9.71 | 6.1 sigma detection | % | 2 | / R Leo / SiO (J=5-4, v=1) / -4.0 / 18.67 / 53.98 / 34.6 (317 $\sigma$) / $-1.1$ / |
| CO mean EVPA R Crt | 7.6 | ±1.0 ±10.8 | deg | 2 | / R Crt / $\phi_{B} = 7.6^{\circ}\pm 1.0^{\circ}\pm 10.8^{\circ}$ / CO $(J=2-1)$ / CARMA / This work / \(a\) / |
| CO mean EVPA R Leo | -77.7 | ±1.7 ±11.6 | deg | 2 | / R Leo / $\phi_{B} = -77.7^{\circ}\pm 1.7^{\circ}\pm 11.6^{\circ}$ / CO $(J=2-1)$ / CARMA / This work / \(1\) / |
| SiO maser linear polarization R Crt / R Leo | 17.2 / 34.6 | not stated | % | 2 | We detect linear polarization in the $v=1,\ J=5-4$ SiO maser emission toward R Crt at $m_l \sim 17.2\%$ and R Leo at $m_l\sim 34.6\%$ |
| Continuum R Crt LSB | 14.9 | 2.4 | mJy/beam | 2 | We detect continuum emission toward R Crt of $14.9 \pm 2.4$ mJy/beam in the LSB continuum spectral window |
| SiO circular polarization R Leo | 5.7 | 40.3 sigma | % | 2 | We detect peak fractional circular polarization $m_c \sim 5.7\%$ in the $v=1, J=5-4$ SiO maser line toward R Leo |

## Qualitative findings

- G-K model with anisotropic radiation cannot readily produce m_l > 5%, so R Leo's 9.7% needs additional effects  
  > "we find that a fractional linear polarization exceeding $m_l > 5\%$ cannot readily be generated by our G-K model including anisotropic radiation." (Observed linear polarization and the G-K model predictions)
- No continuum polarization detected  
  > "No continuum polarization was detected toward either R Crt or R Leo" (Results)

## Claim tuples

- H: CO J=2-1 linear polarization in R Crt and R Leo arises from the G-K effect | E: CARMA full-Stokes observations compared with G-K model using a semi-analytic CSE | R: Model predicts ~3%; observed 3.13% (R Crt) and 9.7% (R Leo) | F: Consistent for R Crt; R Leo exceeds the model, so additional effects needed | **partially**
- H: SiO maser lines are linearly and circularly polarized in these stars | E: Stokes maps of v=1 J=5-4 | R: m_l 17-34%; circular only toward R Leo | F: Maser polarization detected, broadly consistent with earlier J=2-1 results | **supported**

## Reasoning

- Why this data: _not stated_
- Why this method: G-K effect traces field morphology at depth, distinct from dust polarization and Zeeman  
  > "The G-K polarization signal also arises from underlying physics that is distinct from the generating mechanisms for continuum dust polarization and the Zeeman effect." (Introduction)
- How they decided it was enough: _not stated_
- Limitation (authors): Observations are sensitivity-limited; interferometric filtering may overestimate m_l  
  > "These observations are profoundly sensitivity-limited compared to modern telescopes such as ALMA" (Conclusions)
- Caveat (inferred, ours): Data are CARMA, not ALMA; ALMA only supplies calibrator fluxes
- Caveat (inferred, ours): G-K model uses slab with uniform field; only R Leo CSE modeled explicitly
- Caveat (inferred, ours): Absolute EVPA systematic error ~11 deg and weak leakage correlation

## Reproducibility

- Data public (paper): CARMA archival data referenced only for a comparison dataset; target data availability not stated  
  > "CARMA project ID: c1217; Observing Block ID: c1217.2D_2303c279.2" (Polarization and calibration quality assurance)
- Products in archive: _not stated_
- Missing: Target CARMA project IDs
- Missing: G-K code access (cited proceedings)
- Missing: Image sizes, cell sizes
- Data volume (inferred): small (<~10 GB, two 3.7-hr CARMA tracks)
- Score (inferred): 2/5, Non-ALMA data with no project IDs and an obscure G-K code.
- Rediscovery candidate: no, CARMA data not stated public; ALMA minor.

## Links

- Method: Hull & Plambeck 2015 (cite: hullplambeck) (CARMA polarimetry calibration)
- Method: Yang & Lai 2010 (cite: yl10) (G-K numerical code)
- Related: CARMA
- Related: MOJAVE
- Related: VLBA-BU-BLAZAR
- Related: POLAMI

## Checks

```json
{
 "quotes": 55,
 "quotes_ok": 55,
 "quote_pass_rate": 1.0,
 "quotes_too_long": 0,
 "unsupported_facts": 0,
 "project_codes": 0,
 "codes_not_in_text": [],
 "codes_not_in_obscore": [],
 "obscore_codes_not_in_card": [],
 "codes_printed_but_missing": [
  "2011.0.00001.CAL"
 ],
 "numeric_results": 7,
 "numeric_problems": 0,
 "fill": {
  "facts": 74,
  "stated": 42,
  "rate": 0.568
 },
 "evidence_ok": true
}
```
