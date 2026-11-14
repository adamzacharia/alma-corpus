# Closing the feedback-feeding loop of the radio galaxy 3C 84

`2024NatAs...8..256O` | Nature Astronomy 2024 | first author: Oosterloo, Tom | arXiv: 2312.00917 | DOI: 10.1038/s41550-023-02138-y

Card schema 1.0 | model claude-sonnet-5-5-claude-code | depth full | type archival_reuse

## Science

- Fields: agn_and_quasars, galaxy_clusters_and_sz, nearby_galaxies
- Question: Do kpc-sized cold molecular gas filaments in NGC 1275 (host of 3C 84) flow onto and feed the circumnuclear disc (CND), closing the feedback-feeding loop of the AGN?  
  > "Here we present high-resolution ALMA observations that clearly show that kpc-sized filaments of molecular gas are indeed accreting onto the CND." (Introduction); "no observations were yet able to simultaneously trace both these inner structures and explore, with high enough spatial resolution, whether any connection between them exists." (Introduction)
- Target **NGC 1275 (3C 84, Perseus A)**: coordinates _not stated_; z/distance z = 0.01756 (V_hel = 5264 km/s); luminosity distance 76.2 Mpc; 0.1 arcsec = 36 pc  
  > "NGC 1275 is the brightest galaxy of the Perseus cluster and hosts the radio-loud AGN 3C 84 (Perseus A)." (Target information); "In this paper we assume a redshift for NGC 1275 of $z = 0.01756; V_{\rm hel} = 5264$ km s$^{-1}$." (Target information); "Assuming a Hubble constant of $H_\circ = 69.6$ km s$^{-1}$ Mpc$^{-1}$, $\Omega_{\rm M} = 0.286$ and $\Omega_{\rm vac} = 0.714$, this gives" (Target information); "a luminosity distance of 76.2 Mpc." (Target information); distance from assumed redshift with H0 = 69.6 km/s/Mpc, Omega_M = 0.286, Omega_vac = 0.714 (no citation given)  
  > "NGC 1275 is the brightest galaxy of the Perseus cluster and hosts the radio-loud AGN 3C 84 (Perseus A)." (Target information); "In this paper we assume a redshift for NGC 1275 of $z = 0.01756; V_{\rm hel} = 5264$ km s$^{-1}$." (Target information); "Assuming a Hubble constant of $H_\circ = 69.6$ km s$^{-1}$ Mpc$^{-1}$, $\Omega_{\rm M} = 0.286$ and $\Omega_{\rm vac} = 0.714$, this gives" (Target information); "a luminosity distance of 76.2 Mpc." (Target information)

## Data provenance

- ALMA projects: 2017.0.01257.S
- bands: _not stated_
- frequencies and spectral setup: _not stated_
- continuum bandwidth: _not stated_
- arrays: _not stated_
- configurations: _not stated_
- baselines: _not stated_
- angular resolution: beam 0.19 x 0.10 arcsec (P.A. = 4.8 deg), 68 x 36 pc  
  > "The beam size is 0$\overset{\prime\prime}{.}$19 $\times$ 0$\overset{\prime\prime}{.}$10 (P.A. = 4$\overset{\circ}{.}$8), corresponding to 68 $\times$ 36 pc" (Observations and data reduction)
- max recoverable scale: 1.3 arcsec  
  > "The largest recoverable scale of the ALMA array used in the observations is 1$\overset{\prime\prime}{.}$3." (Molecular gas masses)
- sensitivity: 0.36 mJy/beam per channel (new cube); 1 mJy/beam at 20 km/s in original cube  
  > "the noise level in the channels is 0.36 mJy beam$^{-1}$" (Observations and data reduction); "(1 mJy beam$^{-1}$ for a spectral resolution of 20 km s$^{-1}$)" (Observations and data reduction)
- time on source: about 1 hr on 3C 84; bandpass calibrator J0237+2848 observed 5 minutes  
  > "the bandpass calibrator was observed for only 5 minutes, compared to about 1 hr for 3C 84." (Observations and data reduction)
- observing dates: _not stated_
- pi or archival as stated: archival ALMA visibility data of project 2017.0.01257.S, originally published by Nagai et al.  
  > "we reprocessed the archival ALMA visibility data." (Observations and data reduction)
- Line: CO J=2-1 (not stated)
- External data: SMA CO flux integral of the inner and western filaments, 106.0 +/- 3.4 Jy km/s (western filament 34.1 +/- 2.3), used for comparison  
  > "The combined flux integral of their inner and the western filaments, which correspond to most of the emission in our data, is $106.0 \pm 3.4$ Jy km s$^{-1}$." (Molecular gas masses) [from Ho et al. (cite: Ho09)]
- External data: Radial infall velocity of the filaments of order 200 km/s, used for the accretion rate  
  > "In the models of Lim et al.(cite: Lim08) for the radial infall of the filaments towards the CND, they do so with velocities of the order of 200 km s$^{-1}$." (Accretion rates) [from Lim et al. (cite: Lim08)]
- External data: Standard-ISM alpha_CO = 4.3 Msun/(K km/s pc^2) and S_CO(2-1) = 2.4 S_CO(1-0)  
  > "which are characteristic of a standard ISM(cite: Bolatto13)" (Molecular gas masses) [from Bolatto et al. (cite: Bolatto13)]
- External data: X-ray cooling flow rate of at least 30 Msun/yr (O VI) and Halpha filament cooling rate of about 100 Msun/yr, used for comparison  
  > "the disposition rate of at least 30 $M_\odot$ yr$^{-1}$ of the X-ray cooling flow derived by Bregman et al.(cite: Bregman06)" (Molecular gas feeding 3C 84) [from Bregman et al. (cite: Bregman06); Fabian et al. (cite: Fabian11)]

## Processing

### Calibration

- pipeline or manual: ALMA-pipeline calibrated uv data, then re-processed in MIRIAD with a new bandpass calibration  
  > "All our data reduction was done using the MIRIAD software(cite: Sault95), starting with the calibrated $uv$ data produced by the ALMA pipeline." (Observations and data reduction)
- casa version: _not stated_
- pipeline version: _not stated_
- archive products used as is: No; bandpass redone using 3C 84 itself, original pipeline cube had strong artefacts  
  > "Our strategy to improve the spectral dynamic range of the data is based on using 3C 84 itself (being an ALMA calibrator) as the bandpass calibrator." (Observations and data reduction)
- flux calibrator: _not stated_
- flux scale uncertainty: _not stated_
- self calibration: single phase-only self-calibration with a point model for 3C 84  
  > "we applied a single phase-only self-calibration to the visibilities using a point model for 3C 84." (Observations and data reduction)

### Imaging

- task: _not stated_
- deconvolver: _not stated_
- weighting robust: natural weighting  
  > "was made using natural weighting and with channels of 13.1 km s$^{-1}$ wide to which Hanning smoothing was applied" (Observations and data reduction)
- uv taper: none stated; bandpass solved only on baselines longer than 500 klambda  
  > "selecting only the $uv$ data on baselines longer than 500 k$\lambda$ in order to reduce the impact of extended line emission" (Observations and data reduction)
- cell size: _not stated_
- image size: _not stated_
- masking: _not stated_
- multiscale scales: _not stated_
- continuum subtraction: _not stated_
- line free channels: _not stated_
- primary beam correction: _not stated_
- array combination: _not stated_
- smoothing: Hanning smoothing; 13.1 km/s channels give 26.1 km/s velocity resolution  
  > "giving a velocity resolution of 26.1 km s$^{-1}$." (Observations and data reduction)
- final beam: 0.19 x 0.10 arcsec (P.A. = 4.8 deg)  
  > "The beam size is 0$\overset{\prime\prime}{.}$19 $\times$ 0$\overset{\prime\prime}{.}$10 (P.A. = 4$\overset{\circ}{.}$8)" (Observations and data reduction)
- final rms: 0.36 mJy/beam per channel  
  > "the noise level in the channels is 0.36 mJy beam$^{-1}$" (Observations and data reduction)

### Inherited from earlier work

- Original ALMA data set and its pipeline calibration (project 2017.0.01257.S), re-processed here  
  > "This paper is based on re-processing the data taken for ALMA project 2017.0.01257.S of which the original data were published by Nagai et al." (Observations and data reduction) [from Nagai et al. (cite: Nagai19)]
- Standard-ISM CO-to-H2 conversion alpha_CO = 4.3 and CO(2-1)/CO(1-0) ratio 2.4  
  > "which are characteristic of a standard ISM(cite: Bolatto13)" (Molecular gas masses) [from Bolatto et al. (cite: Bolatto13)]
- Infall velocity of 200 km/s adopted from earlier radial infall models  
  > "In the models of Lim et al.(cite: Lim08) for the radial infall of the filaments towards the CND, they do so with velocities of the order of 200 km s$^{-1}$." (Accretion rates) [from Lim et al. (cite: Lim08)]

### Not stated but needed to reproduce (our reading)

- ALMA band, spectral window setup and the rest frequency used for CO(2-1) and the systemic velocity reference
- Phase-only self-calibration solution interval and which channels or spectral windows were used
- How the line emission was modelled and subtracted from the uv data in the bandpass iterations (clean-component model, masks, number of iterations of cleaning)
- Bandpass solution details: solution interval, polynomial or per-channel, and treatment of the flux-scale
- Continuum subtraction method and line-free channels used for the final cube
- Cell size, image size, deconvolution thresholds and primary beam correction in the MIRIAD imaging
- Spatial and spectral extent of the SoFiA-2 masks around the CND and exact region definitions for filaments A, B, C and the CND used for flux integrals
- Conversion from flux integral to mass: the exact formula and distance used, and how the 0.6 Jy km/s smallest cloud was identified
- Flux scale uncertainty and flux calibrator used
- Archive project code printed as 2017.0.01257.S, which differs from the code linked by the archive (2017.1.01257.S); the correct code needs checking

## Analysis recipe

1. **phase self-calibrate on 3C 84**: Single phase-only self-calibration of pipeline-calibrated visibilities using a point model for 3C 84  
  > "Before attempting to improve the bandpass calibration, we applied a single phase-only self-calibration to the visibilities using a point model for 3C 84." (Observations and data reduction)
   - software: MIRIAD
   - assumption: 3C 84 is a point source at the phase centre for the model  
  > "using a point model for 3C 84." (Observations and data reduction)
   - fitting: _not stated_
   - validation: _not stated_
2. **re-derive the bandpass using 3C 84 itself, iteratively**: Bandpass solution from 3C 84 using only baselines longer than 500 klambda; line emission modelled and subtracted from the uv data, then bandpass redetermined; done twice  
  > "selecting only the $uv$ data on baselines longer than 500 k$\lambda$ in order to reduce the impact of extended line emission." (Observations and data reduction); "was done twice, after which successive iterations did not improve the quality of the data anymore." (Observations and data reduction)
   - software: MIRIAD
   - parameter: Baselines > 500 klambda, spatial scales smaller than about 0.4 arcsec  
  > "This limit means that for the bandpass calibration we only consider spatial scales smaller than $\sim$0$\overset{\prime\prime}{.}$4" (Observations and data reduction)
   - assumption: Line emission is much weaker than the 3C 84 continuum so the bandpass error it induces is small  
  > "the level of the continuum is much higher than that of the line emission and therefore the errors induced by this way of calibrating the data are small." (Observations and data reduction)
   - fitting: _not stated_
   - validation: Comparison of position-velocity plots of the CND from archival and re-processed data; good agreement a few beams from 3C 84  
  > "comparison of the emission only a few beams away from 3C 84 shows very good correspondence between the two data sets" (Observations and data reduction)
3. **make the final spectral cube**: Imaging with natural weighting, 13.1 km/s channels, Hanning smoothing  
  > "was made using natural weighting and with channels of 13.1 km s$^{-1}$ wide to which Hanning smoothing was applied" (Observations and data reduction)
   - software: MIRIAD
   - parameter: Velocity resolution 26.1 km/s; beam 0.19 x 0.10 arcsec; noise 0.36 mJy/beam  
  > "giving a velocity resolution of 26.1 km s$^{-1}$." (Observations and data reduction); "the noise level in the channels is 0.36 mJy beam$^{-1}$" (Observations and data reduction)
   - fitting: _not stated_
   - validation: Noise improved by a factor 3 over the original cube  
  > "This is an improvement of a factor 3 over that of the original data cube" (Observations and data reduction)
4. **make moment images (integrated line and velocity field)**: SoFiA-2 Smooth+Clip finder builds a mask from merged smoothed-cube masks; mask applied to the original cube to compute moments  
  > "We have used the Smooth+Clip finder as implemented in Sofia-2 to create a mask including all the emission to apply to the data cube for the calculations of the moments." (Moment images)
   - software: SoFiA-2
   - parameter: Spatial Gaussian kernels 0, 3, 6, 12, 24 pixels; velocity boxcar kernels 0, 3, 7 channels; noise cutoff 4 sigma  
  > "The scales of the spatial Gaussian kernels we used are 0, 3, 6, 12 and 24 pixels and of the velocity boxcar kernels 0, 3, and 7 channels." (Moment images); "The noise cutoff used was 4 $\sigma$." (Moment images)
   - fitting: _not stated_
   - validation: _not stated_
5. **examine kinematics along filaments and the CND**: Position-velocity diagrams along selected position angles and along filaments, plus velocity-field inspection, to judge infall onto the CND  
  > "position-velocity plots along two streams that seem to feed the CND." (Molecular gas feeding 3C 84); "shows the position-velocity plot along position angle 90$^\circ$ after integrating the data cube in declination." (Molecular gas feeding 3C 84)
   - parameter: PA 90 deg slice through the CND; PA 150 deg along filament D centred 0.3 arcsec W of the centre  
  > "The left panel shows the kinematics of the CND along position angle 90$^\circ$." (Molecular gas feeding 3C 84)
   - assumption: Filaments pointing toward 3C 84 with organised E-W kinematics are infalling, not pushed outward by the N-S jets  
  > "something that would not be expected if the gas is pushed outwards by the jets which are oriented N-S." (Molecular gas feeding 3C 84)
   - fitting: _not stated_
   - validation: _not stated_
6. **measure flux integrals and derive H2 masses**: Flux integrals of the full field, CND and filaments A, B, C converted to H2 mass with a CO-to-H2 conversion factor and a CO(2-1)/CO(1-0) ratio  
  > "The flux integral of the CND is $22.2 \pm 1$ Jy km s$^{-1}$" (Molecular gas masses); "If one instead assumes $\alpha_{\rm CO} = 0.8\ M_\odot$/(K km s$^{-1}$ pc$^2$), which could more appropriate for conditions found near an AGN, all masses decrease by a factor 5.4." (Molecular gas masses)
   - parameter: alpha_CO = 4.3 Msun/(K km/s pc^2) and S_CO(2-1) = 2.4 S_CO(1-0) (standard ISM); alternative alpha_CO = 0.8  
  > "Using $\alpha_{\rm CO} = 4.3\ M_\odot$/(K km s$^{-1}$ pc$^2$) and $S_{\rm CO(2-1)} = 2.4\ S_{\rm CO(1-0)}$" (Molecular gas masses)
   - assumption: Standard Galactic ISM conversion factor as default; AGN-like lower factor as alternative  
  > "It is a priori not clear which CO–to–H$_2$ conversion factor to use since the conditions in the molecular gas are likely quite different from that in the standard galaxy ISM(cite: Lim17)." (Molecular gas masses)
   - assumption: Most CO(2-1) emission recovered by the array  
  > "which suggests that we have likely recovered most of the CO(2-1) emission." (Molecular gas masses)
   - fitting: _not stated_
   - validation: Comparison of flux integrals with the SMA result of Ho et al.  
  > "which roughly corresponds to our filaments A and B which have a combined flux integral of $38.3 \pm 1.9$ Jy km s$^{-1}$." (Molecular gas masses)
7. **estimate the gas infall rate onto the CND**: Mdot = M_gas / t_dyn = M_gas (r/v)^-1 for filament gas within r = 0.7 arcsec (~250 pc), with infall velocity 200 km/s  
  > "$$\begin{equation} \dot{M} = \frac{M_{\rm gas}}{t_{\rm dyn}} = M_{\rm gas} \cdot \left(\frac{r}{v}\right)^{-1} \end{equation}$$" (Accretion rates); "If we assume such an infall velocity, this gives an estimated infall rate of about 200 $M_\odot$ yr$^{-1}$." (Accretion rates)
   - parameter: Gas mass of about 5e8 Msun inside radius 0.7 arcsec (~250 pc) for alpha_CO = 4.3; v = 200 km/s  
  > "is about $5 \times 10^8$ $M_\odot$ for $\alpha_{\rm CO} = 4.3\ M_\odot$/(K km s$^{-1}$ pc$^2$)." (Accretion rates)
   - assumption: Infall velocity 200 km/s taken from radial infall models; same conversion factor for filaments and CND  
  > "Assuming the same CO-to-H$_2$ conversion factor for the filaments and the CND and the infall velocity of 200 km s$^{-1}$ used above" (Accretion rates)
   - fitting: _not stated_
   - validation: Compared with cooling rates from the literature (X-ray cooling flow, Halpha filaments)  
  > "This compares reasonably well with the disposition rate of at least 30 $M_\odot$ yr$^{-1}$ of the X-ray cooling flow" (Molecular gas feeding 3C 84)

## Software

- **MIRIAD** : All data reduction: self-calibration, bandpass, line modelling and subtraction, imaging  
  > "All our data reduction was done using the MIRIAD software(cite: Sault95)" (Observations and data reduction)
- **SoFiA-2** : Smooth+Clip source mask and moment images (integrated line image and velocity field)  
  > "The integrated line image and the velocity field were made using the Sofia-2(cite: Westmeier21) software." (Moment images)

## Numeric results

| quantity | value | uncertainty | units | step | quote |
|---|---|---|---|---|---|
| Synthesized beam of the re-processed cube | 0.19 x 0.10 arcsec, P.A. = 4.8 deg (68 x 36 pc) | not stated | arcsec | 3 | The beam size is 0$\overset{\prime\prime}{.}$19 $\times$ 0$\overset{\prime\prime}{.}$10 (P.A. = 4$\overset{\circ}{.}$8), corresponding to 68 $\times$ 36 pc |
| Channel noise of re-processed cube | 0.36 | not stated | mJy/beam | 3 | the noise level in the channels is 0.36 mJy beam$^{-1}$ |
| CO(2-1) flux integral over the entire field of view | 112.9 | 6.0 | Jy km/s | 6 | The flux integral over the entire field of view is $112.9 \pm 6.0$ Jy km s$^{-1}$ |
| CO(2-1) flux integral of the CND | 22.2 | 1 | Jy km/s | 6 | The flux integral of the CND is $22.2 \pm 1$ Jy km s$^{-1}$ |
| CO(2-1) flux integrals of filaments A, B, C | 17.6, 20.7, 12.6 | 0.8, 1.0, 0.6 | Jy km/s | 6 | $17.6 \pm 0.8$, $20.7\pm 1.0$ and $12.6\pm 0.6$ Jy km s$^{-1}$ respectively. |
| Total H2 mass (alpha_CO = 4.3) | 2.79e9 | 0.14e9 | Msun | 6 | this gives a total H$_2$ mass of $2.79 \pm 0.14\times 10^9$ $M_\odot$ |
| H2 masses of filaments A, B, C (alpha_CO = 4.3) | 4.4e8, 5.2e8, 3.1e8 | 0.2e8, 0.3e8, 0.2e8 | Msun | 6 | the H$_2$ masses are $4.4 \pm 0.2\times 10^8$, $5.2 \pm 0.3 \times 10^8$, and $3.1 \pm 0.2 \times 10^8$ $M_\odot$ respectively. |
| H2 mass of the CND (alpha_CO = 4.3) | 5.6e8 | 0.3e8 | Msun | 6 | The H$_2$ mass of the CND is $5.6 \pm 0.3 \times 10^8$ $M_\odot$. |
| Factor by which masses decrease for alpha_CO = 0.8 | 5.4 | not stated | dimensionless | 6 | all masses decrease by a factor 5.4. |
| Infall rate of filaments within 0.7 arcsec (alpha_CO = 4.3 / 0.8) | ~200 / ~40 | not stated | Msun/yr | 7 | this gives an estimated infall rate of about 200 $M_\odot$ yr$^{-1}$.; this reduces to $\sim$40 $M_\odot$ yr$^{-1}$. |
| Infall rate of filaments A and B (alpha_CO = 4.3 / 0.8) | ~90 / ~20 | not stated | Msun/yr | 7 | this gives an infall rate of $\sim$90 $M_\odot$ yr$^{-1}$ or $\sim$20 $M_\odot$ yr$^{-1}$, depending on the conversion factor assumed. |
| Estimated disposition rate of cold gas onto the CND | 20-200 | not stated | Msun/yr | 7 | we estimate that the disposition rate of cold gas onto the CND to be in the range 20–200 $M_\odot$ yr$^{-1}$ |
| Time to build the CND from the filaments | several times 1e6 | not stated | yr | 7 | it would take just several times $10^6$ yr to build the CND. |
| Length and width of filament A | about 2.7 kpc long, ~150 pc wide | not stated | kpc, pc | 4 | has a length of about 2.7 kpc, but has a width of only $\sim$150 pc |
| Length and width of filament B | ~1.8 kpc long, 230 pc wide | not stated | kpc, pc | 4 | somewhat shorter and wider ($\sim$1.8 kpc long and 230 pc wide) |
| Velocity displacement of a cloud from filament B at about 4 arcsec | about 200 | not stated | km/s | 5 | there is a small cloud which is displaced by about 200 km s$^{-1}$ from the main filament |

## Qualitative findings

- Inner and Western filaments split into several thinner filaments with different kinematics, more complex than seen at 1 kpc resolution  
  > "split into several thinner filaments with different kinematics, thus revealing that the distribution and the kinematics of the molecular gas are much more complex than perceived from their data." (Molecular gas feeding 3C 84)
- Outer CND shows unsettled, non-regular kinematics consistent with ongoing gas accretion onto the CND  
  > "This on-going formation of the CND is further confirmed by the non-regular kinematics of the outer regions of the CND" (Closing the feedback loop)
- Accretion is organised in filamentary channels (not chaotic), though individual filaments carry angular momentum  
  > "However, the accretion itself is not chaotic but organised in the form of filamentary channels along which cold gas is funnelled into the central regions." (Molecular gas feeding 3C 84)

## Claim tuples

- H: Do kpc-scale cold molecular filaments flow onto the circumnuclear disc and feed the AGN? | E: Re-processed archival ALMA CO(2-1) data with improved bandpass calibration at 50 pc resolution; moment maps and position-velocity diagrams | R: Filaments connect in position and velocity to the CND; the CND outskirts show asymmetric, unsettled kinematics | F: Cold filaments flow onto and build up the CND, closing the feedback-feeding loop | **supported**
- H: Does a different bandpass calibration scheme remove the artefacts in the archival cube? | E: Bandpass derived from 3C 84 on long baselines with iterative line subtraction, then re-imaged | R: Noise lowered by a factor 3 (0.36 vs 1 mJy/beam) and imaging artefacts eliminated, except inside about 0.2 arcsec of 3C 84 | F: Re-processed cube is of much improved quality and recovers the filaments | **supported**
- H: Is the filamentary structure more complex than seen at 1 kpc resolution? | E: Integrated line emission and velocity-field maps from the new cube | R: Inner and Western filaments split into several thinner filaments with different kinematics | F: Distribution and kinematics of molecular gas are much more complex than previously perceived | **supported**
- H: What is the cold gas infall rate onto the CND relative to the cooling flow? | E: Mdot = M_gas/t_dyn with filament H2 masses, v = 200 km/s, and two CO-to-H2 conversion factors | R: Infall rate of about 20-200 Msun/yr depending on the conversion factor | F: Rate is comparable to the X-ray cooling flow and Halpha cooling rates, but strongly dependent on the uncertain conversion factor | **partially**

## Reasoning

- Why this data: Earlier data lacked the resolution to link filaments to the CND, and the published ALMA cube was limited by bandpass artefacts  
  > "the relatively low spatial resolution of their data do not allow to separate these large filaments from the CND and to establish whether the filaments are actually accreting onto the CND." (Molecular gas feeding 3C 84)
- Why this method: 3C 84 is itself the brightest calibrator on the sky so it is used as the bandpass calibrator  
  > "there are no calibrator sources on the sky that are significantly stronger than 3C 84" (Observations and data reduction)
- Alternative: Standard ALMA pipeline bandpass (as used by Nagai et al.) rejected because the bandpass calibrator is 1 Jy versus 7 Jy for 3C 84 and observed only 5 minutes  
  > "the flux density of the bandpass calibrator used (J0237+2848) is about 1 Jy while that of 3C 84 is roughly 7 Jy." (Observations and data reduction)
- Alternative: Lower alpha_CO = 0.8 considered as an AGN-appropriate alternative to the standard 4.3  
  > "If one instead assumes $\alpha_{\rm CO} = 0.8\ M_\odot$/(K km s$^{-1}$ pc$^2$), which could more appropriate for conditions found near an AGN, all masses decrease by a factor 5.4." (Molecular gas masses)
- How they decided it was enough: Bandpass line-subtraction iterations stopped after two rounds when quality no longer improved  
  > "was done twice, after which successive iterations did not improve the quality of the data anymore." (Observations and data reduction)
- Limitation (authors): Final cube likely incorrect within about 0.2 arcsec of 3C 84 (inner CND)  
  > "our final data cube is likely incorrect within $\sim$0$\overset{\prime\prime}{.}$2 from 3C 84 (i.e. the inner part of the CND)" (Observations and data reduction)
- Limitation (authors): Absorption against the 3C 84 continuum cannot be studied because the calibration removes it  
  > "Another implication of our calibration method is that any absorption signature that would possibly be present is calibrated away" (Observations and data reduction)
- Limitation (authors): Large uncertainty in the CO-to-H2 conversion factor and thus in masses and accretion rates  
  > "Although there is a large uncertainty in which CO-to-H$_2$ conversion factor to use" (Molecular gas feeding 3C 84)
- Limitation (authors): Eastern filament lies beyond the half-power point of the ALMA primary beam, so only faint emission is detected there  
  > "is located well beyond the half-power point of the ALMA primary beam and only some faint emission is detected at that location in our observations." (Molecular gas masses)
- Caveat (inferred, ours): Infall is inferred from morphology and position-velocity connections; line-of-sight geometry could allow outflow, and no dynamical model or fit is shown
- Caveat (inferred, ours): Infall rate depends on an assumed 200 km/s velocity taken from older models and on a conversion factor uncertain by a factor 5.4
- Caveat (inferred, ours): Bandpass derived from 3C 84 with iterative line subtraction may bias faint extended emission; no quantified test of fidelity beyond comparison with the archival cube
- Caveat (inferred, ours): Mass and flux values lack stated primary-beam correction and systematic flux-scale error

## Reproducibility

- Data public (paper): Archival ALMA visibilities; calibrated data cube available at a stated link or on request  
  > "we reprocessed the archival ALMA visibility data." (Observations and data reduction); "The calibrated data cube is available from" (Data availability)
- Products in archive: _not stated_
- Code: No new code released; MIRIAD and SoFiA-2 are described as publicly available  
  > "The data were reduced using the publicly available software Miriad(cite: Sault95) and Sofia-2(cite: Westmeier21)." (Methods)
- Missing: Self-calibration solution interval and bandpass solution parameters
- Missing: Line modelling and subtraction method used in the bandpass iterations
- Missing: MIRIAD imaging parameters (cell, image size, deconvolution, primary beam correction)
- Missing: Exact regions and masks used for the filament and CND flux integrals
- Missing: Spectral window and rest-frequency setup, and ALMA band
- Data volume (inferred): Tens of GB: one archival ALMA project, single target, pipeline-calibrated measurement set needed
- Score (inferred): 3/5, Data are public and the main pipeline is described (self-cal, bandpass from 3C 84 above 500 klambda, natural weighting, SoFiA-2 kernels and cutoff, alpha_CO values, infall formula) with numeric results, but self-cal and bandpass details, line subtraction and imaging parameters are missing.
- Rediscovery candidate: yes, Public ALMA data, flux integrals and H2 masses are numeric and the moment and mass recipe is largely given, though the custom bandpass step needs inference.

## Links

- Method: Sault et al. (cite: Sault95) (MIRIAD, used for all data reduction)
- Method: Westmeier et al. (cite: Westmeier21) (SoFiA-2, used for source masks and moment images)
- Companion: Nagai et al. (cite: Nagai19) (Original publication of the same ALMA data set, with the CND analysis and the pipeline-calibrated cube)
- Companion: Ho et al. (cite: Ho09) (SMA CO observations used for flux comparison)
- Companion: Lim et al. (cite: Lim08) (Earlier lower-resolution CO filament observations and infall models)
- Related: ALMA project 2017.0.01257.S

## Checks

```json
{
 "quotes": 102,
 "quotes_ok": 102,
 "quote_pass_rate": 1.0,
 "quotes_too_long": 0,
 "unsupported_facts": 0,
 "project_codes": 1,
 "codes_not_in_text": [],
 "codes_not_in_obscore": [
  "2017.0.01257.S"
 ],
 "obscore_codes_not_in_card": [
  "2017.1.01257.S"
 ],
 "codes_printed_but_missing": [],
 "numeric_results": 16,
 "numeric_problems": 0,
 "fill": {
  "facts": 95,
  "stated": 62,
  "rate": 0.653
 },
 "evidence_ok": true
}
```
