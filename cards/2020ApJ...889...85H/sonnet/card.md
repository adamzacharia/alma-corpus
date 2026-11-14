# Evolution from Spherical AGB Wind to Multipolar Outflow in Pre-planetary Nebula IRAS 17150-3224

`2020ApJ...889...85H` | The Astrophysical Journal 2020 | first author: Huang, Po-Sheng | arXiv: 1912.06358 | DOI: 10.3847/1538-4357/ab5f09

Card schema 1.0 | model claude-sonnet-5-5 | depth full | type observational_alma_primary

## Science

- Fields: evolved_stars
- Question: How does the spherical AGB wind of the pre-planetary nebula IRAS 17150-3224 evolve into multipolar outflows, and what are the ages and shaping mechanisms of the outflows?  
  > "The aim is to determine the mass-loss process in the end of the AGB phase and the shaping mechanism of the outflows." (4 Model for I17150)
- Target **IRAS 17150-3224 (Cotton Candy Nebula, I17150)**: coordinates RA 17h18m19.875s, Dec -32d27m21.8s (ICRS, continuum primary peak)  
  > "In this paper, we assume $d=3$ kpc as an average and $V_{\rm{sys}} = 14$ km s$^{-1}$." (1 Introduction); "The ICRS coordinate of the primary peak is R.A. $=17^{\rm{h}}18^{\rm{m}}19^{\rm{s}}_{^.}875$, Dec. $=-32$$^\circ$   $27^{\prime}$ $21^{\prime\prime}_{^\textrm{.}}8$." (3.1 350 GHz Continuum); z/distance d = 3 kpc; Vsys = 14 km/s  
  > "In this paper, we assume $d=3$ kpc as an average and $V_{\rm{sys}} = 14$ km s$^{-1}$." (1 Introduction); "The ICRS coordinate of the primary peak is R.A. $=17^{\rm{h}}18^{\rm{m}}19^{\rm{s}}_{^.}875$, Dec. $=-32$$^\circ$   $27^{\prime}$ $21^{\prime\prime}_{^\textrm{.}}8$." (3.1 350 GHz Continuum); distance from assumed average of 2.42 kpc (D05) and 3.6 kpc (M02)  
  > "In this paper, we assume $d=3$ kpc as an average and $V_{\rm{sys}} = 14$ km s$^{-1}$." (1 Introduction); "The ICRS coordinate of the primary peak is R.A. $=17^{\rm{h}}18^{\rm{m}}19^{\rm{s}}_{^.}875$, Dec. $=-32$$^\circ$   $27^{\prime}$ $21^{\prime\prime}_{^\textrm{.}}8$." (3.1 350 GHz Continuum)

## Data provenance

- ALMA projects: 2016.1.01530.S
- bands: Band 7 (350 GHz)  
  > "Observations of I17150 were carried out with ALMA in band 7 with 47 antennas in configuration of C40-6 on 2017 August 27." (2 Observations)
- frequencies and spectral setup: channel width ~244 kHz, ~0.212 km/s per channel  
  > "The channel width is $\sim$ 244 kHz, giving a velocity resolution of $\sim$ 0.212 km s$^{-1}$ per channel." (2 Observations)
- continuum bandwidth: _not stated_
- arrays: _not stated_
- configurations: C40-6, 47 antennas  
  > "Observations of I17150 were carried out with ALMA in band 7 with 47 antennas in configuration of C40-6 on 2017 August 27." (2 Observations)
- baselines: ~38 m to ~3.55 km  
  > "The shortest baseline was $\sim$ 38 m, and the longest baseline was $\sim$ 3.55 km." (2 Observations)
- angular resolution: ~0.09" x 0.06", PA ~ -81 deg (continuum); PA ~ -76 deg (CO)  
  > "The synthesized beam has a size of $\sim$ $0^{\prime\prime}_{^\textrm{.}}09$ $\times$ $0^{\prime\prime}_{^\textrm{.}}06$ with a position angle (P.A.) of $\sim$ $-$81$^{\circ}$." (2 Observations)
- max recoverable scale: _not stated_
- sensitivity: continuum ~0.1 mJy/beam; CO ~1.7 mJy/beam per 0.212 km/s channel  
  > "The noise level in the representative spectral window of CO is $\sim$ 1.7 mJy beam$^{-1}$ for a channel width of 0.212 km s$^{-1}$." (2 Observations)
- time on source: ~50 min  
  > "The target was observed for $\sim$ 50 min." (2 Observations)
- observing dates: 2017 August 27  
  > "Observations of I17150 were carried out with ALMA in band 7 with 47 antennas in configuration of C40-6 on 2017 August 27." (2 Observations)
- pi or archival as stated: _not stated_
- Line: CO J=3-2 (not stated)
- Other facility **HST (F606W)**: optical image showing the lobes and arcs, overlaid and used for arc positions in the model  
  > "superimposed on the optical image taken by the *HST* with filter F606W (cite: K98)" (3.1 350 GHz Continuum)
- Other facility **JCMT**: previously reported ~0.8 Jy at similar frequency, 19" resolution  
  > "previously reported at a similar frequency in (cite: H93) with James Clerk Maxwell Telescope (JCMT) at a resolution of $\sim$ $19^{\prime\prime}$" (3.1 350 GHz Continuum)
- External data: Arc positions A-G in HST image (1.2" to 4.6")  
  > "Previously, seven arc structures, A, B, C, D, E, F, and G, have been identified at a distance of" (3.5.1 Expansion Velocity of the AGB Wind) [from (cite: K98)]
- External data: Average AGB mass-loss rate 5.3e-4 Msun/yr  
  > "the averaged AGB mass-loss rate $\dot{M}_{\textrm{\scriptsize {a,0}}}=5.3\times10^{-4}$ M$_\ensuremath{\odot}$ yr$^{-1}$, as in the model of (cite: M02)" (4.1 AGB Wind) [from (cite: M02)]
- External data: Dust opacity 0.3 cm2/g at 350 GHz and gas-to-dust ratio 77  
  > "Assuming that the dust grains are similar to to those around evolved stars (cite: D18), we have ${\kappa}_{\nu}=0.3$ cm$^2$ g$^{-1}$ at 350 GHz" (3.1 350 GHz Continuum) [from (cite: D18)]
- External data: CO abundance 2e-4  
  > "we assume a CO abundance of $2 \times 10^{-4}$, similar to that of the circumstellar envelopes of O-rich stars (cite: W05)" (4.3 Model Results) [from (cite: W05)]

## Processing

### Calibration

- pipeline or manual: ALMA pipeline  
  > "The calibration and imaging were done by the ALMA pipeline in version r39732." (2 Observations)
- casa version: _not stated_
- pipeline version: r39732  
  > "The calibration and imaging were done by the ALMA pipeline in version r39732." (2 Observations)
- archive products used as is: _not stated_
- flux calibrator: J1733-1304 (flux); J1924-2914 bandpass; J1717-3342 phase  
  > "The quasars J1924-2914, J1733-1304, and J1717-3342 were observed for the bandpass, flux, and phase calibration, respectively." (2 Observations)
- flux scale uncertainty: _not stated_
- self calibration: _not stated_

### Imaging

- task: _not stated_
- deconvolver: _not stated_
- weighting robust: robust = 0.5 (continuum and CO)  
  > "a weighting with a robustness parameter of 0.5 was adopted for the uv visibilities" (2 Observations)
- uv taper: _not stated_
- cell size: _not stated_
- image size: _not stated_
- masking: _not stated_
- multiscale scales: _not stated_
- continuum subtraction: _not stated_
- line free channels: _not stated_
- primary beam correction: _not stated_
- array combination: _not stated_
- smoothing: 15 channels binned to one ~3.2 km/s channel for channel maps  
  > "we binned 15 channels to one single wide channel with a velocity width of $\sim$ 3.2 km s$^{-1}$" (3.4 CO Channel Maps)
- final beam: ~0.09" x 0.06"  
  > "The synthesized beam has a size of $\sim$ $0^{\prime\prime}_{^\textrm{.}}09$ $\times$ $0^{\prime\prime}_{^\textrm{.}}06$ with a P.A. of $\sim -$76$^{\circ}$." (2 Observations)
- final rms: 0.1 mJy/beam continuum; 1.7 mJy/beam per channel CO  
  > "The noise level is $\sim$ 0.1 mJy beam$^{-1}$." (2 Observations)

### Inherited from earlier work

- Radiative transfer code (LTE) for CO 3-2 model emission  
  > "The CO $J=3$–2 emissions are calculated using a radiative transfer code with an assumption of local thermal equilibrium (cite: H16)." (4.3 Model Results) [from (cite: H16)]
- Outflow velocity form similar to LS03 wind input; shell structure following LS03 simulations  
  > "Our velocity form is similar to the input velocity of the wind in (cite: LS03)." (4.2 Outflows) [from (cite: LS03)]
- Dust temperature ~150 K  
  > "dust temperature $T_{d} \sim 150$ K (cite: M02; dV15)" (3.1 350 GHz Continuum) [from (cite: M02; dV15)]

### Not stated but needed to reproduce (our reading)

- Name and version of the radiative transfer code (only cited to H16)
- CASA version used by the pipeline
- Line-free channels and continuum subtraction method
- Image size, cell size, and cleaning parameters
- How the model was fit (manual vs algorithm) and the parameter search ranges
- Rest frequency of CO 3-2 used and spectral window setup
- Flux calibration uncertainty
- PV cut widths and the model-to-data comparison procedure for absorption stripes

## Analysis recipe

1. **Continuum mass estimate**: Optically thin thermal dust: Md = D^2 F / (B(Td) kappa); gas mass via gas-to-dust ratio  
  > "Assuming that the continuum emission is all thermal dust emission and optically thin, the dust mass producing the continuum emission can be roughly estimated from the following equation" (3.1 350 GHz Continuum)
   - parameter: Td ~150 K; kappa = 0.3 cm2/g at 350 GHz; gas-to-dust 77  
  > "Thus, we adopt a ratio of 77, as found in the circumstellar envelope around O-rich stars (cite: D18)" (3.1 350 GHz Continuum)
   - assumption: d = 3 kpc; optically thin; all emission thermal dust  
  > "In this paper, we assume $d=3$ kpc as an average" (1 Introduction)
   - fitting: _not stated_
   - validation: Gas mass 5.4 Msun judged reasonable for OH/IR star; ratio 280 gave 20 Msun, too big  
  > "which seems too big for an OH/IR star, like our source" (3.1 350 GHz Continuum)
2. **Map outflow morphology and kinematics**: CO moment/intensity-weighted velocity maps, line profile, channel maps and PV diagrams along outflow axes  
  > "Position-velocity (PV) diagrams can be used to reveal the kinematics of the outflow lobes." (3.5 Position-Velocity Diagrams)
   - parameter: CO integrated from -15 to 45 km/s; Vsys = 14 km/s  
  > "integrated from $-$15 to 45 km s$^{-1}$" (3.2 CO Intensity and Velocity Maps)
   - fitting: _not stated_
   - validation: _not stated_
3. **AGB wind expansion velocity from absorption stripes**: Model absorption stripes in PV diagram linked to HST arcs, assuming constant velocity for inner arcs and a jump from arc D to E  
  > "we assume the expansion velocity to be the same for the inner arcs and to increase from arc D to arc E" (3.5.1 Expansion Velocity of the AGB Wind)
   - parameter: inner arcs ~13 km/s, outer arcs ~14.4 km/s  
  > "the expansion velocity of inner arcs A, B, C, and D are found to be $\sim$ 13 km s$^{-1}$" (3.5.1 Expansion Velocity of the AGB Wind)
   - fitting: _not stated_
   - validation: model stripes match observed reasonably well  
  > "the resulting model absorption stripes (as indicated by the dashed curves) can match the observed absorption stripes reasonably well" (3.5.1 Expansion Velocity of the AGB Wind)
4. **Forward model AGB wind and outflows in CO 3-2**: Parametric model: spherical AGB wind with periodic density enhancements, ellipsoidal-shell outflows with r^-2 density, temperature and velocity laws; LTE radiative transfer; best-fit params in Tables 1 and 3  
  > "Our model consists of a spherical AGB wind, a quadrupolar outflow, and three pairs of bipolar outflows" (4 Model for I17150)
   - parameter: Mdot_a,0 = 5.3e-4 Msun/yr; shell thickness 0 to 600 au  
  > "the shells have a thickness increasing from 0 au at the base to 600 au at the outflow tips" (4.2 Outflows)
   - assumption: CO abundance 2e-4; He n=0.1 nH; density in outflows proportional to r^-2  
  > "we assume a CO abundance of $2 \times 10^{-4}$" (4.3 Model Results)
   - fitting: _not stated_
   - validation: Line profile peaks and absorption dip within 15%; channel maps and PV structures consistent with observations  
  > "should be consistent with the observed values within 15%" (4.3 Model Results)
5. **Dynamical ages of outflows and AGB arcs**: Age from lobe length and tip velocity in model; arcs from distance and expansion velocity  
  > "The resulting dynamical ages are $\sim$ 350 yr for outflows Q1 and Q2, 280 yr for outflow B1, 200 yr for outflow B2, and 50 yr for outflow B3." (4.3 Model Results)
   - fitting: _not stated_
   - validation: _not stated_

## Software

- **ALMA pipeline** r39732: calibration and imaging  
  > "The calibration and imaging were done by the ALMA pipeline in version r39732." (2 Observations)

## Numeric results

| quantity | value | uncertainty | units | step | quote |
|---|---|---|---|---|---|
| Continuum total flux density (three components) | ~0.3 | not stated | Jy | 1 | The total flux density of the continuum in the three components is $\sim$ 0.3 Jy |
| Dust mass | ~7e-2 | not stated | Msun | 1 | $M_{d} \sim 7
\times 10^{-2}$ M$_{\ensuremath{\odot}}$ |
| Gas mass of shell (gas-to-dust 77) | ~5.4 | not stated | Msun | 1 | find it to be $\sim$ 5.4 M$_{\ensuremath{\odot}}$ |
| AGB expansion velocity inner arcs | ~13 | not stated | km/s | 3 | the expansion velocity of inner arcs A, B, C, and D are found to be $\sim$ 13 km s$^{-1}$ |
| AGB expansion velocity outer arcs | ~14.4 | not stated | km/s | 3 | the expansion velocity of the outer arcs E, F, G, and etc are found to be $\sim$ 14.4 km s$^{-1}$ |
| Dynamical age of arc A (end of AGB wind) | ~1300 | not stated | yr | 5 | estimated to be $\sim$ 1300, 1850, 2410, 2970, 3180, 3860, 4550, and 5230 yr |
| Dynamical ages Q1/Q2, B1, B2, B3 | ~350, 280, 200, 50 | not stated | yr | 5 | The resulting dynamical ages are $\sim$ 350 yr for outflows Q1 and Q2, 280 yr for outflow B1, 200 yr for outflow B2, and 50 yr for outflow B3. |
| Outflow tip velocities Q1, Q2, B1, B2, B3 | ~130, 130, 100, 100, 80 | not stated | km/s | 4 | the velocities at the tips of outflows Q1, Q2, B1, B2, and B3 are $\sim$ 130, 130, 100, 100, and 80 km s$^{-1}$, respectively |
| Total outflow mass | ~0.6 | not stated | Msun | 4 | The total mass of the outflows are $\sim$ 0.6 M$_\ensuremath{\odot}$. |
| CO peak flux of line profile | ~8.6 at ~16 km/s | not stated | Jy | 2 | The line profile has a peak flux of $\sim$ 8.6 Jy at $\sim$ 16 km s$^{-1}$ |

## Qualitative findings

- The optically bipolar lobe is actually a quadrupolar outflow of two overlapping bipolar outflows; two additional younger bipolar outflows (B1, B2) and an inner outflow B3 are detected.  
  > "CO map shows that it is actually a quadrupolar outflow consisting of two overlapping bipolar outflows." (abstract)
- Blueshifted absorption stripes in PV maps arise from absorption by AGB shells.  
  > "blueshifted absorption stripes are detected in the outflow emissions, due to absorption by a series of shells produced by a series of asymptotic giant branch (AGB) wind ejections." (abstract)

## Claim tuples

- H: Is the optical bipolar lobe of I17150 truly bipolar? | E: CO 3-2 intensity and velocity maps plus channel maps and PV diagrams | R: Two overlapping bipolar outflows Q1 and Q2 with opposite inclinations, same age ~350 yr | F: Quadrupolar outflow, likely from simultaneous multidirectional bullets | **supported**
- H: Do the younger lower-latitude outflows trace a change of ejection direction? | E: Model dynamical ages of B1 and B2 | R: Ages 280 and 200 yr, decreasing with latitude | F: Could be produced by a precessing collimated fast wind | **partially**
- H: What caused the absorption stripes and what are the AGB wind properties? | E: Model the stripes with HST arc positions | R: Velocity ~13 km/s inner, ~14.4 km/s outer; innermost arc ~1300 yr ago | F: Periodic AGB mass loss shells absorb outflow emission; AGB wind ended ~1300 yr ago, possibly later if an unseen inner arc exists | **supported**

## Reasoning

- Why this data: _not stated_
- Why this method: Forward modeling of morphology, line profile, and PV structures to derive physical properties and shaping mechanism  
  > "Here we derive the physical properties (including temperature, density, velocity, and the mass-loss rate) of the AGB wind and the outflows by modeling their observed intensity maps, line profile, and PV structures in CO $J=3$–2." (4 Model for I17150)
- Alternative: Gas-to-dust ratio 280 rejected as it gives ~20 Msun, too big for an OH/IR star  
  > "Using this ratio, we derive a shell mass of $\sim$ 20 M$_{\ensuremath{\odot}}$, which seems too big for an OH/IR star, like our source." (3.1 350 GHz Continuum)
- Alternative: Two separate bipolar winds from two stars rejected as very unlikely  
  > "However, the chance of simultaneously producing two bipolar winds from two stars is very low." (5.3 Possible Shaping Mechanisms for the Quadrupolar Outflow)
- How they decided it was enough: _not stated_
- Limitation (authors): Distance poorly constrained; AGB stripe semi-major axis cannot be clearly identified; higher sensitivity needed for velocity jump  
  > "The distance to I17150 is not well constrained." (1 Introduction); "Further observations at higher sensitivity are needed to derive a precise value of the velocity jump from the PV diagrams." (3.5.1 Expansion Velocity of the AGB Wind)
- Caveat (inferred, ours): Model parameters are hand-tuned with no uncertainties or degeneracy analysis
- Caveat (inferred, ours): Dynamical ages scale with the assumed 3 kpc distance (range 2.4-3.6 kpc)
- Caveat (inferred, ours): Gas-to-dust ratio choice is ad hoc
- Caveat (inferred, ours): Imposed symmetry and shell thickness assumptions bias derived ages and masses

## Reproducibility

- Data public (paper): ALMA project code given in acknowledgments  
  > "This paper makes use of the following ALMA data: ADS$/$JAO.ALMA\#2016.1.01530.S." (Acknowledgments)
- Products in archive: _not stated_
- Missing: Radiative transfer model code and exact fitting procedure
- Missing: Imaging parameters beyond robust=0.5
- Missing: Line-free channel selection and PV cut details
- Data volume (inferred): ~50-100 GB (single Band 7 EB, long baselines)
- Score (inferred): 4/5, Archival data and pipeline reproduce the maps easily, but the forward model code is only cited and fitting is unspecified.
- Rediscovery candidate: no, Key results depend on a custom forward model whose code and fitting procedure are not provided.

## Links

- Method: Huang, Lee, Moraghan & Smith 2016, ApJ, 820, 134 (cite: H16) (radiative transfer/LTE modeling approach)
- Method: Lee & Sahai 2003 (cite: LS03) (outflow shell and velocity prescriptions)
- Companion: Meixner et al. 2002 (cite: M02) (circumstellar envelope model of I17150)

## Checks

```json
{
 "quotes": 70,
 "quotes_ok": 70,
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
  "facts": 79,
  "stated": 50,
  "rate": 0.633
 },
 "evidence_ok": true
}
```
