# ALMA Survey of Orion Planck Galactic Cold Clumps (ALMASOP). I. Detection of New Hot Corinos with the ACA

`2020ApJ...898..107H` | The Astrophysical Journal 2020 | first author: Hsu, Shih-Ying | arXiv: 2006.15850 | DOI: 10.3847/1538-4357/ab9f3a

Card schema 1.0 | model claude-sonnet-5-5 | depth full | type observational_alma_primary

## Science

- Fields: star_formation, astrochemistry
- Question: Which Planck Galactic Cold Clump cores in Orion harbor hot corinos, and what are their COM, deuteration and carbon-chain chemical properties, using ACA 1.3 mm line data?  
  > "We report the detection of four new hot corino sources, G211.47-19.27S, G208.68-19.20N1, G210.49-19.79W and G192.12-11.10 from a survey study of Planck Galactic Cold Clumps in the Orion Molecular Cloud Complex" (abstract)
- Target **G211.47-19.27S**: coordinates 05:39:56.097 -07:30:28.403 (J2000)  
  > "G211.47-19.27S | 05:39:56.097 -07:30:28.403" (Table 1); z/distance 415 pc  
  > "G211.47-19.27S | 05:39:56.097 -07:30:28.403" (Table 1); distance from PGCC catalog (Planck 2016)  
  > "G211.47-19.27S | 05:39:56.097 -07:30:28.403" (Table 1)
- Target **G208.68-19.20N1**: coordinates 05:35:23.486 -05:01:31.583  
  > "05:35:23.486 -05:01:31.583" (Table 1); z/distance 415 pc  
  > "05:35:23.486 -05:01:31.583" (Table 1); distance from PGCC catalog (Planck 2016)  
  > "05:35:23.486 -05:01:31.583" (Table 1)
- Target **G210.49-19.79W**: coordinates 05:36:18.860 -06:45:28.035  
  > "05:36:18.860 -06:45:28.035" (Table 1); z/distance 415 pc  
  > "05:36:18.860 -06:45:28.035" (Table 1); distance from PGCC catalog (Planck 2016)  
  > "05:36:18.860 -06:45:28.035" (Table 1)
- Target **G192.12-11.10**: coordinates 05:32:19.540 +12:49:40.190  
  > "05:32:19.540 +12:49:40.190" (Table 1); z/distance 400 pc  
  > "05:32:19.540 +12:49:40.190" (Table 1); distance from PGCC catalog (Planck 2016)  
  > "05:32:19.540 +12:49:40.190" (Table 1)

## Data provenance

- ALMA projects: 2018.1.00302.S
- bands: _not stated_
- frequencies and spectral setup: Four SPWs at 216.6, 218.9, 231.0, 233.0 GHz; 1875 MHz each; ~1.129 MHz (~1.5 km/s) resolution  
  > "Four spectral windows, centered at 216.6, 218.9, 231.0 and 233.0 GHz with an uniform bandwidth of 1875 MHz ($\sim$2500 km s$^{-1}$) and a resolution of $\sim$1.129 MHz" (Observations)
- continuum bandwidth: _not stated_
- arrays: ACA 7m, twelve antennas  
  > "The observations were carried out with the ACA, which is an interferometer composed of twelve 7-meter antennas." (Observations)
- configurations: _not stated_
- baselines: longest 49 m (~37.7 kλ)  
  > "The longest baseline was 49 m, which was about 37.7 k$\lambda$." (Observations)
- angular resolution: HPBW ~5.6 arcsec  
  > "The HPBW of the synthesized beam was $\sim$ 5.6${''}$" (Observations)
- max recoverable scale: _not stated_
- sensitivity: _not stated_
- time on source: 210 s (G211), 500 s (G208), 300 s (G210), 480 s (G192)  
  > "G211.47-19.27S | 05:39:56.097 -07:30:28.403 | 210 sec" (Table 1)
- observing dates: 2018 (Nov), multiple executions  
  > "All the measurements were made in 2018." (Table 1 notes)
- pi or archival as stated: Cycle 6 project PI Tie Liu  
  > "ALMA Cycle 6 project, (#2018.1.00302.S; PI: Tie Liu)" (Observations)
- Line: CH3OH multiple, e.g. 5(1,4)-4(2,3) E (216946 MHz)
- Other facility **JCMT SCUBA-2 / NRO 45m**: 850 um continuum core selection and N2D+ evolutionary stage used to select targets  
  > "On the basis of these surveys, we selected 72 dense and compact 850 $\mu$m continuum cores at early stages" (Introduction)
- External data: Distances to sources from PGCC catalog  
  > "$D$ is the distance to the source adopted from the PGCC catalog" (Results) [from (cite: 2016Planck_PGCC)]
- External data: HOPS protostar classes, Lbol, Tbol  
  > "HOPS 288 | 05:39:55.95 | -07:30:28.0 | 0 | 135.47 | 48.6" (Table 3) [from (cite: 2016Furlan_HOPS_Class)]

## Processing

### Calibration

- pipeline or manual: ALMA pipeline  
  > "The data were calibrated with the Common Astronomy Software Applications package (cite: 2007McMullin_CASA) version 5.4.0-68 and its pipeline version 42030M (Pipeline-CASA54-P1-B)." (Observations)
- casa version: 5.4.0-68  
  > "version 5.4.0-68 and its pipeline version 42030M" (Observations)
- pipeline version: _not stated_
- archive products used as is: _not stated_
- flux calibrator: _not stated_
- flux scale uncertainty: _not stated_
- self calibration: _not stated_

### Imaging

- task: tclean via pipeline  
  > "the images were processed through tclean with auto-masking and the robust parameter of the Briggs weighting set to 0.5" (Observations)
- deconvolver: _not stated_
- weighting robust: Briggs robust = 0.5  
  > "robust parameter of the Briggs weighting set to 0.5" (Observations)
- uv taper: _not stated_
- cell size: _not stated_
- image size: _not stated_
- masking: auto-masking: sidelobethreshold=1.25, noisethreshold=5.0, negativethreshold=0.0  
  > "sidelobethreshold=1.25, noisethreshold=5.0 and negativethreshold=0.0" (Observations)
- multiscale scales: _not stated_
- continuum subtraction: _not stated_
- line free channels: _not stated_
- primary beam correction: _not stated_
- array combination: _not stated_
- smoothing: _not stated_
- final beam: _not stated_
- final rms: _not stated_

### Inherited from earlier work

- Continuum column density and mass formulae modified from Kauffmann et al. 2008  
  > "formulae modified from Eq. A.26 and A.30 in (cite: 2008Kauffmann_CONTFormula) for optically thin continuum emission" (Results) [from (cite: 2008Kauffmann_CONTFormula)]
- Dust opacity law kappa=0.1(nu/1THz)^beta  
  > "$\kappa_\nu=0.1(\nu/1\,\mathrm{THz})^\beta\,\mathrm{cm^2\,g^{-1}}$ where $\beta$ is the the dust opacity index (cite: 1990Beckwith_DustOpacity)" (Results) [from (cite: 1990Beckwith_DustOpacity)]
- Full sample/ALMA observation details deferred  
  > "Information about the ALMA observations over the full sample will be reported in a separate paper (Dutta et al. in preparation)." (Introduction) [from Dutta et al. in preparation]

### Not stated but needed to reproduce (our reading)

- Dust temperatures actually adopted as primary (50/100/150 K grid only)
- Spectrum extraction aperture and line-free channels/continuum subtraction method
- XCLASS/MAGIX parameter ranges, optimizer algorithm and priors
- Flux calibration uncertainty
- How rms and dynamic range limits were handled
- Line identification criteria beyond Splatalogue search

## Analysis recipe

1. **Continuum fitting and mass/column density**: 2D Gaussian fit in CASA to continuum; optically thin N(H2), M, R formulae  
  > "We applied a 2D Gaussian fit in CASA to the continuum" (Results)
   - software: CASA
   - parameter: Td = 50, 100, 150 K  
  > "estimated with a range of dust temperatures at 50K, 100K, and 150K" (Results)
   - assumption: beta=1.70, kappa(1.3mm)=0.0083 cm2/g, mu_H2=2.8  
  > "The indices $\beta$ were assumed to be 1.70" (Results)
   - fitting: _not stated_
   - validation: _not stated_
2. **Extract spectra and fit line Gaussians**: Spectra at continuum peak; Gaussian fits to lines above 3 sigma; identification via Splatalogue (JPL, CDMS)  
  > "We extracted the spectra at the continuum peak in the four spectral datacubes for each of the 72 sources" (Results)
   - software: Splatalogue
   - fitting: _not stated_
   - validation: _not stated_
3. **LTE modelling of molecular emission**: myXCLASS LTE synthetic spectra optimized with MAGIX; each molecule individually then global fit  
  > "We executed MAGIX for each molecule individually to find their correspondingly best-fit." (Results)
   - software: XCLASS, MAGIX
   - parameter: component size fixed to deconvolved continuum size (C18O 8 arcsec); Trot fixed to 100 K for single-line species  
  > "we fixed the component sizes ($\theta_C$) to be the same as the deconvolved dust continuum" (Results)
   - assumption: LTE, isothermal, one component per molecule  
  > "each (gaseous) component of a molecule is assumed to be in its individual local-thermodynamic equilibrium (LTE)" (Results)
   - fitting: MAGIX optimization; uncertainties from MAGIX error estimation  
  > "The parameter uncertainties estimated by the error estimation function of MAGIX are also presented." (Results)
   - validation: Methanol population diagrams consistent with MAGIX  
  > "the derived column densities and rotational temperatures are all consistent with the estimation of MAGIX" (Results)
4. **Abundances and isotopic/deuteration ratios**: Compute X relative to H2, [COM]/[CH3OH], D/H, 12C/13C, compare with other hot corinos  
  > "Table [18] shows the fractional column density, $X$, of COMs relative to hydrogen." (Discussion)
   - assumption: 12C/13C=70 for 13CH3OH proxy  
  > "assuming $^{12}$C/$^{13}$C ratio is 70" (Table 5 notes)
   - fitting: _not stated_
   - validation: _not stated_

## Software

- **CASA** 5.4.0-68: calibration, tclean imaging, 2D Gaussian fits  
  > "version 5.4.0-68 and its pipeline version 42030M" (Observations)
- **XCLASS** : LTE line synthesis  
  > "Spectra of the molecule candidates were then modeled with the eXtended CASA Line Analysis Software Suite" (Results)
- **MAGIX** : parameter optimization  
  > "optimizes these molecular component parameters within the given ranges through the XCLASS interface" (Results)
- **astropy** : listed in Software section  
  > "astropy (cite: astropy:2013; astropy:2018), CASA (cite: 2007McMullin_CASA), XCLASS (cite: 2017Moller_XCLASS)" (Software)

## Numeric results

| quantity | value | uncertainty | units | step | quote |
|---|---|---|---|---|---|
| CH3OH Trot in G211 | 185 | ±4 | K | 3 | CH$_3$OH / 185$\pm$4 / 8.5E+16 (0.1) |
| CH3OH Trot in G208 | 298 | ±3 | K | 3 | 298$\pm$3 |
| G211 integrated continuum flux | 552 | not stated | mJy | 1 | G211.47-19.27S / 6.07 / 2.22 / 552 / 415 |
| G211 mass (100 K) | 0.39 | not stated | Msun | 1 | 0.82 / 0.39 / 0.25 |
| [CH2DOH]/[CH3OH] in G211 | 0.27 | not stated | dimensionless | 4 | the D/H ratio of methanol ([CH$_2$DOH]/[CH$_3$OH]) is 0.27 |
| [CH3OH]/[13CH3OH] in G211 | ~10 (9.2 in table) | not stated | dimensionless | 4 | the $^{12}$C/$^{13}$C ratio of methanol ([CH$_3$OH]/[$^{13}$CH$_3$OH]) is $\sim$ 10 |
| NH2CHO column density in G211 | 3.6E+14 | 0.1 dex | cm^-2 | 3 | NH$_2$CHO / 295$\pm$6 / 3.6E+14 (0.1)$^\dagger$ |
| [D2CO]/[H2CO] G211, G208, G210, G192 | 0.039, 0.091, 0.089, 0.112 | not stated | dimensionless | 4 | The [D$_2$CO]/[H$_2$CO]=0.039, 0.091, 0.089 and 0.112 for G211, G208, G210 and G192, respectively. |
| Hot corino fraction | ~8 | not stated | percent | 0 | we have identified 4 hot corino sources, a fraction of $\sim$ 8$\%$ |

## Qualitative findings

- COMs are unresolved and compact while hydrocarbons and carbon chains are resolved, tracing cooler envelopes  
  > "The hydrocarbons and the carbon-chain molecules are resolved while saturated COMs are not" (Results)

## Claim tuples

- H: Do four cores in the ALMASOP sample host hot corinos? | E: Scan ACA spectra of 72 cores for rich lines incl. multiple CH3OH lines with Eu>100 K; model with XCLASS | R: Four sources show compact CH3OH with Trot >165 K | F: G211, G208, G210, G192 are hot corinos | **supported**
- H: Are COM ratios in these sources similar to other hot corinos? | E: Compare [COM]/[CH3OH] with IRAS 16293B, B335, HH-212 | R: G211 and G208 ratios an order of magnitude higher, but comparable using 13CH3OH proxy | F: Differences possibly due to beam dilution and methanol opacity | **partially**

## Reasoning

- Why this data: _not stated_
- Why this method: Optically thin LTE modelling with component size set to continuum size  
  > "we fixed the component sizes ($\theta_C$) to be the same as the deconvolved dust continuum" (Results)
- How they decided it was enough: _not stated_
- Limitation (authors): Resolution insufficient; column densities may be underestimated by beam dilution and opacity  
  > "The estimated column densities could be affected by beam dilution since the COM emission is not resolved." (Conclusions)
- Caveat (inferred, ours): LTE single-size assumption and unresolved emission make abundance ratios uncertain
- Caveat (inferred, ours): Only 7m data; 8% rate depends on biased sample
- Caveat (inferred, ours): Line-blending in line-rich sources

## Reproducibility

- Data public (paper): ALMA data cited by project code; public status not explicitly stated  
  > "This paper makes use of the following ALMA data: ADS/JAO.ALMA#2018.1.00302.S." (Acknowledgments)
- Products in archive: _not stated_
- Missing: XCLASS/MAGIX parameter bounds and fitting settings
- Missing: Spectrum extraction details
- Missing: Full sample paper (Dutta et al.)
- Data volume (inferred): ~tens of GB (ACA, 4 fields, 4 SPWs)
- Score (inferred): 3/5, Pipeline settings and tool names given, but fitting ranges and extraction details missing
- Rediscovery candidate: no, XCLASS fitting setup incompletely specified.

## Links

- Method: (cite: 2017Moller_XCLASS) (XCLASS LTE modelling)
- Method: (cite: 2008Kauffmann_CONTFormula) (continuum mass formulae)
- Companion: Dutta et al. in preparation (full ALMASOP sample description)
- Related: ALMASOP
- Related: SCOPE
- Related: HOPS
- Related: CALYPSO
- Related: VANDAM

## Checks

```json
{
 "quotes": 64,
 "quotes_ok": 64,
 "quote_pass_rate": 1.0,
 "quotes_too_long": 0,
 "unsupported_facts": 0,
 "project_codes": 1,
 "codes_not_in_text": [],
 "codes_not_in_obscore": [],
 "obscore_codes_not_in_card": [],
 "codes_printed_but_missing": [],
 "numeric_results": 9,
 "numeric_problems": 0,
 "fill": {
  "facts": 81,
  "stated": 50,
  "rate": 0.617
 },
 "evidence_ok": true
}
```
