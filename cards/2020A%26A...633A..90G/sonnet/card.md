# The ALPINE-ALMA [C II] survey: Star-formation-driven outflows and circumgalactic enrichment in the early Universe

`2020A&A...633A..90G` | Astronomy and Astrophysics 2020 | first author: Ginolfi, M. | arXiv: 1910.04770 | DOI: 10.1051/0004-6361/201936872

Card schema 1.0 | model claude-sonnet-5-5 | depth full | type large_program_or_survey

## Science

- Fields: high_z_galaxies
- Question: Do star-formation-driven outflows and circumgalactic enrichment show up in stacked [C II] spectra and cubes of normal galaxies at 4<z<6?  
  > "we explore the efficiency of star-formation-driven outflows through a stacking analysis of [C II] emission lines in a large sample of normal galaxies at $4 < z < 6$" (1 Introduction)
- Target **ALPINE [C II]-detected normal star-forming galaxies (50 used)**: coordinates _not stated_; z/distance 4.4 < z < 5.8  
  > "The final sample, drawn from ALPINE and used in this work, consists of 50 normal star-forming galaxies at redshift $4.4 < z < 5.8$" (3.1.2 Exclusion of possible contaminants); distance from optical spectroscopic redshifts (VLT VUDS, Keck-COSMOS), refined with [C II]  
  > "The final sample, drawn from ALPINE and used in this work, consists of 50 normal star-forming galaxies at redshift $4.4 < z < 5.8$" (3.1.2 Exclusion of possible contaminants)

## Data provenance

- ALMA projects: 2017.1.00428.L
- bands: Band 7  
  > "ALMA observations were carried out in Band 7 during Cycles 5 and 6, and completed in February 2019." (2 Sample and observations)
- frequencies and spectral setup: One spectral window centered on [C II]; other side bands for continuum  
  > "One spectral window was centered on the [C II] expected frequencies, according to the spectroscopic redshifts extracted from UV spectra, while other side bands were used for continuum measurements." (2 Sample and observations)
- continuum bandwidth: _not stated_
- arrays: _not stated_
- configurations: _not stated_
- baselines: _not stated_
- angular resolution: ~0.9" average circularized beam (0.8-1")  
  > "The typical angular resolution of the final products, computed as the average circularized beam axis, is 0.9$''$" (2 Sample and observations)
- max recoverable scale: _not stated_
- sensitivity: median ~0.35 mJy/beam per 25 km/s channel (range 0.2-0.55)  
  > "The median sensitivity (in the spectral regions close to [C II] frequencies) reached by the cubes in our sample is $\sim 0.35$ mJy/beam for a 25 km s$^{-1}$ spectral channel" (2 Sample and observations)
- time on source: 20 min to 1 hour per target  
  > "Each target was observed for between 20 minutes and 1 hour of exposure time," (2 Sample and observations)
- observing dates: _not stated_
- pi or archival as stated: ALMA large program, PI O. Le Fèvre  
  > "ALPINE is an ALMA large program (PI: O. Le Fèvre;" (2 Sample and observations)
- Line: [C II] 158 um (not stated)
- Other facility **VLT (VUDS) and Keck (Keck-COSMOS)**: optical spectroscopic redshifts  
  > "All galaxies have reliable optical spectroscopic redshifts coming from extensive campaigns at the Very Large Telescope (VUDS:" (2 Sample and observations)
- Other facility **Ancillary UV-FIR photometry (ground, HST, Spitzer)**: stellar masses and SFRs via SED fitting  
  > "Stellar masses and star formation rates are derived using a rich set of available ancillary data, including ground-based imaging observations from rest-frame UV to the optical, HST observations" (3.1.2)
- External data: Local starbursts Mdot_out vs SFR compilation  
  > "we show a comparison of our results with a compilation of local starbursts ((cite: Heckman2015))" (4 Discussion) [from Heckman2015]
- External data: Best-fitting Mdot_out-SFR relations for local AGN and star-forming galaxies  
  > "the best-fitting relations of local AGNs and normal star-forming galaxies from (cite: Fluetsch2019)" (4 Discussion) [from Fluetsch2019]
- External data: Stellar mass-halo mass relation  
  > "according to the SMHM relation by (cite: Behroozi2019), correspond to DM halos masses in the range" (4 Discussion) [from Behroozi2019]

## Processing

### Calibration

- pipeline or manual: CASA calibration with extra flagging of bad antennae in a few cases  
  > "additional flagging of bad antennae was performed in a few cases (see Béthermin et al. in prep.)." (2 Sample and observations)
- casa version: CASA 5.4.0  
  > "version 5.4.0" (2 Sample and observations)
- pipeline version: _not stated_
- archive products used as is: _not stated_
- flux calibrator: _not stated_
- flux scale uncertainty: _not stated_
- self calibration: _not stated_

### Imaging

- task: CASA clean; continuum MFS over line-free visibilities; cubes from continuum-subtracted visibilities  
  > "Continuum maps were obtained running the `CASA` task `clean` (multi-frequency synthesis mode) over the line-free visibilities in all spectral windows" (2 Sample and observations)
- deconvolver: clean with 500 iterations, S/N threshold 3 sigma  
  > "with 500 iterations and a S/N threshold of $\sigma_{\rm{clean}}=3$ in the `clean` algorithm." (2 Sample and observations)
- weighting robust: natural weighting  
  > "We chose a natural weighting of the visibilities" (2 Sample and observations)
- uv taper: _not stated_
- cell size: 0.15"  
  > "a common pixel size of 0.15$''$" (2 Sample and observations)
- image size: _not stated_
- masking: _not stated_
- multiscale scales: _not stated_
- continuum subtraction: _not stated_
- line free channels: _not stated_
- primary beam correction: _not stated_
- array combination: _not stated_
- smoothing: common spectral bin of 25 km/s  
  > "a common spectral bin of 25 km s$^{-1}$" (2 Sample and observations)
- final beam: stacked beam 0.98" x 0.89", PA -30 deg  
  > "major axis FWHM of $0.98''$, a minor axis FWHM of $0.89'',$ and a position angle of $-30$ deg." (footnote 8)
- final rms: _not stated_

### Inherited from earlier work

- Data reduction, imaging and [C II]/continuum extraction details  
  > "In Béthermin et al. in prep., we discuss in detail the methods adopted to extract continuum and $\rm [C~ II]$ information from ALPINE observations" (2 Sample and observations) [from Béthermin et al. in prep.]
- Merger/rotator morpho-kinematic classification  
  > "Such selection is based on a morpho-kinematic classification, described in detail in (cite: LeFevre2019a)" (3.1.2) [from (cite: LeFevre2019a)]
- SED-fitting stellar masses and SFRs  
  > "For further details we refer to Faisst et al. in prep." (3.1.2) [from Faisst et al. in prep.]
- Residual stacking procedure  
  > "We performed a simple standard procedure (see e.g., (cite: Gallerani2018)) described as follows:" (3.2 Combining the residuals) [from (cite: Gallerani2018)]
- Outflow mass relation  
  > "adopting the relation from (cite: Hailey2010)" (4 Discussion) [from (cite: Hailey2010)]

### Not stated but needed to reproduce (our reading)

- Line-free channels used for continuum subtraction
- Per-source spectral masks/rms values and the list of the 50 galaxies
- Initial guesses, bounds and fitter for the Gaussian fits
- Number of bootstrap realizations
- Aperture/size fit details for the stacked cube maps
- Exact SFR and stellar mass values per galaxy
- Which ALPINE data products (version) were used

## Analysis recipe

1. **Select sample and extract aligned spectra**: Exclude 25 merging systems from 75 detections; extract spectra in 2-sigma apertures of [C II] moment maps; align to Gaussian centroid frequency  
  > "we excluded from our analysis 25 objects (corresponding to $\sim30\%$ of the [C II]-detected ALPINE sample) with signs of ongoing major or minor mergers;" (3.1.2)
   - software: CASA
   - parameter: 25 km/s channels; cubes centered on brightest pixel  
  > "We also spatially align the [C II] cubes, centering them on the brightest pixel of [C II] velocity-integrated maps." (3.1.1)
   - fitting: _not stated_
   - validation: repeated with phase center as reference; identical within errors  
  > "the results of cube-stacking are identical within the errors." (footnote 3)
2. **Stack residuals of single-Gaussian fits**: Fit single Gaussian per spectrum, subtract, variance-weighted stack (w=1/sigma^2, sigma from channels outside +-800 km/s); repeat for SFR<25 and >=25  
  > "we combine the residuals performing a variance-weighted stacking:" (3.2)
   - parameter: SFR median split 25 Msun/yr  
  > "we use the median SFR of galaxies in our sample (SFR$_{med} = 25$ ${\rm M_{\odot}}$ yr$^{-1}$" (3.2)
   - fitting: single Gaussian, free peak, center, FWHM  
  > "where the peak flux, center velocity" (3.2)
   - validation: 3BAROLO tilted-ring test on five rotators shows rotation affects only about -225 to +275 km/s  
  > "only affecting the velocity range $v \sim [-225 : + 275]$ km s$^{-1}$" (3.2.1)
3. **Stack spectra and fit two-component Gaussian**: Variance-weighted stack; single vs narrow+broad Gaussian fits; bootstrap for FWHM uncertainty; fixed 4x4 pixel aperture test  
  > "We performed a bootstrap analysis to estimate the possible effect of contamination from a few individual sources" (3.3)
   - software: 3DBAROLO
   - fitting: Gaussian fits; uncertainties = sigma of bootstrapped FWHM distributions  
  > "we adopt the $\sigma$ of the bootstrapped FWHM distributions" (3.3)
   - validation: Two-Gaussian residuals consistent with noise; bootstrap peaks match  
  > "a two-component Gaussian fit can accurately describe the stacked spectrum" (3.3)
4. **Stack cubes and measure extent**: Variance-weighted cube stack; collapse [-200,200] and 200-600 km/s; radial SB profiles vs PSF and stacked continuum; median stack check  
  > "We then collapsed the spectral slices of the [C II] stacked cubes in the velocity ranges (i) $[-200: +200]$ km s$^{-1}$" (3.4)
   - fitting: 2D Gaussian for beam-deconvolved sizes  
  > "We calculated beam-deconvolved sizes by fitting a 2D Gaussian model" (footnote 9)
   - validation: Median stacking gives no evident deviations  
  > "We do not find evident deviations, confirming that our findings are not affected by outliers in the distribution." (3.4)
5. **Derive outflow mass, rate, loading factor and escape velocity**: Hailey-Dunsheath [C II] mass relation, Mdot=v M/R, x3 multi-phase correction, SMHM-based v_esc  
  > "We then compute the atomic $\dot{M}_{\rm out}$ assuming time-averaged expelled shells or clumps" (4 Discussion)
   - parameter: v_out~500 km/s, R_out~6 kpc  
  > "We adopt $v_{\rm out} \sim 500$ km s$^{-1}$" (4 Discussion)
   - assumption: n>n_crit, X_C+=1.4e-4, T=60-200 K, 70% of [C II] from PDRs, optically thin  
  > "a gas temperature in the range" (4 Discussion)
   - fitting: _not stated_
   - validation: _not stated_

## Software

- **CASA** 5.4.0: calibration and imaging  
  > "The data were calibrated using the Common Astronomy Software Applications package" (2)
- **3DBAROLO** : tilted-ring kinematic models of five rotators  
  > "we use $^{\rm 3D}$`BAROLO`" (3.2.1)
- **LePhare** : SED fitting for M* and SFR  
  > "using the `LePhare` code" (3.1.2)

## Numeric results

| quantity | value | uncertainty | units | step | quote |
|---|---|---|---|---|---|
| Narrow FWHM, full sample | 233 | 15 | km/s | 3 | FHWM - narrow / $233 \pm 15$ km s$^{-1}$ |
| Broad FWHM, full sample | 531 | 90 | km/s | 3 | FHWM - broad / $531 \pm 90$ km s$^{-1}$ |
| Narrow FWHM, high-SFR | 251 | 10 | km/s | 3 | narrow (FWHM = $251 \pm 10$ km s$^{-1}$) |
| Broad FWHM, high-SFR | 684 | 75 | km/s | 3 | broad (FWHM = $684 \pm 75$ km s$^{-1}$) |
| Outflowing atomic gas mass, full sample | 2.1e8 | 0.8e8 | Msun | 5 | $M_{\rm out}^{\rm atom} = (2.1 \pm 0.8) \times 10^8 ~{\rm M_{\odot}}$ |
| Outflowing atomic gas mass, high-SFR | 2.9e8 | 1.2e8 | Msun | 5 | $M_{\rm out}^{\rm atom} = (2.9 \pm 1.2) \times 10^8 ~{\rm M_{\odot}}$ for the high-SFR subsample |
| Mass outflow rate, full sample | 18 | 5 | Msun/yr | 5 | $\dot{M}_{\rm out} = 18\pm5$ ${\rm M_{\odot}}$ yr$^{-1}$ for the full sample |
| Mass outflow rate, high-SFR | 25 | 8 | Msun/yr | 5 | $\dot{M}_{\rm out} = 25\pm8$ ${\rm M_{\odot}}$ yr$^{-1}$ for the high-SFR subsample |
| Atomic mass-loading factor | 0.3-0.9 | not stated | dimensionless | 5 | ($\eta^{\rm atom}\sim0.3 - 0.9$) |
| Escape velocity of halos | 400-800 | not stated | km/s | 5 | we find typical escapes velocities of $v_{\rm esc}\sim 400 - 800$ km s$^{-1}$ |
| High-velocity [C II] size | ~0.9" (~6 kpc) | not stated | arcsec | 4 | extending on beam-deconvolved [^9] angular sizes of $\sim0.9''$ |

## Qualitative findings

- Stacked [C II] shows broad wings that strengthen with SFR; extended ~30 kpc [C II] halo in high-SFR galaxies  
  > "extends over physical sizes of $\sim$ 30 kpc (diameter scale)" (5 Conclusions)

## Claim tuples

- H: Normal z~5 galaxies show SF-driven outflow wings in [C II] | E: Stacked residuals and spectra of 50 ALPINE galaxies | R: Two-Gaussian fit needed; broad FWHM 531 km/s, 684 km/s for high-SFR | F: Outflows present and stronger at higher SFR | **supported**
- H: SF-driven outflows are efficient quenchers | E: Mass outflow rates and loading factors | R: eta_atom 0.3-0.9, eta_tot 1-3 | F: Less efficient than AGN feedback | **supported**
- H: Enriched CGM exists around normal high-z galaxies | E: Cube stacking and radial profiles | R: Extended core emission ~30 kpc in high-SFR | F: Metal-enriched circumgalactic halos | **supported**

## Reasoning

- Why this data: _not stated_
- Why this method: Individual spectra too weak, so stacking is needed  
  > "stacking of large samples would be needed." (1)
- Alternative: Rotating disks as origin of residuals tested and found confined to low velocities  
  > "should not have a significant impact on the residuals observed at $|v| \lesssim 500$ km s$^{-1}$" (3.2.1)
- How they decided it was enough: _not stated_
- Limitation (authors): Sample may still be contaminated by faint unresolved satellites  
  > "our exclusion of interacting systems does not prevent the sample from being somehow still contaminated by unresolved" (3.1.2)
- Limitation (authors): Possible AGN contribution to broadening  
  > "some contribution to the [C II] broadening may come from (i) winds powered by gas accretion onto moderately massive black holes" (3.3)
- Caveat (inferred, ours): Broad component could reflect beam-smeared kinematics or satellites
- Caveat (inferred, ours): Assumed PDR fraction, temperature and v_out are crude and drive the mass rates
- Caveat (inferred, ours): No formal significance of the broad component over single Gaussian (no BIC test)

## Reproducibility

- Data public (paper): _not stated_
- Products in archive: _not stated_
- Missing: Béthermin et al. reduction and line-free channel details
- Missing: Source list and SFRs
- Missing: Fit initialisation and bootstrap settings
- Data volume (inferred): ~100s GB (about 75 Band 7 cubes, calibrated products much smaller)
- Score (inferred): 3/5, Stacking recipe is clear and data likely public, but key reduction and sample details are deferred to in-prep papers.
- Rediscovery candidate: no, Needs the ALPINE products and the deferred sample and reduction details; recipe partly incomplete.

## Links

- Method: Gallerani et al. 2018 (residual stacking procedure)
- Method: Hailey-Dunsheath et al. 2010 ([C II] outflow mass relation)
- Companion: Le Fèvre et al. 2019a (ALPINE survey description and classification)
- Companion: Béthermin et al. in prep. (data reduction)
- Companion: Fujimoto et al. 2019 ([C II] halo stacking)
- Related: ALPINE
- Related: VUDS
- Related: Keck-COSMOS

## Checks

```json
{
 "quotes": 68,
 "quotes_ok": 68,
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
  "facts": 79,
  "stated": 51,
  "rate": 0.646
 },
 "evidence_ok": true
}
```
