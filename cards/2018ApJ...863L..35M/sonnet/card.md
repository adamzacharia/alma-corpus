# First Results of an ALMA Band 10 Spectral Line Survey of NGC 6334I: Detections of Glycolaldehyde (HC(O)CH<SUB>2</SUB>OH) and a New Compact Bipolar Outflow in HDO and CS

`2018ApJ...863L..35M` | The Astrophysical Journal Letters 2018 | first author: McGuire, Brett A. | arXiv: 1808.05438 | DOI: 10.3847/2041-8213/aad7bb

Card schema 1.0 | model claude-sonnet-5-5 | depth full | type observational_alma_primary

## Science

- Fields: star_formation, astrochemistry
- Question: What do ALMA Band 10 observations of NGC 6334I reveal about thermal water in the MM1B outflow, and can high-energy glycolaldehyde lines be detected and used to constrain excitation, compared with Herschel HIFI?  
  > "A bright, bipolar north-south outflow is seen in HDO and CS emission, driven by the embedded massive protostar MM1B." (abstract)
- Target **NGC 6334I**: coordinates 17h20m53.3s, -35d46m59.0s (MM1 phase center, J2000)  
  > "relatively small heliocentric distance of 1.3 kpc (cite: Reid:2014km; Chibueze2014)" (Introduction); "with a phase center of $\alpha$(J2000) = 17$^{\rm{h}}$20$^{\rm{m}}$53.3$^{\rm{s}}$ $\delta$(J2000) = $-35^{\circ}$46$'$59.0$''$" (Observations & Data Reduction); z/distance 1.3 kpc  
  > "relatively small heliocentric distance of 1.3 kpc (cite: Reid:2014km; Chibueze2014)" (Introduction); "with a phase center of $\alpha$(J2000) = 17$^{\rm{h}}$20$^{\rm{m}}$53.3$^{\rm{s}}$ $\delta$(J2000) = $-35^{\circ}$46$'$59.0$''$" (Observations & Data Reduction); distance from Reid et al. 2014; Chibueze et al. 2014  
  > "relatively small heliocentric distance of 1.3 kpc (cite: Reid:2014km; Chibueze2014)" (Introduction); "with a phase center of $\alpha$(J2000) = 17$^{\rm{h}}$20$^{\rm{m}}$53.3$^{\rm{s}}$ $\delta$(J2000) = $-35^{\circ}$46$'$59.0$''$" (Observations & Data Reduction)

## Data provenance

- ALMA projects: 2017.1.00717.S, 2017.1.00661.S, 2015.A.00022.T
- bands: Band 10 (~880 GHz, 0.35 mm); Band 7 and Band 4 complementary  
  > "The 0.35 mm continuum was created from (relatively) line-free channels" (Observations & Data Reduction)
- frequencies and spectral setup: _not stated_
- continuum bandwidth: 2.7 GHz aggregate, rms 50 mJy/beam  
  > "has an aggregate bandwidth and rms noise of 2.7 GHz and 50 mJy beam$^{-1}$, respectively" (Observations & Data Reduction)
- arrays: _not stated_
- configurations: nominal C43-3, 40 antennas, max baseline 532 m  
  > "with 40 ALMA antennas in the array in a nominal C43-3 configuration with a maximum baseline of 532 m" (Observations & Data Reduction)
- baselines: _not stated_
- angular resolution: 0.21'' x 0.15'' (robust 0.5)  
  > "providing a 0.21$''$ $\times$ 0.15$''$ synthesized beam (robust weighting parameter = 0.5)" (Observations & Data Reduction)
- max recoverable scale: _not stated_
- sensitivity: 62 mJy/beam in 0.5 km/s channels  
  > "resulting in an RMS noise level of 62 mJy beam$^{-1}$ in 0.5 km s$^{-1}$ channels" (Observations & Data Reduction)
- time on source: 47 minutes  
  > "Total time on source was 47 minutes" (Observations & Data Reduction)
- observing dates: 05 April 2018 (Band 10)  
  > "The Band 10 observation occurred 05 April 2018" (Observations & Data Reduction)
- pi or archival as stated: _not stated_
- Line: HDO 1_{1,1}-0_{0,0} (893.6 GHz)
- Line: HDO 6_{2,4}-5_{3,3} (895.9 GHz)
- Line: CS J=18-17 (880.9 GHz)
- Other facility **Herschel HIFI**: Archival spectral line survey (ObsID 1342192328) for comparison  
  > "obtained from the *Herschel* Science Archive, ObsID 1342192328" (Observations & Data Reduction)
- Other facility **VLA**: cm-wavelength water maser positions  
  > "By overlaying the locations of cm-wavelength masers from the VLA data" (HDO and CS)
- External data: Laboratory spectroscopy of glycolaldehyde to 1.2 THz used for simulation  
  > "high-frequency laboratory work of (cite: Carroll:2010gt) that extended the measured frequencies from 354 GHz to 1.2 THz" (Spectral Line Survey & Glycolaldehyde) [from (cite: Carroll:2010gt)]
- External data: MM1B N-S outflow extent 6.2'' and dynamical time 166 yr from ALMA CS(6-5)  
  > "total linear extent of $6.2\ensuremath{''}$ (8060 au) for MM1B N-S" (HDO and CS) [from (cite: Brogan18)]

## Processing

### Calibration

- pipeline or manual: _not stated_
- casa version: _not stated_
- pipeline version: _not stated_
- archive products used as is: _not stated_
- flux calibrator: J1517-2422 (flux and bandpass); J1733-3722 phase  
  > "J1517-2422 ($\sim$1.85 Jy at 880 GHz) was used as the flux and bandpass calibration source" (Observations & Data Reduction)
- flux scale uncertainty: _not stated_
- self calibration: Self-calibration on continuum, applied to line data after uv-plane continuum subtraction  
  > "Self-calibration was performed on the continuum and applied to the spectral line data after subtracting the continuum in the uv-plane." (Observations & Data Reduction)

### Imaging

- task: _not stated_
- deconvolver: _not stated_
- weighting robust: robust = 0.5  
  > "synthesized beam (robust weighting parameter = 0.5)" (Observations & Data Reduction)
- uv taper: _not stated_
- cell size: _not stated_
- image size: _not stated_
- masking: _not stated_
- multiscale scales: _not stated_
- continuum subtraction: uv-plane subtraction, method of Brogan et al. 2018  
  > "The method employed for continuum subtraction is described in detail in (cite: Brogan18)." (Observations & Data Reduction)
- line free channels: _not stated_
- primary beam correction: _not stated_
- array combination: _not stated_
- smoothing: Bands 4, 7, 10 convolved to common 0.26'' x 0.26''  
  > "all convolved to the smallest common synthesized beam size of 0.26$''$$\times$0.26$''$" (Spectral Line Survey & Glycolaldehyde)
- final beam: _not stated_
- final rms: _not stated_

### Inherited from earlier work

- Continuum subtraction method  
  > "The method employed for continuum subtraction is described in detail in (cite: Brogan18)." (Observations & Data Reduction) [from (cite: Brogan18)]
- Band 7 data description  
  > "The details of the complementary Band 7 data used in this paper are described in (cite: McGuire:2017gy)" (Observations & Data Reduction) [from (cite: McGuire:2017gy)]

### Not stated but needed to reproduce (our reading)

- CASA version and pipeline/manual calibration details
- Imaging task, cell size, image size, deconvolver, masks
- Line-free channels and self-calibration parameters
- Exact spectral setup for Band 10
- Software used for spectral simulation
- Source size/beam-filling assumed in glycolaldehyde model and continuum temperature per frequency
- Line identification and counting criteria for 695 vs 65 lines

## Analysis recipe

1. **Extract spectra at MM1 position**: Single-pixel spectrum at offset position ~400 au west of MM1B  
  > "spectra were extracted toward MM1 from a single pixel at a position of" (Observations & Data Reduction)
   - fitting: _not stated_
   - validation: _not stated_
2. **Simulate glycolaldehyde spectrum across Bands 4,7,10**: Single-Tex LTE formalism of Turner 1991 including background continuum, Planck scale conversion to Jy/beam, compared by eye  
  > "We therefore used the formalism described in (cite: Turner:1991um) to simulate the spectrum of across the entire $\sim$750 GHz span in observational coverage" (Spectral Line Survey & Glycolaldehyde)
   - parameter: Tex=135 K, dV=3.2 km/s, N=1.3e17 cm-2  
  > "$T_{\rm{ex}}$ = 135 K), linewidth ($\Delta V$ = 3.2 km s$^{-1}$), and column density ($N_T$ = $1.3\times10^{17}$ cm$^{-2}$)" (Spectral Line Survey & Glycolaldehyde)
   - assumption: Single Tex because high density (n_H>1e6 cm-3)  
  > "suggest that molecules should be well-described by a single $T_{\rm{ex}}$" (Spectral Line Survey & Glycolaldehyde)
   - fitting: No formal fit; zeroth-order match  
  > "well reproduces the observed emission to zeroth order" (Spectral Line Survey & Glycolaldehyde)
   - validation: Visual overlay on observed spectra in three bands  
  > "Figure [4](#gly) shows the resulting simulated emission overlaid on the observational data in Bands 4, 7, and 10." (Spectral Line Survey & Glycolaldehyde)

## Software

- **Astropy** : Python analysis  
  > "Astropy, a community-developed core Python package for Astronomy" (Acknowledgments)
- **APLpy** : plotting  
  > "APLpy, an open-source plotting package for Python" (Acknowledgments)

## Numeric results

| quantity | value | uncertainty | units | step | quote |
|---|---|---|---|---|---|
| System temperature | 926 | not stated | K at 880 GHz | 0 | the average resulting system temperature was $T_{\rm{Sys}}$ = 926 K at 880 GHz |
| Glycolaldehyde excitation temperature | 135 | not stated | K | 2 | $T_{\rm{ex}}$ = 135 K |
| Glycolaldehyde column density | 1.3e17 | not stated | cm-2 | 2 | $N_T$ = $1.3\times10^{17}$ cm$^{-2}$ |
| Number of lines ALMA vs HIFI | 695 vs 65 | not stated | lines | 0 | 695 vs 65 lines in the ALMA vs HIFI spectra over the same range |

## Qualitative findings

- Masers lie along outflow cavity walls where high-velocity gas impacts surroundings  
  > "The maser locations are shown to correspond to the sites along the outflow cavity walls where high velocity gas impacts the surrounding material." (abstract)

## Claim tuples

- H: Does a bipolar outflow from MM1B appear in HDO and CS, and relate to water masers? | E: Mapped high-velocity HDO and CS, overlaid VLA masers | R: N-S bipolar outflow; masers on cavity walls | F: Masers trace impact sites of the outflow | **supported**
- H: Does ALMA Band 10 resolve more line structure than HIFI? | E: Compared spectra over same range | R: 695 vs 65 lines | F: Order of magnitude more lines; glycolaldehyde detected | **supported**

## Reasoning

- Why this data: _not stated_
- Why this method: _not stated_
- How they decided it was enough: _not stated_
- Limitation (authors): Full spectral fit including blends is beyond scope; lab data lacking at high frequency  
  > "A full fit of the spectrum, including line contamination and blending from other species, is beyond the scope of this first-look paper." (Spectral Line Survey & Glycolaldehyde)
- Caveat (inferred, ours): Tex/N not fitted with uncertainties
- Caveat (inferred, ours): Only one pointing observed
- Caveat (inferred, ours): Line identification reliability at extrapolated frequencies

## Reproducibility

- Data public (paper): _not stated_
- Products in archive: _not stated_
- Missing: Calibration/imaging parameters
- Missing: Spectral simulation code
- Missing: Line list for 695 lines
- Data volume (inferred): ~100-300 GB across three bands
- Score (inferred): 3/5, Data identified by project codes, but processing and fitting details are sparse.
- Rediscovery candidate: no, Excitation analysis is non-quantitative and imaging details are missing.

## Links

- Method: (cite: Brogan18) (Continuum subtraction method)
- Method: (cite: Turner:1991um) (Spectral simulation formalism)
- Companion: (cite: McGuire:2017gy) (Band 7 data)
- Related: CHESS Herschel HIFI survey

## Checks

```json
{
 "quotes": 48,
 "quotes_ok": 48,
 "quote_pass_rate": 1.0,
 "quotes_too_long": 0,
 "unsupported_facts": 0,
 "project_codes": 3,
 "codes_not_in_text": [],
 "codes_not_in_obscore": [
  "2017.1.00661.S",
  "2015.A.00022.T"
 ],
 "obscore_codes_not_in_card": [],
 "codes_printed_but_missing": [],
 "numeric_results": 4,
 "numeric_problems": 0,
 "fill": {
  "facts": 61,
  "stated": 32,
  "rate": 0.525
 },
 "evidence_ok": true
}
```
