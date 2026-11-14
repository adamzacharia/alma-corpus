# ALMA Reveals Spatially Resolved Properties of Molecular Gas in the Host Galaxy of FRB 20191001A at z = 0.2340

`2024ApJ...969..122Y` | The Astrophysical Journal 2024 | first author: Yamanaka, Itsuki | arXiv: 2407.01889 | DOI: 10.3847/1538-4357/ad553f

Card schema 1.0 | model claude-sonnet-5-5 | depth full | type observational_alma_primary

## Science

- Fields: nearby_galaxies, transients
- Question: What are the spatially resolved molecular gas properties and kinematics of the FRB 20191001A host galaxy and its companion, and the gas and continuum limits at the FRB site?  
  > "We derive molecular gas properties of these galaxies and at the FRB location and discuss its progenitors and possible effects of the galactic interaction." (1 Introduction)
- Target **HG 20191001A (host of FRB 20191001A)**: coordinates 21h33m24.44s, -54d44m54.65s (J2000)  
  > "localized to a host galaxy DESJ213324.44-544454.65 at $z=0.2340$ (hereafter HG 20191001A, or simply “the host”)" (2.1 Target); z/distance z=0.2340; D_L=1179 Mpc  
  > "localized to a host galaxy DESJ213324.44-544454.65 at $z=0.2340$ (hereafter HG 20191001A, or simply “the host”)" (2.1 Target); distance from optical redshift (Bhandari2020; Heintz2020)  
  > "localized to a host galaxy DESJ213324.44-544454.65 at $z=0.2340$ (hereafter HG 20191001A, or simply “the host”)" (2.1 Target)
- Target **the western source (J213323.65-544453.6)**: coordinates 21h33m23.65s, -54d44m53.6s (J2000)  
  > "The galaxy J213323.65-544453.6 at $z=0.2339$ (hereafter “the western source”) is located $\sim\SI{25}{kpc}$ to the west of this host" (2.1 Target); z/distance z=0.2339  
  > "The galaxy J213323.65-544453.6 at $z=0.2339$ (hereafter “the western source”) is located $\sim\SI{25}{kpc}$ to the west of this host" (2.1 Target); distance from _not stated_

## Data provenance

- ALMA projects: 2021.1.00027.S
- bands: Band 5  
  > "with ALMA Band 5 (Project code is 2021.1.00027.S)" (2.2 ALMA observations and data reduction)
- frequencies and spectral setup: SPWs 25, 27, 29, 31; 1.875 GHz each, 1920 channels  
  > "The spectral windows are 25, 27, 29, 31, and the correlator setup bandwidth was 1.875 GHz and subdivided into 1920 channels for each spectral window." (2.2 ALMA observations and data reduction)
- continuum bandwidth: _not stated_
- arrays: _not stated_
- configurations: _not stated_
- baselines: 15.1–500.2 m, 45 antennas  
  > "45 antennas were set up with baseline lengths of 15.1–500.2 m." (2.2 ALMA observations and data reduction)
- angular resolution: 0.94" x 0.91" (3.5x3.4 kpc2) cube beam  
  > "The synthesized beam sizes were $3.5\times3.4\,\si{kpc^2}(0.94\ensuremath{''} \times 0.91\ensuremath{''})$" (2.2 ALMA observations and data reduction)
- max recoverable scale: _not stated_
- sensitivity: 0.92 mJy/beam per 50 km/s channel; 3.0e-2 mJy/beam continuum  
  > "The rms noise level was $\SI{0.92}{mJy.beam^{-1}}$ for each channel of the $\SI{50}{km.s^{-1}}$ cube and $\SI{3.0e-2}{mJy.beam^{-1}}$ for the continuum map." (2.2 ALMA observations and data reduction)
- time on source: 11 min 9 sec  
  > "The total integration time on the science target was 11 min 9 sec." (2.2 ALMA observations and data reduction)
- observing dates: 2022 September 25, 01:15:40–01:49:37 UTC  
  > "were made on 2022 September 25, from 01:15:40 to 01:49:37 UTC" (2.2 ALMA observations and data reduction)
- pi or archival as stated: _not stated_
- Line: CO J=2–1 (not stated (nu_obs = 186.822 GHz))
- Other facility **ASKAP**: FRB detection and localization  
  > "FRB 20191001A was detected by the Australian Square Kilometre Array Pathfinder (ASKAP) on 2019 October 1" (2.1 Target)
- External data: Host stellar mass, SFR, metallicity  
  > "gas-phase metallicity is $12+\log(\mathrm{O/H})=\num{8.94+-0.05}$ (cite: Heintz2020)" (2.1 Target) [from (cite: Heintz2020)]
- External data: Western source SFR from 1.4 GHz luminosity  
  > "The SFR of the western source is estimated to be about $\SI{21}{M_\odot.yr^{-1}}$ based on the 1.4 GHz luminosity (cite: Bhandari2020)." (2.1 Target) [from (cite: Bhandari2020)]
- External data: Comparison FRB host gas masses and SFRs  
  > "previously observed FRB host galaxies (brown-filled squares from (cite: Hatsukade2022) and (cite: Chittidi2023))" (3.1 HG 20191001A) [from (cite: Hatsukade2022; Chittidi2023)]
- External data: SN site column density distribution  
  > "compares it with the cumulative distribution of the SNe (cite: Galbany2017)" (4.2 Molecular gas property at the FRB site) [from (cite: Galbany2017)]

## Processing

### Calibration

- pipeline or manual: CASA pipeline  
  > "with the CASA pipeline version 6.4.1.12" (2.2 ALMA observations and data reduction)
- casa version: _not stated_
- pipeline version: 6.4.1.12  
  > "with the CASA pipeline version 6.4.1.12" (2.2 ALMA observations and data reduction)
- archive products used as is: _not stated_
- flux calibrator: _not stated_
- flux scale uncertainty: _not stated_
- self calibration: _not stated_

### Imaging

- task: tclean  
  > "Imaging was performed using the tclean task" (2.2 ALMA observations and data reduction)
- deconvolver: _not stated_
- weighting robust: briggs, robust = 2  
  > "a weighting of briggs, a robust parameter of 2" (2.2 ALMA observations and data reduction)
- uv taper: _not stated_
- cell size: 0.2"  
  > "with a cell size of $0.2\ensuremath{''}$" (2.2 ALMA observations and data reduction)
- image size: _not stated_
- masking: mask of CO emission area; threshold 2x rms  
  > "a threshold of twice the rms noise, and used a mask of CO emission area" (2.2 ALMA observations and data reduction)
- multiscale scales: _not stated_
- continuum subtraction: continuum map made excluding CO channels  
  > "The continuum map was created by excluding channels with CO emission." (2.2 ALMA observations and data reduction)
- line free channels: _not stated_
- primary beam correction: _not stated_
- array combination: _not stated_
- smoothing: _not stated_
- final beam: cube 0.94"x0.91"; continuum 1.1"x1.0"  
  > "$4.1\times3.8\si{kpc^2}(1.1\ensuremath{''} \times 1.0\ensuremath{''})$" (2.2 ALMA observations and data reduction)
- final rms: 0.92 mJy/beam per channel; 3.0e-2 mJy/beam continuum  
  > "The rms noise level was $\SI{0.92}{mJy.beam^{-1}}$ for each channel" (2.2 ALMA observations and data reduction)

### Inherited from earlier work

- CO(2-1)/CO(1-0) ratio 0.77 for typical star-forming galaxies  
  > "assuming the typical star-forming galaxy value of $L'_\mathrm{CO(2-1)}/L'_\mathrm{CO(1-0)}=0.77$ (cite: Genzel2015; Tacconi)" (3.1 HG 20191001A) [from (cite: Genzel2015; Tacconi)]
- L'CO equation  
  > "CO luminosity is calculated from the following equation by (cite: Solomon2004)" (3.1 HG 20191001A) [from (cite: Solomon2004)]

### Not stated but needed to reproduce (our reading)

- Line-free channels used for continuum
- Cleaning iteration limits and primary beam correction details
- Flux calibrator and flux scale uncertainty
- Aperture/region used for spectrum extraction and moment-0 integration
- 3DBarolo parameter file details (initial guesses, mask, thresholds)
- How FRB-site column density and upper limits were computed in detail
- SFR/stellar mass uncertainty propagation for mu_gas and t_depl

## Analysis recipe

1. **Image cube and continuum**: tclean with Briggs weighting, cube -1000 to 1000 km/s at 50 km/s; continuum from line-free channels  
  > "The data cube was generated over the velocity range from $\SI{-1000}{km.s^{-1}}$ to $\SI{1000}{km.s^{-1}}$ with a velocity resolution of $\SI{50}{km.s^{-1}}$." (2.2 ALMA observations and data reduction)
   - software: CASA
   - parameter: cell 0.2", robust 2  
  > "a cell size of $0.2\ensuremath{''}$, a weighting of briggs, a robust parameter of 2" (2.2 ALMA observations and data reduction)
   - fitting: _not stated_
   - validation: _not stated_
2. **Extract spectra, fit line width, flux**: Gaussian fit to CO line profile for FWHM; integrated intensity map by summing channels  
  > "Using the Gaussian function to fit the CO line profile, the velocity width of the galaxy (at the Full Width at Half Maximum; FWHM) was estimated" (3.1 HG 20191001A)
   - fitting: Gaussian  
  > "Using the Gaussian function to fit the CO line profile, the velocity width of the galaxy (at the Full Width at Half Maximum; FWHM) was estimated to be" (HG 20191001A)
   - validation: _not stated_
3. **Derive CO luminosity and molecular gas mass**: L'CO via Solomon & Vanden Bout; Mgas = alphaCO L'CO(1-0)  
  > "$$\begin{equation}
    M_\mathrm{gas}=\alpha_{\mathrm{CO}}L'_\mathrm{CO(1-0)},
\end{equation}$$" (3.1 HG 20191001A)
   - parameter: D_L=1179 Mpc, nu_obs=186.822 GHz  
  > "we adopt $\nu_{\mathrm{obs}} = \SI{186.822}{GHz}$, and $D_L=\SI{1179}{Mpc}$" (3.1 HG 20191001A)
   - assumption: alphaCO = 4.3 (Galactic), r21 = 0.77  
  > "we use the Galactic value $\alpha_\mathrm{CO}=\SI{4.3}{M_\odot. (K. km.s^{-1} pc^{-2})^{-1}}$" (3.1 HG 20191001A)
   - fitting: _not stated_
   - validation: alphaCO upper limit from dynamical mass is consistent with assumed value  
  > "This result is consistent with the value of $\alpha_\mathrm{CO}$ assumed in this study." (3.4 Modelling CO disk dynamics)
4. **Disk kinematic modelling and dynamical mass**: 3DBarolo tilted-ring fit, two passes (second with inclination and PA fixed), VRAD=0; Mdyn = R Vrot^2/G  
  > "$^\mathrm{3D}$Barolo fits tilted-ring models to a data cube. The ring width was set to $0.25\ensuremath{''}$" (3.4 Modelling CO disk dynamics)
   - software: 3DBarolo
   - parameter: ring width 0.25", normalization local  
  > "the normalization option was set to local" (3.4 Modelling CO disk dynamics)
   - assumption: no radial motion (VRAD=0)  
  > "The parameter VRAD, the galactocentric radial velocity, was fixed to 0 in the modeling" (3.4 Modelling CO disk dynamics)
   - fitting: _not stated_
   - validation: PV diagrams and Vrot/sigma >1  
  > "These values are higher than 1, supporting the rotation-dominated systems (cite: Pelliccia2017)." (3.4 Modelling CO disk dynamics)
5. **FRB-site limits**: 3 sigma upper limit on N(H2) with Galactic conversion factor and 100 km/s linewidth; 3 sigma 1.3 mm continuum limit  
  > "That is obtained by assuming the Galactic conversion factor, and the CO linewidth at the site, $\SI{100}{km.s^{-1}}$" (3.3 FRB 20191001A site)
   - fitting: _not stated_
   - validation: _not stated_

## Software

- **CASA** 6.4.1.12 (pipeline): data reduction and tclean imaging  
  > "Data reduction was performed with the Common Astronomy Software Application (CASA; (cite: TheCASATeam_2022))" (2.2 ALMA observations and data reduction)
- **3DBarolo** : tilted-ring modelling of CO disk dynamics  
  > "CO disk dynamics of both galaxies were modeled by $^\mathrm{3D}$Barolo (cite: Teodoro2015)." (3.4 Modelling CO disk dynamics)

## Numeric results

| quantity | value | uncertainty | units | step | quote |
|---|---|---|---|---|---|
| Host CO(2-1) integrated flux | 6.0 | 1.0 | Jy km/s | 2 | $S_\mathrm{CO}\Delta V$($\si{Jy.km.s^{-1}}$)   /  $\num{6.0 +- 1.0}$ |
| Host molecular gas mass | 2.3e10 | 0.4e10 | Msun | 3 | The inferred molecular gas mass of the host galaxy is $\SI{2.3+-0.4e+10}{M_\odot}$ |
| Host molecular gas fraction | 0.50 | 0.22 | dimensionless | 3 | $\mu_\mathrm{gas}=\num{0.50+-0.22}$ |
| Host CO FWHM | 346 | 49 | km/s | 2 | was estimated to be $\SI{346+-49}{km.s^{-1}}$ |
| Western source gas mass | 2.9e10 | 0.3e10 | Msun | 3 | $M_\mathrm{gas}=\SI{2.9+-0.3e+10}{M_\odot}$ were calculated |
| Host dynamical mass at R=8.0 kpc | 7.8e10 | 2.0e10 | Msun | 4 | $M_\mathrm{dyn}=\SI{7.8 +- 2.0e+10}{M_\odot}$ for the host |
| Upper limit alphaCO | <5.9 | not stated | Msun/(K km/s pc^2) | 4 | $\alpha_\mathrm{CO} < \SI{5.9}{M_\odot.(K .km.s^{-1}. pc^{-2})^{-1}}$ |
| N(H2) at FRB site (3 sigma) | <2.1e21 | not stated | cm^-2 | 5 | is $< \SI{2.1e+21}{cm^{-2}}$ |
| Host half-light radius | 6.9 | 0.7 | kpc | 4 | derive the half-light radius to be $\SI{6.9+-0.7}{ kpc}$ for the host |
| Host inclination | 61 | 5 | deg | 4 | $i$(deg) / $\num{61+-5}$ |
| Host Vrot | 205 | 26 | km/s | 4 | $V_\mathrm{rot}$($\si{km.s^{-1}}$) / $\num{205+-26}$ |

## Qualitative findings

- Both host and western source are rotation-dominated; no clear interaction signs in kinematics.  
  > "We do not find a clear sign of interaction between these galaxies." (3.4 Modelling CO disk dynamics)

## Claim tuples

- H: Is the host of FRB 20191001A gas-rich compared to other FRB hosts? | E: CO(2-1) mapping and conversion to gas mass | R: Mgas = 2.3e10 Msun, mu_gas = 0.50 | F: Expands the range of FRB host gas mass, favouring multiple progenitors or sources unrelated to recent star formation | **supported**
- H: Does galaxy interaction disturb the host's molecular gas and trigger FRB? | E: 3DBarolo kinematic modelling | R: Velocity fields well fitted by rotation; Vrot/sigma 49 and 42 | F: Interaction effect likely weak; FRB not likely triggered by it | **supported**
- H: Can molecular gas at the FRB site constrain the progenitor? | E: 3 sigma upper limit on N(H2) compared with SN sites | R: <2.1e21 cm^-2, above median of SN types | F: Does not constrain progenitor | **partially**

## Reasoning

- Why this data: _not stated_
- Why this method: _not stated_
- How they decided it was enough: _not stated_
- Limitation (authors): Sample size too small for statistical conclusions; FRB-site limit not constraining.  
  > "The sample size is insufficient to show that this difference is statistically significant" (3.1 HG 20191001A)
- Caveat (inferred, ours): Galactic alphaCO and r21=0.77 assumed; large systematic uncertainty
- Caveat (inferred, ours): Short integration, low S/N (~10) limits kinematic fit; inclination 61 deg with beam ~ disk size
- Caveat (inferred, ours): Robust=2 (natural weighting) cube coarse 50 km/s channels
- Caveat (inferred, ours): Vdisp values consistent with zero within errors

## Reproducibility

- Data public (paper): ALMA project code given; public status not stated  
  > "(Project code is 2021.1.00027.S)" (2.2 ALMA observations and data reduction)
- Products in archive: _not stated_
- Missing: Spectrum extraction regions
- Missing: 3DBarolo detailed parameters
- Missing: Line-free channels and flux calibrator
- Data volume (inferred): ~10-30 GB raw single-EB Band 5 dataset
- Score (inferred): 3/5, Single public dataset and basic recipe with clear numbers, but extraction regions and 3DBarolo settings are missing.
- Rediscovery candidate: yes, Single archival dataset with stated imaging parameters and numeric results (gas mass, FWHM, flux).

## Links

- Method: (cite: Teodoro2015) (3DBarolo)
- Method: (cite: Solomon2004) (L'CO formula)
- Companion: (cite: Hatsukade2022) (previous CO observations of FRB hosts)
- Companion: (cite: Heintz2020) (host properties)
- Related: EDGE-CALIFA
- Related: PHIBSS2

## Checks

```json
{
 "quotes": 64,
 "quotes_ok": 64,
 "quote_pass_rate": 1.0,
 "quotes_too_long": 0,
 "unsupported_facts": 0,
 "project_codes": 1,
 "codes_not_in_text": [],
 "codes_not_in_obscore": [],
 "obscore_codes_not_in_card": [],
 "codes_printed_but_missing": [],
 "numeric_results": 11,
 "numeric_problems": 0,
 "fill": {
  "facts": 77,
  "stated": 47,
  "rate": 0.61
 },
 "evidence_ok": true
}
```
