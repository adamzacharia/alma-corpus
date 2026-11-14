# Zooming in to Massive Star Birth

`2018ApJ...867...94K` | The Astrophysical Journal 2018 | first author: Kong, Shuo | arXiv: 1701.05953 | DOI: 10.3847/1538-4357/aae1b2

Card schema 1.0 | model claude-sonnet-5-5 | depth full | type observational_alma_primary

## Science

- Fields: star_formation, astrochemistry, milky_way_ism
- Question: Is the N2D+ core C1-S a massive starless (pre-stellar) core distinct from the nearby protostars C1-Sa and C1-Sb, and what is its dynamical state?  
  > "With this higher-resolution data, we are able to spatially and kinematically resolve the $\rm N_2D^+$(3-2) core from the nearby protostars" (Introduction)
- Target **G028.37+00.07-C1 (C1-S, C1-Sa, C1-Sb)**: coordinates R.A.=18h42m46.585634s, Dec=-04d04m12.36111s (J2000) pointing  
  > "Both observations targeted R.A.=$\rm 18^h42^m46.585634s$" (ALMA Observations); "The C1-S core is at the western end of the massive IRDC G028.37+00.07 at a distance of about 5 kpc" (Introduction); z/distance 5.0 kpc  
  > "Both observations targeted R.A.=$\rm 18^h42^m46.585634s$" (ALMA Observations); "The C1-S core is at the western end of the massive IRDC G028.37+00.07 at a distance of about 5 kpc" (Introduction); distance from Rathborne et al. 2006  
  > "Both observations targeted R.A.=$\rm 18^h42^m46.585634s$" (ALMA Observations); "The C1-S core is at the western end of the massive IRDC G028.37+00.07 at a distance of about 5 kpc" (Introduction)

## Data provenance

- ALMA projects: 2013.1.00248.S
- bands: Band 6 (1.3 mm)  
  > "The observations were carried out in *ALMA* band 6." (ALMA Observations)
- frequencies and spectral setup: Seven spectral windows in four basebands: N2D+(3-2), 12CO(2-1)+continuum, C18O(2-1), DCO+, CH3OH, SiO, DCN  
  > "Four basebands and seven spectral windows were used." (ALMA Observations)
- continuum bandwidth: ~1.4 GHz aggregate for imaging  
  > "the final aggregate continuum bandwidth is $\sim$ 1.4 GHz for imaging" (ALMA Observations)
- arrays: _not stated_
- configurations: C34-1 (compact) and C34-6 (extended), 12m array  
  > "The compact configuration (C34-1) observation was performed on 05-Apr-2015 (UTC) with 34 12-m antennas" (ALMA Observations)
- baselines: 15-327 m (compact); 34-1574 m (extended)  
  > "The baselines range from 34m to 1574m, corresponding to angular scales from 2.3$''$ to 0.2$''$." (ALMA Observations)
- angular resolution: ~0.25'' extended; 0.2'' combined continuum; 0.3'' lines  
  > "The angular resolution obtained from this observation is about 0.25$''$ ." (ALMA Observations)
- max recoverable scale: _not stated_
- sensitivity: continuum 0.040 mJy/beam combined; line ~6 mJy/beam per 0.1 km/s combined  
  > "0.040 mJy beam$^{-1}$ for the combined data" (ALMA Observations)
- time on source: 2087 s compact; 4174 s extended  
  > "a total on-source integration time of 4174 seconds" (ALMA Observations)
- observing dates: 05-Apr-2015 (compact), 03-Jul-2015 (extended)  
  > "The extended configuration (C34-6) data were taken on 03-Jul-2015 (UTC)" (ALMA Observations)
- pi or archival as stated: PI Tan, Cycle 2  
  > "The observations were carried out during *ALMA* Cycle 2, under the project 2013.1.00248.S (PI: Tan)" (ALMA Observations)
- Line: N2D+ 3-2 (231.32183 GHz)
- Line: 12CO 2-1 (230.538 GHz)
- Line: C18O 2-1 (219.56036 GHz)
- Line: DCO+ 3-2 (216.11258 GHz)
- Line: DCN 3-2 (217.23853 GHz)
- Other facility **VLA**: NH3 (1,1) and (2,2) D-configuration data for gas kinetic temperature  
  > "in its D configuration on 2014 August 12 and September 11, with the same correlator setup to observe NH$_3$ (J,K) = (1,1) and (2,2) lines" (VLA Observations)
- Other facility **Herschel**: 70 and 100 um images used to check for point sources  
  > "In *Herschel* 70 $\ensuremath{\mu}m$ and 100 $\ensuremath{\mu}m$ images, this entire region has no sign of point sources" (3.2.1)
- External data: MIREX mid-IR extinction mass surface density map  
  > "We first use the MIREX image from (cite: 2014ApJ...782L..30B) to estimate the mass surface density of the core" (3.2.4) [from (cite: 2014ApJ...782L..30B)]
- External data: Dust opacity model (thin ice mantle, moderately coagulated)  
  > "using the opacities of the moderately coagulated thin ice mantle model of (cite: 1994A&A...291..943O)" (3.1) [from (cite: 1994A&A...291..943O)]
- External data: Dust temperature of 10+-3 K for C1-S  
  > "T13 estimated $T_{d}= 10\pm3$ K, based on the region appearing dark at up to $\sim100\:{\rm \mu m}$." (3.1) [from (cite: 2013ApJ...779...96T)]
- External data: Astrochemical model for N2D+  
  > "The chemical model is from (cite: 2015ApJ...804...98K)" (3.5) [from (cite: 2015ApJ...804...98K)]

## Processing

### Calibration

- pipeline or manual: _not stated_
- casa version: _not stated_
- pipeline version: _not stated_
- archive products used as is: _not stated_
- flux calibrator: Neptune (compact), Titan (extended)  
  > "the flux calibrator was Neptune" (ALMA Observations)
- flux scale uncertainty: _not stated_
- self calibration: Three iterations of phase-only self-cal on compact data; solutions applied to other spws  
  > "For the compact data, we performed three iterations of phase-only self-calibration, which improved the sensitivity by a factor of two." (ALMA Observations)

### Imaging

- task: CASA clean  
  > "We performed the standard cleaning procedure in CASA using the task *clean*." (ALMA Observations)
- deconvolver: _not stated_
- weighting robust: Briggs robust 0.5 for continuum and CO; natural for lines  
  > "we used the Briggs weighting with a robust number of 0.5" (ALMA Observations)
- uv taper: Outer uv-taper to 0.57''x0.54'' beam for smoothed N2D+  
  > "obtained by applying an outer uv-taper to the $\rm N_2D^+~$data to have a $0.57\ensuremath{''}\times0.54\ensuremath{''}~P.A.=89.59\ensuremath{^\circ}$ beam" (3.2.1)
- cell size: _not stated_
- image size: _not stated_
- masking: _not stated_
- multiscale scales: _not stated_
- continuum subtraction: _not stated_
- line free channels: _not stated_
- primary beam correction: _not stated_
- array combination: Compact and extended data imaged together  
  > "combining compact and extended configuration observations that achieve 0.2$''$ resolution" (Introduction)
- smoothing: _not stated_
- final beam: ~0.25'' continuum/CO; ~0.3'' lines  
  > "(restoring beam $\sim$ 0.3$''$)" (ALMA Observations)
- final rms: _not stated_

### Inherited from earlier work

- Mass estimate from 1.3 mm continuum using eq. (7) of T13  
  > "following eq. (7) of T13" (3.1) [from Tan et al. 2013 (cite: 2013ApJ...779...96T)]
- Dynamical analysis approach, Turbulent Core Model  
  > "Our general methodological approach follows that of T13." (3.2.4) [from T13; MT03 (cite: 2003ApJ...585..850M)]
- NH3 temperature fitting routines  
  > "following the routines outlined in (cite: 2012ApJ...745L..30W; 2014MNRAS.439.3275W)" (VLA Observations) [from (cite: 2012ApJ...745L..30W; 2014MNRAS.439.3275W)]
- N2D+ HFS fitting assuming optically thin line  
  > "assuming the line is optically thin (cite: 2016ApJ...821...94K)" (3.2.3) [from (cite: 2016ApJ...821...94K)]

### Not stated but needed to reproduce (our reading)

- Number of clean iterations, thresholds and masks for clean
- Cell and image size
- Line-free channels and continuum subtraction method
- Self-calibration solution intervals
- Exact aperture centers and radii for C1-S inner/outer (beyond table values)
- Flux calibrator model details
- Exact annuli definitions for radial profiles
- N2D+ column density derivation details and hyperfine parameters

## Analysis recipe

1. **Image continuum and lines**: CASA clean of combined compact+extended data; Briggs 0.5 continuum, natural weighting lines  
  > "In the following, all analysis are based on the combined images." (ALMA Observations)
   - software: CASA
   - fitting: _not stated_
   - validation: _not stated_
2. **Derive NH3 kinetic temperature**: Fit NH3 (1,1) and (2,2) simultaneously with five free parameters on pixels >6 sigma  
  > "The model fitting is performed on pixels with $>6 \sigma$ NH$_3$ (J,K) = (1,1) integrated intensity." (VLA Observations)
   - software: CASA
   - fitting: _not stated_
   - validation: _not stated_
3. **Core masses from dust continuum**: Sigma_mm from eq. with Ossenkopf & Henning opacity, kappa=5.95e-3 cm2/g, 30% opacity uncertainty; envelope subtraction  
  > "We choose $\kappa_\nu = 5.95\times
10^{-3}\:{\rm cm^2\:g^{-1}}$ and assume 30% uncertainties in these opacities." (3.1)
   - assumption: Dust T=10+-3 K for starless core; 20 K (15-30) for protostellar cores; 15+-5 K for clump; distance 5 kpc  
  > "Here we adopt a fiducial temperature of 20 K for the protostellar cores C1-Sa and C1-Sb" (3.1)
   - fitting: _not stated_
   - validation: _not stated_
4. **Radial density structure**: Fit projected singular polytropic profile rho~r^-k to surface density profile, with isothermal and T-gradient cases  
  > "Following the turbulent core model of MT03, we assume a core volume density profile following a singular polytropic spherical structure" (3.2.2)
   - fitting: _not stated_
   - validation: _not stated_
5. **Velocity dispersion of core**: HFS fit of N2D+(3-2) spectra, thermal subtraction and H2 thermal added back; chi2 fit of sigma(r) profile  
  > "We performed hyperfine-structure spectral fitting to the $\rm N_2D^+$(3-2) spectrum using the HFS method of the CLASS software package" (3.2.3)
   - software: CLASS
   - fitting: _not stated_
   - validation: _not stated_
6. **Virial/magnetic analysis**: Compare sigma_N2D+ to Turbulent Core virial sigma; derive virial parameter, phi_B, m_A, B-field  
  > "Thus our basic procedure is to evaluate $\sigma_{\rm c,vir}$ using equation" (3.2.4)
   - fitting: _not stated_
   - validation: _not stated_
7. **CO depletion and astrochemical model**: _not stated_
   - assumption: Tex=10 K optically thin; [12CO/H]=1e-4; 16O/18O=557  
  > "Assuming \[$^{12}$CO/H\] = 10$^{-4}$ and \[$^{16}$O/$^{18}$O\] = 557" (3.4)
   - fitting: _not stated_
   - validation: _not stated_

## Software

- **CASA** 4.2.2 (VLA only): ALMA cleaning and VLA reduction  
  > "Data reduction was performed in CASA 4.2.2." (VLA Observations)
- **CLASS (GILDAS)** : hyperfine fitting of N2D+(3-2)  
  > "using the HFS method of the CLASS software package" (3.2.3)

## Numeric results

| quantity | value | uncertainty | units | step | quote |
|---|---|---|---|---|---|
| C1-S outer mass (fiducial, T=10 K, total) | 58.8 | 26.8-123 (T range) | Msun | 3 | 58.8$_{26.8}^{123}$ |
| C1-Sa envelope mass (T=20 K) | 33.5 | 20.2-49.5 | Msun | 3 | C1-Sa / 28.32209 / 0.06770 / 2.18 / 49.5 / 33.5$^a$ / 20.2 |
| sigma_N2D+ C1-S inner | 0.302 | 0.0267 | km/s | 5 | 0.302$\pm$0.0267 |
| sigma_N2D+/sigma_c,vir (envelope-subtracted, inner) | 0.402 | 0.311-0.604 | dimensionless | 6 | 0.402$_{0.311}^{0.604}$ |
| CO depletion factor C1-S inner | >616 | not stated | dimensionless | 7 | corresponds to a CO depletion factor of $f_{D}> 616$ |
| B-field needed for virial equilibrium at C1-S outer | ~2 | not stated | mG | 6 | $B_{\rm c,crit}\simeq B_{\rm c,vir}\simeq 2\:$mG |

## Qualitative findings

- C1-S shows no centrally peaked continuum, no CO outflow and no point source in Herschel, consistent with starless core  
  > "In summary, C1-S shows no obvious sign of star formation." (3.2.1)

## Claim tuples

- H: C1-S is a starless massive core distinct from protostars | E: 0.2'' N2D+, continuum and CO imaging | R: N2D+ core separated from C1-Sa/Sb, no outflow or peaked continuum | F: C1-S is a promising massive pre-stellar core (~50 Msun) | **supported**
- H: C1-S is in virial equilibrium with fiducial turbulent core | E: Compare N2D+ dispersion to virial prediction | R: ratio ~0.4 | F: Sub-virial unless ~2 mG fields exist | **partially**

## Reasoning

- Why this data: _not stated_
- Why this method: _not stated_
- Alternative: Sub-virial fast collapse rejected as unlikely given deuteration timescale  
  > "It seems unlikely that all the core material is slowly moving and on the verge of fast collapse" (3.2.4)
- How they decided it was enough: _not stated_
- Limitation (authors): Hard to determine core structure given temperature and opacity uncertainties  
  > "we conclude that it is difficult to determine the core structure from the current data" (3.2.2)
- Caveat (inferred, ours): Mass depends on assumed dust temperature and opacity (factor ~2)
- Caveat (inferred, ours): Constant N2D+ abundance assumed
- Caveat (inferred, ours): B-field inferred indirectly, not measured

## Reproducibility

- Data public (paper): ALMA project cited; public status not explicitly stated  
  > "This paper makes use of the following ALMA data: ADS/JAO.ALMA#2013.1.00248.S." (Acknowledgments)
- Products in archive: _not stated_
- Missing: Clean parameters
- Missing: Aperture definitions
- Missing: VLA data not provided with project code
- Data volume (inferred): ~50-100 GB raw for two ALMA EBs
- Score (inferred): 5/5, Data are identified and many numbers given, but imaging and aperture details are sparse.
- Rediscovery candidate: no, Key steps depend on VLA data and inherited choices; imaging details are incomplete.

## Links

- Method: Tan et al. 2013 (cite: 2013ApJ...779...96T) (mass and dynamics method)
- Companion: Tan et al. 2016 (cite: 2016ApJ...821L...3T) (compact configuration results of same project)

## Checks

```json
{
 "quotes": 63,
 "quotes_ok": 63,
 "quote_pass_rate": 1.0,
 "quotes_too_long": 0,
 "unsupported_facts": 0,
 "project_codes": 1,
 "codes_not_in_text": [],
 "codes_not_in_obscore": [],
 "obscore_codes_not_in_card": [],
 "codes_printed_but_missing": [],
 "numeric_results": 6,
 "numeric_problems": 0,
 "fill": {
  "facts": 81,
  "stated": 45,
  "rate": 0.556
 },
 "evidence_ok": true
}
```
