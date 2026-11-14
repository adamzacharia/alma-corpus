# The efficient star-forming regions of stripped-envelope supernovae

`2026MNRAS.552g1615S` | Monthly Notices of the Royal Astronomical Society 2026 | first author: Solar, Martín | arXiv: 2608.18897 | DOI: 10.1093/mnras/stag1615

Card schema 1.0 | model claude-sonnet-5-5-claude-code | depth full | type archival_reuse

## Science

- Fields: nearby_galaxies, transients, star_formation
- Question: Compute star-formation efficiencies (SFR/M_mol) at the locations of H-rich SNe and stripped-envelope SNe, using MUSE Halpha/Hbeta and ALMA CO(2-1) at ~100 pc, to constrain SN progenitor properties  
  > "We compute for the first time the star-formation efficiencies (SFEs) at the locations of hydrogen-rich (H-rich) SNe and stripped-envelope SNe (SESNe) to constrain their progenitor properties." (abstract)
- Target **Sample of 40 core-collapse SN sites (21 H-rich SNe, 19 SESNe) in 25 nearby host galaxies (PHANGS, AMUSING, ACOS and archival)**: coordinates per-SN RA/Dec listed in Table C1  
  > "This table lists the host-galaxy name, whether the observation was made by PHANGS, SN name, right ascension (R.A.), declination (Dec.), SN type, SN group, and redshift." (Appendix C Host galaxies and supernova environments); "After this correction, the final sample is 21 H-rich SNe and 19 SESNe, exploding in 25 host galaxies." (2.1 Sample Selection); "We use a flat $\Lambda$-CDM cosmological model with $H_{0} = 69$ km s$^{-1}$ Mpc$^{-1}$" (1 Introduction); z/distance per-SN redshift in Table C1; sample limited to z<0.018 (<80 Mpc)  
  > "This table lists the host-galaxy name, whether the observation was made by PHANGS, SN name, right ascension (R.A.), declination (Dec.), SN type, SN group, and redshift." (Appendix C Host galaxies and supernova environments); "After this correction, the final sample is 21 H-rich SNe and 19 SESNe, exploding in 25 host galaxies." (2.1 Sample Selection); "We use a flat $\Lambda$-CDM cosmological model with $H_{0} = 69$ km s$^{-1}$ Mpc$^{-1}$" (1 Introduction); distance from not stated (redshifts tabulated; flat LCDM with H0 = 69 km/s/Mpc adopted)  
  > "This table lists the host-galaxy name, whether the observation was made by PHANGS, SN name, right ascension (R.A.), declination (Dec.), SN type, SN group, and redshift." (Appendix C Host galaxies and supernova environments); "After this correction, the final sample is 21 H-rich SNe and 19 SESNe, exploding in 25 host galaxies." (2.1 Sample Selection); "We use a flat $\Lambda$-CDM cosmological model with $H_{0} = 69$ km s$^{-1}$ Mpc$^{-1}$" (1 Introduction)

## Data provenance

- ALMA projects: 2021.1.00099.S, 2013.1.00243.S, 2013.1.01161.S, 2015.1.00902.S, 2015.1.00925.S, 2015.1.00956.S, 2017.1.00392.S, 2017.1.00886.L, 2018.A.00062.S, 2018.1.00272.S, 2018.1.01651.S, 2019.1.01305.S
- bands: Band 6 (CO(2-1))  
  > "observable at its Band 6" (2.2 Data Description)
- frequencies and spectral setup: _not stated_
- continuum bandwidth: _not stated_
- arrays: _not stated_
- configurations: _not stated_
- baselines: _not stated_
- angular resolution: ACOS requested 0.5'' to 1.1''; archival data 0.22'' to 5.77''  
  > "requested angular resolutions of $0.5\ensuremath{''}$ to $1.1\ensuremath{''}$" (2.2 Data Description); "angular resolutions ranged from $0.22\ensuremath{''}$ to $5.77\ensuremath{''}$, able to spatially resolve cloud-scale observations" (2.2 Data Description)
- max recoverable scale: _not stated_
- sensitivity: ACOS: rms 100 mK in 2.049 km/s (1.6 MHz) channels per 50 pc beam  
  > "the sensitivity was set to a root mean square of 100 mK and a bandwidth of 2.049 km s$^{-1}$ (1.6 MHz) per 50 pc beam" (2.2 Data Description)
- time on source: ACOS: integration time 0.3 to 3.6 h  
  > "The observed integration time ranged from 0.3 to 3.6 h" (2.2 Data Description)
- observing dates: 2021.1.00099.S (ACOS): 2022 January to 2022 May  
  > "Observations from 2021.1.00099.S were made from 2022 January to 2022 May." (2.2 Data Description)
- pi or archival as stated: PHANGS, ACOS (PI Michalowski) and archival projects; all data public  
  > "2021.1.00099.S: PI Michałowski (ACOS survey)" (Acknowledgements); "All data are publicly available." (2.2 Data Description)
- Line: CO J=2-1 (230.54 GHz)
- Other facility **VLT/MUSE**: Halpha and Hbeta emission maps for SFR (PHANGS-MUSE, AMUSING archival and own program 114.27G5.001)  
  > "VLT/MUSE spectral data was collected from the AMUSING survey (from the specific program 095.D-0172: PI H. Kuncarayakti) and our own observations" (2.2 Data Description)
- Other facility **PHANGS survey**: ALMA CO(2-1) and MUSE maps of nearby galaxies, plus random-pixel host-galaxy comparison sample  
  > "PHANGS observations covers full galaxy extension in H $\alpha$, H $\beta$, and CO(2–1)." (2.2 Data Description)
- Other facility **NASA/IPAC Infrared Science Archive (dust map)**: Galactic foreground extinction correction of MUSE data  
  > "VLT/MUSE data was corrected for foreground Galactic extinction using the NASA/IPAC Infrared Science Archive" (2.3 Star Formation Efficiency)
- External data: Halpha-SFR calibration (5.5e-42 Msun/yr per erg/s) with Kroupa IMF  
  > "we follow the (cite: 2013Calzetti) prescription as" (2.3 Star Formation Efficiency); "the H $\alpha$-SFR conversion uses a (cite: 2001Kroupa) initial mass function (IMF)" (2.3 Star Formation Efficiency) [from (cite: 2013Calzetti); (cite: 2001Kroupa)]
- External data: Sigma_mol prescription including CO-dark gas, emissivity and opacity  
  > "we follow the (cite: 2024Schinnerer) prescription, which accounts for the fraction of the CO-dark molecular gas, the emissivity, and the opacity of CO-emitting regions" (2.3 Star Formation Efficiency) [from (cite: 2024Schinnerer)]
- External data: R21 = CO(2-1)/CO(1-0) as a function of Sigma_SFR  
  > "line ratio as a function of $\Sigma_{\rm SFR}$ from local ISM conditions (cite: 2025denBrok)" (2.3 Star Formation Efficiency) [from (cite: 2025denBrok)]
- External data: Milky Way CO-to-H2 conversion factor alpha_CO = 4.35  
  > "is the CO-to-H$_{2}$ conversion factor assuming a Milky Way calibration (cite: 2013Bolatto)" (2.3 Star Formation Efficiency) [from (cite: 2013Bolatto)]
- External data: O3N2 gas-phase metallicity calibration  
  > "we computed the gas-phase metallicity indicator described by (cite: 2013Marino) as" (Appendix A Metallicity corrections) [from (cite: 2013Marino)]
- External data: Solar abundances Z_sun = 0.0142 and 12+log(O/H)_sun = 8.69  
  > "where according to (cite: 2009Asplund), $Z_{\odot} = 0.0142$" (Appendix A Metallicity corrections) [from (cite: 2009Asplund)]
- External data: Extinction law with k_alpha=2.52, k_beta=3.66  
  > "Applying the (cite: 1994ODonnell) extinction law (with the extinction coefficients $\rm{k}_{\alpha}=2.52$ and $\rm{k}_{\beta}=3.66$)" (2.3 Star Formation Efficiency) [from (cite: 1994ODonnell)]
- External data: Description of how the PHANGS maps were computed  
  > "We refer to (cite: 2021Pessa) for a description of how the maps were computed." (2.2 Data Description) [from (cite: 2021Pessa)]
- External data: ACOS survey CO(2-1) data of SN sites  
  > "the ALMA CO SN (ACOS) survey (cite: 2024Solar)" (2.1 Sample Selection) [from (cite: 2024Solar)]

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
- smoothing: Coarser of MUSE and ALMA resolution adopted; ALMA convolved with a Gaussian of the MUSE FWHM, or MUSE smoothed to the ALMA beam shape  
  > "If VLT/MUSE had the coarsest resolution, ALMA data were convolved with a Gaussian with the VLT/MUSE full width at half maximum." (2.3 Star Formation Efficiency); "VLT/MUSE observations were smoothed to the ALMA beam shape (with the respective major and minor axes)" (2.3 Star Formation Efficiency)
- final beam: _not stated_
- final rms: _not stated_

### Inherited from earlier work

- Map construction for PHANGS data; archival data processed similarly for homogeneity  
  > "We refer to (cite: 2021Pessa) for a description of how the maps were computed. For observations not covered by PHANGS, we followed a similar approach for archival data" (2.2 Data Description) [from (cite: 2021Pessa)]
- Sigma_mol formula, including metallicity exponent and R21  
  > "To calculate $\Sigma_{\rm{mol}}$, we follow the (cite: 2024Schinnerer) prescription" (2.3 Star Formation Efficiency) [from (cite: 2024Schinnerer)]
- Sigma_SFR from Halpha  
  > "we follow the (cite: 2013Calzetti) prescription as" (2.3 Star Formation Efficiency) [from (cite: 2013Calzetti)]
- ACOS observing design and data  
  > "the ALMA CO SN (ACOS) survey (cite: 2024Solar)" (2.1 Sample Selection) [from (cite: 2024Solar)]
- MUSE data reduction  
  > "The VLT/MUSE data was reduced using the ESO Reflex MUSE pipeline (cite: 2020Weilbacher)." (2.2 Data Description) [from (cite: 2020Weilbacher)]

### Not stated but needed to reproduce (our reading)

- How CO(2-1) moment-0 maps were made (velocity range, masking, noise clipping, channel width) for the archival and ACOS data
- CASA version, calibration and imaging parameters (robust, cell size, deconvolver, tclean settings), array configurations and whether 7 m / total power data were combined
- Which PHANGS data release and resolution versions (native vs. common-resolution) of the CO and MUSE maps were used
- Pixel size, aperture or beam-sized extraction used to read the SN-site values and the SN position accuracy
- STARLIGHT configuration (SSP library, masks) and Gaussian line-fitting setup for MUSE
- Per-galaxy inclination values used in the cos i terms and their sources
- Exact numerical form of the R21 relation (units and normalisation are ambiguous) and how errors on Sigma_SFR, Sigma_mol and SFE were propagated
- How the 1000 Monte Carlo realisations and non-detection upper limits enter the eCDFs and KS/AD tests
- BPT demarcation lines used for star-forming, composite and AGN classification
- The per-SN classification and SN position sources (catalogs listed only generically)

## Analysis recipe

1. **Select CCSNe with MUSE and ALMA CO(2-1) coverage**: Collect CCSNe from catalogs, keep those in face-on nearby galaxies (<80 Mpc) with available MUSE and ALMA CO(2-1) at ~100 pc; classify as H-rich SNe or SESNe  
  > "We selected available observations from both VLT/MUSE and ALMA at spatial resolutions of" (2.1 Sample Selection); "The CCSNe were divided into the following classification groups: Type II, IIP, and IIn as H-rich SNe and Type Ib, IIb, Ib/c, Ic, Ic-pec, and Ic-BL as SESNe." (2.1 Sample Selection)
   - parameter: Distance <80 Mpc (z<0.018), low inclination (face-on) galaxies  
  > "we used face-on galaxies with low inclination angles" (2.1 Sample Selection)
   - fitting: _not stated_
   - validation: _not stated_
2. **Reduce MUSE and ALMA data**: MUSE reduced with ESO Reflex MUSE pipeline; ALMA reduced and analysed with CASA  
  > "The VLT/MUSE data was reduced using the ESO Reflex MUSE pipeline (cite: 2020Weilbacher)." (2.2 Data Description); "The ALMA data was reduced and analysed using the Common Astronomy Software Applications (cite: 2022CASATeam)." (2.2 Data Description)
   - software: ESO Reflex MUSE pipeline, CASA
   - fitting: _not stated_
   - validation: _not stated_
3. **Measure Halpha and Hbeta fluxes from MUSE**: Correct for Galactic extinction, fit and subtract stellar continuum per spectrum, fit Gaussians to emission lines  
  > "For each spectrum, we fitted the best stellar continuum with" (2.3 Star Formation Efficiency); "The integrated area under the Gaussian profile fitted to the respective emission lines gave us an estimate of the flux." (2.3 Star Formation Efficiency)
   - software: STARLIGHT
   - fitting: Gaussian profile fitted to each emission line; priors/likelihood not stated  
  > "The integrated area under the Gaussian profile fitted to the respective emission lines gave us an estimate of the flux." (2.3 Star Formation Efficiency)
   - validation: _not stated_
4. **Correct Halpha for internal dust extinction**: Balmer decrement against intrinsic Halpha/Hbeta = 2.86 with an extinction law to derive A_V  
  > "using the known line-intensity ratio of H $\alpha$ and H $\beta$ of 2.86, as dictated by quantum mechanics" (2.3 Star Formation Efficiency)
   - parameter: k_alpha = 2.52, k_beta = 3.66 (O'Donnell 1994 law)  
  > "Applying the (cite: 1994ODonnell) extinction law (with the extinction coefficients $\rm{k}_{\alpha}=2.52$ and $\rm{k}_{\beta}=3.66$)" (2.3 Star Formation Efficiency)
   - assumption: Case B recombination with T_e = 10000 K and n_e = 100 cm^-3  
  > "For this a Case B recombination is assumed, in which the electron temperature ($T_{e}$) is $T_{e}=10\,000~\rm{K}$" (2.3 Star Formation Efficiency)
   - fitting: _not stated_
   - validation: Typical A_V 1-2 mag; 90 per cent of CCSN environments have A_V<2.5 mag; trends unchanged when the three high-extinction SNe are removed  
  > "However, when these highly extincted CCSNe are removed from the original sample, the trends stay similar." (5 Caveats)
5. **Derive Sigma_SFR**: Sigma_SFR = 5.5e-42 L(Halpha,corrected) cos i, following Calzetti 2013  
  > "where the factor $5.5 \times 10^{-42}$ is in units of" (2.3 Star Formation Efficiency)
   - assumption: Kroupa (2001) IMF  
  > "the H $\alpha$-SFR conversion uses a (cite: 2001Kroupa) initial mass function (IMF)" (2.3 Star Formation Efficiency)
   - fitting: _not stated_
   - validation: _not stated_
6. **Derive gas-phase metallicity**: O3N2 indicator of Marino 2013, 12+log(O/H) = 8.535 - 0.214 O3N2, then Z/Zsun from solar abundance  
  > "we computed the gas-phase metallicity indicator described by (cite: 2013Marino) as" (Appendix A Metallicity corrections)
   - parameter: Zsun = 0.0142, 12+log(O/H)sun = 8.69  
  > "where according to (cite: 2009Asplund), $Z_{\odot} = 0.0142$" (Appendix A Metallicity corrections)
   - fitting: _not stated_
   - validation: Trends do not change whether metallicity is taken into account or not  
  > "our trends do not change whether this metallicity is taken into account or not" (4 Results)
7. **Derive Sigma_mol from CO(2-1)**: Sigma_mol = alpha_CO(1-0) (Z/Zsun)^-1.5 R21^-1 I_CO(2-1) cos i, following Schinnerer & Leroy 2024; 2 sigma upper limits for non-detections  
  > "we follow the (cite: 2024Schinnerer) prescription, which accounts for the fraction of the CO-dark molecular gas, the emissivity, and the opacity of CO-emitting regions" (2.3 Star Formation Efficiency); "$2\sigma$ upper limits were used" (2.3 Star Formation Efficiency)
   - parameter: alpha_CO,MW(1-0) = 4.35 Msun (K km/s pc^2)^-1  
  > "is the CO-to-H$_{2}$ conversion factor assuming a Milky Way calibration (cite: 2013Bolatto)" (2.3 Star Formation Efficiency)
   - parameter: Metallicity factor (Z/Zsun)^-1.5; R21 depends on Sigma_SFR  
  > "the metallicity correction $(Z/Z_{\odot})^{-1.5}$" (5 Caveats)
   - assumption: Milky Way CO-to-H2 calibration scaled with metallicity; CO(2-1)/CO(1-0) from local ISM relation of den Brok 2025  
  > "line ratio as a function of $\Sigma_{\rm SFR}$ from local ISM conditions (cite: 2025denBrok)" (2.3 Star Formation Efficiency)
   - fitting: _not stated_
   - validation: _not stated_
8. **Match resolutions and compute SFE at SN positions**: Extract parameters at the coarser of MUSE/ALMA resolution (convolve or smooth the other), then SFE = 1/tau_dep = Sigma_SFR/Sigma_mol  
  > "For CCSNe, we extracted the environmental parameters using the coarsest resolution available from VLT/MUSE and ALMA." (2.3 Star Formation Efficiency)
   - fitting: _not stated_
   - validation: _not stated_
9. **Remove AGN-ionised regions with a BPT diagnostic**: BPT diagram ([OIII]/Hbeta vs [NII]/Halpha); keep star-forming and composite regions; remove 20 per cent of AGN-dominated host pixels and two SNe in AGN regions  
  > "We retained CCSNe located in star-forming and composite regions (a total of 40). We excluded two CCSNe located in AGN regions" (Appendix B Dominant ionisation source)
   - fitting: _not stated_
   - validation: _not stated_
10. **Build host-galaxy comparison sample and test distributions**: Repeat the procedure on 10000 random PHANGS pixels per galaxy; compare eCDFs of Sigma_SFR, Sigma_mol and SFE between host pixels, H-rich SNe and SESNe with two-sample KS and AD tests (p<0.05)  
  > "To give each galaxy a similar statistical weight, we randomly selected 10 000 pixels per galaxy." (2.3 Star Formation Efficiency); "Table [\[tab:tab2\]](#tab:tab2) reports two-sample Kolmogorov–Smirnov (KS) and Anderson–Darling (AD) tests." (4 Results)
   - parameter: 1 sigma confidence intervals from 1000 Monte Carlo simulations  
  > "(computed using 1000 Monte Carlo simulations)" (4 Results)
   - fitting: _not stated_
   - validation: Results compared with previous SN-environment studies; trends robust to removing high-extinction SNe  
  > "Second, the SFR trends are consistent with previous studies, with higher values for SESNe than for H-rich SNe" (5 Discussion)

## Software

- **CASA** : Reduction and analysis of ALMA data  
  > "The ALMA data was reduced and analysed using the Common Astronomy Software Applications (cite: 2022CASATeam)." (2.2 Data Description)
- **ESO Reflex MUSE pipeline** : Reduction of VLT/MUSE data  
  > "The VLT/MUSE data was reduced using the ESO Reflex MUSE pipeline (cite: 2020Weilbacher)." (2.2 Data Description)
- **STARLIGHT** : Stellar continuum fitting and subtraction of MUSE spectra  
  > "For each spectrum, we fitted the best stellar continuum with" (2.3 Star Formation Efficiency)
- **CARTA** : _not stated_
- **Julia** : _not stated_
- **Astropy** : _not stated_
- **NumPy** : _not stated_
- **SciPy** : _not stated_

## Numeric results

| quantity | value | uncertainty | units | step | quote |
|---|---|---|---|---|---|
| Final sample size | 21 H-rich SNe and 19 SESNe in 25 host galaxies | not stated | dimensionless | 9 | After this correction, the final sample is 21 H-rich SNe and 19 SESNe, exploding in 25 host galaxies. |
| CO(2-1) detections at SN sites | 23 detections (12 H-rich, 11 SESNe); 17 non-detections (9 H-rich, 8 SESNe) | not stated | dimensionless | 7 | CO(2–1) was detected at the positions of 23 CCSNe (12 H-rich SNe and 11 SESNe), and 17 were not detected (9 H-rich SNe and 8 SESNe). |
| log Sigma_SFR (host pixels / H-rich SNe / SESNe) | -2.8227 / -2.09 / -1.26 | +0.0002/-0.0002 / +0.01/-0.01 / +0.01/-0.01 | log(Msun yr^-1 kpc^-2) | 5 | host galaxy pixels ($\log \Sigma_{\mathrm{SFR}} = -2.8227^{+0.0002}_{-0.0002}$), to H-rich SNe ($\log \Sigma_{\mathrm{SFR}} = -2.09^{+0.01}_{-0.01}$), and SESNe ($\log \Sigma_{\mathrm{SFR}} = -1.26^{+0.01}_{-0.01}$) |
| log Sigma_mol (H-rich SNe / SESNe) | 7.7 / 7.6 | +0.1/-0.1 for both | log(Msun kpc^-2) | 7 | $\log \Sigma_{\mathrm{mol}}= 7.7^{+0.1}_{-0.1}$ for H-rich SNe and $\log \Sigma_{\mathrm{mol}} = 7.6^{+0.1}_{-0.1}$ for SESNe |
| log Sigma_mol (host galaxy pixels) | 6.86150 | +0.00003/-0.00001 | log(Msun kpc^-2) | 7 | $\log \Sigma_{\mathrm{mol}} = 6.86150^{+0.00003}_{-0.00001}$ |
| log SFE (host pixels / H-rich SNe / SESNe) | -1.0954 / -0.74 / 0.18 | +0.0003/-0.0003 / +0.09/-0.08 / +0.06/-0.10 | log(Gyr^-1) | 8 | host galaxy pixels ($\log \rm{SFE}=-1.0954^{+0.0003}_{-0.0003}$) $<$ H-rich SNe ($\log \rm{SFE}=-0.74^{+0.09}_{-0.08}$) $<$ SESNe ($\log \rm{SFE}=0.18^{+0.06}_{-0.10}$) |
| SFE ratio SESNe to H-rich SNe | ~8 | not stated | dimensionless | 8 | We find that SESNe explode in environments that are currently forming stars eight times more efficiently than those of H-rich SNe |
| KS and AD p-values for SFE, H-rich SNe vs SESNe | KS p = 1e-4; AD p = 2e-4 | not stated | dimensionless | 10 | This is supported by the low p-values of $1\times10^{-4}$ and $2\times10^{-4}$ for KS and AD, respectively. |
| KS and AD p-values for Sigma_mol, H-rich SNe vs SESNe | KS p = 0.5; AD p = 0.3 (not significant) | not stated | dimensionless | 10 | This is also supported by the high KS and AD p-values (0.5 and 0.3, respectively). |
| Metallicity correction factor (Z/Zsun)^-1.5 (host / H-rich / SESNe) | 1.7451 / 1.62 / 1.66 | +0.0003/-0.0003 / +0.04/-0.03 / +0.12/-0.04 | dimensionless | 6 | is equal to $1.7451^{+0.0003}_{-0.0003}$, $1.62^{+0.04}_{-0.03}$, and $1.66^{+0.12}_{-0.04}$ for host galaxies, H-rich SNe, SESNe, respectively |

## Qualitative findings

- SESNe lie in regions of higher Sigma_SFR than H-rich SNe, and both lie above the host-galaxy baseline  
  > "In summary, SESNe preferentially explode in regions of higher SFR than H-rich SNe, and both CCSN types lie above the host-galaxy baseline." (4 Results)
- H-rich SNe and SESNe share similar molecular gas surface densities, higher than host-galaxy average  
  > "Altogether, both CCSNe explode in regions with similar molecular gas surface densities, but at densities higher than the host galaxy average." (4 Results)
- SESN environments are best explained by a top-heavy IMF and/or high binary fraction, with simple very-massive-single-star origin unlikely  
  > "It is unlikely the scenario where SESN progenitors originate only from very massive stars in star-forming regions with normal IMFs." (6 Conclusions)

## Claim tuples

- H: Do SESN sites differ from H-rich SN sites in SFR surface density? | E: MUSE Halpha-based Sigma_SFR at SN positions compared with random host pixels using eCDFs and KS/AD tests | R: log Sigma_SFR = -2.09 (H-rich) vs -1.26 (SESNe) vs -2.8227 (host pixels); differences significant | F: SESNe explode in regions of higher SFR than H-rich SNe | **supported**
- H: Do SESN sites have more molecular gas than H-rich SN sites? | E: ALMA CO(2-1)-based Sigma_mol at SN positions compared between groups and with host pixels | R: log Sigma_mol = 7.7 vs 7.6; KS p = 0.5, AD p = 0.3 | F: Molecular gas surface densities are similar for both types but above the host average | **supported**
- H: Are SESNe found in more efficient star-forming regions than H-rich SNe? | E: SFE = Sigma_SFR/Sigma_mol at SN sites versus host pixels, with KS/AD tests | R: log SFE = -0.74 (H-rich) vs 0.18 (SESNe); KS p = 1e-4, AD p = 2e-4 | F: SESN sites form stars about eight times more efficiently than H-rich SN sites | **supported**
- H: What progenitor channel explains higher SFE at SESN sites with similar gas content? | E: Interpretation of SFR and M_mol trends in terms of very massive stars, top-heavy IMF and binary evolution | R: Similar M_mol but higher Halpha at SESN sites disfavours a single-star-only very-massive scenario | F: Top-heavy IMF and/or enhanced binary fraction (possibly via turbulence) are favoured; scenarios are not mutually exclusive and not directly tested | **partially**

## Reasoning

- Why this data: Combining MUSE (warm ionised gas) and ALMA (cold molecular gas) at cloud scales yields SFE at SN sites  
  > "Combining both approaches (VLT/MUSE + ALMA) makes it possible to compute the star formation efficiency (SFE) from the ratio of the star formation rate to the amount of molecular gas" (1 Introduction)
- Why this method: Resolution comparable to H II regions and GMCs is needed since progenitors are associated with ionised gas and parent clouds at explosion  
  > "The resolution comparable to typical sizes of H ii regions and GMCs is beneficial as CCSN progenitors should be associated with the ionised gas and their parent molecular clouds at the moment of the explosions." (1 Introduction)
- Alternative: SESN progenitors only from very massive single stars with normal IMF is rejected because it predicts higher M_mol at SESN sites  
  > "Such a model would imply that SESNe should be found in regions with higher $M_{\text{mol}}$ due to the shorter timescales involved" (6 Conclusions)
- How they decided it was enough: _not stated_
- Limitation (authors): Host galaxies are biased toward massive, metal-rich galaxies  
  > "Our host galaxies are not a homogeneous sample and are biased toward large and massive galaxies, which makes it systematically inclined to metal-rich galaxies" (5.3 Caveats)
- Limitation (authors): Three SNe have high dust extinction where Halpha/Hbeta SFR calibration may break down  
  > "Only three CCSNe show high dust extinction values" (5.3 Caveats)
- Limitation (authors): Resolution is ~100 pc, coarser than some H II regions and GMCs; finer resolution would shrink the sample  
  > "Due to instrumental limitations, increasing the spatial resolution would reduce the sample size." (5.3 Caveats)
- Limitation (authors): ALMA observations are not sensitive to large-scale structure (not required for marginally resolved sources)  
  > "The sensitivity to the large-scale structures (on kiloparsec scales) is not required for the detection of marginally-resolved sources." (2.2 Data Description)
- Caveat (inferred, ours): About 17 of 40 SN sites are CO non-detections and use 2 sigma upper limits, so the Sigma_mol and SFE distributions for SESNe are partly limits
- Caveat (inferred, ours): Halpha SFR at a single SN pixel is sensitive to the ionising contribution of the progenitor itself and to binary or IMF assumptions, which are the very effects being inferred
- Caveat (inferred, ours): Statistical tests treat pixels and SNe as independent although host galaxies contribute several SNe and heterogeneous resolutions are mixed
- Caveat (inferred, ours): Heterogeneous CO resolutions (0.22 to 5.77 arcsec) and metallicity-dependent alpha_CO may bias SFE comparisons between samples

## Reproducibility

- Data public (paper): MUSE and ALMA data stated as publicly available  
  > "All data are publicly available." (2.2 Data Description)
- Products in archive: _not stated_
- Missing: Exact CO moment-map construction and noise treatment
- Missing: ALMA calibration and imaging parameters and CASA version
- Missing: Per-pixel extraction aperture and inclination values
- Missing: STARLIGHT and line-fitting configuration
- Missing: Details of Monte Carlo error propagation and the KS/AD handling of upper limits
- Data volume (inferred): Tens to a few hundred GB: about 12 ALMA projects (PHANGS-ALMA CO cubes for ~10 galaxies plus ACOS and archival fields) and ~30 MUSE cubes; PHANGS released maps would greatly reduce this
- Score (inferred): 3/5, Data are public and the Sigma_SFR/Sigma_mol formulas and constants are given, with a per-SN results table, but ALMA processing, map making, extraction apertures and several inputs (inclination, R21 normalisation, BPT lines) are not specified
- Rediscovery candidate: no, Public data and numeric per-SN results exist, but the recipe lacks map construction and extraction details needed to redo it reliably

## Links

- Method: (cite: 2024Schinnerer) (Prescription for Sigma_mol from CO(2-1) including CO-dark gas and opacity)
- Method: (cite: 2021Pessa) (Description of how the PHANGS maps were computed)
- Method: (cite: 2013Calzetti) (Halpha SFR calibration)
- Companion: (cite: 2024Solar) (ACOS survey of CO(2-1) at CCSN sites providing the ACOS data)
- Companion: (cite: 2023MaykerChen) (Earlier ALMA study of molecular gas at SN locations)
- Related: PHANGS
- Related: AMUSING
- Related: ACOS

## Checks

```json
{
 "quotes": 109,
 "quotes_ok": 109,
 "quote_pass_rate": 1.0,
 "quotes_too_long": 0,
 "unsupported_facts": 0,
 "project_codes": 12,
 "codes_not_in_text": [],
 "codes_not_in_obscore": [],
 "obscore_codes_not_in_card": [],
 "codes_printed_but_missing": [],
 "numeric_results": 10,
 "numeric_problems": 0,
 "fill": {
  "facts": 115,
  "stated": 65,
  "rate": 0.565
 },
 "evidence_ok": true
}
```
