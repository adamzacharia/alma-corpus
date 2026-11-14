# Grand-design Spiral Arms in a Young Forming Circumstellar Disk

`2017ApJ...835L..11T` | The Astrophysical Journal Letters 2017 | first author: Tomida, Kengo | arXiv: 1611.09361 | DOI: 10.3847/2041-8213/835/1/L11

Card schema 1.0 | model claude-sonnet-5-5 | depth light | type theory_or_simulation_compared_to_alma

## Science

- Fields: protoplanetary_disks, star_formation
- Question: Can recurrent gravitational-instability material spiral arms in a long-term resistive MHD disk-formation simulation explain the grand-design spiral arms of Elias 2-27 seen by ALMA?  
  > "Our model suggests that the grand design spiral arms around Elias 2-27 are consistent with material arms formed by gravitational instability." (abstract)
- Target **Elias 2-27**: coordinates RA 16h26m45.024s, Dec -24d23m08.250s (J2000)  
  > "the source position is Right Ascension (J2000) = 16h26m45.024s, Declination (J2000) = -24d23m08.250s." (3.4 ALMA Simulation); "Assuming the object is located at a distance of 139 pc" (3.3 Dust Continuum Map); z/distance 139 pc (assumed)  
  > "the source position is Right Ascension (J2000) = 16h26m45.024s, Declination (J2000) = -24d23m08.250s." (3.4 ALMA Simulation); "Assuming the object is located at a distance of 139 pc" (3.3 Dust Continuum Map); distance from _not stated_

## Data provenance

- ALMA projects: 2013.1.00498.S
- bands: _not stated_
- frequencies and spectral setup: _not stated_
- continuum bandwidth: 6.8 GHz (simulated, chosen close to the Elias 2-27 observation)  
  > "We chose observation parameters as close to (cite: e2-27) as possible; the bandwidth is 6.8 GHz, the integration time is 12.5 minutes" (3.4 ALMA Simulation)
- arrays: _not stated_
- configurations: alma.cycle4.5.cfg (simulated)  
  > "We use “alma.cycle4.5.cfg" array configuration file" (3.4 ALMA Simulation)
- baselines: _not stated_
- angular resolution: 0.29 arcsec x 0.26 arcsec synthetic beam  
  > "This produces a synthetic beam of $0.29\, {\rm arcsec} \times 0.26\, {\rm arcsec}$, which is very close to the original observation." (3.4 ALMA Simulation)
- max recoverable scale: _not stated_
- sensitivity: _not stated_
- time on source: 12.5 minutes (simulated)  
  > "the integration time is 12.5 minutes" (3.4 ALMA Simulation)
- observing dates: _not stated_
- pi or archival as stated: _not stated_
- External data: Observed ALMA 1.3 mm continuum image of Elias 2-27 and its disk parameters (disk mass ~0.14 Msun, surface density estimates)  
  > "Observations of Elias 2-27 suggest that its disk can be indeed massive, $M_{\rm disk}\sim 0.14\, {\rm M_\odot}$ (cite: andrews09; e2-27)." (2.2 Results) [from (cite: e2-27) Pérez et al. 2016]
- External data: Accretion rate 8e-8 Msun/yr and spectral type M0 of Elias 2-27  
  > "we adopt $\dot{M}=8 \times 10^{-8}\, {\rm M_\odot\, yr^{-1}}$ to calculate the accretion luminosity based on the observation of Elias 2-27 (cite: najita15)" (3.1 Protostar Evolution) [from (cite: najita15)]
- External data: Dust opacity tables, composite aggregate model, normal abundance  
  > "we adopt the monochromatic opacity tables of (cite: semenov) [^2], using the composite aggregate dust model of the normal abundance." (3.2 Temperature Recalculation) [from (cite: semenov)]
- Simulation/model as data: 3D nested-grid resistive MHD simulation of collapsing 1.25 Msun Bonnor-Ebert-like core with Ohmic dissipation and barotropic EOS, run to ~47,000 yr protostar age  
  > "at the end of the simulation the protostar age reaches about 47,000 years." (2.2 Results)

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

- task: simobserve and simanalyze (CASA)  
  > "we perform simulated observation using the *simobserve* and *simanalyze* tasks" (3.4 ALMA Simulation)
- deconvolver: _not stated_
- weighting robust: Briggs, robustness 0.5 (simulated)  
  > "the Briggs waiting with the robustness of 0.5" (3.4 ALMA Simulation)
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

- MHD code details  
  > "We refer readers to (cite: mh13) and (cite: machida14; machida16) for the details." (2.1 Method and Model) [from (cite: mh13); (cite: machida14; machida16)]
- Barotropic approximation  
  > "we adopt the barotropic approximation as in (cite: mm12)" (2.1 Method and Model) [from (cite: mm12)]
- Protostellar evolution calculation  
  > "We calculate evolution of the central protostar using the STELLAR stellar evolution code (cite: yb08; hosokawa13; sakurai15), as in (cite: mh13)." (3.1 Protostar Evolution) [from (cite: mh13)]

### Not stated but needed to reproduce (our reading)

- Exact snapshot time/epoch chosen for the comparison
- Simulation code availability and initial-condition files
- Pointing/hour angle, precipitable water vapour and noise settings in simobserve
- Pixel size and cleaning parameters in simanalyze
- Source of the 139 pc distance
- How the synthetic image was compared quantitatively to the observation (only visual)

## Analysis recipe

1. **Run resistive MHD collapse simulation**: 3D nested-grid MHD with self-gravity, Ohmic dissipation, barotropic EOS and sink particle  
  > "This code solves the MHD equations with self-gravity and Ohmic dissipation." (2.1 Method and Model)
   - software: nested-grid MHD code
   - parameter: Initial core M0=1.25 Msun, R=6.1e3 AU, T=10 K, Omega=1.5e-13 s^-1, Bz=36 uG; finest resolution 0.75 AU; sink accretion radius 1 AU  
  > "we insert a sink particle with an accretion radius of 1 AU at the center of the domain" (2.1 Method and Model)
   - assumption: Cosmic-ray ionization 1e-17 s^-1, MRN dust  
  > "the ionization rate is dominated by cosmic rays, $\zeta=10^{-17}\, {\rm sec^{-1}}$." (2.1 Method and Model)
   - fitting: _not stated_
   - validation: Results said not to change qualitatively with different parameters  
  > "The results do not change qualitatively even when we use different parameters." (2.1 Method and Model)
2. **Protostar evolution**: STELLAR code with adopted accretion rate 8e-8 Msun/yr giving L_acc and Teff  
  > "which gives $L_{\rm acc}=0.379\, {\rm L_\odot}$. Assuming a black body spectrum, the effective stellar temperature is $T_{\rm eff}=4,000\, {\rm K}$." (3.1 Protostar Evolution)
   - software: STELLAR
   - assumption: Episodic accretion lets the actual accretion rate be lower than the simulated one  
  > "this is often interpreted as a result of episodic accretion." (3.1 Protostar Evolution)
   - fitting: _not stated_
   - validation: Teff agrees with the observed M0 spectral type  
  > "This agrees well with the observed spectral type of Elias 2-27, which is M0" (3.1 Protostar Evolution)
3. **Recalculate dust temperature**: RADMC-3D Monte Carlo radiative equilibrium with stellar irradiation, iterated for dust evaporation  
  > "we recalculate the dust temperature distribution assuming radiative equilibrium under irradiation from the central star." (3.2 Temperature Recalculation)
   - software: RADMC-3D
   - parameter: 2e9 photons, anisotropic scattering, no modified random walk, external radiation field T=10 K  
  > "we run RADMC-3D again using $2\times 10^9$ photons to make the temperature distribution as smooth as possible." (3.2 Temperature Recalculation)
   - assumption: Dust-to-gas fraction 0.014 (Semenov composite aggregate)  
  > "The dust-to-gas fraction of this model is 0.014 in the cold" (3.2 Temperature Recalculation)
   - fitting: _not stated_
   - validation: _not stated_
4. **Synthesize 1.3 mm continuum image**: RADMC-3D image at 1.3 mm  
  > "we calculate the intensity distribution of dust continuum at 1.3 mm again using RADMC-3D." (3.3 Dust Continuum Map)
   - software: RADMC-3D
   - parameter: inclination 55.8 deg, distance 139 pc, image (10,000 AU)^2 with 4000^2 pixels  
  > "we calculate the image covering $(10,000\, {\rm AU})^2$ with $4,000^2$ pixels." (3.3 Dust Continuum Map)
   - assumption: kappa_1.3mm ~0.95 cm2/g per dust mass  
  > "The opacity table we use has $\kappa_{1.3{\rm mm}} \sim 0.95 \, {\rm cm^2 \, g^{-1}}$ per unit dust mass in most region within the disk." (3.3 Dust Continuum Map)
   - fitting: _not stated_
   - validation: _not stated_
5. **Simulate ALMA observation and compare**: CASA simobserve/simanalyze with Cycle 4.5 config, compared visually with the observed image  
  > "The disk size, brightness, and thickness of the spiral arms are largely consistent with the observation." (3.4 ALMA Simulation)
   - software: CASA
   - fitting: _not stated_
   - validation: Synthetic beam close to the original observation  
  > "which is very close to the original observation." (3.4 ALMA Simulation)

## Software

- **CASA** : simobserve and simanalyze synthetic ALMA observation  
  > "we perform simulated observation using the *simobserve* and *simanalyze* tasks" (3.4 ALMA Simulation)
- **RADMC-3D** : dust temperature and 1.3 mm continuum image  
  > "we utilize RADMC-3D[^1] (cite: radmc), which computes radiation transfer using the Monte-Carlo method." (3.2 Temperature Recalculation)
- **STELLAR** : protostar evolution  
  > "We calculate evolution of the central protostar using the STELLAR stellar evolution code" (3.1 Protostar Evolution)
- **VisIt** : producing Figure 4  
  > "We use VisIt (cite: visit) to produce Figure [4](#temp)." (Acknowledgments)

## Numeric results

| quantity | value | uncertainty | units | step | quote |
|---|---|---|---|---|---|
| Disk radius toward end of Class-I | >200 | not stated | AU | 1 | Toward the end of the Class-I phase, the disk size becomes larger than 200 AU in the expanding phases with spiral arms. |
| Disk-to-star mass ratio | 30-40% | not stated | percent | 1 | The disk-to-star mass ratio remains almost constant and is about 30-40% throughout the Class-0 and I phases. |
| Spiral arm occurrence probability | ~50% | not stated | percent | 1 | the occurrence probability of the spiral arms is about 50%. |
| Stellar mass/radius/luminosity at chosen epoch | M*=0.444 Msun, R*=2.935 Rsun, L*=1.604 Lsun | not stated | Msun, Rsun, Lsun | 2 | $M_*=0.444\, {\rm M_\odot}$, $R_*=2.935\, {\rm R_\odot}$ and $L_*=1.604\, {\rm L_\odot}$ |
| Envelope H2 column density | 6.34e21 | not stated | cm^-2 | 4 | $N_{\rm H_2} \sim 6.34 \times 10^{21} \, {\rm cm^{-2}}$ |

## Qualitative findings

- Spiral arms disappear in a few rotations but re-form recurrently as the disk becomes unstable again  
  > "new spiral arms form recurrently as the disk soon becomes unstable again by gas accretion." (abstract)

## Claim tuples

- H: Recurrent GI material spiral arms can form in a young resistive-MHD disk | E: Long-term 3D resistive MHD simulation | R: Grand-design m=2 arms form recurrently with Q~1 and persist through Class-0/I | F: Gravitational torque is a key angular momentum transport process | **supported**
- H: Elias 2-27 spiral arms can be material arms from GI | E: Synthetic 1.3 mm ALMA observation of a snapshot compared with observation | R: Disk size, brightness and arm thickness largely consistent; no gaps or outflow reproduced | F: Observed arms are consistent with GI material arms | **partially**

## Reasoning

- Why this data: _not stated_
- Why this method: _not stated_
- Alternative: Density wave scenario favored by Pérez et al. rejected in favor of recurrent material arms  
  > "While (cite: e2-27) favored the density wave scenario pointing out that material spiral arms should disappear in a few orbital periods" (4 Discussions and Conclusions)
- How they decided it was enough: _not stated_
- Limitation (authors): No ambipolar diffusion, Hall effect or radiation transfer in the MHD run; temperature post-processed  
  > "The current MHD simulation does not consider ambipolar diffusion, the Hall effect and radiation transfer." (4 Discussions and Conclusions)
- Limitation (authors): Gap-like structures and absent small-scale outflow not matched  
  > "some features do not match perfectly. For example, gap-like structures exist in Elias 2-27 but we do not find any significant gap in our synthetic observation." (4 Discussions and Conclusions)
- Caveat (inferred, ours): Single snapshot chosen to resemble the target; comparison is visual only
- Caveat (inferred, ours): Accretion rate and inclination tuned to match observation
- Caveat (inferred, ours): Barotropic EOS and fixed opacity (lower than Pérez et al.) affect the Q and brightness
- Caveat (inferred, ours): Only one initial condition explored

## Reproducibility

- Data public (paper): ALMA data acknowledged by project code; simulation code not stated as public  
  > "This paper makes use of the following ALMA data: ADS/JAO.ALMA#2013.1.00498.S." (Acknowledgments)
- Products in archive: _not stated_
- Missing: MHD code and snapshot data not released
- Missing: simobserve parameters beyond those listed
- Missing: Procedure for selecting snapshot
- Data volume (inferred): Small; only the published Elias 2-27 image is needed for comparison (<~1 GB); main cost is the MHD simulation.
- Score (inferred): 2/5, Primarily a simulation paper with a custom unreleased MHD code; the ALMA part is a simulated observation with partial settings.
- Rediscovery candidate: no, Main results come from a non-public simulation and are qualitative comparisons.

## Links

- Method: (cite: mh13) Machida & Hosokawa 2013 (MHD code and protostar evolution method)
- Method: (cite: machida14) Machida et al. 2014 (code details, sink particle and resistivity)
- Companion: (cite: e2-27) Pérez et al. 2016 (ALMA observation of Elias 2-27 being compared)

## Checks

```json
{
 "quotes": 51,
 "quotes_ok": 51,
 "quote_pass_rate": 1.0,
 "quotes_too_long": 0,
 "unsupported_facts": 0,
 "project_codes": 1,
 "codes_not_in_text": [],
 "codes_not_in_obscore": [],
 "obscore_codes_not_in_card": [],
 "codes_printed_but_missing": [],
 "numeric_results": 5,
 "numeric_problems": 0,
 "fill": {
  "facts": 80,
  "stated": 40,
  "rate": 0.5
 },
 "evidence_ok": true
}
```
