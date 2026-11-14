# The role of molecular gas in the nuclear regions of IRAS 00183-7111. ALMA and X-ray investigations of an ultraluminous infrared galaxy

`2018A&A...616A.127R` | Astronomy and Astrophysics 2018 | first author: Ruffa, I. | arXiv: 1805.06477 | DOI: 10.1051/0004-6361/201732268

Card schema 1.0 | model claude-sonnet-5-5 | depth full | type archival_reuse

## Science

- Fields: agn_and_quasars, nearby_galaxies
- Question: To what level can the molecular gas, traced by CO, be responsible for the AGN obscuration seen at X-ray energies in the ULIRG IRAS 00183-7111  
  > "the main aim is to verify at what level the molecular gas, traced by the CO, may be responsible for the obscuration observed at X-ray energies." (abstract)
- Target **IRAS 00183-7111**: coordinates _not stated_; z/distance z = 0.327  
  > "ultraluminous infrared galaxy (ULIRG) IRAS 00183-7111 ($z=0.327$)" (abstract); "conversion scale=4.772 kpc/", according to the adopted cosmology" (4.1 CO as molecular gas tracer); distance from LCDM cosmology H0=70, OmegaM=0.27, OmegaL=0.73  
  > "ultraluminous infrared galaxy (ULIRG) IRAS 00183-7111 ($z=0.327$)" (abstract); "conversion scale=4.772 kpc/", according to the adopted cosmology" (4.1 CO as molecular gas tracer)

## Data provenance

- ALMA projects: 2011.0.00034.S, 2011.0.00020.S
- bands: Band 3 (~87 GHz) and Band 6 (~270 GHz)  
  > "in two frequency bands: Band 3 ($\sim87$ GHz, project code: 2011.0.00034.S) and Band 6 ($\sim$270 GHz, project code: 2011.0.00020.S)" (3 ALMA observations)
- frequencies and spectral setup: Band 3: four 1.875 GHz SPWs, 128 channels of 15.6 MHz (~45 km/s); Band 6: 3840 x 0.98 MHz channels (~1 km/s), two configurations  
  > "four different 1.875 GHz-wide spectral windows, divided into 128 channels of 15.6 MHz in width ($\sim45$ km/s)" (3 ALMA observations)
- continuum bandwidth: _not stated_
- arrays: 12 m antennas, compact configuration  
  > "About 25 antennas of 12 m were arranged in a compact configuration" (3 ALMA observations)
- configurations: _not stated_
- baselines: Band 3: 15-400 m; Band 6: 18-269 m  
  > "with baselines lengths ranging from 15 to 400 m" (3 ALMA observations); "with baselines ranging from 18 to 269 m" (3 ALMA observations)
- angular resolution: Band 3 continuum beam 3.01"x2.05"; CO cube 3.1"x2.2"  
  > "synthesized beam FWHM of 3.01"$\times$2.05"" (3.1 Continuum imaging)
- max recoverable scale: _not stated_
- sensitivity: _not stated_
- time on source: Band 3: 78.1 min; Band 6: 215.14 min  
  > "for a total time-on-source of 78.1 min" (3 ALMA observations); "for a total time on source of 215.14 min" (3 ALMA observations)
- observing dates: Band 3: 18-31 Dec 2012; Band 6: 26 Nov 2011 to 23 Jan 2012  
  > "three observations taken between 18 and 31 December 2012" (3 ALMA observations)
- pi or archival as stated: Archival Cycle 0 data; Band 6 previously presented by Imanishi14  
  > "We calibrated and analysed ALMA archival Cycle 0 data in two bands (Bands 3 and 6)." (abstract)
- Line: CO J=1-0 (115.271 GHz)
- Line: HCN J=4-3 (354.505 GHz)
- Line: HCO+ J=4-3 (356.734 GHz)
- Line: HNC J=4-3 (362.630 GHz)
- Other facility **Chandra**: 22.8 ks ACIS-S X-ray spectrum (archival)  
  > "The 22.8 ks *Chandra* observation was taken on 13 February 2013 using the ACIS-S detector." (5.1 Chandra data)
- Other facility **XMM-Newton**: X-ray spectra (archival)  
  > "observed by XMM-*Newton* on 16 April 2013 with a nominal integration time of 22.2 ks" (5.2 XMM-Newton data)
- Other facility **NuSTAR**: 105 ks hard X-ray spectra, provided by the PI  
  > "for a total exposure time of 105 ks" (5.3 NuSTAR data)
- Other facility **Herschel**: archival FIR flux densities for SED  
  > "radio (cite: Norris12) and Herschel (archival) data" (4.4 Continuum analysis)
- External data: Radio data and spectral index (0.84-87 GHz) alpha=-1.38 for SED  
  > "reported a radio spectral index (in the range 0.84$-$87 GHz) $\alpha=-1.38$" (4.4 Continuum analysis) [from (cite: Norris12)]
- External data: Dust absorption coefficient k_o at 2141 GHz  
  > "we assumed the value of k$_{o}$ tabulated by (cite: Li01) at the reference observed frequency $\nu_{o}=2141$ GHz" (4.4 Continuum analysis) [from (cite: Li01)]
- External data: NuSTAR data courtesy of PI  
  > "*NuSTAR* data were obtained by courtesy of the PI (K. Iwasawa; see (cite: Iwasawa17) for details)" (5 X-ray observations and spectral fitting) [from (cite: Iwasawa17)]

## Processing

### Calibration

- pipeline or manual: Reprocessed from ASDM with standard manual-style calibration in CASA, each dataset separately  
  > "We calibrated each dataset separately, starting from the ASDM data format" (3 ALMA observations)
- casa version: CASA 3.4.2  
  > "The data reduction was conducted using CASA, version 3.4.2, performing a standard calibration procedure." (3 ALMA observations)
- pipeline version: _not stated_
- archive products used as is: No; reprocessed because new flux model libraries gave more reliable flux calibration  
  > "Data re-processing is strongly suggested for Cycle 0 data, mainly because new flux model libraries were released after the archival data reduction" (3 ALMA observations)
- flux calibrator: Neptune or Callisto  
  > "either Neptune or Callisto was used for the absolute flux calibration" (3 ALMA observations)
- flux scale uncertainty: ~10%  
  > "the quoted errors account for the $\sim$10% flux calibration uncertainty of the ALMA data" (3.1 Continuum imaging)
- self calibration: Multiple rounds of phase-only self-calibration on Band 3 continuum  
  > "Multiple rounds of phase-only self calibration were performed" (3.1 Continuum imaging)

### Imaging

- task: CLEAN, MFS mode for continuum; velocity mode for cubes  
  > "Continuum maps were produced using the CLEAN task in *Multi Frequency Synthesis (MFS)* mode" (3.1 Continuum imaging)
- deconvolver: _not stated_
- weighting robust: natural and Briggs robust=0.5  
  > "both natural and Briggs weighting (robust=0.5)" (3.1 Continuum imaging)
- uv taper: _not stated_
- cell size: _not stated_
- image size: _not stated_
- masking: Interactive clean regions to 1.5x rms threshold; moment 0 masked-moment technique with 1.5 sigma threshold  
  > "cleaned in regions of line emission (identified interactively) to a threshold equal to 1.5 times the rms noise level" (3.2 Line imaging)
- multiscale scales: _not stated_
- continuum subtraction: uvcontsub, first-order polynomial fit of line-free channels  
  > "line-free channels are identified and a first-order polynomial fit of them is performed" (3.2 Line imaging)
- line free channels: _not stated_
- primary beam correction: _not stated_
- array combination: _not stated_
- smoothing: CO cube at ~90 km/s (two channels)  
  > "setting a spectral resolution of $\sim90$ km s$^{-1}$ (two channels width)" (3.2 Line imaging)
- final beam: Band 3 3.01"x2.05"; 270 GHz 2.35"x1.19"; 263 GHz 2.48"x1.31"  
  > "The 270 GHz (1.1 mm, Band 6) continuum image has synthesized beam FWHM of 2.35"$\times$1.19"." (3.1 Continuum imaging)
- final rms: Band 3 continuum 16 uJy/beam; CO cube ~0.17 mJy/beam  
  > "yielding a 1$\sigma$ root-mean square (rms) noise level of 16 $\mu$Jy beam$^{-1}$" (3.1 Continuum imaging)

### Inherited from earlier work

- Masked moment technique for moment 0 maps  
  > "created using the masked moment technique (cite: Dame11)" (4.1 CO as molecular gas tracer) [from (cite: Dame11); (cite: Davis17)]
- Column density method assuming spherical gas distribution  
  > "Following the method adopted by (cite: Gilli14), we assumed a spherical symmetry of the molecular gas regions" (6.1 Cold absorber: X-ray versus ALMA) [from (cite: Gilli14)]
- SFR from CO luminosity via L_IR-L'CO relation  
  > "Following (cite: Carilli13)" (4.1 CO as molecular gas tracer) [from (cite: Carilli13)]

### Not stated but needed to reproduce (our reading)

- Line-free channels used for uvcontsub
- Clean iteration limits, cell and image sizes
- Primary beam correction details
- Herschel flux densities used in SED fit
- Exact CASA flux model library version
- Self-calibration solution intervals
- Masking details for continuum CLEAN

## Analysis recipe

1. **Recalibrate and image ALMA data**: Recalibrate from ASDM, combine same-configuration datasets, CLEAN continuum (natural and robust 0.5) with phase-only self-cal  
  > "once a reliable calibration was obtained, we combined data with the same spectral configuration into one calibrated dataset" (3 ALMA observations)
   - software: CASA
   - fitting: _not stated_
   - validation: _not stated_
2. **Make CO cube and moment 0, measure flux and size**: uvcontsub, CLEAN cube at ~90 km/s, masked moment 0, 2-D Gaussian fit for size  
  > "We also performed a 2-D Gaussian fit of the moment 0 map within the region covered by the CO emission" (4.1 CO as molecular gas tracer)
   - software: CASA
   - fitting: 2-D Gaussian  
  > "A 2-D Gaussian fit was performed in each map within circles including all the emission" (Continuum analysis)
   - validation: _not stated_
3. **Derive L'CO, H2 mass, SFR**: Solomon05 L'CO formula; M(H2)=alpha L'CO; Carilli13 L_IR relation; SFR=delta_MF x 1e-10 L_IR  
  > "we used the typical conversion factor associated with ULIRGs, $\alpha=0.8$ M$_{\odot}$ ($K~km~s^{-1}~pc^{2}$)$^{-1}$" (4.1 CO as molecular gas tracer)
   - assumption: alpha=0.8; Salpeter IMF delta_MF=1.8  
  > "Assuming a Salpeter IMF, $\delta_{MF}=1.8$ (cite: Kennicutt98)" (4.1 CO as molecular gas tracer)
   - fitting: _not stated_
   - validation: Compared with Mao14 SFR  
  > "comparable (within the errors) with that derived by (cite: Mao14)" (4.1 CO as molecular gas tracer)
4. **Fit dust SED to estimate thermal contribution**: Single-temperature modified blackbody to Herschel data, extrapolate to ALMA frequencies  
  > "we fit the FIR part of the SED in Figure 5 (based on the archival Herschel flux densities) with a single-temperature modified black-body function" (4.4 Continuum analysis)
   - parameter: beta fixed 1.5; Td and Md free  
  > "We fixed the value of the emissivity index to 1.5." (4.4 Continuum analysis)
   - assumption: Herschel flux uncertainty 20%  
  > "assuming a 20% flux density uncertainty in the archival Herschel measurements" (4.4 Continuum analysis)
   - fitting: _not stated_
   - validation: _not stated_
5. **Fit X-ray spectra and compare NH with molecular column**: XSPEC fits of Chandra, XMM, NuSTAR individually and jointly with XILLVER; molecular NH from uniform sphere  
  > "reduced spectra were analysed using XSPEC software, version 12.9.0" (5 X-ray observations and spectral fitting)
   - software: XSPEC, CIAO, SAS
   - parameter: Gamma fixed 1.9; inclination fixed 87 deg; errors 90% confidence  
  > "with the photon index fixed at 1.9. The inclination angle was fixed at its hard limit of $87^{\circ}$." (5.4 Broad-band spectral fitting)
   - assumption: uniform sphere of radius median of axes (6.4 kpc)  
  > "taking as radius the median value between the major and the minor axis of the elliptical source size" (6.1 Cold absorber: X-ray versus ALMA)
   - fitting: Cash statistic for Chandra, chi2 for XMM/NuSTAR/joint  
  > "Due to the limited number of spectral counts (133), we chose to apply the Cash statistics, which is more appropriate in low-count regimes" (Chandra data)
   - validation: _not stated_

## Software

- **CASA** 3.4.2: calibration, imaging, uvcontsub  
  > "The data reduction was conducted using CASA, version 3.4.2" (3 ALMA observations)
- **XSPEC** 12.9.0: X-ray spectral fitting  
  > "analysed using XSPEC software, version 12.9.0" (5 X-ray observations and spectral fitting)
- **CIAO** 4.7: Chandra reprocessing  
  > "The raw data were reprocessed using CIAO software (version 4.7)." (5.1 Chandra data)
- **SAS** 14.0: XMM reprocessing  
  > "reprocessed them using the Science Analysis System (SAS) software, version 14.0" (5.2 XMM-Newton data)

## Numeric results

| quantity | value | uncertainty | units | step | quote |
|---|---|---|---|---|---|
| CO(1-0) integrated flux | 2.56 | 0.26 | Jy km/s | 2 | S$_{CO}=(2.56\pm0.26)$ Jy km s$^{-1}$ at 86.8 GHz |
| L'CO | 1.42e10 | +0.08/-0.12 e10 | K km/s pc^2 | 3 | $L'_{CO}=1.42^{+0.08}_{-0.12}\times10^{10}$ K km s$^{-1}$ pc$^{2}$ |
| M(H2) | 1.14e10 | 0.11e10 | Msun | 3 | M$(H_{2})=(1.14\pm0.11)\times10^{10}$ M$_{\odot}$ |
| SFR | 260 | 28 | Msun/yr | 3 | the SFR results to be $260\pm28$ M$_{\odot}$ yr$^{-1}$ |
| Dust temperature | 68 | 10 | K | 4 | $T_{d}=68\pm10$ K and $M_{d}=(2.7\pm1.4)\times10^{7}$ M$_{\odot}$ |
| ALMA spectral index 87-270 GHz | -0.24 | 0.10 | dimensionless | 4 | $\alpha=-0.24\pm0.10$ between 87 and 270 GHz |
| CO-continuum offset | 0.53 arcsec (2.5 kpc) | 0.08 arcsec (0.4 kpc) | arcsec | 2 | The observed offset is 0.53"$\pm$0.08" ($\sim7 \sigma$), corresponding to $2.5\pm0.4$ kpc. |
| Molecular column density | 8.0e21 | 0.9e21 | cm^-2 | 5 | obtaining N$_{H}=(8.0\pm0.9)\times10^{21}$ cm$^{-2}$ |
| X-ray broad-band NH | 6.8e22 | +2.1/-1.5 e22 | cm^-2 | 5 | $6.8^{+2.1}_{-1.5}\times10^{22}$ cm$^{-2}$ |
| CO line FWHM | 400 | 27 | km/s | 2 | FWHM$=400\pm27$ km s$^{-1}$ |

## Qualitative findings

- Molecular gas column is ~1/8 of X-ray column, so it may contribute only a fraction of obscuration  
  > "The molecular column density derived from the CO is only $\sim$1/8 the column density inferred from the X-ray data" (6.1 Cold absorber: X-ray versus ALMA)
- Tentative blueshifted CO wing and eastern protrusion hint at molecular outflow  
  > "we can infer a hint of the presence of a molecular outflow from the CO emitting region" (4.2 Outflow hint)

## Claim tuples

- H: Does CO-traced molecular gas account for the X-ray obscuration? | E: Compare NH from CO mass in a uniform sphere with X-ray fitted NH | R: 8.0e21 vs 6.8e22 cm^-2 | F: Molecular gas may contribute only a fraction; link not straightforward | **partially**
- H: Is there a starburst in the molecular gas regions? | E: CO luminosity to SFR | R: SFR 260±28 Msun/yr | F: Vigorous starburst | **supported**
- H: Is HCN excitation AGN-like? | E: HCN detection and HCO+/HNC upper limits | R: HCN/HCO+>2, HCN/HNC>3 | F: Suggests AGN-like excitation, no solid conclusion | **partially**

## Reasoning

- Why this data: Source selected from Spoon diagram as highly obscured AGN candidate  
  > "selected from the Spoon diagnostic diagram as a highly obscured active galactic nucleus (AGN) candidate" (abstract)
- Why this method: _not stated_
- How they decided it was enough: _not stated_
- Limitation (authors): Low ALMA spatial/spectral resolution and limited X-ray statistics prevent strong conclusions; interpretation speculative  
  > "Therefore, our interpretation remains purely speculative and needs to be tested with data of better quality" (6.1 Cold absorber: X-ray versus ALMA)
- Caveat (inferred, ours): Uniform sphere column density is crude and alpha uncertain
- Caveat (inferred, ours): Moment 0 and flux depend on mask choices
- Caveat (inferred, ours): Dust SED fit has fixed beta and few Herschel points
- Caveat (inferred, ours): Chandra, XMM, NuSTAR epochs differ from ALMA epochs

## Reproducibility

- Data public (paper): ALMA archival Cycle 0 data; Chandra and XMM archival; NuSTAR by courtesy of PI  
  > "The X-ray properties of I00183 were studied using archival *Chandra* and XMM-*Newton* data" (5 X-ray observations and spectral fitting)
- Products in archive: _not stated_
- Missing: Line-free channels and clean parameters
- Missing: Herschel flux values
- Missing: Exact CASA flux model library
- Missing: NuSTAR data access
- Data volume (inferred): ~50-100 GB of ALMA raw data for both projects
- Score (inferred): 3/5, ALMA data public and recipe mostly described with numeric results, but several imaging parameters and Herschel inputs are missing.
- Rediscovery candidate: yes, Public Cycle 0 data, stated CASA workflow, and numeric CO flux, mass, SFR and offset results.

## Links

- Method: (cite: Dame11); (cite: Davis17) (Masked moment technique)
- Method: (cite: Solomon05) (L'CO formula)
- Companion: (cite: Imanishi14) (Earlier analysis of same Band 6 data)
- Companion: (cite: Iwasawa17) (NuSTAR data and X-ray study of same source)
- Companion: (cite: Mao14) (ATCA CO(1-0) detection)

## Checks

```json
{
 "quotes": 80,
 "quotes_ok": 80,
 "quote_pass_rate": 1.0,
 "quotes_too_long": 0,
 "unsupported_facts": 0,
 "project_codes": 2,
 "codes_not_in_text": [],
 "codes_not_in_obscore": [],
 "obscore_codes_not_in_card": [],
 "codes_printed_but_missing": [],
 "numeric_results": 10,
 "numeric_problems": 0,
 "fill": {
  "facts": 80,
  "stated": 56,
  "rate": 0.7
 },
 "evidence_ok": true
}
```
