# The Abundance of H<SUB>2</SUB>O and HDO in Orion Kl from Herschel/HIFI

`2013ApJ...770..142N` | The Astrophysical Journal 2013 | first author: Neill, Justin L. | arXiv: 1305.2247 | DOI: 10.1088/0004-637X/770/2/142

Card schema 1.0 | model claude-sonnet-5-5 | depth light | type multi_facility_alma_minor

## Science

- Fields: star_formation, astrochemistry, milky_way_ism
- Question: What are the abundances of H2O and HDO (and HDO/H2O ratios) in the Hot Core, Compact Ridge and Plateau components of Orion KL, and where does the highly excited water component lie?  
  > "we derive the abundances of H$_2$O and HDO in the different spatial/velocity components associated with this massive star-forming region: the Hot Core, Compact Ridge, and Plateau." (abstract)
- Target **Orion KL**: coordinates ALMA phase center 05h35m14.35s, -05d22'35'' (J2000)  
  > "The Orion Kleinmann-Low nebula (Orion KL) is the nearest massive star-forming region, at a distance of 414 $\pm$ 7 pc (cite: menten07)" (Introduction); z/distance 414 ± 7 pc  
  > "The Orion Kleinmann-Low nebula (Orion KL) is the nearest massive star-forming region, at a distance of 414 $\pm$ 7 pc (cite: menten07)" (Introduction); distance from Menten et al. 2007  
  > "The Orion Kleinmann-Low nebula (Orion KL) is the nearest massive star-forming region, at a distance of 414 $\pm$ 7 pc (cite: menten07)" (Introduction)

## Data provenance

- ALMA projects: 2011.0.00009.SV
- bands: Band 6 (214-247 GHz)  
  > "The interferometric observations presented here are part of a Band 6 survey (214–247 GHz) collected by ALMA as part of its science verification." (2.2 ALMA)
- frequencies and spectral setup: _not stated_
- continuum bandwidth: _not stated_
- arrays: 16 antennas, 12 m  
  > "with a total of 16 antennas, all 12 m in diameter." (2.2 ALMA)
- configurations: _not stated_
- baselines: 13 to 202 kλ  
  > "The projected baselines ranged from 13 to 202 k$\lambda$." (2.2 ALMA)
- angular resolution: 1.77''x1.16'' (225.896 GHz); 1.43''x1.03'' (241.561 GHz)  
  > "the angular resolution of the image at 225.896 GHz was $1.77'' \times 1.16''$, with a P.A. of -5.6$^\circ$" (2.2 ALMA)
- max recoverable scale: _not stated_
- sensitivity: _not stated_
- time on source: _not stated_
- observing dates: 20 January 2012  
  > "The observations were taken on 20 January 2012" (2.2 ALMA)
- pi or archival as stated: ALMA science verification data, publicly available  
  > "The full calibrated measurement set is publicly available at https://almascience.nrao.edu/alma-data/science-verification." (2.2 ALMA)
- Line: HDO 3_12-2_21 (225896.7 MHz)
- Line: HDO 2_11-2_12 (241561.6 MHz)
- Other facility **Herschel/HIFI**: HEXOS full spectral survey of Orion KL; main data for H2O isotopologue analysis  
  > "a full spectral survey of Orion KL with HIFI (covering the frequency ranges 479.5–1280.0 and 1426.0–1906.8 GHz) has been obtained" (Introduction)
- Other facility **IRAM 30m**: Single-dish HDO fluxes from Jacq et al. to check ALMA flux recovery  
  > "we compared the line fluxes to the single-dish observations of these two transitions with the IRAM 30 m telescope by (cite: jacq90)." (3.3.1 HDO and HD18O)
- Other facility **ISO**: Far-IR continuum at shorter wavelengths  
  > "and from Infrared Space Observatory surveys for shorter wavelengths (cite: vandishoeck98; lerate06)." (3.2 Strategy)
- External data: 16O/18O = 250 ± 135  
  > "We assume $^{16}$O/$^{18}$O = $250 \pm 135$ (cite: tercero10)" (3.2 Strategy) [from (cite: tercero10)]
- External data: 18O/17O = 3.6 ± 0.7  
  > "$^{18}$O/$^{17}$O = $3.6 \pm 0.7$ (cite: persson07)" (3.2 Strategy) [from (cite: persson07)]
- External data: HDO collisional rates  
  > "for HD$^{16}$O and HD$^{18}$O we use the rates of (cite: faure12) for HDO." (3.2 Strategy) [from (cite: faure12)]
- External data: Hot Core N(H2) = 3.1e23 cm-2  
  > "Using an H$_2$ column density of $3.1 \times 10^{23}$ cm$^{-2}$ (cite: plume12)" (3.3.2 H218O and H217O) [from (cite: plume12)]

## Processing

### Calibration

- pipeline or manual: _not stated_
- casa version: _not stated_
- pipeline version: _not stated_
- archive products used as is: Calibrated measurement set from SV website  
  > "The full calibrated measurement set is publicly available" (2.2 ALMA)
- flux calibrator: Callisto (flux); J0607-085 (phase)  
  > "Callisto was used as the absolute flux calibrator, and the quasar J0607-085 was used as the phase calibrator." (2.2 ALMA)
- flux scale uncertainty: _not stated_
- self calibration: _not stated_

### Imaging

- task: CASA CLEAN  
  > "deconvolved using the Common Astronomy Software Applications (CASA) package[^4] with the CLEAN algorithm." (2.2 ALMA)
- deconvolver: _not stated_
- weighting robust: Briggs robust 0.0  
  > "Robust weighting was used with a Briggs parameter of 0.0" (2.2 ALMA)
- uv taper: _not stated_
- cell size: 0.2''  
  > "and a pixel size of $0.2''$." (2.2 ALMA)
- image size: _not stated_
- masking: _not stated_
- multiscale scales: _not stated_
- continuum subtraction: continuum from line-free channels subtracted  
  > "the continuum as estimated from line-free spectral channels near the HDO transitions was subtracted." (2.2 ALMA)
- line free channels: _not stated_
- primary beam correction: _not stated_
- array combination: _not stated_
- smoothing: _not stated_
- final beam: 1.77''x1.16'' and 1.43''x1.03''  
  > "for the image at 241.561 GHz, the angular resolution was $1.43'' \times 1.03''$, with a P.A. of -5.5$^\circ$." (2.2 ALMA)
- final rms: _not stated_

### Inherited from earlier work

- HIFI survey observing strategy and deconvolution procedure  
  > "see (cite: bergin10) for more information on the observation strategy and deconvolution procedure." (2.1 HIFI) [from (cite: bergin10)]
- Absorption line profile equation  
  > "The line profiles are fit to the following equation (following (cite: melnick10)):" (3.5 Plateau) [from (cite: melnick10)]

### Not stated but needed to reproduce (our reading)

- Line-free channel ranges for continuum subtraction
- CASA version
- Clean masks, threshold and iterations
- Velocity ranges used for moment maps beyond quoted
- Far-IR continuum model (Crockett et al. 2013a in prep.)
- Full-band model of blends (Crockett et al. 2013b in prep.)

## Analysis recipe

1. **Fit Gaussian components to HIFI lines**: Up to four Gaussians per transition with CLASS; some positions and widths fixed to Table 1  
  > "Each transition was fit with up to four Gaussian components using CLASS, depending on which of the spatial components were detected." (3.1 Gaussian component fitting)
   - software: CLASS
   - fitting: _not stated_
   - validation: _not stated_
2. **Image HDO with ALMA to locate emission**: Extract and CLEAN two HDO lines; integrate over ~2.5 km/s channels; compare flux to IRAM 30m  
  > "Figure 6 shows images of these two transitions, integrated over $\sim 2.5$ km s$^{-1}$ velocity widths." (3.3.1 HDO and HD18O)
   - software: CASA
   - fitting: _not stated_
   - validation: 80-90% of flux recovered versus IRAM 30m after smoothing to 10.5''  
  > "found that 80–90% of the flux of these two transitions is recovered by ALMA." (3.3.1 HDO and HD18O)
3. **Derive column densities per component**: RADEX non-LTE models, population summation, LTE rotation diagram for D2O, absorption grid models  
  > "We have used two different approaches to derive the column densities of H$_2$O and HDO" (3.2 Strategy)
   - software: RADEX
   - parameter: Hot Core 2'' clump: Tkin=200 K, n(H2)=1e8 cm-3, enhanced continuum  
  > "Both models have $T_\textnormal{kin} = 200$ K and $n$(H$_2$) = $10^8$ cm$^{-3}$, and the enhanced continuum field from Figure 5." (3.3.2 H218O and H217O)
   - assumption: ortho:para H2O = 3; 16O/18O=250; 18O/17O=3.6; 10% calibration uncertainty  
  > "We assume a 10% calibration uncertainty in all measured line fluxes." (2.1 HIFI)
   - fitting: Compact Ridge: reduced chi-squared over Tkin, n(H2), N  
  > "There are three free parameters in the modeling: the kinetic temperature, the H$_2$ density, and the HDO or H$_2$O column density." (3.4 Compact ridge)
   - validation: _not stated_

## Software

- **CASA** : Extract and CLEAN HDO images from ALMA SV data  
  > "deconvolved using the Common Astronomy Software Applications (CASA) package[^4] with the CLEAN algorithm." (2.2 ALMA)
- **HIPE** 5.0: HIFI data processing and deconvolution  
  > "All data presented here were processed with HIPE (cite: ott10) version 5.0" (2.1 HIFI)
- **CLASS** : Gaussian fitting of HIFI lines  
  > "Each transition was fit with up to four Gaussian components using CLASS" (3.1 Gaussian component fitting)
- **XCLASS** : Line identification with CDMS and JPL catalogs  
  > "Line identifications for both water and other species were made using the XCLASS program[^2]" (2.1 HIFI)
- **RADEX** : Non-LTE radiative transfer models and correction factors  
  > "calculated from 1-D large velocity gradient calculations using the publicly available RADEX code (cite: vandertak07)." (3.2 Strategy)

## Numeric results

| quantity | value | uncertainty | units | step | quote |
|---|---|---|---|---|---|
| H2O abundance in 2'' Hot Core clump | 6.5e-4 | +7.3/-4.8 e-4 | relative to H2 | 3 | $6.5_{-4.8}^{+7.3} \times 10^{-4}$ |
| [HDO]/[H2O] 2'' Hot Core clump | 3.0e-3 | +3.1/-1.7 e-3 | dimensionless | 3 | $3.0_{-1.7}^{+3.1} \times 10^{-3}$ |
| N(HDO) 2'' Hot Core clump | 6.0e17 | ±3.6e17 | cm-2 | 3 | This leads to an HDO column density of $(6.0 \pm 3.6) \times 10^{17}$ cm$^{-2}$. |
| [HDO]/[H2O] Compact Ridge | 3.8e-3 | +3.6/-2.5 e-3 | dimensionless | 3 | $3.8_{-2.5}^{+3.6} \times 10^{-3}$ |
| [HDO]/[H2O] Plateau emission | 1.4e-3 | ±0.8e-3 | dimensionless | 3 | $1.4_{-0.8}^{+0.8} \times 10^{-3}$ |
| [HDO]/[H2O] absorbing gas | 2.2e-4 | ±1.3e-4 | dimensionless | 3 | $2.2_{-1.3}^{+1.3} \times 10^{-4}$ |
| [D2O]/[HDO] in 2'' clump | 0.0016 | ±0.0013 | dimensionless | 3 | \[D$_2$O\]/\[HDO\] = $0.0016 \pm 0.0013$ |

## Qualitative findings

- The high-excitation water clump lies about 1'' south of the dust continuum peak, near but not coincident with the continuum sources.  
  > "is located about $1''$ south of the dust continuum peak" (3.3.1 HDO and HD18O)

## Claim tuples

- H: Is there a compact Hot Core component with very high water abundance and HDO fractionation? | E: Radiative transfer modeling of HIFI H2(18)O, HD18O lines plus ALMA HDO maps | R: 2'' clump with chi(H2O)=6.5e-4 and HDO/H2O=0.003 | F: Water is recently evaporated ice mantle material in a small clump south of the continuum peak | **supported**
- H: Does the outflow have different deuteration from compact components? | E: Column densities of emission and absorption components | R: Outflow HDO/H2O lower, absorption component lowest | F: Gas-phase shock chemistry may modify the ratio | **partially**

## Reasoning

- Why this data: _not stated_
- Why this method: _not stated_
- Alternative: Observed continuum with higher density (1e9 cm-3) fits HDO equally well as enhanced continuum  
  > "If the observed continuum is used instead, an equally good fit can be obtained with a higher H$_2$ density ($10^9$ cm$^{-3}$)" (3.3.1 HDO and HD18O)
- How they decided it was enough: _not stated_
- Limitation (authors): ALMA data lack zero-spacing; HDO collision rates only up to 450 K so highest HDO lines cannot be modeled; vibrational pumping excluded  
  > "The ALMA observation was performed without zero-spacing information." (3.3.1 HDO and HD18O); "At the present time, therefore, we cannot model the highest-energy transitions of HDO detected by HIFI." (3.2 Strategy)
- Caveat (inferred, ours): Large uncertainties from 16O/18O ratio and assumed source sizes
- Caveat (inferred, ours): Relies on unpublished continuum model and full-band blend model
- Caveat (inferred, ours): Single-pointing, single-epoch ALMA SV data with low resolution

## Reproducibility

- Data public (paper): ALMA SV measurement set public  
  > "The full calibrated measurement set is publicly available at https://almascience.nrao.edu/alma-data/science-verification." (2.2 ALMA)
- Products in archive: _not stated_
- Missing: Herschel HEXOS spectra processing details and unpublished continuum/full-band models
- Missing: CASA version and clean parameters
- Missing: Velocity-channel details for maps
- Data volume (inferred): Tens of GB for ALMA SV Orion KL Band 6 measurement set; plus HIFI spectra
- Score (inferred): 3/5, ALMA part is small and public, but the main results rely on HIFI data and unpublished models.
- Rediscovery candidate: no, Main numeric results derive from Herschel data and unpublished inputs; ALMA is only supporting.

## Links

- Method: (cite: vandertak07) (RADEX code)
- Method: (cite: goldsmith99) (column density equation and rotation diagram)
- Companion: (cite: bergin10) (HEXOS Orion KL HIFI survey)
- Companion: (cite: melnick10) (previous H2O analysis of same dataset)
- Related: HEXOS
- Related: ALMA Science Verification Orion KL

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
 "numeric_results": 7,
 "numeric_problems": 0,
 "fill": {
  "facts": 71,
  "stated": 42,
  "rate": 0.592
 },
 "evidence_ok": true
}
```
