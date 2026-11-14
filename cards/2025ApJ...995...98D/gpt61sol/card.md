# DiskMINT: Self-consistent Thermochemical Disk Models with Radially Varying Gas and Dust—Application to the Massive, CO-Rich Disk of IM Lup

`2025ApJ...995...98D` | The Astrophysical Journal 2025 | first author: Deng, Dingshan | arXiv: 2509.15487 | DOI: 10.3847/1538-4357/ae0e66

Card schema 1.0 | model gpt-6.1-sol | depth full | type archival_reuse

## Science

- Fields: protoplanetary_disks
- Question: Infer the mass and surface density distribution of the IM Lup disk with self-consistent thermochemical models.  
  > "we use `DiskMINT` to investigate the mass and surface density distribution of the IM Lup disk." (The Large Disk of IM Lup)
- Target **IM Lup (Sz 82)**: coordinates _not stated_; z/distance 158.9 pc in text; 158±0.5 pc in Table 1  
  > "IM Lup (Sz 82) is a $\sim 1$ Myr-old star (cite: mawet_direct_2012) located at a distance of $158.9\,{\rm pc}$ (`Gaia` DR3; (cite: gaia_collaboration_gaia_2023)) in the Lupus star-forming region." (The Large Disk of IM Lup); "| distance | $D$ | 158$\pm$0.5 pc | \[2\] |" (Table 1); "\[2\] (cite: gaia_collaboration_gaia_2023);" (Table 1); distance from Gaia DR3 (cite: gaia_collaboration_gaia_2023)  
  > "IM Lup (Sz 82) is a $\sim 1$ Myr-old star (cite: mawet_direct_2012) located at a distance of $158.9\,{\rm pc}$ (`Gaia` DR3; (cite: gaia_collaboration_gaia_2023)) in the Lupus star-forming region." (The Large Disk of IM Lup); "| distance | $D$ | 158$\pm$0.5 pc | \[2\] |" (Table 1); "\[2\] (cite: gaia_collaboration_gaia_2023);" (Table 1)

## Data provenance

- ALMA projects: 2016.1.00484.L, 2018.1.01055.L
- bands: Band 6 for fitting; Band 3 for validation  
  > "Note that the models are fit to the higher quality ALMA Band 6 data, without considering the poorer quality Band 3 information." (Band 3 analysis)
- frequencies and spectral setup: Continuum at 110 GHz and 240 GHz; C18O (2-1) fitting and C18O (1-0) validation  
  > "Here we present the results of the ALMA Band 3 continuum at 110 GHz and $\rm C^{18}O\,(1-0)$ line emission for the structured model" (Band 3 analysis); "The continuum emission shows that the slightly larger dust grains ($\sim 0.03\,{\rm cm}$) traced at 110 GHz have a similar distribution compared to the grains ($\sim 0.01\,{\rm cm}$) traced at 240 GHz." (Band 3 analysis); "both $\Sigma_{\rm dust}(r)$ and $\Sigma_{\rm gas}(r)$ are set in iterations by fitting the dust continuum and $\rm C^{18}O\,(2-1)$ line radial profiles" (Step 2. Derive gas surface density)
- continuum bandwidth: _not stated_
- arrays: _not stated_
- configurations: _not stated_
- baselines: _not stated_
- angular resolution: _not stated_
- max recoverable scale: _not stated_
- sensitivity: _not stated_
- time on source: _not stated_
- observing dates: _not stated_
- pi or archival as stated: _not stated_
- Line: C18O 2-1 (not stated)
- Line: C18O 1-0 (not stated)
- Other facility **Gaia DR3**: Distance to IM Lup  
  > "located at a distance of $158.9\,{\rm pc}$ (`Gaia` DR3; (cite: gaia_collaboration_gaia_2023))" (The Large Disk of IM Lup)
- Other facility **SMA**: Multiwavelength (sub)millimeter continuum measurements used in earlier dust-mass estimates  
  > "A large $M_{\rm dust}\sim 1.0-2.0\times10^{-3}\,M_\odot$ was inferred from its bright (sub)millimeter continuum emission observed from SMA and ALMA using multiple wavelengths." (The Large Disk of IM Lup)
- Other facility **University of Arizona HPC**: High Performance Computing resources  
  > "This work made use of the High Performance Computing (HPC) resources, which are supported by the University of Arizona TRIF, UITS, and Research, Innovation, and Impact (RII)" (Acknowledgments)
- External data: DSHARP high angular resolution continuum image and radial profile  
  > "We compare the radial profile inferred from the synthetic continuum image with the profile inferred from a high angular resolution image from DSHARP (cite: huang_disk_2018)," (Step 1. Derive dust surface density) [from (cite: huang_disk_2018)]
- External data: MAPS imaging parameters, gas inclination 47.5°, PA 144.5°, systemic velocity 4.5 km s−1  
  > "generate synthetic images using the same imaging parameters from MAPS data," (dust-to-gas mass ratio); "The adopted gas disk inclination ($i = 47.5\ensuremath{^\circ}$), position angles (${\rm PA} = 144.5\ensuremath{^\circ}$), and the systematic velocity ($v_{\rm sys} = 4.5 \,\mathrm{km\,s^{-1}}$) are also from MAPS CO isotopologue data (cite: zhang_MAPS_molecules_2021)." (dust-to-gas mass ratio) [from (cite: zhang_MAPS_molecules_2021)]
- External data: Stellar mass 1.1 M_sun and radius 2.5 R_sun  
  > "| stellar mass | $M_\mathrm{\star}$ | 1.1$\,M_\odot$ | \[1\] |" (Table 1); "| stellar radius | $r_\mathrm{\star}$ | 2.5$\,R_\odot$ | \[1\] |" (Table 1); "\[1\] (cite: zhang_MAPS_molecules_2021);" (Table 1) [from (cite: zhang_MAPS_molecules_2021)]
- External data: Distance: 158.9 pc in text; 158±0.5 pc in Table 1  
  > "located at a distance of $158.9\,{\rm pc}$ (`Gaia` DR3; (cite: gaia_collaboration_gaia_2023))" (The Large Disk of IM Lup); "| distance | $D$ | 158$\pm$0.5 pc | \[2\] |" (Table 1) [from (cite: gaia_collaboration_gaia_2023)]
- External data: Extinction A_V = 0.7 mag  
  > "| extinction | $A_V$ | 0.7 mag | \[3\] |" (Table 1); "\[3\] (cite: gunther_disk-bearing_2010);" (Table 1) [from (cite: gunther_disk-bearing_2010)]
- External data: Mass accretion rate 1×10−8 M_sun yr−1  
  > "| mass accretion rate | $\dot{M}_\mathrm{acc}$ | $1\times 10^{-8}\,M_\odot\,\mathrm{yr^{-1}}$ | \[4\] |" (Table 1); "\[4\] (cite: alcala_x-shooter_2017);" (Table 1) [from (cite: alcala_x-shooter_2017)]
- External data: Dust radius containing 90% of flux: 264±1 AU  
  > "Its dust disk, measured as the radius containing 90% of the flux, is $R^{90}_{\rm mm} \sim 264\pm1\,{\rm AU}$ (cite: huang_disk_2018)." (The Large Disk of IM Lup) [from (cite: huang_disk_2018)]
- External data: 12CO gas radius containing 90% of flux: 481±6 AU  
  > "Its $\rm {}^{12}CO$ gas disk is nearly double the size of the dust disk $R^{90}_{\rm {}^{12}CO}\sim 481\pm6\,{\rm AU}$ (cite: law_IMLup_molecules_vertical_2021)." (The Large Disk of IM Lup) [from (cite: law_IMLup_molecules_vertical_2021)]
- External data: System age ~1 Myr  
  > "IM Lup (Sz 82) is a $\sim 1$ Myr-old star (cite: mawet_direct_2012)" (The Large Disk of IM Lup) [from (cite: mawet_direct_2012)]
- External data: BT-settl stellar photosphere spectrum, T_eff = 4300 K  
  > "a `BT-settl` stellar photosphere spectrum with $T_{\rm eff} = 4300\,{\rm K}$ (cite: Allard_2003IAUS..211..325A; Allard_2011ASPC..448...91A);" (Models and Main Results) [from (cite: Allard_2003IAUS..211..325A; Allard_2011ASPC..448...91A)]
- External data: DIANA standard dust opacities and composition  
  > "we use the DIANA standard opacities (cite: Woitke_diana_2016; min_multiwavelength_2016)," (Dust properties) [from (cite: Woitke_diana_2016; min_multiwavelength_2016)]
- External data: Amorphous silicate and amorphous carbon BE-sample optical materials  
  > "a mixture 60% of amorphous silicates ((cite: dorschner_steps_1995), ${\rm Mg_{0.7}Fe_{0.3}SiO_{3}}$) with 15% amorphous carbon ((cite: zubko_optical_1996), BE-sample), with 25% porosity, by volume." (Dust properties) [from (cite: dorschner_steps_1995); (cite: zubko_optical_1996)]
- External data: Dynamical gas-mass estimates for comparison  
  > "Considering the underlying uncertainties, this range of values agrees with dynamical-based estimates (cite: lodato_dynamical_mass_2023; martire_rotation_2024)" (Summary) [from (cite: lodato_dynamical_mass_2023; martire_rotation_2024)]
- External data: Earlier thermochemical gas-mass estimate ~2.0×10−3 M_sun and factor-100 homogeneous CO reduction  
  > "However, the $M_{\rm gas}$ inferred from thermochemical models matching CO isotopologue data is reported to be only $\sim 2.0\times10^{-3}\,M_\odot$ (cite: zhang_MAPS_molecules_2021)." (The Large Disk of IM Lup); "The authors can reconcile models with data if gas-phase CO is homogeneously reduced by a factor of 100 from their model output." (The Large Disk of IM Lup) [from (cite: zhang_MAPS_molecules_2021)]
- External data: Dust-mass comparisons: ~137 M_earth; 656 M_earth; ~639 M_earth  
  > "With these assumptions, the dust disk mass of IM Lup is $M_{\rm dust}\sim 137\,M_\oplus$ (cite: Manara2022DemographicsFormation) with the revised Gaia distance." (Uncertainties on the dust disk mass); "Using this approach, (cite: zhang_MAPS_molecules_2021) found $M_{\rm dust}= 1.97\times10^{-3}\,M_\odot = 656\,M_{\oplus}$," (Uncertainties on the dust disk mass); "They also adopted the DSHARP dust composition and inferred $M_{\rm dust}\sim 639\,M_{\oplus}$," (Uncertainties on the dust disk mass) [from (cite: Manara2022DemographicsFormation); (cite: zhang_MAPS_molecules_2021); (cite: sierra_molecules_2021)]
- External data: CO-isotopologue and N2H+ thermochemical gas-mass estimate for comparison  
  > "a new thermochemical model-based estimate using a combination of CO isotopologues and ${\rm N_2H^+}$ emission (cite: trapman_exoalma_2025)." (Summary) [from (cite: trapman_exoalma_2025)]
- External data: Streaming-instability threshold Z ~0.02 for alpha_v ~10−3  
  > "Therefore, the $Z \sim 0.02$ threshold inferred with $\alpha_{\rm v} \sim 10^{-3}$ (cite: li_thresholds_2021) is a good approximation for the IM Lup disk." (Dust-to-gas mass ratio and planetesimal formation) [from (cite: li_thresholds_2021)]
- External data: Literature turbulence constraints from CO rotation, dust settling, and midplane grains  
  > "(cite: flaherty_evidence_2024) found $0.03 \lesssim \alpha_{\rm v} \lesssim 0.08$ by modeling the rotation curves of CO isotopologues that emit at disk surface;" (Dust-to-gas mass ratio and planetesimal formation); "(cite: franceschi_IMLup_constraining_2022) found $2.1\times10^{-3} \lesssim \alpha_{\rm v} \lesssim 3.4\times10^{-3}$ by modeling the multi-wavelength observations regarding the dust vertical structure with settling;" (Dust-to-gas mass ratio and planetesimal formation); "(cite: jiang_grain-size_2024) found $\alpha_{\rm v} \sim 10^{-3}$ by modeling the grains in the pebble-settled midplane." (Dust-to-gas mass ratio and planetesimal formation) [from (cite: flaherty_evidence_2024); (cite: franceschi_IMLup_constraining_2022); (cite: jiang_grain-size_2024)]
- Simulation/model as data: BT-settl stellar photosphere spectrum with T_eff = 4300 K  
  > "a `BT-settl` stellar photosphere spectrum with $T_{\rm eff} = 4300\,{\rm K}$ (cite: Allard_2003IAUS..211..325A; Allard_2011ASPC..448...91A);" (Models and Main Results)
- Simulation/model as data: DIANA standard opacities  
  > "we use the DIANA standard opacities (cite: Woitke_diana_2016; min_multiwavelength_2016)," (Dust properties)
- Simulation/model as data: Full thermochemical models used to assess omitted gas cooling  
  > "this simplified approach yields a thermal profile relatively similar to the full model, particularly near the disk midplane," (Omission of gas cooling); "compared to the full model in (cite: Ruaud2022)." (Omission of gas cooling)

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
- image size: Synthetic images: field-of-view out to 20″  
  > "with a synthetic beam size of $0.15\ensuremath{''} \times 0.15\ensuremath{''}$ and field-of-view out to 20$''$." (dust-to-gas mass ratio)
- masking: _not stated_
- multiscale scales: _not stated_
- continuum subtraction: _not stated_
- line free channels: _not stated_
- primary beam correction: _not stated_
- array combination: _not stated_
- smoothing: _not stated_
- final beam: Synthetic images: 0.15″ × 0.15″  
  > "with a synthetic beam size of $0.15\ensuremath{''} \times 0.15\ensuremath{''}$ and field-of-view out to 20$''$." (dust-to-gas mass ratio)
- final rms: _not stated_

### Inherited from earlier work

- Well-mixed modeling and vertical hydrostatic equilibrium procedure  
  > "We start with a well-mixed model, following the same approach used on the disk around RU Lup as in (cite: Deng_2023_diskmint)." (Models and Main Results); "Following (cite: Deng_2023_diskmint), we run `DiskMINT` by solving for disk vertical hydrostatic equilibrium." (dust-to-gas mass ratio) [from (cite: Deng_2023_diskmint)]
- Reduced chemical network and ISM chemical abundances  
  > "it includes a reduced chemical network (cite: Ruaud2022)" (Models and Main Results); "we run the reduced chemical network using the ISM chemical abundances (cite: Ruaud2022; Deng_2023_diskmint) to determine the CO abundances." (Models and Main Results) [from (cite: Ruaud2022; Deng_2023_diskmint)]
- DIANA standard opacities and Bruggeman mixing rule  
  > "using the Bruggeman (cite: bruggeman_berechnung_1935) mixing rule," (Dust properties); "we use the DIANA standard opacities (cite: Woitke_diana_2016; min_multiwavelength_2016)," (Dust properties) [from (cite: bruggeman_berechnung_1935); (cite: Woitke_diana_2016; min_multiwavelength_2016)]
- 20 logarithmic grain-size bins; stated thermal-structure accuracy 5%  
  > "We divide the dust grains into 20 different size bins – which is sufficient to constrain the resulting thermal structure to an accuracy of $5\%$" (Dust properties); "(for details, see Section 2.1 in (cite: Deng_2023_diskmint))" (Dust properties) [from (cite: Deng_2023_diskmint), Section 2.1]
- Self-similar viscous surface-density distribution  
  > "This well-mixed model uses the surface density distribution that follows the similarity solutions of viscously evolving disks (cite: lynden-bell_evolution_1974; Hartmann1998):" (A self-similar surface density distribution) [from (cite: lynden-bell_evolution_1974; Hartmann1998)]
- Well-mixed characteristic radius 100 AU and surface-density slope 1.0  
  > "We adopt typical values for the characteristic radius of $r_{c} = 100\,\mathrm{AU}$ and $\gamma = 1.0$ as in previous thermochemical models" (A self-similar surface density distribution); "(cite: Miotello2014; Miotello2016; miotello_lupus_2017; Ruaud2022; trapman_exoalma_2025; Trapman_AGEPRO_V_gas_masses)." (A self-similar surface density distribution) [from (cite: Miotello2014; Miotello2016; miotello_lupus_2017; Ruaud2022; trapman_exoalma_2025; Trapman_AGEPRO_V_gas_masses)]
- Continuum inclination 47.5° from DSHARP  
  > "The SED is generated using `RADMC3D` with the disk inclination ($i = 47.5\ensuremath{^\circ}$) from ALMA continuum images by DSHARP (cite: huang_disk_2018)." (dust-to-gas mass ratio) [from (cite: huang_disk_2018)]
- LIME non-LTE line radiative transfer  
  > "Then we utilize `LIME` to conduct non-Local Thermal Equilibrium line radiative transfer as in (cite: Deng_2023_diskmint)" (dust-to-gas mass ratio) [from (cite: Deng_2023_diskmint)]
- MAPS synthetic imaging parameters and gas geometry  
  > "generate synthetic images using the same imaging parameters from MAPS data," (dust-to-gas mass ratio); "The adopted gas disk inclination ($i = 47.5\ensuremath{^\circ}$), position angles (${\rm PA} = 144.5\ensuremath{^\circ}$), and the systematic velocity ($v_{\rm sys} = 4.5 \,\mathrm{km\,s^{-1}}$) are also from MAPS CO isotopologue data (cite: zhang_MAPS_molecules_2021)." (dust-to-gas mass ratio) [from MAPS data; (cite: zhang_MAPS_molecules_2021)]
- Steady-state dust diffusion formulation; Schmidt number ~1  
  > "We consider the transport of dust particles by the turbulent fluctuations as a diffusion process in steady state (cite: dullemond_flaring_2004; fromang_n_Nelson_settling_2009):" (Vertical distribution: dust settling); "${\rm Sc}$ is the Schmidt number assumed to be $\sim 1$ (cite: fromang_n_Nelson_settling_2009)." (Vertical distribution: dust settling) [from (cite: dullemond_flaring_2004; fromang_n_Nelson_settling_2009)]
- Fragmentation threshold grain size  
  > "We consider the dust fragmentation by including the threshold grain size following (cite: birnstiel_simple_2012)," (Dust fragmentation) [from (cite: birnstiel_simple_2012)]
- Drift threshold grain-size estimate  
  > "The drift threshold size $a_{\rm drift}$ can also be estimated as (cite: birnstiel_simple_2012; birnstiel_dust_2024):" (Dust radial drifting) [from (cite: birnstiel_simple_2012; birnstiel_dust_2024)]
- Drift-velocity calibration f_d = 0.3  
  > "Here $f_{\rm d}$ is an order-of-unity constant introduced in (cite: birnstiel_simple_2012) and was taken to be $0.3$ according to the calibration to more comprehensive numerical simulations (cite: birnstiel_outer_2014)," (Indications of radial drift in the IM Lup disk) [from (cite: birnstiel_simple_2012); (cite: birnstiel_outer_2014)]

### Not stated but needed to reproduce (our reading)

- Exact observed continuum images, C18O cubes, product filenames, and versioned download locations.
- Photometric measurements, uncertainties, source citations for individual SED points, and multi-epoch averaging procedure.
- Observed-data calibration, self-calibration, continuum subtraction, spectral channelization, weighting, masks, and noise estimates.
- Annular widths, radial sampling, image centering, spectral integration limits, and radial-profile uncertainty calculation.
- Numerical a_max and q values: the supplied model-parameter tables do not retain them.
- Numerical model grid, radiative-transfer sampling, scattering treatment, and convergence tolerances.
- Chemical evolution time, initial abundance values, reaction-network configuration, and radiation or ionization inputs.
- LIME molecular data, collision rates, sampling, spectral resolution, and numerical convergence settings.
- Fit objective, data weighting, parameter search strategy, and statistical uncertainty procedure.
- Normalization and radial prescription for the small-grain component beyond the continuum edge.
- Resolution of the distance values 158.9 pc versus 158±0.5 pc and dust-edge values 300 AU versus 320 AU.

## Analysis recipe

1. **Set stellar illumination and dust opacities**: Use a three-component stellar spectrum and compute size-dependent wavelength-dependent dust opacities.  
  > "For all of the models, we adopt an input stellar spectrum with three components:" (Models and Main Results); "We use the `optool`[^3] (cite: dominik_optool_2021) package to compute the wavelength-dependent dust opacity using the Bruggeman (cite: bruggeman_berechnung_1935) mixing rule," (Dust properties)
   - software: optool
   - parameter: BT-settl 4300 K; blackbodies 8500 K and 1500 K, the latter at 0.055 AU  
  > "a `BT-settl` stellar photosphere spectrum with $T_{\rm eff} = 4300\,{\rm K}$ (cite: Allard_2003IAUS..211..325A; Allard_2011ASPC..448...91A);" (Models and Main Results); "a $8500\,{\rm K}$ blackbody radiation fitting the UV data-point in the SED; and a $1500\,{\rm K}$ blackbody radiation at $0.055\,{\rm AU}$ representing the accreting gas in the inner disk." (Models and Main Results)
   - parameter: a_min = 10−5 cm; fit a_max and q; 20 size bins  
  > "We fix $a_{\rm min} = 10^{-5}\,\mathrm{cm}$ and fit the SED to infer the $a_{\rm max}$ and $q$." (Dust properties); "We divide the dust grains into 20 different size bins" (Dust properties)
   - assumption: Power-law grain-size distribution n(a) ∝ a−q; DIANA composition: 60% amorphous silicates, 15% amorphous carbon, 25% porosity by volume  
  > "The dust number density follows a power-law distribution" (Dust properties); "a mixture 60% of amorphous silicates ((cite: dorschner_steps_1995), ${\rm Mg_{0.7}Fe_{0.3}SiO_{3}}$) with 15% amorphous carbon ((cite: zubko_optical_1996), BE-sample), with 25% porosity, by volume." (Dust properties)
   - fitting: Fit SED for a_max and q; fit UV point with 8500 K blackbody.  
  > "We fix $a_{\rm min} = 10^{-5}\,\mathrm{cm}$ and fit the SED to infer the $a_{\rm max}$ and $q$." (Dust properties); "a $8500\,{\rm K}$ blackbody radiation fitting the UV data-point in the SED;" (Models and Main Results)
   - validation: 20 size bins stated to constrain thermal structure to 5%, referring to earlier work.  
  > "We divide the dust grains into 20 different size bins – which is sufficient to constrain the resulting thermal structure to an accuracy of $5\%$" (Dust properties)
2. **Fit the well-mixed dust disk**: Solve vertical hydrostatic equilibrium and fit the SED at wavelengths ≳100 μm for dust mass and thermal structure.  
  > "Following (cite: Deng_2023_diskmint), we run `DiskMINT` by solving for disk vertical hydrostatic equilibrium." (dust-to-gas mass ratio); "We fit the long wavelengths ($\gtrsim 100\,{\rm\mu  m}$) SED to derive the dust disk mass ($M_{\rm dust}$) and thermal structure." (Models and Main Results)
   - software: DiskMINT, RADMC-3D
   - parameter: r_c = 100 AU; gamma = 1.0; r_in = 0.055 AU; r_out ~1000 AU  
  > "We adopt typical values for the characteristic radius of $r_{c} = 100\,\mathrm{AU}$ and $\gamma = 1.0$" (A self-similar surface density distribution); "We set the inner disk radius $r_{\rm in} = 0.055\,\mathrm{AU}$" (A self-similar surface density distribution); "We also adopt $r_{\rm out} \sim 1000\,\mathrm{AU}$ to ensure that all disk emission is included beyond $r_c$." (A self-similar surface density distribution)
   - parameter: Inclination 47.5°  
  > "The SED is generated using `RADMC3D` with the disk inclination ($i = 47.5\ensuremath{^\circ}$) from ALMA continuum images by DSHARP (cite: huang_disk_2018)." (dust-to-gas mass ratio)
   - assumption: Fixed gas-to-dust spatial coupling and constant dust-to-gas mass ratio  
  > "We first build a well-mixed model where the dust and gas have a fixed mass ratio all through the disk (at all $(r,z)$)" (Well-mixed model: Perfectly coupled gas and dust with a uniform dust-to-gas mass ratio)
   - assumption: Long-wavelength emission likely optically thin  
  > "where the disk emission is likely optically thin and a better indicator of dust mass." (dust-to-gas mass ratio)
   - fitting: SED fitting, mainly using ALMA mm-wavelength continuum flux densities for dust mass.  
  > "We estimate $M_{\rm dust}$ from the SED, mainly referring to the $\mathrm{mm}$-wavelength continuum flux densities from ALMA," (dust-to-gas mass ratio)
   - validation: Integrated emission fits; radial continuum and C18O distributions do not reproduce observations well.  
  > "the first well-mixed model reproduces the SED and the integrated $\rm C^{18}O$ luminosity," (Discussions and implications); "the radial distributions of neither the dust nor $\rm C^{18}O$ gas line emission of the well-mixed model well reproduce the observations" (Spatially Structured Model: decoupled gas and dust and fitting the radial profiles)
3. **Infer well-mixed gas mass**: Run chemistry for several constant dust-to-gas ratios; synthesize non-LTE C18O images and fit integrated luminosity.  
  > "we run `DiskMINT` with different constant $\varepsilon$ around the fiducial ISM value of $0.01$, including $\varepsilon = 0.02$, $0.01$, and $0.005$," (dust-to-gas mass ratio); "Then we utilize `LIME` to conduct non-Local Thermal Equilibrium line radiative transfer as in (cite: Deng_2023_diskmint)" (dust-to-gas mass ratio)
   - software: DiskMINT, LIME
   - parameter: epsilon = 0.02, 0.01, 0.005  
  > "including $\varepsilon = 0.02$, $0.01$, and $0.005$," (dust-to-gas mass ratio)
   - parameter: i = 47.5°; PA = 144.5°; v_sys = 4.5 km s−1  
  > "The adopted gas disk inclination ($i = 47.5\ensuremath{^\circ}$), position angles (${\rm PA} = 144.5\ensuremath{^\circ}$), and the systematic velocity ($v_{\rm sys} = 4.5 \,\mathrm{km\,s^{-1}}$) are also from MAPS CO isotopologue data (cite: zhang_MAPS_molecules_2021)." (dust-to-gas mass ratio)
   - assumption: ISM chemical abundances; isotope-selective photodissociation and CO/CO2 ice conversion  
  > "we run the reduced chemical network using the ISM chemical abundances (cite: Ruaud2022; Deng_2023_diskmint) to determine the CO abundances." (Models and Main Results); "has a detailed treatment of CO isotopologue chemistry, including isotope-selective photodissociation and grain-surface chemistry with ${\rm CO}$/${\rm CO_2}$ ice conversion." (Models and Main Results)
   - fitting: Compare synthetic C18O luminosity with observations to find best-fit epsilon.  
  > "Then we compare the synthetic $\rm C^{18}O$ luminosity with observations" (dust-to-gas mass ratio); "find the best-fit $\varepsilon=6.41\times10^{-3}$" (dust-to-gas mass ratio)
   - validation: Compare mass estimates with the structured model.  
  > "the models provide consistent $M_{\rm dust}$ and $M_{\rm gas}$ within a factor of a few." (Discussions and implications)
4. **Solve settled vertical structure**: Iterate dust radiative transfer, dust-gas thermal equilibrium, gas hydrostatic equilibrium, and steady-state dust diffusion.  
  > "we go through iterations including solving radiative transfer with `RADMC3D` to estimate $T_{\rm dust}(a)$, thermal equilibrium to estimate $T_{\rm gas}$, vertical hydrostatic equilibrium to estimate $\rho_{\rm gas}$, and the dust diffusive equation to estimate $\rho_{\rm dust}(a)$." (Vertical distribution: dust settling)
   - software: DiskMINT, RADMC-3D
   - parameter: Best-fit alpha_v = 10−3 from SED; test alpha_v = 10−4, 10−3, 10−2  
  > "we also find the best-fit value for the turbulent parameter $\alpha_{\rm v} = 10^{-3}$ based on the SED fitting" (Results for Structured Model); "apply dust settling with three different $\alpha_{\rm v} = 10^{-4}, 10^{-3}, 10^{-2}$," (Effect of dust settling)
   - assumption: Schmidt number ~1; vertically integrated grain-size distributions remain fixed at each radius  
  > "${\rm Sc}$ is the Schmidt number assumed to be $\sim 1$ (cite: fromang_n_Nelson_settling_2009)." (Vertical distribution: dust settling); "the overall dust size distribution at each radius and the vertically integrated (surface) densities for each size, $\Sigma_{\rm dust}(a, r)$ – are kept fixed." (Vertical distribution: dust settling)
   - assumption: Gas-phase heating and cooling omitted; gas temperature from thermal equilibrium with dust grains  
  > "Specifically, gas-phase heating and cooling mechanisms are omitted and $T_{\rm gas}$ is computed from the thermal equilibrium with dust grains of different sizes" (Omission of gas cooling)
   - fitting: Constrain turbulence from the infrared SED near 100 μm.  
  > "It is constrained from the infrared SED at $\sim 100\,{\rm\mu  m}$, and we use the best-fit $\alpha_{\rm v} \sim 10^{-3}$ from the structured model." (alpha_v)
   - validation: Settling models improve the ~100 μm SED; mass estimates are insensitive to tested alpha_v choices.  
  > "We find that the models with dust settling (green, red, and purple lines) match the SED better at $\lambda \sim 100\,{\rm\mu  m}$," (Effect of dust settling); "We also find that neither the $M_{\rm dust}$ nor $M_{\rm gas}$ estimates are sensitive to the choice of $\alpha_{\rm v}$," (Effect of dust settling)
5. **Recover dust surface density**: Extract continuum profiles in elliptical annuli; multiply each radial dust surface density by observed/model intensity and iterate from the well-mixed model.  
  > "We derive the continuum radial profile from the images using elliptical annuli, utilizing the inclination and position angles from the observation, and get the intensity per area for each annulus." (Step 1. Derive dust surface density); "\Sigma_{{\rm dust,model\,}i+1}(r) =  \Sigma_{{\rm dust,model\,}i}(r) R_{{\rm cont},i}(r)" (Step 1. Derive dust surface density)
   - software: DiskMINT
   - parameter: Typically three iterations for dust  
  > "It typically takes three iterations to find the converged best-fit $\Sigma_{\rm dust}(r)$ and five iterations for the converged best-fit $\Sigma_{\rm gas}(r)$," (Step 2. Derive gas surface density)
   - assumption: Dust emission optically thin in the majority of the outer disk  
  > "Because the dust thermal emission is expected to be optically thin in the majority of the outer disk," (Step 1. Derive dust surface density)
   - fitting: Iterative radial-profile matching using the observed/model continuum ratio.  
  > "We start from the image generated from the well-mixed model, and modify $\Sigma_{\rm dust}$ until it matches the observed continuum radial intensity profile." (Step 1. Derive dust surface density)
   - validation: Best-fit structured model matches the long-wavelength SED and continuum radial profile.  
  > "We find this structured model with the same dust size distribution (described by $a_{\rm max}$ and $q$) as the well-mixed model can also fit the slope of the SED at longer wavelengths" (Results for Structured Model); "the second structured model also matches the continuum emission profile and the $\rm C^{18}O$ radial profile." (Discussions and implications)
6. **Recover gas surface density**: Multiply each radial gas surface density by the observed/model C18O (2-1) profile ratio and iterate.  
  > "\Sigma_{{\rm gas,model\,}i+1}(r) =  \Sigma_{{\rm gas,model\,}i}(r) R_{{\rm \rm C^{18}O},i}(r)" (Step 2. Derive gas surface density); "where $R_{{\rm \rm C^{18}O},i}(r)$ is the ratio between the observation and the synthetic image from the model $i$ for $\rm C^{18}O$ line radial profile." (Step 2. Derive gas surface density)
   - software: DiskMINT, LIME
   - parameter: Typically five iterations for gas; profiles in Jy AU−2 and Jy m s−1 AU−2  
  > "It typically takes three iterations to find the converged best-fit $\Sigma_{\rm dust}(r)$ and five iterations for the converged best-fit $\Sigma_{\rm gas}(r)$," (Step 2. Derive gas surface density); "they are presented in the flux per unit area ($\mathrm{Jy\,AU^{-2}}$ and $\mathrm{Jy\,m\,s^{-1}\,AU^{-2}}$)," (Step 2. Derive gas surface density)
   - assumption: C18O emission optically thin and close to the disk midplane  
  > "we derive $\Sigma_{\rm gas}$ based on the radial profile of the $\rm C^{18}O$ line emission because it is optically thin and its emission layer is close to the disk midplane" (Step 2. Derive gas surface density)
   - fitting: Iteratively fit the C18O (2-1) radial profile from the well-mixed starting distribution.  
  > "We start from what is adopted in the well-mixed model" (Step 2. Derive gas surface density); "both $\Sigma_{\rm dust}(r)$ and $\Sigma_{\rm gas}(r)$ are set in iterations by fitting the dust continuum and $\rm C^{18}O\,(2-1)$ line radial profiles" (Step 2. Derive gas surface density)
   - validation: Compare the structured model with SED, continuum and C18O profiles, and C18O spectra.  
  > "The main results including the SED fitting, continuum and $\rm C^{18}O(2-1)$ radial profile, and the $\rm C^{18}O(2-1)$ line spectra for the structured model are presented" (Results for Structured Model)
7. **Validate with Band 3**: Predict 110 GHz continuum and C18O (1-0) emission from the Band 6 best-fit structured model.  
  > "Here we present the results of the ALMA Band 3 continuum at 110 GHz and $\rm C^{18}O\,(1-0)$ line emission for the structured model" (Band 3 analysis)
   - software: DiskMINT
   - fitting: Band 3 data excluded from fitting.  
  > "Note that the models are fit to the higher quality ALMA Band 6 data, without considering the poorer quality Band 3 information." (Band 3 analysis)
   - validation: Both longer-wavelength continuum and C18O (1-0) match within uncertainties.  
  > "Both the continuum and $\rm C^{18}O\,(1-0)$ line emission from the best-fit model match the these longer wavelength data within the uncertainties." (Band 3 analysis)
8. **Bound gas mass and compare methods**: Assess omitted gas cooling, inner optical depth and outer sensitivity; compare with dynamical and other gas-mass estimates.  
  > "Here, we discuss two main sources of uncertainty in our gas mass estimates: i) the omission of gas thermal processes in `DiskMINT` and ii) the limited observational constraints in the optically thick inner disk and the faint outer disk." (Gas masses constrained within a factor of a few); "Our $M_{\rm gas}$ estimates, obtained with an ISM CO abundance as input, are consistent with the dynamical mass estimate," (C18O: a reliable Mgas tracer with self-consistent models)
   - parameter: Optically thick inside ≲40 AU; direct sensitivity limits ~300 AU dust and ~400 AU C18O; model extends to 1000 AU  
  > "the dust and gas become optically thick inside $\lesssim 40\,{\rm AU}$," (The optically thick inner disk and faint outer disk); "In the outer disk, sensitivity sets a limit at $\sim 300\,{\rm AU}$ for dust and at $\sim 400\,{\rm AU}$ for $\rm C^{18}O$ gas," (The optically thick inner disk and faint outer disk); "the structured model grid extends out to $1,000\,{\rm AU}$." (The optically thick inner disk and faint outer disk)
   - assumption: A full thermochemical calculation expected to raise the inferred mass by at most ~2  
  > "a detailed thermo-chemical model is expected to yield a mass at most larger than a factor of $\sim2$ compared to `DiskMINT`," (Omission of gas cooling)
   - fitting: _not stated_
   - validation: Gas-mass estimates from different methods converge within a factor ≲2–3.  
  > "the $M_{\rm gas}$ estimates derived from different methods converge within a factor of $\lesssim 2-3$," (C18O: a reliable Mgas tracer with self-consistent models)
9. **Construct the dust-evolution test**: Fit structured-model gas surface density with a self-similar profile; apply fragmentation then drift to redistribute dust by grain size.  
  > "We fit the $\Sigma_{\rm gas}(r)$ profile that is derived to match the $\rm C^{18}O(2-1)$ radial emission between $40$ and $300\,{\rm AU}$," (Setup for the dust dynamics test); "We solve for fragmentation equilibrium first and then consider drift." (Setup for the dust dynamics test)
   - software: DiskMINT
   - parameter: gamma ~0.4; r_c ~300 AU; alpha_v ~10−3  
  > "find best-fit values of the parameters $\gamma \sim 0.4$ and $r_{c} \sim 300\,{\rm AU}$." (Setup for the dust dynamics test); "we use the best-fit $\alpha_{\rm v} \sim 10^{-3}$ from the structured model." (alpha_v)
   - parameter: r_drift = 300 AU; a_drift ~0.01 cm; u_frag = 750 cm s−1  
  > "we set $r_{\rm drift}$ to $300\,{\rm AU}$ ($\sim R_{\rm dust}$), and find $a_{\rm drift} \sim 0.01\,{\rm cm}$" (r_drift and a_drift); "we therefore adopt $u_{\rm frag} = 750\,{\rm cm\,s^{-1}}$ to reduce the mass in small grains that remain beyond $r_{\rm drift}$." (u_frag)
   - assumption: Fragmented mass redistributed to smaller grains at the same radius; grains above the drift threshold moved inside r_drift  
  > "This ensures that we retain and redistribute the mass in the fragmented grains at the same radius." (Dust fragmentation); "We move all the mass of large dust grains with $a \geq a_{\rm drift}$ inside $r_{\rm drift}$," (Dust radial drifting)
   - assumption: Initial constant epsilon; dust boundary assumed shaped by radial drift  
  > "Then, we initially assume an arbitrary constant $\varepsilon$ to obtain the original dust surface density" (Setup for the dust dynamics test); "Here we estimate the radial drift from the observations, by assuming that the dust disk boundary ($R_{\rm dust}$) is shaped by the radial drift barrier." (Dust radial drifting)
   - fitting: Vary total dust mass to match the mm-wavelength flux-density profile.  
  > "The shape of $\Sigma_{\rm dust}(r,a)$ is determined by solving fragmentation and drift, and we vary the total $M_{\rm dust}$ to match the mm-wavelength flux density profile." (Results for the test of dust dynamical effects)
   - validation: Dust continuum matches data; self-similar gas fit omits low-level structures and an outer mass enhancement.  
  > "The dust continuum emission from our test model can provide a good match to the data" (Results for the test of dust dynamical effects); "The lower total mass for this case is because we neglected structures by using a self-similar fit," (Results for the test of dust dynamical effects)
10. **Test whether radial drift is needed**: Compare fragmentation-only continuum profiles with fragmentation-plus-drift; estimate drifted mass and an age-based drift distance.  
  > "From our structured model, we estimate $\Sigma_{\rm gas}/c_s^2$ and vary $u_{\rm frag}$ and test the fragmentation-only scenario." (Indications of radial drift in the IM Lup disk); "We estimate the fraction of dust mass that needs to have drifted inside $r_{\rm drift}$ in our test model with dust dynamics." (Indications of radial drift in the IM Lup disk)
   - software: DiskMINT
   - parameter: Fragmentation-only tests: u_frag = 100, 500, 750 and 1000 cm s−1  
  > "four different values of $u_{\rm frag}=100, 500, 750\,{\rm and}\,1000\,{\rm cm\,s^{-1}}$" (Indications of radial drift in the IM Lup disk)
   - parameter: Age ~1 Myr; initial radius ~1000 AU; initial epsilon ~0.01; f_d = 0.3  
  > "the dust-to-gas mass ratio starts from the ISM value $\varepsilon \sim 0.01$, both the gas and dust are well-coupled with the initial radius of $R^{o} \sim 1000\,{\rm AU}$," (Indications of radial drift in the IM Lup disk); "the disk evolved for $\sim 1\,{\rm Myr}$," (Indications of radial drift in the IM Lup disk); "was taken to be $0.3$ according to the calibration to more comprehensive numerical simulations (cite: birnstiel_outer_2014)," (Indications of radial drift in the IM Lup disk)
   - assumption: Axisymmetric distribution; order-of-magnitude drift estimate  
  > "Note that this is an order-of-magnitude consistency estimate." (Indications of radial drift in the IM Lup disk); "IM Lup is observed to have spiral arms in the outer disk, while we have assumed an axisymmetric distribution," (Indications of radial drift in the IM Lup disk)
   - fitting: Fix drift radius to observed dust radius; fit epsilon and fragmentation velocity.  
  > "the dust drift radius was fixed to be the observationally constrained radius $R_{\rm dust}$, and fits to ALMA data provided values of $\epsilon=0.02$ and $u_{\rm frag}=750\,{\rm cm\,s^{-1}}$." (Indications of radial drift in the IM Lup disk)
   - validation: Fragmentation-only profiles cannot reproduce the sharp dust edge; drift models match it.  
  > "In this model without radial drift, the decrease of the millimeter-wavelength continuum radial profile is also shallower and cannot reproduce the observed sharp drop at $R_{\rm dust}$." (Indications of radial drift in the IM Lup disk); "We find that the mm-dust edge is well explained by considering radial drift," (Indications of radial drift in the IM Lup disk)
11. **Assess streaming-instability conditions**: Compare structured-model dust-to-gas ratio and midplane Stokes numbers with turbulence-dependent streaming-instability thresholds.  
  > "We plot the dust-to-gas mass ratio (metallicity) for the structured model" (Dust-to-gas mass ratio and planetesimal formation); "we also show Stokes number in the midplane for the large grains ($\sim 0.1\,{\rm cm}$) at the top axis." (Dust-to-gas mass ratio and planetesimal formation)
   - parameter: Large grains ~0.1 cm; reference SI threshold Z ~0.02 at alpha_v ~10−3  
  > "the large grains ($\sim 0.1\,{\rm cm}$)" (Dust-to-gas mass ratio and planetesimal formation); "Therefore, the $Z \sim 0.02$ threshold inferred with $\alpha_{\rm v} \sim 10^{-3}$ (cite: li_thresholds_2021) is a good approximation for the IM Lup disk." (Dust-to-gas mass ratio and planetesimal formation)
   - assumption: Dust-derived turbulence is relevant to midplane dust clumping.  
  > "we also mostly utilize the dust disk to constrain $\alpha_{\rm v}$ – and this should be most relevant to the dust clumping in the disk midplane." (Dust-to-gas mass ratio and planetesimal formation)
   - fitting: _not stated_
   - validation: Consider ratios within one pressure scale height and a factor-5 dust-opacity change; SI remains unlikely in their interpretation.  
  > "this ratio is higher if we consider only the region of the disk within one pressure scale height $1\,h$, and it could potentially be as high as 0.1 for a different choice of dust opacity" (Dust-to-gas mass ratio and planetesimal formation); "the derived metallicity is still likely small enough that SI may not be triggered for a disk with a moderate level of turbulence." (Dust-to-gas mass ratio and planetesimal formation)

## Software

- **DiskMINT** v1.5.0: Self-consistent thermochemical disk structures and models  
  > "`DiskMINT` computes self-consistent disk structures, iterating between density and temperature," (Models and Main Results); "The models in this work is created with `DiskMINT` (cite: Deng_2023_diskmint) v1.5.0" (Acknowledgments)
- **RADMC-3D / RADMC3D** : Radiative transfer, dust temperatures and synthetic SEDs  
  > "`DiskMINT` is an open-source tool built on `RADMC-3D` (cite: Dullemond_radmc-3d_2012) for radiative transfer," (Models and Main Results); "The SED is generated using `RADMC3D`" (dust-to-gas mass ratio)
- **radmc3dPy** : Basis for developing the authors' code  
  > "The authors thank C.P. Dullemond and A. Juhasz for their helpful assistance and suggestions in developing our code based on `RADMC-3D` and `radmc3dPy`." (Acknowledgments)
- **LIME** : Non-LTE line radiative transfer and synthetic images  
  > "Then we utilize `LIME` to conduct non-Local Thermal Equilibrium line radiative transfer as in (cite: Deng_2023_diskmint)" (dust-to-gas mass ratio); "Then, we utilize `LIME` [^2] (cite: BrichHogerheijde_LIME_2010) to generate synthetic images." (Models and Main Results)
- **optool / Optool** : Wavelength-dependent dust opacities  
  > "We use the `optool`[^3] (cite: dominik_optool_2021) package to compute the wavelength-dependent dust opacity" (Dust properties)
- **GoFish** : _not stated_
- **Astropy** : _not stated_
- **Scipy** : _not stated_
- **Python** : Language underlying the figure-generation package  
  > "All figures were generated with the `Python`-based package `MATPLOTLIB` (cite: Hunter2007)." (Acknowledgments)
- **MATPLOTLIB** : All figures  
  > "All figures were generated with the `Python`-based package `MATPLOTLIB` (cite: Hunter2007)." (Acknowledgments)
- **RAC2D** : Earlier literature thermochemical gas-mass estimate  
  > "The earliest and lowest $M_{\rm gas}$ value" (C18O: a reliable Mgas tracer with self-consistent models); "is from (cite: zhang_MAPS_molecules_2021) using `RAC2D` (cite: du_water_2014)." (C18O: a reliable Mgas tracer with self-consistent models)
- **DALI** : Literature models compared with this work  
  > "(cite: paneque-carreno_vertical_2025) and (cite: trapman_exoalma_2025) both used `DALI` (cite: bruderer_warm_2012; bruderer_survival_2013)," (C18O: a reliable Mgas tracer with self-consistent models)
- **BT-settl** : Input stellar photosphere spectrum  
  > "a `BT-settl` stellar photosphere spectrum with $T_{\rm eff} = 4300\,{\rm K}$" (Models and Main Results)
- **zenodo** : Frozen DiskMINT v1.5.0 release  
  > "v1.5.0 (frozen version released on `zenodo` (cite: Deng_2025_diskmint_zenodo_v1p5))" (Acknowledgments)
- **GitHub** : Public DiskMINT repository  
  > "it can also be downloaded from our public `GitHub` repository: <https://github.com/DingshanDeng/DiskMINT>." (Acknowledgments)

## Numeric results

| quantity | value | uncertainty | units | step | quote |
|---|---|---|---|---|---|
| Well-mixed dust mass | 2.5×10−4 | not stated | M_sun | 2 | we find $M_{\rm dust}= 2.5\times10^{-4}\,M_\odot = 83\,M_\oplus$. |
| Well-mixed dust mass | 83 | not stated | M_earth | 2 | we find $M_{\rm dust}= 2.5\times10^{-4}\,M_\odot = 83\,M_\oplus$. |
| Well-mixed dust-to-gas mass ratio | 6.41×10−3 | not stated | dimensionless | 3 | find the best-fit $\varepsilon=6.41\times10^{-3}$ |
| Well-mixed gas mass | 3.9×10−2 | not stated | M_sun | 3 | corresponding to $M_{\rm gas}= 3.9\times10^{-2}\,M_\odot$. |
| Structured dust mass | 4.0×10−4 | not stated | M_sun | 5 | with the best-fit $M_{\rm dust}= 4.0\times 10^{-4}\,M_\odot = 133\,M_\oplus$ and $M_{\rm gas}=2.8\times 10^{-2}\,M_\odot$. |
| Structured dust mass | 133 | not stated | M_earth | 5 | with the best-fit $M_{\rm dust}= 4.0\times 10^{-4}\,M_\odot = 133\,M_\oplus$ and $M_{\rm gas}=2.8\times 10^{-2}\,M_\odot$. |
| Structured gas mass | 2.8×10−2 | not stated | M_sun | 6 | with the best-fit $M_{\rm dust}= 4.0\times 10^{-4}\,M_\odot = 133\,M_\oplus$ and $M_{\rm gas}=2.8\times 10^{-2}\,M_\odot$. |
| Structured turbulence parameter | 10−3 | not stated | dimensionless | 4 | we also find the best-fit value for the turbulent parameter $\alpha_{\rm v} = 10^{-3}$ based on the SED fitting |
| Gas mass including discussed systematic bounds | 0.02-0.08 | not stated | M_sun | 8 | We find $M_{\rm gas}\sim 0.02-0.08\,M_\odot$ for the IM Lup disk. |
| Structured gas mass inside the optically thick inner region | ~2.7×10−3 | not stated | M_sun | 8 | in the structured model, the integrated mass in this optically thick region is $\sim 2.7\times10^{-3}\,M_{\odot}$, $< 10\%$ of the total gas mass. |
| Gas-mass fraction at ~400-1000 AU | approximately 25% | not stated | dimensionless | 8 | The mass from $\sim400-1000\,{\rm AU}$ (which consists of approximately 25% of the total $M_{\rm gas}$) is therefore a little uncertain. |
| Dust-mass range across models | 83 - 153 | not stated | M_earth | 9 | In this work, we find the following range $M_{\rm dust}\sim 83 - 153\,M_\oplus$, |
| Modeled optical depth beyond r ≳50 AU | ≲0.01 | not stated | dimensionless | 5 | our detailed modeling finds an optical depth $\tau \lesssim 0.01$ beyond $r \gtrsim 50\,{\rm AU}$. |
| Self-similar gas-profile slope in dust-evolution test | ~0.4 | not stated | dimensionless | 9 | find best-fit values of the parameters $\gamma \sim 0.4$ and $r_{c} \sim 300\,{\rm AU}$. |
| Self-similar characteristic radius in dust-evolution test | ~300 | not stated | AU | 9 | find best-fit values of the parameters $\gamma \sim 0.4$ and $r_{c} \sim 300\,{\rm AU}$. |
| Dust-evolution test dust mass | 4.6×10−4 | not stated | M_sun | 9 | We find the best-fit is $M_{\rm dust}= 4.6\times 10^{-4}\,M_\odot = 153\,M_\oplus$. |
| Dust-evolution test dust mass | 153 | not stated | M_earth | 9 | We find the best-fit is $M_{\rm dust}= 4.6\times 10^{-4}\,M_\odot = 153\,M_\oplus$. |
| Dust-evolution test gas mass in the stated radial range | ~2.3×10−2 | not stated | M_sun | 9 | we obtain a similar estimate of $M_{\rm gas}\sim 2.3\times10^{-2}\,M_\odot$ in that radius range. |
| Fitted dust-evolution epsilon | 0.02 | not stated | dimensionless | 10 | fits to ALMA data provided values of $\epsilon=0.02$ and $u_{\rm frag}=750\,{\rm cm\,s^{-1}}$. |
| Fitted fragmentation velocity | 750 | not stated | cm s−1 | 10 | fits to ALMA data provided values of $\epsilon=0.02$ and $u_{\rm frag}=750\,{\rm cm\,s^{-1}}$. |
| Estimated inward-drifted dust mass | ~9 | not stated | M_earth | 10 | suggesting that $\sim 8\%$ of the mass ($\sim 9 M_\oplus$) that is currently inside could have drifted from outside of $r_{\rm drift}$. |
| Estimated inward-drifted fraction of current inner dust mass | ~8% | not stated | dimensionless | 10 | suggesting that $\sim 8\%$ of the mass ($\sim 9 M_\oplus$) that is currently inside could have drifted from outside of $r_{\rm drift}$. |
| Order-of-magnitude drift distance | ~625 | not stated | AU | 10 | gives $\Delta R_{dr}\sim 625\,{\rm AU}$. |
| Order-of-magnitude dust outer edge after 1 Myr | ~375 | not stated | AU | 10 | This would result in an approximate dust disk outer edge at $R^{1\,{\rm Myr}} \sim R^{o} - \Delta R_{\rm drift} \sim 375\,{\rm AU}$, |
| Dust-to-gas mass ratio between ~40-300 AU | ~0.02 | not stated | dimensionless | 11 | For the specific case of IM Lup, we find a dust-to-gas mass ratio of $\sim 0.02$ between $\sim 40 -300\,{\rm AU}$ |
| Radial variation of outer dust-to-gas mass ratio | factor of ≲2 | not stated | dimensionless | 11 | nearly constant with small variations within a factor of $\lesssim 2$. |
| Gas-mass range in settling sensitivity tests | 0.025 - 0.056 | not stated | M_sun | 4 | We find the best-fit $\varepsilon = 0.007-0.016$ with $M_{\rm gas}= 0.025 - 0.056\,M_\odot$, |

## Qualitative findings

- Self-consistent models reproduce gas masses consistent with dynamical estimates without global CO depletion.  
  > "the gas mass of IM Lup is consistent with the dynamical mass within the described uncertainties – without requiring global CO depletion" (Summary)
- Spatially decoupled dust and gas are needed to reproduce resolved radial profiles.  
  > "the radial distributions of neither the dust nor $\rm C^{18}O$ gas line emission of the well-mixed model well reproduce the observations" (Spatially Structured Model: decoupled gas and dust and fitting the radial profiles); "the second structured model also matches the continuum emission profile and the $\rm C^{18}O$ radial profile." (Discussions and implications)
- The sharp outer mm-continuum decline is most likely shaped by radial drift.  
  > "the fast decline of the mm continuum emission beyond $\sim 250$ AU is most likely shaped by drift." (Summary)
- Modeling does not provide support for streaming-instability conditions.  
  > "Therefore, our modeling results for IM Lup do not provide support for SI condition." (Dust-to-gas mass ratio and planetesimal formation)
- Dust opacity is the primary uncertainty in dust mass.  
  > "uncertainties in dust properties that determine the opacity are the primary source of uncertainty." (Uncertainties on the dust disk mass)

## Claim tuples

- H: C18O alone can recover IM Lup gas mass without homogeneous CO depletion. | E: Fit self-consistent dust and C18O models and compare gas masses with dynamical estimates. | R: M_gas ~0.02-0.08 M_sun. | F: C18O is a reliable gas-mass tracer within the stated self-consistent framework and uncertainties. | **supported**
- H: Spatially decoupled dust and gas distributions improve the resolved-data fit. | E: Iteratively fit separate continuum and C18O radial profiles with settled vertical structure. | R: Structured model gives M_dust = 4.0×10−4 M_sun and M_gas = 2.8×10−2 M_sun. | F: The structured model reproduces radial profiles that the well-mixed model does not. | **supported**
- H: Fragmentation alone explains the sharp mm-dust edge. | E: Test fragmentation-only profiles over four fragmentation velocities and compare with drift models. | R: Fragmentation-only profiles are too shallow and leave excessive outer mm emission. | F: Fragmentation alone is insufficient in the tested models; radial drift is favored. | **refuted**
- H: The inferred disk conditions establish that streaming instability can operate. | E: Compare radial dust-to-gas ratios and Stokes numbers with turbulence-dependent SI conditions. | R: Dust-to-gas ratio ~0.02 over ~40-300 AU, with modest radial variations. | F: The models do not support SI conditions; the conclusion remains sensitive to dust opacity and turbulence. | **refuted**
- H: The Band 6 best-fit model predicts longer-wavelength emission without refitting. | E: Compare synthetic Band 3 continuum and C18O (1-0) with data excluded from fitting. | R: Both observables match within uncertainties. | F: The independent wavelength comparison supports the modeled CO snowline. | **supported**

## Reasoning

- Why this data: IM Lup combines a young age, large radial extent, inferred CO abundance anomaly, and resolved dust and gas observations.  
  > "The young age, large radial extent, and large inferred CO abundance anomaly make the disk around IM Lup an interesting target to attempt to model in a self-consistent fashion." (The Large Disk of IM Lup); "IM Lup has high angular resolution ALMA observations on both dust continuum and $\rm C^{18}O$ line emission, which enables us to radially resolve its dust and gas line emission." (Spatially Structured Model: decoupled gas and dust and fitting the radial profiles)
- Why this method: Use self-consistent structure and CO chemistry; prioritize optically thin long-wavelength dust emission and C18O near the midplane.  
  > "`DiskMINT` computes self-consistent disk structures, iterating between density and temperature, and has a detailed treatment of CO isotopologue chemistry, including isotope-selective photodissociation and grain-surface chemistry with ${\rm CO}$/${\rm CO_2}$ ice conversion." (Models and Main Results); "where the disk emission is likely optically thin and a better indicator of dust mass." (dust-to-gas mass ratio); "because it is optically thin and its emission layer is close to the disk midplane" (Step 2. Derive gas surface density)
- Alternative: Well-mixed gas and dust: adequate for integrated quantities but inadequate for resolved profiles.  
  > "the first well-mixed model reproduces the SED and the integrated $\rm C^{18}O$ luminosity," (Discussions and implications); "the radial distributions of neither the dust nor $\rm C^{18}O$ gas line emission of the well-mixed model well reproduce the observations" (Spatially Structured Model: decoupled gas and dust and fitting the radial profiles)
- Alternative: Standard particle-scale-height prescriptions rejected because they assume vertical isothermality.  
  > "We do not adopt the standard approach of calculating particle scale height (cite: dubrulle_dust_settling_1995; Estrada_2016_particle_distribution) as these expressions implicitly assume a vertically isothermal temperature profile." (Vertical distribution: dust settling)
- Alternative: Fragmentation alone does not reproduce the sharp outer continuum edge.  
  > "the difference in dust and gas disk radii of the IM Lup disk is not easily explained with a dust evolution model that includes only fragmentation." (Indications of radial drift in the IM Lup disk)
- Alternative: DSHARP instead of DIANA dust opacity could increase inferred dust mass by ~5.  
  > "If the dust in the IM Lup disk has been processed to the extent that it resembles meteoritic compositions, which the DSHARP values are based on, then our dust mass estimates could be underestimated by a factor of $\sim 5$." (Uncertainties on the dust disk mass)
- Alternative: 12CO and 13CO could constrain farther-out gas, but require more detailed thermal and kinematic modeling.  
  > "more detailed models are needed to properly infer $\Sigma_{\rm gas}(r)$ from those two tracers in the outer disk," (The optically thick inner disk and faint outer disk)
- How they decided it was enough: Iterate to converged radial profiles; typically three dust and five gas iterations; validate against unfitted Band 3 data.  
  > "It typically takes three iterations to find the converged best-fit $\Sigma_{\rm dust}(r)$ and five iterations for the converged best-fit $\Sigma_{\rm gas}(r)$," (Step 2. Derive gas surface density); "Both the continuum and $\rm C^{18}O\,(1-0)$ line emission from the best-fit model match the these longer wavelength data within the uncertainties." (Band 3 analysis)
- Limitation (authors): Gas-phase heating and cooling omitted; gas masses may be underestimated by up to ~2.  
  > "Specifically, gas-phase heating and cooling mechanisms are omitted" (Omission of gas cooling); "a detailed thermo-chemical model is expected to yield a mass at most larger than a factor of $\sim2$ compared to `DiskMINT`," (Omission of gas cooling)
- Limitation (authors): Inside ≲40 AU, optical thickness makes surface densities lower limits.  
  > "the dust and gas become optically thick inside $\lesssim 40\,{\rm AU}$, hence what we derive within is a lower limit to the surface density." (The optically thick inner disk and faint outer disk)
- Limitation (authors): No direct constraints beyond ~300 AU for dust and ~400 AU for C18O.  
  > "In the outer disk, sensitivity sets a limit at $\sim 300\,{\rm AU}$ for dust and at $\sim 400\,{\rm AU}$ for $\rm C^{18}O$ gas, thus we have no direct observational constraints at larger radii." (The optically thick inner disk and faint outer disk)
- Limitation (authors): Dust composition can shift mass by ~5; omitted ice-mantle opacity effects could increase dust mass by ~20%.  
  > "our dust mass estimates could be underestimated by a factor of $\sim 5$." (Uncertainties on the dust disk mass); "we also ignore the effects of ice mantles in the midplane on dust opacities in the radiative transfer, although these effects are included in the chemistry." (Uncertainties on the dust disk mass); "This would lower the opacities and increase our dust mass estimates by $\sim 20$% as well." (Uncertainties on the dust disk mass)
- Limitation (authors): Axisymmetry neglects observed spiral arms; simple drift calculation is only an order-of-magnitude consistency estimate.  
  > "Note that this is an order-of-magnitude consistency estimate." (Indications of radial drift in the IM Lup disk); "IM Lup is observed to have spiral arms in the outer disk, while we have assumed an axisymmetric distribution," (Indications of radial drift in the IM Lup disk)
- Limitation (authors): The dust-dynamics test smooths away low-level structures and is not an independent surface-density inference.  
  > "is not a separate attempt or approach to infer the surface densities." (Placing the derived gas and dust surface densities in the context of dust dynamical evolution); "with the smoother slope for both $\Sigma_{\rm gas}(r)$ and $\Sigma_{\rm dust}(r)$ compared to those in the structured model, the low-level structures are ignored" (Results for the test of dust dynamical effects)
- Caveat (inferred, ours): The paper does not give a formal likelihood or posterior uncertainty analysis; the gas-mass interval is a systematic assessment.
- Caveat (inferred, ours): Integrated-mass agreement does not establish unique radial surface densities.
- Caveat (inferred, ours): The drift test fixes the drift radius to the observed edge, so it establishes consistency rather than an independent prediction of that edge.
- Caveat (inferred, ours): The SI conclusion depends strongly on adopted opacity, settling, turbulence and the applicable threshold.
- Caveat (inferred, ours): The supplied parameter tables lose a_max and q, preventing exact reconstruction from this text.
- Caveat (inferred, ours): Distance and dust-edge values differ across sections and need reconciliation.

## Reproducibility

- Data public (paper): _not stated_
- Products in archive: _not stated_
- Code: DiskMINT v1.5.0 frozen on Zenodo; DOI 10.5281/zenodo.17042059  
  > "v1.5.0 (frozen version released on `zenodo` (cite: Deng_2025_diskmint_zenodo_v1p5))" (Acknowledgments); "v1.5.0 Zenodo, doi: [`10.5281/zenodo.17042059`](http://doi.org/10.5281/zenodo.17042059)" (References)
- Code: https://github.com/DingshanDeng/DiskMINT  
  > "it can also be downloaded from our public `GitHub` repository: <https://github.com/DingshanDeng/DiskMINT>." (Acknowledgments)
- Missing: Exact observed image/cube products and radial-profile tables with uncertainties.
- Missing: Complete SED photometry with provenance and averaging details.
- Missing: Intact numerical model-parameter tables, particularly a_max and q.
- Missing: Paper-specific model input files, final radial surface-density arrays, and outer small-grain prescription.
- Missing: Chemical-network and radiative-transfer numerical settings inherited from earlier work.
- Missing: Fit statistic, search procedure, stopping criteria and uncertainty calculation.
- Missing: Explicit ALMA data-publicity statement and archive-product inventory.
- Data volume (inferred): Cannot estimate from the supplied text: product dimensions, channel counts and visibility sizes are absent.
- Score (inferred): 5/5, Versioned public modeling code, project codes, an explicit iterative recipe and numeric results are provided, but essential observed products, numerical inputs and fit settings are missing.
- Rediscovery candidate: no, The supplied text does not establish public availability of the ALMA products, and the recipe lacks inputs needed for exact reproduction despite numeric main results.

## Links

- Method: (cite: Deng_2023_diskmint) (Original DiskMINT framework, well-mixed procedure, hydrostatic solution, grain binning and non-LTE synthesis.)
- Method: (cite: Ruaud2022) (Reduced chemistry, ISM abundances, self-consistent thermochemistry and full-model comparison.)
- Method: (cite: Dullemond_radmc-3d_2012) (RADMC-3D radiative transfer.)
- Method: (cite: BrichHogerheijde_LIME_2010) (LIME line radiative transfer.)
- Method: (cite: dominik_optool_2021) (Dust-opacity calculation.)
- Method: (cite: Woitke_diana_2016; min_multiwavelength_2016) (DIANA dust composition and opacities.)
- Method: (cite: bruggeman_berechnung_1935) (Dust-material mixing rule.)
- Method: (cite: lynden-bell_evolution_1974; Hartmann1998) (Self-similar viscous surface-density prescription.)
- Method: (cite: dullemond_flaring_2004; fromang_n_Nelson_settling_2009) (Steady-state dust diffusion and settling.)
- Method: (cite: birnstiel_simple_2012; birnstiel_dust_2024) (Fragmentation and radial-drift grain-size thresholds.)
- Method: (cite: birnstiel_outer_2014) (Drift-velocity calibration.)
- Method: (cite: li_thresholds_2021) (Streaming-instability threshold comparison.)
- Companion: (cite: Deng_2023_diskmint) (Earlier DiskMINT application to RU Lup and inherited model details.)
- Companion: (cite: Deng_2025_diskmint_zenodo_v1p5) (Frozen code release used for the models.)
- Companion: (cite: huang_disk_2018) (DSHARP continuum constraints.)
- Companion: (cite: zhang_MAPS_molecules_2021) (MAPS CO constraints, adopted geometry and earlier thermochemical comparison.)
- Companion: (cite: Deng_2025_AGEPRO_III_Lupus) (Related application of self-consistent gas-mass modeling to AGE-PRO Lupus disks.)
- Related: DSHARP
- Related: MAPS
- Related: ALMA AGE-PRO

## Checks

```json
{
 "quotes": 261,
 "quotes_ok": 261,
 "quote_pass_rate": 1.0,
 "quotes_too_long": 0,
 "unsupported_facts": 0,
 "project_codes": 2,
 "codes_not_in_text": [],
 "codes_not_in_obscore": [],
 "obscore_codes_not_in_card": [],
 "codes_printed_but_missing": [],
 "numeric_results": 27,
 "numeric_problems": 0,
 "fill": {
  "facts": 174,
  "stated": 136,
  "rate": 0.782
 },
 "evidence_ok": true
}
```
