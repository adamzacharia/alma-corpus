# Line Ratios Reveal N<SUB>2</SUB>H<SUP>+</SUP> Emission Originates above the Midplane in TW Hydrae

`2019ApJ...876L..13S` | The Astrophysical Journal Letters 2019 | first author: Schwarz, Kamber R. | arXiv: 1904.09303 | DOI: 10.3847/2041-8213/ab1b0d

Card schema 1.0 | model claude-sonnet-5-5 | depth full | type observational_alma_primary

## Science

- Fields: protoplanetary_disks, astrochemistry
- Question: At what gas temperature do the N2H+ 1-0 and 4-3 lines emit in TW Hya, and does the emission trace the midplane CO snowline?  
  > "We conclude that the N$_{2}$H$^+$ emission in TW Hya is not emitting from near the midplane, but rather from higher in the disk" (abstract)
- Target **TW Hya**: coordinates _not stated_; z/distance _not stated_; distance from _not stated_

## Data provenance

- ALMA projects: 2016.1.00592.S, 2011.0.00340.S
- bands: Band 3 (N2H+ 1-0); 4-3 data from archival project  
  > "The ALMA Band 3 observations targeting N$_{2}$H$^+$ J = 1-0 where obtained on 2016 October 2 with 42 antennas" (Observations)
- frequencies and spectral setup: _not stated_
- continuum bandwidth: _not stated_
- arrays: _not stated_
- configurations: _not stated_
- baselines: _not stated_
- angular resolution: 1-0: 0.62'' x 0.49''; 4-3: 0.63'' x 0.59''  
  > "resulting in a $0.62\ensuremath{''}$ $\times$ $0.49\ensuremath{''}$ beam" (Observations); "The final image has a synthesized beam of $0.63\ensuremath{''}$ $\times$ $0.59\ensuremath{''}$" (Observations)
- max recoverable scale: _not stated_
- sensitivity: 1-0: 2.2 K per 0.1 km/s channel; 4-3: 0.71 K per 0.1 km/s channel  
  > "a per channel rms noise level of 2.2 K per 0.1 km s$^{-1}$ channel" (Observations); "a per channel rms noise level of 0.71 K per 0.1 km s$^{-1}$ channel" (Observations)
- time on source: _not stated_
- observing dates: 2016 October 2 (1-0)  
  > "obtained on 2016 October 2 with 42 antennas" (Observations)
- pi or archival as stated: 1-0 new (PI Schwarz); 4-3 archival (PI Qi)  
  > "Additionally, we use archival observations of the N$_{2}$H$^+$ J = 4-3 transition (2011.0.00340.S, PI: C. Qi)." (Observations)
- Line: N2H+ J = 1-0 (not stated)
- Line: N2H+ J = 4-3 (not stated)
- External data: Disk physical and kinematic properties from CS analysis, used for deprojection  
  > "assuming the physical and kinematic properties derived from previous analysis of the CS emission in TW Hya (cite: Teague18b)" (Analysis) [from (cite: Teague18b)]
- External data: CO freeze-out temperature of 21 K and 13CO temperature profile  
  > "At the relevant radii in TW Hya the freeze out temperature is expected to be 21 K (cite: Schwarz16)." (Analysis) [from (cite: Schwarz16)]

## Processing

### Calibration

- pipeline or manual: _not stated_
- casa version: CASA v4.7.0  
  > "The data were calibrated and imaged using `CASA v4.7.0`." (Observations)
- pipeline version: _not stated_
- archive products used as is: _not stated_
- flux calibrator: _not stated_
- flux scale uncertainty: _not stated_
- self calibration: Phase and amplitude self-calibration on continuum, applied to line spw (1-0 data)  
  > "Phase and amplitude self-calibration were performed on the continuum and applied to the line spectral window." (Observations)

### Imaging

- task: _not stated_
- deconvolver: _not stated_
- weighting robust: natural weighting (1-0)  
  > "The line data were imaged using natural weighting" (Observations)
- uv taper: _not stated_
- cell size: _not stated_
- image size: _not stated_
- masking: _not stated_
- multiscale scales: _not stated_
- continuum subtraction: CASA uvcontsub  
  > "Continuum subtraction was performed using the `CASA` task `uvcontsub`." (Observations)
- line free channels: _not stated_
- primary beam correction: _not stated_
- array combination: _not stated_
- smoothing: _not stated_
- final beam: 1-0: 0.62'' x 0.49''; 4-3: 0.63'' x 0.59''  
  > "The final image has a synthesized beam of $0.63\ensuremath{''}$ $\times$ $0.59\ensuremath{''}$" (Observations)
- final rms: _not stated_

### Inherited from earlier work

- 4-3 data reduction  
  > "For a detailed discussion of the data reduction we refer the reader to (cite: Qi13b)." (Observations) [from (cite: Qi13b)]
- Stacking method for Keplerian disks  
  > "we employ the stacking method for Keplerian disks introduced by (cite: Yen16)" (Analysis) [from (cite: Yen16)]

### Not stated but needed to reproduce (our reading)

- Disk geometry and stellar mass values used in eddy deprojection
- Annulus widths for stacking
- Line-free channels and uvcontsub fit order
- tclean parameters, cell and image size for 1-0 cube
- Hyperfine components and frequencies used for integration
- Integration velocity range
- How the 4-3 data were processed beyond Qi13b
- Details of how the 39 K and 2 K uncertainty were computed (hyperfine treatment, error propagation)

## Analysis recipe

1. **Upper limit from image plane**: Upper limit RMS x sqrt(Nchan) x dv for 1-0 non-detection  
  > "the upper limit is RMS$\times \sqrt{N_{chan}}\time \delta v$ and $\delta v = 1.5$ km s$^{-1}$ is the line width based on the 4-3 data" (Analysis)
   - fitting: _not stated_
   - validation: _not stated_
2. **Stack spectra in annuli**: Deproject annuli to system velocity and stack (Yen16 method)  
  > "the image cube is divided into concentric annuli, which are each de-projected to the system velocity" (Analysis)
   - software: eddy
   - parameter: Ring 0.8'' to 2''  
  > "Figure [1](#spectra) shows the averaged spectrum for a ring from 0.8 to 2$''$" (Analysis)
   - fitting: _not stated_
   - validation: _not stated_
3. **Check optical depth from hyperfine ratios**: Hyperfine line ratios relative to 1_{2,3}-0_{1,2}; gives tau>1 (1.5 to 66), judged unreliable due to low S/N  
  > "A more likely explanation is that the signal-to-noise remains too poor to use the relative strength of the hyperfine components to constrain the optical depth." (Analysis)
   - fitting: _not stated_
   - validation: _not stated_
4. **Derive excitation temperature**: LTE ratio of integrated intensities of 4-3 and 1-0  
  > "Assuming LTE, the ratio of the integrated intensities can be used to measure the excitation temperature (cite: Goldsmith99)" (Analysis)
   - assumption: Optically thin emission, LTE  
  > "These brightness temperatures are well below this value and thus the emission is assumed to be optically thin." (Analysis)
   - fitting: _not stated_
   - validation: Compared with 13CO temperature of 21 K and disk models  
  > "the 21 K from $^{13}$CO provides an upper limit for the midplane temperature at these radii" (Discussion)

## Software

- **CASA** 4.7.0: calibration, imaging, uvcontsub  
  > "The data were calibrated and imaged using `CASA v4.7.0`." (Observations)
- **eddy** : annulus deprojection and spectral stacking  
  > "Using the package `eddy` (cite: eddy) the image cube is divided into concentric annuli" (Analysis)

## Numeric results

| quantity | value | uncertainty | units | step | quote |
|---|---|---|---|---|---|
| Excitation temperature of N2H+ emitting gas, 0.8-2'' | 39 | 2 K (1 sigma) | K | 4 | Using these values we find an excitation temperature of 39 K, with a one sigma uncertainty of 2 K. |
| Integrated intensity 1-0 (ring-averaged) | 5.1 | 0.2 | K km/s | 2 | $5.1\pm0.2$ K km s$^{-1}$ for the 1-0 transition |
| Integrated intensity 4-3 (ring-averaged) | 28.7 | 0.8 | K km/s | 2 | $28.7\pm0.8$ K km s$^{-1}$ for the 4-3 transition |
| 1-0 upper limit single hyperfine (image plane) | 2.7 | not stated | K km/s | 1 | upper limit on the integrated line intensity of 2.7 K km s$^{-1}$ for a single hyperfine component |
| Ring-averaged peak Tb 1-0 | 1.5 | 1 | K | 2 | $1.5\pm1$ K and $12\pm7$ K respectively |
| Ring-averaged peak Tb 4-3 | 12 | 7 | K | 2 | $1.5\pm1$ K and $12\pm7$ K respectively |

## Qualitative findings

- N2H+ emits from a surface layer bounded by photodissociation or chemical reprocessing, not a good midplane CO snowline tracer in TW Hya  
  > "it is clear that in this system N$_{2}$H$^+$ emission is not a good tracer of the CO snowline deeper in the disk" (Discussion)

## Claim tuples

- H: N2H+ emission in TW Hya originates near the cold midplane | E: LTE line ratio of ring-averaged 4-3 and 1-0 integrated intensities, 0.8-2'' | R: Excitation temperature 39 +/- 2 K versus midplane <20 K | F: N2H+ emits from a warmer surface layer above the midplane | **supported**

## Reasoning

- Why this data: _not stated_
- Why this method: _not stated_
- Alternative: Optically thick interpretation would imply gas colder than 2 K, deemed unlikely  
  > "implying that N$_{2}$H$^+$ is emitting from gas colder than 2 K" (Analysis)
- How they decided it was enough: _not stated_
- Limitation (authors): Low S/N prevents hyperfine optical depth constraint; radial variations in 4-3 intensity add uncertainty  
  > "Radial variations in the intensity of the 4-3 line within our annular bins likely contribute to the uncertainty for the ring-averaged peak brightness." (Analysis)
- Caveat (inferred, ours): LTE and optically thin assumptions untested given weak 1-0 detection
- Caveat (inferred, ours): Excitation temperature may not equal kinetic temperature at N2H+ critical densities
- Caveat (inferred, ours): Ring-averaging over 0.8-2'' mixes radii
- Caveat (inferred, ours): Different beams for the two lines

## Reproducibility

- Data public (paper): 4-3 data described as archival  
  > "we use archival observations of the N$_{2}$H$^+$ J = 4-3 transition" (Observations)
- Products in archive: _not stated_
- Missing: eddy deprojection parameters
- Missing: imaging parameters
- Missing: integration windows and error propagation
- Data volume (inferred): ~20-50 GB
- Score (inferred): 3/5, Short letter with public data and a simple calculation, but stacking and imaging parameters are missing.
- Rediscovery candidate: yes, Public data, simple line-ratio recipe, and numeric main result, though some settings are unstated.

## Links

- Method: (cite: Yen16) (Stacking method for Keplerian disks)
- Method: (cite: eddy) (Software used for stacking)
- Companion: (cite: Qi13b) (Source of the 4-3 data and reduction)
- Companion: (cite: vantHoff17) (Disk models of N2H+ emission)

## Checks

```json
{
 "quotes": 42,
 "quotes_ok": 42,
 "quote_pass_rate": 1.0,
 "quotes_too_long": 0,
 "unsupported_facts": 0,
 "project_codes": 2,
 "codes_not_in_text": [],
 "codes_not_in_obscore": [],
 "obscore_codes_not_in_card": [],
 "codes_printed_but_missing": [
  "2016.0.00592.S"
 ],
 "numeric_results": 6,
 "numeric_problems": 0,
 "fill": {
  "facts": 66,
  "stated": 28,
  "rate": 0.424
 },
 "evidence_ok": true
}
```
