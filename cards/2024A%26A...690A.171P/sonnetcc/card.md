# No evidence of active galactic nucleus features in the nuclei of Arp 220 from JWST/NIRSpec IFS

`2024A&A...690A.171P` | Astronomy and Astrophysics 2024 | first author: Perna, Michele | arXiv: 2403.13948 | DOI: 10.1051/0004-6361/202450094

Card schema 1.0 | model claude-sonnet-5-5-claude-code | depth light | type multi_facility_alma_minor

## Science

- Fields: nearby_galaxies, agn_and_quasars
- Question: Do the two nuclei of Arp 220 show AGN signatures (high-ionisation lines, outflow kinematics) in JWST/NIRSpec IFS spectra of 55 pc apertures?  
  > "The primary goal is to investigate the potential presence of AGN signatures in the nuclear regions by analysing the spectra extracted from circular apertures of radius 55 pc" (abstract)
- Target **Arp 220 (W nucleus, E nucleus, NE cluster)**: coordinates W: 15:34:57.224 +23:30:11.515; E: 15:34:57.294 +23:30:11.353; NE cluster: 15:34:57.309 +23:30:11.698 (J2000)  
  > "with a distance of $\sim 78$ Mpc and log $L_{IR}/L_\odot$ = 12.2 (e.g. (cite: Pereira2021))" (Introduction); "With this cosmology, $1''$ corresponds to a distance of 0.368 kpc at $z=0.018$." (Introduction); "RA (J2000) | 15:34:57.224 | 15:34:57.294 | 15:34:57.309" (Spectral extraction); "DEC (J2000) | +23:30:11.515 | +23:30:11.353 | +23:30:11.698" (Spectral extraction); z/distance ~78 Mpc; z_W = 0.01774, z_E = 0.01839, z_NE = 0.01870 (from H I line centroids)  
  > "with a distance of $\sim 78$ Mpc and log $L_{IR}/L_\odot$ = 12.2 (e.g. (cite: Pereira2021))" (Introduction); "With this cosmology, $1''$ corresponds to a distance of 0.368 kpc at $z=0.018$." (Introduction); "RA (J2000) | 15:34:57.224 | 15:34:57.294 | 15:34:57.309" (Spectral extraction); "DEC (J2000) | +23:30:11.515 | +23:30:11.353 | +23:30:11.698" (Spectral extraction); distance from (e.g. (cite: Pereira2021)); redshifts measured from NIRSpec hydrogen lines  
  > "with a distance of $\sim 78$ Mpc and log $L_{IR}/L_\odot$ = 12.2 (e.g. (cite: Pereira2021))" (Introduction); "With this cosmology, $1''$ corresponds to a distance of 0.368 kpc at $z=0.018$." (Introduction); "RA (J2000) | 15:34:57.224 | 15:34:57.294 | 15:34:57.309" (Spectral extraction); "DEC (J2000) | +23:30:11.515 | +23:30:11.353 | +23:30:11.698" (Spectral extraction)
- Target **VV114 (comparison source)**: coordinates _not stated_; z/distance _not stated_; distance from _not stated_

## Data provenance

- ALMA projects: 2017.1.00042.S
- bands: ALMA 2.6 mm and 1.3 mm continuum maps (used only for absolute astrometry); JWST NIRSpec G140H/F100LP, G235H/F170LP, G395H/F290LP  
  > "The absolute astrometric registration is performed using the ALMA 0.1$''$  resolution maps of continuum emission at 2.6 mm presented by (cite: Scoville2017), and the 0.03$''$  resolution map of 1.3 mm continuum (project 2017.1.00042.S)." (Astrometric registration); "corresponding to the grating settings G140H/F100LP (referred to as band1 hereinafter), G235H/F170LP (band2), and G395H/F290LP (band3)" (Data reduction)
- frequencies and spectral setup: JWST NIRSpec IFS, three high-resolution (R ~ 2700) gratings covering 0.95-5.1 um; ALMA spectral setup not stated  
  > "in each of the three high resolution (R $\sim 2700$) grating settings, to cover the spectral range from 0.95 to 5.1 $\mu$m." (Observations and data reduction)
- continuum bandwidth: _not stated_
- arrays: _not stated_
- configurations: _not stated_
- baselines: _not stated_
- angular resolution: ALMA: 0.1'' (2.6 mm), 0.03'' (1.3 mm); JWST NIRSpec FWHM ~0.15'' at 5 um  
  > "The absolute astrometric registration is performed using the ALMA 0.1$''$  resolution maps of continuum emission at 2.6 mm presented by (cite: Scoville2017), and the 0.03$''$  resolution map of 1.3 mm continuum (project 2017.1.00042.S)." (Astrometric registration); "This aperture size broadly corresponds to two NIRSpec spatial resolution elements at 5 $\mu$m (FWHM $\sim 0.15\ensuremath{''}$; (cite: DEugenio2023))" (Spectral extraction)
- max recoverable scale: _not stated_
- sensitivity: _not stated_
- time on source: JWST: 933 s per set in each grating (two sets of four-point dithers)  
  > "The total integration time is 933 seconds per set, in each of the three high resolution (R $\sim 2700$) grating settings" (Observations and data reduction)
- observing dates: JWST/NIRSpec: 6 March 2023  
  > "The observations were collected on 6 March 2023, using the NIRSpec IFS mode" (Observations and data reduction)
- pi or archival as stated: JWST programme 1267 (PI: D. Dicken); also described as part of the NIRSpec IFS GTO survey (lead T. Boker)  
  > "Arp 220 was observed in NIRSpec IFS mode as part of the programme 1267 (PI: D. Dicken)." (Observations and data reduction)
- Other facility **JWST/NIRSpec IFS**: Primary data: 0.95-5.1 um IFS cubes of Arp 220 nuclei (programme 1267)  
  > "Arp 220 was observed in NIRSpec IFS mode as part of the programme 1267 (PI: D. Dicken)." (Observations and data reduction)
- Other facility **JWST/NIRSpec IFS, VV114**: Comparison NIRSpec cubes of the LIRG VV114 (programme 1328), reduced the same way  
  > "They were reduced following the same procedure reported above." (Data reduction)
- Other facility **Swift/BAT BASS sample**: Comparison sample of hard X-ray selected AGN for the [Si VI] luminosity plots  
  > "selected in the hard X-ray band (14-195 keV) from the *Swift*/Burst Alert Telescope (BAT) survey, as part of the BASS sample" (Absence of high-ionisation lines)
- External data: ALMA 2.6 mm continuum maps at 0.1'' resolution used for absolute astrometry  
  > "continuum emission at 2.6 mm presented by (cite: Scoville2017)" (Astrometric registration) [from (cite: Scoville2017)]
- External data: Sub-mm/mm molecular-line redshifts of the W and E nuclei (z_W ~ 0.01768, z_E ~ 0.01808) for comparison  
  > "as reported in (cite: Sakamoto2021b), $z_W \sim 0.01768$ and $z_E \sim 0.01808$" (Systemic redshift of the two nuclei) [from (cite: Sakamoto2021b)]
- External data: Radio and far-IR SFRs of the nuclei  
  > "Radio and far-IR based SFR measurements come from (cite: Varenius2016) and (cite: Pereira2021), respectively." (Spectral extraction) [from (cite: Varenius2016); (cite: Pereira2021)]
- External data: Intrinsic 2-10 keV luminosity upper limits for the nuclei  
  > "computed by (cite: Paggi2017) from the $3\sigma$ upper limits on the neutral Fe–K$\alpha$ line." (Absence of high-ionisation lines) [from (cite: Paggi2017)]
- External data: BASS sample [Si VI] and X-ray luminosities for nearby AGN  
  > "as part of the BASS sample ((cite: Koss2017; Ricci2017))" (Absence of high-ionisation lines) [from (cite: Koss2017; Ricci2017)]
- Simulation/model as data: MARCS synthetic stellar spectra used as pPXF templates  
  > "We used the MARCS synthetic library of stellar spectra to model the stellar continuum ((cite: Gustafsson2008))" (Modelling of the continuum emission)

## Processing

### Calibration

- pipeline or manual: STScI JWST pipeline with a patch for known bugs (JWST data); ALMA calibration not stated  
  > "A patch was included to correct some important bugs that affect this specific version of the pipeline (cite: Perna2023a)." (Data reduction)
- casa version: _not stated_
- pipeline version: STScI pipeline v1.8.2, CRDS context 1063 (JWST)  
  > "We used the STScI pipeline v1.8.2 with CRDS context 1063." (Data reduction)
- archive products used as is: _not stated_
- flux calibrator: _not stated_
- flux scale uncertainty: _not stated_
- self calibration: _not stated_

### Imaging

- task: _not stated_
- deconvolver: _not stated_
- weighting robust: _not stated_
- uv taper: _not stated_
- cell size: JWST cube spaxel 0.05'' (~20 pc)  
  > "resulting in cube spaxels with a size of 0.05$''$ (corresponding to $\sim 20$ pc per spaxel)" (Data reduction)
- image size: _not stated_
- masking: _not stated_
- multiscale scales: _not stated_
- continuum subtraction: _not stated_
- line free channels: _not stated_
- primary beam correction: _not stated_
- array combination: _not stated_
- smoothing: _not stated_
- final beam: _not stated_
- final rms: _not stated_

### Inherited from earlier work

- JWST pipeline bug patch (incl. 1/f noise correction)  
  > "A patch was included to correct some important bugs that affect this specific version of the pipeline (cite: Perna2023a)." (Data reduction) [from (cite: Perna2023a)]
- Outlier rejection scheme  
  > "We also implemented the outlier rejection of (cite: DEugenio2023)." (Data reduction) [from (cite: DEugenio2023)]
- Wiggle correction methodology, adapted to the Arp 220 dataset  
  > "we applied the methodology presented in (cite: Perna2023a), and adapted to the Arp 220 dataset as reported in (cite: Uliviinprep)" (Data reduction) [from (cite: Perna2023a); (cite: Uliviinprep)]
- Pa-alpha SFR calibration  
  > "We derived the instantaneous ($\sim 10$ Myr) SFR from the Pa$\alpha$ dust corrected luminosity, following (cite: Gimenez2022):" (Star-formation tracers) [from (cite: Gimenez2022)]
- 3.3 um PAH luminosity to L(IR) calibration  
  > "We also use the calibration of SFR for the 3.3 $\mu$m PAH from (cite: Kim2012)" (Star-formation tracers) [from (cite: Kim2012)]
- Extinction law used for E(B-V) coefficients  
  > "were derived assuming a (cite: Cardelli1989) extinction law." (Extinction) [from (cite: Cardelli1989)]

### Not stated but needed to reproduce (our reading)

- ALMA calibration, imaging and measurement details for 2017.1.00042.S 1.3 mm map used for astrometry (only the project code and resolution are given)
- How the nuclear positions were measured in the ALMA maps and in the NIRSpec 5.1-5.12 um image (centroiding method, uncertainty)
- Where the JWST programme 1267 data are retrieved (MAST identifiers, observation numbers) and CRDS patch/version of the Perna2023a bug fixes
- Wiggle-correction parameters (in prep. paper, Ulivi et al.)
- pPXF settings: template subset, velocity/kinematic starting guesses, masks, gas-template list
- Savitzky-Golay window and polynomial order for the pseudo-continuum above 2.4 um
- Initial guesses, bounds and which lines were tied for the CAP-MPFIT emission-line fits
- Exact line lists and wavelength windows used for the extinction, n_e and diagnostic-diagram ratios and the Pa-alpha dust-correction factors per region
- How the 3-sigma upper limits for high-ionisation lines were computed (noise estimate, integration window)

## Analysis recipe

1. **reduce NIRSpec IFS cubes**: STScI pipeline with patches, outlier rejection and drizzle combination of eight dithers  
  > "We used the STScI pipeline v1.8.2 with CRDS context 1063." (Data reduction); "The combination of the eight dithers (with drizzle weighting) allowed us to sub-sample the detector pixels" (Data reduction)
   - software: STScI JWST pipeline
   - parameter: 1/f noise corrected by polynomial fit; slice-edge pixels (one pixel wide) masked  
  > "we masked pixels at the edge of the slices (one pixel wide)" (Data reduction)
   - fitting: _not stated_
   - validation: Overlapping band ranges at ~1.85 and ~3 um match, showing consistent flux calibration  
  > "show a perfect match between the different bands, demonstrating a consistent flux calibration." (Spectral extraction)
2. **register cubes and tie to ALMA astrometry**: Align band cubes via narrow-band images, then match nuclei positions to ALMA 2.6 mm and 1.3 mm continuum  
  > "Therefore, we corrected the WCS registrations of the band2 and band3 cubes to match the coordinates in band1." (Astrometric registration); "We matched the central position of the two nuclei in the NIRSpec narrow-band image" (Astrometric registration)
   - parameter: Final correction applied to all three cubes: dRA = -0.3028'', dDec = -0.0209''  
  > "The astrometry corrections we applied to the three NIRSpec cubes are $\delta$RA $=-0.3028\ensuremath{''}$ and $\delta$DEC $= -0.0209\ensuremath{''}$." (Astrometric registration)
   - fitting: _not stated_
   - validation: Offset consistent with expected JWST pointing accuracy without dedicated target acquisition  
  > "This offset is consistent with the expected accuracy of JWST pointing without a dedicated target acquisition procedure" (Astrometric registration)
3. **extract nuclear spectra**: Circular apertures of 3 spaxels radius (0.15'', 55 pc) on W nucleus, E nucleus and NE cluster for each grating  
  > "We used apertures of three spaxels in radius, corresponding to $0.15\ensuremath{''}$ or $55$ pc." (Spectral extraction)
   - parameter: No aperture corrections applied  
  > "We note that no aperture corrections are taken into account in this work." (Spectral extraction)
   - fitting: _not stated_
   - validation: _not stated_
4. **model stellar and pseudo-continuum**: pPXF with MARCS templates plus Gaussian gas templates below 2.4 um; Savitzky-Golay pseudo-continuum above 2.4 um  
  > "we used the penalised-pixel-fitting routine pPXF ((cite: Cappellari2017))" (Modelling of the continuum emission); "we preferred to model the pseudo-continuum with a Savitzky–Golay filter after masking all prominent emission and absorption features." (Modelling of the continuum emission)
   - software: pPXF, MARCS library
   - parameter: Sixth-order multiplicative polynomial  
  > "We also adopted a sixth-order multiplicative polynomial to better reproduce the spectral continuum shape." (Modelling of the continuum emission)
   - fitting: Penalised pixel fitting (pPXF); priors not stated  
  > "we used the penalised-pixel-fitting routine pPXF ((cite: Cappellari2017))" (Modelling of the continuum emission)
   - validation: _not stated_
5. **fit emission lines**: Gaussian fits of H I, H2 and [Fe II] transitions as separate species, tied wavelengths and common widths; 1 vs 2 components chosen by BIC  
  > "For each species we performed two fits, with one and two Gaussian components per emission line respectively." (Modelling of the emission lines); "The number of Gaussian sets (i.e. distinct kinematic components) used to model the lines of a specific species was determined on the basis of the Bayesian information criterion (BIC; (cite: Schwarz1978))." (Modelling of the emission lines)
   - software: CAP-MPFIT
   - parameter: Line widths in km/s fixed equal within a species; wavelength separations fixed by atomic physics  
  > "we fixed their widths (in km s$^{-1}$) to be the same for all the emission lines." (Modelling of the emission lines)
   - fitting: Levenberg-Marquardt least squares (CAP-MPFIT); no priors or sampler stated  
  > "All transitions were fitted using the Levenberg–Markwardt least-squares fitting code CAP-MPFIT ((cite: Cappellari2017))." (Modelling of the emission lines)
   - validation: _not stated_
6. **derive extinction, electron density, SFR and outflow velocity**: Colour excess from Pa-beta/Br-gamma (also Br-delta/Pf-gamma and [Fe II] ratios); n_e from [Fe II] 1.677/1.644 um; Pa-alpha and PAH SFRs; v_max = DeltaV_broad + 2 sigma_broad  
  > "We calculated the colour excess in terms of Pa$\beta$ and Br$\gamma$," (Extinction); "to infer electron densities in the range log n$_e$ $\approx 3.5- 4.5$ cm$^{-3}$ for the three regions of interest (from Eq. 6 in (cite: Koo2016))" (Electron density); "In this work, we consider as outflow velocity $v_{max} = \Delta V_{broad} + 2\sigma_{broad}$, where $\sigma_{broad}$ is corrected for instrumental resolution" (Nuclear outflows)
   - parameter: For E and W nuclei only narrow components used for SFR  
  > "for the E and W nuclear emission we consider only the narrow components" (Star-formation tracers)
   - assumption: Intrinsic Pa-beta/Br-gamma = 5.88 for Te = 10^4 K, ne = 10^3 cm^-3  
  > "where the intrinsic ratio Pa$\beta$/Br$\gamma$ is set to 5.88 assuming an electron temperature and a density of 10$^4$ K and 10$^3$ cm$^{-3}$ respectively" (Extinction)
   - assumption: Cardelli et al. extinction law, R_V = 3.1  
  > "were derived assuming a (cite: Cardelli1989) extinction law." (Extinction); "(assuming R$_V = 3.1$)" (Extinction)
   - assumption: Pa-alpha SFR assumes ne = 10^3 cm^-3 and T = 10^4 K  
  > "we assumed electron density of 10$^3$ cm$^{-3}$ (the dependence from n$_e$ is very weak) and temperature of 10$^4$ K." (Star-formation tracers)
   - fitting: _not stated_
   - validation: Extinction from three diagnostic ratios agrees  
  > "We do not observe significant differences in the measurements obtained from the three diagnostic ratios above mentioned" (Extinction)
7. **test AGN signatures: high-ionisation lines and diagnostic diagrams**: Search for coronal lines (IP > 54 eV) with 3-sigma upper limits, compare [Si VI] with BASS L(X-ray) relation, and place line ratios on NIR diagnostic diagrams after extinction correction  
  > "for all other high ionisation lines we report 3$\sigma$ upper limits for the luminosities, assuming FWHM $= 250$ km s$^{-1}$." (Absence of high-ionisation lines); "We used the diagnostic diagrams presented by (cite: Riffel2013), (cite: Colina2015), and (cite: Calabro2023)" (Near-infrared emission line diagnostic diagrams)
   - parameter: Upper limits assume FWHM = 250 km/s  
  > "assuming FWHM $= 250$ km s$^{-1}$." (Table 1 notes)
   - fitting: _not stated_
   - validation: VV114 nuclei used as a benchmark for comparison  
  > "Hence, they serve as an optimal benchmark for comparison with the nuclei of Arp 220" (Identification of the lines)

## Software

- **STScI JWST pipeline** v1.8.2 (CRDS context 1063): Reduction of NIRSpec IFS data to cubes  
  > "We used the STScI pipeline v1.8.2 with CRDS context 1063." (Data reduction)
- **pPXF** : Stellar continuum fitting  
  > "we used the penalised-pixel-fitting routine pPXF ((cite: Cappellari2017))" (Modelling of the continuum emission)
- **CAP-MPFIT** : Least-squares fitting of emission lines  
  > "All transitions were fitted using the Levenberg–Markwardt least-squares fitting code CAP-MPFIT ((cite: Cappellari2017))." (Modelling of the emission lines)
- **NIST Atomic Spectra Database** : Identification of faint lines  
  > "We also use the NIST atomic spectra database[^2] ((cite: Ralchenko2005))" (Identification of the lines)
- **HITRAN** : Identification of faint molecular lines  
  > "and the HITRAN (high-resolution transmission molecular absorption database[^3], (cite: Rothman2021))" (Identification of the lines)

## Numeric results

| quantity | value | uncertainty | units | step | quote |
|---|---|---|---|---|---|
| Number of ionised emission lines identified in nuclear spectra | ~70 | not stated | lines | 5 | We identify $\sim 70$ ionised and $\sim 50$ molecular emission lines in the nuclear spectra of Arp 220. |
| Number of molecular emission lines identified in nuclear spectra | ~50 | not stated | lines | 5 | We identify $\sim 70$ ionised and $\sim 50$ molecular emission lines in the nuclear spectra of Arp 220. |
| Optical extinction A_V from recombination lines (nuclei and NE cluster) | ~11-14 | not stated | mag | 6 | We use recombination line ratios to measure optical extinctions in the range A$_V \sim 11-14$ mag. |
| A_V of the E nucleus | ~14 | not stated | mag | 6 | The most extreme extinction is associated with the E nucleus, with A$_V \sim 14$ |
| [Fe II]-based electron density, three regions | log n_e ~ 3.5-4.5 | not stated | cm^-3 | 6 | to infer electron densities in the range log n$_e$ $\approx 3.5- 4.5$ cm$^{-3}$ for the three regions of interest |
| Pa-alpha SFR of W nucleus | ~0.5 | not stated | Msun/yr | 6 | resulting in a SFR $\sim 0.5$ M$_{\odot}$ yr$^{-1}$ for the W nucleus, $\sim 0.2$ M$_{\odot}$ yr$^{-1}$ for the E nucleus, and $\sim 0.9$ M$_{\odot}$ yr$^{-1}$ for the NE cluster. |
| Pa-alpha SFR of E nucleus | ~0.2 | not stated | Msun/yr | 6 | resulting in a SFR $\sim 0.5$ M$_{\odot}$ yr$^{-1}$ for the W nucleus, $\sim 0.2$ M$_{\odot}$ yr$^{-1}$ for the E nucleus, and $\sim 0.9$ M$_{\odot}$ yr$^{-1}$ for the NE cluster. |
| Pa-alpha SFR of NE cluster | ~0.9 | not stated | Msun/yr | 6 | resulting in a SFR $\sim 0.5$ M$_{\odot}$ yr$^{-1}$ for the W nucleus, $\sim 0.2$ M$_{\odot}$ yr$^{-1}$ for the E nucleus, and $\sim 0.9$ M$_{\odot}$ yr$^{-1}$ for the NE cluster. |
| Total SFR(Pa-alpha) of the three regions | ~2 | not stated | Msun/yr | 6 | these three regions account for a total SFR(Pa$\alpha$) $\sim 2$ M$_{\odot}$ yr$^{-1}$. |
| Dust-corrected SFR(PAH 3.3 um) of the three regions | ~1.5-3.4 | not stated | Msun/yr | 6 | dust-corrected SFR(PAH) in the range $\sim 1.5-3.4$ M$_{\odot}$ yr$^{-1}$ |
| Total SFR(PAH) from integrated spectrum, r = 1.5'' | ~40 | not stated | Msun/yr | 6 | the total SFR(PAH) $\sim 40$ M$_{\odot}$ yr$^{-1}$ we measure from NIRSpec data using an integrated spectrum extracted over a very large aperture |
| Maximum outflow velocity in the nuclei | ~550 | not stated | km/s | 6 | with velocities up to $\sim 550$ km s$^{-1}$. |
| Maximum outflow velocity in off-nuclear regions | ~900 | not stated | km/s | 6 | Significantly higher velocities (up to $\sim 900$ km s$^{-1}$) are detected in the off-nuclear regions |
| [Mg IV] 4.488 um line luminosity, W nucleus | 38.03 (log) | 0.01 | log erg/s | 7 | $38.03\pm 0.01$ (W) |
| [Mg IV] 4.488 um line luminosity, E nucleus | 37.72 (log) | 0.02 | log erg/s | 7 | $37.72\pm 0.02$ (E) |
| FWHM of the 4.488 um feature | ~300 | not stated | km/s | 7 | these features are broad (FWHM $\sim 300$ km s$^{-1}$) and blue-shifted ($\Delta V\sim -100$ km s$^{-1}$) |
| Improvement of [Si VI] upper limit over previous observations at z ~ 0.018 | ~1 | not stated | dex | 7 | NIRSpec enables us to obtain more stringent upper limits compared to previous observations of other systems at $z \sim 0.018$ (by $\sim 1$ dex) |

## Qualitative findings

- NE cluster has narrow symmetric profiles; both nuclei show broad, preferentially blue-shifted profiles  
  > "The NE cluster shows symmetric and narrow profiles; conversely, broad and asymmetric (preferentially blue-shifted) line shapes are observed in both nuclear regions" (Nuclear outflows)
- High-ionisation lines are not detected apart from the 4.488 um feature  
  > "High ionisation lines are not detected in the nuclear spectra of Arp 220." (Absence of high-ionisation lines)
- 12CO ro-vibrational lines are seen up to J_low = 23  
  > "The W and E nuclei of Arp 220 show $^{12}$CO ro-vibrational lines up to J$_{low}$ = 23" (Qualitative comparison between Arp 220 nuclear regions and the bright cluster)

## Claim tuples

- H: Is the 4.488 um feature an AGN-excited [Mg IV] line? | E: Compared feature width, velocity and spatial distribution with expectations, and checked for [Ar VI] | R: Feature is broad, blue-shifted, bright at clusters and [Ar VI] is not detected | F: Emission attributed to shocks (stellar activity), not AGN | **partially**
- H: Do the nuclear outflow velocities show AGN activity? | E: Multi-component Gaussian fits of Pa-alpha, [Fe II] and H2 lines, v_max and W80 | R: v_max up to ~550 km/s in nuclei and ~900 km/s off-nuclear | F: Velocities do not conclusively demonstrate AGN activity | **partially**
- H: Can NIR emission-line diagnostics separate AGN from supernova/starburst ionisation? | E: Extinction-corrected line ratios on Riffel2013, Colina2015 and Calabro2023 diagrams | R: Nuclei lie in AGN/AGN+supernova regions or slightly above maximum starburst line | F: Diagnostics cannot distinguish supernova and AGN ionisation | **refuted**
- H: Can the NIRSpec data explain the discrepancy between NIR and radio/far-IR star-formation tracers? | E: Pa-alpha and 3.3 um PAH SFRs for each region compared with radio/far-IR values | R: NIR SFRs are far below radio/far-IR SFRs | F: NIRSpec SFRs do not resolve the existing discrepancy | **refuted**
- H: Is an AGN present in the Arp 220 nuclei? | E: Search for AGN features in NIRSpec spectra within 55 pc | R: No unambiguous AGN features; A_V ~ 11-14 from recombination lines | F: AGN presence neither confirmed nor excluded because of extreme obscuration | **partially**

## Reasoning

- Why this data: JWST/NIRSpec IFS gives NIR spectra of the obscured nuclei at high sensitivity and spatial resolution  
  > "In this work, we revisit Arp 220 and its nuclear regions taking advantage of JWST observations performed with the IFS unit of the NIRSpec instrument" (Introduction)
- Why this method: MARCS templates chosen over E-MILES and XSL for resolution and wavelength coverage reasons  
  > "MARCS templates were preferred to E-MILES ((cite: Vazdekis2016)), which have lower spectral resolution than our NIRSpec data" (Modelling of the continuum emission)
- Alternative: E-MILES and XSL stellar libraries rejected (lower resolution; narrower coverage and telluric features)  
  > "which have narrower wavelength coverage and are affected by telluric features." (Modelling of the continuum emission)
- How they decided it was enough: _not stated_
- Limitation (authors): NIRSpec may probe only outer gas layers; true extinction towards the cores may be much higher  
  > "This suggests that NIRSpec observations may only probe the outer gaseous layers" (Extinction)
- Limitation (authors): Intrinsic X-ray luminosities of Arp 220 are only upper limits and highly uncertain  
  > "it should be noted that measuring intrinsic X-ray luminosity for highly obscured sources can be highly uncertain" (Absence of high-ionisation lines)
- Limitation (authors): No aperture corrections applied  
  > "We note that no aperture corrections are taken into account in this work." (Spectral extraction)
- Caveat (inferred, ours): ALMA role is limited to astrometric registration; no ALMA reduction or measurement is described
- Caveat (inferred, ours): Positional offsets are applied without stated uncertainty
- Caveat (inferred, ours): Tabulated line fluxes come from single-Gaussian fits only, while kinematics use multi-component fits
- Caveat (inferred, ours): Choice of 1 vs 2 components by BIC without stated priors or fit uncertainties method
- Caveat (inferred, ours): No aperture corrections, so luminosities are lower limits for extended emission

## Reproducibility

- Data public (paper): _not stated_
- Products in archive: _not stated_
- Missing: JWST observation identifiers and the pipeline patch / wiggle-correction code
- Missing: ALMA map reduction details for astrometry
- Missing: Fit initial conditions and masks for pPXF and CAP-MPFIT
- Data volume (inferred): JWST NIRSpec IFS cubes (several GB); ALMA 2017.1.00042.S 1.3 mm continuum only for astrometry (tens of GB archive-wide if reprocessed, but archive image products would suffice)
- Score (inferred): 2/5, ALMA enters only for astrometry and its details are not given; JWST processing depends on unpublished patches and in-prep methods, though numeric results are tabulated
- Rediscovery candidate: no, ALMA is minor, data public status not stated in the paper, and the JWST recipe relies on unpublished in-prep and patched methods

## Links

- Method: (cite: Perna2023a) (Pipeline patch and wiggle-correction methodology)
- Method: (cite: DEugenio2023) (Outlier rejection and NIRSpec spatial resolution)
- Method: (cite: Boker2022) (NIRSpec IFS mode description)
- Method: (cite: Cappellari2017) (pPXF and CAP-MPFIT)
- Companion: Ulivi et al., in prep. (Spatially resolved gas kinematics and outflow energetics)
- Companion: Buiten et al., in prep. (Modelling of high-excitation CO gas)
- Companion: Pereira-Santaella et al. (subm.) ([Mg IV] emission from supernova shocks in ULIRGs)
- Related: JWST/NIRSpec IFS GTO survey 'Resolved structure and kinematics of the nuclear regions of nearby galaxies'
- Related: JWST programme 1267
- Related: JWST programme 1328 (VV114)
- Related: BASS (Swift/BAT AGN Spectroscopic Survey)

## Checks

```json
{
 "quotes": 109,
 "quotes_ok": 109,
 "quote_pass_rate": 1.0,
 "quotes_too_long": 0,
 "unsupported_facts": 0,
 "project_codes": 1,
 "codes_not_in_text": [],
 "codes_not_in_obscore": [],
 "obscore_codes_not_in_card": [
  "2015.1.00113.S"
 ],
 "codes_printed_but_missing": [],
 "numeric_results": 17,
 "numeric_problems": 0,
 "fill": {
  "facts": 104,
  "stated": 65,
  "rate": 0.625
 },
 "evidence_ok": true
}
```
