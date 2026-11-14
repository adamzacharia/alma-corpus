# Very Compact Millimeter Sizes for Composite Star-forming/AGN Submillimeter Galaxies

`2017ApJ...849L..36I` | The Astrophysical Journal Letters 2017 | first author: Ikarashi, Soh | arXiv: 1710.09021 | DOI: 10.3847/2041-8213/aa9572

Card schema 1.0 | model claude-sonnet-5-5 | depth full | type observational_alma_primary

## Science

- Fields: high_z_galaxies, agn_and_quasars
- Question: How do millimeter-wave sizes of ALMA-identified SMGs relate to their flux (Eddington-limited star formation) and to mid-IR AGN fraction?  
  > "Firstly, we study the empirical relation between the ALMA continuum flux densities and the millimeter-wave sizes of SMGs." (Introduction)
- Target **ASXDF SMGs (69 AzTEC/ASTE-selected SMGs in Subaru/XMM-Newton Deep Field)**: coordinates Table gives individual R.A./Dec. (e.g. ASXDF1100.002.1 at 2:17:30.63, -4:59:36.8)  
  > "our ALMA 1100-$\mu$m continuum imaging survey of 144 bright AzTEC/ASTE sources with $F_{\rm 1100 \mu m,\,AzTEC}\geq 2.4$ mJy in the Subaru/*XMM-Newton* Deep Field" (2 ALMA Observations and samples); z/distance photometric/spectroscopic z=0.7-6.8 for 51 SMGs  
  > "our ALMA 1100-$\mu$m continuum imaging survey of 144 bright AzTEC/ASTE sources with $F_{\rm 1100 \mu m,\,AzTEC}\geq 2.4$ mJy in the Subaru/*XMM-Newton* Deep Field" (2 ALMA Observations and samples); distance from Le Phare SED fitting photo-z (S. Ikarashi et al. 2017 in prep.); literature spec-z  
  > "our ALMA 1100-$\mu$m continuum imaging survey of 144 bright AzTEC/ASTE sources with $F_{\rm 1100 \mu m,\,AzTEC}\geq 2.4$ mJy in the Subaru/*XMM-Newton* Deep Field" (2 ALMA Observations and samples)

## Data provenance

- ALMA projects: 2015.1.00442.S
- bands: _not stated_
- frequencies and spectral setup: 1100 µm continuum  
  > "our ALMA 1100-$\mu$m continuum imaging survey" (2 ALMA Observations and samples)
- continuum bandwidth: _not stated_
- arrays: 12-m antennas (37-38 in Cycle 2)  
  > "with 37–38 working 12-m antennas covering up to a $uv$ distance of $\sim 1500$ k$\lambda$" (2 ALMA Observations and samples)
- configurations: Cycle 2: C34-5 and C34-7; Cycle 3: C40-4  
  > "In Cycle 3, the observations were executed in array configuration C40-4, covering up to a $uv$ distance of $\sim 1000$ k$\lambda$." (2 ALMA Observations and samples)
- baselines: _not stated_
- angular resolution: ~0.30" x 0.23" (PA ~56°)  
  > "The typical synthesized beam size for our ALMA continuum images is $\sim 0.''30 \times 0.''23$ ($\rm PA \sim 56^{\circ}$), after combining the Cycle 2 and 3 data." (2 ALMA Observations and samples)
- max recoverable scale: _not stated_
- sensitivity: average rms 120 µJy/beam  
  > "The average r.m.s. noise level is 120 $\mu$Jy beam$^{-1}$." (2 ALMA Observations and samples)
- time on source: 0.6 min per source in each cycle  
  > "On-source integration times per source in each cycle were 0.6 min." (2 ALMA Observations and samples)
- observing dates: _not stated_
- pi or archival as stated: _not stated_
- Other facility **Spitzer (IRAC, MIPS 24 µm)**: mid-IR photometry for AGN diagnostic  
  > "which are detected in all IRAC and MIPS 24 $\mu$m images" (5 Relation between millimeter sizes and AGN)
- Other facility **Subaru/UKIRT optical-NIR**: B,V,Rc,i',z',J,H,Ks photometry for photo-z  
  > "using the $B$, $V$, $Rc$, $i'$, $z'$, $J$, $H$, $Ks$, 3.6 and 4.5 $\mu$m data" (2 ALMA Observations and samples)
- External data: Dust temperature distribution for lensed 1.3mm-selected galaxies, used to convert flux to SFR  
  > "given a dust temperature ($T_d$) distribution for lensed 1.3mm-selected galaxies (cite: wei13)" (4 Relation between millimeter sizes and fluxes) [from (cite: wei13)]
- External data: SED library with Td information  
  > "an SED library with $T_d$ information compiled in (cite: swi14)" (4 Relation between millimeter sizes and fluxes) [from (cite: swi14)]
- External data: Median gas velocity dispersion 510 km/s from CO of SCUBA SMGs  
  > "a median gas velocity dispersion of 510 km s$^{-1}$ from CO line observations of SCUBA SMGs (cite: bot13)" (4 Relation between millimeter sizes and fluxes) [from (cite: bot13)]
- External data: Public mid-IR SED templates by AGN fraction  
  > "public empirical mid-IR SED templates for high-$z$ star-forming galaxies, composite galaxies, and AGN dominant galaxies (cite: kir15)" (5.1 Mid-IR AGN diagnostic) [from (cite: kir15)]
- External data: 13 fainter SMGs at z>~3 sizes  
  > "we plot 13 ALMA-identified, fainter SMGs at $z\gtrsim 3$ from (cite: ika15)" (4 Relation between millimeter sizes and fluxes) [from (cite: ika15)]

## Processing

### Calibration

- pipeline or manual: _not stated_
- casa version: _not stated_
- pipeline version: _not stated_
- archive products used as is: _not stated_
- flux calibrator: _not stated_
- flux scale uncertainty: Cycle-3 fluxes ~20% smaller; primary flux calibration corrected  
  > "the fluxes in the Cycle-3 data are systematically $\sim$20% smaller. Therefore, we corrected the primary flux calibration for this effect." (footnote 1)
- self calibration: _not stated_

### Imaging

- task: _not stated_
- deconvolver: _not stated_
- weighting robust: Briggs, robust = 0.3  
  > "The images were generated with Briggs weighting, using a robust parameter of 0.3." (2 ALMA Observations and samples)
- uv taper: tapered images with ~0.6" beam for flux re-measurement  
  > "ALMA fluxes were re-measured in tapered ALMA images with a synthesized beam of $\sim0{''}.6$" (2 ALMA Observations and samples)
- cell size: _not stated_
- image size: _not stated_
- masking: _not stated_
- multiscale scales: _not stated_
- continuum subtraction: _not stated_
- line free channels: _not stated_
- primary beam correction: _not stated_
- array combination: _not stated_
- smoothing: _not stated_
- final beam: ~0.30" x 0.23"  
  > "The typical synthesized beam size for our ALMA continuum images is $\sim 0.''30 \times 0.''23$" (2 ALMA Observations and samples)
- final rms: 120 µJy/beam  
  > "The average r.m.s. noise level is 120 $\mu$Jy beam$^{-1}$." (2 ALMA Observations and samples)

### Inherited from earlier work

- Size measurement method (uv-amp Gaussian fitting)  
  > "in the same manner as (cite: ika15)" (3 ALMA millimeter-wave source size measurements) [from (cite: ika15)]
- Mock source injection simulation for size systematics  
  > "we injected mock sources into ALMA noise visibility images, generated from the actual ALMA data as in (cite: ika15)" (3 ALMA millimeter-wave source size measurements) [from (cite: ika15)]
- Eddington-limit SFR_max formula and kappa_100=1  
  > "$\kappa_{\rm 100}=1$, as in (cite: you08)" (4 Relation between millimeter sizes and fluxes) [from (cite: you08)]
- ALMA survey data details and photo-z  
  > "B. Hatsukade et al. 2017, in preparation" (2 ALMA Observations and samples) [from Hatsukade et al. 2017 in prep.; Ikarashi et al. 2017 in prep.]

### Not stated but needed to reproduce (our reading)

- Calibration/pipeline details and CASA version
- Exact uv-amp binning and Gaussian fit procedure/errors
- Simulation correction factors for sizes
- SFR-to-flux conversion details and bootstrapping setup
- Stellar masses and mid-IR flux measurements/deblending
- Toy SF/AGN mixing SEDs used
- Photo-z catalogue and SED fitting from in-prep paper

## Analysis recipe

1. **Measure fluxes**: Re-measure fluxes in tapered ~0.6" images  
  > "ALMA fluxes were re-measured in tapered ALMA images with a synthesized beam of $\sim0{''}.6$" (2 ALMA Observations and samples)
   - software: CASA IMFIT
   - fitting: _not stated_
   - validation: _not stated_
2. **Measure millimeter sizes**: Gaussian model fit to uv-amplitude plots using uv<=500 kλ; other >=5σ sources removed  
  > "We measured sizes by fitting a Gaussian model to the observed data in the $uv$-amp plots." (3 ALMA millimeter-wave source size measurements)
   - software: IMFIT
   - parameter: uv cutoff 500 kλ (~0.2")  
  > "we used only data at $\leq 500$ k$\lambda$, which corresponds to a scale of $\sim0.''2$" (3 ALMA millimeter-wave source size measurements)
   - fitting: Gaussian model  
  > "We measured sizes by fitting a Gaussian model to the observed data in the $uv$-amp plots." (ALMA millimeter-wave source size measurements)
   - validation: Mock sources injected into noise visibilities; sizes corrected  
  > "We corrected our raw measured sizes based on the results of the simulations for the data used in this paper." (3 ALMA millimeter-wave source size measurements)
3. **Compare size-flux/SFR with Eddington limit**: Compute SFR_max from Younger et al. formula, convert flux to SFR via bootstrapped Td/SED, plot size vs SFR  
  > "The conversion factors from ALMA fluxes to SFRs were derived by bootstrapping given a dust temperature ($T_d$) distribution" (4 Relation between millimeter sizes and fluxes)
   - parameter: D = 4×Rc,e with 0.94 correction; z=2 fixed for left panel  
  > "We also adopt 2$\times$ FWHM or 4$\times R_{\rm c,e}$, which is expected to include 94% of the total light, as $D_{\rm kpc}$." (4 Relation between millimeter sizes and fluxes)
   - assumption: Chabrier IMF, kappa_100=1, sigma=510 km/s, negligible AGN contribution to submm flux  
  > "We assume that the AGN contribution to the submillimeter flux is negligible (cite: ros12)." (4 Relation between millimeter sizes and fluxes)
   - fitting: _not stated_
   - validation: _not stated_
4. **Classify mid-IR AGN fraction**: 4.5/8/24 µm colour cuts: star-forming, composite, AGN, no class, compared with Kirkpatrick templates and toy SF+AGN SED mixes  
  > "We divided the 25 SMGs into four sub-groups based on their 4.5/8/24-$\mu$m colors: star-forming, composite, AGN-dominant and ‘no class’." (5.1 Mid-IR AGN diagnostic)
   - parameter: F8/F4.5 = 1.15 and 1.50 thresholds; F24/F8 = 5  
  > "$F_{\rm 8 \mu m}/F_{\rm 4.5 \mu m}\geq1.15$ $\bigwedge$ $F_{\rm 24 \mu m}/F_{\rm 8 \mu m}\geq 5$ (composite)" (5.1 Mid-IR AGN diagnostic)
   - fitting: _not stated_
   - validation: Compared with Donley and Stern AGN criteria and model tracks  
  > "as this ensures that all galaxies that satisfy neither an AGN criteria by (cite: don12) nor another criteria by (cite: ste05) also lie on the star-forming region of the colour-colour diagram." (Mid-IR AGN diagnostic)
5. **Compare sizes across classes**: Median Rc,e per class; KS test; check stellar-mass dependence  
  > "with a significance level of $>99$%, according to the Kolmogorov-Smirnov test" (5.2 Results)
   - fitting: _not stated_
   - validation: Checked at fixed stellar mass  
  > "Composite SMGs are the most compact of the three types, even at fixed stellar mass." (5.2 Results)

## Software

- **CASA (IMFIT)** : flux and source property measurement in tapered images  
  > "using the IMFIT task in CASA" (2 ALMA Observations and samples)
- **Le Phare** : photometric redshifts via SED fitting  
  > "estimated by *Le Phare* (cite: ilb06) in spectral energy distribution (SED) model fitting" (2 ALMA Observations and samples)

## Numeric results

| quantity | value | uncertainty | units | step | quote |
|---|---|---|---|---|---|
| Median Rc,e star-forming mid-IR class | 1.6 | +0.34/-0.21 | kpc | 5 | respective median $R_{\rm c,e} = 1.6^{+0.34}_{-0.21}$ and 1.5$^{+0.93}_{-0.24}$ kpc |
| Median Rc,e AGN-dominant class | 1.5 | +0.93/-0.24 | kpc | 5 | respective median $R_{\rm c,e} = 1.6^{+0.34}_{-0.21}$ and 1.5$^{+0.93}_{-0.24}$ kpc |
| Median Rc,e composite class | 1.0 | +0.20/-0.20 | kpc | 5 | median $R_{\rm c,e}=1.0^{+0.20}_{-0.20}$ kpc |
| Median FWHM size of ASXDF SMGs with F1100 >~2.5 mJy | 0.31 | +0.03/-0.03 | arcsec | 2 | our ASXDF SMGs have a median size of$0.''31^{+0.''03}_{-0.''03}$ |
| Range of FWHM sizes | 0.08-0.68 | not stated | arcsec | 2 | we obtained ALMA millimeter-wave sizes of 0$''.08$–0$''.68$ (FWHM) for the 69 ASXDF SMGs |

## Qualitative findings

- SMGs avoid the region near the Eddington limit in size-flux/SFR plane  
  > "the SMGs avoid the SFR region around the Eddington limit" (4 Relation between millimeter sizes and fluxes)

## Claim tuples

- H: Minimum SMG sizes are set by Eddington-limited star formation | E: Plot 69 SMGs in size-flux and size-SFR planes against SFR_max | R: SMGs absent from bottom-right region | F: Minimum sizes consistent with Eddington limit | **supported**
- H: Millimeter size depends on mid-IR AGN fraction | E: Classify 25 SMGs at z=1-3 by mid-IR colours and compare median sizes with KS test | R: Composite SMGs median 1.0 kpc vs 1.6 and 1.5 kpc | F: Composite SF/AGN SMGs are more compact | **supported**

## Reasoning

- Why this data: _not stated_
- Why this method: _not stated_
- How they decided it was enough: _not stated_
- Limitation (authors): X-ray maps too shallow to detect any SMG  
  > "probably because these maps are too shallow" (5.2 Results)
- Caveat (inferred, ours): Small sample (25) split into three classes
- Caveat (inferred, ours): Mid-IR colour classes rely on toy models and photo-z
- Caveat (inferred, ours): Interpretation of AGN-dominant extended sizes is speculative
- Caveat (inferred, ours): Uncertain Td/SED conversion to SFR

## Reproducibility

- Data public (paper): _not stated_
- Products in archive: _not stated_
- Missing: Calibrated visibilities and flux correction details
- Missing: Mid-IR photometry and photo-z catalogues
- Missing: Details of mock-source correction
- Data volume (inferred): ~50-100 GB for 144-field survey visibilities
- Score (inferred): 3/5, Methods outlined but heavily deferred to prior and in-preparation papers; catalogue values tabulated.
- Rediscovery candidate: no, Key inputs (photo-z, mid-IR photometry, size corrections) are not fully specified.

## Links

- Method: Ikarashi et al. 2015 (cite: ika15) (size measurement method and simulations)
- Method: Younger et al. 2008 (cite: you08) (Eddington-limit SFR formula)
- Method: Kirkpatrick et al. 2015 (cite: kir15) (mid-IR SED templates by AGN fraction)
- Companion: Hatsukade et al. 2017, in preparation (ALMA SXDF survey)
- Companion: Ikarashi et al. 2017, in preparation (photometric redshifts)
- Related: ASXDF
- Related: AzTEC/ASTE SXDF survey

## Checks

```json
{
 "quotes": 52,
 "quotes_ok": 52,
 "quote_pass_rate": 1.0,
 "quotes_too_long": 0,
 "unsupported_facts": 0,
 "project_codes": 1,
 "codes_not_in_text": [],
 "codes_not_in_obscore": [],
 "obscore_codes_not_in_card": [
  "2013.1.00781.S"
 ],
 "codes_printed_but_missing": [],
 "numeric_results": 5,
 "numeric_problems": 0,
 "fill": {
  "facts": 77,
  "stated": 43,
  "rate": 0.558
 },
 "evidence_ok": true
}
```
