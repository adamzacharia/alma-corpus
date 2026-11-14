# Dynamical resonances in PHANGS galaxies

`2024A&A...691A.351R` | Astronomy and Astrophysics 2024 | first author: Ruiz-García, Marina | arXiv: 2410.13353 | DOI: 10.1051/0004-6361/202450935

Card schema 1.0 | model claude-sonnet-5-5-claude-code | depth full | type archival_reuse

## Science

- Fields: nearby_galaxies
- Question: Locate the bar corotation resonance (and derive ILR/OLR) in 46 barred PHANGS-ALMA galaxies with the gravitational torque method, and compare with literature CR estimates  
  > "The main objective of this paper is to apply this last method and compare it with the results obtained with other methods in the literature." (Introduction)
- Target **46 barred galaxies of the PHANGS-ALMA sample (74-galaxy parent sample)**: coordinates not stated (per-galaxy RA/Dec in Table 1)  
  > "From the parent sample of 74 galaxies, 46 are barred" (2.1 Sample); "and the distances are listed in (cite: 2021MNRAS.501.3621A)" (2.1 Sample); z/distance D ~ 17 Mpc (sample selection); per-galaxy distances in Table 1  
  > "From the parent sample of 74 galaxies, 46 are barred" (2.1 Sample); "and the distances are listed in (cite: 2021MNRAS.501.3621A)" (2.1 Sample); distance from Anand et al. 2021 (cite: 2021MNRAS.501.3621A)  
  > "From the parent sample of 74 galaxies, 46 are barred" (2.1 Sample); "and the distances are listed in (cite: 2021MNRAS.501.3621A)" (2.1 Sample)
- Target **NGC 1097, NGC 3627, NGC 4321, NGC 4579 (case studies)**: coordinates _not stated_; z/distance _not stated_; distance from _not stated_

## Data provenance

- ALMA projects: 2012.1.00650.S, 2013.1.00803.S, 2013.1.01161.S, 2015.1.00121.S, 2015.1.00782.S, 2015.1.00925.S, 2015.1.00956.S, 2016.1.00386.S, 2017.1.00886.L, 2018.1.01651.S
- bands: _not stated_
- frequencies and spectral setup: CO(2-1) line  
  > "The CO(2-1) transition has been used in PHANGS to trace the cold molecular gas H$_2$." (2.2 PHANGS–ALMA data (gas maps))
- continuum bandwidth: _not stated_
- arrays: _not stated_
- configurations: _not stated_
- baselines: _not stated_
- angular resolution: <~ 1 arcsec (PHANGS-ALMA survey)  
  > "The PHANGS–ALMA survey includes massive star-forming galaxies observed at a resolution of $\lesssim 1''$ at various wavelengths." (2.1 Sample)
- max recoverable scale: _not stated_
- sensitivity: _not stated_
- time on source: _not stated_
- observing dates: _not stated_
- pi or archival as stated: public PHANGS-ALMA v4.0 moment-0 products  
  > "For the CO maps, we use the zeroth-order moment maps (integrated intensity) based on the public" (2.2 PHANGS–ALMA data (gas maps)); "as published in PHANGS–ALMA version 4.0." (2.2 PHANGS–ALMA data (gas maps))
- Line: CO J=2-1 (not stated)
- Other facility **Spitzer IRAC 3.6 micron (S4G and other archival Spitzer imaging)**: NIR stellar mass maps used for the gravitational potential  
  > "Images from this survey used in the present work were obtained using the 3.6$\mu$m band of IRAC" (2.3 NIR images (stellar mass maps))
- Other facility **VLT/MUSE (PHANGS-MUSE)**: alternative rotation curves (MUSE stellar and H-alpha kinematics) tested in the appendix  
  > "but based on MUSE data" (Appendix: Rotation curves)
- External data: Galaxy centers, orientations and distances from the PHANGS sample table v1.6  
  > "The corresponding galaxy parameters such as distances, centers, and orientations are adopted from PHANGS sample table version v1.6" (2.1 Sample) [from (cite: 2021ApJS..257...43L)]
- External data: Inclination and position angle from CO kinematic analysis  
  > "The inclination ($i$) and position angle (PA) are obtained from the CO kinematic analysis in (cite: Lang+20)" (2.1 Sample) [from (cite: Lang+20)]
- External data: CO-based rotation curves used as proxy for circular velocity  
  > "We use rotation curves based on CO kinematics from (cite: Lang+20) as a proxy for the circular velocity." (3.4 Identifying other dynamical resonances) [from (cite: Lang+20)]
- External data: Bar radii R_bar  
  > "where $R_{\rm bar}$ is obtained from (cite: Querejeta+21)" (3.3 Gas flows) [from (cite: Querejeta+21)]
- External data: Disk scale-lengths H_disk from NIR photometric decompositions  
  > "where $H_{\rm disk}$ is obtained from photometric decompositions of NIR images ((cite: 2015ApJS..219....4S; Querejeta+21))" (3.1 Gravitational potential) [from (cite: 2015ApJS..219....4S; Querejeta+21)]
- External data: Stellar mass maps (S4G, ICA-corrected where recommended)  
  > "Most stellar mass maps are obtained from the S$^4$G survey ((cite: Sheth+2010; Querejeta+15))." (2.3 NIR images (stellar mass maps)) [from (cite: Sheth+2010; Querejeta+15)]
- External data: Bar classification (strong/weak) from infrared data  
  > "This bar classification is based on infrared data from (cite: Buta+15)." (2.1 Sample) [from (cite: Buta+15)]
- External data: Literature CR measurements (ten methods, 33 papers) used for comparison  
  > "After this extensive literature research (ten different methods, 33 different papers)" (6 Summary and conclusions) [from references listed in Table 4]
- External data: Central ring radii from earlier work, used to test rings against the derived ILR  
  > "Columns (4) and (5) contain the central ring positions registered in (cite: Querejeta+21) and (cite: Comeron+14) respectively." (Table 4.5 notes) [from (cite: Querejeta+21); (cite: Comeron+14)]

## Processing

### Calibration

- pipeline or manual: _not stated_
- casa version: _not stated_
- pipeline version: _not stated_
- archive products used as is: yes, released PHANGS-ALMA v4.0 moment-0 maps (strict masks, with single-dish combined) used as published  
  > "as published in PHANGS–ALMA version 4.0." (2.2 PHANGS–ALMA data (gas maps))
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
- masking: strict masks: S/N > 4 over two consecutive channels, extended to surrounding S/N > 2 over two consecutive channels  
  > "These CO maps were calculated first considering only positions in the cubes where emission exceeds a signal-to-noise ratio of four over two consecutive velocity channels." (2.2 PHANGS–ALMA data (gas maps)); "Then, these positions were extended by including any surrounding areas where the S/N is greater than two over two consecutive velocity channels in terms of signal-to-noise ratio." (2.2 PHANGS–ALMA data (gas maps))
- multiscale scales: _not stated_
- continuum subtraction: _not stated_
- line free channels: _not stated_
- primary beam correction: _not stated_
- array combination: single-dish measurements included in the CO maps to correct missing short spacings  
  > "These maps include single dish measurements to correct for missing short spacings" (2.2 PHANGS–ALMA data (gas maps))
- smoothing: _not stated_
- final beam: _not stated_
- final rms: _not stated_

### Inherited from earlier work

- Gravitational torque method (potential, torques, CR identification)  
  > "This section summarizes the method from (cite: GB+05) used to study gravitational torques exerted by the stellar potential on the gas distribution and estimate the location of CR." (3 Gravitational torques) [from (cite: GB+05)]
- Fourier-transform convolution for the potential  
  > "The convolution for the potential is implemented using a Fourier transform approach (see (cite: GB+05) or (cite: Querejeta+16) for more details)." (3.1 Gravitational potential) [from (cite: GB+05); (cite: Querejeta+16)]
- Sample selection details  
  > "Readers can refer to (cite: 2021ApJS..257...43L) for a more detailed explanation of the selection strategy." (2.1 Sample) [from (cite: 2021ApJS..257...43L)]
- Constant CO line ratio R21 ~ 0.65  
  > "We assumed a constant line ratio $R_{21}=(2-1)/(1-0)\sim 0.65$ for PHANGS" (2.2 PHANGS–ALMA data (gas maps)) [from (cite: 2021ApJS..257...43L)]
- ICA stellar mass map construction  
  > "Further information can be found in (cite: Querejeta+15)." (2.3 NIR images (stellar mass maps)) [from (cite: Querejeta+15)]

### Not stated but needed to reproduce (our reading)

- Processing of the PHANGS-ALMA cubes (CASA version, imaging parameters, calibration) is not given; reproducer must rely on the public v4.0 release
- Which stellar mass map (IRAC, ICA1 or ICA2) is nominal for each galaxy (Table 2) and the per-galaxy H_disk values
- pydisc version and deprojection options (interpolation, pixel grid, handling of CO vs 1.7 arcsec S4G resolution mismatch)
- Numerical treatment of the rotation-curve derivative (smoothing/spline) used for kappa and the ILR/OLR intersections
- Exact sign convention bookkeeping and mask handling when azimuthally averaging
- Literature CR values, their rescaling to the adopted distances/inclinations, and which entries were excluded
- Random seeds and perturbation implementation for the bootstrap; criteria for manual QF downgrades beyond visual inspection

## Analysis recipe

1. **assemble gas and stellar mass maps**: Use PHANGS-ALMA v4.0 strict-mask CO(2-1) moment-0 maps as the gas distribution and S4G/Spitzer 3.6 micron maps (ICA1, ICA2 or IRAC) as stellar mass maps  
  > "For the CO maps, we use the zeroth-order moment maps (integrated intensity) based on the public" (2.2 PHANGS–ALMA data (gas maps)); "Therefore, we adopt the map recommended in (cite: Querejeta+15) when available and the original (IRAC) map otherwise." (2.3 NIR images (stellar mass maps))
   - parameter: M/L = 0.6 at 3.6 micron  
  > "We use a constant mass-to-light ratio of $M/L=0.6$ at $3.6 \ \mu\rm m$, based on (cite: Meidt+14)" (2.3 NIR images (stellar mass maps))
   - assumption: Milky Way-like alpha_CO = 4.3 Msun (K km/s pc^2)^-1  
  > "We note that this value is the Milky Way-like $\alpha_{\rm CO}$." (2.2 PHANGS–ALMA data (gas maps))
   - assumption: constant line ratio R21 ~ 0.65  
  > "We assumed a constant line ratio $R_{21}=(2-1)/(1-0)\sim 0.65$ for PHANGS" (2.2 PHANGS–ALMA data (gas maps))
   - fitting: _not stated_
   - validation: Cited comparison of ICA mass maps with MUSE stellar-population estimates shows good agreement (other work)  
  > "They find very good agreement in terms of stellar mass surface density, $\Sigma_{\star}$, arm/interarm contrasts." (2.3 NIR images (stellar mass maps))
2. **deproject images**: Deproject gas and stellar maps with PA and inclination from Table 1  
  > "Prior to obtaining the gravitational potential, our images are deprojected according to the PA and $i$ from Table" (3 Gravitational torques)
   - software: pydisc
   - parameter: PA and i from CO kinematics (Lang+20)  
  > "The inclination ($i$) and position angle (PA) are obtained from the CO kinematic analysis in (cite: Lang+20)" (2.1 Sample)
   - assumption: central structures are as flattened as the disk (no spherical bulge)  
  > "we assume that any central structures are as flattened as the disk" (5.4 Deprojection issues)
   - fitting: _not stated_
   - validation: _not stated_
3. **compute gravitational potential**: Convolve the stellar surface density with the kernel of a constant scale-height isothermal (sech^2) disk using Fourier transforms  
  > "The convolution for the potential is implemented using a Fourier transform approach" (3.1 Gravitational potential)
   - parameter: h ~ 1/12 H_disk  
  > "h\sim 1/12 H_{\rm disk}" (3.1 Gravitational potential)
   - assumption: vertical distribution of an isothermal disk  
  > "we assume our galaxies have a vertical distribution similar to that of an isothermal disk" (3.1 Gravitational potential)
   - assumption: baryon-dominated disk, no dark matter  
  > "This implicitly assumes that the disk is baryon-dominated" (3.1 Gravitational potential)
   - fitting: _not stated_
   - validation: scale-height effect judged negligible for CR location based on a cited M51 test  
  > "its effect is negligible, as seen in (cite: Querejeta+16) for M 51" (5.4 Other assumptions)
4. **compute torque field**: Forces from the potential gradient; torque per unit mass t = xFy - yFx; multiplied by molecular gas to get angular momentum change  
  > "Then, the torques per unit gas mass, in units of $\rm km^{2}s^{-2}$, associated with the gravitational potential are obtained as follows:" (3.2 Torques); "is obtained by multiplying the torque by the total amount of molecular gas in each position" (3.2 Torques)
   - fitting: _not stated_
   - validation: _not stated_
5. **azimuthally average torques and identify CR**: Gas-weighted azimuthal average tau(R); CR taken as the negative-to-positive crossing with the largest amplitude within 0.75-2.25 R_bar  
  > "This often results in multiple zero crossings, and we identify the most significant crossing as the one with the largest amplitude, which we associate with $R_{\rm CR}$." (3.3 Gas flows); "Therefore, we establish $0.75R_{\rm bar}-2.25R_{\rm bar}$ as the range in which we search for the CR of the primary bar." (3.3 Gas flows)
   - parameter: annulus width delta R = 1.5 arcsec  
  > "This is done by an integration of pixels in an annulus defined as $[R+\delta R]$, where $\delta R = 1.5 \ \rm arcsec$." (3.3 Gas flows)
   - assumption: steady state, gas distribution traces where gas spends its time  
  > "this is, we assume steady state" (3.3 Gas flows)
   - fitting: _not stated_
   - validation: Visual inspection of torque profiles and CO coverage  
  > "The $QF$ are further validated by visual inspection of the results" (3.5.2 Quality flags)
6. **derive pattern speed and Lindblad resonances**: Omega_p from the angular velocity curve at R_CR; ILR/OLR from intersections of Omega -/+ kappa/2 with Omega_p using CO rotation curves  
  > "we estimate the pattern speed $\Omega_p$ as the intersection of the position of the $R_{\rm CR}$ and the angular velocity curve, since $\Omega = v / R$" (3.4 Identifying other dynamical resonances); "the intersection of $\Omega\pm \kappa/2$ with the pattern speed $\Omega_p$ provides the location of the ILR and OLR, respectively" (3.4 Identifying other dynamical resonances)
   - parameter: rotation curves in 150 pc wide radial bins  
  > "These rotation curves approximate the circular velocity $v_{\rm c}$ in 150 pc wide fixed radial bins." (3.4 Identifying other dynamical resonances)
   - assumption: epicyclic theory (valid only for small perturbations); observed rotation curve used as circular velocity  
  > "It is important to note that the epicyclic theory is only valid when the perturbations are small." (3.4 Identifying other dynamical resonances)
   - fitting: _not stated_
   - validation: Alternative rotation curves (arctan, MUSE stellar and H-alpha) compared; significant differences found  
  > "We have tried a number of alternatives" (3.4 Identifying other dynamical resonances)
7. **bootstrap uncertainties and quality flags**: Perturb i, PA and center with Gaussian errors N=100 times, take 16th-84th percentile as error, add in quadrature; assign QF from max error relative to R_bar; also vary stellar mass map  
  > "We take the 16th-84th percentile range on the resulting CR as the error bar" (3.5.1 Uncertainties); "Then we combine all errors by adding them in quadrature" (3.5.1 Uncertainties)
   - parameter: N = 100 iterations; center uncertainty +/-0.5 px  
  > "repeat this process $N=100 \ \rm times$" (3.5 Uncertainties and quality flags)
   - parameter: QF=2 for 30% R_bar < err < 80% R_bar (QF=1 below, QF=3 above)  
  > "30 \% \ R_{\rm bar} < err < 80 \% \ R_{\rm bar} \Longrightarrow QF = 2" (3.5.2 Quality flags)
   - fitting: _not stated_
   - validation: QF=3 cases excluded; QF validated by visual inspection  
  > "The $QF$ are further validated by visual inspection of the results" (3.5.2 Quality flags)
8. **compare CR with literature methods**: Spearman correlation and ratio of CR to literature CR, overall and per method, for QF=1,2 galaxies  
  > "We quantify the differences using a Spearman correlation coefficient" (5.1 R_CR comparison)
   - fitting: _not stated_
   - validation: _not stated_
9. **classify bars by R = R_CR/R_bar**: Compute R = R_CR/R_bar and classify ultra-fast (<1), fast (1-1.4), slow (>1.4)  
  > "We calculate the ratio $\mathcal{R} = R_{\rm CR} / R_{\rm bar}$, using the $R_{\rm bar}$ values compiled by (cite: Querejeta+21)." (5.2 Fast and slow bars)
   - fitting: _not stated_
   - validation: _not stated_

## Software

- **pydisc** : deprojection of images  
  > "using the code `pydisc`" (3 Gravitational torques)
- **Python** : implementation language of pydisc  
  > "implemented in Python" (3 Gravitational torques)

## Numeric results

| quantity | value | uncertainty | units | step | quote |
|---|---|---|---|---|---|
| R_CR NGC 1097 | 6.4 | not stated | kpc | 5 | the change from negative to positive torques at $R_{\rm CR}=6.4 \ \rm kpc$, is identified as the CR |
| Omega_p NGC 1097 | 38.5 | +/-4.7 | km s^-1 kpc^-1 | 6 | we measure a pattern speed value of $\Omega_{\rm p} = 38.5\pm 4.7 \ \rm km \ s^{-1}\ kpc^{-1}$ |
| oILR and OLR NGC 1097 | oILR 1.0 kpc, OLR 9.6 kpc | not stated | kpc | 6 | This leads to an oILR at $R = 1.0\ \rm kpc$ and an OLR at $R = 9.6\ \rm kpc$. |
| R_CR NGC 3627 | 5.2 | not stated | kpc | 5 | we consider the CR to be at $R_{\rm CR}=5.2 \ \rm kpc$ |
| Omega_p NGC 3627 | 38.8 | +/-1.8 | km s^-1 kpc^-1 | 6 | we measure a pattern speed value of $\Omega_{\rm p} = 38.8\pm 1.8 \ \rm km \ s^{-1} \ kpc ^{-1}$ |
| R_CR NGC 4321 | 3.7 | not stated | kpc | 5 | the selected crossing ($R_{\rm CR}=3.7 \ \rm kpc$) clearly represents the CR of the bar |
| Omega_p NGC 4321 | 44.2 | +/-4.5 | km s^-1 kpc^-1 | 6 | we measure a pattern speed of $\Omega_{\rm p} = 44.2\pm4.5 \ \rm km \ s^{-1} \ kpc^{-1}$ |
| R_CR NGC 4579 | 3.3 | not stated | kpc | 5 | torques robustly point to a CR at $R_{\rm CR} = 3.3 \ \rm kpc$ |
| Omega_p NGC 4579 | 68.2 | +/-3.5 | km s^-1 kpc^-1 | 6 | We measure a pattern speed $\Omega_{\rm p} = 68.2\pm3.5 \ \rm km \ s^{-1} \ kpc^{-1}$ |
| galaxies with a derived R_CR | 38 of 46 | not stated | galaxies | 5 | We derived the $R_{\rm CR}$ for 38 out of 46 galaxies |
| galaxies with reliable CR (QF=1 or 2) | 20 of 46 (QF=1: 8, QF=2: 12) | not stated | galaxies | 7 | we find that $20$ out of $46$ barred galaxies are reliable; $QF=1$ (8 galaxies, $\sim17\%$) or $QF=2$ (12 galaxies, $\sim26\%$) |
| number of ILRs deduced | 19 (41% of sample) | not stated | galaxies | 6 | we have a total of 19 ILRs (i.e., a $41\%$ of the sample) |
| mean R = R_CR/R_bar (QF=1,2) | 1.12 | +/-0.39 | dimensionless | 9 | Our average value, if we exclude those galaxies with $QF=3$, is $\mathcal{R}\sim 1.12 \pm 0.39$ |
| bar classes among 20 QF=1,2 galaxies | 6 fast (30%), 4 slow (20%), 10 ultra-fast (50%) | not stated | galaxies | 9 | we find six galaxies (30%) presenting fast bars, four galaxies (20%) presenting slow bars and ten galaxies (50%) presenting ultra-fast bars |
| Spearman correlation with all literature methods | rho = 0.64, p < 0.001 | not stated | dimensionless | 8 | We obtain a Spearman coefficient $\rho=0.64\ (p\rm-value<0.001)$. |
| mean and median CR_this paper/CR_literature | mean ~0.9, median ~0.8 | not stated | dimensionless | 8 | the mean quotient of all datapoints $\rm CR_{\rm This \ paper}/\rm CR_{\rm Literature}\sim 0.9$ and the median is $\sim 0.8$ |

## Qualitative findings

- Central rings lie inside the registered ILR in all five galaxies where both were available  
  > "we notice that in all these galaxies ($100\%$), the central ring lies inside the registered ILR" (4.5 Statistics)

## Claim tuples

- H: The gravitational torque method yields a bar corotation radius from the sign change of gas-weighted torques for the PHANGS barred sample | E: Gas-weighted azimuthally averaged torque profiles from PHANGS-ALMA CO and S4G stellar mass maps, bootstrap quality flags | R: CR found for 38 of 46 barred galaxies; 20 flagged reliable (QF=1,2) | F: A catalog of bar CR and other resonances is obtained, with ILR/OLR dependent on the chosen rotation curve | **supported**
- H: Torque-based CR agree with CR from other methods in the literature | E: Spearman correlation and CR ratios against ten methods from 33 papers | R: rho = 0.64 (p < 0.001) overall; most compatible with the potential-density phase-shift method | F: Generally good agreement, though literature uncertainties are very large | **supported**
- H: Bars are predominantly fast (R between 1 and 1.4), arguing against strong braking by dark matter | E: Ratio R = R_CR/R_bar for galaxies with QF=1,2 | R: mean R = 1.12 +/- 0.39; most bars fast or ultra-fast near R ~ 1 | F: Most bars are fast, or compatible with fast within uncertainties | **supported**
- H: Central rings lie inside the ILR, as predicted by Sormani et al. 2023 | E: Compare ring radii with derived ILR for five galaxies with both | R: In all five galaxies the ring lies inside the ILR | F: Consistent with the ring forming at the inner edge of a gap around the ILR | **supported**

## Reasoning

- Why this data: Need stellar mass maps and molecular gas maps at ~1 arcsec to measure gas-stellar phase shifts  
  > "In order to quantify the effect of these gravitational torques on molecular gas, we need to combine stellar mass maps and molecular gas observations." (Introduction)
- Why this method: Torque method applied and compared with other CR methods  
  > "The main objective of this paper is to apply this last method and compare it with the results obtained with other methods in the literature." (Introduction)
- Alternative: Extending the CR search range to 0.3-2.25 R_bar was tested and not adopted  
  > "We assessed the impact of extending the radial range to $0.3R_{\rm bar}-2.25R_{\rm bar}$" (3.3 Gas flows)
- Alternative: Arctan, MUSE stellar and MUSE H-alpha rotation curves tested against the nominal Lang+20 curves  
  > "In said figures, four different rotation curve approaches are represented, namely: our nominal choice, from (cite: Lang+20) (first row), an $\arctan$ approach (second row)" (Appendix: Rotation curves)
- How they decided it was enough: Strict masks preferred to limit noise spikes; QF validated by visual inspection  
  > "because noise spikes often bias the azimuthal averages when calculating torque profiles" (5.4.1 Choice of gas tracer); "The $QF$ are further validated by visual inspection of the results" (3.5.2 Quality flags)
- Limitation (authors): Epicyclic theory and observed rotation curves make derived resonances uncertain, especially for strong bars  
  > "Thus, the calculated dynamical resonances may not be entirely correct, when studying bars (especially strong ones)." (3.4 Identifying other dynamical resonances)
- Limitation (authors): HI neglected  
  > "Also we note that in this analysis, we neglect HI because gas is mostly molecular in the inner parts of galaxies, where bars exist." (5.4.1 Choice of gas tracer)
- Limitation (authors): Spherical bulges not modelled in deprojection  
  > "we do not account for spherical bulges" (5.4.3 Deprojection issues)
- Limitation (authors): Disks assumed baryon-dominated  
  > "We are implicitly assuming that the disks from our sample are baryon-dominated" (5.4.4 Other assumptions)
- Limitation (authors): Literature CR uncertainties are very large  
  > "the uncertainties in the CR literature measurements are very large" (6 Summary and conclusions)
- Caveat (inferred, ours): Only 20 of 46 barred galaxies have reliable CR, and QF downgrades involve manual visual judgement
- Caveat (inferred, ours): ILR/OLR results depend on rotation curve choice and are not independent checks
- Caveat (inferred, ours): Literature comparison has small N for several methods (N=3-7), so correlations are weak
- Caveat (inferred, ours): ALMA data processing is not described; the ALMA part is entirely inherited from PHANGS-ALMA release

## Reproducibility

- Data public (paper): PHANGS-ALMA v4.0 public moment-0 maps and S4G/IRSA Spitzer images  
  > "For the CO maps, we use the zeroth-order moment maps (integrated intensity) based on the public" (2.2 PHANGS–ALMA data (gas maps)); "These maps were downloaded from IRSA" (2.3 NIR images (stellar mass maps))
- Products in archive: _not stated_
- Code: Supplementary material at zenodo.org/records/13898598 (contents not specified in the text)  
  > "Supplementary material is available at: <https://zenodo.org/records/13898598>" (Data availability)
- Missing: pydisc deprojection settings and version
- Missing: per-galaxy H_disk and nominal stellar mass map
- Missing: rotation curve smoothing for kappa
- Missing: torque-profile code (only the Zenodo supplementary material is mentioned)
- Missing: manual QF downgrade criteria per galaxy
- Data volume (inferred): A few GB: PHANGS-ALMA moment-0 maps for 46 galaxies plus Spitzer 3.6 micron images; cubes not needed
- Score (inferred): 4/5, Public input maps, a fully described torque recipe with numeric results in tables; code and some per-galaxy choices not given, and manual QF judgement.
- Rediscovery candidate: yes, Public PHANGS-ALMA and S4G maps, recipe largely complete, and numeric R_CR, Omega_p and R values are tabulated.

## Links

- Method: (cite: GB+05) (Gravitational torque method followed throughout)
- Method: (cite: Lang+20) (CO rotation curves, i and PA)
- Method: (cite: 2021ApJS..257...43L) (PHANGS-ALMA data and sample table v1.6)
- Method: (cite: Querejeta+15) (ICA stellar mass maps)
- Method: (cite: Querejeta+21) (Bar radii and ring measurements)
- Companion: (cite: 2021ApJS..255...19L) (PHANGS-ALMA survey overview)
- Companion: (cite: Williams+21) (Tremaine-Weinberg pattern speeds in PHANGS used for comparison)
- Related: PHANGS-ALMA
- Related: S4G
- Related: PHANGS-MUSE
- Related: ARRAKIS
- Related: SINGS

## Checks

```json
{
 "quotes": 116,
 "quotes_ok": 116,
 "quote_pass_rate": 1.0,
 "quotes_too_long": 0,
 "unsupported_facts": 0,
 "project_codes": 10,
 "codes_not_in_text": [],
 "codes_not_in_obscore": [],
 "obscore_codes_not_in_card": [],
 "codes_printed_but_missing": [],
 "numeric_results": 16,
 "numeric_problems": 0,
 "fill": {
  "facts": 114,
  "stated": 69,
  "rate": 0.605
 },
 "evidence_ok": true
}
```
