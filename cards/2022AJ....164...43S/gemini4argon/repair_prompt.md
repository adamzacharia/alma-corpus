# Repair task for a Claude Code subagent

A methods card has evidence quotes that were not found verbatim in the paper. Below are the rules, the paper, and the failing items. Write ONE JSON object, nothing else, of the form {"repairs": [{"path": ..., "found": true|false, "loc": ..., "quote": ...}, ...]} with one entry per item (path unchanged) to:

    C:\Users\adama\alma-corpus\cards\2022AJ....164...43S\gemini4argon\repair_reply.txt

Use the Write tool for that file. Copy each quote character for character from the paper text below; a returned quote is checked mechanically and dropped if it is not in the paper. Do not read any other file, do not run commands, and do not change anything else. Reply with one line when done.

---

## Rules

You check evidence quotes for a methods card extracted from an astronomy paper. Some quotes could not be found verbatim in the paper text, and some stated values came without a quote. For each item: find the passage in the paper that supports the value and copy it VERBATIM (same words and order, at most 40 words; LaTeX markup may be dropped) with its loc (section heading, "abstract", "Table N" or "Figure N caption"). If the paper does not support the value, return found = false and leave quote and loc empty. Use only the paper text. Return one entry per item, with the item's path unchanged.

## Paper

<paper>
# Molecular Cloud Populations in the Context of Their Host Galaxy Environments:\
A Multiwavelength Perspective

## Abstract

We present a rich, multiwavelength, multiscale database built around the PHANGS–ALMA $\mathrm{CO}\,(2\text{--}1)$ survey and ancillary data. We use this database to present the distributions of molecular cloud populations and sub-galactic environments in 80 PHANGS galaxies, to characterize the relationship between population-averaged cloud properties and host galaxy properties, and to assess key timescales relevant to molecular cloud evolution and star formation. We show that PHANGS probes a wide range of kpc-scale gas, stellar, and star formation rate (SFR) surface densities, as well as orbital velocities and shear. The population-averaged cloud properties in each aperture correlate strongly with both local environmental properties and host galaxy global properties. Leveraging a variable selection analysis, we find that the kpc-scale surface densities of molecular gas and SFR tend to possess the most predictive power for the population-averaged cloud properties. Once their variations are controlled for, galaxy global properties contain little additional information, which implies that the apparent galaxy-to-galaxy variations in cloud populations are likely mediated by kpc-scale environmental conditions. We further estimate a suite of important timescales from our multiwavelength measurements. The cloud-scale free-fall time and turbulence crossing time are ${\sim}5{-}20$ Myr, comparable to previous cloud lifetime estimates. The timescales for orbital motion, shearing, and cloud–cloud collisions are longer, ${\sim}100$ Myr. The molecular gas depletion time is $1{-}3$ Gyr and shows weak to no correlations with the other timescales in our data. We publish our measurements online and expect them to have broad utility to future studies of molecular clouds and star formation.

# Introduction

Molecular clouds are deeply integrated with their host galaxies by a number of intertwined physical processes. The gas distribution, gravitational potential, radiation field, and feedback-driven flows in the host galaxy regulate molecular cloud formation and evolution (cite: Dobbs_etal_2014; Ballesteros-Paredes_etal_2020). The internal structure and dynamical properties of these clouds in turn set the initial conditions for star formation, which over time reshapes the matter and radiation distribution in the galaxy (cite: McKee_Ostriker_2007; Padoan_etal_2014; Klessen_Glover_2016; Girichidis_etal_2020). These complex interactions lead to strong, observable correlations between the properties of molecular clouds and the local and global properties of the host galaxy. Characterizing these cloud–environment correlations is thus a promising avenue for understanding the physics governing molecular cloud evolution and, consequently, star formation and galaxy evolution.

Observations of molecular clouds in our Galaxy and a number of nearby galaxies have identified various empirical trends manifesting such cloud–environment correlations. Within a galaxy, molecular clouds located closer to the galaxy center appear denser, more massive, and more turbulent (cite: Oka_etal_2001; Colombo_etal_2014a; Freeman_etal_2017; Hirota_etal_2018; Miura_etal_2018; Brunetti_etal_2021). Similar trends have been found in galaxy-scale numerical simulations (cite: Pan_etal_2015a; Jeffreson_etal_2020; Tress_etal_2020b). Recent observational works also report that more massive and actively star-forming galaxies tend to host clouds with typically larger sizes, masses, surface densities, and velocity dispersions (cite: Hughes_etal_2013a; Leroy_etal_2015a; Leroy_etal_2016; Schruba_etal_2019; Sun_etal_2020a).

To proceed from the existing empirical knowledge to more concrete understandings of the cloud–environment correlations, major advances on two issues are necessary. First, the characterization of environmental dependence often stops at a qualitative level in the molecular cloud literature: the “environments” are commonly defined in crude, categorical ways (e.g., galaxy centers, stellar bars, spiral arms), and they are merely considered as a secondary, moderating factor on the scaling relations followed by molecular clouds. To better understand the underlying physics, a more direct approach would be to quantify the dependence of molecular cloud properties on a set of quantitative “environmental metrics,” such as the local gas and stellar mass surface density, star formation rate (SFR) surface density, and orbital shear (cite: Hughes_etal_2013a; Schruba_etal_2019). Second, many previous works (especially earlier ones) had to rely on observations in a small number of galaxies or sub-galactic regions, and thus only probed a limited range of host galaxy properties. While such case studies could yield unique insights for specific targets, only systematic surveys across large galaxy samples can cover a wide, continuous range of host galaxy properties, produce representative population statistics, and make meaningful connections to galaxy evolution models.

The PHANGS–ALMA survey (cite: Leroy_etal_2021a) was designed to address both of these issues. This survey provides sensitive, high resolution, wide field-of-view $\mathrm{CO}\,(2\text{--}1)$ imaging data for ${\sim}90$ nearby, high-mass, star-forming galaxies. With these galaxies sampled uniformly along the star-forming main sequence, PHANGS–ALMA enables systematic studies of giant molecular clouds (GMCs; $M \gtrsim 10^5~\mbox{$\rm M_\odot$}$) across an array of environments where most stars form in the local universe. Furthermore, a rich set of multiwavelength ancillary data furnishes a multifaceted depiction of these host galaxies, making it possible to study their molecular cloud populations in full environmental context.

Indeed, one of the core science goals that motivated the PHANGS–ALMA survey was to characterize the dependence of molecular cloud populations on global and local galaxy properties. Studies on this data set have presented population statistics for key molecular cloud properties such as mass, size, surface density, velocity dispersion, and virial parameter (cite: Sun_etal_2018; Sun_etal_2020a; Rosolowsky_etal_2021). They also noted significant variations among galaxies and across morphological regions within galaxies (e.g., centers, bars). In the direct predecessor of this paper, (cite: Sun_etal_2020b) conducted a joint analysis on the PHANGS–ALMA CO data and multiwavelength ancillary data. They showed that the variations in molecular gas turbulent pressure can be attributed to the dynamical balance between gravity and internal/\
\[0\]external pressure in the gas, as previously argued in Galactic and extragalactic molecular cloud studies (cite: Field_etal_2011; Hughes_etal_2013a; Schruba_etal_2019).

In this paper, we directly address this core science goal of the PHANGS–ALMA survey. We build on a cross-spatial-scale analysis framework used by (cite: Sun_etal_2020b) and calculate population statistics for the molecular cloud properties measured in (cite: Sun_etal_2018; Sun_etal_2020a; Rosolowsky_etal_2021); and A. Hughes et al. (in preparation). We further cross-match them with a large suite of environmental metrics depicting the local gas and stellar mass distribution, orbital kinematics, morphological structures, and star formation activities in the host galaxy. This allows us to (1) present the full range of cloud populations and host galaxy environments captured by PHANGS–ALMA, (2) delineate the quantitative relationships between cloud characteristics (e.g., mass, surface density, velocity dispersion) and environmental metrics (e.g., gas, star, and SFR surface densities), and (3) identify a subset of relationships that carry unique explanatory/predictive power among all the observed cloud–environment correlations.

Another goal of this paper is to present a set of machine-readable data tables that consolidate all the aforementioned measurements from PHANGS-ALMA and ancillary surveys. These high-level data products have already been used in a number of studies. (cite: Herrera_etal_2020) and (cite: Barnes_etal_2021) have utilized previous versions of these tables to quantitatively assess several physical mechanisms relevant to molecular cloud and H II  region evolution, including stellar feedback and pressure balance. Several ongoing works also rely on these tables to calculate the star formation efficiency and its link to small-scale turbulence, orbital shear, and disk instabilities (E. Rosolowsky et al. in preparation; J. Sun et al. in preparation; T. Williams et al. in preparation). In this paper, we also utilize the measurements in these tables to calculate a suite of characteristic timescales related to the gravity, turbulent motions, orbital motions, and star formation rate of molecular clouds. The ratios among these timescales provide unique constraints on the viable mechanisms regulating molecular cloud evolution and star formation (cite: Wong_2009; Jeffreson_Kruijssen_2018; Kruijssen_etal_2019b; Chevance_etal_2020a; Chevance_etal_2020b; KimJY_etal_2020).

The structure of this paper is as follows. Section [2](#sec:data) describes our galaxy sample and the sources of all data we use. Section [3](#sec:analysis) elaborates the cross-spatial-scale analysis framework we use to assemble the multiwavelength measurements into a coherent data structure. Section [4](#sec:stats) presents the distribution of various molecular cloud population properties and sub-galactic environmental properties measured in this work, and Section [5](#sec:corr) characterizes the correlations between these two types of measurements. To demonstrate an application scenario of our rich multiwavelength measurements, Section [6](#sec:timescales) presents a set of characteristic timescales relevant to molecular cloud evolution and star formation. Finally, Section [7](#sec:summary) summarizes all our findings.

# Data

In this paper, we focus on a sample of 80 galaxies (see Table [\[tab:sample\]](#tab:sample)) selected from the full PHANGS–ALMA survey sample (cite: Leroy_etal_2021a). We select these galaxies according to two criteria: (1) their PHANGS–ALMA $\mathrm{CO}\,(2\text{--}1)$ observations have beam full-width-half-maximum (FWHM) sizes corresponding to physical scales of $150$ pc or smaller, so that each beam roughly probes a GMC-sized molecular gas structure; and (2) they are not too heavily inclined ($i \lesssim 75^\circ$), so that we can unambiguously determine the locations of molecular clouds in the host galaxy. A subset of 28 galaxies in this sample already appeared in (cite: Sun_etal_2020b), where they utilized earlier versions of the same observational data sets and data analysis infrastructure.

In addition to the PHANGS–ALMA CO data, our target galaxies have abundant multiwavelength coverage, including radio, mid-/\
\[0\]near-infrared (MIR/NIR), optical, and near-/\
\[0\]far-ultraviolet (NUV/FUV) data (Sections [2.2](#sec:data:HI), [2.3](#sec:data:NIR), [2.4](#sec:data:z0MGS), and [2.7](#sec:data:other)). High-level measurements such as CPROPS object catalogs created from CO data cubes (cite: Rosolowsky_etal_2021), rotation curves derived from CO line kinematics (cite: Lang_etal_2020), and morphological feature masks constructed from near-IR images (cite: Querejeta_etal_2021) are also available for most targets (Sections [2.1.1](#sec:data:CO:obj), [2.5](#sec:data:rotcurve), and [2.6](#sec:data:environ)). These rich ancillary data provide us with comprehensive information about the multiphase ISM, stellar disk structures, star formation, and galactic dynamical properties on $\lesssim\,$kpc scales for our target galaxies.

In the following subsections, we detail the sources and characteristics of all raw data and high-level data products used in this study. We provide a schematic summary of these input data at the top of Figure [1](#fig:schematic).

## PHANGS–ALMA CO Data

We use the PHANGS–ALMA $\mathrm{CO}\,(2\text{--}1)$ imaging data[^1] (cite: Leroy_etal_2021a) to probe molecular gas properties on ${\lesssim}150$ pc scales. These data cover the actively star-forming area in each galaxy (${\sim}100$ kpc$^2$ on average) and have sufficient depth and resolving power to detect and isolate the CO emission from individual GMCs (with a typical mass of $\gtrsim 10^5~\mathrm{M}_\odot$). They include both interferometric and single dish observations and thus provide sensitivity to emission on all spatial scales. We refer interested readers to (cite: Leroy_etal_2021a) for more details regarding sample selection, observational setup, and data product characteristics, and (cite: Leroy_etal_2021b) for an in-depth description of data calibration, imaging, and product creation procedures.

In this study, we measure properties of molecular cloud populations from the PHANGS–ALMA CO data using two different approaches. The first approach measures molecular gas properties “object-by-object.” In this case, the objects of interest are identified by applying the cloud segmentation algorithm CPROPS to the PHANGS–ALMA CO data cubes (cite: Rosolowsky_Leroy_2006; Rosolowsky_etal_2021). The second approach treats the molecular gas as a spatially continuous medium and extracts measurement in a “pixel-by-pixel” fashion directly from the PHANGS–ALMA CO line moment maps, where the beam size corresponds roughly to the typical size of an individual GMC or giant molecular association (cite: Leroy_etal_2016; Sun_etal_2018; Sun_etal_2020a).

While the two approaches access similar physical properties and often lead to similar results (cite: Sun_etal_2020a; Rosolowsky_etal_2021), they complement each other in important ways. The object-by-object approach treats each identified object as a fundamental structural unit, and by providing size estimates for these objects it probes the spatial organization of molecular gas. The pixel-by-pixel method instead treats each resolution element as a fundamental unit, which preserves information from the smallest recoverable scale while remaining agnostic about the organization of the gas on larger scales. When presenting our measurements in Section [4](#sec:stats), we compare the two approaches to illustrate how methodological choices could influence the main results.

### Object-by-object Measurements

We extract a set of molecular gas measurements for each object tabulated in the PHANGS–ALMA CPROPS catalogs[^2] (cite: Rosolowsky_etal_2021). These catalogs are constructed by running CPROPS (cite: Rosolowsky_Leroy_2006) on data cubes at a set of common spatial resolutions (60, 90, 120, and 150 pc whenever available). Note that A. Hughes et al. (in preparation) present two versions of CPROPS catalogs for the PHANGS-ALMA sample: one is constructed from data cubes whose noise levels are homogenized among all galaxies, and the other from data cubes with the native noise. We use the latter version in this paper, because (a) we would like to compare the object-by-object measurements to the corresponding pixel-by-pixel ones, which were derived from the original data cubes without noise homogenization; and (b) we would like to recover as much CO emission above the noise floor as possible.

For each object identified by the CPROPS algorithm, the catalog records its integrated CO line luminosity, $L_\mathrm{CO,\,obj}$, CO line width, $\sigma_\mathrm{CO,\,obj}$, and the two-dimensional projected radius on the sky[^3], $R_\mathrm{2D,\,obj}$. These numbers are calculated after radially extrapolating each object to a hypothetical boundary at 0 K brightness temperature and then deconvolving the beam size and channel width. From these basic observables, we estimate the following physical properties for each object:

- *Molecular gas mass, $M_\mathrm{obj}$*. This is derived from the integrated $\mathrm{CO}\,(2\text{--}1)$ line luminosity $L_\mathrm{CO,\,obj}$ (in units of $\rm K~km~s^{-1}~pc^2$) via $$\begin{equation}
  M_\mathrm{obj} = \alpha_\mathrm{CO(1\text{--}0)}R_\mathrm{21}^{-1}L_\mathrm{CO,\,obj}~.
  \label{eq:M_obj}
  \end{equation}$$ Here $R_\mathrm{21}=0.65$ is the adopted $\mathrm{CO}\,(2\text{--}1)$ to $\mathrm{CO}\,(1\text{--}0)$ line ratio (cite: denBrok_etal_2021; Leroy_etal_2021c), and $\alpha_\mathrm{CO(1\text{--}0)}$ is a varying CO-to-$\mathrm{H}_2$ conversion factor for the $\mathrm{CO}\,(1\text{--}0)$ line. By default, we use a metallicity-dependent $\alpha_\mathrm{CO}$ prescription as described in (cite: Sun_etal_2020b): $$\begin{equation}
  \alpha_\mathrm{CO(1\text{--}0)} = 4.35~Z^\mathrm{\prime-1.6}~\mathrm{M_\odot~(\mbox{$\rm K~km~s^{-1}$}~pc^2)^{-1}}~.
  \label{eq:alphaCO}
  \end{equation}$$ Here, $Z'$ is the inferred local gas phase abundance normalized to the solar value (see Section [3.3](#sec:analysis:env)). While we use Equation [\[eq:alphaCO\]](#eq:alphaCO) as our fiducial prescription, we also calculate $\alpha_\mathrm{CO}$ using several alternative prescriptions and include them in the data products (see Appendix [9](#apdx:alphaCO)).

- *Molecular gas surface density, $\Sigma_\mathrm{obj}$*. This is derived from $M_\mathrm{obj}$ and $R_\mathrm{2D,\,obj}$ via $$\begin{equation}
  \Sigma_\mathrm{obj}
  = \frac{\onehalf M_\mathrm{obj}}{\pi R_\mathrm{2D,\,obj}^2}\cos{i}
  = \frac{M_\mathrm{obj}}{2\pi R_\mathrm{2D,\,obj}^2}\cos{i}~.
  \label{eq:Sigma_obj}
  \end{equation}$$ Following (cite: Rosolowsky_etal_2021), this estimate assumes a two-dimensional Gaussian profile for the projected gas mass distribution and focuses on the area within a FWHM, which includes half of the total gas mass. The $\cos{i}$ term accounts for galaxy inclination (see Table [\[tab:sample\]](#tab:sample)) by correcting the derived surface densities to face-on projection. This correction was not present in the formulae used by (cite: Rosolowsky_etal_2021) and previous similar work. We motivate this correction in Appendix [10](#apdx:inclination).

- *One-dimensional velocity dispersion, $\sigma_\mathrm{obj}$*. This is derived from the measured CO line width $\sigma_\mathrm{CO,\,obj}$ via $$\begin{equation}
  \sigma_\mathrm{obj}
  = \sigma_\mathrm{CO,\,obj}(\cos{i})^{0.5}~.
  \label{eq:vdisp_obj}
  \end{equation}$$ Here $\sigma_\mathrm{CO,\,obj}$ comes from the second moment (moment-2) of the CO line profile and is corrected for broadening due to the line spread function (cite: Rosolowsky_etal_2021). The extra $(\cos{i})^{0.5}$ term is an empirically determined correction that accounts for the dependence of the observed CO line width on galaxy inclination. Appendix [10](#apdx:inclination) details the origin of this term and the rationale for including it here.

  In the following discussions, we will assume that $\sigma_\mathrm{obj}$ is dominated by turbulent motions, though this measurement will include additional contributions from thermal or ordered, streaming motions. Fundamentally, it reflects the velocity dispersion along the line of sight direction within each object.

- *Three-dimensional mean radius, $R_\mathrm{obj}$*. This quantity is inferred from $R_\mathrm{2D,\,obj}$ via $$\begin{equation}
  R_\mathrm{obj} = 
  \mathrm{min}\!\left[ R_\mathrm{2D,\,obj}, \sqrt[3]{R_\mathrm{2D,\,obj}^2\frac{H}{2\cos{i}}}\,\right]~.
  \label{eq:R_obj}
  \end{equation}$$ Here $H=100$ pc is an assumed molecular gas disk thickness perpendicular to the galaxy plane (cite: Heyer_Dame_2015), and $\frac{H}{\cos{i}}$ would be the expected line-of-sight depth given the disk inclination. Equation [\[eq:R_obj\]](#eq:R_obj) assumes a spheroidal geometry when the object diameter on the sky exceeds this line-of-sight depth, and a spherical geometry otherwise. This is similar to the treatments in (cite: Rosolowsky_etal_2021), except that here we also correct for galaxy inclination (also see Appendix [10](#apdx:inclination)).

  Our adopted value for $H$ is likely uncertain by a factor of ${\sim}\,2$ due to variations within a galaxy and among galaxies (cite: Yim_etal_2014; Bacchini_etal_2019a). Systematic trends with galactocentric radius and global galaxy mass are also expected. A fixed value of $H=100$ pc cannot capture these variations, which means that our inferred $R_\mathrm{obj}$ values (and any measurements that rely on them, see bullet points below) are affected accordingly. Nevertheless, the functional form of Equation [\[eq:R_obj\]](#eq:R_obj) suggests that at most $1/3$ of the fractional uncertainty on $H$ will propagate to $R_\mathrm{obj}$, which would only be marginally significant in comparison to other sources of systematic uncertainties (see discussions in Section [4.2](#sec:stats:MC) and Appendix [12](#apdx:scale)).

- *Turbulent pressure, $P_\mathrm{turb,\,obj}$*. This is derived from $M_\mathrm{obj}$, $\sigma_\mathrm{obj}$, and $R_\mathrm{obj}$ via $$\begin{equation}
  P_\mathrm{turb,\,obj}
  \equiv \rho_\mathrm{obj}\sigma_\mathrm{obj}^2
  = \frac{\onehalf M_\mathrm{obj}}{\frac{4}{3}\pi R_\mathrm{obj}^3}\sigma_\mathrm{obj}^2
  = \frac{3M_\mathrm{obj}\sigma_\mathrm{obj}^2}{8\pi R_\mathrm{obj}^3}~.
  \label{eq:Pturb_obj}
  \end{equation}$$ Here the mean density $\rho_\mathrm{obj}$ is derived from $R_\mathrm{obj}$ and the mass within the FWHM of a two-dimensional Gaussian profile (cite: Rosolowsky_etal_2021).

- *Virial parameter, $\alpha_\mathrm{vir,\,obj}$*. This is derived from $M_\mathrm{obj}$, $\sigma_\mathrm{obj}$, and $R_\mathrm{obj}$ via $$\begin{equation}
  \alpha_\mathrm{vir,\,obj}
  \equiv \frac{2E_\mathrm{kin}}{|E_\mathrm{grav}|}
  = \frac{5\,\sigma_\mathrm{obj}^2R_\mathrm{obj}}{G(\onehalf M_\mathrm{obj})}
  = \frac{10\,\sigma_\mathrm{obj}^2R_\mathrm{obj}}{GM_\mathrm{obj}}~.
  \label{eq:alphavir_obj}
  \end{equation}$$ This formula is derived by calculating the kinetic energy ($E_\mathrm{kin}$) and gravitational potential energy ($E_\mathrm{grav}$) for the gas within the two-dimensional FWHM size, assuming a uniform density distribution (cite: Rosolowsky_etal_2021). With this definition, a virialized object would have $\alpha_\mathrm{vir,\,obj}=1$, whereas an object in energy equipartition would have $\alpha_\mathrm{vir,\,obj}=2$. But we note that the virial parameter estimated in this way might not be a complete description of cloud dynamical states if there are strong magnetic field, surface pressure, or external tidal forces (cite: Ballesteros-Paredes_2006; Sun_etal_2020b; KimJG_etal_2020; LiuLJ_etal_2021).

### Pixel-by-pixel Measurements

As an alternative to the object-by-object approach, we also derive molecular gas properties at fixed spatial resolutions (60, 90, 120, and 150 pc whenever available) measured pixel-by-pixel from the PHANGS–ALMA CO moment maps (cite: Sun_etal_2018; Sun_etal_2020a). The PHANGS-ALMA data reduction pipeline (cite: Leroy_etal_2021b) produces two versions of moment maps: a “broad” version that prioritizes high CO flux completeness through highly inclusive signal masking, and a “strict” version that features high signal-to-noise (S/N) CO line moment measurements thanks to more restrictive masking. For our pixel-by-pixel analysis, we primarily use the “strict” moment maps so that only pixels with reliable measurements are included in our calculation. To account for the lower CO flux completeness of the “strict” maps, we later estimate their flux completeness by comparing the “strict” and “broad” maps, and further correct for sensitivity-induced biases (see Section [3.2.2](#sec:analysis:cloud:completeness)).

The “strict,” beam-matched moment maps provide CO line integrated intensity (moment-0), $I_\mathrm{CO,\,pix}$, CO line effective width (cite: Heyer_etal_2001), $\sigma_\mathrm{CO,\,pix}$, and their associated uncertainties for every pixel with detected CO emission. From these basic observables, we derive a set of molecular gas physical properties mirroring those from the object-by-object approach, and estimate their statistical uncertainties through Gaussian error propagation:

- *Molecular gas surface density, $\Sigma_\mathrm{pix}$*. This quantity is derived from the integrated $\mathrm{CO}\,(2\text{--}1)$ line intensity $I_\mathrm{CO,\,pix}$ (in units of $\rm K~km~s^{-1}$) for each pixel, via $$\begin{equation}
  \Sigma_\mathrm{pix} = \alpha_\mathrm{CO(1\text{--}0)}R_\mathrm{21}^{-1}I_\mathrm{CO,\,pix}\cos{i}~.
  \label{eq:Sigma_pix}
  \end{equation}$$ Here $R_\mathrm{21}$ and $\alpha_\mathrm{CO(1\text{--}0)}$ represent the adopted CO line ratio and $\mathrm{CO}\,(1\text{--}0)$-to-$\mathrm{H}_2$ conversion factor as in Equation [\[eq:M_obj\]](#eq:M_obj). The same $\cos{i}$ inclination correction from Equation [\[eq:Sigma_obj\]](#eq:Sigma_obj) also applies here.

- *Molecular gas mass, $M_\mathrm{pix}$*. We also record the total molecular gas mass captured in each beam[^4] via $$\begin{align}
  M_\mathrm{pix}
  &= \alpha_\mathrm{CO(1\text{--}0)}R_\mathrm{21}^{-1}I_\mathrm{CO,\,pix}A_\mathrm{beam}~.
  \label{eq:M_pix}
  \end{align}$$ Here $A_\mathrm{beam}=(\pi/4\ln{2})D_\mathrm{beam}^2$ is the effective area of the beam with a FWHM of $D_\mathrm{beam}$ (i.e., 60, 90, 120, or 150 pc). No inclination correction is required here since both $I_\mathrm{CO,\,pix}$ and $A_\mathrm{beam}$ are measured/defined in the projected plane of the sky.

- *One-dimensional velocity dispersion, $\sigma_\mathrm{pix}$*. This quantity is derived from the LSF-corrected CO line width $\sigma_\mathrm{CO,\,pix}$ in each pixel and uses the same inclination correction as Equation [\[eq:vdisp_obj\]](#eq:vdisp_obj): $$\begin{equation}
  \sigma_\mathrm{pix}
  = \sigma_\mathrm{CO,\,pix}(\cos{i})^{0.5}~.
  \label{eq:vdisp_pix}
  \end{equation}$$ Here $\sigma_\mathrm{CO,\,pix}$ represents the CO line *effective width*, which is a different line width metric than the one based on the second moment used in Equation [\[eq:vdisp_obj\]](#eq:vdisp_obj). The effective width is a more robust line width metric than moment-2 at low S/N, but it could give biased results when there are multiple velocity components along the line of sight (cite: Henshaw_etal_2020).

- *Three-dimensional mean radius, $R_\mathrm{pix}$*. We adopt the following three-dimensional size for the gas structure captured in each beam, mirroring Equation [\[eq:R_obj\]](#eq:R_obj): $$\begin{equation}
  R_\mathrm{pix} = \mathrm{min}\!\left[\frac{D_\mathrm{beam}}{2},\,\sqrt[3]{\frac{D_\mathrm{beam}^2H}{8\cos{i}}}\,\right]~.
  \label{eq:R_pix}
  \end{equation}$$ Again, the $\cos{i}$ term accounts for galaxy inclination by converting the molecular gas disk thickness (perpendicular to the galaxy plane) to the depth along the line of sight. Note that Equation [\[eq:R_pix\]](#eq:R_pix) yields a single $R_\mathrm{pix}$ value for each given beam size.

- *Turbulent pressure, $P_\mathrm{turb,\,pix}$*. This is derived from $\Sigma_\mathrm{pix}$ and $\sigma_\mathrm{pix}$ via $$\begin{equation}
  P_\mathrm{turb,\,pix}
  \equiv \rho_\mathrm{pix}\sigma_\mathrm{pix}^2
  = \frac{3M_\mathrm{pix}\sigma_\mathrm{pix}^2}{4\pi R_\mathrm{pix}^3}~.
  \label{eq:Pturb_pix}
  \end{equation}$$ This assumes that the gas mass captured in each beam is uniformly distributed within a radius of $R_\mathrm{pix}$. This is consistent with the geometrical assumptions adopted in previous studies (cite: Sun_etal_2020b), yet it leads to an inconsistency with the object-based approach (Equation [\[eq:Pturb_obj\]](#eq:Pturb_obj)). We comment on this issue in Section [2.1.3](#sec:data:CO:notes).

- *Virial parameter, $\alpha_\mathrm{vir,\,pix}$*. This is derived from $\Sigma_\mathrm{pix}$ and $\sigma_\mathrm{pix}$ via $$\begin{equation}
  \alpha_\mathrm{vir,\,pix}
  \equiv \frac{2E_\mathrm{kin}}{|E_\mathrm{grav}|}
  = \frac{5\,\sigma_\mathrm{pix}^2R_\mathrm{pix}}{GM_\mathrm{pix}}~.
  \label{eq:alphavir_pix}
  \end{equation}$$ This also assumes a spherical geometry and a uniform density distribution within $R_\mathrm{pix}$. Similar to the situation with our turbulent pressure estimates, the geometrical assumptions here are not fully consistent with those adopted for the object-based analysis (see Section [2.1.3](#sec:data:CO:notes) for further comments).

### Notes on the Common Grounds and Differences between the Object-based and Pixel-base Approaches

The object-based and pixel-based approaches show an apparent symmetry, in the sense that they have many measured quantities in common, such as molecular gas surface density, velocity dispersion, turbulent pressure, and virial parameter. This allows us to make direct comparisons between the two approaches and assess how our methodological choices might influence the quantitative results. However, it is worth emphasizing that, for several reasons, we do not necessarily expect the two approaches to yield exactly the same quantitative results.

First and foremost, the two approaches are motivated by two slightly different views for the structure and geometry of the molecular ISM in galaxies. The object-based approach views the molecular ISM as a collection of dense, centrally concentrated structures, and the central goal of the CPROPS algorithm is to segment the observed CO emission distribution such that each identified CO-emitting object corresponds to a coherent structure like a GMC or a giant molecular association. The pixel-based approach instead views the molecular ISM as a continuous distribution of gas while being agnostic about its spatial clustering, and the measurement process simply characterizes the gas captured in each beam. In a sense, the two approaches see the same observational data through different lenses, and each attempts to extract measurable properties in a way that is most consistent with its adopted view.

Reflecting these different views, there are also important, practical differences in the methodologies between these two approaches, which make it non-trivial to draw direct comparisons between them. In particular, the object-based approach aims to measure the true size and mass of each identified object by deconvolving the beam and extrapolating the detected part of each object to a hypothetical boundary at 0 K brightness temperature. Such operations could in principle account for biases due to the finite resolution and sensitivity of the observations, but they are implicitly model-dependent and not easily adaptable to fit the pixel-based approach.

The distinct physical models underlying these two approaches are also reflected in the different auxiliary assumptions they adopt when calculating physical quantities. The object-based approach assumes compact, Gaussian-shaped gas distributions and calculate gas surface density, turbulent pressure, and virial parameter for only the half of the gas located within the Gaussian FWHM (Equations [\[eq:Sigma_obj\]](#eq:Sigma_obj)–[\[eq:alphavir_obj\]](#eq:alphavir_obj), consistent with (cite: Rosolowsky_etal_2021)). In contrary, the pixel-based approach considers all the gas mass detected in each beam and assumes it is uniformly distributed within the beam area (Equations [\[eq:Pturb_pix\]](#eq:Pturb_pix)–[\[eq:alphavir_pix\]](#eq:alphavir_pix), in line with (cite: Sun_etal_2018; Sun_etal_2020a)).

Considering these complications, we do not necessarily expect the two approaches to agree in their quantitative results, even though we start from the same CO data cubes and attempt to define measurable properties in a symmetric way.

##  H I Data

We use interferometric H I  21 cm line data to trace the distribution of neutral atomic gas in each galaxy. These include both new and archival observations taken by the Karl G. Jansky Very Large Array (VLA) and the Australia Telescope Compact Array (ATCA).

Among the 53 galaxies with H I  data (see Table [\[tab:sample\]](#tab:sample)), 20 have been observed as part of the PHANGS–VLA survey (A. Sardone et al. in preparation). The other galaxies have archival data from either large nearby galaxy surveys such as THINGS (cite: Walter_etal_2008), VIVA (cite: Chung_etal_2009), HERACLES (cite: Leroy_etal_2009), LVHIS (cite: Koribalski_etal_2018), EveryTHINGS (two galaxies; I. Chiang et al. in preparation), or individual case studies with the VLA (seven galaxies) and the ATCA (cite: Murugeshan_etal_2019). These H I  data sets have typical angular resolution of $15\ensuremath{''}{-}35\ensuremath{''}$ ($16{-}84$ percentile), which corresponds to linear scales of $0.7{-}2.8$ kpc (see Section [3.3](#sec:analysis:env) for further discussions about H I  data resolution). The $3\sigma$ sensitivity limit ranges $10{-}100\;\mbox{$\rm K~km~s^{-1}$}$ for the H I  line intensity.

Assuming optically thin 21 cm emission, we convert 21 cm line intensity $I_\mathrm{21cm}$ to atomic gas surface density $\Sigma_\mathrm{atom}$ via $$\begin{equation}
    \frac{\Sigma_\mathrm{atom}}{\mbox{$\rm M_\odot~pc^{-2}$}} = 2.0\times10^{-2} \left(\frac{I_\mathrm{21cm}}{\mbox{$\rm K~km~s^{-1}$}}\right) \cos{i}~.
    \label{eq:SigHI}
\end{equation}$$ Here $\Sigma_\mathrm{atom}$ includes the (extra 35%) mass of helium and heavier elements. The $\cos{i}$ term accounts for galaxy inclination.

## Near-IR Data

We use near-IR imaging data from the *Spitzer Space Telescope* and the *Wide-field Infrared Survey Explorer (WISE)* to trace the old stellar mass distribution (see Table [\[tab:sample\]](#tab:sample), column 8). For 61 galaxies in our sample, we use *Spitzer* IRAC $3.6$ $\mu$m images from the S$^4$G survey (cite: Sheth_etal_2010). For those without S$^4$G data, we instead use *WISE* W1 band ($3.4$ $\mu$m) images compiled by the $z0$MGS project (cite: Leroy_etal_2019). All these data are postprocessed by subtracting background emission, masking foreground stars in the field of view, and convolving the non-Gaussian point spread function (PSF) to a $7.5\ensuremath{''}$ Gaussian PSF using appropriate convolution kernels (cite: Aniano_etal_2011).

We convert the stellar continuum intensity at $3.4$ $\mu$m and $3.6$ $\mu$m to stellar mass surface density, $\Sigma_\mathrm{\star}$, location-by-location via $$\begin{align}
    \frac{\Sigma_\mathrm{\star}}{\mbox{$\rm M_\odot~pc^{-2}$}} &= 350 \left(\frac{\Upsilon_{3.4\,\mu m}}{0.5}\right)\left(\frac{I_\mathrm{3.6\,\mu m}}{\mbox{$\rm MJy~sr^{-1}$}}\right) \cos{i}~, \label{eq:Sigstar_3p6um}\\
    \frac{\Sigma_\mathrm{\star}}{\mbox{$\rm M_\odot~pc^{-2}$}} &= 330 \left(\frac{\Upsilon_{3.4\,\mu m}}{0.5}\right)\left(\frac{I_\mathrm{3.4\,\mu m}}{\mbox{$\rm MJy~sr^{-1}$}}\right) \cos{i}~.
    \label{eq:Sigstar_3p4um}
\end{align}$$ Here, $\Upsilon_{3.4\,\mu m}$ is the stellar mass-to-light (M/L) ratio at $3.4$ $\mu$m, which should be nearly identical to that at $3.6$ $\mu$m. We adopt a *spatially varying* M/L ratio, which was estimated by (cite: Leroy_etal_2021a) for all PHANGS-ALMA targets based on an empirical relation between $\Upsilon_{3.4\,\mu m}$ and the local SFR surface density to $3.4$ $\mu$m surface brightness ratio.

## Mid-IR and UV Data

We use mid-IR images from *WISE* and far-/\
\[0\]near-UV images from the *Galaxy Evolution Explorer (GALEX)* to trace the distribution of obscured and unobscured star formation. These data are also compiled by the $z0$MGS project (cite: Leroy_etal_2019) and have been postprocessed by subtracting background emission, masking foreground stars, reprojecting to a shared astrometry, and then convolving to a $15\ensuremath{''}$ Gaussian PSF.

We combine the mid-IR and UV data and calculate the local star formation rate (SFR) surface density following the prescriptions described in (cite: Leroy_etal_2021a). By default we use the combination of *GALEX* FUV (154 nm) and *WISE* 22 $\mu$m data to calculate the local SFR surface density $$\begin{align}
\frac{\Sigma_\mathrm{SFR}}{\mbox{$\rm M_\odot~yr^{-1}~kpc^{-2}$}}
&= \left(8.9\times10^{-2}\,\frac{I_\mathrm{154\,nm}}{\mbox{$\rm MJy~sr^{-1}$}}\right. \nonumber\\
&\quad \left.+\,3.0\times10^{-3}\,\frac{I_\mathrm{22\,\mu m}}{\mbox{$\rm MJy~sr^{-1}$}}\right) \cos{i}~.
\label{eq:SigSFR_FUVW4}
\end{align}$$ For galaxies that do not have FUV data (see Table [\[tab:sample\]](#tab:sample), column 9), we instead combine *GALEX* NUV (231 nm) and *WISE* 22 $\mu$m data (when NUV is available) or use the *WISE* data alone (when NUV is not available either) to calculate SFR surface density $$\begin{align}
\frac{\Sigma_\mathrm{SFR}}{\mbox{$\rm M_\odot~yr^{-1}~kpc^{-2}$}}
&= \left(8.9\times10^{-2}\,\frac{I_\mathrm{231\,nm}}{\mbox{$\rm MJy~sr^{-1}$}}\right. \nonumber\\
&\quad \left.+\,2.6\times10^{-3}\,\frac{I_\mathrm{22\,\mu m}}{\mbox{$\rm MJy~sr^{-1}$}}\right) \cos{i}~,
\label{eq:SigSFR_NUVW4}\\
\frac{\Sigma_\mathrm{SFR}}{\mbox{$\rm M_\odot~yr^{-1}~kpc^{-2}$}}
&= 3.8\times10^{-3}\,\left(\frac{I_\mathrm{22\,\mu m}}{\mbox{$\rm MJy~sr^{-1}$}}\right) \cos{i}~.
\label{eq:SigSFR_W4ONLY}
\end{align}$$ These prescriptions assume a Chabrier initial mass function (cite: Chabrier_2003) via their calibration against (cite: Salim_etal_2016), which is also consistent within $\approx 5\%$ with calibrations using a Kroupa IMF (cite: Kroupa_2001). The quantitative results agree with extinction-corrected H$\alpha$-based SFR estimates from the PHANGS–MUSE survey (cite: Emsellem_etal_2021) at a ${\sim}20{-}30\%$ level overall, but there is divergence in low SFR regions due to contributions from IR cirrus and/or old stellar populations (cite: Boquien_etal_2016). We refer the reader to (cite: Leroy_etal_2021a) for more details on the calibration of these SFR prescriptions.

## Rotation Curves

We use rotation curves derived from CO line kinematics by (cite: Lang_etal_2020) to characterize galactic orbital kinematics (e.g., orbital period and shear) locally within each galaxy. These rotation curves are measured from the same PHANGS–ALMA CO data set, and therefore cover roughly the same galactocentric radius range as the CO maps themselves. They are available for 62 out of the 80 galaxies.

The rotation curves in (cite: Lang_etal_2020) are measured and recorded with finite radial bin sizes (${\sim}150$ pc). Due to the sparse distribution of CO detections across the field of view and the likely presence of unaccounted local streaming motions in the gas, the measured circular velocity sometimes fluctuates considerably between adjacent radial bins. These bin-to-bin fluctuations make it challenging to reliably estimate any parameter that depends on the derivative of the rotation curves.

To address this issue, we use a set of functional fitting models constructed from the measured rotation curves (J. Nofech et al. in preparation) rather than the raw measurements themselves. These fitting models adopt the “universal rotation curve” functional form suggested by (cite: Persic_etal_1996). The fitting process effectively forces the rotation curve models to be smooth and have physically sensible slopes (i.e., with its logarithmic derivative between -0.5 and 1), while still matching the actual measurements as closely as possible. We visually inspect all fitting results and conclude that the models represent the raw measurements reasonably well.

Based on these best-fit analytical models of the CO rotation curves and the estimated uncertainties on the model parameters, we extract at each radius the circular velocity, $V_\mathrm{circ}$, the corresponding angular velocity, $\Omega_\mathrm{circ}$, the logarithmic derivative of the rotation curve $$\begin{equation}
\beta = \frac{\mathrm{d}\ln V_\mathrm{circ}}{\mathrm{d}\ln r_\mathrm{gal}}~,
\end{equation}$$ and Oort’s $A$ parameter $$\begin{equation}
A_\mathrm{Oort}= \frac{1}{2}\Omega_\mathrm{circ}(1-\beta)~.
\end{equation}$$ These parameters (and their associated uncertainties) will be used to describe the local galactic dynamical properties at various locations within the target galaxies.

## Morphological Environment Masks

We use the environment masks presented in (cite: Querejeta_etal_2021) to distinguish different morphological regions in each galaxy. These masks are constructed based on structural decomposition analysis and visual inspection of the IRAC $3.6$ $\mu$m data (cite: Herrera-Endoqui_etal_2015; Salo_etal_2015). The full set of environment masks mark the area covered by morphological features such as galaxy centers, stellar bars, spiral arms, rings, and lenses (see the last panel in Figure [2](#fig:image)). The typical width of these environmental masks are set by the physical extent of the corresponding morphological features, which are often ${\gtrsim}\,1$ kpc wide for stellar bars and spiral arms but can be much narrower for the other features.

In this work, we primarily use these masks to divide each galaxy into two types of environment: the area that falls into galaxy centers and stellar bars (referred to as “center/bar” hereafter), and the remaining outer disk area (“disk” hereafter). We make this distinction because we expect the physical conditions influencing GMCs to be different between these two regimes: the “center/bar” environment often sees galactic dynamics (i.e., gravitational torque and shear) playing a more prominent role, and in some galaxies AGN feedback can significantly impact the molecular gas in its central region.

## Other Data

In addition to what has been described above, we also include measurements derived from other data sets in the analysis. These measurements are not presented among the main scientific results in this paper, but they are part of our final data products and they have appeared in publications that used our data products (cite: Querejeta_etal_2021).

We use continuum-subtracted, narrow-band H$\alpha$ imaging data to provide alternative estimates of star formation rate in 60 out of our 80 targets. These observations were obtained as part of the PHANGS–H$\alpha$ survey[^5] by either the Wide Field Imager (WFI) on the ESO/MPG 2.2-m Telescope or the Direct CCD on the CIS 2.5-m Irénée du Pont Telescope (A. Razza et al. in preparation). The narrow-band H$\alpha$ data have been calibrated astrometrically and photometrically, corrected for sky emission, and masked for foreground stars; the continuum contribution was removed based on the associated $R$-band observations; and the continuum-subtracted data were further corrected for filter transmission and \[ N II \] contamination.

We combine H$\alpha$ data with *WISE* 22 $\mu$m data to derive an attenuation-corrected SFR surface density following (cite: Calzetti_etal_2007) and (cite: Murphy_etal_2011): $$\begin{align}
\frac{\Sigma_\mathrm{SFR}}{\mbox{$\rm M_\odot~yr^{-1}~kpc^{-2}$}}
&= \left(2.7\times10^{13}\,\frac{I_\mathrm{H\alpha}}{\mbox{$\rm erg~s^{-1}\ cm^{-2}\ arcsec^{-2}$}}\right. \nonumber\\
&\quad \left.+\,2.7\times10^{-3}\,\frac{I_\mathrm{22\,\mu m}}{\mbox{$\rm MJy~sr^{-1}$}}\right) \cos{i}~,
\label{eq:SigSFR_HaW4}
\end{align}$$ This prescription assumes constant star formation over 100 Myr and a Kroupa IMF (cite: Kroupa_2001). Given that the H$\alpha$ data and *WISE* data have very different angular resolution (${\sim}1\ensuremath{''}$ versus $15\ensuremath{''}$), we first convolve the H$\alpha$ images to the *WISE* resolution and estimate $\Sigma_\mathrm{SFR}$ via Equation [\[eq:SigSFR_HaW4\]](#eq:SigSFR_HaW4). Then we determine the spatially varying $\Sigma_\mathrm{SFR}$-to-H$\alpha$ ratio at that coarser resolution and multiply it to the native resolution H$\alpha$ images to get the final, high resolution $\Sigma_\mathrm{SFR}$ maps. This approach ensures that the average $\Sigma_\mathrm{SFR}$ value over a large area converges to the expectation from Equation [\[eq:SigSFR_HaW4\]](#eq:SigSFR_HaW4).

# Cross-spatial-scale Analysis

We adopt a “cross-spatial-scale” analysis framework to connect molecular cloud properties (measured on $60{-}150$ pc scales) to galactic environmental properties (mostly measured on $\sim$kpc scales). This analysis framework is inspired by a number of previous works (cite: Sandstrom_etal_2013; Leroy_etal_2016). Briefly, we divide the sky footprint of each galaxy into a set of averaging apertures, within which we aggregate high resolution molecular gas measurements to characterize the underlying cloud population. We also attempt to build a full inventory of ancillary measurements to characterize various aspects of the host galaxy itself. In this way, we assemble the diverse set of observational data described in Section [2](#sec:data) into a coherent, multiwavelength database. An early version of this database was constructed by (cite: Sun_etal_2020b), with its subsequently improved versions used in several publications (cite: Herrera_etal_2020; Jeffreson_etal_2020; Barnes_etal_2021; Querejeta_etal_2021; Stuber_etal_2021). The source code for database construction, including generic tools for aggregating measurements from maps and catalogs into the existing database, is available on GitHub[^6], and a copy of the version used in this article is published on Zenodo (cite: MegaTable_3.0).

## Defining Averaging Apertures

We divide the sky footprint of each galaxy into a set of hexagonal apertures, as illustrated in Figure [2](#fig:image). These apertures form a regular tiling in the plane of the sky, with a “central” aperture positioned right at the galaxy center. Adjacent apertures are separated by a linear distance of 1.5 kpc, which implies that each aperture has a projected area of 1.95 kpc$^2$ on the sky. The configuration of the hexagonal apertures here is analogous to the “solution pixels” used in (cite: Sandstrom_etal_2013), except that the apertures in the current work do not overlap with each other.

For a complete coverage of the galaxy footprint, we include all apertures covering out to $r_\mathrm{gal}= 1.5r_\mathrm{25}$ in each galaxy, where $r_\mathrm{25}$ is the galaxy radius defined by its 25 mag/arcsec$^2$ isophote (in $B$ band; see Table [\[tab:sample\]](#tab:sample)). This way, the constructed database for each galaxy includes almost all valid measurements from all data sets described in Section [2](#sec:data). However, this work focuses on the correlation of molecular clouds and their galactic environments, and thus we will only present results from a subset of apertures that enclose non-zero signals in the PHANGS-ALMA CO moment maps.

In addition to the hexagonal tiling method described above, we also run a parallel line of analysis with a different binning scheme. Specifically, we define a series of radial bins that are 500 pc in width and again cover out to $r_\mathrm{gal}= 1.5\,r_\mathrm{25}$ in each galaxy. Assembling measurements in these radial bins allows us to rigorously calculate their radial profiles, but at the expense of losing all non-axisymmetric information. We publish the data products from these radial profile calculations together with those from the hexagonal aperture analysis (see Appendix [13](#apdx:mrt)). We do not present the results of this parallel line of analysis in this paper, but we expect the distributions of most measurements to be consistent with the hexagonal aperture averages once we use consistent weighting schemes (e.g., by the enclosed area or molecular gas mass; see Section [4](#sec:stats)) for each aperture/ring.

## Aggregating Molecular Cloud Measurements

Within each aperture, we calculate the ensemble average of molecular cloud measurements using a molecular gas mass-weighted averaging scheme. This is equivalent to a CO intensity-weighted averaging, because the $\alpha_\mathrm{CO}$ value is calculated per aperture rather than per object/pixel in this study (see Appendix [9](#apdx:alphaCO)). We use a “$\left<\right>$” symbol to denote this averaging operation: $$\begin{equation}
\left<X_\mathrm{\theta\,pc}\right> = 
\frac{\sum\limits_i M_i\, X_\mathrm{\textit{i},\,\theta\,pc}}{\sum\limits_i M_i}~.
\label{eq:average}
\end{equation}$$ Here, $X_\mathrm{\textit{i},\,\theta\,pc}$ represents a molecular gas property measured for the $i$-th object or pixel at $\theta$ pc resolution ($\theta=60,\,90,\,120,\,150$); it can be any of the object- or pixel-based measurements defined in Sections [2.1.1](#sec:data:CO:obj) and [2.1.2](#sec:data:CO:pix). $M_i$ is the molecular gas mass associated with the object or pixel for which $X_\mathrm{\textit{i},\,\theta\,pc}$ is measured. The summation in Equation [\[eq:average\]](#eq:average) includes all detected objects/\
\[0\]pixels with their center coordinates located inside the sharp boundary of the averaging aperture. In this case, each object/\
\[0\]pixel belongs to a unique averaging aperture, and thus the averaging results in adjacent apertures are independent by construction.

Based on Equation [\[eq:average\]](#eq:average), we can also estimate statistical uncertainties for the population-averaged cloud properties through Gaussian error propagation. We take into account the uncertainties on both the quantity to be averaged, $X_\mathrm{i,\,\theta\,pc}$, and the weight, $M_\mathrm{i}$. When aggregating the pixel-by-pixel measurements, we further consider the built-in correlation between adjacent pixels and scale the estimated uncertainty of the population average according to the oversampling factor.

Our aperture averaging scheme resembles the one adopted by (cite: Leroy_etal_2016) but differs from that approach in important ways. In that work, the averaging is performed via a Gaussian kernel convolution, in which case the averaging result at any given location has a nonzero response to molecular clouds far away from that location. This response pattern is designed to replicate the Gaussian beam of low-resolution data sets, and thus it may be preferable for rigorous calculations combining cloud-scale and kpc-scale measurements (cite: Leroy_etal_2017a; Utomo_etal_2018). However, such an extended response pattern can lead to built-in correlations between averaging results at adjacent locations. More importantly, it can yield biased population statistics when, for example, studying a region with little molecular gas next to a very gas-rich region (such as a galaxy center). Since one of the main goals of this work is to derive reliable molecular cloud population statistics, we deem the “sharp boundary” scheme more appropriate here and will use it consistently for calculating both cloud population statistics and host galaxy properties (also see Section [3.3](#sec:analysis:env)).

### Molecular Gas Clumping Factor

The averaging operation described above essentially extracts the (mass-weighted) expectation value of a molecular gas property from its probability distribution within each averaging aperture. But one can also extract other types of statistics from the same distribution, such as the standard deviation of the gas surface density distribution (which quantifies the inhomogeneity of the medium), or the slope of the GMC mass function. These other types of statistics can also provide unique observational constraints on the physical processes driving molecular cloud formation and evolution.

As part of the analysis done for this work, we calculate the molecular gas “clumping factor,” which is a dimensionless characterization of the surface density inhomogeneity in each aperture (cite: Leroy_etal_2013b): $$\begin{equation}
c_\mathrm{pix,\,\theta\,pc} =
\frac{\left(\sum\limits_i \Sigma_\mathrm{\textit{i},\,\theta\,pc}^2\right)N_\mathrm{pix}}{\left(\sum\limits_i \Sigma_\mathrm{\textit{i},\,\theta\,pc}\right)^2}~.
\label{eq:clumping}
\end{equation}$$ Here $\Sigma_\mathrm{\textit{i},\,\theta\,pc}$ is the molecular gas surface density measured in the $i$-th pixel at $\theta\,pc$ resolution. Similar to Equation [\[eq:average\]](#eq:average), the summation includes all pixels with CO detections within the averaging aperture, and $N_\mathrm{pix}$ is the total number of such pixels. The right hand side of Equation [\[eq:clumping\]](#eq:clumping) can be interpreted as the ratio between the mass-weighted mean and the area-weighted mean of molecular gas surface density in the limit of infinite sensitivity (cite: Leroy_etal_2013b).

We note that $c_\mathrm{pix}$ is a measure of the width (i.e., second moment) of the surface density distribution among many similar parametrizations in the literature (cite: Davis_etal_2022). To measure this type of parameter reliably, a careful treatment of non-detections is particularly important. We describe our strategy to handle non-detections in Section [3.2.2](#sec:analysis:cloud:completeness), and we illustrate the amplitude of the necessary corrections in Section [4.2](#sec:stats:MC) and Appendix [11](#apdx:completeness).

### CO Flux Completeness and Corrections

The ensemble-average molecular cloud properties (Equation [\[eq:average\]](#eq:average)) and the molecular gas clumping factor (Equation [\[eq:clumping\]](#eq:clumping)) are both calculated based on pixels/\
\[0\]objects that are *detected* in the PHANGS–ALMA CO data. For these calculations to reflect the true statistics of the *entire* molecular cloud population in each region, the CO detections need to be reasonably complete, such that they represent a significant portion of the underlying cloud population.

Our object- and pixel-based measurements come from the PHANGS–ALMA CPROPS catalogs and the “strict” moment maps (Sections [2.1.1](#sec:data:CO:obj) and [2.1.2](#sec:data:CO:pix)), thus the completeness of our analysis is determined by the completeness of these data products. Both data products adopt similar signal identification criteria to extract high-confidence CO detections in the original data cubes (cite: Leroy_etal_2021b; Rosolowsky_etal_2021), which ensure reliable CO line measurements for the detected pixels/\
\[0\]objects. However, this comes at the price of excluding faint CO emission, which renders these data products incomplete in terms of both flux coverage and area coverage.

The extent of this effect can be quantified by the CO flux completeness, $f_\mathrm{flux}$, and area coverage fraction, $f_\mathrm{area}$, of the CPROPS catalog or the strict moment maps (cite: Leroy_etal_2021a). Here, we calculate $f_\mathrm{flux}$ and $f_\mathrm{area}$ for each averaging aperture and report these values along with the ensemble-average molecular cloud properties. Specifically, within the footprint of each aperture, we calculate $f_\mathrm{area}$ by comparing the total area covered by CO detections in the “strict” moment-0 map to the total area of the aperture. We calculate $f_\mathrm{flux}$ by comparing the total CO flux included in the “strict” moment-0 map to that in the corresponding “broad” moment-0 map. The latter map is constructed with much more inclusive signal identification criteria than the strict map and has nearly 100% flux completeness (cite: Leroy_etal_2021b).

The incomplete CO flux and area coverage of the “strict” moment maps and CPROPS catalogs introduces a selection bias in our analysis. The sense of this bias is that we miss places where CO emission is too faint to meet the masking criteria (e.g., areas occupied by small, low-mass molecular clouds or a diffuse gas component). This selection bias affects many of the ensemble-average cloud properties calculated in this study, and is particularly severe for the clumping factor (see Section [4.2](#sec:stats:MC) and Appendix [11](#apdx:completeness)).

To account for this systematic bias, we introduce a correction factor for our measurements in each aperture based on the $f_\mathrm{flux}$ and $f_\mathrm{area}$ values in that aperture (see Appendix [11](#apdx:completeness) for detailed derivations). We assume that the CO intensity distribution (or equivalently, molecular gas surface density distribution) has a lognormal shape within each averaging aperture, and that the aforementioned selection bias prevents us from detecting CO emission below an intensity threshold. Under these assumptions, we can solve for the width of the lognormal intensity distribution as well as its centroid (relative to the intensity threshold) from $f_\mathrm{flux}$ and $f_\mathrm{area}$. This in turn allows us to calculate the appropriate correction factors to apply to the ensemble-average molecular cloud surface density, $\left<\Sigma_\mathrm{obj}\right>$ and $\left<\Sigma_\mathrm{pix}\right>$, and the clumping factor, $c_\mathrm{pix}$. We then assume that the correction factor calculated for $\left<\Sigma_\mathrm{obj}\right>$ and $\left<\Sigma_\mathrm{pix}\right>$ also applies to the ensemble-average cloud mass and turbulent pressure, but we leave molecular cloud size, velocity dispersion, and virial parameter uncorrected. Though these latter quantities likely do suffer sensitivity-induced selection biases (cite: Sun_etal_2018), the appropriate functional forms of their completeness corrections remain uncertain at present. Finally, we scale the corresponding (statistical) uncertainty for each ensemble-average value by the same correction factor.

As illustrated in Section [4.2](#sec:stats:MC) and Appendix [11](#apdx:completeness), thanks to the relatively high flux completeness of the PHANGS–ALMA CO data, the correction factors on the average cloud surface densities and the clumping factor are both moderate (${<}0.3$ dex for 90% of the apertures with CO detections). Nevertheless, we do expect our completeness correction scheme to be less reliable for apertures with low $f_\mathrm{flux}$ and/or $f_\mathrm{area}$, in which case the extrapolation is done based on very few measurements. For this reason, we will exclude apertures with low $f_\mathrm{flux}$ or $f_\mathrm{area}$ when performing analyses that requires accurate cloud population statistics in individual apertures (see Section [5](#sec:corr) and Appendix [11](#apdx:completeness)).

## Aggregating Local Environmental Metrics

In addition to the compilation of ensemble-average molecular cloud properties described above, we assemble an inventory of “environmental metrics” that delineate various host galaxy local properties within each averaging aperture. This inventory covers orbital kinematic properties (derived from rotation curves), gas-phase metallicity (predicted from scaling relations), surface densities of molecular gas, atomic gas, stellar mass, and SFR (estimated from multiwavelength imaging data), and morphological environment information (inherited from environmental masks).

We generally use two schemes to integrate these environmental metrics into the databases of aperture-wide statistics. For those metrics that are calculated analytically (e.g., galactocentric coordinates, metallicity) or interpolated from analytical models (e.g., rotation curve-related properties), we directly record their values at the location of the aperture center. For those metrics that rely on two-dimensional images, we use the native resolution images and calculate the *unweighted* average among all pixels inside the sharp boundary of each aperture. This latter scheme is consistent with the averaging scheme we used for aggregating molecular cloud properties (modulo the different weighting), and thus allows for direct comparisons between the averaging results.

We elaborate the specific treatment for each type of environmental metric below:

- *Coordinates*. For each hexagonal aperture, we record its central R.A. and Dec. coordinates. Then based on the center coordinates, inclination angle, position angle, and the distance of the galaxy (see Table [\[tab:sample\]](#tab:sample)), we calculate the deprojected galactocentric radius, $r_\mathrm{gal}$, (in kpc units) at the aperture center and the deprojected azimuthal angle, $\phi_\mathrm{gal}$, in the galaxy plane with respect to the major axis direction. These coordinates uniquely determine the location of each aperture both on the sky and in the deprojected galaxy plane.

- *Orbital kinematics*. We report local orbital kinematic properties for apertures in the galaxy sample and galactocentric radius range covered by the rotation curve measurements from (cite: Lang_etal_2020). As detailed in Section [2.5](#sec:data:rotcurve), these orbital properties include the circular velocity, $V_\mathrm{circ}$, angular velocity, $\Omega_\mathrm{circ}$, logarithmic derivative of the rotation curve, $\beta$, and Oort’s $A$ parameter, $A_\mathrm{Oort}$. They are calculated by interpolating the functional fitting model of the rotation curves at the location of the aperture center.

- *Metallicity*. We report the predicted gas-phase metallicity in each aperture using a prescription similar to the one described in (cite: Sun_etal_2020b), but with a few methodological improvements. In short, we first infer the metallicity at $r_\mathrm{gal}= 1.0\,r_\mathrm{e}$ in each galaxy based on a galaxy global mass–metallicity relationship (cite: Sanchez_etal_2019), and then extrapolate to all $r_\mathrm{gal}$ assuming a fixed radial metallicity gradient of $-0.1\,\mathrm{dex}/r_\mathrm{e}$ within each galaxy (cite: Sanchez_etal_2014). For better methodological consistency with the original references, here we approximate the galaxy effective radius as $r_\mathrm{e}\approx 1.68\,r_\mathrm{disk}$, where $r_\mathrm{disk}$ is the stellar disk scale length. We also elevate the global stellar masses in Table [\[tab:sample\]](#tab:sample) by $0.1$ dex before substituting their values into the mass–metallicity relationship. We refer interested readers to Appendix [9](#apdx:alphaCO) for more details about these adjustments.

- *Molecular gas surface density (kpc-scale)*. We report the *area-weighted* mean molecular gas surface density, $\Sigma_\mathrm{mol}$, in each kpc-scale aperture. We emphasize the distinction between this measurement and the mass-weighted average of molecular cloud surface density, $\left<\Sigma_\mathrm{[pix|obj]}\right>$, defined in Section [3.2](#sec:analysis:cloud). The area-weighted mean $\Sigma_\mathrm{mol}$ here is calculated from the total CO flux inside the hexagonal boundary of each kpc-sized aperture divided by its total deprojected area. For this particular calculation, we use the native resolution “broad” moment-0 map to ensure a high flux completeness (see Section [3.2.2](#sec:analysis:cloud:completeness)). We then use the same metallicity-dependent CO-to-H$_2$ conversion factor to convert CO line intensity into mass surface density unit, as we do in Equation [\[eq:Sigma_pix\]](#eq:Sigma_pix).

  We note that our methodology for calculating this kpc-scale aperture averaged $\Sigma_\mathrm{mol}$ is different from the one used in (cite: Sun_etal_2020b). There, the kpc-scale $\Sigma_\mathrm{mol}$ was derived via convolving the CO moment-0 maps to a fixed 1 kpc resolution and then sampling the convolved maps at the aperture centers. As discussed above, the new averaging scheme in this paper leads to better methodological consistency with our calculation of molecular cloud population statistics.

- *Atomic gas surface density*. We report the area-weighted mean atomic gas surface density, $\Sigma_\mathrm{atom}$, in all apertures for which we have H I  data (see Table [\[tab:sample\]](#tab:sample)). This is calculated in the same way as the area-weighted mean $\Sigma_\mathrm{mol}$: we divide the total H I  21 cm line flux inside the hexagonal aperture by the aperture area, and then convert it to mass surface density unit via Equation [\[eq:SigHI\]](#eq:SigHI).

  Since the H I  data resolution is typically comparable to or coarser than our adopted aperture size, our calculated $\Sigma_\mathrm{atom}$ might not reflect the true atomic gas surface density inside the sharp aperture boundaries, but rather a slightly “smoothed” version of it. However, the atomic gas distribution is usually much smoother than the molecular gas (cite: Leroy_etal_2013b), and $\Sigma_\mathrm{atom}$ only plays a minor role throughout this paper. The resolution degradation is thus not a serious concern for the following analysis.

- *Stellar mass surface density*. We report the area-weighted mean stellar mass surface density, $\Sigma_\mathrm{\star}$, in each aperture. We calculate $\Sigma_\mathrm{\star}$ via Equations [\[eq:Sigstar_3p6um\]](#eq:Sigstar_3p6um) or [\[eq:Sigstar_3p4um\]](#eq:Sigstar_3p4um) based on the mean *WISE* 3.4 $\mu$m or IRAC 3.6 $\mu$m surface brightness at $7.5\ensuremath{''}$ resolution within sharp aperture boundaries. We determine the stellar M/L ratio, $\Upsilon_{3.4\,\mu m}$, for each aperture by sampling the M/L ratio maps from (cite: Leroy_etal_2021a) at the location of the aperture center.

- *SFR surface density*. We report the area-weighted mean SFR surface density, $\Sigma_\mathrm{SFR}$, in each aperture. This is primarily calculated via Equations [\[eq:SigSFR_FUVW4\]](#eq:SigSFR_FUVW4)–[\[eq:SigSFR_W4ONLY\]](#eq:SigSFR_W4ONLY) based on the best available UV/IR data combination (see Table [\[tab:sample\]](#tab:sample)) at $15\ensuremath{''}$ resolution. We note that this resolution could approach the averaging aperture size in the more distant targets in our sample, in which case concerns about correlated measurements could again arise. To evaluate these concerns, we compare the UV/IR-based $\Sigma_\mathrm{SFR}$ measurements with H$\alpha$-based measurements (the latter includes data at much higher angular resolution; see Section [2.7](#sec:data:other)). We find quantitatively consistent results at $\Sigma_\mathrm{SFR}\gtrsim10^{-3}\;\mbox{$\rm M_\odot~yr^{-1}~kpc^{-2}$}$, which is the range of interest in this paper (see Figure [3](#fig:hist_env) below).

- *Morphological environment*. We keep track of the morphological regions each averaging aperture inhabits in the host galaxy (see Section [2.6](#sec:data:environ)). Because of the kpc-scale sizes of these apertures, some of them could stretch across multiple morphological regions. To deal with this ambiguity, we calculate the fraction of CO flux originating from each morphological region (especially galaxy centers and stellar bars) relative to the sum over the entire aperture. We then classify all apertures that have a non-zero[^7] CO flux contribution from galaxy centers or stellar bars as “center/bar” apertures, and all the remainder as “disk” apertures.

## Outcome of the Cross-spatial-scale Analysis

Our analysis yields a rich value-added database for each of the 80 galaxies listed in Table [\[tab:sample\]](#tab:sample). These databases present the molecular cloud populations residing in each galaxy, along with the large-scale gas and stellar mass distribution, kinematic information, morphological structures, and star formation activities of the galaxy disk itself. Together, these high-level measurements have a broad range of applications (see Section [7](#sec:summary)). They are published in the form of machine-readable tables online (see Appendix [13](#apdx:mrt)).

Our databases include $46{,}628$ apertures in total. These apertures collectively cover the footprint of every target galaxy out to a galactocentric radius limit of $1.5\,r_\mathrm{25}$. The majority of these apertures have local environmental measurements derived from multiwavelength data (such as UV, and IR), yet only a smaller subset of them have valid molecular gas measurements from PHANGS-ALMA CO data. This is because the footprint of the PHANGS–ALMA survey is often more confined and covers only the inner, molecular gas-rich part of the galaxy disk (cite: Leroy_etal_2021a). Since this paper focuses on linking the molecular cloud population to their local environment, in the following sections, we restrict ourselves to a subset of $3{,}383$ apertures that are inside the PHANGS–ALMA survey footprint and show detectable CO emission in the 60–150 pc scale “strict” moment maps. Nonetheless, the full set of $46{,}628$ apertures will be included in the public data release given the rich information provided by the multiwavelength ancillary data alone.

# Distributions of Average Molecular Cloud Properties and Sub-galactic Environments in PHANGS–ALMA

In this section, we characterize the distributions of region-averaged molecular cloud properties and host galaxy local properties across the full PHANGS–ALMA data set. To do this, we use the databases constructed in Sections [3](#sec:analysis) and focus on $3{,}383$ apertures with CO measurements from PHANGS-ALMA (including $2{,}724$ apertures classified as “disk” and the remainder as “center/bar”). In the main text, we will only present the statistics of molecular cloud measurements at 150 pc scales, which is the best common resolution achievable for all galaxies. Quantitative comparisons across different resolutions are shown in Appendix [12](#apdx:scale).

## Sub-galactic Environments Probed by PHANGS–ALMA

Our multiwavelength measurements provide a multifaceted depiction of the range of local galactic environments probed by the PHANGS-ALMA survey. To this end, Figure [3](#fig:hist_env) shows the histograms of 12 local environmental metrics across $3{,}383$ apertures. We also calculate statistics such as the median value and $16{-}84$ percentile range for each environmental metric and tabulate them in Table [1](#tab:stats_env). These statistics are calculated from the histogram using two different weighting schemes: simple counting of the number of apertures or weighting each aperture by the molecular gas mass it encloses. The first scheme treats all apertures equally, and the calculated statistics reflect *a typical kpc-sized area* covered by PHANGS-ALMA; the latter scheme instead treats each unit of gas mass equally, and the calculated statistics reflect the local environment in which *most molecular gas resides*.

Below we split the 12 environmental metrics into four topical groups and comment on the corresponding histograms and statistics.

- *Galactocentric radii.* The PHANGS–ALMA CO measurements cover a wide radial range in terms of both absolute and normalized $r_\mathrm{gal}$ (panels *a* and *b*). When weighting by the number of apertures, we find median values and $\pm1\sigma$ ranges of $r_\mathrm{gal}=5.4^{+3.1}_{-2.7}$ kpc and $r_\mathrm{gal}/r_\mathrm{disk}=1.8^{+1.0}_{-0.8}$ across all apertures. We find smaller values when weighting each aperture by its encircled molecular gas mass. This reflects that the molecular gas distribution typically peaks toward the galaxy center, and thus apertures at smaller radii often enclose more molecular gas mass.

  We note that the $r_\mathrm{gal}$ histogram appears “quantized” simply due to the fixed 1.5 kpc linear size of the hexagonal apertures and their tiling pattern on the sky. This behavior is not obvious in the $r_\mathrm{gal}/r_\mathrm{disk}$ histogram because the normalization factor $r_\mathrm{disk}$ varies among galaxies, which effectively “smooth” the histogram.

- *Kinematic properties.* For the subset of apertures located in the 62 galaxies with CO kinematic measurements, we report the distributions of orbital angular velocity (panel *c*) and Oort’s $A$ parameter (panel *d*). Weighting all apertures equally, we find typical $\Omega_\mathrm{circ}=32^{+16}_{-8}~\mbox{$\rm Gyr^{-1}$}$ and $A_\mathrm{Oort}=14^{+6}_{-4}~\mbox{$\rm km~s^{-1}~kpc^{-1}$}$ across galaxy disks, which translate to an orbital period of ${\sim}\,200~\mbox{$\rm Myr$}$ and a local shearing timescale of ${\sim}\,70~\mbox{$\rm Myr$}$ (i.e., the reciprocal of $A_\mathrm{Oort}$; also see Section [6](#sec:timescales)). These values suggest that the kinematic properties of a typical kpc-sized area probed by PHANGS-ALMA are very similar to those of the Solar Neighborhood (cite: Bovy_2017a).

  We also find that apertures located in galaxy centers and stellar bars show systematically higher $\Omega_\mathrm{circ}$ and $A_\mathrm{Oort}$ values. This is expected from their locations at smaller $r_\mathrm{gal}$ and the stronger shear often observed in these environments.

- *Galaxy disk mass components.* Weighting all apertures in galaxy disks equally, we find typical surface densities of $\Sigma_\mathrm{\star}=65^{+80}_{-34}~\mbox{$\rm M_\odot~pc^{-2}$}$ and $\Sigma_\mathrm{mol}=5.4^{+10.8}_{-3.7}~\mbox{$\rm M_\odot~pc^{-2}$}$ (panels *e* and *f*). Among the 53 galaxies with H I  21 cm line data (see Table [\[tab:sample\]](#tab:sample)), we find a typical total gas surface density of $\Sigma_\mathrm{gas}=\Sigma_\mathrm{mol}+\Sigma_\mathrm{atom}=13^{+14}_{-7}~\mbox{$\rm M_\odot~pc^{-2}$}$ (panel *g*). This gives a typical gas fraction of $f_\mathrm{gas}=\Sigma_\mathrm{gas}/(\Sigma_\mathrm{\star}+\Sigma_\mathrm{gas})=0.16^{+0.14}_{-0.07}$ (panel *i*) and a molecular fraction of $f_\mathrm{mol}=\Sigma_\mathrm{mol}/\Sigma_\mathrm{gas}=0.53^{+0.22}_{-0.30}$ (panel *j*). These values are modestly higher than the Solar Neighborhood values (cite: McKee_etal_2015).

  Examining the corresponding molecular gas mass-weighted statistics for galaxy disks, we find that most molecular gas mass resides in environments with even higher surface densities ($\Sigma_\mathrm{\star}=110^{+140}_{-60}~\mbox{$\rm M_\odot~pc^{-2}$}$, $\Sigma_\mathrm{mol}=17^{+29}_{-11}~\mbox{$\rm M_\odot~pc^{-2}$}$, $\Sigma_\mathrm{gas}=28^{+30}_{-15}~\mbox{$\rm M_\odot~pc^{-2}$}$) and molecular fraction ($f_\mathrm{mol}=0.71^{+0.13}_{-0.20}$). For comparison, these gas surface densities are likely higher than the averaged value across any kpc-sized neighborhood in our Galaxy (cite: Nakanishi_Sofue_2006; Spilker_etal_2021).

- *Star formation activity.* The typical range of SFR surface density of “disk” apertures, when weighted by simple number counts, is $\Sigma_\mathrm{SFR}=3.5^{+6.8}_{-2.1}\times10^{-3}~\mbox{$\rm M_\odot~yr^{-1}~kpc^{-2}$}$ (panel *h*). This is again comparable to the estimated Solar Neighborhood SFR surface density at the present day (cite: Bovy_2017b). Combined with the measured $\Sigma_\mathrm{mol}$ and $\Sigma_\mathrm{gas}$ in our sample, this implies typical depletion times of $t_\mathrm{dep,\,mol}=\Sigma_\mathrm{mol}/\Sigma_\mathrm{SFR}=1.5^{+1.0}_{-0.7}$ Gyr for the molecular gas (panel *k*) and $t_\mathrm{dep,\,gas}=\Sigma_\mathrm{gas}/\Sigma_\mathrm{SFR}=3.3^{+2.2}_{-1.3}$ Gyr for the total gas (panel *l*).

  In comparison, the molecular gas mass-weighted statistics reveal that most of the molecular gas mass resides in more actively star-forming environments with $\Sigma_\mathrm{SFR}=9.6^{+20.9}_{-6.4}\times10^{-3}~\mbox{$\rm M_\odot~yr^{-1}~kpc^{-2}$}$. Yet associated gas depletion times appear similar to the aperture number-weighted values, with $t_\mathrm{dep,\,mol}=1.8^{+1.0}_{-0.7}$ Gyr and $t_\mathrm{dep,\,gas}=2.8^{+1.7}_{-1.1}$ Gyr. In other words, the SFR surface density is proportionally higher in these environments as their gas surface densities are.

In summary, the PHANGS-ALMA survey covers an wide variety of host galaxy local environments. When weighting all apertures equally, the most representative local environment in our sample closely resembles the Solar Neighborhood in many aspects. Comparatively, most molecular gas mass is hosted in regions that are closer to the galaxy center, have higher surface densities of stars, gas, and SFR, and are possibly not matched by any kpc-scale regions in our Galaxy.

## Molecular Cloud Populations in PHANGS-ALMA

Our calculations aggregate individual molecular cloud measurements to yield mass-weighted average properties for each aperture (Section [3.2](#sec:analysis:cloud)). The distributions of these population-averaged measurements offer a comprehensive portrait of how cloud populations vary across PHANGS–ALMA. This is demonstrated by Figure [4](#fig:hist_MC), which shows histograms of population-averaged cloud properties measured from object/pixel-based approaches (originally measured at 150 pc). These histograms include all $3{,}383$ apertures with pixel-based data and $2{,}784$ apertures with object-based data. The latter number is smaller because CPROPS uses a slightly more stringent criterion for identifying objects in CO data cubes (cite: Rosolowsky_etal_2021).

Similar to Section [4.1](#sec:stats:env), here we calculate the median values and $16{-}84$ percentile ranges with two different weighting schemes (Table [2](#tab:stats_gmc)). We note that because most variables depicted in Figure [4](#fig:hist_MC) (except $c_\mathrm{pix}$) are already mass-weighted averages *within individual apertures*, an additional mass-weighted averaging step *across all apertures* can be interpreted as the mass-weighted average cloud properties combining all clouds in all galaxies in PHANGS–ALMA. In comparison, the other weighting scheme (i.e., same weight for all apertures) gives us a view of the typical molecular cloud population likely to be found at a random location in a PHANGS–ALMA galaxy. As results from the latter weighting method is less straightforward to interpret, below we focus mostly on the mass-weighted statistics in our discussion.

- *Molecular cloud mass and size.* The mass-weighted average molecular cloud mass at 150 pc resolution is $6.9^{+10.5}_{-4.5}\times10^6~\mbox{$\rm M_\odot$}$ for all clouds in galaxy disks (panel *a*). This value is high compared to the typical mass of molecular clouds in the Milky Way (cite: Rice_etal_2016; Miville-Deschenes_etal_2017; Colombo_etal_2019), but is consistent with numbers measured in nearby galaxy studies (cite: Hughes_etal_2013a). As pointed out by (cite: Rosolowsky_etal_2021), the finite resolution and sensitivity of the PHANGS–ALMA CO data limit our ability to identify molecular clouds with mass $\lesssim10^5~\mbox{$\rm M_\odot$}$. Specifically, the 60–150 pc resolution of the PHANGS–ALMA data would lead to individual, moderate size clouds being blended into a single object by CPROPS (also see discussions on the resolution-dependence of average cloud mass in Appendix [12](#apdx:scale)). That said, our completeness correction can partly remedy sensitivity-related biases by compensating for isolated, less massive clouds undetected in the high resolution CO observations (the histograms for the corrected measurements extend to lower values than those for the uncorrected measurements).

  In line with this consideration, the mass-weighted cloud effective radius measured at the same resolution spans $90^{+19}_{-15}$ pc, which slightly exceeds half the beam FWHM size (panel *b*). This is consistent with a series of previous studies, all of which found that cloud segmentation algorithms tend to identify objects comparable to or slightly larger than the beam size (cite: Verschuur_1993; Pineda_etal_2009; Hughes_etal_2013a; Leroy_etal_2016).

- *Molecular cloud surface density.* At 150 pc resolution, the mass-weighted molecular cloud surface density in galaxy disks is $78^{+124}_{-50}~\mbox{$\rm M_\odot~pc^{-2}$}$ from the object-based approach and $33^{+60}_{-22}~\mbox{$\rm M_\odot~pc^{-2}$}$ from the pixel-based approach (both weighted by gas mass; see panels *d* and *h*). These values are on the low end of the surface density distribution of Galactic molecular clouds (cite: Colombo_etal_2019). This likely reflects the coarser spatial resolution of our data compared to most Galactic studies, which means our measurements would be “diluted” by low column density sightlines within each beam.

  The quantitative differences between the object- and pixel-based approaches reflect that the they attempt to measure fundamentally different quantities (see Section [2.1.3](#sec:data:CO:notes)). In particular, the CPROPS algorithm attempts to measure the true surface density of an identified object. Therefore, it includes additional de-convolution and extrapolation procedures, which lead to smaller cloud sizes and larger masses, and thus larger surface densities. The pixel-by-pixel analysis instead measures the surface density point-by-point from a contiguous molecular gas distribution. Without a priori expectation for the gas spatial distribution, it does not perform any de-convolution but simply extracts measurements at the resolution of the observations. Given these differences, for marginally resolved clouds the pixel-based approach would simply yield the native, beam-averaged value at the data resolution, whereas the object-based approach would yield higher surface densities as a result of the de-convolution.

  Compared to the results for disk apertures, the cloud populations in galaxy centers and stellar bars have much higher mass-weighted mean surface densities of $210^{+560}_{-160}~\mbox{$\rm M_\odot~pc^{-2}$}$ (object-based) or $200^{+840}_{-160}~\mbox{$\rm M_\odot~pc^{-2}$}$ (pixel-based). Such a trend has been highlighted in previous works on the same galaxies (cite: Sun_etal_2018; Sun_etal_2020a; Rosolowsky_etal_2021) and is also consistent with observations in our Galaxy (cite: Oka_etal_2001). We do caution that these results are more sensitive to the choice of $\alpha_\mathrm{CO}$ prescriptions (see Appendix [9](#apdx:alphaCO)). Several lines of evidence suggest lower $\alpha_\mathrm{CO}$ in galaxy centers (cite: Bolatto_etal_2013; Sandstrom_etal_2013; Israel_2020; Teng_etal_2021) and our fiducial prescription only mildly depresses $\alpha_\mathrm{CO}$ near galaxy centers.

- *Molecular gas velocity dispersion.* For molecular cloud populations located in galaxy disks, we find mass-weighted average velocity dispersions of $5.8^{+1.9}_{-1.5}~\mbox{$\rm km~s^{-1}$}$ (object-based; panel *e*) or $4.7^{+2.2}_{-1.7}~\mbox{$\rm km~s^{-1}$}$ (pixel-based; panel *i*). The cloud populations in galaxy centers or stellar bars show systematically higher values ($9.0^{+3.6}_{-3.0}~\mbox{$\rm km~s^{-1}$}$ from object-based and $16^{+11}_{-10}~\mbox{$\rm km~s^{-1}$}$ from pixel-based statistics). These typical values and their environmental dependence are broadly consistent with previous galactic and extragalactic studies (cite: Heyer_etal_2009; DonovanMeyer_etal_2013; Hughes_etal_2013a; Leroy_etal_2015a; Sun_etal_2020a; Rosolowsky_etal_2021).

  The quantitative discrepancies between the two approaches here can also be explained by methodological differences. As described above, the objects identified by CPROPS are often slightly larger than the beam size. We would then expect larger CO line width measurements from the object-based approach due to both the size–line width relation in molecular clouds (cite: Larson_1981) and additional contributions from galaxy rotation and large-scale gas streaming motions. This explains the sense of deviation for the measurements in galaxy disks. However, in places where molecular clouds are spatially crowded (such as galaxy centers), the $ppv$ space segmentation in CPROPS helps to demarcate clouds that fall along the same line of sight but are separable in velocity space, whereas the pixel-based analysis simply measures the line effective width and thus cannot tell them apart (cite: Henshaw_etal_2016). This explains why the pixel-based approach yields higher velocity dispersions with a wider spread in these environments.

- *Molecular cloud turbulent pressure.* Molecular clouds in galaxy disks have mass-weighted average turbulent pressure of $2.1^{+7.2}_{-1.6}\times10^5~\mbox{$\rm K~cm^{-3}$}$ (object-based; panel *f*) or $1.1^{+5.4}_{-0.9}\times10^5~\mbox{$\rm K~cm^{-3}$}$ (pixel-based; panel *j*). These values are at least an order of magnitude higher in galaxy centers and stellar bars ($1.8^{+6.8}_{-1.6}\times10^6~\mbox{$\rm K~cm^{-3}$}$ from object-based and $6.5^{+106.4}_{-6.4}\times10^6~\mbox{$\rm K~cm^{-3}$}$ from pixel-based statistics), as anticipated from the high environmental pressure there (cite: Schruba_etal_2019; Sun_etal_2020b).

  The sense of deviation between the two approaches here is similar to that of the surface density and velocity dispersion measurements. It is most apparent near the low pressure end, where the distribution almost always exceeds $10^4~\mbox{$\rm K~cm^{-3}$}$ in the object-based statistics but extends to below $10^3~\mbox{$\rm K~cm^{-3}$}$ in the pixel-based statistics. This aligns with the intuition that the object-based calculations focus on the denser inner portion of molecular clouds (i.e., the half of gas within the FWHM of each object), whereas the pixel-based analysis treats every chunk of molecular gas equally at fixed resolution, and thus can reflect the behavior of the lower pressure, more diffuse gas when it dominates the mass budget.

- *Molecular cloud virial parameter.* Molecular cloud populations in galaxy disks exhibit a narrow range of mass-weighted average virial parameters: $1.1^{+0.8}_{-0.4}$ (object-based; panel *g*) or $1.6^{+0.9}_{-0.6}$ (pixel-based; panel *k*). If taken at face value, these values would suggest that the dynamical state of molecular clouds are somewhere between virial equilibrium ($\alpha_\mathrm{vir}=1$) and energy equipartition (cite: Sun_etal_2018; Sun_etal_2020a; Rosolowsky_etal_2021). However, systematic uncertainties related to the sub-resolution gas distribution and the CO-to-$\mathrm{H}_2$ conversion factor are especially concerning for the $\alpha_\mathrm{vir}$ measurements given the narrow dynamic range. More, it can be challenging to determine the true dynamical state of the observed gas structures from a measured $\alpha_\mathrm{vir}$ alone (cite: Ballesteros-Paredes_etal_2011a; Ibanez-Mejia_etal_2016; Lu_etal_2020). The most conservative conclusions from these data are that molecular cloud populations show a relatively narrow range of dynamical states and appear near energy equipartition across a wide range of environments.

  Comparing the mass-weighted average $\alpha_\mathrm{vir}$ between cloud populations in galaxy disks versus those in galaxy centers and stellar bars, the pixel-based statistics indicate higher $\alpha_\mathrm{vir}$ values for the latter, while the object-based statistics show essentially no difference. This can be explained by the same line-of-sight blending effect that drive the pixel-based velocity dispersion measurements higher in centers and bars (cite: Henshaw_etal_2016; Kruijssen_etal_2019a). We suggest to prefer the object-based results in this case, but again caution that we may be overestimating $\alpha_\mathrm{CO}$ in these regions. If this is the case, the correct object-based values would also suggest higher $\alpha_\mathrm{vir}$ in bars and galaxy centers.

- *Molecular gas clumping factor.* We find a completeness-corrected clumping factor of $1.9^{+1.1}_{-0.4}$ (uniform weight per aperture) or $1.9^{+1.0}_{-0.4}$ (weighted by molecular gas mass in each aperture) across our sample (panel *c*). These values are markedly smaller than those reported in (cite: Leroy_etal_2013b), which were calculated from early CO observations targeting a handful of very nearby galaxies (including several CO-poor Local Group members). This is partly due to the much higher sensitivity of the PHANGS–ALMA data set, and partly due to the improvement in the treatment of non-detections. The small clumping factors we derive suggest that the molecular gas is much less clumpy than reported in previous studies on a smaller set of galaxies.

+--------------------------------------------------------------------------+--------------------------------------------------------------------------+--------------------------------------------------------------------------+
| Quantity                                                                 | Weighted by number of apertures                                          | Weighted by molecular gas mass                                           |
+:=========================================================================+:======================:+:======================:+:======================:+:======================:+:======================:+:======================:+
| 2-4 (lr)5-7                                                              | All                    | Disk                   | Center/bar             | All                    | Disk                   | Center/bar             |
+--------------------------------------------------------------------------+------------------------+------------------------+------------------------+------------------------+------------------------+------------------------+
|                                                                          |                        |                        |                        |                        |                        |                        |
+--------------------------------------------------------------------------+------------------------+------------------------+------------------------+------------------------+------------------------+------------------------+
|                                                                          |                        |                        |                        |                        |                        |                        |
+--------------------------------------------------------------------------+------------------------+------------------------+------------------------+------------------------+------------------------+------------------------+
| $r_\mathrm{gal}$ \[$\mathrm{kpc}$\]                                      | $5.4^{+3.1}_{-2.7}$    | $5.8^{+3.2}_{-2.4}$    | $3.1^{+2.9}_{-1.5}$    | $3.5^{+3.4}_{-3.5}$    | $5.0^{+3.0}_{-2.1}$    | $1.5^{+2.0}_{-1.5}$    |
+--------------------------------------------------------------------------+------------------------+------------------------+------------------------+------------------------+------------------------+------------------------+
| $r_\mathrm{gal}/r_\mathrm{disk}$                                         | $1.8^{+1.0}_{-0.8}$    | $1.9^{+1.0}_{-0.7}$    | $0.9^{+0.9}_{-0.5}$    | $1.2^{+1.1}_{-1.2}$    | $1.7^{+0.9}_{-0.7}$    | $0.2^{+0.8}_{-0.2}$    |
+--------------------------------------------------------------------------+------------------------+------------------------+------------------------+------------------------+------------------------+------------------------+
| $\Omega_\mathrm{circ}$ \[$\mathrm{Gyr^{-1}}$\]                           | $34^{+23}_{-9}$        | $32^{+16}_{-8}$        | $53^{+30}_{-21}$       | $45^{+34}_{-16}$       | $37^{+21}_{-11}$       | $66^{+25}_{-25}$       |
+--------------------------------------------------------------------------+------------------------+------------------------+------------------------+------------------------+------------------------+------------------------+
| $A_\mathrm{Oort}$ \[$\mathrm{km\;s^{-1}\;kpc^{-1}}$\]                    | $15^{+8}_{-4}$         | $14^{+6}_{-4}$         | $18^{+17}_{-6}$        | $18^{+10}_{-6}$        | $17^{+8}_{-5}$         | $21^{+20}_{-6}$        |
+--------------------------------------------------------------------------+------------------------+------------------------+------------------------+------------------------+------------------------+------------------------+
| $\Sigma_\star$ \[$\mathrm{M_\odot\;pc^{-2}}$\]                           | $77^{+129}_{-42}$      | $65^{+80}_{-34}$       | $190^{+280}_{-110}$    | $200^{+750}_{-130}$    | $110^{+140}_{-60}$     | $550^{+2000}_{-360}$   |
+--------------------------------------------------------------------------+------------------------+------------------------+------------------------+------------------------+------------------------+------------------------+
| $\Sigma_\mathrm{mol}$ \[$\mathrm{M_\odot\;pc^{-2}}$\]                    | $6.0^{+13.3}_{-4.1}$   | $5.4^{+10.8}_{-3.7}$   | $10^{+24}_{-7}$        | $28^{+118}_{-20}$      | $17^{+29}_{-11}$       | $83^{+449}_{-66}$      |
+--------------------------------------------------------------------------+------------------------+------------------------+------------------------+------------------------+------------------------+------------------------+
| $\Sigma_\mathrm{gas}$ \[$\mathrm{M_\odot\;pc^{-2}}$\]                    | $13^{+16}_{-7}$        | $13^{+14}_{-7}$        | $14^{+24}_{-9}$        | $35^{+71}_{-21}$       | $28^{+30}_{-15}$       | $71^{+176}_{-52}$      |
+--------------------------------------------------------------------------+------------------------+------------------------+------------------------+------------------------+------------------------+------------------------+
| $\Sigma_\mathrm{SFR}$ \[$10^{-3}\;\mathrm{M_\odot\;yr^{-1}\;kpc^{-2}}$\] | $4.0^{+8.3}_{-2.5}$    | $3.5^{+6.8}_{-2.1}$    | $7.2^{+18.7}_{-5.0}$   | $16^{+92}_{-12}$       | $9.6^{+20.9}_{-6.4}$   | $45^{+469}_{-36}$      |
+--------------------------------------------------------------------------+------------------------+------------------------+------------------------+------------------------+------------------------+------------------------+
| $f_\mathrm{gas}$                                                         | $0.14^{+0.13}_{-0.08}$ | $0.16^{+0.14}_{-0.07}$ | $0.07^{+0.07}_{-0.05}$ | $0.16^{+0.13}_{-0.08}$ | $0.18^{+0.13}_{-0.07}$ | $0.11^{+0.08}_{-0.06}$ |
+--------------------------------------------------------------------------+------------------------+------------------------+------------------------+------------------------+------------------------+------------------------+
| $f_\mathrm{mol}$                                                         | $0.58^{+0.22}_{-0.31}$ | $0.53^{+0.22}_{-0.30}$ | $0.76^{+0.18}_{-0.27}$ | $0.78^{+0.18}_{-0.21}$ | $0.71^{+0.13}_{-0.20}$ | $0.92^{+0.07}_{-0.15}$ |
+--------------------------------------------------------------------------+------------------------+------------------------+------------------------+------------------------+------------------------+------------------------+
| $t_\mathrm{dep,\,mol}$ \[$\mathrm{Gyr}$\]                                | $1.5^{+1.1}_{-0.8}$    | $1.5^{+1.0}_{-0.7}$    | $1.5^{+1.3}_{-0.8}$    | $1.7^{+1.0}_{-0.9}$    | $1.8^{+1.0}_{-0.7}$    | $1.6^{+0.9}_{-0.9}$    |
+--------------------------------------------------------------------------+------------------------+------------------------+------------------------+------------------------+------------------------+------------------------+
| $t_\mathrm{dep,\,gas}$ \[$\mathrm{Gyr}$\]                                | $3.0^{+2.2}_{-1.2}$    | $3.3^{+2.2}_{-1.3}$    | $2.2^{+1.6}_{-1.1}$    | $2.4^{+1.7}_{-1.1}$    | $2.8^{+1.7}_{-1.1}$    | $2.0^{+1.1}_{-1.2}$    |
+--------------------------------------------------------------------------+------------------------+------------------------+------------------------+------------------------+------------------------+------------------------+

: Statistics of Galactic Environmental Properties

Table notes: The median value and $\pm1\sigma$ range (i.e., $16{-}84$ percentile range) of the galactic environmental metrics shown in Figure [3](#fig:hist_env). Results in columns (2) to (4) are calculated by weighting each aperture equally, whereas those in columns (5) to (7) are calculated by weighting each aperture by the molecular gas mass it contains.

+------------------------------------------------------------------------------+----------------------------------------------------------------------------------------------------+--------------------------------------------------------------------------------------------+
| Quantity                                                                     | Weighted by number of apertures                                                                    | Weighted by molecular gas mass                                                             |
+:=============================================================================+:======================:+:======================:+:======================:+:=======================:+:=====================:+:=====================:+:====================:+:===================:+
| 2-5 (lr)6-9                                                                  | All (uncor.)           | All                    | Disk                   | Center/bar              | All (uncor.)          | All                   | Disk                 | Center/bar          |
+------------------------------------------------------------------------------+------------------------+------------------------+------------------------+-------------------------+-----------------------+-----------------------+----------------------+---------------------+
|                                                                              |                        |                        |                        |                         |                       |                       |                      |                     |
+------------------------------------------------------------------------------+------------------------+------------------------+------------------------+-------------------------+-----------------------+-----------------------+----------------------+---------------------+
|                                                                              |                        |                        |                        |                         |                       |                       |                      |                     |
+------------------------------------------------------------------------------+------------------------+------------------------+------------------------+-------------------------+-----------------------+-----------------------+----------------------+---------------------+
| Object-based Population Statistics ($2{,}784$ Apertures)                                                                                                                                                                                                                       |
+------------------------------------------------------------------------------+------------------------+------------------------+------------------------+-------------------------+-----------------------+-----------------------+----------------------+---------------------+
| $\left<M_\mathrm{obj,\,150pc}\right>$ \[$10^6\;\mathrm{M_\odot}$\]           | $4.2^{+6.1}_{-2.3}$    | $3.2^{+6.1}_{-2.0}$    | $2.9^{+4.9}_{-1.8}$    | $4.6^{+12.5}_{-3.0}$    | $11^{+30}_{-7}$       | $10^{+30}_{-7}$       | $6.9^{+10.5}_{-4.5}$ | $27^{+91}_{-21}$    |
+------------------------------------------------------------------------------+------------------------+------------------------+------------------------+-------------------------+-----------------------+-----------------------+----------------------+---------------------+
| $\left<R_\mathrm{obj,\,150pc}\right>$ \[$\mathrm{pc}$\]                      | –                      | $92^{+23}_{-21}$       | $91^{+22}_{-22}$       | $96^{+24}_{-19}$        | –                     | $95^{+21}_{-16}$      | $90^{+19}_{-15}$     | $100^{+20}_{-20}$   |
+------------------------------------------------------------------------------+------------------------+------------------------+------------------------+-------------------------+-----------------------+-----------------------+----------------------+---------------------+
| $\left<\Sigma_\mathrm{obj,\,150pc}\right>$ \[$\mathrm{M_\odot\,pc^{-2}}$\]   | $47^{+77}_{-28}$       | $35^{+64}_{-23}$       | $33^{+58}_{-20}$       | $45^{+102}_{-31}$       | $130^{+260}_{-90}$    | $110^{+250}_{-80}$    | $78^{+124}_{-50}$    | $210^{+560}_{-160}$ |
+------------------------------------------------------------------------------+------------------------+------------------------+------------------------+-------------------------+-----------------------+-----------------------+----------------------+---------------------+
| $\left<\sigma_\mathrm{obj,\,150pc}\right>$ \[$\mathrm{km\,s^{-1}}$\]         | –                      | $5.0^{+1.9}_{-1.4}$    | $4.8^{+1.6}_{-1.3}$    | $6.2^{+3.0}_{-1.7}$     | –                     | $6.7^{+3.7}_{-1.9}$   | $5.8^{+1.9}_{-1.5}$  | $9.0^{+3.6}_{-3.0}$ |
+------------------------------------------------------------------------------+------------------------+------------------------+------------------------+-------------------------+-----------------------+-----------------------+----------------------+---------------------+
| $\left<P_\mathrm{turb,\,obj,\,150pc}\right>$ \[$10^5\;\mathrm{K\,cm^{-3}}$\] | $1.0^{+3.3}_{-0.7}$    | $0.75^{+3.03}_{-0.57}$ | $0.65^{+2.20}_{-0.49}$ | $1.5^{+10.5}_{-1.2}$    | $4.7^{+31.8}_{-3.8}$  | $4.3^{+32.2}_{-3.6}$  | $2.1^{+7.2}_{-1.6}$  | $18^{+68}_{-16}$    |
+------------------------------------------------------------------------------+------------------------+------------------------+------------------------+-------------------------+-----------------------+-----------------------+----------------------+---------------------+
| $\left<\alpha_\mathrm{vir,\,obj,\,150pc}\right>$                             | –                      | $1.4^{+1.2}_{-0.6}$    | $1.3^{+1.0}_{-0.6}$    | $1.7^{+1.8}_{-0.8}$     | –                     | $1.1^{+0.9}_{-0.5}$   | $1.1^{+0.8}_{-0.4}$  | $1.0^{+1.2}_{-0.6}$ |
+------------------------------------------------------------------------------+------------------------+------------------------+------------------------+-------------------------+-----------------------+-----------------------+----------------------+---------------------+
| Pixel-based Population Statistics ($3{,}383$ Apertures)                                                                                                                                                                                                                        |
+------------------------------------------------------------------------------+------------------------+------------------------+------------------------+-------------------------+-----------------------+-----------------------+----------------------+---------------------+
| $\left<\Sigma_\mathrm{pix,\,150pc}\right>$ \[$\mathrm{M_\odot\,pc^{-2}}$\]   | $17^{+29}_{-9}$        | $12^{+27}_{-8}$        | $10^{+21}_{-7}$        | $21^{+64}_{-15}$        | $61^{+316}_{-43}$     | $55^{+294}_{-41}$     | $33^{+60}_{-22}$     | $200^{+840}_{-160}$ |
+------------------------------------------------------------------------------+------------------------+------------------------+------------------------+-------------------------+-----------------------+-----------------------+----------------------+---------------------+
| $\left<\sigma_\mathrm{pix,\,150pc}\right>$ \[$\mathrm{km\,s^{-1}}$\]         | –                      | $3.3^{+2.2}_{-1.0}$    | $3.1^{+1.6}_{-0.9}$    | $4.8^{+6.1}_{-2.0}$     | –                     | $5.9^{+14.0}_{-2.5}$  | $4.7^{+2.2}_{-1.7}$  | $16^{+11}_{-10}$    |
+------------------------------------------------------------------------------+------------------------+------------------------+------------------------+-------------------------+-----------------------+-----------------------+----------------------+---------------------+
| $\left<P_\mathrm{turb,\,pix,\,150pc}\right>$ \[$10^5\;\mathrm{K\,cm^{-3}}$\] | $0.29^{+1.92}_{-0.22}$ | $0.20^{+1.77}_{-0.16}$ | $0.16^{+0.95}_{-0.13}$ | $0.76^{+16.64}_{-0.68}$ | $3.4^{+230.1}_{-3.1}$ | $3.1^{+216.3}_{-2.8}$ | $1.1^{+5.4}_{-0.9}$  | $65^{+1064}_{-64}$  |
+------------------------------------------------------------------------------+------------------------+------------------------+------------------------+-------------------------+-----------------------+-----------------------+----------------------+---------------------+
| $\left<\alpha_\mathrm{vir,\,pix,\,150pc}\right>$                             | –                      | $1.7^{+1.1}_{-0.6}$    | $1.6^{+0.9}_{-0.6}$    | $2.5^{+1.7}_{-0.9}$     | –                     | $1.9^{+1.6}_{-0.6}$   | $1.6^{+0.9}_{-0.6}$  | $2.5^{+2.2}_{-1.0}$ |
+------------------------------------------------------------------------------+------------------------+------------------------+------------------------+-------------------------+-----------------------+-----------------------+----------------------+---------------------+
| $c_\mathrm{pix,\,150pc}$                                                     | $1.4^{+0.4}_{-0.3}$    | $1.9^{+1.1}_{-0.4}$    | $1.9^{+1.0}_{-0.4}$    | $1.9^{+1.2}_{-0.5}$     | $1.7^{+0.6}_{-0.3}$   | $1.9^{+1.0}_{-0.4}$   | $1.8^{+0.8}_{-0.4}$  | $2.1^{+1.2}_{-0.7}$ |
+------------------------------------------------------------------------------+------------------------+------------------------+------------------------+-------------------------+-----------------------+-----------------------+----------------------+---------------------+

: Statistics of Molecular Cloud Population Properties

Table notes: The median value and $\pm1\sigma$ range (i.e., $16{-}84$ percentile range) of the population average molecular cloud properties shown in Figure [4](#fig:hist_MC). Results in columns (2) to (5) are calculated by weighting each aperture equally, whereas those in columns (6) to (9) are calculated by weighting each aperture by the molecular gas mass it contains. Columns (2) and (6) correspond to measurements without applying completeness corrections (see Section [3.2.2](#sec:analysis:cloud:completeness)).

In summary, we observe substantial variations in the molecular cloud population-averaged properties across all apertures in our sample. The mass-weighted average of all clouds in PHANGS-ALMA yields high masses, large sizes, and low surface densities compared to the cloud population in our Galaxy. The contrast of cloud populations in galaxy disks and those in center/bar environments are qualitatively consistent with findings in previous extragalactic and Galactic studies. While the object-based and pixel-based results display qualitatively similar trends, there exist important quantitative discrepancies, which reflect their different measurement approaches in expected ways. Finally, after correcting for the completeness of CO detections, we find that the molecular gas in PHANGS-ALMA galaxies appears significantly less clumpy than previously determined from low sensitivity CO observations of a few very nearby galaxies.

# Environmental Dependence of Molecular Cloud Populations in PHANGS-ALMA

In the previous section, we see strong variations in both the molecular cloud populations and the host galaxy local environments from aperture to aperture. These variations are also known to correlate with each other — numerous studies have shown that the physical properties of molecular clouds depend on their host galaxy environment in various ways (see discussions in Section [1](#sec:intro)). The rich set of measurements derived in this study allow for a systematic characterization of such cloud–environment connections across an unprecedented range of physical conditions. In this section, we first summarize the basic, pairwise correlations between the population-averaged cloud properties and the local/global host galaxy properties (Section [5.1](#sec:corr:pairwise)). We then perform a variable selection method to identify a subset of host galaxy properties carrying the most predictive power, and to construct empirical predictive models for the molecular cloud properties (Section [5.2](#sec:corr:model)).

Both the pairwise correlation analysis and the variable selection procedure requires high quality measurements for the cloud population statistics. The latter also needs to be applied on a consistent sample of apertures that all have the relevant variables measured to good quality. To meet these requirements, this part of the analysis works with a subsample of $871$ apertures from 42 galaxies. These apertures are selected because: (1) they have the most complete multiwavelength data coverage, such that none of the cloud population statistics or host galaxy environmental metrics are missing; and (2) the PHANGS–ALMA CO data have reasonably high flux completeness and area coverage fraction inside these apertures ($f_\mathrm{flux}>0.5$ and $f_\mathrm{area}>0.2$, see Appendix [11](#apdx:completeness)), such that our measured cloud population statistics represent a significant portion of the molecular gas residing in that area. This down-selection primarily restricts our sample to regions with higher $\Sigma_\mathrm{mol}$ (with all apertures weighted equally, the median value and 16–84 percentile range is $14^{+17}_{-8}\;\mbox{$\rm M_\odot~pc^{-2}$}$ for the sub-sample, in comparison to $6.0^{+13.3}_{-4.1}\;\mbox{$\rm M_\odot~pc^{-2}$}$ for the parent sample). Consequently, it also tends to select apertures in more massive, molecular gas-rich galaxies and at smaller $r_\mathrm{gal}$ within each galaxy ($4.4^{+2.4}_{-1.8}\rm\;kpc$ for the sub-sample versus $5.4^{+3.1}_{-2.7}\rm\;kpc$ for the parent sample). Nevertheless, the selected apertures still cover a considerable range of the relevant parameter space to allow for the following analyses.

## Pairwise Correlation

To provide an empirical characterization of the observed cloud–environment connections, we calculate Spearman’s rank correlation coefficients for each pair of population-averaged molecular cloud property and host galaxy environmental metric within the sub-selected $871$ apertures. For this analysis, we consider seven local environmental metrics ($r_\mathrm{gal}$, $\Sigma_\mathrm{mol}$, $\Sigma_\mathrm{atom}$, $\Sigma_\mathrm{\star}$, $\Sigma_\mathrm{SFR}$, $\Omega_\mathrm{circ}$, and $A_\mathrm{Oort}$), each of which holds a unique piece of information unavailable to all other variables. We complement these local properties with five global galaxy properties ($r_\mathrm{disk}$, $M_\mathrm{mol}$, $M_\mathrm{atom}$, $M_\star$, and SFR), so that our correlation analysis can also capture galaxy-to-galaxy trends. These global properties are measured by (cite: Leroy_etal_2021a) for all PHANGS-ALMA galaxies.

The top left part of Figure [5](#fig:corr_all) summarize the outcome of this pairwise analysis. Broadly speaking, we find significant correlations between most pairs of population-averaged cloud properties and environmental metrics. The signs of the correlation coefficients indicate that an average molecular cloud tends to be denser, more massive, more turbulent, and more strongly self-gravitating at places that are closer to the galaxy center, have higher gas and stellar content, show more active star formation, and feature shorter orbital period and stronger local shear. The correlations of population-averaged cloud properties versus global galaxy properties are weaker, but most of them are statistically significant. These findings agree well with previous observations targeting individual galaxy or smaller galaxy samples (see references in Section [1](#sec:intro)).

Beyond these general trends, we highlight three interesting patterns in Figure [5](#fig:corr_all). First, most molecular cloud properties show the strongest correlation with the (kpc-scale) aperture-averaged molecular gas surface density, $\Sigma_\mathrm{mol}$. While some systematic effects (e.g., uncertainties in the CO-to-$\mathrm{H}_2$ conversion factor or calibrations of the raw data) could influence both the independent and dependent variables here, these correlations, including the ones regarding cloud surface densities, still carry real information about multi-scale structures in the molecular gas. Specifically, the correlation strength between the cloud-scale and kpc-scale surface densities partly reflects the inhomogeneity of the molecular gas on spatial scales between 1.5 kpc (aperture size) and $60{-}150$ pc (data resolution). The limiting case of a perfect correlation appears only if the gas distribution is completely homogeneous, or if it is structured in a way that the clumping factor is the same in all apertures (which is not far from the reality given the narrow range of clumping factors observed across our sample; see Section [4.2](#sec:stats:MC)). On the contrary, we would expect no correlation if all molecular gas is concentrated into small, isolated clouds with fixed surface densities.

Second, for the cloud radius and virial parameter, the correlations with environmental metrics are weaker compared to the other cloud properties. This is mainly due to the narrow dynamic range of these quantities in our data. For the cloud radius, the narrow range is somewhat imposed by the limited data resolution and our adopted object identification algorithm (see Section [2.1.1](#sec:data:CO:obj) and [4.2](#sec:stats:MC)). For the virial parameter, the narrow range across our sample is more intrinsic and reflects the relative uniformity of the cloud dynamical state (cite: Sun_etal_2018; Sun_etal_2020b; Rosolowsky_etal_2021).

Third, when comparing some of the local environmental metrics to their corresponding “integrated”, galaxy global measurements (i.e., $\Sigma_\mathrm{mol}$–$M_\mathrm{mol}$, $\Sigma_\mathrm{atom}$–$M_\mathrm{atom}$, $\Sigma_\mathrm{\star}$–$M_\star$, and $\Sigma_\mathrm{SFR}$–SFR), the correlation coefficients for the latter are always smaller. One possible explanation is that the correlations between cloud populations and their local environment are more fundamental, to the extent that all galaxy-to-galaxy trends arise as their consequences. In other words, the apparent relationships between cloud populations and global galaxy properties might be completely *mediated* by the local properties. This hypothesis is challenging to test based on the pairwise correlation coefficients alone, as the strengths of mutual correlations between the independent variables (a.k.a., multicollinearity) are not explicitly modeled.

The issue of multicollinearity is in fact a general concern that impacts more than the local–global quantity pairs identified above. Many local environmental metrics considered here are known to follow scaling relations (cite: Kennicutt_Evans_2012; Sanchez_etal_2021), and the same is true for the global galaxy properties (cite: Saintonge_Catinella_2022). This issue poses challenges to determining whether there are any secondary trends on top of the cloud–environment relationships with the largest correlation coefficients. To quantify the severity of this issue, the bottom left part of Figure [5](#fig:corr_all) shows the variance inflation factors (VIFs) of the same independent variable set. A larger VIF means that a larger fraction of variations in that particular independent variable can be explained by the other independent variables. The VIFs for many variables exceed commonly adopted cutoff values of $5{-}10$ (cite: James_etal_2013), signaling strong multicollinearity.

In the following section, we address this issue of multicollinearity with an information criterion-based variable selection method.

## Variable Selection

The goal of this section is to identify a subset of environmental metrics that are most directly relevant for setting each population-averaged cloud property. We attempt to distinguish the most fundamental cloud–environment correlations from the ones that likely arise as indirect consequences of covariance among environment metrics. Here we distinguish these underlying relations through variable selection. For each cloud property (as a target variable), we compose an empirical predictive model using a minimal set of environmental metrics (feature variables) that carry most predictive power. This approach has the advantage of removing irrelevant feature variables while optimizing prediction accuracy in the face of multicollinearity. While this approach is still limited by the precision at which we can estimate each quantity of interest, it is an effective way to collapse a high-dimensional data set into concise and highly interpretable predictive models.

### Variable Selection Methodology

The basis of this analysis is a multivariable linear regression in the logarithmic space. That is, we restrict the model functional forms to simple linear combinations of logarithmic variables (including an intercept term), which are equivalent to products of power-laws of the original variables (with a normalization constant). The regression is done independently for each population-averaged cloud property as a target variable, using all the environmental metrics in Figure [5](#fig:corr_all) as available features. Although we have applied inclination corrections to the measured cloud properties, we still include $\cos{i}$ as an extra feature to capture residual trends with inclination when they are present. After converting our feature and target variables to their logarithms, we median-subtract all features to further reduce correlations between the fitting variables (i.e., power-law slopes versus the normalization constant).

With this regression setup, we perform a *lasso* model fit (cite: Tibshirani_1996) and use the Bayesian Information Criterion (cite: Schwarz_1978) for model selection. This is implemented with the `LassoLarsIC` function in the `scikit-learn` Python library. In detail, for a linear predictive model with the form $\hat{y_i} = \beta_0 + \sum_{j=1}^m\beta_j x_{ij}$, the *lasso* regression minimizes the following objective function: $$\begin{equation}
\frac{1}{2n} \sum_{i=1}^n(y_i-\hat{y_i})^2 +
\alpha \sum_{j=1}^m|\beta_j|~.
\label{eq:lasso}
\end{equation}$$ Here $i=1,2,...,n$ is the index of data (index of averaging aperture in our case) and $j=1,2,...,m$ is the index of features in the model. The $\alpha$ parameter is a non-negative hyper-parameter, so that the second term in Equation [\[eq:lasso\]](#eq:lasso) adds a penalty for the use of any non-zero slope in the fitted model. This particular “regularization” term is the reason that the *lasso* as a regression method can also be used for variable selection.

The *lasso* regression yields a best-fit model that minimizes Equation [\[eq:lasso\]](#eq:lasso) for each choice of the $\alpha$ parameter. To guide subsequent model selection, we calculate the BIC value for each such model via $$\begin{equation}
\mathrm{BIC} = n \ln(2 \pi \sigma^2) + \frac{\sum_{i=1}^{n} (y_i - \hat{y}_i)^2}{\sigma^2} + d\ln(n)~,
\end{equation}$$ where $d$ is the number of features with non-zero slope in that particular model, and $\sigma^2$ is the noise variance for the target variable. This expression of BIC is derived from its formal definition of $d\ln(n)-2\ln(\hat{L})$ assuming Gaussian error, with $\hat{L}$ being the maximum of the likelihood function. It is consistent with other definitions in the literature (cite: James_etal_2013) up to irrelevant constants.

For the noise variance $\sigma^2$, the contribution from statistical uncertainties is generally small for our measurements (typical fractional error ${\sim}$1–10%). We thus expect several sources of systematic uncertainties on the level of at least 0.1–0.3 dex to dominate the total noise variance. These sources include (but are not limited to) the estimated $\alpha_\mathrm{CO}$ and the adopted $R_\mathrm{21}$ values, the unknown sub-resolution gas spatial and kinematic structures, and calibrations of the ALMA data. Considering these uncertainties, we conservatively use a noise variance of $\sigma^2=0.1\;\mathrm{dex}^2$ (i.e., about a factor of 2) for the cloud masses, sizes, surface densities, and velocity dispersions. We use a larger variance of $\sigma^2=0.25\;\mathrm{dex}^2$ (i.e., about a factor of 3) for the turbulent pressures and virial parameters, as they are particularly sensitive to the assumed geometry of the gas.

To complete the model selection procedure, we compare the BIC of all candidate models to their minimum ($\mathrm{BIC_{min}}$) and identify a subset of candidate models that satisfy $\Delta\mathrm{BIC}\equiv\mathrm{BIC}-\mathrm{BIC_{min}}\leq10$ (cite: Kass_Raftery_1995). Among this subset, we select the one model that corresponds to the largest $\alpha$ value, which typically includes the fewest features. This last step allows us to further suppress any less relevant features, as there is less strong evidence for their inclusion in the model.

### Variable Selection Outcomes

|  |  |  |  |
|:---|:--:|:--:|:--:|
| Model | Residual \[dex\] | $R^2$ | $\Delta\mathrm{BIC}$ |
|  |  |  |  |
| $\frac{\left<M_\mathrm{obj,150pc}\right>}{10^6\rm\;M_\odot}=10^{0.59}\,\left(\frac{\Sigma_\mathrm{mol}}{10\rm\;M_\odot\,pc^{-2}}\right)^{0.75}\,\left(\cos{i}\right)^{-0.50}$ | 0.17 | 0.70 | 678.18 |
| $\frac{\left<R_\mathrm{obj,150pc}\right>}{10\rm\;pc}=10^{0.99}$ | 0.09 | 0.00 | – |
| $\frac{\left<\Sigma_\mathrm{obj,150pc}\right>}{10^2\rm\;M_\odot\,pc^{-2}}=10^{-0.37}\,\left(\frac{\Sigma_\mathrm{mol}}{10\rm\;M_\odot\,pc^{-2}}\right)^{0.78}\,\left(\frac{\Sigma_\mathrm{SFR}}{10^{-2}\rm\;M_\odot\,yr^{-1}\,kpc^{-2}}\right)^{0.08}$ | 0.19 | 0.74 | 968.54 |
| $\frac{\left<\Sigma_\mathrm{pix,150pc}\right>}{10^2\rm\;M_\odot\,pc^{-2}}=10^{-0.65}\,\left(\frac{\Sigma_\mathrm{mol}}{10\rm\;M_\odot\,pc^{-2}}\right)^{0.77}\,\left(\frac{\Sigma_\mathrm{SFR}}{10^{-2}\rm\;M_\odot\,yr^{-1}\,kpc^{-2}}\right)^{0.13}$ | 0.14 | 0.85 | 1046.80 |
| $\frac{\left<\sigma_\mathrm{obj,150pc}\right>}{10\rm\;km\,s^{-1}}=10^{-0.24}\,\left(\frac{\Sigma_\mathrm{mol}}{10\rm\;M_\odot\,pc^{-2}}\right)^{0.10}\,\left(\frac{\Sigma_\mathrm{SFR}}{10^{-2}\rm\;M_\odot\,yr^{-1}\,kpc^{-2}}\right)^{0.06}$ | 0.10 | 0.32 | 32.82 |
| $\frac{\left<\sigma_\mathrm{pix,150pc}\right>}{10\rm\;km\,s^{-1}}=10^{-0.33}\,\left(\frac{\Sigma_\mathrm{mol}}{10\rm\;M_\odot\,pc^{-2}}\right)^{0.18}\,\left(\frac{\Sigma_\mathrm{SFR}}{10^{-2}\rm\;M_\odot\,yr^{-1}\,kpc^{-2}}\right)^{0.08}$ | 0.11 | 0.52 | 119.87 |
| $\frac{\left<P_\mathrm{turb,obj,150pc}\right>}{10^4\rm\;K\,cm^{-3}}=10^{1.07}\,\left(\frac{\Sigma_\mathrm{mol}}{10\rm\;M_\odot\,pc^{-2}}\right)^{0.93}\,\left(\frac{\Sigma_\mathrm{SFR}}{10^{-2}\rm\;M_\odot\,yr^{-1}\,kpc^{-2}}\right)^{0.28}$ | 0.30 | 0.69 | 764.43 |
| $\frac{\left<P_\mathrm{turb,pix,150pc}\right>}{10^4\rm\;K\,cm^{-3}}=10^{0.87}\,\left(\frac{\Sigma_\mathrm{mol}}{10\rm\;M_\odot\,pc^{-2}}\right)^{1.05}\,\left(\frac{\Sigma_\star}{10^2\rm\;M_\odot\,pc^{-2}}\right)^{0.08}\,\left(\frac{\Sigma_\mathrm{SFR}}{10^{-2}\rm\;M_\odot\,yr^{-1}\,kpc^{-2}}\right)^{0.39}$ | 0.34 | 0.71 | 1104.86 |
| $\left<\alpha_\mathrm{vir,obj,150pc}\right>=10^{0.15}\,\left(\frac{\Sigma_\mathrm{mol}}{10\rm\;M_\odot\,pc^{-2}}\right)^{-0.30}\,\left(\frac{\Omega_\mathrm{circ}}{30\rm\;Gyr^{-1}}\right)^{0.27}\,\left(\frac{A_\mathrm{Oort}}{10\rm\;km\,s^{-1}\,kpc^{-1}}\right)^{0.14}\,\left(\cos{i}\right)^{0.26}$ | 0.20 | 0.35 | 49.23 |
| $\left<\alpha_\mathrm{vir,pix,150pc}\right>=10^{0.25}\,\left(\frac{A_\mathrm{Oort}}{10\rm\;km\,s^{-1}\,kpc^{-1}}\right)^{0.13}$ | 0.19 | 0.09 | 6.72 |

: Power-law Predictive Models

Table notes: The first column lists the power-law predictive models given by the *lasso* regression and BIC-based model selection (Section [5.2](#sec:corr:model)). The second column shows the residual scatters around these models. The third column quotes the coefficients of determination, i.e., the fraction of variation in the dependent variable that is explained by the model. The last column records the BIC difference between the selected model and a null model with only the normalization term.

With the *lasso* regression and the BIC-based model selection, we find a set of “preferred” power-law predictive models, whose analytical forms are tabulated in Table [3](#tab:models). We also report in Table [3](#tab:models) the model residual scatter, the model coefficient of determination ($R^2$, which quantifies the model explanatory power), and the BIC difference between the preferred model and a null model with only the normalization term. Figure [6](#fig:lasso_path) illustrates the full path of the *lasso* regression up to the “preferred” model. The model residual scatter reduces as each new feature variable is added into the model.

We find that only a small number ($0{-}4$) of environmental metrics are included in the preferred model for each molecular cloud property, which means that most of the correlations in Figure [5](#fig:corr_all) can be attributed to a more concise set of fundamental correlations. This result is in sharp contrast to the impression one would get from the correlations in Figure [5](#fig:corr_all), which indicates ubiquitous, significant trends for nearly all local and global galaxy properties. Evidently, for most galactic properties considered in this work, their apparent correlations with molecular cloud properties are potentially explicable via their covariance with other galaxy properties, such that the predictive models need only a few variables. Once the modulating effect of those few variables are accounted for, we see no evidence that the remainder play a significant role at the current precision level of our measurements.

Our variable selection exercise allows us to draw some interesting conclusions based on the functional form of the power-law predictive models in Table [3](#tab:models). First of all, the absence of global galaxy properties (except inclination angle, see below) in these models implies that their correlations with cloud properties are not fundamental: these correlations probably originate from the tighter connections between molecular clouds and their local (sub-galactic) environment. As star-forming galaxies follow various scaling relations, galaxies with larger size, mass, and SFR would include more sub-galactic regions with higher mass and SFR surface densities, which subsequently entails cloud populations with higher average masses, surface densities, velocity dispersions, and turbulent pressures. This is likely the driver of the observed systematic variations in molecular cloud properties from galaxy to galaxy (cite: Hughes_etal_2013a; Sun_etal_2020a; Rosolowsky_etal_2021).

Furthermore, the galactocentric radius $r_\mathrm{gal}$ does not appear in any of the predictive models either. Given that most physical properties of the host galaxy (including many not considered in this work) are strong functions of galactocentric radius, its general absence in the predictive models is rather encouraging. It suggests that those environmental metrics included in the models are doing a decent job in capturing most systematic trends: they likely make better proxies than $r_\mathrm{gal}$ for many relevant physical quantities not considered in this work (e.g., radiation field, magnetic field, and cosmic ray strength).

The predictive models for specific molecular cloud properties also provide insights into various aspects of molecular cloud formation and evolution. Below we comment on these models individually:

- *Molecular cloud mass.* The average molecular cloud mass shows primary dependence on the kpc-scale molecular gas surface density and galaxy inclination: together, these two quantities can explain 70% of all variations. On the one hand, we can make sense of the former dependence in light of the theoretical expectation that gravitationally unstable gas disks tend to fragment into objects at a specific mass scale (i.e., the Toomre mass). This mass scale is often linked to the local gas surface density and the disk vertical scale height $H$ via $M_T \approx \pi H^2 \Sigma_\mathrm{mol}$ (cite: Murray_etal_2010). While $H$ is not available for variable selection, our derived predictive models for molecular cloud mass do exhibit slightly sub-linear dependencies on $\Sigma_\mathrm{mol}$. This is consistent with the expected anti-correlation between $\Sigma_\mathrm{mol}$ and $H$, as $\Sigma_\mathrm{mol}$ rapidly declines with galactocentric radius, while $H$ mildly increases with it in the inner part of nearby disk galaxies (cite: Yim_etal_2011; Yim_etal_2014).

  On the other hand, a non-trivial portion of the trends with $\Sigma_\mathrm{mol}$ and $\cos{i}$ could originate from observational and methodological limitations. The nearly constant cloud radii given by CPROPS, in combination with small clumping factors (see Section [4.2](#sec:stats:MC)), would naturally produce strong correlations between masses of the identified clouds and the large-scale $\Sigma_\mathrm{mol}$. The additional $\cos{i}$ dependence also signifies stronger source blending in more inclined galaxies, despite CPROPS’s attempt to deblend based on information in the velocity space (see Section [2.1.1](#sec:data:CO:obj)). Therefore, any attempt to interpret the predictive model should also take these non-physical factors into consideration.

- *Molecular cloud radius.* The BIC-based variable selection favors the “null” model for the average molecular cloud radius, i.e., the one that includes only a normalization term and nothing else. In other words, there is no strong evidence that any of the environmental metrics considered here can effectively predict the (small) variations in the cloud radius. This agrees with the notion that the sizes of the CPROPS-identified objects are more influenced by algorithm-related factors (e.g., deblending criteria) and data characteristics (e.g., beam size; see Figure [11](#fig:resolution)) than physical properties of the gas or the host galaxy environment (cite: Hughes_etal_2013a; Rosolowsky_etal_2021).

- *Molecular cloud surface density.* For this quantity (measured with either object-based or pixel-based approach), we find significant, secondary trends with $\Sigma_\mathrm{SFR}$ on top of the prominent correlations with the large-scale $\Sigma_\mathrm{mol}$. A possible explanation is that regions with more clumpy molecular gas (i.e., larger clumping factor, higher $\left<\Sigma_\mathrm{150\,pc}\right>/\Sigma_\mathrm{mol}$ ratio) are possibly more subject to gravitational instabilities and the gas there has more chance to form stars. This points at a possibility that knowing the molecular gas clumping factor on 60–150 pc scales could allow for better prediction of $\Sigma_\mathrm{SFR}$ at a given $\Sigma_\mathrm{mol}$ on kpc scales (cite: Schmidt_1959; Kennicutt_1998).

  It is also worth noting that the preferred models for the average cloud surface densities do not include a $\cos{i}$ dependent term. Though partly by construction, this still affirms the effectiveness of the inclination correction on the cloud surface densities (see Section [2.1.1](#sec:data:CO:obj) and [2.1.2](#sec:data:CO:pix) as well as Appendix [10](#apdx:inclination)).

- *Molecular gas clumping factor.* We do not separately construct a power-law predictive model for the clumping factor because this quantity can be well approximated by $\left<\Sigma_\mathrm{pix}\right>/\Sigma_\mathrm{mol}$ when the data sensitivity is sufficiently high (see Section [3.2.1](#sec:analysis:cloud:clumping)). Instead, one can easily derive a predictive model for this quantity by dividing the model for $\left<\Sigma_\mathrm{pix}\right>$ by $\Sigma_\mathrm{mol}$.

- *Molecular cloud velocity dispersion.* The preferred models for this quantity include the same environmental metrics, $\Sigma_\mathrm{mol}$ and $\Sigma_\mathrm{SFR}$, as the models for the cloud surface densities. Since molecular gas surface density and velocity dispersion correlate strongly even on a cloud-to-cloud level (see discussions in Section [1](#sec:intro)), it is not surprising that the same environmental metrics turn out to be most relevant for both molecular cloud properties after population averaging. However, the preferred predictive models for the cloud velocity dispersion explain a much less fraction of its total observed scatter (32–52%) compared to those for the cloud surface density (74-85%). At least part of this is attributable to the latter fraction being exaggerated, because the cloud-scale and kpc-scale molecular gas surface densities tend to co-vary for many non-physical reasons (e.g., relying on the same conversion factor). It is also possible that the physical drivers of gas velocity dispersion variations are less well-captured by the set of environmental metrics included in this work (cite: Krumholz_Burkert_2010).

- *Molecular cloud turbulent pressure.* The functional forms of the preferred models for this cloud property are broadly consistent with the expectation from the models for the average cloud surface density and velocity dispersion. Interestingly, the preferred model for the pixel-based turbulent pressure also includes an extra term depending on the large-scale stellar mass surface density, $\Sigma_\mathrm{\star}$, albeit with a small power-law index (0.08). Adding this term improves the model $R^2$ by only a small amount (from $0.70$ to $0.71$; see Figure [6](#fig:lasso_path)), but it lowers the model BIC by more than 10, which means that our data clearly favor the model with an extra dependence on $\Sigma_\mathrm{\star}$. This extra dependence is in line with theoretical models proposing that molecular clouds can be influenced by the external gravitational potential of the host galaxy stellar disk (cite: Meidt_etal_2018; Meidt_etal_2020; Sun_etal_2020b; LiuLJ_etal_2021).

- *Molecular cloud virial parameter.* For this quantity, the preferred models for the object-based and pixel-based results show the largest deviation. The preferred model for the object-based measurement includes four galaxy properties ($\Sigma_\mathrm{mol}$, $\Omega_\mathrm{circ}$, $A_\mathrm{Oort}$, and $\cos{i}$), whereas that for the pixel-based only includes $A_\mathrm{Oort}$. This difference is probably related to the narrower dynamic range in $\left<\alpha_\mathrm{vir,\,pix,\,150pc}\right>$ than in $\left<\alpha_\mathrm{vir,\,obj,\,150pc}\right>$ (see Section [4.2](#sec:stats:MC)).

  Moreover, the appearance of $\Omega_\mathrm{circ}$, $A_\mathrm{Oort}$, and $\cos{i}$ in the models points at potential influence of galactic rotation on the inferred cloud dynamical state. Particularly, if the measured velocity dispersion includes contributions from differential galactic rotation (i.e., beam smearing), it would lead to positive correlations with $\Omega_\mathrm{circ}$ and $A_\mathrm{Oort}$ because they reflect the strength of the differential motion, and with $\cos{i}$ because the beam smearing effect is more prominent in more inclined galaxies.

In summary, through the *lasso* regression and BIC-based model selection we compose power-law predictive models for all population averaged molecular cloud properties. These models capture the primary cloud–environment correlations with at most four environmental metrics as independent variables. The most commonly involved environmental metrics in these models are the large-scale molecular gas surface density, $\Sigma_\mathrm{mol}$, and SFR surface density, $\Sigma_\mathrm{SFR}$. Furthermore, the general absence of global galaxy properties in these models suggests that galaxy-to-galaxy variations in molecular cloud populations might be the mere consequences of their tighter connections with sub-galactic environments.

# Characteristic Timescales of Molecular Cloud Evolution in PHANGS–ALMA

Molecular cloud formation and evolution are influenced by a number of physical processes including turbulence driving and cascade, gravitational collapse, galactic rotation and shearing motions, cloud–cloud collisions, and gas depletion due to star formation. These processes not only operate over a vast span of spatial scales, but also feature different characteristic timescales. Estimating their timescales across diverse galactic environments allows us to demonstrate the balance (or not) between these processes and infer how star formation is regulated under distinct physical conditions (cite: Wong_2009; Jeffreson_Kruijssen_2018; Kruijssen_etal_2019b; Chevance_etal_2020a; Chevance_etal_2020b; KimJY_etal_2020).

In this section, we estimate six different characteristic timescales as a use case demonstration for our rich multiwavelength measurements. We detail the definition and derivation of each timescale in Section [6.1](#sec:timescales:method), and compare the quantitative results in Section [6.2](#sec:timescales:results).

## Timescale Definitions

- *Free-fall time, $t_\mathrm{ff}$.* This is the timescale for a molecular cloud to collapse in free-fall due to self-gravity, provided no pressure support to counterbalance it. We estimate this timescale from the mean volume density of molecular clouds under the assumption of spherical symmetry. The population-average free fall time, $\bar{t}_\mathrm{ff}$, is subsequently calculated via $$\begin{equation}
      \frac{1}{\bar{t}_\mathrm{ff}}
      = \left<\frac{1}{t_\mathrm{ff}}\right>
      \simeq \left<\sqrt{\frac{32G \rho_\mathrm{mol}}{3\pi}}\right>
      = \left<\sqrt{\frac{8G M_\mathrm{mol}}{\pi^2 R_\mathrm{cloud}^3}}\right>~.
      \label{eq:t_ff}
  \end{equation}$$ Here $M_\mathrm{mol}$ and $R_\mathrm{cloud}$ are the cloud mass and radius, estimated from either object- or pixel-based approaches[^8]. The “$\left<\right>$” symbol denotes the same mass-weighted averaging scheme as defined in Section [3.1](#sec:analysis:aperture). We define this population-averaged free fall time as a *mass-weighted harmonic mean* so that it appropriately reflects the overall timescale for the whole cloud population[^9] (cite: Jeffreson_Kruijssen_2018; Utomo_etal_2018). We apply a similar completeness correction to this measurement as we did for the other population-averaged cloud properties (see Appendix [11](#apdx:completeness) for more detail).

- *Turbulence crossing time, $t_\mathrm{cr}$.* This is the timescale for the turbulent flow to cross the span of a molecular cloud. We drive it from the cloud radius and the (one-dimensional) turbulent velocity dispersion, and then calculate the mass-weighted harmonic mean as $$\begin{equation}
      \frac{1}{\bar{t}_\mathrm{cr}}
      = \left<\frac{1}{t_\mathrm{cr}}\right>
      \simeq \left<\frac{\sigma_\mathrm{mol}}{R_\mathrm{cloud}}\right>.
      \label{eq:t_cr}
  \end{equation}$$ Here $R_\mathrm{cloud}$ and $\sigma_\mathrm{mol}$ are the radius and one-dimensional velocity dispersion of individual molecular clouds, again derived from either object-based or pixel-based analyses (see Sections [2.1.1](#sec:data:CO:obj) to [2.1.2](#sec:data:CO:pix)). Under this definition, the crossing time is related to the free-fall time and the virial parameter via $t_\mathrm{ff}/t_\mathrm{cr} \approx 0.50\,\alpha_\mathrm{vir}^{0.5}$. Therefore, the crossing time of a virialized molecular cloud would be roughly two times longer than its free-fall time.

- *Orbital time, $t_\mathrm{orb}$.* This is the period of the orbital revolution around the galaxy center. We derive it from the orbital angular velocity measured from the CO rotation curves (see Section [2.5](#sec:data:rotcurve)): $$\begin{equation}
      t_\mathrm{orb} = 2\pi/\Omega_\mathrm{circ}~.
      \label{eq:t_orb}
  \end{equation}$$

- *Shearing time, $t_\mathrm{shear}$.* This is the timescale for two objects to move closer/farther by a unit length azimuthally, given that they are on two circular orbits separated radially by the same unit length. It equals the reciprocal of Oort’s $A$ parameter (see Section [2.5](#sec:data:rotcurve)): $$\begin{equation}
      t_\mathrm{shear} = A_\mathrm{Oort}^{-1} = \frac{2}{\Omega_\mathrm{circ}\,(1-\beta)}~.
      \label{eq:t_shear}
  \end{equation}$$

- *Cloud–cloud collision time, $t_\mathrm{coll}$.* Most generally, this is the timescale for any *particular* molecular cloud to collide with another cloud (i.e., it is *not* the timescale for such collisions to happen within a given area). We estimate this timescale following a simplified model of shear-induced collision (cite: Tan_2000). The key assumptions are that molecular clouds are randomly distributed in each aperture, and that cloud–cloud collision happens *only* when clouds catch up with other clouds on adjacent circular orbits due to orbital shear. In this scenario, we can estimate a population-averaged collision time, $\bar{t}_\mathrm{coll}$, via: $$\begin{align}
      \frac{1}{\bar{t}_\mathrm{coll}}
      = \left<\frac{2v_\mathrm{shear}}{\lambda_\mathrm{mfp}}\right>
      &\simeq \left<\frac{2R_\mathrm{cloud}/t_\mathrm{shear}}{(2R_\mathrm{cloud}N_\mathrm{cloud})^{-1}}\right> \nonumber\\
      &= \frac{4}{t_\mathrm{shear}}N_\mathrm{cloud}\left<R_\mathrm{cloud}^2\right>~.
      \label{eq:t_coll}
  \end{align}$$ Here $v_\mathrm{shear} \simeq R_\mathrm{cloud}/t_\mathrm{shear}$ is the shear velocity of two orbits separated radially by $R_\mathrm{cloud}$, the average impact parameter among all collisions. $\lambda_\mathrm{mfp} \simeq (2R_\mathrm{cloud}N_\mathrm{cloud})^{-1}$ is the mean free path of cloud–cloud collisions given a linear cross section of $2R_\mathrm{cloud}$ and an area number density of $N_\mathrm{cloud}$. The extra factor of 2 on the numerator accounts for the fact that the other cloud can be located on either an inner orbit (smaller $r_\mathrm{gal}$) or an outer orbit (larger $r_\mathrm{gal}$) relative to the cloud in question (cite: Tan_2000).

  Equation [\[eq:t_coll\]](#eq:t_coll) makes it straightforward to estimate $\bar{t}_\mathrm{coll}$ from measurable quantities in the object-based approach (or specifically, $N_\mathrm{cloud}$ as area density of identified objects and $\left<R_\mathrm{cloud}^2\right>$ as mass-weighted average of object radius squared). Yet it is not trivial to measure them with the pixel-based approach in a totally symmetric way. Alternatively, we follow a similar line of reasoning as (cite: Tan_2000) to approximate $\bar{t}_\mathrm{coll}$ from other pixel-based measurements: $$\begin{align}
      \frac{1}{\bar{t}_\mathrm{coll}}
      \simeq \frac{4}{t_\mathrm{shear}}N_\mathrm{cloud}\,R_\mathrm{cloud}^2
      &\simeq \frac{4}{t_\mathrm{shear}}\frac{\Sigma_\mathrm{mol}}{\pi\Sigma_\mathrm{cloud}} \nonumber\\
      &\simeq \frac{4}{\pi\,t_\mathrm{shear}\,c_\mathrm{pix}}~.
      \label{eq:t_coll_pix}
  \end{align}$$ The second step assumes all molecular gas is concentrated into clouds with characteristic surface densities $\Sigma_\mathrm{cloud}$ and radii $R_\mathrm{cloud}$, such that $\Sigma_\mathrm{mol}\approx N_\mathrm{cloud}\, (\Sigma_\mathrm{cloud}\,\pi R_\mathrm{cloud}^2$). The third step follows from the definition of the molecular gas clumping factor, $c_\mathrm{pix}$, as the contrast between molecular gas surface densities on cloud scales and kpc scales (cite: Leroy_etal_2013b).

  We caution that the simplifying assumptions involved in Equations [\[eq:t_coll\]](#eq:t_coll) and [\[eq:t_coll_pix\]](#eq:t_coll_pix) likely bias our $\bar{t}_\mathrm{coll}$ estimates high. In reality, molecular clouds are not evenly distributed and have random motions in addition to circular rotation (cite: Dobbs_etal_2015). Possible blending of multiple clouds in a single beam or a single identified object can also lead to longer estimated collision timescales than reality.

- *Molecular gas depletion time, $t_\mathrm{dep,\,mol}$.* This is the timescale to convert all molecular gas into stars at the current SFR, provided no other sources or sinks for the gas: $$\begin{equation}
      t_\mathrm{dep,\,mol} = \Sigma_\mathrm{mol}/\Sigma_\mathrm{SFR}~.
      \label{eq:t_dep}
  \end{equation}$$

## Timescale Comparisons

Figure [7](#fig:timescales) shows the statistical distributions of all six timescales, including their variants derived from object- or pixel-based measurements. For reference, we also mark the range of molecular cloud lifetimes, $t_\mathrm{life}$, measured from the spatial (de-)correlation of molecular gas and young star tracers in a subset of PHANGS–ALMA targets (cite: Chevance_etal_2020a; Chevance_etal_2020b; KimJY_etal_2020). Table [4](#tab:stats_timescales) summarizes the median values and $1\sigma$ ranges of all our estimated timescales.

Based on Figure [7](#fig:timescales) and Table [4](#tab:stats_timescales), we can identify three distinct groups of timescales separated by roughly an order of magnitude apart from each other. The first group consists of $\bar{t}_\mathrm{ff}$ and $\bar{t}_\mathrm{cr}$, both around $5{-}20~\mbox{$\rm Myr$}$. These timescales correspond to physical processes taking place inside molecular clouds. The median values of $t_\mathrm{ff}$ and $t_\mathrm{cr}$ differs by less than a factor of two, which is no more than a restatement that most molecular clouds have virial parameters of order unity. Furthermore, they appear comparable to (or only slightly shorter than) $t_\mathrm{life}$, as seen in previous observations and simulations[^10] (cite: Fukui_etal_1999; Elmegreen_2000; Kawamura_etal_2009; Murray_2011; Grudic_etal_2018; Kim_etal_2018; Kruijssen_etal_2019b; Benincasa_etal_2020a; Chevance_etal_2020a). This is not inconsistent with our estimated $\alpha_\mathrm{vir}=1{-}2$, as even clouds in free-fall collapse can yield apparent virial parameters of ${\sim}2$ (cite: Ballesteros-Paredes_etal_2011a; Camacho_etal_2016).

The second group of timescales consists of $t_\mathrm{shear}$, $t_\mathrm{orb}$, and $\bar{t}_\mathrm{coll}$, all of which are ${\sim}100~\mbox{$\rm Myr$}$. These timescales characterize dynamical processes taking place on kpc scales or even over entire galaxies. The order of magnitude contrast between them and the cloud “internal” timescales discussed above implies that the effects of galactic-scale dynamics on individual molecular clouds are likely modest. More specifically, $t_\mathrm{shear}\gg\bar{t}_\mathrm{cr}\;\text{or}\;\bar{t}_\mathrm{ff}$ indicates that shearing motions are generally small on cloud scales relative to motions generated by turbulence or gravitational collapse (cite: Utreras_etal_2020); $t_\mathrm{orb}\gg t_\mathrm{life}$ means that molecular clouds can only last a small fraction of a complete orbital revolution around the galaxy center (cite: Chevance_etal_2020a); and $\bar{t}_\mathrm{coll}\gg t_\mathrm{life}$ suggests that cloud–cloud collisions do not happen to most molecular clouds throughout their lifetimes (cite: Blitz_Shu_1980; Jeffreson_Kruijssen_2018).

The last group consists of $t_\mathrm{dep,\,mol}$ by itself, which is about $1{-}3$ Gyr across our sample. This range is consistent with many previous studies on the molecular dominated regions in nearby, massive, star-forming galaxies (cite: Bigiel_etal_2008; Leroy_etal_2008; Utomo_etal_2017; Muraoka_etal_2019; Ellison_etal_2020c). The large ratios between $t_\mathrm{dep,\,mol}$ and all other characteristic timescales reaffirm the notion that star formation is inefficient: the implied star formation efficiency is $0.5{-}1\%$ per free-fall time or turbulence crossing time (cite: Evans_etal_2014; Lee_etal_2016; Vutisalchavakul_etal_2016; Utomo_etal_2018), ${\sim}1\%$ per cloud lifetime (cite: Kruijssen_etal_2019a; Chevance_etal_2020a; Chevance_etal_2021; KimJY_etal_2020), and ${\sim}10\%$ per orbital revolution or cloud–cloud collision (cite: Silk_1997; Kennicutt_1998a).

Beyond the typical values of the estimated timescales and their ratios, we also examine which timescales correlate the best with $t_\mathrm{dep,\,mol}$. Figure [8](#fig:scatter_timescales) shows that all the other timescales we considered show weak to no correlations with $t_\mathrm{dep,\,mol}$ (judging from the small correlation coefficients). The only statistically significant trends are with $t_\mathrm{shear}$ and $t_\mathrm{orb}$. They exhibit mild positive correlations with $t_\mathrm{dep,\,mol}$ with coefficients of $\rho=0.18$ and $0.14$, quantitatively consistent with the results in (cite: Wong_2009). Since these two timescales only differ by a factor of $\pi/(1-\beta)$, and the measured $1-\beta$ has a narrow dynamic range across our sample and a relatively large uncertainty, it is expected that $t_\mathrm{shear}$ and $t_\mathrm{orb}$ contain virtually the same amount of information and have similar predictive power for $t_\mathrm{dep,\,mol}$.

+---------------------------------------+--------------------------------------------------------------------+--------------------------------------------------------------------+
| Quantity                              | Weighted by number of apertures                                    | Weighted by molecular gas mass                                     |
+:======================================+:====================:+:====================:+:====================:+:====================:+:====================:+:====================:+
| 2-4 (lr)5-7                           | All                  | Disk                 | Center/bar           | All                  | Disk                 | Center/bar           |
+---------------------------------------+----------------------+----------------------+----------------------+----------------------+----------------------+----------------------+
|                                       |                      |                      |                      |                      |                      |                      |
+---------------------------------------+----------------------+----------------------+----------------------+----------------------+----------------------+----------------------+
|                                       |                      |                      |                      |                      |                      |                      |
+---------------------------------------+----------------------+----------------------+----------------------+----------------------+----------------------+----------------------+
| $\bar{t}_\mathrm{ff,\,obj}$ \[Myr\]   | $9.3^{+4.2}_{-3.4}$  | $9.2^{+4.5}_{-3.3}$  | $9.5^{+3.1}_{-3.9}$  | $6.6^{+3.9}_{-2.0}$  | $6.7^{+3.8}_{-1.9}$  | $6.5^{+3.9}_{-2.2}$  |
+---------------------------------------+----------------------+----------------------+----------------------+----------------------+----------------------+----------------------+
| $\bar{t}_\mathrm{ff,\,pix}$ \[Myr\]   | $10.5^{+4.7}_{-3.8}$ | $10.9^{+4.8}_{-3.9}$ | $9.9^{+4.0}_{-4.1}$  | $7.7^{+4.1}_{-2.5}$  | $8.0^{+4.2}_{-2.2}$  | $6.8^{+4.5}_{-2.5}$  |
+---------------------------------------+----------------------+----------------------+----------------------+----------------------+----------------------+----------------------+
| $\bar{t}_\mathrm{cr,\,obj}$ \[Myr\]   | $15.6^{+7.1}_{-4.2}$ | $16.1^{+7.0}_{-4.1}$ | $14.0^{+7.3}_{-4.1}$ | $13.1^{+6.6}_{-3.0}$ | $13.8^{+6.8}_{-2.9}$ | $11.5^{+5.4}_{-2.0}$ |
+---------------------------------------+----------------------+----------------------+----------------------+----------------------+----------------------+----------------------+
| $\bar{t}_\mathrm{cr,\,pix}$ \[Myr\]   | $15.3^{+6.1}_{-4.6}$ | $15.7^{+6.4}_{-4.1}$ | $13.1^{+4.8}_{-6.2}$ | $12.5^{+4.4}_{-4.1}$ | $13.3^{+4.3}_{-3.1}$ | $9.2^{+6.2}_{-3.6}$  |
+---------------------------------------+----------------------+----------------------+----------------------+----------------------+----------------------+----------------------+
| $t_\mathrm{shear}$ \[Myr\]            | $59^{+25}_{-19}$     | $62^{+23}_{-19}$     | $52^{+32}_{-23}$     | $54^{+24}_{-20}$     | $57^{+22}_{-16}$     | $44^{+29}_{-20}$     |
+---------------------------------------+----------------------+----------------------+----------------------+----------------------+----------------------+----------------------+
| $t_\mathrm{orb}$ \[Myr\]              | $160^{+70}_{-60}$    | $170^{+70}_{-50}$    | $120^{+70}_{-50}$    | $140^{+60}_{-60}$    | $160^{+60}_{-60}$    | $100^{+60}_{-30}$    |
+---------------------------------------+----------------------+----------------------+----------------------+----------------------+----------------------+----------------------+
| $\bar{t}_\mathrm{coll,\,obj}$ \[Myr\] | $74^{+101}_{-37}$    | $85^{+99}_{-45}$     | $57^{+64}_{-31}$     | $62^{+71}_{-32}$     | $73^{+74}_{-38}$     | $45^{+37}_{-24}$     |
+---------------------------------------+----------------------+----------------------+----------------------+----------------------+----------------------+----------------------+
| $\bar{t}_\mathrm{coll,\,pix}$ \[Myr\] | $90^{+61}_{-36}$     | $92^{+53}_{-35}$     | $77^{+84}_{-29}$     | $80^{+52}_{-31}$     | $84^{+47}_{-32}$     | $68^{+85}_{-27}$     |
+---------------------------------------+----------------------+----------------------+----------------------+----------------------+----------------------+----------------------+
| $t_\mathrm{dep,\,mol}$ \[Gyr\]        | $1.8^{+0.9}_{-0.6}$  | $1.7^{+0.8}_{-0.5}$  | $1.9^{+1.0}_{-1.0}$  | $1.9^{+0.9}_{-0.6}$  | $1.8^{+0.8}_{-0.6}$  | $2.0^{+1.0}_{-0.9}$  |
+---------------------------------------+----------------------+----------------------+----------------------+----------------------+----------------------+----------------------+

: Statistics of Characteristic Timescales

Table notes: The median value and 1$\sigma$ range (i.e., $16{-}84$ percentile range) of the characteristic timescales shown in Figure [7](#fig:timescales). Results in columns (2) to (4) are calculated by weighting each aperture equally, whereas those in columns (5) to (7) are calculated by weighting each aperture by the molecular gas mass it contains.

# Summary

This work examines the fundamental correlations between molecular clouds and their host galaxy environments in 80 nearby, massive, star-forming galaxies targeted by the PHANGS–ALMA survey. It directly addresses one of the core science questions that motivated the PHANGS–ALMA survey: *how do molecular cloud populations depend on local and global properties of the host galaxy?* Taking advantage of the large, representative galaxy sample and the homogeneous, high-quality data provided by PHANGS–ALMA, we provide a first systematic description of the environmental dependence of the cloud populations residing in typical star-forming environments across the local universe.

To achieve this overarching goal, we use PHANGS–ALMA $\mathrm{CO}\,(2\text{--}1)$ imaging data products (cite: Sun_etal_2018; Sun_etal_2020a; Leroy_etal_2021a; Leroy_etal_2021b) and CPROPS-based object catalogs (cite: Rosolowsky_etal_2021) to determine a rich set of molecular gas properties on $60{-}150$ pc scales. We further complement these molecular cloud scale measurements with multiwavelength observations covering UV, optical, IR, and radio bands (cite: Leroy_etal_2019; Querejeta_etal_2021), as well as high-level data products including rotation curves (cite: Lang_etal_2020) and morphological feature catalogs (cite: Querejeta_etal_2021). Together, these ancillary data present the kpc-scale gas and stellar mass distributions, star formation activities, kinematic properties, and morphological structures in the host galaxy (see Figure [1](#fig:schematic) for a schematic summary).

Following the cross-spatial-scale analysis framework developed by (cite: Sun_etal_2020b), we divide the sky footprint of each target galaxy into a series of hexagonal apertures, each 1.5 kpc in size (Figure [2](#fig:image)). We aggregate cloud-scale molecular gas measurements within each aperture, and then calculate the mass-weighted, population-averaged properties. We also compile measurements of host galaxy properties as area-weighted averages across the $\sim$kpc-scale apertures. Our analysis covers $46{,}628$ apertures in total, and $3{,}383$ apertures with *both* cloud population measurements *and* host galaxy measurements. We publish these rich multiwavelength measurements online in machine-readable formats (see Appendix [13](#apdx:mrt)).

Utilizing these databases, we construct basic statistical profiles for both the molecular cloud populations probed by the PHANGS–ALMA survey and the kpc-scale sub-galactic environments they inhabit. We quantify empirical correlations between cloud population properties and host galaxy environmental metrics. We further perform a data-driven variable selection technique and identify a small subset of environmental metrics as primary predictors of the cloud population statistics. Our main findings are as follows:

1.  The PHANGS–ALMA survey samples a wide range of host galaxy local properties. This is illustrated by the broad distributions of galactocentric radii, orbital kinematic properties, as well as kpc-scale gas, stellar, and star formation rate surface densities among all the kpc-scale averaging apertures (Figure [3](#fig:hist_env) and Table [1](#tab:stats_env)). Judged purely by aperture number counts, the most typical sub-galactic environment in our sample closely resembles the Solar Neighborhood. In comparison, most molecular gas mass is hosted in apertures with higher gas, stellar, and SFR surface densities, which are likely not matched by any kpc-scale region in the Milky Way.

2.  Molecular cloud populations vary substantially across kpc-scale regions. This is seen in population-averaged cloud properties such as mass, surface density, velocity dispersion, and turbulent pressure from aperture to aperture (Figure [4](#fig:hist_MC) and Table [2](#tab:stats_gmc)). These population-averaged measurements have been corrected for the effect of galaxy inclination and finite data sensitivity with novel methods. We conclude that variations of cloud properties within and among galaxies are not merely random scatter from cloud to cloud, but reflect systematic change across sub-galactic environments.

3.  Cloud population average properties appear significantly correlated with many local and global host galaxy properties (Figure [5](#fig:corr_all)). The sense of these correlations indicate that cloud populations with higher average mass, surface density, and turbulence strength prefer galactic environments at smaller galactocentric radii, higher gas, star, and SFR surface densities, shorter orbital period, and stronger shear. Similar trends are also present with global galaxy properties.

4.  Our BIC-based variable selection analysis yields a set of power-law predictive models that capture the most prominent trends for each cloud population-averaged property (Table [3](#tab:models)). The small number of independent variables appeared in these models suggests that most cloud–environment correlations can be reduced to the primary dependencies on a few local environmental metrics, especially on the kpc-scale molecular gas and SFR surface densities. The absence of global galaxy properties in these predictive models suggests that the correlations between molecular clouds and their local kpc-scale environment are more fundamental, and that galaxy-to-galaxy variations might arise merely as their consequences.

The rich multiwavelength measurements derived in this work have broad applications. We demonstrate one application scenario by deriving and comparing a set of characteristic timescales relevant to molecular cloud evolution and star formation (Figure [7](#fig:timescales) and Table [4](#tab:stats_timescales)). This further inquiry leads to the following findings:

5.  The molecular cloud population average free-fall time and turbulent crossing time are around $5{-}20~\mbox{$\rm Myr$}$, comparable to typical molecular cloud lifetimes estimated in a subset of our target galaxies (cite: Kruijssen_etal_2019a; Chevance_etal_2020a; Chevance_etal_2021; KimJY_etal_2020). These results support the notion that, when averaged across co-spatial populations, typical molecular clouds have virial parameters of order unity and only live for a few “internal” dynamical timescales.

6.  The characteristic timescales of galactic-scale dynamical processes (including orbital revolution, shearing, and cloud–cloud collision) are around $100~\mbox{$\rm Myr$}$, or about an order of magnitude longer than the cloud “internal” timescales or their estimated lifetimes. This contrast seems to suggest that galactic dynamical processes would have to be highly efficient to have a pronounced impact on molecular clouds throughout their short lifetime.

7.  The molecular gas depletion time ranges $1{-}3$ Gyr across our sample, implying star formation efficiencies of $0.5{-}1\%$ per cloud free-fall time or crossing time, ${\sim}1\%$ per cloud lifetime, and ${\sim}10\%$ per orbital time or cloud–cloud collision time.

8.  Among all molecular cloud internal timescales and galactic dynamical timescales we considered, only orbital time and shearing time show statistically significant (yet weak) correlations with the molecular gas depletion time (Figure [8](#fig:scatter_timescales)).

Our rich multiwavelength measurements have already supported multiple observational studies on PHANGS galaxies. These studies cover a broad range of topics, including the dynamical equilibrium of the ISM (cite: Sun_etal_2020b), pressures in H II  regions (cite: Barnes_etal_2021), morphological features in the stellar disks (cite: Querejeta_etal_2021), nuclear gas outflows (cite: Stuber_etal_2021), and the molecular gas–star formation cycle (cite: Pan_etal_2022). We also expect similar applications in future studies on PHANGS targets examining molecular cloud lifecycle (J. Kim et al. in preparation), molecular cloud star formation efficiency per free-fall time (J. Sun et al. in preparation), and galaxy disk global instabilities (T. Williams et al. in preparation).

Beyond the projects mentioned above, we expect these databases to be useful for many purposes, and we highlight as few of them here. (1) Our cloud population measurements can be directly compared to similar measurements in other types of galaxies, such as dwarf galaxies (cite: Mizuno_etal_2001a; Leroy_etal_2006; Schruba_etal_2017; Imara_Faesi_2019), starburst galaxies (cite: Ueda_etal_2012; Brunetti_etal_2021; Krieger_etal_2021), bulge-dominated early-type galaxies (cite: Utomo_etal_2015; Espada_etal_2019; LiuLJ_etal_2021), or even lensed, high-$z$ galaxies (cite: Dessauges-Zavadsky_etal_2019). Such comparisons could highlight commonalities and differences among star-forming environments across the universe. (2) Both our database and our power-law models can be used to predict molecular cloud properties in other samples of star-forming galaxies with only kpc-resolution data (cite: Bolatto_etal_2017; Sorai_etal_2019; LinLH_etal_2020). (3) Our databases provide a comprehensive set of initial conditions and outcome properties for benchmarking numerical simulations of the cold interstellar gas at high spatial resolution (cite: Benincasa_etal_2013; Kim_Ostriker_2017; Dobbs_etal_2019; Jeffreson_etal_2020; LiH_etal_2020; Tress_etal_2020b). (4) Our measurements allow for crucial tests of analytical star formation theories (cite: Krumholz_McKee_2005; Hennebelle_Chabrier_2011; Padoan_Nordlund_2011; Federrath_Klessen_2012; Krumholz_etal_2018; Burkhart_Mocz_2019; Orr_etal_2021a), as well as empirical calibrations of “sub-grid star formation recipes” in galaxy evolution models (cite: Olsen_etal_2017; Vallini_etal_2018; Popping_etal_2019a).

We plan to keep maintaining and improving the databases, thereby making them a long-term reference for the community. In particular, crucial next steps will come from incorporating measurements of ionised gas and stellar populations from the PHANGS–MUSE survey (cite: Emsellem_etal_2021), as well as star clusters from the PHANGS–HST survey (cite: Lee_etal_2021). Future versions of these databases will be released at the same location online as indicated in Appendix [13](#apdx:mrt).

This work was carried out as part of the PHANGS collaboration. The work of JS is partially supported by the Natural Sciences and Engineering Research Council of Canada (NSERC) through the Canadian Institute for Theoretical Astrophysics (CITA) National Fellowship. The work of JS, AKL, and DU is partially supported by the National Science Foundation (NSF) under Grants No. 1615105, 1615109, and 1653300. The work of JS and AKL is partially supported by the National Aeronautics and Space Administration (NASA) under ADAP grants NNX16AF48G and NNX17AF39G. EWR acknowledges the support of the NSERC, funding reference number RGPIN-2017-03987. EWK acknowledges support from the Smithsonian Institution as a Submillimeter Array Fellow. GAB gratefully acknowledges support by the ANID BASAL project FB210003. HAP acknowledges funding from the European Research Council (ERC) under the European Union’s Horizon 2020 research and innovation programme (grant agreement No. 694343) and the Ministry of Science and Technology of Taiwan under grant 110-2112-M-032-020-MY3. JP acknowledges support by the Programme National “Physique et Chimie du Milieu Interstellaire” (PCMI) of CNRS/INSU with INC/INP, co-funded by CEA and CNES. MQ acknowledges support from the Spanish grant PID2019-106027GA-C44, funded by MCIN/AEI/10.13039/501100011033. AS is supported by an NSF Astronomy and Astrophysics Postdoctoral Fellowship under award AST-1903834. TGW acknowledges funding from the ERC under the European Union’s Horizon 2020 research and innovation programme (grant agreement No. 694343). ATB and FB would like to acknowledge funding from the ERC under the European Union’s Horizon 2020 research and innovation programme (grant agreement No. 726384/Empire). MB gratefully acknowledges support by the ANID BASAL project FB210003. MC gratefully acknowledges funding from the Deutsche Forschungsgemeinschaft (DFG) in the form of an Emmy Noether Research Group (grant number CH2137/1-1). MC and JMDK gratefully acknowledge funding from the DFG in the form of an Emmy Noether Research Group (grant number KR4801/1-1) and the DFG Sachbeihilfe (grant number KR4801/2-1), and from the ERC under the European Union’s Horizon 2020 research and innovation programme via the ERC Starting Grant MUSTANG (grant agreement No. 714907). SCOG and RSK acknowledge financial support from the DFG via the collaborative research center (SFB 881, Project-ID 138713538) “The Milky Way System” (subprojects A1, B1, B2, and B8). They also acknowledge funding from the Heidelberg Cluster of Excellence “STRUCTURES” in the framework of Germany’s Excellence Strategy (grant EXC-2181/1, Project-ID 390900948) and from the European Research Council via the ERC Synergy Grant “ECOGAL” (grant 855130). KG is supported by the Australian Research Council through the Discovery Early Career Researcher Award (DECRA) Fellowship DE220100766 funded by the Australian Government. KK gratefully acknowledges funding from the DFG in the form of an Emmy Noether Research Group (grant number KR4598/2-1, PI Kreckel). The work of ECO is partially supported by NASA under ATP grant No. NNX17AG26G.

This paper makes use of the following ALMA data, which have been processed as part of the PHANGS–ALMA $\mathrm{CO}\,(2\text{--}1)$ survey:\
ADS/JAO.ALMA#2012.1.00650.S,\
ADS/JAO.ALMA#2013.1.00803.S,\
ADS/JAO.ALMA#2013.1.01161.S,\
ADS/JAO.ALMA#2015.1.00121.S,\
ADS/JAO.ALMA#2015.1.00782.S,\
ADS/JAO.ALMA#2015.1.00925.S,\
ADS/JAO.ALMA#2015.1.00956.S,\
ADS/JAO.ALMA#2016.1.00386.S,\
ADS/JAO.ALMA#2017.1.00392.S,\
ADS/JAO.ALMA#2017.1.00766.S,\
ADS/JAO.ALMA#2017.1.00886.L,\
ADS/JAO.ALMA#2018.1.01321.S,\
ADS/JAO.ALMA#2018.1.01651.S,\
ADS/JAO.ALMA#2018.A.00062.S.\
ALMA is a partnership of ESO (representing its member states), NSF (USA), and NINS (Japan), together with NRC (Canada), NSC and ASIAA (Taiwan), and KASI (Republic of Korea), in cooperation with the Republic of Chile. The Joint ALMA Observatory is operated by ESO, AUI/NRAO, and NAOJ. The National Radio Astronomy Observatory (NRAO) is a facility of NSF operated under cooperative agreement by Associated Universities, Inc (AUI).

This work is based in part on observations made with NSF’s Karl G. Jansky Very Large Array (VLA; project code: 14A-468, 14B-396, 16A-275, 17A-073, 18B-184). VLA is also operated by NRAO.

This work is based in part on observations made with the Australia Telescope Compact Array (ATCA). ATCA is part of the Australia Telescope National Facility, which is funded by the Australian Government for operation as a National Facility managed by CSIRO.

This work is based in part on observations made with the *Spitzer Space Telescope*, which is operated by the Jet Propulsion Laboratory, California Institute of Technology under a contract with NASA.

This work makes use of data products from the *Wide-field Infrared Survey Explorer (WISE)*, which is a joint project of the University of California, Los Angeles, and the Jet Propulsion Laboratory/California Institute of Technology, funded by NASA.

This work is based in part on observations made with the *Galaxy Evolution Explorer (GALEX)*. *GALEX* is a NASA Small Explorer, whose mission was developed in cooperation with the Centre National d’Etudes Spatiales (CNES) of France and the Korean Ministry of Science and Technology. *GALEX* is operated for NASA by the California Institute of Technology under NASA contract NAS5-98034.

This work is based in part on data gathered with the CIS 2.5m Irénée du Pont Telescope and the ESO/MPG 2.2m Telescope at Las Campanas Observatory, Chile.

This work has made use of the NASA/IPAC Infrared Science Archive (IRSA) and the NASA/IPAC Extragalactic Database (NED), which are funded by NASA and operated by the California Institute of Technology. Relevant datasets to this work include (cite: S4G_2010) and (cite: z0MGS_2019).

We acknowledge the usage of the HyperLeda database[^11] (cite: Makarov_etal_2014) and the SAO/NASA Astrophysics Data System[^12].

# Facilities

ALMA, VLA, ATCA, Spitzer, WISE, GALEX, Max Planck:2.2m, Du Pont, IRSA

# Software

`NumPy` (cite: NumPy_2020), `SciPy` (cite: SciPy_2020), `Astropy` (cite: Astropy_2013; Astropy_2018), `pandas` (cite: Pandas_1.3.4), `scikit-learn` (cite: Scikit-learn_2011), `Matplotlib` (cite: Matplotlib_2007), `APLpy` (cite: APLpy_2012), `MegaTable` (cite: MegaTable_3.0), `adstex` (<https://github.com/yymao/adstex>).

# Galaxy Sample

We list our galaxy sample in Table [\[tab:sample\]](#tab:sample).

lcccccccccc Galaxy & 2c$d$ & 2c$i$ & 2cP.A. & 2c$r_\mathrm{25}$ & 2c$r_\mathrm{disk}$ & 2c$M_\star$ & 2cSFR &

H I  Data & IR Data & UV Data\
& 2c\[$\mathrm{Mpc}$\] & 2c\[$\deg$\] & 2c\[$\deg$\] & 2c\[$\mathrm{kpc}$\] & 2c\[$\mathrm{kpc}$\] & 2c\[$10^{10}\mbox{$\rm M_\odot$}$\] & 2c\[$\mbox{$\rm M_\odot$}/\mathrm{yr}$\] & & &\
Circinus & 4.2 & 64.3 & 36.7 & 5.3 & 1.8 & 3.4 & 4.1 & ATCA:LVHIS & WISE & –\
IC 1954 & 12.8 & 57.1 & 63.4 & 5.6 & 1.5 & 0.47 & 0.36 & – & IRAC & WISE & FUV & NUV\
IC 5273 & 14.2 & 52.0 & 234.1 & 6.3 & 1.3 & 0.53 & 0.54 & – & IRAC & WISE & FUV & NUV\
IC 5332 & 9.0 & 26.9 & 74.4 & 8.0 & 2.8 & 0.47 & 0.41 & – & IRAC & WISE & FUV & NUV\
NGC 253 & 3.7 & 75.0 & 52.5 & 14.4 & 2.8 & 4.3 & 5.0 & ATCA:LVHIS & IRAC & WISE & FUV & NUV\
NGC 300 & 2.1 & 39.8 & 114.3 & 5.9 & 1.3 & 0.18 & 0.15 & ATCA:LVHIS & IRAC & WISE & FUV & NUV\
NGC 628 & 9.8 & 8.9 & 20.7 & 14.1 & 2.9 & 2.2 & 1.8 & VLA:THINGS & IRAC & WISE & FUV & NUV\
NGC 685 & 19.9 & 23.0 & 100.9 & 8.7 & 3.1 & 1.2 & 0.42 & – & IRAC & WISE & –\
NGC 1087 & 15.9 & 42.9 & 359.1 & 6.9 & 2.1 & 0.86 & 1.3 & VLA:PHANGS & IRAC & WISE & FUV & NUV\
NGC 1097 & 13.6 & 48.6 & 122.4 & 20.9 & 4.3 & 5.7 & 4.7 & VLA:AH539 & IRAC & WISE & FUV & NUV\
NGC 1300 & 19.0 & 31.8 & 278.0 & 16.4 & 3.7 & 4.1 & 1.2 & VLA:PHANGS & IRAC & WISE & FUV & NUV\
NGC 1317 & 19.1 & 23.2 & 221.5 & 8.5 & 2.4 & 4.2 & 0.48 & – & WISE & FUV & NUV\
NGC 1365 & 19.6 & 55.4 & 201.1 & 34.2 & 13.1 & 9.8 & 17 & – & IRAC & WISE & FUV & NUV\
NGC 1385 & 17.2 & 44.0 & 181.3 & 8.5 & 2.6 & 0.95 & 2.1 & VLA:PHANGS & IRAC & WISE & FUV & NUV\
NGC 1433 & 18.6 & 28.6 & 199.7 & 16.8 & 6.9 & 7.3 & 1.1 & – & IRAC & WISE & FUV & NUV\
NGC 1511 & 15.3 & 72.7 & 297.0 & 8.2 & 1.7 & 0.81 & 2.3 & – & IRAC & WISE & FUV & NUV\
NGC 1512 & 18.8 & 42.5 & 261.9 & 23.1 & 6.2 & 5.2 & 1.3 & VLA:AT285 & IRAC & WISE & FUV & NUV\
NGC 1546 & 17.7 & 70.3 & 147.8 & 9.5 & 2.1 & 2.2 & 0.83 & – & IRAC & WISE & FUV & NUV\
NGC 1559 & 19.4 & 65.4 & 244.5 & 11.8 & 2.4 & 2.3 & 3.8 & – & IRAC & WISE & NUV\
NGC 1566 & 17.7 & 29.5 & 214.7 & 18.6 & 3.9 & 6.1 & 4.5 & – & IRAC & WISE & FUV & NUV\
NGC 1637 & 11.7 & 31.1 & 20.6 & 5.4 & 1.8 & 0.88 & 0.64 & VLA:AR351 & IRAC & WISE & –\
NGC 1792 & 16.2 & 65.1 & 318.9 & 13.1 & 2.4 & 4.1 & 3.7 & ATCA:literature & IRAC & WISE & FUV & NUV\
NGC 1809 & 20.0 & 57.6 & 138.2 & 10.9 & 2.4 & 0.59 & 5.7 & – & IRAC & WISE & NUV\
NGC 2090 & 11.8 & 64.5 & 192.5 & 7.7 & 1.7 & 1.1 & 0.41 & – & WISE & FUV & NUV\
NGC 2283 & 13.7 & 43.7 & 355.9 & 5.5 & 1.9 & 0.78 & 0.52 & VLA:PHANGS & WISE & –\
NGC 2566 & 23.4 & 48.5 & 312.0 & 14.5 & 4.0 & 5.1 & 8.7 & VLA:PHANGS & WISE & –\
NGC 2775 & 23.1 & 41.2 & 156.5 & 14.3 & 4.1 & 12 & 0.87 & VLA:PHANGS & IRAC & WISE & FUV & NUV\
NGC 2835 & 12.2 & 41.3 & 1.0 & 11.4 & 2.2 & 1.0 & 1.2 & VLA:PHANGS & WISE & FUV & NUV\
NGC 2903 & 10.0 & 66.8 & 203.7 & 17.4 & 3.5 & 4.3 & 3.1 & VLA:THINGS & IRAC & WISE & FUV & NUV\
NGC 2997 & 14.1 & 33.0 & 108.1 & 21.0 & 4.0 & 5.4 & 4.4 & VLA:PHANGS & WISE & FUV & NUV\
NGC 3059 & 20.2 & 29.4 & 345.2 & 11.2 & 3.2 & 2.4 & 2.4 & – & WISE & –\
NGC 3137 & 16.4 & 70.3 & 359.7 & 13.2 & 3.0 & 0.77 & 0.49 & VLA:PHANGS & WISE & FUV & NUV\
NGC 3239 & 10.9 & 60.3 & 72.9 & 5.7 & 2.0 & 0.15 & 0.39 & VLA:PHANGS & WISE & FUV & NUV\
NGC 3351 & 10.0 & 45.1 & 193.2 & 10.5 & 2.1 & 2.3 & 1.3 & VLA:THINGS & IRAC & WISE & FUV & NUV\
NGC 3489 & 11.9 & 63.7 & 70.0 & 5.9 & 1.4 & 1.9 & 0.023 & – & IRAC & WISE & FUV & NUV\
NGC 3507 & 23.5 & 21.7 & 55.8 & 10.0 & 2.3 & 2.5 & 0.99 & VLA:PHANGS & IRAC & WISE & FUV & NUV\
NGC 3511 & 13.9 & 75.1 & 256.8 & 12.2 & 2.4 & 1.1 & 0.81 & VLA:PHANGS & IRAC & WISE & FUV & NUV\
NGC 3521 & 13.2 & 68.8 & 343.0 & 16.0 & 4.9 & 11 & 3.7 & VLA:THINGS & IRAC & WISE & FUV & NUV\
NGC 3596 & 11.3 & 25.1 & 78.4 & 6.0 & 2.0 & 0.45 & 0.30 & VLA:EveryTHINGS & IRAC & WISE & NUV\
NGC 3599 & 19.9 & 23.0 & 41.9 & 6.9 & 2.0 & 1.1 & 0.047 & – & IRAC & WISE & FUV & NUV\
NGC 3621 & 7.1 & 65.8 & 343.8 & 9.8 & 2.0 & 1.1 & 0.99 & VLA:THINGS & WISE & FUV & NUV\
NGC 3626 & 20.0 & 46.6 & 165.2 & 8.6 & 2.1 & 2.9 & 0.21 & VLA:AJ255 & IRAC & WISE & NUV\
NGC 3627 & 11.3 & 57.3 & 173.1 & 16.9 & 3.7 & 6.8 & 3.8 & VLA:THINGS & IRAC & WISE & FUV & NUV\
NGC 4254 & 13.1 & 34.4 & 68.1 & 9.6 & 1.8 & 2.7 & 3.1 & VLA:HERACLES & IRAC & WISE & FUV & NUV\
NGC 4293 & 15.8 & 65.0 & 48.3 & 14.3 & 2.8 & 3.2 & 0.51 & VLA:VIVA & IRAC & WISE & FUV & NUV\
NGC 4298 & 14.9 & 59.2 & 313.9 & 5.5 & 1.6 & 1.0 & 0.46 & VLA:VIVA & IRAC & WISE & FUV & NUV\
NGC 4303 & 17.0 & 23.5 & 312.4 & 17.0 & 3.1 & 3.3 & 5.3 & VLA:AW536 & IRAC & WISE & FUV & NUV\
NGC 4321 & 15.2 & 38.5 & 156.2 & 13.5 & 3.6 & 5.6 & 3.6 & VLA:HERACLES & IRAC & WISE & FUV & NUV\
NGC 4457 & 15.1 & 17.4 & 78.7 & 6.1 & 2.2 & 2.6 & 0.31 & VLA:VIVA & IRAC & WISE & FUV & NUV\
NGC 4459 & 15.9 & 47.0 & 108.8 & 9.6 & 3.3 & 4.8 & 0.22 & – & WISE & FUV & NUV\
NGC 4476 & 17.5 & 60.1 & 27.4 & 4.3 & 1.2 & 0.65 & 0.040 & – & WISE & FUV & NUV\
NGC 4477 & 15.8 & 33.5 & 25.7 & 8.5 & 2.1 & 3.9 & 0.079 & – & WISE & FUV & NUV\
NGC 4496A & 14.9 & 53.8 & 51.1 & 7.3 & 1.9 & 0.34 & 0.61 & VLA:EveryTHINGS & IRAC & WISE & FUV & NUV\
NGC 4535 & 15.8 & 44.7 & 179.7 & 18.7 & 3.8 & 3.4 & 2.2 & VLA:VIVA & IRAC & WISE & FUV & NUV\
NGC 4536 & 16.2 & 66.0 & 305.6 & 16.7 & 2.7 & 2.5 & 3.4 & VLA:HERACLES & IRAC & WISE & FUV & NUV\
NGC 4540 & 15.8 & 28.7 & 12.8 & 5.0 & 1.4 & 0.61 & 0.17 & VLA:PHANGS & IRAC & WISE & FUV & NUV\
NGC 4548 & 16.2 & 38.3 & 138.0 & 13.1 & 3.0 & 4.9 & 0.52 & VLA:VIVA & IRAC & WISE & FUV & NUV\
NGC 4569 & 15.8 & 70.0 & 18.0 & 20.9 & 4.3 & 6.4 & 1.3 & VLA:HERACLES & IRAC & WISE & FUV & NUV\
NGC 4571 & 14.9 & 32.7 & 217.5 & 7.7 & 2.0 & 1.2 & 0.29 & VLA:PHANGS & IRAC & WISE & FUV & NUV\
NGC 4596 & 15.8 & 36.6 & 120.0 & 9.0 & 3.8 & 3.9 & 0.11 & – & IRAC & WISE & FUV & NUV\
NGC 4689 & 15.0 & 38.7 & 164.1 & 8.3 & 3.0 & 1.6 & 0.40 & VLA:VIVA & IRAC & WISE & –\
NGC 4731 & 13.3 & 64.0 & 255.4 & 12.2 & 3.0 & 0.30 & 0.60 & VLA:PHANGS & IRAC & WISE & FUV & NUV\
NGC 4781 & 11.3 & 59.0 & 290.0 & 6.1 & 1.1 & 0.44 & 0.48 & VLA:PHANGS & IRAC & WISE & FUV & NUV\
NGC 4826 & 4.4 & 59.1 & 293.6 & 6.7 & 1.1 & 1.7 & 0.20 & VLA:THINGS & IRAC & WISE & FUV & NUV\
NGC 4941 & 15.0 & 53.4 & 202.2 & 7.3 & 2.2 & 1.5 & 0.44 & VLA:AM384 & IRAC & WISE & FUV & NUV\
NGC 4951 & 15.0 & 70.2 & 91.2 & 6.9 & 1.9 & 0.62 & 0.35 & VLA:PHANGS & IRAC & WISE & FUV & NUV\
NGC 5042 & 16.8 & 49.4 & 190.6 & 10.2 & 2.4 & 0.80 & 0.60 & VLA:PHANGS & IRAC & WISE & FUV & NUV\
NGC 5068 & 5.2 & 35.7 & 342.4 & 5.7 & 1.3 & 0.25 & 0.28 & VLA:PHANGS & IRAC & WISE & FUV & NUV\
NGC 5128 & 3.7 & 45.3 & 32.2 & 13.7 & 4.1 & 9.4 & 1.2 & – & WISE & FUV & NUV\
NGC 5134 & 19.9 & 22.7 & 311.6 & 7.9 & 2.1 & 2.6 & 0.45 & VLA:PHANGS & IRAC & WISE & FUV & NUV\
NGC 5236 & 4.9 & 24.0 & 225.0 & 9.7 & 2.4 & 3.4 & 4.2 & VLA:THINGS & IRAC & WISE & FUV & NUV\
NGC 5248 & 14.9 & 47.4 & 109.2 & 8.8 & 2.0 & 2.5 & 2.3 & VLA:AS787 & IRAC & WISE & FUV & NUV\
NGC 5530 & 12.3 & 61.9 & 305.4 & 8.6 & 1.7 & 1.2 & 0.33 & – & WISE & –\
NGC 5643 & 12.7 & 29.9 & 318.7 & 9.7 & 1.6 & 2.2 & 2.6 & – & WISE & –\
NGC 6300 & 11.6 & 49.6 & 105.4 & 9.0 & 2.1 & 2.9 & 1.9 & ATCA:literature & WISE & –\
NGC 6744 & 9.4 & 52.7 & 14.0 & 21.4 & 4.8 & 5.3 & 2.4 & – & WISE & FUV & NUV\
NGC 7456 & 15.7 & 67.3 & 16.0 & 9.4 & 2.9 & 0.44 & 0.37 & – & IRAC & WISE & FUV & NUV\
NGC 7496 & 18.7 & 35.9 & 193.7 & 9.1 & 1.5 & 0.99 & 2.3 & – & IRAC & WISE & FUV & NUV\
NGC 7743 & 20.3 & 37.1 & 86.2 & 7.7 & 1.9 & 2.3 & 0.21 & – & IRAC & WISE & FUV & NUV\
NGC 7793 & 3.6 & 50.0 & 290.0 & 5.5 & 1.1 & 0.23 & 0.27 & VLA:THINGS & IRAC & WISE & FUV & NUV

Table notes: (2) distance (cite: Anand_etal_2020); (3) inclination angle (cite: Lang_etal_2020); (4) position angle (cite: Lang_etal_2020); (5) isophotal radius at 25 mag/arcsec$^2$ in $B$ band (LEDA); (6) stellar disk scale length (cite: Leroy_etal_2021a); (7) global stellar mass (cite: Leroy_etal_2021a); (9) H I  data source (VLA:PHANGS – A. Sardone et al., in preparation; VLA:EveryTHINGS – I. Chiang et al., in preparation; VLA:THINGS – (cite: Walter_etal_2008); VLA:HERACLES – (cite: Leroy_etal_2009); VLA:VIVA – (cite: Chung_etal_2009); ATCA:LVHIS – (cite: Koribalski_etal_2018); ATCA:literature – (cite: Murugeshan_etal_2019)); (10) IR data source (*Spitzer* IRAC – S$^4$G, (cite: Sheth_etal_2010),

*WISE* – $z0$MGS, (cite: Leroy_etal_2019)); (11) UV data source (*GALEX* FUV and NUV – $z0$MGS, (cite: Leroy_etal_2019)).

# Prescriptions for the Metallicity and the CO-to-H$_2$ Conversion Factor

In this work, we adopt empirical relation-based prescriptions to infer a local gas-phase metallicity (Section [3.3](#sec:analysis:env)) and its associated CO-to-$\mathrm{H}_2$ conversion factor (Sections [2.1.1](#sec:data:CO:obj) to [2.1.2](#sec:data:CO:pix)) in each kpc-sized aperture. Here we detail these prescriptions and the rationale behind them.

## Metallicity

To account for possible variations of CO-to-$\mathrm{H}_2$ conversion factor across our galaxy sample, a key first step is to get homogeneous and reliable metallicity estimates. Although extensive compilations of (global and resolved) metallicity measurements for nearby galaxies exist in the literature (cite: Pilyugin_etal_2014; DeVis_etal_2019), we do not yet have a uniform sample of resolved metallicity measurements with the same calibration scheme for all PHANGS–ALMA targets. In this work, we instead rely on two well-calibrated scaling relations to capture the general trends of metallicity variation across our sample.

We assume a global galaxy mass–metallicity relation (cite: Sanchez_etal_2019) and a fixed radial metallicity gradient within each galaxy (cite: Sanchez_etal_2014), such that $$\begin{align}
\log_{10}\!Z'(r_\mathrm{e}) &= 0.04 + 0.01\,\left(\log_{10}\!\frac{M_\star}{M_\odot} - 11.5\right)\, \exp\left(-\log_{10}\!\frac{M_\star}{M_\odot} + 11.5\right)\,, \label{eq:MZR}\\
\log_{10}\!Z'(r_\mathrm{gal}) &= \log_{10}\!Z'(r_\mathrm{e}) - 0.1\frac{r_\mathrm{gal}}{r_\mathrm{e}}~. \label{eq:Z_grad}
\end{align}$$ Here $Z'(r_\mathrm{e})$ is the local gas-phase abundance at $r_\mathrm{gal}=r_\mathrm{e}$ normalized by the solar value \[$12+\log\mathrm{(O/H)}=8.69$\], $Z'(r_\mathrm{gal})$ is the normalized abundance at arbitrary $r_\mathrm{gal}$, and $M_\star$ is the galaxy global stellar mass derived by assuming a Chabrier IMF (cite: Chabrier_2003). Note that these scaling relations are appropriate for abundance measurements adopting the O3N2 calibration in (cite: Pettini_Pagel_2004).

While Equations [\[eq:MZR\]](#eq:MZR) and [\[eq:Z_grad\]](#eq:Z_grad) are identical to the formulae used in (cite: Sun_etal_2020b), we make two methodological improvements when applying them in this work. First, we elevate the $M_\star$ values in Table [\[tab:sample\]](#tab:sample) by 0.1 dex before inserting them into Equation [\[eq:MZR\]](#eq:MZR). According to (cite: Sanchez_etal_2019), this 0.1 dex offset can largely correct for systematic effects due to (a) differences between Salpeter and Chabrier IMFs, and (b) the finite aperture size of their IFU data (see their Appendix A and Figure A1). Second, we estimate $r_\mathrm{e}$ by multiplying the stellar disk scale length, $r_\mathrm{disk}$, by a factor of $1.68$. This step mirrors the procedure for deriving $r_\mathrm{e}$ in (cite: Sanchez_etal_2019). Overall, these two methodological changes improve the self-consistency of our metallicity prescription.

As a sanity check, we compare our predictions to the observed two-dimensional metallicity distributions in 18 galaxies in the PHANGS–MUSE survey (cite: Williams_etal_2021a). Modulo the uncertain translation between different metallicity calibration schemes (cite: Pettini_Pagel_2004; Pilyugin_Grebel_2016), the predictions and the actual measurements show similar median values (within 0.05 dex) across this subsample, although the dynamic range of our predictions appears narrower than the observed range (0.12 dex versus 0.21 dex).

## CO-to-H~2~ Conversion Factor

The CO-to-$\mathrm{H}_2$ conversion factor, $\alpha_\mathrm{CO}$, is expected to depend strongly on metallicity (cite: Wilson_1995; Arimoto_etal_1996; Israel_1997; Wolfire_etal_2010; Glover_MacLow_2011; Feldmann_etal_2012; Narayanan_etal_2012; Schruba_etal_2012; Amorin_etal_2016; Accurso_etal_2017; Gong_etal_2020). Within a star-forming galaxy, $\alpha_\mathrm{CO}$ can vary by more than a factor of 2 (cite: Leroy_etal_2011; Blanc_etal_2013; Sandstrom_etal_2013), with part of it attributable to metallicity variations (at least in the low temperature “outer disk” regime). These considerations motivate us to use a metallicity-dependent $\alpha_\mathrm{CO}$ prescription as a fiducial choice in this work. Nevertheless, we also consider a few other prescriptions and provide these alternative estimates in the published datasets.

Our fiducial estimate follows the same metallicity-dependent prescription as described in (cite: Sun_etal_2020b): $$\begin{equation}
\frac{\alpha_\mathrm{CO(1\text{--}0)}}{\mbox{$\rm M_\odot~pc^{-2}\ (K~km~s^{-1})^{-1}$}} = 4.35\;Z^\mathrm{\prime-1.6}~,
\label{eq:alphaCO_S20}
\end{equation}$$ where $Z'$ is the predicted local metallicity from Equations [\[eq:MZR\]](#eq:MZR) and [\[eq:Z_grad\]](#eq:Z_grad). The adopted power-law slope in Equation [\[eq:alphaCO_S20\]](#eq:alphaCO_S20) is motivated primarily by the metallicity-dependent part of the xCOLD GASS calibration (cite: Accurso_etal_2017), whereas the normalization is anchored to the Galactic value at solar metallicity (cite: Bolatto_etal_2013). This prescription gives similar predictions to many other prescriptions in the literature (cite: Genzel_etal_2012; Schruba_etal_2012; Amorin_etal_2016) within the metallicity range probed in this work (cite: Accurso_etal_2017).

Beyond this fiducial $\alpha_\mathrm{CO}$ prescription, we calculate four alternative prescriptions, following and expanding on (cite: Sun_etal_2020b). The first is simply a constant value matching the Galactic average: $$\begin{equation}
\frac{\alpha_\mathrm{CO(1\text{--}0)}}{\mbox{$\rm M_\odot~pc^{-2}\ (K~km~s^{-1})^{-1}$}} = 4.35~.
\label{eq:alphaCO_MW}
\end{equation}$$

The second prescription follows (cite: Narayanan_etal_2012) and infers $\alpha_\mathrm{CO}$ from both metallicity ($Z'$) and the flux-weighted $\mathrm{CO}\,(2\text{--}1)$ line intensity ($\left<I_\mathrm{CO(2{-}1)}\right>$): $$\begin{equation}
\frac{\alpha_\mathrm{CO(1\text{--}0)}}{\mbox{$\rm M_\odot~pc^{-2}\ (K~km~s^{-1})^{-1}$}} 
= 8.5\;Z^{\prime-0.65}\;\min\!\!\left[1,\;1.5\times\left(\frac{\left<\I_\mathrm{CO(2{-}1)}\right>}{\mbox{$\rm K~km~s^{-1}$}}\right)^{-0.32}\right]~.
\label{eq:alphaCO_N12}
\end{equation}$$ The above formula is adapted from equation (11) in (cite: Narayanan_etal_2012) with two notable distinctions. First, the original formula depends on $\left<I_\mathrm{CO(1{-}0)}\right>$, whereas our formula converts that dependence to $\left<I_\mathrm{CO(2{-}1)}\right>$ assuming a line ratio of $R_\mathrm{21}=0.65$ (cite: denBrok_etal_2021; Leroy_etal_2021c). Second, we increase the normalization by a factor of 1.36 to correct for helium contribution.

The third prescription follows (cite: Bolatto_etal_2013) and infers $\alpha_\mathrm{CO}$ from metallicity ($Z'$), molecular cloud surface density (proxied by $\left<\Sigma_\mathrm{mol,\,pix}\right>$), and kpc-scale total surface density including both gas and stellar mass ($\Sigma_\mathrm{total}$): $$\begin{align}
\frac{\alpha_\mathrm{CO(1\text{--}0)}}{\mbox{$\rm M_\odot~pc^{-2}\ (K~km~s^{-1})^{-1}$}} 
&= 2.9\;\exp\!\left(\frac{40\;\mbox{$\rm M_\odot~pc^{-2}$}}{Z'\left<\Sigma_\mathrm{mol,\,pix}\right>}\right)\;\left(\frac{\Sigma_\mathrm{total}}{100\;\mbox{$\rm M_\odot~pc^{-2}$}}\right)^{-\gamma}~,\nonumber\\
&\text{with } \gamma=
\begin{cases}
0.5, &\text{if } \Sigma_\mathrm{total}>100\;\mbox{$\rm M_\odot~pc^{-2}$}\\
0. &\text{otherwise}
\end{cases}
\label{eq:alphaCO_B13}
\end{align}$$ Since calculating $\left<\Sigma_\mathrm{mol,\,pix}\right>$ and $\Sigma_\mathrm{total}$ relies on knowing $\alpha_\mathrm{CO}$ in the first place, we solve for $\alpha_\mathrm{CO}$ iteratively until the output of Equation [\[eq:alphaCO_B13\]](#eq:alphaCO_B13) converges to the assumed value for calculating $\left<\Sigma_\mathrm{mol,\,pix}\right>$ and $\Sigma_\mathrm{total}$ (cite: Sun_etal_2020b).

We combine the above prescriptions for $\alpha_\mathrm{CO(1\text{--}0)}$ with the adopted $\mathrm{CO}\,(2\text{--}1)$-to-$\mathrm{CO}\,(1\text{--}0)$ line ratio $R_\mathrm{21}=0.65$ (cite: denBrok_etal_2021; Leroy_etal_2021c) to get the appropriate conversion factor for the $\mathrm{CO}\,(2\text{--}1)$ line, $\alpha_\mathrm{CO(2\text{--}1)}$. We then apply these $\alpha_\mathrm{CO(2\text{--}1)}$ values on a per aperture basis — that is, we assume a constant conversion factor within the $\sim$kpc scale extent of each averaging aperture. These treatments largely follow (cite: Sun_etal_2020b).

As another improvement over (cite: Sun_etal_2020b), here we add a fourth alternative prescription following (cite: Gong_etal_2020). This simulation-motivated prescription considers the dependence on metallicity ($Z'$), CO line integrated intensity ($I_\mathrm{CO}$), and the physical beam size ($D_\mathrm{beam}$). It directly predicts the conversion factor for the $\mathrm{CO}\,(2\text{--}1)$ line without relying on a separately assumed $R_\mathrm{21}$ value. The original formula is expressed in number column density convention (cite: Gong_etal_2020): $$\begin{equation}
\frac{X_\mathrm{CO(2\text{--}1)}}{10^{20}\;\mathrm{cm}^{-2}\,(\mbox{$\rm K~km~s^{-1}$})^{-1}}
= 21.1\,Z^\mathrm{\prime-0.50}\,\left(\frac{I_\mathrm{CO(2\text{--}1)}}{\mbox{$\rm K~km~s^{-1}$}}\right)^{-0.97+0.34\log_{10}\left(\frac{D_\mathrm{beam}}{\mathrm{pc}}\right)}\,\left(\frac{D_\mathrm{beam}}{\mathrm{pc}}\right)^{-0.41}~.
\label{eq:alphaCO_G20}
\end{equation}$$ We convert it into mass surface density units via $$\begin{equation}
\frac{\alpha_\mathrm{CO(2\text{--}1)}}{\mbox{$\rm M_\odot~pc^{-2}\ (K~km~s^{-1})^{-1}$}}
= 2.18\,\left(\frac{X_\mathrm{CO(2\text{--}1)}}{10^{20}\;\mathrm{cm}^{-2}\,(\mbox{$\rm K~km~s^{-1}$})^{-1}}\right)~.
\end{equation}$$ Since this prescription is calibrated at $\lesssim100$ pc scales, we derive the $\alpha_\mathrm{CO(2\text{--}1)}$ values pixel-by-pixel at 60–150 pc scales and then calculate CO line intensity weighted mean values within the $\sim$kpc-scale averaging apertures. This is done for all four resolution levels considered in this work (60, 90, 120, and 150 pc).

We include our estimated $\alpha_\mathrm{CO(2\text{--}1)}$ values from all aforementioned prescriptions in the published databases. This allows for easy conversions if the reader wish to adopt an alternative prescription instead of our fiducial choice. Concretely, our molecular cloud measurements scale with the adopted conversion factor as $\left<M\right>\propto\left<\Sigma\right>\propto\left<P_\mathrm{turb}\right>\propto\alpha_\mathrm{CO(2\text{--}1)}$ and $\left<\alpha_\mathrm{vir}\right>\propto\alpha_\mathrm{CO(2\text{--}1)}^{-1}$; the kpc-scale molecular gas surface density scales as $\Sigma_\mathrm{mol}\propto\alpha_\mathrm{CO(2\text{--}1)}$; the timescale measurements scale as $\bar{t}_\mathrm{ff}\propto\alpha_\mathrm{CO(2\text{--}1)}^{-0.5}$ and $t_\mathrm{dep,\,mol}\propto\alpha_\mathrm{CO(2\text{--}1)}$. The impact of different prescriptions on some of the molecular gas measurements is examined in detailed by (cite: Sun_etal_2020b).

We expect future works to improve the handling of the CO-to-H$_2$ conversion factor even further. Particularly, combining a varying $R_\mathrm{21}$ (cite: Leroy_etal_2021c) with an $R_\mathrm{21}$-dependent $\alpha_\mathrm{CO}$ prescription (cite: Gong_etal_2020) would allow us to better capture the gas excitation temperature variations, especially in galaxy centers where this effect becomes very pronounced. We also defer a more thorough comparisons between the different $\alpha_\mathrm{CO}$ prescriptions to a subsequent paper.

# Inclination Corrections

In Section [2.1.1](#sec:data:CO:obj) and [2.1.2](#sec:data:CO:pix), we introduce inclination corrections on several molecular cloud properties measured at 60–150 pc scales. These corrections represent an important methodological change, as many previous works (cite: Sun_etal_2018; Sun_etal_2020a; Rosolowsky_etal_2021) have assumed spherical geometry for observations on these spatial scales and, consequently, have not applied such corrections. This spherical approximation assumes that at the resolution scale, the structure of the molecular ISM is isotropic. While this assumption is common throughout the literature, it is not well tested. Furthermore, the 60–150 pc resolutions are also comparable to the thickness of the molecular gas disk, which implies anisotropy. In this appendix, we show that there is an inclination dependence in our measurements and motivate specific functional forms for empirical corrections.

The primary motivation for introducing these corrections is that the observed molecular gas properties (such as surface density and velocity dispersion) at $\sim\,$100 pc scales show apparent correlations with the host galaxy inclination angle. For example, A. Hughes et al. (in preparation) found such trends in the measured properties of CPROPS-identified objects among the PHANGS-ALMA galaxy sample. A parallel examination of the pixel-by-pixel measurements derived from the same dataset (cite: Sun_etal_2020a) also reveals a similar trend (see Figure [9](#fig:incl) left panel). Since inclination angle is not an intrinsic property of galaxies, the presence of these inclination-related trends signifies systematic biases in the molecular gas measurements derived with both CPROPS-based and pixel-by-pixel approaches.

To quantify these biases, we carry out a modified version of the variable selection analysis in Section [5.2](#sec:corr:model). We suppress the inclination corrections for all molecular cloud properties (i.e., the $\cos{i}$ terms in Equations [\[eq:M_obj\]](#eq:M_obj)–[\[eq:alphavir_pix\]](#eq:alphavir_pix)) while keeping $\cos{i}$ in the list of feature variables. This re-analysis yields a new set of power-law predictive models similar to those in Table [3](#tab:models), but many of these models now carry an extra $(\cos{i})^\beta$ term. Specifically, in the predictive models for $\Sigma_\mathrm{obj}$ and $\Sigma_\mathrm{pix}$, the power of the $\cos{i}$ terms are close to $\beta=-1.0$; while in the models for $\sigma_\mathrm{obj}$ and $\sigma_\mathrm{pix}$ they are close to $\beta=-0.5$. In other words, to eliminate the apparent $\cos{i}$ dependence in these models (which should not be present were these models reflecting purely physical trends), one would have to multiply $\cos{i}$ to the measured surface densities and $(\cos{i})^{0.5}$ to the velocity dispersions. This motivates the correction terms in Equations [\[eq:Sigma_obj\]](#eq:Sigma_obj), [\[eq:vdisp_obj\]](#eq:vdisp_obj), [\[eq:Sigma_pix\]](#eq:Sigma_pix), and [\[eq:vdisp_pix\]](#eq:vdisp_pix).

We also inspect the effects of these inclination corrections on the original pixel-by-pixel measurements in (cite: Sun_etal_2020a) without doing any cloud population averaging. Figure [9](#fig:incl) compares the surface density–velocity dispersion relation before and after applying the inclination corrections. Without these corrections, the median velocity dispersion at given surface densities appears tends to be higher in galaxies with high inclination angles (smaller $\cos{i}$). This trend largely disappears when we apply the inclination corrections to both axes. This result suggests that, despite being motivated by the observed cloud–environment correlations, our adopted inclination corrections can also remove the unphysical inclination dependence in the relationships among molecular cloud internal properties.

Our adopted inclination corrections are empirical and data-driven, but their functional forms have physical implications. For the surface densities, a multiplicative term of $\cos{i}$ is the exact correction one would use for disk-like structures with their orientations aligned with the whole galaxy disk. Our proposed interpretation is that the interstellar gas forms filamentary networks, which preferentially align with the large-scale galaxy disk even at $\sim\,$100 pc scales (cite: Zucker_etal_2018). This preference in orientation should eventually disappear at smaller scales, but evidently, the PHANGS-ALMA observations do not yet reach the transitional spatial scale.

For the velocity dispersions, there are at least two effects that can produce some inclination dependence: (1) contributions from ordered, in-plane motions of the gas (e.g., beam smearing), and (2) anisotropy of the gas velocity dispersion (usually with the in-plane components larger than the vertical component; see e.g., Jeffreson et al. submitted). Both effects would predict higher velocity dispersions at higher inclination angles, which is consistent with the direction of the adopted correction factor, but neither would call for a specific functional form of $(\cos{i})^{0.5}$ for this correction. Alternatively, if one assumes that the velocity structure of the turbulent gas can be described by a line width–size relation of $\sigma_\mathrm{mol}(l) \propto l^{0.5}$ (cite: Solomon_etal_1987), and that this relationship still holds at 60–150 pc scales, then the varying line-of-sight depth with inclination (i.e., $l \propto 1/\cos{i}$) could imply $\sigma_\mathrm{mol}\propto (\cos{i})^{-0.5}$, which matches our empirical result.

We stress that all the inclination-dependent trends we identify above are real measurements that only emerge in statistical analysis of many galaxies at similarly high resolution. They imply that the molecular gas structures are clearly anisotropic at 60–150 pc scales. Existing and future surveys at even higher resolution (e.g., in very nearby galaxies or in CO-bright sub-regions of PHANGS galaxies) can help us extend this analysis to smaller spatial scales, where the transition from anisotropic to isotropic structures presumably occurs. This transitional spatial scale can be further compared with estimates of the gas disk scale height from independent methods (cite: Koch_etal_2020).

# Completeness Corrections

In Section [3.2.2](#sec:analysis:cloud:completeness), we identify a systematic bias affecting the population-averaged molecular cloud properties. This systematic bias originates from the incomplete CO flux recovery in the PHANGS–ALMA “strict” moment maps and the associated CPROPS catalogs. We introduce a completeness correction to account for this bias, making use of the measured CO flux completeness, $f_\mathrm{flux}$, and area coverage fraction, $f_\mathrm{area}$, in each averaging aperture. In this appendix, we present the mathematical derivation of this completeness correction method.

We assume that the intrinsic CO intensity probability distribution function (PDF) within each averaging aperture follows a lognormal distribution: $$\begin{equation}
    P(I_\mathrm{CO})
    = \frac{1}{\sqrt{2\pi}\,\sigma_\mathrm{int}\,I_\mathrm{CO}}\,\exp\left[-\frac{(\ln I_\mathrm{CO}-\ln\bar{I}_\mathrm{CO,\,int})^2}{2\sigma_\mathrm{int}^2}\right]~.
    \label{eq:lognormal}
\end{equation}$$ This assumption is motivated by observational constraints on the CO intensity distribution in nearby galaxies (cite: Hughes_etal_2013b; Leroy_etal_2016; Egusa_etal_2018; Sun_etal_2018; Sun_etal_2020a). We further assume that the CO emission included in the “strict” moment maps constitutes everything above a threshold intensity $I_\mathrm{CO,\,th}$ (i.e., the maps have a sharp, well-defined sensitivity limit), and that the “strict” maps capture all emission along the sightlines with CO detections. Under these assumptions, we can express $f_\mathrm{flux}$ and $f_\mathrm{area}$ in terms of $\sigma_\mathrm{int}$, $\bar{I}_\mathrm{CO,\,int}$, and $I_\mathrm{CO,\,th}$: $$\begin{align}
    f_\mathrm{area}
    &= \int^{+\infty}_{I_\mathrm{CO,\,th}} P(I_\mathrm{CO})\,\mathrm{d}I_\mathrm{CO}
    = \frac{1}{2}\left[1 - \mathrm{erf}\left(\frac{\ln(I_\mathrm{CO,\,th}/\bar{I}_\mathrm{CO,\,int})}{\sqrt{2}\sigma_\mathrm{int}}\right) \right]~, \\
    f_\mathrm{flux}
    &= \frac{\int^{+\infty}_{I_\mathrm{CO,\,th}} I_\mathrm{CO}\,P(I_\mathrm{CO})\,\mathrm{d}I_\mathrm{CO}}{\int^{+\infty}_{0} I_\mathrm{CO}\,P(I_\mathrm{CO})\,\mathrm{d}I_\mathrm{CO}}
    = \frac{1}{2}\left[1 - \mathrm{erf}\left(\frac{\ln(I_\mathrm{CO,\,th}/\bar{I}_\mathrm{CO,\,int}) - \sigma_\mathrm{int}^2}{\sqrt{2}\sigma_\mathrm{int}}\right) \right]~.
\end{align}$$ Notice that these two relations allow us to inversely solve for $\sigma_\mathrm{int}$ and $\ln(I_\mathrm{CO,\,th}/\bar{I}_\mathrm{CO,\,int})$ and express their combinations in terms of the measurable quantities $f_\mathrm{area}$ and $f_\mathrm{flux}$: $$\begin{align}
    \frac{\ln(I_\mathrm{CO,\,th}/\bar{I}_\mathrm{CO,\,int})}{\sigma_\mathrm{int}}
    &= \sqrt{2}\;\mathrm{erf^{-1}}(1-2f_\mathrm{area})~, \\
    \sigma_\mathrm{int}
    &= \sqrt{2}\left[\mathrm{erf^{-1}}(1-2f_\mathrm{area}) - \mathrm{erf^{-1}}(1-2f_\mathrm{flux})\right]~.
\end{align}$$ Here “$\mathrm{erf^{-1}}$” stands for the inverse error function.

We then calculate the appropriate correction factors for the population-averaged molecular cloud properties and express them in terms of $f_\mathrm{area}$ and $f_\mathrm{flux}$. The three population-averaged properties we consider here are the the flux-weighted average cloud surface density, $\left<\Sigma\right>$ (Section [2.1.1](#sec:data:CO:obj)–[2.1.2](#sec:data:CO:pix)), the molecular gas clumping factor, $c_\mathrm{pix}$ (Section [3.2.1](#sec:analysis:cloud:clumping)), and the flux-weighted average of the reciprocal of free-fall time, $\left<t_\mathrm{ff}^{-1}\right>$ (Section [6.1](#sec:timescales:method)). $$\begin{align}
    F_\mathrm{correct,\,\Sigma}
    \equiv \frac{\left<\Sigma\right>_\mathrm{true}}{\left<\Sigma\right>_\mathrm{obs}}
    &\propto \frac{\int^{+\infty}_{0} I_\mathrm{CO}^2\,P(I_\mathrm{CO})\,\mathrm{d}I_\mathrm{CO}}{\int^{+\infty}_{0} I_\mathrm{CO}\,P(I_\mathrm{CO})\,\mathrm{d}I_\mathrm{CO}}
    \left[\frac{\int^{+\infty}_{I_\mathrm{CO,\,th}} I_\mathrm{CO}^2\,P(I_\mathrm{CO})\,\mathrm{d}I_\mathrm{CO}}{\int^{+\infty}_{I_\mathrm{CO,\,th}} I_\mathrm{CO}\,P(I_\mathrm{CO})\,\mathrm{d}I_\mathrm{CO}}\right]^{-1}
    = \frac{f_\mathrm{flux}}{f_\mathrm{compl}(2)}~, \label{eq:correction_Sigma}\\
    F_\mathrm{correct,\,c}
    \equiv \frac{c_\mathrm{pix,\,true}}{c_\mathrm{pix,\,obs}}
    &\propto \frac{\int^{+\infty}_{0}I_\mathrm{CO}^2\,P(I_\mathrm{CO})\,\mathrm{d}I_\mathrm{CO}}{\left(\int^{+\infty}_{0}I_\mathrm{CO}\,P(I_\mathrm{CO})\,\mathrm{d}I_\mathrm{CO}\right)^2}
    \left[\frac{\left(\int^{+\infty}_{I_\mathrm{CO,\,th}}I_\mathrm{CO}^2\,P(I_\mathrm{CO})\,\mathrm{d}I_\mathrm{CO}\right)\left(\int^{+\infty}_{I_\mathrm{CO,\,th}}P(I_\mathrm{CO})\,\mathrm{d}I_\mathrm{CO}\right)}{\left(\int^{+\infty}_{I_\mathrm{CO,\,th}} I_\mathrm{CO}\,P(I_\mathrm{CO})\,\mathrm{d}I_\mathrm{CO}\right)^2}\right]^{-1} \nonumber\\
    &= \frac{f_\mathrm{flux}^2}{f_\mathrm{area}\,f_\mathrm{compl}(2)}~, \label{eq:correction_clumping}\\
    F_\mathrm{correct,\,t}
    \equiv \frac{\left<t_\mathrm{ff}^{-1}\right>_\mathrm{true}}{\left<t_\mathrm{ff}^{-1}\right>_\mathrm{obs}}
    &\propto \frac{\int^{+\infty}_{0} I_\mathrm{CO}^{3/2}\,P(I_\mathrm{CO})\,\mathrm{d}I_\mathrm{CO}}{\int^{+\infty}_{0} I_\mathrm{CO}\,P(I_\mathrm{CO})\,\mathrm{d}I_\mathrm{CO}}
    \left[\frac{\int^{+\infty}_{I_\mathrm{CO,\,th}} I_\mathrm{CO}^{3/2}\,P(I_\mathrm{CO})\,\mathrm{d}I_\mathrm{CO}}{\int^{+\infty}_{I_\mathrm{CO,\,th}} I_\mathrm{CO}\,P(I_\mathrm{CO})\,\mathrm{d}I_\mathrm{CO}}\right]^{-1}
    = \frac{f_\mathrm{flux}}{f_\mathrm{compl}(3/2)}~, \label{eq:correction_tff}\\
    \mathrm{where} \quad f_\mathrm{compl}(\beta)
    &= \frac{\int^{+\infty}_{I_\mathrm{CO,\,th}} I_\mathrm{CO}^\beta\,P(I_\mathrm{CO})\,\mathrm{d}I_\mathrm{CO}}{\int^{+\infty}_{0} I_\mathrm{CO}^\beta\,P(I_\mathrm{CO})\,\mathrm{d}I_\mathrm{CO}}
    = \frac{1}{2}\left[1 - \mathrm{erf}\left(\frac{\ln(I_\mathrm{CO,\,th}/\bar{I}_\mathrm{CO,\,int}) - \beta\sigma_\mathrm{int}^2}{\sqrt{2}\sigma_\mathrm{int}}\right) \right] \nonumber\\
    &= \frac{1}{2}\left[1 - \mathrm{erf}\Big(\beta\,\mathrm{erf^{-1}}(1-2f_\mathrm{flux}) - (\beta-1)\,\mathrm{erf^{-1}}(1-2f_\mathrm{area}) \Big) \right]~. \nonumber
\end{align}$$ Note that the second steps in Equations [\[eq:correction_Sigma\]](#eq:correction_Sigma)–[\[eq:correction_tff\]](#eq:correction_tff) is valid because we adopt a constant $\alpha_\mathrm{CO}$ within each aperture.

Figure [10](#fig:completeness) shows the joint distribution of $f_\mathrm{area}$ and $f_\mathrm{flux}$ for all $3{,}383$ hexagonal apertures, with color-codes reflecting the amplitude of the derived correction factors $F_\mathrm{correct,\,\Sigma}$ and $F_\mathrm{correct,\,c}$. The $f_\mathrm{area}$ and $f_\mathrm{flux}$ values for $\sim$68% of apertures are consistent with intrinsic lognormal $I_\mathrm{CO}$-PDFs with $\sigma_\mathrm{int}$ ranging from 0 to 1.0 dex. This broadly matches the observed $I_\mathrm{CO}$-PDF widths of 0.2 to 0.6 dex in sub-regions of nearby galaxies (cite: Hughes_etal_2013b; Sun_etal_2018; Sun_etal_2020a) The implied $I_\mathrm{CO}$ PDF widths for another $\sim$12% of apertures exceed 1.0 dex, which seem too high to be physical. These apertures tend to have low $f_\mathrm{area}$, possibly suggesting that these apertures include true “empty” areas devoid of CO emission, in which case the lognormal PDF assumption is no longer appropriate. Finally, the remaining $\sim$20% of apertures have $f_\mathrm{flux}< f_\mathrm{area}$. Given the high $f_\mathrm{area}$ in most of these regions, it is likely that there is missing CO flux along sight lines with CO detections. We calculate the completeness correction for these apertures by assuming an ad-hoc $f_\mathrm{flux}$ value equal to $f_\mathrm{area}$.

The color trends in Figure [10](#fig:completeness) indicate that apertures with low $f_\mathrm{flux}$ or $f_\mathrm{area}$ would require very significant completeness corrections, which means that the CO detections in these apertures are too “unrepresentative” of the underlying cloud population for us to extract reliable statistics. This motivates us to select a subsample of apertures with high $f_\mathrm{flux}$ *and* high $f_\mathrm{area}$ for the more careful correlation analyses in Section [5](#sec:corr). The selection criteria, $f_\mathrm{flux}> 50\%$ and $f_\mathrm{area}> 20\%$, are also illustrated in Figure [10](#fig:completeness). Among all apertures that meet these criteria, the correction factors on $\left<\Sigma\right>$ have a median value of 0.03 dex and a maximum of 0.2 dex, which means that the uncorrected $\left<\Sigma\right>$ values are already close to the inferred true population average. For the same set of apertures, the correction factors on $c_\mathrm{pix}$ have a smaller median of 0.01 dex but a much larger maximum of 0.6 dex. The few apertures with very large correction factors are those with high $f_\mathrm{flux}$ but low $f_\mathrm{area}$, where a simple lognormal PDF is likely not a good description of the underlying CO intensity distribution.

# Resolution Dependence

In this work, we derive molecular cloud measurements from the PHANGS–ALMA CO data at four common resolution levels: 60, 90, 120, and 150 pc. The main text focuses on results derived at 150 pc scale so as to cover the full sample of apertures while keeping the presentation succinct. In this appendix, we draw comparisons across all four spatial scales to illustrate the scale-dependence of the measured molecular cloud properties.

The molecular cloud measurements are available for fewer and fewer apertures/galaxies as the resolution goes from 150 pc to 60 pc (cite: Leroy_etal_2021a). To control for changes in the aperture/galaxy sample and any associated selection effects, here we focus on a subset of 328 apertures in 15 galaxies with data at all four spatial scales. Besides, the data sensitivity also drops as the beam size decreases, which could also leads to systematic biases in our molecular cloud population statistics. We address this issue by applying completeness corrections to all population-averaged measurements according to the flux completeness and area coverage fraction of the CO moment maps at each resolution (see Section [3.2.2](#sec:analysis:cloud:completeness)).

Figure [11](#fig:resolution) illustrates that most molecular cloud properties presented in Figure [4](#fig:hist_MC) show some level of resolution dependence. In detail, the average molecular cloud mass and radius both increase strongly as the data resolution gets coarser (the former is most likely driven by the latter). This reinforces the conclusion that the sizes of the CPROPS-identified objects are primarily set by data resolution rather than physical properties of the gas distribution (see Section [5.2](#sec:corr:model)). The slope of the $\left<R_\mathrm{ojb}\right>$ trend appears sub-linear ($\left<R_\mathrm{obj}\right> \propto D_\mathrm{beam}^{0.6}$), which seems to suggest that the molecular gas structure is not completely scale-free between 60–150 pc. The average cloud surface density mildly decreases with beam size, as expected from more beam dilution. The average cloud velocity dispersion increases with beam size, but with a power-law slope of $\sim$0.20–0.23, shallower than the line width–size relation for molecular clouds in the Milky Way disk (cite: Solomon_etal_1987). The average cloud turbulent pressure mildly declines toward coarser resolution, whereas the average virial parameter largely remains roughly constant. Both trends are predictable from their functional relations with cloud mass, size, and velocity dispersion. Finally, as the molecular gas surface density distribution becomes more homogeneous at coarser resolutions, the estimated clumping factor diminishes accordingly.

# Machine-readable Tables

We publish our high-level measurements in the form of machine-readable data tables via the PHANGS CANFAR storage[^13]. A permanent copy of the version used in this article will also be available via the CANFAR Data Publication Service[^14]. This version includes two types of tables. The first records the hexagonal aperture measurements, and the second presents the radial bin measurements (see Section [3.1](#sec:analysis:aperture)). Here we provide column-by-column descriptions of the hexagonal aperture tables in Table [5](#tab:database). For clarity, we also add links to the relevant sections and equations for each derived quantity. We do not separately provide column-by-column descriptions for the radial bin tables, but simply note that the set of columns therein are almost identical, except that the radial bin tables lack the , , and columns.

We plan to keep improving these data tables and release subsequent versions via the same CANFAR storage^[13](#canfar)^. Future versions will cover a larger sample of galaxies and include more measurements derived from other data sets, such as H II  regions and stellar populations from the PHANGS–MUSE survey (cite: Emsellem_etal_2021) and star clusters from the PHANGS–HST survey (cite: Lee_etal_2021).

|  |  |  |
|:---|:---|:---|
| Column name | Unit | Description |
|  |  |  |
|  | $\mathrm{}$ | Aperture ID |
|  | $\mathrm{{}^{\circ}}$ | Right Ascension of the aperture center (§[3.3](#sec:analysis:env)) |
|  | $\mathrm{{}^{\circ}}$ | Declination of the aperture center (§[3.3](#sec:analysis:env)) |
|  | $\mathrm{kpc}$ | Deprojected galactocentric radius (§[3.3](#sec:analysis:env)) |
|  | $\mathrm{{}^{\circ}}$ | Deprojected azimuthal angle (0 = receding major axis; §[3.3](#sec:analysis:env)) |
|  | $\mathrm{}$ | Fraction of $\mathrm{CO}\,(2\text{--}1)$ flux in the central region (§[2.6](#sec:data:environ), §[3.3](#sec:analysis:env)) |
|  | $\mathrm{}$ | Fraction of $\mathrm{CO}\,(2\text{--}1)$ flux in the bar region (§[2.6](#sec:data:environ), §[3.3](#sec:analysis:env)) |
|  | $\mathrm{km\,s^{-1}}$ | CO-derived circular velocity (Persic+96 model; §[2.5](#sec:data:rotcurve), §[3.3](#sec:analysis:env)) |
|  | $\mathrm{km\,s^{-1}}$ | Statistical error on CO-derived circular velocity |
|  | $\mathrm{}$ | Logarithmic derivative of CO rotation curve (Persic+96 model; §[2.5](#sec:data:rotcurve), §[3.3](#sec:analysis:env)) |
|  | $\mathrm{}$ | Statistical error on logarithmic derivative of CO rotation curve |
|  | $\mathrm{}$ | Gas-phase metallicity relative to solar (Eq. [\[eq:MZR\]](#eq:MZR)–[\[eq:Z_grad\]](#eq:Z_grad)) |
|  | $\mathrm{s\,M_{\odot}\,K^{-1}\,km^{-1}\,pc^{-2}}$ | $\mathrm{CO}\,(2\text{--}1)$-to-H$_2$ conversion factor (fiducial; Sun+20; Eq. [\[eq:alphaCO_S20\]](#eq:alphaCO_S20)) |
|  | $\mathrm{s\,M_{\odot}\,K^{-1}\,km^{-1}\,pc^{-2}}$ | $\mathrm{CO}\,(2\text{--}1)$-to-H$_2$ conversion factor (Narayanan+12; Eq. [\[eq:alphaCO_N12\]](#eq:alphaCO_N12)) |
|  | $\mathrm{s\,M_{\odot}\,K^{-1}\,km^{-1}\,pc^{-2}}$ | $\mathrm{CO}\,(2\text{--}1)$-to-H$_2$ conversion factor (Bolatto+13; Eq. [\[eq:alphaCO_B13\]](#eq:alphaCO_B13)) |
|  | $\mathrm{s\,M_{\odot}\,K^{-1}\,km^{-1}\,pc^{-2}}$ | Flux-weighted mean $\mathrm{CO}\,(2\text{--}1)$-to-H$_2$ conversion factor (Gong+20 $I_\mathrm{CO}$-based @ $X$$^{*}$ pc; Eq. [\[eq:alphaCO_G20\]](#eq:alphaCO_G20)) |
|  | $\mathrm{M_{\odot}\,pc^{-2}}$ | Region-average molecular gas surface density (PHANGS-ALMA; §[3.3](#sec:analysis:env)) |
|  | $\mathrm{M_{\odot}\,pc^{-2}}$ | Statistical error on region-average molecular gas surface density |
|  | $\mathrm{M_{\odot}\,pc^{-2}}$ | Region-average atomic gas surface density (PHANGS-HI; Eq. [\[eq:SigHI\]](#eq:SigHI), §[3.3](#sec:analysis:env)) |
|  | $\mathrm{M_{\odot}\,pc^{-2}}$ | Statistical error on region-average atomic gas surface density |
|  | $\mathrm{M_{\odot}\,L_{\odot}^{-1}}$ | Stellar mass-to-light ratio at 3.4 $\mu$m (Leroy+21; §[2.3](#sec:data:NIR)) |
|  | $\mathrm{M_{\odot}\,pc^{-2}}$ | Region-average stellar mass surface density (fiducial; §[2.3](#sec:data:NIR), §[3.3](#sec:analysis:env)) |
|  | $\mathrm{M_{\odot}\,pc^{-2}}$ | Statistical error on region-average stellar mass surface density (fiducial) |
|  | $\mathrm{M_{\odot}\,pc^{-2}}$ | Region-average stellar mass surface density (3.6 $\mu$m + varying M/L; Eq. [\[eq:Sigstar_3p6um\]](#eq:Sigstar_3p6um), §[3.3](#sec:analysis:env)) |
|  | $\mathrm{M_{\odot}\,pc^{-2}}$ | Statistical error on region-average stellar mass surface density (3.6 $\mu$m + varying M/L) |
|  | $\mathrm{M_{\odot}\,pc^{-2}}$ | Region-average stellar mass surface density (3.4 $\mu$m + varying M/L; Eq. [\[eq:Sigstar_3p4um\]](#eq:Sigstar_3p4um), §[3.3](#sec:analysis:env)) |
|  | $\mathrm{M_{\odot}\,pc^{-2}}$ | Statistical error on region-average stellar mass surface density (3.4 $\mu$m + varying M/L) |
|  | $\mathrm{M_{\odot}\,yr^{-1}\,kpc^{-2}}$ | Region-average SFR surface density (fiducial; §[2.4](#sec:data:z0MGS), §[3.3](#sec:analysis:env)) |
|  | $\mathrm{M_{\odot}\,yr^{-1}\,kpc^{-2}}$ | Statistical error on region-average SFR surface density (fiducial) |
|  | $\mathrm{M_{\odot}\,yr^{-1}\,kpc^{-2}}$ | Region-average SFR surface density (GALEX FUV + WISE4; Eq. [\[eq:SigSFR_FUVW4\]](#eq:SigSFR_FUVW4), §[3.3](#sec:analysis:env)) |
|  | $\mathrm{M_{\odot}\,yr^{-1}\,kpc^{-2}}$ | Statistical error on region-average SFR surface density (GALEX FUV + WISE4) |
|  | $\mathrm{M_{\odot}\,yr^{-1}\,kpc^{-2}}$ | Region-average SFR surface density (GALEX NUV + WISE4; Eq. [\[eq:SigSFR_NUVW4\]](#eq:SigSFR_NUVW4), §[3.3](#sec:analysis:env)) |
|  | $\mathrm{M_{\odot}\,yr^{-1}\,kpc^{-2}}$ | Statistical error on region-average SFR surface density (GALEX NUV + WISE4) |
|  | $\mathrm{M_{\odot}\,yr^{-1}\,kpc^{-2}}$ | Region-average SFR surface density (WISE4 only; Eq. [\[eq:SigSFR_W4ONLY\]](#eq:SigSFR_W4ONLY), §[3.3](#sec:analysis:env)) |
|  | $\mathrm{M_{\odot}\,yr^{-1}\,kpc^{-2}}$ | Statistical error on region-average SFR surface density (WISE4 only) |
|  | $\mathrm{M_{\odot}\,yr^{-1}\,kpc^{-2}}$ | Region-average SFR surface density (H$\alpha$ + WISE4; Eq. [\[eq:SigSFR_HaW4\]](#eq:SigSFR_HaW4), §[3.3](#sec:analysis:env)) |
|  | $\mathrm{M_{\odot}\,yr^{-1}\,kpc^{-2}}$ | Statistical error on region-average SFR surface density (H$\alpha$ + WISE4) |
|  | $\mathrm{}$ | Area filling fraction of $\mathrm{CO}\,(2\text{--}1)$ detection @ $X$$^{*}$ pc (§[3.2.2](#sec:analysis:cloud:completeness)) |
|  | $\mathrm{}$ | Flux completeness of $\mathrm{CO}\,(2\text{--}1)$ detection @ $X$$^{*}$ pc (§[3.2.2](#sec:analysis:cloud:completeness)) |
|  | $\mathrm{}$ | Completeness correction on flux-weighted mean cloud surface density @ $X$$^{*}$ pc (Eq. [\[eq:correction_Sigma\]](#eq:correction_Sigma)) |
|  | $\mathrm{}$ | Completeness correction on $\mathrm{CO}\,(2\text{--}1)$ clumping factor @ $X$$^{*}$ pc (Eq. [\[eq:correction_clumping\]](#eq:correction_clumping)) |
|  | $\mathrm{}$ | Completeness correction on flux-weighted mean reciprocal of free-fall time @ $X$$^{*}$ pc (Eq. [\[eq:correction_tff\]](#eq:correction_tff)) |
|  | $\mathrm{}$ | Clumping factor of $\mathrm{CO}\,(2\text{--}1)$ emission @ $X$$^{*}$ pc (Eq. [\[eq:clumping\]](#eq:clumping)) |
|  | $\mathrm{}$ | Statistical error on clumping factor of $\mathrm{CO}\,(2\text{--}1)$ emission @ $X$$^{*}$ pc |
|  | $\mathrm{M_{\odot}\,pc^{-2}}$ | Flux-weighted mean molecular gas surface density @ $X$$^{*}$ pc (Eq. [\[eq:Sigma_pix\]](#eq:Sigma_pix), §[3.2](#sec:analysis:cloud)) |
|  | $\mathrm{M_{\odot}\,pc^{-2}}$ | Statistical error on flux-weighted mean molecular gas surface density @ $X$$^{*}$ pc |
|  | $\mathrm{km\,s^{-1}}$ | Flux-weighted mean molecular gas velocity dispersion @ $X$$^{*}$ pc (Eq. [\[eq:vdisp_pix\]](#eq:vdisp_pix), §[3.2](#sec:analysis:cloud)) |
|  | $\mathrm{km\,s^{-1}}$ | Statistical error on flux-weighted mean molecular gas velocity dispersion @ $X$$^{*}$ pc |
|  | $\mathrm{K\,cm^{-3}}$ | Flux-weighted mean molecular gas turbulent pressure @ $X$$^{*}$ pc (Eq. [\[eq:Pturb_pix\]](#eq:Pturb_pix), §[3.2](#sec:analysis:cloud)) |
|  | $\mathrm{K\,cm^{-3}}$ | Statistical error on flux-weighted mean molecular gas turbulent pressure @ $X$$^{*}$ pc |
|  | $\mathrm{}$ | Flux-weighted mean virial parameter @ $X$$^{*}$ pc (Eq. [\[eq:alphavir_pix\]](#eq:alphavir_pix), §[3.2](#sec:analysis:cloud)) |
|  | $\mathrm{}$ | Statistical error on flux-weighted mean virial parameter @ $X$$^{*}$ pc |
|  | $\mathrm{Myr^{-1}}$ | Flux-weighted mean reciprocal of crossing time @ $X$$^{*}$ pc (Eq. [\[eq:t_cr\]](#eq:t_cr), §[3.2](#sec:analysis:cloud)) |
|  | $\mathrm{Myr^{-1}}$ | Statistical error on flux-weighted mean reciprocal of crossing time @ $X$$^{*}$ pc |
|  | $\mathrm{Myr^{-1}}$ | Flux-weighted mean reciprocal of free-fall time @ $X$$^{*}$ pc (Eq. [\[eq:t_ff\]](#eq:t_ff), §[3.2](#sec:analysis:cloud)) |
|  | $\mathrm{Myr^{-1}}$ | Statistical error on flux-weighted mean reciprocal of free-fall time @ $X$$^{*}$ pc |
|  | $\mathrm{}$ | Number of CPROPS objects in each aperture @ $X$$^{*}$ pc |
|  | $\mathrm{}$ | Flux completeness of CPROPS objects @ $X$$^{*}$ pc (§[3.2.2](#sec:analysis:cloud:completeness)) |
|  | $\mathrm{M_{\odot}}$ | Flux-weighted mean object molecular gas mass @ $X$$^{*}$ pc (Eq. [\[eq:M_obj\]](#eq:M_obj), §[3.2](#sec:analysis:cloud)) |
|  | $\mathrm{M_{\odot}}$ | Statistical error on flux-weighted mean object molecular gas mass @ $X$$^{*}$ pc |
|  | $\mathrm{M_{\odot}\,pc^{-2}}$ | Flux-weighted mean object molecular gas surface density @ $X$$^{*}$ pc (Eq. [\[eq:Sigma_obj\]](#eq:Sigma_obj), §[3.2](#sec:analysis:cloud)) |
|  | $\mathrm{M_{\odot}\,pc^{-2}}$ | Statistical error on flux-weighted mean object molecular gas surface density @ $X$$^{*}$ pc |
|  | $\mathrm{km\,s^{-1}}$ | Flux-weighted mean object velocity dispersion @ $X$$^{*}$ pc (Eq. [\[eq:vdisp_obj\]](#eq:vdisp_obj), §[3.2](#sec:analysis:cloud)) |
|  | $\mathrm{km\,s^{-1}}$ | Statistical error on flux-weighted mean object velocity dispersion @ $X$$^{*}$ pc |
|  | $\mathrm{pc}$ | Flux-weighted mean object 3d radius @ $X$$^{*}$ pc (Eq. [\[eq:R_obj\]](#eq:R_obj), §[3.2](#sec:analysis:cloud)) |
|  | $\mathrm{pc}$ | Statistical error on flux-weighted mean object 3d radius @ $X$$^{*}$ pc |
|  | $\mathrm{K\,cm^{-3}}$ | Flux-weighted mean object molecular gas turbulent pressure @ $X$$^{*}$ pc (Eq. [\[eq:Pturb_obj\]](#eq:Pturb_obj), §[3.2](#sec:analysis:cloud)) |
|  | $\mathrm{K\,cm^{-3}}$ | Statistical error on flux-weighted mean object molecular gas turbulent pressure @ $X$$^{*}$ pc |
|  | $\mathrm{}$ | Flux-weighted mean object virial parameter @ $X$$^{*}$ pc (Eq. [\[eq:alphavir_obj\]](#eq:alphavir_obj), §[3.2](#sec:analysis:cloud)) |
|  | $\mathrm{}$ | Statistical error on flux-weighted mean object virial parameter @ $X$$^{*}$ pc |
|  | $\mathrm{Myr^{-1}}$ | Flux-weighted mean reciprocal of object crossing time @ $X$$^{*}$ pc (Eq. [\[eq:t_cr\]](#eq:t_cr), §[3.2](#sec:analysis:cloud)) |
|  | $\mathrm{Myr^{-1}}$ | Statistical error on flux-weighted mean reciprocal of object crossing time @ $X$$^{*}$ pc |
|  | $\mathrm{Myr^{-1}}$ | Flux-weighted mean reciprocal of object free-fall time @ $X$$^{*}$ pc (Eq. [\[eq:t_ff\]](#eq:t_ff), §[3.2](#sec:analysis:cloud)) |
|  | $\mathrm{Myr^{-1}}$ | Statistical error on flux-weighted mean reciprocal of object free-fall time @ $X$$^{*}$ pc |

: Column-by-column Descriptions of the Published Machine-readable Tables

Table notes: $^{*}$ $X$ = 60, 90, 120, and 150.

natexlab

(ref: Accurso_etal_2017) Accurso, G., Saintonge, A., Catinella, B., et al. 2017, MNRAS, 470, 4750

(ref: Amorin_etal_2016) Amorı́n, R., Muñoz-Tuñón, C., Aguerri, J. A. L., & Planesas, P. 2016, A&A, 588, A23

(ref: Anand_etal_2020) Anand, G. S., Lee, J. C., Van Dyk, S. D., et al. 2021, MNRAS, 501, 3621

(ref: Aniano_etal_2011) Aniano, G., Draine, B. T., Gordon, K. D., & Sandstrom, K. 2011, PASP, 123, 1218

(ref: Arimoto_etal_1996) Arimoto, N., Sofue, Y., & Tsujimoto, T. 1996, PASJ, 48, 275

(ref: Astropy_2013) Astropy Collaboration, Robitaille, T. P., Tollerud, E. J., et al. 2013, A&A, 558, A33

(ref: Astropy_2018) Astropy Collaboration, Price-Whelan, A. M., Sipőcz, B. M., et al. 2018, AJ, 156, 123

(ref: Bacchini_etal_2019a) Bacchini, C., Fraternali, F., Iorio, G., & Pezzulli, G. 2019, A&A, 622, A64

(ref: Ballesteros-Paredes_2006) Ballesteros-Paredes, J. 2006, MNRAS, 372, 443

(ref: Ballesteros-Paredes_etal_2011a) Ballesteros-Paredes, J., Hartmann, L. W., Vázquez-Semadeni, E., Heitsch, F., & Zamora-Avilés, M. A. 2011, MNRAS, 411, 65

(ref: Ballesteros-Paredes_etal_2020) Ballesteros-Paredes, J., André, P., Hennebelle, P., et al. 2020, Space Sci. Rev., 216, 76

(ref: Barnes_etal_2021) Barnes, A. T., Glover, S. C. O., Kreckel, K., et al. 2021, MNRAS, arXiv:2110.05492

(ref: Benincasa_etal_2013) Benincasa, S. M., Tasker, E. J., Pudritz, R. E., & Wadsley, J. 2013, ApJ, 776, 23

(ref: Benincasa_etal_2020a) Benincasa, S. M., Loebman, S. R., Wetzel, A., et al. 2020, MNRAS, 497, 3993

(ref: Bigiel_etal_2008) Bigiel, F., Leroy, A., Walter, F., et al. 2008, AJ, 136, 2846

(ref: Blanc_etal_2013) Blanc, G. A., Schruba, A., Evans, Neal J., I., et al. 2013, ApJ, 764, 117

(ref: Blitz_Shu_1980) Blitz, L., & Shu, F. H. 1980, ApJ, 238, 148

(ref: Bolatto_etal_2008) Bolatto, A. D., Leroy, A. K., Rosolowsky, E., Walter, F., & Blitz, L. 2008, ApJ, 686, 948

(ref: Bolatto_etal_2013) Bolatto, A. D., Wolfire, M., & Leroy, A. K. 2013, ARA&A, 51, 207

(ref: Bolatto_etal_2017) Bolatto, A. D., Wong, T., Utomo, D., et al. 2017, ApJ, 846, 159

(ref: Boquien_etal_2016) Boquien, M., Kennicutt, R., Calzetti, D., et al. 2016, A&A, 591, A6

(ref: Bovy_2017a) Bovy, J. 2017a, MNRAS, 468, L63

(ref: Bovy_2017b) —. 2017b, MNRAS, 470, 1360

(ref: Brunetti_etal_2021) Brunetti, N., Wilson, C. D., Sliwa, K., et al. 2021, MNRAS, 500, 4730

(ref: Burkhart_Mocz_2019) Burkhart, B., & Mocz, P. 2019, ApJ, 879, 129

(ref: Calzetti_etal_2007) Calzetti, D., Kennicutt, R. C., Engelbracht, C. W., et al. 2007, ApJ, 666, 870

(ref: Camacho_etal_2016) Camacho, V., Vázquez-Semadeni, E., Ballesteros-Paredes, J., et al. 2016, ApJ, 833, 113

(ref: Chabrier_2003) Chabrier, G. 2003, PASP, 115, 763

(ref: Chevance_etal_2020a) Chevance, M., Kruijssen, J. M. D., Hygate, A. P. S., et al. 2020a, MNRAS, 493, 2872

(ref: Chevance_etal_2020b) Chevance, M., Kruijssen, J. M. D., Vazquez-Semadeni, E., et al. 2020b, Space Sci. Rev., 216, 50

(ref: Chevance_etal_2021) Chevance, M., Kruijssen, J. M. D., Krumholz, M. R., et al. 2021, MNRAS, arXiv:2010.13788

(ref: Chung_etal_2009) Chung, A., van Gorkom, J. H., Kenney, J. D. P., Crowl, H., & Vollmer, B. 2009, AJ, 138, 1741

(ref: Colombo_etal_2014a) Colombo, D., Hughes, A., Schinnerer, E., et al. 2014, ApJ, 784, 3

(ref: Colombo_etal_2019) Colombo, D., Rosolowsky, E., Duarte-Cabral, A., et al. 2019, MNRAS, 483, 4291

(ref: Davis_etal_2022) Davis, T. A., Gensior, J., Bureau, M., et al. 2022, arXiv e-prints, arXiv:2203.01358

(ref: DeVis_etal_2019) De Vis, P., Jones, A., Viaene, S., et al. 2019, A&A, 623, A5

(ref: denBrok_etal_2021) den Brok, J. S., Chatzigiannakis, D., Bigiel, F., et al. 2021, MNRAS, 504, 3221

(ref: Dessauges-Zavadsky_etal_2019) Dessauges-Zavadsky, M., Richard, J., Combes, F., et al. 2019, Nature Astronomy, 3, 1115

(ref: Dobbs_etal_2015) Dobbs, C. L., Pringle, J. E., & Duarte-Cabral, A. 2015, MNRAS, 446, 3608

(ref: Dobbs_etal_2019) Dobbs, C. L., Rosolowsky, E., Pettitt, A. R., et al. 2019, MNRAS, 485, 4997

(ref: Dobbs_etal_2014) Dobbs, C. L., Krumholz, M. R., Ballesteros-Paredes, J., et al. 2014, in Protostars and Planets VI, ed. H. Beuther, R. S. Klessen, C. P. Dullemond, & T. Henning, 3

(ref: DonovanMeyer_etal_2013) Donovan Meyer, J., Koda, J., Momose, R., et al. 2013, ApJ, 772, 107

(ref: Egusa_etal_2018) Egusa, F., Hirota, A., Baba, J., & Muraoka, K. 2018, ApJ, 854, 90

(ref: Ellison_etal_2020c) Ellison, S. L., Lin, L., Thorp, M. D., et al. 2021, MNRAS, 501, 4777

(ref: Elmegreen_2000) Elmegreen, B. G. 2000, ApJ, 530, 277

(ref: Emsellem_etal_2021) Emsellem, E., Schinnerer, E., Santoro, F., et al. 2021, A&A submitted. <https://arxiv.org/abs/2110.03708v1>

(ref: Espada_etal_2019) Espada, D., Verley, S., Miura, R. E., et al. 2019, ApJ, 887, 88

(ref: Evans_etal_2014) Evans, Neal J., I., Heiderman, A., & Vutisalchavakul, N. 2014, ApJ, 782, 114

(ref: Federrath_Klessen_2012) Federrath, C., & Klessen, R. S. 2012, ApJ, 761, 156

(ref: Feldmann_etal_2012) Feldmann, R., Gnedin, N. Y., & Kravtsov, A. V. 2012, ApJ, 747, 124

(ref: Field_etal_2011) Field, G. B., Blackman, E. G., & Keto, E. R. 2011, MNRAS, 416, 710

(ref: Freeman_etal_2017) Freeman, P., Rosolowsky, E., Kruijssen, J. M. D., Bastian, N., & Adamo, A. 2017, MNRAS, 468, 1769

(ref: Fukui_Kawamura_2010) Fukui, Y., & Kawamura, A. 2010, ARA&A, 48, 547

(ref: Fukui_etal_1999) Fukui, Y., Mizuno, N., Yamaguchi, R., et al. 1999, PASJ, 51, 745

(ref: Genzel_etal_2012) Genzel, R., Tacconi, L. J., Combes, F., et al. 2012, ApJ, 746, 69

(ref: Girichidis_etal_2020) Girichidis, P., Offner, S. S. R., Kritsuk, A. G., et al. 2020, Space Sci. Rev., 216, 68

(ref: Glover_MacLow_2011) Glover, S. C. O., & Mac Low, M. M. 2011, MNRAS, 412, 337

(ref: Gong_etal_2020) Gong, M., Ostriker, E. C., Kim, C.-G., & Kim, J.-G. 2020, ApJ, 903, 142

(ref: Grudic_etal_2018) Grudić, M. Y., Hopkins, P. F., Faucher-Giguère, C.-A., et al. 2018, MNRAS, 475, 3511

(ref: NumPy_2020) Harris, C. R., Millman, K. J., van der Walt, S. J., et al. 2020, Nature, 585, 357

(ref: Hennebelle_Chabrier_2011) Hennebelle, P., & Chabrier, G. 2011, ApJL, 743, L29

(ref: Henshaw_etal_2016) Henshaw, J. D., Longmore, S. N., Kruijssen, J. M. D., et al. 2016, MNRAS, 457, 2675

(ref: Henshaw_etal_2020) Henshaw, J. D., Kruijssen, J. M. D., Longmore, S. N., et al. 2020, Nature Astronomy, 4, 1064

(ref: Herrera_etal_2020) Herrera, C. N., Pety, J., Hughes, A., et al. 2020, A&A, 634, A121

(ref: Herrera-Endoqui_etal_2015) Herrera-Endoqui, M., Dı́az-Garcı́a, S., Laurikainen, E., & Salo, H. 2015, A&A, 582, A86

(ref: Heyer_Dame_2015) Heyer, M., & Dame, T. M. 2015, ARA&A, 53, 583

(ref: Heyer_etal_2009) Heyer, M., Krawczyk, C., Duval, J., & Jackson, J. M. 2009, ApJ, 699, 1092

(ref: Heyer_etal_2001) Heyer, M. H., Carpenter, J. M., & Snell, R. L. 2001, ApJ, 551, 852

(ref: Hirota_etal_2018) Hirota, A., Egusa, F., Baba, J., et al. 2018, PASJ, 70, 73

(ref: Hughes_etal_2013a) Hughes, A., Meidt, S. E., Colombo, D., et al. 2013a, ApJ, 779, 46

(ref: Hughes_etal_2013b) Hughes, A., Meidt, S. E., Schinnerer, E., et al. 2013b, ApJ, 779, 44

(ref: Matplotlib_2007) Hunter, J. D. 2007, Computing in Science and Engineering, 9, 90

(ref: Ibanez-Mejia_etal_2016) Ibáñez-Mejı́a, J. C., Mac Low, M.-M., Klessen, R. S., & Baczynski, C. 2016, ApJ, 824, 41

(ref: Imara_Faesi_2019) Imara, N., & Faesi, C. M. 2019, ApJ, 876, 141

(ref: Israel_1997) Israel, F. P. 1997, A&A, 328, 471

(ref: Israel_2020) —. 2020, A&A, 635, A131

(ref: James_etal_2013) James, G., Witten, D., Hastie, T., & Tibshirani, R. 2013, An introduction to statistical learning, Vol. 112 (Springer), doi:10.1007/978-1-4614-7138-7

(ref: Jeffreson_Kruijssen_2018) Jeffreson, S. M. R., & Kruijssen, J. M. D. 2018, MNRAS, 476, 3688

(ref: Jeffreson_etal_2020) Jeffreson, S. M. R., Kruijssen, J. M. D., Keller, B. W., Chevance, M., & Glover, S. C. O. 2020, MNRAS, 498, 385

(ref: Kass_Raftery_1995) Kass, R. E., & Raftery, A. E. 1995, Journal of the American Statistical Association, 90, 773. <http://www.jstor.org/stable/2291091>

(ref: Kawamura_etal_2009) Kawamura, A., Mizuno, Y., Minamidani, T., et al. 2009, ApJS, 184, 1

(ref: Kennicutt_1998) Kennicutt, Robert C., J. 1998a, ARA&A, 36, 189

(ref: Kennicutt_1998a) —. 1998b, ApJ, 498, 541

(ref: Kennicutt_Evans_2012) Kennicutt, R. C., & Evans, N. J. 2012, ARA&A, 50, 531

(ref: Kim_Ostriker_2017) Kim, C.-G., & Ostriker, E. C. 2017, ApJ, 846, 133

(ref: KimJY_etal_2020) Kim, J., Chevance, M., Kruijssen, J. M. D., et al. 2021a, MNRAS, 504, 487

(ref: Kim_etal_2018) Kim, J.-G., Kim, W.-T., & Ostriker, E. C. 2018, ApJ, 859, 68

(ref: KimJG_etal_2020) Kim, J.-G., Ostriker, E. C., & Filippova, N. 2021b, ApJ, 911, 128

(ref: Klessen_Glover_2016) Klessen, R. S., & Glover, S. C. O. 2016, Saas-Fee Advanced Course, 43, 85

(ref: Koch_etal_2020) Koch, E. W., Chiang, I.-D., Utomo, D., et al. 2020, MNRAS, 492, 2663

(ref: Koda_etal_2009) Koda, J., Scoville, N., Sawada, T., et al. 2009, ApJL, 700, L132

(ref: Koribalski_etal_2018) Koribalski, B. S., Wang, J., Kamphuis, P., et al. 2018, MNRAS, 478, 1611

(ref: Krieger_etal_2021) Krieger, N., Walter, F., Bolatto, A. D., et al. 2021, ApJL, 915, L3

(ref: Kroupa_2001) Kroupa, P. 2001, MNRAS, 322, 231

(ref: Kruijssen_etal_2019b) Kruijssen, J. M. D., Schruba, A., Chevance, M., et al. 2019a, Nature, 569, 519

(ref: Kruijssen_etal_2019a) Kruijssen, J. M. D., Dale, J. E., Longmore, S. N., et al. 2019b, MNRAS, 484, 5734

(ref: Krumholz_Burkert_2010) Krumholz, M., & Burkert, A. 2010, ApJ, 724, 895

(ref: Krumholz_etal_2018) Krumholz, M. R., Burkhart, B., Forbes, J. C., & Crocker, R. M. 2018, MNRAS, 477, 2716

(ref: Krumholz_McKee_2005) Krumholz, M. R., & McKee, C. F. 2005, ApJ, 630, 250

(ref: Lang_etal_2020) Lang, P., Meidt, S. E., Rosolowsky, E., et al. 2020, ApJ, 897, 122

(ref: Larson_1981) Larson, R. B. 1981, MNRAS, 194, 809

(ref: Lee_etal_2016) Lee, E. J., Miville-Deschênes, M.-A., & Murray, N. W. 2016, ApJ, 833, 229

(ref: Lee_etal_2021) Lee, J. C., Whitmore, B. C., Thilker, D. A., et al. 2021, arXiv e-prints, arXiv:2101.02855

(ref: Leroy_etal_2006) Leroy, A., Bolatto, A., Walter, F., & Blitz, L. 2006, ApJ, 643, 825

(ref: Leroy_etal_2008) Leroy, A. K., Walter, F., Brinks, E., et al. 2008, AJ, 136, 2782

(ref: Leroy_etal_2009) Leroy, A. K., Walter, F., Bigiel, F., et al. 2009, AJ, 137, 4670

(ref: Leroy_etal_2011) Leroy, A. K., Bolatto, A., Gordon, K., et al. 2011, ApJ, 737, 12

(ref: Leroy_etal_2013b) Leroy, A. K., Lee, C., Schruba, A., et al. 2013, ApJL, 769, L12

(ref: Leroy_etal_2015a) Leroy, A. K., Bolatto, A. D., Ostriker, E. C., et al. 2015, ApJ, 801, 25

(ref: Leroy_etal_2016) Leroy, A. K., Hughes, A., Schruba, A., et al. 2016, ApJ, 831, 16

(ref: Leroy_etal_2017a) Leroy, A. K., Schinnerer, E., Hughes, A., et al. 2017, ApJ, 846, 71

(ref: Leroy_etal_2019) Leroy, A. K., Sandstrom, K. M., Lang, D., et al. 2019, ApJS, 244, 24

(ref: Leroy_etal_2021a) Leroy, A. K., Schinnerer, E., Hughes, A., et al. 2021a, arXiv e-prints, arXiv:2104.07739

(ref: Leroy_etal_2021b) Leroy, A. K., Hughes, A., Liu, D., et al. 2021b, ApJS, 255, 19

(ref: Leroy_etal_2021c) Leroy, A. K., Rosolowsky, E., Usero, A., et al. 2021c, arXiv e-prints, arXiv:2109.11583

(ref: LiH_etal_2020) Li, H., Vogelsberger, M., Marinacci, F., Sales, L. V., & Torrey, P. 2020, MNRAS, 499, 5862

(ref: LinLH_etal_2020) Lin, L., Ellison, S. L., Pan, H.-A., et al. 2020, ApJ, 903, 145

(ref: LiuLJ_etal_2021) Liu, L., Bureau, M., Blitz, L., et al. 2021, MNRAS, 505, 4048

(ref: Lu_etal_2020) Lu, Z.-J., Pelkonen, V.-M., Padoan, P., et al. 2020, ApJ, 904, 58

(ref: Makarov_etal_2014) Makarov, D., Prugniel, P., Terekhova, N., Courtois, H., & Vauglin, I. 2014, A&A, 570, A13

(ref: McKee_Ostriker_2007) McKee, C. F., & Ostriker, E. C. 2007, ARA&A, 45, 565

(ref: McKee_etal_2015) McKee, C. F., Parravano, A., & Hollenbach, D. J. 2015, ApJ, 814, 13

(ref: Meidt_etal_2018) Meidt, S. E., Leroy, A. K., Rosolowsky, E., et al. 2018, ApJ, 854, 100

(ref: Meidt_etal_2020) Meidt, S. E., Glover, S. C. O., Kruijssen, J. M. D., et al. 2020, ApJ, 892, 73

(ref: Miura_etal_2018) Miura, R. E., Espada, D., Hirota, A., et al. 2018, ApJ, 864, 120

(ref: Miville-Deschenes_etal_2017) Miville-Deschênes, M.-A., Murray, N., & Lee, E. J. 2017, ApJ, 834, 57

(ref: Mizuno_etal_2001a) Mizuno, N., Rubio, M., Mizuno, A., et al. 2001, PASJ, 53, L45

(ref: Muraoka_etal_2019) Muraoka, K., Sorai, K., Miyamoto, Y., et al. 2019, PASJ, 71, S15

(ref: Murphy_etal_2011) Murphy, E. J., Condon, J. J., Schinnerer, E., et al. 2011, ApJ, 737, 67

(ref: Murray_2011) Murray, N. 2011, ApJ, 729, 133

(ref: Murray_etal_2010) Murray, N., Quataert, E., & Thompson, T. A. 2010, ApJ, 709, 191

(ref: Murugeshan_etal_2019) Murugeshan, C., Kilborn, V., Obreschkow, D., et al. 2019, MNRAS, 483, 2398

(ref: Nakanishi_Sofue_2006) Nakanishi, H., & Sofue, Y. 2006, PASJ, 58, 847

(ref: Narayanan_etal_2012) Narayanan, D., Krumholz, M. R., Ostriker, E. C., & Hernquist, L. 2012, MNRAS, 421, 3127

(ref: Oka_etal_2001) Oka, T., Hasegawa, T., Sato, F., et al. 2001, ApJ, 562, 348

(ref: Olsen_etal_2017) Olsen, K., Greve, T. R., Narayanan, D., et al. 2017, ApJ, 846, 105

(ref: Orr_etal_2021a) Orr, M. E., Fielding, D. B., Hayward, C. C., & Burkhart, B. 2021, arXiv e-prints, arXiv:2109.14656

(ref: Padoan_etal_2014) Padoan, P., Federrath, C., Chabrier, G., et al. 2014, in Protostars and Planets VI, ed. H. Beuther, R. S. Klessen, C. P. Dullemond, & T. Henning, 77

(ref: Padoan_Nordlund_2011) Padoan, P., & Nordlund, Å. 2011, ApJ, 730, 40

(ref: Pan_etal_2015a) Pan, H.-A., Fujimoto, Y., Tasker, E. J., et al. 2015, MNRAS, 453, 3082

(ref: Pan_etal_2022) Pan, H.-A., Schinnerer, E., Hughes, A., et al. 2022, arXiv e-prints, arXiv:2201.01403

(ref: Scikit-learn_2011) Pedregosa, F., Varoquaux, G., Gramfort, A., et al. 2011, Journal of Machine Learning Research, 12, 2825. <http://jmlr.org/papers/v12/pedregosa11a.html>

(ref: Persic_etal_1996) Persic, M., Salucci, P., & Stel, F. 1996, MNRAS, 281, 27

(ref: Pettini_Pagel_2004) Pettini, M., & Pagel, B. E. J. 2004, MNRAS, 348, L59

(ref: Pilyugin_Grebel_2016) Pilyugin, L. S., & Grebel, E. K. 2016, MNRAS, 457, 3678

(ref: Pilyugin_etal_2014) Pilyugin, L. S., Grebel, E. K., & Kniazev, A. Y. 2014, AJ, 147, 131

(ref: Pineda_etal_2009) Pineda, J. E., Rosolowsky, E. W., & Goodman, A. A. 2009, ApJL, 699, L134

(ref: Popping_etal_2019a) Popping, G., Narayanan, D., Somerville, R. S., Faisst, A. L., & Krumholz, M. R. 2019, MNRAS, 482, 4906

(ref: Querejeta_etal_2021) Querejeta, M., Schinnerer, E., Meidt, S., et al. 2021, arXiv e-prints, arXiv:2109.04491

(ref: Rice_etal_2016) Rice, T. S., Goodman, A. A., Bergin, E. A., Beaumont, C., & Dame, T. M. 2016, ApJ, 822, 52

(ref: APLpy_2012) Robitaille, T., & Bressert, E. 2012, APLpy: Astronomical Plotting Library in Python, Astrophysics Source Code Library, ascl:1208.017

(ref: Rosolowsky_Leroy_2006) Rosolowsky, E., & Leroy, A. 2006, PASP, 118, 590

(ref: Rosolowsky_etal_2021) Rosolowsky, E., Hughes, A., Leroy, A. K., et al. 2021, MNRAS, 502, 1218

(ref: S4G_2010) S4G team. 2010, Spitzer Survey of Stellar Structure in Galaxies, IRSA, doi:10.26131/IRSA425. <https://doi.org/10.26131/IRSA425>

(ref: Saintonge_Catinella_2022) Saintonge, A., & Catinella, B. 2022, arXiv e-prints, arXiv:2202.00690

(ref: Salim_etal_2016) Salim, S., Lee, J. C., Janowiecki, S., et al. 2016, ApJS, 227, 2

(ref: Salo_etal_2015) Salo, H., Laurikainen, E., Laine, J., et al. 2015, ApJS, 219, 4

(ref: Sanchez_etal_2014) Sánchez, S. F., Rosales-Ortega, F. F., Iglesias-Páramo, J., et al. 2014, A&A, 563, A49

(ref: Sanchez_etal_2019) Sánchez, S. F., Barrera-Ballesteros, J. K., López-Cobá, C., et al. 2019, MNRAS, 484, 3042

(ref: Sanchez_etal_2021) Sánchez, S. F., Barrera-Ballesteros, J. K., Colombo, D., et al. 2021, MNRAS, 503, 1615

(ref: z0MGS_2019) Sandstrom, K. 2019, z=0 Multiwavelength Galaxy Synthesis, IRSA, doi:10.26131/IRSA6. <https://doi.org/10.26131/IRSA6>

(ref: Sandstrom_etal_2013) Sandstrom, K. M., Leroy, A. K., Walter, F., et al. 2013, ApJ, 777, 5

(ref: Schmidt_1959) Schmidt, M. 1959, ApJ, 129, 243

(ref: Schruba_etal_2019) Schruba, A., Kruijssen, J. M. D., & Leroy, A. K. 2019, ApJ, 883, 2

(ref: Schruba_etal_2012) Schruba, A., Leroy, A. K., Walter, F., et al. 2012, AJ, 143, 138

(ref: Schruba_etal_2017) Schruba, A., Leroy, A. K., Kruijssen, J. M. D., et al. 2017, ApJ, 835, 278

(ref: Schwarz_1978) Schwarz, G. 1978, The Annals of Statistics, 6, 461

(ref: Scoville_Hersh_1979) Scoville, N. Z., & Hersh, K. 1979, ApJ, 229, 578

(ref: Sheth_etal_2010) Sheth, K., Regan, M., Hinz, J. L., et al. 2010, PASP, 122, 1397

(ref: Silk_1997) Silk, J. 1997, ApJ, 481, 703

(ref: Solomon_etal_1987) Solomon, P. M., Rivolo, A. R., Barrett, J., & Yahil, A. 1987, ApJ, 319, 730

(ref: Sorai_etal_2019) Sorai, K., Kuno, N., Muraoka, K., et al. 2019, PASJ, 71, S14

(ref: Spilker_etal_2021) Spilker, A., Kainulainen, J., & Orkisz, J. 2021, A&A, 653, A63

(ref: Stuber_etal_2021) Stuber, S. K., Saito, T., Schinnerer, E., et al. 2021, A&A, 653, A172

(ref: MegaTable_3.0) Sun, J. 2022, PhangsTeam/MegaTable: PHANGS mega-table pipeline public release, v3.0, Zenodo, doi:10.5281/zenodo.6584842

(ref: Sun_etal_2018) Sun, J., Leroy, A. K., Schruba, A., et al. 2018, ApJ, 860, 172

(ref: Sun_etal_2020a) Sun, J., Leroy, A. K., Schinnerer, E., et al. 2020a, ApJL, 901, L8

(ref: Sun_etal_2020b) Sun, J., Leroy, A. K., Ostriker, E. C., et al. 2020b, ApJ, 892, 148

(ref: Tan_2000) Tan, J. C. 2000, ApJ, 536, 173

(ref: Teng_etal_2021) Teng, Y.-H., Sandstrom, K. M., Sun, J., et al. 2021, ApJ submitted

(ref: Pandas_1.3.4) The pandas development team. 2021, Pandas-Dev/Pandas: Pandas, vv1.3.4, Zenodo, doi:10.5281/zenodo.5574486

(ref: Tibshirani_1996) Tibshirani, R. 1996, Journal of the Royal Statistical Society. Series B (Methodological), 58, 267. <http://www.jstor.org/stable/2346178>

(ref: Tress_etal_2020b) Treß, R. G., Sormani, M. C., Smith, R. J., et al. 2021, MNRAS, 505, 5438

(ref: Ueda_etal_2012) Ueda, J., Iono, D., Petitpas, G., et al. 2012, ApJ, 745, 65

(ref: Utomo_etal_2015) Utomo, D., Blitz, L., Davis, T., et al. 2015, ApJ, 803, 16

(ref: Utomo_etal_2017) Utomo, D., Bolatto, A. D., Wong, T., et al. 2017, ApJ, 849, 26

(ref: Utomo_etal_2018) Utomo, D., Sun, J., Leroy, A. K., et al. 2018, ApJL, 861, L18

(ref: Utreras_etal_2020) Utreras, J., Blanc, G. A., Escala, A., et al. 2020, ApJ, 892, 94

(ref: Vallini_etal_2018) Vallini, L., Pallottini, A., Ferrara, A., et al. 2018, MNRAS, 473, 271

(ref: Verschuur_1993) Verschuur, G. L. 1993, AJ, 106, 2580

(ref: SciPy_2020) Virtanen, P., Gommers, R., Oliphant, T. E., et al. 2020, Nature Methods, 17, 261

(ref: Vutisalchavakul_etal_2016) Vutisalchavakul, N., Evans, Neal J., I., & Heyer, M. 2016, ApJ, 831, 73

(ref: Walter_etal_2008) Walter, F., Brinks, E., de Blok, W. J. G., et al. 2008, AJ, 136, 2563

(ref: Williams_etal_2021a) Williams, T. G., Kreckel, K., Belfiore, F., et al. 2021, arXiv e-prints, arXiv:2110.10697

(ref: Wilson_1995) Wilson, C. D. 1995, ApJL, 448, L97

(ref: Wolfire_etal_2010) Wolfire, M. G., Hollenbach, D., & McKee, C. F. 2010, ApJ, 716, 1191

(ref: Wong_2009) Wong, T. 2009, ApJ, 705, 650

(ref: Yim_etal_2011) Yim, K., Wong, T., Howk, J. C., & van der Hulst, J. M. 2011, AJ, 141, 48

(ref: Yim_etal_2014) Yim, K., Wong, T., Xue, R., et al. 2014, AJ, 148, 127

(ref: Zucker_etal_2018) Zucker, C., Battersby, C., & Goodman, A. 2018, ApJ, 864, 153

[^1]: We use PHANGS–ALMA internal data release v4, which corresponds to the first full public release.

[^2]: We use the v4 resolution-matched catalogs as described in A. Hughes et al. (in preparation).

[^3]: This radius is defined as the geometrical mean of the fitted semi-major and semi-minor axes for each identified object (cite: Rosolowsky_etal_2021).

[^4]: Since the beam is usually over-sampled by the pixel grid in observational data, in theory $M_\mathrm{pix}$ should only be derived for each *independent* beam (rather than for each pixel) in order to conserve the total molecular gas mass budget. In this work, we only use $M_\mathrm{pix}$ as an intermediate quantity to derive other pixel-based measurements, and none of these measurements requires an accurate gas mass accounting. Therefore, we do not explicitly distinguish between measurements per beam versus per pixel.

[^5]: We use PHANGS–H$\alpha$ internal data release version 2.3.

[^6]: <https://github.com/PhangsTeam/MegaTable>

[^7]: Given the large aperture size, choosing a different threshold (e.g., 10%) would make a negligible difference in the classification results.

[^8]: We use $M_\mathrm{mol}=M_\mathrm{obj}/2$ for the object-based measurements to be consistent with our calculations in Section [2.1.1](#sec:data:CO:obj).

[^9]: This mass-weighted harmonic mean can be very convenient in the following scenario: if all clouds form stars on their corresponding free-fall timescale with the same efficiency per free-fall time ($\epsilon_\mathrm{ff}$), one can easily derive the total SFR of a cloud population via $\epsilon_\mathrm{ff}\,M_\mathrm{tot}/\bar{t}_\mathrm{ff}$, where $M_\mathrm{tot}$ is the total gas mass held by the cloud population, and $\bar{t}_\mathrm{ff}$ the population-averaged free fall time defined by the mass-weighted harmonic mean.

[^10]: We note that some studies in the literature argue for a longer molecular cloud lifetime on the order of $100$ Myr (cite: Scoville_Hersh_1979; Koda_etal_2009). These studies typically use the timescales of galactic dynamical processes (such as orbital time or spiral arm crossing time) as anchoring points to derive molecular cloud lifetimes, which might partly explain why their estimated cloud lifetimes are comparatively longer.

[^11]: <http://leda.univ-lyon1.fr>

[^12]: <http://www.adsabs.harvard.edu>

[^13]: <https://www.canfar.net/storage/vault/list/phangs/RELEASES/Sun_etal_2022>

[^14]: <https://doi.org/10.11570/22.0072>

</paper>

## Items to check

```json
[
 {
  "path": "data.other_facilities[3].provided.evidence[1]",
  "value": "3.4 um (W1) near-IR and 22 um mid-IR imaging compiled by z0MGS to trace stellar mass and obscured star formation",
  "failed_quote": "We use mid-IR images from *WISE* and far-/\n\\[0\\]near-UV images from the *Galaxy Evolution Explorer (GALEX)* to trace the distribution of obscured and unobscured star formation."
 },
 {
  "path": "data.other_facilities[4].provided.evidence[0]",
  "value": "FUV (154 nm) and NUV (231 nm) imaging compiled by z0MGS to trace unobscured star formation",
  "failed_quote": "We use mid-IR images from *WISE* and far-/\n\\[0\\]near-UV images from the *Galaxy Evolution Explorer (GALEX)* to trace the distribution of obscured and unobscured star formation."
 }
]
```
