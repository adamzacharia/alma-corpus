# Luminous, pc-scale CO 6-5 emission in the obscured nucleus of NGC 1377

`2017A&A...608A..22A` | Astronomy and Astrophysics 2017 | first author: Aalto, S. | arXiv: 1702.05458 | DOI: 10.1051/0004-6361/201730650

Card schema 1.0 | model claude-sonnet-5-5 | depth full | type observational_alma_primary

## Science

- Fields: nearby_galaxies, agn_and_quasars
- Question: What are the structure, dynamics and obscuration of the nucleus of NGC 1377, probed by ALMA band 9 CO 6-5 and 690 GHz dust continuum?  
  > "We obtained ALMA band 9 observations to probe the structure and orientation of the intervening dust in the nucleus of NGC 1377 and to determine gas and dust column densities." (Introduction)
- Target **NGC 1377**: coordinates 03:36:39.074 -20:54:07.055 (J2000, phase centre)  
  > "NGC 1377 is a nearby (21 Mpc (1$''$=102 pc)), lenticular galaxy" (Introduction); "The phase centre was set to $\alpha$=03:36:39.074 and $\delta$=$-$20:54:07.055 (J2000)." (2 Observations); z/distance 21 Mpc (1''=102 pc)  
  > "NGC 1377 is a nearby (21 Mpc (1$''$=102 pc)), lenticular galaxy" (Introduction); "The phase centre was set to $\alpha$=03:36:39.074 and $\delta$=$-$20:54:07.055 (J2000)." (2 Observations); distance from _not stated_

## Data provenance

- ALMA projects: 2012.1.00900.S
- bands: Band 9 (690 GHz)  
  > "Atacama Large Millimeter/submillimeter Array (ALMA) band 9 (690 GHz) observations" (Introduction)
- frequencies and spectral setup: two 1.875 GHz spectral windows (~690 GHz for CO 6-5 in LSB; 709 GHz for HCN 8-7) plus two 2 GHz continuum bands  
  > "The correlator was set up to cover two spectral windows of 1.875 GHz in spectral mode, one centred at a frequency of $\sim$690 GHz" (2 Observations)
- continuum bandwidth: _not stated_
- arrays: 35 antennas  
  > "with 35 antennas in the array" (2 Observations)
- configurations: _not stated_
- baselines: B_max=2250 m, B_min=41 m  
  > "B$_{\rm max}$=2250 m, B$_{\rm min}$= 41 m" (2 Observations)
- angular resolution: 0.06'' x 0.05'' (6x5 pc), Briggs  
  > "The synthesized beam is $0.\mbox{$''$}06 \times 0.\mbox{$''$}05$ (6$\times$5 pc)" (2 Observations)
- max recoverable scale: 2.2'' theoretical; effectively <1''  
  > "effectively we could not recover structures larger than 1$''$." (2 Observations)
- sensitivity: rms 10 mJy per 20 km/s channel (theoretical 9 mJy)  
  > "Our data set is close to this with an rms of 10 mJy." (2 Observations)
- time on source: 4 min on-source (250 s); 30 min total  
  > "for 4 minutes on-source (30 minutes in total)" (2 Observations)
- observing dates: 2015 September 25  
  > "on 2015 September 25" (2 Observations)
- pi or archival as stated: _not stated_
- Line: CO J=6-5 (not stated)
- Line: HCN 8-7 (not stated)
- Other facility **ALMA band 7 (345 GHz) earlier data**: CO 3-2 and 345 GHz continuum for excitation and column limits  
  > "We convolved our CO 6–5 map to the same resolution (25 pc) as that of the CO 3–2 ALMA data of (cite: aalto15b)." (4.1 Gas excitation)
- External data: Herschel 690 GHz flux of 200 mJy  
  > "find a 690 GHz flux of 200 mJy (cite: dale14)" (4.2 How obscured is NGC 1377?) [from (cite: dale14)]
- External data: Compact mid-IR source size <0.14'' and surface brightness  
  > "We fix the source size of the compact component to 0.$''$14 (14 pc)." (4.2.1 Foreground obscuration) [from (cite: imanishi11)]
- External data: SMBH mass ~1.5e6 Msun  
  > "We have previously estimated the mass of the buried SMBH to $\approx$ $1.5 \times 10^6$ M$_{\odot}$ (cite: aalto12b)." (4.3 Origin of the FIR luminosity) [from (cite: aalto12b)]

## Processing

### Calibration

- pipeline or manual: calibrated in CASA, then imported to AIPS for imaging  
  > "After calibration within the CASA reduction package (cite: mcm07), the visibility set was imported into the AIPS package for further imaging." (2 Observations)
- casa version: _not stated_
- pipeline version: _not stated_
- archive products used as is: _not stated_
- flux calibrator: J0334-401 (flux); J0522-3627 bandpass; J0348-2749 gain  
  > "The absolute flux scale was calibrated using the quasar $J0334-401$." (2 Observations)
- flux scale uncertainty: _not stated_
- self calibration: _not stated_

### Imaging

- task: imaging in AIPS  
  > "the visibility set was imported into the AIPS package for further imaging." (2 Observations)
- deconvolver: _not stated_
- weighting robust: Briggs, robust = 0.5  
  > "with Briggs weighting (parameter robust set to 0.5)" (2 Observations)
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
- final beam: 0.06'' x 0.05''  
  > "The synthesized beam is $0.\mbox{$''$}06 \times 0.\mbox{$''$}05$" (2 Observations)
- final rms: 10 mJy per 20 km/s channel  
  > "Our data set is close to this with an rms of 10 mJy." (2 Observations)

### Inherited from earlier work

- Molecular jet and CO 3-2 data context and precession model  
  > "The simple precessing jet model proposed in (cite: aalto16) predicts that velocities, after peaking at a distance $\pm$25 pc, decrease closer to the nucleus." (5 Nuclear dynamics) [from (cite: aalto16)]
- Column density from dust continuum via Keene prescription  
  > "following the prescription in (cite: keene82)" (4.1 Gas excitation) [from (cite: keene82)]

### Not stated but needed to reproduce (our reading)

- Channel width and velocity resolution of the final cube
- Image size and cell size
- Line-free channels used for continuum
- Dust opacity law/emissivity index used in the Keene conversion
- Details of the two-component SED fit and the IR data points used
- Whether self-calibration was applied
- CASA version

## Analysis recipe

1. **Image CO 6-5 and make moment maps**: Imaging in AIPS with Briggs weighting; moment 0 clipped at 3 sigma, flux-weighted moments 1 and 2  
  > "We clipped the moment 0 map at the 3$\sigma$ level." (3.1.1 Moment maps)
   - software: CASA, AIPS
   - parameter: robust = 0.5  
  > "parameter robust set to 0.5" (2 Observations)
   - fitting: _not stated_
   - validation: _not stated_
2. **Source size and high-velocity gas**: 2D Gaussian fit of moment 0; integrate high-velocity channels 1500-1670 and 1815-2000 km/s  
  > "With a two-dimensional Gaussian fitting we find a full width half maximum (FWHM) source size of 0.$''$096 $\times$ 0.$''$07" (3.1.1 Moment maps)
   - fitting: 2D Gaussian  
  > "With a two-dimensional Gaussian fitting we find a full width half maximum (FWHM) source size of 0.$''$096 $\times$ 0.$''$07 ($\pm 0.01$) (10 $\times$ 7 pc)." (Results, Moment maps, Moment 0 map)
   - validation: _not stated_
3. **Gas excitation and column density**: Convolve to 25 pc, compare CO 6-5/3-2 brightness ratio; RADEX non-LTE modeling  
  > "Using the RADEX (cite: vandertak07) non-LTE radiative transport model" (4.1 Gas excitation)
   - software: RADEX
   - parameter: dV=150 km/s  
  > "(for $\Delta V$=150 ${\rm km\,s}^{-1}$)" (4.1 Gas excitation)
   - assumption: CO abundance 1e-5 to 1e-4  
  > "For typical CO abundances of $10^{-5} - 10^{-4}$" (4.1 Gas excitation)
   - assumption: gas-to-dust ratio 100  
  > "for a gas-to-dust ratio of 100" (4.1 Gas excitation)
   - fitting: _not stated_
   - validation: _not stated_
4. **Dust column limits and SED model**: Continuum upper limit converted to tau and N(H+H2) via Keene prescription; two-component (compact+extended) SED fit; opaque-source size limit  
  > "We include a two-component fit to the data-points consisting of a *compact* and an *extended* source." (4.2.1 Foreground obscuration)
   - parameter: compact size 0.14'', Td 100 K; extended size 1.5''  
  > "we selected a size of 1.$''$5 (cite: aalto12b; aalto16) for the extended component" (4.2.1 Foreground obscuration)
   - fitting: _not stated_
   - validation: _not stated_
5. **Dynamical mass**: M_dyn = R V_rot^2/G for an edge-on disk from separation of high-velocity peaks; Keplerian PV tracks compared  
  > "A simple estimate of the dynamical mass is $M_{\rm dyn}$=RV$\mathstrut{^{2}_{{\rm rot}}}$/G" (Footnote 5)
   - assumption: edge-on disk  
  > "assuming an edge-on disk, the dynamical mass" (5.1 The high velocity gas)
   - fitting: _not stated_
   - validation: compared to M-sigma SMBH mass  
  > "This is close to the SMBH mass of $1.5 \times 10^6$ M$_{\odot}$ inferred from the $M$-$\sigma$ relation" (Nuclear dynamics, The high velocity gas)

## Software

- **CASA** : calibration  
  > "After calibration within the CASA reduction package (cite: mcm07)" (2 Observations)
- **AIPS** : imaging  
  > "imported into the AIPS package for further imaging" (2 Observations)
- **RADEX** : non-LTE CO excitation modeling  
  > "Using the RADEX (cite: vandertak07) non-LTE radiative transport model" (4.1 Gas excitation)

## Numeric results

| quantity | value | uncertainty | units | step | quote |
|---|---|---|---|---|---|
| CO 6-5 peak flux density | 90 | 17 | mJy/beam | 1 | The peak flux density is $90\pm 17$ mJy beam$^{-1}$ |
| CO 6-5 source size FWHM | 0.096 x 0.07 | 0.01 | arcsec | 2 | FWHM) source size of 0.$''$096 $\times$ 0.$''$07 ($\pm 0.01$) (10 $\times$ 7 pc) |
| 690 GHz continuum upper limit | 2 | 1 sigma | mJy | 4 | we do not detect any 690 GHz continuum with an upper limit of 2 mJy (1$\sigma$) |
| CO 6-5/3-2 ratio at 25 pc | 1.2 | not stated | dimensionless | 3 | resulting in a CO 6–5/3–2 intensity ratio of ${\cal R}$ of 1.2 |
| Dynamical mass inside 2.5 pc | 3e6 | not stated | Msun | 5 | $M_{\rm dyn}=3 \times 10^6$ M$_{\odot}$ inside $r$=2.5 pc |
| N(H+H2) upper limit in 5 pc beam | 2.4e23 | not stated | cm^-2 | 4 | $N$(H+H$_2$) is ${_<\atop{^\sim}}2.4 \times 10^{23}$ $\rm {cm^{-2}}$ in the 5 pc ALMA beam |

## Qualitative findings

- Compact CO 6-5 is aligned with the jet; nuclear column is not Compton thick at 5 pc but a subparsec CT core is possible  
  > "CT obscuration may instead occur in a much smaller, subparsec, structure undetected by ALMA." (Conclusions)

## Claim tuples

- H: Is the nucleus hidden by a compact opaque Compton-thick dust structure? | E: 690 GHz continuum at 5 pc resolution | R: no detection, <2 mJy, N(H2)<3e23 cm^-2 | F: Not CT at 5 pc; CT could be subparsec | **supported**
- H: Does high-velocity nuclear CO 6-5 trace a rotating disk? | E: high-velocity peaks separation and PV diagram | R: 145 km/s shift within 2-3 pc, Mdyn 3e6 Msun | F: Likely an inclined rotating disk/torus consistent with SMBH mass | **partially**

## Reasoning

- Why this data: Designed to detect a purported high-surface-brightness dusty nucleus  
  > "designed to detect a purported high-surface brightness dusty nucleus" (2 Observations)
- Why this method: _not stated_
- Alternative: Jet/outflow origin of the high-velocity gas considered but PA inconsistent  
  > "is also inconsistent with it being associated with gas along the jet" (5.1 The high velocity gas)
- How they decided it was enough: _not stated_
- Limitation (authors): Decorrelation implies Tb may be higher; short observation limits sensitivity  
  > "There are significant effects of decorrelation in our CO 6–5 data implying that the line intensity (and hence $T_{\rm B}$) may be higher." (Footnote 1)
- Caveat (inferred, ours): No uncertainties on SED fit or RADEX solutions
- Caveat (inferred, ours): Single short observation, few quantitative fits
- Caveat (inferred, ours): Dynamical mass from two peaks assumes edge-on

## Reproducibility

- Data public (paper): _not stated_
- Products in archive: _not stated_
- Missing: Imaging parameters beyond robust
- Missing: SED data and fit details
- Missing: Channel/mask definitions
- Data volume (inferred): ~10-50 GB
- Score (inferred): 3/5, Single dataset and basic recipe given, but many imaging and modelling details missing.
- Rediscovery candidate: no, Data public presumably, but recipe incomplete and key results rely on unstated modelling choices.

## Links

- Method: (cite: keene82) (dust column density prescription)
- Method: (cite: vandertak07) (RADEX)
- Companion: (cite: aalto16) (CO 3-2 molecular jet in NGC 1377)
- Companion: (cite: aalto12b) (earlier outflow discovery)

## Checks

```json
{
 "quotes": 58,
 "quotes_ok": 58,
 "quote_pass_rate": 1.0,
 "quotes_too_long": 0,
 "unsupported_facts": 0,
 "project_codes": 1,
 "codes_not_in_text": [],
 "codes_not_in_obscore": [],
 "obscore_codes_not_in_card": [],
 "codes_printed_but_missing": [],
 "numeric_results": 6,
 "numeric_problems": 0,
 "fill": {
  "facts": 76,
  "stated": 44,
  "rate": 0.579
 },
 "evidence_ok": true
}
```
