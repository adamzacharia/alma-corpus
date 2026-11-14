# Big Three Dragons: A z = 7.15 Lyman-break galaxy detected in [O III] 88 μm, [C II] 158 μm, and dust continuum with ALMA

`2019PASJ...71...71H` | Publications of the Astronomical Society of Japan 2019 | first author: Hashimoto, Takuya | arXiv: 1806.00486 | DOI: 10.1093/pasj/psz049

Card schema 1.0 | model claude-sonnet-5-5 | depth full | type observational_alma_primary

## Science

- Fields: high_z_galaxies
- Question: What are the kinematic, dust and ISM properties of the z=7.15 LBG B14-65666 from resolved [OIII] 88um, [CII] 158um and dust continuum, and is it a merger?  
  > "we argue that B14-65666 is a starburst galaxy induced by a major-merger." (abstract)
- Target **B14-65666**: coordinates RA 10:01:40.69, Dec +01:54:52.42 (total)  
  > "| R.A. | 10:01:40.69 | 10:01:40.70 | 10:01:40.67 |" (Table 3); "The size and PA values of [Cii] and [Oiii] are consistent with each other." (3.1 Measurements for the Whole System); z/distance z_sys = 7.1521 ± 0.0003  
  > "| R.A. | 10:01:40.69 | 10:01:40.70 | 10:01:40.67 |" (Table 3); "The size and PA values of [Cii] and [Oiii] are consistent with each other." (3.1 Measurements for the Whole System); distance from S/N-weighted mean of [CII] and [OIII] redshifts measured in this paper  
  > "| R.A. | 10:01:40.69 | 10:01:40.70 | 10:01:40.67 |" (Table 3); "The size and PA values of [Cii] and [Oiii] are consistent with each other." (3.1 Measurements for the Whole System)

## Data provenance

- ALMA projects: 2016.1.00954.S, 2017.1.00190.S
- bands: Band 6 (Cycle 4) and Band 8 (Cycles 4+5)  
  > "with beam size of $\approx 0''.3 \times 0''.2$ ($0''.3 \times 0''.3$) in Band 6 (Band 8)." (Introduction)
- frequencies and spectral setup: Band 6: four SPWs of 1.875 GHz in FDM, two at 7.813 MHz resolution for the line, two at 31.25 MHz for continuum; Band 8 same strategy  
  > "We used four spectral windows (SPWs) with 1.875 GHz bandwidths in the Frequency Division Mode (FDM), totaling the band width of 7.5 GHz." (2.1 ALMA Band 6 Observations); "The observation strategy was the same as that used in Band 6." (2.2 ALMA Band 8 Observations)
- continuum bandwidth: _not stated_
- arrays: _not stated_
- configurations: C40-6 (Band 6); C40-4 and C43-3 (Band 8)  
  > "The antenna configuration was C40-4 (C43-3) for the Cycle 4 (5) observations" (2.2 ALMA Band 8 Observations)
- baselines: 15-2647 m  
  > "| 2017-07-09 | $16 - 2647$ | 40 | 218.78, 216.98, 232.66, 234.48 | 37.80 | 0.45 |  |" (Table 1)
- angular resolution: Band 6 natural 0.29x0.23 arcsec; Briggs 0.23x0.12; Band 8 natural 0.39x0.37  
  > "| Band 6 (natural) |          9.5          |     $0.29\times0.23$     | $-60$  |" (Table 2)
- max recoverable scale: _not stated_
- sensitivity: continuum rms 9.5 (B6 natural), 11.0 (B6 Briggs), 29.4 (B8) uJy/beam  
  > "| Band 8 (natural) |         29.4          |     $0.39\times0.37$     | $+62$  |" (Table 2)
- time on source: 114 min (Band 6); 282 min (Band 8)  
  > "the on-source exposure times was 114 minutes" (2.1 ALMA Band 6 Observations); "the total on-source exposure times was 282 minutes" (2.2 ALMA Band 8 Observations)
- observing dates: _not stated_
- pi or archival as stated: _not stated_
- Line: [CII] 158 um (1900.5369 GHz)
- Line: [OIII] 88 um (3393.006244 GHz)
- Other facility **HST WFC3 F140W**: rest-UV two-clump image for comparison with ALMA, astrometrically recalibrated with Gaia/SDSS catalogs  
  > "we compare the spatial position of B14-65666 in ALMA data with that in the HST F140W band image data (PI: R.A.A. Bowler)." (Appendix 1)
- Other facility **UltraVISTA and Spitzer/IRAC**: Y,J,H,K and IRAC 3.6/4.5 um photometry for SED fitting  
  > "We use the $Y$, $J$, $H$, and $K$ band data taken by UltraVISTA ((cite: bowler2014)) and the deep *Spitzer*/IRAC 3.6 and 4.5 $\mu$m data ((cite: bowler2017))." (6 SED fit)
- Other facility **Subaru/FOCAS**: Lya spectrum used to remeasure z_Lya  
  > "We have remeasured $z_{\rm Ly\alpha}$ in the spectrum of (cite: furusawa2016)" (7 Lya velocity offset)
- External data: Lya spectrum of B14-65666  
  > "We have remeasured $z_{\rm Ly\alpha}$ in the spectrum of (cite: furusawa2016)" (7 Lya velocity offset) [from (cite: furusawa2016)]
- External data: UV slope beta = -1.85 for B14-65666  
  > "We adopt $\beta = -1.85^{+0.54}_{-0.53}$ in (cite: bowler2018) calculated with updated $J$- and $H$-band photometry values." (5.1) [from (cite: bowler2018)]
- External data: Compilation of literature Lya velocity offsets, MUV, EW and [CII] luminosities at z~6-8  
  > "We summarize these literature sample at $z\approx6-8$ in Table [\[tab:compilation\]](#tab:compilation)." (7) [from (cite: erb2014; nakajima2018) and others in Table 7]

## Processing

### Calibration

- pipeline or manual: CASA pipeline  
  > "The data were reduced and calibrated using the Common Astronomy Software Application (CASA; (cite: McMullin2007)) pipeline version 4.7.2." (2.1 ALMA Band 6 Observations)
- casa version: _not stated_
- pipeline version: Band 6: 4.7.2; Band 8: 4.7.0 (Cycle 4) and 5.1.1 (Cycle 5)  
  > "first reduced and calibrated with the CASA pipeline versions 4.7.0 and 5.1.1, respectively" (2.2 ALMA Band 8 Observations)
- archive products used as is: _not stated_
- flux calibrator: J1058+0133 and J0854+2006 (Band 6)  
  > "two quasars, J1058+0133 and J0854+2006, were used for flux calibrations" (2.1 ALMA Band 6 Observations)
- flux scale uncertainty: <~10%  
  > "The flux calibration uncertainty was estimated to be $\lesssim$ 10%." (2.1 ALMA Band 6 Observations)
- self calibration: _not stated_

### Imaging

- task: CLEAN task  
  > "Using the `CLEAN` task, we produced two images and cubes with different weighting" (2.1 ALMA Band 6 Observations)
- deconvolver: _not stated_
- weighting robust: Band 6: natural and Briggs robust 0.3; Band 8: natural  
  > "the Briggs weighting with the robust parameter of 0.3 to investigate morphological properties" (2.1 ALMA Band 6 Observations)
- uv taper: _not stated_
- cell size: _not stated_
- image size: _not stated_
- masking: _not stated_
- multiscale scales: _not stated_
- continuum subtraction: uvcontsub using off-line channels; continuum image from collapsing all off-line channels  
  > "we subtracted continuum using the off-line channels in the line cube with the CASA task `uvcontsub`." (2.1 ALMA Band 6 Observations)
- line free channels: _not stated_
- primary beam correction: _not stated_
- array combination: Cycle 4 and 5 Band 8 data combined with concat  
  > "combined into a single measurement set with the CASA task `concat`" (2.2 ALMA Band 8 Observations)
- smoothing: Channel binning: 3 (Band 6) and 6 (Band 8) native channels, ~30 (33) km/s  
  > "by binning three (six) native channels, resulting in a velocity resolution of $\approx 30 \ (33)$ km s$^{-1}$" (3.1)
- final beam: _not stated_
- final rms: _not stated_

### Inherited from earlier work

- Clump decomposition using velocity information  
  > "we decompose the [Cii] and [Oiii] emission into the two clumps using velocity information following (cite: matthee2017) and (cite: carniani2018b)." (3.2) [from (cite: matthee2017); (cite: carniani2018b)]
- Fixed-beta dust temperature estimation  
  > "Following analyses of (cite: knudsen2017), we attempt to estimate $T_{\rm d}$ with fixed $\beta_{\rm d}$ values." (4 Dust) [from (cite: knudsen2017)]
- SED fitting code and procedure  
  > "The SED fitting code used in this study is the same as that used in (cite: hashimoto2018a) and (cite: tamura2018)." (6 SED fit) [from (cite: mawatari2016); (cite: hashimoto2018a); (cite: tamura2018)]
- Beta from two photometric points  
  > "we uniformly derive $\beta$ from two photometry values following the equation (1) of (cite: ono2010b)." (5.1) [from (cite: ono2010b)]

### Not stated but needed to reproduce (our reading)

- Line-free channel ranges used for continuum and uvcontsub
- Image size, cell size, clean threshold, masks and number of iterations
- Band 8 Briggs/robust settings (natural only stated)
- Exact imfit regions and starting parameters
- Exact channel ranges for the Gaussian spectral fits and spectral extraction apertures
- Details of the CMB-corrected modified blackbody fit (fit method, T_d uncertainties per clump)
- Whether the QA2 archive products were used as delivered or re-calibrated manually
- SED fitting model grid details (in cited Mawatari 2016)

## Analysis recipe

1. **Calibrate and image ALMA data**: CASA pipeline calibration, concat for Band 8, CLEAN imaging (natural and Briggs 0.3), uvcontsub  
  > "Using the `CLEAN` task, we produced two images and cubes with different weighting" (2.1 ALMA Band 6 Observations)
   - software: CASA, CLEAN, uvcontsub, concat
   - parameter: robust = 0.3 for Briggs images  
  > "the Briggs weighting with the robust parameter of 0.3 to investigate morphological properties" (2.1 ALMA Band 6 Observations)
   - fitting: _not stated_
   - validation: _not stated_
2. **Measure line fluxes, sizes, redshifts, FWHM and luminosities**: Velocity-integrated maps over ~600 km/s; 2D Gaussian fits with imfit; Gaussian spectral fits; clump decomposition by velocity ranges; L_line from Carilli & Walter relation  
  > "We spatially integrate the image with the CASA task `imfit` assuming a 2D Gaussian profile for the velocity-integrated intensity." (3.1)
   - software: CASA imfit, immoments
   - parameter: Clump velocity ranges [+8,+280] and [-353,-52] km/s relative to z_sys  
  > "extracted from the velocity range of [+8 km s$^{-1}$, +280 km s$^{-1}$] and [-353 km s$^{-1}$, -52 km s$^{-1}$]" (3.2)
   - assumption: Cosmology Om=0.272, H0=70.4  
  > "$\Omega_{\small m} = 0.272$, $\Omega_{\small b} = 0.045$, $\Omega_{\small \Lambda} = 0.728$ and $H_{\small 0} = 70.4$ km s$^{-1}$ Mpc$^{-1}$" (Introduction)
   - fitting: Gaussian line profile fits to spectra from >3 sigma regions  
  > "Applying a Gaussian line profile and the rest-frame [Cii] ([Oiii]) frequency[^3] of 1900.5369 (3393.006244) GHz" (3.1)
   - validation: [CII] and [OIII] redshifts consistent within ~1 sigma; clump centroids match HST UV positions  
  > "The two redshift and FWHM values are consistent within $\approx 1\sigma$ uncertainties." (3.1)
3. **Dynamical mass**: Virial estimate M_dyn = C r_1/2 sigma^2 / G with C = 6.7, r_1/2 from major semi-axis of 2D Gaussian  
  > "Because we do not see a clear velocity field in each clump (Figure [3](#fig:velocity_map)), we use $C =$ 6.7." (3.3)
   - assumption: Uncertain at least by factor of three due to C; virial theorem may not apply  
  > "Note that our dynamical mass estimate is uncertain at least by a factor of three due to the uncertainty in $C$." (3.3)
   - fitting: _not stated_
   - validation: _not stated_
4. **Dust continuum flux, T_d, L_TIR and M_d**: imfit two-component Gaussians at fixed clump positions; modified blackbody with CMB correction at fixed beta_d (1.5, 1.75, 2.0); L_TIR over 8-1000 um; dust mass with kappa0 = 10 cm2/g at 250 um  
  > "we obtain the best-fit $T_{\rm d}$ values of 61 K, 54 K, and 48 K for $\beta_{\rm d}=$ 1.5, 1.75, and 2.0, respectively" (4 Dust)
   - software: CASA imfit
   - assumption: kappa0 = 10 cm2 g-1 at 250 um (Hildebrand 1983); using Dunne 2000 doubles M_d  
  > "where $\kappa_{0} = 10$ cm$^{2}$ g$^{-1}$ at $250$ $\mu$m ((cite: hildebrand1983))" (4 Dust)
   - assumption: Clumps assumed to have same T_d, beta_d as whole system  
  > "we assume the same combinations of $\beta_{\rm d}$ and $T_{\rm d}$ as in the whole system" (4 Dust)
   - fitting: best-fit T_d from two flux densities; 1 sigma ~10 K  
  > "where the $1\sigma$ temperature uncertainty is about 10 K for each case" (4 Dust)
   - validation: S163 consistent with Bowler et al. 158 um flux of 168±56 uJy  
  > "well consistent with the flux density at 158 $\mu$m presented by (cite: bowler2018), $168\pm56$ $\mu$Jy" (4 Dust)
5. **IRX-beta and [OIII]/[CII] vs L_bol comparison with literature**: Uniform beta and L_UV for 11 z>6.5 galaxies, L_TIR assuming T_d = 50 K, beta_d = 1.5; compared to Calzetti and SMC curves (intrinsic beta -2.2)  
  > "To obtain $L_{\rm TIR}$ of the literature sample, we have assumed $T_{\rm d}$ $=50$ K and $\beta_{\rm d} = 1.5$." (5.1)
   - assumption: T_d = 50 K, beta_d = 1.5 for literature sample  
  > "To obtain $L_{\rm TIR}$ of the literature sample, we have assumed $T_{\rm d}$ $=50$ K and $\beta_{\rm d} = 1.5$." (5.1)
   - fitting: _not stated_
   - validation: _not stated_
6. **SED fitting**: GALAXEV BC03 with nebular emission, Calzetti law, Chabrier IMF, constant SFH, z fixed 7.1520, [OIII] flux and dust continuum included; least chi2 of Sawicki 2012; Monte Carlo N=300 errors  
  > "we use the least $\chi^{2}$ formula of (cite: sawicki2012) including an analytic treatment of upper limits for non-detections." (6 SED fit)
   - software: KENSFIT, GALAXEV
   - assumption: Constant SFH; Calzetti attenuation same for stellar and nebular; Chabrier IMF 0.1-100 Msun  
  > "For simplicity, we assume a constant star formation history (SFH)." (6 SED fit)
   - fitting: least chi2 with Monte Carlo uncertainties (N=300)  
  > "Uncertainties on the parameters are estimated based on a Monte Carlo technique ($N=300$)." (6 SED fit)
   - validation: Compared dust mass vs SN yield and M_dyn vs M_*  
  > "To test the validity of our SED-fit results, we examine if the derived stellar and dust masses can be explained in a consistent manner." (6 SED fit)
7. **Lya velocity offset and correlations**: Gaussian peak of Lya in FOCAS spectrum; dv = c(zLya - zsys)/(1+zsys); Spearman rank tests on 17-galaxy z~6-8 compilation  
  > "To evaluate the significance of the relation, we perform Spearman rank correlation tests." (7)
   - parameter: vacuum rest wavelength 1215.67 A; systematic ±100 km/s  
  > "we add a systematic uncertainty of $\pm 100$ km s$^{-1}$" (7)
   - fitting: Gaussian fit to Lya  
  > "by reading the peak wavelength of a Gaussian fit to the line" (7)
   - validation: _not stated_

## Software

- **CASA** 4.7.2, 4.7.0, 5.1.1 (pipeline); 4.5.1 for re-analysis of Bowler data: pipeline calibration, CLEAN imaging, uvcontsub, concat, imfit, immoments  
  > "pipeline version 4.7.2" (2.1 ALMA Band 6 Observations)
- **IRAF** : ccmap and ccsetwcs for HST astrometry recalibration  
  > "we have performed `IRAF` tasks `ccmap` and `ccsetwcs` to calibrate astrometry." (Appendix 1)
- **KENSFIT** : SED fitting code (linked via Mawatari website)  
  > "we refer the reader to (cite: mawatari2016) and the relevant link [^8]." (6 SED fit)
- **CLOUDY** : photoionization models mentioned for prior work (not run here)  
  > "photoionization models of `CLOUDY` ((cite: ferland2013))" (Introduction)

## Numeric results

| quantity | value | uncertainty | units | step | quote |
|---|---|---|---|---|---|
| z_sys (whole system) | 7.1521 | 0.0003 | dimensionless | 2 | / $z_{\rm sys.}$ $^{a}$ / $7.1521\pm0.0003$ / $7.1530\pm0.0003$ / $7.1482\pm0.0003$ / |
| [OIII] luminosity (total) | 34.4e8 | 4.1e8 | Lsun | 2 | We obtain $(11.0\pm1.4) \times 10^{8}$ $L_{\rm \odot}$ and $(34.4\pm4.1) \times 10^{8}$ $L_{\rm \odot}$ for the [Cii] and [Oiii] luminosity |
| [CII] luminosity (total) | 11.0e8 | 1.4e8 | Lsun | 2 | We obtain $(11.0\pm1.4) \times 10^{8}$ $L_{\rm \odot}$ and $(34.4\pm4.1) \times 10^{8}$ $L_{\rm \odot}$ for the [Cii] and [Oiii] luminosity |
| [OIII]/[CII] luminosity ratio (total) | 3.1 | 0.6 | dimensionless | 2 | the line luminosity ratio is [Oiii]/[Cii] $= 3.1\pm0.6$, $3.5\pm0.8$, $2.7\pm0.6$ |
| Clump velocity offset | 177 | 16 | km/s | 2 | the velocity offset of the two clumps is $177\pm16$ km s$^{-1}$ |
| S_nu 163 um (total) | 130 | 25 | uJy | 4 | $S_{\nu, 163\mu m} = 130 \pm 25$ $\mu$Jy and $S_{\nu, 90\mu m} = 470 \pm 128$ $\mu$Jy |
| S_nu 90 um (total) | 470 | 128 | uJy | 4 | $S_{\nu, 163\mu m} = 130 \pm 25$ $\mu$Jy and $S_{\nu, 90\mu m} = 470 \pm 128$ $\mu$Jy |
| T_d (beta_d = 1.5, 1.75, 2.0) | 61, 54, 48 | ~10 K | K | 4 | we obtain the best-fit $T_{\rm d}$ values of 61 K, 54 K, and 48 K for $\beta_{\rm d}=$ 1.5, 1.75, and 2.0 |
| L_TIR (total) | ~1e12 | not stated | Lsun | 4 | We obtain $L_{\rm TIR}$ $\approx 1 \times 10^{12}$, $3 \times 10^{11}$, and $7 \times 10^{11}$ $L_{\rm \odot}$ |
| M_dyn (total) | 8.8e10 | 1.9e10 | Msun | 3 | we obtain the total dynamical mass of ($8.8\pm1.9) \times 10^{10}$ $M_{\rm \odot}$ |
| IRX (fiducial) | 0.5 | +0.3/-0.1 | dimensionless | 5 | Therefore, we adopt IRX $=0.5^{+0.3}_{-0.1}$ as a fiducial value. |
| Stellar mass | 7.7e8 | +1.0/-0.7 e8 | Msun | 6 | $M_{\rm *} = 7.7^{+1.0}_{-0.7} \times 10^{8}$ $M_{\rm \odot}$ |
| SFR | 200 | +82/-38 | Msun/yr | 6 | a very high current SFR, $200^{+82}_{-38}$ $M_{\rm \odot}$ yr$^{-1}$ |
| sSFR | 260 | +119/-57 | Gyr^-1 | 6 | The sSFR of $260^{+119}_{-57}$ Gyr$^{-1}$ |
| Lya velocity offset | 772 | ±45 (stat) ±100 (sys) | km/s | 7 | Hereafter we adopt $\Delta v_{\rm Ly\alpha}$ $= 772\pm45\pm100$ km s$^{-1}$. |

## Qualitative findings

- [CII] and [OIII] decompose into two clumps matching the HST UV clumps, separated by ~200 km/s, with a non-smooth velocity field, suggesting a merger.  
  > "These results indicate that B14-65666 is a merger system, as first claimed by (cite: bowler2017)" (3.2)
- Five dust-detected z>6.5 LBGs are consistent with the Calzetti curve; no strong evidence for SMC-like attenuation.  
  > "there is no strong evidence for a steep (i.e., SMC-like) attenuation curve at least for the five LBGs detected in dust." (5.1)

## Claim tuples

- H: Is B14-65666 a merger of two clumps? | E: Decomposed [CII] and [OIII] by velocity; compared with HST UV clumps; built moment-1 maps | R: Two clumps with ~177-200 km/s offset, consistent with UV positions, comparable luminosities | F: B14-65666 is a major-merger-induced starburst | **supported**
- H: What are the dust temperature and TIR luminosity with two continuum bands? | E: Fit modified blackbody to 90 and 163 um flux densities for fixed beta_d | R: T_d ~ 48-61 K, L_TIR ~ 1e12 Lsun | F: High dust temperature and large L_TIR | **supported**
- H: Does Lya velocity offset correlate with MUV and [CII] luminosity at z~6-8? | E: Spearman tests on 17 galaxies | R: 4.5 sigma with MUV, 4.0 sigma with [CII] luminosity; weak with EW | F: Brighter galaxies have larger offsets, enhancing Lya visibility | **partially**

## Reasoning

- Why this data: _not stated_
- Why this method: Velocity decomposition of the lines is used to match HST clumps, following earlier work.  
  > "Motivated by these, we decompose the [Cii] and [Oiii] emission into the two clumps using velocity information" (3.2)
- Alternative: Rotating disk interpretation disfavoured because velocity field is not smooth.  
  > "The velocity field is not smooth, implying that the velocity field may not be due to a rotational disk" (3.2)
- How they decided it was enough: _not stated_
- Limitation (authors): M_dyn uncertain by at least a factor of three; virial theorem may not apply.  
  > "Furthermore, given the nature of merger in B14-65666, the virial theorem may not be applicable for the individual clumps" (3.3)
- Limitation (authors): Clump continuum fluxes may be contaminated by each other at current resolution.  
  > "it is possible that the continuum flux density of each clump is contaminated by the other clump." (4 Dust)
- Caveat (inferred, ours): T_d relies on only two continuum points with fixed beta_d; large degeneracy
- Caveat (inferred, ours): Clump decomposition by velocity windows is subjective
- Caveat (inferred, ours): Compilation for Lya offset correlation is heterogeneous with small N
- Caveat (inferred, ours): Constant SFH and very young age affect sSFR
- Caveat (inferred, ours): Unexplained 0.44 arcsec offset between the two Band 6 datasets

## Reproducibility

- Data public (paper): Archival ALMA project codes given; public status not explicit  
  > "ADS/JAO.ALMA#2015.1.00540.S, ADS/JAO.ALMA#2016.1.00954.S, and ADS/JAO.ALMA#2017.1.00190.S" (Acknowledgments)
- Products in archive: _not stated_
- Missing: Clean parameters (image size, cell, mask, threshold)
- Missing: Line-free channels
- Missing: Fit regions for imfit
- Missing: SED fit grid details
- Missing: Literature compilation values for Spearman tests are in tables but exact sample selection partly implicit
- Data volume (inferred): ~100-300 GB raw for 3 Band 6 + 7 Band 8 execution blocks
- Score (inferred): 3/5, Data and main steps are identifiable, with numeric results, but imaging parameters and the SED fit setup are partly unstated or inherited.
- Rediscovery candidate: yes, Archival data from two projects, numeric results (fluxes, redshifts, luminosities) in tables, and a reasonably described recipe.

## Links

- Method: (cite: mawatari2016) (SED fitting procedure)
- Method: (cite: carilli_walter2013) (line luminosity relation)
- Companion: (cite: bowler2018) (earlier ALMA Band 6 detection of dust in B14-65666)
- Companion: (cite: hashimoto2018a) (same team [OIII] detection at z=9.11)
- Related: 2015.1.00540.S (Bowler et al. Band 6 data)

## Checks

```json
{
 "quotes": 92,
 "quotes_ok": 92,
 "quote_pass_rate": 1.0,
 "quotes_too_long": 0,
 "unsupported_facts": 0,
 "project_codes": 2,
 "codes_not_in_text": [],
 "codes_not_in_obscore": [],
 "obscore_codes_not_in_card": [],
 "codes_printed_but_missing": [
  "2015.1.00540.S"
 ],
 "numeric_results": 15,
 "numeric_problems": 0,
 "fill": {
  "facts": 92,
  "stated": 64,
  "rate": 0.696
 },
 "evidence_ok": true
}
```
