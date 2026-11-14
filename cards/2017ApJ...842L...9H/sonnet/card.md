# Unveiling the Role of the Magnetic Field at the Smallest Scales of Star Formation

`2017ApJ...842L...9H` | The Astrophysical Journal Letters 2017 | first author: Hull, Charles L. H. | arXiv: 1706.03806 | DOI: 10.3847/2041-8213/aa71b7

Card schema 1.0 | model claude-sonnet-5-5 | depth full | type observational_alma_primary

## Science

- Fields: star_formation
- Question: Does the magnetic field in the Class 0 protostar Ser-emb 8 show strong-field (hourglass, large-scale-aligned) morphology at ~100 AU scales, and is it consistent with weakly or strongly magnetized AREPO simulations?  
  > "We conclude that the Ser-emb 8 data are most similar to the weakly magnetized simulations, which exhibit random alignment" (abstract)
- Target **Ser-emb 8 (S68N)**: coordinates RA ~277.45 deg, Dec ~1.278 deg (J2000; from Table 1 positions)  
  > "Ser-emb 8 is one of several low-mass, Class 0 protostars in the Serpens Main star-forming region" (1 Introduction); z/distance _not stated_; distance from _not stated_

## Data provenance

- ALMA projects: _none stated_
- bands: Band 7 (870 um)  
  > "The 870 $\mu$m (Band 7) ALMA dust polarization observations of Ser-emb 8 were taken on 2015 June 3 and 7" (2 ALMA Observations)
- frequencies and spectral setup: _not stated_
- continuum bandwidth: 8 GHz, ~336-350 GHz, mean 343.479 GHz  
  > "The ALMA polarization data comprise 8 GHz of wide-band dust continuum ranging in frequency from $\sim$ 336–350 GHz, with a mean frequency of 343.479 GHz." (2 ALMA Observations)
- arrays: _not stated_
- configurations: _not stated_
- baselines: _not stated_
- angular resolution: ~0.3" (140 AU)  
  > "have $\sim$ 0.3$^{\prime\prime}$ angular resolution" (2 ALMA Observations)
- max recoverable scale: _not stated_
- sensitivity: sigma_I = 50 uJy/beam; sigma_Q ≈ sigma_U = 25 uJy/beam  
  > "The rms noise level in the final Stokes $I$ dust map is $\sigma_I = 50$ $\mu$Jy beam$^{-1}$" (2 ALMA Observations)
- time on source: _not stated_
- observing dates: 2015 June 3 and 7  
  > "were taken on 2015 June 3 and 7" (2 ALMA Observations)
- pi or archival as stated: _not stated_
- Other facility **CARMA (TADPOL)**: Earlier lower-resolution polarization maps of Ser-emb 8  
  > "were observed in full polarization with the Combined Array for Millimeter-wave Astronomy (CARMA) as part of the TADPOL survey" (1 Introduction)
- Other facility **JCMT**: Large-scale polarization map for comparison  
  > "not resolved in the lower-resolution observations by CARMA or the James Clerk Maxwell Telescope (JCMT)" (4 Results and analysis)
- External data: Ser-emb 8 mass ~9.4 Msun within 100,000 AU (Bolocam)  
  > "estimating that the source has a mass of approximately 9.4 $M_\odot$ within a 100,000 AU region surrounding the protostar" (1 Introduction) [from (cite: Enoch2009b; Enoch2011)]
- External data: CARMA and JCMT polarization maps of Ser-emb 8  
  > "previous polarization observations of Ser-emb 8 by CARMA (cite: Hull2014; Hull2015b)" (4 Results and analysis) [from (cite: Hull2014)]
- Simulation/model as data: Four AREPO ideal-MHD turbulent self-gravitating simulations, 5.2 pc box, 8000 Msun, initial B = 1.2, 12, 36, 120 uG (M_A = 35, 3.5, 1.2, 0.35), Ms = 10, 256^3 cells  
  > "Each simulation uses $256^3$ particles, which corresponds to a mass resolution of $8 \times 10^{-5}~{M_\odot}$" (3 AREPO simulations)

## Processing

### Calibration

- pipeline or manual: _not stated_
- casa version: _not stated_
- pipeline version: _not stated_
- archive products used as is: _not stated_
- flux calibrator: _not stated_
- flux scale uncertainty: _not stated_
- self calibration: Four rounds of phase-only self-calibration using Stokes I image as model  
  > "The image was improved iteratively by four rounds of phase-only self calibration using the Stokes $I$ image as a model." (2 ALMA Observations)

### Imaging

- task: CASA CLEAN  
  > "The dust continuum image (Figure [1](#fig:3panel)(c)) was produced by using the CASA task `CLEAN`" (2 ALMA Observations)
- deconvolver: _not stated_
- weighting robust: Briggs robust = 1  
  > "with a Briggs weighting parameter of robust = 1" (2 ALMA Observations)
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
- final beam: 0.35" x 0.32", PA -61 deg  
  > "The final synthesized beam is $0.35\ensuremath{''}\times0.32\ensuremath{''}$ at a position angle of –61$\degree$." (2 ALMA Observations)
- final rms: Stokes I 50 uJy/beam; Q,U 25 uJy/beam  
  > "$\sigma_Q \approx \sigma_U \approx \sigma_P = 25$ $\mu$Jy beam$^{-1}$" (2 ALMA Observations)

### Inherited from earlier work

- ALMA polarization system and reduction of polarization data  
  > "For further details on the ALMA polarization system and the reduction of ALMA polarization data, see (cite: Cortes2016; Nagai2016)" (2 ALMA Observations) [from (cite: Cortes2016; Nagai2016) and CASA Guide on 3C 286 polarization]
- Debiasing of polarized intensity  
  > "We thus debias the polarized intensity map as described in (cite: Vaillancourt2006) and (cite: Hull2015b)." (2 ALMA Observations) [from (cite: Vaillancourt2006; Hull2015b)]
- HRO method  
  > "The “Histogram of Relative Orientation” (HRO) method (cite: Soler2013) can be used to study how morphological density structures and the magnetic field are related." (4.1 Histogram of Relative Orientation) [from (cite: Soler2013)]
- Detailed simulation analysis  
  > "For a detailed analysis of the simulations, along with the theoretical properties of the collapsed protostellar cores" (3 AREPO simulations) [from (cite: Mocz2017)]

### Not stated but needed to reproduce (our reading)

- Project code and calibrators (flux, bandpass, polarization)
- CASA version and calibration procedure
- Number of CLEAN iterations, masks, cell and image size
- Number of HRO bins and exact gradient computation
- AREPO line-of-sight set and core selection for mock observations
- Distance to Ser-emb 8

## Analysis recipe

1. **Image Stokes I, Q, U**: CLEAN with robust=1 after four rounds of phase-only self-calibration; Stokes I, Q, U cleaned independently  
  > "The Stokes $I$, $Q$, and $U$ maps were each `CLEANed` independently with an appropriate number of `CLEAN` iterations" (2 ALMA Observations)
   - software: CASA
   - fitting: _not stated_
   - validation: _not stated_
2. **Derive polarization maps and field orientation**: P = sqrt(Q^2+U^2), P/I, chi = 0.5 arctan(U/Q), P debiased; B field taken perpendicular to polarization  
  > "The polarized intensity $P = \sqrt{Q^2 + U^2}$, the fractional polarization $P_\textrm{frac} = P / I$, and the polarization position angle $\chi = 0.5\,\arctan{\left(U / Q\right)}$." (2 ALMA Observations)
   - fitting: _not stated_
   - validation: _not stated_
3. **Run AREPO simulations and make synthetic polarization**: Synthetic Q, U, column density in 3000 AU region around each core, optically thin, 12 AU grid, multiple lines of sight  
  > "we calculate synthetic polarization in a $3000$ AU region centered on each core assuming the optically thin limit." (4.1 Histogram of Relative Orientation)
   - software: AREPO
   - assumption: Isothermal, ideal MHD; scaled with cs = 0.2 km/s, nH = 1000 cm^-3  
  > "We have scaled our simulations to physical units using a sound speed of $c_{\rm s}=0.2~{\rm km}~{\rm s}^{-1}$ and hydrogen density $n_{\rm H} = 1000~{\rm cm}^{-3}$." (3 AREPO simulations)
   - fitting: _not stated_
   - validation: Downsampling mock column densities has no significant effect on HRO  
  > "downsampling the mock projected column densities has no significant effect on the computed HRO" (4.1 Histogram of Relative Orientation)
4. **Compute HRO for ALMA and simulations**: Angle between B and Stokes I (or density) gradient per pixel, weighted 1/0 by gradient above median; averaged over lines of sight  
  > "weighting the contribution from each element by a 1 or 0 depending on whether the magnitude of the density gradient is above the median value" (4.1 Histogram of Relative Orientation)
   - assumption: Field perpendicular to measured polarization; Stokes I traces column density structure  
  > "we assume the magnetic field has an orientation that is perpendicular to the measured polarization" (4.1 Histogram of Relative Orientation)
   - fitting: _not stated_
   - validation: Shaded regions show variation across lines of sight  
  > "the shaded error regions in Figure [3](#fig:HRO) reflect the variation in the HROs calculated along different lines of sight" (4.1 Histogram of Relative Orientation)

## Software

- **CASA** : Imaging (CLEAN) and polarization reduction  
  > "produced by using the CASA task `CLEAN` with a Briggs weighting parameter of robust = 1" (2 ALMA Observations)
- **AREPO** : MHD gravo-turbulence simulations  
  > "We perform our simulations using the AREPO code (cite: 2010MNRAS.401..791S), which uses a moving Voronoi mesh" (3 AREPO simulations)

## Numeric results

| quantity | value | uncertainty | units | step | quote |
|---|---|---|---|---|---|
| Synthesized beam | 0.35 x 0.32 at PA -61 | not stated | arcsec, deg | 1 | The final synthesized beam is $0.35\ensuremath{''}\times0.32\ensuremath{''}$ at a position angle of –61$\degree$. |
| Stokes I rms | 50 | not stated | uJy/beam | 1 | $\sigma_I = 50$ $\mu$Jy beam$^{-1}$ |
| Stokes Q/U rms | 25 | not stated | uJy/beam | 1 | $\sigma_Q \approx \sigma_U \approx \sigma_P = 25$ $\mu$Jy beam$^{-1}$ |
| Initial mass-to-flux ratio of the four simulations | 80, 8, 2.7, 0.8 | not stated | dimensionless | 3 | Thus, our four simulations have $\mu_{\Phi,0}=80,8,2.7,0.8$. |

## Qualitative findings

- ALMA field in Ser-emb 8 has no hourglass morphology and shows perturbed structure at small scales  
  > "The magnetic field revealed by the ALMA data does not have an hourglass morphology" (4 Results and analysis)
- HRO of ALMA data is flat, like the weakly magnetized simulations; strong-field HRO peaks at phi = 0  
  > "we find that the HRO of the ALMA observations of Ser-emb 8 is flat, indicating a random field similar to the weakly magnetized simulations" (4.1 Histogram of Relative Orientation)

## Claim tuples

- H: Ser-emb 8 formed in a strongly magnetized environment with an hourglass field | E: ALMA Band 7 polarization map compared with four AREPO simulations via HRO | R: No hourglass; flat HRO matching weak-field simulations | F: Ser-emb 8 formed in a super- or trans-Alfvénic environment where turbulence shapes the material | **supported**
- H: Cloud-scale field strength determines small-scale field and density structure | E: Four AREPO simulations with different initial field strengths | R: Only the 120 uG simulation preserves field direction and shows hourglass below 1000 AU | F: Only very strong fields yield hourglass and aligned structure | **supported**

## Reasoning

- Why this data: _not stated_
- Why this method: HRO quantifies relation between field and density structure, as used by Planck  
  > "Here we use this technique to shed light on the role of the magnetic field at the $\sim$ 100 AU scale of an individual star-forming core" (4.1 Histogram of Relative Orientation)
- How they decided it was enough: _not stated_
- Limitation (authors): Trends in P vs I are weak and could be geometrical; simulations lack outflows, disks, non-ideal MHD  
  > "However, the trends in Figure [4](#fig:P_vs_I) are weak, and could be due to geometrical effects." (5.2 Dust-grain alignment)
- Caveat (inferred, ours): Single source compared with simulations
- Caveat (inferred, ours): Grain alignment at 100 AU assumed
- Caveat (inferred, ours): No kinematic constraint on Alfvén Mach number
- Caveat (inferred, ours): Only one self-cal and imaging choice

## Reproducibility

- Data public (paper): Machine-readable polarization table available online with the paper  
  > "*The full, machine-readable table is available in the online version of the ApJ Letter.*" (Table 1)
- Products in archive: _not stated_
- Missing: Project code not printed
- Missing: Calibration details
- Missing: AREPO simulation outputs/code not released
- Missing: HRO implementation details
- Data volume (inferred): ~10-50 GB raw for two Band 7 polarization execution blocks
- Score (inferred): 3/5, ALMA imaging steps are partly given, but calibration and simulation inputs are missing; the HRO method is clear.
- Rediscovery candidate: no, The simulations are not available and the calibration and polarization reduction details are incomplete.

## Links

- Method: (cite: Soler2013) (HRO method)
- Method: (cite: Cortes2016; Nagai2016) (ALMA polarization reduction)
- Method: (cite: Mocz2016) (AREPO MHD implementation)
- Companion: (cite: Mocz2017) (Detailed analysis of the AREPO simulations)
- Companion: (cite: Hull2014) (CARMA TADPOL observations of Ser-emb 8)
- Related: TADPOL

## Checks

```json
{
 "quotes": 43,
 "quotes_ok": 43,
 "quote_pass_rate": 1.0,
 "quotes_too_long": 0,
 "unsupported_facts": 0,
 "project_codes": 0,
 "codes_not_in_text": [],
 "codes_not_in_obscore": [],
 "obscore_codes_not_in_card": [
  "2013.1.00726.S"
 ],
 "codes_printed_but_missing": [],
 "numeric_results": 4,
 "numeric_problems": 0,
 "fill": {
  "facts": 71,
  "stated": 36,
  "rate": 0.507
 },
 "evidence_ok": true
}
```
