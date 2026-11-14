# Sulphur and carbon isotopes towards Galactic centre clouds

`2020A&A...642A.222H` | Astronomy and Astrophysics 2020 | first author: Humire, P. K. | arXiv: 2009.07306 | DOI: 10.1051/0004-6361/202038216

Card schema 1.0 | model claude-sonnet-5-5 | depth light | type multi_facility_alma_minor

## Science

- Fields: milky_way_ism, astrochemistry
- Question: What are the 32S/34S, 12C/13C and 34S/33S isotope ratios in Galactic centre clouds (+50 km/s Cloud, Sgr B2(N) envelope and line-of-sight clouds), and does the 32S/34S decrease with galactocentric distance continue to the GC?  
  > "We present measurements of the carbon and sulphur abundances in the interstellar medium of the central region of our Galaxy." (abstract)
- Target **+50 km/s Cloud**: coordinates 17h45m50.20s, -28d59m41.1s (J2000)  
  > "The observed position was EQ J2000: 17h45m50.20s, −28◦59′41.1′′ for both telescopes" (2.1 +50 km/s Cloud); z/distance l.o.s. distance 3±3 pc relative to the Galactic centre  
  > "The observed position was EQ J2000: 17h45m50.20s, −28◦59′41.1′′ for both telescopes" (2.1 +50 km/s Cloud); distance from Ferrière 2012  
  > "The observed position was EQ J2000: 17h45m50.20s, −28◦59′41.1′′ for both telescopes" (2.1 +50 km/s Cloud)
- Target **Sgr B2(N) and l.o.s. clouds**: coordinates field centre 17h47m19.87s, -28d22m16s (J2000)  
  > "Sgr B2(N) is located at a galactocentric distance of 130 +60 −30 pc from Sgr A∗ (from Reid et al. 2009" (3. Sources); "assuming a distance to the Galactic centre, Sgr A∗, of 8.122 kpc (Gravity Collaboration et al. 2018)" (2.2 Line-of-sight clouds towards Sgr B2(N)); z/distance 130 +60/-30 pc from Sgr A*; 8.122 kpc to GC  
  > "Sgr B2(N) is located at a galactocentric distance of 130 +60 −30 pc from Sgr A∗ (from Reid et al. 2009" (3. Sources); "assuming a distance to the Galactic centre, Sgr A∗, of 8.122 kpc (Gravity Collaboration et al. 2018)" (2.2 Line-of-sight clouds towards Sgr B2(N)); distance from Reid et al. 2009; Gravity Collaboration et al. 2018  
  > "Sgr B2(N) is located at a galactocentric distance of 130 +60 −30 pc from Sgr A∗ (from Reid et al. 2009" (3. Sources); "assuming a distance to the Galactic centre, Sgr A∗, of 8.122 kpc (Gravity Collaboration et al. 2018)" (2.2 Line-of-sight clouds towards Sgr B2(N))

## Data provenance

- ALMA projects: 2011.0.00017.S, 2012.1.00012.S
- bands: _not stated_
- frequencies and spectral setup: EMoCA survey 84.1–114.4 GHz, 488 kHz resolution (1.7–1.3 km/s)  
  > "The survey covers the frequency range from 84.1 to 114.4 GHz, which includes carbon monosulfide J=2–1 lines, with a spectral resolution of 488 kHz (1.7 to 1.3 km s−1)" (2.2 Line-of-sight clouds towards Sgr B2(N))
- continuum bandwidth: _not stated_
- arrays: _not stated_
- configurations: _not stated_
- baselines: _not stated_
- angular resolution: median 1.6 arcsec (~0.06 pc)  
  > "at a median angular resolution of 1′′.6, or ∼ 0.06 pc" (2.2 Line-of-sight clouds towards Sgr B2(N))
- max recoverable scale: _not stated_
- sensitivity: ~3 mJy/beam per channel  
  > "The average noise level is ∼ 3 mJy beam−1 per channel." (2.2 Line-of-sight clouds towards Sgr B2(N))
- time on source: _not stated_
- observing dates: _not stated_
- pi or archival as stated: _not stated_
- Line: CS J=2–1 (97.9809533 GHz)
- Line: C34S J=2–1 (96.4129549 GHz (ALMA))
- Line: 13CS J=2–1 (92.4943080 GHz)
- Line: 13C34S J=2–1 (90.9260260 GHz)
- Other facility **IRAM 30 m**: J=2–1 and 3–2 CS isotopologue emission spectra of the +50 km/s Cloud  
  > "With the IRAM 30 m telescope, three frequency set-ups were observed with the E090 and E150 receivers" (2.1 +50 km/s Cloud)
- Other facility **APEX 12 m**: J=6–5 lines of C34S and 13CS in the +50 km/s Cloud  
  > "The measurements were conducted simultaneously using the FLASH345 (Klein et al. 2014) receiver connected to the extended FFTS (XFFTS) backend." (2.1 +50 km/s Cloud)
- External data: Weeds-modelled CS isotopologue column densities in Sgr B2(N) absorption  
  > "The synthetic spectra were obtained by Thiel (2019)." (Figure 3 caption) [from Thiel (2019), PhD thesis, University of Bonn]
- External data: Reduced EMoCA ALMA survey data  
  > "Details of the calibration and deconvolution of the data are reported in Belloche et al. (2016, Sect. 2.2)." (2.2 Line-of-sight clouds towards Sgr B2(N)) [from Belloche et al. (2016)]
- External data: Chemical network for sulphur fractionation  
  > "we used the network from Loison et al. (2019)" (4.3 Discussion on the validity of using C32S/C34S as a proxy for 32S/34S) [from Loison et al. (2019)]
- Simulation/model as data: Gas-phase chemical network models of CS fractionation versus cloud age  
  > "To determine the potential fractionation of sulphur, we used the network from Loison et al. (2019)" (4.3 Discussion on the validity of using C32S/C34S as a proxy for 32S/34S)

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
- weighting robust: _not stated_
- uv taper: _not stated_
- cell size: _not stated_
- image size: _not stated_
- masking: _not stated_
- multiscale scales: _not stated_
- continuum subtraction: _not stated_
- line free channels: _not stated_
- primary beam correction: data corrected for primary beam attenuation  
  > "For this work, we corrected the data for primary beam attenuation." (2.2 Line-of-sight clouds towards Sgr B2(N))
- array combination: _not stated_
- smoothing: _not stated_
- final beam: _not stated_
- final rms: _not stated_

### Inherited from earlier work

- ALMA calibration and deconvolution  
  > "Details of the calibration and deconvolution of the data are reported in Belloche et al. (2016, Sect. 2.2)." (2.2 Line-of-sight clouds towards Sgr B2(N)) [from Belloche et al. (2016, Sect. 2.2)]
- Weeds absorption modelling method  
  > "carried out by Thiel (2019) using the EMoCA survey, following the same method as Thiel et al. (2019)." (4.2 Modelling the Sgr B2(N) data) [from Thiel et al. (2019)]

### Not stated but needed to reproduce (our reading)

- ALMA calibration, CASA version and imaging parameters (deferred to Belloche et al. 2016)
- Weeds fit details and Thiel (2019) column densities beyond Table 4
- Baseline-subtraction and line-free windows for IRAM/APEX spectra
- Exact initial conditions and temperatures of chemical models

## Analysis recipe

1. **Reduce single-dish spectra and fit Gaussians**: GILDAS reduction, order-2 baseline, smoothing to 3 km/s; Gaussian fits (single or double for self-absorbed CS) with lmfit  
  > "required minimal flagging, followed by a baseline subtraction of order two." (2.1 +50 km/s Cloud); "They were obtained using a series of Python codes, mainly within the lmfit package" (4.1 Peak opacities and column density ratios in the +50 km/s Cloud)
   - software: GILDAS, lmfit
   - fitting: lmfit minimisation, uncertainties from lmfit  
  > "where the uncertainties were taken directly from the lmfit package (for details see Appendix D)." (4.1 Peak opacities and column density ratios in the +50 km/s Cloud)
   - validation: lmfit compared with GILDAS uncertainties  
  > "We compared the uncertainties from Gildas and lmfit" (Appendix D: Gaussian fitting)
2. **Derive column densities, opacities and isotope ratios in +50 km/s Cloud**: Column densities via Eq. 80 of Mangum & Shirley (2015); 12C/13C from C34S/13C34S; opacities from line-ratio equations at redshifted velocity 63 km/s; 32S/34S via double-isotope and direct 13CS/13C34S  
  > "Our column density values were calculated using Eq. 80 in Mangum & Shirley (2015) assuming a filling factor of unity." (4.1 Peak opacities and column density ratios in the +50 km/s Cloud)
   - parameter: Tex range 9.4–300 K  
  > "we consider an excitation temperature range of 9.4–300 K for our column density computations" (4.1 Peak opacities and column density ratios in the +50 km/s Cloud)
   - assumption: C34S and 13C34S optically thin; equal Tex and beam filling for isotopologues; lines co-spatial  
  > "Generally, the analysis assumes that lines with the same rotational quantum numbers, related to different CS isotopologues, are co-spatial." (4. Results)
   - fitting: _not stated_
   - validation: Consistency of 32S/34S from J=2–1 and J=6–5 and between double-isotope and direct methods  
  > "This agreement within the uncertainties can be taken as another argument in favour of the low opacity of C34S" (4.1.1 A 32S/34S ratio obtained through the double isotope method)
3. **Isotope ratios in Sgr B2(N) absorption**: Use Weeds-modelled column densities at four continuum peaks; compute ratios and unweighted averages  
  > "The resulting unweighted average values of the isotopic ratios are listed in Table 4" (4.2 Modelling the Sgr B2(N) data)
   - software: Weeds
   - assumption: Tex equal to CMB (2.73 K); unit beam filling  
  > "under the assumption that the excitation temperature is equal to the temperature of the cosmic microwave background (2.73 K)" (4.2 Modelling the Sgr B2(N) data)
   - fitting: Weeds fits of column density, line width, centroid velocity (by Thiel 2019)  
  > "The fitted parameters were the column density, line width, and the centroid velocity" (4.2 Modelling the Sgr B2(N) data)
   - validation: _not stated_
4. **Assess CS sulphur fractionation**: Chemical network of Loison et al. (2019) run for the three environments  
  > "we used the network from Loison et al. (2019) in the +50 km s−1 Cloud, the l.o.s. clouds towards Sgr B2(N) and the envelope of Sgr B2(N)" (4.3 Discussion on the validity of using C32S/C34S as a proxy for 32S/34S)
   - parameter: density 1e5 cm-3, CRIR 7e-16 s-1 for +50 Cloud; density 1e4, CRIR 3e-15 s-1 for Sgr B2 regions  
  > "we adopted a density of 10 5 cm −3 and a CRIR of ζ H2 = 7 × 10 −16 s −1" (4.3 Discussion on the validity of using C32S/C34S as a proxy for 32S/34S)
   - fitting: _not stated_
   - validation: _not stated_

## Software

- **GILDAS** : reduction of IRAM/APEX spectra  
  > "The data were reduced with the GILDAS package" (2.1 +50 km/s Cloud)
- **lmfit** : Gaussian line fitting  
  > "mainly within the lmfit package" (4.1 Peak opacities and column density ratios in the +50 km/s Cloud)
- **Weeds** : modelling Sgr B2(N) absorption profiles  
  > "They used the software Weeds (Maret et al. 2011) to model the absorption profiles." (4.2 Modelling the Sgr B2(N) data)
- **RADEX (ndradex)** : Tex vs opacity test  
  > "RADEX (van der Tak et al. 2007), a statistical equilibrium molecular radiative transfer code." (Appendix B: Excitation temperatures)

## Numeric results

| quantity | value | uncertainty | units | step | quote |
|---|---|---|---|---|---|
| 12C/13C in +50 km/s Cloud | 22.1 | +3.3/-2.4 (as printed in text +3/-2.34) | dimensionless | 2 | we derive a 12 C/ 13 C isotopic ratio of 22.1 |
| 32S/34S direct (13CS/13C34S) in +50 km/s Cloud | 16.3 | +2.1/-1.7 | dimensionless | 2 | Using this we obtain a 32S/34S J=2–1 ratio of 16.3 |
| 32S/34S in Sgr B2(N) envelope | 17.9 | ±5.0 | dimensionless | 3 | 17.9 ± 5.0 in the envelope of Sgr B2(N) |
| 32S/34S in l.o.s. clouds towards Sgr B2(N) | 16.3 | ±3.8 | dimensionless | 3 | a 32S/34S isotope ratio of 16.3 ± 3.8 in the GC l.o.s. clouds towards Sgr B2(N) |
| 34S/33S in +50 km/s Cloud | 4.3 | ±0.2 | dimensionless | 2 | We obtain a 34S/33S ratio of 4.3 ± 0.2 |
| 12C/13C in Sgr B2(N) envelope | 27.6 | ±6.5 | dimensionless | 3 | For this envelope we obtain a 12 C/ 13 C ratio of 27.6 ± 6.5. |

## Qualitative findings

- 32S/34S shows no decrease toward the GC down to ~130 pc, unlike 12C/13C, 14N/15N and 18O/17O  
  > "Our result indicates a termination of this tendency at least at a galactocentric distance of 130 +60 −30 pc." (abstract)

## Claim tuples

- H: The decreasing 32S/34S trend with galactocentric distance continues to the GC | E: Measured 32S/34S in the +50 km/s Cloud and Sgr B2(N) clouds with IRAM, APEX and ALMA | R: Ratios ~16–18, versus ~5–10 expected from the trend | F: The trend terminates at least at ~130 pc from Sgr A* | **supported**
- H: CS 32S/34S is a good proxy for the elemental ratio | E: Chemical network modelling of fractionation | R: Ratios may be underestimated by ≲10–15% | F: Fractionation is small | **supported**

## Reasoning

- Why this data: _not stated_
- Why this method: _not stated_
- How they decided it was enough: _not stated_
- Limitation (authors): Locations of the l.o.s. clouds are poorly constrained  
  > "The exact locations of the different velocity components of the l.o.s. clouds towards Sgr B2(N) are not yet fully constrained." (3. Sources)
- Caveat (inferred, ours): ALMA part relies on unpublished thesis Weeds modelling
- Caveat (inferred, ours): Averages of few components with unweighted scatter
- Caveat (inferred, ours): Single-position single-dish beams mix gas components

## Reproducibility

- Data public (paper): ALMA data available in the archive  
  > "The interferometric data are available in the ALMA archive at https://almascience.eso.org/aq/." (Acknowledgements)
- Products in archive: _not stated_
- Missing: Thiel (2019) Weeds models
- Missing: IRAM/APEX raw data availability
- Data volume (inferred): Large for EMoCA full survey (hundreds of GB); small for a single-field cube subset
- Score (inferred): 3/5, ALMA part inherited from EMoCA and thesis modelling; single-dish data not public; analysis equations given.
- Rediscovery candidate: no, Key ALMA results depend on Weeds modelling from an unpublished thesis and single-dish data.

## Links

- Method: Belloche et al. (2016) (EMoCA survey calibration and deconvolution)
- Method: Thiel et al. (2019) (Weeds absorption modelling method)
- Method: Mangum & Shirley (2015) (column density formula)
- Companion: Loison et al. (2019) (sulphur fractionation network)
- Related: EMoCA

## Checks

```json
{
 "quotes": 58,
 "quotes_ok": 58,
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
  "facts": 76,
  "stated": 38,
  "rate": 0.5
 },
 "evidence_ok": true
}
```
