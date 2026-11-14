# Planck's Dusty GEMS. VIII. Dense-gas reservoirs in the most active dusty starbursts at z ∼ 3

`2021A&A...645A..45C` | Astronomy and Astrophysics 2021 | first author: Cañameras, R. | arXiv: 2009.13538 | DOI: 10.1051/0004-6361/202038979

Card schema 1.0 | model claude-sonnet-5-5 | depth full | type multi_facility_alma_minor

## Science

- Fields: high_z_galaxies, astrochemistry
- Question: What are the dense-gas properties (line ratios, excitation, heating, star-formation law, dense-gas fractions) of lensed dusty starbursts at z~3 from HCN, HCO+ and HNC lines?  
  > "In this paper, we study the dense-gas components of *Planck*’s Dusty Gravitationally Enhanced subMillimetre Sources (GEMS)" (1 Introduction)
- Target **PLCK_G244.8+54.9 (the Ruby)**: coordinates _not stated_; z/distance z=3.006  
  > "the latter being a maximal starburst[^2] at $z=3$" (1 Introduction); distance from CO lines (previous work)  
  > "the latter being a maximal starburst[^2] at $z=3$" (1 Introduction)
- Target **PLCK_G092.5+42.9**: coordinates 16:09:17.76 +60:45:21.0 (phase center)  
  > "$\alpha$=16:09:17.76 and $\delta$=+60:45:21.0 for PLCK_G092.5+42.9" (2.2.1 NOEMA); z/distance z=3.257  
  > "$\alpha$=16:09:17.76 and $\delta$=+60:45:21.0 for PLCK_G092.5+42.9" (2.2.1 NOEMA); distance from HCO+ line fit  
  > "$\alpha$=16:09:17.76 and $\delta$=+60:45:21.0 for PLCK_G092.5+42.9" (2.2.1 NOEMA)
- Target **PLCK_G145.2+50.9**: coordinates 10:53:22.56 +60:51:49.0 (phase center)  
  > "$\alpha$=10:53:22.56 and $\delta$=+60:51:49.0 for PLCK_G145.2+50.9" (2.2.1 NOEMA); z/distance z=3.549  
  > "$\alpha$=10:53:22.56 and $\delta$=+60:51:49.0 for PLCK_G145.2+50.9" (2.2.1 NOEMA); distance from HCO+ line fit  
  > "$\alpha$=10:53:22.56 and $\delta$=+60:51:49.0 for PLCK_G145.2+50.9" (2.2.1 NOEMA)

## Data provenance

- ALMA projects: 2015.1.01518.S
- bands: ALMA Band 3  
  > "These correspond to two science goals in Band 3, with lower and higher spatial resolution, respectively." (2.2.2 ALMA)
- frequencies and spectral setup: _not stated_
- continuum bandwidth: _not stated_
- arrays: _not stated_
- configurations: C40-5 (lower res, 39 antennas); C36-8 (higher res, 35 antennas)  
  > "with 39 antennas (configuration C40-5)" (2.2.2 ALMA); "with 35 antennae (configuration C36-8)" (2.2.2 ALMA)
- baselines: _not stated_
- angular resolution: 0.78"x0.67" (LR); 0.119"x0.081" (HR); 0.21"x0.16" tapered  
  > "obtained a synthesized beam of $0.119\ensuremath{''}\times0.081\ensuremath{''}$ at a position angle of 45.3$^\circ$" (2.2.2 ALMA)
- max recoverable scale: _not stated_
- sensitivity: HR cube rms 0.18 mJy/beam per 42 km/s channel  
  > "The rms in the data cube is $0.18\,{\rm mJy}\,{\rm beam}^{-1}$, with a spectral channel width of $42\,{\rm km}\,{\rm s}^{-1}$." (2.2.2 ALMA)
- time on source: 1.2 hr  
  > "HCN $J$=5–4 | 2015.1.01518 | 21/07/16 | 0.78$''$$\times$ 0.67$''$ | 110.63 | 1.2" (Table 1)
- observing dates: 21 July 2016 (LR); 23 October 2015 (HR)  
  > "These data were taken on 23 October 2015" (2.2.2 ALMA)
- pi or archival as stated: _not stated_
- Line: HNC J=5-4 (not stated)
- Line: HCN J=5-4 (not stated)
- Other facility **IRAM 30-m/EMIR**: HCN, HCO+, HNC mid-J spectra of eight GEMS  
  > "We observed high-density tracer molecules in the GEMS with EMIR on the IRAM 30-m telescope (project 108$-$14, PI Nesvadba)." (2.1)
- Other facility **NOEMA**: J=5-4 lines for three GEMS  
  > "The two GEMS, PLCK_G092.5+42.9 and PLCK_G145.2+50.9, were observed with NOEMA in September and October 2015 (project S15CH, PI Cañameras)." (2.2.1 NOEMA)
- External data: CO(1-0) fluxes and CO/[CI] line data for GEMS  
  > "we use the ratios of mid-$J$ dense-gas emission lines from the current analysis to CO(1–0) from (cite: harrington18)" (5.2) [from (cite: harrington18)]
- External data: Low-z dense-gas relations L_IR-L'dense  
  > "the GEMS are compared to relations from (cite: zhang14) drawn from $J=4$–3 line detections" (5.1) [from (cite: zhang14)]
- External data: Lens model magnifications  
  > "we used the amplification maps from our best-fit lens model of PLCK_G244.8+54.9 (cite: canameras17a)" (3.4) [from (cite: canameras17a)]

## Processing

### Calibration

- pipeline or manual: standard manual scripts with CASA (LR); automatic and manual flagging (HR)  
  > "For the reduction, we used standard manual scripts with the Common Astronomy Software Application (cite: mcmullin07)." (2.2.2 ALMA)
- casa version: _not stated_
- pipeline version: _not stated_
- archive products used as is: _not stated_
- flux calibrator: J1058+0133 (bandpass and flux)  
  > "calibrating bandpass and amplitude/flux with J1058+0133" (2.2.2 ALMA)
- flux scale uncertainty: _not stated_
- self calibration: _not stated_

### Imaging

- task: CLEAN  
  > "We produced the data cubes for the final analysis using `CLEAN` “Briggs” weighting" (2.2.2 ALMA)
- deconvolver: _not stated_
- weighting robust: Briggs robust=1.0  
  > "We used a “Briggs” weighting with ${\rm robust=1.0}$" (2.2.2 ALMA)
- uv taper: tapered HR cube, beam 0.21"x0.16"  
  > "using a ($u$,$v$) tapered version of the higher-resolution data cube, with beamsize of $0.21\ensuremath{''}\times0.16\ensuremath{''}$" (2.2.2 ALMA)
- cell size: _not stated_
- image size: _not stated_
- masking: _not stated_
- multiscale scales: _not stated_
- continuum subtraction: template from baseband at 111.616 GHz, scaled by 0.67  
  > "we needed to correct the amplitude of the continuum template map by a factor 0.67" (2.2.2 ALMA)
- line free channels: _not stated_
- primary beam correction: _not stated_
- array combination: _not stated_
- smoothing: _not stated_
- final beam: _not stated_
- final rms: _not stated_

### Inherited from earlier work

- Lens modelling and CO line properties/SLEDs  
  > "we used the amplification maps from our best-fit lens model of PLCK_G244.8+54.9 (cite: canameras17a)" (3.4) [from (cite: canameras17a); C18 (cite: canameras18b)]
- Stacking method  
  > "We performed the stacking following the method described in (cite: spilker14) and (cite: wilson17)." (Appendix A) [from (cite: spilker14); (cite: wilson17)]

### Not stated but needed to reproduce (our reading)

- CASA version
- Cell size, image size, clean masks and thresholds
- Line-free channels used for continuum
- Flux scale uncertainty
- Spatial template details and H2O correction details
- CO fluxes and lens model files from earlier papers

## Analysis recipe

1. **Image ALMA cubes and extract spectra**: Briggs robust=1 CLEAN cubes, pixels >3 sigma summed from velocity-integrated map for integrated spectra; HR cube tapered for line profile  
  > "We created a velocity-integrated line map and summed up pixels above 3$\,\sigma$ from this map." (2.2.2 ALMA)
   - software: CASA
   - fitting: single Gaussians with mpfit; per-channel flux uncertainty 10%  
  > "Emission lines were fitted with single Gaussians and errors computed with flux uncertainties per spectral channel of 10%." (2.2.2 ALMA)
   - validation: Compared with NOEMA and LR fluxes within 1 sigma  
  > "the HNC(5–4) flux matches those from the higher-resolution data cube and from NOEMA within 1$\,\sigma$" (2.2.2 ALMA)
2. **Deblend HNC(5-4) and CN(4-3)**: Simultaneous single Gaussian fit with frequencies fixed to CO redshift; HNC/CN = 1.76±0.86  
  > "The HNC(5–4)/CN(4–3) integrated flux ratio is 1.76$\pm$0.86" (3.3)
   - fitting: _not stated_
   - validation: J=4-3 and 5-4 HNC/HCN ratios agree  
  > "This similarity also suggests that our deblending of HNC(5–4) and CN(4–3) in Sect. [3](#sec:lineprop) is robust." (4.1.2)
3. **Differential magnification of HNC vs CO**: Luminosity-weighted magnification from lens model amplification maps and ALMA line image  
  > "We found $\mu = 16.3 \pm 1.8$, lower than the factor $\mu = 22.0 \pm 1.3$ for CO(4–3)" (3.4)
   - software: Lenstool
   - fitting: _not stated_
   - validation: _not stated_
4. **LVG excitation modelling**: RADEX grids over n and Tkin, chi2 vs measured ratios  
  > "We then computed the goodness-of-fit $\chi^2$ values between the measured and predicted line ratios for each combination of $n$ and $T_{\rm kin}$." (4.2)
   - software: RADEX
   - parameter: n=1e3-1e7 cm^-3, Tkin=TCMB-1e3 K, N/dv=1e14, Tbg=10.9 K  
  > "The column densities per unit velocity gradient were fixed to $N_{\rm dense}/dv=10^{14}\,{\rm cm}^{-2}\,{\rm km}^{-1}\,{\rm s}$." (4.2)
   - assumption: pure collisional excitation, single component, expanding sphere  
  > "The models adopt a single gas excitation component and a background radiation temperature of 10.9 K" (4.2)
   - fitting: chi2 grid  
  > "We then computed the goodness-of-fit $\chi^2$ values between the measured and predicted line ratios for each combination of $n$ and $T_{\rm kin}$." (4.2 Excitation of high-density tracers at high-redshift)
   - validation: compared with Arp 220 ratios  
  > "through the agreement between our LVG model extrapolations and line ratios in Arp 220" (4.2)

## Software

- **CASA** : ALMA reduction and CLEAN imaging  
  > "we used standard manual scripts with the Common Astronomy Software Application (cite: mcmullin07)" (2.2.2 ALMA)
- **GILDAS (CLASS, CLIC, MAPPING)** : EMIR fits; NOEMA calibration and imaging  
  > "The data were calibrated and imaged within `GILDAS/CLIC` and `MAPPING`." (2.2.1 NOEMA)
- **mpfit** : Gaussian line fitting  
  > "fitted simultaneously with Gaussian profiles using the `mpfit` algorithm" (2.2.1 NOEMA)
- **RADEX** : non-LTE LVG excitation grids  
  > "compared with those predicted by the `RADEX` code (cite: vandertak07)" (4.2)
- **Lenstool** : strong-lensing models  
  > "our detailed strong-lensing models with Lenstool (cite: jullo07)" (1 Introduction)

## Numeric results

| quantity | value | uncertainty | units | step | quote |
|---|---|---|---|---|---|
| HCN(5-4) flux, ALMA LR, PLCK_G244.8+54.9 | 2.05 | 0.25 | Jy km/s | 1 | The HCN(5–4) line flux of $(2.05\pm0.25)\,{\rm Jy}\,{\rm km}\,{\rm s}^{-1}$ |
| HNC(5-4)/CN(4-3) flux ratio | 1.76 | 0.86 | dimensionless | 2 | The HNC(5–4)/CN(4–3) integrated flux ratio is 1.76$\pm$0.86 |
| magnification HNC(5-4) | 16.3 | 1.8 | dimensionless | 3 | We found $\mu = 16.3 \pm 1.8$ |
| HCO+/HCN(5-4) in G244.8 | 1.00 | 0.15 | dimensionless | 0 | we measure an HCO$^+$/HCN(5–4) ratio of $1.00\pm0.15$ |
| LVG minimum chi2 density | n ~ 10^6.5 cm^-3 at Tkin ~ 50 K (chi2=9.1, 4 dof) | degenerate | cm^-3, K | 4 | The minimum $\chi^2 = 9.1$ (for four degrees of freedom) is obtained for $n \simeq 10^{6.5}\,{\rm cm}^{-3}$ and $T_{\rm kin} \simeq 50\,$K |

## Qualitative findings

- HNC(5-4) and CO(4-3) are nearly cospatial in G244.8, so differential lensing is ignored  
  > "CO(4–3) and HNC(5–4) (blended with CN(4–3)) are nearly cospatial in the image plane" (3.4)

## Claim tuples

- H: Differential lensing biases dense-gas line ratios | E: Compare luminosity-weighted magnification of HNC(5-4) and CO(4-3) in ALMA data | R: mu 16.3±1.8 vs 22.0±1.3, similar morphology | F: Differential lensing ignored | **supported**
- H: GEMS follow the local dense-gas star-formation law | E: Place GEMS on L_IR-L'dense relations | R: G244.8 consistent; two others show HCN deficit | F: Consistent with a unique law | **partially**
- H: Dense-gas fraction evolved between z~3 and 0 | E: HCO+(4-3)/[CI](1-0) vs local sources | R: similar ratios | F: dense-gas budget evolved little | **supported**

## Reasoning

- Why this data: _not stated_
- Why this method: _not stated_
- How they decided it was enough: _not stated_
- Limitation (authors): Strong parameter degeneracies in LVG models  
  > "illustrates the strong parameter degeneracies that prevent us measuring the exact gas conditions" (4.2)
- Caveat (inferred, ours): ALMA is one of three facilities; most results rely on NOEMA/EMIR
- Caveat (inferred, ours): Single-component LVG with fixed column density
- Caveat (inferred, ours): 30% missing-flux correction is approximate

## Reproducibility

- Data public (paper): _not stated_
- Products in archive: _not stated_
- Missing: CASA version and imaging parameters
- Missing: Lens model and CO data from previous papers
- Data volume (inferred): ~50-100 GB for ALMA Band 3 data
- Score (inferred): 3/5, ALMA calibration is described, but key parameters and earlier-paper inputs are missing.
- Rediscovery candidate: no, ALMA is a minor component and the recipe depends on other facilities and earlier-paper inputs.

## Links

- Method: (cite: canameras17a) (Lens model)
- Companion: (cite: canameras18b) (CO survey of GEMS)
- Related: Planck's Dusty GEMS

## Checks

```json
{
 "quotes": 59,
 "quotes_ok": 59,
 "quote_pass_rate": 1.0,
 "quotes_too_long": 0,
 "unsupported_facts": 0,
 "project_codes": 1,
 "codes_not_in_text": [],
 "codes_not_in_obscore": [],
 "obscore_codes_not_in_card": [],
 "codes_printed_but_missing": [],
 "numeric_results": 5,
 "numeric_problems": 0,
 "fill": {
  "facts": 77,
  "stated": 46,
  "rate": 0.597
 },
 "evidence_ok": true
}
```
