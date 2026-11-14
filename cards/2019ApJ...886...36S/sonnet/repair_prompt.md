# Repair task for a Claude Code subagent

A methods card has evidence quotes that were not found verbatim in the paper. Below are the rules, the paper, and the failing items. Write ONE JSON object, nothing else, of the form {"repairs": [{"path": ..., "found": true|false, "loc": ..., "quote": ...}, ...]} with one entry per item (path unchanged) to:

    C:\Users\adama\alma-corpus\cards\2019ApJ...886...36S\sonnet\repair_reply.txt

Use the Write tool for that file. Copy each quote character for character from the paper text below; a returned quote is checked mechanically and dropped if it is not in the paper. Do not read any other file, do not run commands, and do not change anything else. Reply with one line when done.

---

## Rules

You check evidence quotes for a methods card extracted from an astronomy paper. Some quotes could not be found verbatim in the paper text, and some stated values came without a quote. For each item: find the passage in the paper that supports the value and copy it VERBATIM (same words and order, at most 40 words; LaTeX markup may be dropped) with its loc (section heading, "abstract", "Table N" or "Figure N caption"). If the paper does not support the value, return found = false and leave quote and loc empty. Use only the paper text. Return one entry per item, with the item's path unchanged.

## Paper

<paper>
#  ALMA observations of fragmentation, sub-structure, and protostars in high-mass starless clump candidates

## Abstract

The initial physical conditions of high-mass stars and protoclusters remain poorly characterized. To this end we present the first targeted ALMA Band 6 1.3 mm continuum and spectral line survey towards high-mass starless clump candidates, selecting a sample of 12 of the most massive candidates ($\SI{4e2}{\ensuremath{
    \mathit{M}_\odot
}} \lesssim M_\mathrm{cl} \lesssim \SI{4e3}{\ensuremath{
    \mathit{M}_\odot
}}$) within $d_\odot < \SI{5}{kpc}$. The joint $12+\SI{7}{m}$ array maps have a high spatial resolution of $\lesssim \SI{3000}{au}$ (0.015 pc, $\theta_\mathrm{syn} \approx 0.8\ensuremath{''}$) and have high point source mass-completeness down to $M \approx \SI{0.3}{\ensuremath{
    \mathit{M}_\odot
}}$ at $6\ensuremath{
    \sigma_\mathrm{rms}
}$ (or $1\ensuremath{
    \sigma_\mathrm{rms}
}$ column density sensitivity of $N = \SI{1.1e22}{cm^{-2}}$). We discover previously undetected signposts of low-luminosity star formation from $J=2\rightarrow1$ and $J=5\rightarrow4$ bipolar outflows towards 11 out of 12 clumps, showing that current MIR/FIR Galactic Plane surveys are incomplete to low- and intermediate-mass protostars ($\ensuremath{
    \mathit{L}_\mathrm{bol}
}\lesssim \SI{50}{\ensuremath{
    \mathit{L}_\odot
}}$), and emphasizing the necessity of high-resolution followup. We compare a subset of the observed cores with a suite of radiative transfer models of starless cores. We find a high-mass starless core candidate with a model-derived mass consistent with $29^{52}_{15} \, \ensuremath{
    \mathit{M}_\odot
}$ when integrated over size scales of $R < \SI{2e4}{au}$. Unresolved cores are poorly fit by radiative transfer models of externally heated Plummer density profiles, supporting the interpretation they are protostellar even without detection of outflows. A high degree of fragmentation with rich sub-structure is observed towards 10 out of 12 clumps. We extract sources from the maps using a dendrogram to study the characteristic fragmentation length scale. Nearest neighbor separations when corrected for projection with Monte Carlo random sampling are consistent with being equal to the clump average thermal Jeans length ($\lambda_\mathrm{j,th}$; i.e., separations equal to $0.4-1.6\times\ensuremath{
    \lambda_\mathrm{j,th}
}$). In context of previous observations that on larger scales see separations consistent with the turbulent Jeans length or the cylindrical thermal Jeans scale ($\approx 3-4\times\ensuremath{
    \lambda_\mathrm{j,th}
}$), our findings support a hierarchical fragmentation process, where the highest density regions are not strongly supported against thermal gravitational fragmentation by turbulence or magnetic fields.

# Introduction

High-mass stars ($M_* > \SI{8}{\ensuremath{
    \mathit{M}_\odot
}}$) strongly influence the evolution of galaxies and the ISM, yet many fundamental questions remain to be answered concerning the incipient phases of high-mass star formation (cite: beuther07; tan14; motte17). Observational constraints on the initial physical conditions of protocluster evolution are a necessary prerequisite to improved understanding of high-mass star and cluster formation. Of particular importance are observations of the quiescent environments before the initial conditions are disrupted by the extreme radiative and mechanical feedback of high-mass stars. Thus our understanding of both how cluster formation is initiated and the ensuing protocluster evolution depend on identifying and constraining the physical properties of representative samples of starless molecular cloud “clumps”[^1].

Recent blind surveys of dust continuum emission at (sub-)millimeter and far-infrared (FIR) wavelengths of the Galactic Plane have identified large statistical samples of clumps, enabling the discovery of those in the earliest evolutionary phases. Such surveys include the Bolocam Galactic Plane Survey[^2] (cite: aguirre11; rosolowsky10; ginsburg13) at 1.1 mm, ATLASGAL[^3] at 870 μm (cite: schuller09; contreras13; csengeri14), JCMT Galactic Plane Survey[^4] at 850 μm (cite: eden17), and *Herschel* Hi-GAL at 70, 160, 250, 350, and 500 μm (cite: molinari10; molinari16a). Starless clump candidates (SCCs) are identified by cross-matching clump catalogs to catalogs of star formation indicators and selecting clumps unassociated with any indicators. These indicators include 70 μm compact sources, color-selected young stellar objects (YSOs), and masers, and UCHII  regions in (cite: svoboda16) for the BGPS and in (cite: yuan17) for ATLASGAL, in total identifying more than $\gtrsim \num{2e3}$ SCCs in the inner-Galaxy. In addition, more than $\gtrsim \num{e4}$ clumps without 70 μm sources have been identified from the Hi-GAL survey (cite: traficante15; elia17). In this study we aim to systematically study a representative sample of the highest mass SCCs within 5 kpc in order to understand the fragmentation characteristics at high-spatial resolution, identify potential high-mass starless cores ($M \gtrsim \SI{30}{\ensuremath{
    \mathit{M}_\odot
}}$, $R \lesssim \SI{0.1}{pc}$), and search for previously undetected low luminosity protostellar activity.

A variety of physics, including thermal gas pressure, turbulence, magnetic fields, and the geometry of filaments and density gradients, likely play a role in the fragmentation of molecular clouds and the resultant dense core populations. Recent high-resolution observations with millimeter and sub-millimeter interferometers of high-mass clumps with little sign of star formation reveal significant fragmentation at the early stage of cluster formation (cite: zhang09; zhang11; wangk11; wangk12; wangk14; zhang15; lu15b; beuther15b; sanhueza17). These studies found that the most massive fragments in the clumps are at least ten times greater than the thermal Jeans mass, indicating that additional support from turbulence and/or magnetic fields are required. Most of these studies focused on individual clumps and typically have not had the sensitivity to adequately detect fragments of a thermal Jeans mass (detections of $\gtrsim \! \SI{2}{\ensuremath{
    \mathit{M}_\odot
}}$ at $4\ensuremath{
    \sigma_\mathrm{rms}
}$). In contrast, the fragmentation scales in nearby molecular clouds have been studied extensively with recent notable analyses towards Serpens (cite: friesen17), Orion Integral Shaped Filament (cite: kainulainen17a), and Perseus (cite: pokhrel18). These studies find support for hierarchical, scale-dependent fragmentation with separations corresponding to a range between thermal Jeans fragmentation and thermal filamentary gravitational fragmentation. It is not understood how these results extend towards earlier evolutionary stages in massive SCCs which are the focus of this work.

Publicly available millimeter and FIR Galactic Plane survey observations do not have sufficient angular resolution at $\sim \! 20-30\ensuremath{''}$ ($\sim \! \SI{0.5}{pc}$ at $\SI{4}{kpc}$) to study the sub-structure and dense core properties in distant SCCs. The high-mass pre-stellar core candidate G028-C1S ($M_\mathrm{c} \sim \SI{60}{\ensuremath{
    \mathit{M}_\odot
}}$) studied in (cite: tan13) for example was only identified as protostellar until interferometric followup of outflow tracers (cite: tan16; feng16). High-mass SCCs remain largely unstudied at high-spatial resolution owing to their historical difficulty in identification and typically large heliocentric distances, with only a handful of studies on individual objects to date (cite: beuther15a; sanhueza17). In particular the high-mass starless clump candidate “MM1” of IRDC G28.23–0.19 (cite: sanhueza13) has been studied in detail to determine that it is devoid of star formation indicators, including $3.6-\SI{70}{\um}$ point sources, $\mathrm{H_2O}$ and $\mathrm{CH_3OH}$ masers (cite: wangy06; chambers09), and radio continuum (cite: battersby10; rosero16). The global physical properties of G28.23–0.19 MM1 (corresponding to BGPS catalog clump number 4649) are similar to the average properties of the SCCs presented in this work. G28.23–0.19 MM1 is high-mass, cold, compact, and dense (i.e., $M_\mathrm{cl} \approx \SI{1.5e3}{\ensuremath{
    \mathit{M}_\odot
}}$, $T_\mathrm{K} \approx \SI{12}{K}$, $R = \SI{0.6}{pc}$, $n \approx \SI{3e4}{cm^{-3}}$; (cite: sanhueza17) (cite: sanhueza17)). However the sensitivity and sample size of dense cores are not sufficient for a precise measurement of the fragmentation scale, and represents only a single clump. In this survey we present observations on a sample of $12$ clumps that are selected from a blind Galactic Plane survey and are among the most massive SCCs.

Existing large samples of SCCs have been primarily identified through the non-detection of coincident Hi-GAL 70 μm sources (cite: veneziani13; traficante15; svoboda16; elia17) which is less affected than shorter wavelength 8 μm or 24 μm observations by both local extinction and from contamination of evolved stars (principally those on the asympototic giant branch). The completeness of the 70 μm maps to protostar bolometric luminosity, $L_\mathrm{bol}$, is affected by the survey depth and complex structure in the foreground and background emission which hinders the clear identification of compact sources. (cite: svoboda16) calculate the $L_\mathrm{bol}$ completeness function for Hi-GAL 70 μm compact sources associated to BGPS clumps and the respective distribution of heliocentric distances and find that for clumps with low 70 μm backgrounds ($\sim \! 500 - \SI{1000}{MJy.sr^{-1}}$) the $90\%$ completeness limit is $L_\mathrm{bol} = \SI{50}{\ensuremath{
    \mathit{L}_\odot
}}$ (cite: svoboda16), which is greater than $\gtrsim 95\%$ of YSOs in the Gould’s Belt (cite: dunham14). Faint 24 μm sources coincident with the clump column density peaks towards $9/18$ of 70 μm dark SCCs suggest likely embedded intermediate-mass star formation that is undetected in the Hi-GAL observations (cite: traficante17). However, it is currently unknown what degree of star formation has initiated, if at all, in SCCs without sensitive and unambiguous tracers of protostellar activity such as bipolar molecular outflows. Systematic observations of SCCs at high-resolution are necessary to determine what degree (if any) of low-luminosity star formation has begun in SCCs, with important implications for the protostellar accretion history.

The principal theories of high-mass star formation in dense Galactic molecular cloud clumps are the monolithic collapse of turbulent cores in virial equilibrium (cite: mckee02; mckee03; hosokawa09) and the accretion of sub-virial cores through gravitionally-driven cloud inflow (cite: smithr09; hartmann12). The latter replace the competitive Bondi-Hoyle accretion of cores (cite: bonnell01; wangp10) with cores fed the gas reservoir through inflowing streams. The turbulent core model predicts monolithic high-mass starless cores whereas the competitive model predicts a fragmentation of cores near the thermal Jeans mass. The existence of high-mass starless cores is a key distinction between these models, yet few, if any, observational candidates are known (cite: kong17), and some promising candidates have revealed embedded protostellar activity upon further observational investigation (cite: tan13; tan16; feng16b). Irrespective of the specific theoretical model, measurements of the fragmentation properties at early evolutionary phases provide valuable observational constraints on the initial physical conditions of high-mass star and cluster formation. To this end, we perform a systematic search for high-mass starless cores towards massive SCCs with the Atacama Large Millimeter/submillimeter Array.

In this paper we present a systematic survey of $12$ high-mass SCCs at sub-arcsecond resolution. We present our sample selection, observational setup, and data reduction methodology in Section [2](#sec:Obs). We describe detections of previously unknown, low-luminosity protostellar activity in Section [3](#sec:Activity) and the modeling of continuum sources in Section [4](#sec:Modeling). We measure and analyze the fragmentation scale between sources in Section [5](#sec:FragmentationScale), discuss the implications in Section [6](#sec:Discussion), and report our conclusions in Section [7](#sec:Conclusions). In Appendix [11](#apx:Models) we include a detailed description of the setup and computation of radiative transfer models analyzed in Section [4](#sec:Modeling).

# Observations

## Sample Selection

We have identified SCCs through the combined catalogs and images of primarily two dust continuum Galactic Plane surveys: (1) an evolutionary analysis of BGPS 1.1 mm (cite: svoboda16), and (2) comparison of the (cite: peretto09) infrared dark cloud (IRDC) catalog with Hi-GAL images (cite: traficante15). The BGPS observed between $\ang{-10} < \ell < \ang{90}$ with $|b| < \ang{0.5}$ (expanding to $|b| < \ang{1.5}$ for selected $\ell$) at $\lambda_{\rm c} = \SI{1.12}{mm}$ with a $\theta_\mathrm{hpbw} = 33\ensuremath{''}$ synthesized angular resolution. In the region $\ang{10} < \ell < \ang{65}$ the BGPS has been compared to a diverse set of a observational indicators for star formation activity (). These indicators include compact 70 μm sources, mid-IR color-selected YSOs, masers, Class II masers, extended 4.5 μm outflows, and UCHII regions. From the sample of more than $2500$ SCCs in the combined samples of and (cite: traficante15), we target the $12$ highest mass SCCs within $d_\odot < \SI{5}{kpc}$. Point sources at 70 μm were identified by visual inspection in and by an automated extraction in (cite: traficante15). Three clumps (G28565, G29601, and G309120 which were initially determined from the automated extraction to be dark at 70 μm, upon closer scrutiny by visual inspection show association to weak sources. Among the 12 ALMA targets, nine have no detectable point source emission from Hi-GAL 70 μm (flag 0 in ), two have low-confidence or marginal detections (flag 4, G28565 & G29601), and one has bright, compact detection (flag 1, source G30912). We emphasize that starless clump candidates are designated based on the observational data sets and identification techniques used, and that these factors are reflected in the completeness and purity of the resulting catalogs of SCCs. Table [1](#tab:TargetPositions) details the target positions and velocities. Table [2](#tab:PhysicalProperties) details the physical properties of the sample and Figure [1](#fig:IrMosaic) shows images of the clumps at wavelengths from 8 μm to 350 μm.

![](fig_group_both_fir2_mosaic_blank.pdf)

The clump average physical properties in are shown in Figure [2](#fig:Tanogram), plotting peak mass surface density $\Sigma_\mathrm{cl,pk}$ (at $\theta_\mathrm{hpbw} = 33\ensuremath{''}$) and total mass $M_\mathrm{cl}$, for sources with well-constrained distances less than $d_\odot < \SI{5}{kpc}$ and $\ang{10} < \ell < \ang{65}$. Protostellar clumps and SCCs are plotted, where SCCs have quiescent background emission and no detected compact sources from the Hi-GAL 70 μm images (flag 0, see §3.2.4). Protostellar clumps are typically higher in both mass and mass surface density compared to SCCs. The ALMA targets are shown, occupying the highest $\Sigma_\mathrm{cl,pk}$ and $\ensuremath{
    M_\mathrm{cl}
}$ portions of the SCC distribution where typical values for the sample are $\ensuremath{
    M_\mathrm{cl}
}\sim \SI{800}{\ensuremath{
    \mathit{M}_\odot
}}$ and $\Sigma_\mathrm{cl,pk} \sim \SI{0.1}{g.cm^{-2}}$ (measured over $\sim \! \SI{0.6}{pc}$ scales). G28539 in particular stands out as the most massive clump in the sample at $\ensuremath{
    M_\mathrm{cl}
}\sim \SI{3e3}{\ensuremath{
    \mathit{M}_\odot
}}$ and also the highest peak mass surface density.

Assuming a star-formation efficiency of $\epsilon_\mathrm{sf} = 0.3$ and a standard stellar initial mass function (cite: kroupa01), a 320 $\mathit{M}_\odot$ clump meets the criteria of forming a 8 $\mathit{M}_\odot$ star (see §6.1). All of the clumps that comprise this sample are above this mass threshold, and are similarly above the mass-radius relationship for high-mass star formation proposed by (cite: kauffmann10)[^5]. However in practice it is difficult to assess the high-mass star formation potential of clumps beyond these simple heuristics. It should be kept in mind that if the star formation efficiency of the targets is substantially lower than the typical assumed value of $\epsilon_\mathrm{sf} = 0.3$ then they are unlikely to form high-mass stars.

![](fig_tanogram_annotated.pdf)

## ALMA Band 6

As part of Atacama Large Millimeter/submillimeter Array[^6] (ALMA) Cycle 3 program 2015.1.00959.S, we observed 12 clumps in Band 6 in a compact configuration (C36-2; joint $12+\SI{7}{m}$ array baselines range from $\sim \! 9 - \SI{450}{m}$). Data were taken between $3-20$ March, 2016, for the 12 m array and between 30 April to 19 August, 2016, for the 7 m array. Including time for calibration and overheads, the 12 m array observations lasted for approximately 12 hr, with typical precipitable water vapor of 1.5 mm. Titan and J1733–1304 were used as flux calibrators, J1751+0939 to calibrate the bandpass, and J1743–0350 and J1830+0619 to calibrate the time-dependent gains. Identical 1 hr scheduling blocks were configured to interleave and observe all 12 targets within the same block, and because sources are within a 5° radius on the sky ($22.7\ensuremath{^\circ} < \ell < 30.9\ensuremath{^\circ}$), the same calibrators can be used. Thus due to nearly identical observing conditions, the individual maps have similar $uv$-coverage, atmospheric noise, and beam size.

Positions for the sample were chosen from the BGPS 1.1 mm continuum peak flux density position, and compared for consistency with the ATLASGAL 870 μm peak emission and Hi-GAL 70 μm peak absorption (when present) positions. The Band 6 receiver was configured in dual-polarization mode with lower and upper sidebands centered near 215 and 230 GHz, respectively. The observations targeted each clump peak with a single pointing with half-power beam width (HPBW) of the measured primary beam $26.6\ensuremath{''}$ ($\sim \! \SI{0.5}{pc}$ at $d_\odot = \SI{4}{kpc}$) and 20%-power beam width of $40\ensuremath{''}$ ($\sim \! \SI{0.8}{pc}$), the effective limit of the 12 m array field of view.

### ALMA 1.3 mm continuum reduction

Data reduction was performed using `CASA`  (version 4.7.134-DEV, r38011, for consistency with QA2 delivered products). Line-free continuum visibilities were created by flagging channels contaminated by spectral lines, where the input spectral windows were further visually inspected to check for emission at unexpected velocity ranges, partitioned out into a new measurement set with the `split` task, and channel averaged to 25 MHz to avoid bandwidth smearing. Together, this yields $\approx \SI{3.5}{GHz}$ of dual polarization continuum bandwidth. The continuum image root mean square (RMS, $\ensuremath{
    \sigma_\mathrm{rms}
}= \sqrt{\sum_n I_n^2 / n}$) is measured for each CLEANed image within a region that excludes identified emission using the `casaviewer` tool. None of the images are dynamic range limited with peak image intensity divided by the RMS less than 200. We estimate the fiducial mass sensitivity given $T_\mathrm{K}(\ce{NH3}) \approx \SI{12}{K}$, thermally coupled gas and dust ($T_\mathrm{d}=T_\mathrm{K}$), and OH5 dust opacity $\kappa(\lambda = \SI{1.3}{mm}) = \SI{0.899}{cm^2.g^{-1}}$). The methods for deriving dust mass values from the continuum emission are discussed in more detail in §[4](#sec:Modeling). The joint $12+\SI{7}{m}$ continuum was then iteratively CLEANed with manual masking using the `tclean` task using the multiscale deconvolver and a robust weighting of 1, down to a brightness threshold of $2-3\ensuremath{
    \sigma_\mathrm{rms}
}$. An image cell size of $0.1\ensuremath{''}$ was used for all continuum and spectral line maps. Self-calibration was not applied because the brightest sources in the image are only a few mJy, and not sufficiently bright such that a conservative self-cal produces a noticeable improvement without also increasing the image noise. The resultant images have a synthesized beam size of $\theta_\mathrm{maj} \approx 0.85\ensuremath{''}$ by $\theta_\mathrm{min} \approx 0.75\ensuremath{''}$ ($0.8\ensuremath{''}$ angular diameter yields $2800-\SI{3800}{au}$ at $d_\odot=3.5-\SI{4.8}{kpc}$). The continuum images are shown in Figure [3](#fig:ContinuumTwelve).

### ALMA spectral line reduction

The flexibility of the ALMA correlator enabled simultaneous observation of several molecular line transitions. Table [3](#tab:Correlator) reports the details of the correlator configuration. We observed nine spectral windows (SPWs) with one wide-band, low-spectral resolution window centered at 233.8 GHz and eight high-spectral resolution windows centered on lines of interest. Table [4](#tab:LineList) reports the transition quantum numbers, rest frequencies, and upper energy levels ($E_\mathrm{u}/k$). The SPWs containing the and transitions have a spectral resolution of 0.34 km s $^{-1}$ and the other line SPWs have 0.68 km s $^{-1}$ resolution. Line rest frequencies were taken from a combination of the SLAIM[^7] (F. J. Lovas, private communication, (cite: slaim) (cite: slaim)) and the CDMS (cite: cdms) online spectroscopic databases. The line SPWs from the $12+\SI{7}{m}$ arrays were jointly imaged using the CASA task `tclean` with a Briggs robust parameter of $1.0$, cell size of $0.1\ensuremath{''}$, and re-gridded to common spectral resolutions listed in Table [4](#tab:LineList). We find a typical RMS noise levels in the image cubes of 1.8 mJy/( km s $^{-1}$ ) (i.e., 2.2 mJy per 0.68 km s $^{-1}$ channel or 3.0 mJy per 0.34 km s $^{-1}$ channel) or 71 mK/( km s $^{-1}$ ) when converted to brightness temperature units (HPBW beam size of $0.85\ensuremath{''}\times0.75\ensuremath{''}$).

In this work we inspect the line image cubes for detection of emission, and for the presence of outflows traced by and , but do not CLEAN the data cubes. Due to the lack of full $uv$-coverage, the CO maps in particular show strong effects of spatial filtering near the systematic velocities that make the deconvolution process complex and error prone. Detailed analysis of the spectral line data is left to a future work. Table [6](#tab:Detections) lists the detection flags per target for the continuum, molecular lines, and outflows. Features are considered detections if they have peak intensities $\geq 7\ensuremath{
    \sigma_\mathrm{rms}
}$ (“D”), weak detections if between $5 - 7\ensuremath{
    \sigma_\mathrm{rms}
}$ (“W”), and non-detections if $\leq 5\ensuremath{
    \sigma_\mathrm{rms}
}$. Targets that exhibit bipolar outflows in CO or SiO are flagged “B” (discussed below in §[3.2](#ssec:OutflowDetections)).

![](fig_T30912_joint_cont_mosaic_nopbcor_cb.pdf)

## Image fidelity and MIR comparison

The dense gas features revealed in the continuum maps clearly show hierarchical structure, with bright ridges, filaments, and cores contained within larger, lower surface brightness features. Given the complexity within the maps and the systematic uncertainties of imaging, we compare the continuum images to an additional measure of gas column density at comparable resolution, MIR extinction. For appropriate configurations of distance and the MIR radiation field, clumps can appear associated with 8 μm absorption features (EMAFs), where high column densities at close distances typically yield the strong MIR shadows that identify infrared dark clouds (IRDCs). MIR extinction mapping has the dual advantages of comparatively high-resolution, insensitivity to dust temperature, and lack of spatial filtering. We use the *Spitzer*  GLIMPSE (cite: benjamin03; churchwell09) IRAC Band 4 ($\lambda_{\rm c} = \SI{7.9}{\um}$, $2\ensuremath{''}$ FWHM) mosaic to show the EMAF contrast. Figure [4](#fig:EightMicronTau) presents a map of the flux density $S_8$ with the ALMA 230 GHz continuum for source G24051 overlaid. The dense gas structures observed in the millimeter continuum show a remarkable consistency when compared with the column density features inferred from the of MIR contrast. This holds similarly true for the other clumps in the sample, as all show at least some MIR extinction. Qualitatively this good correspondence supports the fidelity of the emission structure detected in the ALMA maps.

![](fig_tau_alma_comparison.pdf)

## Core identification and dendrogram

In order to analyze the fragmentation scale we first identify dense gas sub-structures using a segmentation algorithm. The nature of the tree data-structure in the dendrogram algorithm makes it well-suited to identifying and categorizing structure in images with hierarchical structure (cite: rosolowsky08b), as opposed to a simpler segmentation algorithms, such as that done with a seeded watershed algorithm (cite: williams94). We use the open source Python software library `astrodendro` to create the dendrogram and catalog of cores. The dendrogram has three principal tunable parameters, defining a minimum threshold value $v_\mathrm{min}$ setting the floor or outer boundary of each tree, the minimum contrast or step size $\delta_\mathrm{step}$ between nodes, and the minimum area $\Omega_\mathrm{min}$. Because the noise varies considerably across the primary beam of each image, we apply the dendrogram to maps that have *not* been corrected for the weight of the primary beam. This effectively works to identify features with outer contours of constant statistical significance across the field of view, rather than outer contours of constant flux. Sources are extracted out to the limit of the maps, set to the 20% power point of the primary beam. We choose conservative values for each parameter, using $v_\mathrm{min} = 3\ensuremath{
    \sigma_\mathrm{rms}
}$, $\delta_\mathrm{step} = 3\ensuremath{
    \sigma_\mathrm{rms}
}$, and $\Omega_\mathrm{min} = \Omega_\mathrm{bm}$, applied to the unmasked images. Sources (i.e. leaves, or nodes without children) are then sub-selected to meet the criteria that the peak flux is $>5\ensuremath{
    \sigma_\mathrm{rms}
}$. In total, we identify 67 sub-structures for the sample of 12 clumps. Figure [5](#fig:CorePositions) shows the dendrogram extracted dense gas sub-structures in each clump. Table [5](#tab:CoreProperties) catalogs the measured positions, sizes, and flux densities of the sub-structures. We find an average number of sub-structures per clump of $N_\mathrm{src}=5.6$ (median 6), with the maximum $N_\mathrm{src}=11$ in G24051 and minimum $N_\mathrm{src}=1$ in G23605. G23605 is the only clump with $N_\mathrm{src} < 3$ and is thus not included in the source nearest neighbor distance analysis. Figure [6](#fig:ClumpScatterSigma) presents $N_\mathrm{src}$ per clump versus $\Sigma_\mathrm{cl,pk}$, where a tentative increasing trend is observed, where clumps that have high $\Sigma_\mathrm{cl,pk}$ are more fragmented than lower $\Sigma_\mathrm{cl,pk}$.

![](fig_T30912_joint_cont_mosaic_core_pos_anno.pdf)

![](fig_nleaves_col_pk_md.pdf)

While in theory the distribution of integrated flux densities can be analyzed to measure a CMF, large observational uncertainties exist in practice that complicate its interpretation. The principal contributor arises from at least a factor of three uncertainty in $T_\mathrm{d} \sim 6-\SI{35}{K}$ ($\sim \! 10\times$ uncertainty in $M$), due to uncertainty in the ISRF, local extinction, and uncertainty in the protostellar activity of each source. From single wavelength observations we do not have enough information to construct spectral energy distributions (SEDs) and measure average line-of-sight dust temperatures. Other significant systematics also arise from uncertainty in the missing flux density due to spatial filtering by the interferometer, dust opacity ($\delta \kappa / \kappa \approx 50\%$), kinematic-derived heliocentric distance ($\delta d_\odot / d_\odot \approx 15\%$), and the aperture or source boundary used to extract $S_\nu$. For these reasons, we shall leave the study of the characteristic fragmentation mass and the CMF in SCCs to a future work utilizing complementary JVLA observations that will provide both gas kinetic temperature and kinematic information (Svoboda et al. *in prep.*). The characteristic fragmentation length scale, on the other hand, can be inferred directly from the distribution of angular separations between sources with assumptions on how to correct for geometric projection.

# Protostellar Activity

In this section we describe new evidence for protostellar activity, and in Sect. [5](#sec:FragmentationScale) we perform an analysis of the fragmentation scale from the sub-structure detected in the continuum. With the improved sensitivity and resolution of ALMA, multiple indicators of protostellar activity are observed for the first time. In particular bipolar molecular outflows detected in $J=2\rightarrow1$ and $J=5\rightarrow4$ provide unambiguous evidence of embedded protostellar activity. The detection of molecular transitions with comparatively high upper excitation temperatures ($E$- $4_{2,2} \rightarrow 3_{1,2}$, $\ensuremath{
    E_\mathrm{u}
}/ k = \SI{45.5}{K}$; p- $3_{2,2} \rightarrow 2_{2,1}$, $\ensuremath{
    E_\mathrm{u}
}/ k = \SI{68.1}{K}$) and detection of bright, compact continuum emission (unresolved on scales smaller than $\lesssim \SI{3000}{au}$) are also suggestive of embedded, low-$\ensuremath{
    \mathit{L}_\mathrm{bol}
}$ protostellar activity. Together, these data provide a clear indication of embedded protostars towards 11 out of 12 clumps.

## Compact continuum sources

Numerous high SNR (signal-to-noise ratio, $S_\nu/\ensuremath{
    \sigma_\mathrm{rms}
}$), point-like sources are observed in the continuum images (Figure [3](#fig:ContinuumTwelve)). We speculate such sources originate from the dense, centrally heated inner-envelopes of embedded protostars. In §[4](#sec:Modeling) we investigate whether the compact continuum sources are inconsistent with radiative transfer models of dense, starless cores.

We designate continuum sources as “compact“ if they are unresolved or are marginally resolved on the scale of the ALMA synthesized beam $\theta_\mathrm{syn} \approx 0.8\ensuremath{''}$. Continuum sources are determined to be unresolved if a Gaussian fit to the image plane data using the CASA task `imfit` reports an deconvolved angular sizes $\theta_\mathrm{dec} \lesssim \theta_\mathrm{syn}$. The deconvolved Gaussian FWHM are determined from subtracting the synthesized HPBW in quadrature from the fitted width, i.e. $\theta_\mathrm{dec} = \sqrt{\theta_\mathrm{fit}^2 - \theta_\mathrm{syn}^2}$. These angular widths correspond to physical sizes of $\lesssim\! \SI{1500}{au}$ at heliocentric distances of $d_\odot \approx \SI{4}{kpc}$. The brightest compact sources have typical peak flux densities between $S_\mathrm{1.3,pk} \approx 1-\SI{7}{\milli\jy\per\beam}$. All clumps aside from G28539 host a compact source with $S_\mathrm{1.3,pk} > \SI{1}{\milli\jy\per\beam}$. Indeed, sources G23605 and G30120 host compact sources, even though they show limited fragmentation otherwise. While lacking extended continuum emission, the compact source G23605 S1 in has clear association with emission from multiple molecular species (, , ) at the LSR velocity of the clump, determined from the emission (32″, 0.7 pc resolution; ). G30120 S1 is a compact source near the eastern edge of the field with a strong outflow and other molecular detections.

For comparison to nearby low-mass star forming regions, (cite: enoch11) carried out a survey of Class 0 YSOs in Serpens at 230 GHz with CARMA. The envelope masses range between $M_\mathrm{env} = 0.5 - \SI{20}{\ensuremath{
    \mathit{M}_\odot
}}$ (median $M_\mathrm{env} = \SI{3.7}{\ensuremath{
    \mathit{M}_\odot
}}$) and with integrated flux densities between $S_{1.3} = \num{1.4e1} - \SI{4.0e3}{mJy}$ (median $S_{1.3} = \SI{120}{mJy}$) and deconvolved size scales between $D = 400-\SI{3000}{au}$ (median $D \approx \SI{700}{au}$). With a heliocentric distance of $d_\odot = 415 \pm \SI{25}{pc}$ to Serpens (cite: dzib10), the 120 mJy median source flux density and 700 au size measured by (cite: enoch11) correspond to 1.2 mJy and $0.18\ensuremath{''}$ when scaled to a fiducial distance of 4 kpc. If there are low- to intermediate-mass Class 0 YSOs with similar physical properties in these SCCs as in Serpens, then they would be consistent with the observed bright ($\gtrsim 20\ensuremath{
    \sigma_\mathrm{rms}
}$) unresolved point continuum sources. This is further supported by the frequent coincidence of outflows towards such sources, discussed in section §[3.2](#ssec:OutflowDetections). To determine whether the observed compact continuum sources are consistent with starless cores ($\sim\! \SI{0.1}{pc}$) embedded within the mapped clumps ($\sim\! \SI{1}{pc}$), in §[4](#sec:Modeling) we compare a subset of the observations to radiative transfer models of starless cores.

Some continuum sources without molecular line detections may be background galaxies. Deep surveys performed with ALMA (cite: hatsukade13; carniani15) have determined source counts of background galaxies at 1.3 mm. The number of sources expected in the images with flux densities greater than $N(S_{1.3} > \SI{0.3}{mJy}) \lesssim 3$ over the 12 fields, measured as HPBW area for each pointing, outside of which the degraded sensitivity yields negligible background sources. This represents approximately $\lesssim \! 5\%$ of the detected sources, and thus does not have a significant effect on the calculation of the nearest neighbor separations or other estimated distributions of core properties.

## CO & SiO Outflows

Ordered, bipolar molecular outflows driven by protostellar accretion provide a sensitive and unambiguous detection of embedded protostellar activity (cite: arce07; frank14). In this section we describe the properties of outflows detected with ALMA in $J=2\rightarrow1$ and $J=5\rightarrow4$.

Outflows are identified through visual inspection of the datacubes in conjunction with the 1.3 mm maps overplotted. While the emission structures in the cubes are complex, bipolar outflows are clearly apparent as paired linear emission structures. These features are identified as linear features radiating from the same location with highly ordered red and blue velocity components that are detected over many velocity channels ($\gtrsim\! \SI{10}{km~s\ensuremath{^{-1}}}$, $\gtrsim\! 15$ channels). Outflow candidate features with only a single red or blue component are also observed, but due to the greater ambiguity in identification these are not regarded as clear signatures of star formation activity. The outflows are generally highly ordered in position and velocity, but spatial filtering of bright, extended emission and self-absorption near the source systemic velocity complicate the identification of low-velocity ($|v| \lesssim \SI{1.5}{km~s\ensuremath{^{-1}}}$) outflow components. Higher velocity components of the spectra also suffer both self-absorption from foreground clouds and confusion with bright Galactic emission, which can bias measurements of the maximum outflow velocity to lower values. Analysis of an example outflow in G24051 is presented in Appendix [9](#apx:PvDiagram).

We find that 9 out of 12 clumps are associated with bipolar outflows and 16 outflows in total are observed. We also find that 3 out of 12 clumps are associated with bipolar outflows and 4 outflows in total are observed. The clumps with outflows are reported in Table [6](#tab:Detections). Pairs of outflows originating from the same continuum source are also observed, as seen in G23297 S2 and G29601 S1, which point to unresolved protostellar multiple systems. Figure [7](#fig:CoOutflowMosaic) presents the ALMA joint $12+\SI{7}{m}$ array $J=2\rightarrow1$ integrated intensity maps for blue- and red-shifted velocity components.

![](fig_T30912_joint_co_outflow_mosaic_v2_cb.pdf)

We also detect emission towards several more continuum sources and positions without clear signs of ordered bipolar outflows. emission detection is a strong indicator of protostellar activity because of its origin in high-velocity shocks driven by protostellar outflows (cite: schilke97). However, recent work has shown that low-velocity shocks ($\lesssim\! \SI{10}{km~s\ensuremath{^{-1}}}$) created by colliding flows may produce substantial distributed emission (cite: jimenezserra10; luong13; louvet16). Thus, considered by itself, a detection of relatively narrow linewidth ($\Delta v \lesssim \SI{10}{km~s\ensuremath{^{-1}}}$) $J=5\rightarrow4$ emission is not an unambiguous indicator of star formation activity. Maps of integrated intensities are presented in Appendix [10](#apx:SiOOutflows).

## G28539, a true starless clump?

The 70 μm dark clump G28539 (upper-left corner of Fig. [3](#fig:ContinuumTwelve) & [7](#fig:CoOutflowMosaic)) shows no clear sign of or outflows, and thus remains a starless clump candidate at the improved sensitivity of ALMA. Several indirect tracers of star formation are observed towards G28539 however and we discuss these in turn.

Moderately high-excitation molecular lines ($E_\mathrm{u}/K \gtrsim \SI{50}{K}$) are unlikely to be excited in the cold 10 K gas expected to be found in starless cores and quiescent clump gas. Detection of such lines in our observations are thus indirect evidence of embedded protostars, although as discussed in §[3.2](#ssec:OutflowDetections) it is possible some of these lines are excited from low-velocity shocks originating from colliding flows. In G28539, a compact source of weak emission and $3_{2,2}\rightarrow2_{2,1}$ is detected. These features are not coincident with continuum emission and may originate from non-protostellar shocks, shocks of undetected protostellar outflows, or of embedded protostellar cores that are below our detection limit. Similarly, a compact source of is also detected does not coincide with any continuum emission feature (it may be seen on the west side of the field in Fig. [15](#fig:SiOOutflowMosaic)).

There exist weak 24 μm sources in the vicinity of the clump boundaries as defined by the 350 μm and 500 μm emission, notably a faint source within the extinction feature $\sim \! 1\ensuremath{'}$ east of the ALMA field (see 24 μm panel in Fig. [1](#fig:IrMosaic)), a brighter source on the south-eastern outskirt of the clump, and a marginal feature coincident with the continuum source in the NW edge of the ALMA field of view. Because of the substantial contamination from evolved stars, 24 μm emission alone is not a robust indicator of protostellar activity. If these sources are indeed protostars associated with the clump then they would be evidence that star formation has begun in G28539.

Deep radio continuum observations when available also provide a diagnostic of star formation activity because they are sensitive to the ionized gas in ultra- and hyper-compact HII regions, ionized winds, and jets from low- to intermediate-mass protostars. (cite: rosero16) carried out deep Jansky Very Large Array (JVLA) C & K-band observations towards a sample of high-mass clumps which contains source G28539 in the field “G28.53–00.25”. The HPBW of the primary beam for the JVLA at C-band is $9.2\ensuremath{'}$ at 4.2 GHz (LSB) and $4.2\ensuremath{'}$ at 7.4 GHz (USB), with synthesized HPBW resolution of approximately $\sim \! 0.4\ensuremath{''}$ in the A-configuration. Using the radio-continuum to bolometric luminosity scaling relations for protostars in (cite: shirley07) (Eq. 3), the measured $\ensuremath{
    \sigma_\mathrm{rms}
}= \SI{3}{\micro\jy\per\beam}$ sensitivity at $d_\odot = \SI{4.7}{kpc}$ can be converted to a $1\sigma$ bolometric luminosity sensitivity of $\sim \! 30 \, L_\odot$, that is reasonably comparable to the PACS 70 μm sensitivity from Hi-GAL. Here a faint point source is detected near the center of the ALMA pointing, detected in both side-bands at moderate significance (8 and $5\sigma$ in LSB, USB respectively). The measured in-band spectral index ($S \propto \nu^{\mathbf{+}\alpha}$) $\alpha = -0.65 \pm 0.46$ favors a non-thermal synchrotron dominated source, but the weak constraint is consistent with thermal free-free emission $\alpha = -0.1$ at $1.2\ensuremath{
    \sigma_\mathrm{rms}
}$. The location $18\ensuremath{^\circ} 44\ensuremath{'} 22.621\ensuremath{''}$ $-4^\mathrm{h} 02^\mathrm{m} 00.380s$ (J2000) is not coincident with millimeter continuum or spectral line emission in the ALMA data. Given the lack of a clear association, we conclude that this radio continuum source is likely an extra-galactic contaminant and not an indicator of protostellar activity.

In summary, indirect evidence for star formation exists from two different tracers: (1) 24 μm sources at the edge or outside of the ALMA field of view, and (2) ALMA detections of and that are not clearly associated with continuum sources. G28539 is the most massive clump in the sample ($M_\mathrm{cl} \approx \SI{3600}{\ensuremath{
    \mathit{M}_\odot
}}$) and shows fairly limited signs of fragmentation. After the ALMA observations G28539 is the only starless clump candidate remaining in our sample. It is thus a target of great interest for studying the initial conditions of high-mass star formation.

# Modeling Continuum Sources

## Starless core models

A diverse range of continuum sub-structures are found to be present in SCCs, from unresolved compact sources, filaments, to lower surface brightness extended emission. In this section we analyze whether cores with bright, unresolved continuum emission on scales $< \! \SI{1500}{au}$ ($\sim \! \theta_\mathrm{syn} / 2$) are necessarily protostellar even without detections of outflows or strong high-excitation molecular lines. We also model whether low- to intermediate-mass starless cores are accurately recovered in the observations and perform detailed modeling of high-mass starless core candidates in clump G28539.

To characterize the continuum features in our images we apply the radiative transfer code `RADMC-3D`  (cite: dullemond12) to self-consistently calculate the equilibrium dust temperature distributions of externally heated starless cores and to produce synthetic images. We follow a similar approach to modeling starless cores as found in (cite: shirley05) and (cite: lippok16). We apply conventional assumptions for the dust properties (cite: ossenkopf94; weingartner01; young05) and interstellar radiation field (cite: draine78; black94). A detailed description of the computed models may be found in Appendix [11](#apx:Models).

We apply a spherically symmetric Plummer-like function to parametrize the model radial density profile (cite: plummer1911; whitworth01; lippok16). The gas density profile $n_\mathrm{H}$ can be expressed as: $$\begin{equation}
    n_\mathrm{H}(r) = \left( n_\mathrm{in} - n_\mathrm{out} \right) \left[ 1 + \left( \frac{r}{R_\mathrm{flat}} \right)^2 \right]^{-\eta/2} + n_\mathrm{out}
\end{equation}$$ for radius $r$, inner gas density $n_\mathrm{in}$, outer gas density $n_\mathrm{out}$, flat radius $R_\mathrm{flat}$, and power law exponent $\eta$ (cite: ebert55; bonnor56). The strength of the interstellar radiation field (ISRF) is varied from the local value by a multiplicative scale factor $s_\mathrm{isrf}$. We compute  × 10^4^ models, randomly sampling the parameter space by drawing values from a uniform distribution in log-space within the ranges for the parameters $n_\mathrm{in} = \num{1e4} - \SI{1e7}{cm^{-3}}$, $n_\mathrm{out} = \num{1e1} - \SI{1e3}{cm^{-3}}$, $R_\mathrm{flat} = \num{1e3} - \SI{2e4}{au}$, and $\ensuremath{
    s_\mathrm{isrf}
}= 1 - 100$, while $\eta = 2.5 - 5.5$ is drawn uniformly in linear space. Models are evaluated on a logarithmic radial grid from 2.5 × 10^2^ au to 6.0 × 10^4^ au. These values are chosen to cover the range of values from the sample of low- and intermediate mass cores in (cite: lippok16) but extended to higher $n_\mathrm{in}$ and smaller $R_\mathrm{flat}$. After computing the radiative transfer, the models are ray-traced by `RADMC-3D`  and projected to a fiducial distance of $d_\odot = \SI{4}{kpc}$.

## Model recovery

We find that $53\%$ of the computed models ($5268/\num{e4}$) meet the detection threshold of $S_\mathrm{1.3mm,pk} > 5\ensuremath{
    \sigma_\mathrm{rms}
}$ when convolved with a $\theta = 0.8\ensuremath{''}$ Gaussian beam. The cut in peak flux density has no effect on the recovered distributions of $\eta$ and $n_\mathrm{out}$, and minimal effects on $R_\mathrm{flat}$ and $\ensuremath{
    s_\mathrm{isrf}
}$, with an increase in the median values by a factor of $1.5$ and $1.2$, respectively, over the distribution of model cores.

It is important to keep in mind that the suite of model cores is constructed to span the parameter space of relevant values, not to represent an observed or predicted core mass function. We do not use the fractions of detectable cores to infer completeness, but to show the expected range of physical parameters for which cores can be recovered. To estimate this, we sort the models by $M$ and $s_\mathrm{isrf}$, counting both the fraction of detectable cores, and regions of parameter space with at least one detectable model (Fig. [8](#fig:DetectionFraction)). Computing the detection fraction in this way has the effect of marginalizing over our uncertainty in $R_\mathrm{flat}$, $\eta$, $n_\mathrm{in}$, and $n_\mathrm{out}$, that are poorly constrained with our single wavelength maps. Figure [8](#fig:DetectionFraction) (left) shows that at 50% completeness, the cores at $\ensuremath{
    s_\mathrm{isrf}
}\sim 3$ are recovered for $M \gtrsim \SI{4}{\ensuremath{
    \mathit{M}_\odot
}}$, and that this extends down to $M \sim \SI{1}{\ensuremath{
    \mathit{M}_\odot
}}$ for the extreme value $\ensuremath{
    s_\mathrm{isrf}
}= 100$. Figure [8](#fig:DetectionFraction) (right) shows that it is possible however to recover lower-mass cores if the ranges of models is restricted to those that are the most compact (where $R_\mathrm{flat} < \SI{3e3}{au}$, $\eta > 4.5$) and have high central densities ($n_\mathrm{in} > \SI{1e5}{cm^{-3}}$). For these compact sources, $M \sim \SI{1}{\ensuremath{
    \mathit{M}_\odot
}}$ models may be recovered at $\ensuremath{
    s_\mathrm{isrf}
}\sim 3$ and down to $M \sim \SI{0.2}{\ensuremath{
    \mathit{M}_\odot
}}$ for $\ensuremath{
    s_\mathrm{isrf}
}= 100$.

![image](fig_detection_fraction_mtot_isrfs.pdf) ![image](fig_detection_fraction_mtot_isrfs_compact_crop.pdf)

From these models we can infer that the completeness expected from our point-source sensitivity, $\sim \! \SI{0.3}{\ensuremath{
    \mathit{M}_\odot
}}$ at $6\ensuremath{
    \sigma_\mathrm{rms}
}$, is an underestimate if the majority of cores are resolved (cite: beuther18). Low-mass cores with extended profiles will thus go undetected with a criteria based on peak intensity, leading to our seemingly shallow limit of $\sim \! 1 - \SI{4}{\ensuremath{
    \mathit{M}_\odot
}}$. Observationally, we must approach extended emission at low-SNR with caution because there is extended structure in the maps on scales larger than the 12 m primary beam that cannot be adequately CLEANed. For this reason we do not attempt to identify or catalog sources down to the limits of statistical significance for extended and spatially-integrated flux densities but maintain a conservative detection limit based on source peak flux density. The typical integrated flux density of a source is $S_{1.1} \sim \! 1-\SI{10}{mJy}$ ($M \sim \! 1-\SI{10}{\ensuremath{
    \mathit{M}_\odot
}}$ assuming $T_\mathrm{d} = \SI{12}{K}$ and $d_\odot = \SI{4}{kpc}$), and generally consistent with the thermal Jeans mass $M_\mathrm{j,th}$ for a uniform medium at the density of the clump, $M_\mathrm{j,th} \sim \SI{2}{\ensuremath{
    \mathit{M}_\odot
}}$ where $M_\mathrm{j,th} \equiv (4 \pi / 3)(\lambda_\mathrm{j,th} / 2)^3 \rho_0$ for thermal Jeans length $\lambda_\mathrm{j,th}$ and average density $\rho_0$ ((cite: mckee07) (cite: mckee07); see §[5](#sec:FragmentationScale) for an analysis of the Jeans length $\lambda_\mathrm{j,th}$).

## Synthetic observations with CASA

We now investigate whether the models of starless cores provide adequate fits to the brightness profiles present in the SCCs of this survey. We find that compact sources of continuum emission that are unresolved (i.e. deconvolved sizes $\lesssim \! \SI{1500}{au}$, $\approx \theta_\mathrm{syn}/2$) are poorly fit by models of starless cores. Without multiple wavelength observations or gas kinetic temperature information, the radial dust temperature profiles of the cores are poorly constrained. Because of the substantial systematic uncertainties presented in single wavelength observations and potentially undetected embedded protostars, we do not perform a fit to every continuum source, but select a few characteristic examples for quantitative comparison. We create synthetic observations from the models using the `CASA`  `sm` module by predicting onto the observed visibilities (gridded beforehand for computational efficiency) and imaged without noise using the same `tclean` configuration as the observations. This does not introduce a significant effect on the models however because nearly all the flux is concentrated on radii $r < \SI{2e4}{au}$ or angular diameters of $\lesssim \! 8\ensuremath{''}$, appreciably less than half of the 12 m array $27\ensuremath{''}$ HPBW, and substantially less than the maximum recoverable scale of $33\ensuremath{''}$ from the 7 m array. A subset of models were further tested for consistency, because the aim of this comparison is for an understanding of a few representative sources and not detailed parameter estimation, we do not image the full suite of models; rather, we convolve the models with the angular size of the synthesized beam ($\theta_\mathrm{syn} = 0.8\ensuremath{''}$) and convert to radial brightness profiles.

## Comparison to observations

We compare the observations and models using a method based on the $\chi^2$-statistic, where the reduced $\chi_\mathrm{r}^2$ may be expressed as $$\begin{equation}
    \chi^2_\mathrm{r} = \frac{1}{\nu} \sum_i \frac{\left(o_i - m_i\right)^2}{\sigma^2}
\end{equation}$$ for degrees of freedom $\nu$, independent measurements $i$, measurements $o_i$, model values $m_i$, and variances $\sigma^2$. We discriminate between models based on the goodness of fit metric $\Delta \chi^2_\mathrm{r} \equiv \chi^2_\mathrm{r} - \chi^2_\mathrm{r,best}$ from (cite: robitaille07) and (cite: robitaille17). Robitaille et al. apply the heuristic that models with $\Delta \chi^2_\mathrm{r} < 3$ are considered good fits and rejected as poor fits otherwise. Robitaille et al. further note that the Bayesian likelihood under the assumption of normal errors (i.e., $P(D|\theta_j,M) \propto \exp\left[ - \chi^2 / 2\right]$ for data $D$, parameters $\theta_j$, and model $M$) yields too stringent a definition of probability given systematic sources of error in the measurements and poor physical correspondence of the model to nature. This ultimately provides a more conservative criteria for rejecting poor fits as the $\Delta \chi^2_\mathrm{r}$ heuristic likely overestimates uncertainties.

We consider two example starless core candidates, G28539 S2 and S4 (see Fig. [5](#fig:CorePositions) and Table [5](#tab:CoreProperties), because they (1) lack unresolved continuum emission at their center, (2) host no outflows or other indicators of star formation activity, and (3) are relatively isolated such that radial brightness profiles can be adequately extracted. G28539 S2 and S4 are also of interest because they are among the brightest such sources, and thus are good high-mass starless core candidates.

We extract radial brightness profiles for the cores by extracting the integrated flux density within $0.2\ensuremath{''}$ diameter annuli about the central position. Uncertainties in the integrated flux densities are calculated as the $\delta S_\nu = \ensuremath{
    \sigma_\mathrm{rms}
}\sqrt{\Omega_\mathrm{ann}/\Omega_\mathrm{bm}}$ for the solid angle of the annulus $\Omega_\mathrm{ann}$ and the synthesized beam solid angle $\Omega_\mathrm{bm}$. The radial brightness profiles of the models are then compared by Equation [\[eq:ChiSquare\]](#eq:ChiSquare) for degrees of freedom $\nu = r_\mathrm{max}/0.2\ensuremath{''} - 5 \approx 15$ (maximum radius $r_\mathrm{max}=3.5\ensuremath{''}-4.0\ensuremath{''}$). Well-fit models are then selected where $\Delta \chi^2_\mathrm{r} < 3$. Figure [9](#fig:ExampleCores) shows the best fit models compared to the observations, and Figure [10](#fig:RadialModelProfiles) shows the radial brightness profiles with the range of fits. We find that the extended brightness profiles are well fit by the starless core models ($\chi^2_\mathrm{r,best} = 1.1$ and $0.12$ for S2 and S4 respectively). If the range of models are limited to those that resulted in $T_\mathrm{d}(r = \SI{1e3}{au}) = 7-\SI{13}{K}$ in order to be broadly consistent with the clump-average temperature derived from the Hi-GAL SED and GBT fits (cite: tan13), then $M_\mathrm{S2} = 29^{52}_{15} \, \ensuremath{
    \mathit{M}_\odot
}$ and $M_\mathrm{S4} = 14^{34}_{6.0} \, \ensuremath{
    \mathit{M}_\odot
}$, for the median, maximum, and minimum model mass. With a core star-formation efficiency of $30\%$ it is possible that these cores may form high-mass stars ($M_* > \SI{8}{\ensuremath{
    \mathit{M}_\odot
}}$). Assuming a $50\%$ formation efficiency from models regulated by outflows (cite: zhangy14) the maximum expected stellar mass for S2 could be $M_* \approx \SI{26}{\ensuremath{
    \mathit{M}_\odot
}}$. Given the fact that these cores are not associated with outflows in the ALMA data or other high-excitation molecular lines, they are excellent candidates for high-mass starless cores.

![](fig_core_postage_stamps_combined_relabel.pdf)

![](fig_obs_core_profiles_relabel.pdf)

G29558 S1 represents the class of compact continuum sources in our data set. Analysis of this source is then a test of whether the compact sources are well described by starless core models, or alternatively, likely to host embedded protostars. This continuum source has some surrounding extended continuum emission, does not show clear outflows traced by or , but is associated with weak and p- emission. It is bright with peak flux density 6.6 mJy and is similar to other continuum sources with associated outflows. We find that the models poorly fit the observations, with $\chi^2_\mathrm{r,best} = 23.9$ and no models for $\Delta \chi^2_\mathrm{r} < 9$. The properties are pushed to the extremes of parameter space: $\ensuremath{
    s_\mathrm{isrf}
}\sim 100$, $\eta \sim 5.5$, and $n_\mathrm{in} \gtrsim \SI{1e7}{cm^{-3}}$. The moderate $R_\mathrm{flat} \sim \SI{5e3}{au}$ is a compromise between the compact and extended components of the brightness profile. The poor model fits to G29558 S1 do not strictly require that it or any other individual source is protostellar (models with $n_\mathrm{in} \gtrsim \SI{e8}{cm^{-3}}$ and $R_\mathrm{flat} < \SI{e3}{au}$ would likely fit the observations). However, such extreme starless cores are unlikely to be observed in significant numbers in our sample, where $\sim \! 40\%$ of fragments are compact continuum sources. The free-fall timescale of a core with $n_\mathrm{in} = \SI{e8}{cm^{-3}}$ would be $t_\mathrm{ff} \approx \SI{3e3}{yr}$, and for $n_\mathrm{in} = \SI{e7}{cm^{-3}}$ would be $t_\mathrm{ff} \approx \SI{1e4}{yr}$. These are shorter than the inferred ages from the extent and velocity of the observed outflows, although these have substantial uncertainties. Together, the observed properties of these compact continuum sources are more favorably explained as embedded low- to intermediate-mass YSOs, which at $\sim \SI{4}{kpc}$ would be both of comparable brightness and unresolved (see §[3.1](#ssec:CompactSources)). A detailed analysis of the starless and protostellar core properties and dynamics will follow in a future work incorporating data from the VLA observations.

# Fragmentation Scale

## Nearest neighbor separations and Monte Carlo simulations

We characterize the linear fragmentation scale in terms of the nearest neighbor separation $\ensuremath{
    \delta_\mathrm{nns}
}^\prime$ between dendrogram leaves in each clump. Geometric projection of sources in the plane of the sky will systematically decrease $\ensuremath{
    \delta_\mathrm{nns}
}^\prime$ from the true value, $\ensuremath{
    \delta_\mathrm{nns}
}$. In this work we employ Monte Carlo random sampling to de-project $\ensuremath{
    \delta_\mathrm{nns}
}^\prime$ statistically. Thus while the uncertainty in $\ensuremath{
    \delta_\mathrm{nns}
}$ may make constraints for any individual pair of sources quite weak, with prior assumptions on the relative positions of sources, the posterior distribution from the ensemble of all $\ensuremath{
    \delta_\mathrm{nns}
}$ measurements in our sample of SCCs can be readily constrained.

Monte Carlo sampling is used to draw realizations of relative line-of-sight distances $z$, computing $\delta_\mathrm{nns}$ for each source from the Cartesian coordinates $(x,y,z)$. We use the hierarchical classification of sources in the dendrogram to discriminate between two methods of drawing $z$ values: (i) isolated sources and (ii) sources with common surrounding emission. If sources are isolated (Case i), forming a tree with a single branch, then for each trial we draw line-of-sight distances from a Gaussian distribution with standard deviation $\sigma_\mathrm{z} = \SI{0.15}{pc}$ (FWHM 0.35 pc), chosen such that the double-sided $2\sigma_\mathrm{z}$ interval is 0.6 pc, which is the approximate diameter inferred from the 8 μm maps (cf. Fig. [1](#fig:IrMosaic) & [4](#fig:EightMicronTau)). If sources are associated within the same branch of the dendrogram (Case ii; ie. they are within a common base iso-contour of emission) then we assume that those sources are connected in a filamentary gas structure with unknown inclination with respect to the observer. For each trial, we draw a common inclination $\phi$ for the group, pivoting along the major axis, with the pivot axis fixed to $z=0$ at the projected geometric center. Inclinations are drawn such that the length between the two components with the maximum separation $\delta_\mathrm{max}$ is less than $D = \SI{0.6}{pc}$, thus where $\phi$ is drawn uniformly within the interval $(-\arccos(\delta_\mathrm{max}/D), \, +\arccos(\delta_\mathrm{max}/D))$. If $\delta_\mathrm{max} > D$, then $\phi$ is drawn uniformly within $(\ang{-65}, \, \ang{+65})$, such that $\ensuremath{
    \delta_\mathrm{nns}
}\lesssim \SI{1.4}{pc}$ to extend out to a typical clump effective radius of $R \approx \SI{0.7}{pc}$. In total there are $17$ (26%) isolated sources and $49$ (74%) grouped sources. Without more detailed knowledge available, informed from either additional observational data or theoretical simulations, we consider this scheme a conservative way to correct the data for geometric projection. While the assumptions in the correction are simple and imperfect, for brevity we refer to the distributions of MC trials as “projection-corrected” below to distinguish it from the projected data. Extensions of this method may opt to use more sophisticated schemes to group sources beyond common millimeter continuum emission, such as grouping sources through a lower density kinematic tracer or a source-density based clustering algorithm.

With no correction applied, the distribution of projected separations has a median value of $\mu_{1/2}(\ensuremath{
    \delta_\mathrm{nns}
}^\prime) = \SI{0.083}{pc}$ with $(16,84)$ percentile interval of $(0.051,0.140) \, \mathrm{pc}$. To calculate the projection-corrected separations, we compute 1 × 10^4^ realizations for each clump , and find $\mu_{1/2}(\ensuremath{
    \delta_\mathrm{nns}
}) = \SI{0.118}{pc}$ with $\mu_{1/2}(\ensuremath{
    \delta_\mathrm{nns}
})/\mu_{1/2}(\ensuremath{
    \delta_\mathrm{nns}
}^\prime) = 1.42$ and a $(16,84)$ percentile interval of $(0.065,0.232) \, \mathrm{pc}$. For comparison, if we assume that all sources are uniformly distributed within a spherical volume of radius $R_\mathrm{s}$ the following projection correction may be applied: $$\begin{equation}
    \ensuremath{
    \delta_\mathrm{nns}
}= \ensuremath{
    \delta_\mathrm{nns}
}^\prime \left( \frac{4 R_\mathrm{s}}{3 \ensuremath{
    \delta_\mathrm{nns}
}^\prime} \right)^{1/3} \quad ,
\end{equation}$$ as is done in (cite: myers17). If we assume $R_\mathrm{s} = \SI{0.38}{pc}$ from the radius of the 20%-power point of the ALMA primary beam at 4 kpc, then this correction factor would be $\ensuremath{
    \delta_\mathrm{nns}
}/\ensuremath{
    \delta_\mathrm{nns}
}^\prime \approx 1.84$ and $\ensuremath{
    \delta_\mathrm{nns}
}= \SI{0.153}{pc}$, which is larger than the median value computed above from the MC trials by $29\%$.

## Jeans length comparison

To consistently compare $\ensuremath{
    \delta_\mathrm{nns}
}$ values between clumps with different physical conditions, we scale the values by the clump average thermal Jeans length, the minimum wavelength for gravitational fragmentation in an isothermal, uniform medium. The thermal Jeans length $\lambda_\mathrm{j,th}$ can be expressed as (cite: mckee07): $$\begin{equation}
    \ensuremath{
    \lambda_\mathrm{j,th}
}= \left( \frac{\pi c^2_\mathrm{s}}{G \rho_0} \right)^{1/2} \quad ,
\end{equation}$$ where $c_\mathrm{s} = \sqrt{k T / \mu m_\mathrm{p}}$ is the isothermal sound speed (0.21 km s $^{-1}$ for $T_\mathrm{d} = \SI{12}{K}$), $G$ is the gravitational constant, and $\rho_0$ is the average volume density. For the accurate propagation of uncertainties in the calculation of $\lambda_\mathrm{j,th}$, we perform MC random sampling of the relevant observational uncertainties in $\rho_0$ from the dust mass surface density ($\rho_0 = 3 \Sigma / 4 R$) and heliocentric distance. The total (i.e., gas) mass surface density are calculated with $$\begin{equation}
    \Sigma = \frac{S_\mathrm{\nu,int}}{B_\nu(\ensuremath{
    T_\mathrm{d}
}) f_\mathrm{d} \kappa \mu m_\mathrm{p} \Omega} \quad ,
\end{equation}$$ for source integrated flux density $S_\mathrm{\nu,int}$, source solid angle $\Omega$, Planck function $B_\nu(\ensuremath{
    T_\mathrm{d}
})$ evaluated at dust temperature $T_\mathrm{d}$, opacity per mass of dust $\kappa \left( \lambda = \SI{1.3}{mm} \right) = \SI{0.90}{cm^2.g^{-1}}$ (cite: ossenkopf94), mean molecular weight $\mu=2.33$, and dust-to-gas mass ratio $f_\mathrm{d} \equiv \left( m_\mathrm{d} / m_\mathrm{g} \right) = 1/110$ (values are further described in Appendix [11](#apx:Models)).

The fragmentation measured within the ALMA maps is most sensitive within the HPBW ($27\ensuremath{''}$) of the primary beam, so an estimate of $\rho_0$ within this volume we consider to be the most representative density for the computation of $\lambda_\mathrm{j,th}$. Clump average densities on angular scales ($\sim \! 1-2\ensuremath{'}$) larger than the HPBW likely underestimate $\rho_0$. Likewise, image-integrated flux densities from the $12+\SI{7}{m}$ array data possibly underestimate the $\Sigma$ from spatial filtering. Due to the unfavorable match in resolution compared to the Hi-GAL 500 μm ($\theta_\mathrm{hpbw} \approx 35\ensuremath{''}$) or BGPS 1.1 mm ($\theta_\mathrm{hpbw} \approx 33\ensuremath{''}$), we extract flux densities from the ATLASGAL 870 μm maps ($\theta_\mathrm{hpbw} \approx 19\ensuremath{''}$) at the position of the ALMA pointing for each clump within a beam-sized $27\ensuremath{''}$ diameter circular aperture to measure $\Sigma_\mathrm{cl}$. Use of the single millimeter flux mitigates one systematic uncertainty in choosing between Hi-GAL SED fits with or without the 160 μm band included, or using Hi-GAL SED fits that are over the emission for the full clump rather than the peak at consistent angular resolution. The clump average dust temperatures from SED fits to the Hi-GAL data range from $\ensuremath{
    T_\mathrm{d}
}=10-\SI{14}{K}$, but some systematic uncertainty exists with averaging over larger volumes than the ALMA field of view and choices in including the 160 μm band. We choose a conservative dust temperature distribution by assuming a Gaussian dust temperature distribution $\langle \ensuremath{
    T_\mathrm{d}
}\rangle = 12 \pm \SI{2}{K}$ ($1\sigma$ interval). For consistency this temperature is also used for the gas kinetic temperature in $c_\mathrm{s}$. We propagate the uncertainty in heliocentric distance based on the distance probability density function (DPDF) from (cite: ellsworthbowers15a) for each clump. All sources are well-resolved to the near kinematic distance, and have a $\delta d_\odot / d_\odot \approx 0.15$ fractional uncertainty. We sample the distributions for $S_{870}$, $T_\mathrm{d}$, and $d_\odot$ for each MC trial of $\rho_0$ in the calculation of $\lambda_\mathrm{j,th}$ to combine with a trial of $\delta_\mathrm{nns}$ to compute the quotient $\ensuremath{
    \delta_\mathrm{nns}
}/ \langle \ensuremath{
    \lambda_\mathrm{j,th}
}\rangle$ for each clump. The computed median volume densities for the clumps in the sample range between $n(\mathrm{H_2}) = (2 - 6)\times\SI{e4}{cm^{-3}}$ and with associated values of the thermal Jeans length between $\ensuremath{
    \lambda_\mathrm{j,th}
}= 0.10 - \SI{0.17}{pc}$ ($2.1-\SI{3.5e4}{au}$). The median of samples from all clumps is $\ensuremath{
    \lambda_\mathrm{j,th}
}= \SI{0.135}{pc}$ (2.77 × 10^4^ au). No correlation is observed between $\ensuremath{
    \ensuremath{
    \delta_\mathrm{nns}
}/ \langle \ensuremath{
    \lambda_\mathrm{j,th}
}\rangle
}$ and the number of cores/leaves in each clump (Fig. [11](#fig:ClumpScatterJnns)).

![](fig_nleaves_jnns_md.pdf)

Probability density functions (PDFs) of $\ensuremath{
    \ensuremath{
    \delta_\mathrm{nns}
}/ \langle \ensuremath{
    \lambda_\mathrm{j,th}
}\rangle
}$ are computed for each clump by performing Monte Carlo random sampling of the observational uncertainties in $\lambda_\mathrm{j,th}$ as described above and sampling the de-projected source separations (see §[5.1](#ssec:NearestNeighbor)). Figure [12](#fig:NnsBySource) (left) shows the distributions of $\ensuremath{
    \delta_\mathrm{nns}
}/ \langle \ensuremath{
    \lambda_\mathrm{j,th}
}\rangle$ for each clump sorted in descending order by the number of continuum sources. The separation distributions show a bi-modal tendency with peaks at $\ensuremath{
    \ensuremath{
    \delta_\mathrm{nns}
}/ \langle \ensuremath{
    \lambda_\mathrm{j,th}
}\rangle
}\sim 0.3$ and $\ensuremath{
    \ensuremath{
    \delta_\mathrm{nns}
}/ \langle \ensuremath{
    \lambda_\mathrm{j,th}
}\rangle
}\sim 1$, and with long-tails extending to high values $\gtrsim 1.5$. The distinct peaks at small values of $\ensuremath{
    \delta_\mathrm{nns}
}/ \langle \ensuremath{
    \lambda_\mathrm{j,th}
}\rangle$ (all well-resolved) likely result from closely spaced, connected sources where $\delta_\mathrm{nns}$ is not strongly effected from sampling the inclination distribution. Median values of the distributions range between $\ensuremath{
    \ensuremath{
    \delta_\mathrm{nns}
}/ \langle \ensuremath{
    \lambda_\mathrm{j,th}
}\rangle
}= 0.4 - 1.5$. The values are generally consistent with the thermal Jeans length, but the high frequency of sources with sub-Jeans separations may indicate hierarchical fragmentation at multiple scales. With the initial fragmentation on the clump scale, a further fragmentation on the “core scale” would proceed on sizes $\lesssim \SI{2e4}{au}$ and densities $\gtrsim \SI{3e5}{cm^{-3}}$. If such hierarchical fragmentation proceeds principally with two resultant fragments on the core scale, then the second nearest neighbor distance would measure the above level in the hierarchy and recover the spacing of the clump scale. This is supported by a plot of the second nearest neighbor distance $\delta^{(2)}_\mathrm{nns}$ distributions, shown in Figure [12](#fig:NnsBySource) (right), that shows clumps with more uni-modal distributions, with modes and median values at or slightly above the thermal Jeans length. Median values of the $\delta^{(2)}_\mathrm{nns}$ distributions are greater than those for $\ensuremath{
    \delta_\mathrm{nns}
}$ but generally fall within a similar range between $\delta^{(2)}_\mathrm{nns} / \langle \lambda_\mathrm{j,th} \rangle = 0.75 - 1.7$.

![](fig_nns_src_hists_both1and2_relabel.pdf)

We compute PDFs for each clump (see above) and the ensemble distribution composed of all separation measurements from each clump aggregated together (Fig. [13](#fig:CumulativeNns)). The ensemble separation distribution is used to define a representative fragmentation scale from the SCCs in this survey. As these clumps are at similar distances and blindly selected from Galactic Plane dust continuum surveys, the measured ensemble sample properties may be used to cautiously infer the properties of the Galactic high-mass SCC population ($\ensuremath{
    M_\mathrm{cl}
}\gtrsim \SI{e3}{\ensuremath{
    \mathit{M}_\odot
}}$). Additional observations are required to directly constrain the properties of SCCs with $\ensuremath{
    M_\mathrm{cl}
}\gtrsim \SI{e4}{\ensuremath{
    \mathit{M}_\odot
}}$ (if they exist outside of the Central Molecular Zone) or SCCs below the mass range of this sample, $\ensuremath{
    M_\mathrm{cl}
}\lesssim \SI{400}{\ensuremath{
    \mathit{M}_\odot
}}$. Figure [13](#fig:CumulativeNns) shows the cumulative distribution function (CDF) for the ensemble of $\ensuremath{
    \delta_\mathrm{nns}
}/ \langle \ensuremath{
    \lambda_\mathrm{j,th}
}\rangle$ measurements as drawn from the MC sampling for the projected separations, projection-corrected separations, and relevant scales such as the resolution and primary beam HPBW. The projection-corrected ensemble distribution has a median value of $\ensuremath{
    \ensuremath{
    \delta_\mathrm{nns}
}/ \langle \ensuremath{
    \lambda_\mathrm{j,th}
}\rangle
}= 0.82$ with a $(25,75)$ percentile interval of $0.52-1.25$. The percentiles for $\ensuremath{
    \ensuremath{
    \delta_\mathrm{nns}
}/ \langle \ensuremath{
    \lambda_\mathrm{j,th}
}\rangle
}= 0.5$, $1$, $2$, and $3$ are, respectively, $23.6$, $63.3$, $90.3$, and $97.4$. Overall, the sample of SCCs show a fragmentation scale that is well characterized by the thermal Jeans length.

![](fig_nns_pdfcdf_scaled_grouped_relabel.pdf)

The inner and outer grey areas show the scaled synthesized beam ($0.8\ensuremath{''}$) and scaled $20\%$-point of the primary beam ($40\ensuremath{''}$). The scaled HPBW ($27\ensuremath{''}$) of the primary is also shown (dashed cyan). *Upper left:* PDFs of different length scales $\delta$, with the same color coding. The dashed lines show the values of the 50th percentiles. *Lower right:* CDF for the second nearest neighbor separations, $\ensuremath{
    \delta_\mathrm{nns}
}^{(2)}$. *Upper right:* PDF for the second nearest neighbor separations, $\ensuremath{
    \delta_\mathrm{nns}
}^{(2)}$.

A relatively small fraction of the separation distribution is inconsistent with the thermal Jeans length, $<10\%$ for $> 2 \times \ensuremath{
    \lambda_\mathrm{j,th}
}$. The large separations do not result from a single or small number of clumps with consistently large separations, but from isolated individual sources within clumps that show fragmentation near the thermal Jeans length. G30660 and G30912, for example, have a significant proportion of the distribution at large separations (see Fig. [12](#fig:NnsBySource) left), but do not have peculiar dust temperatures, between $\ensuremath{
    T_\mathrm{d}
}= 11 - \SI{12}{K}$ from Hi-GAL SED fits. This portion of the separation distribution may indicate an additional scale for hierarchical fragmentation where a source of non-thermal support prevents fragmentation at the thermal Jeans scale.

The Jeans length can further take into account sources of non-thermal support, such as turbulence or magnetic fields, by using an effective sound speed $$\begin{equation}
   c_\mathrm{s,eff} = \left( c_\mathrm{s}^2 + \sigma_\mathrm{nt}^2 \right)^{1/2} 
\end{equation}$$ through the contribution of a non-thermal velocity dispersion $\sigma_\mathrm{nt}$. From , 9 out of 12 clumps have $T_\mathrm{K}$ measured from (at $32\ensuremath{''}$ resolution). The measured velocity dispersions (i.e. $c_\mathrm{s,eff}$) determined from the spectral line model fit range between $\sigma(\ce{NH3}) = 0.50 - \SI{0.95}{km~s\ensuremath{^{-1}}}$ with a median value of 0.65 km s $^{-1}$, corresponding to $\sigma_\mathrm{nt} \approx \SI{0.62}{km~s\ensuremath{^{-1}}}$ for $c_\mathrm{s} = \SI{0.21}{km~s\ensuremath{^{-1}}}$ at $T_\mathrm{K} = \SI{12}{K}$ (where $T_\mathrm{K} = 11-\SI{14}{K}$). Replacing $c_\mathrm{s}$ with $c_\mathrm{s,eff}$ in Equation [\[eq:JeansLength\]](#eq:JeansLength) yields the effective Jeans length, or when turbulence is the dominant source of non-thermal support, the turbulent Jeans length $\ensuremath{
    \lambda_\mathrm{j,tu}
}$. Because $\lambda_\mathrm{j} \propto c_\mathrm{s}$, the increase $c_\mathrm{s,eff} / c_\mathrm{s} \sim 2.4 - 4.5$ (median $3.1$) yields a similar scaling for $\ensuremath{
    \lambda_\mathrm{j,tu}
}/ \ensuremath{
    \lambda_\mathrm{j,th}
}$. In comparison, $\ensuremath{
    \ensuremath{
    \delta_\mathrm{nns}
}/ \langle \ensuremath{
    \lambda_\mathrm{j,th}
}\rangle
}= 3$ ($\delta_\mathrm{nns} / \langle \ensuremath{
    \lambda_\mathrm{j,tu}
}\rangle \approx 0.32$) occurs at the $97.4$ percentile, and thus while such separations are not absent from the data, they are also not representative of the fragmentation measured within the ALMA maps. The length scale distribution is incomplete beyond $\ensuremath{
    \ensuremath{
    \delta_\mathrm{nns}
}/ \langle \ensuremath{
    \lambda_\mathrm{j,th}
}\rangle
}> 3.1$, where $10\%$ of the MC trials would have 3D separations greater than or equal to the FOV ($40\ensuremath{''}$).

# Discussion

The physical processes regulating fragmentation in molecular clouds remain an open problem in star formation. How much are SCCs supported against gravitationally induced fragmentation from non-thermal forms of pressure, such as magnetic fields ($\mathbf{B}$-fields) and/or turbulence? Individual SCCs have been studied at high-resolution (cite: beuther15a; sanhueza17), but we shall discuss a systematic set of observations on a representative sample of high-mass SCCs. Here we describe the fragmentation characteristics of SCCs in the context of theoretical models of star and cluster formation and compare to existing high-resolution observations of clumps and IRDCs.

## Cylindrical Fragmentation in SCCs

As shown in §[5](#sec:FragmentationScale), we find that clumps fragment at scales consistent with the thermal Jeans length in SCCs. It is known however that geometry and non-thermal support affect the predicted fragmentation scale, producing deviations from that expected for an isothermal, uniform medium. In this section we discuss how the fragmentation scale observed with ALMA compares to different characteristic length scales.

Filaments are ubiquitous in both observed molecular clouds and simulations (cite: barnard07; andre14; smithr16), and thus cylindrical geometry is of special significance to dense molecular regions. On larger spatial scales observable in MIR extinction, it is clear that the clump peaks are embedded in filamentary gas structures (see Fig. [1](#fig:IrMosaic) and G23297 for a good example). An infinite, self-gravitating cylinder is unstable to axisymmetric perturbations or “sausage” instability, where the cylinder fragments at the scale of the fastest growing mode of the fluid instability (cite: chandrasekhar53; ostriker64; larson85; nagasawa87; inutsuka92). For a pressure confined isothermal gas cylinder of radius $R$ and scale height $H = c_\mathrm{s} \left( 4 \pi G \rho_\mathrm{c} \right)^{-1/2}$ (where $\rho_\mathrm{c}$ is the central density of the cylinder) then the fastest growing mode depends on the ratio of $R$ and $H$ (cite: nagasawa87). In the case where $R \ll H$ then $\lambda_\mathrm{cyl} \approx 10.8 R$; and, alternatively where $R \gg H$, then $\lambda_\mathrm{cyl} \approx 22.4 H$ (cite: nagasawa87; jackson10).

Is the isothermal, cylindrical fragmentation scale representative in SCCs? The approximation of SCCs as isothermal is imperfect due to shielding that decreases the temperatures of inner regions, but the assumption is generally more valid than clumps with active HMSF and substantial internal protostellar heating and feedback. Observed aspect ratios of $\gtrsim \! 5$ over the full clump extent support the approximation of an infinite cylindrical geometry. The typical radial extent of the SCCs as observed in the MIR extinction maps suggests $R \sim \SI{0.4}{pc}$. Assuming that the cylinder central density is equal to the observed clump peak density (i.e. $\rho_\mathrm{c} = \rho_0 \approx \SI{3e4}{cm^{-3}}$) then $H \sim \SI{0.02}{pc}$, and thus $R / H \sim 20$ roughly satisfies the condition $R \gg H$. Note that for $\rho_\mathrm{c}$ equal to the clump peak density then this simplifies to $\lambda_\mathrm{cyl} / \ensuremath{
    \lambda_\mathrm{j,th}
}\approx 3.50$, or for the median $\ensuremath{
    \lambda_\mathrm{j,th}
}= \SI{0.137}{pc}$, $\lambda_\mathrm{cyl} = \SI{0.480}{pc}$. We find that $\lambda_\mathrm{cyl}$ is not representative of the $\ensuremath{
    \delta_\mathrm{nns}
}$ distribution in SCCs, with the observed $\ensuremath{
    \ensuremath{
    \delta_\mathrm{nns}
}/ \langle \ensuremath{
    \lambda_\mathrm{j,th}
}\rangle
}\sim 1$.

Observational studies carried out on larger spatial scales than this work support $\lambda_\mathrm{cyl}$ as a characteristic scale in filaments (cite: beuther15b; friesen16). While these studies did not have sufficient spatial resolution to adequately resolve the thermal Jeans length, they probe separations on the clump scale and larger than $\sim \! \SI{1}{pc}$, as observed with ALMA. This work complements the larger-scale studies by identifying fragmentation on the clump Jeans length at an early evolutionary phase. This is supported by the results of (cite: kainulainen13b) who with *Spitzer* MIR extinction mapping find that the molecular filament G11.11–0.12 is well described by filament fragmentation and turbulent $\lambda_\mathrm{cyl}$ on $\delta \gtrsim \SI{0.5}{pc}$ and $\ensuremath{
    \lambda_\mathrm{j,th}
}$ on smaller scales. (cite: beuther15b) in an analysis of the fragmentation in the star-forming filament IRDC 18223 find a mean fragment separation of $\delta = 0.40 \pm \SI{0.18}{pc}$, consistent with a thermal $\lambda_\mathrm{cyl} = \SI{0.44}{pc}$ of the filament, approximately twice that of $\ensuremath{
    \lambda_\mathrm{j,th}
}= 0.07 - \SI{0.23}{pc}$, however the authors note that measures of $\delta$ should be considered an upper limit due to the sensitivity and resolution of the data. (cite: friesen16) in a survey of the entire Serpens South molecular cloud (cite: friesen17) find that the nearest neighbor separations of dense gas structures within the same filament are significantly larger than $\lambda_\mathrm{j,th}$ and are well represented by $\lambda_\mathrm{cyl}$. The spatial resolution is limited however to approximately $\ensuremath{
    \lambda_\mathrm{j,th}
}\sim \SI{0.07}{pc}$, and thus does not properly resolve $\lambda_\mathrm{j,th}$ in sources with $\langle n \rangle \gtrsim \SI{2e3}{cm^{-3}}$. The above surveys support the view of hierarchical fragmentation by gravitationally unstable filaments, but lack the resolution to test what fragmentation process dominates on the scales of individual cores embedded within the clumps. The measurements of the fragmentation scale presented in §[5](#sec:FragmentationScale) complement the above studies at resolutions down to $\sim \! \SI{3000}{au}$ and provide further support to the view that filaments initially fragment at $\lambda_\mathrm{cyl}$ and then further fragment at $\ensuremath{
    \lambda_\mathrm{j,th}
}$.

## Comparison to more active regions

Direct observations of star-forming IRDCs and embedded protoclusters have found fragmentation consistent with the thermal Jeans length (cite: palau15; beuther15a; teixeira16; busquet16; beuther18) but it is unknown if these systems represent the initial state of fragmentation. Because high-mass SCCs may represent an initial stage of protocluster evolution before the formation of a high-mass star, they offer unique insight into the physical processes regulating fragmentation when compared to more evolved systems. From a survey of dense star-forming cores (cite: palau15) find that the fragmentation on $\sim \! \SI{0.1}{pc}$ scales is best explained through thermal fragmentation. Similar results are found at sub-core spatial scales of $\lesssim \! \SI{1000}{au}$ towards the Orion Molecular Cloud 1S (cite: palau17) and also consistent with the fragmentation measured in OMC-1N (cite: teixeira16). While the measured median nearest neighbor separation in SCCs is consistent with the thermal Jeans length of the clump gas, the distribution also shows a distinct peak at approximately an order of magnitude higher gas density near $\ensuremath{
    \ensuremath{
    \delta_\mathrm{nns}
}/ \langle \ensuremath{
    \lambda_\mathrm{j,th}
}\rangle
}\approx 0.3$ (see Figs. [12](#fig:NnsBySource) & [13](#fig:CumulativeNns)). These results may indicate continued thermal Jeans fragmentation such as in OMC-1S and OMC-1N. (cite: beuther15a) find results approximately consistent with thermal Jeans fragmentation towards the $\sim \! \SI{800}{\ensuremath{
    \mathit{M}_\odot
}}$ IRDC 18310–4, and while showing faint 70 μm emission, has similar physical properties to the SCCs in this sample. Similarly an analysis of the star-forming IRDC G14.225–0.506 favors thermal Jeans fragmentation (cite: busquet16). (cite: beuther18) present a minimal spanning tree analysis of the separations in the CORE survey of 20 luminous ($L_\mathrm{bol} > \SI{e4}{\ensuremath{
    \mathit{L}_\odot
}}$) high-mass star forming regions and find fragmentation at scales on the order of the thermal Jeans length or smaller. As a possible explanation for the sub-Jeans length scales, (cite: beuther18) suggest that bulk motions from ongoing global collapse may have brought the fragments within closer proximity after having initially fragmented on the thermal Jeans scale. All of the sources in the CORE survey are high-mass protostellar objects (HMPOs) and more evolved than this sample. Thus our finding of fragmentation on the thermal Jeans length at an earlier evolutionary stage supports the interpretation of the COREs results and conclusion that the measured fragmentation scale may be impacted by the dynamical evolution of the protocluster.

The agreement between the nearest neighbor separations and the thermal Jeans length appears to favor a Jeans fragmentation process for stellar cluster formation. Indeed the thermal Jeans mass in typical star forming clumps is approximately 1 $\mathit{M}_\odot$, which corresponds well with the stellar mass at the peak of the Initial Mass Function. Therefore, (cite: larson05) argued that the thermal Jeans process is responsible for the formation of lower mass stars in a cluster. (cite: zhang09) found that cores forming massive stars often $\gtrsim \! \SI{10}{\ensuremath{
    \mathit{M}_\odot
}}$, an order of magnitude greater than the thermal Jeans mass of its parental clump. These cores require additional support from turbulence to account for their formation. Furthermore, the observed measurements imply that thermal physics provide the dominant form of support, but additional models exist to describe the thermal fragmentation process that differ in geometry and density profile. For example, (cite: myers17) present 2D axisymmetric models of filamentary structure that fragment through the thermal instability of Bonnor-Ebert spheres above a threshold minimum density. Because the Bonnor-Ebert radius and Jeans length have the same dependence on temperature and density with only slight differences in numerical coefficients, this leads to a fragmentation approximately equal to $\lambda_\mathrm{j,th}$. When compared to the observed median $\ensuremath{
    \ensuremath{
    \delta_\mathrm{nns}
}/ \langle \ensuremath{
    \lambda_\mathrm{j,th}
}\rangle
}= 0.91$ from §[5](#sec:FragmentationScale), the spacings between cores predicted by (cite: myers17) is $\ensuremath{
    \ensuremath{
    \delta_\mathrm{nns}
}/ \langle \ensuremath{
    \lambda_\mathrm{j,th}
}\rangle
}= 0.71$ (for a concentration factor $q_\mathrm{Z} \equiv \langle n \rangle / n_\mathrm{min} = 2$) are broadly consistent.

## Coeval formation of low- and high-mass protostars?

It is not clear if SCCs are the progenitor environments of high-mass star formation. Their high total masses ($M_\mathrm{cl} \sim \SI{1000}{\ensuremath{
    \mathit{M}_\odot
}}$), high central densities ($\langle n \rangle \sim \SI{5e4}{cm^{-3}}$), cold gas kinetic temperatures ($\langle T_\mathrm{K}(\ce{NH3}) \rangle \sim \SI{11}{K}$), and low virial parameters ($\alpha_\mathrm{vir} \sim 0.1 - 1$) (cite: wienen12; svoboda16) all point to persistent, bound clumps with the likely necessary physical conditions for high-mass star formation (cite: mckee07). However, no high-mass protostars are observed. These observational facts are consistent with a scenario where high-mass stars form in SCCs through thermal fragmentation, and then accrete clump gas as initially low-mass protostars. Thus, SCCs may represent a very early and unique stage in protocluster evolution preceding the formation of high-mass protostars. This view is supported by cluster-scale theoretical simulations that incorporate protostellar and stellar feedback (cite: smithr09; wangp10; peters10a; peters10b; peters11). (cite: smithr09) find that no high-mass starless cores are formed in their models, and that massive stars originate from low-to-intermediate mass cores that become high-mass protostars via accretion. The mass accreted comes primarily from the surrounding clump at scales $> \SI{0.1}{pc}$ (cite: smithr09; wangp10).

(cite: cyganowski17) in a study towards the deeply embedded protocluster G11.92–0.61 discover low-mass cores in the accretion reservoir of the accreting high-mass protostellar object “MM1” with mass $M_* \sim 30-\SI{60}{\ensuremath{
    \mathit{M}_\odot
}}$ (cite: ilee16). The detection of coeval low- and high-mass protostars is consistent with competitive accretion-type models of star formation (see §[1](#sec:Introduction)). At a comparable distance of $d_\odot = 3.37^{+0.39}_{-0.32}$ kpc (cite: sato14) and total mass to the SCCs in this study, G11.92-0.61 is more evolved, coincident with several indicators of high-mass star formation, such as Class I & II masers, masers, a GLIMPSE Extended Green Object (cite: cyganowski08), numerous “hot core” molecular lines, and high-velocity collimated outflows. The sample of SCCs in this study complement the study of G11.92–0.61 in (cite: cyganowski17) through ALMA observations at similar resolution and sensitivity for clumps in a less active evolutionary state. In contrast, we find no clear high-mass protostellar cores or high-mass protostars in our sample of SCCs, while numerous accreting low-mass protostars are observed, as evidenced by bipolar outflows in /. If a few of the protostars in SCCs will accrete up to high-mass stars, for which the accretion reservoir of the clump is sufficient, then these observations support a coeval mode of protocluster formation at earlier phases. When initially only low- to intermediate-mass protostars are present, this coeval formation may also be termed “low-mass first” to lie in contrast to the monolithic collapse of turbulently supported high-mass cores. The competitive accretion-type simulations performed by (cite: smithr09) find that high-mass stars form initially from intermediate mass pre-stellar cores near the center of the gravitational potential which accrete principally from collapsing clump gas up to high-mass condensations. An important feature of the (cite: smithr09) model is that low-mass protostars form within the accretion reservoir of the central protostar, at separations $< \! \SI{0.15}{pc}$. This is well matched to the distribution of nearest neighbor separations found in this work of $\mu_{1/2}(\ensuremath{
    \delta_\mathrm{nns}
}) = \SI{0.118}{pc}$ (see §[5](#sec:FragmentationScale)). As (cite: smithr09) point out, this signature is likely the most detectable at the early evolutionary phases of the clump where sources are less centrally concentrated in the potential and bright sources of emission are not present.

In contrast to the results of (cite: cyganowski17), (cite: zhang15) in a study of the protocluster G28.24+0.06 P1 failed to detect a distributed population of low-mass cores with Cycle 0 ALMA observations. Based on this (cite: zhang15) draw the conclusion that the distributed population of low-mass cores forms at a later evolutionary stage and that they are not, at least for the initial generation of protostars, coeval. Because G11.91–0.61 is at a later evolutionary stage, the distributed population of low-mass protostars observed in it may have developed after the massive cores formed. The SCCs in this study are in a similar early evolutionary phase as G28.24+0.06 and also similarly lack high-mass protostars (the maximum core mass in G28.4+0.06 is $M_\mathrm{core} \sim \SI{16}{\ensuremath{
    \mathit{M}_\odot
}}$). Accurate core masses are required for a quantitative analysis of the mass segregation and related length scales, but the diversity in morphologies shown within the sample, from distributed (e.g. G30660, G29558) to weakly fragmented (e.g. G28539, G29601), supports the presence of a distributed low-mass core population at the initial evolutionary phase for some systems. It is possible that depending on the initial level of support provided against fragmentation individual systems develop with varying degrees of hierarchy and segregation, and that the conclusions of (cite: zhang15) and (cite: cyganowski17) may both be correct for sources of different initial physical conditions.

The short evolutionary timescales of high-mass starless clumps, $\tau_\mathrm{SCC} \sim 0.5-\SI{0.1}{Myr}$ for $\ensuremath{
    M_\mathrm{cl}
}= 1-\SI{3e3}{\ensuremath{
    \mathit{M}_\odot
}}$ , is also consistent with the simulations of (cite: smithr09) that show that the central, resultant high-mass protostar accretes in $0.25 \times t_\mathrm{dyn} \sim \SI{0.12}{Myr}$ the clump dynamical time, over a diameter of $\sim \! \SI{0.4}{pc}$ (equivalent to the ALMA HPBW) (cite: wangp10). Similarly, (cite: battersby17) perform a lifetime analysis of dense, molecular gas ($N(\ce{H2}) \gtrsim \SI{e22}{cm^-2}$) analyzed on a per-pixel basis from a Hi-GAL $2\deg \times 2\deg$ field near $\ell = 30\deg$. They find a timescale that is consistent for starless regions of $0.2-\SI{1.7}{Myr}$, although with substantial uncertainty. The similarity in timescales is reasonable, as once a high-mass protostar forms, it would be accompanied by observational star formation indicators that identify it as a protostellar clump and remove it from the SCC category, as determined in . Further, we also observe hierarchical fragmentation as evidenced by the multi-modal distribution of nearest neighbor separations (see Fig. [13](#fig:CumulativeNns)), as seen in G11.92–0.61. The ubiquity of filamentary structures observed (see Fig. [3](#fig:ContinuumTwelve)) may also point to accretion mediated by sub-sonically gravitationally contracting filaments (cite: smithr16). This may suggest that while self-gravitating, turbulent clumps are not globally collapsing, accretion may yet be mediated through locally collapsing filaments. This latter point will be the topic of further research investigated with ALMA observations of $\mathrm{N_2H^+}$ $J=1\rightarrow0$ to study the kinematics of the filaments observed in this sample SCCs.

# Conclusions

We present the first systematic observations of a large sample of well-vetted starless clump candidates with ALMA at high-resolution ($\sim \! \SI{3000}{au}$) capable of resolving the thermal Jeans length and sensitivity (50   ^−1^) sufficient for detecting point sources down to $\sim \! \SI{0.3}{\ensuremath{
    \mathit{M}_\odot
}}$ and moderately compact starless cores down to $\sim \! \SI{1.0}{\ensuremath{
    \mathit{M}_\odot
}}$). The targets are selected from a complete sample of clumps identified from large Galactic Plane surveys. The sample is composed of 12 high-mass SCCs within 5 kpc from (cite: svoboda16) and (cite: traficante15) which did not show detected emission at 70 μm or other star formation indicators. Because these systems have not been affected by the extreme (proto-)stellar feedback of high-mass stars they are ideal environments to study the initial conditions of protocluster evolution. Our main findings are:

1.  The newly sensitive ALMA Band 6 $12+\SI{7}{m}$ ($\nu_\mathrm{c} \approx \SI{230}{GHz}$) data show multiple indicators of low-/intermediate-mass star formation activity present in 11 out of 12 formerly starless clump candidates. This is determined through the presence of bipolar outflows detected in $J=2\rightarrow1$ and $J=5\rightarrow4$ emission, and high-excitation p- $3_{2,2} \rightarrow 2_{2,1}$ emission ($\ensuremath{
        E_\mathrm{u}
    }/ k = \SI{68.1}{K}$). These observations caution the interpretation of infrared dark clouds and SCCs identified from Galactic Plane surveys as quiescent, and unless shown otherwise are, given the findings towards this sample, likely to host low-/intermediate-mass star formation activity below the luminosity completeness of current surveys.

2.  We compare representative examples of resolved and unresolved continuum sources with radiative transfer models of starless cores computed with `RADMC-3D` . Unresolved sources are poorly fit by starless core models with typical physical properties. The range of models does not encompass the most compact and dense cores ($R_\mathrm{flat} < \SI{1e3}{au}$, $n_\mathrm{in} \gtrsim \SI{1e7}{cm^{-3}}$), but the short core free-fall times ($t_\mathrm{ff} \lesssim \SI{1e4}{yr}$) and the observed similar flux-density to Gould’s Belt low-/intermediate-mass protostars, support the conclusion that these cores are protostellar even without identified outflows in or .

3.  Two high-mass starless core candidates in G28539 are identified and well fit by starless core models, with $M_\mathrm{S2} = 29^{52}_{15} \, \ensuremath{
        \mathit{M}_\odot
    }$ and $M_\mathrm{S4} = 14^{34}_{6.0}$. Without supplementary measurements to infer the dust temperature profile, the masses are highly uncertain, and are consistent within the uncertainties of only forming an intermediate mass star ($M_* < \SI{8}{\ensuremath{
        \mathit{M}_\odot
    }}$).

4.  G28539 is the sole remaining starless clump candidate without any definitive indications of protostellar activity from the ALMA observations. It is the most massive SCC in the sample ($M_\mathrm{cl} \approx 3600^{+600}_{-500} \, \ensuremath{
        \mathit{M}_\odot
    }$, $d_\odot =  4.8^{+0.3}{-0.3}\, \mathrm{kpc}$), and stands as an excellent target to study the initial conditions of protocluster evolution. A marginal 24 μm source, however, is observed coincident with 1.3 mm continuum source (G28539 S1) near the NW edge of the ALMA field, which may be evidence or protostellar activity. Further indirect evidence for star formation exists from compact and emission, although the source of emission is not associated with a continuum source. If these signatures are indeed associated with protostellar activity there would be no true high-mass starless clumps in this sample.

5.  A high degree of fragmentation is observed, with nearest neighbor separations consistent with the clump scale thermal Jeans length ($\sim \! \SI{0.1}{pc}$). In context of previous observations that on larger scales see separations consistent with the turbulent Jeans length or cylindrical thermal Jeans length, our findings support a hierarchical fragmentation process, where the highest density regions of SCCs are not strongly supported against fragmentation by turbulence or magnetic fields.

6.  Observed embedded low- to intermediate-mass star formation and thermal Jeans fragmentation in high-mass SCCs are consistent with models of star formation that form high-mass stars through gravitationally driven cloud inflow, in which low- and high-mass stars form coevally. However, further observations and followup study are necessary to properly characterize the clump star formation efficiency, protostellar accretion rates, and presence of dynamical flows in molecular tracers to validate this conclusion.

# Acknowledgments

We are grateful to the anonymous referee for many helpful comments and suggestions. BES would like to thank Al Wootten and the staff of the NRAO North American ALMA Science Center, Kimberly Ward-Duong for helpful discussions, and Viviana Rosero for access to the JVLA C Band image towards G28539. BES was supported in part by the NSF Graduate Research Fellowship under grant No. DGE-114395. YLS and BES acknowledge the support from the NSF AAG grant No. AST-1410190. HB acknowledges support from the European Research Council under the European Community’s Horizon 2020 framework program (2014–2020) via the ERC Consolidator Grant “From Cloud to Star Formation (CSF)” (project number 648505).

# Software

This research has made use of the following software projects: [Astropy](https://astropy.org/) (cite: astropy18), [Matplotlib](https://matplotlib.org/) (cite: matplotlib07), [NumPy](http://www.numpy.org/) and [SciPy](https://scipy.org/) (cite: numpy07), [Pandas](https://pandas.pydata.org/) (cite: pandas10), [IPython](https://ipython.org/) (cite: ipython07), [CASA](https://casa.nrao.edu/) (cite: casa07), and the NASA’s Astrophysics Data System.

# Facilities

ALMA

natexlab

(ref: aguirre11) Aguirre, J. E., Ginsburg, A. G., Dunham, M. K., et al. 2011, ApJS, 192, 4, doi: [`10.1088/0067-0049/192/1/4`](https://doi.org/10.1088/0067-0049/192/1/4)

(ref: andre14) André, P., Di Francesco, J., Ward-Thompson, D., et al. 2014, Protostars and Planets VI, 27, doi: [`10.2458/azu_uapress_9780816531240-ch002`](https://doi.org/10.2458/azu_uapress_9780816531240-ch002)

(ref: arce07) Arce, H. G., Shepherd, D., Gueth, F., et al. 2007, Protostars and Planets V, 245

(ref: barnard07) Barnard, E. E. 1907, ApJ, 25, doi: [`10.1086/141434`](https://doi.org/10.1086/141434)

(ref: battersby10) Battersby, C., Bally, J., Jackson, J. M., et al. 2010, ApJ, 721, 222, doi: [`10.1088/0004-637X/721/1/222`](https://doi.org/10.1088/0004-637X/721/1/222)

(ref: battersby17) Battersby, C., Bally, J., & Svoboda, B. 2017, ApJ, 835, 263, doi: [`10.3847/1538-4357/835/2/263`](https://doi.org/10.3847/1538-4357/835/2/263)

(ref: benjamin03) Benjamin, R. A., Churchwell, E., Babler, B. L., et al. 2003, PASP, 115, 953, doi: [`10.1086/376696`](https://doi.org/10.1086/376696)

(ref: bergin07) Bergin, E. A., & Tafalla, M. 2007, ARA&A, 45, 339, doi: [`10.1146/annurev.astro.45.071206.100404`](https://doi.org/10.1146/annurev.astro.45.071206.100404)

(ref: beuther07) Beuther, H., Churchwell, E. B., McKee, C. F., & Tan, J. C. 2007, Protostars and Planets V, 165

(ref: beuther15b) Beuther, H., Ragan, S. E., Johnston, K., et al. 2015a, A&A, 584, A67, doi: [`10.1051/0004-6361/201527108`](https://doi.org/10.1051/0004-6361/201527108)

(ref: beuther15a) Beuther, H., Henning, T., Linz, H., et al. 2015b, A&A, 581, A119, doi: [`10.1051/0004-6361/201526759`](https://doi.org/10.1051/0004-6361/201526759)

(ref: beuther18) Beuther, H., Mottram, J. C., Ahmadi, A., et al. 2018, ArXiv e-prints. [`https://arxiv.org/abs/1805.01191`](https://arxiv.org/abs/1805.01191)

(ref: black94) Black, J. H. 1994, in Astronomical Society of the Pacific Conference Series, Vol. 58, The First Symposium on the Infrared Cirrus and Diffuse Interstellar Clouds, ed. R. M. Cutri & W. B. Latter, 355

(ref: bonnell01) Bonnell, I. A., Clarke, C. J., Bate, M. R., & Pringle, J. E. 2001, MNRAS, 324, 573, doi: [`10.1046/j.1365-8711.2001.04311.x`](https://doi.org/10.1046/j.1365-8711.2001.04311.x)

(ref: bonnor56) Bonnor, W. B. 1956, MNRAS, 116, 351, doi: [`10.1093/mnras/116.3.351`](https://doi.org/10.1093/mnras/116.3.351)

(ref: busquet16) Busquet, G., Estalella, R., Palau, A., et al. 2016, ApJ, 819, 139, doi: [`10.3847/0004-637X/819/2/139`](https://doi.org/10.3847/0004-637X/819/2/139)

(ref: cardelli89) Cardelli, J. A., Clayton, G. C., & Mathis, J. S. 1989, ApJ, 345, 245, doi: [`10.1086/167900`](https://doi.org/10.1086/167900)

(ref: carniani15) Carniani, S., Maiolino, R., De Zotti, G., et al. 2015, A&A, 584, A78, doi: [`10.1051/0004-6361/201525780`](https://doi.org/10.1051/0004-6361/201525780)

(ref: chambers09) Chambers, E. T., Jackson, J. M., Rathborne, J. M., & Simon, R. 2009, ApJS, 181, 360, doi: [`10.1088/0067-0049/181/2/360`](https://doi.org/10.1088/0067-0049/181/2/360)

(ref: chandrasekhar53) Chandrasekhar, S., & Fermi, E. 1953, ApJ, 118, 116, doi: [`10.1086/145732`](https://doi.org/10.1086/145732)

(ref: churchwell09) Churchwell, E., Babler, B. L., Meade, M. R., et al. 2009, PASP, 121, 213, doi: [`10.1086/597811`](https://doi.org/10.1086/597811)

(ref: contreras13) Contreras, Y., Schuller, F., Urquhart, J. S., et al. 2013, A&A, 549, A45, doi: [`10.1051/0004-6361/201220155`](https://doi.org/10.1051/0004-6361/201220155)

(ref: csengeri14) Csengeri, T., Urquhart, J. S., Schuller, F., et al. 2014, A&A, 565, A75, doi: [`10.1051/0004-6361/201322434`](https://doi.org/10.1051/0004-6361/201322434)

(ref: cyganowski17) Cyganowski, C. J., Brogan, C. L., Hunter, T. R., et al. 2017, MNRAS, 468, 3694, doi: [`10.1093/mnras/stx043`](https://doi.org/10.1093/mnras/stx043)

(ref: cyganowski08) Cyganowski, C. J., Whitney, B. A., Holden, E., et al. 2008, AJ, 136, 2391, doi: [`10.1088/0004-6256/136/6/2391`](https://doi.org/10.1088/0004-6256/136/6/2391)

(ref: draine78) Draine, B. T. 1978, ApJS, 36, 595, doi: [`10.1086/190513`](https://doi.org/10.1086/190513)

(ref: dullemond12) Dullemond, C. P., Juhasz, A., Pohl, A., et al. 2012, RADMC-3D: A multi-purpose radiative transfer tool, Astrophysics Source Code Library. [`https://ascl.net/1202.015`](https://ascl.net/1202.015)

(ref: dunham14) Dunham, M. M., Stutz, A. M., Allen, L. E., et al. 2014, Protostars and Planets VI, 195, doi: [`10.2458/azu_uapress_9780816531240-ch009`](https://doi.org/10.2458/azu_uapress_9780816531240-ch009)

(ref: dzib10) Dzib, S., Loinard, L., Mioduszewski, A. J., et al. 2010, ApJ, 718, 610, doi: [`10.1088/0004-637X/718/2/610`](https://doi.org/10.1088/0004-637X/718/2/610)

(ref: ebert55) Ebert, R. 1955, ZAp, 37, 217

(ref: eden17) Eden, D. J., Moore, T. J. T., Plume, R., et al. 2017, MNRAS, 469, 2163, doi: [`10.1093/mnras/stx874`](https://doi.org/10.1093/mnras/stx874)

(ref: elia17) Elia, D., Molinari, S., Schisano, E., et al. 2017, MNRAS, 471, 100, doi: [`10.1093/mnras/stx1357`](https://doi.org/10.1093/mnras/stx1357)

(ref: ellsworthbowers15a) Ellsworth-Bowers, T. P., Rosolowsky, E., Glenn, J., et al. 2015, ApJ, 799, 29, doi: [`10.1088/0004-637X/799/1/29`](https://doi.org/10.1088/0004-637X/799/1/29)

(ref: enoch11) Enoch, M. L., Corder, S., Duchêne, G., et al. 2011, ApJS, 195, 21, doi: [`10.1088/0067-0049/195/2/21`](https://doi.org/10.1088/0067-0049/195/2/21)

(ref: feng16) Feng, S., Beuther, H., Zhang, Q., et al. 2016a, ApJ, 828, 100, doi: [`10.3847/0004-637X/828/2/100`](https://doi.org/10.3847/0004-637X/828/2/100)

(ref: feng16b) —. 2016b, ApJ, 828, 100, doi: [`10.3847/0004-637X/828/2/100`](https://doi.org/10.3847/0004-637X/828/2/100)

(ref: frank14) Frank, A., Ray, T. P., Cabrit, S., et al. 2014, Protostars and Planets VI, 451, doi: [`10.2458/azu_uapress_9780816531240-ch020`](https://doi.org/10.2458/azu_uapress_9780816531240-ch020)

(ref: friesen16) Friesen, R. K., Bourke, T. L., Di Francesco, J., Gutermuth, R., & Myers, P. C. 2016, ApJ, 833, 204, doi: [`10.3847/1538-4357/833/2/204`](https://doi.org/10.3847/1538-4357/833/2/204)

(ref: friesen17) Friesen, R. K., Pineda, J. E., co-PIs, et al. 2017, ApJ, 843, 63, doi: [`10.3847/1538-4357/aa6d58`](https://doi.org/10.3847/1538-4357/aa6d58)

(ref: ginsburg13) Ginsburg, A., Glenn, J., Rosolowsky, E., et al. 2013, ApJS, 208, 14, doi: [`10.1088/0067-0049/208/2/14`](https://doi.org/10.1088/0067-0049/208/2/14)

(ref: hartmann12) Hartmann, L., Ballesteros-Paredes, J., & Heitsch, F. 2012, MNRAS, 420, 1457, doi: [`10.1111/j.1365-2966.2011.20131.x`](https://doi.org/10.1111/j.1365-2966.2011.20131.x)

(ref: hatsukade13) Hatsukade, B., Ohta, K., Seko, A., Yabe, K., & Akiyama, M. 2013, ApJL, 769, L27, doi: [`10.1088/2041-8205/769/2/L27`](https://doi.org/10.1088/2041-8205/769/2/L27)

(ref: hocuk17) Hocuk, S., Szucs, L., Caselli, P., et al. 2017, ArXiv e-prints. [`https://arxiv.org/abs/1704.02763`](https://arxiv.org/abs/1704.02763)

(ref: hosokawa09) Hosokawa, T., & Omukai, K. 2009, ApJ, 691, 823, doi: [`10.1088/0004-637X/691/1/823`](https://doi.org/10.1088/0004-637X/691/1/823)

(ref: matplotlib07) Hunter, J. D. 2007, Computing In Science & Engineering, 9, 90, doi: [`10.1109/MCSE.2007.55`](https://doi.org/10.1109/MCSE.2007.55)

(ref: ilee16) Ilee, J. D., Cyganowski, C. J., Nazari, P., et al. 2016, MNRAS, 462, 4386, doi: [`10.1093/mnras/stw1912`](https://doi.org/10.1093/mnras/stw1912)

(ref: inutsuka92) Inutsuka, S.-I., & Miyama, S. M. 1992, ApJ, 388, 392, doi: [`10.1086/171162`](https://doi.org/10.1086/171162)

(ref: jackson10) Jackson, J. M., Finn, S. C., Chambers, E. T., Rathborne, J. M., & Simon, R. 2010, ApJL, 719, L185, doi: [`10.1088/2041-8205/719/2/L185`](https://doi.org/10.1088/2041-8205/719/2/L185)

(ref: jimenezserra10) Jiménez-Serra, I., Caselli, P., Tan, J. C., et al. 2010, MNRAS, 406, 187, doi: [`10.1111/j.1365-2966.2010.16698.x`](https://doi.org/10.1111/j.1365-2966.2010.16698.x)

(ref: kainulainen13b) Kainulainen, J., Ragan, S. E., Henning, T., & Stutz, A. 2013, A&A, 557, A120, doi: [`10.1051/0004-6361/201321760`](https://doi.org/10.1051/0004-6361/201321760)

(ref: kainulainen17a) Kainulainen, J., Stutz, A. M., Stanke, T., et al. 2017, A&A, 600, A141, doi: [`10.1051/0004-6361/201628481`](https://doi.org/10.1051/0004-6361/201628481)

(ref: kauffmann10) Kauffmann, J., & Pillai, T. 2010, ApJ, 723, L7, doi: [`10.1088/2041-8205/723/1/L7`](https://doi.org/10.1088/2041-8205/723/1/L7)

(ref: kong17) Kong, S., Tan, J. C., Caselli, P., et al. 2017, ApJ, 834, 193, doi: [`10.3847/1538-4357/834/2/193`](https://doi.org/10.3847/1538-4357/834/2/193)

(ref: kroupa01) Kroupa, P. 2001, MNRAS, 322, 231, doi: [`10.1046/j.1365-8711.2001.04022.x`](https://doi.org/10.1046/j.1365-8711.2001.04022.x)

(ref: larson85) Larson, R. B. 1985, MNRAS, 214, 379, doi: [`10.1093/mnras/214.3.379`](https://doi.org/10.1093/mnras/214.3.379)

(ref: larson05) —. 2005, MNRAS, 359, 211, doi: [`10.1111/j.1365-2966.2005.08881.x`](https://doi.org/10.1111/j.1365-2966.2005.08881.x)

(ref: lippok16) Lippok, N., Launhardt, R., Henning, T., et al. 2016, A&A, 592, A61, doi: [`10.1051/0004-6361/201525792`](https://doi.org/10.1051/0004-6361/201525792)

(ref: louvet16) Louvet, F., Motte, F., Gusdorf, A., et al. 2016, A&A, 595, A122, doi: [`10.1051/0004-6361/201629077`](https://doi.org/10.1051/0004-6361/201629077)

(ref: lu15b) Lu, X., Zhang, Q., Wang, K., & Gu, Q. 2015, ApJ, 805, 171, doi: [`10.1088/0004-637X/805/2/171`](https://doi.org/10.1088/0004-637X/805/2/171)

(ref: mcguire16) McGuire, C., Fuller, G. A., Peretto, N., et al. 2016, A&A, 594, A118, doi: [`10.1051/0004-6361/201527062`](https://doi.org/10.1051/0004-6361/201527062)

(ref: mckee07) McKee, C. F., & Ostriker, E. C. 2007, ARA&A, 45, 565, doi: [`10.1146/annurev.astro.45.051806.110602`](https://doi.org/10.1146/annurev.astro.45.051806.110602)

(ref: mckee02) McKee, C. F., & Tan, J. C. 2002, Nature, 416, 59, doi: [`10.1038/416059a`](https://doi.org/10.1038/416059a)

(ref: mckee03) —. 2003, ApJ, 585, 850, doi: [`10.1086/346149`](https://doi.org/10.1086/346149)

(ref: pandas10) McKinney, W. 2010, in Proceedings of the 9th Python in Science Conference, ed. S. van der Walt & J. Millman, 51 – 56

(ref: casa07) McMullin, J. P., Waters, B., Schiebel, D., Young, W., & Golap, K. 2007, in Astronomical Society of the Pacific Conference Series, Vol. 376, Astronomical Data Analysis Software and Systems XVI, ed. R. A. Shaw, F. Hill, & D. J. Bell, 127

(ref: molinari10) Molinari, S., Swinyard, B., Bally, J., et al. 2010, PASP, 122, 314, doi: [`10.1086/651314`](https://doi.org/10.1086/651314)

(ref: molinari16a) Molinari, S., Schisano, E., Elia, D., et al. 2016, A&A, 591, A149, doi: [`10.1051/0004-6361/201526380`](https://doi.org/10.1051/0004-6361/201526380)

(ref: motte17) Motte, F., Bontemps, S., & Louvet, F. 2017, ArXiv e-prints. [`https://arxiv.org/abs/1706.00118`](https://arxiv.org/abs/1706.00118)

(ref: cdms) Müller, H. S. P., Schlöder, F., Stutzki, J., & Winnewisser, G. 2005, Journal of Molecular Structure, 742, 215, doi: [`10.1016/j.molstruc.2005.01.027`](https://doi.org/10.1016/j.molstruc.2005.01.027)

(ref: myers17) Myers, P. C. 2017, ApJ, 838, 10, doi: [`10.3847/1538-4357/aa5fa8`](https://doi.org/10.3847/1538-4357/aa5fa8)

(ref: nagasawa87) Nagasawa, M. 1987, Progress of Theoretical Physics, 77, 635, doi: [`10.1143/PTP.77.635`](https://doi.org/10.1143/PTP.77.635)

(ref: luong13) Nguyen-Lu’o’ng, Q., Motte, F., Carlhoff, P., et al. 2013, ApJ, 775, 88, doi: [`10.1088/0004-637X/775/2/88`](https://doi.org/10.1088/0004-637X/775/2/88)

(ref: numpy07) Oliphant, T. E. 2007, Computing in Science & Engineering, 9

(ref: ossenkopf94) Ossenkopf, V., & Henning, T. 1994, A&A, 291, 943

(ref: ostriker64) Ostriker, J. 1964, ApJ, 140, 1056, doi: [`10.1086/148005`](https://doi.org/10.1086/148005)

(ref: palau15) Palau, A., Ballesteros-Paredes, J., Vázquez-Semadeni, E., et al. 2015, MNRAS, 453, 3785, doi: [`10.1093/mnras/stv1834`](https://doi.org/10.1093/mnras/stv1834)

(ref: palau17) Palau, A., Zapata, L. A., Roman-Zuniga, C. G., et al. 2017, ArXiv e-prints. [`https://arxiv.org/abs/1706.04623`](https://arxiv.org/abs/1706.04623)

(ref: peretto09) Peretto, N., & Fuller, G. A. 2009, A&A, 505, 405, doi: [`10.1051/0004-6361/200912127`](https://doi.org/10.1051/0004-6361/200912127)

(ref: ipython07) Pérez, F., & Granger, B. E. 2007, Computing in Science & Engineering, 9

(ref: peters11) Peters, T., Banerjee, R., Klessen, R. S., & Mac Low, M.-M. 2011, ApJ, 729, 72, doi: [`10.1088/0004-637X/729/1/72`](https://doi.org/10.1088/0004-637X/729/1/72)

(ref: peters10a) Peters, T., Banerjee, R., Klessen, R. S., et al. 2010a, ApJ, 711, 1017, doi: [`10.1088/0004-637X/711/2/1017`](https://doi.org/10.1088/0004-637X/711/2/1017)

(ref: peters10b) Peters, T., Klessen, R. S., Mac Low, M.-M., & Banerjee, R. 2010b, ApJ, 725, 134, doi: [`10.1088/0004-637X/725/1/134`](https://doi.org/10.1088/0004-637X/725/1/134)

(ref: plummer1911) Plummer, H. C. 1911, MNRAS, 71, 460, doi: [`10.1093/mnras/71.5.460`](https://doi.org/10.1093/mnras/71.5.460)

(ref: pokhrel18) Pokhrel, R., Myers, P. C., Dunham, M. M., et al. 2018, ApJ, 853, 5, doi: [`10.3847/1538-4357/aaa240`](https://doi.org/10.3847/1538-4357/aaa240)

(ref: slaim) Remijan, A. J., Markwick-Kemper, A., & ALMA Working Group on Spectral Line Frequencies. 2007, in American Astronomical Society Meeting Abstracts, Vol. 211, 132.11

(ref: robitaille17) Robitaille, T. P. 2017, A&A, 600, A11, doi: [`10.1051/0004-6361/201425486`](https://doi.org/10.1051/0004-6361/201425486)

(ref: robitaille07) Robitaille, T. P., Whitney, B. A., Indebetouw, R., & Wood, K. 2007, ApJS, 169, 328, doi: [`10.1086/512039`](https://doi.org/10.1086/512039)

(ref: rosero16) Rosero, V., Hofner, P., Claussen, M., et al. 2016, ArXiv e-prints. [`https://arxiv.org/abs/1609.03269`](https://arxiv.org/abs/1609.03269)

(ref: rosolowsky10) Rosolowsky, E., Dunham, M. K., Ginsburg, A., et al. 2010, ApJS, 188, 123, doi: [`10.1088/0067-0049/188/1/123`](https://doi.org/10.1088/0067-0049/188/1/123)

(ref: rosolowsky08b) Rosolowsky, E. W., Pineda, J. E., Kauffmann, J., & Goodman, A. A. 2008, ApJ, 679, 1338, doi: [`10.1086/587685`](https://doi.org/10.1086/587685)

(ref: sanhueza13) Sanhueza, P., Jackson, J. M., Foster, J. B., et al. 2013, ApJ, 773, 123, doi: [`10.1088/0004-637X/773/2/123`](https://doi.org/10.1088/0004-637X/773/2/123)

(ref: sanhueza17) Sanhueza, P., Jackson, J. M., Zhang, Q., et al. 2017, ApJ, 841, 97, doi: [`10.3847/1538-4357/aa6ff8`](https://doi.org/10.3847/1538-4357/aa6ff8)

(ref: sato14) Sato, M., Wu, Y. W., Immer, K., et al. 2014, ApJ, 793, 72, doi: [`10.1088/0004-637X/793/2/72`](https://doi.org/10.1088/0004-637X/793/2/72)

(ref: schilke97) Schilke, P., Walmsley, C. M., Pineau des Forets, G., & Flower, D. R. 1997, A&A, 321, 293

(ref: schuller09) Schuller, F., Menten, K. M., Contreras, Y., et al. 2009, A&A, 504, 415, doi: [`10.1051/0004-6361/200811568`](https://doi.org/10.1051/0004-6361/200811568)

(ref: shirley07) Shirley, Y. L., Claussen, M. J., Bourke, T. L., Young, C. H., & Blake, G. A. 2007, ApJ, 667, 329, doi: [`10.1086/520570`](https://doi.org/10.1086/520570)

(ref: shirley05) Shirley, Y. L., Nordhaus, M. K., Grcevich, J. M., et al. 2005, ApJ, 632, 982, doi: [`10.1086/431963`](https://doi.org/10.1086/431963)

(ref: smithr16) Smith, R. J., Glover, S. C. O., Klessen, R. S., & Fuller, G. A. 2016, MNRAS, 455, 3640, doi: [`10.1093/mnras/stv2559`](https://doi.org/10.1093/mnras/stv2559)

(ref: smithr09) Smith, R. J., Longmore, S., & Bonnell, I. 2009, MNRAS, 400, 1775, doi: [`10.1111/j.1365-2966.2009.15621.x`](https://doi.org/10.1111/j.1365-2966.2009.15621.x)

(ref: svoboda16) Svoboda, B. E., Shirley, Y. L., Battersby, C., et al. 2016, ApJ, 822, 59, doi: [`10.3847/0004-637X/822/2/59`](https://doi.org/10.3847/0004-637X/822/2/59)

(ref: tan14) Tan, J. C., Beltrán, M. T., Caselli, P., et al. 2014, Protostars and Planets VI, 149, doi: [`10.2458/azu_uapress_9780816531240-ch007`](https://doi.org/10.2458/azu_uapress_9780816531240-ch007)

(ref: tan13) Tan, J. C., Kong, S., Butler, M. J., Caselli, P., & Fontani, F. 2013, ApJ, 779, 96, doi: [`10.1088/0004-637X/779/2/96`](https://doi.org/10.1088/0004-637X/779/2/96)

(ref: tan16) Tan, J. C., Kong, S., Zhang, Y., et al. 2016, ApJL, 821, L3, doi: [`10.3847/2041-8205/821/1/L3`](https://doi.org/10.3847/2041-8205/821/1/L3)

(ref: teixeira16) Teixeira, P. S., Takahashi, S., Zapata, L. A., & Ho, P. T. P. 2016, A&A, 587, A47, doi: [`10.1051/0004-6361/201526807`](https://doi.org/10.1051/0004-6361/201526807)

(ref: astropy18) The Astropy Collaboration, Price-Whelan, A. M., Sipőcz, B. M., et al. 2018, AJ, 156, 123, doi: [`10.3847/1538-3881/aabc4f`](https://doi.org/10.3847/1538-3881/aabc4f)

(ref: traficante17) Traficante, A., Fuller, G. A., Billot, N., et al. 2017, MNRAS, 470, 3882, doi: [`10.1093/mnras/stx1375`](https://doi.org/10.1093/mnras/stx1375)

(ref: traficante15) Traficante, A., Fuller, G. A., Peretto, N., Pineda, J. E., & Molinari, S. 2015, MNRAS, 451, 3089, doi: [`10.1093/mnras/stv1158`](https://doi.org/10.1093/mnras/stv1158)

(ref: veneziani13) Veneziani, M., Elia, D., Noriega-Crespo, A., et al. 2013, A&A, 549, A130, doi: [`10.1051/0004-6361/201219570`](https://doi.org/10.1051/0004-6361/201219570)

(ref: wangk12) Wang, K., Zhang, Q., Wu, Y., Li, H.-b., & Zhang, H. 2012, ApJL, 745, L30, doi: [`10.1088/2041-8205/745/2/L30`](https://doi.org/10.1088/2041-8205/745/2/L30)

(ref: wangk11) Wang, K., Zhang, Q., Wu, Y., & Zhang, H. 2011, ApJ, 735, 64, doi: [`10.1088/0004-637X/735/1/64`](https://doi.org/10.1088/0004-637X/735/1/64)

(ref: wangk14) Wang, K., Zhang, Q., Testi, L., et al. 2014, MNRAS, 439, 3275, doi: [`10.1093/mnras/stu127`](https://doi.org/10.1093/mnras/stu127)

(ref: wangp10) Wang, P., Li, Z.-Y., Abel, T., & Nakamura, F. 2010, ApJ, 709, 27, doi: [`10.1088/0004-637X/709/1/27`](https://doi.org/10.1088/0004-637X/709/1/27)

(ref: wangy06) Wang, Y., Zhang, Q., Rathborne, J. M., Jackson, J., & Wu, Y. 2006, ApJL, 651, L125, doi: [`10.1086/508939`](https://doi.org/10.1086/508939)

(ref: weingartner01) Weingartner, J. C., & Draine, B. T. 2001, ApJ, 548, 296, doi: [`10.1086/318651`](https://doi.org/10.1086/318651)

(ref: whitworth01) Whitworth, A. P., & Ward-Thompson, D. 2001, ApJ, 547, 317, doi: [`10.1086/318373`](https://doi.org/10.1086/318373)

(ref: wienen12) Wienen, M., Wyrowski, F., Schuller, F., et al. 2012, A&A, 544, A146, doi: [`10.1051/0004-6361/201118107`](https://doi.org/10.1051/0004-6361/201118107)

(ref: williams94) Williams, J. P., de Geus, E. J., & Blitz, L. 1994, ApJ, 428, 693, doi: [`10.1086/174279`](https://doi.org/10.1086/174279)

(ref: young05) Young, C. H., & Evans, II, N. J. 2005, ApJ, 627, 293, doi: [`10.1086/430436`](https://doi.org/10.1086/430436)

(ref: yuan17) Yuan, J., Wu, Y., Ellingsen, S. P., et al. 2017, ApJS, 231, 11, doi: [`10.3847/1538-4365/aa7204`](https://doi.org/10.3847/1538-4365/aa7204)

(ref: zhang11) Zhang, Q., & Wang, K. 2011, ApJ, 733, 26, doi: [`10.1088/0004-637X/733/1/26`](https://doi.org/10.1088/0004-637X/733/1/26)

(ref: zhang15) Zhang, Q., Wang, K., Lu, X., & Jiménez-Serra, I. 2015, ApJ, 804, 141, doi: [`10.1088/0004-637X/804/2/141`](https://doi.org/10.1088/0004-637X/804/2/141)

(ref: zhang09) Zhang, Q., Wang, Y., Pillai, T., & Rathborne, J. 2009, ApJ, 696, 268, doi: [`10.1088/0004-637X/696/1/268`](https://doi.org/10.1088/0004-637X/696/1/268)

(ref: zhangy14) Zhang, Y., Tan, J. C., & Hosokawa, T. 2014, ApJ, 788, 166, doi: [`10.1088/0004-637X/788/2/166`](https://doi.org/10.1088/0004-637X/788/2/166)

# Example CO outflow analysis

The $J = 2 \rightarrow 1$ image cubes show complex emission structures that complicate the identification of coherent velocity structures such as outflows. Effects may be observed from spatial filtering, foreground and background clouds, and strong self-absorption at the clump systemic velocities. Bipolar outflows with red- and blue-shifted velocity components may still be easily observed in the data however because they are bright and are coherent in velocity over many independent channels. To illustrate these effects, we present a spatially averaged spectrum and position-velocity diagram (PV; Fig. [14](#fig:PvDiagramSpectrum)) for the prominent NW-SE outflow originating from G24051 S4 (see Fig. [7](#fig:CoOutflowMosaic)). The spectrum and PV diagram are extracted from a $6.0\ensuremath{''}$ diameter rectangular aperture centered along the outflow axis. Figure [14](#fig:PvDiagramSpectrum) shows bright, extended emission spanning up to $\sim\! \SI{20}{km~s\ensuremath{^{-1}}}$ from the center LSR velocity of $v_\mathrm{lsr} = \SI{83}{km~s\ensuremath{^{-1}}}$ determined from the dense gas tracer $3_{0,3} \rightarrow 2_{0,2}$. The red-shifted lobe (SE) and blue-shifted lobe (NW) are clearly observed in the PV diagram at negative and positive angular offsets along the rectangular aperture axis.

![](fig_pv_diagram_ex_merged.pdf)

#  $J=5\rightarrow4$ maps

Maps of the $J=5\rightarrow4$ red- and blue-shifted integrated intensities are shown in Figure [15](#fig:SiOOutflowMosaic). Three clumps have clear bipolar outflows: G24051 S5, G28565 S1, and G29601 S1. All three outflows have CO $J=2\rightarrow1$ counterparts at similar positions and velocities.

![](fig_T30912_joint_sio_outflow_mosaic_v2_cb.pdf)

# Core Model Properties

We follow a similar approach to modeling starless cores as found in (cite: shirley05) and (cite: lippok16). A similar approach is also used in (cite: mcguire16). We assume dust opacities $\kappa$ for coagulated grains and thin ice mantles in (cite: ossenkopf94) ((cite: ossenkopf94), hereafter ) for moderately processed grains with a coagulation timescale of  × 10^5^ yr at densities between  × 10^4^ cm^−3^– × 10^8^ cm^−3^ (i.e. “OH4” through “OH6”). The coagulation density $n_\mathrm{cg}$ from is selected for each model core based on whether the mean density (weighted by mass) is in the range $0.5 \times n_\mathrm{cg} - 5 \times n_\mathrm{cg}$. The value of the dust opacity when interpolated at $\lambda = \SI{1.3}{mm}$ for  × 10^5^ cm^−3^ (“OH5a”) is $\kappa = \SI{0.90}{cm^2.g^{-1}}$ and varies between 0.51 cm^2^ g^−1^–1.11 cm^2^ g^−1^ over the full range of densities. We calculate total the gas mass using a dust-to-gas mass ratio of $f_\mathrm{d} \equiv m_\mathrm{d} / m_\mathrm{g} = 1/110$ and an ISM mean molecular weight of $\mu = 2.33$. To fully sample the spectral range of the ISRF we extrapolate the the dust opacities from 1 μm to 90 nm using the prescription of (cite: cardelli89) and from 1.3 mm to 10 mm using the power law $\kappa_\nu \propto \nu^\beta$ with $\beta = 1.75$. In addition, scattering efficiencies for the the models are added following (cite: young05) and albedos from the (cite: weingartner01) WD3.1 model.

The Plummer-like density profile in Eq. ([\[eq:Plummer\]](#eq:Plummer)) is then irradiated in `RADMC-3D`  with an external source input using the spectral energy distribution of the ISRF for a self-consistent calculation of the dust temperature distribution. We use the (cite: black94) ISRF spectrum as parametrized by (cite: hocuk17) with the UV portion of the spectrum adopted from (cite: draine78). The ISRF is then varied in relative strength from the local value of the solar neighborhood by a multiplicative factor $s_\mathrm{isrf}$, excluding the contribution from the CMB. Figure [16](#fig:ModelMassIsrf)a shows the ISRF specific intensity $J_\nu$ for $\ensuremath{
    s_\mathrm{isrf}
}= 10^0$,  × 10^1^, and  × 10^2^ with the five parametrized components clearly visible. Models are computed on a 1D radial grid from 2.5 × 10^2^ au–6.0 × 10^4^ au with 100 zones with 2 × 10^6^ photons to ensure convergence in the output $T_\mathrm{dust}$ profiles over the tested range in $n_\mathrm{H}$. The median core mass $M_\mathrm{core}$ integrated out a radius of 2 × 10^4^ au is $\sim \! \SI{1}{\ensuremath{
    \mathit{M}_\odot
}}$ with the $(25,75)$ percentile interval ranging between 0.2 $\mathit{M}_\odot$–10 $\mathit{M}_\odot$, extending to $> \SI{100}{\ensuremath{
    \mathit{M}_\odot
}}$ at the 92 percentile. Figure [17](#fig:AllModelProfiles) shows the distributions of radial profiles in $n_\mathrm{H}(r)$, $T_\mathrm{dust}(r)$, and $S_\mathrm{1.3mm}(\theta)$ at a fiducial distance of 4 kpc. The typical $n_\mathrm{H}$ at $r = \SI{10}{kau}$ range from $n_\mathrm{H} = \num{8e2}-\SI{3e5}{cm^{-3}}$ and have typical central $T_\mathrm{dust} = 7-\SI{20}{K}$, with the maximum central $T_\mathrm{dust} = \SI{35}{K}$.

![image](fig_isrf.pdf)\
![image](fig_mass_histogram.pdf)

![image](fig_dust_densities.pdf)\
![image](fig_dust_temperatures.pdf)\
![image](fig_brightness_profiles.pdf)

|  |  |  |  |  |  |  |
|:---|---:|---:|:---|:---|---:|---:|
| Name | $\ell$ | $b$ | $\alpha$ (ICRS) | $\delta$ (ICRS) | $v_{\rm lsr}$ | BGPS ID$^{a}$ |
|  | (deg) | (deg) | (h:m:s) | (d:m:s) | (km s^−1^) |  |
| G22695 | 22.695381 | -0.454657 | 18:34:14.58 | -09:18:35.84 | 77.80 | 3686 |
| G23297 | 23.297388 | 0.055330 | 18:33:32.06 | -08:32:26.27 | 55.00 | 3822 |
| G23481 | 23.479544 | -0.534764 | 18:35:59.56 | -08:39:02.53 | 63.80 | 3892 |
| G23605 | 23.605390 | 0.181325 | 18:33:39.40 | -08:12:33.24 | 87.00 | 3929 |
| G24051 | 24.051381 | -0.214655 | 18:35:54.40 | -07:59:44.60 | 81.10 | 4029 |
| G28539 | 28.538652 | -0.270358 | 18:44:22.60 | -04:01:57.70 | 88.60 | 4732 |
| G28565 | 28.527846 | -0.252172 | 18:44:17.52 | -04:02:02.40 | 87.46 | 4729 |
| G29558 | 29.557855 | 0.185321 | 18:44:37.07 | -02:55:04.40 | 79.72 | 5021 |
| G29601 | 29.604891 | -0.576768 | 18:47:25.20 | -03:13:26.04 | 75.78 | 5030 |
| G30120 | 30.119855 | -1.146674 | 18:50:23.54 | -03:01:31.58 | 65.31 | 5114 |
| G30660 | 30.657875 | 0.044680 | 18:47:07.76 | -02:00:12.17 | 80.20 | 5265 |
| G30912 | 30.913113 | 0.720803 | 18:45:11.28 | -01:28:03.72 | 50.74 | 5360 |

: Target Positions

Table notes: ($^{a}$) Catalog ID number in the BGPS v2.1.0 (cite: ginsburg13).

|        |            |                      |                      |                |
|:-------|-----------:|---------------------:|---------------------:|---------------:|
| Name   |  $d_\odot$ | $\Sigma_\mathrm{pk}$ |      $M_\mathrm{cl}$ | $T_\mathrm{K}$ |
|        |      (kpc) |           (g cm^−2^) | ($\mathit{M}_\odot$) |          \(K\) |
| G22695 | 4450 (190) |       0.0580 (0.013) |            930 (110) |   14.70 (0.42) |
| G23297 | 3480 (281) |       0.0760 (0.019) |            420 ( 85) |   11.73 (0.41) |
| G23481 | 3780 (220) |       0.1100 (0.024) |            760 (120) |   11.29 (0.14) |
| G23605 | 4800 (240) |       0.0370 (0.015) |            880 (260) |      ... (...) |
| G24051 | 4490 (210) |       0.0790 (0.015) |            760 (110) |   11.87 (0.37) |
| G28539 | 4780 (220) |       0.1280 (0.011) |           3610 (360) |   12.38 (0.14) |
| G28565 | 4680 (200) |       0.0830 (0.019) |            910 (220) |      ... (...) |
| G29558 | 4370 (240) |       0.0690 (0.014) |            590 ( 86) |   12.11 (0.17) |
| G29601 | 4270 (280) |       0.0900 (0.018) |            660 (130) |   15.98 (0.27) |
| G30120 | 3680 (260) |       0.0750 (0.031) |            820 (160) |   14.12 (0.15) |
| G30660 | 4410 (240) |       0.0770 (0.019) |           1380 (360) |      ... (...) |
| G30912 | 2980 (250) |       0.0990 (0.019) |            450 ( 88) |   11.67 (0.12) |

: Clump Physical Properties

Table notes: Uncertainties are reported as the MAD in parentheses. Properties are taken from (cite: svoboda16), except for mass measurements of G29601 and G30912 which are taken from (cite: traficante15).

|     |            |     |           |                   |            |                   |
|:----|-----------:|----:|----------:|------------------:|-----------:|------------------:|
| SPW | Cen. Freq. | $N$ | Bandwidth |         Bandwidth | $\Delta f$ |        $\Delta v$ |
|     |      (GHz) |     |     (kHz) | ($\mathrm{km/s}$) |      (kHz) | ($\mathrm{km/s}$) |
| 1   | 216.112580 | 960 |  468750.0 |           650.252 |     488.28 |             0.677 |
| 2   | 217.104980 | 960 |  468750.0 |           647.280 |     488.28 |             0.674 |
| 3   | 218.222192 | 480 |  117187.2 |           160.991 |     244.14 |             0.335 |
| 4   | 218.475632 | 480 |  117187.2 |           160.804 |     244.14 |             0.335 |
| 5   | 218.760066 | 480 |  117187.2 |           160.595 |     244.14 |             0.335 |
| 6   | 219.560358 | 240 |  117187.2 |           160.010 |     488.28 |             0.667 |
| 7   | 230.538000 | 960 |  468750.0 |           609.564 |     488.28 |             0.635 |
| 8   | 231.321828 | 960 |  468750.0 |           607.499 |     488.28 |             0.632 |
| 9   | 233.820000 | 128 | 2000000.0 |          2564.301 |   15625.00 |            20.033 |

: ALMA Correlator Configuration

Table notes: Column descriptions: (1) Spectral window (SPW) ID number, (2) Center frequency of SPW in the rest frame, (3) Number of channels, (4,5) SPW total bandwidth, (6,7) SPW channel resolution. Uncertainties are given in parentheses.

|  |  |  |  |  |  |  |
|:---|:--:|---:|---:|:--:|:--:|---:|
| Specie | Transition | Rest Freq. | $E_\mathrm{u}/k$ | Ref. | SPW | $\Delta v$ |
|  |  | (GHz) | \(K\) |  |  | ($\mathrm{km/s}$) |
|  | $3 \rightarrow 2$ | 216.1125800 | 20.74 | \(1\) | 1 | 0.68 |
| c- | $3_{3,0} \rightarrow 2_{2,1}$ | 216.2787560 | 19.47 | \(1\) | 1 | 0.68 |
|  | $5 \rightarrow 4$ | 217.1049800 | 31.26 | \(1\) | 2 | 0.68 |
|  | $3 \rightarrow 2$ | 217.2385378 | 20.85 | \(2\) | 2 | 0.68 |
| p- | $3_{0,3} \rightarrow 2_{0,2}$ | 218.2221920 | 20.96 | \(1\) | 3 | 0.34 |
| p- | $3_{2,2} \rightarrow 2_{2,1}$ | 218.4756320 | 68.09 | \(1\) | 4 | 0.34 |
|  | $4_{2,2} \rightarrow 3_{1,2}$ | 218.4400500 | 45.46 | \(1\) | 4 | 0.34 |
| p- | $3_{2,1} \rightarrow 2_{2,0}$ | 218.7600660 | 68.11 | \(1\) | 5 | 0.34 |
|  | $2 \rightarrow 1$ | 219.5603580 | 15.81 | \(1\) | 6 | 0.68 |
|  | $2 \rightarrow 1$ | 230.5380000 | 16.60 | \(1\) | 7 | 0.68 |
|  | $3 \rightarrow 2$ | 231.3218283 | 22.20 | \(2\) | 8 | 0.68 |

: Spectral Line Transition Properties

Table notes: Transition property reference key: (1) SLAIM, (2) CDMS.

|  |  |  |  |  |  |  |  |  |  |  |  |  |
|:---|:---|:---|:---|---:|---:|---:|---:|---:|---:|---:|:--:|:--:|
| Name | ID | $\alpha$ (ICRS) | $\delta$ (ICRS) | $\Omega_\mathrm{c}$ | $a$ | $b$ | PA | $S_\nu$ | $\delta S_\nu$ | $S_{\nu,\mathrm{pk}}$ | CO | SiO |
|  |  | (h:m:s) | (d:m:s) | (as^2^) | (as) | (as) | (deg) | (mJy) | (mJy) | (mJy/bm) |  |  |
| G22695 | 1 | 18:34:13.7336 | -09:18:36.6910 | 9.30 | 2.597 | 1.213 | 146.0 | 17.284 | 0.109 | 6.414 | 1 |  |
| G22695 | 2 | 18:34:14.6345 | -09:18:44.6915 | 16.54 | 3.022 | 1.976 | 126.1 | 9.083 | 0.196 | 1.518 |  |  |
| G22695 | 3 | 18:34:14.0405 | -09:18:33.7904 | 7.17 | 2.256 | 1.444 | 135.6 | 5.348 | 0.133 | 0.737 |  |  |
| G23297 | 1 | 18:33:32.1419 | -08:32:25.9306 | 22.70 | 7.853 | 1.461 | 85.5 | 16.431 | 0.309 | 0.727 |  |  |
| G23297 | 2 | 18:33:31.6164 | -08:32:29.2777 | 2.79 | 1.055 | 0.870 | 72.4 | 11.515 | 0.088 | 6.381 | 2 |  |
| G23297 | 3 | 18:33:32.1439 | -08:32:34.3684 | 6.86 | 3.124 | 1.180 | 61.9 | 5.699 | 0.130 | 0.925 |  |  |
| G23297 | 4 | 18:33:32.3527 | -08:32:38.5247 | 3.77 | 1.880 | 0.911 | 94.0 | 4.139 | 0.066 | 1.906 | 1 |  |
| G23297 | 5 | 18:33:31.5694 | -08:32:30.9485 | 0.86 | 0.692 | 0.488 | 148.8 | 2.542 | 0.045 | 3.026 |  |  |
| G23297 | 6 | 18:33:31.9659 | -08:32:27.1673 | 2.29 | 1.161 | 0.784 | 107.4 | 1.740 | 0.097 | 0.893 |  |  |
| G23297 | 7 | 18:33:31.6280 | -08:32:22.9146 | 3.53 | 1.982 | 0.798 | 88.6 | 1.645 | 0.099 | 0.472 |  |  |
| G23481 | 1 | 18:35:59.8961 | -08:39:08.0500 | 2.68 | 0.998 | 0.853 | -164.0 | 3.514 | 0.085 | 2.311 |  |  |
| G23481 | 2 | 18:35:59.7404 | -08:39:07.8724 | 3.04 | 1.464 | 0.758 | -137.0 | 2.647 | 0.098 | 1.282 | 1 |  |
| G23481 | 3 | 18:35:59.9838 | -08:38:48.7847 | 3.02 | 1.513 | 0.806 | 176.9 | 2.529 | 0.046 | 1.263 |  |  |
| G23481 | 4 | 18:35:59.4861 | -08:39:01.0450 | 2.56 | 0.962 | 0.702 | 176.2 | 2.265 | 0.103 | 2.030 |  |  |
| G23481 | 5 | 18:35:59.3916 | -08:39:05.8982 | 5.46 | 4.296 | 0.681 | -153.8 | 1.920 | 0.142 | 0.385 |  |  |
| G23605 | 1 | 18:33:39.9726 | -08:12:39.4169 | 1.88 | 0.938 | 0.651 | 177.4 | 1.371 | 0.058 | 1.197 |  |  |
| G24051 | 1 | 18:35:54.1219 | -07:59:53.4130 | 13.49 | 2.213 | 1.980 | -168.1 | 12.535 | 0.164 | 5.085 |  |  |
| G24051 | 2 | 18:35:55.0045 | -07:59:35.7741 | 8.14 | 3.347 | 0.969 | 112.6 | 6.905 | 0.100 | 1.108 |  |  |
| G24051 | 3 | 18:35:53.9805 | -07:59:58.0198 | 7.95 | 2.563 | 1.491 | 155.0 | 6.397 | 0.077 | 0.924 |  |  |
| G24051 | 4 | 18:35:54.4771 | -07:59:41.2910 | 11.24 | 3.038 | 1.379 | -176.6 | 5.844 | 0.207 | 1.192 | 1 |  |
| G24051 | 5 | 18:35:54.5839 | -07:59:52.2422 | 4.87 | 1.920 | 1.103 | -148.3 | 5.500 | 0.111 | 1.810 | 1 | 1 |
| G24051 | 6 | 18:35:54.9096 | -07:59:40.4092 | 4.36 | 1.417 | 1.011 | 150.3 | 3.820 | 0.100 | 2.154 |  | 1 |
| G24051 | 7 | 18:35:54.4693 | -07:59:49.2862 | 4.14 | 1.641 | 0.987 | 62.3 | 3.810 | 0.120 | 1.044 |  |  |
| G24051 | 8 | 18:35:54.8945 | -07:59:42.6850 | 3.87 | 1.813 | 0.959 | 154.2 | 1.911 | 0.102 | 0.612 |  |  |
| G24051 | 9 | 18:35:54.3071 | -07:59:43.7882 | 1.42 | 1.354 | 0.487 | 68.1 | 1.057 | 0.076 | 0.643 |  |  |
| G24051 | 10 | 18:35:54.3750 | -07:59:45.8972 | 1.44 | 1.396 | 0.454 | 55.4 | 1.045 | 0.077 | 0.645 |  |  |
| G24051 | 11 | 18:35:54.8697 | -07:59:51.3991 | 1.47 | 1.060 | 0.555 | 135.5 | 0.659 | 0.054 | 0.506 |  |  |
| G28539 | 1 | 18:44:22.2420 | -04:01:44.7142 | 16.35 | 6.175 | 1.334 | 45.3 | 19.114 | 0.121 | 1.842 |  |  |
| G28539 | 2 | 18:44:22.7348 | -04:01:56.1668 | 8.58 | 2.585 | 1.671 | 73.6 | 5.411 | 0.183 | 0.711 |  |  |
| G28539 | 3 | 18:44:22.8536 | -04:02:03.2640 | 12.63 | 4.346 | 2.086 | 46.9 | 4.587 | 0.191 | 0.439 |  |  |
| G28539 | 4 | 18:44:22.3397 | -04:01:54.0246 | 7.39 | 2.372 | 1.682 | 130.3 | 4.055 | 0.156 | 0.603 |  |  |
| G28539 | 5 | 18:44:22.8195 | -04:02:07.5292 | 2.36 | 1.403 | 0.682 | 80.2 | 1.249 | 0.064 | 0.526 |  |  |
| G28539 | 6 | 18:44:22.7434 | -04:01:53.8880 | 1.41 | 0.930 | 0.656 | 169.0 | 0.842 | 0.070 | 0.551 |  |  |
| G28565 | 1 | 18:44:17.2674 | -04:02:03.5257 | 14.00 | 3.641 | 2.023 | 79.3 | 17.943 | 0.226 | 2.499 | 1 | 1 |
| G28565 | 2 | 18:44:16.9912 | -04:02:01.1285 | 3.52 | 2.395 | 0.776 | 89.0 | 3.894 | 0.093 | 0.946 |  |  |
| G28565 | 3 | 18:44:17.2241 | -04:02:08.5328 | 2.60 | 1.532 | 0.830 | 78.1 | 3.604 | 0.083 | 1.443 |  |  |
| G28565 | 4 | 18:44:17.1101 | -04:02:09.7546 | 3.33 | 1.914 | 0.810 | 62.9 | 3.087 | 0.082 | 0.827 |  |  |
| G28565 | 5 | 18:44:17.0529 | -04:01:58.7236 | 1.87 | 1.082 | 0.690 | 143.2 | 2.401 | 0.069 | 1.347 |  |  |
| G28565 | 6 | 18:44:17.3596 | -04:02:06.5025 | 1.47 | 0.935 | 0.670 | 109.7 | 1.561 | 0.071 | 0.903 |  |  |
| G29558 | 1 | 18:44:37.5015 | -02:55:12.4812 | 20.09 | 2.432 | 2.174 | -146.5 | 20.697 | 0.184 | 6.613 |  |  |
| G29558 | 2 | 18:44:37.3029 | -02:55:01.9117 | 4.83 | 1.372 | 1.029 | 161.9 | 10.569 | 0.130 | 4.941 | 1 |  |
| G29558 | 3 | 18:44:37.5338 | -02:55:00.8673 | 3.41 | 1.524 | 0.742 | 171.2 | 6.624 | 0.093 | 3.588 | 1 |  |
| G29558 | 4 | 18:44:36.6483 | -02:55:02.6587 | 4.40 | 1.548 | 1.109 | 134.4 | 4.624 | 0.114 | 1.666 |  |  |
| G29558 | 5 | 18:44:37.0267 | -02:55:08.7202 | 6.09 | 2.893 | 1.085 | 125.8 | 1.881 | 0.146 | 0.332 |  |  |
| G29558 | 6 | 18:44:37.8020 | -02:55:10.4118 | 3.46 | 1.516 | 1.090 | 125.5 | 1.810 | 0.065 | 0.681 |  |  |
| G29558 | 7 | 18:44:36.6640 | -02:55:00.1446 | 1.87 | 0.937 | 0.766 | 176.3 | 1.688 | 0.070 | 1.116 |  |  |
| G29558 | 8 | 18:44:36.6775 | -02:54:57.2062 | 3.91 | 1.871 | 1.128 | 171.4 | 1.626 | 0.090 | 0.472 |  |  |
| G29558 | 9 | 18:44:37.1252 | -02:55:04.1785 | 2.00 | 1.141 | 0.739 | 45.8 | 1.357 | 0.090 | 0.584 |  |  |
| G29601 | 1 | 18:47:25.3865 | -03:13:29.3698 | 16.05 | 2.547 | 1.728 | 79.6 | 15.771 | 0.240 | 6.686 | 2 | 1 |
| G29601 | 2 | 18:47:25.3644 | -03:13:20.3497 | 4.94 | 1.908 | 1.077 | -140.3 | 2.192 | 0.123 | 0.567 |  |  |
| G29601 | 3 | 18:47:25.3951 | -03:13:23.8223 | 4.15 | 2.104 | 0.976 | 78.6 | 1.751 | 0.124 | 0.501 |  |  |
| G29601 | 4 | 18:47:25.5623 | -03:13:24.6212 | 1.69 | 0.999 | 0.716 | 151.3 | 0.541 | 0.074 | 0.341 |  |  |
| G30120 | 1 | 18:50:24.7282 | -03:01:27.2884 | 1.38 | 0.820 | 0.683 | 147.5 | 3.924 | 0.020 | 2.709 | 1 |  |
| G30120 | 2 | 18:50:24.7785 | -03:01:26.1411 | 0.93 | 0.737 | 0.548 | 53.8 | 2.868 | 0.014 | 2.807 |  |  |
| G30120 | 3 | 18:50:22.9654 | -03:01:43.6061 | 1.61 | 0.912 | 0.680 | -137.5 | 1.232 | 0.034 | 0.854 |  |  |
| G30660 | 1 | 18:47:07.7985 | -02:00:24.1287 | 27.58 | 5.270 | 2.513 | 66.2 | 15.430 | 0.191 | 0.902 |  |  |
| G30660 | 2 | 18:47:08.0553 | -02:00:09.6124 | 14.88 | 2.912 | 2.347 | 178.5 | 8.489 | 0.224 | 2.140 |  |  |
| G30660 | 3 | 18:47:07.8433 | -02:00:04.5482 | 18.40 | 4.397 | 2.139 | 142.3 | 8.257 | 0.219 | 1.318 |  |  |
| G30660 | 4 | 18:47:07.4677 | -01:59:58.7398 | 11.09 | 3.618 | 1.832 | 52.6 | 7.588 | 0.095 | 0.984 |  |  |
| G30660 | 5 | 18:47:07.6647 | -02:00:11.1585 | 11.19 | 2.859 | 1.779 | 53.0 | 5.183 | 0.210 | 0.812 |  |  |
| G30660 | 6 | 18:47:07.3910 | -02:00:09.7055 | 8.59 | 2.296 | 1.622 | 119.3 | 4.896 | 0.162 | 1.128 |  |  |
| G30912 | 1 | 18:45:11.4745 | -01:28:04.9508 | 44.25 | 4.523 | 3.651 | 51.0 | 27.344 | 0.403 | 2.728 | 1 |  |
| G30912 | 2 | 18:45:11.1447 | -01:28:02.2048 | 12.95 | 2.595 | 1.372 | 124.9 | 9.536 | 0.224 | 4.324 | 2 |  |
| G30912 | 3 | 18:45:11.9211 | -01:27:55.2127 | 4.29 | 2.778 | 0.976 | 151.1 | 2.249 | 0.069 | 0.682 |  |  |
| G30912 | 4 | 18:45:11.4095 | -01:27:58.6881 | 4.05 | 2.365 | 1.096 | -161.7 | 1.498 | 0.114 | 0.430 |  |  |
| G30912 | 5 | 18:45:10.5824 | -01:28:11.8467 | 1.53 | 0.820 | 0.629 | 179.5 | 1.399 | 0.039 | 1.353 |  |  |
| G30912 | 6 | 18:45:10.9468 | -01:28:09.9788 | 0.83 | 0.600 | 0.516 | 168.0 | 0.360 | 0.045 | 0.518 |  |  |

: Core Observed Properties

Table notes: Column descriptions: (1) Target clump name, (2) sub-structure ID number, (3) centroid right ascension coordinate, (4) centroid declination coordinate, (5) total dendrogram area, (6) Gaussian major FWHM, (7) Gaussian minor FWHM, (8) Gaussian position angle, (9) source integrated 1.3 mm flux density, (10) uncertainty in source integrated flux density, (11) source peak flux density, (12) number of bipolar CO outflows, (13) number of bipolar SiO outflows.

+--------+--------+------+-------------------------------------------------------+------+-----------------------------------------+------+-------------------------------------------------------------------------------+------+--------------------------------+
| Name   | Cont.  | $\,$ | Deuteration                                           | $\,$ | Kinematic                               | $\,$ | High-Excitation                                                               | $\,$ | Outflow                        |
+:======:+:======:+:====:+:================:+:==============:+:=================:+:====:+:==================:+:==================:+:====:+:================:+:================:+:===================:+:=================:+:====:+:=============:+:==============:+
| 4-6    | 1.3 mm |      | $\mathrm{DCO^+}$ | $\mathrm{DCN}$ | $\mathrm{N_2D^+}$ |      | $\mathrm{C^{18}O}$ | $\mathrm{H_2CO}^b$ |      | $\mathrm{H_2CO}$ | $\mathrm{H_2CO}$ | c-$\mathrm{C_3H_2}$ | $\mathrm{CH_3OH}$ |      | $\mathrm{CO}$ | $\mathrm{SiO}$ |
+--------+--------+------+------------------+----------------+-------------------+------+--------------------+--------------------+------+------------------+------------------+---------------------+-------------------+------+---------------+----------------+
| G28539 | **D**  |      | **W**            | **W**          | **N**             |      | **D**              | **D**              |      | **N**            | **W**            | **N**               | **W**             |      | **D**         | **D**          |
+--------+--------+------+------------------+----------------+-------------------+------+--------------------+--------------------+------+------------------+------------------+---------------------+-------------------+------+---------------+----------------+
| G30660 | **D**  |      | **D**            | **N**          | **N**             |      | **D**              | **D**              |      | **W**            | **W**            | **D**               | **D**             |      | **D**         | **D**          |
+--------+--------+------+------------------+----------------+-------------------+------+--------------------+--------------------+------+------------------+------------------+---------------------+-------------------+------+---------------+----------------+
| G22695 | **D**  |      | **W**            | **W**          | **N**             |      | **D**              | **D**              |      | **D**            | **D**            | **N**               | **D**             |      | **B**         | **D**          |
+--------+--------+------+------------------+----------------+-------------------+------+--------------------+--------------------+------+------------------+------------------+---------------------+-------------------+------+---------------+----------------+
| G23605 | **D**  |      | **N**            | **N**          | **N**             |      | **D**              | **D**              |      | **N**            | **W**            | **N**               | **W**             |      | **D**         | **N**          |
+--------+--------+------+------------------+----------------+-------------------+------+--------------------+--------------------+------+------------------+------------------+---------------------+-------------------+------+---------------+----------------+
| G24051 | **D**  |      | **D**            | **D**          | **D**             |      | **D**              | **D**              |      | **D**            | **W**            | **D**               | **D**             |      | **B**         | **B**          |
+--------+--------+------+------------------+----------------+-------------------+------+--------------------+--------------------+------+------------------+------------------+---------------------+-------------------+------+---------------+----------------+
| G23297 | **D**  |      | **D**            | **D**          | **W**             |      | **D**              | **D**              |      | **D**            | **D**            | **W**               | **D**             |      | **B**         | **D**          |
+--------+--------+------+------------------+----------------+-------------------+------+--------------------+--------------------+------+------------------+------------------+---------------------+-------------------+------+---------------+----------------+
| G23481 | **D**  |      | **N**            | **N**          | **N**             |      | **D**              | **D**              |      | **D**            | **D**            | **N**               | **D**             |      | **B**         | **W**          |
+--------+--------+------+------------------+----------------+-------------------+------+--------------------+--------------------+------+------------------+------------------+---------------------+-------------------+------+---------------+----------------+
| G29558 | **D**  |      | **D**            | **W**          | **D**             |      | **D**              | **D**              |      | **D**            | **D**            | **D**               | **D**             |      | **B**         | **D**          |
+--------+--------+------+------------------+----------------+-------------------+------+--------------------+--------------------+------+------------------+------------------+---------------------+-------------------+------+---------------+----------------+
| G30120 | **W**  |      | **N**            | **N**          | **N**             |      | **D**              | **W**              |      | **N**            | **N**            | **N**               | **W**             |      | **B**         | **D**          |
+--------+--------+------+------------------+----------------+-------------------+------+--------------------+--------------------+------+------------------+------------------+---------------------+-------------------+------+---------------+----------------+
| G28565 | **D**  |      | **D**            | **W**          | **D**             |      | **D**              | **D**              |      | **D**            | **D**            | **D**               | **D**             |      | **B**         | **B**          |
+--------+--------+------+------------------+----------------+-------------------+------+--------------------+--------------------+------+------------------+------------------+---------------------+-------------------+------+---------------+----------------+
| G29601 | **D**  |      | **D**            | **W**          | **N**             |      | **D**              | **D**              |      | **D**            | **D**            | **W**               | **D**             |      | **B**         | **B**          |
+--------+--------+------+------------------+----------------+-------------------+------+--------------------+--------------------+------+------------------+------------------+---------------------+-------------------+------+---------------+----------------+
| G30912 | **D**  |      | **D**            | **D**          | **W**             |      | **D**              | **D**              |      | **D**            | **D**            | **W**               | **D**             |      | **B**         | **D**          |
+--------+--------+------+------------------+----------------+-------------------+------+--------------------+--------------------+------+------------------+------------------+---------------------+-------------------+------+---------------+----------------+

: Band 6 Detections$^{a}$

Table notes: (*a*) Detection flags: **D** detection with $\mathrm{SNR} \geq 7\sigma$, **W** weak detection with $5 \sigma \leq \mathrm{SNR} < 7\sigma$, **N** non-detection with $\mathrm{SNR} < 5 \sigma$, and **B** detection of bipolar outflow. (*b*) $\mathrm{H_2CO}$ transitions listed in order of $3_{0,3}-2_{0,2}$, $3_{2,1}-2_{2,0}$, and $3_{2,2}-2_{2,1}$.

[^1]: In this paper we use the term “core” to refer to a dense gas structure that is $\sim\! \SI{0.1}{pc}$ in size and likely to form a single or bound multiple stellar system. Such cores are embedded within larger scale “clumps” that are dense gas structures likely to form a stellar association or cluster, and are $\sim\! \SI{1}{pc}$ in size and $\sim\! \num{e2}-\SI{e4}{\ensuremath{
        \mathit{M}_\odot
    }}$ in mass (cite: bergin07).

[^2]: Data products can be downloaded from <https://irsa.ipac.caltech.edu/data/BOLOCAM_GPS/>

[^3]: <http://www3.mpifr-bonn.mpg.de/div/atlasgal/>

[^4]: <http://apps.canfar.net/storage/list/JPSPR1>

[^5]: (cite: kauffmann10) define the prescription $M \leq \SI{580}{\ensuremath{
        \mathit{M}_\odot
    }} (R / \si{pc})^{1.33}$ for a clump to form high-mass stars. The pre-factor has been scaled for consistency with the dust opacity used in this work. For radius $R = \SI{0.8}{pc}$, this relation yields a mass threshold of $M \approx \SI{430}{\ensuremath{
        \mathit{M}_\odot
    }}$.

[^6]: ALMA is operated by the National Radio Astronomy Observatory, which is a facility of the National Science Foundation, operated under cooperative agreement by Associated Universities, Inc.

[^7]: <http://splatalogue.net>

</paper>

## Items to check

```json
[
 {
  "path": "analysis_steps[3].assumptions[0].evidence[0]",
  "value": "OH5 dust opacity kappa=0.90 cm2/g, dust-to-gas 1/110, mu=2.33, Td(1000 au)=7-13 K selection",
  "failed_quote": "then the range of models are limited to those that resulted in $T_\\mathrm{d}(r = \\SI{1e3}{au}) = 7-\\SI{13}{K}$"
 }
]
```
