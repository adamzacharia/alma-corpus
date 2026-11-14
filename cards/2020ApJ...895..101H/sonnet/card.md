# Efficient Methanol Production on the Dark Side of a Prestellar Core

`2020ApJ...895..101H` | The Astrophysical Journal 2020 | first author: Harju, Jorma | arXiv: 1903.11298 | DOI: 10.3847/1538-4357/ab8f93

Card schema 1.0 | model claude-sonnet-5-5 | depth full | type observational_alma_primary

## Science

- Fields: star_formation, astrochemistry, milky_way_ism
- Question: Why is gaseous methanol and SO distributed asymmetrically around the prestellar core H-MM1, and what desorption mechanisms release methanol from grains there?  
  > "We discuss the origin of gas-phase methanol based on the observed molecular distributions and the physical conditions of the emission regions." (Introduction)
- Target **Ophiuchus/H-MM1**: coordinates methanol peak RA 16:27:59.5, Dec -24:33:30 (J2000)  
  > "we adopt a distance of 140 pc for the core." (Observations); "the methanol peak at RA 16:27:59.5, Dec. -24:33:30 (J2000)" (7.3); z/distance 140 pc  
  > "we adopt a distance of 140 pc for the core." (Observations); "the methanol peak at RA 16:27:59.5, Dec. -24:33:30 (J2000)" (7.3); distance from VLBA and Gaia distance determinations for L1688 (Ortiz-León et al. 2017, 2018)  
  > "we adopt a distance of 140 pc for the core." (Observations); "the methanol peak at RA 16:27:59.5, Dec. -24:33:30 (J2000)" (7.3)

## Data provenance

- ALMA projects: 2016.1.00035.S
- bands: Band 3 (3 mm)  
  > "which were observed simultaneously with the 3 millimeter continuum in the ALMA Band 3." (Observations)
- frequencies and spectral setup: NH2D 85.9 GHz and CH3OH 96.7 GHz cubes (95-107 m/s channels); SO at 99.3 GHz in continuum window, ~4.9 MHz (1.5 km/s) channels  
  > "This line is unresolved because the channel width in this spectral cube is $\sim
4.9$ MHz ($\sim 1.5\,\rm\,km\,s^{-1}$" (Observations)
- continuum bandwidth: _not stated_
- arrays: ALMA 12 m array (40 antennas) five-point mosaic plus ACA 7 m (10 antennas) single pointing; no total power  
  > "The total power (TP) antennas were not used." (Observations)
- configurations: one of the most compact 12 m configurations  
  > "imaged using the ALMA 12 m array (40 antennas) in one of its most compact configurations" (Observations)
- baselines: _not stated_
- angular resolution: natural-weight beams 3.8x2.5 arcsec (85.9 GHz) to 3.5x2.3 arcsec (99.3 GHz); common 4 arcsec circular beam used  
  > "In what follows, we use image cubes that were created using a common, circular $4\ensuremath{^{\prime\prime}}$ restoring beam for all lines." (Observations)
- max recoverable scale: ~60 arcsec  
  > "The largest recoverable scale of the images is approximately $60\ensuremath{^{\prime\prime}}$." (Observations)
- sensitivity: 3 mm continuum rms ~0.06 mJy/beam; line rms 0.011-0.049 K at 4 arcsec  
  > "For the 3 mm continuum map, the rms noise is approximately 0.06 mJy/beam." (Observations)
- time on source: _not stated_
- observing dates: _not stated_
- pi or archival as stated: _not stated_
- Line: o-NH2D 1_11-1_01 (85926.27 MHz)
- Line: CH3OH 2_k-1_k group (four lines) (96739.36-96755.51 MHz)
- Line: SO 3_2-2_1 (99299.87 MHz)
- Other facility **Spitzer IRAC**: 8 and 24 um maps used for N(H2) from extinction and dust temperature  
  > "we have used the 8 $\rm \mu m$ surface brightness map measured by the InfraRed Array Camera (IRAC) of the Spitzer Space Telescope" (Integrated intensity maps)
- Other facility **SCUBA-2**: 850 um dust continuum map  
  > "The target is prominent in the $850\,\mu$m dust continuum maps of Ophiuchus observed with SCUBA-2 (cite: 2015MNRAS.450.1094P)" (Observations)
- Other facility **Green Bank Ammonia Survey**: NH3(1,1),(2,2) maps for velocity dispersion profiles  
  > "calculated using $\rm NH_3(1,1)$ and $(2,2)$ inversion line data from the Green Bank Ammonia Survey" (Velocity dispersion profiles)
- Other facility **Herschel SPIRE**: dust color temperature map  
  > "dust color temperature map, $T_{\rm
  C}$, derived from Herschel/SPIRE maps (cite: 2017A&A...600A..61H)" (Column density map from 8 um extinction)
- External data: Dust opacity model (unprocessed grains with thin ice mantles), tau8/tau850=780  
  > "the model for unprocessed dust grains with thin ice mantles by (cite: 1994A&A...291..943O)" (Column density map from 8 um extinction) [from (cite: 1994A&A...291..943O)]
- External data: NH2D hyperfine structure model  
  > "takes into account the splittings owing to the electric quadrupole moments of both N and D nuclei (cite: 2016A&A...586L...4D)" (Column densities and velocity distributions) [from (cite: 2016A&A...586L...4D)]
- External data: Cosmic-ray sputtering fluxes of CH3OH  
  > "one obtains from Fig. 11 of (cite: 2019A&A...627A..55D) that the flux of sputtered $\rm CH_3OH$ molecules is" (6.1) [from (cite: 2019A&A...627A..55D)]
- Simulation/model as data: Dust radiative transfer model of an H-MM1-like core with isotropic field plus western point source, giving FUV field  
  > "The calculations were done using the dust continuum radiative transfer program described in (cite: 2019A&A...622A..79J)." (Dust temperature distribution)

## Processing

### Calibration

- pipeline or manual: data calibrated and imaged with CASA  
  > "The data were calibrated and imaged using the CASA version 4.7.2." (Observations)
- casa version: CASA 4.7.2  
  > "The data were calibrated and imaged using the CASA version 4.7.2." (Observations)
- pipeline version: _not stated_
- archive products used as is: _not stated_
- flux calibrator: _not stated_
- flux scale uncertainty: _not stated_
- self calibration: _not stated_

### Imaging

- task: _not stated_
- deconvolver: _not stated_
- weighting robust: natural weighting (for beam sizes quoted)  
  > "The synthesized beam sizes of naturally weighted images ranged from" (Observations)
- uv taper: _not stated_
- cell size: _not stated_
- image size: _not stated_
- masking: _not stated_
- multiscale scales: _not stated_
- continuum subtraction: _not stated_
- line free channels: _not stated_
- primary beam correction: _not stated_
- array combination: 12 m and 7 m data combined; no TP  
  > "The total power (TP) antennas were not used." (Observations)
- smoothing: _not stated_
- final beam: common circular 4 arcsec restoring beam  
  > "a common, circular $4\ensuremath{^{\prime\prime}}$ restoring beam for all lines" (Observations)
- final rms: _not stated_

### Inherited from earlier work

- Rotational temperature and column density procedure for E-CH3OH, no optical thickness assumption  
  > "adopting the procedure described by (cite: 2000ApJS..128..213N), where no assumption about the optical thickness of the lines is made" (Column densities and velocity distributions) [from (cite: 2000ApJS..128..213N)]
- Velocity dispersion profile method  
  > "The method is described in detail by (cite: 2019ApJ...872..207A)." (Velocity dispersion profiles) [from (cite: 2019ApJ...872..207A)]
- Dust color temperature map  
  > "derived from Herschel/SPIRE maps (cite: 2017A&A...600A..61H)" (Column density map from 8 um extinction) [from (cite: 2017A&A...600A..61H)]

### Not stated but needed to reproduce (our reading)

- CASA calibration scripts/steps and calibrators
- Continuum subtraction and line-free channels
- Cleaning parameters (threshold, masks, niter, cell, image size)
- Spitzer IRAC 8 um and 70 um map sources and processing details
- Gaussian fit initialization and uncertainty treatment
- Details of the core model density structure for RT and desorption calculation

## Analysis recipe

1. **Image and make integrated intensity maps**: Calibrate and image 12 m + ACA data in CASA; make cubes at common 4 arcsec beam and integrated intensity maps  
  > "The data were calibrated and imaged using the CASA version 4.7.2." (Observations)
   - software: CASA
   - parameter: 4 arcsec circular restoring beam  
  > "a common, circular $4\ensuremath{^{\prime\prime}}$ restoring beam for all lines" (Observations)
   - fitting: _not stated_
   - validation: _not stated_
2. **Derive H2 column density map from 8 um extinction**: Optical depth from IRAC 8 um absorption against fitted background; foreground fixed via tau8/tau850=780; divided by dust cross section  
  > "Finally, the $\rm H_2$ column density map shown in Fig. [1](#figure:line_maps)d) was calculated by dividing the $8\,\rm \mu m$ optical thickness map by the absorption cross-section of dust per $\rm H_2$ molecule" (Column density map from 8 um extinction)
   - parameter: cross-section 4.1e-23 cm2 per H2  
  > "$4.1\times10^{-23}\,{\rm cm^2\, \rm H_2\,
  molecule^{-1}}$" (Column density map from 8 um extinction)
   - assumption: Ossenkopf & Henning unprocessed thin-ice dust opacity model  
  > "the model for unprocessed dust grains with thin ice mantles by (cite: 1994A&A...291..943O)" (Column density map from 8 um extinction)
   - fitting: _not stated_
   - validation: _not stated_
3. **Derive methanol Trot, column densities, abundances**: Nummelin et al. method for E-CH3OH at positions with >=2 lines at 3 sigma; A-CH3OH from single A line assuming same Trot; divide by N(H2)  
  > "The calculation was limited to the positions where at least two of the $E-\rm CH_3OH$ lines are detected with $3\sigma$ significance." (Column densities and velocity distributions)
   - assumption: SO optically thin, Trot=10 K (or 5 K); equal E and A abundances  
  > "Assuming $T_{\rm rot}=10$ K, we get $N({\rm SO})=1.2\times10^{13}\,{\rm cm}^{-2} \times \int\, T_{\rm
  B}\, dv$" (Column densities and velocity distributions)
   - fitting: _not stated_
   - validation: _not stated_
4. **Fit line kinematics**: Multicomponent Gaussian fits to NH2D hyperfine structure and CH3OH lines (fixed separations, common dispersion); collapsed profiles, channel maps, dispersion maps  
  > "The ortho-$\rm NH_2D$ spectral cube was analyzed by performing multicomponent Gaussian fits to the hyperfine structure of the $1_{11}-1_{01}$ line" (Column densities and velocity distributions)
   - software: Glue
   - assumption: kinetic temperature 10 K for thermal width  
  > "nearly thermal, assuming a kinetic temperature of 10 K" (Column densities and velocity distributions)
   - fitting: Gaussian fits; sampler/priors not stated  
  > "The velocity distribution of methanol was derived by Gaussian fits to the four lines near 96.7 GHz." (Column densities and velocity distributions)
   - validation: _not stated_
5. **Dust temperature and FUV field via radiative transfer**: Td from 8, 70 and 850 um maps; test with dust continuum radiative transfer model of H-MM1-like core with asymmetric illumination  
  > "The combined strength of the isotropic component and the point source were then adjusted until the $850\,\rm \mu m$ surface brightness map agreed with the observations." (Dust temperature distribution)
   - software: dust continuum RT code of Juvela 2019
   - parameter: isotropic field 30 times Mathis et al. 1983 field; point source 10000 K blackbody  
  > "The isotropic field was set equal to 30 times the (cite: 1983A&A...128..212M) field" (Dust temperature distribution)
   - fitting: manual adjustment of field strength to match 850 um map  
  > "The strength of the external field was adjusted until the model could reproduce the observed surface brightness maps at $850\,\rm \mu m$." (Uneven illumination)
   - validation: Model-derived 70 um Td shows similar minimum shift as observed  
  > "shows a similar shift of the minimum as seen in Figure [10](#figure:taumidfar)f." (Dust temperature distribution)
6. **Model methanol abundance with uneven FUV illumination and estimate desorption rates**: Equilibrium grain-surface and gas-phase abundance equations with photodissociation and desorption; analytic desorption rates for CR, photo, reactive, grain-grain mechanisms  
  > "its equilibrium abundance on grains relative to H atoms can be written as" (7.1)
   - parameter: k_des = 5e-15 mol-1 s-1; f_CO=0.05 tuned so max X(CH3OH,s)=4e-6  
  > "The resulting factor is $f_{\rm CO}=0.05$." (7.1)
   - assumption: MRN grain size distribution, dust-to-gas 0.01  
  > "we adopt the MRN grain size distribution" (6.1)
   - fitting: _not stated_
   - validation: Compared model asymmetry (4:3) with observed >=10:1 contrast  
  > "the contrast between the peak methanol abundances on the eastern and western sides, $\ensuremath{\gtrsim}10:1$, cannot be reproduced by this model." (7.1)
7. **Assess Kelvin-Helmholtz shear layer**: Fit Plummer function to N(H2) profile; Brunt-Väisälä frequency, phase velocity, Richardson number criterion  
  > "We estimated the density and the density gradient in the supposed shear layer by fitting a Plummer-type function to the $\rm H_2$ column density profile" (7.4)
   - fitting: Plummer-type profile fit  
  > "by fitting a Plummer-type function to the $\rm H_2$ column density profile from the IRAC $8\,\mu$m absorption." (Desorption in a shear layer)
   - validation: minimum shear compared with observed gradient (factor 4 higher)  
  > "This value exceeds the north-south velocity gradient derived from the molecular line maps by a factor of 4." (7.4)

## Software

- **CASA** 4.7.2: calibration and imaging  
  > "The data were calibrated and imaged using the CASA version 4.7.2." (Observations)
- **Glue** : overlay of CH3OH and NH2D cubes in a video  
  > "using Glue[^1] which is an open-source Python library designed for the analysis of multi-dimensional related datasets" (Column densities and velocity distributions)

## Numeric results

| quantity | value | uncertainty | units | step | quote |
|---|---|---|---|---|---|
| Mean E-CH3OH rotational temperature | 10.3 | 0.7 | K | 3 | ${\bar T}_{\rm rot} = 10.3\pm0.7$ K |
| Peak N(E-CH3OH) | 1.1e14 | 0.1e14 | cm^-2 | 3 | $N(E-\rm CH_3OH)=1.1\pm0.1\times10^{14}\,\rm cm^{-2}$ |
| A/E methanol ratio | 1.3 | 0.2 | dimensionless | 3 | The weighted average of the $A/E$ ratio and its standard deviation are $1.3\pm0.2$ |
| Peak X(CH3OH) | ~8e-9 | not stated | relative to H2 | 3 | The highest methanol abundances, $X(\rm CH_3OH)\sim 8\times10^{-9}$ |
| X(SO) | 0.7-1.0e-9 | not stated | relative to H2 | 3 | $X({\rm SO}) \sim 0.7-1.0\times 10^{-9}$ |
| Velocity gradient | 0.7 km/s over 0.034 pc | not stated | km/s | 4 | The velocity change (including all channels with detectable emission) is approximately $0.7\,\rm km\,s^{-1}$ over a distance of 0.034 pc |
| Western FUV flux in model | 80,000 | not stated | photons cm^-2 s^-1 | 5 | the average FUV flux is approximately $F_{\rm FUV}=80,000$ photons $\rm cm^{-2}\,\rm s^{-1}$ |
| Brunt-Väisälä frequency | 1.3e-12 | not stated | Hz | 7 | The Brunt-Väisälä frequency obtained is $N \sim 1.3\times10^{-12}$ Hz |
| Minimum shear for KHI | ~80 | not stated | km/s/pc | 7 | or $\sim 80\, \rm km\,s^{-1}\,{\rm pc}^{-1}$ |

## Qualitative findings

- NH2D traces the dense core; CH3OH and SO form a halo, strongest on the eastern side  
  > "The dense core is seen in $\rm NH_2D$ emission, whereas the $\rm CH_3OH$ and SO distributions form a halo surrounding the core." (abstract)
- Dust temperature minimum lies on the eastern side near the methanol peak  
  > "the dust temperature reaches, indeed, its minimum on the eastern side of the core, close to the $\rm CH_3OH$ maximum" (7.1)

## Claim tuples

- H: Does asymmetric external illumination explain the methanol asymmetry? | E: Dust temperature maps, RT model and equilibrium abundance model | R: Model gives east:west peak ratio ~4:3 versus observed >=10:1 | F: Illumination contributes but cannot alone explain the contrast; enhanced desorption on the shaded side is needed | **partially**
- H: Is the bright methanol zone a shear layer with Kelvin-Helmholtz instability driving grain-grain desorption? | E: Morphology, Brunt-Väisälä and Richardson analysis, desorption rate estimates | R: Shear-induced collision desorption rate ~4e-15 mol-1 s-1 comparable to other mechanisms | F: Proposed as a plausible mechanism, not proven | **partially**

## Reasoning

- Why this data: _not stated_
- Why this method: _not stated_
- Alternative: Shocks rejected: no evidence of shock heating or large velocity gradients  
  > "do not show any evidence of shock heating or velocity gradients that would be large enough" (7.2)
- How they decided it was enough: _not stated_
- Limitation (authors): Boundaries not probed by lines other than CH3OH and SO, so turbulence asymmetry cannot be tested  
  > "The former condition cannot be properly tested using the present data" (7.3)
- Caveat (inferred, ours): Shear/KHI interpretation is based on morphology and order-of-magnitude estimates
- Caveat (inferred, ours): Single unresolved SO line gives only lower-limit column densities
- Caveat (inferred, ours): Desorption rates rely on many literature-adopted parameters
- Caveat (inferred, ours): Beam-filling factor of shear layer is very small

## Reproducibility

- Data public (paper): ALMA project data acknowledged via ADS/JAO.ALMA#2016.1.00035.S  
  > "The paper makes use of the following ALMA data: ADS/JAO.ALMA#2016.1.00035.S." (Conclusions)
- Products in archive: _not stated_
- Missing: Imaging parameters and calibration scripts
- Missing: IRAC/SCUBA-2/Herschel map processing details
- Missing: Exact model core structure for RT
- Data volume (inferred): ~10-50 GB (12 m mosaic + ACA, Band 3)
- Score (inferred): 3/5, ALMA data public and cube analysis basic, but imaging details missing and much of the paper is analytic/theoretical.
- Rediscovery candidate: no, Imaging recipe incomplete and key conclusions depend on interpretive modelling rather than purely numeric results.

## Links

- Method: (cite: 2000ApJS..128..213N) (Trot and column density procedure for methanol)
- Method: (cite: 2019ApJ...872..207A) (velocity dispersion profile method)
- Companion: (cite: 2017A&A...600A..61H) (earlier study of H-MM1 including Herschel dust temperature map and NH2D modelling)
- Related: Green Bank Ammonia Survey
- Related: SCUBA-2 Ophiuchus survey

## Checks

```json
{
 "quotes": 74,
 "quotes_ok": 74,
 "quote_pass_rate": 1.0,
 "quotes_too_long": 0,
 "unsupported_facts": 0,
 "project_codes": 1,
 "codes_not_in_text": [],
 "codes_not_in_obscore": [],
 "obscore_codes_not_in_card": [],
 "codes_printed_but_missing": [],
 "numeric_results": 9,
 "numeric_problems": 0,
 "fill": {
  "facts": 89,
  "stated": 55,
  "rate": 0.618
 },
 "evidence_ok": true
}
```
