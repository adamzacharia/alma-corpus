# The kinematics of massive high-redshift dusty star-forming galaxies

`2025MNRAS.536.3757A` | Monthly Notices of the Royal Astronomical Society 2025 | first author: Amvrosiadis, A. | arXiv: 2312.08959 | DOI: 10.1093/mnras/stae2760

Card schema 1.0 | model claude-sonnet-5-5 | depth full | type observational_alma_primary

## Science

- Fields: high_z_galaxies
- Question: Can galaxy kinematics be modelled directly in visibility space for massive high-z DSFGs, and what do the results imply for alpha_CO, the Tully-Fisher relation and links to local early-type galaxies?  
  > "performing the optimization of the kinematic model parameters directly in visibility-space instead of the conventional approach of fitting velocity fields produced with the clean algorithm in real-space" (abstract)
- Target **ALESS DSFGs (30 sources in ECDFS, e.g. ALESS 122.1, 073.1)**: coordinates _not stated_; z/distance z ~ 1.2–4.7  
  > "We focus on the analysis of ALMA observations of sources located in the ECDFS field from that study, which are part of the ALESS survey" (2 Data); distance from CO-line spectroscopic redshifts from Birkin et al. 2021 and others  
  > "We focus on the analysis of ALMA observations of sources located in the ECDFS field from that study, which are part of the ALESS survey" (2 Data)

## Data provenance

- ALMA projects: 2016.1.00564.S, 2016.1.00754.S, 2017.1.01163.S, 2017.1.01512.S, 2017.1.01471.S
- bands: _not stated_
- frequencies and spectral setup: _not stated_
- continuum bandwidth: _not stated_
- arrays: _not stated_
- configurations: _not stated_
- baselines: _not stated_
- angular resolution: ~0.5 arcsec best (ALESS 122.1); ~1 arcsec average in main sample; ~0.1 arcsec for ALESS 073.1  
  > "observed uv-coverage of ALESS 122.1, which achieves a resolution of $\sim 0.5$ arcsec, the highest out of all datasets used in this study" (Simulations)
- max recoverable scale: _not stated_
- sensitivity: _not stated_
- time on source: _not stated_
- observing dates: _not stated_
- pi or archival as stated: _not stated_
- Line: 12CO J=2-1, 3-2 or 4-3 (source dependent) (not stated)
- Other facility **HST**: Archival H160 images of three sources to check for clumpy/merger morphology  
  > "For three of the sources we have archival HST observations in the $H_{160}$ band" (HST Morphologies)
- External data: Redshifts, stellar masses, gas masses, LIR, SFR of the sample  
  > "were taken from (cite: 2021MNRAS.501.3926B) or if not available, then from (cite: 2015ApJ...806..110D), (cite: 2018MNRAS.479.3879W) or (cite: 2018ApJ...863...56C)" (2.3 Properties) [from Birkin et al. 2021 (cite: 2021MNRAS.501.3926B); da Cunha 2015; Wardlow 2018; Calistro Rivera 2018]
- External data: KMOS3D comparison sample with Halpha kinematics  
  > "we also show SFGs in the redshift range $z=$ 1.8–2.7 from the KMOS$^{\rm 3D}$ survey (cite: 2019ApJ...886..124W)" (2.3 Properties) [from (cite: 2019ApJ...886..124W)]
- External data: Local early-type galaxy samples ATLAS3D and MASSIVE with velocity dispersions  
  > "we use samples of local massive early-type galaxies from two surveys, ATLAS$^{\rm 3D}$ (cite: 2011MNRAS.413..813C) and MASSIVE (cite: 2014ApJ...795..158M)" (4.4) [from (cite: 2011MNRAS.413..813C); (cite: 2014ApJ...795..158M)]
- External data: Local TFR slopes 3.60 (sTFR) and 3.75 (bTFR)  
  > "we adopt the local slopes of $\alpha = 3.60$ (cite: 2011MNRAS.417.2347R) and $\alpha = 3.75$ (cite: 2016ApJ...816L..14L), respectively" (4.3) [from (cite: 2011MNRAS.417.2347R); (cite: 2016ApJ...816L..14L)]
- Simulation/model as data: Simulated visibilities from Galpak3D disk models with ALESS 122.1 uv-coverage and real line-free noise, used to test parameter recovery  
  > "we use the observed visiblities for ALESS 122.1 in a spectral window where no emission line is observed. We treat these as the noise" (Simulations)

## Processing

### Calibration

- pipeline or manual: CASA standard pipelines provided with each dataset; weights recomputed with statwt  
  > "employing the standard pipelines provided with each dataset" (3.1 Data preparation)
- casa version: _not stated_
- pipeline version: _not stated_
- archive products used as is: _not stated_
- flux calibrator: _not stated_
- flux scale uncertainty: _not stated_
- self calibration: _not stated_

### Imaging

- task: Dirty cubes only for visualization; no clean used for modelling  
  > "Our method does not require any image preprocessing, such as the clean task from CASA" (Summary & Conclusions)
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
- array combination: _not stated_
- smoothing: _not stated_
- final beam: _not stated_
- final rms: _not stated_

### Inherited from earlier work

- alpha_CO estimation approach  
  > "Here we attempt to estimate $\alpha_{\rm CO}$ following the same approach as previous studies in the literature (cite: 2018ApJ...863...56C)" (4.2) [from (cite: 2018ApJ...863...56C)]
- Fixing TFR slope to local values, as in earlier high-z work  
  > "These are the same values that were used in (cite: 2017ApJ...842..121U) with which we want to eventually compare our results." (4.3) [from (cite: 2017ApJ...842..121U)]
- Gas mass derivation (line luminosities, excitation corrections from SMM J2135-0102)  
  > "The measured line luminosities of each transition were converted to CO(1$-$0) luminosities using the excitation corrections that were measured for SMM J2135$-$0102" (2.3 Properties) [from (cite: 2011MNRAS.410.1687D); (cite: 2021MNRAS.501.3926B)]

### Not stated but needed to reproduce (our reading)

- ALMA array configurations, spectral setups, channel widths and on-source times per project
- Per-source mapping of project codes to ALESS sources
- statwt time interval parameters
- Field-of-view and pixel size chosen per source for the NUFFT
- Nested sampler settings (live points, tolerance)
- Velocity channel ranges used in the manual masks
- Aperture used for integrated SNR
- Bootstrapping details for alpha_CO
- Priors for flux scaling and z-centre not fully given

## Analysis recipe

1. **Calibrate and prepare visibilities**: CASA pipeline calibration, export of unflagged visibilities, weights recomputed with statwt  
  > "We therefore recompute the weights of the calibrated visibilities using casa task statwt" (3.1 Data preparation)
   - software: CASA
   - fitting: _not stated_
   - validation: _not stated_
2. **Select sample by integrated SNR and classify**: Integrated SNR >8 cut; velocity maps from single-Gaussian fits per pixel of dirty cubes; visual classes  
  > "we found that the parameters of our model were effectively unconstrained when modelling sources with an integrated SNR $< 8$" (2.2)
   - fitting: _not stated_
   - validation: _not stated_
3. **Fit 3D thick rotating disk in uv-plane**: Galpak3D disk models (exponential flux, isothermal velocity profile, h_z=0.15 R_1/2) transformed by pyNUFFT per channel; Gaussian likelihood on visibilities  
  > "our model is comprised of 10 free parameters" (3.2)
   - software: Galpak3D, pyNUFFT, PyAutoFit, PyMultinest
   - parameter: Gaussian prior on centre (sigma 1 arcsec); uniform Vmax 0-600 km/s, sigma 0-200 km/s, r_e 0-2", r_t 0-1"  
  > "0 $\rm km \, s^{-1}$ \< $V_{\rm max}$ \< 600 $\rm km \, s^{-1}$; 0 $\rm km \, s^{-1}$ \< $\sigma$ \< 200 $\rm km \, s^{-1}$" (3.4)
   - fitting: Nested sampling with PyMultinest; median of marginalised posteriors, 68% intervals  
  > "we use a nested sampling Monte Carlo technique of Skilling (2006) implemented in the PyMultinest algorithm" (3.4)
   - validation: Simulated observations recover true parameters within 3 sigma; comparison with ALESS 122.1 and 073.1 literature  
  > "In general we find that we always recover the true input parameters within 3$\sigma$." (Simulations)
4. **Derive circularized velocity and dynamical mass**: V_circ corrected for asymmetric drift at 2 r_e; M_dyn = r V_circ^2/G within 10 kpc  
  > "the circularized velocity computed at a twice the effective radius and the dynamical mass computed within a radius of $r=$ 10 kpc" (4.1)
   - assumption: Constant velocity dispersion, exponential profile  
  > "Assuming a constant velocity dispersion profile and considering that the vertical profile of our thick disk model does not depend on the radius" (4.1)
   - fitting: _not stated_
   - validation: _not stated_
5. **Constrain alpha_CO**: Equate M_dyn to gas + stellar + dark matter mass; per-source values with bootstrapped errors, combined into joint constraint  
  > "We compute the value of $\alpha_{\rm CO}$ and its associated error (via bootstrapping) for each of the sources in our sample." (4.2)
   - assumption: f_dm = 0.25, r = 10 kpc, SED-fit stellar masses  
  > "we assume a fixed dark matter fraction, $f_{\rm dm} = 0.25$" (4.2)
   - fitting: _not stated_
   - validation: Varied f_dm  
  > "We also explored how the value of $\alpha_{\rm CO}$ changes when varying the adopted dark-matter fraction" (4.2)
6. **Fit Tully-Fisher relations**: Orthogonal distance regression with slope fixed to local value, fitting offset b  
  > "we use an orthogonal distance regression method taking into account the error in both the $x$ and $y$ coordinates (we use the scipy.odr package)" (4.3)
   - software: scipy.odr
   - fitting: ODR, slope fixed 3.60 (sTFR), 3.75 (bTFR)  
  > "For the sTFR and bTFR we adopt the local slopes of $\alpha = 3.60$ (cite: 2011MNRAS.417.2347R) and $\alpha = 3.75$ (cite: 2016ApJ...816L..14L), respectively." (4.3 Tully–Fisher relation at high redshift)
   - validation: Split in redshift at z~2.5  
  > "When splitting our sample in redshift, below and above $z \sim$ 2.5" (4.3)
7. **Place DSFGs on Mb-sigma plane and estimate space density**: Virial-mass equating of rotation- and dispersion-dominated phases to predict sigma; compare with ATLAS3D and MASSIVE; duty-cycle-corrected volume density  
  > "we can use the virial theorem (cite: 2009A&A...504..789E) and equate their virial masses at these two redshift epochs" (4.4)
   - assumption: All gas converted to stars; energy conserved; radius unchanged; beta ~5  
  > "we first need to make three assumptions" (4.4)
   - fitting: _not stated_
   - validation: _not stated_

## Software

- **CASA** : Calibration and statwt weight recomputation  
  > "The raw data were calibrated using the Common Astronomy Software Applications" (3.1 Data preparation)
- **Galpak3D** : 3D parametric rotating-disk models  
  > "We generate 3D parametric kinematical models of a thick rotating-disk using the publicly available software Galpak3D" (3.2)
- **pyNUFFT** : Non-uniform FFT of model cubes to visibilities  
  > "we use the publicly available software pyNUFFT" (3.3)
- **PyAutoFit** : Probabilistic programming framework for fitting  
  > "we use the publicly available software PyAutoFit" (3.4)
- **PyMultinest** : Nested sampling  
  > "implemented in the PyMultinest algorithm" (3.4)
- **scipy.odr** : TFR regression  
  > "we use the scipy.odr package" (4.3)
- **magphys** : SED fitting for stellar mass, LIR, SFR (from earlier work)  
  > "were computed using the spectral energy distribution (SED) fitting code magphys" (2.3 Properties)

## Numeric results

| quantity | value | uncertainty | units | step | quote |
|---|---|---|---|---|---|
| alpha_CO (f_dm=0.25) | 0.92 | 0.36 | dimensionless | 5 | Our approach yields an estimate of $\alpha_{\rm CO} = 0.92 \pm 0.36$, for a dark-matter fraction of, $f_{\rm dm} = 0.25$ |
| sTFR zero-point offset Δb | -0.53 | 0.29 | dimensionless | 6 | $\Delta b = -0.53 \pm 0.29$ and $\Delta b = -0.26 \pm 0.19$ for the sTFR and bTFR, respectively |
| bTFR zero-point offset Δb | -0.26 | 0.19 | dimensionless | 6 | $\Delta b = -0.53 \pm 0.29$ and $\Delta b = -0.26 \pm 0.19$ for the sTFR and bTFR, respectively |
| Median baryonic mass of sample | 3.6e11 | 2.9e11 | Msun | 7 | $M_{\rm b}=($3.6$\pm$2.9$)\times 10^{11}$ M$_\odot$ and $\sigma=$ 186$\pm$59 km s$^{-1}$ |
| Median predicted sigma_e | 186 | 59 | km/s | 7 | $M_{\rm b}=($3.6$\pm$2.9$)\times 10^{11}$ M$_\odot$ and $\sigma=$ 186$\pm$59 km s$^{-1}$ |
| Disk-like fraction among SNR>8 sources | 12 of 20 | not stated | sources | 3 | We find that 12 of the 20 sources that satisfy our SNR selection criteria |

## Qualitative findings

- DSFGs lie on the high-mass end of the Tully-Fisher relations of typical star-forming galaxies.  
  > "Our DSFGs occupy the high-mass end of these relations, but have normalisations that are consistent with those measured for the KMOS$^{\rm 3D}$ sources." (Summary & Conclusions)

## Claim tuples

- H: Massive DSFGs prefer a starburst-like alpha_CO | E: Dynamical mass minus stellar and dark matter mass divided by L_CO(1-0) | R: alpha_CO = 0.92 ± 0.36 | F: Consistent with starburst values | **supported**
- H: Disk-like DSFGs follow the TFR of typical SFGs | E: ODR fit with fixed local slopes | R: Δb = -0.53±0.29 (sTFR), -0.26±0.19 (bTFR) | F: They extend the TFR to higher masses | **supported**
- H: DSFGs are progenitors of local massive early-type galaxies | E: Mb–sigma plane comparison and space densities | R: Median within ~1σ of z~0 trend; density 4–5e-5 Mpc^-3 | F: Supports an evolutionary link | **supported**

## Reasoning

- Why this data: _not stated_
- Why this method: uv-plane fitting gives well-defined Gaussian errors and avoids clean-dependent preprocessing  
  > "because the errors on the visibilities are well defined (i.e., Gaussian errors)" (Summary & Conclusions)
- Alternative: Gaussian flux and Freeman velocity profiles tried for complex sources; same unphysical behaviour  
  > "we also tried different functional forms for both the flux profile (e.g., Gaussian) and the velocity profile (e.g., Freeman model)" (3.5)
- How they decided it was enough: _not stated_
- Limitation (authors): Modest resolution may misclassify mergers as disks  
  > "the modest resolution of our data can lead, in some cases, to a misclassification of mergers as disks" (Summary & Conclusions)
- Caveat (inferred, ours): Fixed f_dm=0.25 and SED stellar masses drive alpha_CO; the result is degenerate with these
- Caveat (inferred, ours): Only 12 sources, small TFR sample with fixed slope
- Caveat (inferred, ours): Disk thickness hard-coded; simple isothermal disk model
- Caveat (inferred, ours): Descendant argument rests on strong assumptions

## Reproducibility

- Data public (paper): ALMA data in the ALMA Science Archive  
  > "The ALMA data that were used in this study are available from the ALMA Science Archive" (DATA AVAILABILITY)
- Products in archive: _not stated_
- Code: Own Python routines not released; dependencies public  
  > "for further analysis with our own PYTHON routines" (3.1 Data preparation)
- Missing: Custom uv-plane fitting code not stated as released
- Missing: Per-source configuration and masks
- Missing: Table values (properties) from external papers
- Data volume (inferred): ~50-200 GB raw for ~30 sources
- Score (inferred): 3/5, Public data and a clear method, but custom code is unreleased and many settings are unstated.
- Rediscovery candidate: no, Custom code is unreleased and inputs depend on external catalogs.

## Links

- Method: Bouché et al. 2015 (cite: 2015AJ....150...92B) (Galpak3D model)
- Companion: Birkin et al. 2021 (cite: 2021MNRAS.501.3926B) (Parent sample and properties)
- Companion: Calistro Rivera et al. 2018 (cite: 2018ApJ...863...56C) (Prior image-plane modelling of ALESS 122.1 and alpha_CO method)
- Related: ALESS
- Related: LESS
- Related: KMOS3D
- Related: ATLAS3D
- Related: MASSIVE
- Related: AS2UDS

## Checks

```json
{
 "quotes": 60,
 "quotes_ok": 60,
 "quote_pass_rate": 1.0,
 "quotes_too_long": 0,
 "unsupported_facts": 0,
 "project_codes": 5,
 "codes_not_in_text": [],
 "codes_not_in_obscore": [],
 "obscore_codes_not_in_card": [],
 "codes_printed_but_missing": [],
 "numeric_results": 6,
 "numeric_problems": 0,
 "fill": {
  "facts": 88,
  "stated": 44,
  "rate": 0.5
 },
 "evidence_ok": true
}
```
