# Physical Conditions and Kinematics of the Filamentary Structure in Orion Molecular Cloud 1

`2020ApJ...893...63T` | The Astrophysical Journal 2020 | first author: Teng, Yu-Hsuan | arXiv: 2003.02459 | DOI: 10.3847/1538-4357/ab7cca

Card schema 1.0 | model claude-sonnet-5-5 | depth light | type multi_facility_alma_minor

## Science

- Fields: star_formation, milky_way_ism
- Question: What are the structure, physical conditions (density, temperature) and kinematics of the dense filamentary gas in OMC1, traced by N2H+ 3-2 and 1-0?  
  > "This study investigates the structure, physical conditions, and gas motions in the OMC1 region." (Introduction)
- Target **Orion Molecular Cloud 1 (OMC1)**: coordinates RA 05:35:12.1, Dec -05:21:15.4 (J2000), map center  
  > "The Orion A molecular cloud, a large-scale filament with an integral-like shape, is the nearest high-mass star-forming region at a distance of 414 pc (cite: omc1_dist)." (Introduction); "centered at R.A.(J2000) = $\rm 5^h 35^m 12^s.1$ and Decl.(J2000) = $-5^\circ 21' 15''.4$" (1.1 mm Observations with the SMT); z/distance 414 pc  
  > "The Orion A molecular cloud, a large-scale filament with an integral-like shape, is the nearest high-mass star-forming region at a distance of 414 pc (cite: omc1_dist)." (Introduction); "centered at R.A.(J2000) = $\rm 5^h 35^m 12^s.1$ and Decl.(J2000) = $-5^\circ 21' 15''.4$" (1.1 mm Observations with the SMT); distance from Menten et al. 2007 (omc1_dist)  
  > "The Orion A molecular cloud, a large-scale filament with an integral-like shape, is the nearest high-mass star-forming region at a distance of 414 pc (cite: omc1_dist)." (Introduction); "centered at R.A.(J2000) = $\rm 5^h 35^m 12^s.1$ and Decl.(J2000) = $-5^\circ 21' 15''.4$" (1.1 mm Observations with the SMT)

## Data provenance

- ALMA projects: _none stated_
- bands: _not stated_
- frequencies and spectral setup: _not stated_
- continuum bandwidth: _not stated_
- arrays: SMA sub-compact, six antennas (N2H+ 3-2); ALMA+IRAM 30m for 1-0 taken from Hacar et al.  
  > "A sub-compact configuration with six antennas in the array was used, providing baselines ranging from 9.476 m to 25.295 m." (1.1 mm Observations with the SMA)
- configurations: _not stated_
- baselines: _not stated_
- angular resolution: SMA+SMT ~5.4''; ALMA+IRAM 30m 4.5''  
  > "The angular resolution and the rms noise level of the combined map are $\sim 5.4''$ and $1.0$ $\rm K \cdot km\ s^{-1}$, respectively." (SMA and SMT Data Combination); "has a circular beam with a size of $4.5''$ in FWHM" (N_2H^+ J=1–0 Observations with ALMA and IRAM 30-m)
- max recoverable scale: _not stated_
- sensitivity: ALMA+IRAM 1-0 cube rms 25 mJy/beam at 0.1 km/s  
  > "a rms level of $25$ $\rm mJy\ beam^{-1}$ at a spectral resolution of $0.1$ $\rm km\ s^{-1}$" (N_2H^+ J=1–0 Observations with ALMA and IRAM 30-m)
- time on source: 45 s per pointing, 144 pointings (SMA)  
  > "giving a total on-source integration time per pointing of 45 seconds" (1.1 mm Observations with the SMA)
- observing dates: SMA: Feb 14, 20, 24, 2014; SMT: Nov 16-17, 2018  
  > "carried out with the SMA on February 14, 20, and 24, 2014" (1.1 mm Observations with the SMA)
- pi or archival as stated: _not stated_
- Line: N2H+ J=3-2 (not stated)
- Line: N2H+ J=1-0 (not stated)
- Other facility **SMA**: N2H+ 3-2 mosaic (144 pointings)  
  > "Using 144 pointing mosaic with a Nyquist sampled hexagonal pattern" (1.1 mm Observations with the SMA)
- Other facility **SMT**: single-dish N2H+ 3-2 OTF map for short spacings  
  > "The On The Fly (OTF) mode was used in order to cover the mapping area of $6' \times 9'$" (1.1 mm Observations with the SMT)
- External data: ALMA + IRAM 30-m combined N2H+ 1-0 cube of OMC1  
  > "we use the $\rm N_2H^+$ 1–0 data cube provided by (cite: omc1_alma), where the ALMA and IRAM 30-m data were combined." (N_2H^+ J=1–0 Observations with ALMA and IRAM 30-m) [from Hacar et al. 2018 (cite: omc1_alma)]
- External data: N2H+ 3-2 hyperfine relative intensities  
  > "With the relative intensities among 16 main hyperfine components for the $\rm N_2H^+$ 3–2 line (cite: hfs_32)" (Hyperfine Spectral Fitting) [from Caselli et al. 2002 (cite: hfs_32)]

## Processing

### Calibration

- pipeline or manual: MIR/IDL for SMA calibration  
  > "The visibility data were calibrated using the MIR/IDL software package." (1.1 mm Observations with the SMA)
- casa version: _not stated_
- pipeline version: _not stated_
- archive products used as is: _not stated_
- flux calibrator: Ganymede (Feb 14), Callisto (other days)  
  > "the flux calibrator was Ganymede on Feb. 14 and Callisto on other two days" (1.1 mm Observations with the SMA)
- flux scale uncertainty: _not stated_
- self calibration: _not stated_

### Imaging

- task: _not stated_
- deconvolver: MOSSDI joint nonlinear deconvolution (MIRIAD)  
  > "followed by a nonlinear joint deconvolution using the CLEAN-based algorithm, MOSSDI" (1.1 mm Observations with the SMA)
- weighting robust: Briggs, robust = 0.5  
  > "The image cube was generated with Briggs weighting with a robust parameter of 0.5" (1.1 mm Observations with the SMA)
- uv taper: _not stated_
- cell size: _not stated_
- image size: _not stated_
- masking: _not stated_
- multiscale scales: _not stated_
- continuum subtraction: _not stated_
- line free channels: _not stated_
- primary beam correction: _not stated_
- array combination: MIRIAD immerge feathering, flux calibration factor 1  
  > "we set the flux calibration factor to 1" (SMA and SMT Data Combination)
- smoothing: _not stated_
- final beam: _not stated_
- final rms: SMA cube ~0.5 K per 0.22 km/s; combined moment 0 1.0 K km/s  
  > "The final data cube has a rms noise level of $\sim 0.5$ K for a $\sim 0.22$ $\rm km\ s^{-1}$ velocity channel." (1.1 mm Observations with the SMA)

### Inherited from earlier work

- Observational details of N2H+ 1-0 data  
  > "The observational details are described in (cite: hacar_2017; omc1_alma)." (N_2H^+ J=1–0 Observations with ALMA and IRAM 30-m) [from (cite: hacar_2017; omc1_alma)]

### Not stated but needed to reproduce (our reading)

- ALMA project code and calibration details of the 1-0 data (only in Hacar et al. 2018)
- Exact pixel/cell and image size of the combined cubes
- Moment-map velocity ranges and clipping
- Hyperfine fit initial guesses and uncertainties method
- How the 1-0 cube was convolved and regridded to the 5.4'' beam
- Non-LTE model abundance/collision rate files and N2H+ column to H2 assumptions used in RADEX
- Mean molecular weight and inclination assumptions for line masses

## Analysis recipe

1. **Combine SMA and SMT cubes**: Feathering with immerge  
  > "We combined the data cubes of the SMA and SMT by using the MIRIAD task *immerge*." (SMA and SMT Data Combination)
   - software: MIRIAD
   - fitting: _not stated_
   - validation: Checked consistency of flux scale of the two cubes  
  > "After checking the consistency in the flux scale of two input image cubes, we set the flux calibration factor to 1." (SMA and SMT Data Combination)
2. **Identify filaments**: FilFinder on moment 0 map  
  > "Filament identification is done by applying the python package *FilFinder* (cite: filfinder) to the SMA + SMT combined moment 0 map." (Filament Identification)
   - software: FilFinder
   - parameter: global threshold 9 K km/s; size threshold 400 px; adaptive threshold 0.06 pc; smooth size 0.03 pc  
  > "The adaptive threshold is set to 0.06 pc, which is approximately twice the width of the filaments, and the smooth size is set to 0.03 pc." (Filament Identification)
   - fitting: Gaussian fits to cuts perpendicular to filaments for FWHM  
  > "We have estimated the typical FWHM of the identified filaments by fitting Gaussian to the several cuts perpendicular to the filaments." (Filament Identification)
   - validation: Smooth size tuned by comparison with identification by eye  
  > "We find the result matches better with identification by human eyes when the smooth size is set to $\sim 0.5$ times the adaptive threshold." (Filament Identification)
3. **Identify cores**: 2-D Clumpfind on moment 0 map  
  > "We identify the high-intensity cores inside the filaments by using the 2-D version of *Clumpfind* (cite: clfind)." (Core Identification)
   - software: Clumpfind
   - parameter: contour levels 50, 53.6, 57.2, 60.8, 64.4 K km/s (spacing 2 Trms)  
  > "set the contour levels as 50, 53.6, 57.2, 60.8, 64.4 $\rm K \cdot km\ s^{-1}$" (Core Identification)
   - fitting: _not stated_
   - validation: _not stated_
4. **Hyperfine spectral fitting for VLSR and linewidth**: LTE hyperfine fit with 16 components, pixels with S/N>5  
  > "we conduct hyperfine spectral fitting on the combined SMA and SMT data for the regions with $S/N > 5$." (Hyperfine Spectral Fitting)
   - assumption: LTE; single component fit even where multiple components exist  
  > "We applied the single-component fitting to the spectra of these regions, because two-component fitting requires too many parameters." (Hyperfine Spectral Fitting)
   - fitting: Fit VLSR, linewidth, Tex, tau_tot  
  > "We fit the $V_{\rm LSR}$, linewidths ($\Delta v$), excitation temperatures ($T_{\rm ex}$), and total opacities ($\tau_{\rm tot}$)" (Hyperfine Spectral Fitting)
   - validation: LTE fit underpredicts satellite lines, motivating non-LTE  
  > "we found that the observed satellite components are much brighter than those predicted by the LTE assumption" (Hyperfine Spectral Fitting)
5. **Non-LTE density and temperature**: RADEX model grid of 3-2 intensity and 3-2/1-0 ratio compared with region-averaged spectra  
  > "Using RADEX (cite: radex), a non-LTE radiative transfer code, we construct spectra models in $\rm N_2H^+$ 3–2 and 1–0." (N_2H^+ RADEX Non-LTE Modeling)
   - software: RADEX
   - parameter: grid: n_H2 1e4-1e9 cm^-3, Tkin 8-60 K, N/dv 5e7-5e8; steps 1 K and 0.5 dex  
  > "The step sizes of the grid are 1 K for $T_{\rm kin}$ and 0.5 in decimal log scale for both $N(\rm N_2H^+)$ and $n_{\rm H_2}$." (N_2H^+ RADEX Non-LTE Modeling)
   - assumption: beam filling factor unity  
  > "In our models, the beam filling factors are assumed to be unity." (N_2H^+ RADEX Non-LTE Modeling)
   - fitting: _not stated_
   - validation: _not stated_
6. **Masses, line masses and virial analysis**: Uniform cylinder masses from non-LTE densities and widths; Mcrit and Mvir formulae  
  > "we have estimated the masses of the cores and the line masses of the filaments under the assumption of uniform cylindrical filaments" (N_2H^+ RADEX Non-LTE Modeling)
   - parameter: Tkin = 20 K, cs = 0.287 km/s; n_H2 = 3e6 for filaments without cores  
  > "we take $T_{\rm kin} = 20$ K for estimation, which leads to $c_s(T) = 0.287$ $\rm km\ s^{-1}$" (Filament and Core Properties)
   - fitting: _not stated_
   - validation: Compared with Hacar et al. 2018 M_lin/M_crit  
  > "Our results show that the filaments in OMC1 have $\rm M_{lin}/M_{crit} < 1.5$, which is consistent with that of (cite: omc1_alma)" (Filament and Core Properties)
7. **Kinematics along minor and major axes**: P-V diagrams, velocity gradients, rotational/gravitational energy, sinusoidal fits to velocity along filament  
  > "In Figure [9](#fig:v_major)a, we show the sinusoidal fits to the velocity oscillation in the east filament." (Major-Axis Analysis)
   - assumption: uniform density (alpha=0), <sin i> = pi/4  
  > "we assume a uniform density profile, i.e. $\alpha = 0$, and a random-averaged inclination angle of $\langle \sin i \rangle = \pi / 4$" (Minor-Axis Analysis)
   - fitting: _not stated_
   - validation: _not stated_

## Software

- **MIR/IDL** : SMA visibility calibration  
  > "The visibility data were calibrated using the MIR/IDL software package." (1.1 mm Observations with the SMA)
- **MIRIAD** : SMA imaging, MOSSDI deconvolution, immerge feathering  
  > "The image processing was carried out using the MIRIAD package (cite: miriad)." (1.1 mm Observations with the SMA)
- **CLASS** : SMT data reduction  
  > "The data were reduced with CLASS." (1.1 mm Observations with the SMT)
- **FilFinder** : Filament identification  
  > "Filament identification is done by applying the python package *FilFinder* (cite: filfinder)" (Filament Identification)
- **Clumpfind** 2-D: Core identification  
  > "by using the 2-D version of *Clumpfind* (cite: clfind)" (Core Identification)
- **RADEX** : Non-LTE N2H+ model grid  
  > "Using RADEX (cite: radex), a non-LTE radiative transfer code" (N_2H^+ RADEX Non-LTE Modeling)

## Numeric results

| quantity | value | uncertainty | units | step | quote |
|---|---|---|---|---|---|
| Number of filaments identified | 11 | not stated | dimensionless | 2 | In total, 11 filaments have been identified. |
| Number of cores identified | 10 | not stated | dimensionless | 3 | Figure [4](#fig:structure)b shows the positions of the 10 cores identified by *2-D Clumpfind*. |
| Filament FWHM width | 0.02-0.03 | not stated | pc | 2 | The FWHM of these filaments are $0.02$–$0.03$ pc |
| Filament-region density | ~1e7 | not stated | cm^-3 | 5 | the filament regions have a higher density of $\sim 10^7$ $\rm cm^{-3}$ and a lower temperature of $\sim 15$–$20$ K |
| Filament-region kinetic temperature | 15-20 | not stated | K | 5 | the filament regions have a higher density of $\sim 10^7$ $\rm cm^{-3}$ and a lower temperature of $\sim 15$–$20$ K |
| 3-2/1-0 ratio, filament vs non-filament | ~1.0 vs ~2.2 | not stated | dimensionless | 5 | The typical line ratio in the filament regions is $\sim 1.0$ even in the eastern part of OMC1, while that of the non-filament region is $\sim 2.2$. |
| Velocity gradient core 8 / core 4 | 17.2 / -11.3 | not stated | km/s/pc | 7 | core 8 and core 4 have $\nabla V = 17.2$ $\rm km\ s^{-1}\ pc^{-1}$ and $\nabla V = -11.3$ $\rm km\ s^{-1}\ pc^{-1}$, respectively |
| beta_rot core 8 | 0.04-0.11 | not stated | dimensionless | 7 | core 8 has $\beta_{\rm rot}$ ranging from 0.04 to 0.11, and core 4 has $\beta_{\rm rot}$ ranging from 0.02 to 0.06 |
| Purely thermal critical line mass (20 K) | 38.4 | not stated | Msun/pc | 6 | In the case of the purely thermally-supported filament, $\rm M_{crit} = 38.4\ M_\odot\ pc^{-1}$. |

## Qualitative findings

- OMC1 splits into northern, western and southern velocity regions with sharp transitions; velocity pattern consistent with global collapse toward the Orion Nebula Cluster  
  > "The observed velocity pattern suggests that dense gas in OMC1 is collapsing globally toward the high-mass star-forming region, Orion Nebula Cluster." (abstract)

## Claim tuples

- H: Do OMC1 filaments have different physical conditions than surrounding gas? | E: RADEX non-LTE using N2H+ 3-2 and 1-0 intensities and ratio | R: Filaments ~1e7 cm^-3, 15-20 K; non-filament lower density and hotter | F: Filaments are shielded from external heating; the east of OMC1 is heated by M42/M43 stars | **supported**
- H: Is core formation ongoing in the filaments? | E: Intensity and velocity along filament major axes with sinusoidal fits | R: Intensity-velocity peak shifts in east filament cores 8 and 4, none in main filament | F: East filament is at an earlier evolutionary stage than the main filament | **partially**
- H: Is OMC1 dense gas collapsing globally? | E: Velocity maps and hyperfine-fit centroid velocities vs RA and Dec | R: Three sub-regions with sharp transitions and a north-to-south gradient from west to south | F: Global inflow toward the Orion Nebula Cluster | **supported**

## Reasoning

- Why this data: _not stated_
- Why this method: Non-LTE used because LTE hyperfine fits fail to constrain Tex and tau and mispredict satellites  
  > "Therefore, we conduct non-LTE analysis in Section [4.3](#subsec::non-lte) to derive the physical conditions." (Hyperfine Spectral Fitting)
- Alternative: Masses from N2H+ column density rejected because abundance and inclination are uncertain  
  > "We adopted this method instead of using the column density of N$_2$H$^+$ because the fractional abundance of N$_2$H$^+$ is highly uncertain" (N_2H^+ RADEX Non-LTE Modeling)
- How they decided it was enough: _not stated_
- Limitation (authors): Line masses may be overestimated under uniform density; 3-2 hyperfine complexity adds linewidth uncertainty  
  > "the $\rm M_{lin}$ derived under our assumption of uniform density inside the filaments (excluding the cores) might be overestimated if the filaments have radial density profiles" (Filament and Core Properties)
- Caveat (inferred, ours): Non-LTE solutions are degenerate (two solutions) and not formally fit with uncertainties
- Caveat (inferred, ours): Mass estimates depend on assumed densities chosen from discrete grid
- Caveat (inferred, ours): Only a single N2H+ pair; no independent temperature tracer
- Caveat (inferred, ours): ALMA data are a secondary input from a previous paper

## Reproducibility

- Data public (paper): ALMA+IRAM 1-0 cube hosted at a Dataverse DOI  
  > "<https://doi.org/10.7910/DVN/DBZUOP>" (footnote 3)
- Products in archive: _not stated_
- Missing: SMA and SMT raw/reduced 3-2 cubes not stated as public
- Missing: Detailed RADEX inputs and region selection masks
- Data volume (inferred): <10 GB for the public 1-0 cube; SMA/SMT data small
- Score (inferred): 3/5, Clear analysis recipe and public 1-0 cube, but the key 3-2 SMA/SMT data are not stated as public and ALMA's role is secondary.
- Rediscovery candidate: no, The 3-2 data are not stated as public and non-LTE matching is not fully specified.

## Links

- Method: Hacar et al. 2018 (cite: omc1_alma) (Source of ALMA+IRAM 1-0 data and filament identification comparison)
- Method: Koch & Rosolowsky 2015 (cite: filfinder) (FilFinder algorithm)
- Companion: Hacar et al. 2017 (cite: hacar_2017) (Observational details of the 1-0 data and velocity structure)
- Related: Orion A ALMA+IRAM 30m N2H+ 1-0 mosaic (Hacar et al. 2018)
- Related: BISTRO survey (JCMT)

## Checks

```json
{
 "quotes": 71,
 "quotes_ok": 71,
 "quote_pass_rate": 1.0,
 "quotes_too_long": 0,
 "unsupported_facts": 0,
 "project_codes": 0,
 "codes_not_in_text": [],
 "codes_not_in_obscore": [],
 "obscore_codes_not_in_card": [
  "2015.1.00669.S"
 ],
 "codes_printed_but_missing": [],
 "numeric_results": 9,
 "numeric_problems": 0,
 "fill": {
  "facts": 85,
  "stated": 51,
  "rate": 0.6
 },
 "evidence_ok": true
}
```
