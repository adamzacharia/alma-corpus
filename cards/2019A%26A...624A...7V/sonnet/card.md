# Spatial segregation of dust grains in transition disks. SPHERE observations of 2MASS J16083070-3828268 and RXJ1852.3-3700

`2019A&A...624A...7V` | Astronomy and Astrophysics 2019 | first author: Villenave, M. | arXiv: 1902.04612 | DOI: 10.1051/0004-6361/201834800

Card schema 1.0 | model claude-sonnet-5-5 | depth light | type multi_facility_alma_minor

## Science

- Fields: protoplanetary_disks
- Question: What are the vertical and radial dust structures of two transition disks (J1608, J1852) from SPHERE scattered light plus archival ALMA, and what do they imply for the origin of cavities?  
  > "aim at constraining their vertical and radial structure using multiwavelength observations that probe different regions of the disks and can help understanding the origin of the cavities." (abstract)
- Target **J1608 (2MASS J16083070-3828268)**: coordinates RA 16 08 30.7, Dec -38 28 26.8  
  > "| Distance$^1$   | \[pc\]                  |     $156 \pm 6$     | $146 \pm1$  |" (Table 1); "J1608 is located at 156 pc (cite: gaia_DR2_2018) in the Lupus III cloud." (2 Stellar and disk properties); z/distance 156 ± 6 pc  
  > "| Distance$^1$   | \[pc\]                  |     $156 \pm 6$     | $146 \pm1$  |" (Table 1); "J1608 is located at 156 pc (cite: gaia_DR2_2018) in the Lupus III cloud." (2 Stellar and disk properties); distance from Gaia DR2  
  > "| Distance$^1$   | \[pc\]                  |     $156 \pm 6$     | $146 \pm1$  |" (Table 1); "J1608 is located at 156 pc (cite: gaia_DR2_2018) in the Lupus III cloud." (2 Stellar and disk properties)
- Target **J1852 (RXJ1852.3-3700)**: coordinates RA 18 52 17.3, Dec -37 00 11.9  
  > "located at a distance of 146 pc (cite: gaia_DR2_2018)" (2 Stellar and disk properties); z/distance 146 ± 1 pc  
  > "located at a distance of 146 pc (cite: gaia_DR2_2018)" (2 Stellar and disk properties); distance from Gaia DR2  
  > "located at a distance of 146 pc (cite: gaia_DR2_2018)" (2 Stellar and disk properties)

## Data provenance

- ALMA projects: 2015.1.00222.S, 2015.1.01083.S
- bands: J1608: Band 6; J1852: Band 3 (~3 mm)  
  > "we use the Band 6 observations (Project ID: 2015.1.00222.S, PI: Williams) obtained on July 23, 2016" (3.3 Complementary data)
- frequencies and spectral setup: J1852: four continuum windows centered at 91.5, 93.4, 101.5, 103.5 GHz  
  > "The four continuum spectral windows were centered respectively on 91.5 GHz, 93.4 GHz, 101.5 GHz and 103.5 GHz." (3.3 Complementary data)
- continuum bandwidth: _not stated_
- arrays: _not stated_
- configurations: _not stated_
- baselines: _not stated_
- angular resolution: J1608 0.24''x0.23''; J1852 beam 0.38''x0.31''  
  > "at a resolution of 0.24$''$$\times$0.23$''$" (3.3 Complementary data); "with the achieved beam of 0.38$''$$\times$0.31$''$" (3.3 Complementary data)
- max recoverable scale: _not stated_
- sensitivity: _not stated_
- time on source: _not stated_
- observing dates: J1608: July 23, 2016; J1852: September 22, 2016  
  > "we use ALMA data observed on September 22, 2016, in Band 3" (3.3 Complementary data)
- pi or archival as stated: Archival ALMA data (PI Williams; PI Morino)  
  > "We complement our datasets with archival ALMA observations" (abstract)
- Line: 12CO 2-1 (not stated)
- Other facility **VLT/SPHERE (IRDIS)**: H- and J-band polarized scattered light images of J1608 and H-band of J1852  
  > "Observations were carried out in dual-polarization imaging mode (cite: Langlois_2014), in both J ($\lambda_J=1.245\,\mu$m) and H-band ($\lambda_H=1.625\,\mu$m) for J1608" (3.1 Observations)
- Other facility **VOSA / Vizier / Spitzer CASSIS**: SED photometry and Spitzer/IRS spectrum  
  > "The SED of J1852 was computed using the VO SED Analyser[^3] (cite: Bayo_2008)." (3.3 Complementary data)
- External data: Stellar ages and masses re-estimated with Gaia DR2  
  > "we will use the stellar ages and masses re-estimated by (cite: Garufi_2018)" (2 Stellar and disk properties) [from (cite: Garufi_2018)]
- External data: J1608 millimeter fluxes at 0.88 mm and 1.3 mm  
  > "we add the millimeter fluxes at 0.88 mm and 1.3 mm obtained from (cite: ansdell_2016) and (cite: ansdell_2018), respectively" (3.3 Complementary data) [from (cite: ansdell_2016); (cite: ansdell_2018)]
- External data: Comparison sample of 22 transition disks (mm peak and scattered light radii) rescaled to Gaia DR2  
  > "We re-scale the published values using the latest distances from Gaia DR2" (5.3 Comparison with other transition disks) [from literature, see Table 3]
- Simulation/model as data: Ovelar et al. 2013 analytic relation between planet mass and scattered-light/mm cavity ratio  
  > "They derived an analytic formula relating the planet mass with the ratio between the position of the so-called ’scattered light wall’ to that of the ALMA peak." (5.3 Comparison with other transition disks)

## Processing

### Calibration

- pipeline or manual: J1852: CASA pipeline; J1608 reduction from Ansdell et al. 2018  
  > "We used the CASA pipeline to calibrate the data" (3.3 Complementary data)
- casa version: _not stated_
- pipeline version: _not stated_
- archive products used as is: _not stated_
- flux calibrator: _not stated_
- flux scale uncertainty: _not stated_
- self calibration: J1852: phase-only self-calibration  
  > "The final image, after performing phase only self-calibration" (3.3 Complementary data)

### Imaging

- task: CASA clean (J1852)  
  > "extracted the continuum images using the CASA `clean` task, with a Briggs robust parameter of +0.5" (3.3 Complementary data)
- deconvolver: _not stated_
- weighting robust: Briggs robust = +0.5 (both)  
  > "cleaned with a Briggs robust weighting parameter of +0.5" (3.3 Complementary data)
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
- final beam: J1852: 0.38''x0.31''  
  > "with the achieved beam of 0.38$''$$\times$0.31$''$" (3.3 Complementary data)
- final rms: _not stated_

### Inherited from earlier work

- J1608 ALMA continuum and line data reduction  
  > "The data reduction of the continuum and line emission is presented in details in (cite: ansdell_2018)." (3.3 Complementary data) [from (cite: ansdell_2018)]
- SPHERE reduction to Stokes/PI maps  
  > "following the approach detailed in (cite: Ginski_2016)" (3.1 Observations) [from (cite: Ginski_2016)]
- Noise estimation for model scattered light images  
  > "We estimate it at each point of the map from the U$_\phi$ image of our observations (cite: Muro-Arena_2018)." (4.1 Methodology) [from (cite: Muro-Arena_2018)]

### Not stated but needed to reproduce (our reading)

- CASA version used for J1852
- Line-free channels and continuum subtraction for 12CO
- Self-calibration solution intervals
- Imaging cell size, image size, masks, deconvolver
- mcfost version and photon/grid settings
- Details of the PV diagram extraction and Keplerian fit
- Coronagraph attenuation map (Wilby et al. in prep)
- Fit statistic for the iterative model comparison

## Analysis recipe

1. **Reduce SPHERE data to PI, Qphi, Uphi**: Reduce to total intensity and Stokes Q,U maps following Ginski et al. 2016; PI = sqrt(Q^2+U^2); Qphi, Uphi per Schmid et al. 2006  
  > "We reduced the data to generate the total intensity map and Stokes Q and U polarized maps, following the approach detailed in (cite: Ginski_2016)." (3.1 Observations)
   - fitting: _not stated_
   - validation: _not stated_
2. **Derive J1608 gas kinematics from ALMA CO PV diagram**: PV diagram of 12CO 2-1, systemic velocity and Keplerian modelling for gas cavity inner radius  
  > "Modeling the disk velocities with Keplerian motion (assuming M$_\star$=1.4 M$_\odot$, i=74$^\circ$), we infer that the inner radius of the gas cavity is $\sim$ 48 au" (3.3 Complementary data)
   - parameter: velocity resolution 0.11 km/s  
  > "obtained with a velocity resolution of 0.11 km s$^{-1}$" (3.3 Complementary data)
   - assumption: M*=1.4 Msun, i=74 deg  
  > "assuming M$_\star$=1.4 M$_\odot$, i=74$^\circ$" (3.3 Complementary data)
   - fitting: _not stated_
   - validation: Agrees with thermo-chemical modeling by van der Marel et al. 2018  
  > "in agreement with the outcome of thermo-chemical modeling of the CO observations (cite: van_der_marel_new_2018)" (3.3 Complementary data)
3. **Radiative transfer modelling of SED, ALMA and SPHERE images**: Iterative mcfost models with small and large grain populations, compared to SED, mm image and PI image; representative rather than best-fit model  
  > "An iterative process is done to find a model that reproduces well the SED and the images. Considering the complexity of our observations, we do not aim to find the best-fit model, but rather a representative one." (4.1 Methodology)
   - software: mcfost
   - parameter: Free parameters per region: Rin, Rout, dust mass, H100au; beta fixed to 1.1; p = -1  
  > "For each region, our free parameters are the inner and outer radius (R$_\mathrm{in}$-R$_\mathrm{out}$), the dust mass and the scale height (H$_\mathrm{100\,au}$)." (4.2 Model setup)
   - parameter: Small grains 0.01-0.5 um, large grains 10-1000 um  
  > "modeling separately the extents of small (0.01 - 0.5 $\mu$m) and large grains (10 - 1000 $\mu$m)" (4.2 Model setup)
   - assumption: Gas-to-dust ratio 100; astronomical silicates; dn(a) ∝ a^-3.5 da  
  > "assume a gas-to-dust ratio of 100" (4.2 Model setup); "number density described with a power law of the grain size $\mathrm{dn(a)} \propto a^{-3.5}\,\mathrm{da}$" (4.2 Model setup)
   - fitting: Manual iterative adjustment, no sampler  
  > "An iterative process is done to find a model that reproduces well the SED and the images." (4.1 Methodology)
   - validation: Compare radial cuts along major/minor axes, SED, Qphi/Uphi maps; noise added to scattered light predictions  
  > "In our model, the radial position of the maxima as well as the radial extent in each cut are well reproduced." (4.3 Modeling J1608)
4. **Compare with sample of 22 transition disks**: Compile scattered-light and mm cavity radii, compute ratio, and use Ovelar et al. 2013 to infer companion mass  
  > "we compiled a sample of 22 disks that have both scattered light and millimeter observations" (5.3 Comparison with other transition disks)
   - parameter: R_cav,PI = mean of R_in,PI and R_peak,PI  
  > "defined as the mean between R$_{\rm{in,PI}}$ and R$_{\rm{peak,PI}}$" (Table 3 notes)
   - assumption: Ovelar models for R band and Band 7 applied to other wavelengths; circular planet orbit  
  > "We also note that the models were specifically calculated for R band scattered light observations and Band 7 (850 $\mu$m), and only for a planet in a circular orbit." (5.3 Comparison with other transition disks)
   - fitting: _not stated_
   - validation: _not stated_

## Software

- **mcfost** : Monte Carlo radiative transfer, SED and image modeling  
  > "we construct models using the radiative transfer code `mcfost` (cite: pinte_2006; pinte_2009)" (4.1 Methodology)
- **CASA** : Pipeline calibration and clean imaging of J1852 Band 3  
  > "We used the CASA pipeline to calibrate the data and extracted the continuum images using the CASA `clean` task" (3.3 Complementary data)
- **VOSA** : SED construction for J1852  
  > "The SED of J1852 was computed using the VO SED Analyser[^3] (cite: Bayo_2008)." (3.3 Complementary data)

## Numeric results

| quantity | value | uncertainty | units | step | quote |
|---|---|---|---|---|---|
| J1608 systemic velocity | +5.2 | 0.4 | km/s (LSR) | 2 | we retrieve the systemic velosity of the source to be +5.2$\pm$0.4 km s$^{-1}$ (LSR) |
| J1608 gas cavity inner radius | ~48 | not stated | au | 2 | we infer that the inner radius of the gas cavity is $\sim$ 48 au |
| J1608 inclination | 74 | not stated | deg | 3 | / Inclination                       / \[$^\circ$\]  / 74              / 30                                / |
| J1608 large grain ring radii | 77-87 | not stated | au | 3 | / $R_\mathrm{in}$-$R_\mathrm{out}$  / \[au\]        / $77 - 87$       / $15-22$         / $42-65$         / |
| J1608 small grain radii | 50-150 | not stated | au | 3 | / $R_\mathrm{in}$-$R_\mathrm{out}$  / \[au\]        / $50-150$        / $15-22$         / $42-65$         / |
| J1608 scale heights at 100 au (small / large) | 12 / 5 | not stated | au | 3 | we constrain the large grains to be located within a height of 5 au, while the small grains extend vertically up to 12 au |
| J1608 mm dust to gas scale height ratio | 0.41 | not stated | dimensionless | 3 | the modeling of J1608 gives mm dust scale heights on the order of $H_\mathrm{1.3\,mm}=0.41\,H_\mathrm{gas}$ |
| J1852 inclination | 30 | not stated | deg | 3 | / Inclination                       / \[$^\circ$\]  / 74              / 30                                / |
| Disks in sample with companion below 13 MJ | 15 of 22 | not stated | disks | 4 | While 15 out of the 22 cavities in our sample could be explained by a planet of less than 13 Jupiter masses |

## Qualitative findings

- Small grains are more extended vertically and radially than mm grains in J1608, consistent with settling and radial drift  
  > "the millimeter-sized grains are less extended vertically and radially than the micron-sized grains, indicating advanced settling and radial drift" (abstract)
- Scattered light cavities are smaller than mm cavities in all 22 disks  
  > "We observe that for each system the scattered light cavity radius is smaller than the millimeter radius" (5.3 Comparison with other transition disks)

## Claim tuples

- H: Do mm and micron grains have different distributions in J1608? | E: mcfost modeling of ALMA Band 6, SPHERE H-band and SED | R: Large grains ring 77-87 au with H=5 au; small grains 50-150 au with H=12 au | F: Advanced settling and radial drift segregate grain sizes | **supported**
- H: Can J1852 constrain vertical segregation? | E: Similar mcfost model with ALMA Band 3 and SED | R: Good model found but changing a_min of large grains to 300 um also works | F: Modeling remains degenerate due to low inclination | **partially**
- H: What explains scattered-light vs mm cavity size differences across 22 disks? | E: Ratio of cavity radii compared with Ovelar et al. 2013 predictions | R: 15 of 22 consistent with planets below 13 MJ; 7 need larger companions or multiple planets | F: Small grains flow inside the mm-grain trap; companions or multiple planets | **partially**

## Reasoning

- Why this data: Two K2 stars with similar properties but different inclinations selected to probe structure and cavity mechanisms  
  > "We selected these two transition disks around K2 stars with similar stellar properties, but seen at different inclinations" (2 Stellar and disk properties)
- Why this method: _not stated_
- Alternative: Grains larger than 1.2 um rejected for J1608 small-grain population; intermediate 0.5-1.2 um grains give too much backward scattering  
  > "These grains are therefore not compatible with the observations." (4.3 Modeling J1608)
- How they decided it was enough: _not stated_
- Limitation (authors): Model is a compromise and working model, not best fit; J1852 modeling degenerate  
  > "This should be considered as a working model to derive the main structural characteristics of the J1608 system." (4.3 Modeling J1608)
- Caveat (inferred, ours): No formal fitting or uncertainties on model parameters
- Caveat (inferred, ours): Strong parameter degeneracies (grain size, scale height) with fixed beta and p
- Caveat (inferred, ours): Comparison sample is heterogeneous in wavelengths and definitions of cavity radii
- Caveat (inferred, ours): ALMA data used at fairly low resolution, limiting radial constraints

## Reproducibility

- Data public (paper): Archival ALMA data used; SPHERE programs given by ID  
  > "We complement our datasets with archival ALMA observations" (abstract)
- Products in archive: _not stated_
- Missing: Model parameter files and mcfost setup details
- Missing: CASA version and imaging parameters
- Missing: Coronagraph attenuation map (in prep)
- Missing: PV diagram extraction details
- Data volume (inferred): ~10-50 GB for the two ALMA datasets
- Score (inferred): 3/5, Data are public and the model table is given, but modeling is manual with unspecified setup and no fitting statistics.
- Rediscovery candidate: no, Main results come from a manual, non-unique radiative transfer model with incomplete recipe; ALMA is a minor part.

## Links

- Method: (cite: pinte_2006; pinte_2009) (mcfost radiative transfer code)
- Method: (cite: Ginski_2016) (SPHERE data reduction approach)
- Method: (cite: Ovelar_2013) (Planet mass prescription from cavity radius ratio)
- Companion: (cite: ansdell_2018) (Reduction of the J1608 ALMA Band 6 data)
- Companion: (cite: van_der_marel_new_2018) (Thermo-chemical modeling of J1608 CO)
- Related: ALMA Lupus survey
- Related: SPHERE GTO
- Related: SEEDS

## Checks

```json
{
 "quotes": 70,
 "quotes_ok": 70,
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
  "facts": 81,
  "stated": 49,
  "rate": 0.605
 },
 "evidence_ok": true
}
```
