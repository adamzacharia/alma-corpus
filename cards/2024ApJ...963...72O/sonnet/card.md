# Revealing Multiple Nested Molecular Outflows with Rotating Signatures in HH270mms1-A with ALMA

`2024ApJ...963...72O` | The Astrophysical Journal 2024 | first author: Omura, Mitsuki | arXiv: 2401.03086 | DOI: 10.3847/1538-4357/ad19ce

Card schema 1.0 | model claude-sonnet-5-5 | depth full | type archival_reuse

## Science

- Fields: star_formation
- Question: Does the HH270mms1-A outflow consist of nested velocity components with rotation, and what are the launching radii of each component (disk wind vs X-wind)?  
  > "We could identify the launching radii of distinct velocity components within a single outflow with all the prototypical characteristics expected from recent theoretical works." (abstract)
- Target **HH270mms1 (mms1-A, mms1-B)**: coordinates _not stated_; z/distance 405.7 pc  
  > "Our target, HH270mms1, is embedded within L1617 ($d = 405.7\,{\rm pc}$, (cite: Tobin2020apj))" (1 Introduction); "The systemic velocity is $v_{\rm LSR} = 8.7\,\text{km\,s}^{-1}$ (cite: Choi2001ApJ; Sepuleveda2011aa)." (1 Introduction); distance from Tobin et al. 2020 (VANDAM Orion)  
  > "Our target, HH270mms1, is embedded within L1617 ($d = 405.7\,{\rm pc}$, (cite: Tobin2020apj))" (1 Introduction); "The systemic velocity is $v_{\rm LSR} = 8.7\,\text{km\,s}^{-1}$ (cite: Choi2001ApJ; Sepuleveda2011aa)." (1 Introduction)

## Data provenance

- ALMA projects: 2019.1.00086.S, 2015.1.00041.S
- bands: Band 7  
  > "the Band 7 observations were performed on December 11 and December 20, 2019 with a 12-m array configuration" (2 Observation and data reduction)
- frequencies and spectral setup: _not stated_
- continuum bandwidth: _not stated_
- arrays: _not stated_
- configurations: _not stated_
- baselines: 2019.1.00086.S: 15 m – 321 m; 2015.1.00041.S: 15.1 m – 2.5 km and 16.7 m – 3.7 km  
  > "the configuration of 12-m Array are 15.1 m – 2.5 km and 16.7 m – 3.7 km in each observation date." (2 Observation and data reduction)
- angular resolution: 0.57"x0.73", 0.71"x0.89", 0.34"x0.36" depending on line  
  > "$0.57\ensuremath{''} \times 0.73\ensuremath{''}$" (Table 1 (imaging))
- max recoverable scale: _not stated_
- sensitivity: _not stated_
- time on source: 9.06 min (2019.1.00086.S); 0.9 min (2015.1.00041.S)  
  > "The total integration time toward HH270mms1 is 9.06 minutes (543.6 seconds)." (2 Observation and data reduction); "The total integration time is 0.9 minutes (54 seconds)" (2 Observation and data reduction)
- observing dates: 2019 Dec 11 and 20; 2016 Sep 4 and 2017 Jul 19  
  > "carried out on September 4, 2016 and July 19, 2017" (2 Observation and data reduction)
- pi or archival as stated: Archival data, PIs Ian Stephens and John Tobin  
  > "We analyzed ALMA archival data taken from two different projects" (2 Observation and data reduction)
- Line: CO (isotopologue not rendered in text) J=3-2 (not stated)
- External data: Disk and continuum properties of mms1-A/B (dust masses 161 and 56.7 Earth masses, separation 887 au, disk radius 90±10 au, Toomre Q)  
  > "The dust mass of mms1-A and mms1-B is $161\,M_\oplus$ and $56.7\,M_\oplus$, respectively (cite: Tobin2020apj)." (4.2) [from (cite: Tobin2020apj)]
- External data: Protostellar mass 0.25 Msun assumed  
  > "We adopted a protostellar mass of $M_{\ast} = 0.25 \,M_{\odot}$ based on the assumption in (cite: Tobin2020apj)" (4.1) [from (cite: Tobin2020apj)]
- External data: CO abundance X_CO = 1e-4  
  > "We assumed the CO abundance ratio with respect to H$_2$, $X_{\rm CO}=10^{-4}$ (cite: Frerking1982ApJ)" (3.2) [from (cite: Frerking1982ApJ)]

## Processing

### Calibration

- pipeline or manual: Calibration performed with CASA; pipeline/manual not stated  
  > "Calibration for raw data was performed using Common Astronomy Software Application (cite: 2022PASP..134k4501C)." (2 Observation and data reduction)
- casa version: _not stated_
- pipeline version: _not stated_
- archive products used as is: _not stated_
- flux calibrator: J0552+0313 (2019 project); J0510+1800 / J0423–0120 (2015 project)  
  > "The calibrator of Bandpass, Gain and Flux is J0552+0313" (2 Observation and data reduction)
- flux scale uncertainty: _not stated_
- self calibration: _not stated_

### Imaging

- task: tclean  
  > "we used `tclean` task with `högbom` deconvolver." (2 Observation and data reduction)
- deconvolver: högbom  
  > "we used `tclean` task with `högbom` deconvolver." (2 Observation and data reduction)
- weighting robust: briggs; robust −1, 0.5, 2.0 depending on dataset/line  
  > "The robust parameter is set to $2.0$ for to minimize the side-lobe artifact due to a short integration time." (2 Observation and data reduction)
- uv taper: baselines >30 kλ, uvtaper 300 kλ (for one line)  
  > "we extract baseline $>\,30\,k\lambda$ and select the parameter for `uvtaper` as $300\,k\lambda$." (2 Observation and data reduction)
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

- Rotation velocity measurement method for v_p and v_phi from PV diagrams  
  > "We applied the same method as in (cite: Matsushita2021ApJ) to measure $v_{p,\infty}$ and $v_{\phi,\infty}$ using the PV diagrams" (4.1) [from (cite: Matsushita2021ApJ)]
- Launching radius formula  
  > "According to (cite: Anderson2003ApJ), we analytically estimated the launching radius of the outflow" (4.1) [from (cite: Anderson2003ApJ)]
- Low-velocity range set equal to earlier work  
  > "Note that the velocity range of the low-velocity component is set to be the same as reported in (cite: Lee2000ApJ)." (3.1) [from (cite: Lee2000ApJ)]

### Not stated but needed to reproduce (our reading)

- Line-free channels and continuum subtraction method
- Image size, cell size, masking and niter/threshold for tclean
- CASA version and whether archive-delivered calibrated products or re-calibration were used
- Which 12CO/13CO/C17O lines map to which rows of the imaging table (isotopologue names lost)
- How v_blue, v_red and r_infty were measured from PV diagrams
- Slit widths and PV cut parameters
- Mask/integration regions used for mass; Omega values
- Primary beam correction
- Rest frequencies

## Analysis recipe

1. **Image line and continuum data**: tclean with briggs weighting, hogbom deconvolver; uvtaper for one dataset  
  > "For both continuum and line imaging, the parameter of weighting is set `briggs`." (2 Observation and data reduction)
   - software: CASA
   - parameter: robust −1, 0.5, 2.0  
  > "The robust parameter is set to $-1$ for to obtain a higher angular resolution image with adequate sensitivity" (2 Observation and data reduction)
   - fitting: _not stated_
   - validation: _not stated_
2. **Identify velocity components and jet knots; knot dynamical times**: Channel maps and PV diagrams along axis; t_dyn = l_out/(v_LSR tan i)  
  > "t_{\rm dyn} = \dfrac{l_{\rm out}}{(v_{\rm LSR}\tan{i})}" (3.1)
   - assumption: Inclination i=51.1 deg from continuum; jets normal to disk  
  > "Adopting the disk inclination angle $i$ of mms1-A with respect to the plane of the sky $i=51.1\deg$ inferred from our high-resolution continuum image" (3.1)
   - fitting: _not stated_
   - validation: _not stated_
3. **Outflow mass, mass loss rate, force, luminosity**: LTE optically thin CO column density, M_out = mu m_H X_CO^-1 Omega d^2 N_CO; divided by t_dyn; 10 sigma boundary  
  > "Assuming the local thermodynamical equilibrium (LTE) and optically thin emission, we estimated the outflow mass as" (3.2)
   - parameter: Tex = 40 K, mu = 2.8, X_CO=1e-4, d=405.7 pc  
  > "excitation temperature, $T_{\rm ex}=40\,\text{K}$" (3.2)
   - assumption: Column density varies within 20% for Tex 20-50 K  
  > "The difference in column density is within 20% with the change of $T_{\rm ex}$ in the range of $20$ to $50\,\text{K}$." (3.2)
   - fitting: _not stated_
   - validation: Optically thin assumption gives lower limits  
  > "Thus, the quantities listed in Table [\[tab:outflowquantities\]](#tab:outflowquantities) may give a lower limit." (3.2)
4. **Outflow rotation and launching radii (low, intermediate)**: PV diagrams perpendicular to axis every 300 au; v_p, v_phi from blue/red peaks; r0 from Anderson et al. 2003 formula; Alfven radius and lever arm  
  > "v_{\phi,\infty} = \frac{1}{\sin{i}}\frac{v_\textrm{blue}-v_\textrm{red}}{2}" (4.1)
   - parameter: M* = 0.25 Msun  
  > "We adopted a protostellar mass of $M_{\ast} = 0.25 \,M_{\odot}$" (4.1)
   - assumption: Axisymmetric rotating outflow; only redshifted lobe used  
  > "In this study, we only derived the redshifted, northern outflow parameters" (3.3)
   - fitting: _not stated_
   - validation: Compared with disk/envelope rotation in 13CO/C17O velocity maps and PV  
  > "The velocity gradient of the disk in the PV diagram (Figure [7](#fig:13COC17O_pv)(c)) is similar to that of the outflow" (3.4)
5. **Jet launching radii**: Keplerian radius r_K = GM/v_K^2 with v_K = v_LSR/cos i of knots (Kudoh & Shibata 1997)  
  > "the launching radii of the high-velocity components can be estimated to be $(2.36- 3.14) \times 10^{-2}\,\text{au}$." (4.2)
   - assumption: Knot plateau velocity equals Keplerian velocity at launch radius  
  > "the plateau velocity (or the terminal velocity) in the PV diagram (Figure [3](#fig:pv_parallel)(a)) should approximately correspond to the Keplarian velocity at the launching radius of the knots." (4.2)
   - fitting: _not stated_
   - validation: _not stated_

## Software

- **CASA** : Calibration and tclean imaging  
  > "Calibration for raw data was performed using Common Astronomy Software Application (cite: 2022PASP..134k4501C)." (2 Observation and data reduction)
- **astropy** : Listed in software section  
  > "CASA (cite: 2022PASP..134k4501C), astropy (cite: 2022ApJ...935..167A), Matplotlib (cite: Huntermatplotlib)" (Software)
- **Matplotlib** : Plotting  
  > "CASA (cite: 2022PASP..134k4501C), astropy (cite: 2022ApJ...935..167A), Matplotlib (cite: Huntermatplotlib)" (Software)

## Numeric results

| quantity | value | uncertainty | units | step | quote |
|---|---|---|---|---|---|
| Launching radius, low-velocity outflow | 67.1–77.1 | not stated | au | 4 | we estimated the outflow launching radii to be $67.1-77.1\,\text{au}$ for the low-velocity flow |
| Launching radius, intermediate-velocity outflow | 13.3–20.8 | not stated | au | 4 | $13.3-20.8\,\text{au}$ for the intermediate-velocity flow |
| Jet launching radius | (2.36–3.14)e-2 | not stated | au | 5 | $(2.36-3.14) \times 10^{-2}\,\text{au}$ |
| Total outflow mass loss rate | 2.9e-7 | not stated | Msun/yr | 3 | $\dot{M}_{\rm out}=2.9 \times 10^{-7} \,M_{\odot}\,\text{yr}^{-1}$ |
| Total outflow force | 8.9e-6 | not stated | Msun km/s/yr | 3 | $F_{\rm out}=8.9 \times 10^{-6} |
| Jet knot interval, redshifted / blueshifted | 47.9 / 42.6 | not stated | yr | 2 | $\Delta t_{\rm dyn} \sim 47.9$ years for the redshifted jet and $\Delta t_{\rm dyn} \sim 42.6$ years for the blueshifted one |
| Lever arm lambda low / intermediate | 2.18–2.42 / 3.95–4.60 | not stated | dimensionless | 4 | The ratio $\lambda$ for the low-velocity outflow ranges from $\lambda = 2.18$ to $2.42$ |
| Deprojected max jet velocity | ~80 | not stated | km/s | 2 | with the maximum velocity of $\sim 80 \,\text{km\,s}^{-1}$ from the systemic velocity of mms1-A |

## Qualitative findings

- Jets (high-velocity) are surrounded by intermediate and low-velocity flows; knots indicate episodic ejection  
  > "The high- and intermediate-velocity flows have well-collimated structures surrounded by the low-velocity flow." (abstract)

## Claim tuples

- H: The outflow has nested velocity components with distinct launching radii | E: PV diagrams and channel maps of CO J=3-2 | R: Low, intermediate, high-velocity and entrained components identified | F: Nested outflow consistent with disk wind | **supported**
- H: Low- and intermediate-velocity flows rotate like the disk | E: Perpendicular PV diagrams compared with 13CO/C17O disk/envelope rotation | R: Same velocity gradients | F: Gradients are due to outflow rotation | **supported**
- H: Knot periodicity arises from binary orbit or disk instability | E: Compare knot intervals with estimated binary orbital period | R: Orbital period ~4.3e4 yr vs 42-48 yr | F: Binary rejected; gravitational instability favored | **partially**

## Reasoning

- Why this data: _not stated_
- Why this method: _not stated_
- Alternative: Binary orbital motion as origin of knot periodicity rejected  
  > "The time interval ($\Delta t_{\rm dyn} \sim 42 - 48\,\text{yr}$) is too short to explain the periodicity due to the binary orbital motion." (4.2)
- How they decided it was enough: _not stated_
- Limitation (authors): Protostellar mass not directly determined; launching radii depend on it  
  > "Thus, we need to determine the protostellar mass in the future in order to more accurately estimate the launching radii." (4.1)
- Limitation (authors): Optically thin assumption gives lower limits  
  > "Thus, the quantities listed in Table [\[tab:outflowquantities\]](#tab:outflowquantities) may give a lower limit." (3.2)
- Caveat (inferred, ours): Launching radius formula depends on assumed M*=0.25 Msun and untested axisymmetry
- Caveat (inferred, ours): Rotation only derived for one lobe; blue lobe lacks clear signature
- Caveat (inferred, ours): Single fixed Tex=40 K and typical velocities
- Caveat (inferred, ours): Jet launching radius assumes terminal velocity equals Keplerian, strongly model dependent

## Reproducibility

- Data public (paper): Archival ALMA data from two projects  
  > "We analyzed ALMA archival data taken from two different projects" (2 Observation and data reduction)
- Products in archive: _not stated_
- Missing: Image/cell size, masks, niter
- Missing: Line-free channels
- Missing: PV cut parameters and peak-fitting procedure
- Missing: CASA version
- Data volume (inferred): ~20-50 GB (two Band 7 12-m datasets)
- Score (inferred): 5/5, Public data and explicit formulas, but many imaging and PV measurement details unstated.
- Rediscovery candidate: yes, Public archival data, formulaic derivations, numeric results; some measurement details missing.

## Links

- Method: (cite: Anderson2003ApJ) (Launching radius formula)
- Method: (cite: Matsushita2021ApJ) (v_p and v_phi measurement)
- Method: (cite: KudohShibata1997ApJ) (Jet launching radius from terminal velocity)
- Companion: (cite: Tobin2020apj) (Source of Band 7 continuum data, disk and binary properties)
- Companion: (cite: Lee2000ApJ) (Earlier low-velocity outflow observations)
- Related: VANDAM Orion survey

## Checks

```json
{
 "quotes": 61,
 "quotes_ok": 61,
 "quote_pass_rate": 1.0,
 "quotes_too_long": 0,
 "unsupported_facts": 0,
 "project_codes": 2,
 "codes_not_in_text": [],
 "codes_not_in_obscore": [],
 "obscore_codes_not_in_card": [],
 "codes_printed_but_missing": [],
 "numeric_results": 8,
 "numeric_problems": 0,
 "fill": {
  "facts": 78,
  "stated": 43,
  "rate": 0.551
 },
 "evidence_ok": true
}
```
