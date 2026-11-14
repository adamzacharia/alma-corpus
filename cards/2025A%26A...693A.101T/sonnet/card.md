# Characterising the molecular line emission in the asymmetric Oph-IRS 48 dust trap: Temperatures, timescales, and sub-thermal excitation

`2025A&A...693A.101T` | Astronomy and Astrophysics 2025 | first author: Temmink, Milou | arXiv: 2411.12418 | DOI: 10.1051/0004-6361/202452175

Card schema 1.0 | model claude-sonnet-5-5 | depth full | type archival_reuse

## Science

- Fields: protoplanetary_disks, astrochemistry
- Question: What are the excitation conditions (rotational/kinetic temperatures), emitting layers and physical/chemical timescales of SO2, CH3OH and H2CO in the asymmetric IRS 48 dust trap, and does a vortex influence the temperature structure?  
  > "We also investigate whether the anticyclonic motion of the potential vortex influences the observable temperature structure of the gas." (abstract)
- Target **Oph-IRS 48**: coordinates _not stated_; z/distance 135 pc  
  > "located in the Ophiuchus star-forming region (at a distance of 135 pc; (cite: GC18))" (1 Introduction); "accounting for the disk’s inclination, $i$=50, and position angle, $PA$=100" (2 Data); distance from Gaia (Gaia Collaboration 2018)  
  > "located in the Ophiuchus star-forming region (at a distance of 135 pc; (cite: GC18))" (1 Introduction); "accounting for the disk’s inclination, $i$=50, and position angle, $PA$=100" (2 Data)

## Data provenance

- ALMA projects: 2021.1.00738.S, 2013.1.00100.S, 2017.1.00834.S, 2019.1.01059.S
- bands: Band 7 (Cycle 8 SO2/CH3OH; Cycle 5 H2CO)  
  > "we use the lower angular resolution ($\sim$0.46"), Cycle 5 Band 7 observations of presented in (cite: vdMarelEA21)." (2 Data)
- frequencies and spectral setup: 8 spectral windows, ~336.9-356.9 GHz, ~0.84 km/s resolution  
  > "The observations consist of 8 spectral windows, covering transitions at frequencies between $\sim$336.9 and $\sim$356.9 GHz at a spectral resolution of $\sim$0.84 km s$^{-1}$." (2 Data)
- continuum bandwidth: _not stated_
- arrays: _not stated_
- configurations: _not stated_
- baselines: _not stated_
- angular resolution: beam 0.34"x0.26" (Cycle 8); ~0.46" (Cycle 5)  
  > "pixel sizes of 0.04", beam sizes of 0.34"$\times$0.26"" (2 Data)
- max recoverable scale: _not stated_
- sensitivity: RMS ~1 mJy/beam (Cycle 8); 1.0-1.5 mJy/beam (Cycle 5)  
  > "Overall, we find RMS values of $\sim$1 mJy beam$^{-1}$ for the Cycle 8 observations" (3.1 Identifying detected transitions)
- time on source: _not stated_
- observing dates: _not stated_
- pi or archival as stated: Cycle 8 PI A. S. Booth  
  > "2021.1.00738.S, PI: A. S. Booth" (2 Data)
- Line: SO2 6(4,2)-6(3,3) and 12 others (357.9258478 GHz)
- Line: CH3OH 13(-1)-13(0) (A) and 21 others (342.729796 GHz)
- Line: H2CO 5(0,5)-4(0,4) (p) and 6 others (362.736048 GHz)
- External data: Cycle 5 Band 7 H2CO observations (7 transitions)  
  > "we use the lower angular resolution ($\sim$0.46"), Cycle 5 Band 7 observations of presented in (cite: vdMarelEA21)." (2 Data) [from (cite: vdMarelEA21)]
- External data: High-resolution 0.9 mm dust continuum  
  > "high-resolution, 0.9 mm dust observations (cite: YangEA23)" (2 Data) [from (cite: YangEA23)]
- External data: DALI thermochemical model of IRS 48 (n_gas, T_gas, T_dust)  
  > "We have used the inferred properties (i.e. $n_\textnormal{gas}$, $T_\textnormal{gas}$, and $T_\textnormal{dust}$) of the IRS 48 disk as modelled by (cite: LeemkerEA23) using the thermochemical code DALI" (6.1 Methodology) [from (cite: LeemkerEA23)]
- External data: Binding energies SO2 3254 K, CH3OH 4930 K, H2CO 3260 K  
  > "$E_\textnormal{b,\ce{SO_2}}$=3254 K (cite: PerreroEA22), $E_\textnormal{b,\ce{CH_3OH}}$=4930 K (cite: BB07)" (6.1 Methodology) [from (cite: PerreroEA22; BB07; NobleEA12; PenteadoEA17)]
- External data: Photodissociation rates for SO2, CH3OH, H2CO  
  > "$k_\textnormal{\ce{SO_2}}$=1.6$\times$10$^{-9}$ s$^{-1}$, $k_\textnormal{\ce{CH_3OH}}$=5.3$\times$10$^{-10}$ s$^{-1}$" (6.1 Methodology) [from (cite: HeaysEA17)]
- Simulation/model as data: DALI model of IRS 48 used for densities, temperatures and FUV field in timescale calculations  
  > "We refer the reader to (cite: LeemkerEA23) for all details on the model (see their Appendix B)." (6.1 Methodology)

## Processing

### Calibration

- pipeline or manual: _not stated_
- casa version: _not stated_
- pipeline version: _not stated_
- archive products used as is: _not stated_
- flux calibrator: _not stated_
- flux scale uncertainty: _not stated_
- self calibration: described in Booth et al. 2024  
  > "We refer to (cite: BoothEA24) for a description of the data reduction, self-calibration, and continuum subtraction." (2 Data)

### Imaging

- task: _not stated_
- deconvolver: _not stated_
- weighting robust: _not stated_
- uv taper: _not stated_
- cell size: 0.04" pixels  
  > "pixel sizes of 0.04", beam sizes of 0.34"$\times$0.26"" (2 Data)
- image size: _not stated_
- masking: _not stated_
- multiscale scales: _not stated_
- continuum subtraction: done as in Booth et al. 2024  
  > "We refer to (cite: BoothEA24) for a description of the data reduction, self-calibration, and continuum subtraction." (2 Data)
- line free channels: _not stated_
- primary beam correction: _not stated_
- array combination: _not stated_
- smoothing: _not stated_
- final beam: 0.34"x0.26" (Cycle 8)  
  > "pixel sizes of 0.04", beam sizes of 0.34"$\times$0.26"" (2 Data)
- final rms: ~1 mJy/beam  
  > "we find RMS values of $\sim$1 mJy beam$^{-1}$ for the Cycle 8 observations" (3.1 Identifying detected transitions)

### Inherited from earlier work

- Data reduction, self-calibration and continuum subtraction of Cycle 8 data  
  > "We refer to (cite: BoothEA24) for a description of the data reduction, self-calibration, and continuum subtraction." (2 Data) [from (cite: BoothEA24)]
- H2CO RADEX column density of 1e14 cm-2 and RADEX line-ratio approach  
  > "Following (cite: vdMarelEA21) we used a column density of $N_\textnormal{\ce{H_2CO}}$=10$^{14}$ cm$^{-2}$ in the calculations" (4.3 H2CO) [from (cite: vdMarelEA21)]
- Rotational diagram model intensity method  
  > "we follow the method described by, for example, (cite: BanzattiEA12) to create model intensities" (3.2 Integrated intensity and rotational diagram analysis) [from (cite: BanzattiEA12)]
- 3 sigma upper limits for pixels without rotational diagram  
  > "we have calculated 3$\sigma$ upper limits, following the description of (cite: CarneyEA19)" (3.2 Integrated intensity and rotational diagram analysis) [from (cite: CarneyEA19)]
- Mixing timescale formulation  
  > "We determine the turbulent vertical mixing timescale following the description provided by (cite: XieEA95) and (cite: SemenovEA06)" (6.1 Methodology) [from (cite: XieEA95; SemenovEA06)]

### Not stated but needed to reproduce (our reading)

- Cycle 8 calibration/imaging details (robust, CLEAN settings, line-free channels) are only in Booth et al. 2024
- Fitting method/optimiser and initial guesses for rotational diagram not given
- Gaussian line fit details (windows, constraints) not given
- Which ortho-to-para ratio assumed for H2CO
- RADEX collisional partner/background temperature settings not given
- Cycle 5 H2CO data reduction details not given
- Minimisation grid details for H2CO ratio temperatures
- Dilution of upper limits and masking of pixels near edge not detailed

## Analysis recipe

1. **Identify detected transitions per pixel and measure RMS**: Search LAMDA lines (A_ul>=1e-6, E_up<=500 K); detect >3 sigma peaks; RMS from Savitzky-Golay filtered, outlier-masked line-free spectrum; remove blends/noise  
  > "We limit our search to transitions with Einstein-A coefficients of $A_\textnormal{ul} \geq 10^{-6}$ s$^{-1}$ and upper level energies of $E_\textnormal{up}\leq$500 K" (3.1 Identifying detected transitions)
   - software: LAMDA, Savitzky-Golay filter
   - parameter: third-order polynomials every 100 data points; 2 sigma outlier masking; 3 sigma detection  
  > "We filtered the data using third-order polynomials that smoothed the data every 100 data points." (3.1 Identifying detected transitions)
   - assumption: Blended transitions with identical A and E_up each contribute half the flux  
  > "we assume that half of the observed line flux can be attributed to each of the transitions" (3.1 Identifying detected transitions)
   - fitting: _not stated_
   - validation: Visual inspection of cubes and line profiles  
  > "through trial and error and visual inspection of the image cubes and line profiles, we have removed additional transitions" (3.1 Identifying detected transitions)
2. **Pixel-by-pixel rotational diagrams for SO2 and CH3OH**: Gaussian fit integrated fluxes; fit model intensities to get T_rot and N; beam area as emitting area; 3 sigma upper limits elsewhere  
  > "We obtain integrated fluxes by fitting Gaussian line profiles. As the flux from individual pixels is not independent, we consider the beam area to be the emitting area" (3.2 Integrated intensity and rotational diagram analysis)
   - parameter: line width 0.2 km/s; pixels within 1.5" radius  
  > "=0.2 km s$^{-1}$. This line width is a combination of the thermal line width" (3.2 Integrated intensity and rotational diagram analysis)
   - assumption: Optically thin, LTE, beam-filling emitting area  
  > "Our analysis assumes that the molecular emission is optically thin" (4 Results)
   - fitting: _not stated_
   - validation: Obs-to-model intensity ratios and uncertainty maps  
  > "The left-side of Figure [14](#fig:RDAs-Ratios) displays the intensity ratios between the observations and the modelled intensities." (4.1)
3. **H2CO temperature from line ratios with RADEX**: Minimise difference between observed and RADEX line ratios for n_H2=1e7 and 1e8 cm-3  
  > "using a simple minimisation of the ratios obtained through RADEX with the inferred ratios from the observations, for gas densities of $n_\textnormal{\ce{H_2}}$=10$^7$ cm$^{-3}$ and 10$^8$ cm$^{-3}$" (4.3 H2CO)
   - software: RADEX
   - parameter: N(H2CO)=1e14 cm-2; line width 1 km/s; one ortho and three para ratio pairs  
  > "we have used the default line width of 1 km s$^{-1}$ within the RADEX calculations" (4.3 H2CO)
   - assumption: Optically thin at 1e14 cm-2  
  > "at which the emission should be optically thin" (4.3 H2CO)
   - fitting: simple minimisation  
  > "using a simple minimisation of the ratios" (4.3 H2CO)
   - validation: Compared with disk-integrated temperatures of van der Marel et al. 2021  
  > "this is generally similar to, albeit slightly higher than, the ratios derived from the disk-integrated values of (cite: vdMarelEA21)" (4.3 H2CO)
4. **Test thermalisation with RADEX grids**: RADEX grids over T_kin and n_H2; fit straight line to fluxes to get T_rot and compare to T_kin  
  > "For each calculation, we infer the rotational temperature by fitting a straight line ($y=ax+b$) through all the retrieved RADEX integrated fluxes" (5.1 Sub-thermal excitation)
   - software: RADEX
   - parameter: T_kin 10-200 K step 10; log n 5-12 step 0.1; N=1e12 cm-2; E_up<=300 K, A>=1e-6; <1000 GHz  
  > "$T_\textnormal{kin}$ (10 K to 200 K in steps of 10 K) and $\log_{10}\left(n_\textnormal{\ce{H_2}}\right)$ (5 to 12 in steps of 0.1" (5.1 Sub-thermal excitation)
   - assumption: Densities from DALI model  
  > "following the DALI model of (cite: LeemkerEA23)" (5.1 Sub-thermal excitation)
   - fitting: linear fit in rotational diagram  
  > "For each calculation, we infer the rotational temperature by fitting a straight line ($y=ax+b$) through all the retrieved RADEX integrated fluxes, where the rotation temperature is given by the slope, $a=-1/T_\textnormal{rot}$." (Sub-thermal excitation)
   - validation: Comparison with Johnstone et al. 2003  
  > "As shown in Figure 6 of (cite: JohnstoneEA03), higher energy lines of have higher critical densities" (5.1 Sub-thermal excitation)
5. **Brightness temperatures and vertical structure**: Planck brightness temperature of 0.9 mm continuum and optically thick isotopologue lines in absorption-free channels  
  > "Using Planck’s law, we have calculated the brightness temperature of the high-resolution, optically thick 0.9 mm continuum emission" (5.2.2 Vertical structure)
   - assumption: Optically thick emission fully resolved  
  > "under the assumption that the emission is fully resolved" (Conclusions)
   - fitting: _not stated_
   - validation: _not stated_
6. **Optical depth grids and beam dilution**: Grid optical depth over emitting beam radius and line width at fixed T_rot; dilution factor estimate for a 10 au sliver  
  > "we have explored grids over both parameters" (5.3.1 Optical depth)
   - parameter: T_rot 55 K SO2, 150 K CH3OH, 150 and 350 K H2CO; line width up to 1.0 km/s  
  > "$T_\textnormal{rot}$=55 K for , $T_\textnormal{rot}$=150 K for , and $T_\textnormal{rot}$=150 K and $T_\textnormal{rot}$=350 K for" (5.3.1 Optical depth)
   - assumption: H2CO/isotopologue ratio ~4 implies optically thick  
  > "Considering a previously derived isotopologue ratio, /$\sim$4 (cite: BoothEA24), it is very likely that its emission is optically thick." (5.3.1 Optical depth)
   - fitting: _not stated_
   - validation: _not stated_
7. **Timescales at dust trap**: Compute mixing, desorption, freeze-out and photodissociation timescales using DALI model quantities  
  > "The mixing timescale can be approximated as $t_\textnormal{mix}\sim H^2/D_\textnormal{turb}$" (6.1 Methodology)
   - software: DALI
   - parameter: alpha = 1e-4, 1e-3, 1e-2; n_s = 1.5e15 cm-2; sticking = 1  
  > "We have determined the vertical mixing timescales for three commonly used values of $\alpha$: 10$^{-4}$, 10$^{-3}$, 10$^{-2}$." (6.1 Methodology)
   - assumption: Isothermal sound speed; single binding energy per species; blackbody 10,000 K for photodissociation  
  > "sound speed (taken to be isothermal)" (6.1 Methodology)
   - fitting: _not stated_
   - validation: _not stated_

## Software

- **RADEX** : Non-LTE line ratios and thermalisation grids  
  > "We have used RADEX (cite: RADEX) to investigate at what gas densities the , , and emission thermalises." (5.1 Sub-thermal excitation)
- **DALI** : Thermochemical model providing densities, temperatures, FUV field  
  > "using the thermochemical code DALI (cite: BrudererEA12; BrudererEA13)" (6.1 Methodology)
- **LAMDA** : Line identification and collisional data  
  > "identified using the ‘Leiden Atomic and Molecular Database’ (LAMDA" (3.1 Identifying detected transitions)
- **Savitzky-Golay filter** : Baseline/RMS estimation  
  > "an iterative, 2$\sigma$-outlier masking process and a Savitzky-Golay filter" (3.1 Identifying detected transitions)
- **NumPy, SciPy, Astropy, Matplotlib, pandas, IPython, Jupyter** : General analysis and plotting  
  > "NumPy, SciPy, Astropy, Matplotlib, pandas, IPython, Jupyter" (Acknowledgements)

## Numeric results

| quantity | value | uncertainty | units | step | quote |
|---|---|---|---|---|---|
| SO2 rotational temperature at peak | 54.8 | ±1.4 | K | 2 | derive a rotational temperature of $T$=54.8$\pm$1.4 K |
| SO2 peak column density | 4.8e13 | ±0.1e13 | cm^-2 | 2 | peak total column density of $N$=(4.8$\pm$0.1)$\times$10$^{13}$ cm$^{-2}$ |
| CH3OH rotational temperature at peak | 125.5 | +3.7/-3.5 | K | 2 | $T$=125.5$^{+3.7}_{-3.5}$ K |
| CH3OH peak column density | 1.2e14 | ±0.1e14 | cm^-2 | 2 | total column density of $N$=(1.2$\pm$0.1)$\times$10$^{14}$ cm$^{-2}$ |
| H2CO temperature range from line ratios | 150-350 | not stated | K | 3 | temperatures of across the dust trap can be expected to be on the order of $T\sim$150-350 K |
| Peak brightness temperature of 0.9 mm continuum | ~32 | not stated | K | 5 | peak brightness temperature of $T_\textnormal{b}\sim$32 K for the dust continuum |
| Brightness temperatures of the 3-2 and 6-5 isotopologue lines | ~110 and ~135 | not stated | K | 5 | $T_\textnormal{b,3-2}\sim$110 K and $T_\textnormal{b,6-5}\sim$135 K |
| Beam dilution inverse factor | ~0.002 (column density underestimated by ~500) | not stated | dimensionless | 6 | This yields $\textnormal{DF}^{-1}\sim$0.002 or, in other words, an underestimation of the column density by a factor of $\sim$500. |
| Vertical mixing timescale for alpha=1e-4/1e-3/1e-2 | (5-8)e5 / (5-8)e4 / (5-8)e3 | not stated | years | 7 | $t_\textnormal{mixing}\sim$(5-8)$\times$10$^5$ years, $\sim$(5-8)$\times$10$^4$ years, and $\sim$(5-8)$\times$10$^3$ years |
| Maximum SO2 optical depth | ~0.1 | not stated | dimensionless | 2 | maximum optical depth of $\tau\sim$0.1 |

## Qualitative findings

- No hints of a vortex influencing the temperature structure; effect at most a few K  
  > "this influence, if present, is very small, on the order of a few K." (Conclusions)
- Turbulent mixing is slower than photodissociation, so another vertical mixing mechanism (e.g. VSI) is needed  
  > "These photodissociation timescales are significantly shorter than the vertical mixing timescales." (6.2)

## Claim tuples

- H: Are SO2 and CH3OH emission thermalised and where do they originate? | E: Rotational diagrams plus RADEX thermalisation grids | R: SO2 diagram well behaved at 54.8 K, thermalises at ~1e8 cm-3; CH3OH diagram shows scatter | F: SO2 emits from near midplane; CH3OH and H2CO are sub-thermally excited, so T_rot underestimates T_kin | **supported**
- H: Does the vortex alter the gas temperature structure? | E: Temperature maps across the dust trap | R: No azimuthal variation; SO2 hints at radial gradient | F: No evidence for vortex influence | **supported**
- H: Can H2CO be optically thick given the low isotopologue ratio? | E: Optical depth grids over beam radius and line width | R: Needs emitting radius ≲8-16 au | F: Emission from a ~10 au radial sliver at the inner edge of dust trap | **partially**
- H: What explains the differing azimuthal extents? | E: Timescale calculations from DALI model | R: Photodissociation timescales ≤1 yr in upper layers | F: Short timescales explain compact extent of one species; a gas-phase formation reservoir is proposed for the wider one | **partially**

## Reasoning

- Why this data: _not stated_
- Why this method: Multiple transitions allow rotational diagrams to constrain excitation; non-LTE RADEX needed for sparse/sub-thermal species  
  > "Detecting multiple transitions allows one, under the assumption of local thermal equilibrium (LTE), to directly infer both the gas thermal and excitation properties through a rotational diagram analysis" (1 Introduction)
- Alternative: Turbulent diffusion rejected as explanation for vertical mixing; VSI suggested  
  > "it is, therefore, unlikely that turbulent diffusion is the correct explanation for vertical mixing" (6.2)
- How they decided it was enough: _not stated_
- Limitation (authors): Radial extent unresolved; beam dilution underestimates column densities  
  > "Beam dilution results in an underestimation of the inferred column densities." (5.3.1)
- Limitation (authors): Continuum oversubtraction/blocking may reduce line flux  
  > "we expect that we are not probing the full line flux of these molecules" (5.3.2)
- Caveat (inferred, ours): Rotational temperatures rely on LTE and beam-filling assumptions contradicted by the paper's own sub-thermal and sliver results
- Caveat (inferred, ours): H2CO temperature minimisation has no formal uncertainties
- Caveat (inferred, ours): Timescales depend on a single DALI model and single binding energies
- Caveat (inferred, ours): Optically thin assumption with fixed 0.2 km/s width affects N and T

## Reproducibility

- Data public (paper): ALMA project codes listed; Cycle 8 data from Booth et al.  
  > "This paper makes use of the following ALMA data: 2013.1.00100.S, 2017.1.00834.S, 2019.1.01059.S, 2021.1.00738.S." (Acknowledgements)
- Products in archive: _not stated_
- Missing: Reduced and self-calibrated image cubes (Booth et al. 2024 pipeline)
- Missing: DALI model outputs from Leemker et al. 2023
- Missing: Fitting code and settings for rotational diagrams
- Missing: Cycle 5 H2CO cubes and high-resolution continuum from Yang et al.
- Data volume (inferred): ~50-200 GB raw for Band 7 Cycle 8 and Cycle 5 data; much less for calibrated cubes
- Score (inferred): 3/5, Data public and methods are clear, but reduction is deferred to another paper, the DALI model is external and fitting details are sparse.
- Rediscovery candidate: no, Depends on cubes from a companion paper and an external DALI model; fitting details incomplete.

## Links

- Method: (cite: BoothEA24) (Data reduction, self-calibration and continuum subtraction)
- Method: (cite: LeemkerEA23) (DALI model of IRS 48)
- Method: (cite: BanzattiEA12) (Rotational diagram model intensity method)
- Companion: (cite: vdMarelEA21) (Original Cycle 5 H2CO observations and analysis)
- Companion: (cite: BoothEA21) (First report of SO2 detection)

## Checks

```json
{
 "quotes": 86,
 "quotes_ok": 86,
 "quote_pass_rate": 1.0,
 "quotes_too_long": 0,
 "unsupported_facts": 0,
 "project_codes": 4,
 "codes_not_in_text": [],
 "codes_not_in_obscore": [],
 "obscore_codes_not_in_card": [],
 "codes_printed_but_missing": [],
 "numeric_results": 10,
 "numeric_problems": 0,
 "fill": {
  "facts": 98,
  "stated": 62,
  "rate": 0.633
 },
 "evidence_ok": true
}
```
