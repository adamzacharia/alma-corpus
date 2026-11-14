# A 260 pc resolution ALMA map of HCN(1─0) in the galaxy NGC 4321

`2024A&A...691A.121N` | Astronomy and Astrophysics 2024 | first author: Neumann, Lukas | arXiv: 2406.12025 | DOI: 10.1051/0004-6361/202449496

Card schema 1.0 | model claude-sonnet-5-5-claude-code | depth full | type observational_alma_primary

## Science

- Fields: nearby_galaxies, star_formation
- Question: How do the dense gas fraction (HCN/CO) and dense gas star formation efficiency (SFR/HCN) vary across morphological environments and ISM pressure at 260 pc resolution over the full disc of NGC 4321, and is there a pressure threshold for dense gas and star formation?  
  > "address the question: “Is there a pressure threshold for dense gas and star formation?”" (5.1 Pressure threshold for dense gas and star formation); "Such a study is, however, needed to study the sub-kpc structured ISM without blending many regions together" (Introduction)
- Target **NGC 4321 (M100)**: coordinates RA 12°21′54.9″, Dec 04°28′25.5″ (J2000)  
  > "12°21′54.9″" (Table 1); "04°28′25.5″" (Table 1); "At a distance of $d=\SI{15.2}{\mega\parsec}$ (cite: Anand2021) it is relatively nearby" (2.1 The target – NGC 4321); "(a) (cite: Anand2021);" (Table 1); z/distance d = 15.2 Mpc (15.21 ± 0.49 Mpc in Table 1); systemic velocity 1572 ± 5 km/s  
  > "12°21′54.9″" (Table 1); "04°28′25.5″" (Table 1); "At a distance of $d=\SI{15.2}{\mega\parsec}$ (cite: Anand2021) it is relatively nearby" (2.1 The target – NGC 4321); "(a) (cite: Anand2021);" (Table 1); distance from Anand et al. 2021 (cite: Anand2021)  
  > "12°21′54.9″" (Table 1); "04°28′25.5″" (Table 1); "At a distance of $d=\SI{15.2}{\mega\parsec}$ (cite: Anand2021) it is relatively nearby" (2.1 The target – NGC 4321); "(a) (cite: Anand2021);" (Table 1)

## Data provenance

- ALMA projects: 2017.1.00815.S, 2015.1.00956.S, 2011.0.00004.SV
- bands: Band 3 (HCN(1-0), HCO+(1-0), CS(2-1))  
  > "we present ALMA Band-3 observations (2017.1.00815.S; PI.: Molly Gallagher) which mapped" (2.2 New ALMA maps of HCN)
- frequencies and spectral setup: 4 spectral windows, each 1875 MHz wide with 976 kHz channels: 88.5 GHz (HCN, HCO+), 87.0 GHz (SiO, H13CN, H13CO+), 98.5 GHz (CS), 100 GHz (continuum)  
  > "The spectral setup encompasses four spectral windows, each with a bandwidth of 1875 MHz" (2.2 New ALMA maps of HCN); "The first window, centred at 88.5 GHz targets" (2.2 New ALMA maps of HCN); "The fourth spectral window at 100 GHz is used to detect continuum emission." (2.2 New ALMA maps of HCN)
- continuum bandwidth: _not stated_
- arrays: 12-m array (18.1 h), ACA 7-m array (73.4 h) and 12-m dishes in total power mode (125.2 h); 27 Nyquist-spaced 12-m pointings in a 200" x 120" mosaic  
  > "The observations combine interferometric observations from the 12-m array (18.1 h observing time) with the ACA consisting of the 7-m array (73.4 h) and the 12-m dishes observing in total power (TP) mode (125.2 h)." (2.2 New ALMA maps of HCN); "created via a mosaic consisting of 27 Nyquist-spaced pointings with the 12-m array" (2.2 New ALMA maps of HCN)
- configurations: _not stated_
- baselines: _not stated_
- angular resolution: 3.5 arcsec (~260 pc)  
  > "at a high angular resolution of 3.5″ using 216.7 h of ALMA telescope time" (2.2 New ALMA maps of HCN)
- max recoverable scale: _not stated_
- sensitivity: ~8 mK noise per 5 km/s channel (HCN cube)  
  > "The resulting HCN position-position-velocity cube has $\sim\SI{8}{\milli\kelvin}$ noise per 5 km s^−1^ channel." (2.2 New ALMA maps of HCN)
- time on source: 216.7 h of ALMA telescope time in total (12-m 18.1 h, 7-m 73.4 h, TP 125.2 h)  
  > "using 216.7 h of ALMA telescope time" (2.2 New ALMA maps of HCN)
- observing dates: _not stated_
- pi or archival as stated: 2017.1.00815.S, PI Molly Gallagher  
  > "(2017.1.00815.S; PI.: Molly Gallagher)" (2.2 New ALMA maps of HCN)
- Line: HCN 1-0 (88.6 GHz)
- Line: HCO+ 1-0 (89.2 GHz)
- Line: CS 2-1 (97.9809533 GHz)
- Line: SiO, H13CN, H13CO+ SiO(2-1), H13CN(1-0), H13CO+(1-0) (SiO 86.9 GHz (others not stated))
- Line: CO 2-1 (PHANGS-ALMA, not part of the new observations) (not stated)
- Other facility **PHANGS-ALMA (CO 2-1)**: CO(2-1) cube at 1.67 arcsec (120 pc) tracing bulk molecular gas  
  > "the CO data are at 1.67″ resolution, which corresponds to 120 physical scale at the distance of the galaxy." (3.2 Molecular gas surface density – CO)
- Other facility **ALMA archival CO(1-0) (science verification)**: 4 arcsec CO(1-0) used to build the R21 map  
  > "with ALMA at 4″ resolution" (7.1.2 Spatially varying conversion factor); "was part of the ALMA science verification" (2.1 The target – NGC 4321)
- Other facility **PHANGS-MUSE (VLT)**: Balmer-decrement corrected Halpha maps used as the primary SFR tracer  
  > "recombination line emission taken by the Multi Unit Spectroscopic Explorer (MUSE) of the Very Large Telescope (VLT) as part of the PHANGS–MUSE survey" (3.4 Star formation rate (SFR) – Halpha)
- Other facility **PHANGS-JWST (MIRI F2100W)**: 21 um dust emission as an alternative SFR tracer (appendix)  
  > "was observed by JWST in June 2023 and we use version 0.9 of the PHANGS–JWST data reduction." (9.1 SFR – 21 um)
- Other facility **VLA 33 GHz**: free-free emission as an additional SFR tracer in the centre  
  > "The data are coming from Very Large Array (VLA) observations of a large sample of galaxies" (9.2 SFR – 33 GHz)
- Other facility **VLA HI (HERACLES)**: HI 21-cm at ~20 arcsec for atomic gas surface density  
  > "data are from VLA observations associated with HERACLES (cite: Leroy2009) mapping several nearby galaxies in" (7.2 Atomic gas – HI 21-cm)
- Other facility **Spitzer S4G 3.6 um**: stellar mass surface density map (via Querejeta et al. 2015) and environment masks  
  > "We use the stellar mass surface density map from (cite: Querejeta2015), who use 3.6 μm observations from the" (7.3 Stellar mass – 3.6 um)
- External data: PHANGS-ALMA CO(2-1) data cube of NGC 4321  
  > "We use $\text{CO(2--1)}$(hereafter CO) line observations from PHANGS–ALMA (cite: Leroy2021b) to trace the bulk molecular gas." (3.2 Molecular gas surface density – CO) [from (cite: Leroy2021b)]
- External data: Morphological environmental masks (centre, bar, bar ends, spiral arms, interarm)  
  > "We adopt the environmental masks presented in (cite: Querejeta2021)" (3.7 Morphological environmental masks) [from (cite: Querejeta2021)]
- External data: Balmer-decrement corrected Halpha maps (MUSE)  
  > "Those rely on the extinction curve from (cite: O’Donnell1994) as described in (cite: Pessa2022) and (cite: Belfiore2023)." (3.4 Star formation rate (SFR) – Halpha) [from (cite: Emsellem2022); (cite: Pessa2022); (cite: Belfiore2023)]
- External data: Halpha-to-SFR conversion factor C_Halpha = 5.3e-42  
  > "using the conversion factor $C_{\ensuremath{\text{H}\alpha}}=\num{5.3e-42}$ from (cite: Calzetti2007)" (3.4 Star formation rate (SFR) – Halpha) [from (cite: Calzetti2007)]
- External data: alpha_CO = 4.35 Msun pc^-2 (K km/s)^-1 (constant case)  
  > "$\ensuremath{\alpha_{\text{CO}}}=\SI{4.35}{\Msun\per\square\parsec}\,(\SI{}{\Kkms})^{-1}$ (cite: Bolatto2013)" (3.3 Dense gas fraction – HCN/CO) [from (cite: Bolatto2013)]
- External data: alpha_HCN = 14 Msun pc^-2 (K km/s)^-1  
  > "$\ensuremath{\alpha_{\text{HCN}}}=\SI{14}{\Msun\per\square\parsec}\,(\SI{}{\Kkms})^{-1}$ (cite: Onus2018)" (3.3 Dense gas fraction – HCN/CO) [from (cite: Onus2018)]
- External data: Fiducial R21 = 0.65  
  > "a fiducial $\text{CO(2--1)}$-to-$\text{CO(1--0)}$ line ratio of $R_{21}=0.65$ (cite: denBrok2022; Leroy2022)" (3.3 Dense gas fraction – HCN/CO) [from (cite: denBrok2022; Leroy2022)]
- External data: Local metallicity from MUSE via Gaussian Process Regression  
  > "applying a Gaussian Process Regression (GPR) to model the 2D metallicity distribution (cite: Williams2022)" (7.1.2 Spatially varying conversion factor) [from (cite: Williams2022)]
- External data: Stellar mass surface density map from attenuation-corrected 3.6 um (ICA)  
  > "We use the stellar mass surface density map from (cite: Querejeta2015), who use 3.6 μm observations from the" (7.3 Stellar mass – 3.6 um) [from (cite: Querejeta2015); S4G (cite: Sheth2010)]
- External data: Stellar disc scale length R_star = 61.1 arcsec (~4.5 kpc)  
  > "We adopt $R_\star=\SI{61.1}{\ensuremath{''}}\sim\SI{4.5}{\kilo\parsec}$ from the S$^4$G photometric decomposition analysis (cite: Salo2015)" (7.3 Stellar mass – 3.6 um) [from (cite: Salo2015)]
- External data: Stellar mass-to-light ratio 0.6 Msun/Lsun  
  > "which assumes a constant mass-to-light ratio of $0.6\,\SI{}{\Msun}/\SI{}{\Lsun}$ (cite: Meidt2014)" (7.3 Stellar mass – 3.6 um) [from (cite: Meidt2014)]
- External data: VLA 33 GHz data and thermal fractions (their table 4)  
  > "where the thermal fraction ($f_{\rm thermal}$) values are taken from (cite: Linden2020) (their table 4;" (9.2 SFR – 33 GHz) [from (cite: Linden2020)]
- External data: Galaxy properties: inclination 38.5 deg, position angle 156.2 deg, systemic velocity  
  > "(b) (cite: Lang2020);" (Table 1) [from (cite: Lang2020)]

## Processing

### Calibration

- pipeline or manual: PHANGS-ALMA pipeline, built on CASA  
  > "The data reduction was performed using the PHANGS–ALMA pipeline (details can be found in (cite: Leroy2021a))" (2.2 New ALMA maps of HCN)
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
- array combination: 12-m interferometric + 7-m ACA + 12-m total power data combined  
  > "The observations combine interferometric observations from the 12-m array (18.1 h observing time) with the ACA consisting of the 7-m array (73.4 h) and the 12-m dishes observing in total power (TP) mode (125.2 h)." (2.2 New ALMA maps of HCN)
- smoothing: CO(2-1) convolved to the HCN resolution with astropy convolution.convolve  
  > "First, we homogenise the data by convolving the CO data to the HCN resolution" (3.1 Integrated intensity maps)
- final beam: 3.5 arcsec (~260 pc)  
  > "at a high angular resolution of 3.5″ using 216.7 h of ALMA telescope time" (2.2 New ALMA maps of HCN)
- final rms: ~8 mK per 5 km/s channel  
  > "The resulting HCN position-position-velocity cube has $\sim\SI{8}{\milli\kelvin}$ noise per 5 km s^−1^ channel." (2.2 New ALMA maps of HCN)

### Inherited from earlier work

- ALMA data reduction and imaging of the HCN cube  
  > "The data reduction was performed using the PHANGS–ALMA pipeline (details can be found in (cite: Leroy2021a))" (2.2 New ALMA maps of HCN) [from PHANGS-ALMA pipeline (cite: Leroy2021a)]
- Moment-0 map construction (CO-based 4 sigma/2 sigma velocity masks)  
  > "We produce integrated intensity maps (moment-0 maps) from the CO and HCN position-position-velocity (PPV) cubes following (cite: Neumann2023a)." (3.1 Integrated intensity maps) [from (cite: Neumann2023a); methodology from (cite: Schruba2011)]
- Dynamical equilibrium pressure prescription (cloud-scale plus atomic terms)  
  > "following the prescription by (cite: Sun2020a)" (3.6 Dynamical equilibrium pressure) [from (cite: Sun2020a)]
- Morphological environment definitions (simple mask)  
  > "We adopt the environmental masks presented in (cite: Querejeta2021)" (3.7 Morphological environmental masks) [from (cite: Querejeta2021)]
- Iterative solution of the spatially varying alpha_CO  
  > "following the iterative approach presented in (cite: Sun2022)" (7.1.2 Spatially varying conversion factor) [from (cite: Sun2022); Equation 31 of (cite: Bolatto2013)]
- Cloud-scale molecular gas properties (Sigma_mol, sigma_mol, alpha_vir)  
  > "The cloud-scale molecular gas properties are computed following the prescriptions of (cite: Sun2018) and (cite: Neumann2023a)" (10.1 Molecular cloud relations) [from (cite: Sun2018); (cite: Neumann2023a)]
- Spectral stacking method (PyStacker)  
  > "presented in (cite: Neumann2023b)" (8 Spectral stacking) [from (cite: Neumann2023b)]
- 21 um SFR calibration  
  > "we use the empirical relation from (cite: Leroy2023) (their equation 5)" (9.1 SFR – 21 um) [from (cite: Leroy2023)]

### Not stated but needed to reproduce (our reading)

- CASA version and PHANGS-ALMA pipeline version/commit used for this project
- Imaging parameters of the HCN cube (tclean weighting/robust, taper, deconvolver, cell size, masks, clean threshold, restoring beam) are not given; only the pipeline is cited
- Line-free channels and any continuum subtraction used for the HCN cube
- How the 12-m, 7-m and total-power data were combined (feather/joint deconvolution) and the primary-beam treatment
- Flux calibrators and absolute flux uncertainty
- Observation dates and baseline ranges / maximum recoverable scale
- Which ALMA project supplies the PHANGS CO(2-1) data (2015.1.00956.S appears in the acknowledgments without a stated role)
- Version/release of the PHANGS-MUSE, PHANGS-JWST (v0.9 stated only for JWST), and PHANGS-ALMA CO products
- Exact bin edges and counts used in the radial, pressure and Sigma_mol stacks beyond the radial 0.5 kpc width
- MARS (earth) settings other than the maximum of two linear segments (degree, penalty, pruning), and LinMix priors/chain settings
- Exact S/N masks used in stacking and the detection threshold handling for individual sight lines
- Total beam-size spaxel grid origin/orientation for the hexagonal grid

## Analysis recipe

1. **Reduce and image the ALMA HCN data**: Data reduced with the PHANGS-ALMA pipeline (CASA-based), producing an HCN PPV cube combining 12-m, ACA 7-m and TP data  
  > "The data reduction was performed using the PHANGS–ALMA pipeline (details can be found in (cite: Leroy2021a))" (2.2 New ALMA maps of HCN)
   - software: PHANGS-ALMA pipeline, CASA
   - parameter: ~8 mK noise per 5 km/s channel  
  > "The resulting HCN position-position-velocity cube has $\sim\SI{8}{\milli\kelvin}$ noise per 5 km s^−1^ channel." (2.2 New ALMA maps of HCN)
   - parameter: Channel width 5 km/s used in the analysis  
  > "is the channel width of 5 km s^−1^" (3.1 Integrated intensity maps)
   - fitting: _not stated_
   - validation: _not stated_
2. **Homogenise CO and ancillary maps to the HCN beam and grid**: Convolve CO to HCN resolution; resample all data onto a hexagonal beam-spaced spaxel grid and common spectral axis; convolve 2D maps (Halpha, 21 um) to 260 pc and reproject  
  > "First, we homogenise the data by convolving the CO data to the HCN resolution" (3.1 Integrated intensity maps); "we convolve the maps to the 260 HCN resolution and reproject them onto the same beam-size hexagonal pixel grid" (3.1 Integrated intensity maps)
   - software: astropy
   - parameter: Hexagonal grid with beam-size spaxel separation  
  > "Then, we adopt a hexagonal spaxel grid with a beam-size spaxel separation and sample all data to the same spaxel grid and spectral axis." (3.1 Integrated intensity maps)
   - assumption: Every hexagonal pixel is an independent line of sight  
  > "This means that every hexagonal pixel is an independent line-of-sight (LOS) measurement." (3.1 Integrated intensity maps)
   - fitting: _not stated_
   - validation: _not stated_
3. **Build velocity masks and integrated intensities**: CO-based pixel-by-pixel velocity masks applied to CO and HCN cubes, summing T x channel width over masked channels; uncertainty from emission-free channel rms times sqrt(N_mask)  
  > "Then, we create velocity masks based on the CO on a pixel-by-pixel basis to select the velocity range where we also expect to find HCN emission." (3.1 Integrated intensity maps); "where $\sigma_{T_{\rm line}}$ is the standard deviation in the emission-free channels (i.e. channels not selected by the mask)" (3.1 Integrated intensity maps)
   - parameter: 4 sigma mask expanded into channels above 2 sigma  
  > "This is done by building a $4\sigma$ mask that is expanded into channels above $2\sigma$ in order to recover broader emission belonging to a $4\sigma$ core" (3.1 Integrated intensity maps)
   - parameter: Detection defined as S/N >= 3 per independent sight line  
  > "Shown are the number of detected ($\rm{S/N}\geq 3$) independent sight lines" (Table notes (stacked intensities))
   - assumption: HCN emission lies in the same velocity range as CO  
  > "to select the velocity range where we also expect to find HCN emission" (3.1 Integrated intensity maps)
   - fitting: _not stated_
   - validation: _not stated_
4. **Derive molecular gas surface density, HCN/CO and f_dense**: Sigma_mol from CO(2-1) with alpha_CO and R21, cos(i) inclination correction; HCN/CO as proxy of f_dense (f_dense ~ 2.1 W_HCN/W_CO(2-1)); two cases: constant conversion factors, and spatially varying alpha_CO and R21 (Bolatto et al. 2013 eq. 31, iterative, using MUSE metallicity, HI and 3.6 um)  
  > "using constant $\alpha_{\text{CO}}$ and $R_{21}$ conversion factors" (3.2 Molecular gas surface density – CO); "using spatially varying $\alpha_{\text{CO}}$ and $R_{21}$" (3.2 Molecular gas surface density – CO); "by applying the prescription described by Equation 31 from (cite: Bolatto2013)" (7.1.2 Spatially varying conversion factor)
   - parameter: alpha_CO = 4.35 Msun pc^-2 (K km/s)^-1 (constant case)  
  > "$\ensuremath{\alpha_{\text{CO}}}=\SI{4.35}{\Msun\per\square\parsec}\,(\SI{}{\Kkms})^{-1}$ (cite: Bolatto2013)" (3.3 Dense gas fraction – HCN/CO)
   - parameter: alpha_HCN = 14 Msun pc^-2 (K km/s)^-1  
  > "$\ensuremath{\alpha_{\text{HCN}}}=\SI{14}{\Msun\per\square\parsec}\,(\SI{}{\Kkms})^{-1}$ (cite: Onus2018)" (3.3 Dense gas fraction – HCN/CO)
   - parameter: R21 = 0.65 (constant); varying case uses a 4 arcsec R21 map from archival CO(1-0), median 0.54, scatter 0.16  
  > "a fiducial $\text{CO(2--1)}$-to-$\text{CO(1--0)}$ line ratio of $R_{21}=0.65$ (cite: denBrok2022; Leroy2022)" (3.3 Dense gas fraction – HCN/CO); "Here, we measure a median $R_{21}=0.54$ and a scatter of 0.16." (7.1.2 Spatially varying conversion factor)
   - parameter: Metallicity from MUSE via Gaussian Process Regression; fiducial GMC surface density fixed at 100 Msun/pc^2; iterative solution  
  > "applying a Gaussian Process Regression (GPR) to model the 2D metallicity distribution (cite: Williams2022)" (7.1.2 Spatially varying conversion factor); "we adopt a fiducial GMC surface density of 100" (7.1.2 Spatially varying conversion factor); "following the iterative approach presented in (cite: Sun2022)" (7.1.2 Spatially varying conversion factor)
   - assumption: Constant alpha_HCN, so f_dense is proportional to HCN/CO  
  > "We use a constant $\alpha_{\text{CO}}$ for the HCN-to-CO line ratio due to the poor knowledge about variations of the HCN-to-dense gas conversion factor thus keeping $f_{\text{dense}}$ proportional to HCN/CO." (3.2 Molecular gas surface density – CO)
   - fitting: _not stated_
   - validation: Compared with multi-line alpha_CO of Teng et al. 2023 in the central 2 kpc  
  > "are on average 0.20 smaller than the values used here, but consistent at the 1-sigma level within 0.21" (7.1.2 Spatially varying conversion factor)
5. **Derive SFR surface density and SFR/HCN**: Balmer-decrement corrected Halpha converted to SFR with the Calzetti et al. 2007 factor; SFE_dense proxy is SFR/HCN; alternative 21 um and 33 GHz tracers used to check Halpha  
  > "We use Balmer decrement-corrected $\text{H}\alpha$ maps to measure the star formation rate surface density" (3.4 Star formation rate (SFR) – Halpha); "We take the ratio of the star formation rate surface density" (3.5 Dense gas star formation efficiency – SFR/HCN)
   - parameter: C_Halpha = 5.3e-42 (Calzetti et al. 2007); extinction curve of O'Donnell 1994  
  > "using the conversion factor $C_{\ensuremath{\text{H}\alpha}}=\num{5.3e-42}$ from (cite: Calzetti2007)" (3.4 Star formation rate (SFR) – Halpha); "Those rely on the extinction curve from (cite: O’Donnell1994) as described in (cite: Pessa2022) and (cite: Belfiore2023)." (3.4 Star formation rate (SFR) – Halpha)
   - assumption: Constant star formation history, age 100 Myr, solar metallicity, Kroupa IMF  
  > "This conversion assumes a constant star formation history, age of 100  , solar metallicity, and a (cite: Kroupa2001) initial mass function (IMF)" (3.4 Star formation rate (SFR) – Halpha)
   - fitting: _not stated_
   - validation: Halpha SFR agrees with 33 GHz SFR within 20 percent and with a linear 21 um SFR within a factor 0.2 in the centre  
  > "agreeing within 20 %." (9.3 SFR tracer comparison); "21 $\mu$ m emission also yields similar SFR values (within 0.2) when adopting a linear conversion" (3.4 Star formation rate (SFR) – Halpha)
6. **Assign morphological environments**: Use the Querejeta et al. 2021 'simple' mask from S4G 3.6 um; bar ends defined as overlap of spiral arms with the bar; interbar and interarm combined; resampled onto the HCN hexagonal grid  
  > "We use the “simple” mask, where each pixel is uniquely assigned to a dominant environment." (3.7 Morphological environmental masks); "For simplicity, we combine interbar, interarm into one region, referred to as interarm." (3.7 Morphological environmental masks)
   - fitting: _not stated_
   - validation: _not stated_
7. **Compute dynamical equilibrium pressure**: Sun et al. 2020 formalism: 120 pc molecular-gas cloud term converted to 260 pc via Sigma_mol-weighted average plus 260 pc atomic-gas term; alternative simple P_DE with all quantities at 260 pc  
  > "In this study we adopt their formalism and combine the 120 scale molecular gas term" (3.6 Dynamical equilibrium pressure)
   - parameter: sigma_atom fixed at 10 km/s  
  > "the velocity dispersion of the atomic gas which is fixed at $\sigma_{\text{atom}}=\SI{10}{\kilo\metre\per\second}$" (7.4 Dynamical equilibrium pressure)
   - parameter: Stellar scale length R_star = 61.1 arcsec (~4.5 kpc); R_star/H_star = 7.3  
  > "We adopt $R_\star=\SI{61.1}{\ensuremath{''}}\sim\SI{4.5}{\kilo\parsec}$ from the S$^4$G photometric decomposition analysis (cite: Salo2015)" (7.3 Stellar mass – 3.6 um); "a fixed stellar disc flattening ratio of $R_\star/H_\star=7.3$ (cite: Kregel2002)" (7.3 Stellar mass – 3.6 um)
   - parameter: Stellar mass-to-light ratio 0.6 Msun/Lsun  
  > "which assumes a constant mass-to-light ratio of $0.6\,\SI{}{\Msun}/\SI{}{\Lsun}$ (cite: Meidt2014)" (7.3 Stellar mass – 3.6 um)
   - assumption: Smooth single-fluid gas disc with a common gas velocity dispersion  
  > "we assume a smooth, single-fluid gas disc, and that all gas shares a similar velocity dispersion" (3.6 Dynamical equilibrium pressure)
   - fitting: _not stated_
   - validation: _not stated_
8. **Stack spectra and binned data**: PyStacker shifts CO-prior-aligned spectra to a common velocity and averages them in bins of radius, pressure, Sigma_mol, environment etc.; integrated intensities from the average spectra; SFR averaged directly; bin ratios are ratios of stacks  
  > "which yields average CO and HCN spectra in each respective bin" (3.8 Stacking and linear regression); "It then uses this velocity information to shift the spectra of various line to correct for the Doppler shift, assuming all lines share the same velocity field." (8 Spectral stacking)
   - software: PyStacker
   - parameter: Equally spaced bins in linear scale for r_gal and logarithmic scale for P_DE; radial bins 0.5 kpc wide (twice the beam)  
  > "we stack the data (HCN, CO, SFR) in equally spaced bins in linear scale ($r_{\rm gal}$) or logarithmic scale ($P_{\text{DE}}$)" (3.8 Stacking and linear regression); "radial bins of 0.5 width, i.e. at twice the beam size" (4.2 Radial trends)
   - assumption: All lines share the CO velocity field  
  > "assuming all lines share the same velocity field" (8 Spectral stacking)
   - fitting: _not stated_
   - validation: Stacked intensities agree within 10 percent with binned integrated intensities using the CO mask  
  > "the spectral stacks agree within $\pm \SI{10}{\percent}$ with binned integrated intensities computed within the same stacking bins" (8 Spectral stacking)
9. **Fit piecewise-linear relations of HCN/CO and SFR/HCN with radius and pressure**: MARS (R package earth) fit to the binned data with at most two linear segments to find thresholds; LinMix fit to individual sight lines for slope uncertainties  
  > "model to the binned data in order to find the best piece-wise linear regression function that describes the data" (3.8 Stacking and linear regression); "Here, we force the model to only consist of up to two linear functions, i.e. it can either find one or two regimes" (3.8 Stacking and linear regression)
   - software: earth (R), LinMix
   - parameter: New split point accepted only if chi^2 improves by more than 0.01  
  > "meaning that the $\chi^2$ value is improved by more than 0.01" (3.8 Stacking and linear regression)
   - assumption: Binned stacks recover the underlying relation without population bias from non-detections  
  > "We fit the stacked data in order to probe the underlying global relation without “population” biases and to not be dominated by non-detections in constraining the best-fit line." (3.8 Stacking and linear regression)
   - fitting: MARS minimises chi^2 over split points (priors not applicable); LinMix is a Bayesian regression run via MCMC (priors, chain settings not stated); MARS gives no slope errors so LinMix sight-line fits provide them  
  > "is a Bayesian inference tool to linear regression, which can take into account upper limits and infers the posterior distribution of the fit line parameters via MCMC simulation" (Footnote 6); "We use these sight-line fits to quantify the uncertainty of the regression slopes since the MARS fitting routine (see below) does not yield uncertainties." (3.8 Stacking and linear regression)
   - validation: LinMix fits to individual sight lines agree within 1 sigma with the binned fits  
  > "resulting in similar fit relations in agreement within 1-sigma uncertainties with the fits reported here for the binned data" (3.8 Stacking and linear regression)
10. **Fit HCN/CO(1-0) versus Sigma_mol at 260 pc**: Stack and fit HCN/CO(1-0) (CO(2-1) converted with the R21 map) against beam-matched Sigma_mol using the varying alpha_CO; compare with literature relations and a constant alpha_CO case  
  > "we stack and fit the data to obtain the mean relation" (4.5 HCN/CO as a density tracer); "using a constant $\alpha_{\text{CO}}$ yields a shallower relation (slope of 0.48) compared to 0.61 with a varying" (4.5 HCN/CO as a density tracer)
   - software: earth (R), LinMix
   - parameter: Data below Sigma_mol = 10 Msun/pc^2 excluded from the fit  
  > "we exclude data below $\ensuremath{\Sigma_{\text{mol}}}<\SI{10}{\Msun\per\square\parsec}$" (4.5 HCN/CO as a density tracer)
   - fitting: Same stacking plus MARS/LinMix approach as step 9  
  > "we stack and fit the data to obtain the mean relation" (4.5 HCN/CO as a density tracer)
   - validation: Fits excluding the centre still show positive slopes of 0.25 (centre) and 0.35 (disc)  
  > "slopes of 0.25 (centre) and 0.35 (disc)" (4.5 HCN/CO as a density tracer)

## Software

- **CASA** : Standard ALMA data reduction package underlying the PHANGS-ALMA pipeline  
  > "which utilises the standard ALMA data reduction package `CASA` (cite: casa_package)" (2.2 New ALMA maps of HCN)
- **PHANGS-ALMA pipeline** : Reduction of the new HCN data  
  > "The data reduction was performed using the PHANGS–ALMA pipeline (details can be found in (cite: Leroy2021a))" (2.2 New ALMA maps of HCN)
- **astropy** : convolution.convolve used to degrade CO to the HCN resolution  
  > "First, we homogenise the data by convolving the CO data to the HCN resolution (using `convolution.convolve` from `astropy`)" (3.1 Integrated intensity maps)
- **PyStacker** : Spectral stacking of CO and HCN in bins  
  > "which yields average CO and HCN spectra in each respective bin" (3.8 Stacking and linear regression)
- **LinMix** : Bayesian linear regression of individual sight lines (slope uncertainties)  
  > "we have also fitted the individual sight-line measurements using" (3.8 Stacking and linear regression)
- **earth (R package, MARS)** : Piecewise-linear regression to find thresholds in the binned relations  
  > "To perform the MARS model we utilise the `R`-package `earth`" (3.8 Stacking and linear regression)

## Numeric results

| quantity | value | uncertainty | units | step | quote |
|---|---|---|---|---|---|
| HCN cube noise | ~8 | not stated | mK per 5 km/s channel | 1 | The resulting HCN position-position-velocity cube has $\sim\SI{8}{\milli\kelvin}$ noise per 5 km s^−1^ channel. |
| Independent lines of sight with HCN emission in the map | 302 | not stated | count | 3 | yielding detection of 302 independent lines of sight in HCN emission |
| Detected HCN sight lines (S/N >= 3), full galaxy | 275 | not stated | count | 3 | allows analysis of 275 detected sight lines |
| Detected HCN sight lines by environment | centre 42, bar 70, bar ends 26, spiral arms 97, interarm 40 | not stated | count | 3 | we detect 42 HCN sight lines in the centre, 70 in the bar, 26 in the bar ends, 97 in the spiral arms, and 40 in the interarm regions |
| Mean HCN/CO of detections in the centre | 0.089 | 0.0003 | dimensionless | 4 | reaches values around $0.1$ (mean of $0.089\pm 0.0003$) |
| Stacked HCN/CO in bar ends | 0.043 | 0.001 | dimensionless | 8 | we observe enhanced HCN/CO in the bar ends (mean of $0.043\pm 0.001$) |
| Stacked HCN/CO in interarm and spiral arms | interarm 0.015, spiral arms 0.028 | interarm 0.003, spiral arms 0.001 | dimensionless | 8 | in the interarm region (mean of $0.015\pm 0.003$) than in the spiral arms (mean of $0.028\pm 0.001$) |
| Mean SFR/HCN in the centre | 0.025 | 0.0001 | (Msun/yr/kpc^2)/(K km/s) | 5 | SFR/HCN decreases towards the centre of the galaxy (mean of $0.025\pm 0.0001$ |
| Mean SFR/HCN in the bar | 0.039 | 0.001 | (Msun/yr/kpc^2)/(K km/s) | 5 | we find SFR/HCN to be particularly low in the bar of the galaxy (mean of $0.039\pm 0.001$) |
| Mean SFR/HCN in bar ends, spiral arms and interarm (range) | 0.086 to 0.274 | 0.003 to 0.057 | (Msun/yr/kpc^2)/(K km/s) | 5 | have means between $0.086\pm 0.003$ and $0.274\pm 0.057$ |
| HCN/CO versus r_gal slope, r_gal <= 2.0 kpc | -0.38 | 0.02 | dex per kpc (slope as stated, units not given) | 9 | we measure a very strong (slope $m=-0.38\pm 0.02$, Pearson correlation coefficient $\rho=-0.86$ |
| HCN/CO versus r_gal slope in the disc (r_gal > 2.0 kpc) | 0.0 | 0.01 | as stated (slope) | 9 | HCN/CO remains constant on average ($m=0.0\pm 0.01$ |
| SFR/HCN versus r_gal slope, r_gal <= 2.8 kpc | 0.34 | 0.02 | as stated (slope) | 9 | SFR/HCN varies systematically with radius ($m=0.34\pm 0.02$ |
| MARS radial break radii | 2.0 kpc (HCN/CO), 2.8 kpc (SFR/HCN) | not stated | kpc | 9 | The MARS model finds two regimes in each of the radial correlations, which separates the relations into a central region ($\leq\SI{2.0}{\kilo\parsec}$ for HCN/CO and $\leq\SI{2.8}{\kilo\parsec}$ SFR/HCN) |
| HCN/CO versus <P_DE> slopes, high and low pressure | high 0.42, low 0.18 | 0.03 each | as stated (slope) | 9 | The correlation is steeper in the high-pressure ($m=0.42\pm 0.03$) regime compared to the low-pressure regime ($m=0.18\pm 0.03$). |
| HCN/CO versus <P_DE> single-line slope | 0.35 | 0.02 | as stated (slope) | 9 | However, the realtion could also be well fitted with a single linear function with $m=0.35\pm 0.02$. |
| SFR/HCN versus <P_DE> slopes, high and low pressure | high -0.89, low -0.32 | high 0.22, low 0.04 | as stated (slope) | 9 | ($\rho=-0.39$, $p=0.003$,$m=-0.89\pm 0.22$); In the low-pressure regime the relation is significantly flatter ($m=-0.32\pm 0.04$) than in the high-pressure regime |
| SFR/HCN pressure threshold | 1.6e6 | not stated | kB K cm^-3 | 9 | with the threshold being at $\ensuremath{\langle P_{\text{DE}}\rangle}_{\rm threshold}=\SI{1.6e6}{\kB\kelvin\per\cubic\centi\metre}$ |
| Pressure thresholds found by MARS in the HCN/CO and SFR/HCN relations | ~4e5 (HCN/CO) and ~1e6 (SFR/HCN) | not stated | kB K cm^-3 | 9 | We find a pressure threshold in both relations (HCN/CO and SFR/HCN) at $\ensuremath{\langle P_{\text{DE}}\rangle}\approx\SI{4e5}{\kB\kelvin\per\cubic\centi\metre}$ and $\ensuremath{\langle P_{\text{DE}}\rangle}\approx\SI{1e6}{\kB\kelvin\per\cubic\centi\metre}$ |
| Correlation of average HCN/CO with <P_DE> | 0.75 | not stated | dimensionless (Pearson rho) | 9 | suggesting that the ISM pressure is well correlated with the average HCN/CO ($\rho=0.75$) over almost three orders of magnitude in pressure |
| Bar SFR/HCN offset below other environments at fixed pressure | ~0.5 | not stated | dex | 9 | the average trend of the bar is $\approx\SI{0.5}{\dex}$ lower compared to the other environments |
| log10(HCN/CO(1-0)) vs log10(Sigma_mol) fit: slope, intercept, scatter | slope 0.61, intercept -2.64, scatter 0.28 | slope 0.10, intercept 0.21 | dimensionless (slope, intercept in dex); scatter in dex | 10 | 0.61 (0.10) / -2.64 (0.21) / 0.28 / 260 / 260 / beam-matched / this work |
| HCN/CO vs Sigma_mol slope with constant alpha_CO | 0.48 | not stated | dimensionless | 10 | using a constant $\alpha_{\text{CO}}$ yields a shallower relation (slope of 0.48) compared to 0.61 with a varying |
| Scatter of 260 pc HCN/CO vs Sigma_mol relation compared with kpc scale | 0.28 versus 0.14 | not stated | dex | 10 | the scatter in the individual 260 sight-line measurements is twice as large (0.28) as the scatter at kpc-scales (0.14) |
| Median R21 and scatter | 0.54 | scatter 0.16 | dimensionless | 4 | Here, we measure a median $R_{21}=0.54$ and a scatter of 0.16. |
| Median spatially varying alpha_CO | 3.3 | scatter 0.10 as stated | Msun pc^-2 (K km/s)^-1 | 4 | The median $\alpha_{\text{CO}}$ value is $\SI{3.3}{\Msun\per\square\parsec}\,(\SI{}{\Kkms})^{-1}$ |
| HCN/HCO+ line ratio, average | ~1.3 (HCN ~30 percent brighter in the central ~1 kpc) | not stated | dimensionless | 0 | HCN is about 30 % brighter than the average line ratio value of $\rm{HCN/HCO}^+\approx 1.3$ |

## Qualitative findings

- Bar ends show enhanced HCN/CO but SFR/HCN similar to the rest of the disc, so cloud-cloud collisions might enhance density but not necessarily change dense gas star formation  
  > "suggesting that collisions might enhance density but not necessarily lead to different processes in the dense gas" (5.2 Normal star formation efficiency in bar ends)
- The SFR/HCN pressure threshold is about one order of magnitude above the simple theoretical estimate  
  > "finding a threshold that is one order of magnitude higher than the value inferred from simple theoretical considerations" (5.1 Pressure threshold for dense gas and star formation)
- Spiral arms and interarm regions have no significant difference in HCN/CO and SFR/HCN  
  > "we find no significant difference of HCN/CO and SFR/HCN between the spiral arms and interarm regions" (6 Conclusions)
- Threshold-like behaviour is seen only against cloud properties, suggesting cloud-scale physics rather than larger-scale environment drives the SFR/HCN threshold  
  > "We find that a threshold-like behaviour is only seen in the cloud property relation" (5.1 Pressure threshold for dense gas and star formation)

## Claim tuples

- H: Do dense gas fraction (HCN/CO) and dense gas star formation efficiency (SFR/HCN) vary with galactocentric position as in kpc-scale surveys? | E: Stacked and sight-line HCN/CO and SFR/HCN at 260 pc versus galactocentric radius and environment, with MARS fits | R: HCN/CO rises and SFR/HCN falls inside 2.0 and 2.8 kpc; both are roughly flat in the disc | F: Galaxy centres have denser clouds that are converted into stars less efficiently than in the disc | **supported**
- H: Is there a pressure threshold for dense gas and star formation? | E: MARS fits of HCN/CO and SFR/HCN versus cloud-scale <P_DE> over a low-pressure regime | R: SFR/HCN flattens at low pressure (threshold about 1e6 kB K cm^-3); HCN/CO is also well fit by a single line | F: Results hint at a pressure threshold below which dense gas star formation decouples from the environment | **partially**
- H: Is star formation from dense gas suppressed in the bar? | E: Compare SFR/HCN and HCN/CO of bar sight lines to disc environments, also versus pressure | R: Bar HCN/CO is similar to the disc but SFR/HCN is much lower, about 0.5 dex below other environments at fixed pressure | F: The bar is much less efficient at converting dense gas into stars, possibly due to shear or streaming motions | **supported**
- H: Does HCN/CO trace the mean molecular gas density at 260 pc as at kpc scales? | E: Stack and fit HCN/CO(1-0) against beam-matched Sigma_mol with varying alpha_CO | R: Slope 0.61 (constant alpha_CO gives 0.48), scatter 0.28 dex, above 10 Msun/pc^2 | F: HCN/CO correlates positively with Sigma_mol, supporting HCN/CO as a tracer of mean cloud density; scale dependence likely related to filling factors | **supported**
- H: Do spiral arms contain denser clouds or convert dense gas to stars more efficiently than interarm regions? | E: Compare HCN/CO and SFR/HCN distributions and stacked means between spiral arms and interarm | R: Comparable HCN/CO and SFR/HCN distributions in spiral arms and interarm regions | F: Spiral arms accumulate gas and have higher pressure but not denser clouds or higher dense gas efficiency | **supported**

## Reasoning

- Why this data: NGC 4321 chosen for earlier HCN detections, ancillary coverage and distance suited to a wide map that still resolves the centre, bar and arms  
  > "as previous ALMA/IRAM mapping showed clear HCN detections, supporting data covers almost all aspects of the ISM and galactic structure" (2.1 The target – NGC 4321)
- Why this method: Binned stacks fitted so that the relation is not dominated by non-detections; MARS used as an objective way to find regime changes  
  > "We fit the stacked data in order to probe the underlying global relation without “population” biases and to not be dominated by non-detections in constraining the best-fit line." (3.8 Stacking and linear regression); "we employ a statistically robust and objective method to find the threshold at which the trends change significantly" (3.8 Stacking and linear regression)
- Alternative: Constant versus spatially varying alpha_CO and R21 tested for the Sigma_mol relation (slope 0.48 versus 0.61)  
  > "using a constant $\alpha_{\text{CO}}$ yields a shallower relation (slope of 0.48) compared to 0.61 with a varying" (4.5 HCN/CO as a density tracer)
- Alternative: A single linear function for HCN/CO versus pressure is also acceptable instead of two regimes  
  > "However, the realtion could also be well fitted with a single linear function with $m=0.35\pm 0.02$." (4.3.1 HCN/CO vs pressure)
- Alternative: 21 um and 33 GHz SFR tracers compared; Halpha kept as primary tracer  
  > "throughout this work we adopt $\text{H}\alpha$ emission as a robust tracer of SFR validated by free-free data in the centre" (3.4 Star formation rate (SFR) – Halpha)
- Alternative: A different constant alpha_HCN (10 instead of 14) would not change results qualitatively  
  > "choosing a different (constant) $\alpha_{\text{HCN}}$ has no qualitative effect on our results" (Footnote 4)
- How they decided it was enough: MARS accepts an extra split point only if chi^2 improves by more than 0.01, with a maximum of two segments  
  > "The algorithm is adapted to only add another split point if a further component significantly improves the fit, meaning that the $\chi^2$ value is improved by more than 0.01." (3.8 Stacking and linear regression)
- Limitation (authors): f_dense estimates are uncertain by a factor of a few because of conversion factors, especially alpha_HCN  
  > "such that our $f_{\text{dense}}$ estimates are expected to be uncertain by a factor of a few" (3.3 Dense gas fraction – HCN/CO)
- Limitation (authors): S/N clipping biases detected-sight-line means towards high HCN/CO and low SFR/HCN  
  > "Since S/N clipping systematically selects luminous HCN regions, these values will be biased towards high HCN/CO and low SFR/HCN" (4.1.1 HCN/CO variations)
- Limitation (authors): Quoted uncertainties exclude calibration and systematic errors  
  > "do not include any calibration or systematic uncertainties" (Table notes (HCN/CO and SFR/HCN statistics))
- Limitation (authors): Single galaxy only  
  > "Further, this work investigates only a single galaxy." (6 Conclusions)
- Limitation (authors): Insufficient sensitivity below Sigma_mol = 10 Msun/pc^2 to test low-surface-density behaviour  
  > "due to a lack of sensitivity below" (4.5 HCN/CO as a density tracer)
- Caveat (inferred, ours): HCN/CO as a density proxy is sensitive to optical depth, excitation and abundance; the alpha_CO prescription and R21 map from 4 arcsec data are model assumptions that enter Sigma_mol and P_DE
- Caveat (inferred, ours): Pressure thresholds from MARS on binned data have no stated uncertainties; the 4e5, 1e6 and 1.6e6 values appear in different places and depend on the P_DE definition (cloud-scale versus 260 pc)
- Caveat (inferred, ours): Same CO(2-1) data enter the x-axis (Sigma_mol, P_DE) and the y-axis (HCN/CO), so correlated errors may bias slopes
- Caveat (inferred, ours): Some numbers are inconsistent between text and tables (e.g. disc HCN/CO correlation rho given as -0.14 in text and -0.03 in the table; centre SFR/HCN uncertainty 0.0001 versus 0.001; centre mean HCN/CO 0.89 versus 0.089; 302 versus 275 detections)
- Caveat (inferred, ours): All results rest on one galaxy and one spectral line, with HCN stacking dependent on a CO velocity prior

## Reproducibility

- Data public (paper): Data stated to be available on reasonable request; ALMA project codes printed in the acknowledgments  
  > "The data used within this paper will be provided on reasonable request to the corresponding author." (Data availability); "ADS/JAO.ALMA#2017.1.00815.S" (Acknowledgements)
- Products in archive: _not stated_
- Code: PyStacker (PHANGS team) is on GitHub; no release of this paper's own analysis scripts is stated  
  > "https://github.com/PhangsTeam/PyStacker" (Footnote 5)
- Missing: Imaging and calibration parameters of the HCN cube (only the PHANGS-ALMA pipeline is cited, no CASA version or tclean settings)
- Missing: Exact bin edges, S/N masks and MARS/LinMix settings used for the stacks and fits
- Missing: Specific versions of PHANGS-MUSE, PHANGS-JWST and PHANGS-ALMA CO products and the Querejeta et al. maps
- Missing: Code and scripts for the P_DE and alpha_CO iteration beyond the equations given
- Data volume (inferred): Raw ALMA data for 12-m, ACA 7-m and TP (216.7 h over four 1.875 GHz windows at 976 kHz) likely hundreds of GB to ~1 TB; processed HCN cube and ancillary maps a few GB (inferred)
- Score (inferred): 3/5, Equations, conversion factors and fit settings are given for most of the analysis and key numbers are listed, but the ALMA imaging relies on the cited PHANGS-ALMA pipeline without parameters and several external products and fit settings are unspecified.
- Rediscovery candidate: no, The paper states data are available on request and the HCN imaging, ancillary product versions, bin edges and fit settings are not specified, so the recipe is not complete enough to redo from the paper alone.

## Links

- Method: (cite: Leroy2021a) (PHANGS-ALMA pipeline used to reduce the HCN data)
- Method: (cite: Neumann2023a) (ALMOND survey; masking, moment-0 and cloud-scale property methodology reused)
- Method: (cite: Sun2020a) (Dynamical equilibrium pressure formalism)
- Method: (cite: Neumann2023b) (PyStacker spectral stacking method)
- Method: (cite: Friedman1991) (MARS regression)
- Method: (cite: Sun2022) (Iterative alpha_CO solution)
- Method: (cite: Bolatto2013) (alpha_CO prescription)
- Companion: (cite: Leroy2021b) (PHANGS-ALMA CO(2-1) data used as the bulk gas tracer)
- Companion: (cite: Emsellem2022) (PHANGS-MUSE Halpha used for SFR)
- Companion: (cite: Lee2023) (PHANGS-JWST 21 um data)
- Companion: (cite: Querejeta2021) (Morphological environment masks)
- Companion: (cite: Jimenez-Donaire2019) (EMPIRE kpc-scale dense gas survey)
- Companion: (cite: Gallagher2018b) (kpc-scale HCN/CO and SFR/HCN versus cloud-scale properties)
- Related: PHANGS-ALMA
- Related: PHANGS-MUSE
- Related: PHANGS-JWST
- Related: ALMOND
- Related: EMPIRE
- Related: CLAWS
- Related: HERACLES
- Related: S4G

## Checks

```json
{
 "quotes": 187,
 "quotes_ok": 187,
 "quote_pass_rate": 1.0,
 "quotes_too_long": 0,
 "unsupported_facts": 0,
 "project_codes": 3,
 "codes_not_in_text": [],
 "codes_not_in_obscore": [],
 "obscore_codes_not_in_card": [],
 "codes_printed_but_missing": [],
 "numeric_results": 27,
 "numeric_problems": 0,
 "fill": {
  "facts": 144,
  "stated": 108,
  "rate": 0.75
 },
 "evidence_ok": true
}
```
