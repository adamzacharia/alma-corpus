# Dead or Alive? How Bursty Star Formation and Patchy Dust Can Cause Temporary Quiescence in High-redshift Galaxies

`2024ApJ...971...47F` | The Astrophysical Journal 2024 | first author: Faisst, Andreas L. | arXiv: 2402.13316 | DOI: 10.3847/1538-4357/ad58e2

Card schema 1.0 | model claude-sonnet-5-5-claude-code | depth light | type theory_or_simulation_compared_to_alma

## Science

- Fields: high_z_galaxies
- Question: Can stochastic star formation histories and/or spatially varying dust attenuation explain the lack of optical emission lines plus blue UV-to-optical ratio of the z=7.3 galaxy JADES-GS-z7-01-QU?  
  > "In this study, we aim at explaining the observation of a galaxy such as JADES-GS-z7-01-QU by two (not mutually exclusive) ideas" (Introduction)
- Target **JADES-GS-z7-01-QU**: coordinates _not stated_; z/distance z = 7.3 (spectroscopic)  
  > "at a spectroscopic redshift of $z=7.3$ reported by (cite: looser23)" (Introduction); distance from JWST/NIRSpec spectroscopy of Looser et al. (cite: looser23)  
  > "at a spectroscopic redshift of $z=7.3$ reported by (cite: looser23)" (Introduction)

## Data provenance

- ALMA projects: 2023.1.00521.S
- bands: _not stated_
- frequencies and spectral setup: _not stated_
- continuum bandwidth: _not stated_
- arrays: _not stated_
- configurations: _not stated_
- baselines: _not stated_
- angular resolution: _not stated_
- max recoverable scale: _not stated_
- sensitivity: _not stated_
- time on source: _not stated_
- observing dates: _not stated_
- pi or archival as stated: Upcoming (future) ALMA program 2023.1.00521.S, PI: Faisst; no ALMA data analysed in this paper  
  > "Upcoming observations with ALMA of the far-infrared continuum and the C II line emission (#2023.1.00521.S, PI: Faisst)" (Summary & Conclusions)
- Line: C II not stated (planned ALMA observation, not analysed here) (not stated)
- Other facility **JWST (NIRCam, NIRSpec)**: Spectrum and photometry of JADES-GS-z7-01-QU defining the observed conditions; NIRCam images (F115W, F210M, F410M) used for a colour composite  
  > "Some of the data presented in this article were obtained from the Mikulski Archive for Space Telescopes (MAST) at the Space Telescope Science Institute." (Acknowledgements); "Specifically, we observe two conditions (cite: looser23):" (2 Quiescence in Stochastic Star Formation Histories)
- Other facility **SPHINX^20 cosmological radiation hydrodynamic simulation**: Simulated SFHs of 177 galaxies at z=7 and E(B-V) along 10 sight lines per galaxy  
  > "we use more realistic SFH histories from simulations from the newly released SPHINX" (2.3 Comparison to Simulations at z=7)
- External data: JWST/NIRSpec and NIRCam observed properties of JADES-GS-z7-01-QU defining Conditions 1 and 2 (no [O II]/[O III] at >3 sigma; UV-to-optical flux ratio 3+-0.3)  
  > "Specifically, we observe two conditions (cite: looser23):" (2 Quiescence in Stochastic Star Formation Histories) [from Looser et al. (cite: looser23)]
- External data: Fiducial burstiness sigma_MS = 0.5-0.6 dex  
  > "Assuming a fiducial $\sigma_{\rm MS} = 0.5-0.6\,{\rm dex}$ (cite: faisst19; looser23; popesso23; mehta23; cole23)" (2.2.2 How likely is it to observe JADES-GS-z7-01-QU?) [from (cite: faisst19; looser23; popesso23; mehta23; cole23)]
- External data: alpha = 2 (damped random walk) PSD slope, with observational evidence  
  > "see (cite: caplar19) for observational evidence" (2.2.2 How likely is it to observe JADES-GS-z7-01-QU?) [from (cite: caplar19)]
- External data: SPHINX^20 simulation outputs (SFHs and sight-line E(B-V))  
  > "For more information on the details of this simulation, we refer to (cite: katz23)." (2.3 Comparison to Simulations at z=7) [from (cite: katz23)]
- External data: Differential dust attenuation factors f = 0.44 and f = 0.7, and starburst reddening curve  
  > "for two differential dust attenuation values of $f=0.44$ (cite: calzetti00) and $0.7$ (cite: kashino13)" (3 Impact of Dust Attenuation on Observed Quiescence) [from (cite: calzetti00); (cite: kashino13)]
- External data: Observed rate of about one mini-quenched galaxy among ~40 star-forming galaxies at 5<z<11, used for comparison  
  > "This is roughly consistent with the work by (cite: looser23b)" (2.3 Comparison to Simulations at z=7) [from (cite: looser23b)]
- Simulation/model as data: SPHINX^20 simulation: SFHs of 177 galaxies in the z=7 slice, plus 10 sight-line E(B-V) measurements per galaxy  
  > "we extract the SFHs of all $177$ galaxies (or halos) in the $z=7$ redshift slice" (2.3 Comparison to Simulations at z=7); "The SPHINX$^{\rm 20}$ simulation release provides a set of measurements along $10$ different sight lines for each of the simulated galaxies." (3 Impact of Dust Attenuation on Observed Quiescence)
- Simulation/model as data: Synthetic stochastic SFHs from a damped-random-walk-type PSD, turned into spectra with FSPS  
  > "Synthetic spectra are derived using the Flexible Stellar Population Synthesis (cite: conroy09; conroy10) code" (2.2.1 Synthetic spectra derived from stochastic SFHs)

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
- primary beam correction: _not stated_
- array combination: _not stated_
- smoothing: _not stated_
- final beam: _not stated_
- final rms: _not stated_

### Inherited from earlier work

- Approach to create stochastic model SFHs  
  > "Here, we use an approach similar to (cite: caplar19) to create model SFHs with different statistical properties." (2.2.1 Synthetic spectra derived from stochastic SFHs) [from (cite: caplar19)]
- Details of the SPHINX^20 simulation  
  > "For more information on the details of this simulation, we refer to (cite: katz23)." (2.3 Comparison to Simulations at z=7) [from (cite: katz23)]
- Definition of the observed Conditions 1 and 2 for JADES-GS-z7-01-QU  
  > "Specifically, we observe two conditions (cite: looser23):" (2 Quiescence in Stochastic Star Formation Histories) [from (cite: looser23)]

### Not stated but needed to reproduce (our reading)

- Wavelength windows used to define the UV and optical lambda f_lambda flux ratio and the [O III] SNR calculation
- FSPS/python-fsps version and full parameter set (SFH sampling grid, age grid, dust settings, exact metallicity)
- Random seeds and number of realisations per (tau_break, sigma) cell; PSD normalisation
- How the PSD was fit to the SPHINX SFHs (algorithm, priors, binning)
- Access route and snapshot of the SPHINX^20 SFHs and sight-line E(B-V) used
- Stellar-mass ratio, SFH normalisation and covering of the blue and red components of the composite spectrum
- Galfit configuration (PSF, fit region, components) for the NIRCam decomposition
- Monte Carlo details for the 2.8% estimate (sampling distributions for the number and duration of quiescent phases)

## Analysis recipe

1. **Single starburst plus passive evolution test**: Model a single burst, compute UV-to-optical flux ratio and [O III] SNR versus time after burst, and place it on the UVJ diagram  
  > "This condition can be reproduced by a single starburst" (2.1 Single Burst)
   - software: FSPS
   - parameter: Burst SFR 10 Msun/yr, length 50 Myr  
  > "we assume a burst with a SFR of $10\,{\rm M_\odot\,yr^{-1}}$ and a length of $50\,{\rm Myrs}$" (2.1 Single Burst)
   - assumption: No dust attenuation; previous star formation negligible  
  > "Furthermore, we do not assume dust attenuation in this simple model." (2.1 Single Burst)
   - fitting: _not stated_
   - validation: Model colours compared with the observed UVJ colours and spectrum of JADES-GS-z7-01-QU  
  > "and they agree well with the burst$+$passive evolution model right at the end of the burst." (2.1 Single Burst)
2. **Generate stochastic SFHs and synthetic spectra**: Simulate SFHs from a damped-random-walk-type PSD with DELightcurveSimulation, then compute spectra with FSPS  
  > "we assume a generalized power spectrum density (PSD) based on a damped random walk" (2.2.1 Synthetic spectra derived from stochastic SFHs); "which is based on the (cite: emmanoulopoulos13) light curve simulation algorithm" (2.2.1 Synthetic spectra derived from stochastic SFHs)
   - software: DELightcurveSimulation, FSPS, Python-FSPS
   - parameter: Emission lines on with log U = -2; 10-50% solar metallicity of gas and stars  
  > "We enable emission lines (with $\log U = -2$), assume a $10-50\%$ solar metallicity of gas and stars" (2.2.1 Synthetic spectra derived from stochastic SFHs)
   - parameter: STELIB library complements the Basel library  
  > "complemented by the empirical STELIB library (cite: leborgne03)" (2.2.1 Synthetic spectra derived from stochastic SFHs)
   - assumption: Chabrier (2003) IMF for stellar masses and SFRs  
  > "stellar masses and SFRs are normalized to a (cite: chabrier03) initial mass function (IMF)." (1 Introduction)
   - fitting: _not stated_
   - validation: _not stated_
3. **Probability of observing a JADES-GS-z7-01-QU analog in stochastic SFHs**: Count 30 Myr time slices meeting condition 1 or conditions 1+2 within a 500 Myr window for grids of tau_break and sigma_MS  
  > "The number of $30\,{\rm Myr}$ time-slices that meet either condition 1 or both conditions $1+2$ are then computed within a $500\,{\rm Myr}$ time window" (2.2.2 How likely is it to observe JADES-GS-z7-01-QU?)
   - software: DELightcurveSimulation, FSPS
   - parameter: tau_break 50 to 500 Myrs; sigma = 0.4, 0.6, 0.8 dex; several 1000 spectra  
  > "we create several 1000 synthetic spectra for various $\tau_{\rm break}$ from 50 to 500 Myrs and $\sigma~=~0.4,0.6,0.8\,{\rm dex}$" (2.2.2 How likely is it to observe JADES-GS-z7-01-QU?)
   - parameter: alpha fixed to 2; redshift z=7.3  
  > "Furthermore, we fix $\alpha=2$ (see (cite: caplar19) for observational evidence) and the redshift is assumed to be $z=7.3$." (2.2.2 How likely is it to observe JADES-GS-z7-01-QU?)
   - assumption: Fiducial sigma_MS = 0.5-0.6 dex to break the tau_break and sigma_MS degeneracy  
  > "We can break this degeneracy by fixing $\sigma_{\rm MS}$" (2.2.2 How likely is it to observe JADES-GS-z7-01-QU?)
   - fitting: _not stated_
   - validation: _not stated_
4. **Fit the PSD to SPHINX^20 SFHs**: Normalise SFHs to their mean SFR (2-degree polynomial) to get sigma_MS, then fit the PSD model to get tau_break and alpha  
  > "The SFHs are then normalized to their mean SFR (fit by a 2-degree polynomial) to obtain an estimate for $\sigma_{\rm MS}$." (2.3 Comparison to Simulations at z=7); "The resulting normalized SFHs are then fit with the PSD model described in" (2.3 Comparison to Simulations at z=7)
   - parameter: 177 galaxies (halos) in the z=7 slice  
  > "we extract the SFHs of all $177$ galaxies (or halos) in the $z=7$ redshift slice" (2.3 Comparison to Simulations at z=7)
   - fitting: _not stated_
   - validation: Recovery test on several 100 simulated SFHs; true tau_break recovered to better than 50% uncertainty  
  > "We verified the fitting method by simulating several $100$ SFHs for various $\tau_{\rm break}$ and $\alpha$ parameters, which we fit with the same methods." (2.3 Comparison to Simulations at z=7); "we are able to recover the true $\tau_{\rm break}$ to better than $50\%$ uncertainty independent of the input $\alpha$ value." (2.3 Comparison to Simulations at z=7)
5. **Occurrence fraction and survey size from SPHINX^20**: Synthetic spectra from the SPHINX^20 SFHs with the same recipe, then a Monte Carlo estimate of the chance of observing a galaxy in a quiescent phase at z=7  
  > "by simulating synthetic spectra from the SFHs of the SPHINX$^{\rm 20}$ galaxies directly" (2.3 Comparison to Simulations at z=7); "evaluate the likelihood that a galaxy is observed in a quiescent phase at $z=7$ based on 1000 samplings" (2.3 Comparison to Simulations at z=7)
   - software: FSPS
   - parameter: 70% of galaxies quiescent within 500 Myr  
  > "we assume that $70\%$ of galaxies go through a temporary quiescent within $500\,{\rm Myrs}$" (2.3 Comparison to Simulations at z=7)
   - parameter: Quiescent phase occurs on average twice and lasts 10 Myr  
  > "the quiescent phase occurs on average twice within that time and lasts on average for $10\,{\rm Myrs}$" (2.3 Comparison to Simulations at z=7)
   - assumption: Galaxies lived for at least 500 Myr  
  > "With the caveat that we assume that the galaxies lived for at least $500\,{\rm Myrs}$." (2.3 Comparison to Simulations at z=7)
   - fitting: _not stated_
   - validation: Compared with an observed rate of one mini-quenched galaxy among about 40 star-forming galaxies  
  > "This is roughly consistent with the work by (cite: looser23b)" (2.3 Comparison to Simulations at z=7)
6. **Decompose NIRCam image into two components**: Fit two components in the blue NIRCam filters with Galfit, convolve model images with the F115W PSF and combine into an RGB image  
  > "we fit the two components (visible in the blue filters, see insets) using" (3 Impact of Dust Attenuation on Observed Quiescence); "The model images are then convolved by the F115W PSF and combined to an RGB image." (3 Impact of Dust Attenuation on Observed Quiescence)
   - software: Galfit
   - parameter: Positional priors based on F115W  
  > "with positional priors based on F115W" (3 Impact of Dust Attenuation on Observed Quiescence)
   - fitting: _not stated_
   - validation: _not stated_
7. **Blue plus red composite spectrum and MIRI predictions**: Combine a young dust-free density-bounded blue component with a dust-obscured post-starburst red component; apply differential attenuation; convolve with MIRI filters  
  > "We model the blue component as a young ($40\,{\rm Myr}$), constant star-forming dust-free UV-emitting region" (3 Impact of Dust Attenuation on Observed Quiescence); "the red component is modeled as a post-starburst $60\,{\rm Myr}$ old dust-obscured region" (3 Impact of Dust Attenuation on Observed Quiescence)
   - software: FSPS
   - parameter: E(B-V) = 0.6 mag for the red component  
  > "If E(B-V) = 0.6 mag (lower panel), the composite spectrum is practically devoid of emission lines." (3 Impact of Dust Attenuation on Observed Quiescence)
   - assumption: Differential attenuation f = 0.44 as worst case  
  > "in the following we assume $f=0.44$ as worst case" (3 Impact of Dust Attenuation on Observed Quiescence)
   - fitting: _not stated_
   - validation: Composite spectrum compared with the observed spectrum of JADES-GS-z7-01-QU (qualitative)  
  > "The right panel of Figure" (3 Impact of Dust Attenuation on Observed Quiescence)
8. **Sight-line variation of nebular attenuation in SPHINX^20**: Use stellar E(B-V) along 10 sight lines per galaxy to compute the [O III] attenuation factor  
  > "We use the stellar continuum color excess E(B-V) measured along the different sight lines as an estimate of the patchiness of dust in these simulated $z=7$ galaxies." (3 Impact of Dust Attenuation on Observed Quiescence)
   - parameter: f = 0.44 and 0.7  
  > "for two differential dust attenuation values of $f=0.44$ (cite: calzetti00) and $0.7$ (cite: kashino13)" (3 Impact of Dust Attenuation on Observed Quiescence)
   - assumption: Starburst reddening curve k'(lambda) from Calzetti et al.  
  > "For $k^\prime(\lambda)$ we assume a starburst reddening curve (cite: calzetti00)." (3 Impact of Dust Attenuation on Observed Quiescence)
   - fitting: _not stated_
   - validation: _not stated_

## Software

- **DELightcurveSimulation** : Simulate stochastic SFHs (light curves) from a PSD  
  > "which is based on the (cite: emmanoulopoulos13) light curve simulation algorithm" (2.2.1 Synthetic spectra derived from stochastic SFHs); "Here, we use an approach similar to (cite: caplar19) to create model SFHs with different statistical properties." (2.2.1 Synthetic spectra derived from stochastic SFHs)
- **FSPS** : Synthetic spectra from SFHs  
  > "Synthetic spectra are derived using the Flexible Stellar Population Synthesis (cite: conroy09; conroy10) code" (2.2.1 Synthetic spectra derived from stochastic SFHs)
- **Python-FSPS** : Python implementation of FSPS  
  > "We are using the Python implementation" (2.2.1 Synthetic spectra derived from stochastic SFHs)
- **Galfit** : Fit two components in NIRCam images  
  > "we fit the two components (visible in the blue filters, see insets) using" (3 Impact of Dust Attenuation on Observed Quiescence)
- **astropy** : _not stated_

## Numeric results

| quantity | value | uncertainty | units | step | quote |
|---|---|---|---|---|---|
| Burst-model time after burst end when conditions 1 and 2 are met | ~5 | not stated | Myr | 1 | Shortly ($\sim5\,{\rm Myrs}$) after the end of the burst, both conditions 1 and 2 are met. |
| Required tau_break for stochastic SFH at sigma ~0.6 dex | <150 | not stated | Myr | 3 | if star formation is fast-varying with a correlation time of $<150\,{\rm Myrs}$ given a reasonable burst amplitude of $\sim 0.6\,{\rm dex}$ |
| Likelihood of the state over 500 Myr at z=7 (stochastic model) | ~50 | not stated | percent | 3 | the likelihood of such a state to occur over $500\,{\rm Myrs}$ at $z=7$ is $\sim50\%$ |
| Average time spent in conditions 1+2 | ~10 | not stated | Myr | 3 | Imposing conditions $1+2$, the average time is $\sim10\,{\rm Myrs}$ in all cases. |
| SPHINX^20 z=7 best-fit sigma_MS | 0.67 | 0.04 | dex | 4 | The best-fit parameters for the $z=7$ SPHINX$^{\rm 20}$ population are $\sigma_{\rm MS} = 0.67\pm0.04\,{\rm dex}$, $\tau_{\rm break} = 202\pm117\,{\rm Myrs}$, and $\alpha=1.3\pm0.2$. |
| SPHINX^20 z=7 best-fit tau_break | 202 | 117 | Myr | 4 | The best-fit parameters for the $z=7$ SPHINX$^{\rm 20}$ population are $\sigma_{\rm MS} = 0.67\pm0.04\,{\rm dex}$, $\tau_{\rm break} = 202\pm117\,{\rm Myrs}$, and $\alpha=1.3\pm0.2$. |
| SPHINX^20 z=7 best-fit alpha | 1.3 | 0.2 | dimensionless | 4 | The best-fit parameters for the $z=7$ SPHINX$^{\rm 20}$ population are $\sigma_{\rm MS} = 0.67\pm0.04\,{\rm dex}$, $\tau_{\rm break} = 202\pm117\,{\rm Myrs}$, and $\alpha=1.3\pm0.2$. |
| Fraction of SPHINX^20 galaxies passing through JADES-GS-z7-01-QU-like properties by z=7 | 60-80 | not stated | percent | 5 | Doing so suggests that about $60-80\%$ of the simulated galaxies go through similar observed properties as JADES-GS-z7-01-QU |
| Likelihood of observing a JADES-GS-z7-01-QU analog at z=7 | 2.8 | 1.6 | percent | 5 | we find a likelihood of $2.8\pm1.6\%$ to observe a galaxy similar to JADES-GS-z7-01-QU at $z=7$ |
| Star-forming galaxies to survey per temporarily quiescent galaxy | 30 | +47/-13 | galaxies | 5 | about $30^{+47}_{-13}$ star-forming galaxies at $5\times10^{8}$ need to be surveyed in order to find a temporarily quiescent galaxy |
| Predicted MIRI F560W AB magnitude (composite, E(B-V)=0.6) | 27.8 | not stated | mag (AB) | 7 | we find $m_{\rm F560W}=27.8$ and $m_{\rm F770W}=27.6$, respectively. |
| Predicted MIRI F770W AB magnitude (composite, E(B-V)=0.6) | 27.6 | not stated | mag (AB) | 7 | we find $m_{\rm F560W}=27.8$ and $m_{\rm F770W}=27.6$, respectively. |
| Maximum E(B-V) along any SPHINX^20 sight line | 0.5 | not stated | mag | 8 | The maximum E(B-V) found on any sight line is $0.5\,{\rm mag}$ |
| Most extreme change of [O III] attenuation between sight lines | 10 | not stated | factor | 8 | In the most extreme case we find that the attenuation changes by a factor of $10$ |

## Qualitative findings

- The composite should still show H-alpha emission, which is outside the current NIRSpec range  
  > "we would still expect the galaxy to show H$\alpha$ emission in this case" (Summary & Conclusions)
- NIRCam imaging shows a blue (east) and a red (west) component  
  > "The color-composite shows a blue component (east), separated from the main redder component (west)." (3 Impact of Dust Attenuation on Observed Quiescence)

## Claim tuples

- H: A single starburst can produce a lack of optical lines with a blue UV-to-optical ratio | E: Burst of SFR 10 Msun/yr for 50 Myr, no dust, tracked after the burst | R: Both conditions are met about 5 Myr after the burst ends | F: The observed properties are achievable shortly after a starburst | **supported**
- H: Stochastic SFHs can make such a galaxy with reasonable likelihood | E: Synthetic spectra from PSD-based SFHs over tau_break and sigma_MS grids, and from SPHINX^20 SFHs | R: tau_break <150 Myr at sigma ~0.6 dex gives ~50% likelihood over 500 Myr; time in state <20 Myr | F: Fast-varying SFH with reasonable burstiness can explain the galaxy | **supported**
- H: Spatially varying dust can explain the spectrum | E: Blue (dust-free, density bounded) plus red (dust-obscured) composite spectrum; SPHINX^20 sight-line attenuation | R: Composite is practically devoid of emission lines at E(B-V)=0.6 mag; nebular attenuation varies up to a factor of 10 between sight lines | F: The spectrum can be naturally explained by a blue plus red spatial composition | **supported**
- H: Such temporary quiescence is consistent with observed rates | E: Monte Carlo from SPHINX^20 quiescence statistics | R: 2.8+-1.6% likelihood, about 30 star-forming galaxies per quiescent one | F: Roughly consistent with one such galaxy among ~40 in the observations | **supported**

## Reasoning

- Why this data: Dust geometry along the line of sight could mimic quiescence, so the dust scenario is tested  
  > "Alternatively, an unlucky geometric distribution of dust along the line of sight could attenuate the nebular emission and mimic quiescence." (1 Introduction)
- Why this method: Stochastic SFH modelling follows an approach similar to earlier work on SFH variability  
  > "Here, we use an approach similar to (cite: caplar19) to create model SFHs with different statistical properties." (2.2.1 Synthetic spectra derived from stochastic SFHs)
- Alternative: AGN or star formation feedback and galaxy-galaxy interactions named as other likely quenching scenarios; not modelled here  
  > "the most likely scenarios involve temporal quenching by star formation or AGN feedback (cite: gelli23; lovell23) or galaxy-galaxy interactions (cite: asada23)" (1 Introduction)
- How they decided it was enough: _not stated_
- Limitation (authors): SPHINX^20 has no black hole formation or AGN feedback  
  > "the SPHINX$^{\rm 20}$ simulation does not include black hole formation or AGN feedback due to its small volume" (Summary & Conclusions)
- Limitation (authors): tau_break and sigma_MS are degenerate in the stochastic analysis  
  > "We note that in the case of this analysis, $\tau_{\rm break}$ and $\sigma_{\rm MS}$ are degenerate." (2.2.2 How likely is it to observe JADES-GS-z7-01-QU?)
- Limitation (authors): E(B-V) = 0.6 mag is rare for low-mass high-z galaxies  
  > "hence an E(B-V) of 0.6 mag is rare (but not unphysical as shown in the paragraph below)" (3 Impact of Dust Attenuation on Observed Quiescence)
- Caveat (inferred, ours): Only one observed object defines the conditions, so the probabilities are anecdotal
- Caveat (inferred, ours): The 2.8% estimate rests on assumed 70%, twice, 10 Myr quiescence statistics
- Caveat (inferred, ours): The blue plus red composite is illustrative and not fitted to data, with no uncertainties
- Caveat (inferred, ours): The E(B-V)=0.6 mag and f=0.44 are chosen as a worst case
- Caveat (inferred, ours): No ALMA data are analysed, so the ALMA prediction is untested

## Reproducibility

- Data public (paper): JWST data obtained from MAST; no ALMA data used  
  > "Some of the data presented in this article were obtained from the Mikulski Archive for Space Telescopes (MAST) at the Space Telescope Science Institute." (Acknowledgements)
- Products in archive: _not stated_
- Missing: Authors' analysis scripts not released
- Missing: FSPS and PSD simulation parameters beyond those listed
- Missing: Access to SPHINX^20 SFHs and sight-line E(B-V) tables
- Missing: UV and optical band definitions and [O III] SNR calculation
- Missing: Component stellar masses of the composite spectrum
- Data volume (inferred): Small: no ALMA data; JWST NIRCam images and SPHINX^20 SFH tables, a few GB at most
- Score (inferred): 2/5, Theory paper with no ALMA data analysed; key model settings and scripts are not given, though headline numbers are quoted.
- Rediscovery candidate: no, No ALMA data; the recipe depends on unreleased scripts and SPHINX^20 outputs.

## Links

- Method: (cite: caplar19) (Approach for stochastic SFH modelling)
- Method: (cite: connolly16); (cite: emmanoulopoulos13) (DELightcurveSimulation code and light-curve algorithm)
- Method: (cite: katz23) (SPHINX^20 simulation details)
- Companion: (cite: looser23) (Discovery and JWST spectroscopy of JADES-GS-z7-01-QU)
- Companion: (cite: gelli23) (Earlier attempt to reproduce the SED of the galaxy)
- Companion: (cite: looser23b) (Observed rate of (mini-)quenched galaxies)
- Related: ALMA program 2023.1.00521.S (PI Faisst, upcoming)
- Related: ALPINE
- Related: REBELS
- Related: SPHINX

## Checks

```json
{
 "quotes": 90,
 "quotes_ok": 90,
 "quote_pass_rate": 1.0,
 "quotes_too_long": 0,
 "unsupported_facts": 0,
 "project_codes": 1,
 "codes_not_in_text": [],
 "codes_not_in_obscore": [],
 "obscore_codes_not_in_card": [],
 "codes_printed_but_missing": [],
 "numeric_results": 14,
 "numeric_problems": 0,
 "fill": {
  "facts": 108,
  "stated": 59,
  "rate": 0.546
 },
 "evidence_ok": true
}
```
