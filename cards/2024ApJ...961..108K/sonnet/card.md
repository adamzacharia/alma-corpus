# The CO Outflow Components Ejected by a Recent Accretion Event in B335

`2024ApJ...961..108K` | The Astrophysical Journal 2024 | first author: Kim, Chul-Hwan | arXiv: 2312.05781 | DOI: 10.3847/1538-4357/ad1400

Card schema 1.0 | model claude-sonnet-5-5 | depth full | type archival_reuse

## Science

- Fields: star_formation
- Question: Is the recent mid-IR accretion burst in B335 directly linked to the high-velocity 12CO ejection components, and what fraction of accreted mass was ejected?  
  > "In this work, we aim to investigate *the relationship between contemporaneous accretion and ejection activities* in B335." (Introduction)
- Target **B335 (IRAS 19345+0727)**: coordinates _not stated_; z/distance 164.5 pc  
  > "B335 is an isolated dark globule located at a distance of 164.5 pc (cite: Watson2020)." (Introduction); distance from Watson2020  
  > "B335 is an isolated dark globule located at a distance of 164.5 pc (cite: Watson2020)." (Introduction)

## Data provenance

- ALMA projects: 2017.1.00288.S
- bands: Band 6  
  > "A high-resolution observation was carried out with ALMA in band 6 between October 21 and 29, 2017" (2.1 ALMA)
- frequencies and spectral setup: 12CO 2-1 SPW 122.070 kHz (0.16 km/s) resolution, 117.187 MHz bandwidth; continuum SPW 2.000 GHz bandwidth; five SPWs also covering 13CO, C18O, SiO 5-4  
  > "the spectral resolution of the data, including $^{12}$CO $v = 0$ $J = 2-1$ (230.538 GHz), was set to 122.070 kHz (0.16 km s$^{-1}$, $\Delta \textit{v}$) while the total bandwidth was 117.187 MHz." (2.1 ALMA)
- continuum bandwidth: _not stated_
- arrays: _not stated_
- configurations: _not stated_
- baselines: _not stated_
- angular resolution: continuum 0.046x0.044 arcsec; 12CO 0.092x0.081 arcsec  
  > "| 2017.1.00288.S | 2017.10.21-29 | Continuum | 0.046 $\times$ 0.044 | $\sim$0.015$^{a}$ |  |" (Table 1)
- max recoverable scale: _not stated_
- sensitivity: continuum ~0.015 mJy/beam; 12CO ~1.70 mJy/beam per channel  
  > "The RMS noise level of the $^{12}$CO maps was calculated per channel (channel width = 0.16 km s$^{-1}$) and averaged over the line-free channels." (Table 1)
- time on source: _not stated_
- observing dates: 2017 October 21-29  
  > "2017.10.21-29" (Table 1)
- pi or archival as stated: Archival data, PI Bjerkeli  
  > "The ALMA data archive contains several observational datasets of B335" (2.1 ALMA)
- Line: 12CO J=2-1 (230.538 GHz)
- Other facility **WISE/NEOWISE**: 4.6 micron (W2) mid-IR light curve of B335 from 2010 onward  
  > "B335 has been observed by the *WISE*/*NEOWISE* survey since 2010: in April and October 2010 and every six months since 2014." (2.2 WISE/NEOWISE)
- Other facility **Spitzer IRAC**: I2 aperture photometry point added to the light curve  
  > "The aperture size was set at 12 $''$ following the guidelines from the IRAC instrument handbook." (3.1 The mid-IR outburst)
- External data: Luminosity vs W2 flux density relation and model parameters (R*=1.17 Rsun, T*=7000 K, infall rate, quiescent luminosity) from 3D continuum modeling  
  > "The relation between the central luminosity and W2 flux density of B335 has been explored based on the 3D continuum modeling by (cite: Evans2023)" (4.2 Mass ratio between ejection and accretion) [from (cite: Evans2023)]
- External data: Outflow inclination of 10 deg from plane of sky  
  > "The outflow inclination is $\sim$10$^\circ$ from the plane of the sky (cite: hirano1988)." (3.2 The high-velocity 12CO clumps) [from (cite: hirano1988)]
- External data: CO abundance X_CO=1.7e-4  
  > "we adopt a standard CO abundance relative to H$_{2}$, $X_{\text{CO}}=1.7\times10^{-4}$ (cite: Lacy2017)" (4.1 Properties of ejected gas components) [from (cite: Lacy2017)]
- External data: Protostar mass estimates 0.05 Msun and 0.02-0.06 Msun  
  > "(cite: yen2015_b335) derived the $M_{\star}$ of 0.05 M$_{\odot}$, while (cite: imai2019) provided a range of mass as 0.02 – 0.06 M$_{\odot}$." (4.2 Mass ratio between ejection and accretion) [from (cite: yen2015_b335; imai2019)]

## Processing

### Calibration

- pipeline or manual: _not stated_
- casa version: CASA v5.1.1 for initial calibration; v6.2.1 for self-calibration and imaging  
  > "The data were initially calibrated using CASA v5.1.1 (cite: McMullin2007)." (2.1 ALMA)
- pipeline version: _not stated_
- archive products used as is: _not stated_
- flux calibrator: _not stated_
- flux scale uncertainty: _not stated_
- self calibration: Self-calibration of continuum, solution applied to the 12CO cube  
  > "we performed self-calibration for the continuum emission using CASA v6.2.1 (cite: McMullin2007)." (2.1 ALMA)

### Imaging

- task: tclean in CASA v6.2.1  
  > "was then imaged from the continuum subtracted visibility data using *tclean* task at CASA v6.2.1." (2.1 ALMA)
- deconvolver: _not stated_
- weighting robust: Natural weighting adopted (uniform and Briggs robust 0.5 tested)  
  > "we adopted a natural weighting and a uvtaper of 0.06$''$ to improve the SNR." (2.1 ALMA)
- uv taper: 0.06 arcsec  
  > "we adopted a natural weighting and a uvtaper of 0.06$''$ to improve the SNR." (2.1 ALMA)
- cell size: _not stated_
- image size: _not stated_
- masking: _not stated_
- multiscale scales: _not stated_
- continuum subtraction: Cube imaged from continuum-subtracted visibilities  
  > "imaged from the continuum subtracted visibility data" (2.1 ALMA)
- line free channels: _not stated_
- primary beam correction: _not stated_
- array combination: _not stated_
- smoothing: _not stated_
- final beam: _not stated_
- final rms: _not stated_

### Inherited from earlier work

- WISE W2 averaging method  
  > "The W2 band data used in this work was averaged applying a similar method from (cite: park2021)." (2.2 WISE/NEOWISE) [from (cite: park2021)]
- Ejection properties (mass, energy, momentum, force) calculation  
  > "of the high-velocity ejection clumps following (cite: dunham2014)." (4.1 Properties of ejected gas components) [from (cite: dunham2014)]
- Minimum-Tex approach for lower limits  
  > "We follow a similar approach, finding the minimum value of $f(J, T_{\text{ex}}, X_{\text{mol}})$" (4.1 Properties of ejected gas components) [from (cite: dunham2010)]
- Spitzer I2 to W2 passband correction  
  > "corrected to match the WISE W2 passband following the equations of (cite: 2014Antoniucci)." (3.1 The mid-IR outburst) [from (cite: 2014Antoniucci)]

### Not stated but needed to reproduce (our reading)

- Self-calibration solution intervals and number of rounds
- Continuum-free channel ranges for 12CO and continuum subtraction fit order
- Image size, cell size, clean threshold, masking, and resulting taper beam
- Which execution blocks/calibrators and flux scale were used
- Exact W2 magnitude to flux-density conversion and light-curve values
- Positions and velocities of individual clumps used for timescales
- Continuum peak position used as protostar location

## Analysis recipe

1. **Image 12CO cube and continuum**: Self-calibrate continuum, apply to line, continuum-subtract, tclean with natural weighting and uvtaper  
  > "we adopted a natural weighting and a uvtaper of 0.06$''$ to improve the SNR." (2.1 ALMA)
   - software: CASA
   - fitting: _not stated_
   - validation: Tested uniform, natural, Briggs 0.5 weightings  
  > "we tested three different weightings: uniform, natural, and Briggs with a robust parameter of 0.5." (2.1 ALMA)
2. **Build mid-IR light curve**: Average WISE/NEOWISE W2 single-epoch photometry within 5 arcsec; add Spitzer I2 aperture photometry  
  > "single-epoch catalogs found at the NASA/IPAC Infrared Science Archive were queried using a 5$''$ radius around the coordinates of B335." (2.2 WISE/NEOWISE)
   - parameter: 12 arcsec aperture for IRAC  
  > "The aperture size was set at 12 $''$" (3.1 The mid-IR outburst)
   - fitting: _not stated_
   - validation: Single-epoch images visually inspected  
  > "Single-epoch images were also visually inspected to ensure that the photometry provided accurate results." (2.2 WISE/NEOWISE)
3. **Date the high-velocity ejection**: Identify clumps in PV diagram, divide distance by inclination-corrected velocity  
  > "We estimate the kinematic timescale of both components by dividing the distance by the velocity." (3.2 The high-velocity 12CO clumps)
   - assumption: Inclination 10 deg from plane of sky; systemic velocity 8.3-8.5 km/s  
  > "We adopt 10$^\circ$ as the standard to derive outflow properties" (3.2 The high-velocity 12CO clumps)
   - fitting: _not stated_
   - validation: Compared with mid-IR brightening period; inclination varied by 30%  
  > "This is consistent with the period of increase when B335 brightened significantly." (3.2 The high-velocity 12CO clumps)
4. **Compute ejected mass, energy, momentum, force**: Optically thin LTE 12CO column density per pixel/channel, summed above 5 sigma over 1x1 arcsec box and -37.3 to -17.3 km/s  
  > "We use only the emission above 5$\sigma$ within the selected region and velocity range" (4.1 Properties of ejected gas components)
   - parameter: Tex = 17.5 K (minimum mass), X_CO=1.7e-4, mu_H2=2.809  
  > "We adopt $T_{\text{ex}}$ = 17.5 K to obtain the *minimum* value for the ejection mass." (4.1 Properties of ejected gas components)
   - assumption: Optically thin, LTE  
  > "we assume that the ejection components are optically thin and follow local thermal equilibrium (LTE) conditions." (4.1 Properties of ejected gas components)
   - fitting: _not stated_
   - validation: Compared force with Yen 2010 and Hirano 1988  
  > "This is approximately one order of magnitude higher than our result due to the larger coverage of the outflow." (4.1 Properties of ejected gas components)
5. **Derive accretion rate and mass ratio**: Convert W2 to luminosity with Evans2023 relation; Mdot_acc = L R/(f G M); compare to ejection rate  
  > "the mass accretion rate, $\dot{M}_{\text{acc}}$, can be obtained from the following equation" (4.2 Mass ratio between ejection and accretion)
   - parameter: R*=1.17 Rsun, M* 0.02-0.25 Msun, f_acc=0.5  
  > "Therefore, we adopt the $M_{\star}$ to range between 0.02 and 0.25 M$_{\odot}$." (4.2 Mass ratio between ejection and accretion)
   - assumption: Luminosity dominated by accretion  
  > "In the early embedded stages, the central luminosity is mainly produced by accretion." (4.2 Mass ratio between ejection and accretion)
   - fitting: _not stated_
   - validation: Cross-checked luminosity enhancement with F_IR ∝ L^1.5  
  > "This result is consistent with the luminosity calculated using the relation found in (cite: Evans2023)." (4.2 Mass ratio between ejection and accretion)

## Software

- **CASA** 5.1.1 (initial calibration); 6.2.1 (self-cal, imaging): Calibration, self-calibration, continuum subtraction and tclean imaging  
  > "The data were initially calibrated using CASA v5.1.1 (cite: McMullin2007)." (2.1 ALMA)

## Numeric results

| quantity | value | uncertainty | units | step | quote |
|---|---|---|---|---|---|
| Mid-IR brightening at 4.6 micron | 2.5 | not stated | mag | 2 | B335 brightened by 2.5 magnitudes between *WISE* and *NEOWISE* observations, reaching a peak brightness of W2$=9.2$ mag. |
| Ejection time before ALMA observation | 4.6 to 2.0 | up to ~3 yr from inclination | yr | 3 | we infer that the high-velocity ejection components were ejected 4.6 to 2.0 years before the ALMA observation date. |
| Ejected mass | 7.5e-8 | not stated | Msun | 4 | are $2.1 \times 10^{23}$ cm$^{-2}$ and $7.5 \times 10^{-8} \; \text{M}_{\odot}$, respectively. |
| Ejection kinetic energy | 1.9e40 | not stated | erg | 4 | 1.9 $\times 10^{40}$ erg |
| Ejection force | 3.8e-6 | not stated | Msun km/s/yr | 4 | 3.8 $\times 10^{-6} \; \text{M}_{\odot} \; \text{km} \; \text{s}^{-1} \; \text{yr}^{-1}$ |
| Mass ejection rate | 2.9e-8 | not stated | Msun/yr | 5 | resulting in 2.9 $\times\; 10^{-8}$ M$_{\odot}$ yr$^{-1}$ |
| Mean accretion rate during burst | 3.1e-6 to 3.8e-5 | range from stellar mass | Msun/yr | 5 | is in the range of $\sim$3.1 $\times 10^{-6}$ to $\sim$3.8 $\times 10^{-5}$ M$_{\odot}$ yr$^{-1}$ |
| Fraction of accreted mass ejected | 0.07 to 0.9 | 0.03-1.3% over parameter ranges | percent | 5 | at least, $\sim$0.07$\%$ to $\sim$0.9$\%$ of the accreted mass was ejected by the recent burst event. |

## Qualitative findings

- No red-shifted counterpart to the high-velocity ejection was detected; SiO and 13CO not detected at high velocity.  
  > "confirmed that no red-shifted high-velocity ejection components were detected in the ALMA observations." (3.2 The high-velocity 12CO clumps)

## Claim tuples

- H: The high-velocity CO ejecta were launched during the recent mid-IR accretion burst | E: Kinematic dating of CO clumps compared with WISE/NEOWISE light curve | R: Ejection 4.6-2.0 yr before ALMA observation, coincident with brightening | F: Ejection is directly linked to the recent accretion event | **supported**
- H: A measurable fraction of accreted mass is ejected in the burst | E: Compare ejected mass with accreted mass from W2-derived luminosity | R: 0.07-0.9% (0.03-1.3% with uncertainties) | F: At least ~1% of accreted mass ejected, a lower limit | **partially**

## Reasoning

- Why this data: Highest-angular-resolution archival data of B335  
  > "we obtained the highest-angular resolution data available in the archive." (2.1 ALMA)
- Why this method: Natural weighting plus taper chosen because the high-velocity emission was undetected in uniform and too faint in Briggs  
  > "The high-velocity ejection emission was not detected in the uniform weighting image" (2.1 ALMA)
- Alternative: Outflow inclination of 3 deg (Stutz) gives ~500 km/s knots and ejection 1.4-0.6 yr before; judged less consistent with typical shock-knot velocities  
  > "the estimated velocity of knots reaches an extremely high velocity of $\sim$500 km s$^{-1}$." (5.3 Inclination)
- How they decided it was enough: _not stated_
- Limitation (authors): Inclination, Tex, stellar R, M, f_acc are uncertain; mass accretion rate varies by factor 45  
  > "These extremes result in a factor of 45 difference in the derived mass accretion rate." (5.1 Stellar properties)
- Caveat (inferred, ours): Ejection and accretion timing is coincident but light curve has a gap 2010-2014
- Caveat (inferred, ours): Lower-limit mass depends on Tex=17.5 K and optically thin LTE
- Caveat (inferred, ours): Inclination without error drives timing
- Caveat (inferred, ours): Single epoch of ALMA data

## Reproducibility

- Data public (paper): Data obtained from ALMA archive  
  > "The ALMA data archive contains several observational datasets of B335" (2.1 ALMA)
- Products in archive: _not stated_
- Missing: Self-calibration parameters
- Missing: Clean parameters and line-free channels
- Missing: Clump positions/velocities and exact light curve data
- Missing: Evans2023 model values beyond those quoted
- Data volume (inferred): ~50-200 GB raw for five execution blocks
- Score (inferred): 3/5, Public data and explicit formulas, but imaging and self-calibration details are missing and key inputs come from other papers.
- Rediscovery candidate: no, Recipe incomplete in imaging settings and clump selection; results depend on inherited model inputs.

## Links

- Method: (cite: dunham2014) (Ejection property calculation)
- Method: (cite: park2021) (WISE light-curve averaging)
- Method: (cite: Evans2023) (Luminosity-W2 relation and stellar parameters)
- Companion: (cite: bjerkeli2019) (Earlier analysis of same ALMA data showing high-velocity CO component)
- Related: WISE/NEOWISE

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
 "numeric_results": 8,
 "numeric_problems": 0,
 "fill": {
  "facts": 78,
  "stated": 48,
  "rate": 0.615
 },
 "evidence_ok": true
}
```
