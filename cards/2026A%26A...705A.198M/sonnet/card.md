# The ALMA survey to Resolve exoKuiper belt Substructures (ARKS): IV. CO gas imaging and overview

`2026A&A...705A.198M` | Astronomy and Astrophysics 2026 | first author: Mac Manamon, S. | arXiv: 2601.11712 | DOI: 10.1051/0004-6361/202556605

Card schema 1.0 | model claude-sonnet-5-5 | depth full | type large_program_or_survey

## Science

- Fields: debris_disks, astrochemistry
- Question: What is the spectro-spatial distribution, optical depth and mass of CO gas in ARKS debris discs, and is CO detectable in the 13 discs without previous detections?  
  > "in order to analyse the spectro-spatial distribution of CO and constrain the gas mass in discs that were known to host gas previously, and to search for gas in the remaining 13 discs" (abstract)
- Target **HD 9672 (49 Ceti)**: coordinates _not stated_; z/distance 57.2 pc  
  > "| HD 9672 | $78.7 \pm 0.2$ | $107.9 \pm 0.2$ | $135.2 \pm 1.9$ | $158 \pm 3$ | 2.00 | 57.2 | 15 | $11906\pm 1$ | 1 |" (Disc parameters for ARKS); distance from _not stated_
- Target **HD 32297**: coordinates _not stated_; z/distance 130 pc  
  > "| HD 32297 | $88.3 \pm 0.0$ | $47.5 \pm 0.0$ | $115.9 \pm 0.3$ | $37\pm 1$ | 1.57 | 130 | 7.0 | $21558^{+4}_{-3}$ | 1 |" (Disc parameters for ARKS); distance from _not stated_
- Target **HD 121617**: coordinates _not stated_; z/distance 118 pc  
  > "| HD 121617 | $44.1 \pm 0.6$ | $58.7 \pm0.7$ | $76.3\pm0.4$ | $18\pm1$ | 1.90 | 118 | 14.9 | $7851^{+3}_{-2}$ | 1 |" (Disc parameters for ARKS); distance from _not stated_
- Target **HD 131488**: coordinates _not stated_; z/distance 152 pc  
  > "| HD 131488 | $85.0 \pm 0.1$ | $97.2 \pm 0.0$ | $89.7 \pm 0.1$ | $13 \pm 1$ | 1.80 | 152 | 12 | $5860^{+7}_{-8}$ | 1 |" (Disc parameters for ARKS); distance from _not stated_
- Target **HD 131835**: coordinates _not stated_; z/distance 130 pc  
  > "| HD 131835 | $74.2\pm 0.2$ | $59.2\pm0.2$ | $77.1 \pm 0.5$ | $65\pm 2$ | 1.70 | 130 | 9.5 | $3621^{+6}_{-5}$ | 1 |" (Disc parameters for ARKS); distance from _not stated_
- Target **13 gas-free ARKS discs (HD 10647, HD 14055, HD 15115, HD 15257, HD 61005, HD 76582, HD 84870, HD 95086, HD 109573, HD 145560, HD 161868, HD 170773, TYC 9340-437-1)**: coordinates _not stated_; z/distance 17-121 pc (Table)  
  > "| HD 10647 | $77.8 \pm 0.1$ | $57.3 \pm 0.3$ | $103.6 \pm 0.4$ | $65 \pm 2$ | 1.12 | 17.3 | 1.6 | $27600\pm100$ | 2 |" (Disc parameters for ARKS); distance from _not stated_

## Data provenance

- ALMA projects: 2022.1.00338.L
- bands: _not stated_
- frequencies and spectral setup: 12CO J=3-2 at 26 m/s resolution (gas-bearing) or 846 m/s (gas-free); 13CO at 886 m/s  
  > "the spectral resolution was set to 26 m s$^{-1}$ (the finest spectral resolution possible with ALMA) for the $^{12}$CO spectral window and to 886 m s$^{-1}$ for the $^{13}$CO spectral window" (2 Observations)
- continuum bandwidth: _not stated_
- arrays: _not stated_
- configurations: _not stated_
- baselines: _not stated_
- angular resolution: beams 70-150 mas for 12CO in gas-bearing discs; 130-950 mas in gas-free discs  
  > "the imaging pipeline led to beam sizes ranging from 70 to 150 mas (corresponding to physical scales projected on the sky of 8 to 16 au) for $^{12}$CO" (2 Observations)
- max recoverable scale: _not stated_
- sensitivity: RMS 3-5 mJy/beam 12CO and 0.6-1.0 mJy/beam 13CO (gas-bearing)  
  > "The RMS levels in the $^{12}$CO cubes ranged between 3 to 5 mJy/beam and from 0.6 to 1.0 mJy/beam in the $^{13}$CO cubes" (2 Observations)
- time on source: _not stated_
- observing dates: _not stated_
- pi or archival as stated: _not stated_
- Line: 12CO J=3-2 (345.796 GHz)
- Line: 13CO J=3-2 (330.599 GHz)
- External data: Disc geometry (i, PA, r, Δr), stellar masses from continuum MCMC fits  
  > "measured from the best fit parameters derived by MCMC sampling carried out by (cite: SebasARKSpaper)" (2 Observations) [from (cite: SebasARKSpaper)]
- External data: Literature 12CO line fluxes, ages and fractional luminosities for population study  
  > "we combine ARKS line fluxes (including 13 upper limits) with any archival discs observed with ALMA with a reported line flux for the $^{12}$CO J=3-2 line" (4.4 population study) [from Archival refs in Table (cite: marino2019gap; marino2018gap; daley2019mass)]
- External data: ISM 12C/13C abundance ratio of 77  
  > "If the ISM $^{12}$C/$^{13}$C abundance ratio of 77 applies, that implies that the $^{12}$CO optical depth must be at least 77" (3.4 Flux and mass) [from (cite: wilson1994abundances)]

## Processing

### Calibration

- pipeline or manual: ALMA pipeline calibration; then barycentric frame transform, time averaging, phase-centre offset  
  > "The calibration of the interferometric visibilities for all observations in time, baseline, and frequency was carried out using the ALMA pipeline." (2 Observations)
- casa version: CASA 6.4.1.12  
  > "package, version 6.4.1.12" (2 Observations)
- pipeline version: _not stated_
- archive products used as is: _not stated_
- flux calibrator: _not stated_
- flux scale uncertainty: 10% (Band 7)  
  > "systematic flux density calibration error associated with ALMA band 7 observations, which is 10% of the measured flux" (3.4 Flux and mass)
- self calibration: _not stated_

### Imaging

- task: CASA tclean called three times, all configurations combined  
  > "We developed an imaging pipeline where `tclean` is called three times." (2 Observations)
- deconvolver: multiscale in third iteration  
  > "In the third and final `tclean` iteration, the deconvolver parameter was set to `multiscale`" (2 Observations)
- weighting robust: Briggs robust 0.5 for gas-bearing non-edge-on; robust 2 for edge-on HD 32297, HD 131488 and gas-free  
  > "we employed Briggs weighting, with a robust parameter of 0.5." (2 Observations); "we employed Briggs weighting with a robust parameter of 2, which is close to Natural weighting" (2 Observations)
- uv taper: _not stated_
- cell size: 1/5 of mean beam size  
  > "which we chose to be $\frac{1}{5}$ of the beam size (averaged between the major and minor axis)" (2 Observations)
- image size: FWHM of 12 m primary beam  
  > "We then chose the image size to be equal to the full width at half maximum (FWHM) of the primary beam of the ALMA 12 m antenna." (2 Observations)
- masking: Keplerian masks (keplerian_mask), nbeams smoothing 1.5-10; clean threshold 4x RMS  
  > "We use a Keplerian mask to leverage the expected near-Keplerian rotation pattern to produce channel-based masks" (2 Observations); "which varied between 1.5 – 10, depending on the system" (Keplerian mask creation)
- multiscale scales: [0,5,10] pixels  
  > "We set the scales for the tclean deconvolution to be $[0,5,10]$" (2 Observations)
- continuum subtraction: _not stated_
- line free channels: _not stated_
- primary beam correction: _not stated_
- array combination: all baseline configurations imaged simultaneously  
  > "we simultaneously imaged the calibrated and preprocessed visibilities from all baseline configurations" (2 Observations)
- smoothing: _not stated_
- final beam: 70-150 mas (12CO gas-bearing)  
  > "beam sizes ranging from 70 to 150 mas" (2 Observations)
- final rms: _not stated_

### Inherited from earlier work

- Visibility calibration and preparation details (phase centre offsets, weights, time averaging)  
  > "The detailed calibration and preparation of the interferometric visibilities for imaging are described in (cite: SebasARKSpaper)" (2 Observations) [from (cite: SebasARKSpaper)]
- CLEAN threshold of 4 RMS  
  > "We adopted this threshold of 4 times the RMS noise level, in line with the CLEANing methodology of (cite: czekala2021molecules)" (2 Observations) [from (cite: czekala2021molecules)]
- Optically thin mass formula (Eq. 2)  
  > "We used Eq. 2 in (cite: matra2015co_fomalhaut) to calculate the $^{12}$CO optically thin ($\tau_{^{12}\rm CO} <<1$) gas mass" (3.4 Flux and mass) [from (cite: matra2015co_fomalhaut)]

### Not stated but needed to reproduce (our reading)

- Line-free channels / continuum subtraction approach for the line cubes
- Exact nbeams and C value for each system
- Clean mask thresholds and RMS estimation region
- Which Measurement Sets / execution blocks per target
- Gofish annulus/aperture radii used for each spectrum
- Excitation temperatures per disc used in mass calculation

## Analysis recipe

1. **Image line cubes**: Three-stage tclean with Keplerian masks and multiscale CLEAN to 4 RMS  
  > "We developed an imaging pipeline where `tclean` is called three times." (2 Observations)
   - software: CASA, tclean, keplerian_mask
   - parameter: robust 0.5 or 2; scales [0,5,10]; pixel 1/5 beam  
  > "We set the scales for the tclean deconvolution to be $[0,5,10]$" (2 Observations)
   - assumption: Gas co-located with dust and near-Keplerian  
  > "we use prior knowledge of each disc’s geometry, assuming gas is co-located with the dust" (2 Observations)
   - fitting: _not stated_
   - validation: Visual inspection of residuals  
  > "which we confirmed by visual inspection" (2 Observations)
2. **Make moment maps**: Quadratic fit to peak velocity; peak brightness temperature via Planck; spectro-spatial shifted integrated intensity  
  > "we fit a quadratic function to the peak and its two neighbouring channels in each of the pixels’ spectra" (3.1 Image galleries)
   - software: bettermoments
   - parameter: clip at 3.5 sigma; integrate channels above 4 sigma  
  > "we clipped velocity values in pixels where the peak of the emission was detected at a significance below $3.5~\sigma$" (3.1 Image galleries)
   - fitting: _not stated_
   - validation: _not stated_
3. **Spectra and radial profiles, 12CO/13CO ratio**: Gofish spectra and shifted-stacked radial profiles in 1/4-beam elliptical annuli; on-sky profiles for edge-on discs; ratio where 13CO >2 sigma  
  > "we split the disc emission into concentric elliptical annuli, $\frac{1}{4}$ of the beam’s major axis wide" (3.2 Spectral and radial profiles)
   - software: GoFish
   - fitting: _not stated_
   - validation: Uncertainties by bootstrapping in noise-only regions  
  > "This region-drawing and averaging (bootstrapping) was repeated many times in different parts of the image" (3.2 Spectral and radial profiles)
4. **Search for CO in gas-free discs by stacking**: Spectro-spatial shifting/stacking of dirty cubes in both rotation directions; 3 sigma upper limits from 7 km/s bootstrapped windows  
  > "We spectrally integrated over 7 km s$^{-1}$ wide noisy regions, located in random regions of each spectrum" (3.5 Flux and mass)
   - software: GoFish
   - assumption: Keplerian rotation, CO co-located with dust  
  > "under the assumption of Keplerian rotation and that the CO emission is co-located with the dust emission" (3.3 stacking)
   - fitting: _not stated_
   - validation: _not stated_
5. **Line fluxes and CO masses**: Integrate stacked spectrum over V*±5 sigma (Gaussian fit); box integration for edge-on; optically thin LTE mass and tau=77 scaling  
  > "We set the limits of integration to $V_{*} \pm 5~\sigma$." (3.4 Flux and mass)
   - software: GoFish
   - assumption: LTE with Tex equal to peak brightness temperature; tau12CO=77 from ISM 12C/13C  
  > "we calculate this assuming local thermodynamic equilibrium (LTE) and a CO excitation temperature equal to the peak-brightness temperature measured" (3.4 Flux and mass)
   - fitting: Gaussian fit to stacked spectrum for centroid/width  
  > "we fitted a Gaussian to the spectro-spatially stacked spectra" (3.3 stacking)
   - validation: Stellar velocity of HD 121617 compared with independent measurement, consistent within 3 sigma  
  > "We found the two measured velocities to be consistent within $3~\sigma$ of each other." (3.3 stacking)
6. **Population comparison**: Scale fluxes to 100 pc, convert J=2-1 to J=3-2 with ratio 1.67, compare with age and fractional luminosity  
  > "We scaled all line flux measurements to 100 pc to compare the intrinsic line luminosity of all discs." (4.4 population study)
   - fitting: _not stated_
   - validation: _not stated_

## Software

- **CASA** 6.4.1.12: calibration and imaging pipeline  
  > "line-imaging pipeline in Python using the Common Astronomy Software Applications (CASA) package, version 6.4.1.12" (2 Observations)
- **keplerian_mask** : CLEAN masks  
  > "through the `keplerian_mask` package" (Keplerian mask creation)
- **GoFish** : spectra, radial profiles, stacking  
  > "using `Gofish` (cite: rt_gofish)" (3.2 Spectral and radial profiles)
- **bettermoments** : quadratic peak-velocity method cited  
  > "Using this quadratic fitting method has been shown to be better than using the intensity weighted average velocity method implemented by CASA" (3.1 Image galleries)

## Numeric results

| quantity | value | uncertainty | units | step | quote |
|---|---|---|---|---|---|
| 12CO J=3-2 integrated flux HD 9672 | 8.9 | 0.9 | Jy km/s | 5 | / HD 9672   / $3$                       / 8.9 $\pm$ 0.9            / 3.0 $\pm$ 0.3 |
| 12CO integrated flux HD 32297 | 3.7 | 0.4 | Jy km/s | 5 | / HD 32297  / $68$                      / 3.7 $\pm$ 0.4 |
| 12CO integrated flux HD 121617 | 3.6 | 0.4 | Jy km/s | 5 | / HD 121617 / $28$                      / 3.6 $\pm$ 0.4 |
| 12CO integrated flux HD 131488 | 2.7 | 0.3 | Jy km/s | 5 | / HD 131488 / $6$                       / 2.7 $\pm$ 0.3 |
| 12CO integrated flux HD 131835 | 1.9 | 0.2 | Jy km/s | 5 | / HD 131835 / $21$                      / 1.9 $\pm$ 0.2 |
| Optically thin 12CO mass range | ~1-6e-4 | not stated | Earth masses | 5 | These values (Table [\[tab:linefluxesofgas\]](#tab:linefluxesofgas)) are of order $\sim1-6\times10^{-4}$ M$_{\oplus}$. |
| 12CO/13CO intensity ratio at 12CO peak | ~2.0-5.5 | ±6%-33% | dimensionless | 3 | intensity ratios at the radial $^{12}$CO intensity peaks of each system are $\sim 2.0 - 5.5$ |
| 12CO peak brightness temperatures | ~25-50 | not stated | K | 2 | we measure peak-brightness temperatures of $\sim 25 - 50$ K |
| Velocity-based upper limits on 12CO inner radius | 3-68 | not stated | au | 3 | We calculated velocity-based upper limits to the inner disc radii of $3 - 68$ au. |
| Planet mass opening gap in HD 131488 (lower limit) | 7 | not stated | Earth masses | 0 | We find that a $7 M_\oplus$ planet located at 5.8 au is capable of opening a gap |

## Qualitative findings

- CO is broader than and peaks interior to the mm dust in all five gas-bearing discs; no 12CO detected in the 13 gas-free discs  
  > "In each disc, the CO peaks interior to the dust, although the offset between the dust and gas varies with each system." (5 Conclusions)

## Claim tuples

- H: Is CO radially co-located with dust? | E: Radial profiles of 12CO/13CO vs ARKS continuum | R: CO peaks interior to the dust and is more extended | F: Second-generation scenario requires significant shielding to viscously spread | **supported**
- H: Is 12CO optically thick with optically thin 13CO? | E: Radial 12CO/13CO ratio profiles | R: Ratios flat with radius in four of five discs | F: Both isotopologues thick or both thin; thick-12CO/thin-13CO ruled out for four | **supported**
- H: Do gas-free discs host detectable CO? | E: Spectro-spatial stacking of 13 discs | R: No 12CO detection | F: 3 sigma upper limits set | **supported**
- H: Does gas detection correlate with age/fractional luminosity? | E: Scaled line luminosity population study | R: Detections mostly in young systems but large scatter | F: No trend among detected systems | **partially**

## Reasoning

- Why this data: _not stated_
- Why this method: Keplerian masks needed because of >1000 channels at 13 m/s  
  > "manual masking is unfeasible and masks covering the gas emission in every channel have to be defined automatically" (2 Observations)
- How they decided it was enough: _not stated_
- Limitation (authors): Optically thick masses are lower limits; inner radii are upper limits; degeneracy thick/thin needs radiative transfer  
  > "To break this degeneracy, radiative transfer modelling needs to be carried out" (4.2)
- Caveat (inferred, ours): Mass depends on assumed tau=77 and Tex=Tb
- Caveat (inferred, ours): Stacking assumes gas co-located with dust
- Caveat (inferred, ours): Different spectral resolution for 12CO and 13CO affects ratios

## Reproducibility

- Data public (paper): _not stated_
- Products in archive: Cubes released on Dataverse; pipelines at arkslp.org  
  > "We make these available to the community at <https://doi.org/10.7910/DVN/PXGNNZ> and the imaging pipelines can be found on <https://arkslp.org>." (footnote)
- Code: Imaging pipelines at arkslp.org  
  > "the imaging pipelines can be found on <https://arkslp.org>" (footnote)
- Missing: Calibrated measurement sets from the companion ARKS paper
- Missing: Per-disc nbeams and C values
- Data volume (inferred): Large (hundreds of GB to TB); ~1000+ channels cubes for 18 targets
- Score (inferred): 4/5, Large-program data, code and cubes released and recipe largely detailed; some per-target parameters unstated.
- Rediscovery candidate: yes, Data and pipeline public, numeric fluxes and masses in tables.

## Links

- Method: (cite: SebasARKSpaper) (Calibration, visibility preparation and disc geometry)
- Method: (cite: rt_gofish) (GoFish spectro-spatial stacking)
- Method: (cite: rich_teague_2020_4321137) (Keplerian mask)
- Companion: (cite: Aoife_arks) (Radiative transfer of HD 121617)
- Companion: (cite: Yinuo_arks) (Continuum radial profiles)
- Companion: (cite: Julien_arks) (Scattered light comparison)
- Related: ARKS
- Related: ALMA MAPS

## Checks

```json
{
 "quotes": 72,
 "quotes_ok": 72,
 "quote_pass_rate": 1.0,
 "quotes_too_long": 0,
 "unsupported_facts": 0,
 "project_codes": 1,
 "codes_not_in_text": [],
 "codes_not_in_obscore": [],
 "obscore_codes_not_in_card": [
  "2012.1.00142.S",
  "2012.1.00198.S",
  "2015.1.01260.S",
  "2016.1.00104.S",
  "2016.1.00195.S",
  "2016.1.00907.S",
  "2017.1.00167.S",
  "2017.1.00825.S",
  "2018.1.01222.S",
  "2019.1.00189.S"
 ],
 "codes_printed_but_missing": [
  "2012.1.00142.S",
  "2012.1.00198.S",
  "2015.1.01260.S",
  "2016.1.00104.S",
  "2016.1.00195.S",
  "2016.1.00907.S",
  "2017.1.00167.S",
  "2017.1.00825.S",
  "2018.1.01222.S",
  "2019.1.00189.S"
 ],
 "numeric_results": 10,
 "numeric_problems": 0,
 "fill": {
  "facts": 94,
  "stated": 52,
  "rate": 0.553
 },
 "evidence_ok": true
}
```
