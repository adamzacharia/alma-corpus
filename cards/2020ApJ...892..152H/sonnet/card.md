# Understanding the Origin of the Magnetic Field Morphology in the Wide-binary Protostellar System BHR 71

`2020ApJ...892..152H` | The Astrophysical Journal 2020 | first author: Hull, Charles L. H. | arXiv: 1910.07290 | DOI: 10.3847/1538-4357/ab5809

Card schema 1.0 | model claude-sonnet-5-5 | depth full | type observational_alma_primary

## Science

- Fields: star_formation
- Question: What is the origin of the magnetic field morphologies toward the two components (IRS1, IRS2) of the wide-binary Class 0 system BHR 71?  
  > "with the goal of understanding the origin of the magnetic field morphologies toward the two components of this iconic wide-binary system." (1 Introduction)
- Target **BHR 71 IRS1 and IRS2**: coordinates IRS2 pointing: RA 12:01:34.042, Dec -65:08:47.870 (J2000); IRS1 RA string garbled in text  
  > "that are separated by $\sim$ 15$\ensuremath{''}$, or $\sim$ 3000 au at a distance of 200 pc" (1 Introduction); "The pointing center was ($\alpha_\textrm{J2000}$=:01:36.514, $\delta_\textrm{J2000}$=–65:08:49.31) for IRS1" (2 Observations); z/distance 200 pc  
  > "that are separated by $\sim$ 15$\ensuremath{''}$, or $\sim$ 3000 au at a distance of 200 pc" (1 Introduction); "The pointing center was ($\alpha_\textrm{J2000}$=:01:36.514, $\delta_\textrm{J2000}$=–65:08:49.31) for IRS1" (2 Observations); distance from Seidensticker & Schmidt-Kaler 1989; Bourke et al. 1997  
  > "that are separated by $\sim$ 15$\ensuremath{''}$, or $\sim$ 3000 au at a distance of 200 pc" (1 Introduction); "The pointing center was ($\alpha_\textrm{J2000}$=:01:36.514, $\delta_\textrm{J2000}$=–65:08:49.31) for IRS1" (2 Observations)

## Data provenance

- ALMA projects: 2013.1.00518.S, 2017.1.00655.S
- bands: Band 6 (1.3 mm), full polarization  
  > "We present ALMA observations of dust polarization at 1.3 mm (Band 6) toward BHR 71 taken on 2018 May 03." (2 Observations)
- frequencies and spectral setup: ~223–227 and ~239–243 GHz, mean 233 GHz; 2 GHz spws, 64 channels of 31.25 MHz  
  > "Each 2 GHz spectral window (with 1.875 GHz of usable bandwidth) was divided into 64 channels with widths of 31.25 MHz." (2 Observations)
- continuum bandwidth: 8.0 GHz  
  > "The polarization data include 8.0 GHz of wide-band dust continuum" (2 Observations)
- arrays: _not stated_
- configurations: C-2  
  > "The baselines in the C-2 antenna configuration range from 15–500 m." (2 Observations)
- baselines: 15–500 m  
  > "The baselines in the C-2 antenna configuration range from 15–500 m." (2 Observations)
- angular resolution: 1.10" x 0.89" (robust=2.0), ~200 au; 0.75" and 0.53" for robust 0.5, -0.5  
  > "the maps have a synthesized beam (or resolution element) of 1.10$''$ $\times$ 0.89$''$," (2 Observations)
- max recoverable scale: ~10.6"  
  > "The maximum spatial scale at which emission can be recovered by ALMA is approximately 10.6$''$." (2 Observations)
- sensitivity: Stokes I rms 150–300 uJy/beam; P rms 25–40 uJy/beam  
  > "ranges from 25 $\mu$Jy beam$^{-1}$(`robust` = 2.0, 0.5) to 40 $\mu$Jy beam$^{-1}$(`robust` = –0.5)." (2 Observations)
- time on source: ~100 min  
  > "The observations included $\sim$ 100 min of on-source time" (2 Observations)
- observing dates: 2018 May 03  
  > "taken on 2018 May 03" (2 Observations)
- pi or archival as stated: _not stated_
- Line: CO J=2-1 (not stated)
- Line: C18O J=2-1 (not stated)
- Line: N2D+ J=3-2 (not stated)
- External data: ALMA CO, C18O, N2D+ spectral-line cubes/moment maps of BHR 71  
  > "these include recent ALMA observations of spectral lines by (see Section [1.1](#sec:tobin_obs))" (1 Introduction) [from Tobin et al. 2019 (cite: Tobin2019)]
- External data: Dust temperatures 34 K (IRS1), 20 K (IRS2); luminosities 14.7 and 1.7 Lsun; outflow inclinations ~50–60 deg  
  > "Assuming dust temperatures of 34 K for IRS1 and 20 K for IRS2" (1.1 Previous observations) [from Tobin et al. 2019 (cite: Tobin2019)]
- External data: Dust opacity at 1.3 mm kappa = 2 cm2/g  
  > "the dust opacity at 1.3 mm $\kappa_{\nu} = 2\,\mathrm{cm}^2/\mathrm{g}$ (cite: Ossenkopf1994)" (4.3) [from Ossenkopf & Henning 1994 (cite: Ossenkopf1994)]
- External data: Synthetic Q and U hourglass models used for inclination comparison  
  > "synthetic models of $Q$ and $U$ for an hourglass-shaped magnetic field morphology shown in (cite: Frau2011)" (3 Results) [from Frau et al. 2011 (cite: Frau2011)]

## Processing

### Calibration

- pipeline or manual: _not stated_
- casa version: _not stated_
- pipeline version: _not stated_
- archive products used as is: _not stated_
- flux calibrator: J1107-4449 (flux and bandpass); J1256-0547 polarization; J1206-6138 phase  
  > "The flux and bandpass calibrator was J1107-4449; the polarization calibrator was J1256-0547; and the phase calibrator was J1206-6138." (2 Observations)
- flux scale uncertainty: ~10% at Band 6  
  > "ALMA’s systematic flux-calibration accuracy is $\sim$ 10%." (2 Observations)
- self calibration: Four rounds of phase-only self-cal using Stokes I model; shortest solint 12 s  
  > "All images were improved by performing four rounds of phase-only self-calibration, where the total intensity (Stokes $I$) image was used as a model." (2 Observations); "The shortest interval for determining the gain solutions was 12 s." (2 Observations)

### Imaging

- task: CASA TCLEAN (two-point mosaic) and CLEAN (single pointings)  
  > "We produced the dust continuum images using the Common Astronomy Software Applications (CASA, (cite: McMullin2007)) tasks `TCLEAN` and `CLEAN`." (2 Observations)
- deconvolver: _not stated_
- weighting robust: robust = 2.0 (main), 0.5, -0.5  
  > "we also made higher resolution images Briggs weighting parameters of `robust` = 0.5 and –0.5" (2 Observations)
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
- final beam: 1.10" x 0.89" at robust 2.0  
  > "the maps have a synthesized beam (or resolution element) of 1.10$''$ $\times$ 0.89$''$," (2 Observations)
- final rms: I: 150–300 uJy/beam; P: 25–40 uJy/beam  
  > "to 150 $\mu$Jy beam$^{-1}$ (`robust` = 2.0; single pointing toward IRS2)." (2 Observations)

### Inherited from earlier work

- HRO analysis procedure details  
  > "For further details of this HRO analysis, see (cite: LeGouellec2019a)." (4.5) [from (cite: LeGouellec2019a)]
- Polarized intensity debiasing  
  > "We debias the polarized intensity map as described in (cite: Vaillancourt2006) and (cite: Hull2015b)" (2 Observations) [from (cite: Vaillancourt2006); (cite: Hull2015b)]
- Flux-to-gas-mass conversion  
  > "we use the standard conversion from flux density $S_{\nu}$ to gas mass $M_{\mathrm{gas}}$ (cite: Hull2017b; HullZhang2019):" (4.3) [from (cite: Hull2017b; HullZhang2019)]

### Not stated but needed to reproduce (our reading)

- CASA version
- Mosaic and single-pointing clean thresholds, masks, niter, cell and image sizes
- Self-calibration solint sequence beyond the shortest 12 s
- Deconvolver and uv-taper settings
- Line cube imaging parameters for CO, C18O, N2D+ (from Tobin et al. 2019)
- Debiasing and polarization-vector sampling/S/N cuts for figures
- HRO gradient computation details

## Analysis recipe

1. **Image Stokes I, Q, U with self-calibration**: Phase-only self-cal using Stokes I model, then independent cleaning of I, Q, U; mosaic and single-pointing images at three robust values  
  > "The Stokes $I$, $Q$, and $U$ maps (where the $Q$ and $U$ maps show the polarized emission) were independently cleaned" (2 Observations)
   - software: CASA
   - parameter: robust = 2.0, 0.5, -0.5; 4 self-cal rounds  
  > "All images were improved by performing four rounds of phase-only self-calibration" (2 Observations)
   - fitting: _not stated_
   - validation: _not stated_
2. **Derive polarization quantities**: Compute P, Pfrac, chi from Q, U, I; debias P; B-field = chi rotated by 90 deg  
  > "We debias the polarized intensity map as described in (cite: Vaillancourt2006) and (cite: Hull2015b)" (2 Observations)
   - fitting: _not stated_
   - validation: Circular polarization checked: ~0.08% of I, below 0.6% systematic, likely spurious  
  > "the circular polarization fraction in the on-axis (single-pointing, non-mosaicked) observations of IRS1 is $\sim$ 0.08% of the total intensity" (2 Observations)
3. **Constrain IRS1 field inclination**: By-eye comparison of Q, U maps with Frau et al. 2011 hourglass models  
  > "By comparing by eye with the synthetic models of $Q$ and $U$ for an hourglass-shaped magnetic field morphology shown in (cite: Frau2011)" (3 Results)
   - fitting: _not stated_
   - validation: Consistent with inclination estimates of Tobin 2019 and Yang 2017  
  > "This is consistent with the inclination estimates by both and (cite: YLYang2017)." (3 Results)
4. **Estimate column density along IRS2 cavity wall**: Gas mass from flux density in a 300 au circle (2.5 mJy) with Planck function at 20 K or 300 K  
  > "assume an average flux of 2.5 mJy in a 300 au-diameter circle centered on the outflow cavity wall." (4.3)
   - parameter: nu = 233 GHz, d = 200 pc, kappa = 2 cm2/g, Td = 20 K or 300 K  
  > "the distance $d=200$ pc, and the dust opacity at 1.3 mm $\kappa_{\nu} = 2\,\mathrm{cm}^2/\mathrm{g}$ (cite: Ossenkopf1994)" (4.3)
   - assumption: Gas-to-dust ratio 100; mean molecular weight 2.8  
  > "We assume a gas-to-dust ratio of 100." (4.3)
   - fitting: _not stated_
   - validation: Compared with UV extinction at A_V~1 (1e21–1e22 cm-2)  
  > "UV radiation is fully extincted at an $A_V$ of order unity, which is achieved at a molecular hydrogen column density of between 10$^{21}$ and 10$^{22}$ cm$^{-2}$" (4.3)
5. **Photon penetration depths in cavity wall**: Path length s = 1/(kappa rho) to tau=1 using Ossenkopf & Henning opacities for 1e6 cm-3 gas, no ice mantles  
  > "the path length $s$ to the point where the optical depth $\tau = 1$ can be calculated simply as $s = 1 / \kappa_\nu \rho$." (4.3)
   - assumption: Constant opacity and dust mass density across the wall  
  > "Assuming a constant opacity $\kappa_\nu$ and mass density $\rho$ of the dust grains throughout the thickness of the cavity wall" (4.3)
   - fitting: _not stated_
   - validation: _not stated_
6. **Histogram of Relative Orientation**: HRO of B-field vs gradients of Stokes I (I>3 sigma) and CO moment 0 (10 sigma threshold), where P>3 sigma_P  
  > "for the locations where there is both a gradient value as well as a magnetic field orientation (i.e., where $P > 3$ $\sigma_P$), we derived $\phi$" (4.5)
   - fitting: _not stated_
   - validation: _not stated_

## Software

- **CASA** : calibration, self-calibration and imaging with TCLEAN/CLEAN  
  > "We produced the dust continuum images using the Common Astronomy Software Applications (CASA, (cite: McMullin2007)) tasks `TCLEAN` and `CLEAN`." (2 Observations)
- **APLpy** : plotting  
  > "APLpy, an open-source plotting package for Python hosted at <http://aplpy.github.com> (cite: Robitaille2012)." (Acknowledgments)
- **Astropy** : listed in software acknowledgment  
  > "Astropy (cite: Astropy2018)." (Acknowledgments)

## Numeric results

| quantity | value | uncertainty | units | step | quote |
|---|---|---|---|---|---|
| Synthesized beam (robust=2.0) | 1.10 x 0.89 | not stated | arcsec | 1 | 1.10$''$ $\times$ 0.89$''$, |
| Stokes I rms (mosaic, robust 2.0) | 300 | not stated | uJy/beam | 1 | $\sigma_I \approx 300$ $\mu$Jy beam$^{-1}$ (`robust` = 2.0; mosaic) |
| IRS1 field inclination to plane of sky | ~60 | not stated | deg | 3 | which is equivalent to a $\sim$ 60$\degree$ inclination of the source with respect to the plane of the sky. |
| IRS2 cavity wall column density (Td=20 K) | 2.6e22 | not stated | cm^-2 | 4 | The resulting column density is $\sim$ $2.6 \times 10^{22}$ cm$^{-2}$. |
| IRS2 cavity wall column density (Td=300 K) | 1.3e21 | not stated | cm^-2 | 4 | the column density we derive is $\sim$ $1.3 \times 10^{21}$ cm$^{-2}$. |
| Penetration depth of 10 um photons (20 K, 300 K) | ~70 and ~1400 | not stated | au | 5 | For 10 $\ensuremath{\mu}m$ photons, the depths are $\sim$ 70 au and $\sim$ 1400 au. |
| Width of polarized lane along IRS2 cavity | ~300 | not stated | au | 0 | is marginally resolved, with an average thickness of $\sim$ 300 au. |
| Width of NE polarized streamer feature in IRS1 | ~50 | not stated | au | 0 | have similar widths of $\sim$ 50 au. |

## Qualitative findings

- IRS1 has a natal hourglass field; IRS2 field is shaped by its outflow, with polarization confined to cavity walls  
  > "IRS1 has what appears to be a natal, hourglass-shaped magnetic field. In contrast, its fainter, more embedded binary counterpart IRS2 exhibits a magnetic field that has been affected by its bipolar outflow." (5 Conclusions)
- N2D+ is anticorrelated with polarization, tracing cold unpolarized gas  
  > "this species (and its non-deuterated counterpart N$_2$H$^+$) is an excellent tracer of unpolarized material" (5 Conclusions)

## Claim tuples

- H: Do IRS1 and IRS2 have different magnetic field origins? | E: Compare polarization maps with CO outflow, C18O and N2D+ maps and HROs | R: IRS1 hourglass aligned with but not shaped by outflow; IRS2 polarization along cavity walls | F: IRS1 natal hourglass; IRS2 outflow-affected field | **supported**
- H: What aligns grains in IRS2 cavity walls? | E: Column density and photon penetration depth estimates | R: UV cannot penetrate 300 au; MIR/FIR photons can | F: MIR/FIR photons imply grain growth ('thick' scenario favoured), though not conclusive | **partially**
- H: Is the NE linear feature in IRS1 an accretion streamer? | E: Examine multi-resolution polarization map and compare with kinematics | R: Narrow, 10–20% polarized feature not tied to outflow; no streamer in N2D+/C18O kinematics | F: Speculated magnetized streamer; unconfirmed | **partially**

## Reasoning

- Why this data: _not stated_
- Why this method: _not stated_
- Alternative: MAT (mechanical alignment) by the outflow for IRS2 polarization is unlikely because the redshifted lobe is offset from the polarized emission  
  > "we find it unlikely that the action of the outflow itself is producing the polarization via MATs." (Footnote 3)
- Alternative: 'Thin' layer scenario disfavoured due to high polarization fractions  
  > "Given the major caveat of the polarization fraction levels in the “thin” case" (4.3)
- How they decided it was enough: _not stated_
- Limitation (authors): Stokes I is dynamic-range limited, which limits interpretation of polarization fraction  
  > "our ability to interpret $P_\textrm{frac}$ is limited by the fact that the Stokes $I$ image is much more strongly dynamic-range limited than the $P$ image" (3 Results)
- Caveat (inferred, ours): Polarization mechanism arguments are qualitative; no radiative transfer or RAT modeling
- Caveat (inferred, ours): Inclination from by-eye model comparison
- Caveat (inferred, ours): Column density depends strongly on assumed dust temperature
- Caveat (inferred, ours): HRO has limited statistics for the redshifted lobe

## Reproducibility

- Data public (paper): ALMA projects listed in acknowledgments; public availability not explicitly stated  
  > "This paper makes use of the following ALMA data: ADS/JAO.ALMA#2013.1.00518.S and ADS/JAO.ALMA#2017.1.00655.S." (Acknowledgments)
- Products in archive: _not stated_
- Missing: CASA version and clean parameters
- Missing: Self-cal details beyond shortest solint
- Missing: Spectral-line cube processing (from Tobin et al. 2019)
- Missing: HRO implementation details
- Data volume (inferred): ~50–100 GB for polarization data plus line data
- Score (inferred): 3/5, Observation setup and imaging are described, but many clean/self-cal parameters and the HRO details are missing; results are largely morphological.
- Rediscovery candidate: no, Main results are mostly qualitative morphology; the recipe is incomplete.

## Links

- Method: Brogan et al. 2018 (cite: Brogan2018) (Self-calibration best practices)
- Method: Nagai et al. 2016 (cite: Nagai2016) (ALMA polarization system)
- Method: Soler et al. 2013 (cite: Soler2013) (HRO method)
- Companion: Tobin et al. 2019 (cite: Tobin2019) (ALMA spectral-line data and source properties of BHR 71)
- Companion: Le Gouellec et al. 2019 (cite: LeGouellec2019a) (HRO analysis details; Serpens comparison)
- Related: VANDAM

## Checks

```json
{
 "quotes": 71,
 "quotes_ok": 71,
 "quote_pass_rate": 1.0,
 "quotes_too_long": 0,
 "unsupported_facts": 0,
 "project_codes": 2,
 "codes_not_in_text": [],
 "codes_not_in_obscore": [],
 "obscore_codes_not_in_card": [],
 "codes_printed_but_missing": [],
 "numeric_results": 8,
 "numeric_problems": 0,
 "fill": {
  "facts": 80,
  "stated": 50,
  "rate": 0.625
 },
 "evidence_ok": true
}
```
