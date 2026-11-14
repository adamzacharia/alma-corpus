# Multiwavelength Dust Characterization of the HL Tau Disk and Implications for Planet Formation

`2025ApJ...990..183U` | The Astrophysical Journal 2025 | first author: Ueda, Takahiro | arXiv: 2507.14443 | DOI: 10.3847/1538-4357/adf214

Card schema 1.0 | model claude-sonnet-5-5 | depth full | type observational_alma_primary

## Science

- Fields: protoplanetary_disks
- Question: What are the dust properties (temperature, surface density, maximum grain size, composition, filling factor, size distribution) of the HL Tau disk, and what do they imply for planet formation via pebble accretion?  
  > "In this paper, we investigate the dust properties in the HL Tau disk using the MCMC method to better constrain key parameters and assess their uncertainties." (Introduction)
- Target **HL Tau**: coordinates _not stated_; z/distance 147 pc  
  > "corresponding to a spatial resolution of 7.35 au for the distance of HL Tau (147 pc; (cite: Galli+18))." (Observations); distance from Galli+18  
  > "corresponding to a spatial resolution of 7.35 au for the distance of HL Tau (147 pc; (cite: Galli+18))." (Observations)

## Data provenance

- ALMA projects: 2019.1.00134.S, 2011.0.00015.SV
- bands: 0.45 mm (Band 9), 0.87 (Band 7), 1.3 (Band 6), 2.1 (Band 4), 3.1 (Band 3) and 7.9 mm (VLA Ka+Q)  
  > "$\lambda=0.45$ (ALMA Band 9), 0.87 (Band 7), 1.3 (Band 6), 2.1 (Band 4), 3.1 (Band 3) and 7.9 mm (VLA Ka$+$Q)" (Observations)
- frequencies and spectral setup: _not stated_
- continuum bandwidth: _not stated_
- arrays: _not stated_
- configurations: _not stated_
- baselines: Band 4 short-baseline data down to ~30 m; the original SV data lack baselines below ~170 m  
  > "those original data lack short baselines ($\lesssim170~{\rm m}$)" (Observations)
- angular resolution: common 0.05'' (7.35 au)  
  > "These datasets have a common angular resolution of $0.05\ensuremath{''}$" (Observations)
- max recoverable scale: _not stated_
- sensitivity: _not stated_
- time on source: _not stated_
- observing dates: _not stated_
- pi or archival as stated: Band 4 short baselines archival (PI Ian Stephens); Band 3 and long-baseline Band 4 from ALMA Science Verification; 0.45, 0.87, 1.3, 7.9 mm data from earlier papers  
  > "The 0.45 mm data are originally from (cite: Guerra-Alvarado+24) and the data at 0.87, 1.3 and 7.9 mm are from (cite: Carrasco-Gonzalez+19)." (Observations)
- Other facility **VLA**: 7.9 mm (Ka+Q) intensity profile  
  > "7.9 mm (VLA Ka$+$Q)" (Observations)
- External data: 0.45 mm (Band 9) image data  
  > "The 0.45 mm data are originally from (cite: Guerra-Alvarado+24)" (Observations) [from (cite: Guerra-Alvarado+24)]
- External data: 0.87, 1.3 and 7.9 mm data  
  > "the data at 0.87, 1.3 and 7.9 mm are from (cite: Carrasco-Gonzalez+19)" (Observations) [from (cite: Carrasco-Gonzalez+19)]
- External data: 13C17O-based gas surface density profile (Md=0.2 Msun)  
  > "with $M_{\rm d}=0.2M_{\odot}$ (cite: BI20), $r_{\rm c}=80$ au, $r_{\rm in}=8.8$ au, and $\gamma=0.2$ from fitting of dust continuum emission (cite: Kwon+15)." (4.1 Full fitting) [from (cite: BI20); (cite: Kwon+15)]
- External data: Stellar mass 2.1 Msun  
  > "We adopt $f_{\rm d2g}=0.01$, $Q=1.4$ and $M_{*}=2.1M_{\odot}$ (cite: Yen+19)." (4.1 Full fitting) [from (cite: Yen+19)]

## Processing

### Calibration

- pipeline or manual: ALMA pipeline scripts for flagging, bandpass, gain and flux scaling, followed by manual self-calibration  
  > "The initial flagging of the visibilities and calibrations for the bandpass characteristics, complex gain, and flux scaling are performed using the pipeline scripts provided by ALMA." (Observations)
- casa version: _not stated_
- pipeline version: _not stated_
- archive products used as is: _not stated_
- flux calibrator: _not stated_
- flux scale uncertainty: 10% at 0.45 mm, 5% at 0.87, 1.3 and 7.9 mm, 2.5% at 2.1 and 3.1 mm  
  > "We set $\delta_{\nu}$ as 10% at 0.45 mm, 5% at 0.87, 1.3 and 7.9 mm, and 2.5% at 2.1 and 3.1 mm, following the ALMA and VLA official values." (3.3 Markov Chain Monte Carlo fitting)
- self calibration: Short-baseline: two phase-only rounds (60 s, 30 s) and one phase+amplitude round (inf); concatenated data again: two phase-only and one phase+amp  
  > "two rounds of phase-only calibration and one round of phase and amplitude calibration are applied with solution intervals of 60 s, 30 s and infinity (scan lengths), respectively." (Observations)

### Imaging

- task: tclean  
  > "The calibrated data are imaged by `tclean` with adopting Briggs weighting with a robust parameter of $-1.5$." (Observations)
- deconvolver: _not stated_
- weighting robust: Briggs, robust = -1.5 (Band 4 and Band 3)  
  > "The calibrated data are imaged by `tclean` with adopting Briggs weighting with a robust parameter of $-1.5$." (Observations)
- uv taper: _not stated_
- cell size: _not stated_
- image size: _not stated_
- masking: _not stated_
- multiscale scales: _not stated_
- continuum subtraction: _not stated_
- line free channels: _not stated_
- primary beam correction: _not stated_
- array combination: Short- and long-baseline Band 4 data concatenated after phaseshift/fixplanets to align phase centers  
  > "we apply `phaseshift` and `fixplanets` to the datasets before the concatenation to ensure that the both datasets have the same phase center (following (cite: Andrews+18))." (Observations)
- smoothing: imsmooth to common 0.05''x0.05'' beam area (Band 3: 0.061''x0.041'')  
  > "The image is smoothed using `imsmooth` to achieve a beam size of 0.061$''$$\times$0.041$''$, resulting in a beam area equivalent to 0.05$''$$\times$0.05$''$." (Observations)
- final beam: Band 4 native beam 0.044''x0.036''; Band 3 native 0.06''x0.035''; smoothed to 0.05'' equivalent  
  > "The obtained image has the FWHM beam size of 0.044$''$$\times$0.036$''$." (Observations)
- final rms: _not stated_

### Inherited from earlier work

- Phase-center alignment of concatenated datasets with phaseshift and fixplanets  
  > "to ensure that the both datasets have the same phase center (following (cite: Andrews+18))." (Observations) [from (cite: Andrews+18)]
- Dust composition model based on DSHARP  
  > "Our dust composition model is based on the DSHARP model (cite: Birnstiel+18)" (2.2 Opacities) [from (cite: Birnstiel+18)]
- Intensity model with scattering  
  > "and is described as (e.g., (cite: Sierra+24))" (3.1 Analytical model of the intensities) [from (cite: Sierra+24)]
- Band 3 data calibrated in the ALMA Science Verification program  
  > "we use the data taken and calibrated in the ALMA Science Verification program (cite: ALMAPartnership15)." (Observations) [from (cite: ALMAPartnership15)]

### Not stated but needed to reproduce (our reading)

- CASA version and pipeline version
- Imaging details: cell size, image size, deconvolver, masking, niter/threshold
- Azimuthal averaging details: deprojection geometry (inclination, PA), radial bin width, radial range fitted
- Exact reprocessing steps for the 0.45, 0.87, 1.3 and 7.9 mm images
- Dust material density and optical constants details per material (partly cited only)
- Details of the pebble accretion calculation setup (seed planet radial locations)
- Treatment of the Stokes number and gas profile at the gaps

## Analysis recipe

1. **Reduce and combine Band 4 data; image Band 4 and Band 3**: Calibrate short-baseline archival data, self-calibrate, concatenate with long-baseline data, image with tclean and smooth to common beam  
  > "The calibrated short-baseline data is concatenated with the long-baseline data which is self-calibrated by using the pipeline scripts provided by ALMA." (Observations)
   - software: CASA, tclean, imsmooth
   - parameter: Briggs robust = -1.5, common beam 0.05''  
  > "The calibrated data are imaged by `tclean` with adopting Briggs weighting with a robust parameter of $-1.5$." (Observations)
   - fitting: _not stated_
   - validation: Compared concatenated Band 4 with SV-only data; concatenated about twice as bright beyond ~60 au  
  > "Beyond $\sim60$ au, the concatenated data are about twice as bright." (Effect of short-baseline data on the Band 4 image)
2. **Build dust opacities**: Compute opacities and effective albedo with OpTool for DSHARP-based mixture with fraction of amorphous carbon f_AC, filling factor, size-distribution slope, using DHS and Bruggeman mixing  
  > "The irregularity of dust shape is considered by using the distribution of hollow spheres method with $f_{\rm max}=0.8$" (2.2 Opacities)
   - software: OpTool
   - parameter: DHS f_max = 0.8; porosity via vacuum mixed with Bruggeman rule  
  > "The porosity is implemented using vacuum as an additional material, which is mixed with the other materials using the Bruggeman rule." (2.2 Opacities)
   - assumption: Mass fractions: water ice 20%, silicates 33%, troilite 7%, carbonaceous 40%  
  > "a mixture of water ice (20% in mass; (cite: WB08)), astronomical silicates (33%; (cite: Draine03)), troilite (7%; (cite: HS96)) and carbonaceous material (40%)." (2.2 Opacities)
   - fitting: _not stated_
   - validation: _not stated_
3. **MCMC fit of radial intensity profiles at each radius**: Fit six-wavelength azimuthally averaged intensities with analytical scattering model; six free parameters (T, Sigma_d, a_max, f_AC, f_fill, p_d)  
  > "We analyze the observed intensity at each radius to infer the six parameters: dust temperature, surface density, maximum dust size, amorphous carbon fraction, filling factor and power-law of size distribution." (3.3 Markov Chain Monte Carlo fitting)
   - software: emcee
   - parameter: 180 walkers, 9000 steps, 30% burn-in; initial 2700-step run to set starting positions  
  > "The MCMC simulation is performed using 180 walkers and 9000 steps, with the initial 30% of the steps discarded as the burn-in period to ensure convergence." (3.3 Markov Chain Monte Carlo fitting)
   - parameter: Ranges: T 5-200 K, log Sigma_d -4 to 1.5, log a_max -2 to 3 mm, f_AC 0-1, log f_fill -2 to 0, p_d 2.5-4  
  > "$T$ between 5 and 200 K, $\log{\Sigma_{\rm d}}$ \[${\rm g~cm^{-2}}$\] between $-4$ and $1.5$" (3.3 Markov Chain Monte Carlo fitting)
   - assumption: Temperature prior from luminosity L*=6 Lsun (sigma 5 Lsun), grazing angle uniform 0.01-0.3; uniform priors otherwise  
  > "The grazing angle $\phi$ is set to be uniformly distributed from 0.01 to 0.3." (3.3 Markov Chain Monte Carlo fitting)
   - assumption: Inclination effect via mu = cos i; flux calibration errors added to sigma  
  > "$\mu\equiv\cos{i}$ represents the effect of the disk inclination" (3.1 Analytical model of the intensities)
   - fitting: Likelihood exp(-chi^2/2) with sigma^2 = standard deviation of azimuthal average^2 + (flux calibration fraction x I)^2  
  > "The posterior probability distributions are calculated using a standard likelihood function" (3.3 Markov Chain Monte Carlo fitting)
   - validation: Model reproduces observed profile within ~1 sigma  
  > "Our model successfully reproduces the observed intensity profile within $\sim1\sigma$ level." (4.1 Full fitting)
4. **Test fixed composition and porosity**: Repeat MCMC with f_AC = 0.3 or 0.8 and f_fill = 0.1 or 0.8  
  > "We set $f_{\rm AC} = 0.3$ or $0.8$ to test the robustness of its radial variation seen in the full fitting." (4.2 Fixing the dust composition and porosity)
   - software: emcee
   - fitting: _not stated_
   - validation: Compared posteriors across fixed cases  
  > "Figure [5](#fig:MCMC_comparison) presents the posterior distributions of four parameters from MCMC fitting with fixed $f_{\rm fill}$ and $f_{\rm AC}$, along with intensity profiles within the 68% confidence interval." (4.2 Fixing the dust composition and porosity)
5. **Add polarization-based prior**: Add prior p2 = 0.5{1+tanh[(P90*omega_eff(345GHz)-0.15)/0.1]} on polarization efficiency and rerun full fit  
  > "we perform the MCMC analysis with an additional prior based on the polarization efficiency at 0.87 mm" (4.3 Scattering Polarization)
   - software: emcee
   - parameter: Polarization degree approx C P90 omega with C ~ 0.02; applied to entire disk  
  > "it can be roughly approximated as $C P_{90} \omega^{\rm eff}_{\nu}$ with $C \sim 0.02$ (cite: Kataoka+16)" (4.3 Scattering Polarization)
   - fitting: Modified prior p1*p2  
  > "the modified prior is given by $p_{1}p_{2}$." (4.3 Scattering Polarization)
   - validation: _not stated_
6. **Derive pebble flux, accretion rate and pebble lifetime**: Compute Stokes number, radial drift, pebble flux 2 pi r v_r Sigma_d, pebble accretion efficiency (Liu & Ormel 2018) for 3 Earth-mass seed from MCMC posteriors  
  > "The radial pebble flux is calculated as" (6.4 Planet formation in the HL Tau disk)
   - parameter: alpha_vert = 1e-4 (also 1e-3 and 1e-5 tested)  
  > "We assume $\alpha_{\rm vert}=10^{-4}$." (6.4 Planet formation in the HL Tau disk)
   - assumption: Smooth gas disk from 13C17O-based profile; dust-to-gas 0.01; rho_m = 1.675 g cm^-3; Q=1.4; M*=2.1 Msun  
  > "where $\rho_{\rm m}=1.675~{\rm g~cm^{-3}}$ is the dust material density." (4.1 Full fitting)
   - fitting: _not stated_
   - validation: Compared to pebble flux estimates in the literature  
  > "These values are consistent with the pebble fluxes of our organics-rich dust model at $>40$ au where the derived dust properties are not significantly affected by high optical thickness." (5.4 Planet formation in the HL Tau disk)

## Software

- **CASA** : Reduction, calibration, concatenation and imaging of Band 4 and Band 3  
  > "The short-baseline data are reduced and calibrated using the Common Astronomical Software Application (`CASA`) package (cite: CASA)." (Observations)
- **OpTool** : Computing dust opacities and albedo  
  > "optical properties of our dust model calculated with `OpTool` (cite: Dominik+21)" (2.2 Opacities)
- **emcee** : MCMC posterior sampling  
  > "using the MCMC implementation within the `emcee` package (cite: Foreman-Mackey+13)" (3.3 Markov Chain Monte Carlo fitting)

## Numeric results

| quantity | value | uncertainty | units | step | quote |
|---|---|---|---|---|---|
| Dust temperature profile (full fit) | T = 55 (r/30 au)^-0.51 | not stated | K | 3 | T=55(r/{\rm 30~au})^{-0.51}~{\rm K} |
| Outer-disk spectral index (>~40 au, lambda>~0.87 mm) | ~3.7 | not stated | dimensionless | 0 | increases to $\sim 3.7$ at $\lambda \gtrsim 0.87$ mm |
| Dust mass within 140 au, f_AC=0.3, f_fill=0.8 | 265 | +11/-9 | M_earth | 4 | The total dust mass within 140 au is $265_{-9}^{+11}$, $547_{-10}^{+10}$, $30_{-1}^{+1}$ and $113_{-3}^{+2}M_{\oplus}$ |
| Dust mass within 140 au, f_AC=0.3, f_fill=0.1 | 547 | +/-10 | M_earth | 4 | $547_{-10}^{+10}$ |
| Dust mass within 140 au, f_AC=0.8, f_fill=0.8 | 30 | +/-1 | M_earth | 4 | $30_{-1}^{+1}$ |
| Dust mass within 140 au, f_AC=0.8, f_fill=0.1 | 113 | +2/-3 | M_earth | 4 | $113_{-3}^{+2}M_{\oplus}$ |
| Preferred filling factor with polarization prior | 0.03 to 0.3 | not stated | dimensionless | 5 | The filling factor is preferred to be in the range $0.03 \lesssim f_{\rm fill} \lesssim 0.3$ |
| Maximum dust size beyond 40 au with polarization prior | ~100 | not stated | micron | 5 | At $r \gtrsim 40$ au, the maximum dust size is likely $\sim100$ ${\rm \mu m}$ |
| Radial pebble flux beyond 40 au (porous organics-rich) | up to 1e3 | not stated | M_earth/Myr | 6 | where it can be as high as $10^{3}M_{\oplus}~{\rm Myr^{-1}}$ |
| Dust temperature relative to Carrasco-Gonzalez+19 | ~36% lower | not stated | percent | 3 | The derived dust temperature is $\sim36$% lower than that derived by (cite: Carrasco-Gonzalez+19) |

## Qualitative findings

- Full fit prefers organics-rich, low filling factor dust beyond ~40 au, but amorphous-carbon-rich dust also reproduces the data  
  > "shows a preference for organics-rich dust with a low filling factor in the outer region ($r \gtrsim 40$ au)" (abstract)
- Gaps appear leaky: no significant decrease in dust flux inside gaps  
  > "no significant decrease in dust flux is observed inside the gaps." (6.4 Planet formation in the HL Tau disk)

## Claim tuples

- H: Can multi-wavelength intensity profiles constrain dust composition, porosity and size without a fixed dust model? | E: Six-parameter MCMC fits at each radius to six-band profiles | R: Organics-rich low-filling-factor dust is preferred beyond 40 au, but amorphous-carbon-rich compact dust also fits | F: Dust properties are sensitive to assumed dust model; data alone do not break degeneracies | **partially**
- H: Is compact amorphous-carbon-rich dust consistent with scattering polarization at 0.87 mm? | E: Compare polarization efficiency posterior for fixed models | R: f_fill=0.8, f_AC=0.8 model fails to produce sufficient polarization | F: Moderately porous dust is favored | **supported**
- H: Can pebble accretion form giant planet cores in the HL Tau disk? | E: Pebble flux and accretion rate from posterior for different dust models | R: Porous organics-rich dust gives ~10 M_earth/Myr accretion; amorphous-carbon-rich dust gives too little | F: Pebble accretion viable only for porous organics-rich dust; otherwise gravitational instability may be needed | **supported**
- H: Missing short baselines in earlier Band 4 data biased the dust size | E: Concatenate archival short-baseline data and compare with SV data | R: Concatenated emission twice as bright beyond 60 au | F: Earlier data artificially steepened alpha and favored larger compact grains | **supported**

## Reasoning

- Why this data: HL Tau is bright and extensively observed, an ideal target; new Band 4 short-baseline and Band 3 data fix missing flux  
  > "The protoplanetary disk around HL Tau is among the brightest and most extensively observed disks, making it an ideal target for detailed investigations of dust properties." (Introduction)
- Why this method: _not stated_
- Alternative: Fixed f_AC and f_fill models, and RICCI/DIANA opacity models compared with variable f_AC  
  > "adjusting the amorphous-carbon fraction in the DSHARP model largely reproduces the behavior of both models." (2.2 Opacities)
- How they decided it was enough: _not stated_
- Limitation (authors): Preference for amorphous-carbon-rich dust within 40 au arises partly from priors and high optical depth, not conclusive  
  > "the preference for amorphous-carbon-rich dust arises from prior selection rather than intrinsic composition." (4.1 Full fitting)
- Limitation (authors): Filling factor assumed constant across the size distribution; smooth gas disk assumed  
  > "Although this study assumes that the filling factor is constant across the dust size distribution, filling factor may, in reality, depend on dust size." (5.2 Dust porosity in the HL Tau disk)
- Caveat (inferred, ours): Single polarization prior applied uniformly across radii and based on rough C~0.02 approximation
- Caveat (inferred, ours): Azimuthal averaging with a 1D model ignores substructure asymmetries and optical depth/scattering geometry
- Caveat (inferred, ours): Inner disk results sensitive to high optical depth and prior choice
- Caveat (inferred, ours): Pebble accretion results rely on a smooth gas profile and CO-isotopologue-based gas mass

## Reproducibility

- Data public (paper): Band 4 short-baseline data from ALMA archive 2019.1.00134.S; SV data public  
  > "we use the short-baseline data from the ALMA archive (ID: 2019.1.00134.S, PI: Ian Stephens)" (Observations)
- Products in archive: _not stated_
- Missing: Reduced images at 0.45, 0.87, 1.3, 7.9 mm from earlier papers
- Missing: Imaging parameters (cell, size, masks)
- Missing: Radial profile extraction and deprojection geometry
- Missing: MCMC code and opacity tables not released
- Data volume (inferred): ~100-300 GB for the Band 4 and Band 3 raw archival datasets (inferred); other bands from published images
- Score (inferred): 5/5, MCMC recipe is well described with priors and ranges, but several inputs come from earlier papers and imaging/profile extraction details are missing.
- Rediscovery candidate: no, Needs images from multiple earlier papers and unstated extraction details, so the full recipe is not complete.

## Links

- Method: (cite: Birnstiel+18) (DSHARP dust opacity model basis)
- Method: (cite: Sierra+24) (analytical intensity model with scattering)
- Method: (cite: Andrews+18) (data concatenation procedure)
- Companion: (cite: Carrasco-Gonzalez+19) (previous multiwavelength HL Tau analysis and source of data)
- Companion: (cite: Guerra-Alvarado+24) (Band 9 data and prior analysis)
- Related: DSHARP
- Related: ALMA Science Verification HL Tau

## Checks

```json
{
 "quotes": 73,
 "quotes_ok": 73,
 "quote_pass_rate": 1.0,
 "quotes_too_long": 0,
 "unsupported_facts": 0,
 "project_codes": 2,
 "codes_not_in_text": [],
 "codes_not_in_obscore": [],
 "obscore_codes_not_in_card": [],
 "codes_printed_but_missing": [],
 "numeric_results": 10,
 "numeric_problems": 0,
 "fill": {
  "facts": 88,
  "stated": 56,
  "rate": 0.636
 },
 "evidence_ok": true
}
```
