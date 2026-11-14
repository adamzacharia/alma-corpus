# ALMA imaging of C<SUB>2</SUB>H emission in the disk of <ASTROBJ>NGC 1068</ASTROBJ>

`2017A&A...608A..56G` | Astronomy and Astrophysics 2017 | first author: García-Burillo, S. | arXiv: 1709.05895 | DOI: 10.1051/0004-6361/201731862

Card schema 1.0 | model claude-sonnet-5-5 | depth full | type observational_alma_primary

## Science

- Fields: nearby_galaxies, astrochemistry, agn_and_quasars
- Question: Do the fractional abundances of C2H differ between the starburst ring and the AGN-driven outflow region of NGC 1068, and what chemistry (PDR, shocks, gas-grain) explains them?  
  > "by analyzing if the abundances of key molecular species like ethynyl (C$_2$H), a classical tracer of Photon Dominated Regions (PDR), change in the different environments of the disk of the galaxy." (abstract)
- Target **NGC 1068**: coordinates 02h42m40.771s, -00d00m47.84s (phase center, J2000)  
  > "The phase tracking center was set to $\alpha_{2000}=02^{h}42^{m}40.771^{s}$, $\delta_{2000}=-00^{\circ}00^{\prime}47.84\ensuremath{''}$" (3 Observations (ALMA data)); "Hereafter we assume a distance to NGC 1068 of $D\simeq14$ Mpc (cite: Bla97)" (1.1 The target: NGC 1068); z/distance D ~ 14 Mpc (70 pc/arcsec)  
  > "The phase tracking center was set to $\alpha_{2000}=02^{h}42^{m}40.771^{s}$, $\delta_{2000}=-00^{\circ}00^{\prime}47.84\ensuremath{''}$" (3 Observations (ALMA data)); "Hereafter we assume a distance to NGC 1068 of $D\simeq14$ Mpc (cite: Bla97)" (1.1 The target: NGC 1068); distance from Bland-Hawthorn et al. 1997 (Bla97)  
  > "The phase tracking center was set to $\alpha_{2000}=02^{h}42^{m}40.771^{s}$, $\delta_{2000}=-00^{\circ}00^{\prime}47.84\ensuremath{''}$" (3 Observations (ALMA data)); "Hereafter we assume a distance to NGC 1068 of $D\simeq14$ Mpc (cite: Bla97)" (1.1 The target: NGC 1068)

## Data provenance

- ALMA projects: 2013.1.00055.S, 2011.0.00083.S
- bands: Band 3, single pointing (C2H); Band 7 Cycle 0 for CO(3-2) and 349 GHz continuum  
  > "We used Band 3 receivers and a single pointing." (2.1 ALMA data)
- frequencies and spectral setup: Four 1.875 GHz spectral windows (2 LSB, 2 USB), ~0.98 MHz (3.4 km/s) resolution; lowest LSB window centred at 86.3082 GHz  
  > "We used four spectral windows each with a bandwidth of 1.875 GHz and a spectral resolution of $\simeq0.98$ MHz (3.4 km s$^{-1}$)." (2.1 ALMA data)
- continuum bandwidth: _not stated_
- arrays: 34 antennas, one track  
  > "We observed one track in August 2015 with 34 antennas with projected baselines ranging from 12 m to 1430 m." (2.1 ALMA data)
- configurations: _not stated_
- baselines: 12 m to 1430 m  
  > "projected baselines ranging from 12 m to 1430 m" (2.1 ALMA data)
- angular resolution: 1.0" x 0.7" (70 x 50 pc), PA = 69 deg, natural weighting  
  > "The angular resolution obtained using natural weighting was $1.0\ensuremath{''}~\times~0.7\ensuremath{''}$ (70 pc $\times~50$ pc) at a position angle $PA=69^{\circ}$" (2.1 ALMA data)
- max recoverable scale: ~4"  
  > "the latter corresponds to the expected largest angular scale of the emission that can be recovered in the ALMA maps used in this work" (2.1 ALMA data)
- sensitivity: line rms ~0.4 mJy/beam per ~10 km/s channel; continuum 80 uJy/beam  
  > "is $\simeq0.4$ mJy beam$^{-1}$ in $\simeq10$ km s$^{-1}$-channels." (2.1 ALMA data); "The corresponding point source sensitivity for the continuum is 80 $\mu$Jy beam$^{-1}$." (2.1 ALMA data)
- time on source: _not stated_
- observing dates: August 2015 (Cycle 2)  
  > "We observed one track in August 2015" (2.1 ALMA data)
- pi or archival as stated: Own Cycle 2 program (PI Garcia-Burillo); Cycle 0 Band 7 data from previous publications  
  > "project-ID: $\#$2013.1.00055.S; PI: S. Garcı́a-Burillo" (2.1 ALMA data)
- Line: C2H N=1-0 hyperfine multiplet (strongest J=3/2-1/2, F=2-1) (87.317 GHz)
- Line: CO J=3-2 (Cycle 0 data) (not stated)
- Other facility **HST NICMOS (NIC3) via Hubble Legacy Archive**: Pa-alpha narrow-band images (F187N, F190N) tracing star formation  
  > "We retrieved the HST NICMOS (NIC3) narrow-band (F187N, F190N) data of NGC 1068 from the Hubble Legacy Archive (HLA)" (2.2 Ancillary data)
- External data: 349 GHz ALMA dust continuum map used for N(H2)  
  > "we have estimated $N$(H$_2$) from the ALMA dust continuum emission map of the galaxy obtained at 349 GHz by (cite: GB14)" (3.4 C2H abundances) [from (cite: GB14)]
- External data: Kinetic temperature constraints (LVG/LTE/RADEX) from multiline CO, HCN, HCO+ used to set Tex 10-150 K  
  > "encompasses the total span of kinetic temperatures found by (cite: Vit14) in their Large Velocity Gradient (LVG) fit" (3.4 C2H abundances) [from (cite: Vit14)]
- External data: Dust emissivity at 352 GHz ~0.09 m2/kg  
  > "$\kappa_{{\rm 352~GHz}}\simeq0.09$ m$^2$ kg$^{-1}$(cite: Kla01)" (3.4 C2H abundances) [from (cite: Kla01)]
- External data: Gas-to-dust ratio ~60 from Draine dust/gas scaling and oxygen abundances  
  > "which yields a gas–to–dust mass ratio of $\sim60^{+30}_{-30}$ (cite: GB14)" (3.4 C2H abundances) [from (cite: Dra07; Pil04; Pil07; GB14)]
- External data: Rotation curve model of the disk subtracted from p-v diagrams  
  > "we have subtracted the rotation curve model of (cite: GB14) projected along each individual p-v plot before averaging" (3.2 C2H map) [from (cite: GB14)]
- External data: Theoretical hyperfine line strengths for opacity fit  
  > "optical depth ratios are based on the theoretical line strengths (cite: Tuc74)" (3.3 C2H line opacities) [from (cite: Tuc74)]
- External data: Grid of UCL_CHEM models  
  > "We use and augment the grid of chemical models from (cite: Vit17) run using the UCL_CHEM time dependent gas-grain chemical model" (4.1 Chemical models: description) [from (cite: Vit17; Vit11)]
- Simulation/model as data: Chemical model grids: 4 UCL_PDR models (48-51), 41 UCL_CHEM gas-grain models (1-44 listed), 3 parametrized shock models (45-47, Vs~40 km/s)  
  > "Tables [2](#Tab4), [3](#Tab5) and [4](#Tab6) list, respectively, the parameters of the grid of UCL_PDR, UCL_CHEM and shock models we considered." (4.2 Chemical models: results)

## Processing

### Calibration

- pipeline or manual: Calibrated with CASA; details not given  
  > "We calibrated the data using the ALMA reduction package `CASA`[^1]." (2.1 ALMA data)
- casa version: _not stated_
- pipeline version: _not stated_
- archive products used as is: _not stated_
- flux calibrator: _not stated_
- flux scale uncertainty: 10-15%  
  > "We estimate that the absolute flux accuracy in the maps is about 10–15$\%$." (2.1 ALMA data)
- self calibration: _not stated_

### Imaging

- task: Calibrated uv-tables exported to GILDAS; mapping and cleaning done there  
  > "The calibrated uv-tables were transformed to `GILDAS`[^2]-readable format where the mapping and cleaning were performed." (2.1 ALMA data)
- deconvolver: _not stated_
- weighting robust: natural weighting  
  > "The angular resolution obtained using natural weighting was" (2.1 ALMA data)
- uv taper: _not stated_
- cell size: _not stated_
- image size: _not stated_
- masking: _not stated_
- multiscale scales: _not stated_
- continuum subtraction: _not stated_
- line free channels: Continuum at 86.3 GHz from 60 line-free channels (~600 km/s) around C2H group  
  > "obtained by averaging 60 channels ($\simeq600$ km s$^{-1}$) free of line emission around the C$_2$H group" (2.1 ALMA data)
- primary beam correction: Applied, assuming 70" FWHM  
  > "All the maps have been corrected for the attenuation by the primary beam, assuming a FWHM of 70$\ensuremath{''}$ for the latter." (2.1 ALMA data)
- array combination: No short-spacing correction  
  > "As our observations do not contain short-spacing correction" (2.1 ALMA data)
- smoothing: Line cube binned to ~2.92 MHz (~10 km/s)  
  > "The line data cube was binned to a frequency resolution of $\simeq2.92$ MHz ($\simeq$10 km s$^{-1}$)." (2.1 ALMA data)
- final beam: 1.0" x 0.7", PA 69 deg  
  > "$1.0\ensuremath{''}~\times~0.7\ensuremath{''}$ (70 pc $\times~50$ pc) at a position angle $PA=69^{\circ}$" (2.1 ALMA data)
- final rms: 0.4 mJy/beam per 10 km/s channel; continuum 80 uJy/beam  
  > "is $\simeq0.4$ mJy beam$^{-1}$ in $\simeq10$ km s$^{-1}$-channels." (2.1 ALMA data)

### Inherited from earlier work

- Systemic velocity 1136 km/s used as velocity reference  
  > "derived relative to $v_{\rm sys}^{\rm HEL}$=1136 km s$^{-1}$ (cite: GB16)" (2.1 ALMA data) [from (cite: GB16)]
- HST Pa-alpha images reprocessed with calibration pipeline  
  > "These images were completely reprocessed with a calibration pipeline as explained in detail in Sect. 2.2 of (cite: GB14)." (2.2 Ancillary data) [from (cite: GB14)]
- Cycle 0 Band 7 CO(3-2) and continuum data reduction  
  > "published by (cite: GB14) and (cite: Vit14)" (2.2 Ancillary data) [from (cite: GB14; Vit14)]
- Outflow axis PA=30 deg  
  > "which is oriented along $PA=$ 30$^{\circ}$ (cite: GB14)" (3.2 C2H map) [from (cite: GB14)]

### Not stated but needed to reproduce (our reading)

- CASA version and calibrators (flux, bandpass, phase) not given
- GILDAS clean parameters (cell size, image size, clean threshold, mask) not given
- Exact definitions of the SB ring and outflow regions used for spatial averaging of X(C2H)
- Dust temperature adopted when converting 349 GHz continuum to M_dust/N(H2)
- Method/regridding used to degrade the N(H2) map to the C2H resolution
- How the 349 GHz Band 7 continuum was processed and whether a flux correction was applied
- UCL_CHEM/UCL_PDR input networks, grids and exact outputs per model (only parameter tables given)
- Uncertainty derivation of abundances in Table 1

## Analysis recipe

1. **Image continuum and C2H line cubes**: Calibrate in CASA, map and clean in GILDAS with natural weighting; bin to 10 km/s; continuum from 60 line-free channels  
  > "The calibrated uv-tables were transformed to `GILDAS`[^2]-readable format where the mapping and cleaning were performed." (2.1 ALMA data)
   - software: CASA, GILDAS
   - fitting: _not stated_
   - validation: ALMA flux over 29" aperture (~35 Jy km/s) compared to IRAM-30m (47 Jy km/s), 75-85% recovered  
  > "The corresponding flux measured by ALMA for the same aperture is $\simeq35\pm5$ Jy km s$^{-1}$, which is $\simeq75-85\%$ of the 30m flux estimates." (2.1 ALMA data)
2. **Make C2H integrated-intensity map and p-v diagrams**: Integrate over v-vsys in [-510,200] km/s; p-v diagrams averaged along 5 axes (PA 10-50 deg) after subtracting rotation curve  
  > "Intensities have been integrated at each pixel inside the velocity interval defined by: $v-v_{\rm sys}^{\rm HEL}\subset[ -510, 200]$ km s$^{-1}$." (3.2 C2H map)
   - fitting: _not stated_
   - validation: Compared to CO(3-2) morphology and kinematics  
  > "the emission of C$_2$H follows closely the velocities associated with the CO outflow in this region" (3.2 C2H map)
3. **Estimate C2H line opacities**: Fit four Gaussian hyperfine components with common widths and Tex, optical depth ratios fixed by theoretical line strengths; free centroids and tau_str  
  > "We have performed a fit of the spectra shown in Fig. [3](#Fig3) using a comb of four Gaussian profiles that correspond to the strongest hyperfine components" (3.3 C2H line opacities)
   - fitting: Gaussian comb fit; sampler/likelihood not stated  
  > "We have performed a fit of the spectra shown in Fig. [3](#Fig3) using a comb of four Gaussian profiles that correspond to the strongest hyperfine components of the C$_2$H(1–0) multiplet." (C$_2$H line opacities)
   - validation: Compared to secondary-to-main intensity ratio R vs optically thin limit 0.46  
  > "which is very close to the optically thin limit for $R$ ($\simeq0.46$)" (3.3 C2H line opacities)
4. **Derive C2H column density in LTE**: Renormalize multiplet intensity by 0.46 to main line; optically thin LTE with filling factor 1 via Boltzmann equation for Tex=10-150 K  
  > "we have first re-normalized the observed intensities by a factor $\simeq0.46$ defined by the expected ratio of intensities of the strongest main line" (3.4 C2H abundances)
   - parameter: Tex = 10, 25, 50, 100, 150 K  
  > "we will assume a range of temperatures ($T_{\rm ex}$=10–150 K)" (3.4 C2H abundances)
   - assumption: LTE, optically thin, filling factor unity  
  > "If the emission is assumed to be optically thin, and if we adopt a filling factor of unity" (3.4 C2H abundances)
   - fitting: _not stated_
   - validation: Lower limit Tex >= 8 K from fitted eta_f*(Tex-Tbg)*tau  
  > "the formal lower limit on $T_{\rm ex}\geq8$ K" (3.4 C2H abundances)
5. **Derive H2 column density from 349 GHz dust continuum**: Modified black-body to get dust mass per beam; convert with gas-to-dust ratio ~60; degrade map to C2H resolution  
  > "We have used a modified black-body law to derive the dust mass ($M_{\rm dust}$)." (3.4 C2H abundances)
   - parameter: kappa_349GHz ~ 0.09 m2/kg  
  > "$\kappa_{{\rm 352~GHz}}\simeq0.09$ m$^2$ kg$^{-1}$(cite: Kla01)" (3.4 C2H abundances)
   - assumption: Gas-to-dust ~60; optically thin dust; negligible HI; D=14 Mpc  
  > "because the dust continuum emission at 349 GHz is mostly optically thin" (3.4 C2H abundances)
   - fitting: _not stated_
   - validation: _not stated_
6. **Compute fractional abundances X(C2H) and compare with chemical models**: X = N(C2H)/N(H2) averaged over SB ring and outflow regions; compared with UCL_PDR, UCL_CHEM and parametrized shock model grids  
  > "using a set of time-dependent gas-grain chemical models, parametrized shock models, and gas-phase PDR models" (4 The origin of the C2H abundances)
   - software: UCL_CHEM, UCL_PDR
   - parameter: Solar C/O ~0.6; shock velocity ~40 km/s; cosmic-ray ionization 5e-17 s-1 standard  
  > "We assume for all the models a solar C/O abundance ratio $\sim$ 0.6." (4.1 Chemical models: description)
   - assumption: Cosmic-ray ionization used to mimic X-ray enhancement  
  > "The grid of models we employ from (cite: Vit17) uses the cosmic-ray ionization flux to also simulate an enhancement in X-ray flux." (4.1 Chemical models: description)
   - fitting: No formal fit; qualitative comparison  
  > "Hence we can only qualitatively discuss the origin of this emission" (4.1 Chemical models: description)
   - validation: _not stated_

## Software

- **CASA** : Calibration of ALMA data  
  > "We calibrated the data using the ALMA reduction package `CASA`[^1]." (2.1 ALMA data)
- **GILDAS** : Mapping and cleaning  
  > "where the mapping and cleaning were performed" (2.1 ALMA data)
- **UCL_CHEM** : Time-dependent gas-grain chemistry and parametrized shock models  
  > "The code UCL_CHEM (cite: Hol17) is a time dependent gas-grain chemical model" (4.1 Chemical models: description)
- **UCL_PDR** : 1D time-dependent gas-phase PDR models  
  > "the UCL_PDR code is a 1 D time dependent PDR code" (4.1 Chemical models: description)

## Numeric results

| quantity | value | uncertainty | units | step | quote |
|---|---|---|---|---|---|
| ALMA angular resolution | 1.0 x 0.7 | not stated | arcsec | 1 | with a spatial resolution $1.0\ensuremath{''}\times0.7\ensuremath{''}$ |
| Fraction of total C2H flux from SB ring | ~65 | not stated | % | 2 | a sizeable fraction ($\simeq65\%$) of the total (spatially-integrated) C$_2$H line flux recovered by ALMA stems from the SB ring region |
| ALMA C2H flux in 29" aperture | 35 | 5 | Jy km/s | 2 | $\simeq35\pm5$ Jy km s$^{-1}$ |
| Average R (secondary/main) in CND | 0.49 | 0.05 | dimensionless | 3 | $<R>~\simeq0.49\pm0.05$ |
| Average R in bow-shock arc | 0.70 | 0.09 | dimensionless | 3 | $<R>~\simeq0.70\pm0.09$ |
| Average R in SB ring | 0.56 | 0.06 | dimensionless | 3 | $<R>~\simeq0.56\pm0.06$ |
| tau_str at OUT-III | 1.3 | 0.6 | dimensionless | 3 | $\tau_{\rm str}\simeq1.3~(\pm0.6)$ |
| X(C2H) SB ring, Tex=10 K | 1.3e-8 | 0.7e-8 | dimensionless | 6 | T$_{\rm ex}$=10 K  / $(1.3\pm0.7)\times10^{-8}$ / $(1.6\pm0.8)\times10^{-8}$ |
| X(C2H) outflow, Tex=25 K | 1.1e-7 | 0.4e-7 | dimensionless | 6 | T$_{\rm ex}$=25 K  / $(9.7\pm4.0)\times10^{-8}$ / $(1.1\pm0.4)\times10^{-7}$ |
| X(C2H) outflow, Tex=50 K | 4.8e-7 | 2.0e-7 | dimensionless | 6 | T$_{\rm ex}$=50 K  / $(4.3\pm2.0)\times10^{-7}$ / $(4.8\pm2.0)\times10^{-7}$ |

## Qualitative findings

- C2H traces the interface between the molecular disk and ionized outflow better than CO, lying at the edges of the Pa-alpha and radio continuum emission  
  > "The C$_2$H line seems to probe better than CO the interface between the molecular disk and the ionized gas outflow on the same spatial scales." (3.2 C2H map)

## Claim tuples

- H: C2H abundance differs between SB ring and outflow region | E: LTE column densities from ALMA C2H divided by N(H2) from 349 GHz dust continuum | R: X(C2H) a few 1e-8 in SB ring, a few 1e-7 in outflow (for adopted Tex) | F: Abundances are higher in the outflow, though strongly dependent on assumed Tex | **partially**
- H: PDR/gas-grain chemistry explains C2H in SB ring | E: Compare with UCL_CHEM/UCL_PDR grids | R: Models such as 37 (Galactic UV, 1e4 cm-3, Av=1) match ~1e-8 at steady state | F: C2H in the SB ring consistent with PDR gas tracing star formation | **supported**
- H: High outflow C2H abundance requires non-PDR conditions | E: Compare with UV/X-ray enhanced models and shock models | R: High abundances reached only at very early times (<=1e2-3 yr) in irradiated dense gas; shock model 46 approaches LTE values | F: Transient UV/X-ray irradiated non-dissociative shocks at the outflow interface, continually resupplied | **partially**
- H: C2H lines are optically thin | E: Hyperfine fits and R ratios | R: tau_str <=0.1-0.2 except bow-shock arc (~1.3) | F: Mostly optically thin | **supported**

## Reasoning

- Why this data: _not stated_
- Why this method: Only one C2H transition available, so LTE with a range of Tex adopted from CO studies  
  > "As we only have one line multiplet of C$_2$H, we will assume a range of temperatures" (3.4 C2H abundances)
- Alternative: Pure gas-phase low-density PDR models (48-51) never exceed C2H abundance of 1e-9  
  > "none of the pure gas-phase low density (10$^3$ cm$^{-3}$) PDR models (Models 48-51; Table [2](#Tab4)), at any time or depth into the cloud, succeed in achieving a fractional abundance of C$_2$H larger than 10$^{-9}$" (4.2 Chemical models: results)
- How they decided it was enough: _not stated_
- Limitation (authors): Single C2H transition gives uncertain abundance; chemical modelling is limited and qualitative  
  > "we are aware of the limitations of having observed only one $N$ transition of the C$_2$H multiplet, leading to an uncertain derivation of the fractional abundance" (4.1 Chemical models: description)
- Limitation (authors): No short-spacing correction; extended emission filtered on scales >4"  
  > "we expect to start filtering out an increasing fraction of the line and continuum emissions on scales $>4\ensuremath{''}$" (2.1 ALMA data)
- Caveat (inferred, ours): Abundances span two orders of magnitude with Tex, so the SB vs outflow difference rests on an assumed factor 2-3 in Tex
- Caveat (inferred, ours): Model comparison is qualitative with no fitting or uncertainty on model abundances
- Caveat (inferred, ours): LTE with Tex assumed from CO may be inappropriate for sub-thermally excited C2H (critical density 2e5)
- Caveat (inferred, ours): Shock interpretation not unique; UV vs X-ray cannot be distinguished

## Reproducibility

- Data public (paper): ALMA project IDs given; data acknowledged via ADS/JAO  
  > "This paper makes use of the following ALMA data: ADS/JAO.ALMA$\#$2013.1.00055.S and $\#$2011.0.00083.S." (Acknowledgements)
- Products in archive: _not stated_
- Missing: Calibration and cleaning parameters
- Missing: Region definitions and N(H2) map construction details
- Missing: Model grid outputs
- Data volume (inferred): ~10-50 GB for Band 3 track plus Band 7 data
- Score (inferred): 5/5, Data identifiable and key numbers given, but cleaning details, region definitions and H2 map construction are underspecified and chemical modelling is qualitative.
- Rediscovery candidate: no, Recipe lacks imaging and region details and main conclusions rely on qualitative chemical modelling with assumed Tex.

## Links

- Method: (cite: Vit17; Vit11; Hol17) (UCL_CHEM model grids and code)
- Method: (cite: Bel05; Bel06; Bay12) (UCL_PDR code)
- Companion: (cite: GB14) (Cycle 0 ALMA CO(3-2) and 349 GHz continuum of NGC 1068, outflow characterization)
- Companion: (cite: Vit14) (Multiline CO/HCN/HCO+ excitation analysis)
- Related: IRAM-30m single-dish C2H observations (Costagliola 2011; Aladro 2013)

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
 "numeric_results": 10,
 "numeric_problems": 0,
 "fill": {
  "facts": 88,
  "stated": 64,
  "rate": 0.727
 },
 "evidence_ok": true
}
```
