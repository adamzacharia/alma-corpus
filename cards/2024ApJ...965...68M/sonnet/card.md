# ALMA Confirmation of Millimeter Time Variability in the Gamma-Ray Detected Seyfert Galaxy GRS 1734-292

`2024ApJ...965...68M` | The Astrophysical Journal 2024 | first author: Michiyama, Tomonari | arXiv: 2404.00647 | DOI: 10.3847/1538-4357/ad2fae

Card schema 1.0 | model claude-sonnet-5-5 | depth full | type observational_alma_primary

## Science

- Fields: agn_and_quasars
- Question: Does the gamma-ray detected radio-quiet Seyfert GRS 1734-292 show a compact millimeter excess with time variability, and does it come from the corona or disk winds?  
  > "This paper presents ALMA observations of GRS 1734-292 and investigates millimeter emissions originally either from the corona or disk winds." (Introduction)
- Target **GRS 1734-292**: coordinates _not stated_; z/distance z = 0.0214  
  > "GRS 1734-292 at $z=0.0214$ is the fifth nearby galaxy among Fermi-detected Seyferts" (2.1 Fermi detection of GRS 1734-292); distance from optical spectroscopy (Marti et al. 1998)  
  > "GRS 1734-292 at $z=0.0214$ is the fifth nearby galaxy among Fermi-detected Seyferts" (2.1 Fermi detection of GRS 1734-292)

## Data provenance

- ALMA projects: 2018.1.00576.S
- bands: Band 3, 4, 6 (97.5, 145, 225 GHz)  
  > "using Band 3, 4, and 6 receivers" (3 ALMA observations)
- frequencies and spectral setup: B3 90.521, 92.416, 102.521, 104.479 GHz; B4 138.021, 139.916, 150.021, 151.979; B6 224, 226, 240, 242  
  > "138.021, 139.916, 150.021, 151.979" (Table 1)
- continuum bandwidth: _not stated_
- arrays: _not stated_
- configurations: _not stated_
- baselines: 41.4 m to ~3640-3737 m  
  > "41.4, 3637.7 (1.7$''$)" (Table 1)
- angular resolution: Beams 0.29x0.16'' (B3 d1), 0.24x0.18'' (B3 d2), 0.19x0.11'' (B4), 0.14x0.07'' (B6)  
  > "B6 | 225 | $0.14\times0.07$" (Table 2)
- max recoverable scale: MRS 1.7'' (B6), 4.3''/4.1'' (B3), 2.9'' (B4)  
  > "41.4, 3637.6 (2.9$''$)" (Table 1)
- sensitivity: rms 0.036-0.046 mJy/beam  
  > "B6 | 225 | $0.14\times0.07$ | 0.046" (Table 2)
- time on source: _not stated_
- observing dates: 2019-08-14 and 2019-08-18  
  > "we observed GRS 1734-292 on August 14th and 18th, 2019" (3 ALMA observations)
- pi or archival as stated: _not stated_
- Other facility **VLA**: 8.5 GHz map and archival continuum fluxes (14/15 GHz) for jet contamination  
  > "Figure [4](#fig:ALMA_VLA) shows the Very Large Array (VLA) 8.5 GHz map" (4.2 Millimeter excess)
- Other facility **Fermi-LAT**: 4FGL-DR3 gamma-ray detection  
  > "The source named as 4FGL J1737.1-2901 is the gamma-ray candidate of GRS 1734-292" (2.1 Fermi detection of GRS 1734-292)
- External data: Black hole mass log M_BH = 8.50±0.50; coronal kTe=11.9 keV and tau=2.98  
  > "The black hole mass is measured as $\log{(M_{\rm BH}\,[M_{\odot}])}=8.50\pm0.50$" (2.2 Details of GRS 1734-292) [from Tortosa et al. 2017 (cite: Tortosa2017MNRAS.466.4193T)]
- External data: Global jet spectrum S=76 (nu/GHz)^-0.75 mJy  
  > "the global jet spectrum follows $S_{\mu}\approx76(\mu/{\rm GHz})^{-0.75}$" (4.2 Millimeter excess) [from (cite: Marti1998A&A...330...72M)]

## Processing

### Calibration

- pipeline or manual: Provided calibration scripts run in CASA  
  > "The raw visibility data was calibrated using `CASA` (cite: McMullin_2007ASPC..376..127M; CASA2022arXiv221002276T) by running the provided calibration scripts." (3 ALMA observations)
- casa version: _not stated_
- pipeline version: _not stated_
- archive products used as is: _not stated_
- flux calibrator: _not stated_
- flux scale uncertainty: amplitude calibration error up to 5% at Band 3  
  > "the amplitude calibration error of the ALMA design can be as high as 5 % at Band 3" (4.1 Time variability)
- self calibration: _not stated_

### Imaging

- task: clean in CASA  
  > "The continuum images were generated using `clean` in `CASA`" (3 ALMA observations)
- deconvolver: _not stated_
- weighting robust: Briggs, robust = -0.2  
  > "Briggs weighting with a robust parameter of $-0.2$" (3 ALMA observations)
- uv taper: _not stated_
- cell size: 0.03''  
  > "with a cell size of 0.03$''$" (3 ALMA observations)
- image size: 3000 pixels  
  > "an image size of 3000 pixels" (3 ALMA observations)
- masking: automatic masking (sidelobethreshold 2.0, noisethreshold 3.0, lownoisethreshold 2.0, minbeamfrac 0.3, growiterations 75, negativethreshold 0.0)  
  > "sidelobethreshold = 2.0, noisethreshold = 3.0, lownoisethreshold = 2.0, minbeamfrac = 0.3, growiterations = 75, and negativethreshold = 0.0" (3 ALMA observations)
- multiscale scales: _not stated_
- continuum subtraction: _not stated_
- line free channels: _not stated_
- primary beam correction: _not stated_
- array combination: _not stated_
- smoothing: beam matched to 0.3'' and uv-clipped >40 klambda for flux comparison  
  > "we also made beam matched ($0.3\ensuremath{''}$) and uv-clipped ($>40\,{\mathrm k\lambda}$) images" (3 ALMA observations)
- final beam: _not stated_
- final rms: _not stated_

### Inherited from earlier work

- Corona SSA magnetic field and size derived following Inoue et al. 2020 and Inoue & Doi 2014 calculations  
  > "The detailed calculation processes are given in (cite: Inoue2014PASJ...66L...8I)." (4.3 Corona) [from (cite: Inoue2020ApJ...891L..33I); (cite: Inoue2014PASJ...66L...8I)]
- Wind synchrotron/free-free model formulation  
  > "(See (cite: Nims2015MNRAS.447.3612N) for the detailed formulation)" (4.4 Disk wind) [from (cite: Nims2015MNRAS.447.3612N)]

### Not stated but needed to reproduce (our reading)

- Line-free channels / spectral windows used for continuum
- Number of CASA clean iterations and thresholds, niter
- Exact CASA and pipeline versions
- emcee settings (walkers, steps, priors, likelihood)
- How the VLA 15 GHz unresolved flux was measured
- Flux calibrator names and flux values
- Wind model parameters beyond those listed
- Coordinates of target

## Analysis recipe

1. **calibrate and image continuum**: Run provided calibration scripts, tclean-style clean with automasking at Bands 3, 4, 6  
  > "The continuum images were generated using `clean` in `CASA`" (3 ALMA observations)
   - software: CASA
   - parameter: cell 0.03'', 3000 pix, robust -0.2  
  > "with a cell size of 0.03$''$, an image size of 3000 pixels" (3 ALMA observations)
   - fitting: _not stated_
   - validation: _not stated_
2. **measure matched-beam fluxes**: Beam-matched 0.3'' uv-clipped images; peak flux and 2D Gaussian fit  
  > "$F_{0.3\ensuremath{''}}^{\rm imfit}$ is the total flux measured by the 2D Gaussian fit (`imfit` task in `CASA`)" (3 ALMA observations)
   - software: CASA
   - fitting: 2D Gaussian (imfit)  
  > "2D Gaussian fit (`imfit` task in `CASA`)" (3 ALMA observations)
   - validation: Variability checked per spw, phase calibrator and check source flux, extended component consistency  
  > "we have confirmed the presence of time variability in each spectral window (spw), ruling out spurious effects in specific spectral windows" (4.1 Time variability)
3. **fit coronal SSA + jet SED**: Bayesian fit of SSA corona model plus jet fraction to ALMA B3/4/6 day-1 and VLA 15 GHz fluxes  
  > "We use ALMA Band 3, 4, and 6 flux in day-1 and VLA 15 GHz un-resolved flux as the input data" (4.3 Corona)
   - software: emcee
   - parameter: p = 2.7  
  > "assuming $p=2.7$" (4.3 Corona)
   - assumption: kTe=11.9 keV, tau=2.98 from Tortosa 2017  
  > "we assume a temperature of the coronal plasma of $kT_{\rm e}=11.9^{+1.2}_{-0.9}$ keV" (4.3 Corona)
   - fitting: Bayesian parameter estimation (emcee); 16/50/84th percentiles  
  > "the errors are calculated based on the 16th, 50th, and 84th percentiles of the posterior distributions" (4.3 Corona)
   - validation: _not stated_
4. **derive B and size, test alternatives**: Convert SSA parameters to B and R; compare with wind and jet-base models  
  > "correspond to the coronal magnetic field $B\approx10$ G and the size $R\approx10\,R_{\rm s}$" (4.3 Corona)
   - fitting: _not stated_
   - validation: _not stated_

## Software

- **CASA** : calibration, imaging, imfit  
  > "The raw visibility data was calibrated using `CASA`" (3 ALMA observations)
- **emcee** : Bayesian parameter estimation of SSA parameters  
  > "Using the Bayesian parameter estimation technique developed by (cite: Foreman-Mackey2013PASP..125..306F)" (4.3 Corona)
- **Astropy** : listed in software  
  > "Astropy (cite: 2022ApJ...935..167A; 2018AJ....156..123A; 2013A&A...558A..33A)" (Software)

## Numeric results

| quantity | value | uncertainty | units | step | quote |
|---|---|---|---|---|---|
| 97.5 GHz peak flux (0.3'') day 1 | 1.45 | 0.06 | mJy | 2 | B3 (d1) / 97.5 / $0.29\times0.16$ / 0.038 / 1.6 / $2.2\pm0.1$ / $1.45\pm0.06$ |
| 97.5 GHz peak flux (0.3'') day 2 | 2.5 | 0.06 | mJy | 2 | B3 (d2) / 97.5 / $0.24\times0.18$ / 0.04 / 2.5 / $3.1\pm0.1$ / $2.5\pm0.06$ |
| Variability at 97.5 GHz over four days | 70 | not stated | % | 2 | corresponding to a 70% variability in four days |
| S_nu_SSA | 1.5 | +0.08/-0.08 | mJy | 3 | ($1.5^{+0.08}_{-0.08}$ mJy, $110^{+13}_{-6}$ GHz, $0.26^{+0.02}_{-0.02}$) |
| nu_SSA | 110 | +13/-6 | GHz | 3 | ($1.5^{+0.08}_{-0.08}$ mJy, $110^{+13}_{-6}$ GHz, $0.26^{+0.02}_{-0.02}$) |
| jet fraction f_jet | 0.26 | +0.02/-0.02 | dimensionless | 3 | ($1.5^{+0.08}_{-0.08}$ mJy, $110^{+13}_{-6}$ GHz, $0.26^{+0.02}_{-0.02}$) |
| coronal magnetic field | ≈10 | not stated | G | 4 | correspond to the coronal magnetic field $B\approx10$ G and the size $R\approx10\,R_{\rm s}$ |
| coronal size | ≈10 | not stated | R_s | 4 | correspond to the coronal magnetic field $B\approx10$ G and the size $R\approx10\,R_{\rm s}$ |

## Qualitative findings

- Wind of ~10 pc could give ~2 mJy at ~100 GHz but struggles to explain fast variability; jet-base scenario judged untenable.  
  > "Therefore, the jet-base scenario might be untenable." (4.5 Jet base)

## Claim tuples

- H: Is the nuclear millimeter emission variable? | E: Compare two Band 3 epochs four days apart with calibrator checks | R: 1.45 vs 2.5 mJy, ~70% change | F: Time variability is significant, implying a compact source (<~100 Rs) | **supported**
- H: Is there a millimeter excess beyond jet and dust? | E: Compare ALMA fluxes with the extrapolated jet spectrum and a dust spectral index | R: ALMA flux exceeds the beam-limited jet component; flat spectrum | F: Millimeter excess confirmed | **supported**
- H: Does coronal synchrotron explain the excess? | E: SSA+jet fit to the SED | R: B≈10 G, R≈10 Rs | F: Corona is the favored origin; the disk wind remains a possible contaminant | **partially**

## Reasoning

- Why this data: Target chosen for significant gamma-ray flux and absence of intense starburst and jet activity  
  > "we have identified GRS 1734-292 (AX J1737.4-2907) as an optimal target due to its significant gamma-ray flux, coupled with an absence of intense starburst and jet activity" (Introduction)
- Why this method: _not stated_
- Alternative: Jet synchrotron, dust blackbody, disk wind, and jet base considered; mostly disfavored  
  > "the alternative potential sources, such as extended (e.g., $>100\,R_{\rm s}$) jet synchrotron and dust blackbody, can not exhibit daily time variability" (4.1 Time variability)
- How they decided it was enough: _not stated_
- Limitation (authors): Only two epochs; higher resolution needed to separate corona and wind  
  > "it is crucial to validate the light curve using more than two observing epochs in both millimeter bands and X-ray" (6 Summary)
- Caveat (inferred, ours): Only two epochs at Band 3 and non-simultaneous B4/B6
- Caveat (inferred, ours): Variability argument relies on 5% flux scale accuracy
- Caveat (inferred, ours): Fit has 3 parameters with 4 data points; priors unstated
- Caveat (inferred, ours): Jet fraction model assumes fixed global jet spectrum
- Caveat (inferred, ours): Single-dish-like beam mixing of extended emission

## Reproducibility

- Data public (paper): ALMA data from project 2018.1.00576.S retrieved via JVO / archive  
  > "Some of the ALMA data were retrieved from the JVO portal" (Acknowledgments)
- Products in archive: _not stated_
- Missing: emcee configuration and priors
- Missing: VLA flux extraction details
- Missing: Wind/corona conversion formulas (in cited papers)
- Data volume (inferred): ~50-100 GB raw for four execution blocks
- Score (inferred): 3/5, Imaging parameters given and data public, but fitting setup and conversion to B/R rely on cited works.
- Rediscovery candidate: yes, Public data, stated imaging recipe, numeric flux results; fit details partly missing.

## Links

- Method: (cite: Inoue2014PASJ...66L...8I) (Corona SSA model and calculation of B and R)
- Method: (cite: Foreman-Mackey2013PASP..125..306F) (emcee MCMC)
- Companion: (cite: Kawamuro2022ApJ...938...87K) (Used the same ALMA dataset in a statistical analysis)
- Companion: Yamada et al. under review at ApJ (Disk wind radio SED details)
- Related: ALMA Cycle 6 project 2018.1.00576.S

## Checks

```json
{
 "quotes": 55,
 "quotes_ok": 55,
 "quote_pass_rate": 1.0,
 "quotes_too_long": 0,
 "unsupported_facts": 0,
 "project_codes": 1,
 "codes_not_in_text": [],
 "codes_not_in_obscore": [],
 "obscore_codes_not_in_card": [],
 "codes_printed_but_missing": [],
 "numeric_results": 8,
 "numeric_problems": 0,
 "fill": {
  "facts": 70,
  "stated": 42,
  "rate": 0.6
 },
 "evidence_ok": true
}
```
