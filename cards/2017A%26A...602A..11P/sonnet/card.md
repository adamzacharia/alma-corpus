# ALMA reveals starburst-like interstellar medium conditions in a compact star-forming galaxy at z   2 using [CI] and CO

`2017A&A...602A..11P` | Astronomy and Astrophysics 2017 | first author: Popping, Gergö | arXiv: 1703.05764 | DOI: 10.1051/0004-6361/201730391

Card schema 1.0 | model claude-sonnet-5-5 | depth full | type observational_alma_primary

## Science

- Fields: high_z_galaxies
- Question: What are the ISM conditions (density, UV field), gas mass, depletion time and kinematics of a compact star-forming galaxy at z=2.225, from [CI] and CO?  
  > "We study CO and [CI] kinematics, the density and UV radiation field of the ISM, and the global gas properties such as gas fraction and gas depletion time." (1 Introduction)
- Target **3D-HST GS30274**: coordinates RA 53.13108 deg, Dec -27.77311 deg  
  > "| 53.13108 | -27.77311 | 2.225 |" (Table 1); "A secure spectroscopic redshift between 2.0 and 2.5" (2.1 Target selection); z/distance z = 2.225  
  > "| 53.13108 | -27.77311 | 2.225 |" (Table 1); "A secure spectroscopic redshift between 2.0 and 2.5" (2.1 Target selection); distance from spectroscopic redshift (source not stated)  
  > "| 53.13108 | -27.77311 | 2.225 |" (Table 1); "A secure spectroscopic redshift between 2.0 and 2.5" (2.1 Target selection)

## Data provenance

- ALMA projects: 2015.1.00228.S
- bands: Band 3 and Band 4  
  > "Band 3 observations of 3D-HST GS30274 were performed on January 12 2016" (2.2 Observations)
- frequencies and spectral setup: Band 3: SPWs at 99.322 (CO 3-2, 3840 ch), 95.182, 107.199, 105.241 GHz; Band 4: 142.568 (CO 4-3), 152.610 ([CI]) GHz with 240 ch, plus 140.693 and 154.551 GHz continuum; all 1.875 GHz wide  
  > "One spectral window was centered at 142.568 GHz with a bandwidth of 1.875 GHz covering 240 channels, to target the CO J$=$4–3 emission line." (2.2 Observations)
- continuum bandwidth: _not stated_
- arrays: _not stated_
- configurations: C36-1 compact configuration  
  > "with a compact configuration (C36-1; shortest and longest baselines were 15.1 and 331 meters" (2.2 Observations)
- baselines: _not stated_
- angular resolution: Band 3 3.4x2.16 arcsec; Band 4 2.22x1.54 arcsec  
  > "resulted in a synthetic beam size of 2.22 $\times$ 1.54 arcsec$^2$ with a position angle of 76 degrees" (2.2 Observations)
- max recoverable scale: _not stated_
- sensitivity: Band 4 rms 0.014 mJy/beam continuum, 0.076 (CO 4-3) and 0.08 ([CI]) mJy/beam/(100 km/s); Band 3 0.012 continuum, 0.16 CO 3-2  
  > "The typical rms noise level is 0.014 mJy/beam for the continuum and 0.076 mJy/beam/(100 km s$^{-1}$) for the CO J$=$ 4–3 line" (2.2 Observations)
- time on source: 46 min Band 3; 89 min Band 4  
  > "The total integration time on 3D-HST GS30274 in band 4 was 89 minutes." (2.2 Observations)
- observing dates: 12 Jan 2016 (Band 3); 17 and 21 Jan 2016 (Band 4)  
  > "The band 4 observations of 3D-HST GS30274 were performed on January 17 2016 and January 21 2016" (2.2 Observations)
- pi or archival as stated: Own program (PI G. Popping)  
  > "project 2015.1.00228.S (PI: G. Popping)" (2.2 Observations)
- Line: CO J=3-2 (not stated)
- Line: CO J=4-3 (not stated)
- Line: [CI] 3P1-3P0 (1-0) (not stated)
- Other facility **Herschel PACS/SPIRE**: far-IR photometry for SED fit  
  > "A counterpart in the blind fields from *Herschel*/PACS (cite: Magnelli2013) and SPIRE (cite: Roseboom2010)" (2.1 Target selection)
- Other facility **3D-HST**: UV-to-8um photometry and selection catalogue  
  > "3D-HST catalogue (cite: Skelton2014) that includes photometry from the U-band to the *S*pitzer 8 $\mu$m band" (2.1 Target selection)
- External data: Optical-NIR photometry  
  > "(1) (cite: Skelton2014)" (Table 2) [from (cite: Skelton2014)]
- External data: Effective radius 2.5 kpc  
  > "This source has an effective radius of 2.5 $\pm$ 0.1 kpc (cite: vanderWel2014)." (2.1 Target selection) [from (cite: vanderWel2014)]
- External data: Hα velocity dispersion for comparison  
  > "The derived velocity dispersions of CO and [CI] are in agreement with the H$\alpha$ velocity dispersion for this source (cite: vanDokkum2015)." (4 Discussion) [from (cite: vanDokkum2015)]
- Simulation/model as data: PDR model grids (Kaufman) as in Alaghband2013; Meijerink PDR/XDR models  
  > "We overplotted the density and UV radiation field contours as presented in (cite: Alaghband2013), based on the (cite: Kaufman1999) and (cite: Kaufman2006) PDR models." (3.4 Comparing line ratios with PDR models)

## Processing

### Calibration

- pipeline or manual: Standard ALMA pipeline  
  > "The data were calibrated using the standard ALMA pipeline (`CASA` version 4.5.1)." (2.2 Observations)
- casa version: CASA 4.5.1  
  > "The data were calibrated using the standard ALMA pipeline (`CASA` version 4.5.1)." (2.2 Observations)
- pipeline version: _not stated_
- archive products used as is: _not stated_
- flux calibrator: _not stated_
- flux scale uncertainty: _not stated_
- self calibration: _not stated_

### Imaging

- task: CASA CLEAN  
  > "Images were produced using the `CLEAN` task in `CASA` (cite: McMullin2007), with a natural weighting." (2.2 Observations)
- deconvolver: _not stated_
- weighting robust: natural weighting  
  > "The imaging was done with the `CLEAN` task with natural weighting" (2.2 Observations)
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

- Carbon mass formula  
  > "We derive the atomic carbon mass following (cite: Weiss2005)" (3.5.1 Based on [CI]) [from (cite: Weiss2005)]
- Tex = 30 K assumed  
  > "We assume $T_{\rm ex} = 30$ K, the average excitation temperature found in (cite: Walter2011)." (3.5.1 Based on [CI]) [from (cite: Walter2011)]
- Gas-to-dust ratio calibration  
  > "We estimate $\delta_{\rm GDR}(Z)$ using the empirical calibration of (cite: Magdis2012a)." (3.5.3 Based on the dust mass) [from (cite: Magdis2012a)]
- Predicted velocity dispersion relation  
  > "Following (cite: vanDokkum2015) the predicted velocity dispersion of a galaxy is" (4 Discussion) [from (cite: vanDokkum2015)]

### Not stated but needed to reproduce (our reading)

- CLEAN threshold, masks, iterations, cell and image size
- Line-free channels and continuum subtraction method
- Channel width used for line spectra and flux extraction aperture/method
- Exact alpha_CO starburst value and gas-to-dust formula numerical values
- MAGPHYS setup/priors and handling of ALMA upper limit
- Flux calibrators and flux-scale uncertainty
- How line S/N and Gaussian fit errors were computed
- Cosmology adopted for luminosity distance

## Analysis recipe

1. **Image and detect lines and continuum**: CLEAN with natural weighting; moment-0 maps; spectra extracted and fit with single Gaussian  
  > "The spectra presented in Figure [5](#fig:spectra) can be well fitted with a single gaussian" (3.3 Kinematics)
   - software: CASA
   - fitting: single Gaussian  
  > "can be well fitted with a single gaussian with a dispersion of 328 $\pm$ 38" (3.3 Kinematics)
   - validation: _not stated_
2. **Line luminosities**: L' from Solomon & Vanden Bout relation  
  > "We calculate the CO and [CI] line luminosities using the following relation (cite: Solomon2005)" (3.1)
   - fitting: _not stated_
   - validation: _not stated_
3. **SED fit for LIR, M*, SFR, Mdust**: MAGPHYS fit to optical-NIR, Herschel and ALMA Band 4 photometry  
  > "This was obtained by fitting the ALMA band 4, the *Herschel*/ PACS (cite: Magnelli2013) and SPIRE continuum (cite: Roseboom2010), and optical and NIR data photometry (cite: Skelton2014) with the `MAGPHYS` (cite: daCunha2008) model" (3.2)
   - software: MAGPHYS
   - assumption: Chabrier IMF  
  > "Throughout this paper we assume a Chabrier initial mass function (cite: Chabrier2003)." (1 Introduction)
   - fitting: _not stated_
   - validation: AGN contribution checked against Kirkpatrick2015 templates (~20% extra IR)  
  > "suggests that an additional contribution of 20% to the total IR luminosity by an AGN can make up for the mismatch" (3.2)
4. **ISM density and UV field from line ratios**: Compare [CI]/CO(4-3) vs [CI]/FIR to PDR model contours; XDR check  
  > "We present the [CI] 1–0/ CO J$=$4-3 luminosity ratio of 3D-HST GS30274 as a function of its [CI] 1–0/ FIR luminosity ratio" (3.4)
   - fitting: _not stated_
   - validation: XDR code cannot reproduce ratios, supporting minor AGN role  
  > "This supports the finding that the AGN only plays a minor role in the emission from 3D-HST GS30274." (3.4)
5. **H2 mass from [CI], CO, dust**: [CI] mass via Weiss+05 then X[CI]; CO via assumed thermalised ratio and starburst alpha_CO; dust via gas-to-dust ratio  
  > "assuming a carbon abundance of $\rm{X}_{\rm [CI]} = M_{\rm [CI]}/(6\,M_{\rm H2}) = 3\times 10^{-5}$" (3.5.1)
   - parameter: Tex = 30 K  
  > "We assume $T_{\rm ex} = 30$ K" (3.5.1)
   - assumption: CO 3-2/1-0 flux ratio = 9 (thermalised)  
  > "We therefore assume that the flux intensity ratio between the CO J$=$3–2 and CO $J$= 1–0 line equals $3^2/1^2=9$." (3.5.2)
   - fitting: _not stated_
   - validation: Compare three tracers; Tex sensitivity <3%  
  > "this would result in a change in carbon mass (and resulting H$_2$ mass) of less than 3%." (3.5.1)
6. **Gas fraction, depletion time, alpha_CO, gas-to-dust**: M_H2/SFR, M_H2/(M_H2+M*), alpha_CO=M_H2/L'CO1-0, gas/dust with 1.36 He  
  > "The gas depletion time of 3D-HST GS30274 is $M_{\rm H2}/{\rm SFR}= 140 \pm 30\,\rm{Myr}$." (3.6)
   - fitting: _not stated_
   - validation: _not stated_
7. **Dynamical test of line widths**: Predicted sigma from M_dyn = M* + 1.36 MH2 and re  
  > "we can replace $M_*$ by $M_{\rm dyn} = M_* + 1.36 M_{\rm H2}$" (4 Discussion)
   - assumption: gas and stars dynamically coupled  
  > "Assuming that the gas and stars are dynamically coupled" (4 Discussion)
   - fitting: _not stated_
   - validation: Compared with observed CO sigma  
  > "The predicted velocity dispersions are similar to the observed velocity dispersion of the CO lines in 3D-HST GS30274" (4 Discussion)

## Software

- **CASA** 4.5.1: calibration and CLEAN imaging  
  > "The data were calibrated using the standard ALMA pipeline (`CASA` version 4.5.1)." (2.2 Observations)
- **MAGPHYS** : SED fitting for M*, SFR, Mdust, LIR  
  > "fitting the spectral energy distribution (SED) using `MAGPHYS` (cite: daCunha2008; daCunha2015)" (2.1 Target selection)

## Numeric results

| quantity | value | uncertainty | units | step | quote |
|---|---|---|---|---|---|
| CO(3-2) integrated flux | 0.77 | 0.06 | Jy km/s | 1 | CO (3–2)      / $0.77 \pm 0.06$ |
| CO(4-3) integrated flux | 1.08 | 0.04 | Jy km/s | 1 | CO (4–3)      / $1.08 \pm 0.04$ |
| [CI](1-0) integrated flux | 0.32 | 0.03 | Jy km/s | 1 | $[$CI$]$ (1–0)   / $0.32\pm 0.03$ |
| 660 um continuum | 0.085 | 0.014 | mJy | 1 | $0.085 \pm 0.014$ |
| FWHM CO(4-3) | 751 | 44 | km/s | 1 | This corresponds to a FWHM of 764 $\pm$ 88, 751 $\pm$ 44, and 675 $\pm$ 92 km s$^{-1}$, respectively. |
| LIR | 2.3e12 | 0.6e12 | Lsun | 3 | $L_{\rm IR} = 2.3\pm0.6\,\times10^{12}\,\rm{L}_\odot$ |
| ISM density | 6e4 | 0.5e4 | cm^-3 | 4 | a density of $(6 \pm 0.5)\times 10^4\,\rm{cm}^{-3}$ |
| UV radiation field | 2e4 | 2e4 | G0 | 4 | a UV radiation field of $(2 \pm 2) \times 10^4\,\rm{G}_0$ |
| M_H2 from [CI] | 3.0e10 | 0.3e10 | Msun | 5 | $M_{\rm H2}(\rm{[CI]}) = 3.0 \pm 0.3 \times 10^{10}\,\rm{M}_\odot$ |
| M_H2 from CO | 1.7e10 | 0.1e10 | Msun | 5 | CO-based H$_2$ mass of $1.7 \pm 0.1 \times 10^{10}\,\rm{M}_\odot$ |
| Depletion time ([CI]) | 140 | 30 | Myr | 6 | $M_{\rm H2}/{\rm SFR}= 140 \pm 30\,\rm{Myr}$ |
| alpha_CO | 1.4 | 0.15 | Msun/(K km/s pc^2) | 6 | $\alpha_{\rm CO} = \rm{M}_{\rm H2} / L'_{\rm CO 1-0} = 1.4 \pm 0.15 |
| Predicted sigma ([CI]-based Mdyn) | 340 | 35 | km/s | 7 | we find a predicted velocity dispersion for the gas of $340 \pm 35$ km s$^{-1}$ |

## Qualitative findings

- No outflow signature (broad second component) seen in CO/[CI]; galaxy unresolved  
  > "We do not find any signatures in the flux density profile for a CO or [CI] outflow" (3.3 Kinematics)

## Claim tuples

- H: Does the ISM of the cSFG resemble a starburst? | E: [CI]/CO/FIR ratios compared with PDR models | R: n~6e4 cm^-3, G0~2e4 | F: ISM conditions similar to local starbursts/ULIRGs | **supported**
- H: Is the gas depletion time short? | E: H2 mass from [CI], CO, dust | R: t_dep <=140 Myr, 80 and <30 Myr | F: Shorter than extended SFGs | **supported**
- H: Are line widths gravitational from a compact gas reservoir? | E: Compare observed sigma with predicted from Mdyn | R: predicted 316-340 vs observed ~290-330 km/s | F: Consistent with gravitational motions in compact reservoir | **supported**

## Reasoning

- Why this data: _not stated_
- Why this method: [CI] is a better H2 tracer in cosmic-ray/X-ray dominated environments  
  > "[CI] is a better tracer of the H$_2$ mass than CO." (1 Introduction)
- Alternative: Tex of ~200 K from PDR models rejected in favour of 30 K  
  > "We therefore stick to the assumed excitation temperature of $T_{\rm ex} = 30$ K" (3.5.1)
- How they decided it was enough: _not stated_
- Limitation (authors): Galaxy unresolved; outflows could be missed; needs higher resolution  
  > "Future high-resolution observations are needed to properly measure the size of the compact molecular gas reservoir" (4 Discussion)
- Caveat (inferred, ours): Tex and X[CI] assumed, driving H2 mass
- Caveat (inferred, ours): No [CI] 2-1 or CO 1-0 to constrain excitation
- Caveat (inferred, ours): AGN present may bias SED, PDR and alpha_CO inference
- Caveat (inferred, ours): Single source; unresolved, so size/kinematics are indirect

## Reproducibility

- Data public (paper): Project code given; public status not explicitly stated  
  > "This paper makes use of the following ALMA data: ADS/JAO.ALMA#2015.1.00228.S." (Acknowledgements)
- Products in archive: _not stated_
- Missing: CLEAN parameters and line extraction details
- Missing: MAGPHYS configuration
- Missing: alpha_CO starburst value and PDR grid access
- Data volume (inferred): ~10-30 GB raw for a few short low-resolution Band 3/4 execution blocks
- Score (inferred): 6/5, Simple data and analysis with equations given, but imaging, flux extraction and SED details are missing.
- Rediscovery candidate: yes, Archival-quality data with numeric line fluxes and derived quantities, simple analysis chain.

## Links

- Method: (cite: Weiss2005) (carbon mass formula and X[CI])
- Method: (cite: Solomon2005) (line luminosity relation)
- Method: (cite: daCunha2008) (MAGPHYS SED fitting)
- Companion: (cite: vanDokkum2015) (cSFG classification and Hα kinematics)
- Related: 3D-HST
- Related: GOODS-South

## Checks

```json
{
 "quotes": 73,
 "quotes_ok": 73,
 "quote_pass_rate": 1.0,
 "quotes_too_long": 0,
 "unsupported_facts": 0,
 "project_codes": 1,
 "codes_not_in_text": [],
 "codes_not_in_obscore": [],
 "obscore_codes_not_in_card": [],
 "codes_printed_but_missing": [],
 "numeric_results": 13,
 "numeric_problems": 0,
 "fill": {
  "facts": 83,
  "stated": 49,
  "rate": 0.59
 },
 "evidence_ok": true
}
```
