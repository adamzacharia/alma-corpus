# Molecular line polarisation from the circumstellar envelopes of asymptotic giant branch stars

`2024A&A...686A.274V` | Astronomy and Astrophysics 2024 | first author: Vlemmings, W. H. T. | arXiv: 2404.01681 | DOI: 10.1051/0004-6361/202449448

Card schema 1.0 | model claude-sonnet-5-5 | depth full | type observational_alma_primary

## Science

- Fields: evolved_stars, stellar_physics
- Question: What is the large-scale magnetic field morphology and strength in AGB circumstellar envelopes, as traced by non-maser molecular line polarisation (GK effect and radiative alignment) in CW Leo and R Leo?  
  > "Non-masing molecular line polarisation observation can more directly reveal the large scale magnetic field morphology and hence probe the effect of the magnetic field on AGB mass-loss and the shaping of the AGB wind." (abstract)
- Target **CW Leo**: coordinates _not stated_; z/distance 123 pc  
  > "CW Leo is a C-type star located at a distance of 123 pc (cite: Groenewegen12)." (Introduction); distance from Groenewegen et al. 2012  
  > "CW Leo is a C-type star located at a distance of 123 pc (cite: Groenewegen12)." (Introduction)
- Target **R Leo**: coordinates _not stated_; z/distance 100 ± 5 pc  
  > "(cite: Andriant22) have derived an updated period-luminosity relation which yields a distance to R Leo of $100\pm5$ pc. This is the distance we adopt for this source." (Introduction); distance from Andriantsaralaza et al. 2022 period-luminosity relation  
  > "(cite: Andriant22) have derived an updated period-luminosity relation which yields a distance to R Leo of $100\pm5$ pc. This is the distance we adopt for this source." (Introduction)

## Data provenance

- ALMA projects: 2016.1.00251.S
- bands: Band 7 (~338 GHz continuum)  
  > "Considering the absolute flux uncertainty in ALMA band 7 is $\sim10\%$" (2 Observations and data reduction)
- frequencies and spectral setup: 4 spws of 1.875 GHz, 960 channels each, centred on 331.1, 333.0, 343.1, 345.0 GHz; channel width ~1.7 km/s  
  > "The spws were centred on $331.1$, $333.0$, $343.1$, and $345.0$ GHz and the resulting channel width was $\sim1.7$ km s$^{-1}$." (2 Observations and data reduction)
- continuum bandwidth: _not stated_
- arrays: _not stated_
- configurations: _not stated_
- baselines: _not stated_
- angular resolution: Line beams at 345 GHz: 0.84x0.75'' (CW Leo), 0.83x0.75'' (R Leo)  
  > "At 345 GHz, the beam sizes are $0.84\times0.75$$''$ (PA $42.7^\circ$) and $0.83\times0.75$$''$ (PA $49.1^\circ$) for CW Leo and R Leo respectively." (2 Observations and data reduction)
- max recoverable scale: ~7.9 arcsec  
  > "The maximum recoverable scale in our observations is $\sim 7.9$$''$." (2 Observations and data reduction)
- sensitivity: Line-free channel rms Stokes I: 2.0 (CW Leo), 1.1 (R Leo) mJy/beam  
  > "are $2.0~(1.1)~$mJy beam$^{-1}$, $1.5~(1.1)~$mJy beam$^{-1}$, $1.8~(1.2)~$mJy beam$^{-1}$ and $1.6~(1.2)~$mJy beam$^{-1}$." (2 Observations and data reduction)
- time on source: ~20 min CW Leo, ~60 min R Leo; 3.3 h session  
  > "The total on source observing time for CW Leo was $\sim 20$ min, while the time spent on R Leo was $\sim 60$ min." (2 Observations and data reduction)
- observing dates: May 20 2018  
  > "performed with ALMA in full polarisation mode on May 20 2018" (2 Observations and data reduction)
- pi or archival as stated: PI Vlemmings  
  > "(Project 2016.1.00251.S, PI:Vlemmings)" (2 Observations and data reduction)
- Line: 12CO J=3-2 (not stated)
- Line: CS J=7-6 (not stated)
- Line: H13CN J=4-3 (not stated)
- Line: SiS J=19-18 (not stated)
- Line: 29SiO v=0, J=8-7 (not stated)
- Line: SiO v=1, J=8-7 (maser) (not stated)
- Line: SiO v=2, J=8-7 (not stated)
- Other facility **ALMA ACA (Ramstedt+2020)**: 12CO J=3-2 total flux comparison for R Leo  
  > "compared to ALMA ACA observations of $^{12}$CO $J=3-2$ around R Leo (cite: Ramstedt20), we recover approximately half the Stokes I flux." (2 Observations and data reduction)
- Other facility **JCMT**: calibration observations for CW Leo CO flux comparison  
  > "For CW Leo, a comparison with JCMT calibration observations indicate we resolve out $\sim70\%$ of the CO emission." (2 Observations and data reduction)
- External data: R Leo distance 100±5 pc from updated period-luminosity relation  
  > "yields a distance to R Leo of $100\pm5$ pc. This is the distance we adopt for this source." (Introduction) [from (cite: Andriant22)]
- External data: CW Leo CSE model parameters (R*, T*, Mdot, vinf, Tc, qc, Rw, gas-to-dust) from literature, see model table  
  > "We have attempted to be as representative as possible to the models that exist in the literature but have not adjusted the model parameters for the different distances" (4.1 Circumstellar envelope models) [from (cite: Velilla19; 2012A&A...543A..48A)]
- External data: CO abundance profile parameters  
  > "We used the results of (cite: Saberi19) for the CO abundance profile." (4.1 Circumstellar envelope models) [from (cite: Saberi19)]
- External data: CN Zeeman line-of-sight field 2-9 mG at R~2500 au in CW Leo  
  > "line-of-sight magnetic field strength of $|B_{||}|\sim2-9$ mG estimated from Zeeman splitting of CN in the outer part ($R\sim2500$ au) of the envelope of CW Leo (cite: Duthu17)" (5.3 Structure function) [from (cite: Duthu17)]
- External data: Stellar continuum flux CW Leo ~500 mJy at 258 GHz  
  > "Recent ALMA high angular resolution observations of CW Leo at 258 GHz found a stellar continuum flux of $\sim500$ mJy (cite: Velilla23)." (3.1 Polarisation result overview) [from (cite: Velilla23)]
- Simulation/model as data: PORTAL polarised radiative transfer models (with LIME) of CW Leo and R Leo CSEs compared to the observations  
  > "The radiative transfer is performed using the converged output of a LIME (version 1.9.5) simulation (cite: Brinch10)." (4 Polarised radiative transfer models)

## Processing

### Calibration

- pipeline or manual: ALMA polarisation calibration scripts, redone after amplitude re-normalisation by ESO ARC  
  > "Calibration was done using the ALMA polarisation calibration scripts (cite: Nagai16)." (2 Observations and data reduction); "ALMA staff from the ESO ALMA Regional Centre performed a re-normalisation correction on our data. After that, calibration was redone using the standard procedure." (2 Observations and data reduction)
- casa version: CASA 5.7.2 (self-calibration and imaging)  
  > "self-calibration and imaging was performed using CASA 5.7.2." (2 Observations and data reduction)
- pipeline version: _not stated_
- archive products used as is: _not stated_
- flux calibrator: J0854+2006 (amplitude and polarisation calibrator)  
  > "the amplitude and polarisation calibrator J0854+2006" (2 Observations and data reduction)
- flux scale uncertainty: ~10% in band 7  
  > "Considering the absolute flux uncertainty in ALMA band 7 is $\sim10\%$" (2 Observations and data reduction)
- self calibration: Two rounds phase-only on continuum, solint 'inf' and 'int'  
  > "Two rounds of phase-only self-calibration, (with solution intervals "inf" and "int") were done on the continuum." (2 Observations and data reduction)

### Imaging

- task: _not stated_
- deconvolver: _not stated_
- weighting robust: Briggs, robust = 0.5  
  > "the spectral lines were imaged using Briggs weighing and a robust parameter of $0.5$." (2 Observations and data reduction)
- uv taper: _not stated_
- cell size: _not stated_
- image size: _not stated_
- masking: _not stated_
- multiscale scales: _not stated_
- continuum subtraction: CASA uvcontsub  
  > "the continuum was subtracted using the CASA task *uvcontsub*." (2 Observations and data reduction)
- line free channels: _not stated_
- primary beam correction: _not stated_
- array combination: _not stated_
- smoothing: CW Leo: two channels averaged to ~3.4 km/s; R Leo native 1.7 km/s  
  > "For CW Leo, we averaged two channels, obtaining a velocity resolution of $\sim 3.4$ km s$^{-1}$." (2 Observations and data reduction)
- final beam: Continuum 0.79x0.72'' (CW Leo), 0.78x0.71'' (R Leo)  
  > "are $0.79\times0.72$$''$ (PA $39.0^\circ$) and $0.78\times0.71$$''$ (PA $46.2^\circ$) for CW Leo and R Leo respectively." (2 Observations and data reduction)
- final rms: Continuum Stokes I 390 uJy/beam (CW Leo), 98 uJy/beam (R Leo)  
  > "The final continuum rms in Stokes I ($\sigma_I$) is $390~\mu$Jy beam$^{-1}$ for CW Leo and $98~\mu$Jy beam$^{-1}$ for R Leo." (2 Observations and data reduction)

### Inherited from earlier work

- Structure function analysis steps  
  > "In our analysis, we follow the equations from (cite: Koch10) and the steps described in (cite: Vlemmings23)." (5.3 Structure function) [from (cite: Koch10); (cite: Vlemmings23)]
- Estimate of number of turbulent cells N  
  > "Following the approach outlined in (cite: Vlemmings23), the number of independent turbulent cells ($N$) probed by our observations is estimated using the formula from (cite: Houde16)" (5.3 Structure function) [from (cite: Vlemmings23); (cite: Houde16)]
- CW Leo dipole field position angle 125 deg  
  > "We assume the dipole to be directed with a position angle of 125$^\circ$, as was suggested by (cite: Andersson23)" (4.2 CW Leo) [from (cite: Andersson23)]
- Circular polarisation vs B relation for SiO masers  
  > "Assuming the relation between SiO maser circular polarisation fraction and magnetic field strength from (cite: 1997ApJ...481L.111K)" (3.3 R Leo) [from (cite: 1997ApJ...481L.111K)]

### Not stated but needed to reproduce (our reading)

- Exact self-calibration solution interval values and spw/channel selection for continuum
- Line-free channels used for uvcontsub and fit order
- Image size, cell size, deconvolver, masking and clean threshold
- Polarisation calibration script details and leakage solutions
- Details of the amplitude re-normalisation correction
- PORTAL/LIME setup: grid, number of photons, magnetic field strength used for the CO models, abundances for 29SiO/other molecules' vibrational details
- Structure function fit details (bin sizes, vector selection, fitting range, turbulent velocity and density values)
- Stellar velocity-based channel selection for radial profiles and centre position definition
- R Leo CO abundance and temperature profile specifics beyond table

## Analysis recipe

1. **Calibrate and self-calibrate**: ALMA polarisation calibration scripts after re-normalisation correction; two rounds phase-only self-cal on continuum  
  > "Calibration was done using the ALMA polarisation calibration scripts (cite: Nagai16)." (2 Observations and data reduction)
   - software: CASA 5.7.2
   - parameter: solint 'inf' then 'int'  
  > "Two rounds of phase-only self-calibration, (with solution intervals "inf" and "int") were done on the continuum." (2 Observations and data reduction)
   - fitting: _not stated_
   - validation: Compared before/after re-normalisation spectra; compared flux with ACA and JCMT  
  > "A comparison between the results before and after re-normalisation indeed revealed significant differences in the total intensity spectra." (2 Observations and data reduction)
2. **Make Stokes cubes and debiased polarisation maps**: uvcontsub, Briggs robust 0.5 imaging of I,Q,U,V; P_l = sqrt(Q^2+U^2-sigma_P^2) with sigma_P mean of sigma_Q and sigma_U  
  > "Finally we produce debiased linear polarisation maps from the Stokes Q and U imaged using $P_l=\sqrt{Q^2+U^2-\sigma^2_P}$." (2 Observations and data reduction)
   - software: CASA
   - parameter: detection threshold >5 sigma_P  
  > "We detect significant ($>5\sigma_P$) polarised emission towards the 338 GHz continuum of both CW Leo and R Leo" (3.1 Polarisation result overview)
   - fitting: _not stated_
   - validation: Stokes V found dominated by beam effects for extended lines  
  > "find that these are, for the extended molecular lines, dominated by ALMA beam effects (cite: Hull20)." (2 Observations and data reduction)
3. **Characterise polarisation morphology and radial profiles**: Histograms of deviation from tangential direction; azimuthally averaged Stokes I, polarised flux and fraction in channel nearest stellar velocity  
  > "we plot a histogram with the deviation from the tangential direction for all polarisation vectors in Fig. [6](#fig:angdist)(left)" (3.2 CW Leo)
   - parameter: V_lsr CW Leo = -26.5 km/s  
  > "($V_{\rm lsr, CW Leo}=-26.5$ km s$^{-1}$)" (3.2 CW Leo)
   - fitting: _not stated_
   - validation: Consistency between neighbouring channels used to argue against missing-flux artefacts  
  > "All lines show a good correspondence of polarisation structure between neighbouring channels" (3.2 CW Leo)
4. **Polarised radiative transfer modelling**: PORTAL on converged LIME output with parameterised CSE (density, T, velocity, abundance profiles); compare radiative rates to magnetic precession rate; model radial alignment for CS/H13CN/SiS and dipole/toroidal B for CO of CW Leo, radial for R Leo  
  > "The modelling of the line polarisation is performed with the PORTAL (POlarised Radiative Transfer Adapted to Lines) code (cite: Lankhaar20)." (4 Polarised radiative transfer models)
   - software: PORTAL, LIME 1.9.5
   - parameter: CW Leo dipole inclined 45 deg, PA 125 deg  
  > "we assume it to be inclined at 45$^\circ$" (4.2 CW Leo)
   - parameter: turbulent velocity 1 km/s; gas mean particle mass 2.35 AMU  
  > "contained a contribution from a constant turbulent velocity of 1 km s$^{-1}$" (4.1 Circumstellar envelope models)
   - assumption: Spherically symmetric envelope expanding at constant velocity; amorphous carbon opacities (CW Leo), silicate (R Leo); gas-to-dust 300 (CW Leo), 167 (R Leo)  
  > "In the case of C-rich CSEs, such as CW Leo, we adopted the opacities for amorphous carbon type of dust given by (cite: suh00)" (4.1 Circumstellar envelope models)
   - fitting: No fitting; forward models compared qualitatively  
  > "Comparing the predicted polarisation morphology to the observed polarisation morphology in CO, we find only modest agreement." (Line polarisation simulations: CW Leo)
   - validation: Qualitative comparison of predicted and observed polarisation morphology and fractions  
  > "The predicted polarisation morphology appears to be consistent with the observations." (4.3 R Leo)
5. **Magnetic field strength via structure function analysis (CW Leo CO)**: Structure function of CO J=3-2 polarisation angles in central channel, fit with Koch et al. 2010 equation within <~2''; B0 from turbulent-to-ordered ratio and Alfven velocity; correction N from Houde16  
  > "The structure function can be fit using the equation from (cite: Koch10) within $\lesssim2$$''$" (5.3 Structure function)
   - parameter: delta~300 au, Delta'~500 au, W1~40 au, N~1.2  
  > "This yields $\delta\sim300$ au and $\Delta'\sim500$ au. The parameter $W_1\approx40$ au is the radius of the interferometric beam." (5.3 Structure function)
   - assumption: Field frozen into gas, isotropic incompressible turbulence from transverse Alfven waves; result a lower limit if not frozen  
  > "the derived field strength should be considered a lower limit." (5.3 Structure function)
   - fitting: structure function fit; ratio 0.061 ± 0.001  
  > "$\frac{\langle B_t^2\rangle^{1/2}}{B_0} = 0.061\pm0.001$" (5.3 Structure function)
   - validation: Other velocity channels give field within 30%  
  > "yield similar field strengths to within $30\%$" (5.3 Structure function)

## Software

- **CASA** 5.7.2: self-calibration and imaging, uvcontsub  
  > "self-calibration and imaging was performed using CASA 5.7.2." (2 Observations and data reduction)
- **PORTAL** : polarised radiative transfer modelling  
  > "The modelling of the line polarisation is performed with the PORTAL (POlarised Radiative Transfer Adapted to Lines) code (cite: Lankhaar20)." (4 Polarised radiative transfer models)
- **LIME** 1.9.5: radiative transfer providing the converged radiation field input to PORTAL  
  > "The radiative transfer is performed using the converged output of a LIME (version 1.9.5) simulation (cite: Brinch10)." (4 Polarised radiative transfer models)

## Numeric results

| quantity | value | uncertainty | units | step | quote |
|---|---|---|---|---|---|
| Max continuum fractional polarisation CW Leo | 0.88 | not stated | % | 2 | The maximum fraction of continuum polarisation is $0.88\%$ for CW Leo and $0.17\%$ for R Leo. |
| Max continuum fractional polarisation R Leo | 0.17 | not stated | % | 2 | The maximum fraction of continuum polarisation is $0.88\%$ for CW Leo and $0.17\%$ for R Leo. |
| Peak fractional polarisation 12CO J=3-2 CW Leo | 1.18 | not stated | % | 2 | / $^{12}$CO $J=3-2$      / 17.89              / 1.18             / |
| Peak fractional polarisation 12CO J=3-2 R Leo | 3.90 | not stated | % | 2 | / $^{12}$CO $J=3-2$      / 4.66               / 3.90             / |
| Peak fractional polarisation SiO v=1 J=8-7 R Leo | 32.4 | not stated | % | 2 | / SiO $v=1,J=8-7$        / 12.68              / 32.4             / |
| SiO v=1 circular polarisation fraction R Leo | 1.3 | not stated | % | 2 | This corresponds to a circular polarisation percentage of $P_v=1.3\%$. |
| Structure function ratio B_t/B0 CW Leo | 0.061 | 0.001 | dimensionless | 5 | $\frac{\langle B_t^2\rangle^{1/2}}{B_0} = 0.061\pm0.001$ |
| Plane-of-sky field CW Leo at ~250 au | ~19 | not stated | mG | 5 | reveal a plane-of-the-sky magnetic field of $\sim19$ mG at $R=250$ au |
| B(r) CW Leo, r=50-485 au | 107 x (50/r) | not stated | mG (r in au) | 5 | $B=107\times(50/r)$ mG between $r=50$ and $485$ au |
| Number of turbulent cells N | ~1.2 | not stated | dimensionless | 5 | Hence, we find $N\sim1.2$. |
| SiO maser field strength R Leo from circular polarisation | 2-3 | not stated | G | 2 | this corresponds to a magnetic field of $B\sim2-3$ G in the SiO maser region |
| Dust fractional polarisation R Leo / CW Leo (if dust-only) | ~0.6 / 3 | not stated | % | 2 | this means the dust fractional polarisation is $\sim0.6\%$. |

## Qualitative findings

- CO polarisation traces the magnetic field in CW Leo while CS (outer), SiS and H13CN are radiatively aligned (tangential vectors); around R Leo CO is radial and H13CN, 29SiO tangential, consistent with a radial field advected by the wind.  
  > "Around R Leo, the observed polarisation morphology of the CO, H$^{13}$CN and $^{29}$SiO can be explained by a large scale magnetic field that is radially advected by the outflow." (Conclusions)
- Anisotropic resonant scattering likely does not affect the polarisation of these sources.  
  > "we conclude that anisotropic resonant scattering likely does not affect the polarisation of our sources." (5.2 Anisotropic Resonant Scattering)

## Claim tuples

- H: Non-maser molecular line polarisation is detectable in AGB CSEs with ALMA. | E: Full-polarisation ALMA Band 7 observations of CW Leo and R Leo. | R: Several lines with >5 sigma_P polarisation, 1-4% fraction; SiO v=1 up to ~32%. | F: Linear polarisation detected in multiple molecular lines around both stars. | **supported**
- H: Different polarisation structures arise from magnetic (GK) versus radiative alignment. | E: Compare PORTAL models and radiative vs precession rates to vector orientations. | R: CO aligned with B; CS (outer), SiS, H13CN aligned with radiation field in CW Leo. | F: Competition of alignment mechanisms explains line-to-line differences and constrains B(r). | **supported**
- H: Field strengths from alignment, structure function and CN Zeeman are consistent for CW Leo. | E: Compare alignment-derived limit (<~20 uG beyond 170 au) with SFA (~19 mG at 250 au) and CN Zeeman. | R: SFA and Zeeman consistent with each other but far above the alignment limit. | F: Inconsistency between methods remains unresolved. | **refuted**
- H: The R Leo field is advected by the wind. | E: Radial-field PORTAL model of CO, H13CN, 29SiO. | R: Predicted morphologies match observed radial CO and tangential H13CN/29SiO. | F: Field in outer envelope of R Leo is radial, advected outward. | **supported**

## Reasoning

- Why this data: Two sources close on the sky observed in one session as representative C-type and M-type AGB stars  
  > "We selected these two sources, located sufficiently close on the sky to be observed with ALMA in a single observation, as representative cases of the C-type and M-type families" (Introduction)
- Why this method: _not stated_
- Alternative: Dipole and toroidal B models for CW Leo CO gave only modest agreement, so field is not a simple geometry.  
  > "This likely indicates that the morphology of the magnetic field in the envelope of CW Leo cannot be described by a simple magnetic field geometry." (4.2 CW Leo)
- How they decided it was enough: _not stated_
- Limitation (authors): Spatial filtering resolves out much CO flux, overestimating polarisation fractions by factor 2-3.  
  > "this can lead to an overestimate of the polarisation fractions with a factor of $2-3$" (2 Observations and data reduction)
- Limitation (authors): Circular polarisation of extended lines dominated by beam effects; no test of anisotropic resonant scattering.  
  > "we cannot directly investigate anisotropic resonance scattering through a study of the circular polarisation." (5.2 Anisotropic Resonant Scattering)
- Caveat (inferred, ours): Models use literature parameters at inconsistent distances and are compared only qualitatively, no fitting or uncertainties
- Caveat (inferred, ours): SFA field relies on assumed density, turbulent velocity and flux freezing
- Caveat (inferred, ours): Resolved-out flux affects polarisation fractions and possibly SFA
- Caveat (inferred, ours): Vibrational-state coverage in alignment rates is incomplete, limiting B constraints

## Reproducibility

- Data public (paper): Project code given in acknowledgements; archive data  
  > "This paper makes use of the following ALMA data: ADS/JAO.ALMA#2016.1.00251.S." (Acknowledgements)
- Products in archive: _not stated_
- Missing: Self-cal and imaging parameters (cell, image size, masks)
- Missing: Details of amplitude re-normalisation correction
- Missing: PORTAL model grid/numerical settings and full molecular abundance inputs
- Missing: Structure function binning and vector selection
- Data volume (inferred): ~50-100 GB raw (single 3.3 h full-polarisation Band 7 session, 4 spws x 960 channels)
- Score (inferred): 3/5, Public data and clear observational recipe with numeric results, but imaging details and PORTAL modelling specifics are missing and modelling is qualitative.
- Rediscovery candidate: no, Observational numbers reproducible in principle, but key imaging/calibration details and the re-normalisation are unstated and main conclusions rely on PORTAL modelling.

## Links

- Method: (cite: Lankhaar20) (PORTAL polarised radiative transfer code)
- Method: (cite: Nagai16) (ALMA polarisation calibration scripts)
- Method: (cite: Koch10) (structure function equations)
- Companion: (cite: Vlemmings23) (similar CO polarisation and structure function analysis (steps followed))
- Companion: (cite: Girart12) (previous SMA polarisation of CW Leo)
- Companion: (cite: Huang20) (previous CARMA polarisation of R Leo)

## Checks

```json
{
 "quotes": 91,
 "quotes_ok": 91,
 "quote_pass_rate": 1.0,
 "quotes_too_long": 0,
 "unsupported_facts": 0,
 "project_codes": 1,
 "codes_not_in_text": [],
 "codes_not_in_obscore": [],
 "obscore_codes_not_in_card": [],
 "codes_printed_but_missing": [],
 "numeric_results": 12,
 "numeric_problems": 0,
 "fill": {
  "facts": 89,
  "stated": 65,
  "rate": 0.73
 },
 "evidence_ok": true
}
```
