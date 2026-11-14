# The Core Mass Function across Galactic Environments. III. Massive Protoclusters

`2021ApJ...916...45O` | The Astrophysical Journal 2021 | first author: O'Neill, Theo J. | arXiv: 2104.08861 | DOI: 10.3847/1538-4357/ac062d | **HELD OUT (benchmark)**

Card schema 1.0 | model claude-haiku-5-5 | depth full | type archival_reuse

## Science

- Fields: star_formation
- Question: Measure the core mass function (CMF) of 28 dense clumps within 3.5 kpc that are likely central regions of massive protoclusters, and test for a break in its power-law behavior  
  > "Here we measure the CMF in 28 dense clumps within 3.5 kpc that are likely to be central regions of massive protoclusters" (abstract)
- Target **28 ALMAGAL clumps (Table 1 sample)**: coordinates Galactic l, b per clump, listed in Table 1  
  > "Clumps distances ranged between 0.79 kpc and 3.5 kpc." (Results); "Overview of Clump Sample" (Table 1 caption); z/distance 0.79 to 3.5 kpc (text); per-clump d in Table 1  
  > "Clumps distances ranged between 0.79 kpc and 3.5 kpc." (Results); "Overview of Clump Sample" (Table 1 caption); distance from _not stated_

## Data provenance

- ALMA projects: 2019.1.00195.L
- bands: 1.3 mm dust continuum  
  > "observed via 1.3 mm dust continuum emission by the ALMAGAL project" (abstract)
- frequencies and spectral setup: Continuum only; the ALMAGAL survey is described as observing near 1.4 mm, while the abstract says 1.3 mm  
  > "ALMAGAL was designed to observe continuum and line emission near 1.4 mm" (Source Selection)
- continuum bandwidth: _not stated_
- arrays: 12m array  
  > "had 12m-array observations delivered to the ALMA archive by May 2020" (Source Selection)
- configurations: _not stated_
- baselines: _not stated_
- angular resolution: _not stated_
- max recoverable scale: _not stated_
- sensitivity: Median 1-sigma RMS of 0.30 mJy/beam across pointings; G316.80, G316.81 and G345.50 are higher (1.05, 0.85, 1.38 mJy/beam)  
  > "The median value of $\sigma$ was 0.30 mJy $\textrm{beam}^{-1}$." (Core Identification)
- time on source: _not stated_
- observing dates: _not stated_
- pi or archival as stated: ALMAGAL Cycle 7 project, PI S. Molinari  
  > "We selected sources from the ALMA Cycle 7 project" (Source Selection)
- Other facility **Herschel Hi-GAL survey**: Clump radii, masses, surface densities and evolutionary type (derived by Elia et al. 2017); clump selection  
  > "The radius, mass, $\Sigma_{\rm cl}$, and type were derived by (cite: elia_hi-gal_2017)" (Table 1 notes)
- External data: Clump radius, mass, surface density and evolutionary type for the 28 clumps (Table 1)  
  > "The radius, mass, $\Sigma_{\rm cl}$, and type were derived by (cite: elia_hi-gal_2017)" (Table 1 notes) [from (cite: elia_hi-gal_2017)]
- External data: G286 protocluster CMF: alpha = 1.24 +/- 0.17 over M >~ 1 Msun from 76 cores (WLS)  
  > "In the first paper in this series we measured the CMF from 1.3 mm ALMA continuum observations of the G286 protocluster" (Introduction) [from (cite: cheng_core_2018)]
- External data: IRDC clump CMF: alpha = 0.86 +/- 0.11 over the same mass range from 107 cores (WLS)  
  > "In the second paper, we analyzed a sample of IRDC clumps" (Introduction) [from (cite: liu_core_2018)]
- External data: Salpeter IMF slope alpha = 1.35 for 0.4 to 10 Msun  
  > "derived $\alpha\simeq1.35$ for the mass range between 0.4 and 10" (Introduction) [from (cite: salpeter_luminosity_1955)]
- External data: W43-MM1 CMF slope alpha = 0.90 +/- 0.06 for M >~ 1.6 Msun from 105 cores  
  > "found $\alpha = 0.90\pm0.06$ for masses $M\gtrsim 1.6\:M_\odot$ from a sample of 105 cores" (Introduction) [from (cite: motte_unexpectedly_2018)]
- External data: G286 clump surface density within 1.54 pc of about 0.1 g cm^-2  
  > "G286 is estimated to have $\Sigma_{\rm cl}\sim 0.1\:{\rm g\:cm}^{-2}$" (Comparison of CMFs in Different Environments) [from (cite: cheng_gas_2020)]
- External data: IRDC clump surface densities usually <= 0.4 g cm^-2  
  > "the IRDC clumps usually have $\Sigma_{\rm cl}\lesssim 0.4\:{\rm g\:cm}^{-2}$" (Comparison of CMFs in Different Environments) [from (cite: butler_mid-infrared_2012)]
- Simulation/model as data: Turbulent Core Model prediction: core accretion rate from the clump scales as Sigma_cl^(3/4)  
  > "the Turbulent Core Model of (cite: mckee_formation_2003) predicts that the rate of accretion of a core from the ambient clump is" (Comparison of CMFs in Different Environments)

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
- primary beam correction: Cores identified on images NOT corrected for the primary beam (pre-primary-beam corrected continuum images)  
  > "follow those used in Paper II by identifying cores in images that have not been corrected for the primary beam." (Core Identification)
- array combination: _not stated_
- smoothing: _not stated_
- final beam: _not stated_
- final rms: Median 1-sigma RMS 0.30 mJy/beam; elevated for G316.80, G316.81, G345.50  
  > "The median value of $\sigma$ was 0.30 mJy $\textrm{beam}^{-1}$." (Core Identification)

### Inherited from earlier work

- Dendrogram parameters: Fmin = 4 sigma, delta = 1 sigma, Smin = 0.5 synthesized beam, cores = leaves  
  > "These parameter choices are the same as used in Papers I and II" (Core Identification) [from Paper I (cite: cheng_core_2018) and Paper II (cite: liu_core_2018)]
- Optically thin dust-emission mass method with fiducial kappa and gas-to-dust ratio  
  > "We estimated masses of cores by assuming optically thin thermal emission from dust, as in Papers I and II." (Core Mass Estimation) [from Papers I and II (cite: cheng_core_2018; liu_core_2018)]
- Dust opacity per unit dust mass 0.899 cm^2 g^-1 at 1.3 mm (thin ice mantle model)  
  > "the value from the moderately coagulated thin ice mantle model of (cite: ossenkopf_dust_1994)" (Core Mass Estimation) [from (cite: ossenkopf_dust_1994)]
- Gas-to-refractory-dust ratio of 141  
  > "using a gas-to-refractory-component-dust ratio of 141 (cite: draine_physics_2011)" (Core Mass Estimation) [from (cite: draine_physics_2011)]
- Flux and number recovery correction factors from artificial core insertion, applied as universal medians; CMF binning (five bins per dex, bin at 1 Msun) and WLS fitting method  
  > "In Papers I and II, we derived correction factors to estimate a complete, i.e., “true”, CMF from an observed “raw” CMF." (Core Flux Recovery and Completeness Corrections) [from Papers I and II (cite: cheng_core_2018; liu_core_2018)]

### Not stated but needed to reproduce (our reading)

- Imaging parameters of the ALMAGAL continuum mosaics used (CASA task, weighting/robust, uv taper, cell and image size, beam size, final beam)
- Calibration pipeline/version and any self-calibration; the data reduction history of the archive products
- Definition of the mosaic/pointing boundaries and the primary-beam response map used to define the 'pre-primary-beam' images
- Mask or region used by astrodendro (any spatial restriction, pixel-based vs. beam-based unit conversion details)
- Numerical details of the artificial core insertion: inserted core profile, number of insertions, radial/morphological assumptions, and the function fitted to f_flux and f_num
- Per-clump distance values and their source for the mass conversion (the paper gives a table of distances but not the adopted distance origin)
- Per-clump dust temperature choice beyond the fixed 20 K, and how the 1.3 vs 1.4 mm wavelength was handled in the mass formula
- Exact treatment of the empty high-mass bin beyond the stated pseudo-count rule, and random seeds for bootstrap and synthetic CMFs
- Software versions for astrodendro, networkx and powerlaw; code used for MLE, MLE-B, AICc and LOWESS steps

## Analysis recipe

1. **estimate per-pointing noise**: Mean sigma over 50 randomly placed synthesized-beam-sized areas of pre-primary-beam corrected continuum images, using areas with max intensity below 3.5 mJy/beam  
  > "finding the mean value of $\sigma$ in 50 randomly-placed synthesized-beam-sized-areas of the pre-primary-beam corrected continuum images with a maximum intensity less than 3.5 mJy" (Core Identification)
   - parameter: 50 random beam-sized areas; max intensity < 3.5 mJy/beam  
  > "with a maximum intensity less than 3.5 mJy" (Core Identification)
   - fitting: _not stated_
   - validation: Three high-noise clumps attributed to cleaning residuals  
  > "We attribute these elevated “noise” estimates to the presence of cleaning residuals" (Core Identification)
2. **identify cores with dendrogram**: Dendrogram identification of cores as leaves of the dendrogram in each clump image  
  > "We used the dendrogram algorithm (cite: rosolowsky_structural_2008) as implemented in the python package astrodendro to identify cores." (Core Identification)
   - software: astrodendro
   - parameter: Fmin = 4 sigma for trunks  
  > "We required parent structures (trunks) in the dendrogram to have a minimum intensity $F_{\rm min}$ of $4\sigma$." (Core Identification)
   - parameter: delta = 1 sigma for branches and leaves  
  > "We also required substructures (*branches* and *leaves*) to have a minimum increase in intensity $\delta$ of $1\sigma$" (Core Identification)
   - parameter: Smin = 0.5 synthesized beam  
  > "a minimum area $S_{\rm{min}}$ of half the synthesized beam" (Core Identification)
   - fitting: _not stated_
   - validation: Parameter variation (Fmin 3,4,5 sigma; Smin 0.5 or 1 beam) gives 128 to 293 cores  
  > "We found a minimum of 128 cores with $F_{\rm{min}}=5\sigma$ and $S_{\rm{min}}=1$ beam, and a maximum of 293 cores" (Effects of Dendrogram Parameters, Binning Scheme, and Clump Distance)
3. **convert flux to core mass**: Optically thin thermal dust emission: Sigma_mm from integrated flux and dust opacity; M = Sigma A, scaled by distance squared  
  > "We estimated masses of cores by assuming optically thin thermal emission from dust, as in Papers I and II." (Core Mass Estimation)
   - parameter: Dust temperature 20 K for all cores  
  > "In the absence of measurements of temperature for each source, we assumed dust temperatures" (Core Mass Estimation)
   - parameter: Opacity 0.899 cm^2/g per unit dust mass; kappa_1.3mm = 6.38e-3 cm^2/g (gas-to-dust 141)  
  > "the value from the moderately coagulated thin ice mantle model of (cite: ossenkopf_dust_1994)" (Core Mass Estimation)
   - parameter: Mass scale 0.192 Msun per mJy at 2.5 kpc (fiducial)  
  > "where $A$ is the projected area of the core, $d$ is the source distance" (Core Mass Estimation)
   - assumption: Optically thin emission; dust temperature 20 K; gas-to-dust ratio 141; per-clump Hi-GAL-based distance used in mass scaling  
  > "where $A$ is the projected area of the core, $d$ is the source distance" (Core Mass Estimation)
   - fitting: _not stated_
   - validation: Temperature sensitivity: masses change by factors 1.48 (15 K) and 0.604 (30 K)  
  > "If temperatures of 15 K or 30 K were to be adopted, the mass estimates would differ by factors of 1.48 and 0.604, respectively." (Core Mass Estimation)
4. **correct flux and number completeness**: Artificial core insertion into clump images; flux recovery fraction is the median recovered/true flux; number recovery fraction from insertions; corrections applied as functions of normalized flux  
  > "Artificial cores of varying masses were randomly inserted into real clump images" (Core Flux Recovery and Completeness Corrections)
   - parameter: Flux recovery defined as median of recovered to true flux  
  > "defined as the median value of the ratio of recovered to true flux" (Core Flux Recovery and Completeness Corrections)
   - parameter: Median correction curves adopted as universal  
  > "We adopted the median values of these factors as universal values with which to correct our observed “raw” CMFs from our entire clump sample." (Core Flux Recovery and Completeness Corrections)
   - fitting: _not stated_
   - validation: Correction curves closely approximate each other when plotted against normalized flux  
  > "they closely approximate each other when considered as a function of normalized flux" (Core Flux Recovery and Completeness Corrections)
5. **build binned CMFs and fit single power law by WLS**: Combine clumps into raw, flux-corrected and number-corrected (true) binned CMFs; fit power law by weighted least squares in log dN/dlogM  
  > "We then combined all sources together to create final CMFs." (Construction of the CMF)
   - parameter: Five bins per dex, bin centered on 1 Msun, Mmin = 0.79 Msun  
  > "with five bins per dex, and a bin centered on 1" (Construction of the CMF)
   - assumption: Poisson N^1/2 uncertainties per bin  
  > "We assumed $\textit{N}^{1/2}$ Poisson counting uncertainties for each bin." (Construction of the CMF)
   - fitting: Weighted least squares on log dN/dlogM normalized by averaged asymmetric Poisson errors; empty high-mass bin treated as an effective upper limit  
  > "First, we follow the fiducial weighted least squares (WLS) method of Papers I and II" (Single Power-Law Fits to the CMF)
   - validation: Results insensitive to the treatment of the empty bin  
  > "Note that the results are insensitive to these details of how the empty bin is treated." (Single Power-Law Fits to the CMF)
6. **fit power law by maximum likelihood (unbinned and binned)**: MLE on unbinned cores (raw and flux-corrected only) and MLE-B on binned histograms (all three CMFs)  
  > "we applied an MLE (cite: newman_power_2005)" (Single Power-Law Fits to the CMF)
   - parameter: Mmin = 0.79 Msun for MLE and MLE-B  
  > "We first adopt $M_{\rm{min}}$ $=0.79$ $M_{\odot}$" (Single Power-Law Fits to the CMF)
   - assumption: Power-law form f(M) proportional to M^-(alpha+1)  
  > "We assume a power-law form of" (Single Power-Law Fits to the CMF)
   - fitting: MLE alpha = n [sum ln(Mi/Mmin)]^-1; standard error alpha/sqrt(n); MLE-B log-likelihood over bins (after Virkar and Clauset)  
  > "This method is based on that proposed by (cite: virkar_power-law_2014)" (Single Power-Law Fits to the CMF)
   - validation: Binned MLE bias ~0.1 in alpha, comparable to Poisson uncertainty  
  > "which is about the uncertainty level caused by Poisson sampling uncertainties of the CMFs." (Effects of Dendrogram Parameters, Binning Scheme, and Clump Distance)
7. **choose Mmin for the power-law range and test goodness of fit**: Scan Mmin; compute KS D and Anderson-Darling A^2 between CDFs; bootstrap p-values using synthetic CMFs (semi-parametric, after Clauset et al.); best fit starts at lowest Mmin with p >= 0.10 by A^2  
  > "We first estimated the optimal $M_{\rm{min}}$ for each CMF through fitting power-laws beginning at every unique core mass" (Single Power-Law Fits to the CMF)
   - parameter: N = 3000 synthetic CMFs per Mmin  
  > "We then repeated this procedure $N=3000$ times" (Single Power-Law Fits to the CMF)
   - parameter: 100 Mmin values between 0.1 and 10 Msun (raw, flux-corrected); 11 bins between 0.1 and 10 Msun (true)  
  > "For the raw and flux-corrected CMFs, we performed this bootstrapping procedure for 100 values" (Single Power-Law Fits to the CMF)
   - parameter: Acceptance threshold p >= 0.10  
  > "we report final “best” fits that begin at the lowest significant" (Single Power-Law Fits to the CMF)
   - assumption: Low-mass end of synthetic CMF resampled with replacement from real cores; high-mass end drawn from fitted power law  
  > "we randomly selected $n_{\rm low}$ cores from the pool of the $n_{\rm low}$ real cores." (Single Power-Law Fits to the CMF)
   - fitting: MLE with optimal Mmin re-fit for each synthetic sample  
  > "we fitted a power-law to it using the fiducial MLE method, including fitting an optimal $M_{\rm{min}}$" (Single Power-Law Fits to the CMF)
   - validation: A^2 preferred over KS because KS is insensitive to tails  
  > "We prefer the AD statistic due to the known issue of the KS statistic being insensitive to differences in the tails" (Single Power-Law Fits to the CMF)
8. **test for a break via piecewise power laws**: Fit single, double and triple piecewise power laws with non-linear WLS for Mmin from 1 to 16 Msun; compare with corrected AIC and Akaike weights  
  > "we fit a single power-law, a double PPL, and a triple PPL by performing non-linear WLS regression" (PPL fits and evidence for a break in the CMF)
   - parameter: kappa = 2, 4, 6 parameters for single, double, triple PPL  
  > "For a single, double, and triple PPL $\kappa_{q}=2$, $4$ and $6$, respectively." (PPL fits and evidence for a break in the CMF)
   - fitting: Non-linear WLS; AICc with small-sample penalty; Akaike weights w_i  
  > "we fit a single power-law, a double PPL, and a triple PPL by performing non-linear WLS regression" (PPL fits and evidence for a break in the CMF)
   - validation: Turnover from double to single PPL at ~4 Msun (raw), ~5 Msun (flux-corrected and true); triple PPL never preferred  
  > "A triple PPL is never indicated as being more appropriate than the other forms." (PPL fits and evidence for a break in the CMF)
9. **compare log-normal and power-law descriptions**: Vuong-type log-likelihood ratio R between power law and log-normal, plus AICc weights including log-normal  
  > "We explored the goodness of fit of log-normal distributions and single power-laws by calculating the ratio $R$ of their log-likelihoods" (Comparison to log-normal distributions)
   - software: powerlaw
   - parameter: Median R over 2000 random-mass realizations for binned CMFs  
  > "calculated the median $R$ over 2000 iterations of the same process" (Comparison to log-normal distributions)
   - fitting: Log-normal fit to M > 0.79 Msun (and M > 1.26 Msun as a check)  
  > "Fitting only for $M>0.79\:M_\odot$, we derive the log-normal fits" (Comparison to log-normal distributions)
   - validation: Significance from powerlaw package; p > 0.10 means no significant difference  
  > "$p$-values larger than $p=.10$ indicate that there is no significant difference" (Comparison to log-normal distributions)
10. **test sensitivity to distance and dendrogram choices**: Compare near (<=3 kpc) and far (>3 kpc) clump CMFs with KS tests and single power-law MLE fits; repeat core identification with varied dendrogram parameters  
  > "Figure [8](#fig:cmfs_distance) compares the CMFs of the 15 clumps (containing 127 cores) within 3 kpc" (Effects of Dendrogram Parameters, Binning Scheme, and Clump Distance)
   - parameter: Near sample 15 clumps (127 cores); far sample 13 clumps (95 cores)  
  > "the 13 clumps (containing 95 cores) farther than 3 kpc" (Effects of Dendrogram Parameters, Binning Scheme, and Clump Distance)
   - fitting: Single power-law MLE as in the fiducial fit  
  > "We fit single power-laws to the near and far CMFs using the fiducial MLE fitting process" (Effects of Dendrogram Parameters, Binning Scheme, and Clump Distance)
   - validation: Both samples independently show evidence for a break  
  > "Thus, note that both samples independently show evidence for a break in the CMF via this method." (Effects of Dendrogram Parameters, Binning Scheme, and Clump Distance)
11. **measure core clustering**: Minimum spanning tree per clump (clumps with at least 10 cores) and dimensionless Q = mbar/sbar  
  > "For those clumps with at least 10 cores, we analyzed the clustering of cores within clumps by calculating minimum spanning trees (MST)" (Spatial Distribution of Cores)
   - software: networkx
   - parameter: Q > 0.8 centrally concentrated; Q < 0.8 fractal substructure  
  > "large $Q$ values ($Q>0.8$) indicate that structures are centrally concentrated" (Spatial Distribution of Cores)
   - fitting: _not stated_
   - validation: Caveat: small core numbers limit conclusions  
  > "the relatively small sample sizes of cores within each clump severely limit the conclusions" (Spatial Distribution of Cores)

## Software

- **astrodendro** : Dendrogram identification of cores as leaves  
  > "as implemented in the python package astrodendro to identify cores." (Core Identification)
- **networkx** : Minimum spanning trees for core clustering (Q parameter)  
  > "which were generated using the Python package" (Spatial Distribution of Cores)
- **powerlaw** : Significance levels for log-normal vs power-law likelihood ratio test  
  > "The significance levels of this test were calculated through the powerlaw Python package" (Comparison to log-normal distributions)

## Numeric results

| quantity | value | uncertainty | units | step | quote |
|---|---|---|---|---|---|
| Number of dendrogram cores identified in 28 clumps | 222 | not stated | cores | 2 | We found 222 cores in total |
| Raw core mass range | 0.04 to 252 | not stated | Msun | 3 | Raw masses ranged from 0.04 to 252 |
| Median raw core mass | 3.0 | not stated | Msun | 3 | with a median mass of 3.0 $M_{\odot}$. |
| Median flux-corrected core mass | 4.6 | not stated | Msun | 4 | resulted in a new median mass of 4.6 $M_{\odot}$ |
| Single power-law slope alpha, true CMF, above Mmin ~5.0 Msun (best fit) | 0.94 | 0.08 | dimensionless | 7 | The best fit to the true CMF is $\alpha = 0.94 \pm 0.08$ above the bin with a lower limit of |
| Single power-law slope alpha, raw CMF, above Mmin ~3.6 Msun (best fit) | 0.95 | 0.09 | dimensionless | 7 | The single power law best fit to the raw CMF is then $\alpha=0.95 \pm 0.09$ |
| Single power-law slope alpha, flux-corrected CMF, above Mmin ~6.0 Msun (best fit) | 1.04 | 0.11 | dimensionless | 7 | The best fit to the flux-corrected CMF is $\alpha=1.04 \pm 0.11$ |
| Single power-law slope alpha, true CMF, WLS, Mmin = 0.79 Msun | 0.50 | 0.07 | dimensionless | 5 | for the true CMF we derived $\alpha=0.60 \pm 0.05$ (via MLE-B), while the WLS method found $\alpha=0.50\pm0.07$. |
| Single power-law slope alpha, true CMF, MLE-B, Mmin = 0.79 Msun | 0.60 | 0.05 | dimensionless | 6 | for the true CMF we derived $\alpha=0.60 \pm 0.05$ (via MLE-B) |
| Break mass range in the true CMF | ~5 to 15 | not stated | Msun | 8 | a “break” in the power-law behavior of the true CMF is indicated between $\sim$5 to $15 \ M_{\odot}$ |
| Best double PPL break mass M1, true CMF (Mmin = 0.79 Msun) | 15 | not stated | Msun | 8 | For the true CMF the best fit results are $M_{1} = 15 \: M_{\odot}$ |
| Double PPL slope alpha1 (below break), true CMF | 0.11 | 0.12 | dimensionless | 8 | $\alpha_1 = 0.11 \pm 0.12$, and $\alpha_2 = 1.29 \pm 0.26$. |
| Double PPL slope alpha2 (above break), true CMF | 1.29 | 0.26 | dimensionless | 8 | and $\alpha_2 = 1.29 \pm 0.26$. |
| Log-likelihood ratio R (power law vs log-normal), true CMF, Mmin = 0.79 Msun; p = 0.25 | -1.2 | not stated | dimensionless | 9 | there was no significant evidence that a log-normal was a better descriptor of the true CMF than a single power-law ($R=-1.2$, $p=.25$). |
| Mean core mass of log-normal fit (fit down to 0.79 Msun) | 0.90 | not stated | Msun | 9 | the mean core mass is $\bar{M}=0.90\:M_\odot$ when the fit is carried out down to this bin |
| Q parameter range for the seven clumps with at least 10 cores | 0.64 to 0.82 | not stated | dimensionless | 11 | with values of $Q$ ranging from 0.64 to 0.82 |
| Mass rescaling factor if T = 15 K (relative to 20 K) | 1.48 | not stated | dimensionless | 3 | the mass estimates would differ by factors of 1.48 and 0.604, respectively. |
| Mass rescaling factor if T = 30 K (relative to 20 K) | 0.604 | not stated | dimensionless | 3 | the mass estimates would differ by factors of 1.48 and 0.604, respectively. |
| Single power-law slope alpha for G286 (MLE, M >= 0.79 Msun), from this paper's comparison | 1.45 | 0.15 | dimensionless | 6 | we derive $\alpha = 1.45 \pm 0.15$ for G286 when $M \geq 0.79 \ M_{\odot}$ |
| Single power-law slope alpha for IRDC sample (MLE, M >= 0.79 Msun), from this paper's comparison | 1.03 | 0.07 | dimensionless | 6 | and $\alpha = 1.03 \pm 0.07$ for the sample of IRDCs |
| Core formation efficiency implied by break scale comparison | 0.1 to 0.3 | not stated | dimensionless | 0 | implies a range star formation efficiencies of $\epsilon_{\rm core} \sim 0.1$ to 0.3. |

## Qualitative findings

- The massive protocluster CMF has significantly more high-mass cores than the G286 and IRDC CMFs (KS p < .001 vs both)  
  > "has a significantly larger population of high-mass cores than the CMFs derived from the G286 protocluster and the IRDC clumps." (Comparison of CMFs in Different Environments and Implications for Massive Star Formation)
- Single power-law slope of the flux-corrected CMF is steeper than WLS-derived values, and the single power law is not a good description at low mass  
  > "a single power law fit over this mass range is not a very accurate description of the CMFs" (Single Power-Law Fits to the CMF)

## Claim tuples

- H: Does the CMF of massive protoclusters show a break in its power-law form? | E: Kolmogorov-Smirnov and Anderson-Darling minimum-Mmin analysis with bootstrap p-values, plus piecewise power-law fits compared by corrected AIC weights, on the true CMF of 222 cores | R: Single power law acceptable above about 5 Msun (alpha = 0.94 +/- 0.08); double PPL preferred down to 1 Msun with break at 15 Msun | F: A break in the CMF power law between about 5 and 15 Msun is indicated | **supported**
- H: Is the high-mass CMF of massive protoclusters different from the CMFs of G286 and IRDC clumps? | E: KS tests comparing true CMFs above 0.79 Msun, and comparison of MLE slopes | R: Both KS tests give p < .001; massive protocluster CMF has more high-mass cores | F: The massive protocluster CMF is significantly different, containing more massive cores | **supported**
- H: Is the difference in CMF caused by the clump environment (surface density)? | E: Comparison of clump mass surface densities across the three samples and theoretical scalings (Bonnor-Ebert mass, Turbulent Core Model) | R: Massive protoclusters have Sigma_cl > 1 g/cm^2 vs <= 0.4 for IRDCs and ~0.1 for G286; no direct test of the mechanism | F: Environmental conditions are judged the factor most likely responsible for the CMF variation | **partially**
- H: Does the CMF slope match the Salpeter-like IMF? | E: Single power-law fits to CMF above Mmin | R: alpha = 0.94 +/- 0.08 for M >~ 5 Msun, significantly shallower than the Salpeter value 1.35 | F: The CMF is shallower than the standard Salpeter IMF and many local CMFs | **supported**

## Reasoning

- Why this data: Sources within 3.5 kpc with 12m-array data, so that cores down to about 1 Msun can be probed  
  > "To be able to probe down to relatively low core masses, i.e., $\sim1\:M_\odot$, we limited our analysis to sources within 3.5 kpc" (Source Selection)
- Why this method: Same methods as Papers I and II to allow direct comparison of CMFs  
  > "thus allowing a direct comparison of the derived CMFs" (Core Identification)
- Alternative: Identify cores on primary-beam-corrected images, rejected because noise varies with position  
  > "Attempting to identify cores in primary-beam-corrected images would be compromised as a result of this effect." (Core Identification)
- Alternative: clumpfind instead of dendrogram, explored in Paper I and not repeated  
  > "the effects of using the" (Core Identification)
- Alternative: Log-normal or hybrid log-normal plus power-law models; log-normal not preferred for the true CMF  
  > "Other models, such as hybrid models with a log-normal at low masses plus a high-mass power law tail are likely to be possible good descriptions" (Comparison to log-normal distributions)
- How they decided it was enough: Sample size judged large enough: core count more than double earlier samples  
  > "the sample is large enough that the number of cores identified in the clumps is more than double that of previous samples" (Source Selection)
- Limitation (authors): No correction for local background; masses may be overestimated  
  > "The core masses we report have significant uncertainties due to no correction being made for the local backgrounds" (Discussion and Conclusions)
- Limitation (authors): No temperature information on core scales; brighter cores may be warmer and over-massed  
  > "If, for example, brighter cores are systematically warmer than fainter cores, then their masses would be systematically overestimated in our analysis." (Discussion and Conclusions)
- Limitation (authors): Many cores likely protostellar with internal heating  
  > "It is also likely that a large fraction of the cores observed here are protostellar" (Discussion and Conclusions)
- Limitation (authors): Sample is not complete and only a fraction of ALMAGAL data  
  > "We note that this is not a complete sample of all such massive clumps within 3.5 kpc of the Sun" (Source Selection)
- Caveat (inferred, ours): Number-correction factors reach >~20 for the far sample near 1 Msun, so the lowest-mass true CMF bins are unreliable
- Caveat (inferred, ours): Break mass is quoted inconsistently: ~5 to 15 Msun in abstract/conclusion, ~4 to 15 in the PPL section, ~3 to 10 in the comparison section
- Caveat (inferred, ours): Frequency is given as 1.3 mm in the abstract and as near 1.4 mm for ALMAGAL in Source Selection
- Caveat (inferred, ours): Clump distance minimum is 0.79 kpc in text while Table 1 lists 0.76 kpc for G320.24; distance source not stated
- Caveat (inferred, ours): Single-clump core counts for Q analysis are small (10 to 33), limiting the clustering conclusions
- Caveat (inferred, ours): Environmental interpretation rests on a comparison of different samples and methods, not a controlled test

## Reproducibility

- Data public (paper): Archive delivery by May 2020 is stated; public status of the ALMAGAL data is not stated  
  > "had 12m-array observations delivered to the ALMA archive by May 2020" (Source Selection)
- Products in archive: _not stated_
- Code: _not stated_
- Missing: Imaging recipe for the ALMAGAL continuum mosaics (task, weighting, robust, cell size, beam)
- Missing: Calibration and pipeline versions used to produce the archive images
- Missing: Per-clump distance table origin and adopted values
- Missing: Artificial core insertion details and the fitted correction function
- Missing: Software versions and analysis code for MLE, MLE-B, AICc, bootstrap and LOWESS
- Missing: Dust temperature treatment beyond fixed 20 K
- Data volume (inferred): Modest: 28 continuum mosaics (likely a few to tens of GB including products), inferred
- Score (inferred): 5/5, Analysis recipe and fitting statistics are described in detail, but imaging parameters, calibration details, insertion-test specifics and code are absent, so the core catalog could not be rebuilt exactly.
- Rediscovery candidate: no, Recipe is incomplete (no imaging or calibration settings) and public data status is not stated, so reproduction would require guessing key inputs.

## Links

- Method: (cite: rosolowsky_structural_2008) (Dendrogram core identification method)
- Method: (cite: clauset_power-law_2009) (MLE power-law fitting, KS-based Mmin selection and bootstrap goodness-of-fit)
- Method: (cite: virkar_power-law_2014) (Binned MLE (MLE-B) method and AD/KS test comparison)
- Method: (cite: newman_power_2005) (MLE estimator for the power-law index)
- Method: (cite: cartwright_statistical_2004) (Q parameter for MST clustering)
- Companion: (cite: cheng_core_2018) (Paper I: G286 protocluster CMF with the same methods)
- Companion: (cite: liu_core_2018) (Paper II: IRDC clump CMF with the same methods)
- Related: ALMAGAL (ALMA Evolutionary Study of High Mass Protocluster Formation in the Galaxy), PI S. Molinari
- Related: Herschel Hi-GAL survey

## Checks

```json
{
 "quotes": 119,
 "quotes_ok": 118,
 "quote_pass_rate": 0.992,
 "quotes_too_long": 0,
 "unsupported_facts": 0,
 "project_codes": 1,
 "codes_not_in_text": [],
 "codes_not_in_obscore": [],
 "obscore_codes_not_in_card": [],
 "codes_printed_but_missing": [],
 "numeric_results": 21,
 "numeric_problems": 0,
 "fill": {
  "facts": 125,
  "stated": 90,
  "rate": 0.72
 },
 "evidence_ok": false
}
```

## Figures

- **Figure 2** (other, 4 panel(s), model, simulation): Median flux recovery fraction and number recovery fraction versus core mass and versus normalized inserted flux, for the dendrogram method on the G286 protocluster and seven IRDCs, from synthetic core insertion tests.
  - axes: x (left panels): core mass M [M_sun]; x (right panels): normalized flux of inserted cores [multiples of RMS noise (not labelled as unit-free ratio)]; y (top): flux recovery fraction f_flux [dimensionless]; y (bottom): number recovery fraction f_num [dimensionless]
  - supports step 4
  - validation: Shows how completeness of flux and number recovery varies with core mass and inserted flux, which is used to correct the CMFs.
  - read off the plot: approx. f_flux plateau about 0.53-0.62 at low mass for all regions; approx. f_num reaches 0.9 near M about 1 M_sun for region B (purple) and near 2-3 M_sun for region D (red); approx. G286 f_num 0.5 at M about 0.6-1 M_sun
- **Figure 3** (histogram, 2 panel(s), data): Combined core mass function of the 28 massive clumps: raw, flux-corrected and number-corrected true CMFs, with power-law fits by weighted least squares (left) and by maximum likelihood from Mmin of 3.6, 6.0 and 5.0 M_sun (right).
  - axes: x: core mass M [M_sun (log scale)]; y: dN/dlogM [number per dex (log scale)]
  - supports step 5
  - read off the plot: approx. true CMF peak dN/dlogM about 700 near 0.3-0.4 M_sun; approx. WLS slopes alpha 0.44 (raw), 0.30 (flux-corrected), 0.50 (true); approx. MLE slopes alpha 0.95, 1.04, 0.94; approx. true CMF highest mass bin about 5 at about 250 M_sun
  - reproduction target
- **Figure 4** (other, 4 panel(s), model): Goodness-of-fit diagnostics for power-law fits versus minimum mass Mmin: KS and Anderson-Darling statistics and their bootstrapped p-values for raw, flux-corrected and true CMFs.
  - axes: x: minimum mass Mmin [M_sun (log scale)]; y (left): KS statistic D and Anderson-Darling statistic A^2 [dimensionless]; y (right): p-value [dimensionless]
  - supports step 7
  - validation: Tests goodness of fit of the power-law model as a function of the chosen Mmin using KS and AD statistics with bootstrapped p-values; p = 0.10 threshold marked.
  - read off the plot: approx. true-CMF KS D about 0.05 at Mmin about 0.3 M_sun; approx. raw-CMF p-value peak about 0.9 near Mmin about 7.5 M_sun; approx. true-CMF p-value about 0.78 at Mmin = 8 M_sun; approx. flux-corrected p-value about 0.58 at Mmin about 8 M_sun
- **Figure 5** (model_vs_data, 3 panel(s), model, data): Piecewise power-law fits (single, double and triple components) to the raw, flux-corrected and true CMFs, from bin 1 M_sun to about 250 M_sun.
  - axes: x: core mass M [M_sun (log scale)]; y: dN/dlogM [number per dex (log scale)]
  - supports step 8
  - validation: Visual comparison of single, double and triple piecewise power-law fits against the binned CMF to test for a break.
  - read off the plot: approx. raw-CMF double-fit break near 4 M_sun; approx. flux-corrected double-fit break near 6 M_sun; approx. true-CMF single fit ends near 10 at 250 M_sun
- **Figure 6** (other, 3 panel(s), model): Akaike weights of single, double and triple piecewise power-law fits as a function of the Mmin from which each fit was derived, for raw, flux-corrected and true CMFs.
  - axes: x: minimum mass Mmin [M_sun]; y: Akaike weight w_i [dimensionless]
  - supports step 8
  - validation: Model selection among single, double and triple piecewise power laws via Akaike weights.
  - read off the plot: approx. raw-CMF single-fit weight about 0.53 at Mmin 4 M_sun; approx. true-CMF double-fit weight about 0.98 at Mmin 1.6 M_sun; approx. single-fit weight about 0.98 at Mmin 10 M_sun for all three CMFs
- **Figure 7** (model_vs_data, 2 panel(s), model, data): Best log-normal fits by maximum likelihood to the raw, flux-corrected and true CMFs above Mmin of 0.79 M_sun (left) and 1.25 M_sun (right).
  - axes: x: core mass M [M_sun (log scale)]; y: dN/dlogM [number per dex (log scale)]
  - supports step 9
  - validation: Compares log-normal model shapes against the binned CMFs to assess log-normal versus power-law description.
  - read off the plot: approx. raw-CMF log-normal peak about 120 dN/dlogM near 3-4 M_sun; approx. true-CMF log-normal fit with sigma 1.67 and mu -0.10 (left panel); approx. true-CMF peak about 270 dN/dlogM near 0.8 M_sun (left)
- **Figure 8** (histogram, 2 panel(s), data): Combined CMFs of the 15 clumps within 3 kpc (left) and the 13 clumps beyond 3 kpc (right), with raw, flux-corrected and true CMFs and MLE power-law fits.
  - axes: x: core mass M [M_sun (log scale)]; y: dN/dlogM [number per dex (log scale)]; distance: clump distance [kpc]
  - supports step 10
  - validation: Tests sensitivity of the CMF slope to distance subsets of the sample.
  - read off the plot: approx. d<=3 kpc slopes alpha 0.83, 0.86, 0.81; approx. d>3 kpc slopes alpha 0.90, 1.04, 1.02; approx. d>3 kpc true-CMF peak about 400 dN/dlogM near 0.4 M_sun
- **Figure 9** (other, 7 panel(s), data): Minimum spanning trees linking core positions within seven clumps that each contain at least ten cores, drawn inside the ALMA primary beam field of view.
  - axes: x: relative position on sky [not labelled]; y: relative position on sky [not labelled]
  - supports step 11
  - validation: Provides the spatial structure used for core clustering measurement via minimum spanning trees.
  - read off the plot: approx. seven clumps shown: G305.13, G314.22, G316.80, G319.86, G327.39, G341.94, G345.50
- **Figure 10** (histogram, 1 panel(s), data, literature_comparison): Normalized true CMFs of the G286 protocluster, the seven IRDCs and the massive clump sample, with best WLS power-law fits, compared across the three samples.
  - axes: x: core mass M [M_sun (log scale)]; y: probability density [normalized per total core count (log scale)]
  - supports step 5
  - validation: Compares the massive clump CMF against CMFs from Papers I and II.
  - read off the plot: approx. G286 WLS alpha 1.24 plus or minus 0.17; approx. IRDC WLS alpha 0.86 plus or minus 0.11; approx. massive clump alpha 0.50 (Mmin 0.79) and 0.94 at Mmin 5 M_sun
  - reproduction target
