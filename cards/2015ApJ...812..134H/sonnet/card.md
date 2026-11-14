# The Early ALMA View of the FU Ori Outburst System

`2015ApJ...812..134H` | The Astrophysical Journal 2015 | first author: Hales, A. S. | arXiv: 1509.02543 | DOI: 10.1088/0004-637X/812/2/134

Card schema 1.0 | model claude-sonnet-5-5 | depth full | type observational_alma_primary

## Science

- Fields: protoplanetary_disks, star_formation
- Question: Do the FU Ori binary components host disks, how massive and large are they, and is there a large envelope or circumbinary reservoir feeding the outburst?  
  > "Clearly, resolving the source and determining the mass is key." (Introduction); "to measure the link between the inner disk instability and the outer disk through sub-mm continuum and molecular line observations" (abstract)
- Target **FU Ori (N and S binary components)**: coordinates Gaussian 1 (05:45:22.36,+09.04.12.24); Gaussian 2 (05:45:22.37,+09.04.11.75)  
  > "at a distance of 450 pc (cite: 1977MNRAS.181..657M)" (FU Ori); "(05:45:22.36,+09.04.12.24)" (Table 1); z/distance 450 pc  
  > "at a distance of 450 pc (cite: 1977MNRAS.181..657M)" (FU Ori); "(05:45:22.36,+09.04.12.24)" (Table 1); distance from Murdin & Penston 1977  
  > "at a distance of 450 pc (cite: 1977MNRAS.181..657M)" (FU Ori); "(05:45:22.36,+09.04.12.24)" (Table 1)

## Data provenance

- ALMA projects: 2011.0.00538.S
- bands: Band 7  
  > "FU Ori Band 7 observations were acquired on December 2$^{nd}$ 2012 using 24 antennas." (Observations and data reduction)
- frequencies and spectral setup: FDM, four spectral windows of 468.75 MHz at 122 kHz resolution; three on 12CO 3-2, HCN 4-3, HCO+ 4-3, fourth continuum at 345.78359 GHz  
  > "The ALMA correlator was configured in the Frequency Division Mode (FDM) to provide 468.75 MHz bandwidth in each of four different spectral windows at 122 kHz ($\sim$0.1 km s$^{-1}$) resolution per channel." (Observations and data reduction)
- continuum bandwidth: 1.759 GHz centered at 351.33 GHz (line-free channels of all four spws)  
  > "adding to a total bandwidth of 1.759 GHz centered at 351.33 GHz" (Observations and data reduction)
- arrays: _not stated_
- configurations: _not stated_
- baselines: 15 to 381 m  
  > "The dataset provides baselines from 15 to 381 meters." (Observations and data reduction)
- angular resolution: 0.63" x 0.51" at PA = 3.0 deg (natural weighting)  
  > "Using natural weighting resulted in a synthesized beam size of 0.63$\ensuremath{''}\times$0.51$\ensuremath{''}$ at PA$=3.0$ degrees." (Observations and data reduction)
- max recoverable scale: _not stated_
- sensitivity: 25.0 mJy/beam per 0.22 km/s channel (12CO); continuum 0.64 mJy/beam, 0.31 after self-cal  
  > "an RMS noise level of 25.0 mJy beam$^{-1}$ per 0.22 km s$^{-1}$ channel was reached" (Observations and data reduction)
- time on source: 16.9 minutes  
  > "The total time spent on-source was 16.9 minutes." (Observations and data reduction)
- observing dates: December 2, 2012 (Cycle 0)  
  > "FU Ori Band 7 observations were acquired on December 2$^{nd}$ 2012 using 24 antennas." (Observations and data reduction)
- pi or archival as stated: _not stated_
- Line: 12CO J=3-2 (345.79599 GHz)
- Line: HCN J=4-3 (354.50547 GHz)
- Line: HCO+ J=4-3 (356.73424 GHz)
- External data: JCMT 850 and 450 um fluxes (66 and 400 mJy) and disk mass upper limit 0.02 Msun, used for comparison  
  > "a flux of 66 and 400  mJy at 850 and 450 $\mu$m, respectively" (FU Ori) [from (cite: 2001ApJS..134..115S)]
- External data: Stellar masses of FU Ori (0.3 Msun) and FU Ori S (1.2 Msun)  
  > "the masses of FU Ori and FU Ori S are 0.3 M$_{\odot}$, and 1.2 M$_{\odot}$ respectively" (Discussion) [from (cite: 2012AJ....143...55B)]

## Processing

### Calibration

- pipeline or manual: CASA, standard manual-style calibration (WVR, Tsys, bandpass, phase, amplitude)  
  > "in a standard fashion, which included offline Water Vapor Radiometer (WVR) calibration, system temperature correction, as well as bandpass, phase and amplitude calibrations." (Observations and data reduction)
- casa version: _not stated_
- pipeline version: _not stated_
- archive products used as is: _not stated_
- flux calibrator: Callisto  
  > "Callisto was observed as flux calibrator" (Observations and data reduction)
- flux scale uncertainty: 10 to 15%  
  > "the absolute flux calibration of the data is estimated to be accurate to within 10 to 15$\%$." (Observations and data reduction)
- self calibration: single iteration of phase-only self-calibration on continuum  
  > "After a single iteration of phase-only self-calibration the RMS of the continuum image was reduced to 0.31 mJy beam$^{-1}$." (Observations and data reduction)

### Imaging

- task: CLEAN in CASA  
  > "Imaging of the continuum and molecular emission lines was performed using the CLEAN task in CASA." (Observations and data reduction)
- deconvolver: _not stated_
- weighting robust: natural weighting  
  > "Using natural weighting resulted in a synthesized beam size" (Observations and data reduction)
- uv taper: _not stated_
- cell size: _not stated_
- image size: _not stated_
- masking: _not stated_
- multiscale scales: _not stated_
- continuum subtraction: in the visibility domain prior to line imaging  
  > "Continuum subtraction in the visibility domain was performed prior to imaging of each molecular line." (Observations and data reduction)
- line free channels: _not stated_
- primary beam correction: _not stated_
- array combination: _not stated_
- smoothing: _not stated_
- final beam: _not stated_
- final rms: continuum 0.31 mJy/beam after self-cal; 12CO 25.0 mJy/beam per 0.22 km/s  
  > "the RMS of the continuum image was reduced to 0.31 mJy beam$^{-1}$" (Observations and data reduction)

### Inherited from earlier work

- Dust mass formalism (optically thin, opacity)  
  > "we can compute a coarse estimate of the disks’ total masses (cite: 1990AJ.....99..924B)" (Discussion) [from (cite: 1990AJ.....99..924B)]

### Not stated but needed to reproduce (our reading)

- CLEAN cell size, image size, masks, threshold and iterations
- Line-free channel ranges used for continuum subtraction
- Velocity ranges for integrated line maps
- CASA version
- Self-calibration solution interval
- Which spectral windows/channels flagged
- Details of PV cut and moment-map settings

## Analysis recipe

1. **Image continuum and lines**: CLEAN of continuum (line-free channels of four spws) and of continuum-subtracted lines; one phase-only self-cal on continuum  
  > "CLEANing of the dust continuum was performed after combining the line-free channels from all four spectral windows" (Observations and data reduction)
   - software: CASA
   - parameter: natural weighting; beam 0.63"x0.51"  
  > "Using natural weighting resulted in a synthesized beam size of 0.63$\ensuremath{''}\times$0.51$\ensuremath{''}$ at PA$=3.0$ degrees." (Observations and data reduction)
   - fitting: _not stated_
   - validation: _not stated_
2. **Fit continuum components**: IMFIT with one and two Gaussian components; two unresolved sources fit well  
  > "Using two unresolved sources provides a much better fit to the observed emission (with residuals down to the image noise levels)." (Dust Continuum)
   - software: CASA IMFIT
   - fitting: 2-D Gaussians; single component fit rejected by residuals  
  > "inspection of the residual image shows that a single-component fit fails to match data." (Dust Continuum)
   - validation: residual image inspection  
  > "inspection of the residual image shows that a single-component fit fails to match data." (Dust Continuum)
3. **Derive disk dust masses**: optically thin dust mass from 854 um fluxes  
  > "the ALMA 854 $\mu$m fluxes correspond to disk dust masses of $2\times 10^{-4}$ M$_{\odot}$ and $8\times 10^{-5}$ M$_{\odot}$" (Discussion)
   - assumption: Td = 50 K, gas-to-dust 100, kappa(345 GHz) = 1.5 cm2/g, distance 450 pc, optically thin  
  > "Assuming a dust temperature of 50 K for the individual disks around FU Ori and FU Ori S, a gas-to-dust ratio of 100, and a 345 GHz dust opacity of 1.5 cm$^2\,$g$^{-1}$" (Discussion)
   - fitting: _not stated_
   - validation: discussed optical depth: disks marginally optically thick if mean T > 80 K  
  > "For the disks to be optically thick, the average disk dust temperature would have to be higher than 80 K." (Discussion)

## Software

- **CASA** : calibration, CLEAN imaging, IMFIT  
  > "All the data were calibrated using the *Common Astronomy Software Applications* package (cite: 2007ASPC..376..127M)" (Observations and data reduction)
- **Astropy** : acknowledged as used in the research  
  > "This research made use of Astropy, a community-developed core Python package for Astronomy" (Acknowledgments)

## Numeric results

| quantity | value | uncertainty | units | step | quote |
|---|---|---|---|---|---|
| Continuum flux, north component | 50.1 | 0.3 | mJy | 2 | The total fluxes of each component are 50.1$\pm 0.3$ mJy and 21.2$\pm 0.4$ mJy respectively. |
| Continuum flux, south component | 21.2 | 0.4 | mJy | 2 | The total fluxes of each component are 50.1$\pm 0.3$ mJy and 21.2$\pm 0.4$ mJy respectively. |
| Dust mass north / south | 2e-4 / 8e-5 | not stated | Msun | 3 | disk dust masses of $2\times 10^{-4}$ M$_{\odot}$ and $8\times 10^{-5}$ M$_{\odot}$ |
| Disk radius upper limit | <45 | not stated | AU | 2 | the disks must have radial sizes smaller than 0.1” (45 AU) |
| Integrated 12CO 3-2 flux | 31.61 | 0.12 | Jy km/s | 1 | 31.61$\pm 0.12$, 2.14$\pm 0.07$ and 0.37$\pm 0.07$ Jy km s$^{-1}$ respectively |
| Integrated HCO+ 4-3 flux | 2.14 | 0.07 | Jy km/s | 1 | 31.61$\pm 0.12$, 2.14$\pm 0.07$ and 0.37$\pm 0.07$ Jy km s$^{-1}$ respectively |
| Integrated HCN 4-3 flux | 0.37 | 0.07 | Jy km/s | 1 | 31.61$\pm 0.12$, 2.14$\pm 0.07$ and 0.37$\pm 0.07$ Jy km s$^{-1}$ respectively |
| Circumbinary ring dust mass limit (3 sigma, 20 K) | <1.9e-4 | not stated | Msun | 3 | the ring would need to have a dust mass smaller than $1.9\times 10^{-4}$M$_{\odot}$ to remain undetected by our observations |

## Qualitative findings

- 12CO is widespread and more extended than continuum; HCO+ peaks near FU Ori S; HCN peaks near FU Ori  
  > "The denser gas tracer HCO$^{+}$ peaks close to the position of the southern binary component, while HCN appears peaked at the position of the northern component." (abstract)

## Claim tuples

- H: Is there a large envelope around FU Ori? | E: Compare ALMA flux with single-dish fluxes | R: ALMA recovers entire single-dish flux | F: No large envelope | **supported**
- H: Do both binary components host disks and which is more massive? | E: Two-Gaussian fit and optically thin mass | R: Two unresolved sources; north 2e-4, south 8e-5 Msun | F: Most massive disk orbits the less massive star, under equal-temperature assumptions | **partially**
- H: Does the molecular gas distribution differ between components? | E: Integrated line maps | R: HCO+ peaks near south, HCN near north | F: South component embedded in denser material | **partially**

## Reasoning

- Why this data: _not stated_
- Why this method: _not stated_
- Alternative: Single-component Gaussian fit rejected in favour of two components  
  > "a single-component fit fails to match data." (Dust Continuum)
- How they decided it was enough: _not stated_
- Limitation (authors): Disks unresolved; interaction between disks cannot be disentangled; line data cannot resolve velocity gradients; cloud contamination in 12CO central channels  
  > "At this angular resolution any interaction between the two unresolved disk components cannot be disentangled." (abstract); "There is significant cloud contamination in the central channels" (Line emission)
- Caveat (inferred, ours): Mass ordering depends on assumed equal dust temperature and optical thinness
- Caveat (inferred, ours): Gaussian-fit sizes for unresolved sources give only upper limits
- Caveat (inferred, ours): 12CO is contaminated by foreground cloud; Keplerian rotation claim is tentative
- Caveat (inferred, ours): Project code in text (00538) differs from archive link (00548)

## Reproducibility

- Data public (paper): _not stated_
- Products in archive: _not stated_
- Missing: CLEAN parameters and masks
- Missing: line-free channel ranges
- Missing: CASA version
- Missing: integration velocity ranges
- Data volume (inferred): ~10-30 GB (single Cycle 0 execution)
- Score (inferred): 3/5, Short single-dataset analysis with simple recipe, but imaging parameters and CASA version are missing.
- Rediscovery candidate: no, Public status not stated in the paper, and imaging details are incomplete.

## Links


## Checks

```json
{
 "quotes": 57,
 "quotes_ok": 57,
 "quote_pass_rate": 1.0,
 "quotes_too_long": 0,
 "unsupported_facts": 0,
 "project_codes": 1,
 "codes_not_in_text": [],
 "codes_not_in_obscore": [
  "2011.0.00538.S"
 ],
 "obscore_codes_not_in_card": [
  "2011.0.00548.S"
 ],
 "codes_printed_but_missing": [],
 "numeric_results": 8,
 "numeric_problems": 0,
 "fill": {
  "facts": 62,
  "stated": 36,
  "rate": 0.581
 },
 "evidence_ok": true
}
```
