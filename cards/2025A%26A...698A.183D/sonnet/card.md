# Dust populations from 30 to 1000 au in the debris disk of HD 120326: Panchromatic view with VLT/SPHERE, ALMA, and HST/STIS

`2025A&A...698A.183D` | Astronomy and Astrophysics 2025 | first author: Desgrange, C. | arXiv: 2504.15352 | DOI: 10.1051/0004-6361/202452647

Card schema 1.0 | model claude-sonnet-5-5 | depth light | type multi_facility_alma_minor

## Science

- Fields: debris_disks
- Question: What are the morphology and dust properties of the HD 120326 debris disk from 30 to 1000 au, combining SPHERE, ALMA and HST/STIS?  
  > "By combining them with archival HST/STIS ($0.2$–$1.0~\ensuremath{\mathrm{\mu m}}$) and archival SPHERE data, we have been able to examine the morphology and photometry of the debris disk, along with its dust properties." (abstract)
- Target **HD 120326 (HIP 67497)**: coordinates _not stated_; z/distance 113.3±0.4 pc  
  > "the system HD 120326 (HIP 67497), located at $113.3\pm0.4~\ensuremath{\mathrm{pc}}$ (cite: gaiacollaboration_gaia_2021)" (1 Introduction); distance from Gaia Collaboration 2021  
  > "the system HD 120326 (HIP 67497), located at $113.3\pm0.4~\ensuremath{\mathrm{pc}}$ (cite: gaiacollaboration_gaia_2021)" (1 Introduction)

## Data provenance

- ALMA projects: 2022.1.00968.S
- bands: Band 6 (1.3 mm)  
  > "The observations use a spectral set-up using Band 6 receivers" (2.2 ALMA millimeter observations)
- frequencies and spectral setup: Two 128-channel continuum windows (15.6 MHz) at 218.0 and 233.0 GHz; line windows at 230.5 GHz (3840 ch, 244 kHz) and 220.0 GHz (1920 ch, 976 kHz)  
  > "two relatively coarse resolution spectral windows with 128 channels of width 15.6 MHz placed at central frequencies of $218.0$ GHz ($1.375~\ensuremath{\mathrm{mm}}$) and $233.0$ GHz" (2.2 ALMA millimeter observations)
- continuum bandwidth: _not stated_
- arrays: _not stated_
- configurations: _not stated_
- baselines: _not stated_
- angular resolution: 1.321'' x 0.950'' (PA=-86.729 deg)  
  > "synthesized beam of size of $1.321\ensuremath{''} \times0.950\ensuremath{''}$ ($PA=-86.729\ensuremath{^\circ}$)" (2.2 ALMA millimeter observations)
- max recoverable scale: _not stated_
- sensitivity: 17 uJy/beam  
  > "achieved a noise level of $17~\mu$Jy/beam" (2.2 ALMA millimeter observations)
- time on source: _not stated_
- observing dates: Five executions, Oct 19 and 21, Dec 17, 18, 27, 2022  
  > "In total five separate executions were made on October 19 and 21, and December 17, 18, and 27, 2022." (2.2 ALMA millimeter observations)
- pi or archival as stated: PI J. Miley  
  > "project 2022.1.00968.S (PI J. Miley)" (2.2 ALMA millimeter observations)
- Line: 12CO not stated (230.538 GHz)
- Other facility **VLT/SPHERE**: NIR polarized and total intensity imaging of the inner belt  
  > "observed both in polarimetry and total intensity with the Spectro-Polarimetric High-contrast Exoplanet REsearch instrument" (2.1 SPHERE NIR observations)
- Other facility **HST/STIS**: archival optical coronagraphic imaging of extended halo/spiral  
  > "The archival HST/STIS observation of HD 120326 were already published in (cite: padgett_warm_2016) and (cite: bonnefoy_belts_2017)." (2.3 HST/STIS optical observations)
- External data: SED photometry and Spitzer IRS spectrum  
  > "we collected photometry from various sources, for instance: $UBV$, Stromgren, HIPPARCOS, *Gaia*, 2MASS, WISE, *Spitzer*, and *Herschel*." (4.2 Modeling of the spectral energy distribution) [from not stated]

## Processing

### Calibration

- pipeline or manual: ALMA pipeline script  
  > "We reduced the raw data by using the pipeline script provided by ALMA observatory using CASA version $6.4$" (2.2 ALMA millimeter observations)
- casa version: CASA 6.4  
  > "using CASA version $6.4$ (cite: mcmullin_casa_2007)" (2.2 ALMA millimeter observations)
- pipeline version: _not stated_
- archive products used as is: _not stated_
- flux calibrator: _not stated_
- flux scale uncertainty: _not stated_
- self calibration: _not stated_

### Imaging

- task: tclean  
  > "Images were reconstructed using `tclean` task in CASA using the Hogbom deconvolver" (2.2 ALMA millimeter observations)
- deconvolver: Hogbom  
  > "using the Hogbom deconvolver (cite: hogbom_aperture_1974) and natural weighting" (2.2 ALMA millimeter observations)
- weighting robust: natural weighting; robust -2 to 2 tested, gave noisy images  
  > "We also tested other weightings, using a robust parameter ranging from -2 to 2 in steps of 0.5." (2.2 ALMA millimeter observations)
- uv taper: _not stated_
- cell size: _not stated_
- image size: _not stated_
- masking: _not stated_
- multiscale scales: _not stated_
- continuum subtraction: _not stated_
- line free channels: Channels within ±15 km/s of 12CO, 13CO, C18O flagged  
  > "we flagged channels corresponding to $\pm$15 km/s of the rest frequency of the bright molecular line transitions" (2.2 ALMA millimeter observations)
- primary beam correction: _not stated_
- array combination: _not stated_
- smoothing: _not stated_
- final beam: 1.321'' x 0.950''  
  > "synthesized beam of size of $1.321\ensuremath{''} \times0.950\ensuremath{''}$" (2.2 ALMA millimeter observations)
- final rms: 17 uJy/beam  
  > "achieved a noise level of $17~\mu$Jy/beam" (2.2 ALMA millimeter observations)

### Inherited from earlier work

- SED fitting with stellar plus modified blackbody models  
  > "These data were fit with stellar and blackbody disk models as described previously by (cite: yelverton_statistically_2019)." (4.2 Modeling of the spectral energy distribution) [from yelverton_statistically_2019]
- Optically thin 3D Gaussian torus model for ALMA visibilities  
  > "We used an optically thin 3D model that takes line of sight effects into account, which was previously used to model debris disks (cite: kennedy_unexpected_2020)." (4.1 Morphology of the disk) [from kennedy_unexpected_2020]

### Not stated but needed to reproduce (our reading)

- MCMC settings (walkers, steps, priors) for the ALMA galario/emcee fit
- Cell size, image size and mask for tclean
- Pixel/image size and phase center for uv-plane Gaussian fit
- Which continuum spectral windows were used and channel binning details
- Distance and stellar parameters used in SED fit given only by reference

## Analysis recipe

1. **Make continuum image**: Flag line channels, average to 15.625 MHz channels, concatenate five executions, tclean with Hogbom and natural weighting  
  > "The observed data was then averaged in frequency to produce consistent channel widths of $15.625$ MHz before imaging and the five executions were then concatenated into a single dataset for imaging." (2.2 ALMA millimeter observations)
   - software: CASA, tclean
   - fitting: _not stated_
   - validation: _not stated_
2. **Measure continuum flux and CO limit**: Gaussian fit in uv-plane for flux; 3 sigma rms over a beam area for 12CO upper limit  
  > "Our measurement of the flux of the debris disk is achieved by fitting a Gaussian in the uv-plane" (2.2 ALMA millimeter observations)
   - software: CASA
   - fitting: _not stated_
   - validation: _not stated_
3. **Fit disk morphology in visibilities**: Gaussian torus model, Fourier transformed with galario, MCMC with emcee  
  > "we modeled the data using `galario` (cite: tazzari_galario_2018) to Fourier transform the model images and compare them to the observed visibilities, and `emcee`" (4.1 Morphology of the disk)
   - software: galario, emcee
   - parameter: scale height H/r < 0.05; stellar flux not included  
  > "The scale height ($H/r$) was restricted to be small ($<0.05$)." (4.1 Morphology of the disk)
   - fitting: emcee MCMC run until convergence  
  > "We ran the `MCMC` until all parameters converged" (4.1 Morphology of the disk)
   - validation: Compared with scattered-light inclination and PA  
  > "are consistent at $2\sigma$ with the scattered light results" (4.1 Morphology of the disk)
4. **Dust mass from mm flux**: M_dust = F d^2 / (kappa B_nu(T)) with T=110 K from SED  
  > "$T_\text{dust}$ is the temperature of the dust grains chosen to be consistent with the observed SED ($110$ K, see Sect. [\[sec:sed\]](#sec:sed))." (4.3 Dust mass)
   - assumption: kappa = 1.7 cm2/g (850 um/lambda)  
  > "dust opacity assumed to be $1.7~\mathrm{cm^2 g^{-1}}$ ($850~\ensuremath{\mathrm{\mu m}}/\lambda_\text{obs}$) from (cite: beckwith_survey_1990)" (4.3 Dust mass)
   - fitting: _not stated_
   - validation: Compared with Krivov & Wyatt 2020 sample  
  > "we compare this dust mass to the sample from (cite: krivov_solution_2020)" (4.3 Dust mass)

## Software

- **CASA** 6.4: ALMA pipeline calibration and tclean imaging  
  > "using CASA version $6.4$ (cite: mcmullin_casa_2007)" (2.2 ALMA millimeter observations)
- **galario** : Fourier transform of models to compare with visibilities  
  > "we modeled the data using `galario` (cite: tazzari_galario_2018) to Fourier transform the model images" (4.1 Morphology of the disk)
- **emcee** : MCMC sampling for ALMA and SPHERE disk fits  
  > "`emcee` to perform Markov-Chain Monte-Carlo sampling" (4.1 Morphology of the disk)
- **MoDiSc** : Joint SPHERE scattered-light disk modeling  
  > "we developed the open-access Python-based tool Modeling Disks in Scattered light" (3 Morphology, photometry, and polarization)
- **VIP** : PCA ADI processing and GRaTeR disk models  
  > "We homogeneously postprocessed the observations in total intensity with a principal component analysis" (2.1.2 Total intensity observations)
- **IRDAP** : SPHERE polarimetric reduction  
  > "we used the public pipeline IRDAP" (2.1.1 Polarimetric observations)

## Numeric results

| quantity | value | uncertainty | units | step | quote |
|---|---|---|---|---|---|
| ALMA 1.3 mm integrated continuum flux | 561 | 20 | uJy | 2 | giving an integrated flux value of $561 \pm 20~\mu$Jy in the continuum at $1.3~\ensuremath{\mathrm{mm}}$ |
| 12CO upper limit | 4.8 | not stated | Jy km/s | 2 | we derived an upper limit of the $^{12}$CO value of $4.8~\mathrm{Jy\cdot km/s}$ |
| ALMA disk inclination | 70 | 5 | deg | 3 | The inclination ($70\pm5\ensuremath{^\circ}$) and position angle ($-91.7\pm4.5\ensuremath{^\circ}$) |
| ALMA disk peak radius | 35 | 25 | au | 3 | the disk detected with ALMA peaks at radii of $35\pm25~\ensuremath{\mathrm{au}}$ at $1\sigma$ |
| Dust mass | 0.067 | not stated | Earth masses | 4 | We obtained a dust mass for HD 120326 of $0.067~\ensuremath{\mathrm{M}_\oplus}$. |
| Disk fractional luminosity (SED) | 1.8e-3 | not stated | dimensionless | 0 | a temperature of $110 \pm 1$ K and a fractional luminosity of $1.8 \times 10^{-3}$ |
| Maximum polarization fraction at 1.6 um | 51 | 6 | % | 0 | maximum polarization fraction of $51\pm6\,\%$ |

## Qualitative findings

- 12CO not detected; ALMA disk is unresolved and consistent with the SPHERE inner belt, identified as a planetesimal belt  
  > "We did not detect any $^{12}$CO emission." (abstract)

## Claim tuples

- H: Does the mm emission trace the same belt as seen in SPHERE? | E: uv-plane MCMC modeling of ALMA visibilities | R: Inclination 70±5 deg, PA -91.7±4.5 deg, peak radius 35±25 au | F: The inner belt is a planetesimal belt | **supported**
- H: What are the disk dust mass and fractional luminosity? | E: SED fit with ALMA point and dust mass formula | R: f=1.8e-3, Mdust=0.067 Mearth | F: Similar to beta Pictoris | **supported**

## Reasoning

- Why this data: _not stated_
- Why this method: _not stated_
- How they decided it was enough: _not stated_
- Limitation (authors): ALMA resolution limits conclusions on the mm belt morphology  
  > "While the resolution clearly limits the conclusions that can be drawn" (4.1 Morphology of the disk)
- Caveat (inferred, ours): ALMA beam (~1 arcsec) barely resolves the disk, so radius is poorly constrained
- Caveat (inferred, ours): Dust mass depends on assumed opacity and single temperature

## Reproducibility

- Data public (paper): ALMA project ID given; code MoDiSc open-access  
  > "We present the open-access code `MoDiSc` (Modeling Disks in Scattered light)" (Abstract)
- Products in archive: _not stated_
- Code: MoDiSc at github.com/cdesgrange/MoDiSc  
  > "<https://github.com/cdesgrange/MoDiSc>" (footnote 7)
- Missing: MCMC priors and chain length for ALMA fit
- Missing: tclean cell/image size
- Missing: Gaussian uv-fit setup
- Data volume (inferred): ~10-50 GB for five Band 6 executions
- Score (inferred): 5/5, ALMA part is a small portion with partial detail; MCMC and imaging settings are missing.
- Rediscovery candidate: no, ALMA analysis is partly specified but the flux and morphology fits lack key settings.

## Links

- Method: tazzari_galario_2018 (visibility modeling)
- Method: kennedy_unexpected_2020 (debris disk model)
- Companion: bonnefoy_belts_2017 (earlier SPHERE study)
- Companion: olofsson_vertical_2022 (polarimetric study)

## Checks

```json
{
 "quotes": 53,
 "quotes_ok": 53,
 "quote_pass_rate": 1.0,
 "quotes_too_long": 0,
 "unsupported_facts": 0,
 "project_codes": 1,
 "codes_not_in_text": [],
 "codes_not_in_obscore": [],
 "obscore_codes_not_in_card": [],
 "codes_printed_but_missing": [],
 "numeric_results": 7,
 "numeric_problems": 0,
 "fill": {
  "facts": 71,
  "stated": 41,
  "rate": 0.577
 },
 "evidence_ok": true
}
```
