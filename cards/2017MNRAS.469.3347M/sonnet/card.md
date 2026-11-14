# ALMA spectral survey of Supernova 1987A - molecular inventory, chemistry, dynamics and explosive nucleosynthesis

`2017MNRAS.469.3347M` | Monthly Notices of the Royal Astronomical Society 2017 | first author: Matsuura, M. | arXiv: 1704.02324 | DOI: 10.1093/mnras/stx830

Card schema 1.0 | model claude-sonnet-5-5 | depth full | type observational_alma_primary

## Science

- Fields: star_formation, astrochemistry
- Question: Which molecules, isotopologue ratios and kinematics does the ejecta of SN 1987A show in an ALMA 210–360 GHz line survey, and what do they imply for chemistry, mixing and nucleosynthesis?  
  > "We present a molecular line survey of SN 1987A’s ejecta in the 210–300 and 340–360 GHz ALMA spectra, from Cycle-1, Cycle-2 and Cycle-3 observations." (Introduction)
- Target **SN 1987A**: coordinates _not stated_; z/distance 50 kpc (LMC)  
  > "SN1987A is unique. It is located only 50 kpc away." (Introduction); "We adopt an LMC distance of 50$\pm$0.19$\pm$1.11 kpc (cite: Pietrzynski:2013ck)" (4.1 SiO analysis); distance from Pietrzynski et al. 2013 (LMC distance)  
  > "SN1987A is unique. It is located only 50 kpc away." (Introduction); "We adopt an LMC distance of 50$\pm$0.19$\pm$1.11 kpc (cite: Pietrzynski:2013ck)" (4.1 SiO analysis)

## Data provenance

- ALMA projects: 2013.1.00280.S, 2012.1.00075.S, 2013.1.00063.S
- bands: Bands 6 and 7, 210–300 GHz continuous plus 340–360 GHz  
  > "ALMA obtained spectra covering a continuous spectral range from 210 to 300 GHz, using a combination of 10 ALMA ‘Scheduling Blocks’ in bands 6 and 7." (2 Observations and data reduction)
- frequencies and spectral setup: _not stated_
- continuum bandwidth: _not stated_
- arrays: _not stated_
- configurations: _not stated_
- baselines: _not stated_
- angular resolution: fixed circular beam 0.3 arcsec  
  > "The baselines were weighted in order to have a fixed circular beam size (0.3”) across the frequencies." (2 Observations and data reduction)
- max recoverable scale: _not stated_
- sensitivity: requested rms 47–52 µJy, generally achieved  
  > "We requested a root mean square (rms) noise level of 47–52 $\mu$Jy, which was in general achieved." (2 Observations and data reduction)
- time on source: 480–750 s per segment; total observing time 5.6 hours  
  > "The integration time was 480–750 s per segment" (2 Observations and data reduction)
- observing dates: 2014 Aug 29 (band 7), 2014 Sep 2 (band 6), 2014 Aug 18 (CO 2–1), 2015 Jul 25 (CO 3–2, HCO+ 4–3)  
  > "on 2014 August 29th (day 10,048 since the explosion) for part of band 7 (275–298 GHz)" (2 Observations and data reduction)
- pi or archival as stated: PIs Matsuura (Cycle 2) and Indebetouw (Cycles 1 and 3)  
  > "2013.1.00280.S (P.I. Matsuura)" (2 Observations and data reduction)
- Line: SiO J=5–4, 6–5 (217.105, 260.518 GHz)
- Line: CO J=2–1, 3–2 (230.538, 345.796 GHz)
- Line: HCO+ J=3–2 (267.558 GHz)
- Line: SO 5_5–4_4, 5_6–4_5, 6_6–5_5 (215.221, 219.949, 258.256 GHz)
- Other facility **Herschel Space Observatory**: CO J=7–6 and 6–5 fluxes  
  > "together with published Herschel Space Observatory $J$=7–6 and 6–5 measurements" (4.2 CO analysis)
- External data: Herschel CO J=7–6 and 6–5 line fluxes  
  > "together with published Herschel Space Observatory $J$=7–6 and 6–5 measurements (cite: Kamenetzky:2013fv; Matsuura:2015kn)" (4.2 CO analysis) [from Kamenetzky:2013fv; Matsuura:2015kn]
- External data: SiO–H2 collisional data (LAMDA)  
  > "We used SiO Einstein coefficients and SiO–H$_2$ collisional cross-sections from the LAMDA molecular and atomic data base (cite: Schoier:2005ja)" (4.1 SiO analysis) [from Schoier:2005ja]
- External data: CO–H2 collisional data  
  > "We used the collisional cross sections and Einstein coefficients for CO–H$_2$ from (cite: Yang:2010bb)." (4.2 CO analysis) [from Yang:2010bb]
- External data: Nucleosynthesis models and presolar grain Si isotope data for comparison  
  > "The isotope ratios of pre-solar grains are taken from Washington University’s data base (cite: Hynes:2009vp)" (5.4 Isotope ratios) [from Hynes:2009vp; Sukhbold:2016bo]

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

- task: _not stated_
- deconvolver: _not stated_
- weighting robust: baselines weighted to a fixed circular 0.3 arcsec beam; robust not stated  
  > "The baselines were weighted in order to have a fixed circular beam size (0.3”) across the frequencies." (2 Observations and data reduction)
- uv taper: _not stated_
- cell size: _not stated_
- image size: _not stated_
- masking: _not stated_
- multiscale scales: _not stated_
- continuum subtraction: local continuum subtraction  
  > "We measured integrated line intensities after local continuum subtraction" (3.1 ALMA spectrum and molecular identifications)
- line free channels: _not stated_
- primary beam correction: _not stated_
- array combination: _not stated_
- smoothing: spectra smoothed to 345.2 km/s resolution  
  > "yielding a final spectral resolution of 345.2 km s$^{-1}$." (2 Observations and data reduction)
- final beam: _not stated_
- final rms: _not stated_

### Inherited from earlier work

- CO modelling follows earlier method with revised CO 2–1 flux; filling factor definition differs  
  > "The CO models have been revised after (cite: Kamenetzky:2013fv), as the ALMA CO $J=$2–1 line flux has been re-calibrated." (4.2 CO analysis) [from (cite: Kamenetzky:2013fv)]

### Not stated but needed to reproduce (our reading)

- CASA version and calibration steps/calibrators
- robust value, cell and image size, cleaning details
- line-free channels and continuum fitting
- aperture centre coordinates
- how spectral segments were combined
- flux scale uncertainty

## Analysis recipe

1. **extract ejecta spectrum**: spectra extracted from an elliptical aperture 1.29×1.10 arcsec on ejecta; noise from differences of fluxes in four ring apertures (~80% above rms)  
  > "The spectrum was extracted from an ellipse-shaped aperture with long axis of 1.29 arcsec (east-west) and short axis of 1.10 arcsec (north-south), centred on the SN ejecta" (2 Observations and data reduction)
   - software: CASA
   - fitting: _not stated_
   - validation: _not stated_
2. **identify and measure lines**: Gaussian fits after local continuum subtraction; compared with RADEX and LTE SO2 model spectra; 3-sigma upper limits for FWHM 2000 km/s  
  > "We fit the lines with a Gaussian, and their heights, centres and FWHMs are also listed in the table." (3.1 ALMA spectrum and molecular identifications)
   - software: RADEX, HITRAN
   - fitting: Gaussian profiles  
  > "We fit the lines with a Gaussian, and their heights, centres and FWHMs are also listed in the table." (Spectrum and images)
   - validation: model spectra at 40 K compared with observed  
  > "The temperatures of the models are 40 K in this plot." (3.1 ALMA spectrum and molecular identifications)
3. **derive SiO and CO masses**: non-LTE RADEX LVG grids in Tkin and N matched to line ratios (SiO 6–5/5–4; CO 7–6/2–1) and filling factor limits f<0.11 (max 0.45); M=fΩNd²m  
  > "The obtained column density is an ‘averaged’ value within the beam, and is converted to the total molecular mass by $M_{\rm SiO}=f\Omega N_{\rm SiO}  d^2 m$" (4.1 SiO analysis)
   - software: RADEX
   - parameter: n_coll=1e6 cm-3 adopted for SiO (1e5 and 1e4 excluded)  
  > "Thus, we adopted the gas density of the collisional partner of $10^6$ cm$^{-3}$ for the analysis." (4.1 SiO analysis)
   - assumption: distance 50 kpc; H2 collisional partner  
  > "where $d$ is the distance to SN 1987A (50 kpc)" (4.1 SiO analysis)
   - fitting: grid contours, no sampler  
  > "Fig. [4](#fig-sio-ratio) demonstrates the set of ($T_{\rm {kin}}$, $N_{\rm SiO}$) values that match the ALMA measured line ratio" (SiO analysis)
   - validation: _not stated_
4. **masses of HCO+, SO, CS, SiS**: RADEX with Tkin=40 K, n=1e6, filling factor 1, optically thin  
  > "We also fixed the kinetic temperature of the gas to be 40 K because both the $^{12}$CO and $^{28}$SiO modelling gave solutions at this temperature." (4.3 Estimating the masses)
   - software: RADEX
   - assumption: 267 GHz line entirely HCO+  
  > "We assume that the 267 GHz line is due to HCO$^+$ only, with no SO$_2$ contamination" (4.3 Estimating the masses)
   - fitting: _not stated_
   - validation: _not stated_
5. **isotopologue ratios**: optically thin LTE line ratios and RADEX with same Tkin for isotopologues  
  > "We assume that the excitation temperatures of $^{28}$SiO, $^{29}$SiO and $^{30}$SiO are identical." (4.4 Isotopologue ratios)
   - software: RADEX
   - fitting: _not stated_
   - validation: _not stated_
6. **toy line-profile model**: hollow prolate ellipsoid, axis ratio ~2, inner radius 80%, inclination 45°, ballistic expansion with max 1500 km/s, SiO deficient inner 20%, smoothed to 375 km/s  
  > "we assume that the line-emitting region is a hollow, prolate ellipsoid." (4.5 Modelling of the CO and SiO line profiles)
   - fitting: no fit; qualitative comparison  
  > "we have derived normalised line profiles, which are comparable to the observed ones within the uncertainties" (Modelling of the CO and SiO line profiles)
   - validation: compared to observed normalised profiles  
  > "we have derived normalised line profiles, which are comparable to the observed ones within the uncertainties" (4.5 Modelling of the CO and SiO line profiles)

## Software

- **CASA** : data reduction of each setting  
  > "Each setting and observation was reduced individually with the Common Astronomy Software Applications (CASA)" (2 Observations and data reduction)
- **RADEX** : non-LTE LVG excitation modelling  
  > "We analysed the measured line intensities by modelling them with the non-LTE radiative transfer code RADEX" (4 Analysis of the line intensities)

## Numeric results

| quantity | value | uncertainty | units | step | quote |
|---|---|---|---|---|---|
| SiO mass range | 4e-5 to 2e-3 | not stated | Msun | 3 | the resulting SiO mass range is $4\times10^{-5}$–$2\times10^{-3}$ $M_{\odot}$ |
| CO mass range | 0.02 to 1.0 | not stated | Msun | 3 | Our analysis finds a current CO mass of 0.02–1.0 $M_{\odot}$. |
| HCO+ mass | <=5e-6 | upper limit | Msun | 4 | HCO$^+$   / $\leq5\times10^{-6}$ |
| SiS mass | <6e-5 | upper limit | Msun | 4 | SiS       / $<6\times10^{-5}$ |
| 28SiO/29SiO (RADEX, 50 K) | >128 | lower limit | dimensionless | 5 | increases to $^{28}$SiO/$^{29}$SiO$>128$ at 50 K |
| 28SiO/30SiO (RADEX, 50 K) | >188 | lower limit | dimensionless | 5 | increases to $>$188 at 50 K |
| SiO J=6–5/5–4 ratio | 1.54 | +0.3/-0.2 | dimensionless | 3 | ($r=1.54^{+0.3}_{-0.2}$) |
| CO J=2–1 integrated flux | 51.0 | 0.4 (stat), 0.3 (sys) | 1e-20 W m-2 | 2 | CO $J$=2–1 & 230.538 & 51.0&0.4&0.3 |

## Qualitative findings

- SiO line profiles show a central dip while CO does not, implying non-spherical SiO distribution  
  > "The absence of a prominent dip in the CO line profile is compelling evidence that the CO and SiO have different spatial distributions." (6.2 Line profile and geometry)

## Claim tuples

- H: Do SN 1987A ejecta contain molecules beyond CO and SiO? | E: ALMA 210–360 GHz line survey | R: HCO+ and SO detected | F: first identification of HCO+ and SO in a young SNR | **supported**
- H: Are Si neutron-rich isotopes low in SN 1987A? | E: upper limits on 29SiO, 30SiO with RADEX | R: 28Si/29Si>128, 28Si/30Si>188 for Tkin 50 K | F: consistent with low-metallicity nucleosynthesis | **partially**
- H: Is ejecta morphology elongated and do CO and SiO differ? | E: line profile analysis and toy model | R: dip in SiO profiles | F: elongated, non-spherical SiO distribution | **supported**
- H: Does mixing explain large HCO+ and small SiS masses? | E: compare masses with chemical models | R: HCO+ ~5e-6 Msun, SiS <6e-5 Msun | F: some mixing after the explosion plausible | **partially**

## Reasoning

- Why this data: _not stated_
- Why this method: _not stated_
- Alternative: n_coll 1e4 and 1e5 cm-3 excluded for SiO  
  > "a density $10^4$ cm$^{-3}$ can therefore be excluded" (4.1 SiO analysis)
- How they decided it was enough: _not stated_
- Limitation (authors): SiO excitation poorly constrained; more SiO lines needed  
  > "Ill-constrained excitation conditions are the main concern in this current work." (5.4 Isotope ratios)
- Caveat (inferred, ours): Masses depend strongly on assumed Tkin and filling factor
- Caveat (inferred, ours): Collision partner uncertain (O2, SO instead of H2)
- Caveat (inferred, ours): Herschel and ALMA fluxes taken two years apart
- Caveat (inferred, ours): HCO+ blend with SO2

## Reproducibility

- Data public (paper): _not stated_
- Products in archive: _not stated_
- Missing: calibration and imaging parameters
- Missing: aperture position
- Missing: exact RADEX input grids
- Data volume (inferred): ~100 GB raw for three projects
- Score (inferred): 3/5, Archive data and RADEX analysis are clear, but calibration/imaging settings are not given.
- Rediscovery candidate: no, Imaging and calibration recipe incomplete.

## Links

- Method: van der Tak et al. 2007 (RADEX) (non-LTE radiative transfer)
- Companion: Kamenetzky et al. 2013 (Cycle-0 detection of CO and SiO)

## Checks

```json
{
 "quotes": 59,
 "quotes_ok": 59,
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
  "facts": 75,
  "stated": 37,
  "rate": 0.493
 },
 "evidence_ok": true
}
```
