# Revealing new features of the millimetre emission of the circumbinary envelope of Mira Ceti

`2020MNRAS.495..943H` | Monthly Notices of the Royal Astronomical Society 2020 | first author: Hoai, D. T. | arXiv: 2004.11518 | DOI: 10.1093/mnras/staa1173

Card schema 1.0 | model claude-sonnet-5-5 | depth full | type archival_reuse

## Science

- Fields: evolved_stars
- Question: What is the morpho-kinematics of the circumbinary envelope of Mira Ceti between ~100 and ~350 au in SiO(5-4) and CO(3-2), and what do its fragments imply about Mira B's influence, mass ejection and turbulence?  
  > "We study the morpho-kinematics of the circumbinary envelope of Mira Ceti between $\sim$100 and $\sim$350 au from the stars using ALMA observations of the SiO ($\nu$=0, $J$=5-4) and CO ($\nu$=0, $J$=3-2) emissions" (abstract)
- Target **Mira Ceti (Mira AB)**: coordinates RA 02h 19m 20.79210s, Dec -02d58m39.4956s (J2000, proper-motion corrected)  
  > "We adopt a distance of 100 pc, average between the two values in the table." (Table 1); "Right ascension (J2000)(b) & 02h 19m 20.79210 s &\" (Table 1); z/distance 100 pc adopted (92±10 and 110±9 pc)  
  > "We adopt a distance of 100 pc, average between the two values in the table." (Table 1); "Right ascension (J2000)(b) & 02h 19m 20.79210 s &\" (Table 1); distance from average of van Leeuwen 2007 and Haniff 1995 values  
  > "We adopt a distance of 100 pc, average between the two values in the table." (Table 1); "Right ascension (J2000)(b) & 02h 19m 20.79210 s &\" (Table 1)

## Data provenance

- ALMA projects: 2011.0.00014.SV, 2013.1.00047.S
- bands: _not stated_
- frequencies and spectral setup: SiO 217.1 GHz, CO 345.8 GHz, channel width 0.4 km/s  
  > "| Frequency (GHz) | 217.1 | 345.8 |" (Table 2)
- continuum bandwidth: _not stated_
- arrays: SiO: 35/36 antennas; CO: 34/36 antennas  
  > "| Number of antennas | 35/36 | 34/36 |" (Table 2)
- configurations: _not stated_
- baselines: Max baseline 15.24 km (SiO), 0.65 km (CO)  
  > "| Maximal baseline (km) | 15.24 | 0.65 |" (Table 2)
- angular resolution: Beam 60x30 mas (SiO), 390x360 mas (CO)  
  > "| Beam size (mas$^2$) | 60$\times$30 | 390$\times$360 |" (Table 2)
- max recoverable scale: 11.3 arcsec (SiO), ~4 arcsec (CO)  
  > "| Maximal recoverable scale (arcsec) | 11.3 | $\sim$4 |" (Table 2)
- sensitivity: 0.66 mJy/beam (SiO); effective 1 sigma 32 mJy/beam (CO)  
  > "| Noise level (mJy beam$^{-1}$) | 0.66 | 32 |" (Table 2)
- time on source: _not stated_
- observing dates: SiO 29 Oct and 1 Nov 2014; CO 12-15 June 2014  
  > "| Date of observation | 29 October and 1st November 2014 | 12-15 June 2014 |" (Table 2)
- pi or archival as stated: Archival; SiO from ALMA Long Baseline Science Verification (PI ALMA), CO PI P. Planesas  
  > "The data used here are retrieved from ALMA archives and correspond to two different sets of observations." (2.1 Generalities)
- Line: SiO v=0 J=5-4 (217.1 GHz)
- Line: CO v=0 J=3-2 (345.8 GHz)
- Line: 13CO v=0 J=3-2 (not stated)
- External data: Orbit of Mira B (period ~500 yr, pair mass 4.4 Msun)  
  > "The orbit of Mira B has been calculated by (cite: Prieur2002), however with large uncertainties" (5 North-eastern outflow) [from (cite: Prieur2002)]
- External data: Systemic velocity 47.7 km/s from CO(v=1, 3-2) fit  
  > "we use a systemic velocity of 47.7 km s$^{-1}$ with respect to the local standard of rest (LSR) as obtained by (cite: Khouri2018)" (2.1 Generalities) [from (cite: Khouri2018)]
- External data: Continuum centre of Mira A used as origin  
  > "The origin is taken to match the centre of continuum emission of Mira A as observed by (cite: Planesas2016) and (cite: Wong2016)." (2.1 Generalities) [from (cite: Planesas2016; Wong2016)]

## Processing

### Calibration

- pipeline or manual: Recalibrated SiO data with provided ALMA scripts, no continuum subtraction  
  > "we recalibrated and reduced the data using the provided ALMA scripts and CASA version 4.2.2 omitting continuum subtraction." (2.1 Generalities)
- casa version: CASA 4.2.2 (SiO data)  
  > "we recalibrated and reduced the data using the provided ALMA scripts and CASA version 4.2.2 omitting continuum subtraction." (2.1 Generalities)
- pipeline version: _not stated_
- archive products used as is: _not stated_
- flux calibrator: _not stated_
- flux scale uncertainty: _not stated_
- self calibration: _not stated_

### Imaging

- task: GILDAS (adopted) and CASA compared for CO deconvolution  
  > "we have compared the performance of two software packages, GILDAS and CASA and explored the relevant parameter space" (2.2 De-convolution)
- deconvolver: _not stated_
- weighting robust: Natural weighting adopted (robust 1.0 also tested)  
  > "The data used in the subsequent sections of the article were processed by GILDAS using optimal masks and natural weighting" (2.2 De-convolution)
- uv taper: _not stated_
- cell size: 0.01 arcsec (SiO), 0.06 arcsec (CO)  
  > "| Pixel size (arcsec$^2$) | 0.01$\times$0.01 | 0.06$\times$0.06 |" (Table 2)
- image size: _not stated_
- masking: Different optimal mask per channel  
  > "a very significant improvement is obtained by using different masks for each frequency channel, well adapted to the specific morphology." (2.2 De-convolution)
- multiscale scales: _not stated_
- continuum subtraction: None, continuum negligible beyond 50 au  
  > "In the region explored in this article, beyond some 50 au from Mira A, the contribution of continuum emission is negligible and does not need to be subtracted." (2.1 Generalities)
- line free channels: _not stated_
- primary beam correction: _not stated_
- array combination: _not stated_
- smoothing: _not stated_
- final beam: 0.39x0.36 arcsec (CO natural)  
  > "| Natural    | 0.39$\times$0.36" (Table 3)
- final rms: CO effective 32 mJy/beam; brightness cut 0.08 Jy/beam (~2.5 sigma)  
  > "the cut at 0.08 Jy beam$^{-1}$ corresponds to an effective 2.5$\sigma$ cut" (2.2 De-convolution)

### Inherited from earlier work

- Detailed observation and data reduction of SiO data not repeated  
  > "The very detailed description of observations and data reduction given by (cite: Wong2016) does not need to be repeated." (2.1 Generalities) [from (cite: Wong2016)]
- CO observation details not repeated  
  > "Here again we do not need to repeat the detailed descriptions given by these authors." (2.1 Generalities) [from (cite: Planesas2016; Nhung2016)]

### Not stated but needed to reproduce (our reading)

- CLEAN thresholds, iteration counts and the actual per-channel masks for the adopted GILDAS CO cubes
- GILDAS version
- Which SiO imaging parameters (weighting, robust, beam) were used in CASA
- Exact selection of data/calibrators for the CO set
- Line-free channels and continuum treatment for CO
- Details of the radiative transfer calculation for absorption (37%) and the 12CO/13CO abundance conversion

## Analysis recipe

1. **Recalibrate and image data**: SiO recalibrated with ALMA scripts in CASA 4.2.2; CO deconvolved in GILDAS with optimal channel masks, natural weighting; CASA compared  
  > "The data used in the subsequent sections of the article were processed by GILDAS using optimal masks and natural weighting" (2.2 De-convolution)
   - software: CASA, GILDAS
   - parameter: 20,000 clean iterations in illustrated GILDAS channel; brightness cut 0.08 Jy/beam  
  > "Figure [2](#fig2) displays a clean map obtained from GILDAS after 20,000 iterations." (2.2 De-convolution)
   - fitting: _not stated_
   - validation: Brightness in four test regions compared across codes, masks and weightings; results checked with and without cut  
  > "Systematically, we made sure that all the statements made in the remaining part of the article are robust with respect to this brightness cut and to de-convolution and cleaning processes." (2.2 De-convolution)
2. **Build intensity maps and position-velocity maps**: Intensity integrated over Vz, multiplied by R; PV maps in (Vz, phi), (Vz, R); define fragments by R, phi, Vz volumes  
  > "In the following four sections we define volumes of the data cubes as intervals in $R$, $\varphi$ and $V_z$ aimed at selecting different components" (3 Global description)
   - assumption: Systemic velocity 47.7 km/s; distance 100 pc  
  > "we use a systemic velocity of 47.7 km s$^{-1}$ with respect to the local standard of rest (LSR)" (2.1 Generalities)
   - fitting: _not stated_
   - validation: _not stated_
3. **Estimate absorption and 12CO/13CO**: Simple radiative transfer for optical thickness; 12CO/13CO brightness ratio  
  > "assuming a uniform radial expansion velocity of 7 km s$^{-1}$ and a temperature of 100 K, a simple radiative transfer calculation gives an absorption reaching $\sim$37%." (3 Global description)
   - assumption: Expansion 7 km/s, T=100 K  
  > "assuming a uniform radial expansion velocity of 7 km s$^{-1}$ and a temperature of 100 K" (3 Global description)
   - fitting: _not stated_
   - validation: Spread of ratio across fragments only ±0.8  
  > "is only $\pm$0.8, confirming the small impact of absorption." (3 Global description)
4. **Analyse inner Doppler wings in SiO**: Average spectra in annuli of width 0.03 arcsec, radii 0.025-0.215 arcsec in 0.01 steps, flat continuum subtracted; measure line width vs R  
  > "We do so by averaging the spectra over annular rings having a width of 0.03 arcsec and mean radii increasing between 0.025 and 0.215 arcsec in steps of 0.01 arcsec." (8 Large Doppler velocities)
   - fitting: _not stated_
   - validation: Checked by quadrant  
  > "We checked that this result remains true when considering only one quadrant" (8 Large Doppler velocities)

## Software

- **CASA** 4.2.2: Recalibration/reduction of SiO data; CO cleaning comparison  
  > "CASA version 4.2.2 omitting continuum subtraction" (2.1 Generalities)
- **GILDAS** : CO deconvolution (adopted cubes)  
  > "The data used in the subsequent sections of the article were processed by GILDAS using optimal masks and natural weighting" (2.2 De-convolution)

## Numeric results

| quantity | value | uncertainty | units | step | quote |
|---|---|---|---|---|---|
| 12CO/13CO abundance ratio | 12 | ±2 | dimensionless | 3 | this result translates into a $^{12}$CO/$^{13}$CO abundance ratio of 12$\pm$2 |
| Absorption in SW outflow | ~37% | not stated | percent | 3 | gives an absorption reaching $\sim$37% |
| Mean 12CO/13CO brightness ratio (uncorrected) | 7.3 | rms 3.1 | dimensionless | 3 | Its average value is 7.3 with an rms deviation with respect to the mean of 3.1. |
| Mean brightness in fragments vs between | 2.6 vs 1.3 | not stated | Jy arcsec^-2 | 2 | having a mean brightness of 2.6 Jy arcsec$^{-2}$ compared with only 1.3 Jy arcsec$^{-2}$ in between the fragments |
| NE arc inner-edge ellipse semi-axes | 1.72 and 1.02 | not stated | arcsec | 2 | having semi-major and semi-minor axes along the $x$ and $y$ axes of 1.72 and 1.02 arcsec respectively |
| Maximum |Vz| of wings | 16 | not stated | km/s | 4 | reaching 16 km s$^{-1}$ for both CO and SiO |
| Focused wind velocity V of NE outflow | 3.9 | ±1.3 | km/s | 2 | We infer from this that $V=V_z/\sin50$$^{\circ}$$\sim3.9\pm1.3$ km s$^{-1}$. |

## Qualitative findings

- Emission is strongly fragmented; SW outflow shows anti-correlated CO and SiO, interpreted as a mass ejection with shock  
  > "We identify a South-western outflow and give arguments for the anti-correlation observed between CO and SiO emissions being the result of a recent mass ejection accompanied by a shock wave." (abstract)

## Claim tuples

- H: Is the SW outflow CO/SiO anti-correlation due to a recent mass ejection and shock? | E: Radial profiles and PV maps of SiO and CO in SW outflow | R: SiO confined to a narrow (phi,Vz) region and sharp radial decrease; CO suppressed along it | F: Consistent with mass ejection (possibly 2003 X-ray burst) plus shock, not ascertained | **partially**
- H: Does Mira B focusing explain the NE outflow? | E: Model of focused wind compared with PV maps | R: Only a small part consistent with focusing | F: Bulk of NE outflow may be accumulation or unrelated to Mira B | **partially**
- H: Is the Southern arc the start of a WRLOF spiral from Mira B focusing? | E: Compare PV maps and spiral winding | R: Vz oscillates in phase opposition and spiral winds in the wrong direction | F: Association with Mira B focusing excluded | **refuted**
- H: What causes the large Doppler wings near Mira A? | E: Annular SiO spectra versus R | R: Profile ~4 times broader inside ~0.1 arcsec | F: Suggests turbulence within ~5-10 au | **partially**

## Reasoning

- Why this data: _not stated_
- Why this method: Imaging revisited because of complex fragmented morphology and sidelobe/negative-bowl issues  
  > "It prompted us to revisit the imaging process with the aim of assessing as rigorously as possible the reliability of the results obtained." (2.1 Generalities)
- Alternative: Rotation, gas streams and pulsations rejected for large Doppler wings  
  > "we fail to think of a plausible interpretation of these large Doppler velocities in terms of previously considered scenarios." (8 Large Doppler velocities)
- How they decided it was enough: _not stated_
- Limitation (authors): CO recoverable scale ~4 arcsec means much extended flux missing; CO deconvolution leaves negative regions; arbitrariness of fragment definition  
  > "The value of the recoverable scale associated with the CO observations implies that a large fraction of the extended flux is missing." (2.1 Generalities)
- Caveat (inferred, ours): Interpretations (mass ejection, turbulence) are qualitative with no quantitative modelling or fitting
- Caveat (inferred, ours): CO deconvolution relies on hand-tuned masks and an ad hoc 0.08 Jy/beam cut
- Caveat (inferred, ours): Systemic velocity uncertainty of ~1 km/s affects PV-map arguments
- Caveat (inferred, ours): Imaging uncertainties not propagated into results

## Reproducibility

- Data public (paper): Data retrieved from ALMA archive via JVO portal  
  > "The data are retrieved from the JVO portal (http://jvo.nao.ac.jp/portal) operated by the NAOJ." (Acknowledgements)
- Products in archive: _not stated_
- Missing: Per-channel clean masks and GILDAS clean parameters
- Missing: Exact fragment definition scripts and PV-map construction details
- Missing: Radiative transfer absorption calculation details
- Data volume (inferred): ~50-200 GB for both datasets (long-baseline SV SiO and band 7 CO)
- Score (inferred): 3/5, Public data and clear region definitions, but the key CO imaging uses unspecified hand-made masks and results are mostly qualitative.
- Rediscovery candidate: no, Imaging recipe incomplete (custom masks) and main results largely morphological rather than numeric.

## Links

- Method: (cite: Wong2016) (Detailed SiO observation and reduction)
- Companion: (cite: Nhung2016) (Earlier analysis of the same CO data)
- Companion: (cite: Ramstedt2014) (Earlier ALMA CO(3-2) morphology of the envelope)
- Companion: (cite: Planesas2016) (Earlier analysis of CO project continuum)
- Related: ALMA 2014 Long Baseline Science Verification Campaign

## Checks

```json
{
 "quotes": 63,
 "quotes_ok": 63,
 "quote_pass_rate": 1.0,
 "quotes_too_long": 0,
 "unsupported_facts": 0,
 "project_codes": 2,
 "codes_not_in_text": [],
 "codes_not_in_obscore": [],
 "obscore_codes_not_in_card": [],
 "codes_printed_but_missing": [],
 "numeric_results": 7,
 "numeric_problems": 0,
 "fill": {
  "facts": 68,
  "stated": 43,
  "rate": 0.632
 },
 "evidence_ok": true
}
```
