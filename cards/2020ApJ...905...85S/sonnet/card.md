# Ubiquitous Molecular Outflows in z &gt; 4 Massive, Dusty Galaxies. I. Sample Overview and Clumpy Structure in Molecular Outflows on 500 pc Scales

`2020ApJ...905...85S` | The Astrophysical Journal 2020 | first author: Spilker, Justin S. | arXiv: 2010.12590 | DOI: 10.3847/1538-4357/abc47f

Card schema 1.0 | model claude-sonnet-5-5 | depth full | type observational_alma_primary

## Science

- Fields: high_z_galaxies
- Question: How common are molecular outflows (traced by OH 119 um absorption) in z>4 lensed dusty star-forming galaxies, and what is their spatial structure on ~500 pc scales?  
  > "In this first paper, we give an overview of the survey, focusing on the detection rate and structure of molecular outflows." (abstract)
- Target **SPT DSFG sample (11 lensed DSFGs, e.g. SPT0202-61, SPT0418-47, SPT0441-46, SPT0459-58, SPT0459-59, SPT0544-40, SPT2048-55, SPT2103-60, SPT2132-58, SPT2311-54, SPT2319-55)**: coordinates per-source R.A./Dec. given in the ALMA observation table (e.g. SPT0202-61 02h02m58.86s, -61d21m11.1s)  
  > "The final sample consists of 11 objects at $4.09 < z < 5.30$ including SPT2319-55, previously published in ." (2.1 Parent Sample and Source Selection); "SPT0202-61 & $02^\mathrm{h}02^\mathrm{m}58.86^\mathrm{s}$ & $-61^\circ21{}^\prime11.1\ensuremath{''}$ & 5.0180" (Table 1); z/distance z = 4.09-5.30 (e.g. SPT0202-61 z=5.0180)  
  > "The final sample consists of 11 objects at $4.09 < z < 5.30$ including SPT2319-55, previously published in ." (2.1 Parent Sample and Source Selection); "SPT0202-61 & $02^\mathrm{h}02^\mathrm{m}58.86^\mathrm{s}$ & $-61^\circ21{}^\prime11.1\ensuremath{''}$ & 5.0180" (Table 1); distance from spectroscopic redshifts from CO/[CII] lines (weiss13; strandet16; marrone18; reuter20)  
  > "The final sample consists of 11 objects at $4.09 < z < 5.30$ including SPT2319-55, previously published in ." (2.1 Parent Sample and Source Selection); "SPT0202-61 & $02^\mathrm{h}02^\mathrm{m}58.86^\mathrm{s}$ & $-61^\circ21{}^\prime11.1\ensuremath{''}$ & 5.0180" (Table 1)

## Data provenance

- ALMA projects: 2015.1.00942.S, 2016.1.00089.S, 2018.1.00191.S, 2019.1.00253.S, 2016.1.01499.S
- bands: Band 8 (385-500 GHz), OH doublet at 399-494 GHz observed  
  > "frequencies of relatively good atmospheric transmission in ALMA Band 8 (385–500 GHz)" (2.1 Parent Sample and Source Selection)
- frequencies and spectral setup: Two slightly overlapping 1.875 GHz basebands with 3.9 MHz channels covering the OH doublet; two more 1.875 GHz basebands for continuum in the other sideband  
  > "we configured the correlator to observe the OH doublet with two slightly overlapping 1.875 GHz wide basebands and 3.9MHz channels" (2.2 ALMA Observations)
- continuum bandwidth: _not stated_
- arrays: _not stated_
- configurations: _not stated_
- baselines: max 700-1600 m, min ~15 m  
  > "with maximum baseline lengths ranging from 700–1600m and minimum baseline lengths $\sim$15 m for all observations" (2.2 ALMA Observations)
- angular resolution: beams ~0.11x0.16 to 0.46x0.49 arcsec (natural weighting)  
  > "SPT2103-60 & $21^\mathrm{h}03^\mathrm{m}30.85^\mathrm{s}$ & $-60^\circ32{}^\prime40.5\ensuremath{''}$ & 4.4357 & 462.6 & 2016.1.00089.S & 23 & 0.46$\times$0.49" (Table 1)
- max recoverable scale: ≳2.5 arcsec  
  > "The shortest baselines lead to maximum recoverable scales $\gtrsim$2.5$''$ depending on observing frequency" (2.2 ALMA Observations)
- sensitivity: continuum rms 64-352 uJy/beam; 0.41-2.10 mJy/beam per 100 km/s channel  
  > "The spectral line sensitivity $\sigma_{\mathrm{100\ensuremath{\rm{km\,s}^{-1}}}}$ is measured in a 100 $\rm{km\,s}^{-1}$ channel near the upper OH rest frequency." (Table 1)
- time on source: 11-94 min per source/project (Table 1 t_obs)  
  > "SPT2311-54 & $23^\mathrm{h}11^\mathrm{m}23.97^\mathrm{s}$ & $-54^\circ50{}^\prime30.2\ensuremath{''}$ & 4.2795 & 476.2 & 2015.1.00942.S & 45" (Table 1)
- observing dates: 2016-2019  
  > "ALMA observed our sample galaxies across several projects from 2016–2019" (2.2 ALMA Observations)
- pi or archival as stated: _not stated_
- Line: 16OH 2Pi3/2 J=3/2-5/2 Lambda doublet (119 um) (2509.9 and 2514.3 GHz)
- Line: [CII] 158 um (not stated)
- Other facility **ATCA**: CO(2-1) for molecular gas masses and redshifts  
  > "Molecular gas masses were measured from observations of CO(2–1) using ATCA." (2.3 Ancillary Data)
- Other facility **Herschel PACS/SPIRE, APEX/LABOCA, SPT**: far-IR/submm photometry for SED fits and luminosities  
  > "the available data include *Herschel*/PACS and SPIRE data at 100, 160, 250, 350, and 500 $\mu\rm{m}$, APEX/LABOCA 870 $\mu\rm{m}$, the SPT 1.4, 2, and 3 mm photometry" (2.3 Ancillary Data)
- External data: Molecular gas masses from CO(2-1) ATCA, with updated magnifications  
  > "$M_{\rm{H}_2}$ from (cite: aravena16) and Aravena et al. in prep. using updated magnifications from this work." (Table 1) [from (cite: aravena16)]
- External data: Low-redshift OH absorption comparison samples (published properties)  
  > "For these low-redshift samples, we adopt the sample properties as published by the original authors." (2.4 Literature Comparison Samples) [from (cite: veilleux13; spoon13; calderon16; herreracamus20; stone16)]
- External data: SPT2319-55 OH results reproduced from earlier paper  
  > "$^{b}$ Reproduced from (cite: spilker18a)." (Table 1) [from (cite: spilker18a)]
- External data: Spectroscopic redshifts and far-IR photometry  
  > "fitting to the available far-IR and submm photometry (cite: weiss13; strandet16; reuter20)" (2.3 Ancillary Data) [from (cite: weiss13; strandet16; reuter20)]

## Processing

### Calibration

- pipeline or manual: Standard pipelines for each ALMA cycle with additional manual calibration and flagging where necessary  
  > "The data were reduced with the standard pipelines available for each ALMA cycle, with additional manual calibration and flagging where necessary." (2.2 ALMA Observations)
- casa version: _not stated_
- pipeline version: _not stated_
- archive products used as is: _not stated_
- flux calibrator: _not stated_
- flux scale uncertainty: _not stated_
- self calibration: 1-2 rounds of phase-only self-cal, solution intervals of scan length or half scan length; successful for all except SPT2103-60; rms reduced up to factor 2  
  > "we attempted one or two rounds of phase-only self-calibration on the test and target sources, using solution intervals of the scan length or half the scan length." (2.2 ALMA Observations)

### Imaging

- task: _not stated_
- deconvolver: _not stated_
- weighting robust: natural weighting  
  > "We generate images of each target using natural weighting of the visibilities" (2.2 ALMA Observations)
- uv taper: _not stated_
- cell size: _not stated_
- image size: _not stated_
- masking: manual clean mask over high S/N emission; cleaned to 5x image noise  
  > "manually applying a clean mask over regions with clear, high S/N emission, and stopped the image cleaning at 5 times the image noise level" (2.2 ALMA Observations)
- multiscale scales: _not stated_
- continuum subtraction: _not stated_
- line free channels: _not stated_
- primary beam correction: _not stated_
- array combination: continuum images combine all available data  
  > "Continuum images were created combining all available data" (2.2 ALMA Observations)
- smoothing: cubes with channel widths 50-150 km/s; tapered cubes at 2-3x lower resolution as a check  
  > "image cubes of the OH lines were created with channel resolutions varying from 50–150 $\rm{km\,s}^{-1}$ in order to maximize the S/N" (2.2 ALMA Observations)
- final beam: _not stated_
- final rms: _not stated_

### Inherited from earlier work

- Pixellated lens modeling code and approach  
  > "utilizing the pixellated modeling code described in detail in (cite: hezaveh16), as in ." (3.3 Lens Modeling Methods and Tests) [from (cite: hezaveh16); Spilker et al. 2018 (cite: spilker18a)]
- Parametric source-plane lens fitting for initial lens parameters  
  > "a code that represents the source plane with one or more simple parametric light profiles (cite: spilker16)" (3.3 Lens Modeling Methods and Tests) [from (cite: spilker16)]
- Mock-data resolution/sensitivity tests of reconstructions  
  > "Following , we perform a series of reconstructions of mock data to test the resolution and sensitivity of the source reconstructions." (3.3.1 Model Selection and Tests) [from Spilker et al. 2018 (cite: spilker18a)]
- vmax defined as velocity above which 98% of absorption occurs  
  > "As in , here we take $v_\mathrm{max}$ to be the velocity above which 98% of the absorption occurs." (3.1 Spectral Analysis) [from Spilker et al. 2018 (cite: spilker18a)]
- CO(2-1) gas masses derived with same procedures as earlier paper  
  > "have been observed and analyzed using the same procedures and will be published elsewhere." (2.3 Ancillary Data) [from (cite: aravena16)]

### Not stated but needed to reproduce (our reading)

- CASA version and pipeline versions per cycle
- Line-free channel ranges and continuum-subtraction method for each source
- Cell size, image size, clean masks and exact tclean parameters
- Self-calibration solution intervals per source and exact flux/bandpass/phase calibrators
- MCMC settings (sampler, priors, chain lengths) for lens models; visilens/ripples configuration
- Pixel grid sizes in source and image planes
- Exact aperture definition for integrated spectra
- Systemic redshift velocity zero points used for each source
- Details of Gini/M20/multiplicity implementation and pixel selection
- Unpublished CO(2-1) ATCA data (Aravena et al. in prep.) for gas masses

## Analysis recipe

1. **Image continuum and OH cubes**: Natural-weighted cleaning with manual masks; continuum from all data; OH cubes with 50-150 km/s channels  
  > "We generate images of each target using natural weighting of the visibilities, which maximizes sensitivity at the expense of spatial resolution." (2.2 ALMA Observations)
   - software: CASA
   - parameter: clean threshold 5x image noise  
  > "stopped the image cleaning at 5 times the image noise level" (2.2 ALMA Observations)
   - fitting: _not stated_
   - validation: Tapered images at 2-3x lower resolution show no significant flux resolved out  
  > "find no evidence that significant flux has been resolved out in our observations" (2.2 ALMA Observations)
2. **Extract integrated OH spectra and fit Gaussian profiles**: Aperture photometry within region where continuum >3 sigma; fit one or two pairs of Gaussians with fixed doublet separation ~520 km/s and equal amplitudes; derive EW, v50, v84, vmax  
  > "we fit the integrated spectra with one or two pairs of Gaussians depending on the complexity of the line profile for each source." (3.1 Spectral Analysis)
   - parameter: free params: continuum, absorption depth, velocity offset, width per component  
  > "The free parameters are the continuum flux density and either one or two of each of the absorption depth, the velocity offset relative to the systemic, and Gaussian line width." (3.1 Spectral Analysis)
   - assumption: constant continuum across the band; alternate-sideband continuum or SED used when few line-free channels  
  > "We assume a constant continuum flux density across the relatively narrow bandwidth of these observations." (3.1 Spectral Analysis)
   - fitting: Gaussian fits; sampler/likelihood not stated  
  > "we fit the integrated spectra with one or two pairs of Gaussians depending on the complexity of the line profile for each source." (3.1 Spectral Analysis)
   - validation: Tested alternate-sideband continuum on sources with line-free bandwidth in both sidebands; no appreciable differences  
  > "We tested this procedure using the sources with sufficient line-free bandwidth in both sidebands and find no appreciable differences in the OH fit parameters." (3.1 Spectral Analysis)
3. **Classify outflow vs not**: Outflow if OH absorption is more blueshifted than detected [CII] or CO emission; compared with v50<-50 km/s criterion  
  > "we define a source as containing an outflow if it shows OH absorption more blueshifted than the detected \[CII\] or CO emission, which we expect to be a conservative definition." (3.2 Molecular Outflow Classification)
   - assumption: systemic redshift from [CII] (5 sources) or S/N-weighted stacked CO lines  
  > "we instead stack the spectra of all available transitions of CO for each source, weighted by the S/N of each line." (2.3 Ancillary Data)
   - fitting: _not stated_
   - validation: Binomial statistics for the detection rate; v50 alternative gives 7/11  
  > "would still result in 7/11 sources being classified as showing outflows" (3.2 Molecular Outflow Classification)
4. **Lens model continuum and reconstruct OH absorption components**: Pixellated visibility-space lens modeling with SIE (+shear, multipoles) and gradient regularization; lens parameters from continuum then applied to OH velocity ranges  
  > "We fit for the lensing potential using a Markov Chain Monte Carlo (MCMC) sampling algorithm." (3.3 Lens Modeling Methods and Tests)
   - software: ripples, visilens
   - parameter: visibilities averaged temporally unless binned visibility spans >10 m in uv  
  > "which we average temporally unless doing so would cause a binned visibility to span more than 10m in the $uv$ plane" (3.3 Lens Modeling Methods and Tests)
   - assumption: Regularization strength set by maximizing Bayesian evidence for fixed lens parameters, iterated  
  > "The best-fit strength of the regularization is determined by maximizing the Bayesian evidence given a fixed set of parameters for the lensing potential." (3.3 Lens Modeling Methods and Tests)
   - fitting: MCMC for lens potential; iterative regularization/MCMC; priors not stated  
  > "we perform an iterative process of fitting for the regularization strength, MCMC fitting for the lens parameters, and re-fitting for the regularization strength until all parameters have converged." (3.3 Lens Modeling Methods and Tests)
   - validation: Deviance information criterion, negative-bowl check (>=10% of peak), mock point-source tests across source plane (recover fluxes to ~25%)  
  > "This final test shows that even these weak signals are recoverable to $\approx$25% accuracy." (3.3.1 Model Selection and Tests)
5. **Measure covering fractions and clumpiness**: Covering fraction as fraction of pixels with detectable absorption where continuum S/N>10; Gini, M20, multiplicity on equivalent-width maps; MC noise for uncertainties  
  > "We calculate uncertainties for these measurements through a Monte Carlo procedure, adding normally-distributed noise to the reconstructions and re-measuring $G$, $M_{20}$, and $\Psi$" (4.4 Ubiquitous Clumpy Molecular Outflows)
   - parameter: continuum S/N>10 pixels; differences relative to continuum  
  > "measured from the equivalent width maps and for pixels where the continuum S/N$>$10" (4.4 Ubiquitous Clumpy Molecular Outflows)
   - assumption: OH 119 um absorption optically thick so absorption depth equals covering fraction  
  > "wherever OH is present along the line of sight $\sim$100% of the 119 $\mu\rm{m}$ continuum light is absorbed" (5.1 Expectations and Prospects for Detecting Small-Scale Clumpiness)
   - fitting: _not stated_
   - validation: Conclusions unchanged using absorbed flux maps instead of equivalent width  
  > "our conclusions are unchanged if we use the absorbed flux maps instead" (4.4 Ubiquitous Clumpy Molecular Outflows)
6. **Search for [CII] high-velocity wings and stack**: Compare OH and [CII] profiles for four sources; stack [CII] after linear continuum subtraction excluding |v|<500 km/s, regridding and peak normalizing  
  > "We construct this stack by subtracting a linear continuum from the integrated spectrum of each source excluding velocities $|v| < 500$ $\rm{km\,s}^{-1}$" (5.2 [CII] is Not a Reliable Molecular Outflow Tracer)
   - fitting: _not stated_
   - validation: Tried other stacking and continuum subtraction methods; result insensitive  
  > "We tried a variety of other stacking procedures and continuum subtraction methods and found that our result is not sensitive to these details" (5.2 [CII] is Not a Reliable Molecular Outflow Tracer)

## Software

- **CASA** : data reduction and imaging  
  > "CASA (cite: mcmullin07), `visilens` (cite: spilker16), `ripples` (cite: hezaveh16)" (Software)
- **visilens** : parametric lens modeling for initial lens parameters  
  > "a code that represents the source plane with one or more simple parametric light profiles (cite: spilker16)" (3.3 Lens Modeling Methods and Tests)
- **ripples** : pixellated lens modeling code  
  > "`ripples` (cite: hezaveh16)" (Software)
- **CIGALE** : SED fitting to limit AGN fraction  
  > "We use the CIGALE SED fitting code (cite: burgarella05; boquien19) to place limits on the fractional AGN contribution" (2.3 Ancillary Data)
- **astropy** : general analysis  
  > "`astropy` (cite: astropy18), `matplotlib` (cite: hunter07)" (Software)

## Numeric results

| quantity | value | uncertainty | units | step | quote |
|---|---|---|---|---|---|
| Outflow detection rate | 8/11 (73%) | ±13% | percent | 3 | Assuming binomial statistics, the outflow detection rate is 73$\pm$13%. |
| Equivalent width KS test p-value (high-z vs low-z) | 0.004 | not stated | dimensionless | 2 | a two-sided KS test rejects the hypothesis that the two samples are drawn from the same underlying distribution ($p=0.004$) |
| Outflow covering fraction from reconstructions | 30-85% | not stated | percent | 5 | We find generally high covering fractions ranging from 30–85% for the outflows or 40–95% for the systemic absorption. |
| Maximum outflow velocities | 430-1200 | not stated | km/s | 2 | The outflows reach maximum velocities 430–1200$\rm{km\,s}^{-1}$ and possibly faster. |
| Implied biconical opening angle | ~150 | not stated | degrees | 3 | our detection rate would correspond to an opening angle of $\sim$150$^\circ$ |
| Predicted clump scale | 50-200 | not stated | pc | 5 | the true size scale of clumps in the molecular outflows we have observed is of the order 50–200 pc |
| Molecular outflow masses for four [CII] sources | 40-80e7 | not stated | Msun | 0 | we find best estimates for the molecular outflow masses for these four sources $\sim40-80\times10^7$ $\rm{M}_\odot$ |

## Qualitative findings

- Outflows are significantly clumpier than the dust continuum; all by at least two metrics, 6 of 8 by all three  
  > "All outflows would be considered as clumpier by at least two metrics, and 6 of 8 outflows by all three metrics." (4.4 Ubiquitous Clumpy Molecular Outflows)
- No high-velocity [CII] wings in sources with clear OH outflows  
  > "We do not detect high-velocity \[CII\] wings in any of the sources with clear OH outflows" (abstract)

## Claim tuples

- H: Molecular outflows are common in z>4 DSFGs | E: ALMA Band 8 OH 119 um absorption in 11 lensed SPT DSFGs, classified relative to [CII]/CO emission | R: 8/11 (73±13%) show unambiguous outflows | F: Outflows have near-unity occurrence and large opening angles | **supported**
- H: Outflows are clumpy on ~500 pc scales | E: Lens reconstructions and Gini/M20/multiplicity metrics comparing absorption to continuum | R: outflows clumpier than continuum by at least two metrics in all sources | F: Clumpy structure is common; clumps unresolved, expected 50-200 pc | **supported**
- H: [CII] wings trace molecular outflows | E: Compare OH and [CII] for four sources and stack | R: no excess [CII] emission at OH outflow velocities | F: [CII] is not a reliable molecular outflow tracer | **supported**
- H: High-z OH absorption and outflow velocities resemble low-z ULIRGs | E: KS tests against Herschel low-z samples | R: velocity distributions indistinguishable; equivalent widths larger at high z (p=0.004) | F: similar velocities but stronger OH absorption at high z | **partially**

## Reasoning

- Why this data: _not stated_
- Why this method: Absorption-based OH simplifies geometry; lensing allows spatially resolving absorption  
  > "All targets are gravitationally lensed by foreground galaxies, which allows us to spatially resolve both the rest-frame 120 $\mu\rm{m}$ dust continuum emission as well as the OH absorption" (1 Introduction)
- Alternative: v50 < -50 km/s outflow criterion rejected as biased by systemic absorption and arbitrary systemic velocity  
  > "For a variety of reasons we find this definition unsatisfying for our sample." (3.2 Molecular Outflow Classification)
- How they decided it was enough: _not stated_
- Limitation (authors): Limited ALMA bandwidth prevents detection of redshifted P Cygni emission and caps vmax  
  > "our ability to detect redshifted emission as in the classic P Cygni profile is limited due to the small ALMA bandwidth" (4.1 Molecular Outflow Detection Rate)
- Limitation (authors): Conservative classification is S/N dependent and may exclude weak outflows  
  > "This definition has the drawback of being signal-to-noise dependent, which may exclude weak outflows" (3.2 Molecular Outflow Classification)
- Caveat (inferred, ours): Sample is extreme and lensed, not representative
- Caveat (inferred, ours): Outflow classification depends on reference CO/[CII] spectra and arbitrary velocity ranges
- Caveat (inferred, ours): Small sample; Gaussian fits non-unique
- Caveat (inferred, ours): Covering fraction discrepancy between spectra and reconstructions unresolved
- Caveat (inferred, ours): Lens-model systematics (e.g. unsubtracted lens emission, multiple lenses)

## Reproducibility

- Data public (paper): Sample property tables on GitHub; ALMA data cited by project code  
  > "Tables of the sample properties from this work, as well as the outflow properties from , are available in electronic form at <https://github.com/spt-smg/publicdata>." (1 Introduction)
- Products in archive: _not stated_
- Missing: Lens-modeling code configuration and priors
- Missing: CASA version and exact imaging parameters
- Missing: Line-free channel definitions
- Missing: Unpublished ATCA CO(2-1) data
- Data volume (inferred): ~100-300 GB for 10 sources across 4 ALMA Band 8 projects (raw); pipeline products smaller
- Score (inferred): 3/5, ALMA projects and many analysis choices are stated, but lens-model settings, CASA versions and imaging parameters are missing and lens code is partly in-house.
- Rediscovery candidate: no, Key results depend on custom lens reconstruction code and incompletely specified settings, though data are archival and some results are numeric.

## Links

- Method: (cite: hezaveh16) (pixellated lens modeling code)
- Method: (cite: spilker16) (parametric lens modeling code and earlier lens models)
- Method: (cite: spilker18a) (first z>4 OH outflow detection; methods followed)
- Companion: (cite: spilker20a) (Paper II: outflow physical properties, rates and energetics)
- Related: SPT 2500 deg2 survey DSFG sample
- Related: Herschel SHINING and HERUS OH samples
- Related: ALPINE

## Checks

```json
{
 "quotes": 85,
 "quotes_ok": 85,
 "quote_pass_rate": 1.0,
 "quotes_too_long": 0,
 "unsupported_facts": 0,
 "project_codes": 5,
 "codes_not_in_text": [],
 "codes_not_in_obscore": [
  "2016.1.01499.S"
 ],
 "obscore_codes_not_in_card": [],
 "codes_printed_but_missing": [],
 "numeric_results": 7,
 "numeric_problems": 0,
 "fill": {
  "facts": 90,
  "stated": 63,
  "rate": 0.7
 },
 "evidence_ok": true
}
```
