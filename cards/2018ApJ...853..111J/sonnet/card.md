# First Results from the Herschel and ALMA Spectroscopic Surveys of the SMC: The Relationship between [C II]-bright Gas and CO-bright Gas at Low Metallicity

`2018ApJ...853..111J` | The Astrophysical Journal 2018 | first author: Jameson, Katherine E. | arXiv: 1801.03518 | DOI: 10.3847/1538-4357/aaa4bb

Card schema 1.0 | model claude-sonnet-5-5 | depth full | type multi_facility_alma_minor

## Science

- Fields: nearby_galaxies, milky_way_ism, star_formation
- Question: How does [C II]-bright molecular gas relate to CO-bright gas at low metallicity in the SMC, and what does this imply for the CO-to-H2 conversion factor?  
  > "investigate how the “[C ii]-bright” molecular gas relates to the “CO-bright” molecular gas at low metallicity." (1. INTRODUCTION)
- Target **SMC Southwest Bar regions SWBarS, N22, SWBarN, SWDarkPK (ALMA); N83 (APEX CO only)**: coordinates SWBarS 00h45m24.54s -73d21m42.63s (ACA map center); other regions in Table 3  
  > "a distance of D ≈ 63 kpc, the Small Magellanic Cloud (SMC) provides an ideal laboratory" (1. INTRODUCTION); "SWBarS 00h45m24.54s _−_ 73d21m42.63s 2 _._ 3 _[′]_ _×_ 3 _._ 5 _[′]_ 10 _[◦]_" (Table 3); z/distance D ≈ 63 kpc  
  > "a distance of D ≈ 63 kpc, the Small Magellanic Cloud (SMC) provides an ideal laboratory" (1. INTRODUCTION); "SWBarS 00h45m24.54s _−_ 73d21m42.63s 2 _._ 3 _[′]_ _×_ 3 _._ 5 _[′]_ 10 _[◦]_" (Table 3); distance from _not stated_

## Data provenance

- ALMA projects: 2015.1.00581.S, 2013.1.00652.S
- bands: Band 6 (ACA 7m + Total Power)  
  > "using Band 6 of the ALMA Atacama Compact Array (ACA; 7m-array consisting of 11 antennas) and Total Power array (TP; 12m single-dish) during Cycle 2." (2.2. ALMA Survey of the Southwest Bar)
- frequencies and spectral setup: 12CO and 13CO: 117.2 MHz (152 km/s) bandwidth, 121.15 kHz (0.2 km/s) resolution; C18O: 468.8 MHz, 0.24 MHz resolution; 4th SPW continuum 1875.0 MHz  
  > "Both 12CO and 13CO were observed with 117.2 MHz (152 km s−1) bandwidth and 121.15 kHz (0.2 km s−1) spectral resolution." (2.2. ALMA Survey of the Southwest Bar)
- continuum bandwidth: _not stated_
- arrays: _not stated_
- configurations: _not stated_
- baselines: _not stated_
- angular resolution: ~7" x 5.5" (2.1 x 1.7 pc) for 12CO(2-1)  
  > "synthesized beam sizes of ∼ 7′′ × 5.5′′ (2.1 pc × 1.7 pc) for 12CO (2 − 1)." (2.2. ALMA Survey of the Southwest Bar)
- max recoverable scale: sensitive to all spatial scales via ACA+TP combination  
  > "The combination of the ACA and TP data make the observations sensitive to all spatial scales." (2.2. ALMA Survey of the Southwest Bar)
- sensitivity: RMS 0.08-0.24 K per region/line (Table 4)  
  > "SWBarS 6 _._ 60 _×_ 6 _._ 06 6 _._ 92 _×_ 6 _._ 05 6 _._ 76 _×_ 6 _._ 18 0.17 0.16 0.10" (Table 4)
- time on source: 25.5 s per pointing; 47 pointings (N22, SWBarS, SWBarN), 52 (SWDarkPK)  
  > "22.1′′ spacing of 47 pointings for the N22, SWBarS, and SWBarN regions and 52 pointings for the SWDarkPK with 25.5 s integration time per pointing." (2.2. ALMA Survey of the Southwest Bar)
- observing dates: _not stated_
- pi or archival as stated: _not stated_
- Line: 12CO J=2-1 (not stated)
- Line: 13CO J=2-1 (not stated)
- Line: C18O J=2-1 (not stated)
- Other facility **Herschel PACS/SPIRE-FTS (HS3)**: [C II], [O I], [O III], [N II] maps and FTS spectra  
  > "maps the key far-infrared (far-IR) lines of [C ii] 158 µm, [O i] 63 µm, [O iii] 88 µm, and [N ii] 122 µm with the PACS spectrometer" (2.1. The Herschel Spectroscopic Survey of the SMC)
- Other facility **APEX**: 12CO(2-1) map for N83  
  > "there are new APEX [2] maps of [12] CO (2 _−_ 1) that overlap the N83 HS [3] region (PI: Rubio)." (2.4. Additional Data)
- Other facility **SOFIA GREAT**: velocity-resolved [C II] spectra  
  > "We also use a velocity-resolved [C ii] spectrum from the GREAT heterodyne instrument" (2.4. Additional Data)
- Other facility **Spitzer / Herschel HERITAGE**: IR maps for TIR and dust-based AV; H2 S(0)  
  > "We use mid-infrared Spitzer IRAC and MIPS data from the SMC-SAGE" (2.4. Additional Data)
- Other facility **ATCA+Parkes**: HI 21 cm map  
  > "We use the H i map from Stanimirovi´c et al. (1999) that combined Australian Telescope Compact Array (ATCA) and Parkes 64m radio telescope data." (2.3. H i Data)
- External data: Dust temperature map and tau160-to-AV conversion  
  > "We convert from τ160 to AV using AV ∼ 2200 τ160 from Lee et al. (2015)" (2.6. Estimating AV) [from Lee et al. (2015)]
- External data: HI map of SMC  
  > "We use the H i map from Stanimirovi´c et al. (1999)" (2.3. H i Data) [from Stanimirović et al. (1999)]
- External data: _not stated_ [from Wolfire et al. (2017, in preparation)]
- External data: Dust-based H2 mass estimates for comparison  
  > "recent dustbased molecular gas estimates for the SMC presented in Jameson et al. (2016)." (5.1. Comparison to Dust-based H2 Estimates) [from Jameson et al. (2016)]
- Simulation/model as data: New SMC PDR models (based on Kaufman et al. 2006, Wolfire et al. 2010) used with PDR Toolbox to derive n and G0  
  > "We use new PDR models generated using the elemental abundances and grain properties for SMC conditions" (4.3.2. Method 2: PDR Model)

## Processing

### Calibration

- pipeline or manual: ACA: delivered pipeline calibration; TP: manually calibrated delivered data  
  > "The ACA data were calibrated with the pipeline using CASA version 4.2.2, and no modifications were made to the calibration script." (2.2. ALMA Survey of the Southwest Bar)
- casa version: ACA calibration CASA 4.2.2; TP CASA 4.5.0; imaging CASA 4.7.0  
  > "which were manually calibrated using CASA version 4.5.0" (2.2. ALMA Survey of the Southwest Bar)
- pipeline version: _not stated_
- archive products used as is: Delivered ACA calibration script and imaged TP SPWs used, except SWBarN SPW 17 baseline modification  
  > "We created the reduced measurement set using the script provided with the delivered ACA data and use the imaged TP SPWs as part of the delivered data." (2.2. ALMA Survey of the Southwest Bar)
- flux calibrator: _not stated_
- flux scale uncertainty: _not stated_
- self calibration: _not stated_

### Imaging

- task: clean per SPW, then feather with TP image  
  > "We cleaned each spectral window of the ACA data and imaged it using clean and then used feather to combine the ACA images with the corresponding TP image" (2.2. ALMA Survey of the Southwest Bar)
- deconvolver: _not stated_
- weighting robust: Briggs, robust = 0.5  
  > "We used Briggs weighting with a robust parameter of 0.5 and cleaned to ∼ 2.5 × RMS found away from strong emission in the dirty data cube." (2.2. ALMA Survey of the Southwest Bar)
- uv taper: _not stated_
- cell size: _not stated_
- image size: _not stated_
- masking: conservative masks for cleaning  
  > "we used conservative masks for cleaning to reduce the effects of the poor u − v coverage of the ACA-only data." (2.2. ALMA Survey of the Southwest Bar)
- multiscale scales: _not stated_
- continuum subtraction: none applied (no noticeable continuum)  
  > "we did not include any continuum subtraction for the final imaged cubes." (2.2. ALMA Survey of the Southwest Bar)
- line free channels: _not stated_
- primary beam correction: _not stated_
- array combination: ACA + TP feather  
  > "used feather to combine the ACA images with the corresponding TP image re-gridded to match the ACA data" (2.2. ALMA Survey of the Southwest Bar)
- smoothing: imaged at 0.3 km/s resolution  
  > "The data were imaged at 0.3 km s−1 spectral resolution" (2.2. ALMA Survey of the Southwest Bar)
- final beam: _not stated_
- final rms: _not stated_

### Inherited from earlier work

- TIR prescription  
  > "The totalinfrared intensity is calculated following the prescription by Galametz et al. (2013):" (2.5. Total-infrared) [from Galametz et al. (2013)]
- Standard PACS reduction steps  
  > "(see Poglitsch et al. 2010; Croxall et al. 2012)" (2.1.1. Data Reduction) [from Poglitsch et al. 2010; Croxall et al. 2012]
- Carbon abundance (C/H)MW  
  > "(C/H)MW = 1.4 × 10−4 (Sofia et al. 1997)" (4. ESTIMATING H2 USING [C II] AND 12CO) [from Sofia et al. 1997]

### Not stated but needed to reproduce (our reading)

- Line-free channels / velocity ranges used for integrated intensity and RMS
- Cell size and image size for ACA cubes
- Exact clean threshold in Jy and mask definitions
- Flux calibrator and ACA flux scale uncertainty
- Wolfire et al. (2017) cooling curves are unpublished
- Details of AV regridding and pixel-matching procedure
- Integration velocity ranges for 12CO/13CO maps (partly in Table 5)

## Analysis recipe

1. **Image ACA+TP CO cubes**: Clean ACA data per SPW, feather with TP  
  > "We cleaned each spectral window of the ACA data and imaged it using clean and then used feather" (2.2. ALMA Survey of the Southwest Bar)
   - software: CASA
   - parameter: Briggs robust 0.5, clean to ~2.5×RMS  
  > "We used Briggs weighting with a robust parameter of 0.5" (2.2. ALMA Survey of the Southwest Bar)
   - fitting: _not stated_
   - validation: Compared peak temperature with SEST data convolved to 43": 2.55 K vs 2.56 K  
  > "we find a peak temperature of 2.55 K in the same aperture in the SWBarN ACA+TP data when convolved to 43′′ resolution." (2.2. ALMA Survey of the Southwest Bar)
2. **Estimate AV from dust**: tau160 from HERITAGE 160um map with Lee et al. dust temperatures, AV ~ 2200 tau160  
  > "We convert from τ160 to AV using AV ∼ 2200 τ160 from Lee et al. (2015)" (2.6. Estimating AV)
   - assumption: single dust temperature modified blackbody, beta = 1.5  
  > "Lee et al. (2015) fit a modified blackbody with β = 1.5" (2.6. Estimating AV)
   - fitting: _not stated_
   - validation: _not stated_
3. **Optical depth and 13CO-based XCO**: Use 12CO/13CO ratio for tau12CO, 13CO column density, scale to H2 with 12CO/13CO=70 and C/H=2.8e-5  
  > "we scale by the [12] CO _/_ [13] CO abundance of 70 (Nikoli´c et al. 2007) and the [12] C _/_ H abundance of 2 _._ 8 _×_ 10 _[−]_ [5]" (3.6. Estimating X_CO Using 13CO)
   - parameter: X = 70  
  > "We adopt an abundance ratio of X = 70" (3.5. Estimating the Optical Depth of 12CO)
   - assumption: same Tex for 12CO and 13CO, LTE, 13CO optically thin  
  > "We assume that the 13CO and 12CO lines share the same excitation temperature" (3.6. Estimating XCO Using 13CO)
   - fitting: _not stated_
   - validation: Compared to Wong et al. 2017 and Padoan et al. 2000 caveats  
  > "Wong et al. (2017) make similar estimates of the molecular gas mass using" (3.6. Estimating X_CO Using 13CO)
4. **Remove ionized and atomic gas contributions to [C II]**: Ionized from [N II] 205um and Halpha EM; atomic from HI with WNM/CNM assumptions (50/50)  
  > "We assume that 50% of NHi associated with the CO emission is associated with the CNM and the other 50% with the WNM" (4.2. I[C II] Contribution from Atomic Gas)
   - parameter: Te = 8000 K; CNM n=100 cm-3, T=40 K; WNM n=1 cm-3, T=8000 K  
  > "We assume Te = 8000 K, appropriate for Galactic H ii regions" (4.1. I[C II] Contribution from Ionized Gas)
   - fitting: _not stated_
   - validation: Halpha estimate consistent with [N II]-based upper limit on ne  
  > "consistent with the upper limit on _n_ e determined from the [N ii] 122 _µ_ m/205 _µ_ m values (see Section 3.2)." (4.1. I_[C II] Contribution from Ionized Gas)
5. **Convert remaining [C II] to NH2**: Method 1: fixed T=90 K, n=4000 cm-3; Method 2: PDR Toolbox with SMC models gives n and G0, then SMC [C II] cooling rates  
  > "Using PDR models tuned to the SMC conditions (see Appendix A) to estimate n and the FUV radiation field intensity" (4.3. Converting I[C II] to NH2)
   - software: PDR Toolbox
   - assumption: Carbon abundance (C/H)SMC = 2.8e-5  
  > "We assume a carbon abundance ((C _/_ H) SMC ) that is the Milky Way abundance scaled by the metallicity of the SMC" (4. ESTIMATING H2 USING [C II] AND 12CO)
   - fitting: Nearest model grid match to [C II], [O I], TIR per pixel  
  > "We use the [C ii], [O i], and total-infrared (TIR) intensity images as inputs to determine the nearest volume density and FUV radiation field strength in the model grids" (4.3.2. Method 2: PDR Model)
   - validation: Two methods agree within factor ~1.5  
  > "Table 6 shows that average column densities and total H2 masses for both methods are different by at most a factor of ∼ 1.5." (4.5. NH2 Estimates)
6. **Convert CO to NH2 and combine; derive XCO and molecular-to-atomic ratio**: Galactic XCO = 2e20 for CO (2-1 assumed thermalized to 1-0); total NH2 = [C II]-traced + CO-traced; XCO vs AV compared with models  
  > "we use a Galactic CO-to-H2 conversion factor XCO = 2 × 1020 cm−2 (K km−1 s−1)−1" (4.4. Converting ICO to NH2)
   - fitting: Linear fits of NH2 vs ICO  
  > "The thick dashed colored lines show the linear fits to the data" (Figure 19 caption)
   - validation: Uncertainty budget (quadrature ~50%, adopt factor 2); compared to Wolfire 2010 and Glover & Mac Low 2011  
  > "we choose to adopt an uncertainty of a factor of ∼ 2 for the mass of H2." (4.5.1. Estimating Uncertainties)

## Software

- **CASA** 4.2.2 (ACA calibration), 4.5.0 (TP), 4.7.0 (imaging): calibrate, image (clean) and combine (feather) ACA and TP data  
  > "We used the Common Astronomy Software Applications (CASA; McMullin et al. 2007) package to reduce, combine, and image the data." (2.2. ALMA Survey of the Southwest Bar)
- **HIPE** 12.0.2765: Herschel PACS data reduction  
  > "schel Interactive Processing Environment (HIPE) version 12.0.2765 (Ott 2010)." (2.1.1. Data Reduction)
- **PDR Toolbox** : fit n and G0 from [C II], [O I], TIR  
  > "a version of the PDR Toolbox (Pound & Wolfire 2008) that is updated with the SMC models" (4.3.2. Method 2: PDR Model)
- **NADA (R package, cenfit)** : mean ratios including upper limits (censored data)  
  > "using the cenfit routine in the R package NADA (Lee 2017; Helsel 2005)" (Figure 2)
- **Meudon PDR code** : check of beta scaling assumption in SMC PDR models  
  > "This assumption was checked using the Meudon PDR code (Le Petit et al. 2006)." (A. SMC PDR MODELS)

## Numeric results

| quantity | value | uncertainty | units | step | quote |
|---|---|---|---|---|---|
| [O I]/[C II] ratio | ~0.3 | not stated | dimensionless | 0 | The observed ratio is approximately constant with a value of [Oi]/[Cii] ∼ 0.3. |
| Ionized-gas fraction of [C II] from [N II] | at most 5% | not stated | percent | 4 | suggests that the contribution of ionized gas to [C ii] is at most 5%. |
| Electron density upper limit | ≲ 20 | not stated | cm-3 | 0 | this translates to an upper limit to the electron density of ne ≲ 20 cm−3 |
| Average 12CO/13CO (2-1) ratio | ~5-7.5 | not stated | K km/s ratio | 3 | We find average 12CO/13CO (2 − 1) ratios of ∼ 5 − 7.5 (in units of K km s−1). |
| tau12CO (SWBarN, SWBarS, N22, SWDarkPK) | 7.8, 13.8, 12.5, 19.0 | not stated | dimensionless | 3 | indicate optical depths of τ12CO = 7.8, 13.8, 12.5, and 19.0 for the SWBarN, SWBarS, N22, and SWDarkPK regions, respectively. |
| H2/13CO | 1.25e6 | not stated | dimensionless | 3 | This results in H2/13CO = 1.25 × 106. |
| Median XCO from 13CO (AV>1) | 1.3-2.3e20 | factor of several systematics | cm-2 (K km/s)-1 | 3 | The distributions have median values of 1.3 − 2.3 × 1020 cm−2 (K km s−1)−1 |
| Fraction of molecular gas traced by [C II] | ~70% on average | not stated | percent | 6 | with ∼ 70% of the molecular gas coming from [C ii]-bright regions on average. |
| Average XCO in regions | ~5 XCO,MW | factor ~2 in NH2 | dimensionless | 6 | The values we find for our regions have on average a conversion factor of XCO ∼ 5 XCO,MW. |
| Peak NH2/NHI | ~1.5; CO detected out to ~0.5 | not stated | dimensionless | 6 | we observe peak molecularto-atomic ratios of NH2/NHi ∼ 1.5 |
| Total systematic uncertainty on [C II]-based H2 | ~±50% (adopted factor ~2) | not stated | percent | 6 | produces a total uncertainty estimate of ∼±50%. |

## Qualitative findings

- [C II] emission structure closely follows 12CO and H2 S(0), and its velocity profile matches CO rather than HI, indicating mostly molecular/PDR origin  
  > "provide strong evidence that a majority of the [C ii] emission arises from molecular gas." (3.7. Relationship between 12CO and [C ii])

## Claim tuples

- H: Most [C II] emission in the SMC regions arises from molecular gas in PDRs | E: Compared [N II], HI-based contributions, velocity profiles and morphology | R: Ionized ≲5%, atomic ≲5%, profiles match CO | F: [C II] traces CO-faint H2 | **supported**
- H: CO/[C II] ratio varies with depth into clouds | E: CO(2-1)/[C II] versus dust-derived AV | R: Ratios ~1/5-1/10 MW at low AV, reach MW value at high AV | F: Translucent molecular gas not traced by bright CO | **supported**
- H: Most molecular gas is traced by [C II] rather than CO | E: Sum [C II]-based and CO-based NH2 | R: ~70% from [C II] on average | F: Most H2 is CO-faint at low metallicity | **supported**
- H: XCO depends primarily on AV | E: XCO from total NH2 versus AV, compared with models | R: XCO decreases with AV, consistent with Wolfire 2010 and Glover & Mac Low 2011 | F: XCO primarily a function of AV | **supported**

## Reasoning

- Why this data: _not stated_
- Why this method: [O I] observations constrain density and temperature of [C II]-emitting gas, improving on earlier [C II]-based estimates  
  > "Our [O i] observations allow us to use the [O i]/[C ii] line ratios to constrain the conditions of the [C ii]-emitting gas and better estimate the amount of molecular gas." (4. ESTIMATING H2 USING [C II] AND 12CO)
- Alternative: Did not apply the Stanimirović optically thick HI correction because of small effect on H2 from [C II]  
  > "We choose not to apply the correction since it has little effect on our H2 estimate from [C ii]" (2.3. HI Data)
- How they decided it was enough: _not stated_
- Limitation (authors): XCO from 13CO is highly uncertain (LTE, abundance ratios, beam dilution)  
  > "we caution the reader that there is a large degree of uncertainty on this estimate." (3.6. Estimating XCO Using 13CO)
- Limitation (authors): AV estimate smoothed at ~40" and biased low by single dust temperature  
  > "A high dust temperature results in underestimating τ160 and AV." (3.8. 12CO-to-[C ii] Ratio)
- Caveat (inferred, ours): Dependence on unpublished Wolfire et al. cooling curves and SOFIA data
- Caveat (inferred, ours): Factor ~2 PDR-model systematic larger than quoted error budget
- Caveat (inferred, ours): ALMA ACA data have short integrations, C18O undetected
- Caveat (inferred, ours): Coarse 12-18" resolution of Herschel/AV limits pixel-wise comparison with ALMA

## Reproducibility

- Data public (paper): ALMA project codes cited in acknowledgments; archive data  
  > "This paper makes use of the following ALMA data: [[ADS/JAO.ALMA#2015.1.00581.S]]" (Acknowledgments)
- Products in archive: _not stated_
- Missing: Unpublished SMC cooling curves and PDR model grids
- Missing: Herschel HS3 reduced maps and SOFIA data not in ALMA archive
- Missing: Exact line-free channel and integration ranges
- Data volume (inferred): ~10-50 GB (ACA+TP Band 6 mosaics for 4 regions, plus ancillary maps)
- Score (inferred): 3/5, ALMA imaging recipe is mostly given, but the central H2 analysis relies on unpublished models and multi-facility data.
- Rediscovery candidate: no, Main results depend on Herschel data and unpublished PDR cooling curves, not ALMA alone.

## Links

- Method: Jameson et al. (2016) (Dust-based H2 estimates compared)
- Method: Kaufman et al. (2006) (Base PDR models)
- Method: Wolfire et al. (2010) (PDR model updates and XCO prediction)
- Companion: R. Herrera-Camus et al. 2017 (in preparation) (SOFIA GREAT [C II] spectra)
- Companion: Wolfire et al. 2017 (in preparation) (SMC [C II] cooling curves)
- Related: HS3
- Related: S4MC
- Related: HERITAGE
- Related: SMC-SAGE
- Related: KINGFISH
- Related: Dwarf Galaxy Survey

## Checks

```json
{
 "quotes": 83,
 "quotes_ok": 83,
 "quote_pass_rate": 1.0,
 "quotes_too_long": 0,
 "unsupported_facts": 0,
 "project_codes": 2,
 "codes_not_in_text": [],
 "codes_not_in_obscore": [],
 "obscore_codes_not_in_card": [],
 "codes_printed_but_missing": [],
 "numeric_results": 11,
 "numeric_problems": 0,
 "fill": {
  "facts": 89,
  "stated": 60,
  "rate": 0.674
 },
 "evidence_ok": true
}
```
