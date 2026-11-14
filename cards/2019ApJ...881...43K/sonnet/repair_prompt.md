# Repair task for a Claude Code subagent

A methods card has evidence quotes that were not found verbatim in the paper. Below are the rules, the paper, and the failing items. Write ONE JSON object, nothing else, of the form {"repairs": [{"path": ..., "found": true|false, "loc": ..., "quote": ...}, ...]} with one entry per item (path unchanged) to:

    C:\Users\adama\alma-corpus\cards\2019ApJ...881...43K\sonnet\repair_reply.txt

Use the Write tool for that file. Copy each quote character for character from the paper text below; a returned quote is checked mechanically and dropped if it is not in the paper. Do not read any other file, do not run commands, and do not change anything else. Reply with one line when done.

---

## Rules

You check evidence quotes for a methods card extracted from an astronomy paper. Some quotes could not be found verbatim in the paper text, and some stated values came without a quote. For each item: find the passage in the paper that supports the value and copy it VERBATIM (same words and order, at most 40 words; LaTeX markup may be dropped) with its loc (section heading, "abstract", "Table N" or "Figure N caption"). If the paper does not support the value, return found = false and leave quote and loc empty. Use only the paper text. Return one entry per item, with the item's path unchanged.

## Paper

<paper>
# The Molecular Outflow in NGC 253 at a Resolution of Two Parsecs

## Abstract

We present 0.15$''$ ($\sim2.5$ pc) resolution ALMA CO(3–2) observations of the starbursting center in NGC 253. Together with archival ALMA CO(1–0) and CO(2–1) data we decompose the emission into a disk and non–disk component. We find $\sim7-16\%$ of the CO luminosity to be associated with the non-disk component ($1.2-4.2 \times 10^7$ K km s$^{-1}$ pc$^2$). The total molecular gas mass in the center of NGC 253 is $\sim3.6\times10^8$ M$_\odot$ with $\sim0.5\times10^8$ M$_\odot$ ($\sim15\%$) in the non-disk component. These measurements are consistent across independent mass estimates through three CO transitions. The high-resolution CO(3–2) observations allow us to identify the molecular outflow within the non-disk gas. Using a starburst conversion factor, we estimate the deprojected molecular mass outflow rate, kinetic energy and momentum in the starburst of NGC 253. The deprojected molecular mass outflow rate is in the range $\sim 14-39$ M$_\odot$ yr$^{-1}$ with an uncertainty of 0.4 dex. The large spread arises due to different interpretations of the kinematics of the observed gas while the errors are due to unknown geometry. The majority of this outflow rate is contributed by distinct outflows perpendicular to the disk, with a significant contribution by diffuse molecular gas. This results in a mass loading factor $\eta = \dot{M}_\mathrm{out} / \dot{M}_\mathrm{SFR}$ in the range $\eta\sim8-20$ for gas ejected out to $\sim300$ pc. We find the kinetic energy of the outflow to be $\sim2.5-4.5\times10^{54}$ erg and $\sim0.8$ dex typical error which is $\sim0.1$% of the total or $\sim8$% of the kinetic energy supplied by the starburst. The outflow momentum is $4.8-8.7\times10^8$ M$_\odot$ km s$^{-1}$($\sim0.5$ dex error) or $\sim2.5-4$% of the kinetic momentum released into the ISM by feedback. The unknown outflow geometry and launching sites are the primary source of uncertainty in this study.

# Introduction

Outflows driven by star formation are thought to be a crucial driver of galaxy evolution. Strong stellar feedback caused by high star formation rate densities can launch outflows of ionized, neutral and molecular gas that potentially can escape the main body of a galaxy. Consequently, such outflowing gas removes the potential fuel for future star formation. Therefore, outflows can suppress and quench star formation, as also demonstrated by theoretical predictions and simulations (cite: 1986ApJ...303...39D; 2017MNRAS.466.1213K; 2018ApJ...857..116M). Depending on the velocity of the outflow and a galaxy’s escape velocity, outflowing gas can be re–accreted at later cosmic times (the so–called ‘galactic fountain’) or leave the system altogether. This process thus has the potential to enrich the galactic disk and circum–galactic medium with heavy metals (cite: Oppenheimer:2006eq; 2010MNRAS.406.2325O; Hopkins:2012ez; Christensen:2018ka).

Galactic outflows are a multi–phase phenomenon and are observed across the electro–magnetic spectrum from X-ray (cite: 2007ApJ...658..258S), UV (cite: 2005ApJ...619L..99H), optical like H$\alpha$ (cite: 2009ApJ...696..192W) to IR (cite: 2009ApJ...700L.149V), cold dust (cite: 2010A&A...518L..66R), PAH emission (cite: 2006ApJ...642L.127E), and sub-millimeter to radio including HI (cite: 2013Natur.499..450B; 2015ApJ...814...83L; Lucero:2015if). Typically, large-scale outflow features at high relative velocity (100s-1000s km s$^{-1}$) are observed in the ionized and neutral gas, whereas molecular outflows often appear as smaller, more compact features (cite: Strickland:2002kp; Westmoquette:2011bp). The latter are nonetheless important as they dominate the mass budget (cite: 2015ApJ...814...83L). In some galaxies, the gas phases seem to be stratified with an inner ionized outflow cone, a surrounding neutral shell, and molecular gas situated along the outer edge (cite: 2015ApJ...801...63M). Typically, the outflows originate from an extended region, so the apparent outflow cone has its tip cut-off.

Molecular outflows are thus closely intertwined with feedback processes and star formation. The high-resolution structure and kinematic properties of (molecular) outflows are not studied in great detail yet, primarily due to the lack of high resolution and sensitivity observations. Starburst galaxies are the obvious target to study star formation-driven outflows due to the high star formation rates (SFR) in these system. Consequently, molecular outflows have been studied over the past years in a few nearby starbursts : M 82 (cite: 2002ApJ...580L..21W; 2015ApJ...814...83L), NGC 253 (cite: 2013Natur.499..450B; 2017ApJ...835..265W; 2018ApJ...867..111Z), NGC 1808 (cite: 2018ApJ...856...97S), and ESO320-G030 (cite: 2016A&A...594A..81P).

NGC 253 is one of the nearest starburst systems at a distance of 3.5 Mpc (cite: Rekola:2005ha). It is considered one of the prototypical starburst galaxies with a star formation rate surface density of $\Sigma_{SFR} \sim 10^2$ M$_\odot$ yr$^{-1}$ kpc$^{-2}$ in the nuclear region and a molecular depletion time that is $\tau^{mol}_{dep} \sim 5-25$ times lower than what is found in local disks (cite: Leroy:2015ds). A galactic wind emerges from the central $\sim 200$ pc of NGC 253 that has been characterized in H$\alpha$, X-ray, as well as neutral and molecular gas emission (cite: Sharp:2010jl; Turner:1985iy; Sturm:2011jb; Strickland:2000wd; Strickland:2002kp; Westmoquette:2011bp; 2000ApJS..129..493H; 2013Natur.499..450B; 2017ApJ...835..265W). Due to the close proximity, starburst and galactic winds can be studied in detail and individual structures can be resolved.

Studies of the molecular gas phase in NGC 253 showed that its central starburst is fueled by gas accretion along the bar (cite: 2004ApJ...611..835P). The molecular ISM in the nuclear region is structured in several clumps that show high temperatures of $\sim 50$ K (cite: 2004ApJ...611..835P; Sakamoto:2011et; 2019ApJ...871..170M). From earlier low resolution observations (cite: 2006ApJ...636..685S; Sakamoto:2011et) to recent observations at high resolution ($8\,\mathrm{pc}\times5$ pc in (cite: 2017ApJ...849...81A) and 2 pc in (cite: 2018ApJ...869..126L)) the number of molecular clumps associated the starburst increased from $\sim5$ to 14. These studies find the clumps to be massive ($4-10 \times 10^4$ M$_\odot$), compact ($<10$ pc), chemically rich (up to $>19$ molecules detected in the 0.8 mm band) and hot (up to 90 K). Each clump likely hosts an embedded massive star cluster (cite: 2018ApJ...869..126L). Further structures in the molecular gas are shells and bubbles blown up by feedback from the intense star formation process. (cite: 2006ApJ...636..685S) found two 100 pc diameter superbubbles. (cite: 2013Natur.499..450B) report molecular streamers[^1] originating from these shells with a lower limit to the outflow rate of $3-9$ M$_\odot$ yr$^{-1}$, about three times the star formation rate. This estimate was revisited by (cite: 2018ApJ...867..111Z), based on observations that show that the CO emission associated with the most prominent streamer is optically thick, increasing it to $25-50$ M$_\odot$ yr$^{-1}$.

As suggested by these studies, the outflow rate in NGC 253 is factors of a few to potentially $>10$ larger than the star formation rate. Hence, the impact of the outflows on the amount of material lost from the molecular gas reservoir, and thus the lifetime of the starburst, is significant. The availability of new data makes it interesting to revisit the determination of the mass outflow rate in NGC 253, while also removing some limitations of previous determinations. (cite: 2013Natur.499..450B) estimated the outflow rate from a few massive molecular streamers, but did not include potential diffuse outflowing gas. Also, resolution plays an important role in the ability to disentangle outflows from material in the starbursting disk. New ALMA band 7 observations provide excellent spatial resolution and reasonable surface brightness sensitivity. This information enables increasingly accurate determination of the total mass outflow rate, and its impact on the starburst.

In this work, we present ALMA CO(3–2) observations carried out in cycle 3 and 4 that target the molecular gas in the central $\sim 750$ pc of NGC 253. Together with ancillary band 3 and 6 data from our previous work (cite: 2013Natur.499..450B; 2015ApJ...801...63M; Leroy:2015ds; 2018ApJ...867..111Z), we have an inventory of three CO lines to study the molecular gas in the starbursting disk and a kinematically different component that includes the outflow. By decomposing the detected emission, we aim to measure the total molecular gas outflow rate in NGC 253 and improve upon previous less systematic results.

Throughout this paper, we adopt a distance of 3.5 Mpc to NGC 253 (cite: Rekola:2005ha) at which 1$''$ corresponds to 17 pc. We also define the “center” of the nuclear region of NGC 253 to be the kinematic center at $\alpha, \delta = 00^h47^m33.134^s, -25^\circ17^m19.68^s$ as identified in (cite: MullerSanchez:2010dr). The paper is structured as follows: In section [2](#section: data reduction), we describe observational setup and data reduction, and show the results in the form of channel maps, moment maps and position-velocity diagrams. Our approach on separating gas in the star-forming disk from potentially outflowing gas is laid out in section [3](#section: disk separation). Section [4](#section: results separated disk/non-disk) discusses the derived quantities such as CO luminosities, molecular gas masses, outflow rate, kinetic energy and momentum. Our conclusions are summarized in section [5](#section: summary).

# Data Reduction and Imaging

|  | CO(1–0) | CO(2–1) | CO(3–2) |
|:---|:--:|:--:|:--:|
| ALMA ID | 2011.1.00172.S | 2012.1.00108.S | 2015.1.00274.S |
| spatial resolution | $1.85\ensuremath{''} \times 1.32\ensuremath{''}$ | $1.70\ensuremath{''} \times 1.02\ensuremath{''}$ | $0.17\ensuremath{''} \times 0.13\ensuremath{''}$ |
|  | 31.4 pc $\times$ 22.4 pc | 28.8 pc $\times$ 17.3 pc | 2.9 pc $\times$ 2.2 pc |
| spectral resolution | 5.0 km s$^{-1}$ | 5.0 km s$^{-1}$ | 2.5 km s$^{-1}$ |
| RMS noise per channel | 1.99 mJy beam$^{-1}$ | 2.19 mJy beam$^{-1}$ | 0.81 mJy beam$^{-1}$ |
|  | 75 mK | 29 mK | 0.37 K |

: Details of the datasets used in this analysis.

## Data reduction

The data presented in this paper are based on observations in ALMA cycles 2, 3 and 4 in bands 3, 6 and 7 that cover the redshifted emission in NGC 253 of CO(1–0), CO(2–1) and CO(3–2) as well as other molecular lines. For data reduction and imaging of the band 3 and 6 data see (cite: 2013Natur.499..450B), (cite: Leroy:2015ds), (cite: 2015ApJ...801...63M) and (cite: 2018ApJ...867..111Z). Table [1](#table: used datasets) gives an overview of the datasets used in this analysis.

For the band 7 observations, we tuned the lower side band to $342.0-345.8$ GHz and the upper side band to $353.9-357.7$ GHz (total bandwidth 7.6 GHz) with 976.6 kHz channel width (corresponding to 0.8 km s$^{-1}$). We targeted the central $\sim 750$ pc of NGC 253 in a linear four pointing mosaic with two configurations of the 12 m array (12 m compact and 12 m extended, half power beam width $\sim 17\ensuremath{''}$) and a five pointing mosaic of the 7 m array (ACA, half power beam width $\sim 30\ensuremath{''}$). Additional single dish observations with the total power array (TP) recovers emission on large spatial scales. The baseline ranges covered by this setup are 8.9-49.0 m, $15.1 - 783.5$ m and $15.1 - 1813.1$ m for the ACA and the two 12 m setups, respectively.

The observations were carried out primarily in the first half of 2016 (TP: 07-Dec-2015 to 02-Aug-2016; ACA: 07-Dec-2015 to 23-Nov-2016; 12 m compact configuration: 16-Apr-2016, 23-Apr-2016, 17-Jun-2016, 27-Jun-2016; 12 m extended configuration: 30-Aug-2016, 03-Sep-2016). The total on-source observation time is $48^h45^m$ split across $27^h:23^m$ (TP), $14^h57^m$ (ACA), $2^h37^m$ (12 m compact) and $3^h59^m$ (12 m extended). The calibrators were: J0006-0623 (bandpass); J0038-2459 (complex gain); the asteroid Pallas (absolute flux density); J0104-2416, J0106-2718 (both WVR). Visibilities of the 12 m data are calibrated using the ALMA cycle 3 pipeline in CASA 4.6.0 and the delivered calibration script. The other datasets are calibrated in CASA 4.7.2 and the cycle 4 pipeline.

In order to image the spectral lines, we subtract the continuum in the $U,V$ plane using a first order polynomial fitted to the channels that do not contain strong spectral lines. We reliably detect $>25$ lines in the range 342.0-345.0 GHz and 353.9-357.7 GHz beside the four strong lines CO(3–2), HCN (4-3), HCO$^+$ (4-3) and CS (7-6). Most of these lines are weak and only detected in small spatial regions so they do not affect the overall continuum fit and subtraction.

## Imaging

Combined imaging of the interferometric data is done with the `tclean` task in CASA 5.4.0 which includes crucial bug fixes for ALMA mosaics[^2]. We regrid the visibilities during deconvolution to a spectral resolution of 2.5 km s$^{-1}$. Applying a Briggs weighting scheme with robust parameter 0.5 results in a synthesized beam of $0.17\ensuremath{''} \times 0.13\ensuremath{''}$ (pixel scale $0.05\ensuremath{''}$). The images are cleaned to a level of $2.5 \times$ the RMS noise in line-free channels of $2.5 \times 0.81$ mJy beam$^{-1}$($2.5 \times 0.37$ K) using a clean mask derived from a low resolution image of the compact 12 m array CO(3–2) data only.

We correct the cleaned images for the mosaic sensitivity pattern (mosaic primary beam response pattern), combine them with the TP images using `feather` and finally convert the units to brightness temperature.

For the final images, we do not consider the ACA data as they introduce large scale noise fluctuation towards the edge of the mosaic, which we attribute to decreasing sensitivity of the 12 m data relative to the ACA data. These fluctuations obscure the regions where outflows have been found previously. This work requires accurate integrated flux measurements and correct representation of the small scale structure which are defined by single dish observations (TP) and long baselines (extended 12 m), respectively. By checking the images without ACA data against the images including ACA data, we can confirm that neither the overall flux scale, nor the small scale structure is significantly altered.

Data products for CO(1–0) are shown in (cite: 2013Natur.499..450B), (cite: 2015ApJ...801...63M), (cite: Leroy:2015ds) and (cite: 2018ApJ...867..111Z) presents the CO(2–1) data. Imaging results for CO(3–2) are presented in the following section.

In order to keep the amount of detail and contrast in the high resolution data, we do not match the spatial resolution to that of the data with the lowest resolution, but perform our analysis at the native resolution of each dataset. All further steps work on the data cubes masked at $5.0 \sigma$ (cf. table [1](#table: used datasets)) and further masks where necessary. For generating the masks, we do not consider the non-uniform noise level caused by the mosaic sensitivity pattern but use the per channel RMS noise in the center of the field of view.

## CO(3–2) data presentation

![](fig1.pdf)

![image](fig2a.pdf) ![image](fig2b.pdf) ![image](fig2c.pdf)

![](fig3.pdf)

In this section, we present the CO(3–2) data in different representations. Channel maps (figure [1](#figure: CO channel map)), moment maps (figure [2](#figure: CO moment maps)) and a position-velocity (pV) diagram (figure [3](#figure: co pV)) show the spatial and kinematic structures to be discussed and highlight the data quality.

Figure [1](#figure: CO channel map) shows channel maps of the image cube. To retain the intrinsic resolution, only every 16$^{th}$ channel (40 km s$^{-1}$ spacing) is shown here. Besides the rotating disk of molecular gas, we clearly detect the prominent south-west (SW) streamer (cite: 2017ApJ...835..265W) in the range $180 - 250$ km s$^{-1}$(Fig. [1](#figure: CO channel map), panels 220 km s$^{-1}$ and 260 km s$^{-1}$). Additional gas streamers are apparent between $\sim 60$ km s$^{-1}$ and $\sim 350$ km s$^{-1}$ towards north and south of the disk as can be seen for example in the panels at 260 km s$^{-1}$ or 340 km s$^{-1}$. Several notable molecular shells are present between 180 km s$^{-1}$ and 340 km s$^{-1}$. Beside the (super-)shells at the eastern (left) and western (right) edge of the map that have been previously identified by (cite: 2006ApJ...636..685S) and (cite: 2013Natur.499..450B), further smaller shell–like structures are located along the molecular disk.

We calculate image moments (figure [2](#figure: CO moment maps)) with `immoments` in CASA for emission above $5\sigma$ for the moment 0 (integrated intensity) map, the moment 1 (intensity-weighted line-of-sight velocity) and moment 2 (intensity-weighted velocity dispersion) maps. Note that due to the complex line shapes, the moment 2 map does not directly correspond to velocity dispersion which is only the case for Gaussian line profiles. The maps are further constrained to the region defined by the collapsed clean mask to limit them to emission that has been processed by the clean algorithm.

Figure [3](#figure: co pV) shows the kinematic structure of NGC 253 as a pV diagram along the major axis of the disk ($\mathrm{PA} = 55^\circ$) averaged over the full width of the field of view ($\sim 30\ensuremath{''}$) centered on the kinematic center. The pV cut shows several high velocity dispersion structures extending from a rotating disk, indicative of outflows.

# Separating disk and non-disk emission

## Separating disk and non-disk emission in position-position-velocity space

Our goal is to account for all the molecular wind, separating outflowing molecular gas from foreground or background disk emission. A clean separation in 2D position-position space cannot be easily accomplished due to the inclination of $78^\circ$ of NGC 253. At this high inclination, outflows and disk emission are co-spatial in projection. Kinematic information from line-of-sight velocities, however, makes it possible to disentangle the outflow. Note that this becomes increasingly difficult as the velocity vector aligns with the plane of the sky, resulting in line-of-sight velocities that are systemic. From H$\alpha$ kinematic modeling the NGC 253 outflow is approximately bi-conical with an axis normal to the disk and an opening angle of $\sim60^\circ$ (cite: Westmoquette:2011bp), and thus the range of possible projection angles is large (see (cite: 2015ApJ...801...63M) for a sketch). Note that because the cone opening angle is larger than the angle between the axis of the cone and the plane of the sky, gas in the approaching and receding cones can have both blue- and red-shifted velocities with respect to systemic.

The launching of molecular gas occurs within the disk through star formation feedback, thus the outflows originate from the same location in position-position-velocity (ppV) space as disk molecular clouds. Outflows will therefore blend into the disk near their launching sites, which makes disentanglement increasingly difficult closer to the starburst region.

The complexity of systematically separating emission corresponding to the disk and the outflow in ppV space is challenging. Algorithmically, this separation is simpler in a lower dimensional space, obtained by slicing the data cube into a collection of 2D position-velocity diagrams. In what follows we identify kinematic components in these diagrams, which then we project back to 3D ppV space. In order to avoid introducing biases we model the large-scale disk velocity field and use this model as the basis of the kinematic separation.

## Definition of components

Images of the center of NGC 253 on large scales show an elongated gas structure (figure [2](#figure: CO moment maps) top) with a regular velocity field (figure [2](#figure: CO moment maps) middle) that roughly matches a rotating disk disturbed by streaming motions from a bar (cite: 2004ApJ...611..835P). The elongated gas structure is consistent with a highly inclined disk of molecular gas, or possibly a ring-like structure as observed in other galaxies (cite: 2016ApJ...823...68S; 2018ApJ...857..116M). Similar structures break up at higher spatial resolution into two embracing spiral arms or complex non-closed orbits in the Milky Way center (cite: 2015MNRAS.453..739K; 2016MNRAS.457.2675H; 2018MNRAS.481....2S).

Superimposed on this large scale structure, there are smaller features that are not part of the large-scale pattern of rotation and streaming motions. Some of them have high aspect ratios in channel maps and line-of-sight velocity gradients, both typical for outflows. Local deviations from the large-scale velocity field can also be due to infalling gas, or clumps of gas that do not follow the global pattern due perhaps to a cloud-cloud collision.

Henceforth, we will refer to the bulk of the molecular gas that moves according to the large-scale velocity field in the central regions of NGC 253 as the *disk*. We assume this large-scale velocity field consists of rotation and streaming motions. The term *non-disk* refers to any gas that is not following the ppV structure of the disk. By this definition, non-disk gas encompasses material from features that may be attributed to a variety of physical processes, including outflow and infall.

Structures of outflowing gas are frequently referred to by names that describe their kinematic or spatial appearance, such as “streamer”. We will use the term outflow to denote localized structures with morphology and kinematics consistent with gas moving away from the disk, as inferred from their location in ppV space. Typical signatures are a velocity that is inconsistent with rotation in the plane of the disk, and a high aspect ratio oriented roughly perpendicular to the disk major axis. Note that similar kinematic and structural properties can arise in infalling gas clouds. We will assume that all molecular gas with these characteristics is outflowing, which is likely the case for the majority of the material in NGC 253.

## Position-velocity slicing

Kinematic analyses typically depend on high signal-to-noise ratios (SNR) because faint features can easily drown in noisy spectra. As a trade-of between necessary high SNR and also trying to include as much faint emission as possible, we conduct the following analysis on data cubes masked at the $5\sigma$ level (cf. table [1](#table: used datasets)).

We split the ppV cubes into position-velocity (pV) slices along the major axis of NGC 253 as shown in figure [4](#figure: slice positions). The slices assume the kinematic center is $\alpha,\delta = 00^h47^m33.134^s, -25^\circ17^m19.68^s$ (cite: MullerSanchez:2010dr), and are oriented along the major axis of the projected CO emission with $\mathrm{PA} = 55^\circ$. The area sliced is chosen to cover the region for which we have overlapping CO(1–0), (2–1) and (3–2), and also cover the full length of the SW streamer outflow feature (cite: 2017ApJ...835..265W).

These requirements are fulfilled by slices of $50\ensuremath{''}$ (850 pc) length (major axis) and covering $50\ensuremath{''}$ (850 pc) along the minor axis (figure [4](#figure: slice positions)). To reduce the problems introduced by splitting features across slices, each slice is $5.0\ensuremath{''}$ (85 pc) wide, and we overlap slices by half their width ($2.5\ensuremath{''}$, 42 pc). A sample pV diagram is shown in figure [5](#figure: sample slice) for the central slice, which runs along the major axis (offset $0.0\ensuremath{''}$). A complete set of pV diagrams is given in appendix [8](#appendix: all pVs). The resolution differences between our three transitions, a factor of $\sim 100$ in beam solid angle, are apparent in figure [5](#figure: sample slice). In the high angular resolution CO(3–2), small features with large linewidth are common. These features are blurred out in the lower resolution CO(1–0) and (2–1).

![image](fig4a.pdf) ![image](fig4b.pdf) ![image](fig4c.pdf)

## Modeling the disk

We derive a model for the velocity of the disk component from the CO(1–0) observations using the kinematic fitting tool `diskfit` (cite: 2007ApJ...664..204S; 2010MNRAS.404.1733S; 2015arXiv150907120S). Because the CO(1–0) observations cover the largest area among our observations, we use them to derive the model; the additional information provided by the CO(2–1) and/or CO(3–2) data is negligible in terms of the bulk motions of the gas. We obtain a CO(1–0) velocity field by computing the first moment of the cube after masking it at $20\sigma$ (1.26 K), in order to represent the velocity of the bright emission. We show the details of the fit parameters and a comparison to the CO(1–0) velocity field in Appendix [6](#appendix: model).

In each pV slice, we use the velocity profile of the `diskfit` model to define the local disk velocity. We consider the CO emission consistent with the disk component of the emission when the velocity difference is within the local observed velocity range, $\Delta v$. This velocity range varies spatially and depends on distance $x$ from the major axis, increasing towards the center due to the combined effects of higher intrinsic velocity dispersion and projection. For the success of this analysis, it is crucial that $\Delta v$ is broad enough to cover the observed velocity range of the disk but also narrow enough in order to not classify potential outflows as disk. The definition of $\Delta v$ is thus a crucial source of uncertainty for the derived quantities. We parametrize the velocity range of the disk as

$$\begin{equation}
    \Delta v\,(x) = 120\,\exp \left( - \left(\frac{x}{2.5}\right)^2 \right) + 100,
    \label{equation: delta v}
\end{equation}$$

with $\Delta v$ in km s$^{-1}$ and $x$ in arcsec. We find this empirical relation to fit the pV data best and small variations of order 10-20% already show noticeable mismatch as is discussed in appendix [7](#appendix: disk velocity range). Note that the parameters (120, 2.5 and 100) in equation [\[equation: delta v\]](#equation: delta v) are visually selected to fit the fit pV diagrams as best as possible. The quality of this definition can be assessed from figure [5](#figure: sample slice) and appendix [8](#appendix: all pVs): The velocity ranges are wide enough to include obvious emission of the disk but do not extend into the kinematically distinct features (potential outflows) that appear as spikes. This is most apparent for CO(3–2) as this line offers the highest spatial resolution. The effect of a 10% change in the velocity range $\Delta v$ correspond to up to 0.1 dex variations in the derived quantities (cf. appendix [7](#appendix: disk velocity range)).

## Selecting the components

We use the modelled velocity field and the $\Delta v$ relation together to define a “disk mask” over ppV space, corresponding to emission that is consistent with disk rotation. We show in figure [5](#figure: sample slice) the central pV slices for CO(1–0), (2–1) and (3–2). We show in Appendix [8](#appendix: all pVs) the complete set of pV slices.

Note that the CO emission extends beyond the disk mask. These extensions are not symmetric, and due to non-disk gas and projection effects. At $\sim78^\circ$ inclination gas flowing perpendicular to the galaxy disk towards the south (negative slice offsets) is primarily approaching us and seen at lower velocities relative to the disk emission. Similarly, outflow emission toward the north is primarily at velocities higher than the disk emission. Consequently, emission in pV slices shifts from lower to higher velocities relative to the disk model when the offset from the major axis increases (see figure [12](#figure: all pV diagrams) in appendix [8](#appendix: all pVs)). We designed the disk mask to be wide enough to capture the disk emission but exclude the asymmetric component caused by outflows.

We define a “non-disk” mask that is the mathematical complement of the disk mask, with the addition of removing emission from known sources (portions of the spiral arms) that were not included in our model of the central disk and are not of interest for this analysis.

![image](fig5a.pdf) ![image](fig5b.pdf) ![image](fig5c.pdf)

## Identifying outflows in the non-disk component

We identify three different types of structures in the non-disk component (figure [6](#figure: separated moments), contours in figure [7](#figure: nondisk zoomin) highlight these structures):

\(1\) Emission that is co-located with the central disk and bar in projection. This is visible as a ridge in CO(3–2) (inner contour in figure [7](#figure: nondisk zoomin)), and also present but less apparent in CO(1–0) and CO(2–1). The structure is unlikely to be an outflow. It appears more likely to be an additional kinematic component of the disk/bar that is not included in the model we used for the separation. We therefore do not consider this gas to contribute to the total mass outflow rate.

\(2\) Emission associated with the so-called western superbubble, located to the west and north of the central starburst region (cite: 2006ApJ...636..685S; 2013Natur.499..450B). This feature is already known to be kinematically distinct from the surrounding gas. Part of it is likely the base of the northern outflow cone (and giving rise to the NW streamers identified by (cite: 2013Natur.499..450B), for example), but it is difficult to know what portion of the emission should be associated with a net outflow. In our calculations below we exclude this feature from the total outflow rate of NGC 253, although it likely has some contribution to outflow.

\(3\) The remaining gas associated with the non-disk component is organized in small clumps along the edge of the disk region or beyond it. Some of this gas is not discernible as individual structures, particularly in the CO(1–0) and CO(2–1) cubes, perhaps due to the resolution but maybe also due to the excitation conditions, constituting extended regions with diffuse emission. Some of the emission is located in well-defined structures known to be part of the outflow, such as the SW streamer which is apparent in all CO transitions.

In summary, the non-disk component consists of these three sub-components: structures that we associate with a net “outflow,” structures that are part of the “western superbubble,” and structures that are co-located with the “disk”. The latter is not associated with the outflow, while parts of the western supperbubble may contribute to it. Below we calculate properties for the two components disk and non-disk, and its sub-components individually where it is feasible to do so.

# Results

The process described in the previous section allows us to estimate the properties of the galactic outflow and other structures. A 2D representation of the separated data cubes is shown in figure [6](#figure: separated moments) in the form of moment maps for integrated intensity (moment 0) and intensity-weighted velocity (moment 1) for all three CO transitions. Striping artifacts due to the pV cuts used in the separation method are present in the disk and non-disk components, visible as straight lines parallel to the major axis. This is primarily aesthetic. We tested their effects on the fluxes and derived velocities by varying the slice width and found them to be negligible.

![image](fig7a.pdf) ![image](fig7b.pdf)

+:------------------------------+:-----------------------------:+:-----------------:+:--------------------:+:-----------------:+:--------------------:+:-----------------:+:--------------------:+
| quantity                      | unit                          | CO(1–0)                                  | CO(2–1)                                  | CO(3–2)                                  |
+-------------------------------+-------------------------------+-------------------+----------------------+-------------------+----------------------+-------------------+----------------------+
|                               |                               | disk              | non-disk             | disk              | non-disk             | disk              | non-disk             |
+-------------------------------+-------------------------------+-------------------+----------------------+-------------------+----------------------+-------------------+----------------------+
| **luminosity**                                                |                   |                      |                   |                      |                   |                      |
+-------------------------------+-------------------------------+-------------------+----------------------+-------------------+----------------------+-------------------+----------------------+
| L$_\mathrm{CO}$               | K km s$^{-1}$ pc$^2$          | $2.8 \times 10^8$ | $4.2 \times 10^7$    | $2.3 \times 10^8$ | $4.5 \times 10^7$    | $1.8 \times 10^8$ | $1.2 \times 10^7$    |
+-------------------------------+-------------------------------+-------------------+----------------------+-------------------+----------------------+-------------------+----------------------+
| fraction                      | \%                            | 87                | 13                   | 84                | 16                   | 94                | 6.5                  |
+-------------------------------+-------------------------------+-------------------+----------------------+-------------------+----------------------+-------------------+----------------------+
| **molecular gas mass $\mathrm{M}_\mathrm{mol}$ $^{\dag}$**    |                   |                      |                   |                      |                   |                      |
+-------------------------------+-------------------------------+-------------------+----------------------+-------------------+----------------------+-------------------+----------------------+
| total$^{a}$                   | M$_\odot$                     | $3.1 \times 10^8$ | $4.5 \times 10^7$    | $3.1 \times 10^8$ | $6.1 \times 10^7$    | $2.9 \times 10^8$ | $2.0 \times 10^7$    |
+-------------------------------+-------------------------------+-------------------+----------------------+-------------------+----------------------+-------------------+----------------------+
| outflow$^{b}$                 | M$_\odot$                     |                   | $2.7 \times 10^7$    |                   | $4.1 \times 10^7$    |                   | $8.3 \times 10^6$    |
+-------------------------------+-------------------------------+-------------------+----------------------+-------------------+----------------------+-------------------+----------------------+
| superbubble$^{c}$             | M$_\odot$                     |                   | $8.9 \times 10^6$    |                   | $8.9 \times 10^6$    |                   | $5.8 \times 10^6$    |
+-------------------------------+-------------------------------+-------------------+----------------------+-------------------+----------------------+-------------------+----------------------+
| other-disk$^{d}$              | M$_\odot$                     |                   | $7.6 \times 10^6$    |                   | $7.4 \times 10^6$    |                   | $5.8 \times 10^6$    |
+-------------------------------+-------------------------------+-------------------+----------------------+-------------------+----------------------+-------------------+----------------------+
| **molecular mass outflow rate $\dot{M}$**                     |                   |                      |                   |                      |                   |                      |
+-------------------------------+-------------------------------+-------------------+----------------------+-------------------+----------------------+-------------------+----------------------+
| outflow (continuous)$^{e}$    | M$_\odot$ yr$^{-1}$           |                   | 14                   |                   | 20                   |                   | 2.7                  |
+-------------------------------+-------------------------------+-------------------+----------------------+-------------------+----------------------+-------------------+----------------------+
| outflow (constant)$^{f}$      | M$_\odot$ yr$^{-1}$           |                   | 29                   |                   | 39                   |                   | 4.8                  |
+-------------------------------+-------------------------------+-------------------+----------------------+-------------------+----------------------+-------------------+----------------------+
| **kinetic energy $\mathrm{E}_\mathrm{kin}$ $^{\S}$**          |                   |                      |                   |                      |                   |                      |
+-------------------------------+-------------------------------+-------------------+----------------------+-------------------+----------------------+-------------------+----------------------+
| outflow (continuous)$^{e}$    | erg s$^{-1}$                  |                   | $3.9 \times 10^{54}$ |                   | $4.5 \times 10^{54}$ |                   | $6.5 \times 10^{53}$ |
+-------------------------------+-------------------------------+-------------------+----------------------+-------------------+----------------------+-------------------+----------------------+
| outflow (constant)$^{f}$      | erg s$^{-1}$                  |                   | $2.5 \times 10^{54}$ |                   | $3.1 \times 10^{54}$ |                   | $4.3 \times 10^{53}$ |
+-------------------------------+-------------------------------+-------------------+----------------------+-------------------+----------------------+-------------------+----------------------+
| **momentum $\mathrm{P}$ $^{\P}$**                             |                   |                      |                   |                      |                   |                      |
+-------------------------------+-------------------------------+-------------------+----------------------+-------------------+----------------------+-------------------+----------------------+
| outflow (continuous)$^{e}$    | M$_\odot$ km s$^{-1}$         |                   | $6.9 \times 10^8$    |                   | $8.7 \times 10^8$    |                   | $1.2 \times 10^8$    |
+-------------------------------+-------------------------------+-------------------+----------------------+-------------------+----------------------+-------------------+----------------------+
| outflow (constant)$^{f}$      | M$_\odot$ km s$^{-1}$         |                   | $4.8 \times 10^8$    |                   | $6.4 \times 10^8$    |                   | $8.0 \times 10^7$    |
+-------------------------------+-------------------------------+-------------------+----------------------+-------------------+----------------------+-------------------+----------------------+

: Results of separating disk from non-disk emission in NGC 253. Uncertainties for these quantities are discussed in the corresponding subsections of section [4](#section: results separated disk/non-disk).

Table notes: Sources of error are discussed and quantified in the respective subsections of section [4](#section: results separated disk/non-disk). $^{a}$ CO line luminosity of all emission considered consistent with disk rotation (disk) and not consistent with disk rotation (non-disk), respectively. $^{b}$ Non-disk excluding the western superbubble and the gas that is co-spatial with the projected disk. $^{c}$ Non-disk emission belonging to the western superbubble as defined by (cite: 2006ApJ...636..685S) $^{d}$ Non-disk gas that is co-spatial with the disk in projection. See section [4.3](#section: outflow rate) for the definition. $^{e}$ Outflowing gas as defined by note $^b$ under the assumption of continuous mass ejection without accelerations to the gas after ejection. $^{f}$ Outflowing gas as defined by note $^b$ under the assumption of approximately constant starting mass outflow rate over the lifetime of the starburst. $^{\dag}$ Molecular gas mass derived using a conversion factor for CO(1–0) emission of $\mathrm{X}_{\mathrm{CO}} = 0.5\times10^{20}\,\left(\mathrm{K\,km\,s}^{-1}\right)^{-1}$, including the contribution of Helium, and assuming CO brightness temperature line ratios of $r_{21} = 0.80$ and $r_{31} = 0.67$ for CO(2–1) and CO(3–2) relative to CO(1–0). $^{\ddag}$ Deprojected molecular mass outflow rate. $50^{th}$ percentile best estimate assuming a flat distribution of outflow inclinations for the unknown geometry. $^{\S}$ Deprojected kinetic energy of the molecular gas. $50^{th}$ percentile best estimate assuming a flat distribution of outflow inclinations for the unknown geometry. $^{\P}$ Deprojected momentum of the molecular gas. $50^{th}$ percentile best estimate assuming a flat distribution of outflow inclinations for the unknown geometry.

## CO luminosities

We quantify in table [2](#table: results) the CO luminosities of the disk and non-disk components. We measure luminosities of $2.8 \times 10^8$ K km s$^{-1}$ pc$^2$, $2.3 \times 10^8$ K km s$^{-1}$ pc$^2$ and $1.8 \times 10^8$ K km s$^{-1}$ pc$^2$ for CO(1–0), (2–1) and (3–2), respectively, in the central disk of NGC 253. The non-disk component is, naturally, much fainter with luminosities of $\sim 4.2 \times 10^7$ K km s$^{-1}$ pc$^2$ for CO(1–0), $\sim 4.2 \times 10^7$ K km s$^{-1}$ pc$^2$ for (2–1) and $\sim 4.2 \times 10^7$ K km s$^{-1}$ pc$^2$(3–2). These correspond to approximately $12.9\%$, 16.4% and 6.5% of the total luminosity. These luminosities are measured over the sliced area (cf. figure [4](#figure: slice positions)) for which the coverage is not the same among the datasets. We therefore also measure luminosities integrated over the same spatial region, here defined as the overlap between the datasets. This overlap amounts to 885 $''$$^2$ ($2.55\times10^5$ pc$^2$). The luminosities in the overlap area are: disk: $2.6 \times 10^8$ K km s$^{-1}$ pc$^2$, $2.1 \times 10^8$ K km s$^{-1}$ pc$^2$ and $1.8 \times 10^8$ K km s$^{-1}$ pc$^2$; non-disk: $2.6 \times 10^7$ K km s$^{-1}$ pc$^2$, $2.4 \times 10^7$ K km s$^{-1}$ pc$^2$ and $1.2 \times 10^7$ K km s$^{-1}$ pc$^2$ for CO(1–0), (2–1) and (3–2), respectively.

An interesting result coming out of our decomposition is that not all the material we identify as “outflow” is in well-defined structures such as the streamers identified by (cite: 2013Natur.499..450B). Correctly estimating the outflow rate requires accounting also for a diffuse extended component.

It is important to compare our fluxes to measurements in the literature. (cite: 1996A&A...305..421M) find a CO(2–1) luminosity of $1.2 \times 10^6$ K km s$^{-1}$ arcsec$^2$ which translates[^3] to $3.5 \times 10^8$ K km s$^{-1}$ pc$^2$ or $1.3$ times our measurement. Their observations cover $80\ensuremath{''} \times 60\ensuremath{''}$, a area similar to our CO(1–0) observations (but $\sim 4$ times larger than the area of our CO(3–2) observations). For the outflow CO(1–0) luminosity, (cite: 2013Natur.499..450B) derive an estimate of $2.0 \times 10^7$ K km s$^{-1}$ pc$^2$ by summing over individual identified molecular outflow features. This includes flux from the “superbubble” component, so it is probably better compared to the sum of our “outflow” and “superbubble” components of $\sim3.6\times10^7$ K km s$^{-1}$ pc$^2$. Given the large methodological differences and the importance of the diffuse emission, these numbers are in reasonable agreement.

## Masses of components

The total gas mass $M$ is estimated from the CO line luminosity, using the conversion factor $\mathrm{X}_{\mathrm{CO}} = 0.5\times10^{20}\,\left(\mathrm{K\,km\,s}^{-1}\right)^{-1}$ cm$^{-2}$ corresponding to $\alpha_\mathrm{CO} = 1.1\,\mathrm{M}_\odot\,\left(\mathrm{K\,km\,s}^{-1}\,\mathrm{pc}^{-1}\right)^{-1}$ discussed by (cite: Leroy:2015ds) for the central starburst region. This value accounts for the effects of moderate optical depth, high velocity dispersion, and warm gas temperatures that are likely to dominate the central regions of NGC 253. The masses we report include the contribution of Helium to the total mass. To compute masses using the CO(2–1) and CO(3–2) transitions we assume typical line ratios of $r_{21} = 0.80$ and $r_{31} = 0.67$ relative to CO(1–0) as implied by (cite: 2018ApJ...867..111Z). Note that we do not measure line ratios from the images but adopt a uniform factor to keep the mass measurements from the three observed CO lines independent.

Table [2](#table: results) lists the masses corresponding to the disk and the non-disk components. Uncertainty in the mass estimates arises primarily from the assumed conversion factor and the apportioning of emission among the different components. The calibration uncertainty for the flux measurements is $\sim10-15\%$ for the ALMA observations. Overall, we adopt a systematic error of factor $\sim2$ for the the derived masses.

The molecular masses derived from the three CO transitions are very similar. They match within 10% for the disk component, and within 50% for the non-disk component. We estimate the total gas mass in the center of NGC 253 to be $\sim 3.5 \times 10^8$ M$_\odot$ (adding the disk and non-disk components), with estimates in the range of $3.1-3.6 \times 10^8$ M$_\odot$ for the different transitions. About 85% of the total mass is in the disk component. The masses estimated in the non-disk components using CO(1–0) and CO(2–1) are fairly similar at $4.5 \times 10^7$ M$_\odot$ and $6.1 \times 10^7$ M$_\odot$ whereas in CO(3–2) we detect a lower $2.0 \times 10^7$ M$_\odot$, a consequence of the lower luminosity. The non-disk masses are primarily contributed by the outflow component ($\sim 50$%). About $20-30$% of mass is in the western supperbubble and $12-30$% is co-spatial with the disk but kinematically distinct.

It is important to compare these mass estimates to previous results for the total molecular gas mass in NGC 253, noting that our analysis covers the central $45\ensuremath{''} \times 25\ensuremath{''}$ ($750\,\mathrm{pc} \times 400\,\mathrm{pc}$). Towards the east, $\sim 10\%$ of the known molecular gas close to the center is not covered by our CO(3–2) observations and thus not considered in this analysis. The agreement with previous measurements is very good. (cite: 1996A&A...305..421M) reported a mass of $1.3 \times 10^8$ M$_\odot$ over a similar area ($80\ensuremath{''} \times 60\ensuremath{''}$ in the center of NGC 253), but this was based on a different distance and $\mathrm{X}_{\mathrm{CO}}$. After correcting for those differences, their luminosity corresponds to $4.2 \times 10^8$ M$_\odot$, consistent with our measurement. Using the same distance and the same 1–0 observations, (cite: Leroy:2015ds) measure a molecular mass of $3.5 \times 10^8$ M$_\odot$. (cite: 2018ApJ...860...23P) report a total gas mass of $4.5 \times 10^8$ M$_\odot$ derived from the sub-mm dust spectral energy distribution, which is very consistent with our result given the very different methodologies.

No estimates in the literature separate the “disk” and “non-disk” components as we do above. Previous estimates of the outflowing mass range from a lower limit of $6.6 \times 10^6$ M$_\odot$ calculated for the optically thin limit (cite: 2013Natur.499..450B), to $2-4 \times 10^7$ M$_\odot$ when accounting for optical depth (cite: 2018ApJ...867..111Z). Since we identify an outflowing mass $\sim5\times10^7$ M$_\odot$, the agreement with the latter estimate is fairly good. Note, however, that these studies derive the outflowing mass from individual features rather than using the position-velocity information as we do here in a systematic way.

## Mass outflow rate

![image](fig8a.pdf)\
![image](fig8b.pdf)

A mass flow rate is defined as the flux of mass per unit time through a surface. In our case, we are interested in the flow of molecular gas mass through a virtual closed surface around the center of NGC 253 at a given distance. Note that an individual outflow feature observed over a certain length, such as the SW streamer, can develop in at least two ways: as the distance of an outflow from its origin corresponds to time since ejection times velocity, continuously outflowing gas results in extended streaming structures. Gas ejected at a single ejection event in the past with a distribution of ejection velocities, on the other hand, will also result in an extended streamer. In reality gas will be ejected with a distribution of velocities at a varying rate over a period of time, and in order to interpret the measurements we need to make some simplifying assumptions. We chose two edge cases to span the range of different interpretations: (1) the gas does not experience accelerations after being launched (cite: 2017ApJ...835..265W), and (2) that the gas outflow rate is approximately constant with time. For all calculations, however, we assume that the projected direction of flow is perpendicular the the central plane of the bar and that CO emission traces the mass with a constant conversion factor.

We compute both the outflow rate as a function of distance and as a function of time. If we assume that the mass outflow rate has been approximately constant over the lifetime of the starburst, for example, a diminishing outflow rate as a function of distance would suggest that gas is either launched with or somehow develops a distribution of velocities. Conversely, if we assume that the present day velocity has been constant since the gas was ejected, we can derive a history of the mass outflow rate as a function of time and account for a variable mass outflow rate. Both interpretations are equally, but not simultaneously, valid.

For the detailed calculation of the mass outflow rate, we proceed as follows. A mass outflow rate is $\dot{\mathrm{M}} = \mathrm{M} \,t^{-1}$ with mass M and relevant time scale $t$. For each image element $i$ (3D pixel or sometimes also called voxel), we calculate the outflow rate $\dot{m}_i$ of the gas that was ejected at time $t_{{\mathrm{eject}},i}$ over the time interval $\Delta t_{\mathrm{cross},i}$, as the ratio of mass of the pixel ${m}_i$ to the pixel crossing interval $t_{\mathrm{cross},i}$. Ejection time and pixel crossing interval are functions of the outflow velocity $v_i$ and the distance $s_i$ between current pixel position and the launching site, and the pixel size in the direction of the flow $\Delta s$, respectively. We therefore compute $$\begin{eqnarray}
    \Delta t_{\mathrm{cross},i}   &=& \frac{\Delta s}{v_i}\\    
    \dot{m}_i\ (t_{\mathrm{eject},i}) &=& \frac{m_i}{\Delta t_{\mathrm{cross},i}}\\
    t_{\mathrm{eject},i} &=& \frac{s_i}{v_i}
\end{eqnarray}$$

obtaining a mass outflow rate $\dot{m}_i$, a distance $s_i$, and an ejection time $t_{\mathrm{eject},i}$ for each pixel in the “outflow” component. Note that this approach takes the 3D phase space information into account by treating pixels independently. Typically, a sightline shows multiple pixels with emission at different velocities that all contribute an outflow rate with their respective mass, distance and velocity. We then bin the outflow rates $\dot{m}_i$ by ejection time $t_{\mathrm{eject},i}$ and integrate over the time range $\left[\mathrm{T}_1, \mathrm{T}_2 \right]$ to obtain the average outflow rate in this time interval, $$\begin{equation}
    \dot{M} \left( \mathrm{T}_1, \mathrm{T}_2 \right) = 
    \frac{\displaystyle \sum_i \dot{m}_i \left( \mathrm{T}_1 < t_{\mathrm{eject},i} < \mathrm{T}_2 \right)  \Delta t_{\mathrm{cross},i} }{\displaystyle \mathrm{T}_2 - \mathrm{T}_1 }.
    \label{equation: outflow rate time}
\end{equation}$$

Similarly, binning by distance results in the average outflow rate at a given distance, $$\begin{equation}
    \dot{M} \left( \mathrm{D}_1, \mathrm{D}_2 \right) =
    \frac{\displaystyle \sum_i \dot{m}_i \left( \mathrm{D}_1 < s_i < \mathrm{D}_2 \right) \Delta s }{\displaystyle \mathrm{D}_2 - \mathrm{D}_1 }.
    \label{equation: outflow rate distance}
\end{equation}$$ Performing binning on a sequence of time intervals yields the outflow rate history, while binning in distance tells us how far from the launching site a given fraction of the mass is able to escape.

Calculating velocity $v$ and distance $s$ requires knowledge about the geometry and origin of each outflowing gas parcel. The simplest assumption, used here, is that on average outflows are launched in the plane of the central region of the galaxy which corresponds to launching on the major axis. The distance $s$ is thus the projected distance to the major axis on the edge of an outflow cone with given opening angle. Note that the outflow originates from an extended region in the disk and the term cone thus refers to a cut-off cone (called a frustum in geometry). Velocity $v$ is the velocity difference between launching site and current velocity of the outflow parcel, i.e. the velocity difference over distance $s$. Both the velocity of the launching site and the projected distance are uncertain. The velocity changes by $\pm 25$ km s$^{-1}$ when an outflow originates from the northern/southern edge of the observed CO disk (above/below the plane), while the projected distance traveled by the gas changes by $\pm1.25\ensuremath{''}$ ($\pm20$ pc).

Distance $s$, ejection time scale $t_\mathrm{eject}$ and pixel crossing time scale $t_\mathrm{cross}$ are measured as projected quantities that need to be deprojected to account for the outflow geometry. The bright molecular streamers (the SW and SE streamers) seem to lie at the edge of the ionized outflow cone with $\sim60^\circ$ opening angle (cite: 2013Natur.499..450B). Assuming that all molecular outflows are along this cone, and that the axis of the cone is oriented perpendicular to the disk ($i = 78^\circ$), the range of effective inclination of outflowing gas can be anywhere between $\theta = 48^\circ$ and $\theta = 108^\circ$. Deprojected velocity, $v_\mathrm{depro} = v_\mathrm{obs} / \sin\theta$, and distance, $s_\mathrm{depro} = s_\mathrm{obs} / \cos\theta$, have a direct effect on the deprojected outflow rate, $\dot{m}_\mathrm{depro} = \dot{m}_\mathrm{obs} \tan\theta$, and also on the inferred time and distance evolution of the outflow rate. We use a Monte Carlo approach to derive the errors introduced by deprojection, assuming that the outflow direction has an equal probability of being in any direction along the surface of the outflow cone.

Figure [8](#figure: outflow rate) shows the molecular mass outflow rate as a function of time or distance, corresponding to the two alternative interpretations we discuss above: a flow where the distribution of material is interpreted as resulting from the history of mass outflow rate (top panel), and one where we show the mass outflow rate as a function of distance, which under the assumption of a constant outflow rate over the last several Myr can be interpreted as an efficiency of ejection to a given distance (bottom panel). Indeed, for an outflow with a distribution of velocities the slower material will not travel as far in a given time, neither will it escape the galaxy if it does not have a high enough velocity. Close to the starburst region (or at small times since ejection) the mass outflow rate drops to zero, because it becomes increasingly difficult to separate the “outflow” component from the “disk” component. At large values of distance or time it also drops to zero, due to a decreasing amount of outflowing molecular material detected far from the starbursts (and the fact that the observations have a limited field-of-view). The constant outflow rate out to $\sim 300$ pc is in tension with (cite: 2018ApJ...853..173K) who find a steeply dropping “cold” ($\mathrm{T}<5050$ K) component in their TIGRESS simulation. Within 400 pc, they find the averaged mass loading factor to drop by two orders of magnitude. It is unlikely that the SFR in NGC 253 has increased by two orders of magnitude within the past 1-2 Gyr which would alter the observed constant outflow rate profile to be consistent with the (cite: 2018ApJ...853..173K) simulation. Note, however, that their simulation recreates solar neighborhood-like conditions instead of a starburst. A direct comparison may thus be not possible.

Our data show that the *average* outflow rates within 20$''$ (340 pc) from the major axis are 29 M$_\odot$ yr$^{-1}$($^{+0.48}_{-0.35}$ dex), 39 M$_\odot$ yr$^{-1}$($^{+0.49}_{-0.34}$ dex) and 4.8 M$_\odot$ yr$^{-1}$($^{+0.50}_{-0.39}$ dex) for CO(1–0), (2–1) and (3–2) respectively. Similarly, within the past 1.0 Myr, the *average* outflow rates are 14 M$_\odot$ yr$^{-1}$($^{+0.25}_{-0.29}$ dex), 20 M$_\odot$ yr$^{-1}$($^{+0.27}_{-0.37}$ dex) and 2.7 M$_\odot$ yr$^{-1}$($^{+0.22}_{-0.56}$ dex) for CO(1–0), (2–1) and (3–2) respectively. The uncertainties, indicated by the $16^{th}$ to $84^{th}$ percentile in the Monte Carlo described above, are substantial at a factor of $2-3$. Real systematic uncertainties are even larger, since there can be conversion of molecular into atomic material (cite: 2015ApJ...814...83L), or in general variations in the CO-to-H$_2$ conversion.

Note that the average outflow rates quoted above differ between the two representations, with the median outflow rate as a function of distance being about twice as high as a function of time. The outflowing mass is identical in both cases, and the difference arises solely from binning. Comparing between lines, it is apparent that as measured in CO(3–2) the outflow rate is roughly one order of magnitude lower than for the lower two transitions. This is a direct consequence of the lower mass detected in CO(3–2), and the smaller field-of-view of those observations. The CO(3–2) observations cover only $\sim 12.5\ensuremath{''}$ ($\sim 210$ pc projected) above/below the disk and thus miss significant amounts of non-disk gas. Their lower surface brightness sensitivity means we also fail to detect a diffuse non-disk component, as we see in the two lower lines. The measurements in CO(3–2) should thus be interpreted as a lower limit, and in that sense they are consistent with those for the lower two transitions.

Overall, the deprojected total mass outflow rate in the starburst of NGC 253 is most likely in the range $\sim 14-39$ M$_\odot$ yr$^{-1}$ as derived from CO(1–0) and CO(2–1) with $\sim 0.4$ dex uncertainty. The large spread arises due to different interpretations of the kinematics of the observed gas while the errors are due to unknown geometry. The majority of this outflow rate is contributed by massive outflows alongside the disk like the SW/SE streamers, with a significant contribution by diffuse molecular gas.

The present day star formation rate in the central region of NGC 253 is $1.7-2.8$ M$_\odot$ yr$^{-1}$, derived from radio continuum and far-infrared measurements (cite: Ott:2005il; Leroy:2015ds; 2015MNRAS.450L..80B). This results in a mass loading factor $\eta = \dot{M}_\mathrm{out} / \dot{M}_\mathrm{SFR}$ in the range $\eta \sim 5.4-23.5$. Note that this is for gas ejected as far as 340 pc. We do not currently know what fraction of the gas makes it to the far regions of the halo, or reaches escape velocity from the system. Theoretical works suggest that most of the molecular outflow will not escape but rain back down on the galaxy (e.g. (cite: Shapiro:1976ha) up to recent work by (cite: 2018ApJ...853..173K) or (cite: 2019MNRAS.tmp..540T)).

In our data, no gas reaches the escape velocity of $v_\mathrm{esc} = 500$ km s$^{-1}$(cite: 2017ApJ...835..265W). The uncertainty on $v_\mathrm{esc}$ is substantial, so allowing a factor of two is still plausible. At $v_\mathrm{esc} = 250$ km s$^{-1}$, the fraction of gas above $v_\mathrm{esc}$ by mass is 0.5%, 0.5% and 6.0% for CO(1–0), CO(2–1) and CO(3–2), respectively. The mismatch between the lower transitions and CO(3–2) implies that some high velocity gas can be found on small scales that is blurred out in the low resolution observations.

This estimate of the molecular mass outflow rate is higher than the lower limit found by (cite: 2013Natur.499..450B) for optically thin emission. (cite: 2018ApJ...867..111Z) analysis of the CO line ratios in the SW streamer shows that the emission there is optically thick, which the authors used this to rescale the (cite: 2013Natur.499..450B) measurements finding a NGC 253 galactic outflow rate of $25-50$ M$_\odot$ yr$^{-1}$. The result presented here, a mass outflow rate of $\sim 14-39$ M$_\odot$ yr$^{-1}$, is consistent with this number using an independent and a more complete methodology than the original work.

From H$\alpha$ observations by (cite: Westmoquette:2011bp), we can estimate the ionized outflow rate to $\sim 4$ M$_\odot$ yr$^{-1}$ using their ionized mass ($\mathrm{M} = 10^7$ M$_\odot$) and typical velocity (200 km s$^{-1}$) at mean deprojected distance (510 pc). X-ray observations yield comparable values. (cite: Strickland:2000wd) finds an upper limit of 2.2 M$_\odot$ yr$^{-1}$ assuming a standard outflow velocity of 3000 km s$^{-1}$. The upper limit reported in (cite: Strickland:2002kp) translates to 2.3 M$_\odot$ yr$^{-1}$ when assuming 3000 km s$^{-1}$ outflow velocity and a reasonable 10% filling factor. These estimates scale linearly with the unknown velocity and also depend on the unknown metallicity and filling factor in the outflow. Estimates of the outflow rate in neutral gas are not known in the literature but are arguably at a similar level. The molecular phase thus clearly dominates the mass budget in the outflow close to the disk as found in other galaxies (e.g. M82, (cite: 2015ApJ...814...83L) and simulations, e.g. (cite: 2018ApJ...853..173K)).

## Outflow energy and momentum

![image](fig9a.pdf)   ![image](fig9b.pdf)\
![image](fig9c.pdf)   ![image](fig9d.pdf)

Similar to mass outflow rate, energy and momentum can be calculated as a function of time and distance which is shown in figure [9](#figure: outflow energy momentum). In equations [\[equation: outflow rate time\]](#equation: outflow rate time) and [\[equation: outflow rate distance\]](#equation: outflow rate distance) the molecular outflow rate $\dot{m}_i$ is replaced by kinetic energy $E_{\mathrm{kin},i} = \frac{1}{2} m_i\,v_i^2$ or momentum $P_i = m_i\,v_i$. As with the outflow rate, the dominant sources of error are the uncertainty in the launching site and the geometry for which we Monte Carlo the errors as described before. Our median estimate with 16$^{th}$ and 84$^{th}$ percentile uncertainties are given below and in table [2](#table: results).

The kinetic energy in the outflow integrated over the past 1.0 Myr is $3.9 \times 10^{54}$ erg ($^{+0.91}_{-0.75}$ dex) in CO(1–0), $4.5 \times 10^{54}$ erg ($^{+0.94}_{-0.80}$ dex) in CO(2–1), and $6.5 \times 10^{53}$ erg ($^{+0.58}_{-0.83}$ dex) for CO(3–2). Within 20$''$ (340 pc), the kinetic energies amount to $2.5 \times 10^{54}$ erg ($^{+0.96}_{-0.65}$ dex) in CO(1–0), $3.1 \times 10^{54}$ erg ($^{+0.96}_{-0.65}$ dex) in CO(2–1), and $4.3 \times 10^{53}$ erg ($^{+0.98}_{-0.64}$ dex) for CO(3–2). For the reasons described above, the CO(3–2) measurement is a lower limit, thus the results for the lower transitions are consistent.

NGC 253 does not appear to host an energetically important AGN, and the outflow is driven by the starburst. It is interesting then to compare our results for the kinetic energy to the energy released by the starburst. We assume the current star formation rate of $\sim 2.8$ M$_\odot$ yr$^{-1}$ in the central region (cite: Ott:2005il; 2015MNRAS.450L..80B) that has been approximately constant over the last few Myr.

The total energy $E_\mathrm{bol}$ produced by the starburst is simply the time integrated bolometric luminosity $L_\mathrm{bol}$ which depends[^4] on the bolometric magnitude $M_\mathrm{bol}$. $$\begin{eqnarray}
    E_\mathrm{bol} &=& L_\mathrm{bol} \times \Delta t\\
    &=& 3 \times 10^{35-0.4\,M_\mathrm{bol}} \Delta t \left( \frac{SFR}{1\,\mathrm{M}_\odot\,\mathrm{yr}^{-1}} \right)\,\mathrm{erg\,s}^{-1}
    \label{equation: bolometric energy}
\end{eqnarray}$$ According to Starburst99 (cite: Leitherer:1999jt), the bolometric magnitude of a starburst at an age of $10^7$ yr to $10^8$ yr is $M_\mathrm{bol} \sim -20.5$ for $\mathrm{SFR} = 1$ M$_\odot$ yr$^{-1}$. The total energy output of the starburst over the past 1 Myr is thus $4.2 \times 10^{57}$ erg. The observed kinetic energy $\sim3.9-4.5\times10^{54}$ erg in the outflow is a factor of $\sim 10^3$ lower which places the coupling efficiency of outflow kinetic energy to starburst energy at $\sim 0.1$%.

In terms of only kinetic energy, the fraction is higher. Primarily supernovae and winds supply kinetic energy to the ISM which can be estimated from the energy deposition rate according to (cite: Leitherer:1999jt) as given in (cite: Chisholm:2017bu) and (cite: Murray:2005jt). $$\begin{eqnarray}
    \dot{E}_\mathrm{SN} &= 3 \times 10^{41} \left( \frac{SFR}{1\,\mathrm{M}_\odot\,\mathrm{yr}^{-1}} \right) \,\mathrm{erg\,s}^{-1}
    \label{equation: supernova energy}
\end{eqnarray}$$ Each SN releases approximately $10^{51}$ erg in kinetic energy, with the progenitor releasing a similar amount of kinetic energy during its lifetime by winds (cite: Leitherer:1999jt). The approximate total kinetic energy released by SNe in the past 1 Myr is then $\sim 5.3 \times 10^{55}$ erg, compared to the $\sim3.9-4.5\times10^{54}$ erg we observe in the outflow. Hence, the observed starburst is sufficient to kinetically power the measured molecular outflows with $\sim 8\%$ efficiency.

The commonly adopted 50% relative contribution of wind feedback is a first order estimate that is subject to environmental dependence and requires careful modeling to determine precisely (cite: Leitherer:1999jt). Furthermore, it should be noted that the observed outflow energy and its error is based on a fixed mass conversion factor that may vary. The uncertainty on the energy coupling efficiency is thus substantial and it should be understood as an order of magnitude comparison.

The above calculation ignores the contribution of other energies, such as the turbulent energy within the molecular outflow and the kinetic energy of the neutral and ionized gas. (cite: 2009ApJ...701.1636M) derived a kinetic energy of the ionized wind in NGC 253 of $1.3 \times 10^{53}$ erg or more than one order of magnitude lower than the molecular outflow kinetic energy. The molecular outflow is slower ($50-100$ km s$^{-1}$ on the scales we observed here) than the ionized outflow (cite: 2009ApJ...701.1636M) but also more massive. The ionized outflow thus has only a very small effect on the total kinetic energy and the coupling efficiency.

Deprojected outflow momenta integrated over the past 1.0 Myr are $6.9 \times 10^8$ M$_\odot$ km s$^{-1}$($^{+0.50}_{-0.49}$ dex), $8.7 \times 10^8$ M$_\odot$ km s$^{-1}$($^{+0.57}_{-0.57}$ dex) and $1.2 \times 10^8$ M$_\odot$ km s$^{-1}$($^{+0.33}_{-0.59}$ dex) for CO(1–0), (2–1) and (3–2), respectively. Within 20$''$ (340 pc) deprojected distance from the launching site the outflow momenta integrate to $4.8 \times 10^8$ M$_\odot$ km s$^{-1}$($^{+0.48}_{-0.35}$ dex) in CO(1–0), $6.4 \times 10^8$ M$_\odot$ km s$^{-1}$($^{+0.49}_{-0.34}$ dex) in CO(2–1) and $8.0 \times 10^7$ M$_\odot$ km s$^{-1}$($^{+0.50}_{-0.39}$ dex) in CO(3–2).

The momentum released initially by SNe is given in (cite: Murray:2005jt): $$\begin{eqnarray}
    \dot{P}_\mathrm{SN} &=& 2 \times 10^{33} \left( \frac{SFR}{1\,\mathrm{M}_\odot\,\mathrm{yr}^{-1}} \right) \,\mathrm{g\,cm\,s}^{-2} \\
    &=& 317 \left( \frac{SFR}{1\,\mathrm{M}_\odot\,\mathrm{yr}^{-1}} \right) \,\mathrm{M_\odot\,yr}^{-1}\,\mathrm{km\,s}^{-1}
    \label{equation: supernova momentum}
\end{eqnarray}$$ In 1 Myr, a constant SFR of 2.8 M$_\odot$ yr$^{-1}$ yields $8.9 \times 10^8$ M$_\odot$ km s$^{-1}$. Assuming a contribution by stellar winds of the same order (cite: Leitherer:1999jt), the total momentum is $1.8 \times 10^9$ M$_\odot$ km s$^{-1}$ or roughly twice the observed outflow momentum. SNe, however, gain significant amounts[^5] of momentum by sweeping up surrounding material. From simulations, the total momentum supplied to the ISM is expected to be $2.8 \times 10^5$ M$_\odot$ km s$^{-1}$ per SNe ((cite: Kim:2015iy) and references therein). For a constant SFR of 2.8 M$_\odot$ yr$^{-1}$ over 1 Myr, this amounts to $1.0 \times 10^{10}$ M$_\odot$ km s$^{-1}$ or $2.0 \times 10^{10}$ M$_\odot$ km s$^{-1}$ when adopting 50% contribution by stellar winds which is about four times the observed momentum. The efficiency of transferring feedback momentum to outflow momentum is thus in the range $27-49$% considering the initially available momentum or $2.5-4$% efficiency for total to outflow momentum transfer.

These outflow momenta are much higher than the momentum currently produced by young ($<10$ Myr) super star clusters in the starburst. (cite: 2018ApJ...869..126L) list 14 candidate clusters that together produce $1.5\times10^7$ M$_\odot$ km s$^{-1}$ measured from gas kinematics, a factor $10-100$ lower than the observed outflow momentum. The currently forming (super-) star cluster thus could not have launched the outflow but the feedback of another population of stars is needed to explain the observed outflows. This is indicative of the time delay of SF feedback.

Energy and momentum curves in figure [9](#figure: outflow energy momentum) differ only by a factor $v$ but follow a similar evolution. This implies that the median velocity at a given distance must be roughly constant along the outflow. As the curves as a function of distance are roughly constant within $50\,\mathrm{pc}<s<300\,\mathrm{pc}$, especially for kinetic energy, the outflow mass at a given distance must also be approximately constant along the outflow. The decline in energy and momentum below 50 pc is caused by a decrease in outflow mass, again because both curves follow a similar trend. This is at least partially related to the difficulty of separating outflow from disk where the former emerges from the latter. The decrease could also be interpreted physically as the outflow sweeping up mass while emerging from the disk. An estimation of the relative importance of these effects requires high-resolution modelling of the outflow that are not possible yet because we do not know the detailed outflow geometry. The drop beyond $\sim 300$ pc ($\sim 200$ pc in CO(3–2)) is partially related to reaching the edge of the field-of-view. Discerning this effect from an actual decrease is not possible with our data as we do not know the inclination at every location in the outflow. The edge of the field-of-view thus corresponds to a range of deprojected distances from the disk which gradually depresses the curve rather than showing a sudden drop. A physical reason for the decrease could be the destruction of the molecular gas, e.g. photo-dissociation by the intense starburst radiation or ionization.

The kinetic energy and momentum evolution in figure [9](#figure: outflow energy momentum) thus suggest both energy and momentum conservation along the outflow from $\sim50$ pc to $\sim 300$ pc, as well as approximately constant molecular gas mass.

When additionally assuming no acceleration of the outflow after launch, it becomes possible to study the time evolution. The corresponding plots (figure [8](#figure: outflow rate) top and [9](#figure: outflow energy momentum) top) all show a peak within the past 0.5 Myr and steady decrease towards earlier gas ejection times. Corresponding to the decline towards zero distance, the decrease towards zero ejection time is most likely a methodological complication. From the peak at t$_\mathrm{eject} = 0.2-0.3$ Myr, kinetic energy and momentum in the outflow drops by a factor of 10 within $\sim 2$ Myr. This decline would be physically plausible if the starburst in NGC 253 is very young and taking into account a time delay between start of star formation, feedback and efficient outflow driving (superbubble breakout). For the observed age of the starburst of $20-30$ Myr (cite: Rieke:1980hh; Engelbracht:1998cj) this scenario is implausible. Time delays of $>20$ Myr are longer than the lifetime of the most massive stars. A younger generation of massive stars at an age of $\sim 6$ Myr (cite: Kornei:2009ee) may, however, drive the currently visible molecular outflows. If this were to be true, a time delay between star formation and outflow launching of $\sim 4$ Myr is implied. Outflow launching in this context means the time after which the outflow reaches a mass loading $\eta>1$. The time delay is 2 Myr until the outflow carries more energy (momentum) than the feedback kinetic energy (momentum) of a single high mass star. Note that these rough estimates depend on the assumption of no acceleration (positive, nor negative) of the outflow after being launched from the disk which might be a close enough approximation on these scales of a few hundred parsecs. The very young ($\lesssim 1$ Myr) and still deeply embedded super star cluster discussed recently by (cite: 2017ApJ...849...81A) and (cite: 2018ApJ...869..126L) are most likely too young to have affected the observed molecular outflow.

# Summary and Conclusions

We present CO(3–2) observations taken with ALMA that offer an unprecedented resolution of $\sim 0.15\ensuremath{''}$ ($\sim 2$ pc) in the starbursting center of NGC 253. The new high resolution data show structures consistent with previous lower resolution observations in other CO lines, revealing the complexity of the molecular ISM in a starburst on scales of a few parsecs.

We use archival CO(1–0), CO(2–1), and the new CO(3–2) ALMA observations to perform a position-position-velocity decomposition of the emission into different structures. The bulk of the emission is associated with a rotating disk with streaming motions due to the bar. The rest of the emission is incompatible with a simple kinematic model of a disk plus a bar. This “non-disk” component is further decomposed into an outflow, an expanding superbubble (part of which may be associated with outflowing gas) and a potential second kinematic component within the disk.

We find CO line luminosities of the disk component of $2.8\times10^8$ K km s$^{-1}$ pc$^2$, $2.3\times10^8$ K km s$^{-1}$ pc$^2$ and $1.8\times10^8$ K km s$^{-1}$ pc$^2$ for CO(1–0), (2–1) and (3–2), respectively. The fractional luminosity of the non-disk component is small, amounting the $\sim7-16\%$ of the total. A significant amount of the outflow emission we identify is faint and diffuse, while part of the emission is in discrete, higher surface brightness structures (e.g., the SW streamer).

Assuming a starburst conversion factor, we estimate the molecular gas mass from the three CO transitions. Masses match within 10% for the disk component and within 50% for the non-disk component. The total gas mass in the center of NGC 253 is $\sim 3.6 \times 10^8$ M$_\odot$, with $\sim 0.5 \times 10^8$ M$_\odot$ in the non-disk component.

We further estimate the deprojected molecular mass outflow rate, kinetic energy and momentum in the starburst of NGC 253. The observed gas distribution can be interpreted to have formed in two ways: (1) by constant starting mass outflow rate over the lifetime of the starburst and (2) through continuous gas ejection without acceleration of the gas after ejection. In the first interpretation, the molecular mass outflow rate averaged over a deprojected distance of 340 pc (20$''$) from the launching site is $29-39$ M$_\odot$ yr$^{-1}$. Typical uncertainties are 0.4 dex. The majority of this outflow rate is contributed by massive localized features such as the SW/SE streamers, with a significant contribution by diffuse molecular gas. The mass loading factor $\eta=\dot{M}_\mathrm{SFR}/\dot{M}_\mathrm{out}\sim14-20$ is relatively high. Due to the limited field-of-view of our observations, this $\eta$ applies to gas ejected as far away as 340 pc: the fraction of mass that makes it to the far regions of the halo or escapes is not known. The kinetic energy of the molecular outflow within 340 pc from the launching site is $2.5-3.1 \times 10^{54}$ erg with a $\sim 0.8$ dex error. The coupling efficiency of kinetic energy in the outflow to the total energy released by the starburst is $\sim 0.1$% while the coupling to only the kinetic energy is higher at $\sim 8$%. Including other phases of the outflow would increase this efficiency. The kinetic energy of the ionized outflow is negligible relative to the molecular outflow. The outflow momenta within the same distance are $4.8-6.4 \times 10^8$ M$_\odot$ km s$^{-1}$(error $\sim 0.5$ dex) which is $\sim 2.5-4$% of the momentum supplied by SNe and winds. These best estimates for the physical properties of the outflow are derived from the CO(1–0) and (2–1) observations. The very high resolution of the CO(3–2) data is necessary to identify the outflow features that connect to the central regions.

When interpreting the outflow as a structure of constant velocity along the outflow, the time evolution can be reconstructed. We derive outflow rate, kinetic energy and momentum within the approximate dynamical time scale of 1 Myr and find lower values compared to the previous interpretation. The difference is systematic at the $\sim 30-40$% level. The outflow rate is $14-20$ M$_\odot$ yr$^{-1}$(0.3 dex), kinetic energy $2.5-3.1 \times 10^{54}$ erg (0.8 dex) and momentum $4.8-6.4 \times 10^8$ M$_\odot$ km s$^{-1}$(0.5 dex).

For all measurements given above, we assume a fixed starburst mass conversion factor of $\mathrm{X}_{\mathrm{CO}} = 0.5\times10^{20}\,\left(\mathrm{K\,km\,s}^{-1}\right)^{-1}$. The quoted uncertainties are primarily systematic due to the unknown geometry of the outflow and its launching sites. A further uncertainty of $30-40$% ($\sim 0.1$ dex) comes from the assumptions regarding the outflowing material (constant starting mass over the lifetime of the starburst vs. continuous gas ejection without acceleration). These limitations need to be addressed in the future. In principle, ALMA can provide the very high resolution and sensitivity needed to enable this detailed view of a starburst also on larger scales than probed in this study.

# Software

CASA (cite: McMullin:2007tj), astropy (cite: Collaboration:2013cd; Collaboration:2018ji), APLpy (cite: Robitaille:2012wl)

# Acknowledgments

We would like to thank the anonymous referee for their constructive feedback which helped improve the paper. The authors thank Jan-Torge Schindler and Roberto Decarli for insightful discussion and advise. This paper makes use of the following ALMA data: ADS/JAO.ALMA #2011.1.00172.S, #2012.1.00108.S, and #2015.1.00274.S. ALMA is a partnership of ESO (representing its member states), NSF (USA) and NINS (Japan), together with NRC (Canada), NSC and ASIAA (Taiwan), and KASI (Republic of Korea), in cooperation with the Republic of Chile. The Joint ALMA Observatory is operated by ESO, AUI/NRAO and NAOJ. The National Radio Astronomy Observatory is a facility of the National Science Foundation operated under cooperative agreement by Associated Universities, Inc. Part of the work presented in this paper was carried out at the Finnish Center for Astronomy with ESO (FINCA). The work of AKL is partially supported by NASA ADAP grants NNX16AF48G and NNX17AF39G and National Science Foundation under grants No. 1615105, 1615109, and 1653300.

# Kinematic model of the central molecular gas

We derive a model for the velocity of the disk component from the CO(1–0) observations using the kinematic fitting tool `diskfit` (cite: 2007ApJ...664..204S; 2010MNRAS.404.1733S; 2015arXiv150907120S). As mentioned in section [3.1](#subsection: ppV separation), these models benefit from large area which is why we base them on the CO(1–0) observations. A $20\sigma$ threshold ensures that the model is fitted to the bright disk excluding any fainter outflows.

In `diskfit`, we fit using the velocity field fitter. The names of the set options in `diskfit` are given in paratheses in the following. The model is fitted to all pixels within an ellipse of $75\ensuremath{''}$ major axis length (`regrad`), $\mathrm{PA} = 53^\circ$ (`regpa`) and ellipticity $\epsilon = 0.66$ (`regeps`). Outside this range, we use a sampling factor of 2 pixels (`istepout`). During the fit, the center is held fixed while we fit for disk position angle and ellipticity with initial guesses of $\mathrm{PA} = 53^\circ$ and $\epsilon = 0.66$ based on by eye inspection (line 9 and 10 of the parameter file). We allow the model to fit for non-axisymmetric flows with $\mathrm{PA} = 78^\circ$ initial guess and order $m=2$ (line 12) which means `diskfit` will fit for rotation plus a bisymmetric model with $m=2$ perturbations to the potential (bar). As the CO(1–0) data cover the kinematic center we set the inner interpolation toggle to true which assumes the velocity raises linearly within the innermost fitted ring. We do not fit for radial flows (radial flows toggle) because it allows to many degrees of freedom and produces bad models as is warned about in the `diskfit` manual. We further fit for the systemic velocity and exclude warps from the model. A model with these parameters is fitted in rings at radii $12.5\ensuremath{''}$, $25\ensuremath{''}$, $37.5\ensuremath{''}$, $50\ensuremath{''}$, $62.5\ensuremath{''}$, $75\ensuremath{''}$, $87.5\ensuremath{''}$, $100\ensuremath{''}$, $125\ensuremath{''}$, $150\ensuremath{''}$, $175\ensuremath{''}$, $200\ensuremath{''}$, $225\ensuremath{''}$, $250\ensuremath{''}$, $275\ensuremath{''}$ and $300\ensuremath{''}$.

The residuals show a slight mismatch in velocity of $\sim 20-30$ km s$^{-1}$ along the direction of the bar. This is likely due to the bar being underestimated because the CO(1–0) image covers only the inner half of the total extent of the bar. The mismatch gets larger when fitting a model to the smaller images of CO(2–1) and (3–2) which confirms that it is caused by lack of observed area. We fit this mismatch in the velocity field with an additional 2D Gaussian component and add it to the velocity field of the diskfit model to obtain a better model. Note that this additional component is not physically motivated or meaningful but purely aims to counteract the effect of limited observation area.

Figure [10](#figure: model) shows the velocity field of the model in comparison to the input CO(1–0) velocity field. The model typically fits the observed velocity field better than $\pm 25$ km s$^{-1}$; larger deviations occur mostly over small areas of order one beam size. The model thus successfully reproduces the large scale velocity field.

![image](figA1a.pdf) ![image](figA1b.pdf)\
![image](figA1c.pdf) ![image](figA1d.pdf)

# Velocity width of the disk mask

The definition of the disk mask is crucial for this analysis as it determines if a molecular cloud is considered kinematically consistent with the disk or if it is potentially outflowing. The position of the disk mask in ppV space is set by the disk model but the width (velocity range $\Delta v$) of the mask is a free parameter. From figure [12](#figure: all pV diagrams) it is obvious that $\Delta v$ depends on the distance from the major axis which is most simply accounted for by a parametrisation of form $\Delta v = a \exp \left( -\left( \frac{x}{b} \right)^2 \right) +c$. Finding the best fit values for $a, b$ and $c$ is difficult to do mathematically as the fit would need to be on the disk component that we want to determine from the mask first. We therefore select values that visually fit the pV diagrams as best as possible. They are given in equation [\[equation: delta v\]](#equation: delta v).

Figure [11](#figure: disk mask width) shows five alternative masks that vary only in width by 10% from the best fit mask. It is apparent that even slight changes of 10% deteriorate the fit between mask and disk emission. More narrow masks obviously do not cover all disk emission whereas the wider masks include spike features that are kinematically inconsistent with disk rotation.

![](figB1.pdf)

The effect of a $^{+10}_{-10}$% ($^{+0.04}_{-0.04}$ dex) variation in mask velocity width results in a $^{+0.01}_{-0.01}$ dex change in integrated disk luminosity for CO(1–0), CO(2–1) and CO(3–2). The non-disk components is less bright than the disk and thus shows a higher relative variation when changing the mask width: luminosities vary by $^{-0.07}_{+0.08}$ dex ($^{-0.06}_{+0.07}$ dex, $^{-0.11}_{+0.12}$ dex) for CO(1–0) (CO(2–1), CO(3–2)). Note the inverse scaling between disk and non-disk due to shifting the balance between the two components for a constant total luminosity. To first order, the same percentage changes apply to the further quantities mass, outflow rate, energy and momentum.

# Disk/non-disk separation: Position-velocity diagrams

Figure [12](#figure: all pV diagrams) shows all pV diagrams for the slices defined in figure [4](#figure: slice positions). For the discussion of these diagrams, see section [3](#section: disk separation).

![](figC1a.pdf)

![](figC1b.pdf)

natexlab

(ref: 2017ApJ...849...81A) Ando, R., Nakanishi, K., Kohno, K., et al. 2017, The Astrophysical Journal, 849, 81

(ref: 2015MNRAS.450L..80B) Bendo, G. J., Beswick, R. J., D’Cruze, M. J., et al. 2015, Monthly Notices of the Royal Astronomical Society: Letters, 450, L80

(ref: 2013Natur.499..450B) Bolatto, A. D., Warren, S. R., Leroy, A. K., et al. 2013, Nature, 499, 450

(ref: Chisholm:2017bu) Chisholm, J., Tremonti, C. A., Leitherer, C., & Chen, Y. 2017, Monthly Notices of the Royal Astronomical Society, 469, 4831

(ref: Christensen:2018ka) Christensen, C. R., Davé, R., Brooks, A., Quinn, T., & Shen, S. 2018, The Astrophysical Journal, 867, 142

(ref: Collaboration:2013cd) Collaboration, A., Robitaille, T. P., Tollerud, E. J., et al. 2013, Astronomy & Astrophysics, 558, A33

(ref: Collaboration:2018ji) Collaboration, A., Price-Whelan, A. M., Sipőcz, B. M., et al. 2018, The Astronomical Journal, 156, 123

(ref: 1986ApJ...303...39D) Dekel, A., & Silk, J. 1986, Astrophysical Journal, 303, 39

(ref: Engelbracht:1998cj) Engelbracht, C. W., Rieke, M. J., Rieke, G. H., Kelly, D. M., & Achtermann, J. M. 1998, The Astrophysical Journal, 505, 639

(ref: 2006ApJ...642L.127E) Engelbracht, C. W., Kundurthy, P., Gordon, K. D., et al. 2006, The Astrophysical Journal, 642, L127

(ref: 2000ApJS..129..493H) Heckman, T. M., Lehnert, M. D., Strickland, D. K., & Armus, L. 2000, The Astrophysical Journal Supplement Series, 129, 493

(ref: 2016MNRAS.457.2675H) Henshaw, J. D., Longmore, S. N., Kruijssen, J. M. D., et al. 2016, Monthly Notices of the Royal Astronomical Society, 457, 2675

(ref: 2005ApJ...619L..99H) Hoopes, C. G., Heckman, T. M., Strickland, D. K., et al. 2005, The Astrophysical Journal, 619, L99

(ref: Hopkins:2012ez) Hopkins, P. F., Quataert, E., & Murray, N. 2012, Monthly Notices of the Royal Astronomical Society, 421, 3522

(ref: Kim:2015iy) Kim, C.-G., & Ostriker, E. C. 2015, The Astrophysical Journal, 802, 99

(ref: 2018ApJ...853..173K) —. 2018, The Astrophysical Journal, 853, 173

(ref: Kornei:2009ee) Kornei, K. A., & McCrady, N. 2009, The Astrophysical Journal, 697, 1180

(ref: 2015MNRAS.453..739K) Krumholz, M. R., & Kruijssen, J. M. D. 2015, Monthly Notices of the Royal Astronomical Society, 453, 739

(ref: 2017MNRAS.466.1213K) Krumholz, M. R., Kruijssen, J. M. D., & Crocker, R. M. 2017, Monthly Notices of the Royal Astronomical Society, 466, 1213

(ref: Leitherer:1999jt) Leitherer, C., Schaerer, D., Goldader, J. D., et al. 1999, The Astrophysical Journal Supplement Series, 123, 3

(ref: Leroy:2015ds) Leroy, A. K., Bolatto, A. D., Ostriker, E. C., et al. 2015a, The Astrophysical Journal, 801, 25

(ref: 2015ApJ...814...83L) Leroy, A. K., Walter, F., Martini, P., et al. 2015b, The Astrophysical Journal, 814, 83

(ref: 2018ApJ...869..126L) Leroy, A. K., Bolatto, A. D., Ostriker, E. C., et al. 2018, The Astrophysical Journal, 869, 126

(ref: Lucero:2015if) Lucero, D. M., Carignan, C., Elson, E. C., et al. 2015, Monthly Notices of the Royal Astronomical Society, 450, 3935

(ref: 2018ApJ...857..116M) Ma, C., de Grijs, R., & Ho, L. C. 2018, The Astrophysical Journal, 857, 116

(ref: 2019ApJ...871..170M) Mangum, J. G., Ginsburg, A. G., Henkel, C., et al. 2019, The Astrophysical Journal, 871, 170

(ref: 2009ApJ...701.1636M) Matsubayashi, K., Sugai, H., Hattori, T., et al. 2009, The Astrophysical Journal, 701, 1636

(ref: 1996A&A...305..421M) Mauersberger, R., Henkel, C., Wielebinski, R., Wiklind, T., & Reuter, H. P. 1996, Astronomy & Astrophysics, 305, 421

(ref: McMullin:2007tj) McMullin, J. P., Waters, B., Schiebel, D., Young, W., & Golap, K. 2007, Astronomical Data Analysis Software and Systems XVI, 376, 127

(ref: 2015ApJ...801...63M) Meier, D. S., Walter, F., Bolatto, A. D., et al. 2015, The Astrophysical Journal, 801, 63

(ref: MullerSanchez:2010dr) Müller-Sánchez, F., González-Martı́n, O., Fernández-Ontiveros, J. A., Acosta-Pulido, J. A., & Prieto, M. A. 2010, The Astrophysical Journal, 716, 1166

(ref: Murray:2005jt) Murray, N., Quataert, E., & Thompson, T. A. 2005, The Astrophysical Journal, 618, 569

(ref: Oppenheimer:2006eq) Oppenheimer, B. D., & Davé, R. 2006, Monthly Notices of the Royal Astronomical Society, 373, 1265

(ref: 2010MNRAS.406.2325O) Oppenheimer, B. D., Davé, R., Kereš, D., et al. 2010, Monthly Notices of the Royal Astronomical Society, 406, 2325

(ref: Ott:2005il) Ott, J., Weiß, A., Henkel, C., & Walter, F. 2005, The Astrophysical Journal, 629, 767

(ref: 2004ApJ...611..835P) Paglione, T. A. D., Yam, O., Tosaki, T., & Jackson, J. M. 2004, The Astrophysical Journal, 611, 835

(ref: 2016A&A...594A..81P) Pereira-Santaella, M., Colina, L., Garcı́a-Burillo, S., et al. 2016, Astronomy & Astrophysics, 594, A81

(ref: 2018ApJ...860...23P) Pérez-Beaupuits, J. P., Güsten, R., Harris, A., et al. 2018, The Astrophysical Journal, 860, 23

(ref: Rekola:2005ha) Rekola, R., Richer, M. G., McCall, M. L., et al. 2005, Monthly Notices of the Royal Astronomical Society, 361, 330

(ref: Rieke:1980hh) Rieke, G. H., Lebofsky, M. J., Thompson, R. I., Low, F. J., & Tokunaga, A. T. 1980, The Astrophysical Journal, 238, 24

(ref: Robitaille:2012wl) Robitaille, T., & Bressert, E. 2012, Astrophysics Source Code Library

(ref: 2010A&A...518L..66R) Roussel, H., Wilson, C. D., Vigroux, L., et al. 2010, Astronomy & Astrophysics, 518, L66

(ref: Sakamoto:2011et) Sakamoto, K., Mao, R.-Q., Matsushita, S., et al. 2011, The Astrophysical Journal, 735, 19

(ref: 2006ApJ...636..685S) Sakamoto, K., Ho, P. T. P., Iono, D., et al. 2006, The Astrophysical Journal, 636, 685

(ref: 2016ApJ...823...68S) Salak, D., Nakai, N., Hatakeyama, T., & Miyamoto, Y. 2016, The Astrophysical Journal, 823, 68

(ref: 2018ApJ...856...97S) Salak, D., Tomiyasu, Y., Nakai, N., et al. 2018, The Astrophysical Journal, 856, 97

(ref: 2010MNRAS.404.1733S) Sellwood, J. A., & Sánchez, R. Z. 2010, Monthly Notices of the Royal Astronomical Society, 404, 1733

(ref: 2015arXiv150907120S) Sellwood, J. A., & Spekkens, K. 2015, arXiv.org, arXiv:1509.07120

(ref: Shapiro:1976ha) Shapiro, P. R., & Field, G. B. 1976, The Astrophysical Journal, 205, 762

(ref: Sharp:2010jl) Sharp, R. G., & Bland-Hawthorn, J. 2010, The Astrophysical Journal, 711, 818

(ref: 2018MNRAS.481....2S) Sormani, M. C., Sobacchi, E., Fragkoudi, F., et al. 2018, Monthly Notices of the Royal Astronomical Society, 481, 2

(ref: 2007ApJ...664..204S) Spekkens, K., & Sellwood, J. A. 2007, The Astrophysical Journal, 664, 204

(ref: 2007ApJ...658..258S) Strickland, D. K., & Heckman, T. M. 2007, The Astrophysical Journal, 658, 258

(ref: Strickland:2000wd) Strickland, D. K., Heckman, T. M., Weaver, K. A., & Dahlem, M. 2000, American Astronomical Society, 5, 15.14

(ref: Strickland:2002kp) Strickland, D. K., Heckman, T. M., Weaver, K. A., Hoopes, C. G., & Dahlem, M. 2002, The Astrophysical Journal, 568, 689

(ref: Sturm:2011jb) Sturm, E., González-Alfonso, E., Veilleux, S., et al. 2011, The Astrophysical Journal Letters, 733, L16

(ref: 2019MNRAS.tmp..540T) Tollet, É., Cattaneo, A., Macciò, A. V., Dutton, A. A., & Kang, X. 2019, Monthly Notices of the Royal Astronomical Society, 485, 2511

(ref: Turner:1985iy) Turner, B. E. 1985, Astrophysical Journal, 299, 312

(ref: 2009ApJ...700L.149V) Veilleux, S., Rupke, D. S. N., & Swaters, R. 2009, The Astrophysical Journal Letters, 700, L149

(ref: 2002ApJ...580L..21W) Walter, F., Weiß, A., & Scoville, N. 2002, The Astrophysical Journal, 580, L21

(ref: 2017ApJ...835..265W) Walter, F., Bolatto, A. D., Leroy, A. K., et al. 2017, The Astrophysical Journal, 835, 265

(ref: 2009ApJ...696..192W) Westmoquette, M. S., Smith, L. J., Gallagher, J. S. I., et al. 2009, The Astrophysical Journal, 696, 192

(ref: Westmoquette:2011bp) Westmoquette, M. S., Smith, L. J., & Gallagher III, J. S. 2011, Monthly Notices of the Royal Astronomical Society, 414, 3719

(ref: 2018ApJ...867..111Z) Zschaechner, L. K., Bolatto, A. D., Walter, F., et al. 2018, The Astrophysical Journal, 867, 111

[^1]: The term *streamer* here denotes structures with a high aspect ratio that are typically oriented roughly perpendicular to the disk and often show a velocity gradient.

[^2]: For details see NAASC memo 117 by the North American ALMA Science Center (NAASC) at <http://library.nrao.edu/public/memos/naasc/NAASC_117.pdf>.

[^3]: adjusting from the distance $\mathrm{D} = 2.5$ pc used by (cite: 1996A&A...305..421M) to the $\mathrm{D} = 3.5$ pc assumed here

[^4]: We follow IAU resolution B2 that defines the bolometric magnitude in absolute terms and eliminates the dependence on the variable magnitude of the sun.

[^5]: Assuming a Salpeter-like IMF ($\alpha=2.35$, mass range $0.1-100$ M$_\odot$, $\mathrm{Z} = 0.008$). The usual uncertainties related to the shape, upper mass cutoff and influence of binary stars apply.

</paper>

## Items to check

```json
[
 {
  "path": "analysis_steps[1].method.evidence[0]",
  "value": "diskfit velocity-field fit (rotation plus m=2 bar) to CO(1-0) first-moment map masked at 20 sigma, plus a 2D Gaussian residual correction",
  "failed_quote": "we fit for rotation plus a bisymmetric model with $m=2$ perturbations to the potential (bar)"
 },
 {
  "path": "analysis_steps[1].fitting.evidence[0]",
  "value": "diskfit least-squares",
  "failed_quote": "(no quote given)"
 }
]
```
