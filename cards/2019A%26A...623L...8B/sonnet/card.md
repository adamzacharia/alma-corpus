# Unveiling a cluster of protostellar disks around the massive protostar GGD 27 MM1

`2019A&A...623L...8B` | Astronomy and Astrophysics 2019 | first author: Busquet, G. | arXiv: 1902.07581 | DOI: 10.1051/0004-6361/201833687

Card schema 1.0 | model claude-sonnet-5-5 | depth full | type archival_reuse

## Science

- Fields: star_formation, protoplanetary_disks
- Question: What are the properties and spatial distribution of the protostellar disks in the GGD 27 cluster, and how do they compare with disks in nearby regions (Taurus, Ophiuchus, ONC)?  
  > "Investigate the properties of the protostellar disks in the GGD 27 cluster and compare them with those obtained from disks formed in nearby regions." (abstract)
- Target **GGD 27 (MM1, MM2)**: coordinates _not stated_; z/distance 1.4 kpc  
  > "GGD 27 is a reflection nebula at a distance of 1.4 kpc (Girart et al. in prep.)" (1 Introduction); distance from Girart et al. in prep. (Gaia DR2 astrometry of pre-main-sequence stars)  
  > "GGD 27 is a reflection nebula at a distance of 1.4 kpc (Girart et al. in prep.)" (1 Introduction)

## Data provenance

- ALMA projects: 2015.1.00480.S
- bands: 1.14 mm, central frequency 263 GHz  
  > "The observations were performed on 2015 December in the C36-8/7 configuration at the central frequency of 263 GHz (1.14 mm)." (2 Observations)
- frequencies and spectral setup: _not stated_
- continuum bandwidth: _not stated_
- arrays: _not stated_
- configurations: C36-8/7  
  > "The observations were performed on 2015 December in the C36-8/7 configuration at the central frequency of 263 GHz (1.14 mm)." (2 Observations)
- baselines: _not stated_
- angular resolution: 45.0 mas x 38.3 mas, PA -62.4 deg  
  > "The angular resolution achieved is 45.0 mas$\times$38.3 mas with a position angle of $-62.4^{\circ}$." (2 Observations)
- max recoverable scale: _not stated_
- sensitivity: _not stated_
- time on source: _not stated_
- observing dates: 2015 December  
  > "The observations were performed on 2015 December in the C36-8/7 configuration" (2 Observations)
- pi or archival as stated: _not stated_
- Other facility **JVLA (VLA15A-132)**: 1 cm counterpart identification  
  > "the high angular resolution ($\sim0.3\ensuremath{''}$) JVLA observations at 1 cm (project ID: VLA15A-132)" (Table)
- External data: Taurus disk fluxes and radii  
  > "1.14 mm flux as a function of the radius of the disks for GGD 27, Taurus-Auriga (cite: Guilloteau2011; Pietu2014), Ophiuchus (cite: Cieza2019), and ONC (cite: Eisner2018)." (4.2 Comparison with nearby regions) [from Guilloteau2011; Pietu2014; Cieza2019; Eisner2018; Tripathi2017]
- External data: X-ray/IR counterparts and spectral classes  
  > "Finally, we list the infrared spectral classification, when available, based on the work of (cite: Pravdo09)." (Table) [from Pravdo04; Pravdo09]
- External data: Extragalactic 1.1 mm source counts  
  > "we used as a reference the deep 1.1 mm ALMA observations carried out by (cite: Hatsukade16) over a 2 arcmin$^2$ field." (6 Background sources) [from Hatsukade16]
- External data: Dust temperatures for MM1 (109 K) and MM2 (35 K)  
  > "we adopted the more appropriate values of $T_{\rm{d}}=109$ K for MM1 and $T_{\rm{d}}=35$ K for MM2(E) and MM2(W)" (7 Disk masses and radii) [from FernandezC11; Qiu09]

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
- weighting robust: robust = 0.5  
  > "we performed maps with a robust weighting of 0.5 and excluded baselines shorter than 300 k$\lambda$." (2 Observations)
- uv taper: baselines shorter than 300 kλ excluded  
  > "excluded baselines shorter than 300 k$\lambda$" (2 Observations)
- cell size: _not stated_
- image size: _not stated_
- masking: _not stated_
- multiscale scales: _not stated_
- continuum subtraction: _not stated_
- line free channels: _not stated_
- primary beam correction: images corrected for primary beam attenuation  
  > "The images presented here are corrected by the primary beam attenuation." (2 Observations)
- array combination: _not stated_
- smoothing: _not stated_
- final beam: 45.0 x 38.3 mas, PA -62.4 deg  
  > "The angular resolution achieved is 45.0 mas$\times$38.3 mas with a position angle of $-62.4^{\circ}$." (2 Observations)
- final rms: _not stated_

### Inherited from earlier work

- Detailed observation description and calibration  
  > "A detailed description is given in (cite: Girart2018)." (2 Observations) [from (cite: Girart2018)]
- Excluding short baselines gives higher fidelity images  
  > "The exclusion of baselines shorter than 300 k$\lambda$ allows to have higher fidelity cleaned images (cite: Girart2018)." (2 Observations) [from (cite: Girart2018)]
- Disk fitting procedure and uncertainties  
  > "The fitting procedure was similar to that used in other fittings by (cite: Palau14) and (cite: Estalella17)." (7 Disk masses and radii) [from (cite: Palau14; Estalella17)]
- Clustering analysis (MST, Q parameter)  
  > "we follow the formalism of (cite: 2004Cartwright) by using the minimum spanning tree (MST)" (8 Statistical analysis) [from (cite: 2004Cartwright)]

### Not stated but needed to reproduce (our reading)

- CASA version and calibration/pipeline details (deferred to Girart et al. 2018)
- Continuum bandwidth and line-free channels
- Imaging task, deconvolver, cell and image size, masks, clean threshold
- Subtraction of the compact free-free component of MM1 (from Girart 2018)
- Halton sampling number of points and random seed
- Sources' flux scale uncertainty

## Analysis recipe

1. **Image continuum and detect sources**: Robust 0.5 maps excluding baselines <300 kλ, primary beam corrected; sources detected above 8σ local rms, plus three tentative at 5σ  
  > "we adopted an 8$\sigma$ threshold for source detection, where $\sigma$ is the local rms noise measured within a radius of $0.5\ensuremath{''}$ of the source" (2 Observations)
   - fitting: 2D Gaussian fit for flux density  
  > "the flux density obtained by fitting a two-dimensional Gaussian function" (Table)
   - validation: Expected background extragalactic sources estimated as no more than one  
  > "we expect no more than one extragalactic sources in our ALMA field of view." (6 Background sources)
2. **Derive disk masses**: Optically thin dust emission with uniform temperature  
  > "assuming that the 1.14 mm dust continuum emission is optically thin and the temperature distribution is uniform." (7 Disk masses and radii)
   - parameter: kappa = 2.63 at 263 GHz, beta = 1, Td = 20 K for most sources  
  > "opacity law of (cite: Beckwith1990) with a dust opacity coefficient of $\kappa_\nu=2.63$ cm$^{-2}$ g$^{-1}$ at 263 GHz and a spectral index $\beta=1$." (7 Disk masses and radii)
   - assumption: Gas-to-dust ratio 100  
  > "We adopted a gas-to-dust ratio of 100" (7 Disk masses and radii)
   - fitting: _not stated_
   - validation: Opacity uncertainty is a factor of two; T=10/30 K changes masses by 8/3 and 2/3  
  > "The uncertainty in the masses due to an uncertainty in the dust opacity is a factor of two." (7 Disk masses and radii)
3. **Fit disk radii and geometry**: Power-law intensity (q=1.1) model up to R_disk, convolved with beam, fit up to 8 parameters  
  > "with an intensity that is a power-law of the radius ($I_\nu\propto r^{-q}$), up to a maximum radius $R_\mathrm{disk}$, convolved with a Gaussian beam" (7 Disk masses and radii)
   - parameter: q = 1.1 for all except ALMA 17 (q=1.46); background 0 except ALMA 7 and 8  
  > "we decided to use the same value of $q$ for all the disks, $q= 1.1$, except for ALMA 17." (7 Disk masses and radii)
   - fitting: Halton pseudo-random sampling of parameter space minimizing rms residual  
  > "The fit was performed by sampling the space parameter of dimension up to 8 using a Halton pseudo-random sequence" (7 Disk masses and radii)
   - validation: Radii consistent with Gaussian-fit radii via R_G=0.46 R_disk; sizes unchanged within uncertainty when all visibilities used  
  > "the derived disk sizes do not change significantly if all visibilities are included" (7 Disk masses and radii)
4. **Cluster structure and mass segregation**: Separation distribution function p(s), MST, Q parameter, mass segregation ratio with 1000 random sets  
  > "We take an average over 1000 random sets of $N$ sources in the cluster to estimate $L_\mathrm{norm}$" (8.3 Mass segregation)
   - parameter: 20 bins, Δs = 2 arcsec; cluster radius 20 arcsec  
  > "We made 20 bins using $\Delta s=2 R_{\rm{GGD27}} / 20=2\ensuremath{''}$" (8.1 Distribution function)
   - fitting: _not stated_
   - validation: _not stated_
5. **Compare with other regions**: Scale fluxes to 140 pc and 1.14 mm (alpha=3), compare median radii above sensitivity limit  
  > "We scaled the observed fluxes of GGD 27 to the distance of 140 pc and the fluxes of Taurus, Ophiuchus, and ONC disks to the wavelength of 1.14 mm assuming a spectral index $\alpha=3$." (4.2 Comparison with nearby regions)
   - fitting: _not stated_
   - validation: _not stated_

## Software


## Numeric results

| quantity | value | uncertainty | units | step | quote |
|---|---|---|---|---|---|
| Number of continuum sources | 25 | not stated | dimensionless | 1 | We detected a cluster of 25 continuum sources |
| Median disk radius GGD 27 | 34 | not stated | au | 5 | the median radius in GGD 27 is 34 au whereas that derived for Taurus and Ophiuchus disks is 92 au and 42 au, respectively |
| Median ONC disk radius | 44 | not stated | au | 5 | the median radius of ONC disks is 44 au |
| Q parameter | 0.68 | not stated | dimensionless | 4 | Having $\bar{m}$ and $\bar{s}$, we now obtain the value for the parameter $\bar{Q}=\bar{m}/\bar{s}=$0.68. |
| Normalized mean edge length | 0.40 | not stated | dimensionless | 4 | we derived the normalized mean edge length, $\bar{m}=$0.40 |
| Fractal dimension | 2.2 | not stated | dimensionless | 4 | it has a notional fractal dimension $D\simeq$2.2 |
| Power-law index q (ALMA 3) | 1.1 | not stated | dimensionless | 3 | $q= 1.1$ |

## Qualitative findings

- Little mass segregation except for the two most massive disks  
  > "Figure [3](#fcluster) shows a dominant $\Lambda_{MSR}$ value of about one, which means no mass segregation or random distribution" (8.3 Mass segregation)

## Claim tuples

- H: GGD 27 disks are smaller than in nearby regions | E: Compare flux-size relation and median radii with Taurus, Ophiuchus, ONC | R: Median 34 au vs 92 au (Taurus), 42 au (Ophiuchus), 44 au (ONC) | F: Only Taurus differs, possibly evolutionary | **supported**
- H: GGD 27 is a young, subclustered cluster | E: MST, Q parameter, mass segregation ratio | R: Q=0.68, D~2.2, Lambda_MSR ~1 | F: Moderate subclustering and no primordial mass segregation suggest youth | **supported**
- H: Disks near the massive star are depleted by external photoevaporation | E: Disk mass and radius vs projected distance from MM1 | R: Deficit of disks at <0.02 pc, no mass depletion, larger disks only beyond 0.04 pc | F: No evidence of photoevaporation depletion; deficit near massive star | **partially**

## Reasoning

- Why this data: _not stated_
- Why this method: _not stated_
- Alternative: Background extragalactic sources considered, expected at most one  
  > "we expect no more than one extragalactic sources in our ALMA field of view." (6 Background sources)
- How they decided it was enough: _not stated_
- Limitation (authors): Masses are lower limits due to optically thin assumption  
  > "the derived masses are most likely a lower limit since we assumed optically thin emission" (Footnote 2)
- Limitation (authors): Sample incomplete; faint small disks cannot be excluded  
  > "since we cannot exclude the presence of faint and small disks" (4.2 Comparison with nearby regions)
- Caveat (inferred, ours): Disk mass tracks protostellar mass only roughly
- Caveat (inferred, ours): Fixed q and Td=20 K assumed for all disks
- Caveat (inferred, ours): Distance (1.4 kpc) is from an unpublished work
- Caveat (inferred, ours): Comparison samples use different radius definitions and wavelengths

## Reproducibility

- Data public (paper): _not stated_
- Products in archive: _not stated_
- Missing: Calibration details (in Girart et al. 2018)
- Missing: Clean imaging parameters beyond robust and uv cut
- Missing: Fitting code (Estalella 2017) settings
- Data volume (inferred): ~50-200 GB
- Score (inferred): 3/5, Data identified by project code and analysis described with parameters, but calibration and imaging details are deferred to another paper.
- Rediscovery candidate: no, Imaging and calibration details are not given; the paper does not state data are public.

## Links

- Method: Estalella 2017, PASP 129, 025003 (Disk fitting method and uncertainties)
- Method: Cartwright & Whitworth 2004 (MST and Q parameter formalism)
- Method: Allison et al. 2009 (Mass segregation ratio)
- Companion: Girart et al. 2018 (cite: Girart2018) (Source of the ALMA observations and calibration)
- Related: VLA15A-132

## Checks

```json
{
 "quotes": 50,
 "quotes_ok": 50,
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
  "facts": 75,
  "stated": 38,
  "rate": 0.507
 },
 "evidence_ok": true
}
```
