# Hydrocarbon Emission Rings in Protoplanetary Disks Induced by Dust Evolution

`2016ApJ...831..101B` | The Astrophysical Journal 2016 | first author: Bergin, Edwin A. | arXiv: 1609.06337 | DOI: 10.3847/0004-637X/831/1/101

Card schema 1.0 | model claude-sonnet-5-5 | depth full | type observational_alma_primary

## Science

- Fields: protoplanetary_disks, astrochemistry
- Question: Why do C2H (and c-C3H2) emission rings appear at the edge of the mm-dust (pebble) disk in TW Hya and DM Tau, and what physical/chemical conditions (UV field, C/O) are needed to produce them?  
  > "Here we present the spatially resolved distribution of C$_2$H and C$_3$H$_2$ emission in TW Hya and C$_2$H in DM Tau obtained with the Atacama Large Millimeter/submillimeter Array (ALMA)." (Introduction)
- Target **TW Hya**: coordinates _not stated_; z/distance 54±6 pc  
  > "TW Hya is the closest young star with a disk at a distance of $54{\pm}6$ pc (cite: vanLeeuwen07)." (3.1 C$_2$H Emission Distributions in TW Hya and DM Tau); distance from van Leeuwen 2007  
  > "TW Hya is the closest young star with a disk at a distance of $54{\pm}6$ pc (cite: vanLeeuwen07)." (3.1 C$_2$H Emission Distributions in TW Hya and DM Tau)
- Target **DM Tau**: coordinates _not stated_; z/distance ~140 pc  
  > "at a distance of $\sim$140 pc (cite: Kenyon94; Schlafly14)" (3.1 C$_2$H Emission Distributions in TW Hya and DM Tau); distance from Kenyon et al. 1994; Schlafly et al. 2014  
  > "at a distance of $\sim$140 pc (cite: Kenyon94; Schlafly14)" (3.1 C$_2$H Emission Distributions in TW Hya and DM Tau)

## Data provenance

- ALMA projects: 2013.1.00198.S
- bands: _not stated_
- frequencies and spectral setup: 122.07 kHz channels; C2H N=3-2 (DM Tau, ~262 GHz), C2H N=4-3 and c-C3H2 (TW Hya, ~349-352 GHz, 338 GHz)  
  > "Observations of both sources were carried out with 122.07 kHz-width channels." (2 Observations)
- continuum bandwidth: _not stated_
- arrays: DM Tau: 37 and 38 antennas; TW Hya: 34 and 36 antennas (two configurations each)  
  > "DM Tau was observed on June 6, 2015 with 37 antennas ($21.4-740.4$ meter baselines) and on December 25, 2014 with 38 antennas ($15.1-348.5$ meter baselines)." (2 Observations)
- configurations: _not stated_
- baselines: 15.1–783.55 m  
  > "34 antennas ($15.1-348.5$ meter baselines) and 36 antennas ($21.36-783.55$ meter baselines), respectively." (2 Observations)
- angular resolution: TW Hya 0.48''x0.39''; DM Tau 0.56''x0.37'' (combined)  
  > "The synthesized beam for the DM Tau combined data sets has a shape and position angle (PA) of $0.56\ensuremath{''}\times 0.37\ensuremath{''}$" (2 Observations)
- max recoverable scale: _not stated_
- sensitivity: DM Tau 2.5 mJy/beam in 0.279 km/s; TW Hya 7 mJy/beam in 0.15 km/s  
  > "For DM Tau, the resulting RMS noise level in the image is 2.5 mJy beam$^{-1}$ in 0.279 km s$^{-1}$, and for TW Hya is 7 mJy beam$^{-1}$ in 0.15 km s$^{-1}$ channels." (2 Observations)
- time on source: DM Tau 57.1 min; TW Hya 43.4 min  
  > "The total on-source integration time for DM Tau in both configurations was 57.1 minutes. The total on-source integration time for TW Hya was 43.4 minutes." (2 Observations)
- observing dates: DM Tau: 2014 Dec 25 and 2015 Jun 6; TW Hya: 2014 Dec 31 and 2015 Jun 15  
  > "TW Hya was observed on December 31, 2014 and June 15, 2015" (2 Observations)
- pi or archival as stated: _not stated_
- Line: C2H N=4-3 hyperfine complex (TW Hya) (349.313-349.415 GHz)
- Line: C2H N=3-2 hyperfine complex (DM Tau) (261.978-262.079 GHz)
- Line: c-C3H2 10(1,10)-9(0,9)/10(0,10)-9(1,9) and others (351.782, 351.966, 352.194, 338.204 GHz)
- Other facility **SMA/APEX (Kastner et al. 2015)**: Earlier C2H N=3-2 and N=4-3 data used for line ratio comparison  
  > "for the higher transition data, an unresolved line detection from APEX was used, while the N = 3 – 2 emission was resolved by the SMA" (5.3 Excitation Analysis)
- External data: Edge of TW Hya 820 um dust disk at 47.1±0.2 AU  
  > "traces the edge of the surface density distribution at 820 $\mu$m to a radius of 47.1$\pm$0.2 AU" (3.1 C$_2$H Emission Distributions in TW Hya and DM Tau) [from Hogerheijde15]
- External data: TW Hya stellar UV spectrum used as radiation field input  
  > "The UV radiation field uses the observed stellar spectrum of TW Hya (cite: herczeg_twhya1; herczeg_twhya2) as an input" (4 Physical and Chemical Models) [from herczeg_twhya1; herczeg_twhya2]
- External data: X-ray luminosities: DM Tau 3e29 erg/s; TW Hya 1.6e30 erg/s  
  > "The X-ray luminosity for DM Tau is taken to be the preferred value from (cite: Henning10) of $L_X = 3 \times 10^{29}$ erg s$^{-1}$" (4 Physical and Chemical Models) [from Henning10; Raassen09]
- External data: C2H collision rates for RADEX  
  > "using RADEX (cite: radex) and the state to state collision rates by (cite: c2hcolxs)" (5.3 Excitation Analysis) [from van der Tak 2007; Spielfiedel 2012]
- Simulation/model as data: Thermo-chemical disk models (Du & Bergin 2014; Du et al. 2015) for TW Hya and DM Tau, with parametrized C and O depletion  
  > "Using the thermo-chemical model of (cite: Du14), we demonstrate that hydrocarbon rings are a natural feature" (1 Introduction)

## Processing

### Calibration

- pipeline or manual: Pipeline-calibrated measurement sets, then self-calibrated on continuum  
  > "From the pipeline calibrated measurement sets we self-calibrated the data using each source’s bright continuum emission to improve the signal-to-noise." (2 Observations)
- casa version: _not stated_
- pipeline version: _not stated_
- archive products used as is: _not stated_
- flux calibrator: DM Tau: J0510+180; TW Hya: Titan  
  > "Titan was used for the flux calibration." (2 Observations)
- flux scale uncertainty: 15%  
  > "An additional 15% uncertainty should be applied for the absolute flux calibration uncertainty." (2 Observations)
- self calibration: Self-cal on continuum; DM Tau used dedicated continuum SPW; TW Hya used line SPW with lines masked  
  > "TW Hya’s dedicated continuum window was in the opposite sideband from the C$_2$H lines, so we instead used the continuum data from the spectral window containing the lines, which were masked." (2 Observations)

### Imaging

- task: CASA 4.3 clean  
  > "We imaged the measurement sets with the `clean` task in CASA version 4.3" (2 Observations)
- deconvolver: _not stated_
- weighting robust: Briggs, robust = 0.5 (uniform for high-res DM Tau extended-only image)  
  > "using Briggs’ weighting with a robust parameter of 0.5." (2 Observations)
- uv taper: _not stated_
- cell size: _not stated_
- image size: _not stated_
- masking: _not stated_
- multiscale scales: _not stated_
- continuum subtraction: _not stated_
- line free channels: _not stated_
- primary beam correction: _not stated_
- array combination: Compact and extended data combined; TW Hya phase centres aligned on continuum peak  
  > "we aligned the compact and extended data’s phase-centers based on the continuum peak location." (2 Observations)
- smoothing: _not stated_
- final beam: High-res DM Tau: 0.30''x0.48'', PA=-23.8°  
  > "The beam on the higher resolution images is $0.30\ensuremath{''}\times0.48\ensuremath{''}$, $\rm PA=-23.8^\circ$." (2 Observations)
- final rms: High-res DM Tau: 6 mJy/beam per 0.279 km/s channel; 8 mJy/beam km/s integrated  
  > "The RMS noise on the high resolution image is 6 mJy/beam in 0.279 km s$^{-1}$ channels" (2 Observations)

### Inherited from earlier work

- Disk thermo-chemical model and TW Hya template  
  > "For this purpose we will use the disk model described by (cite: Du15)" (4 Physical and Chemical Models) [from Du15; Du14]
- Disk surface density parameterization  
  > "The disk parameterization is the same as (cite: Andrews2009)" (4 Physical and Chemical Models) [from Andrews2009]
- Dust optical constants (astrosilicate/graphite)  
  > "Their optical constants are taken from (cite: dl84)" (4 Physical and Chemical Models) [from dl84]

### Not stated but needed to reproduce (our reading)

- Line-free channels / continuum subtraction method
- Self-calibration solution intervals and number of rounds
- Image size, cell size, clean threshold, masks
- Details of stacking and ring-fitting for position angle and inclination
- Chemical network and reaction rate details of the Du & Bergin model
- Exact criteria for the 'best-fit' models (no fitting algorithm)
- Coordinates of targets

## Analysis recipe

1. **Image line and continuum data**: Self-calibrate pipeline-calibrated data and image with CASA clean (Briggs)  
  > "We imaged the measurement sets with the `clean` task in CASA version 4.3 using Briggs’ weighting with a robust parameter of 0.5." (2 Observations)
   - software: CASA
   - parameter: robust = 0.5  
  > "using Briggs’ weighting with a robust parameter of 0.5." (2 Observations)
   - fitting: _not stated_
   - validation: _not stated_
2. **Stack lines and derive disk geometry and radial profiles**: Stack lines to make integrated map; derive PA and inclination from outer C2H ring; deproject to radial brightness profile  
  > "For both disks, we derive a disk position angle and inclination from the outer C$_2$H ring, which we use to deproject the image to create a disk brightness profile." (2 Observations)
   - fitting: _not stated_
   - validation: _not stated_
3. **Exclude dust optical depth as ring origin**: Compare ring locations to dust optical depth from literature models  
  > "Thus, the outer ring is not an effect of dust optical depth and is the result of a change in molecular abundance." (3.3 Dust Optical Depth and Ring Structure)
   - fitting: _not stated_
   - validation: _not stated_
4. **Thermo-chemical modelling of rings**: Three-component dust disk models (inner, sub-mm, UV-dominated), uniform C/O tests, then parametrized C and O depletion; compare simulated N=4-3 emission to observations  
  > "The “best-fit” emission images of for both disks are shown in Fig. [9](#fig:best)." (5.1 Source Specific Models)
   - software: Du & Bergin thermo-chemical code, Monte Carlo radiative transfer (Dullemond et al. 2002)
   - parameter: Gas-to-dust mass ratio 100; dust size distribution power law exponent 3.5; cosmic ray rate ~1e-19 s^-1; models sampled at 5 Myr (TW Hya) and 1 Myr (DM Tau)  
  > "Thus we have run our models with a rate that is reduced compared to the interstellar medium by two orders of magnitude ($\sim 10^{-19}$ s$^{-1}$, with an attenuation parameter of 96 g/cm$^2$)." (Physical and Chemical Models)
   - assumption: Same TW Hya UV field used for both systems; 8:2 astrosilicate:graphite  
  > "we use the TW Hya radiation field for both systems" (4 Physical and Chemical Models)
   - fitting: Parameters chosen heuristically, no formal fit  
  > "The parameters are chosen heuristically for each disk to investigate what C and O distribution best reproduce the observed C$_2$H observations." (Appendix A)
   - validation: Predicted emission matches observations within a factor of 1.5; test with 10x higher gas mass  
  > "the predicted emission distribution shown in Fig. [9](#fig:best) matches observations within a factor of 1.5." (5.1.1 TW Hya)
5. **Excitation analysis of TW Hya C2H**: RADEX analysis of N=4-3/N=3-2 flux ratio  
  > "We have therefore re-analyzed the excitation characteristics of this emission using RADEX" (5.2 Excitation Analysis)
   - software: RADEX
   - assumption: 15% calibration uncertainty for ALMA and SMA  
  > "We have assumed 15\% calibration uncertainty for both ALMA and SMA." (5.2 Excitation Analysis)
   - fitting: _not stated_
   - validation: Consistent with model-predicted densities  
  > "C$_2$H appears to be emitting from gas with densities greater than 10$^6$ cm$^{-3}$ consistent with our predictions." (5.2 Excitation Analysis)

## Software

- **CASA** 4.3: Imaging with clean  
  > "We imaged the measurement sets with the `clean` task in CASA version 4.3" (2 Observations)
- **RADEX** : C2H excitation analysis  
  > "using RADEX (cite: radex)" (5.2 Excitation Analysis)

## Numeric results

| quantity | value | uncertainty | units | step | quote |
|---|---|---|---|---|---|
| DM Tau outer C2H ring position angle | 157 | ±5 | deg | 2 | The outer ring in DM Tau has a position angle of $157\pm5^\circ$ and inclination of $i=36\pm3^\circ$. |
| DM Tau inclination | 36 | ±3 | deg | 2 | inclination of $i=36\pm3^\circ$ |
| TW Hya ring position angle | 150 | ±10 | deg | 2 | The ring in TW Hya has a position angle of $150\pm10^\circ$ and inclination of $i=7\pm4^\circ$. |
| TW Hya inclination | 7 | ±4 | deg | 2 | inclination of $i=7\pm4^\circ$ |
| TW Hya C2H disk-integrated flux (F=5-4 + 4-3 pair) | 12.14 | 0.04 | Jy km/s | 1 | $12.14\pm0.04^\dagger$ |
| C2H N=4-3/N=3-2 flux ratio (TW Hya) | 2.16 | ±0.45 | dimensionless | 5 | = 2.16 \pm 0.45. |
| TW Hya C2H ring peak radius | ~1.1 | not stated | arcsec | 2 | The peak of the C$_2$H ring appears just beyond this edge at $R\sim 1.1\ensuremath{''}$ |
| DM Tau outer C2H ring radius | ~350 | not stated | AU | 2 | At much greater distances (R $\sim 350$ AU) there is a weaker and thinner C$_2$H emission ring. |
| Gas density required for C2H emission | > 1e6 | not stated | cm^-3 | 5 | it seems clear that the emission arises from gas with at least moderate density $>$ 10$^6$ cm$^{-3}$. |

## Qualitative findings

- C2H rings lie at the edge of the mm-dust disk in both TW Hya and DM Tau; c-C3H2 shares the TW Hya ring  
  > "In each case the emission ring is found to arise at the edge of the observable disk of mm-sized grains (pebbles) traced by (sub)mm-wave continuum emission." (abstract)

## Claim tuples

- H: Hydrocarbon rings arise from dust evolution (settling, drift) that raises UV penetration and the C/O ratio | E: Thermo-chemical models with dust stratification and varied C/O compared to ALMA C2H maps | R: Stratification alone underpredicts emission; C/O ≳ 1 and UV-dominated outer disk needed, matching within factor 1.5 | F: Grain motions lead to hydrocarbon-rich chemistry in surface layers and outer disk | **supported**
- H: High dust optical depth explains the ring/hole structure | E: Compare ring positions with literature optical depth | R: Outer rings lie where dust is optically thin | F: A chemical abundance effect, not optical depth, causes the rings | **supported**
- H: Photodissociation of carbonaceous grains could supply C2H | E: Equilibrium abundance estimate and time-dependent model | R: Equilibrium abundance ~5e-10 vs ~1e-7 needed unless oxygen is depleted | F: Carbon extraction from CO with O depletion is more likely | **partially**

## Reasoning

- Why this data: _not stated_
- Why this method: _not stated_
- Alternative: High dust optical depth rejected as sole cause of ring; photodissociation of a-C:H/PAH as carbon source disfavored  
  > "Thus, the outer ring is not an effect of dust optical depth" (3.3 Dust Optical Depth and Ring Structure)
- How they decided it was enough: _not stated_
- Limitation (authors): Depletion parameterization is somewhat arbitrary; DM Tau inner hole not modelled; outer ring sharpness not matched  
  > "This parameterization is somewhat arbitrary" (5.1 Source Specific Models)
- Caveat (inferred, ours): Models tuned by eye with no formal fit or uncertainty on parameters
- Caveat (inferred, ours): Same UV field assumed for both stars
- Caveat (inferred, ours): DM Tau inner ring ambiguous between optical depth and chemistry
- Caveat (inferred, ours): Distance to DM Tau uncertain

## Reproducibility

- Data public (paper): ALMA project 2013.1.00198.S cited; public status not explicitly stated  
  > "under the project code ADS/JAO.ALMA#2013.1.00198.S." (2 Observations)
- Products in archive: _not stated_
- Missing: Thermo-chemical code not released/available
- Missing: Self-calibration and imaging details
- Missing: Chemical network details
- Missing: Model fit procedure
- Data volume (inferred): tens of GB
- Score (inferred): 3/5, Observations and imaging are described moderately, but the model is non-public and best-fit selection is heuristic.
- Rediscovery candidate: no, Main results depend on a proprietary thermo-chemical model with heuristic tuning; only the line fluxes and ring geometry are redoable.

## Links

- Method: Du & Bergin 2014 (cite: Du14) (Thermo-chemical model used)
- Method: Du, Bergin & Hogerheijde 2015 (cite: Du15) (Disk model and TW Hya template)
- Companion: Kastner et al. 2015 (cite: Kastner15) (SMA detection of C2H ring in TW Hya)
- Companion: Zhang et al. 2016 (cite: Zhang16) (Continuum visibility modelling of the same DM Tau data)

## Checks

```json
{
 "quotes": 65,
 "quotes_ok": 65,
 "quote_pass_rate": 1.0,
 "quotes_too_long": 0,
 "unsupported_facts": 0,
 "project_codes": 1,
 "codes_not_in_text": [],
 "codes_not_in_obscore": [],
 "obscore_codes_not_in_card": [],
 "codes_printed_but_missing": [],
 "numeric_results": 9,
 "numeric_problems": 0,
 "fill": {
  "facts": 79,
  "stated": 48,
  "rate": 0.608
 },
 "evidence_ok": true
}
```
