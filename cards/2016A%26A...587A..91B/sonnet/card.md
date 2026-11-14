# Exploring molecular complexity with ALMA (EMoCA): Deuterated complex organic molecules in Sagittarius B2(N2)

`2016A&A...587A..91B` | Astronomy and Astrophysics 2016 | first author: Belloche, A. | arXiv: 1511.05721 | DOI: 10.1051/0004-6361/201527268

Card schema 1.0 | model claude-sonnet-5-5 | depth full | type observational_alma_primary

## Science

- Fields: star_formation, astrochemistry, milky_way_ism
- Question: Which deuterated complex organic molecules are detectable toward the hot core Sgr B2(N2), what are their deuteration levels, and how do they compare with astrochemical models and Orion KL?  
  > "Our goal is to detect deuterated complex organic molecules toward the high mass star forming region Sagittarius B2 (Sgr B2) and derive their level of deuteration." (abstract)
- Target **Sgr B2(N2)**: coordinates (17h47m19.86s, -28d22'13.4'') J2000  
  > "The analysis toward Sgr B2(N2) was performed at the offset position ($\Delta\alpha$, $\Delta\delta$) = ($-0.1\ensuremath{''}, 2.6\ensuremath{''}$)" (5 Results); "corresponding to $0.2$ pc in projection at a distance of 8.3 kpc (cite: Reid14)" (1 Introduction); z/distance 8.3 kpc  
  > "The analysis toward Sgr B2(N2) was performed at the offset position ($\Delta\alpha$, $\Delta\delta$) = ($-0.1\ensuremath{''}, 2.6\ensuremath{''}$)" (5 Results); "corresponding to $0.2$ pc in projection at a distance of 8.3 kpc (cite: Reid14)" (1 Introduction); distance from Reid et al. 2014  
  > "The analysis toward Sgr B2(N2) was performed at the offset position ($\Delta\alpha$, $\Delta\delta$) = ($-0.1\ensuremath{''}, 2.6\ensuremath{''}$)" (5 Results); "corresponding to $0.2$ pc in projection at a distance of 8.3 kpc (cite: Reid14)" (1 Introduction)

## Data provenance

- ALMA projects: 2011.0.00017.S, 2012.1.00012.S
- bands: _not stated_
- frequencies and spectral setup: 84.1-114.4 GHz, five setups, 4 spectral windows each of 1875 MHz, channel spacing 244.141 kHz smoothed to 488.3 kHz  
  > "Each spectral window has a bandwidth of 1875 MHz and a channel spacing of 244.141 kHz, but the spectra were smoothed to a spectral resolution of 488.3 kHz (1.7 to 1.3 km s$^{-1}$)." (2.1 Observations)
- continuum bandwidth: _not stated_
- arrays: 12 m antennas, 13-38 antennas per observation  
  > "The size (HPBW) of the primary beam of the 12 m antennas varies between $69''$ at 84 GHz and $51''$ at 114 GHz (cite: Remijan15)." (2.1 Observations)
- configurations: _not stated_
- baselines: _not stated_
- angular resolution: ~1.8''  
  > "at the angular resolution of EMoCA ($\sim 1.8\ensuremath{''}$)" (1 Introduction)
- max recoverable scale: _not stated_
- sensitivity: _not stated_
- time on source: _not stated_
- observing dates: Cycle 0 (S1-S4, 2012) and Cycle 1 (S5, 2014-04-05)  
  > "Setups S1 to S4 were observed in Cycle 0 while setup S5 was observed in Cycle 1." (2.1 Observations)
- pi or archival as stated: _not stated_
- Other facility **IRAM 30 m**: Earlier single-dish survey of Sgr B2(N) whose LTE model was the starting point  
  > "We used the input parameters of our LTE model of the IRAM 30 m spectrum of Sgr B2(N) (cite: Belloche13) as a starting point" (3 Radiative transfer modeling)
- External data: Spectroscopic predictions (CDMS/JPL entries and laboratory data) for deuterated and main species  
  > "Predictions for singly-deuterated methyl cyanide were taken from the CDMS catalog (tag 42511, version 2)." (4 Spectroscopic predictions) [from Mueller01; Mueller05; Pickett98]
- External data: LTE parameters of methanol and ethanol from companion paper  
  > "We report in Table [\[t:coldens\]](#t:coldens) the parameters derived in that paper for the main isotopologue based on the analysis of all isotopologues." (5.4 Deuterated methanol CH2DOH) [from (cite: Mueller15c)]
- External data: Model predictions of deuteration (T14, A12)  
  > "The two models considered here follow the evolution of molecular abundances in a collapsing dense core that is heated up by the central protostar once it is formed (cite: Taquet12; Taquet14; Aikawa12)." (6.2 Comparison to predictions of chemical models) [from (cite: Taquet14); (cite: Aikawa12)]

## Processing

### Calibration

- pipeline or manual: Standard JAO procedures for bandpass, amplitude, phase calibration  
  > "We used the standard procedures provided by the Joint ALMA Observatory to apply the bandpass, amplitude, and phase calibrations." (2.2 Data reduction)
- casa version: CASA 4.2.0 (r28322) for S1-S4; 4.2.1 (r29047) for S5  
  > "We used version 4.2.0 (r28322) for setups S1 to S4 and version 4.2.1 (r29047) for setup S5." (2.2 Data reduction)
- pipeline version: _not stated_
- archive products used as is: _not stated_
- flux calibrator: _not stated_
- flux scale uncertainty: ~15% relative  
  > "we estimate the relative calibration uncertainty on the flux density to be on the order of 15%." (2.2 Data reduction)
- self calibration: three or four iterations using a strong line toward Sgr B2(N1)  
  > "three or four iterations of self-calibration were performed using a strong spectral line detected toward Sgr B2(N1) in each setup." (2.2 Data reduction)

### Imaging

- task: CASA csclean imager mode  
  > "The deconvolution was performed with the *csclean* imager mode and a *Briggs* weighting scheme with a *robust* parameter of 0.5." (2.2 Data reduction)
- deconvolver: _not stated_
- weighting robust: Briggs, robust = 0.5  
  > "The deconvolution was performed with the *csclean* imager mode and a *Briggs* weighting scheme with a *robust* parameter of 0.5." (2.2 Data reduction)
- uv taper: _not stated_
- cell size: 0.3''  
  > "The cell size was set to $0.3''$." (2.2 Data reduction)
- image size: _not stated_
- masking: _not stated_
- multiscale scales: _not stated_
- continuum subtraction: First-order baseline fitted to six groups of line-free channels per spectral window, in CLASS  
  > "A first-order baseline was fitted to these selected channels and the result of the fit was used to split each data cube into two cubes" (2.2 Data reduction)
- line free channels: _not stated_
- primary beam correction: _not stated_
- array combination: Measurement sets of S3 and S4 concatenated with concat  
  > "The measurement sets of setup S3 were merged into one single measurement set with the CASA task *concat* before imaging." (2.2 Data reduction)
- smoothing: _not stated_
- final beam: ~1.2-2.9'' HPBW (Table of beams)  
  > "S3 | 0 | 91368 – 93242   | $2.9 \times 1.5$ | $84$" (Table 2)
- final rms: 1.9-4.9 mJy/beam per spectral window (0.10-0.24 K)  
  > "| 3         | 112494 – 114368 | $1.6 \times 1.2$ | $-77$        |   | 4.9         | 0.24  |" (Table 3 (synthesized beam and rms noise per spectral window))

### Inherited from earlier work

- Initial LTE model parameters from IRAM 30 m survey  
  > "We used the input parameters of our LTE model of the IRAM 30 m spectrum of Sgr B2(N) (cite: Belloche13) as a starting point" (3 Radiative transfer modeling) [from (cite: Belloche13)]
- Optical depth correction of population diagrams  
  > "Each population diagram was also corrected for optical depth following the method described in (cite: Goldsmith99)" (3 Radiative transfer modeling) [from (cite: Goldsmith99)]
- Methanol and ethanol LTE parameters  
  > "We report in Table [\[t:coldens\]](#t:coldens) the parameters derived in that paper for the main isotopologue based on the analysis of all isotopologues." (5.5.3 Deuterated ethanol) [from (cite: Mueller15c)]

### Not stated but needed to reproduce (our reading)

- Exact line-free channel ranges per spectral window
- Self-calibration solution intervals and the line used
- Clean thresholds, masks, image size
- Integration frequency boundaries for each line
- Full list of identified transitions (stated as not available)
- Tolerances for by-eye LTE parameter optimization
- Velocity of source systemic velocity assumed

## Analysis recipe

1. **Measure source sizes**: 2D Gaussian fits to integrated intensity maps of uncontaminated lines; median deconvolved size adopted  
  > "The source size was set to the median deconvolved size of all such transitions." (3 Radiative transfer modeling)
   - software: GILDAS
   - fitting: _not stated_
   - validation: _not stated_
2. **Population diagrams for rotational temperature**: Linear fit to optical-depth- and contamination-corrected population diagrams of well-detected lines  
  > "Each population diagram was also corrected for optical depth following the method described in (cite: Goldsmith99), using the opacities delivered by Weeds." (3 Radiative transfer modeling)
   - software: Weeds
   - fitting: Linear fit; formal errors viewed with caution  
  > "we believe that the formal errors on the rotational temperature derived from the fit to the population diagrams do not necessarily represent the true errors" (3 Radiative transfer modeling)
   - validation: Population diagram used to verify manually derived temperature  
  > "The population diagrams were used to verify that the rotational temperature derived in the course of the (manual) modeling with Weeds made sense." (3 Radiative transfer modeling)
3. **LTE modeling of full spectrum**: Per-species synthetic LTE spectra with size, N, T, velocity offset and FWHM; four parameters optimized by eye; summed linearly into full model  
  > "The other four parameters were optimized by eye." (3 Radiative transfer modeling)
   - software: Weeds
   - assumption: LTE, uniform physical structure, Gaussian source; deuterated species share parameters of main isotopologue  
  > "The physical structure of the source assumed for the modeling is uniform." (3 Radiative transfer modeling)
   - fitting: Manual by-eye  
  > "The other four parameters were optimized by eye." (3 Radiative transfer modeling of the line survey)
   - validation: Detected if frequency, peak intensity and width are reproduced and line not contaminated  
  > "We emphasize that our definition of a “detected” line is very conservative" (3 Radiative transfer modeling)
4. **Deuteration levels and upper limits**: Column density of deuterated species from the main-species LTE model parameters; ratio XD/XH  
  > "This model is then used to obtain constraints on the column density of the deuterated species." (5 Results)
   - software: Weeds
   - assumption: 12C/13C used to derive main species N from 13C isotopologues; statistical 2:1 distribution for out-of-plane/in-plane conformers  
  > "we assumed a statistical distribution (2:1) to compute and report individual column densities" (4 Spectroscopic predictions)
   - fitting: _not stated_
   - validation: Compared with astrochemical models T14, A12 and Orion KL  
  > "The results are compared to predictions of two astrochemical models that treat the deuteration process." (abstract)

## Software

- **CASA** 4.2.0 / 4.2.1: Calibration, imaging, fixvis, concat  
  > "The data was calibrated and imaged with CASA." (2.2 Data reduction)
- **CLASS** : Baseline subtraction to separate line and continuum  
  > "This process of baseline subtraction was performed with the CLASS software" (2.2 Data reduction)
- **GREG (GILDAS)** : Noise measurement with go noise  
  > "The noise level of each spectral window corresponds to the median of the noise levels measured in all channel maps using the procedure *go noise* in GREG" (2.2 Data reduction)
- **Weeds** : Synthetic LTE spectra and opacities  
  > "We used the software Weeds (cite: Maret11) to produce synthetic LTE spectra" (3 Radiative transfer modeling)

## Numeric results

| quantity | value | uncertainty | units | step | quote |
|---|---|---|---|---|---|
| CH2DCN deuteration level | 0.4 | not stated | % | 4 | we derive a deuterium fractionation of $0.4\%$ for this molecule |
| CH2DOH deuteration | 0.12 | not stated | % | 4 | The deuterium fractionation we derive for this isotopologue is 0.12% |
| CH3OD deuteration upper limit | <0.07 | not stated | % | 4 | CH$_3$OD ($<0.07\%$) |
| DC3N deuteration | 0.09 | not stated | % | 4 | We obtain a deuterium fractionation of 0.09% |
| [CH2DOH]/[CH3OD] | >1.8 | not stated | dimensionless | 4 | leads to \[CH$_2$DOH\]/\[CH$_3$OD\] $> 1.8$ |
| CH2DCN rotational temperature (population diagram) | 136 | 14 | K | 2 | / CH$_2$DCN / $\varv=0$ / 136 (14) / |
| C2H5CN rotational temperature (population diagram) | 137.3 | 1.6 | K | 2 | / C$_2$H$_5$CN / $\varv=0$ / 137.3 (1.6) / |

## Qualitative findings

- Ethyl cyanide is less deuterated than methyl cyanide by at least a factor five  
  > "Ethyl cyanide is less deuterated than methyl cyanide by at least a factor five." (abstract)

## Claim tuples

- H: Deuterated COMs are detectable in Sgr B2(N2) | E: LTE modeling of ALMA 3 mm survey | R: CH2DCN secure; CH2DOH, CH2DCH2CN, CH3CHDCN, DC3N tentative | F: Deuteration levels 0.05-0.4% | **supported**
- H: Observed deuteration agrees with chemical models | E: Comparison with models T14 and A12 | R: Except CH3CN, levels at least factor four below predictions | F: Models overpredict deuteration | **refuted**
- H: Sgr B2(N2) deuteration differs from Orion KL | E: Literature comparison | R: Lower by a factor of a few up to ten | F: May be due to higher temperature or lower D abundance in the Galactic Center | **partially**

## Reasoning

- Why this data: Sgr B2(N2) chosen for narrow linewidths at EMoCA resolution compared with N1  
  > "We focus on Sgr B2(N2) rather than the main hot core Sgr B2(N1) because the former has relatively narrow linewidths" (1 Introduction)
- Why this method: _not stated_
- How they decided it was enough: _not stated_
- Limitation (authors): Uniform single-component LTE model cannot fit very optically thick lines; formal temperature errors unreliable  
  > "Here again, a more complex model with a non-uniform physical structure would be necessary to fit all transitions in a consistent way." (5.2)
- Caveat (inferred, ours): Tentative detections rest on one or two lines
- Caveat (inferred, ours): Column densities by-eye fits with no uncertainties
- Caveat (inferred, ours): Models are for low-mass hot corinos
- Caveat (inferred, ours): Deuterium abundance explanation untested

## Reproducibility

- Data public (paper): Interferometric data available in ALMA archive  
  > "The interferometric data are available in the ALMA archive at https://almascience.eso.org/aq/." (Acknowledgements)
- Products in archive: _not stated_
- Missing: Line-free channel selections
- Missing: Self-calibration details
- Missing: Full line list
- Missing: By-eye fit parameters beyond table
- Data volume (inferred): Large; ~10 measurement sets of 4 spectral windows, likely several hundred GB raw
- Score (inferred): 3/5, Data public and LTE parameters tabulated, but by-eye fitting and missing channel/selfcal details limit exact reproduction.
- Rediscovery candidate: no, Manual by-eye modeling and unstated processing choices make a faithful redo difficult.

## Links

- Method: (cite: Belloche13) (IRAM 30 m LTE model starting point)
- Method: (cite: Maret11) (Weeds software)
- Companion: (cite: Mueller15c) (Alkanols and alkanethiols from EMoCA; methanol/ethanol parameters)
- Companion: (cite: Belloche14) (First EMoCA result, branched alkyl cyanide)
- Related: EMoCA

## Checks

```json
{
 "quotes": 61,
 "quotes_ok": 61,
 "quote_pass_rate": 1.0,
 "quotes_too_long": 0,
 "unsupported_facts": 0,
 "project_codes": 2,
 "codes_not_in_text": [],
 "codes_not_in_obscore": [],
 "obscore_codes_not_in_card": [],
 "codes_printed_but_missing": [],
 "numeric_results": 7,
 "numeric_problems": 0,
 "fill": {
  "facts": 70,
  "stated": 45,
  "rate": 0.643
 },
 "evidence_ok": true
}
```
