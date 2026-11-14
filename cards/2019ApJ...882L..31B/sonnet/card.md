# The First Detection of <SUP>13</SUP>C<SUP>17</SUP>O in a Protoplanetary Disk: A Robust Tracer of Disk Gas Mass

`2019ApJ...882L..31B` | The Astrophysical Journal Letters 2019 | first author: Booth, Alice S. | arXiv: 1908.05045 | DOI: 10.3847/2041-8213/ab3645

Card schema 1.0 | model claude-sonnet-5-5 | depth full | type observational_alma_primary

## Science

- Fields: protoplanetary_disks
- Question: Can the rarest CO isotopologue (13C17O) be detected in the HD 163296 disk and used as an optically thin tracer to constrain the disk CO gas mass?  
  > "We present the first detection of in a protoplanetary disk providing a strong constraint on the CO gas mass in the HD 163296 disk." (Introduction)
- Target **HD 163296**: coordinates _not stated_; z/distance 122 pc (Gaia DR2: 101.5 pc)  
  > "All data plotted assumes a source distance of 122 pc (cite: 1998A&A...330..145V)." (Observations); "Although gaia DR2 puts this source at 101.5 pc (cite: 2018A&A...616A...1G)" (Observations); distance from van den Ancker et al. 1998 (Gaia DR2 as alternative)  
  > "All data plotted assumes a source distance of 122 pc (cite: 1998A&A...330..145V)." (Observations); "Although gaia DR2 puts this source at 101.5 pc (cite: 2018A&A...616A...1G)" (Observations)

## Data provenance

- ALMA projects: 2015.1.01259.S, 2011.0.00010.SV, 2013.1.00601.S
- bands: Band 7  
  > "HD 163296 was observed with ALMA in Band 7 during Cycle 3 on 2016 September 16" (Observations)
- frequencies and spectral setup: spectral window resolution 1953.125 kHz; J=3-2 hyperfine lines at 321.851-321.852 GHz blended  
  > "The spectral windows have a resolution of 1953.125 kHz." (Observations); "There are 14 J=3-2 hyperfine structure lines that lie between 321.851 and 321.852 GHz." (Observations)
- continuum bandwidth: _not stated_
- arrays: _not stated_
- configurations: _not stated_
- baselines: _not stated_
- angular resolution: 0.87'' x 0.51'' synthesised beam (with 0.5'' uv taper)  
  > "a $uv$ taper of 0.5$''$ resulting in a synthesised beam of 0.87$''$ x 0.51$''$ (100)." (Observations)
- max recoverable scale: _not stated_
- sensitivity: _not stated_
- time on source: _not stated_
- observing dates: 2016 September 16  
  > "HD 163296 was observed with ALMA in Band 7 during Cycle 3 on 2016 September 16" (Observations)
- pi or archival as stated: PI S. Notsu (2015.1.01259.S); archival data for other isotopologues and ALMA Science Verification  
  > "We also use archival data to benchmark our modelling" (Observations)
- Line: 13C17O J=3-2 (321.851-321.852 GHz (14 hyperfine lines blended))
- Other facility **Archival ALMA/SV data**: Other CO isotopologue lines (J=2-1 from Isella et al. 2016, J=3-2 SV data) used to benchmark model  
  > "including the , , J=2-1 transitions observed from (cite: 2016PhRvL.117y1101I), and the J=3-2 ALMA Science Verification data." (Observations)
- External data: Disk model (density, temperature, CO abundance) fitting multiple CO isotopologues  
  > "we utilise an existing disk model that has been shown to fit emission lines from multiple CO isotopologues" (Analysis) [from (cite: 2011ApJ...740...84Q)]
- External data: Molecular data for the 13C17O hyperfine lines  
  > "The molecular data we use is from (cite: Klapper_2003) and was accessed via the Cologne Database for Molecular Spectroscopy (cite: 2005JMoSt.742..215M)." (Observations) [from (cite: Klapper_2003); (cite: 2005JMoSt.742..215M)]
- External data: Dust mass used to derive g/d  
  > "using the dust mass from (cite: 2007A&A...469..213I) we find a g/d $\approx$ 260" (5.1 Comparison to other mass estimates) [from (cite: 2007A&A...469..213I)]
- External data: Stellar age and accretion rate  
  > "HD 163296 has an estimated age of $6.03^{+0.43}_{-0.14}$ Myr and $\log \dot{M} = -6.81^{+0.16}_{-0.15}$ M$_{\odot}$ yr$^{-1}$ (Wichittanakom et al., in prep.)" (5.4 Is the disk gravitationally stable?) [from Wichittanakom et al., in prep.]

## Processing

### Calibration

- pipeline or manual: _not stated_
- casa version: CASA 4.6.0 (imaging)  
  > "The line imaging was conducted using CLEAN with CASA version 4.6.0." (Observations)
- pipeline version: _not stated_
- archive products used as is: _not stated_
- flux calibrator: _not stated_
- flux scale uncertainty: _not stated_
- self calibration: see Notsu et al. 2019 for calibration and self-calibration  
  > "See (cite: 2019ApJ...875...96N) for details on the calibration and self-calibration of the data." (Observations)

### Imaging

- task: CLEAN in CASA 4.6.0  
  > "The line imaging was conducted using CLEAN with CASA version 4.6.0." (Observations)
- deconvolver: _not stated_
- weighting robust: _not stated_
- uv taper: 0.5''  
  > "a $uv$ taper of 0.5$''$ resulting in a synthesised beam of 0.87$''$ x 0.51$''$ (100)." (Observations)
- cell size: _not stated_
- image size: _not stated_
- masking: _not stated_
- multiscale scales: _not stated_
- continuum subtraction: _not stated_
- line free channels: _not stated_
- primary beam correction: _not stated_
- array combination: _not stated_
- smoothing: 3 km/s channel width (native 1.8 km/s)  
  > "the final images were generated with a 3 $\mathrm{km~s^{-1}}$ channel width" (Observations)
- final beam: 0.87'' x 0.51''  
  > "resulting in a synthesised beam of 0.87$''$ x 0.51$''$ (100)." (Observations)
- final rms: 0.08 Jy/beam km/s (integrated intensity map)  
  > "with an rms noise level of 0.08 $\mathrm{Jy~beam^{-1}~km~s^{-1}}$ (S/N = 7)" (Observations)

### Inherited from earlier work

- Calibration and self-calibration of the Band 7 data  
  > "See (cite: 2019ApJ...875...96N) for details on the calibration and self-calibration of the data." (Observations) [from (cite: 2019ApJ...875...96N)]
- Disk position angle 132 and inclination 42 for the Keplerian mask  
  > "assuming a disk position angle of 132 and an inclination of 42 (cite: 2016PhRvL.117y1101I)" (Observations) [from (cite: 2016PhRvL.117y1101I)]
- CO abundance of 6.0e-5 w.r.t. H2 in the molecular layer and isotope ratios  
  > "shown in Figure 2c, was determined by setting $n(\ce{CO})$ to a constant fractional abundance of $6.0\times10^{-5}$ with respect to in the molecular layer following (cite: 2011ApJ...740...84Q)" (Analysis) [from (cite: 2011ApJ...740...84Q)]
- Optically thin LTE column density method  
  > "Following (cite: 2019A&A...623A.124C) (their Equation 1, with molecular data obtained from CDMS" (Analysis) [from (cite: 2019A&A...623A.124C)]
- Radial profile error estimate  
  > "The errors are the standard deviation of intensity of the pixels in each bin divided by the number of beams per annulus (cite: 2018A&A...614A.106C)." (Observations) [from (cite: 2018A&A...614A.106C)]

### Not stated but needed to reproduce (our reading)

- CLEAN parameters (weighting/robust, masking, threshold, cell/image size, deconvolver)
- Line-free channels and continuum subtraction procedure
- Matched filter details beyond Keplerian mask
- LIME settings (photons, grid, number of channels) and hyperfine LAMDA file
- Exact model gas-to-dust and dust opacity assumptions
- Stellar parameters for Toomre Q calculation (stellar mass, temperature profile details)
- Calibrators and flux scale uncertainty

## Analysis recipe

1. **Detect 13C17O**: Matched filter analysis with a Keplerian mask  
  > "We detected initially via a matched filter analysis[^1] (cite: 2018AJ....155..182L) using a Keplerian mask" (Observations)
   - software: VISIBLE
   - parameter: PA 132, inclination 42, source velocity 5.8 km/s  
  > "assuming a disk position angle of 132 and an inclination of 42 (cite: 2016PhRvL.117y1101I)" (Observations)
   - fitting: _not stated_
   - validation: S/N about 3.5 from matched filter  
  > "The resulting S/N ratio is $\approx 3.5$." (Observations)
2. **Image line and make moment maps**: CLEAN with 3 km/s channels and 0.5'' taper; integrated intensity from channels within ±6 km/s of source velocity; velocity map with 3 sigma clip  
  > "The integrated intensity map was made using channels $\pm~6~\mathrm{km~s^{-1}}$ about the source velocity." (Observations)
   - software: CASA
   - fitting: _not stated_
   - validation: _not stated_
3. **Radial profiles of all isotopologues**: De-project and azimuthally average integrated intensity maps  
  > "All integrated intensity maps were de-projected and azimuthally averaged and are shown in Figures 3a to 3e." (Observations)
   - assumption: distance 122 pc  
  > "All data plotted assumes a source distance of 122 pc (cite: 1998A&A...330..145V)." (Observations)
   - fitting: _not stated_
   - validation: _not stated_
4. **Optically thin LTE column density estimate**: Average column density within 50 au assuming optically thin LTE, compared with C18O  
  > "the average column density for the within 50 au, assuming an excitation temperature of 50 K, is $\mathrm{7.1~\times~10^{15}\mathrm{~cm^{-2}}}$." (Analysis)
   - parameter: Tex = 50 K  
  > "assuming an excitation temperature of 50 K" (Analysis)
   - fitting: _not stated_
   - validation: Ratio 2.5 vs expected factor 100 larger implies C18O optically thick  
  > "Under the assumption that both the lines are optically thin (and taking the previously derived isotopic ratios), this value is a factor of 100 too small." (Analysis)
5. **Radiative transfer modelling and gas mass scaling**: LIME on the Qi et al. 2011 disk model (Model 1), smoothed with IMSMOOTH, then n_H scaled globally in steps of 0.5 from 1.5 to best by-eye fit (Model 2)  
  > "This was done by initially multiplying $n_{\rm H}$ by a factor of 1.5 and then increasing this factor in steps of 0.5 until the best by-eye fit of 3.5 was found." (Analysis)
   - software: LIME, CASA
   - parameter: Model 1 13C17O abundance 5.39e-10 relative to H2; midplane CO depleted by 1e-4 below 19 K; atmosphere by 1e-8  
  > "uses a constant fractional abundance of $5.39~\times~10^{-10}$ relative to ." (Analysis)
   - assumption: interstellar isotope ratios consistent with Qi et al. 2011; fit only beyond 50 au  
  > "therefore we focus on reproducing the data beyond 50 au." (Analysis)
   - fitting: by-eye comparison of radial profiles, no formal fit  
  > "until the best by-eye fit of 3.5 was found." (Analysis)
   - validation: Comparison of Model 2 with all isotopologue radial profiles  
  > "Model 2 provides a better fit to all of the lines." (Analysis)
6. **Optical depth**: Face-on optical depth maps, maximum tau, radially averaged  
  > "We also generated optical depth maps for a face on disk to recover the maximum value of $\mathrm{\tau}$ for each transition." (Analysis)
   - software: LIME
   - fitting: _not stated_
   - validation: _not stated_
7. **Toomre Q stability**: Q = c_s kappa/(pi G Sigma) using model temperature, g/d = 260, Gaia distance mass  
  > "assuming a g/d of 260, and the midplane temperature structure of our model (Figure 2b)" (5.4 Is the disk gravitationally stable?)
   - assumption: constant accretion rate over disk lifetime; all accreted mass once in disk  
  > "we therefore assume that all of the accreted mass once resided in the disk, and that the accretion rate ($\dot{M}$) has been constant over disk lifetime." (5.4 Is the disk gravitationally stable?)
   - fitting: _not stated_
   - validation: _not stated_

## Software

- **CASA** 4.6.0: CLEAN imaging and IMSMOOTH of model cubes  
  > "The line imaging was conducted using CLEAN with CASA version 4.6.0." (Observations)
- **LIME** : Radiative transfer modelling of 13C17O hyperfine lines  
  > "in order to model the J=3-2 hyper-fine components in LIME[^3] (cite: 2010A&A...523A..25B)" (Analysis)
- **VISIBLE** : Matched filter detection  
  > "A python-based open-source implementation of VISIBLE is available at <http://github.com/AstroChem/VISIBLE>" (Observations)
- **CDMS** : Molecular data  
  > "accessed via the Cologne Database for Molecular Spectroscopy (cite: 2005JMoSt.742..215M)" (Observations)

## Numeric results

| quantity | value | uncertainty | units | step | quote |
|---|---|---|---|---|---|
| Peak integrated intensity of 13C17O J=3-2 | 0.55 | rms 0.08 | Jy/beam km/s | 2 | The peak integrated intensity is 0.55 $\mathrm{Jy~beam^{-1}~km~s^{-1}}$ with an rms noise level of 0.08 |
| Required increase in CO gas mass | 3.5 | not stated | dimensionless | 5 | Reconciliation between the observations and the model requires a global increase in CO gas mass by a factor of 3.5. |
| Total disk gas mass (Model 2, 122 pc) | 0.31 | not stated | Msun | 5 | Model 2 has a total disk mass of 0.31 M$_{\odot}$. |
| Disk gas mass at 101.5 pc | 0.21 | not stated | Msun | 5 | the total disk gas mass from our work is thus 0.21 $M_{\odot}$ |
| Gas-to-dust ratio | about 260 | not stated | dimensionless | 5 | we find a g/d $\approx$ 260 |
| Minimum Toomre Q (current) | about 6 at about 110 au | not stated | dimensionless | 7 | We find that the minimum value of Q is $\approx$ 6 at $\approx$ 110 au |
| Disk mass at 0.1 Myr | 1.13 | +0.51/-0.28 | Msun | 7 | we estimate the disk mass at 0.1 Myr to be $1.13_{-0.28}^{+0.51}$ $M_{\odot}$. |
| Column density 13C17O within 50 au | 7.1e15 | not stated | cm^-2 | 4 | is $\mathrm{7.1~\times~10^{15}\mathrm{~cm^{-2}}}$. |

## Qualitative findings

- C18O is optically thick within the CO snowline while 13C17O is optically thin across the disk  
  > "It can be seen that is optically thick within the CO snowline (155 au) in both models, whereas the remains optically thin across the full radial extent of the disk." (Analysis)

## Claim tuples

- H: 13C17O is detectable and traces CO gas mass robustly | E: ALMA Band 7 J=3-2 detection and LIME modelling | R: Detection at S/N=7; model needs 3.5x more gas | F: Disk gas mass is 0.31 Msun, 2-6 times larger than C18O-based estimates | **supported**
- H: Disk is gravitationally stable | E: Toomre Q from new mass | R: Minimum Q about 6; early-time Q 0.7-1.3 | F: Stable now, possibly unstable earlier | **partially**

## Reasoning

- Why this data: Rarest isotopologue expected to be optically thin  
  > "We find that emission is optically thick within the snow line, while the emission is optically thin" (abstract)
- Why this method: _not stated_
- Alternative: Snowline at 90 au (Qi et al. 2015) gives a similar fit but the 155 au model fits slightly better  
  > "was found to be a slightly better fit to the observations." (Analysis)
- How they decided it was enough: _not stated_
- Limitation (authors): Model assumes smooth radial gas density; gas mass is a lower limit due to isotope-selective photodissociation and carbon depletion  
  > "This model assumes a smooth radial gas density structure contrary to the most recent observations." (Analysis); "imply that our gas mass estimate is a lower limit." (5.2 The impact of CO chemistry on the disk mass)
- Caveat (inferred, ours): Detection is only S/N 7 with coarse beam
- Caveat (inferred, ours): By-eye mass scaling with no uncertainties
- Caveat (inferred, ours): Single model structure and fixed temperature
- Caveat (inferred, ours): Mass depends on assumed isotope ratios and distance

## Reproducibility

- Data public (paper): ALMA project codes and SV data listed; archival  
  > "This paper makes use of the following ALMA data: 2011.0.00010.SV, 2013.1.00601.S and 2015.1.01259.S." (Acknowledgements)
- Products in archive: _not stated_
- Code: VISIBLE matched filter code is public  
  > "A python-based open-source implementation of VISIBLE is available at <http://github.com/AstroChem/VISIBLE>" (Observations)
- Missing: Qi et al. 2011 model files and LIME settings
- Missing: Imaging parameters
- Missing: Isella et al. 2016 line data provided privately
- Data volume (inferred): about 10-50 GB
- Score (inferred): 3/5, Data public and recipe outlined, but model details and imaging settings are missing and fitting is by eye.
- Rediscovery candidate: no, Key result depends on a model from earlier work and a by-eye scaling with incomplete settings.

## Links

- Method: (cite: 2018AJ....155..182L) (Matched filter method)
- Method: (cite: 2010A&A...523A..25B) (LIME code)
- Companion: (cite: 2019ApJ...875...96N) (Calibration of the same Band 7 data)
- Companion: (cite: 2011ApJ...740...84Q) (Benchmark disk model)

## Checks

```json
{
 "quotes": 71,
 "quotes_ok": 71,
 "quote_pass_rate": 1.0,
 "quotes_too_long": 0,
 "unsupported_facts": 0,
 "project_codes": 3,
 "codes_not_in_text": [],
 "codes_not_in_obscore": [
  "2013.1.00601.S"
 ],
 "obscore_codes_not_in_card": [],
 "codes_printed_but_missing": [],
 "numeric_results": 8,
 "numeric_problems": 0,
 "fill": {
  "facts": 88,
  "stated": 52,
  "rate": 0.591
 },
 "evidence_ok": true
}
```
