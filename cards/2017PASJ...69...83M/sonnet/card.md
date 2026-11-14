# ALMA multiline observations toward the central region of NGC 613

`2017PASJ...69...83M` | Publications of the Astronomical Society of Japan 2017 | first author: Miyamoto, Yusuke | arXiv: 1707.06329 | DOI: 10.1093/pasj/psx076

Card schema 1.0 | model claude-sonnet-5-5 | depth full | type observational_alma_primary

## Science

- Fields: nearby_galaxies, agn_and_quasars, astrochemistry
- Question: What are the physical conditions, heating and feedback (jets vs star formation) of molecular gas in the circum-nuclear disk and star-forming ring of NGC 613, using multiline and continuum ALMA observations?  
  > "These results strongly suggest that the jets heat the gas in the CND, in which the feedback prevents star formation." (abstract)
- Target **NGC 613**: coordinates _not stated_; z/distance 17.5 Mpc  
  > "NGC 613 is one of the best targets for studying the jet/outflow activities due to the proximity (17.5 Mpc; (cite: tully1988))" (Observations); distance from Tully 1988  
  > "NGC 613 is one of the best targets for studying the jet/outflow activities due to the proximity (17.5 Mpc; (cite: tully1988))" (Observations)

## Data provenance

- ALMA projects: 2013.1.01329.S
- bands: Band 3 and Band 7  
  > "NGC 613 was observed through the ALMA using Bands 3 and 7 receivers" (Observations)
- frequencies and spectral setup: Band 3: 3 LSB windows (SiO, HCN, HCO+ 1-0), 2 USB (CS 2-1, 100 GHz continuum); Band 7: 2 LSB (CO 3-2, CS 7-6), 2 USB (HCN 4-3, HCO+ 4-3)  
  > "The correlators for Band 7 were configured to set two spectral windows in the lower sideband to cover CO(3–2)" (Observations)
- continuum bandwidth: _not stated_
- arrays: 12-m array, ACA (7 m) and total power  
  > "For both Bands 3 and 7 observations, the 12-m array, Atacama compact array (ACA) and total power array (TP) were used." (Observations)
- configurations: _not stated_
- baselines: up to 1573.0 m (Band 3), 780.7 m (Band 7)  
  > "The baseline lengths extended up to 1573.0 m (524.3 k$\lambda$ at 100 GHz) for Band 3 and 780.7 m (923.9 k$\lambda$ at 355 GHz) for Band 7." (Observations)
- angular resolution: typical beams 0.7'' (Band 3) and 0.4'' (Band 7); 59 and 34 pc  
  > "The typical synthesized beams at Bands 3 and 7 were 0.7$''$ and 0.4$''$," (Observations)
- max recoverable scale: _not stated_
- sensitivity: _not stated_
- time on source: _not stated_
- observing dates: Band 3 June 2014–Sept 2015; Band 7 June 2014–Aug 2015  
  > "Observations at Band 3 were conducted from June 2014 to September 2015." (Observations)
- pi or archival as stated: PI program (Miyamoto), Cycle 2  
  > "as a Cycle 2 early science program (ID 2013.1.01329.S, PI: Miyamoto)" (Observations)
- Line: HCN J=1–0 (88.631847 GHz)
- Line: HCO+ J=1–0 (89.188526 GHz)
- Line: CS J=2–1 (97.980953 GHz)
- Line: CS J=7–6 (342.882857 GHz)
- Line: CO J=3–2 (345.79599 GHz)
- Line: HCN J=4–3 (354.505473 GHz)
- Line: HCO+ J=4–3 (356.734242 GHz)
- Line: SiO J=2–1 (86.846995 GHz)
- Other facility **VLA (project AH231)**: 4.9 GHz archival continuum  
  > "We obtained the 4.9 GHz data (project AH231) from Very Large Array (VLA) archives and reanalyzed them in a standard manner in CASA." (3.1 Continuum emission)
- Other facility **SEST**: CO(1-0) spectrum (literature)  
  > "CO(1–0) observations with SEST, whose angular resolution was $\timeform{44''}$" (Observations)
- Other facility **VLT/SINFONI**: Brγ and H2 maps from Falcón-Barroso et al.  
  > "We thank J. Falcón–Barroso for providing us the data with VLT" (Acknowledgments)
- External data: CO(1-0) SEST spectrum and intensity I_CO10 = 33.7 K km/s  
  > "Figure [14](#fig:co_spe) shows the spectra of CO(3–2) with ALMA TP array and of CO(1–0) with SEST for comparison (cite: elfhag)." (3.3.2) [from (cite: elfhag)]
- External data: Brγ star-formation rates and extinctions in CND and ring  
  > "(cite: falcon) showed lower star-formation rate (SFR) in the CND, 0.02  yr$^{-1}$, than those at the spots in the ring" (4.4.1) [from (cite: falcon)]
- External data: Line spectroscopic data and collisional rates  
  > "All line specifications (spectroscopic data and collisional excitation rates) were taken from the Leiden Atomic and Molecular Database" (4.3) [from (cite: lamda)]

## Processing

### Calibration

- pipeline or manual: _not stated_
- casa version: _not stated_
- pipeline version: _not stated_
- archive products used as is: _not stated_
- flux calibrator: Uranus, Neptune, Ceres, J0334-401 (varies by track)  
  > "| 3    | 7 m $\times$ 9   | 2014 June 5       | J0137-2430          | Uranus          | J0145-2733       | 18 min                       |" (Table 1)
- flux scale uncertainty: _not stated_
- self calibration: _not stated_

### Imaging

- task: CLEAN in CASA  
  > "The imaging was performed using the CLEAN-algorithm in CASA." (Observations)
- deconvolver: _not stated_
- weighting robust: Briggs, robustness 0.5  
  > "CLEAN maps were obtained considering the Briggs weighting mode on the data with a robustness of 0.5." (Observations)
- uv taper: _not stated_
- cell size: 0.05'' per pixel  
  > "The resultant maps were $1500\times1500$ pixels with $0.05\ensuremath{''}$ per pixel." (Observations)
- image size: 1500x1500 pixels  
  > "The resultant maps were $1500\times1500$ pixels with $0.05\ensuremath{''}$ per pixel." (Observations)
- masking: _not stated_
- multiscale scales: _not stated_
- continuum subtraction: continuum determined at emission-free channels and subtracted  
  > "Each line data was then combined after subtracting continuum emission determined at the emission-free channels." (Observations)
- line free channels: _not stated_
- primary beam correction: _not stated_
- array combination: TP combined with 12-m+ACA using Feather in CASA  
  > "By using the Feather algorithm in CASA, the low-resolution image obtained through the TP and high-resolution image obtained through the 12-m and ACA were converted into the gridded visibility plane and combined." (Observations)
- smoothing: Velocity channels rearranged to 10 km/s (2.5 km/s for CO 3-2); maps convolved to 0.72'' for ratio/LTE analysis  
  > "were separately rearranged to be 10 km s$^{-1}$, except for the resolution of 2.5 km s$^{-1}$ in CO(3–2)." (Observations)
- final beam: CO(3-2) 0.44''x0.37'' after feathering; HCN(4-3) 0.43''x0.37''  
  > "$\theta=0.44\ensuremath{''}\times0.37\ensuremath{''}$ ($P.A.=\timeform{45D}$)" (Observations)
- final rms: _not stated_

### Inherited from earlier work

- Submillimeter-HCN diagram used to classify AGN vs starburst  
  > "on the submillimeter-HCN diagram developed by (cite: izumi2016)" (4.2) [from (cite: izumi2016)]
- Rotational diagram method under optically thin LTE  
  > "(cf. (cite: izumi2013))." (4.1 LTE analysis) [from (cite: izumi2013)]
- Molecular mass equation with Xco  
  > "(e.g., (cite: kohno2002), (cite: bolatto2013))" (3.3.2) [from (cite: kohno2002), (cite: bolatto2013)]

### Not stated but needed to reproduce (our reading)

- Line-free channel ranges for continuum subtraction
- Number of CLEAN iterations, thresholds and masks
- Whether archive pipeline calibration or manual scripts were used, and CASA version
- Flux calibration uncertainty
- Rotational diagram fitting details and uncertainties (line-ratio errors, aperture definitions)
- 3DBarolo parameter files
- Band 3 phase center and continuum peak coordinates (missing in text)
- Details of the star-formation rate per spot used for SFE (Table not in text)

## Analysis recipe

1. **Image continuum and lines**: Continuum subtraction, CLEAN imaging, TP feathering for lines  
  > "The imaging was performed using the CLEAN-algorithm in CASA." (Observations)
   - software: CASA
   - parameter: Briggs robust 0.5, 0.05'' pixels, 1500x1500  
  > "The resultant maps were $1500\times1500$ pixels with $0.05\ensuremath{''}$ per pixel." (Observations)
   - fitting: _not stated_
   - validation: _not stated_
2. **Continuum position/size and spectral index**: 2D Gaussian fit to 350 GHz nucleus; spectral index between 4.9 GHz (VLA) and 95 GHz at 0.8'' resolution  
  > "We fit a two-dimensional Gaussian to the nuclear 350 GHz continuum source to derive the position and intrinsic size of the nucleus by using imfit in CASA." (3.1 Continuum emission)
   - software: CASA imfit
   - fitting: _not stated_
   - validation: Compared with 4.9–14.9 GHz index of Hummel & Jörsäter  
  > "The index is slightly flatter than that derived from 4.9 and 14.9 GHz continuum images" (3.1 Continuum emission)
3. **Kinematic parameters**: 3D tilted-ring fit of CO(3-2) cube  
  > "fits a 3D tilted-ring to spectroscopic data cubes" (3.3.1)
   - software: 3DBarolo
   - parameter: 25 annuli of width 0.2'', scale height 150 pc, weighting |cosθ|  
  > "was divided into 25 annuli with a width of $\Delta r=0.2\ensuremath{''}" (3.3.1)
   - assumption: ring has constant circular velocity depending only on r  
  > "assuming that the ring has a constant circular velocity $(V_{\rm rot})$ depending only on $r$" (3.3.1)
   - fitting: 3D tilted-ring model fit  
  > "that fits a 3D tilted-ring to spectroscopic data cubes" (Systemic velocity, position angle, inclination angle, and rotation curve)
   - validation: Compared with RC3 and Burbidge values  
  > "The position and inclination angles are consistent with the result of (cite: rc3)" (3.3.1)
4. **Molecular gas mass and surface density**: CO(3-2) flux converted via R32/10 and Xco  
  > "adopting the CO-to-H$_2$ conversion factor of $X_{\rm CO}=0.5\times10^{20}$ cm$^{-2}$ (K km s$^{-1}$)$^{-1}$" (3.3.2)
   - parameter: R32/10 = 0.25–2; D=17.5 Mpc  
  > "for

$R_{32/10}=0.25$–2 with" (3.3.2)
   - assumption: Xco = 0.5e20 cm-2 (K km/s)-1  
  > "by adopting the CO-to-H$_2$ conversion factor of $X_{\rm CO}=0.5\times10^{20}$ cm$^{-2}$ (K km s$^{-1}$)$^{-1}$ (cite: bolatto2013)" (Mass and radial distribution of molecular gas)
   - fitting: Exponential fit to radial profile  
  > "The radial distribution $\Sigma_{\rm H_2}$ shows an exponential decrease (dotted line) of $\Sigma_{\rm H_2}=1330\exp(-r/r_{\rm e})$" (Mass and radial distribution of molecular gas)
   - validation: _not stated_
5. **LTE rotational diagrams**: Rotational diagrams of HCN, HCO+ (1-0, 4-3) and CS (2-1, 7-6) in inner/outer CND and ring at 0.72'' beam  
  > "assuming optically thin LTE" (4.1 LTE analysis)
   - assumption: optically thin LTE; only two transitions  
  > "can be estimated from the rotational diagrams, assuming optically thin LTE." (LTE analysis)
   - fitting: _not stated_
   - validation: _not stated_
6. **Non-LTE modeling**: RADEX grid with chi2 minimisation on line ratios  
  > "we applied RADEX and conducted a $\chi^2$ test" (4.3)
   - software: RADEX
   - parameter: Tk 10–700 K step 10 K; NH2 1e18–1e25; nH2 1e3–1e9 step 10^0.25; dV=15 km/s  
  > "we varied the gas kinetic temperature within a range of $T_{\rm k}=10$–700 K" (4.3)
   - assumption: uniform sphere, all lines from same region; [HCN]/[HCO+]=[HCN]/[CS]; Tbg 2.7 K  
  > "assuming that all lines radiate from the same region. We adopted a uniform spherical geometry" (Non-LTE analysis of HCN, HCO$^+$, and CS)
   - fitting: chi2 grid search; chi2<1 region  
  > "the dark regions indicate the regions where $\chi^2<1$" (4.3)
   - validation: Repeat with HCO+-based ratios; compare N_H2 with CO(3-2)-derived value  
  > "The derived column densities are comparable to that derived from the CO(3–2) flux" (4.3)
7. **Star formation efficiency and outflow**: SFE = SFR surface density / Sigma_H2 using Brγ SFR; three-Gaussian decomposition of CO spectra; virial mass  
  > "The spectra are fitted by three Gaussians" (4.4.3)
   - assumption: R32/10=2 in CND; Mvir=1040 σ R, size ~30 pc  
  > "We calculated the virial mass given by $M_{\rm vir}=1040~\sigma_{v}~R$" (Outflow of molecular gas in CND)
   - fitting: three Gaussians  
  > "The spectra are fitted by three Gaussians" (Outflow of molecular gas in CND)
   - validation: Checked SFE with different extinction, R32/10 and Xco  
  > "SFE at the CND is still lower than those at the spots." (4.4.1)

## Software

- **CASA** : calibration/imaging, imfit, feather  
  > "The data were processed using the Common Astronomy Software Application (CASA" (Observations)
- **3DBarolo** : tilted-ring kinematics fit  
  > "fits a 3D tilted-ring to spectroscopic data cubes" (3.3.1)
- **RADEX** : non-LTE radiative transfer  
  > "non-LTE radiative transfer code RADEX" (4.3)

## Numeric results

| quantity | value | uncertainty | units | step | quote |
|---|---|---|---|---|---|
| Systemic velocity | 1471 | ±3 | km/s | 3 | The resultant $V_{\rm sys}$ of $1471\pm3$ km s$^{-1}$ |
| Position angle of major axis | 118 | ±4 | deg | 3 | $\theta_{\rm maj}=\timeform{118D}\pm\timeform{4D}$ |
| Inclination | 46 | ±1 | deg | 3 | $i=\timeform{46D}\pm\timeform{1D}$ |
| Molecular gas mass r≤5'' | 7.2e7–5.8e8 | not stated | Msun | 4 | $M_{\rm H_2}=7.2\times10^7-5.8\times10^8$ |
| CND kinetic temperature | 350–550 | not stated | K | 6 | $T_{\rm k}=$350–550 K, $n_{\rm H_2}\sim10^{4.5}$ cm$^{-3}$ |
| Ring kinetic temperature | 80–300 | not stated | K | 6 | In the ring, the best-fitted parameters with $\chi^2\lesssim1$ were $T_{\rm k}=80$–300 K |
| HCN rotational temperature in CND | 11.6 | ±1.8 | K | 5 | $T_{\rm rot}=11.6\pm1.8$ K |
| 95 GHz continuum PA | 20 | ±8 | deg | 2 | position angle of $\timeform{20D}\pm\timeform{8D}$ |

## Qualitative findings

- SFE in CND is almost an order of magnitude lower than at ring spots  
  > "The SFE in the CND is almost an order of magnitude lower than those at the spots in the star-forming ring." (4.4.1)

## Claim tuples

- H: Gas in the CND is hotter than in the ring | E: RADEX modelling of HCN, HCO+, CS ratios | R: Tk 350–550 K vs 80–300 K | F: CND gas hotter | **supported**
- H: Star formation is suppressed in the CND | E: Compare ALMA gas surface density with Brγ SFR | R: SFE lower by ~order of magnitude | F: jets heat gas and feedback prevents star formation | **partially**

## Reasoning

- Why this data: _not stated_
- Why this method: _not stated_
- How they decided it was enough: _not stated_
- Limitation (authors): Non-LTE parameters in the ring not rigidly determined owing to low S/N; LTE fits use only two transitions  
  > "However, the parameters could not be determined rigidly because of the low S/N." (Summary)
- Caveat (inferred, ours): Gas heating attributed to jets is circumstantial
- Caveat (inferred, ours): Non-LTE results depend on assumed abundance ratios and single-zone model
- Caveat (inferred, ours): R32/10 and Xco assumptions dominate gas-mass uncertainty

## Reproducibility

- Data public (paper): ALMA project data acknowledged via ADS/JAO  
  > "This paper makes use of the following ALMA data: ADS/JAO.ALMA#2013.1.01329.S." (Acknowledgments)
- Products in archive: _not stated_
- Missing: Imaging masks and clean thresholds
- Missing: Line-free channels
- Missing: Region apertures and flux tables
- Missing: Brγ SFR maps from Falcón-Barroso
- Data volume (inferred): Large: multiple Band 3/7 12m+ACA+TP tracks, roughly 100s of GB raw
- Score (inferred): 3/5, Public data and named tools, but many imaging and fitting details missing and SFR data external.
- Rediscovery candidate: no, Recipe incomplete for several key results and relies on non-public Brγ data.

## Links

- Method: (cite: barolo) (3DBarolo tilted-ring fitting)
- Method: (cite: vandertak) (RADEX)
- Companion: (cite: falcon) (Brγ/H2 SINFONI data for SFR and shock diagnostics)
- Companion: (cite: izumi2016) (Submillimeter-HCN diagnostic diagram)

## Checks

```json
{
 "quotes": 78,
 "quotes_ok": 78,
 "quote_pass_rate": 1.0,
 "quotes_too_long": 0,
 "unsupported_facts": 0,
 "project_codes": 1,
 "codes_not_in_text": [],
 "codes_not_in_obscore": [],
 "obscore_codes_not_in_card": [],
 "codes_printed_but_missing": [],
 "numeric_results": 8,
 "numeric_problems": 0,
 "fill": {
  "facts": 87,
  "stated": 58,
  "rate": 0.667
 },
 "evidence_ok": true
}
```
