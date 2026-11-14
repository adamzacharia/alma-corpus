# [N II] Fine-structure Emission at 122 and 205 μm in a Galaxy at z = 2.6: A Globally Dense Star-forming Interstellar Medium

`2020ApJ...905..152D` | The Astrophysical Journal 2020 | first author: Doherty, M. J. | arXiv: 2010.15128 | DOI: 10.3847/1538-4357/abc5b9

Card schema 1.0 | model claude-sonnet-5-5 | depth full | type observational_alma_primary

## Science

- Fields: high_z_galaxies
- Question: What is the average electron density of the ionised ISM in the lensed SMG 9io9 at z=2.6, from the [N II] 122/205 micron line ratio, and how does it relate to the dense molecular gas?  
  > "The 122-/205-$\mu$m [N ii] line ratio is sensitive to electron density, $n_{\rm e}$, in the ionised interstellar medium, and we use this to measure $n_{\rm e}\approx 300\,\text{cm}^{-3}$ averaged across the galaxy." (abstract)
- Target **9io9**: coordinates 02h09m41.3s, +00d15m58.5s  
  > "9io9 ($02^{\rm h}09^{\rm m}41.3s$, $00\ensuremath{^\circ}15\ensuremath{'}58.5\ensuremath{''}$, $z=2.5543$)" (Observations); "Even after taking into account the 15$\times$ magnification factor" (Introduction); z/distance z = 2.5543; magnification about 15x  
  > "9io9 ($02^{\rm h}09^{\rm m}41.3s$, $00\ensuremath{^\circ}15\ensuremath{'}58.5\ensuremath{''}$, $z=2.5543$)" (Observations); "Even after taking into account the 15$\times$ magnification factor" (Introduction); distance from _not stated_

## Data provenance

- ALMA projects: 2017.1.00814.S
- bands: Bands 4, 8, 9 (new data: Bands 8 and 9)  
  > "The details of the Band 4 observations are presented in (cite: geach_magnified_2018), and here we present the new Band 8 and 9 data." (Observations)
- frequencies and spectral setup: Band 8: four SPWs at 397.466, 399.404, 409.481, 411.481 GHz; Band 9: eight SPWs from 670.311 to 692.138 GHz  
  > "The central frequencies of the four spectral windows were 397.466, 399.404, 409.481 and 411.481 GHz" (Observations); "eight spectral windows at 670.311, 672.249, 674.249, 676.202, 686.248, 688.201, 690.200 and 692.138 GHz" (Observations)
- continuum bandwidth: _not stated_
- arrays: ALMA 12-m array  
  > "was observed with the ALMA 12-m array in project 2017.1.00814.S in Bands 4, 8 and 9." (Observations)
- configurations: Band 8: C43-4 (47 antennas); Band 9: C43-3 (46 antennas)  
  > "The antenna configuration was C43–4 (with 47 antennas), with a maximum baseline of 783 m." (Observations); "The antenna configuration was C43–3 (with 46 antennas), with a maximum baseline of 484 m." (Observations)
- baselines: Max baseline 783 m (Band 8), 484 m (Band 9)  
  > "with a maximum baseline of 484 m" (Observations)
- angular resolution: Natural weighting beams 0.43x0.35 arcsec (Band 8), 0.32x0.28 arcsec (Band 9); tapered to 0.6 arcsec  
  > "With natural weighting, the synthesised beams were $0.43\ensuremath{''} \times 0.35\ensuremath{''}$ (FWHM, position angle $33\ensuremath{^\circ}$)" (Observations)
- max recoverable scale: LAS <~ 3-4 arcsec  
  > "(LAS $\lesssim$3–4$''$)" (Observations)
- sensitivity: Band 8: 3 mJy/beam per 15.6-MHz channel; Band 9: 10 mJy/beam per 15.6-MHz channel  
  > "resulting in an r.m.s. noise of 3 mJy beam$^{-1}$ in a 15.6-MHz channel" (Observations); "resulting in an r.m.s. noise of 10 mJy beam$^{-1}$ in a 15.6-MHz channel" (Observations)
- time on source: Band 8: 42 min; Band 9: 31 min  
  > "the total on-source integration time was 42 min" (Observations); "The total time on-source was 31 min" (Observations)
- observing dates: Band 8: 2018 Aug 26 and Sep 07; Band 9: 2018 Aug 19  
  > "The Band 8 observations were conducted on 2018 August 26 and 2018 September 07" (Observations); "The Band 9 observations were conducted on 2018 August 19 in a single 70-min execution block." (Observations)
- pi or archival as stated: _not stated_
- Line: [N II] 3P1-3P0 (205 um) (1461.131 GHz)
- Line: [N II] 3P2-3P1 (122 um) (2459.380 GHz)
- External data: Band 4 ALMA data with CO(4-3) and CI(1-0) lines and the lens model of 9io9  
  > "The details of the Band 4 observations are presented in (cite: geach_magnified_2018)" (Observations) [from (cite: geach_magnified_2018)]
- External data: N+ collision rate coefficients at Te = 8000 K  
  > "Using collision rates from (cite: tayal_electron_2011) for a kinetic temperature, $T_{\text e} = 8000$ K" (Electron density) [from (cite: tayal_electron_2011)]

## Processing

### Calibration

- pipeline or manual: Band 8: pipeline-restored calibrated MS; Band 9: manual re-calibration, flagging antennas DA64 and DA24  
  > "For the Band 8 data we used the pipeline-restored calibrated measurement set." (Observations); "due to unstable phases in two antennas (DA64 and DA24) we re-calibrated manually" (Observations)
- casa version: _not stated_
- pipeline version: _not stated_
- archive products used as is: Band 8 pipeline-restored calibrated measurement set used  
  > "For the Band 8 data we used the pipeline-restored calibrated measurement set." (Observations)
- flux calibrator: _not stated_
- flux scale uncertainty: _not stated_
- self calibration: _not stated_

### Imaging

- task: CASA tclean (v.5.1.0-74.el7)  
  > "We imaged and cleaned the data using the casa (v.5.1.0-74.el7) task, `tclean`." (Observations)
- deconvolver: multi-scale clean at scales 0, 0.5, 1.25 arcsec  
  > "we employ multi-scale cleaning (at scales of $0\ensuremath{''}, 0.5\ensuremath{''},$and$, 1.25\ensuremath{''}$)" (Observations)
- weighting robust: natural weighting  
  > "With natural weighting, the synthesised beams were" (Observations)
- uv taper: 0.6 arcsec  
  > "we also produce *uv*-tapered maps with a scale of 0.6$''$" (Observations)
- cell size: _not stated_
- image size: _not stated_
- masking: dirty cubes to set per-channel rms, then clean to 3 sigma threshold  
  > "First we produce dirty cubes to establish the r.m.s. (1$\sigma$) noise per channel, and then clean down to a threshold of 3$\sigma$." (Observations)
- multiscale scales: _not stated_
- continuum subtraction: per-pixel linear fit (free gradient and normalisation) to line-free regions of the cube  
  > "Subtracting the continuum model from each pixel based on a linear fit to line free regions of the lines corresponding data cube allowing the gradient and normalisation vary as free parameters" (Line and continuum measurements)
- line free channels: _not stated_
- primary beam correction: _not stated_
- array combination: _not stated_
- smoothing: _not stated_
- final beam: 0.43x0.35 arcsec (Band 8), 0.32x0.28 arcsec (Band 9) natural; source-plane average beam 280 mas (2.3 kpc)  
  > "The resulting source plane reconstruction has an average beam size of $280\,\text{mas}$ (FWHM) corresponding to a physical scale of 2.3 kpc in the source plane." (Lens model)
- final rms: _not stated_

### Inherited from earlier work

- Multi-scale cleaning approach  
  > "As in (cite: geach_magnified_2018), we employ multi-scale cleaning" (Observations) [from (cite: geach_magnified_2018)]
- Lens model (two-galaxy potential, semi-linear inversion)  
  > "We adopt the same lens model as (cite: geach_magnified_2018)." (Lens model) [from (cite: geach_magnified_2018)]
- Rate-equation formalism for [N II] levels  
  > "Following (cite: goldsmith_herschel_2015), the rate equations can be written" (Electron density) [from (cite: goldsmith_herschel_2015)]

### Not stated but needed to reproduce (our reading)

- Lens model parameters and the source-plane reconstruction code/setup (in Geach et al. 2018)
- Cell size, image size, channel width and velocity resolution of the cubes
- Line-free channel ranges used for continuum fitting
- Modified blackbody details: beta/Td fit results, fit method, rest-frame wavelengths and flux errors
- Flux calibrator and flux scale uncertainty
- Band 9 manual calibration details
- Source-plane mask construction and how the 3 sigma region was defined for the ratio
- How the n_e uncertainty was propagated from the flux errors
- Data and sources used for Fig. 4 literature comparison

## Analysis recipe

1. **Calibrate and image Band 8/9 cubes**: Pipeline-restored data (Band 8) or manual recalibration (Band 9), tclean multiscale, natural weighting, plus 0.6 arcsec taper  
  > "We imaged and cleaned the data using the casa (v.5.1.0-74.el7) task, `tclean`." (Observations)
   - software: CASA
   - parameter: clean to 3 sigma; scales 0, 0.5, 1.25 arcsec  
  > "then clean down to a threshold of 3$\sigma$" (Observations)
   - fitting: _not stated_
   - validation: uv plane well sampled, negligible extended-emission losses expected  
  > "we expect negligible losses to extended emission on the scale of the lens" (Observations)
2. **Reconstruct source-plane cubes**: Semi-linear inversion with the Geach et al. 2018 lens model; each slice reconstructed with 50 randomised Voronoi grids, averaged weighted by log-likelihood  
  > "Each slice was reconstructed with 50 realisations of a randomised Voronoi source plane grid (cite: dye_modelling_2018) and the mean taken, weighted by the log of the likelihood of each realisation." (Lens model)
   - parameter: 50 Voronoi realisations per slice  
  > "Each slice was reconstructed with 50 realisations of a randomised Voronoi source plane grid" (Lens model)
   - assumption: Errors exclude systematic uncertainty of the parametric lens model  
  > "The errors quoted for the intrinsic source properties do not include any systematic uncertainty introduced by the prescribed parametric lens model" (Lens model)
   - fitting: _not stated_
   - validation: _not stated_
3. **Measure L_IR from continuum SED**: Single-temperature modified blackbody fit with free beta, Td, normalisation; luminosity summed within the 3 sigma Band 8 contour in the source plane  
  > "We fit the observed emission with a single-temperature modified blackbody spectrum, allowing the dust emissivity ($\beta$), dust temperature ($T_{\rm d}$) and normalisation to be free parameters." (Line and continuum measurements)
   - parameter: L_IR defined at rest-frame 8-1000 um  
  > "we can estimate $L_{\rm IR}$ (rest-frame 8–1000 $\mu$m)" (Line and continuum measurements)
   - fitting: _not stated_
   - validation: _not stated_
4. **Measure [N II] line fluxes and luminosities**: Subtract linear continuum per pixel, integrate within the 3 sigma mask, convert with the Solomon et al. 1997 relation; Monte Carlo errors by adding Gaussian noise (1000 realisations)  
  > "Repeating this 1000 times and integrating the lines for each realisation allows us to estimate the uncertainties." (Line and continuum measurements)
   - parameter: 122 um integrated over -500 to 300 km/s because lines are incomplete  
  > "integrating between $-500~\text{km}~\text{s}^{-1}$ and $300~\text{km}~\text{s}^{-1}$ due to the [N ii] lines being incomplete" (Line and continuum measurements)
   - assumption: About 10% of line flux missed for both lines, so the ratio is unaffected  
  > "we estimate we are missing $\approx 10\%$ of the total line flux for both lines" (Line and continuum measurements)
   - assumption: Planck 2015 cosmology, H0=68, Omega_m=0.31  
  > "$H_{0} = 68~\text{km}~\text{s}^{-1}\,\text{Mpc}^{-1}$ and $\Omega_{\text{m}} = 0.31$" (Introduction)
   - fitting: _not stated_
   - validation: _not stated_
5. **Derive electron density from the line ratio**: Three-level N+ rate equations with electron collisions, Tayal collision rates at Te=8000 K, giving n_e = 247 (R-0.52)/(9.73-R) cm^-3  
  > "$$\begin{equation}
 \label{eq:ne247}
    n_{\text{e}}=247\left(\frac{R - 0.52}{9.73-R}\right)\text{cm}^{-3}.
\end{equation}$$" (Electron density)
   - parameter: Te = 8000 K; collision rates assumed temperature independent  
  > "assuming that collision rates are independent of temperature" (Electron density)
   - assumption: Optically thin emission; column density ratio equals volume density ratio  
  > "assuming the ratio of column densities equals the ratio of volume densities" (Electron density)
   - fitting: _not stated_
   - validation: n_e changes by under 10% for a 2000 K increase in temperature; optical pumping tested at about 2% of collision rate  
  > "the derived electron density does not vary by more than 10% for a 2000 K increase in kinetic temperature" (Electron density); "or approximately 2 per cent of the collision rate" (Electron density)

## Software

- **CASA** v.5.1.0-74.el7: Imaging and cleaning with tclean  
  > "We imaged and cleaned the data using the casa (v.5.1.0-74.el7) task, `tclean`." (Observations)

## Numeric results

| quantity | value | uncertainty | units | step | quote |
|---|---|---|---|---|---|
| L_IR (8-1000 um) | 1.1e13 | 0.2e13 | Lsun | 3 | we measure a total $L_{\rm IR}=(1.1\pm 0.2)\times 10^{13}\,\mathrm{L}_\odot$ |
| [N II] 205um integrated flux | 2.37 | 0.06 | Jy km/s | 4 | $\mathbf{S}\Delta V = (2.37 \pm 0.06)~\text{Jy~km}~\text{s}^{-1}$ |
| L_205 | 4.7e8 | 0.1e8 | Lsun | 4 | $L_{205}=(4.7 \pm 0.1) \times 10^{8} \,\mathrm{L}_\odot$ |
| [N II] 122um integrated flux | 7.6 | 0.9 | Jy km/s | 4 | the integrated flux density is S$\Delta V = (7.6 \pm 0.9)~\text{Jy~km}~\text{s}^{-1}$ |
| L_122 | 2.6e9 | 0.3e9 | Lsun | 4 | $L_{122}=(2.6 \pm 0.3) \times 10^{9} \,\mathrm{L}_\odot$ |
| Electron density | 290 | +90/-70 | cm^-3 | 5 | we find an electron density of $n_{\text{e}} = 290^{+90}_{-70}\text{cm}^{-3}$ |
| Source-plane continuum flux density at 400 and 680 GHz | 12 mJy and 43 mJy | not stated | mJy | 3 | the total Band 8 and Band 9 source plane continuum flux densities are 12 mJy and 43 mJy at observed frequencies of 400 and 680 GHz |

## Qualitative findings

- [N II] line profiles resemble the CO(4-3) and CI(1-0) profiles, so ionised and molecular gas are co-located  
  > "indicating that the ionised and molecular tracers originate from the same material and local environments" (Interpretation and discussion)
- Weak trend of higher [N II] ratio with higher CO(4-3)/CI(1-0) ratio across literature sources  
  > "there is a weak trend that galaxies or regions with high electron densities" (Interpretation and discussion)

## Claim tuples

- H: Is the ionised ISM of 9io9 dense on global scales? | E: Measured [N II] 122/205 um ratio in the source plane and converted to n_e | R: n_e = 290 (+90/-70) cm^-3 | F: Globally averaged n_e is over an order of magnitude above the Milky Way average, comparable to Galactic star-forming regions | **supported**
- H: Is the ionised gas co-located with the molecular gas? | E: Compared [N II] line profiles with CO(4-3) and CI(1-0) | R: Double-horned profiles match | F: Ionised gas broadly co-located with molecular material on kpc scales | **supported**
- H: Does the ionised gas density track the dense molecular gas fraction? | E: Compared [N II] ratio with CO(4-3)/CI(1-0) for 9io9 and literature sources | R: Tentative trend | F: Picture of a globally dense ISM | **partially**

## Reasoning

- Why this data: Lensing amplification allows [N II] diagnostics that would be impossible for unlensed targets  
  > "their lens-amplified flux offers a route to measure diagnostic tracers of the ISM and its conditions in a way that would be impossible in the unlensed case" (Introduction)
- Why this method: _not stated_
- Alternative: Resolved 122 um properties and resolved line ratio not interpreted due to low S/N  
  > "we do not attempt to interpret the resolved properties of the line itself, or the line ratio, concentrating our analysis on the integrated properties" (Lens model)
- How they decided it was enough: _not stated_
- Limitation (authors): Errors exclude lens-model systematics  
  > "The errors quoted for the intrinsic source properties do not include any systematic uncertainty introduced by the prescribed parametric lens model" (Lens model)
- Limitation (authors): Lines incomplete in the band coverage; roughly 10% flux missing  
  > "we estimate we are missing $\approx 10\%$ of the total line flux for both lines" (Line and continuum measurements)
- Caveat (inferred, ours): Single-temperature, temperature-independent collision-rate assumption for n_e
- Caveat (inferred, ours): Low S/N of the 122 um line
- Caveat (inferred, ours): Trend with CO/CI ratio rests on a heterogeneous literature sample
- Caveat (inferred, ours): Lens model inherited without independent check

## Reproducibility

- Data public (paper): ALMA data acknowledged by project code; public status not stated  
  > "This paper makes use of the following ALMA data: ADS/JAO.ALMA#2017.1.00814.S." (Acknowledgements)
- Products in archive: _not stated_
- Missing: Lens model and source-plane reconstruction code or parameters
- Missing: Cell/image size and channel settings
- Missing: Line-free channel ranges
- Missing: Band 9 manual calibration script
- Missing: Uncertainty propagation to n_e
- Data volume (inferred): ~50-150 GB raw for Bands 8 and 9 (a few execution blocks)
- Score (inferred): 3/5, Data and main formulas are clear, but the lens model and several imaging settings are external or unstated.
- Rediscovery candidate: no, Depends on the lens model and source-plane reconstruction from another paper, and the recipe lacks several imaging details.

## Links

- Method: (cite: warren_semilinear_2003) (Semi-linear inversion lens reconstruction method)
- Method: (cite: goldsmith_herschel_2015) (N+ rate equation formalism)
- Method: (cite: tayal_electron_2011) (N+ electron collision rates)
- Companion: (cite: geach_magnified_2018) (Band 4 CO(4-3) and CI(1-0) data and the lens model)
- Companion: (cite: harrington_red_2019) (Earlier [N II] 205 um SFR comparison assuming low n_e)
- Related: Spacewarps
- Related: Planck
- Related: Herschel
- Related: Atacama Cosmology Telescope

## Checks

```json
{
 "quotes": 74,
 "quotes_ok": 74,
 "quote_pass_rate": 1.0,
 "quotes_too_long": 0,
 "unsupported_facts": 0,
 "project_codes": 1,
 "codes_not_in_text": [],
 "codes_not_in_obscore": [],
 "obscore_codes_not_in_card": [],
 "codes_printed_but_missing": [],
 "numeric_results": 7,
 "numeric_problems": 0,
 "fill": {
  "facts": 78,
  "stated": 51,
  "rate": 0.654
 },
 "evidence_ok": true
}
```
