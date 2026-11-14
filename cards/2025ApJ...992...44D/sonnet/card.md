# Revisiting the Gas Dynamics of Henize 2─10: Possible Drivers of the Starburst

`2025ApJ...992...44D` | The Astrophysical Journal 2025 | first author: Dalsin, Josephine M. | arXiv: 2508.06472 | DOI: 10.3847/1538-4357/adf857

Card schema 1.0 | model claude-sonnet-5-5 | depth light | type multi_facility_alma_minor

## Science

- Fields: nearby_galaxies, star_formation
- Question: What drove the starburst in the dwarf galaxy Henize 2-10: a merger or interaction, or internal processes? Tested by comparing the H I and CO gas distribution and kinematics, including the CO 'tail'.  
  > "We also find that the H i appears dynamically decoupled from an extended CO feature (inferred to be a tidal tail in previous work)" (abstract); "We investigate the distribution and kinematics of the molecular and neutral atomic gas to understand the cause of the intense star formation in the dwarf galaxy Henize 2-10." (Summary)
- Target **Henize 2-10**: coordinates Region A: 08:36:15.2, -26:24:34.3 (J2000)  
  > "Henize 2-10 (Hen 2-10) is a nearby (9 Mpc; (cite: Vacca:1992)) starbursting blue compact dwarf (BCD) galaxy" (Case Study: Henize 2-10); "Region A, nominally centered at (RA, Dec.)[^1] = (08:36:15.2, -26:24:34.3)" (Case Study: Henize 2-10); z/distance 9 Mpc  
  > "Henize 2-10 (Hen 2-10) is a nearby (9 Mpc; (cite: Vacca:1992)) starbursting blue compact dwarf (BCD) galaxy" (Case Study: Henize 2-10); "Region A, nominally centered at (RA, Dec.)[^1] = (08:36:15.2, -26:24:34.3)" (Case Study: Henize 2-10); distance from Vacca & Conti 1992  
  > "Henize 2-10 (Hen 2-10) is a nearby (9 Mpc; (cite: Vacca:1992)) starbursting blue compact dwarf (BCD) galaxy" (Case Study: Henize 2-10); "Region A, nominally centered at (RA, Dec.)[^1] = (08:36:15.2, -26:24:34.3)" (Case Study: Henize 2-10)

## Data provenance

- ALMA projects: 2016.1.00027.S
- bands: ALMA Band 3 (115 GHz) 12CO(1-0), archival  
  > "for ALMA Band 3 (115 GHz), it is $\sim$10% (cite: Fomalont:2014)" (Final Data Products)
- frequencies and spectral setup: _not stated_
- continuum bandwidth: _not stated_
- arrays: _not stated_
- configurations: _not stated_
- baselines: _not stated_
- angular resolution: 0.69 x 0.55 arcsec for combined CARMA+ALMA 12CO(1-0) cube  
  > "a 0.69$''$ $\times$ 0.55$''$ beam; we refer to these data as the combined $^{12}$CO(1-0)." (CO Data Reduction)
- max recoverable scale: 112 arcsec (combined CARMA+ALMA 12CO(1-0))  
  > "| 0.69 $\times$ 0.55 | 112 | 1.4$^{a}$ | ... |" (Table 2)
- sensitivity: _not stated_
- time on source: _not stated_
- observing dates: _not stated_
- pi or archival as stated: ALMA data archival, originally presented in Imara & Faesi 2019; CARMA c1274 PI Stierwalt unpublished  
  > "archival ALMA Science Archive (Project Code: 2016.1.00027.S; originally presented in (cite: Imara:2019))" (CO Data Reduction)
- Line: 12CO 1-0 (115.2712 GHz)
- Other facility **VLA**: New 21-cm H I C-array observations (project 21A-198)  
  > "We observed Hen 2-10 with the Karl G. Jansky Very Large Array[^4] (VLA) in C-array at L band (1–2 GHz)." (New VLA HI Observations)
- Other facility **CARMA**: Unpublished 12CO(1-0) and 12CO(2-1) data, project c1274  
  > "We present previously unpublished Combined Array for Research in Millimeter-wave Astronomy (CARMA) data from project c1274 (PI: Stierwalt, S)." (CARMA CO Data)
- Other facility **SMA**: Archival 12CO(2-1), project 2008B-S043, combined with CARMA  
  > "archival SMA $^{12}$CO(2-1) (Project Code 2008B-S043)" (CO Data Reduction)
- External data: 12CO(2-1)/(1-0) line ratio R21 ~ 0.97  
  > "we adopt the value of (cite: Baas:1994) and propagate a 10% uncertainty." (Final Data Products) [from Baas et al. 1994 (cite: Baas:1994)]
- External data: D_HI-M_HI relation log(D_HI)=0.506 log(M_HI)-3.291  
  > "$$\begin{equation}
    \log(D_{HI}) = 0.506\log(M_{HI})-3.291," (HI Mass) [from Wang et al. 2016 (cite: Wang:2016)]

## Processing

### Calibration

- pipeline or manual: ALMA data processed by the standard ALMA pipeline  
  > "which had been processed by the standard ALMA pipeline (cite: hunter23)" (CO Data Reduction)
- casa version: _not stated_
- pipeline version: _not stated_
- archive products used as is: _not stated_
- flux calibrator: _not stated_
- flux scale uncertainty: ~10% for ALMA Band 3; CARMA flux scale problem (CARMA-only tail flux 55% of ALMA)  
  > "for ALMA Band 3 (115 GHz), it is $\sim$10% (cite: Fomalont:2014)" (Final Data Products)
- self calibration: _not stated_

### Imaging

- task: tclean, mosaic, mode cube, common restoring beam  
  > "In `tclean`, with the *imagermode* parameter set to ‘mosaic’, the *mode* set to ‘cube’, the restoring beam set to ‘common’" (CO Data Reduction)
- deconvolver: _not stated_
- weighting robust: Briggs robust = 1.5  
  > "the *weighting* set to ‘briggs’ with a *robust* parameter of 1.5" (CO Data Reduction)
- uv taper: _not stated_
- cell size: _not stated_
- image size: _not stated_
- masking: _not stated_
- multiscale scales: _not stated_
- continuum subtraction: _not stated_
- line free channels: _not stated_
- primary beam correction: _not stated_
- array combination: ALMA and CARMA visibilities imaged jointly  
  > "we combined these data with archival ALMA Science Archive (Project Code: 2016.1.00027.S" (CO Data Reduction)
- smoothing: _not stated_
- final beam: 0.69 x 0.55 arcsec, 3 km/s channels between 780-900 km/s  
  > "which has 3 km s$^{-1}$ wide steps between 780 – 900 km s$^{-1}$and a 0.69$''$ $\times$ 0.55$''$ beam" (CO Data Reduction)
- final rms: _not stated_

### Inherited from earlier work

- Standard ALMA pipeline processing of archival data, originally presented in Imara & Faesi 2019  
  > "originally presented in (cite: Imara:2019)), which had been processed by the standard ALMA pipeline (cite: hunter23)" (CO Data Reduction) [from (cite: Imara:2019); (cite: hunter23)]
- Smooth-and-clip masking for moment maps  
  > "Following methods described in (cite: Popping:2012) and (cite: Serra:2012)" (Final Data Products) [from (cite: Popping:2012); (cite: Serra:2012)]

### Not stated but needed to reproduce (our reading)

- CASA version used for the ALMA+CARMA combination in tclean
- Image size, cell size, niter, threshold and clean masks for the CO(1-0) combination
- Which ALMA execution blocks or members, and ALMA pointings, were used
- CARMA weight scaling and relative weighting between ALMA and CARMA
- Continuum subtraction for the CO data
- Primary beam correction details

## Analysis recipe

1. **Combine CARMA and ALMA 12CO(1-0) and image**: Joint tclean mosaic cube of CARMA and archival ALMA, Briggs robust 1.5  
  > "the *weighting* set to ‘briggs’ with a *robust* parameter of 1.5, and the rest frequency set to 115.2712 GHz" (CO Data Reduction)
   - software: CASA
   - parameter: 3 km/s channels; 0.69x0.55 arcsec beam  
  > "which has 3 km s$^{-1}$ wide steps between 780 – 900 km s$^{-1}$and a 0.69$''$ $\times$ 0.55$''$ beam" (CO Data Reduction)
   - fitting: _not stated_
   - validation: Doubling CARMA amplitude and weights changed ALMA+CARMA image by 3%; ALMA smoothed to CARMA resolution shows similar morphology  
  > "the resulting ALMA+CARMA image only differs from the unmodified version by 3%" (CO Data Reduction)
2. **Make masked moment maps and noise**: Smooth-and-clip mask (A=4 for CO(1-0)), immoments; noise as MAD STD  
  > "In the H i data, the scalar A was set to 3, and in the $^{12}$CO(1-0) data, it was set to 4." (Final Data Products)
   - software: CASA, Astropy
   - fitting: _not stated_
   - validation: _not stated_
3. **Measure integrated flux and molecular mass**: RectangularAperture spectra; M_H2 from Bolatto et al. 2013 Eq. 3  
  > "From Equation (3) of (cite: Bolatto:2013), the total molecular mass is" (Final Data Products)
   - software: Photutils
   - assumption: X_CO = 3e20 cm^-2 (K km/s)^-1 with 30% uncertainty; distance 9 Mpc  
  > "We use 3 $\times$ 10$^{20}$ cm$^{-2}$ (K km s$^{-1}$)$^{-1}$ for consistency with and (cite: Santangelo_Testi_Gregorini_Leurini_Vanzi_Walmsley_Wilner_2009)" (Final Data Products)
   - fitting: _not stated_
   - validation: _not stated_
4. **Position-velocity slices of CO**: pvextractor slices at PA=49, 130, 180 deg  
  > "In the $^{12}$CO(1-0) data, we similarly extracted slices at PA = 49$^{\circ}$ and 130$^{\circ}$, both anchored at Region A." (Final Data Products)
   - software: Pvextractor, Spectral-Cube
   - fitting: _not stated_
   - validation: _not stated_

## Software

- **CASA** 4.2 for CARMA; 6.4 for VLA: Calibration, imaging, moments  
  > "were reduced independently in CASA version 4.2" (CO Data Reduction)
- **Photutils** 1.11: Aperture photometry of spectra  
  > "with the `RectangularAperture` function from the Python package Photutils (cite: Bradley:1.11)" (Final Data Products)
- **Pvextractor** 0.3: Position-velocity slices  
  > "With the Python package Pvextractor[^9] version 0.3 and Spectral-Cube" (Final Data Products)
- **Astropy** : MAD STD noise estimates  
  > "function `mad`$\_$`std`" (Final Data Products)
- **CARTA** : Inspecting H I cubes for line-free channels  
  > "We inspected the data using the Cube Analysis and Rendering Tool for Astronomy (CARTA; (cite: CARTA))" (HI Data Reduction)

## Numeric results

| quantity | value | uncertainty | units | step | quote |
|---|---|---|---|---|---|
| Total 12CO(1-0) molecular mass | 14.1e7 | 4.4e7 | Msun | 3 | / $^{12}$CO(1-0) Total / 08:36:15.52 / –26:24:36.36 / 849 / 58 / 42 / 46 / 0 / 111 $\pm$ 11 / 14.1 $\pm$ 4.4 / |
| 12CO(1-0) tail molecular mass | 2.5e7 | 0.8e7 | Msun | 3 | / $^{12}$CO(1-0) Tail  / 08:36:15.70 / –26:24:49.00 / 826 / 30 / 15 / 11 / –30 / 20 $\pm$ 2 / 2.5 $\pm$ 0.8 / |
| Total H I mass | 16.9e7 | 0.5e7 | Msun | 0 | / H i Total            / 08:36:14.65 / –26:24:26.41 / 858           / 117 |
| Mass of NW CO clump | 0.8e6 | 0.3e6 | Msun | 3 | corresponding to a molecular gas mass of (0.8 $\pm$ 0.3) $\times$ 10$^6$ $\textrm{M}_{\odot}$ |
| Body to tail CO intensity ratio | 3.2 | 0.2 | dimensionless | 3 | is 3.2 $\pm$ 0.2 |

## Qualitative findings

- CO tail is clumpy and kinematically coherent, and not a spatial filtering artifact; combining CARMA with ALMA recovers more diffuse flux but keeps the clumps  
  > "does not eliminate the clumpy appearance of the tail, suggesting that the fragmentation is real and not an artifact of imaging." (Distribution for CO Gas)

## Claim tuples

- H: Is the CO tail due to outflow or fountain? | E: Energetics and kinematics arguments using CO tail mass and Keplerian orbit | R: About 2e55 erg needed, ~1e5 supernovae | F: Outflow unlikely; infall favored | **supported**
- H: Is there an H I tail as reported earlier? | E: New VLA C-array H I cube | R: No significant tail; extended envelope | F: Tail not confirmed | **supported**
- H: Could infall of the CO tail trigger the starburst? | E: Ram-pressure estimate | R: P/k = 3-4e8 K cm^-3 | F: Plausible trigger | **partially**

## Reasoning

- Why this data: _not stated_
- Why this method: _not stated_
- How they decided it was enough: _not stated_
- Limitation (authors): CARMA absolute flux scale problem could not be reconciled  
  > "the comparison revealed a problem with the CARMA absolute flux scale that we could not reconcile" (CO Data Reduction)
- Caveat (inferred, ours): Interpretation of the tail rests on circumstantial evidence
- Caveat (inferred, ours): CARMA flux scale discrepancy
- Caveat (inferred, ours): R21 and X_CO assumed uniform

## Reproducibility

- Data public (paper): ALMA data from archive; SMA archival  
  > "archival ALMA Science Archive (Project Code: 2016.1.00027.S" (CO Data Reduction)
- Products in archive: _not stated_
- Missing: CARMA c1274 data availability and calibration details
- Missing: tclean image size, cell size, masks for the CO combination
- Data volume (inferred): ~50-150 GB
- Score (inferred): 3/5, Public data and a fairly clear recipe, but the CARMA data and several imaging parameters are not given.
- Rediscovery candidate: no, CARMA data are unpublished and the ALMA role is minor; the recipe is incomplete.

## Links

- Companion: Imara & Faesi 2019 (cite: Imara:2019) (Original publication of the ALMA 12CO(1-0) data)
- Related: CARMA c1274
- Related: SMA 2008B-S043
- Related: VLA 21A-198

## Checks

```json
{
 "quotes": 52,
 "quotes_ok": 52,
 "quote_pass_rate": 1.0,
 "quotes_too_long": 0,
 "unsupported_facts": 0,
 "project_codes": 1,
 "codes_not_in_text": [],
 "codes_not_in_obscore": [],
 "obscore_codes_not_in_card": [],
 "codes_printed_but_missing": [
  "2016.1.0027.S"
 ],
 "numeric_results": 5,
 "numeric_problems": 0,
 "fill": {
  "facts": 71,
  "stated": 36,
  "rate": 0.507
 },
 "evidence_ok": true
}
```
