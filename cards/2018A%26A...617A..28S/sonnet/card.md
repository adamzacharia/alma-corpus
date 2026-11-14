# Chemistry in disks. XI. Sulfur-bearing species as tracers of protoplanetary disk physics and chemistry: the DM Tau case

`2018A&A...617A..28S` | Astronomy and Astrophysics 2018 | first author: Semenov, D. | arXiv: 1806.07707 | DOI: 10.1051/0004-6361/201832980

Card schema 1.0 | model claude-sonnet-5-5 | depth full | type observational_alma_primary

## Science

- Fields: protoplanetary_disks, astrochemistry
- Question: What are the sulfur-bearing molecule abundances in the DM Tau disk, and how sensitive is sulfur chemistry to physical and chemical conditions (e.g. C/O)?  
  > "We combine observations and chemical models to constrain the sulfur abundances and their sensitivity to physical and chemical conditions in the DM Tau protoplanetary disk." (abstract)
- Target **DM Tau**: coordinates RA 04h33m48.747s, Dec +18d10m09.585s (J2000)  
  > "The phase tracking center was $\alpha_{J2000} = 04\rm^{h} 33\rm^{m}48.747s$, $\delta_{J2000} = 18\ensuremath{^\circ} 10\ensuremath{'} 09.585\ensuremath{''}$." (2 Observations); "a distance of 140 pc, and a stellar mass of $0.55M_{\ensuremath{\odot}}$" (Line imaging); z/distance 140 pc  
  > "The phase tracking center was $\alpha_{J2000} = 04\rm^{h} 33\rm^{m}48.747s$, $\delta_{J2000} = 18\ensuremath{^\circ} 10\ensuremath{'} 09.585\ensuremath{''}$." (2 Observations); "a distance of 140 pc, and a stellar mass of $0.55M_{\ensuremath{\odot}}$" (Line imaging); distance from _not stated_

## Data provenance

- ALMA projects: 2015.1.00296.S
- bands: Band 4 and Band 6  
  > "Observations of DM Tau were carried out with ALMA at June 22 (in Band 6) and July 26, 2016 (in Band 4)" (2 Observations)
- frequencies and spectral setup: Band 4: six spws of 480 channels, 122.07 kHz width, 145.926-159.010 GHz, plus 2 GHz continuum spw at 145.021 GHz; Band 6: three spws of 240 channels, 244.141 kHz, 215.195-218.936 GHz, plus continuum spw at 232.012 GHz  
  > "The Band 6 spectral setup consisted of three spectral windows with 240 channels each with a channel width of 244.141 kHz ($\sim 0.3$ km s$^{-1}$)" (2 Observations)
- continuum bandwidth: _not stated_
- arrays: _not stated_
- configurations: _not stated_
- baselines: Band 4: 15.1 m to 1.1 km (45 antennas); Band 6: 15.1 m to 704.1 m (37 antennas)  
  > "The Band 6 data were taken with 37 antennas and baselines from 15.1 m up to 704.1 m with an on source time of about 20 min" (2 Observations)
- angular resolution: ~0.6" x 0.5" for lines; 0.61" x 0.58" for 145 GHz continuum  
  > "For the line images at the Band 4 and 6 the synthesized beams are similar, $\approx 0.6\ensuremath{''} \times 0.5\ensuremath{''}$" (2 Observations)
- max recoverable scale: _not stated_
- sensitivity: line 1 sigma rms 5e-3 Jy/beam at ~0.3 km/s; continuum 7.6e-5 Jy/beam  
  > "the spectral resolution of $\sim 0.3$ km s$^{-1}$ and the $1~\sigma$ rms sensitivity of $5 \times 10^{-3}$ Jy beam$^{-1}$" (2 Observations)
- time on source: Band 4 ~2 min; Band 6 ~20 min  
  > "Band 4 data were taken with 45 antennas and baselines from 15.1 m up to 1.1 km with an on source time of about 2 min." (2 Observations)
- observing dates: 22 June 2016 (Band 6), 26 July 2016 (Band 4)  
  > "Observations of DM Tau were carried out with ALMA at June 22 (in Band 6) and July 26, 2016 (in Band 4)" (2 Observations)
- pi or archival as stated: PI: Dmitry Semenov (own Cycle 3 program)  
  > "as part of the ALMA project 2015.1.00296.S, PI: Dmitry Semenov." (2 Observations)
- Line: CS 3-2 (146.96903 GHz)
- Line: SO2 3(2,2)-3(1,3) (158.19974 GHz)
- Line: H2S 2(2,0)-2(1,1) (216.71044 GHz)
- Other facility **IRAM 30-m**: previous CS (3-2) data merged with ALMA in DiskFit  
  > "the ALMA data were merged with our previous CS (3-2) IRAM 30-m data (cite: 2011A&A...535A.104D)" (Parametric fitting with DiskFit)
- External data: Previous IRAM 30-m CS (3-2) data  
  > "the ALMA data were merged with our previous CS (3-2) IRAM 30-m data (cite: 2011A&A...535A.104D)" (Parametric fitting with DiskFit) [from (cite: 2011A&A...535A.104D)]
- External data: Local line width 0.14 km/s from previous CS observations  
  > "A local line width of 0.14 km s$^{-1}$ was assumed for all molecules based on the previous CS observations by (cite: 2012A&A...548A..70G)." (Fitting with RADEX) [from (cite: 2012A&A...548A..70G)]
- External data: Molecular collisional data from LAMDA  
  > "The molecular data were taken from the Leiden Atomic and Molecular Database (LAMDA)[^4], see (cite: Schoier2005)." (Fitting with RADEX) [from (cite: Schoier2005)]
- Simulation/model as data: About 20 chemical calculations with the ALCHEMIC code on a 1+1D DM Tau disk model, varying Sc, grain size, Ediff/Ebind, S abundance, Lx, UV, CRP, C/O  
  > "we performed about 20 detailed chemical calculations by varying various physical and chemical parameters as shown in Table [\[tabruns\]](#tabruns)." (Results)

## Processing

### Calibration

- pipeline or manual: _not stated_
- casa version: CASA 4.5.3  
  > "through the Common Astronomy Software Applications (CASA) software (cite: McMullin_ea07), version 4.5.3." (2 Observations)
- pipeline version: _not stated_
- archive products used as is: _not stated_
- flux calibrator: J0510+1800 (Band 4 and 6)  
  > "The quasars J0510+1800 and J0431+2037 were used as bandpass, flux, and phase calibrators." (2 Observations)
- flux scale uncertainty: _not stated_
- self calibration: 145.021 GHz continuum self-calibrated; solutions applied to Band 4 lines  
  > "The continuum image at 145.021 GHz was self-calibrated, and the solutions were applied to the lines observed in Band 4" (2 Observations)

### Imaging

- task: _not stated_
- deconvolver: _not stated_
- weighting robust: natural weighting  
  > "the Bands 4 and 6 data were cleaned using the “natural” weighting." (2 Observations)
- uv taper: _not stated_
- cell size: _not stated_
- image size: _not stated_
- masking: _not stated_
- multiscale scales: _not stated_
- continuum subtraction: performed in uv-space with CASA  
  > "Data reduction and continuum subtraction in the $uv$-space were performed through the Common Astronomy Software Applications (CASA)" (2 Observations)
- line free channels: _not stated_
- primary beam correction: neglected for the ~4" source  
  > "Neglecting the primary beam correction, which is justified for our $\sim 4\ensuremath{''}$ emission source" (Parametric fitting with DiskFit)
- array combination: _not stated_
- smoothing: _not stated_
- final beam: 0.61" x 0.58", PA ~28 deg (145 GHz continuum)  
  > "The resulting synthesized beam size is $0.61\ensuremath{''} \times 0.58\ensuremath{''}$ at a positional angle of $\sim 28\ensuremath{^\circ}$" (2 Observations)
- final rms: 7.6e-5 Jy/beam continuum; 5e-3 Jy/beam lines  
  > "with the $1~\sigma$ rms of $7.6 \times 10^{-5}$ Jy beam$^{-1}$" (2 Observations)

### Inherited from earlier work

- Pixel deprojection and azimuthal averaging technique  
  > "we applied the pixel deprojection and azimuthal averaging technique as presented in (cite: 2016A&A...592A..49T), (cite: Yen_ea_16), and (cite: Matra_ea17)." (Line imaging) [from (cite: 2016A&A...592A..49T), (cite: Yen_ea_16), (cite: Matra_ea17)]
- DiskFit parametric method  
  > "our DiskFit parametric method (cite: Pietu_ea07; 2011A&A...535A.104D; Teague:2015jk)" (Parametric fitting with DiskFit) [from (cite: Pietu_ea07; 2011A&A...535A.104D; Teague:2015jk)]
- RADEX disk-averaged column density approach  
  > "we decided to start with a simple approach based on (cite: 2012A&A...544L...9F; Fedele_ea13a)" (Fitting with RADEX) [from (cite: 2012A&A...544L...9F; Fedele_ea13a)]
- Disk physical model and chemical code  
  > "The DM Tau physical disk model is based on a 1+1D steady-state $\alpha$-model similar to that of (cite: DAea99)" (Disk physical structure) [from (cite: DAea99); (cite: Semenov_ea10; SW2011)]

### Not stated but needed to reproduce (our reading)

- Continuum self-calibration solint and number of iterations
- Line-free channels and continuum fit order for uv continuum subtraction
- Clean threshold, cell and image size
- Velocity-channel stacking details for SO, SO2, OCS pairs
- DiskFit priors and MCMC settings
- Flux calibrator flux values and ALMA data processing script
- Exact definition of median column density comparison and chemical model run grid (Table tabruns details)

## Analysis recipe

1. **Calibrate and image**: CASA reduction, uv continuum subtraction, natural weighting; Band 4 self-calibration  
  > "the Bands 4 and 6 data were cleaned using the “natural” weighting." (2 Observations)
   - software: CASA
   - fitting: _not stated_
   - validation: _not stated_
2. **Deproject and stack spectra**: Pixel deprojection and azimuthal averaging; stacking of transition pairs  
  > "For deprojection we used a inclination angle of $-34\ensuremath{^\circ}$, a positional angle of $27\ensuremath{^\circ}$, a distance of 140 pc" (Line imaging)
   - parameter: i = -34 deg, PA = 27 deg, d = 140 pc, M* = 0.55 Msun  
  > "a distance of 140 pc, and a stellar mass of $0.55M_{\ensuremath{\odot}}$" (Line imaging)
   - fitting: _not stated_
   - validation: _not stated_
3. **Disk-averaged column densities with RADEX**: Gaussian fit of integrated spectra in GILDAS; chi2 minimization over Tex, n, N with RADEX LVG  
  > "By varying excitation temperature, volume density, and column density, the $\chi^{2}$ values between the observed and modeled CS line fluxes were computed and minimized." (Fitting with RADEX)
   - software: GILDAS, RADEX
   - parameter: source diameter 4" (560 au); line width 0.14 km/s; n = 1e6, 1e7, 1e8 cm-3; upper limits from 3 sigma  
  > "The resulting $\chi^{2}$ distributions for the assumed volume densities of $10^{6}$, $10^{7}$, and $10^{8}$ cm$^{-3}$" (Fitting with RADEX)
   - fitting: chi2 minimization  
  > "By varying excitation temperature, volume density, and column density, the $\chi^{2}$ values between the observed and modeled CS line fluxes were computed and minimized." (Fitting with RADEX)
   - validation: _not stated_
4. **Radial column densities with DiskFit**: Power-law parametric fit of visibilities (chi2 + MCMC), ALMA merged with IRAM CS; upper limits use CS temperature and profiles  
  > "which are fitted with a combination of $\chi^2$ minimization and MCMC of the observed visibilities in the $uv$-plane." (Parametric fitting with DiskFit)
   - software: DiskFit
   - fitting: chi2 + MCMC in uv-plane  
  > "which are fitted with a combination of $\chi^2$ minimization and MCMC of the observed visibilities in the $uv$-plane" (Parametric fitting with DiskFit)
   - validation: Compared with RADEX results  
  > "while the CS column densities derived by both methods are comparable, $\sim 2-6\,10^{12}$ cm$^{-2}$" (Parametric fitting with DiskFit)
5. **Chemical modeling and comparison**: ALCHEMIC gas-grain chemistry on 1+1D disk model, 5 Myr; parameter grid; median column densities at 100-800 au compared with observations  
  > "medians of these column densities were computed at radii between 100 and 800 au and compared with the best-fit disk-averaged quantities derived with RADEX" (Results)
   - software: ALCHEMIC
   - parameter: Mdisk 0.066 Msun, Mdot 5e-9 Msun/yr, alpha 0.01, Rout 800 au, Lx 1e31 erg/s, grain 0.1 um  
  > "an outer radius of $800$ au, an accretion rate of $5\times10^{-9}\mathrm{M}_\odot$ yr$^{-1}$, a viscosity parameter $\alpha = 0.01$" (Disk physical structure)
   - assumption: Equal gas and dust temperatures; gas-to-dust 100  
  > "where equal gas and dust temperatures are assumed" (Disk physical structure)
   - fitting: _not stated_
   - validation: Modeling uncertainties of factor ~3-10 considered  
  > "taking modeling uncertainties of a factor of $\sim 3-10$ into account" (Impact of C/O ratios)

## Software

- **CASA** 4.5.3: reduction, continuum subtraction, imaging  
  > "through the Common Astronomy Software Applications (CASA) software (cite: McMullin_ea07), version 4.5.3." (2 Observations)
- **GILDAS** : Gaussian fits of integrated spectra  
  > "The ALMA data in the CASA format were exported as FITS files and analyzed in GILDAS" (Fitting with RADEX)
- **RADEX** : non-LTE column densities  
  > "we employed a widely used RADEX code[^3] (cite: Radex)." (Fitting with RADEX)
- **DiskFit** : parametric uv-plane fitting  
  > "we performed a more elaborate analysis of the data using our DiskFit parametric method" (Parametric fitting with DiskFit)
- **ALCHEMIC** : gas-grain disk chemistry  
  > "The adopted chemical model is based on the public gas-grain `ALCHEMIC` code" (Disk chemical model)

## Numeric results

| quantity | value | uncertainty | units | step | quote |
|---|---|---|---|---|---|
| CS column density (RADEX) | 1.5-3e12 | not stated | cm^-2 | 3 | / CS           / $\lesssim 100$ / $1.5-3\times10^{12}$ |
| CS column density (DiskFit, r=300 au) | 6e12 | ±3e12 | cm^-2 | 4 | $6\pm3^{a} \times10^{12}$ |
| CS excitation temperature (DiskFit) | 10 | ±2 | K | 4 | $10\pm2$ |
| CS 3-2 integrated flux | 1.1 | 0.3 (3 sigma) | Jy km/s | 3 | / CS / 3-2 / 6.2(0.3) / 1.9(0.6) / 520(100) / 1.1(0.3) / |
| Modeled CS/SO at C/O=1.2 | 282 | not stated | dimensionless | 5 | the modeled CS/SO ratio increases from the “standard” low value of $\approx 0.026$ (C/O $=0.46$) to the values of 13 (C/O $=1.0$) and 282 (C/O $=1.2$) |

## Qualitative findings

- Only CS firmly detected; tentative SO2 detection at peak S/N ~4.7  
  > "There is a tentative detection of the SO$_{2}$ ($3_{2,2}-3_{1,3}$) line, with a peak signal-to-noise ratio $\approx 4.7$" (Line imaging)

## Claim tuples

- H: Does the observed CS/SO ratio require non-solar C/O? | E: Compare RADEX/DiskFit column densities with ~20 chemical models | R: Observed CS/SO >~1 vs modeled ~0.02-0.04 at solar C/O | F: Gas-phase C/O >~1 at r >~50-100 au is required (or low Lx and low S) | **supported**
- H: Are S-bearing species other than CS present in DM Tau? | E: ALMA Band 4/6 line search | R: Only CS detected; upper limits 1e11-1e14 cm-2; tentative SO2 | F: Dearth of reactive gas-phase sulfur | **supported**

## Reasoning

- Why this data: _not stated_
- Why this method: _not stated_
- Alternative: Turbulent mixing, S abundance, grain growth, CRP and UV do not raise CS/SO enough; low Lx 1e29 plus low S is an alternative but Lx seems too low  
  > "the best-fit stellar X-ray luminosity of $10^{29}$ erg s$^{-1}$ seems to be to low compared to the observed X-ray properties of DM Tau" (Impact of stellar X-ray luminosity)
- How they decided it was enough: _not stated_
- Limitation (authors): C/O cannot be constrained more accurately due to non-detections and poorly known available sulfur  
  > "We cannot constrain the C/O ratio in the molecular layer more accurately due to the non-detection of SO and SO$_{2}$" (Comparison with previous studies of sulfur chemistry)
- Caveat (inferred, ours): Short Band 4 integration (2 min) gives noisy data
- Caveat (inferred, ours): Single-disk model with fixed physical structure; degeneracies in T and N
- Caveat (inferred, ours): CCS not analyzed in RADEX
- Caveat (inferred, ours): Tentative SO2 detection offset in velocity

## Reproducibility

- Data public (paper): ALMA data acknowledged under project 2015.1.00296.S  
  > "This paper makes use of the following ALMA data: ADS/JAO.ALMA#2015.1.00296.S." (Acknowledgements)
- Products in archive: _not stated_
- Code: ALCHEMIC code is public  
  > "The adopted chemical model is based on the public gas-grain `ALCHEMIC` code[^6]" (Disk chemical model)
- Missing: DiskFit priors/setup
- Missing: self-cal parameters
- Missing: line-free channels
- Missing: full chemical model run grid
- Data volume (inferred): ~10-30 GB
- Score (inferred): 5/5, Public data and RADEX recipe are clear, but DiskFit and imaging details are sparse and the chemical modeling is heavy.
- Rediscovery candidate: no, Key results rely on DiskFit with IRAM data merge and extensive chemical modeling with incomplete detail.

## Links

- Method: (cite: Pietu_ea07) (DiskFit method)
- Method: (cite: 2016A&A...592A..49T) (deprojection and azimuthal averaging)
- Companion: (cite: 2011A&A...535A.104D) (previous IRAM DM Tau sulfur study)

## Checks

```json
{
 "quotes": 65,
 "quotes_ok": 65,
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
  "stated": 51,
  "rate": 0.637
 },
 "evidence_ok": true
}
```
