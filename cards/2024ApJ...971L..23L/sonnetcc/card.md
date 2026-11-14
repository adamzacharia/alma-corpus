# Polarization Substructure in the Spiral-dominated HH 111 Disk: Evidence for Grain Growth

`2024ApJ...971L..23L` | The Astrophysical Journal Letters 2024 | first author: Lee, Chin-Fei | arXiv: 2407.20484 | DOI: 10.3847/2041-8213/ad68e1

Card schema 1.0 | model claude-sonnet-5-5-claude-code | depth full | type observational_alma_primary

## Science

- Fields: protoplanetary_disks, star_formation
- Question: What produces the dust polarization in the HH 111 inner envelope and spiral-dominated disk (magnetically aligned grains vs dust self-scattering), and does it indicate grain growth  
  > "In order to better determine the origin of the dust polarization, here we report the dust polarization detection at 2.4 times as high resolution and the modeling with the two polarization mechanisms." (Introduction)
- Target **HH 111 protostellar disk and inner envelope**: coordinates _not stated_; z/distance ~400 pc  
  > "located in Orion at a distance of $\sim$ 400 pc" (Introduction); distance from _not stated_

## Data provenance

- ALMA projects: 2015.1.00037.S, 2017.1.00044.S, 2016.1.00389.S
- bands: Band 7 (~870 um) polarization in Cycles 3 and 5; Band 6 (1.3 mm, 231 GHz) archival map used for the disk model  
  > "Polarization observations toward the HH 111 system were carried out with ALMA in Band 7 in Cycle 3 (Project ID: 2015.1.00037.S) in 2016 and Cycle 5 (Project ID: 2017.1.00044S) in 2017." (Observations); "this disk has also been mapped in ALMA Band 6 at" (Fiducial Disk Model)
- frequencies and spectral setup: four continuum windows centered at 336.5, 338.5, 348.5, and 350.5 GHz  
  > "The correlator was set up to have four continuum windows, centered at 336.5, 338.5, 348.5, and 350.5 GHz" (Observations)
- continuum bandwidth: ~8 GHz total, centered at 343.5 GHz (lambda ~870 um)  
  > "for a total bandwidth of $\sim$ 8 GHz centered at 343.5 GHz" (Observations)
- arrays: _not stated_
- configurations: _not stated_
- baselines: ~14-8550 m after combining the two cycles  
  > "The projected baseline lengths were $\sim$ 14-8550 m, after combining the observations in the two cycles." (Observations)
- angular resolution: 0.080x0.070, 0.062x0.046, 0.041x0.030 arcsec for robust 2, 0.5, 0  
  > "The resulting resolutions are $0^{\prime\prime}_{^\textrm{.}}080$$\times$$0^{\prime\prime}_{^\textrm{.}}070$, $0^{\prime\prime}_{^\textrm{.}}062$$\times$$0^{\prime\prime}_{^\textrm{.}}046$, and $0^{\prime\prime}_{^\textrm{.}}041$$\times$$0^{\prime\prime}_{^\textrm{.}}030$, respectively." (Observations)
- max recoverable scale: ~1.4 arcsec  
  > "The maximum recoverable size (MRS) scale was $\sim$ $1^{\prime\prime}_{^\textrm{.}}4$, enough to cover the disk seen in the continuum." (Observations)
- sensitivity: Stokes I noise ~100, 80, 50 uJy/beam (186, 290, 417 mK); Stokes Q/U noise ~16, 18, 26 uJy/beam for robust 2, 0.5, 0  
  > "the noise levels $\sigma$ are $\sim$ 100 $\mu$Jy beam$^{-1}$ (186 mK), 80 $\mu$Jy beam$^{-1}$ (290 mK), and 50 $\mu$Jy beam$^{-1}$ (417 mK), respectively" (Observations); "the noise levels $\sigma_p$ are $\sim$ 16 $\mu$Jy beam$^{-1}$ (30 mK), 18 $\mu$Jy beam$^{-1}$ (65 mK), and 26 $\mu$Jy beam$^{-1}$ (217 mK), respectively" (Observations)
- time on source: _not stated_
- observing dates: Cycle 3 in 2016 and Cycle 5 in 2017  
  > "Polarization observations toward the HH 111 system were carried out with ALMA in Band 7 in Cycle 3 (Project ID: 2015.1.00037.S) in 2016 and Cycle 5 (Project ID: 2017.1.00044S) in 2017." (Observations)
- pi or archival as stated: _not stated_
- Other facility **VLA Band Ka**: 9.1 mm (32.9 GHz) map at ~0.07 arcsec used with ALMA Bands 7 and 6 to constrain the disk model and opacity law  
  > "VLA Band Ka at $\lambda \sim 9.1$ mm (or 32.9 GHz)" (Fiducial Disk Model)
- External data: VLA Band Ka 9.1 mm (32.9 GHz) map of the HH 111 disk  
  > "VLA Band Ka at $\lambda \sim 9.1$ mm (or 32.9 GHz)" (Fiducial Disk Model) [from (cite: Tobin2020)]
- External data: Total protostar plus disk mass of ~1.8 Msun  
  > "Since the protostar and disk were previously found to have a total mass of $\sim$ 1.8 $M_\odot$ (cite: Lee2016HH111)" (Fiducial Disk Model) [from (cite: Lee2016HH111)]
- External data: Disk tilted ~18 deg away from edge-on  
  > "consistent with the disk tilted only by $\sim$ 18$^\circ$ away from being edge-on (cite: Lee2020HH111)" (Results) [from (cite: Lee2020HH111)]
- External data: Inner envelope gas temperature ~40 K from C18O  
  > "which is $\sim$ 40 K (cite: Lee2010)" (Origin of the Dust Polarization in the Inner Envelope) [from (cite: Lee2010)]
- External data: DSHARP dust opacities (compact grains, MRN size distribution) used for the self-scattering model  
  > "Recently DSHARP dust opacities have been used to model the dust emission in protoplanetary disks (cite: Birnstiel2018), assuming compact grains with a MRN size distribution." (Dust Self-Scattering) [from (cite: Birnstiel2018)]
- External data: Scattering efficient for maximum grain size ~70-210 um (peak ~140 um) at 870 um  
  > "dust scattering is efficient when the maximum grain size $a_\textrm{\scriptsize max}$ $\sim$ 70-210 $\mu$m (with a peak at $\sim$ 140 $\mu$m)" (Dust Self-Scattering) [from (cite: Kataoka2015)]
- Simulation/model as data: Fiducial flared disk model with a pair of trailing logarithmic spiral arms, adopted from earlier work and compared with the polarization maps  
  > "To construct the fiducial model, we adopt the same flared disk model previously used to model the continuum map of this disk obtained at a similar resolution in (cite: Lee2020HH111)." (Disk Model)
- Simulation/model as data: RADMC-3D dust self-scattering polarization model of the disk  
  > "We use RADMC-3D (cite: Dullemond2012) to calculate the dust polarization due to dust self-scattering." (Dust Self-Scattering)

## Processing

### Calibration

- pipeline or manual: calibrated with CASA (pipeline vs manual not stated)  
  > "the $uv$ data were calibrated with the Common Astronomy Software Applications (CASA) package" (Observations)
- casa version: _not stated_
- pipeline version: _not stated_
- archive products used as is: _not stated_
- flux calibrator: _not stated_
- flux scale uncertainty: _not stated_
- self calibration: phase-only self-calibration  
  > "We also performed a phase-only self-calibration to improve the map fidelity." (Observations)

### Imaging

- task: _not stated_
- deconvolver: _not stated_
- weighting robust: robust = 2, 0.5, 0  
  > "we used 3 decreasing robust factors for the $uv$ weighting in making the maps. The robust factors are 2, 0.5, and 0." (Observations)
- uv taper: _not stated_
- cell size: _not stated_
- image size: _not stated_
- masking: _not stated_
- multiscale scales: _not stated_
- continuum subtraction: _not stated_
- line free channels: _not stated_
- primary beam correction: _not stated_
- array combination: Cycle 3 and Cycle 5 calibrated data combined into one data set for mapping  
  > "The calibrated data from the two cycles were then combined into one calibrated data for mapping." (Observations)
- smoothing: _not stated_
- final beam: 0.080x0.070, 0.062x0.046, 0.041x0.030 arcsec  
  > "The resulting resolutions are $0^{\prime\prime}_{^\textrm{.}}080$$\times$$0^{\prime\prime}_{^\textrm{.}}070$, $0^{\prime\prime}_{^\textrm{.}}062$$\times$$0^{\prime\prime}_{^\textrm{.}}046$, and $0^{\prime\prime}_{^\textrm{.}}041$$\times$$0^{\prime\prime}_{^\textrm{.}}030$, respectively." (Observations)
- final rms: Stokes I ~100, 80, 50 uJy/beam; Stokes Q/U ~16, 18, 26 uJy/beam  
  > "the noise levels $\sigma$ are $\sim$ 100 $\mu$Jy beam$^{-1}$ (186 mK), 80 $\mu$Jy beam$^{-1}$ (290 mK), and 50 $\mu$Jy beam$^{-1}$ (417 mK), respectively" (Observations); "the noise levels $\sigma_p$ are $\sim$ 16 $\mu$Jy beam$^{-1}$ (30 mK), 18 $\mu$Jy beam$^{-1}$ (65 mK), and 26 $\mu$Jy beam$^{-1}$ (217 mK), respectively" (Observations)

### Inherited from earlier work

- Details of the Cycle 3 and Cycle 5 observations  
  > "Since the details of the observations in Cycles 3 and 5 have been reported in (cite: Lee2018Pdisk) and (cite: Lee2020HH111), respectively, we only recap the observation information most directly relevant to our investigation." (Observations) [from (cite: Lee2018Pdisk) for Cycle 3 and (cite: Lee2020HH111) for Cycle 5]
- Flared disk model (density and temperature structure) used as the fiducial model  
  > "we adopt the same flared disk model previously used to model the continuum map of this disk obtained at a similar resolution in (cite: Lee2020HH111)" (Disk Model) [from (cite: Lee2020HH111)]
- Logarithmic spiral structure excited by gravitational instability  
  > "They are assumed to follow the logarithmic structure as excited by gravitational instability (GI) due to the self gravity of the disk (cite: Lee2020HH111)" (Disk Model) [from (cite: Lee2020HH111)]
- Radiative transfer code for dust emission and magnetically aligned grain polarization  
  > "We use the radiative transfer code reported in (cite: Lee2021Pdisk) to calculate the dust emission from the model" (Fiducial Disk Model) [from (cite: Lee2021Pdisk)]

### Not stated but needed to reproduce (our reading)

- Which source was the ALMA flux calibrator and the absolute flux scale uncertainty in each cycle
- CASA version and whether the standard pipeline or manual scripts were used
- Self-calibration details: solution intervals, number of iterations, reference antenna, and which data went into the self-cal model
- How the Cycle 3 and Cycle 5 data were aligned (astrometry, relative flux scaling) before combination
- tclean settings: deconvolver, masks, cleaning threshold, niter, cell and image size, Stokes Q/U imaging and polarization leakage calibration
- Primary beam correction treatment and line-free channel handling (continuum windows only)
- Reduction of the archival Band 6 data (2016.1.00389.S) and the VLA Ka map: beams, calibration, imaging
- Source coordinates and the origin of the 400 pc distance
- The radiative transfer code of Lee et al. 2021 is not given here; the aligned-grain polarization model, inclination and field geometries are not fully specified
- RADMC-3D setup: photon number, scattering treatment, inclination and position angle, and the DSHARP opacity files used
- Disk model fitting is done by eye, so no fit statistics, uncertainty method, or priors are available

## Analysis recipe

1. **Calibrate and image Stokes I, Q, U**: CASA calibration of both cycles, phase-only self-calibration, combination of the two cycles, and imaging with three robust values  
  > "In both cycles, the $uv$ data were calibrated with the Common Astronomy Software Applications (CASA) package" (Observations); "The calibrated data from the two cycles were then combined into one calibrated data for mapping." (Observations)
   - software: CASA
   - parameter: robust = 2, 0.5, 0  
  > "The robust factors are 2, 0.5, and 0." (Observations)
   - parameter: Bandpass J5010+1800, gain J0552+0313, polarization J0522-3627  
  > "with quasars J5010+1800, J0552+0313, and J0522-3627 as bandpass, gain, and polarization calibrators, respectively" (Observations)
   - fitting: _not stated_
   - validation: _not stated_
2. **Derive polarized intensity, fraction and orientation**: Bias-corrected polarized intensity from Q and U, polarization fraction P = P_i/I, orientations as E vectors  
  > "and thus is bias-corrected" (Observations); "The fraction of the polarization is then defined as $P=P_i/I$." (Observations); "Polarization orientations are defined by the $E$ vectors." (Observations)
   - fitting: _not stated_
   - validation: Instrumental error on P expected to be below ~0.2% for the disk at the phase center  
  > "the instrumental error on $P$ is expected to be $\lesssim$ 0.2% for the disk at the phase center" (Observations)
3. **Interpret envelope polarization as aligned grains**: Rotate polarization orientation by 90 deg to get the magnetic field orientation, assuming optically thin thermal emission  
  > "the dust polarization is likely due to thermal emission of the dust and magnetic field orientation can be obtained by rotating the polarization orientation by 90$^\circ$" (Origin of the Dust Polarization in the Inner Envelope)
   - assumption: Envelope brightness temperature ~1-6 K is far below the ~40 K gas temperature, so the continuum is optically thin  
  > "The inner envelope has a brightness temperature of $\sim$ 1$-$6 K" (Origin of the Dust Polarization in the Inner Envelope); "Therefore, the continuum emission is optically thin at the observed wavelength." (Origin of the Dust Polarization in the Inner Envelope)
   - fitting: _not stated_
   - validation: _not stated_
4. **Build the fiducial disk model from multi-band intensity**: Radiative transfer model of the flared disk with spiral arms, fit by eye to Band 7, Band 6 and Band Ka intensity, with density set by Toomre Q ~1 at the turnover radius  
  > "We use the radiative transfer code reported in (cite: Lee2021Pdisk) to calculate the dust emission from the model and fit (by eye) it roughly to the observed maps." (Fiducial Disk Model); "Then, since the spiral arms appears to be excited by GI (cite: Lee2020HH111), the Toomre Q parameters there are required to be $\sim$ 1-2" (Fiducial Disk Model)
   - software: radiative transfer code of Lee et al. 2021, ParaView
   - parameter: T_t ~26 K, q ~0.65, rho_t ~3.6e-16 g cm^-3  
  > "$T_\mathrm{t}\sim 26$ K, $q \sim 0.65$" (Fiducial Disk Model)
   - parameter: kappa_0 ~0.12 and beta ~1.4 for the opacity law  
  > "$\kappa_0 \sim 0.12$ cm$^{-2}$ g$^{-1}$, and $\beta \sim 1.4$ can roughly reproduce the observed disk emission in Bands 7 and 6" (Fiducial Disk Model)
   - parameter: Toomre Q ~1 at R_t  
  > "The value of $\rho_\mathrm{t}$ is set to have Toomre Q parameter of $\sim$ 1 at $R_\mathrm{t}$" (Fiducial Disk Model)
   - assumption: Purely thermal dust emission, LTE everywhere  
  > "we assume that the dust emission is purely thermal and the disk is everywhere in LTE" (Fiducial Disk Model)
   - assumption: Gas to dust mass ratio ~100  
  > "Assuming that the disk also contains gas with a gas to dust mass ratio of $\sim$ 100" (Disk Model)
   - assumption: Density power-law index n = 2.5  
  > "In order to simplify our fitting, we assume $n=2.5$." (Fiducial Disk Model)
   - assumption: Dust opacity law kappa_lambda = kappa_0 (9.1 mm/lambda)^beta  
  > "With multi-band observations, we can also define an opacity law" (Fiducial Disk Model)
   - fitting: Fit by eye, no sampler or likelihood  
  > "fit (by eye) it roughly to the observed maps" (Fiducial Disk Model)
   - validation: Spiral parameters agree with earlier work and expected scale height is similar to the best-fit value  
  > "the spiral parameters $a$ and $R_s$ are in good agreement with those previously reported in (cite: Lee2020HH111)" (Fiducial Disk Model); "The expected scale height in vertical hydrostatic equilibrium is $h_\mathrm{t}^e \sim$ 17.3 au, similar to the best-fit value of $h_\mathrm{t}$" (Fiducial Disk Model)
5. **Test magnetically aligned grains in the disk**: Generate Band 7 polarization maps from the fiducial model with highly pinched poloidal fields and with toroidal fields, and compare patterns with observations  
  > "In the following, we present the polarization results of the model for the two field morphologies separately in order to check these possibilities." (Magnetically Aligned Grains)
   - software: radiative transfer code of Lee et al. 2021
   - parameter: alpha = 0.1 (maximum polarization fraction in an optically thin region)  
  > "Here $\alpha = 0.1$ is used to produce the small polarization degree of $\sim$ 2% as observed in the disk" (Magnetically Aligned Grains)
   - assumption: Grains aligned with long axis perpendicular to the field lines  
  > "magnetically aligned grains have their long axis perpendicular to the field lines" (Magnetically Aligned Grains)
   - fitting: _not stated_
   - validation: Qualitative comparison of orientation and polarization gap patterns with the observed map  
  > "In summary, it is unclear if the observed dust polarization of the disk can be due to magnetic alignment of the dust grains." (Magnetically Aligned Grains)
6. **Test dust self-scattering in the disk**: RADMC-3D polarization from DSHARP grains with a_max of 170 um, with absorption opacity scaled to 3.2 cm^2 per g of dust and the disk temperature raised by ~1.3  
  > "We use RADMC-3D (cite: Dullemond2012) to calculate the dust polarization due to dust self-scattering." (Dust Self-Scattering); "the disk temperature is increased by a factor of $\sim$ 1.3 in order to roughly match the observed brightness temperature in the disk" (Dust Self-Scattering)
   - software: RADMC-3D
   - parameter: DSHARP grains with a_max = 170 um  
  > "we adopt the DSHARP grains with $a_\textrm{\scriptsize max}$ of 170 $\mu$m" (Dust Self-Scattering)
   - parameter: Absorption opacity ~1.4 scaled up to 3.2 cm^2 per g of dust  
  > "The dust absorption opacity is $\sim$ 1.4 cm$^2$ per gram of dust but is scaled up to 3.2 cm$^2$ per gram of dust." (Dust Self-Scattering)
   - parameter: Scattering opacity ~10 cm^2 per g, albedo ~0.76  
  > "The scattering opacity is $\sim$ 10 cm$^2$ per gram of dust, giving rise an albedo of $\sim$ 0.76." (Dust Self-Scattering)
   - assumption: Compact grains with MRN size distribution (DSHARP); porous grains could give the scaled opacity combination  
  > "Note that this combination could be obtained if using porous grains (cite: Tazaki2019)." (Dust Self-Scattering)
   - fitting: _not stated_
   - validation: Model reproduces ~2% polarization degree, minor-axis orientation on the near side, azimuthal orientation at the disk edges and the anticorrelation with the spiral arms; fails on near-far asymmetry and upper rim  
  > "The polarization degree is $\sim$ 2%, roughly consistent with the observation." (Dust Self-Scattering); "no clear near-far side asymmetry is seen in the polarized intensity, inconsistent with the observed" (Dust Self-Scattering)
7. **Infer grain size from the best scattering model**: Conclude that self-scattering by grains of ~150 um dominates the disk polarization, supported by the opacity index beta ~1.4  
  > "Thus, our result indicates a grain growth in the disk to a size of $\sim$ 150 $\mu$m." (Dust Self-Scattering)
   - fitting: _not stated_
   - validation: _not stated_

## Software

- **CASA** : Calibration of the ALMA uv data  
  > "the $uv$ data were calibrated with the Common Astronomy Software Applications (CASA) package" (Observations)
- **RADMC-3D** : Dust self-scattering polarization model  
  > "We use RADMC-3D (cite: Dullemond2012) to calculate the dust polarization due to dust self-scattering." (Dust Self-Scattering)
- **ParaView** : Volume rendering of the model density and temperature  
  > "produced by the visualization application ParaView using volume rendering (cite: Ahrens2005)" (Fiducial Disk Model)
- **Radiative transfer code of Lee et al. 2021** : Dust emission model and aligned-grain polarization  
  > "We use the radiative transfer code reported in (cite: Lee2021Pdisk) to calculate the dust emission from the model" (Fiducial Disk Model)

## Numeric results

| quantity | value | uncertainty | units | step | quote |
|---|---|---|---|---|---|
| Polarization degree in the inner envelope | ~6% | not stated | percent | 2 | The polarization degree is $\sim$ 6% in the envelope but decreases to $\sim$ 2% in the disk. |
| Polarization degree in the disk | ~2% | not stated | percent | 2 | The polarization degree is $\sim$ 6% in the envelope but decreases to $\sim$ 2% in the disk. |
| Disk dust temperature index q | ~0.65 | not stated | dimensionless | 4 | $T_\mathrm{t}\sim 26$ K, $q \sim 0.65$ |
| Midplane temperature at R_t | ~26 | not stated | K | 4 | $T_\mathrm{t}\sim 26$ K, $q \sim 0.65$ |
| Dust opacity spectral index beta | ~1.4 | not stated | dimensionless | 4 | $\kappa_0 \sim 0.12$ cm$^{-2}$ g$^{-1}$, and $\beta \sim 1.4$ can roughly reproduce the observed disk emission in Bands 7 and 6 |
| Dust opacity kappa at 0.87, 1.3 and 9.1 mm | 3.2, 1.8, 0.12 | not stated | cm^2 per g of dust | 4 | The resulting $\kappa_\lambda$ values are 3.2, 1.8, 0.12 cm$^2$ per gram of dust at $\lambda=$ 0.87, 1.3, and 9.1 mm, respectively. |
| Mean dust surface density at R_t | ~0.22 | not stated | g cm^-2 | 4 | The resulting mean dust surface density $\Sigma_t/100$ is $\sim 0.22$ g cm$^{-2}$ at $R_\mathrm{t}$ |
| Disk mass | ~0.58 | not stated | Msun | 4 | The resulting disk mass $M_d$ is $\sim$ 0.58 $M_\odot$. |
| Protostar mass | ~1.22 | not stated | Msun | 4 | the protostar has a mass of $\sim$ 1.22 $M_\odot$. |
| Disk to protostar mass ratio | ~0.48 | not stated | dimensionless | 4 | Therefore the disk to protostar mass ratio is $\sim$ 0.48, and thus the disk is massive enough to excite GI for 2 prominent spiral arms |
| Scale height to radius ratio at R_t | ~0.1 | not stated | dimensionless | 4 | The scale height to radius ratio at $R_\mathrm{t}$ is $\sim$ 0.1 |
| Aligned-grain parameter alpha | 0.1 | not stated | dimensionless | 5 | Here $\alpha = 0.1$ is used to produce the small polarization degree of $\sim$ 2% as observed in the disk |
| Albedo of the DSHARP 170 um grains with scaled absorption opacity | ~0.76 | not stated | dimensionless | 6 | The scattering opacity is $\sim$ 10 cm$^2$ per gram of dust, giving rise an albedo of $\sim$ 0.76. |
| Temperature increase factor in the scattering model | ~1.3 | not stated | dimensionless | 6 | the disk temperature is increased by a factor of $\sim$ 1.3 in order to roughly match the observed brightness temperature in the disk |
| Inferred grain size | ~150 | not stated | um | 7 | Thus, our result indicates a grain growth in the disk to a size of $\sim$ 150 $\mu$m. |

## Qualitative findings

- Polarized intensity and degree are lower in the spiral arms and higher in between the arms  
  > "This suggests an anticorrelation between the spiral arms and the polarized intensity (and thus the polarization degree)." (Results)
- Inner envelope magnetic field is mainly toroidal  
  > "the magnetic fields in the inner envelope are almost everywhere parallel to the major axis and are, thus, mainly toroidal" (Origin of the Dust Polarization in the Inner Envelope)
- Interarms are sandwiched and illuminated by two brighter arms, giving higher scattered polarized intensity  
  > "The interarms are sandwiched and illuminated by two brighter spiral arms and thus have higher polarized intensity." (Dust Self-Scattering)

## Claim tuples

- H: Is the envelope polarization due to magnetically aligned grains | E: Rotated the observed polarization orientations by 90 deg, assuming optically thin emission | R: Polarization is almost everywhere parallel to the minor axis with ~6% degree | F: Envelope polarization is likely from aligned grains tracing a mainly toroidal field | **supported**
- H: Does the disk polarized intensity correlate with the spiral arms | E: Mapped Stokes I and polarized intensity at three resolutions | R: Polarized intensity is lower in the arms and higher in the interarms | F: The polarized intensity is anticorrelated with the spiral arms, though the inner NE arm is unresolved | **supported**
- H: Can magnetically aligned grains explain the disk polarization | E: Modeled poloidal and toroidal field configurations in the fiducial disk with alpha = 0.1 | R: Poloidal fields match only the far-side azimuthal pattern; toroidal fields fail for most orientations; both give polarization along the arms opposite to observed | F: It is unclear if magnetic alignment explains the disk polarization | **partially**
- H: Can dust self-scattering explain the disk polarization and indicate grain growth | E: RADMC-3D self-scattering model with DSHARP grains of a_max 170 um in the fiducial disk | R: Reproduces ~2% degree, minor-axis orientation on the near side, azimuthal orientation at edges, and the anticorrelation with arms, but not the near-far asymmetry | F: Polarization is likely dominated by self-scattering by grains grown to ~150 um, with possible contributions from other mechanisms | **partially**

## Reasoning

- Why this data: Higher resolution polarization to clarify the pattern and its relation to the spiral arms  
  > "At this higher resolution, we can clarify the polarization pattern and its morphological relationship with the spiral arms." (Introduction)
- Why this method: Generate polarization maps from a fiducial disk model for the two mechanisms and compare with observations  
  > "we construct a fiducial disk model and then generate dust polarization maps with these two polarization mechanisms to compare with the dust polarization mapped here at higher resolutions" (Origin of the Dust Polarization in the Disk)
- Alternative: Pure magnetically aligned grains with poloidal or toroidal fields, and their combination, judged inconsistent with the observed orientations  
  > "Adding the toroidal fields into the model with poloidal fields will tilt the polarization orientations to one side (not shown), also inconsistent with the observed polarization orientations." (Magnetically Aligned Grains)
- Alternative: Scattering by aligned (effectively prolate) grains, as proposed for HL Tau, is considered plausible but not modeled  
  > "It is plausible that the polarization observed in our case of HH 111 is also produced by scattering aligned grains." (Dust Self-Scattering)
- How they decided it was enough: _not stated_
- Limitation (authors): Near-far side asymmetry in polarized intensity and far-side azimuthal orientation are not reproduced  
  > "Further modeling work is needed to study how to reproduce the observed near-far side asymmetry in the polarized intensity and the observed azimuthal polarization orientation on the far side." (abstract)
- Limitation (authors): Inner NE spiral arm is unresolved, so higher resolution and sensitivity are needed  
  > "observations at higher resolution and sensitivity are needed to confirm it" (Results)
- Limitation (authors): Detailed calculations including both emission and scattering by aligned grains are needed to test the scenario quantitatively  
  > "are needed to test the scenario quantitatively" (Dust Self-Scattering)
- Limitation (authors): Model spiral properties and grain properties differ from the actual ones  
  > "The detailed distribution and intensity of the polarized emission are different from the observed polarization map because the actual spirals may have different physical properties" (Dust Self-Scattering)
- Caveat (inferred, ours): Disk model is fit by eye with no uncertainties or degeneracy exploration; opacity, density and temperature are degenerate
- Caveat (inferred, ours): Grain size of ~150 um rests on one DSHARP grain demonstration with absorption opacity scaled by a factor of ~2.3, not a fit
- Caveat (inferred, ours): Self-scattering vs aligned prolate grains is not uniquely separated; paper itself calls the latter plausible
- Caveat (inferred, ours): Effect of phase self-calibration and combining two cycles on polarization fidelity not shown
- Caveat (inferred, ours): No polarization at other wavelengths to test the scattering wavelength dependence

## Reproducibility

- Data public (paper): _not stated_
- Products in archive: _not stated_
- Missing: Flux calibrator, CASA version, self-calibration and tclean settings
- Missing: Reduction recipes for Band 6 and VLA Ka data
- Missing: Aligned-grain radiative transfer code and field geometry parameters
- Missing: RADMC-3D configuration and DSHARP opacity inputs
- Data volume (inferred): Rough guess: 100-300 GB raw for two Band 7 long-baseline projects plus a Band 6 project; a few GB for calibrated continuum
- Score (inferred): 2/5, ALMA projects are named but calibration, imaging and the by-eye model fit are under-specified, and the aligned-grain code and settings are not provided.
- Rediscovery candidate: no, Recipe is incomplete (self-cal, imaging and model fitting by eye) and main results are qualitative pattern comparisons.

## Links

- Method: Lee et al. 2018 (cite: Lee2018Pdisk) (Cycle 3 observation details)
- Method: Lee et al. 2020 (cite: Lee2020HH111) (Cycle 5 observation details, spiral arms and the flared disk model)
- Method: Lee et al. 2021 (cite: Lee2021Pdisk) (Radiative transfer code with aligned-grain polarization)
- Method: Yang et al. 2017 (cite: Yang2017) (Self-scattering polarization patterns in disks, used for interpretation)
- Companion: Stephens et al. 2023 (cite: Stephens2023) (HL Tau polarization at 870 um with an analogous ring-gap anticorrelation)
- Companion: Lin et al. 2024 (cite: Lin2024) (HL Tau polarization modeling)
- Companion: Lee et al. 2023 (cite: Lee2023HH211) (HH 211 disk model with spiral arms)
- Related: 2015.1.00037.S
- Related: 2017.1.00044.S
- Related: 2016.1.00389.S
- Related: VLA Ka-band data of Tobin et al. 2020

## Checks

```json
{
 "quotes": 107,
 "quotes_ok": 107,
 "quote_pass_rate": 1.0,
 "quotes_too_long": 0,
 "unsupported_facts": 0,
 "project_codes": 3,
 "codes_not_in_text": [],
 "codes_not_in_obscore": [],
 "obscore_codes_not_in_card": [],
 "codes_printed_but_missing": [],
 "numeric_results": 15,
 "numeric_problems": 0,
 "fill": {
  "facts": 106,
  "stated": 72,
  "rate": 0.679
 },
 "evidence_ok": true
}
```
