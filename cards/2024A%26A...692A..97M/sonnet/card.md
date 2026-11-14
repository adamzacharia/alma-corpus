# Sulfur-bearing molecules in a sample of early star-forming cores

`2024A&A...692A..97M` | Astronomy and Astrophysics 2024 | first author: Martinez, N. C. | arXiv: 2411.00539 | DOI: 10.1051/0004-6361/202452350

Card schema 1.0 | model claude-sonnet-5-5 | depth full | type archival_reuse

## Science

- Fields: star_formation, astrochemistry, milky_way_ism
- Question: How do abundances of sulfur-bearing molecules (34SO, SO2, NS, SO, SO+, H2CS) relate to gas temperature, column density and line widths in early star-forming cores?  
  > "abundance measurements of S-bearing molecules and comparisons among them towards different interstellar environments are essential for understanding sulfur chemistry." (1 Introduction)
- Target **37 dense cores in infrared-quiet ATLASGAL clumps (e.g. 006.1879-0.3586 ... 359.6158-0.2429)**: coordinates Per-core RA/Dec in Table of sample (e.g. core 1: 18:01:02.075 -23.47.11.525)  
  > "Distances were obtained from the catalogs in Vizier ‘ATLASGAL cold high-mass clumps with NH$_{3}$’ (cite: wie12) and ‘Complete sample of Galactic clump properties’ (cite: urqu18)." (Source sample and data); "The ATLASGAL source names and the coordinates of the selected and analyzed molecular cores are presented in Table" (Source sample and data); z/distance 1.1 to 7.8 kpc (core 1 has no distance)  
  > "Distances were obtained from the catalogs in Vizier ‘ATLASGAL cold high-mass clumps with NH$_{3}$’ (cite: wie12) and ‘Complete sample of Galactic clump properties’ (cite: urqu18)." (Source sample and data); "The ATLASGAL source names and the coordinates of the selected and analyzed molecular cores are presented in Table" (Source sample and data); distance from Wienen et al. 2012 and Urquhart et al. 2018 catalogs  
  > "Distances were obtained from the catalogs in Vizier ‘ATLASGAL cold high-mass clumps with NH$_{3}$’ (cite: wie12) and ‘Complete sample of Galactic clump properties’ (cite: urqu18)." (Source sample and data); "The ATLASGAL source names and the coordinates of the selected and analyzed molecular cores are presented in Table" (Source sample and data)

## Data provenance

- ALMA projects: 2017.1.00914.S
- bands: Band 7 (0.87 mm continuum)  
  > "Data acquired in the ALMA Band 7 fulfill this requirement." (Source sample and data)
- frequencies and spectral setup: 333.3–349.1 GHz, spectral resolution 1.1 MHz  
  > "The observed frequency range and the spectral resolution are 333.3–349.1 GHz and 1.1 MHz, respectively." (Source sample and data)
- continuum bandwidth: _not stated_
- arrays: 7 m array, single pointing  
  > "The single-pointing observations for the 37 targets were carried out using the following telescope configuration: L5BL/L80BL(m): 8.7/27.5 in the 7 m array." (Source sample and data)
- configurations: _not stated_
- baselines: L5BL/L80BL 8.7/27.5 m  
  > "L5BL/L80BL(m): 8.7/27.5 in the 7 m array." (Source sample and data)
- angular resolution: 3.3" to 3.8"  
  > "The angular resolution goes from 3.3$''$ to 3.8$''$ for the whole sample." (Source sample and data)
- max recoverable scale: _not stated_
- sensitivity: continuum ~1.2 mJy/beam; line (10 km/s) ~30 mJy/beam  
  > "The continuum and line (each 10 km s$^{-1}$) sensitivity are about 1.2 and 30 mJy beam$^{-1}$." (Source sample and data)
- time on source: _not stated_
- observing dates: _not stated_
- pi or archival as stated: Archival, PI Csengeri  
  > "project 2017.1.00914 (PI: Csengeri) consists of observations in Band 7 towards massive infrared quiet clumps in the inner Galaxy" (Source sample and data)
- Line: 34SO 7(8)–6(7) (333.900 GHz)
- Line: SO2 v=0 8(2,6)–7(1,7) (334.673 GHz)
- Line: NS v=0 15/2–13/2 (346.221 GHz)
- Line: SO v=0 9(8)–8(7) (346.528 GHz)
- Line: SO+ 15/2–13/2 (1/2) l=f (348.115 GHz)
- Line: H2CS 10(1,9)–9(1,8) (348.534 GHz)
- Line: CH3OH 7(1,7)–6(1,6)++ and 12(1,11)–12(0,12)-+ (335.582 and 336.865 GHz)
- Other facility **ATLASGAL**: Parent clump sample, velocities and distances  
  > "The systemic velocities (v$_{\rm LSR}$), needed to identify the molecular lines, were obtained from the cataloged velocity of the ATLASGAL source" (Source sample and data)
- External data: Dust opacity 0.0185 cm2/g at 870 um  
  > "for which we adopt the value of 0.0185 cm$^2$g$^{-1}$ (cite: csengeri2017)" (Results) [from (cite: csengeri2017)]
- External data: Molecular line parameters (Eu, gu, Aul, Q) from Splatalogue/CDMS  
  > "Note: Parameters extracted from the Splatalogue Database for" (Table 2) [from (cite: muller05)]
- External data: Cloud distances and v_LSR from catalogs  
  > "Distances were obtained from the catalogs in Vizier ‘ATLASGAL cold high-mass clumps with NH$_{3}$’ (cite: wie12)" (Source sample and data) [from (cite: wie12), (cite: urqu18)]

## Processing

### Calibration

- pipeline or manual: Archival QA2 pipeline products used; some raw data reprocessed as a check  
  > "Thus, we reprocessed some raw data using CASA 4.5.1 and 4.7.2 versions and the calibration pipeline scripts." (Source sample and data)
- casa version: CASA 4.5.1 and 4.7.2 (reprocessing check)  
  > "we reprocessed some raw data using CASA 4.5.1 and 4.7.2 versions" (Source sample and data)
- pipeline version: _not stated_
- archive products used as is: Yes, archival cubes used  
  > "Consequently, we chose to rely on the archival data." (Source sample and data)
- flux calibrator: _not stated_
- flux scale uncertainty: _not stated_
- self calibration: _not stated_

### Imaging

- task: Archival cubes (clean); reprocessing tests with clean task  
  > "Particular care was taken with the different parameters of the task *clean*." (Source sample and data)
- deconvolver: _not stated_
- weighting robust: _not stated_
- uv taper: _not stated_
- cell size: _not stated_
- image size: _not stated_
- masking: _not stated_
- multiscale scales: _not stated_
- continuum subtraction: imcontsub, first-order polynomial, in some cases  
  > "A first-order polynomial was enough for an appropriate continuum subtraction after carefully selecting frequency ranges without molecular line emission in each spectral window." (Source sample and data)
- line free channels: _not stated_
- primary beam correction: _not stated_
- array combination: _not stated_
- smoothing: _not stated_
- final beam: _not stated_
- final rms: _not stated_

### Inherited from earlier work

- LTE column density method following Artur de la Villarmois et al.  
  > "assuming local thermodynamic equilibrium (LTE) and following (cite: artur23), firstly we derive the column densities of the upper levels" (Results) [from (cite: artur23)]
- N(H2) and mass equations  
  > "we use the following equation (cite: kauff08):" (Results) [from (cite: kauff08)]
- Rotational diagram procedure for CH3OH  
  > "from a typical rotational diagram procedure ((cite: goldsmith99); see Appendix [8](#appmetanol))" (Results) [from (cite: goldsmith99), (cite: miao95)]

### Not stated but needed to reproduce (our reading)

- Which cores were reprocessed and the clean parameters used
- Line-free channel ranges for continuum subtraction and which cores needed it
- Archival cube imaging parameters (weighting, robust, cell, size)
- Which spectral windows hold each line and the mapping to the beam-size extraction aperture
- Gaussian fitting code and initial guesses
- Linear fit method for abundance correlations
- Flux calibration uncertainty

## Analysis recipe

1. **Identify cores and extract spectra**: Cores identified in 0.87 mm continuum; most intense core per clump; spectra extracted at continuum peak with a beam-size circular region  
  > "the spectra from each of them were extracted at their continuum peak position using a beam-size circular region." (Results)
   - software: CASA
   - fitting: _not stated_
   - validation: _not stated_
2. **Fit line profiles**: Gaussian fits to each line for peak, FWHM and integrated flux W; only main component fitted when wings present  
  > "Gaussian fittings to each line were applied to obtain the intensity peaks, the FWHM $\Delta$v, and the integrated line intensity" (Results)
   - fitting: _not stated_
   - validation: Lines well fitted by Gaussians, no absorption or flattening  
  > "None of the analyzed lines showed signs of absorption or flattening, and all were well-fitted by Gaussians" (Results)
3. **Derive molecular column densities**: Upper-level column density from W, Aul and beam area, then total column density using partition function  
  > "Then, the total column density of each molecule was obtained from:" (Results)
   - assumption: Tex = 20 K for all lines and cores; optically thin  
  > "A ${\rm T_{ex}}$ of 20 K was assumed for the excitation of all lines uniformly in the whole sample." (Results)
   - fitting: _not stated_
   - validation: Optical depths computed for all lines, mostly <<1; correction ~factor 2 for cores 29 and 30 does not change results  
  > "Almost all values of $\tau$ are $<<1$, showing that indeed the lines are optically thin." (Calculation of optical depths)
4. **Derive core temperature from CH3OH**: Rotational diagram from two CH3OH lines, Trot taken as Tkin  
  > "we obtain the rotational temperatures that were assumed to be the T$_{\rm kin}$ of each core" (Results)
   - assumption: LTE, optically thin, beam filling factor 1  
  > "By assuming LTE conditions, optically thin lines, and a beam filling factor equal to the unity" (Calculation of Trot from the CH3OH)
   - fitting: Linear fit to the Boltzmann equation for Ntot/Qrot and Trot  
  > "The free parameters, (${\rm N_{tot}/Q_{rot}}$) and ${\rm T_{rot}}$ were determined by a linear fitting" (Calculation of Trot from the CH3OH)
   - validation: Opacity correction affects both lines similarly so Trot unaffected  
  > "it modifies the ${\rm N_u}$ value in a similar way for both transitions, and therefore it does not affect the ${\rm T_{rot}}$ estimation." (Calculation of Trot from the CH3OH)
5. **Derive N(H2), mass and density from continuum**: Kauffmann et al. 2008 formulae with beam-integrated 0.87 mm flux; density from sphere of beam diameter  
  > "The volume densities were derived assuming spherical symmetries with a diameter of the beam" (Results)
   - assumption: kappa = 0.0185 cm2/g at 870 um; Tdust = Tkin  
  > "We assume thermal coupling between dust and gas (i.e. T$_{\rm dust}$=T$_{\rm kin}$)." (Results)
   - fitting: _not stated_
   - validation: _not stated_
6. **Abundance and line width correlations**: X = N/N(H2); linear fits with R2 of X vs T, X vs N, X vs X; line width histograms and Pearson coefficients  
  > "All figures present the results of a linear fitting with the coefficient of determination R$^{2}$." (Molecular abundances)
   - fitting: Linear regression  
  > "All figures present the results of a linear fitting with the coefficient of determination R$^{2}$." (Molecular abundances)
   - validation: Compared with Fontani et al. 2023 and Chen et al. 2024  
  > "(cite: fontani23) presented relations of abundances of SO$^{+}$, NS, SO$_{2}$, and H$_{2}$CS with SO" (Discussion)

## Software

- **CASA** 4.5.1 and 4.7.2: Reprocessing check, imcontsub, line identification  
  > "the task *imcontsub* in CASA was used to subtract it." (Source sample and data)
- **Splatalogue** : Line identification and spectroscopic parameters (JPL, CDMS)  
  > "The molecular line identification was made using CASA software by cross checking with the JPL and CDMS databases using the Splatalogue" (Example of spectra and Gaussian fittings)

## Numeric results

| quantity | value | uncertainty | units | step | quote |
|---|---|---|---|---|---|
| Mean X(SO2)/X(SO) | 1.6 | not stated | dimensionless | 6 | We obtain a media of 1.6, with a maximum value of 9.29 and a minimum of 0.06. |
| Average CH3OH-derived temperature of sample | 65 | not stated | K | 4 | The average measured temperature of our sample is 65 K. |
| Pearson coefficients of X vs X(SO) for SO+, NS, SO2, H2CS | 0.83, 0.87, 0.93, 0.93 | not stated | dimensionless | 6 | for such abundance relations are 0.83, 0.87, 0.93, and 0.93, respectively. |
| Pearson correlation of H2CS and NS line widths | 0.93 | not stated | dimensionless | 6 | there is an excellent correlation between H$_2$CS and NS ($\rho = 0.93$) |

## Qualitative findings

- Abundances of all S-bearing species increase with gas temperature at similar rates over 20–100 K  
  > "the abundance of all analyzed sulfur-bearing species increases with the temperature" (Discussion)
- O-bearing species have larger line widths, tracing warmer, more turbulent gas; H2CS and NS trace quiescent gas  
  > "We note that the four O-bearing species have larger $\Delta$v than the other molecular species" (Discussion)

## Claim tuples

- H: Do S-bearing molecule abundances depend on temperature in early cores? | E: Abundances from ALMA column densities and N(H2) vs CH3OH temperature | R: Positive correlations with similar slopes for all species | F: Supports sulfur frozen on grains released with warming, though gas-phase activation not excluded | **supported**
- H: Are the species chemically related at early stages? | E: Abundance-abundance correlations compared to more evolved samples | R: R2>0.75, sometimes ~0.9; higher than in Fontani et al. 2023 | F: Similar chemical origin, correlations decrease with evolution | **partially**
- H: Can X(SO2)/X(SO) serve as a chemical clock? | E: Compare measured ratios with chemical models | R: Ratios agree with a core evolved ~1e5 yr at 60 K | F: Observations may support its use as a clock | **partially**
- H: Do line widths reveal different gas layers? | E: Line width distributions and pairwise correlations | R: H2CS narrowest, SO2 widest; none near y=x except 34SO vs NS | F: O-bearing species trace inner turbulent gas, H2CS and NS the outer quiescent envelope | **supported**

## Reasoning

- Why this data: Band 7 archival project covers several S-bearing lines toward many early-stage cores  
  > "we first looked in the ALMA database for data containing several lines of sulfur-bearing species." (Source sample and data)
- Why this method: _not stated_
- Alternative: Reprocessing raw data gave images and spectra close to archival ones, so archival data adopted  
  > "The images and spectra from our data reprocessing, following multiple runs of the *clean* task with varied parameters, closely resembled the archival data." (Source sample and data)
- How they decided it was enough: _not stated_
- Limitation (authors): N(H2) may be underestimated due to dust opacity  
  > "However, we can not rule out a possible underestimation in the N(H$_{2}$) due to dust opacity effects." (Discussion)
- Limitation (authors): Sample not uniform in evolutionary stage; chemical ages unknown  
  > "it is likely that this sample of clumps is not fully uniform, potentially exhibiting variations in evolutionary stage." (Discussion)
- Caveat (inferred, ours): Single Tex=20 K for all lines while Tkin is 20–100 K biases column densities
- Caveat (inferred, ours): Resolution of ~3.5" mixes envelope and core gas; beam-averaged abundances
- Caveat (inferred, ours): Abundance-temperature correlation may be partly driven by shared N(H2) dependence and common distance/flux scaling
- Caveat (inferred, ours): No uncertainty propagation for mass and density; 7m-only data resolve out extended emission
- Caveat (inferred, ours): Hydrogen column from continuum with fixed kappa and Tdust=Tkin

## Reproducibility

- Data public (paper): Data from ALMA Science Archive  
  > "were obtained from the ALMA Science Archive" (Source sample and data)
- Products in archive: _not stated_
- Missing: Gaussian fitting scripts and aperture details
- Missing: Imaging parameters of archival products
- Missing: Line-free channels per spw
- Data volume (inferred): Tens of GB (37 fields, archival 7m cubes)
- Score (inferred): 4/5, Public archival data and explicit formulas with tabulated inputs; minor imaging/fitting details missing.
- Rediscovery candidate: yes, Public data, explicit LTE and rotational-diagram recipe, numeric tables of results.

## Links

- Method: (cite: artur23) (LTE column density method)
- Method: (cite: kauff08) (N(H2) and mass equations)
- Method: (cite: goldsmith99) (Rotational diagram)
- Companion: (cite: fontani23) (Single-dish sulfur abundances toward evolved cores, compared)
- Companion: (cite: chen24) (H2CS in massive protoclusters, compared)
- Related: ATLASGAL
- Related: ALMA project 2017.1.00914.S (Csengeri)

## Checks

```json
{
 "quotes": 68,
 "quotes_ok": 68,
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
  "facts": 78,
  "stated": 47,
  "rate": 0.603
 },
 "evidence_ok": true
}
```
