# Probing the final stages of protoplanetary disk evolution with ALMA

`2015A&A...583A..66H` | Astronomy and Astrophysics 2015 | first author: Hardy, A. | arXiv: 1504.05562 | DOI: 10.1051/0004-6361/201526504

Card schema 1.0 | model claude-sonnet-5-5 | depth full | type observational_alma_primary

## Science

- Fields: protoplanetary_disks, debris_disks
- Question: Are weak-line T Tauri stars with IR excess photoevaporating transition disks or young debris disks, based on their dust masses and CO content?  
  > "We aim to provide observational constraints on theories of disk-clearing by measuring the dust masses and CO content of a sample of young (1.8-26.3 Myr) WTTS." (abstract)
- Target **24 IR-excess WTTS in Taurus, eta Cha, Cha I, Lupus, Ophiuchus, Corona Australis**: coordinates 2MASS IDs given in table (e.g. 04182147+1658470)  
  > "| 1 | 04182147+1658470 | Taurus | 135$\pm$20 | K5 | Absorp. | 1,2,3 | ... | ... |  |" (Table 1); z/distance 97-200 pc depending on cloud (e.g. Taurus 135±20 pc)  
  > "| 1 | 04182147+1658470 | Taurus | 135$\pm$20 | K5 | Absorp. | 1,2,3 | ... | ... |  |" (Table 1); distance from _not stated_

## Data provenance

- ALMA projects: 2012.1.00350.S, 2011.0.00733.S
- bands: Band 6; Cycle 0 (systems 14,17,19,23,24) and Cycle 1 (rest)  
  > "Observations of the above systems were performed in Band 6, with Systems 14, 17, 19, 23 and 24 being observed in Cycle 0 (2012), and the remaining in Cycle 1 (2013)." (2.2 ALMA observations)
- frequencies and spectral setup: one baseband at 230.52 GHz (12CO 2-1), continuum basebands at 228.52, 214.52, 212.52 GHz; 976.56 kHz in 3840 channels per 1.875 GHz baseband  
  > "one baseband centred on 230.52 GHz which was aimed at detecting the $^{12}$CO(2–1) spectral line, and three continuum basebands centred at 228.52, 214.52, and 212.52 GHz." (2.2 ALMA observations)
- continuum bandwidth: 3.75 GHz (Cycle 0), 7.5 GHz (Cycle 1) total  
  > "The total bandwidth for the observations was 3.75 GHz for the Cycle 0 and 7.5 GHz for Cycle 1 observations" (2.2 ALMA observations)
- arrays: _not stated_
- configurations: _not stated_
- baselines: min/max 15.1-21.2 m / 402-992 m  
  > "| 13/12/18 | Cha | 23 | 4.16 | DV19,08 | J1107-4449 | Ceres | J0635-7516 | 2.31 | 15.1/992 |  |" (Table 2)
- angular resolution: _not stated_
- max recoverable scale: _not stated_
- sensitivity: requested rms 0.16 mJy continuum, 30 mJy per channel  
  > "the requested rms was set at 0.16 mJy for the continuum, and 30 mJy for each individual velocity channel" (2.2 ALMA observations)
- time on source: 2.07-4.54 min per execution  
  > "| 12/06/17 | Lup/Op/CrA | 20 | 4.54 | ... | J1733-1304 | Neptune | J1924-2914 | 1.41 | 21.2/402 |  |" (Table 2)
- observing dates: 2012-06-17, 2013-11-01, 2013-12-04, 2013-12-18  
  > "| 13/12/04 | Taurus | 27 | 3.60 | DV08 | J0423-0120 | J0510+180 | J0510+180 | 5.11 | 15.8/463 |  |" (Table 2)
- pi or archival as stated: _not stated_
- Line: 12CO J=2-1 (230.52 GHz (baseband centre))
- Other facility **Spitzer, WISE, Herschel**: mid/far-IR photometry for SEDs and fractional disk luminosities  
  > "show weak yet robust (\>5-10 $\sigma$) excesses in the mid and/or far-IR from Spitzer, WISE, and/or Herschel." (2.1 Target selection)
- External data: Photometry, spectral types and Halpha widths of targets  
  > "The target’s photometry, spectral types and H$_{\alpha}$ widths can be found in the following papers" (Table 1 notes) [from Nguyen2012; Howard2013; Luhman2010; Cieza2013a; Cieza2012; Wahhaj2010; Romero2012 etc.]
- External data: Dust-mass constant at 1.3 mm  
  > "We adopt the constant derived for 1.3mm by (cite: Cieza2008a)" (3.1 Disk dust masses) [from (cite: Cieza2008a)]
- External data: Spectral-type temperature scale and de-reddening values  
  > "using the scale provided by (cite: Kenyon1995)" (3.3 Stellar ages) [from (cite: Kenyon1995)]
- External data: PMS isochrones for ages and masses  
  > "compared to the PMS isochrones of (cite: Siess2000) to obtain the age" (3.3 Stellar ages) [from (cite: Siess2000)]
- Simulation/model as data: Williams & Best (2014) grid of CO models, stellar mass 0.5 Msun, other parameters free, used to interpret 12CO non-detections  
  > "(cite: Williams2014) created a grid of models with different density structures that include a simple prescription for the CO chemistry." (3.2 12CO(2-1) non-detections)

## Processing

### Calibration

- pipeline or manual: Standard calibration steps (no details)  
  > "Standard calibration steps were applied to the data" (2.2 ALMA observations)
- casa version: _not stated_
- pipeline version: _not stated_
- archive products used as is: _not stated_
- flux calibrator: Neptune, Ceres, J0510+180 (per execution)  
  > "| 13/11/01 | Lup/Op | 29 | 2.07 | DV19,08,06 | J1924-2914 | Neptune | J1625-2527 | 1.60 | 17.3/992 |  |" (Table 2)
- flux scale uncertainty: _not stated_
- self calibration: _not stated_

### Imaging

- task: CASA clean  
  > "deconvolving the set of visibilities with the clean task implemented in CASA (cite: McMullin2007), using natural weighting" (2.2 ALMA observations)
- deconvolver: _not stated_
- weighting robust: natural weighting  
  > "deconvolving the set of visibilities with the clean task implemented in CASA (cite: McMullin2007), using natural weighting" (2.2 ALMA observations)
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

- Dust mass conversion with 0.566 Mearth per mJy at 140 pc  
  > "We adopt the constant derived for 1.3mm by (cite: Cieza2008a)" (3.1 Disk dust masses) [from (cite: Cieza2008a)]
- Gas-mass constraints from CO using model grid  
  > "(cite: Williams2014) created a grid of models with different density structures" (3.2 12CO(2-1) non-detections) [from (cite: Williams2014)]

### Not stated but needed to reproduce (our reading)

- Reduction software/CASA version and pipeline
- Image size, cell size, clean masks and thresholds
- Synthesized beams and per-source rms values
- Channel width and velocity range for CO upper limit (90 mJy km/s)
- Point-source fit details
- Photometry values and fitted blackbody parameters used for SEDs
- Flux calibrator model/uncertainty
- Extinction values used for de-reddening

## Analysis recipe

1. **Image and measure 1.3 mm continuum flux**: clean with natural weighting; point-source fit to visibilities for detections; 3 sigma upper limits otherwise  
  > "A point-source, fitted to the measured visibilities, was used for those systems with a continuum detection to gain accurate estimation of this flux value." (2.2 ALMA observations)
   - software: CASA
   - fitting: _not stated_
   - validation: _not stated_
2. **Derive dust masses**: M_dust = 0.566 [F(1300)/mJy (d/140 pc)^2] Mearth  
  > "M_{\mathrm{dust}}=0.566 \times \left[ \dfrac{F_{\nu}(1300)}{mJy} \left( \dfrac{d}{140 pc} \right)^{2} \right] M_{\oplus}" (3.1 Disk dust masses)
   - assumption: optically thin continuum at mm wavelengths  
  > "owing to continuum emission being optically thin at mm wavelengths, the dust mass can be estimated by a simple equation" (3.1 Disk dust masses)
   - fitting: _not stated_
   - validation: Upper limits uncertainty dominated by distance  
  > "we quote the 3 sigma value as our upper limit, with this uncertainty being dominated by the uncertainty in the distance to the system." (3.1 Disk dust masses)
3. **Constrain gas-to-dust ratio from CO non-detection**: compare 3 sigma limit of 90 mJy km/s to Williams & Best grid  
  > "would be readily detectable in $^{12}$CO(2-1) at our $3\sigma$ detection limit of 90 mJy km s$^{-1}$." (3.2 12CO(2-1) non-detections)
   - parameter: stellar mass 0.5 Msun; other parameters free  
  > "We compare our results to this grid for a stellar mass of 0.5 M$_{\odot}$" (3.2 12CO(2-1) non-detections)
   - assumption: ISM gas-to-dust ratio 100 as reference  
  > "an ISM gas-to-dust ratio of 100 would imply a gas mass of $\sim 1\,M_{\rm J}$" (3.2 12CO(2-1) non-detections)
   - fitting: _not stated_
   - validation: CO would be detected in 90% of models for other disks  
  > "the CO emission would still be above our detection threshold for 90% of the models" (3.2 12CO(2-1) non-detections)
4. **Derive stellar ages and masses**: Teff from spectral type, J-band luminosity de-reddened, compared to Siess et al. PMS isochrones  
  > "The values of temperature and luminosity were then compared to the PMS isochrones of (cite: Siess2000) to obtain the age." (3.3 Stellar ages)
   - assumption: distances from Table 1  
  > "The distances in Table [\[sampleparams\]](#sampleparams) were then used to calculate the stellar radius" (3.3 Stellar ages)
   - fitting: _not stated_
   - validation: distance uncertainty ~15% gives ~30% luminosity uncertainty  
  > "which can introduce a $\sim$30$\%$ uncertainty into the intrinsic luminosity of the object" (3.3 Stellar ages)
5. **Compute fractional disk luminosity**: fit one or two modified blackbodies to star-subtracted SED (lambda0 = 70 um, beta=2 for limits); integrate with Simpson's rule and divide by stellar blackbody normalised to J  
  > "Both flux densities were then integrated according to Simpson’s rule and divided to obtain the fractional disk luminosity." (3.4 Fractional disk luminosities)
   - parameter: lambda0 fixed at 70 micron  
  > "It was therefore assigned a fixed value of 70$\mu$m" (3.4 Fractional disk luminosities)
   - assumption: all emission in star-subtracted SED attributed to disk  
  > "we attribute all emission from the star-subtracted SED to the disk ($L_{D}$)" (3.4 Fractional disk luminosities)
   - fitting: blackbody fits; sampler not stated  
  > "we attribute all emission from the star-subtracted SED to the disk ($L_{D}$) and fit this emission to either one or two black bodies, as required." (Fractional disk luminosities)
   - validation: _not stated_

## Software

- **CASA** : clean imaging of visibilities  
  > "clean task implemented in CASA (cite: McMullin2007)" (2.2 ALMA observations)

## Numeric results

| quantity | value | uncertainty | units | step | quote |
|---|---|---|---|---|---|
| Continuum detections | 4 of 24 (systems 2, 14, 17, 23) | not stated | count | 1 | Only four of our 24 systems have detectable continuum above the 3$\sigma$ level |
| 1.3 mm flux system 17 | 1.813 | not stated | mJy | 1 | / 17 / 1.813 / 2.09$\pm$0.44 / 0.10 / $2.6_{-0.5}^{+1.2}$ / 140 / |
| Dust mass system 17 | 2.09 | 0.44 | Mearth | 2 | / 17 / 1.813 / 2.09$\pm$0.44 / 0.10 / $2.6_{-0.5}^{+1.2}$ / 140 / |
| Dust mass system 14 | 0.45 | 0.13 | Mearth | 2 | / 14 / 0.696 / 0.45$\pm$0.13 / 0.17 / $6.9_{-1.7}^{+2.8}$ / 80 / |
| CO 3 sigma limit | 90 | not stated | mJy km/s | 3 | our $3\sigma$ detection limit of 90 mJy km s$^{-1}$ |
| Age range of sample | 1.8-26.3 | not stated | Myr | 4 | a sample of young (1.8-26.3 Myr) WTTS |

## Qualitative findings

- No 12CO(2-1) emission detected in any system, implying severely reduced gas-to-dust ratios  
  > "We detect continuum emission in only four of 24 WTTS, and no $^{12}$CO(2-1) emission in any of them." (abstract)

## Claim tuples

- H: Are IR-WTTS mostly photoevaporating transition disks? | E: ALMA Band 6 continuum and CO of 24 IR-WTTS | R: Only 4/24 continuum detections; no CO | F: Most are young debris disks; clearing of dust is rapid | **supported**
- H: Do detected systems have normal gas content? | E: Compare CO limit with model grid | R: CO undetected though ISM ratio would give detectable gas | F: Gas-to-dust ratio well below 100 | **supported**

## Reasoning

- Why this data: _not stated_
- Why this method: 12CO(2-1) chosen as sensitive to gas at large radii  
  > "it is highly sensitive to the presence of circumstellar gas out to large radii" (2.2 ALMA observations)
- How they decided it was enough: _not stated_
- Limitation (authors): Dust mass method has significant uncertainties; ages uncertain; binarity unconfirmed  
  > "This approach has significant uncertainties but is quite standard in the field" (3.1 Disk dust masses)
- Caveat (inferred, ours): Single-band continuum with fixed opacity and temperature gives only rough masses
- Caveat (inferred, ours): Distances uncertain up to 15%
- Caveat (inferred, ours): CO limits rely on model grid; 12CO optically thick
- Caveat (inferred, ours): Snapshot observations with short integration

## Reproducibility

- Data public (paper): _not stated_
- Products in archive: _not stated_
- Missing: Calibration/imaging details
- Missing: SED photometry table and fits
- Data volume (inferred): ~10-50 GB
- Score (inferred): 3/5, Data projects identified and dust-mass formula explicit, but imaging and SED fitting details lacking.
- Rediscovery candidate: no, Imaging details and SED photometry are incomplete, though the dust-mass results are numeric.

## Links

- Method: (cite: Williams2014) (CO model grid for gas masses)
- Method: (cite: Cieza2008a) (dust mass conversion)
- Companion: (cite: Caceres2015) (ALMA observation of FW Tau)
- Related: Spitzer transition disk survey (Cieza et al. 2010, 2012)

## Checks

```json
{
 "quotes": 53,
 "quotes_ok": 53,
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
  "facts": 75,
  "stated": 41,
  "rate": 0.547
 },
 "evidence_ok": true
}
```
