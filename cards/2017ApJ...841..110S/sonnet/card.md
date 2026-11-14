# The Coldest Place in the Universe: Probing the Ultra-cold Outflow and Dusty Disk in the Boomerang Nebula

`2017ApJ...841..110S` | The Astrophysical Journal 2017 | first author: Sahai, R. | arXiv: 1703.06929 | DOI: 10.3847/1538-4357/aa6d86

Card schema 1.0 | model claude-sonnet-5-5 | depth full | type observational_alma_primary

## Science

- Fields: evolved_stars
- Question: What are the structure, kinematics, mass-loss history and dust content of the ultra-cold outflow and dusty waist of the Boomerang Nebula, and what formation mechanism do they imply?  
  > "Here, we report the highest-angular molecular-line observations of this object with ALMA at 0.88 mm, new CO 1–0 data that recover all of the flux from the very extended ultra-cold outflow" (1 Introduction)
- Target **Boomerang Nebula**: coordinates RA 12h44m45.978s, Dec -54d31'13.043"  
  > "single pointing centered on R.A.$=12^h44^m45.978^s$ and $\delta=-54^\circ31'13.043{''}$" (2 Observations); "Although we have adopted a distance of D=1.5 kpc for the Boomerang (as inferred by SN97) for most of our analysis in this paper" (1 Introduction); z/distance D = 1.5 kpc  
  > "single pointing centered on R.A.$=12^h44^m45.978^s$ and $\delta=-54^\circ31'13.043{''}$" (2 Observations); "Although we have adopted a distance of D=1.5 kpc for the Boomerang (as inferred by SN97) for most of our analysis in this paper" (1 Introduction); distance from inferred by Sahai & Nyman 1997 (SN97)  
  > "single pointing centered on R.A.$=12^h44^m45.978^s$ and $\delta=-54^\circ31'13.043{''}$" (2 Observations); "Although we have adopted a distance of D=1.5 kpc for the Boomerang (as inferred by SN97) for most of our analysis in this paper" (1 Introduction)

## Data provenance

- ALMA projects: 2012.0.00510.S
- bands: Band 3 (CO 1-0, SO, continuum) and Band 7 (CO/13CO 3-2, continuum)  
  > "The continuum Band 3 and CO J=3–2 Band 7 observations were taken using a single pointing" (2 Observations)
- frequencies and spectral setup: _not stated_
- continuum bandwidth: _not stated_
- arrays: 12-m array, ACA, and Total Power antennas  
  > "consisted of a 7-point mosaic with the ALMA 12-m array and a 5-point mosaic using the Atacama Compact Array (ACA)" (2 Observations)
- configurations: _not stated_
- baselines: up to 1280 m  
  > "the observations are sensitive to emission on all scales, with baselines ranging up to 1280 m" (2 Observations)
- angular resolution: ~0.3-0.4" for CO 3-2 (Band 7); 4.1"x1.8" for CO 1-0 combined  
  > "were observed with the 12m array with an angular resolution of about 0.3$''$" (3.1.1 Spatio-Kinematic Structure of the Lobes)
- max recoverable scale: _not stated_
- sensitivity: _not stated_
- time on source: TP 160 min; see Table 1 for others  
  > "using three ALMA Total Power (TP) antennas, using a total of 160 min" (2 Observations)
- observing dates: 12-m 17 Dec 2013; ACA 20-21 Mar 2014; TP 25-26 Apr 2015; Band 7 14/15 Jun 2014  
  > "The 12-m array observations were completed on December 17 2013, the ACA observations on March 20-21 2014 and the TP observations on April 25-26 2015." (2 Observations)
- pi or archival as stated: _not stated_
- Line: 12CO J=1-0 (115.271 GHz)
- Line: 12CO J=3-2 (345.796 GHz)
- Line: 13CO J=3-2 (330.588 GHz)
- Line: SO N,J=2,3-1,2 (99.299 GHz)
- Other facility **APEX**: CO J=3-2 single-dish spectrum to assess flux loss  
  > "we obtained a spectrum of the line on October 8 2014 using the APEX telescope." (2 Observations)
- Other facility **HST ACS**: 0.6 micron polarized-light image for comparison  
  > "a 0.6 $\mu$m polarized-light image obtained using the ACS" (3.1.1 Spatio-Kinematic Structure of the Lobes)
- External data: HST ACS polarimetric image of the Boomerang  
  > "obtained using the ACS (Fig. [1](#boom-acs-co32)b, Cracraft & Sparks 2007)" (3.1.1 Spatio-Kinematic Structure of the Lobes) [from Cracraft & Sparks 2007]
- External data: Cycle 0 ALMA continuum fluxes and SED model  
  > "We revise the Setal13 model of the radio-to-(sub)millimeter-wave SED" (3.4 Continuum Imaging and Dust Mass in the Dense Waist) [from Sahai et al. 2013 (Setal13)]
- External data: Two-shell model with tau_1,0=5.2 at r=10"  
  > "as per the SN97 model, $\tau_{1,0}=5.2$ at $r=10{''}$" (3.2 Physical Properties of the Ultra-Cold Outflow) [from Sahai & Nyman 1997 (SN97)]

## Processing

### Calibration

- pipeline or manual: Observatory-provided scripts with a few extra flagging commands  
  > "calibrated using the Common Astronomy Software Application (CASA 4.2) and the observatory provided scripts with only a few additional flagging commands" (2 Observations)
- casa version: CASA 4.2  
  > "Common Astronomy Software Application (CASA 4.2)" (2 Observations)
- pipeline version: _not stated_
- archive products used as is: _not stated_
- flux calibrator: Callisto (12-m Band 3 line), Mars (ACA and 12-m Band 3 continuum), Titan (12-m Band 7)  
  > "Flux calibration was done using Callisto (12-m Band 3 spectral line observations), Mars (ACA and 12-m continuum Band 3 observations), and Titan (12-m Band 7 observations)." (2 Observations)
- flux scale uncertainty: _not stated_
- self calibration: _not stated_

### Imaging

- task: _not stated_
- deconvolver: _not stated_
- weighting robust: natural weighting (Band 3 12m+ACA)  
  > "imaged using natural weighting and a Gaussian taper radius of 100 $k\lambda$" (2 Observations)
- uv taper: Gaussian taper radius of 100 klambda  
  > "imaged using natural weighting and a Gaussian taper radius of 100 $k\lambda$" (2 Observations)
- cell size: _not stated_
- image size: _not stated_
- masking: _not stated_
- multiscale scales: _not stated_
- continuum subtraction: _not stated_
- line free channels: _not stated_
- primary beam correction: _not stated_
- array combination: 12m and ACA combined in visibility plane; TP combined with CASA feather  
  > "the TP image, also obtained using the provided script, was combined with the interferometric image using the CASA task *feather*" (2 Observations)
- smoothing: Continuum images convolved to 4.1"x2.9" PA=-33.9 for SED fluxes  
  > "The fluxes were extracted from images convolved to the same beam as used in the lower-resolution Cycle 0 data ($4.1\ensuremath{''}\,\times\,2.9\ensuremath{''}$ at $PA=-33.9$$^\circ$)" (3.4 Continuum Imaging and Dust Mass in the Dense Waist)
- final beam: _not stated_
- final rms: 0.06 mJy/beam at 0.88 mm; 0.015-0.02 mJy/beam at 3.3 mm  
  > "the noise in the image is about 0.06 mJy/beam" (3.4 Continuum Imaging and Dust Mass in the Dense Waist)

### Inherited from earlier work

- Reasoning to constrain dust temperature from continuum source size  
  > "We follow Setal13’s reasoning to constrain $T_d$" (3.4 Continuum Imaging and Dust Mass in the Dense Waist) [from Sahai et al. 2013 (Setal13)]
- Distance 1.5 kpc and warm/ultra-cold shell model  
  > "Although we have adopted a distance of D=1.5 kpc for the Boomerang (as inferred by SN97)" (1 Introduction) [from Sahai & Nyman 1997 (SN97)]
- Optical depth formulation  
  > "Using the formulation of Morris (1975), we derive the radiative-contact length" (Appendix) [from Morris (1975)]

### Not stated but needed to reproduce (our reading)

- Imaging parameters for Band 7 (weighting, robust, cell size, clean threshold, masks)
- Continuum channel selection and line-free channels
- Self-calibration use
- Absolute flux scale uncertainty
- Details of how HST image was reprojected
- Dust opacity normalization and gas-to-dust assumptions used for the dust mass
- Aperture and method for annulus spectra

## Analysis recipe

1. **Calibrate and image data**: Observatory scripts in CASA; combine 12m+ACA, feather with TP  
  > "The Band 3 data of the 12-m and ACA observations were combined in the visibility plane" (2 Observations)
   - software: CASA, feather
   - fitting: _not stated_
   - validation: APEX CO 3-2 spectrum used to estimate flux resolved out by ALMA (~4 Jy of 8.2 Jy)  
  > "The ALMA observations thus resolve out about 4 Jy of extended emission." (3.1.1 Spatio-Kinematic Structure of the Lobes)
2. **Derive expansion timescales and waist properties**: Divide linear extent by deprojected velocity; deconvolved size over FWHM velocity for waist; RADEX for excitation  
  > "we roughly estimate an expansion age of 1925 yr, by dividing the half-power extent (deconvolved) of the $^{13}$CO J=3–2 waist emission" (3.1.2 Spatio-Kinematic Structure of the Waist)
   - software: RADEX
   - assumption: Outer waist expanding; lobe inclination 75-90 deg  
  > "where $90\ensuremath{^\circ}>\theta\ge75\ensuremath{^\circ}$ is the lobe’s inclination" (3.1.1 Spatio-Kinematic Structure of the Lobes)
   - fitting: _not stated_
   - validation: _not stated_
3. **Constrain mass-loss rate and mass of ultra-cold outflow**: Analytic tau_1,0 with Mdot proportional to V^a and V linear in r; require tau>=1 at 80" and 10"  
  > "We can therefore analytically express $\tau_{1,0}$ as a function of a radially-variable mass-loss rate" (3.2 Physical Properties of the Ultra-Cold Outflow)
   - parameter: V0=164 km/s, R0=80", r_in=6", f_CO=1.3e-3  
  > "We set $V_0=164$ km s$^{-1}$ and $R_0=80{''}$." (3.2 Physical Properties of the Ultra-Cold Outflow)
   - assumption: Main-sequence mass <=8 Msun; central star ~0.61 Msun; D=1.5 kpc  
  > "which implies that its main-sequence mass is, $M_{ms}\lesssim8$ $M_{\odot}$" (3.2 Physical Properties of the Ultra-Cold Outflow)
   - fitting: _not stated_
   - validation: _not stated_
4. **Model the mm-submm SED for dust temperature, beta and mass**: Fluxes in 6"x4" aperture from beam-matched images; power-law emissivity; dust radius-temperature relation for central heating  
  > "using an aperture of size $6{''}\times4{''}$ that encompasses most of the emission" (3.4 Continuum Imaging and Dust Mass in the Dense Waist)
   - parameter: Deconvolved half-power size ~2.3" at 3.3 mm (radius ~2.6e16 cm)  
  > "giving a characteristic radius of $\sim2.6\times10^{16}$ cm for the dust source" (3.4 Continuum Imaging and Dust Mass in the Dense Waist)
   - assumption: Optically thin dust; 10% of stellar flux reddened to 900 K for disk case  
  > "we conservatively assume that only 10% of the total stellar flux, reddened to 900 K is available for heating" (3.4 Continuum Imaging and Dust Mass in the Dense Waist)
   - fitting: _not stated_
   - validation: Alternatives (spinning dust, Fe nanoparticles) tested and rejected  
  > "We now discuss and discard two alternative mechanisms for explaining the shallow mm-submm spectral index" (3.4 Continuum Imaging and Dust Mass in the Dense Waist)
5. **Energetics of common-envelope ejection**: Compare orbital energy released with kinetic energy of ultra-cold outflow to bound final separation  
  > "from which we can derive an upper limit on the separation of the final binary." (4 Ejection Time-Scales and Binary Interaction Models)
   - parameter: M1=4, M1c=0.6, M2=1 Msun, eta~1  
  > "Taking $M_1=4$ $M_{\odot}$, and typical values for $M_{1,c}=0.6$ $M_{\odot}$, $M_2=1$ $M_{\odot}$" (4 Ejection Time-Scales and Binary Interaction Models)
   - fitting: _not stated_
   - validation: _not stated_

## Software

- **CASA** 4.2: Calibration and imaging, feather combination  
  > "Common Astronomy Software Application (CASA 4.2)" (2 Observations)
- **RADEX** : Excitation modelling of waist CO emission  
  > "Simple modeling using RADEX (Van der Tak et al. 2007)" (3.1.2 Spatio-Kinematic Structure of the Waist)

## Numeric results

| quantity | value | uncertainty | units | step | quote |
|---|---|---|---|---|---|
| Mass-loss rate lower limit at r=80" (a=0) | >=2.1e-3 | not stated | Msun/yr | 3 | we find that $\mbox{$\dot{M}$}_0\ge2.1\times10^{-3}$ $M_{\odot}$ yr$^{-1}$ |
| Mass in ultra-cold outflow | >=3.3 | not stated | Msun | 3 | $M_{cold}\gtrsim3.3$ $M_{\odot}$, and $M_{ms}\gtrsim4$ $M_{\odot}$ |
| Exponent a (Mdot proportional to V^a) | 0.9-2.2 | not stated | dimensionless | 3 | we find that $a\gtrsim\,0.9$ |
| Dust mass in waist | (4-7)e-4 | not stated | Msun | 4 | with a dust mass $(4-7)\times10^{-4}$ $M_{\odot}$ |
| Dust temperature | 19-32 | not stated | K | 4 | has $T_d\sim19-32$ K, $\beta=0.1-0.2$ |
| 0.88 mm peak intensity | 2.7 | 0.1 | mJy/beam | 4 | The peak intensity is $2.7\pm0.1$ mJy/beam |
| Waist expansion age | ~1925 | not stated | yr | 2 | we roughly estimate an expansion age of 1925 yr |
| S-lobe expansion age upper limit | 1050 | not stated | yr | 2 | We derive an upper limit of 1050 yr to the expansion time-scale of the S-lobe |
| Kinetic energy of ultra-cold outflow | >4.8e47 | not stated | erg | 5 | $KE_{cold}>4.8\times10^{47}$ erg |
| Final binary separation 2a_f | <4.7 | not stated | Rsun | 5 | we find that $2\,a_f<4.7$ $R_{\odot}$ |

## Qualitative findings

- CO 3-2 molecular gas matches HST scattered-light structure; N-lobe complex, S-lobe simple  
  > "reveals a detailed correspondence between the molecular gas and the dust as seen in scattered light via optical HST imaging." (Conclusions)
- SO detected, suggesting an O-rich nebula  
  > "We find the presence of SO in the central region of the Boomerang." (Conclusions)

## Claim tuples

- H: Is the ultra-cold outflow mass-loss rate uniform? | E: Analytic CO 1-0 optical depth with constraints from ALMA 12m+ACA+TP map out to 80" | R: Uniform rate gives implausibly large mass; a=0.9-2.2 gives >=3.3 Msun | F: Mass-loss rate increases with radius; progenitor >=4 Msun | **supported**
- H: Does the waist harbor very large cold grains? | E: SED across 0.87-3.3 mm and dust radius-temperature argument | R: beta ~0.1-0.2, Td ~19-32 K, mass (4-7)e-4 Msun | F: mm-to-cm grains present; spinning dust and Fe nanoparticles disfavored | **supported**
- H: What formation mechanism produced the Boomerang? | E: Compare expansion ages and energetics with binary interaction models | R: Long jet-lag; CEE energy exceeds outflow kinetic energy; 2a_f smaller than stellar radius | F: Common-envelope event with companion merger | **partially**

## Reasoning

- Why this data: Higher resolution CO 3-2 and CO 1-0 with ACA and TP to recover flux from extended outflow  
  > "new CO 1–0 data that recover all of the flux from the very extended ultra-cold outflow" (1 Introduction)
- Why this method: _not stated_
- Alternative: Spinning dust grains and Fe nanoparticles rejected as explanations for shallow spectral index  
  > "We conclude that spinning dust grains cannot explain the shallow spectral index of the mm-submm SED in the Boomerang." (3.4 Continuum Imaging and Dust Mass in the Dense Waist)
- How they decided it was enough: _not stated_
- Limitation (authors): Envelope size only a lower limit because CO is in absorption  
  > "We can only determine a lower-limit from the data because of the rather pathological conditions in this object" (3.1.3 CO (J=1–0) Imaging)
- Caveat (inferred, ours): Mass and mass-loss rate are limits from analytic assumptions (linear velocity law, tau>=1) and depend on distance
- Caveat (inferred, ours): Waist age assumes expansion while possible Keplerian rotation is noted
- Caveat (inferred, ours): Dust mass depends on unstated opacity assumptions
- Caveat (inferred, ours): Polarization explanation is speculative

## Reproducibility

- Data public (paper): ALMA data cited by project code in acknowledgments  
  > "This paper makes use of the following ALMA data: ADS/JAO.ALMA#2012.0.00510.S." (Acknowledgments)
- Products in archive: _not stated_
- Missing: Band 7 imaging parameters
- Missing: Dust opacity law and normalization
- Missing: Spectral extraction regions details
- Missing: HST data processed version
- Data volume (inferred): ~100-300 GB raw across 12m, ACA, TP Bands 3 and 7
- Score (inferred): 3/5, Public data and scripted calibration, but imaging details and some analysis choices are missing; results are analytic limits.
- Rediscovery candidate: no, Imaging recipe for Band 7 incomplete and several results depend on unstated assumptions.

## Links

- Method: Morris (1975) (Radiative-contact formulation for optical depth)
- Method: Van der Tak et al. 2007 (RADEX excitation modelling)
- Companion: Sahai et al. 2013 (Setal13) (Cycle 0 ALMA observations of the Boomerang)
- Companion: Sahai & Nyman 1997 (SN97) (Discovery of ultra-cold outflow and two-shell model)

## Checks

```json
{
 "quotes": 69,
 "quotes_ok": 69,
 "quote_pass_rate": 1.0,
 "quotes_too_long": 0,
 "unsupported_facts": 0,
 "project_codes": 1,
 "codes_not_in_text": [],
 "codes_not_in_obscore": [
  "2012.0.00510.S"
 ],
 "obscore_codes_not_in_card": [
  "2011.0.00510.S"
 ],
 "codes_printed_but_missing": [],
 "numeric_results": 10,
 "numeric_problems": 0,
 "fill": {
  "facts": 78,
  "stated": 47,
  "rate": 0.603
 },
 "evidence_ok": true
}
```
