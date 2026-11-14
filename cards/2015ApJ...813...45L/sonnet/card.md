# Radio Jet Feedback and Star Formation in Heavily Obscured, Hyperluminous Quasars at Redshifts ∼ 0.5-3. I. ALMA Observations

`2015ApJ...813...45L` | The Astrophysical Journal 2015 | first author: Lonsdale, Carol J. | arXiv: 1509.00342 | DOI: 10.1088/0004-637X/813/1/45

Card schema 1.0 | model claude-sonnet-5-5 | depth full | type observational_alma_primary

## Science

- Fields: agn_and_quasars, high_z_galaxies
- Question: How much cool dust emission / star formation accompanies highly obscured, radio-powerful WISE-selected quasars at z~0.5-3, as measured with ALMA 870 um snapshot photometry?  
  > "obtained to constrain cool dust emission from starbursts concurrent with highly obscured radiative-mode black hole (BH) accretion in massive galaxies which possess a small radio jet." (abstract)
- Target **49 WISE-NVSS radio-powerful obscured quasars (southern subsample of 156)**: coordinates -40<dec<+1 deg; RA 3h-8h30m and 13h-21h  
  > "The declination range for the ALMA subsample was chosen to allow access to many northern facilities as well as ALMA: $-40^{\circ}<{\delta}<$+1$^{\circ}$." (3.1 FIR and Submillimeter Observations); z/distance 0.47<z<2.85 (spectroscopic for 45; z=2 assumed otherwise)  
  > "The declination range for the ALMA subsample was chosen to allow access to many northern facilities as well as ALMA: $-40^{\circ}<{\delta}<$+1$^{\circ}$." (3.1 FIR and Submillimeter Observations); distance from optical/NIR spectroscopy (SOAR, Palomar, Magellan, VLT)  
  > "The declination range for the ALMA subsample was chosen to allow access to many northern facilities as well as ALMA: $-40^{\circ}<{\delta}<$+1$^{\circ}$." (3.1 FIR and Submillimeter Observations)

## Data provenance

- ALMA projects: 2011.0.00397.S
- bands: Band 7 (870 um, 345 GHz)  
  > "The central frequency was set to 345 GHz (870 $\mu$m), with an 8 GHz bandwidth split into two sidebands." (3.1 FIR and Submillimeter Observations)
- frequencies and spectral setup: TDM, 256 channels per sideband, 14 km/s resolution  
  > "The objects were observed with the correlator in Time Division Mode, which results in 256 channels per sideband with a spectral resolution of 14 km s$^{-1}$." (3.1 FIR and Submillimeter Observations)
- continuum bandwidth: _not stated_
- arrays: _not stated_
- configurations: 'compact' Early Science configuration; 15, 19, 23 antennas  
  > "Fifteen antennas were used in the “compact” Early Science configuration for the November 2011 observations, 19 for the May 2012 observations and 23 for the August observations." (3.1 FIR and Submillimeter Observations)
- baselines: _not stated_
- angular resolution: 1.2", 0.5", 1.2" for the three epochs  
  > "The resulting beamsizes are 1$\ensuremath{''}$2, 0$\ensuremath{''}$5 and 1$\ensuremath{''}$2, respectively." (3.1 FIR and Submillimeter Observations)
- max recoverable scale: _not stated_
- sensitivity: rms 0.3-0.6 mJy  
  > "Time on source was 1.5 min per object, resulting in an $rms$ noise of 0.3–0.6 mJy" (3.1 FIR and Submillimeter Observations)
- time on source: 1.5 min per object  
  > "Time on source was 1.5 min per object" (3.1 FIR and Submillimeter Observations)
- observing dates: 2011 Nov 16; 2012 May 25; 2012 Aug 29  
  > "Twenty-three sources were observed with ALMA in two Band 7 scheduling blocks on 2011 November 16. An additional 14 were observed on 2012 May 25 and the final 12 on 2012 August 29." (3.1 FIR and Submillimeter Observations)
- pi or archival as stated: _not stated_
- Other facility **WISE**: 3.4-22 um photometry for selection and SEDs  
  > "we cross-matched the NVSS catalog, which covers the sky north of ${\delta}=-40^{\circ}$, with point sources from the WISE Allsky Catalog." (2 Sample Selection)
- Other facility **Herschel PACS/SPIRE**: FIR photometry for two ALMA sources  
  > "PACS observations are available for two sources, W1500-0649 and W2059-3541, and SPIRE observations for one, W2059-3541." (3.1 FIR and Submillimeter Observations)
- Other facility **CSO SHARC-II**: 350 um upper limits  
  > "Two additional sources have upper limits from the CSO at 350$\mu$m, W1343-1136 and W1400-2919." (3.1 FIR and Submillimeter Observations)
- Other facility **SOAR/Palomar/Magellan/VLT**: redshifts and R-band photometry  
  > "Redshifts for 45 of the 49 ALMA sources and $R$-band photometry for 26 were obtained" (3.2 Optical and Near-IR Photometry and Spectroscopy)
- External data: ISM mass calibration from 870 um flux (Scoville eq. 12)  
  > "derive the following relation for a flux density measured at observed frequency $\nu_{\rm obs}$" (5.1 Interstellar Medium Mass) [from (cite: scoville14)]
- External data: SED templates (Arp 220, M82, Mrk 231, QSO2 torus)  
  > "The source templates in all five figures are from (cite: polletta07)" (4.2 Colors and Spectral Energy Distributions) [from (cite: polletta07)]
- External data: Stellar population models  
  > "we use either a 100 or 600 Myr stellar population from (cite: maraston05)" (5.2.2 Three-Component SED Fits) [from (cite: maraston05)]

## Processing

### Calibration

- pipeline or manual: _not stated_
- casa version: _not stated_
- pipeline version: _not stated_
- archive products used as is: _not stated_
- flux calibrator: Callisto (Nov), Titan/Neptune (May), Titan (Aug)  
  > "For the November observations, Callisto was used for flux calibration. Titan was used for 7 sources in May and Neptune for the other 7 sources in May." (3.1 FIR and Submillimeter Observations)
- flux scale uncertainty: _not stated_
- self calibration: _not stated_

### Imaging

- task: flux densities measured with imfit in CASA  
  > "Flux densities were measured using imfit in CASA, and are reported in Table [1](#tbl-flux)." (3.1 FIR and Submillimeter Observations)
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

- CSO SHARC-II observing and reduction follow earlier work  
  > "Our observing and data reduction process follows that described by (cite: wu12)." (3.1 FIR and Submillimeter Observations) [from (cite: wu12)]
- Multi-component SED fitting methodology  
  > "The methodology follows (cite: sajina12) but is simplified from their four dust components to only two" (5.2.2 Three-Component SED Fits) [from (cite: sajina12)]

### Not stated but needed to reproduce (our reading)

- CASA version and calibration/imaging procedure (pipeline vs manual, weighting, cleaning)
- Region used for imfit and how upper limits were set (3 sigma assumed?)
- Rest-frame Gamma_RJ/Gamma_0 values and temperature-scaled constant for 30 K and 90 K ISM masses
- Fitting code and parameter priors for the AGN+BB+stellar fits; photometry weighting
- Redshift-tied details of k-correction templates

## Analysis recipe

1. **Measure 870 um flux densities**: imfit in CASA on ALMA images; 26 detections at >=3 sigma, none resolved  
  > "There are 26 ALMA detections at 3$\sigma$ or above. None of the sources are resolved." (4.1 Photometry and Redshifts)
   - software: CASA
   - fitting: _not stated_
   - validation: _not stated_
2. **Derive ISM masses**: Scoville et al. 2014 relation scaling 870 um flux, assuming all flux is thermal dust  
  > "We derive the ISM masses assuming that 100% of the 345 GHz flux is thermal dust emission." (5.1 Interstellar Medium Mass)
   - parameter: dust temperatures 30 K and 90 K  
  > "We derive ISM masses (Table [5](#tbl-mass), columns 13 & 14), for dust temperatures of 30 K and 90 K" (5.1 Interstellar Medium Mass)
   - assumption: uncertainty factor of 5; synchrotron contamination not corrected  
  > "We estimate the overall uncertainty to be a factor of 5" (5.1 Interstellar Medium Mass)
   - fitting: _not stated_
   - validation: compared with Scoville COSMOS IR-bright median  
  > "Their “IR Bright” sample has a median ISM mass of 11.91$\pm$0.77 ${\times} 10^{10} M_{\odot}$, about twice that of our sample." (5.1 Interstellar Medium Mass)
3. **Fit SEDs (AGN torus + modified blackbody + stellar) and derive SFRs**: parametric AGN MIR component plus greybody at fixed T=30,50,90,120 K, beta=1.5 (2 for 50 K); SFR from Kennicutt conversion  
  > "We have made four fits to each source, each with a different temperature for the BB component." (5.2.2 Three-Component SED Fits)
   - parameter: beta=1.5; 50K model beta=2  
  > "For $\beta$ we have selected a value of 1.5" (5.2.2 Three-Component SED Fits)
   - assumption: z=2 for sources without redshift  
  > "For the four sources without measured redshift we assume $z = 2$." (5.2.2 Three-Component SED Fits)
   - fitting: _not stated_
   - validation: free-Td fits for two Herschel sources set 90 K and 120 K  
  > "we have adopted the two dust temperature values which have fitted W1500-0649 and W2059-3541 successfully: 90 K (rounding up from 89 K) and 120 K" (5.2.2 Three-Component SED Fits)
4. **Radiative transfer model for W1500-0649**: tapered disk torus (Efstathiou & Rowan-Robinson) or Stalevski clumpy torus plus Efstathiou starburst models  
  > "We use a standard $\chi^2$ minimization technique to find the model parameters that best fit the data." (5.2.1 Radiative Transfer Model for WISE 1500-0649)
   - parameter: tau_uv 500, r2/r1=160, i=54 deg, t*=15 Myr  
  > "$\tau_{uv}^{eq}=500$, $r_2/r_1=160$, $i=54^o$ and $t_*=15$ Myr." (5.2.1 Radiative Transfer Model for WISE 1500-0649)
   - fitting: chi^2 minimization  
  > "We use a standard $\chi^2$ minimization technique to find the model parameters that best fit the data." (Radiative Transfer Model for WISE 1500-0649)
   - validation: two torus models agree on comparable AGN and starburst luminosity  
  > "We conclude that irrespective of the uncertain dust geometry, in W1500-0649 the AGN and the starburst emit comparable luminosity." (5.2.1 Radiative Transfer Model for WISE 1500-0649)
5. **BH masses and accretion rates**: from AGN luminosity assuming Eddington ratio 0.25, efficiency 0.1, covering factor unity  
  > "We assume an Eddington ratio, ${\lambda}_{\rm Edd}$, of 0.25, which is typical of $z{\sim}2$ quasars" (5.5 Black Hole Masses and Accretion Rates)
   - fitting: _not stated_
   - validation: compared with Kim et al. [OIII]-based masses  
  > "In columns 6-7 we also list the BH masses derived by (cite: kim13), based on the \[O III\]${\lambda} 5007\AA$ line luminosity." (Black Hole Masses and Accretion Rates)

## Software

- **CASA** : imfit flux measurement  
  > "Flux densities were measured using imfit in CASA" (3.1 FIR and Submillimeter Observations)
- **HIPE** 11.1.0: Herschel data processing  
  > "The data were processed with HIPE 11.1.0 (Ott 2010)." (3.1 FIR and Submillimeter Observations)

## Numeric results

| quantity | value | uncertainty | units | step | quote |
|---|---|---|---|---|---|
| ALMA 870 um detections | 26 of 49 | not stated | sources | 1 | Twenty-six sources are detected at 870 $\mu$m |
| Median ISM mass (30 K) of detected sources | 5.9e10 | factor of 5 | Msun | 2 | with a median for the 26 ALMA-detected sources of 5.9 ${\times}10^{10} M_{\odot}$ |
| SFR range from BB fits (detected) | 13.5-25700 | not stated | Msun/yr | 3 | the corresponding SFR range is 13.5–25700 $M_{\odot}$ ${\rm yr}^{-1}$ |
| log P(3 GHz) range | 24.74-27.33 | not stated | W/Hz | 0 | $\log$ $(P_{\rm 3 GHz}/W Hz^{-1})$ = 24.74–27.33 |
| W1500-0649 AGN luminosity (tapered disk) | 1.6e13 | not stated | Lsun | 4 | to give an AGN luminosity of $1.6 \times 10^{13} L_\odot$ |
| W1500-0649 starburst luminosity (tapered disk) | 1.8e13 | not stated | Lsun | 4 | The starburst luminosity is $1.8 \times 10^{13} L_\odot$ |

## Qualitative findings

- MIR-submm SEDs are similar to radio-blind Hot DOGs and redder than Spitzer DOGs, AGN-dominated in MIR  
  > "They are redder in the NIR-MIR than previous samples selected from $Spitzer$ surveys, including almost all of the $Spitzer$ DOGs." (7 Conclusions)

## Claim tuples

- H: Are obscured radio-powerful WISE quasars dominated by AGN with limited star formation? | E: ALMA 870 um photometry plus SED modelling | R: Large MIR/submm ratios; SFR from hundreds to thousands Msun/yr possible but AGN-only fits also possible | F: Sources are AGN-dominated, with star formation uncertain and dependent on dust temperature | **partially**
- H: Does the best-constrained source host a starburst? | E: Radiative transfer fit of W1500-0649 | R: comparable AGN and starburst luminosity, starburst age 10-15 Myr | F: Young compact starburst contributes about half of luminosity | **supported**

## Reasoning

- Why this data: _not stated_
- Why this method: _not stated_
- Alternative: Synchrotron contribution to 345 GHz flux judged <10% for most steep-spectrum sources; blazar explanation rejected  
  > "None of the flat or inverted spectrum sources has a plausible SED that can explain the WISE data as synchrotron emission from a blazar." (4.3 Synchrotron Contribution to the ALMA fluxes)
- How they decided it was enough: _not stated_
- Limitation (authors): Dust temperature unconstrained for most sources; L_BB and SFR uncertain by orders of magnitude  
  > "is uncertain by 2-3 dex without measurements at the FIR peak of the dust SED." (5.2 Spectral Energy Distribution Fits)
- Caveat (inferred, ours): Single ALMA point beyond 22 um makes SFR highly degenerate with dust temperature
- Caveat (inferred, ours): Snapshot data unresolved; AGN heating of cool dust not separable
- Caveat (inferred, ours): Eddington ratio and covering factor assumptions drive BH masses

## Reproducibility

- Data public (paper): ALMA project 2011.0.00397.S acknowledged  
  > "This paper makes use of the following ALMA data: ADS/JAO.ALMA#2011.0.00397.S." (Acknowledgments)
- Products in archive: _not stated_
- Missing: CASA version and imaging parameters
- Missing: SED fitting code and details
- Missing: Redshift spectra (deferred to later paper)
- Data volume (inferred): small (~tens of GB; 49 short snapshots)
- Score (inferred): 3/5, Public ALMA data and tabulated fluxes, but calibration/imaging and SED fitting details are sparse.
- Rediscovery candidate: no, Photometry is simple, but derived quantities rely on unspecified fitting code and external templates.

## Links

- Method: (cite: scoville14) (ISM mass from 870 um flux)
- Method: (cite: sajina12) (SED fitting methodology)
- Companion: (cite: jones15) (JCMT 850 um imaging of northern sample)
- Companion: (cite: kim13) (Magellan/FIRE spectroscopy of seven sources)
- Companion: (cite: silva15) (serendipitous 870 um sources in these ALMA fields)
- Related: WISE
- Related: NVSS
- Related: FIRST
- Related: Hot DOGs (EWB12)

## Checks

```json
{
 "quotes": 53,
 "quotes_ok": 53,
 "quote_pass_rate": 1.0,
 "quotes_too_long": 0,
 "unsupported_facts": 0,
 "project_codes": 1,
 "codes_not_in_text": [],
 "codes_not_in_obscore": [],
 "obscore_codes_not_in_card": [],
 "codes_printed_but_missing": [],
 "numeric_results": 6,
 "numeric_problems": 0,
 "fill": {
  "facts": 77,
  "stated": 43,
  "rate": 0.558
 },
 "evidence_ok": true
}
```
