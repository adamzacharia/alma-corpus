# Chemical segregation in hot cores with disk candidates. An investigation with ALMA

`2017A&A...603A.133A` | Astronomy and Astrophysics 2017 | first author: Allen, V. | arXiv: 1705.06346 | DOI: 10.1051/0004-6361/201629118

Card schema 1.0 | model claude-sonnet-5-5 | depth full | type archival_reuse

## Science

- Fields: star_formation, astrochemistry
- Question: What are the chemical composition and spatial distribution of molecules in the hot cores G35.20-0.74N (four continuum peaks) and G35.03+0.35, and what does chemical segregation imply about the disk/multiple-protostar nature of the sources?  
  > "We investigate the chemical make up of several hot molecular cores to determine physical and chemical structure." (abstract)
- Target **G35.20-0.74N (peaks A, B1, B2, B3)**: coordinates A: 18:58:12.948 +01:40:37.419 (peaks B1-B3 listed in Table 1)  
  > "The distance to both sources has been estimated from parallax measurements to be 2.2 kpc for G35.20 (cite: Zhang2009) and 2.32 kpc for G35.03 (cite: parallax)." (Introduction); "| G35.20 A | 18:58:12.948 | +01:40:37.419 |" (Table 1); z/distance 2.2 kpc  
  > "The distance to both sources has been estimated from parallax measurements to be 2.2 kpc for G35.20 (cite: Zhang2009) and 2.32 kpc for G35.03 (cite: parallax)." (Introduction); "| G35.20 A | 18:58:12.948 | +01:40:37.419 |" (Table 1); distance from parallax (Zhang et al. 2009)  
  > "The distance to both sources has been estimated from parallax measurements to be 2.2 kpc for G35.20 (cite: Zhang2009) and 2.32 kpc for G35.03 (cite: parallax)." (Introduction); "| G35.20 A | 18:58:12.948 | +01:40:37.419 |" (Table 1)
- Target **G35.03+0.35 (peak A)**: coordinates 18:54:00.645 +02:01:19.235  
  > "The distance to both sources has been estimated from parallax measurements to be 2.2 kpc for G35.20 (cite: Zhang2009) and 2.32 kpc for G35.03 (cite: parallax)." (Introduction); "| G35.03 A | 18:54:00.645 | +02:01:19.235 |" (Table 1); z/distance 2.32 kpc  
  > "The distance to both sources has been estimated from parallax measurements to be 2.2 kpc for G35.20 (cite: Zhang2009) and 2.32 kpc for G35.03 (cite: parallax)." (Introduction); "| G35.03 A | 18:54:00.645 | +02:01:19.235 |" (Table 1); distance from parallax (Wu et al. 2014)  
  > "The distance to both sources has been estimated from parallax measurements to be 2.2 kpc for G35.20 (cite: Zhang2009) and 2.32 kpc for G35.03 (cite: parallax)." (Introduction); "| G35.03 A | 18:54:00.645 | +02:01:19.235 |" (Table 1)

## Data provenance

- ALMA projects: 2011.0.00275.S
- bands: Band 7 (350 GHz)  
  > "The sources were observed in Band 7 (350 GHz) with the 16 antennas of the array in the extended configuration" (2.1 Observations)
- frequencies and spectral setup: 4 spectral windows of 1875 MHz, 3840 channels each, ~0.4 km/s resolution; 334.97-338.72 GHz and 346.89-350.72 GHz  
  > "The digital correlator was configured in four spectral windows (with dual polarization) of 1875 MHz and 3840 channels each, providing a resolution of $\sim$0.4 km/s." (2.1 Observations)
- continuum bandwidth: _not stated_
- arrays: 16 antennas, extended configuration  
  > "with the 16 antennas of the array in the extended configuration" (2.1 Observations)
- configurations: _not stated_
- baselines: 36-400 m, sensitive to structures 0.4"-2"  
  > "baselines in the range 36-400 m) providing sensitivity to structures 0.4” - 2”" (2.1 Observations)
- angular resolution: _not stated_
- max recoverable scale: _not stated_
- sensitivity: continuum rms 1.8 mJy/beam (G35.20), 3 mJy/beam (G35.03)  
  > "The rms noise of the continuum maps are 1.8 mJy/beam for G35.20 and 3 mJy/beam for G35.03." (2.1 Observations)
- time on source: _not stated_
- observing dates: May-June 2012 (Cycle 0)  
  > "observed with ALMA in Cycle 0 between May and June 2012" (2.1 Observations)
- pi or archival as stated: _not stated_
- Line: CH3CN 19_K-18_K (K=0-8) (~349.4 GHz (K ladder, 349.45 GHz for K=0/1))
- Line: HNCO 16(1,16)-15(1,15) (350333 MHz)
- Line: NH2CHO 16(2,15)-15(2,14) (336136 MHz)
- External data: Molecular line catalogs (CDMS, JPL) used for identification  
  > "primarily using the CDMS (Cologne Database for Molecular Spectroscopy; (cite: CDMS)) database and JPL (Jet Propulsion Laboratory; (cite: JPL)) database" (2.2 Line Identification Process) [from (cite: CDMS), (cite: JPL)]
- External data: Collisional rate coefficients from LAMDA for RADEX  
  > "uses collisional rate coefficients from the LAMDA database (cite: Lamda)" (3.3 Kinetic Gas Temperatures) [from (cite: Lamda)]
- External data: H2 column densities and masses from 870 um continuum, and 30% flux recovery vs SCUBA  
  > "(cite: Alvaro2014) determined that in our observations we recover 30$\%$ of the flux compared to SCUBA 850 $\mu$m observations." (3.4 Molecular column densities) [from (cite: Alvaro2014)]

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

- task: CASA used for spectrum extraction at the central pixel of continuum peaks, channel maps and moment maps  
  > "Spectra were extracted from the central pixel of the continuum peak in core A and the three continuum peaks in core B (B1, B2, B3)" (2.2 Line Identification Process)
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
- final beam: _not stated_
- final rms: _not stated_

### Inherited from earlier work

- Observation and data reduction details  
  > "For full details see (cite: Alvaro2014) and (cite: Beltran2014)." (2.1 Observations) [from (cite: Alvaro2014), (cite: Beltran2014)]
- H2 column density and mass from 870 um continuum with dust opacity 1.75 cm2/g, gas-to-dust 100  
  > "These average kinetic temperatures were used in calculating the mass of the core and H$_2$ column density based on the 870 $\mu$m continuum flux as in (cite: Alvaro2014)." (3.3 Kinetic Gas Temperatures) [from (cite: Alvaro2014)]

### Not stated but needed to reproduce (our reading)

- Calibration pipeline/CASA version, calibrators and imaging parameters (weighting, robust, cleaning, beam) - only deferred to earlier papers
- Beam size and per-channel rms of the line cubes
- Brightness-temperature conversion/beam used for T_peak
- XCLASS version and fit settings (iteration algorithm, number of iterations)
- Line-free channels/continuum subtraction method
- How dust attenuation/ continuum level was handled in XCLASS
- Cassis rotation diagram settings and opacity treatment

## Analysis recipe

1. **Extract spectra at continuum peaks**: Spectra extracted from the central pixel of each continuum peak in CASA  
  > "Spectra were extracted from the central pixel of the continuum peak in core A and the three continuum peaks in core B (B1, B2, B3)" (2.2 Line Identification Process)
   - software: CASA
   - fitting: _not stated_
   - validation: _not stated_
2. **Identify lines and measure line parameters**: Gaussian fits to lines with Cassis; identification by catalogs, Einstein A, E_up, velocity tolerance, in stages  
  > "Line parameters were measured by fitting a Gaussian profile to the emission line with the Cassis "Line Spectrum" tool." (2.2 Line Identification Process)
   - software: Cassis, CDMS, JPL
   - parameter: Candidate selection: Einstein A >~1e-7 s-1, E_up generally <500 K, within 2 km/s; detection threshold 3 sigma (~0.5 K)  
  > "limited to a minimum of about 10$^{-7}$ s$^{-1}$, or with a upper level energy (E$_{up}$) within the expected range, generally less than 500 K" (2.2 Line Identification Process)
   - fitting: Gaussian profile fits; blended lines fit with extra Gaussians  
  > "In some cases, partially blended lines were fit together with one or more extra Gaussians for a more accurate measurement, though the errors were then larger." (2.2 Line Identification Process)
   - validation: Simultaneous XCLASS fits of all species; residuals 5-25%  
  > "The residuals between the fitted lines and the observed spectra are between 5 and 25$\%$, validating the XCLASS fits and our line identifications." (2.2 Line Identification Process)
3. **Map species distributions**: Moment 0/1/2 and channel maps of unblended lines for 20 species  
  > "Channel maps were made in CASA for 20 different species for interesting isolated lines with a range of upper energy levels" (2.3 Image analysis)
   - software: CASA
   - fitting: _not stated_
   - validation: Similar spatial distribution/velocity profiles of lines with similar E_up taken as same species  
  > "Similar spatial distributions and velocity profiles of transitions with similar upper energy levels are consistent with these being the same species." (2.3 Image analysis)
4. **Derive kinetic temperature**: RADEX modelling of CH3CN K-ladder line ratios over T_kin 100-500 K and n(H2) 1e6-1e9 cm-3  
  > "The line ratios were modeled for kinetic temperatures between 100 and 500 K and for H$_2$ densities between 10$^6$ and 10$^9$ cm$^{-3}$." (3.3 Kinetic Gas Temperatures)
   - software: RADEX
   - parameter: CH3CN column density 5e15 cm-2  
  > "with a column density of 5 $\times$ 10$^{15}$ cm$^{-2}$" (3.3 Kinetic Gas Temperatures)
   - assumption: Isothermal, homogeneous medium, escape probability  
  > "a radiative transfer code that assumes an isothermal and homogeneous medium, treats optical depth using a local escape probability" (3.3 Kinetic Gas Temperatures)
   - fitting: Errors from Gaussian-fit errors on line peaks  
  > "Errors were calculated from the measured error on the Gaussian fit of each spectral line." (3.3 Kinetic Gas Temperatures)
   - validation: _not stated_
5. **Derive H2 column density and core mass**: 870 um continuum flux with T_kin, as in Sanchez-Monge 2014  
  > "Using a dust opacity of 1.75 cm$^{2}$ g$^{-1}$ and a gas-to-dust ratio of 100, Core A has mass of 13.0 M$_{\ensuremath{\odot}}$" (3.3 Kinetic Gas Temperatures)
   - assumption: Dust opacity 1.75 cm2/g, gas-to-dust 100  
  > "Using a dust opacity of 1.75 cm$^{2}$ g$^{-1}$ and a gas-to-dust ratio of 100" (3.3 Kinetic Gas Temperatures)
   - fitting: _not stated_
   - validation: _not stated_
6. **Fit LTE models for column densities**: XCLASS chi2 minimization over source size, T_ex, N, v_LSR, linewidth; INS error estimator; single-line species at fixed size and T=50/100 K  
  > "The fitting process compares the synthetic spectrum to the observed one, and minimizes the $\chi^2$ by changing the five parameters indicated above." (3.4 Molecular column densities)
   - software: XCLASS
   - parameter: COMs: size 0.1-1.5", Tex 50-500 K, N 1e13-1e19 cm-2; extended (H2CS, SO2): size 1.0-3.5", Tex 20-200 K, N 1e12-1e16  
  > "the source size was varied from 0.1-1.5$''$ to be comparable with the observed emission extent and the T$_{ex}$ was allowed to vary from 50-500 K." (3.4 Molecular column densities)
   - assumption: LTE, isothermal 1D source; isotopologues coupled with fixed/varied ratios (12C/13C=50 for HC3N)  
  > "This program models the data by solving the radiative transfer equation for an isothermal object in one dimension, taking into account source size and dust attenuation." (2.2 Line Identification Process)
   - fitting: chi2 minimization; errors via Interval Nested Sampling in XCLASS  
  > "The errors were calculated using the Interval Nested Sampling (INS) error estimator algorithm in XCLASS." (XCLASS fit errors)
   - validation: Checked against Cassis rotation diagrams  
  > "The modeled values for column density and excitation temperature were checked against rotational diagrams from Cassis and found to be in agreement." (3.4 Molecular column densities)
7. **Deuterium fractionation**: Cassis rotation diagrams with opacity function for CH2DCN, CH2DOH, CH3CHDCN and parent species  
  > "We determined the deuterium fractionation of the other three, CH$_2$DCN, CH$_2$DOH, and CH$_3$CHDCN, using rotation diagrams in Cassis for consistency" (4.4 Deuteration)
   - software: Cassis
   - fitting: Rotation diagram fits  
  > "rotational diagrams were created using Cassis for all peaks in G35.20." (Species Analyzed with Cassis)
   - validation: CH3CN D/H from XCLASS falls within Cassis ranges  
  > "which fall within the ranges determined using Cassis." (4.4 Deuteration)

## Software

- **CASA** : Spectrum extraction, channel and moment maps  
  > "Channel maps were made in CASA for 20 different species" (2.3 Image analysis)
- **Cassis** : Gaussian line fitting, rotation diagrams, D/H  
  > "Line parameters (listed in Appendix B) were determined using Gaussian profiles fit to spectral lines from each continuum peak using Cassis" (2.2 Line Identification Process)
- **XCLASS** : LTE spectral modelling and column densities  
  > "To estimate the column densities of each detected species, we used the XCLASS software." (3.4 Molecular column densities)
- **RADEX** : Kinetic temperature from CH3CN ratios  
  > "we use RADEX (cite: Radex), a radiative transfer code" (3.3 Kinetic Gas Temperatures)

## Numeric results

| quantity | value | uncertainty | units | step | quote |
|---|---|---|---|---|---|
| Average T_kin G35.20 A | 285 | range 150-450 K | K | 4 | G35.20 A is significantly hotter than these with an average T$_{kin}$ of 285 K and a range from 150-450 K. |
| Average T_kin B2 | 120 | range 90-170 K | K | 4 | We find that B2 is the coolest region with an average T$_{kin}$ of 120 K and a range from 90-170 K. |
| Average T_kin B3 | 300 | range 175-490 K | K | 4 | B3 is consistently the hottest, ranging from 175-490 K with an average T$_{kin}$ of 300 K. |
| Core mass G35.20 A | 13.0 | not stated | Msun | 5 | Core A has mass of 13.0 M$_{\ensuremath{\odot}}$, B1 3.8 M$_{\ensuremath{\odot}}$, B2 2.2 M$_{\ensuremath{\odot}}$, B3 1.4 M$_{\ensuremath{\odot}}$, and G35.03 has a mass of 4.4 M$_{\ensuremath{\odot}}$. |
| Number of transitions identified | 431 | not stated | dimensionless | 2 | A total of 431 different transitions were identified in 52 different catalog entries |
| CH2DCN/CH3CN D/H (Cassis) at A, B1, B3 | 6, 3, 12 | ±5; +3/-2.7; +9/-5 | % | 7 | / A / 6$\pm{5}$ / 4$^{+4}_{-2}$ / 13$^{+13}_{-10}$ / |
| X-CHO/X-CH3 ratio at B2 | 1.6 | not stated | dimensionless | 6 | we also see a higher ratio of X-CHO/X-CH$_3$ at the coolest peak, G35.20 B2, where the ratio is 1.6 |
| N(HNCO)/N(NH2CHO) | 2-8 (HNCO at 50 K); 1-10 (100 K) | not stated | dimensionless | 6 | Our modeled abundance values show N(HNCO)/N(NH$_2$CHO) is between 2 and 8 for HNCO at 50 K and between 1 and 10 for HNCO modeled at 100 K. |
| HNCO-NH2CHO peak separation in G35.20 B | 0.15 (~300 AU) | not stated | arcsec | 3 | their emission peaks are only 0.15$''$ (or $\sim$300 AU) apart in G35.20 B |

## Qualitative findings

- Nitrogen-bearing (especially CN) species are only observed toward A and southern B (B3), segregated from O-bearing species on <1000 AU scales  
  > "The linear scale for this separation of chemistry is less than 1000 AU, which is the smallest observed chemical separation in a star-forming region to date." (4.2 Chemical segregation in G35.20)
- No deuterated species detected in G35.03  
  > "No deuterated species are detected in G35.03, but similar molecular abundances to G35.20 were found in other species." (abstract)

## Claim tuples

- H: Do the continuum peaks in G35.20 have different chemistry? | E: Line survey and LTE modelling at four peaks | R: B1/B2 lack N-bearing species; A and B3 rich in N-bearing species | F: Chemical segregation on <1000 AU suggests multiple protostars or a disrupted/fragmenting disk | **supported**
- H: Is formamide formed from HNCO? | E: Compare spatial distributions and velocities of HNCO and NH2CHO | R: Peaks separated by <0.15" and velocities differ by 0.5-1 km/s | F: Strong chemical link | **supported**
- H: Does deuteration differ across sources, indicating age? | E: D/H from rotation diagrams | R: CH3CN D/H ~8% (A) and 13% (B3); none in G35.03 | F: B3 is a much younger region than G35.03 | **partially**

## Reasoning

- Why this data: _not stated_
- Why this method: RADEX used to estimate temperature without assuming LTE and check LTE  
  > "To estimate the kinetic temperature (T$_{kin}$) for each region without assuming LTE" (3.3 Kinetic Gas Temperatures)
- Alternative: Three scenarios for B chemical differentiation: fragmenting disk, multiple sources, disrupted disk  
  > "There are three plausible scenarios to explain this chemical differentiation." (4.2 Chemical segregation in G35.20)
- How they decided it was enough: _not stated_
- Limitation (authors): Mass and column densities are lower limits since only ~30% of flux recovered; H2 from dust may not trace warm gas  
  > "These mass and column density estimates are lower limits" (3.4 Molecular column densities)
- Limitation (authors): Single-temperature XCLASS model inadequate given temperature gradients  
  > "a single temperature model is inadequate to fit lines with very different excitation energy" (4.1 Overall chemical composition)
- Caveat (inferred, ours): Single-pixel spectra at ~0.4" resolution; source-size fits degenerate with column density
- Caveat (inferred, ours): Absorption from resolved-out emission may bias B1-B3 line fluxes
- Caveat (inferred, ours): Single-line species depend on assumed fixed Tex and size
- Caveat (inferred, ours): D/H uncertainties are large and overlap between sources

## Reproducibility

- Data public (paper): ALMA Cycle 0 data acknowledged with project code; archive data  
  > "This paper makes use of the following ALMA data: ADS/JAO.ALMA 2011.0.00275.S." (Acknowledgements)
- Products in archive: _not stated_
- Missing: Calibration/imaging parameters (in Sanchez-Monge 2014, Beltran 2014)
- Missing: XCLASS fit settings and starting values
- Missing: Beam sizes and cube rms
- Missing: Exact line lists beyond tables
- Data volume (inferred): ~50-100 GB (Cycle 0 Band 7, four 1.9 GHz windows, two fields)
- Score (inferred): 6/5, Public data and detailed tables, but calibration/imaging deferred to prior papers and XCLASS settings are incomplete.
- Rediscovery candidate: no, Imaging and calibration recipe not given here; analysis is heavily manual line identification.

## Links

- Method: (cite: XCLASS) (XCLASS software)
- Method: (cite: Radex) (RADEX code)
- Companion: (cite: Alvaro2014) (Earlier ALMA analysis of G35.20 with the same data)
- Companion: (cite: Beltran2014) (Earlier analysis of G35.03 with the same data)
- Related: Red MSX Source survey

## Checks

```json
{
 "quotes": 75,
 "quotes_ok": 75,
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
  "facts": 87,
  "stated": 51,
  "rate": 0.586
 },
 "evidence_ok": true
}
```
