# ALMA Reveals Bright Circumgalactic Emission and a Biconical Outflow in z ∼ 6.4 Quasar PSOJ183+05

`2025ApJ...990L..31B` | The Astrophysical Journal Letters 2025 | first author: Bischetti, Manuela | arXiv: 2504.15357 | DOI: 10.3847/2041-8213/ade6ff

Card schema 1.0 | model claude-sonnet-5-5 | depth full | type archival_reuse

## Science

- Fields: high_z_galaxies, agn_and_quasars
- Question: Does combining multi-configuration archival ALMA data reveal extended [CII] emission (CGM) and a high-velocity outflow in the z~6.4 quasar PSOJ183+05 that high-resolution data alone miss?  
  > "We combined archival observations acquired with different antenna configurations, to boost the detectability of diffuse cold gas with respect to previous studies and, at the same time, map it with high angular resolution." (Introduction)
- Target **PSOJ183+05**: coordinates RA 12:12:26.974, Dec +05:05:33.540  
  > "| RA                                            | 12:12:26.974        |" (Table 1); "| $z_{\rm [CII]}$                               | 6.4388$\pm$0.0004   |" (Table 1); z/distance z_[CII] = 6.4388±0.0004  
  > "| RA                                            | 12:12:26.974        |" (Table 1); "| $z_{\rm [CII]}$                               | 6.4388$\pm$0.0004   |" (Table 1); distance from [CII] redshift measured in this work (Table 1)  
  > "| RA                                            | 12:12:26.974        |" (Table 1); "| $z_{\rm [CII]}$                               | 6.4388$\pm$0.0004   |" (Table 1)

## Data provenance

- ALMA projects: 2015.1.01115.S, 2019.1.01633.S, 2016.1.00544.S, 2021.1.01082.S
- bands: Band 6 continuum; [CII] line  
  > "targeting \[CII\] and band 6 continuum emission" (ALMA Observations and Data analysis)
- frequencies and spectral setup: continuum spws cover 237.7-242.8 and 252.7-257.9 GHz  
  > "covering the observed frequencies $237.7-242.8$ and $252.7-257.9$ GHz" (ALMA Observations and Data analysis)
- continuum bandwidth: _not stated_
- arrays: _not stated_
- configurations: _not stated_
- baselines: _not stated_
- angular resolution: ~1.1", ~0.3", ~0.12" for the three datasets; combined beam 0.13x0.12 arcsec^2  
  > "The resulting synthesized beam for the spectral window including \[CII\] is 0.13$\times$0.12 arcsec$^2$" (ALMA Observations and Data analysis)
- max recoverable scale: _not stated_
- sensitivity: [CII] cube rms 0.095 mJy/beam per 30 km/s channel; continuum rms 6.6 uJy/beam  
  > "the rms sensitivity of the continuum map is $\sigma_{\rm cont}=6.6$ $\mu$Jy beam$^{-1}$" (ALMA Observations and Data analysis)
- time on source: _not stated_
- observing dates: _not stated_
- pi or archival as stated: archival data; PIs Neeleman, Banados, Walter  
  > "We analyse archival ALMA observations of PSOJ183$+$05" (ALMA Observations and Data analysis)
- Line: [CII] 158 um (1900.537 GHz)
- External data: Dynamical mass ~1.3e11 Msun within inner 4 kpc (escape velocity ~700 km/s)  
  > "(cite: Neeleman21) reported a dynamical mass $M_{\rm dyn}\sim1.3\times10^{11}$ $\rm M_{\odot}$ in the inner 4 kpc around the quasar" (4.1 The [CII] outflow in PSOJ183+05) [from (cite: Neeleman21)]
- External data: SFR ~650-890 Msun/yr assuming 50% quasar contribution to dust heating  
  > "SFR $\sim650-890$ $\rm M_{\odot}$ yr$^{-1}$ measured in the host galaxy of PSOJ183$+$05" (4.1 The [CII] outflow in PSOJ183+05) [from (cite: Duras17; Decarli23; Tripodi24sfr)]
- External data: OH molecular outflow, median velocity 530 km/s, rate ~75-800 Msun/yr  
  > "with a median velocity of 530 km/s and an outflow rate of about 75-800 M$_\odot$ yr$^{-1}$" (Introduction) [from (cite: Butler23)]

## Processing

### Calibration

- pipeline or manual: standard ALMA observatory calibration with default phase, bandpass and flux calibrators  
  > "Visibilities were calibrated using the standard calibration provided by the ALMA observatory and the default phase, bandpass and flux calibrators." (ALMA Observations and Data analysis)
- casa version: CASA 6.4.0 (analysis); version 6.6.5 for concat  
  > "We merged the visibilities from the three datasets using CASA (version 6.6.5) task *concat*." (ALMA Observations and Data analysis)
- pipeline version: _not stated_
- archive products used as is: _not stated_
- flux calibrator: _not stated_
- flux scale uncertainty: _not stated_
- self calibration: _not stated_

### Imaging

- task: tclean  
  > "A continuum-subtracted datacube was created using CASA task $tclean$" (ALMA Observations and Data analysis)
- deconvolver: hogbom, non-interactive, threshold 2x rms  
  > "with the $hogbom$ cleaning algorithm in non-interactive mode, a threshold equal to two times the rms sensitivity" (ALMA Observations and Data analysis)
- weighting robust: natural weighting  
  > "a natural weighting of the visibilities" (ALMA Observations and Data analysis)
- uv taper: _not stated_
- cell size: _not stated_
- image size: _not stated_
- masking: _not stated_
- multiscale scales: _not stated_
- continuum subtraction: uv-plane first-order polynomial fit to channels with |v|>1000 km/s  
  > "performed a fit in the $uv$ plane to channels with $|v|>1000$ km s$^{-1}$, using a first-order polynomial continuum" (ALMA Observations and Data analysis)
- line free channels: _not stated_
- primary beam correction: _not stated_
- array combination: concat of visibilities from three configurations  
  > "We merged the visibilities from the three datasets using CASA (version 6.6.5) task *concat*." (ALMA Observations and Data analysis)
- smoothing: _not stated_
- final beam: 0.13x0.12 arcsec^2  
  > "The resulting synthesized beam for the spectral window including \[CII\] is 0.13$\times$0.12 arcsec$^2$" (ALMA Observations and Data analysis)
- final rms: 0.095 mJy/beam per 30 km/s channel  
  > "$\sigma_{\rm 30}=0.095$ mJy beam$^{-1}$ for a 30 km s$^{-1}$ channel width" (ALMA Observations and Data analysis)

### Inherited from earlier work

- [CII] brightness profile in annuli computed following earlier method  
  > "calculated following the method described in (cite: Tripodi22; Bischetti24)" (4.2 Bright CGM emission and feedback) [from (cite: Tripodi22; Bischetti24)]
- Atomic outflow mass from Eq. (1) of Hailey-Dunsheath10, T=200 K  
  > "according to Eq. (1) in (cite: Hailey-Dunsheath10), for a gas temperature $T=200$K" (4.1 The [CII] outflow in PSOJ183+05) [from (cite: Hailey-Dunsheath10)]
- Conical-wind mass outflow rate relation  
  > "by applying the relation for a conical wind $\dot{M}_{\rm of}=\Omega\frac{M_{\rm of}v_{\rm max}}{r_{\rm of}}f$ (cite: Bischetti19pds; Bischetti17; Cicone15)" (4.1 The [CII] outflow in PSOJ183+05) [from (cite: Bischetti19pds; Bischetti17; Cicone15)]

### Not stated but needed to reproduce (our reading)

- Which spectral windows/baseband and line-free channels exactly used per dataset
- Primary-beam correction and image/cell size
- Pixel-fit details (fitting algorithm, S/N handling, how the broad component amplitude limit and widths were enforced)
- Flux scale offsets between datasets/execution blocks and any uv weighting between configurations
- Moment map clipping thresholds and mask for outflow maps
- Details of [CII] luminosity and atomic mass conversions
- Exact solid angle map for bicone and how uncertainty propagated
- Quasar-position-centred radii/annuli definition code

## Analysis recipe

1. **Combine and calibrate multi-configuration data**: Standard ALMA calibration of three archival datasets, merged with concat  
  > "We merged the visibilities from the three datasets using CASA (version 6.6.5) task *concat*." (ALMA Observations and Data analysis)
   - software: CASA
   - fitting: _not stated_
   - validation: Individual datasets imaged separately for comparison  
  > "By imaging the individual datasets following the approach in Sect. [2](#sect:data), we verified that this is due to the increased sensitivity" (3 Continuum and [CII] emission)
2. **Continuum map and continuum subtraction, line cube**: Continuum averaged over spws excluding [CII]; uv-plane linear fit; tclean cube at 30 km/s  
  > "We adopted a 30 km s$^{-1}$ channel width." (ALMA Observations and Data analysis)
   - software: CASA tclean
   - parameter: channels |v|>1000 km/s for fit; hogbom; natural weighting  
  > "channels with $|v|>1000$ km s$^{-1}$, using a first-order polynomial continuum" (ALMA Observations and Data analysis)
   - fitting: _not stated_
   - validation: _not stated_
3. **Pixel-by-pixel two-Gaussian spectral decomposition and moment maps**: Fit systemic (FWHM<500 km/s) plus broad (FWHM>500 km/s, amplitude <=20% of systemic) Gaussians to pixels >3 sigma  
  > "a second broad Gaussian with a FWHM$>500$ km s$^{-1}$, to account for possible high-velocity wings in the line profile." (ALMA Observations and Data analysis)
   - parameter: broad amplitude limited to 20% of systemic  
  > "The amplitude of this broad component is limited at maximum 20% of the systemic component" (ALMA Observations and Data analysis)
   - assumption: Narrow width limit based on previous line widths (Venemans20)  
  > "based on previous line width measurements (cite: Venemans20)" (ALMA Observations and Data analysis)
   - fitting: _not stated_
   - validation: _not stated_
4. **Size measurement of continuum and [CII]**: 2D Gaussian fits of maps; one vs two-Gaussian components with residual inspection  
  > "No significant residuals are obtained by fitting a two Gaussians model" (3 Continuum and [CII] emission)
   - fitting: 2D Gaussian profile fits  
  > "By fitting the \[CII\] map with a 2D Gaussian profile, we find a deconvolved FWHM size" (3 Continuum and [CII] emission)
   - validation: Residual maps; comparison with high-resolution-only dataset  
  > "by extracting the \[CII\] brightness profile of PSOJ183$+$05 from the high-resolution dataset alone" (4.2 Bright CGM emission and feedback)
5. **Outflow mass, rate and energetics**: v_max=|v_mom1|+2 sigma_v of broad component; atomic mass from Hailey-Dunsheath10; Mdot=Omega M v/r f per pixel; kinetic power  
  > "We calculate the maximum velocity as $v_{\rm max}=|v_{\rm mom1}^{\rm broad}|+2\sigma_v^{\rm broad}$" (4.1 The [CII] outflow in PSOJ183+05)
   - parameter: Omega~1/2 (opening angle ~120 deg), f~1, r_of = beam radius in centre  
  > "We consider $\Omega\sim1/2$ (corresponding to a bicone opening angle of about 120 deg, Fig. [2](#fig:maps)d) and $f\simeq1$." (4.1 The [CII] outflow in PSOJ183+05)
   - assumption: PDR excitation, T=200 K, density >> critical  
  > "in the assumption that most of \[CII\] is excited by photodissociation regions" (4.1 The [CII] outflow in PSOJ183+05)
   - fitting: _not stated_
   - validation: Uncertainty dominated by opening angle (+-20 deg)  
  > "where the uncertainty is dominated by that on the bicone opening angle (about $\pm20$ deg)" (4.1 The [CII] outflow in PSOJ183+05)

## Software

- **CASA** 6.4.0 (6.6.5 for concat): calibration, concat, continuum subtraction, tclean imaging  
  > "using CASA 6.4.0 software" (ALMA Observations and Data analysis)
- **astropy** : listed in software section  
  > "astropy (cite: Astropy13; Astropy18; Astropy22)," (Software)

## Numeric results

| quantity | value | uncertainty | units | step | quote |
|---|---|---|---|---|---|
| Continuum flux density | 3.53 | 0.04 | mJy | 2 | / $S_{\rm cont}$ \[mJy\]                        / 3.53$\pm$0.04       / |
| [CII] line flux | 10.10 | 0.25 | Jy km/s | 3 | / $S_{\rm [CII]}$ \[Jy km s$^{-1}$\]            / 10.10$\pm$0.25      / |
| [CII] luminosity | 1.09e10 | 0.03e10 | Lsun | 3 | / L$_{\rm [CII]}$ \[10$^{10}$L$_\odot$\]        / 1.09$\pm$0.03       / |
| Continuum deconvolved size | 0.23x0.21 | 0.01 | arcsec | 4 | we infer a deconvolved size of ($0.23\pm0.01$) $\times$ ($0.21\pm0.01$) arcsec$^2$ |
| [CII] extended component FWHM | 1.03 (~5.8 kpc) | 0.04 | arcsec | 4 | plus an extended component with a FWHM of (1.03 $\pm 0.04$) arcsec, corresponding to about 5.8 kpc |
| Outflow atomic mass | 5.4e9 | 0.04e10 (Table) | Msun | 5 | we calculate the outflowing atomic gas mass ${M}_{\rm of}\sim5.4\times10^{9}$ $\rm M_{\odot}$ |
| Mass outflow rate | 930 | +330/-290 | Msun/yr | 5 | $\dot{M}_{\rm of}=930^{+330}_{-290}$ $\rm M_{\odot}$ yr$^{-1}$ |
| Outflow kinetic power | 8.3e43 | not stated | erg/s | 5 | $\sim8.3\times10^{43}$ erg s$^{-1}$, corresponding to about 0.5% of $L_{\rm Bol}$ |
| Fraction of [CII] emission missed by high-res dataset alone | ~55% | not stated | percent | 4 | we find that about 55% of the total \[CII\] emission and 100% of the emission beyond a 2 kpc radius is not recovered |

## Qualitative findings

- Biconical high-velocity [CII] outflow extends to ~5 kpc in NE-SW direction with elevated dispersion 150-200 km/s  
  > "An increased $\sigma_{\rm v}\sim150-200$ km s$^{-1}$ is observed in a biconical region centered on the quasar and extending out to $\sim5$ kpc" (3 Continuum and [CII] emission)

## Claim tuples

- H: Combining multi-configuration data reveals extended [CII] (ISM-CGM interface) in a z~6.4 quasar | E: Concatenated three configurations, 2D Gaussian fits and radial profile | R: Extended component FWHM ~5.8 kpc; ~50% of [CII] beyond 0.5" | F: Extended [CII] likely traces ISM/CGM interface | **supported**
- H: A high-velocity [CII] outflow exists | E: Two-Gaussian pixel decomposition, v_max, mass outflow rate | R: Mdot ~930 Msun/yr, v_max up to ~1000-1200 km/s | F: Quasar-driven outflow reaches CGM with delayed feedback without quenching ISM star formation | **supported**
- H: High-resolution data alone miss extended emission and outflow | E: Compare spectra and profiles from high-resolution dataset alone | R: ~55% of total flux and all emission beyond 2 kpc missed | F: May explain conflicting literature results | **supported**

## Reasoning

- Why this data: Multi-configuration data boost sensitivity to diffuse gas while keeping good resolution  
  > "Combining visibilities acquired from different antenna configurations allows us to maximise the sensitivity to possible extended \[CII\] emission" (ALMA Observations and Data analysis)
- Why this method: _not stated_
- Alternative: Galaxy interaction disfavoured: symmetric structure and no double-peaked continuum or disturbed morphology  
  > "Other processes such as galaxy interactions are disfavoured as (i) they cannot reproduce such a symmetric structure with high $\sigma_{\rm v}$" (3 Continuum and [CII] emission)
- Alternative: Dataset 2021.1.01082.S not combined because limited spectral coverage hampers continuum modelling  
  > "its limited spectral coverage (velocities $|v|\lesssim1000$ km s$^{-1}$) with respect to the \[CII\] line would introduce high uncertainty" (ALMA Observations and Data analysis)
- How they decided it was enough: _not stated_
- Limitation (authors): Archival data are heterogeneous and unsuited for systematic CGM studies  
  > "the archival observations contains heterogenous observations in terms of angular resolution, sensitivity, and frequency coverage, which are not suited for a systematic study of CGM properties" (Conclusions)
- Caveat (inferred, ours): Broad-component amplitude capped at 20% and width limits may bias outflow flux
- Caveat (inferred, ours): Outflow mass assumes PDR origin and T=200 K; ionised gas would change it
- Caveat (inferred, ours): Extended [CII] may arise from PDRs or unresolved clumps rather than CGM
- Caveat (inferred, ours): Single source; outflow vs rotation disk separation model-dependent
- Caveat (inferred, ours): No flux-scale cross-check between datasets stated

## Reproducibility

- Data public (paper): Archival ALMA data  
  > "We analyse archival ALMA observations of PSOJ183$+$05" (ALMA Observations and Data analysis)
- Products in archive: _not stated_
- Missing: Fitting code for pixel-by-pixel decomposition
- Missing: Masks and moment-map thresholds
- Missing: Exact imaging parameters (cell, size, primary beam)
- Data volume (inferred): ~100-300 GB raw for four-dataset set; three used
- Score (inferred): 3/5, Public data and a clear outline, but key fitting and imaging details are not given.
- Rediscovery candidate: no, Recipe incomplete for the spectral decomposition and moment masking, so outputs can only be approximately reproduced.

## Links

- Method: (cite: Bischetti24) (Multi-configuration combination approach and radial profile method)
- Method: (cite: Hailey-Dunsheath10) (Atomic gas mass from [CII])
- Companion: (cite: Neeleman21) (Kinematic modelling of same source)
- Companion: (cite: Venemans20) (Previous [CII] study of PSOJ183+05)
- Related: MUSE program 112.262L.002
- Related: JWST GO 4912

## Checks

```json
{
 "quotes": 67,
 "quotes_ok": 67,
 "quote_pass_rate": 1.0,
 "quotes_too_long": 0,
 "unsupported_facts": 0,
 "project_codes": 4,
 "codes_not_in_text": [],
 "codes_not_in_obscore": [],
 "obscore_codes_not_in_card": [],
 "codes_printed_but_missing": [],
 "numeric_results": 9,
 "numeric_problems": 0,
 "fill": {
  "facts": 75,
  "stated": 46,
  "rate": 0.613
 },
 "evidence_ok": true
}
```
