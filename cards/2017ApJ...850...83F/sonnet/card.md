# Demonstrating a New Census of Infrared Galaxies with ALMA (DANCING-ALMA). I. FIR Size and Luminosity Relation at z = 0-6 Revealed with 1034 ALMA Sources

`2017ApJ...850...83F` | The Astrophysical Journal 2017 | first author: Fujimoto, Seiji | arXiv: 1703.02138 | DOI: 10.3847/1538-4357/aa93e6

Card schema 1.0 | model claude-sonnet-5-5 | depth full | type archival_reuse

## Science

- Fields: high_z_galaxies
- Question: What is the relation between rest-frame FIR effective radius and FIR luminosity of ALMA-detected dusty galaxies at z=0-6, and how does it evolve with redshift and compare with UV/optical sizes?  
  > "We analyze this large dataset to investigate the $R_{\rm e(FIR)}-L_{\rm FIR}$ relation and the $R_{\rm e(FIR)}$ evolution by a systematic $uv$-visibility based technique." (Introduction)
- Target **1034 ALMA continuum sources in HUDF, HFF, COSMOS, SXDS, GOODS-S archival maps**: coordinates _not stated_; z/distance photometric redshifts z=0-6; median z_med=2.36  
  > "We collect 1627 continuum maps in Band 6/7 from the ALMA archival data in the regions of HUDF, HFF, Cosmic Evolution Survey (COSMOS; (cite: scoville2007))" (2.1 Data); distance from photometric redshifts from optical-NIR catalogs  
  > "We collect 1627 continuum maps in Band 6/7 from the ALMA archival data in the regions of HUDF, HFF, Cosmic Evolution Survey (COSMOS; (cite: scoville2007))" (2.1 Data)

## Data provenance

- ALMA projects: 2011.1.00097.S, 2013.1.00999.S, 2015.1.00664.S
- bands: Band 6/7 continuum, cycles 0-3  
  > "We collect 1627 continuum maps in Band 6/7 from the ALMA archival data" (2.1 Data)
- frequencies and spectral setup: _not stated_
- continuum bandwidth: _not stated_
- arrays: _not stated_
- configurations: _not stated_
- baselines: _not stated_
- angular resolution: 0.18''x0.18'' to 4.08''x1.07''  
  > "achieve angular resolutions of $0.18\ensuremath{''}\times 0.18\ensuremath{''}$$-$$4.08\ensuremath{''}\times1.07\ensuremath{''}$" (2.2 Data Reduction)
- max recoverable scale: _not stated_
- sensitivity: 0.01-1.4 mJy/beam before primary beam correction  
  > "the sensitivities of 0.01$-$1.4 mJy beam$^{-1}$ before the primary beam corrections" (2.2 Data Reduction)
- time on source: _not stated_
- observing dates: _not stated_
- pi or archival as stated: ALMA archive data public by 2017 July  
  > "1627 Atacama Large Millimeter/submillimeter Array (ALMA) 1-mm band maps that become public by 2017 July" (abstract)
- Other facility **HST (3D-HST and other optical-NIR catalogs)**: Optical-NIR counterparts, photometric redshifts, stellar masses, UV/optical sizes and morphology  
  > "We search the optical-NIR counterparts for the ALL5S and the ALL10S sources." (3.6 Optical and NIR Counterpart)
- External data: Optical-NIR catalogs (photometry, photz, Mstar) for SXDS, GOODS-S, HUDF, COSMOS, HFF  
  > "| GOODS-S Wide | (cite: santini2015) | $H<27.4$ $(0.17\ensuremath{''})$ |" (Table 3) [from santini2015; ilbert2013; momcheva2016; castellano2016]
- External data: Lensing magnification factors for HFF sources  
  > "magnification factors that are obtained from (cite: castellano2016)" (3.6 Optical and NIR Counterpart) [from castellano2016]
- External data: HST/ALMA astrometric offset correction in GOODS-S (-80 mas, +260 mas)  
  > "we apply the corrections of $\Delta\alpha$ = $-80$ mas and $\Delta\delta$ = $+260$ mas (cite: rujopakarn2016)" (3.6 Optical and NIR Counterpart) [from rujopakarn2016]
- External data: HST rest-frame UV/optical sizes for comparison  
  > "We cross-match the OC10S sources with the 3D-HST sources whose $R_{\rm e}$ values are measured with the HST/$J$- and $H$-bands in (cite: vanderwel2012)." (5.2) [from vanderwel2012; shibuya2015]

## Processing

### Calibration

- pipeline or manual: Scripts provided by the ALMA observatory (flagging, bandpass, gain/flux); extra flagging where needed  
  > "These major steps are performed with the scripts provided by the ALMA observatory." (2.2 Data Reduction)
- casa version: CASA 4.2.0 to 4.7.2  
  > "we use the CASA versions from 4.2.0 to 4.7.2." (2.2 Data Reduction)
- pipeline version: _not stated_
- archive products used as is: _not stated_
- flux calibrator: _not stated_
- flux scale uncertainty: _not stated_
- self calibration: _not stated_

### Imaging

- task: CLEAN with boxit-defined boxes, 4 iterations  
  > "We repeat 1)-3) for four times, changing from the 50$\sigma_{\rm d}$ level to the 20$\sigma_{\rm d}$, 10$\sigma_{\rm d}$, and 5$\sigma_{\rm d}$ levels in the step 1)." (2.2 Data Reduction)
- deconvolver: _not stated_
- weighting robust: natural weighting  
  > "performing the CLEAN algorithm down to the depth of the 3$\sigma_{\rm d}$ level with the natural weighting in the CLEAN boxes." (2.2 Data Reduction)
- uv taper: _not stated_
- cell size: _not stated_
- image size: _not stated_
- masking: CLEAN boxes around peaks >=50,20,10,5 sigma_d  
  > "making CLEAN boxes with the boxit task for the peak pixels given in the step 1)" (2.2 Data Reduction)
- multiscale scales: _not stated_
- continuum subtraction: _not stated_
- line free channels: _not stated_
- primary beam correction: _not stated_
- array combination: HUDF projects combined with concat; weights recomputed with statwt  
  > "we combine these two data sets with the concat task." (2.2 Data Reduction)
- smoothing: _not stated_
- final beam: _not stated_
- final rms: _not stated_

### Inherited from earlier work

- Data reduction done in the same manner as earlier work  
  > "Basically, the data is reduced in the same manner as (cite: fujimoto2016)" (2.2 Data Reduction) [from (cite: fujimoto2016)]
- Beta=1.8 for modified blackbody  
  > "we assume $\beta=1.8$ (cite: chapin2009)" (3.6 Optical and NIR Counterpart) [from (cite: chapin2009)]

### Not stated but needed to reproduce (our reading)

- Which exact archival projects/maps entered the sample (full 1627-map table is only online)
- Cell size and image size for CLEAN
- Line-free channel ranges and how line channels were identified in the three line projects
- uvmultifit initial-value and fit settings details
- Perturbation-method and power-law fit algorithm details (fit method, priors)
- Completeness threshold values per sub-dataset
- Photometric-redshift catalogs per source and flux-scale uncertainties
- Binning details for Td-L_FIR relation fit

## Analysis recipe

1. **Reduce archival ALMA data and make continuum maps**: Archive calibration scripts, extra flagging, CLEAN with boxes, natural weighting  
  > "We perform Fourier transformations for the reduced $uv$-data to create "dirty" continuum maps." (2.2 Data Reduction)
   - software: CASA
   - parameter: CLEAN to 3 sigma_d in boxes around >=50,20,10,5 sigma_d peaks  
  > "performing the CLEAN algorithm down to the depth of the 3$\sigma_{\rm d}$ level with the natural weighting in the CLEAN boxes." (2.2 Data Reduction)
   - assumption: [CII] contamination by chance negligible (~1-2% of sources, <=10% of continuum)  
  > "Therefore, we assume that the second case is negligible in our statistical results" (2.2 Data Reduction)
   - fitting: _not stated_
   - validation: _not stated_
2. **Extract sources**: SExtractor on maps before PB correction; peak >=5 sigma_f in regions with >50% sensitivity; imfit total flux >=10 sigma_f for ALL10S  
  > "We then select only the sources with $S^{\rm peak}_{\rm obs}\geq5\sigma_{\rm f}$ to make a 5$\sigma$-peak catalog." (3.1 Source Detection)
   - software: SExtractor, CASA imfit
   - fitting: 2D Gaussian in image plane (imfit)  
  > "The total flux densities are measured with the imfit task in CASA that carries out the fitting routine with the 2D Gaussian model on the image plane." (3.1 Source Detection)
   - validation: _not stated_
3. **Measure flux and size in uv plane**: uvmultifit with symmetric exponential disk (n=1), positions fixed, imfit values as initial guesses; Re=0.826 FWHM; visual flagging  
  > "The fitting result of the FWHM values are converted to the $R_{\rm e}$ values via the relation of $R_{\rm e}=0.826\,{\rm FWHM}$ in the case of $n=1$" (3.2 Flux and Size Measurement)
   - software: uvmultifit
   - assumption: Sersic n=1 exponential disk  
  > "Here we adopt a symmetric exponential disk model." (3.2 Flux and Size Measurement)
   - fitting: uv-visibility fitting; flag=0 reliable results only  
  > "We use only the results with flag = 0 in the following analyses in this paper." (3.2 Flux and Size Measurement)
   - validation: Compared with previous ALMA flux/size measurements  
  > "Our size measurements are also consistent with the majority of the previous ALMA results within the $\sim$ 1$-$2 $\sigma$ errors" (3.4)
4. **Correct biases with Monte-Carlo simulations**: Inject 26,600 artificial sources into uv data of 10 representative maps; fit linear input-output relations in 3 SNR bins  
  > "we create $26,600$ artificial sources with the uniform distribution of the total fluxes in the $5\sigma_{\rm f}-45\sigma_{\rm f}$ levels" (3.3 Simulation and Correction)
   - software: uvmultifit
   - parameter: sizes 0.04''-3.0''; random positions within 10'' radius; SNR bins 5-10, 10-20, 20-30  
  > "we divide our simulation results into three bins with the output peak signal to noise ratio (SNR) of 5$-$10, 10$-$20, and 20$-$30." (3.3 Simulation and Correction)
   - fitting: S_in = A0 S_out + A1; Re_in = B0 Re_out + B1  
  > "$A_{0}, A_{1}, 
 B_{0},$ and $B_{1}$ are the free parameters." (3.3 Simulation and Correction)
   - validation: Selection completeness and measurement completeness maps; completeness thresholds  
  > "we define the completeness threshold in each sub-dataset." (3.5)
5. **Identify counterparts and derive L_FIR, SFR, Mstar**: Nearest optical-NIR source within 1.0'' ; L_FIR from modified blackbody; SFR from Murphy+11  
  > "we define the optical-NIR counterparts as the optical-NIR sources that locate within a search radius of $1\ensuremath{''}$0 from our ALMA source centers." (3.6)
   - parameter: beta=1.8, Td=35 K, CMB effect included  
  > "we assume $\beta=1.8$ (cite: chapin2009) and $T_{\rm d}=35$ K (cite: kovacs2006; coppin2008)" (3.6)
   - assumption: Chabrier IMF; flat cosmology Om=0.3, OL=0.7, H0=70  
  > "In this paper, we assume the (cite: chabrier2003) initial mass function (IMF)." (3.7)
   - fitting: _not stated_
   - validation: Td-L_FIR relation test showed results consistent within 1 sigma  
  > "We thus conclude that our assumption of $T_{\rm d}=35$ K does not produce the significant systematics" (4.2)
6. **Fit Re(FIR)-L_FIR relation and redshift evolution**: Power law R_e=R0 (L/L0)^alpha above completeness thresholds; Spearman test; errors by 1000 Gaussian perturbations; alpha fixed to fit R0 per redshift bin  
  > "We generate 1000 data sets of the $R_{\rm e (FIR)}$ and $L_{\rm FIR}$ for the ALL10S and OC10S sources based on the random perturbations" (4.2)
   - parameter: redshift bins 0-1, 1-2, 2-4, 4-6; L0 = Schechter L* at z~3  
  > "We select the $L_{0}$ value to the best-fit Schechter parameter $L_{*}$ at $z\sim3$." (4.2)
   - fitting: Power-law fit with perturbation method (Curran 2014) for 1 sigma errors  
  > "We estimate the 1$\sigma$-error range of the power-law function by the perturbation method (cite: curran2014)." (4.2)
   - validation: Tested without AGNs, potential lensed sources, cycle 0/1 data; no completeness threshold; Band 6 vs 7 for CMB effect  
  > "We thus conclude that the $R_{\rm e(FIR)}-L_{\rm FIR}$ relation is unchanged by the contaminations of the AGNs, the lensed sources, and the early ALMA cycles." (4.2)
7. **Compare with UV/optical sizes and classify mergers**: Compare with Shibuya+15 and van der Wel+12 sizes; major merger pair selection within 2.5'' with dz<1 and Mstar>10%; CNN morphology catalog  
  > "i) selecting the optical-NIR objects that are located within an offset of $2.5\ensuremath{''}$ from the OC5S-mmT source centers" (5.5)
   - fitting: _not stated_
   - validation: KS tests; extended 6'' radius check  
  > "We identify no additional OS5S-mmT sources that have the major merger pairs with an extended radius of 6$''$" (5.5)

## Software

- **CASA** 4.2.0 to 4.7.2: Reduction, CLEAN, imfit, concat, statwt, boxit  
  > "we use the CASA versions from 4.2.0 to 4.7.2." (2.2 Data Reduction)
- **SExtractor** 2.5.0: Source extraction  
  > "with sextractor version 2.5.0 (cite: bertin1996)" (3.1 Source Detection)
- **uvmultifit** : uv-visibility flux and size fitting  
  > "We perform uvmultifit ((cite: marti2014)) that is a simultaneous fitting tool for multiple objects on $uv$-visibility." (3.2 Flux and Size Measurement)

## Numeric results

| quantity | value | uncertainty | units | step | quote |
|---|---|---|---|---|---|
| Number of sources in ALL5S | 1034 | not stated | sources | 2 | We obtain 1034 sources in the 5$\sigma$-peak catalog. |
| Number of sources in ALL10S | 780 | not stated | sources | 2 | we select 780 sources with total flux densities |
| Median redshift (OC5S-mmT) | 2.36 | not stated | dimensionless | 5 | The median redshift is estimated to be $z_{\rm med}=2.36$ |
| alpha (all redshifts) in Re(FIR) ∝ L_FIR^alpha | 0.28 | 0.07 | dimensionless | 6 | the $\alpha^{\rm FIR}$ value is estimated to be 0.28 $\pm$ 0.07 |
| alpha at z=2-4 | 0.23 | 0.07 | dimensionless | 6 | We obtain $\alpha^{\rm FIR} = 0.23\,\pm\,0.07$. |
| Starburst fraction, all redshifts | ~52 | not stated | percent | 5 | With the redshift bins all together, the starburst fraction is $\sim$52%. |
| Major merger fraction (early/mid-stage) in OC5S-mmT | 27 (15/56) | not stated | percent | 7 | We find that 27% ($=$15/56) of the OC5S-mmT sources have the major merger pairs. |
| Median ALMA-HST offset | 0.24 | not stated | arcsec | 5 | the median value of the individual scatters is estimated to be $0.24\ensuremath{''}$ |

## Qualitative findings

- Re(FIR) at fixed L_FIR decreases toward high redshift, like UV/optical sizes  
  > "shows that $R_{\rm e(FIR)}$ at a fixed $L_{\rm FIR}$ decreases toward high redshifts" (abstract)
- Re(FIR) generally smaller than Re(UV) and Re(Opt.)  
  > "we conclude that the $R_{\rm e(FIR)}$ values are generally smaller than the $R_{\rm e(UV)}$ and $R_{\rm e(Opt.)}$ values" (5.2)

## Claim tuples

- H: Re(FIR) correlates with L_FIR across z=0-6 | E: uv-plane size measurement of ALMA archival sources with completeness corrections; power-law fit | R: alpha=0.28±0.07, >99% significance | F: Positive size-luminosity relation with slope similar to UV | **supported**
- H: Dusty starbursts are more compact than their UV/optical extent | E: Compare Re(FIR) with Re(UV/Opt.) statistically and for 53 individual sources | R: Re(FIR) <~ Re(UV), Re(Opt.) | F: Dusty starbursts occur in compact regions | **supported**
- H: Dusty starbursts are triggered only by major mergers | E: Pair-based and CNN morphology classification of HST images | R: ~30-40% classified as major mergers | F: Other mechanisms also trigger dusty starbursts | **supported**

## Reasoning

- Why this data: Archive sample gives large statistics and homogeneous analysis across redshift  
  > "A homogeneous measurement based on a large dataset is required to compare the different redshift samples and determine the $R_{\rm e(FIR)}$ evolution." (Introduction)
- Why this method: _not stated_
- Alternative: Td-L_FIR relation instead of fixed Td=35 K; rejected since results consistent  
  > "we adopt the $L_{\rm FIR}$ values estimated by $T_{\rm d}=35$ K in the following analyses." (4.2)
- How they decided it was enough: _not stated_
- Limitation (authors): Sample not complete at fixed stellar mass  
  > "our ALMA sources are not the complete sample at a fixed $M_{\rm star}$." (3.7)
- Limitation (authors): Size measurement unreliable for compact/faint sources in low-resolution maps  
  > "We cannot obtain the reliable size measurements for the compact and/or faint sources in the low-resolution observations." (3.5)
- Caveat (inferred, ours): Single dust temperature and photometric redshifts bias L_FIR
- Caveat (inferred, ours): Heterogeneous target selection in archival programs
- Caveat (inferred, ours): Exponential-disk assumption and Gaussian-based completeness
- Caveat (inferred, ours): Low-resolution maps may bias sizes

## Reproducibility

- Data public (paper): Public ALMA archive data  
  > "1627 Atacama Large Millimeter/submillimeter Array (ALMA) 1-mm band maps that become public by 2017 July" (abstract)
- Products in archive: _not stated_
- Missing: Imaging cell/image sizes
- Missing: Completeness threshold values
- Missing: Photometric catalogs matching per source
- Missing: Line-channel masks
- Data volume (inferred): Multi-TB (~30 ALMA projects, 1627 maps)
- Score (inferred): 3/5, Public data and a clear recipe, but heavy volume and many unstated parameters; results are numeric.
- Rediscovery candidate: no, Very large data volume and incomplete imaging and selection details make full reproduction impractical.

## Links

- Method: (cite: fujimoto2016) (Data reduction approach)
- Method: (cite: marti2014) (uvmultifit tool)
- Related: 3D-HST
- Related: ALESS
- Related: HUDF
- Related: Hubble Frontier Fields
- Related: COSMOS

## Checks

```json
{
 "quotes": 68,
 "quotes_ok": 68,
 "quote_pass_rate": 1.0,
 "quotes_too_long": 0,
 "unsupported_facts": 0,
 "project_codes": 3,
 "codes_not_in_text": [],
 "codes_not_in_obscore": [
  "2011.1.00097.S"
 ],
 "obscore_codes_not_in_card": [
  "2011.0.00097.S",
  "2011.0.00294.S",
  "2012.1.00076.S",
  "2012.1.00090.S",
  "2012.1.00173.S",
  "2012.1.00245.S",
  "2012.1.00307.S",
  "2012.1.00326.S",
  "2012.1.00523.S",
  "2012.1.00756.S",
  "2012.1.00775.S",
  "2012.1.00869.S",
  "2012.1.00979.S",
  "2012.1.00983.S",
  "2013.1.00034.S",
  "2013.1.00118.S",
  "2013.1.00151.S",
  "2013.1.00205.S",
  "2013.1.00208.S",
  "2013.1.00566.S",
  "2013.1.00668.S",
  "2013.1.00718.S",
  "2013.1.00781.S",
  "2013.1.00884.S",
  "2013.1.01292.S",
  "2015.1.00039.S",
  "2015.1.00137.S",
  "2015.1.00540.S",
  "2015.1.01495.S"
 ],
 "codes_printed_but_missing": [
  "2011.0.00097.S",
  "2011.0.00294.S",
  "2012.1.00076.S",
  "2012.1.00090.S",
  "2012.1.00173.S",
  "2012.1.00245.S",
  "2012.1.00307.S",
  "2012.1.00326.S",
  "2012.1.00523.S",
  "2012.1.00756.S",
  "2012.1.00775.S",
  "2012.1.00869.S",
  "2012.1.00979.S",
  "2012.1.00983.S",
  "2013.1.00034.S",
  "2013.1.00118.S",
  "2013.1.00151.S",
  "2013.1.00173.S",
  "2013.1.00205.S",
  "2013.1.00208.S",
  "2013.1.00566.S",
  "2013.1.00668.S",
  "2013.1.00718.S",
  "2013.1.00781.S",
  "2013.1.00884.S",
  "2013.1.01292.S",
  "2015.1.00039.S",
  "2015.1.00137.S",
  "2015.1.00540.S",
  "2015.1.01495.S"
 ],
 "numeric_results": 8,
 "numeric_problems": 0,
 "fill": {
  "facts": 86,
  "stated": 53,
  "rate": 0.616
 },
 "evidence_ok": true
}
```
