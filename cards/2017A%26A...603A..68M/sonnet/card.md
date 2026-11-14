# Approaching hell's kitchen: Molecular daredevil clouds in the vicinity of Sagittarius A*

`2017A&A...603A..68M` | Astronomy and Astrophysics 2017 | first author: Moser, Lydia | arXiv: 1603.00801 | DOI: 10.1051/0004-6361/201628385

Card schema 1.0 | model claude-sonnet-5-5 | depth full | type archival_reuse

## Science

- Fields: milky_way_ism, astrochemistry
- Question: What is the distribution, excitation and origin of molecular gas and the continuum/RRL properties within the central parsec of Sgr A* seen with ALMA Cycle 0 bands 3, 6 and 7?  
  > "We report the serendipitous detection of line emission in the central parsec up to within 1 ′′ (∼ 0.04 pc) around Sgr A* in projection." (1. Introduction)
- Target **Sgr A* and central parsec (minispiral, CND)**: coordinates 17h45m40.040s, -29d00m28.118s (J2000)  
  > "The single pointing on Sgr A* (17 h .45 m . 40 s .040, -29 ◦ .00. ′ 28 ′′ . 118, J2000)" (2.1 Observation); "At the distance to the GC of - here we adopt 8±0.3kpc" (1. Introduction); z/distance 8±0.3 kpc  
  > "The single pointing on Sgr A* (17 h .45 m . 40 s .040, -29 ◦ .00. ′ 28 ′′ . 118, J2000)" (2.1 Observation); "At the distance to the GC of - here we adopt 8±0.3kpc" (1. Introduction); distance from Schödel et al. 2002; Eisenhauer et al. 2003; Horrobin et al. 2004; Ghez et al. 2008; Gillessen et al. 2009a,b  
  > "The single pointing on Sgr A* (17 h .45 m . 40 s .040, -29 ◦ .00. ′ 28 ′′ . 118, J2000)" (2.1 Observation); "At the distance to the GC of - here we adopt 8±0.3kpc" (1. Introduction)

## Data provenance

- ALMA projects: 2011.0.00887.S
- bands: Band 3, 6, 7 (~100, 250, 340 GHz)  
  > "the corresponding central frequencies were tuned to ∼ 100, 250, and 340 GHz, respectively." (2.1 Observation)
- frequencies and spectral setup: TDM, 128 channels of 15.625 MHz, 2 GHz per spw, four spws per band (8 GHz total); channels ~50, 20, 15 km/s  
  > "the correlator provides 128 channels with a width of 15.625 MHz resulting in a total bandwidth of the spectral window of 2 GHz." (2.1 Observation)
- continuum bandwidth: _not stated_
- arrays: _not stated_
- configurations: most extended Cycle 0 configuration, baselines 36-400 m, 19 antennas  
  > "the array was in its most extended configuration (in cycle 0) with baselines ranging from 36 to 400 m." (2.1 Observation)
- baselines: _not stated_
- angular resolution: about 1.5'', 0.7'', 0.5''  
  > "This results in angular resolutions of about 1.5 ′′, 0.7 ′′, and 0.5 ′′, respectively." (2.1 Observation)
- max recoverable scale: <10'', <4'', <3'' for bands 3, 6, 7  
  > "the instrument is sensitive in the different FOVs to angular scales < 10 ′′, < 4 ′′ and < 3 ′′, respectively." (2.1 Observation)
- sensitivity: continuum rms 0.5, 0.2, 0.3 mJy/beam; channel rms 0.5, 1.0, 1.6 mJy/beam  
  > "The noise rms is 0.5, 0.2, and 0.3 mJy beam −1 for the continuum, and 0.5, 1.0, and 1.6 mJy beam −1 for a channel." (2.3 Line and continuum imaging)
- time on source: 7.5 h total; ~20 min per target and band  
  > "The total observation time is 7.5 h and the integration time per target and band is on the order of 20 min." (2.1 Observation)
- observing dates: 18 May 2012  
  > "on 18 May 2012 with ALMA in Band 3, 6, and 7 alternatingly." (2. ALMA observations and data reduction)
- pi or archival as stated: Archival data, PI Heino Falcke monitoring campaign  
  > "GC data obtained in a monitoring campaign, under the project 2011.0.00887.S (PI: Heino Falcke)" (2. ALMA observations and data reduction)
- Line: CS 5–4 (244.936 GHz)
- Line: 13CS 2–1 (92.494 GHz)
- Line: N2H+ 1–0 (93.174 GHz)
- Line: SiO 6–5, 8–7 (260.518, 347.331 GHz)
- Line: H39α RRL (106.737 GHz)
- Other facility **VLT/NACO, VISIR, HST NICMOS**: NIR/MIR comparison images  
  > "compared to the NIR VLT/NACO L’ (3.8 µm) emission (top, Sabha, private communication)" (Figure 6 caption)
- External data: CN(2–1) map of the CND for comparison  
  > "show CN(2–1) emission of the CND at a resolution of 4.0 ′′ × 2.6 ′′ for orientation (compare Fig. 1; CN data: Martín et al. 2012)." (Figure 4 caption) [from Martín et al. 2012]
- External data: Stellar positions/velocities for IRS sources  
  > "References for the source positions and velocities are (P06) Paumard et al. (2006), (V06) Viehmann et al. (2006)" (Table 3) [from Paumard et al. 2006; Viehmann et al. 2006]
- External data: Critical densities from LAMDA  
  > "based on data from the Leiden Atomic and Molecular Database (LAMDA; Schöier et al. 2005" (Table 2) [from Schöier et al. 2005]

## Processing

### Calibration

- pipeline or manual: Basic calibration with archive-provided reduction scripts  
  > "using the reduction scripts provided with the archive data." (2.2 Data calibration)
- casa version: CASA 3.4 for calibration; CASA 4.3 for imaging/analysis  
  > "All further reduction, imaging, and analysis were carried out in CASAv.4.3." (2.2 Data calibration)
- pipeline version: _not stated_
- archive products used as is: _not stated_
- flux calibrator: _not stated_
- flux scale uncertainty: <17%, 9%, 10% in bands 3, 6, 7  
  > "The uncertainty in the flux calibration is less than 17%, 9%, and 10% in band 3, 6, and 7, respectively." (2.2 Data calibration)
- self calibration: Phase, then amplitude, then amplitude-phase self-cal; DR improved 11.4, 31.9, 57.7x to 4500, 7600, 11200  
  > "we performed an elaborate and careful self-calibration not only on phase but also on amplitude, despite the variable nature of the source." (2.2 Data calibration)

### Imaging

- task: immoments for moment maps  
  > "we created the moment maps, i.e., integrated flux (0th order) and velocity field (1st order), for the velocity ranges given in Table 2 using the CASA task immoments." (2.3 Line and continuum imaging)
- deconvolver: _not stated_
- weighting robust: natural weighting (uniform also used for some continuum fits)  
  > "We weighted the line and continuum data naturally" (2.3 Line and continuum imaging)
- uv taper: _not stated_
- cell size: 0.15, 0.075, 0.05 arcsec  
  > "a pixel size of 0.15, 0.075, and 0.05 ′′, respectively." (2.3 Line and continuum imaging)
- image size: 768 × 768 pixels  
  > "restored the images with 768 × 768 pixels and a pixel size of 0.15, 0.075, and 0.05 ′′, respectively." (2.3 Line and continuum imaging)
- masking: clipped at ≥3σ before moments  
  > "All line (cube channels) and continuum data were clipped at ≥ 3σ to avoid the inclusion of noise and dilution effects." (2.3 Line and continuum imaging)
- multiscale scales: _not stated_
- continuum subtraction: uv-plane continuum subtraction; continuum from line-free channels  
  > "The subtraction of the continuum from the uv data gave access to the emission line information." (2.2 Data calibration)
- line free channels: _not stated_
- primary beam correction: Moment 0 and continuum maps corrected to 10% primary beam level  
  > "all moment 0 maps, i.e., integrated flux maps and the continuum maps are corrected for the primary beam attenuation out to a primary beam level of 10%." (2.3 Line and continuum imaging)
- array combination: _not stated_
- smoothing: uv-tapering and common restoring beam for ratio maps  
  > "we uv tapered and restored the images and image cubes with the same beam size per ratio" (2.4 Obtaining spectral and spatial properties of the sources)
- final beam: _not stated_
- final rms: _not stated_

### Inherited from earlier work

- Electron temperature LTE formula  
  > "we use the formula given in Zhao et al. (2010) to derive the LTE electron temperature from the H39α and the continuum emission." (4.2 Electron temperature) [from Zhao et al. (2010)]
- CND and minispiral nomenclature  
  > "Following the CND nomenclature of Christopher et al. (2005) and Martín et al. (2012)" (3. Results and analysis) [from Christopher et al. (2005); Martín et al. (2012); Paumard et al. (2004)]

### Not stated but needed to reproduce (our reading)

- Self-calibration solution intervals, reference antenna, flagging details
- tclean/clean parameters (deconvolver, threshold, iterations, masks)
- Line-free channels used for continuum
- Which calibrators were used for flux/bandpass/phase
- Exact formula/constants for Te and mass estimates
- Choice of 5'' taper details and velocity-binning specifics

## Analysis recipe

1. **Calibrate and self-calibrate**: Archive scripts in CASA 3.4, then flagging and phase, amplitude and amplitude-phase self-calibration in CASA 4.3  
  > "We inspected the visibilities and flagged residual noisy data." (2.2 Data calibration)
   - software: CASA
   - fitting: _not stated_
   - validation: Dynamic range improvement quoted  
  > "yields a total improvement of the DR by a factor of 11.4, 31.9, and 57.7, respectively." (2.2 Data calibration)
2. **Image continuum and line cubes, make moment maps**: Natural weighted imaging, continuum subtraction in uv, 3σ clipping, immoments, primary beam correction  
  > "From the clipped line cubes, we created the moment maps" (2.3 Line and continuum imaging)
   - software: CASA immoments
   - fitting: _not stated_
   - validation: Missing flux estimated by comparing 5''-tapered CS map with 0.75'' map smoothed to 5''  
  > "Considering these scales, about 20-40% of the emission is resolved out at 0.75”." (3.4 Molecular gas in the inner 40 arcseconds)
3. **Catalogue clumps and sources**: 2D Gaussian fits with imfit; spectra from beam-sized apertures fit with MPFIT  
  > "Positions, sizes, and contained fluxes were derived with the CASAv4.3 task imfit fitting a 2D Gaussian" (2.4 Obtaining spectral and spatial properties of the sources)
   - software: CASA imfit, MPFIT
   - fitting: Gaussian line fits; visual estimates when fit fails  
  > "we estimate the uncertainties and/or the parameters by visual inspection." (2.4 Obtaining spectral and spatial properties of the sources)
   - validation: _not stated_
4. **Spectral index maps**: Power law S∝ν^α between tapered same-resolution continuum maps clipped at 5σ  
  > "we clipped the tapered (same resolution) continuum maps at 5σ before primary beam correction." (4.1 Continuum spectral index)
   - fitting: _not stated_
   - validation: Error maps from S/N and flux calibration  
  > "A map of the uncertainties based on the S/N and the flux calibration uncertainties is given" (4.1 Continuum spectral index)
5. **LTE electron temperature**: Zhao et al. formula from H39α and 100 GHz continuum, with integrated line flux in place of S_L ΔV_FWHM; H51β scaled by Hα/Hβ=3.55  
  > "the assumption of optically thin RRL and continuum emission and LTE conditions for the ionized gas, we use the formula given in Zhao et al. (2010) to derive the LTE electron temperature from" (4.2 Electron temperature)
   - assumption: Optically thin, LTE, correction factor 0.904 at 100 GHz, Te~10^4 K  
  > "α(ν = 100 GHz, T e ∼ 10 4 K)∼ 0.904 (Mezger & Henderson 1967)" (4.2 Electron temperature)
   - fitting: _not stated_
   - validation: Compared to H51β-based map and literature  
  > "We derive T e from the H51β line (Fig. 9), which is the better detected of the two band 3 Hβ lines, by scaling its flux to the Hα emission using the LTE Hα/Hβ ratio of 3.55" (4.2 Electron temperature)
6. **Molecular line ratios**: Channel flux ratios in beam-sized apertures of tapered images per region  
  > "We calculated the line luminosity ratios for selected molecules based on the channel fluxes (Table E.1)" (2.4 Obtaining spectral and spatial properties of the sources)
   - fitting: _not stated_
   - validation: _not stated_

## Software

- **CASA** 3.4 (calibration), 4.3 (imaging/analysis): Calibration, self-calibration, imaging, moment maps, imfit  
  > "All further reduction, imaging, and analysis were carried out in CASAv.4.3." (2.2 Data calibration)
- **MPFIT (Python)** : Spectral line fitting  
  > "were fitted with the MPFIT module in Python" (2.4 Obtaining spectral and spatial properties of the sources)

## Numeric results

| quantity | value | uncertainty | units | step | quote |
|---|---|---|---|---|---|
| Sgr A* spectral index 100-250 GHz | 0.58 | ±0.21 | dimensionless | 4 | α 100−250 ∼ 0.58 ± 0.21 |
| Sgr A* spectral index 250-340 GHz | 0.17 | ±0.45 | dimensionless | 4 | α 250−340 = 0.17 ± 0.45 |
| Minispiral LTE electron temperature | ~6000 | ±1000 | K | 5 | the temperature range of 6000 ± 1000 K is in agreement with |
| Te in minicavity | 6500 | ±500 | K | 5 | resulting in an electron temperature of 6500 ± 500 K throughout this region |
| Total gas mass of central association | ~5 | not stated | Msun | 0 | we obtain a total gas mass of the CA of about 5 M ⊙ |
| Missing CS flux at 0.75'' | 20-40 | not stated | percent | 2 | about 20-40% of the emission is resolved out at 0.75”. |

## Qualitative findings

- CS/X ratios are more than three times higher in the center and SEW than in the triop and CND clumps  
  > "more than three times higher than in the triop and single clumps further out of the center" (4.4 The molecular line ratios)
- N2H+ coincides with the largest IRDCs outside the CND  
  > "Outside the CND, we find the traditionally quiescent gas tracer N 2 H + coinciding with the largest IRDCs in the field." (6. Summary)

## Claim tuples

- H: Is the electron temperature of the minispiral uniform? | E: LTE Te from H39α and 100 GHz continuum, cross-checked with H51β | R: Te ~6000 K, 5000-9000 K locally | F: Almost uniform Te around 6000 K | **supported**
- H: What emission mechanism dominates Sgr A* and minispiral continuum? | E: Spectral index maps 100-250-340 GHz | R: Sgr A* α~0.5 at 100-250 GHz, ~0 at 250-340; bright sources ~-0.1 | F: Synchrotron for Sgr A*, free-free in bright sources, dust emerging in exterior | **supported**
- H: Is the molecular gas in the central 20'' closer to Sgr A* than the CND? | E: Compared CS/X ratios across regions | R: CS/X three times higher in CA | F: CA is closer to the center than the CND (higher excitation/abundance enhancement) | **partially**
- H: Is there high velocity molecular gas near Sgr A*? | E: Channel maps of CS and SiO | R: CS and SiO clumps at 100-200 km/s | F: Possibly tidally sheared infalling cloud remnants | **partially**

## Reasoning

- Why this data: ALMA gives needed sensitivity and resolution for the GC  
  > "A detailed analysis requires high sensitivity and angular resolution. Both can now be obtained using ALMA." (2. ALMA observations and data reduction)
- Why this method: _not stated_
- Alternative: Clipping uv ranges to match bands rejected because of image quality loss  
  > "this reduced the image quality so significantly, i.e., distortions and flux losses of up to 50 % even when clipping only large baselines, that we refrained from applying this procedure." (2.4 Obtaining spectral and spatial properties of the sources)
- How they decided it was enough: _not stated_
- Limitation (authors): Low velocity resolution (15-50 km/s) and missing flux limit RRL and ratio analysis  
  > "our RRL maps might be affected by the large velocity bins given by the observational setup" (3.2 Radio recombination lines)
- Caveat (inferred, ours): Line ratios are rough, no uncertainties, cross-band ratios only lower limits
- Caveat (inferred, ours): Self-calibration on a variable source may alter fluxes
- Caveat (inferred, ours): Interpretation of CA distance rests on excitation arguments without radiative transfer modelling

## Reproducibility

- Data public (paper): Archive data, project 2011.0.00887.S; reduced FITS at CDS  
  > "Supplementary data (reduced FITS images and datacubes) of the continuum and line emission listed in Tables 1 and 2 are available at the CDS" (Title footnote)
- Products in archive: _not stated_
- Missing: Self-cal parameters
- Missing: Clean/imaging parameters
- Missing: Line-free channel selection
- Missing: Calibrator names
- Data volume (inferred): ~10-30 GB for three bands of one Cycle 0 execution
- Score (inferred): 3/5, Public archival data and tables with numbers, but processing details (self-cal, clean settings) are sparse.
- Rediscovery candidate: no, Key numbers (spectral indices, Te) are reproducible in principle but the recipe lacks imaging and self-calibration details and the main results are largely qualitative.

## Links

- Method: Zhao et al. (2010) (LTE electron temperature formula)
- Companion: Moser et al. 2017, in prep. (lower resolution N2H+ and CH3OH(2-1) observations)
- Related: Kunneriath et al. 2012 CARMA 1.3 mm

## Checks

```json
{
 "quotes": 72,
 "quotes_ok": 72,
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
  "facts": 74,
  "stated": 51,
  "rate": 0.689
 },
 "evidence_ok": true
}
```
