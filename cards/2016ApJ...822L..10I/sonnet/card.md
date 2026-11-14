# ALMA 0.1-0.2 arcsec Resolution Imaging of the NGC 1068 Nucleus: Compact Dense Molecular Gas Emission at the Putative AGN Location

`2016ApJ...822L..10I` | The Astrophysical Journal Letters 2016 | first author: Imanishi, Masatoshi | arXiv: 1604.03953 | DOI: 10.3847/2041-8205/822/1/L10

Card schema 1.0 | model claude-sonnet-5-5 | depth full | type observational_alma_primary

## Science

- Fields: nearby_galaxies, agn_and_quasars
- Question: Can compact dense molecular gas emission (HCN and HCO+ J=3-2) from the putative dusty torus at the AGN location in NGC 1068 be separated from the brighter eastern and western knots at 0.1-0.2 arcsec resolution, and what are its properties?  
  > "Molecular gas observation with even higher angular resolution may better reveal the molecular emission arising from the dusty molecular torus." (1 Introduction)
- Target **NGC 1068**: coordinates 02h42m40.71s, -00d00m47.94s (J2000)  
  > "NGC 1068 (z = 0.0037, distance = 14 Mpc, 1 arcsec is $\sim$70 pc)" (1 Introduction); "The peak coordinate agrees with the reported AGN location at (02$^{h}$42$^{m}$40.71$^{s}$, $-$00$^{\circ}$00$'$47.94$''$)J2000" (3 Results); z/distance z = 0.0037, 14 Mpc  
  > "NGC 1068 (z = 0.0037, distance = 14 Mpc, 1 arcsec is $\sim$70 pc)" (1 Introduction); "The peak coordinate agrees with the reported AGN location at (02$^{h}$42$^{m}$40.71$^{s}$, $-$00$^{\circ}$00$'$47.94$''$)J2000" (3 Results); distance from _not stated_

## Data provenance

- ALMA projects: 2013.1.00188.S
- bands: Band 6 (211-275 GHz)  
  > "Band 6 (211–275 GHz) ALMA observations of the nucleus of NGC 1068 were conducted" (2 Observations and data analysis)
- frequencies and spectral setup: 263.9-268.6 GHz with three spectral windows, 1.875 GHz width mode  
  > "We covered 263.9–268.6 GHz with three spectral windows" (2 Observations and data analysis); "we adopted the widest 1.875 GHz width mode in each spectral window" (2 Observations and data analysis)
- continuum bandwidth: _not stated_
- arrays: _not stated_
- configurations: _not stated_
- baselines: 41-2270 m, 36 antennas  
  > "There were 36 antennas, and the baseline lengths were 41–2270 m." (2 Observations and data analysis)
- angular resolution: 0.23x0.12 arcsec continuum; 0.1-0.2 arcsec lines  
  > "The achieved angular resolution was 0$\ensuremath{''}$23$\times$0$\ensuremath{''}$12" (3 Results)
- max recoverable scale: ~4.0 arcsec  
  > "and $\sim$4$\ensuremath{''}$0, respectively." (2 Observations and data analysis)
- sensitivity: _not stated_
- time on source: 24.9 min  
  > "The total net on-source integration time was 24.9 min." (2 Observations and data analysis)
- observing dates: 2015 September 19 (UT)  
  > "on 2015 September 19 (UT), with a median precipitable water vapor value of $\sim$1.9 mm" (2 Observations and data analysis)
- pi or archival as stated: Own Cycle 2 program (PI M. Imanishi)  
  > "our Cycle 2 program 2013.1.00188.S (PI = M. Imanishi)" (2 Observations and data analysis)
- Line: HCN J=3-2 (265.886 GHz)
- Line: HCO+ J=3-2 (267.558 GHz)
- Line: HCN v2=1f J=3-2 (267.199 GHz)
- Line: HCO+ v2=1f J=3-2 (268.689 GHz)
- External data: Clumpy torus model: torus outer size 20 (+6/-10) pc and gas mass (2.1±1.2)e5 Msun  
  > "(2.1$\pm$1.2)$\times$10$^{5}$ M$_{\odot}$" (4.1 Molecular emission from the putative AGN dusty torus) [from (cite: gar14)]
- External data: AGN location coordinates  
  > "reported AGN location at (02$^{h}$42$^{m}$40.71$^{s}$, $-$00$^{\circ}$00$'$47.94$''$)J2000" (3 Results) [from (cite: roy98; gar14)]
- External data: AGN luminosity L_AGN ~ 6e44 erg/s  
  > "central AGN luminosity of L$_{\rm AGN}$ $\sim$ 6 $\times$ 10$^{44}$ \[erg s$^{-1}$\]" (4.3 Molecular emission at the nuclear region) [from (cite: boc00)]

## Processing

### Calibration

- pipeline or manual: Calibrated data provided by the JAO used  
  > "Data analysis began with calibrated data provided by the Joint ALMA Observatory, using CASA 4.5.0" (2 Observations and data analysis)
- casa version: CASA 4.5.0  
  > "using CASA 4.5.0" (2 Observations and data analysis)
- pipeline version: _not stated_
- archive products used as is: Calibrated data from JAO  
  > "calibrated data provided by the Joint ALMA Observatory" (2 Observations and data analysis)
- flux calibrator: J0334-401 (bandpass J0224+0659, phase J0219+0120)  
  > "J0224$+$0659, J0334$-$401, and J0219$+$0120 were used as bandpass, flux, and phase calibrators, respectively." (2 Observations and data analysis)
- flux scale uncertainty: <30%  
  > "The absolute flux calibration uncertainty and maximum recoverable scale of our ALMA band 6 data are $<$30%" (2 Observations and data analysis)
- self calibration: _not stated_

### Imaging

- task: CASA clean; mfs for continuum  
  > "applied the task “clean” (natural weighting, gain $=$ 0.1, threshold $=$ 0.8 mJy)" (2 Observations and data analysis)
- deconvolver: _not stated_
- weighting robust: natural weighting  
  > "natural weighting, gain $=$ 0.1, threshold $=$ 0.8 mJy" (2 Observations and data analysis)
- uv taper: _not stated_
- cell size: 0.03 arcsec/pixel  
  > "utilized a pixel scale of 0$\ensuremath{''}$03 pixel$^{-1}$" (2 Observations and data analysis)
- image size: _not stated_
- masking: _not stated_
- multiscale scales: _not stated_
- continuum subtraction: constant continuum level subtracted with uvcontsub  
  > "We subtracted the estimated constant continuum level using the CASA task “uvcontsub”" (2 Observations and data analysis)
- line free channels: channels not affected by strong emission lines (not specified)  
  > "we estimated the continuum flux level using channels that were not affected by strong emission lines" (2 Observations and data analysis)
- primary beam correction: applied to all data  
  > "we applied the primary beam correction to all data" (2 Observations and data analysis)
- array combination: _not stated_
- smoothing: binned 40 channels (~20 km/s)  
  > "we binned 40 channels ($\sim$20 km s$^{-1}$)" (2 Observations and data analysis)
- final beam: 0.23x0.12 arcsec continuum; 0.22x0.13 (HCN), 0.24x0.13 (HCO+)  
  > "0.22$\times$0.13 (54$^{\circ}$)" (Table 1)
- final rms: 0.32 (HCN), 0.15 (HCO+) Jy/beam km/s in moment 0; continuum peak 51 sigma at 9.2 mJy/beam  
  > "The peak flux is estimated to be 9.2 mJy beam$^{-1}$ (51$\sigma$)" (3 Results)

### Inherited from earlier work

- Conversion of HCN J=3-2 to J=1-0 luminosity via Solomon & Vanden Bout equations  
  > "derived using Equations (1) and (3) of (cite: sol05)" (4.1 Molecular emission from the putative AGN dusty torus) [from (cite: sol05)]
- Dense gas mass = 10 x HCN J=1-0 luminosity  
  > "M$_{\rm dense}$ = 10 $\times$ HCN J=1–0 luminosity" (4.1 Molecular emission from the putative AGN dusty torus) [from (cite: gao04; kri08)]
- FIR luminosity from free-free emission using Equation (1)  
  > "when Equation (1) of (cite: nak05) is used" (4.2 Continuum emission) [from (cite: nak05)]

### Not stated but needed to reproduce (our reading)

- Line-free channel ranges used for continuum estimation
- Clean mask/iteration settings and image size
- Continuum bandwidth and exact channels used for the mfs image
- Gaussian-fit procedure and baseline treatment for spectra
- imfit region/parameters for deconvolved size
- Exact continuum-to-free-free conversion assumptions (temperature, spectral index)

## Analysis recipe

1. **Continuum subtraction and imaging**: uvcontsub with constant continuum, then clean with natural weighting; mfs for continuum  
  > "We subtracted the estimated constant continuum level using the CASA task “uvcontsub”" (2 Observations and data analysis)
   - software: CASA
   - parameter: gain 0.1, threshold 0.8 mJy, 40 channels binned, 0.03 arcsec pixel  
  > "natural weighting, gain $=$ 0.1, threshold $=$ 0.8 mJy" (2 Observations and data analysis)
   - fitting: _not stated_
   - validation: PSFs checked for clean sidelobes  
  > "We have confirmed that the PSFs of our data are fairly clean" (2 Observations and data analysis)
2. **Moment maps and spectral Gaussian fits**: Moment 0 and 1 maps; Gaussian fits to spectra at E-peak, W-subpeak, C-peak and 2.4 arcsec radius region  
  > "Gaussian fits for the HCN J=3–2 and HCO$^{+}$ J=3–2 emission lines in the spectra, within the beam size, at the E-peak, W-subpeak, and C-peak" (3 Results)
   - fitting: Gaussian fits; two components at C-peak  
  > "At the C-peak, two Gaussian fits are made because a very broad component is observed" (Table 1)
   - validation: _not stated_
3. **Torus size and dense gas mass**: imfit for deconvolved size; HCN J=3-2 to J=1-0 luminosity assuming thermalized optically thick; M_dense=10 x L'HCN(1-0)  
  > "If HCN emission is thermalized at up to J=3 and optically thick, then the HCN J=1–0 flux is 1/9 of the HCN J=3–2 flux." (4.1 Molecular emission from the putative AGN dusty torus)
   - software: CASA imfit
   - assumption: HCN thermalized to J=3 and optically thick; conversion factor 10 Msun/(K km/s pc^2)  
  > "M$_{\rm dense}$ = 10 $\times$ HCN J=1–0 luminosity" (4.1 Molecular emission from the putative AGN dusty torus)
   - fitting: _not stated_
   - validation: Compared to clumpy torus model gas mass of Garcia-Burillo et al.  
  > "which roughly agrees to the gas mass estimated with the clumpy torus model" (4.1 Molecular emission from the putative AGN dusty torus)
4. **Star formation estimate in SW region**: Continuum flux in rectangle assuming solely free-free emission, converted to FIR luminosity and SFR  
  > "If this is solely due to the thermal free-free emission inside star-forming HII-regions" (4.2 Continuum emission)
   - assumption: Emission purely thermal free-free (upper limit)  
  > "If dust thermal radiation contributes in some way to the continuum flux there, the estimated star-formation luminosity will be smaller." (4.2 Continuum emission)
   - fitting: _not stated_
   - validation: Compared to PAH-based upper limit from infrared spectroscopy  
  > "This upper limit is apparently smaller than the above estimate but can be reconciled" (4.2 Continuum emission)

## Software

- **CASA** 4.5.0: Data analysis: uvcontsub, clean, imfit  
  > "using CASA 4.5.0" (2 Observations and data analysis)

## Numeric results

| quantity | value | uncertainty | units | step | quote |
|---|---|---|---|---|---|
| Continuum peak flux | 9.2 | not stated | mJy/beam | 1 | The peak flux is estimated to be 9.2 mJy beam$^{-1}$ (51$\sigma$) |
| HCN J=3-2 deconvolved size at C-peak | 175x92 mas (12.3x6.2 pc) | ±52, ±31 mas | mas | 3 | 175$\pm$52 \[mas\] $\times$ 92$\pm$31 \[mas\], or 12.3$\pm$3.6 \[pc\] $\times$ 6.2$\pm$2.2 \[pc\] |
| HCN J=1-0 luminosity at C-peak | 8.8e4 | 2.6e4 | K km/s pc^2 | 3 | (8.8$\pm$2.6)$\times$10$^{4}$ \[K km s$^{-1}$ pc$^{2}$\] |
| Dense molecular mass in torus | several x 1e5 | large potential uncertainty | Msun | 3 | we obtain a dense molecular mass in the torus of several $\times$ 10$^{5}$ M$_{\odot}$ |
| HCN J=3-2 flux at C-peak | 1.1 | 0.3 | Jy km/s | 2 | 1.1$\pm$0.3 |
| SW region continuum flux | ~10 | not stated | mJy | 4 | to be $\sim$10 mJy |
| SW star-formation FIR luminosity | ~6e43 | not stated | erg/s | 4 | $\sim$6 $\times$ 10$^{43}$ \[erg s$^{-1}$\] |
| SW star formation rate | ~3 | not stated | Msun/yr | 4 | a star formation rate of $\sim$3 M$_{\odot}$ yr$^{-1}$ |
| HCN-to-HCO+ J=3-2 flux ratio | 1.6-3.3 | not stated | dimensionless | 2 | The HCN-to-HCO$^{+}$ J=3–2 flux ratios were 1.6–3.3 (Table 1) |
| Vibrationally excited line 3-sigma upper limit | <0.15 | not stated | Jy/beam km/s | 2 | 3$\sigma$ upper limits of $<$0.15 \[Jy beam$^{-1}$ km s$^{-1}$\] |

## Qualitative findings

- Continuum elongated along radio jet direction to the north of the AGN  
  > "The continuum emission displayed an elongated morphology along the direction of the radio jet located at the northern side of the AGN" (abstract)
- Broad emission component detected only at the C-peak  
  > "A broad emission component is detected at the C-peak, but not in the other regions." (3 Results)

## Claim tuples

- H: Compact dense gas emission from the dusty torus can be isolated at the AGN position | E: HCN and HCO+ J=3-2 imaging at 0.1-0.2 arcsec | R: Compact emission detected at the 266 GHz continuum peak with size ~12x6 pc | F: Dense gas emission is associated with the putative torus, mass several x1e5 Msun | **supported**
- H: Nuclear region has enhanced HCN/HCO+ ratio due to AGN | E: Gaussian-fit flux ratios at four positions | R: Ratios 1.6-3.3 | F: Explained naturally by the AGN effect | **supported**
- H: SW continuum component arises from star formation | E: Continuum flux and free-free luminosity conversion | R: ~10 mJy, L_SF < 6e43 erg/s, ~3 Msun/yr | F: Star formation with luminosity an order of magnitude below AGN | **supported**

## Reasoning

- Why this data: Higher resolution than previous studies needed to separate torus emission from brighter knots  
  > "the emission is overwhelmed by the much brighter nearby eastern knot" (1 Introduction)
- Why this method: _not stated_
- How they decided it was enough: _not stated_
- Limitation (authors): Only one pointing; star-forming ring at 10-15 arcsec not adequately probed  
  > "dense molecular gas emission from the well-known star-forming molecular gas ring at 10–15 arcsec from the nucleus" (2 Observations and data analysis)
- Limitation (authors): Dense mass has large potential uncertainty  
  > "(with large potential uncertainty)" (4.1 Molecular emission from the putative AGN dusty torus)
- Caveat (inferred, ours): Torus size from imfit has large errors; HCO+ size is unconstrained
- Caveat (inferred, ours): Single-epoch short observation with low S/N (3.4-4.5 sigma) at C-peak
- Caveat (inferred, ours): Mass depends on thermalization assumption and HCN conversion factor
- Caveat (inferred, ours): Continuum at C-peak may include jet synchrotron contribution

## Reproducibility

- Data public (paper): Project code given; ALMA data acknowledged  
  > "This paper makes use of the following ALMA data: ADS/JAO.ALMA#2013.1.00188.S." (Acknowledgments)
- Products in archive: _not stated_
- Missing: Line-free channels
- Missing: Image size and masks
- Missing: imfit settings
- Missing: Free-free conversion assumptions
- Data volume (inferred): ~20-50 GB
- Score (inferred): 3/5, Short letter with single dataset and public CASA tasks, but several imaging and fitting details are missing.
- Rediscovery candidate: yes, Data public, simple CASA workflow, numeric results (fluxes, size, ratios) available.

## Links

- Companion: (cite: gar14) Garcia-Burillo et al. 2014 (Prior ALMA Cycle 0 observations and torus model)

## Checks

```json
{
 "quotes": 71,
 "quotes_ok": 71,
 "quote_pass_rate": 1.0,
 "quotes_too_long": 0,
 "unsupported_facts": 0,
 "project_codes": 1,
 "codes_not_in_text": [],
 "codes_not_in_obscore": [],
 "obscore_codes_not_in_card": [],
 "codes_printed_but_missing": [],
 "numeric_results": 10,
 "numeric_problems": 0,
 "fill": {
  "facts": 69,
  "stated": 49,
  "rate": 0.71
 },
 "evidence_ok": true
}
```
