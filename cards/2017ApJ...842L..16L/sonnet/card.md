# ALMA [N II] 205 μm Imaging Spectroscopy of the Interacting Galaxy System BRI 1202-0725 at Redshift 4.7

`2017ApJ...842L..16L` | The Astrophysical Journal Letters 2017 | first author: Lu, Nanyao | arXiv: 1706.03018 | DOI: 10.3847/2041-8213/aa77fc

Card schema 1.0 | model claude-sonnet-5-5 | depth full | type observational_alma_primary

## Science

- Fields: high_z_galaxies, agn_and_quasars
- Question: Use [N II] 205 um to CO(7-6) flux ratio to constrain dust temperature, FIR luminosity, SFR and gas depletion in the QSO and SMG of BRI 1202-0725 at z=4.7  
  > "The ratio of the [N ii] flux to the existing CO (7$-$6) flux is used to constrain the dust temperature ($T_{\rm dust}$) for a more accurate determination of the FIR luminosity $L_{\rm FIR}$." (abstract)
- Target **BRI 1202-0725 (QSO, SMG, LAE1, LAE2)**: coordinates QSO 12h05m23s13, -7d42'32.8" (J2000, Table 1)  
  > "At $z = 4.694$, the luminosity distance is 44,172 Mpc and 1$''$ corresponds to 6.6 kpc." (Analysis and Discussion); z/distance z = 4.695 (QSO), 4.692-4.693 (SMG); D_L = 44,172 Mpc at z=4.694  
  > "At $z = 4.694$, the luminosity distance is 44,172 Mpc and 1$''$ corresponds to 6.6 kpc." (Analysis and Discussion); distance from cosmology (flat, Omega_M=0.27, H0=71) from measured redshift  
  > "At $z = 4.694$, the luminosity distance is 44,172 Mpc and 1$''$ corresponds to 6.6 kpc." (Analysis and Discussion)

## Data provenance

- ALMA projects: 2015.1.00388.S
- bands: Band 6  
  > "BRI 1202-0725 was observed in ALMA Band 6 in the time division mode." (Observations and Results)
- frequencies and spectral setup: 4 SPWs of 1875 MHz; one on [N II] at ~256.6 GHz, three continuum at 254.6, 240.6, 238.6 GHz; 128 channels, 31.25 MHz (~36.5 km/s)  
  > "Each SPW has 128 channels with an effective resolution of 31.25 MHz ($\sim$36.5 km s$^{-1}$)." (Observations and Results)
- continuum bandwidth: _not stated_
- arrays: _not stated_
- configurations: _not stated_
- baselines: 15.1 to 310.2 m (first execution), 15.1 to 460.0 m (second)  
  > "the second on March 13, 2016 using 38 antennas and baselines ranging from 15.1 to 460.0 meters." (Observations and Results)
- angular resolution: 1.0" x 0.8" PA 75 deg (natural); 0.7" x 0.6" (robust=0)  
  > "resulting in a synthesized beam of 1.0$''$$\times$0.8$''$ (full width at half maximum; FWHM) at a position angle (PA) of 75$^\circ$ (N to E) for both continuum and line data." (Observations and Results)
- max recoverable scale: _not stated_
- sensitivity: continuum rms ~34 uJy/beam; line rms ~0.3 mJy/beam per 100 km/s channel  
  > "with an r.m.s. noise of $\sim$0.3 mJy beam$^{-1}$ in individual channels." (Observations and Results)
- time on source: 2 executions, 20.3 min each on target  
  > "The observation consisted of 2 independent executions, each with a 20.3 min on-target integration." (Observations and Results)
- observing dates: January 8, 2016 and March 13, 2016  
  > "The first was executed on January 8, 2016 using 37 antennas" (Observations and Results)
- pi or archival as stated: _not stated_
- Line: [N II] 205 um fine-structure (1461.13 GHz)
- External data: CO(7-6) line fluxes used for L_CO(7-6)  
  > "$^{i}$ Based on the line fluxes in Salomé et al. (2012)." (Table 1) [from Salomé et al. 2012]
- External data: [C II] line fluxes used for L_[CII]  
  > "$^{j}$ Based on the line fluxes in Wagg et al. (2012)." (Table 1) [from Wagg et al. 2012]
- External data: Local (U)LIRG and high-z sample line ratios vs C(60/100) used for calibration  
  > "for the local (U)LIRGs and high-$z$ galaxies used in Lu15." (Dust Continuum) [from Lu et al. 2015 (Lu15)]

## Processing

### Calibration

- pipeline or manual: CASA 4.5.3 data reduction; calibrators J1229+0230 and J1159-0940  
  > "The data reduction was carried out with the Common Astronomy Software Applications (CASA) 4.5.3" (Observations and Results)
- casa version: CASA 4.5.3  
  > "The data reduction was carried out with the Common Astronomy Software Applications (CASA) 4.5.3" (Observations and Results)
- pipeline version: _not stated_
- archive products used as is: _not stated_
- flux calibrator: _not stated_
- flux scale uncertainty: ALMA flux uncertainties exclude absolute calibration uncertainty  
  > "The ALMA flux uncertainties cited do not include the absolute calibration uncertainty." (Table 1)
- self calibration: _not stated_

### Imaging

- task: _not stated_
- deconvolver: _not stated_
- weighting robust: natural weighting; Briggs robust = 0 for enhanced resolution  
  > "we also cleaned the data using the Briggs weighting (with *robust* $= 0$) to lower the sidelobes" (Observations and Results)
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
- final beam: 1.0"x0.8" PA 75 (natural)  
  > "resulting in a synthesized beam of 1.0$''$$\times$0.8$''$" (Observations and Results)
- final rms: 34 uJy/beam continuum; 0.3 mJy/beam per channel  
  > "is $\sim$34 $\mu$Jy beam$^{-1}$." (Observations and Results)

### Inherited from earlier work

- SFR from L_CO(7-6), C(60/100) calibration and dual-line method  
  > "Following Lu15, the SFR inferred from $L_{\rm CO(7-6)}$ is 5.1 $(6.9) \times 10^3$" (Star Formation Properties) [from Lu et al. 2015 (Lu15)]
- Molecular gas mass from rest-frame 850 um flux  
  > "Following Scoville et al. (2016), we estimated the molecular gas mass" (Star Formation Properties) [from Scoville et al. 2016]

### Not stated but needed to reproduce (our reading)

- Continuum-subtraction method and line-free channels
- Clean threshold, mask, cell and image size
- Flux calibrator flux values and which was used for which role
- Modified blackbody SED fit details and photometry used
- Exact conversions of C(60/100) to Tdust
- Self-calibration not mentioned

## Analysis recipe

1. **Image continuum and [N II] cube**: Clean with natural weighting; also robust=0 for enhanced resolution  
  > "the final images were cleaned using the natural weighting" (Observations and Results)
   - software: CASA
   - parameter: 100 km/s channels  
  > "The final [N ii] spectral cube has a velocity channel width of 100  km s$^{-1}$" (Observations and Results)
   - fitting: _not stated_
   - validation: _not stated_
2. **Measure [N II] flux and size**: Extract spectra in elliptical apertures, fit single Gaussian plus constant; 2D Gaussian fit to image and deconvolve beam  
  > "we fit to their spectrum a single Gaussian profile plus a constant to derive the line flux." ([N ii] Line Emission)
   - fitting: Gaussian fits  
  > "For the QSO and SMG, we fit to their spectrum a single Gaussian profile plus a constant to derive the line flux." (Analysis and Discussion, [N ii] Line Emission)
   - validation: _not stated_
3. **Measure continuum flux**: 2D Gaussian fit to each galaxy after masking others  
  > "by fitting a 2d Gaussian to the galaxy image in Fig. 1a after temporarily masking out the other galaxies." (Dust Continuum)
   - fitting: 2D Gaussian  
  > "We derive the total continuum flux density of a galaxy by fitting a 2d Gaussian to the galaxy image in Fig. 1a after temporarily masking out the other galaxies." (Analysis and Discussion, Dust Continuum)
   - validation: _not stated_
4. **Derive C(60/100) and Tdust**: Intersect [C II]/CO(7-6) and [N II]/CO(7-6) ratios with least-squares bisector fit to local (U)LIRGs; average values  
  > "The black line in each plot is a least-squares bisector fit (Isobe et al. 1990) to the local (U)LIRGs of detections only, excluding the AGNs" (Dust Continuum)
   - parameter: uncertainty on C(60/100) ~0.15  
  > "We set the uncertainty of these FIR colors to the horizontal scatter w.r.t. the black line in the [N ii] plot, i.e., $\sim$0.15." (Dust Continuum)
   - assumption: beta = 1.8  
  > "Assuming $\beta = 1.8$ (Planck Collaboration et al. 2011)" (Dust Continuum)
   - fitting: Least-squares bisector  
  > "The black line in each plot is a least-squares bisector fit (Isobe et al. 1990) to the local (U)LIRGs of detections only, excluding the AGNs" (Analysis and Discussion, Dust Continuum)
   - validation: Two independent line ratios agree within scatter  
  > "The difference between these values is smaller than the scatter (0.15 to 0.2) in these plots." (Dust Continuum)
5. **Fit SED and derive L_FIR**: Modified blackbody with Tdust=43 K, beta=1.8 fixed  
  > "after fixing $T_{\rm dust}$ at 43 K and $\beta$ at 1.8" (Dust Continuum)
   - fitting: Modified blackbody, T and beta fixed  
  > "Our best modified-blackbody SED fits for the QSO and SMG separately, after fixing $T_{\rm dust}$ at 43 K and $\beta$ at 1.8, are also shown in Fig. 4." (Analysis and Discussion, Dust Continuum)
   - validation: Similar SED from CO(7-6) continuum plus C(60/100)  
  > "We note that similar SED fits would be obtained by using only the continuum flux from the CO (7$-$6) observation and our adopted $C(60/100)$." (Dust Continuum)
6. **Derive SFR, SF size, gas mass, depletion time**: SFR from L_CO(7-6) (Chabrier IMF); Sigma_SFR from C(60/100) and Tdust correlations; d from Sigma_SFR; Mgas from 850 um flux  
  > "The face-on FWHM diameter, $d$, of the SF region can be estimated via $\Sigma_{\rm SFR} = (\frac{1}{2}\,{\rm SFR})/({\frac{1}{4}}\pi\,d^2)$." (Star Formation Properties)
   - assumption: Sigma_SFR = 2e3 Msun/yr/kpc^2; Chabrier IMF  
  > "assuming $\Sigma_{\rm SFR} = 2,000\,M_{\odot}$ yr$^{-1}$ kpc$^{-2}$." (Table 1)
   - fitting: _not stated_
   - validation: Two Sigma_SFR correlations give comparable estimates  
  > "these two independent correlations give comparable estimates for $\Sigma_{\rm SFR}$" (Star Formation Properties)

## Software

- **CASA** 4.5.3: Data reduction and cleaning  
  > "The data reduction was carried out with the Common Astronomy Software Applications (CASA) 4.5.3" (Observations and Results)

## Numeric results

| quantity | value | uncertainty | units | step | quote |
|---|---|---|---|---|---|
| Tdust (QSO and SMG) | 43 | ±2 | K | 4 | Our best estimated $T_{\rm dust}$ equals $43\ (\pm 2)$ K for both galaxies |
| [N II] flux QSO | 1.01 | ±0.02 | Jy km/s | 2 | 1.01 ($\pm 0.02$) |
| [N II] flux SMG | 0.99 | ±0.02 | Jy km/s | 2 | 0.99 ($\pm 0.02$) |
| L_FIR QSO (SMG) | 2.3 (2.4)e13 | ±18% | Lsun | 5 | is $2.3$ $(2.4) \times 10^{13}\,L_{\odot}$ |
| SFR QSO (SMG) | 5.1 (6.9)e3 | 30% | Msun/yr | 6 | has a SFR of 5.1 $(6.9) \times 10^3\,M_{\odot}$ yr$^{-1}$ ($\pm$ 30%) |
| [N II] deconvolved major axis QSO (SMG) | 9 (14) | not stated | kpc | 2 | The de-convolved major axes correspond to $\sim$14 and 9 kpc for the SMG and QSO, respectively. |
| Continuum S(256 GHz) QSO (SMG) | 7.58 (7.20) | ±0.01 | mJy | 3 | 7.58 ($\pm 0.01$) |
| SF diameter QSO (SMG) | 1.3 (1.5) | not stated | kpc | 6 | the resulting $d = 1.3$ (1.5) kpc for the QSO (SMG) |
| Gas depletion time QSO (SMG) | 10 (7)e7 | not stated | yr | 6 | The gas depletion time $\tau_{\rm gas} \approx$ 10 (7) $\times 10^7$ years for the QSO (SMG). |

## Qualitative findings

- [N II] emission is more extended than continuum and [C II]; QSO [N II] marginally resolved into 3 peaks suggesting tidal interaction  
  > "The relative positions of (ii) and (iii) are suggestive of tidal interaction or gas connection between the member galaxies." (Observations and Results)

## Claim tuples

- H: Is [N II] more extended than dust continuum in the QSO and SMG? | E: Gaussian fits to [N II] and continuum images | R: [N II] major axes 9 and 14 kpc; continuum unresolved | F: [N II] is much more diffuse than dust or [C II] | **supported**
- H: Does L_CO(7-6) trace SFR in these galaxies? | E: Compare L_CO(7-6)/L_FIR with local (U)LIRGs using Tdust=43 K | R: log ratio -4.54 and -4.42 vs local -4.61, within ~1.5 sigma | F: Consistent with local (U)LIRGs | **supported**

## Reasoning

- Why this data: _not stated_
- Why this method: _not stated_
- How they decided it was enough: _not stated_
- Limitation (authors): AGN sample too small for firm conclusion on AGN segregation; Mgas uncertain by factor ~2  
  > "The formal uncertainty for $M_{\rm gas}$ is about a factor of 2." (Star Formation Properties)
- Caveat (inferred, ours): Tdust depends on local-sample calibration and fixed beta
- Caveat (inferred, ours): SED fit poorly constrained at peak
- Caveat (inferred, ours): Archival Pavesi et al. data gave different [N II] fluxes, not reconciled in detail

## Reproducibility

- Data public (paper): _not stated_
- Products in archive: _not stated_
- Missing: Calibration and imaging details beyond weighting
- Missing: SED photometry list and fit procedure
- Missing: Lu15 calibration relations
- Data volume (inferred): ~10-30 GB raw (two short Band 6 executions)
- Score (inferred): 3/5, Short letter; ALMA project code and CASA version given, but imaging and SED details are sparse and rely on Lu15.
- Rediscovery candidate: no, Recipe depends on external calibration relations from Lu15 and unspecified SED details.

## Links

- Method: Lu et al. 2015 (Lu15) (Dual-line method for SFR and C(60/100))
- Method: Scoville et al. 2016 (Gas mass from 850 um flux)
- Companion: Pavesi et al. 2016 (Independent analysis of archival ALMA [N II] data)
- Related: Cycle-3 ALMA snapshot survey of 8 ULIRGs and 4 LIRGs at 4<z<5.5

## Checks

```json
{
 "quotes": 56,
 "quotes_ok": 56,
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
  "facts": 73,
  "stated": 42,
  "rate": 0.575
 },
 "evidence_ok": true
}
```
