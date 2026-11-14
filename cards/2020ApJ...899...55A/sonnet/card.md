# Search for Alignment of Disk Orientations in Nearby Star-forming Regions: Lupus, Taurus, Upper Scorpius, ρ Ophiuchi, and Orion

`2020ApJ...899...55A` | The Astrophysical Journal 2020 | first author: Aizawa, Masataka | arXiv: 2007.03393 | DOI: 10.3847/1538-4357/aba43d

Card schema 1.0 | model claude-sonnet-5-5 | depth full | type archival_reuse

## Science

- Fields: protoplanetary_disks, star_formation
- Question: Are proto-planetary disk orientations (position angles) mutually aligned in five nearby star-forming regions (Lupus, Taurus, Upper Sco, Ophiuchus, Orion)?  
  > "We select five nearby star-forming regions that comprise a number of proto-planetary disks with spatially-resolved images with ALMA and HST, and search for the mutual alignment of the disk axes." (abstract)
- Target **Lupus clouds (incl. Lupus III)**: coordinates _not stated_; z/distance 150-200 pc  
  > "The Lupus clouds are a young (1-2 Myr) and nearby (150-200 pc) star-forming region" (3.1 Lupus); distance from Comerón 2008 review  
  > "The Lupus clouds are a young (1-2 Myr) and nearby (150-200 pc) star-forming region" (3.1 Lupus)
- Target **Taurus Molecular Cloud**: coordinates _not stated_; z/distance 140 pc  
  > "The Taurus Molecular Cloud is a nearby low-mass star-forming region located at 140 pc away." (3.2 The Taurus Molecular Cloud); distance from _not stated_
- Target **Upper Scorpius OB Association**: coordinates _not stated_; z/distance 145 pc  
  > "located at 145 pc away" (3.3 The Upper Scorpius OB Association); distance from Preibisch et al. 2002  
  > "located at 145 pc away" (3.3 The Upper Scorpius OB Association)
- Target **rho Ophiuchi (L1688)**: coordinates L1688: 246.2<RA<247.2 deg, -24.8<Dec<-24 deg  
  > "located at $\sim 137$ pc away (cite: 2017ApJ...834..141O)" (3.4 The rho Ophiuchi cloud complex); z/distance ~137 pc  
  > "located at $\sim 137$ pc away (cite: 2017ApJ...834..141O)" (3.4 The rho Ophiuchi cloud complex); distance from Ortiz-León et al. 2017  
  > "located at $\sim 137$ pc away (cite: 2017ApJ...834..141O)" (3.4 The rho Ophiuchi cloud complex)
- Target **Orion Nebula Cluster**: coordinates _not stated_; z/distance ~400 pc  
  > "ONC is located at $\sim 400$ pc away, and the age is estimated as 2 Myr" (3.5 Orion Nebula Cluster); distance from _not stated_

## Data provenance

- ALMA projects: 2013.1.00220.S, 2015.1.00534.S
- bands: Lupus continuum typical ~335 GHz; comparison dataset Band 6  
  > "The typical frequency of the observation is $\sim 335$ GHz" (4.1 CLEAN+imfit); "we also adopt the completely independent observation in Band 6" (4.4)
- frequencies and spectral setup: _not stated_
- continuum bandwidth: _not stated_
- arrays: _not stated_
- configurations: _not stated_
- baselines: _not stated_
- angular resolution: typical beam 0.34'' x 0.28'' (Lupus, Ansdell+2016); ~0.25'' for Ansdell+2018  
  > "the typical beam size is $0.34'' \times 0.28''$" (4.1 CLEAN+imfit)
- max recoverable scale: _not stated_
- sensitivity: _not stated_
- time on source: _not stated_
- observing dates: _not stated_
- pi or archival as stated: _not stated_
- Other facility **HST (WFPC2)**: Silhouette disk PAs for the ONC (Bally et al. 2000)  
  > "detected 31 disks seen in silhouette in the ONC from the narrow-band images of the Orion Nebula with WFPC2" (3.5 Orion Nebula Cluster)
- Other facility **Gaia DR2**: Parallaxes to select Lupus III members  
  > "We exclude such stars on the basis of the parallaxes from Gaia Data Release 2" (3.1 Lupus)
- Other facility **Planck**: Dust polarization map for magnetic field direction  
  > "we estimate the magnetic field in the region using the *Planck* polarization map" (7 Discussion)
- External data: Lupus disk PAs (0-360 deg, from CO spectroscopy) and cos i  
  > "In the current analysis, we adopt PA estimated by (cite: 2018A&A...616A.100Y) instead of those from continuum images." (3.1 Lupus) [from Yen et al. 2018 (cite: 2018A&A...616A.100Y)]
- External data: Upper Sco disk PAs  
  > "we adopt PA estimated by (cite: 2017ApJ...851...85B), which presents disk parameters in their Table 1." (3.3) [from Barenfeld et al. 2017]
- External data: Ophiuchus disk PAs  
  > "We adopt the values of PA listed in their Table 4." (3.4) [from Cox et al. 2017; Cieza et al. 2019]
- External data: ONC disk PAs from HST  
  > "We use the values of PA listed in their Tables 1 and 2." (3.5) [from Bally et al. 2000]
- External data: Taurus PAs compiled from literature  
  > "We compile the values of PA published in previous literature" (3.2) [from Kitamura 2002; Andrews & Williams 2007; Guilloteau 2011; Long 2018, 2019]
- External data: Planck polarization angle dispersions  
  > "Table D.1 of (cite: 2016A&A...586A.138P) shows that $\sigma_{\psi} = 36^{\circ}\pm0.1^{\circ}$ in the Orion region" (7 Discussion) [from Planck Collaboration 2016b (cite: 2016A&A...586A.138P)]

## Processing

### Calibration

- pipeline or manual: Raw archive data calibrated and reduced with CASA; standard pipelines; self-calibration applied  
  > "Then, we calibrate and reduce the data using CASA 4.4.0." (4 Comparison of different estimators); "we apply self-calibration that adjusts the gains of antennas using the bright emissions of targets" (4 Comparison of different estimators)
- casa version: CASA 4.4.0  
  > "Then, we calibrate and reduce the data using CASA 4.4.0." (4 Comparison of different estimators)
- pipeline version: _not stated_
- archive products used as is: _not stated_
- flux calibrator: _not stated_
- flux scale uncertainty: _not stated_
- self calibration: _not stated_

### Imaging

- task: CASA clean, then imfit  
  > "After creating images using the CASA task `clean`, we deconvolve them with the two-dimensional elliptical Gaussian function using the CASA task `imfit`" (4.1 CLEAN+imfit)
- deconvolver: _not stated_
- weighting robust: Briggs, robust = 0.5  
  > "we adopt a Briggs weighting with a robust weighting parameter of 0.5" (4.1 CLEAN+imfit)
- uv taper: _not stated_
- cell size: sparse modeling image 200x200 pixels, 0.1'' (main text) or 0.01'' (appendix)  
  > "The image $\bm{I} = \{I_{i,j}\}$ is created on 200 $\times$ 200 pixels with one pixel size being $0.1\ensuremath{''}$." (4.3 Sparse modeling)
- image size: _not stated_
- masking: threshold 0.001 Jy/beam, gain 0.02, max 10,000 iterations  
  > "(= 0.001 Jy/Beam in case of the Lupus region in our calculation)" (4.1 CLEAN+imfit)
- multiscale scales: _not stated_
- continuum subtraction: _not stated_
- line free channels: _not stated_
- primary beam correction: _not stated_
- array combination: _not stated_
- smoothing: _not stated_
- final beam: _not stated_
- final rms: _not stated_

### Inherited from earlier work

- Regularization form (l1 + TSV) for sparse modeling  
  > "we adopt $l_{1}$ norm of the image and the Total Square Variation (TSV) term as the regularization terms, following (cite: 2018ApJ...858...56K)" (4.3 Sparse modeling) [from Kuramochi et al. 2018 (cite: 2018ApJ...858...56K)]
- MFISTA optimizer  
  > "we use a monotonic fast iterative shrinkage thresholding algorithm (MFISTA) introduced by (cite: beck2009fast2; beck2009fast) following (cite: 2017AJ....153..159A)" (Appendix) [from Beck & Teboulle 2009; Akiyama et al. 2017b]
- Cross-validation details  
  > "we choose the optimal solutions using 10-fold cross-validation (CV) (see the detail in (cite: 2017ApJ...838....1A))" (Appendix) [from Akiyama et al. 2017a (cite: 2017ApJ...838....1A)]

### Not stated but needed to reproduce (our reading)

- Which archival datasets/ASDM files map to which Lupus targets and which project each is from
- Self-calibration solution intervals and reference antenna
- Line-free channels and continuum averaging windows
- Image size/cell and masks for CLEAN
- uvmodelfit starting model and initial parameters
- Sparse modeling pixel size inconsistent (0.1'' vs 0.01'')
- Details of the ONC ALMA PA analysis
- PA values from the Band 6 reduction and exact disk list for 29 disks

## Analysis recipe

1. **Compile PAs per region and select disks**: Take published PAs; keep disks with PA error <30 deg; Lupus III members selected 3D with Gaia parallax; Oph overlapping disks handled by choosing one catalog or the other; exclude face-on disks  
  > "we select those disks with the estimated PA error less than a certain threshold value: $30^{\circ}$ in our analysis." (2 Statistical analysis)
   - parameter: Lupus III 3D box: -60<x<-56 pc, -114<y<-106 pc  
  > "$-60 < x \;({\rm pc}) < -56$, $-114 < y \;({\rm pc}) < -106$" (3.1 Lupus)
   - assumption: Disk circular, cos i = minor/major axis ratio  
  > "Since we assume that the disk is circular in reality, $\cos$ $i$ should be equal to the ratio of the minor and major axes of the ellipse" (2 Statistical analysis)
   - fitting: _not stated_
   - validation: Compared PAs of 17 overlapping Oph disks between two surveys  
  > "The mean and standard deviation of their difference, $\Delta$PA, are $-2.3^{\circ}$ and $24.0^{\circ}$, respectively" (3.4)
2. **Test PA uniformity**: Kuiper test against uniform distribution; circular mean and standard deviation estimators (doubled angles for 0-180 deg)  
  > "we adopt a statistics proposed by (cite: kuiper1960tests), which improves the KS test for variables with rotational invariance." (2 Statistical analysis)
   - software: astropy
   - parameter: p~0.05 ~ 2 sigma; p~0.003 ~ 3 sigma  
  > "$p\simeq0.05$ roughly corresponds to 2$\sigma$-significance, and $p\simeq0.003$ to 3$\sigma$-significance" (2 Statistical analysis)
   - fitting: _not stated_
   - validation: Check cos i distribution and S/N vs PA for Lupus III  
  > "there is no clear correlation between S/N and PA values either in and outside the Lupus III." (5)
3. **Re-measure Lupus PAs from continuum with three methods**: CLEAN+imfit, uvmodelfit, and sparse modeling (PRIISM) with Gaussian fit and second-moment tensor; compare to published PAs  
  > "we examine the robustness of the derived PAs applying three different methods to continuum images for the Lupus region." (4 Comparison of different estimators)
   - software: CASA, PRIISM
   - parameter: uvmodelfit up to 20 iterations; 20 (Lambda_l, Lambda_t) sets; 10-fold CV; MFISTA up to 1000 iterations; keep images with MSE < MSE_best+sigma  
  > "we use PA estimated only from images with MSE less than ${\rm MSE}_{\rm best}$ + $\sigma({\rm MSE}_{\rm best})$." (Appendix)
   - fitting: Gaussian fit and tensor of second-order moments within 3 sigma contour of Gaussian  
  > "we determine $L$ to be $3\sigma$ contours of derived Gaussian" (Appendix)
   - validation: Compare Delta PA vs Ansdell+2016 CLEAN+imfit reference, Tazzari+2017, Band 6 data, Yen+2018  
  > "there are seven independent measurements of PA" (4.4)
4. **Compare to magnetic field and filament**: Alfvén Mach number from Planck polarization dispersion; field direction from Planck map with bilinear interpolation  
  > "we determine the direction of magnetic field to be PA $\simeq 10^{\circ}$ at the scale of 0.3$^\circ$ and $\simeq 170^{\circ}$ the scale of 1$^\circ$" (7 Discussion)
   - assumption: sigma_phi ~ sigma_psi, M_A ~ sigma_psi  
  > "If $\sigma_{\phi}$ is assumed to be the same as $\sigma_{\psi}$" (7 Discussion)
   - fitting: _not stated_
   - validation: _not stated_

## Software

- **CASA** 4.4.0: Calibration, clean, imfit, uvmodelfit  
  > "we calibrate and reduce the data using CASA 4.4.0." (4)
- **PRIISM** : Sparse modeling imaging  
  > "we use Python Module for Radio Interferometry Imaging with Sparse Modeling (PRIISM, (cite: 2019nakazato))" (4.3)
- **astropy** : Kuiper test p-values  
  > "In computing $p$-value, we employ `astropy`" (2)

## Numeric results

| quantity | value | uncertainty | units | step | quote |
|---|---|---|---|---|---|
| Kuiper p, entire Lupus (37 disks) | 0.29 | not stated | dimensionless | 2 | / Lupus / 37 / $7^{\circ}$ / $0.3\ensuremath{''}$ / Radio/ALMA / 0.29 / |
| Kuiper p, Lupus III (16 disks) | 0.037 | not stated | dimensionless | 2 | The statistical significance of this non-uniformity is barely $2\sigma$ ($p=0.037$) |
| Mean PA ± sigma, Lupus III | 77.3 ± 69.9 | not stated | deg | 2 | Mean(PA) $\pm$ $\sigma$(PA) =$77.3^{\circ} \pm 69.9^{\circ}$ |
| Kuiper p, Taurus / Upper Sco / Ophiuchus / L1688 / ONC | 0.69 / 0.16 / 0.68 / 0.95 / 0.47 | not stated | dimensionless | 2 | / Taurus / 50 / $15^{\circ}$ / 0.4–1$\ensuremath{''}$ / Radio$^{b}$ / 0.69 / |
| Delta PA mean and std vs Yen+2018 (22 overlap disks) | 0.17 and 30.9 | not stated | deg | 3 | the mean and the standard deviation of $\Delta$PA are $0.17^{\circ}$ and $30.9^{\circ}$, respectively |
| M_A from Planck | 0.6-0.8 | not stated | dimensionless | 4 | Eq ([\[eq:MA-CF\]](#eq:MA-CF)) implies that $\mathcal{M}_{\rm A} \simeq 0.6 \sim 0.8$ |

## Qualitative findings

- Disk PAs in Taurus, Upper Sco, Ophiuchus and ONC are consistent with random orientation.  
  > "The disks located in the star-forming regions, except the Lupus clouds, do not show any signature of the alignment, supporting the random orientation." (abstract)
- Different PA estimators including sparse modeling agree without significant bias.  
  > "there is no significant bias in the estimated PA among different analysis methods and datasets" (4.4)

## Claim tuples

- H: Disk axes are aligned within star-forming regions | E: Kuiper test of PA distributions in five regions | R: Only Lupus III gives p=0.037; others p>0.16 | F: Mostly random orientation, consistent with turbulent origin; Lupus III is marginal | **supported**
- H: Lupus III PAs are robust against estimator choice | E: CLEAN+imfit, uvmodelfit, sparse modeling, other datasets and literature | R: No significant bias, large scatter | F: PAs are robust | **supported**
- H: Lupus III alignment is related to filament and magnetic field | E: Compare mean PA with filament and Planck field direction | R: Disks parallel to filament, ~perpendicular to field | F: Suggestive, not conclusive | **partially**

## Reasoning

- Why this data: _not stated_
- Why this method: Kuiper test handles rotational invariance unlike KS test  
  > "a widely-used statistics to validate the non-uniformity of the distribution, the Kolmogorov-Smirnov test for instance, cannot be applied in a straightforward fashion." (2)
- Alternative: ALMA ONC data rejected because of spurious elongation giving artificial 6 sigma alignment; HST used instead  
  > "our preliminary analysis suggested an *artificial* alignment of the disks even at a 6$\sigma$ level." (3.5)
- How they decided it was enough: _not stated_
- Limitation (authors): Statistically limited sample; Lupus III result marginal  
  > "Our current result is statistically limited, so future analyses or observations of other disk systems are highly desired." (8 Summary and conclusion)
- Caveat (inferred, ours): Kuiper test ignores PA errors; threshold of 30 deg arbitrary
- Caveat (inferred, ours): Heterogeneous literature PAs from different methods across regions
- Caveat (inferred, ours): Lupus III selection after seeing data; no look-elsewhere correction
- Caveat (inferred, ours): 16 disks give only 2 sigma

## Reproducibility

- Data public (paper): Raw data downloaded from ALMA Science Archive  
  > "First, we download the raw data from the ALMA Science Archive (https://almascience.nao.ac.jp/aq/)." (4)
- Products in archive: _not stated_
- Missing: Self-cal and imaging parameters beyond those given
- Missing: Full per-disk output PAs of the re-measurement
- Missing: Exact regularization of final images
- Data volume (inferred): ~50-200 GB for Lupus raw ALMA data
- Score (inferred): 6/5, Main statistics reproducible from published tables; re-measurement partly specified.
- Rediscovery candidate: yes, Kuiper test on tabulated PAs is fully reproducible; numeric p-values given.

## Links

- Method: Kuramochi et al. 2018 (cite: 2018ApJ...858...56K) (Sparse modeling formulation)
- Method: Nakazato et al. 2019 (cite: 2019nakazato) (PRIISM)
- Companion: Ansdell et al. 2016 (cite: 2016ApJ...828...46A) (Lupus ALMA survey data)
- Companion: Yen et al. 2018 (cite: 2018A&A...616A.100Y) (Spectroscopic PAs)
- Related: ODISEA
- Related: ALMA Lupus survey

## Checks

```json
{
 "quotes": 67,
 "quotes_ok": 67,
 "quote_pass_rate": 1.0,
 "quotes_too_long": 0,
 "unsupported_facts": 0,
 "project_codes": 2,
 "codes_not_in_text": [],
 "codes_not_in_obscore": [],
 "obscore_codes_not_in_card": [],
 "codes_printed_but_missing": [],
 "numeric_results": 6,
 "numeric_problems": 0,
 "fill": {
  "facts": 91,
  "stated": 52,
  "rate": 0.571
 },
 "evidence_ok": true
}
```
