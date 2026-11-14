# Dynamical Equilibrium in the Molecular ISM in 28 Nearby Star-forming Galaxies

`2020ApJ...892..148S` | The Astrophysical Journal 2020 | first author: Sun, Jiayi | arXiv: 2002.08964 | DOI: 10.3847/1538-4357/ab781c

Card schema 1.0 | model claude-sonnet-5-5 | depth full | type large_program_or_survey

## Science

- Fields: nearby_galaxies, milky_way_ism, star_formation
- Question: Does the observed turbulent pressure in molecular gas match the dynamical equilibrium pressure required to support the ISM in the galactic gravitational potential, on kpc and cloud scales?  
  > "We compare the observed turbulent pressure in molecular gas, $P_\mathrm{turb}$, to the required pressure for the interstellar gas to stay in equilibrium in the gravitational potential of a galaxy, $P_\mathrm{DE}$." (abstract)
- Target **28 PHANGS-ALMA nearby star-forming galaxies (e.g. NGC 628, NGC 3627, NGC 4321)**: coordinates _not stated_; z/distance 4.36-26.1 Mpc (Table 1)  
  > "(2) Distance (from the Extragalactic Distance Database; (cite: Tully_etal_2009)); (3) inclination angle (cite: Lang_etal_2019)" (Table 1 notes); distance from Extragalactic Distance Database (Tully et al. 2009)  
  > "(2) Distance (from the Extragalactic Distance Database; (cite: Tully_etal_2009)); (3) inclination angle (cite: Lang_etal_2019)" (Table 1 notes)

## Data provenance

- ALMA projects: 2012.1.00650.S, 2015.1.00925.S, 2015.1.00956.S, 2017.1.00392.S, 2017.1.00886.L, 2018.1.01321.S
- bands: _not stated_
- frequencies and spectral setup: _not stated_
- continuum bandwidth: _not stated_
- arrays: 12-m array + ACA (7-m and total power)  
  > "They include data from both the 12-m array and the Morita Atacama Compact Array (ACA; consisting of the 7-m array and four 12-m total power antennas), and therefore should recover emission on all spatial scales." (2.1 Cloud-scale Resolution CO Data)
- configurations: _not stated_
- baselines: _not stated_
- angular resolution: 1.0''-1.8'' (25-120 pc)  
  > "The angular resolution (i.e., beam FWHM) ranges between $1.0\ensuremath{''}$–$1.8\ensuremath{''}$, corresponding to 25–120 pc linear resolution at the targets’ distances." (2.1 Cloud-scale Resolution CO Data)
- max recoverable scale: _not stated_
- sensitivity: 1sigma 0.2-0.3 K in a 2.5 km/s channel  
  > "The 1$\sigma$ noise level in the data is $0.2\text{--}0.3$ K in a $2.5\,\mbox{$\rm km\,s^{-1}$}$ channel." (2.1 Cloud-scale Resolution CO Data)
- time on source: _not stated_
- observing dates: _not stated_
- pi or archival as stated: _not stated_
- Line: CO J=2-1 (not stated)
- Other facility **VLA/ATCA**: HI 21 cm maps for atomic gas  
  > "We include new VLA data from the PHANGS-VLA project (covering 11 targets in our sample; PI: D. Utomo)" (2.2 Kpc-scale Resolution Supporting Data)
- Other facility **Spitzer IRAC**: 3.6 um stellar mass maps (S4G)  
  > "We use *Spitzer* IRAC 3.6 $\mu$m data to trace the stellar mass distribution." (2.2 Kpc-scale Resolution Supporting Data)
- Other facility **GALEX and WISE**: NUV and 12 um data for SFR  
  > "We combine GALEX near-UV (NUV) data and WISE mid-IR (MIR) data to derive kpc-scale star formation rate (SFR) estimates." (2.2 Kpc-scale Resolution Supporting Data)
- External data: S4G stellar disk scale lengths and bulge decompositions  
  > "we use the $\mathrm{S^4G}$ structural decomposition results presented by (cite: Salo_etal_2015)." (3.2 CO Flux from Various Morphological Regions) [from (cite: Salo_etal_2015)]
- External data: Visual bar identification  
  > "To identify bar regions, we instead use results from the visual identification in (cite: Herrera-Endoqui_etal_2015)" (3.2 CO Flux from Various Morphological Regions) [from (cite: Herrera-Endoqui_etal_2015)]
- External data: Mass-metallicity relation used to predict Z'  
  > "Using a mass-metallicity relation reported by (cite: Sanchez_etal_2019), we first predict $Z'$ at one effective radius ($R_\mathrm{e}$)" (3.3.1 Cloud-scale Molecular Gas Properties) [from (cite: Sanchez_etal_2019)]

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
- masking: 'strict' signal masks for moment maps; 'broad' mask for total flux  
  > "selected by the “strict” signal masks as described in A. K. Leroy et al., in preparation" (2.1 Cloud-scale Resolution CO Data)
- multiscale scales: _not stated_
- continuum subtraction: _not stated_
- line free channels: _not stated_
- primary beam correction: _not stated_
- array combination: _not stated_
- smoothing: Cubes convolved to 60 pc, 120 pc and 1 kpc  
  > "we convolve all the data cubes to two different linear resolutions, 60 pc and 120 pc, whenever possible." (2.1 Cloud-scale Resolution CO Data)
- final beam: _not stated_
- final rms: _not stated_

### Inherited from earlier work

- CO data reduction  
  > "For more details regarding the CO data reduction, readers are referred to A. K. Leroy et al. (in preparation) and (cite: Sun_etal_2018)." (2.1 Cloud-scale Resolution CO Data) [from A. K. Leroy et al. (in preparation); (cite: Sun_etal_2018)]
- Cloud-scale surface density and velocity dispersion estimation  
  > "Following (cite: Sun_etal_2018), we estimate cloud-scale molecular gas surface density ($\Sigma_\mathrm{mol,\,\theta pc}$)" (3.3.1 Cloud-scale Molecular Gas Properties) [from (cite: Sun_etal_2018)]
- SFR calibration  
  > "following the calibration suggested by (cite: Leroy_etal_2019)" (3.3.2 Kpc-scale Environment Characteristics) [from (cite: Leroy_etal_2019)]

### Not stated but needed to reproduce (our reading)

- Calibrated PHANGS-ALMA v3.4 cubes are an internal release; imaging parameters (robust, cell, deconvolver) not given
- Exact strict/broad mask construction not given
- Convolution kernel and handling of noise after convolution not specified
- Bootstrap details for fit errors
- Hexagonal grid center/orientation definition
- PHANGS-VLA HI processing

## Analysis recipe

1. **Homogenize data and aperture**: Convolve CO cubes to 60/120 pc and 1 kpc, build moment maps, tile footprint in 1 kpc hexagonal apertures  
  > "We first divide the PHANGS-ALMA CO observation footprint into hexagonal apertures." (3 Methods)
   - parameter: 1 kpc spacing between aperture centers  
  > "with a 1 kpc spacing (corresponding to $8''$–$40''$) between the centers of adjacent apertures" (3 Methods)
   - fitting: _not stated_
   - validation: CO flux recovery fraction per aperture  
  > "we quantify a CO flux recovery fraction, $f_\mathrm{CO,\,\theta pc}$, within each 1 kpc aperture." (3.1 CO Flux Recovery Fraction)
2. **Convert observables to physical quantities**: Sigma_mol = alpha_CO/R21 I_CO; metallicity-dependent alpha_CO; HI, 3.6um, NUV+12um conversions  
  > "$R_{21} = 0.7$ is the adopted $\mathrm{CO}\,(2\text{--}1)$ to $\mathrm{CO}\,(1\text{--}0)$ line ratio" (3.3.1 Cloud-scale Molecular Gas Properties)
   - parameter: alpha_CO = 4.35 Z'^-1.6; metallicity gradient -0.1 dex/Re  
  > "$$\begin{equation}
    \alpha_\mathrm{CO}= 4.35\,Z'^{-1.6}\;\mbox{$\rm M_{\odot}\,pc^{-2}$}\,(\mbox{$\rm K\,km\,s^{-1}$})^{-1}~.
\label{eq:alphaCO}
\end{equation}$$" (3.3.1 Cloud-scale Molecular Gas Properties)
   - assumption: 3.6 um mass-to-light ratio 0.47 Msun/Lsun  
  > "This conversion assumes a 3.6 $\mu$m mass-to-light ratio of $Y_{3.6} = 0.47\,M_\odot/L_\odot$ (cite: McGaugh_Schombert_2014)." (3.3.2 Kpc-scale Environment Characteristics)
   - fitting: _not stated_
   - validation: Three alternative alpha_CO prescriptions tested  
  > "we re-derive our key measurements using three alternative $\alpha_\mathrm{CO}$ prescriptions, and compare them with our fiducial prescription." (6.1 CO-to-H~2~ Conversion Factor)
3. **Compute turbulent and equilibrium pressures**: P_turb = 3 Sigma sigma^2/(2D) with D = beam FWHM; P_DE at kpc scale and cloud scale (weight of clouds + atomic layer); CO-intensity weighted averages  
  > "we assume a constant density spherical cloud filling each beam, with the cloud diameter $D_\mathrm{cloud}$ equal to the beam FWHM" (4.1 Internal Pressure in Molecular Gas)
   - parameter: sigma_atom = 10 km/s; R*/H* = 7.3  
  > "We adopt a fixed atomic gas velocity dispersion $\sigma_\mathrm{atom}=10\;\mbox{$\rm km\,s^{-1}$}$" (4.2 Kpc-scale Dynamical Equilibrium Pressure)
   - assumption: Turbulence dominates internal pressure; dark matter neglected  
  > "we assume in this work that turbulent motion represents the primary source of internal pressure in molecular gas, and treat all other contributions as sub-dominant." (4.1 Internal Pressure in Molecular Gas)
   - fitting: _not stated_
   - validation: Flared disk, fixed sigma_gas,z and CPROPS cloud segmentation comparisons  
  > "In Section [6.3](#sec:systematics:CPROPS) we compare our method with an alternative method that relies on cloud segmentation." (6 Systematic Effects)
4. **Fit power-law relations and correlations**: OLS in log space for P_turb vs P_DE,1kpc; f_CO-weighted OLS bisector for P_turb vs P_DE,cloud; bisector for SFR-P_DE and Rmol-P_DE; Spearman correlations  
  > "We weight each measurement by its corresponding CO recovery fraction $f_\mathrm{CO}$, and perform an OLS bisector fit (cite: Isobe_etal_1990) in logarithmic space." (5.2.2 Quantifying the Turbulent Pressure–Equilibrium Pressure Relation on Cloud Scales)
   - fitting: Bootstrap statistical errors  
  > "All the quoted errors here are *statistical* errors estimated from bootstrapping." (Table 3)
   - validation: Systematic variation of slope/offset in Table 4  
  > "Across all rows, the amplitude of variations in the best-fit $\beta$ and $A$ values roughly reflect their systematic uncertainties." (Table 4)

## Software

- **CASA** : Listed in software section  
  > "`CASA` (cite: McMullin_etal_2007), `Astropy`" (Software)
- **Astropy** : Listed in software section  
  > "`CASA` (cite: McMullin_etal_2007), `Astropy` (cite: AstropyCollaboration_etal_2013; AstropyCollaboration_etal_2018)" (Software)
- **CPROPS** : Cloud catalogs for comparison  
  > "We use the PHANGS-ALMA CPROPS cloud catalogs, which are derived from the same CO dataset that we use" (6.3 Intensity Statistics versus Cloud Segmentation)

## Numeric results

| quantity | value | uncertainty | units | step | quote |
|---|---|---|---|---|---|
| Median P_turb,120pc/P_DE,1kpc over-pressurization factor (disk) | 2.8 | 1sigma range 1.3-6.3 | dimensionless | 3 | We find a median over-pressurized factor of 2.8, and a 1$\sigma$ range of 1.3–6.3 at this resolution. |
| Median P_turb,60pc/P_DE,1kpc (disk) | 6.0 | 1sigma range 3.1-12.1 | dimensionless | 3 | The median and 1$\sigma$ range of the over-pressurized factor is 6.0 and 3.1–12.1, respectively. |
| P_turb,120pc vs P_DE,120pc slope | 1.02 | 0.01 | dimensionless | 4 | $1.02[\pm0.01]\ensuremath{^{*}}$ / $-0.12[\pm0.01]\ensuremath{^{*}}$ dex / 0.17 dex |
| P_turb,60pc vs P_DE,60pc slope | 0.95 | 0.02 | dimensionless | 4 | $0.95[\pm0.02]\ensuremath{^{*}}$ / $0.06[\pm0.01]\ensuremath{^{*}}$ dex / 0.13 dex |
| Sigma_SFR-P_DE relation slope | 0.84 | 0.01 (stat) | dimensionless | 4 | \frac{\Sigma_\mathrm{SFR}}{10^{-3}\;\mbox{$\rm M_{\odot}\,yr^{-1}\,kpc^{-2}$}} = 3.2\, \left(\frac{P_\mathrm{DE}}{10^4\;\mbox{$k_\mathrm{B}\rm\,K\,cm^{-3}$}}\right)^{0.84} |
| R_mol-P_DE threshold pressure P0 | 2.1e4 | 0.01 dex stat; ~0.15 dex sys | k_B K cm^-3 | 4 | 0.01 dex for the threshold pressure $P_0=2.1\times10^4\,\mbox{$k_\mathrm{B}\rm\,K\,cm^{-3}$}$ |
| Stellar disk flattening R*/H* | 7.3 | +2.6/-1.9 | dimensionless | 0 | R_\star/H_\star=7.3^{+2.6}_{-1.9} |

## Qualitative findings

- Cloud-scale dynamical equilibrium holds in disk regions; bulge/bar regions show higher P_turb  
  > "many measurements in bulge or bar regions show systematically higher $\left<P_\mathrm{turb,\,\theta pc}\right>$." (5.2.1 Differentiating Morphological Regions)

## Claim tuples

- H: Molecular gas pressure equals smooth-disk kpc-scale P_DE | E: Compare P_turb to P_DE,1kpc in 1762 apertures | R: P_turb exceeds P_DE,1kpc, median factor 2.8 at 120 pc | F: Molecular gas is over-pressurized relative to the smooth-disk estimate | **supported**
- H: Clumping explains the over-pressure | E: Cloud-scale P_DE including self-gravity, external gravity and ambient pressure | R: Near-unity slope (1.02) with 0.17 dex scatter | F: Dynamical equilibrium holds on cloud scales | **supported**
- H: Feedback regulates star formation | E: Compare Sigma_SFR with P_turb and P_DE | R: Strong correlations; slope 0.84 | F: Consistent with feedback-driven momentum injection, if SF clumping is considered | **partially**

## Reasoning

- Why this data: _not stated_
- Why this method: Top-down aperture approach avoids cloud identification and handles marginally resolved data  
  > "it is designed to robustly treat data with a wide range of physical resolutions, even when individual gas structures are not fully resolved or cleanly separated from one another." (4 Pressure Estimates)
- Alternative: CPROPS cloud segmentation with spherical geometry gives P_turb below P_DE by ~0.66 dex; fixed 120 pc depth restores agreement  
  > "On average, this offset is about 0.66 dex." (6.3 Intensity Statistics versus Cloud Segmentation)
- How they decided it was enough: _not stated_
- Limitation (authors): Sensitivity censoring biases slope shallower; systematics dominate fit errors  
  > "This means that our cloud-scale measurements cannot probe as low molecular gas surface density as our kpc-scale measurements do, and our pressure estimates suffer from a similar censoring effect." (Predicting Turbulent Pressure from Kpc-scale Equilibrium Pressure)
- Caveat (inferred, ours): Uniform-sphere with D = beam FWHM sets P_turb scale and resolution dependence
- Caveat (inferred, ours): P_turb and P_DE both scale with alpha_CO so their agreement is partly built in
- Caveat (inferred, ours): Metallicity predicted from a global relation, not measured
- Caveat (inferred, ours): The 1 kpc scale and stellar scale heights are assumed

## Reproducibility

- Data public (paper): _not stated_
- Products in archive: Derived table released at PHANGS CADC storage  
  > "This table is available in its entirety in the [PHANGS CADC storage](https://www.canfar.net/storage/list/phangs/RELEASES/Sun_etal_2020)." (11 Table of Key Measurements)
- Missing: Internal-release PHANGS-ALMA v3.4 cubes and masks (Leroy et al. in prep)
- Missing: PHANGS-VLA HI data
- Missing: Aperture grid and weighting code
- Data volume (inferred): Hundreds of GB to ~1 TB for CO cubes of 28 galaxies; small derived tables
- Score (inferred): 3/5, Equations and assumptions are fully given and a derived table is public, but the input cubes and masks come from unpublished internal releases.
- Rediscovery candidate: no, The inputs are an internal data release and the masks are not described in this paper.

## Links

- Method: (cite: Sun_etal_2018) (Cloud-scale surface density and velocity dispersion methodology)
- Method: (cite: Leroy_etal_2019) (SFR calibration)
- Companion: A. K. Leroy et al., in preparation (PHANGS-ALMA CO data reduction and masks)
- Related: PHANGS-ALMA
- Related: PHANGS-VLA
- Related: S4G
- Related: z0MGS

## Checks

```json
{
 "quotes": 57,
 "quotes_ok": 57,
 "quote_pass_rate": 1.0,
 "quotes_too_long": 0,
 "unsupported_facts": 0,
 "project_codes": 6,
 "codes_not_in_text": [],
 "codes_not_in_obscore": [],
 "obscore_codes_not_in_card": [],
 "codes_printed_but_missing": [],
 "numeric_results": 7,
 "numeric_problems": 0,
 "fill": {
  "facts": 75,
  "stated": 39,
  "rate": 0.52
 },
 "evidence_ok": true
}
```
