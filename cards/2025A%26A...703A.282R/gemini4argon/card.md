# Observations of sulfuretted species in HL Tau

`2025A&A...703A.282R` | Astronomy and Astrophysics 2025 | first author: Rivière-Marichalar, P. | arXiv: 2511.19148 | DOI: 10.1051/0004-6361/202555440

Card schema 1.0 | model gemini-4-argon | depth light | type multi_facility_alma_minor

## Science

- Fields: protoplanetary_disks, astrochemistry, star_formation
- Question: Investigate the chemical differences between the protoplanetary disk and the surrounding envelope of HL Tau by comparing column density ratios of CS, H2CO, H2S, and SO2.  
  > "The goal of this paper is to investigate the chemical differences between the disk and the surrounding envelope by comparing the column density ratios of a few selected species in each region." (Observations of sulfuretted species in HL Tau)
- Target **HL Tau**: coordinates 04h31m38s4.511, 18d13m57.860s  
  > "HL Tau is a well-known Class I-II (cite: Furlan2008) protostar in Taurus." (Introduction); "The phase tracking center of our observation was $\alpha$(J2000) = 04h31m38s4.511, $\beta$(J2000) = 18$^{\circ}$13$'$57.$''$860." (Observations and data reduction); z/distance _not stated_; distance from _not stated_

## Data provenance

- ALMA projects: 2018.1.01037.S
- bands: _not stated_
- frequencies and spectral setup: _not stated_
- continuum bandwidth: _not stated_
- arrays: _not stated_
- configurations: _not stated_
- baselines: _not stated_
- angular resolution: _not stated_
- max recoverable scale: _not stated_
- sensitivity: _not stated_
- time on source: _not stated_
- observing dates: _not stated_
- pi or archival as stated: archival ALMA data from Garufi et al. (2022) (ADS/JAO.ALMA#2018.1.01037.S)  
  > "We repeated the analysis, including the detections by (cite: Garufi2022)." (SO$\rm _2$); "This paper makes use of the following ALMA data: ADS/JAO.ALMA#2018.1.01037.S." (Acknowledgements)
- Line: SO2 4(2,2)-4(1,3) (146.605 GHz)
- Line: CS 3-2 (146.969 GHz)
- Line: H2CO 2(1,1)-1(1,0) (150.498 GHz)
- Line: SO2 2(2,0)-2(1,1) (151.379 GHz)
- Line: SO2 5(2,4)-5(1,5) (165.144 GHz)
- Line: H2S 1(1,0)-1(0,1) (168.762 GHz)
- Line: SO2 14(1,13)-14(0,14) (163.605 GHz)
- Line: SO2 15(5,11)-16(4,12) (150.381 GHz)
- Line: SO2 18(2,16)-17(3,15) (163.119 GHz)
- Line: SO2 24(2,25)-25(1,25) (168.790 GHz)
- Line: SO2 5(2,4)-4(1,3) (not stated)
- Line: SO2 14(0,14)-14(1,13) / 14(0,14)-13(1,13) (not stated)
- Other facility **NOEMA**: Primary interferometric observations of HL Tau in Band 2 (146.4-154.2 GHz and 161.8-169.6 GHz) combining A- and B-array configurations (project W22BA).  
  > "Observations were carried out with NOEMA as part of project W22BA (PI: P. Rivière-Marichalar), combining the A- and B-array configurations in Band 2 from February 15 and March 22, 2023" (Observations and data reduction)
- External data: Molecular spectroscopic data from CDMS  
  > "Table notes: Molecular data from CDMS (cite: Muller2005)." (Table 1) [from (cite: Muller2005)]
- External data: ALMA SO2 transition detections toward HL Tau  
  > "(cite: Garufi2022) detected emission from 5$\rm _{2,4}$-4$\rm _{1,3}$, 14$\rm _{0,14}$-13$\rm _{1,13}$, and 3$\rm _{3,1}$-2$\rm _{2,0}$." (SO$\rm _2$) [from (cite: Garufi2022)]
- External data: Collisional rates for CS, H2S, and H2CO  
  > "We derived critical densities for the studied transitions using the Einstein coefficients for spontaneous emission from Table [\[Tab:line_fluxes\]](#Tab:line_fluxes) and collisional rates from (cite: DenisAlpizar2013) for CS, (cite: Dagdigian2020) for H$\rm _2$S, and (cite: Wiesenfeld2013) for H$\rm _2$CO." (Molecular column densities) [from (cite: DenisAlpizar2013), (cite: Dagdigian2020), (cite: Wiesenfeld2013)]
- Simulation/model as data: Grid of RADEX non-LTE radiative transfer models for excitation temperature and optical depth of CS, H2S, and H2CO.  
  > "To further support our assumption regarding T$\rm _{ex}$, we computed a grid of RADEX models (cite: vanDerTak2007) for a set of densities and CS, H$\rm_2$S, and H$\rm _2$CO column densities resembling those in a cold protostellar envelope" (Molecular column densities)

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

- Stellar mass (2.1 M_sun), inclination (i=46.7 deg), and position angle (PA=138 deg) of HL Tau  
  > "We assumed a stellar mass of 2.1 M$\rm _{\odot}$, and $i$=46.7$^{\circ}$, $PA$=138$^{\circ}$ (cite: Yen2019)." (CS, H$\rm _2$S, and H$\rm _2$CO) [from (cite: Yen2019)]
- Beam-integrated method for SO2 line fluxes  
  > "We integrated inside the beam area of the 4$\rm _{2,2}$-4$\rm _{1,3}$ transition centered at the position of the peak of the same transition line, following the beam-integrated method used by (cite: Garufi2022)." (SO$\rm _2$) [from (cite: Garufi2022)]
- Gas temperature of 15 K in the envelope for RADEX modeling  
  > "assuming a gas temperature of 15 K in the envelope (cite: Yen2017)." (Molecular column densities) [from (cite: Yen2017)]

### Not stated but needed to reproduce (our reading)

- Distance to HL Tau used to convert angular scales to physical scales (implicitly ~140 pc based on 0.75 arcsec = 105 au)
- Exact pixel coordinates or mask definition for the central absorption region and the CS, H2S, and H2CO emission peaks
- How the archival ALMA data (2018.1.01037.S) were calibrated and imaged or whether archive/literature products from Garufi et al. (2022) were used directly

## Analysis recipe

1. **Compute moment maps, Keplerian-masked maps, line fluxes, and radial profiles for CS, H2S, and H2CO**: Spectrally smooth cubes by a factor of 3, compute moment 0, 1, 2 maps (S/N > 4), apply Keplerian masks using bettermoments and make_mask, integrate fluxes within r = 1.6 arcsec masking out absorption, and compute deprojected azimuthally averaged radial profiles.  
  > "The data cubes were spectrally smoothed by a factor of three before computing the moment maps to boost the S/N." (CS, H$\rm _2$S, and H$\rm _2$CO); "In Fig. [3](#Fig:moments_KeplerMask) we show the integrated intensity maps after applying a Keplerian mask computed using `Bettermoments` (cite: Teague2018). We used the `make mask` tool[^2] (cite: makeMask) to produce the Keplerian masks." (CS, H$\rm _2$S, and H$\rm _2$CO); "Table [\[Tab:line_fluxes\]](#Tab:line_fluxes) includes line fluxes for CS, H$\rm _2$S, and H$\rm _2$CO integrated inside a radius of 1.6$\ensuremath{''}$ around the center of the zeroth-moment Keplerian-masked maps." (CS, H$\rm _2$S, and H$\rm _2$CO)
   - software: Bettermoments, make_mask
   - parameter: S/N > 4 threshold for unmasked moment maps; spectral smoothing factor = 3; integration radius = 1.6 arcsec  
  > "Only channels with an S/N larger than four were included." (CS, H$\rm _2$S, and H$\rm _2$CO)
   - assumption: M_star = 2.1 M_sun, i = 46.7 deg, PA = 138 deg  
  > "We assumed a stellar mass of 2.1 M$\rm _{\odot}$, and $i$=46.7$^{\circ}$, $PA$=138$^{\circ}$ (cite: Yen2019)." (CS, H$\rm _2$S, and H$\rm _2$CO)
   - fitting: _not stated_
   - validation: _not stated_
2. **Measure SO2 line fluxes and perform rotational diagram analysis combining NOEMA and ALMA transitions**: Integrate SO2 emission inside the beam area of the 4(2,2)-4(1,3) transition centered on its peak, recompute ALMA fluxes from Garufi et al. (2022), and fit a rotational diagram for T_rot and N(SO2).  
  > "We integrated inside the beam area of the 4$\rm _{2,2}$-4$\rm _{1,3}$ transition centered at the position of the peak of the same transition line, following the beam-integrated method used by (cite: Garufi2022)." (SO$\rm _2$); "We used the detected transitions to compute the rotational diagram of SO$\rm _2$. Assuming optically thin emission and the Rayleigh-Jeans limit, the rotation temperature and molecular column density can be derived" (SO$\rm _2$)
   - parameter: Partition function computed for 198 rotational levels  
  > "The partition function was computed for 198 rotational levels." (SO$\rm _2$)
   - assumption: Optically thin emission and Rayleigh-Jeans limit  
  > "Assuming optically thin emission and the Rayleigh-Jeans limit, the rotation temperature and molecular column density can be derived from the equations" (SO$\rm _2$)
   - fitting: Linear fit to rotational diagram  
  > "The results are shown in Fig. [8](#Fig:SO2_rot_diag). We derived a temperature of (60$\rm \pm$10) K and a column density of (3.0$\rm \pm$0.5)$\rm \times 10^{14}~cm^{-2}$." (SO$\rm _2$)
   - validation: Recomputed fluxes for transitions detected in Garufi et al. (2022) to ensure compatibility.  
  > "To ensure that our flux was compatible with the one used in (cite: Garufi2022), we recomputed the fluxes for the transitions detected in that work and retrieved compatible values." (SO$\rm _2$)
3. **Derive molecular column densities and ratios in the envelope and protoplanetary disk**: Compute optical depth and column density in the envelope from central absorption features for T_ex = 5 K and T_ex -> 0 K; compute LTE optically thin column densities in the disk at CS, H2S, and H2CO peaks and disk mean for T = 20, 40, and 58 K.  
  > "We applied the equations mentioned above to the absorption features in our NOEMA maps and derived the column density of CS, H$\rm _2$CO, and H$\rm _2$S in the absorbing envelope." (Molecular column densities); "We only have one transition per molecule, so we assumed local thermodynamical equilibrium (LTE) and optically thin emission." (Molecular column densities)
   - software: RADEX
   - parameter: Envelope T_ex = 5 K and T_ex -> 0 K; Disk T = 20 K, 40 K, and 58 K; ortho-to-para correction factor of 1.33 (OPR = 3) for H2S and H2CO  
  > "Thus, we multiplied the column densities computed for the o-species by a factor of 1.33 to retrieve the total column densities included in Table [\[Tab:col_dens\]](#Tab:col_dens)." (Molecular column densities)
   - assumption: Continuum source fills the beam for absorption; LTE and optically thin emission in the disk; ortho-to-para ratio of 3 for H2S and H2CO  
  > "To estimate the column densities, we assumed that the source fills the beam." (Molecular column densities); "Assuming that H$\rm _2$S behaves similar to H$\rm _2$O, we used an ortho-to-para ratio of three (cite: Hama2016)." (Molecular column densities)
   - fitting: _not stated_
   - validation: Computed a grid of RADEX models to validate T_ex <= 5 K in the envelope and to check optical depth tau = 1 thresholds in the disk.  
  > "To further support our assumption regarding T$\rm _{ex}$, we computed a grid of RADEX models (cite: vanDerTak2007) for a set of densities and CS, H$\rm_2$S, and H$\rm _2$CO column densities resembling those in a cold protostellar envelope" (Molecular column densities)

## Software

- **GILDAS** : Calibration and imaging (MAPPING package) of the NOEMA interferometric data.  
  > "The NOEMA data were calibrated using the continuum and line interferometer calibration package of GILDAS." (Observations and data reduction); "Imaging was performed with the MAPPING GILDAS package using natural weighting." (Observations and data reduction)
- **Bettermoments** : Computing Keplerian-masked integrated intensity maps.  
  > "In Fig. [3](#Fig:moments_KeplerMask) we show the integrated intensity maps after applying a Keplerian mask computed using `Bettermoments` (cite: Teague2018)." (CS, H$\rm _2$S, and H$\rm _2$CO)
- **make_mask** : Generating Keplerian masks.  
  > "We used the `make mask` tool[^2] (cite: makeMask) to produce the Keplerian masks." (CS, H$\rm _2$S, and H$\rm _2$CO)
- **RADEX** : Computing grids of non-LTE radiative transfer models for excitation temperature and line optical depth.  
  > "To further support our assumption regarding T$\rm _{ex}$, we computed a grid of RADEX models (cite: vanDerTak2007) for a set of densities and CS, H$\rm_2$S, and H$\rm _2$CO column densities resembling those in a cold protostellar envelope" (Molecular column densities)

## Numeric results

| quantity | value | uncertainty | units | step | quote |
|---|---|---|---|---|---|
| CS 3-2 integrated line flux | 0.35 | 0.05 | Jy km s^-1 | 1 | / CS / 3-2 / 146.969 / 0.81 $\times$ 0.31 / 14.10692 / 6.0517$\rm \times 10^{-5}$ / 0.35$\rm \pm$0.05 / |
| H2CO 2(1,1)-1(1,0) integrated line flux | 0.26 | 0.03 | Jy km s^-1 | 1 | / H$\rm _2$CO / 2$\rm _{1,1}$-1$\rm _{1,0}$ / 150.498 / 0.81 $\times$ 0.30 / 22.61771 / 3.5950$\rm \times 10^{-5}$ / 0.26$\rm \pm$0.03 / |
| H2S 1(1,0)-1(0,1) integrated line flux | 0.27 | 0.03 | Jy km s^-1 | 1 | / H$\rm _2$S / 1$\rm _{1,0}$-1$\rm _{0,1}$ / 168.762 / 0.72 $\times$ 0.26 / 27.87738 / 2.6773$\rm \times 10^{-5}$ / 0.27$\rm \pm$0.03 / |
| SO2 4(2,2)-4(1,3) integrated line flux | 0.028 | 0.005 | Jy km s^-1 | 2 | / SO$\rm _2$ / 4$\rm _{2,2}$-4$\rm _{1,3}$ / 146.605 / 0.81 $\times$ 0.31 / 19.02892 / 2.4697$\rm \times 10^{-5}$ / 0.028$\rm \pm$0.005 / |
| SO2 2(2,0)-2(1,1) integrated line flux | 0.014 | 0.003 | Jy km s^-1 | 2 | / SO$\rm _2$ / 2$\rm _{2,0}$-2$\rm _{1,1}$ / 151.379 / 0.74 $\times$ 0.27 / 12.58483 / 1.8752$\rm \times 10^{-5}$ / 0.014$\rm \pm$0.003 / |
| SO2 5(2,4)-5(1,5) integrated line flux | 0.035 | 0.06 | Jy km s^-1 | 2 | / SO$\rm _2$ / 5$\rm _{2,4}$-5$\rm _{1,5}$ / 165.144 / 0.74 $\times$ 0.27 / 23.58866 / 3.1223$\rm \times 10^{-5}$ / 0.035$\rm \pm$0.06 / |
| SO2 14(1,13)-14(0,14) integrated line flux | 0.026 | 0.005 | Jy km s^-1 | 2 | / SO$\rm _2$ / 14$\rm _{1,13}$-14$\rm _{0,14}$ / 163.605 / 0.75 $\times$ 0.27 / 101.75216 / 3.0054$\rm \times 10^{-5}$ / 0.026$\rm \pm$0.005 / |
| SO2 5(2,4)-4(1,3) recomputed ALMA flux | 120 | 8 | mJy km s^-1 | 2 | We retrieved a flux of (120$\rm \pm$8) mJy km s$\rm ^{-1}$ for the 5$\rm _{2,4}$-4$\rm _{1,3}$ transition and of (164$\rm \pm$8) mJy km s$\rm ^{-1}$ for the 14$\rm _{0,14}$-14$\rm _{1,13}$ transition. |
| SO2 14(0,14)-14(1,13) recomputed ALMA flux | 164 | 8 | mJy km s^-1 | 2 | We retrieved a flux of (120$\rm \pm$8) mJy km s$\rm ^{-1}$ for the 5$\rm _{2,4}$-4$\rm _{1,3}$ transition and of (164$\rm \pm$8) mJy km s$\rm ^{-1}$ for the 14$\rm _{0,14}$-14$\rm _{1,13}$ transition. |
| SO2 rotational temperature (NOEMA only) | 60 | 10 | K | 2 | We derived a temperature of (60$\rm \pm$10) K and a column density of (3.0$\rm \pm$0.5)$\rm \times 10^{14}~cm^{-2}$. |
| SO2 column density (NOEMA only) | 3.0e14 | 0.5e14 | cm^-2 | 2 | We derived a temperature of (60$\rm \pm$10) K and a column density of (3.0$\rm \pm$0.5)$\rm \times 10^{14}~cm^{-2}$. |
| SO2 rotational temperature (NOEMA + ALMA) | 56 | 5 | K | 2 | This resulted in a temperature of (56$\rm \pm$5) K and a column density of (3.0$\rm \pm$0.3)$\rm \times 10^{14}~cm^{-2}$. |
| SO2 column density (NOEMA + ALMA) | 3.0e14 | 0.3e14 | cm^-2 | 2 | This resulted in a temperature of (56$\rm \pm$5) K and a column density of (3.0$\rm \pm$0.3)$\rm \times 10^{14}~cm^{-2}$. |
| Disk mean N(CS)/N(H2S) ratio at T = 58 K | 0.7 | 0.2 | dimensionless | 3 | / Disk mean / (3.2$\rm \pm 1.4$)$\rm \times 10^{12}$ / (5.6$\rm \pm 2.6$)$\rm \times 10^{12}$ / (8.4$\rm \pm$4.0)$\rm \times 10^{12}$ / 0.7$\rm \pm$0.2 / 0.4$\rm\pm$0.1 / 0.6$\rm \pm$0.2 / |
| Envelope N(CS)/N(H2S) ratio at T_ex = 5 K | 28 | 12 | dimensionless | 3 | / Envelope / (4.7$\rm \pm0.4$)$\rm \times 10^{14}$ / (3$\rm \pm$1)$\rm \times 10^{13}$ / (2.0$\rm \pm$0.9)$\rm \times 10^{14}$ / 28$\rm \pm$12 / 4$\rm \pm$2 / 0.15$\rm \pm$0.12 / |
| Envelope N(CS)/N(H2S) ratio at T_ex -> 0 K | 16 | 8 | dimensionless | 3 | / / (2.7$\rm \pm0.6$)$\rm \times 10^{14}$ / (1.3$\rm \pm$0.4)$\rm \times 10^{13}$ / (7$\rm \pm$3)$\rm \times 10^{13}$ / 16$\rm \pm$8 / 3$\rm \pm$2 / 0.19$\rm \pm$0.14 / |

## Qualitative findings

- CS, H2S, and H2CO show broken ring morphologies surrounding central absorption and peak at similar deprojected radial distances (~105-111 au), showing no radial chemical segregation within the beam resolution.  
  > "CS and H$\rm _2$CO peak at the same position (0.75$\ensuremath{''}$, $\sim$ 105 au), while H$\rm _2$S peaks slightly farther out (0.8$\ensuremath{''}$, $\sim$ 111 au)." (Radial profiles); "Accordingly, we observed no hints of chemical segregation in the radial direction within the angular resolution of our observations." (Radial profiles)
- SO2 is only detected in emission on the western/southwestern side of the disk and along the streamer filament, with no central absorption.  
  > "Three species, H$\rm _2$S, CS, and H$\rm _2CO$, are detected at all azimuths, while SO$\rm _2$ is only detected at the southwestern side of the disk." (Summary and conclusions)

## Claim tuples

- H: Comparing molecular column density ratios between the envelope and protoplanetary disk of HL Tau reveals whether gas is chemically reprocessed from the envelope to the disk. | E: Derive column densities and ratios of CS, H2S, and H2CO in the absorbing envelope and emitting protoplanetary disk using NOEMA observations. | R: The N(CS)/N(H2S) ratio is 23 to 70 times (40 to 50 times in abstract/summary) larger in the envelope than in the disk. | F: Significant differences in molecular ratios between the envelope and disk indicate chemical reprocessing/evolution during the transition from envelope to protoplanetary disk, and N(CS)/N(H2S) can differentiate envelope from disk emission. | **supported**
- H: Localized SO2 emission and azimuthal chemical variations in the HL Tau disk are linked to the impact of a large-scale infalling streamer. | E: Map four SO2 transitions with NOEMA, combine with ALMA detections from Garufi et al. (2022) in a rotational diagram, and compare N(H2S)/N(H2CO) across disk emission peaks. | R: SO2 is detected only on the western side where the streamer impacts the disk with T_rot = 56 +/- 5 K and N(SO2) = (3.0 +/- 0.3)e14 cm^-2, and N(H2S)/N(H2CO) varies by almost a factor of five between the H2S and H2CO peaks. | F: SO2 emission likely traces gas sputtered/desorbed from dust grains by shocks where the streamer impacts the disk, while azimuthal variations in molecular ratios reflect localized streamer impact and differing turbulence. | **supported**

## Reasoning

- Why this data: HL Tau shows deep molecular absorption lines from its infalling envelope alongside disk emission, allowing direct comparison of column densities in the envelope and disk.  
  > "The source we focus on is HL Tau, where molecular absorption lines from the envelope have been detected, thus allowing for the derivation of column densities and molecular abundances." (Observations of sulfuretted species in HL Tau)
- Why this method: _not stated_
- Alternative: Thermal desorption as the origin of SO2 emission was rejected because it would produce azimuthally symmetric emission rather than localized western emission.  
  > "As pointed out by (cite: Garufi2022), thermal desorption would result in an azimuthally symmetrical emission, rather than a localized emission." (SO$\rm _2$ detection)
- How they decided it was enough: _not stated_
- Limitation (authors): SO2 column densities are lower limits because optically thick SO2 emission lines cannot be ruled out.  
  > "Since we cannot rule out optically thick SO$\rm _2$ emission lines, the column densities reported here are lower limits." (SO$\rm _2$)
- Limitation (authors): Only one transition per molecule (CS, H2S, H2CO) was observed, requiring LTE and optically thin assumptions for disk column densities.  
  > "We only have one transition per molecule, so we assumed local thermodynamical equilibrium (LTE) and optically thin emission." (Molecular column densities)
- Limitation (authors): Dust optical depth at 2 mm (tau ~ 1) could cause continuum oversubtraction if line emission originates in colder regions like the midplane, making disk column densities lower limits.  
  > "However, if the emission originates in a region with lower temperatures, such as the mid-plane, over-subtraction could be an issue. In any case, the reported column densities act as lower limits." (Molecular column densities)
- Caveat (inferred, ours): Envelope column densities are measured along a single line of sight toward the central continuum absorption peak, whereas disk column densities are measured at outer ring peaks (~105 au), so the comparison probes different physical radii as well as different components.
- Caveat (inferred, ours): Single-transition disk column densities rely on assumed uniform excitation temperatures (20, 40, 58 K) across all three molecules.

## Reproducibility

- Data public (paper): Processed data cubes are publicly available at the CDS.  
  > "Data cubes are available at the CDS via anonymous ftp to cdsarc.u-strasbg.fr (130.79.128.5) or via http://cdsweb.u-strasbg.fr/cgi-bin/qcat?J/A+A/." (Data availability)
- Products in archive: _not stated_
- Missing: Exact pixel coordinates of the CS, H2S, and H2CO emission peaks and the central absorption region
- Missing: Exact beam area center coordinates used for the SO2 4(2,2)-4(1,3) integration
- Missing: Details of the archival ALMA image cubes used to recompute the Garufi et al. (2022) SO2 fluxes
- Data volume (inferred): ~1-5 GB (CDS data cubes and archival ALMA cubes)
- Score (inferred): 75/5, Processed NOEMA data cubes are publicly hosted at CDS, equations for rotational diagrams and optical depth/column density are explicitly given, and analysis tools (bettermoments, make_mask, RADEX) are public, though exact aperture/pixel coordinates for peak extractions are not tabulated.
- Rediscovery candidate: yes, The calibrated/imaged data cubes are publicly available on CDS, the archival ALMA data (2018.1.01037.S) are public, and the analytical equations to derive fluxes, rotational temperatures, and column densities are straightforward and yield explicit numeric benchmarks.

## Links

- Method: (cite: Teague2018) (Bettermoments tool used to compute Keplerian-masked integrated intensity maps)
- Method: (cite: makeMask) (make_mask tool used to generate Keplerian masks)
- Method: (cite: vanDerTak2007) (RADEX radiative transfer code used for excitation and optical depth grids)
- Companion: (cite: Garufi2022) (Provided the ALMA SO2 detections and beam-integrated flux methodology combined with the NOEMA observations in this work)
- Companion: (cite: Yen2019) (Provided the disk geometry parameters, stellar mass, and prior detection of infalling streamer and central absorption in HL Tau)

## Checks

```json
{
 "quotes": 81,
 "quotes_ok": 81,
 "quote_pass_rate": 1.0,
 "quotes_too_long": 0,
 "unsupported_facts": 0,
 "project_codes": 1,
 "codes_not_in_text": [],
 "codes_not_in_obscore": [],
 "obscore_codes_not_in_card": [],
 "codes_printed_but_missing": [],
 "numeric_results": 16,
 "numeric_problems": 0,
 "fill": {
  "facts": 76,
  "stated": 35,
  "rate": 0.461
 },
 "evidence_ok": true
}
```
