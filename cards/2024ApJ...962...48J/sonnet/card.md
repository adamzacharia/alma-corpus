# Thermal Properties of the Hot Core Population in Sagittarius B2 Deep South.

`2024ApJ...962...48J` | The Astrophysical Journal 2024 | first author: Jeff, D. | arXiv: 2401.09749 | DOI: 10.3847/1538-4357/ad1507

Card schema 1.0 | model claude-sonnet-5-5 | depth full | type archival_reuse

## Science

- Fields: star_formation, astrochemistry, milky_way_ism
- Question: What are the thermal and physical properties (temperature, mass, radius, density profile, CH3OH abundance) of the hot cores in Sgr B2 Deep South, and how do they compare with Galactic disk hot cores and Sgr B2(N)?  
  > "We measure the rotational temperature of CH$_3$OH and derive the physical conditions present within these cores and the hot core Sgr B2(S)." (abstract)
- Target **Sgr B2 Deep South (DS1-DS9) and Sgr B2(S)**: coordinates Sgr B2(S) 17:47:20.48 -28:23:46.3 (ICRS); DS1-DS9 listed in Table 2  
  > "$D=8.34$ kpc is the distance to Sgr B2" (3.2.2 Radial density profiles); "| Sgr B2(S) | 17:47:20.48(0.02) | -28:23:46.3(0.3) | 69.3 | $20_{1}-20_{0}$ E1 |  |" (Table 2); z/distance 8.34 kpc  
  > "$D=8.34$ kpc is the distance to Sgr B2" (3.2.2 Radial density profiles); "| Sgr B2(S) | 17:47:20.48(0.02) | -28:23:46.3(0.3) | 69.3 | $20_{1}-20_{0}$ E1 |  |" (Table 2); distance from chosen for consistency with Schmiedeke2016  
  > "$D=8.34$ kpc is the distance to Sgr B2" (3.2.2 Radial density profiles); "| Sgr B2(S) | 17:47:20.48(0.02) | -28:23:46.3(0.3) | 69.3 | $20_{1}-20_{0}$ E1 |  |" (Table 2)

## Data provenance

- ALMA projects: 2017.1.00114.S
- bands: Band 6, 12 m  
  > "We have carried out this work using 12 m Band 6 data" (2.1 Data reduction and imaging)
- frequencies and spectral setup: 4 spws centered 217.35, 219.20, 231.30, 233.18 GHz; 1.875 GHz bandwidth each; 488 kHz (~0.6 km/s) resolution; 10 fields  
  > "Each field contains four spectral windows, centered on 217.35, 219.20, 231.30, and 233.18 GHz, respectively." (2.1 Data reduction and imaging); "Each spectral window has a bandwidth of 1.875 GHz and a spectral resolution of 488 kHz ($\sim0.6$ km s$^{-1}$)." (2.1 Data reduction and imaging)
- continuum bandwidth: _not stated_
- arrays: _not stated_
- configurations: _not stated_
- baselines: _not stated_
- angular resolution: 0.36" x 0.29" (continuum)  
  > "achieving a beam size of $0.36\ensuremath{''}\times 0.29\ensuremath{''}$" (2.1 Data reduction and imaging)
- max recoverable scale: LAS 2.075"  
  > "The largest angular scale (LAS) of our observations was 2.075”" (2.1 Data reduction and imaging)
- sensitivity: _not stated_
- time on source: _not stated_
- observing dates: _not stated_
- pi or archival as stated: _not stated_
- Line: CH3OH 5_1-4_2 E1, 10_2--9_3-, 8_0-7_1 E1, 20_1-20_0 E1 and 13 others (Table 1) (216.946-233.917 GHz)
- Other facility **Bolocam Galactic Plane Survey (1.1 mm)**: Large-scale continuum feathered with ALMA  
  > "we use `uvcombine` to feather the Atacama Large Millimeter/submillimeter Array (ALMA) observations with 1.1 mm continuum data from the Bolocam Galactic Plane Survey" (2.1 Data reduction and imaging)
- External data: Dust opacity kappa=0.008 cm2/g (gas-to-dust 100)  
  > "The opacity constant $\kappa_\nu=0.008$ cm$^2$ g$^{-1}$ (cite: OssenkopfandHenning1994) implicitly assumes a gas-to-dust ratio of 100." (3.2.2 Radial density profiles) [from (cite: OssenkopfandHenning1994)]
- External data: CORE hot core masses, radii, density and temperature power-law indices for comparison  
  > "The masses reported in Table 3 of (cite: Gieser+2021) were derived using a gas to dust ratio $\frac{M_{gas}}{M_{dust}}=150$" (4.2 Comparison to Galactic disk hot cores) [from (cite: Gieser+2021)]
- External data: Sgr B2(S) H2 mass of 4472 Msun within 0.35 pc  
  > "Within this radius, we quote their measured H$_2$ mass of 4472 M$_\odot$." (4.1) [from (cite: Schmiedeke2016)]
- External data: CH3OH abundances of other hot cores (Sgr B2 N1-N5, W51, Orion KL, WB 89789)  
  > "we compare peak abundance values as a function of coincident temperature to a selection of hot cores in Sgr B2" (4.4) [from (cite: Busch+2022; Bonfand2017; Ginsburg2017; Crockett+2014; Shimonishi+2021)]

## Processing

### Calibration

- pipeline or manual: _not stated_
- casa version: _not stated_
- pipeline version: _not stated_
- archive products used as is: _not stated_
- flux calibrator: _not stated_
- flux scale uncertainty: _not stated_
- self calibration: _not stated_

### Imaging

- task: tclean, CASA 5.6.0  
  > "using `tclean`(CASA version 5.6.0, (cite: McMullin2007))" (2.1 Data reduction and imaging)
- deconvolver: _not stated_
- weighting robust: robust 0 for line cubes; robust 2 for continuum  
  > "Data cubes for each spectral window were produced using a robust parameter of 0" (2.1 Data reduction and imaging); "imaged with a Briggs robust parameter of 2" (2.1 Data reduction and imaging)
- uv taper: _not stated_
- cell size: 0.05"  
  > "our pixel scale was 0.05”" (2.1 Data reduction and imaging)
- image size: _not stated_
- masking: _not stated_
- multiscale scales: _not stated_
- continuum subtraction: STATCONT --continuum mode per spw  
  > "we use the `--continuum` mode of STATCONT (cite: SanchezMonge2018) to perform continuum subtraction on each spectral window" (2.1 Data reduction and imaging)
- line free channels: _not stated_
- primary beam correction: _not stated_
- array combination: Feathering with BGPS 1.1 mm using uvcombine  
  > "we use `uvcombine` to feather the Atacama Large Millimeter/submillimeter Array (ALMA) observations" (2.1 Data reduction and imaging)
- smoothing: _not stated_
- final beam: 0.36" x 0.29"  
  > "achieving a beam size of $0.36\ensuremath{''}\times 0.29\ensuremath{''}$" (2.1 Data reduction and imaging)
- final rms: cube clean threshold 3.09 mJy (3 sigma); feathered continuum ~0.2 mJy  
  > "The lowest noise level away from bright sources in the feathered continuum image is $\sim0.2$ mJy." (2.1 Data reduction and imaging)

### Inherited from earlier work

- Radial power-law modelling of temperature and density follows Gieser et al. 2021  
  > "we follow (cite: Gieser+2021), who created radial power-law indices to model the physical characteristics of a catalogue of hot cores in the Galactic Disk" (3.2 Core physical structure) [from (cite: Gieser+2021)]
- Distance 8.34 kpc to Sgr B2  
  > "We choose a distance of 8.34 kpc to Sgr B2 to maintain consistency with (cite: Schmiedeke2016)" (3.2.2 Radial density profiles) [from (cite: Schmiedeke2016)]

### Not stated but needed to reproduce (our reading)

- Pipeline/manual calibration and flux calibrator details
- Line-free channel selection and STATCONT parameters
- Clean masks and image size
- Which Ntot/NH2 pixels and beam definition used for mass integration
- Broken power-law fitting method and priors
- Column densities adopted for 25 species in spectral models
- Partition function source and spectroscopic catalog entries used

## Analysis recipe

1. **Image cubes and continuum**: tclean cubes per spw; 4-spw continuum; feather with BGPS 1.1 mm  
  > "We produced a continuum image by combining all four spectral windows with `tclean`." (2.1 Data reduction and imaging)
   - software: CASA, uvcombine, STATCONT
   - parameter: robust 0 cubes, 3 sigma = 3.09 mJy threshold  
  > "cleaning to a threshold of 3$\sigma$ above the noise (3.09 mJy)" (2.1 Data reduction and imaging)
   - fitting: _not stated_
   - validation: _not stated_
2. **Identify hot core candidates**: By-eye search of CH3OH in 1 mm cubes; require >3 sigma compact (<0.1 pc) 10_2--9_3- detection; within HPBW; line IDs via astroquery/JPL/Splatalogue  
  > "we choose the detection of the $10_{2-}-9_{3-}$ line to mark hot core candidates ($E_{upper} = 165$ K" (2.2.1 Source Identification)
   - software: astroquery, astropy, Splatalogue
   - fitting: Single Gaussian, Levenberg-Marquardt, for velocity  
  > "We then fit a single-component Gaussian to the line using the Levenberg-Marquardt least-squares fitter in `astropy` to obtain a precise doppler velocity" (Methods, Data Analysis, Source Identification)
   - validation: _not stated_
3. **Rotational temperature and column density maps**: Per-pixel rotational diagrams of CH3OH lines selected by LTE >3 sigma prediction, continuum dilution corrected, linear fit for Trot, Ntot  
  > "we construct per-pixel rotational diagrams for the detected CH$_3$OH transitions" (2.3)
   - software: astropy, pyspeckit
   - parameter: LTE trial T=150-300 K, Ntot=0.1-1.0e17 cm-2; line peak >=3 sigma_SC  
  > "$T=150-300$ K and $N_{tot} = 0.1-1.0 \times10^{17}$ cm$^{-2}$" (2.3)
   - assumption: LTE, optically thin, Tex=Trot  
  > "setting $T_{ex}=T_{rot}$" (2.3)
   - fitting: Linear fit; errors from 1000 bootstrap resamples (Gaussian std)  
  > "In each pixel, we perform 1000 bootstrap resampling iterations." (2.3)
   - validation: Opacity test with pyspeckit: tau up to ~0.3; correction changes Nu by 28.3%, <=10 K Trot; synthetic spectra reproduce data  
  > "We find that these modeled values of $N_u$ differ from the values we measure with the optically thin approximation by 28.3%" (2.3.1)
4. **Derive H2 column density, density profiles, mass, radius**: N(H2) from dust continuum with Tdust=Trot; spherical symmetry; Rcore at min or 150 K; mass summed within Rcore  
  > "Source radii were measured as the radius at which the azimuthally average temperature reached its minimum value or 150 K ($R_{{core}}$)." (3 Results)
   - parameter: D=8.34 kpc, mu=2.8, kappa=0.008 cm2/g  
  > "mean molecular weight $\mu=2.8$ (cite: Kauffman+2008)" (3.2.2)
   - assumption: Tdust=Trot; gas-to-dust 100; optically thin dust (tau<0.07)  
  > "we first set the dust temperature $T_{dust}=T_{rot}$" (3.2.2)
   - fitting: Single power law for density; single and broken power laws for temperature  
  > "we fit broken power-law profiles to the data" (3.2.1)
   - validation: _not stated_
5. **Abundance maps and comparison**: X(CH3OH)=Ntot/N(H2); Sgr B2(S) HII region omitted; compare with disk hot cores with masses rescaled  
  > "we create methanol abundance (X(CH$_3$OH)) maps by taking the ratio $N_{tot}$/$N(H_2)$" (3.3)
   - fitting: _not stated_
   - validation: _not stated_

## Software

- **CASA** 5.6.0: tclean imaging  
  > "using `tclean`(CASA version 5.6.0, (cite: McMullin2007))" (2.1)
- **STATCONT** : continuum level and sigma  
  > "we use the `--continuum` mode of STATCONT" (2.1)
- **uvcombine** : feathering with BGPS  
  > "we use `uvcombine` to feather" (2.1)
- **astroquery** : JPL/Splatalogue line search  
  > "we use `astroquery` to search the JPL Millimeter, Submillimeter, and Microwave Spectral Line Catalog" (2.2.1)
- **astropy** : Gaussian fitting and bootstrap  
  > "using the `astropy.stats.bootstrap` package" (2.3)
- **pyspeckit** : LTE opacity and model spectra  
  > "the `lte_molecule` module of `pyspeckit` to model the optical depth" (2.3.1)

## Numeric results

| quantity | value | uncertainty | units | step | quote |
|---|---|---|---|---|---|
| Peak Trot range of cores | 252-662 | DS9 252±39; Sgr B2(S) 662±191 | K | 3 | / DS9 / $252\pm39$ / $2.42\pm0.14$ / |
| Core masses range | 203-4842 | DS9 ±16; Sgr B2(S) ±787 | Msun | 4 | We find that the cores span a range of masses (203-4842 M$_\odot$) and radii (3587–9436 AU). |
| Mean density power-law index p (DS) | 1.66 | 0.01 | dimensionless | 4 | shallower ($p={1.66} \pm 0.01$) density profiles than the CORE catalogue ($p=1.85 \pm 0.09$ |
| Total mass of DS1-DS5 | 4128 | not stated | Msun | 4 | The newly discovered hot cores contain a total molecular gas mass of 4128 M$_\odot$ |
| Sgr B2(S) peak X(CH3OH) | 11.31e-7 | 1.76e-7 | dimensionless | 5 | $11.31\pm1.76$ |

## Qualitative findings

- CH3OH abundance rises with temperature but levels off above ~250 K, unlike chemical model predictions  
  > "we observe constant peak abundances at higher temperatures ($T\gtrsim250$ K)" (abstract)

## Claim tuples

- H: Are DS hot cores structurally like Galactic disk hot cores? | E: Radial temperature/density power laws, radii and masses compared with CORE | R: Similar radii and temperature indices; shallower density index (1.66 vs 1.85) | F: Structurally similar but denser, possibly due to the CMZ higher star formation threshold | **partially**
- H: Is Sgr B2(S)+DS a younger, comparably massive counterpart to N and M? | E: Summed core masses; maser and UCHII census | R: Combined 8970 Msun; Sgr B2(S) only 54% of mass | F: Region may be a younger, comparably massive sibling | **partially**
- H: Does CH3OH abundance follow chemical model predictions with temperature? | E: X vs Trot for DS and comparison cores | R: Qualitative agreement, but constant abundance above ~250 K | F: Possible unaccounted methanol survival or formation mechanisms | **partially**

## Reasoning

- Why this data: _not stated_
- Why this method: _not stated_
- Alternative: Single power-law temperature profile rejected as poor fit for r<~4000 AU; broken power law used  
  > "these profiles are a poor fit to the data for $r \lesssim 4000$ AU" (3.2.1)
- How they decided it was enough: _not stated_
- Limitation (authors): Single-temperature, single-velocity assumption and non-LTE excitation of some lines (5-4) not explored  
  > "We do not explore the apparent non-LTE excitation of these lines in this work." (2.3)
- Limitation (authors): Dust temperature not well known and assumed equal to Trot  
  > "While the dust temperatures are not well known at these scales" (3.2.2)
- Caveat (inferred, ours): Tdust=Trot and LTE at ~1000 AU scales may bias masses and abundances
- Caveat (inferred, ours): Mass and abundance dependence on adopted kappa and continuum free-free contamination
- Caveat (inferred, ours): Small, heterogeneous comparison sample with different methods
- Caveat (inferred, ours): Radii uncertainty equals beam radius, comparable to radii

## Reproducibility

- Data public (paper): ALMA archival project 2017.1.00114.S (PI Ginsburg)  
  > "This paper makes use of the following ALMA data: ADS/JAO.ALMA#2017.1.00114.S." (Acknowledgements)
- Products in archive: _not stated_
- Missing: Calibration details
- Missing: STATCONT/line-free channel settings
- Missing: Fitting code for power laws
- Missing: Exact line list per pixel selection and Q_rot source
- Data volume (inferred): Large: 10 fields x 4 spws x 1.875 GHz at 488 kHz; hundreds of GB to ~1 TB
- Score (inferred): 3/5, Public data and a clear LTE rotational diagram recipe, but calibration, masking and fitting details are missing.
- Rediscovery candidate: no, Data are public and results numeric, but the recipe lacks imaging masks, line-free channel and fitting details.

## Links

- Method: (cite: SanchezMonge2018) (STATCONT continuum determination)
- Method: (cite: Goldsmith&Langer1999) (rotational diagram and opacity correction)
- Method: (cite: Gieser+2021) (power-law profile approach)
- Companion: (cite: Ginsburg2018) (identified the 3 mm continuum source arc in DS)
- Companion: (cite: Budaiev+2024) (companion Sgr B2(N) YSO study)
- Related: CORE survey
- Related: Bolocam Galactic Plane Survey

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
 "numeric_results": 5,
 "numeric_problems": 0,
 "fill": {
  "facts": 80,
  "stated": 47,
  "rate": 0.588
 },
 "evidence_ok": true
}
```
