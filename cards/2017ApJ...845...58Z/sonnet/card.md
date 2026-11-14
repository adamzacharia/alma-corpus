# ALMA Maps of Dust and Warm Dense Gas Emission in the Starburst Galaxy IC 5179

`2017ApJ...845...58Z` | The Astrophysical Journal 2017 | first author: Zhao, Yinghe | arXiv: 1707.04363 | DOI: 10.3847/1538-4357/aa7ff8

Card schema 1.0 | model claude-sonnet-5-5 | depth full | type observational_alma_primary

## Science

- Fields: nearby_galaxies
- Question: How do warm dense gas (CO 6-5) and dust continuum emission compare, and what is the nuclear gas kinematics, at ~34 pc resolution in the starburst LIRG IC 5179?  
  > "In order to study the properties of warm molecular gas and cold dust, and their relations to star formation in more details, we have initiated a multi-cycle ALMA program" (Introduction)
- Target **IC 5179**: coordinates 22:16:09.10 -36:50:37.4 (J2000)  
  > "| IC 5179       | 22:16:09.10  | $-$36:50:37.4       | 51.4          | 3422          | SA(rs)bc      | Starburst     | 11.24         |" (Table 1); "At its distance (angular size distance) of 50.2 Mpc, 1$''$ corresponds to 244 pc." (Introduction); z/distance D_L = 51.4 Mpc; cz = 3422 km/s  
  > "| IC 5179       | 22:16:09.10  | $-$36:50:37.4       | 51.4          | 3422          | SA(rs)bc      | Starburst     | 11.24         |" (Table 1); "At its distance (angular size distance) of 50.2 Mpc, 1$''$ corresponds to 244 pc." (Introduction); distance from Table 1 (cz from NED; D_A = D_L/(1+z)^2)  
  > "| IC 5179       | 22:16:09.10  | $-$36:50:37.4       | 51.4          | 3422          | SA(rs)bc      | Starburst     | 11.24         |" (Table 1); "At its distance (angular size distance) of 50.2 Mpc, 1$''$ corresponds to 244 pc." (Introduction)

## Data provenance

- ALMA projects: 2013.1.00524.S, 2015.1.00385.S
- bands: Band 9  
  > "were conducted using the Band 9 receivers of ALMA in the time division mode" (2 Observations and Data Reduction)
- frequencies and spectral setup: 4 SPWs centered at ~683.6, 685.4, 679.9, 681.8 GHz, ~2 GHz each; ~6.8 km/s velocity resolution  
  > "were centered at the sky frequencies of $\sim$683.6, 685.4, 679.9, and 681.8 GHz, respectively, each with a bandwidth of about 2 GHz" (2 Observations and Data Reduction)
- continuum bandwidth: _not stated_
- arrays: 12-m antennae  
  > "using up to 32, 37 and 42 12-m antennae" (2 Observations and Data Reduction)
- configurations: C34-5 and C36-4  
  > "the relatively extended configurations C34-5 and C36-4" (2 Observations and Data Reduction)
- baselines: _not stated_
- angular resolution: ~0.15" x 0.13" (37 x 32 pc), PA -69 deg  
  > "with the full width of half maximum (FWHM) of $\sim$$0^{\prime\prime}.15\times0^{\prime\prime}.13$, corresponding to physical scales of 37 pc$\times$32 pc" (2 Observations and Data Reduction)
- max recoverable scale: ~2.1 arcsec  
  > "the maximum recoverable scale is $\sim$$2^{\prime\prime}.1$" (2 Observations and Data Reduction)
- sensitivity: channel rms 3.3-4.0 mJy/beam (14 km/s); continuum 0.4 mJy/beam; moment-0 0.46 Jy km/s/beam  
  > "For the continuum, the $1\sigma$ rms noise is about 0.4 mJy beam$^{-1}$" (2 Observations and Data Reduction)
- time on source: ~101 minutes total  
  > "The total on-source integration time was $\sim$101 minutes." (2 Observations and Data Reduction)
- observing dates: 2014/07/26, 2015/06/07, 2016/06/18  
  > "| X87b480_Xb68  | 2014/07/26   | 03:10:59$-$04:48:15 | C34-5         | 27            | 820           | 39.44         | $637-752$     |" (Table 1)
- pi or archival as stated: PI N. Lu; the authors' own multi-cycle program  
  > "Cycle-3, Program ID: 2015.1.00385.S, PI: N. Lu" (2 Observations and Data Reduction)
- Line: CO J=6-5 (691.473 GHz)
- Other facility **Herschel SPIRE FTS/photometry**: Total CO(6-5) flux and 350/500 um photometry for fractions recovered  
  > "By interpolating the *Herschel* SPIRE photometric measurements at 350 and 500 $\mu$m, we estimated that the total flux density at 434 $\mu$m is 3.01 Jy" (3.2 Continuum Emission at 434 um)
- Other facility **HST**: Pa-alpha image (0.18") for comparison  
  > "The Pa-$\alpha$ map was obtained from a set of *HST* NIR narrow-band images (Diáz-Santos et al. 2008)." (3.4 Comparison with Pa-alpha Observations)
- External data: Herschel SPIRE/FTS CO(6-5) flux of 802±52 Jy km/s  
  > "our SPIRE/FTS-measured flux of $802\pm52$ Jy km s$^{-1}$ (Lu et al. 2017)" (3.1 CO (6-5) Line Emission) [from Lu et al. 2017]
- External data: HST Pa-alpha map and EW  
  > "*HST* Pa-$\alpha$ (Alonso-Herrero et al. 2006; Diáz-Santos et al. 2008) image" (3.4 Comparison with Pa-alpha Observations) [from Alonso-Herrero et al. 2006; Díaz-Santos et al. 2008]
- External data: Optical PA of 57 deg and axis ratio  
  > "very similar to the one measured in the optical image (57$^\circ$; Lehnert & Heckman 1995)" (3.3 Kinematics of the Nuclear Region) [from Lehnert & Heckman 1995]

## Processing

### Calibration

- pipeline or manual: _not stated_
- casa version: CASA 4.6.0  
  > "The data were reduced with CASA 4.6.0 (McMullin et al. 2007)." (2 Observations and Data Reduction)
- pipeline version: _not stated_
- archive products used as is: _not stated_
- flux calibrator: _not stated_
- flux scale uncertainty: _not stated_
- self calibration: _not stated_

### Imaging

- task: _not stated_
- deconvolver: _not stated_
- weighting robust: Briggs robust=0.5 (robust=2.0 to match Pa-alpha resolution)  
  > "cleaned using the Briggs weightings with *robust=0.5*" (2 Observations and Data Reduction)
- uv taper: outertaper=100 kλ with robust=2.0 for 0.86" beam test  
  > "$robust=2.0$ and $uv$-taper ($\mathrm{outertaper}=100 k \lambda$)" (3.1 CO (6-5) Line Emission)
- cell size: _not stated_
- image size: _not stated_
- masking: _not stated_
- multiscale scales: _not stated_
- continuum subtraction: continuum from SPWs 0-3 excluding line channels  
  > "The continuum was measured using data in SPWs 0-3 by excluding the line emission channels." (2 Observations and Data Reduction)
- line free channels: _not stated_
- primary beam correction: flux measurements on PB-corrected images; figures and noise before correction  
  > "flux measurements are based on the images after the primary beam correction, whereas all of the figures are produced using the results before the primary beam correction" (2 Observations and Data Reduction)
- array combination: three datasets combined and cleaned jointly  
  > "The calibrated datasets were combined and cleaned" (2 Observations and Data Reduction)
- smoothing: cubes binned to 14 km/s channels  
  > "we binned spectral cubes into channels with the width of $\delta v=14$ km s$^{-1}$" (2 Observations and Data Reduction)
- final beam: ~0.15" x 0.13", PA -69 deg  
  > "a position angle (P.A.; north to east) of $-69^\circ$" (2 Observations and Data Reduction)
- final rms: continuum 0.4 mJy/beam; channel 3.3-4.0 mJy/beam  
  > "The noise for these channel maps in CO (6$-$5) is in the range of $3.3-4.0$ mJy beam$^{-1}$." (2 Observations and Data Reduction)

### Inherited from earlier work

- Clump finding with the Williams et al. algorithm  
  > "Using the clump-finding algorithm of Williams et al. (1994)" (3.1 CO (6-5) Line Emission) [from Williams et al. 1994]
- Constant CO/70um ratio assumption and 70um fractional flux for the recovered-flux estimate  
  > "we assume that the CO (6$-$5) (or dust continuum at 434 $\mu$m) to the 70 micron flux ratio ($R_{{\rm CO}/70\,\mu {\rm m}}$) is constant, according to Lu et al. (2014) and Liu et al. (2015)" (3.1 CO (6-5) Line Emission) [from Lu et al. 2014; Liu et al. 2015]
- Heating interpretation of CO/dust offsets  
  > "As discussed in detail in Zhao et al. (2016b), the displacement between the dust and line emission peaks" (3.2 Continuum Emission at 434 um) [from Zhao et al. 2016b]
- Kinemetry method  
  > "(see Krajnović et al. 2006 for more details)" (3.3 Kinematics of the Nuclear Region) [from Krajnović et al. 2006]

### Not stated but needed to reproduce (our reading)

- Flux/bandpass/phase calibrators per execution and flux-scale uncertainty
- Line-free channels used for continuum
- Clean threshold, mask, niter, cell and image size
- Parameters for clump finding (contour levels, thresholds)
- Kinemetry settings (ring spacing, center and fixed parameters)
- Whether the 14 km/s channel binning was applied before the moment maps and moment masking/clipping
- Pipeline vs manual calibration

## Analysis recipe

1. **Calibrate, combine and image**: Reduce with CASA, combine three datasets, clean with Briggs weighting robust=0.5; continuum from SPWs 0-3 excluding line; cube from SPW-0  
  > "The calibrated datasets were combined and cleaned using the Briggs weightings with *robust=0.5*" (2 Observations and Data Reduction)
   - software: CASA
   - parameter: robust=0.5; 14 km/s channels  
  > "we binned spectral cubes into channels with the width of $\delta v=14$ km s$^{-1}$" (2 Observations and Data Reduction)
   - fitting: _not stated_
   - validation: Each dataset imaged separately to check quality and flux consistency  
  > "we also imaged each dataset separately to check quality and flux consistency" (2 Observations and Data Reduction)
2. **Identify CO clumps and measure fluxes**: Clump-finding by contouring at multiple levels; Gaussian fits to spectra in elliptical apertures  
  > "which performs a blind search for clumps by contouring the map at different levels to identify peaks, we identified 14 clumps" (3.1 CO (6-5) Line Emission)
   - software: Williams et al. 1994 algorithm
   - fitting: Gaussian profile for the clump spectra  
  > "obtained by fitting a Gaussian profile to the spectrum extracted within an elliptical aperture" (Table 2)
   - validation: _not stated_
3. **Estimate flux recovered vs Herschel**: Compare aperture flux to SPIRE/FTS flux scaled by fractional 70um flux in the beams, assuming constant CO/70um  
  > "our observation recovers 40% ($\equiv 0.8/0.4 \times 20\%$) of the total CO flux within the ALMA FOV" (3.1 CO (6-5) Line Emission)
   - assumption: R_CO/70um constant across scales  
  > "this missing flux is a very crude estimation since $R_{{\rm CO}/70\,\mu {\rm m}}$ may vary at physical scales of $\lesssim$kpc" (3.1 CO (6-5) Line Emission)
   - fitting: _not stated_
   - validation: Compared the integrated map with the sum of channel photometry and a coarser 0.86" beam  
  > "the measured flux is 1.4 times higher than the current value when a much larger beam ($0\ensuremath{''}.86\times0\ensuremath{''}.86$) is used" (3.1 CO (6-5) Line Emission)
4. **CO-to-dust ratio map and Pa-alpha comparison**: Ratio of CO luminosity to nu f_nu (cont), using 2 sigma where fluxes below 2 sigma; compare with HST Pa-alpha EW with matched resolution  
  > "For pixels with fluxes less than 2$\sigma$, we used the 2$\sigma$ flux to calculate the ratio." (3.2 Continuum Emission at 434 um)
   - fitting: _not stated_
   - validation: _not stated_
5. **Kinematic analysis**: P-V diagram (width 0.175", PA ~55 deg) and kinemetry of the first-moment map  
  > "which was extracted using a slice with the width of 0$''$.175 (7 pixels) and P.A. of $\sim$55$^\circ$" (3.3 Kinematics of the Nuclear Region)
   - software: kinemetry
   - assumption: inclination i = arccos q  
  > "suggesting an inclination $i=\arccos q \sim 54^\circ$" (3.3 Kinematics of the Nuclear Region)
   - fitting: Best-fitting ellipses to the first-moment map  
  > "which does surface photometry to the first moment map by determining the best-fitting ellipse" (3.3 Kinematics of the Nuclear Region)
   - validation: Kinematic PA compared with optical PA; vmax compared with the P-V diagram  
  > "The maximum $v_{\rm rot}$ is similar to that estimated from the P-V diagram" (3.3 Kinematics of the Nuclear Region)

## Software

- **CASA** 4.6.0: Data reduction, combining and cleaning  
  > "The data were reduced with CASA 4.6.0 (McMullin et al. 2007)." (2 Observations and Data Reduction)
- **kinemetry** : Kinemetric analysis of first moment map  
  > "we further quantify the kinemetric features using the code *kinemetry*" (3.3 Kinematics of the Nuclear Region)

## Numeric results

| quantity | value | uncertainty | units | step | quote |
|---|---|---|---|---|---|
| CO(6-5) beam-matched flux within r=1.125" | 160 | 16 | Jy km/s | 2 | is $160\pm16$ Jy km s$^{-1}$ |
| CO(6-5) total flux from channel photometry | 180 | 18 | Jy km/s | 3 | is $180\pm18$ Jy km s$^{-1}$ ($71\pm7$ mJy) |
| 434 um continuum flux density | 71 | 7 | mJy | 4 | $f_{434\,\mu{\rm m,\,ALMA}}=71\pm7$ mJy |
| Fraction of CO flux recovered within ALMA FOV | 40 | not stated | percent | 3 | our observation recovers 40% ($\equiv 0.8/0.4 \times 20\%$) of the total CO flux within the ALMA FOV |
| Rotation velocity amplitude from P-V (uncorrected for inclination) | ~140 | not stated | km/s | 5 | the velocity amplitude (uncorrected for the inclination) of this rotation is $\sim$140 km s$^{-1}$ |
| Median axis ratio q and inclination | q=0.59, i~54 | not stated | deg | 5 | has a median value of 0.59, suggesting an inclination $i=\arccos q \sim 54^\circ$ |
| Flux-weighted mean systemic velocity | 3345 | not stated | km/s | 2 | is 3345 km s$^{-1}$ |
| Number of clumps | 14 | not stated | dimensionless | 2 | we identified 14 clumps |

## Qualitative findings

- CO(6-5) is filamentary with dense cores and shows rotating-disk velocity field  
  > "The CO (6$-$5) emission displays a filamentary structure where many dense cores can be located" (Summary)

## Claim tuples

- H: Do CO(6-5) and dust emit co-spatially at ~34 pc scales? | E: Compared line and continuum maps and CO-to-continuum ratio | R: Peaks do not always coincide; ratio varies by >10 | F: Different excitation mechanisms are likely | **supported**
- H: Is the nuclear CO gas in an ordered rotating disk? | E: Moment maps, P-V diagram, kinemetry | R: Spider-diagram velocity field, ~140 km/s amplitude, weak non-circular motions | F: Rotating disk with possible weak inflow/outflow | **supported**
- H: Does the SW region differ in heating mechanism? | E: Compared CO/dust ratio, Pa-alpha EW and k5 | R: SW has higher CO/dust and ~10x smaller Pa-alpha EW | F: SW gas may be mechanically heated (indirect evidence) | **partially**

## Reasoning

- Why this data: _not stated_
- Why this method: _not stated_
- How they decided it was enough: _not stated_
- Limitation (authors): Missing-flux estimate is crude; extended emission over 2.1" is resolved out  
  > "this missing flux is a very crude estimation" (3.1 CO (6-5) Line Emission)
- Caveat (inferred, ours): Missing-flux estimate relies on a constant CO/70um ratio
- Caveat (inferred, ours): No uncertainties on the kinematic quantities
- Caveat (inferred, ours): Flux calibration inconsistencies among the three datasets (15% line, 37% continuum)
- Caveat (inferred, ours): Heating interpretation is indirect

## Reproducibility

- Data public (paper): Project IDs given; public archive status not explicitly stated  
  > "This paper makes use of the following ALMA data: ADS/JAO.ALMA#2013.1.00524.S and #2015.1.00385.S." (Acknowledgements)
- Products in archive: _not stated_
- Missing: Calibrator choices and flux scale
- Missing: Cleaning parameters
- Missing: Kinemetry and clump-finder settings
- Data volume (inferred): ~100-300 GB raw across three Band 9 executions
- Score (inferred): 3/5, Project codes, CASA version and robust are given, but cleaning, calibration and kinemetry details are missing.
- Rediscovery candidate: no, Key steps such as clump finding and kinemetry lack parameters; the missing-flux estimate depends on external data.

## Links

- Method: Krajnović et al. 2006 (Kinemetry method)
- Method: Williams et al. 1994 (Clump-finding algorithm)
- Companion: Zhao et al. 2016b (NGC 7130 sister ALMA CO(6-5) study)
- Companion: Xu et al. 2014, 2015 (NGC 34 and NGC 1614 ALMA CO(6-5) studies)
- Companion: Lu et al. 2017 (Herschel FTS data for the sample)
- Related: GOALS
- Related: Herschel SPIRE FTS LIRG sample

## Checks

```json
{
 "quotes": 68,
 "quotes_ok": 68,
 "quote_pass_rate": 1.0,
 "quotes_too_long": 0,
 "unsupported_facts": 0,
 "project_codes": 2,
 "codes_not_in_text": [],
 "codes_not_in_obscore": [],
 "obscore_codes_not_in_card": [],
 "codes_printed_but_missing": [],
 "numeric_results": 8,
 "numeric_problems": 0,
 "fill": {
  "facts": 74,
  "stated": 50,
  "rate": 0.676
 },
 "evidence_ok": true
}
```
