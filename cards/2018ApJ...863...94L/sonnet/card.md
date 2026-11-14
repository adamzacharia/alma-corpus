# ALMA Observations of the Very Young Class 0 Protostellar System HH211-mms: A 30 au Dusty Disk with a Disk Wind Traced by SO?

`2018ApJ...863...94L` | The Astrophysical Journal 2018 | first author: Lee, Chin-Fei | arXiv: 1807.05336 | DOI: 10.3847/1538-4357/aad2da

Card schema 1.0 | model claude-sonnet-5-5 | depth full | type observational_alma_primary

## Science

- Fields: star_formation, protoplanetary_disks
- Question: How early and how small a disk can form around a very young Class 0 protostar (HH 211-mms), and does a rotating SO outflow trace a disk wind?  
  > "we aim to determine how early and how small a disk can form in order to provide stronger constraints on current models of disk formation." (Introduction)
- Target **HH 211-mms**: coordinates RA(J2000)=03h43m56.8054s, Dec=32d00m50.189s (continuum peak)  
  > "which is located at a distance of $\sim$ 235 pc (cite: Hirota2008)" (Introduction); "The disk has an emission peak at the position $\alpha_{(2000)}=3^\mathrm{h} 43^\mathrm{m} 56^\mathrm{s}_{^\textrm{.}} 8054$" (3.1 Disk in Continuum at 350 GHz); z/distance ~235 pc  
  > "which is located at a distance of $\sim$ 235 pc (cite: Hirota2008)" (Introduction); "The disk has an emission peak at the position $\alpha_{(2000)}=3^\mathrm{h} 43^\mathrm{m} 56^\mathrm{s}_{^\textrm{.}} 8054$" (3.1 Disk in Continuum at 350 GHz); distance from Hirota et al. 2008 (VLBI)  
  > "which is located at a distance of $\sim$ 235 pc (cite: Hirota2008)" (Introduction); "The disk has an emission peak at the position $\alpha_{(2000)}=3^\mathrm{h} 43^\mathrm{m} 56^\mathrm{s}_{^\textrm{.}} 8054$" (3.1 Disk in Continuum at 350 GHz)

## Data provenance

- ALMA projects: 2015.1.00024.S
- bands: Band 7 (~350 GHz)  
  > "with ALMA at $\sim$ 350 GHz in Band 7, with one pointing toward the center" (Observations)
- frequencies and spectral setup: 6 spws; 5 line spws at ~0.212 km/s per channel, 1 continuum spw (1875 MHz, centre 357.994 GHz) at ~0.848 km/s  
  > "| 5 | Continuum | 1920 | 357.994 | 1875.000 | 976.562 |" (Table 2)
- continuum bandwidth: _not stated_
- arrays: _not stated_
- configurations: C36-7, 37-41 antennas  
  > "C36-7 array configuration was used with 37-41 antennas." (Observations)
- baselines: 15-7930 m  
  > "The projected baselines are 15-7930 m." (Observations)
- angular resolution: continuum 0.047x0.031 arcsec (robust 0.5), 0.036x0.024 arcsec (robust -0.5); SO 0.064x0.046 arcsec  
  > "Robust weighting factors of 0.5 and $-$0.5 were used for the visibility to generate the continuum maps" (Observations)
- max recoverable scale: ~0.4 arcsec  
  > "The resulting maximum recoverable scale is $\sim$ $0^{\prime\prime}_{^\textrm{.}}4$." (Observations)
- sensitivity: continuum 0.11 and 0.154 mJy/beam; SO ~1.6 mJy/beam at 3 km/s  
  > "we binned the channel maps to have a velocity resolution of 3 km s$^{-1}$ and a noise level of $\sim$ 1.6 mJy beam$^{-1}$" (Observations)
- time on source: ~123 minutes usable  
  > "The total usable time on HH 211-mms is $\sim$ 123 minutes." (Observations)
- observing dates: 2015-12-04, 05 (excluded), 06 (two executions)  
  > "Four executions were carried out in 2015 in Cycle 3, one on December 4, one on December 5, and two on December 6." (Observations)
- pi or archival as stated: _not stated_
- Line: SO N_J=8_9-7_8 (346.528 GHz (spw centre))
- Other facility **VLA**: 36.9 GHz disk flux (and 33 GHz dust flux via literature) used for spectral index  
  > "the disk has been detected by the VLA at 36.9 GHz at a resolution of $\sim$ $0^{\prime\prime}_{^\textrm{.}}07$ with a flux density of $\sim$ 0.855 mJy" (3.1 Disk in Continuum at 350 GHz)
- External data: VLA 36.9 GHz disk flux density ~0.855 mJy  
  > "with a flux density of $\sim$ 0.855 mJy (cite: Tobin2016; Segura-Cox2016)" (3.1 Disk in Continuum at 350 GHz) [from (cite: Tobin2016; Segura-Cox2016)]
- External data: Free-free-corrected dust flux ~0.57 mJy at ~33 GHz  
  > "the flux density of the dust emission corrected for the free-free emission is $\sim$ 0.57 mJy at $\sim$ 33 GHz" (3.1 Disk in Continuum at 350 GHz) [from (cite: Tychoniec2018)]
- External data: Systemic velocity from H13CO+ and jet PA/inclination  
  > "the jet has a position angle of 116.5$^\circ$ and an inclination angle of $\lesssim$ 6$^\circ$ to the plane of the sky" (3 Results) [from (cite: Gueth1999; Lee2009; Jhan2016)]
- External data: SO abundance 2e-6 from jet  
  > "Assuming an SO abundance of $2\times10^{-6}$ as found in the jet (cite: Lee2010)" (3.2 Disk Atmosphere and Rotating Outflow in SO) [from (cite: Lee2010)]
- External data: Disk radius vs protostellar mass compilation  
  > "The growth of Keplerian disk radius from Class 0 to I phase has been studied by (cite: Yen2017)." (4.1 Disk Growth and Magnetic Braking) [from (cite: Yen2017)]

## Processing

### Calibration

- pipeline or manual: CASA used to calibrate; pipeline/manual not stated  
  > "The CASA package was used to calibrate the data." (Observations)
- casa version: _not stated_
- pipeline version: _not stated_
- archive products used as is: _not stated_
- flux calibrator: J0238+1636 (1.11 Jy on 12-04; 0.85 Jy on later dates)  
  > "| 2015-12-04 | J0237+2848, 1.22 Jy | J0238+1636, 1.11 Jy | J0336+3218, 0.51 Jy |" (Table 3)
- flux scale uncertainty: HH 211-mms flux densities consistent within ~10% between dates  
  > "the resulting flux densities of HH 211-mms are consistent to within $\sim$ 10%" (Observations)
- self calibration: _not stated_

### Imaging

- task: _not stated_
- deconvolver: _not stated_
- weighting robust: continuum robust 0.5 and -0.5; SO robust 2  
  > "a robust weighting factor of 2 was used for the visibility to generate the SO maps" (Observations)
- uv taper: 0.25 arcsec taper for comparison map  
  > "using a taper of $0^{\prime\prime}_{^\textrm{.}}25$" (3.1 Disk in Continuum at 350 GHz)
- cell size: _not stated_
- image size: _not stated_
- masking: _not stated_
- multiscale scales: _not stated_
- continuum subtraction: _not stated_
- line free channels: line-free channels combined for continuum (ranges not given)  
  > "Line-free channels were combined to produce the continuum channels." (Observations)
- primary beam correction: _not stated_
- array combination: _not stated_
- smoothing: SO channel maps binned to 3 km/s  
  > "we binned the channel maps to have a velocity resolution of 3 km s$^{-1}$" (Observations)
- final beam: 0.047x0.031 and 0.036x0.024 arcsec continuum; 0.064x0.046 arcsec SO  
  > "$\sim$ $0^{\prime\prime}_{^\textrm{.}}064$$\times$$0^{\prime\prime}_{^\textrm{.}}046$ resolution" (Observations)
- final rms: 0.11 and 0.154 mJy/beam continuum; ~1.6 mJy/beam SO  
  > "with a noise level of 0.11 mJy beam$^{-1}$ (or 0.73 K)" (Observations)

### Inherited from earlier work

- Systemic velocity 9.2 km/s from H13CO+ and jet geometry  
  > "as derived from the optically thin line of H$^{13}$CO$^+$ toward the system (cite: Gueth1999)" (3 Results) [from (cite: Gueth1999)]
- SO excitation temperature ~100 K as in HH 212  
  > "an excitation temperature of $\sim$ 100 K as in HH 212 (cite: Lee2018)" (3.2 Disk Atmosphere and Rotating Outflow in SO) [from (cite: Lee2018)]
- Dust mass opacities  
  > "$\kappa_\nu = 0.1 (\nu/10^{3} \textrm{GHz})^\beta$ cm$^2$ g$^{-1}$ (cite: Beckwith1990)" (3.1 Disk in Continuum at 350 GHz) [from (cite: Beckwith1990); (cite: Ossenkopf1994); (cite: Tychoniec2018)]

### Not stated but needed to reproduce (our reading)

- CASA version and whether pipeline or manual calibration
- Line-free channel ranges for continuum
- Clean parameters: deconvolver, threshold, masks, cell and image size, niter
- Continuum self-calibration, if any
- How the PV cuts (position angle, width, offsets) were made
- Details of the SO column density calculation and partition function
- Method for the Keplerian curves in PV diagrams (inclination, distance) and the emission outline criteria
- How flux error values (e.g. 192±38 mJy) were derived

## Analysis recipe

1. **Calibrate and image continuum and SO**: CASA calibration; continuum from line-free channels at robust 0.5/-0.5; SO at robust 2, binned to 3 km/s  
  > "Line-free channels were combined to produce the continuum channels." (Observations)
   - software: CASA
   - parameter: Robust 0.5, -0.5 (continuum); 2 (SO)  
  > "a robust weighting factor of 2 was used for the visibility to generate the SO maps" (Observations)
   - fitting: _not stated_
   - validation: Excluded the poor-phase-stability 12-05 execution; checked flux consistency across dates (~10%)  
  > "The execution on December 5 was excluded because of its poor phase stability" (Observations)
2. **Measure disk geometry and flux in continuum**: Two-dimensional Gaussian fit and intensity cut along the major axis  
  > "A two-dimensional Gaussian fit to the disk structure indicates that the disk has a major axis at a position angle of 27.6$^\circ$" (3.1 Disk in Continuum at 350 GHz)
   - assumption: Inclination <~6 deg from jet  
  > "an inclination angle of $\lesssim$ 6$^\circ$ to the plane of the sky" (3 Results)
   - fitting: _not stated_
   - validation: Tapered map compared with earlier SMA map  
  > "we made a continuum map with a similar resolution to that in (cite: Lee2009) using a taper of $0^{\prime\prime}_{^\textrm{.}}25$" (3.1 Disk in Continuum at 350 GHz)
3. **Spectral index and disk mass**: Spectral index between 33 GHz dust flux and 350 GHz flux; optically thin mass formula M = D^2 F / (B(T) kappa)  
  > "$$M_\textrm{\scriptsize disk} \sim \frac{D^2 F_\nu}{B_\nu(T_{dust}) \kappa_\nu}$$" (3.1 Disk in Continuum at 350 GHz)
   - parameter: T_dust = 100 K, beta = 1  
  > "thus we assume $T_{dust}=100$ K" (3.1 Disk in Continuum at 350 GHz)
   - assumption: Two mass opacities (Beckwith 1990; Ossenkopf & Henning 1994 via Tychoniec 2018); optically thin so lower limit  
  > "Since the emission is at least partially optically thick, the masses estimated here are only lower limits." (3.1 Disk in Continuum at 350 GHz)
   - fitting: _not stated_
   - validation: Compared with masses from 33 GHz emission  
  > "We can compare the disk masses estimated above with that derived from the emission at 33 GHz" (3.1 Disk in Continuum at 350 GHz)
4. **SO kinematics: protostellar mass and angular momentum**: Channel maps and PV diagrams across the jet axis; Keplerian curves outline the PV outer boundaries; linear/elliptical PV structures give specific angular momentum  
  > "the outer boundaries of the PV structures can be roughly outlined by the magenta curves, which are the Keplerian rotation curves due to a protostellar mass of 50 $M_\textrm{\scriptsize Jup}$" (3.2 Disk Atmosphere and Rotating Outflow in SO)
   - assumption: Inclination 6 deg  
  > "assuming an inclination angle of 6$^\circ$" (3.2 Disk Atmosphere and Rotating Outflow in SO)
   - fitting: _not stated_
   - validation: _not stated_
5. **SO column density and mass of atmosphere plus outflow**: Optically thin LTE column density from mean intensity, converted to H2 using SO abundance  
  > "Assuming an optically thin emission in local thermodynamic equilibrium and an excitation temperature of $\sim$ 100 K" (3.2 Disk Atmosphere and Rotating Outflow in SO)
   - parameter: Tex 100 K, X(SO)=2e-6  
  > "Assuming an SO abundance of $2\times10^{-6}$" (3.2 Disk Atmosphere and Rotating Outflow in SO)
   - fitting: _not stated_
   - validation: _not stated_
6. **Compare disk radius with protostellar mass growth models**: Add HH 211-mms to Yen et al. 2017 plot and compare to R_d ∝ M^3 (Terebey 1984) and R_d ∝ M (Basu 1998) tracks  
  > "Figure [\[fig:diskmass\]](#fig:diskmass) shows their plot after adding our measurement of HH 211-mms" (4.1 Disk Growth and Magnetic Braking)
   - fitting: Model coefficients chosen by eye to bracket data  
  > "two coefficients chosen to roughly bracket the currently available data on late Class 0 and early Class I sources" (4.1 Disk Growth and Magnetic Braking)
   - validation: _not stated_

## Software

- **CASA** : Calibration of the data  
  > "The CASA package was used to calibrate the data." (Observations)

## Numeric results

| quantity | value | uncertainty | units | step | quote |
|---|---|---|---|---|---|
| Disk deconvolved FWHM, major axis | 0.127 arcsec (~30 au) | not stated | arcsec | 2 | deconvolved size (FWHM) of $0^{\prime\prime}_{^\textrm{.}}127$ (or $\sim$ 30 au) along the major axis |
| Disk deconvolved FWHM, minor axis | 0.067 arcsec (~16 au) | not stated | arcsec | 2 | $0^{\prime\prime}_{^\textrm{.}}067$ ($\sim$ 16 au) along the minor axis |
| Disk major axis position angle | 27.6 | not stated | deg | 2 | major axis at a position angle of 27.6$^\circ$ |
| Disk total flux density at 350 GHz | 83 | 16 | mJy | 2 | The disk has a total flux density of $\sim$ 83$\pm16$ mJy |
| Envelope plus disk flux density | 192 | 38 | mJy | 2 | total flux density of $\sim$ 192$\pm38$ mJy |
| Spectral index | 2.11 | 0.2 | dimensionless | 3 | we have $\alpha \sim$ 2.11$\pm0.2$ |
| Disk mass from 350 GHz (two opacities) | 1.8 and 4.6 | not stated | M_Jup | 3 | The resulting disk masses are $\sim
1.8$ $M_\textrm{\scriptsize Jup}$ and $\sim 4.6$ $M_\textrm{\scriptsize Jup}$, respectively. |
| Disk mass from 33 GHz (two opacities) | 14 and 35 | not stated | M_Jup | 3 | the resulting disk masses are $\sim$ 14 $M_\textrm{\scriptsize Jup}$ and 35 $M_\textrm{\scriptsize Jup}$ |
| Protostellar mass | <~50 | upper limit | M_Jup | 4 | suggesting that the central protostar has a mass of $\lesssim$ 50 $M_\textrm{\scriptsize Jup}$ |
| Outflow specific angular momentum | <~20 | upper limit | au km/s | 4 | The specific angular momentum of the outflow is estimated to be $\lesssim$ 20 au km s$^{-1}$ |
| Mean SO column density | 4.4e15 | 0.9e15 | cm^-2 | 5 | the mean SO column density is estimated to be $\sim$ $4.4\pm0.9\times10^{15}$ cm$^{-2}$ |
| Mass of atmosphere plus rotating outflow | 1.3e-3 | not stated | M_Jup | 5 | the total mass in the atmosphere and rotating outflow is $\sim 1.3\times10^{-3}$ $M_\textrm{\scriptsize Jup}$ |
| Disk atmosphere radius in SO | ~0.05 arcsec (12 au) | not stated | arcsec | 4 | with its radius estimated to be $\sim$ $0^{\prime\prime}_{^\textrm{.}}05$ or 12 au, using a 4$\sigma$ detection level |

## Qualitative findings

- Disk is geometrically thick, so mm grains have not settled  
  > "Therefore, the disk is geometrically thick" (3.1 Disk in Continuum at 350 GHz)
- Rotating SO outflow co-rotates with the flattened envelope and may trace a disk wind  
  > "is rotating in the same direction as the flattened envelope, and hence could trace a disk wind carrying away angular momentum from the inner disk" (Abstract)

## Claim tuples

- H: A disk can already exist in a very young Class 0 source | E: Band 7 continuum at up to 0.03 arcsec | R: Disk ~30 au along major axis, near edge-on, perpendicular to jet, intensity jump from ~10 K to ~90 K | F: Dusty disk confirmed; inner Keplerian disk of ~10 au expected | **supported**
- H: Disk radius grows linearly vs as M^3 with protostellar mass | E: Add HH 211-mms to the Yen et al. 2017 disk radius vs mass plot with model tracks | R: Disk radius and mass lie in the region expected for linear growth | F: Favors R_d ∝ M* (Basu 1998) over Terebey 1984 | **supported**
- H: Rotating SO outflow traces a disk wind | E: SO channel maps and PV diagrams | R: Compact bipolar rotating outflow from inner disk surfaces, l<~20 au km/s | F: Could trace a disk wind, but not confirmed | **partially**

## Reasoning

- Why this data: _not stated_
- Why this method: Mass estimated with two opacities, as the actual opacity is uncertain  
  > "The actual opacity of the HH 211 protostellar disk can be in between the two." (3.1 Disk in Continuum at 350 GHz)
- Alternative: Secondary SW peak in earlier SMA map judged an artifact of uv coverage  
  > "the secondary emission peak seen in (cite: Lee2009) is likely an artifact due to limited uv-coverages" (3.1 Disk in Continuum at 350 GHz)
- How they decided it was enough: _not stated_
- Limitation (authors): Disk masses are lower limits since emission is partially optically thick  
  > "the masses estimated here are only lower limits" (3.1 Disk in Continuum at 350 GHz)
- Limitation (authors): Outflow velocity and angular momentum need better sensitivity to confirm  
  > "further observations with a better sensitivity are needed to confirm these values" (4.2 Disk Atmosphere and Disk Wind?)
- Caveat (inferred, ours): Keplerian curves in PV diagrams outlined by eye, so the mass limit is loose
- Caveat (inferred, ours): Disk-growth conclusion rests on a few literature points and hand-chosen model coefficients
- Caveat (inferred, ours): Some Keplerian disk inference rests on an intensity jump, not on kinematics of the disk
- Caveat (inferred, ours): Flux uncertainty and mass dependence on assumed T and opacity are large

## Reproducibility

- Data public (paper): ALMA project code given; acknowledgement cites ADS/JAO.ALMA#2015.1.00024.S  
  > "This paper makes use of the following ALMA data: ADS/JAO.ALMA#2015.1.00024.S." (Acknowledgments)
- Products in archive: _not stated_
- Missing: CASA version and clean parameters
- Missing: Line-free channel selection
- Missing: PV cut definitions and Keplerian curve parameters
- Data volume (inferred): ~100-300 GB raw for four Band 7 executions
- Score (inferred): 3/5, Archive data and key settings (robust, baselines, calibrators) are given, but CASA version, clean settings and kinematic analysis details are missing.
- Rediscovery candidate: yes, Data are from a public ALMA project, and the continuum size, flux and mass results are numeric and mostly reproducible; the SO kinematics are more qualitative.

## Links

- Method: Lee et al. 2017 (cite: Lee2017com) (Analogous HH 212 analysis of disk, SO atmosphere and rotating outflow)
- Companion: (cite: Lee2017disk) (HH 212 Keplerian disk comparison)
- Companion: (cite: Tychoniec2018) (VLA 33 GHz dust flux and mass opacity)
- Related: VLA Nascent Disk and Multiplicity (VANDAM) survey

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
 "obscore_codes_not_in_card": [],
 "codes_printed_but_missing": [],
 "numeric_results": 13,
 "numeric_problems": 0,
 "fill": {
  "facts": 82,
  "stated": 55,
  "rate": 0.671
 },
 "evidence_ok": true
}
```
