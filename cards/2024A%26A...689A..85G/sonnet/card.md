# MINDS: A multi-instrument investigation into the molecule-rich JWST-MIRI spectrum of the DF Tau binary system

`2024A&A...689A..85G` | Astronomy and Astrophysics 2024 | first author: Grant, Sierra L. | arXiv: 2406.10217 | DOI: 10.1051/0004-6361/202450768

Card schema 1.0 | model claude-sonnet-5-5 | depth light | type multi_facility_alma_minor

## Science

- Fields: protoplanetary_disks, astrochemistry
- Question: What are the physical and chemical properties of the DF Tau binary's disks, and does DF Tau B host a disk? Where does the molecular emission in the JWST-MIRI spectrum originate?  
  > "We investigate the physical and chemical properties of the equal-mass, small-separation ($\sim$66 milliarcsecond, $\sim$9 au) binary system DF Tau." (abstract)
- Target **DF Tau (A and B)**: coordinates _not stated_; z/distance 140±10 pc  
  > "The projected distance between these measurements is about 3 mas, or 0.5 au at the distance of DF Tau B" (2.3 VLTI-GRAVITY); "Therefore, we adopted the standard distance to Taurus of 140$\pm$10 pc, in agreement with the group location found in (cite: krolikowski21)" (4.1 Slab modeling procedure); distance from standard distance to Taurus (Gaia parallax deemed unreliable due to binarity)  
  > "The projected distance between these measurements is about 3 mas, or 0.5 au at the distance of DF Tau B" (2.3 VLTI-GRAVITY); "Therefore, we adopted the standard distance to Taurus of 140$\pm$10 pc, in agreement with the group location found in (cite: krolikowski21)" (4.1 Slab modeling procedure)

## Data provenance

- ALMA projects: 2019.1.01739.S, 2021.1.00854.S
- bands: 1.3 mm continuum (~218-247 GHz)  
  > "The 1.3 mm ALMA observations show two equal-brightness sources of compact ($R\lesssim$3 au) continuum emission" (abstract)
- frequencies and spectral setup: SB1/LB1: 4 SPWs (12CO 2-1 at 230.538 GHz; continuum at 232.6, 245.0, 246.9 GHz). SB2/LB2: 6 SPWs (C18O, 13CO, 12CO 2-1, N2D+ 3-2, continuum at 218 and 233 GHz)  
  > "The observations SB1 and LB1 had the correlator configured to observe 4 spectral windows, with one of them centered at 230.538 GHz to observe the $^{12}$CO $J$=2-1 line" (2.2 ALMA)
- continuum bandwidth: _not stated_
- arrays: _not stated_
- configurations: One long-baseline (LB) and one compact (SB) execution in each project  
  > "Each project observed DF Tau twice, once with a long baseline configuration and once with a compact baseline configuration, which we name LB and SB, respectively" (2.2 ALMA)
- baselines: SB1 15-3697 m; LB1 47-12595 m; LB2 64-8283 m; SB2 15-1997 m  
  > "| 2019.1.01739.S | SB1 | Tofflemire, B. | 2021-07-18 | 49 | 15 - 3697 | 5.14 | 230.07 - 247.90 |" (Appendix A table)
- angular resolution: _not stated_
- max recoverable scale: _not stated_
- sensitivity: _not stated_
- time on source: Exposure times: SB1 5.14, LB1 45.29, LB2 26.31, SB2 6.25 min  
  > "|  | LB1 |  | 2021-08-24 | 48 | 47 - 12595 | 45.29 |  |" (Appendix A table)
- observing dates: 2021-07-18, 2021-08-24, 2021-10-29, 2022-07-04  
  > "| 2021.1.00854.S | LB2 | Long, F. | 2021-10-29 | 45 | 64 - 8283 | 26.31 | 217.60 - 233.93 |" (Appendix A table)
- pi or archival as stated: Programs of PI Tofflemire and PI Long  
  > "DF Tau was observed with ALMA as part of the projects 2019.1.01739.S (PI: Tofflemire) and 2021.1.00854.S (PI: Long)." (2.2 ALMA)
- Line: 12CO J=2-1 (230.538 GHz)
- Other facility **JWST-MIRI MRS**: Mid-infrared spectrum (PID 1282, MINDS) with molecular emission  
  > "These observations are part of the MIRI mid-INfrared Disk Survey (MINDS) JWST guaranteed time observation program (PID: 1282, PI: T. Henning" (2.1 JWST-MIRI observations)
- Other facility **VLTI-GRAVITY**: K-band interferometry: binary astrometry and inner dust disk size  
  > "DF Tau was observed with VLTI-GRAVITY (cite: gravity17) on 28 October 2022." (2.3 VLTI-GRAVITY)
- Other facility **IRTF-iSHELL**: M-band high-resolution CO and H2O line profiles  
  > "DF Tau was observed with iSHELL (cite: rayner16; rayner22) on the Infrared Telescope Facility (IRTF) on 24 January 2022." (2.4 IRTF-iSHELL)
- External data: Orbital parameters, stellar properties (spectral type, mass 0.55 Msun, R*, Teff)  
  > "Both DF Tau A and B have spectral types of $\sim$M2 and stellar masses of 0.55 $M_{\odot}$ (cite: allen17)." (1 Introduction) [from (cite: allen17)]
- External data: K-band magnitude / flux ratio used to fix relative fluxes in GRAVITY model  
  > "we constrained the relative flux of each component ($F_A$, $F_B$, and $F_{disk}$) using the K-band magnitude from (cite: schaefer14)" (3.2 VLTI-GRAVITY) [from (cite: schaefer14)]
- External data: iSHELL CO and H2O line widths  
  > "(cite: banzatti23a) find that the CO fundamental emission lines have two velocity components, a broad component (FWHM=113 km s$^{-1}$)" (2.4 IRTF-iSHELL) [from (cite: banzatti23a)]
- External data: Dust opacity 2.254 cm2/g  
  > "an opacity of 2.254 cm$^{2}$ g$^{-1}$ (cite: beckwith90)" (Table 1 notes) [from (cite: beckwith90)]

## Processing

### Calibration

- pipeline or manual: Pipeline-calibrated with the delivered scriptforPI, then self-calibrated  
  > "The observations of both programs were pipeline-calibrated with the `scriptforPI` delivered by ALMA." (2.2 ALMA)
- casa version: CASA 5.6.2  
  > "Then, `CASA 5.6.2` was used to extract the dust continuum emission from all the spectral windows." (2.2 ALMA)
- pipeline version: _not stated_
- archive products used as is: _not stated_
- flux calibrator: J0510+1800 (LB1)  
  > "the antenna DV23 returned a temperature of 0 K while observing the flux calibrator J0510+1800" (2.2 ALMA)
- flux scale uncertainty: _not stated_
- self calibration: Each observation self-calibrated individually; phase until no S/N improvement, then one amplitude calibration; scans and SPWs combined  
  > "Phase calibrations were applied until no improvement was seen in the peak signal-to-noise ratio, and then only one amplitude calibration was applied to each observation." (2.2 ALMA)

### Imaging

- task: tclean  
  > "which was imaged with the task `tclean`, using a Briggs robust parameter of 0.5 for all epochs" (2.2 ALMA)
- deconvolver: _not stated_
- weighting robust: Briggs robust = 0.5  
  > "using a Briggs robust parameter of 0.5 for all epochs" (2.2 ALMA)
- uv taper: _not stated_
- cell size: _not stated_
- image size: _not stated_
- masking: Each image cleaned down to 1 sigma threshold; gain=0.02, cyclefactor=1.5  
  > "Each image was cleaned down to a 1$\sigma$ threshold." (2.2 ALMA)
- multiscale scales: _not stated_
- continuum subtraction: Channels within ±20 km/s of expected lines flagged; rest combined into pseudo-continuum, averaged to 125 MHz channels and 6 s bins  
  > "we flagged the channels located at $\pm20$ km s$^{-1}$ from the expected lines" (2.2 ALMA)
- line free channels: _not stated_
- primary beam correction: _not stated_
- array combination: _not stated_
- smoothing: _not stated_
- final beam: _not stated_
- final rms: _not stated_

### Inherited from earlier work

- Line-channel flagging for continuum extraction  
  > "As in (cite: andrews18), we flagged the channels located at $\pm20$ km s$^{-1}$ from the expected lines" (2.2 ALMA) [from (cite: andrews18)]
- JWST continuum subtraction and baseline procedure  
  > "We followed the methods of (cite: temmink24a)." (4.1 Slab modeling procedure) [from (cite: temmink24a)]
- LTE slab model approach  
  > "and therefore we used the same methods to analyze the DF Tau MRS data." (4.1 Slab modeling procedure) [from (cite: grant23a; gasman23b; kospal23; perotti23; ramirez-tannus23; tabone23)]
- Gaussian line profile FWHM 4.7 km/s for slab  
  > "as is done in (cite: salyk11a)" (4.1 Slab modeling procedure) [from (cite: salyk11a)]

### Not stated but needed to reproduce (our reading)

- Phase-center/field and image sizes and cell sizes for tclean
- MCMC priors, walker number, and convergence details for the galario visibility fit
- Number of self-calibration iterations and solution intervals
- Disk inclination/PA priors in the visibility fit
- Slab-model parameter prior ranges and number of walkers
- Details of Kutra et al. independent ALMA analysis (in prep.)

## Analysis recipe

1. **Pseudo-continuum extraction and self-calibration**: Flag line channels, average to pseudo-continuum, self-calibrate each epoch separately using tclean images  
  > "we self-calibrated each observation individually, as combining them would assume that the brightness distribution has not changed in the time spanned between epochs." (2.2 ALMA)
   - software: CASA, tclean, gaincal
   - parameter: robust 0.5; gain 0.02; cyclefactor 1.5  
  > "we lowered the `gain` parameter to $0.02$ and increased the `cyclefactor` to $1.5$" (2.2 ALMA)
   - fitting: _not stated_
   - validation: _not stated_
2. **Visibility modeling of the ALMA continuum**: Parametric visibility model with two Gaussian-ring disks, per-epoch positions and flux scaling, SB2 used as flux reference  
  > "the dust continuum emission was analyzed using parametric visibility modeling with the packages `galario` (cite: tazzari2018) and `emcee` (cite: emcee)." (7 ALMA log and visibility model)
   - software: galario, emcee
   - parameter: Gaussian ring I(r)=f exp(-0.5((r-r_k)/sigma_k)^2); gamma_SB2=1  
  > "As a flux reference we used SB2, as it is the observation with the shortest baselines. Therefore, $\gamma_{SB2}=1$" (7 ALMA log and visibility model)
   - assumption: Dust mass: T_dust 20 K, wavelength 1.33 mm, kappa 2.254 cm2/g, distance 140±10 pc  
  > "Dust masses are computed assuming a dust temperature of 20 K, a wavelength of 1.33 mm, an opacity of 2.254 cm$^{2}$ g$^{-1}$" (Table 1 notes)
   - fitting: MCMC with emcee; priors not stated; 3 sigma uncertainties  
  > "Uncertainties are the 3$\sigma$ values of the distributions." (Table 1 notes)
   - validation: Positions compared with GRAVITY astrometry and Allen+17 orbit  
  > "with separations consistent with astrometry from VLTI-GRAVITY and movement consistent with the known orbital parameters of the system" (abstract)
3. **Fit GRAVITY visibilities and iSHELL line profiles for inner disk**: Binary vs binary+Gaussian disk model MCMC with chi2; Keplerian line-profile model for CO  
  > "The binary-plus-disk model provides a significant improvement in the $\chi^2_r$ compared to the binary-only model (from 8 to 5)." (3.2 VLTI-GRAVITY)
   - fitting: MCMC with chi2 statistic  
  > "a Markov chain Monte Carlo (MCMC) procedure was adopted. The posterior distribution was used, assuming a $\chi^2$ statistic" (3.2 VLTI-GRAVITY)
   - validation: _not stated_
4. **LTE slab fit of MIRI spectrum**: Simultaneous multi-component LTE slab fit of all molecules with emcee  
  > "used an MCMC fitting procedure to fit all of the molecules and all components simultaneously" (4.1 Slab modeling procedure)
   - software: emcee, PyBaselines
   - parameter: Fit 13.4-18 and 18-25.6 micron; noise 2 and 4 mJy; ~1e5 steps  
  > "Model convergence was achieved after $\approx10^5$ steps." (4.1 Slab modeling procedure)
   - assumption: distance 140±10 pc; Gaussian line FWHM 4.7 km/s  
  > "Gaussian line profile with a FWHM of $\Delta$V=4.7 km s$^{-1}$ ($\sigma$=2 km s$^{-1}$)" (4.1 Slab modeling procedure)
   - fitting: emcee, uniform priors, 8x walkers as free parameters  
  > "using a uniform prior for each parameter, and eight times the number of walkers compared to the number of free parameters" (4.1 Slab modeling procedure)
   - validation: A fourth water component tested; posterior clustered at 0 au radius  
  > "We tested adding a fourth water component. The posteriors for this component clustered at an emitting radius of 0 au" (4.2 Best-fit models)

## Software

- **CASA** 5.6.2: Continuum extraction, self-calibration, tclean imaging  
  > "Then, `CASA 5.6.2` was used to extract the dust continuum emission from all the spectral windows." (2.2 ALMA)
- **galario** : Visibility modeling of ALMA data  
  > "parametric visibility modeling with the packages `galario` (cite: tazzari2018) and `emcee`" (7 ALMA log and visibility model)
- **emcee** : MCMC for visibility and slab fits  
  > "The fitting is done using `emcee`" (4.1 Slab modeling procedure)
- **PyBaselines** : Baseline determination for MIRI spectrum  
  > "Finally, the baseline is determined using `PyBaselines` (cite: erb22)." (4.1 Slab modeling procedure)
- **JWST pipeline / VIP** 1.13.4 (CRDS context 1202): Hybrid MIRI MRS reduction  
  > "combining routines from the standard JWST pipeline (cite: bushouse_1.13.4) using CRDS context 1202, and from the VIP package" (2.1 JWST-MIRI)

## Numeric results

| quantity | value | uncertainty | units | step | quote |
|---|---|---|---|---|---|
| 1.3 mm flux DF Tau A | 2.00 | ±0.06 (3σ) | mJy | 2 | / 1.3 mm Flux \[mJy\] / $F_{A}$ / $2.00 \pm 0.06$ / |
| 1.3 mm flux DF Tau B | 2.00 | ±0.15 (3σ) | mJy | 2 | /  / $F_{B}$ / $2.00 \pm 0.15$ / |
| Dust mass A and B | 1.18 each | ±0.16 (A), ±0.18 (B) | Earth masses | 2 | / Dust Mass \[$M_{\oplus}$\] / $M_{dust,A}$ / $1.18 \pm 0.16$ / |
| GRAVITY separation | 65.9 | ±0.6 | mas | 3 | / $\rho$ \[mas\]             / $65.9 \pm 0.5$          / $65.9 \pm 0.6$           / |
| GRAVITY disk HWHM | 1.0 (0.14 au) | ±0.6 mas | mas | 3 | / HWHM \[mas\]               / \-                      / $1.0 \pm 0.6$            / |
| H2O component 1 temperature | 920 | ±10 | K | 4 | / H$_2$O #1 / 19.26$^{+0.03}_{-0.03}$ / 920$^{+10}_{-10}$ / 0.20$^{+0.002}_{-0.002}$ / 5.3$\times 10^{44}$ / |
| H2O component 3 temperature and radius | 180 K, 3.78 au | +10/-0 K; +1.027/-0.262 au | K, au | 4 | / H$_2$O #3 / 17.53$^{+0.09}_{-0.31}$ / 180$^{+10}_{-0}$ / 3.78$^{+1.027}_{-0.262}$ / 3.4$\times 10^{45}$ / |
| HCN temperature | 800 | ±20 | K | 4 | / HCN / 16.73$^{+0.22}_{-0.29}$ / 800$^{+20}_{-20}$ / 0.31$^{+0.110}_{-0.061}$ / 3.8$\times 10^{42}$ / |
| CO2 temperature | 400 | +10/-20 | K | 4 | / CO$_2$ / 18.78$^{+0.07}_{-0.06}$ / 400$^{+10}_{-20}$ / 0.21$^{+0.011}_{-0.009}$ / 1.8$\times 10^{44}$ / |

## Qualitative findings

- Two compact equal-brightness 1.3 mm sources detected; DF Tau B hosts a disk that moves consistent with its orbit, possibly with a ~1 au cavity  
  > "We interpret this as a robust detection of the disk around DF Tau B, which we suggest may host a small ($\sim$1 au) cavity" (abstract)

## Claim tuples

- H: Does DF Tau B host a circumstellar disk? | E: Visibility modeling of four ALMA epochs compared to GRAVITY astrometry and orbit | R: Two blobs >100σ, both ~2 mJy, moving as expected between LB1 and LB2 | F: The second blob is a disk around DF Tau B, possibly with a small cavity | **supported**
- H: Where does the MIRI molecular emission originate? | E: LTE slab fits plus GRAVITY, iSHELL and ALMA constraints | R: Hot H2O, HCN, C2H2 at >500 K and small radii; cold H2O (≲200 K) with extended area | F: Hot emission likely from DF Tau A; cold water from both disks | **partially**
- H: Does binarity change inner disk chemistry? | E: Compare slab results to isolated systems such as GW Lup | R: Similar CO2, HCN and H2O properties, but more complex water | F: Neither compact outer disks nor close binarity drive inner disk chemistry here | **supported**

## Reasoning

- Why this data: _not stated_
- Why this method: Simultaneous MCMC slab fit used because the water forest overlaps species too strongly for iterative fitting  
  > "the spectrum is so line-rich that there is too much overlap between species to allow for a good fit using that method" (4.1 Slab modeling procedure)
- Alternative: Circumbinary and two-disk GRAVITY models rejected (non-convergence, poorer fit)  
  > "The circumbinary model never converged making this possibility very unlikely" (3.2 VLTI-GRAVITY)
- How they decided it was enough: _not stated_
- Limitation (authors): ALMA emission only marginally resolved; disk geometry and sizes poorly constrained, cavity cannot be confirmed  
  > "we can neither conclusively confirm nor reject the presence of a cavity in the disk around DF Tau B" (3.1 discovery of a disk)
- Caveat (inferred, ours): Dust masses depend on assumed 20 K temperature and opacity
- Caveat (inferred, ours): MIRI emission cannot be assigned to A or B; attribution is inferred
- Caveat (inferred, ours): Inclination from ALMA (18.9 deg) conflicts with CO line profile (67 deg)
- Caveat (inferred, ours): Uncertainties are quoted at 3 sigma from marginally resolved data

## Reproducibility

- Data public (paper): Calibrated ALMA data posted on Zenodo; MIRI/iSHELL spectra on request/spexodisks  
  > "The calibrated ALMA data are publicly available[^5]." (2.2 ALMA)
- Products in archive: _not stated_
- Code: MINDS hybrid pipeline on GitHub  
  > "The pipeline and associated documentation are available at <https://github.com/VChristiaens/MINDS>" (footnote 2)
- Missing: Galario/emcee setup and priors
- Missing: Image parameters (cell, size, masks)
- Missing: Slab fit prior bounds
- Data volume (inferred): ~100 GB for four ALMA EBs raw; pseudo-continuum products are small
- Score (inferred): 3/5, ALMA data public and visibility analysis described, but fit priors and setup are missing, and the paper is multi-facility.
- Rediscovery candidate: no, ALMA recipe lacks fit details and main results span JWST, GRAVITY and iSHELL data.

## Links

- Method: (cite: tazzari2018) (galario visibility modeling)
- Method: (cite: temmink24a) (MIRI continuum subtraction and slab method)
- Method: (cite: andrews18) (continuum extraction)
- Companion: Kutra et al. in preparation (independent ALMA continuum, 12CO analysis and updated orbit)
- Companion: (cite: banzatti23a) (iSHELL data)
- Related: MINDS (JWST GTO 1282)

## Checks

```json
{
 "quotes": 72,
 "quotes_ok": 72,
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
  "facts": 80,
  "stated": 54,
  "rate": 0.675
 },
 "evidence_ok": true
}
```
