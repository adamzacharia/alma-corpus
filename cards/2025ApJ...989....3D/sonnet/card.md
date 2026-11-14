# The ALMA Survey of Gas Evolution of PROtoplanetary Disks (AGE-PRO). III. Dust and Gas Disk Properties in the Lupus Star-forming Region

`2025ApJ...989....3D` | The Astrophysical Journal 2025 | first author: Deng, Dingshan | arXiv: 2506.10734 | DOI: 10.3847/1538-4357/add43a

Card schema 1.0 | model claude-sonnet-5-5 | depth full | type large_program_or_survey

## Science

- Fields: protoplanetary_disks, astrochemistry
- Question: What are the dust and gas disk masses, sizes and line-flux correlations of 10 Lupus disks around M3-K6 stars observed in the AGE-PRO Large Program?  
  > "We find strong correlations between the CO isotopologue line fluxes and the continuum flux densities." (abstract); "We estimate gas disk masses by comparing $\mathrm{C^{18}O}$ $J$=2-1 line fluxes with those predicted by the limited grid of self-consistent disk models of (cite: ruaud_C18O_2022)." (abstract)
- Target **Lupus 1-10 (Sz65, Sz71, J16124373-3815031, Sz72, Sz77, J16085324-3914401, Sz131, Sz66, Sz95, V1094Sco)**: coordinates Table 1 lists R.A./Decl. per source, e.g. Sz65 15:39:27.753 -34:46:17.577  
  > "| 1 | Sz65 | 15:39:27.753 | -34:46:17.577 | 153.00 | I | K7 | 4060 | 0.869 | 0.6 | -9.480 |" (Table 1); "Geometric distances are from *Gaia/r*-band (cite: Bailer-Jones_2021AJ_Gaia_geodistance)." (Table 1); z/distance 153.00-161.48 pc  
  > "| 1 | Sz65 | 15:39:27.753 | -34:46:17.577 | 153.00 | I | K7 | 4060 | 0.869 | 0.6 | -9.480 |" (Table 1); "Geometric distances are from *Gaia/r*-band (cite: Bailer-Jones_2021AJ_Gaia_geodistance)." (Table 1); distance from Gaia geometric distances (Bailer-Jones et al. 2021)  
  > "| 1 | Sz65 | 15:39:27.753 | -34:46:17.577 | 153.00 | I | K7 | 4060 | 0.869 | 0.6 | -9.480 |" (Table 1); "Geometric distances are from *Gaia/r*-band (cite: Bailer-Jones_2021AJ_Gaia_geodistance)." (Table 1)

## Data provenance

- ALMA projects: 2021.1.00128.L, 2017.1.00569.S, 2019.1.01135.S, 2019.2.00054.S
- bands: Band 6 (234 GHz, 1.28 mm) and Band 7 (285 GHz, 1.05 mm)  
  > "ALMA 12 m array in Band 6 (234 GHz, or 1.28 mm)" (2.2 Observations); "Targets were also observed in Band 7 (285 GHz, or 1.05 mm)" (2.2 Observations)
- frequencies and spectral setup: Band 6: continuum, 12CO, 13CO, C18O 2-1 plus H2CO, DCN, N2D+; Band 7: N2H+ 3-2 plus DCO+, C34S, DCN, H2CO  
  > "our Band 6 setup covers the $\mathrm{{}^{12}CO}$, $\mathrm{{}^{13}CO}$ and $\mathrm{C^{18}O}$ $J$=2-1 lines, while our Band 7 setup covers the $\mathrm{N_2H^+}$ $J$=3-2 line" (abstract)
- continuum bandwidth: _not stated_
- arrays: ALMA 12 m array  
  > "observed between December 2021 and June 2022 with the ALMA 12 m array in Band 6" (2.2 Observations)
- configurations: Band 6: C43-2 (short) and C43-5 (long); Band 7: C43-3 only  
  > "using the C43-2 (15-314 m) and C43-5 (15-1400 m) array configurations, which we refer to as ‘short’ and ‘long’ baselines, respectively." (2.2 Observations); "in April 2022 using only the C43-3 (15-500 m) configuration" (2.2 Observations)
- baselines: C43-2 15-314 m; C43-5 15-1400 m; C43-3 15-500 m  
  > "C43-2 (15-314 m) and C43-5 (15-1400 m)" (2.2 Observations)
- angular resolution: ~0.35'' continuum Band 6, ~0.70'' Band 7; weak lines ~0.50'' (B6), ~0.80'' (B7) at robust 1.0  
  > "a Briggs robust parameter of 0.5 to achieve an angular resolution of $\sim 0.35\,\ensuremath{''}$ for Band 6 and $\sim 0.70\,\ensuremath{''}$ for Band 7." (3.2 Imaging Strategy)
- max recoverable scale: _not stated_
- sensitivity: continuum ~0.1 mJy; 12CO ~7.0, 13CO and C18O ~4.0, N2H+ ~3.0 mJy km/s  
  > "typical noise level of $\sigma \sim 0.1 \,\mathrm{mJy}$ generated with robust = 0.5" (3.2 Imaging Strategy)
- time on source: _not stated_
- observing dates: Dec 2021 - Jun 2022 (AGE-PRO); archival Aug 2018 and Oct-Nov 2019  
  > "Our targets were observed between December 2021 and June 2022" (2.2 Observations)
- pi or archival as stated: _not stated_
- Line: 12CO J=2-1 (230.5 GHz)
- Line: 13CO J=2-1 (220.3 GHz)
- Line: C18O J=2-1 (219.6 GHz)
- Line: N2H+ J=3-2 (279.5 GHz)
- External data: Stellar Teff, L*, A_V and accretion rates (rescaled to Gaia DR3 distances)  
  > "are from (cite: Manara_2023_PPVII), summarizing (cite: alcala_x-shooter_2014; alcala_x-shooter_2017; alcala_hst_2019; Herczeg_n_Hillenbrand_TTauri_SpT)" (Table 1) [from (cite: Manara_2023_PPVII)]
- External data: Thermochemical model grid of C18O line luminosities vs dust mass  
  > "Figure [13](#fig:derive_Mgas_ruaud) shows the AGE-PRO $\mathrm{C^{18}O}\,(2-1)$ line luminosities ($L_\mathrm{C^{18}O\,(2-1)}$) with model predictions from (cite: ruaud_C18O_2022)" (5.3) [from (cite: ruaud_C18O_2022)]
- External data: Inclination and position angles from visibility fitting  
  > "we adopt the values from (cite: Vioque_AGEPRO_X_dust_disks) for consistency among the AGE-PRO papers." (3.2 Imaging Strategy) [from (cite: Vioque_AGEPRO_X_dust_disks)]
- External data: Gas masses from DALI models for comparison  
  > "The second set is from an accompanying AGE-PRO paper, (cite: Trapman_AGEPRO_V_gas_masses) (blue points)" (5.3) [from (cite: Trapman_AGEPRO_V_gas_masses)]
- Simulation/model as data: Ruaud et al. 2022 thermochemical disk model tracks (Rc=30 and 100 AU) used to scale C18O luminosity to gas mass  
  > "The two sets of models correspond to different disk sizes, one set with outer radius $R_{\rm out} = 100\,{\rm AU}$ and critical radius $R_c = 30\,{\rm AU}$" (5.3)

## Processing

### Calibration

- pipeline or manual: ALMA staff CASA pipeline per execution block, then self-calibration of continuum  
  > "The execution blocks were initially calibrated individually by the ALMA staff using the CASA pipeline version `6.2.1-7-pipeline`" (3.1 Calibration Strategy)
- casa version: _not stated_
- pipeline version: 6.2.1-7-pipeline (Band 6 and 7); 5.6.1-8-pipeline for archival Band 7  
  > "`6.2.1-7-pipeline` for both short and long baseline Band 6 and Band 7 data, and `5.6.1-8-pipeline` for archival Band 7 data." (3.1 Calibration Strategy)
- archive products used as is: _not stated_
- flux calibrator: _not stated_
- flux scale uncertainty: _not stated_
- self calibration: Phase-only iterations from solint 300s or inf, then one amplitude round; SNR improved ~50%  
  > "We start with a large solution interval (`solint=‘300s’` or `‘inf’`)" (3.1 Calibration Strategy); "Self-calibration improves the SNR for the disks in AGE-PRO Lupus sample by $\sim 50\%$ within a few iterations." (3.1 Calibration Strategy)

### Imaging

- task: tclean; cvel2 for velocity regridding  
  > "we use the `tclean` task with an elliptical mask" (3.2 Imaging Strategy)
- deconvolver: _not stated_
- weighting robust: robust 0.5 for continuum and 12CO; robust 1.0 for 13CO, C18O, N2H+ and other lines  
  > "a robust value of 1.0 is chosen to generate images for other lines." (3.2 Imaging Strategy)
- uv taper: uvrange '>50klambda' for Band 6 (except Lupus 10); uvtaper for circularized beam  
  > "We also use the constraint of `uvrange = ‘>50klambda’` for Band 6 data" (3.2 Imaging Strategy)
- cell size: _not stated_
- image size: _not stated_
- masking: Interactive manual Keplerian masks with inflated Mstar, Rmax and emitting heights (z0/r1 0.23, 0.15, 0.10)  
  > "The `CLEAN` masks for the `tclean` tasks are adjusted manually in `interactive` mode and checked channel by channel by visual inspection" (3.2 Imaging Strategy)
- multiscale scales: _not stated_
- continuum subtraction: Continuum subtracted from self-calibrated visibilities  
  > "Then we subtract the continuum from these aligned and self-calibrated visibilities" (3.1 Calibration Strategy)
- line free channels: Channels between -19.0 and 21.0 km/s flagged as line  
  > "we flag channels with velocities between -19.0 and 21.0 km s$^{-1}$ as spectral lines" (3.1 Calibration Strategy)
- primary beam correction: _not stated_
- array combination: Short-baseline self-calibrated data concatenated with long baseline, then jointly self-calibrated  
  > "we concatenate the self-calibrated short-baseline data with the long-baseline data." (3.1 Calibration Strategy)
- smoothing: imsmooth to perfectly circularize beam after uv taper  
  > "then we apply `imsmooth` to make a perfectly circularized image." (3.2 Imaging Strategy)
- final beam: _not stated_
- final rms: Continuum ~0.1 mJy  
  > "typical noise level of $\sigma \sim 0.1 \,\mathrm{mJy}$ generated with robust = 0.5" (3.2 Imaging Strategy)

### Inherited from earlier work

- Data reduction procedure and scripts  
  > "The data reduction procedure is described in detail in the overview paper (cite: Zhang_AGEPRO_I_overview)" (3. Data Reduction) [from (cite: Zhang_AGEPRO_I_overview)]
- CLEAN stopping criterion rationale  
  > "More details on why we choose this `CLEAN` criterion is discussed in the accompanying AGE-PRO overview paper (cite: Zhang_AGEPRO_I_overview)." (3.2 Imaging Strategy) [from (cite: Zhang_AGEPRO_I_overview)]
- Curve-of-growth flux and radius method  
  > "measured from the curve-of-growth method following the same method adopted in the literature" (4.3) [from (cite: Ansdell_2016ApJ_Lupus; Ansdell_Lupus_2018ApJ; Andrews_DSHARP_2018ApJ...869L..41A; Sanchis_Lupus_radius_2021A&A...649A..19S)]
- Bayesian stellar mass/age inference  
  > "We adopt a Bayesian framework as in (cite: Pascucci2016_massrelation)" (2.1) [from (cite: Pascucci2016_massrelation)]
- Kendall tau test with censored data  
  > "To test whether correlations are present we follow (cite: pascucci_largedisks_2023)" (5.1) [from (cite: pascucci_largedisks_2023)]
- Spectral index error procedure  
  > "The errors are estimated with the same procedure described in (cite: Chiang_spectralindex_2012)" (4.3) [from (cite: Chiang_spectralindex_2012)]

### Not stated but needed to reproduce (our reading)

- Exact self-calibration solint sequence and number of iterations per source
- Image size and cell size for tclean
- Multiscale scales or deconvolver choice
- Spectral windows used and exact channel flags per execution
- Flux calibrator names and flux scale uncertainty
- Final per-source beam sizes for non-circularized images
- Details of aperture selection for 13CO/C18O spectra
- Uncertainty prior details for stellar mass/age grids beyond uniform priors

## Analysis recipe

1. **Derive stellar masses and ages**: Bayesian inference on HR-diagram with evolutionary tracks  
  > "we use non-magnetic tracks: from (cite: baraffe_stellar_model_2015) for targets with $T_{\rm eff} < 3900\,{\rm K}$ and from (cite: Feiden_YSO_tracks_2016) for hotter stars" (2.1)
   - software: ysoisochrone
   - parameter: uniform priors on model properties; Teff and L* uncertainties from Alcala et al.  
  > "The conditional likelihood function assumes uniform priors on the model properties" (2.1)
   - fitting: _not stated_
   - validation: Masses consistent with literature  
  > "The $M_{\star}$ estimated here are consistent with the ones reported in the literature" (2.1)
2. **Calibrate and self-calibrate continuum visibilities**: Pipeline calibration, flag line channels, average to 125 MHz, phase then amplitude self-cal, apply to line data, subtract continuum  
  > "averaging into a maximum 125 MHz channel width" (3.1 Calibration Strategy)
   - software: CASA
   - fitting: _not stated_
   - validation: _not stated_
3. **Image continuum and lines**: tclean with Keplerian masks, robust 0.5 or 1.0, circularized versions for radii  
  > "The line images are then produced with the `tclean` task." (3.2 Imaging Strategy)
   - software: CASA, tclean, cvel2
   - parameter: velocity spacing 0.1 km/s for 12CO, 0.2 km/s other lines; CLEAN to 1 sigma  
  > "The emission is `CLEANed` down to $1 \times \mathrm{RMS}$" (3.2 Imaging Strategy)
   - fitting: _not stated_
   - validation: _not stated_
4. **Check detections with spectra and stacked profiles**: Velocity-stacked spectra and radial profiles de-projected with disk geometry  
  > "We also use `GoFish` code (cite: GoFish) to generate: i) the velocity-stacked spectra" (4.1 Band 6 Images)
   - software: GoFish
   - fitting: _not stated_
   - validation: _not stated_
5. **Measure fluxes and radii**: Curve-of-growth on moment 0 maps with elliptical apertures; R68 and R90; cloud-contamination correction using uncontaminated half doubled for Lupus 2, 3, 6  
  > "We report the $R\mathrm{_{68}}$ and $R\mathrm{_{90}}$ at the radius where the curve-of-growth flux is 68% and 90% of the total flux." (4.3)
   - software: bettermoments
   - parameter: Rmax enlarged 1.5x for moment 0 masks  
  > "but with $1.5\times$ larger $R_\mathrm{max}$ to make sure all the emission is included" (4.3)
   - fitting: _not stated_
   - validation: RMS uncertainties checked by bootstrapping (N=10^4) on Band 6 CO cubes  
  > "We bootstrap the emission-free part of the datacube for $N=10^{4}$ times" (Appendix 11)
6. **Derive dust masses and spectral indices**: Optically thin M_dust = d^2 F / (B_nu(T) kappa); alpha_mm from 234 and 285 GHz  
  > "assuming the dust continuum fluxes are optically thin and derive the dust disk masses from the equation" (4.3)
   - assumption: T_dust = 20 K, kappa = 2.3 (nu/230 GHz) cm^2/g  
  > "We adopt the average dust temperature of 20 K, and the dust opacity as $\kappa_\nu = 2.3\,(\nu/{\rm 230\,GHz})\,{\rm cm^2\,g^{-1}}$." (4.3)
   - fitting: _not stated_
   - validation: _not stated_
7. **Test flux correlations**: Kendall tau with censored data including uncertainties and upper limits  
  > "use the `pymccorrelation` routine v0.2.5 which carries out the non-parametric Kendall’s $\tau$ test with censored data" (5.1)
   - software: pymccorrelation
   - fitting: _not stated_
   - validation: _not stated_
8. **Estimate gas disk masses from C18O luminosity**: Linear scaling of Ruaud et al. 2022 track at same dust mass: Mgas = Mgas,model x L_obs/L_model; Rc=100 AU model for Lupus 1, 2, 10, Rc=30 AU for others  
  > "we linearly scale the model track that has the same dust disk mass to match each source to derive the gas disk masses" (5.3)
   - parameter: Uncertainties assigned manually as x3 and x1/3  
  > "with the upper and lower limits of $M_{\rm gas, derived} \times 3$ and $\times 1/3$" (5.3)
   - fitting: _not stated_
   - validation: Compared with DALI masses of Miotello 2017 and Trapman et al. 2025  
  > "there is good agreement for the mass estimates in (cite: Trapman_AGEPRO_V_gas_masses) and the values inferred from the (cite: ruaud_C18O_2022) tracks" (5.3)

## Software

- **CASA** pipeline 6.2.1-7 and 5.6.1-8: Calibration and imaging (tclean, cvel2, uvtaper, imsmooth)  
  > "using the CASA pipeline version `6.2.1-7-pipeline`" (3.1 Calibration Strategy)
- **ysoisochrone** : Stellar mass and age estimates  
  > "we use a new `Python` package `ysoisochrone`" (2.1)
- **GoFish** : Velocity-stacked spectra and radial profiles  
  > "We also use `GoFish` code" (4.1 Band 6 Images)
- **bettermoments** : First-moment maps and bootstrapping collapse  
  > "Here we use the `bettermoments`" (Appendix 8)
- **pymccorrelation** v0.2.5: Kendall tau correlation tests with censored data  
  > "use the `pymccorrelation` routine v0.2.5" (5.1)
- **DALI** : Thermochemical models used by comparison works  
  > "both based on `DALI` (`DustAndLInes`) thermochemical models" (5.3)

## Numeric results

| quantity | value | uncertainty | units | step | quote |
|---|---|---|---|---|---|
| Band 6 234 GHz continuum flux, Lupus 10 | 220.2 | 0.5 | mJy | 5 | / Lupus 10 / 220.2$\pm$0.5 / 382.7$\pm$0.1 / 2.80$\pm$0.01 / 149.32 / |
| Dust mass, Lupus 10 | 149.32 | not stated | M_earth | 6 | / Lupus 10 / 220.2$\pm$0.5 / 382.7$\pm$0.1 / 2.80$\pm$0.01 / 149.32 / |
| C18O 2-1 flux, Lupus 10 | 970.0 | 21.5 | mJy km/s | 5 | 970.0$\pm$21.5$^{d}$ |
| N2H+ 3-2 flux, Lupus 2 | 288.2 | 6.4 | mJy km/s | 5 | / Lupus 2 / 76.4$\pm$0.1 / 109.4$\pm$0.1 / 1.83$\pm$0.01 / 49.96 / 2602.3$\pm$10.4 / 3359.2$\pm$9.0 / 574.4$\pm$9.1 / 77.0$\pm$6.1 / 288.2$\pm$6.4 / |
| Spectral index, Lupus 1 after correction | ~2.0 (Band 7 archival flux corrected by factor 1.22) | not stated | dimensionless | 6 | We find its flux density is off by a factor of 1.22 based on the analysis on Lupus 8 |
| Gas/dust radius ratio for Lupus 2 and 10 | ~2 | not stated | dimensionless | 5 | their CO gas radii are about two times their dust radii (this is true for both $R_{68}$ and $R_{90}$) |
| Kendall p, C18O vs 234 GHz continuum | 2.47 | not stated | percent | 7 | positively correlated with $F_{\rm 234\,GHz\,cont.}$ with $p \sim 2.47\%$ |
| Detection rate of 13CO / C18O vs earlier Band 6 survey | 10% to 100% and 0% to 90% | not stated | percent | 5 | AGE-PRO increases the detection rates of the rare isotopologue $\mathrm{{}^{13}CO}$ and $\mathrm{C^{18}O}$ from 10% to 100% and from 0% to 90%, respectively. |

## Qualitative findings

- AGE-PRO Lupus sample is representative of M3-K6 Lupus disks (K-S tests)  
  > "suggesting that the AGE-PRO sample is representative of the Lupus disks in the M3-K6 SpT range." (2.1)
- Lupus 3 is an outlier, possibly CO depleted  
  > "Lupus 3 shows enhanced $\mathrm{N_2H^+}$ emission and may be depleted in CO." (Summary)
- Gas-to-dust mass ratios between 10-100  
  > "gas-to-dust mass ratios are between $10-100$ in the AGE-PRO Lupus sample." (abstract)

## Claim tuples

- H: Are CO isotopologue fluxes correlated with continuum flux? | E: Kendall tau with censored data on Band 6 and 7 fluxes | R: Positive correlations, p<1% for 12CO and 13CO; p~2.47% for C18O | F: Strong correlations between CO line fluxes and continuum | **supported**
- H: Do Lupus disks have similar CO abundance? | E: Compare C18O and N2H+ fluxes | R: Correlation with p<1% when excluding Lupus 3 | F: Similar CO abundance except Lupus 3 | **partially**
- H: Is there significant radial drift in the resolved disks? | E: Compare 12CO and continuum R68 and R90 for Lupus 2 and 10 | R: R_gas ~ 2 R_dust | F: No evidence of significant radial drift for large disks | **supported**
- H: Do C18O-based gas masses agree with Trapman et al. DALI masses? | E: Scale Ruaud et al. tracks to C18O luminosities | R: Good agreement for massive disks; differences below ~5x for small ones | F: Consistent within uncertainties | **supported**

## Reasoning

- Why this data: _not stated_
- Why this method: Robust 1.0 for weak lines to boost SNR and total fluxes  
  > "to boost the SNR and provide more accurate total fluxes, a robust value of 1.0 is chosen to generate images for other lines." (3.2 Imaging Strategy)
- Alternative: Robust 0.5 for weak lines rejected for low SNR  
  > "the robust value of 0.5 resulted in a low SNR" (3.2 Imaging Strategy)
- How they decided it was enough: _not stated_
- Limitation (authors): Radii are image-plane and not beam-deconvolved, so upper limits for unresolved disks  
  > "the AGE-PRO radii summarized here should be considered upper limits for unresolved disks" (5. Discussion)
- Limitation (authors): Gas mass uncertainties assigned manually from sparse model tracks  
  > "The uncertainties of these estimated masses are manually assigned to cover nearly an order of magnitude" (5.3)
- Caveat (inferred, ours): Gas masses rest on a very sparse model grid with arbitrary factor-3 uncertainties
- Caveat (inferred, ours): Cloud contamination correction (doubling one half) is crude
- Caveat (inferred, ours): Optically thin dust assumption with fixed 20 K temperature
- Caveat (inferred, ours): Only 10 sources; correlation significance sensitive to outlier Lupus 3 and upper limits

## Reproducibility

- Data public (paper): Products and scripts on AGE-PRO website; archival data from ALMA  
  > "The data products, continuum+line measurement sets and data reduction scripts are available for download from the AGE-PRO website." (3.1 Calibration Strategy)
- Products in archive: _not stated_
- Code: Bootstrapping script released on Zenodo; data reduction scripts on AGE-PRO website  
  > "We provide the `Python` script [^7](cite: trapman_2025_ageproobs_pythoncode) to the community" (Appendix 11)
- Missing: Image/cell sizes and exact tclean parameters
- Missing: Self-calibration per-source details
- Missing: Ruaud et al. 2022 model grid values
- Missing: Exact apertures used
- Data volume (inferred): Several hundred GB raw for ~20+ execution blocks; ~tens of GB with calibrated products
- Score (inferred): 6/5, Data and scripts are public and the flux methods are clear, but many tclean and self-cal settings sit in the overview paper or scripts and the gas masses depend on an external model grid.
- Rediscovery candidate: yes, Data are public, the flux measurement recipe is clear and results are numeric (fluxes, radii, dust masses).

## Links

- Method: (cite: Zhang_AGEPRO_I_overview) (Data reduction and curve-of-growth details)
- Method: (cite: Trapman_2025_ageproobs_pythoncode) (Bootstrapping flux uncertainty code)
- Companion: (cite: Trapman_AGEPRO_V_gas_masses) (DALI gas masses compared here)
- Companion: (cite: Vioque_AGEPRO_X_dust_disks) (Dust disk geometry and radii from visibility fitting)
- Companion: (cite: Trapman_AGEPRO_XI_gas_disk_sizes) (Beam-deconvolved gas sizes)
- Companion: (cite: Kurtovic_AGEPRO_VI_DustEvolution) (Dust evolution from spectral indices)
- Related: AGE-PRO
- Related: Ophiuchus (AGE-PRO II)
- Related: Upper Sco (AGE-PRO IV)

## Checks

```json
{
 "quotes": 94,
 "quotes_ok": 94,
 "quote_pass_rate": 1.0,
 "quotes_too_long": 0,
 "unsupported_facts": 0,
 "project_codes": 4,
 "codes_not_in_text": [],
 "codes_not_in_obscore": [],
 "obscore_codes_not_in_card": [],
 "codes_printed_but_missing": [],
 "numeric_results": 8,
 "numeric_problems": 0,
 "fill": {
  "facts": 96,
  "stated": 66,
  "rate": 0.688
 },
 "evidence_ok": true
}
```
