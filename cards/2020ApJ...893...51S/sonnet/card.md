# Disk Structure around the Class I Protostar L1489 IRS Revealed by ALMA: A Warped-disk System

`2020ApJ...893...51S` | The Astrophysical Journal 2020 | first author: Sai, Jinshi | arXiv: 2003.07067 | DOI: 10.3847/1538-4357/ab8065

Card schema 1.0 | model claude-sonnet-5-5 | depth full | type observational_alma_primary

## Science

- Fields: star_formation, protoplanetary_disks
- Question: What are the structure and kinematics of the disk around the Class I protostar L1489 IRS at ~40 au resolution, and is the disk warped?  
  > "To reveal the disk structures in more detail at a scale of tens of au, we have conducted observations at angular resolutions three times higher than the previous observations" (1 Introduction)
- Target **L1489 IRS**: coordinates phase center 4h4m42.85s, +26d18m56.3s (J2000)  
  > "the Class I protostar L1489 IRS in the Taurus molecular cloud, which is one of the nearest star-forming regions to our solar system ($d\sim$140 pc)" (1 Introduction); z/distance ~140 pc  
  > "the Class I protostar L1489 IRS in the Taurus molecular cloud, which is one of the nearest star-forming regions to our solar system ($d\sim$140 pc)" (1 Introduction); distance from _not stated_

## Data provenance

- ALMA projects: 2013.1.01086.S
- bands: Band 6 (1.3 mm), Cycle 2  
  > "We have observed L1489 IRS with ALMA in Band 6 during its Cycle 2 phase." (2 Observations)
- frequencies and spectral setup: _not stated_
- continuum bandwidth: 2 GHz at 234.000 GHz  
  > "Velocity resolution (lines) / Band width (continuum) | $0.17 \kmps$ | $0.17 \kmps$ | 2 GHz" (Table 1)
- arrays: _not stated_
- configurations: _not stated_
- baselines: 20.6-558.2 m (2015 May 24) and 40.6-1507.9 m (2015 Sep 20)  
  > "one at the baseline length from 20.6 m to 558.2 m on 2015 May 24 and a more extended one at the baseline length from 40.6 m to 1507.9 m on 2015 September 20" (2 Observations)
- angular resolution: _not stated_
- max recoverable scale: ~17 arcsec at 10% level  
  > "which provides sensitivity to structures extending to $\sim \ang[angle-symbol-over-decimal]{;;17}$ scales at a level of 10%" (2 Observations)
- sensitivity: 5.9 and 5.1 mJy/beam (lines); 0.079 mJy/beam (continuum)  
  > "The final rms noise level for the 1.3 mm continuum is 0.079$\mjpbm$." (2 Observations)
- time on source: ~23 min and ~25 min  
  > "The on-source times are $\sim$23 min and $\sim$25 min for the former and latter observations, respectively." (2 Observations)
- observing dates: _not stated_
- pi or archival as stated: _not stated_
- Line: C18O J=2-1 (220.39868 GHz)
- External data: Dust mass opacity kappa=0.1 (nu/1THz)^beta, beta=1  
  > "The dust mass opacity is assumed to follow $\kappa_\nu = 0.1 (\nu/1 \mathrm{THz})^\beta$ with $\beta = 1$" (3.1 Continuum) [from (cite: Beckwith:1990aa; Jorgensen:2007aa)]
- External data: Class II disk radii and stellar masses  
  > "The Class $\mathrm{I\hspace{-.1em}I}\ $samples are taken from (cite: Guilloteau:2014aa; Simon:2017aa), which measure gas disk radii." (Disk Radius and Mass) [from (cite: Guilloteau:2014aa; Simon:2017aa)]
- External data: Class II 1.3 mm flux densities  
  > "using the flux densities measured at the 1.3 mm continuum in (cite: Andrews:2013aa)" (Disk Radius and Mass) [from (cite: Andrews:2013aa)]

## Processing

### Calibration

- pipeline or manual: _not stated_
- casa version: CASA 4.5.0 (longer baselines), CASA 4.5.2 (shorter baselines)  
  > "The calibration of the data with longer and shorter baselines was done with CASA 4.5.0 and CASA 4.5.2, respectively." (2 Observations)
- pipeline version: _not stated_
- archive products used as is: _not stated_
- flux calibrator: _not stated_
- flux scale uncertainty: ~10%  
  > "have an uncertainty of $\sim$10% (cite: Lundgren:2013aa)" (2 Observations)
- self calibration: continuum only, phase-only, solint per scan (~6 s), one iteration; peak SNR 59 to 97; flux +20%  
  > "Only the phase was calibrated with a solution interval of each scan (i.e., with the time bin of $\sim$6 s). The number of iterations was one, which increased the peak SNR from $\sim$59 to $\sim$97." (2 Observations)

### Imaging

- task: CASA clean (CASA version 5)  
  > "All of our images were produced by CLEAN using the CASA task *clean* with CASA version 5." (2 Observations)
- deconvolver: _not stated_
- weighting robust: Briggs, robust 0.5  
  > "For all the images, the Briggs weighting with a robust vale of 0.5 was used." (2 Observations)
- uv taper: FWHM = 200 klambda for PA=54 deg PV diagram  
  > "image cube made from the visibility tapered at FWHM = $200\ \mathrm{k\lambda}$ in the $(u,v)$ domain" (4.1 Velocity Structure)
- cell size: _not stated_
- image size: _not stated_
- masking: _not stated_
- multiscale scales: 0, 0.75", 1.25", 2.5"  
  > "scales sizes of approximately zero, three, five and ten times as large as the synthesized beam size" (2 Observations)
- continuum subtraction: _not stated_
- line free channels: _not stated_
- primary beam correction: _not stated_
- array combination: _not stated_
- smoothing: _not stated_
- final beam: 0.35x0.25" (C18O), 0.34x0.23" (continuum)  
  > "$\ang[angle-symbol-over-decimal]{;;0.34} \times \ang[angle-symbol-over-decimal]{;;0.23}\ (\ang{28})$ in the 1.3 mm continuum" (2 Observations)
- final rms: _not stated_

### Inherited from earlier work

- Beam-convolution correction to stellar mass (factor 1.3)  
  > "the derived central stellar mass should be multiplied by 1.3 to correct the effect of the beam convolution (see APPENDIX A in (cite: Aso:2015aa))" (4.1 Velocity Structure) [from (cite: Aso:2015aa)]
- Monte Carlo error estimation by refitting 10000 times  
  > "The uncertainties of the parameters are derived from fitting 10000 times with the data values changed within their errors at each fitting (cite: Yen:2013aa)" (4.1 Velocity Structure) [from (cite: Yen:2013aa)]
- Dust temperature of 25 K  
  > "the dust temperature to be 25 K, which is the minimum disk temperature within a radius of $500$ au in a disk model in (cite: Yen:2014aa)" (3.1 Continuum) [from (cite: Yen:2014aa)]
- Simulation model extended from earlier work  
  > "The model presented here was constructed by extending that of (cite: Matsumoto:2019aa)." (Numerical Simulations) [from (cite: Matsumoto:2019aa)]

### Not stated but needed to reproduce (our reading)

- Image sizes and cell sizes
- Clean masks and thresholds
- Line-free channels and continuum subtraction method
- Exact imaging parameters of the tapered cube
- Reference antenna and calibrator flux values
- Model temperature/dust setup details beyond the listed parameters
- Hydrodynamic simulation density normalization and initial parameters beyond those given

## Analysis recipe

1. **Fit continuum and estimate disk mass**: Two-Gaussian fit with MIRIAD imfit; mass from flux density with optically thin formula  
  > "The fitting was performed with the MIRIAD fitting task *imfit*." (3.1 Continuum)
   - software: MIRIAD
   - parameter: d=140 pc, T=25 K, kappa=0.023 cm2/g at 234 GHz, F=59 mJy  
  > "The total disk gas mass is thus estimated to be $7.1 \times 10^{-3} \Msun$ with $F_\nu = 59$ mJy." (3.1 Continuum)
   - assumption: beta=1, thin disk, inclination from broad Gaussian axes ~73 deg  
  > "we estimate the inclination angle $i$ of the disk to be $\sim$73$^\circ$from the lengths of the major and minor axes" (3.1 Continuum)
   - fitting: _not stated_
   - validation: Compared with Yen et al. 2014 flux densities  
  > "The total flux density derived from the two Gaussian components is 59 $\pm$ 4.5 mJy" (3.1 Continuum)
2. **Measure position angles of velocity gradient for high and low velocity components**: 2D Gaussian fits to blue/red peaks in moment 0 maps of two velocity ranges  
  > "we fitted 2D Gaussian functions to these blueshifted and redshifted components in the relevant maps with MIRIAD fitting task *imfit* and determined their peak positions." (3.2 C18O)
   - software: MIRIAD
   - fitting: _not stated_
   - validation: _not stated_
3. **Derive rotation profiles from PV diagrams**: Gaussian fitting at each channel (inner, positions) or each position (outer, velocities within +/-2 channels of peak); power-law and double power-law chi2 fits  
  > "We fit the following power-law function to the determined data points from the PV diagram by $\chi^2$ fitting" (4.1 Velocity Structure)
   - parameter: inner fit uses r<100 au  
  > "we use only data points at $r<100 \au$ for fitting to the inner component" (4.1 Velocity Structure)
   - assumption: i=73 deg for stellar mass  
  > "with $i=73 \ensuremath{^\circ}$, $V_{100}=3.20 \kmps$, and $r = 100 \au$" (4.1 Velocity Structure)
   - fitting: chi2 fit; errors from 10000 resamplings, 3 sigma  
  > "as $3\sigma$ values of the posterior distribution" (4.1 Velocity Structure)
   - validation: Model PV diagrams of Keplerian disks used to evaluate bias of the fitting method  
  > "we examine how correctly the new method derives the rotational profile." (Evaluation of Fitting Method on PV Diagram)
4. **Warped vs coplanar disk model comparison**: RADMC-3D models of two disks added in image domain, observed with simobserve, compared to channel maps, moment maps and PV  
  > "The produced disk models are observed using the CASA task *simobserve* with the ALMA antenna configurations similar to those in our observations." (4.2 Kinetic Model)
   - software: RADMC-3D, CASA
   - parameter: M*=1.6 Msun, Mdisk=0.0071 Msun, p=0.5, i=73 deg; inner 0.1-200 au PA 69; outer 300-600 au PA 54  
  > "Disk outer radius ($R_\mathrm{out}$)     |        $600 \au$        |" (Table 2)
   - assumption: h/r=0.03 (r/1au)^0.25, Keplerian, Semenov dust opacity, T*=4000 K  
  > "The scale height is given by $h/r = 0.03\ (r/ 1\au)^{0.25}$." (4.2 Kinetic Model)
   - fitting: No parameter fitting  
  > "No parameter fitting is performed because our purpose here is to confirm whether the warped disk model can reproduce the observed features" (4.2 Kinetic Model)
   - validation: Visual comparison  
  > "The warped disk model matches the observations, while the coplanar disk model exhibits a clear offset from the observations in the P.A. direction." (Kinetic Model)
5. **Compare disk radii/masses with other Class I and II**: Literature compilation, histograms, correlation of Mdisk with Tbol and Lbol/Lsubmm  
  > "Figure [14](#disk_corr)a shows a marginal, slight negative trend (the correlation coefficient is $-0.43$)" (Disk Mass Evolution during the Class I Phase)
   - assumption: Class II: kappa=2.3 cm2/g at 1.3 mm, T=25 (L*/Lsun)^0.25 K  
  > "$\langle T_\mathrm{disk} \rangle \sim 25(L_\ast/L_\odot)^{1/4}\ \mathrm{K}$ following (cite: Andrews:2013aa)" (Disk Radius and Mass)
   - fitting: _not stated_
   - validation: _not stated_

## Software

- **CASA** 4.5.0 / 4.5.2 (calibration); 5 (imaging): Calibration, clean imaging, self-calibration, simobserve  
  > "All of our images were produced by CLEAN using the CASA task *clean* with CASA version 5." (2 Observations)
- **MIRIAD** : imfit Gaussian fitting  
  > "The fitting was performed with the MIRIAD fitting task *imfit*." (3.1 Continuum)
- **RADMC-3D** : Temperature and synthetic images of disk models  
  > "We use the 3D radiative transfer code RADMC-3D" (4.2 Kinetic Model)
- **SFUMATO** : Hydrodynamic simulation of warped disk formation  
  > "We use `SFUMATO` (cite: Matsumoto:2007aa) with so-called fixed mesh refinement." (Numerical Simulations)

## Numeric results

| quantity | value | uncertainty | units | step | quote |
|---|---|---|---|---|---|
| Disk gas mass (kappa=0.023) | 7.1e-3 | not stated | Msun | 1 | The total disk gas mass is thus estimated to be $7.1 \times 10^{-3} \Msun$ with $F_\nu = 59$ mJy. |
| Total continuum flux density | 59 | 4.5 | mJy | 1 | The total flux density derived from the two Gaussian components is 59 $\pm$ 4.5 mJy |
| PA of high-velocity component | 69 | 2.6 | deg | 2 | The P.A. is estimated to be $69\ensuremath{^\circ}\pm 2.6\ensuremath{^\circ}$ for the high velocity component |
| PA of low-velocity component | 54 | 2.9 | deg | 2 | it is estimated to be $54\ensuremath{^\circ}\pm 2.9\ensuremath{^\circ}$ for the low velocity component |
| Inner rotation power-law index p | 0.50 | 0.11 | dimensionless | 3 | $7.22\pm 0.09\ \kmps$  / $3.20\pm0.15\ \kmps$ / $0.50\pm 0.11$ |
| Central stellar mass | 1.64 | 0.12 | Msun | 3 | The estimated central stellar mass after the correction is $1.64 \pm 0.12 \Msun$ |
| Outer break radius | 624 | 62 | au | 3 | $1.31 \pm 0.08\ \kmps$ / $624 \pm 62 \au$     / $0.47\pm0.05$   / $1.07\pm0.24$ |
| Outer p_in / p_out | 0.47 / 1.07 | 0.05 / 0.24 | dimensionless | 3 | $0.47\pm0.05$   / $1.07\pm0.24$ |

## Qualitative findings

- C18O emission shows dips at ~280 au (NE) and ~140 au (SW) absent in continuum, likely due to CO depletion  
  > "The dips are unlikely due to a real gas absence because the 1.3 mm continuum emission does not show any dips." (Summary)

## Claim tuples

- H: The L1489 IRS disk is warped | E: PA of velocity gradient in inner and outer parts; warped vs coplanar RADMC-3D models | R: PA 69 vs 54 deg; warped model reproduces dips and PA offset, coplanar does not | F: L1489 IRS is better explained as a warped disk system | **supported**
- H: A Keplerian disk extends beyond the dips | E: Power-law fits to PV-derived rotation profiles | R: p=0.50 inside, p_in=0.47 out to Rbreak~600 au | F: Keplerian disk to ~600 au, envelope outside | **supported**
- H: Disk mass decreases during the Class I phase | E: Compare Mdisk with Tbol and Lbol/Lsubmm for 10 Class I sources | R: correlation coefficients -0.43 and -0.49 | F: Weak negative trends only, possibly supporting mass decline | **partially**

## Reasoning

- Why this data: _not stated_
- Why this method: _not stated_
- Alternative: Binary torque breaking the disk is unlikely at 200-300 au (r_break <~60 au)  
  > "This upper limit implies that the binary torque is unlikely to break the disk at a large radius of $\sim$200–300 au" (5.1 Morphology)
- How they decided it was enough: _not stated_
- Limitation (authors): Outer disk inclination cannot be measured independently; non-axisymmetry not modeled  
  > "it is difficult to measure the inclination angle of the outer disk independently of the inner disk from the current data set" (5.1 Morphology)
- Caveat (inferred, ours): Warped model is not fitted, only visually compared
- Caveat (inferred, ours): Disk mass depends strongly on assumed opacity and temperature
- Caveat (inferred, ours): Class I sample is small and heterogeneous
- Caveat (inferred, ours): Cause of dips untested

## Reproducibility

- Data public (paper): Data from project 2013.1.01086.S (PI S. Koyamatsu)  
  > "ADS/JAO.ALMA #2013.1.01086.S (P.I. S. Koyamatsu)" (Acknowledgments)
- Products in archive: _not stated_
- Missing: Clean masks, thresholds, image size, cell size
- Missing: Line-free channels
- Missing: Model script details
- Data volume (inferred): ~50-100 GB raw
- Score (inferred): 3/5, Key imaging and fitting settings are given but several imaging details and the model setup are incomplete; the model comparison is qualitative.
- Rediscovery candidate: no, Main model comparison is qualitative and imaging details are incomplete, although the fitted numbers are reproducible.

## Links

- Method: (cite: Aso:2015aa) (Beam correction and rotation profile method)
- Method: (cite: Yen:2013aa) (Error estimation method)
- Companion: (cite: Yen:2014aa) (Previous lower resolution ALMA observations of L1489 IRS)

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
 "numeric_results": 8,
 "numeric_problems": 0,
 "fill": {
  "facts": 79,
  "stated": 49,
  "rate": 0.62
 },
 "evidence_ok": true
}
```
