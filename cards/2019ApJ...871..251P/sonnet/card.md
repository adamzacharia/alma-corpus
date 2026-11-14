# ALMA Observations of Ethyl Formate toward Orion KL

`2019ApJ...871..251P` | The Astrophysical Journal 2019 | first author: Peng, Yaping | arXiv: 1812.03700 | DOI: 10.3847/1538-4357/aafad4

Card schema 1.0 | model claude-sonnet-5-5 | depth full | type archival_reuse

## Science

- Fields: astrochemistry, star_formation
- Question: Is ethyl formate present toward Orion KL, where is it located, and does its abundance and distribution relative to methyl formate, ethanol and formic acid favour gas-phase or grain-surface formation?  
  > "We wish to explore more organic molecules with increasing complexity in this region. In particular, we have searched for one of the most complex organic molecules detected in space so far, ethyl formate" (abstract)
- Target **Orion KL (hot core-SW and compact ridge)**: coordinates phase center RA 05h35m14.35s, Dec -05d22m35.00s (J2000)  
  > "The phase center of the observations is R.A.(J2000)=$05^\mathrm{h}35^\mathrm{m}14^\mathrm{s}.35$ and Decl.(J2000)=$-05^{\circ}22^{'}35^{\prime\prime}.00$." (2 Observations); z/distance _not stated_; distance from _not stated_

## Data provenance

- ALMA projects: 2011.0.00009.SV
- bands: Band 6 (214-247 GHz)  
  > "observed with ALMA at band 6 (214–247 GHz)" (Summary)
- frequencies and spectral setup: 20 spectral windows of 1.875 GHz, 3840 channels each, 0.448 MHz (~0.7 km/s) resolution, covering 214-247 GHz  
  > "A total of 20 spectral windows of 1.875 GHz completely cover a frequency range from 214 GHz to 247 GHz. Each spectral window consists of 3840 channels with a uniform spectral resolution of 0.448 MHz" (2 Observations)
- continuum bandwidth: _not stated_
- arrays: 16 antennas of 12 m  
  > "The observations were carried with 16 antennas of 12 m in January 2012." (2 Observations)
- configurations: _not stated_
- baselines: 17 to 265 m  
  > "The baseline lengths range from 17 to 265 m." (2 Observations)
- angular resolution: ~1.8" x 1.3" (natural weighting), PA -2.6 deg  
  > "The synthesized beam size with natural weighting for spectral images is approximately $1.^{\prime\prime}8\times1.^{\prime\prime}3$" (2 Observations)
- max recoverable scale: _not stated_
- sensitivity: _not stated_
- time on source: _not stated_
- observing dates: January 2012  
  > "The observations were carried with 16 antennas of 12 m in January 2012." (2 Observations)
- pi or archival as stated: ALMA science verification data, public  
  > "We used data from the ALMA science verification (SV) program" (2 Observations)
- Line: C2H5OCHO (trans and gauche) 82 unblended lines, Eu 152-411 K (214-247 GHz)
- External data: Continuum peak intensities 1.34±0.06 Jy/beam (hot core) and 0.28±0.03 Jy/beam (compact ridge) used for N(H2)  
  > "We adopt S$_{\nu}$ of 1.34 $\pm$ 0.06 Jy beam$^{-1}$ for the hot core and 0.28 $\pm$ 0.03 Jy beam$^{-1}$ for the compact ridge from (cite: Wu14) that used same ALMA data." (3.2 Molecular abundances) [from (cite: Wu14)]
- External data: Peak positions of continuum hot core and compact ridge  
  > "The coordinates of two peak positions are from (cite: Peng17) that used the same dataset." (3.2 Spatial Distributions) [from (cite: Peng17)]
- External data: Grain emissivity 2e-5 at 230 GHz  
  > "grain emissivity of 2 $\times$ 10$^{-5}$ at 230 GHz (cite: Lis91)" (3.2 Molecular abundances) [from (cite: Lis91)]
- Simulation/model as data: Grain-surface model predictions (Garrod08) and gas-phase model predictions (Taquet16, Charnley95) compared with observed abundances  
  > "with the theoretical values from the grain-surface model by (cite: Garrod08) and gas-phase model by (cite: Taquet16)" (3.2 Molecular abundances)

## Processing

### Calibration

- pipeline or manual: _not stated_
- casa version: _not stated_
- pipeline version: _not stated_
- archive products used as is: _not stated_
- flux calibrator: Callisto (flux), quasar J0607-085 (phase)  
  > "Callisto and the quasar J0607-085 were used for the flux and phase calibration, respectively." (2 Observations)
- flux scale uncertainty: _not stated_
- self calibration: _not stated_

### Imaging

- task: Miriad (calibrated uv data exported to Miriad format)  
  > "The calibrated UV data were exported to Miriad format, and images were using the Miriad software package" (2 Observations)
- deconvolver: _not stated_
- weighting robust: natural weighting  
  > "The synthesized beam size with natural weighting for spectral images is approximately $1.^{\prime\prime}8\times1.^{\prime\prime}3$" (2 Observations)
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
- final beam: _not stated_
- final rms: 1σ channel rms per transition listed in Table A.1 (~0.04-0.09 K for EF)  
  > "The last column of Table A.1 lists the 1$\sigma$ channel rms noise level of each transition." (3.1 Line Identification)

### Inherited from earlier work

- Calibrated data and continuum peak intensities from earlier analysis of same ALMA SV data  
  > "from (cite: Wu14) that used same ALMA data" (3.2 Molecular abundances) [from (cite: Wu14)]
- Line identification criteria  
  > "To identify lines, we set the following constraints (cite: Snyder05; Brouillet15)" (3.1 Line Identification) [from (cite: Snyder05; Brouillet15)]
- N(H2) formula from dust continuum  
  > "the column density of H$_{2}$ can be derived by the formula (e.g., (cite: Lis91; Qin10))" (3.2 Molecular abundances) [from (cite: Lis91; Qin10)]

### Not stated but needed to reproduce (our reading)

- Calibration steps, CASA version, and whether flux scale or self-calibration were applied
- Continuum subtraction method and line-free channels
- Cell size, image size, deconvolution/clean parameters and masking
- Initial guesses, parameter bounds and the specific MAGIX settings for T_rot and N
- How the 1.6" source size was fit and the velocity offsets/linewidths fixed
- Distance to Orion KL
- Which lines were included in the final LTE fits (blended ones)
- Integration ranges for the line-integrated maps

## Analysis recipe

1. **Image the spectral data**: Calibrated uv data exported to Miriad and imaged with natural weighting  
  > "The calibrated UV data were exported to Miriad format, and images were using the Miriad software package" (2 Observations)
   - software: Miriad
   - fitting: _not stated_
   - validation: _not stated_
2. **Identify lines and extract spectra**: Identify with XCLASS using CDMS/JPL; require rest frequency, common vLSR, 5σ detection; spectra at EF intensity peaks; Gaussian fits to each line  
  > "We identified spectral line transitions using the eXtended CASA Line Analysis Software Suite (XCLASS; (cite: Moller17)), which accesses the Cologne Database for Molecular Spectroscopy" (3.1 Line Identification); "We performed Gaussian fits to every transition." (3.1 Line Identification)
   - software: XCLASS
   - parameter: 5σ detection threshold; rms from line-free channels among nearby 50 channels  
  > "In order to compute rms of a certain transition, we measured the rms value considering the line-free channels among the nearby 50 channels." (3.1 Line Identification)
   - fitting: _not stated_
   - validation: _not stated_
3. **Map spatial distributions**: Velocity-integrated maps of EF, MF, ET, t-HCOOH at low, intermediate and high Eu  
  > "We show in Figure 4 the line integrated maps of EF, MF, ET and t-HCOOH at different (lower, intermediate and higher) upper level energies" (3.2 Spatial Distributions)
   - software: Miriad
   - fitting: _not stated_
   - validation: _not stated_
4. **Derive T_rot and N by LTE modelling**: XCLASS LTE synthetic spectra with MAGIX optimisation; T_rot and N free, vLSR and linewidth fixed from Gaussian fits, source size 1.6" from IMFIT 2D Gaussian fits; both conformers fitted together  
  > "The algorithms we adopted are the Genetic, Levenberg-Marquardt and Error estimation using Interval-Nested-Sampling." (4.1 Rotational temperatures and column Densities); "We obtain the source sizes of 1.6$^{\prime\prime }$ for the hot core-SW and compact ridge based on the integrated maps of EF." (4.1 Rotational temperatures and column Densities)
   - software: XCLASS, MAGIX, Miriad IMFIT
   - assumption: LTE, with beam dilution, opacity and blending included  
  > "Under the assumption of local thermodynamical equilibrium (LTE), XCLASS takes into account the beam dilution, the line opacity and line blending" (4.1 Rotational temperatures and column Densities)
   - fitting: _not stated_
   - validation: _not stated_
5. **Derive N(H2) and abundances**: Optically thin dust continuum formula with Td 200 K (hot core), 100 K (compact ridge)  
  > "We used dust temperature of 200 K for the hot core and 100 K for the compact ridge (e.g., Wu et al. 2014; Favre et al. 2011)" (3.2 Molecular abundances)
   - assumption: grain radius 0.1 um, grain density 3 g/cm3, gas-to-dust 100, Q=2e-5 at 230 GHz, Td = rotation temperature  
  > "taking a grain radius of 0.1 $\mu$m, a grain density of 3 g cm$^{-3}$, and a gas-to-dust ratio of 100" (3.2 Molecular abundances)
   - fitting: _not stated_
   - validation: _not stated_
6. **Compare with chemical models**: Compare abundances, MF/EF ratios, T_rot and spatial distributions with Garrod08 grain-surface and Taquet16/Charnley95 gas-phase models  
  > "We compare in the following the result found in star-forming regions (Orion KL, W51 and Sgr B2(N)) with the predictions of the proposed models." (5 Discussion)
   - fitting: _not stated_
   - validation: _not stated_

## Software

- **Miriad** : Imaging and IMFIT 2D Gaussian source sizes  
  > "images were using the Miriad software package" (2 Observations)
- **XCLASS** : Line identification and LTE spectral modelling  
  > "We identified spectral line transitions using the eXtended CASA Line Analysis Software Suite (XCLASS" (3.1 Line Identification)
- **MAGIX** : Optimising LTE fit and error estimates  
  > "MAGIX is used to optimize the fit and find the best solutions of T$_{\rm rot}$ and N" (4.1 Rotational temperatures and column Densities)

## Numeric results

| quantity | value | uncertainty | units | step | quote |
|---|---|---|---|---|---|
| EF T_rot, hot core-SW | 122 | ±34 | K | 4 | 122 $\pm$ 34 K, (0.9 $\pm$ 0.3) $\times$ 10$^{16}$ cm$^{-2}$ for the hot core-SW |
| EF N, hot core-SW | 0.9e16 | ±0.3e16 | cm^-2 | 4 | 122 $\pm$ 34 K, (0.9 $\pm$ 0.3) $\times$ 10$^{16}$ cm$^{-2}$ for the hot core-SW |
| EF T_rot, compact ridge | 103 | ±13 | K | 4 | 103 $\pm$ 13 K, (0.6 $\pm$ 0.3) $\times$ 10$^{16}$ cm$^{-2}$ for the compact ridge |
| EF N, compact ridge | 0.6e16 | ±0.3e16 | cm^-2 | 4 | 103 $\pm$ 13 K, (0.6 $\pm$ 0.3) $\times$ 10$^{16}$ cm$^{-2}$ for the compact ridge |
| N(H2) hot core | 4.7e24 | ±0.2e24 | cm^-2 | 5 | (4.7 $\pm$ 0.2) $\times$ 10$^{24}$ cm$^{-2}$ and (2.0 $\pm$ 0.2) $\times$ 10$^{24}$ cm$^{-2}$ for the hot core and the compact ridge |
| N(H2) compact ridge | 2.0e24 | ±0.2e24 | cm^-2 | 5 | (4.7 $\pm$ 0.2) $\times$ 10$^{24}$ cm$^{-2}$ and (2.0 $\pm$ 0.2) $\times$ 10$^{24}$ cm$^{-2}$ for the hot core and the compact ridge |
| EF abundance hot core / compact ridge | 0.19e-8 / 0.3e-8 | ±0.06e-8 / ±0.1e-8 | relative to H2 | 5 | 122$\pm$34 / 0.9$\pm$0.3 / 0.19$\pm$0.06 / |
| MF T_rot, N (hot core-SW) | 135 K; 7e17 cm-2 | ±5 K; ±3e17 | K; cm^-2 | 4 | T$_{\rm rot}$ = 135 $\pm$ 5 K and N = (7 $\pm$ 3) $\times$ 10$^{17}$ cm$^{-2}$ toward the hot core-SW |
| ET T_rot, N (hot core-SW) | 144 K; 1.3e17 cm-2 | ±13 K; ±0.5e17 | K; cm^-2 | 4 | T$_{\rm rot}$ = 144 $\pm$ 13 K and N = (1.3 $\pm$ 0.5)$\times$ 10$^{17}$ cm$^{-2}$ toward the hot core-SW |
| t-HCOOH T_rot, N (hot core-SW) | 120 K; 6.2e15 cm-2 | ±16 K; ±1.8e15 | K; cm^-2 | 4 | We derive T$_{\rm rot}$ = 120 $\pm$ 16 K and N = (6.2 $\pm$ 1.8) $\times$ 10$^{15}$ cm$^{-2}$ toward the hot core-SW peak |
| MF/EF ratio hot core / compact ridge | 79 / 140 | ±36 / ±81 | dimensionless | 4 | our observed ratio values of (79$\pm$36)/1 for the hot core and (140$\pm$81)/1 for the compact ridge |

## Qualitative findings

- EF emits mainly from compact ridge and hot core-SW, peaking at same positions as MF; ET is absent from the compact ridge; HCOOH does not coincide with EF  
  > "The gas emission of MF is very similar to that of EF, while ET mainly originates from the hot core-SW but not from the compact ridge." (Summary)

## Claim tuples

- H: Does EF form via gas-phase reactions involving HCOOH and NH3? | E: Compared HCOOH abundance, HCOOH and NH3 spatial distribution with EF and with Taquet16 requirements | R: HCOOH abundance (1.3±0.4)e-9 far below model needs; no spatial coincidence of HCOOH or NH3 with EF | F: Gas-phase routes cannot produce the observed EF | **supported**
- H: Is EF formed on grain surfaces from MF-derived radicals? | E: Compared EF abundance, MF/EF ratio, T_rot and spatial co-peaking with Garrod08 model | R: EF abundance (2-3)e-9 and MF/EF ratios agree with model; EF and MF share peaks | F: EF likely formed on grains by CH3 addition to CH2OCHO and then evaporated | **supported**

## Reasoning

- Why this data: Interferometric high-resolution multi-transition data needed to get spatial distribution and source-averaged column densities  
  > "To better constrain the formation of this species, interferometric observations at high angular resolution and good sensitivity are needed." (1 Introduction)
- Why this method: _not stated_
- Alternative: Gas-phase formation (Charnley95, Taquet16) rejected  
  > "So this gas-phase reaction can not produce enough abundance of EF." (5 Discussion)
- How they decided it was enough: _not stated_
- Limitation (authors): Some EF lines are blended or affected by poor baseline subtraction and CDMS/JPL discrepancies; strong MF lines overestimated possibly by opacity and filtering  
  > "A possible explanation is a poor baseline subtraction at these spectral ranges, since Orion is a line-rich source, and it is difficult to find free-line channels" (4.1 Rotational temperatures and column Densities)
- Caveat (inferred, ours): LTE assumed with a single 1.6" source size for all species; MF opacity indicates this is imperfect
- Caveat (inferred, ours): N(H2) assumes Td equal to T_rot and uses continuum peaks from another paper
- Caveat (inferred, ours): Low angular resolution (~1.8") limits separation of components
- Caveat (inferred, ours): Model comparison uses abundances from single-dish literature with different beams

## Reproducibility

- Data public (paper): Public ALMA SV data  
  > "The data are available to the public and can be accessed from the ALMA-SV website" (2 Observations)
- Products in archive: _not stated_
- Missing: Calibration and imaging parameters
- Missing: Continuum subtraction details
- Missing: MAGIX/XCLASS fit setups and priors
- Missing: Integration ranges for maps
- Data volume (inferred): ~50-100 GB (20 spectral windows, SV data, calibrated products likely smaller)
- Score (inferred): 3/5, Public data and clear LTE fit outcomes, but imaging, continuum subtraction and fit setups are not specified.
- Rediscovery candidate: no, Recipe lacks imaging and fit details; main results depend on XCLASS/MAGIX setups and continuum values from another paper.

## Links

- Method: (cite: Moller17) (XCLASS)
- Method: (cite: Moller13) (MAGIX)
- Companion: (cite: Peng17) (Same dataset; peak positions)
- Companion: (cite: Wu14) (Same ALMA data; continuum intensities)
- Related: ALMA Science Verification Orion KL

## Checks

```json
{
 "quotes": 55,
 "quotes_ok": 55,
 "quote_pass_rate": 1.0,
 "quotes_too_long": 0,
 "unsupported_facts": 0,
 "project_codes": 1,
 "codes_not_in_text": [],
 "codes_not_in_obscore": [],
 "obscore_codes_not_in_card": [],
 "codes_printed_but_missing": [],
 "numeric_results": 11,
 "numeric_problems": 0,
 "fill": {
  "facts": 77,
  "stated": 37,
  "rate": 0.481
 },
 "evidence_ok": true
}
```
