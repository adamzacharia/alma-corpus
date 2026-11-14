# The ALMA Survey of 70 μm Dark High-mass Clumps in Early Stages (ASHES). I. Pilot Survey: Clump Fragmentation

`2019ApJ...886..102S` | The Astrophysical Journal 2019 | first author: Sanhueza, Patricio | arXiv: 1909.07985 | DOI: 10.3847/1538-4357/ab45e9

Card schema 1.0 | model claude-sonnet-5-5 | depth full | type large_program_or_survey

## Science

- Fields: star_formation, milky_way_ism
- Question: How do 70 um dark, massive IRDC clumps fragment at the earliest stages (core populations, mass function, spatial distribution, mass segregation), and which high-mass star formation theory do they favor?  
  > "As the first paper of the series, we concentrate
on the dust continuum emission to reveal the clump fragmentation." (abstract)
- Target **12 IRDC clumps (e.g. G010.991-00.082, G014.492-00.139, G028.273-00.167, G327.116-00.294, G331.372-00.116, G332.969-00.029, G337.541-00.082, G340.179-00.242, G340.222-00.167, G340.232-00.146, G341.039-00.114, G343.489-00.416)**: coordinates e.g. G010.991-00.082 18:10:06.65 -19:27:50.7 (J2000); phase centers in Table 1  
  > "G010.991–00.082 18:10:06.65 _−_ 19.27.50.7 29.5 1.27 3.7 12.0 2230" (Table 1); z/distance 2.9-5.4 kpc (average ~4 kpc)  
  > "G010.991–00.082 18:10:06.65 _−_ 19.27.50.7 29.5 1.27 3.7 12.0 2230" (Table 1); distance from kinematic distances from Whitaker et al. 2017  
  > "G010.991–00.082 18:10:06.65 _−_ 19.27.50.7 29.5 1.27 3.7 12.0 2230" (Table 1)

## Data provenance

- ALMA projects: 2015.1.01539.S, 2016.1.01246.S
- bands: Band 6 (~224 GHz; 1.34 mm)  
  > "observations in band 6 ( _∼_ 224 GHz;
1.34 mm) with the main 12 m array" (3. OBSERVATIONS)
- frequencies and spectral setup: Same correlator setup for all; at least 10 lines (N2D+, DCN, DCO+, CCD, 13CS, SiO, C18O, CO, H2CO, CH3OH)  
  > "The same correlator setup was used for all
sources." (3. OBSERVATIONS)
- continuum bandwidth: _not stated_
- arrays: 12 m array, ACA 7 m, and Total Power  
  > "the Atacama Com

pact 7 m Array (ACA; Morita Array), and total power
(TP)." (3. OBSERVATIONS)
- configurations: 12 m: C36-1 to C40-4 depending on source (Table 2)  
  > "G340.179–00.242 0.094 1.41 _×_ 1.29 15 – 704 C36-2/3 – C40-4 36 – 41 (8 – 9)" (Table 2)
- baselines: 12 m: 15-704 m depending on source; 7 m: 8-48 m  
  > "For the 7 m array, the baselines range from 8 – 48 m." (Table 2)
- angular resolution: ~1.2 arcsec (uv-taper used to homogenize beams)  
  > "uv-taper
was used in those observations with more extended baselines

in order to achieve a similar synthesized beam of _∼_ 1 _[′′]_ _._ 2
for every source" (3. OBSERVATIONS)
- max recoverable scale: ~11 arcsec (12 m), ~19 arcsec (ACA)  
  > "These observations are sensitive to angular scales smaller than _∼_ 11 _[′′]_,
and _∼_ 19 _[′′]_, respectively." (3. OBSERVATIONS)
- sensitivity: continuum 1 sigma rms on average 0.10 mJy/beam; line ~9.5 mJy/beam per 0.17 km/s channel (first six lines), ~3.5 mJy/beam per 1.3 km/s channel (last four)  
  > "the 1 _σ_ rms noise for the continuum emission is on average 0.10 mJy beam _[−]_ [1] (see
Table 2 for each individual source)." (3. OBSERVATIONS)
- time on source: 12 m: ~16 min per mosaic (one execution) or ~25 min (two); 7 m: ~50 min (~100 min for first three sources)  
  > "Total 12 m array time on source per mosaic for sources
that were observed in one execution is _∼_ 16 min" (3. OBSERVATIONS)
- observing dates: _not stated_
- pi or archival as stated: PI program, PI Sanhueza  
  > "Cycle 3 (Project ID:
2015.1.01539.S; PI: Sanhueza)" (3. OBSERVATIONS)
- Line: C18O J=2-1 (not stated)
- Line: H2CO J=3-2 (not stated)
- Other facility **ATLASGAL (APEX 870 um)**: Single-dish 870 um continuum used to compare flux recovery and clump sizes/masses  
  > "For
comparison, the 870 _µ_ m dust continuum emission from
the single-dish survey ATLASGAL is overlaid." (4.1 Dust Continuum Emission)
- Other facility **Spitzer and Herschel**: 3.6-70 um images used to select IR-dark clumps  
  > "we first identify IR-dark
clumps from 3.6 to 70 _µ_ m in _Spitzer_ / _Herschel_" (2. SOURCE SELECTION)
- Other facility **MALT90**: Molecular line survey used for clump selection, Vlsr  
  > "11 IRDC clumps
were selected from the Millimetre Astronomy Legacy
Team 90 GHz Survey" (2. SOURCE SELECTION)
- External data: Clump dust temperatures used for core masses  
  > "we have adopted the clump’s
dust temperature derived by Guzm´an et al. (2015)" (5.1 Core Physical Properties) [from Guzmán et al. 2015]
- External data: Clump kinematic distances  
  > "(Whitaker et al. 2017, distances)" (Table 1) [from Whitaker et al. 2017]
- External data: Dust opacity kappa(1.3mm)=0.9 cm2/g  
  > "A value of
0.9 cm [2] g _[−]_ [1] is adopted for _κ_ 1 _._ 3 _mm_" (5.1 Core Physical Properties) [from Ossenkopf & Henning 1994]
- External data: Clump masses from MALT90/Herschel  
  > "(Contreras et al. 2017, masses)" (Table 1) [from Contreras et al. 2017]

## Processing

### Calibration

- pipeline or manual: _not stated_
- casa version: Calibration CASA 4.5.3, 4.6, 4.7; imaging CASA 5.4  
  > "Calibration was carried out using the CASA software
package version 4.5.3, 4.6, and 4.7, while imaging was
done using CASA 5.4" (3. OBSERVATIONS)
- pipeline version: _not stated_
- archive products used as is: _not stated_
- flux calibrator: _not stated_
- flux scale uncertainty: 10% absolute flux uncertainty assumed for Band 6  
  > "Considering an absolute flux uncertainty of 10% for ALMA
observations in band 6" (5.1 Core Physical Properties)
- self calibration: _not stated_

### Imaging

- task: tclean  
  > "we used tclean and its multi-scale
imaging option" (3. OBSERVATIONS)
- deconvolver: _not stated_
- weighting robust: Briggs, robust = 0.5  
  > "Using Briggs weighting with a robust parameter of 0.5" (3. OBSERVATIONS)
- uv taper: applied to extended-baseline data to reach ~1.2 arcsec beam; values not given  
  > "uv-taper
was used in those observations with more extended baselines" (3. OBSERVATIONS)
- cell size: 0.2 arcsec  
  > "All images have 512 _×_ 512 pixels, with a pixel size of 0 _[′′]_ _._ 2." (3. OBSERVATIONS)
- image size: 512 x 512 pixels  
  > "All images have 512 _×_ 512 pixels" (3. OBSERVATIONS)
- masking: _not stated_
- multiscale scales: 0, 5, 15, 25 times the pixel size  
  > "with scales values of 0, 5, 15, and 25
times the pixel size" (3. OBSERVATIONS)
- continuum subtraction: _not stated_
- line free channels: continuum made by averaging line-free channels in visibility space (channels not listed)  
  > "The continuum emission was produced by averaging the line-free channels in visibility space." (3. OBSERVATIONS)
- primary beam correction: Images not PB-corrected; fluxes measured on PB-corrected images  
  > "All images presented in this paper are not primary beam corrected; but all fluxes are measured on the primary beam
corrected images." (3. OBSERVATIONS)
- array combination: 12 m + 7 m combined; TP not used for continuum  
  > "TP antennas do not provide continuum emission and are
therefore not used in this work." (3. OBSERVATIONS)
- smoothing: _not stated_
- final beam: ~1.29x0.86 to 1.41x1.29 arcsec depending on source  
  > "G010.991–00.082 0.115 1.29 _×_ 0.86 15 – 330 C36-1 41 (9 – 10)" (Table 2)
- final rms: 0.068-0.168 mJy/beam per clump (avg 0.10)  
  > "G014.492–00.139 0.168 1.29 _×_ 0.85 15 – 330 C36-1 41 (9 – 10)" (Table 2)

### Inherited from earlier work

- Uncertainty on gas-to-dust ratio and kappa estimated from literature extremes  
  > "Sanhueza
et al. (2017) searched in the literature for possible values
of R and _κ_ _ν_, finding the extreme possible values." (5.1 Core Physical Properties) [from Sanhueza et al. (2017)]
- Maximum stellar mass formulae  
  > "Following Equations (1) and
(2) [2] in Sanhueza et al. (2017)" (2. SOURCE SELECTION) [from Sanhueza et al. (2017)]
- Q parameter method  
  > "we follow
the approach of Cartwright & Whitworth (2004)" (5.5.1 Spatial Core Distribution) [from Cartwright & Whitworth (2004)]
- Core evolutionary classification from outflows (CO, SiO, H2CO) analysis  
  > "molecular outflows were evident in
the CO, SiO, and/or H 2 CO lines (Li et al., in prep.)" (4.3 Evolutionary Stage of the Cores) [from Li et al., in prep.]

### Not stated but needed to reproduce (our reading)

- uv-taper values per source
- line-free channel selection for continuum
- tclean threshold, niter and masking
- self-calibration (if any) and flux calibrators
- Gaussian-fit procedure and dendrogram package/version
- CMF binning and power-law fit method
- warm-core and outflow detection criteria thresholds
- number of mosaic pointings/phase centers for imaging
- which executions were combined (2015 vs 2016 project data)

## Analysis recipe

1. **Image continuum**: Multiscale tclean of line-free channels, 12 m + 7 m combined, with uv-taper to homogenize beam  
  > "we used tclean and its multi-scale
imaging option with scales values of 0, 5, 15, and 25
times the pixel size." (3. OBSERVATIONS)
   - software: CASA
   - parameter: Briggs robust 0.5, 0.2" pixels, 512x512  
  > "Using Briggs weighting with a robust parameter of 0.5" (3. OBSERVATIONS)
   - fitting: _not stated_
   - validation: Compared flux recovery to ATLASGAL 870 um scaled with beta = 1.5  
  > "the 870 _µ_ m emission was scaled by assuming
a dust emissivity spectral index ( _β_ ) of 1.5" (4.1 Dust Continuum Emission)
2. **Identify cores**: Dendrogram leaves as cores; cores below 3.5 sigma integrated flux removed; fluxes PB-corrected  
  > "An intensity threshold of 2.5 _σ_, step of 1.0 _σ_,
and a minimum number of pixels equal to those con

tained in half of each synthesized beam" (4.2 Extraction of Core’s Properties)
   - software: astrodendro (dendrogram technique, Rosolowsky et al. 2008)
   - parameter: threshold 2.5 sigma, step 1.0 sigma, min pixels = half beam, flux cut 3.5 sigma  
  > "cores with integrated flux densities smaller than
3.5 _σ_ were filtered to eliminate spurious detections." (4.2 Extraction of Core’s Properties)
   - fitting: _not stated_
   - validation: Repeated on 12 m only images (242 cores)  
  > "Using the same set of input parameters for dendrograms in the 12 m alone images, a total of 242 cores" (4.2 Extraction of Core’s Properties)
3. **Classify cores**: Protostellar if outflow in CO/SiO/H2CO or warm-core lines H2CO 3(2,2)-2(2,1), 3(2,1)-2(2,0), CH3OH 4(2,2)-3(1,2); otherwise prestellar  
  > "Cores with an absence of both molecular outflow and
warm core tracers were categorized as prestellar." (4.3 Evolutionary Stage of the Cores)
   - fitting: _not stated_
   - validation: _not stated_
4. **Derive core masses and densities**: Optically thin dust emission M = R F D^2/(kappa B(T))  
  > "The mass of the cores was computed assuming optically thin dust continuum emission" (5.1 Core Physical Properties)
   - parameter: kappa1.3mm = 0.9 cm2/g; T = clump Herschel dust temperature; R = 100; mu_H2=2.8  
  > "A gas-to-dust mass ratio of 100 was assumed in this work." (5.1 Core Physical Properties)
   - assumption: core temperature equals clump temperature; 30 K tested for protostellar cores  
  > "On this work, core temperatures have been assumed to be the same as their host clump." (B. ADDITIONAL FIGURES)
   - fitting: _not stated_
   - validation: Mass uncertainty ~50% estimated  
  > "we estimate
mass, number density, and surface density uncertainties
of _∼_ 50%." (5.1 Core Physical Properties)
5. **Test thermal vs turbulent Jeans fragmentation**: Compute Jeans length/mass and compare to MST mean separation corrected by 2/pi projection  
  > "we have used the minimum spanning tree
(MST) method" (5.4.1 Jeans Length and Core Separation)
   - parameter: mu = 2.37 for thermal velocity dispersion  
  > "mean molecular weight per free particle, _µ_ = 2 _._ 37" (5.4 Fragmentation)
   - fitting: _not stated_
   - validation: _not stated_
6. **Spatial distribution and mass segregation**: Q parameter from MST; mass segregation ratios Lambda_MSR and Gamma_MSR with 1000 random sets  
  > "A total of 1000 sets of
random N MST cores were used to derive the average
MST length." (5.5.2 Mass Segregation)
   - fitting: _not stated_
   - validation: Tested 30 K for protostellar cores  
  > "We have tested the effect of changing the temperature for the protostellar cores to 30 K" (5.5.2 Mass Segregation)
7. **Core mass function slope**: Power-law fit to prestellar CMF above the peak (>=0.6 Msun)  
  > "The power law fitting includes
masses up to the peak of the CMF, ≳0.6 _M_ _⊙_ ." (5.6 Core Mass Function)
   - fitting: _not stated_
   - validation: Alternative lower mass cut at 0.9 Msun gives alpha=1.24+-0.12  
  > "If the
next bin is used instead, ≳0.9 _M_ _⊙_, the power law index
is _α_ = 1.24 _±_ 0.12." (5.6 Core Mass Function)

## Software

- **CASA** 4.5.3, 4.6, 4.7 (calibration); 5.4 (imaging): Calibration and imaging (tclean)  
  > "Calibration was carried out using the CASA software
package version 4.5.3, 4.6, and 4.7, while imaging was
done using CASA 5.4" (3. OBSERVATIONS)
- **dendrogram technique (Rosolowsky et al. 2008)** : Core identification and property extraction  
  > "we
have adopted the dendrogram technique (Rosolowsky et
al. 2008)" (4.2 Extraction of Core’s Properties)

## Numeric results

| quantity | value | uncertainty | units | step | quote |
|---|---|---|---|---|---|
| Number of cores detected (excluding 7 edge cores) | 294 | not stated | cores | 2 | We have detected a total of 294 cores, from which
84 (29%) are categorized as protostellar |
| Prestellar core candidates | 210 (71%) | not stated | cores | 3 | The remaining 210
(71%) are considered prestellar core candidates. |
| Prestellar CMF power-law index | 1.17 | 0.10 | dimensionless | 7 | The power law index for the prestellar core
population is _α_ = 1.17 _±_ 0.10 |
| Most massive prestellar core | 11 | not stated | Msun | 4 | The most massive prestellar core has a mass of 11
_M_ _⊙_ . |
| Core mass range | 0.12 to 30.4 | ~50% per core | Msun | 4 | Core
masses range from 0.12 to 30.4 _M_ _⊙_ |
| Mean MST core separation | 0.11 (range 0.07-0.17) | ~10% | pc | 5 | The mean _L_ av for all clumps is
0.11 pc, ranging from 0.07 to 0.17 pc. |
| Mean thermal Jeans length | 0.14 (0.06-0.24) | 24-27% | pc | 5 | The mean
Jeans length for all clumps is 0.14 pc, ranging from 0.06
to 0.24 pc. |
| Q parameter range | 0.63 to 0.80 | negligible | dimensionless | 6 | The narrow range in _Q_ values
(0.63 to 0.80) |
| Fraction of single-dish flux recovered | 10-33% (average 21%) | not stated | percent | 1 | between 10 and 33% (average of 21%) of the single-dish |
| Fraction of cores with mass below Jeans mass | ~74% | not stated | percent | 5 | We find that _∼_ 74% of cores have masses lower than
the Jeans mass |

## Qualitative findings

- No high-mass (>30 Msun) prestellar cores; large population of low-mass cores  
  > "We find a large population of low-mass
( _<_ 1 _M_ _⊙_ ) cores and no high-mass ( _>_ 30 _M_ _⊙_ ) prestellar cores." (abstract)
- No conclusive mass segregation  
  > "There is no conclusive evidence
of mass segregation." (abstract)

## Claim tuples

- H: Does turbulent Jeans fragmentation or thermal fragmentation govern clump fragmentation? | E: Compared MST separations and core masses to thermal and turbulent Jeans length/mass | R: Separations within factor 2 of thermal Jeans lengths; turbulent lengths 2-10x larger | F: Thermal Jeans fragmentation, not turbulent | **supported**
- H: Do high-mass prestellar cores exist at earliest stages? | E: Core mass measurement across 12 clumps | R: No prestellar cores >30 Msun; max prestellar 11 Msun | F: Constrains turbulent core accretion; favors clump-fed scenarios | **supported**
- H: Is the prestellar CMF Salpeter-like? | E: Power-law fit to prestellar CMF | R: alpha = 1.17+-0.10 | F: Slightly shallower than Salpeter 1.35 | **supported**
- H: Is there primordial mass segregation? | E: MSR with MST | R: 8 clumps consistent with 1; 4 marginal with 2-3 cores | F: No solid evidence of mass segregation | **partially**

## Reasoning

- Why this data: ALMA allows uniform, high-resolution study of large samples of clumps  
  > "ALMA has finally made
possible the study of large samples to achieve statistically significant conclusions in uniform fashion" (1. INTRODUCTION)
- Why this method: _not stated_
- Alternative: Turbulent Jeans fragmentation discarded  
  > "We therefore
discard turbulence Jeans fragmentation as the controlling process" (5.4.1 Jeans Length and Core Separation)
- How they decided it was enough: _not stated_
- Limitation (authors): Core temperatures assumed equal to clump temperature; protostellar cores likely warmer; MSR results not robust with few massive cores  
  > "However, protostellar cores
are likely warmer and differences in Figure 13 could be produced by the assumed temperature." (B. ADDITIONAL FIGURES)
- Caveat (inferred, ours): Dendrogram parameters sensitive to resolution and noise; core mass depends on assumed clump temperature
- Caveat (inferred, ours): CMF fit method and completeness correction not described
- Caveat (inferred, ours): Classification relies on unpublished companion outflow results
- Caveat (inferred, ours): Single dust temperature and kappa yield ~50% mass uncertainty

## Reproducibility

- Data public (paper): Project IDs given; ALMA data acknowledged  
  > "This paper makes use of the following ALMA data: ADS/JAO.ALMA#2015.1.01539.S
and ADS/JAO.ALMA#2016.1.01246.S." (Acknowledgments)
- Products in archive: _not stated_
- Missing: uv-taper values
- Missing: tclean cleaning thresholds and masks
- Missing: outflow/warm-core classification (from companion papers)
- Missing: CMF fitting details
- Missing: Table 3/4 machine-readable only online
- Data volume (inferred): Several hundred GB to ~1 TB for 12 mosaics (12m + ACA + TP, 10 lines)
- Score (inferred): 5/5, Imaging and dendrogram parameters and mass recipe are well given; uv-taper, classification inputs and CMF fit details missing, and the data volume is large.
- Rediscovery candidate: no, Core classification depends on line analyses in unpublished companion papers and the data volume is large, though continuum steps are mostly specified.

## Links

- Method: Rosolowsky et al. 2008 (dendrogram core identification)
- Method: Cartwright & Whitworth (2004) (Q parameter)
- Method: Allison et al. (2009); Olczak et al. (2011) (mass segregation ratios)
- Method: Sanhueza et al. (2017) (mass uncertainty and max stellar mass)
- Companion: Contreras et al. 2019 (core dynamics from C18O, DCO+, N2D+)
- Companion: Li et al., in prep. (molecular outflows)
- Companion: Izumi et al., in prep. (warm core line emission)
- Related: MALT90
- Related: ATLASGAL
- Related: Hi-GAL
- Related: ALMA-IMF

## Checks

```json
{
 "quotes": 82,
 "quotes_ok": 82,
 "quote_pass_rate": 1.0,
 "quotes_too_long": 0,
 "unsupported_facts": 0,
 "project_codes": 2,
 "codes_not_in_text": [],
 "codes_not_in_obscore": [
  "2016.1.01246.S"
 ],
 "obscore_codes_not_in_card": [],
 "codes_printed_but_missing": [],
 "numeric_results": 10,
 "numeric_problems": 0,
 "fill": {
  "facts": 86,
  "stated": 63,
  "rate": 0.733
 },
 "evidence_ok": true
}
```
