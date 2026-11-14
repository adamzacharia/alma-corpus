# First Detection of the Simplest Organic Acid in a Protoplanetary Disk

`2018ApJ...862L...2F` | The Astrophysical Journal Letters 2018 | first author: Favre, Cécile | arXiv: 1807.05768 | DOI: 10.3847/2041-8213/aad046

Card schema 1.0 | model claude-sonnet-5-5 | depth full | type observational_alma_primary

## Science

- Fields: protoplanetary_disks, astrochemistry
- Question: Is formic acid (HCOOH) present in the TW Hya protoplanetary disk, at what column density, and can disk chemical modeling reproduce it?  
  > "we report the first detection of formic acid (HCOOH) towards the TW Hydrae protoplanetary disk." (abstract)
- Target **TW Hya**: coordinates 11h01m51.875s, -34d42m17.155s (J2000, phase center)  
  > "The phase-tracking center was: $\alpha_{J2000}$ = 11$^{h}$01$^{m}$51.875s, $\delta_{J2000}$ =$-$34$\ensuremath{^\circ}$42$\ensuremath{'}$17$\ensuremath{''}$155." (2 Observations and data reduction); "distance of 59 pc, consistent with the recent GAIA measurements (cite: Gaia-Collaboration:2016)," (3.2 Data processing: keplerian mask); z/distance 59 pc  
  > "The phase-tracking center was: $\alpha_{J2000}$ = 11$^{h}$01$^{m}$51.875s, $\delta_{J2000}$ =$-$34$\ensuremath{^\circ}$42$\ensuremath{'}$17$\ensuremath{''}$155." (2 Observations and data reduction); "distance of 59 pc, consistent with the recent GAIA measurements (cite: Gaia-Collaboration:2016)," (3.2 Data processing: keplerian mask); distance from consistent with Gaia measurements (Gaia Collaboration 2016)  
  > "The phase-tracking center was: $\alpha_{J2000}$ = 11$^{h}$01$^{m}$51.875s, $\delta_{J2000}$ =$-$34$\ensuremath{^\circ}$42$\ensuremath{'}$17$\ensuremath{''}$155." (2 Observations and data reduction); "distance of 59 pc, consistent with the recent GAIA measurements (cite: Gaia-Collaboration:2016)," (3.2 Data processing: keplerian mask)

## Data provenance

- ALMA projects: 2015.1.00845.S
- bands: _not stated_
- frequencies and spectral setup: six spectral windows of 960 channels, 244.141 kHz width (~0.6 km/s), covering 129.538-132.405 GHz; one 2 GHz continuum window centred at 130.973 GHz (128 channels of 15.625 MHz)  
  > "six spectral windows each of 960 channels with a channel width used during the observations of 244.141 kHz (about 0.6 km s$^{-1}$) covering about 1.4 GHz between 129.538 GHz and 132.405 GHz" (2 Observations and data reduction)
- continuum bandwidth: _not stated_
- arrays: _not stated_
- configurations: _not stated_
- baselines: 15.1 m (6.5 kλ) to 713.1 m (310.0 kλ)  
  > "with 39 antennas and baselines from 15.1 m (6.5 k$\lambda$) up to 713.1 m (310.0 k$\lambda$)" (2 Observations and data reduction)
- angular resolution: 1.28" x 1.00" (continuum), 1.29" x 1.02" (line)  
  > "The resulting synthesized beam sizes are 1.28$\ensuremath{''}$ $\times$ 1.00$\ensuremath{''}$ at a P.A.$\sim$ $-$89$\ensuremath{^\circ}$" (2 Observations and data reduction)
- max recoverable scale: _not stated_
- sensitivity: _not stated_
- time on source: about 39 min  
  > "with an on source time of about 39 min with ALMA, during Cycle 3." (2 Observations and data reduction)
- observing dates: 2016 May 31 and 2016 June 1  
  > "The observations were performed toward TW Hya on 2016 May 31 and on 2016 June 1" (2 Observations and data reduction)
- pi or archival as stated: PI C. Favre, project 2015.1.00845.S  
  > "ADS/ JAO.ALMA$\#$2015.1.00845.S (PI C. Favre)." (footnote)
- Line: trans-HCOOH 6(1,6)-5(1,5) (129671.82 MHz)
- Line: c-C3H2 3-2 (145089.6 MHz)
- Other facility **IRAM-30m (ASAI)**: Previous detection of the same HCOOH line in L1157-B1 and NGC1333-IRAS4A, used to support the identification  
  > "the same line was clearly detected in the Solar-like regions L1157–B1 and NGC1333–IRAS4A with the IRAM-30m telescope" (3.1 t-HCOOH)
- External data: HCOOH spectroscopic parameters  
  > "We used the spectroscopic data parameters from (cite: Kuze:1982) that are available at the Cologne Database for Molecular Spectroscopy line catalog (cite: Muller:2005)." (2 Observations and data reduction) [from (cite: Kuze:1982); (cite: Muller:2005)]
- External data: Methanol observations in TW Hya used for the HCOOH/CH3OH ratio  
  > "As methanol was previously detected towards TW Hya (cite: Walsh:2016)" (3.3 Column densities and relative abundances) [from (cite: Walsh:2016)]
- External data: Cometary HCOOH/CH3OH ratio for comparison  
  > "about one order of magnitude higher than the ratio measured in comets (cite: Biver:2014)" (3.3 Column densities and relative abundances) [from (cite: Biver:2014)]
- Simulation/model as data: Thermochemical TW Hya disk structure (Gorti 2011) with ALCHEMIC chemistry run for 1 Myr and LIME line radiative transfer, synthetic ALMA observation via simobserve  
  > "These datacubes were then converted into visibilities using the simobserve task from the CASA package, using the same antenna positions as in the observations." (4.2 Radiative transfer modeling)

## Processing

### Calibration

- pipeline or manual: _not stated_
- casa version: CASA 4.5.3  
  > "Data reduction and continuum subtraction were performed through the version 4.5.3 of the Common Astronomy Software Applications, CASA." (2 Observations and data reduction)
- pipeline version: _not stated_
- archive products used as is: _not stated_
- flux calibrator: Ganymede (May) and Titan (June); J1037-2934 and J1103-3251 for bandpass and phase  
  > "Ganymede and Titan were used as flux calibrators for the observations performed in May and June, respectively." (2 Observations and data reduction)
- flux scale uncertainty: _not stated_
- self calibration: Continuum self-calibrated at 129 GHz, solutions applied to molecular data  
  > "The continuum emission at 129 GHz was self-calibrated with the solutions (gain tables) applied to the molecular data." (2 Observations and data reduction)

### Imaging

- task: _not stated_
- deconvolver: _not stated_
- weighting robust: Natural weighting  
  > "the data were cleaned using a $``$Natural" weighting." (2 Observations and data reduction)
- uv taper: _not stated_
- cell size: _not stated_
- image size: _not stated_
- masking: _not stated_
- multiscale scales: _not stated_
- continuum subtraction: performed in CASA (method not detailed)  
  > "Data reduction and continuum subtraction were performed through the version 4.5.3 of the Common Astronomy Software Applications, CASA." (2 Observations and data reduction)
- line free channels: _not stated_
- primary beam correction: _not stated_
- array combination: _not stated_
- smoothing: Gaussian kernel of 7" x 7" on the integrated map  
  > "smoothed by a Gaussian kernel of 7$\ensuremath{''}$ $\times$ 7$\ensuremath{''}$ to spatially enhance the signal to noise ratio." (3.2 Data processing: keplerian mask)
- final beam: 1.29" x 1.02", PA ~90 deg (line)  
  > "1.29$\ensuremath{''}$ $\times$ 1.02$\ensuremath{''}$ at a P.A. of about 90$\ensuremath{^\circ}$ for the continuum (see Fig. [1](#fg1)) and line images" (2 Observations and data reduction)
- final rms: _not stated_

### Inherited from earlier work

- Keplerian mask technique  
  > "one can significantly improve the signal- to-noise by the use of a Keplerian mask (cite: Salinas:2017a; Carney:2017)." (3.2 Data processing: keplerian mask) [from (cite: Salinas:2017a; Carney:2017)]
- Pixel spectral stacking method  
  > "the HCOOH spectrum resulting from the pixel spectral stacking method (cite: Yen:2016)" (3.1 t-HCOOH) [from (cite: Yen:2016)]
- Bootstrapped noise computation  
  > "to compute the "bootstrapped" noise, the same keplerian mask was applied to channels with no signal that were far away from the ones in which HCOOH is emitting (cite: Bergner:2018)." (3.2 Data processing: keplerian mask) [from (cite: Bergner:2018)]
- Modeling suite and LIME setup  
  > "with a setup similar to the one used by (cite: Parfenov:2017) to reproduce methanol emission towards TW Hya by (cite: Walsh:2016)." (4.2 Radiative transfer modeling) [from (cite: Parfenov:2017)]

### Not stated but needed to reproduce (our reading)

- Self-calibration solution intervals, number of iterations and reference channels
- Line-free channels used for continuum subtraction
- Clean threshold, image size, cell size and masks
- How the column density was computed from F (line width, partition function, source size)
- Aperture position and shape for the disk-averaged spectrum
- Methanol column density used for the HCOOH/CH3OH ratio
- Noise-estimation details for the 4 sigma and 12 sigma values
- LIME grid and model parameters

## Analysis recipe

1. **Calibrate, self-calibrate and image**: CASA reduction, continuum self-calibration with gain tables applied to line data, continuum subtraction, natural-weighted cleaning  
  > "The continuum emission at 129 GHz was self-calibrated with the solutions (gain tables) applied to the molecular data." (2 Observations and data reduction)
   - software: CASA 4.5.3
   - fitting: _not stated_
   - validation: _not stated_
2. **Extract disk-averaged spectrum and confirm detection**: Elliptical aperture of ~400 au on native data plus pixel spectral stacking  
  > "disk-averaged spectrum extracted from the native dataset using an elliptical aperture of about 400 au" (3.1 t-HCOOH)
   - fitting: _not stated_
   - validation: Two independent methods above 4 sigma; line is the brightest expected in range  
  > "two independent methods show a detection above the 4$\sigma$ level" (3.1 t-HCOOH)
3. **Apply Keplerian mask and make integrated map**: Keplerian mask, integrate v=0.9-3.4 km/s, smooth by 7"x7" Gaussian  
  > "integrated over the line profile, from v=0.9 to 3.4 km s$^{-1}$ and smoothed by a Gaussian kernel of 7$\ensuremath{''}$ $\times$ 7$\ensuremath{''}$" (3.2 Data processing: keplerian mask)
   - parameter: M*=0.7 Msun, i=7 deg, PA=155 deg, vsys=2.7 km/s, d=59 pc, Rout=400 au  
  > "outer radius of 400 au (to be consistent with the data)." (3.2 Data processing: keplerian mask)
   - assumption: Keplerian rotation  
  > "Assuming that the disk is in Keplerian rotation" (3.2 Data processing: keplerian mask)
   - fitting: _not stated_
   - validation: Mask checked on c-C3H2 (3-2) detected above 12 sigma; S/N improved by factor ~5  
  > "the signal to noise ratio was enhanced by a factor $\sim$5." (3.2 Data processing: keplerian mask)
4. **Derive column density and HCOOH/CH3OH ratio**: Convert disk-averaged integrated intensity to column density for Tex = 10 and 40 K; compare with methanol  
  > "corresponds to a t-HCOOH source averaged column density of (2.9$\pm$1.3)$\times$10$^{12}$ cm$^{-2}$ and (3.5$\pm$0.8)$\times$10$^{12}$ cm$^{-2}$ for an excitation temperature of 10 and 40 K, respectively." (3.3 Column densities and relative abundances)
   - assumption: Excitation temperature 10-40 K  
  > "The 10-40 K temperature range is the typical one where the molecular gas is expected to be emissive." (3.3 Column densities and relative abundances)
   - fitting: _not stated_
   - validation: _not stated_
5. **Model HCOOH chemistry and synthetic observation**: Gorti 2011 disk structure, ALCHEMIC chemistry for 1 Myr, LIME LTE radiative transfer, simobserve and clean to compare with observations  
  > "we used the three-dimensional Monte-Carlo code Line Modeling Engine (cite: Brinch:2010)" (4.2 Radiative transfer modeling)
   - software: ALCHEMIC, LIME, CASA
   - parameter: CR ionization 1.3e-17 s^-1; 1% chemical desorption; grain radius 7 micron; UV photodesorption yield 1e-5  
  > "A low UV-photodesorption yield of 10$^{-5}$ is adopted for all ices" (4.1 Physical and chemical model of TW Hya disk)
   - assumption: LTE, gas-to-dust ratio 100, star mass 0.7 Msun  
  > "An accretion rate of 10$^{-9}$ M$_{\odot}$ yr$^{-1}$ and a constant gas-to-dust mass ratio of 100 are assumed." (4.1 Physical and chemical model of TW Hya disk)
   - fitting: _not stated_
   - validation: Model reproduces observed column densities within a factor 3  
  > "Our physico-chemical modeling reproduces well the observed column densities within a factor 3" (4.3 Chemical desorption as the source of HCOOH in disks?)

## Software

- **CASA** 4.5.3: Data reduction, continuum subtraction, self-calibration, imaging, simobserve  
  > "version 4.5.3 of the Common Astronomy Software Applications, CASA" (2 Observations and data reduction)
- **LIME** : 3D non-LTE-capable Monte-Carlo line radiative transfer (run in LTE)  
  > "The radiative transfer calculations were performed assuming local thermodynamic equilibrium (LTE)." (4.2 Radiative transfer modeling)
- **ALCHEMIC** : Gas-grain disk chemical evolution  
  > "The chemical structure of the disk was computed with the public gas-grain ALCHEMIC code (cite: Semenov:2010)." (4.1 Physical and chemical model of TW Hya disk)

## Numeric results

| quantity | value | uncertainty | units | step | quote |
|---|---|---|---|---|---|
| t-HCOOH line integrated intensity | 89e-3 | 12e-3 | Jy km/s | 4 | F = (89$\pm$12)$\times$10$^{-3}$ Jy km s$^{-1}$ |
| t-HCOOH column density (Tex=10 K) | 2.9e12 | 1.3e12 | cm^-2 | 4 | (2.9$\pm$1.3)$\times$10$^{12}$ cm$^{-2}$ |
| t-HCOOH column density (Tex=40 K) | 3.5e12 | 0.8e12 | cm^-2 | 4 | (3.5$\pm$0.8)$\times$10$^{12}$ cm$^{-2}$ |
| Peak S/N of Keplerian-masked, smoothed map | 12 | not stated | sigma | 3 | with a detection at a peak to noise ratio of 12$\sigma$ |
| HCOOH/CH3OH ratio | <= 1 | not stated | dimensionless | 4 | we obtain an average abundance t-HCOOH/CH$_3$OH ratio lower than and/or equal to 1 |

## Qualitative findings

- HCOOH is the first organic molecule with two oxygen atoms detected in a protoplanetary disk.  
  > "HCOOH is the first organic molecules containing two oxygen atoms detected in a protoplanetary disk" (abstract)

## Claim tuples

- H: Is HCOOH detectable in the TW Hya disk? | E: ALMA band 3 spectrum extraction, pixel stacking and Keplerian-mask analysis | R: Line detected at S/N ~4 in the spectrum and 12 sigma after masking and smoothing | F: First detection of formic acid in a protoplanetary disk | **supported**
- H: Is HCOOH as abundant as methanol in the disk? | E: Compared column densities with literature methanol | R: Column density (2-4)e12 cm^-2, ratio <= 1 | F: Abundance comparable to methanol, though spatial scales differ | **partially**
- H: Can grain-surface formation with reactive desorption explain the HCOOH abundance? | E: Disk chemical model with LIME synthetic observation | R: Observed column densities reproduced within a factor 3 | F: Chemical desorption model is consistent with observations | **supported**

## Reasoning

- Why this data: _not stated_
- Why this method: _not stated_
- Alternative: Gas-phase ethanol-based scheme (Skouteris 2018) does not appear to dominate HCOOH production in a preliminary 0D model  
  > "this new set of reactions does not seem to dominate the production of formic acid in disks." (4.3 Chemical desorption as the source of HCOOH in disks?)
- How they decided it was enough: _not stated_
- Limitation (authors): Low spatial and spectral resolution prevents resolving the emission structure and kinematics; at least 100 au uncertainty in spatial extent  
  > "the low angular resolution observations along with the convolution procedure, lead to at least 100 au of uncertainty regarding the spatial extent of HCOOH." (3.2 Data processing: keplerian mask)
- Limitation (authors): Non-LTE not possible because HCOOH collisional rates are unavailable  
  > "Non-LTE calculations could not be performed as the collisional rate coefficients for HCOOH are not available." (4.2 Radiative transfer modeling)
- Caveat (inferred, ours): Single line at S/N ~4 in the unmasked spectrum; the identification rests on the mask and stacking
- Caveat (inferred, ours): Column density depends on an assumed emitting area and Tex
- Caveat (inferred, ours): Methanol ratio compares different spatial scales
- Caveat (inferred, ours): The Keplerian mask could bias the S/N

## Reproducibility

- Data public (paper): ALMA project 2015.1.00845.S is cited with PI, so it is in the archive  
  > "ADS/ JAO.ALMA$\#$2015.1.00845.S (PI C. Favre)." (footnote)
- Products in archive: _not stated_
- Missing: Self-calibration parameters
- Missing: Exact column density calculation
- Missing: Clean parameters and line-free channels
- Missing: LIME model setup details
- Data volume (inferred): ~20-50 GB raw
- Score (inferred): 3/5, Data are archival and the Keplerian mask parameters are given, but the imaging and self-calibration details and the column density derivation are missing.
- Rediscovery candidate: no, Recipe incomplete, with a marginal detection that is sensitive to unstated imaging details.

## Links

- Method: (cite: Salinas:2017a); (cite: Carney:2017) (Keplerian mask method)
- Method: (cite: Yen:2016) (Pixel spectral stacking)
- Method: (cite: Parfenov:2017) (Disk modeling suite)
- Companion: (cite: Walsh:2016) (Methanol detection in TW Hya)
- Companion: Favre et al. in prep (c-C3H2 detection in the same project)
- Related: ASAI (Astrochemical Surveys At IRAM)

## Checks

```json
{
 "quotes": 62,
 "quotes_ok": 62,
 "quote_pass_rate": 1.0,
 "quotes_too_long": 0,
 "unsupported_facts": 0,
 "project_codes": 1,
 "codes_not_in_text": [],
 "codes_not_in_obscore": [],
 "obscore_codes_not_in_card": [],
 "codes_printed_but_missing": [],
 "numeric_results": 5,
 "numeric_problems": 0,
 "fill": {
  "facts": 79,
  "stated": 47,
  "rate": 0.595
 },
 "evidence_ok": true
}
```
