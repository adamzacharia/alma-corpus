# Hidden or missing outflows in highly obscured galaxy nuclei?

`2019A&A...623A..29F` | Astronomy and Astrophysics 2019 | first author: Falstad, N. | arXiv: 1901.06723 | DOI: 10.1051/0004-6361/201834586

Card schema 1.0 | model claude-sonnet-5-5 | depth light | type archival_reuse

## Science

- Fields: nearby_galaxies, agn_and_quasars
- Question: Is there a connection between strong HCN-vib emission and the development of feedback (outflows traced by far-IR OH 119 um) in (U)LIRGs?  
  > "We aim to investigate if there is a connection between the presence of strong HCN-vib emission and the development of feedback in (ultra) luminous infrared galaxies ((U)LIRGs)." (abstract)
- Target **IRAS 05189-2524**: coordinates _not stated_; z/distance z = 0.0428; D_L = 180.2 Mpc  
  > "| IRAS 05189-2524 | Sy 2 | $0.0428$ | $180.2\pm12.4$ | $13.50\pm1.85$ |" (Table 1); distance from redshift ~0.0428 from CO J=1-0 (San91); cosmology H0=73  
  > "| IRAS 05189-2524 | Sy 2 | $0.0428$ | $180.2\pm12.4$ | $13.50\pm1.85$ |" (Table 1)
- Target **IRAS 12224-0624**: coordinates _not stated_; z/distance z = 0.0264; D_L = 119.5 Mpc  
  > "| IRAS 12224-0624 | L | $0.0264$ | $119.5\pm8.2$ | $1.98\pm0.27$ |" (Table 1); distance from _not stated_

## Data provenance

- ALMA projects: 2015.1.00708.S, 2016.1.00140.S, 2015.1.01448.S
- bands: _not stated_
- frequencies and spectral setup: IRAS 05189-2524: one SPW at 341.8 GHz, 1.875 GHz bandwidth, 3.9 MHz resolution; IRAS 12224-0624: SPW at 347.4 GHz, same bandwidth/resolution  
  > "A spectral window centered at $341.8$ GHz covered a bandwidth of $1.875$ GHz" (Previously unpublished HCN-vib detections); "A spectral window centered at $347.4$ GHz covered a bandwidth of $1.875$ GHz" (Previously unpublished HCN-vib detections)
- continuum bandwidth: _not stated_
- arrays: _not stated_
- configurations: _not stated_
- baselines: IRAS 05189-2524: 15.1 m-1.0 km (42 antennas); IRAS 12224-0624: 15.1-452.8 m (38 antennas)  
  > "with a total of $42$ antennas with baseline lengths ranging between $15.1$ m and $1.0$ km" (Previously unpublished HCN-vib detections); "with a total of $38$ antennas with baseline lengths ranging between $15.1$ m and $452.8$ m" (Previously unpublished HCN-vib detections)
- angular resolution: 0.29"x0.22" (PA~63 deg) and 0.51"x0.44" (PA~82 deg)  
  > "The resulting beam size is $0.29\ensuremath{''}\,\times\,0.22\ensuremath{''}$ (PA ${\sim}63\ensuremath{^\circ}$)." (Previously unpublished HCN-vib detections)
- max recoverable scale: _not stated_
- sensitivity: 0.5 mJy/beam per 20 km/s (IRAS 05189-2524); 1.5 mJy/beam per 20 km/s (IRAS 12224-0624)  
  > "the final sensitivity achieved was $0.5$ mJy beam$^{-1}$ per $20$ km s$^{-1}$" (Previously unpublished HCN-vib detections); "the final sensitivity achieved was $1.5$ mJy beam$^{-1}$ per $20$ km s$^{-1}$" (Previously unpublished HCN-vib detections)
- time on source: 3340 s (IRAS 05189-2524); 395 s (IRAS 12224-0624)  
  > "The total on-source time of the observations was $3340$ s" (Previously unpublished HCN-vib detections); "The total on-source time of the observations was $395$ s" (Previously unpublished HCN-vib detections)
- observing dates: 2016 Nov 12 and 15 (IRAS 05189-2524); 2016 Apr 27 (IRAS 12224-0624)  
  > "conducted during two runs on 2016 November 12 and 15" (Previously unpublished HCN-vib detections); "conducted during a single run on 2016 April 27" (Previously unpublished HCN-vib detections)
- pi or archival as stated: _not stated_
- Line: HCN-vib v2=1 J=4-3 (also J=3-2 in other sources) (not stated)
- Other facility **Herschel PACS**: OH 119 um absorption median velocities (v50) for sample  
  > "checked for observations of the far-infrared OH doublet at $119$ $\mu$m with the *Herschel* Space Observatory" (2 Sample)
- Other facility **SMA, PdBI, NOEMA**: published HCN-vib observations for some sources  
  > "we have included published HCN-vib observations taken with the Plateau de Bure Interferometer (PdBI), the Northern Extended Millimeter Array (NOEMA), or the Submillimeter Array (SMA)" (2 Sample)
- External data: OH 119 um median velocities and OH sample  
  > "the 43 sources in the far-infrared OH sample of (cite: vei13) have been checked" (2 Sample) [from (cite: vei13)]
- External data: HCN-vib data for the other sources  
  > "data for the remaining thirteen were taken from (cite: sak10; aal15a; aal15b; ima16a; ima16b; mar16; pri17; ala18)" (2 Sample) [from (cite: sak10; aal15a; aal15b; ima16a; ima16b; mar16; pri17; ala18)]

## Processing

### Calibration

- pipeline or manual: CASA used to reapply the calibration  
  > "package was used to reapply the calibration and perform imaging" (Previously unpublished HCN-vib detections)
- casa version: _not stated_
- pipeline version: _not stated_
- archive products used as is: _not stated_
- flux calibrator: _not stated_
- flux scale uncertainty: _not stated_
- self calibration: _not stated_

### Imaging

- task: _not stated_
- deconvolver: _not stated_
- weighting robust: Briggs, robust = 0.5  
  > "For the imaging we used Briggs weighting with a robustness factor of 0.5." (Previously unpublished HCN-vib detections)
- uv taper: _not stated_
- cell size: _not stated_
- image size: _not stated_
- masking: _not stated_
- multiscale scales: _not stated_
- continuum subtraction: _not stated_
- line free channels: _not stated_
- primary beam correction: _not stated_
- array combination: _not stated_
- smoothing: 20 km/s channels  
  > "per $20$ km s$^{-1}$ (${\sim}24$ MHz) channel" (Previously unpublished HCN-vib detections)
- final beam: _not stated_
- final rms: _not stated_

### Inherited from earlier work

- OH 119 um doublet fitting procedure  
  > "the profiles of the $119$ $\mu$m OH doublets were modeled using the same procedure as in (cite: vei13)" (New OH outflow measurements) [from (cite: vei13)]

### Not stated but needed to reproduce (our reading)

- Calibrator names (stripped from text)
- CASA version
- Line-free channels / continuum subtraction
- Image size and cell size
- Flux calibration uncertainty
- Integration ranges for line fluxes
- L_IR sources and literature v50 values

## Analysis recipe

1. **Measure HCN-vib line flux in new ALMA data**: Gaussian fits to HCO+ and HCN-vib in spatially integrated spectra  
  > "fitting Gaussians to the HCO$^{+}$ and HCN-vib lines in spectra that were spatially integrated over the sources" (Previously unpublished HCN-vib detections)
   - software: CASA
   - fitting: _not stated_
   - validation: _not stated_
2. **Derive OH 119um median velocity for new sources**: Two-Gaussian doublet fits after order-2 polynomial continuum subtraction  
  > "Each line was fitted with two Gaussian components characterized by their amplitude, position, and width." (New OH outflow measurements)
   - software: PySpecKit
   - parameter: doublet separation fixed at 0.208 um  
  > "The separation between the two lines of the doublet was fixed at $0.208$ $\mu$m in the rest frame" (New OH outflow measurements)
   - fitting: _not stated_
   - validation: _not stated_
3. **Compute HCN-vib luminosities and L_HCN-vib/L_IR**: Solomon & Vanden Bout Eq. 1; 3 sigma upper limits for non-detections; J=4-3 divided by 2.5 with extra 20% uncertainty when only it is available  
  > "we have therefore divided its luminosity by $2.5$ and included it in the plot with an extra $20\%$ uncertainty added in quadrature" (3 Results)
   - assumption: H0=73, Om=0.27, OL=0.73  
  > "a $H_{0} =73$ km s$^{-1}$ Mpc$^{-1}$, $\Omega_{\mathrm{m}} = 0.27$, and $\Omega_{\Lambda} = 0.73$ cosmology is adopted" (1 Introduction)
   - fitting: _not stated_
   - validation: _not stated_

## Software

- **CASA** : reapply calibration and image archival ALMA data  
  > "package was used to reapply the calibration and perform imaging" (Previously unpublished HCN-vib detections)
- **PySpecKit** : fit OH 119 um doublets  
  > "The fitting procedure was carried out using the spectroscopic analysis toolkit *PySpecKit*" (New OH outflow measurements)
- **HIPE** 14.0.1: Herschel point-source correction extraction  
  > "the *Herschel* interactive processing environment (cite: ott10) version 14.0.1" (New OH outflow measurements)

## Numeric results

| quantity | value | uncertainty | units | step | quote |
|---|---|---|---|---|---|
| L_HCN-vib/L_IR IRAS 05189-2524 (J=4-3) | 0.59e-8 | 0.18e-8 | dimensionless | 3 | / IRAS 05189-2524 / $8.0\pm2.7$ / $0.59\pm0.18$ / $-387\ensuremath{^{d}}$ / ALMA / 9 / |
| L_HCN-vib/L_IR IRAS 12224-0624 (J=4-3) | 8.52e-8 | 1.95e-8 | dimensionless | 3 | / IRAS 12224-0624 / $16.9\pm4.5$ / $8.52\pm1.95$ / not obs. / ALMA / 9 / |
| J=4-3 to J=3-2 luminosity ratio mean | 2.5 | range 2-3 | dimensionless | 3 | the luminosity ratio between the $J=4\text{--}3$ and $J=3\text{--}2$ lines lies in the range $2\text{--}3$, with a mean of $2.5$ |

## Qualitative findings

- Sources with L_HCN-vib/L_IR above 1e-8 all lack fast OH outflows  
  > "the sources with high $L_{\mathrm{HCN-vib}}/L_{\mathrm{IR}}$ ratios, in excess of $10^{-8}$, all lack fast outflows" (3 Results)

## Claim tuples

- H: Strongest HCN-vib emitters lack wide-angle outflows in far-IR OH | E: Compare L_HCN-vib/L_IR with OH 119um v50 in 17 (U)LIRGs | R: High-ratio sources all have slow or positive v50 | F: Most HCN-vib luminous nuclei do not drive wide-angle outflows detectable in OH; may trace pre-feedback phase | **supported**

## Reasoning

- Why this data: _not stated_
- Why this method: _not stated_
- Alternative: Orientation effects, hidden/collimated outflows, and intrinsic differences (starburst-dominated) considered as explanations  
  > "One is that there are no outflows, another that the outflows are hidden from detection" (4.1 Why do the HCN-vib luminous galaxies lack outflow signatures)
- How they decided it was enough: _not stated_
- Limitation (authors): Heterogeneous sample; possible selection biases  
  > "Admittedly, our sample is quite heterogeneous" (4.1 Why do the HCN-vib luminous galaxies lack outflow signatures)
- Caveat (inferred, ours): Small heterogeneous sample, no statistical test of correlation
- Caveat (inferred, ours): Total L_IR may not match nuclear luminosity
- Caveat (inferred, ours): Mixed instruments and literature calibrations

## Reproducibility

- Data public (paper): ALMA archival data public  
  > "have the data publicly available in the the ALMA science archive" (2 Sample)
- Products in archive: _not stated_
- Missing: Literature HCN-vib fluxes and OH v50 values from many papers
- Missing: CASA version and imaging details
- Data volume (inferred): ~10-50 GB for the two ALMA datasets
- Score (inferred): 3/5, Mostly compilation of literature values; only two archival datasets reprocessed with partial details.
- Rediscovery candidate: no, Result relies mainly on literature compilation, not a redoable ALMA recipe.

## Links

- Method: (cite: vei13) (OH 119um fitting procedure and median velocity definition)
- Companion: (cite: aal15b) (Earlier HCN-vib vs outflow trend this paper tests)

## Checks

```json
{
 "quotes": 44,
 "quotes_ok": 44,
 "quote_pass_rate": 1.0,
 "quotes_too_long": 0,
 "unsupported_facts": 0,
 "project_codes": 3,
 "codes_not_in_text": [],
 "codes_not_in_obscore": [
  "2015.1.01448.S"
 ],
 "obscore_codes_not_in_card": [],
 "codes_printed_but_missing": [],
 "numeric_results": 3,
 "numeric_problems": 0,
 "fill": {
  "facts": 68,
  "stated": 30,
  "rate": 0.441
 },
 "evidence_ok": true
}
```
