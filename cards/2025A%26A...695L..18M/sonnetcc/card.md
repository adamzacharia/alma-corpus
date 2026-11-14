# ALMA 360 parsec, high-frequency observations reveal warm dust in the center of a z = 6.9 quasar

`2025A&A...695L..18M` | Astronomy and Astrophysics 2025 | first author: Meyer, Romain A. | arXiv: 2502.14539 | DOI: 10.1051/0004-6361/202453279

Card schema 1.0 | model claude-sonnet-5-5-claude-code | depth full | type observational_alma_primary

## Science

- Fields: high_z_galaxies, agn_and_quasars
- Question: Can resolved Band 9 plus Band 6 continuum give the resolved dust temperature and opacity of the z=6.9 quasar host J2348-3054, and is AGN radiation heating its central dust?  
  > "these observations enable us to derive the resolved dust temperature profile and dust opacity for the first time at this redshift." (Introduction); "An interesting question is whether the luminous BAL quasar or an associated intense starburst is primarily responsible for heating the dust." (4 Is AGN radiation heating the dust in the center of J2348–3054?)
- Target **J2348–3054**: coordinates Band 9 continuum peak at RA=23:48:33.346, Dec=-30:54:10.307 (ICRS)  
  > "J2348–3054 is a luminous broad absorption line (BAL) quasar at $z=6.9$" (Introduction); "at a position of RA=23:48:33.346, Dec=-30:54:10.307 (ICRS)" (2 The resolved dust properties of a z=6.9 quasar); z/distance z=6.9  
  > "J2348–3054 is a luminous broad absorption line (BAL) quasar at $z=6.9$" (Introduction); "at a position of RA=23:48:33.346, Dec=-30:54:10.307 (ICRS)" (2 The resolved dust properties of a z=6.9 quasar); distance from _not stated_

## Data provenance

- ALMA projects: 2021.1.01350.S, 2018.1.00012.S
- bands: Band 9 (670 GHz, new data); Band 6 (250 GHz continuum, previous data of Walter2022)  
  > "in configuration C43-6 in ALMA Band 9 at a frequency of" (2 The resolved dust properties of a z=6.9 quasar); "Combined with the previous Band 6 190 pc resolution data (cite: Walter2022)" (Introduction)
- frequencies and spectral setup: _not stated_
- continuum bandwidth: entire bandwidth, 15 GHz (Band 9)  
  > "using the entire bandwidth ($15\ \rm{GHz}$)" (2 The resolved dust properties of a z=6.9 quasar)
- arrays: _not stated_
- configurations: C43-6 (Band 9)  
  > "in configuration C43-6 in ALMA Band 9 at a frequency of" (2 The resolved dust properties of a z=6.9 quasar)
- baselines: _not stated_
- angular resolution: Band 9 synthesized beam 0.076'' x 0.06'' (FWHM ~360 pc, effective radius r=216 pc); Band 6 beam effective radius r=110 pc  
  > "The final $670\ \rm{GHz}$ continuum map has a synthesized beam of $0.076\ensuremath{''}\times0.06\ensuremath{''}$, corresponding to a FWHM of $\sim 360\ \rm{pc}$ and an effective radius of $r=216\ \rm{pc}$" (2 The resolved dust properties of a z=6.9 quasar)
- max recoverable scale: 0.9'' (Band 9), similar to the 250 GHz observations  
  > "Importantly, the maximum recoverable scale ($0.9\ensuremath{''}$) is similar to that of the $250\ \rm{GHz}$ continuum observations (cite: Walter2022)." (2 The resolved dust properties of a z=6.9 quasar)
- sensitivity: Band 9 continuum rms 215 uJy/beam; convolved 250 GHz map rms 6.2 uJy/beam  
  > "The rms of the continuum map is 215 $\mu\rm{Jy\ beam}^{-1}$." (2 The resolved dust properties of a z=6.9 quasar); "resulting in an rms of $6.2\ \mu\rm{Jy\ beam}^{-1}$ at $250\ \rm{GHz}$." (2 The resolved dust properties of a z=6.9 quasar)
- time on source: 48 min (Band 9)  
  > "these results, obtained in only 48 minutes, show the potential of such observations" (Summary and future prospects)
- observing dates: _not stated_
- pi or archival as stated: Band 9: Program ID 2021.1.01350.S, PI: Meyer; Band 6 data from Walter2022  
  > "(Program ID #2021.1.01350.S, PI: Meyer)" (2 The resolved dust properties of a z=6.9 quasar)
- Other facility **Herschel/PACS**: Literature FIR fluxes used in the integrated SED (together with all literature data at 100-2000 GHz)  
  > "the observed SED implies that the Herschel/PACS fluxes at" (3 Constraining cold/warm ISM dust and the AGN hot dust torus emission)
- External data: 250 GHz (Band 6) continuum map at 190 pc resolution  
  > "Finally, we convolve the $250\ \rm{GHz}$ continuum map from (cite: Walter2022) down to the $670\ \rm{GHz}$ continuum beam" (2 The resolved dust properties of a z=6.9 quasar) [from (cite: Walter2022)]
- External data: Aperture-integrated residual-scaled 250 GHz fluxes  
  > "We then rescale the flux in these maps to match the aperture-integrated residual-scaled fluxes reported in (cite: Walter2022) and this work." (Impact of the dirty beam and residuals) [from (cite: Walter2022)]
- External data: Integrated FIR SED, all literature data at 100-2000 GHz (individual measurements and references not listed)  
  > "using all literature data at $100-2000$ GHz." (3 Constraining cold/warm ISM dust and the AGN hot dust torus emission) [from not stated]
- External data: Optically-thin single-temperature (85 K) greybody model fit to the SED  
  > "the ALMA Band 9 continuum data excludes the optically-thin model fitted by (cite: Walter2022) with a single temperature of $85\ \rm{K}$." (3 Constraining cold/warm ISM dust and the AGN hot dust torus emission) [from (cite: Walter2022)]
- Simulation/model as data: Di Mascia et al. 2021 simulations (noAGN, AGNsphere, AGNcone) compared with the observed dust temperature profile, dust mass and luminosity fraction vs temperature  
  > "We compare our observations to three different simulations from (cite: DiMascia2021): 1) no AGN feedback, 2) spherical AGN feedback, and 3) conical AGN feedback" (4 Is AGN radiation heating the dust in the center of J2348–3054?)
- Simulation/model as data: SKIRTOR AGN torus models, 1920 models, inclination i=10 deg  
  > "We fit the data at hand for each 1920 SKIRTOR models" (Averaged Dust properties in radial annuli)

## Processing

### Calibration

- pipeline or manual: Reduced by the ALMA ARC Node; baselines with phase RMS >100 deg flagged manually. Bandpass J1924-2914, phase J2349-3133  
  > "The data was reduced directly by the ALMA ARC Node." (2 The resolved dust properties of a z=6.9 quasar); "were manually flagged to minimize decoherence." (2 The resolved dust properties of a z=6.9 quasar); "J1924-2914 was used a bandpass calibrator, and J2349-3133 as phase calibrator." (2 The resolved dust properties of a z=6.9 quasar)
- casa version: _not stated_
- pipeline version: _not stated_
- archive products used as is: _not stated_
- flux calibrator: _not stated_
- flux scale uncertainty: _not stated_
- self calibration: _not stated_

### Imaging

- task: _not stated_
- deconvolver: multiscale cleaning down to 2 sigma (CASA 6.2.1-7)  
  > "version 6.2.1-7 (cite: THECASATEAM2022) with multiscale cleaning down to $2\sigma$" (2 The resolved dust properties of a z=6.9 quasar)
- weighting robust: Briggs robust r = 0.5  
  > "a robust Briggs weighting of $r=0.5$ using the entire bandwidth ($15\ \rm{GHz}$)" (2 The resolved dust properties of a z=6.9 quasar)
- uv taper: _not stated_
- cell size: 0.005''  
  > "with a pixel scale of $0.005\ensuremath{''}$" (2 The resolved dust properties of a z=6.9 quasar)
- image size: _not stated_
- masking: _not stated_
- multiscale scales: _not stated_
- continuum subtraction: none; entire bandwidth used because no significant absorption or emission seen in the spectrum  
  > "Visual inspection of the datacube did not reveal significant absorption or emission in the spectrum." (2 The resolved dust properties of a z=6.9 quasar)
- line free channels: _not stated_
- primary beam correction: _not stated_
- array combination: _not stated_
- smoothing: 250 GHz continuum map convolved to the 670 GHz beam with SpectralCube  
  > "we convolve the $250\ \rm{GHz}$ continuum map from (cite: Walter2022) down to the $670\ \rm{GHz}$ continuum beam" (2 The resolved dust properties of a z=6.9 quasar)
- final beam: 0.076'' x 0.06'' at 670 GHz  
  > "has a synthesized beam of $0.076\ensuremath{''}\times0.06\ensuremath{''}$" (2 The resolved dust properties of a z=6.9 quasar)
- final rms: 215 uJy/beam at 670 GHz; 6.2 uJy/beam for convolved 250 GHz map  
  > "The rms of the continuum map is 215 $\mu\rm{Jy\ beam}^{-1}$." (2 The resolved dust properties of a z=6.9 quasar)

### Inherited from earlier work

- Band 6 (250 GHz) continuum data and its reduction/imaging and residual-scaled integrated fluxes  
  > "We then rescale the flux in these maps to match the aperture-integrated residual-scaled fluxes reported in (cite: Walter2022) and this work." (Impact of the dirty beam and residuals) [from (cite: Walter2022)]
- Optically-thick dust SED with CMB contrast and heating corrections  
  > "apply Cosmic Microwave Background contrast and heating corrections as per (cite: DaCunha2015)" (2 The resolved dust properties of a z=6.9 quasar) [from (cite: DaCunha2015)]
- Dust opacity prescription (kappa_0=13.9 cm2/g, nu_ref=2141 GHz)  
  > "In this work, we adopt the prescription of (cite: Draine2003)" (2 The resolved dust properties of a z=6.9 quasar) [from (cite: Draine2003)]
- Emissivity index beta=1.8, taken as the median of high-z samples  
  > "which corresponds roughly to the median value found in statistical samples of galaxies and quasars observed in multi-band FIR observations at $z>5$ (cite: Witstok2023; Tripodi2024)" (2 The resolved dust properties of a z=6.9 quasar) [from (cite: Witstok2023; Tripodi2024)]
- Residual-scaling of integrated fluxes  
  > "(where we have applied residual-scaling (cite: Jorsater1995; Walter1999) as implemented in the" (2 The resolved dust properties of a z=6.9 quasar) [from (cite: Jorsater1995; Walter1999)]
- L_TIR to SFR conversion  
  > "we would derive a central SFR of $717\pm75 \ M_\odot\ \rm{yr}^{-1}$ using the (cite: Kennicutt2012) relation." (2 The resolved dust properties of a z=6.9 quasar) [from (cite: Kennicutt2012)]
- SKIRTOR AGN torus models (naming convention and physical parameters)  
  > "AGN models (cite: Stalevski2012; Stalevski2016) with a nearly face-on geometry" (3 Constraining cold/warm ISM dust and the AGN hot dust torus emission) [from (cite: Stalevski2012; Stalevski2016)]

### Not stated but needed to reproduce (our reading)

- Flux calibrator and flux-scale uncertainty for the Band 9 data
- CASA pipeline version used by the ARC Node and which flagging was applied beyond the phase RMS >100 deg baselines
- Whether the 2018.1.00012.S data (acknowledged) are the Band 6 data of Walter2022 and how they were imaged
- Mask, threshold and multiscale scales used in tclean; number of iterations
- Which baselines/spw were flagged and the line-free handling (spectral setup of Band 9 not given)
- Table of the literature FIR SED fluxes (100-2000 GHz) and their references
- Sampler/optimizer, priors and parameter bounds of the per-pixel and annuli SED fits (the paper says it maximizes a chi2 log-likelihood and shows posteriors)
- Annuli boundaries are only partly given in text; exact aperture radius is stated as 0.2'' in one place and 0.15'' in another
- How uncertainties on pixel fluxes were derived (including residual-scaling error), and the treatment of the Band 6 absolute flux scale
- Details of the L_TIR integration (wavelength range given as 8-1000 um) and the SKIRTOR parameter grid

## Analysis recipe

1. **Image the Band 9 continuum**: CASA imaging with multiscale clean and Briggs weighting over the full 15 GHz bandwidth  
  > "version 6.2.1-7 (cite: THECASATEAM2022) with multiscale cleaning down to $2\sigma$ and a robust Briggs weighting of $r=0.5$ using the entire bandwidth ($15\ \rm{GHz}$) with a pixel scale of $0.005\ensuremath{''}$" (2 The resolved dust properties of a z=6.9 quasar)
   - software: CASA 6.2.1-7
   - parameter: robust r = 0.5; pixel scale 0.005''; bandwidth 15 GHz; clean to 2 sigma  
  > "a robust Briggs weighting of $r=0.5$ using the entire bandwidth ($15\ \rm{GHz}$) with a pixel scale of $0.005\ensuremath{''}$" (2 The resolved dust properties of a z=6.9 quasar)
   - assumption: no significant line emission or absorption in the Band 9 spectrum, so full bandwidth treated as continuum  
  > "Visual inspection of the datacube did not reveal significant absorption or emission in the spectrum." (2 The resolved dust properties of a z=6.9 quasar)
   - fitting: _not stated_
   - validation: _not stated_
2. **Measure Band 9 peak and integrated flux**: Peak flux density, then aperture-integrated flux centred on the peak pixel with residual-scaling; aperture size chosen with a curve-of-growth analysis  
  > "The aperture radius of $r=0.15\ensuremath{''}$ is chosen with a curve-of-growth analysis, where we find that the flux is consistent within uncertainties for all $r>0.15\ensuremath{''}$ apertures." (2 The resolved dust properties of a z=6.9 quasar)
   - software: interferopy
   - parameter: peak position RA=23:48:33.346, Dec=-30:54:10.307 (ICRS)  
  > "at a position of RA=23:48:33.346, Dec=-30:54:10.307 (ICRS)" (2 The resolved dust properties of a z=6.9 quasar)
   - fitting: _not stated_
   - validation: Curve-of-growth: flux consistent within uncertainties for all r>0.15'' apertures  
  > "where we find that the flux is consistent within uncertainties for all $r>0.15\ensuremath{''}$ apertures." (2 The resolved dust properties of a z=6.9 quasar)
3. **Match the Band 6 map to the Band 9 beam**: Convolve the Band 6 250 GHz continuum map of Walter2022 down to the 670 GHz beam  
  > "we convolve the $250\ \rm{GHz}$ continuum map from (cite: Walter2022) down to the $670\ \rm{GHz}$ continuum beam" (2 The resolved dust properties of a z=6.9 quasar)
   - software: SpectralCube
   - parameter: resulting 250 GHz rms 6.2 uJy/beam  
  > "resulting in an rms of $6.2\ \mu\rm{Jy\ beam}^{-1}$ at $250\ \rm{GHz}$." (2 The resolved dust properties of a z=6.9 quasar)
   - fitting: _not stated_
   - validation: _not stated_
4. **Fit resolved dust SED pixel by pixel**: Optically-thick modified blackbody with CMB contrast correction fitted per pixel to Band 6 and Band 9; only pixels with SNR>3 at both frequencies  
  > "We therefore fit the dust SED using the dust emission equation in the optically-thick regime and apply Cosmic Microwave Background contrast and heating corrections as per (cite: DaCunha2015)" (2 The resolved dust properties of a z=6.9 quasar); "We only fit pixels where the $670\ \rm{GHz}$ and $250\ \rm{GHz}$ continuum is detected at SNR$>3$" (2 The resolved dust properties of a z=6.9 quasar)
   - software: Python (numpy, scipy, astropy)
   - parameter: beta = 1.8 fixed; kappa_0 = 13.9 cm2/g; nu_ref = 2141 GHz  
  > "where $\kappa_0=13.9$ cm$^2$ g$^{-1}$ is the absorption coefficient per unit dust mass" (2 The resolved dust properties of a z=6.9 quasar); "$\nu_{\rm ref}=2141$ GHz is the reference frequency for the dust emissivity" (2 The resolved dust properties of a z=6.9 quasar)
   - parameter: two free parameters: dust temperature and dust mass  
  > "Consequently, the only two free parameters of our fit are the dust temperature and mass" (2 The resolved dust properties of a z=6.9 quasar)
   - assumption: Dust emission optically thick in the inner center of the host; beta=1.8 equal to the median of z>5 samples; Draine (2003) opacity prescription; cosmology Omega_L=0.7, Omega_M=0.3, H0=70  
  > "As (cite: Walter2022) showed, the dust emission is likely optically-thick in the inner center of the quasar host galaxy." (2 The resolved dust properties of a z=6.9 quasar)
   - fitting: Per-pixel fit of Td and Mdust; optimizer, priors and error treatment not stated  
  > "we fit the SED in each pixel using the Band 6 and Band 9 resolved data" (2 The resolved dust properties of a z=6.9 quasar)
   - validation: Model-only (residual-subtracted) maps give consistent temperature and opacity maps, so gradients are not driven by dirty beams  
  > "We find that the dust temperature and opacity maps are consistent with what is observed when including the residuals, confirming that the gradients are real" (Impact of the dirty beam and residuals)
5. **Derive L_TIR, SFR and SFR density**: Integrate fitted SED (8-1000 um) for central beam, convert to SFR with Kennicutt & Evans 2012 relation, assuming star-formation heating  
  > "Assuming that dust is heated by star-formation we would derive a central SFR of $717\pm75 \ M_\odot\ \rm{yr}^{-1}$ using the (cite: Kennicutt2012) relation." (2 The resolved dust properties of a z=6.9 quasar)
   - assumption: All central dust heating attributed to star formation (upper limit if AGN contributes)  
  > "These values could be lower if the central pixel is contaminated by AGN torus hot dust emission and/or the cold dust is in part heated by the AGN" (2 The resolved dust properties of a z=6.9 quasar)
   - fitting: _not stated_
   - validation: Band 6 only (190 pc) limits are consistent with Walter2022  
  > "in agreement with (cite: Walter2022)." (2 The resolved dust properties of a z=6.9 quasar)
6. **Joint annuli plus integrated SED fit with AGN torus**: Four radial annuli (central beam out to 0.15''), each an optically-thick dust model, plus a SKIRTOR hot-dust torus in the central beam, fitted simultaneously with the integrated FIR SED; best of 1920 SKIRTOR models selected by highest likelihood  
  > "We then extract the fluxes in the central beam, and $3$ annuli spanning up to $0.15\ensuremath{''}$." (Averaged Dust properties in radial annuli); "and select the model with the highest likelihood." (Averaged Dust properties in radial annuli)
   - software: SKIRTOR
   - parameter: torus inclination i = 10 deg (nearly face-on); torus assumed unresolved and located at the Band 9 peak  
  > "We first assume that the AGN hot dust torus emission is unresolved at 360 pc resolution, and solely located at the peak of the Band 9 continuum observation." (Averaged Dust properties in radial annuli)
   - parameter: best-fit SKIRTOR model file name t3_p1.5_q1.5_oa80_R10_Mcl0.97_i0_sed.dat  
  > "the best-fit SKIRTOR AGN model is the" (Footnote 2)
   - assumption: beta=1.8; Gaussian, i.i.d. errors; AGN face-on because J2348-3054 is a luminous type 1 quasar  
  > "As we assume errors are gaussian and i.i.d, the log likelihood is simply the sum of the $\chi^2$ for each annuli and the integrated SED." (Averaged Dust properties in radial annuli)
   - fitting: Total log-likelihood = sum of chi2 over annuli and integrated SED; posterior distributions shown; sampler and priors not stated  
  > "We define the total log-likelihood as the sum of the individual log-likelihoods in each annuli and that of the integrated SED" (3 Constraining cold/warm ISM dust and the AGN hot dust torus emission)
   - validation: Compared with independent fits of each annulus to Band 6 and 9 only, without the total SED constraint and without an AGN  
  > "For completeness we also present the same parameters inferred for independent fits to the each annuli" (Averaged Dust properties in radial annuli)
7. **Compare with AGN feedback simulations**: Compare dust temperature profile, dust mass and luminosity fraction vs temperature with noAGN, AGNsphere and AGNcone simulations of Di Mascia et al. 2021 for their most luminous source  
  > "We compare our observations to three different simulations from (cite: DiMascia2021): 1) no AGN feedback, 2) spherical AGN feedback, and 3) conical AGN feedback" (4 Is AGN radiation heating the dust in the center of J2348–3054?)
   - fitting: _not stated_
   - validation: Caveat noted that the simulated AGNsphere source is much less luminous than J2348-3054  
  > "Firstly, the luminosity of the most-luminous source in the *AGNsphere* model is much lower than that observed for J2348–3054." (4 Is AGN radiation heating the dust in the center of J2348–3054?)

## Software

- **CASA** 6.2.1-7: Imaging the Band 9 continuum (tclean)  
  > "version 6.2.1-7 (cite: THECASATEAM2022) with multiscale cleaning down to $2\sigma$" (2 The resolved dust properties of a z=6.9 quasar)
- **SpectralCube** : Convolving the 250 GHz continuum map to the 670 GHz beam  
  > "we convolve the $250\ \rm{GHz}$ continuum map from (cite: Walter2022) down to the $670\ \rm{GHz}$ continuum beam" (2 The resolved dust properties of a z=6.9 quasar)
- **interferopy** : Residual-scaling of integrated fluxes  
  > "(where we have applied residual-scaling (cite: Jorsater1995; Walter1999) as implemented in the" (2 The resolved dust properties of a z=6.9 quasar)
- **SKIRTOR** : AGN hot dust torus models in the joint SED fit  
  > "We fit the data at hand for each 1920 SKIRTOR models" (Averaged Dust properties in radial annuli)
- **numpy, matplotlib, scipy, Astropy** : Python packages used in the work (specific use not stated)  
  > "This work made use of the following Python packages" (Acknowledgements)

## Numeric results

| quantity | value | uncertainty | units | step | quote |
|---|---|---|---|---|---|
| Band 9 (670 GHz) peak continuum flux density | 3.2 | 0.2 | mJy | 2 | We find a peak continuum flux density of $3.2\pm0.2 \ \rm{mJy}$ |
| Band 9 integrated flux density (aperture r=0.2'' as written) | 9.1 | 1.1 | mJy | 2 | and find $S_{\nu=670\ \rm{GHz}}= 9.1\pm1.1\ \rm{mJy}$ |
| Central beam-averaged dust temperature (r<216 pc, no AGN torus) | 88 | 2 | K | 4 | The dust temperature peaks in the central beam to a beam-averaged temperature $88\pm2\ \rm{K}$ |
| Central optical depth at rest 1900 GHz | 1.8 | not stated | dimensionless | 4 | with an optical depth of $\tau_d= 1.8$ at $\nu_{rest}=1900\ \rm{GHz}$ |
| Central (r<216 pc) total infrared luminosity | 4.8e12 | 0.5e12 | L_sun | 5 | the central ($r<216\ \rm{pc}$) total infrared luminosity ($8-1000\ \mu\rm{m}$) is $L_{\rm{TIR}} =  4.8\pm0.5 \times 10^{12}\ L_\odot$ |
| Central SFR (r<216 pc), if heated by star formation | 717 | 75 | M_sun/yr | 5 | we would derive a central SFR of $717\pm75 \ M_\odot\ \rm{yr}^{-1}$ |
| Central SFR surface density | 4.9e3 | not stated | M_sun/yr/kpc^2 | 5 | The corresponding star-formation rate densities (SFRD) $\Sigma_{SFR}=4.9\times10^{3}\ M_\odot \ \rm{yr}^{-1}\ \rm{kpc}^{-2}$. |
| Upper limit on central (r<110 pc) dust temperature | <149 | 5 | K | 5 | we find an upper limit on the a central ($r<110\ \rm{pc}$) dust temperature $T_d < 149\pm5\ \rm{K}$ |
| Upper limit on central (r<110 pc) total infrared luminosity | <10.5e12 | 0.6e12 | L_sun | 5 | $L_{\rm{TIR}}< (10.5\pm0.6) \times 10^{12}\ L_\odot$ |
| Central (r<110 pc) SFR upper limit | <1567 | not stated | M_sun/yr | 5 | a central SFR of $< 1567\ M_\odot\ \rm{yr}^{-1}$ |
| Central dust temperature including AGN hot torus (r<216 pc) | 72 | +2/-1 | K | 6 | the central temperature decreases to $T_d(r<216\ \rm{pc})=72^{+2}_{-1}$ K when including an AGN hot torus contribution |
| Dust temperature at larger radii (joint fit) | ~60-66 | not stated | K | 6 | we still find lower dust temperatures at larger radii $T_d\sim60-66\rm{K}$ |
| Summed FIR luminosity of the four annuli | 8.78e12 | 0.10e12 | L_sun | 6 | the summed FIR luminosity of the four annuli is $L_{FIR} = (8.78\pm0.10)\times 10^{12}L_\odot$, corresponding to SFR$=1307\pm15\ M_\odot\ \rm{yr}^{-1}$. |
| Total SFR from summed annuli luminosity | 1307 | 15 | M_sun/yr | 6 | corresponding to SFR$=1307\pm15\ M_\odot\ \rm{yr}^{-1}$. |
| Ratio of previously reported (optically thin) SFR to this work | 3.6 | not stated | dimensionless | 6 | This is $3.6\times$ lower than the previously-reported value of (cite: Walter2022) |
| Fraction of 670 GHz continuum in the central r<216 pc | 35 | not stated | % | 7 | which accounts for $35\%$ of the continuum emission at $670\ \rm{GHz}$ |
| Predicted AGN torus flux at 875 GHz in the central beam | 2.7 | not stated | mJy | 6 | $f_\nu(875\ \rm{GHz})=2.7\ \rm{mJy}$ |

## Qualitative findings

- The 250/670 GHz contour spacing differs, indicating a radial evolution of the flux ratio and hence of dust properties  
  > "suggesting a radial evolution of $S_{\nu=250\ \rm{GHz}}/S_{\nu=670\ \rm{GHz}}$ and thus the dust emission properties." (2 The resolved dust properties of a z=6.9 quasar)
- Simulations without AGN feedback do not reproduce the observed central warm dust profile; observations agree generally with the AGNsphere model  
  > "We find that the simulations without AGN feedback do not reproduce the warm dust temperature profile observed in the center of J2348–3054" (4 Is AGN radiation heating the dust in the center of J2348–3054?)

## Claim tuples

- H: The dust in the center of the z=6.9 quasar host is warm and optically thick | E: Pixel-by-pixel optically-thick SED fit to 360 pc resolution Band 6 and Band 9 continuum | R: Central beam Td = 88+-2 K with tau = 1.8 at rest 1900 GHz | F: A warm, optically-thick dust component is present at the center (r<216 pc) | **supported**
- H: A single optically-thin cold greybody is adequate for the FIR SED and SFR | E: Compare Band 9 data with the 85 K optically-thin model and fit optically-thick annuli to the integrated SED | R: Band 9 excludes the optically-thin model; summed L_FIR gives an SFR 3.6 times lower | F: The optically-thin approximation overestimates FIR luminosity and the SFR | **supported**
- H: AGN radiation rather than star formation heats the central dust | E: Compare the resolved temperature profile with Di Mascia 2021 simulations with and without AGN feedback | R: No-AGN simulations fail to reproduce warm center; AGNsphere agrees best | F: High central dust temperature is most likely due to AGN heating, though a starburst cannot be formally excluded | **partially**
- H: An AGN hot dust torus contributes to the FIR SED | E: Joint fit of annuli and integrated SED including SKIRTOR torus in the central beam | R: Central Td drops to 72 (+2/-1) K with torus; torus strength and Td strongly anti-correlated | F: Torus contribution is indicated but needs Band 10 high-resolution data to be pinned down | **partially**

## Reasoning

- Why this data: High-frequency data are needed to constrain the SED peak and the dust temperature at high redshift  
  > "high-frequency observations are thus required to accurately constrain the peak of the spectral energy distribution (SED) and infer the dust temperature" (Introduction)
- Why this method: Optically-thick dust model chosen because Walter2022 showed dust emission is likely optically thick in the center  
  > "As (cite: Walter2022) showed, the dust emission is likely optically-thick in the inner center of the quasar host galaxy." (2 The resolved dust properties of a z=6.9 quasar)
- Alternative: Single-temperature (85 K) optically-thin greybody excluded by the Band 9 data  
  > "the ALMA Band 9 continuum data excludes the optically-thin model fitted by (cite: Walter2022) with a single temperature of $85\ \rm{K}$." (3 Constraining cold/warm ISM dust and the AGN hot dust torus emission)
- How they decided it was enough: _not stated_
- Limitation (authors): SFR overestimate factor is a very rough estimate; AGN can heat dust beyond the central beam  
  > "We note that this is a very rough estimate: in reality, the AGN can heat dust beyond the central beam" (4 Is AGN radiation heating the dust in the center of J2348–3054?)
- Limitation (authors): Other models might reproduce the observed temperature profiles  
  > "other models and simulations might reproduce the observed temperature profiles" (4 Is AGN radiation heating the dust in the center of J2348–3054?)
- Caveat (inferred, ours): Only two bands per pixel with beta fixed at 1.8 and two free parameters, so temperature is model-dependent
- Caveat (inferred, ours): Aperture radius is given as 0.2'' and 0.15'' in adjacent sentences
- Caveat (inferred, ours): Residual-scaled flux and pixel-level uncertainties are not described; beam-correlated noise across pixels not discussed
- Caveat (inferred, ours): Comparison to a single most-luminous simulated source with mismatched luminosity for AGNsphere
- Caveat (inferred, ours): Fitting algorithm and priors for the simultaneous SED fit are not given

## Reproducibility

- Data public (paper): _not stated_
- Products in archive: _not stated_
- Missing: Band 6 reduced data/image of Walter2022 and its residual-scaled fluxes
- Missing: Table of literature FIR SED fluxes used in the integrated fit
- Missing: Fitting code, optimizer/sampler and priors
- Missing: Band 9 calibration details (flux calibrator, pipeline version, flagging)
- Missing: Annuli boundaries and error budget for each annulus flux
- Data volume (inferred): Band 9 single 48 min C43-6 execution (likely a few GB raw) plus the Band 6 data from earlier work
- Score (inferred): 3/5, Scale 1-5. Band 9 imaging parameters, dust model and result numbers are given, but Band 6 inputs are inherited, literature SED fluxes and fitting algorithm are not stated, and public availability is not stated.
- Rediscovery candidate: no, Data availability is not stated and the Band 6 inputs, literature SED and fitting details are missing, so the recipe is not complete enough to redo from the paper alone.

## Links

- Method: (cite: Walter2022) (Band 6 250 GHz data, reduction and optically-thin fit this work builds on)
- Method: (cite: DaCunha2015) (CMB contrast and heating corrections for the dust emission equation)
- Method: (cite: Draine2003) (Dust opacity prescription)
- Method: (cite: Stalevski2012; Stalevski2016) (SKIRTOR AGN torus models)
- Method: (cite: Jorsater1995; Walter1999) (Residual-scaling of cleaned-image fluxes)
- Companion: (cite: Walter2022) (190 pc resolution [CII] and Band 6 continuum of the same quasar)
- Companion: (cite: DiMascia2021) (Simulations compared with the observed dust temperature profile)
- Companion: (cite: DiMascia2023) (Suggests the SFR of J2348-3054 might be overestimated by about a factor 10)
- Related: REBELS and ALPINE (non-active galaxy SFR comparison samples)

## Checks

```json
{
 "quotes": 104,
 "quotes_ok": 104,
 "quote_pass_rate": 1.0,
 "quotes_too_long": 0,
 "unsupported_facts": 0,
 "project_codes": 2,
 "codes_not_in_text": [],
 "codes_not_in_obscore": [],
 "obscore_codes_not_in_card": [],
 "codes_printed_but_missing": [],
 "numeric_results": 17,
 "numeric_problems": 0,
 "fill": {
  "facts": 99,
  "stated": 70,
  "rate": 0.707
 },
 "evidence_ok": true
}
```
