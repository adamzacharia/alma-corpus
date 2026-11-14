# CO(1─0) imaging reveals 10-kiloparsec molecular gas reservoirs around star-forming galaxies at high redshift

`2025A&A...700A.278R` | Astronomy and Astrophysics 2025 | first author: Rybak, M. | arXiv: 2411.06474 | DOI: 10.1051/0004-6361/202452948

Card schema 1.0 | model claude-sonnet-5-5 | depth full | type observational_alma_primary

## Science

- Fields: high_z_galaxies
- Question: How extended are the cold molecular gas (CO(1–0)) reservoirs of high-redshift dusty star-forming galaxies compared with dust, stars and [CII] halos?  
  > "our knowledge of the extent and morphology of their cold-gas reservoirs is still in its infancy." (abstract)
- Target **19 AS2VLA DSFGs with secure CO(1–0) detections (e.g. AS2COS13.1, AS2COS14.1, AS2UDS126.0)**: coordinates _not stated_; z/distance z=2.2-4.6 spectroscopic (Table); median z=3.1  
  > "Our initial sample consists of 30 sub-millimetre selected, star-forming galaxies at $z=2.2-4.4$ from the AS2VLA survey" (2.1 Target sample); distance from spectroscopic redshifts from mid-J CO lines and [CI](1–0)  
  > "Our initial sample consists of 30 sub-millimetre selected, star-forming galaxies at $z=2.2-4.4$ from the AS2VLA survey" (2.1 Target sample)

## Data provenance

- ALMA projects: _none stated_
- bands: JVLA K and Ka bands (CO(1–0)); ALMA for [CI](1–0)  
  > "We observed in the K- and Ka-bands, using a contiguous bandwidth of 2 GHz with 2-MHz spectral channels." (2.2 JVLA observations)
- frequencies and spectral setup: _not stated_
- continuum bandwidth: _not stated_
- arrays: JVLA D-array  
  > "The observations were taken between March 2021 and December 2023, under good weather conditions in the D-array configuration." (2.2 JVLA observations)
- configurations: _not stated_
- baselines: _not stated_
- angular resolution: 2.5"–5.1" circularised FWHM (JVLA); 2.2"–4.0" for ALMA [CI]  
  > "the angular resolution ranged from 2.5$"$ to 5.1$"$ (circularised FWHM)" (2.2 JVLA observations)
- max recoverable scale: 44"–60"  
  > "the maximum recoverable scale was 44$"$–60$"$." (2.2 JVLA observations)
- sensitivity: 0.014 Jy km/s/beam in stacked moment-0, median beam 4.2"x2.7"  
  > "We achieve an rms sensitivity of $\sigma=$0.014 Jy km s$^{-1}$ beam$^{-1}$ with a median beam FWHM 4.2”$\times$2.7”" (2.3 Visibility-plane analysis and stacking)
- time on source: 4 h per source incl. overheads (AS2COS14.1 8 h; AS2COS44.1, AS2COS65.1 2 h); ~80 h total  
  > "The total time per source including overheads was four hours for almost all sources." (2.2 JVLA observations)
- observing dates: March 2021 to December 2023  
  > "The observations were taken between March 2021 and December 2023" (2.2 JVLA observations)
- pi or archival as stated: JVLA programs 21A-254 (PI Hodge) and 17A-251 (PI Walter)  
  > "The surveys comprises of the JVLA programs ID:21A-254 (PI: Hodge) and ID:17A-251 (PI: Walter)." (2.2 JVLA observations)
- Line: CO J=1–0 (115.2712 GHz)
- Line: [CI] (1–0) (not stated)
- Other facility **JWST NIRCam**: 4.4-micron stellar sizes (literature)  
  > "stellar emission (traced by JWST NIRCam imaging)" (4.2)
- External data: 870-um dust continuum half-light radius 1.1±0.3 kpc  
  > "870 $\mu$m  |    1.1$\pm$0.3    | (cite: gullberg2019)" (Table 1) [from (cite: gullberg2019)]
- External data: 870-um size 1.8±0.1 kpc for ALESS  
  > "870 $\mu$m  |    1.8$\pm$0.1    |  (cite: hodge2016)" (Table 1) [from (cite: hodge2016)]
- External data: 4.4-um stellar half-light radius 2.7±0.2 kpc  
  > "we adopt the 4.4-$\mu$m half-light radius of $R_{1/2}=2.7\pm0.2$ kpc derived by (cite: Gillman2024)" (4.2) [from (cite: Gillman2024)]
- External data: [CII]/FIR range (1.5-38)e-3 for z=2-4 DSFGs  
  > "\[C ii\]/FIR $=(1.5-38)\times10^{-3}$" (3.3 PDR modelling) [from (cite: gullberg2018; rybak2019; Mitsuhashi2021)]
- External data: median gas depletion time 140±70 Myr  
  > "median gas depletion time ($t_\mathrm{dep}=140\pm70$ Myr, (cite: FriasCastillo2023))" (4.2) [from (cite: FriasCastillo2023)]
- Simulation/model as data: SIMBA z=3.1 snapshot, 100 cMpc box, galaxies with Mmol>=1e11 Msun  
  > "We focus on the $z=3.1$ snapshot from the default 100-cMpc box." (4.3)

## Processing

### Calibration

- pipeline or manual: manual inspection and calibration with standard JVLA pipeline  
  > "We manually inspected and calibrated the data using the Common Astronomy Software Applications package" (2.2 JVLA observations)
- casa version: CASA 6.4.1 and 6.4.3  
  > "versions 6.4.1 and 6.4.3 and the standard JVLA pipeline" (2.2 JVLA observations)
- pipeline version: _not stated_
- archive products used as is: _not stated_
- flux calibrator: _not stated_
- flux scale uncertainty: _not stated_
- self calibration: _not stated_

### Imaging

- task: _not stated_
- deconvolver: _not stated_
- weighting robust: natural weighting (CLEANed cubes for spectral stack)  
  > "We adopt CLEANed cubes, made with natural weighting." (3.1)
- uv taper: _not stated_
- cell size: _not stated_
- image size: _not stated_
- masking: _not stated_
- multiscale scales: _not stated_
- continuum subtraction: uvcontsub if wide-band continuum S/N>=5  
  > "if the wide-band imaging shows a significant (S/N$\geq$5) continuum, subtract the continuum (constant signal) from the data using the `uvcontsub` task" (2.3)
- line free channels: _not stated_
- primary beam correction: _not stated_
- array combination: _not stated_
- smoothing: _not stated_
- final beam: _not stated_
- final rms: _not stated_

### Inherited from earlier work

- First 17 galaxies' observations and survey design  
  > "The observations of the first 17 galaxies (11 robust detections) were presented in (cite: FriasCastillo2023)." (2.2) [from (cite: FriasCastillo2023)]
- Individual-galaxy PDR models and ALMA [CI] observations  
  > "compared to the models for *individual* galaxies from the AS2VLA sample from (cite: Frias2024b)" (3.3) [from (cite: Frias2024b)]
- Mstar and SFR from MAGPHYS SED fits  
  > "$M_\star$ and SFR were derived by (cite: Dudzeviciute2020; simpson2020) using the high-redshift version of the MAGPHYS" (2.1) [from (cite: Dudzeviciute2020; simpson2020)]

### Not stated but needed to reproduce (our reading)

- JVLA/ALMA data identifiers and archive locations
- visibility weights and stacking weights for combining sources
- how galaxies were scaled/normalised before stacking
- emcee walkers, steps, burn-in
- exact uv bin choice used for fiducial fit
- ALMA [CI] project codes and reduction details
- PDRToolbox grid ranges and fitting procedure
- frequency ranges for continuum estimate

## Analysis recipe

1. **Prepare visibilities**: continuum subtraction, select ±1 FWHM velocity range, average to one channel, bin radially  
  > "(3) frequency-average the selected data into a single channel; (4) bin the resulting visibilities in radial bins with a size of 2.5, 5, and 10 k$\lambda$." (2.3)
   - software: CASA
   - parameter: radial bins 2.5, 5, 10 kλ  
  > "bin the resulting visibilities in radial bins with a size of 2.5, 5, and 10 k$\lambda$." (2.3)
   - fitting: _not stated_
   - validation: _not stated_
2. **Fit sizes in uv-plane**: fit point-source and exponential profiles; compare AIC/BIC; upper limits from 95th percentile  
  > "We fit each binned visibility function with: (1) point-source (constant signal) and (2) an exponential profile." (2.3)
   - software: emcee
   - fitting: MCMC with emcee, wide uniform priors in total flux and half-light radius  
  > "We assumed wide, uniform priors in total flux and half-light radius." (2.3)
   - validation: bandwidth change, baseline cut, excluding four extended sources, pointing error test  
  > "Changing the bandwidth used for calculation from 2 FWHM to 1 FWHM results in $\leq$10% change in the inferred $R_\mathrm{1/2}$." (3)
3. **PDR modelling**: PDRToolbox uniform-density models with CO(1-0), [CI], [CII], FIR  
  > "we estimate the gas density and far-UV irradiation using the `PDRToolbox` suite of uniform-density PDR models" (3.3)
   - software: PDRToolbox
   - assumption: extended component 13% of FIR; 20% of [CII] from ionised gas; geometric factor of two  
  > "We assume that 20% of the \[C ii\] emission arises from ionised gas" (3.3)
   - fitting: _not stated_
   - validation: varied CMB suppression, [CII] ionised fraction, [CI] size  
  > "To assess the sensitivity of our conclusions to the various assumptions made in the PDR modelling we have varied these as follows:" (3.3)

## Software

- **CASA** 6.4.1 and 6.4.3: calibration, uvcontsub, ft, imfit  
  > "versions 6.4.1 and 6.4.3 and the standard JVLA pipeline" (2.2)
- **emcee** : MCMC size fits  
  > "We utilise Monte-Carlo Markov chain modelling using the `emcee` package" (2.3)
- **PDRToolbox** : PDR models  
  > "`PDRToolbox` suite of uniform-density PDR models" (3.3)

## Numeric results

| quantity | value | uncertainty | units | step | quote |
|---|---|---|---|---|---|
| Stacked CO(1-0) half-light radius | 0.49 arcsec (3.8 kpc) | ±0.07 arcsec (±0.5 kpc) | arcsec / kpc | 2 | we adopt $R_{1/2}=0.49\pm0.07$$"$ (3.8$\pm$0.5 kpc at $z=3.1$) |
| Stacked [CI](1-0) size upper limit | ≤0.33 arcsec (2.6 kpc) | not stated | arcsec / kpc | 2 | ($\leq$ 0.33$"$ (2.6 kpc) |
| Stacked CO line FWHM | 590 | ±70 | km/s | 0 | line FWHM of 590$\pm$70 km s$^{-1}$ |
| PDR gas density | 10^4.4 | ±0.4 dex | cm^-3 | 3 | median $n=10^{4.4\pm0.4}$ cm$^{-3}$ |
| Filling factor at R1/2 | 0.8 | ±0.5 | percent | 3 | $\phi(R=R_{1/2})=0.8\pm0.5$% |
| Required inflow velocity | 50 | ±12 | km/s | 0 | We obtain $v_{in}=50\pm12$ km s$^{-1}$ |

## Qualitative findings

- No high-velocity wings indicating outflows in stacked spectrum  
  > "The lack of obvious outflow features indicates that the bulk of CO(1–0) is close to the systemic velocity." (3.1)

## Claim tuples

- H: CO(1-0) is more extended than dust and stars in DSFGs | E: uv-plane stack of 19 galaxies, exponential fit | R: R1/2 = 3.8±0.5 kpc vs 1.1-1.8 kpc dust and 2.7-3.0 kpc stars | F: Bulk of molecular gas lies outside star-forming region | **supported**
- H: Extended gas is smooth and diffuse | E: PDR modelling with filling factor | R: n~10^4.4, G~10^3.4, phi~0.8% | F: Clumpy dense clouds | **supported**

## Reasoning

- Why this data: _not stated_
- Why this method: _not stated_
- Alternative: Image-plane imfit does not give reliable size  
  > "Image-plane deconvolution with the `imfit` task in CASA does not yield a reliable source size." (2.3)
- How they decided it was enough: _not stated_
- Limitation (authors): Stacking azimuthal averaging smears out compact satellites  
  > "Unfortunately, our stacking averages the data in the azimuthal direction - i.e., smearing emission from compact satellites." (4.4)
- Caveat (inferred, ours): Stacked size depends on exponential-profile assumption and sample selection (S/N>=3 detections)
- Caveat (inferred, ours): PDR conclusions rest on assumed [CII]/FIR ranges from other samples
- Caveat (inferred, ours): [CI] size is marginal

## Reproducibility

- Data public (paper): _not stated_
- Products in archive: _not stated_
- Missing: Stacking weights and procedure details
- Missing: emcee settings
- Missing: ALMA project codes for [CI]
- Missing: PDR grid details
- Data volume (inferred): ~hundreds of GB (JVLA D-array, 19-30 sources, 2 GHz at 2 MHz channels)
- Score (inferred): 3/5, Methods outlined but stacking and fitting details and data identifiers missing.
- Rediscovery candidate: no, Data public status and recipe details not stated.

## Links

- Method: (cite: FriasCastillo2023) (AS2VLA survey and first observations)
- Companion: (cite: Frias2024b) (ALMA [CI] and PDR modelling of individual galaxies)
- Related: AS2VLA
- Related: AS2UDS
- Related: AS2COSMOS
- Related: Z-GAL
- Related: ALPINE
- Related: CRISTAL

## Checks

```json
{
 "quotes": 50,
 "quotes_ok": 50,
 "quote_pass_rate": 1.0,
 "quotes_too_long": 0,
 "unsupported_facts": 0,
 "project_codes": 0,
 "codes_not_in_text": [],
 "codes_not_in_obscore": [],
 "obscore_codes_not_in_card": [
  "2019.1.01600.S",
  "2021.1.01342.S"
 ],
 "codes_printed_but_missing": [
  "2021.1.01324.S"
 ],
 "numeric_results": 6,
 "numeric_problems": 0,
 "fill": {
  "facts": 70,
  "stated": 39,
  "rate": 0.557
 },
 "evidence_ok": true
}
```
