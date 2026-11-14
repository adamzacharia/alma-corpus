# Into the Mystic: the MUSE view of the ionized gas in the Mystic Mountains in Carina

`2025MNRAS.537.3009R` | Monthly Notices of the Royal Astronomical Society 2025 | first author: Reiter, Megan | arXiv: 2501.18029 | DOI: 10.1093/mnras/staf193

Card schema 1.0 | model claude-sonnet-5-5-claude-code | depth light | type multi_facility_alma_minor

## Science

- Fields: star_formation, milky_way_ism
- Question: What are the physical conditions (extinction, electron density and temperature, excitation) of the ionized gas in the Mystic Mountains, and what photoevaporation rate, remaining lifetime and protostar shielding time follow when combined with ALMA molecular gas masses?  
  > "we measure the physical properties in the ionized gas including the electron density and temperature, excitation, and ionization." (abstract); "We compute the photoevaporation rate of the Mystic Mountains and combine it with recent ALMA observations of the cold molecular gas to estimate the remaining lifetime of the Mystic Mountains and the corresponding shielding time for the embedded protostars." (abstract)
- Target **Mystic Mountains (HH 901, HH 902, HH 1066 pillars), Carina Nebula**: coordinates MUSE tile 1 centre 10:44:08.4, -59:29:40.0 (J2000); four tiles span 10:44:00.7 to 10:44:08.4 and -59:29:40 to -59:30:39  
  > "Embedded young stellar objects (YSOs) have been harder to detect due to the large distance to the region (2.35 kpc)." (3.4 Cores, clumps and young stellar objects); "10:44:08.4" (Table 1); "59:29:40.0" (Table 1); z/distance 2.35 kpc  
  > "Embedded young stellar objects (YSOs) have been harder to detect due to the large distance to the region (2.35 kpc)." (3.4 Cores, clumps and young stellar objects); "10:44:08.4" (Table 1); "59:29:40.0" (Table 1); distance from _not stated_

## Data provenance

- ALMA projects: 2018.1.01001.S
- bands: 1.3 mm continuum; 12CO J=2-1 and C18O J=2-1 (from Reiter 2023 ALMA maps; band number not stated)  
  > "Contours showing the large-scale distribution of $^{12}$CO J=2-1 and C$^{18}$O J=2-1 from (cite: reiter2023_MM)" (3.5.1 CO and isotopologues); "Figure [5](#fig:density_comp) shows 1.3 mm continuum contours (cyan)" (3.5.2 Continuum and dense gas tracers)
- frequencies and spectral setup: _not stated_
- continuum bandwidth: _not stated_
- arrays: _not stated_
- configurations: _not stated_
- baselines: _not stated_
- angular resolution: ~6 arcsec beam (ALMA data used for comparison)  
  > "with modest spatial resolution (6$''$ beam)." (1 Introduction)
- max recoverable scale: _not stated_
- sensitivity: _not stated_
- time on source: _not stated_
- observing dates: _not stated_
- pi or archival as stated: Publicly available from the ALMA archive, program ADS/JAO.ALMA#2018.1.01001.S; ALMA results taken from Reiter et al. (2023)  
  > "The ALMA data used in this study are publicly available from the ALMA archive" (Data Availability)
- Line: 12CO J=2-1 (not stated)
- Line: C18O J=2-1 (not stated)
- Line: 13CS J=5-4 (not stated)
- Line: DCN J=3-2 (not stated)
- Other facility **VLT/MUSE (ESO programme 097.C-0137)**: Optical IFU cubes (4650-9300 A, four tiles) used for all ionized-gas measurements; this is the primary dataset  
  > "The observations used in this paper are part of a larger survey of Tr14 and the surrounding nebulosity with MUSE (programme ID 097.C-0137; PI: A. F. McLeod; see also (cite: itrich2024))." (2 Observations); "continuous spectral coverage from $\lambda 4650-9300$ Å." (2 Observations)
- Other facility **Gaia**: Reference catalog for the astrometric solution of each MUSE cube  
  > "and compute the updated astrometric solution, then apply this solution to each MUSE cube." (2 Observations)
- External data: Molecular gas masses and areas of the Mystic Mountains and the HH 901, HH 902, HH 1066 pillars  
  > "Molecular gas mass of the Mystic Mountains and the smaller pillars it contains. Data from (cite: reiter2023_MM)." (Table 1 caption) [from (cite: reiter2023_MM)]
- External data: 12CO and C18O J=2-1 maps, 13CS and DCN maps, 1.3 mm continuum sources and dendrogram structures  
  > "A dendrogram analysis to identify the hierarchical clustering in the gas identified these as three distinct structures in position-position-velocity space" (3.5.1 CO and isotopologues) [from (cite: reiter2023_MM)]
- External data: HH 901 YSO remaining envelope mass of 0.52 Msun  
  > "For a remaining envelope mass of 0.52 $\text{M}_{\ensuremath{\odot}}$ (cite: reiter2023_MM)" (3.6 The remaining lifetime of the Mystic Mountains) [from (cite: reiter2023_MM)]
- External data: R_V = 4.4 +/- 0.2 toward Carina  
  > "extinction curves with $R_V = 4.4 \pm 0.2$ as measured toward Carina by (cite: hur2012)" (3.1 Extinction) [from (cite: hur2012)]
- External data: Intrinsic Halpha/Hbeta = 2.86 for Case B  
  > "the intrinsic flux ratio is (H$\alpha$/H$\beta$)$_{\mathrm{int}}$ = 2.86 (cite: osterbrock2006)." (3.1 Extinction) [from (cite: osterbrock2006)]
- External data: Distance to the region, 2.35 kpc  
  > "Embedded young stellar objects (YSOs) have been harder to detect due to the large distance to the region (2.35 kpc)." (3.4 Cores, clumps and young stellar objects) [from not stated for this value]
- External data: Seeing values for the long exposures  
  > "long exposure values from Table A.1 in (cite: itrich2024)" (Table 1) [from (cite: itrich2024)]

## Processing

### Calibration

- pipeline or manual: MUSE (not ALMA) data reduced with MUSE recipes v.2.8.9 in EsoRex with standard calibrations, modified sky subtraction; ALMA calibration not described (ALMA products come from Reiter et al. 2023)  
  > "Data were reduced using the MUSE recipes v.2.8.9 (cite: weilbacher2012) in the EsoRex environment with standard calibrations." (2 Observations)
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

- MUSE sky subtraction method (five-step modified approach for bright HII regions)  
  > "we use the modified sky subtraction approach developed by (cite: zeidler2019)." (2 Observations) [from (cite: zeidler2019)]
- All ALMA data products, molecular masses, and pillar naming  
  > "We refer to these pillars by the name of the jet they contain (i.e. the HH 901 pillar) as in (cite: reiter2023_MM)." (4 Discussion); "Data from (cite: reiter2023_MM)." (Table 1 caption) [from (cite: reiter2023_MM)]
- Photoevaporation mass-loss expression for a cylinder illuminated from one side  
  > "we use the expression for a cylinder illuminated from one side from (cite: smith2004_finger)" (4.1 Photoevaporation rate) [from (cite: smith2004_finger)]
- MUSE observations are a subset of a larger Tr14 MUSE survey  
  > "see also (cite: itrich2024)" (2 Observations) [from (cite: itrich2024)]

### Not stated but needed to reproduce (our reading)

- How line fluxes were measured from the MUSE cubes (Gaussian fits, integration windows, per-spaxel fitting, binning or smoothing)
- Atomic data set and PyNeb version used for A_V, Te and ne
- Which pixels were used for the fourth-order polynomial continuum fit
- Radii of curvature used in the photoevaporation estimate are listed only as r_surf in Table 2; the circle-fitting procedure and regions (red circles) are only in a figure
- Regions and exact definition of the 1 arcsec P-V extraction paths and the intensity-profile cuts
- Whether ALMA products from Reiter et al. (2023) can be re-derived: ALMA calibration, imaging, masks, mass derivation (dust or gas conversion) are not given here
- How the ionizing photon rate Q_0,local was computed (Table 2 column) and how Omega was defined
- How the ~4e-6 Msun/yr average photoevaporation rate was averaged

## Analysis recipe

1. **Reduce MUSE cubes with modified sky subtraction and continuum removal**: MUSE recipes v.2.8.9 in EsoRex; modified five-step sky subtraction (muse_create_sky run twice, continuum zeroed, only OH and O2 telluric lines kept, muse_scipost); fourth-order polynomial continuum subtraction  
  > "Data were reduced using the MUSE recipes v.2.8.9 (cite: weilbacher2012) in the EsoRex environment with standard calibrations." (2 Observations); "To remove the continuum emission from the reduced data, we fit a fourth-order polynomial to a subset of pixels without strongly structured nebular emission and subtract this from the entire cube." (2 Observations)
   - software: EsoRex, muse_create_sky, muse_scipost
   - parameter: Wide-field mode, 1 arcmin x 1 arcmin field, R=2000-4000; three exposures per pointing with 90 deg rotation; long (780 s) and short (5 s) exposures  
  > "At each pointing, three separate exposures were obtained with a 90$^{\circ}$ rotation between each to minimize detector artifacts." (2 Observations); "each position was observed twice – once with short (5 s) exposures and once with long (780 s) exposures." (2 Observations)
   - parameter: Long exposures used for most lines; short exposures for Halpha near HH 901 and HH 902 and for Halpha/Hbeta  
  > "For the majority of the analysis in this paper, we use only the long exposures as these provide the best signal-to-noise for most lines." (2 Observations)
   - assumption: OH and O2 lines dominate telluric emission; all other telluric line fluxes set to zero  
  > "we assume that OH and O$_2$ lines dominate the telluric emission; all other telluric line fluxes are set to zero." (2 Observations)
   - fitting: _not stated_
   - validation: _not stated_
2. **Align MUSE cubes to Gaia astrometry**: astrometry python package: extract an image from each cube, match stars to Gaia, apply updated astrometric solution  
  > "we used the astrometry python package from (cite: wenzl2022)." (2 Observations)
   - software: astrometry (wenzl2022)
   - fitting: _not stated_
   - validation: _not stated_
3. **Derive line-of-sight extinction map**: Halpha/Hbeta ratio with PyNeb, CCM89 extinction curve, intrinsic ratio 2.86; extinction from short exposures applied to both short and long exposures  
  > "The line-of-sight extinction was computed as a function of position using PyNeb (cite: luridiana2013; luridiana2015)." (3.1 Extinction); "We use the extinction correction measured from the short exposures to correct the fluxes in both the short and long exposures." (3.1 Extinction)
   - software: PyNeb
   - parameter: R_V = 4.4 +/- 0.2; CCM89 curves; intrinsic Halpha/Hbeta = 2.86  
  > "we use the (cite: ccm1989) extinction curves with $R_V = 4.4 \pm 0.2$ as measured toward Carina by (cite: hur2012)." (3.1 Extinction)
   - assumption: Case B recombination, T = 1e4 K, ne = 1e3 cm^-3  
  > "We assume Case B recombination for gas with a temperature $T=10^4$ K and an electron density $n_e = 10^3$ cm$^{-3}$." (3.1 Extinction)
   - fitting: _not stated_
   - validation: Compared A_V from short and long exposures (agree within ~0.1 mag away from saturation) and with point-source A_V from Itrich et al. (2024)  
  > "Extinction values derived from the short and long exposures are consistent to within $\sim 0.1$ mag everywhere except for where the H$\alpha$ emission is saturated in the long exposures." (3.1 Extinction)
4. **Compute electron temperature and density maps and extract values at pillar tips**: Te from [N II] 5755/(6548,6583) (cross-checked with [S III] 6312/9068); ne from [S II] 6731/6716; computed simultaneously with PyNeb at every map point; uncertainties from variation within extracted regions  
  > "To compute $T_e$, we use the ratio of lines with very different excitation energies, in this case \[N ii\] $\lambda 5755 / \lambda 6548,6583$ (cite: osterbrock2006; piembert2017)." (3.2 Electron temperature and density); "We use PyNeb to compute these inter-related quantities simultaneously." (3.2 Electron temperature and density); "thus determine uncertainties directly from the variations in each extracted region." (3.2 Electron temperature and density)
   - software: PyNeb
   - fitting: _not stated_
   - validation: Similar Te results with the [S III] 6312/9068 ratio  
  > "For the Mystic Mountains, we obtain similar results if we use the ratio" (3.2 Electron temperature and density)
5. **Map excitation and neutral carbon emission and trace ionization-front intensity profiles**: He I 6678 / [S II] 6717,6731 ratio map for ionization degree; [C I] 8727 map; intensity profiles of lines of different excitation extracted along cuts across ionized interfaces  
  > "We consider the ratio of lines with similar ionization potentials, He i $\lambda 6678$ Å / \[S ii\] $\lambda 6717,6731$ Å, to estimate the degree of ionization in the gas." (3.3 Excitation); "Finally, we extract the intensity profiles of emission lines of different excitation to trace the structure of the ionization fronts." (3.3 Excitation)
   - fitting: _not stated_
   - validation: _not stated_
6. **Extract jet position-velocity diagrams**: pvextractor P-V diagrams in Halpha, [S II] 6717, [O I] 6300, [C I] 8727, [Fe II] 8616 over a 1 arcsec wide region centred on each outflow  
  > "To make the position-velocity (P-V) diagrams, we extract emission in a 1$''$ wide region centered on the outflow." (3.5 Jets and outflows)
   - software: pvextractor
   - fitting: _not stated_
   - validation: _not stated_
7. **Compute local photoevaporation (mass-loss) rates at ionized interfaces**: Cylinder illuminated from one side: Mdot ~ 2 pi r^2 m_H n_H v with n_H = 1.4 ne, v the ionized-gas sound speed (~10-12 km/s), r the radius of curvature of the best-matching circle at the pillar head  
  > "we use the expression for a cylinder illuminated from one side from (cite: smith2004_finger)" (4.1 Photoevaporation rate); "We determine the radius of curvature from the radius of the circle that best matches the curvature at the pillar head." (4.1 Photoevaporation rate)
   - parameter: v = sqrt(gamma k_B T / m), about 10-12 km/s for Te ~ 8000-10,500 K  
  > "this corresponds to $v \approx 10-12$ km s$^{-1}$." (4.1 Photoevaporation rate)
   - assumption: n_H = 1.4 ne; ideal isothermal gas sound speed  
  > "We adopt a value for the sound speed, $v$, for an ideal isothermal gas" (4.1 Photoevaporation rate)
   - fitting: _not stated_
   - validation: _not stated_
8. **Estimate remaining lifetime and shielding time**: Molecular mass from Reiter et al. (2023) divided by photoevaporation rate, for the whole complex and sub-regions  
  > "we can estimate the remaining Mystic Mountains lifetime." (4.3 The remaining lifetime of the Mystic Mountains)
   - assumption: Constant current photoevaporation rate  
  > "will remain shielded for $\gtrsim2.5$ Myr at the current photoevaporation rate." (4.3 The remaining lifetime of the Mystic Mountains)
   - fitting: _not stated_
   - validation: Compared with lifetimes of ~1e4-1e5 yr for molecular cocoons from Cortes-Rangel et al. (2020)  
  > "find even shorter remaining lifetimes, $\sim 10^4 - 10^5$ yr, for the molecular cocoons surrounding HH 901 and HH 902." (4.3 The remaining lifetime of the Mystic Mountains)

## Software

- **MUSE pipeline recipes / EsoRex** MUSE recipes v.2.8.9: MUSE data reduction  
  > "Data were reduced using the MUSE recipes v.2.8.9 (cite: weilbacher2012) in the EsoRex environment with standard calibrations." (2 Observations)
- **muse_create_sky / muse_scipost** : Modified sky-model creation and subtraction  
  > "Finally, this sky model is subtracted from the science observations during post-processing with the `muse_scipost` recipe." (2 Observations)
- **astrometry (python package)** : Aligning MUSE cubes with Gaia  
  > "we used the astrometry python package from (cite: wenzl2022)." (2 Observations)
- **PyNeb** : Extinction, electron temperature and density  
  > "The line-of-sight extinction was computed as a function of position using PyNeb (cite: luridiana2013; luridiana2015)." (3.1 Extinction); "We use PyNeb to compute these inter-related quantities simultaneously." (3.2 Electron temperature and density)
- **pvextractor** : Position-velocity diagrams of the jets  
  > "using pvextractor; these are shown in Figures" (3.5 Jets and outflows)

## Numeric results

| quantity | value | uncertainty | units | step | quote |
|---|---|---|---|---|---|
| Mean A_V toward the Mystic Mountains | 2.9 | 0.4 | mag | 3 | The average extinction toward the Mystic Mountains computed this way is $2.9 \pm 0.4$ mag (median $A_V=2.9$ mag). |
| ne at HH901 | 1825 | 390 | cm^-3 | 4 | $1825 \pm 390$ |
| Te at HH901 | 10392 | 253 | K | 4 | $10392 \pm 253$ |
| Mdot at HH901 | 2.0e-7 | 0.5e-7 | Msun/yr | 7 | $2.0 \pm 0.5 \times 10^{-7}$ |
| ne at HH902 a | 2214 | 378 | cm^-3 | 4 | $2214 \pm 378$ |
| Te at HH902 a | 10090 | 177 | K | 4 | $10090 \pm 177$ |
| Mdot at HH902 a | 1.2e-5 | 0.3e-5 | Msun/yr | 7 | $1.2 \pm 0.3 \times 10^{-5}$ |
| ne at HH902 b | 1908 | 155 | cm^-3 | 4 | $1908 \pm 155$ |
| Te at HH902 b | 9990 | 125 | K | 4 | $9990 \pm 125$ |
| Mdot at HH902 b | 1.0e-5 | 0.2e-5 | Msun/yr | 7 | $1.0 \pm 0.2 \times 10^{-5}$ |
| ne at HH902 c | 2131 | 246 | cm^-3 | 4 | $2131 \pm 246$ |
| Te at HH902 c | 9878 | 164 | K | 4 | $9878 \pm 164$ |
| Mdot at HH902 c | 2.7e-6 | 0.5e-6 | Msun/yr | 7 | $2.7 \pm 0.5 \times 10^{-6}$ |
| ne at HH1066 a | 2497 | 435 | cm^-3 | 4 | $2497 \pm 435$ |
| Te at HH1066 a | 10487 | 346 | K | 4 | $10487 \pm 346$ |
| Mdot at HH1066 a | 5.8e-7 | 1.3e-7 | Msun/yr | 7 | $5.8 \pm 1.3 \times 10^{-7}$ |
| ne at HH1066 b | 1687 | 294 | cm^-3 | 4 | $1687 \pm 294$ |
| Te at HH1066 b | 10276 | 264 | K | 4 | $10276 \pm 264$ |
| Mdot at HH1066 b | 3.4e-6 | 0.8e-6 | Msun/yr | 7 | $3.4 \pm 0.8 \times 10^{-6}$ |
| ne at mm5 a | 697 | 43 | cm^-3 | 4 | $697 \pm 43$ |
| Te at mm5 a | 10591 | 351 | K | 4 | $10591 \pm 351$ |
| Mdot at mm5 a | 2.1e-6 | 0.3e-6 | Msun/yr | 7 | $2.1 \pm 0.3 \times 10^{-6}$ |
| ne at mm5 b | 474 | 25 | cm^-3 | 4 | $474 \pm 25$ |
| Te at mm5 b | 10143 | 241 | K | 4 | $10143 \pm 241$ |
| Mdot at mm5 b | 5.1e-7 | 0.8e-7 | Msun/yr | 7 | $5.1 \pm 0.8 \times 10^{-7}$ |
| Average photoevaporation rate of the Mystic Mountains | ~4e-6 | not stated | Msun/yr | 7 | For the average photoevaporation rate, $\sim 4 \times 10^{-6}$ $\text{M}_{\ensuremath{\odot}}$ yr$^{-1}$, the entire Mystic Mountains will be completely evaporated in $8 \pm 2$ Myr. |
| Remaining lifetime of the whole Mystic Mountains | 8 | 2 | Myr | 8 | For the average photoevaporation rate, $\sim 4 \times 10^{-6}$ $\text{M}_{\ensuremath{\odot}}$ yr$^{-1}$, the entire Mystic Mountains will be completely evaporated in $8 \pm 2$ Myr. |
| Range of sub-region lifetimes | ~1 to ~13 | not stated | Myr | 8 | the estimated lifetimes vary from $\sim 1$ Myr to $\sim 13$ Myr. |
| Shielding time of the HH 901 YSO | >~2.5 | not stated | Myr | 8 | will remain shielded for $\gtrsim2.5$ Myr at the current photoevaporation rate. |
| Ionized-gas sound speed | 10-12 | not stated | km/s | 7 | this corresponds to $v \approx 10-12$ km s$^{-1}$. |

## Qualitative findings

- High electron densities (often above 1e3 cm^-3) trace pillar heads, globules and compressed ridges; the temperature map shows little structure with Te near 10,000 K along ionization fronts  
  > "High electron densities, often in excess of 10$^3$ cm$^{-3}$, trace the heads of pillars and globules" (3.2 Electron temperature and density); "Electron temperatures along the ionization front are typically near 10,000 K" (3.2 Electron temperature and density)
- HH 901 and HH 902 jets are high-density, low-ionization structures; only HH 901 shows extended [C I] emission, interpreted as dissociating molecular outflow  
  > "The HH 901 and HH 902 jets stand out as low-ionization structures" (3.3 Excitation); "Only HH 901 shows extended" (3.5 Jets and outflows)
- A new candidate jet seen in [Fe II] about 2 arcsec north of HH 902  
  > "We identify a new candidate jet located" (3.5 Jets and outflows)
- C18O contours follow high-ne regions in the HH 902 and HH 1066 pillars but not in the HH 901 pillar, where the C18O peak is offset ~10 arcsec from the ne peak  
  > "The correlation between C$^{18}$O and $n_e$ does not extend to the HH 901 pillar." (3.5.1 CO and isotopologues)
- All seven 1.3 mm continuum peaks lie immediately behind bright ionization fronts  
  > "All seven continuum peaks are found immediately behind bright ionization fronts." (3.5.2 Continuum and dense gas tracers)

## Claim tuples

- H: Does the ionized gas in the pillars show compression traced by high electron densities? | E: MUSE ne maps from [S II] ratio compared with ALMA C18O contours | R: ne often exceeds 1e3 cm^-3 at pillar tips and ridges; C18O peaks lie behind high-ne ionization fronts except in the HH 901 pillar | F: High densities and small sizes of pillar heads suggest compression by external UV from Tr14 | **partially**
- H: What is the remaining lifetime of the Mystic Mountains under photoevaporation? | E: Cylinder mass-loss formula applied with MUSE ne and Te; combined with ALMA-derived molecular masses | R: Whole complex 8 +/- 2 Myr; sub-regions ~1 to ~13 Myr; HH 901 tip >~2.5 Myr | F: The longest lifetimes are for the smallest structures independent of distance from the ionizing sources | **supported**
- H: Does the data point to triggered star formation in the Mystic Mountains? | E: Compare gas velocities from ALMA, jet bending, and pillar morphology with expectations for triggering | R: Velocities and jet bending do not clearly show acceleration; HH 900, 901, 1066 globules give mixed evidence | F: Data are consistent with star formation being revealed as the cloud is evaporated; triggering is not required | **partially**
- H: Can MUSE characterize the HH 901, 902, 1066 jets in different ionization states? | E: Line ratio maps and P-V diagrams in Halpha, [S II], [O I], [C I], [Fe II] | R: High-density low-ionization jets; marginally resolved velocities; extended [C I] only for HH 901 | F: HH 901 [C I] likely traces dissociation of the molecular outflow in the HII region | **supported**

## Reasoning

- Why this data: MUSE gives broad spatial and spectral coverage to measure ionized-gas properties across the pillars and compare with ALMA cold-gas observations  
  > "using the broad spatial and spectral coverage of the Multi-Unit Spectroscopic Explorer" (1 Introduction)
- Why this method: Modified sky subtraction used because the standard pipeline oversubtracts nebular lines that coincide with sky lines in bright HII regions  
  > "Important nebular lines have similar wavelengths to bright sky lines which can lead to them being oversubtracted in the automatic pipeline reduction." (2 Observations)
- Alternative: Standard pipeline sky subtraction rejected in favour of the Zeidler et al. modified approach  
  > "Important nebular lines have similar wavelengths to bright sky lines which can lead to them being oversubtracted in the automatic pipeline reduction." (2 Observations)
- Alternative: Long exposures not used for Halpha where saturated; short exposures used instead  
  > "However, H$\alpha$ emission is saturated in some portions of the long exposures, particularly along the ionization fronts." (2 Observations)
- How they decided it was enough: _not stated_
- Limitation (authors): HH 1066 jet body difficult to resolve with seeing-limited observations  
  > "The body of the smaller HH 1066 jet is difficult to resolve with these seeing-limited observations." (3.2 Electron temperature and density)
- Limitation (authors): MUSE velocity resolution is low (>~100 km/s), so jet radial velocities are only marginally resolved  
  > "Despite the low velocity resolution of MUSE" (3.5 Jets and outflows)
- Limitation (authors): Unambiguous evidence of triggered star formation is hard to identify  
  > "Unambiguous evidence of triggered star formation is difficult to identify in observations" (4.4 The erosion of the Mystic Mountains)
- Caveat (inferred, ours): Table 2 gives Mdot(HH901) = 2.0e-7 Msun/yr, the lowest value, but the text says HH 1066 has the lowest rate (~6e-7) and HH 901 is only ~2 times higher; the two are inconsistent
- Caveat (inferred, ours): Uncertainties on the photoevaporation rate omit systematic error from the radius of curvature, geometry and the isothermal sound speed assumption
- Caveat (inferred, ours): Lifetimes assume constant rate and that the molecular mass from a 6 arcsec ALMA map applies to sub-regions with large mass uncertainties (e.g. HH 901 3.31 +/- 2.64)
- Caveat (inferred, ours): Table 1 exposure times (15 s) differ from the 5 s quoted in the text
- Caveat (inferred, ours): Seeing-limited MUSE data may blend ionization-front structure at sub-arcsec scales

## Reproducibility

- Data public (paper): MUSE data public from the ESO archive; ALMA data public from the ALMA archive  
  > "The MUSE data presented in this paper are publicly available from the ESO archive" (Data Availability); "The ALMA data used in this study are publicly available from the ALMA archive" (Data Availability)
- Products in archive: _not stated_
- Missing: Line-flux measurement procedure and atomic data / PyNeb version
- Missing: ALMA calibration and imaging (inherited from Reiter et al. 2023)
- Missing: Definition of Q_0,local and Omega, and the pillar-tip circle fits
- Missing: Details of P-V extraction paths and intensity-profile cuts
- Missing: Reduced MUSE products only available on request
- Data volume (inferred): MUSE: eight cubes (four long, four short), likely a few GB each (~10-20 GB with raw calibrations); ALMA data from project 2018.1.01001.S are not processed here (their products come from Reiter et al. 2023)
- Score (inferred): 3/5, Public MUSE data and a clear recipe for ne, Te and Mdot with a numeric results table, but line-fitting details, atomic data version, region definitions and the ALMA mass products are not given.
- Rediscovery candidate: no, The ALMA part is inherited from another paper and key MUSE steps (line flux extraction, region and radius choices) are not specified, so an exact redo of the main numbers is not possible from this paper alone.

## Links

- Method: (cite: weilbacher2012) (MUSE data reduction pipeline)
- Method: (cite: zeidler2019) (Modified sky subtraction for bright HII regions)
- Method: (cite: wenzl2022) (Astrometry package used to align MUSE with Gaia)
- Method: (cite: smith2004_finger) (Mass-loss formula for an illuminated cylinder)
- Companion: (cite: reiter2023_MM) (ALMA 12CO, C18O, 13CS, DCN and 1.3 mm continuum data and molecular masses used here)
- Companion: (cite: itrich2024) (Companion MUSE survey of Tr14; seeing values and point-source extinction)
- Companion: (cite: cortes-rangel2020) (Higher-resolution ALMA observations of the HH 901 and HH 902 YSOs)
- Related: ESO programme 097.C-0137 (MUSE survey of Tr14, PI A. F. McLeod)
- Related: ALMA 2018.1.01001.S

## Checks

```json
{
 "quotes": 117,
 "quotes_ok": 117,
 "quote_pass_rate": 1.0,
 "quotes_too_long": 0,
 "unsupported_facts": 0,
 "project_codes": 1,
 "codes_not_in_text": [],
 "codes_not_in_obscore": [],
 "obscore_codes_not_in_card": [],
 "codes_printed_but_missing": [],
 "numeric_results": 30,
 "numeric_problems": 0,
 "fill": {
  "facts": 103,
  "stated": 57,
  "rate": 0.553
 },
 "evidence_ok": true
}
```
