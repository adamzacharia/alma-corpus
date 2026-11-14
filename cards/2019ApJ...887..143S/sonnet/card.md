# ALMA Observations of Atomic Carbon [C I] ( <SUP> 3 </SUP> P <SUB> 1 </SUB> → <SUP> 3 </SUP> P <SUB> 0 </SUB>) and Low-J CO Lines in the Starburst Galaxy NGC 1808

`2019ApJ...887..143S` | The Astrophysical Journal 2019 | first author: Salak, Dragan | arXiv: 1911.04077 | DOI: 10.3847/1538-4357/ab55dc

Card schema 1.0 | model claude-sonnet-5-5 | depth full | type observational_alma_primary

## Science

- Fields: nearby_galaxies
- Question: How does atomic carbon [C I](1-0) relate to low-J CO lines, molecular gas mass and outflow in the central 1 kpc of the starburst galaxy NGC 1808?  
  > "To understand the origin of [C I] emission and its relation with CO in different environments in gas-rich, star-forming galaxies, it is important to bridge the gap" (Introduction)
- Target **NGC 1808**: coordinates RA 05h07m42.329s, Dec -37d30m45.85s (ICRS)  
  > "Distance | 10.8 Mpc ($1\ensuremath{''}=52$ pc) | \(3\)" (Table 1); "$\alpha_\mathrm{ICRS}$ | $\mathrm{05^h07^m42.329s}$ | \(2\)" (Table 1); z/distance 10.8 Mpc  
  > "Distance | 10.8 Mpc ($1\ensuremath{''}=52$ pc) | \(3\)" (Table 1); "$\alpha_\mathrm{ICRS}$ | $\mathrm{05^h07^m42.329s}$ | \(2\)" (Table 1); distance from Table 1 reference (3), not named in the text  
  > "Distance | 10.8 Mpc ($1\ensuremath{''}=52$ pc) | \(3\)" (Table 1); "$\alpha_\mathrm{ICRS}$ | $\mathrm{05^h07^m42.329s}$ | \(2\)" (Table 1)

## Data provenance

- ALMA projects: 2017.1.00984.S, 2016.1.00296.S, 2012.1.01004.S, 2013.1.00911.S
- bands: Bands 6 (220, 230 GHz) and 8 (500 GHz)  
  > "Three tuning settings were implemented to cover the 220 GHz, 230 GHz, and 500 GHz frequency bands" (2 Observations)
- frequencies and spectral setup: _not stated_
- continuum bandwidth: _not stated_
- arrays: 12-m, 7-m (ACA) and total power  
  > "The ALMA observations were carried out in cycle 5 during 2017 and 2018 by the 12-m array, 7-m array (Atacama Compact Array; ACA), and total power (TP) antennas." (2 Observations)
- configurations: _not stated_
- baselines: 12m: 15-479 m (B6), 15-314 m (B8); 7m: 9-45 m  
  > "Baselines (meters) | 15-479 | 9-45 | ... | 15-314 | 9-45 | ... |" (Table 2)
- angular resolution: [C I] 0.825''x0.590''; CO(2-1) 1.280''x0.943''  
  > "(${^3}\mathrm{P}_1\rightarrow{^3}\mathrm{P}_0$) | 492.1606510 | 23.6 | $0.825\ensuremath{''}\times0.590\ensuremath{''}$ | 20" (Table 3)
- max recoverable scale: ACA ~29'' (B6); ~13'' (B8)  
  > "the maximum recoverable scale of ACA ($\sim29\ensuremath{''}$) was comparable to the starburst region" (2 Observations)
- sensitivity: [C I] 20 mJy/beam; CO(2-1) 3.0 mJy/beam  
  > "CO ($J=2\rightarrow1$) | 230.5380000 | 16.6 | $1.280\ensuremath{''}\times0.943\ensuremath{''}$ | 3.0 | 5424" (Table 3)
- time on source: _not stated_
- observing dates: 2017 Oct to 2018 May  
  > "Observation date | 2018 May 6 | 2017 Oct 19, | 2018 Jan 11, 15 | 2018 May 22" (Table 2)
- pi or archival as stated: _not stated_
- Line: [C I] 3P1-3P0 (492.1606510 GHz)
- Line: 12CO J=2-1 (230.5380000 GHz)
- Line: 13CO J=2-1 (220.3986842 GHz)
- Line: C18O J=2-1 (219.5603541 GHz)
- Other facility **HST**: Optical R-band image for comparison  
  > "an optical image taken by the *Hubble Space Telescope* of the central starburst region is shown in Figure [2](#fig:co)(c)" (3.1 Molecular Gas Traced by CO (2–1))
- External data: CO(1-0) and CO(3-2) ALMA data  
  > "$^{e}$ Data from (cite: Sal17)." (Table 3) [from (cite: Sal17)]
- External data: L'CO-L'CI relations for nearby galaxies  
  > "(cite: Jia19) have shown that, for a sample of 15 nearby galaxies, including Seyfert and starburst galaxies" (4.2.4 L'CO-L'[CI] Correlations) [from (cite: Jia19)]

## Processing

### Calibration

- pipeline or manual: CASA pipeline  
  > "First, the data were calibrated by a CASA pipeline." (2 Observations)
- casa version: _not stated_
- pipeline version: _not stated_
- archive products used as is: _not stated_
- flux calibrator: _not stated_
- flux scale uncertainty: 10% interferometer (B6, B8); 15% TP in B8  
  > "The absolute flux uncertainty of the interferometer is 10% in bands 6 and 8 and that of the TP is 15% in band 8." (2 Observations)
- self calibration: _not stated_

### Imaging

- task: tclean in CASA, 12m+ACA combined  
  > "We then reconstructed images from the two visibility data sets using the task *tclean* in CASA, yielding a single data product (12m+ACA)." (2 Observations)
- deconvolver: Hogbom, interactive CLEAN, mosaic gridder  
  > "The CLEAN process was interactively performed by applying the Hogbom minor cycle algorithm, mosaic gridder, and Briggs weighting with the robust parameter of 0.5." (2 Observations)
- weighting robust: Briggs, robust = 0.5  
  > "Briggs weighting with the robust parameter of 0.5" (2 Observations)
- uv taper: _not stated_
- cell size: 0.2'' in band 6, 0.1'' in band 8  
  > "$0.2\ensuremath{''}$ in band 6 and $0.1\ensuremath{''}$ in band 8" (2 Observations)
- image size: _not stated_
- masking: _not stated_
- multiscale scales: _not stated_
- continuum subtraction: Line data continuum-subtracted  
  > "The calibrated data were then split into line and continuum data sets, and the line data were continuum-subtracted." (2 Observations)
- line free channels: _not stated_
- primary beam correction: applied  
  > "The final images were corrected for the primary beam response." (2 Observations)
- array combination: [C I] band 8 12m+ACA feathered with TP using feather  
  > "The [C I] (1–0) line data in band 8 were then combined with TP data using the CASA task *feather*" (2 Observations)
- smoothing: imsmooth to ~100 pc common resolution  
  > "The smoothed images were derived by convolving the original ones with Gaussian kernels using the CASA task *imsmooth*." (4.1.1 Line Intensities and Profiles)
- final beam: _not stated_
- final rms: _not stated_

### Inherited from earlier work

- CO(1-0) and CO(3-2) observations and data reduction  
  > "The descriptions of the observations and data reduction of CO (1–0) and CO (3–2) data used in this paper, that also contain 12-m, ACA, and TP data, are given in (cite: Sal16; Sal17)." (2 Observations) [from (cite: Sal16; Sal17)]
- Outflow mass estimate method (<10% of flux)  
  > "Following the analysis in (cite: Sal16), we estimate that the noncircular motions due to outflows comprise less than 10% of the total [C I] flux" (4.3 Atomic Carbon in the Outflow) [from (cite: Sal16)]

### Not stated but needed to reproduce (our reading)

- Line-free channels for continuum subtraction
- Number of clean iterations, thresholds and masks
- Flux calibrators/CASA version
- Image sizes and channel widths for band 6
- Mask thresholds for moment maps
- Feather parameters and TP scaling
- Pixel selection and weighting for correlation fits

## Analysis recipe

1. **Calibrate and image 12m+ACA(+TP) data**: CASA pipeline calibration, continuum subtraction, tclean cube imaging, feather with TP for band 8  
  > "We then reconstructed images from the two visibility data sets using the task *tclean* in CASA, yielding a single data product (12m+ACA)." (2 Observations)
   - software: CASA, tclean, feather
   - parameter: robust = 0.5, Hogbom, mosaic gridder  
  > "Briggs weighting with the robust parameter of 0.5" (2 Observations)
   - fitting: _not stated_
   - validation: Flux recovery check: feathering increased [C I] flux by 56%  
  > "yielding a recovery of as much as 56% of the flux by combining the interferometer data with TP." (2 Observations)
2. **Make moment maps and line fluxes/luminosities**: immoments with no masking for integrated intensity; masked moments 1 and 2; L' from SDR92 formula  
  > "The integrated intensity images were created in CASA using the task *immoments* with no masking, yielding unbiased images." (3.1 Molecular Gas Traced by CO (2–1))
   - software: CASA
   - assumption: distance 10.8 Mpc  
  > "Distance | 10.8 Mpc ($1\ensuremath{''}=52$ pc)" (Table 1)
   - fitting: _not stated_
   - validation: _not stated_
3. **CND column density and abundance in LTE**: LTE optically thin N_CO and N_CI from mean 3'' aperture spectra; masses via XCO  
  > "Similarly, assuming LTE and optically thin [C I] (1–0) emission, the column density of atomic carbon gas can be derived" (4.1.2 Column Density and Abundance)
   - parameter: Tex = 20-100 K  
  > "For a range of $T_\mathrm{ex,[CI]}=20\mathrm{-}100$ K" (4.1.2 Column Density and Abundance)
   - assumption: CO/H2 = 1e-4; Galactic XCO = 2e20 or starburst 0.5e20  
  > "Assuming an CO/H$_2$ abundance ratio of $10^{-4}$" (4.1.2 Column Density and Abundance)
   - fitting: _not stated_
   - validation: _not stated_
4. **Non-LTE LVG modelling of CND**: RADEX grid in N, Tk, nH2; match CO(3-2)/(1-0), CO(2-1)/(1-0), [C I]/CO(1-0) ratios within 3 sigma  
  > "we ran a series of calculations using the non-LTE radiative transfer program RADEX" (4.1.3 Non-LTE Calculations of Physical Conditions)
   - software: RADEX
   - parameter: dV = 25 km/s, T_bg = 2.73 K, LVG escape probability  
  > "The velocity width was fixed at $\Delta V=25$ km s$^{-1}$" (4.1.3 Non-LTE Calculations of Physical Conditions)
   - fitting: _not stated_
   - validation: _not stated_
5. **Radial intensity ratios and correlations**: Azimuthally averaged ratio profiles in elliptical rings; pixel power-law least-squares fits W_CO = a W_CI^b  
  > "We fitted the distribution in each panel by a power law $W_\mathrm{CO}=aW_\mathrm{[CI]}^b$ using a least-squares method" (4.2.4 L'CO-L'[CI] Correlations)
   - software: CASA
   - parameter: PA 324 deg, inclination 57 deg  
  > "The position angle and inclination adopted for the geometry of elliptical rings are from Table [1]" (4.2.1 Intensity Ratios)
   - fitting: _not stated_
   - validation: _not stated_
6. **Outflow upper limits from PVDs**: [C I] smoothed to CO(1-0) resolution; PVDs along dust lanes; <10% of flux in non-circular motions; Ek=Mv^2/2  
  > "the upper limit of the kinetic energy of the atomic carbon outflow is $E_\mathrm{k}\sim M_\mathrm{out}v_\mathrm{out}^2/2\sim3\times10^{51}$ erg" (4.3 Atomic Carbon in the Outflow)
   - assumption: v_out ~180 km/s for inclination 57 deg  
  > "For an inclination of $57\ensuremath{^\circ}$, the average velocity of the outflow perpendicular to the galactic disk is $v_\mathrm{out}\sim180$ km s$^{-1}$." (4.3 Atomic Carbon in the Outflow)
   - fitting: _not stated_
   - validation: _not stated_

## Software

- **CASA** : Calibration, tclean, feather, immoments, imsmooth, spectral profile Gaussian fits  
  > "The acquired visibility data were reduced using the Common Astronomy Software Applications (CASA) package (cite: McM07)" (2 Observations)
- **RADEX** : Non-LTE LVG radiative transfer  
  > "using the non-LTE radiative transfer program RADEX (cite: vdT07)" (4.1.3 Non-LTE Calculations of Physical Conditions)

## Numeric results

| quantity | value | uncertainty | units | step | quote |
|---|---|---|---|---|---|
| [C I] column density in CND | 3e18 | not stated | cm^-2 | 3 | obtain $N_\mathrm{CI}\sim3\times10^{18}$ cm$^{-2}$ |
| M_CI in CND at Tex=50 K | 5.4e3 | 0.1e3 | Msun | 3 | For $T_\mathrm{ex,[CI]}=50$ K, the mass is $M_\mathrm{CI}=(5.4\pm0.1)\times10^3~M_\ensuremath{\odot}$ |
| CI/H2 abundance in CND | ~6e-5 | not stated | dimensionless | 3 | the mean C I/H$_2$ abundance ratio in the CND is $N_\mathrm{CI}/N_\mathrm{H_2}=M_\mathrm{CI}/(6M_\mathrm{H_2})\sim6\times10^{-5}$ |
| Mean [C I]/CO(2-1) ratio within 20'' | 0.21 | 0.01 | dimensionless | 5 | the mean value over the rings within a radius of $20\ensuremath{''}$ is $r_{21}=0.21\pm0.01$ |
| Mean [C I]/CO(1-0) ratio within 20'' | 0.18 | 0.04 | dimensionless | 5 | The mean intensity ratio over the rings in the central radius $20\ensuremath{''}$ region is $0.18\pm0.04$. |
| CO(1-0) vs [C I] power-law index b | 0.686 | 0.010 | dimensionless | 5 | CO (1–0)        / $1.488\pm0.019$ / $0.686\pm0.010$ / $0.85$ |
| Outflow C I mass upper limit | ~1e4 | not stated | Msun | 6 | which is $M_\mathrm{out}\sim1\times10^4~M_\ensuremath{\odot}$ |
| Total C I mass central 1 kpc | 9.7e4 | not stated | Msun | 3 | $M_\mathrm{CI}\sim9.7\times10^4~M_\ensuremath{\odot}$ |
| L'[CI]/L'CO(1-0) central 1 kpc | 0.11 | 0.02 | dimensionless | 2 | The luminosity ratio $L'_\mathrm{[CI]}/L'_\mathrm{CO(1-0)}=0.11\pm0.02$ |

## Qualitative findings

- CO(2-1)/[C I] ratio is uniform, explained by similar effective critical densities of the two lines  
  > "Then, if $\tau_\mathrm{CO(2-1)}=10$, expanding sphere (LVG) geometry yields $\beta_\mathrm{CO(2-1)}=0.1$ and $n_\mathrm{cr,CO(2-1)}\approx n_\mathrm{cr,[CI]}$." (4.2.1 Intensity Ratios)

## Claim tuples

- H: Is the CND warm, dense and rich in atomic carbon? | E: RADEX LVG modelling of CO and [C I] line ratios | R: Tk~40-80 K, nH2~1e3-4, N_CI~3e18 | F: CND has warm dense gas with enhanced C I abundance | **supported**
- H: Can [C I](1-0) trace molecular gas mass like CO? | E: Pixel correlations and ratio profiles vs CO lines | R: Near-linear with CO(2-1), CO(3-2); b~0.7 with CO(1-0) | F: Usable as a CO-equivalent tracer with caution in resolved starburst nuclei | **partially**
- H: Is C I enhanced in the starburst-driven outflow? | E: PVDs of [C I] and CO(1-0) at 100 pc | R: r10 <~0.15 at outflow base | F: No enhancement; only upper limits on mass and energy | **supported**

## Reasoning

- Why this data: _not stated_
- Why this method: RADEX LVG used to test LTE and optically thin assumptions  
  > "Are LTE and optically thin line reasonable assumptions for [C I] (1–0) toward the CND?" (4.1.3 Non-LTE Calculations of Physical Conditions)
- How they decided it was enough: _not stated_
- Limitation (authors): Only statistical uncertainties in line parameters; flux calibration uncertainty excluded  
  > "Only statistical uncertainties are stated; flux calibration uncertainty (10-15%) is not included." (Table 4)
- Caveat (inferred, ours): Single-Gaussian and LTE assumptions are simple
- Caveat (inferred, ours): RADEX solution is not unique, with only ratio matching and a fixed dV
- Caveat (inferred, ours): Outflow limits depend on a 10% fraction inherited from earlier work
- Caveat (inferred, ours): Beam filling factors are assumed equal

## Reproducibility

- Data public (paper): ALMA archive data cited by project code, including CO(3-2) from the archive  
  > "These CO (3–2) data were acquired from the ALMA Archive (project 2016.1.00296.S)" (4.1 Atomic Carbon in the CND)
- Products in archive: _not stated_
- Missing: Line-free channels
- Missing: CASA version
- Missing: CLEAN masks and thresholds
- Missing: Details of the CO(1-0) and CO(3-2) data from earlier papers
- Missing: Pixel selection for fits
- Data volume (inferred): Several hundred GB raw for 12m, ACA and TP mosaics in Bands 6 and 8; roughly 50-100 GB of calibrated products
- Score (inferred): 3/5, Data are public and the main steps are given, but several imaging details are missing and CO(1-0) and CO(3-2) come from earlier papers.
- Rediscovery candidate: yes, The data are public, the recipe is reasonably clear, and the results are numeric (ratios, column densities, fit indices).

## Links

- Method: (cite: vdT07) (RADEX code)
- Method: (cite: SDR92) (Line luminosity definitions)
- Companion: (cite: Sal16) (CO(1-0) data, outflow analysis)
- Companion: (cite: Sal17) (CO(3-2) and 90 GHz continuum data)
- Companion: (cite: Sal18) (Dense gas properties of the CND)
- Related: 2016.1.00296.S

## Checks

```json
{
 "quotes": 70,
 "quotes_ok": 70,
 "quote_pass_rate": 1.0,
 "quotes_too_long": 0,
 "unsupported_facts": 0,
 "project_codes": 4,
 "codes_not_in_text": [],
 "codes_not_in_obscore": [
  "2016.1.00296.S",
  "2012.1.01004.S",
  "2013.1.00911.S"
 ],
 "obscore_codes_not_in_card": [],
 "codes_printed_but_missing": [],
 "numeric_results": 9,
 "numeric_problems": 0,
 "fill": {
  "facts": 77,
  "stated": 46,
  "rate": 0.597
 },
 "evidence_ok": true
}
```
