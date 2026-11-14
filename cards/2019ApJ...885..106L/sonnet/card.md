# Characterizing Magnetic Field Morphologies in Three Serpens Protostellar Cores with ALMA

`2019ApJ...885..106L` | The Astrophysical Journal 2019 | first author: Le Gouellec, Valentin J. M. | arXiv: 1909.00046 | DOI: 10.3847/1538-4357/ab43c2

Card schema 1.0 | model claude-sonnet-5-5 | depth full | type observational_alma_primary

## Science

- Fields: star_formation, astrochemistry
- Question: What magnetic field morphologies and grain-alignment processes characterize the Class 0 protostellar cores Serpens SMM1, Emb 8(N) and Emb 8, especially along outflow cavity walls and in inner cores?  
  > "With the aim of characterizing the dynamical processes involved in the formation of young protostars, we present high angular resolution ALMA dust polarization observations" (abstract)
- Target **Serpens SMM1**: coordinates SMM1a 18:29:49.81 +1:15:20.41 (J2000)  
  > "Serpens SMM1a      | 18:29:49.81               | +1:15:20.41" (Table 1); "which are located at a distance of 436 $\pm$ 9 pc (cite: OrtizLeon2017b)" (Introduction); z/distance 436 ± 9 pc  
  > "Serpens SMM1a      | 18:29:49.81               | +1:15:20.41" (Table 1); "which are located at a distance of 436 $\pm$ 9 pc (cite: OrtizLeon2017b)" (Introduction); distance from Ortiz-León et al. 2017  
  > "Serpens SMM1a      | 18:29:49.81               | +1:15:20.41" (Table 1); "which are located at a distance of 436 $\pm$ 9 pc (cite: OrtizLeon2017b)" (Introduction)
- Target **Serpens Emb 8(N)**: coordinates 18:29:48.73 +1:16:55.61 (J2000)  
  > "Serpens Emb 8(N)   | 18:29:48.73               | +1:16:55.61" (Table 1); z/distance 436 ± 9 pc  
  > "Serpens Emb 8(N)   | 18:29:48.73               | +1:16:55.61" (Table 1); distance from Ortiz-León et al. 2017  
  > "Serpens Emb 8(N)   | 18:29:48.73               | +1:16:55.61" (Table 1)
- Target **Serpens Emb 8**: coordinates 18:29:48.09 +1:16:43.30 (J2000)  
  > "Serpens Emb 8      | 18:29:48.09               | +1:16:43.30" (Table 1); z/distance 436 ± 9 pc  
  > "Serpens Emb 8      | 18:29:48.09               | +1:16:43.30" (Table 1); distance from Ortiz-León et al. 2017  
  > "Serpens Emb 8      | 18:29:48.09               | +1:16:43.30" (Table 1)

## Data provenance

- ALMA projects: 2013.1.00726.S, 2015.1.00768.S, 2016.1.00710.S, 2017.1.01174.S
- bands: Band 7 (870 um) polarization; Band 6 (1.3 mm) and Band 3 (3 mm) lines  
  > "Finally we present 1.3 mm (Band 6) and 3 mm (Band 3) ALMA spectral-line data" (2 ALMA Observations and Data Reduction)
- frequencies and spectral setup: four 2 GHz spectral windows, 336.5-350.5 GHz  
  > "Each dataset consists of four spectral windows of 2 GHz each, ranging in frequency from 336.5 GHz to 350.5 GHz." (2 ALMA Observations and Data Reduction)
- continuum bandwidth: _not stated_
- arrays: _not stated_
- configurations: _not stated_
- baselines: A: 16.5-763 m; B: 12.4-3042 m; C: 11.7-3320 m  
  > "| A       | 16.5 - 763  | phase    | J1751+0939  |" (Table 2)
- angular resolution: 0.33" to 0.11" (~144 au to ~48 au)  
  > "The synthesized beam of our observations varies from 0$\ensuremath{''}$33 to 0$\ensuremath{''}$11" (2 ALMA Observations and Data Reduction)
- max recoverable scale: dataset C recovers 0.11" to ~1.3"  
  > "dataset C recovered angular scales from 0$\ensuremath{''}$11 to $\sim$ $1\ensuremath{''}$3" (3 Results)
- sensitivity: _not stated_
- time on source: _not stated_
- observing dates: 2015 June 3 & 7; 2016 Sept 12 & 13; 2017 July 31 (polarization)  
  > "were taken on 2015 June $3\,\&\,7$, 2016 September $12\,\&\,13$, and 2017 July $31^{st}$" (2 ALMA Observations and Data Reduction)
- pi or archival as stated: PI: C. Hull  
  > "(ALMA projects: 2013.1.00726.S, 2015.1.00768.S, 2016.1.00710.S; PI: C. Hull)" (2 ALMA Observations and Data Reduction)
- Line: CO J=2-1 (not stated)
- Line: 13CS J=5-4 (not stated)
- Line: C18O J=2-1 (not stated)
- Line: DCO+ J=3-2 (not stated)
- External data: Dust opacity table (kappa at 1 mm = 2.74 cm2/g, etc.)  
  > "$\kappa_{1\textrm{mm}}\,=\,2.74\,\textrm{cm}^2\,\textrm{g}^{-1}$" (Footnote 8) [from Ossenkopf & Henning 1994 (cite: Ossenkopf1994)]
- External data: Dust temperature ~20 K  
  > "the estimated dust temperature $T_\textrm{d}\,\approx\,20$K (cite: Hull2017b)" (4.4) [from (cite: Hull2017b)]
- External data: SMM1 inclination 50 deg  
  > "(cite: Yildiz2015) estimate an inclination of 50$^\circ$ with respect to the line of sight" (4.1.2) [from (cite: Yildiz2015)]

## Processing

### Calibration

- pipeline or manual: _not stated_
- casa version: _not stated_
- pipeline version: _not stated_
- archive products used as is: _not stated_
- flux calibrator: Titan (A), J1751+0939 (B); C see table note  
  > "|         |             | flux     | Titan       |" (Table 2)
- flux scale uncertainty: 10% in Band 7  
  > "The ALMA flux calibration accuracy in Band 7 (870$\mu$m) is 10$\%$." (2 ALMA Observations and Data Reduction)
- self calibration: four rounds of phase-only self-calibration; Stokes I solutions applied to Q and U  
  > "applying four rounds of consecutive phase-only self-calibration, using the total intensity (Stokes $I$) solutions as a model for the Stokes $Q$ and $U$" (2 ALMA Observations and Data Reduction)

### Imaging

- task: CASA clean  
  > "The polarized dust continuum images were produced by using the CASA task `clean`" (2 ALMA Observations and Data Reduction)
- deconvolver: _not stated_
- weighting robust: Briggs robust = 1  
  > "with a Briggs weighting parameter of robust = 1" (2 ALMA Observations and Data Reduction)
- uv taper: _not stated_
- cell size: _not stated_
- image size: _not stated_
- masking: _not stated_
- multiscale scales: _not stated_
- continuum subtraction: _not stated_
- line free channels: _not stated_
- primary beam correction: applied to all I and P maps  
  > "we performed a primary beam correction on all the total intensity and polarized intensity maps presented in this article." (2 ALMA Observations and Data Reduction)
- array combination: datasets combined in three schemes (A, AC, ABC, BC etc.)  
  > "the datasets were combined together following three different schemes during the production of the Stokes images" (2 ALMA Observations and Data Reduction)
- smoothing: imsmooth to common beam for I, Q, U in Case-3  
  > "we used the `imsmooth` CASA task to smooth the three Stokes parameters $I$, $Q$, and $U$ to have the same reconstructed beam" (2 ALMA Observations and Data Reduction)
- final beam: 0.35x0.32" (A) to 0.13x0.13" (Case-3 SMM1)  
  > "| Ser-Emb 8 | A | A | 0.35 $\times$ 0.32 | 102 |" (Table 3)
- final rms: _not stated_

### Inherited from earlier work

- Polarized intensity debiasing method  
  > "following the method described in (cite: Vaillancourt2006; Hull2015b)" (2 ALMA Observations and Data Reduction) [from (cite: Vaillancourt2006; Hull2015b)]
- Penetration-depth procedure for UV and longer-wavelength photons  
  > "Following the procedure of (cite: Hull2019), we estimate the depth to which UV and longer-wavelength photons can penetrate" (4.4) [from (cite: Hull2019)]
- CO outflow integration ranges including EHV component  
  > "see (cite: Tychoniec2019) for details." (Footnote 4) [from (cite: Tychoniec2019)]

### Not stated but needed to reproduce (our reading)

- Line-free channels and continuum bandwidth used for continuum imaging
- Image size, cell size, clean masks and thresholds, number of iterations
- Self-calibration solution intervals
- CASA version and whether pipeline or manual calibration was used
- Flux and phase calibrators for dataset C (only 'see note')
- Exact Stokes I/Q/U combinations and uv ranges per case
- CO and other line imaging parameters and moment velocity ranges
- Rotation applied to polarization angles
- UVMULTIFIT fit details and Band 3 continuum data

## Analysis recipe

1. **Produce Stokes I, Q, U images**: CASA clean with four rounds of phase-only self-calibration, I solutions applied to Q and U, datasets combined in three schemes  
  > "applying four rounds of consecutive phase-only self-calibration, using the total intensity (Stokes $I$) solutions as a model for the Stokes $Q$ and $U$" (2 ALMA Observations and Data Reduction)
   - software: CASA
   - parameter: robust = 1  
  > "with a Briggs weighting parameter of robust = 1" (2 ALMA Observations and Data Reduction)
   - fitting: _not stated_
   - validation: _not stated_
2. **Derive polarization quantities**: compute P, Pfrac, chi from Q,U,I; debias P; smooth to common beam; keep Pfrac where P>3sigma_P and I>5sigma_I  
  > "we considered only emission within the zones of 3$\sigma_P$ and 5$\sigma_I$" (3.1)
   - software: CASA
   - fitting: _not stated_
   - validation: _not stated_
3. **Test grain alignment mechanisms in inner core**: histogram of relative orientation between B-field and Stokes I gradient; spectral index from UVMULTIFIT 2D Gaussian fits to Band 3 and Band 7 visibilities; brightness temperature  
  > "we fit a single 2D-Gaussian component model to the visibilities of our datasets using the UVMULTIFIT tool" (4.1.1)
   - software: UVMULTIFIT
   - parameter: gradient selection >1/100x(peak-rms) for moment 0 maps, >1/1000x(peak-rms) for continuum; Nyquist sampling 4 points per beam  
  > "we consider only gradients \> 1/100 $\times$ (peak – rms) for the moment 0 maps, and \> 1/1000 $\times$ (peak – rms) for the dust continuum maps" (Appendix)
   - assumption: Stokes I gradient as proxy for radiation field  
  > "we use the Stokes $I$ gradient map as a proxy for the radiation field." (4.1.1)
   - fitting: _not stated_
   - validation: _not stated_
4. **Estimate gas mass and column density in Emb 8(N) cavity wall and photon penetration depths**: M_gas = S d^2/(kappa B(Td)); N_H2 = M/(mu m_H A); tau=1 path length s=1/(kappa rho_dust)  
  > "We derive the column density in the cavity wall of Emb 8(N) as follows" (4.4)
   - parameter: d = 440 pc, Td 20 K and 100 K, kappa(1 mm)=2.74 cm2/g, 343.5 GHz  
  > "the distance $d= 440$ pc, the estimated dust temperature $T_\textrm{d}\,\approx\,20$K" (4.4)
   - assumption: gas-to-dust ratio 100; mu_H2 = 2.8  
  > "We assume a gas-to-dust ratio of 100." (4.4)
   - fitting: _not stated_
   - validation: _not stated_

## Software

- **CASA** : clean, self-calibration, imsmooth  
  > "The polarized dust continuum images were produced by using the CASA task `clean`" (2 ALMA Observations and Data Reduction)
- **UVMULTIFIT** : 2D Gaussian visibility fits for spectral index  
  > "we fit a single 2D-Gaussian component model to the visibilities of our datasets using the UVMULTIFIT tool" (4.1.1)
- **APLpy** : plotting  
  > "*Software:* APLpy, an open-source plotting package for Python" (Acknowledgments)
- **Astropy** : listed software  
  > "Astropy (cite: Astropy2018)." (Acknowledgments)

## Numeric results

| quantity | value | uncertainty | units | step | quote |
|---|---|---|---|---|---|
| Max polarization fraction along Emb 8(N) blueshifted northern cavity wall | 36% at 1150 au (30% at 690 au) | not stated | percent | 2 | reaches 30$\%$ at 690 au and 36$\%$ at 1150 au from the center of the protostar |
| Peak polarization fraction in SMM1-a inner core | 6 | not stated | percent | 2 | (achieving a maximum of 6%) |
| Spectral index of Emb 8 inner core | 3.36 | not stated | dimensionless | 3 | given the spectral index of its inner core ($\alpha \approx 3.36$) |
| Peak brightness temperature SMM1-a | 101 | not stated | K | 3 | The brightness temperature peaks at 101 K |
| Column density in Emb 8(N) cavity wall | 3.4e22 (100 K) to 2.5e23 (20 K) | not stated | cm^-2 | 4 | we obtain column density values between $\sim\,3.4\,\times\,10^{22}\,\textrm{cm}^{-2}$ and $\sim\,2.5\,\times\,10^{23}\,\textrm{cm}^{-2}$ |
| Penetration depth of 100 um photons | ~200 au (20 K), ~1400 au (100 K) | not stated | au | 4 | For 100 $\mu$m photons, the depths are $\sim$ 200 au and $\sim$ 1400 au. |

## Qualitative findings

- SMM1-a inner core shows poloidal field aligned with outflow; two polarized filaments south, one possibly an accretion streamer  
  > "The other may be an accretion streamer of material infalling onto the central protostar." (abstract)

## Claim tuples

- H: Is the polarization in inner cores due to k-RATs or self-scattering? | E: HRO vs Stokes I gradient, spectral index, brightness temperature, comparison with models | R: broad HRO distribution, polarization pattern inconsistent with models | F: neither self-scattering nor k-RATs occurs; B-RATs assumed dominant | **supported**
- H: Does the magnetic field follow outflow cavity walls? | E: HRO of B-field vs dust and CO gradients | R: HRO peaks near 90 deg in Emb 8(N) | F: field aligned along cavity walls | **supported**
- H: What enables enhanced polarization along cavity walls? | E: gas column density and photon penetration depth estimates | R: UV cannot penetrate deep; ~300 au thick polarized wall | F: large (>10 um) grains aligned by longer-wavelength photons required | **partially**

## Reasoning

- Why this data: _not stated_
- Why this method: _not stated_
- Alternative: k-RAT alignment and dust self-scattering rejected for inner cores  
  > "we conclude that neither self-scattering nor grain alignment via $k$-RATs is occurring in our sources." (4.1.2)
- How they decided it was enough: _not stated_
- Limitation (authors): cannot disentangle MAT and RAT roles  
  > "our observations are not yet able to disentangle the roles played by each of these two grain alignment mechanisms." (4.3)
- Limitation (authors): column densities are lower limits due to interferometric filtering  
  > "these values of the envelope column density at small scales are at best lower limits" (4.4)
- Caveat (inferred, ours): Mixed dataset combinations give different beams and sensitivities, complicating comparisons
- Caveat (inferred, ours): HRO histograms from few points, not statistically significant in some cases
- Caveat (inferred, ours): Single temperature and opacity assumptions drive penetration depths
- Caveat (inferred, ours): Debiasing and polarization-angle details are unspecified

## Reproducibility

- Data public (paper): ALMA project codes given; public status not stated explicitly  
  > "This paper makes use of the following ALMA data: ADS/JAO.ALMA#2016.1.00710.S, ADS/JAO.ALMA#2013.1.00726.S" (Acknowledgments)
- Products in archive: _not stated_
- Missing: clean parameters, masks, self-cal solints
- Missing: CASA version
- Missing: dataset C calibrators
- Missing: gradient and HRO code details
- Data volume (inferred): ~100-300 GB for three Band 7 polarization datasets plus line data
- Score (inferred): 4/5, Data codes known, recipe partly described but many imaging parameters missing; results mostly maps.
- Rediscovery candidate: no, Recipe incomplete and main results are mostly morphological.

## Links

- Method: Hull & Plambeck 2015 (cite: Hull2015b) (polarization debiasing)
- Method: Martí-Vidal et al. 2014 (cite: MartiVidal2014) (UVMULTIFIT)
- Companion: Hull et al. 2017 (cite: Hull2017b) (earlier SMM1 polarization)
- Companion: Hull et al. 2017 (cite: Hull2017a) (Emb 8 dataset A)
- Companion: Tychoniec et al. 2019 (cite: Tychoniec2019) (Emb 8(N) jet kinematics)
- Related: TADPOL

## Checks

```json
{
 "quotes": 71,
 "quotes_ok": 71,
 "quote_pass_rate": 1.0,
 "quotes_too_long": 0,
 "unsupported_facts": 0,
 "project_codes": 4,
 "codes_not_in_text": [],
 "codes_not_in_obscore": [
  "2017.1.01174.S"
 ],
 "obscore_codes_not_in_card": [],
 "codes_printed_but_missing": [],
 "numeric_results": 6,
 "numeric_problems": 0,
 "fill": {
  "facts": 80,
  "stated": 50,
  "rate": 0.625
 },
 "evidence_ok": true
}
```
