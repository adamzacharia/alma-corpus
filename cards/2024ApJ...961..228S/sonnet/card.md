# Ring Gap Structure around Class I Protostar WL 17

`2024ApJ...961..228S` | The Astrophysical Journal 2024 | first author: Shoshi, Ayumu | arXiv: 2312.02504 | DOI: 10.3847/1538-4357/ad12b5

Card schema 1.0 | model claude-sonnet-5-5 | depth full | type archival_reuse

## Science

- Fields: star_formation, protoplanetary_disks
- Question: Does the Class I protostar WL 17 have a ring-hole or a ring-gap structure, is an outflow associated with it, and what do these imply for ring formation timescale and planet formation?  
  > "WL 17 is a Class I object and was considered to have a ring–hole structure. We analyzed the structure around WL 17 to investigate the detailed properties of WL 17." (abstract)
- Target **WL 17**: coordinates _not stated_; z/distance 137 pc  
  > "Our target WL 17 is a protostar in the $\rho$ Ophiuchus L1688 molecular cloud located 137 pc from the Sun" (Introduction); distance from Ortiz-Leon_2017; Ortiz-Leon_2018  
  > "Our target WL 17 is a protostar in the $\rho$ Ophiuchus L1688 molecular cloud located 137 pc from the Sun" (Introduction)

## Data provenance

- ALMA projects: 2019.1.00458.S, 2019.1.01792.S
- bands: Band 6 (1.3 mm)  
  > "There were two continuum spectral windows with central frequencies of 218 GHz and 232 GHz in Band 6." (2.1 High-resolution Continuum Observations)
- frequencies and spectral setup: Line data: 12CO at 230 GHz and C18O at 219 GHz, each spw 11.7 MHz wide; continuum spw 232 GHz  
  > "The $^{12}$CO and C$^{18}$O line spectral windows had central frequencies of 230 and 219 GHz, respectively. The bandwidth of both windows was 11.7 MHz." (2.2 Molecular Line Observations)
- continuum bandwidth: 1.875 GHz per continuum spw  
  > "Both had a bandwidth of 1.875 GHz." (2.1 High-resolution Continuum Observations)
- arrays: ALMA main array  
  > "using the ALMA main array in its C43-9/10 configuration" (2.1 High-resolution Continuum Observations)
- configurations: C43-9/10 (continuum); C-7 (lines)  
  > "using the ALMA main array in its C-7 configuration" (2.2 Molecular Line Observations)
- baselines: _not stated_
- angular resolution: 0.037'' x 0.031'' (5.1 x 4.2 au), PA -65.9 deg (continuum); 1.21'' x 0.93'' (lines)  
  > "The resultant synthesized beam size was $0.037\ensuremath{''} \times 0.031\ensuremath{''}$ ($5.1 \times 4.2$ au)" (2.1 High-resolution Continuum Observations)
- max recoverable scale: _not stated_
- sensitivity: 18 uJy/beam continuum (high-res); 0.33 mJy/beam continuum and 0.35 K per 0.1 km/s for CO lines (low-res)  
  > "We achieved a sensitivity of 0.33 mJy beam$\mathbf{^{-1}}$ for the continuum and 0.35 K per 0.1 km s$^{-1}$ for the CO lines." (2.2 Molecular Line Observations)
- time on source: _not stated_
- observing dates: 2019 September 29 (continuum); 2019 November 21 (lines)  
  > "The observations were carried out on 2019 September 29" (2.1 High-resolution Continuum Observations)
- pi or archival as stated: Archival; PIs Patrick Sheehan and Diego Mardones  
  > "We used ALMA archival data (Project 2019.1.00458.S, PI Patrick Sheehan)" (2.1 High-resolution Continuum Observations)
- Line: 12CO J=2-1 (not stated)
- Line: C18O J=2-1 (not stated)
- Other facility **Herschel Gould Belt Survey**: H2 column density map (18'' resolution) used to estimate envelope mass  
  > "Figure [9](#fig:herschel) shows the column density map derived from the Herschel Gould Belt Survey data (cite: Andre_2010) with a resolution of 18$"$ (cite: Ladjelate_2020)." (4.1 Remaining Mass of Core and Envelope around WL 17)
- External data: ALMA Band 3 ring-hole results (hole radius ~10-13 au, outer ring ~20 au, 0.06''x0.05'' beam, 36 uJy/beam)  
  > "They found that WL 17 has a ring–hole structure based on high angular resolution ALMA Band 3 observations, where the radius of the hole is $\sim10$ au and the outer radius of the ring is $\sim20$ au." (1 Introduction) [from (cite: Sheehan_2017)]
- External data: Single-dish 12CO(3-2) outflow properties (lengths, masses, velocities, t_dyn, rate) and v_sys = 4 km/s  
  > "We determined the outflow maximum velocity $v_{\rm max}$ with the system velocity $v_{\rm sys}=$ 4 km s$^{-1}$ (cite: van_der_Marel_2013)." (3.3 Outflow Physical Quantities) [from (cite: van_der_Marel_2013)]
- External data: Inner disk radii, fluxes and ring radii of ring-gap protoplanetary disks for comparison  
  > "We compare the properties of the inner disk of the WL 17 system with those of other inner disks of objects associated with the ring–gap structure presented in (cite: Francis_2020)." (3.1 High-spatial Resolution Continuum Image) [from (cite: Francis_2020)]
- External data: Spectral index alpha=2 assumed for converting sensitivity to 3 mm  
  > "Assuming a spectral index $\alpha$=2 (cite: Ilseing_2023)" (3.1 High-spatial Resolution Continuum Image) [from (cite: Ilseing_2023)]
- External data: Herschel column density map of the region  
  > "Figure [9](#fig:herschel) shows the column density map derived from the Herschel Gould Belt Survey data (cite: Andre_2010)" (4.1 Remaining Mass of Core and Envelope around WL 17) [from (cite: Andre_2010; Ladjelate_2020)]

## Processing

### Calibration

- pipeline or manual: _not stated_
- casa version: CASA 6.2.1  
  > "The data were calibrated with the Common Astronomy Software Application (cite: McMullin_2007) version 6.2.1." (2.1 High-resolution Continuum Observations)
- pipeline version: _not stated_
- archive products used as is: _not stated_
- flux calibrator: _not stated_
- flux scale uncertainty: _not stated_
- self calibration: Attempted on continuum; no improvement due to low S/N (<100)  
  > "We performed self-calibrations and could not achieve any improvement because of the low signal-to-noise-ratio ($<$100)." (2.1 High-resolution Continuum Observations)

### Imaging

- task: CASA tclean  
  > "We used only the `tclean` task in our imaging process." (2.1 High-resolution Continuum Observations)
- deconvolver: _not stated_
- weighting robust: Briggs, robust = 0.5 (both datasets)  
  > "We applied Briggs weighting with a robustness parameter of 0.5 and an image grid of 0.0037$''$." (2.1 High-resolution Continuum Observations)
- uv taper: _not stated_
- cell size: 0.0037'' (continuum); 0.140'' (lines)  
  > "an image grid of 0.140$''$, and a velocity resolution of 0.1 km s$^{-1}$" (2.2 Molecular Line Observations)
- image size: _not stated_
- masking: _not stated_
- multiscale scales: _not stated_
- continuum subtraction: CASA imcontsub on image cubes  
  > "the continuum was subtracted from the $^{12}$CO and C$^{18}$O line data using the CASA task `imcontsub`." (2.2 Molecular Line Observations)
- line free channels: _not stated_
- primary beam correction: _not stated_
- array combination: _not stated_
- smoothing: Continuum smoothed to 0.06''x0.05'' to match Sheehan & Eisner 2017; rms ~21 uJy/beam  
  > "We smoothed our 1.3 mm image into a lower-resolution image with a beam size of 0.06$''$$\times$0.05$''$" (3.1 High-spatial Resolution Continuum Image)
- final beam: 0.037'' x 0.031'' PA -65.9 deg (continuum); 1.21'' x 0.93'' PA -85.5 deg (lines)  
  > "The resultant synthesized beam size was $1.21\ensuremath{''} \times 0.93\ensuremath{''}$ ($166 \times 127$ au) with a PA of $-85.5^\circ$." (2.2 Molecular Line Observations)
- final rms: 18 uJy/beam (high-res continuum)  
  > "The sensitivity of the continuum achieved was 18 $\mu$Jy beam$^{-1}$." (2.1 High-resolution Continuum Observations)

### Inherited from earlier work

- Ellipse-fitting method for ring inclination and PA  
  > "using the method adopted in (cite: Yamaguchi_2021)" (3.1 High-spatial Resolution Continuum Image) [from (cite: Yamaguchi_2021)]
- Outflow physical quantities estimated in the same manner as the earlier single-dish study  
  > "We estimated the physical properties of the outflows around WL 17 in the same manner as in (cite: van_der_Marel_2013)." (3.3 Outflow Physical Quantities) [from (cite: van_der_Marel_2013)]
- C18O optical depth and column density formalism; N(C18O)=1.7e-7 N(H2)  
  > "The C$^{18}$O column density $N_{\rm C^{18}O}$ is then converted to the averaged H$_2$ column density $N_{\rm H_2}$ using the relation $N_{\rm C^{18}O}=1.7\times10^{-7}\times N_{\rm H_2}$ (cite: Frerking_1982)." (4.1 Remaining Mass of Core and Envelope around WL 17) [from (cite: Frerking_1982)]
- Dust opacity kappa=2 cm2/g at 1.3 mm  
  > "a dust opacity at 1.3 mm of $\kappa_{\nu}=2$ cm$^2$ g$^{-1}$ (cite: Beckwith_1990)" (3.1 High-spatial Resolution Continuum Image) [from (cite: Beckwith_1990)]
- X_CO = 2.0e20 cm-2 K-1 km-1 s  
  > "A $X_{\rm{CO}}$ factor of $X_{\rm{CO}} = 2.0 \times 10^{20}\,\rm{cm^{-2}\,K^{-1}\,km^{-1}\,s}$ is adopted (cite: Balatto_2013)." (3.3 Outflow Physical Quantities) [from (cite: Balatto_2013)]
- Accretion-to-ejection ratio epsilon = 10  
  > "where $\varepsilon=10$ is adopted (cite: Carbit_2009; Konigl_2000)" (4.2 Disk Growth Timescale) [from (cite: Carbit_2009; Konigl_2000)]

### Not stated but needed to reproduce (our reading)

- Spectral window/channel ranges used for continuum vs line, and line-free channels for imcontsub
- Image size (pixels) and deconvolution settings (deconvolver, threshold, mask, niter)
- Calibrators and flux scale; whether the pipeline or manual scripts were used
- Rest frequencies and the velocity range used to define the blue/red outflow moment maps
- Exact outflow area definition, 0.5 K km/s contour and the outflow lengths and mean column density per lobe
- Primary-beam correction treatment
- Dipole moment, J and partition-function inputs used in C18O column density; how the C18O area was defined
- Uncertainties on fitted ring parameters
- Details of the pixel-peak ellipse fit and Gaussian fits to radial profile

## Analysis recipe

1. **Image continuum and line data**: tclean with Briggs weighting; imcontsub for lines  
  > "we also used the CASA task `tclean` and applied Briggs weighting with a robustness parameter of 0.5" (2.2 Molecular Line Observations)
   - software: CASA
   - parameter: robust 0.5; cell 0.0037'' (cont), 0.140'' (lines); 0.1 km/s channels  
  > "an image grid of 0.140$''$, and a velocity resolution of 0.1 km s$^{-1}$" (2.2 Molecular Line Observations)
   - fitting: _not stated_
   - validation: Self-calibration attempted, no improvement  
  > "We performed self-calibrations and could not achieve any improvement because of the low signal-to-noise-ratio ($<$100)." (2.1 High-resolution Continuum Observations)
2. **Fit ring geometry and radial profile**: Peak radius every 1 deg in polar coordinates fitted with an ellipse; deproject; azimuthally average; Gaussian fits to inner disk and outer ring peaks  
  > "First, we determined the radial peak position of the outer ring every 1$^{\circ}$ in the position angle (or vertical) direction from the intensity map on polar coordinates." (3.1 High-spatial Resolution Continuum Image)
   - fitting: Ellipse fit to ring peaks; Gaussian fit for FWHM without beam deconvolution  
  > "We adopted the Gaussian fitting to the peaks of the inner disk and the outer ring shown in Figure [3](#fig:azintpro) and estimated the full width at half maximum (FWHM) without the beam deconvolution." (3.1 High-spatial Resolution Continuum Image)
   - validation: Comparison with Sheehan & Eisner 2017 after smoothing to the same beam  
  > "which is the same as in (cite: Sheehan_2017)" (3.1 High-spatial Resolution Continuum Image)
3. **Dust and gas mass of ring/disk**: Optically thin M_dust = F d^2 /(kappa B(T)) on flux above 5 sigma  
  > "where the dust is assumed to be optically thin, and a dust opacity at 1.3 mm of $\kappa_{\nu}=2$ cm$^2$ g$^{-1}$ (cite: Beckwith_1990) and a dust temperature of $T_{\rm dust}=20$ K were adopted." (3.1 High-spatial Resolution Continuum Image)
   - parameter: 5 sigma threshold, sigma = 18 uJy/beam  
  > "considering the dust emission larger than 5$\sigma$ ($\sigma$ = 18 $\mu$Jy beam$^{-1}$)" (3.1 High-spatial Resolution Continuum Image)
   - assumption: kappa=2 cm2/g, T_dust=20 K, gas-to-dust 100, d=137 pc  
  > "Adopting a gas-to-dust mass ratio of 100, the outer ring mass of WL 17 is at least $M_{\rm gas,ring}\simeq 0.01 M_{\odot}$" (3.1 High-spatial Resolution Continuum Image)
   - fitting: _not stated_
   - validation: Compared to Sheehan & Eisner 2017 mass and Class I disk masses  
  > "which is comparable or smaller than the dust ring mass estimated in previous studies ($M_{\rm gas,ring}\simeq 0.04\,M_{\odot}$ for (cite: Sheehan_2017))" (3.1 High-spatial Resolution Continuum Image)
4. **Outflow velocity, timescale, mass, mass-loss rate**: PV diagrams give v_max; t_dyn = r_out/v_max tan(i); M_out = mu m_H A N_ave with N = X_CO W_CO; Mdot = M_out/t_dyn  
  > "Next, we estimate the outflow mass $M_{\rm out}$ as $M_{\rm out} = \mu m_{\rm H} AN_{\rm ave}$" (3.3 Outflow Physical Quantities)
   - parameter: Outflow area: intensity > 0.5 K km/s; v_sys = 4 km/s; i_out = i_ring  
  > "the areas surrounded by white lines indicate outflow areas with intensities exceeding 0.5 K km s$^{-1}$" (3.3 Outflow Physical Quantities)
   - assumption: mu = 2.8; X_CO = 2.0e20; protostellar mass 1 Msun for Keplerian; constant mass loss rate  
  > "We used a protostellar mass of $1{M}_\odot$ for calculating the physical quantities for the WL 17 system below." (3.3 Outflow Physical Quantities)
   - fitting: _not stated_
   - validation: Compared with van der Marel et al. 2013 values  
  > "The outflow mass derived in this study is comparable to that in (cite: van_der_Marel_2013)." (3.3 Outflow Physical Quantities)
5. **Envelope mass from C18O and Herschel**: Optical depth from T_B (Tex = 10, 20 K), column density, convert to H2 and mass over area; Herschel mass within 1000, 2000, 3000 au minus background 1.5e22 cm-2  
  > "Therefore, we treated the column density of 1.5$\times$10$^{22}$ cm$^{-2}$ as the background level." (4.1 Remaining Mass of Core and Envelope around WL 17)
   - parameter: T_B ~1.1 K; Delta v ~0.8 km/s from Gaussian fit; nu = 220 GHz  
  > "We performed a Gaussian fit of the spectra in the area of Figure [8](#fig:envelope) (b) and used the FWHM as the velocity width $\Delta v\,(\sim 0.8$ km s$^{-1}$)." (4.1 Remaining Mass of Core and Envelope around WL 17)
   - assumption: Tex = 10 and 20 K; N(C18O)=1.7e-7 N(H2); mu=2.8  
  > "$T_{\rm ex}$ denotes the excitation temperature, which is assumed to be 10 and 20 K." (4.1 Remaining Mass of Core and Envelope around WL 17)
   - fitting: Gaussian fit to spectrum for FWHM  
  > "We performed a Gaussian fit of the spectra in the area of Figure [8](#fig:envelope) (b) and used the FWHM as the velocity width $\Delta v\,(\sim 0.8$ km s$^{-1}$)." (Discussion, Remaining Mass of Core and Envelope around WL 17)
   - validation: Compared C18O and Herschel masses; difference attributed to missing flux  
  > "This difference can be partly attributed to missing flux in the ALMA observation (cite: Tokuda_2018)." (4.1 Remaining Mass of Core and Envelope around WL 17)
6. **Disk growth timescale**: t_grow = M_disk/Mdot_acc with Mdot_acc = epsilon Mdot_out  
  > "$$\begin{equation} t_{\rm grow} = \frac{M_{\rm disk}}{\dot{M}_{\rm acc}} = \frac{M_{\rm disk}}{\varepsilon \dot{M}_{\rm out}}" (4.5 Uncertainty in Timescale Estimation)
   - parameter: epsilon = 10; M_disk = 0.01 Msun; Mdot_acc ~1e-6 Msun/yr  
  > "Assuming a disk mass of $M_{\rm disk}=0.01\,M_{\odot}$, the disk growth timescale is as short as $(M_{\rm disk}/\dot{M}_{\rm acc}) \sim 10^4$ yr" (4.2 Disk Growth Timescale)
   - fitting: _not stated_
   - validation: Uncertainty discussion: epsilon 3-10 gives factor ~3; estimate is an upper limit  
  > "Thus, the uncertainty in the growth timescale caused by the parameter $\varepsilon$ is a factor of $\sim3$." (4.5 Uncertainty in Timescale Estimation)

## Software

- **CASA** 6.2.1: Calibration, tclean imaging, imcontsub  
  > "The data were calibrated with the Common Astronomy Software Application (cite: McMullin_2007) version 6.2.1." (2.1 High-resolution Continuum Observations)
- **tclean** : Imaging of continuum and line data  
  > "We used only the `tclean` task in our imaging process." (2.1 High-resolution Continuum Observations)
- **imcontsub** : Continuum subtraction from line cubes  
  > "the continuum was subtracted from the $^{12}$CO and C$^{18}$O line data using the CASA task `imcontsub`." (2.2 Molecular Line Observations)

## Numeric results

| quantity | value | uncertainty | units | step | quote |
|---|---|---|---|---|---|
| Ring inner and outer edge radii | 11 and 21 | not stated | au | 2 | the inner and outer edge radius of the outer ring are 11 and 21 au, respectively |
| Inner disk radius upper limit | <5 (FWHM 5.2) | not stated | au | 2 | the estimated FWHM ($5.2$ au) as the upper limit of the radius |
| Ring inclination and PA | i = 33.8, PA = 68.7 | not stated | deg | 2 | we estimated an inclination angle $i_{\rm ring}$ of 33.8$^{\circ}$ and a PA of 68.7$^{\circ}$ |
| Ring peak radius and FWHM | 15.7 and 8.8 | not stated | au | 2 | the peak radius of the outer ring is 15.7 au and the FWHM is 8.8 au |
| Total continuum flux | 4.37e-2 (inner disk 6.6e-4, ring 4.3e-2) | not stated | Jy | 3 | The total flux is $F_{\nu} = 4.37 \times$10$^{-2}$ Jy, which is the sum of the inner disk (6.6$\times$10$^{-4}$ Jy) and outer ring (4.3$\times$10$^{-2}$ Jy). |
| Dust mass | 7.4e-5 | not stated | Msun | 3 | The total dust mass was estimated to be $M_{\rm dust}$=7.4$\times$10$^{-5}\,M_{\odot}$. |
| Outflow total mass | 8.7e-4 | not stated | Msun | 4 | The total mass of the blue-shifted and red-shifted outflows is $M_{\rm out,total}=$8.7$\times$10$^{-4}\, M_{\odot}$ |
| Outflow max velocities (blue, red) | 2.0 and 3.5 | not stated | km/s | 4 | $v_{\rm blue,max}=$2.0$\,{\rm km\,s^{-1}}$ and $v_{\rm red,max}=$3.5$\,{\rm km\,s^{-1}}$ |
| Mean outflow dynamical timescale | 3.0e3 | not stated | yr | 4 | is $t_{\rm dyn}=$ 3.0 $\times 10^3$ yr |
| Total outflow mass ejection rate | 3.6e-7 | not stated | Msun/yr | 4 | we estimated the total mass loss rate (sum of the red and blue shifted outflows) of 3.6$\times$10$^{-7}$ $M_{\odot}$ yr$^{-1}$ |
| H2 mass from C18O | 4e-3 (3.6e-3 to 4.4e-3 for Tex 20/10 K) | not stated | Msun | 5 | The mass of molecular hydrogen estimated from C$^{18}$O is $4\times10^{-3}\,{M}_\odot$. |
| Herschel H2 mass within 1000/2000/3000 au | 1.0e-2 / 5.5e-2 / 1.1e-1 | not stated | Msun | 5 | H$_2$ & Black circle (c) in Fig. [9](#fig:herschel), $R < 3000$ au & 0.9$^\ast$ & 2.8 & 1.1$\times$10$^{-1}$ |
| Disk growth timescale | ~1e4 | order of magnitude; epsilon factor ~3 | yr | 6 | the disk growth timescale is as short as $(M_{\rm disk}/\dot{M}_{\rm acc}) \sim 10^4$ yr |

## Qualitative findings

- No emission detected in the gap or inner disk, so no sign of a planet, circumplanetary disk, or binary companion  
  > "We did not detect any marked emission in either the gap or inner disk, indicating that there is no sign of a planet, circumplanetary disk, or binary companion." (abstract)
- C18O shows an inhomogeneous infalling envelope within ~1000 au  
  > "The C$^{18}$O emission showed that an inhomogeneous infalling envelope, which can induce episodic mass accretion, is distributed in the region within $\sim1000$ au from the central protostar." (abstract)

## Claim tuples

- H: WL 17 has a ring-hole structure | E: 1.3 mm continuum imaging at 0.037''x0.031'' | R: Ring at 11-21 au plus inner disk <5 au radius | F: WL 17 has a ring-gap structure, not ring-hole | **supported**
- H: An outflow is driven by the WL 17 disk | E: 12CO(2-1) channel maps, moment maps, PV diagrams | R: Blue and red outflow bases coincide with the continuum; Mdot_out ~3.6e-7 Msun/yr, t_dyn ~1e3-1e4 yr | F: Outflow associated with the disk; mass ejection currently occurring | **supported**
- H: WL 17 is still in the accretion phase with envelope remaining | E: C18O moment map and Herschel column density mass estimates | R: Envelope H2 mass ~0.1 Msun within 2000-3000 au | F: Accretion phase, late Class I; inhomogeneous envelope | **partially**
- H: Ring-gap formation timescale can be constrained in the accretion phase | E: t_grow = M_disk/(epsilon Mdot_out) | R: t_grow ~1e4 yr | F: Ring-gap may form within ~1e4 yr; neither wind dispersal nor dust growth front explains inner disk | **partially**

## Reasoning

- Why this data: Archival ALMA data have higher angular resolution and sensitivity than earlier Band 3 data  
  > "We used ALMA archival data, which have a higher angular resolution than previous observations." (abstract)
- Why this method: _not stated_
- Alternative: Embedded binary scenario judged not plausible; protoplanet cannot be rejected; wind dispersal and dust growth front cannot explain inner disk  
  > "the embedded binary scenario is not plausible for explaining the ring–gap structure around WL 17." (4.3.1 Embedded Binary System)
- How they decided it was enough: _not stated_
- Limitation (authors): Protostellar mass is uncertain because Keplerian motion cannot be separated from the jet  
  > "Thus, in this study, the protostellar mass is uncertain and cannot be determined accurately." (4.5 Uncertainty in Timescale Estimation)
- Limitation (authors): Outflow mass and velocity are likely underestimated; field of view limits outflow length  
  > "Thus, we will likely underestimate both the mass and velocity of the outflow." (4.5 Uncertainty in Timescale Estimation)
- Caveat (inferred, ours): Few quantitative uncertainties are given for ring geometry, masses and rates
- Caveat (inferred, ours): Tdust=20 K and fixed kappa strongly affect disk mass; the ring is possibly optically thick
- Caveat (inferred, ours): The tan(i) factor in t_dyn with a possibly unreliable inclination and misaligned outflows
- Caveat (inferred, ours): The low-resolution line data (C-7) suffer missing flux, so the envelope mass is poorly constrained
- Caveat (inferred, ours): epsilon=10 and a disk mass of 0.01 Msun are assumed, making the timescale only order of magnitude
- Caveat (inferred, ours): Inner disk is unresolved, so a <5 au upper limit rests on a non-deconvolved Gaussian FWHM

## Reproducibility

- Data public (paper): Archival ALMA data, projects 2019.1.00458.S and 2019.1.01792.S  
  > "This paper makes use of the following ALMA data: ADS/JAO. ALMA#2019.1.00458.S and #2019.1.01792.S." (Acknowledgments)
- Products in archive: _not stated_
- Missing: Line-free channels and continuum spw handling
- Missing: Deconvolution and masking parameters and image sizes
- Missing: Outflow region definitions and velocity channel ranges
- Missing: Exact area and spectrum extraction regions for C18O
- Missing: Herschel map processing details
- Data volume (inferred): ~50-150 GB of raw data for the two ALMA execution blocks (continuum high-resolution and narrow lines); a few GB of products
- Score (inferred): 3/5, Public data and a clear recipe for the main numbers, but imaging details, regions and several assumptions are not fully stated.
- Rediscovery candidate: yes, Data are public, the continuum recipe (tclean, robust 0.5, 0.0037'' cell) is given and the main results (ring radii, flux, masses, rates) are numeric.

## Links

- Method: Yamaguchi et al. 2021 (cite: Yamaguchi_2021) (Ring ellipse fitting method)
- Method: Frerking et al. 1982 (cite: Frerking_1982) (C18O optical depth and column density)
- Companion: Sheehan & Eisner 2017 (cite: Sheehan_2017) (Earlier ALMA Band 3 ring-hole detection of WL 17)
- Companion: van der Marel et al. 2013 (cite: van_der_Marel_2013) (Single-dish CO outflow of WL 17)
- Companion: Han et al. 2023 (cite: Ilseing_2023) (Band 3 and 7 observations of WL 17)
- Related: Herschel Gould Belt Survey

## Checks

```json
{
 "quotes": 87,
 "quotes_ok": 87,
 "quote_pass_rate": 1.0,
 "quotes_too_long": 0,
 "unsupported_facts": 0,
 "project_codes": 2,
 "codes_not_in_text": [],
 "codes_not_in_obscore": [],
 "obscore_codes_not_in_card": [],
 "codes_printed_but_missing": [],
 "numeric_results": 13,
 "numeric_problems": 0,
 "fill": {
  "facts": 89,
  "stated": 65,
  "rate": 0.73
 },
 "evidence_ok": true
}
```
