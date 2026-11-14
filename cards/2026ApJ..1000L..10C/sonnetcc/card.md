# An Overabundance of Radio Active Galactic Nuclei in the SPT2349─56 Protocluster: Preheating the Intracluster Medium

`2026ApJ..1000L..10C` | The Astrophysical Journal Letters 2026 | first author: Chapman, Scott C. | arXiv: 2511.17814 | DOI: 10.3847/2041-8213/ae4344

Card schema 1.0 | model claude-sonnet-5-5-claude-code | depth light | type multi_facility_alma_minor

## Science

- Fields: high_z_galaxies, agn_and_quasars, galaxy_clusters_and_sz
- Question: Search for additional radio detections (radio-excess AGN) among SPT2349-56 protocluster members with new MeerKAT S-band and ATCA data, and whether the radio-AGN can heat the nascent ICM; ALMA CO(11-10) used as an AGN diagnostic  
  > "This paper presents a search for additional radio detections of members of the SPT2349$-$56 cluster" (1 Introduction); "The overdensity of radio-loud AGN in the compact core region of the cluster may be providing significant heating to the recently discovered nascent intra-cluster medium (ICM) in SPT2349$-$56." (abstract)
- Target **SPT2349-56 protocluster (z=4.3); members A, C, E, N1, N2**: coordinates 23h49m42.5s, -56d38m22.5s (MeerKAT pointing centre)  
  > "A single pointing was centred on the target at ($\alpha, \delta$) = 23h49m42.5s, $-$56d38m22.5s." (2.1.1 MeerKAT 2.4 GHz data); "resulting in a proper angular scale of 6.88 kpc/$''$ at $z=4.3$" (1 Introduction); z/distance z = 4.3  
  > "A single pointing was centred on the target at ($\alpha, \delta$) = 23h49m42.5s, $-$56d38m22.5s." (2.1.1 MeerKAT 2.4 GHz data); "resulting in a proper angular scale of 6.88 kpc/$''$ at $z=4.3$" (1 Introduction); distance from _not stated_

## Data provenance

- ALMA projects: 2021.1.01313.S, 2018.1.00058.S, 2015.1.01543.T, 2021.1.01010.P
- bands: Band 6, continuum at about 240 GHz  
  > "observed $^{12}$CO(11–10) ($\nu_{\rm rest}\,{=}\,$1267.01 GHz) and continuum at about 240 GHz in Band 6" (A.1 New ALMA observations)
- frequencies and spectral setup: _not stated_
- continuum bandwidth: _not stated_
- arrays: _not stated_
- configurations: C-4  
  > "used the C-4 array configuration with baselines of 15 to 784 m" (A.1 New ALMA observations)
- baselines: 15 to 784 m  
  > "used the C-4 array configuration with baselines of 15 to 784 m" (A.1 New ALMA observations)
- angular resolution: 0.47 arcsec (naturally-weighted synthesized beam)  
  > "giving a naturally-weighted synthesized beam size of 0.47$^{\prime\prime}$." (A.1 New ALMA observations)
- max recoverable scale: _not stated_
- sensitivity: _not stated_
- time on source: _not stated_
- observing dates: 2022 September 1  
  > "carried out on 2022, September 1" (A.1 New ALMA observations)
- pi or archival as stated: Cycle 8 program 2021.1.01313.S, PI: Canning (described initially in chapman24)  
  > "The Cycle 8 program (2021.1.01313.S, PI: Canning), described initially in (cite: chapman24) for sources B, C, and G" (A.1 New ALMA observations)
- Line: 12CO 11-10 (1267.01 GHz)
- Other facility **MeerKAT S-band (2.4 GHz)**: New 2.4 GHz imaging of SPT2349-56 (S1 sub-band 1968.75-2843.75 MHz)  
  > "Observations with the MeerKAT radio telescope (cite: Jonas2016) were carried out on SPT2349$-$56 in the S-band" (2.1.1 MeerKAT 2.4 GHz data)
- Other facility **MeerKAT UHF (816 MHz)**: Archival UHF data from chapman24, re-imaged with modified weighting (robust = -2 and -1.2)  
  > "The MeerKAT 816 MHz data processing and imaging was described in (cite: chapman24) and is not repeated here." (2.1.2 MeerKAT 816 MHz data)
- Other facility **ATCA 5.5 and 9.0 GHz**: New 7.5 hr per band imaging in 6A configuration (PI: Aravena)  
  > "SPT2349$-$56 was observed by the ATCA at 5.5 GHz and 9.0 GHz between July 23 to 27, 2023 (PI: Aravena)." (2.2 ATCA observations); "The on-source time was 7.5 hrs in each band." (2.2 ATCA observations)
- External data: UHF 816 MHz MeerKAT data and its processing  
  > "The MeerKAT 816 MHz data processing and imaging was described in (cite: chapman24) and is not repeated here." (2.1.2 MeerKAT 816 MHz data) [from (cite: chapman24)]
- External data: Apertures used to extract line and continuum measurements  
  > "The same apertures used by (cite: Hill20) to extract line and continuum measurements were applied to all sources" (A.1 New ALMA observations) [from (cite: Hill20)]
- External data: Radio-far-IR relation for star-forming galaxies used for radio excess  
  > "an excess of 125 times above the radio-far-infrared (far-IR) relation at this frequency for star-forming galaxies (cite: helou1985)" (3.1 Source C: revised radio power and spectral index) [from (cite: helou1985)]
- External data: X-ray AGN identification of source A  
  > "Source A was previously identified as an X-ray-luminous AGN (cite: vito24)" (3.2 Two new radio AGN in SPT2349$-$56) [from (cite: vito24)]
- External data: Cavity power versus 1.4 GHz radio luminosity correlation  
  > "to estimate the kinetic power from radio luminosity alone for each of the radio AGN" (4.2 Energetics of the radio-AGN); "which can be described using (cite: heckman14)" (4.2 Energetics of the radio-AGN) [from (cite: heckman14)]
- External data: Energy estimated from the tSZ decrement (~1e61 erg)  
  > "comparable to that estimated directly from the tSZ decrement ($\sim10^{61}$ erg) in (cite: zhou2026)" (4.2 Energetics of the radio-AGN) [from (cite: zhou2026)]
- External data: Catalog of about 30 submm-emitting cluster members  
  > "the vast majority selected by submm continuum or [CII] line emission (cite: sulzenauer25)" (4.1 Overdensity of radio-AGN) [from (cite: sulzenauer25)]

## Processing

### Calibration

- pipeline or manual: Standard observatory-supplied calibration script  
  > "All the data were calibrated using the standard observatory-supplied calibration script." (A.1 New ALMA observations)
- casa version: _not stated_
- pipeline version: _not stated_
- archive products used as is: _not stated_
- flux calibrator: J2357-5311 and J2258-2758 for amplitude; J2357-5311 and J2336-5236 for phase  
  > "J2357$-$5311 and J2258$-$2758 were used to calibrate the amplitude, while J2357$-$5311 and J2336$-$5236 were used to calibrate the phase." (A.1 New ALMA observations)
- flux scale uncertainty: _not stated_
- self calibration: _not stated_

### Imaging

- task: CASA tclean  
  > "Imaging was done using the `CASA` task `tclean`, using Briggs weighting with a robust parameter of 0.5" (A.1 New ALMA observations)
- deconvolver: _not stated_
- weighting robust: Briggs, robust = 0.5  
  > "Imaging was done using the `CASA` task `tclean`, using Briggs weighting with a robust parameter of 0.5" (A.1 New ALMA observations)
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
- final beam: 0.47 arcsec (naturally-weighted synthesized beam)  
  > "giving a naturally-weighted synthesized beam size of 0.47$^{\prime\prime}$." (A.1 New ALMA observations)
- final rms: _not stated_

### Inherited from earlier work

- ALMA CO(11-10) reduction and analysis procedures  
  > "Reduction and analysis followed the same procedures described in (cite: hughes25)." (A.1 New ALMA observations) [from (cite: hughes25)]
- Spectrum extraction apertures for line and continuum  
  > "The same apertures used by (cite: Hill20) to extract line and continuum measurements were applied to all sources" (A.1 New ALMA observations) [from (cite: Hill20)]
- MeerKAT 816 MHz processing and imaging  
  > "The MeerKAT 816 MHz data processing and imaging was described in (cite: chapman24) and is not repeated here." (2.1.2 MeerKAT 816 MHz data) [from (cite: chapman24)]
- MeerKAT S-band calibration strategy (OXKAT pipeline)  
  > "using a similar strategy to that described in (cite: chapman24)" (2.1.1 MeerKAT 2.4 GHz data) [from (cite: Heywood2020), (cite: Heywood2022), (cite: chapman24)]

### Not stated but needed to reproduce (our reading)

- ALMA flux density scale uncertainty and flux model for the Cycle 8 calibrators
- CASA version used for ALMA calibration and imaging
- Image size, cell size, deconvolver, masking and cleaning threshold for the Band 6 tclean imaging
- Whether continuum was subtracted and which channels were line-free for CO(11-10)
- Aperture definitions from Hill20 and how line flux was integrated and converted to L_CO(11-10)
- Far-IR luminosities and SFRs used to compute the radio excess, and the radio-far-IR relation parameters
- Priors and likelihood for the emcee spectral-index fit
- Details of the A/C double point-source deconvolution (Appendix B) and the UHF robust = -2 / -1.2 imaging parameters
- ATCA calibrators, flux scale and imaging parameters (robust weighting stated as natural only)
- Whether the MeerKAT and ATCA visibilities are publicly available

## Analysis recipe

1. **Reduce and image MeerKAT 2.4 GHz data**: OXKAT cross-calibration, two rounds of antenna-based self-calibration with Cubical and WSClean MFS imaging, final DDFACET image  
  > "The data were reduced using OXKAT[^1], a semi-automated MeerKAT data analysis pipeline" (2.1.1 MeerKAT 2.4 GHz data); "through two rounds of antenna-based delay self-calibration using the Cubical package (cite: Kenyon2018)" (2.1.1 MeerKAT 2.4 GHz data)
   - software: OXKAT, CASA, Cubical, WSClean, DDFACET
   - parameter: Initial mask from shallow clean with Briggs robust -0.3; final image Briggs robust 0  
  > "using a `Briggs robust` weighting of -0.3" (2.1.1 MeerKAT 2.4 GHz data); "with Briggs’ `robust` weighting of 0 as a trade-off between desired angular resolution and achieved sensitivity" (2.1.1 MeerKAT 2.4 GHz data)
   - parameter: Self-cal in eight spectral bins with 64 s time intervals  
  > "splitting the data into eight spectral bins and time intervals of 64 sec" (2.1.1 MeerKAT 2.4 GHz data)
   - assumption: J 0408-6545 is a point source with Stokes I flux density 8.244 Jy/beam and alpha = -1.138 at 2406 MHz  
  > "Absolute flux calibration assumes J 0408$-$6545 is a point source with Stokes I flux density of $S_\nu =  8.244$ Jy beam$^{-1}$" (2.1.1 MeerKAT 2.4 GHz data)
   - assumption: No direction-dependent calibration needed  
  > "We do not perform any direction-dependent calibration as the S-band residual image has a Gaussian-like noise distribution." (2.1.1 MeerKAT 2.4 GHz data)
   - fitting: _not stated_
   - validation: _not stated_
2. **Re-image MeerKAT UHF 816 MHz data**: Re-imaged with modified visibility weighting: robust = -2 (about 6 arcsec) and robust = -1.2 (about 7 arcsec)  
  > "We use a `robust = -2` weighting to maximise angular resolution ($\sim$6"), while a second image with `robust = -1.2` (similar to (cite: chapman24)) has degraded resolution ($\sim$7")" (2.1.2 MeerKAT 816 MHz data)
   - fitting: _not stated_
   - validation: _not stated_
3. **Image ATCA 5.5 and 9.0 GHz data**: Edited, calibrated and imaged with Miriad and CASA; visibilities inverted with natural weighting  
  > "imaged using the `Miriad` and `CASA` packages" (2.2 ATCA observations); "We inverted the visibilities using natural weighting" (2.2 ATCA observations)
   - software: Miriad, CASA
   - fitting: _not stated_
   - validation: _not stated_
4. **Measure radio fluxes of A, C, E, N1, N2**: Model five sources as unresolved sources in S-band and UHF with free peak positions; subtract and check residuals  
  > "Five source positions (A, C, E, N1, and N2) were modeled as unresolved sources in both S-band and UHF imaging, with peak positions allowed to vary." (B.1 Radio flux measurements)
   - fitting: _not stated_
   - validation: Residuals below 2 sigma after subtracting the five sources  
  > "Subtracting these five sources yields residuals $<2\sigma$ as shown." (B.1 Radio flux measurements)
5. **Fit radio spectral indices**: Linear fit in log space with MCMC (emcee)  
  > "The data were fit according to a linear function in log-space using a Markov Chain Monte Carlo algorithm (MCMC) implemented by the `emcee` package (cite: foreman2013)." (B.2 Radio spectral indices)
   - software: emcee
   - fitting: emcee MCMC sampling the posterior; priors and likelihood not stated  
  > "This MCMC package samples the posterior probability function" (B.2 Radio spectral indices)
   - validation: _not stated_
6. **Derive rest-frame 1.4 GHz luminosity and radio excess**: L_1.4 from luminosity distance, S_1.4 and K-correction (1+z)^-(alpha+1); compare to radio-far-IR relation  
  > "We compute the rest-frame radio luminosity using the equation" (3.1 Source C: revised radio power and spectral index)
   - assumption: H0 = 70 km/s/Mpc, Omega_Lambda = 0.7, Omega_m = 0.3  
  > "a Hubble constant of $H_0\,{=}\,70$ km s$^{-1}$ Mpc$^{-1}$ and density parameters of $\Omega_{\Lambda}\,{=}\,0.7$ and $\Omega_{\rm m}\,{=}\,0.3$ are assumed" (1 Introduction)
   - fitting: _not stated_
   - validation: _not stated_
7. **Estimate kinetic power and injected energy**: Cavity power relation P_cav = 7e43 erg/s x f_cav x (L_1.4/1e25 W/Hz)^0.68, then multiplied by t_radio  
  > "where the enthalpy factor $f_{\rm cav}=4$ for relativistic plasma." (4.2 Energetics of the radio-AGN)
   - assumption: f_cav = 4  
  > "where the enthalpy factor $f_{\rm cav}=4$ for relativistic plasma." (4.2 Energetics of the radio-AGN)
   - assumption: AGN activity time t_AGN = 100 Myr  
  > "Adopting $t_{\rm AGN}=100\,\rm Myr$ for AGN activities" (4.2 Energetics of the radio-AGN)
   - fitting: _not stated_
   - validation: Compared with the energy implied by the tSZ decrement (about 1e61 erg)  
  > "comparable to that estimated directly from the tSZ decrement ($\sim10^{61}$ erg) in (cite: zhou2026)" (4.2 Energetics of the radio-AGN)
8. **Extract ALMA CO(11-10) spectra and continuum fluxes**: Imaging with tclean at robust 0.5, channels averaged to 15.625 MHz, 1D spectra from apertures of Hill20  
  > "in all cases channel widths were averaged down to a common 15.625 MHz" (A.1 New ALMA observations); "to extract one-dimensional CO(11–10) spectra for each source" (A.1 New ALMA observations)
   - software: CASA, tclean
   - parameter: Channel width 15.625 MHz  
  > "channel widths were averaged down to a common 15.625 MHz" (A.1 New ALMA observations)
   - fitting: _not stated_
   - validation: _not stated_

## Software

- **OXKAT** : Semi-automated MeerKAT calibration pipeline  
  > "The data were reduced using OXKAT[^1], a semi-automated MeerKAT data analysis pipeline" (2.1.1 MeerKAT 2.4 GHz data)
- **CASA** : Cross-calibration tasks (MeerKAT); ALMA and ATCA imaging  
  > "the cross-calibration process uses standard Casa tasks" (2.1.1 MeerKAT 2.4 GHz data); "Imaging was done using the `CASA` task `tclean`" (A.1 New ALMA observations)
- **tclean** : ALMA Band 6 imaging  
  > "Imaging was done using the `CASA` task `tclean`" (A.1 New ALMA observations)
- **Cubical** : Antenna-based delay self-calibration of MeerKAT S-band data  
  > "using the Cubical package (cite: Kenyon2018)" (2.1.1 MeerKAT 2.4 GHz data)
- **WSClean** : Multi-frequency synthesis imaging during self-calibration  
  > "with multi-frequency synthesis imaging performed during this process using WSClean (cite: Offringa2014)" (2.1.1 MeerKAT 2.4 GHz data)
- **DDFACET** : Final MeerKAT S-band image  
  > "we use DDFACET (cite: Tasse_2023dd) to generate a $10,125 \times 10,125$ pixel image" (2.1.1 MeerKAT 2.4 GHz data)
- **Miriad** : ATCA editing, calibration and imaging  
  > "imaged using the `Miriad` and `CASA` packages" (2.2 ATCA observations)
- **emcee** : MCMC fit of radio spectral indices  
  > "implemented by the `emcee` package (cite: foreman2013)" (B.2 Radio spectral indices)

## Numeric results

| quantity | value | uncertainty | units | step | quote |
|---|---|---|---|---|---|
| MeerKAT S-band rms near target | 4.3 | not stated | uJy/beam | 1 | The rms sensitivity in the vicinity of the target source of this final map is $\sigma = 4.3 \,\mu$Jy beam$^{-1}$ |
| MeerKAT S-band PSF FWHM | 4.4 x 3.4 at PA -38.8 | not stated | arcsec, deg | 1 | The resultant point spread function FWHM dimensions are 4.4$''$ by 3.4$''$, at a position angle of -38.8 deg east of north. |
| ATCA beams and rms at 5.5 and 9.0 GHz | 2.7x1.5 and 2.1x1.2 arcsec; rms 3.6 and 2.9 | not stated | arcsec; uJy/beam | 3 | beam sizes of $2.7^{\prime\prime}\,{\times}\,1.5^{\prime\prime}$ and $2.1^{\prime\prime}\,{\times}\,1.2^{\prime\prime}$ at 5.5 and 9.0 GHz, respectively, with associated RMS noise values of 3.6 and 2.9 $\mu$Jy beam$^{-1}$. |
| Spectral index of source C | -1.45 | 0.08 | dimensionless | 5 | constrains a slope with high significance, $\alpha=-1.45\pm0.08$ |
| Spectral index of source A | -1.0 | 0.1 | dimensionless | 5 | relatively steep spectrum ($\alpha=-1.0\pm0.1$) radio-loud AGN, with a radio excess of nine times above that implied by star formation |
| Spectral index of source E | -1.2 | 0.3 | dimensionless | 5 | Source E is steeper in radio slope than A ($\alpha=-1.2\pm0.3$) |
| Rest-frame L_1.4 of source C | 2e33 | not stated | erg/s/Hz | 6 | Source C accordingly has a revised 10% lower radio luminosity (L$_{1.4, \rm rest}$ = $2\times10^{33}$ erg s$^{-1}$ Hz$^{-1}$). |
| Radio excess of C over radio-far-IR relation | 125 | not stated | dimensionless | 6 | However this still represents an excess of 125 times above the radio-far-infrared (far-IR) relation at this frequency for star-forming galaxies |
| Radio excess of E over SFR expectation | 9.4 | not stated | dimensionless | 6 | still with a radio excess of 9.4 times that inferred from its SFR |
| Deconvolved radio sizes of C and A at 5.5 GHz | 3.2 (C) and 2.2 (A) | 1.1 (C) and 1.3 (A) | arcsec | 3 | the true sizes are $3.2''\pm1.1''$ for C and $2.2''\pm1.3''$ for A |
| Total kinetic power of the three radio-AGN | 2.6e45 x (f_cav/4) | 0.3e45 | erg/s | 7 | This scaling relation yields a total kinetic power from the three radio-AGN of $\dot{E}_{\rm kin, radio}=(2.6\pm0.3)\times10^{45}{\rm\,erg/s}\times(f_{\rm cav}/4)$. |
| Total energy injection for t_AGN = 100 Myr | 8.7e60 | 0.8e60 | erg | 7 | we obtain a total energy injection of $(8.7\pm0.8)\times10^{60}\rm\,erg$ |
| AGN fraction among submm-emitting members | 13% | not stated | percent | 0 | representing a fairly typical 13% AGN fraction for protoclusters |
| AGN fraction among 14 ULIRGs with SFR>100 | 29% | not stated | percent | 0 | If we consider only the 14 ULIRGs in SPT2349$-$56 with SFR$>100$ M$_\odot$ yr$^{-1}$, the AGN fraction is 29%. |
| CO(11-10) line flux of N1 | 0.98 | 0.08 | Jy km/s | 8 | 0.98$\pm$0.08 |
| CO(11-10) luminosity of N1 | 64.0 | 4.9 | 1e8 Lsun | 8 | 64.0$\pm$4.9 |
| CO(11-10) line flux of A | 0.37 | 0.06 | Jy km/s | 8 | 0.37$\pm$0.06 |

## Qualitative findings

- Radio-AGN A and E are newly identified, with steep spectra and radio excess; N1 shows a CO SLED more like Mrk231 than M82  
  > "N1 is the only source in SPT2349$-$56 showing a spectral line energy density (SLED) more like the AGN Mrk231 than the starburst galaxy M82." (3.2 Two new radio AGN in SPT2349$-$56)
- Sources N1 and N2 follow the radio-far-IR correlation, with no strong evidence for an increase at high redshift  
  > "As such there is not any strong evidence for an increase in radio-far-IR claimed at high redshifts" (3.3 Radio contribution from star formation)

## Claim tuples

- H: Do additional SPT2349-56 members host radio-excess AGN beyond source C? | E: New MeerKAT 2.4 GHz imaging plus re-imaged UHF data, with spectral indices and radio-far-IR excess | R: Sources A and E show excess radio emission and steep spectra | F: Three radio-AGN (A, C, E) are in the cluster core | **supported**
- H: Is N1 an AGN despite no radio excess? | E: New ALMA CO(11-10) spectra and SLED comparison | R: Large and compact CO(11-10) excess in N1 | F: N1 is a probable obscured AGN identified only through CO(11-10) | **partially**
- H: Do the radio-AGN supply enough energy to heat the nascent ICM and explain the tSZ signal? | E: Kinetic power from the Heckman14 cavity-power relation, assuming f_cav = 4 and 100 Myr activity | R: Total injected energy (8.7+-0.8)e60 erg versus about 1e61 erg from tSZ | F: Energetically comparable, but requires nearly 100% coupling efficiency | **partially**
- H: Is the radio-AGN overdensity in the core unusual compared to field surveys? | E: Compare three radio-AGN in the central 130 kpc with deep radio surveys | R: Overdensity factor greater than 1e7 relative to GOODS-N and COSMOS | F: An enormous overdensity of radio-AGN | **supported**

## Reasoning

- Why this data: _not stated_
- Why this method: Briggs robust weighting chosen as a trade-off between angular resolution and sensitivity  
  > "with Briggs’ `robust` weighting of 0 as a trade-off between desired angular resolution and achieved sensitivity" (2.1.1 MeerKAT 2.4 GHz data)
- Alternative: Radio emission over source B attributed to the jet from C projected over B rather than to B itself  
  > "this is indeed the radio jet from C projected over source B, rather than B contributing to the radio luminosity" (3.1 Source C: revised radio power and spectral index)
- How they decided it was enough: _not stated_
- Limitation (authors): Flux loss at higher frequencies from large spatial extent may affect the spectral slope of A  
  > "there is also a possibility that the radio source has a large spatial extent and flux loss at higher frequencies may affect the spectral slope" (3.2 Two new radio AGN in SPT2349$-$56)
- Limitation (authors): Statistical uncertainty of the overdensity is large (three versus one)  
  > "although the statistical uncertainly of three versus one is small" (5 Conclusions)
- Caveat (inferred, ours): ALMA is a minor supporting dataset; the radio excess depends on far-IR SFRs taken from earlier papers that are not tabulated here
- Caveat (inferred, ours): Beam is quoted as naturally weighted but imaging uses robust 0.5, so the setup is ambiguous
- Caveat (inferred, ours): Overdensity factor and energy estimate depend on f_cav = 4 and an assumed 100 Myr lifetime
- Caveat (inferred, ours): Source E flux is blended with D at S-band and was split by hand

## Reproducibility

- Data public (paper): _not stated_
- Products in archive: _not stated_
- Missing: Far-IR luminosities and SFRs per source
- Missing: ALMA tclean image/cell size, masks and continuum-subtraction channels
- Missing: Aperture definitions for CO(11-10) extraction
- Missing: emcee priors and likelihood
- Missing: Public status of MeerKAT and ATCA data not stated
- Data volume (inferred): ALMA Band 6 C-4 single execution plus MeerKAT S-band and UHF visibilities; tens to hundreds of GB for the radio data
- Score (inferred): 2/5, The radio data, calibration and fitting recipe are partly described and numbers are given, but key inputs (SFRs, apertures, public data status, ALMA imaging settings) are missing or deferred to earlier papers.
- Rediscovery candidate: no, Main results come from MeerKAT and ATCA data whose public availability is not stated, and ALMA plays a minor role.

## Links

- Method: (cite: Heywood2020), (cite: Heywood2022) (OXKAT MeerKAT pipeline description)
- Method: (cite: hughes25) (ALMA reduction and analysis procedures followed)
- Companion: (cite: chapman24) (Earlier radio-loud AGN detection in SPT2349-56 and the UHF data)
- Companion: (cite: zhou2026) (tSZ detection and energy reservoir in SPT2349-56)
- Companion: (cite: Hill20) (ALMA apertures and earlier measurements of the members)
- Related: MeerKAT survey of eight z>4 SPT protocluster fields (SCI-20230907-SC-01)

## Checks

```json
{
 "quotes": 100,
 "quotes_ok": 100,
 "quote_pass_rate": 1.0,
 "quotes_too_long": 0,
 "unsupported_facts": 0,
 "project_codes": 4,
 "codes_not_in_text": [],
 "codes_not_in_obscore": [
  "2015.1.01543.T",
  "2021.1.01010.P"
 ],
 "obscore_codes_not_in_card": [],
 "codes_printed_but_missing": [],
 "numeric_results": 17,
 "numeric_problems": 0,
 "fill": {
  "facts": 102,
  "stated": 61,
  "rate": 0.598
 },
 "evidence_ok": true
}
```
