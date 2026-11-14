# ALMA Observations of a Quiescent Molecular Cloud in the Large Magellanic Cloud

`2017ApJ...850..139W` | The Astrophysical Journal 2017 | first author: Wong, Tony | arXiv: 1708.08890 | DOI: 10.3847/1538-4357/aa9333

Card schema 1.0 | model claude-sonnet-5-5 | depth full | type observational_alma_primary

## Science

- Fields: nearby_galaxies, star_formation, milky_way_ism
- Question: How do size-linewidth, mass and virial properties of substructures differ between a quiescent LMC cloud (PCC) and the active 30 Dor cloud at matched 0.6 pc resolution?  
  > "The present work aims at improving our empirical knowledge of molecular cloud structure and turbulence by comparing two molecular clouds in the nearest star-forming galaxy, the Large Magellanic Cloud." (Introduction)
- Target **PCC (PGCC G282.98-32.40)**: coordinates 5h24m09.2s, -71d53m37s (J2000, reference position)  
  > "PCC | 5$^{\rm h}$24$^{\rm m}$09.2s | $-71$$^\circ$ 53$'$ 37$''$" (Table 1); "adopting $d=48$ kpc (cite: Freedman:10)" (3.3 Structural Decomposition); z/distance d = 48 kpc  
  > "PCC | 5$^{\rm h}$24$^{\rm m}$09.2s | $-71$$^\circ$ 53$'$ 37$''$" (Table 1); "adopting $d=48$ kpc (cite: Freedman:10)" (3.3 Structural Decomposition); distance from Freedman & Madore 2010  
  > "PCC | 5$^{\rm h}$24$^{\rm m}$09.2s | $-71$$^\circ$ 53$'$ 37$''$" (Table 1); "adopting $d=48$ kpc (cite: Freedman:10)" (3.3 Structural Decomposition)
- Target **30 Dor (30Dor-10)**: coordinates 5h38m47.0s, -69d04m36s (J2000, reference position)  
  > "30 Dor | 5$^{\rm h}$38$^{\rm m}$47.0s | $-69$$^\circ$ 04$'$ 36$''$" (Table 1); z/distance d = 48 kpc  
  > "30 Dor | 5$^{\rm h}$38$^{\rm m}$47.0s | $-69$$^\circ$ 04$'$ 36$''$" (Table 1); distance from Freedman & Madore 2010  
  > "30 Dor | 5$^{\rm h}$38$^{\rm m}$47.0s | $-69$$^\circ$ 04$'$ 36$''$" (Table 1)

## Data provenance

- ALMA projects: 2013.1.00832.S, 2011.0.00471.S
- bands: Band 6; 12CO(2-1), 13CO(2-1), C18O(2-1) plus continuum at 218 and 232 GHz  
  > "The correlator was set to simultaneously observe the $^{12}$CO(2–1), $^{13}$CO(2–1), and C$^{18}$O(2–1) lines with a velocity resolution of 0.1 km s$^{-1}$, along with two continuum bands at 218 and 232 GHz." (2.2 ALMA data)
- frequencies and spectral setup: _not stated_
- continuum bandwidth: _not stated_
- arrays: 12m, 7m (ACA) and total power; ACA not used in final analysis  
  > "Observations were performed separately using the 12m, 7m (ACA), and total power (TP) arrays" (2.2 ALMA data)
- configurations: _not stated_
- baselines: _not stated_
- angular resolution: PCC native 1.81x1.24 arcsec; both clouds convolved to 2.5 arcsec (0.6 pc)  
  > "we convolve the data for both clouds to achieve a circular Gaussian beam of FWHM 2.5$''$, corresponding to 0.6 pc." (2.2 ALMA data)
- max recoverable scale: _not stated_
- sensitivity: PCC 12CO rms 0.19 K (0.2 km/s channel) at 2.5 arcsec; continuum rms 0.21 mJy/beam  
  > "2.50 $\times$ 2.50 | 0.2 | 0.19 | 12.0 | 0.21" (Table 1)
- time on source: _not stated_
- observing dates: 2014 and 2015 (PCC, Cycle 2); Cycle 0 (30 Dor)  
  > "ALMA Cycle 2 observations were obtained in 2014 and 2015" (2.2 ALMA data)
- pi or archival as stated: PCC PI Wong; 30 Dor data from PI Indebetouw (previous data set)  
  > "we have also analyzed ALMA data for an additional cloud, 30Dor-10 (cite: Indebetouw:13)" (2.2 ALMA data)
- Line: 12CO J=2-1 (not stated)
- Line: 13CO J=2-1 (not stated)
- Other facility **Mopra**: CO(1-0) maps (MAGMA DR3, project M625) for large-scale view and line ratios  
  > "The region of particular interest for this paper was observed as part of project M625 in 2013." (2.1 Mopra)
- Other facility **Spitzer SAGE / Herschel HERITAGE**: IR photometry for dust temperature SED fits  
  > "The input SED was constructed using the MIPS, PACS and SPIRE data delivered by the Spitzer SAGE and Herschel HERITAGE programs" (3.2 Dust Temperature Validation)
- Other facility **Planck**: Identification of the cold clump  
  > "Planck Galactic Cold Clump (PGCC) G282.98$-$32.40 (cite: Planck:XXVIII)" (Introduction)
- External data: 30 Dor-10 ALMA Cycle 0 cubes  
  > "we have also analyzed ALMA data for an additional cloud, 30Dor-10 (cite: Indebetouw:13)" (2.2 ALMA data) [from Indebetouw:13]
- External data: Southern IR source 24um flux and far-IR luminosity 330 Lsun  
  > "(cite: Seale:14) obtain a far-IR luminosity of 330$\pm$74 $L_\odot$ for this source" (4.1 The Southern IR Source) [from Seale:14]
- External data: Virial-based LMC CO-to-H2 factor ~2.4 times Milky Way  
  > "The CO(1–0) to H$_2$ conversion factor in the LMC is $\sim$2.4 times the factor for the Milky Way, based on the virial analysis of the MAGMA GMC catalog by (cite: Hughes:10)." (3.3 Structural Decomposition) [from Hughes:10]

## Processing

### Calibration

- pipeline or manual: Delivered pipeline-calibrated data; 12m re-imaged in CASA  
  > "calibrated data sets were delivered via the ALMA pipeline." (2.2 ALMA data)
- casa version: _not stated_
- pipeline version: _not stated_
- archive products used as is: _not stated_
- flux calibrator: _not stated_
- flux scale uncertainty: <10%  
  > "Uncertainties in the absolute flux scale are expected to be $<$10%" (3.1)
- self calibration: _not stated_

### Imaging

- task: CASA clean with automatic boxes then interactive clean  
  > "This was performed initially using automatically generated CLEAN boxes (as described in the M100 Band 3 tutorial of the online CASA Guides) followed by a final interactive CLEAN." (2.2 ALMA data)
- deconvolver: _not stated_
- weighting robust: _not stated_
- uv taper: _not stated_
- cell size: _not stated_
- image size: _not stated_
- masking: Moment mask from 3.5 sigma expanded to 2 sigma, padded by 1 pixel  
  > "The mask was obtained by starting at the 3.5$\sigma$ contour and expanding to the 2$\sigma$ contour, then padding the mask by 1 pixel in all directions." (2.2 ALMA data)
- multiscale scales: _not stated_
- continuum subtraction: _not stated_
- line free channels: _not stated_
- primary beam correction: _not stated_
- array combination: 12m + TP via CASA feather; ACA excluded (differences <~10%)  
  > "The resulting 12m images were combined with the corresponding TP images using the CASA task `feather`." (2.2 ALMA data)
- smoothing: Convolved to 2.5 arcsec circular beam  
  > "we convolve the data for both clouds to achieve a circular Gaussian beam of FWHM 2.5$''$" (2.2 ALMA data)
- final beam: _not stated_
- final rms: _not stated_

### Inherited from earlier work

- 30 Dor H2/13CO abundance ratio 5e6 kept for consistency  
  > "using an abundance ratio of H$_2$/$^{13}$CO of $5 \times 10^6$, to maintain consistency with (cite: Indebetouw:13)" (3.5) [from Indebetouw:13]
- Mopra mapping approach same as MAGMA  
  > "We employed the same mapping approach as with MAGMA" (2.1 Mopra) [from Wong:11]
- Spherical radius R = 1.91 sigma_r  
  > "the spherical radius $R = 1.91 \sigma_r$, following (cite: Solomon:87)" (3.3) [from Solomon:87]

### Not stated but needed to reproduce (our reading)

- astrodendro min_value/min_delta/min_npix numeric values in sigma units beyond description, and the rms used
- Imaging weighting, robust, cell and image size, clean thresholds, line-free channels
- Exact CASA version
- TP-to-12m feather scaling and TP calibration details
- Regridded 30 Dor cube specifics (velocity resolution handling, mosaic size)
- Dust SED masks, background region definitions in detail
- How data cubes were smoothed to 2.5 arcsec including primary beam correction

## Analysis recipe

1. **Image and combine ALMA data**: Re-image 12m visibilities in CASA with clean, feather with TP, convolve to 2.5 arcsec  
  > "we re-imaged the calibrated visibilities in CASA." (2.2 ALMA data)
   - software: CASA
   - fitting: _not stated_
   - validation: ACA inclusion tested; fluxes differ by <~10%  
  > "found the fluxes to differ by $\lesssim$10%." (2.2 ALMA data)
2. **Dendrogram decomposition and structure properties**: astrodendro on PPV cubes with bijection property measurement; derive R, L, M_vir, M_lum with bootstrap errors  
  > "we used the Python package *astrodendro*, which decomposes emission into a hierarchy of structures" (3.3)
   - software: astrodendro
   - parameter: local maxima >3 sigma, >=2.5 sigma above merge level, span at least two beams  
  > "Each local maximum was required to span at least two synthesized beams in area." (3.3)
   - assumption: d=48 kpc; X2=4 (alpha_CO=4.3 x X2); M_vir=5 sigma_v^2 R/G  
  > "In this paper we have adopted $X_2$=4 (scaling the luminosity-based masses upward by a factor of 4)" (3.3)
   - fitting: _not stated_
   - validation: 100 bootstrap realizations, scaled by sqrt(pixels per beam)  
  > "For each structure we generate 100 realizations of the data by random sampling with replacement" (3.3)
3. **Fit scaling relations**: Power-law fits in log space with effective variance weighting using kmpfit, initial guess from linregress; exclude points below resolution  
  > "We employ the kmpfit module of the Python package `Kapteyn`" (3.4)
   - software: Kapteyn, scipy
   - fitting: Least squares with effective variance, 95% confidence interval  
  > "weighting each sample by the inverse of its effective variance" (3.4)
   - validation: _not stated_
4. **LTE 13CO mass**: Derive Tex from 12CO peak, tau13, N(13CO), scale with H2/13CO=5e6; Monte Carlo errors  
  > "We derived an LTE-based estimate of clump masses by scaling $N$($^{13}$CO) to $N$(H$_2$) using an abundance ratio of H$_2$/$^{13}$CO of $5 \times 10^6$" (3.5)
   - parameter: Tex floor 8 K, varied 6-10 K in Monte Carlo  
  > "For each realization the $T_{\rm ex}$ floor was randomly varied between 6 and 10 K." (3.5)
   - assumption: 12CO optically thick, common Tex, no beam dilution  
  > "We assume the $^{12}$CO (2–1) line is optically thick at line center and not subject to beam dilution" (3.5)
   - fitting: _not stated_
   - validation: Compared with luminosity and virial masses  
  > "We compare the LTE-based masses with masses derived from the CO luminosity or virial theorem in Figure [11](#fig:masscorr)." (3.5 Comparison with 13CO-based masses)
5. **Dust temperature check**: Modified blackbody fit to 100-500 um SEDs with DUSTEM, beta in [0.8,2.8], Td in [5,55] K, 10% flux uncertainty  
  > "We constrain $T_{d}$ and $\beta$ to lie in the intervals \[5, 55\] K and \[0.8, 2.8\] respectively." (3.2)
   - software: DUSTEM
   - fitting: Levenberg-Marquardt  
  > "an iterative procedure based on the Levenberg-Marquardt method" (3.2)
   - validation: Compared to MAGMA island distribution  
  > "Figure [3](#fig:tdust_histo) presents the distribution of dust temperatures that we obtain for the CO-emitting ‘islands’ identified in the MAGMA survey." (3.2 Dust Temperature Validation)

## Software

- **CASA** : re-imaging, clean, feather  
  > "we re-imaged the calibrated visibilities in CASA." (2.2 ALMA data)
- **astrodendro** : dendrogram decomposition  
  > "we used the Python package *astrodendro*" (3.3)
- **SCIMES** : cluster-based segmentation comparison  
  > "SCIMES, an extension to *astrodendro* that segments the emission into closely related structures via cluster analysis" (4.2)
- **Kapteyn** 2.3: kmpfit power-law fits  
  > "We employ the kmpfit module of the Python package `Kapteyn`" (3.4)
- **DUSTEM** : MBB dust SED fits  
  > "as implemented in the DUSTEM software package" (3.2)
- **gridzilla** : gridding Mopra spectra into cubes  
  > "Spectra were subsequently gridded into a data cube using the ATNF package gridzilla." (2.1 Mopra)

## Numeric results

| quantity | value | uncertainty | units | step | quote |
|---|---|---|---|---|---|
| PCC TP CO(2-1) flux | 1691 | 10 | Jy km/s | 0 | we measure a CO(2–1) flux of 1691$\pm$10 Jy km s$^{-1}$ |
| CO(2-1)/13CO(2-1) flux ratio | 13.5 | 1.6 | dimensionless | 0 | implying a CO(2–1)/$^{13}$CO(2–1) flux ratio of 13.5$\pm$1.6 |
| PCC dust temperature (mask 2) | 15.9 | 1.0 | K | 5 | The PCC and 30 Dor clouds have dust temperatures of $15.9\pm1.0$ K and $37\pm5$ K respectively |
| 30 Dor dust temperature (mask 2) | 37 | 5 | K | 5 | $15.9\pm1.0$ K and $37\pm5$ K |
| Max leaf sigma_v PCC / 30 Dor | 0.95 / 3.20 | not stated | km/s | 2 | $\sigma_v$ for leaves ranges up to 0.95 km s$^{-1}$ for the PCC (3.20 km s$^{-1}$ for 30 Dor) |
| Leaf share of kinetic energy PCC / 30 Dor | 5.5% / 5.1% | not stated | percent | 2 | the leaves as a whole contribute only 5.5% and 5.1% of the energy in PCC and 30 Dor respectively |
| Total CO(1-0) gas mass of PCC (MAGMA) | 2.7e4 | not stated | Msun | 0 | which translates to a molecular gas mass (including helium) of $2.7 \times 10^4$ $M_\odot$ |

## Qualitative findings

- PCC structures have ~10x lower surface density and ~5x lower velocity dispersion than comparable 30 Dor structures  
  > "Structures in the PCC exhibit roughly 10 times lower surface density and 5 times lower velocity dispersion than comparably sized structures in 30 Dor" (abstract)

## Claim tuples

- H: Cloud linewidth normalization depends on environment/star formation activity | E: Identical dendrogram analysis of PCC and 30 Dor at 0.6 pc | R: Linewidth at 1 pc is 0.3 km/s in PCC vs 1.5 km/s in 30 Dor | F: Molecular cloud properties are non-universal | **supported**
- H: Dense structures are near virial equilibrium | E: Compare virial and luminous masses/surface densities | R: Higher-density structures lie near SVE; low-density leaves are super-virial | F: High-density structures near equilibrium | **supported**
- H: Small-scale leaves span full linewidth range | E: Dendrogram leaf properties | R: Southern IR source leaf dominates linewidth in PCC | F: Localized energy injection increases scatter in size-linewidth relations | **supported**
- H: Mass estimators agree | E: Compare CO luminosity, virial and 13CO LTE masses | R: Strong correlations but offsets up to ~6 | F: Estimators depend on uncertain assumptions | **partially**

## Reasoning

- Why this data: _not stated_
- Why this method: Dendrogram approach and matched resolution to compare clouds consistently  
  > "Comparing the PCC cloud with the well-studied 30 Dor cloud using the same analysis techniques at the same physical resolution" (5 Conclusions)
- Alternative: ACA data excluded for limited sensitivity  
  > "In this study we have not incorporated the ACA data, given that the ACA cubes have limited sensitivity" (2.2 ALMA data)
- How they decided it was enough: _not stated_
- Limitation (authors): LTE masses likely biased high; sizes and linewidths not corrected for resolution; bijection underestimates leaf linewidths  
  > "We do not attempt to correct the sizes and line widths for resolution effects." (3.3)
- Limitation (authors): Limited FoV targets bright CO peaks  
  > "the limited field-of-view of the ALMA mosaics confines our observations to regions of bright CO emission" (3.4.2)
- Caveat (inferred, ours): X2=4 partly calibrated assuming virial equilibrium, risking circularity
- Caveat (inferred, ours): Only two clouds compared; 30 Dor is extreme
- Caveat (inferred, ours): 12CO opacity broadening may flatten slopes
- Caveat (inferred, ours): Only northern half of PCC covered

## Reproducibility

- Data public (paper): ALMA data identified by project code; acknowledged as ADS/JAO.ALMA data  
  > "This paper makes use of the following ALMA data: ADS/JAO.ALMA 2011.0.00471.S, 2013.1.00832.S." (Acknowledgments)
- Products in archive: _not stated_
- Missing: Dendrogram exact parameters
- Missing: Imaging parameters
- Missing: Table of structure properties not given
- Data volume (inferred): ~50-200 GB for both projects (12m, ACA, TP); fewer if only 12m+TP
- Score (inferred): 3/5, Public data and named tools, but imaging and dendrogram parameters are incompletely specified.
- Rediscovery candidate: yes, Public archival data, numeric results (scaling relations, line widths) and a mostly described recipe, though imaging parameters are missing.

## Links

- Method: Rosolowsky:08 (dendrogram bijection property measurement)
- Method: Rosolowsky:06 (bootstrap uncertainties and resolution treatment)
- Method: Colombo:15 (SCIMES)
- Companion: Indebetouw:13 (30 Dor-10 ALMA Cycle 0 data)
- Companion: Wong:11 (MAGMA survey)
- Related: MAGMA
- Related: NANTEN
- Related: SAGE
- Related: HERITAGE
- Related: Planck

## Checks

```json
{
 "quotes": 74,
 "quotes_ok": 74,
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
  "facts": 84,
  "stated": 55,
  "rate": 0.655
 },
 "evidence_ok": true
}
```
