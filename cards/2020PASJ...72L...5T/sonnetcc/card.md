# How far actually is the Galactic Center IRS 13E3 from Sagittarius A<SUP>*</SUP>?

`2020PASJ...72L...5T` | Publications of the Astronomical Society of Japan 2020 | first author: Tsuboi, Masato | arXiv: 2002.08508 | DOI: 10.1093/pasj/psaa016

Card schema 1.0 | model claude-sonnet-5-5-claude-code | depth full | type archival_reuse

## Science

- Fields: milky_way_ism, astrochemistry
- Question: Can the line-of-sight (3D) distance of IRS 13E3 from Sgr A* be estimated from the presence of a vibrationally excited CH3OH line in the ionized gas stream, given that CH3OH is destroyed by cosmic rays near Sgr A*?  
  > "Because the abundances of some molecules are considerably affected by the 3D distance, we would attempt to estimate the 3D distance by the spectroscopic informations of the molecules." (Introduction)
- Target **IRS 13E3 / IRS 13E cluster (Galactic Center)**: coordinates _not stated_; z/distance 8.2 kpc (Galactic center); projection distance from Sgr A* ~0.13 pc  
  > "located at $\sim0.13$ pc from Sagittarius A$^\ast$ (Sgr A$^\ast$) in projection distance" (abstract); "Throughout this paper, we adopt 8.2 kpc as the distance to the Galactic center" (Introduction); "(e.g. (cite: Ghez), (cite: Gillessen), (cite: Schodel2009), (cite: Boehle))" (Introduction); distance from adopted from (cite: Ghez), (cite: Gillessen), (cite: Schodel2009), (cite: Boehle)  
  > "located at $\sim0.13$ pc from Sagittarius A$^\ast$ (Sgr A$^\ast$) in projection distance" (abstract); "Throughout this paper, we adopt 8.2 kpc as the distance to the Galactic center" (Introduction); "(e.g. (cite: Ghez), (cite: Gillessen), (cite: Schodel2009), (cite: Boehle))" (Introduction)
- Target **Northern arm (NA) of the Galactic center mini-spiral**: coordinates _not stated_; z/distance 8.2 kpc (Galactic center)  
  > "Figure 2b is the PV diagram in the H30$\alpha$ recombination line along the Northern arm (NA) of the GCMS" (Vibrationally excited CH$_3$OH emission in the Northern arm); "Throughout this paper, we adopt 8.2 kpc as the distance to the Galactic center" (Introduction); distance from adopted from (cite: Ghez), (cite: Gillessen), (cite: Schodel2009), (cite: Boehle)  
  > "Figure 2b is the PV diagram in the H30$\alpha$ recombination line along the Northern arm (NA) of the GCMS" (Vibrationally excited CH$_3$OH emission in the Northern arm); "Throughout this paper, we adopt 8.2 kpc as the distance to the Galactic center" (Introduction)

## Data provenance

- ALMA projects: 2017.1.00503.S
- bands: _not stated_
- frequencies and spectral setup: _not stated_
- continuum bandwidth: _not stated_
- arrays: _not stated_
- configurations: _not stated_
- baselines: _not stated_
- angular resolution: _not stated_
- max recoverable scale: _not stated_
- sensitivity: _not stated_
- time on source: _not stated_
- observing dates: _not stated_
- pi or archival as stated: Published ALMA data of the gas around IRS 13E (H30alpha data detected earlier by the same group); searched for molecular lines in them  
  > "There are several published data with ALMA of the gas associated with the IRS 13 cluster" (Search for the molecular emission line in the gas flows around the IRS 13E cluster); "we had detected the ionized gas associated with IRS 13E3 in the H30$\alpha$ recombination line using ALMA" (Introduction)
- Line: H (recombination line) H30alpha (231900.928 MHz)
- Line: He (recombination line) He30alpha (231995.428 MHz)
- Line: C (recombination line) C30alpha (232016.636 MHz)
- Line: CH3OH (vibrationally excited, v=1) 17(6,11)-17(7,10) (231589.972 MHz)
- External data: Rest frequencies of candidate transitions (NIST table, Li-Hong & Lovas for CH3OH v=1) and line intensities in Sgr B2(N) and Orion MC-1  
  > "https://physics.nist.gov/cgi-bin/micro/table5/start.pl." (Table 1); "(cite: Demyk). $^\ddagger$ (cite: Nummelin). $^\natural$(cite: Li-Hong)." (Table 1) [from NIST; (cite: Demyk); (cite: Nummelin); (cite: Li-Hong)]
- External data: Keplerian orbit parameters of the Northern arm: a ~1 pc, e ~0.8, i ~140 deg  
  > "Assuming the trajectory of the NA is described by a Keplerian orbit with the semi-major axis of $a\sim1$ pc, the eccentricity of $e\sim0.8$, and the inclination angle of $i\sim 140^\circ$ ((cite: Zhao2009))" (Vibrationally excited CH$_3$OH emission in the Northern arm) [from (cite: Zhao2009)]
- External data: Astrometric upper limit mass of an IMBH around Sgr A* (~3e4 Msun at the projection distance, increasing to ~4e4 Msun at larger 3D distance)  
  > "upper limit mass of the IMBH around Sgr A$^{\ast}$ by long-term VLBA astrometry ((cite: Reid), (cite: Hansen))" (Introduction); "the astrometric upper limit mass increases up to $\sim 4\times10^4  M_\odot$ ((cite: Reid), (cite: Hansen))" (Vibrationally excited CH$_3$OH emission in the Northern arm) [from (cite: Reid), (cite: Hansen)]
- External data: Limit radius ~1 pc for CH3OH survival, from the weak CH3OH emission of the innermost CND  
  > "The limit radius is expected to be at least $r\sim 1$ pc from the projection distance of the innermost component of the CND in the CH$_3$OH emission line ((cite: Tsuboi2018))." (Search for the molecular emission line in the gas flows around the IRS 13E cluster) [from (cite: Tsuboi2018)]
- External data: Bar of the mini-spiral on a nearly pole-on high-eccentricity Keplerian orbit; apoastron 3D distance a(1+e) ~0.9 pc  
  > "The "Bar" is thought to obey a nearly pole-on high-eccentricity Keplerian orbit around Sgr A$^{\ast}$ ((cite: Tsuboi2017))" (Search for the molecular emission line in the gas flows around the IRS 13E cluster) [from (cite: Tsuboi2017)]

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

- H30alpha ALMA data and the detection of the ionized gas associated with IRS 13E3 (observation, calibration and imaging not described here)  
  > "we had detected the ionized gas associated with IRS 13E3 in the H30$\alpha$ recombination line using ALMA ((cite: Tsuboi2017b) , (cite: Tsuboi2019))" (Introduction) [from (cite: Tsuboi2017b), (cite: Tsuboi2019)]
- Keplerian orbit of the ionized gas stream used to follow the CH3OH feature  
  > "along the ionized gas stream depicted by a high-eccentricity Keplerian orbit ((cite: Tsuboi2017b))" (Search for the molecular emission line in the gas flows around the IRS 13E cluster) [from (cite: Tsuboi2017b)]
- Enclosed mass of IRS 13E3 compared with the astrometric limit  
  > "The enclosed mass of IRS 13E3 is derived to be $M_{\mathrm{encl.}}\simeq2.4\times10^4 M_\odot$, which agrees with the mass being an IMBH (cite: Tsuboi2019)." (Introduction) [from (cite: Tsuboi2019)]

### Not stated but needed to reproduce (our reading)

- Which ALMA project (2015.1.01080.S or 2017.1.00503.S) supplies each figure, and the band, spectral windows and array configurations
- CASA version, calibration and any self-calibration applied to the H30alpha cube
- Imaging parameters: weighting, robust, cell size, beam, channel width and rms of the cube used for the PV diagrams and channel maps
- Continuum subtraction method and line-free channels
- Exact positions, widths and position angles of the red and black rectangles used for the PV diagrams and line profiles
- Gaussian-fit procedure and fitted parameters for features A to E, and their uncertainties
- How the 3D distance limit was derived: the abstract gives r >~ 0.4 pc while the main text gives r >~ 1 pc for the streamer

## Analysis recipe

1. **Build PV diagram along the IRS 13E3 stream and identify features**: Position-velocity diagram along a rectangle on the H30alpha map, features A to D identified by their velocity pattern  
  > "Figure 1b is the position-velocity (PV) diagram along a red rectangular shown in Figure 1a." (Search for the molecular emission line in the gas flows around the IRS 13E cluster)
   - assumption: Molecular gas physically mixed with the ionized gas shares its PV velocity pattern, so the ionized-gas pattern is a template  
  > "The molecular gas would have a similar velocity feature in the PV diagram to that of the ionized gas if they are physically mixed in the same region." (Search for the molecular emission line in the gas flows around the IRS 13E cluster)
   - fitting: _not stated_
   - validation: _not stated_
2. **Measure line-profile offsets between feature D and the H30alpha feature A**: Extract line profiles over a box and Gaussian-fit the central frequencies; convert the frequency difference to velocity and derive the rest frequency of D  
  > "The frequency difference between the Gaussian-fit central frequencies of the features A and D is about $\Delta \nu \sim 318.7$ MHz." (Search for the molecular emission line in the gas flows around the IRS 13E cluster); "The rest frequency of the feature D is expected to be $\nu_{\mathrm{rest}}= 231582.2$ MHz." (Search for the molecular emission line in the gas flows around the IRS 13E cluster)
   - fitting: Gaussian fits to line profiles (priors and sampler not stated)  
  > "The frequency difference between the Gaussian-fit central frequencies of the features A and D is about $\Delta \nu \sim 318.7$ MHz." (Search for the molecular emission line in the gas flows around the IRS 13E cluster)
   - validation: _not stated_
3. **Identify the carrier of feature D from candidate transitions**: Compare the derived rest frequency with candidate transitions (Table 1) within a velocity tolerance equal to the half width of feature A, then reject candidates whose companion lines are not seen  
  > "the half width of the feature A is used as the tolerance mentioned above." (Search for the molecular emission line in the gas flows around the IRS 13E cluster); "However, there is no sign in Figure 1c. The transition presumably is not the feature D." (Search for the molecular emission line in the gas flows around the IRS 13E cluster)
   - parameter: Velocity tolerance Delta V = +/-25 km/s around V_LSR ~134 km/s  
  > "within $\Delta V=\pm25$ km s$^{-1}$ from the velocity of the feature D, $V_{\mathrm{LSR}}\sim134$ km s$^{-1}$ (see Figure 1c)" (Search for the molecular emission line in the gas flows around the IRS 13E cluster)
   - assumption: Isotopologue lines of the same family and the CH3CHO E and A transitions should have similar intensities in warm dense clouds  
  > "The intensities of these emission lines are observed to be similar in warm and dense molecular clouds" (Search for the molecular emission line in the gas flows around the IRS 13E cluster)
   - fitting: _not stated_
   - validation: Absence of companion lines at the expected velocities rules out CH3(13)CH2CN and CH3CHO; CH3OH v=1 is called most probable  
  > "it is most probable that we detect the vibrationally excited CH$_3$OH emission line as the counterpart of the feature D." (Search for the molecular emission line in the gas flows around the IRS 13E cluster)
4. **Map the CH3OH v=1 feature along the ionized gas stream**: Channel map at V_LSR = 130 km/s (H30alpha reference), width 10 km/s, tracing the feature along the Keplerian stream  
  > "Figure 1d shows the feature D in the channel map of $V_{\mathrm{LSR}}=130$ km s$^{-1}$ referencing to the H30$\alpha$ recombination line" (Search for the molecular emission line in the gas flows around the IRS 13E cluster); "The velocity width is $\Delta V=10$ km s$^{-1}$." (Search for the molecular emission line in the gas flows around the IRS 13E cluster)
   - fitting: _not stated_
   - validation: _not stated_
5. **Infer a lower limit on the 3D distance of IRS 13E3 from CH3OH survival**: CH3OH is destroyed by cosmic-ray photodissociation near Sgr A*; detection of CH3OH in the stream implies a minimum 3D radius, using the CND limit radius  
  > "Therefore the detection of the CH$_3$OH emission line in the gas streamer suggests that the streamer is located at the 3D distance of $r\gtrsim1$ pc from Sgr A$^{\ast}$." (Search for the molecular emission line in the gas flows around the IRS 13E cluster)
   - assumption: Cosmic-ray intensity rises strongly toward Sgr A*, so CH3OH cannot survive inside a limit radius  
  > "Because the cosmic ray intensity is thought to increase significantly with approaching to Sgr A$^\ast$, CH$_3$OH molecule does not survive within some limit radius." (Search for the molecular emission line in the gas flows around the IRS 13E cluster)
   - assumption: The gas streamer is physically associated with IRS 13E3  
  > "Because the gas streamer is associated physically with IRS 13E3, IRS 13E3 is also located at a similar 3D distance from Sgr A$^{\ast}$" (Search for the molecular emission line in the gas flows around the IRS 13E cluster)
   - fitting: _not stated_
   - validation: Feature E (CH3OH v=1 counterpart of the Bar, feature C) near the apoastron, a(1+e) ~0.9 pc, is said to be consistent  
  > "The 3D distance is consistent with the detection of the CH$_3$OH $v=1$, 17(6,11)-17(7,10) emission line there." (Search for the molecular emission line in the gas flows around the IRS 13E cluster)
6. **Test the method on the Northern arm and locate the molecular gas front**: PV diagram along the Northern arm; a faint ridge ~400 km/s from the H30alpha ridge is taken as CH3OH v=1; its disappearance point is placed on a Keplerian orbit to obtain the 3D distance  
  > "the 3D distance of the disappearance point (molecular gas front) is estimated to be $r \sim 0.4$ pc (please see figure 2c)" (Vibrationally excited CH$_3$OH emission in the Northern arm)
   - parameter: Keplerian orbit with a ~1 pc, e ~0.8, i ~140 deg  
  > "Assuming the trajectory of the NA is described by a Keplerian orbit with the semi-major axis of $a\sim1$ pc, the eccentricity of $e\sim0.8$, and the inclination angle of $i\sim 140^\circ$ ((cite: Zhao2009))" (Vibrationally excited CH$_3$OH emission in the Northern arm)
   - assumption: The NA trajectory is Keplerian; CH3OH decays gradually while the arm falls toward Sgr A*  
  > "The gradual decay would be why CH$_3$OH molecule is survived up to $r \sim 0.4$ pc." (Vibrationally excited CH$_3$OH emission in the Northern arm)
   - fitting: _not stated_
   - validation: _not stated_

## Software


## Numeric results

| quantity | value | uncertainty | units | step | quote |
|---|---|---|---|---|---|
| Frequency difference between Gaussian-fit centres of features A and D | 318.7 | not stated | MHz | 2 | The frequency difference between the Gaussian-fit central frequencies of the features A and D is about $\Delta \nu \sim 318.7$ MHz. |
| Velocity difference between features A and D | 412.3 | not stated | km/s | 2 | This corresponds to the velocity difference of $\Delta v\sim412.3$ km s$^{-1}$. |
| Inferred rest frequency of feature D | 231582.2 | not stated | MHz | 2 | The rest frequency of the feature D is expected to be $\nu_{\mathrm{rest}}= 231582.2$ MHz. |
| V_LSR of feature D | ~134 | not stated | km/s | 3 | from the velocity of the feature D, $V_{\mathrm{LSR}}\sim134$ km s$^{-1}$ (see Figure 1c) |
| FWHM velocity widths of features A and D | 50 and 46 | not stated | km/s | 2 | because features A and D have wide FWHM velocity widths of $\Delta V_{\mathrm{FWHM}}=50$ and $46$ km s$^{-1}$, respectively |
| Frequency difference between features C and E | 308.9 (velocity difference 398.9) | not stated | MHz (km/s) | 5 | the frequency difference between the Gaussian-fit central frequencies of the features C and E is about $\Delta \nu \sim 308.9$ MHz or the velocity difference is $\Delta V\sim398.9$ km s$^{-1}$ |
| 3D distance lower limit of the IRS 13E3 gas streamer from Sgr A* (main text) | >~1 | not stated | pc | 5 | suggests that the streamer is located at the 3D distance of $r\gtrsim1$ pc from Sgr A$^{\ast}$. |
| 3D distance lower limit of IRS 13E3 from Sgr A* (abstract) | >~0.4 | not stated | pc | 6 | This indicates that IRS 13E3 is located at $r\gtrsim 0.4$ pc from Sgr A$^{\ast}$. |
| Apparent velocity at the CH3OH disappearance point in the Northern arm | ~350 | not stated | km/s | 6 | The apparent velocity at the disappearance point is $V_\mathrm{LSR} \sim 350$ km s$^{-1}$. |
| Projection distance of the CH3OH disappearance point | ~0.1 | not stated | pc | 6 | $r_{\mathrm{p}} \sim 0.1$ pc, the 3D distance may be larger than the projection distance |
| 3D distance of the Northern arm molecular gas front | ~0.4 | not stated | pc | 6 | the 3D distance of the disappearance point (molecular gas front) is estimated to be $r \sim 0.4$ pc (please see figure 2c) |
| Elapsed time moving from r ~1 pc to r ~0.4 pc along the Northern arm | ~(1-2)x10^3 | not stated | yr | 6 | The elapse time moving from $r \sim 1$ pc to $r \sim 0.4$ pc is $\sim(1-2)\times10^3$ yr. |

## Qualitative findings

- A feature with the same velocity pattern as the H30alpha gas of IRS 13E3 is most probably the first detection of CH3OH v=1 17(6,11)-17(7,10)  
  > "If this is the case, we have the first detection of the CH$_3$OH $v=1$, 17(6,11)-17(7,10) emission line" (Search for the molecular emission line in the gas flows around the IRS 13E cluster)
- A similar CH3OH v=1 ridge appears in the Northern arm and disappears near Sgr A*  
  > "this probably corresponds to the CH$_3$OH $v=1$ emission line." (Vibrationally excited CH$_3$OH emission in the Northern arm)
- Because IRS 13E3 is at larger 3D distance, the astrometric upper limit on an IMBH mass rises, making an IMBH more plausible  
  > "If so, the astrometric upper limit mass becomes larger and increases the possibility that an IMBH exists in the IRS 13E cluster." (Search for the molecular emission line in the gas flows around the IRS 13E cluster)

## Claim tuples

- H: The 3D distance of IRS 13E3 from Sgr A* can be constrained by CH3OH, which cosmic rays destroy near Sgr A* | E: Searched published ALMA H30alpha cubes for a molecular line sharing the PV pattern of the ionized IRS 13E3 stream, and identified candidate transitions | R: Feature D at rest frequency 231582.2 MHz, offset 412.3 km/s from H30alpha, matched to CH3OH v=1 17(6,11)-17(7,10) after rejecting two other candidates | F: CH3OH is present in the IRS 13E3 stream, implying IRS 13E3 lies at 3D distance of at least ~0.4 pc (abstract) or ~1 pc (main text) from Sgr A* | **partially**
- H: CH3OH v=1 also traces the Bar of the mini-spiral, consistent with its larger 3D distance | E: Examined feature E in the line profiles and compared with feature C (Bar, H30alpha) | R: Feature E lies 308.9 MHz (398.9 km/s) from C, presumably CH3OH v=1 at the Bar apoastron (a(1+e) ~0.9 pc) | F: The detection is consistent with the 3D distance at the apoastron | **supported**
- H: The appearance and disappearance of CH3OH v=1 along another GCMS stream (Northern arm) shows the same effect | E: PV diagram of H30alpha along the Northern arm, faint ridge offset ~400 km/s, orbit model from literature | R: CH3OH v=1 ridge disappears at projected r ~0.1 pc, with estimated 3D distance r ~0.4 pc | F: CH3OH survives down to r ~0.4 pc in the Northern arm, supporting IRS 13E3 at r >~0.4 pc | **supported**
- H: The larger 3D distance leaves room for an IMBH in IRS 13E | E: Compared the astrometric upper limit mass at larger distance with the IRS 13E3 enclosed mass from earlier work | R: Upper limit rises to ~4e4 Msun, larger than the earlier enclosed-mass estimate | F: An IMBH in the IRS 13E cluster remains allowed | **supported**

## Reasoning

- Why this data: Published ALMA data of the IRS 13 region were searched, since no molecular gas was found in the easily detected molecules  
  > "First, we searched the sign of the easily found molecules like CO, CS, SiO and so on in the published data." (Search for the molecular emission line in the gas flows around the IRS 13E cluster)
- Why this method: Use the ionized-gas velocity pattern as a template to find molecular emission  
  > "If so, the use of the velocity feature of the ionized gas as a template should be useful to find the sign of the molecular emission from the IRS 13 cluster." (Search for the molecular emission line in the gas flows around the IRS 13E cluster)
- Alternative: CH3(13)CH2CN 26(3,24)-25(3,23) rejected as feature D: companion isotopologue lines expected near V_LSR ~30 and ~50 km/s are not seen  
  > "Therefore, if the feature D is the CH$_3^{13}$CH$_2$CN 26(3,24)-25(3,23) emission line, the other emission lines should be also observed in some degree around $V_{\mathrm{LSR}}\sim30$ and $\sim50$ km s$^{-1}$." (Search for the molecular emission line in the gas flows around the IRS 13E cluster)
- Alternative: CH3CHO 12(3,10)-11(3,9)A rejected as feature D: the E-type line expected near V_LSR ~-80 km/s is not seen  
  > "Therefore, if the feature D is the transition of the CH$_3$CHO molecule, the CH$_3$CHO 12(-3,10)-11(-3,9)E emission line should be also observed in some degree around $V_{\mathrm{LSR}}\sim-80$ km s$^{-1}$." (Search for the molecular emission line in the gas flows around the IRS 13E cluster)
- How they decided it was enough: _not stated_
- Limitation (authors): No molecular gas such as CO, CS or SiO was found in the published data; CH3OH v=1 has not been observed previously, so the identification rests on indirect arguments  
  > "However, we could not find the molecular gas" (Search for the molecular emission line in the gas flows around the IRS 13E cluster); "has not been observed" (Table 1)
- Limitation (authors): The IRS 13E3 distance bound for the Northern arm test is an assumption, not a measurement  
  > "It is assumed here that IRS 13E3 is located at $r \gtrsim 0.4$ pc." (Vibrationally excited CH$_3$OH emission in the Northern arm)
- Caveat (inferred, ours): The line is identified from a single frequency offset with no second CH3OH v=1 transition or rotation-diagram check, so a blend or unlisted species (feature D) cannot be excluded.
- Caveat (inferred, ours): The abstract limit (r >~ 0.4 pc) differs from the main-text limit (r >~ 1 pc) with no reconciliation.
- Caveat (inferred, ours): The CH3OH destruction radius is inferred from CND emission and is not modelled for a streamer on an eccentric orbit.
- Caveat (inferred, ours): No uncertainties are given on the fitted frequencies, velocities or distances.
- Caveat (inferred, ours): Observational parameters (bands, beams, sensitivity, calibration) are not given, so detection significance cannot be judged.

## Reproducibility

- Data public (paper): ALMA project codes cited in the acknowledgements; archive availability is not stated explicitly  
  > "This paper makes use of the following ALMA data: ADS/JAO.ALMA#2015.1. 01080.S and ALMA#2017.1.00503.S." (Acknowledgements)
- Products in archive: _not stated_
- Missing: Observation, calibration and imaging recipe for the H30alpha cubes (deferred to earlier Tsuboi papers)
- Missing: Coordinates, widths and orientation of the PV and line-profile extraction regions
- Missing: Gaussian-fit procedure and uncertainties
- Missing: Procedure for the orbit-based 3D distance estimate (Figure 2c) beyond the quoted orbital elements
- Data volume (inferred): Likely tens to a few hundred GB for two ALMA projects before imaging; not stated in the paper
- Score (inferred): 2/5, Project codes are given and the frequency-offset arithmetic is simple, but no observing, calibration or imaging details, no fit uncertainties and no extraction regions are published.
- Rediscovery candidate: no, The recipe lacks processing and region details, results are few and uncertainty-free, and the line identification is qualitative.

## Links

- Method: (cite: Tsuboi2017b) (Original ALMA H30alpha detection of the IRS 13E3 ionized gas stream and its Keplerian orbit)
- Method: (cite: Tsuboi2019) (H30alpha ring around IRS 13E3 and the enclosed mass of ~2e4 Msun)
- Companion: (cite: Tsuboi2018) (CH3OH emission of the circum-nuclear disk, used for the cosmic-ray destruction limit radius)
- Companion: (cite: Tsuboi2017) (Keplerian orbit of the Bar of the mini-spiral)

## Checks

```json
{
 "quotes": 77,
 "quotes_ok": 77,
 "quote_pass_rate": 1.0,
 "quotes_too_long": 0,
 "unsupported_facts": 0,
 "project_codes": 1,
 "codes_not_in_text": [],
 "codes_not_in_obscore": [],
 "obscore_codes_not_in_card": [
  "2015.1.01080.S"
 ],
 "codes_printed_but_missing": [],
 "numeric_results": 12,
 "numeric_problems": 0,
 "fill": {
  "facts": 86,
  "stated": 40,
  "rate": 0.465
 },
 "evidence_ok": true
}
```
