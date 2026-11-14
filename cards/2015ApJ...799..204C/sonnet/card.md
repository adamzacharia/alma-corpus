# Constraining the X-Ray and Cosmic-Ray Ionization Chemistry of the TW Hya Protoplanetary Disk: Evidence for a Sub-interstellar Cosmic-Ray Rate

`2015ApJ...799..204C` | The Astrophysical Journal 2015 | first author: Cleeves, L. Ilsedore | arXiv: 1412.1491 | DOI: 10.1088/0004-637X/799/2/204

Card schema 1.0 | model claude-sonnet-5-5 | depth light | type multi_facility_alma_minor

## Science

- Fields: protoplanetary_disks, astrochemistry
- Question: What are the cosmic-ray and X-ray ionization rates in the TW Hya disk, constrained by molecular ion emission compared with a grid of disk chemistry models?  
  > "We present an observational and theoretical study of the primary ionizing agents (cosmic rays and X-rays) in the TW Hya protoplanetary disk." (abstract)
- Target **TW Hya**: coordinates _not stated_; z/distance d = 55 pc  
  > "assuming a distance of $d=55$ pc" (3.4 Line Radiative Transfer and Synthetic Observations); distance from assumed; not attributed in the text  
  > "assuming a distance of $d=55$ pc" (3.4 Line Radiative Transfer and Synthetic Observations)

## Data provenance

- ALMA projects: 2011.0.00001.SV
- bands: HCO+ (1-0) in Band 3; HCO+ (4-3) in Band 7 (ALMA Science Verification)  
  > "The HCO$^+$ ($1-0$) line was observed in Band 3 on May 13-14, 2011 with ten 12-m antennas for a total of 3.7 hours." (2.2 Archival Data); "The HCO$^+$ ($4-3$) line was observed in Band 7 on April 22, 2011 in three scheduling blocks for a total of 4.5 hours." (2.2 Archival Data)
- frequencies and spectral setup: _not stated_
- continuum bandwidth: _not stated_
- arrays: _not stated_
- configurations: _not stated_
- baselines: _not stated_
- angular resolution: HCO+ (1-0) beam 4.2''x2.9''; HCO+ (4-3) beam 1.7''x1.6''  
  > "| HCO$^+$ ($4-3$) | $23.3\pm3.5$ | ($1.7''\times1.6''$, $18^\circ$) | ALMA 2011.0.00001.SV. | N |" (Table 1)
- max recoverable scale: _not stated_
- sensitivity: _not stated_
- time on source: 3.7 h (HCO+ 1-0); 4.5 h (HCO+ 4-3)  
  > "The HCO$^+$ ($1-0$) line was observed in Band 3 on May 13-14, 2011 with ten 12-m antennas for a total of 3.7 hours." (2.2 Archival Data)
- observing dates: _not stated_
- pi or archival as stated: _not stated_
- Line: HCO+ 1-0 (not stated)
- Line: HCO+ 4-3 (not stated)
- Other facility **SMA**: New HCO+ (3-2) VEX observations and H13CO+ (3-2) observations  
  > "The HCO$^+$ (3-2) observations of TW Hydra were made with the SMA (cite: ho2004) located atop Mauna Kea on April 12, 2012 in the very extended (VEX) configuration" (2.1 Submillimeter Array Data)
- Other facility **Herschel**: HD (1-0) flux used to calibrate disk gas mass  
  > "We estimate the total mass in gas from the *Herschel* detection of HD (cite: bergin2013)" (3.1 Physical Structure)
- External data: N2H+ (4-3) ALMA flux and radial profile  
  > "| N$_{2}$H$^+$ ($4-3$) | $4.6\pm0.7$ | ($0.63''\times0.59''$, $-18^\circ$) | (cite: qioberg2013) | N |" (Table 1) [from (cite: qioberg2013)]
- External data: HD (1-0) flux 70.6±7.8 Jy km/s  
  > "| HD ($1-0$) | $70.6\pm7.8$ | ($9.4''\times9.4''$) | (cite: bergin2013) | Y |" (Table 1) [from (cite: bergin2013)]
- External data: C18O and 13CO (2-1) fluxes  
  > "| $^{13}$CO ($2-1$) | $2.76\pm0.18$ | ($2.7''\times1.8''$, $-3^\circ$) | (cite: favre2013; qioberg2013) | Y |" (Table 1) [from (cite: favre2013; qioberg2013)]
- External data: N2H+ (3-2) flux  
  > "| N$_{2}$H$^+$ ($3-2$) | $2.2\pm0.46$ | ($3.5''\times2.0''$, $10^\circ$) | (cite: qi2013) | Y |" (Table 1) [from (cite: qi2013)]
- External data: Quiescent X-ray spectrum model used as baseline template  
  > "the baseline “quiescent” X-ray model is the two component plasma model (raymond) derived by (cite: kastner1999), with 1.7 MK and 9.7 MK components" (3.3.2 X-ray Ionization) [from (cite: kastner1999)]
- Simulation/model as data: Grid of 20 chemical models (5 CR x 4 X-ray spectra) with LIME synthetic line emission, compared with the observed line fluxes  
  > "The set of five CR models (§[3.3.1](#sec:CRs)) and four X-ray models (§[3.3.2](#sec:xrays)) forms a grid of twenty different ionization profiles" (3.4 Line Radiative Transfer and Synthetic Observations)

## Processing

### Calibration

- pipeline or manual: _not stated_
- casa version: _not stated_
- pipeline version: _not stated_
- archive products used as is: Publicly available calibrated Science Verification data used; flux extracted from an 8'' region  
  > "From the publicly available calibrated data, we extract the flux from an 8$''$ region for both lines." (2.2 Archival Data)
- flux calibrator: Titan (ALMA SV); Titan and Callisto for SMA H13CO+  
  > "Titan, 3C279, and J1037-295 were used for flux, gain and phase calibration, respectively." (2.2 Archival Data)
- flux scale uncertainty: 15% absolute flux uncertainty  
  > "All reported noise in Table [1](#tab:data) combines in quadrature the random noise on the data and an absolute flux uncertainty of 15%." (2.2 Archival Data)
- self calibration: _not stated_

### Imaging

- task: SMA data imaged with MIRIAD, natural weighting; simulated ALMA/SMA data with CASA simobserve and clean, natural weighting  
  > "From the simulated visibilities we reconstruct the on-sky image using `clean` with natural weighting." (3.4 Line Radiative Transfer and Synthetic Observations)
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

- Disk density profile parametrization  
  > "We adopt the same parametric density profile presented in (cite: cleeves2013a) Eqs. (1-4), adapted from (cite: andrews2011)." (5.1 Dust Model) [from (cite: cleeves2013a)]
- CR ionization models and X-ray propagation  
  > "we have adopted the results of (cite: cleeves2013a) to construct five input cosmic ray models." (3.3.1 CR Ionization) [from (cite: cleeves2013a)]
- Chemical code  
  > "We employ a time-dependent chemical code specifically tailored to the disk chemical environment (cite: fogel2011)." (3.2 Disk Chemistry) [from (cite: fogel2011)]
- Compact and extended SMA HCO+ data combined with the new track  
  > "We have also combined the new VEX HCO$^+$ track with shorter spacing data from compact and extended tracks (cite: qi2008) to improve the imaging fidelity." (2.1 Submillimeter Array Data) [from (cite: qi2008)]

### Not stated but needed to reproduce (our reading)

- Exact CASA version and simobserve configuration/integration parameters
- ALMA SV imaging/extraction details (line-free channels, velocity range)
- Gas temperature fitting function from S. Bruderer (private communication)
- Chemical network files and LIME settings (photon count, grid)
- Fixed model parameters for the N2H+ and HCO+ radial profile comparison
- Calibration of the ALMA SV data (the Band 3 and Band 7 flux values) beyond the quoted integrated fluxes

## Analysis recipe

1. **extract line fluxes**: Integrated line fluxes from the SMA and ALMA cubes using an 8'' box  
  > "Integrated line fluxes were extracted from the spectral image cubes using an 8$"$ box to be consistent with the new and archival HCO$^+$ data." (2.2 Archival Data)
   - software: MIRIAD
   - fitting: _not stated_
   - validation: _not stated_
2. **build disk physical model**: SED fitting for dust structure; gas mass calibrated on Herschel HD flux  
  > "The resulting disk gas mass in our model is $M_g=0.04$ M$_\odot$ with an uncertainty of 0.02 M$_\odot$" (3.1 Physical Structure)
   - software: TORUS
   - assumption: gas-to-dust ratio 100 for interstellar gas, adjusted to 75-100 to match HD  
  > "With a vertically integrated gas-to-dust mass ratio of $f_g=\Sigma_g/\Sigma_d=75-100$ ($M_g=0.03-0.04$ M$_\odot$)" (5.2 Gas Model)
   - fitting: _not stated_
   - validation: Reproduces HD flux 76.6 vs observed 70.6 Jy km/s  
  > "our 0.04 M$_\odot$ model predicts $\int{F_{\rm HD}dv}=76.6$ Jy km s$^{-1}$" (5.2 Gas Model)
3. **run chemistry over ionization grid**: Time-dependent chemistry at 1 Myr for 5 CR x 4 X-ray models; CO abundance calibrated on CO isotopologues  
  > "we opt to examine the time-evolved chemical abundances at 1 Myr, when the ion-chemistry has leveled to an approximate steady-state." (3.2 Disk Chemistry)
   - software: XSPEC
   - parameter: chemically active grain surface area reduced to 3% of standard  
  > "we reduce the “chemically active” surface area of grains to $3\%$ of its standard value" (3.2 Disk Chemistry)
   - fitting: _not stated_
   - validation: Neutral gas CO and HCN used to verify the model  
  > "the present model is verified as appropriate to the current chemical evolutionary stage of TW Hya using neutral gas constraints, CO and HCN" (3.2 Disk Chemistry)
4. **synthetic observations and comparison**: LIME non-LTE line transfer; CASA simobserve for resolved-out lines; compare fluxes and radial profiles to data within 1/2/3 sigma  
  > "The line radiative transfer is computed using the LIME code (cite: brinch2010) in non-LTE where available" (3.4 Line Radiative Transfer and Synthetic Observations)
   - software: LIME, CASA
   - parameter: turbulent velocity 40 m/s; inclination ~7 deg  
  > "We adopt a turbulent velocity of 40 m s$^{-1}$ based on the observed upper limit from (cite: hughes2011)." (3.4 Line Radiative Transfer and Synthetic Observations)
   - assumption: 12C/13C=70±10, 18O/16O=540±30  
  > "using a fixed ratio of $\rm ^{12}C/^{13}C=70\pm10$ and $\rm ^{18}O/^{16}O=540\pm30$" (3.4 Line Radiative Transfer and Synthetic Observations)
   - fitting: Qualitative sigma-based goodness of fit; no sampler  
  > "For each considered emission line, agreement is classified as within 1$\sigma$, 2$\sigma$, 3$\sigma$ or as a poor fit between the observation and model." (Constraints on Ionizing Agents)
   - validation: Simulated beams compared with observed beams  
  > "which are in good agreement with the beams from the observations" (3.4 Line Radiative Transfer and Synthetic Observations)
5. **estimate dead zone**: Magnetic Reynolds number criterion Re<=3300 from modeled electron abundance  
  > "We choose a critical $Re$ for the disk to be dead as $Re\le3300$" (5.2 Dead-zones, Dust Growth and Accretion)
   - fitting: _not stated_
   - validation: Tested Re=1000 and 5000  
  > "but we also show $Re=1000$ and $Re=5000$ on the same plot" (5.2 Dead-zones, Dust Growth and Accretion)

## Software

- **CASA** : simobserve and clean for synthetic observations  
  > "we make synthetic observations using the `simobserve` task in CASA" (3.4 Line Radiative Transfer and Synthetic Observations)
- **MIRIAD** : CLEAN imaging of SMA data  
  > "All continuum and spectral line maps were then generated and CLEANed using the MIRIAD software package with natural weighting." (2.1 Submillimeter Array Data)
- **MIR** : SMA phase and amplitude calibration  
  > "All data were phase- and amplitude-calibrated using the MIR software package" (2.1 Submillimeter Array Data)
- **LIME** : non-LTE line radiative transfer  
  > "The line radiative transfer is computed using the LIME code (cite: brinch2010) in non-LTE" (3.4 Line Radiative Transfer and Synthetic Observations)
- **XSPEC** : X-ray template spectra  
  > "We construct four low-resolution X-ray templates with XSPEC" (3.3.2 X-ray Ionization)
- **TORUS** : dust temperatures and SED  
  > "We use the radiative transfer code TORUS" (5.1 Dust Model)

## Numeric results

| quantity | value | uncertainty | units | step | quote |
|---|---|---|---|---|---|
| CR ionization rate of best-fit models | <~1e-19 | not stated | s^-1 | 4 | a low CR ionization rate, $\zeta_{\rm CR}\lesssim10^{-19}$ s$^{-1}$ |
| Disk gas mass | 0.04 | 0.02 | Msun | 2 | TW Hya’s gas mass is $M_g=0.04\pm0.02$ M$_\odot$ |
| CO abundance relative to H2 | 1e-6 | not stated | dimensionless | 3 | we derive a CO abundance of $\chi({\rm CO})=10^{-6}$ relative to H$_2$ |
| Best-fit X-ray hardness ratio | -0.4 | not stated | dimensionless | 4 | these two models also have an X-ray spectral hardness ratio of $-0.4$ |
| Dead zone outer radius | 50 and 65 | not stated | AU | 5 | the $Re$ criteria results in a MRI dead region that extends from the inner disk out to 50 AU and 65 AU in the midplane |
| HCO+ (3-2) integrated flux | 12.9 | 2.12 | Jy km/s | 1 | / HCO$^+$ ($3-2$) / $12.9\pm2.12$ / ($0.69''\times0.39''$, $16.9^\circ$) / This work. / Y / |

## Qualitative findings

- HCO+ (3-2) shows an asymmetric excess contributing ~15-20% of the disk-integrated flux  
  > "The emission contributes approximately $\sim15-20\%$ of the overall disk-integrated HCO$^+$ ($3-2$) flux" (4.1 HCO$^+$ Spatial Distribution)

## Claim tuples

- H: Is the CR ionization rate in TW Hya at interstellar levels? | E: Compared a 5x4 CR/X-ray model grid with 11 molecular line observations | R: All acceptable models have zeta_CR <~1e-18 s^-1; best fits <~1e-19 | F: CRs are strongly excluded from the TW Hya disk | **supported**
- H: Do X-ray flares affect the disk chemistry? | E: Varied X-ray hardness ratio | R: Best fits have HR=-0.4, harder than the quiescent -0.8 | F: The chemistry reflects an elevated, flaring X-ray state | **supported**
- H: Does the dead zone coincide with the mm-grain concentration? | E: Computed Re from the best-fit ionization structure | R: Dead zone out to 50-65 AU | F: Coincides with the large-grain region | **partially**

## Reasoning

- Why this data: _not stated_
- Why this method: _not stated_
- Alternative: Higher CR rates reproduce the broad N2H+ emission but not the observed narrow ring  
  > "These observed features are only reproduced by low, modulated CR models and moderately hardened X-ray spectra." (4.3 Constraints on Ionizing Agents)
- How they decided it was enough: _not stated_
- Limitation (authors): Models under-predict HCO+ emission for lines other than (3-2); causes include asymmetry, CO abundance structure and temperature structure  
  > "the models generally under predict the HCO$^+$ emission for all lines except the ($3-2$) transition" (4.3 Constraints on Ionizing Agents)
- Caveat (inferred, ours): Fit quality is a qualitative sigma-count classification, with no formal likelihood or parameter uncertainty
- Caveat (inferred, ours): Results depend on a single fixed physical structure and uniform CO depletion
- Caveat (inferred, ours): Grain surface area reduction (3%) is ad hoc
- Caveat (inferred, ours): The grid is coarse (4 X-ray x 5 CR)

## Reproducibility

- Data public (paper): ALMA SV data are public, and the paper cites the ALMA SV website  
  > "From the publicly available calibrated data, we extract the flux from an 8$''$ region for both lines." (2.2 Archival Data)
- Products in archive: _not stated_
- Missing: Chemical code and network not released
- Missing: Gas temperature parametrization from private communication
- Missing: SMA data reduction parameters for the new tracks
- Missing: Full LIME settings
- Data volume (inferred): small (<10 GB) for ALMA SV portion
- Score (inferred): 3/5, ALMA SV data are public but the main results depend on a private chemical code and a complex model grid with qualitative fit criteria.
- Rediscovery candidate: no, The main results come from custom chemical modeling that cannot be reproduced from the ALMA data alone.

## Links

- Method: (cite: cleeves2013a) (CR models and disk structure)
- Method: (cite: cleeves2014par) (disk ion chemistry parameter study)
- Method: (cite: fogel2011) (chemical code)
- Companion: (cite: qioberg2013) (ALMA N2H+ (4-3) observations)
- Companion: (cite: bergin2013) (HD detection and gas mass)
- Related: ALMA Science Verification TW Hya

## Checks

```json
{
 "quotes": 61,
 "quotes_ok": 61,
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
  "facts": 83,
  "stated": 46,
  "rate": 0.554
 },
 "evidence_ok": true
}
```
