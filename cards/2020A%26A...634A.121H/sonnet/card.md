# The headlight cloud in NGC 628: An extreme giant molecular cloud in a typical galaxy disk

`2020A&A...634A.121H` | Astronomy and Astrophysics 2020 | first author: Herrera, Cinthya N. | arXiv: 1910.14311 | DOI: 10.1051/0004-6361/201936060

Card schema 1.0 | model claude-sonnet-5-5 | depth full | type observational_alma_primary

## Science

- Fields: nearby_galaxies, star_formation, milky_way_ism
- Question: What are the molecular gas properties, young stellar population, feedback and galactic environment of the brightest CO(2-1) cloud (the headlight cloud) in the disk of NGC 628?  
  > "In this paper, we study the brightest cloud traced in CO(2$-$1) emission in the disk of nearby spiral galaxy NGC 628." (abstract)
- Target **NGC 628 headlight cloud**: coordinates RA 01:36:45.328, Dec +15:47:48.48 (J2000)  
  > "| L1$^{\star}$ | 01:36:45.328 | 15:47:48.48 |" (Table 1); "(47 pc in linear scale at a distance of 9.6 Mpc)" (Reduction and Imaging); z/distance 9.6 Mpc  
  > "| L1$^{\star}$ | 01:36:45.328 | 15:47:48.48 |" (Table 1); "(47 pc in linear scale at a distance of 9.6 Mpc)" (Reduction and Imaging); distance from _not stated_

## Data provenance

- ALMA projects: 2012.1.00650.S, 2013.1.00532.S
- bands: Band 6 (Cycle 1: CO(2-1), CS(5-4)); Band 3 (Cycle 2: 90, 110, 115 GHz setups)  
  > "ALMA Band 6 observations were obtained during Cycle 1 to image the emission of $^{12}$CO(2$-$1)" (Observations); "Three band 3 frequency setups at 90, 110 and 115 GHz were required to cover all these emission lines." (3 mm lines)
- frequencies and spectral setup: _not stated_
- continuum bandwidth: _not stated_
- arrays: 12-m, 7-m and Total Power  
  > "12-m, 7-m, and Total Power observations were performed." (Observations)
- configurations: _not stated_
- baselines: _not stated_
- angular resolution: CO(2-1) 1.0"; CO(1-0) 1.9"x3.1"; 13CO 2.6"x3.5"; HCN 2.1"x2.2"  
  > "| $^{13}$CO(1$-$0) | 110.20 | 0.03 | 2$\ensuremath{''}$6 $\times$ 3$\ensuremath{''}$5 | 6.0 | yes |" (Table 1)
- max recoverable scale: _not stated_
- sensitivity: noise 0.17 K (CO(2-1), headlight region), 0.12 K CO(1-0), 0.03 K 13CO, ~1.1-1.2 K HCN/HCO+/HNC  
  > "| $^{12}$CO(2$-$1) | 230.54 | 0.17$^{\rm a}$ |" (Table 1)
- time on source: _not stated_
- observing dates: _not stated_
- pi or archival as stated: _not stated_
- Line: 12CO 2-1 (230.54 GHz)
- Line: 12CO 1-0 (115.27 GHz)
- Line: 13CO 1-0 (110.20 GHz)
- Line: HCN 1-0 (88.63 GHz)
- Line: HCO+ 1-0 (89.19 GHz)
- Other facility **VLT/MUSE**: Halpha, Hbeta and stellar continuum for the HII region  
  > "We use MUSE observations to characterize the ionized gas and stellar content associated with the headlight cloud." (Complementary MUSE data)
- External data: MUSE Halpha luminosity and H II region properties of the headlight  
  > "The extinction-corrected H$\alpha$ luminosity associated with the headlight cloud (cite: kreckel16; kreckel18)" (Young stellar content) [from (cite: kreckel16; kreckel18)]
- External data: EMPIRE line ratios for nearby galaxies  
  > "using the values determined by (cite: cormier18) and (cite: jimenez-donaire19)" (Comparison to literature line ratios) [from (cite: cormier18; jimenez-donaire19)]
- External data: Corotation radii of NGC 628  
  > "corotation radii of 3.2 kpc (red circles) and 5.1 kpc (green circles) (cite: cepa90; fathi07)" (Relation to the spiral arms) [from (cite: cepa90; fathi07)]
- Simulation/model as data: Starburst99 instantaneous burst models, solar metallicity, Kroupa IMF  
  > "The observations were compared to models using a solar metallicity, an instantaneous burst of star formation of 10$^6$ $\mathrm{M_{\odot}}$, and a Kroupa initial mass function (IMF)." (Young stellar content)

## Processing

### Calibration

- pipeline or manual: ALMA reduction scripts followed; statwt applied  
  > "interferometric calibration followed the recipes provided in the ALMA reduction scripts." (Reduction and Imaging)
- casa version: Cycle 1: CASA 4.2.2 (12-m), 4.2.1 (7-m); imaging 5.4.0; TP 4.5.3; Cycle 2 band 3: 4.2.1, 4.3.1 (interf.), 4.4, 4.5 (TP)  
  > "We imaged and post-processed the data using CASA version 5.4.0." (Reduction and Imaging)
- pipeline version: _not stated_
- archive products used as is: _not stated_
- flux calibrator: _not stated_
- flux scale uncertainty: _not stated_
- self calibration: _not stated_

### Imaging

- task: tclean multi-scale then single-scale clean; feather for TP combination  
  > "First, we carry out a multi-scale clean using the CASA task `tclean`." (Reduction and Imaging)
- deconvolver: _not stated_
- weighting robust: _not stated_
- uv taper: _not stated_
- cell size: _not stated_
- image size: _not stated_
- masking: broad mask, cleaned until residual peak S/N of 4, then restrictive mask  
  > "We used a broad clean mask and cleaned until the residual maps has a maximum signal-to-noise ratio of $4$." (Reduction and Imaging)
- multiscale scales: _not stated_
- continuum subtraction: _not stated_
- line free channels: _not stated_
- primary beam correction: applied after imaging  
  > "After imaging, we converted the units of the cube to Kelvin, primary beam corrected the data." (Reduction and Imaging)
- array combination: 12m+7m joint imaging, feathered with Total Power  
  > "We then projected the single dish data onto the astrometric grid of the interferometric image and used the CASA task `feather` to combine the two data sets." (Reduction and Imaging)
- smoothing: CO(2-1) convolved to 1.0"; channel width ~2.5 km/s; 3mm CO smoothed to 6 km/s  
  > "We spectrally regrid all data onto a common velocity frame with channel width $\sim 2.5$ km s$^{-1}$." (Reduction and Imaging)
- final beam: _not stated_
- final rms: _not stated_

### Inherited from earlier work

- Full CO(2-1) observing strategy, calibration, imaging and delivery  
  > "are described in a forthcoming dedicated PHANGS-ALMA survey paper (Leroy et al., in prep.)." (1 mm lines) [from Leroy et al., in prep.]
- GMC catalog via CPROPS  
  > "Catalogs of giant molecular clouds (GMCs) for all the PHANGS-ALMA galaxies, including NGC 628, have been constructed and will be presented in a forthcoming paper (Rosolowsky et al., in prep)." (GMC properties in NGC 628) [from Rosolowsky et al., in prep; (cite: rosolowsky06)]
- MUSE data reduction  
  > "(cite: kreckel16; kreckel18) present a detailed explanation of the strategy and data reduction of the MUSE observations of NGC 628." (Complementary MUSE data) [from (cite: kreckel16; kreckel18)]
- Torque/inflow method  
  > "We follow the method of (cite: querejeta16) and (cite: garciaburillo05)" (Relation to the spiral arms) [from (cite: querejeta16; garciaburillo05)]

### Not stated but needed to reproduce (our reading)

- tclean robust/weighting, cell and image size
- multi-scale scales and clean convergence criterion
- feather parameters and scaling
- line-free channels for continuum subtraction
- CPROPS settings for the cloud catalog
- 3mm imaging weights and rms thresholds
- RADEX collision files and fitting procedure (chi2 details)
- Starburst99 input parameters beyond those listed
- Details of 1 kpc aperture measurements (Sun et al. in prep)

## Analysis recipe

1. **Calibrate and image ALMA 12m+7m+TP data**: ALMA scripts calibration, tclean, custom TP reduction, feather  
  > "We then projected the single dish data onto the astrometric grid of the interferometric image and used the CASA task `feather` to combine the two data sets." (Reduction and Imaging)
   - software: CASA, tclean, feather
   - fitting: _not stated_
   - validation: Visual inspection of calibration steps  
  > "Visual inspection of the different calibration steps (bandpass, phase, amplitude, and flux) showed that the scripts yielded a satisfactory calibration." (Reduction and Imaging)
2. **Derive cloud mass, size, linewidth, virial parameter**: CPROPS cloud decomposition of CO(2-1) cube; luminous mass from alpha_CO  
  > "These catalogs are generated using the CPROPS algorithm (cite: rosolowsky06) to segment the CO(2$-$1) data cubes into individual molecular clouds" (GMC properties in NGC 628)
   - software: CPROPS
   - parameter: alpha_CO(2-1) = 6.2 Msun (K km/s pc2)^-1  
  > "This mass assumes a CO(2$-$1)-to-H$_2$ conversion factor $\alpha_{\rm CO} = 6.2$ $\mathrm{M_{\odot}}$ (K km s$^{-1}$ pc$^2$)$^{-1}$" (The headlight cloud)
   - assumption: Galactic alpha_CO(1-0)=4.3 divided by R21=0.69  
  > "divided by 0.69, i.e., the CO(2$-$1)/CO(1$-$0) ratio measured in the headlight cloud" (The headlight cloud)
   - fitting: _not stated_
   - validation: _not stated_
3. **Measure multi-line profiles and ratios**: Smooth cubes to 13CO resolution, extract spectra at peak, single Gaussian fits, compute ratios  
  > "We fit a single Gaussian profile to each line in Fig. [5](#fig:lvg) and report the results in Table [2](#tab:fitprof)." (Observed line ratios in the headlight cloud)
   - fitting: _not stated_
   - validation: _not stated_
4. **LVG modelling of density and temperature**: RADEX grid fit to 12CO/13CO, HCN/13CO, HCN/12CO(2-1) ratios  
  > "We fit the $^{12}$CO(1$-$0)/$^{13}$CO(1$-$0) ratio as a good tracer of temperature variations, HCN(1$-$0)/$^{13}$CO(1$-$0) as a tracer of gas density variations" (LVG modelling)
   - software: RADEX
   - parameter: Tkin 10-160 K; nH2 1e2-1e7 cm-3; linewidth 20 km/s; NH2 = 9e21 cm-2; Tbg 2.73 K; expanding sphere  
  > "We first compute a grid of LVG models, which covers a kinetic gas temperature range of $T_{\rm kin}=10-160$ K" (LVG modelling)
   - assumption: [12CO]/[H2]=3e-4, [12CO]/[13CO]=70, [HCN]/[H2]=5e-9  
  > "\[$^{12}$CO\]/\[H$_2$\] = 3$\times10^{-4}$, \[$^{12}$CO\]/\[$^{13}$CO\] = 70, and \[HCN\]/\[H$_2]= 5\times10^{-9}$" (LVG modelling)
   - fitting: _not stated_
   - validation: RADEX-predicted CO(2-1) about three times larger than measured; treated as order-of-magnitude  
  > "the RADEX-predicted CO(2$-$1) brightness is about three times larger than what is measured." (LVG modelling)
5. **Young stellar population and feedback pressures**: Starburst99 comparison using Halpha EW (age) and N_ion (mass); pressure terms from winds, SN, radiation, turbulence, gravity  
  > "our best constraint on the age comes from the equivalent width of the H$\alpha$ line, and our best constraint on the mass comes from the number of ionizing photons produced" (Young stellar content)
   - software: Starburst99, LZIFU
   - parameter: v_wind ~2e3 km/s; v_SN = 1e4 km/s  
  > "$v_{\rm wind} \sim 2\times10^3\,$km s$^{-1}$" (Stellar Feedback)
   - assumption: Case B Ha/Hb=2.86, Fitzpatrick99 curve R_V=3.1  
  > "to an intrinsic value of 2.86 (for case B recombination and an electron temperature of 10,000 K)" (Complementary MUSE data)
   - fitting: _not stated_
   - validation: _not stated_
6. **Gravitational torques and mass inflow rate**: Torque profile from S4G 3.6um stellar mass map and ALMA gas map, M/L=0.6  
  > "adopting a global $M/L=0.6$ assuming a Chabrier IMF (cite: meidt14)" (Relation to the spiral arms)
   - fitting: _not stated_
   - validation: _not stated_

## Software

- **CASA** 4.2.1/4.2.2/4.3.1/4.4/4.5/4.5.3 (cal); 5.4.0 (imaging): calibration, imaging, TP reduction  
  > "We imaged and post-processed the data using CASA version 5.4.0." (Reduction and Imaging)
- **CPROPS** : cloud segmentation and properties; signal mask for 3mm CO  
  > "These catalogs are generated using the CPROPS algorithm (cite: rosolowsky06)" (GMC properties in NGC 628)
- **RADEX** : LVG radiative transfer  
  > "We use RADEX[^4], a public LVG radiative transfer code." (LVG modelling)
- **Starburst99** : age and mass of young stars  
  > "comparing observed properties to Starburst99 (S99) models assuming an instantaneous burst" (Young stellar content)
- **LZIFU** : Halpha line fitting of MUSE  
  > "The H$\alpha$ emission line was obtained using the LZIFU pipeline (cite: ho16)" (Complementary MUSE data)
- **GILDAS/CLASS** : baselining ozone line artifacts in TP data  
  > "We used advanced baselining functionality in the `GILDAS/CLASS` software to remove this artifact" (Total power data reduction)

## Numeric results

| quantity | value | uncertainty | units | step | quote |
|---|---|---|---|---|---|
| Headlight CO luminous mass | 2.0e7 | not stated | Msun | 2 | $M_{\rm lum}=\alpha_{\rm CO}\,L_{\rm CO} = 2.0\times10^{7}$ $\mathrm{M_{\odot}}$ |
| Cloud radius | 184 | not stated | pc | 2 | The cataloged radius and (FWHM) linewidth of the headlight cloud are 184 pc and 16.3 km s$^{-1}$ respectively. |
| Virial parameter | 0.5 | not stated | dimensionless | 2 | is low, 0.5. |
| CO(2-1)/CO(1-0) peak ratio | 0.70 | not stated | dimensionless | 3 | 0.70  /    0.75 |
| LVG density | 5e4 | not stated | cm-3 | 4 | These curves intersect at $n_{\rm H_2}\sim5\times 10^{4}$ cm$^{-3}$ and $T_{\rm kin}\sim20$ K. |
| Kinetic temperature | ~20 | not stated | K | 4 | $T_{\rm kin}\sim20$ K |
| Young stellar mass | 3e5 | not stated | Msun | 5 | / Young star mass / M$_{\rm cl}$ / $3\times 10^5$ $\mathrm{M_{\odot}}$ / |
| Net mass inflow rate between corotations | 0.07 | 0.04 | Msun/yr | 6 | at a net rate $0.07\pm0.04$ $\mathrm{M_{\odot}}$ yr$^{-1}$ |
| Mean cloud-scale CO(2-1)/CO(1-0) in NGC 628 | 0.54 | 0.10 (std) | dimensionless | 3 | we find a mean cloud-scale value of CO(2$-$1)/CO(1$-$0) in NGC 628 of 0.54, with a standard deviation of $0.10$ |

## Qualitative findings

- Headlight is the most massive and brightest cloud, coincident with the most luminous HII region, with CO likely overluminous due to heating.  
  > "We argue that the CO emission is over-luminous based on its high CO(2$-$1) peak temperature" (Conclusions)

## Claim tuples

- H: Is the headlight cloud exceptional among NGC 628 clouds? | E: CPROPS catalog comparison, CDFs, radial profiles | R: Most massive and brightest (peak ~7 K), low alpha_vir 0.5 | F: Exceptional bright compact core in a typical-size massive cloud | **supported**
- H: Is the CO emission overluminous because of heating? | E: Compare peak Tb, R21 and alpha_vir with other clouds | R: Peak 6.7 K vs 5.5 K LTE prediction for 10 K gas; R21 0.7 vs 0.54 | F: Heating by HII region favored | **partially**
- H: Do corotation and inflow explain the cloud's mass growth? | E: Gravitational torque analysis | R: Located at inner corotation 3.2 kpc, net inflow 0.07 Msun/yr | F: Proposed mechanism for growth | **partially**

## Reasoning

- Why this data: _not stated_
- Why this method: More sophisticated modelling not justified by current line data  
  > "it is difficult to justify more sophisticated modelling with the current set of molecular line data." (LVG modelling)
- How they decided it was enough: _not stated_
- Limitation (authors): LVG model overpredicts CO(2-1) by ~3x; results order-of-magnitude  
  > "consider our results for the cloud density and pressure as order-of-magnitude estimates." (LVG modelling)
- Caveat (inferred, ours): Single cloud, no statistical context
- Caveat (inferred, ours): alpha_CO assumed; true mass uncertain
- Caveat (inferred, ours): LVG assumes single-component, fixed abundances and column density
- Caveat (inferred, ours): Dense tracers at low S/N with possible positional offsets
- Caveat (inferred, ours): Inflow estimate depends on M/L and ignores viscous torques

## Reproducibility

- Data public (paper): Project codes given; archival public data implied  
  > "This paper makes use of the following ALMA data: ADS/JAO.ALMA#2012.1.00650.S and 2013.1.00532.S." (Acknowledgements)
- Products in archive: _not stated_
- Code: TP reduction scripts on GitHub/PHANGS site  
  > "Scripts implementing our procedures are also available on GitHub at <https://sites.google.com/view/phangs/home/data>." (Conclusions)
- Missing: Cloud catalog (Rosolowsky et al. in prep) settings
- Missing: PHANGS imaging details in Leroy et al. in prep
- Missing: MUSE reduced products from Kreckel et al.
- Data volume (inferred): ~100-300 GB raw for two projects including TP
- Score (inferred): 3/5, Data public and many steps described, but key imaging and catalog details deferred to in-prep papers.
- Rediscovery candidate: no, Key imaging and cloud catalog recipes are inherited from unpublished work.

## Links

- Method: (cite: rosolowsky06) (CPROPS algorithm)
- Method: (cite: querejeta16) (gravitational torque method)
- Method: (cite: leitherer99) (Starburst99)
- Companion: (cite: kreckel18) (MUSE HII region data and the headlight source)
- Companion: Leroy et al., in prep. (PHANGS-ALMA survey paper)
- Related: PHANGS-ALMA
- Related: EMPIRE
- Related: LEGUS
- Related: THINGS

## Checks

```json
{
 "quotes": 71,
 "quotes_ok": 71,
 "quote_pass_rate": 1.0,
 "quotes_too_long": 0,
 "unsupported_facts": 0,
 "project_codes": 2,
 "codes_not_in_text": [],
 "codes_not_in_obscore": [],
 "obscore_codes_not_in_card": [],
 "codes_printed_but_missing": [],
 "numeric_results": 9,
 "numeric_problems": 0,
 "fill": {
  "facts": 85,
  "stated": 48,
  "rate": 0.565
 },
 "evidence_ok": true
}
```
