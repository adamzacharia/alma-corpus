# VALES VI: ISM enrichment in star-forming galaxies up to z ∼ 0.2 using <SUP>12</SUP>CO(1-0), <SUP>13</SUP>CO(1-0), and C<SUP>18</SUP>O(1-0) line luminosity ratios

`2020MNRAS.497.2771M` | Monthly Notices of the Royal Astronomical Society 2020 | first author: Méndez-Hernández, H. | arXiv: 2007.01182 | DOI: 10.1093/mnras/staa1964

Card schema 1.0 | model claude-sonnet-5-5 | depth full | type observational_alma_primary

## Science

- Fields: nearby_galaxies
- Question: How do the 12CO/13CO and 13CO/C18O line luminosity ratios of low-z star-forming galaxies depend on global galaxy properties (SFR, SFE, LIR, morphology), probing ISM enrichment?  
  > "to explore the $L'$ ($^{12}$CO($1-0$) )/$L'$ ($^{13}$CO($1-0$))) (hereafter $L'$ ($^{12}$CO )/$L'$ ($^{13}$CO)) and $L'$ ($^{13}$CO($1-0$) )/$L'$ (C$^{18}$O($1-0$)) (hereafter $L'$ ($^{13}$CO )/$L'$ (C$^{18}$O) line luminosity ratio dependence" (abstract)
- Target **27 VALES galaxies (H-ATLAS, 0.02<z<0.2)**: coordinates not stated (HATLAS names listed in Table)  
  > "Galaxies were selected using a spectroscopic redshift at 0.02$<z<0.2$, and a *Herschel* detection near the peak of the spectral energy distribution (SED) of a normal star-forming galaxy" (2.1 Sample); z/distance 0.02<z<0.2; luminosity distances from LCDM H0=70, OmegaM=0.3, OmegaL=0.7  
  > "Galaxies were selected using a spectroscopic redshift at 0.02$<z<0.2$, and a *Herschel* detection near the peak of the spectral energy distribution (SED) of a normal star-forming galaxy" (2.1 Sample); distance from GAMA spectroscopic redshifts; cosmology assumed  
  > "Galaxies were selected using a spectroscopic redshift at 0.02$<z<0.2$, and a *Herschel* detection near the peak of the spectral energy distribution (SED) of a normal star-forming galaxy" (2.1 Sample)

## Data provenance

- ALMA projects: 2013.1.00530.S
- bands: Band 3  
  > "Observations with ALMA in band-3 were performed as part of project 2013.1.00530.S (P.I.  E. Ibar)" (2.2 ALMA observations)
- frequencies and spectral setup: three spectral setups, four spectral windows each covering 7.5 GHz bandwidth  
  > "we could observe all 27 galaxies using just three spectral setups (each one using four spectral windows to cover 7.5 GHz of bandwidth)" (2.2 ALMA observations)
- continuum bandwidth: _not stated_
- arrays: _not stated_
- configurations: compact configuration, max baseline ~300 m  
  > "in compact configuration (maximum baseline of $\sim$300 m)" (2.2 ALMA observations)
- baselines: _not stated_
- angular resolution: natural-weighted beam 3-4 arcsec; fixed to 4.5 arcsec  
  > "This yielded a restoring beam between 3$"$ and 4$"$, nevertheless for the purposes of this work, we fixed the restoring beam to a common value, at $4.5\ensuremath{''}$" (2.2 ALMA observations)
- max recoverable scale: _not stated_
- sensitivity: 0.9 mJy/beam at 30 km/s for 13CO and C18O; continuum rms 4 uJy/beam  
  > "The $^{13}$CO($1-0$) and C$^{18}$O($1-0$) observations reached rms noise of 0.9 mJy beam$^{-1}$ at 30 km s$^{-1}$ channel width" (2.2 ALMA observations)
- time on source: _not stated_
- observing dates: 23-25 January 2015  
  > "were taken between 23 and 25 January 2015" (2.2 ALMA observations)
- pi or archival as stated: PI E. Ibar, project 2013.1.00530.S  
  > "project 2013.1.00530.S (P.I.  E. Ibar)" (2.2 ALMA observations)
- Line: 12CO 1-0 (115.271 GHz)
- Line: 13CO 1-0 (110.201 GHz)
- Line: C18O 1-0 (109.782 GHz)
- Other facility **Herschel / H-ATLAS**: parent sample, [CII] detections, far-IR photometry  
  > "previously detected by *Herschel* in \[C ii\] ((cite: Ibar15))" (2.1 Sample)
- Other facility **GAMA**: spectroscopic redshifts and multiwavelength imaging for morphology  
  > "have high-quality spectra from the Galaxy and Mass Assembly survey" (2.1 Sample)
- External data: 12CO(1-0) data, SFR, SFE, Sigma_SFR, Sigma_H2, M*, morphology classes and line widths of VALES galaxies  
  > "(cite: Villanueva17) derived various global galaxy properties, including star formation rate (SFR), star formation efficiency (SFE), molecular gas surface density" (4.1.2 The star-formation activity) [from (cite: Villanueva17)]
- External data: LIR from SED fitting  
  > "The total IR luminosity was obtained as described in (cite: Ibar15) by integrating the best-fitting SED between 8 and 1000 $\mu$m" (4.1.2 The star-formation activity) [from (cite: Ibar15)]
- External data: 12CO/13CO ratios and LFIR for 61 nearby normal and starburst galaxies used in Spearman test  
  > "if we also consider starburst galaxies and normal galaxies covering a wider range of $L_{\rm FIR}$ as reported by (cite: Taniguchi98)" (4.1.2 The star-formation activity) [from (cite: Taniguchi98)]

## Processing

### Calibration

- pipeline or manual: common custom pipeline in CASA, as in Villanueva17  
  > "Data reduction and imaging were performed using the same procedure as in (cite: Villanueva17), where we developed a common pipeline" (2.2 ALMA observations)
- casa version: CASA 4.4.0  
  > "a common pipeline within the Common Astronomy Software Applications (CASA version 4.4.0) to process all of the science goals" (2.2 ALMA observations)
- pipeline version: _not stated_
- archive products used as is: _not stated_
- flux calibrator: Ganymede, J0750+125, J0854+201 (varies by execution)  
  > "| J085340.7+013348, J085405.9+011130  | 2015 January 24 (1/3)     | Ganymede   | J1058+0133 | J0909+0121 | 5.9    |" (Table 1 (observations))
- flux scale uncertainty: _not stated_
- self calibration: _not stated_

### Imaging

- task: tclean  
  > "Each source was imaged with the tclean task using a natu- ral weighting." (2.2 ALMA observations)
- deconvolver: _not stated_
- weighting robust: natural weighting  
  > "Each source was imaged with the tclean task using a natu- ral weighting." (2.2 ALMA observations)
- uv taper: _not stated_
- cell size: _not stated_
- image size: _not stated_
- masking: _not stated_
- multiscale scales: _not stated_
- continuum subtraction: _not stated_
- line free channels: _not stated_
- primary beam correction: _not stated_
- array combination: _not stated_
- smoothing: channel width 125 km/s for 3D stacking; spectral coverage +/-2000 km/s  
  > "Using a common channel width of 125 km s$^{-1}$, a spectral coverage of $\pm$2000km s$^{-1}$, and a restoring beam with a FWHM of 4.5$''$" (3.1.2 3D-image stacking)
- final beam: 4.5 arcsec common restoring beam  
  > "we fixed the restoring beam to a common value, at $4.5\ensuremath{''}$, for all sources" (2.2 ALMA observations)
- final rms: stacked moment-0 rms: 108 mJy/beam km/s (12CO); 18 mJy/beam km/s (13CO, C18O)  
  > "reaching rms values of 108  mJy beam$^{-1}$  km s$^{-1}$ for the $^{12}$CO line and 18  mJy beam$^{-1}$  km s$^{-1}$ for the $^{13}$CO and C$^{18}$O emission lines" (3.1.1 2D-moment-0 stacking)

### Inherited from earlier work

- Data reduction and imaging procedure (common CASA pipeline)  
  > "Data reduction and imaging were performed using the same procedure as in (cite: Villanueva17)" (2.2 ALMA observations) [from (cite: Villanueva17)]
- Derivation of SFR, SFE, gas masses, surface densities and alpha_CO  
  > "A more detailed discussion about the computations of these parameters can be found in (cite: Villanueva17)." (4.1.2 The star-formation activity) [from (cite: Villanueva17)]
- Luminosity conversion formula  
  > "We compute the $^{12}$CO, $^{13}$CO and C$^{18}$O luminosities using the velocity integrated line flux densities following (cite: Solomon05)" (3.3 Luminosity measurements) [from (cite: Solomon05)]

### Not stated but needed to reproduce (our reading)

- Custom stacking code is not released; weighting (mean vs median, weights) for moment-0 stacking not specified
- Exact channel selection and line-free channels; continuum subtraction method not stated
- Astrometric offsets per galaxy and 12CO velocity offsets not tabulated
- Primary beam correction and image size/cell size not stated
- Details of uv stacking (stacker settings, weights)
- Moment-0 flux-extraction details (aperture, error estimate from 2D Gaussian fit)
- Redshift distribution sampling and number of Monte Carlo iterations for luminosity error
- Definition of low/high bin split thresholds

## Analysis recipe

1. **Image cubes and check individual detections**: tclean natural weighting at 4.5" beam; moment-0 maps collapsed over ±1 FWHM of 12CO at expected 13CO/C18O frequencies  
  > "we created moment-0 maps by collapsing the cube around $\pm1\times$ FWHM$_{^{12}\text{CO}}$ of the expected $^{13}$CO frequencies" (3 Analysis)
   - software: CASA
   - fitting: _not stated_
   - validation: 7 galaxies with SNR>5 in moment-0 13CO maps  
  > "In the collapsed images we identify 7 galaxies with SNR \> 5." (3 Analysis)
2. **Moment-0 stacking and flux extraction**: Align moment-0 maps with astrometric corrections (~1.4") and stack with custom code; fit 2D Gaussian (FWHM 4.5", point-like) on 30"x30" stamps  
  > "To extract velocity integrated line flux densities from the stacked signals, we create $30"\times30"$ stamps and model the sources with a 2D Gaussian profile" (3.1.1 2D-moment-0 stacking)
   - software: CASA immoments, custom stacking code
   - parameter: 12CO line widths measured at 20 km/s channels  
  > "we measure $^{12}$CO line widths using 20 km s$^{-1}$ channel for all galaxies" (3.1.1 2D-moment-0 stacking)
   - fitting: 2D Gaussian  
  > "we create $30"\times30"$ stamps and model the sources with a 2D Gaussian profile, assuming that the stacked signals are point-like with a FWHM of 4.5$''$." (2D-moment-0 stacking)
   - validation: Monte Carlo systematic errors; comparison with 3D and uv stacking  
  > "we ran Monte-Carlo simulations using data cubes with the same physical scales (pixel size, synthesised beam, primary beam) as those covered by the ALMA Band-3 observations." (Systematic Errors)
3. **Compare 3D and uv stacking**: 3D channel-by-channel stacking at optimal 125 km/s channel; uv stacking with stacker on averaged-channel uv data; compare SNR  
  > "we decided to use a common spectral channel width of 125 km s$^{-1}$ for $^{12}$CO, $^{13}$CO and C$^{18}$O" (3.1.2 3D-image stacking)
   - software: CASA tclean, CASA split, stacker
   - fitting: 1D Gaussian for line width then 2D Gaussian in central channel (3D)  
  > "we fitted a 1D Gaussian profile to obtain the global stacked velocity line width FWHM$_{f}$ (see Fig. [2](#fig:3DStack-Scheme1) lower panel). Hence, we took the central channel" (3D-image stacking)
   - validation: Moment-0 chosen as it gives highest 13CO SNR  
  > "we decide to use the 2D (moment-0) approach to measure values, as this method yields the highest $^{13}$CO stacked SNRs" (3.3 differences between the stacking approaches)
4. **Systematic errors from Monte Carlo**: Simulate 27 point-like cubes with Gaussian noise, 1000 trials, compare input/output flux  
  > "We repeat this process 1000 times, where amplitudes and velocity widths are simulated to take fixed values between 0 and 100 times the rms" (3.1.3 Systematic Errors)
   - fitting: _not stated_
   - validation: systematic errors 8%, 3%, 2% (3D) and 5%, 3%, 1% (2D) at SNR ~6, 13, 18  
  > "three different SNRs values $\sim$6, $\sim$13 and $\sim$18 at which our 3D-stacks show systematic errors of 8%, 3% and 2% while 2D-moment-0 stacks show 5%, 3% and 1%." (Systematic Errors)
5. **Compute luminosities and ratios for subsamples**: L' = 3.25e7 S dv nu_obs^-2 D_L^2 (1+z)^-3; Monte Carlo over flux errors and redshift distribution for CI; stack subsamples by morphology, LIR, SFR, SFE, Sigma  
  > "we have used a Monte Carlo simulation considering that the error from the velocity integrated line flux density measurements is normally distributed" (3.3 Luminosity measurements)
   - assumption: LCDM H0=70, OmegaM=0.3, OmegaL=0.7; Chabrier IMF; alpha_CO 4.6 (B,D) and 0.8 (mergers)  
  > "$\alpha_{\text{CO}}=4.6$ K km s$^{-1}$ pc$^{2}$ for B and D dominated galaxies and $\alpha_{\text{CO}}=0.8$ K km s$^{-1}$ pc$^{2}$ for mergers/interacting galaxies" (4.1.2 The star-formation activity)
   - fitting: _not stated_
   - validation: _not stated_
6. **Statistical tests of trends**: Student's t-test between low/high bins, Spearman rank test, KS test for galaxy property distributions  
  > "we applied a Student’s t-test to determine the probability that the $L'$ ($^{12}$CO )/$L'$ ($^{13}$CO) line luminosity ratio variations between the low and high $L_{\text{IR}}$ populations are not statistically significant" (4.1.2 The star-formation activity)
   - fitting: _not stated_
   - validation: outlier J090949.6+014847 excluded in Spearman; stacks robust to its removal  
  > "Stacking results are robust against the removal of this peculiar source from the sample." (4.1.3 13CO Individual detections)

## Software

- **CASA** 4.4.0: data reduction, tclean imaging, immoments, split, imfit  
  > "Common Astronomy Software Applications (CASA version 4.4.0)" (2.2 ALMA observations)
- **stacker** : uv-plane stacking  
  > "(cite: Lindroos15) developed *stacker* [^3], a tool which directly stacks interferometric continuum datasets in the $uv$-plane" (3.2 uv stacking)
- **Astropy** : general analysis  
  > "This research made use of Astropy,[^4] a community-developed core Python package for Astronomy" (Acknowledgements)

## Numeric results

| quantity | value | uncertainty | units | step | quote |
|---|---|---|---|---|---|
| Average L'(12CO)/L'(13CO), all 27 galaxies | 16.1 | 2.5 | dimensionless | 5 | Using all of the 27 galaxies, we find an average $L'$ ($^{12}$CO )/$L'$ ($^{13}$CO) line luminosity ratio of 16.1$\pm$2.5. |
| Average L'(13CO)/L'(C18O), 24 galaxies | 2.5 | 0.6 | dimensionless | 5 | The average $L'$ ($^{13}$CO )/$L'$ (C$^{18}$O) line luminosity ratio found is 2.5$\pm$0.6 |
| L'(12CO)/L'(13CO) for mergers | 22.1 | 8.6 | dimensionless | 5 | / 4 / M / 3 / 22.1 $\pm$ 8.6 / 34 $\pm$ 6.9 / 9.6 $\pm$ 0.8 / 11.5 $\pm$ 0.2 / |
| L'(12CO)/L'(13CO) low vs high SFR | 13.3 vs 18.7 | 2.4 and 3.8 | dimensionless | 6 | / \[10.3 - 83.4\] / 12 / 28.6 $\pm$ 5.3 / 18.7 $\pm$ 3.8 / |
| L'(13CO)/L'(C18O) low vs high SFE | 4.4 vs 2.1 | 1.2 and 0.5 | dimensionless | 6 | / SFE (Gyr$^{-1}$)                   / \[0.4 - 0.9\]   / 11 / 0.6 $\pm$ 0.1  / 12.4 $\pm$ 2.8                  / -4.8 / 7E-5   / 4.4 $\pm$ 1.2 |
| Stacked 13CO SNR (moment-0) | 15.1 | not stated | dimensionless | 2 | / $^{13}$CO /   15.1   /     12.9      /     9.5     /     / |
| Stacked ~110 GHz continuum SNR | 13 | not stated | dimensionless | 0 | we could detect a high signal-to-noise ratio (SNR=13) emission after stacking the individual continuum emission of our 27 galaxy sample |

## Qualitative findings

- Galaxies with high LIR, SFR and SFE show high 12CO/13CO and low 13CO/C18O ratios, interpreted as selective nucleosynthesis by massive stars in young starbursts; photodissociation and fractionation disfavoured.  
  > "suggesting that these trends are produced by selective enrichment of massive stars in young starbursts." (abstract)

## Claim tuples

- H: Stacking can detect faint 13CO and C18O in low-z galaxies | E: Moment-0, 3D, uv stacking of 27 galaxies | R: 13CO stacked SNR 15.1, C18O ~5 | F: Stacking pushes ALMA detectability limits | **supported**
- H: 12CO/13CO ratio depends on SFR, SFE, LIR | E: Split sample into low/high bins and t-test | R: Higher ratios for high LIR/SFR/SFE, p<0.001 | F: Significant positive trends | **supported**
- H: Mergers/companions have higher 12CO/13CO | E: Morphological subsets | R: Mergers 22.1 vs 10.7 without companion | F: Factor ~2 but low significance | **partially**
- H: Selective nucleosynthesis drives the ratios | E: Compare trends with photodissociation and fractionation expectations | R: Low 13CO/C18O with high LIR inconsistent with photodissociation; T>20 K rules out fractionation | F: Selective nucleosynthesis most probable | **partially**

## Reasoning

- Why this data: _not stated_
- Why this method: Moment-0 stacking chosen since it gives highest 13CO SNR and is simple, consistent with prior 12CO data.  
  > "this method yields the highest $^{13}$CO stacked SNRs that are straightforward to interpret and simple to calculate" (3.3)
- Alternative: 3D and uv stacking explored but not adopted for measurements  
  > "we decide to use the 2D (moment-0) approach to measure values" (3.3)
- How they decided it was enough: _not stated_
- Limitation (authors): Optical depth not accounted; 12CO/13CO luminosity ratios are lower limits to abundance ratios; degeneracy between starburst age and top-heavy IMF  
  > "the $L'$ ($^{12}$CO )/$L'$ ($^{13}$CO) luminosity ratios reported here should be taken as a lower limit of the $^{12}$CO/$^{13}$CO abundance ratio" (5.1)
- Caveat (inferred, ours): Small subsamples (3 mergers) and overlapping bins make t-test significances fragile
- Caveat (inferred, ours): SFR, LIR, and redshift are correlated so trends may be driven by redshift/beam dilution
- Caveat (inferred, ours): Blind 13CO extraction at 12CO-derived frequency and point-source assumption may bias fluxes
- Caveat (inferred, ours): Luminosity-weighted stacking mixes sources of differing redshift
- Caveat (inferred, ours): Table inconsistencies (e.g. N for BC,DC vs text n=8)

## Reproducibility

- Data public (paper): Data in ALMA Science Archive under 2013.1.00530.S  
  > "The data underlying this article are available in the ALMA Science Archive at <https://almascience.nrao.edu/asax/>, and can be accessed with the Project ID: 2013.1.00530.S." (Data Availability)
- Products in archive: _not stated_
- Code: _not stated_
- Missing: Custom stacking code
- Missing: Per-galaxy astrometric and velocity offsets
- Missing: Villanueva17 derived galaxy properties and 12CO line widths
- Missing: Stacking weights and bin definitions
- Data volume (inferred): ~50-150 GB raw for 27 Band 3 compact-array fields (several executions)
- Score (inferred): 3/5, Data public and method clear, but the stacking code, offsets and galaxy properties from earlier work are needed.
- Rediscovery candidate: no, Depends on unreleased custom stacking code and inputs from Villanueva17, so recipe is incomplete although data are public.

## Links

- Method: (cite: Villanueva17) (Same data reduction pipeline and derived galaxy properties)
- Method: (cite: Lindroos15) (stacker uv stacking tool)
- Method: (cite: Solomon05) (Luminosity conversion formula)
- Companion: (cite: Villanueva17) (VALES 12CO(1-0) ALMA observations of same sources)
- Companion: (cite: Ibar15) (VALES sample and [CII]/SED properties)
- Related: VALES
- Related: H-ATLAS
- Related: GAMA

## Checks

```json
{
 "quotes": 66,
 "quotes_ok": 66,
 "quote_pass_rate": 1.0,
 "quotes_too_long": 0,
 "unsupported_facts": 0,
 "project_codes": 1,
 "codes_not_in_text": [],
 "codes_not_in_obscore": [],
 "obscore_codes_not_in_card": [],
 "codes_printed_but_missing": [],
 "numeric_results": 7,
 "numeric_problems": 0,
 "fill": {
  "facts": 78,
  "stated": 50,
  "rate": 0.641
 },
 "evidence_ok": true
}
```
