# Volatile composition of the HD 169142 disc and its embedded planet

`2024MNRAS.534.3576K` | Monthly Notices of the Royal Astronomical Society 2024 | first author: Keyte, Luke | arXiv: 2410.01418 | DOI: 10.1093/mnras/stae2314

Card schema 1.0 | model claude-sonnet-5-5-claude-code | depth light | type theory_or_simulation_compared_to_alma

## Science

- Fields: protoplanetary_disks, astrochemistry, exoplanets
- Question: What are the gas-phase elemental C, O and S abundances (and C/O) in the HD 169142 disk, how do the sulfur-bearing molecules (incl. SiS) relate to the embedded protoplanet HD 169142 b, and what is the composition of gas the planet may accrete  
  > "Our aim is to determine the gas-phase abundance of elemental carbon, oxygen, and sulfur at the small spatial scales relevant to planet formation." (Introduction)
- Target **HD 169142**: coordinates _not stated_; z/distance d = 115 pc  
  > "HD is a well-studied nearby Herbig Ae star located at a distance of $d=115$ pc" (2.1 The HD disk); "assuming a source distance of $d=115$ pc (cite: bailer_jones_2021)" (6.4 Linking the SiS emission to a circumplanetary disk); distance from Gaia-based distance (cite: bailer_jones_2021)  
  > "HD is a well-studied nearby Herbig Ae star located at a distance of $d=115$ pc" (2.1 The HD disk); "assuming a source distance of $d=115$ pc (cite: bailer_jones_2021)" (6.4 Linking the SiS emission to a circumplanetary disk)

## Data provenance

- ALMA projects: 2017.1.00727.S, 2012.1.00799.S, 2016.1.00344.S, 2015.1.00806.S, 2016.1.00346.S, 2018.1.01237.S
- bands: Continuum at 0.45, 0.89 and 1.3 mm; lines at ~220-670 GHz  
  > "high-resolution continuum observations from ALMA at 0.45 mm (cite: leemker_2022), 0.89 mm (cite: law_2023), and 1.3 mm (cite: garg_2022)" (2.2 Archival data)
- frequencies and spectral setup: Continuum 670.5837, 331.0, 225.0 GHz; line frequencies listed per transition in Table 1  
  > "670.583700" (Table 1); "331.000000" (Table 1); "225.000000" (Table 1)
- continuum bandwidth: _not stated_
- arrays: ALMA 12m array  
  > "ALMA 12m array" (Table 1)
- configurations: _not stated_
- baselines: _not stated_
- angular resolution: Beams per dataset in Table 1; e.g. C18O 2-1 0.07"x0.06" (~8 au); CS/13CS/H2CS beams ~80 au (large)  
  > "higher resolution data used here ($0.07" \times 0.06" \sim 8$ au)" (3.1 Baseline model); "The large beam size ($\sim80$ au) limits our ability to precisely constrain the C/O ratio in the inner disk beyond an upper limit of $<1$." (CS/SO ratio)
- max recoverable scale: _not stated_
- sensitivity: _not stated_
- time on source: _not stated_
- observing dates: _not stated_
- pi or archival as stated: Archival ALMA data from six programmes (PIs M. Honda, J. Pineda, S. Perez, J. Szulagyi, T. Tsukagoshi, E. Macias per Table 1)  
  > "In this study, we make use of a wealth of archival data." (2.2 Archival data); "The data presented in this work are from various programmes detailed in Table" (Data Availability)
- Line: CO J=2-1 (230.538000 GHz)
- Line: CO J=3-2 (345.795990 GHz)
- Line: 13CO J=2-1 (220.398684 GHz)
- Line: 13CO J=3-2 (330.587965 GHz)
- Line: 13CO J=6-5 (661.067277 GHz)
- Line: C18O J=2-1 (219.560354 GHz)
- Line: [CI] 3P1-3P0 (492.160651 GHz)
- Line: CS J=10-9 (489.750921 GHz)
- Line: 13CS J=6-5 (277.455405 GHz)
- Line: SO J=8_8-7_7 (344.310612 GHz)
- Line: H2CS J=8_{1,7}-7_{1,6} (278.887661 GHz)
- Line: SiS J=19-18 (344.779481 GHz)
- Other facility **Herschel/PACS**: Disk-integrated HD 56/112 um fluxes and upper limits, and [OI] 63/146 um fluxes (gas mass and O/H constraints)  
  > "from Herschel/PACS (cite: meeus2012; kama_2020)" (2.2 Archival data)
- Other facility **VLT/SPHERE**: Planet mass estimate Mp = 2.2 MJup used in CPD and accretion-zone calculations  
  > "based on estimates from observations with SPHERE (cite: gratton_2019)" (6.4 Linking the SiS emission to a circumplanetary disk)
- External data: Disk structure parameters used as the starting point of the DALI model  
  > "In this work, we use the disk parameters from (cite: fedele_2017) and (cite: carney_2018) as our starting point for refining the model." (3 Modelling) [from (cite: fedele_2017); (cite: carney_2018)]
- External data: Stellar effective temperature T*=8400 K  
  > "$T_*=8400$ K (cite: dunkin_1997)" (2.1 The HD disk) [from (cite: dunkin_1997)]
- External data: X-ray spectrum assumed from similar Herbig Ae/Be systems  
  > "based on observations of similar Herbig Ae/Be systems (cite: stelzer_2006)" (3.2 Stellar parameters) [from (cite: stelzer_2006)]
- External data: CO isotopologue chemical network  
  > "we employ the CO isotopologue network from (cite: miotello_2016), which is based on a subset of the UMIST 06 (cite: woodall2007) network" (3.3 Chemical networks) [from (cite: miotello_2016); (cite: woodall2007)]
- External data: Sulfur chemical network  
  > "we use the network from (cite: keyte_2023) to model the sulfur-bearing species" (3.3 Chemical networks) [from (cite: keyte_2023)]
- External data: Observed CS and SO radial column densities and CS/SO ratio profile  
  > "derived the CS/SO ratio for this disk by calculating the CS and SO radial column densities, assuming a fixed temperature of 60 K" (5.3 CS/SO ratio) [from (cite: booth_2023b)]
- External data: Molecular spectroscopic data (Einstein A, partition functions)  
  > "taken from the Cologne Database for Molecular Spectroscopy (CDMS)" (6.3 Linking the SiS emission to a circumplanetary disk) [from (cite: CDMS_muller_2001; muller_2005; endres_2016)]
- External data: Upper state energy levels  
  > "taken from the Leiden Atomic and Molecular Database (LAMDA)" (6.3 Linking the SiS emission to a circumplanetary disk) [from (cite: LAMDA_schoier_2005; klos_lique_2008)]
- External data: SiS line width of 6 km/s  
  > "Taking the linewidth to be $\Delta \nu = 6$ km/s (cite: law_2023)" (6.3 Linking the SiS emission to a circumplanetary disk) [from (cite: law_2023)]
- Simulation/model as data: DALI 2D thermochemical disk models with parameterised gas and dust structure, run to 5 Myr  
  > "We ran source-specific models using the 2D physical-chemical code DALI" (3 Modelling); "We let the chemistry evolve to 5 Myr, consistent with recent age estimates for the system" (3 Modelling)
- Simulation/model as data: Simulated ALMA observations of the composite model cubes with simobserve/simanalyze  
  > "to create simulated ALMA observations, using parameters matching the observations" (4.2 CS, 13CS, SO, and H2CS modelling)

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

- Disk structure parameters from earlier DALI models  
  > "we use the disk parameters from (cite: fedele_2017) and (cite: carney_2018) as our starting point for refining the model" (3 Modelling) [from (cite: fedele_2017); (cite: carney_2018)]
- Model fitting procedure  
  > "Our fitting procedure follows the approach of (cite: Kama2016b) and (cite: keyte_2023)." (4.1 Baseline model) [from (cite: Kama2016b); (cite: keyte_2023)]
- Sulfur network validation against full RATE 12 gas-phase network  
  > "(see (cite: keyte_2024) for full details)" (3.3 Chemical networks) [from (cite: keyte_2024)]
- CPD temperature profile approach  
  > "We follow a similar approach to (cite: isella_2014) and (cite: keppler_2019)" (6.3 Linking the SiS emission to a circumplanetary disk) [from (cite: isella_2014); (cite: keppler_2019)]
- Column density with optical depth correction  
  > "by following a similar approach to e.g. (cite: Loomis_2018)" (6.3 Linking the SiS emission to a circumplanetary disk) [from (cite: Loomis_2018)]
- Planet accretion region (1-3 scale heights, to Bondi or Hill radius)  
  > "Following (cite: cridland_2020), we can approximate the region of the disk from which gas is accreted" (6.4 Composition of planet-accreted gas) [from (cite: cridland_2020)]

### Not stated but needed to reproduce (our reading)

- Calibration, imaging and continuum-subtraction details for all six ALMA datasets (the paper relies on the cited papers' products and gives no pipeline, CASA version, robust, uv-taper or self-calibration)
- How radial intensity profiles were extracted from the observed cubes (moment maps, deprojection geometry, annuli, noise treatment)
- DALI version and the t_chem entry of the parameter table (left blank); the radial grid and the exact grid steps used
- Goodness-of-fit criterion for choosing the best-fit model (comparison appears to be by eye; no likelihood or chi-square given)
- Exact C/O values of the inner and outer zones of each composite model beyond the stated 0.5 inner and elevated outer values
- Spatial positions and shapes of the beam-sized apertures used for SiS flux (7.5 mJy km/s) and the exact molecular constants used

## Analysis recipe

1. **Constrain the dust distribution**: Joint fit of the SED and high-resolution continuum observations with a grid of DALI models  
  > "We begin by constraining the dust distribution by jointly fitting the spectral energy distribution and high-resolution continuum observations." (4.1 Baseline model)
   - software: DALI
   - parameter: Grid of ~2500 models varying psi, h_c, Delta_g/d, chi, f, plus dust ring locations and gap depletion  
  > "Using a grid of $\sim2500$ models, we vary the parameters" (4.1 Baseline model); "We also include variations in the parameters that define the radial location of the dust rings and the level of dust depletion within the gaps." (4.1 Baseline model)
   - assumption: Gas surface density fixed at an arbitrary value so Delta_g/d changes only change dust mass  
  > "is kept fixed at an arbitrary value such that changes to $\Delta_\text{g/d}$ are equivalent only to changes in the dust mass." (4.1 Baseline model)
   - fitting: _not stated_
   - validation: Match to SED and 0.89 mm continuum radial profile  
  > "The model provides an excellent match to the spectral energy distribution and 0.89mm continuum radial intensity profile" (4.1 Baseline model)
2. **Constrain gas mass / gas-to-dust ratio**: Second grid varying Sigma_gas and Delta_g/d at fixed dust mass, compared with HD 56 and 112 um upper limits  
  > "Our model grid covers gas-to-dust ratios ranging from 10 to 500, but the HD upper limits are not tight enough to provide any useful constraint." (4.1 Baseline model)
   - software: DALI
   - assumption: Interstellar gas-to-dust ratio of 100 adopted  
  > "From this point on, we therefore adopt the interstellar value of" (4.1 Baseline model)
   - fitting: _not stated_
   - validation: _not stated_
3. **Constrain total elemental C and O and gas depletion**: DALI grids compared to CO isotopologue and [CI] radial intensity profiles and [OI] disk-integrated fluxes, starting with C18O 2-1  
  > "We focus initially on fitting the C$^{18}$O $J=2-1$ radial intensity profile, since this line is expected to be the most optically thin" (4.1 Baseline model); "We run models covering a range of C/O ratios (C/O = 0.3 to 1.1), and total elemental carbon and oxygen abundances (C/H and O/H between $2 \times 10^{-5}$ and $2 \times 10^{-4}$)." (4.1 Baseline model)
   - software: DALI
   - parameter: C/O 0.3-1.1; C/H and O/H 2e-5 to 2e-4; fiducial C/O=1.0, C/H=1e-4  
  > "Adopting C/O $=1.0$ and C/H $=1\times 10^{-4}$ as fiducial values" (4.1 Baseline model)
   - assumption: CO isotopologue network with isotope-selective photodissociation  
  > "allowing us to take into account the effects of isotope-selective photodissociation" (3.3 Chemical networks)
   - fitting: _not stated_
   - validation: C18O 2-1 intensity matched; 12CO/13CO peak overpredicted by factor <~1.5, attributed to too-hot modelled atmosphere  
  > "Consistent overprediction of the $^{12}$CO and $^{13}$CO emission suggests that the modelled gas temperature in the disk atmosphere, from where these species mainly emit, is too high." (4.1 Baseline model)
4. **Constrain total gas-phase sulfur abundance**: Sulfur-network DALI grid compared to CS, 13CS, SO and H2CS radial intensity profiles at fixed C/H  
  > "we ran models covering a wide range of initial sulfur abundances (S/H $=10^{-12}$ to $10^{-5}$) and C/O ratios (0.3 to 1.1)" (4.2 CS, 13CS, SO, and H2CS modelling)
   - software: DALI
   - parameter: S/H 1e-12 to 1e-5; C/O 0.3-1.1; C/H fixed at 1e-4; SiS treated separately  
  > "In each case, the total elemental carbon abundance was fixed at the fiducial value C/H = $1\times 10^{-4}$." (4.2 CS, 13CS, SO, and H2CS modelling)
   - fitting: _not stated_
   - validation: Peak fluxes matched but morphology poorly reproduced by single C/O  
  > "they provide a poor match to the morphology of the individual radial intensity profiles" (4.2 CS, 13CS, SO, and H2CS modelling)
5. **Build composite radially varying C/O model and mock ALMA observations**: Two radial zones with different C/O (varied via O/H), split at 56 au; composite cubes passed through simobserve/simanalyze and collapsed to moment-0  
  > "we divide the disk into two radial regions; an inner region in which the C/O ratio is approximately solar (C/O=0.5), and an outer region in which the C/O region is elevated." (4.2 CS, 13CS, SO, and H2CS modelling); "The processed cubes were collapsed to generate moment-zero integrated intensity maps" (4.2 CS, 13CS, SO, and H2CS modelling)
   - software: DALI, CASA (simobserve, simanalyze)
   - parameter: Splice point at inner edge of outer dust ring (r=56 au); anywhere in the gap 32-56 au gives similar results  
  > "the division point between the two regions is set to the inner edge of the outer dust ring ($r=56$ au)" (4.2 CS, 13CS, SO, and H2CS modelling)
   - assumption: C/O variation driven only by O/H, C/H fixed at 1e-4  
  > "Variations in C/O are driven solely by variations in the oxygen abundance" (4.2 CS, 13CS, SO, and H2CS modelling)
   - fitting: _not stated_
   - validation: Qualitative morphological comparison of model and mock-observed moment maps  
  > "the emission from species in the composite model provide a close morphological match to the observations" (4.2 CS, 13CS, SO, and H2CS modelling)
6. **Compare modelled and observed CS/SO column-density ratio**: Extract CS and SO radial column densities from models, convolve to the CS beam, compare N(CS)/N(SO) with literature observed values  
  > "We extracted CS and SO radial column densities from a range of models spanning C/O = 0.3 to 1.1." (5.3 CS/SO ratio); "We then convolved both column densities to the same angular resolution, matching the beam size of the CS observation" (5.3 CS/SO ratio)
   - software: DALI
   - parameter: S/H fixed at 4e-8  
  > "the initial gas-phase sulfur abundance was fixed at S/H = $4 \times 10^{-8}$" (5.3 CS/SO ratio)
   - fitting: _not stated_
   - validation: S/H increase by 10x changes CS/SO by less than a factor of 1.5  
  > "typically altering the CS/SO ratio by less than a factor of 1.5 for a factor 10 increase in S/H" (5.3 CS/SO ratio)
7. **Compare modelled SiS 19-18 to observed hotspot flux**: Collapse DALI SiS cube to a moment-0 map, convolve to the observed beam, measure flux near the planet, then raise Si/H and S/H together to cosmic values  
  > "We then extract an SiS $J=19-18$ image cube from the DALI model, collapse it to produce an integrated intensity map, and convolve it with the same beam size as the observations." (5.4 SiS modelling)
   - software: DALI
   - parameter: Si/H and S/H raised in lockstep following cosmic ratio, then Si/H alone to cosmic  
  > "We increase both Si/H and S/H in lockstep, following the ratio of their cosmic abundances" (5.4 SiS modelling)
   - fitting: _not stated_
   - validation: _not stated_
8. **Estimate SiS emitting area and test circumplanetary-disk heating**: Optically thick emitting area from Omega = F/(B_nu(T) Delta nu); CPD temperature from stellar, planet and accretion heating terms; column density with optical-depth correction  
  > "We begin by assuming that the emission is optically thick, such that the intensity of the emission at the line center is given by:" (6.3 Linking the SiS emission to a circumplanetary disk); "where $\tau$ is the optical depth, which we set to $\tau=1$ to approximate optically thick emission." (6.3 Linking the SiS emission to a circumplanetary disk)
   - software: CDMS, LAMDA
   - parameter: Delta nu = 6 km/s; d = 115 pc; T = 20-3000 K; Mp = 2.2 MJ, Rp = 2 RJ; sublimation T ~1500 K  
  > "Figure [\[fig_cpd_size\]](#fig_cpd_size) (top panel) shows how the emitting area of the gas varies for temperatures $20-3000$ K." (6.3 Linking the SiS emission to a circumplanetary disk); "we can use the grain sublimation temperature ($\sim 1500$ K) to place an upper limit on emitting area" (6.3 Linking the SiS emission to a circumplanetary disk)
   - assumption: LTE, optically thick emission, 100 K for accretion-shock gas, CPD aspect ratio 0.1  
  > "Taking 100 K as a representative value for gas in a CPD accretion shock (cite: schulik_2020)" (6.3 Linking the SiS emission to a circumplanetary disk)
   - fitting: _not stated_
   - validation: Compared with Law et al. column density 4.5+-0.7e13 cm^-2  
  > "This is consistent with the column density of $4.5 \pm 0.7 \times 10^{13}$ cm$^{-2}$ determined by (cite: law_2023)" (6.3 Linking the SiS emission to a circumplanetary disk)
9. **Derive C/O of gas in planet feeding zone**: Average modelled gas-phase C/O between 1 and 3 scale heights out to the smaller of the Bondi and Hill radii  
  > "We calculate the average C/O of the gas between one and three scale heights for both models." (6.4 Composition of planet-accreted gas)
   - software: DALI
   - parameter: Mp = 2.2 MJ; Bondi radius 2.6 au adopted as accretion radius  
  > "and therefore adopt $R_\text{B} = 2.6$ au as the accretion radius." (6.4 Composition of planet-accreted gas)
   - assumption: Planet accretes from upper layers via meridional flows  
  > "newly-forming planets may infact accrete most of their gas from upper layers of the disk atmosphere via meridional flows" (6.4 Composition of planet-accreted gas)
   - fitting: _not stated_
   - validation: _not stated_

## Software

- **DALI** : 2D thermochemical disk modelling, Monte Carlo radiative transfer, time-dependent chemistry and ray tracing  
  > "We ran source-specific models using the 2D physical-chemical code DALI" (3 Modelling)
- **CASA (simobserve, simanalyze)** : Simulated ALMA observations of the composite model cubes  
  > "to create simulated ALMA observations, using parameters matching the observations" (4.2 CS, 13CS, SO, and H2CS modelling)
- **STARCHEM** : Full RATE 12 gas-phase network model used to test the sulfur network (previous work)  
  > "using the STARCHEM modelling code" (3.3 Chemical networks)
- **CDMS** : Line frequencies, Einstein A coefficients and partition functions  
  > "taken from the Cologne Database for Molecular Spectroscopy (CDMS)" (6.3 Linking the SiS emission to a circumplanetary disk)
- **LAMDA** : Upper state energy levels  
  > "taken from the Leiden Atomic and Molecular Database (LAMDA)" (6.3 Linking the SiS emission to a circumplanetary disk)

## Numeric results

| quantity | value | uncertainty | units | step | quote |
|---|---|---|---|---|---|
| Inner dust ring extent in best-fit model | 21 to 32 au | not stated | au | 1 | extending from 21 to 32 au, rather than 20 to 35 au |
| Total elemental C/H and O/H (approximate) | ~1e-4 (approximately full interstellar abundance) | not stated | dimensionless | 3 | (C/H and O/H $\sim 10^{-4}$ i.e. approximately the full interstellar abundance) |
| Best-fit gas depletion factor in the dust/gas gap | 0.02 | not stated | dimensionless | 3 | we find a best-fitting gas depletion factor of $\delta_\text{gas.gap}=0.02$ |
| Gas-phase elemental sulfur abundance S/H | ~4e-8 | not stated | dimensionless | 4 | with a best-fit modelled abundance of S/H$\sim4 \times 10^{-8}$ |
| Sulfur depletion from gas phase relative to cosmic | ~1000 (about 3 orders of magnitude) | not stated | dimensionless | 4 | In contrast to carbon and oxygen, elemental sulfur is heavily depleted from the gas phase by a factor of $\sim 1000$. |
| Outer-disk C/O best matching observed CS/SO | 0.9 (close to but not exceeding unity) | not stated | dimensionless | 6 | The observed profile is best fit with a model using C/O=0.9 |
| Observed SiS 19-18 flux near planet vs model flux | ~7.5 mJy km/s observed vs ~1e-10 mJy km/s model | not stated | mJy km/s | 7 | ($\sim7.5$ mJy km/s compared to $\sim 10^{-10}$ mJy km/s) |
| SiS model shortfall with cosmic Si and S gas abundances | ~5 orders of magnitude | not stated | orders of magnitude | 7 | the modelled SiS $J=19-18$ emission is still $\sim5$ orders of magnitude lower that the observed value |
| Upper limit on SiS emitting radius (optically thick, 1500 K) | ~0.2 au | not stated | au | 8 | which we find to be $r \sim 0.2$ au in the optically thick regime |
| Accretion rate needed for 1500 K at 0.2 au in CPD | >~1e-4 | not stated | Msun/yr | 8 | a mass accretion rate of $\gtrsim 10^{-4} M_\odot$ yr$^{-1}$ is required to produce a temperature of $1500$ K at 0.2 au |
| SiS total column density, optically thick, r=0.75 au, T=100 K | 6.2e16 | not stated | cm^-2 | 8 | we find $N_\text{tot} = 6.2 \times 10^{16}$ cm$^{-2}$ for optically thick emission |
| SiS column density, optically thin, beam-sized area | ~5.5e13 | not stated | cm^-2 | 8 | the observed emission intensity can be reproduced using a column density $\sim 5.5 \times 10^{13}$ cm$^{-2}$ if the emitting area is comparable to the size of the synthesised beam |
| Gas-phase C/O in planet accretion zone | >~0.73 | not stated | dimensionless | 9 | we can infer that the gas in planet feeding zone has C/O$\gtrsim0.73$ |
| Fraction of volatile molecular sulfur in ices | ~99.5% | not stated | percent | 5 | Approximately 99.5% of molecular volatile sulfur is sequestered in ices, leaving $\sim$0.5% available for gas-phase chemistry. |

## Qualitative findings

- CS, SO and H2CS morphology is reproduced only with radially varying C/O (solar inside, elevated outside)  
  > "The emission morphology of sulfur-bearing species CS, SO, and H$_2$CS can only be reproduced when our models incorporate a radial variation in the C/O ratio" (7 Conclusions)
- SO abundance rises with C/O up to C/O=1 as less oxygen is available for SO2, so CS/SO2 is a more sensitive tracer than CS/SO  
  > "We show that the SO abundance can infact increase with increasing C/O (up to C/O=1)" (7 Conclusions)
- SiS emission is unlikely to result solely from sublimation in a circumplanetary disk but may trace infalling shocked gas  
  > "We show analytically that the emission is unlikely to result solely from sublimation in a circumplanetary disk, but may be tracing infalling shocked gas." (7 Conclusions)

## Claim tuples

- H: Are carbon and oxygen strongly depleted from the gas in the HD 169142 disk, as in many other disks | E: DALI grids fit to C18O, other CO isotopologue, [CI] and [OI] data | R: C/H and O/H ~1e-4, approximately the full interstellar abundance | F: Carbon and oxygen are at most moderately depleted | **supported**
- H: How depleted is gas-phase sulfur | E: Sulfur-network DALI grids fit to CS, 13CS, SO, H2CS radial profiles | R: S/H ~4e-8, ~3 orders of magnitude below cosmic | F: Sulfur is highly depleted from the gas phase, similar to other disks | **supported**
- H: Can a single disk-wide C/O explain the sulfur-molecule emission morphology | E: Varied C/O and S/H, then built composite two-zone C/O models, and compared with mock ALMA images | R: Only radially varying C/O (solar inside, elevated outside, split in the 32-56 au gap) improves all four species | F: C/O is elevated in the outer disk and approximately solar in the inner disk, suggesting inward oxygen transport as midplane ices | **partially**
- H: Is the SiS emission near HD 169142 b background disk chemistry | E: Compared DALI SiS flux with observed beam flux, raised Si and S to cosmic, and estimated emitting area and CPD temperature | R: Observed SiS exceeds the model by many orders of magnitude (~5 even at cosmic Si and S); CPD heating needs unphysical accretion rates | F: SiS is enhanced by planet-related processes, likely shocked gas or a localised outflow rather than CPD sublimation alone | **supported**
- H: What is the C/O of gas near and accreted by the protoplanet | E: Averaged modelled gas-phase C/O in the accretion region of the composite models | R: C/O ~0.73 to ~1.0 in the accretion region | F: Gas near the planet likely has C/O above solar (>~0.73) | **partially**

## Reasoning

- Why this data: High-resolution archival ALMA lines and continuum plus Herschel constrain elemental abundances at small spatial scales  
  > "In this paper, we present thermochemical models of this system, which are constrained using a range of high-resolution archival data." (Introduction)
- Why this method: SiS is modelled separately because its emission is thought to trace planet-related shocks; a radial C/O composite is motivated by literature on enhanced outer-disk C/O and inward ice drift  
  > "We opt to treat the SiS separately in the next section, since the emission is thought to be tracing shocks in the vicinity of a protoplanet" (4.2 CS, 13CS, SO, and H2CS modelling); "This is motivated by an increasing number of studies which suggest high levels of carbon/oxygen depletion and enhanced C/O ratios in the outer regions of protoplanetary disks" (4.2 CS, 13CS, SO, and H2CS modelling)
- Alternative: Radially varying S/H instead of C/O was tried and cannot fit all species at once  
  > "It is not possible to simultaneously balance the emission morphology of the CS, $^{13}$CS, SO, and H$_2$CS profiles in this manner." (4.2 CS, 13CS, SO, and H2CS modelling)
- Alternative: Varying stellar luminosity, temperature, X-ray spectrum or disk structure to fix 12CO/13CO overprediction was rejected because of the SED fit  
  > "varying each of these parameters was found to significantly impact the SED fit for only minimal variations in the $^{12}$CO and $^{13}$CO emission" (4.1 Baseline model)
- Alternative: SiS from CPD accretion-heating sublimation alone was rejected as requiring unphysical accretion rates  
  > "Our initial assessment therefore suggests that the SiS emission cannot solely be due to Si sublimation induced by accretion heating in the circumplanetary disk." (6.3 Linking the SiS emission to a circumplanetary disk)
- How they decided it was enough: _not stated_
- Limitation (authors): Modelled 0.45 mm and 1.3 mm continuum fluxes cannot be improved simultaneously  
  > "we were unable to simultaneously decrease the 0.45mm continuum flux while increasing the 1.3mm flux" (4.1 Baseline model)
- Limitation (authors): Single best-fit C/H and O/H is hard to define; optically thick CO lines are overpredicted  
  > "Determining best-fitting values for C/H and O/H is challenging." (4.1 Baseline model)
- Limitation (authors): Models poorly reproduce the radial morphology of individual sulfur species  
  > "they provide a poor match to the morphology of the individual radial intensity profiles" (4.2 CS, 13CS, SO, and H2CS modelling)
- Limitation (authors): Large beam limits inner-disk C/O constraint; splice radius not constrained within the gap  
  > "The large beam size ($\sim80$ au) limits our ability to precisely constrain the C/O ratio in the inner disk beyond an upper limit of $<1$." (5.3 CS/SO ratio)
- Limitation (authors): CPD temperature treatment is not fully self-consistent  
  > "This treatment is not entirely self-consistent" (6.3 Linking the SiS emission to a circumplanetary disk)
- Caveat (inferred, ours): Best fits are judged by eye on radial profiles with no formal likelihood or uncertainty on S/H, C/H, O/H or C/O
- Caveat (inferred, ours): Many parameters (distance, stellar properties, dust opacities, grain-size distribution, planet properties) are fixed from the literature and their uncertainties are not propagated
- Caveat (inferred, ours): Archival ALMA data reduction is not described, so profile extraction and flux scale systematics are unchecked
- Caveat (inferred, ours): The spliced two-zone composite model is ad hoc and not self-consistent (the C/O step location is unconstrained)
- Caveat (inferred, ours): CS and SO abundance mismatches and optically thick CO overprediction suggest the thermal structure may be wrong, which would affect all derived abundances

## Reproducibility

- Data public (paper): Raw ALMA data public in the ALMA archive  
  > "The raw ALMA data is publicly available from the ALMA archive." (Data Availability)
- Products in archive: _not stated_
- Missing: Version and settings of DALI (not said to be public in the paper) and the full model input files, including t_chem
- Missing: ALMA data reduction and imaging recipes and the radial profile extraction method
- Missing: Fit criterion and the exact model grids behind the quoted best fits
- Missing: Observed SiS flux aperture definition and CDMS/LAMDA molecular constants used
- Data volume (inferred): Raw data for six ALMA projects likely hundreds of GB; reproducing the models needs DALI runs, not large data
- Score (inferred): 3/5, Raw ALMA data and a full fiducial parameter table are public, but data reduction is not described, DALI input and version are not given, the fits are by eye, and many numeric results are approximate.
- Rediscovery candidate: no, The central results come from DALI thermochemical modelling with by-eye fits and approximate numbers, and the ALMA processing recipe is not given.

## Links

- Method: (cite: Bruderer2012); (cite: Bruderer2013) (DALI code description)
- Method: (cite: keyte_2023) (Sulfur chemical network and fitting approach)
- Method: (cite: Kama2016b) (Fitting procedure for disk elemental abundances)
- Method: (cite: miotello_2016) (CO isotopologue chemical network)
- Companion: (cite: law_2023) (SiS, SO and CO data and the protoplanet shock interpretation)
- Companion: (cite: booth_2023b) (CS/SO ratio and [CI], CS, 13CS, H2CS observations)
- Companion: (cite: keyte_2024) (Previous sulfur chemistry modelling of the system)
- Companion: (cite: garg_2022) (1.3 mm continuum and CO isotopologue data)
- Companion: (cite: leemker_2022) (0.45 mm continuum and 13CO 6-5 data)
- Companion: (cite: fedele_2017); (cite: carney_2018) (Previous DALI models used as starting point)
- Related: MAPS ALMA Large Program (comparison)
- Related: Herschel DIGIT and GASPS programmes

## Checks

```json
{
 "quotes": 129,
 "quotes_ok": 129,
 "quote_pass_rate": 1.0,
 "quotes_too_long": 0,
 "unsupported_facts": 0,
 "project_codes": 6,
 "codes_not_in_text": [],
 "codes_not_in_obscore": [],
 "obscore_codes_not_in_card": [],
 "codes_printed_but_missing": [],
 "numeric_results": 14,
 "numeric_problems": 0,
 "fill": {
  "facts": 119,
  "stated": 75,
  "rate": 0.63
 },
 "evidence_ok": true
}
```
