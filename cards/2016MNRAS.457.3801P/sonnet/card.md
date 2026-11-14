# The central parsecs of M87: jet emission and an elusive accretion disc

`2016MNRAS.457.3801P` | Monthly Notices of the Royal Astronomical Society 2016 | first author: Prieto, M. A. | arXiv: 1508.02302 | DOI: 10.1093/mnras/stw166

Card schema 1.0 | model claude-sonnet-5-5 | depth light | type multi_facility_alma_minor

## Science

- Fields: agn_and_quasars, nearby_galaxies
- Question: What is the SED shape of the M87 core on 0.4 arcsec (32 pc) scales in quiescent and active states, and can a jet plus thin accretion disc model explain it and constrain the accretion rate?  
  > "This section investigates whether a physical model based on a jet plus a thin disc can reproduce M87 SEDs." (4 MODELLING M87 SED)
- Target **M87 core**: coordinates _not stated_; z/distance D = 16.4 Mpc  
  > "A distance to M87 of 16 _._ 4 Mpc (1 _[′′]_ = 80 pc; Jord´an et al. 2005) is assumed in this article." (1 INTRODUCTION); distance from Jordán et al. 2005  
  > "A distance to M87 of 16 _._ 4 Mpc (1 _[′′]_ = 80 pc; Jord´an et al. 2005) is assumed in this article." (1 INTRODUCTION)

## Data provenance

- ALMA projects: _none stated_
- bands: Bands 3, 6, 7, 9 (93–630 GHz), 2012  
  > "the ALMA data collected in 2012 in bands 3, 6, 7, and 9 spanning the spectral range 93–630 GHz, were used." (2.1 Compiled fluxes in a nominal aperture radius of 0″.4 (∼ 32 pc))
- frequencies and spectral setup: four spectral regions per band; six independent frequencies noted elsewhere  
  > "In each band, four spectral regions were extracted from which images were constructed." (2.1 Compiled fluxes in a nominal aperture radius of 0″.4 (∼ 32 pc))
- continuum bandwidth: _not stated_
- arrays: _not stated_
- configurations: _not stated_
- baselines: _not stated_
- angular resolution: beams from 0.33″×0.28″ at 635 GHz to 2.7″×1.5″ at 93 GHz  
  > "Beam sizes range from 0″.33 × 0″.28 at 635 GHz to 2″.7 × 1″.5 arcsec at 93 GHz." (2.1 Compiled fluxes in a nominal aperture radius of 0″.4 (∼ 32 pc))
- max recoverable scale: _not stated_
- sensitivity: _not stated_
- time on source: _not stated_
- observing dates: _not stated_
- pi or archival as stated: _not stated_
- Other facility **HST (ACS, STIS, WFPC2, NICMOS)**: UV, optical and IR nuclear fluxes  
  > "This SED combines VLBI radio, and Hubble Space Telescope (HST) IR, optical and UV data." (2 EXTRACTION OF THE M87 CORE SED)
- Other facility **Chandra**: X-ray core spectrum and fluxes  
  > "At high energies all the SEDs are restricted to Chandra data only" (2 EXTRACTION OF THE M87 CORE SED)
- Other facility **VLA/NRAO**: radio-cm fluxes  
  > "The new data reported here were complemented with literature values if available at the suitable angular resolution and time period." (2.1 Compiled fluxes in a nominal aperture radius of 0″.4 (∼ 32 pc))
- Other facility **VLT-NACO**: near-IR J and K fluxes, 2005  
  > "J-band VLT-NACO 05-01" (Table 2)
- External data: VLBI fluxes for highest-resolution SED (1.3 mm, 3 mm, 86, 22, 8.4, 2.3, 1.6 GHz)  
  > "VLBI 1.3 mm 2009, Doeleman et al. 2012, FWHM = 40 ± 1.8 mas" (Table 4) [from Doeleman et al. 2012; Lonsdale et al. 1998; Lee et al. 2008; Junor & Biretta 1995; Morabito et al. 1986, 1988; Giovannini et al. 1990]
- External data: 2000 Chandra fluxes at 1 and 10 keV  
  > "That of 2000 is published in Di Matteo et al. (2003), whose reported fluxes at 1 and 10 keV" (2.1 Compiled fluxes in a nominal aperture radius of 0″.4 (∼ 32 pc)) [from Di Matteo et al. 2003]
- External data: Black hole mass 5.9e9 Msun rescaled to 16.4 Mpc  
  > "With a BH mass of 5.9 × 10 9 M⊙ (Gebhardt & Thomas 2009, re-scaled to D = 16.4 Mpc adopted in this work)" (1 INTRODUCTION) [from Gebhardt & Thomas 2009]

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
- primary beam correction: _not stated_
- array combination: _not stated_
- smoothing: _not stated_
- final beam: _not stated_
- final rms: _not stated_

### Inherited from earlier work

- Jet plus truncated disc model description  
  > "The modelling follows the description by Markoff et al. (2005, 2008) and Maitra et al. (2009)." (4 MODELLING M87 SED) [from Markoff et al. (2005, 2008); Maitra et al. (2009)]
- HST aperture corrections  
  > "We follow prescriptions by Sirianni et al. (2005) for the ACS, Holtzman et al. (1995) for the WFPC2, and Proffitt et al. (2003) for STIS." (2.1 Compiled fluxes in a nominal aperture radius of 0″.4 (∼ 32 pc)) [from Sirianni et al. 2005; Holtzman et al. 1995; Proffitt et al. 2003]

### Not stated but needed to reproduce (our reading)

- ALMA calibration, CASA version, flux calibrators and imaging parameters
- Exact ALMA project/execution blocks and which spectral windows
- Aperture integration details for ALMA fluxes
- Model fitting procedure, priors and statistic for the jet model
- ALMA flux scale uncertainty

## Analysis recipe

1. **Measure ALMA core fluxes**: Images made from four spectral regions per band; fluxes integrated over the beam on the unresolved central point source  
  > "fluxes and errors were measured on the central point-like source detected in all cases by integrating on the beam size associated with the angular resolution at each frequency." (2.1 Compiled fluxes in a nominal aperture radius of 0″.4 (∼ 32 pc))
   - parameter: adopted ALMA error of 40% reflecting 2012 outburst  
  > "with an associated error bar of 40%, which reflects the average flux increase seen at 22 and 43 GHz in the 2012 outburst." (2 EXTRACTION OF THE M87 CORE SED)
   - assumption: No peak activity at 5 and 230 GHz during ALMA observations  
  > "Examination of the light curves shown by these authors at 5 and 230 GHz indicates no peak activity at these frequencies at that time." (2 EXTRACTION OF THE M87 CORE SED)
   - fitting: _not stated_
   - validation: ALMA trend joins cm data smoothly  
  > "the trend defined by the ALMA data – which run over six independent frequencies – joins the cm data smoothly from 2003" (2 EXTRACTION OF THE M87 CORE SED)
2. **Build quiescent and active SEDs**: Fixed 0.4 arcsec aperture photometry across bands, with galaxy subtraction from circumnuclear rings in UV-IR and Galactic extinction correction  
  > "the stellar emission was removed by averaging the emission in circumnuclear rings taken a various distances from the core, and avoiding HST-1." (2.1 Compiled fluxes in a nominal aperture radius of 0″.4 (∼ 32 pc))
   - software: TinyTim
   - parameter: AV = 0.073, RV = 3.1  
  > "the extinction curve (RV = 3.1) and the extinction value (AV = 0.073) given by Schlegel et al. (1998)" (2.1 Compiled fluxes in a nominal aperture radius of 0″.4 (∼ 32 pc))
   - fitting: _not stated_
   - validation: _not stated_
3. **Fit jet plus truncated disc model**: Multi-component self-absorbed synchrotron jet plus Comptonization plus multicolour blackbody truncated disc; Chandra spectrum folded through detector response  
  > "The SED is thus constructed out of direct jet synchrotron and inverse Compton emission components, together with the disc." (4 MODELLING M87 SED)
   - software: ISIS
   - parameter: fixed: NH = 0.0194e22 cm-2, D = 16.4 Mpc, M = 5.9e9 Msun, inclination 15 deg, plfrac 0.6, rout = 200 Rg, zmax = 1e19 cm  
  > "the fraction of accelerated electrons, set to 0.6, the outer radius of the accretion disc to 200 Rg, gravitational radius, the maximum distance in the jet along which the electrons are accelerated, zmax = 10 19 cm." (4 MODELLING M87 SED)
   - assumption: energy density in protons and thermal pressure equal  
  > "We further assume that the energy density in protons and thermal pressure is the same." (4 MODELLING M87 SED)
   - fitting: _not stated_
   - validation: Tested inclination 25 deg: equivalent fit with Nj up 10-15%  
  > "the total jet power, Nj, has to be increased accordingly by 10–15%." (4 MODELLING M87 SED)

## Software

- **ISIS** : fitting Chandra spectrum folded through detector response  
  > "The model fits the Chandra photon event spectrum after being folded through detector space using the program ISIS (Houck & Denicola 2000)." (4 MODELLING M87 SED)
- **TinyTim** : HST PSF computation  
  > "PSFs were computed with the TINYTIM software" (2.1 Compiled fluxes in a nominal aperture radius of 0″.4 (∼ 32 pc))

## Numeric results

| quantity | value | uncertainty | units | step | quote |
|---|---|---|---|---|---|
| Quiescent core bolometric luminosity (radio to UV) | 2.7e42 | not stated | erg s-1 | 2 | Lobs = 3.6 × 10 −6 Ledd = 2.7 × 10 42 erg s −1 |
| Quiescent jet power Nj | 2.3e-6 | order of magnitude | Ledd | 3 | Nj = 2.3 × 10 −6 Ledd (Table 5) |
| Maximum disc luminosity | 3.4e41 | not stated | erg s-1 | 3 | the inferred disc power is at most Ldisc = 3.4 × 10 41 erg s −1 |
| Accretion rate upper limit (10% efficiency) | <6e-5 | not stated | Msun yr-1 | 3 | implies a strict upper limit to the accretion rate of < 6 × 10 −5 M⊙ yr −1 |
| Jet power, highest-resolution SED | 5.2e-7 (~3.8e41 erg/s) | not stated | Ledd | 3 | Nj = 5.2 × 10 −7 Ledd ∼ 3.8 × 10 41 erg s −1 |
| Post-shock spectral index p (quiescent) | 3.0 | not stated | dimensionless | 3 | p spectral index post-shock e − 3.0 2.9 |

## Qualitative findings

- Core SEDs are featureless power-law-like with a mm turnover near 150-200 GHz; no blue bump, IR bump or 1 micron inflection.  
  > "a turnover in the millimetre region, at about 150–200 GHz, and a steep power-law slope ( α ≈ 1.1) from the IR to the UV." (3 THE SHAPE OF M87 CORE SED)

## Claim tuples

- H: Is the M87 core SED consistent with an accretion-disc or RIAF-dominated AGN? | E: Compared multiwavelength 0.4 arcsec SEDs with Seyfert and quasar templates | R: Featureless power-law SEDs lacking AGN features | F: Jet emission dominates; thin disc or RIAF signature elusive | **supported**
- H: Does the accretion power account for the jet kinetic power? | E: Jet plus disc modelling with disc upper limit | R: Mdot < 6e-5 Msun/yr; jet power 1-2 orders below literature kinetic power | F: Requires past higher activity or spin extraction | **partially**

## Reasoning

- Why this data: _not stated_
- Why this method: _not stated_
- Alternative: Sersic-profile bulge fitting was rejected in favour of aperture photometry because of PSF-matching residual errors of 20-30%  
  > "we find large residual errors up to 20–30% in the fitting procedure in the central 0.2–0.3 arcsec radii" (2.1 Compiled fluxes in a nominal aperture radius of 0″.4 (∼ 32 pc))
- How they decided it was enough: _not stated_
- Limitation (authors): ALMA data are from 2012, not contemporaneous with 2003/2005 SEDs, and lower resolution may include HST-1 below 250 GHz  
  > "These resolutions imply that HST-1's emission is de facto included at frequencies below 250 GHz but not at the higher ones." (2.1 Compiled fluxes in a nominal aperture radius of 0″.4 (∼ 32 pc))
- Caveat (inferred, ours): ALMA fluxes from 2012 are combined with 2003 and 2005 data under an assumed lack of variability
- Caveat (inferred, ours): Model fit statistics and uncertainties are not given
- Caveat (inferred, ours): ALMA beams of up to 2.7 arcsec exceed the 0.4 arcsec aperture

## Reproducibility

- Data public (paper): _not stated_
- Products in archive: _not stated_
- Missing: ALMA reduction details
- Missing: Model code and fit procedure
- Missing: Full ALMA flux extraction method
- Data volume (inferred): tens of GB for ALMA, multi-band
- Score (inferred): 2/5, ALMA is a minor input, with little processing detail and no fit details.
- Rediscovery candidate: no, Recipe incomplete for ALMA processing and model fitting.

## Links

- Method: Markoff et al. 2005, 2008; Maitra et al. 2009 (Jet-disc model)
- Companion: Fernández-Ontiveros et al. 2012 (Earlier SEDs of nearby LLAGN)

## Checks

```json
{
 "quotes": 39,
 "quotes_ok": 39,
 "quote_pass_rate": 1.0,
 "quotes_too_long": 0,
 "unsupported_facts": 0,
 "project_codes": 0,
 "codes_not_in_text": [],
 "codes_not_in_obscore": [],
 "obscore_codes_not_in_card": [
  "2011.0.00754.S"
 ],
 "codes_printed_but_missing": [],
 "numeric_results": 6,
 "numeric_problems": 0,
 "fill": {
  "facts": 71,
  "stated": 30,
  "rate": 0.423
 },
 "evidence_ok": true
}
```
