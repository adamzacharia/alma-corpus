# Active Galactic Nuclei in Dusty Starbursts at z = 2: Feedback Still to Kick in

`2019ApJ...877L..38R` | The Astrophysical Journal Letters 2019 | first author: Rodighiero, G. | arXiv: 1905.06955 | DOI: 10.3847/2041-8213/ab222e

Card schema 1.0 | model claude-sonnet-5-5 | depth light | type multi_facility_alma_minor

## Science

- Fields: high_z_galaxies, agn_and_quasars
- Question: Do AGN in Herschel-selected dusty starbursts at 1.5<z<2.5 show signs of feedback, e.g. reduced gas fractions or different morphologies, compared with purely star-forming starbursts?  
  > "We study their morphologies, AGN contribution and molecular gas contents (for a sub-sample with an ALMA continuum observation) to infer potential observational evidences of feedback induced by AGN." (Introduction)
- Target **152 Herschel-selected starbursts in COSMOS at 1.5<z<2.5 (33 with ALMA continuum detections)**: coordinates per-source RA/Dec listed in the ALMA source table (COSMOS field)  
  > "Out of 1790 *Herschel* detected sources at $1.5<z<2.5$, we identified a sample of 164 SBs" (Dusty starbursts at 1.5<z<2.5: sample selection); z/distance 1.5<z<2.5 (spectroscopic or photometric)  
  > "Out of 1790 *Herschel* detected sources at $1.5<z<2.5$, we identified a sample of 164 SBs" (Dusty starbursts at 1.5<z<2.5: sample selection); distance from COSMOS2015 catalog  
  > "Out of 1790 *Herschel* detected sources at $1.5<z<2.5$, we identified a sample of 164 SBs" (Dusty starbursts at 1.5<z<2.5: sample selection)

## Data provenance

- ALMA projects: _none stated_
- bands: mostly Band 7 (870 um), a few also Band 3 or 2  
  > "mostly in band 7 at 870$\mu$m (with 4 un-detected sources that we do not include in this work), with few of them detected also in band 3 or 2" (4.1 ALMA continuum counterparts)
- frequencies and spectral setup: _not stated_
- continuum bandwidth: _not stated_
- arrays: _not stated_
- configurations: _not stated_
- baselines: _not stated_
- angular resolution: _not stated_
- max recoverable scale: _not stated_
- sensitivity: _not stated_
- time on source: _not stated_
- observing dates: _not stated_
- pi or archival as stated: public archive data, 2.5" search radius  
  > "We searched for possible ALMA millimetric counterparts of the SBs in the public archive, adopting a search radius of 2.5$"$." (4.1 ALMA continuum counterparts)
- Other facility **Herschel (PACS/SPIRE)**: far-IR photometry used to select starbursts  
  > "PACS and SPIRE-*Herschel* data are originally from the PEP (cite: 2011A&A...532A..90L) and HerMES (cite: 2012MNRAS.424.1614O) surveys" (2 sample selection)
- Other facility **HST ACS**: i-band images for visual morphology  
  > "We performed a visual inspection on the COSMOS/HST ACS $i$-band images of the 140 (out of 152) SBs" (3 UV-restframe HST morphological analysis)
- Other facility **Chandra (COSMOS)**: X-ray stacking for hardness ratios  
  > "We used the CSTACK tool[^3] (v3.1, T. Miyaji) and derive the average Hardness Ratio" (3 UV-restframe HST morphological analysis)
- External data: COSMOS2015 photometry, redshifts, stellar masses and Herschel catalog  
  > "Sources identification, multiwavelength photometry, $M_*$ and redshifts are from the COSMOS2015 sample." (2 sample selection) [from (cite: 2016ApJS..224...24L)]
- External data: Comparison sample of galaxies with CO measurements  
  > "we use the reference sample compiled by (cite: 2014ApJ...793...19S) and (cite: 2018arXiv180703378P), including ’typical’ star-forming galaxies at $z\leq3$ with measurements of their CO luminosity." (4.1 Comparison sample) [from (cite: 2014ApJ...793...19S); (cite: 2018arXiv180703378P)]

## Processing

### Calibration

- pipeline or manual: measurement sets calibrated by running the data reduction scripts in CASA  
  > "The measurement sets were calibrated running the data reduction scripts with the Common Astronomy Software Applications (CASA)." (4.1 ALMA continuum counterparts)
- casa version: _not stated_
- pipeline version: _not stated_
- archive products used as is: _not stated_
- flux calibrator: _not stated_
- flux scale uncertainty: _not stated_
- self calibration: _not stated_

### Imaging

- task: _not stated_
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

- Starburst selection at least a factor 4 above the main sequence  
  > "Starbursts (SBs) are selected to have a SFR well elevated above the MS at $z=2$, at least a factor 4, as in (cite: 2011ApJ...739L..40R)." (2 sample selection) [from (cite: 2011ApJ...739L..40R)]
- Dust mass derivation procedure  
  > "Dust masses ($M_{dust}$) have been derived following the procedure described in (cite: 2012ApJ...760....6M; 2017A&A...603A..93M)" (4.2 Dust and molecular gas masses) [from (cite: 2012ApJ...760....6M; 2017A&A...603A..93M)]

### Not stated but needed to reproduce (our reading)

- ALMA project codes and which datasets were used for each source
- CASA version and the specific reduction scripts
- Imaging parameters (weighting, cell, size, cleaning) for continuum images
- Region/fit settings for the 2D Gaussian flux measurement
- Details of the SED fitting setup (priors, grids) and of the dust model fit
- Chandra stacking settings
- Criteria for the visual morphological classification

## Analysis recipe

1. **select starburst sample**: Herschel-detected COSMOS2015 sources at 1.5<z<2.5 with SFR at least 4x above the main sequence and M*>1e10 Msun  
  > "We limit our analysis to $M_*>10^{10}M_\odot$ (cite: 2016ApJS..224...24L) reducing the SB sample to 152 objects." (2.1 SED fitting)
   - fitting: _not stated_
   - validation: _not stated_
2. **SED fitting and AGN classification**: MAGPHYS and SED3FIT fits; AGN preferred if Fisher test at >=99% confidence  
  > "The fit obtained with the AGN is preferred if the reduced $\chi^2$ value of the best fit (at $\ge$99% confidence level, on the basis of a Fisher test)" (2.2 AGN classification)
   - software: MAGPHYS, SED3FIT
   - assumption: SFR from total IR luminosity with Kennicutt (1998) conversion; Chabrier IMF  
  > "assuming a (cite: 1998ARA&A..36..189K) conversion." (2.1 SED fitting)
   - fitting: _not stated_
   - validation: compared with the IRAC colour-colour diagnostic of Donley et al. (2012), X-ray AGN and mass-weighted ages  
  > "finding that $\sim80\%$ of the SBs-AGN fall into the AGN region, while just one of the SBs-SFR are mis-classified as AGN" (2.2 AGN classification)
3. **measure ALMA continuum fluxes**: 2D Gaussian fit in CASA  
  > "Fluxes and associated errors were evaluated with CASA, by fitting the emissions with a bi-dimensional Gaussian" (4.1 ALMA continuum counterparts)
   - software: CASA
   - parameter: detections >3 sigma  
  > "The final sample includes 33 sources with a clear detection over $3\sigma$" (4.1 ALMA continuum counterparts)
   - fitting: _not stated_
   - validation: _not stated_
4. **derive dust and gas masses and gas fractions**: fit IRAC-ALMA SED with Draine & Li (2007) models; Mgas = Mdust/GDR  
  > "$M_{gas} = M_{dust}/GDR(Z)$" (4.2 Dust and molecular gas masses)
   - assumption: GDR ~30 (alpha_CO=0.8); also GDR ~95 for solar metallicity  
  > "we adopt $GDR \approx 30$, that based on (cite: 2012ApJ...760....6M) corresponds to a CO-to-$M_{gas}$ $\alpha_{co}$ conversion factor of 0.8" (4.2 Dust and molecular gas masses)
   - fitting: _not stated_
   - validation: consistent within 0.15 dex with Mgas from R-J monochromatic fluxes (Scoville et al. 2017 recipe)  
  > "consistent (within 0.15dex) with the average $M_{gas}$ estimates derived based on the monochromatic flux densities in the R-J tail of the SED" (4.2 Dust and molecular gas masses)

## Software

- **CASA** : calibration and 2D Gaussian flux fitting  
  > "Fluxes and associated errors were evaluated with CASA" (4.1 ALMA continuum counterparts)
- **MAGPHYS** : SED fitting  
  > "We used both the *MAGPHYS* (cite: 2008MNRAS.388.1595D), and the *SED3FIT*" (2.1 SED fitting)
- **SED3FIT** : SED fitting including AGN torus component  
  > "the latter accounting for an additional AGN component (dusty torus)." (2.1 SED fitting)
- **CSTACK** v3.1: X-ray stacking for hardness ratios  
  > "We used the CSTACK tool[^3] (v3.1, T. Miyaji)" (3 UV-restframe HST morphological analysis)

## Numeric results

| quantity | value | uncertainty | units | step | quote |
|---|---|---|---|---|---|
| SBs-AGN fraction | 35 of 152 (~23%) | not stated | dimensionless | 2 | 35 out of 152 starbursts (about 23%) show a significant AGN component. |
| mean gas fraction SBs-AGN | 43 | 4 | % | 4 | $f_{gas}=43\,\pm\,4\%$ and $f_{gas}=42\,\pm\,2\%$ |
| mean gas fraction SBs-SFR | 42 | 2 | % | 4 | $f_{gas}=43\,\pm\,4\%$ and $f_{gas}=42\,\pm\,2\%$ |
| disturbed fraction among HST-detected SBs-SFR | 82 | 11 | % | 0 | SBs-SFR are disturbed systems (56 out of 68, i.e. $\sim$82$\pm11$% of the HST detected sample) |
| compact fraction among HST-detected SBs-AGN | 55 | 15 | % | 0 | (13 out of 24 detection, $\sim$55$\pm15$%) |
| stacked hardness ratio of compact SBs-AGN | -0.12 | 0.11 | dimensionless | 0 | have compatible $HR=-0.12\pm0.11$, $0.02\pm0.31$, $-0.04\pm0.13$, respectively |

## Qualitative findings

- SBs-AGN have no significantly lower gas fraction than SBs-SFR; SBs lie on a continuous sequence of increasing SFE between normal galaxies and ULIRG/SBs  
  > "We then observe that SBs lie on a contiguous sequence of increasing SFE" (4.3 Gas masses and gas fractions)

## Claim tuples

- H: AGN feedback has already reduced gas fractions in AGN-hosting starbursts | E: Compare gas fractions of 12 SBs-AGN and 21 SBs-SFR from ALMA-based dust masses | R: f_gas = 43±4% vs 42±2% | F: Feedback has not yet depleted gas in SBs-AGN | **supported**
- H: SBs-AGN and SBs-SFR have different UV morphologies | E: Visual inspection of HST i-band images | R: SBs-SFR mostly disturbed; about half of SBs-AGN compact | F: SBs-AGN are likely more compact, perhaps final-merger or primordial galaxies | **partially**

## Reasoning

- Why this data: _not stated_
- Why this method: _not stated_
- How they decided it was enough: _not stated_
- Limitation (authors): Morphology limited by shallow HST imaging and dust extinction  
  > "We caution that this morphological analysis is limited by the shallowness of the COSMOS/HST imaging" (3 UV-restframe HST morphological analysis)
- Caveat (inferred, ours): Gas masses rest on an assumed GDR and the ALMA fluxes are heterogeneous archival data
- Caveat (inferred, ours): Visual morphological classification is subjective
- Caveat (inferred, ours): AGN sample is not complete
- Caveat (inferred, ours): Small ALMA subsample, with no CO-based gas measurements

## Reproducibility

- Data public (paper): public archive  
  > "We searched for possible ALMA millimetric counterparts of the SBs in the public archive" (4.1 ALMA continuum counterparts)
- Products in archive: _not stated_
- Missing: ALMA project codes and per-source dataset mapping
- Missing: imaging and flux-extraction settings
- Missing: SED fitting configuration details
- Data volume (inferred): tens of GB
- Score (inferred): 3/5, Public data and source table exist, but ALMA projects and processing details are not given.
- Rediscovery candidate: no, The ALMA processing details are missing, and the main results depend on SED fitting and visual classification.

## Links

- Method: (cite: 2012ApJ...760....6M) (dust mass and GDR procedure)
- Method: (cite: 2013A&A...551A.100B) (SED3FIT code)
- Companion: (cite: 2015ApJ...800L..10R) (earlier X-ray stacking and hardness ratio analysis)
- Related: COSMOS
- Related: COSMOS2015
- Related: PEP
- Related: HerMES

## Checks

```json
{
 "quotes": 39,
 "quotes_ok": 39,
 "quote_pass_rate": 1.0,
 "quotes_too_long": 0,
 "unsupported_facts": 0,
 "project_codes": 0,
 "codes_not_in_text": [],
 "codes_not_in_obscore": [],
 "obscore_codes_not_in_card": [
  "2013.1.00034.S",
  "2015.1.00137.S",
  "2015.1.00207.S",
  "2015.1.00568.S",
  "2016.1.00171.S",
  "2016.1.00478.S",
  "2016.1.00646.S",
  "2016.1.00804.S"
 ],
 "codes_printed_but_missing": [],
 "numeric_results": 6,
 "numeric_problems": 0,
 "fill": {
  "facts": 71,
  "stated": 30,
  "rate": 0.423
 },
 "evidence_ok": true
}
```
