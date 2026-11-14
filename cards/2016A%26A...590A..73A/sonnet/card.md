# A precessing molecular jet signaling an obscured, growing supermassive black hole in NGC 1377?

`2016A&A...590A..73A` | Astronomy and Astrophysics 2016 | first author: Aalto, S. | arXiv: 1510.08827 | DOI: 10.1051/0004-6361/201527664

Card schema 1.0 | model claude-sonnet-5-5 | depth full | type observational_alma_primary

## Science

- Fields: nearby_galaxies, agn_and_quasars
- Question: What are the nature of the buried nuclear source in NGC 1377 and the structure and evolutionary status of its molecular outflow, as seen in high-resolution ALMA CO 3–2?  
  > "aiming to determine the nature of the buried source and the structure and evolutionary status of the outflow." (1.1 The extremely radio-quiet FIR-excess galaxy NGC 1377)
- Target **NGC 1377**: coordinates 03:36:39.074 -20:54:07.055 (J2000, phase centre)  
  > "NGC 1377 is a member of the Eridanus galaxy group at an estimated distance of 21 Mpc (1$''$=102 pc)" (1.1 The extremely radio-quiet FIR-excess galaxy NGC 1377); "The phase centre was set to $\alpha$=03:36:39.074 and $\delta$=$-$20:54:07.055 (J2000)." (2 Observations); z/distance 21 Mpc  
  > "NGC 1377 is a member of the Eridanus galaxy group at an estimated distance of 21 Mpc (1$''$=102 pc)" (1.1 The extremely radio-quiet FIR-excess galaxy NGC 1377); "The phase centre was set to $\alpha$=03:36:39.074 and $\delta$=$-$20:54:07.055 (J2000)." (2 Observations); distance from estimated Eridanus group distance (roussel03)  
  > "NGC 1377 is a member of the Eridanus galaxy group at an estimated distance of 21 Mpc (1$''$=102 pc)" (1.1 The extremely radio-quiet FIR-excess galaxy NGC 1377); "The phase centre was set to $\alpha$=03:36:39.074 and $\delta$=$-$20:54:07.055 (J2000)." (2 Observations)

## Data provenance

- ALMA projects: 2012.1.00900.S
- bands: CO 3-2 near 344 GHz (Band 7)  
  > "one centred at a frequency of $\sim$344.0 GHz to cover the CO J=3–2 line (in the lower side band)" (2 Observations)
- frequencies and spectral setup: Two 1.875 GHz spectral bands at ~344.0 and 354.3 GHz (1.0 km/s after Hanning smoothing); two 2 GHz continuum bands at 342.2 and 356 GHz  
  > "The correlator was set up to cover two bands of 1.875 GHz in spectral mode" (2 Observations); "two 2 GHz bands were set up in continuum mode" (2 Observations)
- continuum bandwidth: _not stated_
- arrays: 35 antennas  
  > "with 35 antennas in the array" (2 Observations)
- configurations: _not stated_
- baselines: _not stated_
- angular resolution: 0.25" x 0.18" (25x18 pc)  
  > "The synthesized beam is $0.\mbox{$''$}25 \times 0.\mbox{$''$}18$ (25$\times$18 pc for NGC1377)" (2 Observations)
- max recoverable scale: ~5"  
  > "The maximum recoverable scale of our observations is of the order of $\sim5$$''$." (3.3 Systemic and low-velocity gas)
- sensitivity: 0.8 mJy/beam per 10 km/s (12 MHz) channel  
  > "the resulting data has a sensitivity of 0.8 mJy per beam in a 10 ${\rm km\,s}^{-1}$ (12 MHz) channel width" (2 Observations)
- time on source: about half an hour  
  > "for about half an hour on-source and with good atmospheric conditions" (2 Observations)
- observing dates: 2014 August 12  
  > "on 2014 August 12" (2 Observations)
- pi or archival as stated: _not stated_
- Line: CO J=3-2 (not stated)
- Line: HCO+, HCN J=4-3 (HCN v=0 and v=1f) (not stated)
- Other facility **SMA**: Earlier CO 2-1 observations revealing a molecular outflow  
  > "High resolution SMA CO 2–1 observations revealed a large central concentration of molecular gas and a massive molecular outflow" (1.1 The extremely radio-quiet FIR-excess galaxy NGC 1377)
- External data: Distance 21 Mpc and L_FIR = 4.3e9 Lsun  
  > "has a far-infrared luminosity of $L_{\rm FIR}=4.3 \times 10^9$ L$_{\ensuremath{\odot}}$ (cite: roussel03)" (1.1 The extremely radio-quiet FIR-excess galaxy NGC 1377) [from (cite: roussel03)]
- External data: Upper limit on 1.4 GHz radio luminosity  
  > "We can use the limit to the 1.4 GHz radio luminosity (cite: roussel06)" (4.5.1 Accretion) [from (cite: roussel06)]

## Processing

### Calibration

- pipeline or manual: Calibrated within CASA, then imported into AIPS for imaging  
  > "After calibration within the CASA reduction package, the visibility set was imported into the AIPS package for further imaging." (2 Observations)
- casa version: _not stated_
- pipeline version: _not stated_
- archive products used as is: _not stated_
- flux calibrator: J0334-401, flux from ALMA flux-calibrator database  
  > "The absolute flux scale was calibrated using the quasar $J0334-401$." (2 Observations)
- flux scale uncertainty: _not stated_
- self calibration: _not stated_

### Imaging

- task: _not stated_
- deconvolver: _not stated_
- weighting robust: Briggs, robust = 0.5  
  > "with Briggs weighting (parameter robust set to 0.5)" (2 Observations)
- uv taper: _not stated_
- cell size: _not stated_
- image size: _not stated_
- masking: Moment 0 clipped at 3 sigma; moments 1 and 2 at 4 sigma, after smoothing to two-channel resolution  
  > "for the moment 0 map we clipped at the 3$\sigma$ level, and for the moment 1 and 2 maps we clipped at 4$\sigma$" (3.1 CO 3–2 moment maps)
- multiscale scales: _not stated_
- continuum subtraction: Continuum made by merging all line-free channels (0.8 mm)  
  > "We merged all line-free channels in our observations into a 0.8mm continuum image" (3.5 Continuum)
- line free channels: _not stated_
- primary beam correction: _not stated_
- array combination: _not stated_
- smoothing: Smoothed to two channel resolution for moment maps  
  > "We smoothed to two channel resolution" (3.1 CO 3–2 moment maps)
- final beam: 0.25" x 0.18"  
  > "The synthesized beam is $0.\mbox{$''$}25 \times 0.\mbox{$''$}18$" (2 Observations)
- final rms: 0.8 mJy/beam per 10 km/s channel; continuum rms 0.045 mJy  
  > "The rms is 0.045 mJy." (3.5 Continuum)

### Inherited from earlier work

- Precessing-jet line-of-sight velocity formalism  
  > "We use the formalism by (cite: wu09) to describe the line-of-sight velocity change along the symmetry axis of the jet" (Footnote 2) [from (cite: wu09)]
- Jet power vs 1.4 GHz luminosity relation  
  > "the relation between jet power and 1.4 GHz luminosity (cite: birzan08)" (4.5.1 Accretion) [from (cite: birzan08)]

### Not stated but needed to reproduce (our reading)

- Flux density of J0334-401 and the flux scale uncertainty
- CASA version and the calibration scripts
- AIPS version and imaging parameters (cell size, image size, clean masks, iterations)
- Line-free channels used for the continuum
- Exact PV cut positions and widths
- Jet inclination, v_out and precession-period derivation details, and the mass outflow rate calculation
- Distance and conversion-factor choices for the light-jet mass

## Analysis recipe

1. **Calibrate and image the CO 3-2 cube**: Calibration in CASA, then imaging in AIPS with Briggs weighting  
  > "After calibration within the CASA reduction package, the visibility set was imported into the AIPS package for further imaging." (2 Observations)
   - software: CASA, AIPS
   - parameter: robust = 0.5  
  > "parameter robust set to 0.5" (2 Observations)
   - fitting: _not stated_
   - validation: _not stated_
2. **Make moment maps and PV diagrams**: Flux-weighted first and second moments after smoothing and clipping; five PV diagrams along and across the jet  
  > "The velocity centroids were determined through a flux-weighted first moment of the spectrum of each pixel" (3.1 CO 3–2 moment maps)
   - parameter: clip 3 sigma (moment 0), 4 sigma (moments 1 and 2)  
  > "for the moment 0 map we clipped at the 3$\sigma$ level, and for the moment 1 and 2 maps we clipped at 4$\sigma$" (3.1 CO 3–2 moment maps)
   - fitting: _not stated_
   - validation: _not stated_
3. **Derive H2 masses**: CO flux converted to H2 mass with a standard conversion factor and a 1/4.5 correction from 3-2 to 1-0  
  > "Hence the correction factor we apply is 1/4.5 and $M$(H$_2$)=$2.2 \times 10^3 \, S({\rm CO}\, 3-2) \Delta \nu \, D^2$." (Table 1)
   - assumption: N(H2)/I(CO 1-0)=2.5e20 cm^-2; CO 3-2/1-0 brightness temperature ratio 0.5; D=21 Mpc  
  > "for a conversion factor $N$(H$_2$)/$I$(CO  1–0)=$2.5 \times 10^{20}$ $\rm {cm^{-2}}$)" (Table 1)
   - fitting: _not stated_
   - validation: _not stated_
4. **Model jet precession and derive jet parameters**: Simple analytic precessing-jet model compared with PV diagrams, giving precession angle, v_out, period and dynamical age; no formal fit  
  > "We require higher spatial resolution to carry out proper model fits to the jet properties." (4.1.1 Simple models)
   - parameter: theta=10-25 deg; v_proj 100-150 km/s  
  > "The east-offset implies a precession angle $\theta$=10$^{\circ}$-25$^{\circ}$" (4.1.2 Jet parameters)
   - assumption: Constant outflow velocity; precession axis in the plane of the sky  
  > "the inclination of the precession axis is zero (i.e. in the plane of the sky), and the outflow velocity $v_{\rm out}$ is constant" (4.1.1 Simple models)
   - fitting: _not stated_
   - validation: Rejected a bicone-projection alternative by comparing with PV shapes  
  > "Another important argument against the cone-projection model is the shape of the observed PV diagrams transverse to the jet symmetry axis" (Other potential explanations)

## Software

- **CASA** : Calibration  
  > "After calibration within the CASA reduction package" (2 Observations)
- **AIPS** : Imaging  
  > "the visibility set was imported into the AIPS package for further imaging" (2 Observations)

## Numeric results

| quantity | value | uncertainty | units | step | quote |
|---|---|---|---|---|---|
| Peak CO 3-2 flux density | 156 | 1 | mJy/beam | 1 | Peak flux density$^c$ / 156 $\pm$ 1 (mJy beam$^{-1}$) |
| Molecular jet CO 3-2 flux | 23.2 | 0.5 | Jy km/s | 2 | (molecular jet)$^d$ / $23.2 \pm 0.5$ (Jy ${\rm km\,s}^{-1}$) |
| Jet H2 mass | 2.3e7 | not stated | Msun | 3 | (molecular jet) / $2.3 \times 10^7$ M$_{\odot}$ |
| Continuum peak (0.8 mm) | 1.3 | 0.1 | mJy/beam | 1 | 1.3$\pm$0.1 mJy beam$^{-1}$ peak and 2.2$\pm$0.3 mJy integrated |
| Outflow velocity range | 240-850 | not stated | km/s | 4 | The outflow velocity should, therefore, lie in the range $v_{\rm out}$=240-850 ${\rm km\,s}^{-1}$ with a precession period $P$=0.3-1.1 Myr. |
| Jet mass outflow rate | 9-40 | not stated | Msun/yr | 4 | we estimate the mass outflow rate in the jet at 9 – 40 M$_{\odot}$ yr$^{-1}$ |
| Central-beam H2 column density | 3e24 | not stated | cm^-2 | 3 | The inferred H$_2$ column density in the central beam is $N$(H$_2$)=$3 \times 10^{24}$ $\rm {cm^{-2}}$. |

## Qualitative findings

- A collimated molecular jet (~±150 pc, unresolved width) with velocity reversals along its axis, consistent with precession  
  > "we have discovered a high velocity, collimated molecular jet with a projected length of $\pm$150 pc" (5 Conclusions)

## Claim tuples

- H: The high-velocity CO 3-2 gas is a precessing molecular jet | E: PV diagrams along and across the jet compared with a simple precession model and a bicone alternative | R: Velocity reversals of about ±150 km/s; narrow transverse PV shapes disfavour a cone | F: A precessing jet with v_out 240-850 km/s and P 0.3-1.1 Myr is favoured | **supported**
- H: The jet signals SMBH growth or quenching | E: Energetics for light and massive jet cases | R: Jet mass 2e6-2e7 Msun depending on the conversion factor | F: Cannot decide between growth and quenching | **partially**

## Reasoning

- Why this data: _not stated_
- Why this method: _not stated_
- Alternative: Orbiting SMBH, jet shocks and a projected bicone were considered and judged less likely than a precessing jet  
  > "this seems unlikely compared to the relatively simple scenario of one single precessing jet." (Other potential explanations)
- How they decided it was enough: _not stated_
- Limitation (authors): Resolution is insufficient for proper model fits; the jet mass is uncertain because of the CO-to-H2 conversion factor  
  > "We require higher spatial resolution to carry out proper model fits to the jet properties." (4.1.1 Simple models)
- Caveat (inferred, ours): The jet model is illustrative and has no formal fit or uncertainties
- Caveat (inferred, ours): The 3-2 to 1-0 conversion and the CO-to-H2 factor strongly affect the masses and rates
- Caveat (inferred, ours): Missing flux from extended emission
- Caveat (inferred, ours): No spectral-line energetics beyond CO

## Reproducibility

- Data public (paper): _not stated_
- Products in archive: _not stated_
- Missing: Imaging parameters in AIPS
- Missing: Calibration details
- Missing: PV cut definitions
- Data volume (inferred): ~10-30 GB raw for one short Band 7 execution
- Score (inferred): 3/5, Data are likely public and the main measurements are simple, but the imaging and the jet parameter derivation are only loosely specified.
- Rediscovery candidate: no, The jet modelling is qualitative and the imaging steps are insufficiently specified, although the data are likely public.

## Links

- Method: (cite: wu09) (Line-of-sight velocity formalism for a precessing jet)
- Companion: (cite: aalto12b) (Earlier SMA CO 2-1 study of the NGC 1377 outflow)

## Checks

```json
{
 "quotes": 57,
 "quotes_ok": 57,
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
  "facts": 70,
  "stated": 40,
  "rate": 0.571
 },
 "evidence_ok": true
}
```
