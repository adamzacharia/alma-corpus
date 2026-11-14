# Deep and narrow CO absorption revealing molecular clouds in the Hydra-A brightest cluster galaxy

`2019MNRAS.485..229R` | Monthly Notices of the Royal Astronomical Society 2019 | first author: Rose, Tom | arXiv: 1902.01863 | DOI: 10.1093/mnras/stz406

Card schema 1.0 | model claude-sonnet-5-5 | depth full | type observational_alma_primary

## Science

- Fields: galaxy_clusters_and_sz, agn_and_quasars, nearby_galaxies
- Question: Are there cold molecular gas clouds along the line of sight to the Hydra-A mm-continuum core, and what are their kinematics, temperature and column densities (as a test of chaotic cold accretion)?  
  > "reveal the existence of cold, molecular gas clouds along the line-of-sight to the galaxy’s extremely bright and compact mm-continuum source." (abstract)
- Target **Hydra-A BCG (3C218)**: coordinates RA 09h18m05.65s, dec. -12d05m44.0s (J2000)  
  > "located at RA 09h18m05.65s, dec. $-12^{\circ}05^{\prime}44.0^{\prime\prime}$ (J2000)" (3 Observations); "This redshift is calculated from MUSE observations (ID: 094.A-0859) and corresponds to a recession velocity of 16294 km s$^{-1}$." (1 Introduction); z/distance z = 0.0543519; D_L = 242.4 Mpc  
  > "located at RA 09h18m05.65s, dec. $-12^{\circ}05^{\prime}44.0^{\prime\prime}$ (J2000)" (3 Observations); "This redshift is calculated from MUSE observations (ID: 094.A-0859) and corresponds to a recession velocity of 16294 km s$^{-1}$." (1 Introduction); distance from MUSE stellar redshift (ID 094.A-0859)  
  > "located at RA 09h18m05.65s, dec. $-12^{\circ}05^{\prime}44.0^{\prime\prime}$ (J2000)" (3 Observations); "This redshift is calculated from MUSE observations (ID: 094.A-0859) and corresponds to a recession velocity of 16294 km s$^{-1}$." (1 Introduction)

## Data provenance

- ALMA projects: 2016.1.01214.S, 2017.1.00629.S
- bands: Band 6 (CO 2-1) and Band 3 (CO 1-0)  
  > "was observed over two ALMA cycles in bands 3 and 6." (3 Observations)
- frequencies and spectral setup: Central 218.55 GHz and 109.33 GHz; channel width 977 kHz (1.3 and 2.7 km/s)  
  > "Central frequency / GHz | 218.55 | 109.33" (Table 1)
- continuum bandwidth: _not stated_
- arrays: _not stated_
- configurations: _not stated_
- baselines: Maximum spacing 1.1 km (CO 2-1), 0.16 km (CO 1-0)  
  > "Maximum spacing / km | 1.1 | 0.16" (Table 1)
- angular resolution: 0.19 arcsec (CO 2-1); 1.63 arcsec (CO 1-0)  
  > "Angular resolution / arcsec | 0.19 | 1.63" (Table 1)
- max recoverable scale: _not stated_
- sensitivity: RMS per channel 1.4 mJy (CO 2-1), 0.7 mJy (CO 1-0)  
  > "RMS noise per channel / mJy | 1.4 | 0.7" (Table 1)
- time on source: 2700 s for each line  
  > "Integration time / s | 2700 | 2700" (Table 1)
- observing dates: 2016 Oct 23 (CO 2-1, Cycle 4); 2018 Jul 18 (CO 1-0, Cycle 5)  
  > "The CO(1-0) observations were taken on 2018 July 18 during ALMA Cycle 5, using band 3." (3 Observations)
- pi or archival as stated: _not stated_
- Line: CO J=1-0 (not stated)
- Line: CO J=2-1 (not stated)
- Other facility **MUSE**: Stellar redshift used as velocity zero point  
  > "This redshift is calculated from MUSE observations (ID: 094.A-0859)" (1 Introduction)
- Other facility **HST**: F814 image for overlay  
  > "overlaid onto the HST F814 image of Fig. [1]" (4 Dynamics of the cold gas disc)
- Other facility **JVLA**: Radio dataset for Fig. 1  
  > "providing the JVLA dataset used in Fig. [1]" (Acknowledgements)
- External data: HI absorption profile toward core (VLBA) compared with CO  
  > "warmer atomic gas has also been detected in Hydra-A with the *Very Long Baseline Array* (VLBA) telescope (cite: Taylor1996)." (6 Cold, Clumpy Gas Clouds) [from (cite: Taylor1996)]
- External data: X-ray H2 column density 3.5±0.3e22 cm-2  
  > "They find a value of $N_{ \textnormal{H}_{2}} = 3.5\pm 0.3 \times 10^{22}$ cm$^{-2}$" (7 Temperature and Column Density Derivations) [from (cite: Russell2013)]
- External data: IRAM 30m molecular mass 2.26±0.29e9 Msun  
  > "$M_{\text{mol}}=2.26 \pm 0.29\times 10^{9}$ $M_{\odot}$ found from *Institut de RadioAstronomie Millimétrique* (IRAM) 30m observations" (5 Molecular Gas Mass of the Disc) [from (cite: Hamer2013)]

## Processing

### Calibration

- pipeline or manual: _not stated_
- casa version: CASA 5.1.1  
  > "The data were calibrated using `CASA` version 5.1.1" (3 Observations)
- pipeline version: _not stated_
- archive products used as is: Calibrated data produced by the ALMA observatory  
  > "For each of the observed CO lines, the calibrated data were produced by the ALMA observatory." (3 Observations)
- flux calibrator: _not stated_
- flux scale uncertainty: _not stated_
- self calibration: _not stated_

### Imaging

- task: _not stated_
- deconvolver: _not stated_
- weighting robust: _not stated_
- uv taper: _not stated_
- cell size: _not stated_
- image size: _not stated_
- masking: _not stated_
- multiscale scales: _not stated_
- continuum subtraction: Performed after delivery; details not given  
  > "we performed the necessary continuum subtractions and made channel maps at velocity resolutions to suit our needs." (3 Observations)
- line free channels: _not stated_
- primary beam correction: _not stated_
- array combination: _not stated_
- smoothing: _not stated_
- final beam: _not stated_
- final rms: _not stated_

### Not stated but needed to reproduce (our reading)

- tclean parameters (weighting, robust, cell, image size, masking)
- line-free channels for continuum subtraction
- flux calibrator and flux scale uncertainty
- whether pipeline or manual calibration
- exact extraction regions (circle radii/positions) for spectra
- continuum flux measurement method
- partition function and Aul values used
- pixel/beam used for moment maps and clipping

## Analysis recipe

1. **Make moment maps and disc kinematics**: Integrated brightness, velocity and dispersion maps of CO(2-1) with immoments  
  > "Moments maps of the high angular resolution CO(2-1) data, also produced using `CASA`’s `immoments` task" (4 Dynamics of the cold gas disc)
   - software: CASA
   - fitting: _not stated_
   - validation: _not stated_
2. **Molecular gas mass of disc**: Bolatto2013 relation; Monte Carlo of 100000 noise-perturbed spectra, double-Gaussian chi2 fit to get SCOdv  
  > "100 000 simulated spectra are created based upon the observed spectrum." (5 Molecular Gas Mass of the Disc)
   - parameter: F21 = 3.2, F10 = 1; rms from line-free range outside -600 to +600 km/s  
  > "For CO(1-0), $F_{10}=1$ and for CO(2-1) we use a value of $F_{21}=3.2$." (5 Molecular Gas Mass of the Disc)
   - assumption: X_CO = 2e20 cm-2 (K km/s)-1; D_L = 242.4 Mpc  
  > "We use a standard value of $X_{\text{CO}} = 2 \times 10^{20}$ cm$^{-2}$ (K km s$^{-1}$)$^{-1}$" (5 Molecular Gas Mass of the Disc)
   - fitting: chi2 minimisation of double Gaussian; 1sigma from 15.865 and 84.135 percentiles  
  > "for each of the 100 000 spectra produced such a fit is found using $\chi^{2}$ minimisation." (5 Molecular Gas Mass of the Disc)
   - validation: Compared with IRAM 30m mass of Hamer2013  
  > "the masses we find are consistent with the value of $M_{\text{mol}}=2.26 \pm 0.29\times 10^{9}$" (5 Molecular Gas Mass of the Disc)
3. **Remove emission and fit absorption features**: Fit and subtract a Gaussian emission line excluding absorption channels (about -48 to -1 km/s), then triple-Gaussian fit via Monte Carlo  
  > "We find that a triple-Gaussian line provides the best fit to the absorption features" (6 Cold, Clumpy Gas Clouds)
   - parameter: Mask limits scanned between -55±10 and +5±10 km/s; choose lowest reduced chi2 of flat-line fit  
  > "The selected range produces a spectrum with the lowest $\chi^{2}_{\nu}$ value when the non-masked region is fitted to a flat line after the removal of the emission." (6 Cold, Clumpy Gas Clouds)
   - assumption: Filling factor of 1 (lower limit on tau); tau_a = ln(I0/Iobs) equals tau  
  > "We assume a filling factor of 1, so our calculations provide a lower limit on the optical depths of the absorbing regions." (6 Cold, Clumpy Gas Clouds)
   - fitting: Monte Carlo with 100000 simulated spectra  
  > "we estimate the properties of these emission lines using an appropriately modified version of the Monte Carlo method" (6 Cold, Clumpy Gas Clouds)
   - validation: _not stated_
4. **Excitation temperature and column densities**: Ratio of velocity-integrated tau of CO(2-1) and CO(1-0) for optically thin LTE gas, solved numerically with Monte Carlo; then N_CO and N_H2  
  > "We then use Eq. [\[eq:opacityratio\]] to calculate $T_\textnormal{ex}$ numerically and find a cloud excitation temperature" (7 Temperature and Column Density Derivations)
   - parameter: Spectra from larger circle matching CO(1-0) beam; single Gaussian fit per line  
  > "the optical depth integrals are estimated using a single Gaussian fit to each line" (7 Temperature and Column Density Derivations)
   - assumption: CO/H2 = 3.2e-4 (Milky Way gas-phase carbon, all in CO); optically thin LTE  
  > "there is a conversion factor of CO/H$_{2}=3.2\times 10^{-4}$" (7 Temperature and Column Density Derivations)
   - fitting: _not stated_
   - validation: N_H2 compared with X-ray value of Russell2013, which is larger since it probes all gas  
  > "many times larger than our estimated value." (7 Temperature and Column Density Derivations)

## Software

- **CASA** 5.1.1: Calibration by ALMA, continuum subtraction, channel maps, immoments  
  > "The data were calibrated using `CASA` version 5.1.1" (3 Observations)
- **APLpy** : Plotting  
  > "This research made use of APLpy, an open-source plotting package for Python" (Acknowledgements)

## Numeric results

| quantity | value | uncertainty | units | step | quote |
|---|---|---|---|---|---|
| Molecular mass from CO(1-0) | 1.06e9 | +0.02/-0.02 (e9) | Msun | 2 | we find an estimated mass of $M_{\text{mol}}=1.06^{+0.02}_{-0.02}\times 10^{9}$ $\text{M}_{\odot}$ |
| Molecular mass from CO(2-1) | 5.6e9 | +0.1/-0.1 (e9) | Msun | 2 | we estimate a mass of $M_{\text{mol}}=5.6^{+0.1}_{-0.1}\times 10^{9}$ $M_{\odot}$ |
| Peak CO(2-1) optical depth, region A | 0.88 | +0.06/-0.06 | dimensionless | 3 | / A / -42.8 $^{+0.1}_{-0.1}$ / -33$^{+2}_{-2}$ / 4.4 $^{+0.3}_{-0.3}$ / 0.88$^{+0.06}_{-0.06}$ / |
| Region A FWHM | 4.4 | +0.3/-0.3 | km/s | 3 | / A / -42.8 $^{+0.1}_{-0.1}$ / -33$^{+2}_{-2}$ / 4.4 $^{+0.3}_{-0.3}$ / 0.88$^{+0.06}_{-0.06}$ / |
| Excitation temperature, region A | 42 | +25/-11 | K | 4 | find a cloud excitation temperature of $T_\textnormal{ex} = 42^{+25}_{-11}$ K |
| CO column density | 2e17 | +3/-1 (e17) | cm-2 | 4 | $N_{ \textnormal{CO}}=2^{+3}_{-1}\times 10 ^{17}\textnormal{cm}^{-2}$ |
| H2 column density | 7e20 | +10/-4 (e20) | cm-2 | 4 | $N_{ \textnormal{H}_{2}  }=7^{+10}_{-4}\times 10 ^{20}\textnormal{cm}^{-2}$ |
| Disc velocity gradient | ~140 | not stated | km/s/kpc | 1 | average line-of-sight velocity gradient of ${\sim}$140 km s$^{-1}$ kpc$^{-1}$ |

## Qualitative findings

- Absorbing clouds lie near the line-of-sight velocity centre, not infalling at 200-300 km/s as in NGC 5044 and A2597; likely on low-ellipticity orbits at up to ~200 pc  
  > "This implies that clouds are not yet falling within the black hole’s influence region ($< 10$ pc), but drifting in the turbulent field at up to $\sim 200$ pc." (8 Discussion)

## Claim tuples

- H: Cold molecular clouds exist along the line of sight to the Hydra-A core | E: CO(2-1) spectrum toward the unresolved mm-continuum source | R: Three absorption regions at -43 to -4 km/s; region A tau=0.88, FWHM 4.4 km/s | F: Narrowest and deepest CO absorption found in a BCG | **supported**
- H: Gas temperature and column density can be derived from CO line ratio | E: Monte Carlo on CO(1-0) and CO(2-1) tau integrals | R: Tex=42 K, N_CO=2e17, N_H2=7e20 | F: Cold, moderate column cloud | **supported**
- H: Clouds are consistent with clumpy cold accretion rather than Bondi accretion | E: Compare CO and HI absorption and kinematics | R: Clumpy spatially coincident molecular and atomic clouds | F: Argues against Bondi accretion, favours chaotic cold accretion | **partially**

## Reasoning

- Why this data: Hydra-A is an extremely strong mm source and has abundant gas, making absorption detection likely  
  > "This makes it an ideal backlight against which to observe molecular absorption." (1 Introduction)
- Why this method: _not stated_
- Alternative: Slightly blueshifted velocities could instead be due to a bar  
  > "it is also possible that the slightly blueshifted velocities seen could be due to a bar" (6 Cold, Clumpy Gas Clouds)
- How they decided it was enough: _not stated_
- Limitation (authors): Mass may differ by up to an order of magnitude due to X-factor and F_ul uncertainty  
  > "the molecular mass may differ from the estimated values by as much as an order of magnitude" (5 Molecular Gas Mass of the Disc)
- Limitation (authors): Filling factor of 1 gives lower limit on tau; velocities are only apparent line-of-sight motions  
  > "these are simply apparent motions along the line-of-sight" (6 Cold, Clumpy Gas Clouds)
- Caveat (inferred, ours): CO(1-0) and CO(2-1) masses differ by factor ~5, suggesting F21 or excitation assumption problems
- Caveat (inferred, ours): Temperature uses a CO(1-0) beam much larger than the continuum source, so emission/absorption beam mismatch may bias tau ratio
- Caveat (inferred, ours): Zero velocity reference ambiguous (stellar vs emission centre)
- Caveat (inferred, ours): Single line of sight; a random snapshot

## Reproducibility

- Data public (paper): Project codes cited; archival data presumably public but no statement  
  > "This paper makes use of the following ALMA data: ADS/JAO.ALMA#2016.1.01214.S, ADS/JAO.ALMA#2017.1.00629.S." (Acknowledgements)
- Products in archive: _not stated_
- Missing: Imaging parameters and extraction regions
- Missing: Continuum subtraction channel selection
- Missing: Partition function and Einstein A values
- Missing: Exact Monte Carlo implementation
- Data volume (inferred): ~20-60 GB for two single-pointing, 45-min datasets (raw)
- Score (inferred): 3/5, Data identified and analysis described in equations, but imaging and region details are missing.
- Rediscovery candidate: yes, Public archival data, simple Gaussian-fit Monte Carlo recipe, numeric results (tau, Tex, N).

## Links

- Method: (cite: Bolatto2013) (CO-to-H2 mass relation)
- Method: (cite: Savage1991) (apparent optical depth)
- Companion: (cite: Hamer2013) (previous CO and H2 observations of Hydra-A)
- Companion: (cite: David2014) (NGC 5044 CO absorption comparison)
- Companion: (cite: Tremblay2016) (Abell 2597 CO absorption comparison)
- Related: Rose et al. in preparation ALMA Cycle 5 CO(1-0) sample of 21 sources
- Related: Cycle 6 ALMA follow-up of Hydra-A

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
 "numeric_results": 8,
 "numeric_problems": 0,
 "fill": {
  "facts": 73,
  "stated": 42,
  "rate": 0.575
 },
 "evidence_ok": true
}
```
