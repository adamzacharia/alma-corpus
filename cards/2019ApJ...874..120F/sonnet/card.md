# New Insights into the Physical Conditions and Internal Structure of a Candidate Proto-globular Cluster

`2019ApJ...874..120F` | The Astrophysical Journal 2019 | first author: Finn, Molly K. | arXiv: 1903.08669 | DOI: 10.3847/1538-4357/ab0d1e

Card schema 1.0 | model claude-sonnet-5-5 | depth full | type observational_alma_primary

## Science

- Fields: star_formation, nearby_galaxies, milky_way_ism
- Question: What are the mass, internal structure, pressure environment and evolutionary state of the Firecracker, a candidate proto-globular cluster cloud in the Antennae overlap region?  
  > "we are able to resolve the cloud’s structure and find that it has a characteristic radius of 22 pc and a mass of 1–9$\times 10^6 M_\odot$." (abstract)
- Target **Firecracker cloud (Antennae overlap region)**: coordinates 12:01:54.73 -18:52:53.1 (J2000)  
  > "centered on 12:01:54.73 -18:52:53.1, and velocities in the range 1430–1555 km s$^{-1}$." (3.1 CO Line Profiles and Cloud Extraction); "At a distance of 22 Mpc, it is also close enough that with ALMA" (Introduction); z/distance 22 Mpc  
  > "centered on 12:01:54.73 -18:52:53.1, and velocities in the range 1430–1555 km s$^{-1}$." (3.1 CO Line Profiles and Cloud Extraction); "At a distance of 22 Mpc, it is also close enough that with ALMA" (Introduction); distance from _not stated_

## Data provenance

- ALMA projects: 2015.1.00977.S, 2016.1.00924.S
- bands: Band 6 and Band 7, extended and compact configurations, Cycles 3 and 4  
  > "using ALMA Band 6 and Band 7 in both extended and compact configurations during ALMA Cycles 3 and 4" (2 Observations)
- frequencies and spectral setup: _not stated_
- continuum bandwidth: _not stated_
- arrays: _not stated_
- configurations: _not stated_
- baselines: max baselines 650-3700 m  
  > "Aug 8 2017   |   226   |    51     |   3700" (Table 1)
- angular resolution: ~0.1" (~10 pc); beams 0.09x0.12" to 0.17x0.21"  
  > "$^{12}$CO(2-1) |  0.5   | 0.09$\times$0.12 |    0.6     |    5" (Table 2)
- max recoverable scale: _not stated_
- sensitivity: _not stated_
- time on source: 5-156 min per execution (Table 1)  
  > "Sep 17-22 2016 |   226   |    156    |   3200" (Table 1)
- observing dates: Sep 2016 - Aug 2017  
  > "Jul 23 2017   |   349   |    19     |   3600" (Table 1)
- pi or archival as stated: _not stated_
- Line: 12CO 2-1 (not stated)
- External data: 12CO/13CO abundance ratio ~70 (range 40-200) in Antennae overlap region  
  > "the $^{12}$CO/$^{13}$CO abundance ratio has been measured to be $X_{12} / X_{13} \simeq 70$" (3.2 Cloud Mass) [from (cite: Zhu03)]
- External data: HCN(1-0) and HCO+(1-0) surface brightness in the region  
  > "much lower than the values measured in this region by (cite: Schirm16), which are 46 K km s$^{-1}$ for HCN(1-0) and 73 K km s$^{-1}$ for HCO$^+$(1-0)" (3.8 HCN and HCO$^+$) [from (cite: Schirm16)]
- External data: Henize 2-10 natal SSC line ratios for comparison  
  > "We compare these ratios to those measured for HCN(1-0), HCO$^+$(1-0), and CO(2-1) in potential natal-SSCs found in the Henize 2-10 dwarf galaxy by (cite: Johnson18)." (3.8 HCN and HCO$^+$) [from (cite: Johnson18)]
- External data: dust emissivity 0.9 cm2/g and gas-to-dust ratio 120  
  > "$\kappa=0.9\pm0.13$ cm$^2$ g$^{-1}$ and a ratio of $120\pm28$ (cite: Wilson08)" (3.3 Expected Continuum Emission) [from (cite: Wilson08)]

## Processing

### Calibration

- pipeline or manual: CASA pipeline, no self-calibration  
  > "reduced and calibrated using the CASA 4.7.2 pipeline, and no self-calibration was performed" (2 Observations)
- casa version: CASA 4.7.2  
  > "reduced and calibrated using the CASA 4.7.2 pipeline" (2 Observations)
- pipeline version: _not stated_
- archive products used as is: _not stated_
- flux calibrator: J1256-0547 and J1037-2934  
  > "The flux calibrators used were J1256-0547 and J1037-2934" (2 Observations)
- flux scale uncertainty: 10%  
  > "we estimate the flux uncertainty to be 10% based on the variability in these sources" (2 Observations)
- self calibration: none  
  > "no self-calibration was performed" (2 Observations)

### Imaging

- task: _not stated_
- deconvolver: _not stated_
- weighting robust: Briggs, robust 0.5-2.0 (0.5 for 12CO; 2.0 for 13CO, HCN, HCO+)  
  > "Images were created using Briggs weighting with robust parameters varying between 0.5 and 2.0" (2 Observations)
- uv taper: _not stated_
- cell size: 0.014"  
  > "using a 2646$\times$2646 pixel grid, with pixels of 0.014"" (2 Observations)
- image size: 2646x2646 pixels  
  > "using a 2646$\times$2646 pixel grid" (2 Observations)
- masking: _not stated_
- multiscale scales: _not stated_
- continuum subtraction: emission lines flagged to make continuum image  
  > "we flagged the emission lines to create a continuum image" (3.3 Expected Continuum Emission)
- line free channels: _not stated_
- primary beam correction: not applied; source much smaller than primary beam  
  > "so no primary beam correction is required" (2 Observations)
- array combination: _not stated_
- smoothing: cubes convolved to the 13CO(2-1) beam for line comparisons  
  > "the data cubes were each convolved to the synthesized beam of $^{13}$CO(2-1)" (3.1 CO Line Profiles and Cloud Extraction)
- final beam: _not stated_
- final rms: 0.25-2.0 mJy/beam per channel (Table 2); Band 7 continuum 0.06 mJy/beam  
  > "$^{13}$CO(2-1) |  2.0   | 0.17$\times$0.18 |    0.25    |    5" (Table 2)

### Inherited from earlier work

- Pi = 0.5 in ram/external pressure formula  
  > "and we take $\Pi = 0.5$ (cite: J15)" (3.6 Cloud Pressure) [from (cite: J15)]
- Column density equation for CO  
  > "we found the column density at each pixel using the equation from (cite: MangumShirley15)" (3.2 Cloud Mass) [from (cite: MangumShirley15)]
- Dust mass formula  
  > "From (cite: Wilson08)," (3.3 Expected Continuum Emission) [from (cite: Wilson08)]

### Not stated but needed to reproduce (our reading)

- Spectral window frequencies and exact line-free channel selection
- Which robust value/beam applies to each execution and tclean parameters (deconvolver, masks, thresholds)
- Method of temperature measurement (T 25-35 K) and how T_kin range 25-40 K was derived
- Details of Gaussian fitting and error propagation for Bonnor-Ebert fit
- Exact moment mask thresholds and aperture centers
- Whether pipeline calibration was rerun or archive products used

## Analysis recipe

1. **extract cloud and make moment maps**: 3D extraction in shwirl; moment 0 and 8 over 1430-1555 km/s; Gaussian line profile fits, second velocity component subtracted  
  > "we made total intensity maps (moment 0), integrating over the velocity range 1430-1555 km s$^{-1}$, and peak intensity maps (moment 8)" (3.1 CO Line Profiles and Cloud Extraction)
   - software: shwirl
   - parameter: 0.98x0.84" box, aperture radius 0.24" for profiles  
  > "This corresponds to a 0.98"$\times$0.84" rectangle around the cloud" (3.1 CO Line Profiles and Cloud Extraction)
   - fitting: _not stated_
   - validation: _not stated_
2. **measure characteristic radius**: radius of circle with same area as 13CO(2-1) 5sigma moment 0 contour  
  > "the radius of a circle with the same area as that enclosed by the 5$\sigma$ contour of the $^{13}$CO(2-1) total intensity (moment 0) map" (3.1 CO Line Profiles and Cloud Extraction)
   - assumption: distance 22 Mpc  
  > "which corresponds to a size of 21 pc at a distance of 22 Mpc" (3.1 CO Line Profiles and Cloud Extraction)
   - fitting: _not stated_
   - validation: _not stated_
3. **derive optical depth, Tx, column density and mass**: 12CO/13CO brightness ratio gives tau12 and Tx per pixel and velocity; Mangum & Shirley column density; H2/CO abundance and 1.3 factor give mass  
  > "We then assume the total mass is 1.3 times the mass of H$_2$ to derive the total mass surface density" (3.2 Cloud Mass)
   - parameter: X12/X13 = 40,70,120,200; H2/12CO = 1e4-1e5  
  > "Different combinations of values in the expected ranges of $X_{12} / X_{13}$ and H$_2$/$^{12}$CO were used" (3.2 Cloud Mass)
   - assumption: equal Tx for 12CO and 13CO; constant Tx across velocity; 12CO(2-1) thermalized  
  > "assuming that the excitation temperatures for $^{12}$CO and $^{13}$CO are equal" (3.2 Cloud Mass)
   - fitting: Gaussian fits per pixel to 12CO and 13CO velocity profiles  
  > "fit Gaussian profiles to the velocity profile for each $^{12}$CO(2-1) pixel" (3.2 Cloud Mass)
   - validation: compared with J15 mass range  
  > "is in good agreement with measurements made by (cite: J15)" (3.2 Cloud Mass)
4. **upper mass limit from continuum non-detection**: Band 7 flux in 0.35" aperture to dust mass (Wilson08) times gas-to-dust ratio  
  > "the largest total mass that would be consistent with the continuum non-detection would be $9\times10^6 M_\odot$" (3.3 Expected Continuum Emission)
   - parameter: T>=25 K, kappa>=0.77, S880<=1.34 mJy, G/D<=148  
  > "$S_{880} \leq 1.34$ mJy, $T \geq 25$ K, $\kappa \geq 0.77$ cm$^2$ g$^{-1}$" (3.3 Expected Continuum Emission)
   - fitting: _not stated_
   - validation: _not stated_
5. **derive X_CO maps**: column density divided by 12CO(2-1) integrated intensity, Gaussian fit to map distribution  
  > "Fitting a Gaussian to the distribution of values within each map, the average values vary in the range" (3.4 $X_{CO}$ Conversion Factor)
   - assumption: CO(2-1)/CO(1-0) = 1  
  > "($^{12}$CO(2-1)/$^{12}$CO(1-0) = 1)" (3.4 $X_{CO}$ Conversion Factor)
   - fitting: _not stated_
   - validation: histogram indicates variations not purely Gaussian noise  
  > "the distribution at the higher and lower ends cannot be entirely explained by Gaussian noise in the measurements" (3.4 $X_{CO}$ Conversion Factor)
6. **fit radial column density profile**: azimuthal average in 1-pixel annuli, fit Bonnor-Ebert profile for xi_max; also circular Gaussian  
  > "This profile is then fit to the observed structure profile by determining the best-fit values of $\xi_{max}$" (3.5 Column Density Radial Profile)
   - assumption: isothermal spherical cloud  
  > "with the assumption that the cloud is spherical" (3.5 Column Density Radial Profile)
   - fitting: _not stated_
   - validation: compared with Gaussian; caution due to correlated points  
  > "the points used in the fit are separated by less than the beam size, and so are correlated with each other" (3.5 Column Density Radial Profile)
7. **pressure from surface density vs size-linewidth**: four apertures; sigma_V from two-Gaussian fit to 12CO(3-2); P_e = 3 Pi M sigma^2/(4 pi R^3)  
  > "The velocity dispersions were determined by fitting two Gaussian profiles to the $^{12}$CO(3-2) emission line" (3.6 Cloud Pressure)
   - parameter: Pi = 0.5  
  > "we take $\Pi = 0.5$ (cite: J15)" (3.6 Cloud Pressure)
   - assumption: cloud is bound  
  > "Assuming the cloud is bound" (3.6 Cloud Pressure)
   - fitting: _not stated_
   - validation: _not stated_
8. **PV diagram and cloud-cloud collision ram pressure**: PV cut along collision axis from moment maps; P = rho v^2 using X_CO-derived density  
  > "Taking the ram pressure to be $P = \rho v^2$" (4.2 High Pressure Environment)
   - assumption: colliding cloud depth 88 pc (twice Firecracker diameter)  
  > "have a depth of 88 pc" (4.2 High Pressure Environment)
   - fitting: _not stated_
   - validation: _not stated_
9. **HCN and HCO+ line ratios as evolutionary tracer**: moment 0 maps, convolve to common beam 0.17x0.21", ratios in Apertures 3 and 4 compared with Henize 2-10  
  > "we convolve these images, as well as the $^{12}$CO(2-1) emission, to the same beam size (0.17"$\times$0.21")" (3.8 HCN and HCO$^+$)
   - fitting: _not stated_
   - validation: _not stated_

## Software

- **CASA** 4.7.2: pipeline calibration and imaging  
  > "reduced and calibrated using the CASA 4.7.2 pipeline" (2 Observations)
- **shwirl** : 3D visualization and cloud extraction  
  > "Using the 3D visualization tool `shwirl` (cite: shwirl)" (3.1 CO Line Profiles and Cloud Extraction)

## Numeric results

| quantity | value | uncertainty | units | step | quote |
|---|---|---|---|---|---|
| characteristic radius | 0.21 (21-22) | not stated | arcsec (pc) | 2 | This characteristic radius for the Firecracker is 0.21", which corresponds to a size of 21 pc at a distance of 22 Mpc. |
| cloud mass range | 1-9 | not stated | 10^6 Msun | 4 | a mass of 1–9$\times 10^6 M_\odot$ |
| peak brightness temperature 12CO(2-1) | 17 | 2 | K | 1 | $T_{CO(2-1)} = 17\pm2$ K and $T_{CO(3-2)} = 16\pm2$ K |
| mass upper limit from continuum | 9e6 | not stated | Msun | 4 | the largest total mass that would be consistent with the continuum non-detection would be $9\times10^6 M_\odot$ |
| average X_CO | 0.12-1.1 | not stated | 1e20 cm-2 (K km/s)-1 | 5 | the average values vary in the range $X_{CO} = (0.12-1.1)\times10^{20}$ cm$^{-2}$ (K km s$^{-1}$)$^{-1}$ |
| Bonnor-Ebert xi_max | 3.4 | 0.4 | dimensionless | 6 | The resulting best fit for the derived set of column densities is characterized by $\xi_{max} = 3.4\pm0.4$. |
| external pressure required | >1e8 | not stated | K cm-3 | 7 | P$_e/k \gtrsim 10^8$ K cm$^{-3}$ |
| ram pressure from collision | 1.1e9 | not stated | K cm-3 | 8 | P/k \sim 1.1\times10^9$ K cm$^{-3}$ |
| velocity dispersion 12CO(2-1) | 36 | 3 | km/s | 1 | 1516$\pm$5 / 14$\pm$1 / 26$\pm$2 / 0.87$\pm$0.2 / 36$\pm$3 / 38$\pm$3 / 0.21 |

## Qualitative findings

- Continuum not detected at 226, 237 or 349 GHz at the Firecracker position  
  > "We therefore consider this a non-detection of the Firecracker" (2 Observations)
- HCN/HCO+ falls and HCO+/CO rises with cluster evolution; Firecracker consistent with early stage  
  > "our new data supports the trend found by (cite: Johnson18)" (3.8 HCN and HCO$^+$)

## Claim tuples

- H: Firecracker has mass and size consistent with a proto-globular cluster | E: 13CO/12CO optical depth and column density mapping plus continuum limit | R: R=22 pc, M=1-9e6 Msun | F: Cloud is a viable SSC/GC progenitor | **supported**
- H: Cloud needs high external pressure to be bound | E: surface density vs size-linewidth and pressure formula | R: P/k >~1e8 K cm-3 | F: High-pressure environment required | **supported**
- H: Column density profile reveals stable pressure-confined structure | E: Bonnor-Ebert fit | R: xi_max=3.4+-0.4, also Gaussian consistent | F: stable if BE interpretation holds; cautious | **partially**
- H: Cloud-cloud collision supplies the pressure | E: PV diagram and ram pressure estimate | R: P/k ~1.1e9 K cm-3, hint of broad bridge | F: collision plausible | **partially**
- H: HCN/HCO+ ratios trace cluster evolutionary stage | E: compare Firecracker ratios with Henize 2-10 | R: Firecracker lies at early-stage end | F: supports Johnson18 trend | **supported**

## Reasoning

- Why this data: _not stated_
- Why this method: Optically thin 13CO used for size since 12CO is optically thick  
  > "we use the $^{13}$CO(2-1) emission, since it is optically thin and gives a better representation of the cloud’s structure" (3.1 CO Line Profiles and Cloud Extraction)
- Alternative: Gaussian profile fits the column density as well as Bonnor-Ebert  
  > "The cloud is consistent with both the Bonnor-Ebert profile and this Gaussian profile." (3.5 Column Density Radial Profile)
- How they decided it was enough: _not stated_
- Limitation (authors): Bonnor-Ebert fit may mimic non-equilibrium clouds; fit points are correlated  
  > "so we are cautious in drawing conclusions about the cloud’s physical state from this profile fit" (3.5 Column Density Radial Profile)
- Limitation (authors): Assumptions on Tx and thermalization underestimate mass if violated  
  > "If the excitation temperature of $^{13}$CO is lower than $^{12}$CO, this assumption will underestimate the mass." (3.2 Cloud Mass)
- Caveat (inferred, ours): Mass depends strongly on poorly known abundance ratios, spanning ~30x
- Caveat (inferred, ours): Equal Tx assumption and CO(2-1)/CO(1-0)=1 not tested
- Caveat (inferred, ours): Ram pressure estimate is rough, with assumed cloud depth
- Caveat (inferred, ours): Distance 22 Mpc assumed without source

## Reproducibility

- Data public (paper): Project codes given in acknowledgments; public status not stated  
  > "This paper makes use of the following ALMA data: ADS/JAO.ALMA#2015.1.00977.S and ADS/JAO.ALMA#2016.1.00924.S." (Acknowledgments)
- Products in archive: _not stated_
- Missing: Full tclean parameters and spectral setup
- Missing: Temperature determination
- Missing: Aperture centers and masks
- Missing: Fitting error treatment
- Data volume (inferred): ~100-300 GB raw for two projects
- Score (inferred): 3/5, Data identified and main equations given, but imaging details, thresholds and several assumptions are incomplete.
- Rediscovery candidate: no, Recipe incomplete in imaging details and uncertain public status; results depend on assumed ranges.

## Links

- Method: (cite: MangumShirley15) (CO column density equation)
- Method: (cite: Wilson08) (dust mass formula and dust parameters)
- Companion: (cite: J15) (earlier characterization of the Firecracker)
- Companion: (cite: Whitmore14) (discovery of the cloud)
- Companion: (cite: Johnson18) (HCN/HCO+ evolutionary tracer in Henize 2-10)

## Checks

```json
{
 "quotes": 79,
 "quotes_ok": 79,
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
  "facts": 94,
  "stated": 59,
  "rate": 0.628
 },
 "evidence_ok": true
}
```
