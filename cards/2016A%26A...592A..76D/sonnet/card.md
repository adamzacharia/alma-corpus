# ALMA-resolved salt emission traces the chemical footprint and inner wind morphology of VY Canis Majoris

`2016A&A...592A..76D` | Astronomy and Astrophysics 2016 | first author: Decin, L. | arXiv: 1605.03077 | DOI: 10.1051/0004-6361/201527934

Card schema 1.0 | model claude-sonnet-5-5 | depth full | type archival_reuse

## Science

- Fields: evolved_stars, astrochemistry
- Question: What is the inner-wind density structure of the red supergiant VY CMa, and how do gaseous NaCl and dust interact chemically, as traced by spatially resolved NaCl emission?  
  > "Specifically, the objective is to unravel the density structure in the inner envelope and to examine the chemical interaction between some gas and dust species." (abstract)
- Target **VY CMa**: coordinates 07h22m58.326s, -25d46m03.042s  
  > "the position of the peak of the second continuum component has been shown to coincide with the location of the stellar position ‘VY’ at $\alpha$ = 07h22m58.326s and $\delta$ = $-$25$^\circ$46$^{\prime}$03.042$''$" (2 Observations); "or 5.53 mas at a distance of 1.2$\pm$0.1 kpc (cite: Choi2008PASJ...60.1007C; Zhang2012ApJ...744...23Z)" (1.1 The red supergiant VY CMa); z/distance 1.2±0.1 kpc  
  > "the position of the peak of the second continuum component has been shown to coincide with the location of the stellar position ‘VY’ at $\alpha$ = 07h22m58.326s and $\delta$ = $-$25$^\circ$46$^{\prime}$03.042$''$" (2 Observations); "or 5.53 mas at a distance of 1.2$\pm$0.1 kpc (cite: Choi2008PASJ...60.1007C; Zhang2012ApJ...744...23Z)" (1.1 The red supergiant VY CMa); distance from Choi2008; Zhang2012  
  > "the position of the peak of the second continuum component has been shown to coincide with the location of the stellar position ‘VY’ at $\alpha$ = 07h22m58.326s and $\delta$ = $-$25$^\circ$46$^{\prime}$03.042$''$" (2 Observations); "or 5.53 mas at a distance of 1.2$\pm$0.1 kpc (cite: Choi2008PASJ...60.1007C; Zhang2012ApJ...744...23Z)" (1.1 The red supergiant VY CMa)

## Data provenance

- ALMA projects: _none stated_
- bands: Band 7 (NaCl lines); Band 9 also observed in the SV run  
  > "VY CMa was observed with ALMA during Science Verification in band 7 and band 9" (1 Introduction)
- frequencies and spectral setup: _not stated_
- continuum bandwidth: _not stated_
- arrays: 16-20 12-m antennas  
  > "using 16–20 12-m antennas on baselines from 0.014–2.7 km" (2 Observations)
- configurations: _not stated_
- baselines: 14 m to 2.7 km  
  > "using 16–20 12-m antennas on baselines from 0.014–2.7 km" (2 Observations)
- angular resolution: ~0.24'' x 0.13''  
  > "The synthesized beamsize for the band 7 data is $\sim 0.24\ensuremath{''} \times 0.13\ensuremath{''}$" (2 Observations)
- max recoverable scale: all flux recovered on scales <13''; reliable imaging up to at least 8''  
  > "suggesting that we recover all the flux on scales $<13$$^{\prime\prime}$, with reliable imaging on scales up to at least 8$^{\prime\prime}$" (2 Observations)
- sensitivity: rms 19-195 mJy/beam km/s per 1 km/s channel depending on line  
  > "v=1 J=24-23 | 309.787 | 480.09 | 0.017 | 19" (Table 1)
- time on source: _not stated_
- observing dates: 2013 16–19 August  
  > "VY CMa was observed for ALMA Science Verification on 2013 16–19 August" (2 Observations)
- pi or archival as stated: ALMA Science Verification data  
  > "ALMA Science Verification (SV) data in band 7" (abstract)
- Line: NaCl v=1 J=24-23 (309.787 GHz)
- Line: NaCl v=0 J=24-23 (312.110 GHz)
- Line: NaCl v=1 J=25-24 (322.650 GHz)
- Line: NaCl v=0 J=25-24 (325.069 GHz)
- External data: SiS v=1 J=16-15, 17-16, 19-18 flux densities used to estimate SiS J=18-17 blend (~1.1 Jy)  
  > "they measured maximum flux densities of 0.96 Jy for the SiS v=1 J=16-15 line and 0.97 Jy for the J=17-16 line." (3.1 Spectral line profiles) [from Kaminski2013ApJS..209...38K]
- External data: Thermodynamic and velocity model of the VY CMa wind (density, temperature, mass-loss rate, dust-to-gas 0.002)  
  > "Using a mass-loss rate $\hbox{$\dot{M}$}$ of $1\times10^{-4}$ M$_{\odot}$ yr$^{-1}$ and the gas velocity structure as derived from solving the momentum equation (cite: Decin2006A&A...456..549D)" (4.1.2) [from Decin2006A&A...456..549D]
- External data: Grain temperature of ~130-170 K at the SW clump  
  > "In VY CMa (cite: Shenoy2013AJ....146...90S) derive a grain temperature of $\sim$ 130–170 K at the ‘SW’ clump" (4.1.1) [from Shenoy2013AJ....146...90S]
- External data: NaCl photodissociation cross-sections  
  > "the photodissociation cross-sections of NaCl measured by (cite: Silver1986JChPh..84.4378S)" (4.1.1) [from Silver1986JChPh..84.4378S]

## Processing

### Calibration

- pipeline or manual: _not stated_
- casa version: _not stated_
- pipeline version: _not stated_
- archive products used as is: _not stated_
- flux calibrator: _not stated_
- flux scale uncertainty: accurate to at least 10%  
  > "The absolute astrometric accuracy of the lines described here is 35 mas and the flux density scale is accurate to at least 10%." (2 Observations)
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
- continuum subtraction: continuum subtracted before making line cubes  
  > "The continuum was subtracted before making the final line cubes." (2 Observations)
- line free channels: _not stated_
- primary beam correction: _not stated_
- array combination: _not stated_
- smoothing: cubes at 1 km/s spectral resolution  
  > "Image cubes were made at 1 km s$^{-1}$ spectral resolution around the NaCl frequencies" (2 Observations)
- final beam: 0.217-0.239'' x 0.119-0.134'' (per line)  
  > "v=0 J=24-23 | 312.110 | 119.83 | 0.013 | 30 | 0.239$\times$0.134, 29.48$^\circ$" (Table 1)
- final rms: _not stated_

### Inherited from earlier work

- Observations, data reduction and calibration summarised in earlier paper  
  > "(cite: Richards2014A&A...572L...9R) summarises the observations, data reduction and H$_2$O maser results" (2 Observations) [from Richards2014A&A...572L...9R]
- Relative line alignment good to ~2 mas using stellar continuum  
  > "so that the relative alignment of all lines is good to $\sim$2 mas (cite: Richards2014A&A...572L...9R)" (2 Observations) [from Richards2014A&A...572L...9R]
- Grain size distribution slope -3.5  
  > "The slope of $-3.5$ is typical for interstellar grains (cite: Mathis1977ApJ...217..425M)." (4.1.1) [from Mathis1977ApJ...217..425M]

### Not stated but needed to reproduce (our reading)

- CASA version and reduction/imaging details (task, weighting, robust, cell, image size, masking, deconvolver)
- Line-free channels for continuum subtraction
- Whether archival SV calibrated products were used as is
- Procedure for correcting the 325 GHz blends
- Integration limits for moment-zero maps
- Dust temperature profile and Y_PD assumptions of the chemical network beyond the quoted ones

## Analysis recipe

1. **Extract line spectra**: Flux densities extracted for a 1'' diameter region around the star for the four NaCl lines; blends from H2O maser and SiS estimated and subtracted  
  > "Fig. [1] shows the flux densities extracted for a 1$^{\prime\prime}$ diameter region around the stellar position ‘VY’ for the four NaCl lines" (3.1 Spectral line profiles)
   - fitting: _not stated_
   - validation: v=0 and v=1 line pairs compared for similar intensities  
  > "Given the similar energy levels, quantum numbers, and Einstein-A coefficients, one would expect similar line intensities and spatial distributions for both lines in the same vibrational level." (Results, Spectral line profiles)
2. **Map NaCl spatial distribution and fit clumps**: Moment-zero maps and channel maps; 2D elliptical Gaussians fitted to each clump  
  > "We measured the sizes and positions of each spatial region by fitting two dimensional elliptical Gaussian components" (3.2 Spatial distribution)
   - parameter: Position uncertainty = (mean beam size)/(signal to noise ratio)  
  > "The position uncertainties given are estimated conservatively from the noise as (mean beam size)/(signal to noise ratio)" (3.2 Spatial distribution)
   - fitting: 2D elliptical Gaussians, deconvolved from beam  
  > "We measured the sizes and positions of each spatial region by fitting two dimensional elliptical Gaussian components" (Results, Spatial distribution)
   - validation: consistency of NB position across lines within 8 mas  
  > "The brightest ‘NB’ component is aligned to within 8 mas in both coordinates at 309, 312 and 322 GHz" (Table notes)
3. **Model NaCl gas-grain chemistry**: Simplified network of accretion, thermal desorption and photodesorption; analytic steady-state solution for T_b = 5000, 10000, 15000 K  
  > "we have decided to study the evolution of the NaCl abundance for three different values of the surface binding energies: 5 000 K, 10 000 K, and 15 000 K." (4.1.2)
   - parameter: n_H = 1e8 cm^-3 at ~10 R*, S=1, F_FUV Y_PD = 3e5  
  > "a hydrogen number density of $1\times10^8$ cm$^{-3}$ is reached at $\sim$10 R$_{\star}$" (4.1.2)
   - assumption: Dust-to-gas mass ratio 0.002; grain sizes 0.005-0.25 micron; solar Cl abundance 3.2e-7  
  > "For a dust-to-gas mass ratio of 0.002 (cite: Decin2006A&A...456..549D), $K$ is $\sim$2.8$\times10^{-26}$ cm$^{2.5}$ per H atom" (4.1.1)
   - fitting: _not stated_
   - validation: Compared qualitatively with ALMA detection of NaCl at 1.22''  
  > "The ALMA data clearly show gaseous NaCl emission around 1.22$^{\prime\prime}$ in the south-western extension, at a place where also scattering by dust grains peaks" (Discussion, NaCl gas-grain chemistry)
4. **Interpret morphology with PV diagrams**: Position-velocity diagrams along PA 50 deg and perpendicular, compared with axisymmetric and localized-ejection scenarios  
  > "Two position-velocity (PV) diagrams of the NaCl 312 GHz ALMA observations are shown in Fig. [10]" (4.2.1)
   - fitting: _not stated_
   - validation: Compared with HST, maser and CO literature  
  > "In this section we compare the NaCl emission seen in the ALMA channel maps to some other results presented in the literature." (Results, Morphological comparison to other tracers of the envelope)

## Software


## Numeric results

| quantity | value | uncertainty | units | step | quote |
|---|---|---|---|---|---|
| NB mean separation from star | 100 mas (~18 R*) | 10 mas | mas | 2 | The average separations of ‘NB’ and ‘SB’ from the stellar position, ‘VY’, are 100 mas (or $\sim$18 R$_{\star}$) and 190 mas |
| SB mean separation from star | 190 mas (~34 R*) | 10 mas | mas | 2 | The average separations of ‘NB’ and ‘SB’ from the stellar position, ‘VY’, are 100 mas (or $\sim$18 R$_{\star}$) and 190 mas |
| SW1 distance from VY | 1.22 (~220 R*) | not stated | arcsec | 2 | ‘SW1’, seen at 312 GHz is 1.22$^{\prime\prime}$ ($\sim$220 R$_{\star}$) from VY |
| NB-SB separation | 265 mas (~48 R*) | 10 mas | mas | 2 | The separation between ‘NB’ and ‘SB’ is 265 mas ($\sim$48 R$_{\star}$). |
| NaCl v=0 J=24-23 NB total flux | 10.539 | size err 35 mas | Jy km/s | 2 | NB / 5.327 / 10.539 / 07:22:58.3253 |
| Turn-over T_b/T_d for gaseous fraction | ~50 | not stated | dimensionless | 3 | The turn-over point is around $T_b/T_d \sim 50$ |
| Gaseous NaCl fraction at low dust temperature | ~10% | not stated | percent | 3 | only about 10% of the NaCl abundance resides in the gas phase at low dust temperatures |
| Polar axis position angle | ~50 | not stated | deg | 4 | a preferred axis oriented NE/SW at a PA of $\sim$50$^\circ$ |

## Qualitative findings

- NaCl emission is resolved into NB, SB and SW components, offset from the dust continuum peaks; NaCl velocities lie well below the terminal velocity.  
  > "The velocity traced by the gaseous NaCl line profiles is significantly lower than the average wind terminal velocity" (abstract)

## Claim tuples

- H: Is the inner wind consistent with a single axisymmetric geometry? | E: Channel maps and PV diagrams of NaCl compared with literature | R: Axial symmetry along PA ~50 deg fits partly but localized clumps remain | F: Both an equatorial density enhancement and localized mass ejections are needed | **supported**
- H: Why does gaseous NaCl survive far from the star? | E: Simplified gas-grain network with accretion, thermal and photodesorption | R: Photodesorption is negligible; thermal desorption is insufficient at Td<100 K | F: Shock-induced sputtering from localized ejections is proposed | **partially**

## Reasoning

- Why this data: _not stated_
- Why this method: _not stated_
- Alternative: Photodesorption by stellar FUV photons rejected as explanation for SW gaseous NaCl  
  > "Photodesorption by stellar photons seems not to be a viable explanation for the detection of gaseous NaCl at 220 R$_{\star}$" (abstract)
- How they decided it was enough: _not stated_
- Limitation (authors): Only 16-20 antennas; cannot prove either scenario  
  > "The present data, obtained with only 16–20 ALMA antennas, can not prove the validity of both scenarios" (5 Conclusions)
- Caveat (inferred, ours): Chemical network has free parameters (T_b, sticking, Y_PD) not constrained by data
- Caveat (inferred, ours): Morphological interpretation is qualitative with no kinematic or radiative-transfer fit
- Caveat (inferred, ours): The 325 GHz line is blended and its correction is approximate

## Reproducibility

- Data public (paper): ALMA Science Verification data with project ID acknowledged  
  > "This paper makes use of the following ALMA data: ADS/JAO.ALMA2011.0.00011.SV." (Acknowledgements)
- Products in archive: _not stated_
- Missing: CASA imaging parameters
- Missing: Moment integration ranges
- Missing: Dust temperature profile used for the network
- Data volume (inferred): tens of GB
- Score (inferred): 4/5, Public SV data and clear analytic network, but imaging parameters and software are not stated.
- Rediscovery candidate: no, Imaging recipe is incomplete and the main results are mostly qualitative.

## Links

- Companion: Richards2014A&A...572L...9R (Observations, reduction and H2O masers from the same SV data)
- Companion: OGorman2015A&A...573L...1O (Continuum of the same data)
- Companion: DeBeck2015 (TiO2 lines from the same data)
- Related: ALMA Science Verification

## Checks

```json
{
 "quotes": 57,
 "quotes_ok": 57,
 "quote_pass_rate": 1.0,
 "quotes_too_long": 0,
 "unsupported_facts": 0,
 "project_codes": 0,
 "codes_not_in_text": [],
 "codes_not_in_obscore": [],
 "obscore_codes_not_in_card": [
  "2011.0.00011.SV"
 ],
 "codes_printed_but_missing": [],
 "numeric_results": 8,
 "numeric_problems": 0,
 "fill": {
  "facts": 68,
  "stated": 39,
  "rate": 0.574
 },
 "evidence_ok": true
}
```
