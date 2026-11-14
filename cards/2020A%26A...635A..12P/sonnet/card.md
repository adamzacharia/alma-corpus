# GG Tauri A: gas properties and dynamics from the cavity to the outer disk

`2020A&A...635A..12P` | Astronomy and Astrophysics 2020 | first author: Phuong, N. T. | arXiv: 2001.08147 | DOI: 10.1051/0004-6361/201936173

Card schema 1.0 | model claude-sonnet-5-5 | depth full | type observational_alma_primary

## Science

- Fields: protoplanetary_disks, star_formation
- Question: What are the gas properties (temperature, density, kinematics, mass) in the cavity of the GG Tau A circumbinary disk and, to a lesser extent, in the outer disk?  
  > "in order to determine the gas properties (temperature, density, and kinematics) in the cavity and to a lesser extent in the outer disk." (abstract)
- Target **GG Tau A**: coordinates RA=4h 32m 30.3s, DEC=17d 31' 40'' (epoch 2000, origin of image coordinates)  
  > "Although the GAIA results suggest a value of 150 pc (cite: GAIA_2016; GAIA_2018), we use a distance of 140 pc for comparison with previous works." (1 Introduction); "the origin of the coordinates is at RA=4h 32m 30.3s and DEC=$17^{\circ}\,31'\,40''$ at epoch 2000." (Observations and data reduction); z/distance 140 pc  
  > "Although the GAIA results suggest a value of 150 pc (cite: GAIA_2016; GAIA_2018), we use a distance of 140 pc for comparison with previous works." (1 Introduction); "the origin of the coordinates is at RA=4h 32m 30.3s and DEC=$17^{\circ}\,31'\,40''$ at epoch 2000." (Observations and data reduction); distance from adopted for comparison with previous works (Gaia suggests 150 pc)  
  > "Although the GAIA results suggest a value of 150 pc (cite: GAIA_2016; GAIA_2018), we use a distance of 140 pc for comparison with previous works." (1 Introduction); "the origin of the coordinates is at RA=4h 32m 30.3s and DEC=$17^{\circ}\,31'\,40''$ at epoch 2000." (Observations and data reduction)

## Data provenance

- ALMA projects: 2011.0.00059.S, 2012.1.00129.S, 2015.1.00224.S
- bands: Band 9 (Cycle 0), Band 7 (Cycles 1 and 3)  
  > "GG Tau A was observed with ALMA Band 9 during Cycle 0 (2011.0.00059.S) and Band 7 during Cycle 1 (2012.1.00129.S) and Cycle 3 (2015.1.00224.S)." (Observations and data reduction)
- frequencies and spectral setup: Cycle 3: 13CO(3-2) and C18O(3-2) in two windows of 58.89 MHz, 141 kHz resolution (~0.11 km/s)  
  > "each covering 58.89 MHz bandwidth with a high spectral resolution of 141 kHz ($\sim$0.11 $\,{\rm km\,s}^{-1}$)" (Cycle 3)
- continuum bandwidth: 1875 MHz at 330.15 GHz; 117 MHz at 342.00 GHz  
  > "one centered at 330.15 GHz with 1875 MHz bandwidth and the other centered at 342.00 GHz with 117 MHz bandwidth" (Cycle 3)
- arrays: _not stated_
- configurations: C40-6 (Cycle 3), 37 and 38 useful antennas  
  > "with 37 and 38 useful antennas in configuration C40-6" (Cycle 3)
- baselines: 16 m to 3049 m  
  > "The projected baselines range from 16 m to 3049 m" (Cycle 3)
- angular resolution: 13CO 0.22''x0.16''; C18O 0.19''x0.14''; continuum 0.19''x0.14''  
  > "$0.19''\times0.14''$, PA=$19^\circ$" (Table 1)
- max recoverable scale: ~7'' (1000 au)  
  > "the maximum recoverable scale is about 7$''$ (1000 au at the source distance)" (Observations and data reduction)
- sensitivity: _not stated_
- time on source: 1.4 hours (Cycle 3)  
  > "the total time on source is 1.4 hours" (Cycle 3)
- observing dates: 2012 Aug 13 (C0); 2013 Nov 18-19 (C1); 2016 Sep 25 and 30 (C3)  
  > "Observations were made on 2012 August 13." (Cycle 0); "Observations were carried on 2016 September 25 and 30" (Cycle 3)
- pi or archival as stated: Anne Dutrey is PI of all three projects  
  > "Anne Dutrey is the PI of the three projects." (Observations and data reduction)
- Line: 12CO 6-5 (691.473 GHz)
- Line: 12CO 3-2 (345.795 GHz)
- Line: 13CO 3-2 (330.588 GHz)
- Line: C18O 3-2 (329.330 GHz)
- External data: 12CO(6-5) data (Cycle 0) previously published  
  > "the $^{12}$CO(6–5) data from (cite: Dutrey+DiFolco+Guilloteau_2014)" (5.2 Gas properties) [from (cite: Dutrey+DiFolco+Guilloteau_2014)]
- External data: Dust ring parameters (radii, kappa, temperature) fixed from earlier work  
  > "Fixed values are taken from (cite: Dutrey+DiFolco+Guilloteau_2014)." (Table 2) [from (cite: Dutrey+DiFolco+Guilloteau_2014)]
- External data: 12C/13C = 70  
  > "We assumed the standard isotopic ratios $^{12}$C/$^{13}$C$=70$ (cite: Milam+Savage+Brewster_2005)" (5.2 Gas properties) [from (cite: Milam+Savage+Brewster_2005)]
- External data: 16O/18O = 550  
  > "$^{16}$O/$^{18}$O$=550$ (cite: Wilson_1999)" (5.2 Gas properties) [from (cite: Wilson_1999)]
- External data: CO abundance from TMC-1  
  > "The CO abundance was taken from the abundances measured in TMC-1 by (cite: Ohishi+Irvine+Kaifu_1992)" (5.3 Gas masses) [from (cite: Ohishi+Irvine+Kaifu_1992)]
- External data: Einstein A coefficients from Lamda database  
  > "the Einstein coefficient $A_{ul}$ is taken from Lamda database" (5.3 Gas masses) [from Lamda database]

## Processing

### Calibration

- pipeline or manual: _not stated_
- casa version: CASA 4.7.0 (Cycle 3)  
  > "Data were calibrated with the CASA[^1] software (version 4.7.0)." (Cycle 3)
- pipeline version: _not stated_
- archive products used as is: _not stated_
- flux calibrator: J0522-3627 (~3.84 Jy at 343.5 GHz); J0510+1800 for phase and bandpass  
  > "The absolute amplitude calibration was made using J0522-3627 (flux $\sim$3.84 Jy at 343.5 GHz at the time of observations)." (Cycle 3)
- flux scale uncertainty: additional 10% error on absolute flux scale  
  > "These uncertainty estimates do not take into account an additional 10$\%$ error on the absolute flux scale." (Table 3)
- self calibration: _not stated_

### Imaging

- task: cvel for LSR regridding; export to UVFITS and GILDAS for imaging  
  > "The calibrated data were regrided in velocity to the local standard of rest (LSR) frame using the task cvel, and were exported through UVFITS format to the GILDAS" (Cycle 3)
- deconvolver: Hogbom CLEAN  
  > "the images were cleaned down to the rms noise level with the $hogbom$ algorithm" (Observations and data reduction)
- weighting robust: natural weighting  
  > "The imaging and deconvolution was made with natural weighting" (Observations and data reduction)
- uv taper: _not stated_
- cell size: _not stated_
- image size: _not stated_
- masking: _not stated_
- multiscale scales: _not stated_
- continuum subtraction: _not stated_
- line free channels: _not stated_
- primary beam correction: not applied; 12% attenuation at 500 au, 4% at 300 au  
  > "The images were not corrected for primary beam attenuation: the beam size of 17$''$ yields attenuation of 12% at 500 au and 4% at 300 au." (Observations and data reduction)
- array combination: _not stated_
- smoothing: CO(3-2) and (6-5) smoothed to 0.35''x0.30'' for blob analysis  
  > "smoothed to a similar angular resolution ($0.35''\times0.30''$)" (5.2 Gas properties)
- final beam: 13CO 0.22''x0.16'' PA 15; C18O 0.19''x0.14'' PA 19  
  > "$0.22''\times0.16''$, PA=$15^\circ$" (Table 1)
- final rms: _not stated_

### Inherited from earlier work

- Cycle 1 data reduction details  
  > "Details of data reduction are given in (cite: Tang+Dutrey+Guilloteau+etal_2016)." (Cycle 1) [from (cite: Tang+Dutrey+Guilloteau+etal_2016)]
- Deprojection method; PA 7 deg, i 35 deg  
  > "See also (cite: Phuong+Diep+Dutrey_2018) for a detailed description of the deprojection." (3.2.1 Intensity variations) [from (cite: Phuong+Diep+Dutrey_2018)]
- Continuum fit procedure and fixed dust parameters  
  > "We followed the procedure described in (cite: Dutrey+DiFolco+Guilloteau_2014)" (4.3 Continuum fit) [from (cite: Dutrey+DiFolco+Guilloteau_2014)]
- DiskFit model  
  > "We used the DiskFit tool (cite: Pietu+Dutrey+Guilloteau+etal_2007) to derive the bulk properties of the ring and outer disk." (4.2 Disk model) [from (cite: Pietu+Dutrey+Guilloteau+etal_2007)]
- Cycle 0 12CO(6-5) data  
  > "The spectral windows covered the $^{12}$CO(6–5) line (cite: Dutrey+DiFolco+Guilloteau_2014)." (Cycle 0) [from (cite: Dutrey+DiFolco+Guilloteau_2014)]

### Not stated but needed to reproduce (our reading)

- Calibration of Cycle 0 and Cycle 1 data (CASA versions, calibrators) not given
- uv-weighting details and cell/image size for GILDAS imaging
- Procedure for merging Cycle 1 and Cycle 3 13CO data
- Clean mask/threshold and line-free channels for continuum
- Exact DiskFit initial values and iteration details
- Blob definitions beyond table positions; beam-sized region extraction
- Treatment of Aa continuum subtraction in uv tables

## Analysis recipe

1. **Realign data and image**: Fit continuum in uv plane (circular Gaussian for Aa + elliptical ring) to derive proper motion [9,-23] mas/yr, recenter on ring; natural-weighted Hogbom imaging  
  > "The apparent motion of the ring gives a proper motion of $[9,-23]$ mas per year, which we applied to all our data set." (Observations and data reduction)
   - software: CASA, GILDAS
   - assumption: Ring centered on center of mass of system  
  > "we assumed that the continuum ring is centered on the center of mass of the system" (Observations and data reduction)
   - fitting: _not stated_
   - validation: _not stated_
2. **Outer disk rotation velocity**: Deprojected intensity-weighted Vz/(sin i sin w), azimuthally averaged in 0.15'' bins with |sin w|>0.7; constant fit to V_rot r^0.5  
  > "We then azimuthally averaged these values for all pixels at the same radius (using a $0.15''$ radial binning) such that $|\sin\omega|$ to $> 0.7$" (3.2.2 CO gas kinematics in the outer disk)
   - assumption: Infall neglected in outer disk; i=35 deg  
  > "We can neglect the infall motions" (3.2.2 CO gas kinematics in the outer disk)
   - fitting: Constant fit; std dev of residuals used as error  
  > "We therefore conservatively used the standard deviation as the error on the mean." (3.2.2 CO gas kinematics in the outer disk)
   - validation: Compared with earlier value 3.4±0.1 km/s at 100 au  
  > "in agreement with previous, less precise determinations" (3.2.2 CO gas kinematics in the outer disk)
3. **Fit ring and outer disk model**: DiskFit uv-plane fit with piece-wise power laws; knots at 160,200,260,300,400 au; Clean components inside 160 au subtracted first; 12CO fit for T, 13CO/C18O for surface density, iterated twice  
  > "We used knots at 160, 200, 260, 300 and 400 au." (4.4 CO isotopologs)
   - software: DiskFit
   - parameter: inner radius 169 au; scale height 24 au at 200 au; V0=3.37 km/s; dV=0.3 km/s  
  > "A fixed inner radius of 169 au provided a good compromise to represent all molecular distributions." (4.4 CO isotopologs)
   - assumption: LTE; 12CO and 13CO layers at same temperature; CO = 70 x 13CO  
  > "Our method makes the underlying assumption that the ${^{12}{\rm CO}}$ and ${^{13}{\rm CO}}$ layers are at the same temperature." (4.4 CO isotopologs)
   - fitting: Levenberg-Marquardt chi2 minimization, errors from covariance matrix  
  > "The difference between the predicted model visibilities and the observed ones is minimized using a Levenberg–Marquardt method" (4.2 Disk model)
   - validation: Geometric parameters verified by free fits; confidence intervals from dispersion of minimizations  
  > "We therefore also quote a confidence interval for the temperatures in Table [3]" (4.4 CO isotopologs)
4. **Cavity residual imaging and dynamics**: Subtract best ring+disk model from visibilities, CLEAN residuals; fit sine plus infall term to <Vz/sin i> in five 0.25'' rings  
  > "a better fit to the observed velocities is obtained by taking into account the contribution of a radial (from the disk center) velocity" (5.1 Dynamics inside the cavity)
   - software: GILDAS
   - fitting: Vz/sin i = Vfall cos w + Vrot sin w  
  > "$V_z/\sin(i)=V_{fall}\cos\omega + V_{rot}\sin\omega$" (5.1 Dynamics inside the cavity)
   - validation: PV diagrams along major and minor axes show N-S asymmetry consistent with infall  
  > "The PV diagram along the minor axis shows an asymmetry between the north and the south" (5.1 Dynamics inside the cavity)
5. **Non-LTE analysis of blobs**: Escape-probability non-LTE chi2 grid over n(H2) 1e2-1e10, N(CO) 1e13-1e19, Tkin 3-100 K, 50 steps each, using CO 6-5, 3-2, 13CO, C18O  
  > "for ranges of H$_2$ density of $10^2-10^{10}$ cm$^{-3}$, ${^{12}{\rm CO}}$ column density of $10^{13}-10^{19}$ cm$^{-2}$, and kinetic temperature of $3-100$ K using 50 steps of each parameter" (5.2 Gas properties)
   - software: DiskFit
   - assumption: Single collision partner H2, Gaussian profiles, 12C/13C=70, 16O/18O=550  
  > "a single collision partner, H$_2$, and Gaussian line profiles" (5.2 Gas properties)
   - fitting: chi2 surface sampling  
  > "Non-LTE best-fit solutions were found by sampling the $\chi^2$ surface" (5.2 Gas properties)
   - validation: _not stated_
6. **Gas masses in cavity**: Optically thin integrated flux of 13CO and C18O within 160 au, T=40 K, CO abundance from TMC-1  
  > "we assumed that the gas temperature $T$ is 40 K everywhere inside the cavity" (5.3 Gas masses)
   - assumption: T=40 K; X[CO]=8.0e-5 relative to H2; isotope ratios 70 and 550  
  > "X\[${^{13}{\rm CO}}$\]=X\[${^{12}{\rm CO}}$\]/70" (Table 5)
   - fitting: _not stated_
   - validation: 13CO and C18O masses agree, confirming optical thinness  
  > "The H$_2$ mass derived from ${^{13}{\rm CO}}$(3–2) and C$^{18}$O(3–2) is similar which confirms that these lines are optically thin" (5.3 Gas masses)

## Software

- **CASA** 4.7.0: Calibration of Cycle 3 data; cvel  
  > "Data were calibrated with the CASA[^1] software (version 4.7.0)." (Cycle 3)
- **GILDAS** : Further processing, imaging  
  > "were exported through UVFITS format to the GILDAS[^2] package for further data processing" (Cycle 3)
- **DiskFit** : Disk model fitting in uv plane and non-LTE escape probability  
  > "We used the DiskFit tool (cite: Pietu+Dutrey+Guilloteau+etal_2007) to derive the bulk properties of the ring and outer disk." (4.2 Disk model)

## Numeric results

| quantity | value | uncertainty | units | step | quote |
|---|---|---|---|---|---|
| Keplerian rotation speed at 1'' | 2.94 | 0.03 | km/s | 2 | we derive a mean weighted value of $2.94\pm0.03\,{\rm km\,s}^{-1}$ for the Keplerian rotation speed at $1''$ |
| Total stellar mass | 1.36 | 0.07 | Msun | 2 | this corresponds to a total stellar mass of $1.36 \pm 0.07{\,\rm M}_{\odot}$ |
| Gas temperature from 12CO at 400 au | 10.7 | [10,12] K | K | 3 | / 400   / $10.7$ / $0.02$ / \[10,12\] / |
| Infall velocity in cavity | ~0.3 | not stated | km/s | 4 | the gas in the cavity moves inwards to the center at velocities about $0.3\,\,{\rm km\,s}^{-1}$ |
| Total H2 mass in cavity (13CO) | 1.6e-4 | 0.1e-4 | Msun | 6 | $1.6\pm0.1\times10^{-4}$ |
| Mass accretion rate through cavity | 6.4e-8 | not stated | Msun/yr | 6 | This gives an accretion rate of $\sim6.4\times10^{-8}\,\mathrm{M}_\odot\,\rm{yr}^{-1}$ |
| Blob kinetic temperatures | 40-80 | ±5 to ±10 | K | 5 | temperatures in the range 40–80 K |

## Qualitative findings

- Ring and outer disk are non-smooth, with unresolved substructures and azimuthal variations  
  > "The ring and outer disks do not exhibit a smooth distribution, but likely consist of a series of unresolved substructures" (7 Summary)

## Claim tuples

- H: Is the outer disk cold? | E: Fit 12CO(3-2) with broken power-law DiskFit model | R: T drops from ~27 K at 180 au to 11 K at 400 au, ~r^-1 | F: Outer disk is cold, below 20 K beyond 250 au | **supported**
- H: Does gas in the cavity move inward? | E: Fit azimuthal velocity variation in residual cavity maps | R: Vfall ~0.3 km/s, 10-15% of Keplerian | F: Infall exists feeding inner disks | **supported**
- H: Does cavity accretion sustain the disks? | E: Cavity mass / infall timescale compared to Halpha accretion rate | R: 6.4e-8 vs 2e-8 Msun/yr | F: Mass flow comparable to or higher than stellar accretion | **supported**

## Reasoning

- Why this data: _not stated_
- Why this method: _not stated_
- How they decided it was enough: _not stated_
- Limitation (authors): Formal errors underestimate uncertainties; significant deviations from smooth model; sub-Keplerian rotation in cavity may be resolution artifact  
  > "The formal errors underestimate the uncertainties on the physical parameters." (4.4 CO isotopologs)
- Caveat (inferred, ours): Gas mass relies on assumed TMC-1 CO abundance and fixed T=40 K
- Caveat (inferred, ours): Infall derived from beam-smoothed intensity-weighted velocities with inhomogeneous brightness
- Caveat (inferred, ours): Distance 140 pc vs Gaia 150 pc
- Caveat (inferred, ours): Smooth-model subtraction may bias residual cavity emission

## Reproducibility

- Data public (paper): _not stated_
- Products in archive: _not stated_
- Missing: Cycle 0/1 calibration details
- Missing: DiskFit availability/version and starting parameters
- Missing: Blob extraction details
- Data volume (inferred): ~50-150 GB for three projects
- Score (inferred): 4/5, Data are identifiable and many parameters given, but DiskFit and GILDAS workflow plus earlier-paper reductions are needed.
- Rediscovery candidate: no, Key results depend on a custom DiskFit workflow and inherited choices not fully specified.

## Links

- Method: (cite: Pietu+Dutrey+Guilloteau+etal_2007) (DiskFit model)
- Method: (cite: Phuong+Diep+Dutrey_2018) (deprojection)
- Companion: (cite: Dutrey+DiFolco+Guilloteau_2014) (CO(6-5) data, dust ring parameters)
- Companion: (cite: Tang+Dutrey+Guilloteau+etal_2016) (Cycle 1 data reduction)

## Checks

```json
{
 "quotes": 81,
 "quotes_ok": 81,
 "quote_pass_rate": 1.0,
 "quotes_too_long": 0,
 "unsupported_facts": 0,
 "project_codes": 3,
 "codes_not_in_text": [],
 "codes_not_in_obscore": [],
 "obscore_codes_not_in_card": [],
 "codes_printed_but_missing": [
  "2011.1.00059.S"
 ],
 "numeric_results": 7,
 "numeric_problems": 0,
 "fill": {
  "facts": 83,
  "stated": 59,
  "rate": 0.711
 },
 "evidence_ok": true
}
```
