# The SOMA Atomic Outflow Survey. I. An Atomic O I and Highly Ionized O III Outflow from Massive Protostar G11.94-00.62

`2026ApJ..1003...26O` | The Astrophysical Journal 2026 | first author: Oakey, Phillip | arXiv: 2509.20551 | DOI: 10.3847/1538-4357/ae5485

Card schema 1.0 | model claude-sonnet-5-5 | depth light | type multi_facility_alma_minor

## Science

- Fields: star_formation
- Question: What do far-infrared [O III] and [O I] lines from SOFIA/FIFI-LS, supported by archival ALMA molecular lines, reveal about the outflow and protostellar properties of massive protostar G11.94-0.62?  
  > "We report detection of [O III] $^3P_2\rightarrow^3P_1$ emission at 52 $\mu$m from the massive protostar G11.94-0.62, tracing highly ionized gas." (abstract)
- Target **G11.94-00.62**: coordinates ALMA continuum peak RA 18h14m01s00, Dec -18d53m24.96s  
  > "We adopt a distance of 4.02 kpc and a $v_\text{lsr}$ of 37.0 km s$^{-1}$ (cite: 2015A&A...579A..91W)." (1 Introduction); "determining the continuum peak position at (R.A.: 18$^h$14$^m$01s00, Decl.: $-$18$^\circ$53$'$24$''$96)" (3.1.1 Astrometric Correction); z/distance 4.02 kpc; vlsr 37.0 km/s  
  > "We adopt a distance of 4.02 kpc and a $v_\text{lsr}$ of 37.0 km s$^{-1}$ (cite: 2015A&A...579A..91W)." (1 Introduction); "determining the continuum peak position at (R.A.: 18$^h$14$^m$01s00, Decl.: $-$18$^\circ$53$'$24$''$96)" (3.1.1 Astrometric Correction); distance from (cite: 2015A&A...579A..91W)  
  > "We adopt a distance of 4.02 kpc and a $v_\text{lsr}$ of 37.0 km s$^{-1}$ (cite: 2015A&A...579A..91W)." (1 Introduction); "determining the continuum peak position at (R.A.: 18$^h$14$^m$01s00, Decl.: $-$18$^\circ$53$'$24$''$96)" (3.1.1 Astrometric Correction)

## Data provenance

- ALMA projects: 2021.1.00095.S, 2019.1.00195.L
- bands: _not stated_
- frequencies and spectral setup: ALMAGAL: four SPWs 216.960–218.832, 218.037–218.505, 219.032–220.905, 220.337–220.805 GHz; channels 488, 122, 488, 122 kHz  
  > "covering frequencies from 216.960–218.832 GHz, 218.037–218.505 GHz, 219.032–220.905 GHz, and 220.337–220.805 GHz with a channel width of 488 kHz, 122 kHz, 488 kHz, and 122 kHz, respectively." (2.2 ALMA)
- continuum bandwidth: _not stated_
- arrays: QUARKS 12m C-2 and C-5 plus ACA 7m  
  > "using the 12m-array in the C-2 and C-5 configurations, as well as the ACA (Atacama Compact Array) 7m-array" (2.2 ALMA)
- configurations: _not stated_
- baselines: _not stated_
- angular resolution: QUARKS ~0.3''; ALMAGAL (1.31-1.37'')x(1.06-1.08'')  
  > "The synthesized beam is $\sim$0$''$3 with a sensitivity of $\sim$6 mJy beam$^{-1}$." (2.2 ALMA); "The synthesized beam sizes are (1$''$31–1$''$37)$\times$(1$''$06–1$''$08)." (2.2 ALMA)
- max recoverable scale: _not stated_
- sensitivity: ~6 mJy/beam (both datasets)  
  > "The sensitivity is $\sim$6 mJy beam$^{-1}$." (2.2 ALMA)
- time on source: _not stated_
- observing dates: _not stated_
- pi or archival as stated: Archival ALMA data (QUARKS, ALMAGAL)  
  > "We also obtained archival ALMA (Atacama Large Millimeter/submillimeter Array) data" (2.2 ALMA)
- Line: 12CO J=2-1 (not stated)
- Line: 13CO, C18O J=2-1 (not stated)
- Line: H2CO 3_03-2_02 (not stated)
- Line: CH3OH 4_22-3_12 (not stated)
- Other facility **SOFIA/FIFI-LS**: Far-IR [O III] 52, [O I] 63 and 145, CO 186 micron cubes (primary data)  
  > "The program (project ID 09_0169; PI: Y.-L. Yang) covers 18 massive protostars" (2.1 SOFIA FIFI-LS)
- Other facility **LBT/LUCI**: NIR K, Brgamma, H2 imaging  
  > "The N3.75 camera was employed, offering a field of view of $4\ensuremath{'} \times 4\ensuremath{'}$ and a pixel scale of 0.12$''$." (2.3 LBT)
- Other facility **Spitzer, Herschel, WISE, VLA**: Archival continuum images for SED and astrometry  
  > "We applied this approach to the continuum images at Spitzer IRAC bands (3.6, 4.5, 5.8, and 8.0 $\mu$m), WISE Band 3 and 4 at 12 and 22 $\mu$m" (3.1.2 Continuum Measurements)
- External data: Distance 4.02 kpc and vlsr 37.0 km/s  
  > "We adopt a distance of 4.02 kpc and a $v_\text{lsr}$ of 37.0 km s$^{-1}$ (cite: 2015A&A...579A..91W)." (1 Introduction) [from (cite: 2015A&A...579A..91W)]
- External data: Dust opacities at 52, 63, 145 micron (Ossenkopf-Henning OH5 and Kim et al. models)  
  > "for the moderately coagulated thin ice mantle model of (cite: 1994AA...291..943O) (hereafter the OH5 dust model), the equivalent $\kappa$ is $3.09\:{\rm cm^2\:g}^{-1}$" (4.6.1 The Ionized Outflow) [from (cite: 1994AA...291..943O); (cite: 1994ApJ...422..164K)]
- Simulation/model as data: Zhang & Tan protostellar model grid (turbulent core accretion) used for SED fitting  
  > "a self-consistent model grid of massive protostellar cores has been developed, combining the evolution of the protostar and outflow." (4.1 Protostellar Properties from SED Fitting)

## Processing

### Calibration

- pipeline or manual: _not stated_
- casa version: CASA 6.6.0  
  > "The calibrated visibilities of these data were combined using CASA 6.6.0" (2.2 ALMA)
- pipeline version: _not stated_
- archive products used as is: ALMAGAL imaging products taken from archive without further calibration/imaging; QUARKS calibrated visibilities combined  
  > "the imaging products were gathered from the ALMA Science Archive without further calibration and imaging." (2.2 ALMA)
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
- array combination: 12m C-2, C-5 and ACA visibilities combined and deconvolved together  
  > "The calibrated visibilities of these data were combined using CASA 6.6.0 (cite: 2022PASP..134k4501C) and deconvolved together." (2.2 ALMA)
- smoothing: _not stated_
- final beam: _not stated_
- final rms: _not stated_

### Inherited from earlier work

- QUARKS reduction and imaging details  
  > "The details of the reduction and imaging processes are discussed in (cite: 2024RAA....24b5009L)." (2.2 ALMA) [from (cite: 2024RAA....24b5009L)]
- SED aperture, flux and uncertainty measurement and good-model criteria  
  > "We followed the approach developed in (cite: 2023ApJ...942....7F)" (3.1.2 Continuum Measurements) [from (cite: 2023ApJ...942....7F)]
- Molecular outflow mass/momentum methodology  
  > "Utilizing methodology from (cite: 2014ApJ...783...29D) and (cite: 2019ApJ...873...73Z), we derive the outflow mass and momentum from the TP spectral cube" (4.6.3 The Molecular Outflow) [from (cite: 2014ApJ...783...29D); (cite: 2019ApJ...873...73Z)]

### Not stated but needed to reproduce (our reading)

- ALMA total power 12CO data project code and processing
- Imaging parameters (robust, cell, mask, deconvolver) for combined 12m+7m 13CO, C18O, H2CO, CH3OH cubes
- Velocity channels and moment ranges for blue/red maps
- Which project provided TP and the 13CO/C18O data
- Details of the 12CO mass-calculation formulae (opacity correction, inclination)

## Analysis recipe

1. **Measure FIFI-LS continuum and subtract**: Average line-free wavelengths per pixel and subtract from cubes  
  > "Then, for each pixel, we measure the average flux density within the selected wavelengths for continuum, deriving a continuum image." (3.1 Continuum)
   - software: photutils
   - fitting: _not stated_
   - validation: _not stated_
2. **Fit SED for protostellar properties**: Fit Zhang & Tan model grid, average models with chi2<2  
  > "we select the 44 models with the lowest $\chi^2$ values, ranging from 0.85 to 1.97" (4.1 Protostellar Properties from SED Fitting)
   - software: sedcreator SEDFitter
   - fitting: _not stated_
   - validation: _not stated_
3. **Estimate ionized outflow mass flux**: PyNeb [O III] emissivity vs ne, Te linked to column density with extinction correction  
  > "Using `PyNeb` (cite: 2015A&A...573A..42L), we calculate the emissivity of [O III] at given values of $n_e$ and $T_e$" (4.6.1 The Ionized Outflow)
   - software: PyNeb
   - assumption: XO=3e-4, Te=1e4 K, fV=1/3, all O in O2+, He singly ionized  
  > "adopt an O abundance of $X_{\rm O}=3\times10^{-4}$ with respect to H nuclei." (4.6.1 The Ionized Outflow)
   - fitting: _not stated_
   - validation: Self-consistency of ne and nH  
  > "Thus, approximately self-consistent results are achieved for the case $n_e=300\:{\rm cm}^{-3}$, which implies $N_{\rm H}\simeq8.7\times10^{19}\:{\rm cm}^{-2}$ and $n_{\rm H}\simeq 325\:{\rm cm}^{-3}$" (Mass and Momentum Outflow Rates, The Ionized Outflow)
4. **Estimate molecular outflow from ALMA TP 12CO**: Channel-by-channel optically thin mass, excluding inner ±5 km/s, within 22.6'' beam  
  > "excluding the inner $\pm5$ km s$^{-1}$ to avoid confusion with any surrounding quiescent gas." (4.6.3 The Molecular Outflow)
   - parameter: Tex = 17.5 K  
  > "an excitation temperature $T_{\text{ex}}$ for the $^{12}$CO ($2\rightarrow1$) transition of 17.5 K." (4.6.3 The Molecular Outflow)
   - assumption: 12CO abundance 1e-4 relative to H2, optically thin  
  > "We assume optically thin emission, a $^{12}$CO abundance of $10^{-4}$ with respect to H$_2$" (4.6.3 The Molecular Outflow)
   - fitting: _not stated_
   - validation: _not stated_

## Software

- **CASA** 6.6.0: Combining and deconvolving QUARKS ALMA data  
  > "The calibrated visibilities of these data were combined using CASA 6.6.0" (2.2 ALMA)
- **PyNeb** : [O III] emissivity  
  > "Using `PyNeb` (cite: 2015A&A...573A..42L), we calculate the emissivity of [O III]" (4.6.1 The Ionized Outflow)
- **3d-pdr** : 1-D PDR modeling of [O I] lines  
  > "we utilize a 1-D adaptation of the 3d-pdr software" (4.6.2 The Atomic Outflow)
- **sedcreator** : SedFluxer photometry and SEDFitter  
  > "using the fitting tool `SEDFitter` within the Python package `sedcreator`" (4.1 Protostellar Properties from SED Fitting)
- **photutils** : Aperture photometry of spectra  
  > "The extraction is performed by using `aperture_photometry()` from `photutils` at each wavelength." (3.2 Line Emission)

## Numeric results

| quantity | value | uncertainty | units | step | quote |
|---|---|---|---|---|---|
| Ionized outflow mass flux | 1.2e-4 | not stated | Msun/yr | 3 | Ionized / 0.116 / 211 / 24.5 / 980 / $1.2\times10^{-4}$ |
| Atomic outflow mass flux | 5.1e-6 | not stated | Msun/yr | 0 | Atomic / 0.038 / 43.3 / 1.65 / 7,500 / $5.1\times 10^{-6}$ |
| Molecular outflow mass | 4.14 | not stated | Msun | 4 | a total CO-traced outflow mass of $m_{\rm out,mol}=4.14\:M_\odot$ |
| Molecular outflow mass flux | 2.6e-4 | not stated | Msun/yr | 4 | $\dot{m}_{\rm out,mol} = 2.6\times 10^{-4}\:M_\odot\:{\rm yr}^{-1}$ |
| Protostellar mass from SED | 22.4 | +21/-11 | Msun | 2 | $22.4^{+21}_{-11}$ |
| [O I] 63/145 line ratio | 2.30 | 0.20 | dimensionless | 0 | The measured ratio is $2.30\pm0.20$. |

## Qualitative findings

- ALMA CO isotopologues, H2CO and CH3OH show NE redshifted and SW blueshifted emission consistent with the [O III]-implied axis; red lobe wide-angle (~100-110 deg)  
  > "We estimate a $\sim100^\circ-110^\circ$ for the edge-to-edge outflow opening angle of the red-shifted lobe." (4.4 Discussion on Outflow Orientation)

## Claim tuples

- H: Do [O III] and [O I] trace a bipolar wide-angle outflow from G11.94? | E: Blue/red-shifted maps of FIFI-LS lines compared with ALMA molecular tracers | R: Velocity gradient NE-SW; ALMA tracers show same axis | F: Outflow with red lobe NE and blue lobe SW, PA ~ -143 deg | **supported**
- H: Is the ionized outflow the primary disk wind while molecular gas is swept up? | E: Mass and momentum fluxes for ionized, atomic and molecular components | R: Ionized mass flux ~10% of accretion rate; molecular dominates mass flux | F: Ionized outflow is primary; molecular is secondary swept-up | **supported**

## Reasoning

- Why this data: Archival ALMA data used to investigate the nature of the FIFI-LS emission  
  > "to investigate the nature of the emission lines detected in our FIFI-LS observations" (2.2 ALMA)
- Why this method: _not stated_
- Alternative: NW-SE outflow scenario disfavored in favor of NE-SW  
  > "there are several reasons why we favor the outflow in the NE-SW direction instead of this scenario." (4.4 Discussion on Outflow Orientation)
- How they decided it was enough: _not stated_
- Limitation (authors): Molecular emission contaminated by nearby protostars; Tex choice gives minimum mass  
  > "The molecular emission from these protostars contaminates the analysis of the outflow morphology from G11.94" (4.3 Additional Outflow Tracers)
- Caveat (inferred, ours): Outflow rates rely on assumed filling factor, extinction and 3D velocity equal to line-of-sight velocity
- Caveat (inferred, ours): Single Tex and optically thin CO assumption
- Caveat (inferred, ours): Low FIFI-LS spectral resolution limits kinematics

## Reproducibility

- Data public (paper): Archival ALMA data from ALMA archive  
  > "the imaging products were gathered from the ALMA Science Archive" (2.2 ALMA)
- Products in archive: _not stated_
- Missing: QUARKS imaging parameters
- Missing: TP data provenance
- Missing: Channel ranges for ALMA moment maps
- Data volume (inferred): ~50-100 GB
- Score (inferred): 4/5, ALMA is supporting; ALMA processing is mostly inherited, though outflow calculations are described.
- Rediscovery candidate: no, ALMA role is minor and ALMA processing details are inherited or missing.

## Links

- Method: (cite: 2023ApJ...942....7F) (SED aperture, photometry and model selection approach)
- Method: (cite: 2024RAA....24b5009L) (QUARKS ALMA reduction and imaging)
- Related: SOMA Atomic Outflow Survey
- Related: QUARKS
- Related: ALMAGAL
- Related: ATOMS

## Checks

```json
{
 "quotes": 59,
 "quotes_ok": 59,
 "quote_pass_rate": 1.0,
 "quotes_too_long": 0,
 "unsupported_facts": 0,
 "project_codes": 2,
 "codes_not_in_text": [],
 "codes_not_in_obscore": [],
 "obscore_codes_not_in_card": [],
 "codes_printed_but_missing": [],
 "numeric_results": 6,
 "numeric_problems": 0,
 "fill": {
  "facts": 75,
  "stated": 39,
  "rate": 0.52
 },
 "evidence_ok": true
}
```
