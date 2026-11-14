# Full of Orions: a 200-pc mapping of the interstellar medium in the redshift-3 lensed dusty star-forming galaxy SDP.81

`2020MNRAS.494.5542R` | Monthly Notices of the Royal Astronomical Society 2020 | first author: Rybak, Matus | arXiv: 1912.12538 | DOI: 10.1093/mnras/staa879

Card schema 1.0 | model claude-sonnet-5-5-claude-code | depth full | type observational_alma_primary

## Science

- Fields: high_z_galaxies, milky_way_ism
- Question: Map the ISM of the lensed z=3.042 DSFG SDP.81 at ~200 pc resolution: spatial distribution of FIR continuum, CO and [C II]; gas cooling budget; PDR conditions (FUV field, density, surface temperature) and the origin of the [C II]/FIR deficit  
  > "we use high-resolution, multi-Band ALMA observations to map the ISM properties in the strongly lensed" (1 Introduction); "How are different tracers of ISM - FIR continuum, CO and \[C ii\] emission spatially distributed?" (1 Introduction)
- Target **SDP.81 (H-ATLAS J090311.6+003906)**: coordinates J2000 09:03:11.6 +00:39:06  
  > "SDP.81 (J2000 09:03:11.6 +00:39:06;" (2.1 Target description); "Adopting the spectroscopic redshift of $z=3.042$ (cite: alma2015), this translates to a luminosity distance of 26480 Mpc" (1 Introduction); "luminosity distance of 26480 Mpc, and an angular scale of 1 arcsec = 7.857 kpc" (1 Introduction); z/distance z = 3.042 (lens at z_L = 0.299); luminosity distance 26480 Mpc; 1 arcsec = 7.857 kpc  
  > "SDP.81 (J2000 09:03:11.6 +00:39:06;" (2.1 Target description); "Adopting the spectroscopic redshift of $z=3.042$ (cite: alma2015), this translates to a luminosity distance of 26480 Mpc" (1 Introduction); "luminosity distance of 26480 Mpc, and an angular scale of 1 arcsec = 7.857 kpc" (1 Introduction); distance from spectroscopic redshift from alma2015; flat LambdaCDM Planck2015 cosmology  
  > "SDP.81 (J2000 09:03:11.6 +00:39:06;" (2.1 Target description); "Adopting the spectroscopic redshift of $z=3.042$ (cite: alma2015), this translates to a luminosity distance of 26480 Mpc" (1 Introduction); "luminosity distance of 26480 Mpc, and an angular scale of 1 arcsec = 7.857 kpc" (1 Introduction)

## Data provenance

- ALMA projects: 2016.1.00633.S, 2016.1.01093.S, 2011.0.00016.SV
- bands: Band 3 (CO(3-2), Cycle 5); Band 8 ([C II], Cycle 4); 2014 Long Baseline Campaign Bands 4, 6, 7  
  > "The observations were carried out on 2017 September 9 in ALMA Band 3." (2.2 ALMA Band 3 observations); "This confirms that ALMA Band 8 observations are not resolving out extended" (3.1.2 ALMA Band 8); "The observations comprised of 5.9, 4.4 and 5.6 hours on-source in Bands 4, 6 and 7 respectively, taken in October 2014." (2.4 ALMA 2014 Long Baseline Campaign observations)
- frequencies and spectral setup: Band 3: four SPWs at 97.730, 99.626, 85.813, 87.614 GHz (two line SPWs with 1920 channels of 976.6 kHz, 1.875 GHz each; two continuum SPWs, 15.625 MHz channels). Band 8: four SPWs at 468.35, 458.24, 456.35, 470.24 GHz (SPW 3 split into 240 7.812-kHz channels, 1.875 GHz). LBC: 7.5 GHz bandwidth per band  
  > "The frequency setup consisted of four spectral windows (SPWs), centered at 97.730, 99.626, 85.813 and 87.614 GHz, respectively." (2.2 ALMA Band 3 observations); "The frequency setup consisted of four SPWs, centered on 468.35, 458.24, 456.35 and 470.24 GHz, respectively." (2.3 ALMA Band 8 observations); "while SPW 3 was split into 240 7.812-kHz-wide channels, for a total bandwidth of 1.875 GHz." (2.3 ALMA Band 8 observations)
- continuum bandwidth: 2.0 GHz per continuum SPW (Band 3 and Band 8)  
  > "The other two SPWs were configured in the continuum mode (channel width 15.625 MHz), with a bandwidth of 2.0 GHz per SPW." (2.2 ALMA Band 3 observations); "SPWs 0–2 were configured in a continuum mode with a bandwidth of 2.0 GHz per SPW" (2.3 ALMA Band 8 observations)
- arrays: 12-m array: 40 antennas (Band 3), 44 antennas (Band 8), 22-36 antennas (LBC)  
  > "The array configuration consisted of 40 12-meter antennas" (2.2 ALMA Band 3 observations); "with 44 12-meter antennas with baselines extending from 13 to 850 m" (2.3 ALMA Band 8 observations); "The antenna configuration consisted of 22-36 12-meter antennas" (2.4 ALMA 2014 Long Baseline Campaign observations)
- configurations: _not stated_
- baselines: Band 3: 39 to 7550 m; Band 8: 13 to 850 m; LBC ~15 m to ~15 km; all datasets cut to uv-distance <= 1 Mlambda  
  > "with baselines extending from 39 to 7550 m" (2.2 ALMA Band 3 observations); "baselines extending from 13 to 850 m" (2.3 ALMA Band 8 observations); "This resulted in restricting the CO line analysis to baselines $\leq1$ M$\lambda$; here we adopt this $uv$-distance cut for all the ALMA datasets." (2.4 ALMA 2014 Long Baseline Campaign observations)
- angular resolution: LBC synthesized beam ~30 mas (Band 7) to ~55 mas (Band 4); Band 3 original request 0.2 arcsec  
  > "resulting in a synthesized beam size of $\sim30$ mas for Band 7 to $\sim$55 mas for Band 4 (Briggs weighing, robust = 1)" (2.4 ALMA 2014 Long Baseline Campaign observations); "While the original project requested a total of 4 hours on-source with a resolution of 0.2 arcsec" (2.2 ALMA Band 3 observations)
- max recoverable scale: Angular scales covered by the baselines: ~0.10-19 arcsec (Band 3), ~0.16-10.5 arcsec (Band 8); not stated as MRS  
  > "covering angular scales between $\sim$0.10 and 19 arcsec" (2.2 ALMA Band 3 observations); "corresponding to angular scales between $\sim$0.16 and 10.5 arcsec" (2.3 ALMA Band 8 observations)
- sensitivity: Band 3 continuum rms 10 uJy/beam (natural weighting)  
  > "The Cleaned Band 3 continuum map has an rms noise of 10 $\mu$Jy beam$^{-1}$ (natural weighting)." (3.1.1 ALMA Band 3)
- time on source: Band 3 ~45 min (4 h requested); LBC 5.9 h (Band 4), 4.4 h (Band 6), 5.6 h (Band 7)  
  > "the total observations amount to only $\sim$45 min." (2.2 ALMA Band 3 observations); "The observations comprised of 5.9, 4.4 and 5.6 hours on-source in Bands 4, 6 and 7 respectively" (2.4 ALMA 2014 Long Baseline Campaign observations)
- observing dates: Band 3: 2017 September 9; Band 8: 2016 November 14; LBC: October 2014  
  > "The observations were carried out on 2017 September 9 in ALMA Band 3." (2.2 ALMA Band 3 observations); "The observations were carried out on 2016 November 14 with 44 12-meter antennas" (2.3 ALMA Band 8 observations); "taken in October 2014" (2.4 ALMA 2014 Long Baseline Campaign observations)
- pi or archival as stated: _not stated_
- Line: [C II] not stated (not stated)
- Line: CO 3-2 (not stated)
- Line: CO 10-9 (not stated)
- Line: CO 5-4 and 8-7 (from R15b, LBC data) (not stated)
- Other facility **HST**: Near-infrared imaging of SDP.81 (ancillary)  
  > "Ancillary observations include HST near infra-red imaging" (2.1 Target description)
- Other facility **Herschel (PACS/SPIRE)**: FIR photometry and FTS fine-structure spectroscopy ([O I], [N II] limits) from Zhang et al. 2018 / Valtchanov et al. 2011  
  > "FIR spectroscopy (cite: Valtchanov2011; Zhang2018b), and radio/mm-wave low-resolution spectroscopy and imaging (cite: Valtchanov2011; Lupu2012)" (2.1 Target description)
- Other facility **VLA and CARMA**: Archival CO(1-0) (VLA) and CO(7-6) (CARMA) line luminosities from Valtchanov et al. 2011  
  > "archival observations of the CO(1–0) (VLA; (cite: Valtchanov2011)) and CO(7–6) (CARMA, (cite: Valtchanov2011)) lines" (4.2 Emission lines)
- Other facility **Z-Spec on the Caltech Submillimeter Observatory**: Upper limit on CO(9-8) from Lupu et al. 2012  
  > "an upper limit[^4] on the CO(9–8) lines (Z-Spec on the Caltech Submillimeter Observatory, (cite: Lupu2012))" (4.2 Emission lines)
- Other facility **XMM-Newton**: 0.5-8 keV flux at the position of SDP.81 (Ranalli et al. 2015), used to test AGN contribution  
  > "XMM observations of the SDP.81 field detect 0.5–8 keV flux of" (5.4.2 AGN effects)
- External data: Herschel PACS and SPIRE flux densities used for the dust SED  
  > "with *Herschel* PACS and SPIRE flux-densities adopted from (cite: Zhang2018b)" (Table 1 caption) [from Zhang et al. 2018 (cite: Zhang2018b)]
- External data: ALMA Band 6 and 7 continuum flux densities  
  > "ALMA Bands 6 and 7 flux-densities adopted from R15a" (Table 1 caption) [from R15a (cite: Rybak2015a)]
- External data: CO(5-4) and CO(8-7) source-plane reconstructions  
  > "In this paper, we adopt the CO(5–4) and CO(8–7) from R15b" (2.1 Target description) [from R15b (cite: Rybak2015b)]
- External data: Lens mass model (SIE plus external shear)  
  > "We adopt the lens model of R15a derived from 0.1-arcsec resolution ALMA Band 6 and 7 continuum observations" (3.2 Lens modelling) [from R15a (cite: Rybak2015a)]
- External data: [O I] 63 um line flux and [O I] 145 um upper limit  
  > "while the 3$\sigma$ upper limit on the \[O i\] 145-$\mu$m line flux is $2.3\times10^{-18}$ W m$^{-2}$ (cite: Zhang2018b)" (4.2.1 [CII] dominates the gas cooling budget) [from Zhang et al. 2018 (cite: Zhang2018b)]
- External data: CO line ratios of Class I ULIRGs used to estimate total CO cooling  
  > "assuming that the CO line ratios in SDP.81 match CO ratios of the Class I ULIRGs from (cite: Rosenberg2015)" (4.2.1 [CII] dominates the gas cooling budget) [from Rosenberg et al. 2015 (cite: Rosenberg2015)]
- External data: R31 = 0.78 +/- 0.27 CO(3-2)/CO(1-0) brightness ratio  
  > "We adopt $R_{31}$ from (cite: Sharon2016) who found a mean $R_{31}=0.78\pm0.27$ for a sample of $z\sim2$ sub-millimeter galaxies" (4.2.3 Gas depletion time across the source) [from Sharon et al. 2016 (cite: Sharon2016)]
- External data: alpha_CO = 1.0 CO-to-H2 conversion factor  
  > "$\alpha_\mathrm{CO}=1.0$ inferred by (cite: CR18) from CO kinematic studies of $z=2-3$ DSFGs" (4.2.3 Gas depletion time across the source) [from CR18]
- External data: R51 = 0.32 +/- 0.05 CO(5-4)/CO(1-0) ratio  
  > "adopting $R_{51}=0.32\pm0.05$ from the (cite: Bothwell2013) CO SLED survey of a sample of 40 DSFGs at $z=1.2-4.1$" (4.2.3 Gas depletion time across the source) [from Bothwell et al. 2013 (cite: Bothwell2013)]
- External data: SFR-L_FIR calibration (Salpeter IMF)  
  > "using the (cite: Kennicutt1998) SFR-$L_\mathrm{FIR}$ relation for the Salpeter initial mass function" (4.1.1 Global dust SED) [from Kennicutt 1998 (cite: Kennicutt1998)]
- External data: PDRToolbox PDR model grids (line and FIR continuum predictions)  
  > "We adopt the line and FIR continuum predictions from the PDRToolbox models (cite: Kaufman1999; Kaufman2006; Pound2008)." (5.1 Modelling setup) [from Kaufman et al. 1999, 2006; Pound & Wolfire 2008]
- External data: Empirical PDR fraction of [C II] emission from rest-frame 63 um and 158 um continuum (f_PDR = 0.90 +/- 0.10)  
  > "the PDR contribution to the \[C ii\] can be estimated using the rest-frame 63-$\mu$m and 158-$\mu$m continuum (Equation 4 of (cite: Diaz2017))" (5.1 Modelling setup) [from Diaz-Santos et al. 2017 (cite: Diaz2017)]
- External data: XMM 0.5-8 keV flux and hardness ratio for the SDP.81 position  
  > "with a hardness ratio of -0.4 at the position of SDP.81 (cite: Ranalli2015)" (5.4.2 AGN effects) [from Ranalli et al. 2015 (cite: Ranalli2015)]
- External data: Thermal saturation model of [C II]/FIR (equations for Lambda_CII and L_CII/L_FIR)  
  > "In the thermally saturated regime (cite: MunozOh2016), the" (5.4.3 C+ thermal saturation) [from Munoz & Oh 2016 (cite: MunozOh2016)]
- Simulation/model as data: PDRToolbox semi-infinite slab PDR models, solar metallicity, stopped at A_V = 10, resampled to a 0.05 dex grid in G and n  
  > "The PDRToolbox models are calculated for a semi-infinite slab geometry, assuming a solar metallicity and stopping the calculation at the depth corresponding to a visual extinction $A_V=10$." (5.1 Modelling setup); "We re-sample them onto a finer grid (steps of 0.05 dex), using a degree 2 spline for interpolation." (5.1 Modelling setup)
- Simulation/model as data: Mock ALMA observations of uniform and FIR-like sources forward-lensed with the SDP.81 lens model, to test source reconstruction  
  > "We then create mock ALMA observations for each tracer by setting the sky-plane flux density to the observed value" (Appendix B)

## Processing

### Calibration

- pipeline or manual: Standard ALMA Cycle 4 pipeline plus manual flagging (Band 3: antennas DA53, DV22; Band 8: 6 min of integrations and channels at 468.0 and 457.3 GHz)  
  > "The data were calibrated and flagged using the standard ALMA Cycle 4 pipeline; in addition, antennas DA53 and DV22 were manually flagged due to a systematically high antenna temperature." (3.1.1 ALMA Band 3); "we performed manual flagging in the time-domain to remove several integrations which showed elevated noise levels; a total of 6 minutes of data was flagged." (3.1.2 ALMA Band 8); "We also flagged channels affected by atmospheric lines at 468.0 and 457.3 GHz." (3.1.2 ALMA Band 8)
- casa version: CASA 4.7 and 5.0  
  > "All the data processing was done with Casa versions 4.7 and 5.0 (cite: McMullin2007)." (3.1 Data preparation and imaging)
- pipeline version: _not stated_
- archive products used as is: _not stated_
- flux calibrator: _not stated_
- flux scale uncertainty: 10 per cent flux calibration error adopted per tracer  
  > "we include an additional 10 per cent flux calibration error for each tracer, as appropriate for high-S/N ALMA observations" (5.1 Modelling setup)
- self calibration: _not stated_

### Imaging

- task: _not stated_
- deconvolver: _not stated_
- weighting robust: Natural weighting for Cleaned maps (LBC beams quoted for Briggs robust = 1)  
  > "obtained using natural weighting and an outer Gaussian taper of 0.2 arcsec" (3.1 Data preparation and imaging); "(Briggs weighing, robust = 1)" (2.4 ALMA 2014 Long Baseline Campaign observations)
- uv taper: Outer Gaussian taper of 0.2 arcsec (Cleaned maps in Fig. 1)  
  > "obtained using natural weighting and an outer Gaussian taper of 0.2 arcsec" (3.1 Data preparation and imaging)
- cell size: _not stated_
- image size: _not stated_
- masking: _not stated_
- multiscale scales: _not stated_
- continuum subtraction: _not stated_
- line free channels: _not stated_
- primary beam correction: _not stated_
- array combination: _not stated_
- smoothing: Line-containing channels frequency-averaged into a single bin for CO(3-2) and CO(10-9); [C II] averaged into 62.50 MHz (~40 km/s) channels  
  > "Due to the low S/N, we frequency-averaged the line-containing channels into a single frequency bin." (3.1.1 ALMA Band 3); "We frequency-averaged the line into channels 62.50 MHz ($\sim40$ km s$^{-1}$) wide" (3.3.2 [CII] emission)
- final beam: _not stated_
- final rms: Band 3 continuum 10 uJy/beam (natural weighting)  
  > "The Cleaned Band 3 continuum map has an rms noise of 10 $\mu$Jy beam$^{-1}$ (natural weighting)." (3.1.1 ALMA Band 3)

### Inherited from earlier work

- Time-averaging of 20 s applied to Band 3 visibilities  
  > "A time-averaging of 20 s was applied, as in R15a,b." (3.1.1 ALMA Band 3) [from R15a,b (cite: Rybak2015a; Rybak2015b)]
- Bands 6 and 7 continuum data preparation  
  > "For details of the continuum data preparation, we refer the reader to R15a." (3.1.3 ALMA Long Baseline Campaign) [from R15a (cite: Rybak2015a)]
- LBC observations and CO(10-9) imaging described elsewhere  
  > "As the ALMA Long Baseline Campaign (LBC) observations of SDP.81 were described in detail in (cite: alma2015)" (2.4 ALMA 2014 Long Baseline Campaign observations); "see (cite: alma2015) for detailed description and imaging" (3.1.3 ALMA Long Baseline Campaign) [from ALMA Partnership 2015 (cite: alma2015)]
- uv-distance cut of <= 1 Mlambda adopted for all datasets because of S/N drop on longer baselines  
  > "For the CO lines, a strong drop in S/N was observed for baselines longer than 1 M$\lambda$ (cite: alma2015)." (2.4 ALMA 2014 Long Baseline Campaign observations) [from ALMA Partnership 2015 (cite: alma2015)]
- Lens modelling method (visibility-plane, adaptive Delaunay source grid) and the SIE+shear lens mass model  
  > "We perform the lens-modelling using the method first presented in (cite: Rybak2015a), which is an extension of the Bayesian technique of (cite: Vegetti2009)" (3.2 Lens modelling); "We adopt the lens model of R15a derived from 0.1-arcsec resolution ALMA Band 6 and 7 continuum observations" (3.2 Lens modelling) [from R15a (cite: Rybak2015a); Vegetti & Koopmans 2009 (cite: Vegetti2009)]
- Source-plane PDR-modelling approach for DSFGs and the thermal-saturation analysis of the [C II]/FIR deficit  
  > "We apply the analysis of (cite: Rybak2019) to the 200-pc resolution maps of SDP.81." (5.4 What drives the [CII]/FIR deficit in SDP.81?) [from Rybak et al. 2019 (cite: Rybak2019)]

### Not stated but needed to reproduce (our reading)

- The lens-modelling code itself is not named or stated as public; its regularization form (R_s), the converged lambda_S values and the optimizer settings are not given
- Full lens mass model parameters (SIE and shear values) are only referenced to R15a
- Flux, bandpass and phase calibrators, and any self-calibration, for the Band 3, Band 8 and LBC data are not given
- CASA tasks and parameters used for Cleaning (tclean deconvolver, masks, cell and image size, iterations, thresholds) are not given
- Line-free channel ranges and continuum-subtraction method for [C II], CO(3-2) and CO(10-9) are not stated
- Which Band 8 and Band 3 SPWs formed the continuum maps, and time-averaging used for Band 8, are not stated
- Pipeline version and archive product versions for each dataset are not stated
- PDRToolbox version and exact model grid files, and the exact definition of the 'FIR-bright region' mask and the region used in Fig. 13/15 are not given
- How the CO(1-0) conversion was applied pixel by pixel (CO(5-4) S/N masks, error propagation) is only partly described
- Per-tracer source-plane magnifications used for each S/N threshold are given only in aggregate (table values), not per pixel

## Analysis recipe

1. **Calibrate, flag and average the visibilities**: Standard ALMA Cycle 4 pipeline calibration with extra manual flagging; line channels averaged; 20 s time-averaging; uv-distance cut at 1 Mlambda for all datasets  
  > "The data were calibrated and flagged using the standard ALMA Cycle 4 pipeline; in addition, antennas DA53 and DV22 were manually flagged due to a systematically high antenna temperature." (3.1.1 ALMA Band 3); "A time-averaging of 20 s was applied, as in R15a,b." (3.1.1 ALMA Band 3)
   - software: CASA
   - parameter: CO(3-2) line channels (85.509-85.571 GHz) averaged into one frequency bin  
  > "Due to the low S/N, we frequency-averaged the line-containing channels into a single frequency bin." (3.1.1 ALMA Band 3)
   - parameter: CO(10-9) visibilities (284.733-285.52 GHz) averaged into a single channel  
  > "we frequency-averaged the visibilities into a single channel" (3.1.3 ALMA Long Baseline Campaign)
   - parameter: Band 8: 6 minutes of data flagged; channels at 468.0 and 457.3 GHz flagged  
  > "a total of 6 minutes of data was flagged" (3.1.2 ALMA Band 8); "We also flagged channels affected by atmospheric lines at 468.0 and 457.3 GHz." (3.1.2 ALMA Band 8)
   - parameter: uv-distance <= 1 Mlambda for all datasets (Bands 6 and 7 continuum re-done with this cut instead of 2 Mlambda)  
  > "applying a $uv$-distance cut of $\leq$1 M$\lambda$ as opposed to the 2-M$\lambda$ cut in R15a" (3.1.3 ALMA Long Baseline Campaign)
   - fitting: _not stated_
   - validation: Image-plane [C II] flux compared with the Herschel SPIRE FTS flux, consistent within 1 sigma, to show Band 8 does not resolve out extended emission  
  > "This confirms that ALMA Band 8 observations are not resolving out extended" (3.1.2 ALMA Band 8)
2. **Make Cleaned images to check detections and integrated fluxes**: Cleaned frequency-integrated maps of Band 8 continuum, [C II], CO(3-2), CO(10-9) with natural weighting and 0.2 arcsec outer taper  
  > "obtained using natural weighting and an outer Gaussian taper of 0.2 arcsec" (3.1 Data preparation and imaging)
   - software: CASA
   - parameter: Peak S/N 5.6 sigma for CO(3-2) and ~5 for CO(10-9)  
  > "with a peak S/N of 5.6$\sigma$" (3.1.1 ALMA Band 3); "(peak image-plane SN$\simeq5$, Fig. [1](#fig:cleaned))" (3.1.3 ALMA Long Baseline Campaign)
   - fitting: _not stated_
   - validation: Band 3 continuum AGN flux of the lens compared with synchrotron spectrum from Tamura et al. 2015, consistent within 2 sigma  
  > "The observed flux is consistent with the (cite: Tamura2015) synchrotron spectrum for the foreground AGN within $2\sigma$." (3.1.1 ALMA Band 3)
3. **Reconstruct source-plane maps by visibility-plane lens modelling**: Fixed parametric SIE+shear lens model; source on an adaptive Delaunay triangular grid; penalty function combining visibility chi^2 with source-plane regularization; lambda_S re-optimized per dataset (and per [C II] channel)  
  > "To summarize, this technique uses a parametric lens model, while the source is reconstructed on an adaptive triangular grid obtained via the Delaunay tessellation." (3.2 Lens modelling); "Keeping the lens mass model fixed, we re-optimize for the offset between the lens center and phase-tracking centre" (3.2 Lens modelling)
   - software: lens-modelling code of Rybak et al. 2015a (not named)
   - parameter: Sky-plane pixel size 25 mas; every second pixel cast back, so beam sub-sampled by ~4  
  > "The sky-plane pixel size is set to 25 mas" (3.2 Lens modelling)
   - parameter: Primary beam approximated by an elliptical Gaussian  
  > "The primary beam response is approximated by an elliptical Gaussian." (3.2 Lens modelling)
   - parameter: Visibility noise from the scatter over 10-minute intervals rather than the Sigma column  
  > "rather than from the Sigma column of the ALMA Measurement Set files" (3.2 Lens modelling)
   - parameter: [C II] reconstructed in 62.50 MHz (~40 km/s) channels with lambda_S optimized per channel; moment-0 and moment-1 maps made (pixels with SNR <= 1 masked for moment 1)  
  > "We frequency-averaged the line into channels 62.50 MHz ($\sim40$ km s$^{-1}$) wide" (3.3.2 [CII] emission); "For the moment-one map, we mask pixels with SNR$\leq$1 in each channel before calculating the velocity map." (3.3.2 [CII] emission)
   - parameter: Reconstructions re-sampled onto a Cartesian grid of 200x200 pc pixels  
  > "we re-sample the reconstructed source onto a Cartesian grid with 200$\times$200 pc pixels" (3.3 Source-plane reconstructions)
   - assumption: Lens mass model fixed to R15a (SIE with external shear)  
  > "which follows a singular isothermal ellipsoid profile with an external shear component" (3.2 Lens modelling)
   - fitting: Minimization of a penalty function: visibility-space chi^2 plus source-plane regularization term lambda_S (R_s s)^T R_s s; no sampler or priors stated  
  > "with a source-plane regularization to constrain the problem and prevent noise-fitting" (3.2 Lens modelling)
   - validation: Residuals in the dirty-image plane; mock-data lens-modelling tests (Appendix B) recover mean surface brightness within 10-15 per cent (~20 per cent for CO(3-2))  
  > "we further assess the reliability of the source-plane reconstruction by performing our lens modelling analysis on mock datasets in Appendix" (3.3 Source-plane reconstructions); "with the mean surface brightness recovered within 10–15 per cent for most datasets ($\sim$20 per cent for CO(3–2))" (3.3 Source-plane reconstructions)
4. **Estimate source-plane uncertainties and magnifications**: Noise-realization Monte Carlo for per-pixel uncertainty; integrated magnification from forward-lensing source pixels above S/N thresholds; systematic error from mock uniform and FIR-like sources  
  > "drawing 1000 random realizations of the noise map given the" (3.2 Lens modelling); "forward-lens them into the image-plane and calculate the corresponding magnification and uncertainty for each S/N threshold" (3.2 Lens modelling)
   - software: lens-modelling code of Rybak et al. 2015a (not named)
   - parameter: 1000 noise realizations; S/N thresholds 1, 2, 3 averaged for the magnification  
  > "we take all the source-plane pixels with S/N $\geq$1, 2 and 3" (3.2 Lens modelling)
   - parameter: Mock sources: uniform ellipse 3.4x2.4 kpc and an FIR-luminosity-map source, forward-lensed with the SDP.81 lens model  
  > "a uniform surface-brightness elliptical source with major/minor axis of 3.4$\times$2.4 kpc" (Appendix B)
   - fitting: _not stated_
   - validation: Fractional systematic error on mean surface brightness: 65 per cent CO(3-2), 30 per cent CO(10-9), ~10 per cent for continuum, [C II] and CO(5-4)/(8-7)  
  > "the fractional uncertainty is 65 and 30 per cent, respectively" (Appendix B)
5. **Fit the dust SED and derive L_FIR, T_dust and SFR**: Optimally-thin modified black body fitted to ALMA Bands 4/6/7/8 and Herschel PACS/SPIRE photometry; resolved fit of T_dust only on Bands 6, 7, 8 source-plane maps; SFR from the Kennicutt (1998) relation  
  > "and an optically-thin modified black-body SED" (4.1.1 Global dust SED); "We therefore adopt $\beta=1.8$ derived from the spatially-integrated SED fit, and fit for $T_\mathrm{dust}$ only." (4.1.2 Resolved dust SED)
   - parameter: Uniform magnification adopted for 160 um to 1.3 mm continuum; Herschel 160-500 um emission assumed to follow the Band 8 surface brightness distribution  
  > "for our analysis, we assume all the 160 to 500-$\mu$m emission to follow the Band 8 surface brightness distribution." (Table 1 caption)
   - parameter: Resolved test of T_dust fixed to 60 K and 80 K, fitting only the normalization  
  > "We do this by fixing $T_\mathrm{dust}$ to 60 and 80 K, respectively, and optimizing for the normalization ($\propto M_\mathrm{dust}$) only." (4.1.2 Resolved dust SED)
   - parameter: FIR-bright region defined as Sigma_SFR >= 50 Msun/yr/kpc^2  
  > "we will refer to the region with $\Sigma_\mathrm{SFR}\geq 50$ M$_\odot$ yr$^{-1}$ kpc$^{-2}$ as the *FIR-bright region*" (4.1.1 Global dust SED)
   - assumption: Optically thin dust emission; uniform T_dust and beta; Salpeter IMF; CMB effects negligible (<=0.1 K, <=0.1 dex)  
  > "we consider the CMB effects to be negligible for SDP.81" (4.1.1 Global dust SED); "the CMB effect on $T_\mathrm{dust}$ is $\leq0.1$ K, while the inferred $L_\mathrm{FIR}$ is biased by $\leq$0.1 dex" (4.1.1 Global dust SED)
   - fitting: _not stated_
   - validation: Compared with earlier SDP.81 estimates and the ALESS median T_dust; resolved fit repeated on Cleaned images gives consistent results  
  > "Repeating the SED-fitting on the Cleaned Bands 6, 7 and 8 images (thus eliminating any lens-modelling systematics) yields results consistent with the source-plane analysis." (4.1.2 Resolved dust SED)
6. **Gas cooling budget, CO SLED and CO-FIR correlations**: Compare source-plane [C II], [O I] and CO line luminosities; unobserved CO lines scaled with Class I ULIRG ratios; Pearson correlation of CO or [C II] with FIR per pixel (SNR >= 3) with 1000 Monte Carlo realizations  
  > "assuming that the CO line ratios in SDP.81 match CO ratios of the Class I ULIRGs from (cite: Rosenberg2015)" (4.2.1 [CII] dominates the gas cooling budget); "for each pixel with SNR$\geq$3 in both tracers" (4.2.2 CO spectral energy distribution)
   - parameter: CO(1-0), CO(7-6) and CO(9-8) assumed to follow the spatial distribution of CO(3-2), (8-7) and (10-9)  
  > "we assume that the CO(1–0), (7–6) and (9–8) lines follow the same spatial distribution as the CO(3–2), (8–7) and (10–9) lines, respectively" (4.2 Emission lines)
   - assumption: [O I] lines assumed to follow the FIR continuum surface brightness distribution  
  > "Assuming both lines follow the FIR continuum surface brightness distribution, we obtain the de-lensed source-plane luminosities" (4.2.1 [CII] dominates the gas cooling budget)
   - fitting: _not stated_
   - validation: CO SLED well reproduced (chi^2 <= 1) by PDRToolbox models without mechanical heating  
  > "As the SDP.81 CO ladder is well-reproduced ($\chi^2\leq1$) by the PDRToolbox models which do not include mechanical heating" (4.2.2 CO spectral energy distribution)
7. **Resolved molecular gas depletion time**: Sigma_H2 from the CO(3-2) map via R31 and alpha_CO; t_dep = Sigma_H2 / Sigma_SFR; cross-check with CO(5-4) and R51  
  > "We estimate the molecular gas surface density $\Sigma_\mathrm{H_2}$ using the CO(3–2) line map." (4.2.3 Gas depletion time across the source); "adopting $R_{51}=0.32\pm0.05$ from the (cite: Bothwell2013) CO SLED survey" (4.2.3 Gas depletion time across the source)
   - parameter: R31 = 0.78 +/- 0.27; alpha_CO = 1.0  
  > "We adopt $R_{31}$ from (cite: Sharon2016) who found a mean $R_{31}=0.78\pm0.27$ for a sample of $z\sim2$ sub-millimeter galaxies" (4.2.3 Gas depletion time across the source)
   - assumption: alpha_CO = 1.0 from CO kinematic studies of z=2-3 DSFGs, consistent with dynamical mass constraints  
  > "$\alpha_\mathrm{CO}=1.0$ inferred by (cite: CR18) from CO kinematic studies of $z=2-3$ DSFGs" (4.2.3 Gas depletion time across the source)
   - fitting: _not stated_
   - validation: Check with CO(5-4) as gas tracer gives t_dep = 1-30 Myr; mock tests show CO(3-2) north concentration is physical  
  > "we find a $t_\mathrm{dep}=1-30$ Myr, confirming the extremely short gas depletion time" (4.2.3 Gas depletion time across the source)
8. **Measure the global and resolved [C II]/FIR ratio and its slope with Sigma_SFR**: Ratio of source-plane [C II] and FIR luminosities, globally and per 200 pc pixel; log-log slope vs Sigma_SFR by orthogonal distance regression  
  > "using orthogonal distance regression, similar to the slope of $-0.7$ derived by (cite: Lamarche2018) for SDP.11" (4.3 [CII]/FIR ratio and deficit)
   - fitting: Orthogonal distance regression of log Sigma_SFR vs log([C II]/FIR)  
  > "using orthogonal distance regression" (4.3 [CII]/FIR ratio and deficit)
   - validation: Compared with Smith et al. 2017 trend and other high-z resolved studies; isolated outlying low-ratio pixels judged lens-modelling artifacts  
  > "these are likely lens-modelling artifacts" (4.3 [CII]/FIR ratio and deficit)
9. **PDR modelling of G, n and T_PDR (global and per 200 pc pixel)**: Chi^2 comparison of observed line ratios with PDRToolbox predictions over a G-n grid, including 3-sigma upper limits following Sawicki 2012; maximum a posteriori model for the global fit  
  > "Following (cite: Sawicki2012), we include the $3\sigma$ upper limits as" (5.1 Modelling setup); "The maximum a posteriori model gives $G = 10^{3.1\pm0.1}~G_0$, $n = 10^{4.9\pm0.1}$ cm$^{-3}$, with a reduced $\chi^2=0.96$." (5.2 Global PDR model)
   - software: PDRToolbox
   - parameter: Line ratios: [C II]/FIR, [C II]/CO(5-4), [C II]/CO(3-2), CO(8-7)/CO(5-4), CO(10-9)/CO(5-4)  
  > "For the comparison with observations, we consider the following independent line ratios: \[C ii\]/FIR, \[C ii\]/CO(5–4), \[C ii\]/CO(3–2), CO(8–7)/CO(5–4) and CO(10–9)/CO(5–4)." (5.1 Modelling setup)
   - parameter: Pixels with SNR >= 3 treated as detections, SNR < 3 as 3-sigma upper limits  
  > "for pixels with SNR$<3$, we adopt $3\sigma$ upper limits." (5.1 Modelling setup)
   - parameter: PDR fraction of [C II] adopted f_PDR = 0.8  
  > "we adopt a conservative estimate of the $f_\mathrm{[CII]}^\mathrm{PDR}=0.8$" (5.1 Modelling setup)
   - parameter: Solutions with G0/n <= 1e-3 discarded as unphysical  
  > "we discard the solutions with $G_0/n$(H)$\leq10^{-3}$, which would imply an unphysically large source" (5.3 Resolved PDR model)
   - parameter: Error budget per pixel: 10 per cent flux calibration, lens-model scatter, and mock-source systematic (6 to 65 per cent)  
  > "Flux calibration uncertainty, assumed to be 10 per cent in each Band." (5.3 Resolved PDR model); "These vary between 6 per cent (FIR continuum) to 30 per cent for CO(10–9) and 65 per cent for CO(3–2)" (5.3 Resolved PDR model)
   - assumption: Solar metallicity PDRToolbox model, semi-infinite slab, uniform density  
  > "we consider the $Z=1~Z_\odot$ default PDRToolbox model as appropriate for dust-rich ISM of SDP.81" (5.1 Modelling setup)
   - assumption: Optically thin tracers (FIR, [C II]) predictions doubled for multi-sided illumination; CO lines optically thick  
  > "for the optically-thin tracers, both the sides facing to and away from the observer will contribute to the observed flux, and the predicted fluxes need to be doubled." (5.1 Modelling setup)
   - fitting: Chi^2 minimization on a 0.05 dex G-n grid with upper-limit term (Sawicki 2012); no sampler or priors stated  
  > "We re-sample them onto a finer grid (steps of 0.05 dex), using a degree 2 spline for interpolation." (5.1 Modelling setup)
   - validation: Models reproduce line ratios with reduced chi^2 <= 5; shifts of <= 0.5 dex in G and n under an order-unity bias in the line ratios; detections-only fit changes G, n by <= 0.1 dex  
  > "The PDRToolbox models reproduce the observed line ratios well (reduced $\chi^2\leq5$)" (5.4.1 Caveats and limitations); "We find that the inferred $G$, $n$(H) values shift by $\leq0.5$ dex even in such an extreme scenario" (5.1 Modelling setup)
10. **Test mechanisms behind the [C II]/FIR deficit**: Compare reduced photoelectric heating (Wolfire 2003), AGN X-ray influence and C+ thermal saturation (Munoz & Oh 2016, with correction f_CII for the gas fraction traced by [C II]) against the resolved maps  
  > "we consider the following mechanisms: (1) thermal saturation of the \[C ii\] fine-structure levels; (2) reduced gas heating due to positive grain charging; (3) AGN contribution." (5.4 What drives the [CII]/FIR deficit in SDP.81?)
   - parameter: n_e = 1.1e-4 n; phi_PAH = 0.5 in the photoelectric heating rate  
  > "Assuming $n_e=1.1\times10^{-4}\,n$ and $\phi_\mathrm{PAH}=0.5$" (5.4.1 Reduced photoelectric heating)
   - parameter: f_CII computed per pixel from CO(5-4) S/N >= 3 pixels using the Bothwell 2013 conversion and alpha_CO from CR18  
  > "by using the (cite: Bothwell2013) conversion factor and $\alpha_\mathrm{CO}$ from (cite: CR18)" (5.4.3 C+ thermal saturation)
   - assumption: PDR surface temperature taken as the gas temperature in the [C II]-emitting layer; [C II] optically thin; dense gas above critical density  
  > "This allows us to take the PDR surface temperature $T_\mathrm{PDR}$ as indicative of the gas temperature in the \[C ii\]-emitting regions." (5.4.3 C+ thermal saturation)
   - fitting: Power-law slope of [C II]/FIR vs Sigma_SFR fitted before and after the f_CII correction  
  > "we obtain a best-fitting power-law slope of $=-0.55\pm0.02$" (5.4.3 C+ thermal saturation)
   - validation: Corrected slope -0.55 +/- 0.02 matches the thermal-saturation prediction (-0.5); uncorrected slope 0.65 +/- 0.01 is in tension  
  > "in line with the (cite: MunozOh2016) prediction" (5.4.3 C+ thermal saturation)

## Software

- **CASA** 4.7 and 5.0: All visibility data processing and Cleaned imaging  
  > "All the data processing was done with Casa versions 4.7 and 5.0 (cite: McMullin2007)." (3.1 Data preparation and imaging)
- **ALMA Cycle 4 pipeline** : Standard calibration and flagging of the Band 3 data (and standard calibration of Band 8)  
  > "The data were calibrated and flagged using the standard ALMA Cycle 4 pipeline" (3.1.1 ALMA Band 3)
- **Visibility-plane lens modelling code of Rybak et al. 2015a (unnamed)** : Source-plane reconstruction of all tracers on an adaptive Delaunay grid  
  > "We perform the lens-modelling using the method first presented in (cite: Rybak2015a)" (3.2 Lens modelling)
- **PDRToolbox** : Photon-dominated region model predictions of line and FIR ratios  
  > "We adopt the line and FIR continuum predictions from the PDRToolbox models (cite: Kaufman1999; Kaufman2006; Pound2008)." (5.1 Modelling setup)
- **corner** : Corner plot in Fig. 14  
  > "Fig. [14](#fig:G0_nH_comparison) utilizes the corner package by (cite: Corner)." (Acknowledgements)

## Numeric results

| quantity | value | uncertainty | units | step | quote |
|---|---|---|---|---|---|
| Median source-plane resolution | ~30 mas (~200 pc) | not stated | mas / pc | 3 | The median source-plane resolution is $\sim$30 mas, which corresponds to $\sim$200 parsec |
| Dust temperature (global SED) | 35 | 4 | K | 5 | We obtain $T_\mathrm{dust}=35\pm4$ K and $\beta=1.8\pm0.3$ and a (magnification-corrected) FIR luminosity (8-1000 $\mu$m) $L_\mathrm{FIR}=(2.4\pm0.5)\times10^{12}$ L$_\odot$. |
| Dust emissivity index beta | 1.8 | 0.3 | dimensionless | 5 | We obtain $T_\mathrm{dust}=35\pm4$ K and $\beta=1.8\pm0.3$ and a (magnification-corrected) FIR luminosity (8-1000 $\mu$m) $L_\mathrm{FIR}=(2.4\pm0.5)\times10^{12}$ L$_\odot$. |
| FIR luminosity (8-1000 um, magnification-corrected) | 2.4e12 | 0.5e12 | Lsun | 5 | We obtain $T_\mathrm{dust}=35\pm4$ K and $\beta=1.8\pm0.3$ and a (magnification-corrected) FIR luminosity (8-1000 $\mu$m) $L_\mathrm{FIR}=(2.4\pm0.5)\times10^{12}$ L$_\odot$. |
| Star-formation rate | 410 | 90 | Msun/yr | 5 | which yields SFR = 410$\pm$90 M$_\odot$ yr$^{-1}$. |
| Band 3 continuum flux of the lens-galaxy AGN | 52 | 10 | uJy | 2 | with a total flux of 52$\pm$10 $\mu$Jy |
| Image-plane [C II] integrated line flux | 170 | 20 | Jy km/s | 2 | integrated line flux of 170$\pm$20 Jy km s$^{1}$ |
| Spatially integrated [C II]/FIR luminosity ratio | 1.5e-3 | 0.3e-3 | dimensionless | 8 | FIR luminosity ratio of $(1.5 \pm 0.3)\times 10^{-3}$ |
| [C II]/FIR slope vs Sigma_SFR | -0.75 | 0.01 | dimensionless | 8 | slope of $-0.75\pm0.01$, using orthogonal distance regression |
| Pearson correlation of CO(3-2), CO(5-4), CO(8-7), CO(10-9) with FIR | 0.401, 0.847, 0.821, 0.664 | 0.010, 0.006, 0.006, 0.09 | dimensionless | 6 | We find $R_\mathrm{CO(3-2)/FIR}=0.401\pm0.010$, $R_\mathrm{CO(5-4)/FIR}=0.847\pm0.006$, $R_\mathrm{CO(8-7)/FIR}=0.821\pm0.006$ and $R_\mathrm{CO(10-9)/FIR}=0.664\pm0.09$. |
| Molecular gas depletion time range (CO(3-2) tracer) | ~1 Myr (south) to ~20 Myr (north) | ~33 per cent relative (R31 uncertainty) | Myr | 7 | from $\sim1$ Myr in the south to $\sim20$ Myr in the north; By adopting the (cite: Sharon2016) $r_{3/1}$ value, the relative uncertainty is $\sim$33 per cent |
| Gas depletion time from CO(5-4) check | 1-30 | not stated | Myr | 7 | we find a $t_\mathrm{dep}=1-30$ Myr |
| Global PDR FUV field G | 10^3.1 | +/-0.1 dex | G0 | 9 | The maximum a posteriori model gives $G = 10^{3.1\pm0.1}~G_0$, $n = 10^{4.9\pm0.1}$ cm$^{-3}$, with a reduced $\chi^2=0.96$. |
| Global PDR gas density n | 10^4.9 | +/-0.1 dex | cm^-3 | 9 | The maximum a posteriori model gives $G = 10^{3.1\pm0.1}~G_0$, $n = 10^{4.9\pm0.1}$ cm$^{-3}$, with a reduced $\chi^2=0.96$. |
| Resolved PDR G and n in the central FIR-bright region | G = 10^3.5-10^4.0 G0; n(H) = 10^5.0-10^5.5 cm^-3 | typical ~0.2 dex | G0; cm^-3 | 9 | we find strong FUV fields with $G=10^{3.5} - 10^{4.0}~G_0$, and high density $n$(H)=$10^{5.0}-10^{5.5}$ cm$^{-3}$, with a typical uncertainty of $\sim0.2$ dex |
| East-West gradient in G | 10^3.0 to 10^4.0 | +/-0.2 and +/-0.1 dex | G0 | 9 | $G$ increases from $10^{3.0\pm0.2}$ to $10^{4.0\pm0.1}~G_0$ |
| PDR surface temperature | ~150 K (outskirts) to 1500 K (FIR-bright clumps) | S/N <= 5 across the source | K | 9 | The PDR surface temperature $T_\mathrm{PDR}$ varies from about 150 K in the outskirts to 1500 K in the FIR-bright clumps. |
| Resolved [C II]/FIR minimum in FIR-bright clumps | ~(2-3)e-4 | not stated | dimensionless | 8 | down to $\sim(2-3)\times10^{-4}$ in the two FIR-bright clumps |
| Fraction of [C II] luminosity from Sigma_SFR <= 10 Msun/yr/kpc^2 | ~50 per cent | not stated | per cent | 3 | $\sim$50 per cent of the total \[C ii\] luminosity arises from regions with |
| [C II]/FIR slope after f_CII correction | -0.55 | 0.02 | dimensionless | 10 | we obtain a best-fitting power-law slope of $=-0.55\pm0.02$ |
| [C II]/FIR slope without f_CII correction | 0.65 (as printed alpha) | 0.01 | dimensionless | 10 | yields $\alpha=0.65\pm0.01$ |
| Mean f_CII (fraction of gas traced by [C II]) | 0.32 | 16 (as printed) | dimensionless | 10 | we obtain a mean $f_\mathrm{[CII]}=0.32\pm16$ |
| Source-plane X-ray luminosity if all XMM flux is from a northern-clump AGN | ~2e44 | not stated | erg/s | 10 | we find a source-plane X-ray luminosity $L_\mathrm{0.5-8.0~keV}\simeq2\times10^{44}$ erg s$^{-1}$ (uncorrected for obscuration) |

## Qualitative findings

- [C II] emission is much more extended than the FIR continuum and the CO(5-4) and CO(8-7) emission, with an extended non-corotating feature to the north  
  > "This double-imaged feature is present in the dirty images of the corresponding velocity channels" (3.3.2 [CII] emission); "emission arises outside the FIR-bright region" (abstract)
- No significant spatial variation in T_dust; T_dust = 60 K is excluded at >= 3 sigma almost everywhere and 80 K everywhere  
  > "$T_\mathrm{dust}$=80 K is excluded at $\geq3\sigma$ confidence level for the entire source." (4.1.2 Resolved dust SED)
- Global gas cooling is dominated by [C II]; CO contributes ~10 per cent  
  > "Therefore, the global gas cooling in SDP.81 is dominated by the" (4.2.1 [CII] dominates the gas cooling budget)
- Thermal saturation of C+ fine-structure levels is the most likely cause of the [C II]/FIR deficit  
  > "we consider the thermal saturation of the C$^+$ fine-structure levels to be the most likely cause of the strong" (5.4.3 C+ thermal saturation)

## Claim tuples

- H: Are the FIR continuum, CO and [C II] co-spatial in SDP.81? | E: Visibility-plane lens modelling of Band 8 continuum, [C II], CO(3-2), CO(10-9) and comparison with CO(5-4), CO(8-7) and Band 6/7 continuum at matched resolution | R: [C II] is much more extended than the FIR continuum; ~50 per cent of [C II] arises outside the FIR-bright region; CO(3-2) is concentrated to the north | F: Different ISM tracers occupy different regions, so unresolved line ratios mask the conditions in the star-forming clumps | **supported**
- H: What are the FUV field, density and surface temperature of the star-forming gas on 200 pc scales? | E: Chi^2 fit of PDRToolbox models to five line ratios per 200 pc pixel, plus a global fit | R: G ~ 10^3-10^4 G0, n ~ 1e5 cm^-3, T_PDR up to 1500 K; global G = 10^3.1, n = 10^4.9 | F: Conditions are similar to those near the Orion Trapezium, but averaged over 200 pc | **supported**
- H: What drives the strong [C II]/FIR deficit in the FIR-bright clumps? | E: Compare reduced photoelectric heating, AGN influence and C+ thermal saturation with the resolved G, n, T_PDR and [C II]/FIR maps | R: Photoelectric rate varies by only ~50 per cent, X-ray flux is insufficient, and f_CII-corrected slope (-0.55) matches the saturation model | F: Thermal saturation of the C+ fine-structure level occupancy at high gas temperature is the most likely cause | **supported**
- H: Is the molecular gas depletion time short and spatially variable? | E: Sigma_H2 from CO(3-2) (R31, alpha_CO = 1.0) divided by Sigma_SFR from FIR | R: t_dep from ~1 Myr in the south to ~20 Myr in the north; CO(5-4) check gives 1-30 Myr | F: Extreme starburst depletion times, varying by ~1 dex across the source | **partially**
- H: Does T_dust rise toward the centre, as invoked for DSFGs by CR18? | E: Resolved modified black-body fits to Bands 6, 7, 8 source-plane maps, with T_dust free and fixed to 60 or 80 K | R: No significant T_dust variation; 60 K inconsistent at >= 3 sigma except near the FIR peak; 80 K excluded everywhere | F: The data are in tension with a high central T_dust | **supported**

## Reasoning

- Why this data: Resolved multi-tracer observations are needed because spatially integrated data assume uniform PDR conditions  
  > "Consequently, resolved multi-tracer observations are necessary to robustly infer the PDR conditions in DSFGs." (1 Introduction)
- Why this method: Lens modelling in the visibility plane minimises differential magnification bias; PDRToolbox chosen for performance and consistency with earlier source-averaged DSFG studies  
  > "thereby minimizing the differential magnification bias" (3.2 Lens modelling); "and for consistency with earlier, source-averaged studies of ISM properties in DSFGs" (5.4.1 Caveats and limitations)
- Alternative: Reduced photoelectric heating (positive grain charging) rejected: its variation (~50 per cent) is insufficient to explain the ~1.5 dex [C II]/FIR variation  
  > "The $\Gamma_\mathrm{PE}$ varies by only $\sim$50 per cent across the source; this variation is insufficient to explain the $\sim$1.5 dex variation in the observed" (5.4.1 Reduced photoelectric heating)
- Alternative: AGN-driven deficit disfavoured: X-ray flux insufficient beyond a few hundred pc, and two similar [C II]/FIR minima separated by ~1 kpc  
  > "shows that the X-ray flux in SDP.81 is insufficient to drive the" (5.4.2 AGN effects); "Finally, circumstantial evidence also disfavours the AGN-driven" (5.4.2 AGN effects)
- Alternative: Mechanical heating not directly constrained; the CO ladder is consistent with negligible mechanical heating  
  > "we do not attempt to directly constrain the mechanical heating contribution" (4.2.2 CO spectral energy distribution)
- How they decided it was enough: _not stated_
- Limitation (authors): CO(3-2) has low S/N and must be interpreted carefully  
  > "it must be interpreted carefully" (3.3.3 CO(3-2) emission)
- Limitation (authors): Agreement of the PDR models with line ratios is largely due to large systematic uncertainties on CO(3-2) and CO(10-9) reconstructions  
  > "We emphasise that the agreement between the observed line ratios and the simplistic PDR models is largely due to significant systematic uncertainties on the CO(3–2) and CO(10–9) source reconstructions." (6 Conclusions)
- Limitation (authors): Semi-infinite uniform-density slab models are likely too simplistic for a clumpy ISM  
  > "Our semi-infinite, uniform-density slab models (even after adjusting for multi-side illumination) are likely too simplistic" (5.4.1 Caveats and limitations)
- Limitation (authors): Low surface-brightness CO(10-9) component could be a modelling artifact  
  > "we note that given the S/N of the data at hand, this could be a modelling artifact." (Appendix B)
- Limitation (authors): T_dust from rest-frame 160-350 um is limited because the data lie on the Rayleigh-Jeans tail  
  > "our resolved ALMA imaging is still on the Rayleigh-Jeans tail of the dust continuum SED" (4.1.2 Resolved dust SED)
- Caveat (inferred, ours): Key PDR conclusions rest on CO(3-2) and CO(10-9) reconstructions with 65 and 30 per cent systematic uncertainties, so the resolved G, n maps are weakly constrained by those lines
- Caveat (inferred, ours): Lens-model-dependent source-plane results cannot be checked without the lens-modelling code and fixed lens parameters
- Caveat (inferred, ours): f_CII = 0.32 +/- 16 as printed looks like a typo, and the slope comparison (-0.55 vs -0.5) uses an alpha_CO and CO ladder conversion not independently tested
- Caveat (inferred, ours): Conclusion states t_dep = 10^6-2x10^7 Myr, inconsistent with the text value of 1-20 Myr (unit typo)
- Caveat (inferred, ours): Single-model PDR interpretation (PDRToolbox slab) with no comparison against other PDR codes

## Reproducibility

- Data public (paper): ALMA project codes are given; derived source-plane maps said to be public at sdp81.strw.leidenuniv.nl; ALMA data availability itself is not discussed  
  > "We make the source-plane reconstructions of all emission lines and continuum data publicly available." (abstract); "publicly available at `sdp81.strw.leidenuniv.nl`" (6 Conclusions)
- Products in archive: _not stated_
- Missing: Lens-modelling code or its public availability, regularization matrix definition and lambda_S values
- Missing: Complete SIE and shear parameters (only referenced to R15a)
- Missing: Calibrators, CASA task settings, masks, continuum-subtraction and line-free channel choices
- Missing: Exact PDRToolbox grid version and region masks used for resolved fits and f_CII
- Data volume (inferred): Raw measurement sets for three projects (Band 3 ~45 min, Band 8, and ~10 h of LBC data at 7.5 GHz per band) likely ~100-300 GB; the released reconstructed maps are small
- Score (inferred): 2/5, Data are identified by project code and derived maps are released, but the key lens-modelling code is not named or stated as public, imaging and calibration settings are largely unstated, and several choices are inherited from R15a/R15b and alma2015.
- Rediscovery candidate: no, The recipe depends on an unreleased lens-modelling code and on R15a/R15b products, and imaging/calibration details are missing, so the main numeric results cannot be redone from the paper alone.

## Links

- Method: Rybak et al. 2015a (cite: Rybak2015a) (Visibility-plane lens modelling method and lens model adopted here)
- Method: Vegetti & Koopmans 2009 (cite: Vegetti2009) (Bayesian source reconstruction technique extended to interferometric data)
- Method: Kaufman et al. 1999, 2006; Pound & Wolfire 2008 (PDRToolbox models used for the PDR analysis)
- Method: Munoz & Oh 2016 (cite: MunozOh2016) (Thermal-saturation model of the [C II]/FIR deficit)
- Method: ALMA Partnership 2015 (cite: alma2015) (Long Baseline Campaign observations of SDP.81 and CO(10-9) data description)
- Companion: Rybak et al. 2015b (cite: Rybak2015b) (Source-plane CO(5-4) and CO(8-7) reconstructions adopted here)
- Companion: Rybak et al. 2019 (cite: Rybak2019) (Analogous resolved [C II], CO(3-2) and FIR study of two ALESS DSFGs)
- Companion: Zhang et al. 2018 (cite: Zhang2018b) (Herschel photometry and fine-structure line fluxes)
- Companion: Valtchanov et al. 2011 (cite: Valtchanov2011) (Earlier global PDR model and CO(1-0), CO(7-6) data)
- Companion: Lamarche et al. 2018 (cite: Lamarche2018) (Resolved [C II]/FIR deficit in SDP.11)
- Related: ALMA 2014 Long Baseline Campaign (SDP.81 science verification)
- Related: H-ATLAS (Herschel)
- Related: ALESS

## Checks

```json
{
 "quotes": 211,
 "quotes_ok": 211,
 "quote_pass_rate": 1.0,
 "quotes_too_long": 0,
 "unsupported_facts": 0,
 "project_codes": 3,
 "codes_not_in_text": [],
 "codes_not_in_obscore": [],
 "obscore_codes_not_in_card": [],
 "codes_printed_but_missing": [],
 "numeric_results": 23,
 "numeric_problems": 0,
 "fill": {
  "facts": 148,
  "stated": 123,
  "rate": 0.831
 },
 "evidence_ok": true
}
```
