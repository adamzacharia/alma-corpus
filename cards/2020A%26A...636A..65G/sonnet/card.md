# ALMA chemical survey of disk-outflow sources in Taurus (ALMA-DOT). I. CO, CS, CN, and H<SUB>2</SUB>CO around DG Tau B

`2020A&A...636A..65G` | Astronomy and Astrophysics 2020 | first author: Garufi, A. | arXiv: 2002.10195 | DOI: 10.1051/0004-6361/201937247

Card schema 1.0 | model claude-sonnet-5-5 | depth full | type observational_alma_primary

## Science

- Fields: protoplanetary_disks, astrochemistry, star_formation
- Question: What are the dust and gas (CO, CS, CN, H2CO) distributions of the Class I disk DG Tau B, and what do they say about its inner depression, chemistry and outflows?  
  > "we report on ALMA Cycle 4 observations of the continuum, CO, H$_2$CO, CS, and CN emission toward a prototypical Class I source" (Introduction)
- Target **DG Tau B**: coordinates R.A.=04:27:02.574, Dec=26' 30''.22 (as printed)  
  > "assuming a distance of 140 pc (see Appendix [6](#Distance_DGTauB)), translates into a physical scale of 150 au." (3.1 Dust emission); "In this work, without better constraints, we assume the distance to DG Tau B to be 140 pc." (Distance to DG Tau B); z/distance 140 pc  
  > "assuming a distance of 140 pc (see Appendix [6](#Distance_DGTauB)), translates into a physical scale of 150 au." (3.1 Dust emission); "In this work, without better constraints, we assume the distance to DG Tau B to be 140 pc." (Distance to DG Tau B); distance from assumed from Gaia distance of V* FV Tau/c, which has a proper motion similar to DG Tau B  
  > "assuming a distance of 140 pc (see Appendix [6](#Distance_DGTauB)), translates into a physical scale of 150 au." (3.1 Dust emission); "In this work, without better constraints, we assume the distance to DG Tau B to be 140 pc." (Distance to DG Tau B)

## Data provenance

- ALMA projects: 2016.1.00846.S
- bands: Band 6 (1.27 mm continuum at 235 GHz)  
  > "new high-resolution ($\sim$0.15$''$, i.e., 20 au) Band 6 observations" (Conclusions); "The continuum emission of DG Tau B at 235 GHz (1.27 mm)" (3.1 Dust emission)
- frequencies and spectral setup: 12 spectral windows of 0.122 MHz resolution covering 12 transitions of 6 molecules, plus one 1.875 GHz continuum SPW including CS  
  > "The correlator setup included 12 high-resolution (0.122 MHz) spectral windows (SPWs) covering 12 molecular transitions of six molecules" (2 Observations and data reduction)
- continuum bandwidth: 1.875 GHz  
  > "plus one 1.875 GHz broad SPW for continuum emission (and including a strong CS spectral line)" (2 Observations and data reduction)
- arrays: _not stated_
- configurations: extended configuration  
  > "in an extended configuration with baselines ranging from 17 m to 3.7 km" (2 Observations and data reduction)
- baselines: 17 m to 3.7 km  
  > "baselines ranging from 17 m to 3.7 km" (2 Observations and data reduction)
- angular resolution: ~0.14-0.17 arcsec beams (Table)  
  > "| o-H$_2$CO     | $3_{1,2}-2_{1,1}$                                               | 225.697775       | 33           | 43.5          | 0.17$\times$0.14 | 1.4        | 622 $\pm$ 32  |" (Table 1)
- max recoverable scale: ~1.3 arcsec  
  > "The maximum recoverable scale is $\sim$1.3$''$." (2 Observations and data reduction)
- sensitivity: line r.m.s. 0.6-1.4 mJy/beam per 0.648 km/s channel  
  > "down to the achieved sensitivity of $\sim$1 mJy/beam" (3.5 Fluxes of detected and undetected lines)
- time on source: ~88 minutes total integration  
  > "The total integration time amounted to $\sim$88 minutes." (2 Observations and data reduction)
- observing dates: August 2017 (Cycle 4)  
  > "ALMA observations of DG Tau B were performed during Cycle 4 in August 2017" (2 Observations and data reduction)
- pi or archival as stated: _not stated_
- Line: 12CO 2-1 (230.538000 GHz)
- Line: o-H2CO 3(1,2)-2(1,1) (225.697775 GHz)
- Line: CS 5-4 (244.935556 GHz)
- Line: CN 2-1, J=5/2-3/2, F=7/2-5/2 (226.874781 GHz)
- External data: Single-dish IRAM H2CO and CN 226.87 GHz fluxes within 11'' for missing-flux comparison  
  > "(cite: Guilloteau2013) reported observations of these two lines around DG Tau B using the IRAM single-dish telescope" (3.5 Fluxes of detected and undetected lines) [from (cite: Guilloteau2013)]
- External data: Molecular parameters from the Cologne Database of Molecular Spectroscopy  
  > "adopted the molecular parameters from the Cologne Database of Molecular Spectroscopy (cite: Mueller2005)" (3.6 Column density of molecules) [from (cite: Mueller2005)]
- External data: Proper motion of DG Tau B from VLA, used for the distance argument  
  > "(cite: Rodriguez2012) determined the proper motion of DG Tau B from VLA observations at radio wavelengths" (Distance to DG Tau B) [from (cite: Rodriguez2012)]
- External data: Ortho-to-para H2CO ratio of 1.8-2.8  
  > "by assuming an ortho-to-para ratio of 1.8$-$2.8 (cite: Guzman2018)" (3.6 Column density of molecules) [from (cite: Guzman2018)]

## Processing

### Calibration

- pipeline or manual: ALMA pipeline  
  > "Data reduction was carried out following standard procedures using the ALMA pipeline in CASA 4.7.2." (2 Observations and data reduction)
- casa version: CASA 4.7.2  
  > "using the ALMA pipeline in CASA 4.7.2" (2 Observations and data reduction)
- pipeline version: _not stated_
- archive products used as is: _not stated_
- flux calibrator: _not stated_
- flux scale uncertainty: 10%  
  > "In view of the 10% uncertainty from the flux calibration" (3.5 Fluxes of detected and undetected lines)
- self calibration: Two rounds of phase self-calibration on continuum, solint 180 s and 60 s; continuum S/N from 360 to 1400; same table applied to all SPWs  
  > "Two rounds of self-calibration were attempted with solution intervals of 180 s and 60 s." (2 Observations and data reduction); "These operations improved the S/N of the continuum image from 360 to 1400 and that of the channel maps by a representative 10%." (2 Observations and data reduction)

### Imaging

- task: TCLEAN, interactive  
  > "Continuum images and spectral cubes were produced using TCLEAN interactively, applying a manually selected mask" (2 Observations and data reduction)
- deconvolver: _not stated_
- weighting robust: Briggs weighting of 2.0 for line cubes  
  > "we used Briggs weighting of 2.0 to give more weight to the short baselines" (2 Observations and data reduction)
- uv taper: _not stated_
- cell size: _not stated_
- image size: _not stated_
- masking: manually selected mask; cleaning halted when residuals showed no more source emission  
  > "halting the procedure when the visual inspection of the residuals revealed no more source emission" (2 Observations and data reduction)
- multiscale scales: _not stated_
- continuum subtraction: line SPWs continuum-subtracted  
  > "applying the phase-solutions to the continuum-subtracted line SPWs" (2 Observations and data reduction)
- line free channels: _not stated_
- primary beam correction: _not stated_
- array combination: _not stated_
- smoothing: channel width 0.648 km/s  
  > "set a channel width of 0.648 km s$^{-1}$ to improve the S/N in a single channel" (2 Observations and data reduction)
- final beam: 0.14x0.11 to 0.17x0.14 arcsec (per line)  
  > "| 0.14$\times$0.11 | 1.2        |" (Table 1)
- final rms: r.m.s. measured from a large area in line-free channels; 0.6-1.4 mJy/beam  
  > "The r.m.s. was determined from a large area in map, in the spectral channels without detectable line emission." (2 Observations and data reduction)

### Inherited from earlier work

- Column density estimation procedure  
  > "following the procedure described by (cite: Podio2019), we estimated the disk-integrated column density from the line flux integrated on the line emitting area" (3.6 Column density of molecules) [from (cite: Podio2019)]
- LTE and optically thin emission assumption  
  > "We assumed local thermodynamic equilibrium and optically thin emission (cite: Bianchi2017)" (3.6 Column density of molecules) [from (cite: Bianchi2017)]
- Geometry method for emitting layer height  
  > "we followed a technique commonly used by the near-IR community (cite: deBoer2016; Avenhaus2018)" (3.4 Radial distribution of dust and gas emission) [from (cite: deBoer2016; Avenhaus2018)]

### Not stated but needed to reproduce (our reading)

- Number of channels, cell size, image size and clean threshold
- Self-calibration reference antenna, line-free channel ranges and gain-solution mode
- Exact continuum-subtraction channels and the continuum-image Briggs robust
- Details of the unsharp-mask parameters
- Radial-profile bin widths and how the 3-sigma and isophote levels were set
- Which pipeline/archive products were used as the starting point
- Primary-beam correction treatment

## Analysis recipe

1. **Calibrate and self-calibrate**: ALMA pipeline, then phase self-calibration on continuum applied to line SPWs  
  > "Self-calibration was performed on the DG Tau B continuum emission, by combining a selection of line-free channels" (2 Observations and data reduction)
   - software: CASA
   - parameter: solint 180 s and 60 s  
  > "Two rounds of self-calibration were attempted with solution intervals of 180 s and 60 s." (2 Observations and data reduction)
   - fitting: _not stated_
   - validation: S/N improved from 360 to 1400  
  > "improved the S/N of the continuum image from 360 to 1400" (2 Observations and data reduction)
2. **Image continuum and line cubes, make moment maps**: TCLEAN cubes; moment 0/1 from selected velocity ranges; moment 1 clipped below 3 sigma  
  > "Moment 1 maps are obtained by clipping fluxes below 3$\sigma$." (2 Observations and data reduction)
   - software: CASA tclean
   - parameter: V=3.4-9.4 km/s (CO: 2.8-5.8 and 7.0-12.4 km/s)  
  > "obtained from channels with $V=3.4-9.4$ km s$^{-1}$, except CO from channels with $V=2.8-5.8$ km s$^{-1}$ and $V=7.0-12.4$ km s$^{-1}$" (2 Observations and data reduction)
   - fitting: _not stated_
   - validation: _not stated_
3. **Derive continuum geometry and extent**: Gaussian fit to continuum for PA and inclination; unsharp masking for substructure  
  > "A Gaussian fit to this signal yields a position angle P.A.=23.7 east of north and inclination $i=62.3\degree$." (3.1 Dust emission)
   - assumption: distance 140 pc  
  > "assuming a distance of 140 pc" (3.1 Dust emission)
   - fitting: _not stated_
   - validation: _not stated_
4. **Disk extinction optical depth from the occulted outflow**: tau_ext = ln(I_outflow/I_obs) using plateau of outflow-edge radial profiles as unattenuated emission  
  > "we converted the measured intensity $I_{\rm obs}$ into the extinction optical depth $\tau_{\rm ext}$ through $\tau_{\rm ext} = \ln (I_{\rm outflow}/I_{\rm obs})$." (3.3 Optical depth of continuum emission)
   - assumption: Flat profile beyond 0.3 arcsec is the unattenuated emission  
  > "Both profiles are rather flat from 0.3$''$ outward, and we assumed the values of those plateaus as the unattenuated emission" (3.3 Optical depth of continuum emission)
   - fitting: _not stated_
   - validation: Two outflow edges give nearly identical tau inside 0.4 arcsec  
  > "the values of $\tau_{\rm ext}$ constrained from the two outflow edges are nearly identical inside 0.4$''$" (3.3 Optical depth of continuum emission)
5. **Radial profiles and emitting layer height**: Azimuthal averages using continuum geometry; projected rings raised above midplane matched to observed shift  
  > "We superimposed the shape of projected circular rings, varying their different vertical locations until the match with the observed shift between molecular and continuum emission was reached." (3.4 Radial distribution of dust and gas emission)
   - parameter: 12 deg emitting-layer angle for H2CO, CS (and adopted for CN)  
  > "this exercise yielded an angle between emitting layer and midplane of 12$\degree$, corresponding to a disk scale height of 23 au at a separation of 100 au." (3.4 Radial distribution of dust and gas emission)
   - fitting: _not stated_
   - validation: _not stated_
6. **Line fluxes and missing-flux check**: Integrate flux over 0.3-2.0 arcsec (CN 0.8-2.5 arcsec); compare 11''x11'' flux with IRAM single-dish  
  > "integrating only the flux between 0.3$''$ and 2.0$''$ (referred to as the main region)" (3.5 Fluxes of detected and undetected lines)
   - fitting: _not stated_
   - validation: Interferometric fluxes 20% and 30% below single dish, within moderate missing flux given 10% calibration  
  > "the amount of missing flux may be moderate" (3.5 Fluxes of detected and undetected lines)
7. **Column densities and upper limits**: Disk-integrated column density from line flux assuming LTE, optically thin, with global Tex of 30-300 K  
  > "we adopted a global value of the molecular excitation temperature throughout the disk, leaving this parameter spanning from 30 to 300 K." (3.6 Column density of molecules)
   - assumption: o/p H2CO 1.8-2.8  
  > "assuming an ortho-to-para ratio of 1.8$-$2.8 (cite: Guzman2018)" (3.6 Column density of molecules)
   - fitting: _not stated_
   - validation: _not stated_

## Software

- **CASA** 4.7.2: ALMA pipeline calibration, self-calibration, imaging  
  > "using the ALMA pipeline in CASA 4.7.2" (2 Observations and data reduction)
- **TCLEAN** : continuum images and spectral cubes  
  > "Continuum images and spectral cubes were produced using TCLEAN interactively" (2 Observations and data reduction)

## Numeric results

| quantity | value | uncertainty | units | step | quote |
|---|---|---|---|---|---|
| Continuum position angle | 23.7 | not stated | deg east of north | 3 | yields a position angle P.A.=23.7 east of north and inclination $i=62.3\degree$ |
| Disk inclination | 62.3 | not stated | deg | 3 | inclination $i=62.3\degree$ |
| Radius enclosing 90% of continuum flux | 1.06 arcsec (150 au) | not stated | arcsec | 3 | The separation encompassing 90% of the total flux is 1.06$''$. |
| Radius where extinction optical depth approaches unity at 1.3 mm | 0.35 arcsec (~50 au) | not stated | arcsec | 4 | the total extinction optical depth at 1.3 mm approaches unity at 0.35$''$ |
| H2CO/CS emitting layer angle | 12 | not stated | deg | 5 | an angle between emitting layer and midplane of 12$\degree$, corresponding to a disk scale height of 23 au at a separation of 100 au |
| H2CO flux in 11''x11'' | 1.25 | not stated | Jy km/s | 6 | We found an H$_2$CO flux of 1.25 Jy km s$^{-1}$ and CN flux of 0.93 Jy km s$^{-1}$. |
| CN flux in 11''x11'' | 0.93 | not stated | Jy km/s | 6 | CN flux of 0.93 Jy km s$^{-1}$ |
| CS 5-4 integrated flux | 920 | 14 | mJy km/s | 6 | / CS            / 5$-$4                                                           / 244.935556       / 35           / 19.1          / 0.16$\times$0.13 / 0.6        / 920 $\pm$ 14  / |
| o-H2CO integrated flux | 622 | 32 | mJy km/s | 6 | / 0.17$\times$0.14 / 1.4        / 622 $\pm$ 32  / |
| Total H2CO column density | (0.4-4.6)e14 | range over Tex 30-300 K | cm^-2 | 7 | resulting in a value of $N_{\rm H_2CO}=(0.4-4.6)\cdot10^{14}$ cm$^{-2}$ |
| CH3OH/H2CO ratio upper limit | <1.5-2.3 | depends on Tex | dimensionless | 7 | we then inferred a CH$_3$OH/H$_2$CO ratio \< 1.5 $-$ 2.3 (depending on $T_{\rm ex}$) |

## Qualitative findings

- CS and H2CO have nearly identical radial profiles in the inner 200 au, whereas CN is absent between 50 and 150 au, suggesting a ring-like CN distribution  
  > "Unlike H$_2$CO and CS, no CN emission is detected between 50 au and 150 au." (3.4 Radial distribution of dust and gas emission)
- CS, CN and faint H2CO are seen only in the blueshifted outflow  
  > "Strong CS and CN emission as well as faint H$_2$CO emission is detected from the blueshifted outflow only." (Conclusions)

## Claim tuples

- H: Is the inner gas depression due to optically thick dust continuum? | E: Extinction from the occulted CO outflow compared with the radius where line emission disappears | R: tau~1 at 0.35 arcsec; no line detected inside 50 au | F: The inner ~50 au is optically thick at 1.3 mm and saturated continuum hides line emission | **supported**
- H: Does the dust disk host substructure? | E: Unsharp-masked continuum image and radial profile | R: Shallow rings (20-30% deviations), broad ring at 140 au, marginal leading spiral | F: Shallow substructures exist in a Class I disk | **partially**
- H: Do H2CO, CS and CN trace the same regions? | E: Moment maps and azimuthally averaged radial profiles | R: CS and H2CO similar; CN differs | F: CN likely emitted in a ring and from the disk back side | **supported**
- H: Can H2CO formation route be determined? | E: Radial H2CO profile | R: Inner 50 au not traced | F: Cannot conclude gas-phase versus grain formation | **refuted**

## Reasoning

- Why this data: _not stated_
- Why this method: _not stated_
- Alternative: Inner depression as gas drop, chemistry or continuum absorption alone; negative fluxes imply foreground cloud absorption plus optically thick continuum  
  > "The presence of negative values implies that the continuum absorption from foreground material is at least contributing to this inner depression." (4.1 Origin of the inner depression)
- How they decided it was enough: _not stated_
- Limitation (authors): Poor knowledge of gas temperature and density prevents column density profiles  
  > "Our poor knowledge of the gas temperature and density profile does not allow us to convert the line intensity profile into a column density profile." (3.6 Column density of molecules)
- Limitation (authors): Distance to DG Tau B is unconstrained  
  > "The distance to DG Tau B is unconstrained because its embedded nature impedes the measurement of its parallax in the visible." (Distance to DG Tau B)
- Caveat (inferred, ours): Distance of 140 pc is indirect and could be 120 pc, rescaling all au quantities
- Caveat (inferred, ours): Column densities depend on an assumed global Tex over a 10x range
- Caveat (inferred, ours): Spiral arm is only marginal
- Caveat (inferred, ours): Radial profiles mix disk and outflow emission
- Caveat (inferred, ours): Single-epoch single-configuration data with a 1.3 arcsec recoverable scale and 20-30% missing flux

## Reproducibility

- Data public (paper): Project 2016.1.00846.S cited; public status not stated  
  > "This paper uses ALMA data from project 2016.1.00846.S." (Acknowledgements)
- Products in archive: _not stated_
- Missing: Clean threshold, cell and image size, continuum robust
- Missing: Mask definitions and line-free channels
- Missing: Exact flux integration apertures and radial profile binning
- Missing: Unsharp mask parameters
- Data volume (inferred): ~50-100 GB raw visibilities
- Score (inferred): 3/5, Standard pipeline plus self-cal and clear analysis, but many imaging parameters are unstated and the analysis is mostly morphological.
- Rediscovery candidate: no, Key results are largely morphological and imaging parameters are incomplete, though the data are likely in the public archive.

## Links

- Method: (cite: Podio2019) (Column density procedure and the pilot ALMA-DOT analysis of DG Tau)
- Method: (cite: Cazzoletti2018) (CN ring models used for interpretation)
- Companion: (cite: deValon2020) (High-resolution CO imaging of DG Tau B)
- Companion: (cite: Guilloteau2013) (IRAM single-dish fluxes and CN hyperfine structure)
- Related: ALMA-DOT

## Checks

```json
{
 "quotes": 82,
 "quotes_ok": 82,
 "quote_pass_rate": 1.0,
 "quotes_too_long": 0,
 "unsupported_facts": 0,
 "project_codes": 1,
 "codes_not_in_text": [],
 "codes_not_in_obscore": [],
 "obscore_codes_not_in_card": [],
 "codes_printed_but_missing": [],
 "numeric_results": 11,
 "numeric_problems": 0,
 "fill": {
  "facts": 84,
  "stated": 56,
  "rate": 0.667
 },
 "evidence_ok": true
}
```
