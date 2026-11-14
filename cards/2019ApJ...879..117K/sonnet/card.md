# High Star Formation Rates of Low Eddington Ratio Quasars at z ≳ 6

`2019ApJ...879..117K` | The Astrophysical Journal 2019 | first author: Kim, Yongjung | arXiv: 1905.12268 | DOI: 10.3847/1538-4357/ab25ee

Card schema 1.0 | model claude-sonnet-5-5 | depth full | type observational_alma_primary

## Science

- Fields: agn_and_quasars, high_z_galaxies
- Question: Do z~6 quasars with low Eddington ratios have high host-galaxy star formation rates, as expected if SMBH growth precedes prolonged star formation?  
  > "high-redshift quasars with low Eddington ratios ($\lambda_{\rm Edd}$) would be found in actively star-forming hosts with a star formation rate (SFR) of $>100~M_{\odot}$ yr$^{-1}$." (abstract)
- Target **IMS J2204+0112**: coordinates _not stated_; z/distance z = 5.926  
  > "IMS J2204+0112 is a quasar at $z=5.926$ with a low bolometric luminosity of $L_{\rm bol}=4.24\times10^{12}~L_{\odot}$" (1 Introduction); distance from Kim et al. 2018 (cite: Kim18)  
  > "IMS J2204+0112 is a quasar at $z=5.926$ with a low bolometric luminosity of $L_{\rm bol}=4.24\times10^{12}~L_{\odot}$" (1 Introduction)

## Data provenance

- ALMA projects: 2016.1.01311.S, 2017.1.00125.S
- bands: Band 6 and Band 7  
  > "The ALMA observations of IMS J2204+0112 were carried out in band 6 and 7." (2.1 ALMA)
- frequencies and spectral setup: Central 250 and 343.5 GHz; SPWs at 241, 243, 257, 259 GHz (B6) and 336.5, 338.4, 348.5, 350.5 GHz (B7)  
  > "The central frequencies of the bands 6 and 7 were set to 250 and 343.5 GHz, respectively." (2.1 ALMA)
- continuum bandwidth: 7.5 GHz (four 1875 MHz basebands)  
  > "integrated over a continuum bandwidth of 7.5 GHz" (2.1 ALMA)
- arrays: 12 m antennae, 38 to 46 used  
  > "38 to 46 of the 12 m antennae were used" (2.1 ALMA)
- configurations: _not stated_
- baselines: 15-460 m  
  > "the baseline lengths were between 15 and 460 m" (2.1 ALMA)
- angular resolution: 0.6''-0.7''; beams 0.80''x0.57'' (B6), 0.81''x0.67'' (B7)  
  > "giving an angular resolution of $0.6\ensuremath{''}$-$0.7\ensuremath{''}$." (2.1 ALMA)
- max recoverable scale: _not stated_
- sensitivity: rms 0.021 mJy (B6), 0.026 mJy (B7) over 7.5 GHz  
  > "The rms noise values are 0.021 (band 6) and 0.026 mJy (band 7) over the 7.5 GHz bandwidth." (2.1 ALMA)
- time on source: 57.46 min (B6), 47.88 min (B7)  
  > "The on-source integration times were 57.46 (band 6) and 47.88 minutes (band 7)." (2.1 ALMA)
- observing dates: Band 6: 2016 Dec 13 and 2017 Apr 25; Band 7: 2018 May 17  
  > "The band 6 data were obtained on 2016 December 13 and 2017 April 25" (2.1 ALMA)
- pi or archival as stated: _not stated_
- Other facility **CFHTLS, IMS, HSC-SSP DR1, VIPERS-MLS, WISE, FIRST**: Archival multi-wavelength photometry for the SED  
  > "Table [1](#tbl:ancillary) lists the multi-wavelength datasets and the measured flux densities." (2.2 Ancillary Data)
- Other facility **JCMT SCUBA-2**: 450 and 850 um observations; non-detection, excluded from analysis  
  > "Therefore, the SCUBA-2 data are excluded from the analysis of the result." (Non-detections with SCUBA-2)
- External data: Rest-UV (Lbol, MBH, lambda_Edd) and FIR properties of z>~6 quasars compiled from literature  
  > "Derived Rest-UV and FIR Properties of $z\gtrsim6$ Quasars from the Literature" (Table 3) [from DeRosa11, Shen19, Decarli18, Mazzucchelli17, Willott10a, etc. (Table 3 refs)]
- External data: Simulated evolutionary track of a BH and host from Smidt et al.  
  > "we plot the evolutionary track of a BH in the simulation of (cite: Smidt18)" (4.2 SMBH Activity and Star Formation) [from (cite: Smidt18)]
- External data: Lbol, MBH, lambda_Edd of IMS J2204+0112 and UV spectral properties  
  > "This quasar has $M_{\rm BH}=1.23\times10^{9}~M_{\odot}$, and $\lambda_{\rm Edd}=0.11$" (1 Introduction) [from (cite: Kim15; Kim18)]

## Processing

### Calibration

- pipeline or manual: ALMA Science Pipeline  
  > "We used the reduced data that were provided by the ALMA Science Pipeline." (2.1 ALMA)
- casa version: _not stated_
- pipeline version: _not stated_
- archive products used as is: Pipeline-provided continuum maps used  
  > "the data were provided as integrated continuum maps at 250 and 343.5 GHz over the entire bandwidths" (2.1 ALMA)
- flux calibrator: J2148+0657 and J2253+1608 (flux/bandpass/pointing)  
  > "The sources for the flux/bandpass/pointing calibration were J2148+0657 and J2253+1608" (2.1 ALMA)
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
- final beam: 0.80''x0.57'' (B6), 0.81''x0.67'' (B7)  
  > "the synthesized beam sizes of the bands 6 and 7 are $0.80\ensuremath{''} \times 0.57\ensuremath{''}$ and $0.81\ensuremath{''} \times 0.67\ensuremath{''}$" (2.1 ALMA)
- final rms: 0.021 mJy (B6), 0.026 mJy (B7)  
  > "The rms noise values are 0.021 (band 6) and 0.026 mJy (band 7) over the 7.5 GHz bandwidth." (2.1 ALMA)

### Inherited from earlier work

- Fixed Td=47 K and beta=1.6 for modified blackbody; FIR defined over 42.5-122.5 um  
  > "adopting a model with fixed values of $T_{d}=47$ K and $\beta=1.6$ (cite: Beelen06)" (3.2 FIR Luminosity and Star-formation Rate) [from (cite: Beelen06); (cite: Dunne00)]
- SFR-LFIR relation, Chabrier IMF  
  > "in (cite: Willott17) for the Chabrier initial mass function (cite: Carilli13)." (3.2 FIR Luminosity and Star-formation Rate) [from (cite: Willott17)]
- Ancillary photometry measured with SExtractor as in earlier work  
  > "We measured the fluxes of IMS J2204+0112 with SExtractor (cite: Bertin96) as described in (cite: Kim15; Kim19)." (2.2 Ancillary Data) [from (cite: Kim15; Kim19)]
- MBH from L3000 and MgII FWHM; Lbol from L3000 with BC 5.18  
  > "with a bolometric correction factor of 5.18 (cite: Runnoe12)" (4.1 FIR Excess of IMS J2204+0112) [from (cite: Runnoe12); (cite: Vestergaard09)]

### Not stated but needed to reproduce (our reading)

- CASA version used by the ALMA pipeline and pipeline version
- Whether the pipeline continuum images used any specific weighting/robust or cleaning
- IMFIT region and initial parameters
- Flux calibrator flux values and absolute flux scale uncertainty
- Exact Lbol and MBH derivation inputs for the literature quasars (L3000, FWHM)
- Fitting of lambda_Edd-dependent trend (red dotted line) method
- Binning/scaling of the Smidt18 track
- Values of f_host and L_UV used for A_UV curves

## Analysis recipe

1. **measure continuum flux densities**: Fit 2D Gaussian to each continuum map with IMFIT  
  > "Using the IMFIT task of the CASA package, we fitted the source on each continuum map with a simple 2D Gaussian model" (3.1 Sub-mm Continuum Maps of IMS J2204+0112)
   - software: CASA
   - fitting: _not stated_
   - validation: Residual maps after point-source subtraction show no features  
  > "no features in the residual maps after the point source model subtraction (right panels of Figure [1](#fig:alma))" (3.1 Sub-mm Continuum Maps of IMS J2204+0112)
2. **derive LFIR from modified blackbody**: Fit modified blackbody to 250 GHz point, to two bands, and to eight SPW fluxes; integrate 42.5-122.5 um  
  > "we define the $L_{\rm FIR}$ as the integrated luminosity over the wavelength range from 42.5 to 122.5 $\mu$m in the rest frame." (3.2 FIR Luminosity and Star-formation Rate)
   - software: MPFIT
   - parameter: Td=47 K, beta=1.6 fixed; also free Td and beta  
  > "adopting a model with fixed values of $T_{d}=47$ K and $\beta=1.6$ (cite: Beelen06)" (3.2 FIR Luminosity and Star-formation Rate)
   - assumption: Cosmology Om=0.3, OL=0.7, H0=70  
  > "we used the cosmological parameters of $\Omega_{m}=0.3$, $\Omega_{\Lambda}=0.7$, and $H_{0}=70$ km s$^{-1}$ Mpc$^{-1}$" (1 Introduction)
   - fitting: Least-squares with MPFIT; errors from 10,000 Monte Carlo mock flux sets, median and 68% range  
  > "We generated 10,000 mock sets of flux densities by adding Gaussian random noises scaled by the flux measurement uncertainties, and found a best-fit model for each set." (Footnote 2)
   - validation: Compared single-band, two-band, 8-SPW and free-parameter results (5-30% differences)  
  > "results in a modest increase (5–10%, but up to 30% in rare cases) in the $L_{\rm FIR}$ value." (3.2 FIR Luminosity and Star-formation Rate)
3. **convert LFIR to SFR**: SFR = 1.7e-10 LFIR/Lsun Msun/yr  
  > "\frac{\rm SFR}{M_{\odot}~\rm{yr}^{-1}}\sim1.7\times 10 ^{-10}~\frac{L_{\rm FIR}}{L_{\odot}}," (3.2 FIR Luminosity and Star-formation Rate)
   - assumption: FIR flux arises mainly from star formation; Chabrier IMF  
  > "Under the assumption that the FIR flux of IMS J2204+0112 mainly arises due to star formation" (3.2 FIR Luminosity and Star-formation Rate)
   - fitting: _not stated_
   - validation: _not stated_
4. **test dust-obscuration explanation via A_UV**: Estimate A_UV from LFIR/LUV using Calzetti00 eq. 7 for varying f_host  
  > "we estimated the UV extinction of the host galaxy ($A_{\rm UV}$ at 0.16 $\mu$m) of IMS J2204+0112 from the ratio of the host galaxy’s FIR and UV luminosities" (4.1 FIR Excess of IMS J2204+0112)
   - assumption: Host is a starburst; LFIR dominated by host  
  > "Under the assumption that its host galaxy is a starburst galaxy" (4.1 FIR Excess of IMS J2204+0112)
   - fitting: _not stated_
   - validation: Rejected obscured-quasar scenario using emission lines and UV slope  
  > "IMS J2204+0112 has evident Ly$\alpha~\lambda1216$ and C IV $\lambda1549$ emission lines (cite: Kim18)." (4.1 FIR Excess of IMS J2204+0112)
5. **compare with literature quasars and simulation**: Compute LFIR, Lbol, MBH, lambda_Edd, SFR for literature z>~6 quasars from single ~250 GHz flux; compare to Smidt18 track  
  > "the $L_{\rm FIR}$ values were derived in the same manner as IMS J2204+0112 using the FIR continuum flux densities at $\sim250$ GHz in the literature" (4.1 FIR Excess of IMS J2204+0112)
   - parameter: 3 sigma upper limits for FIR-undetected; LEQ defined as lambda_Edd<0.2  
  > "For FIR-undetected quasars, we used 3$\sigma$ detection limits on FIR flux densities" (4.1 FIR Excess of IMS J2204+0112)
   - fitting: _not stated_
   - validation: _not stated_

## Software

- **CASA** : Pipeline reduction and IMFIT source fitting  
  > "Using the IMFIT task of the CASA package" (3.1 Sub-mm Continuum Maps of IMS J2204+0112)
- **SExtractor** : Photometry of ancillary imaging  
  > "We measured the fluxes of IMS J2204+0112 with SExtractor (cite: Bertin96)" (2.2 Ancillary Data)
- **MPFIT** : Modified blackbody fitting  
  > "The best-fit model using the MPFIT package (cite: Markwardt09)" (3.2 FIR Luminosity and Star-formation Rate)

## Numeric results

| quantity | value | uncertainty | units | step | quote |
|---|---|---|---|---|---|
| Flux density at 250 GHz | 1.474 | 0.023 | mJy | 1 | $f_{\rm 250GHz}=1.474\pm0.023$ and $f_{\rm 343.5GHz}=3.132\pm 0.028$ mJy |
| Flux density at 343.5 GHz | 3.132 | 0.028 | mJy | 1 | $f_{\rm 250GHz}=1.474\pm0.023$ and $f_{\rm 343.5GHz}=3.132\pm 0.028$ mJy |
| LFIR (250 GHz, Td=47 K, beta=1.6) | 3.30e12 | +/-0.05e12 | Lsun | 2 | $L_{\rm FIR}= (3.30^{+0.05}_{-0.05}) \times10^{12}~L_{\odot}$ |
| SFR (representative) | 560 | +/-8 | Msun/yr | 3 | $\bm{560^{+8}_{-8}}$ |
| Free-fit Td, beta (beta>1.6 mode) | Td=46.5, beta=1.73 | +1.9/-1.8; +/-0.03 | K; dimensionless | 2 | $46.5^{+1.9}_{-1.8}$ |
| LFIR (beta<1.6 mode) | 4.30e12 | +0.35/-0.37 | Lsun | 2 | we obtained $L_{\rm FIR}=(4.30^{+0.35}_{-0.37}) \times10^{12}~L_{\odot}$ |
| LFIR/Lbol | 0.8 | not stated | dimensionless | 5 | IMS J2204+0112 has the highest $L_{\rm FIR}/L_{\rm bol}$ value of 0.8 |
| Lower limit on A_UV | >1.7 | not stated | mag | 4 | The lower limit of the UV extinction of IMS J2204+0112 would be $A_{\rm UV}>1.7$ or $E(B-V)>0.4$ |

## Qualitative findings

- Source is compact (<~0.7'' or ~4 kpc) with no spectral features seen; ALMA position offset ~0.2'' from z-band  
  > "The central positions of the ALMA detection are offset by only about $0.2\ensuremath{''}$ from the $z$-band position" (3.1 Sub-mm Continuum Maps of IMS J2204+0112)

## Claim tuples

- H: A low-Eddington-ratio z~6 quasar can have a strongly star-forming host | E: ALMA band 6/7 continuum, modified blackbody fit to LFIR | R: LFIR (3.3-4.3)e12 Lsun, SFR 560-731 Msun/yr | F: Host has high SFR, ~order of magnitude above Lbol-matched high-lambda_Edd quasars | **supported**
- H: High LFIR/Lbol is due to dust obscuring the quasar | E: A_UV estimate and checks of emission lines and UV slope | R: Would require A_UV>1.7 and implausibly steep intrinsic slope | F: Obscured-quasar interpretation rejected | **supported**
- H: Low-lambda_Edd high-SFR quasars match end stage of simulated quasar evolution | E: Compare literature quasars in MBH, lambda_Edd, SFR with Smidt18 track | R: Distributions consistent with the track | F: LEQs may be nearing end of SMBH growth while hosts keep forming stars | **partially**

## Reasoning

- Why this data: _not stated_
- Why this method: Using 250 GHz single-point LFIR for comparability with other z>~6 quasars  
  > "for the sake of comparison with other $z\gtrsim6$ quasars for which $L_{\rm FIR}$ are derived from single data points at $\sim250$ GHz." (3.2 FIR Luminosity and Star-formation Rate)
- Alternative: Obscured-quasar scenario rejected  
  > "However, the suggestion that IMS J2204+0112 is an obscured quasar can be rejected due to the following reasons." (4.1 FIR Excess of IMS J2204+0112)
- How they decided it was enough: _not stated_
- Limitation (authors): Small LEQ sample; quasars not a complete sample  
  > "Since the number of low-$\lambda_{\rm Edd}$ quasars used in the discussion is small, enlarging the sample is necessary to see the validity of our suggestion." (5 Summary)
- Limitation (authors): Alternative explanations (episodic super-Eddington accretion) possible  
  > "leaving a possibility that high-redshift quasar evolution is much more diverse than the simple picture we discussed earlier." (4.2 SMBH Activity and Star Formation)
- Caveat (inferred, ours): Only one new ALMA source; comparison relies on heterogeneous literature fluxes and Td assumptions
- Caveat (inferred, ours): Lbol and MBH of IMS J2204+0112 are uncertain (single-epoch MgII, variability)
- Caveat (inferred, ours): SFR from LFIR ignores AGN heating contribution
- Caveat (inferred, ours): No dynamical/line info to confirm star-formation origin
- Caveat (inferred, ours): Anticorrelation may be affected by selection and shared dependence on Lbol

## Reproducibility

- Data public (paper): _not stated_
- Products in archive: Pipeline products from ALMA archive were used  
  > "We used the reduced data that were provided by the ALMA Science Pipeline." (2.1 ALMA)
- Missing: Pipeline CASA version
- Missing: Literature quasar input measurements (L3000, FWHM, 250 GHz fluxes) must be taken from cited papers
- Missing: Details of correlation fitting
- Data volume (inferred): small (~ a few GB raw; pipeline continuum images only ~MB)
- Score (inferred): 4/5, Simple continuum analysis with pipeline images and clear formulas; literature compilation steps are less specified.
- Rediscovery candidate: yes, Archive data public by ALMA policy, simple recipe and numeric results (fluxes, LFIR, SFR), though the data release status is inferred.

## Links

- Method: (cite: Beelen06) (Modified blackbody Td=47 K, beta=1.6)
- Method: (cite: Willott17) (SFR-LFIR relation)
- Method: (cite: Calzetti00) (A_UV equation)
- Companion: (cite: Kim18) (Optical/NIR spectroscopy giving Lbol, MBH, lambda_Edd of IMS J2204+0112)
- Companion: (cite: Smidt18) (Simulated evolutionary track compared with data)
- Related: Infrared Medium-deep Survey (IMS)
- Related: HSC-SSP
- Related: CFHTLS

## Checks

```json
{
 "quotes": 63,
 "quotes_ok": 63,
 "quote_pass_rate": 1.0,
 "quotes_too_long": 0,
 "unsupported_facts": 0,
 "project_codes": 2,
 "codes_not_in_text": [],
 "codes_not_in_obscore": [],
 "obscore_codes_not_in_card": [],
 "codes_printed_but_missing": [],
 "numeric_results": 8,
 "numeric_problems": 0,
 "fill": {
  "facts": 79,
  "stated": 49,
  "rate": 0.62
 },
 "evidence_ok": true
}
```
