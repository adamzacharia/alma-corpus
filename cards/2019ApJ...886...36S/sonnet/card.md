# ALMA Observations of Fragmentation, Substructure, and Protostars in High-mass Starless Clump Candidates

`2019ApJ...886...36S` | The Astrophysical Journal 2019 | first author: Svoboda, Brian E. | arXiv: 1908.10374 | DOI: 10.3847/1538-4357/ab40ca

Card schema 1.0 | model claude-sonnet-5-5 | depth full | type observational_alma_primary

## Science

- Fields: star_formation, milky_way_ism
- Question: What are the fragmentation scale, sub-structure and protostellar content of massive starless clump candidates, and are there high-mass starless cores?  
  > "identify potential high-mass starless cores ($M \gtrsim \SI{30}{\ensuremath{
    \mathit{M}_\odot
}}$, $R \lesssim \SI{0.1}{pc}$), and search for previously undetected low luminosity protostellar activity." (Introduction)
- Target **12 starless clump candidates (G22695, G23297, G23481, G23605, G24051, G28539, G28565, G29558, G29601, G30120, G30660, G30912)**: coordinates Table 1 lists l, b, ICRS RA/Dec (e.g. G28539: 18:44:22.60 -04:01:57.70)  
  > "| G28539 | 28.538652 | -0.270358 | 18:44:22.60 | -04:01:57.70 | 88.60 | 4732 |" (Table 1); "| G28539 | 4780 (220) |       0.1280 (0.011) |           3610 (360) |   12.38 (0.14) |" (Table 2); z/distance d = 2980-4800 pc (Table 2)  
  > "| G28539 | 28.538652 | -0.270358 | 18:44:22.60 | -04:01:57.70 | 88.60 | 4732 |" (Table 1); "| G28539 | 4780 (220) |       0.1280 (0.011) |           3610 (360) |   12.38 (0.14) |" (Table 2); distance from kinematic distances with DPDF from Ellsworth-Bowers et al. 2015  
  > "| G28539 | 28.538652 | -0.270358 | 18:44:22.60 | -04:01:57.70 | 88.60 | 4732 |" (Table 1); "| G28539 | 4780 (220) |       0.1280 (0.011) |           3610 (360) |   12.38 (0.14) |" (Table 2)

## Data provenance

- ALMA projects: 2015.1.00959.S
- bands: Band 6 (1.3 mm)  
  > "first targeted ALMA Band 6 1.3 mm continuum and spectral line survey" (abstract)
- frequencies and spectral setup: Sidebands near 215 and 230 GHz; nine SPWs (one wide at 233.8 GHz, eight high-resolution line windows)  
  > "lower and upper sidebands centered near 215 and 230 GHz, respectively" (2.2 ALMA Band 6); "We observed nine spectral windows (SPWs) with one wide-band, low-spectral resolution window centered at 233.8 GHz and eight high-spectral resolution windows centered on lines of interest." (2.2.2 ALMA spectral line reduction)
- continuum bandwidth: ~3.5 GHz dual polarization  
  > "Together, this yields $\approx \SI{3.5}{GHz}$ of dual polarization continuum bandwidth." (2.2.1 ALMA 1.3 mm continuum reduction)
- arrays: 12 m + 7 m joint  
  > "The joint $12+\SI{7}{m}$ array maps have a high spatial resolution" (abstract)
- configurations: C36-2 (12 m)  
  > "in a compact configuration (C36-2; joint $12+\SI{7}{m}$ array baselines range from $\sim \! 9 - \SI{450}{m}$)" (2.2 ALMA Band 6)
- baselines: _not stated_
- angular resolution: 0.85" x 0.75" synthesized beam  
  > "synthesized beam size of $\theta_\mathrm{maj} \approx 0.85\ensuremath{''}$ by $\theta_\mathrm{min} \approx 0.75\ensuremath{''}$" (2.2.1 ALMA 1.3 mm continuum reduction)
- max recoverable scale: 33" from the 7 m array  
  > "substantially less than the maximum recoverable scale of $33\ensuremath{''}$ from the 7 m array" (4.3 Synthetic observations with CASA)
- sensitivity: line cubes 1.8 mJy/(km/s) (2.2 mJy per 0.68 km/s channel)  
  > "We find a typical RMS noise levels in the image cubes of 1.8 mJy/( km s $^{-1}$ ) (i.e., 2.2 mJy per 0.68 km s $^{-1}$ channel or 3.0 mJy per 0.34 km s $^{-1}$ channel)" (2.2.2 ALMA spectral line reduction)
- time on source: 12 m observations ~12 hr including overheads  
  > "the 12 m array observations lasted for approximately 12 hr, with typical precipitable water vapor of 1.5 mm" (2.2 ALMA Band 6)
- observing dates: 12 m: 3-20 March 2016; 7 m: 30 April-19 August 2016  
  > "Data were taken between $3-20$ March, 2016, for the 12 m array and between 30 April to 19 August, 2016, for the 7 m array." (2.2 ALMA Band 6)
- pi or archival as stated: Own Cycle 3 program ("we observed")  
  > "we observed 12 clumps in Band 6" (2.2 ALMA Band 6)
- Line: CO J=2-1 (230.538 GHz)
- Line: SiO J=5-4 (217.10498 GHz)
- Line: p-H2CO 3(2,2)-2(2,1) (218.475632 GHz)
- Other facility **Spitzer GLIMPSE**: 8 um IRAC mosaic used for extinction comparison with ALMA continuum  
  > "We use the *Spitzer*  GLIMPSE (cite: benjamin03; churchwell09) IRAC Band 4 ($\lambda_{\rm c} = \SI{7.9}{\um}$, $2\ensuremath{''}$ FWHM) mosaic to show the EMAF contrast." (2.3 Image fidelity and MIR comparison)
- Other facility **ATLASGAL 870 um**: Flux densities in 27" aperture to derive clump surface density  
  > "we extract flux densities from the ATLASGAL 870 μm maps ($\theta_\mathrm{hpbw} \approx 19\ensuremath{''}$) at the position of the ALMA pointing" (5.2 Jeans length comparison)
- Other facility **JVLA C-band (Rosero et al.)**: Radio continuum image towards G28539  
  > "carried out deep Jansky Very Large Array (JVLA) C & K-band observations towards a sample of high-mass clumps which contains source G28539" (3.3 G28539, a true starless clump?)
- External data: Clump distances, masses, temperatures, Sigma_pk  
  > "Properties are taken from (cite: svoboda16), except for mass measurements of G29601 and G30912 which are taken from (cite: traficante15)." (Table 2) [from (cite: svoboda16); (cite: traficante15)]
- External data: Distance probability density functions per clump  
  > "We propagate the uncertainty in heliocentric distance based on the distance probability density function (DPDF) from (cite: ellsworthbowers15a) for each clump." (5.2 Jeans length comparison) [from (cite: ellsworthbowers15a)]
- External data: Clump NH3 kinetic temperatures and velocity dispersions at 32"  
  > "From , 9 out of 12 clumps have $T_\mathrm{K}$ measured from (at $32\ensuremath{''}$ resolution)." (5.2 Jeans length comparison) [from not stated (citation key missing in text)]
- External data: Dust opacity kappa(1.3 mm)=0.90 cm2/g  
  > "opacity per mass of dust $\kappa \left( \lambda = \SI{1.3}{mm} \right) = \SI{0.90}{cm^2.g^{-1}}$ (cite: ossenkopf94)" (5.2 Jeans length comparison) [from (cite: ossenkopf94)]
- Simulation/model as data: 10^4 RADMC-3D models of externally heated Plummer-like starless cores  
  > "We apply a spherically symmetric Plummer-like function to parametrize the model radial density profile" (4.1 Starless core models)

## Processing

### Calibration

- pipeline or manual: _not stated_
- casa version: CASA 4.7.134-DEV, r38011  
  > "Data reduction was performed using `CASA`  (version 4.7.134-DEV, r38011, for consistency with QA2 delivered products)." (2.2.1 ALMA 1.3 mm continuum reduction)
- pipeline version: _not stated_
- archive products used as is: _not stated_
- flux calibrator: Titan and J1733-1304 (bandpass J1751+0939; gains J1743-0350, J1830+0619)  
  > "Titan and J1733–1304 were used as flux calibrators, J1751+0939 to calibrate the bandpass" (2.2 ALMA Band 6)
- flux scale uncertainty: _not stated_
- self calibration: Not applied  
  > "Self-calibration was not applied because the brightest sources in the image are only a few mJy" (2.2.1 ALMA 1.3 mm continuum reduction)

### Imaging

- task: tclean, joint 12+7 m  
  > "The joint $12+\SI{7}{m}$ continuum was then iteratively CLEANed with manual masking using the `tclean` task" (2.2.1 ALMA 1.3 mm continuum reduction)
- deconvolver: multiscale  
  > "using the multiscale deconvolver and a robust weighting of 1, down to a brightness threshold of $2-3\ensuremath{
    \sigma_\mathrm{rms}
}$" (2.2.1 ALMA 1.3 mm continuum reduction)
- weighting robust: robust = 1  
  > "with a Briggs robust parameter of $1.0$, cell size of $0.1\ensuremath{''}$" (2.2.2 ALMA spectral line reduction)
- uv taper: _not stated_
- cell size: 0.1"  
  > "An image cell size of $0.1\ensuremath{''}$ was used for all continuum and spectral line maps." (2.2.1 ALMA 1.3 mm continuum reduction)
- image size: _not stated_
- masking: manual masking; threshold 2-3 sigma  
  > "iteratively CLEANed with manual masking" (2.2.1 ALMA 1.3 mm continuum reduction)
- multiscale scales: _not stated_
- continuum subtraction: _not stated_
- line free channels: channels with lines flagged and visually inspected; averaged to 25 MHz  
  > "Line-free continuum visibilities were created by flagging channels contaminated by spectral lines" (2.2.1 ALMA 1.3 mm continuum reduction)
- primary beam correction: dendrogram run on maps not primary-beam corrected  
  > "we apply the dendrogram to maps that have *not* been corrected for the weight of the primary beam" (2.4 Core identification and dendrogram)
- array combination: joint imaging of 12 m + 7 m  
  > "The line SPWs from the $12+\SI{7}{m}$ arrays were jointly imaged using the CASA task `tclean`" (2.2.2 ALMA spectral line reduction)
- smoothing: _not stated_
- final beam: 0.85" x 0.75"  
  > "synthesized beam size of $\theta_\mathrm{maj} \approx 0.85\ensuremath{''}$ by $\theta_\mathrm{min} \approx 0.75\ensuremath{''}$" (2.2.1 ALMA 1.3 mm continuum reduction)
- final rms: _not stated_

### Inherited from earlier work

- Radiative transfer core modeling approach  
  > "We follow a similar approach to modeling starless cores as found in (cite: shirley05) and (cite: lippok16)." (4.1 Starless core models) [from (cite: shirley05); (cite: lippok16)]
- Delta chi2_r < 3 goodness-of-fit criterion  
  > "We discriminate between models based on the goodness of fit metric $\Delta \chi^2_\mathrm{r} \equiv \chi^2_\mathrm{r} - \chi^2_\mathrm{r,best}$ from (cite: robitaille07) and (cite: robitaille17)." (4.4 Comparison to observations) [from (cite: robitaille07); (cite: robitaille17)]
- Spherical-volume projection correction for nearest-neighbor separations (comparison)  
  > "as is done in (cite: myers17)" (5.1 Nearest neighbor separations and Monte Carlo simulations) [from (cite: myers17)]

### Not stated but needed to reproduce (our reading)

- Multiscale scales for tclean not given
- Exact line-free channel ranges per SPW and clump
- Per-target clean thresholds and rms values
- Manual mask definitions
- Pipeline vs manual calibration and flux scale uncertainty not stated
- Dendrogram implementation details (astrodendro version, handling of beam-area minimum)
- Details of ALMA delivered-product flux scale / flux calibrator models
- Seed and exact setup of MC for projection correction and ISRF/dust parameter ranges beyond those given
- NH3 data source for temperatures/velocity dispersions is cited ambiguously
- Number of model recipes imaged through CASA sm for the 'subset' consistency tests

## Analysis recipe

1. **Continuum imaging**: Line-free channels split and averaged to 25 MHz, joint 12+7 m tclean multiscale, robust 1, manual masks  
  > "The joint $12+\SI{7}{m}$ continuum was then iteratively CLEANed with manual masking using the `tclean` task using the multiscale deconvolver and a robust weighting of 1" (2.2.1 ALMA 1.3 mm continuum reduction)
   - software: CASA, tclean, split
   - parameter: cell 0.1", clean threshold 2-3 sigma  
  > "An image cell size of $0.1\ensuremath{''}$ was used for all continuum and spectral line maps." (2.2.1 ALMA 1.3 mm continuum reduction)
   - fitting: _not stated_
   - validation: Compared with Spitzer 8 um extinction structure  
  > "Qualitatively this good correspondence supports the fidelity of the emission structure detected in the ALMA maps." (2.3 Image fidelity and MIR comparison)
2. **Line cubes and outflow identification**: Joint tclean cubes (not CLEANed for analysis), visual inspection for bipolar CO and SiO outflows  
  > "Outflows are identified through visual inspection of the datacubes in conjunction with the 1.3 mm maps overplotted." (3.2 CO & SiO Outflows)
   - software: CASA, tclean
   - parameter: detection >=7 sigma; weak 5-7 sigma  
  > "Features are considered detections if they have peak intensities $\geq 7\ensuremath{
    \sigma_\mathrm{rms}
}$ (“D”), weak detections if between $5 - 7\ensuremath{
    \sigma_\mathrm{rms}
}$ (“W”)" (2.2.2 ALMA spectral line reduction)
   - fitting: _not stated_
   - validation: _not stated_
3. **Extract continuum sources with dendrogram**: astrodendro on non-primary-beam-corrected images; leaves with peak >5 sigma  
  > "using $v_\mathrm{min} = 3\ensuremath{
    \sigma_\mathrm{rms}
}$, $\delta_\mathrm{step} = 3\ensuremath{
    \sigma_\mathrm{rms}
}$, and $\Omega_\mathrm{min} = \Omega_\mathrm{bm}$" (2.4 Core identification and dendrogram)
   - software: astrodendro
   - parameter: v_min=3 sigma, delta_step=3 sigma, min area = beam area, peak >5 sigma, limit 20% primary beam  
  > "Sources (i.e. leaves, or nodes without children) are then sub-selected to meet the criteria that the peak flux is $>5\ensuremath{
    \sigma_\mathrm{rms}
}$." (2.4 Core identification and dendrogram)
   - fitting: _not stated_
   - validation: _not stated_
4. **Model starless cores and compare profiles**: RADMC-3D grid of Plummer-like externally heated cores; radial brightness profiles compared with reduced chi2 and Delta chi2_r<3  
  > "Well-fit models are then selected where $\Delta \chi^2_\mathrm{r} < 3$." (4.4 Comparison to observations)
   - software: RADMC-3D, CASA sm module, imfit
   - parameter: 10^4 models; n_in 1e4-1e7, n_out 1e1-1e3, R_flat 1e3-2e4 au, s_isrf 1-100, eta 2.5-5.5; ray-traced at 4 kpc  
  > "$n_\mathrm{in} = \num{1e4} - \SI{1e7}{cm^{-3}}$, $n_\mathrm{out} = \num{1e1} - \SI{1e3}{cm^{-3}}$, $R_\mathrm{flat} = \num{1e3} - \SI{2e4}{au}$, and $\ensuremath{
    s_\mathrm{isrf}
}= 1 - 100$" (4.1 Starless core models)
   - assumption: OH5 dust opacity kappa=0.90 cm2/g, dust-to-gas 1/110, mu=2.33, Td(1000 au)=7-13 K selection  
  > "If the range of models are limited to those that resulted in $T_\mathrm{d}(r = \SI{1e3}{au}) = 7-\SI{13}{K}$ in order to be broadly consistent with the clump-average temperature" (Comparison to observations)
   - fitting: Random sampling of parameter grid; chi2_r with 0.2" annuli, nu~15  
  > "for degrees of freedom $\nu = r_\mathrm{max}/0.2\ensuremath{''} - 5 \approx 15$" (4.4 Comparison to observations)
   - validation: Model recovery fraction (53% detectable); synthetic observations through CASA on subset  
  > "We find that $53\%$ of the computed models ($5268/\num{e4}$) meet the detection threshold" (4.2 Model recovery)
5. **Nearest-neighbor separations vs thermal Jeans length**: Monte Carlo de-projection of dendrogram-leaf separations; scale by clump average thermal Jeans length with MC over S870, Td, distance  
  > "In this work we employ Monte Carlo random sampling to de-project $\ensuremath{
    \delta_\mathrm{nns}
}^\prime$ statistically." (5.1 Nearest neighbor separations and Monte Carlo simulations)
   - parameter: 1e4 realizations per clump; sigma_z=0.15 pc for isolated sources; D=0.6 pc for grouped sources  
  > "we compute 1 × 10^4^ realizations for each clump" (5.1 Nearest neighbor separations and Monte Carlo simulations)
   - assumption: Td=12±2 K, kappa=0.90 cm2/g, f_d=1/110, mu=2.33  
  > "We choose a conservative dust temperature distribution by assuming a Gaussian dust temperature distribution $\langle \ensuremath{
    T_\mathrm{d}
}\rangle = 12 \pm \SI{2}{K}$" (5.2 Jeans length comparison)
   - fitting: _not stated_
   - validation: Compared with spherical-volume correction of Myers 2017  
  > "which is larger than the median value computed above from the MC trials by $29\%$" (5.1 Nearest neighbor separations and Monte Carlo simulations)

## Software

- **CASA** 4.7.134-DEV, r38011: Calibration products, tclean imaging, imfit, split, sm synthetic observations  
  > "Data reduction was performed using `CASA`  (version 4.7.134-DEV, r38011, for consistency with QA2 delivered products)." (2.2.1 ALMA 1.3 mm continuum reduction)
- **astrodendro** : Dendrogram and source catalog  
  > "We use the open source Python software library `astrodendro` to create the dendrogram and catalog of cores." (2.4 Core identification and dendrogram)
- **RADMC-3D** : Dust temperature and synthetic images of starless cores  
  > "we apply the radiative transfer code `RADMC-3D`  (cite: dullemond12) to self-consistently calculate the equilibrium dust temperature distributions" (4.1 Starless core models)
- **Astropy, Matplotlib, NumPy, SciPy, Pandas, IPython** : General analysis and plotting  
  > "This research has made use of the following software projects" (Software)

## Numeric results

| quantity | value | uncertainty | units | step | quote |
|---|---|---|---|---|---|
| Number of dendrogram sub-structures | 67 | not stated | sources | 3 | In total, we identify 67 sub-structures for the sample of 12 clumps. |
| Clumps with bipolar outflows/protostellar signposts | 11 of 12 | not stated | clumps | 2 | bipolar outflows towards 11 out of 12 clumps |
| G28539 S2 core mass | 29 (max 52, min 15) | median, maximum, minimum model mass | Msun | 4 | $M_\mathrm{S2} = 29^{52}_{15} \, \ensuremath{
    \mathit{M}_\odot
}$ and $M_\mathrm{S4} = 14^{34}_{6.0} \, \ensuremath{
    \mathit{M}_\odot
}$ |
| Median projection-corrected nearest-neighbor separation | 0.118 (16-84%: 0.065-0.232) | percentile interval | pc | 5 | find $\mu_{1/2}(\ensuremath{
    \delta_\mathrm{nns}
}) = \SI{0.118}{pc}$ |
| Median projected separation | 0.083 (0.051-0.140) | 16-84 percentile | pc | 5 | the distribution of projected separations has a median value of $\mu_{1/2}(\ensuremath{
    \delta_\mathrm{nns}
}^\prime) = \SI{0.083}{pc}$ |
| Ensemble median delta_nns/lambda_J,th | 0.82 | 25-75 percentile 0.52-1.25 | dimensionless | 5 | has a median value of $\ensuremath{
    \ensuremath{
    \delta_\mathrm{nns}
}/ \langle \ensuremath{
    \lambda_\mathrm{j,th}
}\rangle
}= 0.82$ with a $(25,75)$ percentile interval of $0.52-1.25$ |
| Median clump thermal Jeans length | 0.135 | range 0.10-0.17 across clumps | pc | 5 | The median of samples from all clumps is $\ensuremath{
    \lambda_\mathrm{j,th}
}= \SI{0.135}{pc}$ |
| Mean number of sub-structures per clump | 5.6 | median 6 | sources | 3 | We find an average number of sub-structures per clump of $N_\mathrm{src}=5.6$ (median 6) |
| Best-fit chi2_r for G29558 S1 (compact source) | 23.9 | not stated | dimensionless | 4 | We find that the models poorly fit the observations, with $\chi^2_\mathrm{r,best} = 23.9$ |

## Qualitative findings

- Current MIR/FIR Galactic Plane surveys are incomplete to low-luminosity protostars; G28539 is the only remaining starless clump candidate.  
  > "After the ALMA observations G28539 is the only starless clump candidate remaining in our sample." (3.3 G28539, a true starless clump?)

## Claim tuples

- H: Are high-mass starless clump candidates truly starless? | E: Visual search for CO and SiO outflows in ALMA cubes and compact continuum sources | R: Bipolar outflows or other signposts in 11 of 12 clumps | F: Most SCCs host low/intermediate-mass protostars below survey completeness | **supported**
- H: Are unresolved cores consistent with starless cores? | E: Compare radial profiles with RADMC-3D Plummer models | R: Compact source G29558 S1 poorly fit (chi2_r,best=23.9) | F: Unresolved cores likely protostellar | **supported**
- H: Do G28539 S2/S4 qualify as high-mass starless cores? | E: Model fits to extended profiles | R: M_S2=29 (15-52) Msun, M_S4=14 (6-34) Msun | F: Candidate high-mass starless cores but masses highly uncertain | **partially**
- H: What length scale characterizes fragmentation? | E: MC de-projected nearest neighbor separations vs thermal Jeans length | R: Median delta_nns/lambda_J,th = 0.82 | F: Fragmentation consistent with clump thermal Jeans length, supporting hierarchical fragmentation | **supported**

## Reasoning

- Why this data: _not stated_
- Why this method: Dendrogram suited to hierarchical structure; no SED/CMF due to single wavelength and temperature uncertainty  
  > "The nature of the tree data-structure in the dendrogram algorithm makes it well-suited to identifying and categorizing structure in images with hierarchical structure" (2.4 Core identification and dendrogram)
- Alternative: Core mass function not derived because of ~10x mass uncertainty from Td  
  > "we shall leave the study of the characteristic fragmentation mass and the CMF in SCCs to a future work" (2.4 Core identification and dendrogram)
- How they decided it was enough: _not stated_
- Limitation (authors): Line cubes not CLEANed due to spatial filtering; single-wavelength continuum gives poor temperature constraints  
  > "In this work we inspect the line image cubes for detection of emission, and for the presence of outflows traced by and , but do not CLEAN the data cubes." (2.2.2 ALMA spectral line reduction)
- Caveat (inferred, ours): Projection correction depends on assumed geometry (0.6 pc depth, inclination ranges)
- Caveat (inferred, ours): Sample small (11 clumps in separation analysis) and temperature fixed at 12 K
- Caveat (inferred, ours): Outflow detection by visual inspection, subjective
- Caveat (inferred, ours): Compact sources may be protostellar by inference only; model grid does not reach extreme densities
- Caveat (inferred, ours): Spatial filtering affects flux and dendrogram boundaries

## Reproducibility

- Data public (paper): _not stated_
- Products in archive: _not stated_
- Missing: Public status of data not explicitly stated in paper
- Missing: tclean multiscale scales and clean masks
- Missing: Exact flagged channels
- Missing: MC sampling code not released
- Data volume (inferred): ~100-300 GB raw for 12 m and 7 m Band 6 data; products smaller
- Score (inferred): 3/5, Data code given and key settings (robust, cell, dendrogram parameters, model ranges) stated, but multiscale scales, masks, line-free channels and MC code missing.
- Rediscovery candidate: no, Public status not stated in paper and several recipe details missing, though results are numeric.

## Links

- Method: (cite: rosolowsky08b) (Dendrogram algorithm)
- Method: (cite: robitaille07) (Delta chi2 model-fit criterion)
- Method: (cite: lippok16) (Plummer starless core modeling approach)
- Companion: (cite: svoboda16) (Source of BGPS clump sample and properties)
- Companion: (cite: traficante15) (Hi-GAL dark IRDC clump sample)
- Related: BGPS
- Related: ATLASGAL
- Related: Hi-GAL
- Related: GLIMPSE
- Related: CORE survey

## Checks

```json
{
 "quotes": 84,
 "quotes_ok": 84,
 "quote_pass_rate": 1.0,
 "quotes_too_long": 0,
 "unsupported_facts": 0,
 "project_codes": 1,
 "codes_not_in_text": [],
 "codes_not_in_obscore": [],
 "obscore_codes_not_in_card": [],
 "codes_printed_but_missing": [],
 "numeric_results": 9,
 "numeric_problems": 0,
 "fill": {
  "facts": 83,
  "stated": 62,
  "rate": 0.747
 },
 "evidence_ok": true
}
```
