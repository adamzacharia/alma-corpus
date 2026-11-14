# ALMA Spatially Resolved Dense Molecular Gas Survey of Nearby Ultraluminous Infrared Galaxies

`2019ApJS..241...19I` | The Astrophysical Journal Supplement Series 2019 | first author: Imanishi, Masatoshi | arXiv: 1902.04124 | DOI: 10.3847/1538-4365/ab05b9

Card schema 1.0 | model claude-sonnet-5-5 | depth full | type large_program_or_survey

## Science

- Fields: nearby_galaxies, agn_and_quasars, astrochemistry
- Question: How do HCN-to-HCO+ J=3-2 flux ratios, dense gas mass and vibrationally excited HCN vary within a uniformly selected sample of nearby ULIRGs, and do they reveal buried AGNs?  
  > "It is a natural next step to apply the powerful (sub)millimeter molecular line method to an extended number of carefully and uniformly selected nearby ULIRG samples, using the highly sensitive ALMA." (1 Introduction)
- Target **26 nearby ULIRGs from the IRAS 1 Jy sample (e.g. IRAS 00188-0856, IRAS 14348-1447, IRAS 22491-1808)**: coordinates Peak positions listed per source in Table 3 (e.g. IRAS 00188-0856: 00 21 26.514, -08 39 26.01)  
  > "Our targets are nearby ULIRGs in the IRAS 1 Jy sample (cite: kim98)." (2 Selected Targets and Molecular Lines); "Col.(3): Luminosity distance (in Mpc)." (Table 1); z/distance z=0.0730-0.144; d_L 326-676 Mpc (Table 1); H0=71, OmegaM=0.27, OmegaL=0.73  
  > "Our targets are nearby ULIRGs in the IRAS 1 Jy sample (cite: kim98)." (2 Selected Targets and Molecular Lines); "Col.(3): Luminosity distance (in Mpc)." (Table 1); distance from Redshifts from optical (Kim & Sanders 1998) or ALMA line redshifts; luminosity distance from adopted cosmology  
  > "Our targets are nearby ULIRGs in the IRAS 1 Jy sample (cite: kim98)." (2 Selected Targets and Molecular Lines); "Col.(3): Luminosity distance (in Mpc)." (Table 1)

## Data provenance

- ALMA projects: 2017.1.00057.S, 2013.1.00032.S, 2015.1.00027.S
- bands: Band 6 (211-275 GHz)  
  > "Our HCN J=3–2 and HCO$^{+}$ J=3–2 observations of 23 ULIRGs in band 6 (211–275 GHz) were conducted" (3 Observations and Data Analyses)
- frequencies and spectral setup: 1.875 GHz wide mode, three spectral windows covering HCN, HCO+ J=3-2 and v2=1f lines  
  > "We adopted the widest 1.875 GHz width mode and three spectral windows to simultaneously cover HCN J=3–2" (3 Observations and Data Analyses)
- continuum bandwidth: _not stated_
- arrays: _not stated_
- configurations: Longest baseline >2500 m for most; ~500 m for IRAS 21329-2346 and IRAS 22206-2715  
  > "with the longest baseline of $>$2500 m, excluding IRAS 21329$-$2346 and IRAS 22206$-$2715 whose observations were made in 2018 April with the $\sim$500 m longest baseline." (3 Observations and Data Analyses)
- baselines: _not stated_
- angular resolution: 0.1''-0.2'' (150-530 pc) for most; 0.6''-0.8'' for two sources  
  > "with a final synthesized beam size of 0.1$''$–0.2$''$ (150–530 pc)" (3 Observations and Data Analyses)
- max recoverable scale: 1-3'' for 0.1-0.2'' beams; 7-9'' for two sources with 0.6-0.8'' beams  
  > "the maximum recoverable scale (MRS) is 1–3$''$ (1.4–7.5 kpc) for sources with 0.1$''$–0.2$''$ synthesized beam sizes" (3 Observations and Data Analyses)
- sensitivity: _not stated_
- time on source: 8-39 min per source (Table 2)  
  > "Col.(5): Net on source integration time in minutes." (Table 2)
- observing dates: Mostly 2017 December; two sources 2018 April  
  > "Observations of the majority of the ULIRGs were conducted in 2017 December" (3 Observations and Data Analyses)
- pi or archival as stated: Own Cycle 5 program (PI Imanishi); three sources from Cycle 2/3 data of earlier paper  
  > "We thus observed the remaining 23 ULIRGs in Cycle 5." (2 Selected Targets and Molecular Lines)
- Line: HCN J=3-2 (265.886 GHz)
- Line: HCO+ J=3-2 (267.558 GHz)
- Line: HCN v2=1f J=3-2 (267.199 GHz)
- Line: HCO+ v2=1f J=3-2 (268.689 GHz)
- Other facility **IRAS**: Fluxes and IR luminosities for sample selection  
  > "are *IRAS* fluxes at 12 $\mu$m, 25 $\mu$m, 60 $\mu$m, and 100 $\mu$m, respectively, taken from (cite: kim98)." (Table 1)
- Other facility **Herschel**: 250-500 um photometry for SED comparison  
  > "there are photometric data by Herschel at 250 $\mu$m, 350 $\mu$m, and 500 $\mu$m (cite: cle18)" (5.6 Spatially Integrated Continuum Emission and SED)
- External data: IR-spectroscopic AGN bolometric contributions  
  > "Col.(12): Infrared-spectroscopically estimated bolometric contribution of AGNs (in %) by (cite: nar10)." (Table 1) [from (cite: nar10)]
- External data: Pre-ALMA interferometric CO J=1-0 total molecular masses  
  > "from pre-ALMA interferometric CO J=1–0 observations (cite: eva00; eva02)" (5.4 Nuclear Dense Molecular Mass) [from (cite: eva00; eva02)]
- External data: Optical spectral classifications  
  > "Col.(11): Optical spectroscopic classification by (cite: vei99)." (Table 1) [from (cite: vei99)]
- External data: HCN/HCO+ J=3-2 results for three Cycle 2/3 ULIRGs  
  > "$^{C}$ Taken from (cite: ima16c)." (Table 3) [from (cite: ima16c)]

## Processing

### Calibration

- pipeline or manual: Started from ALMA-provided calibrated data  
  > "We started our data reduction from calibrated data provided by ALMA, using CASA (https://casa.nrao.edu)." (3 Observations and Data Analyses)
- casa version: _not stated_
- pipeline version: _not stated_
- archive products used as is: _not stated_
- flux calibrator: _not stated_
- flux scale uncertainty: <10% in Cycle 5 band 6  
  > "The absolute flux calibration uncertainty of band 6 data is expected to be $<$10% in ALMA Cycle 5." (3 Observations and Data Analyses)
- self calibration: _not stated_

### Imaging

- task: CASA clean  
  > "Then we applied the “clean” task (Briggs-weighting; robust $=$ 0.5 and gain $=$ 0.1)" (3 Observations and Data Analyses)
- deconvolver: _not stated_
- weighting robust: Briggs, robust = 0.5, gain 0.1  
  > "Briggs-weighting; robust $=$ 0.5 and gain $=$ 0.1" (3 Observations and Data Analyses)
- uv taper: _not stated_
- cell size: 0.02'' (0.04'' for IRAS 21329-2346 and IRAS 22206-2715)  
  > "The pixel scales were 0.02$''$ pixel$^{-1}$ for the majority of the observed ULIRGs" (3 Observations and Data Analyses)
- image size: _not stated_
- masking: _not stated_
- multiscale scales: _not stated_
- continuum subtraction: uvcontsub using line-free channels  
  > "we determined the continuum level, and subtracted it using the CASA task “uvcontsub”." (3 Observations and Data Analyses)
- line free channels: _not stated_
- primary beam correction: _not stated_
- array combination: _not stated_
- smoothing: Final velocity resolution ~20 km/s  
  > "The final velocity resolution was $\sim$20 km s$^{-1}$." (3 Observations and Data Analyses)
- final beam: 0.1''-0.2'' for most; 0.6''-0.8'' for two  
  > "final synthesized beam size of 0.1$''$–0.2$''$ (150–530 pc)" (3 Observations and Data Analyses)
- final rms: _not stated_

### Inherited from earlier work

- Cycle 2/3 data and results for IRAS 12112+0305, 20414-1651, 22491-1808 taken from earlier paper  
  > "$^{C}$ Taken from (cite: ima16c)." (Table 3) [from (cite: ima16c)]
- Luminosity calculation using equations of Solomon & Vanden Bout  
  > "equations (1) and (3) of (cite: sol05) were used for the calculations from the estimated fluxes" (5.4 Nuclear Dense Molecular Mass) [from (cite: sol05)]
- Free-free flux formula  
  > "(cite: nak05), where D is the luminosity distance (in Mpc)" (5.6 Spatially Integrated Continuum Emission and SED) [from (cite: nak05)]

### Not stated but needed to reproduce (our reading)

- Line-free channel ranges used for uvcontsub per source (only continuum frequency ranges in Table 3)
- Image size, masking, clean threshold and niter
- Whether archive pipeline-calibrated products or manual scripts were used; CASA version
- Velocity ranges summed for moment 0 maps and Gaussian fitting windows/masks
- Calibration of the Cycle 2/3 data (2013.1.00032.S, 2015.1.00027.S) processing
- Details of aperture-flux extraction and spectral-line contamination handling
- Definition of rms for moment maps and thresholds for ratio maps

## Analysis recipe

1. **Image continuum and lines**: uvcontsub then clean to make continuum and line cubes from calibrated data  
  > "Then we applied the “clean” task (Briggs-weighting; robust $=$ 0.5 and gain $=$ 0.1) for the continuum-only and continuum-subtracted molecular line data to create maps." (3 Observations and Data Analyses)
   - software: CASA
   - parameter: robust 0.5, gain 0.1, ~20 km/s channels  
  > "robust $=$ 0.5 and gain $=$ 0.1" (3 Observations and Data Analyses)
   - fitting: _not stated_
   - validation: _not stated_
2. **Measure line fluxes and sizes**: Gaussian fits to spectra at continuum peak; moment 0/1/2 maps; imfit for deconvolved sizes; spectra in 1-2'' apertures  
  > "Gaussian fits for the detected HCN J=3–2 and HCO$^{+}$ J=3–2 emission lines were applied, after removing data points possibly affected by other emission and/or absorption features" (4 Results); "using the CASA task “imfit”" (4 Results)
   - software: CASA
   - fitting: Gaussian line profile fits; some parameters fixed for faint lines  
  > "For faint emission lines, we fixed some parameters to the best fit or fiducial values." (Table 4)
   - validation: Gaussian fluxes compared with moment 0 peak values  
  > "These values roughly agree with the Gaussian fit estimates" (4 Results)
3. **HCN/HCO+ flux ratios and maps**: Ratios of Gaussian fluxes for nuclear beam and integrated spectra; ratio maps from moment 0 where HCO+ >~3 sigma  
  > "we display in Figure 6 only regions with $\gtrsim$3$\sigma$ HCO$^{+}$ J=3–2 emission line detection in the moment 0 maps" (5.1 HCN-to-HCO+ J=3-2 Flux Ratios)
   - fitting: _not stated_
   - validation: NGC 7469 shown as a known-AGN comparison  
  > "This trend is clearly seen in the nearby well-studied optically identified luminous AGN, NGC 7469" (5.1 HCN-to-HCO+ J=3-2 Flux Ratios)
4. **Dense gas mass**: Line luminosity (Solomon & Vanden Bout) times alpha_HCN  
  > "assuming the lower range of $\alpha_{\rm HCN}$ = 10, the derived dense molecular gas mass from the HCN J=3–2 emission line luminosity is as high as $>$10$^{9}$M$_{\odot}$" (5.4 Nuclear Dense Molecular Mass)
   - assumption: alpha_HCN=10 (range 6-40), optically thick thermalized; alpha_CO=1.5 for CO J=2-1 total mass  
  > "$\alpha_{\rm CO}$=1.5 (cite: eva02) and optically thick thermal excitation for CO J=2–1 (T$_{\rm ex}$ $\sim$ T$_{\rm kin}$) are assumed" (5.4 Nuclear Dense Molecular Mass)
   - fitting: _not stated_
   - validation: Compared to CO-based total molecular masses  
  > "dense molecular gas masses can account for the bulk of the nuclear total molecular masses" (5.4 Nuclear Dense Molecular Mass)
5. **Continuum SED and free-free estimate**: Integrated continuum flux vs Herschel/IRAS extrapolation; free-free from L_FIR formula with Te=10^4 K  
  > "These estimates of the free-free emission are shown in Table 10 (column 3), where T$_{\rm e}$ = 10$^{4}$ K is assumed." (5.6 Spatially Integrated Continuum Emission and SED)
   - assumption: Te = 10^4 K  
  > "where T$_{\rm e}$ = 10$^{4}$ K is assumed" (5.6 Spatially Integrated Continuum Emission and SED)
   - fitting: _not stated_
   - validation: _not stated_

## Software

- **CASA** : Calibrated data handling, uvcontsub, clean, imfit  
  > "We started our data reduction from calibrated data provided by ALMA, using CASA (https://casa.nrao.edu)." (3 Observations and Data Analyses)

## Numeric results

| quantity | value | uncertainty | units | step | quote |
|---|---|---|---|---|---|
| Number of ULIRGs in complete sample | 26 | not stated | sources | 0 | We selected 26 sources with infrared fluxes above a certain threshold |
| HCN v2=1f detection rate (Cycle 5) | at most ~9% (2/23) | not stated | percent | 3 | The detection rate of the HCN v$_{2}$=1f J=3–2 emission line in ULIRGs observed in ALMA Cycle 5 is at most $\sim$9 % (=2/23). |
| HCN v2=1f detection rate (full sample) | ~19% (5/26) | not stated | percent | 3 | the detection rate in the complete sample could be as high as $\sim$19 % (=5/26) |
| HCN v2=1f to v=0 flux ratio (IRAS 10378+1108, 11095-0238 NE) | ~0.05 | not stated | dimensionless | 3 | The HCN v$_{2}$=1f to v=0 flux ratios at J=3–2 are $\sim$0.05 |
| Dense gas mass (alpha_HCN=10), IRAS 14348-1447 SW | >5.2e9 | lower limit | Msun | 4 | are $>$5.2 $\times$ 10$^{9}$M$_{\odot}$, $>$3.0 $\times$ 10$^{9}$M$_{\odot}$ |
| Total molecular mass IRAS 22491-1808 nucleus (CO 2-1) | ~6e9 | not stated | Msun | 4 | to be $\sim$6 $\times$ 10$^{9}$M$_{\odot}$ |
| HCN/HCO+ J=3-2 ratio, IRAS 00188-0856 nuclear peak | 1.9 | 0.2 | dimensionless | 3 | / IRAS 00188$-$0856    /    1.9$\pm$0.2     /     1.7$\pm$0.2      / |
| Integrated continuum / peak continuum flux ratio | 1.5-6 | not stated | dimensionless | 5 | are substantially (a factor of 1.5–6) larger than the continuum fluxes at the nuclear peak positions |

## Qualitative findings

- HCN J=3-2 emission size comparable to continuum; HCO+ more extended  
  > "the emission size of the HCO$^{+}$ J=3–2 line is larger overall than those of the continuum and HCN J=3–2 line" (4 Results)
- No broad outflow wings seen in HCN or HCO+ J=3-2  
  > "The broad emission wings in HCN J=3–2 and HCO$^{+}$ J=3–2 lines were not clearly seen in any of the observed ULIRGs in this paper (Fig. 2)." (5.3 Molecular Inflow and Outflow)

## Claim tuples

- H: HCN/HCO+ J=3-2 ratios are elevated at ULIRG nuclei relative to extended regions | E: Compare Gaussian flux ratios in beam-sized nuclear and 1-2'' integrated spectra and ratio maps | R: Most objects lie below the 1:1 line; nuclear ratios higher | F: Elevated nuclear HCN, possibly AGN, dense warm gas or shocks | **supported**
- H: ULIRG nuclei are rich in dense molecular gas | E: Convert HCN/HCO+ J=3-2 luminosity to mass with alpha_HCN=10; compare with CO-based totals | R: >1e9 Msun in most | F: Dense gas dominates nuclear molecular mass | **supported**
- H: Vibrationally excited HCN signals buried AGNs in the sample | E: Search for excess emission on low-frequency side of HCO+ | R: Possible detection in 2 of 23 (5/26 with earlier sources) | F: Low detection rate, possibly due to wide lines and S/N | **partially**
- H: Spatially resolved 240 GHz continuum is dust-dominated | E: Compare integrated flux with free-free estimate and Herschel extrapolation | R: Observed flux exceeds free-free upper limits | F: Dust thermal radiation contributes significantly | **supported**

## Reasoning

- Why this data: _not stated_
- Why this method: Band 6 J=3-2 chosen for better weather tolerance than band 7 and simultaneous coverage of vibrationally excited lines  
  > "due to less requirements for weather conditions in band 6, the chance of program execution is higher than that in band 7" (2 Selected Targets and Molecular Lines)
- Alternative: Decreased HCO+ abundance considered but regarded as likely wide-area rather than nuclear-only  
  > "However, we regard that this could happen in wide areas of merging ULIRGs, rather than only at the compact nuclear cores." (Footnote 1)
- How they decided it was enough: _not stated_
- Limitation (authors): Emission larger than MRS can be missed  
  > "Diffuse continuum and molecular line emission with a spatial scale larger than the MRS can be missed in our ALMA data." (3 Observations and Data Analyses)
- Limitation (authors): HCO+ flux may be contaminated by HCN v2=1f  
  > "possible contamination from the nearby vibrationally excited (v$_{2}$=1f) HCN J=3–2 emission lines cannot be completely removed." (4 Results)
- Caveat (inferred, ours): Alpha_HCN conversion is poorly constrained (6-40) and assumes thermalization
- Caveat (inferred, ours): Flux ratio interpretation is degenerate between AGN, excitation and shocks
- Caveat (inferred, ours): v2=1f detections are tentative and blended with HCO+ wings
- Caveat (inferred, ours): Ratio uncertainties and comparison starburst samples are not quantitatively tested

## Reproducibility

- Data public (paper): Project codes given; ALMA data acknowledged  
  > "This paper made use of the following ALMA data: ADS/JAO.ALMA#2017.1.00057.S, 2013.1.00032.S, and 2015.1.00027.S." (Acknowledgments)
- Products in archive: _not stated_
- Missing: CASA version and exact clean parameters (image size, mask, threshold)
- Missing: Line-free channels and Gaussian-fit windows
- Missing: Aperture centering and flux extraction specifics
- Data volume (inferred): Roughly 100-300 GB raw for 23 Cycle 5 execution blocks plus earlier-cycle data
- Score (inferred): 3/5, Public data and clear basic imaging recipe with tabulated results, but many imaging and fitting details are missing.
- Rediscovery candidate: yes, Data are public, the recipe is mostly simple (CASA clean, Gaussian fits), and results are tabulated numbers such as flux ratios.

## Links

- Method: (cite: sol05) (Line luminosity equations)
- Method: (cite: nak05) (Free-free emission formula)
- Companion: (cite: ima16c) (Cycle 2/3 observations of three of the sample ULIRGs)
- Companion: (cite: ima18b) (Earlier ALMA HCN/HCO+ J=4-3 ULIRG study)
- Related: IRAS 1 Jy sample

## Checks

```json
{
 "quotes": 73,
 "quotes_ok": 73,
 "quote_pass_rate": 1.0,
 "quotes_too_long": 0,
 "unsupported_facts": 0,
 "project_codes": 3,
 "codes_not_in_text": [],
 "codes_not_in_obscore": [],
 "obscore_codes_not_in_card": [],
 "codes_printed_but_missing": [],
 "numeric_results": 8,
 "numeric_problems": 0,
 "fill": {
  "facts": 76,
  "stated": 49,
  "rate": 0.645
 },
 "evidence_ok": true
}
```
