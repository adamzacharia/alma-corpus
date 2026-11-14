# The ALMA Survey of Gas Evolution of PROtoplanetary Disks (AGE-PRO). VII. Testing Accretion Mechanisms from Disk Population Synthesis

`2025ApJ...989....7T` | The Astrophysical Journal 2025 | first author: Tabone, Benoît | arXiv: 2506.10742 | DOI: 10.3847/1538-4357/adc7b1

Card schema 1.0 | model claude-sonnet-5-5-claude-code | depth light | type theory_or_simulation_compared_to_alma

## Science

- Fields: protoplanetary_disks
- Question: Which disk evolution scenario (turbulence-driven accretion with photoevaporative winds, or MHD disk-wind-driven accretion) reproduces the AGE-PRO disk gas masses and CO sizes together with disk fractions and accretion rates?  
  > "we develop a population synthesis approach to interpret the AGE-PRO measurements of disk gas mass and size considering two scenarios" (abstract)
- Target **AGE-PRO Ophiuchus sample (young population, taken as t=0)**: coordinates _not stated_; z/distance _not stated_; distance from _not stated_
- Target **AGE-PRO Lupus sample (median age 2 Myr)**: coordinates _not stated_; z/distance _not stated_; distance from _not stated_
- Target **AGE-PRO Upper Sco sample (median age 4 Myr)**: coordinates _not stated_; z/distance _not stated_; distance from _not stated_

## Data provenance

- ALMA projects: _none stated_
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
- pi or archival as stated: ALMA large program AGE-PRO; the paper uses derived gas masses and CO sizes from companion AGE-PRO papers, not visibilities  
  > "Today, the ALMA large program AGE-PRO" (Introduction); "The distribution of disk size and mass obtained by the AGE-PRO program is also represented in Figure" (2.3.1 Observational data)
- Line: N2H+ not stated (not stated)
- Line: CO isotopologues not stated (not stated)
- Other facility **ALMA**: AGE-PRO disk gas masses (from N2H+ and CO line fluxes plus CO size) and CO gas sizes used as population constraints  
  > "The disk masses in Lupus and Upper Sco are calculated by matching the N$_2$H$^+$ and CO line fluxes, and CO gas size" (2.3.1 Observational data)
- External data: Disk fraction versus age from an infrared-excess compilation (Fedele et al. 2010), multiplied by 1.2 to match the disk fraction of single or wide binaries from Kraus et al. 2012  
  > "The disk fraction (top left panel) stems from the compilation of" (2.3.1 Observational data); "applying a multiplicative factor of 1.2 to match the disk fraction around single or wide binaries determined by" (2.3.1 Observational data) [from (cite: 2010A&A...510A..72F); (cite: kraus2012)]
- External data: Stellar accretion rates in Lupus and Upper Sco, restricted to the AGE-PRO stellar mass bin 0.3-0.7 Msun; Upper Sco sample has upper limits for half the sources  
  > "We selected the stars that are within the bin of AGE-PRO stellar masses" (2.3.1 Observational data); "reports upper limits for $50\%$ of the sources" (2.3.1 Observational data) [from Lupus: (cite: alcala2014; alcala2017; 2023ASPC..534..539M); Upper Sco: (cite: 2023ApJ...945..112F)]
- External data: AGE-PRO CO gas sizes R_CO,90% (beam-corrected radius enclosing 90% of the CO flux) for Oph, Lupus and Upper Sco  
  > "The observed CO gas sizes, denoted as $R_{CO,90\%}$ or simply $R_{CO}$, correspond to the radius that encompasses 90$\%$ of the total CO flux" (2.3.1 Observational data) [from (cite: AGEPRO_XI_gas_disk_sizes)]
- External data: AGE-PRO disk gas masses for Oph, Lupus and Upper Sco; Ophiuchus median gas mass quoted  
  > "The median gas mass of $<M_D> \simeq 7^{+4}_{-2} \times 10^{-3} M_{\odot}$ obtained by AGE-PRO in Ophiuchus" (3.1.2 Accretion rates) [from (cite: AGEPRO_V_gasmasses); Ophiuchus: (cite: AGEPRO_II_Ophiuchus)]
- External data: Radial profile of the photoevaporative mass-loss rate per unit area, computed for M* = 0.5 Msun, rescaled by a free total mass-loss rate  
  > "we adopt the radial profile of $\dot{\Sigma}_{PEW}(R)$ computed by" (2.2.1 Turbulence-driven evolution) [from (cite: 2021MNRAS.508.3611P)]
- External data: Lognormal error on disk mass of sigma = 0.7 dex  
  > "we take into account a lognormal error on the disk mass of $\sigma=0.7$ dex" (4.2 Origin of the discrepancy with turbulent models) [from (cite: AGEPRO_V_gasmasses)]
- External data: Lognormal error on accretion rate of sigma = 0.3 dex (variability)  
  > "and on the accretion rate of $\sigma=0.3$ dex" (4.2 Origin of the discrepancy with turbulent models) [from (cite: 2014A&A...570A..82V)]
- External data: Carbon depletion delta_C = 0.2 used in the CO-size threshold column density  
  > "Throughout this work we adopt $\delta_C = 0.2$, in line with the under-abundance of CO found in" (2.3.1 Observational data) [from (cite: AGEPRO_V_gasmasses)]
- Simulation/model as data: Synthetic disk populations of 400 disks (gas evolution only) generated with Diskpop for each parameter set  
  > "Throughout this paper, the synthetic populations are made of 400 disks by default and we consider only gas evolution." (2.2 Population synthesis with Diskpop)

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

- Disk gas masses derived from N2H+ and CO line fluxes and CO size (CO isotopologues only for Ophiuchus)  
  > "The disk masses in Lupus and Upper Sco are calculated by matching the N$_2$H$^+$ and CO line fluxes, and CO gas size" (2.3.1 Observational data) [from (cite: AGEPRO_V_gasmasses)]
- Beam-corrected CO gas sizes  
  > "The observed CO gas sizes, denoted as $R_{CO,90\%}$ or simply $R_{CO}$, correspond to the radius that encompasses 90$\%$ of the total CO flux" (2.3.1 Observational data) [from (cite: AGEPRO_XI_gas_disk_sizes)]
- Sample ages and their spread (isochronal ages) for Lupus and Upper Sco  
  > "there is a significant spread in the isochronal ages of each source for the Lupus and Upper Sco AGE-PRO samples with overlap between the two regions" (2.3.1 Observational data) [from (cite: AGE-PRO_I-overview)]
- Analytical solutions for MHD wind-driven disk evolution and the generalized alpha formalism  
  > "In this work, we adopt the analytical solutions of" (2.2.2 MHD wind-driven evolution); "with the generalization proposed by" (2.1 Individual disks) [from (cite: 2022MNRAS.512.2290T)]
- Analytical formula for R_CO,90% from a critical gas column density, with threshold raised by the carbon depletion fraction  
  > "we use a simple analytical formula derived from" (2.3.1 Observational data); "we increased the threshold column density by the carbon depletion fraction" (2.3.1 Observational data) [from (cite: 2023ApJ...954...41T); (cite: 2023MNRAS.518L..69T)]
- Diskpop population synthesis code and Popcorn analysis package  
  > "we use the `Diskpop` python package" (2.2 Population synthesis with Diskpop) [from (cite: 2024arXiv240721101S)]
- Argument for limiting omega to the explored values (too-low omega gives disks with no detectable accretion but significant mass)  
  > "a too-low value of $\omega$ produces disks with no detectable accretion signatures but significant mass" (2.2 Population synthesis with Diskpop) [from (cite: 2022MNRAS.512L..74T)]
- Residual envelope around Ophiuchus sources smaller than disk masses, justifying neglect of early accretion  
  > "Neglecting the impact of early accretion is further justified by the mass of the residual envelope around the Ophiuchus sources being smaller than the disk masses" (2.1 Individual disks) [from (cite: AGEPRO_II_Ophiuchus)]

### Not stated but needed to reproduce (our reading)

- Numerical median values and spreads of disk mass and CO size for Oph, Lupus and Upper Sco (given only graphically in Figure 3, with the per-source AGE-PRO tables in companion papers)
- Diskpop and Popcorn version, radial grid, time grid, random seed and outer-radius settings
- Exact grids of median R0, M0, t_nu,0, omega and f_M explored in each stage, and how the best-fit models were selected from the allowed region
- Numerical median Upper Sco and Ophiuchus accretion rates and the exact Lupus median used besides the stated 1e-9 Msun/yr
- Stellar mass assumed per synthetic disk (0.5 Msun appears only in scalings)
- Data file of the Picogna et al. 2021 photoevaporation profile and the magnetic lever arm value used in each MHD run
- Truncation or clipping of lognormal draws and the definition of the disk fraction from the synthetic sample

## Analysis recipe

1. **Define individual disk evolution models**: 1D vertically integrated disk evolution for two scenarios: turbulence-driven (Shakura-Sunyaev alpha) with photoevaporative wind, and MHD disk-wind with analytical solutions  
  > "The evolution of an individual disk is computed using a 1D formalism, where the MHD equations are integrated in the vertical direction." (2.1 Individual disks)
   - parameter: 4 parameters per disk (M0, R0, generalized alpha, wind mass-loss parameter); MHD model adds omega  
  > "In both scenarios, the evolution of an individual disk is set by 4 parameters" (2.1 Individual disks); "For the MHD disk-wind model, an additional parameter, $\omega$, controls the secular evolution of the magnetic field." (2.1 Individual disks)
   - parameter: Inner disk radius 0.1 au  
  > "we adopt an inner disk radius of 0.1 au" (2.2.1 Turbulence-driven evolution)
   - parameter: Disk dispersed when stellar accretion rate falls below 1e-12 Msun/yr  
  > "a disk is considered to be dispersed when the stellar accretion rate drops below a threshold of $10^{-12}~M_{\odot}/yr$" (2.2.1 Turbulence-driven evolution)
   - parameter: Total photoevaporative mass-loss rate is a free parameter scaling the Picogna et al. 2021 profile  
  > "we take the total mass-loss rate as a free parameter to scale the mass-loss rate profile" (2.2.1 Turbulence-driven evolution)
   - parameter: MHD analytical solution with alpha_SS = 0, constant lambda and constant alpha_DW across the disk  
  > "in the absence of radial transport of angular momentum ($\alpha_{SS} = 0$)" (2.2.2 MHD wind-driven evolution); "The analytical solutions further assume a constant $\lambda$ value in space and time and a constant $\alpha_{DW}$ across the disk." (2.2.2 MHD wind-driven evolution)
   - assumption: T proportional to R^-1/2 and aspect ratio 3.33e-2 (M*/1 Msun)^-1/2 at 1 au  
  > "we assume that $T \propto R^{-1/2}$ and $\epsilon(R=1~\text{au}) = 3.33 \times 10^{-2}~(M_*/1M_{\odot})^{-1/2}$" (2.2.1 Turbulence-driven evolution)
   - assumption: Isolated disks, no envelope or streamer feeding; t=0 is the end of Class I  
  > "We only consider isolated disks that are not fed by any envelope or streamer." (2.1 Individual disks); "The time $t=0$ can therefore be considered as the end of the Class I phase" (2.1 Individual disks)
   - assumption: alpha_SS constant in time and radius; photoevaporative mass-loss rate constant in time  
  > "For simplicity, we assume $\alpha_{SS}$ to be constant in time." (2.2.1 Turbulence-driven evolution); "We further assume that the mass-loss rate is constant over time." (2.2.1 Turbulence-driven evolution)
   - assumption: External UV irradiation neglected  
  > "We further neglect the impact of mild external UV irradiation" (2.1 Individual disks)
   - fitting: _not stated_
   - validation: _not stated_
2. **Build synthetic disk populations**: Diskpop draws disk parameters from user-defined probability distributions and solves each disk's evolution numerically or analytically; output analysed with Popcorn  
  > "As a first step, the code randomly picks the values of the parameters for a sample of disks following a user-defined probability distribution" (2.2 Population synthesis with Diskpop); "The output of `Diskpop` is then analyzed using the `Popcorn` package" (2.2 Population synthesis with Diskpop)
   - software: Diskpop, Popcorn
   - parameter: 400 disks per population by default, gas evolution only  
  > "the synthetic populations are made of 400 disks by default and we consider only gas evolution" (2.2 Population synthesis with Diskpop)
   - parameter: 4 free disk parameters give 8 free population parameters (a median and a spread each); omega takes only two values in the MHD model  
  > "our population model is controlled by 8 free population parameters: a median and a spread for each disk parameter" (2.2 Population synthesis with Diskpop); "The MHD disk-wind model has a fifth free parameter, $\omega$, for which only two values are explored." (2.2 Population synthesis with Diskpop)
   - parameter: Spreads fixed (dex): R0 0.3, M0 0.6, alpha 0.2, wind mass-loss rate 0.3 (turbulent model); omega and lambda constant across the population  
  > "This corresponds to the spread of the lognormal distributions used for synthetic populations and measured in dex." (Table 1); "we keep the 4 spreads fixed to meaningful values provided in Table" (2.3.2 Fitting procedure)
   - assumption: The 4 disk parameters are uncorrelated and lognormally distributed  
  > "We assume that the distributions of the 4 disk parameters are not correlated and follow a log-normal distribution." (2.2 Population synthesis with Diskpop)
   - fitting: _not stated_
   - validation: _not stated_
3. **Assemble observational constraints**: Disk fraction fitted with an error function as a lognormal lifetime distribution; median accretion rates from literature compilations; AGE-PRO CO sizes and gas masses from companion papers; model R_CO,90% from a critical gas column density  
  > "By assuming that disk lifetimes follow a lognormal distribution, we fit the disk fraction by an error function" (2.3.1 Observational data); "Therefore, by finding the radius where the column density reaches $N_{gas}(R_{CO,90\%})$, we determine for each simulated disk the $R_{CO,90\%}$ radius." (2.3.1 Observational data)
   - parameter: Median disk lifetime 3 Myr with spread 0.3 dex  
  > "We estimate a spread of about 0.3 dex and a median value of the disk lifetime of $3\,$Myr." (2.3.1 Observational data)
   - parameter: Median accretion rate falls by at least a factor of 3 from Lupus to Upper Sco, spread 0.8 dex per region  
  > "Overall, we find that the median accretion rate decreases by a factor of at least 3 from Lupus to Upper Sco with a large spread of $0.8$ dex for each region." (2.3.1 Observational data)
   - parameter: Median ages adopted: Lupus 2 Myr, Upper Sco 4 Myr; Ophiuchus taken as t = 0  
  > "we adopt a median age of 2 Myr for the Lupus and 4 Myr for the Upper Scorpius AGE-PRO sample" (2.3.1 Observational data)
   - assumption: Carbon depletion delta_C = 0.2 in the CO-size threshold column density  
  > "Throughout this work we adopt $\delta_C = 0.2$, in line with the under-abundance of CO found in" (2.3.1 Observational data)
   - assumption: Radiative-transfer CO sizes were avoided as too expensive; an analytical column-density criterion is used instead  
  > "This method is however computationally prohibitive and in this work, we use a simple analytical formula derived from" (2.3.1 Observational data)
   - assumption: Ophiuchus, Lupus and Upper Sco are treated as the same population at different ages  
  > "One of the fundamental assumptions behind our analysis is that the Ophiuchus, Lupus, and Upper Sco populations are representative of the same population at different ages." (4.3.1 Representativeness of the AGE-PRO star-forming regions)
   - fitting: Disk fraction fitted by an error function (lognormal lifetime distribution)  
  > "By assuming that disk lifetimes follow a lognormal distribution, we fit the disk fraction by an error function" (2.3.1 Observational data)
   - validation: Two Upper Sco accretion surveys give similar median accretion rates  
  > "Still, the two studies lead to similar median accretion rates for Upper Sco." (2.3.1 Observational data)
4. **Stage 1: fit disk dispersal (disk fraction)**: Adjust the median wind mass-loss rate (turbulent) or the median alpha_DW / accretion timescale (MHD) so the median dispersal time is 3 Myr; turbulent case by iterating populations  
  > "it is the median mass-loss rate $<\dot{M}_{PEW}>$ that is adjusted for the turbulence-driven scenario" (2.3.2 Fitting procedure); "to fit a median disk dispersal time of 3 Myr, one needs to set the median value of $\alpha_{DW}$ for each value of $R_0$ to" (3.1.1 Disk dispersal)
   - software: Diskpop
   - parameter: Turbulent: rescale mass-loss rate in proportion if the disk fraction at 3 Myr is above or below 50%; converges in 2-4 iterations with 6% tolerance on disk fraction  
  > "If the disk fraction at the age of $3\,$Myr is larger (resp. smaller) than 50$\%$, the mass-loss rate is reduced (resp. increased) in proportion, and a new population is calculated." (3.2.1 Disk dispersal); "Convergence is typically reached after 2-4 iterations with a tolerance on the disk fraction of 6$\%$." (3.2.1 Disk dispersal)
   - assumption: MHD case: dispersal time follows t_disp = 2 t_acc,0 / omega and is lognormal because alpha_DW and R0 are lognormal  
  > "Because $\alpha_{DW}$ and $R_0$ follow log-normal probability distributions, the disk dispersal time will also follow a log-normal distribution" (3.1.1 Disk dispersal)
   - fitting: Iterative adjustment of one parameter (not a sampler); no priors or likelihood  
  > "Compared with e.g., MCMC fits, our step-by-step fitting method" (4.2 Origin of the discrepancy with turbulent models)
   - validation: _not stated_
5. **Stage 2: fit median accretion rate in Lupus**: Adjust the median initial disk mass for each remaining parameter combination until the median accretion rate at 2 Myr matches the Lupus value; turbulent case uses linear interpolation between bracketing populations  
  > "we adjust the median disk mass $<M_0>$ for each value of $\omega$, $f_M$, and $<R_0>$ to match a median accretion rate of $\dot{M}_* = 10^{-9}$ M$_{\odot}$/yr measured in Lupus." (3.1.2 Accretion rates); "We finally compute the value of $<M_0>$ and $<\dot{M}_{PEW}>$ using a linear interpolation." (3.2.2 Accretion rates)
   - software: Diskpop
   - parameter: Tolerance of 10% on the median accretion rate  
  > "A tolerance of $10 \%$ on the median accretion rate is adopted." (3.1.2 Accretion rates)
   - parameter: Median accretion rate measured at an age of 2 Myr  
  > "measure the median accretion rate at an age of $2\,$Myr" (3.1.2 Accretion rates)
   - assumption: Accretion rates scale with initial disk mass  
  > "since accretion rates are proportional to $M_0$" (2.3.2 Fitting procedure)
   - fitting: Increase or decrease M0 according to whether the median accretion rate is above or below target; no sampler  
  > "The initial median disk mass is subsequently increased (resp. decreased) if the median accretion is higher (resp. lower) than $10^{-9}$ M$_{\odot}$/yr." (3.1.2 Accretion rates)
   - validation: Interpolated turbulent populations re-run to check dispersal time of about 3 Myr and median accretion rate of 1e-9 Msun/yr at 2 Myr  
  > "We further check that the populations with the interpolated value of $<M_0>$ and $<\dot{M}_{PEW}>$ does predict a disk dispersal time of about $3\,$Myr" (3.2.2 Accretion rates)
6. **Stages 3 and 4: constrain R0 and the remaining parameter with Lupus CO size and gas mass**: Compare predicted median CO size and median gas mass at 2 Myr with AGE-PRO Lupus values; CO size constrains R0, gas mass constrains viscous timescale (turbulent) or f_M (MHD)  
  > "The third stage (fit of the median CO gas size in Lupus) constrains the initial disk size $R_0$, and the last stage constrains the remaining parameters" (2.3.2 Fitting procedure)
   - software: Diskpop
   - parameter: Order of constraints: disk fraction, Lupus accretion rate, Lupus CO size, Lupus gas mass  
  > "sequentially reproducing (1) the disk fraction (through the disk dispersal timescale), (2) the median accretion rate in Lupus, (3) the median CO gas size inferred in Lupus, and (4) the median gas mass estimated in Lupus." (2.3.2 Fitting procedure)
   - assumption: Lupus is the reference population because all its sources have accretion rates, its age range is narrow, and its CO sizes are measurable  
  > "The middle-aged Lupus population is used to constrain the parameters before a detailed comparison with the old Upper Sco and the young Ophiuchus populations." (2.3.2 Fitting procedure)
   - fitting: Grid exploration with visual selection of the allowed region (best-fit models outlined in figures)  
  > "In the next section, we adopt the three best-fit models highlighted by black points in Fig." (3.2.3 Constraints from AGE-PRO results on Lupus)
   - validation: _not stated_
7. **Compare best-fit populations with Ophiuchus, Lupus and Upper Sco**: Evolve the best-fit synthetic populations and compare the time evolution of median disk mass, accretion rate and CO size with observations in all three regions  
  > "we present the time evolution of the median disk mass $<M_D>$, accretion rate $<\dot{M}_*>$, CO gas size $<R_{CO}>$ and compare them to the available observational constraints." (3.1.5 Best fit MHD disk-wind model)
   - software: Diskpop, Popcorn
   - parameter: Two MHD best-fit models retained (omega = 0.25 and omega = 0.5); three turbulent best-fit models  
  > "Here, we retained two best-fit models from stage 4, which corresponds to $\omega=0.25$ (steep decline) and $\omega=0.5$ (shallow decline)." (3.1.4 Best fit MHD disk-wind model)
   - assumption: Survivorship bias from dispersal is included because medians are taken over surviving disks  
  > "However, in the presence of disk dispersal, the evolution of the properties of a population is not only determined by the evolution of individual disks but also by the properties of the survivors." (4.4 Disk dispersal and the survivorship bias)
   - fitting: _not stated_
   - validation: Alternative ordering of the fit (matching Lupus disk mass in stage 2 instead of accretion rate) used to identify the origin of the turbulent-model discrepancy  
  > "However, the observed Lupus median disk mass can also be matched in stage 2 instead of adjusting for the observed accretion rate." (4.2 Origin of the discrepancy with turbulent models)
8. **Test apparent disk lifetime in the M_D versus Mdot plane**: Plot AGE-PRO sources aged 1-3 Myr in the M_D-Mdot plane against probability density maps of the best-fit populations convolved with lognormal errors, and compare cumulative distributions of M_D/Mdot  
  > "We show in Figure [12](#fig:MD-Macc) the AGE-PRO sources in the $M_D-\dot{M}_*$ plane, focusing on stellar ages between 1 and 3 Myr." (4.2 Origin of the discrepancy with turbulent models)
   - software: Popcorn
   - parameter: Lognormal error 0.7 dex on disk mass and 0.3 dex on accretion rate  
  > "we take into account a lognormal error on the disk mass of $\sigma=0.7$ dex" (4.2 Origin of the discrepancy with turbulent models); "and on the accretion rate of $\sigma=0.3$ dex" (4.2 Origin of the discrepancy with turbulent models)
   - assumption: Uncertainties on disk mass and accretion variability are lognormal  
  > "we take into account a lognormal error on the disk mass of $\sigma=0.7$ dex" (4.2 Origin of the discrepancy with turbulent models)
   - fitting: _not stated_
   - validation: Turbulent result compared with earlier analytic results that M_D/Mdot is longer than or about the disk age  
  > "turbulent-driven evolution leads to $M_D/\dot{M}_*$ longer or about the disk age, regardless of the details of the turbulence-driven model" (4.2 Origin of the discrepancy with turbulent models)

## Software

- **Diskpop** : Generating synthetic disk populations and solving disk evolution  
  > "we use the `Diskpop` python package" (2.2 Population synthesis with Diskpop)
- **Popcorn** : Analysing Diskpop output  
  > "The output of `Diskpop` is then analyzed using the `Popcorn` package" (2.2 Population synthesis with Diskpop)
- **Matplotlib** : Generating all figures  
  > "All figures were generated with the `PYTHON`-based package `MATPLOTLIB`" (Acknowledgment)
- **Astropy** : Named as used in the research  
  > "This research made use of Astropy" (Acknowledgment)

## Numeric results

| quantity | value | uncertainty | units | step | quote |
|---|---|---|---|---|---|
| Median disk lifetime from disk fraction | 3 | not stated | Myr | 3 | We estimate a spread of about 0.3 dex and a median value of the disk lifetime of $3\,$Myr. |
| Spread of disk lifetime | about 0.3 | not stated | dex | 3 | We estimate a spread of about 0.3 dex and a median value of the disk lifetime of $3\,$Myr. |
| Decline of median accretion rate from Lupus to Upper Sco | at least a factor of 3 | not stated | dimensionless | 3 | Overall, we find that the median accretion rate decreases by a factor of at least 3 from Lupus to Upper Sco with a large spread of $0.8$ dex for each region. |
| Spread of accretion rate in each region | 0.8 | not stated | dex | 3 | Overall, we find that the median accretion rate decreases by a factor of at least 3 from Lupus to Upper Sco with a large spread of $0.8$ dex for each region. |
| MHD model: minimum initial median disk mass to match Lupus accretion rate | 8e-3 (at least) | not stated | Msun | 5 | Overall, we find that initial median disk masses of at least $<M_0> \simeq 8 \times 10^{-3}~M_{\odot}$ are required to reproduce the median accretion rate measured in Lupus. |
| Turbulent model: initial median disk mass to match Lupus accretion rate for R0 = 10 au and t_nu,0 about 0.2-1.5 Myr | about 1e-2 | not stated | Msun | 5 | an initial median disk mass of about $1 \times 10^{-2}~M_{\odot}$ is required to match the Lupus median accretion rate |
| MHD best-fit population (omega, f_M, R0, alpha_DW) | omega = 0.25-0.5; f_M below about 1; R0 = 10 au; alpha_DW about 5e-4 to 1e-3 | not stated | mixed (au for R0; alpha_DW dimensionless) | 7 | we find best-fit models with an $\omega = 0.25-0.5$, low mass ejection-to-accretion $f_M \lesssim 1$, initially compact disks $<R_0> = 10~$au, and $\alpha_{DW} \simeq 5 \times 10^{-4} - 10^{-3}$. |
| MHD best-fit accretion timescale t_acc,0 | 0.75 | not stated | Myr | 7 | the best-fit accretion timescale of $t_{acc,0} \simeq 0.75~$Myr along with an initial disk size of $<R_0> = 10~$au give an initial value of $\alpha_{DW}=5 \times 10^{-4}$ |
| MHD best-fit initial alpha_DW (Table 2) | 4.6e-4 | not stated | dimensionless | 7 | $4.6 \times 10^{-4}$ |
| MHD best-fit initial disk mass M0 (Table 2) | 7.5e-3 | not stated | Msun | 7 | $7.5 \times 10^{-3}$ $M_{\odot}$ |
| Initial disk magnetization beta_0 of MHD best fit | about 1e5 | depends on unknown B_phi/B_z | dimensionless | 7 | Our constraints translate to $\beta_0 \simeq 10^5$ |
| Turbulent best-fit alpha_SS | 2-4e-4 | not stated | dimensionless | 6 | This results in a relatively well constrained $\alpha_{SS}$ parameter of $\alpha_{SS} = 2-4\times 10^{-4}$. |
| Turbulent best-fit initial radius R0 and viscous timescale t_nu,0 | R0 = 5-20 au; t_nu,0 = 0.4-3 Myr | not stated | au; Myr | 7 | we find that the disks should be initially compact ($R_0 \simeq 5-20~$au) with relatively long viscous timescales of $t_{\nu,0} \simeq 0.4-3\,$Myr |
| Turbulent reference model: M0 (Table 2) | 1.2e-2 | not stated | Msun | 7 | $1.2 \times 10^{-2}~M_{\odot}$ |
| Turbulent reference model: alpha_SS (Table 2) | 3.4e-4 | not stated | dimensionless | 7 | $3.4 \times 10^{-4}$ |
| Turbulent reference model: photoevaporative mass-loss rate (Table 2) | 4.4e-9 | not stated | Msun/yr | 7 | $4.4 \times 10^{-9}$ M$_{\odot}$/yr |
| Turbulent models fitting CO size: predicted median disk mass at 2 Myr | about 5e-3 | not stated | Msun | 6 | All the models that reproduce the median CO size consistently produce a median disk mass of about $5 \times 10^{-3}~M_{\odot}$ |
| Overestimate of median disk mass at Lupus and Upper Sco by turbulent models | factor 5-10 | not stated | dimensionless | 7 | the median disk mass at the age of Lupus and Upper Scorpius is overestimated by a factor of 5-10 |
| Typical best-fit turbulent photoevaporative mass-loss rate | about 3e-9 to 1e-8 | not stated | Msun/yr | 7 | Our best-fit models have a typical mass-loss rate of $\simeq 3 \times 10^{-9} - 10^{-8}~$M$_{\odot}$/yr |
| Apparent disk lifetime M_D/Mdot in AGE-PRO sample | half the sample below 1 Myr, 2 disks below 0.1 Myr | not stated | Myr | 8 | half of the AGE-PRO sample is below 1 Myr with 2 disks below 0.1 Myr |

## Qualitative findings

- MHD wind-driven models with compact initial disks and a declining magnetic field reproduce disk fraction, accretion rates, gas masses and CO sizes from Ophiuchus to Upper Sco  
  > "MHD wind-driven accretion can reproduce the bulk properties of the disk populations from Ophiuchus to Upper Sco" (abstract)
- Turbulence-driven models fail to reproduce the drop in median disk mass between Ophiuchus and Lupus  
  > "The drop in median disk mass between Ophiuchus and Lupus cannot be reproduced by the turbulence-driven model." (3.2.4 Best fit viscous model with PEW)
- CO size alone is not a decisive test of disk evolution scenarios  
  > "The measurement of CO size alone, even in regions of different age, is not a decisive test for disk evolution scenarios." (4.3.2 Disk gas mass)
- Disk dispersal causes a survivorship bias in median disk properties in both scenarios  
  > "MHD wind-driven evolution also introduces a survivorship bias: compact disks evolve and disperse faster since they have shorter accretion timescales" (4.4 Disk dispersal and the survivorship bias)

## Claim tuples

- H: Can MHD wind-driven accretion reproduce the AGE-PRO disk populations together with disk fraction and accretion rates? | E: Sequentially fit disk fraction and Lupus accretion rate, CO size and gas mass with synthetic populations, then compare with Ophiuchus and Upper Sco | R: Best-fit populations with R0 about 10 au, omega 0.25-0.5 and low f_M match all three regions, omega = 0.5 doing slightly better | F: MHD wind-driven accretion with compact disks and beta about 1e5 matches the bulk properties of the populations | **supported**
- H: Can turbulence-driven accretion with internal photoevaporation reproduce disk fraction and CO sizes? | E: Constrain mass-loss rate, initial mass, size and viscous timescale with disk fraction, Lupus accretion rate and CO size | R: Compact initial disks (R0 5-20 au) with long viscous timescales (0.4-3 Myr) fit disk fraction and gas sizes | F: Turbulence-driven models can reproduce disk fraction and gas sizes but not simultaneously the disk masses | **partially**
- H: Do turbulence-driven models reproduce the observed apparent disk lifetime M_D/Mdot? | E: Compare the M_D-Mdot plane and cumulative distribution of M_D/Mdot for the best-fit populations with the AGE-PRO sources | R: Turbulence-driven populations give M_D/Mdot longer than about the disk age, while half the AGE-PRO sample is below 1 Myr | F: Turbulence-driven models overestimate the apparent disk lifetime; MHD wind-driven models match it | **supported**
- H: Is the tension with turbulence-driven models robust to the AGE-PRO disk mass estimates? | E: Discuss how a systematic underestimate of disk masses would change the fits | R: If masses were underestimated by a factor of five to ten, turbulence-driven models would be compatible with the data | F: The tension depends on the low gas masses, notably of compact disks, which need confirmation | **partially**
- H: Does disk dispersal bias the evolution of median population properties? | E: Track initial properties of surviving disks in best-fit populations | R: Dispersal removes light disks (turbulent) or compact disks (MHD), flattening median mass or raising median CO size | F: Survivorship bias must be included when interpreting survey medians | **supported**

## Reasoning

- Why this data: AGE-PRO gives gas masses independent of dust opacity and gas-to-dust ratio, plus CO sizes corrected for the beam  
  > "The disk mass estimates are therefore not hampered by assumptions on dust optical properties and gas-to-dust ratio." (Introduction)
- Why this method: A step-by-step fit was chosen as intuitive, computationally efficient and to reduce degeneracies in an under-constrained problem  
  > "has the advantage of being intuitive and computationally efficient at finding best-fit solutions." (4.2 Origin of the discrepancy with turbulent models); "Here, we propose a rationalized approach to map the parameter space and alleviate the degeneracies in a step-by-step process." (2.2 Population synthesis with Diskpop)
- Alternative: Radiative transfer of the 1D surface density to derive R_CO,90% was rejected as computationally prohibitive in favour of an analytical column-density criterion  
  > "This method is however computationally prohibitive and in this work, we use a simple analytical formula derived from" (2.3.1 Observational data)
- Alternative: Matching the Lupus disk mass in stage 2 instead of the accretion rate was tried to find the origin of the turbulent-model discrepancy  
  > "However, the observed Lupus median disk mass can also be matched in stage 2 instead of adjusting for the observed accretion rate." (4.2 Origin of the discrepancy with turbulent models)
- Alternative: Outside-in dispersal was considered as an explanation of the short apparent lifetimes and rejected  
  > "Therefore outside-in disk dispersal cannot account for the short disk lifetime found by AGE-PRO." (4.2 Origin of the discrepancy with turbulent models)
- How they decided it was enough: Iterations stopped within stated tolerances (10% on accretion rate, 6% on disk fraction)  
  > "A tolerance of $10 \%$ on the median accretion rate is adopted." (3.1.2 Accretion rates); "Convergence is typically reached after 2-4 iterations with a tolerance on the disk fraction of 6$\%$." (3.2.1 Disk dispersal)
- Limitation (authors): Order of fitting matters because no parameter set fits all constraints  
  > "in the absence of a set of parameters that fits all the constraints, the order in which the observations are fitted matters." (4.2 Origin of the discrepancy with turbulent models)
- Limitation (authors): Disk mass is the most uncertain constraint; Ophiuchus and Lupus/Upper Sco masses come from slightly different approaches  
  > "Overall, we find that disk mass is a crucial parameter along with accretion rates but indubitably the most uncertain." (4.3.2 Disk gas mass); "However, we acknowledge that the disk masses in Ophiuchus versus Lupus and Upper Sco are estimated following slightly different approaches" (4.2 Origin of the discrepancy with turbulent models)
- Limitation (authors): Upper Sco median accretion rate is an upper limit because half the sample has upper limits  
  > "Therefore, the median value of the accretion rate should be considered as an upper limit." (2.3.1 Observational data)
- Limitation (authors): External photoevaporation and multiplicity are neglected; Upper Sco is the only old-region reference  
  > "We further neglect the impact of mild external UV irradiation" (2.1 Individual disks); "In our models, we neglect the effect of multiplicity" (2.3.1 Observational data)
- Caveat (inferred, ours): Best-fit parameters come from a manual sequential grid search without uncertainties, so quoted ranges are not confidence intervals and depend on stage order
- Caveat (inferred, ours): Only 30 AGE-PRO disks (about 10 per region) with large mass uncertainties (0.7 dex) constrain the medians
- Caveat (inferred, ours): Fixed spreads and no correlations between parameters are assumed; other choices could change the survivor-biased medians
- Caveat (inferred, ours): Ophiuchus is treated as t=0 although its masses use a different method
- Caveat (inferred, ours): Model R_CO,90% uses an analytical column-density criterion, not radiative transfer
- Caveat (inferred, ours): Photoevaporation profile rests on a single hydrodynamical model; MHD model assumes constant lambda and a parameterized field decline (omega)

## Reproducibility

- Data public (paper): _not stated_
- Products in archive: _not stated_
- Missing: Numerical values of the observed medians, spreads and per-source data used as targets (figure only)
- Missing: Diskpop and Popcorn versions and exact configuration files, grids and random seeds
- Missing: Selection criterion for the best-fit models within the allowed region
- Missing: Photoevaporation mass-loss profile file and fixed lambda values for MHD runs
- Data volume (inferred): Negligible: no ALMA visibilities processed; uses published AGE-PRO derived quantities and model runs of 400 disks per population
- Score (inferred): 3/5, Model equations, fitting stages, tolerances and many numeric results are given and the Diskpop code is cited, but observed target medians appear only in figures and software settings, versions and the best-fit selection rule are not stated.
- Rediscovery candidate: no, The paper states no data release or code release for these fits, the observational targets are only in companion papers or figures, and the best-fit selection is manual.

## Links

- Method: Somigliana et al. 2024 (cite: 2024arXiv240721101S) (Diskpop and Popcorn population synthesis packages)
- Method: Tabone et al. 2022a (cite: 2022MNRAS.512.2290T) (Analytical MHD wind-driven disk evolution solutions and generalized alpha formalism)
- Method: Trapman et al. 2023 (cite: 2023ApJ...954...41T) (Critical column density criterion linking R_CO,90% to disk mass)
- Method: Picogna et al. 2021 (cite: 2021MNRAS.508.3611P) (Photoevaporative mass-loss rate profile)
- Companion: Zhang et al. 2025 (cite: AGEPRO_I_overview) (AGE-PRO program overview and sample ages)
- Companion: Ruiz-Rodriguez et al. 2025 (cite: AGEPRO_II_Ophiuchus) (Ophiuchus AGE-PRO results)
- Companion: Deng et al. 2025 (cite: AGEPRO_III_Lupus) (Lupus AGE-PRO results)
- Companion: Agurto-Gangas et al. 2025 (cite: AGEPRO_IV_UpperSco) (Upper Sco AGE-PRO results)
- Companion: Trapman et al. 2025a (cite: AGEPRO_V_gasmasses) (AGE-PRO disk gas masses)
- Companion: Trapman et al. 2025b (cite: AGEPRO_XI_gas_disk_sizes) (AGE-PRO CO gas disk sizes)
- Companion: Anania 2025 (cite: AGE-PRO_externalPE) (External photoevaporation in the Upper Sco AGE-PRO sample)
- Related: AGE-PRO ALMA large program
- Related: Fang et al. 2023 Upper Sco accretion rates
- Related: Alcala et al. 2014, 2017 and Manara et al. 2023 Lupus accretion compilations

## Checks

```json
{
 "quotes": 134,
 "quotes_ok": 134,
 "quote_pass_rate": 1.0,
 "quotes_too_long": 0,
 "unsupported_facts": 0,
 "project_codes": 0,
 "codes_not_in_text": [],
 "codes_not_in_obscore": [],
 "obscore_codes_not_in_card": [
  "2021.1.00128.L"
 ],
 "codes_printed_but_missing": [],
 "numeric_results": 20,
 "numeric_problems": 0,
 "fill": {
  "facts": 136,
  "stated": 84,
  "rate": 0.618
 },
 "evidence_ok": true
}
```
