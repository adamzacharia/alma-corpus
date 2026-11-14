# Massive extended streamers feed high-mass young stars

`2025SciA...11.4512O` | Science Advances 2025 | first author: Olguin, Fernando A. | arXiv: 2508.15889 | DOI: 10.1126/sciadv.adw4512

Card schema 1.0 | model claude-sonnet-5-5 | depth full | type observational_alma_primary

## Science

- Fields: star_formation
- Question: Do high-mass protostars like G336 ALMA1 lack a large Keplerian disk and instead gain gas via massive streamers reaching well inside the expected disk radius, and are the flows strong enough to overcome stellar feedback?  
  > "To investigate the small-scale structure of this region and to search for the presence of an accretion disk, we conducted high-resolution (28 mas or 86 au, Fig. 1A; see Material and Methods)" (Results and Discussion)
- Target **G336.018-00.827 (G336 ALMA1)**: coordinates RA 16h35m09.2585s, Dec -48°46'77.661'' (from continuum Gaussian fit)  
  > "the Galactic high-mass core G336.018-00.827 (hereafter G336 ALMA1; distance 3.1 kpc (cite: Urquhart2018))" (Introduction); "The central source right ascension is $16^{\rm h}35^{\rm m}09.2585^{\rm s}\pm0.0002^{\rm s}$" (Modeling refinement); z/distance 3.1 kpc  
  > "the Galactic high-mass core G336.018-00.827 (hereafter G336 ALMA1; distance 3.1 kpc (cite: Urquhart2018))" (Introduction); "The central source right ascension is $16^{\rm h}35^{\rm m}09.2585^{\rm s}\pm0.0002^{\rm s}$" (Modeling refinement); distance from Urquhart2018 (ATLASGAL)  
  > "the Galactic high-mass core G336.018-00.827 (hereafter G336 ALMA1; distance 3.1 kpc (cite: Urquhart2018))" (Introduction); "The central source right ascension is $16^{\rm h}35^{\rm m}09.2585^{\rm s}\pm0.0002^{\rm s}$" (Modeling refinement)

## Data provenance

- ALMA projects: 2017.1.00237.S, 2022.1.00700.S
- bands: 1.3 mm continuum (Band 6)  
  > "observations of the 1.3 mm continuum and several molecular lines" (Results and Discussion)
- frequencies and spectral setup: channel width 488.281 kHz, ~1.5 km/s resolution (2 channels)  
  > "Both observations were made with a channel width of 488.281 kHz, which corresponds to a spectral resolution (2 channels) of ${\sim}1.5$ km s$^{-1}$" (Observations and data reduction)
- continuum bandwidth: _not stated_
- arrays: 12m array  
  > "G336.018-0.827 was observed with the 12m Atacama Large millimeter/submillimeter Array (ALMA)" (Observations and data reduction)
- configurations: C-8 (45 antennas, DIHCA 2019) and C-9 (49 antennas, 2023)  
  > "the observations were performed in configuration C-8 with 45 antennas. The most recent observations were performed with the C-9 array configuration with 49 antennas." (Observations and data reduction)
- baselines: _not stated_
- angular resolution: continuum 0.031x0.025" (96x78 au)  
  > "The resulting continuum angular resolution is $0.031\times0.025$” (P.A.=57.5$^{\circ}$; $96\times78$ au)" (Observations and data reduction)
- max recoverable scale: _not stated_
- sensitivity: continuum 28 uJy/beam; line cubes 1.1-1.3 mJy/beam per channel  
  > "noise level is $28\,\mu$Jy beam$^{-1}$" (Observations and data reduction); "Their noise levels are between 1.1–1.3 mJy beam$^{-1}$ per channel." (Observations and data reduction)
- time on source: _not stated_
- observing dates: July 2019 and July 2023  
  > "on July 2019 (ID: 2017.1.00237.S) and as part of follow-up observations on July 2023 (ID: 2022.1.00700.S)" (Observations and data reduction)
- pi or archival as stated: DIHCA project data plus follow-up observations  
  > "as part of the Digging into High-mass Cores with ALMA (DIHCA) project" (Observations and data reduction)
- Line: CH3OH 18(3,15)-17(4,14) A, vt=0 (Eu/k=447 K) (233.795666 GHz)
- Line: SO v=0 J_K=6_5-5_4 (Eu/k=35 K) (219.949442 GHz)
- Line: SO v=1 J_K=6_5-5_4 (Eu/k=1634 K) (218.3238577 GHz)
- External data: Central mass 10 Msun, inclination 65 deg, outer streamer temperature 93 K, outer infall rate ~1e-4 Msun/yr  
  > "A central mass of 10 ${\rm M}_\odot$ was determined by (cite: Olguin2023)" (Introduction) [from (cite: Olguin2023)]
- External data: Clump luminosity 2.5e4 Lsun  
  > "Assuming that the luminosity of the clump $L=2.5\times10^{4}$ ${\rm L}_\odot$ (cite: Urquhart2018)" (Inner blue streamer modeling) [from (cite: Urquhart2018)]
- External data: Dust opacity 1 cm2/g at 1.3 mm  
  > "$\kappa_{\nu}=1$ cm$^2$ g$^{-1}$ is the dust opacity at 1.3 mm (cite: Ossenkopf1994)" (Replenishing times) [from (cite: Ossenkopf1994)]

## Processing

### Calibration

- pipeline or manual: delivered calibrated data used, then phase-only self-calibration on combined data  
  > "The delivered calibrated data was combined with the DIHCA observations and self-calibration was performed on the combined data set." (Observations and data reduction)
- casa version: _not stated_
- pipeline version: _not stated_
- archive products used as is: _not stated_
- flux calibrator: _not stated_
- flux scale uncertainty: _not stated_
- self calibration: phase-only, increasingly smaller solution intervals  
  > "Only phase self-calibration with increasingly smaller solution intervals were used to produce the final calibrated data." (Observations and data reduction)

### Imaging

- task: CASA tclean for continuum; YCLEAN for lines  
  > "The continuum was imaged using the TCLEAN task with the Hogbom deconvolver, auto-masking and a Briggs weighting with robust parameter of 0.5." (Observations and data reduction)
- deconvolver: continuum Hogbom; lines multi-scale  
  > "we use the multi-scale deconvolver with scales 0, 5, 15 and 25" (Observations and data reduction)
- weighting robust: continuum robust 0.5; lines robust 2  
  > "Briggs weighting with robust parameter of 2 to increase the S/N of the lines" (Observations and data reduction)
- uv taper: _not stated_
- cell size: _not stated_
- image size: _not stated_
- masking: auto-masking  
  > "with the Hogbom deconvolver, auto-masking and a Briggs weighting" (Observations and data reduction)
- multiscale scales: 0, 5, 15, 25  
  > "multi-scale deconvolver with scales 0, 5, 15 and 25" (Observations and data reduction)
- continuum subtraction: GOCONTINUUM line-free and continuum-subtracted visibilities  
  > "We then followed the procedure described in (cite: Olguin2021) (GOCONTINUUM (cite: fernando_2025_15314190)) to obtain line-free visibilities and continuum subtracted visibilities." (Observations and data reduction)
- line free channels: _not stated_
- primary beam correction: flux densities measured in primary-beam-corrected image  
  > "all measured in the primary beam corrected image" (Replenishing times)
- array combination: C-8 and C-9 visibilities combined; spws trimmed and aligned with CVEL  
  > "the spectral windows were trimmed down to the overlapping ranges and the channels aligned using the CASA (cite: 2022PASP..134k4501C) task CVEL." (Observations and data reduction)
- smoothing: _not stated_
- final beam: continuum 0.031x0.025"; CH3OH 0.041x0.037"; SO v=0 0.045x0.041"; SO v=1 0.044x0.040"  
  > "The median resolutions of the cubes are $0.041\times0.037$” (P.A.=47$^{\circ}$; $127\times115$ au) for CH$_3$OH" (Observations and data reduction)
- final rms: 28 uJy/beam continuum; 1.1-1.3 mJy/beam per channel lines  
  > "noise level is $28\,\mu$Jy beam$^{-1}$" (Observations and data reduction)

### Inherited from earlier work

- Details of the DIHCA C-8 data set  
  > "Detailed description of the former data set are described in (cite: Olguin2023)" (Observations and data reduction) [from (cite: Olguin2023)]
- Line-free/continuum-subtracted visibility procedure  
  > "We then followed the procedure described in (cite: Olguin2021) (GOCONTINUUM (cite: fernando_2025_15314190))" (Observations and data reduction) [from (cite: Olguin2021)]
- Streamline model parameters, central mass 10 Msun, inclination 65 deg  
  > "with the same parameters as (cite: Olguin2023) but varying the centrifugal radius, initial polar angle, and initial azimuthal angle for the outer blue streamer" (Modeling refinement) [from (cite: Olguin2023); (cite: Mendoza2009); (cite: Pineda2020)]

### Not stated but needed to reproduce (our reading)

- Self-calibration solution intervals and number of iterations
- CASA version
- Calibration pipeline version and flux calibrator
- Line-free channels for continuum
- tclean image size, cell size and mask parameters
- Streamline model fixed parameters not repeated from Olguin2023
- PV extraction path widths
- Viscosity alpha and 100 K temperature choices beyond the justification given

## Analysis recipe

1. **Combine and self-calibrate data**: Combine C-8 and C-9 data, align channels with CVEL, phase-only self-calibration  
  > "The delivered calibrated data was combined with the DIHCA observations and self-calibration was performed on the combined data set." (Observations and data reduction)
   - software: CASA
   - fitting: _not stated_
   - validation: _not stated_
2. **Image continuum and lines**: GOCONTINUUM continuum separation; tclean continuum; YCLEAN line cubes  
  > "In order to optimize the computing resources, we only imaged selected molecular lines with the auto-masking routine YCLEAN" (Observations and data reduction)
   - software: GOCONTINUUM, CASA tclean, YCLEAN
   - parameter: continuum robust 0.5, threshold 1.25 sigma; lines robust 2, multiscale 0,5,15,25  
  > "The continuum is cleaned down to a threshold of $1.25\sigma$ with the noise $\sigma$ determined by TCLEAN." (Observations and data reduction)
   - fitting: _not stated_
   - validation: _not stated_
3. **Fit central source**: Gaussian fit to ALMA1 continuum within 50 mas radius  
  > "we first fit a Gaussian to the ALMA1 continuum emission within a region of radius of 50 mas with the CASA task IMFIT" (Modeling refinement)
   - software: CASA imfit
   - fitting: _not stated_
   - validation: _not stated_
4. **Model streamers with streamline models**: Mendoza2009 streamlines grid over centrifugal radius, polar and azimuthal angles, best chosen by visual inspection; separate inner blue streamer in mid-plane with r_f=200 au  
  > "hence here we determine the models that best match the shape of the streamer by visual inspection." (Modeling refinement)
   - software: velocity_tools
   - parameter: rc 400-600 au (50 au steps), theta0 75-85, phi0 50-70; inner: r_c=200 au, theta0=89, phi0 140-195, v_r0=0.1 km/s selected  
  > "| Outer blue | 400–600 (50) |  75–85 (5)   |  50–70 (5)   |            0            |" (Table 1)
   - assumption: Central mass 10 Msun, inclination 65 deg, mid-plane trajectory inside centrifugal radius  
  > "The central mass, $M_c$, was set to 10 ${\rm M}_\odot$ (cite: Olguin2023)." (Inner blue streamer modeling)
   - fitting: Grid with visual comparison, no formal likelihood  
  > "we determine the models that best match the shape of the streamer by visual inspection" (Modeling refinement)
   - validation: Comparison with moment-1 map and PV diagram  
  > "This result is plotted over the streamer in the first moment map in Fig. 1B (outer streamline model) and the PV diagram in Fig. 2." (Modeling refinement)
5. **Compare PV diagram with velocity distributions**: Compare observed PV along blue streamer spine to Keplerian, Keplerian+free-fall, IRE (FERIA) and streamline models at deprojected radius  
  > "We compare the observed position-velocity (PV) diagram (Fig. 2) along the spine of the blue-shifted streamer" (Rotating and infalling motions)
   - software: pvextractor, FERIA
   - parameter: inclination 65 deg, P.A. disk -55 deg, centrifugal barrier 250 au  
  > "with the updated centrifugal barrier (250 au)" (Modeling refinement)
   - fitting: _not stated_
   - validation: Qualitative agreement; Keplerian and IRE best for inner streamer  
  > "We find that Keplerian rotation and IRE are the best-fitting models for the inner blue streamer velocity" (Rotating and infalling motions)
6. **Estimate masses, infall rates, timescales and forces**: Optically thin dust mass; free-fall and viscous times; Mdot = v_ff M/l; force L/c vs Mdot v  
  > "First we estimate the mass of the gas content around the central young star and the inner streamers from their continuum emission assuming optically thin dust" (Replenishing times)
   - parameter: T=100 K, kappa=1 cm2/g at 1.3 mm, R_dg=0.01, d=3.1 kpc, mu=2.33, alpha 0.1-1, v_ff=6 km/s, l=500 au  
  > "We use a single temperature of 100 K for the central source and streamers" (Replenishing times)
   - assumption: Optically thin dust, dust-to-gas 0.01, Ossenkopf1994 opacity  
  > "$R_{dg}=0.01$ is the dust-to-gas mass ratio" (Replenishing times)
   - fitting: _not stated_
   - validation: Compared with outer streamer rates from Olguin2023  
  > "These are roughly one order of magnitude higher than the infall rate from the outer streamers estimated by (cite: Olguin2023)" (Replenishing times)

## Software

- **CASA** : CVEL, tclean, imfit  
  > "using the CASA (cite: 2022PASP..134k4501C) task CVEL" (Observations and data reduction)
- **GOCONTINUUM** v3.0.0: line-free and continuum-subtracted visibilities  
  > "Continuum and continuum-subtracted visibilities were produced with GOCONTINUUM (v3.0.0 (cite: fernando_2025_15314190))." (Data and materials availability)
- **YCLEAN** : line cube imaging  
  > "The data cubes were produced using YCLEAN" (Data and materials availability)
- **velocity_tools** v1.1: streamline models  
  > "Streamline models were calculated using the Python package VELOCITY_TOOLS (v1.1)" (Data and materials availability)
- **FERIA** : IRE models  
  > "while IRE models were calculated using FERIA" (Data and materials availability)
- **pvextractor** : position-velocity diagrams  
  > "Position-velocity diagrams were calculated using PVEXTRACTOR" (Data and materials availability)
- **Astropy** : general analysis  
  > "This work made use of ASTROPY" (Data and materials availability)

## Numeric results

| quantity | value | uncertainty | units | step | quote |
|---|---|---|---|---|---|
| Continuum beam | 0.031x0.025 (P.A.=57.5 deg) | not stated | arcsec | 2 | The resulting continuum angular resolution is $0.031\times0.025$” (P.A.=57.5$^{\circ}$; $96\times78$ au) |
| Continuum rms | 28 | not stated | uJy/beam | 2 | noise level is $28\,\mu$Jy beam$^{-1}$ |
| ALMA1 deconvolved size (geometric mean) | 39 | 6 | mas | 3 | resulting in a geometric mean size of $39\pm6\,{\rm mas}$ (121 au) |
| ALMA1 Gaussian flux density | 7.7 | 1.1 | mJy | 3 | The flux density of the Gaussian is $7.7\pm1.1$ mJy. |
| Centrifugal radius | 500 (450-550 equally good) | not stated | au | 4 | equally good matches can be obtained with a centrifugal radius between 450 and 550 au |
| Gas mass ALMA1 | 0.24 | not stated | Msun | 6 | The resulting masses are 0.24 ${\rm M}_\odot$ for the gas in ALMA1 |
| Inner blue streamer mass | 0.6 | not stated | Msun | 6 | 0.6 ${\rm M}_\odot$ for the inner blue streamer |
| Inner red streamer mass | 0.3 | not stated | Msun | 6 | 0.3 ${\rm M}_\odot$ for the red-shifted streamer |
| Infall rate inner blue streamer | 1.6e-3 | not stated | Msun/yr | 6 | This gives infall rates of $1.6\times10^{-3}$ ${\rm M}_\odot$ yr$^{-1}$ and $0.9\times10^{-3}$ |
| Infall rate inner red streamer | 0.9e-3 | not stated | Msun/yr | 6 | $0.9\times10^{-3}$ ${\rm M}_\odot$ yr$^{-1}$ for the inner blue and red-shifted streamers |
| Free-fall time of ALMA1 | ~25 | not stated | yr | 6 | the free-fall time is ${\sim}25$ yr |
| Replenishing time, blue streamer (free-fall) | ~150 | not stated | yr | 6 | between ${\sim}150$ yr (free-fall) |
| Radiation force | ~1e22 | order of magnitude | N | 6 | the force exerted by the source radiation field is of the order of $10^{22}$ N |
| Streamer inflow force | ~1e24 | order of magnitude | N | 6 | the force exerted by the inflow resulting from the blue-shifted streamer is of the order of $10^{24}$ N |

## Qualitative findings

- No conventional Keplerian disk is detected; velocity gradient is found only in streamer gas  
  > "this gradient is found only in the gas associated with the streamers, and not in a flattened, symmetric disk structure" (Higher-resolution ALMA observations)
- Vibrationally excited SO suggests shocks where the streamers join the mid-plane  
  > "This may be indicative of shocks as the gas from the streamer joins the mid-plane" (Shocked gas)

## Claim tuples

- H: Does G336 ALMA1 host a conventional disk at the centrifugal radius? | E: 28 mas continuum and CH3OH imaging | R: No disk-like over-dense structure or Keplerian gradient beyond streamers | F: Streamers rather than a large disk feed the protostar | **supported**
- H: Do streamers penetrate within the centrifugal radius and what velocity law do they follow? | E: Compare PV with streamline, Keplerian, free-fall, IRE models | R: Inner blue streamer best fit by Keplerian and IRE; outer needs infall | F: Flow continues from ~2000 to 60 au with changing velocity distribution | **supported**
- H: Can streamers overcome radiative feedback? | E: Mass, infall-rate and force estimates | R: Infall ~1e-3 Msun/yr; streamer force ~1e24 N vs radiation ~1e22 N | F: The blue streamer can likely overcome radiation pressure and feed the star | **partially**

## Reasoning

- Why this data: _not stated_
- Why this method: Multi-scale deconvolver and robust 2 chosen to increase S/N of extended lines  
  > "Briggs weighting with robust parameter of 2 to increase the S/N of the lines" (Observations and data reduction)
- Alternative: Final radius of 60 au for inner streamer rejected because no model matched inner streamer shape  
  > "We also tried a final radius of 60 au (the radius of the central continuum source), but we could not find a model that matches the inner streamer shape." (Inner blue streamer modeling)
- How they decided it was enough: _not stated_
- Limitation (authors): Mass of ALMA1 is an upper limit under optically thin approximation; infall is neither free-fall nor viscous  
  > "making its mass an upper limit under the optically thin approximation" (Replenishing times)
- Limitation (authors): Red-shifted streamer excluded from methanol analysis due to outflow contamination  
  > "we exclude it because of contamination from the outflow" (Rotating and infalling motions)
- Caveat (inferred, ours): Streamline fits chosen by visual inspection without uncertainties
- Caveat (inferred, ours): Single 100 K temperature and optically thin assumption affect masses and rates
- Caveat (inferred, ours): Mid-plane geometry of inner streamer is an approximation
- Caveat (inferred, ours): Viewing geometry reversed relative to earlier work
- Caveat (inferred, ours): Unresolved central source may hide a disk

## Reproducibility

- Data public (paper): Raw data in ALMA archive; maps, models and scripts on Zenodo  
  > "The original observational data are available through the ALMA archive located at <https://almascience.nao.ac.jp/aq/> with the program codes listed above." (Data and materials availability)
- Products in archive: _not stated_
- Code: Scripts and auxiliary files on Zenodo 10.5281/zenodo.15362023; GOCONTINUUM on Zenodo  
  > "the scripts and auxiliary files necessary to reproduce these data, results and figures are publicly available as Zenodo 10.5281/zenodo.15362023" (Data and materials availability)
- Missing: CASA version
- Missing: Self-calibration parameters
- Missing: Imaging sizes and mask details
- Missing: Exact PV cut widths and paths
- Data volume (inferred): ~100-500 GB raw for two long-baseline 12m datasets
- Score (inferred): 4/5, Public data, released scripts and mostly explicit parameters; some calibration and imaging details missing, and streamline fits are visual.
- Rediscovery candidate: yes, Public data, released scripts, numeric results (continuum fit, masses, infall rates) can be re-derived.

## Links

- Method: (cite: Mendoza2009) (streamline model)
- Method: (cite: Pineda2020) (streamline implementation)
- Method: (cite: Oya2022) (FERIA IRE model)
- Method: (cite: Olguin2021) (GOCONTINUUM procedure)
- Companion: (cite: Olguin2023) (earlier 0.05" DIHCA study of G336 ALMA1)
- Related: DIHCA

## Checks

```json
{
 "quotes": 88,
 "quotes_ok": 88,
 "quote_pass_rate": 1.0,
 "quotes_too_long": 0,
 "unsupported_facts": 0,
 "project_codes": 2,
 "codes_not_in_text": [],
 "codes_not_in_obscore": [],
 "obscore_codes_not_in_card": [],
 "codes_printed_but_missing": [],
 "numeric_results": 14,
 "numeric_problems": 0,
 "fill": {
  "facts": 86,
  "stated": 61,
  "rate": 0.709
 },
 "evidence_ok": true
}
```
