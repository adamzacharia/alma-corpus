# Discovery of Dying Active Galactic Nucleus in Arp 187: Experience of Drastic Luminosity Decline within 10<SUP>4</SUP> yr

`2019ApJ...870...65I` | The Astrophysical Journal 2019 | first author: Ichikawa, Kohei | arXiv: 1811.07447 | DOI: 10.3847/1538-4357/aaf233

Card schema 1.0 | model claude-sonnet-5-5 | depth full | type multi_facility_alma_minor

## Science

- Fields: agn_and_quasars, nearby_galaxies
- Question: Does Arp 187 host a dying AGN whose central engine is quenched, and how rapidly did its luminosity decline over ~10^4 yr?  
  > "We investigate the observational signatures of AGN in Arp 187, which trace various physical scales from less than 0.1 pc to the nearly 10 kpc, to estimate the longterm luminosity change over $10^{4}$ years." (abstract)
- Target **Arp 187**: coordinates _not stated_; z/distance z=0.040, D_L = 178 Mpc  
  > "Arp 187 located at $z=0.040$ ($D_{\rm L}$ = 178 Mpc, 1$''$ = 798 pc)" (Introduction); distance from not stated (H0=70, OmegaM=0.3, OmegaL=0.7 adopted)  
  > "Arp 187 located at $z=0.040$ ($D_{\rm L}$ = 178 Mpc, 1$''$ = 798 pc)" (Introduction)

## Data provenance

- ALMA projects: 2015.1.01005.S
- bands: Band 4 (center 133 GHz)  
  > "The Band 4 continuum observation of Arp 187 was carried out using the ALMA 12-m array on 2016 July 25" (2.1 Radio Continuum Emission: Existence of Radio Jet-Lobe)
- frequencies and spectral setup: _not stated_
- continuum bandwidth: 4 SPWs, total 8 GHz  
  > "The center frequency of the four SPWs is 133 GHz, and the total bandwidth is 8 GHz." (2.1 Radio Continuum Emission: Existence of Radio Jet-Lobe)
- arrays: _not stated_
- configurations: _not stated_
- baselines: 15 m to 1124 m; 36 antennas  
  > "The baseline lengths range from 15 m to 1124 m." (2.1 Radio Continuum Emission: Existence of Radio Jet-Lobe)
- angular resolution: 0.46" x 0.39", PA=-82.7 deg  
  > "The synthesized beam size is $0.46\ensuremath{''} \times 0.39\ensuremath{''}$ (position angle ${\rm (PA)} = -82.7\ensuremath{^\circ}$)" (2.1 Radio Continuum Emission: Existence of Radio Jet-Lobe)
- max recoverable scale: _not stated_
- sensitivity: rms 0.013 mJy/beam  
  > "the rms noise level is 0.013 mJy beam$^{-1}$" (2.1 Radio Continuum Emission: Existence of Radio Jet-Lobe)
- time on source: _not stated_
- observing dates: 2016 July 25  
  > "using the ALMA 12-m array on 2016 July 25" (2.1 Radio Continuum Emission: Existence of Radio Jet-Lobe)
- pi or archival as stated: _not stated_
- Other facility **VLA C- and X-bands**: archival calibrated uv data at 4.86 and 8.44 GHz  
  > "we used archival calibrated $uv$ data obtained with VLA C- and X-bands, and made the continuum maps using CASA." (2.1 Radio Continuum Emission: Existence of Radio Jet-Lobe)
- Other facility **6dF**: archival optical spectrum  
  > "We first obtained the archival optical spectrum of Arp 187 from the 6dF galaxy survey" (2.2 6dF Optical Spectra)
- Other facility **WISE/NEOWISE**: multi-epoch IR light curves  
  > "we have collected both cryogenic (*WISE* All-sky database) and post-cryogenic multi-epoch photometry" (2.5 WISE IR Time Variability)
- External data: Spitzer/IRS results (L12um < 1.5e42 erg/s, [OIV] luminosity)  
  > "Since the detailed spectral analysis of Arp 187 obtained from the *Spitzer*/InfraRed Spectrograph (IRS) is compiled in (cite: ich16)" (2.3 Spitzer/IRS Spectra) [from (cite: ich16)]
- External data: Swift/BAT 105 month survey limiting flux  
  > "limiting flux at the 14–195 keV band of $f_{\rm 14-195}^{(\rm lim)}=8.0\times 10^{-12}$ erg s$^{-1}$ cm$^{-2}$ (cite: oh18)" (2.7 X-ray Observations) [from (cite: oh18)]

## Processing

### Calibration

- pipeline or manual: delivered calibrated uv data used  
  > "We used the delivered calibrated $uv$ data and made the continuum map by clipping the visibility" (2.1 Radio Continuum Emission: Existence of Radio Jet-Lobe)
- casa version: CASA 4.5.3  
  > "(CASA, ver. 4.5.3)" (2.1 Radio Continuum Emission: Existence of Radio Jet-Lobe)
- pipeline version: _not stated_
- archive products used as is: yes, delivered calibrated uv data  
  > "We used the delivered calibrated $uv$ data" (2.1 Radio Continuum Emission: Existence of Radio Jet-Lobe)
- flux calibrator: _not stated_
- flux scale uncertainty: 5%  
  > "We regard the accuracy of the absolute flux calibration as 5% throughout this paper" (2.1 Radio Continuum Emission: Existence of Radio Jet-Lobe)
- self calibration: _not stated_

### Imaging

- task: _not stated_
- deconvolver: _not stated_
- weighting robust: Briggs robust = 0.5 (ALMA and VLA 8.44 GHz); uniform for VLA 4.86 GHz  
  > "by adopting Briggs weighting of the visibility $({\rm robust} = 0.5)$" (2.1 Radio Continuum Emission: Existence of Radio Jet-Lobe); "by adopting uniform weighting of the visibility" (2.1 Radio Continuum Emission: Existence of Radio Jet-Lobe)
- uv taper: uv distance >= 10 kλ clipping (common shortest UV range for VLA and ALMA)  
  > "made the continuum map by clipping the visibility ($uv$ distance $\geq 10$k$\lambda$)" (2.1 Radio Continuum Emission: Existence of Radio Jet-Lobe)
- cell size: _not stated_
- image size: _not stated_
- masking: _not stated_
- multiscale scales: _not stated_
- continuum subtraction: _not stated_
- line free channels: _not stated_
- primary beam correction: _not stated_
- array combination: _not stated_
- smoothing: maps convolved to 0.47" for SEDs  
  > "We also convolved these maps to $0.47\ensuremath{''}$ angular resolution to make Spectral Energy Distributions" (2.1 Radio Continuum Emission: Existence of Radio Jet-Lobe)
- final beam: 0.46" x 0.39" (ALMA)  
  > "The synthesized beam size is $0.46\ensuremath{''} \times 0.39\ensuremath{''}$" (2.1 Radio Continuum Emission: Existence of Radio Jet-Lobe)
- final rms: 0.013 mJy/beam  
  > "the rms noise level is 0.013 mJy beam$^{-1}$" (2.1 Radio Continuum Emission: Existence of Radio Jet-Lobe)

### Inherited from earlier work

- Optical spectral fitting routine  
  > "we follow the routine in (cite: bae17) and later (cite: tob17a)" (2.2 6dF Optical Spectra) [from (cite: bae17); (cite: tob17a)]
- Spitzer/IRS analysis  
  > "the detailed spectral analysis of Arp 187 obtained from the *Spitzer*/InfraRed Spectrograph (IRS) is compiled in (cite: ich16)" (2.3 Spitzer/IRS Spectra) [from (cite: ich16)]
- Disk aspect ratio h/R~0.05  
  > "we assume $h/R \sim 0.05$ by following (cite: ste18)" (3.2 Luminosity Decline) [from (cite: ste18)]

### Not stated but needed to reproduce (our reading)

- Phase/flux/bandpass calibrators for ALMA
- Exact tclean parameters (cell, image size, deconvolver, threshold, mask)
- VLA project codes, dates and calibration details
- Method and apertures for lobe flux measurement
- Kinematic-age expansion speed value
- Core flux extraction region for 133 GHz limit
- Stellar template fit details beyond masks

## Analysis recipe

1. **Image ALMA and VLA continuum**: Clip uv range to common minimum, image with CASA using Briggs/uniform weighting  
  > "We clipped the visibilities before imaging so that all the VLA and ALMA data have the same shortest UV range." (2.1 Radio Continuum Emission: Existence of Radio Jet-Lobe)
   - software: CASA
   - parameter: robust = 0.5; uv >= 10 kλ  
  > "by adopting Briggs weighting of the visibility $({\rm robust} = 0.5)$" (2.1 Radio Continuum Emission: Existence of Radio Jet-Lobe)
   - fitting: _not stated_
   - validation: _not stated_
2. **Lobe radio SED and spectral index**: Convolve to 0.47", measure peak/total flux, fit f_nu ∝ nu^alpha from 4.86 and 8.44 GHz  
  > "The spectral index $\alpha$ was estimated from two points at 4.86 GHz and 8.44 GHz by using a fitting function of $f_\nu\propto\nu^\alpha$." (2.1 Radio Continuum Emission: Existence of Radio Jet-Lobe)
   - fitting: _not stated_
   - validation: 133 GHz point compared with extrapolation  
  > "the flux point at 133 GHz is nearly on the extrapolated line from the VLA bands" (2.1 Radio Continuum Emission: Existence of Radio Jet-Lobe)
3. **Fit 6dF spectrum and derive L_bol, NLR size**: Subtract stellar continuum, fit emission lines with Gaussians, apply [OIII]+[OI] L_bol relation and size-luminosity relations  
  > "using the IDL/MPFIT code, which is a $\chi^2$-minimization routine (cite: mar09)" (2.2 6dF Optical Spectra)
   - software: IDL/MPFIT
   - assumption: Extinction correction via Balmer decrement  
  > "We also calculate an extinction-corrected, intrinsic luminosity of \[O III\] ($L_{\rm [OIII]}^{\rm int}$) and \[O I\] ($L_{\rm [OI]}^{\rm int}$) luminosities from the Balmer decrement" (2.2 6dF Optical Spectra)
   - fitting: _not stated_
   - validation: BPT classification as AGN  
  > "Figure [4](#fig:BPT) shows that Arp 187 is classified as AGN." (2.2.1 Existence of NLR)
4. **Compile torus/X-ray/fundamental plane upper limits and timescales**: WISE light curve and colors, L12-L[OIII] relation, X-ray upper limits, BH fundamental plane; thin-disk timescales  
  > "We here consider three possible timescales: the orbital, thermal, and the viscous (inflow) timescales" (3.2 Luminosity Decline and Corresponding Timescales)
   - parameter: alpha~0.03, h/R~0.05, eta~0.1  
  > "The typical value is estimated as $\eta \sim 0.1$ (cite: sol82)." (3.2 Luminosity Decline and Corresponding Timescales)
   - assumption: M_BH = 6.7e8 Msun  
  > "the black hole mass in Arp 187 is estimated to be $M_{\rm BH}=6.7 \times 10^8$ $M_{\odot}$" (2.8 Black Hole Fundamental Plane)
   - fitting: _not stated_
   - validation: _not stated_

## Software

- **CASA** 4.5.3: calibration and imaging of ALMA and VLA continuum  
  > "Data calibration and imaging were carried out using the Common Astronomy Software Applications package (CASA, ver. 4.5.3)." (2.1 Radio Continuum Emission: Existence of Radio Jet-Lobe)
- **IDL/MPFIT** : emission-line fitting  
  > "using the IDL/MPFIT code, which is a $\chi^2$-minimization routine (cite: mar09)" (2.2 6dF Optical Spectra)
- **astropy** : listed in Software section  
  > "astropy (cite: ast13), Matplotlib (cite: hun07), Pandas (cite: mck10)" (Software)

## Numeric results

| quantity | value | uncertainty | units | step | quote |
|---|---|---|---|---|---|
| ALMA synthesized beam rms | 0.013 | not stated | mJy/beam | 1 | the rms noise level is 0.013 mJy beam$^{-1}$ |
| Spectral index of eastern lobe | -0.59 | not stated | dimensionless | 2 | The SED shows a steep spectral index of $\alpha\approx-0.59$ for the eastern lobe |
| 133 GHz core flux density | <=0.052 | not stated | mJy | 2 | the observed 133 GHz flux density is $\leq0.052$ mJy |
| Kinematic age of lobes | ~8e4 | not stated | yr | 2 | This gives the kinematic age of $\sim8 \times 10^4$ years. |
| log L_bol from [OIII]+[OI] | 46.2 | not stated | log erg/s | 3 | The estimated value is $\log (L_{\rm bol}/{\rm erg}~{\rm s}^{-1}) = 46.2$ |
| NLR size range | 530-1400 | not stated | pc | 3 | In this study, we assume $R_{\rm NLR}=530$–$1400$ pc as the possible NLR size range. |
| L_bol upper bound from fundamental plane | <=8.0e40 | not stated | erg/s | 4 | This is equivalent to $L_{\rm bol} \leq 8.0 \times 10^{40}$ erg s$^{-1}$ |

## Qualitative findings

- Western lobe 133 GHz flux below power-law extrapolation, suggesting spectral aging  
  > "This suggests the spectral aging for the western jet" (2.1 Radio Continuum Emission: Existence of Radio Jet-Lobe)

## Claim tuples

- H: Is the central engine of Arp 187 already quenched? | E: Multi-wavelength AGN indicators across scales | R: Core absent in radio, weak torus, no WISE variability; NLR and lobes present | F: Arp 187 hosts a dying AGN | **supported**
- H: How fast did luminosity decline? | E: Compare past L_bol from NLR with current upper limits | R: Decline by 10^{3-5} within ~10^4 yr | F: Matches viscous timescale of inner disk | **partially**

## Reasoning

- Why this data: _not stated_
- Why this method: _not stated_
- Alternative: Highly obscured AGN scenario rejected due to absent torus emission and radio core  
  > "The first scenario is unlikely for Arp 187 because of the two reasons." (4.1 AGN Indicators and Scenarios of Current AGN Activity)
- How they decided it was enough: _not stated_
- Limitation (authors): NLR size poorly constrained without IFU  
  > "the optical or near-IR IFU will also give us the detailed NLR size which is poorly constrained with the current study." (Future observations)
- Caveat (inferred, ours): ALMA is one of many datasets; lobe fluxes lack uncertainties
- Caveat (inferred, ours): NLR size from empirical relations with large scatter
- Caveat (inferred, ours): Spectral index from only two points
- Caveat (inferred, ours): Timescale argument is rough

## Reproducibility

- Data public (paper): archival/delivered data used  
  > "We used the delivered calibrated $uv$ data" (2.1 Radio Continuum Emission: Existence of Radio Jet-Lobe)
- Products in archive: _not stated_
- Missing: VLA project IDs
- Missing: Imaging parameters
- Missing: Expansion speed assumed for kinematic age
- Data volume (inferred): ~10-50 GB (ALMA Band 4 plus VLA)
- Score (inferred): 3/5, ALMA part reproducible from public data, but many multiwavelength inputs and some steps underspecified.
- Rediscovery candidate: no, Main results depend on many non-ALMA datasets and empirical relations; imaging recipe is incomplete.

## Links

- Method: (cite: bae17) (Spectral fitting and NLR size-luminosity relation)
- Companion: (cite: ich16) (Earlier Arp 187 study with Spitzer/IRS and ALMA cycle-0 data)
- Related: 6dF Galaxy Survey
- Related: WISE/NEOWISE
- Related: Swift/BAT 105 month survey

## Checks

```json
{
 "quotes": 55,
 "quotes_ok": 55,
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
  "facts": 73,
  "stated": 43,
  "rate": 0.589
 },
 "evidence_ok": true
}
```
