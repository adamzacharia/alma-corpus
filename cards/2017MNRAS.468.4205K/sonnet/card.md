# ALMA observations of cold molecular gas in AGN hosts at z ∼ 1.5 - evidence of AGN feedback?

`2017MNRAS.468.4205K` | Monthly Notices of the Royal Astronomical Society 2017 | first author: Kakkad, D. | arXiv: 1703.08183 | DOI: 10.1093/mnras/stx726

Card schema 1.0 | model claude-sonnet-5-5 | depth full | type observational_alma_primary

## Science

- Fields: agn_and_quasars, high_z_galaxies
- Question: Does the presence of an AGN affect the molecular gas content and star formation efficiency of its host galaxy at z~1.5, compared with matched non-AGN galaxies?  
  > "The main goal of this paper is to identify whether the presence of an AGN affects the molecular gas content of its host galaxy and consequently the star formation process." (Observed relations for AGNs)
- Target **10 obscured X-ray AGN hosts at z~1.5 (C1591, C92, #226, X5308, X2522, C1148, C488, C152, C103, #682)**: coordinates e.g. C1591: RA 10 01 43, Dec +02 33 31 (see Table 1 for all)  
  > "| C1591\* | 10 01 43 | +02 33 31 | 1.238 | 45.7 | 11.3 | 12.6 | 362 | COSMOS |" (Table 1); z/distance z = 1.155-1.581 (spectroscopic)  
  > "| C1591\* | 10 01 43 | +02 33 31 | 1.238 | 45.7 | 11.3 | 12.6 | 362 | COSMOS |" (Table 1); distance from spectroscopic redshifts, COSMOS and CDFS catalogues  
  > "| C1591\* | 10 01 43 | +02 33 31 | 1.238 | 45.7 | 11.3 | 12.6 | 362 | COSMOS |" (Table 1)

## Data provenance

- ALMA projects: 2013.1.00171.S
- bands: Band 3  
  > "The observations were carried out in Band 3, with the receiver tuned to the frequency of $\mathrm{^{12}CO(2-1)}$ emission" (3 Observations and Data analysis)
- frequencies and spectral setup: tuned to CO(2-1), rest frequency 230.5 GHz; ~24 km/s resolution  
  > "The velocity/spectral resolution for all observations was $\sim$24 km/s." (3 Observations and Data analysis)
- continuum bandwidth: _not stated_
- arrays: 12m antennas (35-38)  
  > "using 35-38 12m antennas" (3 Observations and Data analysis)
- configurations: _not stated_
- baselines: up to 800 m  
  > "We reached baselines up to 800 m" (3 Observations and Data analysis)
- angular resolution: ~1.5"x1.4" and 0.8"x0.5"  
  > "resulting in beam sizes of $\sim 1.5^{\prime\prime} \times 1.4^{\prime\prime}$ and $0.8^{\prime\prime} \times 0.5^{\prime\prime}$" (3 Observations and Data analysis)
- max recoverable scale: _not stated_
- sensitivity: 0.21, 0.13, 0.11 Jy/beam in 880, 320, 320 km/s channels for C1591, C92, #226  
  > "we reached a sensitivity of 0.21, 0.13 and 0.11 Jy/beam in 880 km/s, 320 km/s and 320 km/s wide spectral channels" (3 Observations and Data analysis)
- time on source: ~2.5-8 minutes per target (151.2 s or 483.84 s)  
  > "The on-source exposure time was kept between $\sim$2.5-8 minutes depending on the sensitivity requirements." (3 Observations and Data analysis)
- observing dates: _not stated_
- pi or archival as stated: Cycle 2, PI V. Mainieri  
  > "carried out in cycle 2 (Project code: 2013.1.00171.S, PI: V. Mainieri)" (3 Observations and Data analysis)
- Line: 12CO J=2-1 (230.5 GHz)
- Other facility **Chandra/XMM-Newton**: X-ray AGN selection  
  > "We selected our AGN sample in the X-ray band" (2 Target selection)
- Other facility **Herschel PACS**: IR luminosity and SFR  
  > "The SFR were estimated from Herschel Photoconductor Array Camera and Spectrometer (PACS) photometry" (2 Target selection)
- Other facility **IRAM-PdBI**: CO measurements of non-AGN comparison sample (from literature)  
  > "for which the molecular gas measurements are available from CO observations using IRAM-PdBI" (2 Target selection)
- Other facility **HST-ACS**: optical image of C1591 for comparison with CO contours  
  > "The top left panel of Fig. [4](#maps) shows the HST-ACS image of C1591" (Molecular mass from CO)
- External data: Non-AGN comparison sample with CO gas measurements  
  > "We constructed the comparison non-AGN sample from the work of (cite: daddi10; tacconi13) and (cite: magnelli13)" (2 Target selection) [from (cite: daddi10; tacconi13; magnelli13)]
- External data: SFR, Lbol and stellar masses via SED fitting  
  > "We refer the reader to (cite: bonzini15) for details about the SED fitting." (2 Target selection) [from (cite: bonzini15; bongiorno12; bonzini13)]
- External data: Main sequence parametrization  
  > "we adopt one of the most recent parametrization from (cite: schreiber15)" (2 Target selection) [from (cite: schreiber15)]
- External data: Literature AGN data: five Tacconi13 galaxies and XID2028  
  > "Five galaxies from the (cite: tacconi13) sample have been classified as AGN by matching them with the (cite: nandra15) AEGIS-X catalog" (2 Target selection) [from (cite: tacconi13; nandra15; brusa15)]
- External data: Reference MS gas-SFR and L'CO-LIR relations  
  > "given by the following mean equation adapted from (cite: sargent14) for MS galaxies" (Observed relations for AGNs) [from (cite: sargent14)]

## Processing

### Calibration

- pipeline or manual: _not stated_
- casa version: CASA 4.2.2 (for imaging)  
  > "imaging for all the targets was done using CASA (version 4.2.2)" (3 Observations and Data analysis)
- pipeline version: _not stated_
- archive products used as is: calibrated data products as delivered  
  > "We used the calibrated data products as delivered to us" (3 Observations and Data analysis)
- flux calibrator: _not stated_
- flux scale uncertainty: _not stated_
- self calibration: _not stated_

### Imaging

- task: CASA clean  
  > "The images were cleaned using the CASA task “CLEAN” with “natural” WEIGHTING." (3 Observations and Data analysis)
- deconvolver: _not stated_
- weighting robust: natural  
  > "with “natural” WEIGHTING" (3 Observations and Data analysis)
- uv taper: _not stated_
- cell size: _not stated_
- image size: 160 arcsec; analysis within 25 arcsec of field center  
  > "The angular scale of the final image is 160$^{\prime\prime}$ and the analysis was restricted within 25$^{\prime\prime}$ of the field center." (3 Observations and Data analysis)
- masking: _not stated_
- multiscale scales: _not stated_
- continuum subtraction: _not stated_
- line free channels: _not stated_
- primary beam correction: _not stated_
- array combination: _not stated_
- smoothing: velocity bins of 50 km/s for C92, 80 km/s for others  
  > "imaging was done with velocity bins of 50 km/s for C92 and for the remaining targets we used 80 km/s" (3 Observations and Data analysis)
- final beam: _not stated_
- final rms: _not stated_

### Inherited from earlier work

- Assumed average CO(2-1) line width of 400 km/s  
  > "assuming an average width of the CO(2-1) line of 400 km/s (cite: daddi10)" (3 Observations and Data analysis) [from (cite: daddi10)]
- Dark matter 25% of dynamical mass within half-light radius; Mdyn-Mgas relation  
  > "Here we assume a dark matter component within the half-light radius to be 25% of the total dynamical mass (cite: daddi10)." (Molecular mass from CO) [from (cite: daddi10)]
- L'CO formula  
  > "we calculate the CO luminosity using the result from (cite: solomon05)" (Molecular mass from CO) [from (cite: solomon05)]
- alpha_CO = 3.6 adopted as commonly used for MS galaxies  
  > "we use an $\mathrm{\alpha_{CO}}$ value of 3.6, which is commonly used in literature for MS galaxies at a similar redshift as our AGN sample (cite: daddi10; tacconi13)" (Molecular mass from CO) [from (cite: daddi10; tacconi13)]
- CO(3-2) to CO(1-0) excitation correction of 2 for literature data  
  > "we employ an excitation correction of 2 to convert to CO\[1-0\] luminosity following (cite: tacconi13)" (Molecular mass from CO) [from (cite: tacconi13)]
- rms computed from moment maps rather than spectra  
  > "We did not compute rms directly from the spectrum since the noise is a function of frequency and this introduces systematic uncertainties in our measurements (cite: maiolino15)." (3 Observations and Data analysis) [from (cite: maiolino15)]

### Not stated but needed to reproduce (our reading)

- Number of clean iterations, threshold and masking
- Cell size and exact channel ranges used for moment-0 maps
- Which channels were used for continuum/line separation (continuum undetected)
- Flux calibrator and calibration uncertainty
- Details of the survdiff test grouping and how censored data were treated in the fits
- Exact aperture centers and MPFIT initial guesses
- Details of the stacking of non-detections
- Dynamic-mass inclination handling and exact half-light radius deconvolution
- Values of the comparison sample after alpha_CO recalculation

## Analysis recipe

1. **Select AGN sample and comparison sample**: X-ray AGN with secure spec-z, Herschel SFR and SED-fit Mstar, placed on the MS of Schreiber15; non-AGN sample from literature matched in z, Mstar, SFR  
  > "We also matched the sample from these works in SFR and M$_{\ast}$ to that of the AGN sample to make sure we are comparing similar galaxies." (2 Target selection)
   - parameter: AGN: L(2-10 keV) > 1e42 erg/s; non-AGN below this and on MS; 1<z<2  
  > "have an X-ray luminosity (2-10 keV) less than $\mathrm{10^{42}}$ erg/s, while any object above this X ray luminosity is regarded as an AGN" (1 Introduction)
   - assumption: Chabrier IMF; SFR = 1e-10 LIR  
  > "using the relation $\mathrm{SFR = 10^{-10}\cdot L_{IR} [L_{\odot}]}$ assuming a Chabrier initial mass function (IMF)" (2 Target selection)
   - fitting: _not stated_
   - validation: _not stated_
2. **Image CO(2-1) cubes and measure noise**: CASA clean with natural weighting in 50-80 km/s bins; rms from moment 0 maps made with immoments  
  > "we used the CASA task "immoments" to construct moment 0 maps by collapsing along the channels with CO detection" (3 Observations and Data analysis)
   - software: CASA
   - parameter: 3-sigma upper limits over 320 km/s for non-detections  
  > "represents a 3-$\sigma$ upper limit calculated from sensitivity reached over a channel width of 320 km/s" (3 Observations and Data analysis)
   - fitting: _not stated_
   - validation: Stacking of non-detections showed no emission lines  
  > "Stacking of spectra from the sources with no detection revealed no emission lines, justifying our estimation of upper limits for these sources." (Molecular mass from CO)
3. **Extract spectra and fit CO line**: Circular aperture spectra fit with single Gaussian; flux cross-checked with uvmodelfit  
  > "We fit the CO(2-1) line using the IDL routine MPFIT (cite: markwardt12) using a single Gaussian component" (3 Observations and Data analysis)
   - software: MPFIT, CASA uvmodelfit
   - parameter: aperture radius ~1.5" (C1591, C92), ~1" (#226)  
  > "circular aperture with a radius of $\approx$1.5" in case of C1591 and C92 and $\approx$1" in case of #226" (3 Observations and Data analysis)
   - fitting: single Gaussian via MPFIT; uvmodelfit point source or elliptical Gaussian  
  > "using a point source or an elliptical Gaussian model which gives the centroid of the line emission and the integrated flux" (3 Observations and Data analysis)
   - validation: Image-plane and uv-plane fluxes agree within 1 sigma  
  > "they agree well at one-sigma error levels" (3 Observations and Data analysis)
4. **Compute CO luminosity and H2 mass**: L'CO from Solomon05 formula, excitation correction 0.8, MH2 = alpha_CO L'CO  
  > "In all cases, we assume an excitation correction of 0.8 to convert from $\mathrm{L_{CO(2-1)}}$ to $\mathrm{L_{CO(1-0)}}$" (Molecular mass from CO)
   - assumption: alpha_CO = 3.6; r21 correction 0.8; H0=70, Om=0.3, OL=0.7  
  > "we use an $\mathrm{\alpha_{CO}}$ value of 3.6" (Molecular mass from CO)
   - fitting: _not stated_
   - validation: Dynamical mass for C1591 gives alpha_CO 4.1+-1.6, consistent with 3.6  
  > "gives an $\alpha_{CO}$ value of 4.1$\pm$1.6 which is well within the value of 3.6 used here for all cases" (Molecular mass from CO)
5. **Dynamical gas mass for C1591**: imfit elliptical Gaussian for size; Mdyn = 5 sigma^2 r1/2 / G; subtract stars and 25% dark matter  
  > "Using CASA task *imfit*, we fit an elliptical Gaussian model to the CO(2-1) emission line integrated map over a velocity width of 880 km/s" (Molecular mass from CO)
   - software: CASA imfit
   - assumption: spherical symmetry; DM 25% of total  
  > "the dynamical mass for a spherically symmetric case is given by the following equation" (Molecular mass from CO)
   - fitting: _not stated_
   - validation: _not stated_
6. **Compare AGN and non-AGN relations**: survival two-sample test (survdiff); linear fits to AGN with slope fixed to MS slope, upper limits taken as detections, in L'CO-LIR, MH2-SFR, tdep-SFR, fgas-sSFR  
  > "While deriving the correlations for AGNs, we kept the slope of the linear function to be equal to that of the MS relations for ease of comparison with the non-AGN sample." (Observed relations for AGNs)
   - software: R survdiff (via python)
   - assumption: upper limits treated as detections in the fits (so fits are upper limits)  
  > "We also stress here that the derived line for AGNs is itself an upper limit since most of the data points used to fit this correlation are upper limits." (Observed relations for AGNs)
   - fitting: linear fit with fixed slope; priors/sampler not stated  
  > "While deriving the correlations for AGNs, we kept the slope of the linear function to be equal to that of the MS relations for ease of comparison with the non-AGN sample." (Observed relations for AGNs)
   - validation: p-value 0.008 from survival test  
  > "we obtain a $p$-value of 0.008 i.e. a \>99% probability that our AGN sample has a different distribution" (Observed relations for AGNs)

## Software

- **CASA** 4.2.2: imaging (clean), immoments, imfit, uvmodelfit  
  > "imaging for all the targets was done using CASA (version 4.2.2)" (3 Observations and Data analysis)
- **MPFIT** : Gaussian fits of CO line (IDL)  
  > "We fit the CO(2-1) line using the IDL routine MPFIT (cite: markwardt12)" (3 Observations and Data analysis)
- **R survdiff** : survival two-sample test  
  > "using R function *survdiff()* implemented in python" (Observed relations for AGNs)

## Numeric results

| quantity | value | uncertainty | units | step | quote |
|---|---|---|---|---|---|
| CO detections | 3 of 10 | not stated | dimensionless | 2 | We detect CO(2-1) emission in 3 out of the 10 targets observed with ALMA. |
| C1591 CO flux | 0.86 | 0.21 | Jy km/s | 3 | / C1591\* / 1.237 / 151.2 / 1.6x1.4 / 0.86$\pm$0.21 / 10.2$\pm$2.4 / 10.7$\pm$2.6 / 0.2$\pm$0.1 / |
| C92 CO flux | 1.01 | 0.13 | Jy km/s | 3 | / C92\* / 1.581 / 151.2 / 1.6x1.4 / 1.01$\pm$0.13 / 10.4$\pm$1.2 / 11.0$\pm$1.3 / 0.4$\pm$0.1 / |
| #226 CO flux | 0.29 | 0.11 | Jy km/s | 3 | / #226 / 1.389 / 151.2 / 0.8x0.5 / 0.29$\pm$0.11 /  9.8$\pm$3.7 / 10.4$\pm$3.9 / 0.2$\pm$0.2 / |
| C1591 CO FWHM | 616 | 71 | km/s | 3 | / C1591 /  -133.36$\pm$80  /   616$\pm$71    / 0.86$\pm$0.21 / |
| C1591 dynamical gas mass | 6.0e10 | 2.4e10 | Msun | 5 | we obtain a gas mass of $\mathrm{6.0\pm2.4\times 10^{10} M_{\odot}}$ for C1591 |
| alpha_CO from dynamical mass of C1591 | 4.1 | 1.6 | Msun (K km/s pc^2)^-1 | 5 | gives an $\alpha_{CO}$ value of 4.1$\pm$1.6 |
| AGN MH2-SFR intercept (slope 0.81) | 8.90 | 0.35 | dex | 6 | Log ~M_{H_{2}} [M_{\odot}] = 0.81\cdot Log ~SFR [M_{\odot}/yr] + (8.90\pm0.35) |
| AGN L'CO-LIR intercept (slope 0.81) | 0.25 | 0.35 | dex | 6 | Log ~L^{\prime}_{CO}[L{\odot}] = 0.81\cdot Log ~L_{IR}[L{\odot}] + (0.25\pm0.35) |
| Survival test p-value | 0.008 | not stated | dimensionless | 6 | we obtain a $p$-value of 0.008 |
| C1591 half-light radius | ~0.5 arcsec (4.15 kpc) | not stated | arcsec | 5 | we arrive at a half-light radius of $\sim$0.5$^{\prime\prime}$ ($\equiv$4.15 kpc) for C1591 |

## Qualitative findings

- AGN hosts show lower gas fractions and shorter depletion times than matched non-AGN MS galaxies; cannot distinguish negative from positive feedback  
  > "However with the current data we cannot distinguish between a positive or a negative feedback scenario" (Discussion)

## Claim tuples

- H: AGN hosts have different molecular gas content and star formation efficiency than matched non-AGN galaxies | E: ALMA CO(2-1) of 10 AGN hosts compared with a matched IRAM-PdBI non-AGN sample | R: 3 detections; AGN lie below MS relations; p=0.008 from survival test | F: AGN hosts have lower gas fractions (factor >~2) and lower depletion times | **supported**
- H: The CO-derived gas mass with alpha_CO=3.6 is reasonable for these AGN hosts | E: Dynamical mass for marginally resolved C1591 | R: Mgas=6.0+-2.4e10 Msun; alpha_CO=4.1+-1.6 | F: Consistent with alpha_CO=3.6 | **supported**
- H: Gas depletion is indirect evidence of AGN feedback | E: Compare with XID2028 and Tacconi13 AGN | R: Consistent trend for XID2028; Tacconi13 lower-luminosity AGN show no difference | F: Suggestive only; needs outflow measurements | **partially**

## Reasoning

- Why this data: _not stated_
- Why this method: CO(2-1) targeted to sample extended cool gas and avoid excitation uncertainty of higher-J lines  
  > "thereby avoiding the uncertain excitation corrections affecting higher-J transitions" (3 Observations and Data analysis)
- Alternative: Pannella09 MS parametrization used initially, replaced by Schreiber15, which reclassified two sources as starbursts  
  > "with the new parametrization of the MS from (cite: schreiber15), we arrive at a final sample of 8 objects on the MS and 2 starburst galaxies" (2 Target selection)
- How they decided it was enough: _not stated_
- Limitation (authors): alpha_CO is the biggest systematic uncertainty and may differ in AGN  
  > "$\mathrm{\alpha_{CO}}$ presents the biggest systematic uncertainty in molecular gas measurements using CO" (Molecular mass from CO)
- Limitation (authors): AGN fitted relations are upper limits since most points are upper limits  
  > "the derived line for AGNs is itself an upper limit since most of the data points used to fit this correlation are upper limits" (Observed relations for AGNs)
- Caveat (inferred, ours): Small sample with only 3 detections; fits mostly treat upper limits as detections, biasing results
- Caveat (inferred, ours): Comparison sample is heterogeneous, drawn from literature with different selections
- Caveat (inferred, ours): SFR and Mstar uncertain by a factor of 2
- Caveat (inferred, ours): Detections at 3-4 sigma are marginal
- Caveat (inferred, ours): Survival test p-value applies to all relations identically, which looks odd
- Caveat (inferred, ours): Assuming one alpha_CO for AGN and non-AGN

## Reproducibility

- Data public (paper): ALMA project code given; acknowledgement of ALMA data  
  > "This paper makes use of the following ALMA data: ADS/JAO.ALMA#2013.1.00171.S." (Acknowledgements)
- Products in archive: _not stated_
- Missing: clean parameters (threshold, niter, mask, cell size)
- Missing: comparison-sample values after recomputation
- Missing: survival test settings and fitting method with upper limits
- Data volume (inferred): ~10-30 GB (10 targets, short Band 3 scheduling blocks, 3 SBs)
- Score (inferred): 3/5, Public data and simple analysis, but imaging parameters and the comparison-sample and fitting details are missing.
- Rediscovery candidate: no, Recipe is incomplete (clean parameters, comparison sample, statistical details) and the results depend on literature compilations.

## Links

- Method: (cite: bonzini15) (SED fitting for SFR and Mstar)
- Method: (cite: solomon05) (L'CO formula)
- Companion: (cite: brusa15a) (Molecular gas and outflow in XID2028)
- Related: COSMOS
- Related: CDFS
- Related: PHIBBS

## Checks

```json
{
 "quotes": 78,
 "quotes_ok": 78,
 "quote_pass_rate": 1.0,
 "quotes_too_long": 0,
 "unsupported_facts": 0,
 "project_codes": 1,
 "codes_not_in_text": [],
 "codes_not_in_obscore": [],
 "obscore_codes_not_in_card": [],
 "codes_printed_but_missing": [],
 "numeric_results": 11,
 "numeric_problems": 0,
 "fill": {
  "facts": 90,
  "stated": 61,
  "rate": 0.678
 },
 "evidence_ok": true
}
```
