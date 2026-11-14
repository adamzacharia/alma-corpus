# ALMA Observations of the Water Fountain Pre-planetary Nebula IRAS 16342-3814: High-velocity Bipolar Jets and an Expanding Torus

`2017ApJ...835L..13S` | The Astrophysical Journal Letters 2017 | first author: Sahai, R. | arXiv: 1612.05616 | DOI: 10.3847/2041-8213/835/1/L13

Card schema 1.0 | model claude-sonnet-5-5 | depth full | type observational_alma_primary

## Science

- Fields: evolved_stars
- Question: What are the structure, kinematics and mass-loss history of the water-fountain pre-planetary nebula IRAS 16342-3814 (jets, torus, AGB envelope, central continuum source), and what do they imply for the jet-launching binary models?  
  > "We have mapped $^{12}$CO J=3–2 and other molecular lines from the “water-fountain" bipolar pre-planetary nebula (PPN) IRAS 16342-3814 with $\sim0.35\ensuremath{''}$ resolution using ALMA." (abstract)
- Target **IRAS 16342-3814**: coordinates RA=16:37:39.935, Dec=-38:20:17.15 (J2000, continuum peak)  
  > "IRAS 16342-3814 (hereafter IRAS 16342) is the best studied and nearest ($\sim$2 kpc) water-fountain PPN." (Introduction); "peak located at (J2000) RA=16:37:39.935, Dec=-38:20:17.15" (footnote 2); z/distance ~2 kpc  
  > "IRAS 16342-3814 (hereafter IRAS 16342) is the best studied and nearest ($\sim$2 kpc) water-fountain PPN." (Introduction); "peak located at (J2000) RA=16:37:39.935, Dec=-38:20:17.15" (footnote 2); distance from _not stated_

## Data provenance

- ALMA projects: 2012.1.00678.S
- bands: Band 7  
  > "The data were obtained on 2015, June 13 with 37 antennas of the ALMA 12 m array in band 7." (2 Observations)
- frequencies and spectral setup: SPW0 345.170 GHz and SPW2 331.214 GHz (1.875 GHz, 3840 channels each); continuum SPW1 343.337 GHz and SPW4 333.104 GHz (2 GHz, 128 channels)  
  > "Two 1.875 GHz-bandwidth SPW’s were centered on 345.170 GHz (SPW0) and 331.214 GHz (SPW2) with 3840 channels each." (2 Observations)
- continuum bandwidth: _not stated_
- arrays: ALMA 12 m array, 37 antennas  
  > "with 37 antennas of the ALMA 12 m array in band 7" (2 Observations)
- configurations: _not stated_
- baselines: 21 to 783 m  
  > "The baselines range from 21 to 783 m implying a maximum recoverable scale of $\sim4$$''$." (2 Observations)
- angular resolution: ~0.35''  
  > "with $\sim0.35\ensuremath{''}$ resolution using ALMA" (abstract)
- max recoverable scale: ~4''  
  > "The baselines range from 21 to 783 m implying a maximum recoverable scale of $\sim4$$''$." (2 Observations)
- sensitivity: channel rms ~2.3 mJy/beam in 4 km/s line-free channels  
  > "Typical channel rms is $\sim 2.3$ mJy beam$^{-1}$ in line-free $4$ km s$^{-1}$ channels." (2 Observations)
- time on source: 35 min  
  > "Using 35 min on the science target, the data cover four spectral windows (SPW’s)." (2 Observations)
- observing dates: 2015 June 13  
  > "The data were obtained on 2015, June 13" (2 Observations)
- pi or archival as stated: _not stated_
- Line: 12CO J=3-2 (not stated)
- Line: 13CO J=3-2 (not stated)
- Line: H13CN J=4-3 (not stated)
- Other facility **APEX 12-m**: 0.87 mm continuum flux density 602±90 mJy for comparison (Ladjal et al. 2010)  
  > "The 0.87 mm continuum flux density observed with the 12-m APEX telescope’s $18.6\ensuremath{''}$ beam, $602\pm90$ mJy (Ladjal et al. 2010)," (3.3 The Central Continuum Source)
- Other facility **SEST**: 1.3 mm flux density 277±13 mJy (Guertler et al. 1996)  
  > "A 1.3 mm flux density of $277\pm13$ mJy (Guertler et al. 1996) was measured with the SEST $23{''}$ beam." (3.3 The Central Continuum Source)
- External data: HCN abundance f(HCN)=2.2e-7 from IK Tau  
  > "taking f(HCN)=$2.2\times10^{-7}$, from observations of the oxygen-rich AGB star IK Tau (Decin et al. 2010)" (3.2 A Central Torus) [from Decin et al. 2010]
- External data: Dust model extrapolated fluxes ~113 and 30 mJy at 0.886 and 1.3 mm  
  > "($\sim113$ & 30 mJy at 0.886 & 1.3 mm) derived from an extrapolation of the 2-D dust radiative-transfer model fit" (3.3 The Central Continuum Source) [from Murakawa & Izumiura 2012]
- External data: Dust opacity chi(0.85 mm)=1.4 cm2/g  
  > "taking $\chi_{\nu}(0.85\,mm)=1.4$ cm$^{2}$g$^{-1}$ (Sahai et al. 2011)" (3.3 The Central Continuum Source) [from Sahai et al. 2011]
- External data: Stellar luminosity L*=6000 Lsun and T*=650 K  
  > "given IRAS 16342’s luminosity of $L_{*}=6000$ $L_{\odot}$." (3.1 High-Velocity Outflows) [from Setal05 (T*=650 K)]

## Processing

### Calibration

- pipeline or manual: ALMA pipeline  
  > "The data were calibrated using the ALMA pipeline using Ceres as flux calibrator" (2 Observations)
- casa version: _not stated_
- pipeline version: _not stated_
- archive products used as is: _not stated_
- flux calibrator: Ceres (bandpass J1924-2914, gain J1636-4102)  
  > "using Ceres as flux calibrator and the quasars J1924-2914 ($\sim2.7$ Jy) and J1636-4102 ($\sim0.14$ Jy) as bandpass and gain calibrator respectively" (2 Observations)
- flux scale uncertainty: _not stated_
- self calibration: Self-calibration on the continuum emission of IRAS 16342  
  > "Following the standard calibration, self-calibration was performed on the continuum emission of IRAS 16342." (2 Observations)

### Imaging

- task: _not stated_
- deconvolver: _not stated_
- weighting robust: Briggs weighting (robust not stated)  
  > "Images were created using a Briggs weighting scheme channel averaging to $4$ km s$^{-1}$ in continuum subtracted line SPW’s." (2 Observations)
- uv taper: _not stated_
- cell size: _not stated_
- image size: _not stated_
- masking: _not stated_
- multiscale scales: _not stated_
- continuum subtraction: line SPWs continuum subtracted  
  > "channel averaging to $4$ km s$^{-1}$ in continuum subtracted line SPW’s" (2 Observations)
- line free channels: _not stated_
- primary beam correction: _not stated_
- array combination: _not stated_
- smoothing: channel averaging to 4 km/s (line); ~14 km/s effective channel width in continuum SPWs  
  > "In the continuum SPW’s the effective channel width corresponds to $\sim14$ km s$^{-1}$." (2 Observations)
- final beam: continuum beam 0.50'' x 0.26'', PA=-78.2 deg  
  > "(beam is $0.50\ensuremath{''}\times0.26\ensuremath{''}$, $PA=-78.2$$^\circ$)" (3.3 The Central Continuum Source)
- final rms: ~2.3 mJy/beam per 4 km/s channel  
  > "Typical channel rms is $\sim 2.3$ mJy beam$^{-1}$ in line-free $4$ km s$^{-1}$ channels." (2 Observations)

### Inherited from earlier work

- Mass, momentum and energy formulation for the outflow  
  > "using the formulation described in Bujarrabal et al. (2001)" (3.1 High-Velocity Outflows) [from Bujarrabal et al. 2001]
- Accretion rate scaling relative to CRL 618 and comparison with accretion models  
  > "Using Eqn. 6 of BL14," (4 Discussion and Concluding Remarks) [from Blackman & Lucchini 2014 (BL14)]
- Dust emission radius formula  
  > "(Setal99)" (3.3 The Central Continuum Source) [from Sahai et al. 1999 (Setal99)]
- Photodissociation-based mass-loss limit  
  > "(Mamon et al. 1988)" (3.4 The Progenitor AGB Circumstellar Envelope) [from Mamon et al. 1988]

### Not stated but needed to reproduce (our reading)

- Briggs robust value, cell size, image size, and clean masks/thresholds
- Which images and cubes used (tclean parameters, deconvolver)
- CASA/pipeline version
- Self-calibration solution intervals and number of iterations
- Line-free channels and continuum-subtraction order
- Method for radiative transfer/excitation giving Tex, tau, and mass-loss rate (code not named)
- Rest frequencies adopted for lines
- Exact procedure for deriving blob positions/ages and wedge intensity cuts

## Analysis recipe

1. **Image lines and continuum**: Pipeline calibration, self-calibration on continuum, Briggs-weighted imaging with 4 km/s channels  
  > "Images were created using a Briggs weighting scheme channel averaging to $4$ km s$^{-1}$ in continuum subtracted line SPW’s." (2 Observations)
   - software: ALMA pipeline
   - fitting: _not stated_
   - validation: _not stated_
2. **Map high-velocity outflows and derive blob ages**: Moment-0 maps and PV plots along nebular axis; assume radial blob motion at 250 km/s to derive ages  
  > "If we assume that all blobs are moving radially with this same outflow speed, i.e., 250 km s$^{-1}$, then we can derive the locations of blob pairs" (3.1 High-Velocity Outflows)
   - parameter: moment-0 integrated over ±260 km/s of Vlsr~45 km/s  
  > "generated by integrating over a velocity range $\pm260$ km s$^{-1}$ relative to the systemic velocity" (3.1 High-Velocity Outflows)
   - assumption: uniform radial outflow speed of 250 km/s; distance 2 kpc  
  > "the assumption of a uniform radial outflow velocity is likely not strictly true, and the derived ages are somewhat uncertain" (3.1 High-Velocity Outflows)
   - fitting: _not stated_
   - validation: _not stated_
3. **Derive HVO mass, momentum, energy**: Optically thin 12CO J=3-2 following Bujarrabal et al. 2001  
  > "assuming the emission to be optically-thin (and distance 2 kpc), is $P_{HVO}>1.7\times10^{38}$ g cm s$^{-1}$" (3.1 High-Velocity Outflows)
   - parameter: inclination 43 deg; Texc=15-30 K  
  > "We assume a uniform excitation temperature, $T_{exc}=15-30$ K" (3.1 High-Velocity Outflows)
   - assumption: f(12CO)=3e-4, f(13CO)=1e-4 (12/13~3)  
  > "we assume that $f_{12/13}\sim3$, the lowest value achievable via equilibrium CNO nucleosynthesis, and take f($^{12}$CO)=$3\times10^{-4}$" (3.1 High-Velocity Outflows)
   - fitting: _not stated_
   - validation: Texc range gives ~±20% uncertainty  
  > "resulting in a $\sim\pm20$% uncertainty in $P_{HVO}$, $E_{HVO}$, and $M_{HVO}$" (3.1 High-Velocity Outflows)
4. **Characterize torus size, inclination, density**: H13CN J=4-3 channel maps and PV cuts along torus major/minor axes; optically thin column density and density from HCN abundance  
  > "Using the tilted torus’s projected size along its major axis (0.65$''$) and minor axis (0.44$''$) as measured from the PV plots" (3.2 A Central Torus)
   - parameter: Tex=65 K from 12CO/13CO  
  > "assumed excitation temperature, 65 K, derived from the $^{12}$CO and $^{13}$CO J=3–2 line intensities" (3.2 A Central Torus)
   - assumption: H13CN abundance one-third of HCN; f(HCN) from IK Tau or theory  
  > "If we assume the fractional abundance of H$^{13}$CN to be one-third that of HCN, f(HCN)" (3.2 A Central Torus)
   - fitting: _not stated_
   - validation: _not stated_
5. **Analyze central continuum source and dust mass**: Compare ALMA flux with APEX/SEST and model; infer beta and Td from excess flux and dust emission radius; derive mass with chi=1.4 cm2/g  
  > "we find that the dust emissivity power-law ($\chi_{\nu}\propto\nu^{\beta}$) index is, $\beta\sim0.46-0.27$ for a dust temperature of, $T_d\sim30-120$ K" (3.3 The Central Continuum Source)
   - assumption: excess emission is thermal dust; free-free negligible  
  > "The contribution of free-free emission is negligible given the upper limit on radio emission by Sahai et al. (2011)" (footnote 3)
   - fitting: _not stated_
   - validation: _not stated_
6. **Characterize AGB CSE and mass-loss rate**: Mean 12CO and 13CO intensities at 44 km/s in 26-deg wedges along PA 133/-47 vs radius; 12/13 ratio gives optical depth, Tex, mass-loss rate  
  > "in two wedges of angular width $26\ensuremath{^\circ}$ oriented along $PA\sim133\ensuremath{^\circ}$ and $PA\sim-47\ensuremath{^\circ}$ as a function of radius, and average these" (3.4 The Progenitor AGB Circumstellar Envelope)
   - assumption: photodissociation of 13CO beyond Rout limits outer mass-loss rate  
  > "We therefore conclude that there is preferential photodissociation of $^{13}$CO over $^{12}$CO by the interstellar UV at $r\gtrsim1{''}$" (3.4 The Progenitor AGB Circumstellar Envelope)
   - fitting: _not stated_
   - validation: _not stated_
7. **Constrain accretion models**: Scale HVO accretion rate relative to CRL 618 using BL14 Eqn. 6  
  > "we scale the accretion rate for IRAS 16342’s HVO relative to that of CRL 618" (4 Discussion and Concluding Remarks)
   - fitting: _not stated_
   - validation: _not stated_

## Software

- **ALMA pipeline** : calibration  
  > "The data were calibrated using the ALMA pipeline" (2 Observations)

## Numeric results

| quantity | value | uncertainty | units | step | quote |
|---|---|---|---|---|---|
| HVO mass | 6.2e-3 | ~±20% | Msun | 3 | The HVO mass is, $M_{HVO}=6.2\times10^{-3}$ $M_{\odot}$. |
| HVO momentum | >1.7e38 | ~±20% | g cm/s | 3 | $P_{HVO}>1.7\times10^{38}$ g cm s$^{-1}$ and $E_{HVO}>3.2\times10^{45}$ erg |
| HVO age | ~110 | not stated | yr | 2 | We conclude that the HVO expansion age is $\sim110$ yr. |
| Torus size | 1300 | not stated | AU | 4 | we find that the torus size is 1300 AU, and its inclination is 43$^\circ$ |
| Torus expansion age | 160 | not stated | yr | 4 | The deprojected torus expansion velocity is, $V_{tor}=20$ km s$^{-1}$, and its expansion time-scale is 160 yr. |
| Continuum integrated flux at 338.19 GHz | 0.69 | not stated | Jy | 5 | The peak intensity and integrated flux are 0.25 Jy/beam and 0.69 Jy at $\nu=338.19$ GHz. |
| Dust mass of large-grain component | 0.017 | not stated | Msun | 5 | the dust mass of this large-grain component is, $M_d=0.017$ $M_{\odot}$ |
| AGB mass-loss rate | >3.5e-4 (Vagb/23 km/s) | not stated | Msun/yr | 6 | a mass-loss rate $\mbox{$\dot{M}$}_{AGB}>3.5\times10^{-4}\,(V_{AGB}/23\,\mbox{km~s$^{-1}$})$ $M_{\odot}$ yr$^{-1}$ |
| AGB CSE expansion age at Rout | 455 | not stated | yr | 6 | The AGB expansion time-scale at $r=R_{out}$ is 455 yr (23 km s$^{-1}$/$V_{AGB}$). |
| Torus H13CN column density | 4e15 (dV/1 km/s) | not stated | cm^-2 | 4 | N(H$^{13}$CN)=$4\times10^{15}$ cm$^{-2}$($\delta V/1\,\mbox{km~s$^{-1}$})$ |

## Qualitative findings

- Binary models with BHL wind accretion and wind RLOF are ruled out; enhanced RLOF or common-envelope accretion needed  
  > "Enhanced RLOF from the primary (i.e., at the Red Rectangle level: BL14), or accretion within CE evolution appear to be the most likely candidates" (4 Discussion and Concluding Remarks)

## Claim tuples

- H: Is a torus and high-velocity jet formed soon after a sharp AGB mass-loss increase? | E: Derived expansion ages of AGB CSE, EHVO, torus and HVO from ALMA CO and H13CN data | R: AGB CSE ~455 yr, EHVO 130-305 yr, torus 160 yr, HVO ~110 yr | F: Torus and HVO formed a few hundred years after a sharp increase in mass-loss rate | **supported**
- H: Does the mm continuum imply large grains? | E: Compared 0.89 mm flux with model and single-dish fluxes; derived beta and dust mass | R: beta~0.27, Td~120 K, Md=0.017 Msun | F: Substantial mass of mm-sized grains, if thermal dust | **partially**
- H: What accretion mode can power the HVO? | E: Scaled the HVO accretion rate relative to CRL 618 using BL14 | R: Mdot_a ~0.2 x that of CRL 618 | F: BHL and M-WRLOF ruled out for WD and MS accretors | **supported**

## Reasoning

- Why this data: _not stated_
- Why this method: _not stated_
- Alternative: Radiation pressure cannot drive the HVO (timescale too long, >7.3e3 yr)  
  > "The HVO cannot be driven by radiation pressure because its dynamical (expansion) time-scale is much smaller" (3.1 High-Velocity Outflows)
- How they decided it was enough: _not stated_
- Limitation (authors): Blob ages uncertain due to assumed uniform radial velocity  
  > "the assumption of a uniform radial outflow velocity is likely not strictly true, and the derived ages are somewhat uncertain" (3.1 High-Velocity Outflows)
- Caveat (inferred, ours): Many results are lower limits relying on optically thin and abundance assumptions (f12/13~3)
- Caveat (inferred, ours): Large-grain interpretation rests on single-band continuum and single-dish fluxes with different beams
- Caveat (inferred, ours): Processing details too sparse to reproduce images exactly
- Caveat (inferred, ours): Distance of 2 kpc is unreferenced

## Reproducibility

- Data public (paper): Dataset ADS/JAO.ALMA#2012.1.00678.S cited  
  > "This paper uses ALMA dataset ADS/JAO.ALMA#2012.1.00678.S." (Discussion and Concluding Remarks)
- Products in archive: _not stated_
- Missing: Imaging parameters (robust, cell, size, masks)
- Missing: CASA/pipeline version
- Missing: Radiative-transfer/excitation modelling details
- Missing: Blob identification and PV cut specifics
- Data volume (inferred): ~50-100 GB raw for one 35-min Band 7 execution with 4 SPWs
- Score (inferred): 3/5, Public data and numeric results, but sparse imaging and modelling details; short letter.
- Rediscovery candidate: no, Recipe incomplete for several derived quantities (excitation modelling, imaging parameters).

## Links

- Method: Bujarrabal et al. 2001 (formulation for outflow mass, momentum, energy)
- Method: Blackman & Lucchini 2014 (minimum accretion rate comparison with models)
- Companion: Sahai et al. (2017, in prep.) (discusses SO, CS, 29SiO, SO2, 34SO lines from same data)

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
  "facts": 86,
  "stated": 51,
  "rate": 0.593
 },
 "evidence_ok": true
}
```
