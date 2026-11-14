# FRagmentation and Evolution of Dense Cores Judged by ALMA (FREJA). I. Overview: Inner ∼1000 au Structures of Prestellar/Protostellar Cores in Taurus

`2020ApJ...899...10T` | The Astrophysical Journal 2020 | first author: Tokuda, Kazuki | arXiv: 2006.06361 | DOI: 10.3847/1538-4357/ab9ca7

Card schema 1.0 | model claude-sonnet-5-5 | depth full | type large_program_or_survey

## Science

- Fields: star_formation
- Question: What are the inner ~1000 au structures of prestellar/protostellar cores in Taurus, and how long do high-density prestellar cores last before protostar formation?  
  > "The primary purpose of this study is to investigate the innermost part of dense cores with view to understanding the initial condition of star formation." (abstract)
- Target **39 Taurus dense cores (32 prestellar + 7 protostellar; e.g. MC1, MC5N, MC7N/S, MC31, MC35)**: coordinates Per-target RA/Dec in Table 1 (e.g. MC1 04h04m48.0s +26d19m22s)  
  > "MC1 | 4$^{\rm h}$04$^{\rm m}$48.0s | +26$^\circ$19$'$22.0$''$" (Table 1); "Distance$^{\rm c}$" (Table 1); z/distance 126.6-162.7 pc depending on region; 140 pc for L1521  
  > "MC1 | 4$^{\rm h}$04$^{\rm m}$48.0s | +26$^\circ$19$'$22.0$''$" (Table 1); "Distance$^{\rm c}$" (Table 1); distance from Galli18 per cloud; Elias78 for L1521  
  > "MC1 | 4$^{\rm h}$04$^{\rm m}$48.0s | +26$^\circ$19$'$22.0$''$" (Table 1); "Distance$^{\rm c}$" (Table 1)

## Data provenance

- ALMA projects: 2016.1.00928.S, 2018.1.00756.S, 2015.1.00340.S
- bands: Band 6 (1.3 mm); effective continuum frequency 225.3 GHz  
  > "The effective frequency of the final processed continuum images is 225.3 GHz ($\sim$1.3 mm)." (2.2 Observations)
- frequencies and spectral setup: PROJ6: four line windows (62.5 MHz, 61.0 kHz resolution) for N2D+, 12CO, 13CO, C18O; two continuum windows at 218.0 and 232.5 GHz  
  > "There were four spectral windows for molecular line observations with a bandwidth of 62.5 MHz and a spectral resolution of 61.0 kHz" (2.2 Observations); "The central frequencies of the two bands were 218.0 and 232.5 GHz." (2.2 Observations)
- continuum bandwidth: two 2000 MHz continuum windows  
  > "We used two spectral windows, whose bandwidth and resolution were 2000 MHz and 15.6 MHz, respectively, to obtain continuum images." (2.2 Observations)
- arrays: ACA 7 m array plus Total Power array, stand-alone  
  > "We performed the ACA (the 7 m array and the TP (Total Power) array) observations toward the Taurus dense cores" (2.2 Observations)
- configurations: _not stated_
- baselines: 7 m array uv range 5.4-29 klambda  
  > "The covered $uv$ range of the 7 m array was 5.4–29 k$\lambda$." (2.2 Observations)
- angular resolution: 6.5'' geometric mean (~900 au)  
  > "with an angular resolution of 6.5$''$ ($\sim$900 au)" (abstract)
- max recoverable scale: ~30''  
  > "the $\sim$30$''$ maximum recovering scale allow us to distinguish" (2.1.2 Frequency Setting)
- sensitivity: continuum rms ~0.4 mJy/beam (PROJ6)  
  > "PROJ6$^{\rm a}$ | 2018.1.00756.S | 1.3 mm" (Table 2)
- time on source: ~8.5 min per pointing, three pointings per target  
  > "The integration time (on-source time) per pointing was $\sim$8.5 minutes." (2.2 Observations)
- observing dates: PROJ6: 2018 October to 2019 March  
  > "between 2018 October and 2019 March" (2.2 Observations)
- pi or archival as stated: PI K. Tachihara for PROJ4 and PROJ6  
  > "Cycle 6 program (P.I., K. Tachihara, #2018.1.00756.S, hereafter PROJ6)" (2.1.1 Target Selection)
- Line: N2D+ 3-2 (not stated)
- Line: C18O 2-1 (not stated)
- Line: 12CO, 13CO 2-1 (not stated)
- Line: H13CO+, H13CN 3-2 (PROJ4) (not stated)
- Other facility **Herschel, IRAM 30m, JCMT**: single-dish continuum peaks used to select pointing coordinates  
  > "We selected the observation coordinates to the peak positions of the millimeter/submillimeter continuum emission obtained by the IRAM 30 m, the JCMT 15 m, and the Herschel telescope" (2.1.1 Target Selection)
- Other facility **Nobeyama 45 m**: H13CO+ core catalog and N2H+ detections used for target selection  
  > "high-resolution H$^{13}$CO$^{+}$ (1–0) observations using the Nobeyama 45 m telescope (cite: Onishi02) discovered 44 prestellar cores" (2.1.1 Target Selection)
- External data: Distances to Taurus clouds (140 pc for L1521)  
  > "Distance measurements toward individual clouds in Taurus by (cite: Galli18)." (Table 1) [from Galli18; Elias78]
- External data: NH3 kinetic temperatures used as dust temperatures  
  > "Kinematic temperature derived from NH$_3$ observations" (Table 1) [from Benson89; Codella97; Seo15; Feh16; Friesen17]
- External data: Dust opacity kappa_1.3mm = 0.005 cm2/g  
  > "$\kappa_{\rm 1.3\,mm}$ = 0.005 cm${^2}$ g$^{-1}$ for prestellar cores (cite: Ossenkopf94; Preibisch93)" (3.1 Prestellar Cores) [from Ossenkopf94; Preibisch93]
- External data: Higher-resolution interferometric disk fluxes for protostellar sources  
  > "We compiled higher-resolution interferometric observations at the same frequency from the literature for all protostellar sources" (3.2 Protostellar Cores) [from Table 4 footnotes]
- External data: Prestellar core catalog of 44 cores and lifetime ~4e5 yr  
  > "(cite: Onishi02) discovered 44 prestellar cores with an average density of $\gtrsim$10$^{5}$ cm$^{-3}$" (4.3) [from Onishi02]
- Simulation/model as data: Synthetic ACA observations of Plummer-like smooth cores (p=2; R_flat 300-8000 au; N_H2(6000 au) 7e21, 1e22, 3e22 cm-2) via simobserve + tclean  
  > "We generated smoothed core models with a Plummer-like function as input models for the simulated observations." (4.1)

## Processing

### Calibration

- pipeline or manual: _not stated_
- casa version: CASA 5.6.0  
  > "We performed the data reduction using the Common Astronomy Software Application (CASA) package (cite: McMullin07) version 5.6.0." (2.2 Observations)
- pipeline version: _not stated_
- archive products used as is: _not stated_
- flux calibrator: J0423-0120 (bandpass and flux)  
  > "The bandpass and flux calibrator was the quasar J0423–0120." (2.2 Observations)
- flux scale uncertainty: _not stated_
- self calibration: not applied  
  > "We did not apply the self-calibration process, because the continuum emission of the prestellar sources is quite weak." (2.2 Observations)

### Imaging

- task: tclean  
  > "we used the `tclean` task with the `multi-scale` deconvolver (cite: Kepley20) to recover the extended emission." (2.2 Observations)
- deconvolver: multiscale  
  > "we used the `tclean` task with the `multi-scale` deconvolver (cite: Kepley20) to recover the extended emission." (2.2 Observations)
- weighting robust: Natural  
  > "The weighting scheme was $``$Natural.$"$" (2.2 Observations)
- uv taper: _not stated_
- cell size: 1.0'' square pixels  
  > "The imaging grid was set to have square pixels of 1.0$''$ width" (2.2 Observations)
- image size: _not stated_
- masking: manual clean box; cleaned to ~1 sigma residual  
  > "We manually selected the emission mask (clean box) and continued the deconvolution process until the intensity of the residual image reached the $\sim$1$\sigma$ noise level." (2.2 Observations)
- multiscale scales: 0, 6, 18 pixels  
  > "the scales of the `multi-scale` clean are 0, 6, and 18 pixels." (2.2 Observations)
- continuum subtraction: _not stated_
- line free channels: _not stated_
- primary beam correction: applied before 2D Gaussian fitting  
  > "We performed 2D Gaussian fittings to the observed continuum distributions in the image plane after the primary beam correction" (3.1 Prestellar Cores)
- array combination: 7m + TP feathered with CASA feather only for MC1 and MC7 line images  
  > "we used the combined 7 m and TP array images obtained by the `feather` task in CASA" (2.2 Observations)
- smoothing: _not stated_
- final beam: average 6.8'' x 6.2'' (geometric mean 6.5'')  
  > "The average angular resolution is 6.8$''$ $\times$ 6.2$''$, and the geometric mean is 6.5$''$." (7.2 The Image Qualities)
- final rms: ~0.4 mJy/beam (PROJ6); per-target in Table 5  
  > "PROJ6$^{\rm a}$ | 2018.1.00756.S | 1.3 mm" (Table 2)

### Inherited from earlier work

- PROJ4 data reduction and quality  
  > "Detailed data reduction processes and qualities in PROJ4 and PROJ-MC27 were presented in (cite: Tokuda19) and (cite: Tokuda18), respectively." (2.2 Observations) [from Tokuda19; Tokuda18]
- Same imaging method and parameters applied to PROJ4 and PROJ-MC27  
  > "Note that we applied the same method and parameters to the other two different data sets (PROJ4 and PROJ-MC27)." (2.2 Observations) [from Tokuda19; Tokuda18]
- Synthetic-observation aspect-ratio model  
  > "we considered parametric models with aspect ratios (see Equation (5) in (cite: Caselli19))" (4.1) [from Caselli19]

### Not stated but needed to reproduce (our reading)

- Rest frequencies and line windows per target
- Phase calibrator selection per execution block and QA/flagging details
- How the 7 m ms was calibrated (pipeline vs manual, pipeline version)
- Mask definitions per target and exact rms measurement regions
- How Table 3 category I/II/III counts for unobserved cores were assigned
- Simulation integration time and noise treatment

## Analysis recipe

1. **Image continuum and measure source properties**: tclean multiscale natural-weighted continuum imaging, then 2D Gaussian fits after primary beam correction; rms from emission-free pixels  
  > "We manually selected emission-free pixels from each continuum image to estimate their rms noise levels." (2.2 Observations)
   - software: CASA
   - parameter: scales 0,6,18 pix; 1'' pixels; natural weighting; 3 sigma detection threshold  
  > "We could not detect significant ($>$3$\sigma$) emission in 20 prestellar cores" (3.1 Prestellar Cores)
   - fitting: 2D Gaussian in image plane  
  > "We performed 2D Gaussian fittings to the observed continuum distributions in the image plane" (3.1 Prestellar Cores)
   - validation: Two continuum bands compared for MC1 and MC35  
  > "Figure [8](#fig:cont1-2) shows that the two frequency images reproduce almost the same result." (7.1)
2. **Derive masses and densities**: M = D^2 F / (kappa B(Td)); n(H2)=3M/(4 pi mu mH R^3)  
  > "$n(\rm H_2)$ = 3$M_{\rm obs}$/4$\pi\mu$m$_{\rm H}R_{\rm obs}^{3}$" (3.1 Prestellar Cores)
   - parameter: R_obs = sqrt(Major*Minor)/2; mu = 2.8  
  > "$R_{\rm obs}$ is the observed radius (=$\sqrt{\rm Major*Minor}$/2)" (3.1 Prestellar Cores)
   - assumption: kappa_1.3mm=0.005 cm2/g; Td equals NH3 gas temperature, uniform  
  > "assuming that the temperatures of gas and dust are well coupled in the dense regions and a uniform temperature distribution" (3.1 Prestellar Cores)
   - fitting: _not stated_
   - validation: Argued grain growth does not strongly affect mass at 7 m beam  
  > "The grain growth thus does not strongly affect the mass estimation with the 7 m array beam size." (3.1 Prestellar Cores)
3. **Test whether substructures are interferometric artifacts**: simobserve and tclean of smooth Plummer-like cores compared with observations; plus C18O and N2D+ line distributions  
  > "In the CASA simulator, we used the `simobserve` task to generate simulated visibilities at a central frequency of 225 GHz" (4.1)
   - software: CASA simobserve, tclean
   - parameter: p=2; R_flat 8000,2500,1500,900,300 au; aspect ratios 1.0 and 1.8; kappa=0.005, Td=10 K  
  > "We adapted two aspect ratios of 1.0 and 1.8." (4.1)
   - assumption: Td = 10 K, kappa = 0.005 cm2/g  
  > "we assumed $\kappa_{\rm 1.3\,mm}$ = 0.005 cm$^{2}$ g$^{-1}$ and $T_{\rm d}$ = 10 K" (4.1)
   - fitting: _not stated_
   - validation: MC31 real vs synthetic residual comparison  
  > "The residual image does not show large differences between the real and synthetic observations." (7.3)
4. **Estimate lifetimes by statistical counting**: Divide 54 Taurus prestellar cores into categories I/II/III by continuum flux (21 mJy cut) and scale by total lifetime ~5e5 yr  
  > "The total numbers in categories I, II, and III are 45, 6, and 3, respectively." (4.3)
   - parameter: flux criterion 21 mJy (n >= 8e5 cm-3)  
  > "We tentatively set a flux criterion of 21 mJy, whose density is $\gtrsim$8 $\times$10$^{5}$ cm$^{-3}$, to separate II and III." (4.3)
   - assumption: unobserved cores are category I; constant evolution speed; total lifetime ~5e5 yr  
  > "We assumed that the unobserved cores in this study are categorized under I" (4.3)
   - fitting: _not stated_
   - validation: Detection count prediction ~11 consistent with observed  
  > "the expected total number of detections is $\sim$11, which is consistent with our present observations." (4.3)

## Software

- **CASA** 5.6.0: calibration, tclean imaging, simobserve, feather  
  > "We performed the data reduction using the Common Astronomy Software Application (CASA) package (cite: McMullin07) version 5.6.0." (2.2 Observations)
- **Astropy** : listed in software section  
  > "CASA (v5.6.0; (cite: McMullin07)), Astropy (cite: Astropy18), APLpy (v1.1.1: (cite: Robi12)" (Software)
- **APLpy** 1.1.1: plotting  
  > "APLpy (v1.1.1: (cite: Robi12)" (Software)

## Numeric results

| quantity | value | uncertainty | units | step | quote |
|---|---|---|---|---|---|
| Prestellar cores with continuum detection | 12 of 32 (about one-third) | not stated | cores | 1 | we confirmed continuum detection toward 12 prestellar cores |
| Prestellar peak flux range | 2-5 | not stated | mJy/beam | 1 | are 2–5 mJy beam$^{-1}$ and 5–63 mJy, respectively |
| Prestellar total flux range | 5-63 | not stated | mJy | 1 | are 2–5 mJy beam$^{-1}$ and 5–63 mJy, respectively |
| Prestellar mass range | ~1e-2 to 1e-1 | not stated | Msun | 2 | The estimated masses ($M_{\rm obs}$) are $\sim$10$^{-2}$–10$^{-1}$ $M_{\odot}$ |
| Prestellar derived density | ~(3-10)e5 | not stated | cm-3 | 2 | The derived densities are $\sim$(3–10)$\times$10$^5$ cm$^{-3}$ |
| Protostellar total flux range | 62-225 | not stated | mJy | 1 | The observed total and peak fluxes are 62–225 mJy and $\sim$14–202 mJy beam$^{-1}$ |
| Disk contribution fraction | 35-90% except MC27 | not stated | percent | 1 | most of the flux is dominated by $F_{\rm disk}$ with a range of 35–90% except for MC27 |
| Category counts I/II/III | 45, 6, 3 | not stated | cores | 4 | The total numbers in categories I, II, and III are 45, 6, and 3, respectively. |
| Stage timescales I/II/III | ~3e5, ~6e4, ~3e4 | not stated | yr | 4 | $\sim$3 $\times$ 10$^{5}$ yr (I), $\sim$6 $\times$ 10$^{4}$ yr (II), and $\sim$3 $\times$ 10$^{4}$ yr (III) |
| Detection limit of central density | ~4e5 | not stated | cm-3 | 3 | gives us a detection limit of the central density, $\sim$4 $\times$ 10$^{5}$ cm$^{-3}$ |
| Missing flux relative to single dish | >80% | not stated | percent | 1 | there is a large amount of missing flux, more than 80% |

## Qualitative findings

- Two prestellar cores (MC1, MC7) show real ~1000 au substructure supported by C18O and N2D+ distributions, not just artifacts.  
  > "we confirmed that at least two prestellar sources harbor internal substructures" (4.2)
- Synthetic 7 m observations of smooth cores with R_flat ~2500 au can produce spurious multiple peaks.  
  > "the 7 m array measurements can artificially produce multiple peaks whose angular separation is similar to the observed beam size" (4.1)

## Claim tuples

- H: The ACA 7 m array detects inner dense structure in prestellar cores at higher rate than 12 m surveys | E: 1.3 mm continuum ACA survey of 32 prestellar cores | R: 12 of 32 detected (~one-third) versus zero or one in previous surveys | F: Shorter baselines greatly raise the detection rate | **supported**
- H: Prestellar core lifetime approaches freefall time at higher density | E: Statistical counting by continuum category | R: Lifetimes ~3e5, 6e4, 3e4 yr for categories I-III | F: Self-gravity dominates above ~1e6 cm-3 | **supported**
- H: Observed continuum substructures are real fragmentation | E: Synthetic observations plus C18O/N2D+ comparison | R: Artifacts can mimic substructure, but MC1 and MC7 show density contrast in lines | F: At least two cores have real substructure | **partially**
- H: Protostellar disks dominate 7 m continuum in protostellar cores | E: Compare ACA flux with high-resolution literature disk fluxes | R: F_disk 35-90% except MC27 | F: Disk contributions dominate except the VeLLO | **supported**

## Reasoning

- Why this data: ACA 7 m recovers lower spatial frequencies, avoiding the missing-flux issue of the 12 m array  
  > "is the best tool to explore the innermost part of a dense core without a serious missing flux problem compared to the 12 m array alone." (1.2)
- Why this method: _not stated_
- Alternative: Interferometric artifact explanation of substructures considered and rejected for MC7 using single-dish peak positions  
  > "the positions of each continuum source correspond to local peaks obtained by the early single-dish 0.87 mm continuum observation" (4.2)
- How they decided it was enough: _not stated_
- Limitation (authors): Continuum-only substructure cannot be distinguished from artifacts at low contrast  
  > "Therefore, we cannot merely claim that the observed substructure is a substantial piece of evidence of fragmentation of prestellar cores." (4.1)
- Limitation (authors): Mass uncertainty dominated by assumed dust opacity  
  > "The uncertainty of the mass estimation mainly arises from the assumption of $\kappa_{\rm 1.3\,mm}$" (3.1 Prestellar Cores)
- Caveat (inferred, ours): Lifetime statistics depend on an assumed total core count (54) and lifetime (5e5 yr) from earlier work and constant evolution speed
- Caveat (inferred, ours): Category thresholds (21 mJy) are tentative and based on a uniform Td and opacity
- Caveat (inferred, ours): No uncertainties are given on masses, fluxes or timescales
- Caveat (inferred, ours): Uniform NH3 temperature used for dust may bias masses

## Reproducibility

- Data public (paper): Data are ALMA archival projects listed in acknowledgments  
  > "This paper makes use of the following ALMA data: ADS/ JAO.ALMA#2015.1.00340.S, 2016.1.00928.S, and 2018.1.00756.S." (Acknowledgments)
- Products in archive: _not stated_
- Missing: Calibration pipeline details
- Missing: Line-image processing parameters
- Missing: Per-source mask choices and simobserve noise settings
- Data volume (inferred): ~tens of GB for three ACA projects (39 targets, 3 pointings each)
- Score (inferred): 3/5, Imaging parameters and mass equations are given and data are archival, but calibration, masks and some statistics assumptions are vague.
- Rediscovery candidate: yes, Data are public ALMA projects, imaging recipe and mass equations are given, and the main results are numeric (fluxes, masses, detection counts).

## Links

- Method: Tokuda19 (PROJ4 data reduction and pilot study)
- Method: Tokuda18 (PROJ-MC27 data reduction)
- Method: Caselli19 (interferometric artifact model with aspect ratio)
- Companion: Fujishiro20 (Paper II on FHSC candidate MC35)
- Related: FREJA
- Related: Dunham16 Chamaeleon I ALMA survey
- Related: Kirk17 Ophiuchus ALMA survey

## Checks

```json
{
 "quotes": 92,
 "quotes_ok": 92,
 "quote_pass_rate": 1.0,
 "quotes_too_long": 0,
 "unsupported_facts": 0,
 "project_codes": 3,
 "codes_not_in_text": [],
 "codes_not_in_obscore": [],
 "obscore_codes_not_in_card": [],
 "codes_printed_but_missing": [],
 "numeric_results": 11,
 "numeric_problems": 0,
 "fill": {
  "facts": 81,
  "stated": 65,
  "rate": 0.802
 },
 "evidence_ok": true
}
```
