# SERENADE. II. An ALMA Multiband Dust Continuum Analysis of 28 Galaxies at 5 &lt; z &lt; 8 and the Physical Origin of the Dust Temperature Evolution

`2024ApJ...971..161M` | The Astrophysical Journal 2024 | first author: Mitsuhashi, Ikki | arXiv: 2311.16857 | DOI: 10.3847/1538-4357/ad5675

Card schema 1.0 | model claude-sonnet-5-5 | depth full | type observational_alma_primary

## Science

- Fields: high_z_galaxies
- Question: What are the IRX-beta_UV relation, the dust-obscured SFR density, and the dust temperature (and its redshift evolution) of z~5-8 Lyman-break galaxies, from multi-band (Band 6/8) ALMA dust continuum?  
  > "In this paper, we examine the FIR property of galaxies at z ~ 6 with our new ALMA Band-6/8 observations toward 11 Lyman-Break Galaxies (LBGs) at z spec ~ 6." (1. INTRODUCTION)
- Target **SERENADE z~6 LBGs (14 with Band 6+8, plus others observed in one band)**: coordinates _not stated_; z/distance z = 5.8-6.3  
  > "redshifted [O iii] 88 µm and Lyα falling into ALMA Band-8 and ground-based optical telescopes, respectively (z = 5.8–6.3)" (2.1 SERENADE overview); distance from spectroscopic redshifts from literature / [C II], [O III] lines (Table 1)  
  > "redshifted [O iii] 88 µm and Lyα falling into ALMA Band-8 and ground-based optical telescopes, respectively (z = 5.8–6.3)" (2.1 SERENADE overview)
- Target **Archival z~5-7 LBGs (14 galaxies, e.g. HZ4, HZ6, HZ9, HZ10, A1689-zD1, REBELS-12/25/38)**: coordinates _not stated_; z/distance z ~ 5.3-7.3  
  > "four galaxies at z ~ 5 (Faisst et al. 2020a), and ten galaxies at z ~ 7" (2.2 Addtional 5 < z < 8 samples); distance from literature (Table 1)  
  > "four galaxies at z ~ 5 (Faisst et al. 2020a), and ten galaxies at z ~ 7" (2.2 Addtional 5 < z < 8 samples)

## Data provenance

- ALMA projects: 2022.1.00522.S, 2015.1.00540.S, 2015.1.01406.S, 2016.1.00954.S, 2017.1.00190.S, 2017.1.00508.S, 2017.1.00697.S, 2017.1.00775.S, 2019.1.01634.L, 2021.1.01297.S, 2021.1.00318.S
- bands: Band 6 and Band 8 (rest-frame ~158 and ~88 um continuum)  
  > "our new ALMA Band-6/8 observations toward 11 Lyman-Break Galaxies (LBGs)" (1. INTRODUCTION)
- frequencies and spectral setup: _not stated_
- continuum bandwidth: _not stated_
- arrays: _not stated_
- configurations: C43-1/2/3 (SERENADE Cycle 9)  
  > "Observations were conducted between October and December 2022 using the C43-1/2/3 configuration." (2.1 SERENADE overview)
- baselines: _not stated_
- angular resolution: _not stated_
- max recoverable scale: _not stated_
- sensitivity: _not stated_
- time on source: _not stated_
- observing dates: October-December 2022 (SERENADE)  
  > "Observations were conducted between October and December 2022 using the C43-1/2/3 configuration." (2.1 SERENADE overview)
- pi or archival as stated: SERENADE new program (PI Harikane); additional galaxies from public ALMA archive  
  > "We collect galaxies at 5 < z < 8 with both Band-6 and Band-8 observations publicly available in the ALMA science archive." (2.2 Addtional 5 < z < 8 samples)
- Line: [C II] 158 um (not stated)
- Line: [O III] 88 um (not stated)
- Other facility **HSC-SSP, COSMOS2020, VIKING/UKIDSS, HST and other UV/NIR photometric catalogs**: broad-band photometry for beta_UV and M_UV  
  > "Our calculations utilize broad-band photometry spanning a rest-frame wavelength range as large as 800–3000A depending on the data availability" (3.1 Measurement of β UV and M UV)
- External data: UV luminosity function at z~6 used for SFRD  
  > "Our starting point is the galaxy UV luminosity function presented in Harikane et al. (2022)." (4.2 SFR density at z ~ 6) [from Harikane et al. (2022)]
- External data: Faint-galaxy M_UV-beta_UV relation  
  > "The UV slope could be redder than the extrapolated relationship from Bouwens et al. (2014) (hereafter B14)" (3.2 M UV vs β UV relationship) [from Bouwens et al. (2014)]
- External data: Photometry and Lya EWs of archival and SERENADE galaxies (Table 1 references)  
  > "All of the utilized photometries, along with their references, are listed in Table 1." (Table 1) [from Table 1 references (e.g. Weaver et al. 2022; Aihara et al. 2022)]
- External data: Mass-metallicity evolution and gas depletion time used in the T_dust model  
  > "we assume a power-law dependence of d log(O/H)/dz = −0.11 with a z = 0 value of 12 + log(O/H) = 8.77 at M * = 10 10 M ⊙ (Sanders et al. 2021)" (5. DISCUSSION) [from Sanders et al. (2021); Tacconi et al. (2020)]

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

- task: CASA/tclean for continuum images; CASA/imfit for fluxes; imsmooth for stacking  
  > "Subsequently, we generate continuum images with CASA/tclean." (3.3 Dust continuum fluxes)
- deconvolver: _not stated_
- weighting robust: _not stated_
- uv taper: 0.25, 0.5, 1.0, 2.0, 3.0 arcsec plus natural weighting without taper  
  > "we reconstruct images with uv taper of 0.25′′, 0.5′′, 1.0′′, 2.0′′, and 3.0′′ in addition to the naturally-weighted image without tapering." (3.3 Dust continuum fluxes)
- cell size: _not stated_
- image size: _not stated_
- masking: _not stated_
- multiscale scales: _not stated_
- continuum subtraction: Line-masked: 3x line velocity dispersion for detections; ±0.8 GHz (±500 km/s) for non-detections  
  > "we exclude the frequencies at ±0.8 GHz (equivalent to ±500 km s −1 ) from the expected central frequency from their prior redshift" (3.3 Dust continuum fluxes)
- line free channels: _not stated_
- primary beam correction: _not stated_
- array combination: _not stated_
- smoothing: stacking images smoothed to round 2.0 arcsec beam with imsmooth after 1 arcsec taper  
  > "we construct continuum images with a round 2 ′′. 0 beam by applying CASA/imsmooth for the images with a prior 1 ′′ taper." (3.4 Stacking analysis)
- final beam: _not stated_
- final rms: RMS of pixels within FoV where primary beam response >0.5, in images without PB correction  
  > "Noise levels are estimated in the images without primary beam corrections as the root-mean-square (RMS) of pixel values within the Field-of-View (FoV) where the primary beam correction value exceeds 0.5." (3.3 Dust continuum fluxes)

### Inherited from earlier work

- Lya line brightness from literature or calculated following earlier methodology  
  > "The brightness of the Lyα line is obtained from the literature or calculated from spectra following the methodologies in Harikane et al. (2020b)." (3.1 Measurement of β UV and M UV) [from Harikane et al. (2020b)]
- CMB correction to the MBB  
  > "After considering these effects following da Cunha et al. (2013), the equation (2) becomes" (3.5 T dust and L IR estimation) [from da Cunha et al. (2013)]
- Upper-limit treatment in MBB fit  
  > "we adopt the methodology described in Sawicki (2012)" (3.5 T dust and L IR estimation) [from Sawicki (2012)]
- NIR photometry combination  
  > "we combine the photometries at NIR wavelengths with the i, z, and y -band photometry following Matsuoka et al. (2019)." (3.1 Measurement of β UV and M UV) [from Matsuoka et al. (2019)]
- SFR conversion factors  
  > "we derive the total (UV+IR) SFR from the UV and IR luminosities following the conversion factors in Madau & Dickinson (2014) with Chabrier (2003) IMF" (4.2 SFR density at z ~ 6) [from Madau & Dickinson (2014)]
- T_dust evolution analytic model  
  > "we calculate the T dust evolution by combining the analytical model presented in Sommovigo et al. (2022) with recent observational constraints" (5. DISCUSSION) [from Sommovigo et al. (2022)]

### Not stated but needed to reproduce (our reading)

- Exact CASA version and calibration/pipeline details for the archival and new data
- tclean parameters (cell, image size, deconvolver, niter, threshold, masking, robust)
- Which archival projects map to which of the 14 literature galaxies and exact spectral setups/sensitivities
- Specific taper choices used before imfit for each source
- MCMC settings (walkers, steps, convergence)
- Stacking details (pixel positions/weights per galaxy, error estimation)
- Details of the bootstrap for SFRD and the fobs-MUV fit
- Visibility-based analysis details (deferred to Mitsuhashi et al. in prep)

## Analysis recipe

1. **Measure beta_UV and M_UV**: Power-law fit f_lambda ∝ lambda^beta to broad-band photometry with truncation at 1216 A and Lya contribution; chi2 minimization  
  > "assuming a simple power-law spectral shape described by f λ ∝ λ β UV with a truncation at λ rest = 1216A" (3.1 Measurement of β UV and M UV)
   - parameter: grid ranges: normalization [-0.5,0.5] dex, beta_UV [-5,3]; M_UV at rest 1500 A  
  > "We fit model UV SEDs created with the logarithmic ranges of [-0.5, 0.5] for the normalization flux in the y -band and [-5, 3] for the UV slope β UV ." (3.1 Measurement of β UV and M UV)
   - fitting: Best fit at minimum chi2; 1 sigma at delta chi2 = 1  
  > "derived as the value showing the minimum χ 2 and the deviation at which ∆ χ 2 = 1" (3.1 Measurement of β UV and M UV)
   - validation: typical reduced chi2 = 3.0  
  > "We find a typical reduced χ 2 value is χ 2 ν = 3.0" (3.1 Measurement of β UV and M UV)
2. **Measure dust continuum flux densities**: Line-masked tclean continuum images with multiple tapers; imfit for sources detected in both bands, 1 arcsec taper peak for single-band detections, upper limits from natural images; detection at S/N>3.5  
  > "Galaxies with fiducial S/N > 3.5 in any band are considered as continuum detection." (3.3 Dust continuum fluxes)
   - software: CASA
   - parameter: peak within 0.5 arcsec radius of central position; highest S/N among images adopted  
  > "We obtain peak flux density within a 0.5 ′′ radius from each galaxy’s central position" (3.3 Dust continuum fluxes)
   - fitting: _not stated_
   - validation: Compared with UVMultifit visibility fits (Sersic n=1); consistent  
  > "we find that calculated fiducial fluxes, in any case, are consistent with those from the visibility analysis." (3.3 Dust continuum fluxes)
3. **Stack dust continuum in beta_UV bins**: Stack galaxies observed in both bands in two beta_UV bins with L_UV-based weights; measure flux as in step 2  
  > "galaxies in two distinct β UV bins of β UV = [ −3 , −1] and [ −1 , 1]" (3.4 Stacking analysis)
   - software: CASA
   - parameter: weight w_i = L_UV^mean / L_UV,i; two galaxies excluded  
  > "we exclude two galaxies (J020038021052 and J024801-033258)" (3.4 Stacking analysis)
   - fitting: _not stated_
   - validation: No major difference with weighted median  
  > "We find that there is no major difference when we use the weighted median instead of the weighted average." (3.4 Stacking analysis)
4. **Fit modified blackbody for T_dust, M_dust, L_IR**: Optically thin MBB with CMB correction fit by MCMC; upper limits treated per Sawicki (2012); L_IR over 8-1000 um  
  > "We use the Markov Chain Monte Carlo (MCMC) algorithm to fit the MBB profiles by utilizing the emcee library." (3.5 T dust and L IR estimation)
   - software: emcee
   - parameter: Priors: log-uniform log10(Mdust/Msun) in [4,10]; Tdust in [T_CMB,z,120] K; Gaussian beta_dust prior mean 1.8, sigma 0.5  
  > "we adopt a Gaussian prior with a mean value of ⟨β dust ⟩ = 1.8 and a standard deviation of σ β dust = 0.5" (3.5 T dust and L IR estimation)
   - assumption: kappa = kappa*(nu/nu*)^beta with [kappa*, nu*]=[10.41 cm^2/g, 1900 GHz]; T_dust=45 K assumed for unconstrained galaxies  
  > "[ κ ∗, ν ∗ ]=[10.41 cm −2 g −1, 1900 GHz]" (3.5 T dust and L IR estimation)
   - fitting: emcee MCMC; best fit and 1 sigma from modes with highest posterior density intervals  
  > "We compute best-fit values and 1 σ uncertainties from the modes with the highest posterior density intervals." (3.5 T dust and L IR estimation)
   - validation: Tested uniform beta_dust prior [1.5,2.5] and T_dust prior upper edge 150 K; no significant impact  
  > "there is no significant difference if we apply a uniform prior of β dust ∈ [1.5, 2.5]" (3.5 T dust and L IR estimation)
5. **Derive IRX-beta_UV, SFRD and obscured fraction**: Convert UV luminosity function via M_UV-beta_UV and IRX-beta_UV relations to UV+IR SFR, integrate to M_UV=-17; bootstrap uncertainties; alternative via f_obs-M_UV  
  > "We then integrate the SFR function with a range from M UV = −17 mag following previous studies" (4.2 SFR density at z ~ 6)
   - parameter: SFR_UV = 0.76e-28 L_UV; SFR_IR = 2.64e-44 L_IR  
  > "SFR UV = 0 _._ 76 _×_ 10 _[−]_ [28] _L_ UV (erg s _[−]_ [1] Hz _[−]_ [1] ) (5)


SFR IR = 2 _._ 64 _×_ 10 _[−]_ [44] _L_ IR (erg s _[−]_ [1] ) (6)" (4.2. SFR density at z ∼ 6)
   - assumption: Fudamoto et al. (2020a) IRX-beta relation fiducial; Chabrier IMF; for f_obs stacks T_dust=45 K, beta_dust=1.8  
  > "assuming an optically-thin MBB profile with T dust = 45 K and β dust = 1.8" (4.3 Obscured fraction of the star formation)
   - fitting: bootstrap  
  > "We estimate uncertainties using bootstrap techniques" (4.2 SFR density at z ~ 6)
   - validation: Compared alternative M_UV-beta_UV and IRX-beta_UV combinations (Table 3)  
  > "we also calculate the SFRD with the different combinations of the M UV – β UV and IRX- β UV relation." (4.2 SFR density at z ~ 6)
6. **Average T_dust at z~6-7 and model evolution**: Stack 22 galaxies observed in both bands and fit MBB; compare with analytic model of Sommovigo et al. (2022) using t_gas and metallicity evolution  
  > "resulting in a total of 22 galaxies for the stacking analysis." (4.4 T dust evolution)
   - software: emcee
   - parameter: M*=1e10 Msun, tau_eff=1.3, K1500=1.4e10, beta_dust=1.8, D_sun=1/162  
  > "Here we use τ eff = 1.3 to match the T dust observation at z = 0.5, 27.2 K" (5. DISCUSSION)
   - assumption: metallicity evolution dlog(O/H)/dz=-0.11 or none at z>3.3  
  > "we also compute the redshift evolution under the assumption of no metallicity evolution at z > 3.3" (5. DISCUSSION)
   - fitting: MBB with Gaussian beta prior as in step 4  
  > "estimate T dust and its uncertainty from MBB fitting with the Gaussian β dust prior" (4.4 T dust evolution)
   - validation: Median stack gives no major difference  
  > "There is no major difference in the resulting T dust when we use a median stacking instead of the average stacking." (4.4 T dust evolution)

## Software

- **CASA** : mstransform line masking, tclean imaging, imfit, imsmooth  
  > "we mask a frequency range that is three times wider than the line velocity dispersion using CASA/mstransform." (3.3 Dust continuum fluxes)
- **emcee** : MCMC fitting of MBB  
  > "We use the Markov Chain Monte Carlo (MCMC) algorithm to fit the MBB profiles by utilizing the emcee library." (3.5 T dust and L IR estimation)
- **UVMultifit** : visibility-based flux check  
  > "we also measure the fluxes from visibility data with UVMultifit assuming Sérsic index n = 1 just to check the flux recovery." (A. FLUX COMPARISON)

## Numeric results

| quantity | value | uncertainty | units | step | quote |
|---|---|---|---|---|---|
| Average T_dust of stacked z~6-7 galaxies | 40.9 | +10/-9.0 | K | 6 | The stacked result suggests that an average dust temperature is T dust = 40.9 +10 −9.0 K. |
| Dust-obscured fraction of SFRD at z~6 (IRX-beta route) | 31 | +8/-8 | % | 5 | contributes 31 +8 −8 % to the total star formation at z ~ 6. |
| Dust-obscured fraction via M_UV-f_obs | 15 | +17/-8 | % | 5 | comprises 15 +17 −8 % of total SFRD |
| M_UV-beta_UV relation | beta_UV = -(0.76±0.14)(M_UV+22) - (1.51±0.15) | ±0.14, ±0.15 | dimensionless | 1 | β UV = − (0.76 ± 0.14)( M UV + 22) − (1.51 ± 0.15) |
| Stack T_dust, beta_UV in [-3,-1] | 50.4 | +24/-9.5 | K | 4 | −3 < β UV < −1 0.21 ± 0.04 ≤ 0.63 - - - - 50.4 |
| Stack T_dust, beta_UV in [-1,1) | 26.0 | +14/-6.5 | K | 4 | −1 ≤ β UV < 1 0.36 ± 0.01 1.24 ± 0.03 - - - - 26.0 |
| Observed T_dust scatter at z=5-8 | 12 | not stated | K | 6 | The individual measurements have a large scatter of ∆ T dust ~ 12 K at z = 5–8 |

## Qualitative findings

- IRX-beta_UV at z~6 is shallower than Calzetti, Meurer and SMC relations and matches Fudamoto et al. (2020a) z~5.5  
  > "We find that our result from the stacking analysis supports a shallower IRX- β UV relation than the Calzetti (Calzetti et al. 2000) and Meurer (Meurer et al. 1999) relations." (4.1 β UV vs IRX relationship)
- T_dust results support linear (1+z) evolution rather than quadratic  
  > "Our results support the linear relation of ∝ (1+ z ) 1 (Schreiber et al. 2018) rather than the quadratic relation ∝ (1+ z ) 2 (Viero et al. 2022)." (4.4 T dust evolution)

## Claim tuples

- H: Is the IRX-beta_UV relation at z~6 shallower than at z~2-4? | E: Stacked Band 6 and 8 continuum in two beta_UV bins with MBB fits | R: Shallower than Calzetti/Meurer/SMC, ~1 dex lower than z~3 at beta_UV~0 | F: Shallow IRX-beta_UV at z~6, matching z~5.5 single-band results | **supported**
- H: How much of the SFRD at z~6 is dust-obscured? | E: Convert UV luminosity function using M_UV-beta_UV and IRX-beta_UV (and f_obs-M_UV) relations | R: 31% (IRX-beta route), 15% (f_obs route) | F: Limited contribution (~30%) of dust-obscured SF in UV-selected galaxies | **supported**
- H: Does T_dust increase gently with redshift to z~6-7? | E: Stacked MBB fit of 22 galaxies | R: T_dust = 40.9 +10/-9.0 K | F: Consistent with linear (1+z) evolution | **supported**
- H: Can the T_dust evolution and scatter be physically explained? | E: Analytic model of Sommovigo et al. (2022) with t_gas and metallicity evolution | R: ~0.6 dex increase in gas depletion time scale and ~0.4 dex metallicity decrease reproduce the trend; main-sequence and mass-metallicity scatter give ±12 K | F: Evolution and scatter explained by t_gas, metallicity and scatter around relations | **supported**

## Reasoning

- Why this data: _not stated_
- Why this method: Band 8 covers rest ~90 um near the dust peak at z~6, constraining T_dust  
  > "The ALMA Band-8, covering rest-frame ~ 90 µm dust continuum near the peak of the dust thermal emission at z ~ 6, enables us to constrain T dust ." (1. INTRODUCTION)
- Alternative: Optically thick MBB gives the same L_IR but higher T_dust; optically thin adopted  
  > "the resulting L IR does not change under the assumption of the optically thick MBB with λ 0 = 100 µm, whereas T dust becomes higher" (3.5 T dust and L IR estimation)
- How they decided it was enough: _not stated_
- Limitation (authors): Sample selection biases and limited NIR coverage make beta_UV uncertain; sample inhomogeneous  
  > "enlarging the sample size is imperative to draw robust conclusions." (3.2 M UV vs β UV relationship)
- Limitation (authors): beta_dust not constrained by data; some galaxies lack constraints  
  > "the sampling range of the FIR SED is not enough to constrain β dust" (3.5 T dust and L IR estimation)
- Caveat (inferred, ours): T_dust stack depends on assumed beta_dust prior and optically thin assumption
- Caveat (inferred, ours): Archival heterogeneity of data and resolution/flux recovery
- Caveat (inferred, ours): T_dust=45 K fixed for non-detections affects IRX and upper limits
- Caveat (inferred, ours): Stacking sample mixes lensed/selected galaxies with inhomogeneous selection
- Caveat (inferred, ours): The analytic model has tuned tau_eff and fixed assumptions

## Reproducibility

- Data public (paper): Galaxies with both bands publicly available in ALMA archive  
  > "We collect galaxies at 5 < z < 8 with both Band-6 and Band-8 observations publicly available in the ALMA science archive." (2.2 Addtional 5 < z < 8 samples)
- Products in archive: _not stated_
- Missing: CASA version and tclean parameters
- Missing: Per-source choice of method/taper
- Missing: MCMC settings
- Missing: Exact stacking implementation
- Missing: Visibility analysis (in prep)
- Data volume (inferred): Large: ~11 projects, multiple bands per galaxy; likely tens to hundreds of GB raw
- Score (inferred): 5/5, Data are public and the methods are described in reasonable detail, but imaging parameters and CASA versions are missing and the sample assembly from 11 projects is laborious.
- Rediscovery candidate: no, Recipe lacks imaging parameters and sample-to-project mapping, and heavy multi-project processing is needed.

## Links

- Method: Sawicki (2012) (treatment of upper limits in fits)
- Method: da Cunha et al. (2013) (CMB effect on MBB)
- Method: Sommovigo et al. (2022) (analytic T_dust model)
- Companion: Harikane et al. in prep (Paper I) (SERENADE emission-line data)
- Companion: Harikane et al. (2020b) (SERENADE pilot galaxies)
- Companion: Mitsuhashi et al. in prep (visibility-based analysis and REBELS f_obs)
- Related: SERENADE
- Related: REBELS
- Related: ALPINE
- Related: CRISTAL
- Related: HSC-SSP
- Related: SHELLQs

## Checks

```json
{
 "quotes": 85,
 "quotes_ok": 79,
 "quote_pass_rate": 0.929,
 "quotes_too_long": 0,
 "unsupported_facts": 0,
 "project_codes": 11,
 "codes_not_in_text": [],
 "codes_not_in_obscore": [],
 "obscore_codes_not_in_card": [],
 "codes_printed_but_missing": [],
 "numeric_results": 7,
 "numeric_problems": 0,
 "fill": {
  "facts": 92,
  "stated": 60,
  "rate": 0.652
 },
 "evidence_ok": false
}
```
