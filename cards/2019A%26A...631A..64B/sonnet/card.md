# Kinematics around the B335 protostar down to au scales

`2019A&A...631A..64B` | Astronomy and Astrophysics 2019 | first author: Bjerkeli, Per | arXiv: 1909.05178 | DOI: 10.1051/0004-6361/201935948

Card schema 1.0 | model claude-sonnet-5-5 | depth full | type observational_alma_primary

## Science

- Fields: star_formation, astrochemistry
- Question: What are the small-scale kinematics and morphology of the outflow and inner region of the isolated Class 0 protostar B335, and is there a Keplerian disk down to ~10 au?  
  > "Here we aim to determine the small-scale kinematical and morphological properties of the outflow from the isolated protostar B335 for which no Keplerian disk has, so far, been observed on scales down to 10 au." (abstract)
- Target **B335 (IRAS 19347+0727)**: coordinates phase centre 19h37m00.890s, +07d34m09.60s (J2000)  
  > "B335 is an isolated dense globule associated with the infrared identified protostar “IRAS 19347+0727” at a distance of approximately 100 pc (cite: Olofsson:2009jl)." (Introduction); z/distance ~100 pc  
  > "B335 is an isolated dense globule associated with the infrared identified protostar “IRAS 19347+0727” at a distance of approximately 100 pc (cite: Olofsson:2009jl)." (Introduction); distance from Olofsson & Olofsson 2009  
  > "B335 is an isolated dense globule associated with the infrared identified protostar “IRAS 19347+0727” at a distance of approximately 100 pc (cite: Olofsson:2009jl)." (Introduction)

## Data provenance

- ALMA projects: 2017.1.00288.S, 2013.1.00879.S, 2016.1.01552.S
- bands: Band 6 (1.3 mm)  
  > "Observations were carried out in Band 6 and cover five spectral windows (SPWs)." (2.1 New long-baseline observations)
- frequencies and spectral setup: 12CO 230.5, 13CO 220.4, C18O 219.6 GHz (120 MHz each; 122 kHz/61 kHz res.), SiO SPW 217.1 GHz (937 MHz, 488 kHz), continuum 233.0 GHz  
  > "The spectral resolution was set to 122 kHz for the $^{12}$CO SPW, and 61 kHz for $^{13}$CO and C$^{18}$O, while the total bandwidth in each SPW was 120 MHz." (2.1 New long-baseline observations)
- continuum bandwidth: _not stated_
- arrays: 12 m array, 45-51 antennas  
  > "Between 45 and 51 antennas of the 12 m array were used." (2.1 New long-baseline observations)
- configurations: _not stated_
- baselines: 41 - 16196 m  
  > "Baselines were in the range 41 – 16196 m, yielding a spatial resolution of 0.03$''$" (2.1 New long-baseline observations)
- angular resolution: 0.03'' (~3 au)  
  > "Baselines were in the range 41 – 16196 m, yielding a spatial resolution of 0.03$''$" (2.1 New long-baseline observations)
- max recoverable scale: ~0.3'' (long baseline); ~7'' combined  
  > "a largest recoverable scale corresponding to $\sim$0.3$''$" (2.1 New long-baseline observations)
- sensitivity: _not stated_
- time on source: ~2268 s per execution block (Table)  
  > "| 2017.1.00288.S | 08-Oct-2017 | 51 | 2268 | 0.5 | 41 | 16196 | 99 | -19, -1 |" (Table 1)
- observing dates: 21-29 Oct 2017 (five EBs; Table lists 8 Oct-29 Oct)  
  > "B335 was observed with ALMA between October 21st and 29th 2017 (five execution blocks)" (2.1 New long-baseline observations)
- pi or archival as stated: _not stated_
- Line: 12CO J=2-1 (230.5 GHz)
- Line: SiO 5-4 (217.1 GHz (SPW centre))
- Line: CH3OH 5(-1,4)-4(-2,3) E v=0 (216.945 GHz)
- Line: SO2 22(2,20)-22(1,21) (216.643 GHz)
- Other facility **APEX**: single-dish 12CO(2-1) to check flux recovery of combined image  
  > "single dish data acquired with the Atacama Pathfinder Experiment (APEX) telescope (Project: O-087.F-9314A, PI: M. V. Persson)" (2.2 Combining with archived data)
- External data: Dust temperature 30 K at 600 au, scaled with power-law index -0.4  
  > "using the previously estimated dust temperature of 30 K at 600 au (cite: Chandler:1993ms)" (3.2.1 Deriving the excitation conditions from CH3OH) [from Chandler:1993ms; Yen:2015vf; Shirley:2000qf]
- External data: Dust mass opacity 0.014 cm2/g at 1.3 mm  
  > "we use a total mass opacity of $0.014~\rm{cm}^2 \rm{g}^{-1}$ (cite: Yen:2015vf; Chandler:1993ms)" (4.1.1 Mass of the central emission) [from Yen:2015vf; Chandler:1993ms]
- External data: Outflow inclination 10 deg from plane of sky  
  > "We adopt an inclination angle 10$^\circ$ (cite: Hirano:1988lr) with respect to the plane of the sky" (4.2.3 Launching of the wind) [from Hirano:1988lr]
- External data: Source velocity 8.3 km/s  
  > "we adopt a source velocity of 8.3 $\mathrm{km \, s^{-1}}$ based on rare, isotopic line emission (cite: Evans:2005qy)" (3.1 Continuum and carbon monoxide) [from Evans:2005qy]

## Processing

### Calibration

- pipeline or manual: _not stated_
- casa version: CASA v5.1.1 for new data; archival calibrated with v4.3.1 and v4.7.0  
  > "Data reduction and imaging were carried out in CASA v5.1.1 (cite: McMullin:2007nr)." (2.1 New long-baseline observations)
- pipeline version: _not stated_
- archive products used as is: _not stated_
- flux calibrator: J2000-1748, J2134-0153, J2148+0657; phase J1938+0448  
  > "The flux calibration was done using J2000$-$1748, J2134$-$0153, and J2148+0657." (2.1 New long-baseline observations)
- flux scale uncertainty: ~10%  
  > "We estimate a flux accuracy of $\sim$10%." (2.1 New long-baseline observations)
- self calibration: _not stated_

### Imaging

- task: CLEAN (long baseline); tclean (combined)  
  > "Next, we deconvolved the combined data set using the CASA `tclean` procedure." (2.2 Combining with archived data)
- deconvolver: multiscale for line emission; Högbom for continuum of individual sets  
  > "Due to the nature of the combined data set, we used the so-called multiscale deconvolution algorithm for the line emission." (2.2 Combining with archived data)
- weighting robust: Briggs, robust 0.5  
  > "CLEAN algorithm with Briggs weighting and a robust parameter of 0.5." (2.1 New long-baseline observations)
- uv taper: _not stated_
- cell size: 0.01''  
  > "the pixel scale was set to 0.01$''$" (2.2 Combining with archived data)
- image size: 4096 x 4096 pixels  
  > "The size of the cleaned image is 4096 by 4096 pixels." (2.2 Combining with archived data)
- masking: _not stated_
- multiscale scales: 0, 8, 23, 68, 203, 608 pixels  
  > "The input scales used were 0, 8, 23, 68, 203, and 608 pixels, while the pixel scale was set to 0.01$''$." (2.2 Combining with archived data)
- continuum subtraction: uv-domain, line-free channels  
  > "The continuum was subtracted in the $uv$ domain using only line-free channels." (2.1 New long-baseline observations)
- line free channels: _not stated_
- primary beam correction: _not stated_
- array combination: concatenation of three projects after astrometric alignment and weight normalisation  
  > "The weights of each data set were normalised by dividing them by their average (i.e., all data sets received the same average weight level)." (2.2 Combining with archived data)
- smoothing: _not stated_
- final beam: _not stated_
- final rms: _not stated_

### Inherited from earlier work

- Rotation/expansion velocity method from PV Gaussian fits  
  > "can be estimated using the method presented in (cite: Lee:2018et), assuming that only two velocity components are present." (4.2.2 Outflow rotation and cavity expansion) [from Lee:2018et]
- Launching radius via Eq. (4)  
  > "Applying Eq. (4) of (cite: Anderson:2003jk), we thus estimate an upper limit for the launching radius" (4.2.3 Launching of the wind) [from Anderson:2003jk]

### Not stated but needed to reproduce (our reading)

- Line-free channels used for continuum subtraction
- Per-channel rms and final beams for the maps
- Cleaning masks used
- Protostellar mass 0.05 Msun origin for model curves not fully given
- Exact selection of data used in combination (manually flagged data)
- Gaussian fitting details for R-squared PV peak fits

## Analysis recipe

1. **Calibrate and image long-baseline data**: CASA calibration, uv continuum subtraction, CLEAN with Briggs weighting at native spectral resolution  
  > "All spectral line maps were imaged at the native spectral resolution." (2.1 New long-baseline observations)
   - software: CASA
   - parameter: robust = 0.5  
  > "Briggs weighting and a robust parameter of 0.5" (2.1 New long-baseline observations)
   - fitting: _not stated_
   - validation: _not stated_
2. **Combine with archival short-spacing data**: Align by Gaussian-fit continuum peaks, normalise weights, multiscale tclean of 12CO  
  > "We used a 2D-Gaussian fit to the peak position of the compact continuum emission in each data set to constrain their relative astrometry." (2.2 Combining with archived data)
   - software: CASA
   - parameter: thresholds 0.05 mJy/beam continuum, 3 mJy/beam lines  
  > "The cleaning threshold for the continuum was set to 0.05 mJy/beam and the threshold for the lines was set to 3 mJy/beam." (2.2 Combining with archived data)
   - fitting: _not stated_
   - validation: Compared with APEX spectra and Högbom cleaned individual datasets  
  > "Fig. [2](#fig:apexcomp) demonstrates that more than 50% of the emission observed with APEX is recovered in the line wings" (2.2 Combining with archived data)
3. **CH3OH excitation conditions**: LTE optically thin grid of models of four CH3OH lines  
  > "Assuming local thermodynamic excitation (LTE) and optically thin emission, we ran a grid of models covering a range of column densities and excitation temperatures." (3.2.1 Deriving the excitation conditions from CH3OH)
   - software: CASSIS
   - parameter: source size 0.15''  
  > "The source size was taken to be 0.15$''$ based on a 2D Gaussian fit" (3.2.1 Deriving the excitation conditions from CH3OH)
   - assumption: LTE, optically thin; CDMS spectroscopy  
  > "The spectroscopic information was taken from the CDMS" (3.2.1 Deriving the excitation conditions from CH3OH)
   - fitting: Grid of models; detected lines reproduced and non-detections not produced  
  > "In order to reproduce the detected lines, and *not* produce emission for the two non-detected lines" (3.2.1 Deriving the excitation conditions from CH3OH)
   - validation: Tau~0.7 check  
  > "These lines have an optical depth, $\tau$, of $\sim$0.7." (3.2.1 Deriving the excitation conditions from CH3OH)
4. **Continuum size and dust mass**: 2D Gaussian fit; M = S d^2/(kappa B(T))  
  > "M_{\rm{1.3 mm}} = \frac{S_{\rm{1.3 mm}}~d^2}{\kappa_{\rm{1.3 mm}} ~B(T_{\rm{dust}})}" (4.1.1 Mass of the central emission)
   - software: MATLAB
   - assumption: kappa=0.014 cm2/g, Tdust=200 K, d~100 pc  
  > "we use a total mass opacity of $0.014~\rm{cm}^2 \rm{g}^{-1}$" (4.1.1 Mass of the central emission)
   - fitting: _not stated_
   - validation: Compared with Evans et al. 2015 mass  
  > "This mass is comparable to the 7.5$\,\times\,10^{-4}$ $M_{\odot}$ inferred within a 25 au radius by (cite: Evans:2015qp)" (4.1.1 Mass of the central emission)
5. **Velocity gradients from PV diagrams**: Gaussian fit to flux per channel in PV, keep R^2>0.3, straight-line fit to peak positions  
  > "We present only velocity channels where R squared is larger than 0.3 and then subsequently fit a straight line through the peak positions" (4.1.2 Infall and rotation on small scales)
   - software: MATLAB
   - assumption: source velocity 8.3 km/s  
  > "assuming that the source velocity is 8.3 $\mathrm{km \, s^{-1}}$ w.r.t. $\upsilon_{\rm LSR}$" (4.1.2 Infall and rotation on small scales)
   - fitting: _not stated_
   - validation: Lower R^2 threshold does not affect results  
  > "(a lower threshold does not affect the results)" (4.1.2 Infall and rotation on small scales)
6. **Outflow rotation, expansion and launching radius**: 2D Gaussian fits to perpendicular PV cuts (>3 sigma, 7.3-9.3 km/s masked); launching radius from Anderson et al. 2003  
  > "we purposefully mask out velocities between 7.3 and 9.3 $\mathrm{km \, s^{-1}}$" (4.2.2 Outflow rotation and cavity expansion)
   - software: MATLAB
   - assumption: inclination 10 deg  
  > "We adopt an inclination angle 10$^\circ$ (cite: Hirano:1988lr) with respect to the plane of the sky" (4.2.3 Launching of the wind)
   - fitting: _not stated_
   - validation: Including masked velocities does not affect results  
  > "including velocities from 7.3 – 9.3 $\mathrm{km \, s^{-1}}$ in our analysis does not affect our results" (Footnote 7)

## Software

- **CASA** v5.1.1: data reduction, imaging, tclean  
  > "Data reduction and imaging were carried out in CASA v5.1.1 (cite: McMullin:2007nr)." (2.1 New long-baseline observations)
- **CASSIS** : CH3OH LTE spectral modelling  
  > "with the spectral modelling code CASSIS" (3.2.1 Deriving the excitation conditions from CH3OH)
- **MATLAB** : analysis  
  > "The analysis was performed with MATLAB." (2.2 Combining with archived data)

## Numeric results

| quantity | value | uncertainty | units | step | quote |
|---|---|---|---|---|---|
| 1.3 mm continuum peak flux (long baseline) | 4.8 | sigma ~2e-5 Jy | mJy/beam | 1 | continuum emission at 1.3 mm was detected with a peak flux of 4.8 mJy/beam ($\sigma \simeq 2\times10^{-5}$ Jy) |
| CH3OH column density | 6.8e18 | 0.1e18 | cm^-2 | 3 | a CH$_3$OH column density of $6.8\pm0.1\times 10^{18}$ cm$^{-2}$ and an excitation temperature of 220$\pm20$ K |
| CH3OH excitation temperature | 220 | 20 | K | 3 | an excitation temperature of 220$\pm20$ K is required |
| Circumstellar dust mass within 7 au | 3e-4 | not stated | Msun | 4 | the resulting circumstellar mass within 7 au is $M_{\rm{dust}}$ = 3$\,\times\,10^{-4}$ $M_{\odot}$ |
| Velocity gradient CH3OH v=0 | 1.4 | 0.3 | km/s/au | 5 | values of 1.4 $\pm$ 0.3 and 0.9 $\pm$ 0.5 $\mathrm{km \, s^{-1}}$ au$^{-1}$ for the v=0 and v=1 transitions |
| Velocity gradient CH3OH v=1 | 0.9 | 0.5 | km/s/au | 5 | values of 1.4 $\pm$ 0.3 and 0.9 $\pm$ 0.5 $\mathrm{km \, s^{-1}}$ au$^{-1}$ for the v=0 and v=1 transitions |
| Specific angular momentum within ~20 au | ~25 | not stated | au km/s | 5 | we estimate the specific angular momentum within $\sim$20 au to be $\sim$25 au $\mathrm{km \, s^{-1}}$ |
| Launching radius upper limit of high-velocity CO | ~0.07 | not stated | au | 6 | we thus estimate an upper limit for the launching radius of the high-velocity CO gas of the order of 0.07 au |
| Dynamical timescale of high-velocity CO bullet | 1.7 | not stated | yr | 6 | ejection took place within the last few years (formally, 1.7 years) |

## Qualitative findings

- 12CO shows X-shaped morphology from outflow cavity walls with ~50 au wide arms; dust continuum follows cavity walls in combined data  
  > "$^{12}$CO has a X-shaped morphology with arms $\sim$50 au in width that we associate with the walls of an outflow cavity" (abstract)

## Claim tuples

- H: Does the B335 inner region show Keplerian rotation or rotation in tracers? | E: PV analysis of CH3OH, SO2, 13CO in 3 au resolution data | R: CH3OH gradients 1.4 and 0.9 km/s/au; solid-body-like rotation within ~16 au; Keplerian around 0.05 Msun not excluded | F: Compact region rotates, but no clear Keplerian disk | **partially**
- H: Is the 12CO outflow rotating? | E: PV cuts perpendicular to outflow with Gaussian fitting | R: No clear rotation beyond ~30 au | F: CO traces entrained cavity walls rather than wind | **supported**
- H: What is the launching radius and timescale of the high-velocity gas? | E: Anderson et al. relation with measured velocities | R: r<0.1 au, ~1.7 yr | F: Episodic ejection, small launching radius | **supported**

## Reasoning

- Why this data: B335's proximity, age and orientation make it excellent for long-baseline observations  
  > "The age, the orientation, and the proximity of B335 make it an excellent target for long-baseline observations with ALMA." (Introduction)
- Why this method: _not stated_
- Alternative: High-velocity feature as continuous jet or precessing jet rejected in favour of episodic bullet  
  > "Instead, the explanation we find most plausible is that it is a molecular “bullet” associated with a recent accretion event" (4.2.4 Recent ejection outburst?)
- How they decided it was enough: _not stated_
- Limitation (authors): Some channels not cleaned to threshold in combined 12CO image  
  > "Even after that amount of time, a few channels were not properly cleaned" (2.2 Combining with archived data)
- Caveat (inferred, ours): Mass and temperature assumptions (200 K, kappa) uncertain
- Caveat (inferred, ours): CH3OH optically thin LTE with absorption at the protostar position
- Caveat (inferred, ours): Nearly plane-of-sky outflow makes rotation vs expansion degenerate
- Caveat (inferred, ours): Relative astrometry offsets between datasets exceed beam in some cases

## Reproducibility

- Data public (paper): Archival sets described as publicly available; all three project codes named  
  > "we combined our long-baseline data with two publicly-available ALMA data sets towards B335" (2.2 Combining with archived data)
- Products in archive: _not stated_
- Missing: Line-free channel ranges
- Missing: Clean masks
- Missing: Details of flagging
- Missing: MATLAB scripts not released
- Missing: ~800 hr cluster time needed for multiscale combination
- Data volume (inferred): Several hundred GB to ~1 TB raw (8 long-baseline EBs plus archival)
- Score (inferred): 3/5, Data public and key settings given, but masks, line-free channels, and analysis code missing; heavy compute.
- Rediscovery candidate: no, Combination imaging needs ~800 hr compute and several analysis details are unspecified.

## Links

- Method: Lee:2018et (Method for rotation and expansion velocities in outflows)
- Method: Anderson:2003jk (Launching radius formula)
- Companion: Imai:2019ip (Other ALMA observations of B335 CH3OH rotation and SiO)
- Companion: Yen:2015vf (Earlier ALMA infall/rotation study of B335)

## Checks

```json
{
 "quotes": 77,
 "quotes_ok": 77,
 "quote_pass_rate": 1.0,
 "quotes_too_long": 0,
 "unsupported_facts": 0,
 "project_codes": 3,
 "codes_not_in_text": [],
 "codes_not_in_obscore": [],
 "obscore_codes_not_in_card": [],
 "codes_printed_but_missing": [],
 "numeric_results": 9,
 "numeric_problems": 0,
 "fill": {
  "facts": 81,
  "stated": 57,
  "rate": 0.704
 },
 "evidence_ok": true
}
```
