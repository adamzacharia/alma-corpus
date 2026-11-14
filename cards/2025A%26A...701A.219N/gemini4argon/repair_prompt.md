# Repair task for a Claude Code subagent

A methods card has evidence quotes that were not found verbatim in the paper. Below are the rules, the paper, and the failing items. Write ONE JSON object, nothing else, of the form {"repairs": [{"path": ..., "found": true|false, "loc": ..., "quote": ...}, ...]} with one entry per item (path unchanged) to:

    C:\Users\adama\alma-corpus\cards\2025A%26A...701A.219N\gemini4argon\repair_reply.txt

Use the Write tool for that file. Copy each quote character for character from the paper text below; a returned quote is checked mechanically and dropped if it is not in the paper. Do not read any other file, do not run commands, and do not change anything else. Reply with one line when done.

---

## Rules

You check evidence quotes for a methods card extracted from an astronomy paper. Some quotes could not be found verbatim in the paper text, and some stated values came without a quote. For each item: find the passage in the paper that supports the value and copy it VERBATIM (same words and order, at most 40 words; LaTeX markup may be dropped) with its loc (section heading, "abstract", "Table N" or "Figure N caption"). If the paper does not support the value, return found = false and leave quote and loc empty. Use only the paper text. Return one entry per item, with the item's path unchanged.

## Paper

<paper>
# The Rosetta Stone project

The physical mechanisms that regulate the collapse of high-mass parsec-scale clumps and allow them to form clusters of new stars, including high-mass stars, represent a crucial aspect of star formation. To investigate these mechanisms, we developed the Rosetta Stone project: an end-to-end (simulations $\Leftrightarrow$ observations) framework that is based on the systematic production of realistic synthetic observations of clump fragmentation and their subsequent comparison with real data. In this work, we compare ALMA 1.3 mm continuum dust emission observations from the Star formation in QUiescent And Luminous Objects (SQUALO) survey with a new set of $24$ radiative magnetohydrodynamical (RMHD) simulations of high-mass clump fragmentation, post-processed using the CASA software to mimic the observing strategy of SQUALO (combining ACA and `12 m` array). The simulations were initialized combining typical values of clump mass (500 and 1000 M$_\odot$) and radius ($\sim0.4$ pc) with two levels of turbulence (Mach number, $\mathcal{M}$, of $7$ and $10$) and three levels of magnetization (normalized mass-to-magnetic-flux ratio, $\mu$, of $\sim3$, $10$, and $100$). Following the clump evolution over time with two initial random seeds projected along three orthogonal directions, we produced a collection of $732$ synthetic fields. On each field, we performed source extraction and photometry using the *Hyper* software, as in the SQUALO project, to quantitatively characterize how the initial conditions of the clump and the environment affect the observed fragmentation properties. The synthetic observations of clump fragmentation at $\sim7000$ AU resolution revealed between $2$ and $14$ fragments per field, indicating a complex fragmentation process. Among the initial conditions of the simulations, magnetic fields have the largest impact on the fragment multiplicity at these scales. In advanced stages of clump evolution, a lower number of fragments is preferentially associated with magnetized clumps. The clump magnetization might also affect the clustering of fragments, favoring more tightly bound distributions when the magnetic field is stronger. Fragments identified at $\sim7000$ AU correspond to individual or multiple sink particles in $\sim 75\%$ of the cases. This result suggests that not all identified fragments are actively forming stars. Both sink particles and fragments accrete mass throughout the whole clump evolution. This evidence favors a scenario in which fragments are not isolated from the environment and is thus consistent with results from the SQUALO survey. Our study demonstrates the importance of synthetic observations in interpreting results from interferometric observations.

# Introduction

Star formation, particularly in high-mass star-forming regions, is a multi-scale process (e.g., (cite: 2019MNRAS.490.3061V), (cite: 2023MNRAS.522.3719L), (cite: 2023ApJ...953...40Y)). It develops within giant molecular clouds and filaments, where the assembly of parsec-scale clumps takes place (e.g., (cite: 2010A&A...518L.100M)), and then progresses through a hierarchy of nested structures on scales as small as $\sim1000$ AU (e.g., (cite: 2019ApJ...886..102S), (cite: 2019ApJ...886...36S), (cite: 2022A&A...662A...8M), (cite: 2023MNRAS.520.2306T), (cite: 2024ApJ...966..171M), (cite: 2024RAA....24b5009L), (cite: 2024ApJS..270....9X), (cite: 2025A&A...696A.151C)).\
A crucial aspect of this process is represented by the physical mechanisms that regulate the collapse of clumps of mass of the order of $\sim 10^3\, \text{M}_\odot$, ultimately leading to the formation of clusters of new stars, including future high-mass stars (e.g., (cite: 2003ARA&A..41...57L), (cite: 2010A&A...518L..95H), (cite: 2018A&A...617A.100B), (cite: 2022A&A...664A..26P)). Observational studies and numerical simulations have been employed to quantify the impact of gravity, turbulence, magnetic fields, and feedback mechanisms - as well as that of the potential interplay of these forces - on clump fragmentation properties. However, results from these works have not been conclusive, encompassing a range of viable star-formation models beyond the long-established dichotomy between the core-fed (e.g., (cite: 2003ApJ...585..850M), (cite: 2014prpl.conf..149T)) and the clump-fed scenarios (e.g., (cite: Bonnell1997; Bonnell2001), (cite: Klessen2000), (cite: 2006MNRAS.370..488B), (cite: Girichidis2011; Girichidis2012), (cite: 2012A&A...543L...3H), (cite: 2019MNRAS.490.3061V), (cite: 2020MNRAS.496.3482P), (cite: 2024arXiv240810406V)).\
The most recent studies involving high-mass star-forming regions exhibit shared evidence favoring a scenario in which fragments are not isolated from the environment. While some works report thermal Jeans fragmentation as the leading star-formation mechanism (e.g., (cite: 2015MNRAS.453.3785P), (cite: 2019ApJ...886..102S), (cite: 2021A&A...649A.113B), (cite: 2024ApJ...966..171M), Schisano et al. (submitted)), others indicate that additional support from turbulence, magnetic pressure, and feedback mechanisms or a continuous mass accretion onto the fragments must be in place during clump collapse (e.g., (cite: 2007prpl.conf...63B), (cite: 2009ApJ...696..268Z), (cite: 2011A&A...528A..72H), (cite: 2011A&A...530A.118P), (cite: 2011ApJ...735...64W), (cite: 2018A&A...615A..94F), (cite: 2023MNRAS.520.2306T), (cite: 2023MNRAS.520.3259X), (cite: 2024MNRAS.530.3445V)). Magnetic regulation, in particular, seems to be crucial in the case of massive clumps that exhibit a few fragments and/or the presence of super-Jeans fragments (e.g., (cite: 2015ApJ...804..141Z), (cite: 2016A&A...591A..19P), (cite: 2022A&A...668A.147H), (cite: 2023ASPC..534..193P)); yet some works have indicated only partial agreement or conflicting evidences (e.g., (cite: 2021ApJ...912..159P), (cite: 2024A&A...682A..81B)).\
Although conflicting pieces of evidence are often due to the diversity of the explored environments, they may also be due to the spatial scales probed in the various works (e.g., (cite: 2021A&A...653A.157L)). Indeed, the relative importance of gravitational energy, magnetic field strength, turbulence, and radiative pressure might vary across scales, leading to scale-dependent fragmentation patterns regulated by the dominant force at the scale under analysis, and across environments (e.g., (cite: 2018A&A...615A..94F), (cite: 2019ApJ...878...10T), (cite: 2022A&A...662A...8M), (cite: 2024ApJ...962..136W)). While defining a universal model for clump fragmentation can be particularly challenging under these circumstances, the comparison between observations and simulations has proven to be a useful tool for constraining star-formation mechanisms, especially when involving synthetic observations (e.g., (cite: 2007ApJ...656..959K), (cite: 2011IAUS..270..511G), (cite: 2014ApJ...784...61O), (cite: 2017ApJS..233....1K), (cite: 2019ApJ...886...36S), (cite: 2023ApJ...950...88J)).\
With a specific focus on viable scenarios of clump fragmentation, (cite: 2020ApJ...900...82P) used synthetic observations to test the core collapse and the competitive accretion models against *Herschel* and Atacama Large Millimeter/submillimeter Array (ALMA) observations. They proposed the inertial-inflow model to describe turbulent fragmentation and its potential connection to the origin of massive stars. (cite: 2018A&A...615A..94F) carried out analogous studies to analyze the impact of the interplay of turbulence and magnetic fields within simulated clumps. Comparing their results with the fragmentation properties of massive clumps observed with ALMA, they suggest that higher levels of turbulence produce more fragments and that higher magnetization favors the formation of filamentary structures. At the same time, works by (cite: 2011A&A...530A.101M), (cite: 2017MNRAS.471.4111H), and (cite: 2023MNRAS.522.3548P), for example, have proven the utility of synthetic observations in evaluating technical aspects concerning real observations. They used synthetic data to quantify the reliability of clump, core, and protostar mass estimates derived from submillimeter and infrared dust emission. (cite: 2014ApJ...783...60M), (cite: 2018A&A...617A.100B), and (cite: 2024A&A...688A..30B) used synthetic observations to further address the difference in sensitivity to the more extended emission related to single-dish and interferometeric observations, including the ability of detecting the smallest structures and the non-negligible impact of large-scale interferometric filtering.\
Despite the advent of synthetic observations have led to significant advancements in how the star-formation process is understood (e.g., (cite: 2018NewAR..82....1H), (cite: 2020SSRv..216...62R)), the majority of works involving synthetic data are still subject to some limitations. In particular, the theoretical setups are typically tuned to mimic a specific environment and/or target source, hindering the chance to perform a broad and self-consistent exploration of the parameter space and therefore failing to capture the variety of real star-forming systems (e.g., (cite: 2007ARA&A..45..565M), (cite: 2012A&ARv..20...55H), (cite: 2016SAAS...43...85K)). The comparison between observations and synthetic data itself represents an issue. Observational features caused by the resolution limit and by spatial filtering, as well as by the presence of background and interferometric noise, are often not well reproduced in the synthetic observations, precluding a one-to-one comparison with available real data. To effectively address the physics governing star-forming sites at the scales probed by the observations, it is therefore necessary to apply a rigorous post-processing routine to the simulations and ensure that these also mimic the observational features (instrumental effects and observational biases) of the dataset they will be compared against.

![](images/RS_flowchart.jpeg)

While several studies in the literature employ post-processing routines that incorporate customized radiative transfer models and observational feature integration, they primarily address either the physics of isolated cores and the disk scales (e.g., (cite: 2007ApJ...665..478K), (cite: 2012A&A...545A..98C), (cite: 2015MNRAS.453L..73D), (cite: 2019MNRAS.487.1248S), (cite: 2022A&A...665A..25C), (cite: 2022FrASS...9.9223M), (cite: 2024A&A...685A..67R), (cite: 2024A&A...684A..36T)) or the large-scale interstellar medium (e.g., (cite: 2014MNRAS.441.1628S), (cite: 2015MNRAS.447.2144D), (cite: 2018MNRAS.475.2383S), (cite: 2019A&A...629A..63J)). A self-consistent and systematic comparison between actual observations and dust continuum emission synthetic observations, which could provide a quantitative characterization of how the initial conditions of clumps and environment affect the observed clump fragmentation properties, is currently missing in this panorama. To address this problem, we developed the Rosetta Stone project[^2]: an end-to-end (simulation $\Leftrightarrow$ observations) framework designed to systematically produce realistic synthetic observations of high-mass clump fragmentation and compare them with real interferometric data.

In the present work, we provide a detailed description of the Rosetta Stone framework. In Section [2](#Sect:Method) we present our method, and we focus on the strategy designed for the production of synthetic observations. In Section [3](#Sect:Results) we report on the physical properties of fragments identified in the synthetic fields. Section [4](#Sect:Analysis) is dedicated to the analysis of the fragmentation properties (fragmentation level, mass accretion onto the fragments, relative distances between the fragments), and the impact of the initial conditions used in the models. In Section [5](#Sect:Discussion) we compare evidence from synthetic observations with both models and actual observations. Finally, in Section [6](#Sect:Conclusions) we draw the most relevant conclusions, and we provide insights into future research directions.

# The Rosetta Stone project

Below, we introduce the Rosetta Stone post-processing pipeline aimed at producing realistic synthetic observations (see Section [2.2](#Sect:Synthetic observations)) starting from the output of radiative magnetohydrodynamical (RMHD) simulations (see Section [2.1](#Sect:Set of simulations)). The pipeline is designed to be flexible and can already be adapted to mimic any continuum survey performed with ALMA, the Very Large Array (VLA), and the Northern Extended Millimetre Array (NOEMA) interferometers. In Fig. [1](#fig:flow_chart), we provide the flowchart of the Rosetta Stone end-to-end framework and its main building blocks, which are, respectively:

i.  The reference observations - Our first case study takes as reference ALMA 1.3 mm continuum dust emission observations from the Star formation in QUiescent And Luminous Objects (SQUALO) survey by (cite: 2023MNRAS.520.2306T). The SQUALO sample consists of $13$ high-mass star-forming regions of the Galaxy at different evolutionary stages, and all have evidence of infall motions at the clump scales.

ii. The suite of RMHD simulations - We rely on a new set of 24 radiative magnetohydrodynamical simulations of high-mass clumps fragmentation produced by means of the RAMSES code by Lebreuilly et al. (hereafter Paper I).

iii. The radiative transfer - Our simulations are post-processed at Spitzer 24 $\mu$m, *Herschel* and ALMA Band 6 wavelengths by means of the RADMC-3D code by Tung et al. (hereafter Paper II).

iv. The synthetic observations - After the radiative transfer, our simulations are post-processed by means of the CASA software ((cite: 2007ASPC..376..127M)) to mimic the SQUALO survey observing strategy (ACA + `12 m` array) and data reduction. In this paper we focus on the systematic production of synthetic observations of continuum dust emission, coherently with the reference observations.

v.  The source extraction and photometry - We identify compact sources and we compute the photometry using the *Hyper* software ((cite: 2015A&A...574A.119T)).

vi. The common method of analysis and the comparison of the real and synthetic datasets - We compare the fragmentation properties recovered from the analysis of the synthetic sources with those obtained from the analysis of ALMA observations in (cite: 2023MNRAS.520.2306T).

vii. The refinement of models and follow-up observations - The comparison of the two datasets allows us to better tune the initial conditions of the models and optimize the observational setup and strategy for follow-up observations.

## Setup: Simulations and radiative transfer

The RMHD simulations of high-mass clump fragmentation have been newly developed within the framework of the Rosetta Stone project and are described in detail in Paper I. Specifically, we rely on a first suite of simulations labeled RS1.0, together with a supplementary collection of models used to explore the effect of different numerical prescriptions and to tune the fiducial setup. The RS1.0 suite is part of a planned series of simulations specifically tailored to investigate the formation of high-mass protoclusters at the sub-parsec scales.\
Our simulations solve the three-dimensional equations for the conservation of gas mass, momentum, total energy, and radiation total energy, as well as the evolution of the magnetic field under the assumption of ideal MHD. In these models, which are computed by means of the adaptive mesh refinement finite-volume code RAMSES ((cite: 2002A&A...385..337T); (cite: 2006A&A...457..371F)), individual forming stars are represented by sink particles ((cite: 2014MNRAS.445.4015B)) that form self-consistently above a threshold of $n_{thre} = 10^9$ cm$^{-3}$.\
Since our ultimate goal is to mimic the observations of real star-forming high-mass clumps in the early phases of their evolution, we simulate the collapse of uniform clouds initialized with values of mass, radius, and temperature chosen in agreement with observations. These values correspond to clump masses of 500 and 1000 M$_\odot$, a radius of $\sim 0.4$ pc (e.g., (cite: 2014MNRAS.443.1555U), (cite: 2017MNRAS.470.3882T), (cite: 2021MNRAS.504.2742E)), and a temperature of 10 K, as suggested by the peak temperature derived for prestellar clumps in the Galaxy (e.g., (cite: 2021MNRAS.504.2742E)). To also reproduce a realistic clump environment, we initialize our models including self-gravity, stellar radiation due to mass accretion onto the sink particles, turbulence, and magnetic fields. In particular, we explore two different initial levels of turbulence quantified by the Mach number: $$\begin{equation}
        \mathcal{M}=\frac{v}{c_s}\,,
    
\end{equation}$$ where $v$ is the gas speed, and $c_s$ is the speed of sound in the medium. According to the results from (cite: 2017MNRAS.470.3882T), we set $\mathcal{M}$ to $7$ and 10, respectively. These values are also supported by the analysis of turbulence in clumps performed by e.g., (cite: 2010A&A...515A..42R), and (cite: 2024A&A...686A.155C).

Given our limited understanding of the magnetic field impact on fragmentation (from observations alone), we explore three potential scenarios: a quasi-hydrodynamical one, a moderately magnetized one, and a more magnetized one. The clump magnetization of each scenario is quantified by the normalized parameter mass-over-flux to critical-mass-over-flux ratio (also known as normalized mass-to-flux ratio): $$\begin{equation}
        \mu = \biggl(\dfrac{M_0}{\phi}\biggr) \bigg{/}\biggl(\dfrac{M}{\phi}\biggr)_c \, ,
    
\end{equation}$$ where $M_0$ corresponds to the mass of the clump, and $(M/\phi)_c=$ $(0.53/\pi)\sqrt{5/G}$ corresponds to the critical mass-to-flux ratio at which the clump is magnetically stabilized against gravitational collapse ((cite: 1976ApJ...210..326M)). The stronger the magnetic field, the lower is $\mu$ for a clump of fixed mass. We set $\mu$ to $\sim3$, 10 and 100, respectively (Paper I). As initial condition, the magnetic field is uniform and oriented along the $z$-axis.

As anticipated above, this first suite of simulations has been developed including feedback in the form of radiation from luminosity accretion. This approach enables us to isolate the individual contributions and focus on the impact of turbulence and magnetic fields on clump fragmentation properties. Moreover, the computational cost savings achieved through this choice of feedback mechanisms allow us to explore a significantly broader range of parameters (Paper I). Outflows and Hii regions are planned to be incorporated in a future set of Rosetta Stone models.

With fixed physical initial conditions, we let each model evolve in time with two different turbulent seeds, $1$ and $2$ respectively, to account for the stochastic fluctuations in the observed fragmentation process. We also test different time-step samplings across the various realizations, resulting in a varying number of saved time steps per realization. A larger collection of time steps is available for the realizations initialized with Seed $2$. Each computational time step is associated with a specific time in years and a sink formation efficiency (SFE) computed as: $$\begin{equation}
\label{eq:SFE}
        \text{SFE} = \frac{M_{sinks}}{(M_{gas} + M_{sinks})}\,,
    
\end{equation}$$ where $M_{sinks}=\sum_{\mathrm{sinks}} M_{\mathrm{sink}}$ and $(M_{gas} + M_{sinks})$ is the initial mass in the simulated box. As showed in Paper II, the SFE is the most reliable parameter for defining the evolutionary stage of the clumps, providing a direct comparison with observational parameters such as $L/M$. To sample an evolution range of $\sim10^5\,$years from the formation of the first sink particle, we stop the calculations at a SFE of $\sim15\%$ and $\sim30\%$ for the *M500* [^3] and *M1000* realizations, respectively (Paper I).

For each time step, three orthogonal projections are analyzed. These are fixed for all realizations, and correspond to actual projections in the sky along the $x$, $y$, and $z$ axes. Since our observational vantage point is fixed in real observations, such a study is of crucial relevance to quantify the impact of the line-of-sight projection effects on the analysis of the clump fragmentation properties. In total, we rely on a set of 24 available combinations of initial conditions (see Table [1](#tab:initial_conditions)), corresponding to a statistically significant sample of 244 data cubes and 732 2D fields. For each data cube, we have access to the density, velocity, and B fields, and to the gas temperature. For this first work, we focus on the 2D information relative to the projected density fields and projected temperatures. The column density maps also contain information about the projected positions of the sink particles as shown in Fig. [2](#fig:postprocessing_sequence) (a).

|                 |                              |
|:---------------:|:----------------------------:|
|    Parameter    | Available initial conditions |
|      Seed       |           \[1, 2\]           |
| $M$ (M$_\odot$) |        \[500, 1000\]         |
|    $R$ (pc)     |          \[0.383\]           |
|      $\mu$      |        \[3, 10, 100\]        |
|  $\mathcal{M}$  |          \[7, 10\]           |
|                 |                              |

: Initial conditions for the RS1.0 simulations.

Table notes: Col. 1: Parameters to be set (top to bottom: turbulent seed, mass, radius, mass-to-flux ratio, and Mach number). Col. 2: Available initial conditions for each parameter.

![](images/postprocessing_sequence_pbcor.png)

Following the philosophy of the Rosetta Stone project, performing a comparison between this set of simulations and our reference observations requires two additional steps from our end-to-end pipeline. These consist in post-processing physical quantities from the simulations into observable radiation and incorporating observational features into the simulated data to generate realistic synthetic observations, respectively. At this stage, we have to choose which set of observations we want to compare our models to. This is fundamental to replicate the emission recovered at a given wavelength, for a simulated field placed at a given heliocentric distance, as if it was observed with a specific facility.\
In this paper, we employ as reference the ALMA 1.3 mm continuum dust emission observations from the SQUALO project by (cite: 2023MNRAS.520.2306T). Clump and fragmentation properties from the SQUALO survey that are useful for the analysis carried out in this paper are reported in Appendix [7](#SQUALO). In particular, we reproduce the observational strategy used to observe the target source HIGALBM24.0116+0.4897 (HG24), on which forthcoming studies from the SQUALO survey are focusing (Jones et al. in prep.). The source is located at a heliocentric distance of 5.2 kpc ((cite: 2021A&A...646A..74M)). At the SQUALO angular resolution of $\sim1.4^{\prime\prime}$, we are therefore able to probe the fragmentation process at $\sim7000$ AU scales. We emphasize that our post-processing pipeline is highly flexible and can be adapted to different surveys. In a forthcoming paper we will adapt our pipeline to reproduce the observing strategy of the ALMAGAL survey ((cite: 2025A&A...696A.149M)) and discuss clump fragmentation at $\sim2000$ AU scales.\
As a first step in the post-processing, we run the previously saved snapshots of our simulations through the radiative transfer code RADMC-3D ((cite: 2012ascl.soft02015D)). This includes the physics of photon emission and absorption, coupled with a ray-tracing approach: as UV photon packages move through the grid they get absorbed by dust and re-emitted in a new direction, with a new wavelength, both derived according to the prescription by (cite: 2001ApJ...554..615B). To initialize the radiative transfer, we make use of the distribution of sink particles in the 3D-space (volume density cube) and the gas temperature cube ought to derive the dust temperature using a thermal Monte Carlo (MC) computation (Paper II). Once the sources of radiation are identified, the total luminosity is divided into photon packages. We refer to Paper II for a detailed description of the radiative transfer method.\
We focus on the radiative post-processed dust continuum emission maps at 1.3 mm as the one displayed in Fig. [2](#fig:postprocessing_sequence) (b). The flux is here computed with the same opacity assumption in use for the reference observation, i.e. $k_{1.3}=0.005\,\mathrm{g}\,\mathrm{cm}^{-2}$ ((cite: 1993A&A...279..577P)), that already includes a gas-to-dust mass ratio of 100. In Paper II, we also post-process the available simulations at Spitzer and Herschel wavelengths (24 $\mu$m and from 70 to 500 $\mu$m, respectively) to derive an estimate of the clump-averaged bolometric luminosity over mass ratio $L/M$, that (cite: 2016ApJ...826L...8M) demonstrated to be a reliable evolutionary parameter. Specifically, Paper II establishes the quantitative relationship between the timing in SFE from the simulations in Paper I and the observational $L/M$ parameter: $$\begin{equation}
        \log(L/M) = 1.20_{-0.02}^{+0.02} \log(\text{SFE}) +3.28_{-0.03}^{+0.03}\,.
    
\end{equation}$$

We use this result in Section [4](#Sect:Analysis) and in Section [5](#Sect:Discussion) to investigate if and how the global evolution of our clumps - as seen through the eyes of an observer - correlates with fragmentation properties. The conversion from a numerical to an observationally-defined metric of clump evolution allows us to compare the fragmentation properties recovered in (cite: 2023MNRAS.520.2306T) with the ones from synthetic clumps.

## Synthetic observations

Actual observations result from the combination of real sky emission with the response of the imaging system, a process that cannot be replicated by the raw simulations. Effects as the smoothing caused by a finite beam size and the filtering of small or large-scale structures caused by interferometric observations, are examples of possible biases that the radiative transfer computation alone does not address. To mimic the features of the SQUALO project ALMA observations, we post-process our data using the CASA software ((cite: 2007ASPC..376..127M)), version 6.5.4.

### Creating synthetic observations with the CASA software: Main challenges

The CASA software allows the creation of ALMA-like datasets starting from a sky model and incorporate both atmospheric and instrumental effects. For a given simulated source, visibilities[^4] can be computed using the `simalma`[^5] task for ideal ALMA interferometer arrays setups. However, during actual observing sessions the configuration of antennas may not match the ideal setup: some antennas might be out of use or poorly calibrated. Together with the elevation of the source, which often does neither reach the zenith, nor its culmination point, this causes the telescope beam to be more elongated than in the ideal case. Additionally, weather conditions might affect the data quality within the required integration time. These factors introduce layers of complexity that must be considered to produce accurate synthetic observations, and can be included by tuning the CASA task `simobserve`[^6].

### Rosetta Stone (SQUALO) pipeline

To address the aforementioned aspects and reproduce the observing conditions in the most accurate way possible, we make use of actual measurement sets and observations reports available for the SQUALO observations. Specifically, the archival data for the 2018.1.00443.S project (ALMA Cycle 6) include a single observing block on the `12 m` array (C43-1 configuration), and five observing blocks on the `7 m` array for the HG24 reference source. We used the observations reports to recover the following:

- The frequency of the central channel: 231.1 GHz, that is the 1.3 mm wavelength used for the radiative transfer;

- The fiducial antenna configurations, made up of $10$ to $12$ antennas for the execution blocks on the `7 m` array, and $47$ antennas for the `12 m` array;

- The time on source, with $\sim470$ s of integration for each block on the `7 m` array, and $\sim360$ s for the `12 m` array;

- The time off source due to calibration necessity, which further splits each observing block into four intervals;

- The observing conditions, with a mean precipitable water vapor (PWV) of $\sim1.8$ and $\sim2.9$ mm computed over the observing blocks in the two different configurations;

- The (average) source elevation, covering a range from $\sim45^\circ$ to $\sim72^\circ$ in the different observing blocks.

Taking into account the details of each execution block, we used the CASA task `simobserve` to create synthetic measurement sets of the 1.3 mm sky models produced in Paper II, including the corresponding $uv$ coverage and visibilities. Then, the joint deconvolution with cleaning and masking was performed interactively with the task `tclean`[^7] with the same pipeline settings that were applied in the imaging of the reference SQUALO source, namely:

- Spectral definition mode: Mfs, to get continuum imaging (Stokes I) with only one output image channel.

- Gridding options: mosaic, to resample visibilities onto a regular $uv$-grid with azimuthally symmetric beams without side lobes.

- Minor cycle algorithm (deconvolver): Multiscale with scales = \[0, 7, 21\], to look for point-like sources and multi-scale (multiples of the beam in pixels, corresponding to the beam and three times the beam) components left in the residual image to add them to the model image.

- Weighting scheme: Briggs with robustness parameter of 0.5. We use a flexible weighting scheme based on the signal-to-noise ratio of the MeasurementSets and on the noise threshold. In (cite: 2023MNRAS.520.2306T) it was possible to independently tune the cleaning noise threshold for the $13$ sources, here the threshold is automatically set according to the source evolutionary stage.

- Type of mask for deconvolution: Auto-multithresh, to automatically use multiple thresholds for deconvolution.

- Cell size: 0.2$^{\prime\prime}$, to sample our 1.29$^{\prime\prime}\times$1.51$^{\prime\prime}$ synthetic beam with $\sim 7$ pixels. With this setup, we reach a linear resolution of $\sim 7000$ AU (or $\sim0.036$ pc) at the reference heliocentric distance of 5.2 kpc.

Cleaned images with and without primary beam (PB) correction, as the ones displayed in Fig. [2](#fig:postprocessing_sequence) (c) and (d) respectively, are produced along with the residual maps and the sources masks. In the PB corrected maps, we recover from 80% to 95% of the flux present in the RADMC-3D projected maps as a function of clump evolution. Specifically, the interferometric filtering of the extended emission has a larger impact toward earlier stages of clump collapse. On the other hand, the flux retrieval is more effective toward advanced stages of clump evolution where most of the emission comes from the compact structures. In Appendix [8](#Sect:consistency_checks), we report on further consistency checks performed on the recovered r.m.s.. In Appendix [9](#Sec:Pipelines comparison), we address the differences between the results obtained with the Rosetta Stone pipeline and those obtained with `simalma`.

## Source extraction and photometry

As for the previous post-processing steps, we want the source extraction and photometry to match that performed on the reference observations as much as possible. This approach further reduces the chance of introducing additional biases when comparing observations to simulations. Therefore, the source extraction is performed by using the extraction code *Hyper*[^8] ((cite: 2015A&A...574A.119T)), which went through a fine-tuning procedure by (cite: 2023MNRAS.520.2306T). *Hyper* has been originally designed to account for a multi-wavelength source identification and photometry of point-like and compact (elliptical) sources in regions (including crowded regions) where there is significant and variable background emission, and it is thus an optimal tool to use on interferometric observations of clusters formation.\
Even though our strategy involves performing the source extraction as on the reference observations, we have also conducted an independent tuning of the software parameters. We have accounted for different detection thresholds, polynomials for background modeling, source sizes and shapes (defined by centroid position, position angle, pixel weighting). In agreement with the settings used in the SQUALO project, we considered as compact sources all identified objects with semi-axes[^9] between one and two times the telescope beam size, having a maximum aspect ratio of 1.5. We modeled the background with polynomials up to the second order, and we performed the peak identification on the PB non-corrected images at three times above the locally estimated r.m.s., to then compute the photometry on the relative PB corrected images, as shown in Fig. [2](#fig:postprocessing_sequence) (d).\
For each map in our sample of 732, we used *Hyper* to estimate the fragment and field parameters. Specifically, we derived the number of identified fragments and the coordinates of their centroids. We also determined the semi-minor and semi-major axes, along with the position angle, to characterize the region where the aperture photometry is performed. Within this same region, we measured the peak of emission, and the integrated flux. Additionally, we assessed the local background level for each fragment and the r.m.s. level characteristic of each field.\
In Section [3](#Sect:Results), Section [4](#Sect:Analysis), and Section [5.1](#Sect:Comparison with numerical models) we report the results from the realizations with turbulent seed $2$, for which we sampled the clump evolution at a higher cadence obtaining a sample of 393 maps. Results from seed $1$ are reported in Appendix [10](#Sect: Seed1 fragmentation properties). In Section [5.2](#Sect:Comparison with observations), we use all the 732 maps to reconstruct the parameter space covered by the whole RS1.0 collection of synthetic observations.

# Results

Based on the criteria provided in Section [2.3](#Sect:Source extraction and photometry), we are able to identify (and visually validate) 2749 fragments across the 393 maps under analysis. In the following, we report on the physical properties of the identified sample, with specific focus on the mass distribution and the associated uncertainties.

## Physical properties of the fragments

The sample of validated fragments is characterized by radii in the range $0.036\leq R_f \leq 0.071$ pc, computed as the geometrical mean of the two FWHMs estimated by *Hyper*. About $65\%$ of these fragments are symmetrical, of the remaining $\sim35\%$, $\sim20\%$ have an aspect ratio between $1$ and $1.25$, while $\sim15\%$ have an aspect ratio between $1.25$ and $1.5$ (the maximum aspect ratio allowed).

The distribution of mass of the fragments was obtained by converting fluxes into masses as follows ((cite: 1983QJRAS..24..267H)): $$\begin{equation}
\label{eq:mass_f}
        M_f=\dfrac{D^2 S_{1.3}}{B_{1.3}(T_f) \kappa_{1.3}}\,,
    
\end{equation}$$ where D is the distance of the reference source, $S_{1.3}$ the integrated flux at 1.3 mm estimated by *Hyper* for each fragment, $B_{1.3}(T_f)$ is the Planck function computed at 1.3 mm at the chosen temperature $T_f$ for the dust envelope of each fragment, and $\kappa_{1.3}$ the dust absorption coefficient at 1.3 mm.

As in (cite: 2023MNRAS.520.2306T), we adopt the single temperature model to derive the mass of the fragments associated with the same parent clump. We first assign a temperature to each clump based on the $L/M$ parameter, and then we compute the mass of the fragments therein. Thanks to the Rosetta Stone framework, we are now able to assign a value of $L/M$ to each individual time step on the basis of the associated SFE (see Section [2](#Sect:Method) and Paper II). The relative mass uncertainties due to the possible error on the temperature estimate is computed via 1000 MC simulations of fragments temperature, which let the temperature vary within fixed ranges. The $L/M$ ranges, the reference temperatures, and the relative temperature ranges are provided in Table [2](#tab:T_limits).

We do not expect the real dust temperature to significantly vary from the adopted one in the initial evolutionary stages. However, according to recent studies (e.g., (cite: 2025A&A...694A..24M), (cite: 2025A&A...696A.151C), Jones et al. in prep.), a larger mismatch between the real temperatures and the ranges indicated in Table [2](#tab:T_limits) is expected in the more evolved stages. In this case, we face an additional limitation: the SQUALO clumps reached a maximum $L/M$ of 107 L$_\odot$/M$_\odot$, and therefore the $L/M$ range from 10 L$_\odot$/M$_\odot$ onward did not require further division into smaller sub-ranges. As a consequence, the reference temperature of 40 K was not conceived to represent clumps with $L/M > 100$ L$_\odot$/M$_\odot$.

Before assessing the clump fragmentation properties, we evaluate how effectively we can detect the faintest objects in each synthetic observation depending on the r.m.s. of the map. As in (cite: 2023MNRAS.520.2306T), we consider the 1$\sigma$ value of the local r.m.s. as a lower limit to the peak emission that can be recovered in each map. Assuming that the 1$\sigma$ value corresponds to the peak flux emitted by a point-like source, we compute the equivalent mass with Eq. [\[eq:mass_f\]](#eq:mass_f). From this procedure, we estimate a point-like source mass sensitivity in the range between $\sim0.02$ and $\sim5.4$ M$_\odot$ across the whole sample. These two-order magnitude span depends on the temperature associated with each clump in a given evolutionary stage (see Table [2](#tab:T_limits)) and on the r.m.s. level characteristic of each map, which variations are characterized in Appendix [8](#Sect:consistency_checks).

![](images/mass_distr_corr.png)

|                       |       |           |
|:---------------------:|:-----:|:---------:|
|         $L/M$         | $T_f$ | $T_{lim}$ |
| (L$_\odot$/M$_\odot$) | \(K\) |   \(K\)   |
|      $L$/$M < 1$      |  20   |  10 - 40  |
|   $1 < L$/$M < 10$    |  30   |  10 - 50  |
|     $L$/$M > 10$      |  40   |  20 - 60  |
|                       |       |           |

: Reference temperatures based on clump $L/M$.

Table notes: Col. 1: $L/M$ ranges taken from (cite: 2016ApJ...826L...8M). Col. 2: Reference temperature of the dust envelope used to estimate the fragments mass. Col. 3: Range of temperatures used in the MC simulations to estimate the mass uncertainties.

Using the single temperature assumption and Eq. [\[eq:mass_f\]](#eq:mass_f), we obtain a mass estimate for each of the 2749 identified fragments. The overall sample spans a range between $\sim0.02$ and $\sim1010$ M$_\odot$, as displayed in Fig. [3](#fig:mass_distr). For the *M500* realizations, the range of mass covers structures from $\sim0.02$ to $\sim314$ M$_\odot$. For the *M1000* realizations the range in mass is wider, from $\sim0.02$ to $\sim1010$ M$_\odot$. We address this unrealistically high value in Section [3.2.1](#Sec:Temperature consistency) attributing it to the uncertainties on the clump temperatures and in Section [3.2.2](#Sect: mass recovery) where we also compare synthetically observed masses with the values obtained from the RAMSES column density maps.

For each mass distribution we compute the median value, which corresponds to $\sim4$ and $\sim11$ M$_\odot$, respectively. Taking into account the span in mass, and the median value of mass of each sample, we find that the initial reservoir has a role in the mass distribution of the object we recover: the most massive fragments are preferentially observed in the most massive clumps. The SQUALO distribution, ranging from 0.4 and 309 M$_\odot$, falls exactly within the range spanned by both *M500* and *M1000*, as expected. The minimum mass in the SQUALO distribution is one order of magnitude larger than the minimum of the synthetic distribution. This can be a consequence of the range in mass sensitivity associated with the SQUALO sample, from 0.11 to 4.74 M$_\odot$. While the synthetic clumps are all located at the same distance from the observer, SQUALO clumps are distributed across $13$ different distances, resulting in observations at varying resolutions. We acknowledge that variations in clump distances are expected to introduce a slight bias on mass recovery.\
We test the robustness of the results on the mass distribution using 1000 MC runs in which a random temperature in the ranges presented in Table [2](#tab:T_limits) is assigned to each fragment. Following this strategy, the ranges of mass are updated: between $\sim0.01$ and $\sim724$ M$_\odot$, and between $\sim0.01$ and $\sim2338$ M$_\odot$, for the *M500* and *M1000* realizations, respectively. Despite fluctuations in the mass range, the median values of the distributions remain stable. The current analysis demonstrates the importance of providing an accurate temperature estimate for our fragments in order to derive reliable mass measurements. For a more detailed discussion on the impact of temperature uncertainties on the mass estimation of our fragments, we refer to the following section.

## Temperature uncertainties

Uncertainties on the temperatures of the dust envelope of the fragments - necessary to derive masses from both reference and synthetic observations - contribute significantly to the uncertainties associated with fragment mass estimates. The MC runs allow us to test the assumption of multiple temperatures for multiple fragments within the same parent clump. However, MC simulations are conducted on individual fields, without considering that we are observing subsequent time steps in the evolution of the same clumps. This approach hampers our ability to track potential temperature trends throughout the clump evolution. In the case of synthetic observations, we can address these limitations using the projected temperature maps from the simulations.

### Temperature consistency evaluation

![](images/ramses_temperature_mass_shades_corr.png)

Using the known position of the peaks and the area covered by each fragment, we obtain the footprints of the fragments on the RAMSES projected temperature maps. A mean fragment temperature can be then evaluated within these footprints. This kind of analysis, which cannot be reproduced on real observations, is useful to quantify the uncertainties on the assumed temperature values and ranges, along with its impact on mass estimates.\
In Fig. [4](#fig:temperature_ev_ramses_vs_SQUALO) we compare the fragment temperatures and ranges adopted in (cite: 2023MNRAS.520.2306T) with the fragment temperatures derived for the *M1000\_$\mu$10\_$\mathcal{M}$7_S2* realization (the projection in use corresponds to the $x$-axis, i.e. the $y-z$ plane). The simulations-based recovered temperatures gradually increase with the evolution of the clump, as predicted for the observations-based $T_f$. However, in absolute values, the latter does not always prove to have a good match with the temperatures computed from the simulations. By fitting the RAMSES mean temperature, computed across $\sim7000$ AU fragments in the same synthetic field, we derive a power-law of: $$\begin{equation*}
        T_{f,\,mean}\,\textrm{(K)}\, \sim 10.4+0.7\times (L/M)^{0.75}\, \,.
    
\end{equation*}$$ This trend suggests that temperature at the fragment scales increases as a function of clump evolution faster than what observed at the clump scales, e.g., $T_{clump}$ (K) $\propto$ $(L/M)^{0.22}$ for $L/M\geq$10 L$_\odot$/M$_\odot$ ((cite: 2016ApJ...826L...8M)).\
As observed in Fig. [4](#fig:temperature_ev_ramses_vs_SQUALO), toward the evolutionary stages below $\sim30$ L$_\odot$/M$_\odot$, the fragment temperatures populate only the lower end of the SQUALO temperature ranges. This could be due to the absence of feedback mechanisms, as well as a general overestimation of the fragment temperatures in the SQUALO sample. Clump temperatures in the early stages of collapse may also be strongly influenced by the external radiation field. Between $L/M$ $\sim30\,$L$_\odot$/M$_\odot$ and $\sim300\,$L$_\odot$/M$_\odot$, the prescription well represents both the mean temperature and the temperature range associated with the fragments in the field. Above $\sim300$ L$_\odot$/M$_\odot$, few fragments populate the upper end of the SQUALO temperature ranges. The others exceed the predicted maximum temperature (60 K), also reaching temperatures above 100 K. As aforementioned, the reference temperature of 40 K, as well as the $20 - 60$ K span, have not been conceived to represent clumps with $L/M > 100\,$L$_\odot$/M$_\odot$, which are outside the SQUALO $L/M$ range. The mismatch between the SQUALO assumption and the temperature estimates derived from the numerical simulation causes a systematical overestimation of the mass of the observed fragments in the most evolved clumps.\
The results obtained from the Rosetta Stone pipeline are already noteworthy, particularly in helping observers define an appropriate range of temperatures for their $\sim7000$ AU resolution surveys. A more detailed investigation of temperature and mass uncertainties arising from observational assumptions will be presented in future works, through the analysis of a new set of simulations that include jets and Hii regions. By incorporating the effects of these feedback mechanisms on local temperatures and, consequently, on the multiplicity and masses of the recovered fragments, we will be able to more realistically model the advanced stages of cluster formation.

### Mass consistency evaluation

In this section we compare the variations in mass estimates caused by the different temperature assumptions with the masses obtained by integrating the column density maps from simulations. This analysis allows us to quantify to what extent the synthetically observed fluxes yield to outcomes that are consistent with the density distribution observed in the numerical models (Paper I). In particular, in Fig. [4](#fig:temperature_ev_ramses_vs_SQUALO) (bottom panel) we compare the total mass in fragments obtained in four different cases: i) using the SQUALO reference temperatures and temperature ranges; ii) using the mean temperature across fragments derived from the RAMSES temperature maps; iii) using the mean temperature of individual fragments derived from the RAMSES temperature maps; iv) integrating the column densities in the simulations (within the footprints corresponding to the identified fragments).\
Where the SQUALO temperature assumptions are comparable to the average temperatures in the 2D temperature maps from simulations (see Fig. [4](#fig:temperature_ev_ramses_vs_SQUALO), top panel), we obtain consistent mass estimates across the four methods. However, this is not always the case, as observed in e.g., the first evolutionary step. In this case, the SQUALO temperature assumption, as the averaged RAMSES temperatures, do not reflect the actual RAMSES temperature along the line of sight causing the underestimation of the total mass in fragments. We observe a factor $\sim10$ of difference with respect to the mass derived from the column density. Analogous results are discussed in Paper II.\
Additionally, the SQUALO-like mass estimates in the latest evolutionary stages exhibit a factor $\sim2$ of difference with respect to the results obtained using RAMSES temperatures or column density maps. This mismatch occurs because the SQUALO assumptions were designed to cover a narrower range of $L/M$, ending at $\sim100$ L$_\odot$/M$_\odot$. In the most extreme cases, because of the lower end of the assumed temperature range (see Fig. [4](#fig:temperature_ev_ramses_vs_SQUALO) and Table [2](#tab:T_limits)), the most evolved clumps are observed to have a total mass in fragments that exceeds the mass assigned as initial condition in the simulations (see Fig. [6](#fig:tot_mass_MC_vs_LoverM)). These results indicate that a finer prescription on the reference temperature (and associated temperature range) should be made to correctly characterize the observed evolved clumps, especially in the case of $L/M>300$ L$_\odot$/M$_\odot$.

# Analysis

In this section, we report on the analysis of the statistical fragmentation properties derived from the synthetic observations as a function of the $L/M$ clump evolutionary parameter estimated in Paper II. Specifically, we investigate the level of fragmentation in each synthetic map, the accretion of mass onto the fragments (total mass recovered in fragments with respect to the clump mass and evolutionary stage), and the relative (minimum and maximum) distances between the fragments. Specific focus is on the relative contributions of turbulence and magnetic fields, which cannot be directly studied using the 1.3 mm continuum data from (cite: 2023MNRAS.520.2306T). We use the variations observed across the three available projections to provide an estimate of the uncertainties associated with the derived mean fragment properties at $\sim7000$ AU.

Determining the most accurate estimate of fragmentation properties from synthetic maps is a challenging task, as demonstrated by the initial assessment of how well the masses can be recovered using observationally driven assumptions (see Section [3.2.2](#Sect: mass recovery)). A more robust characterization would require identifying three-dimensional, fragment-like structures directly within the simulations smoothed at $\sim7000$ AU, which is currently beyond the scope of this work. Rather than ensuring $100\%$ consistency between simulated and synthetic quantities recovered at 1.3 mm, our primary goal is to compare the fragmentation properties from the post-processed maps with the SQUALO results within a self-consistent framework (see Section [5.2](#Sect:Comparison with observations)). To this end, we rely on the observationally driven assumptions presented in (cite: 2023MNRAS.520.2306T), even if this approach introduces some known biases.

## Fragmentation level

![](images/nfrag_vs_LM.png)

![](images/totmass_MC_vs_LM.png)

![](images/minmaxst_vs_LM_corr.png)

As the clumps collapse and sinks begin to form in the models, we can trace the emergence of fragments in the synthetic observations. In Fig. [5](#fig:n_frag_vs_LoverM), we present the evolution of the number of identified fragments as a function of the $L/M$ evolutionary parameter. This analysis traces the clump evolution for the available combinations of initial conditions, considering both the mean values and the spread observed across the three different projections. For clarity, the plot is divided into two panels to separate the *M500* and *M1000* realizations.\
The fragmentation levels we observe within individual fields range from $2$ to $14$ fragments, with an average of $\sim7$ fragments. Across the 393 maps, we do not find cases in which fragmentation is suppressed. On the contrary, our analysis indicates that fragmentation takes place within the clumps at every evolutionary stage, and that the number of fragments within each field is only weakly dependent on the initial mass of the clump. This suggests that physical factors beyond the initial mass are more relevant in determining the fragmentation patterns.\
When examining the distribution of fragment multiplicities for individual realizations, we do not observe a clear, consistent trend with evolution. Instead, we note a general decrease in the number of fragments toward the more advanced phases of clump collapse. This could be due to both pre-existing and newly formed fragments moving closer to the gravitational potential well(s) and merging as the clump evolves. At $\sim 7000\,$AU resolution, what appears to be a merger of fragments, is not necessarily a physical merger. It is likely the result of multiple structures that may get closer than our resolution limit (see Section [4.3](#Sect:Minimum spanning tree and maximum distance)). From this perspective, the global collapse of the clump appears to dominate the number of detectable fragments at $\sim 7000\,$AU resolution, especially in the latest evolutionary stages.\
Comparing the level of fragmentation for the three available clump magnetization (i.e., $\mu=3$, 10, and 100) we observe that, for $L/M \gtrsim 20$ L$_\odot$/M$_\odot$, a larger number of fragments are preferentially formed when the magnetic parameter $\mu$ is set to the highest of the three explored values. However, while magnetized and non-magnetized scenarios can be disentangled within the uncertainties, it is not possible to distinguish between the two magnetized realizations based solely on the number of identified fragments: multiplicity in the *$\mu$3* realizations is higher than that in the *$\mu$10* realizations during the later stages of the *M500* clump collapse, while it is comparable in the *M1000* case.\
In addition to the influence of magnetic fields, we investigate the role of turbulence in driving the fragmentation properties of our synthetic clumps. As shown in Fig. [5](#fig:n_frag_vs_LoverM), the explored levels of turbulence do not appear to have a significant effect on the multiplicity of fragments. Realizations that differ only for the initial value of $\mathcal{M}$, are indeed comparable. It is possible that the values chosen for the Mach number, $7$ and $10$, are too close to induce any significant variation in the properties of the structures identified at $\sim 7000\,$AU.\
To further characterize potential relationships between the number of identified fragments and the initial conditions of clump collapse, we also use a suite of out-of-the-grid control models. Specifically, we investigate the impact of the initial volume density profile by setting a Bonnor-Ebert profile (realizations *M1000\_$\mu3\_\mathcal{M}$7_S2* and *M1000\_$\mu10\_\mathcal{M}$7_S2*, respectively), the impact of a lower level of turbulence by setting the initial Mach number equal to $3$ (realization *M1000\_$\mu10\_\mathcal{M}3$\_S2*), the impact of stochastic processes by including two additional seeds (realizations *M1000\_$\mu$10\_$\mathcal{M}$7_S3* and *M1000\_$\mu$10\_$\mathcal{M}$7_S4*, respectively). Moreover, we evaluate the impact of the numerical prescription for the accretion luminosity coefficient $f_{\textrm{acc}}$, used to compute the efficiency of the accretion luminosity by testing different values of this parameter with respect to the reference value of 0.1 (for the *M1000\_$\mu$10\_$\mathcal{M}$7_S1* realization; Paper I). Results from the analysis of these control models are reported in Appendix [11](#Appendix:ootg_models).

## Accretion of mass onto the fragments

After presenting the characteristic mass distribution of the fragments across all the available evolutionary stages of the parent clumps (see Fig. [3](#fig:mass_distr)), we now turn our attention to how the total mass recovered in fragments changes as a function of the $L/M$ evolutionary parameter. This is done by calculating the mass of each fragment, assuming a single-temperature model (see Table [2](#tab:T_limits)), and then summing these values for each field. In Fig. [6](#fig:tot_mass_MC_vs_LoverM), we present the mean total mass accreted onto the fragments, which is calculated by considering the three different projections available at each time step. In this case, we use the 1000 MC simulations (see Section [3.2](#Sec:Temperature uncertainties)) to indicate the uncertainty on the distribution.\
The results reveal that uncertainties in the temperature of the dust envelope surrounding the fragments contribute significantly to the uncertainties in the total mass estimate. The variation in mass due to different temperature assumptions can lead to total mass estimates that are up to $\sim5$ times higher than the lowest value they can assume. As mentioned in Section [3.2.1](#Sec:Temperature consistency) (see also Section [3.2.2](#Sect: mass recovery)), the lower ends of the temperature ranges are responsible for overestimating the fragment masses, particularly in the more evolved stages of clump collapse. As a consequence, in most of the MC runs, the most evolved clumps happen to have a total mass in fragments that exceeds the mass assigned as initial conditions.\
By examining the evolution of the total mass in fragments at $\sim 7000$ AU, we find that a continuous accretion process from the parent clumps to the fragments is taking place. The seeds of star formation initially have low masses, often less than 1 M$_\odot$, and their final masses are progressively built up over time. Even relatively large fragments appear to be accreting mass from the parent clump. This provides clear evidence that the fragments do not evolve in isolation, but are instead fed by material from the parent clump which act as a mass reservoir. It is significant that this trend holds regardless of the different environmental initial conditions explored in the simulations.

## Relative distance between the fragments

Among the temperature-independent quantities of interest, we investigate the relative distances between the fragments as a function of the $L/M$ evolutionary parameter. Specifically, we focus on the minimum 2D distance ($d_{\text{min,2D}}$) between the fragments, already explored in (cite: 2023MNRAS.520.2306T), as well as on their maximum 2D distance ($d_{\text{max,2D}}$). Both quantities are derived from the distance matrix of the fragments, using the centroids of the fragments as edges to compute the relative distances. Together, they provide complementary information about the distribution of the fragments within the clumps at different evolutionary stages, potentially revealing important information about the mechanisms driving the approach or separation of the fragments during clump evolution.\
In Fig. [7](#fig:mst_vs_LoverM), we observe the oscillation in time of both $d_{\text{min,2D}}$ and $d_{\text{max,2D}}$. The oscillation occurs regardless of the initial conditions of the simulations, suggesting that the observed behavior is either a general characteristic of the fragment dynamics at $\sim 7000$ AU scales or the result of a systematic observational bias, rather than being driven by specific starting configurations. The resolved fragments appear to be distributed rather evenly across the parent clumps at each evolutionary stage. However, this result might be strongly biased by the linear resolution of $\sim0.036$ pc, which is the minimum observable source separation determined by the combination of the synthetic beam and the reference distance of our sources. We acknowledge that, in the case of rapid collapse, we would be unable to detect new structures forming at scales below the available resolution, or to track already identified structures that get closer than this minimum separation.\
We find that slightly smaller mean values of $d_{\text{max,2D}}$ - reflecting a smaller separation between the most distant fragments - are preferentially observed toward evolved, magnetized clumps. As in the case of the number of fragments (see Section [4.1](#Sect:Fragmentation level)), the evolutionary stage after which the realizations with different clump magnetization start to behave differently corresponds to $L/M\sim20$ L$_\odot$/M$_\odot$. Although we see a difference in the mean values of $d_{\text{max,2D}}$, this result is not always robust across the different projections. For the *$\mu$3* realizations, the fluctuations associated with the three lines of sight are of similar magnitude to the variations introduced by different initial magnetic field conditions, causing its distribution to overlap with that of the non-magnetized scenario at the upper limit.\
The different values observed for $d_{\text{min,2D}}$ and $d_{\text{max,2D}}$ may possibly arise from geometrical effects related to the combination between the size of the parent clumps and the number of fragments formed within them. In our case, it is likely that stronger magnetic fields are shaping the interstellar gas leading to more tightly bound configurations of the parent clumps and, consequently, to smaller $d_{\text{max,2D}}$. However, the observed oscillations and the spread in the data caused by the line of sight effect limit our ability to definitively attribute the recovered fragment distribution to the clump magnetization alone.

# Discussion

Building on the results and the analysis presented in Section [3](#Sect:Results) and Section [4](#Sect:Analysis), we compare the synthetic observations produced at $\sim 7000$ AU resolution with the output of the simulations presented in Paper I. Furthermore, we compare results from our synthetic observations with actual observations, with particular focus on the fragmentation properties analyzed in the SQUALO project ((cite: 2023MNRAS.520.2306T), see Table [\[tab:SQUALO\]](#tab:SQUALO)).

## Comparison with numerical models

The systematic production of synthetic observations of clumps undergoing the fragmentation process is a yet to be established approach (e.g., (cite: 2018NewAR..82....1H), (cite: 2020SSRv..216...62R)), and to the best our knowledge, there are no existing examples of systematic comparisons of fragmentation properties between the synthetic observations and the numerical simulations from which they are derived. Such comparison serves a dual purpose: first, to assess whether the synthetic observations are reliable proxies for the physical outcomes of the underlying models, and second, to ensure that the numerical computation - native at a numerical resolution of $\sim40$ AU (Paper I) - accurately captures the key physical processes, even on larger scales.

### Fragments versus sinks multiplicity

A substantial discrepancy exists between the multiplicity observed in the simulations and in the corresponding synthetic observations. The number of sink particles identified in the models can reach up to the order of 100 in the later stages of clump evolution, with this value being highly sensitive to the initial conditions of the clump collapse, particularly the clump magnetization (up to $\sim50$ sinks of difference across different clump magnetization; Paper I). In contrast, the identification of fragments is strongly affected by the resolution limit covering a narrow range of observed fragment multiplicity ($2-14$), as discussed in Section [4.1](#Sect:Fragmentation level), and supported by results from (cite: 2018A&A...615A..94F) and (cite: 2021A&A...653A.157L).

To address the discrepancy in sinks/fragments multiplicity, we make use of the 3D positional information of the sink particles within the simulated volume to then examine the correspondence between the 2D projected positions of the sinks and the locations of the identified fragments in our synthetic observations. This analysis allows us to evaluate the nature of the structures identified at $\sim7000$ AU and assess the extent to which the fragmentation properties at this scale reflect the underlying physical processes in the simulations. As illustrated in Fig. [2](#fig:postprocessing_sequence) (d), we distinguish different scenarios of fragment-sink(s) correspondence, with their respective statistics reported in Table [3](#tab:fragments_sinks_statistics).

|                             |       |            |
|:---------------------------:|:-----:|:----------:|
|                             |  \#   |     \%     |
|          Fragments          | 2749  |    100     |
|     Fragments w/ sinks      | 2066  | $\sim75.2$ |
|    Fragments w/ one sink    |  458  | $\sim16.7$ |
| Fragments w/ multiple sinks | 1608  | $\sim58.5$ |
|    Fragments w/out sinks    |  683  | $\sim24.8$ |
|            Sinks            | 16209 |    100     |
|     Sinks w/ fragments      | 12389 | $\sim76.4$ |
|    Sinks w/out fragments    | 3820  | $\sim23.6$ |
|                             |       |            |

: Number of fragments and sink particles.

Table notes: Col. 1: Variables related to fragments and sink particles. Col. 2:  Absolute number. Col. 3: Percentage with respect to the total number of fragments and sink particles, respectively.

Focusing on the fragments:

- $\sim75$% of the identified fragments have a correspondence with sink particles. Only $\sim 17$% of the total are associated with a single sink particle;

- $\sim25$% of the identified fragments do not correspond to any sink particle.

The existence of multiple sinks within individual fragments supports a hierarchical and/or multi-layered fragmentation process, suggesting that fragmentation occurs across multiple scales simultaneously. Larger clumps break into smaller fragments, and within these fragments, further fragmentation can occur, leading to the formation of one or more sinks. The differing sensitivity of fragment and sink multiplicity to the clump magnetization indicates that magnetic fields influence the fragmentation process at different scales, though with varying degrees of significance.\
The case of identified fragments that do not correspond to any sink particle, and therefore are not actively forming stars at a given time, can be explained by the following scenarios: i) They correspond to overdensities that have not yet reached the volume density threshold required to form a sink particle but will reach it in the subsequent steps of clump evolution. ii) They correspond to overdensities that are transient and will not form a sink particle in the subsequent steps of clump evolution. Some of these will eventually be dispersed. iii) They appear as overdensities due to projection along the line of sight and/or are the artificial result of the convolution of diffuse structures with the beam of the telescope.\
Focusing on the sink particles, we find that $\sim76$% of them exhibit a corresponding fragment, while the remaining $\sim24$% do not have a correspondence with the identified fragments. Our analysis reveals that this lack of correspondence never involves the most massive sink particle in each field. It is also noteworthy that the absolute number of sink particles without a matching clump varies with the chosen value of $\mu$. For the *$\mu$100*, *$\mu$10*, and *$\mu$3* realizations, this goes up to $\sim 20$, 13, and 8 sinks per field, respectively. This result confirms our ability to best recover compact structures within magnetized clumps. Magnetic fields cause initially homogeneous clumps to collapse in dense and compact sheets and/or filaments (e.g., Paper I, (cite: 2019FrASS...6....5H)), reducing the presence of diffused matter more efficiently than in the quasi-hydrodynamical case. As a potential consequence, compact fragments that exceed the 3$\sigma$ threshold might be more effectively formed in the magnetized scenarios.\
We will be able to address these specific aspects more effectively by closely tracking the evolution of individual fragments through the use of tracer particles, which we plan to include in a forthcoming suite of simulations. As of now, the number of fragments does not correspond to the number of sink particles due to limitations in both spatial resolution and sensitivity (some sinks may not be bright enough to be detected as fragments arising above the 3$\sigma$ level). As a result, the increasing number of sink particles[^10] with the progressive evolution of individual clumps and the impact of clump magnetization - discussed in Paper I, and in line with the models by e.g., (cite: 2011ApJ...729...72P), (cite: 2018A&A...615A..94F), (cite: 2022A&A...668A.147H) - are not equally well observed in the number of fragments at $\sim7000$ AU. Beside the observational biases, this evidence might suggest that the physical mechanisms explored in the simulations could have different significance at the different physical scales.

### Comparison with sink formation efficiency from the simulations

As previously discussed, the SFE parameter, defined as the total mass recovered in sink particles with respect to the mass of the clump (see Eq. [\[eq:SFE\]](#eq:SFE)), can be used in simulations as a proxy of the evolution. In a similar manner, we can define a corresponding quantity at the spatial scales probed by the synthetic observations: the fragment formation efficiency (FFE). The FFE is calculated by dividing the total mass recovered in fragments by the mass of their parent clump, offering a way to track the evolution of the clump at intermediate scales.\
The comparison between the FFE and the SFE provides a valuable tool for interpreting the distribution of mass into compact structures at various physical scales. By examining how much mass is condensed into $\sim 7000$ AU fragments and sink particles at different stages of clump evolution, we gain first insights into the hierarchical fragmentation process. As shown in Fig. [8](#fig:FFE_vs_SFE), the FFE consistently exceeds the SFE at each evolutionary stage. Fragments at $\sim 7000$ AU are more than the simple product of the convolution of one/more sink particles with the telescope beam. Rather, they are real, compact structures that are made up of gas which is more diffuse in comparison to the sinks. This evidence suggests that a significant fraction of the mass within the clump is condensed into fragments, and only a small fraction of it is ultimately converted into stars.\
In particular, in the earliest stages of clump collapse, at SFE$\,\,\sim\,10^{-3}$, the majority of the gas locked into the fragments (FFE $\sim\,10^{-2}$) has not yet been converted into sinks. The difference in these initial efficiencies is further evidence in favor of a multi-layered fragmentation process, where small-scale sinks form within intermediate-scale fragments. With the clump evolution, the mass reservoir available to the fragments diminishes. On the contrary, the sinks accrete with high efficiency from the fragments, bringing the FFE vs. SFE relation closer to the one-to-one line toward the most advanced evolutionary stages. Thanks to the forthcoming RS2.0 suite of simulations, we will explore the same relation in the case of clumps that are formed within filaments. Such analysis will allow us to assess if a depletion in the clump reservoir is observed also when the parent clump can potentially accrete from a larger filament (in opposition to the isolated box).\
In actual observations, the trend in accretion efficiency onto compact structures across scales shows a marked decrease, from values up to $\geq$40% when estimated from clumps down to $\sim$5000 AU structures, to $\leq$10% when considering the efficiency from clumps down to the smallest fragments and cores[^11], as outlined by Traficante et al., in prep.. We will also test this result thanks to the production of high-resolution ($\sim 2000$ AU) synthetic observations.

![](images/FFE_vs_SFE.png)

## Comparison with observations

Synthetic observations serve as a bridge between theory and actual observations, allowing for a self-consistent comparison in terms of common metrics and scales under analysis. The following comparison with the reference observations further proves the predictive power of synthetic observations in the context of star formation. It also represents an important step in the scientific validation of both the RS1.0 simulations and their derived synthetic counterparts.\
Previous studies have certainly benefited from direct comparisons between observations and numerical models (e.g., (cite: 2012ApJ...761..156F), (cite: 2013A&A...555A.112P), (cite: 2019ApJ...886..102S), (cite: 2020A&A...644A..52A), (cite: 2021A&A...645A.142A), (cite: 2024ApJS..270....9X)), but additional layers of complexity must be taken into account when interpreting actual observations on the basis of numerical outputs. Specifically, observers must first understand what kinds of structures and fragmentation properties the models generate at the scales they are interested in, since these are likely to be different from the observed sinks properties (see Section [5.1](#Sect:Comparison with numerical models)).

### Fragmentation level

![](images/parameter_space_nfrag.png)

Based on the results from synthetic observations alone, the level of fragmentation observed in clumps at a spatial resolution of $\sim 7000$ AU does not allow us to resolve the degeneracy concerning the physical mechanisms regulating the fragmentation properties. Extreme cases with more than $\sim 11$ fragments appear to be an exception (see Fig. [5](#fig:n_frag_vs_LoverM)), as they are only associated with the *$\mu$100* realizations in our synthetic observations. According to these findings, clumps with significantly high levels of fragmentation, likely originate from clumps in which the magnetic field is sub-dominant and vice-versa, in line with the observations by e.g., (cite: 2015ApJ...799...74P) and (cite: 2020A&A...644A..52A). Given this result, we hypothesize that the SQUALO clumps, hosting from $1$ to $9$ fragments, are more likely to correspond to magnetized clumps.\
The comparison between fragment multiplicity in the SQUALO clumps and the parameter space covered by the synthetic observations (see Fig. [9](#fig:parameterspace_1)) allows us to evaluate how well the combinations of initial conditions explored in the simulations (see Table [1](#tab:initial_conditions)), together with the post-processing strategy, reproduce the fragmentation properties observed in actual interferometric data. We observe that $7$ out of the $13$ SQUALO clumps are well represented in terms of fragmentation level by the overall distributions. Among the outliers, two clumps, exhibiting $3$ and $4$ fragments, respectively, are very close to the distribution. Four other clumps, exhibiting $2$ fragments or no fragmentation, are poorly represented by the synthetic sample.\
Unlike actual observations, our synthetic observations do not reproduce clumps with a very low number of fragments: only a few maps are characterized by the presence of two fragments, and no cases with a single fragment. Since in our data there is an indication that lower values of $\mu$ may lead to fewer fragments at a resolution of $\sim 7000$ AU, observations with one or two fragments may require stronger magnetic fields than those considered in this study. Alternatively, they could suggest the involvement of additional physical mechanisms to explain the observed fragmentation. Following the philosophy of the Rosetta Stone approach, we begin investigating this hypothesis by utilizing the aforementioned collection of control models, which lie outside the parameter grid presented in Table [1](#tab:initial_conditions) (see Appendix [11](#Appendix:ootg_models)).\
By looking at the overall coverage of the parameter space, we observe that higher levels of fragmentation are generally associated with more advanced evolutionary stages. This pattern also holds for the SQUALO sample, where high fragmentation is not observed in clumps with low $L/M$. Similar findings, supporting the link between high fragmentation and evolved clumps, have been reported in studies based on $\sim1500$ AU resolution observations, such as those by (cite: 2025A&A...696A.151C) and Elia et al. (submitted). Despite this association, a strict correspondence between the number of fragments and the clump evolutionary stage is not found, either in observations or in synthetic observations. In fact, there are many cases where evolved clumps exhibit low fragmentation levels. This suggests that peculiar interplay of the physical forces and/or the impact of larger-scales dynamics concur to the observed variability in fragmentation levels.\
While our synthetic observations predict the formation of up to 14 fragments, higher-resolution observations reveal up to more than 20 fragments (e.g., (cite: 2018A&A...617A.100B), (cite: 2022A&A...664A..26P), (cite: 2025A&A...696A.151C)). This discrepancy suggests that further fragmentation, occurring at smaller scales that our current observations cannot resolve, is expected. As an example, the reference source HG24 exhibits at $\sim 2000$ AU ((cite: 2025A&A...696A.151C)) one more fragment with respect to the $2$ fragments resolved at $\sim 7000$ AU ((cite: 2023MNRAS.520.2306T)).

![](images/parameter_space_totmass_FFE.png)

### Comparison with mass accretion and fragment formation efficiency from the SQUALO sample

Building on prior findings, we now compare the total mass in fragments and the FFE of the SQUALO clumps with the parameter space covered by the synthetic observations. As observed in Section [4.2](#Sect:Accretion of mass onto the fragments), the fragments do not evolve in isolation, but remain closely linked to the parent clump throughout evolution, supporting the clump-fed scenario for star formation (e.g., (cite: Bonnell1997; Bonnell2001), (cite: Klessen2000), (cite: 2006MNRAS.370..488B), (cite: Girichidis2011; Girichidis2012), (cite: 2012A&A...543L...3H), (cite: 2019MNRAS.490.3061V), (cite: 2020MNRAS.496.3482P), (cite: 2023MNRAS.520.2306T)).\
In Fig. [10](#fig:parameterspace_2) (top panel), which shows the total mass accreted onto the fragments as a function of the $L/M$ ratio, only a few outliers (and not too far from the overall covered parameter space) were observed among the $13$ SQUALO clumps. The discrepancy likely arises from differences in the initial clump mass between the SQUALO clumps (ranging from 177 to 2689 M$_\odot$) and the synthetic models, which use two fixed initial mass values. In this case, the normalization by the parent clump mass offers a more direct and meaningful way to compare the two datasets. Indeed, in Fig. [10](#fig:parameterspace_2) (bottom panel), the FFE values from the synthetic models align well with the entire SQUALO sample, suggesting consistent trends across datasets. We acknowledge that the different distances of the SQUALO sources introduce an observational bias in the process of fragment mass estimation (see Eq. [\[eq:mass_f\]](#eq:mass_f)), though this bias should not be significant (except for sensitivity issues) when normalizing the mass in fragments by the mass of the parent clump (which is computed as a function of the same distance). Beside the distance correction, the agreement between datasets implies that the parameter space explored in the RS1.0 suite of simulations successfully reproduces the SQUALO sample in terms of FFE, and further supports the agreement with the clump-fed scenario of star formation already proposed for the SQUALO sources by (cite: 2023MNRAS.520.2306T).

### Comparison with relative distances from the SQUALO sample

When comparing the relative distances between fragments from the SQUALO sample with the parameter space covered by the synthetic observations, we observe some discrepancies across datasets regarding both $d_{\text{min,2D}}$ and $d_{\text{max,2D}}$. The associated trends are shown in Fig. [11](#fig:parameterspace_3). In particular, the $d_{\text{min,2D}}$ distribution in the SQUALO sample shows a decreasing trend over time, which contrasts with our findings (see also the comparison between the SQUALO and CORE surveys presented by (cite: 2023MNRAS.520.2306T)).\
In our synthetic observations, we do not observe a decrease in $d_{\text{min,2D}}$. The large initial spread is due to very high uncertainties (across projections) in the early evolutionary stages of a single realization (see Fig. [14](#fig:Seed1_all_vs_LoverM) for details). These uncertainties cover a shaded area that may give the false impression of a general decreasing trend, even though this behavior does not have a match across all the other realizations. The distribution associated with the synthetic observations cannot fully cover all the SQUALO data due to a known resolution issue. Specifically, we are replicating the observations of the farthest source within the SQUALO sample, which corresponds to the lowest linear resolution in that dataset. As a result, in the comparison, we observe SQUALO points falling below our resolution threshold, reflecting the limitations in resolving smaller-scale structures (which we would resolve by mimicking the high-resolution end of the sample). The resolution issue limits our ability to accurately capture the relative distances between fragments, and to compare these values with those obtained from observations at different resolutions.\
The $d_{\text{max,2D}}$ distribution should, in principle, not be directly affected by resolution limits. However, the synthetic observations do not accurately reproduce the spread observed in the SQUALO sample, especially for the most compact sources. In this case, $d_{\text{max,2D}}$ is likely not recovered properly due to the absence of large-scale dynamics in our simulations, as we are simulating clumps within isolated boxes. The larger-scale interactions, such as the global collapse of a filament or the interactions with neighboring structures, can significantly influence the morphology of the clumps and the clustering of fragments therein. Without these effects, the fragment distribution in our synthetic clumps seems to be on average less compact than in the SQUALO sample. The presence of feedback mechanisms might as well affect the observed clustering properties. We plan to address these limitations in the future RS2.0 suite of models by simulating the collapse of non-isolated clumps incorporating feedback mechanisms.

![](images/parameter_space_mst.png)

# Summary and conclusions

In this paper, we have presented the general workflow of the Rosetta Stone project: an end-to-end framework that aims to probe the fragmentation process of massive clumps by comparing observations and dedicated numerical simulations using realistic synthetic observations (refer to Paper I + Paper II + Paper III for the complete RS1.0 framework). Specifically, we have focused on the comparison of the post-processed simulations produced for this work with real ALMA 1.3 mm observations conducted as part of the SQUALO survey by (cite: 2023MNRAS.520.2306T).

We have demonstrated that, to effectively address the physics governing star-forming sites at the scales probed by actual observations, it is not only necessary to produce readable synthetic observations, but also to ensure that these mimic the observational features (instrumental effects and observational biases) of the dataset they are compared against. This approach has allowed us to perform a self-consistent and systematic comparison between actual observations and synthetic observations to provide a quantitative characterization of how the initial conditions of clumps and environment affect the observed clump fragmentation properties. This comparison was made possible by the estimation of the $L/M$ evolutionary parameter, which was computed for the synthetic clumps in Paper II.

By the analysis of the fragmentation properties of synthetic SQUALO-like clumps performed at $\sim 7000$ AU resolution, we found the following:

- Fragmentation occurs within the clumps at each evolutionary stage. The fragmentation level observed within individual fields ranges from $2$ to $14$ fragments, with an average of $\sim7$ fragments, and is comparable to the fragment multiplicity recovered in SQUALO (1-9). As of now, our suite of simulations does not systematically reproduce cases with $1$ (zero occurrence) or $2$ fragments, which are instead observed in the SQUALO sample.

- At a fixed linear resolution, the number of identified fragments mainly depends on the magnetization of the clump, with high levels of fragmentation preferentially associated with clumps in which the magnetic field is sub-dominant, and vice-versa. This effect is particularly evident in advanced stages of clump collapse corresponding to $L/M\gtrsim20$ L$_\odot$/M$_\odot$. In some instances, stochastic processes limit our ability to discern the impact of clump magnetization on the fragments multiplicity.

- It is possible that magnetic fields are modulating the fragmentation process also in terms of fragmentation patterns, leading to more tightly bound clump configurations and fragment distributions, i.e. to smaller $d_{\text{max,2D}}$ between fragments, in the evolved magnetized clumps.

- The $d_{\text{min,2D}}$ does not exhibit any trend with evolution. However, this result might be strongly biased by the available linear resolution of $\sim0.036$ pc, which is the minimum observable source separation.

- Among identified fragments, $\sim75\%$ have a match with one or multiple sink particles. This evidence supports a hierarchical and/or multi-layered fragmentation process.

- Among the identified fragments that do not have a counterpart in sink particles ($\sim25\%$): some will develop one (or more) sink(s) with the evolution, some are transients, and some others originate from the convolution of the beam with diffuse gas along the line of sight. In the last scenario, identified fragments do not correspond to real compact structures.

- Our synthetic observations support a clump-fed star-formation scenario in which fragments are not isolated from the environment. The accretion of mass onto the fragments continues throughout the whole clump evolution. Based on the comparison with the SFE, the efficiency of the mass accretion process appears to be scale dependent. This represents further evidence of the hierarchical nature of the fragmentation process.

- Overall, the parameter space of fragmentation properties explored with the RS1.0 suite of simulations is in good agreement with the SQUALO observations. The partial mismatch concerning the number of identified fragments suggests that other physical processes with respect to those explored in our grid may be at play in these particular clumps, and has been the primary motivation for developing a set of control models (see Appendix [11](#Appendix:ootg_models)) outside the grid presented in Table [1](#tab:initial_conditions).

As anticipated, the upcoming Rosetta Stone catalogs will feature simulations with a broader parameter space, incorporating more physical effects (such as jets and Hii regions) and a more extensive range of scales (spanning from kpc scales to protostellar disks scales). Thanks to its flexibility, the post-processing pipeline will be also tuned accordingly. We hope that this end-to-end framework will inspire the community to more systematically compare models and observations by means of synthetic observations to advance our understanding of star formation across all scales.

# Acknowledgements

We thank the anonymous referee for the useful feedback, which has helped to improve the quality of the paper. This project was funded by the European Research Council via the ERC Synergy Grant “ECOGAL” (project ID 855130). We thank the whole consortium for the stimulating discussions which helped us tremendously through this process. AT gratefully acknowledges support from a mini-grant funded by INAF. This paper makes use of the following ALMA data: ADS/JAO.ALMA#2018.1.00443.S. ALMA is a partnership of ESO (representing its member states), NSF (USA) and NINS (Japan), together with NRC (Canada), MOST and ASIAA (Taiwan), and KASI (Republic of Korea), in cooperation with the Republic of Chile. The Joint ALMA Observatory is operated by ESO, AUI/NRAO, and NAOJ. We acknowledge PRACE for awarding us access to the JUWELS supercomputer. This work was also granted access to HPC resources of CINES and CCRT under the allocation A0130407023 made by GENCI (Grand Equipement National de Calcul Intensif). RSK also acknowledges financial support from the German Excellence Strategy via the Heidelberg Cluster “STRUCTURES” (EXC 2181 - 390900948) and from the German Ministry for Economic Affairs and Climate Action in project “MAINN” (funding ID 50OO2206). RSK thanks the 2024/25 Class of Radcliffe Fellows for highly interesting and stimulating discussions. G.A.F gratefully acknowledges the Deutsche Forschungsgemeinschaft (DFG) for funding through SFB 1601 “Habitats of massive stars across cosmic time” (sub-project B1) and support from the University of Cologne and its Global Faculty programme. D.W. acknowledges support from the Science and Technology Facilities Council (STFC) \[grant number ST/Y004108/1\].

102 natexlab

(ref: 2020A&A...644A..52A) Añez-López, N., Busquet, G., Koch, P. M., et al. 2020, [A&A](http://dx.doi.org/10.1051/0004-6361/202039152), [644, A52](https://ui.adsabs.harvard.edu/abs/2020A&A...644A..52A)

(ref: 2021A&A...645A.142A) Avison, A., Fuller, G. A., Peretto, N., et al. 2021, [A&A](http://dx.doi.org/10.1051/0004-6361/201936043), [645, A142](https://ui.adsabs.harvard.edu/abs/2021A&A...645A.142A)

(ref: 2007prpl.conf...63B) Ballesteros-Paredes, J., Klessen, R. S., Mac Low, M. M., & Vazquez-Semadeni, E. 2007, in Protostars and Planets V, ed. B. Reipurth, D. Jewitt, & K. Keil, [63](https://ui.adsabs.harvard.edu/abs/2007prpl.conf...63B)

(ref: 2024A&A...682A..81B) Beuther, H., Gieser, C., Soler, J. D., et al. 2024, [A&A](http://dx.doi.org/10.1051/0004-6361/202348117), [682, A81](https://ui.adsabs.harvard.edu/abs/2024A&A...682A..81B)

(ref: 2021A&A...649A.113B) Beuther, H., Gieser, C., Suri, S., et al. 2021, [A&A](http://dx.doi.org/10.1051/0004-6361/202040106), [649, A113](https://ui.adsabs.harvard.edu/abs/2021A&A...649A.113B)

(ref: 2018A&A...617A.100B) Beuther, H., Mottram, J. C., Ahmadi, A., et al. 2018, [A&A](http://dx.doi.org/10.1051/0004-6361/201833021), [617, A100](https://ui.adsabs.harvard.edu/abs/2018A&A...617A.100B)

(ref: 2001ApJ...554..615B) Bjorkman, J. E. & Wood, K. 2001, [ApJ](http://dx.doi.org/10.1086/321336), [554, 615](https://ui.adsabs.harvard.edu/abs/2001ApJ...554..615B)

(ref: 2014MNRAS.445.4015B) Bleuler, A. & Teyssier, R. 2014, [MNRAS](http://dx.doi.org/10.1093/mnras/stu2005), [445, 4015](https://ui.adsabs.harvard.edu/abs/2014MNRAS.445.4015B)

(ref: 2024A&A...688A..30B) Bonanomi, F., Hacar, A., Socci, A., Petry, D., & Suri, S. 2024, [A&A](http://dx.doi.org/10.1051/0004-6361/202348920), [688, A30](https://ui.adsabs.harvard.edu/abs/2024A&A...688A..30B)

(ref: 2006MNRAS.370..488B) Bonnell, I. A. & Bate, M. R. 2006, [MNRAS](http://dx.doi.org/10.1111/j.1365-2966.2006.10495.x), [370, 488](https://ui.adsabs.harvard.edu/abs/2006MNRAS.370..488B)

(ref: Bonnell1997) Bonnell, I. A., Bate, M. R., Clarke, C. J., & Pringle, J. E. 1997, [MNRAS](http://dx.doi.org/10.1093/mnras/285.1.201), [285, 201](https://ui.adsabs.harvard.edu/abs/1997MNRAS.285..201B)

(ref: Bonnell2001) Bonnell, I. A., Bate, M. R., Clarke, C. J., & Pringle, J. E. 2001, [MNRAS](http://dx.doi.org/10.1046/j.1365-8711.2001.04270.x), [323, 785](https://ui.adsabs.harvard.edu/abs/2001MNRAS.323..785B)

(ref: 2025A&A...696A.151C) Coletta, A., Molinari, S., Schisano, E., et al. 2025, [A&A](http://dx.doi.org/10.1051/0004-6361/202452706), [696, A151](https://ui.adsabs.harvard.edu/abs/2025A&A...696A.151C)

(ref: 2024A&A...686A.155C) Colman, T., Brucy, N., Girichidis, P., et al. 2024, [A&A](http://dx.doi.org/10.1051/0004-6361/202348983), [686, A155](https://ui.adsabs.harvard.edu/abs/2024A&A...686A.155C)

(ref: 2012A&A...545A..98C) Commerçon, B., Launhardt, R., Dullemond, C., & Henning, T. 2012, [A&A](http://dx.doi.org/10.1051/0004-6361/201118706), [545, A98](https://ui.adsabs.harvard.edu/abs/2012A&A...545A..98C)

(ref: 2022A&A...665A..25C) Curone, P., Izquierdo, A. F., Testi, L., et al. 2022, [A&A](http://dx.doi.org/10.1051/0004-6361/202142748), [665, A25](https://ui.adsabs.harvard.edu/abs/2022A&A...665A..25C)

(ref: 2015MNRAS.453L..73D) Dipierro, G., Price, D., Laibe, G., et al. 2015, [MNRAS](http://dx.doi.org/10.1093/mnrasl/slv105), [453, L73](https://ui.adsabs.harvard.edu/abs/2015MNRAS.453L..73D)

(ref: 2015MNRAS.447.2144D) Duarte-Cabral, A., Acreman, D. M., Dobbs, C. L., et al. 2015, [MNRAS](http://dx.doi.org/10.1093/mnras/stu2586), [447, 2144](https://ui.adsabs.harvard.edu/abs/2015MNRAS.447.2144D)

(ref: 2012ascl.soft02015D) Dullemond, C. P., Juhasz, A., Pohl, A., et al. 2012, RADMC-3D: A multi-purpose radiative transfer tool, Astrophysics Source Code Library, record ascl:1202.015

(ref: 2021MNRAS.504.2742E) Elia, D., Merello, M., Molinari, S., et al. 2021, [MNRAS](http://dx.doi.org/10.1093/mnras/stab1038), [504, 2742](https://ui.adsabs.harvard.edu/abs/2021MNRAS.504.2742E)

(ref: 2012ApJ...761..156F) Federrath, C. & Klessen, R. S. 2012, [ApJ](http://dx.doi.org/10.1088/0004-637X/761/2/156), [761, 156](https://ui.adsabs.harvard.edu/abs/2012ApJ...761..156F)

(ref: 2018A&A...615A..94F) Fontani, F., Commerçon, B., Giannetti, A., et al. 2018, [A&A](http://dx.doi.org/10.1051/0004-6361/201832672), [615, A94](https://ui.adsabs.harvard.edu/abs/2018A&A...615A..94F)

(ref: 2006A&A...457..371F) Fromang, S., Hennebelle, P., & Teyssier, R. 2006, [A&A](http://dx.doi.org/10.1051/0004-6361:20065371), [457, 371](https://ui.adsabs.harvard.edu/abs/2006A&A...457..371F)

(ref: Girichidis2011) Girichidis, P., Federrath, C., Banerjee, R., & Klessen, R. S. 2011, [MNRAS](http://dx.doi.org/10.1111/j.1365-2966.2011.18348.x), [413, 2741](https://ui.adsabs.harvard.edu/abs/2011MNRAS.413.2741G)

(ref: Girichidis2012) Girichidis, P., Federrath, C., Banerjee, R., & Klessen, R. S. 2012, [MNRAS](http://dx.doi.org/10.1111/j.1365-2966.2011.20073.x), [420, 613](https://ui.adsabs.harvard.edu/abs/2012MNRAS.420..613G)

(ref: 2011IAUS..270..511G) Goodman, A. A. 2011, in Computational Star Formation, ed. J. Alves, B. G. Elmegreen, J. M. Girart, & V. Trimble, Vol. 270, [511–519](https://ui.adsabs.harvard.edu/abs/2011IAUS..270..511G)

(ref: 2017MNRAS.471.4111H) Harries, T. J., Douglas, T. A., & Ali, A. 2017, [MNRAS](http://dx.doi.org/10.1093/mnras/stx1490), [471, 4111](https://ui.adsabs.harvard.edu/abs/2017MNRAS.471.4111H)

(ref: 2018NewAR..82....1H) Haworth, T. J., Glover, S. C. O., Koepferl, C. M., Bisbas, T. G., & Dale, J. E. 2018, [New A Rev.](http://dx.doi.org/10.1016/j.newar.2018.06.001), [82, 1](https://ui.adsabs.harvard.edu/abs/2018NewAR..82....1H)

(ref: 2011A&A...528A..72H) Hennebelle, P., Commerçon, B., Joos, M., et al. 2011, [A&A](http://dx.doi.org/10.1051/0004-6361/201016052), [528, A72](https://ui.adsabs.harvard.edu/abs/2011A&A...528A..72H)

(ref: 2012A&ARv..20...55H) Hennebelle, P. & Falgarone, E. 2012, [A&ARv](http://dx.doi.org/10.1007/s00159-012-0055-y), [20, 55](https://ui.adsabs.harvard.edu/abs/2012A&ARv..20...55H)

(ref: 2019FrASS...6....5H) Hennebelle, P. & Inutsuka, S.-i. 2019, [Frontiers in Astronomy and Space Sciences](http://dx.doi.org/10.3389/fspas.2019.00005), [6, 5](https://ui.adsabs.harvard.edu/abs/2019FrASS...6....5H)

(ref: 2022A&A...668A.147H) Hennebelle, P., Lebreuilly, U., Colman, T., et al. 2022, [A&A](http://dx.doi.org/10.1051/0004-6361/202243803), [668, A147](https://ui.adsabs.harvard.edu/abs/2022A&A...668A.147H)

(ref: 2012A&A...543L...3H) Hennemann, M., Motte, F., Schneider, N., et al. 2012, [A&A](http://dx.doi.org/10.1051/0004-6361/201219429), [543, L3](https://ui.adsabs.harvard.edu/abs/2012A&A...543L...3H)

(ref: 2010A&A...518L..95H) Henning, T., Linz, H., Krause, O., et al. 2010, [A&A](http://dx.doi.org/10.1051/0004-6361/201014635), [518, L95](https://ui.adsabs.harvard.edu/abs/2010A&A...518L..95H)

(ref: 1983QJRAS..24..267H) Hildebrand, R. H. 1983, QJRAS, [24, 267](https://ui.adsabs.harvard.edu/abs/1983QJRAS..24..267H)

(ref: 2023ApJ...950...88J) Jáquez-Domı́nguez, J. M., Galván-Madrid, R., Fritz, J., et al. 2023, [ApJ](http://dx.doi.org/10.3847/1538-4357/accae7), [950, 88](https://ui.adsabs.harvard.edu/abs/2023ApJ...950...88J)

(ref: 2019A&A...629A..63J) Juvela, M., Padoan, P., Ristorcelli, I., & Pelkonen, V.-M. 2019, [A&A](http://dx.doi.org/10.1051/0004-6361/201935882), [629, A63](https://ui.adsabs.harvard.edu/abs/2019A&A...629A..63J)

(ref: Klessen2000) Klessen, R. S. & Burkert, A. 2000, [ApJS](http://dx.doi.org/10.1086/313371), [128, 287](https://ui.adsabs.harvard.edu/abs/2000ApJS..128..287K)

(ref: 2016SAAS...43...85K) Klessen, R. S. & Glover, S. C. O. 2016, [Saas-Fee Advanced Course](http://dx.doi.org/10.1007/978-3-662-47890-5_2), [43, 85](https://ui.adsabs.harvard.edu/abs/2016SAAS...43...85K)

(ref: 2017ApJS..233....1K) Koepferl, C. M., Robitaille, T. P., Dale, J. E., & Biscani, F. 2017, [ApJS](http://dx.doi.org/10.3847/1538-4365/233/1/1), [233, 1](https://ui.adsabs.harvard.edu/abs/2017ApJS..233....1K)

(ref: 2007ApJ...665..478K) Krumholz, M. R., Klein, R. I., & McKee, C. F. 2007a, [ApJ](http://dx.doi.org/10.1086/519305), [665, 478](https://ui.adsabs.harvard.edu/abs/2007ApJ...665..478K)

(ref: 2007ApJ...656..959K) Krumholz, M. R., Klein, R. I., & McKee, C. F. 2007b, [ApJ](http://dx.doi.org/10.1086/510664), [656, 959](https://ui.adsabs.harvard.edu/abs/2007ApJ...656..959K)

(ref: 2003ARA&A..41...57L) Lada, C. J. & Lada, E. A. 2003, [ARA&A](http://dx.doi.org/10.1146/annurev.astro.41.011802.094844), [41, 57](https://ui.adsabs.harvard.edu/abs/2003ARA&A..41...57L)

(ref: 2023MNRAS.522.3719L) Liu, H.-L., Tej, A., Liu, T., et al. 2023, [MNRAS](http://dx.doi.org/10.1093/mnras/stad047), [522, 3719](https://ui.adsabs.harvard.edu/abs/2023MNRAS.522.3719L)

(ref: 2024RAA....24b5009L) Liu, X., Liu, T., Zhu, L., et al. 2024, [Research in Astronomy and Astrophysics](http://dx.doi.org/10.1088/1674-4527/ad0d5c), [24, 025009](https://ui.adsabs.harvard.edu/abs/2024RAA....24b5009L)

(ref: 2021A&A...653A.157L) Louvet, F., Hennebelle, P., Men’shchikov, A., et al. 2021, [A&A](http://dx.doi.org/10.1051/0004-6361/202040053), [653, A157](https://ui.adsabs.harvard.edu/abs/2021A&A...653A.157L)

(ref: 2014ApJ...783...60M) Mairs, S., Johnstone, D., Offner, S. S. R., & Schnee, S. 2014, [ApJ](http://dx.doi.org/10.1088/0004-637X/783/1/60), [783, 60](https://ui.adsabs.harvard.edu/abs/2014ApJ...783...60M)

(ref: 2011A&A...530A.101M) Malinen, J., Juvela, M., Collins, D. C., Lunttila, T., & Padoan, P. 2011, [A&A](http://dx.doi.org/10.1051/0004-6361/201015767), [530, A101](https://ui.adsabs.harvard.edu/abs/2011A&A...530A.101M)

(ref: 2022FrASS...9.9223M) Maury, A., Hennebelle, P., & Girart, J. M. 2022, [Frontiers in Astronomy and Space Sciences](http://dx.doi.org/10.3389/fspas.2022.949223), [9, 949223](https://ui.adsabs.harvard.edu/abs/2022FrASS...9.9223M)

(ref: 2007ARA&A..45..565M) McKee, C. F. & Ostriker, E. C. 2007, [ARA&A](http://dx.doi.org/10.1146/annurev.astro.45.051806.110602), [45, 565](https://ui.adsabs.harvard.edu/abs/2007ARA&A..45..565M)

(ref: 2003ApJ...585..850M) McKee, C. F. & Tan, J. C. 2003, [ApJ](http://dx.doi.org/10.1086/346149), [585, 850](https://ui.adsabs.harvard.edu/abs/2003ApJ...585..850M)

(ref: 2007ASPC..376..127M) McMullin, J. P., Waters, B., Schiebel, D., Young, W., & Golap, K. 2007, in Astronomical Society of the Pacific Conference Series, Vol. 376, Astronomical Data Analysis Software and Systems XVI, ed. R. A. Shaw, F. Hill, & D. J. Bell, [127](https://ui.adsabs.harvard.edu/abs/2007ASPC..376..127M)

(ref: 2021A&A...646A..74M) Mège, P., Russeil, D., Zavagno, A., et al. 2021, [A&A](http://dx.doi.org/10.1051/0004-6361/202038956), [646, A74](https://ui.adsabs.harvard.edu/abs/2021A&A...646A..74M)

(ref: 2016ApJ...826L...8M) Molinari, S., Merello, M., Elia, D., et al. 2016, [ApJL](http://dx.doi.org/10.3847/2041-8205/826/1/L8), [826, L8](https://ui.adsabs.harvard.edu/abs/2016ApJ...826L...8M)

(ref: 2025A&A...696A.149M) Molinari, S., Schilke, P., Battersby, C., et al. 2025, [A&A](http://dx.doi.org/10.1051/0004-6361/202452702), [696, A149](https://ui.adsabs.harvard.edu/abs/2025A&A...696A.149M)

(ref: 2010A&A...518L.100M) Molinari, S., Swinyard, B., Bally, J., et al. 2010, [A&A](http://dx.doi.org/10.1051/0004-6361/201014659), [518, L100](https://ui.adsabs.harvard.edu/abs/2010A&A...518L.100M)

(ref: 2024ApJ...966..171M) Morii, K., Sanhueza, P., Zhang, Q., et al. 2024, [ApJ](http://dx.doi.org/10.3847/1538-4357/ad32d0), [966, 171](https://ui.adsabs.harvard.edu/abs/2024ApJ...966..171M)

(ref: 2022A&A...662A...8M) Motte, F., Bontemps, S., Csengeri, T., et al. 2022, [A&A](http://dx.doi.org/10.1051/0004-6361/202141677), [662, A8](https://ui.adsabs.harvard.edu/abs/2022A&A...662A...8M)

(ref: 2025A&A...694A..24M) Motte, F., Pouteau, Y., Nony, T., et al. 2025, [A&A](http://dx.doi.org/10.1051/0004-6361/202451931), [694, A24](https://ui.adsabs.harvard.edu/abs/2025A&A...694A..24M)

(ref: 1976ApJ...210..326M) Mouschovias, T. C. & Spitzer, Jr., L. 1976, [ApJ](http://dx.doi.org/10.1086/154835), [210, 326](https://ui.adsabs.harvard.edu/abs/1976ApJ...210..326M)

(ref: 2014ApJ...784...61O) Offner, S. S. R. & Arce, H. G. 2014, [ApJ](http://dx.doi.org/10.1088/0004-637X/784/1/61), [784, 61](https://ui.adsabs.harvard.edu/abs/2014ApJ...784...61O)

(ref: 2020ApJ...900...82P) Padoan, P., Pan, L., Juvela, M., Haugbølle, T., & Nordlund, Å. 2020, [ApJ](http://dx.doi.org/10.3847/1538-4357/abaa47), [900, 82](https://ui.adsabs.harvard.edu/abs/2020ApJ...900...82P)

(ref: 2023MNRAS.522.3548P) Padoan, P., Pelkonen, V. M., Juvela, M., Haugbølle, T., & Nordlund, Å. 2023, [MNRAS](http://dx.doi.org/10.1093/mnras/stad1213), [522, 3548](https://ui.adsabs.harvard.edu/abs/2023MNRAS.522.3548P)

(ref: 2015MNRAS.453.3785P) Palau, A., Ballesteros-Paredes, J., Vázquez-Semadeni, E., et al. 2015, [MNRAS](http://dx.doi.org/10.1093/mnras/stv1834), [453, 3785](https://ui.adsabs.harvard.edu/abs/2015MNRAS.453.3785P)

(ref: 2021ApJ...912..159P) Palau, A., Zhang, Q., Girart, J. M., et al. 2021, [ApJ](http://dx.doi.org/10.3847/1538-4357/abee1e), [912, 159](https://ui.adsabs.harvard.edu/abs/2021ApJ...912..159P)

(ref: 2023ASPC..534..193P) Pattle, K., Fissel, L., Tahani, M., Liu, T., & Ntormousi, E. 2023, in Astronomical Society of the Pacific Conference Series, Vol. 534, Protostars and Planets VII, ed. S. Inutsuka, Y. Aikawa, T. Muto, K. Tomida, & M. Tamura, [193](https://ui.adsabs.harvard.edu/abs/2023ASPC..534..193P)

(ref: 2013A&A...555A.112P) Peretto, N., Fuller, G. A., Duarte-Cabral, A., et al. 2013, [A&A](http://dx.doi.org/10.1051/0004-6361/201321318), [555, A112](https://ui.adsabs.harvard.edu/abs/2013A&A...555A.112P)

(ref: 2020MNRAS.496.3482P) Peretto, N., Rigby, A., André, P., et al. 2020, [MNRAS](http://dx.doi.org/10.1093/mnras/staa1656), [496, 3482](https://ui.adsabs.harvard.edu/abs/2020MNRAS.496.3482P)

(ref: 2011ApJ...729...72P) Peters, T., Banerjee, R., Klessen, R. S., & Mac Low, M.-M. 2011, [ApJ](http://dx.doi.org/10.1088/0004-637X/729/1/72), [729, 72](https://ui.adsabs.harvard.edu/abs/2011ApJ...729...72P)

(ref: 2015ApJ...799...74P) Pillai, T., Kauffmann, J., Tan, J. C., et al. 2015, [ApJ](http://dx.doi.org/10.1088/0004-637X/799/1/74), [799, 74](https://ui.adsabs.harvard.edu/abs/2015ApJ...799...74P)

(ref: 2016A&A...591A..19P) Pillai, T., Kauffmann, J., Wiesemeyer, H., & Menten, K. M. 2016, [A&A](http://dx.doi.org/10.1051/0004-6361/201527803), [591, A19](https://ui.adsabs.harvard.edu/abs/2016A&A...591A..19P)

(ref: 2011A&A...530A.118P) Pillai, T., Kauffmann, J., Wyrowski, F., et al. 2011, [A&A](http://dx.doi.org/10.1051/0004-6361/201015899), [530, A118](https://ui.adsabs.harvard.edu/abs/2011A&A...530A.118P)

(ref: 2022A&A...664A..26P) Pouteau, Y., Motte, F., Nony, T., et al. 2022, [A&A](http://dx.doi.org/10.1051/0004-6361/202142951), [664, A26](https://ui.adsabs.harvard.edu/abs/2022A&A...664A..26P)

(ref: 1993A&A...279..577P) Preibisch, T., Ossenkopf, V., Yorke, H. W., & Henning, T. 1993, A&A, [279, 577](https://ui.adsabs.harvard.edu/abs/1993A&A...279..577P)

(ref: 2024A&A...685A..67R) Redaelli, E., Bovino, S., Lupi, A., et al. 2024, [A&A](http://dx.doi.org/10.1051/0004-6361/202346413), [685, A67](https://ui.adsabs.harvard.edu/abs/2024A&A...685A..67R)

(ref: Reissl+2016) Reissl, S., Wolf, S., & Brauer, R. 2016, [A&A](http://dx.doi.org/10.1051/0004-6361/201424930), [593, A87](https://ui.adsabs.harvard.edu/abs/2016A&A...593A..87R)

(ref: Reissl+2018) Reissl, S., Wolf, S., & Brauer, R. 2018, POLARIS: POLArized RadIation Simulator, Astrophysics Source Code Library, record ascl:1807.001

(ref: 2020SSRv..216...62R) Rosen, A. L., Offner, S. S. R., Sadavoy, S. I., et al. 2020, [Space Sci. Rev.](http://dx.doi.org/10.1007/s11214-020-00688-5), [216, 62](https://ui.adsabs.harvard.edu/abs/2020SSRv..216...62R)

(ref: 2010A&A...515A..42R) Rygl, K. L. J., Wyrowski, F., Schuller, F., & Menten, K. M. 2010, [A&A](http://dx.doi.org/10.1051/0004-6361/200913510), [515, A42](https://ui.adsabs.harvard.edu/abs/2010A&A...515A..42R)

(ref: 2019ApJ...886..102S) Sanhueza, P., Contreras, Y., Wu, B., et al. 2019, [ApJ](http://dx.doi.org/10.3847/1538-4357/ab45e9), [886, 102](https://ui.adsabs.harvard.edu/abs/2019ApJ...886..102S)

(ref: 2014MNRAS.441.1628S) Smith, R. J., Glover, S. C. O., Clark, P. C., Klessen, R. S., & Springel, V. 2014, [MNRAS](http://dx.doi.org/10.1093/mnras/stu616), [441, 1628](https://ui.adsabs.harvard.edu/abs/2014MNRAS.441.1628S)

(ref: 2018MNRAS.475.2383S) Sormani, M. C., Treß, R. G., Ridley, M., et al. 2018, [MNRAS](http://dx.doi.org/10.1093/mnras/stx3258), [475, 2383](https://ui.adsabs.harvard.edu/abs/2018MNRAS.475.2383S)

(ref: 2019ApJ...886...36S) Svoboda, B. E., Shirley, Y. L., Traficante, A., et al. 2019, [ApJ](http://dx.doi.org/10.3847/1538-4357/ab40ca), [886, 36](https://ui.adsabs.harvard.edu/abs/2019ApJ...886...36S)

(ref: 2019MNRAS.487.1248S) Szulágyi, J., Dullemond, C. P., Pohl, A., & Quanz, S. P. 2019, [MNRAS](http://dx.doi.org/10.1093/mnras/stz1326), [487, 1248](https://ui.adsabs.harvard.edu/abs/2019MNRAS.487.1248S)

(ref: 2014prpl.conf..149T) Tan, J. C., Beltrán, M. T., Caselli, P., et al. 2014, in Protostars and Planets VI, ed. H. Beuther, R. S. Klessen, C. P. Dullemond, & T. Henning, [149–172](https://ui.adsabs.harvard.edu/abs/2014prpl.conf..149T)

(ref: 2019ApJ...878...10T) Tang, Y.-W., Koch, P. M., Peretto, N., et al. 2019, [ApJ](http://dx.doi.org/10.3847/1538-4357/ab1484), [878, 10](https://ui.adsabs.harvard.edu/abs/2019ApJ...878...10T)

(ref: 2002A&A...385..337T) Teyssier, R. 2002, [A&A](http://dx.doi.org/10.1051/0004-6361:20011817), [385, 337](https://ui.adsabs.harvard.edu/abs/2002A&A...385..337T)

(ref: 2017MNRAS.470.3882T) Traficante, A., Fuller, G. A., Billot, N., et al. 2017, [MNRAS](http://dx.doi.org/10.1093/mnras/stx1375), [470, 3882](https://ui.adsabs.harvard.edu/abs/2017MNRAS.470.3882T)

(ref: 2015A&A...574A.119T) Traficante, A., Fuller, G. A., Pineda, J. E., & Pezzuto, S. 2015, [A&A](http://dx.doi.org/10.1051/0004-6361/201323254), [574, A119](https://ui.adsabs.harvard.edu/abs/2015A&A...574A.119T)

(ref: 2023MNRAS.520.2306T) Traficante, A., Jones, B. M., Avison, A., et al. 2023, [MNRAS](http://dx.doi.org/10.1093/mnras/stad272), [520, 2306](https://ui.adsabs.harvard.edu/abs/2023MNRAS.520.2306T)

(ref: 2024A&A...684A..36T) Tung, N.-D., Testi, L., Lebreuilly, U., et al. 2024, [A&A](http://dx.doi.org/10.1051/0004-6361/202348730), [684, A36](https://ui.adsabs.harvard.edu/abs/2024A&A...684A..36T)

(ref: 2014MNRAS.443.1555U) Urquhart, J. S., Moore, T. J. T., Csengeri, T., et al. 2014, [MNRAS](http://dx.doi.org/10.1093/mnras/stu1207), [443, 1555](https://ui.adsabs.harvard.edu/abs/2014MNRAS.443.1555U)

(ref: 2024MNRAS.530.3445V) Vázquez-Semadeni, E., Gómez, G. C., & González-Samaniego, A. 2024a, [MNRAS](http://dx.doi.org/10.1093/mnras/stae1090), [530, 3445](https://ui.adsabs.harvard.edu/abs/2024MNRAS.530.3445V)

(ref: 2019MNRAS.490.3061V) Vázquez-Semadeni, E., Palau, A., Ballesteros-Paredes, J., Gómez, G. C., & Zamora-Avilés, M. 2019, [MNRAS](http://dx.doi.org/10.1093/mnras/stz2736), [490, 3061](https://ui.adsabs.harvard.edu/abs/2019MNRAS.490.3061V)

(ref: 2024arXiv240810406V) Vázquez-Semadeni, E., Palau, A., Gómez, G. C., et al. 2024b, [[Submitted to MNRAS, arXiv e-prints](http://dx.doi.org/10.48550/arXiv.2408.10406), arXiv:2408.10406](https://ui.adsabs.harvard.edu/abs/2024arXiv240810406V)

(ref: 2024ApJ...962..136W) Wang, J.-W., Koch, P. M., Clarke, S. D., et al. 2024, [ApJ](http://dx.doi.org/10.3847/1538-4357/ad165b), [962, 136](https://ui.adsabs.harvard.edu/abs/2024ApJ...962..136W)

(ref: 2011ApJ...735...64W) Wang, K., Zhang, Q., Wu, Y., & Zhang, H. 2011, [ApJ](http://dx.doi.org/10.1088/0004-637X/735/1/64), [735, 64](https://ui.adsabs.harvard.edu/abs/2011ApJ...735...64W)

(ref: 2024ApJS..270....9X) Xu, F., Wang, K., Liu, T., et al. 2024, [ApJS](http://dx.doi.org/10.3847/1538-4365/acfee5), [270, 9](https://ui.adsabs.harvard.edu/abs/2024ApJS..270....9X)

(ref: 2023MNRAS.520.3259X) Xu, F.-W., Wang, K., Liu, T., et al. 2023, [MNRAS](http://dx.doi.org/10.1093/mnras/stad012), [520, 3259](https://ui.adsabs.harvard.edu/abs/2023MNRAS.520.3259X)

(ref: 2023ApJ...953...40Y) Yang, D., Liu, H.-L., Tej, A., et al. 2023, [ApJ](http://dx.doi.org/10.3847/1538-4357/acdf42), [953, 40](https://ui.adsabs.harvard.edu/abs/2023ApJ...953...40Y)

(ref: 2015ApJ...804..141Z) Zhang, Q., Wang, K., Lu, X., & Jiménez-Serra, I. 2015, [ApJ](http://dx.doi.org/10.1088/0004-637X/804/2/141), [804, 141](https://ui.adsabs.harvard.edu/abs/2015ApJ...804..141Z)

(ref: 2009ApJ...696..268Z) Zhang, Q., Wang, Y., Pillai, T., & Rathborne, J. 2009, [ApJ](http://dx.doi.org/10.1088/0004-637X/696/1/268), [696, 268](https://ui.adsabs.harvard.edu/abs/2009ApJ...696..268Z)

# The SQUALO sample

In this Appendix we report the table (see Table [\[tab:SQUALO\]](#tab:SQUALO)) with all the properties of the $13$ clumps from the SQUALO survey ((cite: 2023MNRAS.520.2306T)). Specifically, the clump properties have been taken from the latest release of the Hi-GAL clump catalog ((cite: 2021MNRAS.504.2742E)) and fragment-scale properties have been taken from (cite: 2023MNRAS.520.2306T) or derived from the analysis therein.

|  |  |  |  |  |  |  |  |  |  |  |
|:---|:--:|:--:|:--:|:--:|:--:|:--:|:--:|:--:|:--:|:--:|
| Designation | $M_\textrm{clump}$ | $L_\textrm{clump}$ | $L_\textrm{clump}$/$M_\textrm{clump}$ | $d$ | $\#$f | $M_{\textrm{tot, fragments}}$ | FFE | $d_{\textrm{min}}$ | $d_{\textrm{max}}$ | r.m.s. |
|  | (M$_\odot$) | (L$_\odot$) | (L$_\odot$/M$_\odot$) | (kpc) |  | (M$_\odot$) |  | (pc) | (pc) | (mJy/beam) |
| HIGALBM327.3918+0.1996 | 1121 | 14146 | 12.6 | 5.16 | 9 | 141.9 | 0.13 | 0.03 | 0.05 | 2.68 |
| HIGALBM327.4022+0.4449 | 2157 | 73841 | 34.2 | 4.63 | 5 | 423.5 | 0.38 | 0.03 | 0.34 | 8.67 |
| HIGALBM331.1314-0.2438 | 2467 | 54845 | 22.2 | 4.95 | 2 | 413.8 | 0.37 | 0.04 | 0.04 | 11.53 |
| HIGALBM332.6045-0.1674 | 177 | 1405 | 7.9 | 3.07 | 2 | 20.7 | 0.02 | 0.14 | 0.14 | 1.15 |
| HIGALBM338.9260+0.6340 | 2689 | 10280 | 3.8 | 4.16 | 4 | 163.4 | 0.15 | 0.07 | 0.19 | 3.26 |
| HIGALBM341.2149-0.2359 | 700 | 7210 | 10.3 | 3.45 | 7 | 34.7 | 0.03 | 0.02 | 0.27 | 1.87 |
| HIGALBM343.5212-0.5172 | 347 | 7039 | 20.3 | 3.03 | 5 | 5.2 | 0.01 | 0.03 | 0.12 | 1.07 |
| HIGALBM343.7560-0.1629 | 461 | 6778 | 14.7 | 2.0 | 1 | 73.4 | 0.07 | \- | \- | 15.18 |
| HIGALBM344.1032-0.6609 | 230 | 3586 | 15.6 | 2.0 | 3 | 3.5 | $<$0.01 | 0.07 | 0.10 | 1.64 |
| HIGALBM344.2210-0.5932 | 202 | 21645 | 107.0 | 2.0 | 7 | 35.5 | 0.03 | 0.01 | 0.05 | 3.81 |
| HIGALBM24.0116+0.4897$^{*}$ | 1334 | 158 | 0.1 | 5.22 | 2 | 40.8 | 0.04 | 0.08 | 0.08 | 1.42 |
| HIGALBM28.1957-0.0724 | 1598 | 594 | 0.4 | 5.36 | 4 | 22.4 | 0.02 | 0.13 | 0.50 | 0.78 |
| HIGALBM31.9462+0.0759 | 1392 | 133 | 0.1 | 5.5 | 4 | 40.8 | 0.04 | 0.07 | 0.29 | 0.83 |
|  |  |  |  |  |  |  |  |  |  |  |

Table notes: The clump properties have been taken from the latest release of the Hi-GAL clump catalog ((cite: 2021MNRAS.504.2742E)) and fragment-scale properties have been taken from (cite: 2023MNRAS.520.2306T) or derived from the analysis therein. Col.1: Source designation ID. Cols. 2–3: Mass $M_\textrm{clump}$ and luminosity $L_\textrm{clump}$ of the parent clumps. Col. 4: $L_\textrm{clump}$/$M_\textrm{clump}$ of the clump, used as evolutionary indicator. Col. 5: Source distances adopted in (cite: 2023MNRAS.520.2306T). Col. 6: Number of fragments $\#$f identified in each clump. Cols. 7-8: Total mass accreted onto the fragments $M_{\textrm{tot, fragments}}$ and fragment formation efficiency FFE obtained by dividing by the mass of the parent clump (normalized to 1). Cols. 9-10: Minimum $d_{\textrm{min}}$ and maximum $d_{\textrm{max}}$ distances between the fragments. Col. 11: Achieved r.m.s..\
\

# Noise consistency analysis

In order to ensure data consistency between the SQUALO reference observations and the synthetic data, we compare the r.m.s. properties obtained for the two datasets (see Fig. [12](#fig:parameterspace_4)). The estimated r.m.s. for the set of synthetic observations, calculated using the *Hyper* software directly on the cleaned (primary beam non-corrected) maps, ranges from $\sim0.02$ to $\sim15$ mJy/beam. While its values varies significantly across the sample, it is comparable to the r.m.s. range of the cleaned reference observations, which spans from $\sim0.8$ to $\sim15$ mJy/beam. The mean r.m.s. of 2.9 mJy/beam across the sample is consistent with the 1.42 mJy/beam r.m.s. of the HG24 reference source.

Notably, the r.m.s. values for the synthetic sample increases with evolutionary stage. This effect may be possibly linked to the variation in clump brightness and morphology over time. The integrated signal reflects both the increased flux from compact sources and the ongoing collapse of filamentary structures; indeed, these structures become progressively brighter and less diffuse as the clumps evolve. Despite the $\sim3$-order-of-magnitude span in r.m.s. values, the corresponding dynamic range, computed as the ratio between the peak flux of the brightest source and the r.m.s. of each field, varies by less than $\sim2$ orders of magnitude. The dynamic range estimated across all realizations and all evolutionary steps goes from $\sim2$ to $\sim115$. This relatively narrow range suggests that the increase in peak source brightness and in the background fluctuations are correlated.

![](images/parameter_space_rms.png)

# Pipelines comparison

In Fig. [13](#fig:model_vs_synt_vs_simalma), we present a visual comparison that illustrates the impact of different post-processing pipelines on the resulting synthetic images. Specifically, we compare the results obtained using the Rosetta Stone pipeline - which includes a tailored computation of visibilities and the parameters of the SQUALO project, optimized for clump fragmentation observations - with those from the `simalma` pipeline implemented in the CASA software. This comparison is based on two distinct evolutionary stages of clump collapse, corresponding to $L/M \sim 10$ and 250 L$_\odot$/M$_\odot$, respectively.\
As mentioned in Section [2.2](#Sect:Synthetic observations), if not tuned to reproduce a specific observation, the `simalma` pipeline operates under default conditions such as ideal instrumental and weather parameters, and continuous integration time. The default settings also include general-purpose data reduction and cleaning steps, which are well suited for a wide range of applications. However, for our specific science goals, a more customized approach was necessary to fully reproduce the complexity of our reference observations. Taking as a reference the outputs from the Rosetta Stone (SQUALO) pipeline, the `simalma` setup causes a loss of flux from the large-scale emission up to $\sim80\%$ ($\sim40\%$) toward the overall clump structure and up to $\sim50\%$ ($\sim20\%$) toward the individual fragments in the earliest (latest) evolutionary stage. This second estimation is possible only for the cases in which the same fragment is detected in both maps. It is likely that a general-purpose algorithm fails to recover most large-scale emission from the `7 m` visibilities causing, for example, the presence of dips surrounding the main structure in the most evolved clumps (typically indicative of missing short-spacings).

Two main factors contribute to the observed flux loss. First, the synthetic acquisition of visibilities in the `simalma` pipeline employs a single-track observation strategy, leading to a different UV-plane sampling with respect to the coverage achieved with multiple execution blocks in real observations. The impact of the different sampling also affects the size of the synthetic beam: in the `simalma` case the beam is $\sim 1.2$ times the SQUALO one, while the one obtained with the Rosetta Stone pipeline is comparable to our reference. Second, the cleaning procedure in `simalma` lacks tools such as auto-masking and multi-scale cleaning, which are typically used to recover large-scale emission components in the final cleaned image when properly tuned. The use of different execution blocks to sample the UV-plane, the incorporation of realistic instrumental setups, the modeling of weather conditions, and the use of joint deconvolution with cleaning and masking techniques implemented by (cite: 2023MNRAS.520.2306T), make the Rosetta Stone pipeline the optimal pipeline for interpreting the reference observations using synthetic observations as a tool.\
Following the production of realistic synthetic maps, the next step in our methodology involves extracting candidate sources from the images and assessing their photometric properties, which allow us to explore the fragmentation properties of the sample (see Section [4](#Sect:Analysis)). An example of source extraction for the fields in Fig. [13](#fig:model_vs_synt_vs_simalma) is provided to demonstrate how the choice of pipeline also affects source identification. In particular, the different UV-plane coverage and deconvolution strategies significantly affect the quality of the cleaned images, and consequently, the accuracy of source identification. This is particularly evident in the early stages of clump collapse. In the `simalma` cleaned map at $L/M \sim 10$ L$_\odot$/M$_\odot$, the unrealistic UV coverage leads to the production of false positives and negatives (see Fig. [13](#fig:model_vs_synt_vs_simalma)), which make source identification and photometry unreliable unless the source extraction algorithm is carefully tuned. The $L/M \sim 10$ L$_\odot$/M$_\odot$ `simalma` cleaned image also exhibits a candidate fragment (peaks exceeding three times the local r.m.s.) outside the main emitting structure (gray contours, identified in the model). Two other false candidate fragments are identified outside of this map cut. With the results from this comparison, we further validate the data reduction and the production of final images with the fine-tuned Rosetta Stone pipeline.

![](images/pipeline_comparison_chart_3.png)

![](images/Seed1_all_corr.png)

# Fragmentation properties from *S1* realizations

In Fig. [14](#fig:Seed1_all_vs_LoverM), we provide the distribution of the number of fragments identified in each clump, the total mass in fragments and the relative distance between the fragments as a function of the clump $L/M$ for the *S1* realizations. In contrast to *S2* results, the impact of the clump magnetization on the number of fragments is less clear, especially across the *M500* realizations. This discrepancy is mainly due to the peculiar stochastic processes at play when the same models are initialized with a different seed. In the *S1* case, the stochasticity has larger impact on the fragmentation, and its effects seem to counteract the magnetic regulation. However, we cannot rule out the possibility that the combination of the stochastic seed and our fixed orthogonal projections may be allowing us to better address the impact of the physical initial conditions of the simulations for the *S2* realizations. General considerations on the fragmentation properties reported in Section [4](#Sect:Analysis) hold true also for the *S1* realizations.

# The necessity of having an end-to-end framework

Following the philosophy of the Rosetta Stone project, we investigate how to recover clumps with low levels of fragmentation by utilizing a collection of control models that lie outside the parameter grid (see Table [1](#tab:initial_conditions)) used to derive the results presented in the main body of this paper. These different models, shown in Fig. [15](#fig:parameterspace_5), include two realizations with an initial Bonnor-Ebert (BE) profile, a realization with $\mathcal{M}=3$, and two realizations in which we explore the impact of different initial seeds, *S3* and *S4*, respectively. None of these control models allows us to systematically reproduce the cases of low or no fragmentation. Only in the case of the Bonnor-Ebert sphere with initial $\mu=3$ (top panel), and in the case with $\mathcal{M}=3$ (central panel), we cover two small portions of the parameter space which are not populated by the RS1.0 models.

The case of the comparison of the different seeds is of particular interest (see Fig. [15](#fig:parameterspace_5), bottom panel). Variations in the initial seed, which influence the morphology of the evolving clumps, typically induce fluctuations of similar magnitude to those associated with projection effects (i.e., variations of a few fragments). However, in some instances the stochastic processes associated with the choice of the initial seed can completely dominate the fragmentation (as in e.g., Fig. [15](#fig:parameterspace_5), realization *M1000\_$\mu10\_\mathcal{M}7$\_S4*). Also in less extreme examples, their impact might hinder the chance to disentangle the role of the other physical initial conditions, as assessed in the case of *M500_S1* realizations (see Appendix [10](#Sect: Seed1 fragmentation properties)).

![](images/parameter_space_nfrag_all.png)

Beside changing the physical initial conditions, we test the potential impact on the number of observed fragments due to a variation of the numerical prescriptions for the luminosity accretion factor ($f_{\textrm{acc}}$). The efficiency of the accretion affects both the thermal feedback from accretion processes and the total luminosity of each sink. The test is conducted at an intermediate evolutionary step of the *M1000\_$\mu$100\_$\mathcal{M}$7_1* realization. In our suite of simulations RS1.0, we compute the accretion luminosity using a fixed factor of 0.1. To further investigate the impact of this parameter on the number of detected fragments, we explore four additional values of $f_{\textrm{acc}}$: 0.01, 0.05, 0.5, and 1, respectively. These values represent a broad range of possible luminosity accretion conditions. As a first test, we change $f_{\textrm{acc}}$ in the radiative transfer calculations, using the POLARIS[^12] code (cite: Reissl+2016; Reissl+2018) to calculate the temperature and the resulting intensity maps. As the variation of the $f_{\textrm{acc}}$ parameter is introduced only in the radiative transfer phase rather than in the underlying RMHD simulation, it does not directly change the fragmentation of the clumps and the number of sinks. Rather, it modifies our ability to detect the fragments at a resolution of $\sim7000$ AU that may correspond to those sinks.\
As shown in Fig. [16](#fig:nfrag_vs_facc), we observe a slight change in the number of fragments as the $f_{\textrm{acc}}$ parameter is varied. Specifically, higher values of $f_{\textrm{acc}}$ (i.e., 0.5 and $1$) lead to slightly more fragments being detected compared to the lower and intermediate values. This suggests that increased luminosity from accretion luminosity contributes to the identification of $\sim 7000$ AU fragments. We also find that lowering $f_{\textrm{acc}}$ primarily affects the total luminosity of the low-mass sinks, which derive most of their luminosity from accretion luminosity (in contrast to high-mass sinks which are dominated by internal luminosity). As a consequence, in the CASA post-processed images we still detect fragments associated with high-mass stars, while it becomes more challenging to recover the population of the faintest sources linked to lower-mass sinks. Despite the observed variation in the number of fragments, the accretion luminosity factor does not appear to be the primary factor affecting the recovered fragments multiplicity in this context.\
Although the low fragmentation cases are not reproduced within the current simulated parameter space, the outputs from both the control models and the RS1.0 grid help refine the initial conditions and the numerical assumptions for our simulations, guiding future investigations.

![](images/nfrag_vs_facc.png)

[^1]: alice.nucara@inaf.it

[^2]: <https://www.the-rosetta-stone-project.eu>

[^3]: From now on, we refer to groups of realizations that share a common initial parameter. For example, we use *M500* for the realizations starting with a 500 M$_\odot$ clump. The same criterion is used to indicate a specific model, as in *M1000\_$\mu$10\_$\mathcal{M}$7_S2*, which is the representative model in Fig. [2](#fig:postprocessing_sequence).

[^4]: Interferometers measure visibilities, a quantity obtained from the interference pattern formed by combining signals from different antennas.

[^5]: <https://casadocs.readthedocs.io/en/v6.5.4/api/tt/casatasks.simulation.simalma.html?highlight=simalma>

[^6]: <https://casadocs.readthedocs.io/en/v6.5.4/api/tt/casatasks.simulation.simobserve.html?highlight=simobserve>

[^7]: <https://casadocs.readthedocs.io/en/v6.5.4/api/tt/casatasks.imaging.tclean.html?highlight=tclean>

[^8]: The latest Python-based version of the *Hyper* code is available at: <https://github.com/Alessio-Traficante/hyper-py>.

[^9]: Semi-minor/major axes correspond to the *Hyper* parameters full width at half maximum: FWHM_MIN and FWHM_MAX, respectively.

[^10]: In our prescription, the merging of sink particles is not allowed. Consequently, the number of sink particles can never decrease.

[^11]: Here, we specifically define cores as units that will eventually form a single protostar or a small-multiplicity system.

[^12]: POLARIS is not the main software used in the RS1.0 pipeline, but it has been used to carry out this specific test. Before running the test, we have ensured that outputs from the two codes are comparable: POLARIS recovers about 96% of the total RADMC-3D emission from the box at 1.3 mm. We therefore expect the following results to be representative of the same analysis conducted by using RADMC-3D.

</paper>

## Items to check

```json
[
 {
  "path": "analysis_steps[4].method.evidence[0]",
  "value": "Convert integrated 1.3 mm fluxes to fragment masses using optically thin dust emission equation and single-temperature model based on clump L/M, estimate temperature uncertainties via 1000 MC runs, compute FFE and 2D distance matrices (d_min,2D, d_max,2D), and cross-match fragment footprints with 3D/2D projected RAMSES sink particles",
  "failed_quote": "The distribution of mass of the fragments was obtained by converting fluxes into masses as follows ((cite: 1983QJRAS..24..267H)): $M_f=\\dfrac{D^2 S_{1.3}}{B_{1.3}(T_f) \\kappa_{1.3}}\\,,$"
 },
 {
  "path": "claims[2].evidence[1]",
  "value": "Fragments at ~7000 AU do not correspond one-to-one with forming stars; most host multiple sinks due to hierarchical multi-scale fragmentation, while about a quarter are not actively forming stars at that time step.",
  "failed_quote": "$\\sim75$% of the identified fragments have a correspondence with sink particles. Only $\\sim 17$% of the total are associated with a single sink particle; $\\sim25$% of the identified fragments do not correspond to any sink particle."
 }
]
```
