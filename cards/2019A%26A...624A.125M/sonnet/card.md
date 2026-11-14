# Spatially resolved carbon and oxygen isotopic ratios in NGC 253 using optically thin tracers

`2019A&A...624A.125M` | Astronomy and Astrophysics 2019 | first author: Martín, S. | arXiv: 1903.03244 | DOI: 10.1051/0004-6361/201935106

Card schema 1.0 | model claude-sonnet-5-5 | depth full | type observational_alma_primary

## Science

- Fields: nearby_galaxies, astrochemistry
- Question: What are the spatially resolved carbon and oxygen isotope ratios across the central molecular zone of the starburst NGC 253, derived from optically thin CO isotopologues?  
  > "we spatially resolve the carbon and oxygen isotope ratios across the central molecular zone (full size $\sim 600$ pc) in the nearby starburst galaxy NGC 253." (abstract)
- Target **NGC 253**: coordinates 00h47m33.182s, -25d17m17.148s (J2000)  
  > "Observations consisted of a single pointing at the nominal phase center of $\alpha_{J2000}=00^{\rm h}47^{\rm m}33.182s$, $\delta_{J2000}=-25^\circ17'17.148\ensuremath{''}$." (2 Observations); "At a distance of $\sim3.5$ Mpc (cite: Rekola2005; Mouhcine2005)" (Introduction); z/distance ~3.5 Mpc  
  > "Observations consisted of a single pointing at the nominal phase center of $\alpha_{J2000}=00^{\rm h}47^{\rm m}33.182s$, $\delta_{J2000}=-25^\circ17'17.148\ensuremath{''}$." (2 Observations); "At a distance of $\sim3.5$ Mpc (cite: Rekola2005; Mouhcine2005)" (Introduction); distance from Rekola2005; Mouhcine2005  
  > "Observations consisted of a single pointing at the nominal phase center of $\alpha_{J2000}=00^{\rm h}47^{\rm m}33.182s$, $\delta_{J2000}=-25^\circ17'17.148\ensuremath{''}$." (2 Observations); "At a distance of $\sim3.5$ Mpc (cite: Rekola2005; Mouhcine2005)" (Introduction)

## Data provenance

- ALMA projects: 2016.1.00292.S
- bands: Band 3 (~91-112 GHz), two receiver tunings  
  > "The observations consisted of two different receiver tunings." (2 Observations)
- frequencies and spectral setup: Tuning 1: SPWs at 91.0, 92.8, 102.9, 104.7 GHz; tuning 2: 97.9, 99.6, 110.0, 111.9 GHz; 1.875 GHz each, 0.488 MHz channels  
  > "the spectral windows were configured to cover a bandwidth of 1.875 GHz each with a channel spacing of 0.488 MHz" (2 Observations)
- continuum bandwidth: _not stated_
- arrays: 12 m array, 43-46 antennas  
  > "In all cases, the number of 12 m-antennas in the array was between 43 and 46." (2 Observations)
- configurations: _not stated_
- baselines: 15-460 m (tuning 1); 15-492 m (tuning 2)  
  > "unprojected baselines ranging $15-460$ m ($5.2-160~\rm k\lambda$)" (2 Observations)
- angular resolution: 3'' common circular beam (~50 pc)  
  > "Imaging after cleaning was performed with a common circular synthesized beam of $3''$ (FWHM)" (2 Observations)
- max recoverable scale: ~15'' (tuning 1); 13'' (tuning 2)  
  > "which results in an estimated maximum recoverable scale of $\sim15''$" (2 Observations)
- sensitivity: rms ~1.5 and ~5 mJy/beam (19 and 62 mK) at 10 km/s  
  > "The achieved rms sensitivities in the velocity smoothed cubes were $\sim1.5$ and $\sim5$ mJy beam$^{-1}$" (2 Observations)
- time on source: 170 min (tuning 1); 12 min (tuning 2)  
  > "with a total on-source time of 170 minutes" (2 Observations); "with only 12 minutes of on-source integration" (2 Observations)
- observing dates: Jan 1-3 2017 (tuning 1); Dec 23 2016 (tuning 2)  
  > "was observed on December 23th, 2016" (2 Observations)
- pi or archival as stated: Cycle 4 project, PI S. Martín  
  > "Cycle 4 project 2016.1.00292.S (P.I. S. Martín)" (2 Observations)
- Line: 13C18O J=1-0 (104.711 GHz)
- Line: 13CO J=1-0 (110.201 GHz)
- Line: C18O J=1-0 (109.782 GHz)
- Line: C17O J=1-0 (112.359 GHz)
- Other facility **IRAM 30m**: Single-dish spectra from literature used to estimate missing flux  
  > "equivalent to that of the IRAM 30m telescope at the frequency of the CO isotopologues $J=1-0$ transitions" (3.1.1 Spatial filtering)
- External data: IRAM 30m spectra of four isotopologues at position SD A  
  > "to compare with the spectra from (cite: Aladro2015) of the four observed isotopologues" (3.1.1 Spatial filtering) [from (cite: Aladro2015)]
- External data: 13C18O single-dish profile at position SD B  
  > "to compare with the $\rm ^{13}C^{18}O$  profile reported by (cite: Mart’in2010a)" (3.1.1 Spatial filtering) [from (cite: Mart’in2010a)]
- External data: Spectroscopic parameters from JPL and CDMS catalogs  
  > "By using the spectroscopic information in the JPL and CDMS catalogs (cite: Pickett1998; Muller2001; Muller2005)" (3.2.1) [from (cite: Pickett1998; Muller2001; Muller2005)]

## Processing

### Calibration

- pipeline or manual: _not stated_
- casa version: CASA 4.7.2  
  > "Calibration and imaging was performed in CASA version 4.7.2 (cite: McMullin2007)." (2 Observations)
- pipeline version: _not stated_
- archive products used as is: _not stated_
- flux calibrator: Neptune and J0038-2459; bandpass J0006-0623, gain J0038-2459  
  > "Absolute flux calibration used observations of Neptune and the quasar J0038$-$2459." (2 Observations)
- flux scale uncertainty: <10% between the two setups  
  > "we conservatively estimate an uncertainty $<10\%$ between the two frequency setups." (2 Observations)
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
- continuum subtraction: uvcontsub with line free channels  
  > "The continuum emission was subtracted from the visibilities (with the CASA task uvcontsub) using line free channels." (2 Observations)
- line free channels: _not stated_
- primary beam correction: primary beam corrected cubes used for missing-flux comparison  
  > "we reconstructed our ALMA primary beam corrected cubes with a $\sim23''$ beam" (3.1.1 Spatial filtering)
- array combination: _not stated_
- smoothing: common 10 km/s velocity resolution  
  > "Final datacubes of the individual transitions were smoothed to a common 10 $\rm km\,s^{-1}$ velocity resolution." (2 Observations)
- final beam: common circular 3'' FWHM  
  > "common circular synthesized beam of $3''$ (FWHM)" (2 Observations)
- final rms: ~1.5 and ~5 mJy/beam  
  > "The achieved rms sensitivities in the velocity smoothed cubes were $\sim1.5$ and $\sim5$ mJy beam$^{-1}$" (2 Observations)

### Inherited from earlier work

- Excitation temperature of 15 K based on earlier multi-transition rotational temperatures  
  > "The excitation temperature was fixed to 15 K based on the rotational temperatures derived from multi-transition studies based on previous spectral scans (cite: Mart’in2006)" (3.2.2) [from (cite: Mart’in2006)]
- Single-dish S/T_MB = 5 Jy/K conversion for IRAM 30m  
  > "have been converted to flux density units with a factor of $S/T_{MB}=5$ Jy/K" (3.1.1 Spatial filtering) [from IRAM 30m efficiencies webpage]

### Not stated but needed to reproduce (our reading)

- tclean parameters (deconvolver, robust, masks, cell size, image size, threshold)
- line-free channel ranges for uvcontsub
- whether pipeline or manual calibration was used
- velocity range for map integration beyond 50-450 km/s
- MADCUBA version and the fitting algorithm/priors; MADCUBA paper is in prep
- how fit uncertainties on column densities were propagated

## Analysis recipe

1. **Image and smooth cubes**: Calibrate, uvcontsub, clean to common 3'' beam, smooth to 10 km/s  
  > "Imaging after cleaning was performed with a common circular synthesized beam of $3''$ (FWHM)" (2 Observations)
   - software: CASA
   - fitting: _not stated_
   - validation: _not stated_
2. **Estimate missing flux**: Smooth ALMA cubes to 23'' and compare with IRAM 30m spectra at SD A and SD B  
  > "We extracted the smoothed spectra at the same positions as those from the single dish observations." (3.1.1 Spatial filtering)
   - software: CASA
   - parameter: Velocity range 40-450 km/s  
  > "integrated over the velocity range 40-450 $\rm km\,s^{-1}$" (3.1.1 Spatial filtering)
   - fitting: _not stated_
   - validation: Comparison with Meier2015 recovered flux  
  > "When using the same single dish reference, both (cite: Meier2015) and this work recover the same fluxes." (3.1.1 Spatial filtering)
3. **Line ratio maps**: Integrated maps 50-450 km/s, ratios for pixels >1 sigma; average and std with unweighted, sigma- and snr-weighting  
  > "These ratios have been calculated for pixels where the signal in the integrated maps in the $50-450$ $\rm km\,s^{-1}$ range is $>1\sigma$" (3.1.2 Line ratio maps)
   - fitting: _not stated_
   - validation: Error propagation in appendix  
  > "Fig. [7](#fig.errormapsratios) displays the ratio between the propagated error of the ratio map over the ratio map in percentage" (Appendix: Error and signal to noise in line ratio maps)
4. **Deblend 13C18O from C4H**: Simultaneous Gaussian fits; use C4H 11_12-10_11 lines to estimate contribution of the blended 11_11-10_10 lines using relative intensities; iterate  
  > "$\rm ^{13}C^{18}O$  emission was then fitted after removing the contribution of $\rm C_4H$." (3.2.1)
   - software: MADCUBA
   - fitting: Multi-Gaussian components with velocities fixed to 13CO  
  > "The velocity of the first two were fixed to those of the two components observed in $\rm ^{13}CO$" (3.2.1)
   - validation: Contaminant rest frequencies matched to C4H in JPL/CDMS  
  > "our estimated frequencies agree well with those of the hyperfine transitions of $\rm C_4H$" (3.2.1)
5. **LTE column densities and ratios at 14 positions**: Fit synthetic LTE spectra at selected C18O peak positions; velocity and width fixed to 13CO fit; average column density ratios with three weightings  
  > "With MADCUBA we fit a synthetic spectrum, calculated from input physical parameters and using the molecular spectroscopic parameters in the JPL and CDMS catalogs, to the observed line profiles." (3.2.2)
   - software: MADCUBA
   - parameter: Tex = 15 K; source size 3''  
  > "ii)$ they have a common excitation temperature of $T_{ex}=15~$K, and $iii)$ the source size is $3''$" (3.2.2)
   - assumption: All isotopologues share distribution and velocity profile; column density ratios equal atomic isotopic ratios  
  > "$i)$ all isotopologues have the same distribution, including velocity profile" (3.2.2)
   - fitting: _not stated_
   - validation: Tex 10 and 20 K change column densities by ~5% and ~10%; ratios nearly unchanged  
  > "For temperatures of 10 and 20 K, we estimate column densities $\sim5\%$ and $\sim10\%$ higher, respectively." (3.2.2)

## Software

- **CASA** 4.7.2: Calibration, imaging, uvcontsub  
  > "Calibration and imaging was performed in CASA version 4.7.2" (2 Observations)
- **MADCUBA** : LTE spectral modeling and column density fits  
  > "modeled under the local thermodynamic equilibrium (LTE) assumption using MADCUBA" (3.2.2)

## Numeric results

| quantity | value | uncertainty | units | step | quote |
|---|---|---|---|---|---|
| 12C/13C (sigma-weighted, spectra) | 21 | 6 | dimensionless | 5 | $21\pm6$ |
| 16O/18O (sigma-weighted, spectra) | 130 | 40 | dimensionless | 5 | $130\pm40$ |
| 18O/17O (sigma-weighted, spectra) | 4.5 | 0.8 | dimensionless | 5 | $4.5\pm0.8$ |
| 13CO/C18O (sigma-weighted, spectra) | 6.1 | 0.9 | dimensionless | 5 | $6.1\pm0.9$ |
| ALMA recovered flux of 13CO, C18O, C17O | ~28%, 26%, 29% | not stated | percent | 2 | only $\sim28\%$, $26\%$, and $29\%$ of the $\rm ^{13}CO$, $\rm C^{18}O$, and $\rm C^{17}O$  single dish flux is recovered by our ALMA data |
| C4H contaminant rest frequencies | 104703.3 and 104666.3 MHz | 0.5 MHz | MHz | 4 | which sets the rest frequencies of the contaminating emission at $104703.3\pm0.5$ MHz, and $104666.3\pm0.5$ MHz, respectively. |

## Qualitative findings

- First extragalactic detection of 13C18O; no obvious gradients in ratios within ~300 pc  
  > "This is the first extragalactic detection of the double isotopologue $\rm ^{13}C^{18}O$." (abstract)

## Claim tuples

- H: Do resolved optically thin tracers give lower isotope ratios than single-dish values? | E: Fit LTE spectra at 14 positions with C4H deblending | R: 12C/13C~21, 16O/18O~130, 18O/17O~4.5 | F: Ratios are about a factor of two below those generally adopted for galaxy nuclei | **supported**
- H: Is 18O enhanced relative to the Galactic center? | E: Compare ratios with Galactic center values | R: Lower 16O/18O and higher 18O/17O than Galactic center | F: Extra 18O injection from massive stars | **partially**
- H: Are there multiple gas components with different processing? | E: Compare interferometric ratios with single-dish ratios and missing flux | R: Filtered-out component implies 12C/13C ~50-70 | F: Highly processed compact gas plus less processed extended gas | **partially**

## Reasoning

- Why this data: _not stated_
- Why this method: Optically thin isotopologues minimize optical depth, excitation and photodissociation biases  
  > "one would rather choose the observation of optically thin isotopologues such as $\rm C^{18}O$  and $\rm ^{13}C^{18}O$" (Introduction)
- Alternative: CH3OCH3 rejected as contaminant because other of its transitions are not detected  
  > "which implies that $\rm CH_3OCH_3$ does not contribute significantly to the observed profile" (3.2.1)
- How they decided it was enough: _not stated_
- Limitation (authors): Fractionation not constrained; source size and Tex assumed; 13CO moderately optically thick; missing short spacings  
  > "Since we are not able to provide sensible constraints on fractionation issues in the framework of this paper" (Introduction)
- Caveat (inferred, ours): Single transition per isotopologue forces fixed Tex=15 K and 3'' source size
- Caveat (inferred, ours): Column density ratios may not equal isotopic ratios if fractionation or selective photodissociation are present
- Caveat (inferred, ours): The multicomponent claim relies on the single-dish flux scaling and positional differences
- Caveat (inferred, ours): C4H deblending for faint components is highly uncertain

## Reproducibility

- Data public (paper): Project code given; ALMA data  
  > "This paper makes use of the following ALMA data: ADS/JAO.ALMA#2016.1.00292.S." (Acknowledgements)
- Products in archive: _not stated_
- Missing: tclean settings
- Missing: line-free channels
- Missing: MADCUBA fitting details and version
- Missing: exact velocity integration windows for maps
- Data volume (inferred): ~50-100 GB raw for two Band 3 tunings
- Score (inferred): 3/5, Data are public and the main steps are described, but imaging and fitting settings are missing and MADCUBA is not documented.
- Rediscovery candidate: no, Imaging and MADCUBA fitting details are missing, so the main numbers cannot easily be reproduced exactly.

## Links

- Method: Martín et al in prep (MADCUBA) (LTE fitting tool)
- Companion: (cite: Meier2015) (Previous ALMA interferometric isotopologue study of NGC 253)
- Related: ALCHEMI

## Checks

```json
{
 "quotes": 67,
 "quotes_ok": 67,
 "quote_pass_rate": 1.0,
 "quotes_too_long": 0,
 "unsupported_facts": 0,
 "project_codes": 1,
 "codes_not_in_text": [],
 "codes_not_in_obscore": [],
 "obscore_codes_not_in_card": [],
 "codes_printed_but_missing": [],
 "numeric_results": 6,
 "numeric_problems": 0,
 "fill": {
  "facts": 72,
  "stated": 48,
  "rate": 0.667
 },
 "evidence_ok": true
}
```
