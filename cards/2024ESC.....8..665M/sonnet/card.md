# Detection and Chemical Modeling of Complex Prebiotic Molecule Cyanamide in the Hot Molecular Core G31.41 + 0.31

`2024ESC.....8..665M` | ACS Earth and Space Chemistry 2024 | first author: Manna, Arijit | arXiv: 2401.12879 | DOI: 10.1021/acsearthspacechem.3c00245

Card schema 1.0 | model claude-sonnet-5-5 | depth full | type archival_reuse

## Science

- Fields: astrochemistry, star_formation
- Question: Is cyanamide (NH2CN) present in the hot molecular core G31.41+0.31, what are its column density and abundance, and how is it formed (grain-surface NH2 + CN)?  
  > "We present the detection of the rotational emission lines of NH$_{2}$CN with vibrational states $v$ = 0 and 1 towards the hot molecular core G31.41+0.31" (abstract)
- Target **G31.41+0.31**: coordinates 18:47:34.315, –01:12:45.900 (J2000, phase center)  
  > "The disk-like hot molecular core G31.41+0.31 is located at a distance of 7.9 kpc from Earth (cite: ch90)." (1. Introduction); "The phase center of G31.41+0.31 is ($\alpha,\delta$)$_{\rm J2000}$ = 18:47:34.315, –01:12:45.900." (2. Observations and data reductions); z/distance 7.9 kpc  
  > "The disk-like hot molecular core G31.41+0.31 is located at a distance of 7.9 kpc from Earth (cite: ch90)." (1. Introduction); "The phase center of G31.41+0.31 is ($\alpha,\delta$)$_{\rm J2000}$ = 18:47:34.315, –01:12:45.900." (2. Observations and data reductions); distance from Churchwell et al. 1990 (cite: ch90)  
  > "The disk-like hot molecular core G31.41+0.31 is located at a distance of 7.9 kpc from Earth (cite: ch90)." (1. Introduction); "The phase center of G31.41+0.31 is ($\alpha,\delta$)$_{\rm J2000}$ = 18:47:34.315, –01:12:45.900." (2. Observations and data reductions)

## Data provenance

- ALMA projects: 2017.1.00501.S
- bands: Band 3  
  > "using ALMA band 3 (PI: Beltrán Maite)" (2. Observations and data reductions)
- frequencies and spectral setup: One of nine datasets used, 98.50–102.15 GHz, four spectral windows, 564.45 kHz resolution  
  > "We take only one dataset between the frequency ranges of 98.50 GHz and 102.15 GHz" (2. Observations and data reductions); "564.45" (Table 1)
- continuum bandwidth: _not stated_
- arrays: 12m array  
  > "This observation data belongs to the G31.41+0.31 Unbiased ALMA sPectral Observational Survey (GUAPOS)[^1] project with ALMA 12m arrays." (2. Observations and data reductions)
- configurations: _not stated_
- baselines: 15.1 m to 783.5 m, 43 antennas  
  > "A total of forty-three antennas were used, with a minimum baseline of 15.1 m and a maximum baseline of 783.5 m." (2. Observations and data reductions)
- angular resolution: about 1.30″×1.01″ (continuum 1.30″×1.02″)  
  > "The synthesized beam size of the continuum image is 1.30$^{\prime\prime}\times$ 1.02$^{\prime\prime}$." (3.1 Continuum emission towards the G31.41+0.31)
- max recoverable scale: _not stated_
- sensitivity: 0.55 mJy/beam at 10 km/s  
  > "Sensitivity (10 km s$^{-1}$)" (Table 1)
- time on source: 41.328 min  
  > "with an on-source integration time of 41.328 min" (2. Observations and data reductions)
- observing dates: 14 March 2018  
  > "was carried out on March 14, 2018" (2. Observations and data reductions)
- pi or archival as stated: Archival, PI Maite Beltrán, GUAPOS  
  > "We used the archival data of G31.41+0.31" (2. Observations and data reductions)
- Line: NH2CN 5(0,5)–4(0,4) etc., v=0 and 1 (ten transitions, six non-blended) (99.747–100.071 GHz)
- External data: H2 column density (1.0±0.2)×10^25 cm^-2  
  > "the column density of H$_{2}$ towards G31.41+0.31 is (1.0$\pm$0.2)$\times$10$^{25}$ cm$^{-2}$ (cite: min20)" (3.2 Detection of the emission lines of NH2CN) [from (cite: min20)]
- External data: NH2CHO column density (5.4±1.1)×10^16 cm^-2  
  > "the column density of NH$_{2}$CHO in G31.41+0.31 is (5.4$\pm$1.1)$\times$10$^{16}$ cm$^{-2}$ (cite: col21)" (3.2 Detection of the emission lines of NH2CN) [from (cite: col21)]
- External data: Abundances of NH2CN in other hot cores/corinos  
  > "the fractional abundances of NH$_{2}$CN towards the hot corino objects NGC 1333 IRAS4A2, NGC 1333 IRAS2A, and IRAS 16293–2422 B were 1.7$\times$10$^{-10}$, 5.0$\times$10$^{-11}$, and 2.0$\times$10$^{-10}$" (4.1 Comparison of the NH2CN abundance) [from (cite: cou18; bel20)]

## Processing

### Calibration

- pipeline or manual: CASA pipeline tasks (hifa_bandpassflag, hifa_flagdata) plus setjy  
  > "Then we used the CASA pipeline tasks `hifa_bandpassflag` and `hifa_flagdata` for bandpass calibration and flagging bad antenna data, respectively." (2. Observations and data reductions)
- casa version: CASA 5.4.1  
  > "we used the Common Astronomy Software Application (`CASA 5.4.1`)" (2. Observations and data reductions)
- pipeline version: _not stated_
- archive products used as is: _not stated_
- flux calibrator: J1751+0939; Perley-Butler 2017 model; phase calibrator J1851+0035  
  > "the flux calibrator was taken as J1751+0939, and the phase calibrator was taken as J1851+0035" (2. Observations and data reductions)
- flux scale uncertainty: _not stated_
- self calibration: Repeated self-calibration with gaincal and applycal  
  > "We also performed the repeated self-calibration method using the tasks `GAINCAL` and `APPLYCAL` in an attempt to improve the RMS of the final images." (2. Observations and data reductions)

### Imaging

- task: tclean (specmode=cube for lines)  
  > "The molecular spectral line images were created using the task `TCLEAN` with the `SPECMODE=CUBE` parameter." (2. Observations and data reductions)
- deconvolver: hogbom (continuum)  
  > "using task `TCLEAN` with `HOGBOM` deconvolution" (2. Observations and data reductions)
- weighting robust: _not stated_
- uv taper: _not stated_
- cell size: _not stated_
- image size: _not stated_
- masking: _not stated_
- multiscale scales: _not stated_
- continuum subtraction: uvcontsub in uv plane  
  > "we also used task `UVCONTSUB` in the UV plane of the calibrated data to subtract continuum emission from the UV plane" (2. Observations and data reductions)
- line free channels: _not stated_
- primary beam correction: impbcor  
  > "Finally, we used task `IMPBCOR` to correct the synthesized beam pattern in the continuum and spectral images." (2. Observations and data reductions)
- array combination: _not stated_
- smoothing: _not stated_
- final beam: 1.30″×1.02″ continuum  
  > "The synthesized beam size of the continuum image is 1.30$^{\prime\prime}\times$ 1.02$^{\prime\prime}$." (3.1 Continuum emission towards the G31.41+0.31)
- final rms: continuum RMS 3.36 mJy/beam (hot core region)  
  > "249.3$\pm$7.9 mJy with RMS of 3.36 mJy" (3.1 Continuum emission towards the G31.41+0.31)

### Inherited from earlier work

- Source size/emitting-region method  
  > "$\theta_{\text{beam}}$ indicates the half-power width of the synthesized beam (cite: riv17)" (3.3 Spatial distribution) [from (cite: riv17)]
- Two-phase warm-up chemical model setup  
  > "Our chemical model is similar to (cite: vi04)." (4.3 New chemical modelling) [from (cite: vi04)]
- Reaction rate coefficients, Ea and Eb  
  > "The rate coefficients of reactions 1 and 2 are taken from (cite: cou18) and (cite: gar13)." (4.3 New chemical modelling) [from (cite: cou18; gar13; gar06)]

### Not stated but needed to reproduce (our reading)

- Line-free channels for continuum and uvcontsub
- tclean robust, cell size, image size, masking, threshold
- Self-calibration solints and number of iterations
- Spectral window frequency/channel details and rest frequency for velocity
- UCLCHEM version, warm-up timescale and exponent n, initial abundances, dust/grain parameters
- Whether the 250±25 K or 250±35 K uncertainty is correct (text is inconsistent)
- How LTE line widths and velocity were fixed or fitted in CASSIS

## Analysis recipe

1. **calibrate and image the archival data**: CASA pipeline tasks, setjy, mstransform, uvcontsub, tclean, self-calibration, impbcor  
  > "After the initial data reduction, we used task `MSTRANSFORM` to split the target source G31.41+0.31 from the rest of the data." (2. Observations and data reductions)
   - software: CASA
   - fitting: _not stated_
   - validation: _not stated_
2. **measure continuum**: Two 2D Gaussian fits with imfit to the hot core and UC HII region  
  > "We fit the two individual 2D Gaussian using the CASA task `IMFIT` over the hot core and UC HII region to estimate the physical properties." (3.1 Continuum emission towards the G31.41+0.31)
   - software: CASA imfit
   - fitting: _not stated_
   - validation: _not stated_
3. **extract spectra and fit LTE model**: Spectrum from 3.1″ circle over main hot core; LTE-RADEX module in CASSIS with JPL catalog fitted to the lines  
  > "We applied the LTE-RADEX module in CASSIS to fit the LTE model spectra of NH$_{2}$CN to the observed spectra of the G31.41+0.31." (3.2 Detection of the emission lines of NH2CN)
   - software: CASSIS
   - parameter: source size 1.3″; Tbg = 2.73 K; Tc = 0; systemic velocity 97 km/s  
  > "we considered a cosmic background temperature of $T_{bg}$ = 2.73 K and background continuum source temperature of $T_{c}$ = 0" (3.2 Detection of the emission lines of NH2CN)
   - assumption: LTE valid since gas density ~1e8 cm^-3  
  > "The LTE assumptions are appropriate for G31.41+0.31 because the gas density in the warm inner envelope of G31.41+0.31 is $\sim$1$\times$10$^{8}$ cm$^{-3}$" (3.2 Detection of the emission lines of NH2CN)
   - fitting: Least-squares in LTE-RADEX  
  > "which is obtained by using the least-squares method in the LTE-RADEX module (cite: vas15)" (3.2 Detection of the emission lines of NH2CN)
   - validation: Six non-blended lines above 5σ; four blended lines checked via JPL and Splatalogue  
  > "we find only six transition lines of NH$_{2}$CN that are non-blended, which are detected above 5$\sigma$ significance" (3.2 Detection of the emission lines of NH2CN)
4. **derive abundance and ratio**: Divide N(NH2CN) by literature N(H2) and N(NH2CHO)  
  > "we use the column density of NH$_{2}$CN inside the 1.3$^{\prime\prime}$ beam, which is divided by the column density of H$_{2}$" (3.2 Detection of the emission lines of NH2CN)
   - fitting: _not stated_
   - validation: _not stated_
5. **map emission and emitting size**: immoments over line channel ranges, imfit Gaussian, θS = sqrt(θ50² − θbeam²)  
  > "We created integrated emission maps of towards G31.41+0.31 using the CASA task `IMMOMENTS`." (3.3 Spatial distribution)
   - software: CASA immoments, CASA imfit
   - fitting: _not stated_
   - validation: _not stated_
6. **chemical modelling**: Two-phase warm-up model with UCLCHEM with added NH2 + CN grain reaction  
  > "We computed a two-phase warm-up chemical model to determine the abundance and possible formation mechanisms of ." (4.3 New chemical modelling)
   - software: UCLCHEM
   - parameter: Phase I: nH 300 to 1e8 cm^-3 at 10 K; Phase II: 10 to 300 K at 1e8 cm^-3; CR rate 1.3e-17 s^-1; initial Av = 2  
  > "the temperature raised from 10 to 300 K with a constant gas density of 1$\times$10$^{8}$ cm$^{-3}$" (4.3 New chemical modelling)
   - assumption: Sticking probability unity; solar abundances for O, C, N, He (Asplund 2009); Si, S, Cl, Mg, P, F depleted by 100  
  > "we assumed the sticking probability to be unity" (4.3 New chemical modelling)
   - fitting: _not stated_
   - validation: Compared modelled peak abundance with observed abundance and with Garrod et al. 2022  
  > "This result indicates that the estimated abundance of towards the G31.41+0.31 is nearly similar to the modelled abundance of ." (4.4 Comparision between observed and modelled abundance)

## Software

- **CASA** 5.4.1: calibration, imaging, imfit, immoments  
  > "we used the Common Astronomy Software Application (`CASA 5.4.1`) with an ALMA data reduction pipeline" (2. Observations and data reductions)
- **CASSIS** : LTE modelling (LTE-RADEX)  
  > "We used CASSIS for the LTE modelling (cite: vas15)." (3.2 Detection of the emission lines of NH2CN)
- **UCLCHEM** : two-phase warm-up chemical modelling  
  > "we use the time-dependent gas-grain chemical code UCLCHEM (cite: hol17)" (4.3 New chemical modelling)
- **Splatalogue** : line identification and blending check  
  > "The blended molecules are confirmed by JPL and the online molecular database Splatalogue." (3.2 Detection of the emission lines of NH2CN)

## Numeric results

| quantity | value | uncertainty | units | step | quote |
|---|---|---|---|---|---|
| NH2CN column density | 7.21e15 | 0.25e15 | cm^-2 | 3 | is (7.21$\pm$0.25)$\times$10$^{15}$ cm$^{-2}$ with an excitation temperature of 250$\pm$25 K |
| Excitation temperature | 250 | ±25 K (abstract; ±35 K in Sec 3.2) | K | 3 | with an excitation temperature of 250$\pm$25 K |
| NH2CN abundance vs H2 | 7.21e-10 | 1.46e-10 | dimensionless | 4 | The abundance of NH$_{2}$CN with respect to H$_{2}$ towards G31.41+0.31 is (7.21$\pm$1.46)$\times$10$^{-10}$. |
| NH2CN/NH2CHO ratio | 0.13 | 0.02 | dimensionless | 4 | The NH$_{2}$CN and NH$_{2}$CHO column density ratio towards G31.41+0.31 is 0.13$\pm$0.02. |
| Main hot core integrated continuum flux (99.9 GHz) | 249.3 | 7.9 | mJy | 2 | 174.4$\pm$3.6 mJy beam$^{-1}$ and 249.3$\pm$7.9 mJy with RMS of 3.36 mJy |
| Modelled peak NH2CN abundance | 5.12e-10 | not stated | dimensionless | 6 | The maximum modelled abundance of NH$_{2}$CN reaches 5.12$\times$10$^{-10}$ on the grain at the time of $\sim$3.8$\times$10$^{5}$ yr |
| NH2CN emitting region size | 1.28–1.32 | not stated | arcsec | 5 | The emitting regions of NH$_{2}$CN vary between 1.28$^{\prime\prime}$ and 1.32$^{\prime\prime}$. |
| NH2CN FWHM | 5.2 | 0.8 | km/s | 3 | The FWHM of the LTE spectra of NH$_{2}$CN is 5.2$\pm$0.8 km s$^{-1}$. |

## Qualitative findings

- Emission arises from warm inner region; lines only marginally resolved; no line emission from UC HII region  
  > "This result indicates that the detected non-blended transitions of NH$_{2}$CN are not spatially resolved or marginally resolved towards G31.41+0.31." (3.3 Spatial distribution)

## Claim tuples

- H: NH2CN is present in G31.41+0.31 | E: LTE fit of band 3 spectra | R: Ten transitions, six non-blended above 5σ | F: First identification of NH2CN in G31.41+0.31 | **supported**
- H: NH2CN is formed on grains via NH2 + CN | E: UCLCHEM two-phase warm-up model compared with observed abundance | R: Modelled 5.12e-10 vs observed 7.21e-10 | F: Neutral-neutral NH2 + CN grain-surface reaction is responsible | **partially**
- H: NH2CN abundance compares with other sources | E: Compare with literature abundances | R: Similar to G358.93–0.03 MM1, IRAS 16293-2422 B, NGC 1333 IRAS4A2 | F: Similar origin plausible | **supported**

## Reasoning

- Why this data: Higher-intensity NH2CN transitions lie at 99.41–100.34 GHz, so only that dataset was used  
  > "because the higher intensity transitions of NH$_{2}$CN are observed between the frequency ranges of 99.41 GHz and 100.34 GHz in ALMA band 3" (2. Observations and data reductions)
- Why this method: _not stated_
- Alternative: Zhang et al. 2023 NCN + H2 model rejected as unsuitable for G31.41+0.31 density and NCN undetected  
  > "The chemical model of (cite: zh23) is not suitable for G31.41+0.31 because the density of G31.41+0.31 is $\sim$1$\times$10$^{8}$ cm$^{-3}$" (4.2 Previous chemical modelling)
- How they decided it was enough: _not stated_
- Limitation (authors): Coarse resolution; morphology cannot be determined  
  > "Therefore, understanding the morphology of NH$_{2}$CN from the spatial distribution maps towards G31.41+0.31 is not possible." (3.3 Spatial distribution)
- Caveat (inferred, ours): Source size of 1.3″ is assumed equal to the beam, so column density is a beam-diluted lower limit
- Caveat (inferred, ours): Model matching only on a single abundance value, no sensitivity to parameters or comparison with other formation routes in the same code
- Caveat (inferred, ours): Abundance uses H2 column from a different dataset/resolution
- Caveat (inferred, ours): Inconsistent Tex uncertainty (±25 vs ±35 K)
- Caveat (inferred, ours): Text says G10.47+0.03 observation in the observation section (likely typo)

## Reproducibility

- Data public (paper): Archival ALMA data from GUAPOS project  
  > "We used the archival data of G31.41+0.31" (2. Observations and data reductions)
- Products in archive: _not stated_
- Missing: tclean parameters and line-free channels
- Missing: self-calibration details
- Missing: CASSIS fit settings and priors
- Missing: UCLCHEM input parameters and added reaction network files
- Data volume (inferred): ~20-50 GB for the MS of one dataset (four spws); smaller for calibrated products
- Score (inferred): 3/5, Public data and moderate recipe, but imaging parameters and chemical model inputs are underspecified.
- Rediscovery candidate: no, Imaging and modelling settings are insufficiently specified to redo exactly, although the data are public.

## Links

- Method: (cite: min20) (GUAPOS survey source properties (H2 column, density, temperature))
- Method: (cite: vas15) (CASSIS tool)
- Method: (cite: hol17) (UCLCHEM code)
- Companion: (cite: man23a) (Same method applied to NH2CN in G358.93–0.03 MM1)
- Companion: (cite: man22) (NH2CN in G10.47+0.03)
- Related: GUAPOS

## Checks

```json
{
 "quotes": 69,
 "quotes_ok": 69,
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
  "stated": 51,
  "rate": 0.654
 },
 "evidence_ok": true
}
```
