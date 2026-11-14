# CO, Water, and Tentative Methanol in η Carinae Approaching Periastron

`2020ApJ...892L..23M` | The Astrophysical Journal Letters 2020 | first author: Morris, Patrick W. | arXiv: 2002.11053 | DOI: 10.3847/2041-8213/ab784a

Card schema 1.0 | model claude-sonnet-5-5 | depth full | type observational_alma_primary

## Science

- Fields: evolved_stars, astrochemistry, stellar_physics
- Question: Is methanol present around the evolved massive binary eta Carinae, what are its physical conditions and abundance relative to water, and how does CO (2-1) trace the equatorial torus before periastron?  
  > "We report the basic physical parameters indicated by the methanol gas, contrast the location and conditions indicated by $^{12}$CO $J=2-1$ and possibly water" (Introduction)
- Target **eta Carinae**: coordinates _not stated_; z/distance 2.35 kpc  
  > "0.01 pc at a distance of 2.35 kpc; Smith 2006" (Introduction); distance from Smith 2006  
  > "0.01 pc at a distance of 2.35 kpc; Smith 2006" (Introduction)

## Data provenance

- ALMA projects: 2018.A.00026.S, 2013.1.00661.S
- bands: Band 6, tuned to 12CO and 13CO J=2-1  
  > "the Band 6 receiver tuned to two frequencies, one for each of the $^{12}$CO and $^{13}$CO $J = 2-1$ lines" (2.1 ALMA Observations)
- frequencies and spectral setup: 1.875 GHz bandwidth (~2500 km/s) in 128 channels; 12CO tuning included H30alpha baseband; continuum baseband near each line  
  > "The correlators were configured for 1.875 GHz bandwidth ($\approx$2500 km s$^{-1}$) in 128 channels." (2.1 ALMA Observations)
- continuum bandwidth: _not stated_
- arrays: 12m main array, 43 to 48 antennae  
  > "using 43 to 48 antennae of the 12m main array with a maximum separation of 350m" (2.1 ALMA Observations)
- configurations: _not stated_
- baselines: _not stated_
- angular resolution: 0.58" x 0.46"  
  > "A synthesized angular resolution ${\theta}_{\rm{maj}} \times {\theta}_{\rm{min}}$ = 0.$''$58 $\times$ 0.$''$46 was achieved" (2.1 ALMA Observations)
- max recoverable scale: _not stated_
- sensitivity: 0.8 mJy over 40 km/s channels  
  > "at a line sensitivity $\sigma_{\rm{rms}}$ of 0.8 mJy over 40 km s$^{-1}$" (3 CO (2-1) emission in the Homunculus)
- time on source: _not stated_
- observing dates: 2019 March 11 and April 27 (12CO); March 29 and April 18 (13CO); orbit phase 0.83-0.85  
  > "on 2019 March 11 and April 27 for $^{12}$CO, and on 2019 March 29 and April 18 for $^{13}$CO" (2.1 ALMA Observations)
- pi or archival as stated: _not stated_
- Line: 12CO J=2-1 (230.5380 GHz)
- Line: CH3OH 10_2-9_3 A- vt=0 (231.2811 GHz)
- Other facility **Herschel/HIFI**: H2O 557 and 988 GHz spectral scans; CS line searches  
  > "The 2009 data are from a HIFI observing mode calibration program spectral scan in Mixer Band 1b (obsid 1342181171)" (2.2 Herschel/HIFI Observations)
- Other facility **Herschel/SPIRE FTS**: Comparison spectrum to verify HIFI features  
  > "comparison of our spectrum taken with the Fourier Transform Spectrometer (FTS) on the *Herschel* Spectral and Photometric Imaging Receiver" (5.1 Identifications and uncertainties)
- External data: Mean N(H2) = 3.0e22 cm^-2 for abundances  
  > "a mean column density $N$(H$_2$) = 3.0 $\times$ 10$^{22}$ cm$^{-2}$ is adopted from previous observational work" (2.3 Theoretical methods) [from (cite: 2006ApJ...644.1151S)]
- External data: Initial Gaussian deconvolution of CO velocity components and HIFI CO modeling  
  > "the LSR velocities and line widths are set based on an initial Gaussian deconvolution" (2.3 Theoretical methods) [from (cite: 2017ApJ...842...79M)]
- External data: CH3OH collisional rates  
  > "with updated collisional rates for CH$_3$OH (cite: 2004MNRAS.352...39P)" (4.3 Physical conditions) [from (cite: 2004MNRAS.352...39P)]

## Processing

### Calibration

- pipeline or manual: _not stated_
- casa version: CASA 5.4.0-70  
  > "were all carried out in CASA 5.4.0-70" (2.1 ALMA Observations)
- pipeline version: _not stated_
- archive products used as is: _not stated_
- flux calibrator: J1032-5917 (bandpass and flux)  
  > "The ALMA calibrator J1032-5917 was used in the bandpass and flux calibrations" (2.1 ALMA Observations)
- flux scale uncertainty: 5%  
  > "yielding an estimated 5% uncertainty on the intensity scale" (2.1 ALMA Observations)
- self calibration: _not stated_

### Imaging

- task: CASA clean on continuum-subtracted cube  
  > "Final image construction in each channel was done using the CASA “clean” algorithm on the continuum-subtracted cube." (2.1 ALMA Observations)
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
- final beam: 0.58" x 0.46"  
  > "0.$''$58 $\times$ 0.$''$46 was achieved" (2.1 ALMA Observations)
- final rms: _not stated_

### Inherited from earlier work

- Radiative transfer modeling approach (as for HIFI CO/13CO)  
  > "following an approach similar to that described in our analysis of $^{12}$CO and $^{13}$CO lines observed with HIFI" (2.3 Theoretical methods) [from (cite: 2017ApJ...842...79M)]
- HIFI data processing details  
  > "details of the processing have been given where the calibration and Open Time observations have been included in a study" (2.2 Herschel/HIFI Observations) [from (cite: 2017ApJ...842...79M)]

### Not stated but needed to reproduce (our reading)

- tclean/clean parameters (weighting, robust, cell, image size, masks, threshold)
- line-free channels used for continuum subtraction
- whether archival 2013.1.00661.S (2015) data were reprocessed and how
- RADEX grids for density, collision partner densities and line widths
- spectral extraction aperture details beyond table notes
- exact HIFI line-free baseline ranges

## Analysis recipe

1. **Calibrate and image ALMA CO cubes**: Calibration in CASA, continuum subtraction, clean per channel  
  > "Final image construction in each channel was done using the CASA “clean” algorithm on the continuum-subtracted cube." (2.1 ALMA Observations)
   - software: CASA
   - fitting: _not stated_
   - validation: _not stated_
2. **Extract spectra and convert to brightness temperature**: Core 2" and Butterfly 10" apertures; T_B from flux density using beam conversion  
  > "The Core spectra are extracted over an aperture 2$''$ in diameter." (Table 1)
   - fitting: _not stated_
   - validation: Compared 2015 and 2019 CO intensities  
  > "in 2015 and 2019 are in close agreement at of 43 $\pm$4 K km s$^{-1}$" (3 CO (2-1) emission in the Homunculus)
3. **Derive Tex and column densities of CO and CH3OH**: Synthetic spectra from RADEX, best agreement weighted by baseline RMS; LTE start with non-LTE cross-checks; layered components  
  > "We have computed line intensities with combinations of excitation temperature $T_{\rm{ex}}$ and column density $N$ that yield the best agreement with the observed profiles" (2.3 Theoretical methods)
   - software: RADEX
   - parameter: Emission Tex grid 50-1200 K in 50 K steps; absorption 5-25 K in 2 K and 30-100 K in 5 K steps  
  > "Emission profiles are computed over the temperature range 50 K $\leq$ $T_{\rm{ex}}$ $\leq$ 1200 K in 50 K intervals." (2.3 Theoretical methods)
   - assumption: N(H2)=3.0e22 cm^-2; methanol source size 1", CO 4"  
  > "We will later show that ${\theta}_s$(CH$_3$OH) = 1$''$ can be adopted for the methanol gas" (2.2 Herschel/HIFI Observations)
   - fitting: _not stated_
   - validation: Compared with HIFI higher-J CO modeling  
  > "The CO $J=2-1$ intensity profile is in good agreement with modeling predictions for $^{12}$CO and $^{13}$CO $J = 5-4$ through $9-8$ lines observed with HIFI" (3 CO (2-1) emission in the Homunculus)
4. **Model HIFI water lines and OPR**: RADEX profiles of 557 GHz line, same Tex range applied to 988 GHz para line; beam-dilution correction with source size  
  > "we first compute synthetic profiles of the 557 GHz line using the RADEX code over a range of $N$($o$-H$_2$O) and $T_{\rm{ex}}$" (5.2 Synthetic profiles)
   - software: RADEX
   - assumption: _not stated_
   - fitting: _not stated_
   - validation: Compared HIFI with SPIRE FTS spectrum; predicted 987 GHz methanol line checked  
  > "The correspondence of features is excellent down to the lowest intensity features resolved with SPIRE" (5.1 Identifications and uncertainties)

## Software

- **CASA** 5.4.0-70: Calibration and clean imaging  
  > "were all carried out in CASA 5.4.0-70" (2.1 ALMA Observations)
- **RADEX** : Radiative transfer excitation and column density modeling  
  > "calculated using the RADEX radiative transfer code" (2.3 Theoretical methods)

## Numeric results

| quantity | value | uncertainty | units | step | quote |
|---|---|---|---|---|---|
| CH3OH warm emission gas temperature | 700 | 100 | K | 3 | 90.0          / 183.0 (5.0)     / 700 (100)      / 60.0 (15.0) |
| CH3OH warm emission column density | 60.0e16 | 15.0e16 | cm^-2 | 3 | 90.0          / 183.0 (5.0)     / 700 (100)      / 60.0 (15.0) |
| CH3OH absorption temperature | 110 | 30 | K | 3 | 8.0           / $-$121.0 (3.0)  / 110 (30)       / 12.0 (4.0) |
| CH3OH absorption column density | 12.0e16 | 4.0e16 | cm^-2 | 3 | 8.0           / $-$121.0 (3.0)  / 110 (30)       / 12.0 (4.0) |
| CO Butterfly gas temperature | 155 | 20 | K | 3 | 17.3 (0.5)      / 155 (20)       / 4.7 (1.0) |
| Water ortho-to-para ratio | 2.3 | 0.4 | dimensionless | 4 | The OPR of the water emission in $\eta$ Car is estimated to be 2.3 $\pm$0.4 |
| CH3OH absorption optical depth | 0.08 | 0.01 | dimensionless | 3 | The absorption line has an indicated optical depth $\tau \approx$ 0.08 $\pm$0.01 |
| CH3OH/H2O abundance ratio | >10^3 | not stated | dimensionless | 4 | The measured CH$_3$OH/H$_2$O abundance ratio is greater than 10$^3$ |

## Qualitative findings

- CO traces the disrupted equatorial torus in three velocity components, with little CO toward the central source  
  > "very little CO emission is detected towards the bright central source, which is marked instead by narrow absorption over the continuum emitting region" (3 CO (2-1) emission in the Homunculus)

## Claim tuples

- H: Methanol exists in the compact core of eta Car | E: ALMA 231 GHz feature identification plus RADEX modeling | R: Hot (~700 K) emission and cool (~110 K) absorption within ~2" | F: Probable first methanol detection around an evolved massive star; 13CS less favored | **partially**
- H: Water is present in eta Car | E: HIFI 557 and 988 GHz spectral scans | R: o-H2O ~5-6 sigma, p-H2O ~3 sigma; abundance ~1e-9 | F: Water detected at low abundance | **partially**
- H: Methanol formed by ice desorption | E: Compare CH3OH/H2O ratio | R: Ratio >10^3 vs few percent for ice mantles | F: Fischer-Tropsch-type catalysis on dust proposed | **partially**

## Reasoning

- Why this data: CO tracks nebular response around periastron; methanol found in archival check of CO variability  
  > "discovered during our investigations with archival ALMA observations to gage variability of CO around periastron passage" (Introduction)
- Why this method: _not stated_
- Alternative: 13CS J=5-4 as carrier rejected based on velocity and distribution  
  > "The CH$_3$OH identification is a better match to the observations" (4.1 Identification)
- How they decided it was enough: _not stated_
- Limitation (authors): Methanol identification rests on a single line  
  > "The identification is presently limited to this feature" (4.1 Identification)
- Caveat (inferred, ours): Single-line identification; other CH3OH lines not detected
- Caveat (inferred, ours): Hot component temperature depends on assumed source size and single-component fits
- Caveat (inferred, ours): Water p-H2O detection only ~3 sigma
- Caveat (inferred, ours): Abundances rely on mean unresolved N(H2)

## Reproducibility

- Data public (paper): ALMA programs cited; Herschel obsids given  
  > "This paper makes use of the following ALMA data: ADS/JAO.ALMA #2018.A.00026.S and ADS/JAO.ALMA #2013.1.00661.S." (Acknowledgments)
- Products in archive: _not stated_
- Missing: clean parameters
- Missing: line-free channels
- Missing: RADEX input grids and densities
- Missing: aperture centers
- Data volume (inferred): tens of GB for ALMA plus small HIFI spectra
- Score (inferred): 3/5, Data identifiable and public but imaging and modeling parameters are sparsely given.
- Rediscovery candidate: no, Imaging settings and model details incomplete; results involve judgment-based fits.

## Links

- Method: (cite: 2007A&A...468..627V) (RADEX)
- Method: (cite: 2017ApJ...842...79M) (HIFI processing and radiative transfer approach)
- Companion: (cite: 2018MNRAS.474.4988S) (Earlier ALMA CO observations of the torus)
- Companion: (cite: 2019MNRAS.490.1570B) (ALMA CO 4-3 and HCN observations)

## Checks

```json
{
 "quotes": 53,
 "quotes_ok": 53,
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
  "facts": 70,
  "stated": 37,
  "rate": 0.529
 },
 "evidence_ok": true
}
```
