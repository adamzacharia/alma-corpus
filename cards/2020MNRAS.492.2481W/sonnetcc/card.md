# Colliding winds in and around the stellar group IRS 13E at the galactic centre

`2020MNRAS.492.2481W` | Monthly Notices of the Royal Astronomical Society 2020 | first author: Wang, Q. Daniel | arXiv: 1912.12344 | DOI: 10.1093/mnras/stz3624

Card schema 1.0 | model claude-sonnet-5-5-claude-code | depth light | type multi_facility_alma_minor

## Science

- Fields: milky_way_ism, stellar_physics
- Question: Is the X-ray and mm emission of the IRS 13E stellar group at the Galactic centre explained by colliding winds of its Wolf-Rayet stars and by the group colliding with the minispiral bar, without needing an intermediate-mass black hole?  
  > "The presence of an IMBH, while favorable to keep the stars bound together, is not necessary to explain the observed stellar and gas properties of IRS 13E." (abstract); "Here we attempt to address these issues about the nature of IRS 13E and its interplay with the environment, based on hydrodynamic simulations and multi-wavelength observations." (1 Introduction)
- Target **IRS 13E**: coordinates _not stated_; z/distance 8 kpc (adopted Galactic centre distance)  
  > "IRS 13E is an enigmatic compact group of massive stars located in projection only 3.6$''$ away from Sgr A\*." (abstract); "(1”=0.039 pc at our adopted GC distance $D=8$ kpc)" (1 Introduction); distance from adopted value, no citation given  
  > "IRS 13E is an enigmatic compact group of massive stars located in projection only 3.6$''$ away from Sgr A\*." (abstract); "(1”=0.039 pc at our adopted GC distance $D=8$ kpc)" (1 Introduction)

## Data provenance

- ALMA projects: 2016.1.0087.S, 2016.1.00870.S
- bands: Band 6  
  > "the present study primarily uses the ALMA band-6 observation taken in May and July, 2017" (6.1 Description of ALMA observations and data processing)
- frequencies and spectral setup: H30alpha cube with 22 km/s spectral resolution  
  > "The final H30$\alpha$ data cube has a spectral resolution of $22~{\rm~km~s^{-1}}$" (6.1 Description of ALMA observations and data processing)
- continuum bandwidth: _not stated_
- arrays: _not stated_
- configurations: _not stated_
- baselines: _not stated_
- angular resolution: 0.22'' x 0.13'' (FWHM) synthesized beam  
  > "The achieved synthesized beam of the observation is $0.22\ensuremath{''}\times 0.13\ensuremath{''}$ (FWHM)." (6.1 Description of ALMA observations and data processing)
- max recoverable scale: _not stated_
- sensitivity: channel noise ~0.08 mJy/beam; moment 0 noise ~0.04 Jy/beam km/s; continuum noise ~0.1 mJy/beam  
  > "a channel noise of $\sigma_{\rm ch}\approx0.08 {\rm~mJy~beam^{-1}}$, estimated with line-free channels and regions." (6.1 Description of ALMA observations and data processing); "while the continuum emission has $\sigma_{\rm cont}\approx 0.1 {\rm~mJy~beam^{-1}}$." (6.1 Description of ALMA observations and data processing)
- time on source: _not stated_
- observing dates: May and July 2017  
  > "the present study primarily uses the ALMA band-6 observation taken in May and July, 2017" (6.1 Description of ALMA observations and data processing)
- pi or archival as stated: Project PI Elena Murchikova, focused on the accretion flow toward Sgr A*; no earlier publication used this observation  
  > "which is focused on the accretion flow toward Sgr A\* (PI: Elena Murchikova)" (6.1 Description of ALMA observations and data processing); "No existing publication has used this observation" (6.1 Description of ALMA observations and data processing)
- Line: hydrogen H30alpha recombination line (not stated)
- Other facility **Chandra ACIS (archival)**: 108 archival observations (45 ACIS-I, 38 ACIS-S/HETG 0th order, 25 ACIS-S) for X-ray imaging and spectra of IRS 13E  
  > "The first set, consisting of 45 separate observations (1.5 Ms total exposure) taken before 2012, had the Advanced CCD Imaging Spectrometer-Imaging (ACIS-I) on axis." (2 Observations and Data Reduction); "based on the archival  observations with a total of 5.3 Ms exposure time" (1 Introduction)
- Other facility **Pa-alpha map of the GC (cite: wang10)**: Shell-like warm gas structure around IRS 13E seen in Pa-alpha  
  > "In the hydrogen Pa-$\alpha$ line emission map of the GC (cite: wang10), we notice a shell-like structure around IRS 13E" (8.3 Emission structures around IRS 13E)
- Other facility **VLA**: Proper motions of gas blobs near IRS 13E, from the literature  
  > "we use proper motion measurements of various thermal gas blobs in and around IRS 13E (cite: zhao09)" (8.1 Kinematics of IRS 13E and its surrounding medium)
- External data: Stellar proper motions and line-of-sight velocities of E1-E4 (Table 1)  
  > "The measurements for E1-4 are from Table 1 and Appendix B of (cite: fritz10)." (Table 1 note) [from (cite: fritz10)]
- External data: VLA proper motions of thermal gas blobs used for the bar transverse velocity  
  > "we use proper motion measurements of various thermal gas blobs in and around IRS 13E (cite: zhao09)" (8.1 Kinematics of IRS 13E and its surrounding medium) [from (cite: zhao09)]
- External data: He/H ratio and alpha(nu,Te) factor used in the electron temperature formula  
  > "$N(\rm He)/N(\rm H) \sim 0.08$ and $\alpha(\nu,T_{\rm e})\sim 0.85$ at $\nu=232$ GHz and $T_{\rm e} \sim 10^4$ K (cite: mezger67)" (8.4 Physical properties of warm ionized gas in IRS 13E) [from (cite: mezger67)]
- External data: H30alpha emissivity 1.25e-31 erg/s  
  > "the H30$\alpha$ emissivity $\epsilon_{\rm H30\alpha}=1.25\times 10^{-31} \rm~erg~s^{-1}$ for $T_{\rm e}=10^4$ K and $n_{\rm e}=10^4\sim 10^7 \rm~cm^{-3}$ (cite: storey95)" (8.4 Physical properties of warm ionized gas in IRS 13E) [from (cite: storey95)]
- External data: Kinematic ring model of the minispiral bar, position angle 25 deg  
  > "(cite: liszt03) shows that the bar can be reasonably well represented by a kinematic model of a series of thin co-planar rings rotating at the local circular velocity around Sgr A\*." (8.1 Kinematics of IRS 13E and its surrounding medium) [from (cite: liszt03)]
- Simulation/model as data: Smoothed particle hydrodynamic simulations of 25 WR stars and their winds around Sgr A*, updated with tuned wind parameters for the two WR stars of IRS 13E and compared with Chandra data  
  > "(cite: cuadra08; cuadra15) performed smoothed particle hydrodynamic simulations of the central 25 WR stars and their stellar winds within 1 pc of the SMBH." (5 Hydrodynamic simulations); "We conduct multiple simulations tuned to match the  data of IRS 13E." (5 Hydrodynamic simulations)

## Processing

### Calibration

- pipeline or manual: _not stated_
- casa version: CASA 5.1.1, standard data processing  
  > "We use the Common Astronomy Software Applications package (CASA) version 5.1.1 for standard data processing." (6.1 Description of ALMA observations and data processing)
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
- primary beam correction: applied to all ALMA images  
  > "We apply the primary beam correction for all the ALMA images presented in the present work." (6.1 Description of ALMA observations and data processing)
- array combination: _not stated_
- smoothing: _not stated_
- final beam: 0.22'' x 0.13'' (FWHM)  
  > "The achieved synthesized beam of the observation is $0.22\ensuremath{''}\times 0.13\ensuremath{''}$ (FWHM)." (6.1 Description of ALMA observations and data processing)
- final rms: channel noise ~0.08 mJy/beam, continuum ~0.1 mJy/beam, moment 0 ~0.04 Jy/beam km/s  
  > "a channel noise of $\sigma_{\rm ch}\approx0.08 {\rm~mJy~beam^{-1}}$, estimated with line-free channels and regions." (6.1 Description of ALMA observations and data processing); "while the continuum emission has $\sigma_{\rm cont}\approx 0.1 {\rm~mJy~beam^{-1}}$." (6.1 Description of ALMA observations and data processing)

### Inherited from earlier work

- Detailed ALMA analysis deferred to a separate paper  
  > "our analysis of relevant observations will be detailed in a separate paper on broader issues of the GC (Li et al. 2019 in preparation)" (6.1 Description of ALMA observations and data processing) [from Li et al. 2019 in preparation]
- Hydrodynamic simulation and X-ray synthesis method  
  > "This part of our study follows the same method of (cite: russell17), the relevant details of which we recap here." (5 Hydrodynamic simulations) [from (cite: russell17)]
- X-ray source detection procedure  
  > "The source detection is the same as detailed in the supplementary material of (cite: wang13)." (2 Observations and Data Reduction) [from (cite: wang13)]
- Volume emission measure formula for H30alpha  
  > "We can also obtain the volume emission measure (EM) as (cite: murchikova19)" (8.4 Physical properties of warm ionized gas in IRS 13E) [from (cite: murchikova19)]

### Not stated but needed to reproduce (our reading)

- CASA pipeline versus manual calibration, flux calibrator and flux scale uncertainty for the 2016.1.00870.S execution blocks
- Imaging recipe: tclean parameters (weighting, robust, cell, image size, deconvolver, masking), continuum subtraction and line-free channels
- Spectral window and rest frequency used for H30alpha and the exact velocity frame and channel width
- How the total E3 continuum and H30alpha flux densities (28.5 mJy, 2.37 Jy km/s) were measured: aperture or Gaussian fit
- How the Gaussian deconvolved size of ~0.01 pc of E3 was derived
- Which ALMA project code is correct: the text prints 2016.1.0087.S and the acknowledgment 2016.1.00870.S
- Full ALMA analysis is in an unpublished companion paper (Li et al. 2019)

## Analysis recipe

1. **Process the ALMA Band 6 data and make H30alpha cube and continuum**: Standard CASA processing, primary beam correction, line-free channels used to estimate noise  
  > "We use the Common Astronomy Software Applications package (CASA) version 5.1.1 for standard data processing." (6.1 Description of ALMA observations and data processing); "We apply the primary beam correction for all the ALMA images presented in the present work." (6.1 Description of ALMA observations and data processing)
   - software: CASA
   - parameter: 22 km/s spectral resolution; moment 0 integrated over -400 to 400 km/s  
  > "The final H30$\alpha$ data cube has a spectral resolution of $22~{\rm~km~s^{-1}}$" (6.1 Description of ALMA observations and data processing); "integrated from velocity from $-400~{\rm~km~s^{-1}}$ to $400 {\rm~km~s^{-1}}$" (6.1 Description of ALMA observations and data processing)
   - fitting: _not stated_
   - validation: ALMA emission peaks compared with compact radio sources from the literature  
  > "Fig. [8](#f:p-v-diag)A further demonstrates a good correspondence of ALMA emission peaks with compact radio sources (cite: zhao09)." (6.2 ALMA results)
2. **Characterise H30alpha morphology and line-of-sight velocity components**: Inspect position-velocity diagrams, line profiles and channel maps across the region to identify two velocity components  
  > "From examining the position-velocity diagrams and the H30$\alpha$ line profiles across the region (e.g., Figs. [8](#f:p-v-diag) and [9](#f:v-profs)), we can further determine the LoS velocity distribution of the H30$\alpha$ emission." (6.2 ALMA results)
   - fitting: _not stated_
   - validation: _not stated_
3. **Derive electron temperature of warm ionized gas in E3**: Ratio of continuum to H30alpha line flux under LTE and optically thin assumptions  
  > "Assuming that that this gas is under the local thermodynamic equilibrium and its 232 GHz continuum and H30$\alpha$ line emissions are optically thin" (8.4 Physical properties of warm ionized gas in IRS 13E)
   - parameter: N(He)/N(H) ~ 0.08 and alpha(nu,Te) ~ 0.85 at 232 GHz and Te ~ 1e4 K  
  > "$N(\rm He)/N(\rm H) \sim 0.08$ and $\alpha(\nu,T_{\rm e})\sim 0.85$ at $\nu=232$ GHz and $T_{\rm e} \sim 10^4$ K (cite: mezger67)" (8.4 Physical properties of warm ionized gas in IRS 13E)
   - assumption: LTE, optically thin continuum and line  
  > "Assuming that that this gas is under the local thermodynamic equilibrium and its 232 GHz continuum and H30$\alpha$ line emissions are optically thin" (8.4 Physical properties of warm ionized gas in IRS 13E)
   - fitting: _not stated_
   - validation: Compared with earlier estimates of 6000-12000 K  
  > "which is consistent with previous estimates, ranging from 6000 K to 12000 K" (8.4 Physical properties of warm ionized gas in IRS 13E)
4. **Derive emission measure, density, filling factor and ionized gas mass**: EM from the H30alpha line flux, density from EM and a Gaussian source size of ~0.01 pc, filling factor from assumed thermal pressure balance with the hot X-ray gas  
  > "This together with the above EM value leads to the estimate of $n_{\rm e} \sim 3 \times 10^5\rm~cm^{-3} f_V^{-1/2}$." (8.4 Physical properties of warm ionized gas in IRS 13E); "By further assuming a thermal pressure balance between the warm and hot gases" (8.4 Physical properties of warm ionized gas in IRS 13E)
   - parameter: Deconvolved Gaussian size ~0.01 pc, spherical symmetry; Te = 1e4 K and ne = 1e4-1e7 cm^-3 for the emissivity  
  > "both the continuum and H30$\alpha$ emission intensities of E3 can be characterized by a Gaussian with a deconvolved size of $\sim 0.01$ pc, assuming a spherical symmetry" (8.4 Physical properties of warm ionized gas in IRS 13E)
   - assumption: Thermal pressure balance between warm and hot gas, P/k ~ 2e10 K cm^-3  
  > "By further assuming a thermal pressure balance between the warm and hot gases" (8.4 Physical properties of warm ionized gas in IRS 13E)
   - assumption: Distance 8 kpc  
  > "(1”=0.039 pc at our adopted GC distance $D=8$ kpc)" (1 Introduction)
   - fitting: _not stated_
   - validation: _not stated_
5. **Fit the Chandra X-ray spectrum of IRS 13E**: Joint fit of spectra from three data sets with an optically thin plasma VAPEC model and TBABS absorption; also tested VNEI  
  > "so we fit them jointly, first with an optically thin plasma VAPEC." (3.2 Spectral analysis); "The photoelectric absorption uses the Tuebingen-Boulder model" (3.2 Spectral analysis)
   - software: XSPEC, CIAO
   - parameter: Spectra local background-subtracted and grouped to S/N greater than 3 per bin; errors at 90% confidence  
  > "are adaptively grouped to achieve a signal-to-noise ratio greater than 3 per bin." (3.2 Spectral analysis); "The presented error ranges are at the 90% confidence." (Table 2 note)
   - assumption: ISM abundance pattern of Wilms et al. for plasma and absorber  
  > "The metal abundance pattern of the plasma and the foreground X-ray-absorbing gas are adopted from (cite: wilms00) for the interstellar medium (ISM)." (3.2 Spectral analysis)
   - fitting: XSPEC joint fit; priors and statistic other than chi2/d.o.f. not stated  
  > "This simple model fit is acceptable and gives the best-fit parameters listed in Table [2](#t:para)." (3.2 Spectral analysis)
   - validation: VNEI alternative does not significantly improve the fit  
  > "We find that this model does not significantly improve the fit to the spectra" (3.2 Spectral analysis)
6. **Compare simulated colliding-wind X-ray emission with the data**: Tune WR wind speeds, mass-loss rates and E2-E4 separation in the hydrodynamic simulations, synthesize spectra and images, fit with XSPEC in the same way as the data, and rescale to a larger separation via L_x proportional to Mdot^2/deltaD  
  > "To have as detailed a model-to-observation comparison as possible, we process the model images and spectra in the same manners as for the observations." (5 Hydrodynamic simulations); "From the comparison of the simulated X-ray spectra and sizes with the observed ones of IRS 13E, we constrain $\delta D$, as well as the stellar wind speeds and mass-loss rates of the stars." (5 Hydrodynamic simulations)
   - software: XSPEC
   - parameter: Absorption fixed at the best-fit NH from the data; remaining 23 WR stars unchanged  
  > "This absorption is fixed at the best-fit ${\rm N_H}$ (Table [2](#t:para)) to reduce the number of variables for the present modeling." (5 Hydrodynamic simulations); "while the remaining 23 WR stars in the simulations are unchanged." (5 Hydrodynamic simulations)
   - fitting: Parameters adjusted one by one by hand; best-fit model reduced chi2 = 1.32  
  > "In the subsequent runs, we adjust the parameters one by one" (5 Hydrodynamic simulations)
   - validation: Radial intensity profile of the PSF-folded model compared with the data  
  > "where a good match to the  profile is found for the synthesized one when it is scaled up to $\delta D \sim 1.3\ensuremath{''}$" (5 Hydrodynamic simulations)

## Software

- **CASA** 5.1.1: Standard processing of the ALMA data  
  > "We use the Common Astronomy Software Applications package (CASA) version 5.1.1 for standard data processing." (6.1 Description of ALMA observations and data processing)
- **CIAO** : Reduction of the Chandra observations  
  > "Individual observations in each of the three data sets are reduced via standard CIAO processing routines." (2 Observations and Data Reduction)
- **XSPEC** : X-ray spectral models (VAPEC, VNEI, VVAPEC, TBABS) for data and simulations  
  > "the spectral models are all in reference to those implemented in the XSPEC software package" (3.2 Spectral analysis)

## Numeric results

| quantity | value | uncertainty | units | step | quote |
|---|---|---|---|---|---|
| E3 electron temperature | 9260 | 650 | K | 3 | We thus have $T_{\rm e}=9260\pm 650$ K, which is consistent with previous estimates |
| E3 total continuum flux density (232 GHz) and H30alpha line flux | S_C = 28.5 mJy; S dV = 2.37 Jy km/s | 1.8 mJy; 0.12 Jy km/s | mJy; Jy km/s | 3 | $S_{\rm C}=28.5\pm 1.8~{\rm mJy}$ and $S\Delta V_{\rm H30\alpha}=2.37\pm 0.12~{\rm Jy~km~s^{-1}}$ |
| E3 electron density (with filling factor) | ~3e5 f_V^-1/2 | not stated | cm^-3 | 4 | leads to the estimate of $n_{\rm e} \sim 3 \times 10^5\rm~cm^{-3} f_V^{-1/2}$. |
| E3 volume filling factor and electron density from pressure balance | f_V ~ 0.1; n_e ~ 1e6 | not stated | dimensionless; cm^-3 | 4 | we estimate the volume filling factor $f_V \sim 0.1$ and hence $n_{\rm e} \sim 10^6\rm~cm^{-3}$. |
| H30alpha flux within 1'' of E3 and its emission measure | ~12 Jy km/s; EM = 6e60 | not stated | Jy km/s; cm^-3 | 4 | is $\sim 12 \rm~Jy~km~s^{-1}$, which corresponds to ${\rm EM} = 6\times 10^{60}\rm~cm^{-3}$ |
| Large-scale filling factor and warm ionized gas mass within 1'' of E3 | f ~ 8e-4; M ~ 1e-2 | not stated | dimensionless; Msun | 4 | The filling factor is then $\sim 8\times 10^{-4}$, while the mass of the warm ionized gas in this region is $\sim m_p EM/n_e\sim 1 \times 10^{-2}~M_\odot$. |
| H30alpha component I (bar) centre velocity | ~ -30 | not stated | km/s | 2 | Component I is relatively narrow and centered at $\sim -30 {\rm~km~s^{-1}}$. |
| H30alpha component II total spread and centre velocity | ~800 spread; centred at ~ +44 | not stated | km/s | 2 | Component II is very broad (with a total spread of $\sim 800 {\rm~km~s^{-1}}$) and is centered roughly at $\sim +44 {\rm~km~s^{-1}}$ |
| IRS 13E X-ray absorbing column density | 1.74e23 | 1.64-1.94e23 (90%) | cm^-2 | 5 | the fitted X-ray absorbing, equivalent hydrogen column density $1.74 (1.64-1.94) \times 10^{23}\rm~cm^{-2}$ for IRS 13E |
| IRS 13E X-ray plasma temperature | 1.34 | 1.22-1.46 (90%) | keV | 5 | The characteristic temperature of 1.34 keV is well consistent with the expected speeds of the winds |
| IRS 13E X-ray luminosity | ~1.2e33 | not stated | erg/s | 5 | with a 2-10 keV luminosity of $\sim 1.2 \times 10^{33} {\rm~ergs~s^{-1}}$ |
| IRS 13E X-ray emission size | ~2 | ~20% | arcsec | 5 | has the full size of about 2$^{\prime\prime}$ with an uncertainty of $\sim 20\%$ |
| Upper limit on central point-source luminosity (2-10 keV) | <~6e32 | not stated | erg/s | 5 | Our upper limit on the source luminosity, $L_x \sim 6 \times 10^{32} {\rm~ergs~s^{-1}}$ in the 2-10 keV band |
| Mean electron density of X-ray plasma | ~6e2 | not stated | cm^-3 | 5 | We estimate the mean electron density of the plasma in IRS 13E as $n_{e}\sim 6 \times 10^{2} {\rm~cm^{-3}}$ |
| Reduced chi2 of best-fit simulated spectrum | 1.32 | not stated | dimensionless | 6 | (with a reduced $\chi^2 = 1.32$) |
| Upper limit on physical E2-E4 separation | up to ~1.3'' (0.05 pc), ~4x the projected separation | not stated | arcsec | 6 | The separation could be up to $\sim 1.3\ensuremath{''}$ (or 0.05 pc), about four times greater than the projected one |

## Qualitative findings

- ALMA continuum and H30alpha emission of IRS 13E are centrally peaked, between E2 and E4, and the central peak is identified with the near-IR complex E3  
  > "Both the mm continuum and the line emission are centrally peaked with their centroids consistent with each other, located between E2 and E4" (6.2 ALMA results)
- X-ray emission peaks between the two WR stars E2 and E4, consistent with colliding winds  
  > "the X-ray emission from IRS 13E appears extended and peaks in the middle between the two WR stars, E2 and E4" (3.1 Spatial analysis)

## Claim tuples

- H: Is an intermediate-mass black hole required to explain the stars and gas of IRS 13E? | E: Multi-wavelength analysis (Chandra, ALMA, simulations) and a critical re-examination of the IMBH interpretation of E3 | R: X-ray point-source contribution is limited to at most 50% of the emission (L < ~6e32 erg/s) and E3 kinematics are asymmetric relative to the stars | F: An IMBH is not necessary to explain the observed stellar and gas properties | **supported**
- H: Is the X-ray emission of IRS 13E due to colliding winds of E2 and E4? | E: Hydrodynamic simulations with tuned WR wind parameters compared with Chandra spectra and radial profiles | R: The model reproduces the peak position and spectrum reasonably but under-predicts intensity outside ~0.6 arcsec and is spectrally harder than observed | F: Colliding winds dominate but an additional contribution from group wind confinement by the ambient medium is needed | **partially**
- H: Is IRS 13E colliding with the dense minispiral bar? | E: Compared stellar and bar velocities, ALMA H30alpha velocity components and the Pa-alpha shell structure with a bow shock scenario | R: H30alpha shows a broad velocity component (~800 km/s spread) and a narrow component at the bar velocity; a ~2 arcsec shell appears in Pa-alpha | F: The group is colliding with the bar, which explains the large velocity spread of the warm gas | **supported**
- H: How far is IRS 13E from Sgr A* along the line of sight? | E: Combined the Jacobi radius bound on E2-E4 separation with the X-ray-inferred separation and the extended X-ray morphology | R: Required orbital distance is > 0.27 pc (7 arcsec) for a separation of ~1.3 arcsec | F: The group is likely physically much farther from Sgr A* than its projected distance | **partially**

## Reasoning

- Why this data: The ALMA Band 6 observation gave the highest spatial resolution H30alpha view of IRS 13E available when this part of the study started  
  > "When we started this part of the study, this observation gave us the highest spatial resolution view of the H30$\alpha$ hydrogen recombination line emission of IRS 13E" (6.1 Description of ALMA observations and data processing)
- Why this method: _not stated_
- Alternative: IMBH interpretation of E3 as a ring rotating around a dark object of 2.4e4 Msun (Tsuboi et al.), judged to have difficulties  
  > "However, there might be some difficulties in the IMBH interpretation of E3." (7 Critical examination of existing results and interpretations)
- Alternative: Warm dusty gas formed by cooling of shocked wind material is rejected because the E2-E4 separation is too large  
  > "However, the separation between E2 and E4 is too large to reach high enough densities for the shocked wind material to cool down significantly, let alone to form dust." (8.3 Emission structure within IRS 13E)
- How they decided it was enough: _not stated_
- Limitation (authors): H30alpha sensitivity is limited and gas is lumpy, so the global structure of Component II is uncertain  
  > "Probably because the H30$\alpha$-emitting gas is quite lumpy and/or the sensitivity of the data is too limited" (6.2 ALMA results); "Thus its global structure remains uncertain." (6.2 ALMA results)
- Limitation (authors): True X-ray absorbing column could be 30% higher than the fit  
  > "the real ${\rm N_H}$ could be 30% higher" (5 Hydrodynamic simulations)
- Caveat (inferred, ours): ALMA processing is only summarised; calibration, imaging parameters and flux extraction are deferred to an unpublished paper
- Caveat (inferred, ours): Line-of-sight separation of E2 and E4 and the bar density are poorly constrained, so the simulation scaling to 1.3 arcsec is a one-parameter rescale rather than a fit
- Caveat (inferred, ours): Te, EM and filling factor depend on LTE, optically thin and pressure balance assumptions with no stated uncertainty on the density estimates
- Caveat (inferred, ours): Wind parameters were adjusted by hand with no formal parameter uncertainties

## Reproducibility

- Data public (paper): Chandra data described as archival; ALMA data cited by archive project code  
  > "based on the archival  observations with a total of 5.3 Ms exposure time" (1 Introduction); "This paper makes use of the following ALMA data: ADS/JAO.ALMA#2016.1.00870.S." (Acknowledgments)
- Products in archive: _not stated_
- Missing: ALMA calibration and imaging parameters (robust weighting, cell, masking, continuum subtraction, line-free channels)
- Missing: Method used to measure E3 flux densities and size
- Missing: Hydrodynamic simulation code and input files for the modified IRS 13E wind parameters
- Missing: Chandra observation IDs and extraction regions in text form (regions only in figures)
- Data volume (inferred): One ALMA Band 6 project (likely tens of GB raw) plus 108 Chandra ACIS observations (a few GB)
- Score (inferred): 2/5, Data are archival and the ALMA numbers (Te, EM, filling factor) are given, but the ALMA imaging recipe is not published here and the main conclusions rest on X-ray and hydrodynamic simulations that are not released.
- Rediscovery candidate: no, The ALMA recipe is incomplete and deferred to an unpublished paper, and the main conclusions depend on Chandra analysis and non-released simulations.

## Links

- Method: Li et al. 2019 in preparation (Detailed ALMA data analysis)
- Method: (cite: russell17) (Hydrodynamic simulation and X-ray synthesis method)
- Method: (cite: murchikova19) (H30alpha emission measure formula)
- Companion: (cite: tsuboi19) (Higher resolution ALMA observation of IRS 13E and the IMBH interpretation)
- Companion: (cite: tsuboi17) (Earlier ALMA detection of large velocity width gas at IRS 13E)
- Companion: (cite: murchikova19) (Earlier ALMA observations of the Sgr A* accretion flow)
- Related: Chandra X-ray Visionary Project (XVP) of Sgr A*
- Related: ALMA project 2016.1.00870.S (PI Elena Murchikova)

## Checks

```json
{
 "quotes": 101,
 "quotes_ok": 101,
 "quote_pass_rate": 1.0,
 "quotes_too_long": 0,
 "unsupported_facts": 0,
 "project_codes": 2,
 "codes_not_in_text": [],
 "codes_not_in_obscore": [
  "2016.1.0087.S"
 ],
 "obscore_codes_not_in_card": [],
 "codes_printed_but_missing": [],
 "numeric_results": 16,
 "numeric_problems": 0,
 "fill": {
  "facts": 92,
  "stated": 58,
  "rate": 0.63
 },
 "evidence_ok": true
}
```
