# ALMA Detects CO(3-2) within a Super Star Cluster in NGC 5253

`2017ApJ...846...73T` | The Astrophysical Journal 2017 | first author: Turner, Jean L. | arXiv: 1706.09944 | DOI: 10.3847/1538-4357/aa8669

Card schema 1.0 | model claude-sonnet-5-5 | depth full | type observational_alma_primary

## Science

- Fields: nearby_galaxies, star_formation
- Question: What are the properties of the molecular cloud coincident with the supernebula in NGC 5253 (Cloud D1), and what do they imply for the cluster's IMF, gas content and feedback?  
  > "We present here an analysis of the molecular cloud coincident with the supernebula, henceforth denoted “Cloud D1"." (Introduction)
- Target **NGC 5253 supernebula / Cloud D1**: coordinates RA 13h39m55.9651s, Dec -31d38m24.364s (J2000)  
  > "NGC 5253 is a local (3.8 Mpc: 1$''$ = 18.4 pc) dwarf spheroidal galaxy" (Introduction); "Assumed distance" (Table 1); z/distance 3.8 Mpc  
  > "NGC 5253 is a local (3.8 Mpc: 1$''$ = 18.4 pc) dwarf spheroidal galaxy" (Introduction); "Assumed distance" (Table 1); distance from not stated (assumed; cites earlier work)  
  > "NGC 5253 is a local (3.8 Mpc: 1$''$ = 18.4 pc) dwarf spheroidal galaxy" (Introduction); "Assumed distance" (Table 1)

## Data provenance

- ALMA projects: 2012.1.00105.S
- bands: Band 7  
  > "NGC 5253 was observed in Band 7" (Observations)
- frequencies and spectral setup: Spectral windows total bandwidth 937.500 MHz, 244.141 kHz per channel  
  > "Spectral windows have a total bandwidth of 937.500 MHz, with 244.141 kHz per channel." (Observations)
- continuum bandwidth: _not stated_
- arrays: _not stated_
- configurations: _not stated_
- baselines: _not stated_
- angular resolution: 0.33'' x 0.27'' p.a. -90 deg  
  > "The synthesized beam for the CO(3-2) maps is 0.33$''$ $\times$ 0.27$''$  p.a. -90$^\circ$." (Observations)
- max recoverable scale: emission more extended than ~4'' (~75 pc) poorly represented; shortest baselines 25-100 kλ  
  > "The shortest baselines in the image are 25-100 k$\lambda$; emission more extended than $\sim$4$''$ ($\sim$75 pc) can be poorly represented in these maps" (Observations)
- sensitivity: RMS 2.7 mJy/beam in 1 km/s CO(3-2) channel maps  
  > "The RMS noise in the individual 1 $\rm km\,s^{-1}$ line maps is 2.7 mJy/bm for CO(3-2) at 345.796 GHz." (Observations)
- time on source: _not stated_
- observing dates: 2015 June 4 and 5  
  > "executed in Cycle 2 on 2015 June 4 and 5" (Observations)
- pi or archival as stated: Cycle 1 program, PI J. Turner  
  > "a Cycle 1 program (ID = 2012.1.00105.S, PI = J. Turner)" (Observations)
- Line: CO J=3-2 (345.796 GHz)
- Line: 13CO J=3-2 (not stated)
- Other facility **SMA**: CO(3-2) comparison to estimate extended emission fraction  
  > "from comparison with SMA data we estimate that $\sim$50% of the emission is in such faint, extended structure" (Observations)
- External data: Lyman continuum rate N_Lyc ≳ 3.3e52 s^-1 from radio continuum and recombination line fluxes  
  > "a Lyman continuum rate of $N_{Lyc} \ensuremath{\gtrsim} 3.3 \times 10^{52}~\rm s^{-1}$ is indicated (cite: 2015Natur.519..331T)" (Cloud D1 and the supernebula) [from (cite: 1998AJ....116.1212T; Bendo17; 2015Natur.519..331T)]
- External data: Gas temperature ~300 K from CO(3-2)/CO(1-0) modeling  
  > "For 300 K, as estimated from modeling of the CO(3-2)/CO(1-0) line ratio (cite: 2015Natur.519..331T)" (Cloud D1 and the supernebula) [from (cite: 2015Natur.519..331T)]
- External data: HII gas mass ~2000 Msun in supernebula  
  > "The mass of ionized gas in the supernebula is $M_{HII} \sim 2000$ $\rm M_\odot$ (cite: 2004ApJ...602L..85T)" (Cloud D1 and the supernebula) [from (cite: 2004ApJ...602L..85T)]
- Simulation/model as data: Starburst99 models (Padova and Geneva, Z=0.004 and 0.008, Kroupa IMF exponent 2.3)  
  > "models were run for Padova and Geneva models for metallicities of Z=0.004 (closest to the mean metallicity of NGC 5253) and 0.008 with Kroupa initial mass functions (IMFs) with exponent 2.3" (Cloud D1 and the supernebula)

## Processing

### Calibration

- pipeline or manual: CASA pipeline by JAO for calibration  
  > "Calibration was done with CASA, pipeline 4.2.2 by the Joint ALMA Observatory." (Observations)
- casa version: 4.2.2 (calibration); 4.5.0 (imaging)  
  > "Imaging was done with CASA pipeline 4.5.0 by the authors." (Observations)
- pipeline version: _not stated_
- archive products used as is: _not stated_
- flux calibrator: Titan (bandpass J1427-42064, phase J1342-2900)  
  > "Bandpass and phase were calibrated with J1427-42064 and J1342-2900 respectively. Titan was the flux calibrator." (Observations)
- flux scale uncertainty: within 10%  
  > "Absolute flux calibration is to within 10% for Cycle 2 Band 7 data (cite: L2013)." (Observations)
- self calibration: _not stated_

### Imaging

- task: CASA pipeline 4.5.0 imaging by authors  
  > "Imaging was done with CASA pipeline 4.5.0 by the authors." (Observations)
- deconvolver: _not stated_
- weighting robust: _not stated_
- uv taper: _not stated_
- cell size: _not stated_
- image size: _not stated_
- masking: Moment 0 summing emission above ±2.5σ in cube  
  > "The integrated intensity map (Moment 0 map) was made by summing emission greater than $\pm 2.5\sigma$ in the cube." (Observations)
- multiscale scales: _not stated_
- continuum subtraction: continuum from offline channels, subtracted in uv data  
  > "A continuum map was constructed from offline channels in the band and subtracted from the (u,v) data by the authors before making line maps." (Observations)
- line free channels: _not stated_
- primary beam correction: _not stated_
- array combination: _not stated_
- smoothing: _not stated_
- final beam: 0.33'' x 0.27'' p.a. -90 deg  
  > "The synthesized beam for the CO(3-2) maps is 0.33$''$ $\times$ 0.27$''$  p.a. -90$^\circ$." (Observations)
- final rms: 2.7 mJy/beam per 1 km/s channel  
  > "The RMS noise in the individual 1 $\rm km\,s^{-1}$ line maps is 2.7 mJy/bm for CO(3-2) at 345.796 GHz." (Observations)

### Inherited from earlier work

- Full mosaic including 13CO(3-2) and nearby clouds presented elsewhere  
  > "The full mosaic of NGC 5253 including $^{13}$CO(3–2) is presented elsewhere (cite: SMC17)." (Observations) [from (cite: SMC17)]
- Lyman continuum correction for 30% dust absorption following Inoue procedure  
  > "corrected for 30% direct absorption of uv photons by dust (cite: 2015Natur.519..331T) following the procedure of (cite: 2001AJ....122.1788I)" (Table 1) [from (cite: 2015Natur.519..331T; 2001AJ....122.1788I)]

### Not stated but needed to reproduce (our reading)

- Robust/weighting, cell and image size, deconvolver and clean threshold
- Line-free channels used for continuum
- Exact virial mass formula and coefficient for r^-1 profile
- Partition-function/Einstein constants for the optically thin CO mass
- Starburst99 input parameters other than IMF and mass limits
- Whether the pipeline product beam/primary-beam correction was applied
- Aperture flux method for 13CO and its uncertainty

## Analysis recipe

1. **Image CO(3-2) and 13CO(3-2) and make moment 0**: Continuum subtraction in uv, line cubes, moment 0 summing >±2.5σ  
  > "The integrated intensity map (Moment 0 map) was made by summing emission greater than $\pm 2.5\sigma$ in the cube." (Observations)
   - software: CASA
   - parameter: 1 km/s channels, rms 2.7 mJy/beam  
  > "The RMS noise in the individual 1 $\rm km\,s^{-1}$ line maps is 2.7 mJy/bm for CO(3-2) at 345.796 GHz." (Observations)
   - fitting: _not stated_
   - validation: _not stated_
2. **Measure size, centroid, linewidth and fluxes of Cloud D1**: Gaussian fit to moment 0 image and channel maps; Gaussian line fit; fluxes in 0.5'' aperture  
  > "A Gaussian fit to the integrated intensity image (Fig. 1) gives a size of 218$\pm$33mas $\times$ 104$\pm$54mas" (Cloud D1 and the supernebula)
   - software: CASA
   - parameter: adopted radius 0.3'' ± 0.05'' (r=2.8 pc)  
  > "We adopt a size of 0.3$''$ $\pm$ 0.05$''$, or r=2.8 pc." (Cloud D1 and the supernebula)
   - assumption: Gaussian source profile  
  > "Deconvolved from beam in CASA assuming a Gaussian source profile." (Table 1)
   - fitting: Gaussian fits in CASA  
  > "FWHM; Gaussian fit to line in CASA." (Table 1)
   - validation: Fits in 24 individual channel maps give consistent sizes  
  > "Fits of D1 within the 24 individual channel maps within the FWHM give sizes of $\ensuremath{\lesssim}$0.3$''$$\pm$ 0.05$''$." (Cloud D1 and the supernebula)
3. **Assess optical depth from CO/13CO ratio**: Compare 12CO/13CO integrated intensity ratio (~50) with abundance ratios and nearby clouds  
  > "The line ratio of $\sim$50 for Cloud D1 is close to the abundance ratio of \[CO\]/\[$^{13}$CO\]$\sim$70 for the solar neighborhood" (Cloud D1 and the supernebula)
   - fitting: _not stated_
   - validation: _not stated_
4. **Derive virial mass**: Virial mass from FWHM linewidth and radius for r^-1 profile  
  > "For an $r^{-1}$ mass profile, as in the Galactic cloud W49N, $M_{vir}$(r$<$2.8 pc)$\sim2.5\pm 0.9 \times 10^5 ~\rm M_\odot$." (Cloud D1 and the supernebula)
   - assumption: Virialized cloud; r^-1 profile (r^-2 gives ~30% less)  
  > "This mass estimate assumes a virialized cloud; it is unclear if this is valid for such a dynamic young source." (Cloud D1 and the supernebula)
   - fitting: _not stated_
   - validation: Mass close to that expected from star cluster based on free-free flux  
  > "Moreover the mass is close to that expected from the star cluster based on its radio free-free flux." (Cloud D1 and the supernebula)
5. **Estimate molecular gas mass**: Optically thin CO mass at Tex=300 K with Galactic CO/H2; alternative with X_CO; add HII and HI  
  > "for $T_{ex} = 300$ K (cite: 2015Natur.519..331T), an uncertain number, the mass in CO molecules alone is $M_{CO}=3.0 ~\rm M_\odot$ for optically thin emission" (Cloud D1 and the supernebula)
   - assumption: Galactic [CO]/[H2]; X_CO = 4.7e20 cm^-2 (K km/s)^-1  
  > "An alternate method using an empirical CO “conversion factor", $X_{CO} = 4.7\times 10^{20}~\rm cm^{-2}" (Cloud D1 and the supernebula)
   - fitting: _not stated_
   - validation: _not stated_
6. **Constrain IMF with Starburst99**: Run Starburst99 for observed N_Lyc and M_dyn to find required lower IMF cutoff  
  > "Starburst99 models with an upper IMF mass cutoff of 150 $\rm M_\odot$ require a lower IMF mass cutoff $\ensuremath{\gtrsim}$2 $\rm M_\odot$" (Cloud D1 and the supernebula)
   - software: Starburst99
   - parameter: Padova/Geneva, Z=0.004 and 0.008, Kroupa IMF exponent 2.3, upper cutoff 150 or 200 Msun  
  > "Even for a 200 $\rm M_\odot$ cutoff, Starburst99 models indicate a lower mass cutoff $\ensuremath{\gtrsim}$1 $\rm M_\odot$ for the D1 cluster." (Cloud D1 and the supernebula)
   - fitting: _not stated_
   - validation: _not stated_
7. **Estimate clump number from line smoothness**: Channel-to-channel variation of ≲20% implies ~25 clumps per channel, N_cl ≳600  
  > "Channel-to-channel variations for the central 24 channels are typically $\lesssim$20%, implying $\sim$25 clumps per channel and $N_{cl}\gtrsim$600" (The internal structure of Cloud D1)
   - assumption: clump thermal linewidths ~1 km/s  
  > "for clumps with individual thermal linewidths of $\sim$1 $\rm km\,s^{-1}$" (The internal structure of Cloud D1)
   - fitting: _not stated_
   - validation: _not stated_

## Software

- **CASA** 4.2.2 (calibration); 4.5.0 (imaging): Calibration, imaging, continuum subtraction, Gaussian fits  
  > "Imaging was done with CASA pipeline 4.5.0 by the authors." (Observations)
- **Starburst99** : Modeling cluster age and IMF  
  > "We use Starburst99 models to model the cluster age and IMF." (Cloud D1 and the supernebula)
- **AIPS** : listed in Software section; use not stated  
  > "Starburst99 (cite: 1999ApJS..123....3L), CASA, AIPS, SAOImage DS9" (Software)
- **SAOImage DS9** : listed in Software section; use not stated  
  > "Starburst99 (cite: 1999ApJS..123....3L), CASA, AIPS, SAOImage DS9" (Software)

## Numeric results

| quantity | value | uncertainty | units | step | quote |
|---|---|---|---|---|---|
| CO(3-2) FWHM linewidth | 21.7 | 0.5 | km/s | 2 | $21.7\pm0.5$  $\rm km\,s^{-1}$ |
| CO(3-2) centroid velocity | 387.6 | 0.5 | km/s | 2 | $387.6\pm0.5~\rm km\,s^{-1}$ |
| CO(3-2) integrated flux (0.5'' aperture) | 2.2 | 0.2 | Jy km/s | 2 | $2.2\pm0.2$ Jy $\rm km\,s^{-1}$ |
| 13CO(3-2) integrated flux | 0.05 | 0.01 | Jy km/s | 2 | $0.05\pm0.01$ Jy $\rm km\,s^{-1}$ |
| Cloud D1 radius | 0.3 (2.8 pc) | 0.05 | arcsec | 2 | 0.3$''$ $\pm$ 0.05$''$ |
| Virial mass | 2.5e5 | 0.9e5 | Msun | 4 | $2.5\pm0.9\times10^5$ $\rm M_\odot$ |
| CO/13CO line ratio | ~50 | not stated | dimensionless | 3 | The line ratio of $\sim$50 for Cloud D1 |
| Molecular gas mass (optically thin, 300 K) | ~3500 | not stated | Msun | 5 | then for a Galactic \[CO\]/\[H$_2$\] the molecular gas mass is $M_{H2} \sim 3500~M_\odot$ |
| Gas mass via X_CO | 6.5e4 | not stated | Msun | 5 | gives $M_{gas}=6.5\times 10^4 ~\rm M_\odot$ (including He) |
| Gas fraction of mass within cloud | <35 | not stated | percent | 5 | We estimate that gas constitutes $<35$% of the mass within the boundaries of Cloud D1. |
| Bonnor-Ebert mass | ~13 | not stated | Msun | 0 | the Bonnor-Ebert mass of Cloud D1 is $M_{BE }\sim$ 13 $\rm M_\odot$ |
| Number of clumps | ≳600 | not stated | dimensionless | 7 | $N_{cl}\gtrsim$600 |

## Qualitative findings

- Cloud D1 coincides with the supernebula in position and velocity and is optically thin in CO(3-2), likely because the gas is hot.  
  > "we conclude that the molecular cloud is mixed in with the super star cluster" (Conclusions)
- CO appears relatively undisturbed despite the presence of ~1500-2000 O stars.  
  > "In spite of the presence of an estimated $\sim 1500-2000$ O stars within the small cloud, the CO appears relatively undisturbed." (abstract)

## Claim tuples

- H: Is the CO linewidth of Cloud D1 set by the cluster potential, and what does it imply about the IMF? | E: Measure linewidth and size, compute virial mass, compare with N_Lyc using Starburst99 | R: M_vir = 2.5e5 Msun; M/L ~5e-4; lower IMF cutoff ≳1-2 Msun | F: The cluster appears to have a top-heavy IMF. | **supported**
- H: Is CO(3-2) in D1 optically thin? | E: Compare CO and 13CO(3-2) integrated intensities | R: Ratio ~50 vs 11-15 in nearby clouds | F: Emission is optically thin, probably because the gas is hot. | **supported**
- H: Is D1 composed of many clumps or cores? | E: Analyse line smoothness and channel-to-channel variation of size and centroid | R: Variations ≲20%, centroids coincide to ≲20 mas | F: D1 likely consists of many (up to hundreds) clumps or cores. | **partially**

## Reasoning

- Why this data: CO(3-2) is bright, easily excited in dense gas and ALMA gives cluster-scale resolution  
  > "The J=3–2 line of CO is bright and easily excited in dense ($n\ensuremath{\gtrsim} 2\times 10^4~\rm cm^{-3}$) gas" (Introduction)
- Why this method: _not stated_
- Alternative: Alternative to high star formation efficiency: gas already dispersed; rejected since linewidth shows no current dispersal  
  > "Based on the CO linewidth, dispersal of gas from the cluster does not appear to be occurring at present." (Feedback and star formation within a young, massive cluster)
- How they decided it was enough: _not stated_
- Limitation (authors): Molecular gas mass is very uncertain (temperature, metallicity, CO abundance).  
  > "It is exceedingly difficult to determine a molecular gas mass for Cloud D1." (Cloud D1 and the supernebula)
- Limitation (authors): Virial assumption may not hold for a dynamic young source.  
  > "it is unclear if this is valid for such a dynamic young source" (Cloud D1 and the supernebula)
- Caveat (inferred, ours): Gas temperature of 300 K comes from lower-resolution data and drives mass and optical depth conclusions
- Caveat (inferred, ours): Virial mass depends on assumed density profile
- Caveat (inferred, ours): Imaging parameters unspecified, so size and flux are hard to reproduce exactly
- Caveat (inferred, ours): Lyman continuum rate is from the literature and is a lower limit

## Reproducibility

- Data public (paper): Archive data cited with project code; public status not explicitly stated  
  > "This paper makes use of the following ALMA data: ADS/JAO.ALMA# 2012.1.00125.S." (Acknowledgments)
- Products in archive: _not stated_
- Missing: Imaging parameters (weighting, cell, deconvolution)
- Missing: Line-free channels
- Missing: Virial and optically thin mass formulae details
- Missing: Starburst99 setup details
- Missing: Acknowledgments code (2012.1.00125.S) differs from the project code in Observations
- Data volume (inferred): ~50-200 GB raw for a Band 7 mosaic; single-pointing subset smaller
- Score (inferred): 3/5, Data are archival and the basic steps are described, but imaging settings and mass derivations are not fully given.
- Rediscovery candidate: no, Imaging and analysis recipe is incomplete, and several key inputs are from other papers.

## Links

- Method: (cite: 1999ApJS..123....3L) (Starburst99 models)
- Companion: (cite: SMC17) (Full NGC 5253 mosaic including 13CO(3-2) and nearby clouds)
- Companion: (cite: 2015Natur.519..331T) (Earlier SMA CO detection and warm gas temperature estimate)

## Checks

```json
{
 "quotes": 77,
 "quotes_ok": 77,
 "quote_pass_rate": 1.0,
 "quotes_too_long": 0,
 "unsupported_facts": 0,
 "project_codes": 1,
 "codes_not_in_text": [],
 "codes_not_in_obscore": [],
 "obscore_codes_not_in_card": [],
 "codes_printed_but_missing": [
  "2012.1.00125.S"
 ],
 "numeric_results": 12,
 "numeric_problems": 0,
 "fill": {
  "facts": 87,
  "stated": 55,
  "rate": 0.632
 },
 "evidence_ok": true
}
```
