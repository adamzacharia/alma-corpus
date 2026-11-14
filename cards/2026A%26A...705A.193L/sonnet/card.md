# Zooming into the water snow line: High-resolution water observations of the HL Tau disk

`2026A&A...705A.193L` | Astronomy and Astrophysics 2026 | first author: Leemker, M. | arXiv: 2511.16737 | DOI: 10.1051/0004-6361/202557609

Card schema 1.0 | model claude-sonnet-5-5 | depth full | type observational_alma_primary

## Science

- Fields: protoplanetary_disks, astrochemistry
- Question: Where is the water snowline in HL Tau, and how much of the water reservoir is hidden by optically thick dust at ALMA versus mid/far-IR wavelengths?  
  > "We aim to spatially resolve the water emission in the HL Tau disk using high resolution ALMA observations of the 183 GHz line ($E_u = 205$ K)." (abstract)
- Target **HL Tau**: coordinates _not stated_; z/distance 140 pc  
  > "HL Tau is a massive Class I/II protoplanetary disk of 0.2 $M_{\odot}$ surrounded by a protostellar envelope at a distance of 140 pc" (Introduction); distance from Rebull2004; Robitaille2007; Furlan2008; Galli2018; Booth2020  
  > "HL Tau is a massive Class I/II protoplanetary disk of 0.2 $M_{\odot}$ surrounded by a protostellar envelope at a distance of 140 pc" (Introduction)

## Data provenance

- ALMA projects: 2017.1.01178.S, 2022.1.00905.S, 2021.1.01310.S, 2017.1.01562.S
- bands: Band 5 (183 GHz) and Band 7 (321 GHz)  
  > "the line at 183 GHz in ALMA Band 5" (2 Observations)
- frequencies and spectral setup: _not stated_
- continuum bandwidth: 2.4 GHz short baseline, 4.2 GHz long baseline  
  > "total continuum bandwidth of 2.4 GHz for the short baseline and 4.2 GHz for the long baseline data" (2 Observations)
- arrays: _not stated_
- configurations: _not stated_
- baselines: SB 15-1398 m; LB 83-11886 m  
  > "| 2017.1.01178.S | SB 0 | 15-1398 | 1.6 | 0.2 |" (Table 1)
- angular resolution: 0.083" x 0.066" for 183 GHz at robust 0.0  
  > "spatial resolution of $0.083\ensuremath{''} \times 0.066\ensuremath{''}\ (-21.0\degree)$" (2.1 Imaging)
- max recoverable scale: 1.7" for the long baseline data  
  > "maximum recoverable scale of $1.7\ensuremath{''}$ of the long baseline data" (3.1 Moment maps and integrated fluxes)
- sensitivity: _not stated_
- time on source: _not stated_
- observing dates: _not stated_
- pi or archival as stated: _not stated_
- Line: H2O 3_{1,3}-2_{2,0} (183.310 GHz)
- Line: H2O 10_{2,9}-9_{3,6} (321.226 GHz)
- Line: H13CO+ J=2-1 (173.507 GHz)
- Line: SO 4_4-3_3 (172.181 GHz)
- Other facility **Herschel**: far-IR water line fluxes (from literature)  
  > "| *Herschel* | -1.52 | 194 | 15 | \< 153 | 1.78% | 3 |" (Table 3)
- Other facility **Gemini North**: mid-IR highly excited water line fluxes (from Salyk2019)  
  > "4. (cite: RiviereMarichalar2012), and 5. (cite: Salyk2019)" (Table 3)
- External data: Herschel PACS water line fluxes  
  > "3. (cite: AlonsoMartinez2017)" (Table 3) [from AlonsoMartinez2017; RiviereMarichalar2012]
- External data: Gemini North mid-IR water line fluxes  
  > "5. (cite: Salyk2019)" (Table 3) [from Salyk2019]
- External data: H13CO+ J=3-2 radial profile at 321.852 GHz  
  > "the $J=3-2$ emission at 321.852 GHz presented in (cite: Booth2020)" (4.4) [from Booth2020]
- External data: 325 GHz water line flux  
  > "| 325.150 | 922.01 | ALMA | -4.94 | 470 | 11 | 1.33 $\pm$ 0.09 | 35.42% | 1 |" (Table 3) [from Facchini2024]
- Simulation/model as data: DALI thermochemical model of HL Tau full disk (0.2 Msun, rc 30 au) used for the tau_dust=1 surface and visible water fractions  
  > "The disk is modelled using the thermo-chemical modelling code DALI" (Thermochemical model)

## Processing

### Calibration

- pipeline or manual: _not stated_
- casa version: CASA 6.5.4  
  > "We used `CASA` version 6.5.4" (2 Observations)
- pipeline version: _not stated_
- archive products used as is: _not stated_
- flux calibrator: J0423-0120 or J0522-3627  
  > "| 2022.1.00905.S | LB 0 | 85-8548 | 1.7 | 0.4 | J0522-3627 | J0431+1731 | 41 |" (Table 1)
- flux scale uncertainty: 10% absolute flux calibration  
  > "The 10% absolute flux calibration uncertainty of ALMA is added in quadrature." (3.2)
- self calibration: phase-only per EB, 5 SB rounds, joint round, then 2 amp+phase rounds  
  > "Finally, we performed two rounds of amplitude and phase-self-calibration on the data." (2 Observations)

### Imaging

- task: tclean with Briggs weighting  
  > "The data were imaged with the `CASA` task `tclean` using Briggs weighting." (2.1 Imaging)
- deconvolver: _not stated_
- weighting robust: 183 GHz robust 0.0 and 2.0; H13CO+ 2.0; SO 0.5; continuum -0.5  
  > "imaged with a `robust` parameter of 0.0 and 2.0 and a channel width of 1 km s$^{-1}$" (2.1 Imaging)
- uv taper: 0.2" taper for H13CO+  
  > "a $0.2\ensuremath{''}$-$uv$ taper was applied" (Table 2)
- cell size: _not stated_
- image size: _not stated_
- masking: Keplerian mask, i=46.7 deg, PA=138 deg, 140 pc, 2.1 Msun, vsys 7.1 km/s, convolved with 1.5x beam Gaussian  
  > "Finally, the mask is convolved with a Gaussian 1.5 times larger than the beam." (3.1)
- multiscale scales: _not stated_
- continuum subtraction: uvcontsub_old, first order polynomial  
  > "using the `CASA` task `uvcontsub_old` by fitting a first order polynomial to the line free channels." (2 Observations)
- line free channels: _not stated_
- primary beam correction: _not stated_
- array combination: _not stated_
- smoothing: 321 GHz cube convolved to 183 GHz beam for rotational diagram  
  > "this cube is convolved to match the beam size of the 183 GHz line." (3.3)
- final beam: _not stated_
- final rms: 183 GHz channel rms 9-11 mJy/beam (robust 0), 5-7 (robust 2)  
  > "| 1.0 | 9-11 | 0.0 |" (Table 2)

### Inherited from earlier work

- Calibration of the data presented in earlier paper  
  > "The calibration of these data is presented in (cite: Facchini2024)." (2 Observations) [from Facchini2024]
- Self-calibration, EB alignment and flux rescaling follow exoALMA methods  
  > "following the methods of the exoALMA large program (cite: Loomis2025)" (2 Observations) [from Loomis2025; Andrews2018; Czekala2021]
- 321 GHz reimaging follows earlier procedure  
  > "The continuum subtracted image was recreated following (cite: Facchini2024)" (2.1 Imaging) [from Facchini2024]
- Rotational diagram formalism  
  > "The formalism by (cite: Goldsmith1999) and (cite: Loomis2018)" (3.3) [from Goldsmith1999; Loomis2018]

### Not stated but needed to reproduce (our reading)

- Line-free channel ranges for continuum subtraction
- tclean image size, cell size, masks and cleaning thresholds for line cubes
- DALI model details such as dust opacities and gas-to-dust ratio
- Coordinates of HL Tau and phase center
- Thresholds and parameters of the exoALMA alignment
- Emitting area values for the radially resolved diagram beyond beam

## Analysis recipe

1. **Self-calibrate and combine SB and LB data**: Phase-only self-cal per EB, SB 5 rounds, joint round, then two amp+phase rounds; gains applied to line data  
  > "A single round of phase-only self-calibration was applied to each EB of the short and long baseline data separately." (2 Observations)
   - software: CASA
   - parameter: Solution intervals EB, 360, 120, 60, 20 s for SB  
  > "decreasing solution intervals with the length of a single EB, 360, 120, 60, and 20 seconds" (2 Observations)
   - fitting: _not stated_
   - validation: Peak S/N of continuum improved from 955 to 2682 for SB  
  > "This improved the peak signal-to-noise ratio on the continuum from 955 to 2682." (2 Observations)
2. **Image line cubes with JvM correction**: tclean at several robust values, then JvM correction  
  > "we apply the so-called JvM correction to the line cubes" (2.2 JvM-correction)
   - software: CASA
   - fitting: _not stated_
   - validation: Verified uniform line fluxes across robust values  
  > "We verified that this correction is needed to maintain the uniform line fluxes across a wide range of `robust` parameters" (2.2 JvM-correction)
3. **Moment maps, integrated fluxes and radial profiles**: Keplerian-masked moment maps; azimuthal averaging; uncertainty from channel rms propagation  
  > "The moment 0, 1, and 8 maps are computed using the `Better Moments` package" (3.1)
   - software: bettermoments, gofish
   - parameter: 183 GHz integrated -8.5 to 22.5 km/s  
  > "integrating the cubes from -8.5 to 22.5 km s$^{-1}$ for the 183 GHz line" (3.1)
   - fitting: _not stated_
   - validation: _not stated_
4. **Rotational diagram of 183 and 321 GHz lines**: Two-line LTE rotational diagram with optical depth correction, per radius and disk-integrated  
  > "we perform a rotational diagram analysis using the warm 183 GHz and the hot 321 GHz line" (4.2)
   - parameter: ortho-to-para ratio 3; emitting area = beam for radially resolved  
  > "For the radially resolved rotational diagram, the emitting area is assumed to be the beam size." (3.3)
   - assumption: LTE  
  > "Under the assumption of local thermodynamical equilibrium (LTE)" (3.3)
   - fitting: Analytic two-line solution; uncertainties by Taylor linearization and error propagation, no sampler  
  > "the equation is linearized through a first order Taylor polynomial around $\bar{T}$" (3.3)
   - validation: Compared with Facchini2024 results  
  > "roughly consistent with those derived from these lines and the 325 GHz line" (4.2)
5. **Fraction of water visible vs wavelength**: DALI model; compute tau_dust=1 surface per line and fraction of gas-phase water above it; correct disk-integrated rotational diagram  
  > "The fraction of the gas-phase molecules above that surface" (4.3)
   - software: DALI
   - parameter: 17 au emitting region, disk mass 0.2 Msun, rc 30 au  
  > "assuming a 17 au emitting region in the disk frame" (4.3)
   - fitting: _not stated_
   - validation: Model reproduces continuum and CO isotopologue flux within factor 2  
  > "The modelled radial profiles reproduce the data within a factor of $<2$ for most disk radii" (Thermochemical model)
6. **Compare H2O with H13CO+ and SO**: Compare radial profiles of H13CO+ J=2-1 and J=3-2, and moment 1 of SO and water  
  > "the $J=2-1$ (173.507 GHz) radial profile is compared to that of the $J=3-2$ emission" (4.4)
   - fitting: _not stated_
   - validation: _not stated_

## Software

- **CASA** 6.5.4: calibration, self-calibration, tclean imaging, uvcontsub  
  > "We used `CASA` version 6.5.4" (2 Observations)
- **bettermoments** : moment maps  
  > "computed using the `Better Moments` package" (3.1)
- **gofish** : azimuthally averaged radial profiles  
  > "obtained using the gofish package" (3.2)
- **CARTA** : extracting spectra for noise analysis  
  > "using `CARTA` (cite: carta)" (7.1)
- **DALI** : thermochemical disk model  
  > "The disk is modelled using the thermo-chemical modelling code DALI" (Thermochemical model)

## Numeric results

| quantity | value | uncertainty | units | step | quote |
|---|---|---|---|---|---|
| Water excitation temperature | ~350 | not stated | K | 4 | The excitation temperature of the line is $\sim350$ K and independent of radius |
| 183 GHz disk-integrated flux (robust 0.0) | 882 | 318 | mJy km/s | 3 | $882 \pm 318$ |
| Peak brightness temperature 183 GHz | 220 | not stated | K | 3 | reach a high brightness temperature of 220 K and 160 K in the inner beam |
| Water snowline upper limit | 6 | not stated | au | 3 | located inside the inner beam ($\lesssim 6$ au) |
| H13CO+ ring radius | ~80 | not stated | au | 6 | peaks at $\sim80$ au from the central star |
| Continuum flux within 1" radius | 335 | 34 | mJy | 1 | is $335 \pm 34$ mJy |
| Water fraction visible with ALMA | 35-70 | not stated | % | 5 | 35-70% of the gas-phase water reservoir is visible |

## Qualitative findings

- SO traces disk, streamer and outflow out to ~2"  
  > "we see SO emission tracing the disk and for the first time in SO a molecular outflow and the infalling streamer out to $\sim 2"$" (abstract)

## Claim tuples

- H: Water snowline location in HL Tau | E: Resolved 183 GHz imaging, brightness temperature and rotational diagram | R: Steep Tb drop outside central beam; Tex ~350 K | F: Snowline lies inside ~6 au at probed height | **supported**
- H: Optically thick dust hides IR water | E: DALI tau_dust=1 surfaces | R: 0.02%-2% visible in IR vs 35-70% with ALMA | F: Dust explains column density offset; lines not strongly masing | **supported**
- H: H13CO+ anti-correlates with water due to snowline | E: Compare radial profiles | R: Anti-correlation found | F: Likely caused by optically thick dust | **refuted**

## Reasoning

- Why this data: _not stated_
- Why this method: JvM correction needed to avoid overestimating extended low S/N line fluxes  
  > "this is needed in order not to overestimate line fluxes for extended and low signal-to-noise ratio emission morphologies" (2.2 JvM-correction)
- Alternative: Masing as cause of ALMA vs Herschel column density difference, rejected after dust correction  
  > "the 183, 321, and 325 GHz lines in this work and (cite: Facchini2024) are unlikely to be strongly masing." (4.3)
- How they decided it was enough: _not stated_
- Limitation (authors): Some SO and H13CO+ flux may be resolved out  
  > "Therefore, some flux might be resolved out." (3.1)
- Caveat (inferred, ours): Two-line rotational diagram with LTE and 10% flux error gives weak temperature constraints
- Caveat (inferred, ours): Snowline conclusion relies on a simple DALI model not fitted formally
- Caveat (inferred, ours): Different ALMA projects and resolutions may introduce flux scale mismatches

## Reproducibility

- Data public (paper): ALMA program data cited with project codes; public status not explicitly stated  
  > "This paper makes use of the following ALMA data: ADS/JAO.ALMA#2017.1.01178.S" (Acknowledgements)
- Products in archive: _not stated_
- Missing: Full tclean parameters
- Missing: DALI input files
- Missing: Line-free channels
- Data volume (inferred): several hundred GB to ~1 TB raw for 8 EBs
- Score (inferred): 3/5, Data and main steps described and projects named, but imaging parameters, model inputs and several inherited procedures are missing.
- Rediscovery candidate: no, Recipe depends on exoALMA self-calibration code, DALI model details and unreported imaging settings.

## Links

- Method: Loomis2025 (exoALMA self-calibration and alignment procedure)
- Method: Czekala2021 (JvM correction)
- Companion: Facchini2024 (first detection of 183 GHz water in HL Tau; 321 GHz data and calibration)
- Related: exoALMA

## Checks

```json
{
 "quotes": 75,
 "quotes_ok": 75,
 "quote_pass_rate": 1.0,
 "quotes_too_long": 0,
 "unsupported_facts": 0,
 "project_codes": 4,
 "codes_not_in_text": [],
 "codes_not_in_obscore": [],
 "obscore_codes_not_in_card": [],
 "codes_printed_but_missing": [],
 "numeric_results": 7,
 "numeric_problems": 0,
 "fill": {
  "facts": 85,
  "stated": 56,
  "rate": 0.659
 },
 "evidence_ok": true
}
```
