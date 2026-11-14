# Molecular clouds as hubs in spiral galaxies: gas inflow and evolutionary sequence

`2024MNRAS.534..683Z` | Monthly Notices of the Royal Astronomical Society 2024 | first author: Zhou, J. W. | arXiv: 2409.03696 | DOI: 10.1093/mnras/stae2101

Card schema 1.0 | model claude-sonnet-5-5 | depth full | type archival_reuse

## Science

- Fields: nearby_galaxies, star_formation, milky_way_ism
- Question: Can multi-scale hub-filament structures be recovered in the spiral galaxy NGC 628 from CO(2-1), and do they show gas inflow and an evolutionary sequence?  
  > "the main goal of this work is to directly recover the multi-scale hub-filament structures in a spiral galaxy NGC 628 (M74 or the Phantom Galaxy)." (Introduction)
- Target **NGC 628 (M74)**: coordinates _not stated_; z/distance 9.8 Mpc  
  > "corresponding to a linear resolution $\sim$50 pc at the distance 9.8 Mpc (cite: Leroy2021-257; Anand2021-501)" (2 Data); "The inclination angle of NGC 628 is only 8.9 degree (cite: Lang2020-897)." (2 Data); distance from Leroy2021-257; Anand2021-501  
  > "corresponding to a linear resolution $\sim$50 pc at the distance 9.8 Mpc (cite: Leroy2021-257; Anand2021-501)" (2 Data); "The inclination angle of NGC 628 is only 8.9 degree (cite: Lang2020-897)." (2 Data)

## Data provenance

- ALMA projects: 2012.1.00650.S, 2017.1.00886.L
- bands: _not stated_
- frequencies and spectral setup: _not stated_
- continuum bandwidth: _not stated_
- arrays: 12m+7m+TP combined  
  > "We used the combined 12m+7m+TP PHANGS-ALMA CO (2$-$1) data cubes" (2 Data)
- configurations: _not stated_
- baselines: _not stated_
- angular resolution: ~1.1 arcsec (~50 pc); spectral resolution 2.5 km/s  
  > "which have a spectral resolution of 2.5 km s$^{-1}$ and an angular resolution $\sim$1.1$''$" (2 Data)
- max recoverable scale: _not stated_
- sensitivity: _not stated_
- time on source: _not stated_
- observing dates: _not stated_
- pi or archival as stated: PHANGS-ALMA survey data products from PHANGS team website  
  > "All the data are available on the PHANGS team website" (2 Data)
- Line: CO J=2-1 (not stated)
- Other facility **JWST (PHANGS-JWST)**: 7.7 and 21 micron maps, ~0.67 arcsec  
  > "JWST) 7.7 and 21 $\mu$m maps with an angular resolution $\sim$0.67$''$" (2 Data)
- Other facility **VLT/MUSE (PHANGS-MUSE)**: H-alpha map, ~0.92 arcsec  
  > "H$_{\alpha}$ emission map with an angular resolution $\sim$0.92$''$" (2 Data)
- External data: Embedded-phase durations t_fb,21um ≈ 5.1 Myr and t_obsc ≈ 2.3 Myr for NGC 628  
  > "In this work, we directly take the typical values $t_{\mathrm{fb, 21 \mu m}}=$ 5.1 Myr and $t_{\rm obsc}=$ 2.3 Myr." (3.6 Star formation) [from Kim2023-944]
- External data: CO-to-H2 conversion alpha_CO^2-1 ≈ 6.7 Msun pc^-2 (K km/s)^-1  
  > "$\alpha^{2-1}_{\rm CO} \approx 6.7~\rm M_{\odot} \rm pc^{-2} (\rm K~km~s^{-1})^{-1}$ (cite: Leroy2022-927)" (3.1 Dendrogram) [from Leroy2022-927]
- External data: Inclination of NGC 628 of 8.9 degrees  
  > "The inclination angle of NGC 628 is only 8.9 degree (cite: Lang2020-897)." (2 Data) [from Lang2020-897]

## Processing

### Calibration

- pipeline or manual: _not stated_
- casa version: _not stated_
- pipeline version: _not stated_
- archive products used as is: PHANGS-ALMA released data cubes and moment maps used directly  
  > "We used the combined 12m+7m+TP PHANGS-ALMA CO (2$-$1) data cubes" (2 Data)
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
- masking: Strictly masked Moment 0 map from PHANGS-ALMA products used for dendrogram  
  > "we select the strictly masked Moment 0 map to identify structures." (3.1 Dendrogram)
- multiscale scales: _not stated_
- continuum subtraction: _not stated_
- line free channels: _not stated_
- primary beam correction: _not stated_
- array combination: 12m+7m+TP  
  > "combined 12m+7m+TP PHANGS-ALMA CO (2$-$1) data cubes" (2 Data)
- smoothing: _not stated_
- final beam: _not stated_
- final rms: _not stated_

### Inherited from earlier work

- Masking strategy and completeness of moment maps  
  > "Details of the masking strategy and completeness statistics are presented in the PHANGS pipeline paper (cite: Leroy2021-255)." (footnote 4) [from Leroy2021-255]
- Gaussian fitting of averaged spectra procedure  
  > "following the procedure described in (cite: Zhou2024-682), we fitted the averaged spectra of 773 leaf structures individually" (3.2 Velocity components) [from Zhou2024-682]
- FILFINDER filament characterization  
  > "As done in (cite: Zhou2024arXiv), we also use the FILFINDER algorithm to characterize the filamentary structures around the hub." (3.4.1 Identification) [from Zhou2024arXiv]
- Velocity gradient fitting  
  > "we follow the same analysis presentend in (cite: Zhou2022-514) to fit the velocity gradients around the intensity peaks." (3.4.2 Velocity gradient) [from Zhou2022-514]

### Not stated but needed to reproduce (our reading)

- FILFINDER parameters (smoothing, adaptive threshold, branch pruning)
- KinMS rotation model inputs (rotation curve, centre, PA)
- GAUSSPY+ parameters (SNR thresholds, alpha values)
- Velocity-gradient fitting details (aperture, fit method, mass estimation)
- Virial ratio and velocity dispersion definitions and formula
- Dendrogram settings for the 21 um and H-alpha maps' sigma_rms values
- Criteria for the visual classification into A/B/C
- Exact data product versions and URLs

## Analysis recipe

1. **Identify CO structures**: Dendrogram decomposition of strictly masked Moment 0 map; leaves as potential hubs  
  > "we only require the smallest area of the identified structure be larger than 1 beam area." (3.1 Dendrogram)
   - software: astrodendro
   - parameter: min_npix = 1 beam area, no other parameters; 773 leaves  
  > "Finally, we obtained 773 leaf structures." (3.1 Dendrogram)
   - fitting: _not stated_
   - validation: _not stated_
2. **Derive sizes and masses**: Ellipse radius R_eff = sqrt(2a x 2b)*D; mass from alpha_CO times integrated intensity times area  
  > "$R_{\rm eff}$ =$\sqrt{2a \times 2b}*D$" (3.1 Dendrogram)
   - assumption: alpha_CO = 6.7; distance 9.8 Mpc  
  > "$\alpha^{2-1}_{\rm CO} \approx 6.7~\rm M_{\odot} \rm pc^{-2} (\rm K~km~s^{-1})^{-1}$ (cite: Leroy2022-927)" (3.1 Dendrogram)
   - fitting: _not stated_
   - validation: _not stated_
3. **Remove rotation and fit spectra**: KinMS dynamical models to remove bulk rotation, then GAUSSPY+ fit of average spectra  
  > "we removed the bulk motion due to the rotation of galaxy by creating gas dynamical models using the Kinematic Molecular Simulation (KinMS) package" (3.2 Velocity components)
   - software: KinMS, GAUSSPY+
   - fitting: Automated Gaussian decomposition; almost all structures single-peak  
  > "Almost all structures exhibit a single-peak profile." (3.2 Velocity components)
   - validation: _not stated_
4. **Classify hub-filament morphology**: Moment 0 in each structure's velocity range, extended to 2.5x hub size, classified by eye into A, B, C  
  > "All leaf structures were classified by eye into three categories only based on their morphology" (3.3 Classification)
   - parameter: enlargement factor 2.5 times effective radius  
  > "extending to 2.5 times the hub size (the effective radius of the leaf structure)" (3.3 Classification)
   - fitting: _not stated_
   - validation: Enlargement factor chosen by trying several  
  > "After trying different enlargement factors" (3.3 Classification)
5. **Identify filaments and fit velocity gradients**: Regrid images 2x pixels, run FILFINDER, fit velocity gradients around peaks for leaf-HFs-A; compare to mass  
  > "we have to regrid the images and increase the number of pixels in the images from $N_{x}*N_{y}$ to $2N_{x}*2N_{y}$" (3.4.1 Identification)
   - software: FILFINDER, scipy.ndimage
   - parameter: zoom with interpolation order 3  
  > "regrid the image by setting an interpolation order of 3." (footnote 5)
   - fitting: _not stated_
   - validation: Gradient-scale slope compared to free-fall expectation (R^-1.5)  
  > "In the free-fall, the velocity gradient $\nabla v$ and the scale $R$ satisfy $\nabla v \propto R^{-1.5}$." (5.1 Formation of hub-filament structures)
6. **Density contrast**: C = N_hub/N_a, ring of width equal to effective radius  
  > "We define the density contrast $C$ as the ratio of the average column density in the hub region, $N_{\rm hub}$" (3.5.1 Density contrast)
   - fitting: _not stated_
   - validation: Comparison restricted to overlapping scale range to rule out resolution effects  
  > "We confined the comparison of leaf-HFs-A, leaf-HFs-B and leaf-HFs-C to this scale range" (3.5.3 Scale and density)
7. **Associate 21 um and H-alpha structures**: Dendrogram of 21 um and H-alpha maps, filter faint ones, associate if peak separation < CO effective radius  
  > "If the separations are less than the effective radius of a CO structure, we consider the corresponding 21 $\mu$m or H$_{\alpha}$ structures are associated with the CO structure." (3.5.2 Association)
   - software: astrodendro
   - parameter: min_value = min_delta = 3 sigma_rms, min_npix = 1 beam; retain peaks above median or contrast >1.5  
  > "we also take the values of *min_value*= 3\*$\sigma_{\rm rms}$, *min_delta* = 3\*$\sigma_{\rm rms}$" (3.1 Dendrogram)
   - fitting: _not stated_
   - validation: _not stated_
8. **Estimate embedded cluster ages and masses**: SFR surface density from 21 um; age linearly scaled with CO-21um separation between 2.3 and 5.1 Myr  
  > "Assuming $t_{0}$ = 2.3 Myr, the age of the embedded star cluster is" (3.6 Star formation)
   - assumption: t_fb = 5.1 Myr, t_obsc = 2.3 Myr from Kim et al.; estimate rough  
  > "Therefore, the estimate is quite rough, given the significant uncertainty regarding the duration time." (3.6 Star formation)
   - fitting: _not stated_
   - validation: Compared with SED-fitting masses of Hassani et al.  
  > "The results here are quite consistent with the findings in (cite: Hassani2023-944)." (3.6 Star formation)

## Software

- **astrodendro** : Dendrogram decomposition of CO, 21 um and H-alpha maps  
  > "Using the *astrodendro* package" (3.1 Dendrogram)
- **KinMS** : Gas dynamical models to remove galactic rotation  
  > "Kinematic Molecular Simulation (KinMS) package" (3.2 Velocity components)
- **GAUSSPY+** : Gaussian decomposition of average spectra  
  > "fully automated Gaussian decomposer `GAUSSPY+`" (3.2 Velocity components)
- **FILFINDER** : Filament identification  
  > "we also use the FILFINDER algorithm to characterize the filamentary structures around the hub" (3.4.1 Identification)
- **scipy.ndimage** : zoom regridding of images  
  > "We do this by using the **zoom** function from the **scipy.ndimage** module" (footnote 5)

## Numeric results

| quantity | value | uncertainty | units | step | quote |
|---|---|---|---|---|---|
| Number of CO leaf structures | 773 | not stated | count | 1 | Finally, we obtained 773 leaf structures. |
| Leaf-HFs-A, B, C counts | 234, 181, 358 | not stated | count | 4 | The numbers of structures in the three categories are 234, 181 and 358. |
| Leaf-HFs-A with identified filaments | 185 | not stated | count | 5 | we successfully identified the filaments for only 185 leaf-HFs-A structures |
| Velocity gradient vs scale slope | nabla v ∝ R^-0.9 | not stated | dimensionless | 5 | However, Fig.[9](#gradient)(a) only gives $\nabla v \propto R^{-0.9}$. |
| Fraction associated with both 21 um and H-alpha (A, B, C) | 58% (95/163), 37% (44/119), 18% (46/251) | not stated | percent | 7 | 58% (95/163), 37% (44/119) and 18% (46/251) |
| Typical CO-21um separation | 0.64 | not stated | arcsec | 8 | The typical value of $d$ is $\sim$ 0.64$''$ |
| Associated 21 um and H-alpha structures | 313 (37%) and 324 (28%) | not stated | count | 7 | there are 313 21 $\mu$m structures (37%, 313/841) and 324 H$_{\alpha}$ structures (28%, 324/1142) |

## Qualitative findings

- Leaf-HFs-A have highest density contrast, largest mass and lowest virial ratio  
  > "leaf-HFs-A exhibit the best hub-filament morphology, which also have the highest density contrast, the largest mass and the lowest virial ratio." (abstract)
- Density contrast decreases as virial ratio increases  
  > "As expected, the density contrast decreases as the virial ratio increases." (5.2 Evolutionary sequence)

## Claim tuples

- H: Velocity gradients around CO peaks indicate gas inflow, making them hub-filament structures | E: Fit velocity gradients around peaks of 185 leaf-HFs-A with FILFINDER filaments | R: Gradients correspond to masses 1e5-1e7 Msun, slope R^-0.9 | F: Gravitational inflow, slower than free fall | **supported**
- H: Leaf-HFs-A are more evolved than leaf-HFs-C | E: Compare 21 um/H-alpha association, peak intensities and CO-21um separations | R: Association fractions 58% vs 18%; intensities and separations larger in A | F: Possible evolutionary sequence C to A | **supported**
- H: Absence of hubs in leaf-HFs-C is not a resolution effect | E: Density contrast vs scale correlation and comparison within overlapping scale range | R: No correlation within categories; same trends in overlap range | F: Absence of hubs is real | **supported**

## Reasoning

- Why this data: Face-on, nearby, high-resolution CO and multiwavelength coverage  
  > "It is covered by multi-wavelength observations." (2 Data)
- Why this method: _not stated_
- Alternative: Broadly masked Moment 0 map rejected as noisier with possible false positives  
  > "they tend to be noisier and may contain false positives" (3.1 Dendrogram)
- How they decided it was enough: _not stated_
- Limitation (authors): Cluster age/mass estimate is rough; small sample for separations  
  > "However, the sample size here is very limited." (3.6 Star formation)
- Limitation (authors): CO may be optically thick, underestimating column density  
  > "We note that CO could be optically thick, which may lead to an underestimation of the column density" (3.5.2 Association)
- Caveat (inferred, ours): Classification by eye is subjective and not reproducible without criteria
- Caveat (inferred, ours): Face-on geometry and 50 pc resolution limit real filament identification
- Caveat (inferred, ours): Single galaxy
- Caveat (inferred, ours): Constant alpha_CO assumed
- Caveat (inferred, ours): Evolutionary sequence inferred from snapshot statistics; separation-age mapping is linear assumption

## Reproducibility

- Data public (paper): Data on PHANGS team website  
  > "All the data used in this work are available on the PHANGS team website." (Data availability)
- Products in archive: _not stated_
- Missing: Visual classification labels
- Missing: FILFINDER, GAUSSPY+, KinMS parameters
- Missing: Velocity gradient fitting details
- Data volume (inferred): ~ a few GB (PHANGS cubes and maps for one galaxy)
- Score (inferred): 4/5, Public products and main steps described, but many parameters and visual classification unspecified.
- Rediscovery candidate: no, Visual classification and unspecified tool parameters prevent a complete redo, though data are public.

## Links

- Method: Leroy2021-255 (PHANGS-ALMA pipeline and masking)
- Method: Zhou2024-682 (Spectral fitting procedure and ellipse enlargement)
- Companion: Zhou2024arXiv (Hub-filament analysis in NGC 4321 and NGC 5236)
- Related: PHANGS-ALMA
- Related: PHANGS-JWST
- Related: PHANGS-MUSE

## Checks

```json
{
 "quotes": 66,
 "quotes_ok": 66,
 "quote_pass_rate": 1.0,
 "quotes_too_long": 0,
 "unsupported_facts": 0,
 "project_codes": 2,
 "codes_not_in_text": [],
 "codes_not_in_obscore": [],
 "obscore_codes_not_in_card": [],
 "codes_printed_but_missing": [],
 "numeric_results": 7,
 "numeric_problems": 0,
 "fill": {
  "facts": 92,
  "stated": 49,
  "rate": 0.533
 },
 "evidence_ok": true
}
```
