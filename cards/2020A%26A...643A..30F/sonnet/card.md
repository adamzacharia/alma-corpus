# GOODS-ALMA: The slow downfall of star formation in z = 2-3 massive galaxies

`2020A&A...643A..30F` | Astronomy and Astrophysics 2020 | first author: Franco, M. | arXiv: 2005.03043 | DOI: 10.1051/0004-6361/202038312

Card schema 1.0 | model claude-sonnet-5-5 | depth full | type observational_alma_primary

## Science

- Fields: high_z_galaxies
- Question: What are the gas fractions, depletion times, sizes and morphologies of massive ALMA-selected galaxies at z~2-3 in GOODS-South, and do they support a slow exhaustion of gas as the path to quiescence?  
  > "In $\S$[5](#sec:slow_death), we discuss the results and interpret them as the evidence for a slow downfall of star formation in $z\sim2-3$ massive galaxies." (1 Introduction)
- Target **GOODS-ALMA field, 35 ALMA-detected galaxies (AGS1-AGS39)**: coordinates RA 03h32m30.0s, Dec -27d48m00s (J2000), field centre  
  > "centered at $\alpha=3^{\rm h}$ 32$^{\rm m}$ 30.0$^{\rm s}$, $\delta=-27$ 48$'$ 00$''$ (J2000)" (2.1 ALMA data); "we analyze a sample of 35 galaxies with redshifts between 0.6 and 4.7 (z$_{med}$ = 2.7)" (2.1 ALMA data); z/distance z = 0.6-4.7, median 2.7  
  > "centered at $\alpha=3^{\rm h}$ 32$^{\rm m}$ 30.0$^{\rm s}$, $\delta=-27$ 48$'$ 00$''$ (J2000)" (2.1 ALMA data); "we analyze a sample of 35 galaxies with redshifts between 0.6 and 4.7 (z$_{med}$ = 2.7)" (2.1 ALMA data); distance from _not stated_

## Data provenance

- ALMA projects: 2015.1.00543.S
- bands: _not stated_
- frequencies and spectral setup: _not stated_
- continuum bandwidth: _not stated_
- arrays: _not stated_
- configurations: _not stated_
- baselines: _not stated_
- angular resolution: _not stated_
- max recoverable scale: _not stated_
- sensitivity: RMS ~0.18 mJy/beam in 0.60"-tapered mosaic, 69 arcmin2  
  > "We perform this analysis in a 0.60$''$-tapered mosaic reaching a RMS $\simeq 0.18$ mJy beam$^{-1}$." (2.1 ALMA data)
- time on source: _not stated_
- observing dates: August-September 2016  
  > "ALMA observations obtained between August and September 2016" (2.1 ALMA data)
- pi or archival as stated: PI D. Elbaz  
  > "(Project ID: 2015.1.00543.S; PI: D. Elbaz)" (2.1 ALMA data)
- Other facility **Herschel PACS/SPIRE**: FIR photometry for SED fitting (SPIRE from Wang et al. in prep. deblended catalog)  
  > "we use the catalog of Wang et al. (in prep.), which is built with a state-of-the-art de-blending method." (2.2 Multiwavelength coverage)
- Other facility **HST, Spitzer, VLA, Chandra, ground-based optical/NIR**: UV-to-radio photometry, sizes, morphologies, X-ray AGN identification  
  > "to fit the spectral energy distribution of these galaxies from the radio to the UV." (2.2 Multiwavelength coverage)
- External data: ALMA source catalog (23 main + 16 supplementary sources), fluxes, redshifts, stellar masses  
  > "where the properties of 23 bright ALMA sources discovered as the result of the blind survey in this field are discussed and cataloged." (2.1 ALMA data) [from Franco et al. 2018 (cite: Franco2018); Franco et al. 2020 (cite: Franco2020)]
- External data: HST galaxy sizes and Sersic indices  
  > "Galaxy sizes and Sérsic indices are obtained from (cite: Van_der_Wel2014)." (5.2.1 Size) [from (cite: Van_der_Wel2014)]
- External data: CNN morphological classification probabilities  
  > "We cross-matched our sample with the catalog of (cite: Huertas-Company2015) that estimates the probability of being a spheroid, disk or irregular" (5.2.2 Morphology) [from (cite: Huertas-Company2015)]
- External data: X-ray catalog of the 7 Ms Chandra Deep Field-South  
  > "Of the 1008 sources detected in X-ray during the 7 Ms exposure survey of the *Chandra* Deep Field–South presented in (cite: Luo2017), 397 lie in the GOODS-ALMA field." (4.4 AGN) [from (cite: Luo2017)]

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

- ALMA data reduction and survey description, source detection, offset corrections  
  > "The complete description of this survey and the data reduction are presented in detail in , where the properties of 23 bright ALMA sources" (2.1 ALMA data) [from Franco et al. 2018 (cite: Franco2018)]
- CIGALE parameter grid  
  > "The parameters used in `CIGALE` were given by (cite: Ciesla2018) and are shown in Table [1](#table:CIGALE_parameter)." (3.1 Method) [from (cite: Ciesla2018)]
- Supplementary 3.5 sigma catalog using IRAC and VLA counterparts  
  > "we used *Spitzer*/IRAC and VLA to extend our catalog to 16 additional sources detected down to 3.5$\sigma$" (1 Introduction) [from Franco et al. 2020 (cite: Franco2020)]

### Not stated but needed to reproduce (our reading)

- Wang et al. in prep. Herschel deblended catalog not public
- ALMA calibration/imaging parameters (CASA version, robust, cleaning) only in Franco+2018
- Flux density correction applied to ALMA fluxes (starred values in Table) not specified here
- Redshift sources (spectroscopic vs photometric) and stellar masses come from earlier paper
- Details of uvmodelfit size measurements and blobcat settings
- Exact SED-fitting photometric inputs and upper-limit treatment
- Linear fitting method for f_gas-M* and tau_dep-Sigma_SFR relations

## Analysis recipe

1. **SED fitting**: CIGALE for galaxies with Herschel counterparts; Schreiber+2017 dust library normalized to 1.13 mm ALMA flux otherwise; UV-16um and 24um-mm fitted independently  
  > "We independently fit the wavelengths from the UV up to 16 $\mu$m, and from 24 $\mu$m up to the millimeter wavelengths respectively" (3.1 Method)
   - software: CIGALE
   - parameter: Bruzual & Charlot 2003 stellar models, Calzetti 2000 attenuation, Draine 2014 dust emission  
  > "We use the stellar population models of (cite: Bruzual2003) and the attenuation law of (cite: Calzetti2000)." (3.1 Method)
   - assumption: Radio added via FIR/radio ratio 2.34  
  > "using the FIR/radio correlation, with a constant ratio between FIR and radio luminosity of 2.34 (cite: Yun2001)" (3.1 Method)
   - fitting: _not stated_
   - validation: Dust masses compared between CIGALE and Schreiber+2017 library: offset ~0.15 dex  
  > "We find a systematic offset of approximately 0.15 dex between the two methods, where dust masses derived using `CIGALE` are systematically larger." (4.1 Dust mass)
2. **AGN subtraction**: decompIR AGN fits extended below 3 um with Kirkpatrick+2015 template; two-iteration CIGALE fit  
  > "The SED fitting is done in two iterations; during the first iteration, we remove the contribution of the AGN." (3.2 AGN subtraction)
   - software: decompIR, CIGALE
   - assumption: Stellar masses of AGN hosts not corrected  
  > "we have chosen not to modify the stellar masses of galaxies hosting an AGN" (3.2 AGN subtraction)
   - fitting: _not stated_
   - validation: _not stated_
3. **Dust temperature**: Modified blackbody fit to points at lambda_rest >= 0.55 lambda_peak  
  > "We fit the flux densities at $\lambda_{rest} \ge 0.55 \lambda_{peak}$ using the MBB model as suggested by (cite: Hwang2010)" (3.3 Dust temperature)
   - parameter: beta = 1.5  
  > "We have assumed a spectral index $\beta=1.5$ (cite: Kovacs2006; Gordon2010)." (3.3 Dust temperature)
   - fitting: _not stated_
   - validation: beta=2 would give 1-4 K lower temperatures  
  > "the MBB temperatures would have been slightly lower (1 - 4 K lower)" (3.3 Dust temperature)
4. **Dust and gas masses**: Dust mass from CIGALE (Draine+2007 formalism); gas mass from metallicity-dependent gas-to-dust ratio of Leroy+2011, metallicity from Genzel+2012 mass-metallicity relation  
  > "To compute the gas mass, we assume a gas-to-dust ratio ($\delta_{GDR}$) depending only on metallicity." (4.2 Gas mass)
   - software: CIGALE
   - parameter: U_max=1e6, alpha=2  
  > "we adopt the maximum starlight intensity relative to the local interstellar radiation field $U_{\max}$ = $10^6$ U$_{\odot}$, and the power-law index $\alpha$ = 2" (4.1 Dust mass)
   - assumption: HI negligible; GDR relation valid at all z; Salpeter IMF with M*(Salp)=1.7 M*(Chab)  
  > "At the redshifts of this study, the atomic hydrogen can be considered negligible compared to the molecular form" (4.2 Gas mass)
   - fitting: _not stated_
   - validation: Metallicity compared with Mannucci+2010 FMR (ratio 1.03±0.01); gas mass compared with Scoville+2016 (ratio 1.1±0.6, T=25 K)  
  > "M$_{(mol,\ Scoville)}$/M$_{(gas,\ this\, work)}$ = 1.1 $\pm$ 0.6." (4.2 Gas mass)
5. **SFR and depletion time**: SFR_IR = 1.72e-10 L_IR (Kennicutt98) plus SFR_UV (Daddi+2004); tau_dep = Mgas/SFR; compare to Tacconi+2018 scaling relations  
  > "The infrared luminosity of each galaxy has been converted to SFR using the Kennicutt relation (cite: Kennicutt1998)" (4.3.1 SFR_IR)
   - fitting: _not stated_
   - validation: _not stated_
6. **Sizes and morphology**: ALMA 1.1 mm sizes from CASA uvmodelfit; compare with HST 5000 A sizes from van der Wel+2014; morphological classes from Huertas-Company CNN catalog with control sample matched in z and M*  
  > "FWHM measured from uvmodelfit in `CASA`" (Table 2)
   - software: CASA, GALFIT
   - fitting: _not stated_
   - validation: Control sample of closest galaxies in redshift and stellar mass  
  > "a galaxy closest to it in terms of redshift and stellar mass" (5.2.2 Morphology)
7. **Sigma_SFR vs depletion time**: Sigma_SFR = SFR/(2 pi R_1.1mm^2); fit power law to tau_dep  
  > "$$\Sigma_{SFR}\,=\,\text{SFR}/(2\pi R_{1.1mm}^2 ),$$" (5.3)
   - fitting: _not stated_
   - validation: _not stated_

## Software

- **CIGALE** : SED fitting and dust mass  
  > "we employ the SED-fitting code `CIGALE` [^2] (Code Investigating Galaxies Emission; (cite: Boquien2019))" (3.1 Method)
- **decompIR** : AGN component fitting  
  > "we used the code $\texttt{decompIR}$ by (cite: Mullaney2011)" (3.2 AGN subtraction)
- **CASA (uvmodelfit)** : ALMA source sizes  
  > "FWHM measured from uvmodelfit in `CASA`" (Table 2)
- **GALFIT** : HST Sersic fits (from van der Wel+2014)  
  > "fitting a single-component Sérsic profile using `GALFIT` (cite: Peng2010)" (5.2.1 Size)

## Numeric results

| quantity | value | uncertainty | units | step | quote |
|---|---|---|---|---|---|
| Median dust temperature | 40 | not stated | K | 3 | We have found a median dust temperature of 40 K for our sample. |
| Fraction of galaxies below the f_gas-R_SB relation | 40% | not stated | percent | 5 | we find a surprisingly large fraction (40%) of galaxies lying well below this relation |
| Median gas fraction | 0.52 | not stated | dimensionless | 4 | with a median of f$_{gas}$ = 0.52 (mean = 0.52) |
| Gas depletion time range | 30-1600 | not stated | Myr | 5 | The depletion times span a large range, between 30 and 1600 Myr. |
| Median r_e,HST / r_e,ALMA | 2.3 | not stated | dimensionless | 6 | we find that ALMA sizes are generally smaller, with a median $r_{e,\text{HST}}$/$r_{e,\text{ALMA}}$ = 2.3. |
| Fraction irregular/mergers | 61% (11/18) | not stated | percent | 6 | 61% (11/18) of our galaxies are classified as irregulars/mergers |
| tau_dep-Sigma_SFR relation | tau_dep = 10^3.20 * Sigma_SFR^-0.49 | ±0.25 (log norm), ±0.12 (slope) | Myr | 7 | \tau_{dep} [Myr]\,=\,10^{(3.20\pm0.25)} \times \Sigma_{SFR}^{(-0.49\pm0.12)}. |
| f_gas vs log M* slope | -0.45 | ±0.09 | dimensionless | 5 | f_{gas}\,=\,(-0.45\pm0.09) \times \log_{10}(M_\star)\,+\,5.44\pm0.95. |

## Qualitative findings

- ALMA-detected galaxies are mostly starbursts or upper main sequence; 54% have R_SB>3  
  > "54% of them have a R$_{SB}$(SFR/SFR$_{MS}$) $>$ 3" (4.3.1 SFR_IR)

## Claim tuples

- H: Massive ALMA galaxies have low gas fractions and short depletion times | E: Gas masses from dust masses and GDR compared to Tacconi+2018 scaling relations | R: About half follow the relation; 40% lie well below, with short depletion times | F: A large fraction are exhausting their gas, consistent with slow downfall/starvation, AGN possibly involved | **supported**
- H: ALMA-selected galaxies are progenitors of compact z~2 ellipticals | E: Compared ALMA 1.1 mm sizes and HST 5000 A sizes | R: Dust sizes ~2.3 times smaller than optical sizes | F: Compact obscured star formation will make them compact | **supported**
- H: Mergers drive compaction | E: CNN morphologies vs a control sample | R: 61% irregular/mergers vs 6% in control | F: ALMA galaxies biased toward irregulars | **partially**

## Reasoning

- Why this data: _not stated_
- Why this method: _not stated_
- How they decided it was enough: _not stated_
- Limitation (authors): Gas mass uncertainties are large; metallicity assumed; selection bias in small survey  
  > "We keep in mind that the uncertainties on the determination of $M_{gas}$ are large, taking into account all of the assumptions used." (4.2 Gas mass)
- Caveat (inferred, ours): Gas masses depend on assumed GDR-metallicity relation with metallicity from mass only
- Caveat (inferred, ours): Only 18-20 galaxies in morphology sample
- Caveat (inferred, ours): Low gas fractions may reflect AGN bias in stellar mass
- Caveat (inferred, ours): Fluxes possibly underestimated

## Reproducibility

- Data public (paper): _not stated_
- Products in archive: _not stated_
- Missing: Wang et al. in prep. Herschel catalog
- Missing: Reduced ALMA images/catalog from Franco+2018, 2020
- Missing: Fitting method for correlations
- Data volume (inferred): ~100-300 GB raw for the mosaic; derived catalogs are small
- Score (inferred): 3/5, The analysis is mostly catalog-level SED fitting built on inputs from companion papers and an unpublished catalog; software is public.
- Rediscovery candidate: no, Depends on companion-paper catalogs and unpublished Herschel photometry.

## Links

- Method: Franco et al. 2018 (cite: Franco2018) (ALMA data reduction and survey description)
- Method: Schreiber et al. 2018 (cite: Schreiber2017) (IR library)
- Companion: Franco et al. 2020 (cite: Franco2020) (Supplementary catalog and counterparts)
- Related: GOODS-ALMA
- Related: ASAGAO
- Related: HUDF ALMA survey
- Related: ASPECS
- Related: CANDELS

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
 "numeric_results": 8,
 "numeric_problems": 0,
 "fill": {
  "facts": 85,
  "stated": 38,
  "rate": 0.447
 },
 "evidence_ok": true
}
```
