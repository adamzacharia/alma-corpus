# Probing fragmentation and velocity sub-structure in the massive NGC 6334 filament with ALMA

`2019A&A...632A..83S` | Astronomy and Astrophysics 2019 | first author: Shimajiri, Y. | arXiv: 1910.02622 | DOI: 10.1051/0004-6361/201935689

Card schema 1.0 | model claude-sonnet-5-5 | depth full | type observational_alma_primary

## Science

- Fields: star_formation, milky_way_ism
- Question: What are the density (core) and velocity sub-structure and fragmentation properties of the massive NGC 6334 main filament, and how do they compare with low-mass filaments such as Taurus B211/B213?  
  > "we investigate the detailed density and velocity structure of the main filament in the high-mass star-forming region NGC 6334." (abstract)
- Target **NGC 6334 main filament**: coordinates _not stated_; z/distance 1.7 kpc  
  > "corresponding to 0.025 pc at a distance of 1.7 kpc." (abstract); distance from _not stated_

## Data provenance

- ALMA projects: 2015.1.01404.S
- bands: Band 3 (3.1 mm)  
  > "We carried out ALMA Cycle 3 observations in Band 3 toward NGC 6334" (2 ALMA observations)
- frequencies and spectral setup: N2H+ and HC5N in narrow band at 61.035 kHz (~0.2 km/s); three 1875 MHz continuum bands; other lines at 31.25 MHz (~100 km/s)  
  > "The N$_2$H$^+$(1–0) line was observed in narrow-band mode at a frequency resolution of 61.035 kHz, corresponding to $\sim\,$0.2 km s$^{-1}$." (2 ALMA observations)
- continuum bandwidth: _not stated_
- arrays: 12m (C36-2) plus ACA 7m; 17-pointing 12m mosaic, 8-pointing ACA mosaic  
  > "We imaged the main filament in the NGC 6334 region using a 17-pointing mosaic with the 12m array and a 8-pointing mosaic with the ACA array." (2 ALMA observations)
- configurations: _not stated_
- baselines: 12m: 11.7–326.8 kλ; ACA: 4.5–48.2 kλ  
  > "projected baseline lengths ranging from 11.7 k$\lambda$ to 326.8 k$\lambda$" (2 ALMA observations)
- angular resolution: ~3'' (0.025 pc)  
  > "The resulting synthesized beam sizes ($\sim$3$\ensuremath{''}$, corresponding to 0.025 pc)" (2 ALMA observations)
- max recoverable scale: ~37'' (0.3 pc) for 12m+ACA; ~14'' (0.1 pc) for 12m only, at 10% level  
  > "sensitive to angular scales up to $\sim$37$\ensuremath{''}$ (corresponding to $\sim$0.3 pc) at the 10% level" (2 ALMA observations)
- sensitivity: _not stated_
- time on source: _not stated_
- observing dates: 12m: 23, 24, 26 Jan 2016; ACA: 16 Mar–8 Jul 2016  
  > "The 12m-array observations were carried out on 23, 24, 26 January 2016 with 42, 46, and 37 antennas, respectively" (2 ALMA observations)
- pi or archival as stated: Project PI Ph. André (own observations)  
  > "as part of project 2015.1.01404.S (PI: Ph. Andr$\acute{\rm e}$)" (2 ALMA observations)
- Line: N2H+ 1-0 (93.176265 GHz)
- Line: HC5N 36-35 (93.188126 GHz)
- Line: HNC 1-0 (90.663572 GHz)
- Line: HC3N 10-9 (90.978989 GHz)
- Line: CH3CCH 6_0-5_0 (102.54798 GHz)
- Line: H2CS 3_{1,2}-2_{1,1} (104.61699 GHz)
- Other facility **APEX/ArTéMiS 350 µm**: 350 µm dust continuum map of the filament (combined with Herschel/SPIRE) used for clump identification and comparison  
  > "we call the map resulting from the combination of APEX/ArT$\acute{\rm e}$MiS 350 $\mu$m (cite: Andre16) and *Herschel*/SPIRE 350 $\mu$m (cite: Russeil13) data the ArT$\acute{\rm e}$MiS 350 $\mu$m map." (3.1 mm continuum emission)
- Other facility **Spitzer 8 µm**: 8 µm map used to identify HII region/shell and a protostellar source  
  > "It is also overlaid as contours on a *Spitzer* 8 $\mu$m emission map in panel $d$" (3.1 mm continuum emission)
- External data: Median dust temperature of 20 K along filament crest from Herschel  
  > "we adopted $T_{\rm dust}$ = 20 K which corresponds to the median dust temperature derived from *Herschel* data along the crest of the filament" (3.3.1) [from (cite: Andre16; Tige17)]
- External data: Filament inner width 0.15±0.05 pc from ArTéMiS  
  > "With a typical inner width of $0.15\pm 0.05\,$pc from the ArTéMiS results (cite: Andre16)" (4.1) [from (cite: Andre16)]
- External data: Aquila prestellar CMF peak ~0.6 Msun from Herschel  
  > "peak of the prestellar core mass function (CMF) at $\sim 0.6\, M_\odot$ as measured with *Herschel* in nearby clouds (cite: Konyves15)" (4.2) [from (cite: Konyves15)]
- Simulation/model as data: CASA simulations of ALMA+ACA observations with the same baselines to test interferometric filtering artifacts (Appendix A)  
  > "simulations of ALMA observations performed with CASA, using the same set of baselines as the real ALMA$+$ACA data, show that interferometric-filtering effects do not generate spurious sub-structures" (2 ALMA observations)

## Processing

### Calibration

- pipeline or manual: CASA calibration with additional manual flagging of a few antennas  
  > "In the calibration process, we made additional flagging of a few antennas that had too low gain or showed large amplitude dispersion in time." (2 ALMA observations)
- casa version: CASA 4.5.3 (12m calibration and imaging); 4.6.0 (7m calibration)  
  > "version 4.5.3 for 12m data calibration and imaging, version 4.6.0 for 7m data calibration" (2 ALMA observations)
- pipeline version: _not stated_
- archive products used as is: _not stated_
- flux calibrator: Callisto and Titan (12m); Mars and Neptune (ACA)  
  > "Absolute flux calibration was achieved by observing two solar system objects (Callisto and Titan) with the 12m array and planets (Mars and Neptune) with ACA." (2 ALMA observations)
- flux scale uncertainty: _not stated_
- self calibration: _not stated_

### Imaging

- task: _not stated_
- deconvolver: _not stated_
- weighting robust: Briggs, robust = 0.5  
  > "we adopted the Briggs weighting scheme with a robust parameter of 0.5" (2 ALMA observations)
- uv taper: _not stated_
- cell size: _not stated_
- image size: _not stated_
- masking: _not stated_
- multiscale scales: _not stated_
- continuum subtraction: _not stated_
- line free channels: _not stated_
- primary beam correction: _not stated_
- array combination: 12m+7m combined image used for flux densities; 12m-only used for source detection  
  > "We used the 12m-only instead of the 12m$+$7m image as the sensitivity of the data is better for the detection of compact ($< 0.1\,$pc) sources" (Footnote 2)
- smoothing: _not stated_
- final beam: Continuum 12m+7m 2.99x1.97''; 12m 2.80x1.84''; N2H+ 3.78x2.40''  
  > "3.1 mm continuum (12m+7m) | ————– | 2.99 $\times$ 1.97 (82.6) | 0.2" (Table 1)
- final rms: Continuum 0.2 mJy/beam (12m+7m), 0.14 (12m); N2H+ 4.4 mJy/beam at 0.2 km/s  
  > "N$_2$H$^+$ (1–0,$E_{\rm u}$=4.472 K) | 93.176265 | 3.78 $\times$ 2.40 (84.1) | 4.4 | 0.2" (Table 1)

### Inherited from earlier work

- Dust opacity law κ=0.1(λ/300µm)^-β cm2/g with β=2, as Herschel Gould Belt survey  
  > "We adopted the same dust opacity law as the *Herschel* Gould Belt survey team" (3.3.1) [from (cite: Hildebrand83; Roy14)]
- Core mean density formula for spheroidal cores  
  > "are the deconvolved FWHM sizes along the major and minor axis of the source, respectively (cite: Konyves15)" (3.3.1) [from (cite: Konyves15)]
- getsources, getfilaments, getimages algorithms  
  > "we made use of the *getsources*, *getfilaments*, and *getimages* algorithms (cite: Menshchikov12; Menshchikov13; Menshchikov17)" (3.3) [from (cite: Menshchikov12; Menshchikov13; Menshchikov17)]

### Not stated but needed to reproduce (our reading)

- Continuum image size, cell size, deconvolver, masking and clean threshold
- Spectral windows and line-free channels for continuum
- getsources/getfilaments detailed settings beyond max size 15'' and scales 3''–16''
- Continuum-subtraction details for line cubes
- Distance to NGC 6334 reference and uncertainty
- Self-calibration usage
- Exact mass sensitivity uncertainties and CMF binning

## Analysis recipe

1. **Extract compact 3.1 mm continuum sources**: getsources on the 12m-only continuum map, with post-selection (remove sources within 3 beams of the edge and below 5σ)  
  > "First, we removed all sources lying closer than 3 ALMA beams from the edge of the map." (Post-extraction selection of getsources results (Appendix))
   - software: getsources
   - parameter: maximum source size 15'' (~0.12 pc)  
  > "we adopted a maximum size of 15 $\ensuremath{''}$ (or $\sim$0.12 pc)" (3.3.1)
   - fitting: _not stated_
   - validation: Cross-check with N2H+ channel maps  
  > "we also applied the *getsources* algorithm to each velocity channel map in the N$_2$H$^+$ data cube." (Post-extraction selection of getsources results (Appendix))
2. **Derive core masses and densities**: Optically thin dust mass from 2D Gaussian flux in 12m+7m image; density assuming spheroidal cores  
  > "We estimated the mass ($M_{\rm tot}$) of each compact continuum source, under the assumption that all of the 3.1 mm continuum emission arises from dust and that the emission is optically thin." (3.3.1)
   - parameter: β=2; Tdust=20 K (50 K for source 1)  
  > "For source ID 1, we adopted a higher temperature value ($T_{\rm dust}$ = 50 K)" (3.3.1)
   - assumption: All 3.1 mm emission is optically thin dust; κ per unit mass of gas+dust  
  > "the dust opacity (per unit mass of gas + dust)" (3.3.1)
   - fitting: 2D Gaussian fitting  
  > "derived from two-dimensional Gaussian fitting" (3.3.1 Compact source extraction from the ALMA 3.1 mm continuum data with getsources)
   - validation: Sensitivity to β=1.5 tested (masses ~3x lower)  
  > "If $\beta = 1.5$ instead of $\beta = 2$, the core masses would be a factor of $\sim$3 lower" (3.3.1)
3. **Remove HFS 2-7 contamination of N2H+ cube**: Multi-velocity-component HFS fit per pixel (N≤3) and subtraction of HFS 2-7 emission  
  > "we fit the N$_2$H$^+$ emission observed at each pixel with a multiple-velocity-component HFS model and subtracted the corresponding HFS 2-7 emission from the data cube." (3.3.2)
   - parameter: add component when residual peak S/N > 10  
  > "Whenever the peak S/N of the residuals was larger than 10, an additional HFS fitting step was performed with $N$+1 components." (Appendix B)
   - fitting: HFS model with same Tex and linewidth for all hyperfine components  
  > "Assuming the same excitation temperature and the same linewidth for all hyperfine transitions (HFS 1-7), and Gaussian line opacity profiles as a function of velocity" (Treatment of multiple velocity components in the N2H+(1-0) spectra (Appendix))
   - validation: Synthetic two-component spectra  
  > "shows model spectra in the case of two velocity components (components 1 and 2) along the line of the sight." (Treatment of multiple velocity components in the N2H+(1-0) spectra (Appendix))
4. **Extract velocity-coherent fiber-like structures**: getfilaments per N2H+ channel (3''–16'' scales), keep structures with >90% crest pixels >3σ in ≥2 consecutive channels, link channels with >60% overlap  
  > "We selected only filamentary structures whose $>$90% pixels along the crest were detected above the $>$ 3$\sigma$ level in each channel." (3.3.2)
   - software: getfilaments
   - fitting: _not stated_
   - validation: Visual inspection of PPV  
  > "careful visual inspection of the data cube" (footnote 5 (Sect. 3.3.2))
5. **Characterize clustering of cores and ArTéMiS clumps**: Nearest-neighbour separation dendrogram (scipy single linkage) with thresholds 0.1 and 0.15 pc; GAUSSCLUMPS on ArTéMiS map; random-source tests (100 realizations)  
  > "with the *scipy* function *cluster.hierarchy.linkage* and the *single* method" (4.1)
   - software: scipy, GAUSSCLUMPS
   - parameter: GAUSSCLUMPS threshold 1 Jy/8''-beam (5σ)  
  > "We applied GAUSSCLUMPS with a detection threshold of 1 Jy/8$''$ -beam corresponding to 5$\sigma$" (4.1)
   - fitting: _not stated_
   - validation: Comparison with getsources and REINHOLD; random distributions  
  > "Thus, we conclude that the seven clumps identified with GAUSSCLUMPS are robust." (Comparison between GAUSSCLUMPS, getsources, and REINOHLD extractions of clumps in the ArTeMiS map (Appendix))
6. **Estimate effective Jeans length and Bonnor-Ebert mass**: λJ,eff and M_BE,eff using N2H+ velocity dispersion plus thermal term, Tk=20 K, per ArTéMiS clump  
  > "Assuming a gas kinetic temperature of 20 K" (4.1)
   - assumption: Tk = 20 K  
  > "Assuming a gas kinetic temperature of 20 K, which corresponds to the median dust temperature derived from" (4.1 Bimodal fragmentation in the NGC 6334 filament)
   - fitting: _not stated_
   - validation: _not stated_

## Software

- **CASA** 4.5.3 / 4.6.0: calibration, imaging, simulations  
  > "Calibration and data reduction were performed with the Common Astronomy Software Application (CASA) package" (2 ALMA observations)
- **getsources** : compact source extraction in continuum and N2H+ channels  
  > "we applied the *getsources* algorithm (cite: Menshchikov12)" (3.3.1)
- **getfilaments** : extraction of fiber-like structures  
  > "using the *getfilaments* algorithm (cite: Menshchikov13)" (3.3.2)
- **GAUSSCLUMPS** : ArTéMiS clump characterization  
  > "we used GAUSSCLUMPS (cite: Stutzki90) to characterize the properties of the ArT$\acute{\rm e}$MiS clumps" (4.1)
- **scipy** : nearest-neighbor dendrogram clustering  
  > "with the *scipy* function *cluster.hierarchy.linkage*" (4.1)
- **REINHOLD (pycupid)** : cross-check of clump identification  
  > "as well as the REINOLD algorithm, available as a python package (*pycupid*; (cite: Berry07))" (Appendix)

## Numeric results

| quantity | value | uncertainty | units | step | quote |
|---|---|---|---|---|---|
| Compact continuum sources identified / embedded in filament | 40 / 26 | not stated | dimensionless | 1 | we identified a total of 40 candidate compact 3.1 mm continuum sources |
| Median core mass (26 cores) | 9.6 | +3.0/-1.9 | Msun | 2 | The median mass of the 26 compact continuum sources embedded in the main filament is $9.6^{+3.0}_{-1.9}$ $M_{\odot}$ |
| Median volume-averaged density of cores | 1.6e7 | quartiles 1.0e7–2.2e7 | cm^-3 | 2 | their median volume-averaged density 1.6$\times$10$^{7}$ cm$^{-3}$ |
| 5σ mass sensitivity | 2.0 | not stated | Msun | 2 | The 5$\sigma$ mass sensitivity of the ALMA 12m continuum data for compact sources is $\sim$$2.0\, M_{\odot}$ |
| Number of fiber-like structures | 5 | not stated | dimensionless | 4 | we identified five distinct fiber-like structures, labeled F-1 to F-5 |
| Typical fiber length | 0.5 | 0.4 | pc | 4 | Their typical length is 0.5$\pm$0.4 pc |
| Typical velocity difference between fibers | 0.8 | not stated | km/s | 4 | the typical velocity difference between them is 0.8 km s$^{-1}$ |
| Mean separation of cores | 0.04 | 0.01 | pc | 5 | the mean separation between observed cores ($0.04\pm 0.01$ pc) |
| Median effective Jeans length in clumps | 0.08 | range 0.04–0.3 | pc | 6 | estimated to range from $\sim$0.04 pc to $\sim$0.3 pc (median: 0.08 pc) |
| Effective Bonnor-Ebert mass in clumps | 7.2 | quartiles 5.0–23.9 | Msun | 6 | or about 7.2 $M_{\odot}$ (lower quartile: 5.0 $M_{\odot}$, upper quartile: 23.9 $M_{\odot}$) |
| 90% completeness mass | 2.6 | not stated | Msun | 2 | estimated 90% completeness level ($2.6\, M_{\odot}$) |

## Qualitative findings

- Cores are grouped into seven groups associated with ArTéMiS clumps, suggesting bimodal fragmentation  
  > "These two distinct separation scales are suggestive of a bimodal fragmentation process in the filament." (abstract)
- Only F-1 and F-2 may be genuine fibers; others may be accretion flows  
  > "the other two features may trace accretion flows onto the main filament." (abstract)

## Claim tuples

- H: Does the NGC 6334 filament fragment at two distinct scales? | E: NNS clustering of ALMA cores and comparison with ArTéMiS clumps and random distributions | R: Clump spacing 0.2–0.3 pc; core separation 0.04±0.01 pc; 16/26 cores in clumps vs 3±2 random | F: Bimodal fragmentation consistent with cylindrical (~4x width) and Jeans-like modes | **supported**
- H: Are cores in NGC 6334 more massive than in nearby low-mass filaments? | E: getsources CMF compared to Aquila Herschel CMF | R: Median core mass 9.6 Msun vs peak ~0.6 Msun | F: Core masses an order of magnitude higher | **supported**
- H: Does the filament have velocity-coherent fiber substructure like Taurus B211/B213? | E: getfilaments on N2H+ cube | R: 5 structures, length ~0.5 pc, Δv ~0.8 km/s | F: Similar to Taurus; only 2–3 may be genuine fibers | **partially**

## Reasoning

- Why this data: _not stated_
- Why this method: Chose channel-by-channel getfilaments with visual inspection rather than FIVE due to few features and no experience  
  > "we had no experience with the FIVE method developed by (cite: Hacar13), we preferred to follow a procedure based on channel-by-channel *getfilaments* extractions" (Footnote 5)
- Alternative: Shell/expanding source D origin for blueshifted N2H+ blobs rejected in favor of cloud-cloud collision  
  > "We conclude that the highly blueshifted N$_2$H$^+$ blobs are more likely related to the cloud-cloud collision scenario" (Appendix D)
- How they decided it was enough: _not stated_
- Limitation (authors): CMF uncertain due to low-number statistics and 3.1 mm dust emissivity; free-free contamination in continuum  
  > "the NGC 6334 CMF shown in Fig. 9 is admittedly quite uncertain due to, for instance, low-number statistics and uncertainties in the 3.1 mm dust emissivity" (4.2)
- Caveat (inferred, ours): Mass depends strongly on assumed β and Tdust; 3 mm emission may include free-free
- Caveat (inferred, ours): Inclination of 30° is assumed to reconcile spacings
- Caveat (inferred, ours): Fiber identification involves visual judgement
- Caveat (inferred, ours): Small number statistics for CMF

## Reproducibility

- Data public (paper): Data from project 2015.1.01404.S acknowledged; public status not explicitly stated  
  > "This paper makes use of the following ALMA data: ADS/JAO.ALMA#2015.1.01404.S." (Acknowledgements)
- Products in archive: _not stated_
- Missing: Imaging parameters (cell, image size, cleaning)
- Missing: getsources/getfilaments configuration files
- Missing: Core catalog is in table but fiber crest data not given
- Data volume (inferred): ~50–100 GB raw (12m + ACA mosaics, Band 3)
- Score (inferred): 5/5, Data and main steps are described and tables of cores exist, but imaging and extraction details are incomplete and getsources is specialized.
- Rediscovery candidate: no, Key extractions rely on getsources/getfilaments with unstated settings and visual selection.

## Links

- Method: (cite: Menshchikov12) (getsources algorithm)
- Method: (cite: Menshchikov13) (getfilaments algorithm)
- Method: (cite: Hacar13) (fiber identification in Taurus)
- Companion: (cite: Andre16) (ArTéMiS 350 µm study of NGC 6334)
- Related: Herschel Gould Belt survey
- Related: ArTéMiS

## Checks

```json
{
 "quotes": 79,
 "quotes_ok": 79,
 "quote_pass_rate": 1.0,
 "quotes_too_long": 0,
 "unsupported_facts": 0,
 "project_codes": 1,
 "codes_not_in_text": [],
 "codes_not_in_obscore": [],
 "obscore_codes_not_in_card": [],
 "codes_printed_but_missing": [],
 "numeric_results": 11,
 "numeric_problems": 0,
 "fill": {
  "facts": 86,
  "stated": 57,
  "rate": 0.663
 },
 "evidence_ok": true
}
```
