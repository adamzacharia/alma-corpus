# ALMA + VLT observations of a damped Lyman-α absorbing galaxy: massive, wide CO emission, gas-rich but with very low SFR

`2018MNRAS.474.4039M` | Monthly Notices of the Royal Astronomical Society 2018 | first author: Møller, P. | arXiv: 1711.00407 | DOI: 10.1093/mnras/stx2845

Card schema 1.0 | model claude-sonnet-5-5 | depth full | type observational_alma_primary

## Science

- Fields: high_z_galaxies
- Question: What are the molecular gas content, kinematics and star formation of a DLA host galaxy at z=0.716, and does it follow scaling relations of flux-selected galaxies?  
  > "to measure their molecular gas masses, kinematical properties of the gas, determine the mass fractions in gas and stars, and their distributions, the star formation efficiencies" (Introduction)
- Target **DLA galaxy towards J1323-0021 (ALMA J132323.81-002154.1)**: coordinates QSO SDSS J132323.78-002155.2; galaxy ALMA J132323.81-002154.1  
  > "a second DLA, at $z_{\rm abs}=0.7163$ towards J1323$-$0021 (SDSS J132323.78-002155.2)" (Introduction); "The absorber was originally detected by (cite: rao06) via Hubble Space Telescope (HST) spectroscopy." (Introduction); z/distance z = 0.7163 (z_CO = 0.71645)  
  > "a second DLA, at $z_{\rm abs}=0.7163$ towards J1323$-$0021 (SDSS J132323.78-002155.2)" (Introduction); "The absorber was originally detected by (cite: rao06) via Hubble Space Telescope (HST) spectroscopy." (Introduction); distance from CO, optical emission lines and UVES absorption redshifts from this work  
  > "a second DLA, at $z_{\rm abs}=0.7163$ towards J1323$-$0021 (SDSS J132323.78-002155.2)" (Introduction); "The absorber was originally detected by (cite: rao06) via Hubble Space Telescope (HST) spectroscopy." (Introduction)

## Data provenance

- ALMA projects: 2013.1.01178.S
- bands: Band 4  
  > "was observed with ALMA using the band 4 receivers" (2.1 ALMA observations)
- frequencies and spectral setup: One 1.875 GHz window with 480 channels at 134.3 GHz (CO 2-1), ~16.4 km/s resolution after Hanning smoothing; three continuum windows of 2 GHz, 128 channels each  
  > "A single high-resolution 1.875 GHz band, sub-divided into 480 channels, was centred at the redshifted CO(2-1) line frequency ($134.3$ GHz)" (2.1 ALMA observations); "the three other bands were used in low-resolution mode, giving 2 GHz bandwidth and 128 channels each" (2.1 ALMA observations)
- continuum bandwidth: _not stated_
- arrays: Forty 12-m antennas  
  > "Forty 12-metre ALMA antennas were used for the observations, with a maximum baseline of 348.5 m." (2.1 ALMA observations)
- configurations: _not stated_
- baselines: max 348.5 m  
  > "with a maximum baseline of 348.5 m" (2.1 ALMA observations)
- angular resolution: 2.7" x 2.2" (after taper)  
  > "The resulting spectral cube has a synthesized beam of extent $2.7\ensuremath{''} \times
2.2\ensuremath{''}$" (2.1 ALMA observations)
- max recoverable scale: _not stated_
- sensitivity: continuum RMS 16.4 uJy/beam; cube RMS 0.25 mJy/beam per 50 km/s channel  
  > "has a root-mean-square (RMS) noise level of 16.4 $\mu$Jy/beam" (2.1 ALMA observations); "an RMS noise of 0.25 mJy/beam per 50 ${\rm km\,s^{-1}}$ channel" (2.1 ALMA observations)
- time on source: ~40 minutes  
  > "The total on-source time was approximately 40 minutes." (2.1 ALMA observations)
- observing dates: 27 December 2014  
  > "on 27 December 2014" (2.1 ALMA observations)
- pi or archival as stated: _not stated_
- Line: CO J=2-1 (not stated (observed at 134.3 GHz))
- Other facility **VLT FORS2**: New long-slit spectrum giving [OII] emission  
  > "The galaxy was observed on 17 and 18 April 2015, with FORS2 long-slit spectroscopy using the grism 600RI" (2.3 VLT-FORS2 data)
- Other facility **VLT SINFONI**: Archival J-band IFU data re-reduced: Halpha, [NII], J-band continuum  
  > "we retrieved the SINFONI dataset (programme ID: 079.A-0673) from the European Southern Observatory (ESO) archive and re-reduced it." (2.4 VLT SINFONI data)
- Other facility **Herschel SPIRE**: 250 and 350 micron photometry for dust SED  
  > "We obtained the re-calibrated maps from the Herschel science archive." (2.2 Herschel data)
- Other facility **VLT UVES and HST STIS**: Absorption redshifts, Delta v90, N(HI)  
  > "We obtained the advanced data product VLT-UVES spectrum of the QSO, presented in (cite: peroux06), from the ESO data archive." (2.5 VLT UVES and HST STIS data)
- External data: ugri photometry of the galaxy  
  > "The input photometry of the galaxy in $ugri$ filters is taken from (cite: rao11)." (3.4.1) [from (cite: rao11)]
- External data: K-band magnitude and position (PA 24.5 deg, 1.25")  
  > "The near-IR $K$-band data are from (cite: hewett07)" (3.4.1) [from (cite: hewett07); (cite: chun10)]
- External data: Properties of g0439 (stellar mass, gas mass, inclination)  
  > "\[b\] (cite: neeleman16)" (Table 4) [from (cite: christensen14); (cite: neeleman16)]
- External data: Comparison samples COLD GASS, ALLSMOG, PHIBSS  
  > "COLD GASS, at $z \approx 0.02$ (cite: saintonge11), ALLSMOG at $z \approx 0.04$ (cite: bothwell14; cicone2017), and PHIBSS at $z \approx 1.2$ and $\approx 2.2$ (cite: tacconi13)" (4.1) [from (cite: saintonge11); (cite: cicone2017); (cite: tacconi13)]

## Processing

### Calibration

- pipeline or manual: CASA, standard procedures  
  > "The data editing, calibration and imaging was carried out in the casa (Common Astronomy Software Applications) package, using standard procedures." (2.1 ALMA observations)
- casa version: _not stated_
- pipeline version: _not stated_
- archive products used as is: _not stated_
- flux calibrator: 3C279  
  > "Flux calibration was obtained through observing the quasar 3C279" (2.1 ALMA observations)
- flux scale uncertainty: _not stated_
- self calibration: Not done; QSO too faint  
  > "This is, however, too faint for the purpose of self-calibration." (2.1 ALMA observations)

### Imaging

- task: _not stated_
- deconvolver: _not stated_
- weighting robust: Briggs robust 0.5 (continuum)  
  > "This image was made using “robust” weighting, with a Briggs parameter of 0.5" (2.1 ALMA observations)
- uv taper: visibilities tapered beyond 75 klambda  
  > "we tapered the visibilities beyond 75 k$\lambda$ during the imaging" (2.1 ALMA observations)
- cell size: _not stated_
- image size: _not stated_
- masking: _not stated_
- multiscale scales: _not stated_
- continuum subtraction: _not stated_
- line free channels: _not stated_
- primary beam correction: _not stated_
- array combination: _not stated_
- smoothing: _not stated_
- final beam: 2.7" x 2.2"  
  > "synthesized beam of extent $2.7\ensuremath{''} \times
2.2\ensuremath{''}$" (2.1 ALMA observations)
- final rms: 0.25 mJy/beam per 50 km/s channel  
  > "an RMS noise of 0.25 mJy/beam per 50 ${\rm km\,s^{-1}}$ channel" (2.1 ALMA observations)

### Inherited from earlier work

- Double-horn fitting formula for CO line width (W50, W20)  
  > "we use the same fitting formula for a double-horn profile (cite: tiley2016)" (3.3) [from (cite: tiley2016)]
- SFR conversion factors from luminosities  
  > "using the conversion factors in (cite: kennicutt98)" (3.4.2) [from (cite: kennicutt98)]
- Herschel aperture photometry procedure  
  > "We performed aperture photometry following the description of SPIRE point source photometry in (cite: pearson14)" (2.2 Herschel data) [from (cite: pearson14)]
- N2 metallicity calibration  
  > "we use the calibration relation of (cite: maiolino08)" (3.4.4) [from (cite: maiolino08)]

### Not stated but needed to reproduce (our reading)

- Line-free channels used for continuum imaging
- CASA version
- Continuum-subtraction method for the cube
- Cell and image size, deconvolver, clean threshold
- Velocity range and aperture details for the line-profile extraction fit
- Primary beam correction details
- Absolute flux uncertainty adopted for ALMA
- Details of spectral-line fit errors for double-horn fit

## Analysis recipe

1. **image continuum and CO cube**: CASA imaging of continuum (robust 0.5) and CO cube in 50 km/s channels with 75 klambda taper; point-source subtraction at QSO position  
  > "A data cube covering the CO(2-1) line redshifted to the redshift of the DLA was made by imaging the high-resolution visibility dataset in 50 ${\rm km\,s^{-1}}$-wide spectral channels." (2.1 ALMA observations)
   - software: CASA
   - fitting: _not stated_
   - validation: Continuum centroid agrees with optical galaxy position  
  > "The position of the centroid of the continuum emission is in excellent agreement with the galaxy position in the optical image." (2.1 ALMA observations)
2. **molecular gas mass**: Convert CO(2-1) flux to CO(1-0) luminosity via r21, then multiply by alpha_CO  
  > "Using $\alpha_{\rm CO} = 4.2 \: {\rm
  M}_\odot$ (K ${\rm km\,s^{-1}}$ pc$^2$)$^{-1}$ (cite: bolatto13)" (3.1)
   - assumption: alpha_CO = 4.2 (incl. helium), r21 = 0.6  
  > "We will assume sub-thermal excitation of the J$=2$ level and a brightness temperature line ratio of $r_{21}
\approx 0.6$" (3.1)
   - fitting: _not stated_
   - validation: Starburst alternative (alpha_CO=1, r21=1) considered unlikely given low SFR  
  > "we consider the starburst scenario to be unlikely" (3.1)
3. **CO line width and dynamical mass**: Fit double-horn profile for W50/W20; second fit locking centre to Halpha and a Gaussian to the blue peak; Mdyn ~ DV^2 R/G  
  > "To test this possibility we also perform a second fit using the same functional form, but now locking the central frequency of the fit to that of the H$\alpha$ line." (3.3)
   - assumption: inclination 48 deg (most conservative); R >= 6.5 kpc  
  > "Using the most conservative value we get W50/sin(48$^o$) = 871 ${\rm km\,s^{-1}}$." (3.3)
   - fitting: _not stated_
   - validation: _not stated_
4. **stellar mass from SED**: Hyperz fit of ugrK and SINFONI photometry, Chabrier IMF, 10^3 Monte Carlo realisations for errors  
  > "To derive the 68% confidence intervals for the results, we assume a Gaussian error distribution, propagate the magnitude errors, and perform SED fits to $10^3$ random realisations." (3.4.1)
   - software: Hyperz
   - assumption: Chabrier IMF; metallicity 0.2-2.5 solar; i-band excluded  
  > "We assume a Chabrier initial mass function (IMF)" (3.4.1)
   - fitting: chi2 minimisation  
  > "Including the uncertain $i$-band data point in the fit (shown as a red open circle in Fig. [8](#fig:sedfit)) significantly increases the $\chi^2$ for the best fit" (3.4.1 The stellar mass of the $z = 0.7163$ galaxy)
   - validation: Compared with magphys stellar mass  
  > "in full agreement with our result in Sect. [3.4.1](#sect:sedfit)" (3.4.3)
5. **dust mass and obscured SFR**: magphys fit to optical-NIR, ALMA 140 GHz and Herschel photometry; tested QSO/galaxy Herschel flux split  
  > "we use magphys (cite: dacunha08) with the photometry in Table [3](#tab:phot), the ALMA 140 GHz measurement of $53 \pm
17$ $\mu$Jy" (3.4.3)
   - software: MAGPHYS
   - assumption: Galaxy fraction of Herschel flux = ALMA fraction 0.27  
  > "we assumed that the fractional flux detected in the ALMA continuum band from the DLA galaxy is the same also at shorter wavelengths" (2.2 Herschel data)
   - fitting: maximum likelihood  
  > "With this assumption the maximum likelihood for the dust mass is found to be" (3.4.3 Dust mass, dust temperature and the obscured SFR)
   - validation: Best fit at 0.30 galaxy fraction  
  > "The best fit is found where 0.30 of the Herschel flux comes from the DLA galaxy" (3.4.3)
6. **SFRs and emission-line metallicity**: Kennicutt98 conversions for UV, [OII], Halpha (Chabrier correction 1.8); N2 index with Maiolino08  
  > "a simple downward correction factor of 1.8 is finally used to shift to the assumption of a Chabrier IMF" (3.4.2)
   - fitting: _not stated_
   - validation: Metallicity agrees with SED and absorption metallicity  
  > "This is in excellent agreement with both the independent result from the best fit SED model" (3.4.4)
7. **compare with scaling relations**: Compare Mmol vs M*, SFR vs fmol, CO Tully-Fisher, gas-to-dust vs metallicity against COLD GASS, ALLSMOG, PHIBSS, CANDELS  
  > "we first use the same comparison samples as above, but now cut out a thin slice in stellar mass of each sample" (4.2)
   - fitting: _not stated_
   - validation: _not stated_

## Software

- **CASA** : ALMA data editing, calibration and imaging  
  > "carried out in the casa (Common Astronomy Software Applications) package" (2.1 ALMA observations)
- **Hyperz** 12.2: SED fit for stellar mass  
  > "using release version 12.2 of Hyperz" (3.4.1)
- **MAGPHYS** : dust mass, dust luminosity, obscured SFR  
  > "we use magphys (cite: dacunha08)" (3.4.3)
- **SINFONI pipeline** 2.6: reduction of SINFONI cubes  
  > "Our data processing was done with the recent version (2.6) of the SINFONI pipeline" (2.4 VLT SINFONI data)
- **HIPE** : verify Herschel aperture flux  
  > "The integrated aperture flux was verified using the data analysis software ’Herschel Interactive Processing Environment (HIPE)’" (2.2 Herschel data)

## Numeric results

| quantity | value | uncertainty | units | step | quote |
|---|---|---|---|---|---|
| CO(2-1) velocity-integrated flux | 0.50 | 0.05 | Jy km/s | 1 | The velocity-integrated CO(2-1) line flux density is $S_{\rm int}=(0.50 \pm 0.05)$ Jy ${\rm km\,s^{-1}}$ |
| 140 GHz continuum flux density at galaxy | 53 | 17 | uJy | 1 | the ALMA 140 GHz measurement of $53 \pm
17$ $\mu$Jy |
| log molecular gas mass | 10.37 | 0.04 | log Msun | 2 | log\[M$_{\rm mol-gas}$/M$_\odot$\]$\dagger$ / $10.37 \pm 0.04$ |
| CO W50 | 647 | 54 | km/s | 3 | a W50 of $647\pm54$ ${\rm km\,s^{-1}}$ |
| Dynamical mass lower limit | 2.9e11 | not stated | Msun | 3 | we obtain M$_{\rm dyn} \mathrel{\hbox{\rlap{\hbox{\lower 4pt\hbox{$\sim$}}}\hbox{$>$}}}2.9 \times
10^{11} \: {\rm M}_\odot$ |
| log stellar mass | 10.80 | +0.07/-0.14 | log Msun | 4 | log$[{\rm M}_*/{\rm  M}_\odot]=10.80^{+0.07}_{-0.14}$ |
| log dust mass | 8.45 | +0.10/-0.30 | log Msun | 5 | $\log [{\rm
    M}_{\mathrm{dust}}/{\rm M}_\odot]= 8.45^{+0.10}_{-0.30}$ |
| Obscured SFR | 4.5 | +4.4/-2.6 | Msun/yr | 5 | The fit yields an obscured SFR of $4.5^{+4.4}_{-2.6}$ M$_{\odot}$ yr$^{-1}$ |
| Halpha SFR | 1.6 | 0.4 | Msun/yr | 6 | the H$\alpha$ line yields SFR$_{\mathrm{H\alpha}}=1.6\pm0.4$ M$_{\odot}$ yr$^{-1}$ |
| Oxygen abundance 12+log(O/H) | 9.20 | 0.09 | dex | 6 | we infer 12+log(O/H) $= 9.20 \pm 0.09$ |

## Qualitative findings

- First DLA host identified via molecular line emission  
  > "this constitutes the first confirmation of the identification of a DLA host galaxy via molecular line emission" (2.1 ALMA observations)

## Claim tuples

- H: Is the DLA galaxy gas-rich but with unusually low SFR relative to flux-selected samples? | E: Compare SFR vs molecular gas fraction in a stellar-mass slice with COLD GASS, PHIBSS, CANDELS | R: g1323 falls well below the relation for both Halpha and total SFR | F: g1323 has no counterparts in flux-selected samples in SFR-gas fraction space | **supported**
- H: Does the CO line width follow the CO Tully-Fisher relation? | E: Double-horn fit W50/W20, compare with COLD GASS TF | R: W50 = 647 km/s, significantly right of relation | F: Wide CO may be partly from a separate kinematic component | **partially**
- H: Part of the CO is kinematically and spatially decoupled | E: Compare CO channel-range maps and line components with Halpha and absorption | R: Blue CO component offset 0.9" (6.6 kpc) from galaxy | F: Suggests separate interacting component | **partially**
- H: Gas-to-dust ratio is consistent with normal galaxies at this metallicity | E: Compare L'CO/Mdust vs metallicity with Magdis11 sample | R: g1323 lies on the relation for local galaxies | F: Not a highly obscured starburst | **supported**

## Reasoning

- Why this data: _not stated_
- Why this method: _not stated_
- Alternative: Starburst alpha_CO=1, r21=1 rejected given low SFR and gas-to-dust ratio  
  > "we consider the starburst scenario to be unlikely" (3.1)
- How they decided it was enough: _not stated_
- Limitation (authors): FORS2 flux likely low by factor ~2 due to non-photometric conditions and slit losses  
  > "with the caveat that the flux is likely to be low by a factor of $\approx 2$" (2.3 VLT-FORS2 data)
- Limitation (authors): CO substructure difficult to verify at current S/N  
  > "the details of this sub-structure is difficult to verify at the current S/N and must await better data" (3.2)
- Caveat (inferred, ours): Single object; low S/N CO line (~7 sigma)
- Caveat (inferred, ours): Result sensitive to assumed alpha_CO and r21
- Caveat (inferred, ours): Herschel QSO/galaxy flux split assumed from ALMA
- Caveat (inferred, ours): QSO subtraction residuals affect optical/NIR photometry

## Reproducibility

- Data public (paper): ALMA data from project 2013.1.01178.S; SINFONI, UVES, HST and Herschel from archives  
  > "we retrieved the SINFONI dataset (programme ID: 079.A-0673) from the European Southern Observatory (ESO) archive" (2.4 VLT SINFONI data)
- Products in archive: _not stated_
- Missing: CASA version and exact imaging parameters
- Missing: Line-free channel selection
- Missing: Exact SED fitting setups for Hyperz and magphys
- Data volume (inferred): ~5-20 GB for the single ALMA Band 4 execution
- Score (inferred): 3/5, ALMA project given and recipe partly described, but imaging details and software versions missing; multiple non-ALMA data sets needed.
- Rediscovery candidate: no, Main results need additional archival optical/IR/Herschel data and unstated imaging details.

## Links

- Method: (cite: tiley2016) (Double-horn profile fitting for CO line widths)
- Method: (cite: dacunha08) (magphys SED model)
- Companion: (cite: neeleman16) (First CO detection in a sub-DLA from the same ALMA survey)
- Related: ALMA survey of DLA/sub-DLA galaxies
- Related: COLD GASS
- Related: ALLSMOG
- Related: PHIBSS

## Checks

```json
{
 "quotes": 81,
 "quotes_ok": 81,
 "quote_pass_rate": 1.0,
 "quotes_too_long": 0,
 "unsupported_facts": 0,
 "project_codes": 1,
 "codes_not_in_text": [],
 "codes_not_in_obscore": [],
 "obscore_codes_not_in_card": [],
 "codes_printed_but_missing": [],
 "numeric_results": 10,
 "numeric_problems": 0,
 "fill": {
  "facts": 89,
  "stated": 59,
  "rate": 0.663
 },
 "evidence_ok": true
}
```
