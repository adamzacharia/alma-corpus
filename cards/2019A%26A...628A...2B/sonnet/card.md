# Molecular complexity on disc scales uncovered by ALMA. Chemical composition of the high-mass protostar AFGL 4176

`2019A&A...628A...2B` | Astronomy and Astrophysics 2019 | first author: Bøgelund, Eva G. | arXiv: 1906.06156 | DOI: 10.1051/0004-6361/201834527

Card schema 1.0 | model claude-sonnet-5-5 | depth full | type archival_reuse

## Science

- Fields: star_formation, astrochemistry
- Question: What is the chemical inventory (species, excitation temperatures, column densities, spatial distribution) of the high-mass protostar AFGL 4176 on disk scales, and how does it compare with other sources and hot-core models?  
  > "Using the Atacama Large Millimeter/submillimeter Array (ALMA) the chemical inventory of AFGL 4176 is characterised." (abstract)
- Target **AFGL 4176**: coordinates 13h43m01.704s, -62d08m51.23s (ICRS J2000)  
  > "AFGL 4176, located in the southern hemisphere at 13$^{\rm{h}}$43$^{\rm{m}}$01.704$^{\rm{s}}$, $-62^{\circ}$08$'$51.23$''$ (ICRS J2000)" (1.1 AFGL 4176); "in this work we will assume a distance of 3.7 kpc, based on the recent second release of *Gaia* data" (1.1 AFGL 4176); z/distance 3.7 kpc (+2.6/-1.6)  
  > "AFGL 4176, located in the southern hemisphere at 13$^{\rm{h}}$43$^{\rm{m}}$01.704$^{\rm{s}}$, $-62^{\circ}$08$'$51.23$''$ (ICRS J2000)" (1.1 AFGL 4176); "in this work we will assume a distance of 3.7 kpc, based on the recent second release of *Gaia* data" (1.1 AFGL 4176); distance from Gaia DR2 (Bailer-Jones2018)  
  > "AFGL 4176, located in the southern hemisphere at 13$^{\rm{h}}$43$^{\rm{m}}$01.704$^{\rm{s}}$, $-62^{\circ}$08$'$51.23$''$ (ICRS J2000)" (1.1 AFGL 4176); "in this work we will assume a distance of 3.7 kpc, based on the recent second release of *Gaia* data" (1.1 AFGL 4176)

## Data provenance

- ALMA projects: 2012.1.00469.S
- bands: Band 6, 211-275 GHz  
  > "using the Band 6 receivers, covering the frequency range of 211 – 275 GHz" (2.1 Observations)
- frequencies and spectral setup: Four spectral windows: two 1875 MHz wide (240.5, 254.0 GHz), two 468.75 MHz (239.0, 256.3 GHz); 976.6 kHz and 244 kHz resolution  
  > "These consist of two wide windows, of 1875 MHz, centred at 240.5 and 254.0 GHz and two narrow windows, of 468.75 MHz, centred at 239.0 and 256.3 GHz." (2.1 Observations)
- continuum bandwidth: _not stated_
- arrays: 39 antennas, Cycle 1  
  > "carried out with ALMA during Cycle 1 (cite: Johnston2015) with 39 antennas in the array" (2.1 Observations)
- configurations: _not stated_
- baselines: _not stated_
- angular resolution: ~0.35 arcsec (~1285 au)  
  > "The angular resolution is $\sim$0.35$\ensuremath{''}$, equivalent to $\sim$1285 au at the distance of AFGL 4176." (2.1 Observations)
- max recoverable scale: _not stated_
- sensitivity: continuum rms ~0.5 mJy/beam; 1.5-2.2 mJy/beam per 1.2 km/s channel  
  > "with an rms noise of approximately 0.5 mJy beam$^{-1}$ (0.1 K at 247 GHz)" (2.1 Observations)
- time on source: _not stated_
- observing dates: August 16-17, 2014  
  > "between August 16, 2014 and August 17, 2014" (2.1 Observations)
- pi or archival as stated: _not stated_
- External data: 12C/13C = 60 from galactocentric relation at d_GC = 6.64 kpc  
  > "adopting a $^{12}$C/$^{13}$C values of 60, derived assuming a galactocentric distance ($d_{\textrm{GC}}$) of 6.64 kpc and the relation for $^{12}$C/$^{13}$C reported by (cite: Milam2005)" (2.2 Methods) [from (cite: Milam2005)]
- External data: Dust opacity kappa = 1.0 cm2/g  
  > "$\kappa_{\rm \nu}$ = 1.0 cm$^{2}$ g$^{-1}$ (cite: Ossenkopf1994)" (2.2 Methods) [from (cite: Ossenkopf1994)]
- External data: Spectroscopic line catalogues JPL and CDMS  
  > "catalogued transition frequencies from the JPL (cite: Pickett1998) and CDMS (cite: Muller2001; Muller2005; Endres2016) molecular databases are compared with the extracted spectra" (2.2 Methods) [from (cite: Pickett1998), (cite: Muller2001)]
- External data: Comparison abundances for Sgr B2, Orion KL, IRAS 16293B and Garrod 2013 models  
  > "These studies focus on Sgr B2(N), Orion KL and the low-mass protostellar binary IRAS 16293. We conclude the section with a comparison to chemical models." (Discussion) [from (cite: Belloche2016; Bonfand2017; Tercero2018; Jorgensen2016; Garrod2013)]
- Simulation/model as data: Garrod (2013) hot core chemical models (fast, medium, slow warm-up) used for abundance comparison  
  > "Three warm-up timescales are adopted: a ’fast’ scale with warm-up to 200 K in 5$\times$10$^4$ yr" (4.3 Comparison with chemical models)

## Processing

### Calibration

- pipeline or manual: Delivered archive pipeline script  
  > "reduced via the delivered pipeline script using the Common Astronomy Software Applications (CASA) version 4.2.1" (2.1 Observations)
- casa version: CASA 4.2.1 (calibration)  
  > "Common Astronomy Software Applications (CASA) version 4.2.1" (2.1 Observations)
- pipeline version: _not stated_
- archive products used as is: _not stated_
- flux calibrator: Titan (Aug 16), Ceres (Aug 17)  
  > "Bandpass and absolute flux calibration was carried out, respectively, using J1617-5848 and Titan, on August 16 and J1427-4206 and Ceres on August 17." (2.1 Observations)
- flux scale uncertainty: 20%  
  > "A conservative flux calibration accuracy of 20% has been adopted." (2.1 Observations)
- self calibration: _not stated_

### Imaging

- task: CASA 5.1.1-5; continuum and line imaged separately  
  > "The continuum and line data were imaged separately in CASA version 5.1.1-5" (2.1 Observations)
- deconvolver: _not stated_
- weighting robust: Briggs, robust = 1.5  
  > "Briggs weighting with a robust parameter of 1.5" (2.1 Observations)
- uv taper: _not stated_
- cell size: 0.04 arcsec  
  > "using a pixel size of 0.04$\ensuremath{''}$" (2.1 Observations)
- image size: _not stated_
- masking: _not stated_
- multiscale scales: _not stated_
- continuum subtraction: Using most line-free channels  
  > "The data were continuum subtracted using the most line-free channels and corrected for primary beam attenuation." (2.1 Observations)
- line free channels: _not stated_
- primary beam correction: Applied  
  > "The data were continuum subtracted using the most line-free channels and corrected for primary beam attenuation." (2.1 Observations)
- array combination: _not stated_
- smoothing: _not stated_
- final beam: 0.33x0.31 arcsec continuum; 0.32-0.35 x 0.28-0.30 arcsec in cubes  
  > "in a beam of 0$\overset{\second}{.}$33$\times$0$\overset{\second}{.}$31" (2.1 Observations)
- final rms: 0.5 mJy/beam continuum; 1.5-2.2 mJy/beam per channel  
  > "The peak continuum emission is 29 mJy beam$^{-1}$ (5.7 K at 247 GHz) with an rms noise of approximately 0.5 mJy beam$^{-1}$ (0.1 K at 247 GHz)" (Observations)

### Inherited from earlier work

- Same ALMA dataset as Johnston et al. 2015; continuum peak label mm1/mm2  
  > "The work is based on the same set of high sensitivity, high resolution ALMA observations as analysed by (cite: Johnston2015)" (1.1 AFGL 4176) [from (cite: Johnston2015)]

### Not stated but needed to reproduce (our reading)

- Line-free channels used for continuum subtraction
- Line-free channels/spectral ranges for the continuum image
- Exact spectrum extraction aperture and line selection for moment maps
- CASSIS version and exact chi2 definition
- Image size and masking/deconvolution settings
- Which lines were used for each species fit

## Analysis recipe

1. **Reduce and image data**: Archive pipeline calibration, continuum subtraction, primary-beam correction, separate continuum and line imaging  
  > "The continuum and line data were imaged separately in CASA version 5.1.1-5" (2.1 Observations)
   - software: CASA
   - parameter: Briggs robust 1.5, 0.04'' pixels, 1.2 km/s channels  
  > "a velocity resolution for the spectral cubes of 1.2 km s$^{-1}$ and Briggs weighting with a robust parameter of 1.5" (2.1 Observations)
   - fitting: _not stated_
   - validation: _not stated_
2. **Extract spectrum and identify lines**: Spectrum averaged over a beam at the continuum peak; compare with JPL/CDMS; detection if S/N>=3; <5 lines tentative  
  > "Observed lines are considered detected if the peak signal-to-noise ratio is three or higher. Species with fewer than five detected lines are considered tentative detections." (2.2 Methods)
   - software: CASSIS
   - fitting: _not stated_
   - validation: Three checks against mis-assignment (no predicted lines without emission, no alternative species, rare isotopologues do not predict missing main lines)  
  > "To ensure that no lines are incorrectly assigned, three checks are conducted." (2.2 Methods)
3. **Fit Tex and column density**: LTE optically thin synthetic spectra over a grid of Tex and Ns; minimum chi2 best fit; fixed Tex for species with few lines  
  > "This is done by creating grids of models varying $T_{\textrm{ex}}$ and $N_{\textrm{s}}$ and identifying the model with the minimal $\chi^2$ as the best fit." (2.2 Methods)
   - software: CASSIS
   - parameter: vLSR = -53.5 km/s, FWHM = 6 km/s fixed; source size = beam; Tex 50-500 K step 10 K  
  > "a source velocity of $-$53.5 km s$^{-1}$ and FWHM line widths of 6 km s$^{-1}$ are found" (2.2 Methods)
   - assumption: LTE, optically thin; fixed Tex = 200 K (average) for poorly constrained species; 12C/13C = 60  
  > "For all other species, the excitation temperature is assumed to be 200 K." (2.2 Methods)
   - fitting: Grid chi2 minimisation; uncertainty = std dev of models within 95% confidence  
  > "The uncertainty on $T_{\textrm{ex}}$ and $N_{\textrm{s}}$ is listed as the standard deviation of models within the 95$\%$ confidence level." (2.2 Methods)
   - validation: Fixed-Tex sensitivity at 130 and 270 K  
  > "column densities are also derived assuming excitation temperatures of 130 K and 270 K" (2.2 Methods)
4. **Derive H2 column density and abundances**: N(H2) from dust continuum with Planck function at 200 K; ratios to CH3OH from 13CH3OH x 60  
  > "The resulting H$_{2}$ column density is found to be $N_{\rm H_{2}}$ = 4$\times$10$^{23}$ cm$^{-2}$." (2.2 Methods)
   - parameter: I = 29 mJy/beam, kappa = 1.0 cm2/g, mu = 2.33  
  > "For our data, $I_{\rm \nu}$ = 29 mJy beam$^{-1}$ and $\kappa_{\rm \nu}$ = 1.0 cm$^{2}$ g$^{-1}$" (2.2 Methods)
   - assumption: Gas-to-dust 100, T = 200 K, optically thin dust  
  > "the factor 100 accounts for the gas-to-dust ratio" (2.2 Methods)
   - fitting: _not stated_
   - validation: Brightness temperature 5.7 K << 200 K so dust opacity negligible  
  > "We therefore conclude that, averaged over the beam, continuum opacity is negligible." (3 Results)
5. **Map spatial distribution**: Zero and first-moment maps of isolated lines (>=3 km/s from neighbours) at low and high Eup; 2D Gaussian fits to moment-0  
  > "The spatial extent of each species is determined by fitting a 2D Gaussian to the zero-moment maps" (3.4 Spatial distribution of selected species)
   - software: CASA
   - fitting: 2D Gaussian  
  > "The spatial extent of each species is determined by fitting a 2D Gaussian to the zero-moment maps" (Spatial distribution of selected species)
   - validation: _not stated_
6. **Compare with other sources and models**: Compare ratios to CH3OH with Sgr B2, Orion KL, IRAS 16293B and Garrod 2013 models  
  > "we compare our ALMA results for AFGL 4176 with a selection of ALMA studies" (4 Discussion)
   - fitting: _not stated_
   - validation: _not stated_

## Software

- **CASA** 4.2.1 (calibration); 5.1.1-5 (imaging): Calibration and imaging  
  > "The continuum and line data were imaged separately in CASA version 5.1.1-5" (2.1 Observations)
- **CASSIS** : LTE synthetic spectra and chi2 grid fitting  
  > "Using the CASSIS[^1] line analysis software and assuming local thermodynamic equilibrium (LTE) and optically thin lines, a synthetic spectrum is produced for each identified species." (2.2 Methods)

## Numeric results

| quantity | value | uncertainty | units | step | quote |
|---|---|---|---|---|---|
| Continuum peak flux | 29 | rms 0.5 | mJy/beam | 1 | The peak continuum emission is 29 mJy beam$^{-1}$ (5.7 K at 247 GHz) |
| N(H2) | 4e23 | not stated | cm-2 | 4 | $N_{\rm H_{2}}$ = 4$\times$10$^{23}$ cm$^{-2}$ |
| CH3OH column density (from 13CH3OH) | 5.5e18 | 0.4e18 | cm-2 | 3 | CH$_3$OH / \[120\] / \[(5.5 $\pm$ 0.4)$\times$10$^{18}$\] |
| 13CH3OH Tex | 120 | 15 | K | 3 | $^{13}$CH$_3$OH / 120 $\pm$ 15 / (9.2 $\pm$ 0.6)$\times$10$^{16}$ |
| CH3CN Tex | 270 | 40 | K | 3 | CH$_3$CN / 270 $\pm$ 40 / (3.4 $\pm$ 0.3)$\times$10$^{16}$ |
| SO2/CH3OH | 14.7 | 3.6 | % | 3 | SO$_2$ / 150 $\pm$ 30 / (8.1 $\pm$ 1.9)$\times$10$^{17}$ / 14.7 $\pm$ 3.6 |
| Number of species detected | 23 (354 lines, 324 assigned, 30 unidentified) | not stated | dimensionless | 2 | A total of 354 lines are identified towards AFGL 4176 with a signal-to-noise ratio of three or above. |
| Glycolaldehyde upper limit | <=1.1e16 (<=0.2% of CH3OH) | not stated | cm-2 | 3 | The column density upper limit is $\leq$1.1$\times$10$^{16}$ cm$^{-2}$, equivalent to $\leq$0.2% with respect to methanol. |
| O-bearing/N-bearing ratio relative to CH3OH | 3 | not stated | dimensionless | 3 | On average, the column density ratios derived for O-bearing species are a factor of three higher than those derived for N-bearing species. |
| 12C/13C and 14N/15N from HC3N | ~16 and ~34 | not stated | dimensionless | 3 | These are found to be $\sim$16 and $\sim$34, respectively. |

## Qualitative findings

- CH3C2H is the only species with two emission peaks, one at mm2  
  > "Instead this species shows two peaks, of approximately similar intensity" (3.4)

## Claim tuples

- H: Does the O/N-bearing ratio indicate the evolutionary stage of AFGL 4176? | E: LTE fits of 23 species and ratios to CH3OH | R: O-bearing ratios are a factor of three higher than N-bearing | F: AFGL 4176 may be a relatively young source | **partially**
- H: Is AFGL 4176 more similar chemically to low-mass IRAS 16293B or to Galactic centre hot cores? | E: Compare ratios to CH3OH | R: Many O-bearing species within a factor of two of IRAS 16293B; Sgr B2 higher by up to an order of magnitude or more | F: Composition resembles IRAS 16293B, suggesting complex chemistry set in the cold cloud stage | **supported**
- H: Do the Garrod 2013 models reproduce the observed abundances? | E: Compare ratios with fast/medium/slow models | R: Matches CH3CHO, C2H5OH, CH3OCH3; underpredicts CH3COCH3 and (CH2OH)2; N-bearing off by ~10x except C2H3CN | F: Models only partly reproduce observations | **partially**

## Reasoning

- Why this data: _not stated_
- Why this method: Optically thin 13C methanol used since main CH3OH lines are optically thick  
  > "because this species is very abundant, many of its lines are optically thick and therefore its column density cannot be derived directly" (2.2 Methods)
- How they decided it was enough: _not stated_
- Limitation (authors): Distance poorly constrained (3.5-5.3 kpc)  
  > "the distance to AFGL 4176 is not well-constrained and cited values range from 3.5 to 5.3 kpc" (1.1 AFGL 4176)
- Limitation (authors): Vibrationally excited column densities not trusted (non-LTE)  
  > "The column densities derived from these transitions can therefore not be trusted." (3 Results)
- Caveat (inferred, ours): Single-position, single-Tex LTE modelling with fixed linewidth ignores gradients and multiple components
- Caveat (inferred, ours): Beam-averaged N and size=beam assumption
- Caveat (inferred, ours): Distance uncertainty affects luminosity-based comparisons
- Caveat (inferred, ours): Chi2 fitting without full sampling

## Reproducibility

- Data public (paper): Data downloaded from ALMA archive  
  > "The data were downloaded from the ALMA archive and reduced via the delivered pipeline script" (2.1 Observations)
- Products in archive: _not stated_
- Missing: CASSIS version and input line lists per species
- Missing: Line-free channel selection
- Missing: Which lines were used per species
- Data volume (inferred): ~20-50 GB (4 spectral windows, Cycle 1, 2 execution blocks)
- Score (inferred): 4/5, Public archive data and a clear LTE grid-fit recipe with tabulated results; some imaging and line-selection details missing.
- Rediscovery candidate: yes, Public data, a clear recipe, and numeric Tex and column density tables.

## Links

- Method: (cite: Jorgensen2016) (PILS comparison survey)
- Companion: (cite: Johnston2015) (Same ALMA data, disk kinematics)
- Related: ALMA-PILS
- Related: EMoCA

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
 "numeric_results": 10,
 "numeric_problems": 0,
 "fill": {
  "facts": 77,
  "stated": 50,
  "rate": 0.649
 },
 "evidence_ok": true
}
```
