# Gas Kinematics of the Massive Protocluster G286.21+0.17 Revealed by ALMA

`2020ApJ...894...87C` | The Astrophysical Journal 2020 | first author: Cheng, Yu | arXiv: 2005.08197 | DOI: 10.3847/1538-4357/ab879f

Card schema 1.0 | model claude-sonnet-5-5 | depth full | type observational_alma_primary

## Science

- Fields: star_formation, astrochemistry, milky_way_ism
- Question: What are the gas kinematics and dynamical (virial) state of the massive protocluster G286 from clump to dense-core scales, as traced by C18O, N2D+, DCO+ and DCN?  
  > "Here we present a follow-up study of multiple spectral lines to investigate the gas kinematics and dynamics of G286 from clump to core scales." (1 Introduction)
- Target **G286.21+0.17 (G286)**: coordinates RA=10:38:33, Dec=-58:19:22  
  > "The position of field center is R.A.=10:38:33, decl.=-58:19:22." (2.1 ALMA Observations); "associated with the $\eta$ Car giant molecular cloud at a distance of 2.5 $\pm$ 0.3 kpc, in the Carina spiral arm (cite: Barnes10)" (1 Introduction); z/distance 2.5 ± 0.3 kpc  
  > "The position of field center is R.A.=10:38:33, decl.=-58:19:22." (2.1 ALMA Observations); "associated with the $\eta$ Car giant molecular cloud at a distance of 2.5 $\pm$ 0.3 kpc, in the Carina spiral arm (cite: Barnes10)" (1 Introduction); distance from Barnes10  
  > "The position of field center is R.A.=10:38:33, decl.=-58:19:22." (2.1 ALMA Observations); "associated with the $\eta$ Car giant molecular cloud at a distance of 2.5 $\pm$ 0.3 kpc, in the Carina spiral arm (cite: Barnes10)" (1 Introduction)

## Data provenance

- ALMA projects: 2015.1.00357.S
- bands: _not stated_
- frequencies and spectral setup: SPW0 N2D+(3-2) 231.32 GHz; SPW2 C18O(2-1) 219.56 GHz; SPW1 continuum 231.00 GHz (2.0 GHz bandwidth); SPW3 215.85-217.54 GHz  
  > "The frequency coverage for SPW3 ranges from 215.85 to $217.54\:$GHz to observe DCN(3-2), DCO$^+$(3-2), SiO($v=0$)(5-4) and $\rm{CH_3OH}(5_{1,4}-4_{2,2})$." (2.1 ALMA Observations)
- continuum bandwidth: 2.0 GHz total at 231.00 GHz (1.30 mm)  
  > "The second baseband SPW1 was set to $231.00\:$GHz, i.e., 1.30 mm, to observe the continuum with a total bandwidth of $2.0\:$GHz" (2.1 ALMA Observations)
- arrays: 12-m (C36-1), 7-m ACA, and Total Power  
  > "Total power (TP) observations were also carried out to recover the total flux (of line emission), which gives a resolution of about 30$''$." (2.1 ALMA Observations)
- configurations: C36-1 compact configuration  
  > "We employed the compact configuration C36-1 to recover scales between 1.5$''$ and 11.0$''$." (2.1 ALMA Observations)
- baselines: _not stated_
- angular resolution: 7-m: 7.32x4.42 arcsec; 12m+7m: 1.62x1.41 arcsec; TP ~30 arcsec  
  > "which yields a resolution of $7.32\ensuremath{''}\times4.42\ensuremath{''}\:$" (2.1 ALMA Observations); "which results in $1.62\ensuremath{''}\times1.41\ensuremath{''}\:$ resolution" (2.1 ALMA Observations)
- max recoverable scale: 12-m: 1.5-11.0 arcsec; ACA up to 18.6 arcsec  
  > "This is complemented by observations with the ACA array, which probes scales up to 18.6$''$." (2.1 ALMA Observations)
- sensitivity: 30 mJy/beam per 0.1 km/s (N2D+, C18O); 45 mJy/beam per 0.1 km/s (DCO+, DCN, SiO, CH3OH)  
  > "Our sensitivity level is about 30 mJy per beam per 0.1 km/s for $\rm{N_2D^+}$ and $\rm{C^{18}O}$." (2.1 ALMA Observations)
- time on source: _not stated_
- observing dates: Dec. 2015 to Sept. 2016 (Cycle 3)  
  > "during a period from Dec. 2015 to Sept. 2016" (2.1 ALMA Observations)
- pi or archival as stated: PI: J. C. Tan; data also used in Cheng18  
  > "Project ID 2015.1.00357.S, PI: J. C. Tan" (2.1 ALMA Observations)
- Line: C18O 2-1 (219.56 GHz)
- Line: N2D+ 3-2 (231.32 GHz)
- Line: DCO+ 3-2 (not stated)
- Line: DCN 3-2 (not stated)
- Other facility **Herschel (Hi-GAL)**: PACS 70/160 um and SPIRE 250/350/500 um images for SED-derived mass surface density  
  > "The FIR dust continuum images of G286 were taken from *Herschel* Infrared GALactic plane survey (cite: Molinari10; Molinari16)." (2.2 Herschel Observations)
- External data: Core sample (dendrogram, 76 cores) and core masses/dust properties from the earlier ALMA CMF study  
  > "Here we adopt the fiducial dendrogram identified core sample with a base threshold of 4$\sigma$, a delta threshold of 1$\sigma$" (5.1 Review of the core sample) [from (cite: Cheng18)]
- External data: N2D+ hyperfine relative frequencies and optical depths  
  > "with the relative frequencies and optical depths for $\rm N_2D^+$ taken from (cite: Dore04) and (cite: Pagani09)" (5.2 Spectral fitting) [from (cite: Dore04); (cite: Pagani09)]
- External data: Distance 2.5 kpc  
  > "at a distance of 2.5 $\pm$ 0.3 kpc, in the Carina spiral arm (cite: Barnes10)" (1 Introduction) [from (cite: Barnes10)]
- External data: Stellar mass ~240 Msun in similar region  
  > "(cite: Andersen17) estimated a total current stellar mass of $\sim 240 M_\odot$ in a similarly sized region" (5.6 Core to core velocity dispersion) [from (cite: Andersen17)]

## Processing

### Calibration

- pipeline or manual: ALMA data reduction pipeline  
  > "The raw data were calibrated with the data reduction pipeline using *Casa* 4.7.0." (2.1 ALMA Observations)
- casa version: CASA 4.7.0  
  > "The raw data were calibrated with the data reduction pipeline using *Casa* 4.7.0." (2.1 ALMA Observations)
- pipeline version: _not stated_
- archive products used as is: _not stated_
- flux calibrator: _not stated_
- flux scale uncertainty: _not stated_
- self calibration: _not stated_

### Imaging

- task: tclean in CASA; all five strips combined into mosaic  
  > "We performed imaging with *tclean* task in *Casa* and during cleaning we combined data for all five strips to generate a final mosaic map." (2.1 ALMA Observations)
- deconvolver: _not stated_
- weighting robust: Briggs, robust = 0.5  
  > "The 7-m array data was imaged using a Briggs weighting scheme with a robust parameter of 0.5" (2.1 ALMA Observations)
- uv taper: 0.6 arcsec uvtaper for combined data  
  > "we also apply a 0.6$''$  *uvtaper* to suppress longer baselines" (2.1 ALMA Observations)
- cell size: _not stated_
- image size: _not stated_
- masking: _not stated_
- multiscale scales: _not stated_
- continuum subtraction: Continuum constructed from all line-free channels  
  > "The continuum visibility data were constructed with all line-free channels." (2.1 ALMA Observations)
- line free channels: _not stated_
- primary beam correction: _not stated_
- array combination: Two image sets: TP+7m, and TP+7m+12m; feathered with TP  
  > "Both image sets are then feathered with the total power image to correct for the missing large scale structures." (2.1 ALMA Observations)
- smoothing: _not stated_
- final beam: 7.32x4.42 arcsec (7m); 1.62x1.41 arcsec (combined)  
  > "which results in $1.62\ensuremath{''}\times1.41\ensuremath{''}\:$ resolution" (2.1 ALMA Observations)
- final rms: _not stated_

### Inherited from earlier work

- Further observational details  
  > "More details of the observations can be found in (cite: Cheng18)." (2.1 ALMA Observations) [from (cite: Cheng18)]
- Herschel pixel-by-pixel graybody SED fitting for mass surface density  
  > "We performed pixel by pixel graybody fits to derive the mass surface density ($\Sigma$) of the G286 region, following the procedures in (cite: Lim16)." (2.2 Herschel Observations) [from (cite: Lim16)]
- 1.3 mm mass with T=20 K and dust properties  
  > "assuming a temperature of 20 K and other dust properties following (cite: Cheng18)" (4 Filamentary Virial Analysis) [from (cite: Cheng18)]
- Filamentary virial analysis  
  > "Here we perform a filamentary virial analysis following (cite: Fiege00)." (4 Filamentary Virial Analysis) [from (cite: Fiege00)]
- Virial parameter definition and a=5/4 for k_rho=1.5  
  > "We adopt a fiducial value of $k_\rho=1.5$ and $a=5/4$, following (cite: Mckee03)." (5.5 Virial state of dense cores) [from (cite: Bertoldi92); (cite: Mckee03)]

### Not stated but needed to reproduce (our reading)

- CLEAN threshold, niter, masking, cell and image size, multiscale settings
- Line-free channels used for continuum
- Flux calibrator and flux-scale uncertainty
- Feathering procedure parameters
- Velocity channel width of final cubes and spectral smoothing
- Aperture/pixel selection used for core-averaged spectra
- Initial guesses and bounds for Gaussian and hyperfine fits
- Rest frequencies for DCO+ and DCN
- Details of Herschel SED fit (opacity law, dust-to-gas ratio, temperature)
- Core masses/areas come from Cheng18 pipeline; dendrogram code not named

## Analysis recipe

1. **Calibrate and image ALMA data**: Pipeline calibration; tclean mosaic of five strips; 7m and 12m+7m images feathered with TP  
  > "Two sets of images were produced for different aspects of the analysis, one including the TP and 7-m array data and one combining TP, 7-m and 12-m data." (2.1 ALMA Observations)
   - software: CASA, tclean
   - parameter: Briggs robust 0.5; 0.6 arcsec uvtaper for combined  
  > "For the combined data, we used the same Briggs parameter." (2.1 ALMA Observations)
   - fitting: _not stated_
   - validation: _not stated_
2. **Herschel SED mass surface density**: Pixel-by-pixel graybody fits to PACS/SPIRE images; background median between 2 and 4 times ellipse aperture  
  > "The background was estimated as the median intensity value between 2 and 4 times the ellipse aperture shown in [1](#fig:overview)." (2.2 Herschel Observations)
   - fitting: graybody  
  > "We performed pixel by pixel graybody fits to derive the mass surface density ($\Sigma$) of the G286 region" (Herschel Observations)
   - validation: _not stated_
3. **Filament virial analysis of NE-SW filament**: Gaussian fit of C18O spectra in four 60x20 arcsec strips from 7m-only cube; compute m_f/m_vir,f with thermal correction; infall mass estimate from velocity gradient  
  > "We perform gaussian fitting to measure the average centroid velocity $\overline{v}_f$ and velocity dispersion $\sigma_{\rm C^{18}O}$." (4 Filamentary Virial Analysis)
   - parameter: Surface pressure and magnetic terms ignored  
  > "we ignore the surface term and magnetic energy term, i.e., only considering the balance between gravity and internal pressure support." (4 Filamentary Virial Analysis)
   - assumption: Distance 2.5 kpc; inclination 60 deg; T = 20 K; mu_p = 2.33  
  > "we further assume the filament axis is inclined by an angle $i = 60^\circ$ to the line of sight" (4 Filamentary Virial Analysis)
   - fitting: Gaussian fits, two components for strips 1 and 3  
  > "For strips 1 and 3, two Gaussian components are used for a better fitting." (4 Filamentary Virial Analysis)
   - validation: Compared 1.3 mm masses with Herschel masses; compared with DCO+ to pick the associated component  
  > "We find the 1.3 mm-derived mass estimates are about a factor of two smaller than that measured from the *Herschel*-SED fitting method." (4 Filamentary Virial Analysis)
4. **Fit core-averaged spectra**: Average spectra per core; fit spectra with peak >4 sigma using 1-d Gaussians; hyperfine fitting for N2D+  
  > "Here we adopt a 4$\sigma$ criterion for this threshold value." (5.2 Spectral fitting)
   - software: scipy.optimize curve_fit, pyspeckit
   - parameter: rms estimated per core per line from signal-free channels; second Gaussian allowed for 31 C18O cores  
  > "In 31 cores where a spectrum has more complex profiles and hence can not be well approximated by a single gaussian, we allow for a second gaussian component." (5.2 Spectral fitting)
   - fitting: curve_fit Gaussian; pyspeckit hyperfine for N2D+  
  > "we use the hyperfine line fitting routine in *pyspeckit* (cite: Ginsburg11)" (5.2 Spectral fitting)
   - validation: Checked single-pixel spectra at continuum peaks  
  > "We also checked the single pixel spectra at the continuum peak of each core and found that the vast majority have similar line profiles as the averaged spectra" (5.2 Spectral fitting)
5. **Compare tracer velocities and core-envelope offsets**: Median offsets of centroid velocities between tracers; core velocity v_c as uncertainty-weighted mean; compare with C18O component closest to v_c  
  > "we define the core velocity, $v_c$, as an average of the detected centroid velocities, weighted by their measurement uncertainties." (5.4 Line parameters of different tracers)
   - parameter: Sound speed 0.27 km/s at 20 K as threshold  
  > "(0.27 km s$^{-1}$  for 20 K temperature)" (5.4 Line parameters of different tracers)
   - fitting: _not stated_
   - validation: Sampling error of offsets ~0.04 km/s  
  > "The sampling error of the velocity offset distribution due to the finite number of cores is estimated to be about 0.04 km s$^{-1}$" (5.4 Line parameters of different tracers)
6. **Core virial parameters**: alpha = 5 sigma_c^2 R_c/(G M_c) with thermal-corrected dispersion; two radius definitions (dendrogram and deconvolved)  
  > "$$\begin{equation}
 \alpha \equiv 5\sigma_c^2R_c/(GM_{c}) = 2aE_K/|E_G|,
\end{equation}$$" (5.5 Virial state of dense cores)
   - parameter: Deconvolved analysis excludes cores with area <1.5 x A_beam (34 of 76)  
  > "This criterion excludes 34 out of 76 cores." (5.5 Virial state of dense cores)
   - assumption: T=20 K masses; k_rho=1.5, a=5/4; alpha_cr = 2a  
  > "a virial parameter above a critical value $\alpha_{\rm cr}= 2a$ indicates that the core is unbound" (5.5 Virial state of dense cores)
   - fitting: _not stated_
   - validation: Uncertainty budget: ~factor 2.5 absolute; T=15/30 K changes alpha by 0.6/1.9  
  > "we estimate the absolute virial parameter uncertainties to be about a factor of 2.5" (5.5 Virial state of dense cores)
7. **Core-to-core velocity dispersion vs clump virial dispersion**: Standard deviation of core centroid velocities; compare with sigma_cl,vir = sqrt(aGM/5R) and TP C18O Gaussian width; split into blue and red groups  
  > "We then calculate the standard deviation of these distributions" (5.6 Core to core velocity dispersion)
   - parameter: R_cl = 1.54 pc; M ~ 2900 Msun; 50% mass uncertainty  
  > "We choose a size of $R_{\rm cl} = 1.54$ pc" (5.6 Core to core velocity dispersion)
   - assumption: k_rho=1.5, a=5/4; gas mass only  
  > "As with cores, we again adopt $k_\rho=1.5$, so that $a=5/4$." (5.6 Core to core velocity dispersion)
   - fitting: _not stated_
   - validation: Errors are sampling errors only, assuming normal distribution  
  > "The uncertainties here only account for sampling errors due to limited sample size, assuming the data points are drawn from a normal distribution." (5.6 Core to core velocity dispersion)

## Software

- **CASA** 4.7.0: Pipeline calibration and tclean imaging  
  > "The raw data were calibrated with the data reduction pipeline using *Casa* 4.7.0." (2.1 ALMA Observations)
- **scipy.optimize curve_fit** : 1-d Gaussian fits to spectra  
  > "using the *curve_fit* function in the *Scipy.optimize* python module" (5.2 Spectral fitting)
- **pyspeckit** : N2D+ hyperfine fitting  
  > "we use the hyperfine line fitting routine in *pyspeckit* (cite: Ginsburg11)" (5.2 Spectral fitting)
- **Dendrogram** : Core identification and areas  
  > "we adopt the core area returned by *Dendrogram*" (5.1 Review of the core sample)

## Numeric results

| quantity | value | uncertainty | units | step | quote |
|---|---|---|---|---|---|
| Number of continuum-defined cores | 76 | not stated | cores | 0 | This parameter combination yields 76 cores. |
| Filament m_f/m_vir,f range over four strips | 0.60 to 2.39 | ~50% systematic | dimensionless | 3 | The values of $m_f/m_{\rm vir,f}$ of the four strips range from 0.60 to 2.39. |
| Filament velocity gradient (plane of sky) | 2.84 | not stated | km/s/pc | 3 | which corresponds to an overall velocity gradient of $2.84\:{\rm
  km\:s^{-1}\:pc}^{-1}$ using plane-of-sky projected distance |
| Dynamical mass from filament infall (i=60 deg) | 1410 | not stated | Msun | 3 | we thus estimate the dynamical mass to be $1410\:M_\odot$, assuming $i = 60^{\circ}$ |
| Fraction of cores with core-envelope offset below sound speed | 71% | not stated | percent | 5 | The majority of cores (71%) have core and envelope velocity offsets less than the sound speed of the ambient medium |
| Median core-envelope velocity offset | 0.01 (std ~0.3) | not stated | km/s | 5 | The median value of the velocity offset is 0.01 km s$^{-1}$, with a standard deviation of about 0.3 km s$^{-1}$. |
| Median virial parameter (deconvolved radius, averaged tracers) | 1.22 | std 0.88; factor ~2.5 systematic | dimensionless | 6 | we obtain a median value of 1.22, and a standard deviation of 0.88 |
| Core-to-core velocity dispersion (C18O) | 1.27 | 0.11 | km/s | 7 | obtaining 1.27 $\pm$ 0.11 km s$^{-1}$  for the $\rm C^{18}O$-detected sample |
| Clump virial velocity dispersion | 1.42 | 0.36 | km/s | 7 | Thus, $\sigma_{\rm cl,vir}=1.42 \pm 0.36$ km s$^{-1}$ |
| Clump gas velocity dispersion from TP C18O | 1.12 | 0.01 | km/s | 7 | $\sigma_{\rm cl}$ (1.12 $\pm$ 0.01 km s$^{-1}$) |

## Qualitative findings

- DCN concentrated at protocluster center where N2D+ and DCO+ are weak, suggesting a more evolved central region  
  > "$\rm DCN$ is strongly concentrated towards the protocluster center, where no or only weak detection is seen for $\rm N_2D^+$ and $\rm DCO^+$" (abstract)

## Claim tuples

- H: Do dense cores have velocity offsets among different dense gas tracers? | E: Compared fitted centroid velocities for cores detected in multiple lines | R: Median offsets 0.03-0.09 km/s, sampling error 0.04 km/s | F: No significant velocity offsets among tracers | **supported**
- H: Are cores kinematically decoupled from their C18O envelope? | E: Compared core velocity v_c with C18O centroid | R: 71% have offsets below sound speed | F: Cores mostly quiescent relative to envelope | **supported**
- H: Are the dense cores in virial equilibrium? | E: Virial parameters from three tracers | R: Median alpha ~1.2 with factor ~2.5 uncertainty | F: Consistent with virial equilibrium within uncertainties | **partially**
- H: Is the protocluster gas relaxed to virial equilibrium? | E: Compared core-to-core dispersion with virial dispersion and split by velocity groups | R: Total sigma_c-c similar to sigma_vir but bimodal velocity distribution | F: Dense gas not yet relaxed, possibly due to infall | **partially**

## Reasoning

- Why this data: _not stated_
- Why this method: Deuterated species used as better tracers of localized dense cores than extended filaments, less affected by multiple velocity components  
  > "which should be better tracers of localized dense cores, rather than more extended filaments" (5.4 Line parameters of different tracers)
- Alternative: 1.3 mm masses rejected for filament virial analysis because 7m data miss flux; Herschel masses adopted  
  > "so here we adopt the *Herschel*-SED-derived mass estimates for the virial analysis" (4 Filamentary Virial Analysis)
- How they decided it was enough: _not stated_
- Limitation (authors): Large systematic uncertainties in virial parameters (temperature, mass, distance), so supervirial vs subvirial unclear  
  > "given the potentially large systematic uncertainties it is difficult to be more certain about whether the dense cores are actually closer to a supervirial or subvirial state" (5.5 Virial state of dense cores)
- Limitation (authors): Many cores are not well resolved  
  > "indicating many cores are not well resolved" (5.1 Review of the core sample)
- Caveat (inferred, ours): Single assumed temperature of 20 K for all cores affects masses and thermal widths
- Caveat (inferred, ours): Filament inclination of 60 deg unconstrained
- Caveat (inferred, ours): Core spectra averaged over unresolved cores with blended components
- Caveat (inferred, ours): Velocity uncertainties are only sampling errors

## Reproducibility

- Data public (paper): ALMA project ID given; no explicit public statement  
  > "This paper makes use of the following ALMA data: ADS/JAO.ALMA#2015.1.00357.S." (Acknowledgments)
- Products in archive: _not stated_
- Missing: Core catalog positions are in appendix table but dendrogram on the continuum image not scripted
- Missing: Imaging parameters (cell, size, clean threshold)
- Missing: Feathering details
- Missing: Herschel SED fitting parameters
- Data volume (inferred): Large mosaic (147 pointings 12m + ACA + TP); likely hundreds of GB raw
- Score (inferred): 3/5, Data public and core table given, but imaging and spectral extraction details are incomplete and rely on Cheng18.
- Rediscovery candidate: no, Imaging and fitting settings are under-specified and rely on a previous paper.

## Links

- Method: (cite: Fiege00) (Filamentary virial analysis)
- Method: (cite: Lim16) (Herschel SED mass surface density)
- Method: (cite: Bertoldi92) (Virial parameter)
- Companion: (cite: Cheng18) (Earlier ALMA CMF study of G286 using same data)
- Related: Herschel Hi-GAL

## Checks

```json
{
 "quotes": 89,
 "quotes_ok": 89,
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
  "facts": 91,
  "stated": 65,
  "rate": 0.714
 },
 "evidence_ok": true
}
```
