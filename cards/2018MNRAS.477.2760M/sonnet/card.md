# Magnetically regulated collapse in the B335 protostar? I. ALMA observations of the polarized dust emission

`2018MNRAS.477.2760M` | Monthly Notices of the Royal Astronomical Society 2018 | first author: Maury, A. J. | arXiv: 1803.00028 | DOI: 10.1093/mnras/sty574

Card schema 1.0 | model claude-sonnet-5-5 | depth full | type observational_alma_primary

## Science

- Fields: star_formation
- Question: What is the magnetic field topology in the B335 Class 0 protostar envelope at 50-1000 au, and is it consistent with magnetically regulated collapse?  
  > "the magnetic field is maintaining a high level of organization from scales 1000 au to 50 au: this suggests the field is dynamically relevant" (abstract)
- Target **B335**: coordinates RA(J2000) 19h37m00.91s, Dec +07d34m09.6s (phase center)  
  > "B335 is an isolated Class 0 protostar with a bolometric luminosity of $\sim 1 L_{\ensuremath{\odot}}$, at a distance of 100 pc (cite: Olofsson09)" (1 Introduction); "The phase center was $\alpha$(J2000) = $19^{\rmn{h}} 37^{\rmn{m}} 00.91s$, $\delta$(J2000) = $+07\ensuremath{^\circ} 34\ensuremath{'} 09.6\ensuremath{''}$." (2 Observations and data reduction); z/distance 100 pc  
  > "B335 is an isolated Class 0 protostar with a bolometric luminosity of $\sim 1 L_{\ensuremath{\odot}}$, at a distance of 100 pc (cite: Olofsson09)" (1 Introduction); "The phase center was $\alpha$(J2000) = $19^{\rmn{h}} 37^{\rmn{m}} 00.91s$, $\delta$(J2000) = $+07\ensuremath{^\circ} 34\ensuremath{'} 09.6\ensuremath{''}$." (2 Observations and data reduction); distance from Olofsson09  
  > "B335 is an isolated Class 0 protostar with a bolometric luminosity of $\sim 1 L_{\ensuremath{\odot}}$, at a distance of 100 pc (cite: Olofsson09)" (1 Introduction); "The phase center was $\alpha$(J2000) = $19^{\rmn{h}} 37^{\rmn{m}} 00.91s$, $\delta$(J2000) = $+07\ensuremath{^\circ} 34\ensuremath{'} 09.6\ensuremath{''}$." (2 Observations and data reduction)

## Data provenance

- ALMA projects: 2013.1.01380.S
- bands: 1.29 mm / 233 GHz continuum, full polarization  
  > "Our ALMA Stokes I map of the 1.29 mm dust continuum emission in B335" (3 ALMA polarized dust emission map)
- frequencies and spectral setup: 223-227 GHz and 239-243 GHz windows  
  > "The receiver was tuned to cover the 223-227 GHz and 239-243 GHz windows" (2 Observations and data reduction)
- continuum bandwidth: 7.5 GHz aggregated (4 basebands of 1.87 GHz)  
  > "using an aggregated bandwidth 7.5 GHz for the continuum emission (4 basebands of 1.87 GHz bandwidth each)" (2 Observations and data reduction)
- arrays: _not stated_
- configurations: _not stated_
- baselines: 21 m to 639 m, 34 antennas  
  > "with 34 antennas sampling baselines from 21m to 639m (peak of baseline density around 200m)" (2 Observations and data reduction)
- angular resolution: 0.8"x0.54" (~80x54 au) beam  
  > "The maps have a synthesized beam $0.8\hbox{$^{\prime\prime}$}\times 0.54\hbox{$^{\prime\prime}$}$ ($\sim 80\times54$au)" (2 Observations and data reduction)
- max recoverable scale: _not stated_
- sensitivity: rms 0.12 mJy/beam Stokes I; ~0.02 mJy/beam Q and U  
  > "the rms noise in the Stokes I map is 0.12 mJy/beam while the Stokes Q and Stokes U map have rms noises $\sim$ 0.02 mJy/beam" (2 Observations and data reduction)
- time on source: 74 minutes  
  > "The total time spent on the source was 74 minutes." (2 Observations and data reduction)
- observing dates: 2015-05-30  
  > "B335 was observed with the ALMA interferometer on 2015-05-30" (2 Observations and data reduction)
- pi or archival as stated: _not stated_
- Other facility **SMA**: Initial dust polarization detection in B335  
  > "After detecting dust polarization in B335 with the SMA in the framework of our polarization survey of Class 0 protostars" (1 Introduction)
- External data: Large-scale B field strength 130±40 uG at 1000 au (SCUBA)  
  > "$130 \pm 40 \mu$G at 1000 au (cite: Wolf03)" (4.2 Magnetic field strength in B335) [from (cite: Wolf03)]
- External data: Large-scale field 12-40 uG  
  > "the field found at larger scales 12-40 $\mu$G (cite: Bertrang14)" (4.2 Magnetic field strength in B335) [from (cite: Bertrang14)]
- External data: Free-fall density profile rho(r)=(cs^2/2piG) r^-1.5  
  > "a density profile in the dynamical free-fall region $\rho(r) = (c_{\rm s}^2/2\pi G)r^{-1.5}$ (cite: Kurono13)" (4.2 Magnetic field strength in B335) [from (cite: Kurono13)]
- Simulation/model as data: Non-ideal MHD collapse models with ambipolar diffusion (2.5 Msun core, mu~2-6, beta 1e-2 to 1e-3, <B,J>=10 deg); best model mu=6, beta=1e-3, edge-on  
  > "from the best simple model found so far ($\mu=6$, $\beta=10^{-3}$), projected along an edge-on view" (4.3 Comparison to numerical models)

## Processing

### Calibration

- pipeline or manual: Calibrated by the NA ARC Node and released to authors  
  > "The data were calibrated by the NA Arc Node, and released to us on November 22, 2016." (2 Observations and data reduction)
- casa version: _not stated_
- pipeline version: _not stated_
- archive products used as is: _not stated_
- flux calibrator: Titan  
  > "The absolute flux scale was determined from observations of Titan" (2 Observations and data reduction)
- flux scale uncertainty: <~10%  
  > "with an absolute flux uncertainty of $\lower.5ex\hbox{$\; \buildrel < \over \sim \;$}$ 10%" (2 Observations and data reduction)
- self calibration: Phase self-calibration on Stokes I dataset  
  > "Self-calibration of the phases was performed on the Stokes I dataset." (2 Observations and data reduction)

### Imaging

- task: _not stated_
- deconvolver: _not stated_
- weighting robust: _not stated_
- uv taper: _not stated_
- cell size: _not stated_
- image size: _not stated_
- masking: _not stated_
- multiscale scales: _not stated_
- continuum subtraction: _not stated_
- line free channels: _not stated_
- primary beam correction: _not stated_
- array combination: _not stated_
- smoothing: _not stated_
- final beam: 0.8"x0.54"  
  > "The maps have a synthesized beam $0.8\hbox{$^{\prime\prime}$}\times 0.54\hbox{$^{\prime\prime}$}$" (2 Observations and data reduction)
- final rms: 0.12 mJy/beam (I); ~0.02 mJy/beam (Q,U)  
  > "the rms noise in the Stokes I map is 0.12 mJy/beam while the Stokes Q and Stokes U map have rms noises $\sim$ 0.02 mJy/beam" (2 Observations and data reduction)

### Not stated but needed to reproduce (our reading)

- CASA version and imaging task
- Weighting/robust, cell and image size, deconvolver, masking
- Self-calibration solution intervals
- Polarization calibration procedure details and debiasing of polarized intensity
- Whether the 2013.1.00211.S data were used
- Line-of-sight weighting details and model snapshots for the MHD comparison
- Gas temperature/sound speed used in DCF density
- How the 300 independent segments and the angle dispersion were computed

## Analysis recipe

1. **Make Stokes I, Q, U maps**: Phase self-calibration on Stokes I; Q and U imaged from full-polarization data  
  > "Self-calibration of the phases was performed on the Stokes I dataset." (2 Observations and data reduction)
   - fitting: _not stated_
   - validation: Instrumental polarization <0.5% from gain scatter  
  > "indicates an instrumental polarization \< 0.5%" (2 Observations and data reduction)
2. **Derive polarization vectors and B-field map**: Combine Q and U into polarized intensity and angles using pixels above 3 sigma; rotate angle by 90 deg  
  > "using only pixels where the Stokes Q and U fluxes exceeds 3 times the standard deviation" (3 ALMA polarized dust emission map)
   - assumption: Polarization not from self-scattering  
  > "it is unlikely the polarization detected in B335 comes from self-scattering" (footnote 2)
   - fitting: _not stated_
   - validation: _not stated_
3. **Estimate B-field strength**: Davis-Chandrasekhar-Fermi method in equatorial region  
  > "using the statistical Davis-Chandrasekhar-Fermi method" (4.2 Magnetic field strength in B335)
   - parameter: sigma_theta ~0.38 rad; v_turb 0.1-1 km/s  
  > "we find $\sigma_{\bar{\theta}} \sim 0.38$ radians" (4.2 Magnetic field strength in B335)
   - assumption: Free-fall density profile; v_turb 0.1 to 1 km/s  
  > "If we use $\rm{v}_{\rm turb}$ from 0.1 km$s^{-1}$ (similar to the thermal linewidth) to 1 km$s^{-1}$" (4.2 Magnetic field strength in B335)
   - fitting: _not stated_
   - validation: Authors caution DCF validity in dense dynamic environments is unvalidated  
  > "we stress that the validity of the DCF method in dense and dynamic environments remains to be validated" (4.2 Magnetic field strength in B335)
4. **Qualitative comparison with MHD models**: Line-of-sight density-weighted model B maps convolved with beam compared morphologically  
  > "integration along the line of sight weighted by the local density and convolved by a Gaussian pattern the size of the ALMA synthesized beam" (4.3 Comparison to numerical models)
   - fitting: _not stated_
   - validation: Qualitative only; quantitative comparison deferred to paper II  
  > "a quantitative comparison with the models is beyond the scope of this paper and will be presented in paper II" (4.3 Comparison to numerical models)

## Software


## Numeric results

| quantity | value | uncertainty | units | step | quote |
|---|---|---|---|---|---|
| Stokes I peak flux density | 44 | not stated | mJy/beam | 1 | a peak flux density 44 mJy/beam |
| Fractional polarization | ~4-11 | not stated | % | 2 | The fractional polarization is found to be $\sim$4-11% on average in the map |
| Maximum polarized intensity | 320 | not stated | uJy/beam | 2 | a maximum of the polarized intensity 320 $\mu$Jy/beam |
| B-field position angle histogram peaks | 74 deg and +164 deg | not stated | deg | 2 | two peaks at PA $74^{\circ}$ and $+164^{\circ}$ |
| Angle dispersion sigma_theta | 0.38 | not stated | rad | 3 | we find $\sigma_{\bar{\theta}} \sim 0.38$ radians |
| Magnetic field strength (DCF) | 300-3000 | range from v_turb | uG | 3 | we find a magnetic field strength 300-3000 $\mu$G, at radii 50-500 au |

## Qualitative findings

- Ordered field: poloidal along outflow cavity walls, pinched/equatorial in the inner envelope  
  > "a transition from a large-scale poloidal magnetic field, in the outflow direction, to strongly pinched in the equatorial direction" (abstract)

## Claim tuples

- H: Is dust polarization detected with a coherent field at 50-1000 au in B335? | E: ALMA 233 GHz full-polarization mapping | R: Polarization detected at all scales with fractional polarization ~4-11% | F: Field is highly ordered with pinched equatorial and poloidal cavity-wall components | **supported**
- H: Does the field strength imply a dynamically relevant field? | E: DCF method on equatorial region | R: 300-3000 uG at 50-500 au | F: Field strongly amplified relative to larger scales, though DCF validity uncertain | **partially**
- H: Is the topology consistent with magnetically regulated collapse? | E: Morphological comparison with non-ideal MHD models | R: Model with mu=6, beta=1e-3 resembles observed map; mu<5 too strong | F: Only magnetically regulated collapse with mu>5 explains the observations | **partially**

## Reasoning

- Why this data: _not stated_
- Why this method: _not stated_
- Alternative: Self-scattering as origin of polarization rejected since densities are too low and fractions too high  
  > "are much higher than the gas densities probed at these scales in B335" (footnote 2)
- How they decided it was enough: _not stated_
- Limitation (authors): Model comparison is only qualitative; DCF validity uncertain; interferometric filtering of large scales  
  > "we stress that a perfect agreement is not sought for here" (4.3 Comparison to numerical models)
- Caveat (inferred, ours): Quantitative model comparison deferred to paper II
- Caveat (inferred, ours): DCF uses assumed turbulent velocity range and density profile giving a factor of 10 range
- Caveat (inferred, ours): Debiasing of polarized intensity and angle uncertainties not described
- Caveat (inferred, ours): Interferometric filtering affects the field-topology interpretation

## Reproducibility

- Data public (paper): ALMA data acknowledged with project code; public status not explicitly stated  
  > "This paper makes use of the ALMA data ADS/JAO.ALMA$\#2013.1.01380.S$." (Acknowledgements)
- Products in archive: _not stated_
- Missing: Imaging parameters
- Missing: CASA version
- Missing: Polarization calibration details
- Missing: MHD model outputs
- Data volume (inferred): ~50-100 GB raw, single full-polarization Band 6 execution
- Score (inferred): 4/5, Single dataset with brief processing description; no imaging parameters or software versions; DCF numbers reproducible only approximately.
- Rediscovery candidate: no, Processing recipe is too sparse (no software or imaging parameters) and the key comparison is qualitative.

## Links

- Method: (cite: Davis51; Chandrasekhar53) (DCF method for field strength)
- Companion: (cite: Masson16) (MHD collapse models used for comparison)
- Related: SMA polarization survey of Class 0 protostars (Galametz et al. in prep)

## Checks

```json
{
 "quotes": 51,
 "quotes_ok": 51,
 "quote_pass_rate": 1.0,
 "quotes_too_long": 0,
 "unsupported_facts": 0,
 "project_codes": 1,
 "codes_not_in_text": [],
 "codes_not_in_obscore": [],
 "obscore_codes_not_in_card": [
  "2013.1.00211.S"
 ],
 "codes_printed_but_missing": [],
 "numeric_results": 6,
 "numeric_problems": 0,
 "fill": {
  "facts": 66,
  "stated": 37,
  "rate": 0.561
 },
 "evidence_ok": true
}
```
