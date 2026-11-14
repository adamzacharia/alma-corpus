# Exploring the molecular chemistry and excitation in obscured luminous infrared galaxies. An ALMA mm-wave spectral scan of NGC 4418

`2015A&A...582A..91C` | Astronomy and Astrophysics 2015 | first author: Costagliola, F. | arXiv: 1506.09027 | DOI: 10.1051/0004-6361/201526256

Card schema 1.0 | model claude-sonnet-5-5 | depth full | type observational_alma_primary

## Science

- Fields: nearby_galaxies, astrochemistry
- Question: What are the molecular abundances and excitation in the compact obscured nucleus of NGC 4418, and how do they compare with other Galactic and extragalactic environments?  
  > "To obtain for the first time a multi-band spectral scan of a LIRG, in order to derive the molecular abundances and excitation, to be compared to other Galactic and extragalactic environments." (abstract)
- Target **NGC 4418**: coordinates _not stated_; z/distance D = 34 Mpc  
  > "Lying at $D$=34 Mpc, the galaxy is part of an interacting pair" (1.1 NGC 4418 : The prototypical obscured LIRG); distance from _not stated_

## Data provenance

- ALMA projects: 2011.0.00820.S
- bands: Bands 3, 6, 7; 11 tunings; total 70.7 GHz (28.7 GHz B3, 28 GHz B6, 14 GHz B7)  
  > "The observed tunings cover 28.7 GHz in band 3, 28 GHz in band 6, and 14 GHz in band 7" (2 Observations)
- frequencies and spectral setup: four 1.875 GHz spectral windows per tuning, 3840 channels of 0.488 MHz, 250 MHz overlap  
  > "four different 1.875 GHz-wide spectral windows were set, each counting 3840 individual channels separated by 0.488 MHz" (2 Observations)
- continuum bandwidth: _not stated_
- arrays: _not stated_
- configurations: 19 to 25 antennas, baselines 20 to 480 m  
  > "The Cycle 0 array configuration was composed of 19 to 25 antennas, with baseline separations from 20 to 480 meters." (2 Observations)
- baselines: _not stated_
- angular resolution: ~2'', ~1'', ~0.8'' for bands 3, 6, 7  
  > "The resulting angular resolution is of $\sim$2$''$, $\sim$1$''$, and $\sim$0$''$.8 for bands 3, 6, and 7 respectively." (2 Observations)
- max recoverable scale: _not stated_
- sensitivity: rms 2 mJy (B3), 6 mJy (B6), 4 mJy (B7) at 20 km/s  
  > "The measured *rms* of the spectrum is 2 mJy in band 3, 6 mJy in band 6, and 4 mJy in band 7." (2.1 UV-fit of the spectrum)
- time on source: ~5 min per tuning  
  > "Each tuning consists in short integrations of $\sim$5 minutes on source" (2 Observations)
- observing dates: April 2012 to January 2013  
  > "between April 2012 and January 2013" (2 Observations)
- pi or archival as stated: _not stated_
- Other facility **IRAM 30m**: single-dish spectra for comparison with ALMA fluxes  
  > "we compare the extracted ALMA spectrum with IRAM 30 m single-dish observations with beam sizes of 27$''$ and 9$''$ at 3 and 1 mm, respectively." (2.1 UV-fit of the spectrum)
- Other facility **SMA**: HNC 3-2 and HC3N 30-29 fluxes and continuum for comparison  
  > "A comparison with the HNC 3-2 and HC$_3$N 30-29 flux densities detected with the SMA in the extended configuration (cite: costagliola2013) is reported" (2.1 UV-fit of the spectrum)
- External data: Source size upper limit 0.4'' for HCN/HNC 3-2 emission  
  > "We take as source size of the emission the upper limit of 0$''$.4 to the HCN and HNC J=3-2 emission observed by (cite: sakamoto2013) and (cite: costagliola2013)." (3.2.1 Population diagrams) [from (cite: sakamoto2013; costagliola2013)]
- External data: H2 column 0.7-2.9e24 cm-2 from CO 2-1  
  > "assuming a molecular hydrogen column of 0.7–2.9$\times$10$^{24}$ cm$^{-2}$, as derived by (cite: costagliola2013) from CO 2–1 observations." (4.5 Chemical composition of NGC 4418) [from (cite: costagliola2013)]
- External data: Literature abundances for Arp 220, M82, NGC 253, NGC 1068, Sgr B2, Orion Bar, TMC-1, PKS1830-211  
  > "Their abundances, together with the relevant references, are reported in Table [\[tab:abtab\]]" (4.5 Chemical composition of NGC 4418) [from (cite: martin2011; martin06; aladro_1068; muller_pks)]
- External data: Extragalactic 12C/13C ratio 40-100  
  > "If we assume an extragalactic $^{12}$C/$^{13}$C ratio between 40 and 100 (cite: henkel2014)" (4.4 Standard line ratios) [from (cite: henkel2014)]
- External data: Line parameters from Splatalogue, CDMS, JPL; collisional coefficients from LAMBDA  
  > "The transition parameters ($\nu$, $E_\mathrm{u}$, $A_\mathrm{u\ell}$, $g_\mathrm{u}$) were taken from the *Splatalogue*[^3] database" (3.2.1 Population diagrams) [from (cite: cdms; jpl; lambda)]

## Processing

### Calibration

- pipeline or manual: CASA, standard procedure  
  > "The data calibration was done within the CASA[^2] package following a standard procedure." (2 Observations)
- casa version: _not stated_
- pipeline version: _not stated_
- archive products used as is: _not stated_
- flux calibrator: Titan (3C 273 on 3 dates)  
  > "Titan for absolute flux calibration (except for 3 dates, for which we used 3C 273)" (2 Observations)
- flux scale uncertainty: ~10% band 3, ~20% bands 6 and 7  
  > "We expect an absolute flux accuracy of the order of $\sim$10% in band 3 and $\sim$20% in bands 6 and 7." (2 Observations)
- self calibration: _not stated_

### Imaging

- task: No imaging; spectrum extracted from visibilities with point-source fit (uvmultifit)  
  > "we chose not to image and clean the whole dataset, but to extract the spectrum from the visibilities." (2.1 UV-fit of the spectrum)
- deconvolver: _not stated_
- weighting robust: _not stated_
- uv taper: _not stated_
- cell size: _not stated_
- image size: _not stated_
- masking: _not stated_
- multiscale scales: _not stated_
- continuum subtraction: 3rd-order polynomial fit to line-free channels across the three bands  
  > "We obtain the best fit with a 3$^\mathrm{rd}$ order polynomial" (3.1 Removing the continuum)
- line free channels: _not stated_
- primary beam correction: _not stated_
- array combination: _not stated_
- smoothing: channels interpolated to 20 km/s common resolution  
  > "The extracted channels were then interpolated to a common resolution of 20 km s$^{-1}$across the whole frequency range" (2.1 UV-fit of the spectrum)
- final beam: _not stated_
- final rms: _not stated_

### Inherited from earlier work

- Combined LTE/NLTE fitting method of whole spectrum and LTE synthetic spectra  
  > "in a fashion similar to what was done for the ULIRG Arp 220 by (cite: martin2011)" (3.2.2 LTE/NLTE fit) [from (cite: martin2011)]
- Population diagram and opacity correction formalism  
  > "following (cite: popdiag), we can write the column density of the upper energy state" (3.2.1 Population diagrams) [from (cite: popdiag)]
- PCA procedure  
  > "an orthogonal set of principal components (PC) was derived following the procedure described in (cite: costagliola11)" (4.5.1 Principal component analysis) [from (cite: costagliola11)]
- Fiducial excitation temperature 80 K for synthetic spectra  
  > "an excitation temperature of 80 K (cite: costagliola2013)" (3.2.2 LTE/NLTE fit) [from (cite: costagliola2013)]

### Not stated but needed to reproduce (our reading)

- Phase/bandpass calibration details and CASA version
- Coordinates of the continuum peak used for the point-source fit
- Line-free channel ranges used for the continuum polynomial
- Exact line-list/species list and the fitting code (not released)
- Priors/grid steps of the RADEX grid and the molecule ordering
- Flux-scale handling for tunings with 3C 273 as flux calibrator

## Analysis recipe

1. **Extract spectrum from visibilities**: Fit point-source model with fixed position, free amplitude to visibilities of each spectral window; merge windows averaging 250 MHz overlaps  
  > "we fitted the interferometric spectral visibilities of each spectral window assuming a point-source model, with a fixed position but free amplitude." (2.1 UV-fit of the spectrum)
   - software: CASA, uvmultifit
   - parameter: 20 km/s common resolution  
  > "interpolated to a common resolution of 20 km s$^{-1}$across the whole frequency range" (2.1 UV-fit of the spectrum)
   - assumption: Emission unresolved (<0.4'' band 3, <0.2'' band 6)  
  > "We found the emission to be unresolved, with upper limits to the source size of 0$''$.4 and 0$''$.2 for band 3 and band 6, respectively." (2.1 UV-fit of the spectrum)
   - fitting: _not stated_
   - validation: Compared with IRAM 30m and SMA fluxes  
  > "The flux densities measured for the two datasets are within the errors" (2.1 UV-fit of the spectrum)
2. **Continuum estimate and removal**: Fit line-free channels with 3rd-order polynomial; power-law fits to band-averaged continuum  
  > "We choose instead to fit the line-free channels in the three bands with a polynomial." (3.1 Removing the continuum)
   - fitting: _not stated_
   - validation: Consistent with SMA continuum within 10% calibration uncertainty  
  > "Allowing for a calibration uncertainty of 10%, the two datasets are consistent." (3.1 Removing the continuum)
3. **Population diagram analysis**: Gaussian line fits, optically thin Nu with opacity correction, fit Tex and N for 12 species  
  > "we perform a population diagram analysis for the molecules which have at least two non-blended lines in different ALMA bands." (3.2.1 Population diagrams)
   - software: Splatalogue
   - assumption: Source size 0.4''; LTE  
  > "We take as source size of the emission the upper limit of 0$''$.4" (3.2.1 Population diagrams)
   - fitting: Fit of LTE Nu equation  
  > "By fitting Eq. [\[eq:lte\]](#eq:lte) to the derived N$_\mathrm{u}$ we can derive $T_\mathrm{ex}$ and $N$ for each molecule." (Population diagrams)
   - validation: _not stated_
4. **LTE/NLTE fit of whole spectrum**: Iterative chi2 fit of molecules ordered by brightness, subtracting each best fit; RADEX grid of 100,000 models for NLTE  
  > "a grid of 100,000 synthetic spectra was produced with the RADEX radiative transfer code (cite: radex)" (3.2.2 LTE/NLTE fit)
   - software: RADEX, LAMBDA
   - parameter: n(H2) 1e3-1e7 cm-3, Tkin 5-300 K, N 1e15-1e18 cm-2; line width 120 km/s; vLSR 2100 km/s; 0.4'' source  
  > "molecular hydrogen densities ranging from 10$^{3}$ to 10$^7$cm$^{-3}$, kinetic temperatures between 5 and 300 K, and molecular column densities between 10$^{15}$ and 10$^{18}$ cm$^{-2}$" (3.2.2 LTE/NLTE fit)
   - assumption: All species share same beam filling factor  
  > "Our fit also assumes that all the molecular species have the same beam filling factor" (3.4 Limitations)
   - fitting: chi2 minimization, one-sigma statistical errors  
  > "represent one-sigma statistical uncertainties derived from the $\chi^2$ minimization" (3.4 Limitations)
   - validation: Normalized chi2 = 5; 92% of molecular flux recovered  
  > "The flux recovered by the fit is 92 % of the total molecular emission, resulting in a normalized $\chi^2$ of 5 for the whole spectrum." (3.3 Results from the line identification and fit)
5. **Compare abundances via PCA**: PCA on abundances and Tkin of nine species for 10 sources, 1000 virtual samples per source with uniform N,T within confidence intervals  
  > "producing 1000 virtual samples for each source, with N and T values uniformly distributed inside their confidence intervals." (4.5.1 Principal component analysis)
   - assumption: N(H2) = 0.7-2.9e24 cm-2 for NGC 4418  
  > "assuming a molecular hydrogen column of 0.7–2.9$\times$10$^{24}$ cm$^{-2}$" (4.5 Chemical composition of NGC 4418)
   - fitting: _not stated_
   - validation: _not stated_

## Software

- **CASA** : data calibration  
  > "The data calibration was done within the CASA[^2] package following a standard procedure." (2 Observations)
- **uvmultifit** : point-source fit of visibilities to extract spectrum  
  > "This last step was performed using the CASA `uvmultifit` routine (cite: uvmultifit)." (2.1 UV-fit of the spectrum)
- **RADEX** : NLTE synthetic spectra grid  
  > "produced with the RADEX radiative transfer code (cite: radex)" (3.2.2 LTE/NLTE fit)

## Numeric results

| quantity | value | uncertainty | units | step | quote |
|---|---|---|---|---|---|
| Number of emission lines detected | 317 | not stated | lines | 4 | We identify 317 emission lines above the three sigma level from a total of 45 molecular species |
| Continuum flux at 98, 244, 284 GHz | 9, 56, 85 | 1, 6, 9 | mJy | 2 | The derived values are 9$\pm$1 mJy, 56$\pm$6 mJy, and 85$\pm$9 mJy at 98, 244, and 284 GHz, respectively. |
| Molecular emission fraction of total flux | 15% band 3; 27% bands 6 and 7 | not stated | percent | 2 | We find that the molecular emission contributes for 15% of the total flux in band 3, and for 27% in bands 6 and 7. |
| HC3N vibrational temperature | 330-400 | not stated | K | 4 | results in a vibrational temperature of 330-400 K |
| HC3N excitation temperature (population diagram) | 65 | 4 | K | 3 | / HC$_3$N / J=10-9 / 90.98 / 4.0$\pm$0.8 / 110$\pm$20 / 34$\pm$7 / 65$\pm$4 / 1$\pm$0.1$\times$10$^{17}$ / 0.5 / |
| HCO+/HCN abundance ratio | 0.35 | 0.2 | dimensionless | 4 | The derived HCO$^+$/HCN abundance ratio in NGC 4418 is thus 0.35$\pm$0.2. |
| HC5N abundance | 0.5-2e-8 | not stated | relative to H2 | 4 | this corresponds to an abundance of 0.5-2$\times$10$^{-8}$. |
| Variance in first three PCs | 80 | not stated | percent | 5 | The first three PCs contain 80% of the variance in the sample |

## Qualitative findings

- First extragalactic detection of HC3N (v7=1,v6=1) emission; spectrum dominated by vibrationally excited HC3N, HCN, HNC.  
  > "The detection of emission from the (v7=1,v6=1) state of HC$_3$N is the first obtained in an extragalactic object." (4.1 A vibrationally excited spectrum)

## Claim tuples

- H: Does NGC 4418 contain a compact hot IR source? | E: Vibrationally excited HC3N, HCN, HNC population analysis | R: Vibrational temperatures 330-450 K | F: Compact (<5 pc) optically thick IR source with Tb >350 K | **supported**
- H: Is NGC 4418's chemistry similar to Arp 220 and distinct from other environments? | E: PCA of nine molecular abundances plus Tkin across 10 sources | R: NGC 4418 and Arp 220 separated from others by PC3 | F: A common peculiar chemistry typical of CONs | **supported**
- H: Does molecular line emission contaminate the continuum? | E: Subtract fitted continuum and compare | R: 15% in band 3, 27% in bands 6 and 7 | F: Line contamination is serious for continuum studies in (U)LIRGs | **supported**

## Reasoning

- Why this data: _not stated_
- Why this method: Source unresolved so spectrum extracted from visibilities instead of imaging  
  > "Given the point-like nature of the emission, we chose not to image and clean the whole dataset" (2.1 UV-fit of the spectrum)
- Alternative: Best power-law continuum fit overestimates 1 mm emission by >20%, so polynomial used instead  
  > "The best power-law fit to the ALMA continuum points overestimates the emission at 1 mm by more than 20%" (3.1 Removing the continuum)
- How they decided it was enough: _not stated_
- Limitation (authors): Unresolved emission: source size and common beam filling factor are the main uncertainties; line blending ~20%  
  > "Because the emission is unresolved in the ALMA beam, the main uncertainty in our LTE/NLTE fit is the source size." (3.4 Limitations)
- Caveat (inferred, ours): Single-beam, unresolved data; single assumed 0.4'' size and common filling factor for all species
- Caveat (inferred, ours): Fixed 120 km/s line width and heavy blending make fits degenerate for many species
- Caveat (inferred, ours): Comparison abundances from heterogeneous literature sources with different methods
- Caveat (inferred, ours): Only 11 of 38 proposed tunings, so coverage is incomplete

## Reproducibility

- Data public (paper): Project code 2011.0.00820.S given in acknowledgements  
  > "This paper makes use of the following ALMA data: ADS/JAO.ALMA#2011.0.00820.S ." (Acknowledgements)
- Products in archive: _not stated_
- Missing: Fitting code and molecule list ordering
- Missing: CASA version and calibration details
- Missing: Continuum peak position and line-free channels
- Data volume (inferred): ~10-50 GB (11 Cycle 0 tunings, short integrations)
- Score (inferred): 5/5, Public Cycle 0 data and a clear multi-step recipe, but the custom fitting code and several settings are unstated.
- Rediscovery candidate: no, Custom LTE/NLTE fitting code and many unstated choices make exact numeric reproduction hard.

## Links

- Method: (cite: martin2011) (LTE/NLTE spectral fitting method followed)
- Method: (cite: uvmultifit) (visibility fitting tool)
- Method: (cite: popdiag) (population diagram formalism)
- Companion: (cite: costagliola2013) (previous SMA/MERLIN study of NGC 4418)
- Companion: (cite: sakamoto2013) (previous SMA study of NGC 4418)

## Checks

```json
{
 "quotes": 63,
 "quotes_ok": 63,
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
  "facts": 81,
  "stated": 50,
  "rate": 0.617
 },
 "evidence_ok": true
}
```
