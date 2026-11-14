# Molecular Gas Contents and Scaling Relations for Massive, Passive Galaxies at Intermediate Redshifts from the LEGA-C Survey

`2018ApJ...860..103S` | The Astrophysical Journal 2018 | first author: Spilker, Justin | arXiv: 1805.02667 | DOI: 10.3847/1538-4357/aac438

Card schema 1.0 | model claude-sonnet-5-5 | depth full | type observational_alma_primary

## Science

- Fields: nearby_galaxies, high_z_galaxies
- Question: Do gas scaling relations derived from star-forming galaxies extend to passive galaxies at z~0.7, and what are their molecular gas contents and kinematics?  
  > "The main focus of our work here is to determine whether the scaling relations derived from observations of star-forming galaxies and cosmological simulations can accurately predict or be extrapolated down to passive galaxies at intermediate redshift." (Introduction)
- Target **8 LEGA-C passive galaxies (IDs 74512, 110509, 130284, 132776, 138718, 169076, 210210, 211409)**: coordinates COSMOS field, e.g. ID 74512 at 10h01m42.88s +02d01m21.9s (see Table 1)  
  > "| 74512     | $10^\mathrm{h}01^\mathrm{m}42.88^\mathrm{s}$ | $+02^\circ01{}^\prime21.9{}^{\prime\prime}$ | 0.7330            | 10.96" (Table 1); "Because the LEGA-C survey targets the COSMOS extragalactic survey field, full panchromatic spectral energy distribution (SED) information is available" (2.1 LEGA-C and Selection of Quiescent Galaxies); z/distance z_spec = 0.60-0.75 (Table 1)  
  > "| 74512     | $10^\mathrm{h}01^\mathrm{m}42.88^\mathrm{s}$ | $+02^\circ01{}^\prime21.9{}^{\prime\prime}$ | 0.7330            | 10.96" (Table 1); "Because the LEGA-C survey targets the COSMOS extragalactic survey field, full panchromatic spectral energy distribution (SED) information is available" (2.1 LEGA-C and Selection of Quiescent Galaxies); distance from LEGA-C spectroscopic redshifts  
  > "| 74512     | $10^\mathrm{h}01^\mathrm{m}42.88^\mathrm{s}$ | $+02^\circ01{}^\prime21.9{}^{\prime\prime}$ | 0.7330            | 10.96" (Table 1); "Because the LEGA-C survey targets the COSMOS extragalactic survey field, full panchromatic spectral energy distribution (SED) information is available" (2.1 LEGA-C and Selection of Quiescent Galaxies)

## Data provenance

- ALMA projects: 2016.1.00790.S
- bands: Band 4 (2 mm)  
  > "using the Band 4 (2 mm) receivers (cite: asayama14)" (2.2 ALMA Observations)
- frequencies and spectral setup: One baseband with 7.812 MHz channels (~16 km/s) on CO(2-1); three further 1.875 GHz basebands for continuum  
  > "one baseband with 7.812 MHz channelization ($\approx 16$ $\rm{km\,s}^{-1}$) after correlator pre-averaging by a factor of 8" (2.2 ALMA Observations); "Three further basebands with 1.875 GHz usable bandwidth each were placed to higher frequencies for continuum observations." (2.2 ALMA Observations)
- continuum bandwidth: _not stated_
- arrays: _not stated_
- configurations: compact configuration, ~40 antennas, maximum baselines 272-330 m  
  > "with $\sim$40 antennas separated by maximum baselines ranging from 272–330 m" (2.2 ALMA Observations)
- baselines: _not stated_
- angular resolution: 1.9-2.4 arcsec (~13-17 kpc), natural weighting  
  > "The effective spatial resolution of the data imaged in this way ranges from 1.9–2.4$''$($\approx$13–17 kpc)." (2.2 ALMA Observations)
- max recoverable scale: _not stated_
- sensitivity: rms 132-256 uJy/beam in 100 km/s channels (naturally weighted)  
  > "$^{a}$ ALMA rms sensitivity in 100 $\rm{km\,s}^{-1}$ channels, naturally-weighted images" (Table 1)
- time on source: 37-49 minutes on-source per target; sessions 57-80 min  
  > "Observing sessions varied between 57–80 minutes in duration, with 37–49 minutes spent on-source per target." (2.2 ALMA Observations)
- observing dates: 17 January to 12 March 2017  
  > "in separate observing sessions from 17 January to 12 March 2017" (2.2 ALMA Observations)
- pi or archival as stated: PI program (PI: Spilker); archive checked, no other observations found  
  > "No other observations were found." (2.2 ALMA Observations)
- Line: CO J=2-1 (not stated)
- Other facility **LEGA-C (VLT/VIMOS)**: Spectroscopic redshifts, stellar rotation curves, D_n4000/Hdelta  
  > "20 hour integrations using the VIMOS spectrograph on the Very Large Telescope" (2.1 LEGA-C and Selection of Quiescent Galaxies)
- Other facility **Spitzer/MIPS 24um, UltraVISTA, HST, COSMOS**: Photometry/SEDs for stellar masses and SFRs, morphologies  
  > "SFRs include the unobscured and obscured components based on UV and IR (24 $\mu\rm{m}$) fluxes." (2.1.1 SFR Estimation)
- External data: Comparison samples of gas masses: xCOLDGASS, PHIBSS, Papovich+16, Suess+17  
  > "We include the xCOLDGASS sample (cite: saintonge17), a large sample of galaxies in the local universe" (3.1 Basic Gas Properties) [from (cite: saintonge17); (cite: tacconi13); (cite: papovich16); (cite: suess17)]
- External data: Gas scaling relations  
  > "The relations derived by (cite: scoville17) are based on ALMA observations of long-wavelength dust continuum emission" (4.1 Gas Scaling Relations) [from (cite: scoville17); (cite: tacconi18)]
- External data: EAGLE molecular gas masses for galaxies  
  > "Molecular gas masses for galaxies in the Ref-L100N1504 EAGLE run were calculated by (cite: lagos15; lagos16)" (4.2 Comparison to Cosmological Simulations) [from (cite: lagos15; lagos16)]
- External data: Stellar masses, SFRs, environment overdensities, DR2 catalog values  
  > "the figures and table in this work use values from the updated DR2 catalog (1989 galaxies; Straatman et al., in prep.)" (2.1 LEGA-C and Selection of Quiescent Galaxies) [from (cite: vanderwel16); (cite: muzzin13a); (cite: darvish16)]
- Simulation/model as data: EAGLE Ref-L100N1504 z=0.6 snapshot, 91 massive passive galaxies selected  
  > "resulting in 91 simulated massive, passive galaxies" (4.2 Comparison to Cosmological Simulations)

## Processing

### Calibration

- pipeline or manual: standard ALMA pipeline with manual inspection  
  > "All data were reduced using the standard ALMA pipeline, with manual inspection of the quality of the reduction." (2.2 ALMA Observations)
- casa version: _not stated_
- pipeline version: _not stated_
- archive products used as is: _not stated_
- flux calibrator: Ganymede or J0854+2006 / J1058+0133  
  > "The absolute flux scale was determined using observations of Ganymede or one of J0854+2006 or J1058+0133" (2.2 ALMA Observations)
- flux scale uncertainty: _not stated_
- self calibration: _not stated_

### Imaging

- task: _not stated_
- deconvolver: _not stated_
- weighting robust: natural weighting  
  > "All data were imaged with a natural weighting of the visibilities" (2.2 ALMA Observations)
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

- LEGA-C survey description, sample and catalogs  
  > "The survey is described in detail by (cite: vanderwel16)." (2.1 LEGA-C and Selection of Quiescent Galaxies) [from (cite: vanderwel16)]
- Star-forming sequence definition for selection  
  > "SFR 3–10$\times$ below the $z\sim0.7$ star-forming sequence as defined by (cite: whitaker12)" (2.3 ALMA Selection) [from (cite: whitaker12)]
- alpha_CO = 4.4 and r21 = 0.8 conventions  
  > "we adopt a ‘Milky Way-like’ value, $\ensuremath{\alpha_{\rm{CO}}}= 4.4$ $\rm{M}_\odot$ (K $\rm{km\,s}^{-1}$ pc$^2$)$^{-1}$ (cite: solomon87; bolatto13; sandstrom13)" (2.3 Molecular Gas Masses) [from (cite: solomon87; bolatto13; sandstrom13)]

### Not stated but needed to reproduce (our reading)

- CASA/pipeline version
- Line-free channels and continuum subtraction method
- Image size, cell size, and clean parameters
- Exact tool and procedure for point-source visibility fitting
- Gaussian line-fit procedure details
- Stacking weights and procedure
- Per-target SFRs/stellar masses from DR2 catalog
- Rest frequency of CO(2-1) used and flux scale uncertainty

## Analysis recipe

1. **Select sample**: Select LEGA-C galaxies at z<0.84 with log Mstar>10.8, SFR 3-10x below star-forming sequence, SFR>2.5 Msun/yr; 8 of 65 observed  
  > "This resulted in a sample of 65 galaxies, from which we selected 8 for observation with ALMA" (2.3 ALMA Selection)
   - fitting: _not stated_
   - validation: _not stated_
2. **Image and extract spectra**: Naturally weighted continuum images and cubes; integrated spectra from point-source fits to visibilities, averaging 6 or 12 channels  
  > "We extract integrated spectra for all targets by fitting point source models to the visibility data directly, averaging 6 or 12 channels" (2.2 ALMA Observations)
   - fitting: _not stated_
   - validation: _not stated_
3. **Measure CO fluxes and upper limits**: Fit one or two Gaussians to line profiles; 3 sigma upper limits from noise in 800 km/s wide channels  
  > "Integrated line fluxes are determined by fitting either one or two Gaussian profiles" (2.3 Molecular Gas Masses); "we estimate upper limits on the CO emission by determining the noise in channels 800 $\rm{km\,s}^{-1}$ wide" (2.3 Molecular Gas Masses)
   - fitting: Gaussian profile fits; no sampler stated  
  > "Integrated line fluxes are determined by fitting either one or two Gaussian profiles, also shown in Figure [4](#fig:spectra)." (Molecular Gas Masses)
   - validation: _not stated_
4. **Derive molecular gas masses**: Convert CO luminosity with r21 and alpha_CO; M_H2 scales as (0.8/r21)(alpha_CO/4.4)  
  > "molecular gas masses can be rescaled under different assumptions as $\ensuremath{M_{\rm{H}_2}}(0.8/r_{21})(\ensuremath{\alpha_{\rm{CO}}}/4.4)$" (Table 1)
   - parameter: r21 = 0.8; alpha_CO = 4.4  
  > "In this work, we assume $r_{21}=0.8$." (2.3 Molecular Gas Masses)
   - assumption: Milky Way-like alpha_CO ~50% systematic uncertainty; flat LCDM Om=0.307, H0=67.7  
  > "it does still carry significant systematic uncertainty, likely of order 50%" (2.3 Molecular Gas Masses)
   - fitting: _not stated_
   - validation: Cross-checked with dust-based gas mass from continuum stack  
  > "This independent check indicates that our assumptions about $\alpha_{\rm{CO}}$ are reasonable." (2.4.1 2 mm Continuum Stack)
5. **Stack continuum and CO**: Average image-plane inverted images/cubes of targets (continuum and CO at known redshifts)  
  > "we opt to simply average together inverted images of the targets rather than perform this analysis in the Fourier plane" (2.4.1 2 mm Continuum Stack)
   - parameter: Dust-based M_H2: kappa_235GHz=0.42 cm2/g, Tdust=25 K, GDR=100  
  > "a dust temperature $\ensuremath{T_{\rm{dust}}}= 25$ K, and a gas-to-dust ratio typical of solar metallicity systems, $\ensuremath{\delta_{\rm{GDR}}}= 100$" (2.4.1 2 mm Continuum Stack)
   - fitting: _not stated_
   - validation: Recovered sample-average line flux by stacking only CO-detected sources  
  > "We have also verified that this procedure accurately recovers the sample-average line flux by stacking only the sources individually detected in CO." (2.4.2 CO Spectral Stack)
6. **Compare kinematics of CO and stars**: Image red and blue velocity channels, fit point sources in visibility and image domain, project gradient onto N-S slit and compare with LEGA-C stellar rotation curves  
  > "We fit the red and blue channels of each source in both the visibility and image domains with point source models" (3.2 Molecular and Stellar Dynamics)
   - fitting: _not stated_
   - validation: Verified gradients with narrower velocity channels  
  > "we have verified that the velocity gradients apparent in Figure [6](#fig:chanmaps) are consistent with imaging the data in narrower velocity channels" (3.2 Molecular and Stellar Dynamics)
7. **Compare with scaling relations and EAGLE**: Compare f_H2 and t_dep with Scoville+17 and Tacconi+18 relations and EAGLE galaxies  
  > "we compare the gas fractions and depletion times for our observed sample with two empirical scaling relations from the literature" (4.1 Gas Scaling Relations)
   - fitting: _not stated_
   - validation: _not stated_
8. **Closed-box evolution toy model**: Gas fraction declines from z=0.7 to 0 with constant t_dep and 30% mass return  
  > "we construct a closed-box toy model, in which a galaxy at $z=0.75$ with $\log \ensuremath{M_{\rm{star}}}/\ensuremath{\rm{M}_\odot}=11$ continues to deplete its reservoir of molecular gas" (5.2 Connection to Local Quiescent Galaxies)
   - parameter: f_H2 = 0.03-0.12 initial; t_dep = 0.7-1.3 Gyr  
  > "$\ensuremath{t_{\rm{dep}}}=0.7-1.3$ Gyr, that remain constant over time" (5.2 Connection to Local Quiescent Galaxies)
   - fitting: _not stated_
   - validation: Compared to ATLAS3D and MASSIVE local quiescent galaxies  
  > "we compare to nearby quiescent galaxies with $\log \ensuremath{M_{\rm{star}}}/\ensuremath{\rm{M}_\odot}> 10.7$ selected from the ATLAS$^{\mathrm{3D}}$ and MASSIVE surveys" (Connection to Local Quiescent Galaxies)

## Software


## Numeric results

| quantity | value | uncertainty | units | step | quote |
|---|---|---|---|---|---|
| CO-detected targets | 4 of 8 | not stated | galaxies | 3 | We clearly detect four of the eight targets in CO(2–1) emission. |
| 2 mm continuum stack (all) | 17 | 5 | uJy | 5 | a faint source with $\ensuremath{S_\mathrm{2mm}}= 17 \pm 5$ $\mu\rm{Jy}$ is detected |
| 2 mm stack of CO-detected | 23 | 7 | uJy | 5 | The CO-detected sources are detected in the 2 mm continuum stack with $\ensuremath{S_\mathrm{2mm}}= 23 \pm 7$ $\mu\rm{Jy}$ |
| Dust-based mean M_H2 of CO-detected | 8.8e9 | not stated | Msun | 5 | we find an average molecular gas mass for the CO-detected sources of $8.8 \times 10^9$ $\rm{M}_\odot$ |
| CO stack of non-detections L'CO(2-1) upper limit (3 sigma) | <5.8e8 | not stated | K km/s pc^2 | 5 | $\ensuremath{\rm{L}_{\rm{CO(2-1)}}'}< 5.8 \times 10^8$ K $\rm{km\,s}^{-1}$ pc$^2$ |
| Stack of non-detections M_H2 limit | <3.2e9 | not stated | Msun | 5 | this is equivalent to $\ensuremath{M_{\rm{H}_2}}< 3.2 \times 10^9$ $\rm{M}_\odot$ |
| Stack of non-detections f_H2 limit | <0.016 | not stated | dimensionless | 5 | the resulting upper limit on the gas fraction of these passive sources is $\ensuremath{f_{\rm{H}_2}}=\ensuremath{M_{\rm{H}_2}}/\ensuremath{M_{\rm{star}}}<0.016$ |
| log M_H2 of ID 130284 | 10.00 | 0.06 | log Msun | 4 | / 130284    / $10^\mathrm{h}00^\mathrm{m}13.78^\mathrm{s}$ / $+02^\circ19{}^\prime37.0{}^{\prime\prime}$ / 0.6017            / 10.96                                                        / 6.8               / 151                                              / 0.36 $\pm$ 0.04                / 10.00 $\pm$ 0.06 |
| CO centroid precision of red/blue components | ~0.3 | not stated | arcsec | 6 | the centroids of each velocity component can be determined to $\approx$0.3$''$, on average |

## Qualitative findings

- Detected galaxies have M_H2 ≲1e10 Msun, over an order of magnitude above local early types, with depletion times ≲1-2 Gyr.  
  > "the $\lesssim$1–2 Gyr depletion times are typical of, or even shorter than, galaxies near the star-forming sequence." (3.1 Basic Gas Properties)
- CO and stellar rotation axes are consistent in at least three of four detections.  
  > "the rotational axes of the stellar and molecular components of the CO-detected objects are consistent in at least three of four cases." (3.2 Molecular and Stellar Dynamics)

## Claim tuples

- H: Gas scaling relations from star-forming galaxies extrapolate to passive galaxies at z~0.7 | E: Compare f_H2 and t_dep with Scoville+17 and Tacconi+18 relations | R: Relations over-predict f_H2 and t_dep, especially for non-detections (stack f_gas factor 5 lower, t_dep factor 4) | F: Break or increased scatter in scaling relations at low sSFR | **supported**
- H: Molecular gas was accreted externally after quenching | E: Compare CO velocity gradients with LEGA-C stellar rotation | R: Axes consistent in 3 of 4 detections | F: Gas not likely accreted after quenching | **partially**
- H: These galaxies evolve into local massive early types without further gas accretion | E: Closed-box toy model with low-level star formation | R: Reproduces range of f_H2 in nearby passive galaxies | F: No need for extra accretion or dynamical stabilization | **supported**

## Reasoning

- Why this data: _not stated_
- Why this method: Natural weighting maximizes sensitivity to faint emission  
  > "which maximizes sensitivity to faint emission in exchange for slightly lower spatial resolution" (2.2 ALMA Observations)
- How they decided it was enough: _not stated_
- Limitation (authors): Small sample of 8; alpha_CO systematic uncertainty ~50%; SFR from 24um may be overestimated up to ~2x  
  > "With only 8 target galaxies in total, we cannot draw strong conclusions on this point." (3.1 Basic Gas Properties)
- Caveat (inferred, ours): Single alpha_CO assumed for all galaxies despite no metallicity measurement
- Caveat (inferred, ours): SFR uncertain due to 24um contamination
- Caveat (inferred, ours): Stacking done in image plane without weights stated
- Caveat (inferred, ours): Selection and non-detection interpretation limited by small N

## Reproducibility

- Data public (paper): ALMA project 2016.1.00790.S acknowledged; archive checked  
  > "This paper makes use of the following ALMA data: ADS/JAO.ALMA#2016.1.00790.S." (Acknowledgments)
- Products in archive: _not stated_
- Missing: Imaging parameters (cell, size, channel selection)
- Missing: CASA version
- Missing: Exact SFR and Mstar per galaxy from DR2 catalog and sSFR sequence formulation
- Missing: Stacking details
- Data volume (inferred): ~10-50 GB raw for 8 short Band 4 compact-array observations
- Score (inferred): 3/5, Data public and recipe simple with tabulated results, but imaging and software details are unstated.
- Rediscovery candidate: no, Software and imaging parameters are not stated, and the comparisons depend on external catalogs and models.

## Links

- Method: (cite: vanderwel16) (LEGA-C survey description)
- Companion: (cite: suess17) (ALMA observations of two post-starburst galaxies at z~0.7)
- Companion: (cite: wu18) (LEGA-C stellar age distributions)
- Related: LEGA-C
- Related: COSMOS
- Related: EAGLE
- Related: xCOLDGASS
- Related: PHIBSS

## Checks

```json
{
 "quotes": 67,
 "quotes_ok": 67,
 "quote_pass_rate": 1.0,
 "quotes_too_long": 0,
 "unsupported_facts": 0,
 "project_codes": 1,
 "codes_not_in_text": [],
 "codes_not_in_obscore": [],
 "obscore_codes_not_in_card": [],
 "codes_printed_but_missing": [],
 "numeric_results": 9,
 "numeric_problems": 0,
 "fill": {
  "facts": 84,
  "stated": 47,
  "rate": 0.56
 },
 "evidence_ok": true
}
```
