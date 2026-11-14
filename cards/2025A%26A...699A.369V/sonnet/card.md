# Dense clumps survive in the vicinity of R136 in 30 Doradus

`2025A&A...699A.369V` | Astronomy and Astrophysics 2025 | first author: Valdivia-Mena, M. T. | arXiv: 2506.01390 | DOI: 10.1051/0004-6361/202554327

Card schema 1.0 | model claude-sonnet-5-5 | depth full | type observational_alma_primary

## Science

- Fields: star_formation, nearby_galaxies, milky_way_ism
- Question: Why do dense molecular clumps survive so close in projection to the massive cluster R136 in 30 Dor, and what are their physical properties?  
  > "We investigated the properties of molecular gas in the Stapler nebula to better understand why these clouds survive so close in projection to R136." (abstract)
- Target **Stapler nebula near R136, 30 Doradus (LMC)**: coordinates 05h38m39.95s, -69d05m40.33s (J2000)  
  > "The phase center of all data is $\alpha=05^h38^m39.95^s$, $\delta= -69^{\circ}05^m40.33^s$ (J2000)" (2 Observations and data reduction); "which corresponds to 1.1 pc at a distance of 50 kpc" (2 Observations and data reduction); z/distance 50 kpc  
  > "The phase center of all data is $\alpha=05^h38^m39.95^s$, $\delta= -69^{\circ}05^m40.33^s$ (J2000)" (2 Observations and data reduction); "which corresponds to 1.1 pc at a distance of 50 kpc" (2 Observations and data reduction); distance from Pietrzynski2013  
  > "The phase center of all data is $\alpha=05^h38^m39.95^s$, $\delta= -69^{\circ}05^m40.33^s$ (J2000)" (2 Observations and data reduction); "which corresponds to 1.1 pc at a distance of 50 kpc" (2 Observations and data reduction)

## Data provenance

- ALMA projects: 2017.1.00368.S
- bands: Band 7 (345 GHz), two correlator setups  
  > "The observations consist of two Band 7 correlator setups." (2 Observations and data reduction)
- frequencies and spectral setup: _not stated_
- continuum bandwidth: 13.5 GHz total, centered 338.5 GHz (0.88 mm)  
  > "It has a central frequency of 338.5 GHz (0.88 mm), a total bandwidth of 13.5 GHz" (2 Observations and data reduction)
- arrays: 7m ACA (Morita array), Cycle 5  
  > "during Cycle 5, using the 7m ALMA Compact Array (ACA, also known as the Morita array)" (2 Observations and data reduction)
- configurations: _not stated_
- baselines: _not stated_
- angular resolution: ~4.7'' (1.1 pc)  
  > "The spatial resolution is approximately 4.7$''$ for all cubes, which corresponds to 1.1 pc at a distance of 50 kpc." (2 Observations and data reduction)
- max recoverable scale: 19.1'' (4.6 pc) setup 1; 18.6'' (4.5 pc) setup 2  
  > "The maximum recoverable scale (MRS) for the first setup is 19.1$''$ (4.6 pc) and for the second setup is 18.6$''$ (4.5 pc)." (2 Observations and data reduction)
- sensitivity: continuum rms 4 mJy/beam; line rms 26-51 mK  
  > "a pixel size of 0.7$''$, and an RMS of 4 m$\rm Jy\,beam^{-1}$." (2 Observations and data reduction)
- time on source: _not stated_
- observing dates: _not stated_
- pi or archival as stated: PI M. Rubio  
  > "under project 2017.1.00368.S (PI M. Rubio)" (2 Observations and data reduction)
- Line: 12CO J=3-2 (345.796 GHz)
- Line: 13CO J=3-2 (330.587 GHz)
- Line: CS J=7-6 (342.883 GHz)
- Line: HCO+ J=4-3 (356.734 GHz)
- Line: HCN J=4-3 (354.505 GHz)
- Other facility **CTIO 1.5 m telescope**: Brgamma image used to estimate free-free emission  
  > "using a Br$\gamma$ emission image obtained with the 1.5 m telescope in Cerro Tololo Observatory (M. Rubio, priv. comm.)" (4.4.1 Free-free emission near R136)
- External data: 12CO 3-2/1-0 line ratio ~2  
  > "using a line ratio $R_{\frac{3-2}{1-0}}\sim2$, as determined by (cite: johansson1998) for the 30Dor-10 cloud" (4.1) [from (cite: johansson1998)]
- External data: alpha_CO = 8.4±3.0 Msun pc-2 (K km/s)-1  
  > "We used $\alpha_{^{12}CO}=8.4\pm3.0$ M$_{\odot}$ pc$^{-2}$ (K km s$^{-1}$)$^{-1}$, obtained toward the 30Dor-10 cloud by (cite: indebetouw2013)" (4.1) [from (cite: indebetouw2013)]
- External data: dust opacity kappa(870um)=1.26±0.02 cm2/g  
  > "such that $\kappa(870\mu m)=1.26\pm0.02$ cm$^2$ g$^{-1}$, found by (cite: bot2010)" (4.4.2) [from (cite: bot2010)]
- External data: Td = 40 K  
  > "We assumed a dust temperature $T_d = 40$ K, based on the dust temperatures obtained for this region in (cite: Tram2021)." (4.4.2) [from (cite: Tram2021)]
- External data: [H2/13CO]=1.8e6  
  > "which we assumed to be $1.8\times10^6$ (cite: garay2002; heikkila1999)" (4.2) [from (cite: garay2002; heikkila1999)]

## Processing

### Calibration

- pipeline or manual: CASA pipeline with standard OSF scripts  
  > "using the standard scripts provided by ALMA Operations Support Facility (OSF) with the delivered raw data" (2 Observations and data reduction)
- casa version: CASA v.5.6.1 (imaging)  
  > "Imaging was performed in CASA v.5.6.1." (2 Observations and data reduction)
- pipeline version: CASA Pipeline v.5.4.0.70  
  > "We obtained the calibrated data using the Common Astronomy Software Applications package (CASA) Pipeline v.5.4.0.70" (2 Observations and data reduction)
- archive products used as is: _not stated_
- flux calibrator: _not stated_
- flux scale uncertainty: _not stated_
- self calibration: _not stated_

### Imaging

- task: uvcontsub then tclean  
  > "Then we used the `tclean` task to deconvolve and clean the data cubes." (2 Observations and data reduction)
- deconvolver: Hogbom CLEAN (lines); MFS for continuum  
  > "We used the Hogbom CLEAN algorithm with manually-applied masking" (2 Observations and data reduction)
- weighting robust: Briggs, robust 0.5 (lines); natural (continuum)  
  > "We deconvolved with Briggs weighting using a robust parameter of 0.5." (2 Observations and data reduction)
- uv taper: _not stated_
- cell size: 0.7''  
  > "a pixel size of 0.7$''$" (2 Observations and data reduction)
- image size: _not stated_
- masking: manual masks  
  > "We do an interactive Hogbom CLEAN to apply a manual mask to the dirty image." (2 Observations and data reduction)
- multiscale scales: _not stated_
- continuum subtraction: 0th order fit to line-free channels  
  > "via a 0th order fit to line-free channels" (2 Observations and data reduction)
- line free channels: _not stated_
- primary beam correction: each channel divided by tclean primary beam response  
  > "In the case of the line cubes, each channel was divided by the primary beam response." (2 Observations and data reduction)
- array combination: _not stated_
- smoothing: _not stated_
- final beam: continuum 4.7''x3.9'' PA 69 deg; line beams in Table 1  
  > "a resolution of 4.7$''$ $\times$ 3.9$''$ (position angle of 69$^{\circ}$)" (2 Observations and data reduction)
- final rms: _not stated_

### Inherited from earlier work

- CPROPS algorithm and bias corrections (Eq. 9, 10)  
  > "using Equations 9 and 10 from (cite: rosolowsky2006)" (4.1) [from (cite: rosolowsky2006)]
- LTE equations for 12CO/13CO 3-2  
  > "we used the equations specific for $^{12}$CO $J=3-2$ and $^{13}$CO $J=3-2$ molecular line emissions given in (cite: celispena2019)." (4.2) [from (cite: celispena2019)]
- Clump terminology  
  > "Following the terminology used in (cite: Wong2022-30Dorclumps), we refer to the individual structures as clumps" (3 Clump identification methods) [from (cite: Wong2022-30Dorclumps)]

### Not stated but needed to reproduce (our reading)

- Line-free channel ranges used for uvcontsub
- Clean thresholds, iterations and mask definitions
- Number of execution blocks, observing dates, integration time
- Flux, bandpass and phase calibrators and flux accuracy
- Free-free image (Brgamma) is private communication
- Exact Gaussian-fitting starting parameters and spectral ranges
- Extrapolation settings of CPROPS beyond those listed

## Analysis recipe

1. **Image line cubes and continuum**: uvcontsub, tclean with Briggs robust 0.5 for lines; MFS natural weighting for combined continuum; primary-beam correction  
  > "We deconvolved the concatenated data using multi-frequency synthesis, implemented in the `tclean` task, with natural weight." (2 Observations and data reduction)
   - software: CASA
   - fitting: _not stated_
   - validation: _not stated_
2. **Identify clumps in line cubes**: CPROPS (ECLUMP) on 12CO, then other lines with same parameters; manual rejection of sidelobe artifacts; Gaussian fitting for blended clumps  
  > "We use the ECLUMP variation of the CPROPS algorithm" (3.1)
   - software: CPROPS, astropy
   - parameter: THRESH=3sigma, EDGE=1.5sigma, MINAREA=0.5 beams, MINPEAK=3sigma, MINVCHAN=3, BOOTSTRAP=1000, /NONUNIFORM  
  > "We set the parameters THRESH $=3\sigma$ and EDGE $=1.5\sigma$" (3.1)
   - fitting: _not stated_
   - validation: manual inspection for sidelobe false detections  
  > "We manually inspected the results for the $^{12}$CO detections by CPROPS to check for false clumps caused by artifacts" (3.1)
3. **Derive 12CO clump properties and masses**: Resolution-corrected radii and luminosity; virial mass 190 dv^2 R; M_gas^CO = alpha_CO L_CO(1-0)  
  > "$$M_{vir}=190(\Delta v)^2R" (4.1)
   - software: CPROPS
   - assumption: D=50 kpc; alpha_CO=8.4; R32/10~2; density profile r^-1  
  > "assuming a distance to 30 Dor of $D=50$ kpc (cite: Pietrzynski2013)" (4.1)
   - fitting: _not stated_
   - validation: compared with Solomon 1987 relation  
  > "together with the relation between these properties found for Molecular Clouds in the first quadrant of the Milky Way by (cite: solomon1987)" (4.1)
4. **LTE column density and mass from 12CO and 13CO**: Tex from optically thick 12CO peak; 13CO optical depth and column density; N(H2)=[H2/13CO]N(13CO); mass with mu=2.72  
  > "First, we assumed that the excitation temperature for $^{13}$CO is the same than for $^{12}$CO, and that the $^{12}$CO emission is optically thick." (4.2)
   - assumption: [H2/13CO]=1.8e6; beam filling factor ~1; TBG=2.73 K  
  > "which we assumed to be $1.8\times10^6$ (cite: garay2002; heikkila1999)" (4.2)
   - fitting: _not stated_
   - validation: 13CO tau<1 confirmed (0.1-0.4)  
  > "The resulting $\tau^{13CO}$ are all lower than 1, between 0.1 and 0.4" (4.2)
5. **Integrated line intensities and ratios**: Gaussian1D fit to peak-position spectra, integrate fit; ratios relative to 13CO  
  > "We first fit a Gaussian profile to the spectra using the `astropy.models.Gaussian1D` module." (4.3)
   - software: astropy
   - fitting: Gaussian profiles, 1-2 components  
  > "For clumps no. 8 and no. 18, which are the clumps manually characterized in Sect. [\[sec:cpropssecondstep\]](#sec:cpropssecondstep), the detected molecules were fit with two Gaussian components" (Integrated line intensities for different molecular species)
   - validation: _not stated_
6. **Continuum source photometry and free-free subtraction**: 3sigma sources, 1.5sigma contour area, aperture photometry with background subtraction; Brgamma->Halpha->free-free scaled to 338.5 GHz and subtracted  
  > "We determined the free-free emission towards each clump through aperture photometry." (4.4.1)
   - software: astropy.modelling
   - assumption: Te=1e4 K, He+/H+~0.08, Halpha/Brgamma=101.78  
  > "We used $T_e=10^4$ K and $n(He^{+})/n(H^{+})\sim0.08$" (4.4.1)
   - fitting: two elliptical Gaussians for B and D  
  > "so to determine their area, we modeled the emission from both clumps as two elliptical Gaussians." (Clump identification in continuum emission)
   - validation: _not stated_
7. **Gas mass from dust**: Optically thin M=S D^2/(kappa x_d B(Td))  
  > "assuming dust emission is optically thin at 0.88 mm" (4.4.2)
   - assumption: Td=40 K, kappa(880um)=1.23 cm2/g, beta=2, dust-to-gas 3.5e-3  
  > "$x_d(LMC)=0.5x_d(\odot)=3.5\times10^{-3}$" (4.4.2)
   - fitting: _not stated_
   - validation: compared with CO and virial masses in same areas  
  > "To perform this comparison we needed to calculate the mass using the same clump areas on all cases." (Gas masses obtained through CO and dust emission)

## Software

- **CASA** 5.4.0.70 pipeline; 5.6.1 imaging: calibration and imaging  
  > "Imaging was performed in CASA v.5.6.1." (2 Observations and data reduction)
- **CPROPS (IDL)** : clump identification and properties  
  > "We used the IDL implementation of CPROPS" (3.1)
- **astropy** : Gaussian fitting and modelling  
  > "We used the `astropy.modelling` package to find the best fit for this region of the image." (4.4.1)

## Numeric results

| quantity | value | uncertainty | units | step | quote |
|---|---|---|---|---|---|
| Number of 12CO clumps | 24 | not stated | clumps | 2 | The final catalog of $^{12}$CO clumps consists of 24 sources |
| Continuum free-free fraction at 0.88 mm | 50-85 | not stated | percent | 6 | These values represent between 50 and 85% of the total 0.88 mm flux measured in the ALMA images |
| Excitation temperature of clump 2 | 33.39 | ±0.06 | K | 4 | / 2 / $33.39\pm0.06$ / $0.38\pm0.00$ / $13.2\pm1.3$ / $23.7\pm2.4$ |
| LTE gas mass range | 203-1148 | not stated | Msun | 4 | The total gas masses $M^{LTE}_{gas}$ range between 203 and 1148 M$_{\odot}$. |
| Gas mass from dust of B+D | 924 | ±520 | Msun | 7 | we obtained a gas mass $M_{gas}^{dust}=924\pm520$ M$_{\odot}$ for sources B and D together |
| Virial mass of clump 2 | 2414.2 | ±382.2 | Msun | 3 | / 2 / $268.56\pm22.11$ / $0.71\pm0.10$ / $2414.2\pm382.2$ / $1128.0\pm413.4$ |

## Qualitative findings

- Densest clumps (all species detected) lie along the NW-SE dark lane; clumps coincide with YSOs at the map center  
  > "are concentrated in a northwest-southeast diagonal seen as a dark dust lane in HST images" (abstract)

## Claim tuples

- H: Dense molecular clumps near R136 are resolved into parsec-scale clumps | E: CPROPS on ALMA ACA 12CO 3-2 cube | R: 24 clumps, mostly unresolved, radii 0.1-0.9 pc | F: Stapler nebula resolves into sub-parsec to parsec clumps | **supported**
- H: Virial and CO/dust masses agree | E: Compare Mvir, CO mass, dust mass in same areas | R: Mvir 2-5 times dust mass; CO and dust masses similar | F: velocity dispersion reflects external pressure plus self-gravity | **partially**
- H: Clump properties resemble other 30 Dor/LMC clumps | E: Compare line ratios, Tex, column densities with literature | R: Similar ratios and turbulence | F: Clumps are densest parts of a cloud carved by R136 | **supported**

## Reasoning

- Why this data: _not stated_
- Why this method: _not stated_
- How they decided it was enough: _not stated_
- Limitation (authors): Most clumps unresolved; missing extended flux without Total Power data; non-LTE modeling out of scope  
  > "Total Power (TP) observations would be necessary to detect extended continuum emission." (5.4)
- Caveat (inferred, ours): Free-free estimate relies on non-public Brgamma image with assumed Te and line ratio
- Caveat (inferred, ours): Dust masses have uncertainties comparable to values
- Caveat (inferred, ours): Virial masses are upper limits for unresolved clumps
- Caveat (inferred, ours): Fixed alpha_CO and uniform Td=40 K assumed

## Reproducibility

- Data public (paper): Project code given and acknowledged; public status not explicitly stated  
  > "This paper makes use of the following ALMA data: ADS/JAO.ALMA#2017.1.00368.S." (Acknowledgements)
- Products in archive: _not stated_
- Missing: Brgamma CTIO image (private communication)
- Missing: line-free channel selection and clean thresholds
- Missing: manual masks
- Data volume (inferred): ~10-50 GB (ACA, two setups)
- Score (inferred): 6/5, Clear CPROPS parameters and equations, but manual masks, line-free channels and private Brgamma image limit exact reproduction.
- Rediscovery candidate: no, Free-free correction needs a private image and manual steps, though ALMA data are archival.

## Links

- Method: (cite: rosolowsky2006) (CPROPS algorithm)
- Method: (cite: celispena2019) (LTE equations)
- Companion: (cite: kalari2018) (earlier SEST CO 2-1 study of the Stapler nebula knots)
- Companion: (cite: Wong2022-30Dorclumps) (30 Dor clump catalog compared)
- Related: ATLASGAL
- Related: CHIMPS

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
 "numeric_results": 6,
 "numeric_problems": 0,
 "fill": {
  "facts": 83,
  "stated": 55,
  "rate": 0.663
 },
 "evidence_ok": true
}
```
