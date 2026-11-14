# The Core Mass Function across Galactic Environments. III. Massive Protoclusters

`2021ApJ...916...45O` | The Astrophysical Journal 2021 | first author: O'Neill, Theo J. | arXiv: 2104.08861 | DOI: 10.3847/1538-4357/ac062d | **HELD OUT (benchmark)**

Card schema 1.0 | model claude-opus-5-5 | depth full | type large_program_or_survey

## Science

- Fields: star_formation, milky_way_ism
- Question: What is the core mass function (CMF) in the central regions of massive protoclusters (shape, power-law index, presence of a break), and does it differ from the CMF in the G286 protocluster and IRDC clumps measured with the same methods?  
  > "Here we measure the CMF in 28 dense clumps within 3.5 kpc that are likely to be central regions of massive protoclusters, observed via $1.3\:{\rm{mm}}$ dust continuum emission by the ALMAGAL project." (abstract); "We compare this massive protocluster CMF with those derived using the same methods in the G286 protocluster and a sample of Infrared Dark Clouds." (abstract)
- Target **28 ALMAGAL massive clumps (Hi-GAL sources, G18.30 to G346.35; listed in Table 1)**: coordinates Galactic l, b per clump given in Table 1  
  > "we limited our analysis to sources within 3.5 kpc that had 12m-array observations delivered to the" (Source Selection); "a $10\%$ error in the Hi-GAL distance estimate to a particular clump would yield a $20\%$ error in mass" (Core Mass Estimation); "Clumps distances ranged between 0.79 kpc and 3.5 kpc." (Effects of Dendrogram Parameters, Binning Scheme, and Clump Distance); z/distance within 3.5 kpc (per-clump d in Table 1)  
  > "we limited our analysis to sources within 3.5 kpc that had 12m-array observations delivered to the" (Source Selection); "a $10\%$ error in the Hi-GAL distance estimate to a particular clump would yield a $20\%$ error in mass" (Core Mass Estimation); "Clumps distances ranged between 0.79 kpc and 3.5 kpc." (Effects of Dendrogram Parameters, Binning Scheme, and Clump Distance); distance from Hi-GAL (cite: elia_hi-gal_2017)  
  > "we limited our analysis to sources within 3.5 kpc that had 12m-array observations delivered to the" (Source Selection); "a $10\%$ error in the Hi-GAL distance estimate to a particular clump would yield a $20\%$ error in mass" (Core Mass Estimation); "Clumps distances ranged between 0.79 kpc and 3.5 kpc." (Effects of Dendrogram Parameters, Binning Scheme, and Clump Distance)

## Data provenance

- ALMA projects: 2019.1.00195.L
- bands: 1.3 mm dust continuum (ALMAGAL designed for continuum and line emission near 1.4 mm)  
  > "observed via $1.3\:{\rm{mm}}$ dust continuum emission by the ALMAGAL project" (abstract); "ALMAGAL was designed to observe continuum and line emission near $1.4\:$mm from $\gtrsim$1000 high-mass Galactic clumps" (Source Selection)
- frequencies and spectral setup: _not stated_
- continuum bandwidth: _not stated_
- arrays: ALMA 12m array  
  > "we limited our analysis to sources within 3.5 kpc that had 12m-array observations delivered to the" (Source Selection)
- configurations: _not stated_
- baselines: _not stated_
- angular resolution: _not stated_
- max recoverable scale: _not stated_
- sensitivity: median 1σ RMS 0.30 mJy/beam; per-clump RMS 0.13-1.38 mJy/beam (Table 1)  
  > "The median value of $\sigma$ was 0.30 mJy $\textrm{beam}^{-1}$." (Core Identification)
- time on source: _not stated_
- observing dates: _not stated_
- pi or archival as stated: ALMAGAL Cycle 7 project (PI: S. Molinari); data delivered to the ALMA archive by May 2020  
  > "We selected sources from the ALMA Cycle 7 project “ALMAGAL: ALMA Evolutionary Study of High Mass Protocluster Formation in the Galaxy” (PI: S. Molinari)." (Source Selection)
- Other facility **Herschel Hi-GAL survey**: Parent clump catalog: clump identification, distances, radii, masses, mass surface densities and evolutionary types  
  > "high-mass Galactic clumps ($d<$ 7.5 kpc and $M_{\rm cl}> 500\:M_{\odot}$) identified by the *Herschel* Hi-GAL survey (cite: elia_hi-gal_2017)." (Source Selection)
- External data: Clump radius, mass, Σ_cl, evolutionary type (and Hi-GAL distances) for the 28 clumps  
  > "The radius, mass, $\Sigma_{\rm cl}$, and type were derived by (cite: elia_hi-gal_2017)" (Table 1) [from (cite: elia_hi-gal_2017)]
- External data: Dust opacity κ_1.3mm,d = 0.899 cm^2 g^-1 from moderately coagulated thin ice mantle model  
  > "(i.e., the value from the moderately coagulated thin ice mantle model of (cite: ossenkopf_dust_1994))" (Core Mass Estimation) [from (cite: ossenkopf_dust_1994)]
- External data: Gas-to-refractory-dust ratio of 141  
  > "using a gas-to-refractory-component-dust ratio of 141 (cite: draine_physics_2011)" (Core Mass Estimation) [from (cite: draine_physics_2011)]
- External data: True CMFs of G286 protocluster (Paper I) and IRDC clumps (Paper II) for comparison  
  > "Figure [10](#fig:Comp_cmfs) compares the “true” CMFs that we have derived for the massive protocluster sample to those derived in Paper I for the G286 protocluster and Paper II for the IRDC clumps." (Comparison of CMFs in Different Environments and Implications for Massive Star Formation) [from Paper I (cite: cheng_core_2018); Paper II (cite: liu_core_2018)]
- External data: Flux and number recovery correction factors from core insertion experiments of Papers I and II  
  > "In Papers I and II, we derived correction factors to estimate a complete, i.e., “true”, CMF from an observed “raw” CMF." (Core Flux Recovery and Completeness Corrections) [from Paper I (cite: cheng_core_2018); Paper II (cite: liu_core_2018)]
- External data: Σ_cl of IRDC clumps (≲0.4 g cm^-2) and G286 (~0.1 g cm^-2) for environment comparison  
  > "while the IRDC clumps usually have $\Sigma_{\rm cl}\lesssim 0.4\:{\rm g\:cm}^{-2}$ (cite: butler_mid-infrared_2012)" (Comparison of CMFs in Different Environments and Implications for Massive Star Formation); "G286 is estimated to have $\Sigma_{\rm cl}\sim 0.1\:{\rm g\:cm}^{-2}$ (cite: cheng_gas_2020)" (Comparison of CMFs in Different Environments and Implications for Massive Star Formation) [from (cite: butler_mid-infrared_2012); (cite: cheng_gas_2020)]
- Simulation/model as data: Artificial cores inserted into real clump images to derive flux and number recovery fractions  
  > "Artificial cores of varying masses were randomly inserted into real clump images to estimate the amount of the flux typically detected by the dendrogram algorithm as a function of inserted mass." (Core Flux Recovery and Completeness Corrections)

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
- cell size: _not stated_
- image size: _not stated_
- masking: _not stated_
- multiscale scales: _not stated_
- continuum subtraction: _not stated_
- line free channels: _not stated_
- primary beam correction: Cores identified in images not corrected for the primary beam (following Paper II)  
  > "we diverge from Paper I’s methods and follow those used in Paper II by identifying cores in images that have not been corrected for the primary beam." (Core Identification)
- array combination: _not stated_
- smoothing: _not stated_
- final beam: _not stated_
- final rms: median 0.30 mJy/beam (estimated from 50 random beam-sized areas in pre-PB-corrected images)  
  > "The median value of $\sigma$ was 0.30 mJy $\textrm{beam}^{-1}$." (Core Identification)

### Inherited from earlier work

- Core identification method and dendrogram parameters (F_min=4σ, δ=1σ, S_min=0.5 beam)  
  > "To identify cores, we followed the methods used in our studies of the G286 protocluster (Paper I) and IRDCs (Paper II), thus allowing a direct comparison of the derived CMFs." (Core Identification); "These parameter choices are the same as used in Papers I and II" (Core Identification) [from Paper I (cite: cheng_core_2018); Paper II (cite: liu_core_2018)]
- Use of non-primary-beam-corrected images for core identification  
  > "we diverge from Paper I’s methods and follow those used in Paper II by identifying cores in images that have not been corrected for the primary beam." (Core Identification) [from Paper II (cite: liu_core_2018)]
- Mass estimation assuming optically thin dust emission  
  > "We estimated masses of cores by assuming optically thin thermal emission from dust, as in Papers I and II." (Core Mass Estimation) [from Papers I and II]
- Flux and number recovery correction factors (median of curves vs. normalized flux)  
  > "In Papers I and II, we derived correction factors to estimate a complete, i.e., “true”, CMF from an observed “raw” CMF." (Core Flux Recovery and Completeness Corrections); "We adopted the median values of these factors as universal values with which to correct our observed “raw” CMFs from our entire clump sample." (Core Flux Recovery and Completeness Corrections) [from Papers I and II]
- Mass binning (five bins per dex, bin centered on 1 Msun)  
  > "Masses were binned using the same methods as Papers I and II, with all bins equal in size in $\Delta \rm{log_{10}}M$ with five bins per dex, and a bin centered on 1 $M_{\odot}$." (Construction of the CMF) [from Papers I and II]
- Fiducial WLS power-law fitting and empty-bin upper-limit treatment  
  > "First, we follow the fiducial weighted least squares (WLS) method of Papers I and II, which involves minimizing differences in the log of $d N / d {\rm log} M$, normalized using the average of the asymmetric Poisson errors." (Single Power-Law Fits to the CMF); "For the one empty bin at the high-mass end, we again follow Papers I and II and treat it as an effective upper limit" (Single Power-Law Fits to the CMF) [from Papers I and II]
- Unbinned MLE power-law fitting, KS-distance M_min selection and semi-parametric bootstrap p-values  
  > "Next, we generated a synthetic CMF through a two-part, semi-parametric method based on the procedure proposed by (cite: clauset_power-law_2009)." (Single Power-Law Fits to the CMF) [from (cite: clauset_power-law_2009)]
- Binned MLE (MLE-B) likelihood  
  > "This method is based on that proposed by (cite: virkar_power-law_2014)" (Single Power-Law Fits to the CMF) [from (cite: virkar_power-law_2014)]

### Not stated but needed to reproduce (our reading)

- Imaging parameters of the continuum images (task, weighting/robust, cell size, image size, masking, continuum channel selection) and whether ALMA pipeline or custom images were used
- Synthesized beam sizes per clump (needed for S_min and beam-area integration)
- Calibration details (pipeline/CASA version, flux calibrator, self-calibration)
- Exact central frequency/bandwidth of the continuum used for flux-to-mass conversion (λ_1.3 factor)
- Tabulated f_flux and f_num correction curves as a function of normalized flux (only shown in Fig. 2)
- Whether new core-insertion experiments were run on the ALMAGAL images or only Paper I/II curves reused
- Exact bin edges and core counts per bin for the CMFs
- Details of synthetic core profiles used in insertion experiments
- Implementation details of non-linear WLS PPL fits (initial values, break-mass grid)
- Random seeds / code for bootstrap (3000 realizations) and LOWESS smoothing

## Analysis recipe

1. **select clump sample**: ALMAGAL clumps within 3.5 kpc with 12m-array data delivered by May 2020  
  > "we limited our analysis to sources within 3.5 kpc that had 12m-array observations delivered to the" (Source Selection)
   - parameter: d < 3.5 kpc; 28 sources  
  > "This yields a sample of 28 sources" (Source Selection)
   - assumption: Sample considered representative of central regions of massive protoclusters  
  > "We thus consider that this clump sample is representative of conditions near the centers of massive protoclusters." (Source Selection)
   - fitting: _not stated_
   - validation: _not stated_
2. **estimate image noise**: Mean σ in 50 randomly-placed beam-sized areas of pre-PB-corrected images with max intensity <3.5 mJy/beam  
  > "We estimated the 1$\sigma$ root mean square (RMS) noise within each pointing by finding the mean value of $\sigma$ in 50 randomly-placed synthesized-beam-sized-areas of the pre-primary-beam corrected continuum images" (Core Identification)
   - parameter: 50 areas; max intensity < 3.5 mJy/beam  
  > "with a maximum intensity less than 3.5 mJy $\textrm{beam}^{-1}$" (Core Identification)
   - fitting: _not stated_
   - validation: _not stated_
3. **identify cores**: Dendrogram (astrodendro); cores = leaves  
  > "We used the dendrogram algorithm (cite: rosolowsky_structural_2008) as implemented in the python package `astrodendro` to identify cores." (Core Identification); "We defined cores as the leaves of the dendrogram." (Core Identification)
   - software: astrodendro
   - parameter: F_min = 4σ  
  > "We required parent structures (trunks) in the dendrogram to have a minimum intensity $F_{\rm min}$ of $4\sigma$." (Core Identification)
   - parameter: δ = 1σ; S_min = 0.5 synthesized beam  
  > "We also required substructures (*branches* and *leaves*) to have a minimum increase in intensity $\delta$ of $1\sigma$ and a minimum area $S_{\rm{min}}$ of half the synthesized beam to be considered independent entities." (Core Identification)
   - fitting: _not stated_
   - validation: Varied F_min (3,4,5σ) and S_min (0.5, 1 beam)  
  > "We kept $\delta$ constant and tested combinations of $F_{\rm{min}}=$ 3, 4, or 5 $\sigma$ and $S_{\rm{min}}=0.5$ beam or 1 beam." (Effects of Dendrogram Parameters, Binning Scheme, and Clump Distance)
4. **derive core masses**: Optically thin dust emission; M = 0.192 (F_ν/mJy)(d/2.5 kpc)^2 Msun for fiducial values  
  > "We estimated masses of cores by assuming optically thin thermal emission from dust, as in Papers I and II." (Core Mass Estimation)
   - assumption: T_d = 20 K  
  > "In the absence of measurements of temperature for each source, we assumed dust temperatures $T_{d} =$ 20 K." (Core Mass Estimation)
   - assumption: κ_1.3mm,d = 0.899 cm^2/g (Ossenkopf & Henning 1994); gas-to-refractory-dust ratio 141  
  > "(i.e., the value from the moderately coagulated thin ice mantle model of (cite: ossenkopf_dust_1994))" (Core Mass Estimation); "using a gas-to-refractory-component-dust ratio of 141 (cite: draine_physics_2011)" (Core Mass Estimation)
   - assumption: Hi-GAL clump distances  
  > "a $10\%$ error in the Hi-GAL distance estimate to a particular clump would yield a $20\%$ error in mass" (Core Mass Estimation)
   - fitting: _not stated_
   - validation: Temperature sensitivity: 15 K or 30 K changes masses by factors 1.48 and 0.604  
  > "If temperatures of 15 K or 30 K were to be adopted, the mass estimates would differ by factors of 1.48 and 0.604, respectively." (Core Mass Estimation)
5. **apply flux and number completeness corrections**: Median f_flux and f_num curves (from artificial core insertion) as function of flux normalized by local σ  
  > "Artificial cores of varying masses were randomly inserted into real clump images to estimate the amount of the flux typically detected by the dendrogram algorithm as a function of inserted mass." (Core Flux Recovery and Completeness Corrections); "We adopted the median values of these factors as universal values with which to correct our observed “raw” CMFs from our entire clump sample." (Core Flux Recovery and Completeness Corrections)
   - assumption: Correction factors are universal as a function of normalized flux  
  > "This similarity in functional form suggests that these factors may be applicable to a variety of Galactic clump source morphologies" (Core Flux Recovery and Completeness Corrections)
   - fitting: _not stated_
   - validation: _not stated_
6. **construct raw, flux-corrected and true CMFs**: Per-clump CMFs combined; log bins, five per dex, centered on 1 Msun; Poisson errors  
  > "Masses were binned using the same methods as Papers I and II, with all bins equal in size in $\Delta \rm{log_{10}}M$ with five bins per dex, and a bin centered on 1 $M_{\odot}$." (Construction of the CMF); "We assumed $\textit{N}^{1/2}$ Poisson counting uncertainties for each bin." (Construction of the CMF)
   - fitting: _not stated_
   - validation: _not stated_
7. **single power-law fits over standard range**: WLS (binned), MLE (unbinned) and MLE-B (binned) fits with M_min = 0.79 Msun  
  > "We also use a second MLE method (MLE-B) to fit to binned data, i.e., fitting power-laws directly to the histograms of the raw, flux-corrected, and true CMFs." (Single Power-Law Fits to the CMF)
   - parameter: M_min = 0.79 Msun  
  > "We first adopt $M_{\rm{min}}$ $=0.79$ $M_{\odot}$ (corresponding to the bin centered at $1\:M_{\odot}$)." (Single Power-Law Fits to the CMF)
   - fitting: MLE α = n[Σ ln(M_i/M_min)]^-1 with Δα = α/√n; MLE-B log-likelihood of Virkar & Clauset  
  > "The standard error on $\alpha$ is $\Delta\alpha = \alpha / \sqrt{n}$." (Single Power-Law Fits to the CMF)
   - validation: _not stated_
8. **find optimal M_min and goodness of fit**: Minimize KS distance D and Anderson-Darling A^2 vs M_min; bootstrap p-values with semi-parametric synthetic CMFs  
  > "Next, we generated a synthetic CMF through a two-part, semi-parametric method based on the procedure proposed by (cite: clauset_power-law_2009)." (Single Power-Law Fits to the CMF); "we report final “best” fits that begin at the lowest significant ($p \geq .10$) $M_{\rm min}$ value as assessed by $A^2$." (Single Power-Law Fits to the CMF)
   - parameter: N = 3000 synthetic CMFs per M_min  
  > "We then repeated this procedure $N=3000$ times, i.e., with 3000 different synthetic CMFs for each $M_{\rm min}$" (Single Power-Law Fits to the CMF)
   - parameter: 100 M_min values in 0.1-10 Msun (raw, flux-corrected); 11 bins for true CMF  
  > "For the raw and flux-corrected CMFs, we performed this bootstrapping procedure for 100 values of $M_{\rm{min}}$ evenly distributed between 0.1 and 10 $M_{\odot}$." (Single Power-Law Fits to the CMF)
   - parameter: LOWESS smoothing parameter 0.05  
  > "with a smoothing parameter of 0.05 determined by cross-validation" (Single Power-Law Fits to the CMF)
   - fitting: p = N(D̂ ≥ D)/N; acceptance p ≥ 0.10  
  > "we report final “best” fits that begin at the lowest significant ($p \geq .10$) $M_{\rm min}$ value as assessed by $A^2$." (Single Power-Law Fits to the CMF)
   - validation: _not stated_
9. **test for a break with piecewise power laws**: Single, double, triple PPL non-linear WLS fits; model comparison with AICc and Akaike weights  
  > "For the mass ranges defined by minimum mass bins $M_{\rm{min}}$ centered from 1 and 16 $M_{\odot}$ we fit a single power-law, a double PPL, and a triple PPL by performing non-linear WLS regression." (PPL fits and evidence for a break in the CMF)
   - parameter: κ_q = 2, 4, 6 parameters for single, double, triple PPL  
  > "For a single, double, and triple PPL $\kappa_{q}=2$, $4$ and $6$, respectively." (PPL fits and evidence for a break in the CMF)
   - fitting: Non-linear WLS; AICc  
  > "We calculate the single, double and triple PPL fit AIC$_{\rm WLS,c}$ values as a function of $M_{\rm{min}}$ for each CMF." (PPL fits and evidence for a break in the CMF)
   - validation: Break consistent with KS/AD-based M_min  
  > "These results are consistent with those derived from the KS and AD based methods, i.e., which also support a break in power-law behavior of the CMF around 4 to $6\:M_{\odot}$." (PPL fits and evidence for a break in the CMF)
10. **compare log-normal vs power-law**: Log-likelihood ratio R (Vuong test) via powerlaw package; AICc weights vs PPLs  
  > "The significance levels of this test were calculated through the `powerlaw` Python package (cite: alstott_powerlaw_2014)." (Comparison to log-normal distributions)
   - software: powerlaw
   - parameter: Median R over 2000 iterations of uniform masses within bins for binned CMFs  
  > "To assess the binned CMFs, we generated the corresponding number of random masses uniformly distributed in each mass bin and calculated the median $R$ over 2000 iterations of the same process." (Comparison to log-normal distributions)
   - fitting: _not stated_
   - validation: _not stated_
11. **robustness tests**: Vary dendrogram parameters, bins per dex, and split sample by distance (near <3 kpc vs far)  
  > "Figure [8](#fig:cmfs_distance) compares the CMFs of the 15 clumps (containing 127 cores) within 3 kpc and the 13 clumps (containing 95 cores) farther than 3 kpc." (Effects of Dendrogram Parameters, Binning Scheme, and Clump Distance)
   - fitting: _not stated_
   - validation: Results not very sensitive to dendrogram parameters  
  > "This shows that our results using the fiducial method are not very sensitive to the choice of dendrogram parameters." (Effects of Dendrogram Parameters, Binning Scheme, and Clump Distance)
12. **core spatial distribution**: Minimum spanning trees and Q parameter for clumps with ≥10 cores  
  > "which were generated using the Python package $\tt{networkx}$" (Spatial Distribution of Cores)
   - software: networkx
   - fitting: _not stated_
   - validation: _not stated_
13. **compare with G286 and IRDC CMFs**: KS tests of true CMFs for M ≥ 0.79 Msun; MLE refits of Paper I/II CMFs  
  > "We only include cores with $M \geq 0.79$ $M_{\odot}$, i.e., more massive than the lower bound of the bin centered at $1\:M_{\odot}$, in these tests" (Comparison of CMFs in Different Environments and Implications for Massive Star Formation)
   - fitting: _not stated_
   - validation: _not stated_

## Software

- **astrodendro** : dendrogram core identification  
  > "We used the dendrogram algorithm (cite: rosolowsky_structural_2008) as implemented in the python package `astrodendro` to identify cores." (Core Identification)
- **powerlaw (Python)** : significance of log-normal vs power-law likelihood ratio test  
  > "The significance levels of this test were calculated through the `powerlaw` Python package (cite: alstott_powerlaw_2014)." (Comparison to log-normal distributions)
- **networkx** : minimum spanning trees  
  > "which were generated using the Python package $\tt{networkx}$" (Spatial Distribution of Cores)
- **clumpfind** : alternative core finder explored in Paper I; not repeated here  
  > "We note that the effects of using the `clumpfind` algorithm (cite: williams_determining_1994) instead of the dendrogram method were explored in Paper I, and we do not repeat this analysis here." (Core Identification)

## Numeric results

| quantity | value | uncertainty | units | step | quote |
|---|---|---|---|---|---|
| number of cores identified | 222 | not stated | dimensionless | 3 | We identify 222 cores using the dendrogram algorithm with masses ranging from 0.04 to $252\:M_{\odot}$. |
| median raw core mass | 3.0 | not stated | Msun | 4 | “Raw” masses ranged from 0.04 to 252 $M_{\odot}$ with a median mass of 3.0 $M_{\odot}$. |
| median raw core mass surface density | 1.5 | not stated | g cm^-2 | 4 | We find a median values of $\Sigma_c =1.5$ g cm$^{-2}$. |
| median flux-corrected core mass / Σ_c | 4.6 / 2.6 | not stated | Msun / g cm^-2 | 5 | resulted in a new median mass of 4.6 $M_{\odot}$ and a new median $\Sigma_c = 2.6$ g cm$^{-2}$. |
| best-fit α, true CMF (M_min ~5.0 Msun, p=.12) | 0.94 | 0.08 | dimensionless | 8 | The best fit to the true CMF is $\alpha = 0.94 \pm 0.08$ above the bin with a lower limit of $M_{\rm{min}}$ $\sim 5.0 \ M_{\odot}$ ($p=.12$). |
| best-fit α, raw CMF (M_min ~3.6 Msun, p=.15) | 0.95 | 0.09 | dimensionless | 8 | The single power law best fit to the raw CMF is then $\alpha=0.95 \pm 0.09$ with $M_{\rm{min}}$ $\sim 3.6 \ M_{\odot}$ ($p=.15$). |
| best-fit α, flux-corrected CMF (M_min ~6.0 Msun, p=.11) | 1.04 | 0.11 | dimensionless | 8 | The best fit to the flux-corrected CMF is $\alpha=1.04 \pm 0.11$ above $M_{\rm{min}}$ $\sim 6.0\ M_{\odot}$ ($p=.11$). |
| α, true CMF, WLS, M_min=0.79 Msun | 0.50 | 0.07 | dimensionless | 7 | e.g., $\alpha=0.50\pm 0.07$ for the true CMF, compared to the Salpeter index of 1.35 |
| α, true CMF, MLE-B, M_min=0.79 Msun | 0.60 | 0.05 | dimensionless | 7 | e.g., for the true CMF we derived $\alpha=0.60 \pm 0.05$ (via MLE-B), while the WLS method found $\alpha=0.50\pm0.07$. |
| double PPL true CMF: break M1, α1, α2 | M1 = 15 Msun, α1 = 0.11, α2 = 1.29 | α1 ±0.12, α2 ±0.26 | Msun / dimensionless | 9 | For the true CMF the best fit results are $M_{1} = 15 \: M_{\odot}$, $\alpha_1 = 0.11 \pm 0.12$, and $\alpha_2 = 1.29 \pm 0.26$. |
| double PPL raw CMF: break M1, α1, α2 | M1 = 4 Msun, α1 = -0.43, α2 = 0.85 | α1 ±0.13, α2 ±0.07 | Msun / dimensionless | 9 | the best double PPL fit to the raw CMF is where $M_{1} = 4 \: M_{\odot}$, $\alpha_1 = -0.43 \pm 0.13$, and $\alpha_2 = 0.85 \pm 0.07$. |
| log-likelihood ratio R, true CMF, power law vs log-normal (M_min=0.79) | -1.2 | p=.25 | dimensionless | 10 | However, there was no significant evidence that a log-normal was a better descriptor of the true CMF than a single power-law ($R=-1.2$, $p=.25$). |
| Akaike weights true CMF: log-normal / double PPL | 0.03 / 0.85 | not stated | dimensionless | 10 | However, for the true CMF a log-normal fit was not the best description ($w_{i}$(AIC)$_{\rm{ln}}=0.03$) and a double PPL was preferred ($w_{i}$(AIC)$_{\rm{double}} = 0.85$). |
| number of cores across dendrogram parameter tests | 128 to 293 | not stated | dimensionless | 11 | We found a minimum of 128 cores with $F_{\rm{min}}=5\sigma$ and $S_{\rm{min}}=1$ beam, and a maximum of 293 cores with $F_{\rm{min}}=3\sigma$ and $S_{\rm{min}}=0.5$ beam. |
| α range of true CMF across dendrogram tests | 0.94 to 1.10 | not stated | dimensionless | 11 | For the true CMF, $M_{\rm{min}}$ typically ranged between 3 and $8\:M_{\odot}$ with $\alpha$’s between 0.94 and 1.10. |
| Q parameter range (7 clumps with ≥10 cores) | 0.64 to 0.82 | not stated | dimensionless | 12 | We found little evidence for centrally condensed structures in these regions, with values of $Q$ ranging from 0.64 to 0.82 |
| MLE α for G286 and IRDCs (M ≥ 0.79 Msun) | 1.45 (G286); 1.03 (IRDCs) | ±0.15; ±0.07 | dimensionless | 13 | we derive $\alpha = 1.45 \pm 0.15$ for G286 when $M \geq 0.79 \ M_{\odot}$ and $\alpha = 1.03 \pm 0.07$ for the sample of IRDCs |
| KS test p-value, true CMF vs Paper I and Paper II | < .001 | not stated | dimensionless | 13 | The true CMF is significantly different than the true CMFs of Paper I ($p < .001$) and Paper II ($p < .001$). |
| implied core star formation efficiency | 0.1 to 0.3 | not stated | dimensionless | 0 | Comparing with our range of CMF break scales, implies a range star formation efficiencies of $\epsilon_{\rm core} \sim 0.1$ to 0.3. |

## Qualitative findings

- A single power law over the standard range (M_min=0.79 Msun) is a poor description of the CMF  
  > "We also note that a single power law fit over this mass range is not a very accurate description of the CMFs, which is indicated by the fits having very low $p$ values ($<0.001$)." (Single Power-Law Fits to the CMF)
- A triple PPL is never preferred  
  > "A triple PPL is never indicated as being more appropriate than the other forms." (PPL fits and evidence for a break in the CMF)
- Near and far subsamples both show evidence for a break  
  > "Thus, note that both samples independently show evidence for a break in the CMF via this method." (Effects of Dendrogram Parameters, Binning Scheme, and Clump Distance)
- Higher Σ_cl environment is likely responsible for the top-heavy CMF  
  > "Thus, we conclude that this difference in environmental conditions is the factor that is most likely to be responsible for the variation in the observed CMFs." (Comparison of CMFs in Different Environments and Implications for Massive Star Formation)

## Claim tuples

- H: The massive protocluster CMF follows a power law at high masses | E: MLE / MLE-B fits with M_min chosen via AD statistic and bootstrap p-values | R: α = 0.94 ± 0.08 above ~5 Msun for the true CMF | F: High-mass CMF is a power law shallower than Salpeter | **supported**
- H: The CMF has a break in its power-law behavior | E: KS/AD M_min analysis and single/double/triple PPL fits compared with AICc | R: Double PPL preferred at M_min ~1 Msun, transitioning to single power law above ~4-5 Msun; best double PPL break at 15 Msun | F: Break between ~5 and 15 Msun; precise location not determined | **supported**
- H: A log-normal describes the CMF better than power-law models | E: Likelihood ratio test and AICc weights | R: Log-normal preferred for raw and flux-corrected CMFs but not for true CMF (double PPL weight 0.85) | F: Log-normal not better than double PPL for the true CMF; result depends on incompleteness corrections | **partially**
- H: The CMF varies with environment | E: KS tests comparing true CMFs with G286 (Paper I) and IRDCs (Paper II) for M ≥ 0.79 Msun | R: p < .001 for both; ALMAGAL sample has more high-mass cores | F: Massive protocluster CMF is more top-heavy, plausibly due to higher Σ_cl | **supported**
- H: Cores are centrally concentrated within clumps | E: MST Q-parameter for 7 clumps with ≥10 cores | R: Q = 0.64-0.82 | F: Little evidence for central concentration; limited by small numbers | **refuted**

## Reasoning

- Why this data: Clumps within 3.5 kpc chosen to probe down to ~1 Msun cores  
  > "To be able to probe down to relatively low core masses, i.e., $\sim1\:M_\odot$, we limited our analysis to sources within 3.5 kpc" (Source Selection)
- Why this method: Same methods as Papers I and II to allow direct comparison; AD preferred over KS for tail sensitivity  
  > "To identify cores, we followed the methods used in our studies of the G286 protocluster (Paper I) and IRDCs (Paper II), thus allowing a direct comparison of the derived CMFs." (Core Identification); "We prefer the AD statistic due to the known issue of the KS statistic being insensitive to differences in the tails of compared distributions." (Single Power-Law Fits to the CMF)
- Alternative: clumpfind core identification not repeated (explored in Paper I)  
  > "We note that the effects of using the `clumpfind` algorithm (cite: williams_determining_1994) instead of the dendrogram method were explored in Paper I, and we do not repeat this analysis here." (Core Identification)
- Alternative: Herschel dust temperature maps not used due to low resolution  
  > "We note that *Herschel*-derived dust temperature maps have much lower angular resolution ($\gtrsim 30\ensuremath{''}$) than the sizes of the ALMA-identified cores." (Core Mass Estimation)
- Alternative: Pearson χ² statistic considered less powerful than KS/AD  
  > "Other distance metrics such as Pearson’s $\chi^{2}$ cumulative test statistic are also potentially applicable for this goal, but have been found to be less powerful than KS or AD based approaches" (Single Power-Law Fits to the CMF)
- Alternative: Primary-beam-corrected images rejected for core finding  
  > "Attempting to identify cores in primary-beam-corrected images would be compromised as a result of this effect." (Core Identification)
- How they decided it was enough: Sample yields more than double the cores of previous papers in the series  
  > "As we will see, the sample is large enough that the number of cores identified in the clumps is more than double that of previous samples analyzed in this series of papers." (Source Selection)
- Limitation (authors): No local background correction and no core-scale temperatures  
  > "The core masses we report have significant uncertainties due to no correction being made for the local backgrounds within which the cores are embedded, and also from a lack of temperature information on the scales of the cores." (Discussion and Conclusions)
- Limitation (authors): True CMF uncertainties underestimated (no f_num uncertainty)  
  > "However, note that these underestimate the true uncertainties, as they do not allow for additional uncertainty in $f_{\rm num}$." (Construction of the CMF)
- Limitation (authors): Sample incomplete  
  > "We note that this is not a complete sample of all such massive clumps within 3.5 kpc of the Sun" (Source Selection)
- Limitation (authors): Elevated noise in three clumps from cleaning residuals  
  > "We attribute these elevated “noise” estimates to the presence of cleaning residuals, perhaps including effects from real emission features that are just outside the primary beam." (Core Identification)
- Limitation (authors): Small core numbers limit Q analysis  
  > "However, we note that the relatively small sample sizes of cores within each clump severely limit the conclusions that can be derived from these results." (Spatial Distribution of Cores)
- Limitation (authors): Binned MLE bias at level Δα ≈ 0.1  
  > "The results shown in Table 2 comparing MLE and MLE-B results indicate that these biases are present at a level corresponding to $\Delta\alpha\simeq 0.1$" (Effects of Dendrogram Parameters, Binning Scheme, and Clump Distance)
- Caveat (inferred, ours): Single dust temperature of 20 K for likely protostellar, internally heated cores could bias high-mass cores upward and flatten the CMF.
- Caveat (inferred, ours): Completeness corrections reused from other regions' insertion experiments; large f_num factors (≳20) at low masses dominate the true CMF and the break location.
- Caveat (inferred, ours): Varying linear resolution across 0.76-3.5 kpc mixes core definitions; break scale may be resolution-dependent (authors note this).
- Caveat (inferred, ours): No imaging or beam information reported, so S_min and flux integration cannot be checked.
- Caveat (inferred, ours): Double PPL vs single PL comparison relies on WLS fits to ~7-13 bins, so AICc weights are sensitive to binning.

## Reproducibility

- Data public (paper): _not stated_
- Products in archive: _not stated_
- Missing: Continuum imaging recipe and per-clump beam sizes
- Missing: Tabulated f_flux and f_num correction curves
- Missing: Exact continuum frequency used for mass conversion
- Missing: Analysis code for bootstrap, PPL/AICc fits and LOWESS
- Data volume (inferred): 28 single-pointing 12m continuum images are small (<1 GB); re-imaging from calibrated ALMAGAL measurement sets would likely require tens to hundreds of GB.
- Score (inferred): 3/5, Core catalog (Table 4) and statistical recipe are detailed, but imaging/calibration are unstated and the incompleteness corrections are only shown graphically.
- Rediscovery candidate: yes, Data from an ALMA large program in the archive; core catalog with raw and flux-corrected masses allows the MLE fits, M_min selection and KS comparisons to be redone numerically, though true-CMF corrections require Fig. 2 curves.

## Links

- Method: (cite: rosolowsky_structural_2008) (dendrogram algorithm)
- Method: (cite: clauset_power-law_2009) (MLE power-law fitting, KS M_min selection, bootstrap p-values)
- Method: (cite: virkar_power-law_2014) (binned MLE likelihood)
- Method: (cite: newman_power_2005) (MLE estimator for α)
- Method: (cite: ossenkopf_dust_1994) (dust opacity)
- Method: (cite: doi:10.1080/03610927808827599) (corrected AIC)
- Method: (cite: vuong_likelihood_1989) (likelihood ratio test)
- Method: (cite: alstott_powerlaw_2014) (powerlaw Python package)
- Method: (cite: cartwright_statistical_2004) (Q parameter)
- Method: (cite: cleveland_robust_1979) (LOWESS smoothing)
- Companion: (cite: cheng_core_2018) (Paper I: G286 protocluster CMF, same methods)
- Companion: (cite: liu_core_2018) (Paper II: IRDC clump CMF, same methods)
- Related: ALMAGAL (ALMA Cycle 7 large program 2019.1.00195.L)
- Related: Herschel Hi-GAL

## Checks

```json
{
 "quotes": 128,
 "quotes_ok": 128,
 "quote_pass_rate": 1.0,
 "quotes_too_long": 0,
 "unsupported_facts": 0,
 "project_codes": 1,
 "codes_not_in_text": [],
 "codes_not_in_obscore": [],
 "obscore_codes_not_in_card": [],
 "codes_printed_but_missing": [],
 "numeric_results": 19,
 "numeric_problems": 0,
 "fill": {
  "facts": 131,
  "stated": 82,
  "rate": 0.626
 },
 "evidence_ok": true
}
```
