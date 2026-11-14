# Multiphase Black Hole Feedback and a Bright [C II] Halo in a LoBAL Quasar at z ∼ 6.6

`2024ApJ...970....9B` | The Astrophysical Journal 2024 | first author: Bischetti, Manuela | arXiv: 2404.12443 | DOI: 10.3847/1538-4357/ad4a77

Card schema 1.0 | model claude-sonnet-5-5 | depth full | type archival_reuse

## Science

- Fields: agn_and_quasars, high_z_galaxies
- Question: What are the properties and energetics of the ionized (BAL) and cold atomic ([CII]) outflows in the z~6.6 LoBAL quasar J0923+0402, and does feedback shape its extended [CII] halo?  
  > "We perform the first multi-scale and multi-phase characterisation of black-hole driven outflows in the $z\sim6.6$ quasar J0923+0402 and assess how these winds impact the cold gas reservoir." (abstract)
- Target **J0923+0402**: coordinates RA 09:23:47.122, Dec +04:02:54.402  
  > "RA | 09:23:47.122" (Table 1); "$z_{\rm [CII]}$ | 6.6321$\pm$0.0003" (Table 1); z/distance z_[CII] = 6.6321 ± 0.0003  
  > "RA | 09:23:47.122" (Table 1); "$z_{\rm [CII]}$ | 6.6321$\pm$0.0003" (Table 1); distance from [CII] peak in the merged ALMA data (this work); consistent with Yang21  
  > "RA | 09:23:47.122" (Table 1); "$z_{\rm [CII]}$ | 6.6321$\pm$0.0003" (Table 1)

## Data provenance

- ALMA projects: _none stated_
- bands: Band 6 continuum, ~242-257 GHz, plus [CII]  
  > "band 6 continuum emission (observed frequency $\sim242-257$ GHz)" (2.2 ALMA data)
- frequencies and spectral setup: _not stated_
- continuum bandwidth: _not stated_
- arrays: _not stated_
- configurations: _not stated_
- baselines: _not stated_
- angular resolution: ~0.12 to 0.57 arcsec across datasets  
  > "with angular resolution varying from $\sim$0.12 to 0.57 arcsec" (2.2 ALMA data)
- max recoverable scale: _not stated_
- sensitivity: [CII] cube rms 7.8e-5 Jy/beam per 30 km/s channel; continuum rms 5.9e-6 Jy/beam  
  > "rms sensitivity $7.8\times10^{-5}$ Jy beam$^{-1}$ for a 30 km s$^{-1}$ channel width" (2.2 ALMA data)
- time on source: _not stated_
- observing dates: _not stated_
- pi or archival as stated: Archival; PIs F. Wang, B. Venemans, J. Yang  
  > "ADS/JAO.ALMA#2018.1.01188S (P.I. F. Wang), ADS/JAO.ALMA#2019.1.00111S (P.I. B. Venemans)" (Acknowledgements)
- Line: [CII] 158 um (1900.5369 GHz)
- Other facility **VLT/X-shooter (XQR-30)**: Rest-UV spectrum for the SimBAL BAL fit  
  > "acquired with the VLT/X-shooter spectrograph as part of the XQR-30 survey" (2.1 BAL data)
- Other facility **JWST NIRCam (GO 2078)**: Optical quasar position  
  > "based on JWST NIRCam observations (F200W filter, project GO 2078" (2.2 ALMA data)
- Other facility **SUBARU HSC**: Quasar position for comparison  
  > "We measure a $0.13"$ offset with respect to the quasar position from SUBARU Hyper Suprime-Cam (HSC) observations" (2.2 ALMA data)
- External data: Composite quasar template for unabsorbed emission  
  > "To model the unabsorbed quasar emission, we used the composite template spectrum from (cite: Bischetti23)." (2.1 BAL data) [from (cite: Bischetti23)]
- External data: L_Bol and M_BH of the quasar  
  > "log($L_{\rm Bol}/\rm erg\ s^{-1})=47.5$ and a black-hole mass log($M_{\rm BH}/\rm M_\odot)=9.4$ (cite: Yang21; Mazzucchelli23)" (1 Introduction) [from (cite: Yang21; Mazzucchelli23)]
- Simulation/model as data: Cloudy C17 ionic column-density grids (solar metallicity) used by SimBAL  
  > "uses the grids calculated from version C17 of *Cloudy* (cite: Ferland17), which assumes solar metallicity" (2.1 BAL data)

## Processing

### Calibration

- pipeline or manual: Standard ALMA calibration with default calibrators  
  > "Visibilities were calibrated using the standard calibration provided by the ALMA observatory and the default phase, bandpass and flux calibrators." (2.2 ALMA data)
- casa version: _not stated_
- pipeline version: _not stated_
- archive products used as is: _not stated_
- flux calibrator: _not stated_
- flux scale uncertainty: _not stated_
- self calibration: _not stated_

### Imaging

- task: CASA tclean, non-interactive  
  > "Continuum-subtracted datacubes were created using CASA task $tclean$, with the $hogbom$ cleaning algorithm in non-interactive mode" (2.2 ALMA data)
- deconvolver: hogbom  
  > "with the $hogbom$ cleaning algorithm in non-interactive mode" (2.2 ALMA data)
- weighting robust: natural  
  > "a natural weighting of the visibilities" (2.2 ALMA data)
- uv taper: _not stated_
- cell size: _not stated_
- image size: _not stated_
- masking: Clean threshold of 2x rms; channel width 30 km/s  
  > "a threshold equal to two times the rms sensitivity" (2.2 ALMA data)
- multiscale scales: _not stated_
- continuum subtraction: uv-plane first-order polynomial fit to channels |v|>750 km/s  
  > "performed a fit in the $uv$ plane to channels with $|v|>750$ km s$^{-1}$, using a first-order polynomial continuum" (2.2 ALMA data)
- line free channels: _not stated_
- primary beam correction: _not stated_
- array combination: Visibilities of the three datasets merged  
  > "we merged the visibilities from the three datasets" (2.2 ALMA data)
- smoothing: _not stated_
- final beam: 0.16"x0.15" ([CII]); 0.14"x0.13" (continuum)  
  > "The resulting synthesized beam is $0.16"\times0.15"$ for the spectral window including \[CII\]" (2.2 ALMA data)
- final rms: 7.8e-5 Jy/beam (30 km/s); continuum 5.9e-6 Jy/beam  
  > "and $0.14"\times0.13"$ for the continuum image (rms sensitivity $5.9\times10^{-6}$ Jy beam$^{-1}$)" (2.2 ALMA data)

### Inherited from earlier work

- X-shooter data reduction and calibration  
  > "Details on the data reduction and calibration are given in (cite: Bischetti22; Dodorico23)" (2.1 BAL data) [from (cite: Bischetti22; Dodorico23)]
- Radial [CII] brightness profile method  
  > "in circular annuli of $0.15"$ radius, following the method described in (cite: Tripodi22)" (3.3 Bright [CII] halo) [from (cite: Tripodi22)]
- Velocity-resolved SimBAL model  
  > "We use a velocity-resolved model for the BAL absorption features (cite: Leighly18; Choi20)" (2.1 BAL data) [from (cite: Leighly18; Choi20)]

### Not stated but needed to reproduce (our reading)

- Which ALMA array configurations, dates and exposure times per project
- CASA version used
- Image size and cell size for tclean
- Clean threshold in absolute units and number of iterations
- Relative weighting or flux scaling when merging the three datasets
- Exact aperture and velocity range defining the outflow [CII] flux and the 3-sigma isophote
- How the 2D Gaussian and continuum peak fits were done
- Velocity cut and region defining the blueshifted outflow emission
- SimBAL priors, fitting sampler and settings
- Software used for the ALMA moment maps and the radial profile

## Analysis recipe

1. **Fit BAL features with SimBAL**: Velocity-resolved spectral synthesis of 25 tophat bins fit to the X-shooter spectrum, rest-frame 1280-2900 A  
  > "We consider 25 bins with velocities spanning from $\sim-32,000\ \mathrm{km\ s^{-1}}$ to $\sim-6,800\ \mathrm{km\ s^{-1}}$" (2.1 BAL data)
   - software: SimBAL, Cloudy
   - parameter: Single log U; log N_H-log U and log a free per bin; density fixed at log n=6  
  > "we fixed the density at log$(n/\rm cm^{-3})=6$" (2.1 BAL data)
   - assumption: Solar metallicity grids  
  > "which assumes solar metallicity and spectral energy distribution (SED) of an ionizing spectrum" (2.1 BAL data)
   - fitting: Uncertainties from posterior probability distribution of model parameters  
  > "Uncertainties were calculated from the posterior probability distribution of model parameters." (2.1 BAL data)
   - validation: Best-fit parameters change <~0.15 dex for densities 2.8<log n<8  
  > "verified that the best-fit parameters do not significantly change ($\lesssim0.15$ dex)" (2.1 BAL data)
2. **Image ALMA [CII] cube and continuum**: Merge three datasets, fit uv continuum, tclean cubes at 30 km/s  
  > "For \[CII\] datacubes, we adopted a 30 km s$^{-1}$ channel width." (2.2 ALMA data)
   - software: CASA
   - fitting: _not stated_
   - validation: _not stated_
3. **Measure [CII] and continuum properties**: Spectrum from 3-sigma isophote, 2D Gaussian fits to [CII] map and continuum peaks; L_IR from continuum  
  > "Fitting a 2D Gaussian to the \[CII\] map gives a FWHM size of ($1.28\times0.92$) arcsec$^2$" (2.2 ALMA data)
   - assumption: Dust temperature 47 K, beta=1.6  
  > "assuming a typical dust temperature of 47 K and a dust emissivity index $\beta=1.6$" (2.2 ALMA data)
   - fitting: _not stated_
   - validation: _not stated_
4. **BAL wind radius and energetics**: Radius range from L_kin<L_Bol (upper) and log n<~8 via ionization parameter (lower); mass outflow rate from Eq. 9 of Dunn10 (thin shell)  
  > "We calculate the mass outflow rate from the best-fit $N_H$ and $v$ using Eq. (9) in (cite: Dunn10), which adopts a thin-shell geometry" (3.1 Wind location and energetics)
   - parameter: log Q=57.2 photons/s  
  > "in which $\log\ Q=57.2$ photons $\mathrm{s^{-1}}$ is the rate of photoionizing photons" (Appendix radius of BAL outflow)
   - assumption: mu=1.4, global covering Omega=0.2  
  > "assuming a mean molecular weight $\mu=1.4$, a global covering $\Omega=0.2$ (cite: Hewett03)" (3.1 Wind location and energetics)
   - fitting: _not stated_
   - validation: _not stated_
5. **[CII] outflow mass and energetics**: Atomic mass from Eq. 1 of Hailey-Dunsheath10; rate from Eq. 1 of Bischetti19pds for a shell, using max extent or bulk scale as radius  
  > "We compute the \[CII\] mass outflow rate using Eq. (1) in (cite: Bischetti19pds) for a shell-like outflow geometry" (3.1 Wind location and energetics)
   - assumption: C+ abundance 1.4e-4 per H, T=200 K, n>>n_crit (lower limit)  
  > "We assume a C$^+$ abundance of $1.4\times10^{-4}$ per hydrogen atom and a gas temperature of 200 K" (3.1 Wind location and energetics)
   - fitting: _not stated_
   - validation: T of 100-1000 K changes M_atom by only 20%  
  > "A temperature in the range 100-1000 K would imply a variation of only 20% in $M_{\rm atom}$." (3.1 Wind location and energetics)
6. **[CII] radial brightness profile**: Brightness in circular annuli of 0.15" radius, compared with stacked profiles  
  > "We calculate the brightness profile of \[CII\] emission in J0923$+$0402 in circular annuli of $0.15"$ radius" (3.3 Bright [CII] halo)
   - fitting: _not stated_
   - validation: _not stated_

## Software

- **SimBAL** : Fitting BAL features  
  > "We use the spectral-synthesis code *SimBAL* (cite: Leighly18) to fit the BAL features" (2.1 BAL data)
- **Cloudy** C17: Ionic column-density grids used by SimBAL  
  > "uses the grids calculated from version C17 of *Cloudy* (cite: Ferland17)" (2.1 BAL data)
- **CASA** : tclean imaging of cubes and continuum  
  > "Continuum-subtracted datacubes were created using CASA task $tclean$" (2.2 ALMA data)
- **astropy** : Listed in the software section  
  > "astropy (cite: Astropy13; Astropy18; Astropy22), Cloudy (cite: Ferland17), SimBAL (cite: Leighly18)" (Software)

## Numeric results

| quantity | value | uncertainty | units | step | quote |
|---|---|---|---|---|---|
| [CII] velocity-integrated flux | 5.94 | 0.35 | Jy km/s | 3 | $S_{\rm [CII]}$ \[Jy km s$^{-1}$\] / 5.94$\pm$0.35 |
| Continuum flux density (242-257 GHz) | 0.80 | 0.08 | mJy | 3 | $S_{\rm cont}$ \[mJy\] / 0.80$\pm$0.08 |
| [CII] redshift | 6.6321 | 0.0003 | dimensionless | 3 | $z_{\rm [CII]}$ / 6.6321$\pm$0.0003 |
| [CII] FWHM | 400 | 25 | km/s | 3 | FWHM$_{\rm [CII]}$ \[km s$^{-1}$\] / 400$\pm$25 |
| Ionization parameter log U | -0.32 | +0.01/-0.02 | dimensionless | 1 | $\log~U=-0.32^{+0.01}_{-0.02}$ |
| BAL total log N_H | 22.57 | +0.01/-0.02 | cm^-2 | 1 | $\log (N_H/\rm cm^{-2})=22.57^{+0.01}_{-0.02}$ |
| BAL mass outflow rate log | 1.89-3.7 | not stated | log(Msun/yr) | 4 | log($\dot{M}_{\rm BAL}/[\rm M_\odot\ yr^{-1}]$)  / $1.89-3.7$ |
| BAL wind radius | 3-210 | not stated | pc | 4 | $R_{\rm BAL}$ \[$\mathrm{pc}$\]                  / $3-210$ |
| BAL kinetic power log | 45.69-47.51 | not stated | log(erg/s) | 4 | log($\dot{E}_{\rm BAL}/[\rm erg\ s^{-1}]$)       / $45.69-47.51$ |
| [CII] outflow mass outflow rate | 150-640 | not stated | Msun/yr | 5 | This results in $\dot{M}_{\rm atom}\simeq150-640$ $M_\odot$ yr$^{-1}$ |
| Atomic outflow mass | 4.3e8 | not stated | Msun | 5 | we calculate an atomic gas mass $M_{\rm atom}\simeq4.3\times10^8$ $M_\odot$ |
| [CII] outflow radius | 520-2220 | not stated | pc | 5 | $R_{\rm [CII]}$ \[pc\]                        / $520-2,220$ |
| Quasar-to-companion continuum flux ratio | ~2.5:1 | not stated | dimensionless | 3 | find a quasar-to-companion flux ratio of $\sim2.5:1$ |
| Infrared luminosity 8-1000um | 2.4e12 | not stated | Lsun | 3 | $L_{\rm IR,8-1000\mu m}\simeq2.4\times10^{12}$ L$_{\odot}$ |

## Qualitative findings

- Most of the outflowing mass is in the neutral phase, while most of the outflow power is in the ionized phase  
  > "Most of the outflowing gas mass is carried by the neutral outflow" (3.2 Multiphase and multiscale outflow)
- About 50% of the [CII] emission arises beyond ~3.3 kpc  
  > "about 50% of the \[CII\] emission arising beyond a radius of $\simeq3.3$ kpc" (3.3 Bright [CII] halo)

## Claim tuples

- H: Does J0923+0402 host a powerful ionized BAL outflow? | E: SimBAL fit to X-shooter spectrum plus energetics | R: BAL kinetic power is 2-100% of L_Bol with a mass outflow rate of log 1.89-3.7 Msun/yr | F: The BAL wind is consistent with efficient quasar feedback | **supported**
- H: Is there a cold neutral outflow in the host? | E: High-velocity [CII] emission and velocity dispersion maps | R: Blueshifted [CII] at ~-300 to -500 km/s near the quasar, with sigma up to ~300 km/s | F: Likely a cold neutral outflow at ~0.5-2 kpc | **partially**
- H: Is the [CII] emission extended into a CGM-scale halo, and is feedback linked to it? | E: Radial [CII] brightness profile compared with stacked profiles | R: Halo of ~15 kpc, four times larger than the Novak20 stacked profile | F: Halo may be a remnant of feedback, but the link is not demonstrated | **partially**

## Reasoning

- Why this data: [CII] traces the galaxy-scale counterpart of the BAL wind and the impact on ISM and CGM  
  > "to trace the galaxy-scale counterpart of the BAL wind and assess the impact of black-hole activity on ISM and CGM properties" (1 Introduction)
- Why this method: _not stated_
- Alternative: Merger as the origin of the extended [CII] halo is questioned because the morphology is mostly symmetric  
  > "The above picture questions the merger as the main mechanism responsible for the extended \[CII\] halo" (3.3 Bright [CII] halo)
- How they decided it was enough: _not stated_
- Limitation (authors): The BAL gas density cannot be constrained, so the radius and energetics span wide ranges  
  > "the gas density ($\log {n}$) cannot be constrained from the spectral analysis" (Appendix radius of BAL outflow)
- Limitation (authors): The triangle-shaped blueshifted region may be a tidal feature  
  > "we cannot a priori exclude that the triangle-shaped region is associated with a tidal feature" (2.2 ALMA data)
- Caveat (inferred, ours): The [CII] outflow is a modest-velocity shoulder that is hard to separate from merger kinematics
- Caveat (inferred, ours): The mass outflow rates depend on assumed geometry, covering factor, temperature and density
- Caveat (inferred, ours): The halo interpretation lacks a quantitative profile fit and a model for the PSF/beam
- Caveat (inferred, ours): The BAL radius range spans ~2 dex, which limits the energetics constraints

## Reproducibility

- Data public (paper): Archival ALMA projects and JWST MAST data  
  > "We analyse archival ALMA observations of J0923$+$0402" (2.2 ALMA data)
- Products in archive: _not stated_
- Missing: Array configurations, CASA version, imaging grid parameters
- Missing: SimBAL priors and fit settings
- Missing: Aperture definitions for the outflow flux
- Missing: Quantitative details of the radial profile extraction
- Data volume (inferred): Three ALMA band 6 projects; likely tens of GB raw, a few GB as calibrated products
- Score (inferred): 5/5, Public data and clear outline, but many imaging, fitting and aperture details are missing and the SimBAL step needs X-shooter data.
- Rediscovery candidate: no, The recipe lacks details such as aperture definitions, outflow region and SimBAL settings, and the main results are partly ranges that depend on assumptions.

## Links

- Method: (cite: Leighly18) (SimBAL spectral synthesis code)
- Method: (cite: Choi20) (SimBAL version used)
- Method: (cite: Tripodi22) (Radial profile method)
- Companion: (cite: Bischetti22) (Discovery of the Lo-BAL wind in J0923+0402)
- Companion: (cite: Bischetti23) (BAL quasar sample and UV template)
- Companion: (cite: Yang21) (Earlier [CII] redshift measurement)
- Related: XQR-30
- Related: JWST GO 2078

## Checks

```json
{
 "quotes": 74,
 "quotes_ok": 74,
 "quote_pass_rate": 1.0,
 "quotes_too_long": 0,
 "unsupported_facts": 0,
 "project_codes": 0,
 "codes_not_in_text": [],
 "codes_not_in_obscore": [],
 "obscore_codes_not_in_card": [
  "2018.1.01188.S",
  "2019.1.00111.S",
  "2021.1.00934.S"
 ],
 "codes_printed_but_missing": [],
 "numeric_results": 14,
 "numeric_problems": 0,
 "fill": {
  "facts": 85,
  "stated": 52,
  "rate": 0.612
 },
 "evidence_ok": true
}
```
