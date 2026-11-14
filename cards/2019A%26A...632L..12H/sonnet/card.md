# Multiple nitrogen reservoirs in a protoplanetary disk at the epoch of comet and giant planet formation

`2019A&A...632L..12H` | Astronomy and Astrophysics 2019 | first author: Hily-Blant, P. | arXiv: 1911.06676 | DOI: 10.1051/0004-6361/201936750

Card schema 1.0 | model claude-sonnet-5-5 | depth full | type archival_reuse

## Science

- Fields: protoplanetary_disks, astrochemistry
- Question: Do HCN and CN trace distinct nitrogen isotopic reservoirs in the TW Hya disk, and does HCN/HC15N vary with radius (selective photodissociation)?  
  > "we aim at providing the requisite evidence for two distinct N reservoirs within the disk that orbits the nearby TTauri star TW Hya" (Introduction)
- Target **TW Hya**: coordinates _not stated_; z/distance 59.5±0.9 pc  
  > "we adopted a distance of 59.5$\pm$0.9 pc to TW Hya (cite: gaia2018)" (4 Results (Radially dependent fluxes)); distance from Gaia Collaboration 2018  
  > "we adopted a distance of 59.5$\pm$0.9 pc to TW Hya (cite: gaia2018)" (4 Results (Radially dependent fluxes))

## Data provenance

- ALMA projects: 2016.1.00629.S
- bands: _not stated_
- frequencies and spectral setup: HCN(4-3), H13CN(4-3), HC15N(4-3) at 354.5, 345.4, 344.2 GHz; 61 kHz (0.053 km/s) resolution; H13CN and HC15N in lower sideband, HCN in upper  
  > "at 354.5, 345.4, and 344.2 GHz, respectively, have been mapped with the ALMA interferometer with a spectral resolution of 61 KHz or 0.053 km s$^{-1}$" (Observations and data reduction)
- continuum bandwidth: _not stated_
- arrays: _not stated_
- configurations: _not stated_
- baselines: _not stated_
- angular resolution: _not stated_
- max recoverable scale: _not stated_
- sensitivity: 2.3, 1.9, 2.0 mJy/beam per 61 kHz channel (HCN, H13CN, HC15N)  
  > "The final sensitivities are 2.3, 1.9, and 2.0 mJy/beam per 61 kHz channel for HCN, H, and HC respectively." (Observations and data reduction)
- time on source: _not stated_
- observing dates: six epochs, 2016 Dec 30 and 2017 July 5, 10, 15, 21, 22  
  > "were spread over six epochs (2016 December 30, 2017 July 5, 2017 July 10, 2017 July 15, 2017 July 21, and 2017 July 22)" (Observations)
- pi or archival as stated: Archival; PI I. Cleeves  
  > "based on archival ALMA data (2016.1.00629.S, Cleeves et al)" (Introduction)
- Line: HCN 4-3 (354505.477 MHz (reference))
- Line: H13CN 4-3 (345339.770 MHz)
- Line: HC15N 4-3 (344200.109 MHz)
- External data: TW Hya disk density/temperature model used to bound density  
  > "Referring to the TW Hya model of (cite: vanthoff2017), this upper limit indicates that the density is at these radii higher than" (4 Isotopic ratios) [from van't Hoff et al. 2017 (cite: vanthoff2017)]
- External data: Local ISM 12C/13C of 65±10  
  > "is significantly higher than the / ratio of $65\pm10$ in the local ISM (cite: halfen2017)" (Discussion) [from Halfen et al. 2017 (cite: halfen2017)]
- External data: PSN 12C/13C of 89±1  
  > "agrees surprisingly well with the value of 89$\pm1$ in the PSN (cite: clayton2004)" (Discussion) [from Clayton & Nittler 2004 (cite: clayton2004)]
- External data: CN/C15N = 323±30 in TW Hya  
  > "CN/C in the TW Hya system yielded a significantly higher ratio, 323$\pm$30 (Paper I)" (Introduction) [from Paper I (Hily-Blant et al. 2017)]

## Processing

### Calibration

- pipeline or manual: Standard CASA pipeline, then self-calibration in Gildas  
  > "The standard pipeline of CASA 5.4.0 was used to generate the complex visibilities, which were then self-calibrated in Gildas" (Observations and data reduction)
- casa version: CASA 5.4.0  
  > "The standard pipeline of CASA 5.4.0 was used to generate the complex visibilities" (Observations and data reduction)
- pipeline version: _not stated_
- archive products used as is: _not stated_
- flux calibrator: J1037-2934 (bandpass, flux, phase)  
  > "J1037-2934 was used as a bandpass, flux, and phase calibrator." (Observations)
- flux scale uncertainty: 10% amplitude calibration error included  
  > "uncertainties on the absolute flux include a conservative 10% error (statistical) from amplitude calibration" (4 Isotopic ratios)
- self calibration: Applied in Gildas; details not given  
  > "Self-calibration was then applied to generate the final set of visibilities." (Observations)

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

- Kinetic temperature upper limit from line width method  
  > "They are used to infer an upper limit on the kinetic temperature following Paper I and (cite: teague2016)." (Radially dependent line width) [from Paper I; Teague et al. 2016 (cite: teague2016)]

### Not stated but needed to reproduce (our reading)

- Imaging parameters (weighting, robust, cell, image size, beam) not given
- Self-calibration solution intervals and reference model
- Which array configurations/execution blocks were combined
- Continuum subtraction and line-free channels
- Gaussian fit details and Keplerian mask construction details beyond threshold
- Disk inclination and position angle used for radii
- Details of ALICO collisional rate inputs

## Analysis recipe

1. **Calibrate and self-calibrate visibilities**: CASA pipeline, export to Gildas, self-calibration  
  > "exported into the Gildas format using the Gildas-Casa filer of Guilloteau, Chapillon et al." (Observations)
   - software: CASA, Gildas
   - fitting: _not stated_
   - validation: _not stated_
2. **Spatially averaged line fluxes in Keplerian masks**: Mask where HCN 354507.455 MHz hf line >40 mJy/beam per channel, exclude r<0.3''; average spectra; Gaussian fit weak hf lines; HCN flux = average corrected by 4.2% relative intensity  
  > "selecting the disk area where the 354507.455 MHz hyperfine emission of HCN is higher than 40 mJy/beam in each velocity channel" (4.1 Spatially averaged line fluxes)
   - software: Gildas
   - parameter: threshold 40 mJy/beam; r>0.3''  
  > "we further masked out the spectra located at radii smaller than 0.3$''$" (4.1 Spatially averaged line fluxes)
   - assumption: Optically thin lines, equal excitation temperature, flux ratio = column density ratio within 1%  
  > "their rotational flux ratios are equal to their column density ratios to within 1%, provided the lines are optically thin and have the same excitation temperature" (5 Isotopic ratios)
   - fitting: Gaussian fitting  
  > "were measured through Gaussian fitting" (4.1 Spatially averaged line fluxes)
   - validation: Opacity corrections tau/(1-exp(-tau)) tested; HCN/H13CN near constant  
  > "the almost constant HCN/H suggests that these lines are instead optically thin" (5 Isotopic ratios)
3. **Radial profile of isotopic ratios**: Combine Keplerian and annular masks, 5 au wide annuli from 5 to 55 au in 5 au steps, rms-weighted averaging, Gaussian fits; power law fit to HCN/HC15N  
  > "Spectra contained within concentric annuli, centered at radii $r=5$ to 55 au in steps of 5 au" (4.2 Radially dependent fluxes)
   - software: Gildas
   - parameter: distance 59.5 pc  
  > "we adopted a distance of 59.5$\pm$0.9 pc to TW Hya" (4.2 Radially dependent fluxes)
   - fitting: Power law to HCN/HC15N  
  > "The best fit of a power law to the HCN/HC gives 117$\pm$10$\times(r/20\,\au)^{1.3\pm0.13}$" (5 Isotopic ratios)
   - validation: Ratios change <4% excluding three central channels  
  > "The ratios change by less than 4% when the three central Keplerian channels are excluded." (5 Isotopic ratios)
4. **Test single excitation temperature assumption**: 1D ALICO non-LTE calculations with hf overlap, densities and 5-30 K; FWHM-based upper limit on Tkin ~35 K  
  > "we used our 1D ALICO code to investigate the density and kinetic gas temperature at which departures from the single excitation temperature assumption may be obtained" (Single excitation temperature assumption)
   - software: ALICO
   - assumption: Uniform physical conditions  
  > "Our calculations assume uniform physical conditions" (5 Isotopic ratios)
   - fitting: _not stated_
   - validation: Density from van't Hoff model implies thermalization  
  > "This validates our basic assumption." (5 Isotopic ratios)

## Software

- **CASA** 5.4.0: Standard pipeline to generate visibilities  
  > "The standard pipeline of CASA 5.4.0 was used to generate the complex visibilities" (Observations and data reduction)
- **Gildas** : Self-calibration  
  > "which were then self-calibrated in Gildas" (Observations and data reduction)
- **ALICO** : 1D non-LTE excitation with hf overlap  
  > "we used our 1D ALICO code" (Single excitation temperature assumption)

## Numeric results

| quantity | value | uncertainty | units | step | quote |
|---|---|---|---|---|---|
| Average HCN/HC15N | 223 | 21 | dimensionless | 2 | /     Average /   223$\pm$21   /   86$\pm$4    / 2.6$\pm$0.2 / |
| Average HCN/H13CN | 86 | 4 | dimensionless | 2 | /     Average /   223$\pm$21   /   86$\pm$4    / 2.6$\pm$0.2 / |
| HCN/HC15N at 20 au | 121.4 | 10.6 | dimensionless | 3 | / $r$ (au)=20 / 121.4$\pm$10.6 / 85.6$\pm$ 5.2 / 1.4$\pm$0.1 / |
| HCN/HC15N at 45 au | 338.7 | 28.2 | dimensionless | 3 | /          45 / 338.7$\pm$28.2 / 82.5$\pm$ 4.2 / 4.2$\pm$0.4 / |
| Power-law fit to HCN/HC15N | 117×(r/20 au)^1.3 | ±10 amplitude, ±0.13 index | dimensionless | 3 | The best fit of a power law to the HCN/HC gives 117$\pm$10$\times(r/20\,\au)^{1.3\pm0.13}$ |
| Upper limit kinetic temperature at r>=35 au | ~35 K | not stated | K | 4 | places an upper limit on the kinetic temperature of $(FWHM/2.35)^2\times\mu \mh/(2k_B)\approx$35 K |

## Qualitative findings

- HCN/HC15N increases with radius from ~121 at 20 au to the ~330 elemental value in the outer disk; HCN/H13CN is constant  
  > "the increasing HCN/HC from 121 up to the bulk value in the outer disk supports a scenario in which a single reservoir of interstellar, not fractionated, nitrogen dominates at large radii" (Discussion)

## Claim tuples

- H: CN and HCN trace distinct 15N isotopic reservoirs in TW Hya | E: Measured HCN/HC15N from ALMA hf lines and compared with CN/C15N | R: Average HCN/HC15N 223±21 vs CN/C15N 323±30 | F: At least two isotopic nitrogen reservoirs exist in the disk | **supported**
- H: Selective photodissociation drives radial gradient of HCN/HC15N | E: Radial profile of ratio from masked annuli | R: Ratio rises from 121 (20 au) to ~339 (45 au) | F: Consistent with selective photodissociation of N2, but dedicated TW Hya models needed | **partially**

## Reasoning

- Why this data: _not stated_
- Why this method: _not stated_
- Alternative: Optically thick HCN weak hf lines as cause of low central-channel ratios; found opacity ~0.3, still thin  
  > "which is not entirely negligible, but still fulfills our optically thin assumption" (5 Isotopic ratios)
- How they decided it was enough: _not stated_
- Limitation (authors): Detailed 2D radiative transfer not done; ratio beyond 55 au tentative  
  > "In the present context, we were unable to make detailed calculations like this." (Single excitation temperature assumption)
- Caveat (inferred, ours): Single-Tex assumption justified only via generic 1D models and linewidth limit; Visser models imply it may fail
- Caveat (inferred, ours): Radial values at large r rest on a weak HC15N detection
- Caveat (inferred, ours): Opacity effects of 0.3-0.75 could bias ratios
- Caveat (inferred, ours): Keplerian masking filters extended emission

## Reproducibility

- Data public (paper): Archival ALMA data 2016.1.00629.S  
  > "This study makes use of the ADS/JAO.ALMA#2016.1.00629.S data." (Acknowledgements)
- Products in archive: _not stated_
- Missing: Self-calibration parameters
- Missing: Imaging parameters and beam
- Missing: Mask and Gaussian fitting details
- Missing: Disk geometry used for radii
- Data volume (inferred): ~50-200 GB raw (six epochs, high spectral resolution Band 7)
- Score (inferred): 4/5, Public data and clear flux-ratio recipe with tabulated results, but imaging and self-calibration settings are unspecified.
- Rediscovery candidate: yes, Public data, numeric results tabulated, simple measurement recipe, though some processing details missing.

## Links

- Method: Teague et al. 2016 (cite: teague2016) (Kinetic temperature upper limit from line width)
- Companion: Paper I, Hily-Blant et al. 2017 (cite: hilyblant2017) (CN/C15N in TW Hya)

## Checks

```json
{
 "quotes": 50,
 "quotes_ok": 50,
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
  "facts": 70,
  "stated": 37,
  "rate": 0.529
 },
 "evidence_ok": true
}
```
