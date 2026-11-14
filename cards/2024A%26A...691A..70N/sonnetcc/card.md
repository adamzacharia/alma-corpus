# Disruption of a massive molecular cloud by a supernova in the Galactic Centre: Initial results from the ACES project

`2024A&A...691A..70N` | Astronomy and Astrophysics 2024 | first author: Nonhebel, M. | arXiv: 2409.12185 | DOI: 10.1051/0004-6361/202451190

Card schema 1.0 | model claude-sonnet-5-5-claude-code | depth full | type large_program_or_survey

## Science

- Fields: milky_way_ism
- Question: What is the origin of the massive ring-like molecular structure M0.8-0.2 in the Galactic Centre (young-star feedback, supernova feedback, cloud-cloud collision, shear, or line-of-sight coincidence)?  
  > "In Sect. [4](#sec_cause) we discuss possible causes of the structure, including young (Sect. [4.1](#subsec_youngfeedback)) and late-stage (Sect. [4.2](#subsec_supernova)) stellar feedback" (Introduction); "We investigated this, and reached the following conclusions." (5 Conclusions)
- Target **M0.8-0.2 ring (CMZ, south-east extension of Sgr B2)**: coordinates l = 0.804 deg, b = -0.184 deg (ring centre, manually determined)  
  > "We manually determined the centre of the M0.8$-$0.2 ring to be $l=0.^{\circ}804$ and $b=-0.^{\circ}184$" (3.1 Morphology); "at the distance of the CMZ (8.2 kpc; (cite: GRAVITYCollaboration2021))" (3.1 Morphology); z/distance 8.2 kpc (distance of the CMZ)  
  > "We manually determined the centre of the M0.8$-$0.2 ring to be $l=0.^{\circ}804$ and $b=-0.^{\circ}184$" (3.1 Morphology); "at the distance of the CMZ (8.2 kpc; (cite: GRAVITYCollaboration2021))" (3.1 Morphology); distance from GRAVITY Collaboration 2021 (cite: GRAVITYCollaboration2021)  
  > "We manually determined the centre of the M0.8$-$0.2 ring to be $l=0.^{\circ}804$ and $b=-0.^{\circ}184$" (3.1 Morphology); "at the distance of the CMZ (8.2 kpc; (cite: GRAVITYCollaboration2021))" (3.1 Morphology)

## Data provenance

- ALMA projects: 2021.1.00172.L
- bands: Band 3; six spectral windows  
  > "The ACES dataset comprises six spectral windows in Band 3" (2 Observations)
- frequencies and spectral setup: two narrow windows (~0.2 km/s channels) around HNCO(4-3); two intermediate (~1.7 km/s) windows with H13CN, H13CO+, SiO, HN13C; two broad (~3 km/s) windows for continuum, CS, SO, HC3N  
  > "There are two narrow windows with high spectral resolution ($\sim$ 0.2 km s$^{-1}$channels) around the HNCO(4–3) transition lines" (2 Observations)
- continuum bandwidth: _not stated_
- arrays: 12 m array, 7 m ACA and total power (feathered)  
  > "we feathered the (primary beam corrected) 7 m Atacama Compact Array (ACA) and total power cubes in CASA (cite: Casa2022), before feathering these cubes to the (primary beam corrected) 12 m array cube." (2 Observations)
- configurations: _not stated_
- baselines: _not stated_
- angular resolution: average spatial scale 0.1 pc; HNCO beam 2.81 arcsec, other lines 2.17-2.72 arcsec (circularised)  
  > "The average spatial resolution of the cubes corresponds to a spatial scale of 0.1 pc." (2 Observations); "HNCO | 4–3 | 87.9252 | 10.5 | 2.1 | 2.81 | 0.24" (Observational information)
- max recoverable scale: _not stated_
- sensitivity: RMS 0.24 K (HNCO cube, 0.5 km/s) and 0.07-0.09 K (other cubes, 3 km/s)  
  > "Note the HNCO cube used throughout this study has a velocity resolution of 0.5 km s$^{-1}$, whereas the remaining cubes have a resolution of 3 km s$^{-1}$." (Observational information); "HC$_{3}$N | 11–10 | 100.0763 | 28.8 | 16 | 2.17 | 0.07" (Observational information)
- time on source: _not stated_
- observing dates: _not stated_
- pi or archival as stated: ACES large programme, initial internal release version; not yet public  
  > "represent an initial internal release version of the dataset" (2 Observations)
- Line: HNCO 4-3 (87.9252 GHz)
- Line: SO 2_2-1_1 (86.0940 GHz)
- Line: H13CN 1-0 (86.3399 GHz)
- Line: H13CO+ 1-0 (86.7543 GHz)
- Line: SiO 2-1 (86.8470 GHz)
- Line: HN13C 1-0 (87.0909 GHz)
- Line: CS 2-1 (97.9810 GHz)
- Line: HC3N 11-10 (100.0763 GHz)
- Line: H40alpha H40alpha recombination line (not stated)
- Other facility **GBT / MUSTANG Galactic Plane Survey (MGPS90)**: Single-dish 3 mm continuum image feathered with the 12 m array continuum image  
  > "the 12 m array image is feathered to the Green Bank Telescope (GBT) image from MUSTANG Galactic Plane Survey" (2 Observations)
- Other facility **Herschel (Hi-GAL)**: 250 micron image used to define the ring centre and radii (and column density for the ring)  
  > "to define the centre and size of the ring-like structure, rather than the ACES continuum image, due to its higher signal-to-noise detection of the large-scale structure and lack of contamination" (3.1 Morphology)
- Other facility **Mopra**: 3 mm survey observations for comparison (HNCO)  
  > "Mopra 3 mm observations (cite: Jones2012), and MeerKAT 20 cm observations (cite: Heywood2022)." (2 Observations)
- Other facility **MeerKAT**: 20 cm radio continuum, spectral indices, surface brightness  
  > "Mopra 3 mm observations (cite: Jones2012), and MeerKAT 20 cm observations (cite: Heywood2022)." (2 Observations)
- Other facility **Chandra**: X-ray: no extended emission associated with the ring  
  > "we find no extended X-ray emission associated with the M0.8$-$0.2 ring" (4.2 Feedback from supernova(e))
- Other facility **VVV survey**: Infrared data used to search for a stellar overdensity  
  > "we checked the infrared data from the VISTA Variables in the Via Lactea (VVV) survey (cite: Minniti2010)" (3.4 Multi-wavelength view)
- External data: Previous mass of the ring, 2.6e5 Msun, from Herschel-based column density  
  > "(cite: Mills2017) determined a mass of $2.6 \times 10^5$ M$_\odot$" (3.3 Mass, energy, and momentum) [from Mills & Battersby 2017 (cite: Mills2017)]
- External data: Previous mass of the ring, 2.7e3 Msun, from CS(1-0) radiative transfer  
  > "(cite: Tsuboi2015) estimated a mass of $2.7 \times 10^3$ M$_\odot$ from radiative transfer modelling of CS (1–0) emission" (3.3 Mass, energy, and momentum) [from Tsuboi et al. 2015 (cite: Tsuboi2015)]
- External data: HNCO column density and abundance (N_H2 ~ 7e22 cm^-2, log X_HNCO ~ -8) from a multi-transition analysis, used to check the assumed ranges  
  > "estimated using a multi-transition analysis ((cite: Martin2008); note that here we can only make use of a single transition of HNCO covered by the ACES survey)" (3.3 Mass, energy, and momentum) [from Martin et al. 2008 (cite: Martin2008)]
- External data: Plane-of-sky magnetic field strength 0.22-0.57 mG  
  > "as well as the plane-of-sky magnetic field strength measured by (cite: Butterfield2024)" (Table 1) [from Butterfield et al. 2024 (cite: Butterfield2024)]
- External data: Lyman continuum flux formula N_LyC from flux density, frequency, Te and distance  
  > "we first calculated the Lyman continuum ionising flux using the following, as set out by (cite: Schmiedeke2016)" (4.1 Feedback from young high-mass star(s)) [from Schmiedeke et al. 2016 (cite: Schmiedeke2016)]
- External data: HNCO position-velocity plot of the CMZ used to place the velocity components  
  > "Figure [1](#fig_CMZ_HNCO_peak) (lower-right panel) shows the PV plot of (cite: Henshaw2016a) for the same area of the CMZ as the upper-right panel in the same figure." (3.2 Kinematics and expansion) [from Henshaw, Longmore & Kruijssen 2016 (cite: Henshaw2016a)]
- Simulation/model as data: Grid of Radex one-dimensional non-LTE models (T_kin 30-150 K, n_H2 10^2-10^8 cm^-3, line widths 5/10/20 km/s, X_HNCO 10^-10-10^-6) compared with observed HNCO brightness temperature  
  > "The kinetic temperature ($T_\mathrm{kin}$) ranged from 30 to 150 K with a step size of 10 K." (3.3 Mass, energy, and momentum); "The line-width values considered were 5, 10, and 20 km s$^{-1}$." (3.3 Mass, energy, and momentum)

## Processing

### Calibration

- pipeline or manual: ALMA pipeline with minor modifications (data size mitigation, fixing divergent cleans)  
  > "with only minor modifications to account for the size mitigation of the data in the ALMA pipeline and fixing divergent cleans." (2 Observations)
- casa version: CASA 6.2.1-7 and 6.4.1.12  
  > "CASA versions 6.2.1-7 and 6.4.1.12; pipeline versions 2021.2.0.128 and 2022.2.0.64" (2 Observations)
- pipeline version: pipeline 2021.2.0.128 and 2022.2.0.64  
  > "CASA versions 6.2.1-7 and 6.4.1.12; pipeline versions 2021.2.0.128 and 2022.2.0.64" (2 Observations)
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
- primary beam correction: 7 m and 12 m cubes primary beam corrected before feathering  
  > "we feathered the (primary beam corrected) 7 m Atacama Compact Array (ACA) and total power cubes in CASA" (2 Observations)
- array combination: Feather ACA + total power cubes, then feather to 12 m cube; four mosaics combined with weighting to mitigate edge noise; 3 mm continuum 12 m image feathered to GBT MGPS90  
  > "we feathered the (primary beam corrected) 7 m Atacama Compact Array (ACA) and total power cubes in CASA (cite: Casa2022), before feathering these cubes to the (primary beam corrected) 12 m array cube." (2 Observations); "which are combined to a single cube, using appropriate weighting across the mosaic fields to mitigate for the increased noise at the map edges caused by the primary beam response." (2 Observations)
- smoothing: HNCO cube at 0.5 km/s working resolution; other lines regridded to 3 km/s  
  > "The data cubes of the other spectral lines were re-gridded to a spectral resolution of 3 km s$^{-1}$, for consistency with the lowest spectral resolution window." (2 Observations)
- final beam: circularised beams 2.17-2.81 arcsec across lines (HNCO 2.81 arcsec)  
  > "HNCO | 4–3 | 87.9252 | 10.5 | 2.1 | 2.81 | 0.24" (Observational information)
- final rms: HNCO 0.24 K; other lines 0.07-0.09 K  
  > "HC$_{3}$N | 11–10 | 100.0763 | 28.8 | 16 | 2.17 | 0.07" (Observational information)

### Inherited from earlier work

- ALMA pipeline calibration and imaging procedure  
  > "CASA versions 6.2.1-7 and 6.4.1.12; pipeline versions 2021.2.0.128 and 2022.2.0.64; see (cite: Hunter2023)" (2 Observations) [from Hunter et al. 2023 (cite: Hunter2023)]
- Full description of the ACES data reduction deferred to a later publication  
  > "The complete dataset will be made available to the public with the full description of the data reduction in a later publication (ACES collaboration, in prep.)." (2 Observations) [from ACES collaboration, in prep.]
- Lyman continuum flux prescription  
  > "we first calculated the Lyman continuum ionising flux using the following, as set out by (cite: Schmiedeke2016)" (4.1 Feedback from young high-mass star(s)) [from Schmiedeke et al. 2016 (cite: Schmiedeke2016)]
- Radex non-LTE radiative transfer code  
  > "using the one-dimensional non-local thermodynamic equilibrium radiative transfer code Radex (see Fig. [5](#fig_HNCO_radex); (cite: vanderTak2007))" (3.3 Mass, energy, and momentum) [from van der Tak et al. 2007 (cite: vanderTak2007)]

### Not stated but needed to reproduce (our reading)

- Exact ACES pipeline modifications (size mitigation, divergent-clean fixes), weighting/robust, cell size, image size, deconvolver and masks for the cubes
- Continuum subtraction method and line-free channels for the line cubes
- Feathering parameters (uv cutoffs, scaling factor) for ACA/TP/12 m and for the GBT combination
- How the four mosaics were stitched and the weighting scheme used
- Exact area/pixels used for the average HNCO spectrum and the Gaussian fit initial guesses
- Herschel column density map source and processing used for N_H2 = 8.5e22 cm^-2
- Radex setup: collisional rate file, background temperature, how the likelihood contours (90 per cent) were computed from the grid
- Flux calibration accuracy and self-calibration for ACES
- Details of the 3 mm continuum flux measurement of the point source (aperture, background)

## Analysis recipe

1. **Define ring centre and radii**: Manually set centre; computed mean flux radial profile of Herschel 250 micron image and took radii where the profile falls to 50% of the ring peak  
  > "we defined inner and outer radii where the mean is 50$\%$ of this peak value" (3.1 Morphology); "We manually determined the centre of the M0.8$-$0.2 ring to be $l=0.^{\circ}804$ and $b=-0.^{\circ}184$" (3.1 Morphology)
   - parameter: r_in = 79 arcsec, r_out = 154 arcsec (3.2 and 6.2 pc at 8.2 kpc in text; 3.1/6.1 pc in table)  
  > "This yields $r_\mathrm{in}= 79\ensuremath{''}$ and $r_\mathrm{out}=154\ensuremath{''}$" (3.1 Morphology)
   - assumption: Distance 8.2 kpc  
  > "at the distance of the CMZ (8.2 kpc; (cite: GRAVITYCollaboration2021))" (3.1 Morphology)
   - assumption: Deprojected values assume inclination i = 45 deg (ellipsoid elongated along the line of sight)  
  > "We assumed an inclination angle of $i=45^{\circ}$" (3.1 Morphology)
   - fitting: _not stated_
   - validation: _not stated_
2. **Fit HNCO line profile, derive expansion speed and age**: Single Gaussian fit to the 38 km/s HNCO component of the average spectrum; v_exp = v_FWHM/2; age = r_out/v_exp  
  > "We fitted a single Gaussian profile to the 38 km s$^{-1}$ component present in the HNCO emission" (3.2 Kinematics and expansion); "We estimated the expansion velocity to be $v\textsubscript{exp} = (v\textsubscript{FWHM})/2 =$ 15.1 km s$^{-1}$." (3.2 Kinematics and expansion)
   - software: PySpecKit
   - parameter: Other velocity components at ~-25 and ~100 km/s excluded as unassociated line-of-sight material  
  > "We thus concluded that these two components represent line-of-sight material unassociated with the M0.8-0.2 ring and hence omitted them from our analysis." (3.2 Kinematics and expansion)
   - assumption: Velocity gradient interpreted as shell expansion; constant velocity  
  > "Here we interpreted the blueshifted and redshifted material to represent the foreground and background parts of a three-dimensional shell of material, respectively" (3.2 Kinematics and expansion); "Assuming the velocity has remained constant throughout the expansion, we calculated $t_\mathrm{age} \sim 0.4$ Myr" (3.2 Kinematics and expansion)
   - fitting: Gaussian profile fit with PySpecKit; line-width corrected for channel width; priors/sampler not stated  
  > "using the PySpecKit package (cite: Ginsburg2011; Ginsburg2022)" (3.2 Kinematics and expansion)
   - validation: Compared with PV plots and channel maps to judge which components belong to the ring  
  > "the HNCO emission from the velocity components at $-$25 and 100 km s$^{-1}$ from the ACES observations do not show any morphological similarity with the HNCO emission of the main component" (3.2 Kinematics and expansion)
3. **Estimate gas density with non-LTE radiative transfer**: Grid of Radex models (SpectralRadex) in T_kin, n_H2, line width, X_HNCO; frequency of models reproducing observed brightness temperature 1-5 K; depth L = N_H2/n_H2 bounded  
  > "depict the frequency with which the models produce brightness temperatures within the observed range of 1 to 5 K for the M0.8$-$0.2 ring" (3.3 Mass, energy, and momentum); "Bounds on the depth are imposed, assuming that the structure should not be much deeper than its projected size ($\sim 10$ pc) and should not be smaller than the angular resolution of our observations ($\sim 0.1$ pc)." (3.3 Mass, energy, and momentum)
   - software: Radex, SpectralRadex
   - parameter: n_H2 grid 10^2-10^8 cm^-3, step 0.05 dex; X_HNCO 10^-10-10^-6, step 0.05 dex  
  > "The number density of molecular hydrogen ($n_\mathrm{H_2}$) spanned $10^2$ to $10^8$ cm$^{-3}$ with a step size of 0.05 dex." (3.3 Mass, energy, and momentum)
   - assumption: Fixed N_H2 = 8.5e22 cm^-2 (Herschel average over the ring)  
  > "We assumed a fixed molecular hydrogen column density ($N_\mathrm{H_2}$) of $8.5 \times 10^{22}$ cm$^{-2}$" (3.3 Mass, energy, and momentum)
   - fitting: Grid search with likelihood contours (90 per cent contour quoted); peak likelihood n_H2 ~ 10^4.2 cm^-3  
  > "The analysis yields a peak likelihood of $n_{\mathrm{H2}} \approx 10^{4.2}$ cm$^{-3}$," (3.3 Mass, energy, and momentum)
   - validation: Cross-check against shell-width estimate (n ~ 10^4.1 cm^-3) and Martin et al. 2008 abundance  
  > "A simple check of this value can be done by comparing our HNCO-derived density with what we get if we divide the mean H$_2$ column density by twice the shell width" (3.3 Mass, energy, and momentum)
4. **Compute mass, kinetic energy and momentum for several geometries**: Constant density 10^4.2 cm^-3 times shell volume (spherical, inclined ellipsoidal, with filling factor 0.5); E = 0.5 M v^2, p = M v  
  > "Taking a constant density of $10^{4.2}$ cm$^{-3}$, and assuming a complete spherical shell geometry with inner and outer radii of 3.1 pc and 6.1 pc" (3.3 Mass, energy, and momentum); "we calculated its kinetic energy ($E\textsubscript{d,f} = 0.5 M\textsubscript{d,f} v\textsubscript{exp,d}^2$)" (3.3 Mass, energy, and momentum)
   - parameter: Filling factor f = 0.5 and inclination 45 deg for best estimate  
  > "Assuming instead a clumpy or partial shell with a filling factor of a half (i.e. $f=0.5$) decreases both of these mass estimates by a factor of 2." (3.3 Mass, energy, and momentum)
   - assumption: Uniform density across the shell  
  > "All mass values are calculated assuming a constant density of $10^{4.2}$ cm$^{-3}$, determined from radiative transfer modelling." (Table 1)
   - fitting: _not stated_
   - validation: Compared with literature masses (Mills & Battersby 2017; Tsuboi et al. 2015)  
  > "These estimates are in agreement with the mass determined from the *Herschel*-derived H$_2$ column density map (cite: Mills2017)" (3.3 Mass, energy, and momentum)
5. **Test the compact HII region as the progenitor**: Measure 3 mm flux of the point source in the 12 m-only continuum map, compute Lyman continuum flux, infer stellar type/mass and energy budget  
  > "where $S_v$ is the integrated flux density of the source, measured in the 12 m-only continuum map to be 36 mJy, with a central frequency, $v$, of 98.6 GHz" (4.1 Feedback from young high-mass star(s))
   - parameter: S_v = 36 mJy at 98.6 GHz, d = 8.2 kpc  
  > "where $S_v$ is the integrated flux density of the source, measured in the 12 m-only continuum map to be 36 mJy, with a central frequency, $v$, of 98.6 GHz" (4.1 Feedback from young high-mass star(s))
   - assumption: Electron temperature 5000 K  
  > "$T_\textsubscript{e}$ is the electron temperature, assumed to be 5000 K" (4.1 Feedback from young high-mass star(s))
   - assumption: 10% coupling efficiency and 50% escape fraction for stellar feedback  
  > "Assuming a conservative coupling efficiency of 10$\%$ and an escape fraction of 50$\%$" (4.1 Feedback from young high-mass star(s))
   - fitting: _not stated_
   - validation: H40alpha velocity (~100 km/s) inconsistent with ring (~50 km/s) at that position  
  > "we find that the ACES H40$\alpha$ spectrum peaks at $\sim$100 km s$^{-1}$, which differs significantly from the molecular gas associated with the M0.8$-$0.2 ring at this position" (4.1 Feedback from young high-mass star(s))
6. **Compare ring energetics with supernova feedback**: Compare kinetic energy to ~10^51 erg per SN with coupling efficiency; estimate minimum number of SNe; test hypernova and Sigma-r relation  
  > "To derive an approximate minimum number of SNe required to power the expansion of the structure, we assumed a generous coupling efficiency of 30$\%$ and an injected energy of $10^{51}$ erg." (4.2 Feedback from supernova(e))
   - parameter: Coupling efficiency 30%, injected energy 1e51 erg per SN  
  > "we assumed a generous coupling efficiency of 30$\%$ and an injected energy of $10^{51}$ erg" (4.2 Feedback from supernova(e))
   - assumption: Energy of multiple SNe is additive  
  > "Assuming the impact of multiple SNe is additive" (4.2 Feedback from supernova(e))
   - fitting: _not stated_
   - validation: Checked against X-ray, radio spectral index, magnetic field geometry and Sigma-r relation  
  > "We also checked for consistency with the typical relationship held by SNRs between radio surface brightness and size" (4.2 Feedback from supernova(e))

## Software

- **CASA** 6.2.1-7 and 6.4.1.12: ALMA pipeline calibration/imaging and feathering of ACA, total power and 12 m cubes  
  > "we feathered the (primary beam corrected) 7 m Atacama Compact Array (ACA) and total power cubes in CASA (cite: Casa2022)" (2 Observations)
- **ALMA pipeline** 2021.2.0.128 and 2022.2.0.64: Calibration and imaging of ACES data  
  > "The calibration and imaging were conducted with the ALMA pipeline" (2 Observations)
- **PySpecKit** : Gaussian fit to the HNCO 38 km/s component  
  > "using the PySpecKit package (cite: Ginsburg2011; Ginsburg2022)" (3.2 Kinematics and expansion)
- **Radex** : 1D non-LTE radiative transfer for HNCO density  
  > "using the one-dimensional non-local thermodynamic equilibrium radiative transfer code Radex" (3.3 Mass, energy, and momentum)
- **SpectralRadex** : Python implementation of Radex used for the model grid  
  > "We made use of the SpectralRadex python package implementation of Radex (cite: Holdship2021)" (3.3 Mass, energy, and momentum)
- **Astropy** : Python packages used in the project  
  > "This project made use of the Astropy, APLpy, PySpecKit, SpectralRadex python packages" (Acknowledgements)
- **APLpy** : Plotting (listed as used in the project)  
  > "This project made use of the Astropy, APLpy, PySpecKit, SpectralRadex python packages" (Acknowledgements)

## Numeric results

| quantity | value | uncertainty | units | step | quote |
|---|---|---|---|---|---|
| HNCO centroid velocity | 37.5 | 1.7 | km/s | 2 | We determined a centroid velocity ($v\textsubscript{cent}$) of 37.5$\pm$1.7 km s$^{-1}$and a line-width ($v\textsubscript{FWHM}$) of 30.1$\pm$4.0 km s$^{-1}$ |
| HNCO line-width (FWHM) | 30.1 | 4.0 | km/s | 2 | We determined a centroid velocity ($v\textsubscript{cent}$) of 37.5$\pm$1.7 km s$^{-1}$and a line-width ($v\textsubscript{FWHM}$) of 30.1$\pm$4.0 km s$^{-1}$ |
| Expansion velocity v_exp | 15.1 | not stated | km/s | 2 | We estimated the expansion velocity to be $v\textsubscript{exp} = (v\textsubscript{FWHM})/2 =$ 15.1 km s$^{-1}$. |
| Deprojected expansion velocity v_exp,d (i = 45 deg) | 21.3 | not stated | km/s | 2 | which gives $v\textsubscript{exp, d} \sim 21.3$ km s$^{-1}$ |
| Inner and outer radii | 79 and 154 | not stated | arcsec | 1 | This yields $r_\mathrm{in}= 79\ensuremath{''}$ and $r_\mathrm{out}=154\ensuremath{''}$ |
| Ring age t_age = r_out/v_exp | ~0.4 | not stated | Myr | 2 | we calculated $t_\mathrm{age} \sim 0.4$ Myr |
| Peak-likelihood H2 number density | 10^4.2 (range 10^3.5 to 10^5.5) | not stated | cm^-3 | 3 | The analysis yields a peak likelihood of $n_{\mathrm{H2}} \approx 10^{4.2}$ cm$^{-3}$, |
| Mass, complete spherical shell (text value; Table 1 lists 7.6e5) | 7.5e5 | not stated | Msun | 4 | we calculated a total mass of $M$ = 7.5 $\times$ 10$^{5}$ M$_\odot$ |
| Best mass estimate M_d,f (inclined, partial shell) | 5.4e5 | not stated | Msun | 4 | yielding $M\textsubscript{d,f}$ = 5.4 $\times$ 10$^{5}$ M$_\odot$. |
| Kinetic energy E_d,f and momentum p_d,f | 2.4e51 erg; 1.1e7 Msun km/s | not stated | erg; Msun km/s | 4 | We find $E\textsubscript{d,f} = 2.4$ $\times$ $10^{51}$ erg and $p\textsubscript{d,f} = 1.1$ $\times$ $10^7$ $\textup{M}_{\odot}$ km s$^{-1}$ |
| Minimum number of SNe to power the expansion | 8 | not stated | dimensionless | 6 | we find eight SNe are required |
| Number of O9/B0 stars needed to power expansion | ~500 | not stated | dimensionless | 5 | $\sim$ 500 similar O9/B0 stars are needed to power the expansion of the structure |

## Qualitative findings

- HNCO(4-3) shows a filamentary, whirlpool-like ring with coherent kinematics over ~10 pc; the 100 km/s and -25 km/s components are unrelated line-of-sight gas  
  > "The structure appears to be coherent in its kinematics across a size-scale of $\sim$ 10 pc" (5 Conclusions)
- Supernova feedback is a viable but atypical cause; multiple clustered SNe or a hypernova would be needed, none of the alternatives gives a clean explanation  
  > "Supernova feedback could be a viable cause, and would provide an explanation for the non-thermal radio emission observed towards the region." (5 Conclusions); "None of these scenarios provide a clean explanation for the structure" (5 Conclusions)

## Claim tuples

- H: Is the ring an expanding shell driven by early-stage stellar feedback from a compact HII region? | E: Identified H40alpha point source, measured 3 mm flux, computed ionising flux and compared velocities | R: Source has ~100 km/s velocity (ring ~50 km/s), single ~20 Msun star gives ~5e50 erg | F: Early-stage young-star feedback is argued against | **supported**
- H: Is the ring a supernova remnant? | E: Compared ring energy (2.4e51 erg) with SN energy budget, radio spectral index, X-ray, magnetic field and Sigma-r relation | R: Needs coupling efficiency >100% for one SN; eight SNe needed at 30%; atypically compact for its radio brightness | F: SN feedback (multiple SNe or hypernova) is viable but unusual | **partially**
- H: Can cloud-cloud collisions, shear or line-of-sight coincidence explain the ring? | E: Inspected PV cuts and channel maps, compared with CMZ dynamics | R: No clear bridge features; velocity gradient direction opposite to shear simulations; structure coherent across lines | F: None provides a clean explanation | **partially**
- H: What is the mass of the ring? | E: Radex modelling of HNCO(4-3) for density, then shell volume | R: M_d,f = 5.4e5 Msun (M ~7.5e5 to 1.1e6 for full shells) | F: Mass of order 10^6 Msun, much higher than the earlier CS-based value | **supported**

## Reasoning

- Why this data: ACES gives an order of magnitude higher spatial and spectral resolution view of dense and shocked gas across the CMZ  
  > "which provides an order of magnitude higher spatial and spectral resolution view of the dense and shocked gas across the whole CMZ" (Introduction)
- Why this method: Herschel 250 micron used to define the ring rather than ACES 3 mm continuum because of higher S/N and no free-free/synchrotron contamination  
  > "to define the centre and size of the ring-like structure, rather than the ACES continuum image, due to its higher signal-to-noise detection of the large-scale structure and lack of contamination" (3.1 Morphology)
- Alternative: Using FWTM instead of FWHM would raise the expansion velocity by ~1.8  
  > "The full width at tenth maximum (FWTM) could also be employed in this calculation to encompass the more extreme velocities" (Footnote 2)
- Alternative: Re-reduced HiGal data with background subtraction (Guzman et al. 2015) gave no significant difference, so original HiGal processing kept  
  > "We find the differences were not significant and thus retain the HiGal processed results." (Footnote 1)
- How they decided it was enough: HNCO cube kept at 0.5 km/s because full 0.2 km/s resolution is not needed for large-scale structure  
  > "which provides a balance between resolution and sensitivity" (2 Observations)
- Limitation (authors): Expansion velocity is a lower limit because of projection effects  
  > "We acknowledge that this estimate is a lower limit due to projection effects" (3.2 Kinematics and expansion)
- Limitation (authors): Three-dimensional geometry unknown; effects of clustered SNe not well understood; comprehensive kinematic analysis left to future work  
  > "In the absence of prior knowledge regarding the three-dimensional structure of the molecular cloud" (3.3 Mass, energy, and momentum); "We note that the effect of subsequent SN explosions is not well understood" (4.2 Feedback from supernova(e))
- Caveat (inferred, ours): Mass depends on a single HNCO transition and a fixed N_H2 plus a uniform-density shell; the quoted values carry no uncertainties
- Caveat (inferred, ours): Expansion speed from FWHM/2 of one Gaussian is an assumption; rotation or shear (3 km/s/pc gradient) could mimic it
- Caveat (inferred, ours): Text and Table 1 disagree slightly (7.5e5 vs 7.6e5 Msun; 3.1/6.1 vs 3.2/6.2 pc)
- Caveat (inferred, ours): Data are an internal, non-public ACES release with unspecified processing

## Reproducibility

- Data public (paper): Not yet public; to be released later by the ACES collaboration  
  > "The complete dataset will be made available to the public with the full description of the data reduction in a later publication (ACES collaboration, in prep.)." (2 Observations)
- Products in archive: _not stated_
- Missing: Public ACES cubes (internal release only)
- Missing: Imaging parameters and feathering settings
- Missing: Exact spectrum extraction region and Gaussian fit setup
- Missing: Herschel column density map used for N_H2
- Missing: Radex configuration and likelihood construction
- Data volume (inferred): Large: four feathered ACES mosaics (~150 pointings each) in Band 3; many hundreds of GB to TB for raw plus cubes
- Score (inferred): 2/5, Recipe for kinematics and energetics is clear and numeric, but the ACES data are not yet public and imaging/feathering settings and the Radex setup are not given.
- Rediscovery candidate: no, The ACES data used are an internal release not yet public, and imaging details are deferred to an in-prep paper.

## Links

- Method: Hunter et al. 2023 (cite: Hunter2023) (ALMA pipeline used for calibration and imaging)
- Method: CASA Team 2022 (cite: Casa2022) (CASA used for feathering)
- Method: van der Tak et al. 2007 (cite: vanderTak2007) (Radex code)
- Method: Schmiedeke et al. 2016 (cite: Schmiedeke2016) (Lyman continuum flux formula)
- Companion: Butterfield et al. 2024 (cite: Butterfield2024) (Multi-wavelength and polarisation study of the same ring)
- Companion: Longmore et al. in prep; ACES collaboration in prep. (ACES survey and data release description)
- Related: ALMA CMZ Exploration Survey (ACES), 2021.1.00172.L
- Related: FIREPLACE (SOFIA/HAWC+ polarimetry)
- Related: Mopra 3 mm and 7 mm CMZ surveys
- Related: MeerKAT Galactic Centre survey

## Checks

```json
{
 "quotes": 122,
 "quotes_ok": 122,
 "quote_pass_rate": 1.0,
 "quotes_too_long": 0,
 "unsupported_facts": 0,
 "project_codes": 1,
 "codes_not_in_text": [],
 "codes_not_in_obscore": [],
 "obscore_codes_not_in_card": [],
 "codes_printed_but_missing": [],
 "numeric_results": 12,
 "numeric_problems": 0,
 "fill": {
  "facts": 105,
  "stated": 79,
  "rate": 0.752
 },
 "evidence_ok": true
}
```
