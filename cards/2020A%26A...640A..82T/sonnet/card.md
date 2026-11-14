# Constraining MHD disk winds with ALMA. Apparent rotation signatures and application to HH212

`2020A&A...640A..82T` | Astronomy and Astrophysics 2020 | first author: Tabone, B. | arXiv: 2004.08804 | DOI: 10.1051/0004-6361/201834377

Card schema 1.0 | model claude-sonnet-5-5 | depth light | type theory_or_simulation_compared_to_alma

## Science

- Fields: protoplanetary_disks, star_formation
- Question: Which systematic biases affect the launch radius, magnetic lever arm and angular momentum flux of an MHD disk wind when inferred from apparent rotation signatures in ALMA-like PV diagrams, and do published HH212 ALMA data confirm the predictions?  
  > "We wish to identify systematic biases in retrieving the true launch zone, magnetic lever arm, and associated angular momentum flux of an MHD DW from apparent rotation signatures" (abstract)
- Target **HH212**: coordinates _not stated_; z/distance 450 pc (inclination 87 deg)  
  > "we adopt for HH212 a systemic velocity of $V_{\rm sys}$ = 1.7 km s$^{-1}$(cite: 2014ApJ...786..114L) and a distance $d$ = 450 pc." (4 Application to the edge-on rotating flow in HH212); distance from adopted for consistency with Tabone et al. 2017; VLBI Orion B parallaxes suggest ~400 pc (Kounkel et al. 2017)  
  > "we adopt for HH212 a systemic velocity of $V_{\rm sys}$ = 1.7 km s$^{-1}$(cite: 2014ApJ...786..114L) and a distance $d$ = 450 pc." (4 Application to the edge-on rotating flow in HH212)

## Data provenance

- ALMA projects: 2012.1.00997.S, 2016.1.01475.S
- bands: _not stated_
- frequencies and spectral setup: _not stated_
- continuum bandwidth: _not stated_
- arrays: _not stated_
- configurations: _not stated_
- baselines: _not stated_
- angular resolution: HH212 SO data at 0.55" (~250 au), 0.15" (~65-70 au), 0.04" (18 au)  
  > "SO blue/red channel maps of the base of the HH212 flow obtained at $0.55" \simeq$ 250 au resolution in ALMA Cycle 0 by (cite: 2015A&A...581A..85P)." (4.1)
- max recoverable scale: _not stated_
- sensitivity: _not stated_
- time on source: _not stated_
- observing dates: _not stated_
- pi or archival as stated: _not stated_
- Line: SO not stated (not stated)
- External data: SO channel maps at 0.55" (Cycle 0) of HH212  
  > "obtained at $0.55" \simeq$ 250 au resolution in ALMA Cycle 0 by (cite: 2015A&A...581A..85P)" (4.1) [from (cite: 2015A&A...581A..85P)]
- External data: SO PV cuts and apparent j ~30±15 au km/s at 0.04" resolution  
  > "Their value $\simeq 30 \pm 15$  au km s$^{-1}$ remains remarkably similar to our results at 0.55$''$ and 0.15$''$." (4.1) [from (cite: 2018ApJ...856...14L)]
- External data: 0.15" SO/SO2 data and MHD DW model for HH212 (L5W30, r_out=40 au)  
  > "It was obtained with the MHD DW solution L5W30, $r_{\rm out}$= 40 au, $M_\star=0.2 M_{\odot}$, $i=87^{\circ}$" (4.2) [from (cite: 2017A&A...607L...6T)]
- Simulation/model as data: Self-similar MHD disk wind solutions L13W36, L13W130, L5W30, L5W17 used to build synthetic PV cuts  
  > "Four semi-analytical solutions of magneto-centrifugal MHD disk winds (hereafter MHD DW), of which three are new, were computed" (2 MHD disk-wind solutions)

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
- weighting robust: _not stated_
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
- final beam: _not stated_
- final rms: _not stated_

### Inherited from earlier work

- HH212 MHD DW model parameters, systemic velocity and distance  
  > "For consistency with our previous modeling work in (cite: 2017A&A...607L...6T), we adopt for HH212 a systemic velocity" (4) [from (cite: 2017A&A...607L...6T)]
- Self-similar MHD DW solution formalism  
  > "developed and described by (cite: 1997A&A...319..340F; 2000A&A...353.1115C; 2000A&A...361.1178C), to which the reader is referred for more details" (2 MHD disk-wind solutions) [from (cite: 1997A&A...319..340F; 2000A&A...353.1115C; 2000A&A...361.1178C)]

### Not stated but needed to reproduce (our reading)

- Radiative transfer/synthetic channel map code not named
- Calibration and imaging of the reused ALMA data not described
- Spectro-astrometry centroid fitting details (channel ranges, noise treatment)
- Numerical solutions of the MHD DW ODEs not released

## Analysis recipe

1. **Build synthetic PV cuts from MHD DW solutions**: Self-similar solutions scaled to physical units, power-law emissivity, convolved with Gaussian beam at 0.44 km/s sampling  
  > "a parametrized emissivity function is adopted with a a simple power law radial variation" (3.1)
   - parameter: M*=0.1 Msun, r_in=0.25 au, r_out=8 au, i=87 deg, alpha=-2, beam 225 au, z_cut=225 au  
  > "$M_\star=0.1M_{\odot}$, $r_{\rm in}=0.25$ au, $r_{\rm out}=8$ au, $i=87^{\circ}$, $\alpha = -2$, and $\theta_b= 225$ au" (3.1)
   - assumption: Steady, axisymmetric, self-similar wind; optically thin  
  > "our MHD DW model is probably too idealized (self-similar, steady, axisymmetric)" (4.2)
   - fitting: _not stated_
   - validation: _not stated_
2. **Estimate j_obs, r_obs, lambda_obs with three methods and compare with true values**: Double-peak separation, rotation curve and flow width methods; Anderson's relation solved for r_obs  
  > "we will thus consider three methods used by observers to estimate the flow specific angular momentum from PV cuts at ALMA-like resolution" (3.2)
   - fitting: _not stated_
   - validation: _not stated_
3. **Test predictions on HH212 ALMA data**: Spectro-astrometry of blue/red centroids in 0.55" channel maps; compare PV cuts and model at 250, 70, 18 au  
  > "spatial shifts much smaller than the beam can still be detected by comparing centroid positions (the so-called “spectro-astrometry" technique)" (4.1)
   - assumption: _not stated_
   - fitting: _not stated_
   - validation: _not stated_
4. **Angular momentum extraction fraction f_J**: Analytic f_J = lambda_BP [1 + ln(r_out/r_in)/(2 ln(1+f_M))]^-1 applied with f_M from SO mass flux and accretion rate  
  > "$$\begin{equation}
\label{eq:fracj2}
f_J =  \lambda_{\rm BP} \times \left[ {1+ \frac{ \ln (r_{\rm out}/r_{\rm in}) }{2 \ln (1+f_M)} } \right]^{-1}.
\end{equation}$$" (4.3)
   - fitting: _not stated_
   - validation: _not stated_

## Software


## Numeric results

| quantity | value | uncertainty | units | step | quote |
|---|---|---|---|---|---|
| HH212 spatial shift at z~70 au (0.55") | 0.06 | 0.02 | arcsec | 3 | The shift amplitude at $z \simeq 70$ au is $\Delta r \simeq 0.06"\pm 0.02"$ (27 au) |
| HH212 apparent specific angular momentum | 27 | not stated | au km/s | 3 | the apparent specific angular momentum in both data sets is $j_{\rm obs}$$=(\Delta r/2)(\Delta V/2)\simeq$ 27 au km s$^{-1}$ |
| HH212 r_obs from Anderson relation | ~1 | not stated | au | 3 | Anderson's relation yields an estimated $r_{\rm obs}$$\simeq 1$ au. |
| f_M,obs for HH212 | 0.33-3.3 | not stated | dimensionless | 4 | we infer an ejection to accretion ratio $f_{M,\rm obs}$ = $\dot{M}_{\rm DW}$/ $\dot{M}_{\rm in}$= 0.33 – 3.3 |
| f_J,obs for HH212 | 0.5-1.8 | not stated | dimensionless | 4 | we obtain $f_{J,\rm obs}$ = 0.5 – 1.8 |
| Flow-width method r_obs and lambda_obs (reference model, i=40) | r_obs ~1.5 au, lambda_obs ~2 | not stated | au; dimensionless | 2 | we obtain with Anderson's method $r_{\rm obs}$$\simeq 1.5$ au and $\lambda_{\rm obs}$$\simeq 2$ |

## Qualitative findings

- Magnetic lever arm from Anderson's formula is always a lower limit due to angular momentum in magnetic torsion  
  > "The magnetic lever arm is always underestimated, due to invisible angular momentum stored as magnetic field torsion." (abstract)

## Claim tuples

- H: Double-peak separation recovers the true outer launch radius | E: Synthetic PV cuts of self-similar MHD DWs with varied parameters | R: r_obs is always a lower limit, independent of resolution, up to factor 10 off | F: Double-peak and flow-width methods underestimate r_out; rotation curve works when resolved | **supported**
- H: HH212 SO wind follows predicted biases | E: Compare PV peak separation at 250, 65 and 18 au resolution with the MHD DW model | R: j_obs ~27-30 au km/s at all resolutions, r_obs ~1 au vs r_out ~40 au | F: ALMA data confirm the predicted biases and large r_out | **supported**
- H: The HH212 MHD DW can sustain disk accretion | E: Apply analytic f_J with observed f_M | R: f_J = 0.5-1.8 | F: Enough angular momentum is extracted to sustain accretion | **supported**

## Reasoning

- Why this data: _not stated_
- Why this method: _not stated_
- Alternative: Swept-up shell driven by an X-wind, or bowshock-shocked disk wind, cannot be ruled out  
  > "Nevertheless, our proposed interpretation in terms of MHD DW is not unique." (4.2)
- How they decided it was enough: _not stated_
- Limitation (authors): Analysis is limited to self-similar steady axisymmetric models; biases may differ for other geometries  
  > "While our analysis strictly pertains only to self-similar models, we expect similar biases to occur in more general geometries" (5 Conclusions)
- Caveat (inferred, ours): ALMA data are not reprocessed; relies on published measurements
- Caveat (inferred, ours): Emissivity is a parametrized power law, not chemistry
- Caveat (inferred, ours): Distance uncertainty (400 vs 450 pc)

## Reproducibility

- Data public (paper): ALMA projects 2012.1.00997.S and 2016.1.01475.S acknowledged  
  > "This paper makes use of the ALMA 2012.1.00997.S and 2016.1.01475.S data (PI: C. Codella)." (Acknowledgements)
- Products in archive: _not stated_
- Missing: MHD DW solution numerical profiles
- Missing: Synthetic imaging code
- Missing: Calibrated HH212 images
- Data volume (inferred): tens of GB if archival data re-reduced
- Score (inferred): 3/5, Theory dominates; analytic parts reproducible but the model solutions and imaging pipeline are not provided.
- Rediscovery candidate: no, Main results rely on custom MHD solutions and published, not reprocessed, ALMA products.

## Links

- Method: (cite: 2003ApJ...590L.107A) (Anderson's relation for launch radius)
- Method: (cite: 1997A&A...319..340F) (Self-similar MHD disk wind formalism)
- Companion: (cite: 2017A&A...607L...6T) (Original HH212 MHD DW model)
- Companion: (cite: 2018ApJ...856...14L) (0.04" SO observations of HH212)

## Checks

```json
{
 "quotes": 34,
 "quotes_ok": 34,
 "quote_pass_rate": 1.0,
 "quotes_too_long": 0,
 "unsupported_facts": 0,
 "project_codes": 2,
 "codes_not_in_text": [],
 "codes_not_in_obscore": [],
 "obscore_codes_not_in_card": [],
 "codes_printed_but_missing": [],
 "numeric_results": 6,
 "numeric_problems": 0,
 "fill": {
  "facts": 67,
  "stated": 20,
  "rate": 0.299
 },
 "evidence_ok": true
}
```
