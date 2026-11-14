# Constraints on Metal Oxide and Metal Hydroxide Abundances in the Winds of AGB Stars: Potential Detection of FeO in R Dor

`2018ApJ...855..113D` | The Astrophysical Journal 2018 | first author: Decin, L. | arXiv: 1801.09302 | DOI: 10.3847/1538-4357/aaab6a

Card schema 1.0 | model claude-sonnet-5-5 | depth full | type observational_alma_primary

## Science

- Fields: evolved_stars, astrochemistry
- Question: Are metal oxides and hydroxides (AlO, AlOH, FeO, MgO, MgOH, CaO, CaOH) and MgS present in the winds of the AGB stars IK Tau and R Dor, and at what abundances compared with chemical models?  
  > "One aim was to detect metal oxides and metal hydroxides (AlO, AlOH, FeO, MgO, MgOH), some of which are thought to be direct precursors of dust nucleation and growth." (abstract)
- Target **R Dor**: coordinates _not stated_; z/distance _not stated_; distance from _not stated_
- Target **IK Tau**: coordinates _not stated_; z/distance _not stated_; distance from _not stated_

## Data provenance

- ALMA projects: 2013.1.00166.S
- bands: Band 7 (335–362 GHz)  
  > "Data were obtained in August-September 2015 in Band 7 (335–362 GHz) with a spatial resolution of $\sim$150 mas" (2 Observations)
- frequencies and spectral setup: _not stated_
- continuum bandwidth: _not stated_
- arrays: _not stated_
- configurations: _not stated_
- baselines: _not stated_
- angular resolution: ~150 mas; restoring beams 120-180 mas (IK Tau), 130-180 mas (R Dor)  
  > "The spectral restoring beam parameters are in the range of 120$-$180 mas for IK Tau and 130$-$180 mas for R Dor." (2 Observations)
- max recoverable scale: _not stated_
- sensitivity: channel rms 3-9 mJy (IK Tau), 2.7-5.7 mJy (R Dor)  
  > "is in the range of 3$-$9 mJy for IK Tau and 2.7$-$5.7 mJy for R Dor" (2 Observations)
- time on source: _not stated_
- observing dates: August-September 2015  
  > "Data were obtained in August-September 2015 in Band 7" (2 Observations)
- pi or archival as stated: PI L. Decin  
  > "(proposal 2013.1.00166.S, PI L. Decin)" (2 Observations)
- Line: FeO v=0, Omega=4, J=11-10 (336 816.030±0.05 MHz)
- External data: FeO laboratory spectroscopic constants and rest frequencies (B = 15493.63255 MHz)  
  > "$B$ = 15493.63255 MHz (cite: Allen1996)" (3.2 FeO column density) [from Allen1996]
- External data: FeO permanent dipole moment 4.7 Debye  
  > "Using a permanent electric dipole moment of 4.7 Debye (cite: Steimle1989)" (Derivation of the column density) [from Steimle1989]
- External data: Kinetic temperature 1300–2400 K between 1 and 2.5 R*  
  > "ranges between 1300–2400 K (cite: Decin2017arXiv170405237D)" (3.2 FeO column density) [from Decin2017arXiv170405237D]
- External data: Collisional rates substituted from HCN-H2 and SiO-H2  
  > "The HCN-H$_2$ system (cite: Green1974ApJ...191..653G) was used to extract the collisional rates for MgOH, CaOH (and AlOH)" (3.3 abundances) [from Green1974ApJ...191..653G; Dayou2006A&A...459..297D]

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

- Data reduction in CASA  
  > "Data reduction was done using CASA (cite: McMullin2007ASPC..376..127M) and is described in detail in (cite: Decin2018)." (2 Observations) [from Decin2018]
- Abundance procedure and ALI non-LTE model, Re=2.5 R*, vturb=1 km/s, Rmax=40 R* for IK Tau  
  > "we use the same procedure as for the determination of the AlO, AlOH and AlCl abundances in R Dor and IK Tau outlined in (cite: Decin2017arXiv170405237D)." (3.3 abundances) [from Decin2017arXiv170405237D]
- Velocity beta-laws and vLSR of 7 km/s  
  > "Using the velocity $\beta$-laws described by (cite: Decin2018) (their Eqs.(2)–(4))" (3.2 FeO column density) [from Decin2018]

### Not stated but needed to reproduce (our reading)

- CASA version, calibrators and flux scale
- Imaging parameters (weighting, robust, cleaning, continuum subtraction, line-free channels)
- Source distances, stellar parameters and temperature/velocity power-law parameters
- Exact aperture and baseline fit details for the TiO2 template subtraction
- Mass-loss and stellar radius values used for R*

## Analysis recipe

1. **Identify FeO feature**: Compare unidentified line frequencies with predicted metal oxide/hydroxide lines in JPL/CDMS and lab data  
  > "The rest frequencies of the unidentified features were carefully compared to the predicted line frequencies of various metal oxides and hydroxides." (2 Observations)
   - fitting: _not stated_
   - validation: Other Omega components undetected; SiS absent in R Dor avoids blend  
  > "The higher excitation $\Omega$ components remain undetected." (3.1 FeO transition)
2. **Subtract TiO2 blend and measure line flux**: Average three TiO2 lines scaled to peak, fit soft-parabola, subtract; spectrum from 300 mas circular aperture  
  > "An average flux density of these three lines scaled to the same peak flux was calculated and fitted using a ‘soft-parabola’ function" (3.1 FeO transition)
   - fitting: soft-parabola  
  > "An average flux density of these three lines scaled to the same peak flux was calculated and fitted using a ‘soft-parabola’ function" (Analysis and results, The FeO (v = 0, Ω = 4, J = 11−10) transition)
   - validation: _not stated_
3. **LTE column density**: Optically thin population-diagram: N_u from W, then N(FeO) via partition function for Tx 80-2000 K  
  > "We use a population diagram analysis to estimate the column density of FeO, $N$(FeO)." (3.2 FeO column density)
   - parameter: Tx lower limit 80 K, upper 2000 K; unresolved source of 150 mas  
  > "We henceforth assume a lower limit for the excitation temperature of 80 K." (3.2 FeO column density)
   - assumption: Optically thin emission, LTE, all H in H2  
  > "Assuming the emission is optically thin" (3.2 FeO column density)
   - fitting: _not stated_
   - validation: _not stated_
4. **Non-LTE abundances and upper limits**: ALI non-LTE radiative transfer 1D with power-law T and v, constant or Gaussian abundance profile, substituted collisional rates  
  > "we modelled the ALMA data using a non-LTE radiative transfer model based on the Accelerated Lambda Iteration (ALI) method" (3.3 abundances)
   - software: ALI code
   - parameter: R Dor: Re=2.5 R*, Rmax=6 R*, vturb=3 km/s; IK Tau: constant f, Rmax=40 R*, vturb=1 km/s  
  > "Allowing the turbulent velocity to be 3 km/s permits the predicted line profile to reach the observed $\Delta v$ of 7.5 km/s" (3.3 abundances)
   - fitting: _not stated_
   - validation: Varying collisional rates by factor 10 changes abundances ≤10%, except FeO -60% if rates lower  
  > "Changing the collisional rates by one order of magnitude only alters the retrieved abundances by 10% or less." (3.3 abundances)
5. **Compare with chemical kinetics model**: Gas-phase network (59 reactions) in a pulsation-shock parcel over a pulsation period  
  > "The gas-phase network used in this study contains 7 atomic (H, He, C, O, Ca, Mg, Fe) and 15 molecular" (4.1 Description of gas-phase chemical kinetics models)
   - fitting: _not stated_
   - validation: Constant T and n runs compared with equilibrium abundances, within factor 2 for most molecules  
  > "For the large majority of molecules, the differences are small and within a factor of 2." (4.1 Description of gas-phase chemical kinetics models)

## Software

- **CASA** : Data reduction  
  > "Data reduction was done using CASA (cite: McMullin2007ASPC..376..127M)" (2 Observations)

## Numeric results

| quantity | value | uncertainty | units | step | quote |
|---|---|---|---|---|---|
| FeO peak flux | 0.093 | not stated | Jy | 2 | The peak flux of the FeO line is 0.093 Jy and the integrated line flux is 0.79 Jy km/s. |
| FeO integrated line flux | 0.79 | not stated | Jy km/s | 2 | the integrated line flux is 0.79 Jy km/s |
| N(FeO) in R Dor | 1.1e15 | ±0.9e15 | cm^-2 | 3 | We derive a column density N(FeO) of $1.1\pm0.9\times10^{15}$ cm$^{-2}$ in R Dor |
| [FeO/H] in R Dor | ~1.5e-8 | not stated | dimensionless | 4 | a fractional abundance \[FeO/H\]$\sim$1.5$\times$10$^{-8}$ accounting for non-LTE effects |
| Cross-ladder temperature upper limit | <130 | not stated | K | 3 | we derive that the cross-ladder temperature, $T_x^{\rm{CL}}$, is $<$130 K |
| [MgO/H2] upper limit R Dor / IK Tau | <5.5e-10 / <7e-11 | not stated | dimensionless | 4 | \[MgO/H$_2$\] $<$5.5$\times$10$^{-10}$ (R Dor) and $<$7$\times$10$^{-11}$ (IK Tau) |

## Qualitative findings

- Observed FeO abundance is about a factor 20 higher than gas-phase chemical kinetic predictions; vibrationally excited OH could partly account for it  
  > "The derived fractional abundance \[FeO/H\] is a factor $\sim$20 larger than conventional gas-phase chemical kinetic predictions." (abstract)

## Claim tuples

- H: Is FeO present in the wind of R Dor? | E: Search of ALMA Band 7 spectra for FeO J=11-10 | R: Feature at 336.815 GHz attributed to FeO; N(FeO)=1.1e15 cm^-2 | F: Potential first detection of FeO in an evolved star wind | **partially**
- H: Do chemical models reproduce observed FeO and upper limits? | E: Pulsation-shock gas-phase kinetics | R: Upper limits consistent; FeO predicted ~20x too low | F: FeO is hard to make at the observed level | **supported**

## Reasoning

- Why this data: _not stated_
- Why this method: _not stated_
- Alternative: Sputtering of dust grains considered unlikely as FeO source  
  > "Another possibility is the sputtering of dust grains, although this seems unlikely" (4.2 Outcome)
- How they decided it was enough: _not stated_
- Limitation (authors): Only one FeO transition detected; collisional rates unknown; source unresolved  
  > "This is unfortunate, since the detection of more than one transition of FeO would strengthen its identification." (3.1 FeO transition)
- Caveat (inferred, ours): Single-line identification
- Caveat (inferred, ours): Large Tx range gives wide N(FeO) uncertainty
- Caveat (inferred, ours): Substituted collisional rates and unresolved source size

## Reproducibility

- Data public (paper): ALMA archive project 2013.1.00166.S acknowledged  
  > "This paper uses the ALMA data ADS/JAO.ALMA2013.1.00166.S." (Acknowledgements)
- Products in archive: _not stated_
- Missing: Calibration and imaging details (in Decin2018)
- Missing: ALI model parameters and stellar properties
- Data volume (inferred): ~100-300 GB
- Score (inferred): 3/5, Public data and clear column density recipe, but reduction and model setup are deferred to other papers.
- Rediscovery candidate: no, Processing deferred to Decin2018 and the non-LTE model inputs are incomplete.

## Links

- Method: Decin2018 (Data reduction and soft-parabola function)
- Method: Decin2017arXiv170405237D (Non-LTE abundance procedure)
- Companion: Decin2018 (Full ALMA survey of the same data)
- Related: ATOMIUM

## Checks

```json
{
 "quotes": 41,
 "quotes_ok": 41,
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
  "facts": 75,
  "stated": 30,
  "rate": 0.4
 },
 "evidence_ok": true
}
```
