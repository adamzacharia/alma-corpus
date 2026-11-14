# Quantifying the detection likelihood of faint peaks in interferometric data through jackknifing: Test application on finding z &gt; 10 galaxy candidates

`2025A&A...695A.204V` | Astronomy and Astrophysics 2025 | first author: van Marrewijk, Joshiwa | arXiv: 2501.03150 | DOI: 10.1051/0004-6361/202451927

Card schema 1.0 | model claude-sonnet-5-5-claude-code | depth full | type archival_reuse

## Science

- Fields: high_z_galaxies, instrumentation
- Question: How to quantify the detection likelihood of faint line peaks in interferometric data by jackknifing visibilities, tested on tentative [O III] 88 um detections toward three z>10 galaxy candidates  
  > "Then, by applying line-finding algorithms on both the real and source-free image cubes, we sample the likelihood of a marginal detection being real without needing to assume an underlying noise distribution." (Introduction); "In this work, we present a straightforward and effective technique to quantify the detection level and underlying noise distribution in interferometric data sets." (Introduction)
- Target **GLASS-z12**: coordinates _not stated_; z/distance z_spec = 12.33 +/- 0.02  
  > "(cite: Zavala2024) detected bright nebular emission lines of GLASS-z12 with JWST, constraining the redshift to be $z_{\rm spec} = 12.33 \pm 0.02$." (5.3 Quantifying detection significance with known redshifts); distance from JWST/MRS spectrum (Zavala2024)  
  > "(cite: Zavala2024) detected bright nebular emission lines of GLASS-z12 with JWST, constraining the redshift to be $z_{\rm spec} = 12.33 \pm 0.02$." (5.3 Quantifying detection significance with known redshifts)
- Target **GLASS-z10**: coordinates _not stated_; z/distance _not stated_; distance from _not stated_
- Target **S5-z17-1**: coordinates _not stated_; z/distance _not stated_; distance from _not stated_

## Data provenance

- ALMA projects: 2021.A.00020.S, 2021.A.00023.S, 2021.A.00031.S
- bands: _not stated_
- frequencies and spectral setup: each spectral setup = four adjacent tunings covering ~30 GHz; targeting [O III] 88 um  
  > "To maximize the redshift coverage, each spectral setup consisted of four adjacent tunings, covering a large, $\approx 30$ GHz bandwidth." (2 The archival ALMA observations)
- continuum bandwidth: _not stated_
- arrays: _not stated_
- configurations: _not stated_
- baselines: _not stated_
- angular resolution: _not stated_
- max recoverable scale: _not stated_
- sensitivity: _not stated_
- time on source: _not stated_
- observing dates: _not stated_
- pi or archival as stated: archival ALMA DDT observations (Bakx2023, Yoon2023, Fujimoto2023)  
  > "We test and validate our jackknifing tool, `jackknify`, on three sets of ALMA DDT observations targeting $z>10$ galaxy candidates pre-identified from photometry" (2 The archival ALMA observations)
- Line: [O III] 88 um fine-structure line (not stated)
- Other facility **JWST/MRS**: spectroscopic redshift of GLASS-z12 (z = 12.33 +/- 0.02) used as a prior on the line frequency  
  > "(cite: Zavala2024) detected bright nebular emission lines of GLASS-z12 with JWST, constraining the redshift to be $z_{\rm spec} = 12.33 \pm 0.02$." (5.3 Quantifying detection significance with known redshifts)
- External data: Reported 5.8 sigma [O III] peak for GLASS-z12  
  > "which differs from their reported $5.8\sigma$ peak over 400 km s$^{-1}$" (5.2 Results on blind line searches) [from (cite: Bakx2023)]
- External data: Reported 5.1 sigma peak for S5-z17-1  
  > "We recover the peak reported in (cite: Fujimoto2023), albeit with a significance of $3.9\sigma$ instead of the reported $5.1\sigma$." (5.2 Results on blind line searches) [from (cite: Fujimoto2023)]
- External data: JWST/MRS redshift of GLASS-z12, z_spec = 12.33 +/- 0.02  
  > "(cite: Zavala2024) detected bright nebular emission lines of GLASS-z12 with JWST, constraining the redshift to be $z_{\rm spec} = 12.33 \pm 0.02$." (5.3 Quantifying detection significance with known redshifts) [from (cite: Zavala2024)]
- External data: Deeper GLASS-z12 observations reporting a ~4.5-5.2 sigma [O III] detection (not used in this work)  
  > "That work showed a $\approx 4.5-5.2\sigma$ detection of the" (5.3 Quantifying detection significance with known redshifts) [from (cite: Zavala2024b)]
- Simulation/model as data: Mock ALMA data from CASA simobserve: 1 h execution block, six channels at 279 GHz, 31 MHz channels, Cycle 7 configuration 4, sources with 3D Gaussian line (FWHM 80 km/s) and continuum  
  > "To validate our method, we simulated mock ALMA data using `CASA`’s `simobserve` task." (4 Application to simulated ALMA data); "The simulated data contained six channels centered at a frequency of $\nu = 279$ GHz with a channel width of 31 MHz." (4 Application to simulated ALMA data); "We created the simulated $uv$-coverage using configuration 4 from cycle 7" (4 Application to simulated ALMA data)

## Processing

### Calibration

- pipeline or manual: calibrated measurement sets delivered by European ARC network via calMS service  
  > "Calibrated measurement sets were provided by the European ALMA Regional Centre network (cite: Hatziminaoglou2015) through the calMS service (cite: Petry2020) using CASA v5.4.0." (2 The archival ALMA observations)
- casa version: CASA v5.4.0  
  > "Calibrated measurement sets were provided by the European ALMA Regional Centre network (cite: Hatziminaoglou2015) through the calMS service (cite: Petry2020) using CASA v5.4.0." (2 The archival ALMA observations)
- pipeline version: _not stated_
- archive products used as is: _not stated_
- flux calibrator: _not stated_
- flux scale uncertainty: _not stated_
- self calibration: _not stated_

### Imaging

- task: tclean  
  > "Finally, we imaged all measurement sets using the TCLEAN task with natural weighting." (2 The archival ALMA observations)
- deconvolver: _not stated_
- weighting robust: natural weighting  
  > "Finally, we imaged all measurement sets using the TCLEAN task with natural weighting." (2 The archival ALMA observations)
- uv taper: _not stated_
- cell size: _not stated_
- image size: _not stated_
- masking: _not stated_
- multiscale scales: _not stated_
- continuum subtraction: uvcontsub, first-order polynomial  
  > "We used `uvcontsub` to manually continuum subtract a first-order polynomial from the measurement sets to remove any potential continuum emitters." (2 The archival ALMA observations)
- line free channels: channels with previously reported tentative features omitted from the fit; channel ranges not given  
  > "We omitted the frequency channels where tentative features might be present in the data based on the previously reported detections." (2 The archival ALMA observations)
- primary beam correction: maps not primary-beam corrected  
  > "This is a reasonable assumption, as there should be no correlation between the $S/N$ of the line detection and these parameters for non-primary-beam-corrected maps." (5.3 Quantifying detection significance with known redshifts)
- array combination: _not stated_
- smoothing: _not stated_
- final beam: _not stated_
- final rms: _not stated_

### Inherited from earlier work

- Jackknifing approach of differencing visibilities to build noise realizations  
  > "We build upon the approach used in (cite: Kaasinen2023); by differencing the visibilities, we generate various noise realizations of the observation-specific ALMA measurement set." (Introduction) [from (cite: Kaasinen2023)]
- FindClump line finder as implemented in interferopy  
  > "We use `FindClump` (cite: Walter2016), as implemented in the `interferopy` package (cite: interferopy), to sample the distribution of positive peak values from both the real and jackknifed data." (5.1 Specific experiment set up) [from (cite: Walter2016); (cite: interferopy)]
- SExtractor default settings, modified (analysis and detection thresholds set to 2)  
  > "we have modified the default settings in `SExtractor` (cite: Bertin1996), specifically the analysis and detection thresholds which we both set to 2 to better detect low $S/N$ clumps." (5.1 Specific experiment set up) [from (cite: Bertin1996)]
- Flat LCDM cosmology with H0 = 67.7 km/s/Mpc, Omega_m = 0.307  
  > "the assumed cosmology is based on (cite: Planck2014_XIII), a spatially flat, $\Lambda$ cold dark matter ($\Lambda$CDM) model with $H_0=67.7$  kms$^{-1}$ Mpc$^{-1}$ and $\Omega_{\rm m} = 0.307$." (Introduction) [from (cite: Planck2014_XIII)]

### Not stated but needed to reproduce (our reading)

- Exact line-free channel ranges excluded before uvcontsub for each of the three sources
- tclean parameters other than natural weighting: cell size, image size, deconvolver, niter, threshold, mask, channel width per source (only 46 km/s given for GLASS-z12)
- Optical/JWST centre coordinates used for the 0.6 arcsec mask for GLASS-z10 and S5-z17-1 (only a table, not text)
- Random seeds used for the 50 jackknife realizations
- Full FindClump/interferopy parameter settings beyond width range, S/N cut and duplicate-cropping radii
- How the peak PDFs are binned in S/N and how the L_FD integral and its uncertainty are computed
- Whether any bright sources were removed from the visibilities before jackknifing (S/N>50 advice)
- Flux calibrators and whether the archive calMS calibration was used unchanged for each project

## Analysis recipe

1. **Prepare calibrated visibilities**: Average calibrated visibilities in time and frequency, subtract a first-order continuum with uvcontsub, then image with tclean  
  > "we performed two additional operations on the calibrated data, applying a time averaging of 30 seconds and spectral averaging of the visibilities in $\approx 30$ MHz bins." (2 The archival ALMA observations); "We used `uvcontsub` to manually continuum subtract a first-order polynomial from the measurement sets to remove any potential continuum emitters." (2 The archival ALMA observations)
   - software: CASA, uvcontsub, tclean
   - parameter: time averaging 30 s; spectral averaging ~30 MHz bins without interpolation on the frequency axis  
  > "The frequency binning was conducted in a manner that avoided interpolation over the frequency axis." (2 The archival ALMA observations)
   - parameter: natural weighting  
  > "Finally, we imaged all measurement sets using the TCLEAN task with natural weighting." (2 The archival ALMA observations)
   - fitting: _not stated_
   - validation: _not stated_
2. **Generate jackknife noise realizations**: Randomly flip the sign of half of the visibilities in the visibility plane with different random seeds, then re-image each realization with the same imaging as the real data  
  > "by randomly multiplying half of the real and imaginary amplitudes of the visibilities by -1 and then rebinning, thereby averaging out the signal" (3.1 Jackknifing); "Resampling the noise distributions requires that the cubes are re-imaged at every iteration." (3.1 Jackknifing)
   - software: jackknify, CASA, tclean
   - parameter: 50 jackknife realizations per observation, ~9 min per iteration on a 2019 MacBook Pro  
  > "from $\approx$ 50 realizations onward we recover the high-$S/N$ tail of the distribution; we decided to use 50 jackknife realizations throughout this work" (3.2.2 / 5.1); "takes $\approx 9$ minutes on a 2019 MacBook Pro with a 2.6 GHz 6-Core Intel Core i7 processor." (5.1 Specific experiment set up)
   - assumption: Visibility noise is additive, Gaussian, uncorrelated and zero-mean for well-calibrated data  
  > "noise in the Fourier domain, unlike in the image plane, is additive and Gaussian" (3.1 Jackknifing)
   - fitting: _not stated_
   - validation: Mock simobserve data show jackknife realizations match the noise structure and standard deviation of cleaned noise maps for source S/N below ~50  
  > "The simulated noise map and jackknifed realization exhibit the same noise structure, validating our jackknifing approach." (4 Application to simulated ALMA data); "We find that our jackknifing approach is perfectly reliable for $S/N \lesssim 50$." (4 Application to simulated ALMA data)
3. **Find peaks in real and jackknifed cubes**: Run FindClump (interferopy, SExtractor-based) on the real cube and each jackknifed cube, keep positive peaks within 0.6 arcsec of the optical centre, to build P_D and P_FD  
  > "We use `FindClump` (cite: Walter2016), as implemented in the `interferopy` package (cite: interferopy), to sample the distribution of positive peak values from both the real and jackknifed data." (5.1 Specific experiment set up); "We mask out features outside a $0.6\ensuremath{''}$ radius of the optically derived center." (5.1 Specific experiment set up)
   - software: FindClump, interferopy, SExtractor
   - parameter: line widths 100-500 km/s (3-11 channel widths)  
  > "we configure `FindClump` to search for emission lines with widths between $100 - 500$ km s$^{-1}$, corresponding to $3-11$ times the channel width." (5.1 Specific experiment set up)
   - parameter: peaks above S/N of 0 retained; duplicates merged within 0.2 arcsec and 0.2 GHz  
  > "With `FindClump`, we identify peaks that exceed a signal-to-noise ratio ($S/N$) of 0" (5.1 Specific experiment set up); "and within 0.2 GHz spectrally (roughly $4-5$ channels apart)." (5.1 Specific experiment set up)
   - parameter: SExtractor analysis and detection thresholds both set to 2  
  > "specifically the analysis and detection thresholds which we both set to 2 to better detect low $S/N$ clumps." (5.1 Specific experiment set up)
   - fitting: _not stated_
   - validation: On simulated data FindClump on 50 jackknife realizations gave a smooth noise peak distribution and recovered the injected S/N = 4.9 sources  
  > "By applying the line-finding algorithm to the real data (orange histogram), we recover the simulated continuum and lines sources, both with a $S/N = 4.9$." (4 Application to simulated ALMA data)
4. **Likelihood ratio test for blind line detection**: Compute false-detection likelihood L_FD(gamma) from jackknifed peak PDF, multiply by number of real peaks for expected noise count, and form Lambda = L_D/L_FD; significant if Lambda >= k = 3  
  > "Finally, an excess in the ratio is considered significant if the likelihood ratio exceeds a critical value $k$" (3.2.2 Line detection inference through jackknifing); "We consider a detection to be significant if the excess of peaks in the real data with respect to the noise has at least a significance of $2\sigma$ based on Poisson statistics." (5.1 Specific experiment set up)
   - software: jackknify, FindClump
   - parameter: detection threshold gamma = 4 sigma, critical value k = 3  
  > "This does not exceed our detection threshold of $k = 3$" (5.2 Results on blind line searches)
   - assumption: Jackknifed peaks sample the false-detection distribution; peak distribution is a subset of the pixel-value distribution of a smoothed random Gaussian field  
  > "can be approximated as a smoothed random Gaussian field." (3.2.2 Line detection inference through jackknifing)
   - fitting: _not stated_
   - validation: Jackknifed negative-peak PDF compared with the real data; scatter within the 95% interval is consistent with Poisson uncertainty  
  > "the scatter in the jackknife realizations within the 95% confidence interval is consistent with the Poisson uncertainty in the real data for each bin" (3.2.2 Line detection inference through jackknifing)
5. **Apply JWST redshift prior to GLASS-z12**: Multiply the PDFs by Gaussian prior on redshift, uniform prior on radial distance and uniform prior on peak S/N in post-processing with Bayes theorem, then renormalise  
  > "we adopt a Gaussian prior on the redshift" (5.3 Quantifying detection significance with known redshifts); "and a uniform prior on the $S/N$ of the peak" (5.3 Quantifying detection significance with known redshifts)
   - software: jackknify, FindClump
   - parameter: Gaussian redshift prior mu = 12.33, sigma = 0.02 (+/-0.4 GHz at 254.54 GHz); uniform radial prior 0 to 0.6 arcsec; uniform S/N prior from 2.5; only peaks with S/N > 2.5 counted  
  > "thereby only counting peaks with $S/N > 2.5$." (5.3 Quantifying detection significance with known redshifts); "The redshift uncertainty ($\Delta z = \pm 0.02$) derived from the JWST/MRS spectrum of GLASS-z12 translates to a frequency width of $\Delta \nu_{\rm obs} = \pm 0.4$ GHz" (5.3 Quantifying detection significance with known redshifts)
   - assumption: No correlation between peak S/N and its RA, Dec or frequency position for non-primary-beam-corrected maps  
  > "This approach assumes no correlation between the $S/N$ of a candidate (since the intrinsic flux of the source is unknown) and its location along the RA, Dec, and frequency axes." (5.3 Quantifying detection significance with known redshifts)
   - fitting: No MCMC; PDFs sampled first without priors, Bayes theorem applied afterwards  
  > "Unlike methods such as Markov Chain Monte Carlo, which directly sample the posterior distribution, we first sampled the PDFs using `FindClumps` without applying any priors." (5.3 Quantifying detection significance with known redshifts)
   - validation: PDF of false detections is flat in frequency, supporting the independence assumption  
  > "The latter indicates that the PDF has a flat distribution with respect to frequency" (5.3 Quantifying detection significance with known redshifts)

## Software

- **CASA** v5.4.0: Calibration of delivered measurement sets, uvcontsub, tclean imaging and simobserve simulations  
  > "Calibrated measurement sets were provided by the European ALMA Regional Centre network (cite: Hatziminaoglou2015) through the calMS service (cite: Petry2020) using CASA v5.4.0." (2 The archival ALMA observations)
- **jackknify** 1.0.0: Public tool that jackknifes visibilities and re-images realizations via CASA tclean  
  > "We make our technique readily available to the community in the form of the public tool `jackknify`, along with clear, step-by-step tutorials." (Introduction)
- **jaxknify** : jax-based iFFT implementation used only to compute the many realizations in Figure 5  
  > "`jaxknify` was only used to compute the many realizations which are visualized in Figure [5](#fig:test_simobs)" (Footnote 5)
- **FindClump** : Line finding in real and jackknifed cubes, through interferopy  
  > "We use `FindClump` (cite: Walter2016), as implemented in the `interferopy` package (cite: interferopy), to sample the distribution of positive peak values from both the real and jackknifed data." (5.1 Specific experiment set up)
- **interferopy** : Package providing the FindClump implementation  
  > "as implemented in the `interferopy` package (cite: interferopy)" (5.1 Specific experiment set up)
- **SExtractor** : Peak detection with modified thresholds inside FindClump  
  > "we have modified the default settings in `SExtractor` (cite: Bertin1996)" (5.1 Specific experiment set up)
- **tclean** : Imaging of real and jackknifed measurement sets with natural weighting  
  > "Finally, we imaged all measurement sets using the TCLEAN task with natural weighting." (2 The archival ALMA observations)
- **uvcontsub** : First-order polynomial continuum subtraction in the visibility plane  
  > "We used `uvcontsub` to manually continuum subtract a first-order polynomial from the measurement sets to remove any potential continuum emitters." (2 The archival ALMA observations)
- **simobserve** : Generating mock ALMA observations for validation  
  > "To validate our method, we simulated mock ALMA data using `CASA`’s `simobserve` task." (4 Application to simulated ALMA data)

## Numeric results

| quantity | value | uncertainty | units | step | quote |
|---|---|---|---|---|---|
| GLASS-z12 expected noise peaks above S/N 4 (L_FD x N_peaks, N_peaks = 1150) | 1.3 | 1.1 | peaks | 4 | = 0.0011 \times 1150 = 1.3 \pm 1.1 |
| GLASS-z12 likelihood ratio Lambda(4 sigma) | 0.80 | not stated | dimensionless | 4 | which results in $\Lambda(4\sigma) = \mathcal{L}_{\rm D}(4\sigma) / \mathcal{L}_{\rm FD}(4\sigma) = 0.80$ |
| GLASS-z12 reported 5.8 sigma peak recovered at lower significance | 2.9 sigma, linewidth 280 km/s | not stated | sigma | 4 | We recover a peak at the same location but at a lower significance of $2.9\sigma$ for a linewidth of 280 km s$^{-1}$ |
| GLASS-z10 expected noise peaks at gamma > 4 sigma (N_peaks = 271) | 1.5 | 1.2 | peaks | 4 | we expect to find $1.5 \pm 1.2$ peaks at $\gamma > 4\sigma$ |
| GLASS-z10 likelihood ratio Lambda(4 sigma) | 1.4 | not stated | dimensionless | 4 | The likelihood ratio resulted in $\Lambda(\gamma = 4\sigma) = 1.4$. |
| GLASS-z10 previously reported 2.7 sigma line: L_FD and Lambda | L_FD = 0.19, Lambda = 0.9 | not stated | dimensionless | 4 | This line has a false detection likelihood of $\mathcal{L}_{\rm FD}(\gamma=2.7\sigma) = 0.19$ and a likelihood ratio test resulting in $\Lambda(\gamma = 2.7\sigma) = 0.9$. |
| S5-z17-1 expected noise peaks above S/N 4 (N_peaks = 221) | 0.7 | 0.8 | peaks | 4 | = 0.0032 \times 221= 0.7 \pm 0.8 |
| S5-z17-1 likelihood ratio Lambda(4 sigma) | 1.4 | not stated | dimensionless | 4 | since $\Lambda(\gamma=4\sigma) = 1.4$ |
| S5-z17-1 reported peak recovered: S/N and Lambda | 3.9 sigma, L_FD = 0.0060, Lambda = 2.2 | not stated | dimensionless | 4 | This line has a false detection likelihood of $\mathcal{L}_{\rm FD}(\gamma=3.9\sigma) = 0.0060$ and a likelihood ratio test resulting in $\Lambda(\gamma = 3.9\sigma) = 2.2$. |
| GLASS-z12 Lambda with JWST redshift prior (gamma = 2.5 sigma) | 1.64 | not stated | dimensionless | 5 | the likelihood ratio test results in $\Lambda(\gamma=2.5\sigma)= 1.64$. |
| Simulated data Lambda(gamma = 4.0) | 13 | not stated | dimensionless | 4 | the likelihood ratio tests yield $\Lambda(\gamma = 4.0) = 13$. |
| Expected spurious line features at S/N ~4-5 in broad ALMA line scans | ~3 | 2 | features | 4 | we expect to find approximately $3 \pm 2$ line features with $S/N \sim 4-5$ in broad ALMA line scans |

## Qualitative findings

- The highest-significance peaks found in the three datasets differ from the previously reported peaks, and the difference in S/N and linewidth for GLASS-z12 is attributed to different imaging choices  
  > "The difference in S/N and linewidth is due to the difference in how the data were imaged." (5.2 Results on blind line searches)
- Because many peaks are searched, a 5 sigma fluke occurs within a few hundred to a thousand peaks  
  > "Given the number of peaks per data set, the detection significance does not follow a Gaussian distribution." (5.2 Results on blind line searches)

## Claim tuples

- H: Jackknifing visibilities reproduces the true interferometric noise distribution | E: Compared jackknife realizations with cleaned noise maps in simobserve mock data over many seeds and source S/N | R: Jackknife realizations match the noise structure and standard deviation for source S/N below ~50 | F: Jackknifing allows accurate estimation of the underlying noise distribution | **supported**
- H: Previously reported tentative [O III] 88 um detections toward GLASS-z12, GLASS-z10 and S5-z17-1 are real | E: Blind FindClump line search on real vs 50 jackknifed cubes, likelihood ratio test with k = 3 | R: Lambda(4 sigma) = 0.80, 1.4, 1.4, all below k = 3 | F: No significant detection in any of the three datasets; peaks consistent with noise | **refuted**
- H: A JWST redshift prior reveals a real [O III] line in the GLASS-z12 ALMA data | E: Applied Gaussian prior on redshift (12.33 +/- 0.02) and spatial/S/N priors to the peak PDFs | R: Lambda(2.5 sigma) = 1.64 for two peaks at S/N 2.7 and 2.6, below k = 3 | F: Even with the JWST prior the ALMA data are statistically consistent with noise | **refuted**
- H: Jackknifing samples the false-positive distribution better than negative peaks in the real data | E: Compared the negative-peak PDF in real data with 50 jackknife realizations | R: Jackknifing gives better statistics, especially at high S/N | F: More complete sampling of the noise distribution without complex noise models | **supported**
- H: Blind line scans of ~30 GHz need a high threshold for secure detection | E: Counted jackknife peaks across datasets with N_peaks of ~200-1000 | R: About 3 +/- 2 spurious features at S/N ~4-5 expected per broad scan | F: Blind single-line detections need more than 5 sigma | **supported**

## Reasoning

- Why this data: Test the tool in two scenarios: no redshift knowledge, and a JWST frequency prior  
  > "We will test two scenarios: one in which no prior knowledge regarding the source’s redshift is available and one in which we can use a prior from JWST on the frequency location of the line." (Introduction)
- Why this method: Jackknifing in the visibility plane keeps correlated noise produced by the Fourier transform  
  > "Jackknifing in the visibility plane is thus essential, rather than splitting in the image plane, to avoid removing any correlated noise induced by the Fourier transform present in the data." (3.1 Jackknifing)
- Alternative: HD1 DDT observations excluded because it was spectroscopically shown to be a passive galaxy at z = 4.0 and had a similar analysis already  
  > "we exclude these observations here as more recent work by (cite: Harikane2024b) spectroscopically confirmed the object to be a passive galaxy at $z=4.0$" (5 Application to z>10 galaxy candidates)
- Alternative: Empirical fidelity (negative-peak) method rejected because absorption or bright sources create negative signal that contaminates the noise statistics  
  > "However, this does not hold when absorption with respect to the CMB or a bright background source leads to negative line fluxes, contaminating the noise statistics." (3.2.1 Traditional empirical methods)
- Alternative: jaxknify not used for the science analysis because its output is not compatible with existing line finders  
  > "The output of the Fourier Transform is, however, not compatible with existing line-find methods." (3.1 Jackknifing)
- How they decided it was enough: 50 realizations chosen as trade-off between tail sampling and computation time  
  > "from $\approx$ 50 realizations onward we recover the high-$S/N$ tail of the distribution; we decided to use 50 jackknife realizations throughout this work" (3.2.2 Line detection inference through jackknifing)
- Limitation (authors): Not evaluated for large extended bright emission  
  > "We note that we did not evaluate the performance of jackknifing the visibilities in cases of large extended bright emission such as in molecular clouds within low-redshift galaxies." (Footnote 6)
- Limitation (authors): Validated only with the w-term neglected  
  > "However, we do note that our tools are validated only on data where the $w$-term was neglected." (Footnote 3)
- Limitation (authors): Computationally intensive for large data sets; bright sources (S/N > 50) must be removed first  
  > "Because of this, `jackknify` can become computationally intensive, particularly for large data sets." (3.1 Jackknifing); "one should remove extremely bright continuum and line-emitting sources (e.g., $S/N>50$) from the data set in the visibility plane" (4 Application to simulated ALMA data)
- Caveat (inferred, ours): Result depends on line-finder choice and imaging (natural weighting, 46 km/s channels) that differ from the original papers' tapered, coarser imaging, so S/N is not directly comparable
- Caveat (inferred, ours): Detection threshold k = 3 and 4 sigma gamma are chosen thresholds; Poisson-limited peak counts of 1-2 give weak statistical power
- Caveat (inferred, ours): Only three sources and a single line finder; the 0.6 arcsec aperture and S/N prior choices shape the result
- Caveat (inferred, ours): Later, deeper GLASS-z12 data (Zavala2024b) show a detection, so the null result applies to the older data only

## Reproducibility

- Data public (paper): Archival ALMA DDT data from three projects  
  > "In this work, we apply `jackknify` to three archival DDT observations targeting $z>10$ galaxy candidates." (Introduction)
- Products in archive: Calibrated measurement sets obtained from calMS service of the European ARC network  
  > "Calibrated measurement sets were provided by the European ALMA Regional Centre network (cite: Hatziminaoglou2015) through the calMS service (cite: Petry2020) using CASA v5.4.0." (2 The archival ALMA observations)
- Code: jackknify public tool with tutorials, installable via pip  
  > "We make our technique readily available to the community in the form of the public tool `jackknify`, along with clear, step-by-step tutorials." (Introduction); "the tool, `jackknify`, is installable using pip" (6 Summary & Implications)
- Missing: Exact line-free channel selection, tclean cell/image size and channel widths per source
- Missing: Random seeds and FindClump parameter file
- Missing: Coordinates of the optical centres used for the 0.6 arcsec mask for two of the sources
- Data volume (inferred): Three DDT datasets with ~30 GHz spectral scans at 31 MHz channels after averaging; probably a few to tens of GB of calibrated visibilities, plus 50 re-imaged cubes per dataset (~9 min each)
- Score (inferred): 4/5, Public archival data, public code and a clear step-by-step recipe with numeric tables; some imaging and line-finder settings are unstated.
- Rediscovery candidate: yes, Data are archival and calibrated MS are available, the tool is public, and main results are numeric (Lambda, L_FD, expected peak counts).

## Links

- Method: (cite: Kaasinen2023) (Original jackknifing of ALMA visibilities that this work builds upon)
- Method: (cite: Walter2016) (FindClump line finder)
- Method: (cite: CASA2022) (CASA software used for imaging and simulation)
- Companion: (cite: Bakx2023) (GLASS-z12 ALMA DDT observations and original tentative detection)
- Companion: (cite: Yoon2023) (GLASS-z10 ALMA DDT observations)
- Companion: (cite: Fujimoto2023) (S5-z17-1 ALMA DDT observations)
- Companion: (cite: Zavala2024) (JWST/MRS redshift of GLASS-z12 used as prior)
- Companion: (cite: Zavala2024b) (Deeper ALMA observations of GLASS-z12, not included here)
- Related: ALMA Director's Discretionary Time programs on z>10 candidates
- Related: ASPECS

## Checks

```json
{
 "quotes": 104,
 "quotes_ok": 104,
 "quote_pass_rate": 1.0,
 "quotes_too_long": 0,
 "unsupported_facts": 0,
 "project_codes": 3,
 "codes_not_in_text": [],
 "codes_not_in_obscore": [],
 "obscore_codes_not_in_card": [
  "2023.A.00017.S",
  "2023.A.00037.S"
 ],
 "codes_printed_but_missing": [
  "2023.A.00017.S"
 ],
 "numeric_results": 12,
 "numeric_problems": 0,
 "fill": {
  "facts": 103,
  "stated": 66,
  "rate": 0.641
 },
 "evidence_ok": true
}
```
