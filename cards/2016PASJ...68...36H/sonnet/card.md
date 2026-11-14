# SXDF-ALMA 2-arcmin<SUP>2</SUP> deep survey: 1.1-mm number counts

`2016PASJ...68...36H` | Publications of the Astronomical Society of Japan 2016 | first author: Hatsukade, Bunyo | arXiv: 1602.08167 | DOI: 10.1093/pasj/psw026

Card schema 1.0 | model claude-sonnet-5-5 | depth full | type observational_alma_primary

## Science

- Fields: high_z_galaxies
- Question: What are the 1.1 mm number counts in a contiguous ALMA field, and are counts from serendipitously detected sources biased by clustering around targets?  
  > "previous studies are based on the ensemble of serendipitously-detected sources in fields originally targeting different sources and could be biased due to the clustering of sources around the targets." (abstract)
- Target **SXDF-ALMA field (Subaru/XMM-Newton Deep Survey Field, part including CANDELS)**: coordinates _not stated_; z/distance mean z=2.5 assumed for SMGs  
  > "we present 1.1 mm number counts in a contiguous area revealed by the ALMA observations of a part of the Subaru/*XMM-Newton* Deep Survey Field (SXDF)" (Introduction); distance from literature SMG redshifts (Chapman05; Yun12)  
  > "we present 1.1 mm number counts in a contiguous area revealed by the ALMA observations of a part of the Subaru/*XMM-Newton* Deep Survey Field (SXDF)" (Introduction)

## Data provenance

- ALMA projects: 2012.1.00756.S
- bands: _not stated_
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
- pi or archival as stated: _not stated_
- Other facility **AzTEC (1.1 mm)**: Source in field used to select the ALMA field; comparison density and bright-end counts  
  > "the field is selected to include an AzTEC source" (Source and Spurious Detection)
- External data: Previous 1-mm number counts (ALMA and single-dish) used for comparison and for the joint fit  
  > "we use the number counts obtained in 1-mm observations (1.1–1.3 mm) with ALMA and single-dish telescopes plotted in figure" (Number Counts) [from hats13; ono14; carn15; fuji16; oteo15; lind11; scot12 (cite)]
- External data: EBL at 1.1 mm from COBE  
  > "The EBL at 1.1 mm based on the measurements by the *Cosmic Background Explorer* satellite is $\sim$18 Jy deg$^{-2}$" (Discussion and Conclusions) [from (cite: puge96); (cite: fixs98)]
- Simulation/model as data: Model counts compared: Shimizu12, Bethermin12, Cai13, da Cunha13  
  > "recent model predictions with different approaches by (cite: shim12), (cite: beth12), (cite: cai13), and (cite: dacu13) are also compared." (Discussion and Conclusions)

## Processing

### Calibration

- pipeline or manual: _not stated_
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
- primary beam correction: Source detection on image before primary beam correction; completeness on corrected map  
  > "Source detection was conducted on the image before correcting for the primary beam attenuation." (Source and Spurious Detection)
- array combination: _not stated_
- smoothing: _not stated_
- final beam: _not stated_
- final rms: _not stated_

### Inherited from earlier work

- Survey design, source catalog and integrated flux densities  
  > "The survey design and source catalog is described in Kohno et al. (in prep.)" (Introduction) [from Kohno et al. (in prep.)]

### Not stated but needed to reproduce (our reading)

- The data section is empty: bands, array configuration, beam, rms, calibration and imaging settings are not given
- Image pixel size, weighting, and CASA version
- Aegean detection parameters
- Exact functional fits for completeness, boosting and false-detection fraction
- Flux scaling used to bring other wavelengths to 1.1 mm
- Source catalog (in prep.)

## Analysis recipe

1. **Detect sources**: Aegean source finder on image before primary beam correction; peak SN>=4 sigma  
  > "We find 25 (6) sources with a peak SN of $\ge$$4\sigma$ ($\ge$$5\sigma$)." (Source and Spurious Detection)
   - software: aegean, aips/sad
   - fitting: _not stated_
   - validation: Peak vs integrated flux with AIPS SAD: ratio 1.1±0.3  
  > "$S_{\rm integ}/S_{\rm peak} = 1.1 \pm 0.3$" (Source and Spurious Detection)
2. **Estimate spurious fraction**: Count negative peaks vs SN and take ratio to positive peaks  
  > "we count the number of negative peaks as a function of SN threshold" (Source and Spurious Detection)
   - fitting: _not stated_
   - validation: _not stated_
3. **Completeness and flux boosting**: Inject artificial sources (scaled synthesized beam) at random positions, 1000 times per flux bin; recovered if extracted within 1.0'' at >=4 sigma; input/output flux ratio gives boosting  
  > "This procedure is repeated 1000 times for each flux bin." (Completeness)
   - fitting: _not stated_
   - validation: Completeness checked without position constraint and against SN threshold  
  > "We checked that the completeness does not change significantly if we remove the constraint on the input source positions." (Completeness)
4. **Derive number counts with errors**: Correct for spurious contamination, completeness and boosting; errors combine Poisson, correction uncertainties and field-to-field variation in quadrature; two brightest sources excluded  
  > "Contributions from the uncertainties are calculated separately and combined by taking the square root of the sum of the squares in each flux bin." (Number Counts)
   - software: Trenti & Stiavelli cosmic variance tool
   - parameter: Survey area 2'x1', mean z=2.5, Δz=3, halo occupation fraction unity  
  > "We use the survey area of $2' \times 1'$, the mean redshift of $\bar{z}=2.5$, the redshift range of $\Delta z = 3$" (Number Counts)
   - assumption: Omega_M=0.26, Omega_Lambda=0.74, h=70, sigma_8=0.9  
  > "$\Omega_{\rm{M}} = 0.26$, $\Omega_{\Lambda} = 0.74$, $h = 70$ km s$^{-1}$ Mpc$^{-1}$" (Number Counts)
   - fitting: _not stated_
   - validation: _not stated_
5. **Fit functions and EBL fraction**: Fit Schechter and double power law to differential counts from this and previous 1-mm studies; integrate for resolved EBL  
  > "The differential number counts obtained in this study and previous studies are fitted to a Schechter function" (Number Counts)
   - assumption: Excluded 870 um counts and S<0.1 mJy lensed counts  
  > "but do not use the number counts at 870 $\mu$m to avoid the uncertainties from flux scaling." (Number Counts)
   - fitting: _not stated_
   - validation: Slopes compared with Fujimoto16  
  > "The power law slopes are consistent with those of (cite: fuji16)." (Number Counts)

## Software

- **aegean** : Source finding  
  > "We adopt a source-finding algorithm aegean (cite: hanc12)" (Source and Spurious Detection)
- **AIPS SAD** : Integrated flux densities  
  > "measured with the aips/sad task" (Source and Spurious Detection)

## Numeric results

| quantity | value | uncertainty | units | step | quote |
|---|---|---|---|---|---|
| Sources >=4 sigma | 25 (23 used after excluding two brightest) | not stated | sources | 1 | We find 25 (6) sources with a peak SN of $\ge$$4\sigma$ ($\ge$$5\sigma$). |
| Cumulative counts N(>0.17 mJy) | 38.2 | +23.5/-9.4 | 10^3 deg^-2 | 4 | / 0.17    / 23      / $38.2^{+23.5}_{-9.4}$ / |
| Differential counts at 0.25 mJy | 143.2 | +104.2/-41.0 | 10^3 mJy^-1 deg^-2 | 4 | / 0.25    / 17      / $143.2^{+104.2}_{-41.0}$ |
| Schechter fit S' | 3.1 | 0.5 | mJy | 5 | / Schechter / $15.0\pm 5.1$ / $3.1 \pm 0.5$ / $-1.9 \pm 0.2$ / $-$ / |
| Resolved EBL fraction at S>0.2 mJy | ~40 | not stated | percent | 5 | $\sim$40% of the extragalactic background light at 1.1 mm is resolved at $S_{\rm 1.1mm} > 0.2$ mJy. |

## Qualitative findings

- Counts agree with previous serendipitous-source counts and with the model predictions  
  > "We found that the model predictions agree with our number counts within the uncertainties from both the models and the observed counts." (Discussion and Conclusions)

## Claim tuples

- H: Counts from serendipitous sources are biased by clustering around targets | E: Number counts from 23 sources in a contiguous 2.0 arcmin^2 field | R: Consistent with previous results within errors | F: Serendipitous counts not significantly biased, though field-to-field variation is possible | **supported**
- H: Sub-mJy sources resolve a large part of the 1.1 mm EBL | E: Integrate best-fit functions | R: ~40% resolved at S>0.2 mJy | F: Consistent with previous ALMA studies | **supported**

## Reasoning

- Why this data: _not stated_
- Why this method: _not stated_
- Alternative: Excluded the two brightest ALMA sources associated with the AzTEC source to avoid the overdensity effect  
  > "we exclude the two ALMA sources when deriving number counts to avoid the effect of the possible overdensity." (Source and Spurious Detection)
- How they decided it was enough: _not stated_
- Limitation (authors): Small area, possible field-to-field variation  
  > "although our survey area is small and could be affected by field-to-field variation." (Discussion and Conclusions)
- Caveat (inferred, ours): Only a few sources at high flux; Poisson-dominated errors
- Caveat (inferred, ours): Observation and imaging details are missing from the text
- Caveat (inferred, ours): Field chosen to include an AzTEC source may be overdense

## Reproducibility

- Data public (paper): _not stated_
- Products in archive: _not stated_
- Missing: Observation and imaging details (data section absent)
- Missing: Source catalog (Kohno et al. in prep.)
- Missing: Fit functions for corrections
- Data volume (inferred): not stated; likely tens of GB raw
- Score (inferred): 3/5, Recipe is outlined, but the data and imaging details are absent and the catalog is deferred.
- Rediscovery candidate: no, Imaging and catalog details are missing, so the recipe is not complete.

## Links

- Method: (cite: hanc12) (Aegean source finder)
- Method: (cite: tren08) (Cosmic variance tool)
- Companion: Kohno et al. 2016 (cite: kohn16) (Survey design and catalog)
- Companion: (cite: tada15) (Source properties)
- Related: SXDF
- Related: CANDELS
- Related: AzTEC

## Checks

```json
{
 "quotes": 34,
 "quotes_ok": 34,
 "quote_pass_rate": 1.0,
 "quotes_too_long": 0,
 "unsupported_facts": 0,
 "project_codes": 1,
 "codes_not_in_text": [],
 "codes_not_in_obscore": [],
 "obscore_codes_not_in_card": [],
 "codes_printed_but_missing": [],
 "numeric_results": 5,
 "numeric_problems": 0,
 "fill": {
  "facts": 71,
  "stated": 25,
  "rate": 0.352
 },
 "evidence_ok": true
}
```
