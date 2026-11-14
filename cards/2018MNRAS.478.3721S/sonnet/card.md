# Deep ALMA photometry of distant X-ray AGN: improvements in star formation rate constraints, and AGN identification

`2018MNRAS.478.3721S` | Monthly Notices of the Royal Astronomical Society 2018 | first author: Stanley, F. | arXiv: 1712.02363 | DOI: 10.1093/mnras/sty1044

Card schema 1.0 | model claude-sonnet-5-5 | depth full | type observational_alma_primary

## Science

- Fields: high_z_galaxies, agn_and_quasars
- Question: How much do deep ALMA 870um photometry improve SFR constraints and MIR AGN identification for Herschel-faint X-ray AGN at 1<z<4.7, and can the F870/F24-redshift plane identify AGN?  
  > "We demonstrate that the F$_{870\mathrel{\rm \mu m}}$/F$_{24\mathrel{\rm \mu m}}$–redshift plane can successfully split between AGN and star formation dominated sources, and can be used as an AGN identification method." (abstract)
- Target **109 X-ray AGN in CDF-S and C-COSMOS (1<z<4.7)**: coordinates _not stated_; z/distance 1<z<4.7 (updated redshifts from Hsu14 and Marchesi16)  
  > "This results in 109 X-ray AGN with ALMA 870$\mathrel{\rm \mu m}$ observations, 101 originally targeted, and 8 serendipitous X-ray AGN." (2.1 Sample selection); distance from Hsu et al. 2014 (CDF-S) and Marchesi et al. 2016 (C-COSMOS) redshift catalogues  
  > "This results in 109 X-ray AGN with ALMA 870$\mathrel{\rm \mu m}$ observations, 101 originally targeted, and 8 serendipitous X-ray AGN." (2.1 Sample selection)

## Data provenance

- ALMA projects: 2012.1.00869.S, 2013.1.00884.S
- bands: Band 7 (870 um)  
  > "observed with ALMA in Band-7 (i.e. 870$\mathrel{\rm \mu m}$)" (1 Introduction)
- frequencies and spectral setup: _not stated_
- continuum bandwidth: 7.5 GHz centred at 351 GHz  
  > "with a bandwidth of 7.5GHz centred at 351GHz" (2.2 ALMA 870um observations)
- arrays: 12m and 7m arrays; Cycle 1: 32 12m + 9 7m antennas; Cycle 2: 34 12m + 9 7m antennas  
  > "Cycle 1 observations were carried out using 32 antennas in the 12m array and 9 antennas in the 7m array" (2.2 ALMA 870um observations)
- configurations: _not stated_
- baselines: _not stated_
- angular resolution: ~0.8" tapered beam  
  > "to obtain a synthesised beam of $\sim$0.8$"$ for all images" (2.2 ALMA 870um observations)
- max recoverable scale: _not stated_
- sensitivity: 0.1–0.8 mJy/beam in CDF-S; 0.08–0.23 mJy/beam in C-COSMOS  
  > "with noise levels of 0.1–0.8 mJy/beam in CDF-S, and 0.08–0.23 mJy/beam in C-COSMOS" (2.2 ALMA 870um observations)
- time on source: Cycle 1: 2.5–13 min; Cycle 2: 1–6 min per source  
  > "with integration times ranging between 2.5–13min" (2.2 ALMA 870um observations)
- observing dates: _not stated_
- pi or archival as stated: Cycle 1 PI Mullaney; Cycle 2 PI Alexander (authors' own programmes)  
  > "Cycle 1 (2012.1.00869.S; PI: J. R. Mullaney) and Cycle 2 (2013.1.00884.S; PI:D. M. Alexander)" (2.2 ALMA 870um observations)
- Other facility **Spitzer (IRAC, IRS, MIPS)**: 3.6–24 um photometry  
  > "*Spitzer*-IRAC at 3.6–8$\mathrel{\rm \mu m}$; *Spitzer*-IRS at 16$\mathrel{\rm \mu m}$; *Spitzer*-MIPS at 24$\mathrel{\rm \mu m}$" (2.3 MIR and FIR photometry)
- Other facility **Herschel (PACS, SPIRE)**: 70–500 um deblended photometry  
  > "*Herschel*-PACS at 70, 100, 160$\mathrel{\rm \mu m}$; and *Herschel*-SPIRE at 250, 350, 500$\mathrel{\rm \mu m}$" (2.3 MIR and FIR photometry)
- Other facility **Chandra CDF-S and C-COSMOS**: X-ray AGN selection catalogues  
  > "The Cycle 1 sample was selected from the 4Ms *Chandra* Deep Field South (CDF-S) catalogue of (cite: Xue11)" (2.1 Sample selection)
- External data: Spitzer and Herschel photometry assigned to the X-ray AGN  
  > "We make use of the *Spitzer* and *Herschel* photometry assigned to the X-ray AGN in (cite: Stanley15) for our analysis" (2.1 Sample selection) [from (cite: Stanley15)]
- External data: ALMA 870um photometry and redshifts of 41 WISE AGN-dominated comparison sources  
  > "(cite: Lonsdale15) present ALMA observations and measurements of 870$\mathrel{\rm \mu m}$ of 49 such sources" (2.4 Comparison samples) [from (cite: Lonsdale15)]
- External data: ALESS SMG sample ALMA photometry (113 sources used)  
  > "The chosen sample of SMGs is taken from the ALMA-LESS survey (A-LESS; (cite: Hodge13); (cite: Karim13))" (2.4 Comparison samples) [from (cite: Hodge13); (cite: Karim13); redshifts Danielson17; Simpson14; MIR/FIR Swinbank14]
- External data: ALMA 870um photometric catalogues of the sample  
  > "In Scholtz et al. (2018) we present the ALMA 870$\mathrel{\rm \mu m}$ photometric catalogues for the full sample of targeted and serendipitous X-ray AGN" (2.2 ALMA 870um observations) [from (cite: Scholtz18)]
- Simulation/model as data: Empirical IR templates: five SF templates (Mullaney11, extended by DelMoro13) + Arp220 (Silva98) and mean AGN template (Mullaney11); Dale02, Mor12, Symeonidis16 templates for comparison  
  > "This includes the five star-forming galaxy templates originally defined in (cite: Mullaney11), (later extended in wavelength by (cite: DelMoro13)), with the addition of Arp220 from (cite: Silva98)" (3 IR SED fitting & decomposition)

## Processing

### Calibration

- pipeline or manual: ALMA data reduction pipeline, with repeat and extra flagging when needed after visual inspection  
  > "The raw data was calibrated using the ALMA data reduction pipeline." (2.2 ALMA 870um observations)
- casa version: CASA 4.4.0  
  > "version 4.4.0" (2.2 ALMA 870um observations)
- pipeline version: _not stated_
- archive products used as is: _not stated_
- flux calibrator: _not stated_
- flux scale uncertainty: _not stated_
- self calibration: _not stated_

### Imaging

- task: CASA clean  
  > "and the clean routine in casa" (2.2 ALMA 870um observations)
- deconvolver: _not stated_
- weighting robust: natural weighting  
  > "we applied natural weighting and appropriate Gaussian tapering in the *uv*–plane" (2.2 ALMA 870um observations)
- uv taper: Gaussian taper to ~0.8" beam (values not given)  
  > "appropriate Gaussian tapering in the *uv*–plane to obtain a synthesised beam of $\sim$0.8$"$ for all images" (2.2 ALMA 870um observations)
- cell size: _not stated_
- image size: _not stated_
- masking: cleaned down to 3 sigma from dirty images; sources identified at SNR>=5  
  > "We created “dirty" images, which were subsequently cleaned down to 3$\sigma$. We then identified the sources with SNR$\geq$5." (2.2 ALMA 870um observations)
- multiscale scales: _not stated_
- continuum subtraction: _not stated_
- line free channels: _not stated_
- primary beam correction: _not stated_
- array combination: _not stated_
- smoothing: _not stated_
- final beam: (0.8"–0.9")x0.7"  
  > "The resulting synthesised beams are of the size of $(0.8"-0.9")\times0.7"$" (2.2 ALMA 870um observations)
- final rms: 0.1–0.8 mJy/beam (CDF-S), 0.08–0.23 mJy/beam (C-COSMOS)  
  > "with noise levels of 0.1–0.8 mJy/beam in CDF-S, and 0.08–0.23 mJy/beam in C-COSMOS" (2.2 ALMA 870um observations)

### Inherited from earlier work

- ALMA data processing and imaging methods  
  > "The data were processed and imaged following the methods of (cite: Hodge13) and (cite: Simpson15); see full details in (cite: Scholtz18)." (2.2 ALMA 870um observations) [from (cite: Hodge13); (cite: Simpson15); (cite: Scholtz18)]
- SED fitting and decomposition method  
  > "We performed fitting and decomposition of the IR SED by following and extending the methods of (cite: Stanley15)." (3 IR SED fitting & decomposition) [from (cite: Stanley15)]
- Sample selection details  
  > "The details of the sample selection for the two programs are given in (cite: Scholtz18)" (2 Sample & Observations) [from (cite: Scholtz18)]

### Not stated but needed to reproduce (our reading)

- Exact tclean/clean parameters (taper values, cell size, image size, masks, niter, threshold per field)
- Flux calibrators and flux-scale uncertainty
- Template normalisation/fit routine details and how photometric errors and upper limits are implemented
- SED fit code not named or released
- Exact photometry values (ALMA catalogue in Scholtz18) needed to reproduce fits
- Treatment of ALMA flux deboosting or flux-density extraction method

## Analysis recipe

1. **Reduce and image ALMA 870um data**: Pipeline calibration, dirty images cleaned to 3 sigma, natural weighting plus taper to ~0.8", sources at SNR>=5; upper limits 3xRMS  
  > "If a source remains undetected we take 3$\times$RMS as the flux density upper limit." (2.2 ALMA 870um observations)
   - software: CASA
   - parameter: beam ~0.8"; SNR>=5 detection  
  > "We then identified the sources with SNR$\geq$5." (2.2 ALMA 870um observations)
   - fitting: _not stated_
   - validation: Visual inspection of pipeline results  
  > "The results were visually inspected, and when deemed necessary, the pipeline calibration process was repeated with additional data flagging." (2.2 ALMA 870um observations)
2. **Fit IR SEDs and decompose SF and AGN**: Fit 8–870um photometry with six SF templates with and without AGN template, forcing fits below upper limits; choose best fit by BIC (AGN required if dBIC>2); five detection-dependent cases  
  > "The SED fit with the minimum BIC value is defined as the best fit." (3 IR SED fitting & decomposition); "the SED with the AGN component has to have a smaller BIC to that of the SED with no AGN component with a difference of $\Delta$BIC$>$2" (3 IR SED fitting & decomposition)
   - parameter: L_IR integrated over 8–1000 um; AGN component counted as significant if >=20% of IR luminosity  
  > "the fit requires an AGN component with a significant contribution (at least 20%)" (3 IR SED fitting & decomposition)
   - assumption: Cosmology H0=70, OmegaM=0.3, OmegaL=0.7; Chabrier IMF  
  > "we assume $\rm H_0 = 70 km \, s^{-1} \, Mpc^{-1}$, $\rm \Omega_M = 0.3$, $\rm \Omega_\Lambda = 0.7$, and a (cite: Chabrier03) initial mass function (IMF)" (1 Introduction)
   - fitting: Template fitting with BIC model selection; uncertainties combine formal fit error and range of fits with dBIC<2  
  > "The uncertainties on the chosen $\mathrel{\rm L_{IR,SF}}$, and $\mathrel{\rm L_{IR,AGN}}$ values are the combination of the formal error on the fit and the range of" (3 IR SED fitting & decomposition)
   - validation: Comparison of AGN 6um luminosity with L2-8keV; test of alternative AGN templates; consistency with Herschel for 2 sources  
  > "The agreement of the ALMA photometry to the *Herschel* constraints provides extra confidence in our SED fitting approach and choice of templates" (4 Improvements on LIR,SF constraints)
3. **Quantify improvement from ALMA**: Repeat SED fitting with 8–500um vs 8–870um photometry and compare LIR,SF  
  > "we have performed the same SED fitting analysis on the sample with and without the ALMA photometry" (4 Improvements on LIR,SF constraints)
   - fitting: _not stated_
   - validation: _not stated_
4. **Define and test F870/F24-redshift AGN selection**: Build composite SEDs with 50% AGN contribution, redshift 1–5 in steps of 0.2, take median F870/F24 track; apply to X-ray AGN, WISE AGN and ALESS SMG samples, compare to Donley12 IRAC selection  
  > "This SED is then shifted with redshift steps of 0.2 from redshifts 1 to 5, and at each step we calculate the observed frame F$_{870\mathrel{\rm \mu m}}$/F$_{24\mathrel{\rm \mu m}}$ ratio." (5.1 Defining the plane)
   - parameter: log10(F870/F24) = -1.19 + 3.623 log10(1+z)  
  > "\log_{10}(\frac{F_{870\mathrel{\rm \mu m}}}{F_{24\mathrel{\rm \mu m}}}) \, = \, -1.19 + 3.623\times \log_{10}(1+z)" (5.1 Defining the plane)
   - fitting: _not stated_
   - validation: Comparison against AGN-dominated and SMG samples and IRAC colour selection  
  > "The IRAC colour criteria select 19 out of the 22 sources selected by the F$_{870\mathrel{\rm \mu m}}$/F$_{24\mathrel{\rm \mu m}}$ limit." (5.2 AGN identification)

## Software

- **CASA** 4.4.0: ALMA calibration pipeline and clean imaging  
  > "We used the common astronomy software application (casa; version 4.4.0; McMullin et al 2007), and the clean routine in casa." (2.2 ALMA 870um observations)

## Numeric results

| quantity | value | uncertainty | units | step | quote |
|---|---|---|---|---|---|
| ALMA 870um detection fraction | 40/109 (36.7%) | not stated | dimensionless | 1 | In total we find that 40/109 (36.7%) of our sources are detected by ALMA. |
| Fraction with measured SFR before ALMA | 2% | not stated | dimensionless | 3 | (from 2% to 37% of the sample) |
| Fraction with measured SFR with ALMA | 37% (40/109) | not stated | dimensionless | 3 | we now have $\mathrel{\rm L_{IR,SF}}$ measurements for 40/109 ($\simeq$37%) of the sources |
| Sources with MIR AGN component identified | 54/109 (~50%) | not stated | dimensionless | 2 | we can now confidently identify a MIR AGN component in 54/109 ($\sim$50%) of the ALMA observed sample |
| Fraction with LIR,SF changed by more than factor 2 | 67% | not stated | dimensionless | 3 | more than half of our sample (67%) have $\mathrel{\rm L_{IR,SF}}$ constraints that have changed by more than a factor of 2 |
| X-ray AGN selected by F870/F24 limit (of 50 with 4 IRAC bands) | 22/50 | not stated | dimensionless | 4 | the F$_{870\mathrel{\rm \mu m}}$/F$_{24\mathrel{\rm \mu m}}$ limit selects 22/50 sources as AGN candidates |
| SMGs selected as strong AGN by F870/F24 limit | 8/81 | not stated | dimensionless | 4 | selection limit selects 8/81 sources as having a strong AGN component |

## Qualitative findings

- The F870/F24 selection and IRAC colour selection are comparable for strong AGN but both miss AGN contributing <50% of IR luminosity  
  > "both methods are comparable in selecting source with a strong AGN component, but both will miss the majority of sources that have AGN components contributing $<$50% to the total IR luminosity." (5.2 AGN identification)

## Claim tuples

- H: Deep ALMA 870um photometry greatly improves SFR constraints for Herschel-faint X-ray AGN | E: SED fitting with and without ALMA photometry | R: SFR measurements for 37% vs 2%; upper limits lowered up to a factor of 10 | F: ALMA enables constraining SFR distributions of distant X-ray AGN | **supported**
- H: ALMA photometry allows identification of MIR AGN components in SEDs | E: SED decomposition with BIC | R: AGN component in 54/109 vs 1 before | F: Large increase in MIR AGN identification | **supported**
- H: F870/F24-redshift plane can identify AGN-dominated/strong AGN sources | E: Test track on X-ray AGN, WISE AGN and SMG samples | R: All 41 AGN-dominated selected; 8/81 SMGs selected, 7 with AGN signatures | F: Method identifies sources with >=50% AGN IR contribution | **supported**

## Reasoning

- Why this data: _not stated_
- Why this method: Deep ALMA needed to probe typical galaxies beyond Herschel's sensitivity  
  > "in order to directly constrain the SFRs of the typical population of galaxies and AGN at redshifts of $z \gtrsim 1$, we need even deeper observations in the FIR/sub-mm." (1 Introduction)
- Alternative: Other AGN templates (Symeonidis16, Mor12) tested; Symeonidis16 inconsistent with AGN-dominated colours  
  > "the (cite: Symeonidis16) AGN template is the most incompatible to the F$_{870\mathrel{\rm \mu m}}$/F$_{24\mathrel{\rm \mu m}}$ ratios of the AGN dominated sample." (5.1 Defining the plane)
- How they decided it was enough: _not stated_
- Limitation (authors): 14 CDF-S targets observed at too-high resolution, requiring heavy tapering and giving higher noise  
  > "for these observations the images had to be heavily tapered to a resolution of 0.8$"$, resulting in increased noise levels" (2.2 ALMA 870um observations)
- Caveat (inferred, ours): Single mean AGN template dominates results; template-dependence only partly tested
- Caveat (inferred, ours): F870/F24 selection calibrated on small comparison samples with heterogeneous photometry
- Caveat (inferred, ours): Sample is Herschel-faint selected, so results may not generalise to all X-ray AGN

## Reproducibility

- Data public (paper): ALMA data acknowledged by project code; public status not explicitly stated  
  > "This paper makes use of ALMA data: ADS/JAO.ALMA#2012.1.00869.S and ADS/JAO.ALMA#2013.1.00884.S." (ACKNOWLEDGMENTS)
- Products in archive: _not stated_
- Missing: Scholtz et al. 2018 ALMA photometry catalogue
- Missing: Custom SED fitting code not released
- Missing: Stanley et al. 2015 photometry and fitting details
- Data volume (inferred): Moderate: two Band 7 snapshot programmes, ~110 short pointings; tens of GB raw
- Score (inferred): 3/5, Data and templates public, but imaging details, photometry and fitting code rest on companion papers; results numeric in tables.
- Rediscovery candidate: no, The recipe relies on inherited photometry and unreleased SED fitting code, so full redoing is difficult.

## Links

- Method: (cite: Stanley15) (SED fitting method and photometry)
- Method: (cite: Scholtz18) (ALMA reduction, catalogue and sample selection)
- Method: (cite: Hodge13) (ALMA imaging methodology)
- Companion: (cite: Scholtz18) (Companion paper using the SFRs to derive SFR and sSFR distributions)
- Companion: (cite: Mullaney15) (Earlier ALMA study of 24 X-ray AGN)
- Related: ALESS
- Related: Chandra Deep Field South
- Related: Chandra-COSMOS
- Related: Herschel PEP/GOODS-H and HerMES

## Checks

```json
{
 "quotes": 61,
 "quotes_ok": 61,
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
  "facts": 74,
  "stated": 47,
  "rate": 0.635
 },
 "evidence_ok": true
}
```
