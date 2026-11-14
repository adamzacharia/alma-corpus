# Star Formation Traced by Optical and Millimeter Hydrogen Recombination Lines and Free-Free Emissions in the Dusty Merging Galaxy NGC 3256—MUSE/VLT and ALMA Synergy

`2020ApJ...895...85M` | The Astrophysical Journal 2020 | first author: Michiyama, Tomonari | arXiv: 2004.06123 | DOI: 10.3847/1538-4357/ab88a5

Card schema 1.0 | model claude-sonnet-5-5 | depth full | type multi_facility_alma_minor

## Science

- Fields: nearby_galaxies, star_formation
- Question: How do nuclear and disk-wide starbursts contribute to the total SFR of the dusty merger NGC 3256, using optical Hbeta (MUSE) plus mm H40alpha and free-free emission (ALMA)?  
  > "Combining both MUSE and ALMA observations, we conclude that the total SFR is $49\pm2~M_{\odot}$ yr$^{-1}$ and the contributions from nuclear and disk-wide starbursts are $\sim34~\%$ and $\sim66~\%$, respectively." (abstract)
- Target **NGC 3256**: coordinates Northern nucleus 10h27m51.22s, -43d54m17.85s (ICRS); southern nucleus Dec -43d54m19.20s  
  > "NGC 3256 (redshift z = 0.00935[^1]) is a merging galaxy with a TIR luminosity (5–1100$\mu$m, $L_{\rm TIR}$) of $4.8\times10^{11}~{L}_{\ensuremath{\odot}}$" (1 Introduction); "This system is at a distance of $D \sim$ 41.7 Mpc, which translates to 1$\ensuremath{''}\sim$198 pc." (1 Introduction); z/distance z = 0.00935; D ~ 41.7 Mpc  
  > "NGC 3256 (redshift z = 0.00935[^1]) is a merging galaxy with a TIR luminosity (5–1100$\mu$m, $L_{\rm TIR}$) of $4.8\times10^{11}~{L}_{\ensuremath{\odot}}$" (1 Introduction); "This system is at a distance of $D \sim$ 41.7 Mpc, which translates to 1$\ensuremath{''}\sim$198 pc." (1 Introduction); distance from redshift from NED; H0=67.7, Omega_m=0.307 (Planck 2016)  
  > "NGC 3256 (redshift z = 0.00935[^1]) is a merging galaxy with a TIR luminosity (5–1100$\mu$m, $L_{\rm TIR}$) of $4.8\times10^{11}~{L}_{\ensuremath{\odot}}$" (1 Introduction); "This system is at a distance of $D \sim$ 41.7 Mpc, which translates to 1$\ensuremath{''}\sim$198 pc." (1 Introduction)

## Data provenance

- ALMA projects: 2015.1.00993.S, 2015.1.00412.S, 2016.1.00965.S
- bands: _not stated_
- frequencies and spectral setup: _not stated_
- continuum bandwidth: _not stated_
- arrays: _not stated_
- configurations: C36-1/2, C36-2/3, C40-3, C40-6  
  > "| H40$\alpha$ | 2016 March 04 | 2015.1.00993.S | C36-1/2 | $28.4\ensuremath{''}$ |" (Table 1)
- baselines: _not stated_
- angular resolution: H40a beam 1.48x1.31 arcsec; continuum 1.32x1.20 arcsec  
  > "| H40$\alpha$ | (99.02 / 98.10) | 2.0 | 1.48 $\times$ 1.31 ($79^\circ$) | 0.08 | 11 | – |  |  |  |" (Table 2)
- max recoverable scale: 3.1 to 28.4 arcsec depending on configuration  
  > "Maximum recovery scale (MRS) for each configuration at 100 GHz" (Table 1)
- sensitivity: H40a cube rms 0.08 mJy/beam (50 km/s); continuum rms 0.028 mJy/beam  
  > "| continuum | (98.61 / 97.70) | 2.0 | 1.32 $\times$ 1.20 ($77^\circ$) | – | – | 0.028 |  |  |  |" (Table 2)
- time on source: _not stated_
- observing dates: 2016 March to October  
  > "|  | 2016 October 29 | 2016.1.00965.S | C40-6 | $3.1\ensuremath{''}$ |" (Table 1)
- pi or archival as stated: _not stated_
- Line: H40alpha H40alpha (99.02 GHz)
- Line: H42alpha H42alpha (85.69 GHz)
- Line: 13CO 1-0 (110.20 GHz)
- Line: CH3OH 2k-1k (~96.74 GHz)
- Other facility **MUSE/VLT**: Extinction map and extinction-corrected Hbeta map, 3D cube for line profiles  
  > "We use these 2D maps for the main analysis (i.e., measurements of SFR). We use the 3D data cube only for measuring line profiles" (2.1 MUSE)
- Other facility **VLA**: 5.0, 8.3, 15 GHz flux densities for SED  
  > "we use the 5.0, 8.3, and 15 GHz continuum flux density measured by Very Large Array (VLA) from the literature (cite: Neff_2003)" (3.1)
- Other facility **Spitzer/Herschel**: 24-250 micron fluxes for L_TIR  
  > "calculated using Spitzer and Hershel observations of 24, 70, 100, 160, and 250 $\mu$m flux density" (3.2 TIR)
- External data: MUSE extinction and Hbeta maps (MAD project)  
  > "Figures [\[fig:MUSE\]](#fig:MUSE) (a) and (b) show the extinction map and extinction-corrected H$\beta$ map processed by (cite: Erroz-Ferrer_2019)." (2.1 MUSE) [from (cite: Erroz-Ferrer_2019)]
- External data: VLA 5.0, 8.3, 15 GHz flux densities  
  > "we use the 5.0, 8.3, and 15 GHz continuum flux density measured by Very Large Array (VLA) from the literature (cite: Neff_2003)" (3.1) [from (cite: Neff_2003)]
- External data: 200 GHz Band 6 archival ALMA data  
  > "200 GHz Band6 data from archival ALMA data (cite: Harada_2018)" (3.1) [from (cite: Harada_2018)]
- External data: Brgamma flux of southern nucleus from online catalog  
  > "We use the Br$\gamma$ data obtained from an online catalog (cite: Piq_2016)" (4.2) [from (cite: Piq_2016)]

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
- weighting robust: robust 2.0 (H40a, H42a, CH3OH, continuum); 0.5 (13CO)  
  > "| $^{13}$CO (1–0) | (110.20 / 109.18) | 0.5 | 1.43 $\times$ 1.33 ($56^\circ$) | 0.24 | 50 | – |  |  |  |" (Table 2)
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
- final beam: H40a 1.48x1.31 arcsec PA 79  
  > "| H40$\alpha$ | (99.02 / 98.10) | 2.0 | 1.48 $\times$ 1.31 ($79^\circ$) | 0.08 | 11 | – |  |  |  |" (Table 2)
- final rms: 0.08 mJy/beam per 50 km/s channel (H40a)  
  > "The velocity resolution is 50 km s$^{-1}$." (Table 2)

### Inherited from earlier work

- MUSE extinction correction, BPT cuts  
  > "we use Baldwin, Phillips $\&$ Terlevich (BPT) cuts for each pixel derived by (cite: Erroz-Ferrer_2019)" (3.3 Results) [from (cite: Erroz-Ferrer_2019)]
- SFR-Q relation and line-flux SFR formula  
  > "According to (cite: Bendo_2016), SFR can be calculated using the relation of" (3.1) [from (cite: Bendo_2016)]
- Excitation temperature 10 K for 13CO  
  > "It is assumed that the excitation temperature of 10 K (cite: Harada_2018)" (3.2) [from (cite: Harada_2018)]

### Not stated but needed to reproduce (our reading)

- How ALMA data were calibrated (pipeline vs manual, CASA version)
- Imaging details: tclean parameters, cell/image size, continuum-subtraction channels, masking
- How the MUSE and ALMA images were matched in resolution
- SED fitting method details and priors
- Aperture definitions for pixel-by-pixel analysis

## Analysis recipe

1. **Identify H40a sources**: Fit elliptical Gaussians to H40a integrated intensity map  
  > "we use the ${\tt imfit}$ task in ${\tt CASA}$ to fit elliptical Gaussian components on the integrated intensity map" (2.2)
   - software: CASA
   - fitting: _not stated_
   - validation: _not stated_
2. **Free-free fraction of 99 GHz continuum**: SED fit with non-thermal power law, free-free and dust (slope 4.0) over 1-300 GHz  
  > "Assuming $T\rm{_e}=5000$ K, the SED fittings show that the contribution of free–free emission at 99 GHz continuum flux density (frac-FF) is $\sim76\%$ and $\sim90\%$" (3.1)
   - assumption: Te = 5000 K  
  > "Assuming $T\rm{_e}=5000$ K, the SED fittings show" (3.1)
   - fitting: _not stated_
   - validation: frac-FF not sensitive to Te  
  > "We note that the values of frac-FF obtained by SED fitting are not significantly sensitive to the assumption of electron temperature." (3.1)
3. **Electron temperature and SFR**: Te from line-to-continuum ratio R; SFR from line flux using alpha_B and epsilon  
  > "The electron temperatures are calculated using equation ([\[R_eq\]](#R_eq))." (6.4)
   - parameter: ne = 10^3 cm^-3, case B  
  > "We fixed the $n\rm{_e}$ to $10^3$ cm$^{-3}$" (3.1)
   - fitting: _not stated_
   - validation: _not stated_
4. **Molecular gas mass**: M_H2 = 0.41 R12/13 L'13CO, optically thin LTE  
  > "It is assumed that the excitation temperature of 10 K (cite: Harada_2018) and the $^{12}$CO/$^{13}$CO ratios ($R_{12/13}$) of $\sim100$ (cite: Henkel_2014) are constant." (3.2)
   - assumption: R12/13 ~ 100  
  > "the $^{12}$CO/$^{13}$CO ratios ($R_{12/13}$) of $\sim100$ (cite: Henkel_2014) are constant" (3.2)
   - fitting: _not stated_
   - validation: _not stated_
5. **Total SFR and nuclear vs disk-wide split**: Total = SFR(Hbeta total) minus Hbeta SFR of the three regions plus H40a SFR of the three regions  
  > "$=40-(6.8+1.7+0.47)+(9.8+6.8+0.98)\sim48\pm2$ $M_{\odot}$ yr$^{-1}$." (3.3 Results)
   - fitting: _not stated_
   - validation: BPT-selected pure HII SFR ~40 consistent with Hbeta total  
  > "The total SFR from pure H $_{\rm II}$ regions is calculated as $\sim40$ $M_{\odot}$ yr$^{-1}$" (3.3 Results)

## Software

- **CASA** : imfit Gaussian fitting of H40a map  
  > "we use the ${\tt imfit}$ task in ${\tt CASA}$ to fit elliptical Gaussian components" (2.2)

## Numeric results

| quantity | value | uncertainty | units | step | quote |
|---|---|---|---|---|---|
| Total SFR (Hbeta+H40a) | 48 | 2 | Msun/yr | 5 | $=40-(6.8+1.7+0.47)+(9.8+6.8+0.98)\sim48\pm2$ $M_{\odot}$ yr$^{-1}$. |
| SFR H40a southern nucleus | 6.8 | 0.3 | Msun/yr | 3 | / Southern Nucleus / 143$\pm$7 / 5.96$\pm$0.30 / 24$\pm$2 / $10200^{+700}_{-600}$ / 6.8$\pm$0.3 / |
| Te northern nucleus | 5900 | +400/-400 | K | 3 | / Northern Nucleus / 273$\pm$14 / 6.36$\pm$0.32 / 43$\pm$3 / $5900^{+400}_{-400}$ / 9.8$\pm$0.5 / |
| Te southern nucleus | 10200 | +700/-600 | K | 3 | / Southern Nucleus / 143$\pm$7 / 5.96$\pm$0.30 / 24$\pm$2 / $10200^{+700}_{-600}$ / |
| Nuclear SFR sum | 16.6 | 0.6 | Msun/yr | 5 | The sum of the nuclear starbursts in the northern and southern nuclei derived from the H$40\alpha$ data is $16.6\pm0.6~M_\odot$ yr$^{-1}$. |
| SFR/L_TIR ratio | 2.63e-44 | 0.17e-44 | Msun/yr per erg/s | 5 | the ratio between SFR$_{\rm RL}$ and $L_{\rm TIR}$ is estimated to be $(2.63\pm0.17)\times10^{-44}$ |

## Qualitative findings

- Disk-wide star formation dominates (~66%) over nuclear (~34%)  
  > "the contributions of the nuclear and disk-wide starbursts are $\sim34~\%$ and $\sim66~\%$, respectively" (5.3)

## Claim tuples

- H: Disk-wide starbursts dominate total SFR in NGC 3256 | E: Combine MUSE Hbeta with ALMA H40a in dusty nuclei | R: Nuclear 16.6 of ~48 Msun/yr | F: Disk-wide ~66%, nuclear ~34% | **supported**
- H: Shocks regulate disk-wide star formation | E: Pixel-by-pixel comparison of CH3OH/13CO with gas depletion time | R: Spearman coefficient 0.315, p=0.002 | F: Possible weak correlation | **partially**
- H: Current starburst was triggered by the merger | E: Compare SFR_RL/L_TIR with Calzetti calibrations | R: Ratio consistent with 100 Myr | F: Starburst ~100 Myr old, shorter than merger age | **supported**

## Reasoning

- Why this data: _not stated_
- Why this method: mm recombination lines are unaffected by dust extinction  
  > "One of the best methods of investigating the properties of star formation activities in such extremely dusty regions is hydrogen recombination lines in the millimeter (mm) range" (1 Introduction)
- Alternative: H40a not from AGN (line width ~300 km/s, not >1000)  
  > "Therefore, the H$40\alpha$ emission is likely originated from star formation activity at the southern nucleus." (5.6)
- How they decided it was enough: _not stated_
- Limitation (authors): Statistical significance of shock correlation is weak  
  > "although the statistical significance is not very strong" (5.3)
- Caveat (inferred, ours): Southern Te differs between text (11500 K) and table/summary (10200 K)
- Caveat (inferred, ours): Total SFR quoted as 49 in abstract and 48 elsewhere
- Caveat (inferred, ours): Free-free fraction uncertain; Te derived from R depends on it
- Caveat (inferred, ours): Acknowledgments list 2015.1.00714.S not in Table 1 while 2016.1.00965.S is omitted

## Reproducibility

- Data public (paper): MUSE cube from ESO archive; ALMA archive data  
  > "The processed MUSE 3D data cube of NGC 3256 can be downloaded from the ESO science archive portal" (2.1 MUSE)
- Products in archive: _not stated_
- Missing: ALMA calibration/imaging parameters
- Missing: SED fit priors
- Missing: Pixel analysis regridding
- Data volume (inferred): ~50-200 GB raw for several ALMA execution blocks
- Score (inferred): 3/5, Formulas and tables given, but ALMA processing details are largely absent.
- Rediscovery candidate: no, Imaging recipe incomplete and SED fits and MUSE products are not fully specified.

## Links

- Method: (cite: Bendo_2016) (SFR from recombination lines and free-free emission)
- Method: (cite: Erroz-Ferrer_2019) (MUSE MAD data products)
- Companion: (cite: Harada_2018) (ALMA broad-band spectral survey of NGC 3256)
- Related: MUSE Atlas of Disks (MAD)

## Checks

```json
{
 "quotes": 58,
 "quotes_ok": 58,
 "quote_pass_rate": 1.0,
 "quotes_too_long": 0,
 "unsupported_facts": 0,
 "project_codes": 3,
 "codes_not_in_text": [],
 "codes_not_in_obscore": [],
 "obscore_codes_not_in_card": [],
 "codes_printed_but_missing": [
  "2015.1.00714.S"
 ],
 "numeric_results": 6,
 "numeric_problems": 0,
 "fill": {
  "facts": 75,
  "stated": 38,
  "rate": 0.507
 },
 "evidence_ok": true
}
```
