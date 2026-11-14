# Dust, Gas, and Metal Content in Star-forming Galaxies at z ∼ 3.3 Revealed with ALMA and Near-IR Spectroscopy

`2021ApJ...908...15S` | The Astrophysical Journal 2021 | first author: Suzuki, Tomoko L. | arXiv: 2012.09447 | DOI: 10.3847/1538-4357/abd4e7

Card schema 1.0 | model claude-sonnet-5-5-claude-code | depth full | type observational_alma_primary

## Science

- Fields: high_z_galaxies
- Question: How large are the dust and gas contents (gas mass fraction, depletion time) of star-forming galaxies at z~3-4 with known metallicities, and what do they say about interaction with the IGM through inflows and outflows  
  > "Comparing the gas contents with the gas-phase metallicities, we aim to understand how star-forming galaxies at this epoch interact with their surrounding IGM via gas inflows and outflows." (Introduction)
- Target **Sample of 12 star-forming galaxies in COSMOS (IDs 208681, 214339, 406444, 3, 434585, 192129, 217753, 218783, 212298, 413391, 5, 434618)**: coordinates per-galaxy R.A./DEC. in degrees given in Table 1 (COSMOS field)  
  > "the sample for the ALMA observations consists of 12 galaxies, two of which are" (2.2 ALMA Band-6 observation); "in the COSMOS field using NIR spectroscopy with Keck/MOSFIRE." (2.1 Spectroscopically confirmed galaxies at z=3-4); z/distance spectroscopic redshifts 3.108-3.609 (Table 1); flat cosmology Omega_m=0.3, Omega_Lambda=0.7, H0=70  
  > "the sample for the ALMA observations consists of 12 galaxies, two of which are" (2.2 ALMA Band-6 observation); "in the COSMOS field using NIR spectroscopy with Keck/MOSFIRE." (2.1 Spectroscopically confirmed galaxies at z=3-4); distance from Keck/MOSFIRE NIR spectroscopy from earlier parent-sample papers (cite: onodera16; suzuki17)  
  > "the sample for the ALMA observations consists of 12 galaxies, two of which are" (2.2 ALMA Band-6 observation); "in the COSMOS field using NIR spectroscopy with Keck/MOSFIRE." (2.1 Spectroscopically confirmed galaxies at z=3-4)
- Target **208681 (brightest source at 1.3 mm)**: coordinates see Table 1  
  > "The brightest source at 1.3 mm, 208681, appears to be detected with the CO(9–8) line." (2.2 ALMA Band-6 observation); z/distance z_spec = 3.267 (Table 1)  
  > "The brightest source at 1.3 mm, 208681, appears to be detected with the CO(9–8) line." (2.2 ALMA Band-6 observation); distance from Keck/MOSFIRE spectroscopy (cite: onodera16; suzuki17)  
  > "The brightest source at 1.3 mm, 208681, appears to be detected with the CO(9–8) line." (2.2 ALMA Band-6 observation)
- Target **192129 (X-ray detected type-2 AGN, kept in sample)**: coordinates see Table 1  
  > "included in the X-ray-selected AGN catalog of (cite: kalfountzou14) as a type-2 AGN." (2.2 ALMA Band-6 observation); z/distance z_spec = 3.495 (Table 1)  
  > "included in the X-ray-selected AGN catalog of (cite: kalfountzou14) as a type-2 AGN." (2.2 ALMA Band-6 observation); distance from Keck/MOSFIRE spectroscopy (cite: onodera16; suzuki17)  
  > "included in the X-ray-selected AGN catalog of (cite: kalfountzou14) as a type-2 AGN." (2.2 ALMA Band-6 observation)

## Data provenance

- ALMA projects: 2018.1.00681.S
- bands: Band 6 (1.3 mm), Cycle 6  
  > "Our ALMA Cycle 6 program with Band-6 was conducted during December 2018 – March 2019" (2.2 ALMA Band-6 observation)
- frequencies and spectral setup: four spectral windows per target, 221.9-254.4 GHz depending on redshift, one covering CO(9-8); Time Domain Mode (TDM)  
  > "Frequencies of four spectral windows are slightly different among the targets depending on their spectroscopic redshifts (between 221.9 GHz and 254.4 GHz)." (2.2 ALMA Band-6 observation); "The data were taken with the Time Domain Mode (TDM)." (2.2 ALMA Band-6 observation)
- continuum bandwidth: effective bandwidth of each spectral window ~1.875 GHz  
  > "The effective bandwidth of each spectral window is ~1.875 GHz." (2.2 ALMA Band-6 observation)
- arrays: _not stated_
- configurations: _not stated_
- baselines: _not stated_
- angular resolution: _not stated_
- max recoverable scale: _not stated_
- sensitivity: RMS levels 0.01-0.05 mJy/beam per target (Table 1)  
  > "RMS level" (Table 1)
- time on source: ~5-90 min depending on target (Table 1 lists 5, 11, 41, 49, 53, 88 min)  
  > "5–90 min depending on the stellar mass, SFR, and gas-phase metallicity of the targets as summarized in" (2.2 ALMA Band-6 observation)
- observing dates: December 2018 - March 2019  
  > "was conducted during December 2018 – March 2019" (2.2 ALMA Band-6 observation)
- pi or archival as stated: Own Cycle 6 program, PI T. Suzuki  
  > "(2018.1.00681.S, PI: T. Suzuki)." (2.2 ALMA Band-6 observation)
- Line: CO J=9-8 (1036.9 GHz)
- Other facility **Keck/MOSFIRE**: H- and K-band NIR spectra giving emission-line fluxes and gas-phase metallicities for all targets  
  > "High quality near-infrared (NIR) spectra obtained with Keck/MOSFIRE" (Introduction)
- Other facility **COSMOS2015 catalog**: optical-NIR broad-band photometry (u to 8.0 um) combined with ALMA 1.3 mm in SED fitting  
  > "from the COSMOS2015 catalog (cite: cosmos2015)" (2.4 SED fitting)
- External data: Gas-phase metallicities and emission-line fluxes of the parent sample  
  > "their gas-phase metallicities are already measured (cite: onodera16; suzuki17)" (Introduction) [from (cite: onodera16; suzuki17)]
- External data: Optical-NIR photometry of the targets  
  > "from the COSMOS2015 catalog (cite: cosmos2015)" (2.4 SED fitting) [from (cite: cosmos2015)]
- External data: Metallicity vs gas-to-dust mass ratio relation (log delta_gdr = 10.54 - 0.99 x (12+log(O/H)), scatter 0.15 dex)  
  > "We use the relation shown in (cite: magdis12) as follows:" (3.3 Gas mass); "The scatter of this relation is 0.15 dex (cite: magdis12)." (3.3 Gas mass) [from (cite: magdis12), based on (cite: leroy11)]
- External data: Metallicity calibrations (PP04 N2 and Curti et al. relations) used to convert between line-ratio metallicities  
  > "to the gas-phase metallicities using the (cite: PP04) calibration." (3.3 Gas mass); "(cite: curti16) showed that the offset of gas-phase metallicities calibrated with different line ratios is 0.04 dex on average." (4.4 Comparison of galaxies at z=0-3.3) [from (cite: PP04); (cite: curti16)]
- External data: Ionization parameter vs O32 and metallicity relation  
  > "We use the following relation by (cite: KK04) to estimate the ionization parameter from the" (3.1 Gas-phase metallicity and ionization parameter) [from (cite: KK04)]
- External data: Star-forming main-sequence scaling relations for f_gas and t_dep at z~3.3  
  > "represents the scaling relation for galaxies on the star-forming main sequence" (4.2 Gas properties of star-forming galaxies) [from (cite: tacconi18)]
- External data: Literature comparison samples of dust/gas masses and metallicities (Magdis+17, Wiklind+19, ASPECS, Cassata+20, AS2UDS, Tan+14, Saintonge+13, Seko+16, xCOLD GASS, ALLSMOG)  
  > "We next introduce samples from the literature to which we compare our data in Section" (3.4 Comparison sample from the literature) [from (cite: magdis17; wiklind19; aravena20; cassata20; dudzeviciute20; tan14; saintonge13; seko16_alma; saintonge17; catinella18; bothwell14; cicone17)]
- External data: Gas regulator model formalism  
  > "with a gas regulator model by (cite: pengmaiolino14)" (4.4 Comparison with a gas regulator model) [from (cite: pengmaiolino14)]
- Simulation/model as data: Gas regulator model tracks of Peng & Maiolino with R=0.4, y=1.5 Zsun, t_dep=0.8 Gyr and five mass-loading factors lambda=0.5-2.5  
  > "We assume R=0.4 (for the Chabrier IMF; (cite: madau14))" (4.4 Comparison with a gas regulator model); "We assume five different mass-loading factors between" (4.4 Comparison with a gas regulator model)

## Processing

### Calibration

- pipeline or manual: CASA used to calibrate the raw data (pipeline vs manual not specified)  
  > "We used the Common Astronomy Software Application package (casa; (cite: CASA)) to calibrate the raw data." (2.2 ALMA Band-6 observation)
- casa version: _not stated_
- pipeline version: _not stated_
- archive products used as is: _not stated_
- flux calibrator: _not stated_
- flux scale uncertainty: _not stated_
- self calibration: _not stated_

### Imaging

- task: CASA clean  
  > "We run the clean algorithm with natural weighting." (2.2 ALMA Band-6 observation)
- deconvolver: _not stated_
- weighting robust: natural weighting  
  > "We run the clean algorithm with natural weighting." (2.2 ALMA Band-6 observation)
- uv taper: tapered maps were used for stacking (taper parameters not stated)  
  > "Then, we stacked the cutout images by weighting with the RMS levels in the tapered maps" (2.3 Stacking analysis)
- cell size: _not stated_
- image size: _not stated_
- masking: clean re-run with masks on sources detected at >=5 sigma  
  > "we run clean again by masking the sources." (2.2 ALMA Band-6 observation)
- multiscale scales: _not stated_
- continuum subtraction: _not stated_
- line free channels: _not stated_
- primary beam correction: _not stated_
- array combination: _not stated_
- smoothing: _not stated_
- final beam: _not stated_
- final rms: _not stated_

### Inherited from earlier work

- Use of the updated magphys version for high-redshift galaxies  
  > "We used the updated version of magphys for galaxies at high redshifts (cite: dacunha15)." (2.4 SED fitting) [from (cite: dacunha15)]
- Treatment of optical-NIR upper limits in magphys (0 in flux column, 3 sigma in error column)  
  > "We took into account the upper limits for the optical-NIR photometries by giving 0 to the flux column" (2.4 SED fitting) [from according to (cite: dacunha15)]
- Entering ALMA non-detections as 1.5 sigma +/- 1 sigma 1.3 mm fluxes  
  > "value as done in (cite: dudzeviciute20)." (2.4 SED fitting) [from (cite: dudzeviciute20)]
- Emission-line fluxes and gas-phase metallicity recalculation taken from earlier MOSFIRE papers (citations missing in the text)  
  > "The emission line fluxes of the sources are available in and ." (3.1 Gas-phase metallicity and ionization parameter) [from earlier parent-sample papers (citation not visible in text; likely (cite: onodera16; suzuki17))]

### Not stated but needed to reproduce (our reading)

- How 1.3 mm flux densities and upper limits were measured from the maps (aperture, point-source fit, or peak) and their uncertainties
- Tapering parameters and the cell size, image size and beam of the individual maps and the stack
- Which CASA version and whether the standard pipeline or manual scripts were used for calibration
- Flux calibrator and absolute flux scale uncertainty
- Details of the recomputed gas-phase metallicities and emission-line fluxes (calibration used, line fluxes) which sit in earlier papers
- The exact method for the 5 sigma stack significance and the stellar-mass cut definition for the stack beyond excluding 434618
- magphys prior/library settings, redshift treatment and treatment of the stack photometry weights beyond what is described
- Source of the gas-regulator model parameters (Phi, epsilon) beyond R, y, t_dep and lambda, and the exact calculation of equilibrium timescales per galaxy

## Analysis recipe

1. **Calibrate and image the Band 6 data**: Calibration of raw data in CASA, imaging with clean using natural weighting and a second clean pass masking sources detected at >=5 sigma  
  > "We run the clean algorithm with natural weighting. When there are sources detected with" (2.2 ALMA Band-6 observation); "we run clean again by masking the sources." (2.2 ALMA Band-6 observation)
   - software: CASA
   - parameter: natural weighting  
  > "We run the clean algorithm with natural weighting." (2.2 ALMA Band-6 observation)
   - fitting: _not stated_
   - validation: _not stated_
2. **Stack ALMA non-detections**: Cutouts of tapered 20x20 arcsec images centred on the Ks-band position, stacked with RMS weights; source 434618 excluded because its stellar mass is much lower  
  > "Then, we stacked the cutout images by weighting with the RMS levels in the tapered maps" (2.3 Stacking analysis); "we excluded this source so that we can investigate the average dust and gas properties of star-forming galaxies with similar stellar masses" (2.3 Stacking analysis)
   - fitting: _not stated_
   - validation: _not stated_
3. **Fit SEDs to derive stellar mass, SFR and dust mass**: magphys SED fit of ALMA 1.3 mm plus COSMOS2015 optical-NIR photometry with emission-line fluxes removed from the H and Ks bands; medians of PDFs adopted  
  > "Because magphys does not include emission lines from the ionized gas, we subtracted the emission line fluxes measured with the NIR spectra from the" (2.4 SED fitting); "We use the median values of the probability distribution function (PDF) for stellar mass, SFR, and dust mass in the following analyses." (2.4 SED fitting)
   - software: magphys
   - parameter: BC03 stellar populations with Chabrier IMF; metallicity 0.2-2 solar; delayed exponential SFH with bursts; two-component Charlot & Fall attenuation  
  > "magphys adopts stellar population synthesis models of (cite: bc03) with the (cite: chabrier03) IMF." (2.4 SED fitting); "The metallicity range is set to be from 0.2 to 2 times solar." (2.4 SED fitting); "magphys uses the two-component model of (cite: charlotfall00)" (2.4 SED fitting)
   - parameter: ALMA non-detections entered as 1.5 sigma +/- 1 sigma flux; dust-mass upper limit taken as 97.5th percentile of PDF; uncertainties are 16-84th percentiles  
  > "provides a better weighting of the sub-millimeter constraint in the best-fit model returned by magphys than using a" (2.4 SED fitting); "we use the 97.5th percentile values of the PDF as the upper limits." (2.4 SED fitting); "The uncertainties correspond to the 16–84th percentile values of the PDF." (2.4 SED fitting)
   - assumption: dust mass absorption coefficient kappa_abs = 0.77 g^-1 cm^2 at 850 um; emissivity index beta = 1.5 for warm and 2 for cold components  
  > "magphys assumes a dust mass absorption coefficient at" (2.4 SED fitting); "of 1.5 for the warm components and 2 for the cold components" (2.4 SED fitting)
   - fitting: energy-balance SED fitting with magphys; sampler details not stated  
  > "magphys combines the emission by stellar populations with the attenuation and emission by dust in galaxies based on the energy balance technique." (2.4 SED fitting)
   - validation: dust-mass upper limits cross-checked with M_dust/L_997.6GHz ratio of detected sources  
  > "The estimated dust mass upper limits are similar as the 97.5th percentile values of the PDF from magphys." (2.4 SED fitting)
4. **Derive ionization parameter**: Kobulnicky & Kewley relation giving log q from log O32 and 12+log(O/H)  
  > "We use the following relation by (cite: KK04) to estimate the ionization parameter from the" (3.1 Gas-phase metallicity and ionization parameter)
   - fitting: _not stated_
   - validation: _not stated_
5. **Convert dust mass to gas mass**: M_gas = M_dust x delta_gdr with delta_gdr from the Magdis et al. metallicity relation (log delta_gdr = 10.54 - 0.99 x (12+log(O/H))); metallicities converted to the PP04 scale via the Curti et al. relation; dust masses multiplied by two to correct to Draine & Li dust models  
  > "We use the relation shown in (cite: magdis12) as follows:" (3.3 Gas mass); "We multiply our dust masses by a factor of two when converting them to gas masses" (3.3 Gas mass); "to the gas-phase metallicities using the (cite: PP04) calibration." (3.3 Gas mass)
   - parameter: relation scatter 0.15 dex  
  > "The scatter of this relation is 0.15 dex (cite: magdis12)." (3.3 Gas mass)
   - assumption: M_gas includes both molecular and atomic hydrogen; magphys dust masses lower by factor two than Draine & Li based masses  
  > "includes both molecular and atomic hydrogen." (3.3 Gas mass); "dust masses obtained with magphys are lower by a factor of two" (2.4 SED fitting)
   - fitting: _not stated_
   - validation: _not stated_
6. **Derive f_gas and t_dep and compare with main-sequence scaling relations**: f_gas = M_gas/(M_gas+M*) and t_dep = M_gas/SFR compared with the Tacconi et al. 2018 scaling relation and with literature samples  
  > "represents the scaling relation for galaxies on the star-forming main sequence" (4.2 Gas properties of star-forming galaxies)
   - fitting: _not stated_
   - validation: _not stated_
7. **Interpret f_gas versus metallicity with a gas regulator model and estimate equilibrium timescales**: Peng & Maiolino gas regulator tracks compared with data at z=0-3.3; lambda inferred by eye from tracks; equilibrium timescale compared with minimum age M*/SFR  
  > "with a gas regulator model by (cite: pengmaiolino14)" (4.4 Comparison with a gas regulator model); "which can be regarded as the minimum age of a galaxy." (4.5 Equilibrium timescale)
   - parameter: R = 0.4 (Chabrier IMF), mass-loading factors lambda = 0.5-2.5 in five tracks  
  > "We assume R=0.4 (for the Chabrier IMF; (cite: madau14))" (4.4 Comparison with a gas regulator model); "We assume five different mass-loading factors between" (4.4 Comparison with a gas regulator model)
   - assumption: Equilibrium timescale is the time to reach equilibrium where inflow balances star formation and outflow  
  > "The equilibrium timescale is the timescale to reach the equilibrium state, where gas acquisition by inflows balance with gas consumption by star formation and outflows." (4.4 Comparison with a gas regulator model)
   - fitting: _not stated_
   - validation: _not stated_

## Software

- **CASA** : calibration of raw data and imaging with clean  
  > "We used the Common Astronomy Software Application package (casa; (cite: CASA)) to calibrate the raw data." (2.2 ALMA Band-6 observation); "We run the clean algorithm with natural weighting." (2.2 ALMA Band-6 observation)
- **magphys** high-redshift version of da Cunha et al. 2015: SED fitting including ALMA 1.3 mm fluxes to derive stellar mass, SFR and dust mass  
  > "We used the SED fitting code magphys (cite: dacunha08; dacunha15; battisti19)" (2.4 SED fitting); "We used the updated version of magphys for galaxies at high redshifts (cite: dacunha15)." (2.4 SED fitting)
- **astropy** : listed under Software; specific use not stated  
  > "astropy (cite: astropy:2013; astropy:2018), casa (cite: CASA), topcat (cite: topcat)" (Software)
- **TOPCAT** : listed under Software; specific use not stated  
  > "astropy (cite: astropy:2013; astropy:2018), casa (cite: CASA), topcat (cite: topcat)" (Software)

## Numeric results

| quantity | value | uncertainty | units | step | quote |
|---|---|---|---|---|---|
| Dust continuum detections | 6 of 12 galaxies | not stated | galaxies | 1 | We detected the dust continuum emission individually from six out of 12 galaxies. |
| Gas mass fraction range f_gas | 0.20-0.75 | typical +/-0.09 | dimensionless | 6 | Our estimated gas mass fractions are 0.20–0.75 and the gas depletion timescales are 0.09–1.55 Gyr. |
| Gas depletion timescale range t_dep | 0.09-1.55 | typical +/-0.22 dex | Gyr | 6 | Our estimated gas mass fractions are 0.20–0.75 and the gas depletion timescales are 0.09–1.55 Gyr. |
| Stacked sample f_gas | 0.38 | +0.10/-0.09 | dimensionless | 6 | As for the stacked sample, the gas mass fraction and gas depletion timescale are estimated to be |
| Stacked sample t_dep | 0.28 | +0.15/-0.14 | Gyr | 6 | As for the stacked sample, the gas mass fraction and gas depletion timescale are estimated to be |
| Stacked sample log(M_dust/M_sun) | 7.33 | +0.17/-0.15 | dex (log M_sun) | 3 | The dust mass of the stacked sample is |
| Source 208681 log(M_dust/M_sun) | 8.89 | +0.11/-0.08 | dex (log M_sun) | 3 | has a dust mass of |
| Median dust-to-stellar mass ratio (Summary) | 3.0e-3 | +/-2.0e-3 | dimensionless | 3 | The median value of the dust-to-stellar mass ratios is |
| Mass-loading factor inferred from gas regulator tracks | lambda ~ 2.0-2.5 | not stated | dimensionless | 7 | 2.0–2.5 rather than the lower values such as |
| Metallicity offset of z>~2 galaxies at fixed f_gas relative to local galaxies | ~0.2 | not stated | dex | 7 | show an offset toward the lower gas-phase metallicities |
| Equilibrium timescale of ALMA-detected sources | 0.03-2.21 (average 0.52) | not stated | Gyr | 7 | The equilibrium timescales of the ALMA-detected sources are estimated to be 0.03–2.21 Gyr (average value: 0.52 Gyr) |
| Minimum age M*/SFR of the galaxies | 0.25-1.25 (average 0.57) | not stated | Gyr | 7 | 0.25–1.25 Gyr (average: 0.57 Gyr), which is closer to the equilibrium timescales than the Hubble time. |

## Qualitative findings

- No statistically significant trend between dust-to-stellar mass ratio and gas-phase metallicity  
  > "We find no statistically significant trend between the dust-to-stellar mass ratio and gas-phase metallicity" (4.1 Dust mass and its metallicity dependence)
- No clear correlation between gas mass fraction and ionization parameter  
  > "We find no clear correlation between the gas mass fraction and ionization parameter as well." (4.3 Gas mass fraction versus physical conditions of the ionized gas)
- Scatter in f_gas and t_dep is not explained by offset from the main sequence alone  
  > "The observed scatter of the gas mass fraction and depletion timescale in our sample cannot be explained by" (4.2 Gas properties of star-forming galaxies)
- z>~2 galaxies are less chemically enriched than local galaxies at similar gas mass fraction  
  > "are less chemically enriched than those at" (4.4 Comparison of galaxies at z=0-3.3)

## Claim tuples

- H: Do z~3.3 galaxies on the star-forming main sequence follow the gas mass fraction and depletion time scaling relations | E: Convert magphys dust masses to gas masses via the metallicity-dependent gas-to-dust ratio and compare f_gas and t_dep with the Tacconi et al. 2018 relation | R: f_gas 0.20-0.75 and t_dep 0.09-1.55 Gyr with a wider spread than the scaling relation, scatter >~1 dex in t_dep at fixed stellar mass | F: Large diversity of gas properties exists among galaxies apparently on the main sequence | **supported**
- H: Does gas mass fraction correlate with gas-phase metallicity or ionization parameter at z~3.3 | E: Compare f_gas with 12+log(O/H) and log q for the sample | R: No statistically significant correlation with metallicity and no clear correlation with ionization parameter | F: No correlation found, possibly due to small sample or bursty star formation | **partially**
- H: Are z~3.3 galaxies more metal-poor than local galaxies at similar gas mass fraction | E: Plot f_gas versus 12+log(O/H) for z=0-3.3 samples using a common Curti et al. metallicity scale | R: z>~2 galaxies show an offset of ~0.2 dex toward lower metallicity | F: z~3.3 galaxies appear more metal-poor than local galaxies with similar gas fractions | **supported**
- H: Can a gas regulator model explain the metallicity offset with outflows | E: Overlay Peng & Maiolino model tracks with lambda=0.5-2.5, R=0.4, y=1.5 Zsun, t_dep=0.8 Gyr on the f_gas-metallicity diagram | R: Data broadly follow tracks with lambda ~2.0-2.5 rather than 0.5 or 1 | F: Higher mass-loading factor at earlier cosmic times explains the offset | **supported**
- H: Are gas-rich z~3 galaxies out of equilibrium | E: Compare model equilibrium timescales with minimum ages M*/SFR | R: Galaxies with f_gas ~0.6-0.8 have equilibrium timescales comparable to minimum ages | F: Gas-rich normal galaxies may not have reached equilibrium | **partially**

## Reasoning

- Why this data: Dust continuum is much cheaper than CO and allows individual gas estimates for more z>3 galaxies, provided metallicities are known  
  > "using dust continuum as a tracer of gas has an advantage to increase the number of galaxies at higher redshifts" (Introduction)
- Why this method: Gas-to-dust ratio depends on metallicity, so metallicity-dependent conversion is used  
  > "Because the gas-to-dust mass ratio depends on the metallicity (cite: leroy11; remy-ruyer14), metallicity measurements are crucial to estimate the gas mass accurately." (Introduction)
- Alternative: 3 sigma upper limits for non-detections in magphys rejected in favour of 1.5 sigma +/- 1 sigma entries for better weighting  
  > "provides a better weighting of the sub-millimeter constraint in the best-fit model returned by magphys than using a" (2.4 SED fitting)
- Alternative: Source 434618 excluded from the stack because of much lower stellar mass  
  > "we excluded this source so that we can investigate the average dust and gas properties of star-forming galaxies with similar stellar masses" (2.3 Stacking analysis)
- How they decided it was enough: _not stated_
- Limitation (authors): Source 192129 is an X-ray type-2 AGN; its stellar mass, SFR, metallicity and ionization parameter may be affected  
  > "may be affected by the emission from the AGN." (2.2 ALMA Band-6 observation)
- Limitation (authors): Unclear whether high-z galaxies follow the local metallicity-gas-to-dust relation  
  > "It remains unclear whether star-forming galaxies at high redshifts follow the same relation between gas-phase metallicity and gas-to-dust mass ratio as local galaxies" (Summary)
- Limitation (authors): Sample size may be too small to find correlations  
  > "Note that our sample size may be too small to find any correlation." (4.3 Gas mass fraction versus physical conditions of the ionized gas)
- Limitation (authors): Dust mass depends on assumed absorption coefficient  
  > "One of the uncertainties on the dust mass is the assumed dust mass absorption coefficient" (2.4 SED fitting)
- Caveat (inferred, ours): Gas masses rest on an unverified z>3 gas-to-dust vs metallicity relation calibrated locally and a factor-of-two dust-mass rescaling
- Caveat (inferred, ours): Single Rayleigh-Jeans band at ~280 um rest frame with an assumed temperature-free SED fit; dust-mass systematic ~0.3 dex
- Caveat (inferred, ours): Only 6 detections plus one stack of 5 non-detections; correlation tests have little power
- Caveat (inferred, ours): Gas regulator tracks compared by eye, no fit or error propagation for lambda
- Caveat (inferred, ours): Mixed comparison samples use different gas tracers and dust models

## Reproducibility

- Data public (paper): _not stated_
- Products in archive: _not stated_
- Missing: Flux extraction method and exact flux uncertainties for the 1.3 mm maps
- Missing: CASA version, calibration method and image parameters (cell, size, taper)
- Missing: Earlier-paper line fluxes and metallicities needed as inputs
- Missing: magphys configuration details and photometry catalog entries used
- Data volume (inferred): Small: 12 short Band 6 TDM observations of 5-90 min; probably tens of GB raw, a few GB calibrated (inferred)
- Score (inferred): 3/5, Project code and key assumptions are given and results are tabulated, but flux measurement details, CASA version, imaging parameters and the metallicity inputs from earlier papers are not stated.
- Rediscovery candidate: no, Paper does not state data availability and inputs (line fluxes, metallicities) come from earlier papers; imaging and flux extraction recipe is incomplete.

## Links

- Method: (cite: dacunha15) (High-redshift version of magphys used for SED fitting)
- Method: (cite: magdis12) (Metallicity-dependent gas-to-dust ratio relation)
- Method: (cite: pengmaiolino14) (Gas regulator model)
- Method: (cite: KK04) (Ionization parameter relation)
- Method: (cite: dudzeviciute20) (Treatment of non-detections in magphys)
- Companion: (cite: onodera16) (Parent UV-selected MOSFIRE sample with metallicities)
- Companion: (cite: suzuki17) (Parent [OIII] emitter MOSFIRE sample with metallicities)
- Related: COSMOS
- Related: HiZELS
- Related: ASPECS
- Related: AS2UDS
- Related: xCOLD GASS
- Related: ALLSMOG

## Checks

```json
{
 "quotes": 115,
 "quotes_ok": 115,
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
  "facts": 107,
  "stated": 70,
  "rate": 0.654
 },
 "evidence_ok": true
}
```
