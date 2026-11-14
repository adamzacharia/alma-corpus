# Compact Molecular Gas Distribution in Quasar Host Galaxies

`2021ApJ...908..231M` | The Astrophysical Journal 2021 | first author: Molina, Juan | arXiv: 2101.00764 | DOI: 10.3847/1538-4357/abd7f6

Card schema 1.0 | model claude-sonnet-5-5 | depth full | type observational_alma_primary

## Science

- Fields: agn_and_quasars, nearby_galaxies
- Question: What are the spatial distribution and kinematics of molecular gas (CO 2-1) in the host galaxies of six low-z PG quasars?  
  > "to study the distribution and kinematics of the molecular gas of their host galaxies at kpc-scale resolution" (abstract)
- Target **PG 0050+124**: coordinates 00:53:34.94 +12:41:36.2 (J2000)  
  > "PG 0050+124 | 00:53:34.94 | +12:41:36.2 | 0.061 | 282.3" (Table 1); z/distance z=0.061, D_L=282.3 Mpc  
  > "PG 0050+124 | 00:53:34.94 | +12:41:36.2 | 0.061 | 282.3" (Table 1); distance from _not stated_
- Target **PG 0923+129**: coordinates 09:26:03.29 +12:44:03.6 (J2000)  
  > "PG 0923+129 | 09:26:03.29 | +12:44:03.6 | 0.029 | 131.2" (Table 1); z/distance z=0.029, D_L=131.2 Mpc  
  > "PG 0923+129 | 09:26:03.29 | +12:44:03.6 | 0.029 | 131.2" (Table 1); distance from _not stated_
- Target **PG 1011-040**: coordinates 10:14:20.69 -04:18:40.5 (J2000)  
  > "PG 1011$-$040 | 10:14:20.69 | $-$04:18:40.5 | 0.058 | 267.9" (Table 1); z/distance z=0.058, D_L=267.9 Mpc  
  > "PG 1011$-$040 | 10:14:20.69 | $-$04:18:40.5 | 0.058 | 267.9" (Table 1); distance from _not stated_
- Target **PG 1126-041**: coordinates 11:29:16.66 -04:24:07.6 (J2000)  
  > "PG 1126$-$041 | 11:29:16.66 | $-$04:24:07.6 | 0.060 | 277.5" (Table 1); z/distance z=0.060, D_L=277.5 Mpc  
  > "PG 1126$-$041 | 11:29:16.66 | $-$04:24:07.6 | 0.060 | 277.5" (Table 1); distance from _not stated_
- Target **PG 1244+026**: coordinates 12:46:35.25 +02:22:08.8 (J2000)  
  > "PG 1244+026 | 12:46:35.25 | +02:22:08.8 | 0.048 | 220.1" (Table 1); z/distance z=0.048, D_L=220.1 Mpc  
  > "PG 1244+026 | 12:46:35.25 | +02:22:08.8 | 0.048 | 220.1" (Table 1); distance from _not stated_
- Target **PG 2130+099**: coordinates 21:32:27.81 +10:08:19.5 (J2000)  
  > "PG 2130+099 | 21:32:27.81 | +10:08:19.5 | 0.061 | 292.3" (Table 1); z/distance z=0.061, D_L=292.3 Mpc  
  > "PG 2130+099 | 21:32:27.81 | +10:08:19.5 | 0.061 | 292.3" (Table 1); distance from _not stated_

## Data provenance

- ALMA projects: 2018.1.00006.S
- bands: Band 6  
  > "designed to detect the continuum and CO(2–1) line in Band 6 using four spectral windows" (2.1 ALMA Observations and Data Reduction)
- frequencies and spectral setup: 4 spectral windows, each 1.875 GHz bandwidth, 7.8125 MHz resolution (~11 km/s channels)  
  > "four spectral windows, each covering 1.875 GHz in bandwidth with a spectral resolution of 7.8125 MHz, equivalent to a channel resolution of $\sim 11$ km s$^{-1}$" (2.1 ALMA Observations and Data Reduction)
- continuum bandwidth: _not stated_
- arrays: 12-m array (43 antennas) plus Cycle 5 ACA  
  > "All the targets were observed by 43 antennas." (2.1 ALMA Observations and Data Reduction); "we concatenate our Cycle 6 observations with the previous Cycle 5 ACA observations" (2.1 ALMA Observations and Data Reduction)
- configurations: _not stated_
- baselines: _not stated_
- angular resolution: beam ~0.4''-1.4''  
  > "beam FWHM $\approx 0.4\ensuremath{''}-1.4\ensuremath{''}$" (Conclusions)
- max recoverable scale: _not stated_
- sensitivity: RMS 0.34-0.59 mJy/beam per channel  
  > "PG 2130+099 | 22 Mar. 2019 | J2000$-$1748 | J2147+0929 | 0.96 | 40.52 | $1.31 \times 1.13$ | 25.5 | 0.34" (Table 2)
- time on source: 11.65-40.52 min per source  
  > "PG 0050+124 | 26 Nov. 2018 | J0006$-$0623 | J0121+1149 | 1.49 | 11.65" (Table 2)
- observing dates: November 2018 to March 2019  
  > "The ALMA observations were carried during November 2018 to March 2019" (2.1 ALMA Observations and Data Reduction)
- pi or archival as stated: Cycle 6 program PI F. Bauer  
  > "program 2018.1.00006.S; PI: F. Bauer" (2.1 ALMA Observations and Data Reduction)
- Line: 12CO J=2-1 (230.538 GHz)
- Other facility **ALMA ACA (Cycle 5)**: Short-spacing CO(2-1) data concatenated with 12-m data  
  > "we concatenate our Cycle 6 observations with the previous Cycle 5 ACA observations using the task CONCAT" (2.1 ALMA Observations and Data Reduction)
- Other facility **HST**: Stellar images of host galaxies (WFC3, NICMOS, WFPC2)  
  > "The stellar component of the six quasar host galaxies are all observed by HST with high spatial resolution at optical or NIR wavelengths." (3.2 CO(2–1) Intensity Map Modeling)
- Other facility **EDGE-CALIFA (CARMA)**: Comparison sample of inactive galaxies' CO(1-0)  
  > "We choose, for comparison, the EDGE-CALIFA sample" (2.4 Comparison Sample)
- External data: ACA-only CO(2-1) fluxes and line ratio L'CO(2-1)/L'CO(1-0)=0.62  
  > "adopting a luminosity ratio $L^\prime_{\rm CO(2-1)} / L^\prime_{\rm CO(1-0)} = 0.62$, the median value found by (cite: Shangguan2020)" (2.3 CO(2–1) Luminosity and Molecular Gas Estimates) [from (cite: Shangguan2020)]
- External data: Stellar mass, L_IR, dust-based gas masses of hosts  
  > "(8) Total infrared luminosity of the host galaxy (cite: Shangguan2018)." (Table 1) [from (cite: Shangguan2018)]
- External data: EDGE-CALIFA CO sizes and gas masses  
  > "We only consider the EDGE-CALIFA galaxies with measured CO sizes (69 systems)." (2.4 Comparison Sample) [from (cite: Bolatto2017)]
- External data: xCOLD GASS nearby galaxy sample  
  > "we also include the larger sample of nearby galaxies from xCOLD GASS (cite: Saintonge2017)" (2.4 Comparison Sample) [from (cite: Saintonge2017)]

## Processing

### Calibration

- pipeline or manual: CASA standard pipeline  
  > "employing the standard pipeline to calibrate the data to generate the $uv$ visibilities" (2.1 ALMA Observations and Data Reduction)
- casa version: _not stated_
- pipeline version: _not stated_
- archive products used as is: _not stated_
- flux calibrator: _not stated_
- flux scale uncertainty: <~10%  
  > "The ALMA flux calibration uncertainty is $\lesssim 10$ %" (2.1 ALMA Observations and Data Reduction)
- self calibration: _not stated_

### Imaging

- task: TCLEAN  
  > "The emission-line imaging is performed using TCLEAN with robust weighting (ROBUST = 0.5)" (2.1 ALMA Observations and Data Reduction)
- deconvolver: _not stated_
- weighting robust: robust = 0.5  
  > "robust weighting (ROBUST = 0.5) and a channel resolution of $11$ km s$^{-1}$" (2.1 ALMA Observations and Data Reduction)
- uv taper: _not stated_
- cell size: synthesized beam sampled by five pixels  
  > "The spatial pixel scale is set to sample the synthesized beam by five pixels." (2.1 ALMA Observations and Data Reduction)
- image size: _not stated_
- masking: AUTO-MULTITHRESH noise 4.0, sidelobe 1.0, low-noise 1.5, fractional beam 0.4  
  > "setting the noise, sidelobe, and low-noise thresholds to 4.0, 1.0, and 1.5, respectively, and the fractional beam size to 0.4" (2.1 ALMA Observations and Data Reduction)
- multiscale scales: _not stated_
- continuum subtraction: UVCONTSUB on flagged line-free channels  
  > "The flagged channels are then input to the task UVCONTSUB to subtract the continuum" (2.1 ALMA Observations and Data Reduction)
- line free channels: _not stated_
- primary beam correction: _not stated_
- array combination: 12-m + ACA concatenated with CONCAT  
  > "we concatenate our Cycle 6 observations with the previous Cycle 5 ACA observations using the task CONCAT" (2.1 ALMA Observations and Data Reduction)
- smoothing: _not stated_
- final beam: 0.40x0.36'' to 1.41x1.17''  
  > "PG 0050+124 | 26 Nov. 2018 | J0006$-$0623 | J0121+1149 | 1.49 | 11.65 | $0.40 \times 0.36$ | 21.1 | 0.55" (Table 2)
- final rms: _not stated_

### Inherited from earlier work

- ACA spectral channel flagging  
  > "For the ACA data we consider the same spectral channel flagging that (cite: Shangguan2020) employed in their work" (2.1 ALMA Observations and Data Reduction) [from (cite: Shangguan2020)]
- R_1/2 half-light radius via tilted-ring method  
  > "We use $R_{\rm 1/2}$ instead of $R_e$ for consistency with the methodology employed by (cite: Bolatto2017)" (3.4 Compact Molecular Gas Distribution) [from (cite: Bolatto2017)]
- Kinematic twist criterion Delta PA>10 deg  
  > "$\Delta {\rm PA}_{\rm kin} > 10^\circ$ according to the criteria of (cite: Krajnovic2008)" (3.3 Kinemetry) [from (cite: Krajnovic2008)]

### Not stated but needed to reproduce (our reading)

- Line-free channel ranges and ACA flagged channels
- Weights/relative scaling used when concatenating 12-m and ACA
- CASA version and pipeline version
- tclean niter/threshold, image size
- Sampler settings and priors for the emcee Sérsic fit (walkers, steps, burn-in)
- Precise flux calibrator fluxes
- Exact definition of BIC 5-sigma probability threshold

## Analysis recipe

1. **Calibrate, concatenate and image CO(2-1)**: CASA pipeline, CONCAT 12m+ACA, UVCONTSUB, TCLEAN with auto-multithresh  
  > "The emission-line imaging is performed using TCLEAN with robust weighting (ROBUST = 0.5) and a channel resolution of $11$ km s$^{-1}$." (2.1 ALMA Observations and Data Reduction)
   - software: CASA
   - parameter: robust 0.5, 11 km/s channels  
  > "robust weighting (ROBUST = 0.5) and a channel resolution of $11$ km s$^{-1}$" (2.1 ALMA Observations and Data Reduction)
   - fitting: _not stated_
   - validation: Compared with ACA-only fluxes  
  > "Four of the six sources recover extra CO emission, ranging from $\sim 9\%$ to $24\%$, with an average of $\sim 12\%$." (3.1 Sensitivity of the Concatenated Data Compared to the ACA Data)
2. **Pixelwise Gaussian line fitting and moment maps**: Fit 1-3 Gaussians per pixel with adaptive binning; BIC model selection at 5 sigma; Monte Carlo errors (300 iterations)  
  > "We iterate 300 times to obtain a distribution for each parameter" (2.2 Emission-line Characterization and Map Construction)
   - software: LMFIT
   - parameter: initial width 20 km/s, max 500 km/s, S/N>=3 mask  
  > "The line width is restricted to a maximum value of 500 km s$^{-1}$." (2.2 Emission-line Characterization and Map Construction)
   - fitting: Least-squares, BIC vs straight line, 5 sigma threshold  
  > "We consider a $5\,\sigma$ probability threshold for detection." (2.2 Emission-line Characterization and Map Construction)
   - validation: Recovers ~97% of channel-summed flux in worst cases  
  > "recovers $\sim 97$ % of $S_{\rm CO(2-1)} \Delta v$ for the two worst cases" (2.2 Emission-line Characterization and Map Construction)
3. **CO luminosity and molecular gas mass**: Solomon & Vanden Bout L'CO formula, r21=0.62, alpha_CO conversion  
  > "We obtain molecular gas masses assuming a CO-to-H$_2$ conversion factor $\alpha_{\rm CO} = 3.1$" (2.3 CO(2–1) Luminosity and Molecular Gas Estimates)
   - assumption: alpha_CO = 3.1 Msun (K km/s pc2)^-1, 0.3 dex uncertainty; L'CO(2-1)/L'CO(1-0)=0.62  
  > "$\alpha_{\rm CO} = 3.1$ $M_\odot$ (K km s$^{-1}$ pc$^2$)$^{-1}$ with 0.3 dex uncertainty (cite: Sandstrom2013)" (2.3 CO(2–1) Luminosity and Molecular Gas Estimates)
   - fitting: _not stated_
   - validation: Consistent with dust-based gas masses  
  > "a value consistent with dust-based gas masses independently derived for the PG quasars" (2.3 CO(2–1) Luminosity and Molecular Gas Estimates)
4. **Sérsic fit to intensity maps**: 2D Sérsic convolved with beam, 7 free parameters, MCMC  
  > "The two-dimensional model considers seven free parameters ($I_e$, $n$, $R_e$, PA$_{\rm pho}$, $b/a$ minor-to-major axis ratio, $[x_0, y_0]$ on-sky center location, and background)" (3.2 CO(2–1) Intensity Map Modeling)
   - software: emcee
   - assumption: Oblate spheroid with intrinsic thickness q0=0.14  
  > "We set $q_0 = 0.14$ based on the mean value reported for edge-on galaxies" (3.2 CO(2–1) Intensity Map Modeling)
   - fitting: emcee affine-invariant sampler, Gaussian log-likelihood  
  > "EMCEE implements the affine invariant ensemble sampler for the Markov chain Monte Carlo sampling method" (3.2 CO(2–1) Intensity Map Modeling)
   - validation: Residual maps; R_e vs R_1/2 comparison  
  > "We find a good agreement between both measurements for the six host galaxies." (Comparison of Radial Sizes)
5. **Kinemetry of velocity maps**: Tilted-ring Fourier decomposition; k5/k1 threshold 0.02; bootstrap 100 times  
  > "we bootstrap these values within their $3\,\sigma$ error range and repeat the KINEMETRY procedure 100 times" (3.3 Kinemetry)
   - software: KINEMETRY
   - parameter: center and axis ratio fixed from Sérsic fit; ring width = half beam FWHM; 75% pixel sampling  
  > "The tilted ring thickness is set equal to half of the beam FWHM" (3.3 Kinemetry)
   - fitting: _not stated_
   - validation: Typical k5/k1 uncertainty ~0.001  
  > "Based on the typical uncertainty of $k_{5,v}/k_{1,v}$ measured for our systems ($\sim 0.001$), we adopt a threshold" (3.3 Kinemetry)
6. **Rotation velocity and dispersion**: Extract profiles along kinematic major axis; mask beam-smeared central region where gradient < 11 km/s; average, correct for inclination  
  > "we mask the data from the nucleus to the radius where the local velocity gradient decreases below the spectral resolution limit of $11$ km s$^{-1}$" (3.4 Regular Motions and Velocity Dispersion)
   - fitting: _not stated_
   - validation: _not stated_
7. **Line asymmetry non-parametric analysis**: Measure v05, v50, v95 of model line; Delta v = Δv+ + Δv-; correlate with v_LOS  
  > "Then, the line asymmetry is given simply by $\Delta v = \Delta v_{+} + \Delta v_{-}$." (3.6 Asymmetric and Complex Line Shapes)
   - fitting: Pearson correlation  
  > "with Pearson’s coefficient $r = -0.2$ to $-0.8$ and very low null-hypothesis probability ($p < 0.01$)" (3.6 Asymmetric and Complex Line Shapes)
   - validation: Simulated beam-smearing datacube  
  > "We simulate a galaxy observation datacube to exemplify the effect of beam-smearing on the observed emission line shapes." (Beam smearing effect on the observed emission line shapes)

## Software

- **CASA** : Calibration, CONCAT, UVCONTSUB, TCLEAN  
  > "We use the Common Astronomy Software Application (CASA; (cite: McMullin2007)) to reduce the ALMA data" (2.1 ALMA Observations and Data Reduction)
- **LMFIT** : Gaussian line fitting  
  > "least-squares minimization procedure implemented in the PYTHON package LMFIT" (2.2 Emission-line Characterization and Map Construction)
- **emcee** : Sérsic model fitting  
  > "We use the PYTHON package EMCEE (cite: Foreman2013) to find the best-fit model." (3.2 CO(2–1) Intensity Map Modeling)
- **KINEMETRY** : Tilted-ring kinematic analysis  
  > "tilted-ring approach as implemented in KINEMETRY (cite: Krajnovic2006)" (3.3 Kinemetry)

## Numeric results

| quantity | value | uncertainty | units | step | quote |
|---|---|---|---|---|---|
| Median CO half-light radius | 1.8 | not stated | kpc | 4 | $R_{\rm 1/2} = 0.9 - 3.7$ kpc, with a median value of 1.8 kpc |
| Molecular gas surface density | >~22 | not stated | Msun pc^-2 | 4 | the sample is characterized by $\Sigma_{\rm H_2} \gtrsim 22$ $M_\odot$ pc$^{-2}$ |
| v_rot/sigma_v range | 9-42 | not stated | dimensionless | 6 | We find $v_{\rm rot} / \sigma_v = 9$–42 for the five analyzed host galaxies |
| Mean Sérsic index | 0.87 | not stated | dimensionless | 4 | disk-like (Sérsic index $n = 0.87$) |
| Kinematic-photometric PA misalignment | ~34 | 26 | deg | 5 | misaligned on average by $\sim 34 \pm 26^\circ$ |
| PG 0050+124 velocity dispersion | 36 | 27 | km/s | 6 | PG 0050+124 / $304$ / 0.010 / $337 \pm 92$ / $36 \pm 27$ |
| Concatenated vs ACA flux excess (four sources) | ~12 average (9-24) | not stated | % | 1 | ranging from $\sim 9\%$ to $24\%$, with an average of $\sim 12\%$ |

## Qualitative findings

- Asymmetric line profiles arise mainly from beam smearing; complex profiles trace central substructure  
  > "We argue that asymmetric profiles predominantly arise from beam-smearing effects, while complex lines are predominantly associated with gas sub-structures in the central regions of the galaxies." (Conclusions)

## Claim tuples

- H: Quasar host molecular gas is more compact than in inactive galaxies | E: Sérsic fits and half-light radii compared with EDGE-CALIFA | R: Median R1/2 = 1.8 kpc, Sigma_H2 >~22 Msun/pc2 | F: Quasar hosts have exceptionally compact molecular gas disks | **supported**
- H: Gas kinematics are dominated by regular rotation | E: Kinemetry and rotation curves | R: vrot/sigma >~9; four of five regular rotators | F: Large-scale velocity field is regular | **supported**
- H: Kinematic and photometric axes misaligned with twisting | E: Kinemetry PA vs Sérsic PA | R: ~30 deg mean difference; 3 of 5 twisted | F: Evidence of misalignment and kinematic twists | **supported**

## Reasoning

- Why this data: Six brightest CO(2-1) sources of ACA sample allow deep, high-resolution imaging  
  > "These six objects constitute the brightest CO(2–1) sources within the ACA sample" (2.1 ALMA Observations and Data Reduction)
- Why this method: _not stated_
- Alternative: Multiple Gaussians preferred over high-order Gauss-Hermite for line shapes  
  > "We find that multiple Gaussians perform better than a high-order Gauss-Hermite function" (2.2 Emission-line Characterization and Map Construction)
- How they decided it was enough: _not stated_
- Limitation (authors): Small and possibly biased sample  
  > "Although our sample is admittedly small and possibly biased" (4 Discussion)
- Limitation (authors): Surface density depends on alpha_CO choice  
  > "Our statements on $\Sigma_{\rm H_2}$ obviously depend on the choice of $\alpha_{\rm CO}$." (3.4 Compact Molecular Gas Distribution)
- Caveat (inferred, ours): Single Sérsic plus fixed q0 for inclination; kinematic center fixed to photometric center
- Caveat (inferred, ours): Beam smearing affects PA and dispersion estimates at ~1 arcsec resolution
- Caveat (inferred, ours): Only six sources, selected as brightest in CO
- Caveat (inferred, ours): Inactive comparison sample uses CO(1-0) with different alpha_CO and resolution

## Reproducibility

- Data public (paper): ALMA program 2018.1.00006.S cited; public status not stated  
  > "This paper makes use of the following ALMA data: ADS/JAO.ALMA#2018.1.00006.S." (Acknowledgments)
- Products in archive: _not stated_
- Missing: CASA version
- Missing: Line-free channel lists
- Missing: emcee configuration
- Missing: ACA data from Shangguan2020 program
- Data volume (inferred): ~50-150 GB raw for 12-m plus ACA
- Score (inferred): 3/5, Data in archive and imaging parameters given, but versions, MCMC settings and channel selections are missing.
- Rediscovery candidate: yes, Data from the archive (likely public), clear recipe, numeric results such as R1/2 and v_rot/sigma.

## Links

- Method: (cite: Krajnovic2006) (KINEMETRY method)
- Method: (cite: Foreman2013) (emcee sampler)
- Companion: (cite: Shangguan2020) (Cycle 5 ACA CO survey of PG quasars)
- Companion: (cite: Shangguan2020b) (Star formation in PG quasar hosts)
- Related: Palomar-Green quasar survey
- Related: EDGE-CALIFA
- Related: xCOLD GASS

## Checks

```json
{
 "quotes": 85,
 "quotes_ok": 85,
 "quote_pass_rate": 1.0,
 "quotes_too_long": 0,
 "unsupported_facts": 0,
 "project_codes": 1,
 "codes_not_in_text": [],
 "codes_not_in_obscore": [],
 "obscore_codes_not_in_card": [],
 "codes_printed_but_missing": [],
 "numeric_results": 7,
 "numeric_problems": 0,
 "fill": {
  "facts": 102,
  "stated": 71,
  "rate": 0.696
 },
 "evidence_ok": true
}
```
