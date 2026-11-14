# The ALMA Frontier Fields Survey. IV. Lensing-corrected 1.1 mm number counts in Abell 2744, MACS J0416.1-2403 and MACS J1149.5+2223

`2018A&A...620A.125M` | Astronomy and Astrophysics 2018 | first author: Muñoz Arancibia, A. M. | arXiv: 1712.03983 | DOI: 10.1051/0004-6361/201732442

Card schema 1.0 | model claude-sonnet-5-5 | depth full | type observational_alma_primary

## Science

- Fields: high_z_galaxies, galaxy_clusters_and_sz
- Question: What are the lensing-corrected 1.1 mm number counts of dusty galaxies behind three Frontier Fields clusters, and how far below the mJy level do they reach?  
  > "We aim to estimate the $1.1\,\textmd{mm}$ number counts along the line of sight of three galaxy clusters" (abstract)
- Target **Abell 2744**: coordinates _not stated_; z/distance z=0.308  
  > "Abell 2744 ($z=0.308$), MACSJ0416.1-2403 ($z=0.396$), and MACSJ1149.5+2223 ($z=0.543$)" (2.1.1 High-significance detections); distance from _not stated_
- Target **MACSJ0416.1-2403**: coordinates _not stated_; z/distance z=0.396  
  > "Abell 2744 ($z=0.308$), MACSJ0416.1-2403 ($z=0.396$), and MACSJ1149.5+2223 ($z=0.543$)" (2.1.1 High-significance detections); distance from _not stated_
- Target **MACSJ1149.5+2223**: coordinates _not stated_; z/distance z=0.543  
  > "Abell 2744 ($z=0.308$), MACSJ0416.1-2403 ($z=0.396$), and MACSJ1149.5+2223 ($z=0.543$)" (2.1.1 High-significance detections); distance from _not stated_

## Data provenance

- ALMA projects: 2013.1.00999.S
- bands: 1.1 mm continuum  
  > "individual ALMA $1.1\,\textmd{mm}$ detections in three of the galaxy clusters" (2.1.1 High-significance detections)
- frequencies and spectral setup: _not stated_
- continuum bandwidth: _not stated_
- arrays: _not stated_
- configurations: _not stated_
- baselines: _not stated_
- angular resolution: beam ~0.5''-1.5''  
  > "have synthesized beam sizes between $\sim0.5\ensuremath{''}-1.5\ensuremath{''}$" (2.1.1 High-significance detections)
- max recoverable scale: _not stated_
- sensitivity: rms ~55-71 uJy/beam (natural weighting)  
  > "With natural weighting, our continuum data reach rms depths of $\sim55-71\,\mu\textmd{Jy}\,\textmd{beam}^{-1}$" (2.1.1 High-significance detections)
- time on source: _not stated_
- observing dates: _not stated_
- pi or archival as stated: Cycle 2 project, PI F. Bauer  
  > "cycle 2 project #2013.1.00999.S, PI: F. Bauer" (2.1.1 High-significance detections)
- Other facility **HST Frontier Fields lensing models**: Public lens models (kappa, gamma maps) from several teams  
  > "we make use of gravitational lensing models produced by independent teams" (2.3 Lensing models)
- Other facility **GLASS survey**: Spectroscopic redshifts for some sources  
  > "have spectroscopic redshifts from the GLASS survey" (2.2 Source redshifts)
- External data: Photometric redshift distributions for S/N>5 sources  
  > "we use the photometric redshift probability distributions obtained in Paper II" (2.2 Source redshifts) [from Laporte et al. 2017 (cite: Laporte2017)]
- External data: Public lens models of the Frontier Fields (v4, v4.1)  
  > "for all cluster fields we consider only v4 or newer models" (2.3 Lensing models) [from Caminha2017, Jullo2009, Diego2015, Kawamata2016, Keeton2010, Johnson2014, Sebesta2016 and others]
- External data: Planck EBL at 1.1 mm  
  > "we interpolate the Planck estimate (see (cite: Ade2014), Table 10)" (4.4 Contribution to the extragalactic background light) [from (cite: Ade2014)]
- Simulation/model as data: SIDES simulated sources lensed with CATS v4 used to test Eddington bias  
  > "drawn from the redshift and flux distribution at 1.1mm predicted by the SIDES galaxy formation model (cite: Bethermin2017)" (3.1 Completeness)

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
- weighting robust: natural weighting  
  > "With natural weighting, our continuum data reach rms depths" (2.1.1 High-significance detections)
- uv taper: _not stated_
- cell size: _not stated_
- image size: _not stated_
- masking: _not stated_
- multiscale scales: _not stated_
- continuum subtraction: _not stated_
- line free channels: _not stated_
- primary beam correction: PB-corrected; extraction where PB>0.5  
  > "The source extraction is done within the region where $\textmd{PB}>0.5$" (2.1.1 High-significance detections)
- array combination: _not stated_
- smoothing: _not stated_
- final beam: _not stated_
- final rms: _not stated_

### Inherited from earlier work

- Mosaic images, data reduction and analysis  
  > "Paper I introduces the $1.1\,\textmd{mm}$ mosaic images, data reduction and analy­sis for these galaxy clusters." (2.1.1 High-significance detections) [from Paper I (cite: Gonzalez-Lopez2017)]
- Source extraction procedure and uv-plane flux estimation  
  > "We refer the reader to Paper I for more details regarding the source extraction procedure" (2.1.1 High-significance detections) [from Paper I]
- Photometric redshift SED fitting  
  > "We refer the reader to Paper II for more details regarding the multiwavelength data used" (2.2 Source redshifts) [from Paper II (cite: Laporte2017)]

### Not stated but needed to reproduce (our reading)

- Calibration and imaging details (CASA version, clean parameters) deferred to Paper I
- Exact DBSCAN parameters
- Photometric redshift probability distributions (numeric) from Paper II
- Exact lens model files and versions per cluster beyond table
- Random seeds for Monte Carlo

## Analysis recipe

1. **Build source catalog**: Detect pixels with S/N>=4.5 in PB>0.5 region, group with DBSCAN; uv-plane Gaussian fits for S/N>=5 flux densities  
  > "Sources are detected by searching for pixels with signal-to-noise ratio $(\textmd{S/N})\geq5$, which are then grouped as individual sources using the DBSCAN python algorithm" (2.1.1 High-significance detections)
   - software: DBSCAN, UVMCMCFIT
   - parameter: low-S/N sources: r_eff=0.23'', q=0.58; peak/integrated ratios 0.85, 0.96, 0.96  
  > "we find a typical ratio between the peak and integrated flux density for these size parameters of 0.85, 0.96, and 0.96" (2.1.2 Going to fainter flux densities)
   - fitting: _not stated_
   - validation: _not stated_
2. **Completeness and flux deboosting**: Inject 1e5 artificial sources, extract at S/N>=4.5  
  > "We draw $10^5$ artificial image-plane sources from a uniform distribution in $\log(S_{\textmd{obs}})$ in the range $0.01-10\,\textmd{mJy}$" (3.1 Completeness)
   - fitting: _not stated_
   - validation: Eddington bias tested with SIDES simulation; deboosting consistent  
  > "We find that within the uncertainties, these ratios are consistent with the deboosting corrections" (3.1 Completeness)
3. **Spurious source fraction**: 300 simulated Gaussian noise maps convolved with beam; detections doubled  
  > "we generate 300 simulated non-PB-corrected maps" (3.2 Fraction of spurious sources)
   - fitting: _not stated_
   - validation: Compared to negative mosaics and sources without optical counterparts  
  > "consistent within $1\sigma$ with both the amount of spurious sources from the negative mosaics" (3.2 Fraction of spurious sources)
4. **Magnifications, demagnified fluxes and effective areas**: Monte Carlo (1000 realizations) over redshift and lens range maps; S_demag=S_obs/mu; effective area from source-plane rms maps at S/N 4.5  
  > "we use a Monte Carlo approach with 1000 realizations" (3.3 Source magnifications)
   - parameter: redshift grid dz=0.2 from 0.4 (0.6 for MACSJ1149) to 4  
  > "using steps of $\Delta z=0.2$ in the range $z_{\textmd{min}}=0.4$ to $z_{\textmd{max}}=4$" (2.3 Lensing models)
   - assumption: sources without redshift: Gaussian z=2, sigma=0.5; no multiple images; differential magnification neglected  
  > "we assume a Gaussian redshift distribution centered at $z=2$ with standard deviation 0.5" (2.2 Source redshifts)
   - fitting: _not stated_
   - validation: Compared with literature magnification dispersions  
  > "Our trend of increasing dispersion with source magnification (see Fig. [4](#fig_magnif_gal)) is in line with results by (cite: Zitrin2015), (cite: Meneghetti2017) and (cite: Bouwens2017)." (3.3 Source magnifications)
5. **Compute number counts**: X_i=(1-p_false)/(C_i A_eff); dN/dlogS and N(>S); median over 1000 realizations and models; Poisson limits from Gehrels 1986  
  > "X_i=\frac{1-p_{\textmd{false},i}}{C_i\,A_{\textmd{eff},i}}" (3 Methodology)
   - parameter: Delta log S = 0.5  
  > "We adopt $\Delta\log(S)=0.5$" (3.6 Monte Carlo simulation for source counts)
   - fitting: _not stated_
   - validation: Compared with ALMA blank-field counts and galaxy formation models  
  > "Figure [13](#fig_countsdiffcumu_comp) shows our $1.1\,\textmd{mm}$ number counts compared to results from recent ALMA observations that probe down to the sub-mJy level." (4.2 Comparison to previous ALMA studies and galaxy formation model predictions)

## Software

- **DBSCAN (scikit-learn)** : grouping detected pixels into sources  
  > "grouped as individual sources using the DBSCAN python algorithm" (2.1.1 High-significance detections)
- **UVMCMCFIT** : uv-plane elliptical Gaussian fits for integrated flux densities  
  > "performing two-dimensional elliptical Gaussian fits in the *uv*-plane using the UVMCMCFIT python algorithm" (2.1.1 High-significance detections)

## Numeric results

| quantity | value | uncertainty | units | step | quote |
|---|---|---|---|---|---|
| sources detected at S/N>=4.5 | 19 | not stated | sources | 1 | Including these detections, our final catalog is comprised by 19 sources. |
| median magnification range | 1.3 to 11.3 | not stated | dimensionless | 4 | Median (combined) magnification values for our sample range from 1.3 to 11.3. |
| total effective area CATS v4 z=2 | 5.3 | not stated | arcmin^2 | 4 | They sum to a total effective area of $\approx5.3\,\textmd{arcmin}^2$. |
| resolved EBL contribution down to 0.013 mJy | 8.222 | +8.837/-4.188 | Jy deg^-2 | 5 | $8.222_{-4.188}^{+8.837}$ ($3.861_{-2.059}^{+7.847}$) $\textmd{Jy}\,\textmd{deg}^{-2}$ |
| fraction of Planck EBL resolved down to 0.013 mJy | 43 | +46/-22 | % | 5 | represents $43_{-22}^{+46}\%$ ($20_{-11}^{+41}\%$) of this EBL |
| combined cumulative counts N(>0.013 mJy) | 3.157e4 | +17.40/-1.795 (x1e4) | deg^-2 | 5 | $(3.157_{-1.795}^{+17.40}\,_{-1.505}^{+2.484})\times10^4$ |

## Qualitative findings

- Counts agree between lens models within errors despite systematic magnification variations  
  > "we find an overall agreement among the number counts derived for the different lens models" (abstract)

## Claim tuples

- H: Can ALMA cluster-field counts extend 1.1 mm number counts to tens of uJy? | E: Monte Carlo lensing-corrected counts using several lens models | R: Differential counts span ~2.5 dex down to tens of uJy | F: Counts reach ~4 times fainter than the rms | **supported**
- H: Do the counts flatten at faint fluxes relative to blank-field results? | E: Compare cumulative counts with Aravena2016, Fujimoto2016 | R: Cumulative counts ~1 dex lower below ~0.1 mJy | F: Suggests flattening, but only consistent at 3 sigma | **partially**

## Reasoning

- Why this data: _not stated_
- Why this method: Strong lensing allows probing faint flux densities statistically  
  > "using strong gravitational lensing by massive galaxy clusters" (1 Introduction)
- Alternative: Eddington bias correction skipped; tested with SIDES  
  > "we consider that it is safe to skip any additional Eddington bias correction in this work" (3.1 Completeness)
- How they decided it was enough: _not stated_
- Limitation (authors): Source size stretching and demagnified geometry not treated; counts below 0.1 mJy highly uncertain  
  > "We leave a detailed analysis about the impact of demagnified source geometries on the number counts for future work" (4.3 Effect of source sizes)
- Caveat (inferred, ours): Only 19 sources, Poisson dominated
- Caveat (inferred, ours): Redshifts for low-S/N sources assumed
- Caveat (inferred, ours): Differential magnification neglected
- Caveat (inferred, ours): Low-S/N sizes assumed

## Reproducibility

- Data public (paper): Lens models public from MAST; ALMA project code given  
  > "The lens models were obtained from the Mikulski Archive for Space Telescopes (MAST)." (Acknowledgements)
- Products in archive: _not stated_
- Missing: Paper I calibration/imaging parameters
- Missing: Paper II redshift PDFs
- Data volume (inferred): ~50-100 GB raw ALMA data for three mosaics, plus lens model maps
- Score (inferred): 3/5, Method well described but depends on Paper I/II and no code release.
- Rediscovery candidate: no, Depends on inherited reductions and redshift PDFs not given; extensive Monte Carlo.

## Links

- Method: Coe et al. 2015 (cite: Coe2015) (Magnification and source-plane area methods)
- Method: Bussmann et al. 2016 (cite: Bussmann2016) (uvmcmcfit)
- Companion: González-López et al. 2017 (cite: Gonzalez-Lopez2017) (Paper I: ALMA data and catalog)
- Companion: Laporte et al. 2017 (cite: Laporte2017) (Paper II: photometric redshifts)
- Related: ALMA Frontier Fields Survey
- Related: Frontier Fields
- Related: GLASS
- Related: ASPECS

## Checks

```json
{
 "quotes": 49,
 "quotes_ok": 49,
 "quote_pass_rate": 1.0,
 "quotes_too_long": 0,
 "unsupported_facts": 0,
 "project_codes": 1,
 "codes_not_in_text": [],
 "codes_not_in_obscore": [],
 "obscore_codes_not_in_card": [],
 "codes_printed_but_missing": [],
 "numeric_results": 6,
 "numeric_problems": 0,
 "fill": {
  "facts": 82,
  "stated": 39,
  "rate": 0.476
 },
 "evidence_ok": true
}
```
