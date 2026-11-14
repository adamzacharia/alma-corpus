# The ALMA-PILS survey: First detections of ethylene oxide, acetone and propanal toward the low-mass protostar IRAS 16293-2422

`2017A&A...597A..53L` | Astronomy and Astrophysics 2017 | first author: Lykke, J. M. | arXiv: 1611.07314 | DOI: 10.1051/0004-6361/201629180

Card schema 1.0 | model claude-sonnet-5-5 | depth full | type observational_alma_primary

## Science

- Fields: astrochemistry, star_formation
- Question: Are ethylene oxide, acetone and propanal present toward the low-mass protostellar binary IRAS16293-2422, and what are their excitation temperatures, column densities and isomer abundance ratios compared with high-mass sources and chemical models?  
  > "Our aim is to start the process of compiling an inventory of oxygen-bearing complex organic molecules toward the solar-type Class 0 protostellar binary IRAS 16293-2422" (abstract)
- Target **IRAS 16293-2422 (component B)**: coordinates pointing center 16h32m22.72s, -24d28m34.3s (J2000); spectrum extracted at 16h32m22.58s, -24d28m32.8s  
  > "a protostellar Class 0 binary system, located at a distance of 120 pc (cite: Loinard2008)" (Introduction); "corresponding to an offset of ($-$0.45$\ensuremath{''}$ ; $-$0.30$\ensuremath{''}$) in the southwestern direction relative to the continuum peak of IRAS16293B" (Analysis and results); z/distance 120 pc  
  > "a protostellar Class 0 binary system, located at a distance of 120 pc (cite: Loinard2008)" (Introduction); "corresponding to an offset of ($-$0.45$\ensuremath{''}$ ; $-$0.30$\ensuremath{''}$) in the southwestern direction relative to the continuum peak of IRAS16293B" (Analysis and results); distance from Loinard et al. 2008  
  > "a protostellar Class 0 binary system, located at a distance of 120 pc (cite: Loinard2008)" (Introduction); "corresponding to an offset of ($-$0.45$\ensuremath{''}$ ; $-$0.30$\ensuremath{''}$) in the southwestern direction relative to the continuum peak of IRAS16293B" (Analysis and results)

## Data provenance

- ALMA projects: 2013.1.00278.S
- bands: Band 7 (~0.8 mm) used  
  > "In this paper we only utilise data from the Band 7 part of the survey (project-id: 2013.1.00278.S)." (Observations)
- frequencies and spectral setup: 329.15-362.90 GHz; 18 settings, each 1875 MHz in four 468.75 MHz windows; 0.244 MHz (~0.2 km/s) resolution, 1920 channels per window  
  > "In total 18 spectral settings were observed: each setting covers a bandwidth of 1875 MHz (over four different spectral windows of 468.75 MHz wide)." (Observations)
- continuum bandwidth: _not stated_
- arrays: 12 m array and ACA (7 m)  
  > "Data were obtained from both the array of 12 m dishes (typically 35–40 antenna in the array at the time of observations) and the Atacama Compact Array (ACA)" (Observations)
- configurations: _not stated_
- baselines: _not stated_
- angular resolution: beams ~0.4-0.7'' native; analysis cubes use circular 0.5'' beam  
  > "The data used in this paper were produced with a circular restoring beam of 0.5$\ensuremath{''}$ to facilitate the analysis across the different spectral windows." (Observations)
- max recoverable scale: _not stated_
- sensitivity: RMS 6-8 mJy/beam/channel; better than 5 mJy/beam km/s  
  > "approximately 6–8 mJy beam$^{-1}$ channel$^{-1}$, which translates into a uniform sensitivity better than 5 mJy beam$^{-1}$ km s$^{-1}$" (Observations)
- time on source: ~13 min per setting for 12 m, double for ACA  
  > "Each setting was observed with approximately 13 minutes integration on source (execution blocks of approximately 40 minutes including calibrations) for the 12 m array and double that for the ACA." (Observations)
- observing dates: _not stated_
- pi or archival as stated: PILS program, PI Jes K. Jørgensen  
  > "IRAS16293 was observed as part of the PILS program (PI: Jes K. Jørgensen)" (Observations)
- Line: ethylene oxide (c-C2H4O) 20 lines detected (329-363 GHz band)
- Line: propanal (C2H5CHO) 44 lines detected (329-363 GHz band)
- Line: acetone (CH3COCH3) 186 lines detected (329-363 GHz band)
- Line: acetaldehyde (CH3CHO) used for ratios (not stated)
- External data: Spectroscopic data for propanal and ethylene oxide from CDMS; acetone and acetaldehyde from JPL  
  > "are available from the CDMS database, while the spectroscopic data for acetone (cite: Groner2002) and acetaldehyde (cite: Kleiner1996) are available from the JPL database." (Analysis and results) [from Groner2002; Kleiner1996; Müller 2001/2005; Pickett 1998]
- External data: Comparison abundance ratios for Sgr B2(N), massive SF regions and chemical models  
  > "Chemical model: peak gas-phase | 0.22: 0.83: 0.07$^{(c)}$" (Table 2) [from Belloche2013; Ikeda2001; Garrod2013; Occhiogrosso2014]
- Simulation/model as data: Reference model of synthetic spectra of previously detected complex organics, used to identify blends  
  > "we create a reference model containing the synthetic spectrum of emission lines of previously detected complex organic molecules" (Analysis and results)

## Processing

### Calibration

- pipeline or manual: _not stated_
- casa version: _not stated_
- pipeline version: _not stated_
- archive products used as is: _not stated_
- flux calibrator: _not stated_
- flux scale uncertainty: _not stated_
- self calibration: phase-only self-calibration on continuum images, applied to full cubes  
  > "a phase-only self-calibration was performed on the continuum images and applied to the full datacubes before combining the 12 m array and ACA data" (Observations)

### Imaging

- task: _not stated_
- deconvolver: _not stated_
- weighting robust: _not stated_
- uv taper: _not stated_
- cell size: _not stated_
- image size: _not stated_
- masking: _not stated_
- multiscale scales: _not stated_
- continuum subtraction: statistical subtraction per spectral window  
  > "A subtraction of the continuum was therefore done statistically for each spectral window" (Observations)
- line free channels: _not stated_
- primary beam correction: _not stated_
- array combination: 12 m and ACA data combined before final cleaning and imaging  
  > "before combining the 12 m array and ACA data and performing the final cleaning and imaging" (Observations)
- smoothing: _not stated_
- final beam: circular 0.5''  
  > "The data used in this paper were produced with a circular restoring beam of 0.5$\ensuremath{''}$" (Observations)
- final rms: _not stated_

### Inherited from earlier work

- Observing log, data reduction and overview of the PILS data  
  > "An observing log, a description of the data reduction and a first overview of the data are presented in (cite: Jorgensen2016)" (Observations) [from Jorgensen2016]
- Continuum maps and details of continuum subtraction  
  > "(for continuum maps and more details see (cite: Jorgensen2016))" (Observations) [from Jorgensen2016]
- Synthetic spectrum LTE approach  
  > "The synthetic spectra are computed following the approach described in (cite: Goldsmith1999)." (Analysis and results) [from Goldsmith1999]

### Not stated but needed to reproduce (our reading)

- CASA version and calibration procedure (deferred to PILS overview paper)
- Clean parameters: robust, deconvolver, masks, line-free channels
- Step sizes of the column-density grid
- Exact lines (ten per species) used in the chi-squared fit
- Propanal vibrational/conformational correction details beyond the factor 1.489
- Code used to produce synthetic spectra

## Analysis recipe

1. **Map emission and choose extraction position**: Inspect line maps of the four species; extract spectrum at an offset from the continuum peak of IRAS16293B to reduce absorption  
  > "we extracted a spectrum from a position at $\alpha_{\rm J2000}=16^\mathrm{h}$32$^\mathrm{m}$22.58$^\mathrm{s}$" (Analysis and results)
   - parameter: V_LSR = 2.7 km/s  
  > "corrected for the LSR velocity (V$_\mathrm{LSR}$ = 2.7 km s$^{-1}$)" (Analysis and results)
   - fitting: _not stated_
   - validation: _not stated_
2. **Identify unblended lines**: Compare with reference model of known species; exclude severely blended lines; check CDMS/JPL  
  > "we have also checked the lines of interest against other species in the CDMS and JPL databases" (Analysis and results)
   - software: CASSIS
   - fitting: _not stated_
   - validation: _not stated_
3. **Fit Tex and Ntot with LTE synthetic spectra**: Grid search minimizing reduced chi-squared on ~10 optically thin non-blended lines per species, using the average of peak channels  
  > "we varied the column density from $1.0 \times 10^{14}~\mathrm{cm}^{-2}$ – $1.0 \times 10^{18}~\mathrm{cm}^{-2}$ with small increments and the temperature from 100 K – 400 K with increments of 25 K" (Analysis and results)
   - parameter: FWHM 1.0 km/s, source size 0.5'', tau <= 0.1  
  > "the source size remained fixed at 1.0 km s$^{-1}$ and $0.5 \ensuremath{''}$, respectively" (Analysis and results)
   - assumption: LTE, Gaussian line profiles, common Tex = 125 K for all species  
  > "we therefore assume $T_\mathrm{ex}=125$ K for all molecules" (Analysis and results)
   - fitting: Reduced chi-squared grid minimization  
  > "we identified approximately ten reasonably non-blended and optically thin $( \tau \le 0.1)$ lines for each species, which we use to minimize the reduced chi-squared statistic" (Analysis and results)
   - validation: Synthetic spectra overlaid on all predicted lines; detection requires integrated strength > 3 sigma and good fit  
  > "the integrated line strength over FWHM is larger than three times the statistical uncertainty" (Analysis and results)
4. **Compute isomer ratios and compare with literature and models**: Ratios of column densities compared with Sgr B2(N), massive SF regions and Garrod 2013 / Occhiogrosso 2014 models  
  > "Table [\[tcompare\]](#tcompare) lists the different abundance ratios" (Discussion)
   - fitting: _not stated_
   - validation: _not stated_

## Software

- **CASSIS** : Checking lines against CDMS and JPL databases  
  > "we have also checked the lines of interest against other species in the CDMS and JPL databases" (Analysis and results)

## Numeric results

| quantity | value | uncertainty | units | step | quote |
|---|---|---|---|---|---|
| Excitation temperature (common) | 125 | 25 K | K | 3 | the uncertainties are estimated to $\sim 50 \%$ and 25 K on the column density and the emission temperature, respectively |
| N_tot acetone | 1.7e16 | ~50% | cm^-2 | 3 | Acetone / CH$_3$COCH$_3$ / $1.7 \times 10^{16}$ |
| N_tot propanal | 2.2e15 | ~50% | cm^-2 | 3 | Propanal / C$_2$H$_5$CHO / $2.2 \times 10^{15}$ |
| N_tot acetaldehyde | 7.0e16 | ~50% | cm^-2 | 3 | Acetaldehyde / CH$_3$CHO / $7.0 \times 10^{16}$ |
| N_tot ethylene oxide | 6.1e15 | ~50% | cm^-2 | 3 | Ethylene oxide / c-C$_2$H$_4$O / $6.1 \times 10^{15}$ |
| CH3COCH3/C2H5CHO ratio | 8 | not stated | dimensionless | 4 | IRAS16293-2422 / 8 / 12 / this study |
| CH3CHO/c-C2H4O ratio | 12 | not stated | dimensionless | 4 | IRAS16293-2422 / 8 / 12 / this study |
| Vinyl alcohol (syn) upper limit | 2e15 | not stated | cm^-2 | 3 | With a conservative upper limit of 2 $\times$ 10$^{15}$ cm$^{-2}$ for the syn form |

## Qualitative findings

- Emission of all species is compact (~0.5'') and originates near the protostar, consistent with coexistence in the same gas  
  > "The high resolution maps demonstrate that the emission for all investigated species originates from the compact central region close to the protostar." (abstract)

## Claim tuples

- H: Ethylene oxide, acetone and propanal are present toward a low-mass protostar | E: Fit LTE synthetic spectra to PILS Band 7 spectrum of IRAS16293B | R: 20, 44 and 186 lines detected | F: First detections of these species toward a low-mass protostar | **supported**
- H: The species coexist in the same gas | E: Compare maps and fit Tex | R: Extent ~0.5'' for all; common Tex ~125 K | F: Consistent with coexistence | **supported**
- H: Isomer ratios in low-mass protostar resemble high-mass sources and chemical models | E: Compare ratios with Sgr B2(N), Ikeda 2001 and models | R: Ratios 8 and 12 comparable to high-mass; up to an order of magnitude above models | F: Models need missing reactions, better rates or different physical conditions | **supported**

## Reasoning

- Why this data: IRAS16293B lines are narrower, easing separation of blended lines  
  > "Consequently IRAS16293B is therefore better for separation of blended lines and identification of new species" (Analysis and results)
- Why this method: _not stated_
- Alternative: Peak pixel spectrum rejected because optically thick continuum causes strong absorption  
  > "since the continuum is optically thick and very bright there are also very prominent absorption lines in the spectrum" (Analysis and results)
- How they decided it was enough: _not stated_
- Limitation (authors): Tex hard to constrain for propanal and acetone; uncertainties dominated by LTE and Gaussian assumptions  
  > "it is difficult to constrain the excitation temperature for propanal and acetone" (Analysis and results)
- Caveat (inferred, ours): Single-position spectrum and fixed 0.5'' source size affect column densities
- Caveat (inferred, ours): Common Tex assumed rather than fitted for acetone and propanal
- Caveat (inferred, ours): No formal uncertainties from fit; ~50% is a rough estimate
- Caveat (inferred, ours): Dust optical depth and absorption not modelled

## Reproducibility

- Data public (paper): Data cited by project code 2013.1.00278.S; public status not stated  
  > "This paper makes use of the following ALMA data: ADS/JAO.ALMA#2013.1.00278.S." (Acknowledgements)
- Products in archive: _not stated_
- Missing: Calibrated PILS cubes (Jørgensen et al. 2016 reduction)
- Missing: Spectral-synthesis code
- Missing: Reference-model parameters for known molecules
- Missing: Line selection list for fits
- Data volume (inferred): Large: 18 settings x 4 windows x 1920 channels, 12 m + ACA; hundreds of GB raw
- Score (inferred): 3/5, Method is simple and described, but data reduction and line selection details are deferred or missing.
- Rediscovery candidate: no, Requires the PILS reduction and unspecified line selections and synthetic-spectrum code.

## Links

- Method: Jorgensen2016 (PILS survey overview, data reduction, continuum subtraction)
- Method: Goldsmith1999 (LTE synthetic spectrum approach)
- Companion: Coutens2016 (Earlier PILS detection of species used in the reference model)
- Related: PILS (Protostellar Interferometric Line Survey)

## Checks

```json
{
 "quotes": 56,
 "quotes_ok": 56,
 "quote_pass_rate": 1.0,
 "quotes_too_long": 0,
 "unsupported_facts": 0,
 "project_codes": 1,
 "codes_not_in_text": [],
 "codes_not_in_obscore": [],
 "obscore_codes_not_in_card": [],
 "codes_printed_but_missing": [],
 "numeric_results": 8,
 "numeric_problems": 0,
 "fill": {
  "facts": 68,
  "stated": 36,
  "rate": 0.529
 },
 "evidence_ok": true
}
```
