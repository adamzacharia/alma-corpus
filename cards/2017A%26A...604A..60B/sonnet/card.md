# Exploring molecular complexity with ALMA (EMoCA): Detection of three new hot cores in Sagittarius B2(N)

`2017A&A...604A..60B` | Astronomy and Astrophysics 2017 | first author: Bonfand, M. | arXiv: 1703.09544 | DOI: 10.1051/0004-6361/201730648

Card schema 1.0 | model claude-sonnet-5-5 | depth full | type archival_reuse

## Science

- Fields: star_formation, astrochemistry, milky_way_ism
- Question: Does the EMoCA 3 mm ALMA line survey reveal additional hot cores in Sgr B2(N), and what are their chemical, physical and evolutionary properties?  
  > "Our goal is to use the high sensitivity of the Atacama Large Millimeter/submillimeter Array (ALMA) to characterize the hot core population in Sgr B2(N)" (abstract)
- Target **Sgr B2(N)**: coordinates phase center 17h47m19.87s, -28d22'16" (J2000)  
  > "at a distance of 8.34 $\pm$ 0.16 kpc from the Sun (cite: reid2014)" (Introduction); "at $\alpha _{\rm J2000}$ = 17$^h$47$^m$19.87$^s$, $\delta _{\rm J2000}$ = -28$^{\rm o}$22$'$16$\ensuremath{''}$" (2.1 Atacama Large Millimiter/submillimeter Array (ALMA)); z/distance 8.34 ± 0.16 kpc  
  > "at a distance of 8.34 $\pm$ 0.16 kpc from the Sun (cite: reid2014)" (Introduction); "at $\alpha _{\rm J2000}$ = 17$^h$47$^m$19.87$^s$, $\delta _{\rm J2000}$ = -28$^{\rm o}$22$'$16$\ensuremath{''}$" (2.1 Atacama Large Millimiter/submillimeter Array (ALMA)); distance from Reid et al. 2014  
  > "at a distance of 8.34 $\pm$ 0.16 kpc from the Sun (cite: reid2014)" (Introduction); "at $\alpha _{\rm J2000}$ = 17$^h$47$^m$19.87$^s$, $\delta _{\rm J2000}$ = -28$^{\rm o}$22$'$16$\ensuremath{''}$" (2.1 Atacama Large Millimiter/submillimeter Array (ALMA))

## Data provenance

- ALMA projects: 2011.0.00017.S, 2012.1.00012.S
- bands: 3 mm (84.1-114.4 GHz)  
  > "We use a complete 3 mm spectral line survey conducted with ALMA" (abstract)
- frequencies and spectral setup: complete line survey 84.1-114.4 GHz, five setups of four spectral windows each, 488 kHz channels  
  > "The spectral line survey is divided into five spectral setups, each one delivering four spectral windows." (2.1 Atacama Large Millimiter/submillimeter Array (ALMA))
- continuum bandwidth: _not stated_
- arrays: _not stated_
- configurations: _not stated_
- baselines: _not stated_
- angular resolution: ~1.6"  
  > "conducted at high angular resolution ($\sim$1.6$\ensuremath{''}$)" (2.1 Atacama Large Millimiter/submillimeter Array (ALMA))
- max recoverable scale: _not stated_
- sensitivity: ~3 mJy/beam per 488 kHz channel  
  > "a high sensitivity $\sim$3 mJy/beam per 488 kHz (1.7 to 1.3 km s$^{-1}$) wide channel" (2.1 Atacama Large Millimiter/submillimeter Array (ALMA))
- time on source: _not stated_
- observing dates: _not stated_
- pi or archival as stated: _not stated_
- Other facility **SMA**: 342.883 GHz continuum map from Qin et al. 2011, beam 0.4"x0.24"  
  > "The continuum map used here was obtained at 342.883 GHz, with a synthesized beam of 0.4$\ensuremath{''}$ $\times$ 0.24$\ensuremath{''}$" (2.2 Submillimeter Array (SMA))
- External data: SMA 343 GHz continuum map of Sgr B2  
  > "(cite: qin2011) observed the Sgr B2 region using the SMA in the compact and very extended configurations" (2.2 Submillimeter Array (SMA)) [from (cite: qin2011)]
- External data: UCHII region fluxes (K2, K3, K7) at 44.2 GHz  
  > "They measured an integrated flux of 30 mJy at 44.2 GHz for a source size of 0.08$\ensuremath{''}$." (Appendix: Estimating the level of free-free emission) [from (cite: depree2015)]
- External data: Z10.24 flux 36 mJy at 22.4 GHz  
  > "They measured an integrated flux of 36 mJy at 22.4 GHz for a source size $<$0.25$\ensuremath{''}$." (Appendix: Estimating the level of free-free emission) [from (cite: gaume1995)]
- External data: Class II methanol maser positions  
  > "class II methanol masers (cite: caswell1996) are shown in Fig. [1](#hot_cores_contour_map)" (3.1 Detection of three new sources) [from (cite: caswell1996)]
- External data: isotopic ratio 12C/13C = 21  
  > "= 21 derived by (cite: belloche2016) to obtain the column density" (3.8 Chemical composition) [from (cite: belloche2016)]

## Processing

### Calibration

- pipeline or manual: _not stated_
- casa version: _not stated_
- pipeline version: _not stated_
- archive products used as is: _not stated_
- flux calibrator: _not stated_
- flux scale uncertainty: _not stated_
- self calibration: _not stated_

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
- primary beam correction: flux densities and spectra corrected for primary beam attenuation  
  > "The derived flux density is then corrected for the primary beam attenuation." (3.2.1 ALMA data: correction for free-free emission)
- array combination: _not stated_
- smoothing: SMA map smoothed to the 20 ALMA resolutions with GILDAS GAUSS-SMOOTH  
  > "We use the task GAUSS-SMOOTH of the GILDAS software." (3.2.2 SMA data: smoothing to the ALMA resolution)
- final beam: _not stated_
- final rms: _not stated_

### Inherited from earlier work

- ALMA setups and data reduction  
  > "Details about the different setups and the data reduction are presented in (cite: belloche2016)." (2.1 Atacama Large Millimiter/submillimeter Array (ALMA)) [from (cite: belloche2016)]
- LTE modelling procedure  
  > "More information about the modelling procedure can be found in (cite: belloche2016)." (2.3 Radiative transfer modelling of the line survey) [from (cite: belloche2016)]
- spectroscopic predictions  
  > "The spectroscopic predictions used to model the spectra are the same as in (cite: belloche2016; belloche2017), and (cite: muller2016)." (2.3 Radiative transfer modelling of the line survey) [from (cite: belloche2016; belloche2017; muller2016)]
- SMA map details  
  > "More details can be found in (cite: qin2011)." (2.2 Submillimeter Array (SMA)) [from (cite: qin2011)]

### Not stated but needed to reproduce (our reading)

- CASA version, imaging parameters and continuum/line-free channel selection (only in Belloche et al. 2016)
- Calibration and flux scale details
- Obtaining the SMA map (provided privately by authors)
- Line-integration frequency boundaries for population diagrams
- Final per-setup beams and noise for the 20 continuum maps
- Full line lists and manual model-fitting choices

## Analysis recipe

1. **Search for hot cores via line density map**: Count channels above 7 sigma per pixel over setups excluding setup 3; fit 2D Gaussians to the count map  
  > "we counted the channels with continuum-subtracted flux densities above the 7$\sigma$ level (1$\sigma$ $\sim$3 mJy/beam) over the whole frequency range for each pixel" (3.1 Detection of three new sources)
   - software: GILDAS
   - parameter: 7 sigma, 1 sigma ~3 mJy/beam, 47296 channels (23.1 GHz)  
  > "The analyzed ranges cover 47296 channels, $i.e.$ 23.1 GHz." (3.1 Detection of three new sources)
   - fitting: _not stated_
   - validation: _not stated_
2. **Derive H2 column densities and dust beta from ALMA+SMA continuum**: Peak flux by 2D Gaussian fits after free-free correction; solve radiative transfer for tau and N_H2; beta from ALMA/SMA flux ratio  
  > "We assume a dust temperature $T_{\rm d}$ $\sim T_{\rm gas}$ $\sim$150 K" (3.2.4 H2 column densities)
   - software: GILDAS
   - parameter: kappa0 = 1.6 cm2/g at 1.3 mm, beta = 1.2  
  > "We adopt a dust mass absorption coefficient $\kappa_0 = 1.6$ cm$^2$ g$^{-1}$ (of dust) at $\lambda_0 = 1.3$ mm" (3.2.4 H2 column densities)
   - assumption: Td=150 K, mu_H2=2.8, gas-to-dust 100  
  > "with $\chi_d$ = 100 the standard gas-to-dust ratio" (3.2.4 H2 column densities)
   - fitting: weighted linear fit for free-free pedestal  
  > "The weighted linear fit to the results excluding setup 3 gives us the correction" (Appendix: Estimating the level of free-free emission)
   - validation: kappa0 checked via methanol abundance ~2e-5 in N2 consistent with chemical models  
  > "consistent with the peak gas-phase abundance of methanol predicted by our chemical models" (3.2.4 H2 column densities)
3. **LTE modelling of spectra and line identification**: Weeds LTE model per species: N, Trot, size, offset, FWHM adjusted manually  
  > "All parameters are then adjusted manually until a good fit to the data is obtained." (2.3 Radiative transfer modelling of the line survey)
   - software: Weeds, CLASS
   - assumption: LTE; Gaussian source  
  > "angular size of the emitting region (assumed to be Gaussian)" (2.3 Radiative transfer modelling of the line survey)
   - fitting: manual adjustment  
  > "All parameters are then adjusted manually until a good fit to the data is obtained." (2.3 Radiative transfer modelling of the line survey)
   - validation: lines assigned only if all transitions detected with predicted intensity  
  > "a line is assigned to a given molecule only if all lines from this molecule emitted in the frequency range of the survey are detected with the right intensity" (2.3 Radiative transfer modelling of the line survey)
4. **Source sizes and spatial distribution**: 2D Gaussian fits to integrated intensity maps; mean deconvolved size sqrt(maj*min)  
  > "allow us to calculate the average deconvolved size of the emitting region ($\sqrt{ \theta_{maj} \times \theta_{min}}$)" (3.5 Size of the hot cores)
   - software: GILDAS
   - fitting: GAUSS-2D  
  > "We fit 2D Gaussians to the channel count map with the GILDAS procedure GAUSS-2D in order to derive the peak position of the five sources." (3.1 Detection of three new sources)
   - validation: _not stated_
5. **Rotational temperatures**: Population diagrams of ethanol and methyl formate with opacity and contamination correction; weighted linear fit  
  > "shows the weighted linear fit to the observed data points." (3.6 Rotational temperature)
   - assumption: optically thin first approximation; other molecules fixed at 145 K  
  > "For the rest of the molecules, we set the temperature to 145 K in our LTE model" (3.6 Rotational temperature)
   - fitting: weighted linear fit  
  > "shows the weighted linear fit to the observed data points." (3.6 Rotational temperature)
   - validation: synthetic population diagrams compared  
  > "The synthetic data points are not affected by contamination from other species and should be strictly aligned." (3.6 Rotational temperature)
6. **Outflow detection and dynamical times**: Integrate blue/red wings of SO, OCS, CS; t_dyn = r/Vmax  
  > "we calculate dynamical timescale of each outflow lobe as $t_{\rm dyn} = \frac{r}{V_{\rm max}}$" (3.7 Kinematic structure of the hot cores)
   - assumption: outflow inclination ~45 deg  
  > "assuming that the inclination of the outflow axis with respect to the line of sight is about 45$^{\rm o}$" (3.7 Kinematic structure of the hot cores)
   - fitting: _not stated_
   - validation: _not stated_
7. **Statistical lifetimes**: Ratio of hot cores/masers to UCHII regions times 1e5 yr  
  > "we estimate a lifetime of 10$^5$ $\times$ $\frac{5}{8}$ $\sim$6$\times$10$^4$ yr" (4.5 Star formation timescales and evolutionary sequence in Sgr B2(N))
   - assumption: UCHII lifetime 1e5 yr, constant star formation rate  
  > "We assume a constant star formation rate to estimate the lifetime of Sgr B2(N)’s hot cores." (4.5 Star formation timescales and evolutionary sequence in Sgr B2(N))
   - fitting: _not stated_
   - validation: maser lifetime compared to van der Walt 2005  
  > "which is, given the low number statistics of the Sgr B2(N) region, surprisingly consistent with the lifetime derived by (cite: vanderwalt2005) for class II methanol masers" (4.5 Star formation timescales and evolutionary sequence in Sgr B2(N))

## Software

- **Weeds** : line identification and LTE modelling  
  > "We use Weeds (cite: maret2011), which is part of the CLASS software" (2.3 Radiative transfer modelling of the line survey)
- **GILDAS** : GAUSS-2D fits, GAUSS-SMOOTH, noise histograms  
  > "using the command GO NOISE of the GILDAS software" (3.2.1 ALMA data: correction for free-free emission)

## Numeric results

| quantity | value | uncertainty | units | step | quote |
|---|---|---|---|---|---|
| Dust emissivity index beta (N2) | 1.2 | 0.1 | dimensionless | 2 | We obtain $\beta$ = 0.8$\pm$0.1 and $\beta$ = 1.2$\pm$0.1 for Sgr B2(N1) and Sgr B2(N2), respectively. |
| Source size N3 | 0.4 | 0.1 | arcsec | 4 | We obtain sizes of 0.4$\pm$0.1$\ensuremath{''}$ for Sgr B2(N3), 1.0$\pm$0.3$\ensuremath{''}$ for Sgr B2(N4) |
| Line density N3, N4, N5 | 31, 11, 22 | not stated | GHz^-1 | 3 | / N3 / 714 / 31 / 23 / 20 / 19 / 9 / |
| N_H2 N1 (ALMA, free-free corrected) | 13.1e24 | 2.2e24 | cm-2 | 2 | / N1     / 15.4(2.2)     / 13.1(2.2)               / 8.1(0.9) |
| Rotational temperature N3 (ethanol-like species, v=0) | 140.9 | 4.6 | K | 5 | / N3 /  / $\varv$ = 0 / 57 / 0.24 / 140.9(4.6) / |
| Hot core lifetime | 6e4 | not stated | yr | 7 | we estimate a lifetime of 10$^5$ $\times$ $\frac{5}{8}$ $\sim$6$\times$10$^4$ yr |
| Class II methanol maser lifetime | 4e4 | not stated | yr | 7 | a statistical lifetime of about 4$\times$10$^4$ yr for the class II 6.7 GHz methanol masers |

## Qualitative findings

- New hot cores have similar chemistry to each other but differ from N2.  
  > "shows that the three new hot cores have similar compositions but differ from Sgr B2(N2)." (3.8 Chemical composition)

## Claim tuples

- H: Are there more hot cores in Sgr B2(N) beyond N1 and N2? | E: Count channels above 7 sigma per pixel in the EMoCA survey | R: Three additional line-density peaks with 11-31 lines/GHz, associated with 6.7 GHz masers | F: Three new hot cores N3, N4, N5 discovered | **supported**
- H: Do N3 and N5 drive outflows? | E: Integrated line wing maps of SO, OCS, CS | R: Bipolar blue/red lobes; none in N2 and N4 | F: Outflows in N3 and N5, dynamical times few 1e3 yr | **supported**
- H: Evolutionary sequence of Sgr B2(N) hot cores | E: Association with masers, outflows, UCHII regions and chemistry | R: Sequence N4, N3, N5, N1 but N2 ambiguous | F: Tentative age sequence; N2 may contain two sources | **partially**

## Reasoning

- Why this data: High sensitivity of EMoCA survey enables search for fainter hot cores  
  > "We take advantage of the high sensitivity of the EMoCA survey" (Introduction)
- Why this method: _not stated_
- Alternative: Region SE of N5 rejected as deconvolution artifact  
  > "We think this structure is a deconvolution artifact." (3.1 Detection of three new sources)
- How they decided it was enough: _not stated_
- Limitation (authors): Source size from few species; column densities depend strongly on adopted size  
  > "the column densities derived from the model strongly depend on the adopted source size" (4.4 Physical properties of the new hot cores)
- Limitation (authors): Evolutionary sequence tentative  
  > "our attempt to classify them with a single evolutionary sequence should be considered as tentative only" (4.5 Star formation timescales and evolutionary sequence in Sgr B2(N))
- Caveat (inferred, ours): Manual LTE fitting without uncertainties on column densities
- Caveat (inferred, ours): Single source size per core
- Caveat (inferred, ours): Statistical lifetimes rest on small numbers and an assumed UCHII lifetime
- Caveat (inferred, ours): Fixed 150 K dust temperature and kappa0 chosen by methanol abundance argument

## Reproducibility

- Data public (paper): Interferometric data available in the ALMA archive  
  > "The interferometric data are available in the ALMA archive at https://almascience.eso.org/aq/." (Acknowledgements)
- Products in archive: _not stated_
- Missing: Calibrated data cubes (reduction in Belloche et al. 2016)
- Missing: SMA map from Qin et al. 2011 provided privately
- Missing: Manual Weeds model parameters beyond tables
- Data volume (inferred): hundreds of GB (full 5-setup 3 mm survey, two projects)
- Score (inferred): 3/5, Public data and clear continuum/size analysis, but reduction is inherited and LTE modelling is manual and partly unstated.
- Rediscovery candidate: no, Key steps depend on inherited reduction, privately supplied SMA map and manual line modelling.

## Links

- Method: (cite: belloche2016) (Survey setups, data reduction and modelling procedure)
- Method: (cite: maret2011) (Weeds LTE modelling)
- Companion: (cite: belloche2016) (EMoCA analysis of Sgr B2(N2))
- Companion: (cite: belloche2017) (EMoCA companion)
- Related: EMoCA

## Checks

```json
{
 "quotes": 67,
 "quotes_ok": 67,
 "quote_pass_rate": 1.0,
 "quotes_too_long": 0,
 "unsupported_facts": 0,
 "project_codes": 2,
 "codes_not_in_text": [],
 "codes_not_in_obscore": [],
 "obscore_codes_not_in_card": [],
 "codes_printed_but_missing": [],
 "numeric_results": 7,
 "numeric_problems": 0,
 "fill": {
  "facts": 87,
  "stated": 50,
  "rate": 0.575
 },
 "evidence_ok": true
}
```
