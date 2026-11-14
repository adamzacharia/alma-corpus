# Constraining the Chemical Signatures and the Outburst Mechanism of the Class 0 Protostar HOPS 383

`2020ApJ...904...78S` | The Astrophysical Journal 2020 | first author: Sharma, Rajeeb | arXiv: 2010.05939 | DOI: 10.3847/1538-4357/abbdf4

Card schema 1.0 | model claude-sonnet-5-5-claude-code | depth full | type observational_alma_primary

## Science

- Fields: star_formation, protoplanetary_disks, astrochemistry
- Question: Can the chemical signatures (N2H+ vs HCO+) and the disk mass/stability of the outbursting Class 0 protostar HOPS 383 constrain the outburst mechanism, e.g. gravitational instability?  
  > "It is unclear if processes such as gravitational instability play an important factor at such a young stellar age." (Introduction); "making gravitational instability a viable mechanism to explain outbursts at an early age if the disk is sufficiently massive." (abstract)
- Target **HOPS 383**: coordinates _not stated_; z/distance ~400 pc  
  > "where D is the distance to the HOPS 383 ($\sim$400 pc)" (Disk Mass); "HOPS 383 is located in the Orion Molecular Cloud 3 (OMC3) region" (Introduction); distance from _not stated_

## Data provenance

- ALMA projects: 2015.1.00041.S
- bands: Band 7 (0.87 mm)  
  > "in band 7 (0.87 mm, Project code: 2015.1.00041.S)" (ALMA)
- frequencies and spectral setup: Two continuum basebands of 1.875 GHz with 31.25 MHz channels centered at 333 and 344 GHz; 12CO(3-2) baseband at 345.8 GHz (937.5 MHz window, 0.489 km/s channels); 13CO(3-2) baseband at 330.6 GHz (234.375 MHz window, 0.24 km/s channels, not detected)  
  > "The correlator setup for the 0.87 mm observations consisted of two of the basebands set to low spectral resolution 1.875 GHz continuum windows of 31.25 MHz channels." (ALMA); "These basebands were centered at 333 GHz and 344 GHz." (ALMA); "The third baseband was centered on $^{12}$CO ($J = 3 \rightarrow 2$) at 345.8 GHz with a 937.5 MHz spectral window (0.489 km s$^{-1}$ channels)" (ALMA)
- continuum bandwidth: two 1.875 GHz continuum windows  
  > "The correlator setup for the 0.87 mm observations consisted of two of the basebands set to low spectral resolution 1.875 GHz continuum windows of 31.25 MHz channels." (ALMA)
- arrays: _not stated_
- configurations: _not stated_
- baselines: 15 m to 3697 m  
  > "The baselines covered ranged from 15 m to 3697 m." (ALMA)
- angular resolution: 0.11'' x 0.10'' synthesized beam (final continuum image)  
  > "This resulted in a synthesized beam of 0.11$''$ $\times$ 0.10$''$ and RMS noise of 0.28 mJy beam$^{-1}$." (ALMA)
- max recoverable scale: _not stated_
- sensitivity: RMS 0.28 mJy/beam (continuum image)  
  > "This resulted in a synthesized beam of 0.11$''$ $\times$ 0.10$''$ and RMS noise of 0.28 mJy beam$^{-1}$." (ALMA)
- time on source: ~54 seconds  
  > "The total on source time was $\sim$54 seconds." (ALMA)
- observing dates: 2016 September 6 and 2017 July 19  
  > "HOPS 383 was observed on 2016 September 6 & 2017 July 19 with ALMA located in the Llano de Chajnantor, Chile in band 7" (ALMA)
- pi or archival as stated: Observed as part of the VANDAM Survey (Tobin et al. 2020)  
  > "as part of the VLA/ALMA Nascent Disk and Multiplicity (VANDAM) Survey" (ALMA)
- Line: 12CO J=3-2 (345.8 GHz (baseband center as stated))
- Line: 13CO J=3-2 (330.6 GHz (baseband center as stated); not detected)
- Line: N2H+ (SMA) J=3-2 (not stated)
- Line: HCO+ and H13CO+ (SMA) J=4-3 and J=3-2 (not stated)
- Other facility **SMA**: Subcompact and Extended configuration continuum and molecular line maps (12CO, 13CO, C18O, N2H+, HCO+, H13CO+, H2CO) at 0.85, 1.1 and 1.3 mm  
  > "We used the SMA located on Mauna Kea, Hawaii in the Subcompact and the Extended configuration to observe HOPS 383." (SMA)
- Other facility **VLA**: Ka-band (8 mm) continuum in C and A arrays, used for the mm-cm spectrum and ALMA+VLA visibility modeling  
  > "The observations were conducted with the Ka-band receivers and three-bit correlator mode with one 4 GHz baseband centered at 36.9 GHz (8.1 mm)" (VLA)
- External data: Archival VLA centimeter flux densities of HOPS 383 added to the mm-cm spectrum (2014 data averaged, upper limits discarded)  
  > "along with a few centimeter wavelengths data from the VLA archive reported by (cite: Madrid15)" (Millimeter to Centimeter Spectrum); "From the archival data, we averaged the 2014 data and discarded the upper-limits" (Millimeter to Centimeter Spectrum) [from (cite: Madrid15)]
- External data: Dust opacity kappa(1.3 mm) = 0.899 cm2/g for thin ice mantles, used in the analytic disk mass  
  > "We take $\kappa_{1.3 \text{ mm}} = 0.899$ cm$^2$g$^{-1}$ for thin ice mantles from dust opacity models of (cite: Ossenkopf94)" (Disk Mass) [from (cite: Ossenkopf94)]
- External data: Mean Class 0 disk mass of 0.0078 Msun from 328 Orion protostars, used for comparison  
  > "Based on the study of 328 protostars in Orion, (cite: Tobin20) found that the mean disk mass of Class 0 protostars was 0.0078 M$_{\odot}$." (Disk Mass) [from (cite: Tobin20)]
- External data: Bolometric luminosity of HOPS 383, L_bol = 7.8 Lsun, used to scale dust temperature  
  > "Also, (cite: Furlan16) found $L_{bol}$ of 7.8 $L_{\odot}$." (HOPS 383 ALMA Model) [from (cite: Furlan16)]
- External data: Earlier SED model luminosity 6-14 Lsun and inclination 41-63 deg  
  > "found luminosities of 6 $L_{\odot}< L_{bol} <$ 14 $L_{\odot}$, and inclination of 41$^{\circ} < i < 63^{\circ}$." (HOPS 383 ALMA Model) [from (cite: Safron15)]
- External data: Typical protostar mass of 0.5 Msun adopted for Toomre Q  
  > "Using a typical protostar mass of 0.5 M$_{\odot}$ ((cite: Kenyon95))" (Flux Density Derived Toomre Q) [from ((cite: Kenyon95))]
- External data: Burst rate of 1 per 1000 yr inferred for a protostar in Orion  
  > "(cite: Fischer19) inferred a burst rate of 1 per 1000 year for a protostar." (Knotty structures in the 12CO outflow) [from (cite: Fischer19)]
- Simulation/model as data: RADMC-3D Monte Carlo radiative transfer models of a disk plus Ulrich envelope with outflow cavity, fit to visibilities and SED  
  > "we use Monte Carlo radiative transfer modeling to create synthetic models of the protostellar systems that match the visibilities from the VLA and/or ALMA and the SED of HOPS 383." (Continuum Modeling)

## Processing

### Calibration

- pipeline or manual: manual reduction by the Dutch Allegro ARC Node  
  > "the data were reduced manually by the Dutch Allegro ARC Node." (ALMA)
- casa version: CASA 4.7.2  
  > "All further processing was done using *CASA* version 4.7.2" (ALMA)
- pipeline version: _not stated_
- archive products used as is: No; data reduced manually to account for variation of the flux calibrator quasar J0510+1800  
  > "To account for the variation of the quasar J0510+1800 used for flux calibration, the data were reduced manually by the Dutch Allegro ARC Node." (ALMA)
- flux calibrator: J0510+1800, J0541–0541 and J0750+1231 for the respective observations (bandpass J0510+1800 / J0522–3627; gain J0541–0541)  
  > "J0510+1800, J0541–0541, and J0750+1231 were used as the absolute flux calibrators for the respective observations and J0541–0541 was used as the complex gain calibrator for all the observations." (ALMA)
- flux scale uncertainty: about 10%  
  > "The estimated uncertainty of the absolute flux calibration is expected to be about 10%." (ALMA)
- self calibration: self-calibration on the continuum, solutions also applied to line data  
  > "The signal-to-noise ratio of the continuum images was improved by performing self-calibration on the continuum and also applying these solutions to the spectral line data." (ALMA)

### Imaging

- task: CASA clean (continuum and lines); uvcontsub for line data  
  > "The data were imaged using the task *clean* with a velocity resolution of 1 km s$^{-1}$ for $^{12}$CO, and 0.5 km s$^{-1}$ for $^{13}$CO." (ALMA)
- deconvolver: _not stated_
- weighting robust: Briggs, robust = 0.5  
  > "The final continuum image was produced using Briggs weighting with a robust parameter of 0.5, providing a balance between sensitivity and resolution." (ALMA)
- uv taper: _not stated_
- cell size: _not stated_
- image size: _not stated_
- masking: _not stated_
- multiscale scales: _not stated_
- continuum subtraction: uvcontsub, fitting the continuum to line-free channels in each spectral window  
  > "The spectral line data were continuum subtracted using the task *uvcontsub*, fitting the continuum to the line free channels in each spectral window." (ALMA)
- line free channels: _not stated_
- primary beam correction: _not stated_
- array combination: _not stated_
- smoothing: _not stated_
- final beam: 0.11'' x 0.10''  
  > "This resulted in a synthesized beam of 0.11$''$ $\times$ 0.10$''$ and RMS noise of 0.28 mJy beam$^{-1}$." (ALMA)
- final rms: 0.28 mJy/beam  
  > "This resulted in a synthesized beam of 0.11$''$ $\times$ 0.10$''$ and RMS noise of 0.28 mJy beam$^{-1}$." (ALMA)

### Inherited from earlier work

- ALMA 0.87 mm data are from the VANDAM survey  
  > "as part of the VLA/ALMA Nascent Disk and Multiplicity (VANDAM) Survey" (ALMA) [from (cite: Tobin20)]
- Disk radius of ~62 au was originally reported by Tobin et al. from a single-component Gaussian fit  
  > "using the 2$\sigma$ of the Gaussian distribution radius derived from a single component Gaussian fit." (Continuum) [from (cite: Tobin20)]
- Radiative transfer modeling procedure  
  > "We followed the modeling procedure of (cite: Sheehan14) and (cite: Sheehan17)." (Continuum Modeling) [from (cite: Sheehan14) and (cite: Sheehan17)]
- Envelope density profile of a rotating collapsing envelope  
  > "We model the envelope using the solution for the density profile of a rotating collapsing envelope found by (cite: Ulrich76)" (Envelope) [from (cite: Ulrich76)]
- Dust opacities for the disk models  
  > "Our disk models use the dust opacities from (cite: Woitke16)." (Dust) [from (cite: Woitke16)]
- Formula for dynamical timescale of outflow knots  
  > "the formula $\tau_{dyn} = D/V_{flow} (cos~i/sin~i)$ ((cite: Plunkett15))" (Knotty structures in the 12CO outflow) [from ((cite: Plunkett15))]
- Simplified Toomre Q expression  
  > "We can rewrite this equation ((cite: Kratter16); (cite: Tobin16)) in the form," (Flux Density Derived Toomre Q) [from ((cite: Kratter16); (cite: Tobin16))]

### Not stated but needed to reproduce (our reading)

- Which of the ALMA execution blocks (2016 vs 2017) enter the continuum image and how they were combined
- Self-calibration details: reference antenna, solution intervals, number of rounds, final cell/image size, clean threshold, mask and niter
- How the 0.87 mm Gaussian source size was fit (task, region, uv or image plane)
- Line-free channel selection for uvcontsub and the 12CO channel/clean parameters
- Source and values of the SED photometry fitted together with the visibilities, and how the uncertainties were set
- Priors/bounds for each free parameter, number of walkers, steps and burn-in, and how visibilities were binned and weighted in the chi^2
- Version of pdspy/RADMC-3D/emcee used for the models
- Distance adopted in the radiative transfer models and the exact distance source
- Opacity at 870 microns and 9 mm used for the analytic masses is only given through the scaling law and beta; ISM temperature choice for pre-burst Q (0.2 vs 0.5 Lsun) is inconsistently stated

## Analysis recipe

1. **Calibrate and image the ALMA 0.87 mm continuum**: Manual calibration by the ARC node, CASA 4.7.2 self-calibration and Briggs weighted imaging  
  > "To account for the variation of the quasar J0510+1800 used for flux calibration, the data were reduced manually by the Dutch Allegro ARC Node." (ALMA); "The signal-to-noise ratio of the continuum images was improved by performing self-calibration on the continuum and also applying these solutions to the spectral line data." (ALMA)
   - software: CASA
   - parameter: Briggs robust = 0.5  
  > "The final continuum image was produced using Briggs weighting with a robust parameter of 0.5, providing a balance between sensitivity and resolution." (ALMA)
   - fitting: _not stated_
   - validation: _not stated_
2. **Measure continuum flux, disk size, position angle and inclination**: Single-component Gaussian fit to the ALMA 870 micron continuum; inclination from arccos of the deconvolved minor/major axis ratio  
  > "The disk radius is estimated to be $\sim$62 au from Gaussian fitting of the ALMA 870 $\mu$m continuum enables." (Continuum); "The deconvolved size also enables us to estimate the inclination of HOPS-383 to be $\sim$48$^\circ$ calculated from arccos($\theta_{min}$/$\theta_{maj}$)." (Continuum)
   - parameter: Deconvolved FWHM 0.18'' x 0.12'', PA 49.7 deg; FWHM = 2.355 sigma  
  > "The deconvolved FWHM source size is 0.18$''$$\times$0.12$''$ and a position angle of 49.7$^\circ$; FWHM $\approx$ 2.355$\sigma$." (Continuum)
   - fitting: Gaussian fit; radius taken as 2 sigma of the Gaussian  
  > "using the 2$\sigma$ of the Gaussian distribution radius derived from a single component Gaussian fit." (Continuum)
   - validation: Model inclination from the radiative transfer fits agrees with this estimate  
  > "The model inclinations are also in good agreement with the estimate made from the deconvolved source size in Section" (HOPS 383 ALMA Model)
3. **Fit the mm-to-cm spectrum to separate dust and free-free emission**: Power-law fit of the free-free emission to the long-wavelength points, subtraction from the 8 mm-1 cm data, then a dust power-law fit from 0.87 mm to 1 cm  
  > "We use the *curve_fit* function from Python’s *scipy* library to fit the free-free emission power law to the longer wavelength data" (Millimeter to Centimeter Spectrum); "We then fit another power law for the dust emission from 0.87 mm to 1 cm." (Millimeter to Centimeter Spectrum)
   - software: scipy curve_fit
   - fitting: scipy curve_fit power laws; priors/weights not stated  
  > "We use the *curve_fit* function from Python’s *scipy* library to fit the free-free emission power law to the longer wavelength data" (Millimeter to Centimeter Spectrum)
   - validation: _not stated_
4. **Estimate disk mass analytically from the ALMA and VLA flux densities**: Optically thin isothermal dust emission mass formula with opacity scaled from 1.3 mm by a power law, times a gas-to-dust ratio of 100  
  > "Assuming isothermal dust emission, well-mixed gas and dust, and optically thin emission, the disk mass is given by," (Disk Mass); "Assuming canonical ISM dust to gas mass ratio of 1:100 ((cite: Bohlin78)), we multiply the resulting dust mass by 100 to get the total disk mass." (Disk Mass)
   - parameter: beta ~ 1.78 for ALMA (870 micron)  
  > "Assuming $\beta\sim1.78$, which is appropriate of young, embedded cores, we obtain disk mass of 0.082 M$_{\odot}$ and 0.043 M$_{\odot}$ for T$_{\text{dust}}$ = 30 K and T$_{\text{dust}}$ = 50 K, respectively." (Disk Mass)
   - parameter: beta ~ 1 for VLA (9 mm)  
  > "Assuming $\beta\sim1$ here, which yields more consistent results between 1.3 mm and 1 cm" (Disk Mass)
   - assumption: Dust temperature 30 K for typical low-luminosity protostar, scaled by (L/Lsun)^0.25 to ~50 K for L_bol = 7.8 Lsun  
  > "This gives us an average temperature of $\sim$50 K for L$_{bol}$ = 7.8 L$_{\odot}$, which we use as a high temperature estimate for HOPS 383." (Disk Mass)
   - assumption: Distance ~400 pc  
  > "where D is the distance to the HOPS 383 ($\sim$400 pc)" (Disk Mass)
   - assumption: Opacity kappa(1.3 mm) = 0.899 cm2/g (Ossenkopf & Henning thin ice mantles), scaled as (1.3 mm / lambda)^beta  
  > "We take $\kappa_{1.3 \text{ mm}} = 0.899$ cm$^2$g$^{-1}$ for thin ice mantles from dust opacity models of (cite: Ossenkopf94)" (Disk Mass)
   - fitting: _not stated_
   - validation: Compared with the mean Class 0 disk mass of Tobin et al. 2020; masses are stated to be lower limits if emission is optically thick  
  > "HOPS 383 appears to be more massive than the mean Class 0 disk based on ALMA derived flux density." (Disk Mass)
5. **Compute Toomre Q from the flux-derived disk masses**: Q approx 2 M* H / (Md R) with a 0.5 Msun protostar, scaled by sqrt(T) for the pre-outburst temperature  
  > "Using a typical protostar mass of 0.5 M$_{\odot}$ ((cite: Kenyon95)), we find that $Q = 1.67$ and 0.87 for M$_{\text{disk}} = 0.043 M_{\odot}$ and 0.082 $M_{\odot}$" (Flux Density Derived Toomre Q); "Q would be lower and closer to instability by a factor of $(50/30)^{0.5}$, as $Q$ scales by $\sqrt{T}$." (Flux Density Derived Toomre Q)
   - parameter: Protostar mass 0.5 Msun  
  > "Using a typical protostar mass of 0.5 M$_{\odot}$ ((cite: Kenyon95))" (Flux Density Derived Toomre Q)
   - assumption: Disk radius R at which c_s is measured; the radius value adopted is not stated  
  > "$R$ is the radius of the disk at which the $c_s$ is measured." (Flux Density Derived Toomre Q)
   - fitting: _not stated_
   - validation: _not stated_
6. **Fit radiative transfer disk+envelope models to ALMA and ALMA+VLA visibilities and the SED**: RADMC-3D models (disk, Ulrich envelope with outflow cavity, protostar) with MCMC fitting using emcee, for truncated and exponentially tapered disks; Fourier transform of synthetic images to visibilities  
  > "We use RADMC-3D ((cite: Dullemond12)) for the continuum modeling and to calculate the temperature throughout the density structure of the disk and envelope." (Radiative Transfer Code); "Synthetic visibilities are then created by Fourier-transforming the synthetic millimeter images." (Radiative Transfer Code)
   - software: RADMC-3D, emcee, pdspy
   - parameter: chi^2 weights w_vis = 0.5, w_SED = 1  
  > "Our fits use $w_{\text{vis}} = 0.5$ and $w_{\text{SED}} = 1$ for both the ALMA only and the ALMA+VLA models, which we empirically determined to fit both data sets simultaneously." (Radiative Transfer Code)
   - parameter: Protostar temperature 4000 K; luminosity L* free  
  > "Our models include a central protostar with a temperature of 4000 K, representative of a general low mass star in the pre-main sequence phase." (Protostar)
   - parameter: Dust: 60% silicate, 15% amorphous carbon, 25% porosity; minimum grain size 0.005 micron; envelope max grain 1 micron; disk max grain size and p (2.5-4.5) free  
  > "The dust grain models consist of 60% silicate, 15% amorphous carbon, and 25% porosity." (Dust); "The minimum grain size is assumed to be 0.005 $\mu$m for all opacities." (Dust)
   - parameter: SMA visibilities not fit  
  > "We do not include the visibility data from the SMA due to their lower signal-to-noise." (Model Fitting)
   - assumption: Models constrain dust mass only; total mass quoted with gas-to-dust ratio of 100  
  > "we list the total mass using the canonical gas-to-dust ratio of 100" (Model Results)
   - assumption: Protostar mass used only to set the envelope density structure, not fit  
  > "is the mass of the protostar only used for setting density structure and is not constrained by fitting" (Envelope)
   - fitting: emcee MCMC minimizing weighted chi^2 of visibilities and SED; best fit = median of walkers once steady; 1 sigma (68%) as uncertainty; lost walkers trimmed; priors not stated  
  > "The 1$\sigma$ value around the median containing $\sim$68% of the walkers is considered as the uncertainty on the parameters." (Radiative Transfer Code); "The walkers that are lost, meaning that they are outside the primary distribution of walkers, are “trimmed" and not considered when determining parameter uncertainties." (Radiative Transfer Code)
   - validation: Visual comparison of models with visibilities and SED; convergence judged by stable best-fit values over ~150-200 steps; ALMA+VLA models fit short baselines and far-IR/submm SED worse and do not include free-free  
  > "the best fit values of the parameters remain more or less constant for $\sim$ 150 - 200 steps." (Radiative Transfer Code); "The models do not fit short baselines as well as the ALMA only models and the fit to the far-IR and submillimiter SED is less optimal than the ALMA only models." (HOPS 383 ALMA+VLA Model)
7. **Compute Toomre Q versus radius and pre-outburst Q from the model profiles**: Use model surface density and temperature (averaged over a few slices above midplane) in Q = c_s Omega / (pi G Sigma); pre-outburst temperature scaled by (L_pre/L_burst)^(1/4)  
  > "Extracting these, we can use Equation [\[eq:Q\]](#eq:Q) to plot Toomre’s $Q$ as a function of radius." (Toomre Q vs. Radius); "we scale the disk temperature by $\sqrt[4]{L_{*, pre}/L_{*, burst}}$" (Toomre Q vs. Radius)
   - software: RADMC-3D
   - parameter: L*,pre = 0.5 Lsun; model-derived L*,burst; protostar masses 0.1 to 0.5 Msun  
  > "We use the model derived luminosities for L$_{*, burst}$ and take L$_{*, pre}$ = 0.5 L$_{\odot}$" (Toomre Q vs. Radius); "Therefore we plot the $Q$ with different protostar masses of 0.1 M$_{\odot}$ to 0.5 M$_{\odot}$." (Toomre Q vs. Radius)
   - assumption: Keplerian disk; dust-to-gas 1:100  
  > "We assume the disk around HOPS 383 to be Keplerian since there is no evidence pointing otherwise." (Toomre Q vs. Radius); "We assume a dust-to-gas mass ratio of 1:100 for our calculation." (Toomre Q vs. Radius)
   - fitting: _not stated_
   - validation: _not stated_
8. **Estimate outflow knot dynamical timescales**: tau_dyn = D / V_flow (cos i / sin i) using the knot offset and line-of-sight velocity from the ALMA cube  
  > "We can roughly calculate the dynamic timescale of the closest knot using the spectral cube from ALMA and the formula $\tau_{dyn} = D/V_{flow} (cos~i/sin~i)$" (Knotty structures in the 12CO outflow)
   - parameter: closest knot 1.35'' from the protostar; V_flow ~ 10 km/s  
  > "The knot closest to the protostar is about 1.35$''$ away." (Knotty structures in the 12CO outflow); "We get $\tau_{dyn} \approx$ 215 yr, with $V_{flow} \approx 10$ km/s" (Knotty structures in the 12CO outflow)
   - assumption: Knots travel at constant speed after ejection  
  > "Assuming the knots travel at a constant speed after being ejected, they are traveling at a speed of $\sim$1 arcsec every 160 yr." (Knotty structures in the 12CO outflow)
   - fitting: _not stated_
   - validation: Knot spacing compared with the burst rate inferred by Fischer et al. 2019  
  > "This aligns well with the rate of bursts inferred by (cite: Fischer19)." (Knotty structures in the 12CO outflow)

## Software

- **CASA** 4.7.2 (ALMA); 4.4.0 pipeline and 4.5.1 clean (VLA): ALMA processing (uvcontsub, clean, self-calibration) and VLA pipeline/imaging  
  > "All further processing was done using *CASA* version 4.7.2" (ALMA); "The data were reduced using the scripted version of the VLA pipeline in *CASA* 4.4.0." (VLA)
- **MIR** : Calibration and editing of the SMA data  
  > "Calibration and editing of the SMA data were performed using the IDL based MIR software package." (Data Reduction)
- **MIRIAD** : Imaging of SMA continuum and line data  
  > "The imaging of both the continuum and the spectral line data were performed using the MIRIAD" (Data Reduction)
- **scipy curve_fit** : Power-law fits to the mm-cm spectrum  
  > "We use the *curve_fit* function from Python’s *scipy* library to fit the free-free emission power law to the longer wavelength data" (Millimeter to Centimeter Spectrum)
- **RADMC-3D** : Dust temperature, synthetic SEDs and images for continuum modeling  
  > "We use RADMC-3D ((cite: Dullemond12)) for the continuum modeling and to calculate the temperature throughout the density structure of the disk and envelope." (Radiative Transfer Code)
- **emcee** : MCMC fitting of model parameters  
  > "using Markov Chain Monte Carlo (MCMC) fitting with the *emcee* code ((cite: Foreman13))" (Radiative Transfer Code)
- **pdspy** : Listed in the Software section as the modeling tool (Sheehan 2018)  
  > "pdspy ((cite: Sheehan18)), CASA ((cite: McMullin07)), RADMC-3D ((cite: Dullemond12)), emcee ((cite: Foreman13))" (Software)
- **matplotlib** : Listed in the Software section (plotting)  
  > "matplotlib ((cite: Hunter07))" (Software)

## Numeric results

| quantity | value | uncertainty | units | step | quote |
|---|---|---|---|---|---|
| ALMA 870 micron integrated flux density | 157.8 | 3.2 | mJy | 2 | The integrated flux density of HOPS 383 at 870 $\mu$m is 157.8 $\pm$ 3.2 mJy with peak intensity value of 47 $\pm$ 0.7 mJy/beam. |
| VLA 8 mm integrated flux density | 411 | 17 | microJy | 0 | the integrated flux density for the 8 mm wavelength data from the VLA is 411 $\pm$ 17 $\mu$Jy with peak intensity value of 290 $\pm$ 7 $\mu$Jy/beam. |
| Disk radius from Gaussian fit to ALMA 870 micron | ~62 | not stated | au | 2 | The disk radius is estimated to be $\sim$62 au from Gaussian fitting of the ALMA 870 $\mu$m continuum enables. |
| Deconvolved FWHM source size and position angle | 0.18'' x 0.12'', PA 49.7 deg | not stated | arcsec; deg | 2 | The deconvolved FWHM source size is 0.18$''$$\times$0.12$''$ and a position angle of 49.7$^\circ$; FWHM $\approx$ 2.355$\sigma$. |
| Inclination from deconvolved size | ~48 | not stated | deg | 2 | The deconvolved size also enables us to estimate the inclination of HOPS-383 to be $\sim$48$^\circ$ calculated from arccos($\theta_{min}$/$\theta_{maj}$). |
| SMA Subcompact integrated flux densities at 0.85, 1.1, 1.3 mm | 323.46, 147.74, 136.63 | 12.7, 12.2, 6.7 | mJy | 0 | In the Subcompact configuration, we obtained integrated flux density of 323.46 $\pm$ 12.7 mJy, 147.74 $\pm$ 12.2 mJy, and 136.63 $\pm$ 6.7 mJy at 0.85 mm, 1.1 mm, and 1.3 mm, respectively. |
| Free-free contribution at 8 mm, 9 mm, 1 cm | ~0.232, ~0.234, ~0.237 | not stated | mJy | 3 | The free-free contribution to the 8 mm, 9 mm, and 1 cm data is found to be $\sim$0.232 mJy, $\sim$0.234 mJy, and $\sim$0.237 mJy, respectively. |
| Dust power-law spectrum F_lambda,dust | (0.17 +/- 0.08) lambda^(-2.85 +/- 0.05) | 0.05 on exponent | mJy (lambda in mm) | 3 | From the spectrum, we get the power law as $\text{F}_{\lambda, \text{dust}} = (0.17 \pm 0.08)\lambda^{-2.85 \pm 0.05}$ mJy |
| Analytic disk mass from ALMA flux (T=30 K, 50 K; beta~1.78) | 0.082 and 0.043 | not stated | Msun | 4 | we obtain disk mass of 0.082 M$_{\odot}$ and 0.043 M$_{\odot}$ for T$_{\text{dust}}$ = 30 K and T$_{\text{dust}}$ = 50 K, respectively. |
| Analytic disk mass from VLA 9 mm flux (T=30 K, 50 K; beta~1) | 0.25 and 0.15 | not stated | Msun | 4 | we obtain total disk mass of 0.25 M$_{\odot}$ and 0.15 M$_{\odot}$ for T$_{\text{dust}}$ = 30 K and T$_{\text{dust}}$ = 50 K, respectively. |
| VLA disk mass after free-free subtraction (T=30 K, 50 K) | 0.11 and 0.063 | not stated | Msun | 4 | we get total disk mass of 0.11 M$_{\odot}$ and 0.063 M$_{\odot}$ for T$_{\text{dust}}$ = 30 K and T$_{\text{dust}}$ = 50 K, respectively. |
| Toomre Q from flux-derived masses (0.5 Msun protostar), for Md = 0.043 and 0.082 Msun | 1.67 and 0.87 | not stated | dimensionless | 5 | we find that $Q = 1.67$ and 0.87 for M$_{\text{disk}} = 0.043 M_{\odot}$ and 0.082 $M_{\odot}$, respectively for the disk masses obtained from the ALMA flux density. |
| ALMA-only model disk mass, inclination and position angle | ~0.02 Msun; i ~ 51 deg; PA ~ 49 deg | see Table 2 (e.g. 0.026 +0.004/-0.003 truncated) | Msun; deg | 6 | Both models have a protostellar disk mass of $\approx$0.02 $M_{\odot}$ and independently find the same inclination ($i \approx 51^{\circ}$) and position angle ($P.A. \approx 49^{\circ}$). |
| ALMA-only model envelope masses and radii (truncated, tapered) | 0.38 and 1.1 Msun; 5700 and 12000 au | not well constrained | Msun; au | 6 | Although the envelope masses (0.38 $M_{\odot}$ and 1.1 $M_{\odot}$) and radii (5700 au and 12000 au) differ between the truncated and tapered model |
| ALMA-only model luminosity | ~5 | not stated | Lsun | 6 | The luminosities of both models are very similar with $L \sim 5$ $L_{\odot}$. |
| ALMA+VLA model disk masses (truncated, tapered) | ~0.33 and ~0.21 | see Table 2 (0.330 +0.025/-0.028; 0.214 +0.011/-0.019) | Msun | 6 | The ALMA+VLA model results find massive disks of $M \sim 0.33 M_{\odot}$ and $M \sim 0.21 M_{\odot}$ for the truncated and the tapered cases, respectively. |
| ALMA+VLA model envelope masses (truncated, tapered) | 0.32 and 0.09 | not stated | Msun | 6 | The truncated disk model has a very similar envelope mass compared to the ALMA only models with $M_{env}$ = 0.32 $M_{\odot}$.; the tapered disk model has very low envelope mass of 0.09 $M_{\odot}$ |
| Radius of the 25 K temperature limit now (ALMA only, ALMA+VLA models) | ~550 au; ~250-400 au | not stated | au | 6 | the ALMA only and the ALMA+VLA models have 25 K temperature limit at $\sim$550 au radius and $\sim$250 - 400 au radius, respectively. |
| Radius of the 25 K temperature limit before the outburst | 50-100 | not stated | au | 6 | Before the outburst, the models have the 25 K temperature limit at a radius around 50 - 100 au |
| Dynamical timescale of the closest outflow knot | ~215 | not stated | yr | 8 | We get $\tau_{dyn} \approx$ 215 yr, with $V_{flow} \approx 10$ km/s |
| Spacing between outflow knots | ~1400 | not stated | yr | 8 | which translates to roughly 1400 yr between the knots. |
| Outflow position angle from SMA 12CO | ~137.5 | not stated | deg | 0 | we determine the position angle (PA) to be about 137.5$^{\circ}$. |
| Free-free to total 9 mm flux ratio and rescaled ALMA+VLA disk masses (truncated, tapered) | 0.57; ~0.14 and ~0.092 | not stated | dimensionless; Msun | 6 | the ratio of free-free emission to total flux density is 234 $\mu$Jy/411 $\mu$Jy $\approx 0.57$.; this gives us disk masses of $\sim$0.14 M$_{\odot}$ and $\sim$0.092 M$_{\odot}$ for the truncated and the tapered ALMA+VLA models, respectively. |

## Qualitative findings

- HCO+ and H13CO+ peak on or near the continuum while N2H+ is reduced there, consistent with CO evaporation after the outburst  
  > "The images show that HCO$^+$ and H$^{13}$CO$^+$ peaks on or near the continuum, while N$_2$H$^+$ is reduced at the same position." (abstract)
- A resolved disk lies orthogonal to the outflow  
  > "A disk is resolved in the ALMA 0.87 mm dust continuum, orthogonal to the outflow direction, with an apparent radius of $\sim$62 AU." (abstract)
- The closest outflow knot is too old to be tied to the 2006 burst; knots may record earlier bursts  
  > "Thus, the most recent clump in the outflow was ejected too long ago to be associated with the most recent accretion burst." (Knotty structures in the 12CO outflow)

## Claim tuples

- H: The outburst of HOPS 383 has left a chemical signature in the envelope (CO evaporation destroying N2H+ and forming HCO+) | E: SMA Subcompact+Extended moment-0 maps of N2H+, HCO+, H13CO+ and N2D+ compared with models temperature profiles | R: HCO+ peaks near the protostar where N2H+ is reduced and N2H+ is marginally double-peaked; model 25 K radius ~250-550 au now vs 50-100 au pre-burst | F: The N2H+ depression is consistent with CO evaporation after the outburst, though of marginal significance | **partially**
- H: A protostellar disk is resolved around HOPS 383 | E: ALMA 0.87 mm continuum imaging and Gaussian fitting | R: Resolved emission elongated perpendicular to the outflow with radius ~62 au and inclination ~48 deg | F: The continuum traces a resolved protostellar disk | **supported**
- H: The disk mass of HOPS 383 from radiative transfer modeling of ALMA and ALMA+VLA data | E: RADMC-3D + emcee fits of truncated and tapered disk models to ALMA only and ALMA+VLA visibilities plus SED | R: ALMA-only disk mass ~0.02 Msun; ALMA+VLA ~0.33 and ~0.21 Msun, i.e. up to ~10x larger | F: The disk mass could be up to a factor of 10 larger when 8 mm data are included, due to lower dust opacity at long wavelengths, though free-free contamination in the VLA data is not modeled | **partially**
- H: Gravitational instability is a viable mechanism for the HOPS 383 outburst | E: Toomre Q from flux-derived masses and from model surface density and temperature profiles, with temperatures scaled back to the pre-outburst luminosity | R: Q = 1.67 (0.043 Msun) and 0.87 (0.082 Msun) at 0.5 Msun; ALMA-only model disks stable but near Q=1, ALMA+VLA models unstable near the critical radius | F: Disk appears to have sufficient mass for GI to be a very plausible outburst mechanism, but instability is not confirmed | **partially**
- H: Outflow knots record past accretion bursts | E: Dynamical timescale of knots from the ALMA 12CO cube and spacing of knots in the SMA maps | R: Closest knot ~215 yr old; knots spaced ~1400 yr apart | F: The closest knot predates the 2006 burst; knot spacing is consistent with the Orion burst rate of Fischer et al. 2019, if knots and bursts are one-to-one | **partially**

## Reasoning

- Why this data: ALMA masses are emphasised because the appropriate 9 mm dust opacity for the VLA data is uncertain  
  > "We focus on the ALMA masses because the appropriate dust opacity at 9 mm for the VLA observations is uncertain." (Flux Density Derived Toomre Q)
- Why this method: Both truncated and exponentially tapered disks are modeled because it is unclear which better reflects the disk structure  
  > "We model two different types of disks as it is unclear which type of disk better reflects the underlying protostellar disk structure." (Protostellar Disk)
- Alternative: Tapered models give less reliable disk radii than truncated models, so the truncated radii are favored  
  > "For this reason, we favor the truncated models values of disk radius." (Discussion of Best-fit Model Parameters)
- Alternative: N2H+ structure may reflect cumulative effects of multiple bursts rather than only the latest one  
  > "the observed structure of N$_2$H$^+$ could be a chemical feature that may represent the cumulative effect of multiple outbursts, rather than the latest one." (HCO+ and N2H+)
- How they decided it was enough: Fits stopped when best-fit values stay constant for ~150-200 steps  
  > "the best fit values of the parameters remain more or less constant for $\sim$ 150 - 200 steps." (Radiative Transfer Code)
- Limitation (authors): Analytic ALMA disk masses are lower limits if the 0.87 mm emission is optically thick  
  > "The dust emission may not be optically thin at 0.87 mm for all radii, thus, the disk masses are likely lower limits for their respective temperatures." (Disk Mass)
- Limitation (authors): VLA visibility fits omit the free-free contribution; models cannot fit VLA visibilities without worsening the SED fit  
  > "Our models are not able to fully reproduce the visibilities from the VLA, without sacrificing the fit for the SED." (HOPS 383 ALMA+VLA Model); "The fitting to the visibility data from the VLA also does not account for a contribution from the free-free emission" (HOPS 383 ALMA+VLA Model)
- Limitation (authors): Envelope properties are poorly constrained for lack of short baselines  
  > "While we model the envelopes, their properties are expected to be poorly constrained due to the lack of short baseline data." (Model Results)
- Limitation (authors): SMA C18O is contaminated by a foreground cloud  
  > "our C$^{18}$O data cube is contaminated by a foreground cloud that is also emitting at a similar velocity range" (Line Results)
- Caveat (inferred, ours): The ALMA-based results rest on a single 54 s observation; self-calibration and imaging parameters (clean mask, threshold, cell, image size) are not given
- Caveat (inferred, ours): Disk mass depends on assumed opacity, beta, temperature and the 100:1 gas-to-dust ratio; 0.082 vs 0.043 Msun spans a factor of two
- Caveat (inferred, ours): The Toomre Q inference uses an assumed 0.5 Msun protostar mass and an unstated radius; pre-outburst luminosity is 0.2 Lsun in some places and 0.5 Lsun in others
- Caveat (inferred, ours): Internal inconsistencies: VLA 9 mm flux given as 411 +/- 17 uJy (Results) and 411 +/- 1.7 uJy (Disk Mass); conclusions quote model disk mass 0.1 Msun/radius ~67 au and 0.065 Msun/~40 au versus Table 2 values of 0.026/0.020 Msun and 65/38 au
- Caveat (inferred, ours): N2H+ double-peaked structure is of marginal significance (5-7 sigma peak S/N) and chemistry conclusions come from SMA data, not ALMA
- Caveat (inferred, ours): Free-free is not modeled in the ALMA+VLA visibility fits, so the factor-of-10 mass increase is partly spurious by the authors' own estimate

## Reproducibility

- Data public (paper): _not stated_
- Products in archive: _not stated_
- Missing: Self-calibration and clean settings for the ALMA continuum
- Missing: SED photometry table used in the model fits
- Missing: MCMC priors, walker/step counts, visibility binning and pdspy version
- Missing: Coordinates and exact distance adoption for HOPS 383
- Missing: Reduced ALMA visibilities (manually calibrated by the ARC node) are not stated to be released
- Data volume (inferred): Small: one ALMA Band 7 project (2015.1.00041.S), two short execution blocks, a few GB to tens of GB of raw data
- Score (inferred): 3/5, ALMA project code, CASA version, robust, flux calibrators and key analytic formulae with numeric results are given, so the continuum flux, size and analytic disk mass are reproducible; the radiative transfer modeling lacks priors, SED data and self-calibration detail, and the calibration was done manually.
- Rediscovery candidate: yes, The ALMA project code is printed and the data come from the VANDAM survey; the continuum flux, Gaussian size, inclination and analytic disk masses are numeric and redoable, though the full RT model fit is not completely specified.

## Links

- Method: (cite: Sheehan14) and (cite: Sheehan17) (Radiative transfer modeling procedure followed for the MCMC disk+envelope fits)
- Method: (cite: Tobin20) (VANDAM survey describing the ALMA observations and original disk radius)
- Companion: (cite: Tobin20) (VANDAM survey paper from which the ALMA data and mean Class 0 disk mass comparison come)
- Companion: (cite: Safron15) (Discovery of the HOPS 383 outburst and earlier SED model)
- Related: VANDAM (VLA/ALMA Nascent Disk and Multiplicity Survey)
- Related: Herschel Orion Protostar Survey

## Checks

```json
{
 "quotes": 151,
 "quotes_ok": 151,
 "quote_pass_rate": 1.0,
 "quotes_too_long": 0,
 "unsupported_facts": 0,
 "project_codes": 1,
 "codes_not_in_text": [],
 "codes_not_in_obscore": [],
 "obscore_codes_not_in_card": [],
 "codes_printed_but_missing": [],
 "numeric_results": 23,
 "numeric_problems": 0,
 "fill": {
  "facts": 120,
  "stated": 93,
  "rate": 0.775
 },
 "evidence_ok": true
}
```
