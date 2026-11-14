# Kiloparsec-Scale Variations in the Star Formation Efficiency of Dense Gas: The Antennae Galaxies (NGC 4038/39)

`2019AJ....157..131B` | The Astronomical Journal 2019 | first author: Bemis, Ashley | arXiv: 1902.02809 | DOI: 10.3847/1538-3881/ab041d

Card schema 1.0 | model claude-sonnet-5-5 | depth full | type archival_reuse

## Science

- Fields: nearby_galaxies, star_formation
- Question: How does the star formation efficiency of dense gas (L_TIR/L_HCN) vary across kpc-scale regions of the Antennae, and does the Antennae follow the L_TIR-L_HCN relation of other galaxies?  
  > "We study the relationship between dense gas and star formation in the Antennae galaxies by comparing ALMA observations of dense gas tracers (HCN, HCO$^+$, and HNC $\mathrm{J}=1-0$)" (abstract)
- Target **Antennae galaxies (NGC 4038/39)**: coordinates _not stated_; z/distance 22 Mpc; z=0.005477  
  > "The Antennae galaxies are the nearest pair of merging galaxies (22 Mpc, (cite: Schweizer:2008))" (1 Introduction); "We use a redshift of $\mathrm{z}=0.005477$." (2.1 ALMA Data); distance from Schweizer et al. 2008  
  > "The Antennae galaxies are the nearest pair of merging galaxies (22 Mpc, (cite: Schweizer:2008))" (1 Introduction); "We use a redshift of $\mathrm{z}=0.005477$." (2.1 ALMA Data)

## Data provenance

- ALMA projects: _none stated_
- bands: Band 3  
  > "the calibration uncertainty of the ALMA data ($\sim 5\%$ for Band 3, ALMA Technical Handbook for Cycle 1)" (7.1 Molecular Luminosities)
- frequencies and spectral setup: _not stated_
- continuum bandwidth: _not stated_
- arrays: _not stated_
- configurations: _not stated_
- baselines: _not stated_
- angular resolution: 5.5'' and 6.8'' after tapering/smoothing  
  > "When working at the $100\ \mu$m resolution, we further smooth the tapered cube to $6.8''$." (2.1 ALMA Data)
- max recoverable scale: ~17'' (~1.8 kpc)  
  > "The largest angular scale of the ALMA observations is $\sim 17''$[^1] ($\sim 1.8$ kpc)." (2.1 ALMA Data)
- sensitivity: 1.2 mJy/beam (5.5'' tapered), 1.4 mJy/beam (6.8'')  
  > "The tapered data reach a root mean square noise level (rms) of $\sigma=1.2\ \mathrm{mJy\ beam}^{-1}$." (2.1 ALMA Data)
- time on source: _not stated_
- observing dates: _not stated_
- pi or archival as stated: _not stated_
- Line: HCN J=1-0 (not stated)
- Line: HCO+ J=1-0 (not stated)
- Line: HNC J=1-0 (not stated)
- Other facility **Herschel PACS/SPIRE**: 70, 100, 160, 250 micron maps for L_TIR  
  > "We obtain user-provided data products of the 70, 100, 160, and 250 $\mu$m maps from the *Herschel* (cite: Pilbratt:2010) Science Archive." (2.2 Infrared Data)
- Other facility **Spitzer MIPS**: 24 micron map  
  > "We also retrieve user-provided *Spitzer* (cite: Werner:2004:Spitzer) 24 $\mu$m Multiband Imaging Photometer (MIPS) data" (2.2 Infrared Data)
- Other facility **OVRO**: CO J=1-0 for total molecular gas  
  > "We also use CO $\mathrm{J}=1-0$ data from the Owens Valley Radio Observatory (OVRO, (cite: Wilson:2003)) as our bulk molecular gas tracer" (2 Data)
- External data: L_TIR calibrations (monochromatic and multi-band)  
  > "We use several calibrations from (cite: Galametz:2013) to estimate L$_\mathrm{TIR}$" (2.2 Infrared Data) [from Galametz et al. 2013 (cite: Galametz:2013)]
- External data: alpha_CO ≈ 7 Msun/(K km/s pc^2)  
  > "we adopt a CO-to-$\mathrm{H_2}$ conversion factor of $\mathrm{\alpha_{CO}}\ \approx 7\ \mathrm{M_\odot\ (K\ km\ s^{-1}\ pc^{2})^{-1}}$ from (cite: Schirm:2014)" (4 Results) [from (cite: Schirm:2014)]
- External data: alpha_HCN ≈ 10  
  > "using the conversion factor published by (cite: Gao:2004a), $\mathrm{\alpha_{HCN}}\ \approx 10\ \mathrm{M_\odot\ (K\ km\ s^{-1}\ pc^{2})^{-1}}$" (4 Results) [from (cite: Gao:2004a)]
- External data: Comparison L_TIR-L_HCN samples of galaxies  
  > "We compare our results with those of (cite: Gao:2004a; Gao:2004b) and (cite: Liu:2015)" (3 Aperture Analysis) [from Gao & Solomon 2004; Liu et al. 2015]
- External data: CMZ L_TIR and L_HCN  
  > "We also compare with measurements of $\mathrm{L_{TIR}}$ and $\mathrm{L_{HCN}}$ of the CMZ (cite: Stephens:2016)" (3 Aperture Analysis) [from (cite: Stephens:2016)]

## Processing

### Calibration

- pipeline or manual: _not stated_
- casa version: CASA 4.2.0 for calibration with original scripts  
  > "The original reduction scripts were used to apply calibrations to the raw data using the appropriate Common Astronomy Software Applications (CASA) version (CASA 4.2.0, (cite: McMullin:2007))." (2.1 ALMA Data)
- pipeline version: _not stated_
- archive products used as is: _not stated_
- flux calibrator: _not stated_
- flux scale uncertainty: ~5% for Band 3  
  > "the calibration uncertainty of the ALMA data ($\sim 5\%$ for Band 3, ALMA Technical Handbook for Cycle 1)" (7.1 Molecular Luminosities)
- self calibration: _not stated_

### Imaging

- task: CASA 4.7.2 clean; immoments for moment 0  
  > "The ALMA data were then cleaned and imaged in in CASA 4.7.2." (2.1 ALMA Data)
- deconvolver: _not stated_
- weighting robust: Briggs 0.5  
  > "using a Briggs weighting of $0.5$ while cleaning" (2.1 ALMA Data)
- uv taper: tapered to FWHM of Herschel 70 um PSF  
  > "We tapered the data to the Full-Width Half-Maximum (FWHM) of the *Herschel* 70 $\mu$m Point Spread Function" (2.1 ALMA Data)
- cell size: _not stated_
- image size: _not stated_
- masking: moment maps require pixels >2 sigma  
  > "We require that all pixels going into the final moment map be greater than $2\sigma$" (2.1 ALMA Data)
- multiscale scales: _not stated_
- continuum subtraction: _not stated_
- line free channels: _not stated_
- primary beam correction: _not stated_
- array combination: _not stated_
- smoothing: smoothed to 6.8'' for 100 um resolution  
  > "we further smooth the tapered cube to $6.8''$" (2.1 ALMA Data)
- final beam: _not stated_
- final rms: 1.2 mJy/beam (5.5''); 1.4 mJy/beam (6.8'')  
  > "$\sigma=1.2$ mJy beam$^{-1}$ in the $5.5''$ maps and $\sigma=1.4$ mJy beam$^{-1}$ in the smoothed 6.8$''$ maps" (2.1 ALMA Data)

### Inherited from earlier work

- Observation details and original reduction scripts  
  > "Details on the observations of the ALMA data are available in (cite: Schirm:2016)." (2.1 ALMA Data) [from (cite: Schirm:2016)]
- Herschel PACS observations and reduction  
  > "Details on the observations and reduction of the 70, 100, and 160 $\mu$m (Photodetector Array Camera and Spectrometer) PACS (cite: Poglitsch:2010) data are available in (cite: Klaas:2010)" (2.2 Infrared Data) [from (cite: Klaas:2010)]
- SPIRE 250 um observations and calibration  
  > "details on the observations and calibrations can be found in (cite: Bendo:2012:VNGS)" (2.2 Infrared Data) [from (cite: Bendo:2012:VNGS)]
- Hexagonal grid aperture approach  
  > "inspired by a similar method employed by (cite: Leroy:2016)" (3 Aperture Analysis) [from (cite: Leroy:2016)]

### Not stated but needed to reproduce (our reading)

- Spectral window setup, rest frequencies, and observing dates/configurations (deferred to Schirm et al. 2016)
- Clean threshold, mask, niter, and image/cell size
- Line-free channels (if any continuum subtraction was done)
- Exact aperture/hexagon grid origin and orientation
- CPROPS parameters
- Background apertures for IR maps
- LINMIX settings (chain length, priors)
- Primary beam correction details
- Unit conversion of upper limits

## Analysis recipe

1. **Image tapered ALMA cubes and make moment-0 maps**: Clean with 5.2 km/s channels over 1000-2000 km/s, taper to Herschel 70 um PSF, Briggs 0.5; immoments with >2 sigma cut  
  > "We cleaned using a velocity resolution of $\Delta \mathrm{v_{opt}} = 5.2\ \mathrm{km\ s}^{-1}$ at the rest frequency of each transition over an optical velocity range of 1000-2000 km s$^{-1}$." (2.1 ALMA Data)
   - software: CASA
   - fitting: _not stated_
   - validation: _not stated_
2. **Compute L_TIR maps from IR data**: Convolve Herschel/Spitzer maps with Aniano kernels, background-subtract, apply Galametz et al. 2013 70 um and 24+70+100 um calibrations  
  > "Each dataset was then convolved to a common resolution using the (cite: Aniano:2011) kernels." (2.2 Infrared Data)
   - fitting: _not stated_
   - validation: L_TIR(70) agrees with L_TIR(24+70+100) to ~3% for SGMC345  
  > "is only $\sim3\%$ lower than the L$_\mathrm{TIR}(24+70+100)$ estimate and agrees within uncertainties." (2.2 Infrared Data)
3. **Aperture photometry and luminosities**: Elliptical apertures from CPROPS clumps and hexagonal grid (6.8'' incircle); convert Jy km/s to L' via Wilson et al. 2008 equation; upper limits from noise-limit 2x sigma_Gauss  
  > "We set our upper limit to two times this noise limit" (3 Aperture Analysis)
   - software: CPROPS, Photutils
   - fitting: _not stated_
   - validation: _not stated_
4. **Fit L_TIR-L_dense relations**: Bayesian linear regression with LINMIX including upper limits; Spearman rank for significance  
  > "We perform the luminosity-luminosity fits using the Bayesian linear regression code LINMIX (cite: Kelly:2007)" (3 Aperture Analysis)
   - software: LINMIX
   - fitting: MCMC medians with 1- and 2-sigma uncertainties  
  > "we take the median values of these iterations as our fit parameters" (3 Aperture Analysis)
   - validation: Spearman p-values  
  > "We estimate the significance of each correlation by calculating the Spearman rank coefficients" (3 Aperture Analysis)
5. **Derive SFR, gas masses, dense gas fraction, SFE**: log SFR = log L_TIR - 9.83; M_dense = alpha_HCN L_HCN; M_H2 = alpha_CO L_CO; f_dense = M_dense/M_H2; SFE_dense = SFR/M_dense  
  > "we calculate the star formation efficiency of dense gas via $\mathrm{SFE_{dense} = SFR/M_{dense}}$" (4 Results)
   - assumption: alpha_HCN ≈ 10, alpha_CO ≈ 7 M_sun (K km/s pc^2)^-1; distance 22 Mpc  
  > "we adopt a CO-to-$\mathrm{H_2}$ conversion factor of $\mathrm{\alpha_{CO}}\ \approx 7\ \mathrm{M_\odot\ (K\ km\ s^{-1}\ pc^{2})^{-1}}$ from (cite: Schirm:2014)" (4 Results)
   - fitting: _not stated_
   - validation: Compared with Brandl et al. 2009 SFRs  
  > "which are higher by a factor $>2$ than the estimates from (cite: Brandl:2009)" (5.2.2 Star Formation)

## Software

- **CASA** 4.2.0 (calibration), 4.7.2 (imaging): calibration, clean, immoments  
  > "The ALMA data were then cleaned and imaged in in CASA 4.7.2." (2.1 ALMA Data)
- **CPROPS** : identify clumps of emission to define elliptical apertures  
  > "we identify clumps of emission using CPROPS (cite: Rosolowsky:2006) in each of the dense gas data-cubes" (3 Aperture Analysis)
- **LINMIX** : Bayesian linear regression with upper limits  
  > "the Bayesian linear regression code LINMIX (cite: Kelly:2007), which incorporates uncertainties in both x- and y-directions" (3 Aperture Analysis)
- **Photutils** : named in acknowledgements (likely aperture photometry)  
  > "Photutils (cite: photutils), Numpy (cite: numpy), and Pandas (cite: pandas) Python packages" (Acknowledgements)
- **Astropy** : general analysis  
  > "This research made use of Astropy, a community-developed core Python package for Astronomy (cite: astropy)." (Acknowledgements)

## Numeric results

| quantity | value | uncertainty | units | step | quote |
|---|---|---|---|---|---|
| Hexagonal fit slope L_TIR vs L_HCN | 0.49 | +0.09/-0.08 | dimensionless | 4 | \mathrm{log}(\mathrm{L_{TIR}}) &= 6.3^{+0.4}_{-0.5} + 0.49^{+0.09}_{-0.08} \mathrm{log}(\mathrm{L_{HCN}}) |
| Hexagonal fit slope L_TIR vs L_HCO+ | 0.52 | +0.07/-0.06 | dimensionless | 4 | 5.9^{+0.3}_{-0.4} + 0.52^{+0.07}_{-0.06} \mathrm{log}(\mathrm{L_{HCO^+}}) |
| Hexagonal fit slope L_TIR vs L_HNC | 0.61 | +0.16/-0.11 | dimensionless | 4 | 5.8^{+0.6}_{-0.9} + 0.61^{+0.16}_{-0.11} \mathrm{log}(\mathrm{L_{HNC}}) |
| Combined Antennae+Liu+15 slope | 0.96 | 0.03 | dimensionless | 4 | The power-law index on this fit is $\mathrm{m}=0.96\pm0.03$, which is slightly sublinear. |
| Median L_TIR/L_HCN, hexagonal apertures | 980 | not stated | Lsun (K km/s pc^2)^-1 | 4 | The median value of the $\mathrm{L_{TIR}/L_{HCN}}$ ratio of the Antennae hexagonal apertures (980 $\mathrm{L_\odot}$ (K km s$^{-1}$ pc$^2$)$^{-1}$) |
| SFE_dense NGC 4038 / NGC 4039 | 0.44 / 0.69 | factor ~10 | 1e-8 yr^-1 | 5 | / NGC4038   / 1.1                   / 26                        / 270       / 9.7                / 0.44                 / 0.043 |
| SFR of SGMC345 | 1.46 | not stated | Msun/yr | 5 | We measure the highest SFR in SGMC345, 1.46 $\mathrm{M_\odot}$ yr$^{-1}$ |

## Qualitative findings

- HCO+ is the brightest dense gas tracer overall; HNC is weaker than HCN and HCO+ everywhere; line ratios consistent with lower-density PDRs with mechanical heating  
  > "These average line ratios of HCN, HCO$^+$, and HNC are consistent with a lower-density ($\mathrm{n<10^5}$ cm$^{-3}$) PDR" (6 Conclusion)

## Claim tuples

- H: SFE of dense gas varies across the Antennae | E: Aperture photometry of L_TIR, L_HCN, L_CO in elliptical regions | R: L_TIR/L_HCN varies up to ~10x; nuclei have the lowest SFE_dense (0.44 and 0.70e-8/yr) | F: SFE_dense is not constant; nuclei have low SFE_dense and high f_dense | **supported**
- H: The Antennae follows the linear L_TIR-L_HCN relation of Gao & Solomon | E: Combined fit with Liu et al. 2015 data | R: m=0.96±0.03 | F: Antennae extends relation to lower luminosity | **supported**
- H: Kpc-scale Antennae relation is linear | E: LINMIX fit of hexagonal apertures | R: sublinear slopes ~0.5-0.6 | F: SFE_dense does not increase directly with M_dense | **partially**

## Reasoning

- Why this data: _not stated_
- Why this method: _not stated_
- How they decided it was enough: _not stated_
- Limitation (authors): Conversion factors alpha_CO and alpha_HCN uncertain (factor ~4 and ~10), making f_dense and SFE uncertain by ~10  
  > "The dense gas fraction should be uncertain by a factor of $\sim10$." (4 Results)
- Limitation (authors): OVRO CO may miss ~20% of flux  
  > "the OVRO data may be missing $\sim20\%$ of the CO $\mathrm{J}=1-0$ flux" (2 Data)
- Caveat (inferred, ours): Few apertures with non-independent hexagons (oversampled by beam) inflate fit significance
- Caveat (inferred, ours): L_TIR as SFR tracer is affected by star formation history in a merger
- Caveat (inferred, ours): Upper-limit prescription is ad hoc
- Caveat (inferred, ours): Constant conversion factors assumed despite likely variation

## Reproducibility

- Data public (paper): ALMA data project 2012.1.1.00185.S acknowledged; Herschel and Spitzer from public archives  
  > "This paper makes use of the following ALMA data: ADS/JAO.ALMA$\#$2012.1.1.00185.S." (Acknowledgements)
- Products in archive: _not stated_
- Missing: Observation/spectral setup details deferred to Schirm et al. 2016
- Missing: Clean parameters and masks
- Missing: Exact aperture grid definitions
- Missing: OVRO CO data reduction details
- Data volume (inferred): ~20-50 GB (Band 3 mosaic cubes plus Herschel/Spitzer maps)
- Score (inferred): 3/5, Data public and the aperture and fitting recipe are clear, but imaging details and inherited calibration are incompletely given.
- Rediscovery candidate: no, Recipe relies on deferred details, several external datasets, and manual aperture choices.

## Links

- Method: (cite: Galametz:2013) (L_TIR calibrations)
- Method: (cite: Kelly:2007) (LINMIX regression)
- Method: (cite: Rosolowsky:2006) (CPROPS clump identification)
- Companion: (cite: Schirm:2016) (Original ALMA observations and reduction scripts)
- Companion: (cite: Bigiel:2015) (Prior CARMA L_IR-L_HCN study of the Antennae)
- Related: Herschel VNGS
- Related: Gao & Solomon 2004 sample
- Related: Liu et al. 2015 sample

## Checks

```json
{
 "quotes": 62,
 "quotes_ok": 62,
 "quote_pass_rate": 1.0,
 "quotes_too_long": 0,
 "unsupported_facts": 0,
 "project_codes": 0,
 "codes_not_in_text": [],
 "codes_not_in_obscore": [],
 "obscore_codes_not_in_card": [
  "2012.1.00185.S"
 ],
 "codes_printed_but_missing": [],
 "numeric_results": 7,
 "numeric_problems": 0,
 "fill": {
  "facts": 79,
  "stated": 46,
  "rate": 0.582
 },
 "evidence_ok": true
}
```
