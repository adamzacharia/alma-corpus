# The ALMA Fornax Cluster Survey I: stirring and stripping of the molecular gas in cluster galaxies

`2019MNRAS.483.2251Z` | Monthly Notices of the Royal Astronomical Society 2019 | first author: Zabel, Nikki | arXiv: 1811.11759 | DOI: 10.1093/mnras/sty3234

Card schema 1.0 | model claude-sonnet-5-5 | depth full | type large_program_or_survey

## Science

- Fields: nearby_galaxies, star_formation, milky_way_ism
- Question: Does the cluster environment affect the molecular gas in Fornax cluster galaxies, and which processes are responsible?  
  > "The goal of this work is to investigate whether the cluster environment indeed affects the molecular gas in galaxies, and if so, attempt to identify which processes are mainly responsible for this." (Introduction)
- Target **Fornax cluster galaxies (30 AlFoCS targets)**: coordinates per-galaxy RA/Dec in Table 1 (e.g. FCC32 03h24m52.4s -35d26m08s)  
  > "Although accurate distance measurements are available for some of the AlFoCS galaxies, here we adopt the distance to the Fornax cluster (19.95 Mpc, (cite: Tonry2001)) as a common distance to all galaxies." (Introduction); z/distance 19.95 Mpc (common cluster distance)  
  > "Although accurate distance measurements are available for some of the AlFoCS galaxies, here we adopt the distance to the Fornax cluster (19.95 Mpc, (cite: Tonry2001)) as a common distance to all galaxies." (Introduction); distance from Tonry et al. 2001  
  > "Although accurate distance measurements are available for some of the AlFoCS galaxies, here we adopt the distance to the Fornax cluster (19.95 Mpc, (cite: Tonry2001)) as a common distance to all galaxies." (Introduction)

## Data provenance

- ALMA projects: 2015.1.00497.S, 2015.1.01135.S
- bands: Band 3 (CO(1-0) at ~115 GHz)  
  > "Band 3 observations were performed between the 7th and 12th of January 2016" (3.1 ALMA data)
- frequencies and spectral setup: SPW3 on 12CO(1-0), 1.875 GHz, 3840 channels; other SPWs 128 channels, 2 GHz for continuum  
  > "The bandwidths are 1.875 GHz, covering 3840 channels. The other spectral windows, covering 128 channels each with total bandwidths of 2 GHz, were used to target the band 3 continuum" (3.1 ALMA data)
- continuum bandwidth: _not stated_
- arrays: 12 m array  
  > "ALMA’s 12 m configuration was used, which has a primary beam size of $\sim$55” at $\sim$115 GHz." (3.1 ALMA data)
- configurations: _not stated_
- baselines: _not stated_
- angular resolution: _not stated_
- max recoverable scale: 25"  
  > "The largest recoverable scale is 25”." (3.1 ALMA data)
- sensitivity: typical rms ~3 mJy/beam per channel  
  > "Typical rms noise levels are around $\sim$3 mJy/beam." (3.1.1 Data reduction)
- time on source: _not stated_
- observing dates: 7-12 January 2016 (NGC1365: 20 March 2016)  
  > "It was observed on 20 March 2016." (3.1.2 NGC1365)
- pi or archival as stated: 2015.1.00497.S PI Davis; NGC1365 from archive 2015.1.01135.S PI Egusa  
  > "project ID: 2015.1.01135.S, PI: Egusa, Fumi" (3.1.2 NGC1365)
- Line: 12CO J=1-0 (115.271 GHz)
- Other facility **Mopra**: single-dish 12CO(1-0) for 28 Fornax galaxies; one extra detection (NGC1317) and upper limits  
  > "Additional single-dish observations of Fornax cluster galaxies from the Mopra Fornax Cluster CO-Line Legacy Survey (PI: M.W.L. Smith) are included" (3.2 Mopra data)
- Other facility **Fornax Deep Survey (VST)**: u, g, r optical images for comparison with CO  
  > "*r*-, *g*-, and *u*-band images were obtained from the Fornax Deep Survey" (3.3 Optical data)
- Other facility **AAT 2dF/AAOmega**: redshifts for a subset of targets  
  > "A subset of the AlFoCS objects were observed with the 3.9m Anglo-Australian Telescope at the Siding Spring Observatory" (3.4 Redshift determinations)
- Other facility **WISE**: 3.6 um images for stellar masses where Fuller+2014 not available  
  > "they were obtained from aperture photometry on archival Wide-field Infrared Survey Explorer (WISE, (cite: Wright2010)) band 1 (3.6 $\mu$m) images" (4.3 H2 masses)
- External data: Stellar masses for many targets and Herschel FIR detections  
  > "$^\dagger$Stellar masses from (cite: Fuller2014)" (Table 1) [from (cite: Fuller2014)]
- External data: xCOLD GASS field control sample median gas fractions  
  > "We use the relation based on the median values that they obtained by subdividing the sample in bins based on their stellar mass (cite: Saintonge2017)" (4.4 Gas fractions & deficiencies) [from (cite: Saintonge2017)]
- External data: Cluster mean velocity 1493 km/s and dispersion 374 km/s  
  > "The mean velocity and velocity dispersion of the Fornax cluster were taken from (cite: Drinkwater2001a), and equal 1493 km s$^{-1}$and 374 km s$^{-1}$, respectively." (2 Sample selection) [from (cite: Drinkwater2001a)]
- External data: Reduced NGC1365 image from archive  
  > "an already reduced image of NGC1365 was taken from the ALMA archive" (3.1.2 NGC1365) [from project 2015.1.01135.S, PI Egusa]
- External data: HI mass of NGC1427A 2.1e9 Msun  
  > "Its atomic hydrogen mass is $M_{\text{H{\sc i} }} = 2.1 \times 10^9 M_\odot$ (cite: Lee-Waddell2018)" (5.5 NGC1427A) [from (cite: Lee-Waddell2018)]

## Processing

### Calibration

- pipeline or manual: manual calibration with standard ALMA calibration scripts  
  > "The data were calibrated manually using the Common Astronomy Software Applications package (CASA, version 5.1.1, (cite: McMullin2007)), using standard ALMA calibration scripts" (3.1.1 Data reduction)
- casa version: CASA 5.1.1 (NGC1365 imaging in CASA 4.7.0)  
  > "CASA, version 5.1.1" (3.1.1 Data reduction)
- pipeline version: _not stated_
- archive products used as is: _not stated_
- flux calibrator: J0336-3616 (Table 2)  
  > "Single fields | 07-01-2016 | 42 | 52 | J0336-3616 | J0336-3616" (Table 2)
- flux scale uncertainty: 10%  
  > "The expected calibration uncertainty of the data is 10%." (3.1 ALMA data)
- self calibration: _not stated_

### Imaging

- task: tclean, interactive  
  > "Cleaning of the channels containing the CO line was done interactively" (3.1.1 Data reduction)
- deconvolver: _not stated_
- weighting robust: natural (robust = 2); NGC1365 Briggs robust 0.5  
  > "using a natural weighting scheme (equivalent to a Briggs weighting scheme (cite: Briggs1995) with a robust parameter of 2)" (3.1.1 Data reduction)
- uv taper: _not stated_
- cell size: 0.5 arcsec (NGC1365: 0.3 arcsec)  
  > "the pixel sizes 0.5 arcseconds" (3.1.1 Data reduction)
- image size: _not stated_
- masking: _not stated_
- multiscale scales: _not stated_
- continuum subtraction: uvcontsub using full line-free bandwidth, when CO and continuum detected  
  > "a continuum estimate is created using the full line-free bandwidth, and subtracted from the channels containing the CO line using the `uvcontsub` command" (3.1.1 Data reduction)
- line free channels: _not stated_
- primary beam correction: impbcor as separate step  
  > "Primary beam (PB) corrections are then carried out as a separate step using the `impbcor` command" (3.1.1 Data reduction)
- array combination: _not stated_
- smoothing: _not stated_
- final beam: ~2.4-3.3" x 1.8-2.4" (Table 3)  
  > "FCC32 | 32 | - | G | 2.4; 1.8; 84 | 2.6 | 50" (Table 3)
- final rms: ~3 mJy/beam per channel  
  > "Typical rms noise levels are around $\sim$3 mJy/beam." (3.1.1 Data reduction)

### Inherited from earlier work

- 10 km/s channel width choice  
  > "The channel widths of most final data cubes are 10 km s$^{-1}$, as is usually chosen for this type of data (cite: Alatalo2013)" (3.1.1 Data reduction) [from (cite: Alatalo2013)]
- Masked moment method  
  > "using the masked moment method (cite: Dame2011)" (3.6 Moment maps) [from (cite: Dame2011)]
- Metallicity-dependent alpha_CO  
  > "We use the metallicity-dependent mass conversion factor derived from (cite: Accurso2017)" (4.3 H2 masses) [from (cite: Accurso2017)]
- Mass-metallicity relation  
  > "using the mass-metallicity relation from (cite: Sanchez2017), which uses the calibration from (cite: Pettini2004)" (4.3 H2 masses) [from (cite: Sanchez2017)]
- Line-flux error equation  
  > "adapted from equation 1 from (cite: Young2011)" (4.3 H2 masses) [from (cite: Young2011)]

### Not stated but needed to reproduce (our reading)

- Which galaxies had continuum subtracted and the line-free channel ranges
- Clean masks, thresholds and iteration limits
- Mosaic pointing layouts and phase/bandpass calibrators other than flux calibrators
- Exact channel ranges and aperture boxes used for integrated spectra
- Exact Gaussian-fit procedure and box boundaries
- Mopra reduction scripts beyond those described
- Continuum imaging parameters and spectral-index fitting method
- Specifics of the xCOLD GASS interpolation for expected H2 mass

## Analysis recipe

1. **Calibrate and image CO cubes**: Manual CASA calibration, tclean with natural weighting, uvcontsub, impbcor  
  > "The resulting “dirty” images were then “cleaned” using the `tCLEAN` algorithm (cite: Hogbom1974) in CASA." (3.1.1 Data reduction)
   - software: CASA
   - parameter: 10 km/s channels (2 km/s for FCC207, FCC261), 0.5" pixels  
  > "Exceptions are the dwarf galaxies FCC207 and FCC261, for which channel widths of 2 km s$^{-1}$were used" (3.1.1 Data reduction)
   - fitting: _not stated_
   - validation: _not stated_
2. **Make moment maps, PVDs and spectra**: Masked moment method with smoothed-cube mask clipped at 3 or 4 sigma; PVD from beam-wide slit along major axis  
  > "Gaussian smoothing was applied to a copy of the data cube, in both spatial axes as well as the velocity axis, with a full width at half the maximum (FWHM) of 1.5 times the beam’s major axis" (3.6 Moment maps)
   - parameter: velocity smoothing 4 channels; clip at 3 or 4 sigma  
  > "where $x$ is chosen to give the best visual result, and equals 3 or 4." (3.6 Moment maps)
   - fitting: _not stated_
   - validation: _not stated_
3. **Classify morphology and kinematics**: Visual inspection of moment 0 and 1 maps: regular vs disturbed  
  > "Whether a galaxy is morphologically disturbed or regular is determined by visual inspection of the moment 0 and 1 maps" (5.1 Gas morphologies & kinematics)
   - fitting: _not stated_
   - validation: _not stated_
4. **Measure line flux and derive H2 masses**: Gaussian fit or direct box integration; M_H2 from CO flux with metallicity-dependent X_CO (Accurso+2017), metallicity from stellar mass  
  > "For the first group we fit a Gaussian to the CO(1-0) line and integrate this fit to obtain the total line flux. For the second group, we integrate directly under the line observed." (4.3 H2 masses)
   - parameter: Delta MS = 0; 10% calibration error added  
  > "Here we assume a distance from the main sequence $\Delta$MS = 0 for all galaxies." (4.3 H2 masses)
   - assumption: D = 19.95 Mpc; alpha_CO multiplied by 2.14e20 for X_CO; stellar M/L = 1 at 3.6 um  
  > "It is multiplied by $2.14 \times 10^{20}$ to obtain X$_\text{CO}$ (cite: Bolatto2013)." (4.3 H2 masses)
   - fitting: _not stated_
   - validation: _not stated_
5. **Upper limits for non-detections**: 3 sigma limits assuming Gaussian line of FWHM 50 km/s, peak 3x rms in inner PB-corrected cube  
  > "we assume Gaussian line profiles with FWHM of 50 km s$^{-1}$" (4.3.1 Upper limits)
   - fitting: _not stated_
   - validation: _not stated_
6. **Compare gas fractions with field**: Compare M_H2/M_star with xCOLD GASS median relation (log interpolation/extrapolation); deficiency = log observed - log expected; KS and Mann-Whitney tests vs. cluster radius  
  > "We define H$_2$ deficiencies here as log($M_{H_{2}, \text{observed}}$) - log($M_{H_{2}, \text{expected}}$)." (4.4 Gas fractions & deficiencies)
   - fitting: _not stated_
   - validation: KS and Mann-Whitney tests  
  > "Kolmogorov-Smirnov and Mann-Whitney *U* tests are unable to reject the null hypothesis that both groups of galaxies are drawn from the same distribution at more than $\sim$2$\sigma$." (4.4 Gas fractions & deficiencies)

## Software

- **CASA** 5.1.1 (4.7.0 for NGC1365 archive): calibration, tclean, uvcontsub, impbcor  
  > "calibrated manually using the Common Astronomy Software Applications package (CASA, version 5.1.1" (3.1.1 Data reduction)
- **LIVEDATA** : Mopra baseline fitting and SDFITS conversion  
  > "`LIVEDATA` is used to fit baselines and transform the raw datafiles to SDFITS files." (3.2 Mopra data)
- **GRIDZILLA** : combining Mopra files into cubes  
  > "`GRIDZILLA` is then used to combine these files into data cubes." (3.2 Mopra data)
- **2dFDR** : reducing AAT spectra  
  > "The spectra were reduced using the 2dFDR software package" (3.4 Redshift determinations)
- **MARZ** : spectral classification and redshifts  
  > "spectral classifications and redshifts were determined using MARZ" (3.4 Redshift determinations)

## Numeric results

| quantity | value | uncertainty | units | step | quote |
|---|---|---|---|---|---|
| CO detections | 15 of 30 | not stated | galaxies | 4 | CO was detected (at $> 3 \sigma$) in 15 of the 30 galaxies observed. |
| Mean H2 deficiency, regular galaxies | -0.50 | not stated | dex | 6 | Galaxies with regular CO emission have an average H$_2$ deficiency of -0.50 dex |
| Mean H2 deficiency, disturbed galaxies | -1.1 | not stated | dex | 6 | galaxies with disturbed CO emission have an average H$_2$ deficiency of -1.1 dex |
| log M_H2 NGC1365 | 9.49 | 0.04 | log Msun | 4 | NGC1365 / 121 / R / B / 2.4; 2.0; 12 / 12 / 940 / 1221 $\pm$ 20 / 9.49 $\pm$ 0.04 |
| NGC1380 continuum spectral index | 1.1 | 0.2 | dimensionless | 0 | NGC1380 / 107.765 / 4.18 $\pm$ 0.04 / 113.763 / 4.65 $\pm 0.08$ / 101.775 / 4.12 $\pm 0.04$ / 1.1 $\pm$ 0.2 |
| NGC1427A metallicity from gas-to-dust ratio | 12+log(O/H) = 8.12 | not stated | dex | 0 | The resulting metallicity, assuming these relations hold, is $12 + \text{log}(\text{O/H})$ = 8.12 (or 0.27 $Z_\odot$). |

## Qualitative findings

- All 8 detected galaxies with M* < 3e9 Msun have disturbed molecular gas; 7 regular galaxies  
  > "All 8 detected galaxies with stellar masses below $3 \times 10^9 M_\odot$ have disturbed molecular gas reservoirs, only 7 galaxies are regular/undisturbed." (abstract)
- Detections and non-detections occur at all projected cluster locations  
  > "Both detections and non-detections occur at all projected locations in the cluster." (abstract)

## Claim tuples

- H: Cluster environment disturbs molecular gas, especially in low-mass galaxies | E: Visual classification of CO moment maps for 15 detections, compared with HI of field dwarfs (LITTLE THINGS) | R: All galaxies below 3e9 Msun disturbed; only ~half of field dwarfs disturbed in HI | F: Low-mass galaxies are more disturbed than in the field; Fornax still active | **supported**
- H: Fornax galaxies are H2 deficient relative to field | E: Compare M_H2/M* with xCOLD GASS | R: Mean deficiency -0.50 dex (regular), -1.1 dex (disturbed) | F: Disturbed galaxies significantly H2 deficient | **supported**
- H: Ram pressure stripping disturbs the molecular gas | E: Look for tails aligned with cluster centre | R: Two tails (MCG-06-08-024, ESO359-G002) aligned with cluster direction | F: RPS possible but not confirmed; galaxy-galaxy interactions not excluded | **partially**
- H: Gas properties depend on cluster location | E: Deficiency vs projected distance with KS and Mann-Whitney tests | R: No significant difference at >~2 sigma | F: No clear dependence on location, small sample | **partially**

## Reasoning

- Why this data: _not stated_
- Why this method: Natural weighting used to recover extended emission and maximise S/N at cost of resolution  
  > "Many of the sources have extended emission, and using natural weighting will help ensure that this is recovered in the data." (3.1.1 Data reduction)
- How they decided it was enough: _not stated_
- Limitation (authors): Current HI data lack resolution to compare HI and CO morphologies  
  > "The current Hi observations available are not of sufficient resolution to do this." (3.7 Comparison to optical morphology)
- Limitation (authors): Small number statistics; 2D projection  
  > "Although we suffer from small number statistics, there are a few other possible explanations for this:" (5.3)
- Caveat (inferred, ours): Disturbed/regular classification is purely visual and subjective
- Caveat (inferred, ours): Single distance of 19.95 Mpc applied to all galaxies
- Caveat (inferred, ours): X_CO from stellar-mass metallicity with Delta MS = 0 is uncertain for dwarfs
- Caveat (inferred, ours): xCOLD GASS control sample lies above the mass range of most disturbed dwarfs; extrapolation used
- Caveat (inferred, ours): 25" maximum recoverable scale may resolve out flux in extended galaxies

## Reproducibility

- Data public (paper): ALMA archive projects cited; reduction scripts and channel maps on GitHub  
  > "The scripts used can be found on <https://github.com/NikkiZabel/AlFoCS_data_reduction_scripts>" (Footnote 2)
- Products in archive: _not stated_
- Code: Data reduction scripts at github.com/NikkiZabel/AlFoCS_data_reduction_scripts  
  > "The scripts used can be found on <https://github.com/NikkiZabel/AlFoCS_data_reduction_scripts>" (Footnote 2)
- Missing: Line-free channel ranges and clean masks
- Missing: Mopra reduction scripts
- Missing: Integration boundaries per galaxy
- Data volume (inferred): ~100-300 GB raw for the three SBs plus NGC1365 archive
- Score (inferred): 4/5, Public data, scripts released, clear mass/deficiency recipe; some per-galaxy choices are visual or unstated.
- Rediscovery candidate: yes, Data are public, recipe is largely complete, and main results (detection counts, M_H2, deficiencies) are numeric.

## Links

- Method: (cite: Accurso2017) (metallicity-dependent alpha_CO)
- Method: (cite: Saintonge2017) (xCOLD GASS field control)
- Method: (cite: Dame2011) (masked moment method)
- Companion: (cite: Fuller2014) (Herschel Fornax Cluster Survey dust and stellar masses)
- Companion: Loni et al. in prep. (ATCA HI data)
- Companion: (cite: Venhola2018) (FDS dwarf photometry)
- Related: Herschel Fornax Cluster Survey
- Related: Fornax Deep Survey
- Related: Mopra Fornax Cluster CO-Line Legacy Survey
- Related: xCOLD GASS
- Related: MeerKAT Fornax Survey

## Checks

```json
{
 "quotes": 73,
 "quotes_ok": 73,
 "quote_pass_rate": 1.0,
 "quotes_too_long": 0,
 "unsupported_facts": 0,
 "project_codes": 2,
 "codes_not_in_text": [],
 "codes_not_in_obscore": [],
 "obscore_codes_not_in_card": [],
 "codes_printed_but_missing": [],
 "numeric_results": 6,
 "numeric_problems": 0,
 "fill": {
  "facts": 89,
  "stated": 59,
  "rate": 0.663
 },
 "evidence_ok": true
}
```
