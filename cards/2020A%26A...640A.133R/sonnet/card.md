# DEATHSTAR: Nearby AGB stars with the Atacama Compact Array. I. CO envelope sizes and asymmetries: A new hope for accurate mass-loss-rate estimates

`2020A&A...640A.133R` | Astronomy and Astrophysics 2020 | first author: Ramstedt, S. | arXiv: 2008.07885 | DOI: 10.1051/0004-6361/201936874

Card schema 1.0 | model claude-sonnet-5-5 | depth full | type large_program_or_survey

## Science

- Fields: evolved_stars
- Question: What are the sizes of the 12CO emitting regions of the circumstellar envelopes of 42 southern M- and C-type AGB stars, and how symmetric are the outflows?  
  > "The aim in this first publication is to constrain the sizes of the [12] CO emitting region from the circumstellar envelopes around 42 mostly southern AGB stars" (abstract)
- Target **42 AGB stars (21 M-type, 21 C-type), e.g. R Leo, R Hya, U Hya, IRC-10529, TW Hor**: coordinates SIMBAD J2000 coordinates (not listed)  
  > "The 42 stars (21 M-type, 21 C-type), which were observed with ALMA ACA in Cycle 4 and for which the data are presented in this paper, are listed in Table 1" (2. The sample); z/distance 65 pc to 1770 pc (previous-analysis distances, Table 1)  
  > "The 42 stars (21 M-type, 21 C-type), which were observed with ALMA ACA in Cycle 4 and for which the data are presented in this paper, are listed in Table 1" (2. The sample); distance from Schöier & Olofsson (2001), González Delgado et al. (2003), Danilovich et al. (2015); Hipparcos, P-L relations, SED modelling; Gaia DR2 for comparison  
  > "The 42 stars (21 M-type, 21 C-type), which were observed with ALMA ACA in Cycle 4 and for which the data are presented in this paper, are listed in Table 1" (2. The sample)

## Data provenance

- ALMA projects: 2016.2.00025.S, 2017.1.00595.S
- bands: Band 6 and Band 7  
  > "in Cycle 4 in Bands 6 and 7" (3.1 Observations with the ACA)
- frequencies and spectral setup: Four spectral windows per band; Band 6 centered at 216.4, 218.3, 230.7, 232.1 GHz; Band 7 at 330.75, 332.25, 343.52, 345.6 GHz; 0.75 km/s resolution in CO windows  
  > "In Band 6 the windows were centered on 216.4, 218.3, 230.7, and 232.1 GHz. In Band 7 they were centered on 330.75, 332.25, 343.52, and 345.6 GHz." (3.1 Observations with the ACA); "The spectral resolution of the imaged data was set to 0.75 km s [−][1] in the [12] CO and [13] CO windows" (3.1 Observations with the ACA)
- continuum bandwidth: _not stated_
- arrays: ACA stand-alone mode (no total power)  
  > "The 42 sample sources listed in Table 1 were observed with the ACA in stand-alone mode in Cycle 4" (3.1 Observations with the ACA)
- configurations: _not stated_
- baselines: _not stated_
- angular resolution: Per-source beams in Table B.1, mostly ~6-7″ x 4-5″ (Band 6) and ~4-5″ x 3″ (Band 7)  
  > "L 2 Pup 6.5 × 5.4 67.0 52 3.9 × 3.5 -70.1 103" (Table B.1)
- max recoverable scale: 25″ ± 4″ (Band 6), 18″ ± 2″ (Band 7) on average  
  > "on average it was 25 [′′] ± 4 [′′] and 18 [′′] ± 2 [′′] for Band 6 and 7, respectively." (3.1 Observations with the ACA)
- sensitivity: Science goal: 5.5″ and 40 mJy/beam (Band 6), 3-4″ and 50 mJy/beam (Band 7) at 1.5 km/s  
  > "The science goal beam widths and rms values at 1.5 km s [−][1] were 5.5 [′′] and 40 mJy beam [−][1] as well as 3-4 [′′] and 50 mJy beam [−][1] in Bands 6 and 7, respectively." (3.1 Observations with the ACA)
- time on source: _not stated_
- observing dates: _not stated_
- pi or archival as stated: _not stated_
- Line: 12CO J=2-1 (not stated)
- Line: 12CO J=3-2 (not stated)
- Line: 13CO J=3-2 (330.588 GHz)
- Other facility **Gaia DR2**: Distances (Bailer-Jones et al. 2018) for comparison  
  > "Gaia data release 2 (DR2) (Gaia Collaboration et al. 2016, 2018) distance from Bailer-Jones et al. (2018)." (2. The sample)
- External data: Mass-loss rates, wind velocities and distances for the 42 stars (Table 1)  
  > "distance according to the previous analysis in Schöier & Olofsson (2001), González Delgado et al. (2003), and Danilovich et al. (2015)" (2. The sample) [from Schöier & Olofsson (2001); González Delgado et al. (2003); Danilovich et al. (2015)]
- External data: Photodissociation model grid used for predicted CO sizes  
  > "based on the recent models by Saberi et al. (2019)" (4.2.1 Gaussian distribution fits) [from Saberi et al. (2019)]
- External data: Gaia DR2 distances  
  > "Gaia data release 2 (DR2) (Gaia Collaboration et al. 2016, 2018) distance from Bailer-Jones et al. (2018)." (2. The sample) [from Bailer-Jones et al. (2018)]
- Simulation/model as data: Previous best-fit 1D radiative transfer models of six stars (3 M, 3 C), turned into image cubes and run through the CASA ALMA simulator  
  > "The output from the best-fit radiative transfer models of the six sources was used to create image cubes with an imaging ray-tracing program" (3.3. Emission distributions from 1D radiative transfer models)
- Simulation/model as data: LIME 1.9.5 models of the Saberi et al. (2019) photodissociation model grid, fit with Gaussians  
  > "We used the LIME 1.9.5 radiative transfer code (Brinch & Hogerheijde 2010) to produce radiative transfer models of the photodissociation models from Saberi et al. (2019)" (4.2.1 Gaussian distribution fits)

## Processing

### Calibration

- pipeline or manual: Standard pipeline scripts  
  > "All data were calibrated using the standard pipeline scripts" (3.1 Observations with the ACA)
- casa version: _not stated_
- pipeline version: _not stated_
- archive products used as is: No; reprocessed data are better than archive products  
  > "The processed data have improved the quality compared to the data products provided in the ALMA archive." (3.1 Observations with the ACA)
- flux calibrator: _not stated_
- flux scale uncertainty: _not stated_
- self calibration: Using typically two channels across the CO peak, applied to all sources in both bands; 10-15% S/N improvement  
  > "Self-calibration was performed using a small number of channels, typically two, across the peak [12] CO line emission and applied to all sources in both bands." (3.1 Observations with the ACA)

### Imaging

- task: CASA (clean) imaging; each spectral window imaged separately  
  > "dow in both bands were imaged separately" (3.1. Observations with the ACA)
- deconvolver: 10000 clean iterations; 20000 for sources brighter than 20 Jy  
  > "All data were cleaned initially using 10000 iterations." (3.1 Observations with the ACA); "finally 20000 iterations were applied to all bright (>20 Jy) sources." (3.1 Observations with the ACA)
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
- final beam: Per-source, Table B.1 (e.g. 6.5 × 5.4″ Band 6 for L2 Pup)  
  > "L 2 Pup 6.5 × 5.4 67.0 52 3.9 × 3.5 -70.1 103" (Table B.1)
- final rms: Measured in emission-free channels at 0.75 km/s; ~40-112 mJy/beam Band 6, ~94-340 mJy/beam Band 7  
  > "root mean square (rms) noise levels at a velocity resolution of 0.75 km s [−][1], which were measured in the emission-free channels in the [12] CO line window of the final images" (3.1 Observations with the ACA)

### Inherited from earlier work

- Photodissociation radius computed with formulae fit to the Mamon et al. model  
  > "was calculated using Eqns. 10 and 11 from Schöier & Olofsson (2001), which were derived (Stanek et al. 1995) by fitting the results of the CO photodissociation model by Mamon et al. (1988)." (4.2.1 Gaussian distribution fits) [from Schöier & Olofsson (2001); Stanek et al. (1995); Mamon et al. (1988)]
- Previous best-fit radiative transfer models adapted for the six-source comparison  
  > "The models were directly adapted from the previous best-fit models (Danilovich et al. 2015, see also Table 1)" (3.3 Emission distributions from 1D radiative transfer models) [from Danilovich et al. (2015)]
- Imaging ray-tracing program used to create image cubes  
  > "an imaging ray-tracing program that is part of the radiative transfer package developed by Schöier (2000)" (3.3 Emission distributions from 1D radiative transfer models) [from Schöier (2000)]

### Not stated but needed to reproduce (our reading)

- CASA version and pipeline version
- tclean parameters: weighting/robust, cell size, image size, masks, threshold, deconvolver
- Continuum subtraction and line-free channels
- Self-calibration solution interval and reference antenna
- Starting model/initial guesses and channel selection for UVMULTIFIT fits
- Exact CSE parameters and CASA simulator settings for the model comparison
- Flux calibrators and flux-scale uncertainty
- Method for evaluating errors on Gaussian fits and spline-fit details

## Analysis recipe

1. **Calibrate and image the ACA data**: Standard pipeline calibration, self-calibration on ~2 channels, CASA cleaning, per-window imaging at 0.75 km/s  
  > "All data were calibrated using the standard pipeline scripts and imaged using the Common Astronomy Software Applications package" (3.1 Observations with the ACA)
   - software: CASA
   - parameter: 10000 clean iterations; 20000 for >20 Jy sources  
  > "finally 20000 iterations were applied to all bright (>20 Jy) sources." (3.1 Observations with the ACA)
   - fitting: _not stated_
   - validation: _not stated_
2. **Extract line profiles**: Spectra from image cubes in a circular aperture of 18″ (CO) ; peak, center velocity and width at 5% of peak  
  > "A circular aperture of 18 [′′] was used for both transitions" (4.1 Line profiles); "The center velocity was measured at the center between the two points where the flux reaches 5% of the peak value at the extreme velocities." (4.1 Line profiles)
   - fitting: _not stated_
   - validation: _not stated_
3. **Fit Gaussian to visibilities per channel**: Least-squares fit of a Gaussian in the uv-plane for each channel of CO(2-1) and (3-2); gives center, major axis, axis ratio, PA; size taken at line center velocity  
  > "The least-square fit gives the center position coordinates, the major axis and the axis ratio of the best-fit Gaussian, and the position angle of the major axis for each channel" (3.2 Fitting the emission distribution in the uv-plane)
   - software: UVMULTIFIT
   - parameter: Error = average error of fits in the two channels adjacent to center velocity; colon marks uncertain values  
  > "The error is the average error of the fits in the two channels adjacent to the center velocity." (4.2.1 Gaussian distribution fits)
   - fitting: Least-squares Gaussian visibility fit  
  > "The least-square fit gives the center position coordinates" (3.2 Fitting the emission distribution in the uv-plane)
   - validation: Checked fits on LIME models of Saberi et al. (2019) photodissociation models  
  > "Subsequently, we fit a Gaussian profile to the CO(2-1) emission at the systemic velocity using a 1 km s [−][1] channel width using the same method as in Sect. 3.2." (4.2.1 Gaussian distribution fits)
4. **Compare with photodissociation predictions**: Compare fitted major axis (times distance) with Saberi et al. (2019) photodissociation diameters and LIME-derived Gaussian sizes versus Mdot/v_inf; spline fit to expected sizes  
  > "A spline fit to the expected CO(2-1) size is shown by the solid lines in Fig. 4" (4.2.1 Gaussian distribution fits)
   - software: LIME
   - parameter: v_inf = 7.5 km/s for the model grid  
  > "The photodissociation radii were calculated across the range of˙ M/v ∞ for v ∞ = 7.5 km s [−][1] ." (4.2.1 Gaussian distribution fits)
   - assumption: Distances from previous analyses (Table 1); CO/H2 = 2e-4 (M) and 1e-3 (C)  
  > "is assumed to be 2 × 10 [−][4] for the M-type stars and 1 × 10 [−][3] for the C-type stars." (2. The sample)
   - fitting: _not stated_
   - validation: _not stated_
5. **Compare with 1D radiative transfer models for six stars**: Create image cubes from previous best-fit models, simulate ACA observations in CASA, apply same Gaussian fitting  
  > "they were run through the ALMA simulator in CASA to simulate observations with the same configuration and under the same conditions as during the ACA observations" (3.3 Emission distributions from 1D radiative transfer models)
   - software: CASA, UVMULTIFIT
   - parameter: 32×32 pixels of 0.8″ (CO 2-1) and 0.7″ (CO 3-2)  
  > "The image cubes were created with 32×32 pixels with sizes of 0 [′′] . 8 and 0 [′′] . 7 for each channel across the CO(2-1) and (3-2) line, respectively." (3.3 Emission distributions from 1D radiative transfer models)
   - fitting: _not stated_
   - validation: No attempt to improve the fit to the ACA data  
  > "no attempt has been made to improve the fit to the ALMA ACA data" (3.3 Emission distributions from 1D radiative transfer models)
6. **Classify asymmetries**: Inspect line profiles and per-channel fit results (size, center offsets) for eight feature types  
  > "These features can be divided into two classes: Features that are consistent with a spherically symmetric CSE and those that are not." (4.3 Asymmetrical features)
   - fitting: _not stated_
   - validation: _not stated_

## Software

- **CASA** : Calibration, imaging, ALMA simulator  
  > "imaged using the Common Astronomy Software Applications package (CASA; McMullin et al. 2007)" (3.1 Observations with the ACA)
- **UVMULTIFIT** : Gaussian fitting in the uv-plane  
  > "using the CASA task UVMULTIFIT (Martí-Vidal et al. 2014)" (3.2 Fitting the emission distribution in the uv-plane)
- **LIME** 1.9.5: Radiative transfer models of the Saberi et al. photodissociation grid  
  > "We used the LIME 1.9.5 radiative transfer code (Brinch & Hogerheijde 2010)" (4.2.1 Gaussian distribution fits)
- **DUSTY** : SED modelling for earlier distances  
  > "by using the dust radiative transfer code DUSTY (Ivezic et al. 1999) to model the spectral energy distribution (SED)" (2. The sample)

## Numeric results

| quantity | value | uncertainty | units | step | quote |
|---|---|---|---|---|---|
| Sources with CO(2-1) axis ratio within 10% of unity | 26/42 | not stated | sources | 3 | for a small majority of the sources (26/42), the CO(2-1) axis ratio deviates ≤10% from one |
| Average maximum recoverable scale, Band 6 | 25 | 4 | arcsec | 1 | on average it was 25 [′′] ± 4 [′′] and 18 [′′] ± 2 [′′] |
| CO(2-1) Gaussian major axis, R Leo | 10.00 | 0.11 | arcsec | 3 | R Leo 18.2 10.00±0.11 0.88±0.02 |
| CO(2-1) Gaussian major axis, W Hya | 10.92 | 0.12 | arcsec | 3 | W Hya 22.6 10.92±0.12 0.75±0.06 |
| Self-calibration S/N improvement | 10-15 | not stated | percent | 1 | This improved the signal-to-noise ratio by 10-15% on average. |

## Qualitative findings

- About a third of sources show strong asymmetries; smaller-scale deviations in more  
  > "For about a third of the sources, indications of strong asymmetries are detected." (5. Discussion and summary)
- CO(2-1) major axis is a factor of two smaller than 2Rp/D for semi-regular/irregular and three smaller for Miras  
  > "the CO(2-1) major axis is a factor of two smaller than 2×R p /D for the semi- and irregular variables, and a factor of three smaller for the Mira variables" (4.2.1 Gaussian distribution fits)

## Claim tuples

- H: CO envelopes are larger for C-type than M-type stars if CO/H2 is higher in C-type | E: Gaussian fits to CO(2-1) ACA visibilities for 21 M and 21 C stars | R: CO envelope sizes generally larger for C-type | F: Consistent with higher CO abundance in C-type stars | **supported**
- H: Measured CO(2-1) size follows photodissociation predictions versus circumstellar density | E: Compare fitted size vs Mdot/v_inf with Saberi et al. grid and LIME-modelled Gaussian sizes | R: Broad agreement with large scatter; low-Mdot sources show size independent of density; Miras increase with density; M-type consistently smaller than predicted | F: Sizes in broad agreement but with systematic differences by stellar type | **partially**
- H: Most AGB CSEs are spherically symmetric and smooth | E: Line profiles and per-channel Gaussian fit axis ratios, centers | R: Majority consistent with smooth outflow on large scales; about a third show strong asymmetries | F: Consistent with earlier northern interferometric results | **supported**

## Reasoning

- Why this data: _not stated_
- Why this method: Direct interferometric size measurement removes dependence on photodissociation models and shielding functions  
  > "A more exact way to determine the [12] CO envelope size (e.g., independent of our knowledge of shielding functions) is to constrain it directly using interferometry." (1. Introduction)
- How they decided it was enough: _not stated_
- Limitation (authors): Gaussian radii less reliable for the densest CSEs (Mdot/v_inf ≳ 1e-7) because the profile is non-Gaussian  
  > "the Gaussian radii determined for the CSEs with the highest density, M [˙] /v ∞ ≳ 10 [−][7] M ⊙ km s [−][1] yr [−][1], are less reliable." (4.2.1 Gaussian distribution fits)
- Limitation (authors): Distances uncertain; large source of scatter  
  > "The most obvious one is the uncertainty of the distance, which introduces significant scatter in the size determinations." (4.2.1 Gaussian distribution fits)
- Limitation (authors): Beams larger and elongated than aimed for; resolved-out flux without total-power data  
  > "For a significant fraction of the data sets, the beams are larger than what was aimed for as well as elongated" (3.1 Observations with the ACA)
- Caveat (inferred, ours): Gaussian FWHM is only a proxy for envelope size; no full radiative transfer
- Caveat (inferred, ours): Distances are old and heterogeneous; Gaia comparison shows factors of several
- Caveat (inferred, ours): Resolved-out flux affects fits and ACA-only data
- Caveat (inferred, ours): Asymmetry classification is qualitative with no objective criteria

## Reproducibility

- Data public (paper): Reprocessed images available through CDS and project website; raw data in ALMA archive  
  > "dow in both bands were imaged separately and can be accessed" (3.1. Observations with the ACA)
- Products in archive: _not stated_
- Missing: CASA version
- Missing: tclean imaging parameters
- Missing: UVMULTIFIT initial settings and channel handling
- Missing: Details of simulator setup for model comparison
- Data volume (inferred): ~50-100 GB for 42 ACA targets in two bands (raw), less if archive products used
- Score (inferred): 3/5, Data are public and approach is clear, but imaging and fitting parameters are mostly unstated; reduced products are provided via CDS.
- Rediscovery candidate: no, Key imaging and fitting settings are not given, and results depend on previously derived inputs (distances, Mdot).

## Links

- Method: Martí-Vidal et al. 2014 (UVMULTIFIT visibility fitting)
- Method: Saberi et al. (2019) (Photodissociation model grid used for predictions)
- Companion: Schöier & Olofsson (2001) (Source of radiative transfer modelling, mass-loss rates and photodissociation formulae)
- Companion: Danilovich et al. (2015) (Previous best-fit models for the subsample)
- Related: DEATHSTAR
- Related: COSAS
- Related: Neri et al. (1998) PdB survey

## Checks

```json
{
 "quotes": 68,
 "quotes_ok": 68,
 "quote_pass_rate": 1.0,
 "quotes_too_long": 0,
 "unsupported_facts": 0,
 "project_codes": 2,
 "codes_not_in_text": [],
 "codes_not_in_obscore": [],
 "obscore_codes_not_in_card": [],
 "codes_printed_but_missing": [],
 "numeric_results": 5,
 "numeric_problems": 0,
 "fill": {
  "facts": 84,
  "stated": 51,
  "rate": 0.607
 },
 "evidence_ok": true
}
```
