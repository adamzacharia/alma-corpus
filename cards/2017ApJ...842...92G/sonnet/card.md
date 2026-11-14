# Thermal Feedback in the High-mass Star- and Cluster-forming Region W51

`2017ApJ...842...92G` | The Astrophysical Journal 2017 | first author: Ginsburg, Adam | arXiv: 1704.01434 | DOI: 10.3847/1538-4357/aa6bfa

Card schema 1.0 | model claude-sonnet-5-5 | depth full | type observational_alma_primary

## Science

- Fields: star_formation, astrochemistry, milky_way_ism
- Question: Do forming high-mass protostars heat large volumes of surrounding gas (inhibiting fragmentation) while the main-sequence stars that power compact H II regions do not, and are the protostars on the main sequence while accreting?  
  > "High-mass stars have generally been assumed to accrete most of their mass while already contracted onto the main sequence, but this hypothesis has not been observationally tested." (abstract)
- Target **W51 (IRS2 and e1/e2 protoclusters; hot cores e2e, e8, North)**: coordinates _not stated_; z/distance _not stated_; distance from Sato2010a cited for distance (value not given in text)  
  > "we observed a $\sim2\arcmin\times1\arcmin$ region centered between W51 IRS2 and W51 e1/e2 with a 37-pointing mosaic." (2 Observations)

## Data provenance

- ALMA projects: 2013.1.00308.S
- bands: 1.3 mm (227 GHz)  
  > "We have presented ALMA 1.3 mm (227 GHz) continuum and line observations of the high-mass protocluster W51" (5 Conclusions)
- frequencies and spectral setup: 4 spectral windows between 218.1 and 235.0 GHz, channel widths 0.17-0.67 km/s  
  > "| 2 | 230.376575 | 232.36876148 | 488.281 | 0.64 |" (Table 1)
- continuum bandwidth: _not stated_
- arrays: 12m array (two configurations) 37-pointing mosaic plus 7m array 12-pointing mosaic  
  > "Additionally, a 12-pointing mosaic was performed using the 7m array, theoretically probing scales up to $\sim28$." (2 Observations)
- configurations: _not stated_
- baselines: ~12 to ~1500 m  
  > "The full UV coverage included baselines over the range $\sim12$ to $\sim1500$ m." (2 Observations)
- angular resolution: 0.2 arcsec (12m continuum); 0.33 arcsec for most line data  
  > "for a 0.33 beam (most of the spectral line data)" (2.1 Data Reduction)
- max recoverable scale: _not stated_
- sensitivity: continuum ~0.2 mJy/beam lowest noise, up to ~2 mJy/beam near e2 and IRS2  
  > "The lowest noise level in the image, away from bright sources, is $\sim0.2$ mJy/beam" (2.1.1 Continuum)
- time on source: _not stated_
- observing dates: _not stated_
- pi or archival as stated: _not stated_
- Line: CH3OH E 4(2,2)-3(1,2) through E 25(3,22)-24(4,20) (218.44-234.70 GHz)
- Line: 12CO 2-1 (230.538 GHz)
- Other facility **VLA**: centimeter continuum limits on free-free emission (from Ginsburg2016a/b)  
  > "This paper makes use of the ALMA data set 2013.1.00308.S and VLA data sets 12B-365, 13A-064, and 12A-074." (Acknowledgments)
- Other facility **BGPS**: single-dish 1.1 mm total flux density  
  > "we use the Bolocam Galactic Plane Survey observations (cite: Aguirre2011a; Ginsburg2013a)" (3.2 mass and light budget)
- External data: Herschel Hi-GAL SED dust temperatures (38 K or 26 K)  
  > "is 38 K when including the 70 $\mu \textrm{m}$ data or 26 K when excluding it." (8.3 Temperature estimation) [from Molinari2016a; Wang2015a]
- External data: cm continuum limits for e2e (<0.6 mJy/beam at 14.5 GHz)  
  > "$S_{14.5 GHz} < 0.6$ mJy/beam (2-$\sigma$) in a FWHM=$0.34\arcsec$ beam" (3.1.2) [from (cite: Ginsburg2016b)]
- External data: dust opacity extrapolation, kappa(227 GHz)=0.0083 cm2/g, beta=1.75  
  > "using the extrapolation of (cite: Ossenkopf1994a) opacity from (cite: Aguirre2011a) with $\beta=1.75$" (2.1.1 Continuum) [from Ossenkopf1994a; Aguirre2011a]

## Processing

### Calibration

- pipeline or manual: QA2 products reprocessed in CASA; datasets delivered with earlier versions reprocessed  
  > "including reprocessing of datasets that were delivered with earlier versions." (2.1 Data Reduction)
- casa version: CASA 4.5.2-REL (r36115)  
  > "Data reduction was performed using CASA 4.5.2-REL (r36115)" (2.1 Data Reduction)
- pipeline version: _not stated_
- archive products used as is: _not stated_
- flux calibrator: _not stated_
- flux scale uncertainty: _not stated_
- self calibration: phase self-cal on baselines >100 m (continuum)  
  > "We then phase self-calibrated the data on baselines longer than 100m to increase the dynamic range." (2.1.1 Continuum)

### Imaging

- task: tclean  
  > "A continuum image combining all 4 spectral windows was produced using `tclean`." (2.1.1 Continuum)
- deconvolver: _not stated_
- weighting robust: robust=-0.5 (hires cubes) and robust=1.0 (others)  
  > "the hires cubes used robust=-0.5 and the others used robust=1.0 in `tclean`." (Data Release)
- uv taper: _not stated_
- cell size: 0.05 arcsec pixels  
  > "minimum 10 pixels (each pixel is 0.05)" (3.1.1)
- image size: _not stated_
- masking: _not stated_
- multiscale scales: _not stated_
- continuum subtraction: median over [25,30],[80,95] km/s for kinematics; line-rich channels flagged for continuum  
  > "the median value over the spectral range \[25,30\],\[80,95\] km s$^{-1}$ was used to estimate and subtract the local continuum." (2.1.2 Lines)
- line free channels: _not stated_
- primary beam correction: _not stated_
- array combination: 12m-only for most analysis; 7m+12m separate set  
  > "Except where otherwise noted, the 12m-only data were used in order to focus on the compact structures." (2.1 Data Reduction)
- smoothing: _not stated_
- final beam: 0.21x0.19 arcsec at e2e; 0.2 arcsec continuum  
  > "In a $0.21\arcsec\times0.19\arcsec$ beam ($1100\times1000$ au)" (3.1.2)
- final rms: ~0.2 mJy/beam  
  > "The final image was cleaned to a threshold of 5 mJy." (2.1.1 Continuum)

### Inherited from earlier work

- Free-free/cm continuum data and H II region parameters  
  > "Assuming emission from an optically thick H II region with $T_e = 8500$ K (cite: Ginsburg2015a)" (3.1.2) [from Ginsburg2016b, Ginsburg2015a]
- Full reduction scripts in project github repository  
  > "Full details of the data reduction, including all scripts used, can be found on the project’s github repository" (2.1 Data Reduction) [from github.com/adamginsburg/W51_ALMA_2013.1.00308.S]

### Not stated but needed to reproduce (our reading)

- Robust value and clean parameters (scales, mask) for the main continuum image
- Exact line-free channel list for continuum
- Self-calibration solution interval
- Source distance value adopted
- Rotational diagram fitting details (pixel selection, S/N cuts)
- Which configurations/execution blocks were used

## Analysis recipe

1. **Continuum source identification**: astrodendro dendrogram on continuum, filtered by S/N from local residual RMS map; plus by-eye ds9 catalog  
  > "We used a minimum value of 1 mJy/beam ($\sim5\sigma$) and a minimum $\Delta=0.4$ mJy/beam ($\sim2\sigma$) with minimum 10 pixels" (3.1.1)
   - software: astrodendro, ds9
   - parameter: removed sources with peak S/N<8, mean S/N<5, min S/N<1; leaves only  
  > "We then removed all sources with peak S/N $< 8$, mean S/N per pixel $< 5$, or minimum S/N per pixel $< 1$." (3.1.1)
   - fitting: _not stated_
   - validation: tuned against by-eye sources; <10 spurious  
  > "most real sources are recovered and few spurious sources ($<10$) are included." (3.1.1)
2. **Brightness-temperature luminosity and dust mass limits for hot cores**: peak T_B as lower limit on temperature; blackbody L; optically thick minimum mass per beam  
  > "The implied luminosity, assuming blackbody emission from a spherical beam-filling source, is $L = 4\pi r^2 \sigma_{sb} T^4 = 2.3\ensuremath{\times 10^{4}} \ensuremath{L_{\odot}}$" (3.1.2)
   - software: dust_emissivity
   - assumption: kappa(227 GHz)=0.0083 cm2/g including gas-to-dust 100  
  > "assume an opacity constant $\kappa(227 \mathrm{GHz})=0.0083$ cm$^2$ g$^{-1}$" (3.1.2)
   - fitting: _not stated_
   - validation: compared with cm upper limits and methanol temperatures  
  > "For an independent measurement of the temperature that is not limited to the optically thick regions, we use the $\textrm{CH}_3\textrm{OH}$ lines in band, calculating an LTE temperature" (3.1.2 W51e2e mass and temperature estimates from continuum)
3. **CH3OH LTE rotational diagram temperatures and columns**: per-pixel rotational diagrams of moment-0 maps of 8 CH3OH lines, E/A=1  
  > "We produce rotational diagrams for each spatial pixel covering all $\textrm{CH}_3\textrm{OH}$ lines detected at high significance toward at least one position" (3.4)
   - software: pyspeckit, spectral-cube
   - parameter: moment range 51-60 km/s; continuum median over 25-35, 85-95 km/s  
  > "integrating over the range (51, 60) km s$^{-1}$ in continuum subtracted spectral cubes" (3.4)
   - assumption: optically thin, LTE, E/A=1  
  > "allowing robust measurements of the temperature assuming the lines are optically thin, in LTE" (3.4)
   - fitting: rotational diagram fit; sampler not stated  
  > "We produce rotational diagrams for each spatial pixel covering all $\textrm{CH}_3\textrm{OH}$ lines detected at high significance toward at least one position" (3.4 CH3OH temperatures & columns in the hot cores)
   - validation: modeled spectra overlaid on observed; significant discrepancies at low J due to self-absorption, temperatures biased high  
  > "These generally display significant discrepancies, especially at low J where self-absorption is evident." (3.4)
4. **Radial mass profiles and Jeans analysis**: enclosed mass vs radius with T_dust=T_CH3OH or 40 K; thermal Jeans mass and length  
  > "We put these together to measure the Jeans mass, $M_J = (\pi / 6) c_s^3 G^{-3/2} \rho^{-1/2}$" (4.4)
   - assumption: T_dust=40 K upper-mass case; 600 K lower bound  
  > "Assuming $T_{dust}=40$ K, approximately the hottest measured dust temperature in the region from Herschel SED fits" (3.5)
   - fitting: _not stated_
   - validation: _not stated_
5. **Kinematics and disk search**: moment 1/2 maps and position-velocity diagrams perpendicular to outflow (PA=35 deg for e2e)  
  > "Figure [14] shows position-velocity diagrams of a CH3OH and a CH3OCHO line extracted along PA $=35^\circ$" (3.6.2)
   - software: pvextractor, spectral-cube
   - fitting: _not stated_
   - validation: _not stated_
6. **Ionizing luminosity limit**: Stromgren sphere Q_lyc from cm T_B upper limit via Condon/Mezger relations; compare with tabulated B-star Q  
  > "the resulting $Q_{\textrm{lyc}}<6\ensuremath{\times 10^{45}}$ $\mathrm{s}^{-1}$ is well below the lowest tabulated $Q_{\textrm{lyc}}$" (4.3)
   - assumption: alpha_B=3e-13 cm3/s; Te=8500 K; optically thin H II region  
  > "where $\alpha_B = 3\ensuremath{\times 10^{-13}}$ cm$^{3}$ s$^{-1}$" (4.3)
   - fitting: _not stated_
   - validation: _not stated_

## Software

- **CASA** 4.5.2-REL (r36115): data reduction and tclean imaging  
  > "Data reduction was performed using CASA 4.5.2-REL (r36115)" (2.1 Data Reduction)
- **astrodendro** : continuum source identification  
  > "implemented in `astrodendro` to identify sources" (3.1.1)
- **ds9** : by-eye source regions  
  > "selected using `ds9`" (3.1.1)
- **pyspeckit** : listed software (spectral fitting)  
  > "pyspeckit <http://pyspeckit.bitbucket.org>" (Software)
- **spectral-cube** : listed software for cubes  
  > "spectral cube <http://spectral-cube.readthedocs.org>" (Software)
- **pvextractor** : position-velocity diagrams  
  > "pvextractor <http://pvextractor.readthedocs.org>" (Software)
- **dust_emissivity** : listed software (dust mass)  
  > "`dust_emissivity` <http://dust_emissivity.readthedocs.org>" (Software)

## Numeric results

| quantity | value | uncertainty | units | step | quote |
|---|---|---|---|---|---|
| Peak T_B toward e2e | 225 | not stated | K | 2 | the peak flux density toward W51 e2e is 0.38 Jy, which corresponds to a brightness temperature $T_B=225$ K. |
| Lower-limit luminosity e2e | 2.3e4 | lower limit | Lsun | 2 | $L = 4\pi r^2 \sigma_{sb} T^4 = 2.3\ensuremath{\times 10^{4}} \ensuremath{L_{\odot}}$ |
| Minimum optically thick mass per beam | 18 | not stated | Msun/beam | 2 | the minimum mass per beam to achieve $\tau\geq1$ is $M=18$ $M_{\odot}$ beam$^{-1}$. |
| Number of dendrogram continuum sources | 113 | not stated | dimensionless | 1 | The resulting catalog includes 113 sources. |
| ALMA flux recovery fraction vs BGPS | 30 | 3 | percent | 0 | The recovery fraction is 30$\pm3$% |
| CH3OH LTE temperature in e2e | 200-600 within r<2 arcsec | not stated | K | 3 | $200 < T < 600$ K out to $r<2$($r<10^4$ AU |
| Upper limit Q_lyc e2e | <6e45 | 2-sigma upper limit | s^-1 | 6 | $Q_{\textrm{lyc}}<6\ensuremath{\times 10^{45}}$ $\mathrm{s}^{-1}$ |
| Velocity dispersion FWHM in cores | 5-15 | not stated | km/s | 5 | With velocity dispersions $\sigma_{FWHM}\approx5-15$ km s$^{-1}$ |

## Qualitative findings

- No clear disks or rotation seen at ~1000 AU resolution; no unambiguous infall signature  
  > "We find no direct evidence of disks in the gas kinematic data." (3.6.2)
- All outflows originate from mm sources without cm continuum  
  > "*none* come from radio continuum sources (H II regions)." (3.8 Outflows)

## Claim tuples

- H: Forming high-mass protostars heat large gas volumes | E: CH3OH rotational diagrams and brightness-temperature limits around e2e, e8, North | R: T>100 K out to ~5000 AU | F: Embedded protostars thermally regulate surrounding gas | **supported**
- H: Massive protostars are on the main sequence while accreting | E: Compare dust-luminosity lower limits with cm-derived Q_lyc upper limits | R: L>2e4 Lsun but Q_lyc far below B0.5V | F: Protostars are not on the main sequence; possibly bloated | **supported**
- H: Heating inhibits fragmentation | E: Jeans mass/length analysis and count of compact sources near cores | R: stable at beam scale; few fragments | F: Fragmentation suppressed, consistent with enforced isolation | **partially**

## Reasoning

- Why this data: _not stated_
- Why this method: _not stated_
- Alternative: Quenched H II region rejected mainly due to the spherical symmetry assumption; multiplicity of ~6 Msun stars ruled out  
  > "The main reason to disregard this scenario is the assumption of spherical symmetry" (4.3)
- How they decided it was enough: _not stated_
- Limitation (authors): CH3OH temperatures biased high due to optically thick, self-absorbed low-J lines and unmodeled cold component  
  > "The presence of this unmodeled low-temperature component renders our $\textrm{CH}_3\textrm{OH}$ temperature measurements uncertain, biasing them to be slightly high." (3.4)
- Limitation (authors): Completeness of faint source catalog hard to quantify due to imaging artifacts  
  > "the completeness is difficult or perhaps impossible to measure." (4.6)
- Caveat (inferred, ours): Moment-0 LTE fits ignore line profiles and optical depth
- Caveat (inferred, ours): Lower-limit luminosities rely on beam-filling assumption
- Caveat (inferred, ours): Dendrogram catalog contaminated by sidelobe artifacts
- Caveat (inferred, ours): Distance not stated explicitly

## Reproducibility

- Data public (paper): Reduced images and cubes publicly released; scripts on GitHub  
  > "The reduced images and data cubes used in this paper are publicly available" (Data Release)
- Products in archive: _not stated_
- Code: https://github.com/adamginsburg/W51_ALMA_2013.1.00308.S  
  > "The reduction and analysis scripts are at <https://github.com/adamginsburg/W51_ALMA_2013.1.00308.S>." (Data Release)
- Missing: Exact tclean parameters for main continuum image
- Missing: Rotational diagram fit details
- Missing: Adopted distance
- Data volume (inferred): Several hundred GB to ~1 TB raw (12m+7m mosaics, 4 spectral windows)
- Score (inferred): 4/5, Public data, released scripts and mostly numeric steps; some imaging parameters need scripts.
- Rediscovery candidate: yes, Public data and scripts, quantitative results (T_B, luminosity, recovery fraction, catalog size) can be redone.

## Links

- Method: Rosolowsky2008c (dendrogram source identification)
- Companion: Ginsburg2016b (VLA cm continuum and ionizing radiation in W51)
- Companion: Goddi2016a (NH3/CH3OH velocities and infall in e2)
- Related: BGPS
- Related: Hi-GAL
- Related: VLA 12B-365, 13A-064, 12A-074

## Checks

```json
{
 "quotes": 70,
 "quotes_ok": 70,
 "quote_pass_rate": 1.0,
 "quotes_too_long": 0,
 "unsupported_facts": 0,
 "project_codes": 1,
 "codes_not_in_text": [],
 "codes_not_in_obscore": [],
 "obscore_codes_not_in_card": [],
 "codes_printed_but_missing": [],
 "numeric_results": 8,
 "numeric_problems": 0,
 "fill": {
  "facts": 87,
  "stated": 55,
  "rate": 0.632
 },
 "evidence_ok": true
}
```
