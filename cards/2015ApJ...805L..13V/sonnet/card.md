# Si-bearing Molecules Toward IRC+10216: ALMA Unveils the Molecular Envelope of CWLeo

`2015ApJ...805L..13V` | The Astrophysical Journal Letters 2015 | first author: Velilla Prieto, L. | arXiv: 1504.05704 | DOI: 10.1088/2041-8205/805/2/L13

Card schema 1.0 | model claude-sonnet-5-5 | depth full | type observational_alma_primary

## Science

- Fields: evolved_stars, astrochemistry
- Question: What are the spatial distributions and excitation conditions of Si-bearing molecules (SiS, SiO, SiC2) in the envelope of IRC+10216?  
  > "We analyze the excitation conditions of the vibrationally excited SiS using the population diagram technique, and we use a large velocity gradient model to compare with the observations." (abstract)
- Target **IRC+10216 (CW Leo)**: coordinates RA 9h47m57.446s, Dec +13d16m43.86s (J2000)  
  > "The continuum comes from a point-like source located at $\alpha$=9$^{\mathrm{h}}$47$^{\mathrm{m}}$57$^{\mathrm{s}}$446 and $\delta$=13$^{\circ}$16$^{'}$43$''$86 (J2000)" (Observations); "considering a distance of $\sim$130 pc to the star from us (cite: gro12)" (3.1 Spatial distribution of Si-bearing molecules); z/distance ~130 pc  
  > "The continuum comes from a point-like source located at $\alpha$=9$^{\mathrm{h}}$47$^{\mathrm{m}}$57$^{\mathrm{s}}$446 and $\delta$=13$^{\circ}$16$^{'}$43$''$86 (J2000)" (Observations); "considering a distance of $\sim$130 pc to the star from us (cite: gro12)" (3.1 Spatial distribution of Si-bearing molecules); distance from Groenewegen et al. 2012 (cite: gro12)  
  > "The continuum comes from a point-like source located at $\alpha$=9$^{\mathrm{h}}$47$^{\mathrm{m}}$57$^{\mathrm{s}}$446 and $\delta$=13$^{\circ}$16$^{'}$43$''$86 (J2000)" (Observations); "considering a distance of $\sim$130 pc to the star from us (cite: gro12)" (3.1 Spatial distribution of Si-bearing molecules)

## Data provenance

- ALMA projects: 2011.0.00229.S
- bands: Band 6, 255.3 to 274.8 GHz, four setups  
  > "IRC+10216 was observed in the frequency range 255.3 to 274.8 GHz (band 6) covered by four different setups with a bandwidth of $\sim$5 GHz" (Observations)
- frequencies and spectral setup: channel spacing 0.49 MHz, effective resolution 0.98 MHz, ~5 GHz per setup  
  > "a channel spacing of 0.49 MHz and an effective resolution of 0.98 MHz" (Observations)
- continuum bandwidth: _not stated_
- arrays: _not stated_
- configurations: _not stated_
- baselines: up to 402 m, shortest ~20 m, sixteen antennas  
  > "The observations were performed using sixteen antennas covering baselines up to 402 m" (Observations)
- angular resolution: ~0.6"  
  > "that allowed us to obtain an angular resolution of $\sim$0.6$''$" (Observations)
- max recoverable scale: ≲12"  
  > "which allow us to recover structures with a size up to $\lesssim$12$''$" (Observations)
- sensitivity: RMS 6, 10, 17, 6 mJy/beam for setups 3-6  
  > "|    3     |   269.9–274.8   |         6         |  0.61$\times$0.47  |  23.2–22.9   |" (Table 1)
- time on source: Two runs of 72 min each, 26 min on source  
  > "Two runs of 72 minutes each were performed, of which 26 minutes correspond to correlations on source." (Observations)
- observing dates: 2012 April 8 and 23, Cycle 0  
  > "The observations were carried out with ALMA[^1] between 2012 April 8 and 23 during Cycle 0." (Observations)
- pi or archival as stated: _not stated_
- Line: SiS J=15-14, v=0-7 (tentative v=8-10) (not stated)
- Line: SiO J=6-5, v=0-2 (not stated)
- Line: SiC2 11(6,6)-10(6,5) and others (not stated)
- External data: SiS collisional data, extrapolated to high rovibrational levels  
  > "The SiS collisional data were taken from (cite: tob08) and extrapolated to high rovibrational levels." (3.2 Vibrationally excited SiS) [from (cite: tob08)]
- External data: SiS dipole moment function, semiempirical  
  > "The dipole moment function used for SiS was determined semiempirically by (cite: LopezPineiro87)" (3.2.1) [from (cite: LopezPineiro87)]
- External data: Stellar parameters: distance ~130 pc, Teff ~2330 K, radius ~4e13 cm  
  > "We adopted a distance to the star of $\sim$130 pc, an effective temperature of $\sim$2330 K and a stellar radius of $\sim$4$\times$10$^{13}$ cm" (3.2 Vibrationally excited SiS) [from (cite: cer00; mon00; gro12)]

## Processing

### Calibration

- pipeline or manual: Calibration with CASA; details in Cernicharo et al. 2013  
  > "The calibration of the data was performed using CASA[^2] and data analysis with GILDAS[^3]." (Observations)
- casa version: _not stated_
- pipeline version: _not stated_
- archive products used as is: _not stated_
- flux calibrator: _not stated_
- flux scale uncertainty: _not stated_
- self calibration: _not stated_

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
- final beam: 0.61x0.47", 0.86x0.47", 0.96x0.47", 0.77x0.60" for setups 3-6  
  > "|    6     |   255.3–260.2   |         6         |  0.77$\times$0.60  |  24.6–24.2   |" (Table 1)
- final rms: _not stated_

### Inherited from earlier work

- Calibration and imaging restoration details  
  > "Further details about calibration and imaging restoration can be found in (cite: cer13)." (Observations) [from (cite: cer13)]
- Reduced H2 density by ~2 in dust nucleation zone for LVG model  
  > "We modified the H$_2$ density, decreasing it by a factor $\sim$2, as described in (cite: cer13)" (3.2 Vibrationally excited SiS) [from (cite: cer13)]
- LVG model of inner layers abundances (2012 model)  
  > "the model of (cite: agu12), which was used to reproduce the molecular abundances in the inner layers of IRC+10216" (3.2 Vibrationally excited SiS) [from (cite: agu12)]

### Not stated but needed to reproduce (our reading)

- CASA version and calibrators
- Imaging parameters (weighting, cell, deconvolver, masks)
- Continuum subtraction and line-free channels
- Rotational diagram fit values (Tvib, N) not tabulated in text
- LVG abundance profiles and SiS abundance values
- Line integrated intensities and FWHM values

## Analysis recipe

1. **Map molecular emission**: Channel maps of SiC2, 29SiO and 29SiS at offset velocities relative to systemic velocity  
  > "we show maps of the emission of the lines SiC$_2$ $J_{K_{\mathrm{a}},K_{\mathrm{c}}}$=11$_{6,6}$ – 10$_{6,5}$, $^{29}$SiO $J$=6 – 5 and $^{29}$SiS $J$=15 – 14" (3.1 Spatial distribution of Si-bearing molecules)
   - software: GILDAS, CASA
   - fitting: _not stated_
   - validation: _not stated_
2. **Rotational diagram of vibrationally excited SiS**: Rotational diagram technique on spectra at stellar position; two linear fits (v=0-2 and v=3-7), v>=8 excluded  
  > "We considered two different linear trends for the observational data: one for the transitions with E$_{up}$$\lesssim$2500 K (i.e. v=0, 1 and 2), and a different trend for the rest (i.e. v=3–7)." (3.2 Vibrationally excited SiS)
   - software: GILDAS
   - fitting: Linear fits  
  > "We considered two different linear trends for the observational data: one for the transitions with E$_{up}$$\lesssim$2500 K (i.e. v=0, 1 and 2), and a different trend for the rest (i.e. v=3–7)." (Vibrationally excited SiS)
   - validation: _not stated_
3. **LVG modelling of SiS emission**: LVG code with two models (2012 model and modified model with H2 density /2 and SiS abundance x2) compared to observations  
  > "We used a large velocity gradient (LVG) code to model the SiS emission (cite: cer12)." (3.2 Vibrationally excited SiS)
   - software: LVG code (Cernicharo 2012)
   - assumption: Distance 130 pc, Teff 2330 K, R*=4e13 cm  
  > "We adopted a distance to the star of $\sim$130 pc, an effective temperature of $\sim$2330 K and a stellar radius of $\sim$4$\times$10$^{13}$ cm" (3.2 Vibrationally excited SiS)
   - fitting: _not stated_
   - validation: Compared Tvib and column density with rotational diagram  
  > "we obtain a good agreement with the vibrational temperature derived from the vibrational diagram and moderate discrepancies with the total column density within a factor of $\sim$2" (3.2 Vibrationally excited SiS)
4. **SiS potential energy function and dipole matrix elements**: Fit of BO potential with BOB corrections to 2863 line positions; Schrödinger equation solved variationally  
  > "The fit to the potential energy function was performed using the Levenberg–Marquardt algorithm (cite: Levenberg44; Marquardt63) to minimize the $\chi^{2}$ function" (3.2.1)
   - fitting: Levenberg-Marquardt chi2 minimization, weights by squared experimental uncertainties  
  > "The fit to the potential energy function was performed using the Levenberg–Marquardt algorithm (cite: Levenberg44; Marquardt63) to minimize the $\chi^{2}$ function, with the line positions weighted by the square of the experimental uncertainties." (SiS potential energy function and vibrational dipole moment)
   - validation: Compared with Lopez-Pineiro et al. 1987 for v<=4: excellent agreement  
  > "The agreement between our calculations and those of (cite: LopezPineiro87) for v$\le$4 is excellent." (3.2.1)

## Software

- **CASA** : Calibration  
  > "The calibration of the data was performed using CASA[^2] and data analysis with GILDAS[^3]." (Observations)
- **GILDAS** : Data analysis  
  > "The calibration of the data was performed using CASA[^2] and data analysis with GILDAS[^3]." (Observations)

## Numeric results

| quantity | value | uncertainty | units | step | quote |
|---|---|---|---|---|---|
| Continuum peak intensity | 650 | ~8 % | mJy/beam | 0 | We measured an intensity peak of 650 mJy beam$^{-1}$ with an uncertainty of $\sim$8 %. |
| SiC column density upper limit | 4.4e14 | not stated | cm^-2 | 0 | We derived an upper limit to the SiC column density of 4.4$\times$10$^{14}$ cm$^{-2}$ from the $^{29}$SiC upper limit |
| Final chi2 of SiS potential fit | 1.767 | not stated | dimensionless | 4 | The final $\chi^{2}$ value was 1.767. |
| SiS v=1 optical depth, model (i) / (ii) | ~10 / ~47 | not stated | dimensionless | 3 | $\tau$(v=1)$\sim$10 to $\tau$(v=4)$\sim$0.8 for the abundance profile ($i$) and $\tau$(v=1)$\sim$47 to $\tau$(v=8)$\sim$1.0 |

## Qualitative findings

- SiS emission is compact; SiO and SiC2 more extended; SiC2 shows a ring at ~10-11" probably partly filtered  
  > "The spatial distribution of these molecules shows compact emission for SiS and a more extended emission for SiO and SiC$_2$" (abstract)

## Claim tuples

- H: Vibrationally excited SiS lines arise from the innermost hot envelope | E: Line widths and rotational diagrams of SiS v=0-7 | R: FWHM decreases with increasing Eup; higher Tvib for high-v lines | F: High-v lines are excited close to the photosphere | **supported**
- H: LVG models reproduce SiS observations | E: Two LVG models compared with rotational diagram | R: Tvib agrees, column densities differ by ~2 | F: Discrepancy may be due to optically thick lines and beam dilution | **partially**

## Reasoning

- Why this data: _not stated_
- Why this method: _not stated_
- How they decided it was enough: _not stated_
- Limitation (authors): Ring structure of SiC2 probably filtered by shortest baselines; poor uv coverage and sidelobes for setups 3-5  
  > "Although, this ringlike structure is probably filtered in our data given the shortest baselines used." (3.1 Spatial distribution of Si-bearing molecules)
- Caveat (inferred, ours): Rotational diagram fit uncertainties and values not given
- Caveat (inferred, ours): Maser nature of v=0 and optical thickness undermine low-v fit
- Caveat (inferred, ours): Tentative lines v>=8 may be blended

## Reproducibility

- Data public (paper): ALMA project code printed  
  > "This paper makes use of the following ALMA data: ADS/JAO.ALMA#2011.0.00229.S ." (footnote 1)
- Products in archive: _not stated_
- Missing: CASA version, calibration and imaging parameters
- Missing: Line-fitting results and rotational diagram parameters
- Missing: LVG model abundance profiles
- Data volume (inferred): ~10-50 GB
- Score (inferred): 3/5, Data identified but processing and fit details are sparse and deferred to another paper.
- Rediscovery candidate: no, Recipe incomplete; key numeric results are not tabulated.

## Links

- Method: Cernicharo et al. 2013 (cite: cer13) (Calibration, imaging and model modifications)
- Companion: Fonfría et al. 2014 (cite: fon14) (CARMA observations of the same molecules)

## Checks

```json
{
 "quotes": 48,
 "quotes_ok": 48,
 "quote_pass_rate": 1.0,
 "quotes_too_long": 0,
 "unsupported_facts": 0,
 "project_codes": 1,
 "codes_not_in_text": [],
 "codes_not_in_obscore": [],
 "obscore_codes_not_in_card": [],
 "codes_printed_but_missing": [],
 "numeric_results": 4,
 "numeric_problems": 0,
 "fill": {
  "facts": 66,
  "stated": 34,
  "rate": 0.515
 },
 "evidence_ok": true
}
```
