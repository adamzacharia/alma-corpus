# Molecular Gas Properties in M83 from CO PDFs

`2018ApJ...854...90E` | The Astrophysical Journal 2018 | first author: Egusa, Fumi | arXiv: 1801.04025 | DOI: 10.3847/1538-4357/aaa76d

Card schema 1.0 | model claude-sonnet-5-5 | depth full | type observational_alma_primary

## Science

- Fields: nearby_galaxies, milky_way_ism, star_formation
- Question: How do galactic structures (center, bar, arm) and stellar feedback affect the PDFs of CO integrated intensity, peak temperature and velocity dispersion in M83?  
  > "In order to investigate how these galactic structures affect gas properties, we have created a probability distribution function (PDF) of the CO integrated intensity ($I_{\rm CO}$), peak temperature, and velocity dispersion for a region with each structure." (abstract)
- Target **M83 (NGC 5236)**: coordinates _not stated_; z/distance nearby; 2'' ~ 40 pc (distance value not stated explicitly)  
  > "a high angular resolution ($2''$ corresponding to $\sim 40$ pc at the distance of M83) has been achieved." (abstract); distance from Thim03 cited for 'nearby'  
  > "a high angular resolution ($2''$ corresponding to $\sim 40$ pc at the distance of M83) has been achieved." (abstract)

## Data provenance

- ALMA projects: 2011.0.00772.S
- bands: 12CO(1-0)  
  > "We have mapped a central disk area of M83 in the $^{12}$CO(1–0) emission using Atacama Large Millimeter/submillimeter Array (ALMA) and the Nobeyama 45m telescope (NRO45m)." (2 Observations and data reduction)
- frequencies and spectral setup: _not stated_
- continuum bandwidth: _not stated_
- arrays: _not stated_
- configurations: 2 EBs compact, 3 EBs extended; 45 mosaic pointings  
  > "consist of two Execution Blocks (EBs) with a compact configuration and three EBs with an extended configuration." (2.1 ALMA observations)
- baselines: _not stated_
- angular resolution: 2.0''x1.1'' (45 pc x 24 pc)  
  > "The synthesized beam is $2.0''\times 1.1''$ in full width at half maximum." (2.2 Nobeyama 45m observations)
- max recoverable scale: _not stated_
- sensitivity: 8.0 mJy/beam (0.33 K) per 2.6 km/s channel; moment-0 1σ 47 mJy/beam km/s (1.8 K km/s)  
  > "We adopt a $1\sigma$ sensitivity of each channel to be 8.0 mJy/beam or 0.33 K with a channel width of 2.6 km/s." (2.2 Nobeyama 45m observations)
- time on source: _not stated_
- observing dates: _not stated_
- pi or archival as stated: _not stated_
- Line: 12CO J=1-0 (not stated)
- Other facility **Nobeyama 45m**: Single-dish CO(1-0) OTF map combined with ALMA to recover total flux  
  > "By combining these two data sets, the total CO flux has been recovered" (abstract)
- External data: Catalogs of young star clusters, HII regions and SNRs used to define feedback areas  
  > "A feedback area and non-feedback area are defined according to catalogs of HII regions, young star clusters, and SNRs." (5 Summary) [from not specified in text (reference list includes Blair12, Blair14, Whit11, Dop10)]
- External data: Bar radial range from Ks-band Fourier analysis  
  > "we define the radial range of the bar to be $r=20''$–$85''$." (3.1 Disk structures) [from (cite: Hiro14)]

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
- cell size: 0.25''  
  > "The pixel size is set to be $0.25''$." (2.2 Nobeyama 45m observations)
- image size: _not stated_
- masking: _not stated_
- multiscale scales: _not stated_
- continuum subtraction: _not stated_
- line free channels: _not stated_
- primary beam correction: _not stated_
- array combination: NRO45m map converted to uv data, then combined with ALMA uv data, FT'd and deconvolved together  
  > "Then, the two uv data sets from ALMA and NRO45m are Fourier-transformed and deconvolved together." (2.2 Nobeyama 45m observations)
- smoothing: _not stated_
- final beam: 2.0''x1.1''  
  > "The synthesized beam is $2.0''\times 1.1''$ in full width at half maximum." (2.2 Nobeyama 45m observations)
- final rms: _not stated_

### Inherited from earlier work

- Detailed observations and data reduction  
  > "A detail of observations and data reduction will be in paper I, and we provide a summary here." (2 Observations and data reduction) [from Hirota et al. (paper I)]

### Not stated but needed to reproduce (our reading)

- CASA version and calibration procedure
- tclean/imaging parameters (weighting, robust, deconvolver, masking, clean threshold)
- Method and software for combining NRO45m and ALMA
- Moment map clipping thresholds
- PDF binning and normalization
- Adopted distance to M83
- Catalog list and matching for feedback areas
- Fit errors for slopes

## Analysis recipe

1. **Create moment maps**: Moment 0 (I_CO) and moment 2 (σ_V) maps, plus peak temperature maps, from combined cube  
  > "The moment 0 (i.e. integrated intensity; $I_{\rm CO}$) and moment 2 (i.e. velocity dispersion; $\sigma_V$) maps are created by" (2.2 Nobeyama 45m observations)
   - assumption: X_CO = 2e20 H2/cm2/(K km/s)  
  > "Assuming the Galactic conversion factor, $X_{\rm CO} = 2\times 10^{20}~{\rm H_2/cm^2/(K~km/s)}$ (cite: Dame01)" (2.2 Nobeyama 45m observations)
   - fitting: _not stated_
   - validation: _not stated_
2. **PDFs by disk structure**: PDFs of I_CO, T_peak, σ_V for center, bar (r=20''-85'', semi-minor 46'') and arm regions  
  > "The semi-minor axis of the bar is set to be $46''$ based on an ellipse fitting to the same $K_{\rm s}$-band image." (3.1 Disk structures)
   - fitting: _not stated_
   - validation: Tested center outer boundary at r=10'' and 30''  
  > "We have confirmed that this general trend holds when the outer boundary of the center region is changed to $r=10''$ or $30''$." (3.1.1 I_CO PDF)
3. **Feedback vs non-feedback PDFs**: Feedback area within 2'' of young clusters, HII regions or SNRs; compare PDFs, fit bright-end slopes at Σ>10^3 Msun/pc2 with a line  
  > "we fit each PDF at $\Sigma > 10^3~M_\odot/{\rm pc^2} = 6\times 10^{22}~{\rm H_2/cm^2}$ with a line." (3.2 Stellar feedback)
   - fitting: linear fit to bright end; slopes consistent within errors  
  > "slopes of the two fitted lines ( lines in Figure [4](#fig:Ico_fb)) are consistent within errors." (3.2.1 I_CO PDF)
   - validation: _not stated_

## Software


## Numeric results

| quantity | value | uncertainty | units | step | quote |
|---|---|---|---|---|---|
| Synthesized beam | 2.0 x 1.1 | not stated | arcsec | 0 | The synthesized beam is $2.0''\times 1.1''$ in full width at half maximum. |
| Moment-0 1σ sensitivity | 1.8 | not stated | K km/s | 1 | A typical $1\sigma$ sensitivity of the integrated intensity map is estimated to be 47 mJy/beam km/s or 1.8 K km/s. |
| Bar/arm I_CO PDF peak position | 10-30 | not stated | K km/s | 2 | Peak positions of bar and arm PDFs are similar (10–30 K km/s), while that for center is an order of magnitude higher. |
| Bar I_CO PDF tail onset | ≳100 | not stated | K km/s | 2 | the bar PDF exhibits a PL like tail at the bright end ($I_{\rm CO} \ensuremath{\gtrsim} 100$ K km/s). |

## Qualitative findings

- σ_V PDF for the bar is shifted to larger values than for the arm; T_peak PDFs similar  
  > "While $T_{\rm peak}$ PDFs do not differ between the bar and arm regions, the $\sigma_V$ PDF for the bar is shifted to the right-hand side of that for the arm." (3.1.2 T_peak and σ_V PDF)

## Claim tuples

- H: Does the bar I_CO PDF bright-end tail indicate active star formation as in the MW? | E: Compare I_CO PDFs of bar and arm regions | R: Bar shows PL-like tail at I_CO≳100 K km/s; arm does not, although SFE is lower in the bar | F: At 40 pc scale a bright-end tail is not always a sign of active star formation | **supported**
- H: Stellar feedback explains the PDF differences between bar and arm | E: Compare PDFs in feedback vs non-feedback areas | R: I_CO and σ_V PDFs do not differ significantly; T_peak shallower in feedback area | F: Feedback does not explain the bar-arm difference at this scale | **supported**

## Reasoning

- Why this data: _not stated_
- Why this method: _not stated_
- Alternative: Stellar feedback truncating the arm PDF considered and found not dominant  
  > "Another explanation for the different $I_{\rm CO}$ PDFs is that the arm PDF is truncated due to the effect of stellar feedback" (3.2 Stellar feedback)
- How they decided it was enough: _not stated_
- Limitation (authors): Few data points above the density limit; constant X_CO assumed  
  > "Although the number of data points that exceed this gas density limit is small" (3.2.1 I_CO PDF)
- Caveat (inferred, ours): PDF shapes depend on uv coverage, noise and moment-map method; no tests shown
- Caveat (inferred, ours): Constant X_CO may bias I_CO PDFs between bar and arm
- Caveat (inferred, ours): Feedback area definition (2'' radius) is arbitrary
- Caveat (inferred, ours): Slope uncertainties unquantified

## Reproducibility

- Data public (paper): ALMA Cycle 0 project cited; NRO45m data not stated as public  
  > "This paper makes use of the following ALMA data: ADS/JAO.ALMA#2011.0.00772.S." (Acknowledgments)
- Products in archive: _not stated_
- Missing: Reduction details deferred to paper I
- Missing: NRO45m data availability and combination method
- Missing: Feedback source catalogs details
- Data volume (inferred): ~50-100 GB raw ALMA, plus NRO45m cube
- Score (inferred): 2/5, Reduction and most analysis parameters are deferred to paper I or omitted; no software named.
- Rediscovery candidate: no, Recipe incomplete, NRO45m data and combination not specified.

## Links

- Method: Hirota et al. (paper I) (Observations and data reduction details)
- Method: (cite: Oss16) (Effect of observing conditions on PDF shapes)
- Companion: Hirota et al. (paper I) (Cloud properties from same data set)

## Checks

```json
{
 "quotes": 33,
 "quotes_ok": 33,
 "quote_pass_rate": 1.0,
 "quotes_too_long": 0,
 "unsupported_facts": 0,
 "project_codes": 1,
 "codes_not_in_text": [],
 "codes_not_in_obscore": [],
 "obscore_codes_not_in_card": [],
 "codes_printed_but_missing": [],
 "numeric_results": 4,
 "numeric_problems": 0,
 "fill": {
  "facts": 60,
  "stated": 24,
  "rate": 0.4
 },
 "evidence_ok": true
}
```
