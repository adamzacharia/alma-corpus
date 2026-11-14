# Strongly star-forming rotating disks in a complex merging system at z = 4.7 as revealed by ALMA

`2013A&A...559A..29C` | Astronomy and Astrophysics 2013 | first author: Carniani, S. | arXiv: 1308.5113 | DOI: 10.1051/0004-6361/201322320

Card schema 1.0 | model claude-sonnet-5-5 | depth full | type archival_reuse

## Science

- Fields: high_z_galaxies, agn_and_quasars
- Question: Do the QSO host and the SMG in BR1202-0725 at z=4.7 show regularly rotating disks or merger-disturbed kinematics in [CII], and what are their dynamical masses and BH-host relation?  
  > "Here we perform a kinematical analysis of the \[CII\] line emission in BR 1202-0725 from the observations obtained with ALMA during the science demonstration phase." (1 Introduction)
- Target **BR1202-0725 (N: SMG, S: QSO)**: coordinates N: 12:05:22.98 -07:42:29.56; S: 12:05:23.13 -07:42:32.68  
  > "Redshift | 4.6891 | 4.6943" (Table 1); "1 arcsec at $z=4.7$ corresponds to a proper distance of 6.48 kpc." (1 Introduction); z/distance z=4.6891 (N), 4.6943 (S); systemic z=4.6949  
  > "Redshift | 4.6891 | 4.6943" (Table 1); "1 arcsec at $z=4.7$ corresponds to a proper distance of 6.48 kpc." (1 Introduction); distance from [CII] Gaussian fit; systemic z from Salomé et al. 2012  
  > "Redshift | 4.6891 | 4.6943" (Table 1); "1 arcsec at $z=4.7$ corresponds to a proper distance of 6.48 kpc." (1 Introduction)

## Data provenance

- ALMA projects: 2011.0.00002.SV
- bands: 0.9 mm (334 GHz)  
  > "BR1202-0725 was observed at 0.9 mm (334 GHz)" (Observations and data reduction)
- frequencies and spectral setup: four ~1.8 GHz spectral windows, 15.6 MHz channels (~14 km/s), tuned to ~333 GHz  
  > "was divided in to four spectral windows of $\sim 1.8$ GHz with a channel width of 15.6 MHz ($\sim$ 14 km s$^{-1}$)" (Observations and data reduction)
- continuum bandwidth: _not stated_
- arrays: 18 12-m and 3 7-m antennas  
  > "with 18 12-m and 3 7-m diameter antennas on 2012 January 16" (Observations and data reduction)
- configurations: _not stated_
- baselines: max ~280 m  
  > "with a maximum baseline length $\sim$ 280 m" (Observations and data reduction)
- angular resolution: 0.8"x0.7", PA 8 deg (continuum)  
  > "achieving an angular resolution of 0.8$^{\prime\prime}$$\times$0.7$^{\prime\prime}$with the beam oriented at P.A. = 8$^{\circ}$" (Observations and data reduction)
- max recoverable scale: _not stated_
- sensitivity: continuum 0.2 mJy/beam rms; cube 2.0 mJy/beam/channel  
  > "The achieved sensitivity in the continuum image is 0.2 mJy (*rms*/beam)." (Observations and data reduction); "The rms noise was estimated to be 2.0 mJy per beam per channel" (Observations and data reduction)
- time on source: about 25 minutes  
  > "The total on-source observing time was about 25 minutes" (Observations and data reduction)
- observing dates: 2012 January 16  
  > "on 2012 January 16" (Observations and data reduction)
- pi or archival as stated: _not stated_
- Line: [CII] 158 um fine structure (1900.539 GHz)
- Other facility **VLT X-shooter**: Spectrum of QSO for MgII-based BH mass  
  > "An intermediate-resolution spectrum of the QSO has been obtained with X-shooter" (Black hole mass of the QSO)
- External data: L'CO(5-4) used for molecular gas masses  
  > "We estimated the molecular gas masses from $L^\prime_{\rm CO}$(5-4) (cite: salome:2012)" (2 Star formation rate and gas mass) [from (cite: salome:2012)]
- External data: alpha_CO = 0.6±0.2  
  > "derived by (cite: papadopoulos:2012) from a large sample of starburst galaxies" (2 Star formation rate and gas mass) [from (cite: papadopoulos:2012)]
- External data: Fluxes for FIR-radio SED compiled from literature  
  > "Fluxes for BR 1202N and BR 1202S were compiled from (cite: carilli:2002), (cite: omont:1996), (cite: benford:1999)" (2 Star formation rate and gas mass) [from (cite: carilli:2002; omont:1996; benford:1999)]

## Processing

### Calibration

- pipeline or manual: CASA; gain/bandpass on 3C279; flux scaled with Titan  
  > "Afterwards we used observations of Titan to rescale the flux, assuming a total value of 2.5 Jy." (Observations and data reduction)
- casa version: _not stated_
- pipeline version: _not stated_
- archive products used as is: _not stated_
- flux calibrator: 3C279 at 15 Jy (SMA 850 um), rescaled with Titan 2.5 Jy  
  > "for which we took the flux of 15 Jy obtained from SMA observation at 850 $\mu$m" (Observations and data reduction)
- flux scale uncertainty: 15%  
  > "Overall, we estimate a 15$\%$ uncertainty on the measured absolute fluxes." (Observations and data reduction)
- self calibration: amplitude and phase self-cal with line-free channels, 3-min solution interval  
  > "we used a 3-min averaging time for the complex gain solutions in the amplitude and phase self-calibration." (Observations and data reduction)

### Imaging

- task: CASA CLEAN  
  > "the image was then cleaned using the CASA task "CLEAN" with ROBUST=1.5" (Observations and data reduction)
- deconvolver: _not stated_
- weighting robust: ROBUST=1.5  
  > "the image was then cleaned using the CASA task "CLEAN" with ROBUST=1.5" (Observations and data reduction)
- uv taper: _not stated_
- cell size: 0.15" per pixel  
  > "The spatial scale is 0.15$^{\prime\prime}$ per pixel" (Observations and data reduction)
- image size: _not stated_
- masking: _not stated_
- multiscale scales: _not stated_
- continuum subtraction: UV-plane model from line-free channels of last three SPWs, subtracted from first two SPWs after linear extrapolation  
  > "was subtracted from the first and second spectral windows after linear extrapolation" (Observations and data reduction)
- line free channels: _not stated_
- primary beam correction: _not stated_
- array combination: _not stated_
- smoothing: first two SPWs rebinned to ~28 km/s channels  
  > "rebinned to channels of $\sim$28 km/s" (Observations and data reduction)
- final beam: _not stated_
- final rms: 2.0 mJy/beam/channel  
  > "The rms noise was estimated to be 2.0 mJy per beam per channel" (Observations and data reduction)

### Inherited from earlier work

- PV slit extraction following CO analysis  
  > "oriented E-W, as in (cite: salome:2012)" (4.1 The submillimeter galaxy BR1202 North) [from (cite: salome:2012)]
- Kinematical disk model  
  > "using the kinematical disk model used for $z\sim 3$ Lyman-break galaxies by (cite: gnerucci:2011a)" (4.1 The submillimeter galaxy BR1202 North) [from (cite: gnerucci:2011a)]
- Spectroastrometric mass calibration  
  > "Following (cite: gnerucci:2011), we can therefore use spectroastrometry" (4.1 The submillimeter galaxy BR1202 North) [from (cite: gnerucci:2011)]
- BH virial calibration  
  > "Here we adopted the very recent calibration by Marconi et al. (2013, in preparation)" (Black hole mass of the QSO) [from Marconi et al. 2013, in preparation]

### Not stated but needed to reproduce (our reading)

- Exact CASA version and calibration script
- Channel ranges identified as line-free
- CLEAN threshold, masks, iterations
- Parameter priors/bounds and MCMC chain settings
- Spectroastrometry velocity cuts defining blue/red channels
- Disk model code not released
- Exact SED fitting details

## Analysis recipe

1. **Calibrate, self-calibrate and image continuum and [CII] cube**: CASA calibration, self-cal, CLEAN, uv continuum subtraction  
  > "The data were calibrated by using the CASA software." (Observations and data reduction)
   - software: CASA
   - parameter: ROBUST=1.5; 0.15" pixel; 28 km/s channels  
  > "The spatial scale is 0.15$^{\prime\prime}$ per pixel" (Observations and data reduction)
   - fitting: _not stated_
   - validation: Compared with released data products; consistent fluxes  
  > "Continuum and line fluxes are consistent within the errors" (Observations and data reduction)
2. **Fit integrated spectra**: Two-Gaussian fits to [CII]; redshifts from Gaussian fit  
  > "The redshifts of the two sources are determined from a Gaussian fit to the \[CII\] lines" (3 Results)
   - assumption: SMG faint component fixed at 250 km/s  
  > "with the fainter component fixed at 250 km/s" (3 Results)
   - fitting: _not stated_
   - validation: _not stated_
3. **Derive SFR and gas mass**: SED fit for LFIR, Kennicutt relation, [CII] calibration, CO-based gas mass  
  > "SFR = 1.73\times 10^{-10} (L_{FIR}/L_\odot)\, M_\odot/yr" (2 Star formation rate and gas mass)
   - assumption: Td=65 K (SMG), 50 K (QSO); k~nu^1.5; Salpeter IMF; alpha_CO=0.6 with factor 2 systematic  
  > "T$_d$ = 65 K for the SMG and T$_d$ = 50 K for the QSO" (2 Star formation rate and gas mass)
   - fitting: SFR the only free parameter of Yun & Carilli SED model  
  > "the latter depends on the SFR, which is the only free parameter of our SED fit" (2 Star formation rate and gas mass)
   - validation: [CII] SFRs used as confirmation  
  > "considered the values based on \[CII\] just as a confirmation of the very high SFR" (2 Star formation rate and gas mass)
4. **Test resolved kinematics**: Spectroastrometry and pixel-by-pixel residual maps  
  > "The first test was to perform a spectroastrometric analysis by collapsing all the velocity channels blueward of the line peak and the redward ones in two separate images." (4.1 The submillimeter galaxy BR1202 North)
   - fitting: _not stated_
   - validation: Residual structure consistent with rotating disk  
  > "The structure of the residuals is clearly what we would expect for a rotating disk after a line fit that does not allow for a variation of the line average velocity." (Kinematical analysis, The submillimeter galaxy BR1202 North)
5. **Fit rotating disk to velocity maps**: Thin exponential disk model, chi2 minimization with MPFIT/AMOEBA then MCMC, with and without gas-mass prior  
  > "The best-fit parameter values for the kinematical model were found using the MPFIT (cite: markwardt:2009) and AMOEBA algorithms in the IDL environment." (4.1 The submillimeter galaxy BR1202 North)
   - software: MPFIT, AMOEBA, EXOFAST IDL
   - parameter: 10^5 MCMC trials; pixels with S/N>=3; Mdyn within 5 kpc  
  > "obtained from the MCMC with $10^5$ trials with (red) and without (green) the dynamical mass prior" (4.1 The submillimeter galaxy BR1202 North)
   - assumption: Circular rotation, potential from disk mass, Sigma=Sigma0 exp(-r/r0), center and r0 from [CII] surface brightness  
  > "We assumed that the gas is circularly rotating in a thin disk" (4.1 The submillimeter galaxy BR1202 North)
   - fitting: Prior: lognormal step function peaked at molecular gas mass, 0.3 dex dispersion  
  > "the dispersion is $0.3$ dex, corresponding to a factor 2" (4.1 The submillimeter galaxy BR1202 North)
   - validation: Spectroastrometric mass consistent; inclination check assuming symmetric flux gives i=6±3 (SMG), 2±2 (QSO)  
  > "the resulting disk inclination is in the range $i=6^\circ\pm3^\circ$ (90% confidence)" (4.1 The submillimeter galaxy BR1202 North)
6. **Intrinsic dispersion and Vmax**: sigma_int^2 = sigma_obs^2 - sigma_model^2 from best-fit cold-disk model  
  > "$\langle\sigma_{\rm int}^2\rangle = \langle\sigma_{\rm obs}^2 -\sigma_{\rm model}^2\rangle$" (4.1 The submillimeter galaxy BR1202 North)
   - fitting: _not stated_
   - validation: _not stated_
7. **QSO BH mass from X-shooter**: Fit MgII with power law + FeII (CLOUDY templates) + broken power-law lines; virial relation  
  > "The spectrum was fit with a combination of power-law continuum, FeII emission and broad line." (Black hole mass of the QSO)
   - software: X-shooter pipeline, CLOUDY
   - assumption: Marconi et al. virial calibration, 0.3 dex systematic  
  > "The zero point of this relations has a $\sim 0.3$ dex systematic uncertainty" (Black hole mass of the QSO)
   - fitting: _not stated_
   - validation: _not stated_

## Software

- **CASA** : Calibration and imaging  
  > "The data were calibrated by using the CASA software." (Observations and data reduction)
- **MPFIT** : Best-fit disk model  
  > "using the MPFIT (cite: markwardt:2009) and AMOEBA algorithms in the IDL environment" (4.1 The submillimeter galaxy BR1202 North)
- **EXOFAST IDL** : MCMC routines  
  > "We used the IDL routines developed for the EXOFAST IDL package (cite: Eastman:2013)." (4.1 The submillimeter galaxy BR1202 North)
- **CLOUDY** 10.00: FeII templates  
  > "CLOUDY (version 10.00; (cite: ferland:2013))" (Black hole mass of the QSO)

## Numeric results

| quantity | value | uncertainty | units | step | quote |
|---|---|---|---|---|---|
| Continuum flux 900 um N / S | 15.8 / 14.8 | 2.4 / 2.2 | mJy | 1 | Integrated continuum flux at 900 $\mu$m \[mJy\] / 15.8$\pm$2.4 / 14.8$\pm$2.2 |
| Projected N-S distance | 23.5 | 0.3 | kpc | 1 | The projected distance between the two continuum sources is 23.5$\pm$0.3 kpc. |
| log Mdyn SMG | 10.8 | 0.6 | log Msun | 5 | $Log_{10}({\rm M}_{\rm SMG}/ {\rm M}_\odot) =10.8 \pm 0.6$ |
| SMG inclination | 25 | 15 | deg | 5 | $i = 25^\circ\pm 15^\circ$ |
| log Mdyn QSO | 10.6 | +0.8/-0.4 | log Msun | 5 | $Log_{10}({\rm M}_{\rm QSO}/ {\rm M}_\odot) =10.6^{+0.8}_{-0.4}$ |
| QSO inclination | 15 | 10 | deg | 5 | $i = 15^\circ\pm 10^\circ$ |
| Vmax/sigma_int SMG | 1.3 | not stated | dimensionless | 6 | ${\rm V_{max}}/\sigma_{\rm int}\sim 1.3$ with ${\rm V_{max}}\sim270$ km/s |
| Vmax/sigma_int QSO | 1.5 | not stated | dimensionless | 6 | corresponding ratio ${\rm V_{max}}/{\rm \sigma_{int}}\sim1.5$ |
| Molecular mass SMG / QSO | 4.6 / 3.2 (1e10) | 1.7 / 1.2 | Msun | 3 | $M_{CO} = (4.6\pm 1.7)\times 10^{10}$$\mathrm{M}_{\odot}$ |
| SFR from LFIR SMG / QSO | 2600 / 3200 | not stated | Msun/yr | 3 | one obtains $\sim 2600$ and $\sim 3200$ M$_{\odot}$ yr$^{-1}$ for the SMG and QSO |
| QSO BH mass | 1.9e9 | 0.3 dex systematic | Msun | 7 | M$_{\rm  BH} = 1.9\times10^{9}$  $\mathrm{M}_{\odot}$ ($\pm 0.3$ dex, systematic) |
| Eddington ratio | 1.5 | not stated | dimensionless | 7 | The Eddington ratio is therefore $L/L_{Edd}\sim 1.5$. |
| Halo mass lower limit | 3.2e11 | not stated | Msun | 0 | M_{\rm tot}= d\,\Delta V ^2 /G = 3.2\times10^{11} |

## Qualitative findings

- Both galaxies show regular rotation, nearly face-on, hot disks; no clear outflow evidence; faint spectroscopic companions consistent with gravitational motions  
  > "Our kinematical analysis reveals that these galaxies apparently have regularly rotating disks, that are seen almost face-on" (7 Conclusions)

## Claim tuples

- H: High SFRs in SMG and QSO are driven by a major merger with disturbed kinematics | E: Spatially resolved [CII] kinematic modelling | R: Velocity fields consistent with regular rotating disks | F: High SFRs likely from minor mergers, interactions or inflows | **supported**
- H: QSO BH to host dynamical mass ratio differs from local | E: MgII BH mass vs [CII] dynamical mass | R: MBH/Mdyn ~0.05, above local relation by ~10 but within upper envelope given inclination uncertainty | F: Comparable to massive local galaxies | **partially**

## Reasoning

- Why this data: _not stated_
- Why this method: Mass prior used because inclination is poorly constrained  
  > "Since the disk inclination is not well constrained from the data and since the dynamical mass could be larger than the molecular gas mass" (4.1 The submillimeter galaxy BR1202 North)
- Alternative: Sargsyan et al. [CII] SFR calibration rejected as not applicable  
  > "but this calibration may not be applicable since it is obtained from galaxies at lower redshifts" (2 Star formation rate and gas mass)
- How they decided it was enough: _not stated_
- Limitation (authors): Inclination poorly constrained, so mass is poorly constrained  
  > "the inclination cannot be well constrained from the data" (4.1 The submillimeter galaxy BR1202 North)
- Caveat (inferred, ours): Rotation inferred from marginally resolved data (~1.2x beam)
- Caveat (inferred, ours): Mass depends on prior and degenerate inclination
- Caveat (inferred, ours): Low inclination relies on gas-mass prior
- Caveat (inferred, ours): Gaussian decomposition of companions is model dependent

## Reproducibility

- Data public (paper): ALMA Science Verification data  
  > "from ALMA Science Verification observations" (7 Conclusions)
- Products in archive: _not stated_
- Missing: Modelling code
- Missing: MCMC and priors details
- Missing: Exact CASA version and clean parameters
- Missing: X-shooter data reduction details
- Data volume (inferred): ~ few GB
- Score (inferred): 3/5, Public SV data and clear workflow, but key settings and custom IDL code unstated.
- Rediscovery candidate: no, Custom disk-fitting model and unstated settings hinder redoing; also needs X-shooter data.

## Links

- Method: (cite: gnerucci:2011a) (Kinematic disk model)
- Method: (cite: gnerucci:2011) (Spectroastrometry mass)
- Companion: (cite: wagg:2012) (Earlier analysis of same ALMA data)
- Companion: (cite: Carilli:2013) (Earlier analysis of same ALMA data)
- Companion: (cite: salome:2012) (CO PdBI observations)
- Related: ALMA Science Verification

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
 "codes_not_in_obscore": [
  "2011.0.00002.SV"
 ],
 "obscore_codes_not_in_card": [
  "2011.0.00006.SV"
 ],
 "codes_printed_but_missing": [],
 "numeric_results": 13,
 "numeric_problems": 0,
 "fill": {
  "facts": 85,
  "stated": 58,
  "rate": 0.682
 },
 "evidence_ok": true
}
```
