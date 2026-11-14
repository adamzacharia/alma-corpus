# Obscured star formation in clusters at z = 1.6-2.0: massive galaxy formation and the reversal of the star formation-density relation

`2024MNRAS.529.2290S` | Monthly Notices of the Royal Astronomical Society 2024 | first author: Smail, Ian | arXiv: 2401.08761 | DOI: 10.1093/mnras/stae692

Card schema 1.0 | model claude-sonnet-5-5 | depth light | type multi_facility_alma_minor

## Science

- Fields: high_z_galaxies, star_formation
- Question: How does obscured star formation in massive clusters at z=1.6-2.0 evolve, and does the SFR-density relation reverse?  
  > "The study presented here aims to assess the evolution in the star formation rate of submillimetre-selected galaxy populations within massive clusters at $z$ $\sim$ 1.5–2.0." (1 Introduction)
- Target **XLSSC122**: coordinates 02 17 44.1 -03 46 10  
  > "| XLSSC122    | ACT-CL J0217.7$-$0345   | 02 17 44.1 | $-$03 46 10 | 1.98 |" (Table 1); z/distance z=1.98  
  > "| XLSSC122    | ACT-CL J0217.7$-$0345   | 02 17 44.1 | $-$03 46 10 | 1.98 |" (Table 1); distance from Table 1 references  
  > "| XLSSC122    | ACT-CL J0217.7$-$0345   | 02 17 44.1 | $-$03 46 10 | 1.98 |" (Table 1)
- Target **SpARCSJ0224**: coordinates 02 24 26.3 -03 23 30  
  > "| SpARCSJ0224 | SpARCS J022426$-$032330 | 02 24 26.3 | $-$03 23 30 | 1.63 |" (Table 1); z/distance z=1.63  
  > "| SpARCSJ0224 | SpARCS J022426$-$032330 | 02 24 26.3 | $-$03 23 30 | 1.63 |" (Table 1); distance from Table 1 references  
  > "| SpARCSJ0224 | SpARCS J022426$-$032330 | 02 24 26.3 | $-$03 23 30 | 1.63 |" (Table 1)
- Target **ClJ1449**: coordinates 14 49 14.0 +08 56 21  
  > "| ClJ1449     | Cl J1449+0856           | 14 49 14.0 | +08 56 21   | 1.99 |" (Table 1); z/distance z=1.99  
  > "| ClJ1449     | Cl J1449+0856           | 14 49 14.0 | +08 56 21   | 1.99 |" (Table 1); distance from Gobat13  
  > "| ClJ1449     | Cl J1449+0856           | 14 49 14.0 | +08 56 21   | 1.99 |" (Table 1)
- Target **SpARCSJ0225, JKCS041, LH146, IDCSJ1426, IDCSJ1433**: coordinates see Table 1  
  > "The sample analysed here comprises eight well-studied clusters at $z$ $\sim$ 1.6–2.0 (Table 1)" (2 Observations and Reduction); z/distance z=1.60-1.89  
  > "The sample analysed here comprises eight well-studied clusters at $z$ $\sim$ 1.6–2.0 (Table 1)" (2 Observations and Reduction); distance from Table 1 references  
  > "The sample analysed here comprises eight well-studied clusters at $z$ $\sim$ 1.6–2.0 (Table 1)" (2 Observations and Reduction)

## Data provenance

- ALMA projects: 2021.1.01257.S, 2018.1.00974.S, 2016.1.01107.S
- bands: Archival ALMA bands 3, 4, 6, 7 in four clusters  
  > "In the remaining four clusters a mix of band 3, 4, 6 and 7 observations were found." (3.1 Interferometric identifications)
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
- pi or archival as stated: Public archival ALMA data  
  > "The ALMA archive was searched to identify any public sub-/millimetre observations of the eight clusters." (3.1 Interferometric identifications)
- Line: CO 2-1 (not stated)
- Other facility **JCMT SCUBA-2**: 850 and 450 um maps of eight clusters; main dataset  
  > "The eight clusters were observed with SCUBA-2 (cite: Holland13) on the 15-m JCMT simultaneously at 850 $\mu$m and 450 $\mu$m" (2.1 Observations)
- Other facility **Spitzer IRAC/MIPS (SEIP)**: Counterpart identification and stellar masses  
  > "The SEIP data cover all eight clusters in this study (Figure 1)" (3.2 Spitzer identifications)
- Other facility **HST**: Imaging of 23 counterparts  
  > "From the 63 reliably identified counterparts, 23 had useable multi-band HST imaging, typically from WFC3." (3.3 Final combined identifications)
- Other facility **JVLA**: Radio catalogues for counterparts  
  > "suitably sensitive catalogues from the JVLA had been published covering LH146" (3.1 Interferometric identifications)
- External data: ALMA-identified AS2UDS SMG counterparts, magphys SFRs and stellar masses used for scaling relations  
  > "Using the magphys-based SED analysis of the ALMA-identified submillimetre sample in the UDS from (cite: Dudzeviciute20), correlations were derived" (3.5 Scaling relations) [from (cite: Dudzeviciute20); (cite: Stach19)]
- External data: ALMA band 7 continuum source in ClJ1449 and XLSSC122 ALMA sources  
  > "$^{13}$ A5 ALMA band 7 continuum source from (cite: Coogan18) $S_{\rm 870\mu m}$ $=$ 6.0 $\pm$ 0.2 mJy." (Table 5) [from (cite: Coogan18); (cite: vanMarrewijk23)]

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
- primary beam correction: _not stated_
- array combination: _not stated_
- smoothing: _not stated_
- final beam: _not stated_
- final rms: _not stated_

### Inherited from earlier work

- Observational strategy and methodology follow Cooke et al.  
  > "By adopting a similar observational strategy and methodology to (cite: Cooke19), the intention was to provide a homogeneous extension of that analysis" (1 Introduction) [from (cite: Cooke19)]
- Source detection approach  
  > "Sources were identified in the SCUBA-2 maps using the approach described in (cite: Simpson19)" (2.3 Source detection) [from (cite: Simpson19)]

### Not stated but needed to reproduce (our reading)

- ALMA data reduction, calibration, imaging and detection details for archival ALMA data
- Which ALMA project covers which cluster
- ALMA band 7/band 3 flux or line measurements beyond footnotes

## Analysis recipe

1. **Reduce SCUBA-2 maps and detect sources**: smurf dimm map-making, match filter, top-down peak finding at SNR>=3  
  > "The faint point-source recipe in the orac-dr pipeline was used for the reduction." (2.2 Data Reduction)
   - software: smurf, starlink kappa
   - fitting: _not stated_
   - validation: Jack-knife false detection rate  
  > "the false detection rate for sources at a $>$ 3.5 $\sigma$ significance limit was $\sim$ 8 per cent" (2.3 Source detection)
2. **Identify counterparts using ALMA, radio, MIPS and IRAC colours**: Corrected-Poisson probabilities with IRAC colour cuts; ALMA used as guide  
  > "the corrected-Poisson probabilistic analysis from (cite: Downes86) was employed (see also (cite: Dunlop89))." (3.2 Spitzer identifications)
   - fitting: _not stated_
   - validation: UDS/AS2UDS contamination and reliability test  
  > "50 of the 69 unique SCUBA-2 sources brighter than $S_{\rm 850\mu m}$ $=$ 3.5 mJy had an ALMA-detected counterpart" (3.4 Field contamination)
3. **Derive SFRs and stellar masses and fit cluster evolution**: 850um-SFR scaling relation, summed within 1 Mpc, normalised by M200, fit (1+z)^gamma  
  > "A fit to the evolution in $\Sigma_{\rm SFR}/M_{\rm cl}$ of the form $\Sigma_{\rm SFR}/M_{\rm cl}  \propto (1+z)^\gamma$ gave a median trend" (4.3 Mass-normalised cluster star formation rates)
   - fitting: _not stated_
   - validation: _not stated_

## Software

- **smurf/starlink** 2018A EAO starlink release: SCUBA-2 reduction  
  > "from the 2018A EAO starlink release" (2.2 Data Reduction)
- **topcat** : catalogue handling  
  > "Extensive use was made of topcat (cite: Taylor05) in this study." (Acknowledgements)

## Numeric results

| quantity | value | uncertainty | units | step | quote |
|---|---|---|---|---|---|
| Overdensity of colour-selected 850um sources within 1 Mpc | 4 | 1 | dimensionless | 2 | of a factor of 4 $\pm$ 1 within the central 1 Mpc radius of the clusters |
| gamma of mass-normalised SFR evolution | 5.5 | 0.6 | dimensionless | 3 | gave a median trend with $\gamma$ $=$ 5.5 $\pm$ 0.6 and a dispersion of 0.4 dex |
| Median integrated SFR per cluster | 530 | 80 | Msun/yr | 3 | The median integrated star formation rate is $\Sigma_{\rm SFR}$ $=$ 530 $\pm$ 80 M$_\odot$ yr$^{-1}$ per cluster |
| Median stellar mass of cluster SMGs | 1.9e11 | 0.2e11 | Msun | 3 | The median stellar masses for the reliably-identified members was $M_\ast$ $=$ (1.9 $\pm$ 0.2) $\times$ 10$^{11}$ M$_\odot$ |

## Qualitative findings

- Cluster mass-normalised SFR reaches field halo level at z~1.8, implying reversal of SFR-density relation  
  > "matched that of average halos in the field at $z$ $\sim$ 1.8 $\pm$ 0.2" (abstract)

## Claim tuples

- H: Clusters at z=1.6-2.0 host overdensities of SMGs | E: SCUBA-2 850um survey of 8 clusters with IRAC colour selection | R: Overdensity factor 4±1 within 1 Mpc | F: Modest but significant overdensity of cluster SMGs | **supported**
- H: Mass-normalised SFR rises rapidly and reverses SFR-density relation | E: Fit (1+z)^gamma to clusters compared with field halos | R: gamma=5.5±0.6; matches field at z~1.8±0.2 | F: Reversal occurs near z~1.8 | **supported**

## Reasoning

- Why this data: _not stated_
- Why this method: _not stated_
- How they decided it was enough: _not stated_
- Limitation (authors): Identifications and cluster membership are statistical  
  > "These are statistical identifications and so both the individual source identifications and their assignment as cluster members are uncertain." (5 Conclusions)
- Caveat (inferred, ours): ALMA data play a minor role and are sparse
- Caveat (inferred, ours): Cluster mass estimates are uncertain
- Caveat (inferred, ours): Cluster centres uncertain

## Reproducibility

- Data public (paper): Data available from JCMT, Spitzer, HST and ALMA archives  
  > "The data used in this paper can be obtained from the JCMT, Spitzer, HST and ALMA data archives." (Data availability)
- Products in archive: _not stated_
- Missing: ALMA processing details
- Missing: exact fitting method for gamma
- Data volume (inferred): small for ALMA part; SCUBA-2 and Spitzer data modest (tens of GB)
- Score (inferred): 3/5, SCUBA-2 and Spitzer recipe is fairly detailed, but the ALMA role is minor and unspecified, and the fitting is not fully described.
- Rediscovery candidate: no, ALMA is minor; the main results rely on SCUBA-2 and literature compilations.

## Links

- Method: (cite: Cooke19) (Homogeneous methodology)
- Method: (cite: Simpson19) (Source detection)
- Method: (cite: Downes86) (Probabilistic counterpart identification)
- Companion: (cite: Cooke19) (z=0.8-1.6 cluster sample)
- Companion: (cite: Smith19) (SCUBA-2 study of ClJ1449)
- Related: S2CLS
- Related: AS2UDS
- Related: SEIP

## Checks

```json
{
 "quotes": 45,
 "quotes_ok": 45,
 "quote_pass_rate": 1.0,
 "quotes_too_long": 0,
 "unsupported_facts": 0,
 "project_codes": 3,
 "codes_not_in_text": [],
 "codes_not_in_obscore": [],
 "obscore_codes_not_in_card": [],
 "codes_printed_but_missing": [],
 "numeric_results": 4,
 "numeric_problems": 0,
 "fill": {
  "facts": 73,
  "stated": 33,
  "rate": 0.452
 },
 "evidence_ok": true
}
```
