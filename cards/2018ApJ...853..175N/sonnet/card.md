# ALMA Reveals Molecular Cloud N55 in the Large Magellanic Cloud as a Site of Massive Star Formation

`2018ApJ...853..175N` | The Astrophysical Journal 2018 | first author: Naslim, N. | arXiv: 1801.01653 | DOI: 10.3847/1538-4357/aaa5b0

Card schema 1.0 | model claude-sonnet-5-5 | depth full | type observational_alma_primary

## Science

- Fields: nearby_galaxies, star_formation, milky_way_ism
- Question: How do the molecular clump properties (size, linewidth, mass, X_CO, mass spectrum) of N 55 in the LMC compare with Galactic clouds, and how do they relate to star formation?  
  > "We have done a detailed study of molecular gas properties, to understand how the cloud properties of N 55 differ from Galactic clouds." (abstract)
- Target **N 55 (LMC)**: coordinates RA ~05h32m15.49s, Dec ~-66d26m14.00s  
  > "The area of coverage was 4$^{\prime}\times$6$^{\prime}$ at the center position" (4 Observations); "due to its proximity (50 kpc) and favorable viewing angle" (1 Introduction); z/distance 50 kpc (LMC)  
  > "The area of coverage was 4$^{\prime}\times$6$^{\prime}$ at the center position" (4 Observations); "due to its proximity (50 kpc) and favorable viewing angle" (1 Introduction); distance from (cite: Pietrzy13; van01)  
  > "The area of coverage was 4$^{\prime}\times$6$^{\prime}$ at the center position" (4 Observations); "due to its proximity (50 kpc) and favorable viewing angle" (1 Introduction)

## Data provenance

- ALMA projects: 2013.1.00214.S, 2012.1.00335.S
- bands: Band 3  
  > "using band 3 receivers in spectral windows centered at 115.27, 110.20 and 109.67 GHz" (4 Observations)
- frequencies and spectral setup: SPWs at 115.27, 110.20, 109.67 GHz; 70.557 kHz (0.2 km/s) resolution; 117.18 MHz bandwidth each  
  > "In each spectral window, the correlator was set to have a bandwidth of 117.18 MHz." (4 Observations)
- continuum bandwidth: _not stated_
- arrays: 12 m array  
  > "missing flux caused by interferometric observation with ALMA 12 m array" (4 Observations)
- configurations: _not stated_
- baselines: _not stated_
- angular resolution: 12CO: 3.5"x2.3" (0.84x0.55 pc); 13CO: 3.1"x2.5" (0.74x0.60 pc)  
  > "The synthesized beam for $^{12}$CO(1-0) is approximately 3.5$^{\prime\prime}\times$2.3$^{\prime\prime}$ which corresponds to 0.84$\times$0.55 pc$^2$." (4 Observations)
- max recoverable scale: _not stated_
- sensitivity: 12CO ~70 mJy/beam (0.8 K) per 0.2 km/s channel; 13CO 20 mJy/beam (0.30 K)  
  > "The achieved rms per channel over 0.2 km s$^{-1}$ is about $\sim$70 mJy beam$^{-1}$ (0.8 K)." (4 Observations)
- time on source: 12CO 70 min (1 EB); 13CO 4 EBs of 55, 51, 65, 57 min  
  > "uid://A002/X98ed3f/X1cf5 | 2015-01-06 | 70" (Table 1)
- observing dates: 2013-12-31 to 2015-01-22  
  > "uid://A002/X9a24bb/X1460 | 2015-01-22 | 57" (Table 1)
- pi or archival as stated: _not stated_
- Line: 12CO J=1-0 (115.27 GHz)
- Line: 13CO J=1-0 (110.20 GHz)
- Other facility **Mopra**: Single-dish 12CO(1-0) to estimate missing flux  
  > "we compare our data with the single dish Mopra observation of $^{12}$CO(1-0)." (4 Observations)
- Other facility **Spitzer/Herschel**: YSO candidates and IRAC 8 um maps  
  > "we adopt the YSOs identified from *Spitzer* and *Herschel* observations" (8.3 Star formation)
- External data: Abundance ratios [12CO/13CO]=50 and [12CO/H2]=1.6e-5 derived for N 159  
  > "We adopt abundance ratios of 50 for \[$^{12}$CO/$^{13}$CO\] and 1.6$\times$10$^{-5}$ for \[$^{12}$CO/H$_2$\] which were derived for N 159 in the LMC" (5 Molecular mass determination) [from (cite: mizuno10)]
- External data: YSO catalogs (16 YSOs in N 55)  
  > "(cite: gruendl09) and (cite: seale14) identified about 16 young stellar objects in N 55 using infrared colors." (8.3 Star formation) [from (cite: gruendl09; seale14)]

## Processing

### Calibration

- pipeline or manual: _not stated_
- casa version: _not stated_
- pipeline version: _not stated_
- archive products used as is: _not stated_
- flux calibrator: Uranus and Ganymede  
  > "Uranus and Ganymede were used as flux calibrators." (4 Observations)
- flux scale uncertainty: _not stated_
- self calibration: _not stated_

### Imaging

- task: CASA, visibilities imaged  
  > "The data were processed in the Common Astronomy Software Application (CASA[^1]) package and visibilities imaged." (4 Observations)
- deconvolver: _not stated_
- weighting robust: _not stated_
- uv taper: _not stated_
- cell size: _not stated_
- image size: _not stated_
- masking: Moment-masked cube (Dame 2011) to suppress noise  
  > "We use a moment masked cube (cite: dame11) to suppress the noise effect in our analysis." (4 Observations)
- multiscale scales: _not stated_
- continuum subtraction: _not stated_
- line free channels: _not stated_
- primary beam correction: _not stated_
- array combination: _not stated_
- smoothing: _not stated_
- final beam: 12CO 3.5"x2.3"; 13CO 3.1"x2.5"  
  > "For $^{13}$CO(1-0) the synthesized beam is about 3.1$^{\prime\prime}\times$2.5$^{\prime\prime}$" (4 Observations)
- final rms: 12CO ~70 mJy/beam; 13CO 20 mJy/beam per 0.2 km/s  
  > "the achieved sensitivity per channel over 0.2 km s$^{-1}$ is 20 mJy beam$^{-1}$ (0.30 K)" (4 Observations)

### Inherited from earlier work

- 13CO column density formula and LTE method  
  > "we follow the method given by (cite: dickman78), (cite: pineda08), (cite: pineda10) and (cite: nishimura15)" (5 Molecular mass determination) [from (cite: dickman78; pineda08; pineda10; nishimura15)]
- Virial mass formula M=1040 sigma_v^2 R  
  > "derive the virial mass from the radius (R) and velocity dispersion ($\sigma_v$) of the clump (cite: wong11) as" (5 Molecular mass determination) [from (cite: wong11)]
- Bootstrap uncertainty method  
  > "we use a bootstrapping technique similar to the method given in (cite: rosolowsky08)." (6 Clump decomposition) [from (cite: rosolowsky08)]

### Not stated but needed to reproduce (our reading)

- CASA version and whether archive pipeline products were used
- Imaging parameters (weighting/robust, deconvolver, cell/image size, cleaning threshold)
- Whether 7m/ACA data used; array configurations
- astrodendro parameters (min_value, min_delta, min_npix)
- Moment-mask smoothing kernels and thresholds
- Mass spectrum fitting method, bins and fit ranges
- Mopra-based flux correction applied or not
- Regression method for scaling relations

## Analysis recipe

1. **Image cubes and apply moment mask**: Image in CASA; moment-masked cube to zero emission-free pixels  
  > "The moment masked cube has zero values at the emission free pixels, which is useful to avoid a large error arising from the random noise." (4 Observations)
   - software: CASA
   - fitting: _not stated_
   - validation: Compared with Mopra: ~30% of ALMA flux missing at 45"  
  > "About 30$\%$ of the ALMA flux is missing when smoothed to 45" and compared to the Mopra observations." (4 Observations)
2. **Decompose into leaves/trunks and measure properties**: astrodendro on 12CO and 13CO cubes; radius R=1.91 sigma_r, sigma_v from second moment, L_CO from summed flux; bootstrap errors  
  > "The rms radius in the second spatial moments obtained from *astrodendro* is converted into the radius of a spherical cloud $R=1.91\sigma_r$ (cite: solomon87)." (6 Clump decomposition)
   - software: astrodendro
   - parameter: 100 bootstrap iterations  
  > "We use 100 iterations to sample the derived parameters." (6 Clump decomposition)
   - assumption: Spherical clouds; no deconvolution, structures below resolution (~0.55 pc) flagged  
  > "Thus, instead of attempting to correct for instrumental resolution, we indicate the regions (as shaded blue)" (6 Clump decomposition)
   - fitting: _not stated_
   - validation: Trunks all above resolution limit; ~30% of leaves below it  
  > "About 30$\%$ of the dendrogram leaves are having a size below the resolution limit" (6 Clump decomposition)
3. **Derive LTE and virial masses**: Tex from 12CO peak, 13CO tau and N(13CO), N(H2)=(50/1.6e-5)N(13CO), mean molecular weight 2.7; M_VIR=1040 sigma^2 R  
  > "Hence, we obtain an H$_2$ column density of $N({\rm H_2})=\frac{50}{1.6\times10^{-5}}N(^{13}\rm CO)$." (5 Molecular mass determination)
   - assumption: Optically thin 13CO, LTE, same Tex for 12CO and 13CO; LMC distance; LTE/LVG scatter ~40%  
  > "the ratio of LTE to LVG model masses is around unity, however there is a scatter about 40$\%$." (5 Molecular mass determination)
   - fitting: _not stated_
   - validation: LTE vs virial mass comparison, ratio 1.12  
  > "The ratio of LTE mass to virial mass shows an average value of 1.12" (7.1)
4. **Scaling relations, X_CO and mass spectra**: Fit size-linewidth, sigma^2/R vs surface density, virial mass-luminosity (X_CO), and differential mass spectra dN/dM ∝ M^-alpha for leaves and trunks  
  > "in our analysis we use the differential form of clump mass spectrum i.e. $dN/dM = f(M)$." (7.3)
   - fitting: Power-law fits; method not stated  
  > "The trunks reveal the high mass end of mass spectra in both $^{12}$CO(1-0) and $^{13}$CO(1-0) which are fitted with the functions $dN/dM \propto M^{-1.5\pm0.15}$ and $dN/dM \propto M^{-1.8\pm0.25}$ respectively." (Cloud mass spectrum)
   - validation: Index not affected by mass bins; compared with Orion (astrodendro on Dame 2001 data), 30 Dor, Galactic clouds  
  > "We find that index of the power law is not affected by the mass bins we adopted." (7.3)

## Software

- **CASA** : Data processing and imaging  
  > "The data were processed in the Common Astronomy Software Application (CASA[^1]) package and visibilities imaged." (4 Observations)
- **astrodendro** : Clump decomposition (leaves/trunks), also Orion data  
  > "we use the python package *astrodendro*." (6 Clump decomposition)

## Numeric results

| quantity | value | uncertainty | units | step | quote |
|---|---|---|---|---|---|
| X_CO | 6.5e20 | not stated | cm^-2 (K km/s)^-1 | 4 | the $^{12}$CO(1-0)-to-H$_2$ conversion factor, X$_{\rm CO}$, is 6.5$\times$10$^{20}$ cm$^{-2}$ (K km s$^{-1}$)$^{-1}$ |
| Mean LTE/virial mass ratio | 1.12 | not stated | dimensionless | 3 | The ratio of LTE mass to virial mass shows an average value of 1.12 |
| M_VIR vs M_LTE power-law index | 0.68 | 0.12 | dimensionless | 3 | $M_{{\rm VIR}}$=1.75$M_{{\rm LTE}}^{0.68\pm0.12}$ |
| Mass-luminosity index (log M vs log L_CO) | 1.15 | 0.3 | dimensionless | 4 | log($M$)=($1.15\pm0.3$) log($L_{\rm CO})+1.0$ |
| Low-mass spectrum index 12CO / 13CO | 0.5 / 0.6 | 0.1 / 0.2 | dimensionless | 4 | fitted with a power law of index 0.5$\pm$0.1, while for $^{13}$CO it is fitted with a power law index 0.6$\pm$0.2 |
| High-mass spectrum index (leaves) 12CO / 13CO | 2.0 / 2.5 | 0.3 / 0.4 | dimensionless | 4 | fitted with a power index of 2.0$\pm$0.3 for $^{12}$CO, and with 2.5$\pm$0.4 for $^{13}$CO |
| Trunk mass spectrum index 12CO / 13CO | 1.5 / 1.8 | 0.15 / 0.25 | dimensionless | 4 | $dN/dM \propto
M^{-1.5\pm0.15}$ and $dN/dM \propto M^{-1.8\pm0.25}$ respectively |
| Size-linewidth index | 0.5 | 0.05 | dimensionless | 4 | The size-linewidth relation is a power law with an index of 0.5$\pm$0.05 |

## Qualitative findings

- N 55 clumps are in self-gravitational virial equilibrium with negligible external pressure; star-forming cores have larger linewidths and masses.  
  > "These findings indicate that N 55 clumps are in self-gravitational virial equilibrium with negligible external pressure." (9 Summary)

## Claim tuples

- H: Are N 55 clumps gravitationally bound? | E: Compare LTE and virial masses; sigma^2/R vs surface density | R: Ratio 1.12; clumps lie on virial equilibrium line | F: Clumps bound with negligible external pressure | **supported**
- H: Does X_CO differ from Galactic value at ~0.67 pc scale? | E: Virial mass vs 12CO luminosity | R: X_CO = 6.5e20 | F: About two times Orion value | **supported**
- H: Is the core mass function similar to Galactic clouds? | E: Differential mass spectra of leaves and trunks | R: Turnover below 200 Msun; power laws as listed | F: Consistent with many Galactic clouds | **supported**

## Reasoning

- Why this data: N55 chosen as less extreme than 30 Dor / N 159, from Spitzer/Herschel studies  
  > "This region is less extreme than the well studied 30 Doradus or N 159 environments." (1 Introduction)
- Why this method: _not stated_
- Alternative: Deconvolution/extrapolation of sizes rejected; unresolved structures flagged instead  
  > "Thus, instead of attempting to correct for instrumental resolution, we indicate the regions (as shaded blue)" (6 Clump decomposition)
- How they decided it was enough: _not stated_
- Limitation (authors): ~30% flux missing vs Mopra; moment mask removes small faint clouds; LTE assumptions  
  > "The caveat of this method is that it eliminates small clouds with low peak intensity" (4 Observations)
- Caveat (inferred, ours): Missing flux (~30%) not corrected, biasing masses and linewidths
- Caveat (inferred, ours): Single-LMC-cloud X_CO relies on virial equilibrium assumption (circular)
- Caveat (inferred, ours): LTE masses depend on adopted LMC abundance ratios from N 159
- Caveat (inferred, ours): No stated fitting uncertainties method; no resolution correction

## Reproducibility

- Data public (paper): _not stated_
- Products in archive: _not stated_
- Missing: Imaging parameters and CASA version
- Missing: astrodendro parameters
- Missing: Fitting procedures
- Data volume (inferred): ~100-300 GB raw for 2 projects
- Score (inferred): 3/5, Data identifiable and analysis formulas given, but imaging and dendrogram parameters unstated.
- Rediscovery candidate: no, Key parameters (astrodendro settings, imaging, fit methods) missing.

## Links

- Method: (cite: rosolowsky08) (dendrogram method and bootstrap errors)
- Method: (cite: pineda08) (13CO column density formula)
- Companion: (cite: nas15) (Spitzer H2 detection in N55)
- Related: SAGE
- Related: HERITAGE
- Related: MAGMA

## Checks

```json
{
 "quotes": 60,
 "quotes_ok": 60,
 "quote_pass_rate": 1.0,
 "quotes_too_long": 0,
 "unsupported_facts": 0,
 "project_codes": 2,
 "codes_not_in_text": [],
 "codes_not_in_obscore": [],
 "obscore_codes_not_in_card": [],
 "codes_printed_but_missing": [],
 "numeric_results": 8,
 "numeric_problems": 0,
 "fill": {
  "facts": 70,
  "stated": 41,
  "rate": 0.586
 },
 "evidence_ok": true
}
```
