# ALMA finds dew drops in the dusty spider's web

`2016A&A...591A..73G` | Astronomy and Astrophysics 2016 | first author: Gullberg, Bitten | arXiv: 1602.04823 | DOI: 10.1051/0004-6361/201527647

Card schema 1.0 | model claude-sonnet-5-5 | depth full | type observational_alma_primary

## Science

- Fields: high_z_galaxies, agn_and_quasars
- Question: What are the dust, atomic carbon, CO(7-6) and H2O properties of the Spiderweb radio galaxy and its surroundings, and what do they say about shocks, molecular gas and star formation?  
  > "Motivated to determine the energy source and distribution of the strong dissipation as possibly observed through H$_2$ emission and determining the state of the molecular gas in MRC1138-262" (1 Introduction)
- Target **MRC1138-262 (Spiderweb Galaxy)**: coordinates 11:40:48.34 -26:29:08.656 (HzRG, Table)  
  > "The high-$z$ radio galaxy (H$z$RG) MRC1138-262 at $z=2.161$ is one of the best studied H$z$RG" (1 Introduction); "We assume H$_0=73$ km/s/Mpc, $\Omega_M=0.27$, and $\Omega_{\Lambda}=0.73$, which implies a scale of 8.172 kpc/$''$ at $z=2.161$." (1 Introduction); z/distance z=2.1606  
  > "The high-$z$ radio galaxy (H$z$RG) MRC1138-262 at $z=2.161$ is one of the best studied H$z$RG" (1 Introduction); "We assume H$_0=73$ km/s/Mpc, $\Omega_M=0.27$, and $\Omega_{\Lambda}=0.73$, which implies a scale of 8.172 kpc/$''$ at $z=2.161$." (1 Introduction); distance from [CI]2-1 line at radio core, consistent with CO(1-0)  
  > "The high-$z$ radio galaxy (H$z$RG) MRC1138-262 at $z=2.161$ is one of the best studied H$z$RG" (1 Introduction); "We assume H$_0=73$ km/s/Mpc, $\Omega_M=0.27$, and $\Omega_{\Lambda}=0.73$, which implies a scale of 8.172 kpc/$''$ at $z=2.161$." (1 Introduction)

## Data provenance

- ALMA projects: 2012.1.01087.S
- bands: Band 6 (Cycle 1)  
  > "The ALMA cycle 1 Band 6 observations were carried out on 2014 April 27 for 49 min on-source time with 36 working antennas." (2.1 ALMA observations)
- frequencies and spectral setup: four 1.875 GHz spws covering 237.3-240.9 and 252.6-256.7 GHz  
  > "The four 1.875 GHz spectral windows were tuned to cover the frequency ranges $237.3-240.9$ GHz and $252.6-256.7$ GHz." (2.1 ALMA observations)
- continuum bandwidth: _not stated_
- arrays: _not stated_
- configurations: _not stated_
- baselines: UV range well covered within 400 kλ  
  > "the UV range was well covered within 400 k$\lambda$." (2.1 ALMA observations)
- angular resolution: continuum beam 0.69'' x 0.44'', PA 89.3 deg  
  > "This results in a continuum map with a synthesised beam of $0.69\ensuremath{''} \times
0.44\ensuremath{''}$ with PA $89.3^{\circ}$ and an RMS of 50 $\mu$Jy." (2.1 ALMA observations)
- max recoverable scale: _not stated_
- sensitivity: _not stated_
- time on source: 49 min  
  > "The ALMA cycle 1 Band 6 observations were carried out on 2014 April 27 for 49 min on-source time with 36 working antennas." (2.1 ALMA observations)
- observing dates: 2014 April 27  
  > "The ALMA cycle 1 Band 6 observations were carried out on 2014 April 27 for 49 min on-source time with 36 working antennas." (2.1 ALMA observations)
- pi or archival as stated: _not stated_
- Line: H2O 2_11-2_02 (752.03 GHz)
- Line: [CI] 3P2-3P1 (2-1) (809.34 GHz)
- Line: CO 7-6 (806.65 GHz)
- External data: CO(1-0) H2 mass ~6e10 Msun and L'CO(1-0)=6.5e10 K km/s pc^2  
  > "$L^{\prime}_{\rm CO(1-0)}=6.5\times 10^{10}$ K km/s pc$^2$ (cite: emonts13)" (4.1.3 Possible causes) [from (cite: emonts13)]
- External data: Comparison sample of lensed galaxies with CO(7-6), [CI], H2O fluxes and magnifications  
  > "find nine lensed sub-millimetre galaxies (SMG) and QSOs" (4.1.2 Line ratios) [from (cite: lupu12; danielson11; weiss03; omont13; vanderwerf11; riechers13)]
- External data: 850 micron dust mass absorption coefficient 0.076 m^2/kg  
  > "850 $\mu$m absorption coefficient of 0.076 m$^2$ kg$^{-1}$ from (cite: stevens03)" (4.3 Mass Estimates) [from (cite: stevens03)]
- External data: Radio fluxes 8.2 GHz 1.88 mJy (core), 5.9 mJy (companion #10); 36.5 GHz from Emonts in prep  
  > "$S(8.2\,\text{GHz)} = 1.88$ mJy (cite: pentericci97)" (3.1.1) [from (cite: pentericci97); Emonts et al. in prep]

## Processing

### Calibration

- pipeline or manual: supplied CASA calibration script used  
  > "We used the supplied Common Astronomy Software Applications (CASA) calibration script to produce the data cube, continuum map and moment-0 maps." (2.1 ALMA observations)
- casa version: _not stated_
- pipeline version: _not stated_
- archive products used as is: _not stated_
- flux calibrator: _not stated_
- flux scale uncertainty: _not stated_
- self calibration: _not stated_

### Imaging

- task: _not stated_
- deconvolver: _not stated_
- weighting robust: natural weighting (Briggs robust = 2)  
  > "We made a natural weighted map (Briggs robust parameter of 2), which exhibits the highest S/N" (2.1 ALMA observations)
- uv taper: _not stated_
- cell size: _not stated_
- image size: _not stated_
- masking: _not stated_
- multiscale scales: _not stated_
- continuum subtraction: UV-plane first-order polynomial for [CI]/CO(7-6) using spw 1; none for H2O  
  > "we subtract the continuum in the UV-plane by fitting a first order polynomial to the line free channels." (2.1 ALMA observations); "The H$_2$O observations are therefore not continuum subtracted." (2.1 ALMA observations)
- line free channels: _not stated_
- primary beam correction: continuum and H2O data corrected; PB 26.3''  
  > "We corrected the continuum map for the primary beam of 26.3$''$." (2.1 ALMA observations)
- array combination: _not stated_
- smoothing: [CI] binned to 20 km/s (RMS 0.5 mJy); H2O to 60 km/s (RMS 0.3 mJy)  
  > "We bin the \[CI\]2–1 line data to 20 km/s which has an RMS of 0.5 mJy and the H$_2$O line data to 60 km/s which has an RMS of 0.3 mJy." (2.1 ALMA observations)
- final beam: _not stated_
- final rms: continuum 50 uJy  
  > "This results in a continuum map with a synthesised beam of $0.69\ensuremath{''} \times
0.44\ensuremath{''}$ with PA $89.3^{\circ}$ and an RMS of 50 $\mu$Jy." (2.1 ALMA observations)

### Inherited from earlier work

- [CI]-based H2 mass formalism  
  > "following the approach of (cite: papadopoulos04) and (cite: alaghband-zadeh13):" (4.3 Mass Estimates) [from (cite: papadopoulos04); (cite: alaghband-zadeh13)]
- Dust mass and FIR luminosity equations  
  > "Following the approach of (cite: debreuck03), using," (4.3 Mass Estimates) [from (cite: debreuck03)]

### Not stated but needed to reproduce (our reading)

- Line-free channel ranges for continuum subtraction
- Imaging task, cell and image size, masking and deconvolution settings
- CASA version
- Flux calibrator and phase calibrator identities and flux scale uncertainty
- How line profiles were fit (fitter, errors) and how the SFR conversion handles the IMF
- Luminosity distance and IR luminosities adopted for the comparison sample

## Analysis recipe

1. **Image continuum and line cubes**: Natural-weighted continuum map excluding 254.9-265.7 GHz; line cubes binned, UV-plane continuum subtraction (except H2O)  
  > "The frequency range between $254.9-265.7$ GHz (i.e. half of the upper side band) is dominated by strong \[CI\]2–1 and CO(7–6) line emission and is therefore not included in the continuum map." (2.1 ALMA observations)
   - software: CASA
   - fitting: _not stated_
   - validation: Jackknife test splitting time in half for H2O  
  > "To establish that this emission is real we perform a ’Jackknife’ test, cutting the observed time in half." (3.3 H2O line emission)
2. **Measure continuum flux densities**: Double 2D Gaussian fit with centres fixed at [CI] component peaks; single Gaussian for companion #10  
  > "we fit a double 2D Gaussian profile to the continuum by fixing the centres of the Gaussians at the peak positions of the \[CI\]2–1 emission line." (3.1.1)
   - fitting: _not stated_
   - validation: Compared LSB/USB flux ratio with 40 K blackbody expectation and radio extrapolation to assess synchrotron  
  > "The expected ratio between 238.28 and 253.48 GHz (i.e. the lower and upper side bands: LSB and USB) from thermal blackbody radiation at 40 K is 0.80, while the observed ratio is $1.19\pm0.22$." (3.1.2)
3. **Fit line profiles and integrate fluxes**: Lorentzian for [CI] comp 1, Gaussians for CO(7-6) and comp 2; fluxes integrated over stated velocity ranges avoiding line blending  
  > "has a Lorentzian-shaped profile, with a full-width at half-maxima (FWHM) of $270\pm15$ km/s" (3.2.1)
   - fitting: _not stated_
   - validation: _not stated_
4. **Compare CO(7-6)/[CI] ratio and H2O/IR with lensed literature sample**: Normalise line luminosities by IR luminosity, plot against literature sources  
  > "we normalise the \[CI\]2–1 and CO(7–6) line luminosities by the IR luminosity" (4.1.2)
   - assumption: no differential lensing between IR and line emission  
  > "(assuming there is no differential lensing between the IR and line emission)" (4.1.2)
   - fitting: _not stated_
   - validation: _not stated_
5. **Derive H2 gas mass from [CI]2-1**: Papadopoulos et al. 2004 formula  
  > "We therefore use the \[CI\]2–1 to estimate the total molecular gas mass" (4.3 Mass Estimates)
   - assumption: X[CI]=3e-5, Q21=0.57, A21=2.68e-7 s^-1  
  > "$Q_{21}$ is the density dependent excitation factor for which we assume the median value of 0.57" (4.3 Mass Estimates)
   - fitting: _not stated_
   - validation: Compared with CO(1-0) mass; varied Q21 from 0.15 to 1.0  
  > "The median value is close to $M(\text{H$_2$})=6\times 10^{10}$ M$_{\odot}$ derived from CO(1-0)" (4.3 Mass Estimates)
6. **Derive dust mass, FIR luminosity and SFR**: Single greybody dust mass and L_FIR following De Breuck 2003, SFR = L_FIR/1e10  
  > "we fix the shape of the SED by assuming a greybody characterised by $\beta=1.5$ and $T_d=40$ K." (4.3 Mass Estimates)
   - assumption: beta=1.5, Td=40 K, delta_MF=1, delta_SB=1  
  > "We assume $\delta_{\text{MF}}=1$ and derive the SFRs" (4.4 Star-formation rate)
   - fitting: _not stated_
   - validation: Compared to Seymour+12 and Drouart+14 IR luminosities  
  > "total starburst-heated IR luminosity of $5.6\times 10^{12}$L$_{\rm \odot}$ of (cite: drouart14)" (4.4 Star-formation rate)

## Software

- **CASA** : supplied calibration script, data cube, continuum and moment-0 maps  
  > "We used the supplied Common Astronomy Software Applications (CASA) calibration script to produce the data cube, continuum map and moment-0 maps." (2.1 ALMA observations)

## Numeric results

| quantity | value | uncertainty | units | step | quote |
|---|---|---|---|---|---|
| 246 GHz continuum flux density of HzRG | 1.78 | 0.29 | mJy | 2 | yields the flux density of $1.78\pm0.29$ mJy |
| Companion #10 continuum flux density | 0.19 | 0.01 | mJy | 2 | we find a flux density of $0.19\pm0.01$ mJy |
| [CI]2-1 line flux, components 1+2 | 1.30 | 0.03 | Jy km/s | 3 | / 2–1        / 809.34    / 11:40:48.33 / -26:29:8.582  / $1.30\pm0.03$   / $420\pm30$  / $280\pm40$ / |
| [CI]2-1 FWHM component 1 | 270 | 15 | km/s | 3 | FWHM) of $270\pm15$ km/s and a redshift of $z=2.1606\pm0.0041$ |
| Total H2 mass from [CI]2-1 | 3.3e10 | not stated | Msun | 5 | We find a total H$_2$ molecular gas mass for both components of $3.3\times10^{10}$ M$_{\odot}$. |
| HzRG dust mass | 6.1e8 | not stated | Msun | 6 | we derive a dust mass of $M_d=6.1\times10^{8}$ M$_{\odot}$ for the H$z$RG |
| HzRG SFR upper limit | <440 | not stated | Msun/yr | 6 | derive the SFRs of $<440$ M$_{\odot}$ yr$^{-1}$ for the H$z$RG |
| H2O line flux West | 0.05 | 0.01 | Jy km/s | 3 | / H$_2$O     / 752.03    / 11:40:48.82 / -26:29:9.580  / $0.05\pm0.01$   / $230\pm50$  / —          / |
| H2O line flux East | 0.1 | 0.02 | Jy km/s | 3 | / H$_2$O     / 752.03    / 11:40:48.11 / -26:29:9.970  / $0.1\pm0.02$   / $350\pm70$  / —          / |
| CO(7-6) flux companion #10 | 0.08 | 0.01 | Jy km/s | 3 | integrated line flux from -170 km/s to 150 km/s of 0.08$\pm$0.01 Jy km/s |
| Upper limit on size of component 2 broad region | <60 | not stated | pc | 5 | we find that $R<60$ pc. |

## Qualitative findings

- H2O is detected near the radio jet bend and east lobe without associated continuum, consistent with slow-shock heating rather than IR pumping.  
  > "are consistent with heating by slow shocks in dense molecular gas." (5 Conclusions)

## Claim tuples

- H: Is the H2O emission powered by IR pumping or by jet-driven shocks? | E: Detect H2O at 2 positions near jet, compare with continuum and the L_H2O/L_IR trend | R: ~4 sigma H2O at two positions with no 246 GHz continuum (<40 uJy rms) | F: H2O is shock-heated post-shock gas from the radio jet | **supported**
- H: Is the CO(7-6)/[CI]2-1 ratio unusual compared with lensed sources? | E: Compare normalised line luminosities with nine lensed literature sources | R: Spiderweb lies low on the correlation | F: Low ratio from low excitation gas, cosmic rays, or differential lensing in comparison sample | **partially**
- H: Does [CI] reveal substructure in the HzRG? | E: Moment maps and line profile fitting | R: Two components 0.5'' apart with Lorentzian and double Gaussian profiles | F: Component 2 broad region <60 pc suggests possible additional radio-quiet AGN | **partially**

## Reasoning

- Why this data: _not stated_
- Why this method: _not stated_
- Alternative: Entrainment of dense gas by the jet judged unlikely given near-systemic velocities and short cooling time.  
  > "it is unlikely that the dense molecular gas has been entrained during the passage of the radio jet" (4.2)
- How they decided it was enough: _not stated_
- Limitation (authors): Continuum from HzRG and companion #10 contaminated by synchrotron, so SFRs are upper limits; single greybody is crude.  
  > "We warn that our approximation of the SED with a single grey body function with an assumed emissivity index is rather crude" (4.4 Star-formation rate)
- Caveat (inferred, ours): H2O detections are only ~4 sigma and rest on a half-time jackknife
- Caveat (inferred, ours): Single-band continuum with assumed Td and beta
- Caveat (inferred, ours): Blending of [CI] and CO(7-6) makes fluxes model dependent
- Caveat (inferred, ours): Companion #10 identification relies on one line

## Reproducibility

- Data public (paper): _not stated_
- Products in archive: Data from ALMA project 2012.1.01087.S cited in acknowledgements  
  > "This paper makes use of the following ALMA data: ADS/JAO.ALMA#2012.1.01087.S." (Acknowledgements)
- Missing: Imaging parameters
- Missing: Line-free channels
- Missing: CASA version
- Missing: Fit procedure details
- Data volume (inferred): ~10-30 GB
- Score (inferred): 5/5, Single archival-type dataset and explicit equations, but imaging and fitting details are sparse.
- Rediscovery candidate: yes, Single-project data likely public, with numeric fluxes and masses to compare, though imaging details are sparse.

## Links

- Method: (cite: papadopoulos04) ([CI] gas mass formalism)
- Method: (cite: debreuck03) (dust mass and FIR luminosity equations)
- Companion: Emonts et al. 2016, in prep. (ATCA CO(1-0) and 36.5 GHz data)
- Related: H-ATLAS

## Checks

```json
{
 "quotes": 63,
 "quotes_ok": 63,
 "quote_pass_rate": 1.0,
 "quotes_too_long": 0,
 "unsupported_facts": 0,
 "project_codes": 1,
 "codes_not_in_text": [],
 "codes_not_in_obscore": [],
 "obscore_codes_not_in_card": [],
 "codes_printed_but_missing": [],
 "numeric_results": 11,
 "numeric_problems": 0,
 "fill": {
  "facts": 74,
  "stated": 40,
  "rate": 0.541
 },
 "evidence_ok": true
}
```
