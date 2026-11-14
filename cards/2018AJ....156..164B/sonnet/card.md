# Medium-sized Satellites of Large Kuiper Belt Objects

`2018AJ....156..164B` | The Astronomical Journal 2018 | first author: Brown, Michael E. | arXiv: 1801.07221 | DOI: 10.3847/1538-3881/aad9f2

Card schema 1.0 | model claude-sonnet-5-5 | depth full | type observational_alma_primary

## Science

- Fields: solar_system
- Question: What are the sizes and albedos of Dysnomia (Eris) and Vanth (Orcus), and do they fit the small icy collisional-satellite paradigm?  
  > "We calculate a diameter for Dysnomia of 700$\pm$115 km and for Vanth of 475$\pm$75 km, with albedos of 0.04$^{+0.02}_{-0.01}$ and 0.08$\pm$0.02 respectively." (abstract)
- Target **Orcus-Vanth**: coordinates _not stated_; z/distance _not stated_; distance from _not stated_
- Target **Eris-Dysnomia**: coordinates _not stated_; z/distance _not stated_; distance from _not stated_

## Data provenance

- ALMA projects: 2016.1.00830.S, 2015.1.00810.S
- bands: Band 7 (~350 GHz), continuum/TDM mode  
  > "All observations in this paper were taken in Band 7, near 350 GHz, in the “continuum” (or “TDM”) mode, with the standard frequency tunings." (2 Observations)
- frequencies and spectral setup: four spectral windows: 335.5–337.5, 337.5–339.5, 347.5–349.5, 349.5–351.5 GHz; effective 345 GHz  
  > "335.5–337.5 GHz; 337.5–339.5 GHz; 347.5–349.5 GHz; and 349.5–351.5 GHz." (2 Observations); "use 345 GHz as the effective frequency in our modeling" (2 Observations)
- continuum bandwidth: _not stated_
- arrays: 12-m array  
  > "Observations of Orcus-Vanth and Eris-Dysnomia were undertaken with the 12-m array of the Atacama Large Millimeter Array (ALMA)." (2 Observations)
- configurations: _not stated_
- baselines: _not stated_
- angular resolution: as fine as 15 mas in high-resolution configurations; 30-50 mas resolution element for Eris data  
  > "the observations were done in high-resolution configurations of ALMA - with resolutions as fine as 15 mas." (2 Observations); "smaller than the 30-50 mas resolution element of the data" (4 Eris-Dysnomia)
- max recoverable scale: _not stated_
- sensitivity: _not stated_
- time on source: _not stated_
- observing dates: Eris-Dysnomia Nov-Dec 2015; Orcus-Vanth Oct-Nov 2016  
  > "The Eris-Dysnomia system was observed in November and December of 2015; The Orcus-Vanth system was observed in October and November of 2016." (2 Observations)
- pi or archival as stated: _not stated_
- Other facility **Spitzer**: unresolved 24 and 71 micron fluxes (literature)  
  > "We fit the unresolved Orcus+Vanth Spitzer 24 and 71 $\mu$m fluxes (cite: 2008ssbn.book..161S)" (3 Orcus-Vanth)
- Other facility **Herschel**: unresolved far-IR fluxes  
  > "the unresolved Herschel 70, 100, and 350 $\mu$m flux (cite: 2013_Fornasier)" (3 Orcus-Vanth)
- Other facility **HST**: archival WFC3 Jan 2015 astrometry of Dysnomia to update its orbit  
  > "We thus use archival observations obtained using WF3 on the Hubble Space Telescope in January 2015 to update the orbital elements of Dysnomia" (4 Eris-Dysnomia)
- External data: Spitzer and Herschel unresolved fluxes for Orcus+Vanth  
  > "We fit the unresolved Orcus+Vanth Spitzer 24 and 71 $\mu$m fluxes (cite: 2008ssbn.book..161S)" (3 Orcus-Vanth) [from (cite: 2008ssbn.book..161S); (cite: 2013_Fornasier)]
- External data: Eris diameter 2326±12 km from occultation  
  > "We assume the occultation-derived circular diameter of Eris of 2326$\pm$12 km (cite: 2011_Sicardy)" (4 Eris-Dysnomia) [from (cite: 2011_Sicardy)]
- External data: Herschel 70, 100, 150 micron and Spitzer 71 micron data for Eris  
  > "data at 70, 100, and 150$\mu$m from the Herschel Space Telescope (cite: 2012A&A...541A..92S)" (4 Eris-Dysnomia) [from (cite: 2012A&A...541A..92S)]

## Processing

### Calibration

- pipeline or manual: ALMA pipeline in CASA initial calibration provided by observatory  
  > "Initial calibration of the data was provided by the ALMA observatory, and is done in the CASA reduction package via the ALMA pipeline (cite: Muders2014)." (2 Observations)
- casa version: _not stated_
- pipeline version: _not stated_
- archive products used as is: _not stated_
- flux calibrator: _not stated_
- flux scale uncertainty: _not stated_
- self calibration: check-source self-calibration used to estimate decorrelation correction to flux densities  
  > "We used one of the check sources in each of the observations to measure the magnitude of this effect, and applied it to our final estimate of flux densities." (2 Observations)

### Imaging

- task: _not stated_
- deconvolver: _not stated_
- weighting robust: natural weighting  
  > "we made images using weighting of the data which sacrifice resolution for sensitivity (so-called "natural weighting")" (2 Observations)
- uv taper: _not stated_
- cell size: _not stated_
- image size: _not stated_
- masking: _not stated_
- multiscale scales: _not stated_
- continuum subtraction: _not stated_
- line free channels: _not stated_
- primary beam correction: _not stated_
- array combination: _not stated_
- smoothing: _not stated_
- final beam: _not stated_
- final rms: _not stated_

### Inherited from earlier work

- Thermal modeling technique and MCMC scheme, emissivity limits, 850 micron emissivity 0.685  
  > "We use the Markov Chain Monte Carlo scheme described in BB17 to explore the best fit parameters and their uncertainties." (3 Orcus-Vanth) [from Brown & Butler 2017 (cite: 2017AJ....154...19B)]
- Orbit fitting method with MCMC  
  > "using the methods described in (cite: 2007Sci...316.1585B) with the updated improvements using a Markov Chain Monte Carlo scheme as described in (cite: 2013ApJ...778L..34B)" (4 Eris-Dysnomia) [from (cite: 2007Sci...316.1585B); (cite: 2013ApJ...778L..34B)]

### Not stated but needed to reproduce (our reading)

- Phase calibrators, flux calibrator, and antenna numbers/baselines
- AIPS imaging parameters (cell, image size, clean depth)
- Decorrelation correction factors per observation
- MCMC sampler details, priors, chain lengths
- Beaming parameter priors
- Distances/heliocentric geometry for thermal model

## Analysis recipe

1. **Reduce visibilities and measure flux densities**: Pipeline calibration in CASA, then AIPS; natural-weight imaging; flux by image, CLEAN components, gaussian fit and visibility fit; decorrelation correction from check source  
  > "flux density in the image; flux density in the CLEAN components; fitting a gaussian in the image; and fitting the visibilities directly." (2 Observations)
   - software: CASA, AIPS
   - parameter: Eris visibility fit: slightly limb-darkened disk, radius 1163 km; others point sources  
  > "For Eris, we used a fit of a slightly limb-darkened disk, with radius of 1163 km (cite: 2011_Sicardy)." (2 Observations)
   - fitting: _not stated_
   - validation: Compared the four flux methods; relatively good agreement  
  > "We found relatively good agreement for all of these techniques." (2 Observations)
2. **Predict Dysnomia position and stack**: Update orbit with HST data (circular fit), predict positions at ALMA epochs, shift images to predicted position and sum  
  > "we shift all three images to be centered on the predicted position of Dysnomia and sum them (Figure 2)." (4 Eris-Dysnomia)
   - fitting: MCMC orbit fit  
  > "so for the final fit we constrain the orbit to be purely circular (Fig 4)." (4 Eris-Dysnomia)
   - validation: Random-shift experiment gives 3.5 sigma significance  
  > "We find values as high as the 0.13 mJy of Dysnomia only 0.02% of the time, corresponding to a 3.5$\sigma$ likelihood that the detection is indeed Dysnomia." (4 Eris-Dysnomia)
3. **Thermal model fit for size and albedo**: Standard thermal model fit with MCMC to ALMA plus Spitzer/Herschel fluxes  
  > "In this model, the free parameters are bolometric emmisivity, phase integral, albedo, diameter, and a beaming parameter" (3 Orcus-Vanth)
   - parameter: emissivity 0.8–1.0; phase integral from albedo empirical fit with 50% variation  
  > "we constrain emissivity to be between 0.8 and 1.0, as argued in BB17" (3 Orcus-Vanth)
   - assumption: 850 micron emissivity 0.685 for all bodies including Eris  
  > "We assume an 850 $\mu$m emissivity of 0.685, as derived in BB17" (3 Orcus-Vanth)
   - fitting: MCMC; median and 16th/84th percentiles reported  
  > "we report the median and 16th and 84th percentiles as our 1$\sigma$ error range" (3 Orcus-Vanth)
   - validation: Fit judged excellent from 30 random samples  
  > "The fit of the model to the data is excellent." (3 Orcus-Vanth)

## Software

- **CASA** : ALMA pipeline initial calibration  
  > "is done in the CASA reduction package via the ALMA pipeline" (2 Observations)
- **AIPS** : data reduction, imaging and flux fitting  
  > "we exported the data from CASA and continued the data reduction in the AIPS package" (2 Observations)

## Numeric results

| quantity | value | uncertainty | units | step | quote |
|---|---|---|---|---|---|
| Dysnomia diameter | 700 | ±115 | km | 3 | We find that Dysnomia has a diameter of 700$\pm$115 km with an albedo of 0.04$^{+0.02}_{-0.01}$. |
| Dysnomia albedo | 0.04 | +0.02/-0.01 | dimensionless | 3 | albedo of 0.04$^{+0.02}_{-0.01}$ |
| Vanth diameter | 475 | ±75 | km | 3 | while Vanth has a diameter of 475$\pm$75 km and an albedo of 0.08$\pm$0.02 |
| Vanth albedo | 0.08 | ±0.02 | dimensionless | 3 | an albedo of 0.08$\pm$0.02 |
| Orcus diameter | 910 | +50/-40 | km | 3 | Orcus has a diameter of $910^{+50}_{-40}$ km and an albedo of 0.23$\pm$0.02 |
| Dysnomia stacked flux density | 0.13 | ±0.03 | mJy | 2 | A source with a flux density of 0.13$\pm$0.03 mJy appears 16 mas from the expected position |
| Dysnomia detection significance | 3.5 | not stated | sigma | 2 | we find a 3.5$\sigma$ detection of Dysnomia by stacking all of the data on the known position of the satellite |

## Qualitative findings

- Neither Vanth nor Dysnomia fits the small icy collisional satellite paradigm; both have low albedos typical of KBOs their size  
  > "Indeed, both Dysnomia and Vanth have the low albedos expected for typical KBOs of their size" (Discussion)

## Claim tuples

- H: Are Dysnomia and Vanth small, high-albedo icy collisional fragments? | E: Resolved ALMA Band 7 thermal flux plus thermal-model MCMC | R: Dysnomia 700±115 km, albedo 0.04; Vanth 475±75 km, albedo 0.08 | F: Both are indistinguishable from typical KBOs of their size, not icy fragments | **supported**
- H: Is Dysnomia detected in ALMA data? | E: Stack images at HST-predicted position; random shift test | R: 0.13 mJy source, 3.5 sigma | F: Weak detection, assumed real | **partially**

## Reasoning

- Why this data: _not stated_
- Why this method: _not stated_
- Alternative: Possible that the Dysnomia detection is erroneous  
  > "First, it is possible that our reported detection of Dysnomia is erroneous." (Discussion)
- How they decided it was enough: _not stated_
- Limitation (authors): Dysnomia detection is weak and needs robust detection at multiple locations  
  > "robust detection at multiple locations are desired" (Discussion)
- Caveat (inferred, ours): Dysnomia result depends on a 3.5 sigma stacked detection and assumed emissivity
- Caveat (inferred, ours): Eris emissivity assumed same as typical KBO despite different surface
- Caveat (inferred, ours): Decorrelation corrections large for some Orcus data

## Reproducibility

- Data public (paper): _not stated_
- Products in archive: _not stated_
- Missing: AIPS imaging parameters
- Missing: MCMC priors and code
- Missing: Decorrelation correction values
- Data volume (inferred): ~50-200 GB raw for seven high-resolution execution blocks
- Score (inferred): 3/5, Data public via archive and methods summarized, but thermal model and MCMC details are deferred to BB17 and imaging details are missing.
- Rediscovery candidate: no, Recipe relies on AIPS steps and an external thermal model not fully specified.

## Links

- Method: Brown & Butler 2017 (cite: 2017AJ....154...19B) (thermal model and MCMC)
- Method: Brown & Schaller 2007 (cite: 2007Sci...316.1585B) (orbit determination)

## Checks

```json
{
 "quotes": 47,
 "quotes_ok": 47,
 "quote_pass_rate": 1.0,
 "quotes_too_long": 0,
 "unsupported_facts": 0,
 "project_codes": 2,
 "codes_not_in_text": [],
 "codes_not_in_obscore": [],
 "obscore_codes_not_in_card": [],
 "codes_printed_but_missing": [],
 "numeric_results": 7,
 "numeric_problems": 0,
 "fill": {
  "facts": 71,
  "stated": 33,
  "rate": 0.465
 },
 "evidence_ok": true
}
```
