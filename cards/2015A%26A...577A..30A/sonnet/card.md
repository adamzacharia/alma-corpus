# Tightening the belt: Constraining the mass and evolution in SDC335

`2015A&A...577A..30A` | Astronomy and Astrophysics 2015 | first author: Avison, A. | arXiv: 1501.04638 | DOI: 10.1051/0004-6361/201425041

Card schema 1.0 | model claude-sonnet-5-5 | depth light | type multi_facility_alma_minor

## Science

- Fields: star_formation, milky_way_ism
- Question: What are the properties (ionising photon flux, spectral type, luminosity, gas mass) of the stars forming in the massive mm-cores MM1 and MM2 of SDC335, and what stellar population will form?  
  > "In this paper we aim to constrain the properties of the stars forming within these two massive millimetre sources." (abstract)
- Target **SDC335.579-0.292 (MM1a, MM1b, MM2)**: coordinates MM1a 16:30:58.765 -48:43:54.00; MM1b 16:30:58.638 -48:43:51.70; MM2 16:30:57.291 -48:43:40.21  
  > "3.25($^{+0.33}_{-0.35}$)kpc (following (cite: Peretto13), using the (cite: Reid09) model)" (Introduction); "MM1*a*& 16:30:58.765 & -48:43:54.00" (3 Results and analysis); z/distance 3.25 (+0.33/-0.35) kpc  
  > "3.25($^{+0.33}_{-0.35}$)kpc (following (cite: Peretto13), using the (cite: Reid09) model)" (Introduction); "MM1*a*& 16:30:58.765 & -48:43:54.00" (3 Results and analysis); distance from following Peretto13, using the Reid09 Galactic model  
  > "3.25($^{+0.33}_{-0.35}$)kpc (following (cite: Peretto13), using the (cite: Reid09) model)" (Introduction); "MM1*a*& 16:30:58.765 & -48:43:54.00" (3 Results and analysis)

## Data provenance

- ALMA projects: _none stated_
- bands: ALMA Band 3 (3.2 mm, 93.7 GHz) from Peretto13; new ATCA data at 6, 8, 23, 25 GHz  
  > "SDC335 was the target of ALMA Cycle 0 observations with ALMA Band 3 (cite: Peretto13)." (Introduction)
- frequencies and spectral setup: _not stated_
- continuum bandwidth: _not stated_
- arrays: _not stated_
- configurations: _not stated_
- baselines: _not stated_
- angular resolution: ALMA 5.6x4.0 arcsec; ATCA 25 GHz 1.9x1.0 arcsec  
  > "| ALMA | 93.7 | 0.400 | 5.6$\times$4.0 |" (Table 1)
- max recoverable scale: _not stated_
- sensitivity: ALMA continuum 0.400 mJy/beam at 93.7 GHz  
  > "| ALMA | 93.7 | 0.400 | 5.6$\times$4.0 |" (Table 1)
- time on source: _not stated_
- observing dates: _not stated_
- pi or archival as stated: _not stated_
- Other facility **ATCA**: 6, 8, 23, 25 GHz continuum (project C2835)  
  > "from two dedicated observing runs under project code C2835." (2.1 ATCA)
- Other facility **Herschel Hi-GAL PACS**: 70 and 160 micron photometry via Hyper  
  > "We limited our analysis to the PACS 70 and 160 $\mu$m data" (2.2 Additional data)
- Other facility **APEX LABOCA**: 870 micron flux densities  
  > "Archival data from *Spitzer*[^5](MIPS and GLIMPSE), MSX, and APEX (LABOCA) have also been used within this work." (2.2 Additional data)
- External data: ALMA 3.2 mm flux densities and deconvolved sizes of MM1 and MM2  
  > "at deconvolved size scales of 0.054pc and 0.057pc (following (cite: Peretto13))" (3.2 SED) [from Peretto13]
- External data: ZAMS Lyman continuum values and spectral types  
  > "compared with the Lyman Continuum values for ZAMS stars given in (cite: Davies11) and spectral types from (cite: Mottram11)" (3.1.3 Derived properties) [from Davies11; Mottram11]

## Processing

### Calibration

- pipeline or manual: _not stated_
- casa version: _not stated_
- pipeline version: _not stated_
- archive products used as is: _not stated_
- flux calibrator: PKS1934-638 (flux and bandpass); PKS1646-50 phase  
  > "PKS1934-638 was used for flux and bandpass calibration and PKS1646-50 for phase calibration." (2.1 ATCA)
- flux scale uncertainty: _not stated_
- self calibration: _not stated_

### Imaging

- task: MIRIAD MFCLEAN  
  > "The task `MFCLEAN`[^3] was used to CLEAN the image owing to the large bandwidths of the data." (2.1 ATCA)
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

- Distance 3.25 kpc  
  > "following (cite: Peretto13), using the (cite: Reid09) model" (Introduction) [from Peretto13]
- Infall rate 2.5e-3 Msun/yr  
  > "the infall rate of SDC335 (2.5 $\pm$ 1.0)$\times10^{-3}$ M$_{\odot}$yr$^{-1}$ (cite: Peretto13)" (4.1) [from Peretto13]

### Not stated but needed to reproduce (our reading)

- ALMA project code and calibration/imaging of the Cycle 0 data
- Peretto13 ALMA flux densities (16% mass correction pending)
- ATCA imaging weights, cell size and Gaussian-fit details
- Fit uncertainties/sampler for the nonlinear least squares
- 43 GHz ATCA data are unpublished

## Analysis recipe

1. **Measure ATCA flux densities**: Gaussian fits to each source with IMFIT; MM1a at 6 GHz measured by polygon in CASA  
  > "Integrated flux density measurements from these observations were obtained by fitting Gaussians to each source using the MIRIAD `IMFIT` task" (2.1 ATCA)
   - software: MIRIAD, CASA
   - fitting: _not stated_
   - validation: _not stated_
2. **Fit free-free emission**: Non-linear least squares of free-free model for turnover frequency and size; EM from tau=1  
  > "implementing a non-linear least square regression algorithm. The fitted parameters are the free-free turnover frequency, $\nu_t$, (where the optical depth, $\tau=1$) and the physical diameter of the source, $l$." (3.1.1)
   - assumption: Te fixed to 10,000 K  
  > "fixing $T_e$ to the fiducial 10,000K" (3.1.1)
   - fitting: non-linear least squares  
  > "implementing a non-linear least square regression algorithm" (3.1.1)
   - validation: _not stated_
3. **Derive Lyman flux and ZAMS type**: N_Lym from 23 GHz flux, compared to Davies11 ZAMS values  
  > "For each source we calculate $N_{Lym}$ using the 23 GHz continuum integrated flux density value." (3.1.3)
   - assumption: Cylindrical homogeneous HII region, D=3.25 kpc  
  > "Assuming a cylindrical homogeneous HII region" (3.1.3)
   - fitting: _not stated_
   - validation: _not stated_
4. **Fit dust SED and derive Lbol and gas mass**: Modified blackbody to free-free subtracted SED; integrate 100 kHz-100 THz; mass from 3.2mm flux  
  > "The resulting best fit parameters are then used in a direct integration of the SED between 100 kHz and 100 THz" (3.2)
   - software: Hyper
   - parameter: Omega_c fixed to radius 11.4 arcsec; priors Td 25 K, nu0 4.3 THz, beta 2.0  
  > "are given priors of 25.0K, 4.3 THz and 2.0 respectively" (3.2)
   - assumption: kappa=0.1(lambda/0.3mm)^-beta cm2/g, dust-to-gas 0.01  
  > "assuming a dust to gas ratio of 0.01" (3.2)
   - fitting: _not stated_
   - validation: Posteriori refit of MM1a with 43 GHz point consistent  
  > "The new fitted properties for MM1 and MM1a are consistent with the initial fitted values for each source" (3.2.2)

## Software

- **MIRIAD** : ATCA reduction, MFCLEAN, IMFIT  
  > "These ATCA data were reduced using the data reduction package `MIRIAD` with standard ATNF reduction strategies." (2.1 ATCA)
- **CASA** : manual flux measurement of MM1a at 6 GHz  
  > "measured “by hand” using a defined polygonal area in CASA (cite: CASAREF)" (2.1 ATCA)
- **Hyper** : Herschel photometry  
  > "carried out with *Hyper*, an enhanced aperture photometry code" (2.2 Additional data)

## Numeric results

| quantity | value | uncertainty | units | step | quote |
|---|---|---|---|---|---|
| Lbol MM1 | 1.8e4 | not stated | Lsun | 4 | / MM1 / \- / \- / \- / \- / 1.8$\times10^{4}$ / 28.7($\pm$2.3) / 1.97($\pm$0.15) / 763($^{+165}_{-171}$) / |
| Gas mass MM2 | 173 | +65/-66 | Msun | 4 | 9.9$\times10^{3}$ / 29.6($\pm$7.2) / 2.26($\pm$0.52) / 173($^{+65}_{-66}$) |
| Spectral index 6-8 GHz MM1a | 1.90 | 0.40 | dimensionless | 1 | /  6 - 8 GHz  / 1.90$\pm$0.40 / 1.01$\pm$0.12 / 0.96$\pm$0.11  / |
| Lbol exceeded by Ltot | ~20 | not stated | dimensionless | 0 | In both cases $L_{tot}$ exceeds the calculated $L_{bol}$ by a factor $\sim$20 |

## Qualitative findings

- Three HCHII regions, two in MM1; ZAMS types B1.5, B1.5 and >=B1-B1.5  
  > "finding two protostars with characteristics of spectral type B1.5 and one with a lower limit of B1-B1.5." (abstract)

## Claim tuples

- H: Do MM1 and MM2 host ionising massive protostars? | E: ATCA 6-25 GHz free-free SED fits | R: Three compact HII regions with sizes <0.5 mpc | F: Three HCHII regions with B1-B1.5 type lower limits | **supported**
- H: Are luminosities consistent with ZAMS plus accretion? | E: Compared Lbol with Ltot,ZAMS | R: Ltot exceeds Lbol by ~20 | F: Accretion luminosity is limited, by swollen/contracting protostars or lower accretion onto stars | **partially**

## Reasoning

- Why this data: _not stated_
- Why this method: _not stated_
- Alternative: Collimated jet interpretation for MM1b and MM2 cannot be excluded  
  > "either the radio jet or compact HII region interpretation may be valid for both MM1*b* and MM2" (3.1)
- How they decided it was enough: _not stated_
- Limitation (authors): MM1a free-free fit least robust as turnover may be above 25 GHz  
  > "The fit to MM1*a* is the least robust as the data for this source allows a rise in flux beyond 25 GHz." (3.1.2)
- Caveat (inferred, ours): Fit uncertainties are not described
- Caveat (inferred, ours): Free-free fits rely on assumed fixed Te
- Caveat (inferred, ours): Mass relies on the ALMA masses with a known 16% error

## Reproducibility

- Data public (paper): _not stated_
- Products in archive: _not stated_
- Missing: ALMA project code
- Missing: Peretto13 ALMA flux values
- Missing: Unpublished 7 mm and 43 GHz data
- Data volume (inferred): small (<10 GB, ATCA continuum plus published fluxes)
- Score (inferred): 3/5, ATCA recipe is partly specified but ALMA data are taken from earlier work and some details are missing.
- Rediscovery candidate: no, ALMA plays a minor role and ATCA data are not stated as public.

## Links

- Method: Traficante14 (Hyper photometry)
- Companion: Peretto13 (ALMA Cycle 0 observations of SDC335)
- Related: Hi-GAL
- Related: ATCA project C2835

## Checks

```json
{
 "quotes": 43,
 "quotes_ok": 43,
 "quote_pass_rate": 1.0,
 "quotes_too_long": 0,
 "unsupported_facts": 0,
 "project_codes": 0,
 "codes_not_in_text": [],
 "codes_not_in_obscore": [],
 "obscore_codes_not_in_card": [
  "2011.0.00474.S"
 ],
 "codes_printed_but_missing": [],
 "numeric_results": 4,
 "numeric_problems": 0,
 "fill": {
  "facts": 72,
  "stated": 32,
  "rate": 0.444
 },
 "evidence_ok": true
}
```
