# Widespread QSO-driven outflows in the early Universe

`2019A&A...630A..59B` | Astronomy and Astrophysics 2019 | first author: Bischetti, M. | arXiv: 1806.00786 | DOI: 10.1051/0004-6361/201833557

Card schema 1.0 | model claude-sonnet-5-5 | depth full | type archival_reuse

## Science

- Fields: agn_and_quasars, high_z_galaxies
- Question: Do high-z QSOs show faint broad [CII] wings tracing cold outflows, detectable by stacking archival ALMA [CII] data?  
  > "We have collected a sample of 48 QSOs with ALMA [CII] detection to investigate the presence of outflows, as traced by weak [CII] broad wings, by performing a stacking analysis." (Introduction)
- Target **48 QSOs at 4.5<z<7.1 with ALMA [CII] detections**: coordinates _not stated_; z/distance 4.5<z<7.1 ([CII]-based redshifts, error 0.001)  
  > "a sample of 48 QSOs at $4.5<z<7.1$ detected in [CII] by ALMA" (Conclusions); distance from Gaussian centroid of the [CII] line  
  > "a sample of 48 QSOs at $4.5<z<7.1$ detected in [CII] by ALMA" (Conclusions)

## Data provenance

- ALMA projects: 2011.0.00243.S, 2012.1.00604.S, 2012.1.00676.S, 2012.1.00882.S, 2013.1.01153.S, 2015.1.01115.S, 2016.1.01515.S, 2015.1.00997.S
- bands: Band 6 or 7  
  > "Observations involve ALMA bands 6 or 7, depending on the redshift of the individual source." (Sample and data reduction)
- frequencies and spectral setup: four spectral windows; two adjacent windows with [CII] combined, ~3.7 GHz  
  > "we combined the two adjacent spectral windows of the sideband containing the [CII] line to increase the available spectral range, for a total of $\sim3.7$ GHz" (Sample and data reduction)
- continuum bandwidth: _not stated_
- arrays: _not stated_
- configurations: _not stated_
- baselines: _not stated_
- angular resolution: ~0.3 to 1.2 arcsec (average beam axis)  
  > "The angular resolutions, computed as average beam axis, range from $\sim 0.3$ to 1.2 arcsec." (Sample and data reduction)
- max recoverable scale: _not stated_
- sensitivity: ~0.3 to ~0.8 mJy/beam per 30 km/s channel for individual sources; stack 0.06 mJy/beam  
  > "the bulk of the observations have similar rms sensitivities from $\sim 0.3$ to $\sim 0.8$ mJy/beam for a 30 km s$^{-1}$channel" (Sample and data reduction)
- time on source: ~34 hours total  
  > "equivalent to a total of $\sim34$ hours of on-source observing time" (Sample and data reduction)
- observing dates: _not stated_
- pi or archival as stated: public archival data as of March 2018, plus unpublished project 2015.1.00997.S  
  > "We collected all [CII] observations of $z>4.5$ QSOs on the ALMA archive public as of March 2018" (Sample and data reduction)
- Line: [CII] 158 um fine structure (1900.5369 GHz)
- External data: Mrk231-like template used to compute L_FIR  
  > "We computed the FIR luminosity by using an Mrk231-like template (cite: Polletta07)" (Sample and data reduction) [from Polletta07]
- External data: AGN bolometric correction from 1450 A luminosity  
  > "by applying the bolometric correction from (cite: Runnoe12)" (Sample and data reduction) [from Runnoe12]
- External data: Low-z AGN outflow energetics for comparison (30 AGN)  
  > "the collection of 30 low redshift AGN by (cite: Flutsch18)" (Discussion) [from Flutsch18]

## Processing

### Calibration

- pipeline or manual: manual or pipeline mode, with extra flagging and flux calibration improvement where necessary  
  > "Data were calibrated using the CASA 4.7.2 software (cite: McMullin07) in manual or pipeline mode." (Sample and data reduction)
- casa version: CASA 4.7.2  
  > "Data were calibrated using the CASA 4.7.2 software" (Sample and data reduction)
- pipeline version: _not stated_
- archive products used as is: _not stated_
- flux calibrator: _not stated_
- flux scale uncertainty: _not stated_
- self calibration: _not stated_

### Imaging

- task: CASA clean  
  > "Data cubes were produced by using the CASA task clean by using the Hogbom algorithm" (Sample and data reduction)
- deconvolver: Hogbom  
  > "Hogbom algorithm with no cleaning mask and a number of iterations $N_{\rm iter}=500-1000$" (Sample and data reduction)
- weighting robust: natural weighting  
  > "We chose a natural weighting to maximise the sensitivity of the individual observations" (Sample and data reduction)
- uv taper: tapering to 1.2 arcsec for common-resolution stack test; sources <0.6'' not used  
  > "We produced ALMA cubes at the worse angular resolution in our sample by tapering the visibilities to 1.2 arcsec." (4.4 Stacked Cube)
- cell size: 0.05 arcsec; 30 km/s channels  
  > "a common pixel size of 0.05$''$ and a common spectral bin of 30 km s$^{-1}$" (Sample and data reduction)
- image size: _not stated_
- masking: no cleaning mask; threshold 3x rms  
  > "together with a threshold of three times the sensitivity limit given by the rms" (Sample and data reduction)
- multiscale scales: _not stated_
- continuum subtraction: zeroth-order model fit in uv plane to channels with |v|>1500 km/s from the [CII] centroid, in the adjacent spws  
  > "We thus fitted a zeroth order continuum model in the UV plane to all the available channels" (Sample and data reduction)
- line free channels: |v|>1500 km/s from the core [CII] centroid (~1/4 of each spw); atmospheric transmission <0.5 excluded  
  > "with a velocity $|v| > 1500$ km s$^{-1}$with respect to the centroid of the (core) [CII] emission" (Sample and data reduction)
- primary beam correction: _not stated_
- array combination: _not stated_
- smoothing: _not stated_
- final beam: variance-weighted 0.52'' x 0.68'' for stacked cube  
  > "we computed an average angular resolution $\theta_{\rm res} = 0.52'' \times 0.68''$" (4.4 Stacked Cube)
- final rms: ~0.06 mJy/beam median in stacked spectrum  
  > "The median rms of the stacked spectrum is $\sim0.06$ mJy/beam" (4.1 Stacked spectrum)

### Inherited from earlier work

- Variance-weighted stacking formalism  
  > "defining the weighted intensity $I^\prime_k$ of a generic spatial pixel ($x^\prime, y^\prime$) in the stacked cube for each spectral channel $k$, and the relative weight $W^\prime_{\rm k}$ as follows (cite: Fruchter&Hook02)" (Methods) [from (cite: Fruchter&Hook02)]
- Outflow mass relation for [CII], X_C+ and T assumptions  
  > "to compute the outflow mass of atomic neutral gas we use the relation from (cite: Hailey-Dunsheath10)" (Discussion) [from (cite: Hailey-Dunsheath10)]
- Outflow rate as time-averaged shells or clumps  
  > "we assume the sceario of time-averaged expelled shells or clumps (cite: Rupke&Veilleux05b)" (Discussion) [from (cite: Rupke&Veilleux05b)]
- SFR from L_FIR  
  > "as inferred from their $L_{\rm FIR}$ (computed following (cite: Kennicutt12))" (4.2 Outflow relation with QSO-galaxy properties) [from (cite: Kennicutt12)]

### Not stated but needed to reproduce (our reading)

- List of the 48 QSOs with per-source flux scaling/calibration corrections (table not in text)
- Exact clean threshold and iteration count per source
- Which sources were calibrated manually vs pipeline
- Exact aperture definition/centering and handling of channels with partial coverage
- Initial guesses for the Gaussian fits
- How the 100 empty positions were chosen
- Fruchter&Hook-based cube regridding details

## Analysis recipe

1. **Image archival data and subtract continuum**: CASA clean cubes (Hogbom, natural, 0.05'' pixels, 30 km/s channels); zeroth-order uv-plane continuum fit to |v|>1500 km/s channels  
  > "We chose a natural weighting to maximise the sensitivity of the individual observations, a common pixel size of 0.05$''$ and a common spectral bin of 30 km s$^{-1}$." (Sample and data reduction)
   - software: CASA
   - parameter: Niter 500-1000, threshold 3 sigma  
  > "a number of iterations $N_{\rm iter}=500-1000$ according to the significance of the detection" (Sample and data reduction)
   - fitting: _not stated_
   - validation: First-order polynomial continuum did not significantly affect results  
  > "We verified that modelling the continuum emission with a first order polynomial did not significantly affect our results" (Sample and data reduction)
2. **Extract spectra and fit [CII] core per source**: Spectra from region of four beams; single Gaussian fit for redshift and core parameters  
  > "we extracted the continuum-subtracted [CII] spectra from a region with an area of four beams" (Sample and data reduction)
   - fitting: one Gaussian component  
  > "The line parameters describing the [CII] core emission were derived by fitting each spectrum with one Gaussian component model." (Sample and data reduction)
   - validation: _not stated_
3. **Stack spectra and cubes**: Variance-weighted stack with weights 1/sigma^2 per channel after aligning at [CII] rest frequency and centering on continuum peak; both 1D spectra and 3D cubes  
  > "We applied a standard variance-weighted stacking, i.e. we used a weighting factor $w_{\rm j,k}=1/\sigma_{\rm j,k}^2$" (Methods)
   - parameter: n=48; channels with atmospheric transmission <0.5 excluded  
  > "We did not include in the stack spectral regions corresponding to an atmospheric transmission $<0.5$ for a 1 mm precipitable water vapour." (Methods)
   - fitting: _not stated_
   - validation: Stacks of 100 empty positions gave spurious SNR ~0.4; 1000 jackknife stacks excluding 5 sources gave ~11% mean luminosity variation  
  > "This resulted into an average spurious signal-to-noise ratio of $\sim0.4$ for the stack of the total sample." (Methods)
4. **Fit broad [CII] wings**: chi2 minimisation with core Gaussian plus broad Gaussian, all parameters free, weights W'_k  
  > "The $\chi^2$ minimisation of the fit was performed by using for each channel the weight $W^\prime_{\rm k}$ (see Eq. 1) and all the model parameters were free to vary in the fit with no constrains." (4.1 Stacked spectrum)
   - software: scipy curve_fit
   - fitting: chi2 minimisation, scipy optimize curve_fit; 1G chi2_nu=8.6 vs 2G 3.7  
  > "by using the python *scipy optimize* package *curve_fit*" (Appendix A: spectral fitting)
   - validation: Subsamples by FWHM, L_AGN, SFR; stack in luminosity density; fixed 8 kpc aperture; Decarli18 sample alone gives SNR~2; excluding 3 companion QSOs  
  > "As further verification, we also excluded these particular three QSOs from the stack and found no significant variation in the luminosity of the broad [CII] wings." (4.3 Outflow detectability)
5. **Size of outflow from stacked cube**: Beam-deconvolved half-light radius of |v|>400 km/s map  
  > "We derived a beam-deconvolved half light radius $R_{\rm out} = \sqrt{(R_{\rm 50\%}^2 - R_{\rm beam}^2})\sim 0.60$ arcsec" (4.4 Stacked Cube)
   - fitting: _not stated_
   - validation: Repeated with cubes tapered to 1.2 arcsec  
  > "we derived a beam-corrected half light radius $R_{\rm out}^{\rm taper} \sim 4.6$ kpc" (4.4 Stacked Cube)
6. **Outflow mass, rate, power, momentum load**: Hailey-Dunsheath10 mass relation; Mdot=v M/R; Edot=0.5 Mdot v^2; momentum load vs L_AGN/c  
  > "$$\dot{M}_{\rm out} = \frac{v_{\rm out} \times M_{\rm out}}{R_{\rm out}}$$" (Discussion)
   - parameter: v_out=|Delta v|+FWHM_broad/2; R_out~3.5 kpc  
  > "$v_{\rm out}= |\Delta v_{\rm broad}| + \rm FWHM_{[CII]}^{broad}/2$" (Discussion)
   - assumption: optically thin [CII], n>>n_crit, X_C+~1e-4, T=200 K, 0.7 PDR fraction  
  > "we consider a conservative $X_{\rm C^+}\sim10^{-4}$ and a gas temperature of 200 K, both typical of PDRs" (Discussion)
   - fitting: _not stated_
   - validation: Assuming T from 100 to 1000 K changes mass by only 20%  
  > "Assuming a temperature from 100 K to 1000 K would imply a variation of only 20% in the resulting gas mass." (Discussion)

## Software

- **CASA** 4.7.2: calibration and imaging  
  > "Data were calibrated using the CASA 4.7.2 software (cite: McMullin07)" (Sample and data reduction)
- **scipy optimize curve_fit** : chi2 spectral fitting of stacked spectra  
  > "by using the python *scipy optimize* package *curve_fit*" (Appendix A: spectral fitting)

## Numeric results

| quantity | value | uncertainty | units | step | quote |
|---|---|---|---|---|---|
| FWHM of broad [CII] component, whole stack | 1730 | 210 | km/s | 4 | 1730 $\pm$ 210 |
| FWHM of [CII] core, whole stack | 390 | 30 | km/s | 4 | FWHM$^{\rm core}_{\rm[CII]}$ = 390 $\pm30$ km s$^{-1}$ |
| Broad [CII] significance (fit) | 5.6 | not stated | sigma | 4 | The significance estimated through the fitting analysis is $5.6\sigma$. |
| L_[CII] broad, whole stack | 4.1 | 0.7 | 1e8 Lsun | 4 | 4.1$\pm$0.7 |
| Broad-to-narrow flux ratio f_[CII] | 0.22 | 0.04 | dimensionless | 4 | 0.22 $\pm$ 0.04 |
| Broad component velocity shift | -90 | 40 | km/s | 4 | -90 $\pm$ 40 |
| Outflow radius R_out | ~3.5 | not stated | kpc | 5 | $R_{\rm out}$ corresponds to $\sim3.5$ kpc at $\langle z_{\rm stack}\rangle$. |
| Outflowing neutral gas mass | 3.7e8 | 0.7e8 | Msun | 6 | $M_{\rm out} = (3.7\pm0.7) \times10^8$ M$_\odot$ |
| Mass outflow rate, whole stack | 100 | 20 | Msun/yr | 6 | $\dot{M}_{\rm out} = 100\pm20$ M$_\odot$ yr$^{-1}$ |
| Sensitivity improvement vs Cicone15 J1148+5251 | ~14 | not stated | dimensionless | 3 | a factor of $\sim14$ lower than that of the J1148$+$5251 observations of (cite: Cicone15) |

## Qualitative findings

- Broad [CII] wing strength correlates with AGN luminosity but not SFR, so outflows are QSO-driven  
  > "we observe that the strength of the stacked broad component correlates with the AGN luminosity, but does not depend on the SFR." (Conclusions)
- Kinetic power and momentum load are lower than energy-driven model expectations  
  > "For our stacked spectra $\dot{P}_{\rm out}/ \dot{P}_{\rm AGN}\lesssim1$, while "energy-driven" outflow models would expect momentum load factors of $\sim20$." (Discussion)

## Claim tuples

- H: Faint broad [CII] wings exist in high-z QSOs | E: Variance-weighted stack of 48 archival ALMA [CII] spectra, two-Gaussian fit | R: Broad component FWHM 1730±210 km/s at 5.6 sigma | F: Cold outflows are widespread in z~6 QSOs | **supported**
- H: Outflows are driven by the QSO rather than star formation | E: Stacks split by L_AGN, FWHM and SFR | R: L_broad rises with L_AGN; comparable L_broad ~4e8 Lsun in low and high SFR stacks | F: QSOs are the primary driver | **supported**
- H: Outflows are spatially extended and energetic | E: Stacked cube and energetics | R: R_out ~3.5 kpc; Mdot ~100 Msun/yr; momentum load 0.1-1 | F: Outflows are not effective at clearing the whole galaxy | **partially**

## Reasoning

- Why this data: _not stated_
- Why this method: Individual observations too shallow to detect weak wings, so stacking  
  > "with a sensitivity generally not yet adequate to individually detect weak [CII] broad wings." (Introduction)
- Alternative: Blueshift of broad component may be a coverage artefact or dust absorption of the red wing  
  > "This might be an artefact resulting from the asymmetric distribution of the data" (4.1 Stacked spectrum)
- How they decided it was enough: _not stated_
- Limitation (authors): Interferometric data may miss extended diffuse emission; stacking dilutes orientations  
  > "we cannot exclude that additional, more extended emission is present but missed by the interferometric data used for the stacking." (Conclusions)
- Caveat (inferred, ours): Reduced chi2 of 3.7 suggests the profile is not well described by two Gaussians; broad component may reflect core shape complexity
- Caveat (inferred, ours): Heterogeneous resolutions and companion contamination may mimic wings
- Caveat (inferred, ours): Mass estimate depends on assumed T, X_C+ and optically thin [CII]
- Caveat (inferred, ours): Stack mixes sources with different widths

## Reproducibility

- Data public (paper): Archive data public as of March 2018, except one unpublished project  
  > "We collected all [CII] observations of $z>4.5$ QSOs on the ALMA archive public as of March 2018" (Sample and data reduction)
- Products in archive: _not stated_
- Missing: Source list table with per-source parameters not in text
- Missing: Stacking code not released
- Missing: Details of flux calibration improvements
- Data volume (inferred): ~100-300 GB raw for 8 projects, 48 sources
- Score (inferred): 3/5, Public data, clear stacking recipe and numeric results, but sample table and per-source calibration details are missing.
- Rediscovery candidate: yes, Data public, recipe mostly complete, results numeric.

## Links

- Method: (cite: Fruchter&Hook02) (variance-weighted stacking)
- Method: (cite: Hailey-Dunsheath10) ([CII] outflow mass relation)
- Companion: (cite: Decarli18) (previous [CII] stack of 23 QSOs, no excess found)
- Companion: (cite: Cicone15) (J1148+5251 outflow detection)

## Checks

```json
{
 "quotes": 76,
 "quotes_ok": 76,
 "quote_pass_rate": 1.0,
 "quotes_too_long": 0,
 "unsupported_facts": 0,
 "project_codes": 8,
 "codes_not_in_text": [],
 "codes_not_in_obscore": [],
 "obscore_codes_not_in_card": [],
 "codes_printed_but_missing": [],
 "numeric_results": 10,
 "numeric_problems": 0,
 "fill": {
  "facts": 78,
  "stated": 53,
  "rate": 0.679
 },
 "evidence_ok": true
}
```
