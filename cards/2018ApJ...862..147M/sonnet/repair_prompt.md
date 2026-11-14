# Repair task for a Claude Code subagent

A methods card has evidence quotes that were not found verbatim in the paper. Below are the rules, the paper, and the failing items. Write ONE JSON object, nothing else, of the form {"repairs": [{"path": ..., "found": true|false, "loc": ..., "quote": ...}, ...]} with one entry per item (path unchanged) to:

    C:\Users\adama\alma-corpus\cards\2018ApJ...862..147M\sonnet\repair_reply.txt

Use the Write tool for that file. Copy each quote character for character from the paper text below; a returned quote is checked mechanically and dropped if it is not in the paper. Do not read any other file, do not run commands, and do not change anything else. Reply with one line when done.

---

## Rules

You check evidence quotes for a methods card extracted from an astronomy paper. Some quotes could not be found verbatim in the paper text, and some stated values came without a quote. For each item: find the passage in the paper that supports the value and copy it VERBATIM (same words and order, at most 40 words; LaTeX markup may be dropped) with its loc (section heading, "abstract", "Table N" or "Figure N caption"). If the paper does not support the value, return found = false and leave quote and loc empty. Use only the paper text. Return one entry per item, with the item's path unchanged.

## Paper

<paper>
Draft version June 27, 2021
Preprint typeset using L [A] TEX style AASTeX6 v. 1.0


RESOLVED STAR FORMATION EFFICIENCY IN THE ANTENNAE GALAXIES


Allison M. Matthews [1], Kelsey E. Johnson [1], Bradley C. Whitmore [2], Crystal L. Brogan [3], Adam K. Leroy [4], and
Remy Indebetouw [1,3]


1 Department of Astronomy, University of Virginia, P. O. Box 400325 Charlottesville, VA 22904-4325, USA
2 Space Telescope Science Institute (STScI), 3700 San Martin Drive, Baltimore, MD 21218, USA
3 National Radio Astronomy Observatory, 520 Edgemont Rd., Charlottesville, VA 22903, USA 0000-0002-6558-7653
4 Department of Astronomy, The Ohio State University, 140 West 18th Avenue, Columbus, OH 43210, USA 0000-0002-2545-1700


ABSTRACT


We use Atacama Large Millimeter Array CO(3-2) observations in conjunction with optical observations
from the _Hubble_ _Space_ _Telescope_ to determine the ratio of stellar to gas mass for regions in the
Antennae Galaxies. We adopt the term “instantaneous mass ratio” IMR( _t_ ) = _M_ _stars_ _/_ ( _M_ _gas_ + _M_ _stars_ ),
that is equivalent to the star formation efficiency for an idealized system at _t_ = 0. We use two
complementary approaches to determining the IMR( _t_ ) based on 1) the enclosed stellar and molecular
mass within circular apertures centered on optically-identified clusters, and 2) a tessellation algorithm
that defines regions based on CO emission. We find that only a small number of clusters appear to have
IMR(0) = SFE _>_ 0 _._ 2, which suggests that only a small fraction of these clusters will remain bound.
The results suggest that by ages of 10 [6] _[.]_ [7] years, some clusters will have lost all of their associated
molecular gas, and by 10 [7] _[.]_ [5] years this is true for the majority of clusters. There appears to be slight
dependence of the IMR( _t_ ) on the CO surface brightness, which could support the idea that dense
molecular environments are more likely to form bound clusters. However, the IMR( _t_ ) appears to have
a strong dependence on extinction, which likely traces the evolutionary state of clusters.


_Keywords:_ galaxies: clusters: general – galaxies: star formation – galaxies: star clusters: general –
galaxies: individual (NGC 4038/9) – galaxies: interactions – submillimeter: galaxies



1. INTRODUCTION


The efficiency with which stars form in a given environment is a fundamental parameter in our attempts
to understand galaxy evolution throughout cosmic time.
For example, cosmological simulation codes must adopt
values for the stellar mass that will form from a given
region of gas over a specified time period (e.g. Springel
et al. 2005; Vogelsberger et al. 2014). A significant body
of work has been devoted to understanding how star formation efficiency (SFE) depends on various environmental parameters, relating gas phase and surface density
to observed star formation rates (SFRs) (e.g. Kennicutt
1989; Bigiel et al. 2008; Leroy et al. 2008). The set of
factors that ultimately determine the SFE of a system
remains an open issue, although work with increasingly
sophisticated models is providing insight. For example, using the Hyperion code, Raskutti et al. (2016) find
that the SFE of a molecular cloud is strongly increased
by turbulent compression of gas, which is, at least in
principle, observationally testable.
“Star formation efficiency” (SFE) is defined in different ways depending on the astrophysical context. In
extragalactic research, the ratio of the star formation



rate (SFR) to the total gas content (SFE=SFR/ _M_ H2 )
is frequently adopted (e.g. Kirkpatrick et al. 2017; Li
et al. 2017; Young et al. 1996). This definition can
also be thought of as an inverse depletion time. Extragalactic studies frequently observe properties related
to star formation and gas mass over relatively large spatial scales ( _∼_ 1 kpc), which averages over star-forming
regions during multiple phases of their evolution. Another common modern definition of the star formation
efficiency is the ratio of the gravitational free fall time
to the depletion time. This expresses the fraction of
gas mass converted into stars per gravitational free fall
time. It is predicted by many theoretical models and the
low values ≲ 1% found indicate the inefficiency of star
formation compared to free collapse (e.g., see Krumholz
& McKee (2005), McKee & Ostriker (2007), Federrath
& Klessen 2013). Studies that probe smaller size scales
find that the general star formation “laws” derived from
averaging over large scales (and the range of star formation stages) start to break down (e.g. Schruba et al.
2010).
On the other hand, studies of the Milky Way often resolve individual molecular clouds and typically

2


define star formation efficiency as the fraction of
gas mass that has been converted to stellar mass
(SFE= _M_ _stars_ _/_ ( _M_ _gas_ + _M_ _stars_ )). In contrast to extragalactic work, these studies are not averaging over the
full range of stages of star formation, but rather are necessarily focused on the early phases in which molecular
material is still present. Thus, the aim with these resolved studies is not to derive average depletion times,
but rather to determine the total mass in stars that re
sults from a given amount of gas in a localized region.
These Galactic studies typically find values ≲ 30% for
embedded Galactic clusters (e.g. Lada & Lada 2003).
Subsequent work by Evans et al. (2009) and Peterson
et al. (2011) derive even lower values of SFE, deriving
values of _<_ 10% for individual clouds in the Milky Way.
Applying the methods typically used in Galactic studies to systems outside the Local Group has been challenging. Due to observational limitations, studies of extragalactic SFE have typically been limited to nearby
galaxies (≲ 10 Mpc), large spatial scales (≳ 500 pc),
or both. Now with the availability of ALMA observations, it is possible to probe SFE on the same size scale
as that of giant molecular clouds (GMCs) of ≲ 100 pc
(Schinnerer et al. 2013; Leroy et al. 2016). Resolving
size scales of ≲ 50 pc is particularly important for probing the SFE involved in the formation of the so-called
“super star clusters” (SSCs).


1.1. _Super_ _Star_ _Cluster_ _Evolution_


SSCs are the most massive and dense type of stellar
cluster, and represent one of the most extreme modes of
star formation in the universe (O’Connell et al. 1994).
First identified as bright blue knots of star formation
(e.g. Arp & Sandage 1985; Melnick et al. 1985), these
objects are now generally considered to be the precursors to globular clusters (Meurer et al. 1995). However,
various lines of evidence suggest that perhaps as few as
_∼_ 1% of SSCs survive to become globular clusters (Fall
2006; Fall et al. 2005; Fall & Zhang 2001). A number
of factors play a role in determining whether a specific
SSC will survive to become a globular cluster, including stellar feedback, tidal shocks, two-body relaxation,
and tidal truncation (Gnedin & Ostriker 1997). One of
the first criteria that a given SSC must meet to (eventually) evolve into a globular cluster is that it must be
gravitationally bound. Moreover, even if an SSC is originally bound at the time of its formation, if a significant
amount of the binding mass is in the form of gas, the
cluster is likely to become unbound when the gas is removed through stellar feedback. Thus, SFE also has an
important role in the formation and survival of globular
clusters.

The impact of SFE on the evolution and long-term
survival of star clusters has been studied by a number



of authors for a distribution of conditions. For example,
early work by Hills (1980) based on the virial theorem
suggested that some clusters can lose as little as 10% of
their mass (SFE = 90%) and still become unbound after
the gas was lost from the system. The general requirement for high SFEs is supported by Geyer & Burkert
(2001), who suggest that the formation of bound clusters (e.g., globular clusters) requires extremely high star
formation efficiencies of _∼_ 50%.
More recent work using simulations has been able to
study the impact of SFE on cluster evolution using more
sophisticated physical processes. For example, using a
grid of simulations Baumgardt & Kroupa (2007) found
that star clusters can remain bound with SFEs as low
as 10% provided that gas is removed from the clusters
over long timescales. If, however, gas is removed instantaneously, clusters with SFE _<_ 33% did not survive. Subsequent work by Pelupessy & Portegies Zwart
(2012) used simulations of clusters with 1000 stars to explore their dynamical evolution under different scenarios. Their simulations allow for clusters with SFEs as
low as 5% to survive, but as with Baumgardt & Kroupa
(2007), cluster survival is more likely if the gas removal
does not take place during violent quasi-instantaneous
episodes.
Observationally determining the SFE for globular
clusters presents numerous challenges. The first issue
is that with current observing capabilities, it is not
possible to observe the formation of globular clusters
≳ 10 Gyr in the past. Instead, we turn to relatively
nearby objects that are generally considered to be analogous to adolescent globular clusters – super star clusters. The second issue is that determining the SFE requires knowing _both_ the total stellar mass that forms in a
given molecular cloud, and the total mass of the molecular cloud. However, these two properties are largely
mutually exclusive – once stars have formed they will
start disrupting the cloud, and if there is still molecular
material available, additional stars could form. In fact,

whether molecular material can remain or be reintro
duced after the first generation of stars is being investigated by a number of studies. For example, whether
various types of “polluters” (e.g. AGB stars, fast rotating massive stars (FRMS), and massive stars in binary
systems D’Ercole et al. 2008; Renzini 2008; Conroy &
Spergel 2011; Decressin et al. 2009; Krause et al. 2013;
de Mink et al. 2009) was explored by Cabrera-Ziri et al.
(2015) in three young (50-200 Myr) molecular clouds.
They found no evidence of CO(3-2) emission in these
YMCs, placing strong constraints on the various “polluter” scenarios.

This problem can be at least partially mitigated if a
statistically significant sample of SSCs with known ages
is available. In this case, the relative fraction of stellar

and gas mass can be tracked through a cluster’s evolution. In this case, the ratio _M_ _stars_ _/_ ( _M_ _gas_ + _M_ _stars_ )
becomes a function of time, and here we adopt the term
“instantaneous mass ratio” (IMR). The IMR is only
equal to the actual SFE at a time when stars have ceased
forming and the molecular cloud has not been disrupted.
One can debate whether such a time is overly idealized
or actually exists – whether stars have truly stopped
forming, or whether the molecular cloud is not significantly disrupted until star formation has ceased. In any
case, one would predict a trend in which the youngest
SSCs would be associated with the lowest IMR values,
and that as the molecular cloud is destroyed the IMR
should approach unity.


1.2. _The_ _Antennae_


In order to constrain the impact of SFE on cluster
survival through observations, an optimal target will be
relatively nearby (for both sensitivity and resolution limitations), and also host a statistical sample of star clusters. As the closest and youngest example in Toomre’s
1977 sequence of prototypical mergers (Toomre 1977),
the Antennae galaxies (NGC 4038/39) have been a target for multiwavelength observations on the internal
structure of galaxy mergers. The IRAS satellite found
that virtually all extragalactic luminous infrared sources
were mergers (Sanders et al. 1988), making them a prime
laboratory for studying early stages of star formation.
With an infrared luminosity of _L_ _IR_ _∼_ 10 [11] _L_ _⊙_, the Antennae galaxy system is barely classified as a LIRG, but
the vast molecular gas reservoir ( _>_ 10 [10] _M_ _⊙_, Gao et al.
2001; Wilson et al. 2003) suggests that the Antennae
may evolve into a superluminous infrared galaxy as the
merger continues.
With a molecular gas reservoir comparable to that of
an early-stage ULIRG, the Antennae has an abundance
of the ingredients needed for star formation. HST observations have identified _>_ 10 _,_ 000 stellar clusters in
the overlap region alone (Whitmore et al. 2010). The
close distance to the Antennae galaxies ( _d_ _∼_ 22 Mpc,
Schweizer et al. 2008) yields better linear resolution than
available for ULIRGs more common at higher redshifts.
As a nearby snapshot in the evolution of a gas-rich
merger, the Antennae provides a crucial opportunity to
better understand when, and how efficiently stars form
in a merger environment and the initiation of starburst
galaxies in exquisite detail.
The organizational structure of this paper is as follows. In Section 2 we describe the sub-mm and optical
observations utilized in this study and methods used for
calculating the stellar and molecular masses. In Section 3 we present the process of determining the IMR( _t_ )
through measurements centered on stellar clusters. In
Section 4 we present the algorithm and method for de


3


**Figure** **1** . An optical image of the Antennae taken with
_HST_ is shown in the top panel. The white box shows the
approximate region covered by the ALMA Cycle 0 observations. This region is expanded in the bottom panel with
CO(3-2) contours overlaid in white. The contour levels are

[55 _,_ 400] K km/s.


termining the IMR( _t_ ) through measurements centered
on molecular gas. In Section 5 we report the total mass
information and instantaneous mass ratios for both mea
surement schemes. In Section 6 we discuss the implications of the results in the context of understanding early
stages of star formation. Finally, in Section 7 we summarize our findings.


2. OBSERVATIONS AND METHODS


2.1. _ALMA_ _Observations_


We utilize previously attained ALMA CO(3-2) Cycle 0
data of the Antennae overlap region (Figure 1). These

4


data were first presented in Whitmore et al. (2014), and
detailed information on the configuration and calibration of such data is given in that work. In summary,
a 13 point mosaic was obtained with the “extended”
configuration ( _∼_ 400 m maximum) covering the overlap
region between the two interacting galaxies. These data
did not contain short or zero spacings, however the sizescales of the structures of interest here are sufficiently
compact (≲ 100 pc _≈_ 1”) this is not a concern.
The resulting CO (3  - 2) data cube has an angular
resolution FWHM of 0 _[′′]_ _._ 56 _×_ 0 _[′′]_ _._ 43, equivalent to (59 _×_ 45
pc) at the distance of the Antennae, _∼_ 22 Mpc. The rms
of this data cube was determined to be 3.3 mJy/beam
using line-free channels. These observations enabled the
high resolution co-spatial study of the mass of molecular
gas as compared to the mass of stars and star clusters
(i.e., the star formation efficiency).


2.2. _HST_ _Observations_


We retrieved _Hubble_ _Space_ _Telescope_ images of the
the Antennae galaxies (NGC 4038/4039) using the Advanced Camera for Surveys (ACS) from the Hubble
Legacy Archive. The original observations were published in Whitmore et al. (2010) and include multi-band
photometry in the following optical broadband filters:
_F435W_, _F550M_, and _F814W_ . All optical observations
were made with the Wide Field Camera (WFC) on the
ACS and exposure times total 2192 s, 2544 s, and 1680 s,
respectively. The observations were taken with a scale of
0 _[′′]_ _._ 049 pixel _[−]_ [1] and yield a field of view of _∼_ 202 _[′′]_ _×_ 202 _[′′]_ .
The registration of the HST optical images was done
following the methods of Brogan et al. (2010). Catalogs of clusters and their optical properties in the Antennae were constructed from the _F_ 550 _M_ image using
DAOFIND in IRAF and were presented in Whitmore
et al. (2010). For our purposes, we use the “concentration index” _CI_ of each source in the catalog to select for
clusters and remove any bright stars from our sample.
This is defined in Whitmore et al. (2010) as the different
between magnitudes measured within a 1 and a 3 pixel
radius with more concentrated objects have lower values
of _CI_ . As in Whitmore et al. (2010) we consider sources
with _CI_ _>_ 1 _._ 52 to be clusters and are included in our

analysis.


2.3. _Determining_ _Mass-to-light_ _ratios_


Our prescription for the IMR includes a term representing the stellar mass of a given region, which therefore necessitates determining the mass-to-light ratio,
M _/L_ 814 . We attempted several methods of determining
the mass-to-light ratio of spatial bins produced by the
Weighted Voronoi Tessellation (WVT, Section 4) before
settling on the procedure described later in this section.
These approaches aimed to characterize the mass-to


light ratio in the Antennae overlap region as a function
of age using 1) model predictions and 2) an empirical
relationship.
For the first approach, we generated Starburst99 models for the I-band mass-to-light ratio, M _/L_ _I_, i.e. we
generated models for _M_ _V_ and _V_ _−_ _I_ and combined
them in such a way to result in _M_ _I_ (Leitherer et al.
1999a). These models were generated for a total cluster masses of 10 [4] _−_ 10 [7] M _⊙_, various metallicity models,
_Z_ from 0 _._ 008 _−_ 0 _._ 04, Salpeter and Kroupa IMFs, and
upper mass limits on the IMF from 20 _−_ 100M _⊙_ . From
these models, we generated functions of M _/L_ _I_ with respect to age. The reduced chi-squared statistic of the
models was calculated with respect to the relationship
of cluster M _/L_ _I_ with age derived from Whitmore et al.
(2010). In addition to chi-square values _>_ 100, adopting this approach requires assuming an extinction value
_a_ _priori_, and given the range of extinction values (particularly for clusters with ages ≲ 10 Myr), we found that
this method was not robust.

We then attempted to derive a strictly empirical relationship between the observed value of cluster M _/L_ _I_
from Whitmore et al. (2010) as a function of age. This
was done by calculating the median of cluster M _/L_ _I_ for
each logarithmic age bin as described below.
From Whitmore et al. (2010), we gathered the following parameters for each cluster in the overlap region:
mass (M _⊙_ ), age ( _τ_ ), apparent magnitude in the I-band
(m I ), and the best estimate of reddening (E(B _−_ V)).
The I-band apparent magnitudes were then corrected
for extinction using the procedure described in Section
4.2 and converted to absolute magnitudes assuming a
distance to the Antennae galaxies of _d_ = 22 Mpc. We
then calculated the mass-to-light ratio to be the ratio of
the mass to the corrected I-band luminosity for a given
cluster. Figure 2 shows the relationship of this ratio
versus age of the cluster. Here we opt to use the I-band
luminosity as the primary value for “light” as opposed to
converting to a luminosity in solar luminosity units _L_ _⊙_,
which requires additional assumptions in the conversion
to bolometric luminosity.
As with the model-based approach, the scatter in the
data at the youngest ages (the clusters we are most interested in) spans three decades in the mass-to-light ratio,
and any ensemble approach improperly estimates M _/L_ _I_
for the majority of the young clusters. For this reason,
we viewed the ensemble median M _/L_ _I_ as a function of
age to be too general for the wide variety of clusters
and environments. Rather, we assigned to each region
the mass-to-light ratio of the enclosed star cluster. In
the case where there are multiple clusters in a region,
we assigned the median of those to that particular region. These mass-to-light ratios are shown in relation to
positions in the Antennae overlap region in Figure 3.

The assumptions made in this process regarding noncluster light in a region follow those discussed in Section 3. Namely, we assume that the diffuse inter-cluster
light in the aperture between the cluster and the larger
aperture boundary has approximately the same massto-light ratio as the central cluster, i.e. they are both
dominated by the same population. In a given WVT bin
that contains at least one star cluster, the mean fraction
of light than can be attributed to the cluster is 11%, the
distribution of this fraction for all WVT bins with a star

cluster can be seen in Figure 4.


2.4. _Calculation_ _of_ _Gas_ _Mass_ _from_ _CO_ _Emission_


The total CO(3-2) emission in a given aperture was
measured from the moment 0 (integrated intensity) map
of the ALMA Cycle-0 observations (see Section 2.1).
The _α_ CO conversion factor assumes a rotational transition of CO(J=1 _−_ 0). Since our measured emission of
CO is the J=3 _−_ 2 rotational transition, we must first
scale our luminosity of this upper transition to that expected for the ground state. We adopt CO(J=1 _−_ 0) _∼_
2 _×_ CO(J=3 _−_ 2), consistent with the median value found
by Wilson et al. (2008) for a sample of LIRGs and with
the values derived by Ueda et al. (2012) found for giant
complexes in the Antennae.
We assume a Milky Way metallicity for the Antennae
galaxies. For this assumption, the CO-to-H 2 conversion
factor is 4 _._ 3 M _⊙_ (K km s _[−]_ [1] pc [2] ) _[−]_ [1] (Bolatto et al. 2013).
The units of the _α_ CO conversion factor necessitate a CO
luminosity _L_ CO, yet simply summing the flux density in
a region yields a measurement in units K km s _[−]_ [1] pixel [2] .
We adopted the following to calculate the corresponding CO luminosity of a region. The pixel scale was
taken from the header of the CO(J=3 _−_ 2) moment-0
map as ∆= 2 _._ 22 _×_ 10 _[−]_ [5] deg, corresponding to 0 _[′′]_ _._ 08
pixels. Assuming a distance to the Antennae of _d_ = 22
Mpc (Schweizer et al. 2008), we determined the physical scale corresponding to a pixel, 8 _._ 5 pc/pixel. We
then converted the the summed CO(J=3 _−_ 2) emission
in a region with units K km s _[−]_ [1] pixel [2] to a CO luminosity by multiplying this total by the conversion factor
72.6 pc [2] /pixel [2] . With the CO luminosity determined,
we arrive at the following conversion from CO(J=3 _−_ 2)
to a molecular gas mass in solar units:


_M_ _mol_ = 2 _α_ CO _L_ CO _._ (1)


3. DETERMINATION OF THE IMR BASED ON

LOCATIONS OF STELLAR CLUSTERS


In order to determine the instantaneous mass ratio
(IMR) for a statistical sample of SSCs, we utilize the
ALMA and _HST_ observations discussed in Sections 2.1

and 2.2. We base the identifications of regions on the
locations of known SSCs, and determine the stellar and



5


gas mass in the surrounding area. To determine the
IMR of SSCs in the Antennae, we utilize the catalog of
star clusters in Whitmore et al. (2010). This method
is fundamentally different from that used below in Section 4 in that the IMR values are determined for local

regions centered on specific star clusters, as opposed to
being based on regions of molecular emission. Each of
these approaches will be subject to different biases. In
order to use this cluster-based method, we needed to de
termine both the total stellar mass and total molecular

mass within an aperture around each cluster.
To determine the stellar mass in a given aperture, we
used the following method. First, clusters from the “50
Most Luminous” and “50 Most Massive” tables (Tables 6 and 7 of that paper) with ages _<_ 10 [8] years were
identified that were contained within the footprint of the
ALMA observations. The upper age limit of 10 [8] years
is motivated by the mass loss and mechanical luminosity evolution, which is expected to decrease abruptly at
_∼_ 30 million years, and roughly level off by 100 million
years (Leitherer et al. 1999b). Although, the observed
age distributions of clusters appear to be more complicated and several other effects may be coming into play
(Fall & Chandar 2012). The ages, masses, and E(B-V)
values for these clusters were retrieved from the Whitmore et al. (2010) catalog. Using the data from the
F814W filter, for each cluster we determined the stellar
mass per electrons per second ( _e_ _[−]_ /s), which incorporated both the extinction and aperture corrections of
Whitmore et al. (2010). These values of stellar mass
per _e_ _[−]_ /s derived from a specific cluster were then applied to the total F814W emission for a given aperture
to determine the enclosed stellar mass. This process
was carried out for circular apertures of both 25 pc and
50 pc, which is well-matched to the synthesized beam
of the ALMA observations (Figure 10). The Hubble
Observations with a pixel size of 0 _[′′]_ _._ 05 (= 5 _._ 33 pc) are
well-resolved at this scale.

There were key assumptions that accompany this determination of the mass-to-light ratio within an aperture. Namely, we assume that the diffuse inter-cluster
light has approximately the same mass-to-light ratio as
the nearest cluster. If the non-cluster light in a given
aperture has a significantly different age or extinction
than that of the cluster, the adopted mass-to-light ratio
will be skewed. Based on Starburst99 models of cluster
magnitudes as a function of age (Leitherer et al. 1999a),
we can constrain the extent to which the adopted massto-light ratio is uncertain. For example, if the ambient
light in a given aperture is due to a stellar population
that is an order of magnitude older than the constituent
cluster, the adopted mass-to-light ratio based on the
cluster will be roughly 2.5 _×_ lower than the value appropriate for the surrounding stellar population. The offset

6



10 [-27]


10 [-28]


10 [-29]


10 [-30]


10 [-31]



10 [-27]


10 [-28]


10 [-29]


10 [-30]


10 [-31]



10 [-32]

10 [6] 10 [7] 10 [8] 10 [9]

Age [yr]


(b)



10 [-32]

10 [6] 10 [7] 10 [8] 10 [9]

Age [yr]


(a)







**Figure** **2** . The I-band mass-to-light ratio ( _M/L_ _I_ ) in solar units taken from the measured cluster mass and I-band magnitudes
of Whitmore et al. (2010) plotted versus age of the cluster. The solid black line indicates the median per logarithmic bin. The
purple shaded region shows the absolute median deviation around the median value per logarithmic bin. Subfigure (a) includes
all clusters in the Antennae overlap region observed by ALMA Cycle 0. Subfigure (b) includes all clusters with concentration
index _CI_ _>_ 1 _._ 52.



in the mass-to-light ratio due to age is likely to be partially offset by differences in extinction for a surrounding
stellar population with a different age than the cluster.
The younger a stellar population is, the more significant
the extinction of its light is likely to be, and therefore
the higher the adopted mass-to-light ratio for the cluster. For the clusters used in this study, the mean inferred extinction is _A_ 814 = 0 _._ 55 (the maximum inferred
extinction is _A_ 814 = 5 _._ 3). If the light from the surrounding stellar population is subject to negligible extinction,
the adopted mass-to-light ratio would be roughly 1.6 _×_
higher than the value appropriate for the surrounding
stellar population, significantly offsetting the effect due
to age. In order to be conservative, here (and below in
Section 4) we adopt the factor of 2.5 as the uncertainty
in inferring the mass-to-light ratio of an aperture based
on the age of the star cluster(s) present.
The stellar mass in an aperture was combined with
the molecular mass as follows to yield the IMR for these
regions centered on stellar clusters:

IMR = _M_ _stars_ (2)
( _M_ _stars_ + _M_ _gas_ ) _[.]_


4. DETERMINATION OF THE IMR BASED ON

LOCATIONS OF CO EMISSION


We then tried a more objective approach to determining the IMR in the overlap region of the Antennae galaxy
system. Interest in the SFE at the most nascent stage
of cluster formation lends itself well to identifying regions based upon the CO(3-2) integrated intensity map.
Due to the complexity of the diffuse gas in the overlap
region, we chose to adopt an algorithmic approach in



-18:52:33"


41"


49"


57"


53:05"


13"







29


30


31


|SGMC1<br>SGMC2<br>SGMC3|Col2|Col3|
|---|---|---|
|SGMC 1<br>SGMC 2<br>SGMC 3|||
|SGMC 1<br>SGMC 2<br>SGMC 3|||
|SGMC 1<br>SGMC 2<br>SGMC 3|||



55.7 12h01m54.5s
RA(J2000)


**Figure** **3** . The tessellation map for a target flux of _L_ _target_ =
7 _._ 3 _×_ 10 [5] K km/s pc [2] of the Antennae overlap region is shown
in grayscale. Overlaid are the mass-to-light ratios of the
star clusters identified by Whitmore et al. (2010) in units of
cluster mass in _M_ _⊙_ over cluster I band luminosity in _L_ _⊙,I_
for all clusters with concentration index, _CI_ _>_ 1 _._ 52.


defining these regions. While more traditional methods
have involved identifying pockets of CO emission “by
eye,” we believe this introduces biases due to the subjective opinions of differing authors. Our goal was to
derive an objective collection of “pixels” (hereafter referred to as bins) such that the size and shape of the bins
traces the density dependence of the emission from the

150


100


50







0

0 _._ 0 0 _._ 2 0 _._ 4 0 _._ 6 0 _._ 8 1 _._ 0
`f` `cluster` _/_ `f` `bin`


**Figure** **4** . Distribution of fraction of light in cluster versus the light in the entire surrounding WVT bin. Inset
shown to highlight the WVT bins with large fractions of
light coming from the enclosed cluster. The various colors
show the distributions for various WVT bin sizes: _L_ _target_ =
3 _._ 6 _×_ 10 [5] K km/s pc [2] (mauve), _L_ _target_ = 7 _._ 3 _×_ 10 [5] K km/s pc [2]

(cyan), and _L_ _target_ = 14 _._ 5 _×_ 10 [5] K km/s pc [2] (gold).


gas. Our criteria for the algorithm did not include the
ability to distinguish individual molecular clouds, and
therefore clump finding algorithms are ill-suited to our
scientific objective. For details on an analysis of cloud
properties in the Antennae, see Leroy et al. (2016).
An initial approach was to position a simple
Cartesian-like coordinate grid on the moment 0 map
and determine the IMR within each pixel. While this
certainly met our criteria for an objective method and
is thereby less-limited by human bias, it failed on the
grounds that it was not adaptive to the variations in
CO emission. Algorithmically separating regions of CO
emission with differing intensities allows us to limit the
effects that result from averaging over regions of differing
surface brightness. We decided to adopt a more sophisticated algorithm than a simple Cartesian-like coordinate
grid. Our aim was to define the “pixels” more intelligently, i.e. the bounds of the pixels should roughly trace
boundaries between differing levels of CO intensity.
We first tested traditional Voronoi tessellations (VT).
This tessellation method is created through a set of generating points (aptly termed “generators”). The goal of
VT is to obtain equal levels of signal-to-noise (S/N, or
another measure of emission strength) in a bin. This is
done by assigning every pixel, _x_ _k_, to its nearest generator, _z_ _i_ . In essence, the bins are defined to minimize
the quantity _|x_ _k_ _−_ _z_ _i_ _|_ . By definition, the boundaries between generators are therefore perpendicular bisectors of
the connecting segment between the points. Since the
boundaries of bins in a VT are straight lines, for complex and diffuse data of _∼_ spherical molecular clouds, the
VT does not optimally follow the intensity contours of
the CO emission in the data. In previous works utilizing



7


VT, the bin sizes and distribution were made sensitive
to density fluctuations by using a bin accretion method.
Since we were looking for an algorithm that will follow
a curved boundary in detail, we opted to use weighted
Voronoi tessellations (WVT).


4.1. _WVT_ _binning_ _algorithm_


The WVT binning algorithm was developed for use
in sparse X-ray data. It is advantageous over the traditional Voronoi tessellations by introducing an additional
parameter, the scalelength _δ_ _i_, to be associated with each
bin. This scalelength works to stretch or compress the
metric inside each bin, which are now defined to minimize the quantity _|x_ _k_ _−_ _z_ _i_ _|/δ_ _i_ . The adaptability of the
metric allows for the boundaries of each bin to have cur
vature that approximately follows a constant gradient of
the CO emission intensity. This allows an objective, but
adaptive, pixellation of the CO integrated intensity map
into bins within which the IMR can be derived.

We made use of the WVT binning algorithm by Diehl
& Statler (2006), which is a generalization of the algorithm developed in Cappellari & Copin (2003). The
original algorithm builds the tessellation such that pixels are accreted into bins until a target signal-to-noise
(S/N) level is reached. This is appropriate for X-ray
data where there exists independent Poisson noise in
each pixel. Since the noise in interferometric images is
correlated in a more complicated manner, this target
parameter is ill-suited for our data. We adapted this
algorithm such that pixels are accreted to bins until a
limiting luminosity level ( _L_ target ) is reached. Given a
conversion prescription from CO radiation luminosity to
total mass, by seeking a target total luminosity we are
effectively probing a particular gas-mass scale in each
tessellation.

Rather than running our adapted WVT binning algorithm over the entire CO moment0-map of the Antennae overlap region, we masked the CO moment0-map to
only consider significant (5 _σ_ ) star-forming gas emission.
The rms of the CO moment0-map was calculated with
CASA in isolated patches of the map and was found
to be _σ_ _∼_ 11 K km/s. We then created a mask of the
CO map that only included locations of emission greater
than 55 K km/s. The WVT binning algorithm was then
run on the masked CO moment0-map for the following limiting luminosity levels: 3 _._ 6 _×_ 10 [5] K km/s pc [2],
7 _._ 3 _×_ 10 [5] K km/s pc [2], and 14 _._ 5 _×_ 10 [5] K km/s pc [2] . The
tessellations of differing luminosity levels probe different size and mass scales. Figure 5 shows snapshots of
the WVT binning algorithm at work during the 25%,
50% and 100% completion stages.


4.2. _Calculating_ _stellar_ _mass_ _in_ _WVT_ _bins_

8



-18:52:33"





55.9s 55.4s
RA(J2000)



55.9s 55.4s
RA(J2000)


|2:33"|Col2|
|---|---|
|55<br>13"<br>3:05"<br>57"<br>49"<br>41"<br>:33||
|55<br>13"<br>3:05"<br>57"<br>49"<br>41"<br>:33|.9s<br>55.4s<br>RA(J2000)|



**Figure** **5** . Timestep through the WVT binning algorithm of the Antennae overlap region shown in the bottom panel of Figure
1 after it has finalized 25%, 50%, and 100% of the bins for a target luminosity of 3 _._ 6 _×_ 10 [5] K km/s pc [2] . Black contours represent
the CO(3-2) emission with levels [165, 330, 500] K km s _[−]_ [1] .



The WVT bin boundaries were applied to the optical image. With the units in _e_ _[−]_ /s, the flux was
summed over each WVT bin. Taking the PHOTFLAM keyword from the image header as 7 _._ 07236 _×_
10 _[−]_ [20] ergs/cm [2] / [˚] A/ _e_ _[−]_, the _e_ _[−]_ /s per bin were converted
to a flux in ergs/cm [2] /s/A [˚] per bin. This flux was converted to an absolute magnitude assuming an _I_ band
flux for Vega of _f_ _vega_ = 1 _._ 134 _×_ 10 _[−]_ [9] ergs/cm [2] /s and
a distance to the Antennae of _d_ = 22 Mpc (Schweizer
et al. 2008),



_−_ _−_ 20
_M_ _I_ = _−_ 2 _._ 5 log ( _e_ _/s_ )7 _._ 07236 _×_ 10
� _f_ _vega_



_−_ 5 log _d._ (3)
�



a WVT bin (Section 2.3), the extinction-corrected absolute _I_ band magnitudes were converted to stellar masses
in solar units. The stellar mass was combined with the
molecular mass in each WVT bin (calculated using the
methods of Section 2.4) following Equation 2 to obtain
the IMR in each WVT bin containing at least one stellar
cluster.


4.3. _Errors_ _in_ _the_ _IMR_


Complicated and unknown uncertainties in both the
stellar and gas mass calculations make estimating formal
errors on the resulting IMR nearly impossible. Despite
this, it is simple to calculate the dependencies of the
error in IMR on several quantities. This allows a better understanding of the areas in parameter space for
which the reported values of the IMR( _t_ ) can be trusted
and to what extent. As an example, we illustrate how
the uncertainties depend on the relative errors in the
gas mass and stellar mass in Figure 6. Throughout the
following calculation, we assume a nominal error in the
gas mass of 20%, _σ_ _M_ _gas_ = 0 _._ 2 _M_ _gas_ . Rewriting the IMR
from its traditional notation ( _M_ _stars_ _/_ ( _M_ _gas_ + _M_ _stars_ ))
into a function of the gas-to-stellar mass ratio yields:



For each bin that contained at minimum one cluster,
the absolute magnitudes could be corrected for extinc
_−_
tion using the best estimate of reddening, E(B V), from
Whitmore et al. (2010). We converted the reddening values to extinctions at 814 nm using _A_ _V_ = 3 _._ 1 _E_ ( _B_ _−_ _V_ )
and the relation between _A_ 814 and _A_ _V_ determined by
Cardelli et al. (1989):


_A_ 814 _≈_ 0 _._ 6 _A_ _V_ _._ (4)


From Figure 3, it is evident that there exist bins without any identified star clusters, particularly in SGMCs
2 and 3. For those bins, the IMR cannot be calculated,
as we lack a suitable method for determining the M/L
ratio for the stellar component. For bins with multiple
clusters, we follow the procedure discussed in Section
2.3 and assume the M/L ratio of the bin can be approximated by the median of the M/L ratios of the enclosed
clusters.

Using our best estimate for the mass-to-light ratio in



IMR = 1 + _[M]_ _[g][as]_
� _M_ _stars_



_−_ 1
_._ (5)
�



Traditional propagation of error gives the fractional error in the IMR as a function of the IMR itself and the

fractional error in stellar mass. Exploring this relationship with varying values of the IMR and the fractional
stellar mass error (Figure 6) results in fractional errors
in the IMR around _∼_ 20% for much of parameter space.

10 [0]


10 _[−]_ [1]



4 _×_ 10 _[−]_ [1]

3 _×_ 10 _[−]_ [1]


2 _×_ 10 _[−]_ [1]


10 _[−]_ [1]


6 _×_ 10 _[−]_ [2]



10 _[−]_ [2]

10 _[−]_ [3] 10 _[−]_ [2] 10 _[−]_ [1] 10 [0]

## `IMR`



**Figure** **6** . The fractional error in the IMR (shown in colorscale) with respect to the IMR and fractional error in the
stellar mass component. This assumes an error in the gas
mass of 20%. For much of the parameter space the fractional
error in the IMR is dominated by the error in gas mass and
hovers around 0.2, which directly reflects the input uncertainty.


The error in the IMR is minimized as the ratio approaches unity with errors in the stellar mass less than
_∼_ 10%.


5. RESULTS


5.1. _SGMC_ _Masses_ _and_ _averaged_ _IMRs_


The Antennae galaxies contain molecular clouds of unusually high mass. Wilson et al. (2000) derived mass
values that are 5 _−_ 10 times more massive than the

largest molecular complexes of similar size in the grandspiral galaxy M51 (Rand & Kulkarni 1990). Wei et al.
(2012) measured clouds in the overlap region of the Antennae to be larger than any in the Milky Way or nearby
disk galaxies (Bolatto et al. 2008; Heyer et al. 2009;
Solomon et al. 1987), causing them to be referred to as
Super Giant Molecular Complexes (SGMCs). Within
the SGMCs, individual clouds are also grand in scale,
Johnson et al. (2015) found a _>_ 5 _×_ 10 [6] M _⊙_ cloud with
a radius of _<_ 24 pc, making it one of the densest clouds
known. As some of the most massive molecular com
plexes, updated molecular mass values for the Antennae
SGMCs remain crucial for improved understanding of
star-formation in intense environments.

As a consistency check with previous work, we determined the mass of each WVT bin in the three SGMCs

following Section 2.4 and summed over these values in
each of the three SGMCs to derive total gas mass. For
the first, second, and third SGMCs, the total gas mass
is approximately 7 _._ 8 _×_ 10 [8] M _⊙_, 6 _._ 3 _×_ 10 [8] M _⊙_, and
6 _._ 6 _×_ 10 [8] M _⊙_ . These values are within a factor of _∼_ 2
with previous mass estimates of Wilson et al. (2003)
for the three SGMCs: 6 _._ 3 _×_ 10 [8] M _⊙_ _,_ 3 _._ 9 _×_ 10 [8] M _⊙_, and
9 _._ 3 _×_ 10 [8] M _⊙_ in SGMCs 1, 2, and 3, respectively.



9


The averaged IMRs are 0.2%, 0.3%, and 0.3% for
SGMCs 1, 2, and 3, respectively. While these values
are quite low, this is reasonable given the enormity of
these molecular clouds and the large age range of the
stellar clusters enclosed.


5.2. _Star_ _Formation_ _Efficiency_ _from_ _Optical_ _clusters_


The instantaneous mass ratio IMR= M stars _/_ (M stars +
M gas ), was calculated for each aperture. The prescription for determining the M/L ratio of a bin, and therefore the corresponding stellar mass, is described in Section 2.3. The prescription for determining the total gas
mass from the CO(3-2) gas emission is described in Section 2.4. These values were then combined to determine

the IMR associated with each stellar cluster. We expect
that this method will have a bias toward regions with
optically visible (un-embedded) clusters that are more
efficient at expelling gas. Indeed, Cabrera-Ziri et al.
(2015) found that for the three most massive clusters in
the overlap region (of ages between 50-200 Myr), the gas
mass is only _<_ 9% of the stellar mass.
The resulting IMR values are presented in Figure 7.
We see a clear trend for the IMR value to increase with

cluster age, as we expected, with some regions reaching
a value of unity (100% of the gas has been removed
and/or converted to stars) at ages of _<_ 10 Myr. For ages
≲ 2 Myr (before which we do not expect supernovae and
winds from Wolf-Rayet stars to have had a significant
effect), the IMR values range from close to zero to _∼_ 0 _._ 5.
A significant caveat to this approach is that for a given
optical cluster, we do not know whether the CO emission in the aperture is associated with the cluster, or
simply along the same line-of-sight. Therefore, we expect a fraction of older clusters to _appear_ to be associated with molecular material, when in fact they are not.
This contamination will result in scatter toward lower

IMR values, as discussed in Section 5.3. The centering
of measurements on either the product of star formation
(stellar clusters), or the gas produces different results on
these small size-scales. Zhang et al. (2001) found that
feedback effects may modify the Schmidt law at scales
below 1 kpc. A similar effect of star-formation relations breaking down on small-scales was presented by
Schruba et al. (2010) in M33 and by Kruijssen & Longmore (2014) for a sample of regions including the solar
neighborhood, the Central Molecular Zone of the Milky
Way, a ‘disk galaxy,’ a ‘dwarf galaxy’, and a starbursting
‘sub-mm galaxy.’


5.3. _Star_ _Formation_ _Efficiency_ _from_ _CO_ _map_


The instantaneous mass ratio (IMR) was also calculated for all WVT bins that had an associated stellar cluster (see Section 4). This procedure was completed for WVTs resulting from target luminosities of

10


1 _._ 0


0 _._ 8


0 _._ 6


0 _._ 4


0 _._ 2


0 _._ 0



40


30


20


10





0

|5 and 50 pc. See Figure 6 for a description of t e calculated IMR(t) values.|Col2|Col3|the bi is th (f|
|---|---|---|---|
|0_._2<br>0_._4<br>0_._6<br>0_._8<br>0<br>1<br>2|0_._2<br>0_._4<br>0_._6<br>0_._8<br>0<br>1<br>2|0_._2<br>0_._4<br>0_._6<br>0_._8<br>0<br>1<br>2|(f<br>th<br>w<br>e<br>b<br>a <br>u<br>te<br>w<br>G|
|0_._2<br>0_._4<br>0_._6<br>0_._8<br>0<br>1<br>2||||


0 _._ 0 0 _._ 2 0 _._ 4 0 _._ 6 0 _._ 8
## IMR [ M ∗ / ( M ∗ + M gas )]


**Figure** **8** . Distribution of the IMR for the various WVT bin
sizes: _L_ _target_ = 3 _._ 6 _×_ 10 [5] K km/s pc [2] (mauve), _L_ _target_ =
7 _._ 3 _×_ 10 [5] K km/s pc [2] (cyan), and _L_ _target_ = 14 _._ 5 _×_ 10 [5]

K km/s pc [2] (gold).


_L_ _target_ = 3 _._ 6 _×_ 10 [5] K km/s pc [2], 7 _._ 3 _×_ 10 [5] K kms pc [2], and
14 _._ 5 _×_ 10 [5] K km/s pc [2] . We find very few WVT bins with
IMRs greater than _∼_ 10%, with the mean of the distribution being 2 _._ 4 % (see Figure 8). The cluster with
consistently the highest IMR (shown as a black star in
Figures 9, 11, 12) is identified as WS80 and has been
studied extensively in the literature (e.g. Whitmore &
Zhang 2002). As the size of the WVT bin increases, the
fractional increase of stellar light due to both the diffuse stellar component and compact clusters within the
WVT bin increases more slowly than the increase in the
diffuse CO(3-2) emission. Correspondingly, as the size
of the WVT bins ( _L_ _target_ ) decreases, the IMR values
systematically increase. We find that determining the



IMR by centering measurements on molecular gas does
not follow the predicted trend as seen in Section 5.2.
A necessary condition for determining the IMR in a
WVT bin is the presence of at least one identified stellar
cluster in the projected area of the bin. The age dating of these clusters, done by Whitmore et al. (2010),
enables us to compare the relationship of the IMR with
time, see Figure 9. The majority of WVT bins contain
only one identified cluster, but in the case where there
are multiple, the median age of the enclosed clusters is
taken. Our original hypothesis was that as a cluster
ages, more of its gas is converted into stars, destroyed,
or expelled, and the IMR would approach 100%. We do
not observe this trend in the overlap region of the Antennae galaxies for regions selected based on their CO(3-2)
emission. Rather, we observe systematically decreasing
IMRs for clusters of increasing age. This result is interesting, but may be better explained by an observational
bias rather than an astrophysical phenomenon (this bias
is explored further in Section 6.1). In particular, because
the bins are determined based on their CO(3-2) flux
(for which a 5 _σ_ detection is required), we expect that
this method will be systematically biased toward regions
with significant CO emission. By requiring the presence of significant CO emission in the analyzed WVT
bins, we bias ourselves exclusively towards clusters with
a significant mass of gas. We repeated all procedures
using a 2 _σ_ and 3 _σ_ threshold for the CO emission to determine whether the trend of decreasing IMR with age
would change, but no significant change was observed.
Given that the clusters are also identified in _projection_,
we also expect there to be contamination from clusters
simply along the line-of-sight, and not physically associated with the molecular gas, which would systematically
manifest itself as older clusters appearing to be gas-rich.
These combined effects may explain the systematically
low IMR values for relatively older clusters in the overlap region of the Antennae galaxies.


5.4. _Comparison_ _of_ _methods_ _for_ _an_ _arbitrary_ _cluster_


As a direct comparison of the two methods, we take an
arbitrary cluster that is both one of the “50 Most Massive” clusters (included in the analysis of Section 3) and
surrounded by a 5 _σ_ detection of CO(3-2) emission (included in the analysis of Section 4). The cluster chosen
is the 19th most massive cluster in the entire Antennae
system (Figure 10), with an ID of 18848 in Whitmore
et al. (2010) and nominal values of the stellar mass and
age estimate of 1 _._ 2 _×_ 10 [6] M _⊙_ and 4.8 Myr, respectively.
Centering the measurement on the stellar cluster
yields an IMR of 23% and 21% for the 25 pc and 50 pc
apertures, respectively. In comparison, the WVT bins
containing this cluster have IMRs of 34%, 11%, and 10%
for increasing _L_ _target_, respectively. In order to compare

11



10 [0]


10 1


10 2


10 3









10 4

10 [6] 10 [7] 10 [8]
Age (year)





10 [0]


10 1


10 2


10 3







10 4

10 [6] 10 [7] 10 [8]



10 [0]


10 1


10 2


10 3





10 4

|0 10 10 Age (year) = 14.5 × 105 K km/s pc2|Col2|
|---|---|
|Ltarget = 14.5 × 105 K km/s pc2<br>SGMC 1<br>SGMC 2<br>SGMC 3<br>Field|Ltarget = 14.5 × 105 K km/s pc2<br>SGMC 1<br>SGMC 2<br>SGMC 3<br>Field|
|6|107<br>1|



Age (year)



**Figure** **9** . The stellar mass to total mass ratio (IMR(t)) is
shown as a function of the median cluster age in each WVT
bin, with the inclusion criterion for clusters being a concentration index _CI_ _>_ 1 _._ 52. This is done for WVT tesselations
with target bin CO luminosity of _∼_ 3 _._ 6 _×_ 10 [5] K km/s pc [2],
_∼_ 7 _._ 3 _×_ 10 [5] K km/s pc [2], and _∼_ 14 _._ 5 _×_ 10 [5] K km/s pc [2], shown
from top to bottom, respectively. Colored points represent
WVT bins whose total stellar cluster mass is greater than
10 [5] M _⊙_, where gray points represent bins with a total stellar
cluster mass less than 10 [5] M _⊙_ . See Figure 6 for a description
of the errors in the calculated IMR( _t_ ) values.



(2010). White contours represent CO(3-2) emission with levels [55,220,440] K km/s. Dashed gray lines represent 25 pc
and 50 pc circular apertures used to determine the IMR
based on locations of stellar clusters. The beam of the ALMA
Cycle 0 observations is shown in the bottom left. The inset
on the upper right shows the tessellation with a target luminosity _L_ target of 7 _._ 3 _×_ 10 [5] K km s _[−]_ [1] of the same region with
identical contours and apertures overlaid.


these values, we consider the physical area of the circular apertures and WVT bins. The 25 pc and 50 pc radii
apertures have areas 1960 pc [2] and 7850 pc [2], respectively,
while the WVT bins have areas of 874 pc [2], 2040 pc [2], and
4440 pc [2], for increasing _L_ _target_ . The smallest WVT bin
has an IMR greater than the apertures. This is reasonable due to its small size, which has a higher fraction
of cluster light to diffuse stellar light and minimizes the
mass from the gas reservoir that encompasses the cluster. The larger IMR ratios for the apertures centered
on the stellar clusters are likely due to the differing focuses of the two methods. While the circular apertures
are centered on the cluster the WVT bins follow the

gas emission, which is not symmetrically distributed and
leads to larger gas masses and lower IMRs.


5.5. _Dependence_ _of_ _IMR_ _on_ _surface_ _brightness_ _and_

_extinction_


The WVT binning algorithm allows us to investigate
the dependence of the IMR on various physical parameters. For example, we can explore whether the efficiency
of star formation depends on the surface density of the
CO gas in molecular clouds. The ratio of the flux in
a given WVT bin and the area in units of pc [2] probes
the CO gas density. Since our WVT bins were defined
algorithmically from the data itself, we are able to objectively measure the dependence of the IMR as a func

12



10 [0]


10 1


10 2


10 3


10 4


10 [0]


10 1


10 2


10 3


10 4


10 [0]


10 1


10 2


10 3


10 4



10 [3] 10 [4]

mol [[M] pc 2 ]


10 [3] 10 [4]




|10 10 mol [M pc 2] = 14.5 × 105 K km/s pc2|Col2|
|---|---|
|Ltarget = 14.5 × 105 K km/s pc2<br>SGMC 1<br>SGMC 2<br>SGMC 3<br>Field|Ltarget = 14.5 × 105 K km/s pc2<br>SGMC 1<br>SGMC 2<br>SGMC 3<br>Field|
|103|1|



mol [[M] pc 2 ]


**Figure** **11** . The instantaneous stellar mass to total mass
ratio (IMR) is shown as a function of the molecular surface
density of each WVT bin. This is done for WVT tesselations
with target bin CO luminosity of _∼_ 3 _._ 6 _×_ 10 [5] K km/s pc [2],
_∼_ 7 _._ 3 _×_ 10 [5] K km/s pc [2], and _∼_ 14 _._ 5 _×_ 10 [5] K km/s pc [2], shown
from top to bottom, respectively. Colored points represent
WVT bins whose total stellar cluster mass is greater than
10 [5] M _⊙_, where gray points represent bins with a total stellar
cluster mass less than 10 [5] M _⊙_ . See Figure 6 for a description
of the errors in the calculated IMR values.



tion of molecular gas surface density. When considering
WVT bins that include optical clusters, the IMR does
not seem to correlate with the CO surface brightness
(Figure 11), which agrees with results of Leroy et al.
(2017) showing that the small-scale surface density of
clouds has a relatively weak effect on star formation.
This is rather unexpected, and may be truly physical
or it may indicate that the surface density is not a
good probe of the volumetric density of CO gas and
we are therefore unable to establish a relationship between IMR and CO gas density. Even when considering
WVT bins with only the more massive optical clusters
of M _>_ 10 [5] M _⊙_, the relationship between IMR and surface brightness remains largely consistent with a random
distribution. (Figure 11).
In addition to the relationship between the IMR and
CO surface brightness, we can also investigate the dependency of IMR and the 814 nm _A_ 814 extinction in each
of the WVT bins. Higher extinction values may indicate
that the cluster is more deeply embedded in the molecular cloud from which its stars are forming. Due to the
increase in the amount of available dense gas in this
environment, we expect higher IMR for clusters with
higher values of extinction. Since the WVT bins were
determined independent of extinction, they provide an
objective means for investigating whether more deeply
embedded clusters indeed correspond to higher IMRs.
We see a clear trend across all SGMCs of increasing IMR
with extinction, confirming that more deeply embedded
clusters are capable of higher rates of SFE (Figure 12).
A comparison of the IMR with respect to both age and
extinction can be seen in Figure 13, along with a comparison of the IMR to both age and surface brightness.


6. DISCUSSION


6.1. _Biases_ _of_ _the_ _two_ _methods_


Each of the two primary methods we used to estimate the IMR(t) for regions in the Antennae is subject to limitations. With the WVT method, there is
power in mathematically defining regions whose areas
adjust based on the amount of CO emission at a given
point. However, it constrains our analysis to regions
where there is significant CO emission, which inherently
biases our results toward regions rich in molecular gas,
but which may not have associated star formation or the
star formation episode may be in its early stages. For
these young clusters, it is likely that we are missing optical light and thereby underestimating the stellar mass
associated with the WVT bin. This method also selects

and highlights slightly older clusters that are either inefficiently producing stars or feedback from massive stars
has failed to clear out much of the initial gas from the
molecular cloud. These scenarios are expected to be rare

10 [0]


10 1


10 2


10 3


10 4


10 [0]


10 1


10 2


10 3


10 4


10 [0]


10 1


10 2


10 3


10 4



0 1 2 3 4 5
A 814 [mag]


0 1 2 3 4 5
A 814 [mag]

A 814 [mag]



**Figure** **12** . The instantaneous stellar mass to total mass
ratio (IMR) is shown as a function of the median extinction at 814 nm for all clusters in each WVT bin. This is
done for WVT tesselations with target bin CO luminosity of _∼_ 3 _._ 6 _×_ 10 [5] K km/s pc [2], _∼_ 7 _._ 3 _×_ 10 [5] K km/s pc [2], and
_∼_ 14 _._ 5 _×_ 10 [5] K km/s pc [2], shown from top to bottom, respectively. Colored points represent WVT bins whose total stellar cluster mass is greater than 10 [5] M _⊙_, where gray
points represent bins with a total stellar cluster mass less
than 10 [5] M _⊙_ . See Figure 6 for a description of the errors in
the calculated IMR values.



13


and cannot explain the presence of multiple clusters with
ages ≳ 5 Myr with very low IMRs. The more plausible
explanation is that these regions are “contaminated” by
clusters along a WVT bin’s line-of-sight and which are
not physically associated with the observed molecular
gas. This limitation of the algorithm biases our results
towards lower values of the IMR, particularly for older
clusters.

Because of these biases towards detecting the population of older clusters that _appear_ to remain in a dense
molecular cloud, the results of the evolution of IMR with
age by centering our measurement on molecular gas contradict our initial hypothesis. Specifically, we observe a
decreasing trend in the relationship between these two
quantities.
On the other hand, the trend is reversed for the analysis done by focusing on circular apertures around luminous and massive clusters. This result follows our

prediction: the ratio of stellar to total mass increases as
stars form and gas is expelled through stellar feedback.
Although this result supports our original hypothesis,
this method is also subject to biases. Building a sample of clusters by requiring their luminosity and mass
to be high will preferentially select a sample of clusters
that have been successful at clearing much of their gas
reservoir. Whitmore et al. (2010) found that _∼_ 15% of
clusters in the entire Antennae system were completely
dust-obscured. This ratio may be higher in the overlap
region due to the larger gas reservoir. While there are
still some of the optically brightest clusters visible within
the SGMCs, the majority of this sample resides outside
of these giant gas clouds. There are very few older clusters that are surrounded by a significant amount of gas,
and it is more likely that older clusters with low IMR
are a result of chance superposition or incorrect age estimates. This sways the stellar to total mass ratios of
this sample to approach unity as age increases.


6.2. _The_ _Observed_ _Instantaneous_ _Mass_ _Ratios_ _and_

_Cluster_ _Survival_


The ability of star clusters to remain bound and
evolve into globular clusters is strongly tied to their
SFE. However, different theoretical efforts have not converged on consistent values, but instead have predicted
a large range of SFEs necessary for clusters to remain
bound. For example, the simplest case without considering environmental effects (e.g. turbulence and noninstantaneous timescales Hills (1980) requires a SFE of
at least 90%, while Baumgardt & Kroupa (2007) and
Pelupessy & Portegies Zwart (2012) report values as
low as 5 _−_ 10% provided the gas is removed over long
timescales. With only _∼_ 8 clusters presented here with
IMR _>_ 10%, our findings suggest that SFEs of several
tens of percent (but much less than 90%) are not espe

14


cially common. Taken at face value, the apparently low
SFE with which clusters in the Antennae are forming
could contribute significantly their destruction.
Our initial hypothesis that the IMR(t) value should
exhibit a trend in which IMR values increase with age
and approach unity appears to be approximately borne
out (as shown in Fig. 7), which is based on localized
emission in the vicinity of optical SSCs. However, this
hypothesis is generally inconsistent with the results from
the second method based on the intensity of the CO
emission (as shown in Fig. 9). These apparently contradictory results can be explained by both line-of-sight
contamination and the Antennae system not being a
steadily evolving post-starburst, but rather having a significant CO reservoir that is actively forming star clusters. In a system crowded with both newly-formed and
mature star clusters, any arbitrary and sufficiently large
aperture is likely to contain a mixed population, which
makes it challenging to disentangle the gas associated
with any particular cluster of a given age.
For these reasons, we assume that the IMR is better
determined through the method that localizes emission
associated with optical clusters. If we assume that the
IMR roughly equivalent to the SFE for clusters with
sufficiently young ages (e.g. IMR( _t_ _≤_ 10 [6] _[.]_ [5] )), we can
assess the fraction of clusters that could remain bound.
Based on the analysis discussed in Section 5.2, only 2/5
of the youngest massive clusters ( _t_ _≤_ 10 [6] _[.]_ [5] years, mass
≳ 7 _×_ 10 [5] M _⊙_ ) optically visible clusters considered here
appear to have instantaneous mass ratios ≳ 0 _._ 5. If SFEs
as low as _∼_ 30% could still produce a bound cluster,
the relative fraction of these massive clusters that could
survive increases to 3/5. Although we recognize small
sample statistics may be at play, this fraction does not
appear to increase until the SFE threshold is lowered to
5%, which may only result in bound clusters under very
specific physical scenarios (see Section 1.1). However,
we note that this method inherently assumes that the
gas within the 25 pc or 50 pc radius around each cluster
is associated with that cluster. For the youngest clusters, the IMR values for the 25 pc and 50 pc radii are
very similar, suggesting that the gas is highly concentrated on the clusters. However, if the gas associated
with the clusters has been over-estimated, the corresponding IMR value will be higher – suggesting a higher
fraction of potentially bound clusters.
If instead we look to the IMR( _t_ ) values determined
based on the CO emission in Section 5.3, only a single
region appears to have IMR(t _<_ 10 [6] _[.]_ [5] ) ≳ 0 _._ 3, suggesting that very few of the regions at large in this system will produce bound clusters. Thus, on the surface,
these results suggest that only a few of the massive clusters formed recently in the Antennae have the chance to
evolve into globular clusters, especially considering the



number of other physical processes that will affect their
survival after the first few million years (e.g. Gnedin &
Ostriker 1997; Hollyhead et al. 2015). This is consistent
with other studies (e.g. Whitmore 2004; Fall et al. 2005;
Whitmore et al. 2007) that find that only a few percent
of young star clusters survive to become old globular
clusters.


6.3. _Clearing_ _Timescales_ _for_ _the_ _CO_ _Gas_


The timescales on which molecular material is de
stroyed or expelled from a massive star cluster is important for determining whether these massive clusters
could potentially undergo a “second generation” of star
formation, as has become an outstanding issue in globular cluster evolution in recent years. Observations of
globular clusters have unambiguously shown evidence
for multiple chemical populations, however the origin of
these populations remains unclear (e.g. Bastian et al.
in prep, Cabrera-Ziri et al. 2015).
From Section 5.2, we can estimate the timescales on
which the CO gas is destroyed or expelled from the cluster environments. Figure 7 shows a clear trend indicating that the relative fraction of CO associated with
clusters decreases with age, as expected. By ages of
_∼_ 10 [6] _[.]_ [7] years, some of the clusters appear to have already cleared the molecular material from within radii
of 50 pc (where Whitmore et al. (2014) found that the
lifetime of GMCs in the region is _≈_ 10 [7] years). By ages
of _∼_ 10 [7] _[.]_ [5] years, this is true for the majority of clusters.
This agrees well with the clearing timescales of 2 Myr
and 7 Myr for gas that is associated and unassociated
with the stellar cluster, respectively (Grasha et al., in
prep). Moreover, we note that for clusters older than
_∼_ 10 [6] _[.]_ [7] years, the IMR values derived from the 25 pc
and 50 pc radii are more discrepant (see Fig. 7), potentially indicating that gas is no longer as centrally concentrated on the clusters by this time. We hypothesize
that the clusters with ages _>_ 10 [7] _[.]_ [5] years that appear to
have molecular material still associated with them may
well simply be contaminated by CO emission along the
line-of-sight.


6.4. _The_ _Need_ _for_ _Thermal_ _Radio_ _Observations_


Determination of the IMR through centering the measurement on gas or clusters are both subject to the additional issue that we are likely missing stellar light from
the youngest clusters, which may not be visible at optical wavelengths. This additional effect is more strongly
felt by the WVT binning method as the resulting bins
are systematically more enshrouded in obscuring material than the clusters assembled by having a high luminosity and/or mass. In both methods (but particularly
for the one based on CO emission) we are very likely underestimating the stellar mass of the youngest clusters

(and older enshrouded ones). This effect extends to the
IMR, which is also likely to be slightly underestimated at
the youngest ages. Properly accounting for stellar mass
of young clusters could be done with high spatial resolution thermal radio observations as an extinction-free

tracer of recent star formation. Although Neff & Ulvestad (2000) present VLA images of the Antennae at 6 and
4 cm of resolutions _∼_ 1 _[′′]_ and 2 _[′′]_ _._ 6, respectively, these observations likely suffer from too much non-thermal synchrotron contamination.


7. CONCLUSIONS


This work sought to derive the SFE of clusters in
the Antennae galaxies, the nearest major-merger to the
Milky Way. Age information for the _>_ 10 _,_ 000 identified
clusters in the overlap region (Whitmore et al. 2010)
allowed further investigation into the relationship between the instantaneous mass ratio (IMR) as a function
of time, where IMR(0) = SFE.
We followed two approaches in deriving the IMR( _t_ ).
The first (Section 5.2) analyzed the enclosed gas and
stellar mass within circular apertures of 25 and 50 pc.
This resulted in a monotonically increasing trend of IMR
with age, as it is biased towards clusters capable of ejecting its molecular gas as internal feedback mechanisms

turn on.
The second approach (Section 5.3) employed an algorithm to intelligently pixelate the moment-0 CO map
such that each bin contains approximately the same flux,
defined by the parameter _L_ _target_ . This method resulted
in a monotonically decreasing trend of IMR with age,
as it is biased towards clusters whose feedback was in
capable of expelling its molecular gas. The combination
of the two methods yields an honest picture of the efficiency of star formation in the Antennae galaxies, from
which we conclude:


_•_ Only a handful of the bins and/or clusters have
IMR(0) = SFE _>_ 0.2. On the surface, this im


15


plies that the fraction of star clusters that remain
bound is small. However, the optical identification of clusters and determination of their masses

will be systematically biased toward low apparent
stellar masses due to dust, and we are likely underestimating the IMRs.


_•_ Some clusters appear to have removed virtually all
of the molecular material at ages as young 10 [6] _[.]_ [7]

years. The majority of clusters appear to have
removed their molecular material by ages 10 [7] _[.]_ [5]


years.


_•_ There is no observed dependence of IMR( _t_ ) on surface density, but a strong dependence on extinction. The dependence of the IMR( _t_ ) on extinction
can be explained if extinction is acting as a proxy
for the evolutionary state of clusters. The lack of
dependence on the surface density of the molecular
clouds indicates that the surface density is a poor
tracer of the IMR and suggests the value of the
IMR is almost independent of the surface density.


We thank the referee for many useful comments that
improved the paper. This material is based upon work
supported by the National Science Foundation Graduate
Research Fellowship under Grant No. DDGE-1315231.
This research is supported by NSF grant 1413231 (PI: K.
Johnson). This paper makes use of the following ALMA
data: ADS/JAO.ALMA#2011.0.00876.S ALMA is a
partnership of ESO (representing its member states),
NSF (USA) and NINS (Japan), together with NRC
(Canada), NSC and ASIAA (Taiwan), and KASI (Republic of Korea), in cooperation with the Republic of
Chile. The Joint ALMA Observatory is operated by
ESO, AUI/NRAO, and NAOJ. The National Radio Astronomy Observatory is a facility of the National Science Foundation operated under cooperative agreement
by Associated Universities, Inc.



REFERENCES



Arp, H., & Sandage, A. 1985, AJ, 90, 1163

Baumgardt, H., & Kroupa, P. 2007, MNRAS, 380, 1589

Bigiel, F., Leroy, A., Walter, F., et al. 2008, AJ, 136, 2846

Bolatto, A. D., Leroy, A. K., Rosolowsky, E., Walter, F., &

Blitz, L. 2008, ApJ, 686, 948

Bolatto, A. D., Wolfire, M., & Leroy, A. K. 2013, ARA&A, 51,

207

Brogan, C., Johnson, K., & Darling, J. 2010, ApJL, 716, L51

Cabrera-Ziri, I., Bastian, N., Longmore, S. N., et al. 2015,

MNRAS, 448, 2224

Cappellari, M., & Copin, Y. 2003, MNRAS, 342, 345



Cardelli, J. A., Clayton, G. C., & Mathis, J. S. 1989, ApJ, 345,

245

Conroy, C., & Spergel, D. N. 2011, ApJ, 726, 36
de Mink, S. E., Pols, O. R., Langer, N., & Izzard, R. G. 2009,
A&A, 507, L1
Decressin, T., Charbonnel, C., Siess, L., et al. 2009, A&A, 505,

727

D’Ercole, A., Vesperini, E., D’Antona, F., McMillan, S. L. W., &
Recchi, S. 2008, MNRAS, 391, 825
Diehl, S., & Statler, T. S. 2006, MNRAS, 368, 497

Evans, II, N. J., Dunham, M. M., Jørgensen, J. K., et al. 2009,
ApJS, 181, 321

16



10 [0]


10 1


10 2


10 3



10 [0]


10 1


10 2


10 3



10 4


Age (year)







10 4

10 [6] 10 [7] 10 [8]
Age (year)


10 [0]



10 4

10 [6] 10 [7] 10 [8]
Age (year)


10 [0]



10 1


10 2


10 3



10 1


10 2


10 3







10 4

10 [6] 10 [7] 10 [8]
Age (year)


10 [0]



10 4

10 [6] 10 [7] 10 [8]
Age (year)


10 [0]



70000


60000


50000


40000


30000


20000


70000


60000


50000


40000


30000


20000



10 1


10 2


10 3



10 1


10 2


10 3







10 4


Age (year)



3.0


3.0


2.5


2.0


1.5


1.0


0.5


0.0



**Figure** **13** . The stellar mass to total mass ratio (IMR) is shown as a function of cluster age, with the inclusion criterion for
clusters being _C_ _>_ 1 _._ 52, for a WVT bin luminosity of 3 _._ 6 _×_ 10 [5] K km/s pc [2], 7 _._ 3 _×_ 10 [5] K km/s pc [2], and 14 _._ 5 _×_ 10 [5] K km/s pc [2]

from top to bottom, respectively. Left: The colors of individual points correspond to the median extinction, _A_ _I_, for the clusters
in the bins taken from Whitmore et al. (2010). Right: The colors of individual points correspond to a measure of the surface
brightness of each bin. See Figure 6 for a description of the errors in the calculated IMR( _t_ ) values.

Fall, S. M. 2006, ApJ, 652, 1129
Fall, S. M., & Chandar, R. 2012, ApJ, 752, 96
Fall, S. M., Chandar, R., & Whitmore, B. C. 2005, ApJL, 631,

L133

Fall, S. M., & Zhang, Q. 2001, ApJ, 561, 751
Gao, Y., Lo, K. Y., Lee, S.-W., & Lee, T.-H. 2001, ApJ, 548, 172
Geyer, M. P., & Burkert, A. 2001, MNRAS, 323, 988
Gnedin, O. Y., & Ostriker, J. P. 1997, ApJ, 474, 223
Heyer, M., Krawczyk, C., Duval, J., & Jackson, J. M. 2009, ApJ,
699, 1092
Hills, J. G. 1980, ApJ, 235, 986
Hollyhead, K., Bastian, N., Adamo, A., et al. 2015, MNRAS,
449, 1106
Johnson, K. E., Leroy, A. K., Indebetouw, R., et al. 2015, ApJ,
806, 35
Kennicutt, Jr., R. C. 1989, ApJ, 344, 685
Kirkpatrick, A., Pope, A., Sajina, A., et al. 2017, ApJ, 843, 71
Krause, M., Charbonnel, C., Decressin, T., Meynet, G., &
Prantzos, N. 2013, A&A, 552, A121
Kruijssen, J. M. D., & Longmore, S. N. 2014, MNRAS, 439, 3239
Krumholz, M. R., & McKee, C. F. 2005, ApJ, 630, 250
Lada, C. J., & Lada, E. A. 2003, ARA&A, 41, 57
Leitherer, C., Schaerer, D., Goldader, J. D., et al. 1999a, ApJS,

123, 3
—. 1999b, ApJS, 123, 3
Leroy, A. K., Walter, F., Brinks, E., et al. 2008, AJ, 136, 2782
Leroy, A. K., Hughes, A., Schruba, A., et al. 2016, ApJ, 831, 16
Leroy, A. K., Schinnerer, E., Hughes, A., et al. 2017, ApJ, 846,

71

Li, H., Gnedin, O. Y., Gnedin, N. Y., et al. 2017, ApJ, 834, 69
McKee, C. F., & Ostriker, E. C. 2007, ARA&A, 45, 565
Melnick, J., Moles, M., & Terlevich, R. 1985, A&A, 149, L24
Meurer, G. R., Heckman, T. M., Leitherer, C., et al. 1995, AJ,

110, 2665
Neff, S. G., & Ulvestad, J. S. 2000, AJ, 120, 670
O’Connell, R. W., Gallagher, III, J. S., & Hunter, D. A. 1994,
ApJ, 433, 65
Pelupessy, F. I., & Portegies Zwart, S. 2012, MNRAS, 420, 1503
Peterson, D. E., Caratti o Garatti, A., Bourke, T. L., et al. 2011,
ApJS, 194, 43



17


Rand, R. J., & Kulkarni, S. R. 1990, ApJL, 349, L43
Raskutti, S., Ostriker, E. C., & Skinner, M. A. 2016, ApJ, 829,

130

Renzini, A. 2008, MNRAS, 391, 354
Sanders, D. B., Soifer, B. T., Elias, J. H., et al. 1988, ApJ, 325,

74

Schinnerer, E., Meidt, S. E., Pety, J., et al. 2013, ApJ, 779, 42
Schruba, A., Leroy, A. K., Walter, F., Sandstrom, K., &
Rosolowsky, E. 2010, ApJ, 722, 1699
Schweizer, F., Burns, C. R., Madore, B. F., et al. 2008, AJ, 136,

1482

Solomon, P. M., Rivolo, A. R., Barrett, J., & Yahil, A. 1987,
ApJ, 319, 730
Springel, V., White, S. D. M., Jenkins, A., et al. 2005, Nature,
435, 629
Toomre, A. 1977, in Evolution of Galaxies and Stellar
Populations, ed. B. M. Tinsley & R. B. G. Larson,
D. Campbell, 401
Ueda, J., Iono, D., Petitpas, G., et al. 2012, ApJ, 745, 65
Vogelsberger, M., Genel, S., Springel, V., et al. 2014, MNRAS,
444, 1518
Wei, L. H., Keto, E., & Ho, L. C. 2012, ApJ, 750, 136
Whitmore, B. C. 2004, in Astronomical Society of the Pacific
Conference Series, Vol. 322, The Formation and Evolution of
Massive Young Star Clusters, ed. H. J. G. L. M. Lamers, L. J.
Smith, & A. Nota, 419
Whitmore, B. C., Chandar, R., & Fall, S. M. 2007, AJ, 133, 1067


Whitmore, B. C., & Zhang, Q. 2002, AJ, 124, 1418
Whitmore, B. C., Chandar, R., Schweizer, F., et al. 2010, AJ,
140, 75
Whitmore, B. C., Brogan, C., Chandar, R., et al. 2014, ApJ,
795, 156
Wilson, C. D., Scoville, N., Madden, S. C., & Charmandaris, V.
2000, ApJ, 542, 120
—. 2003, ApJ, 599, 1049
Wilson, C. D., Petitpas, G. R., Iono, D., et al. 2008, ApJS, 178,

189

Young, J. S., Allen, L., Kenney, J. D. P., Lesser, A., & Rownd,
B. 1996, AJ, 112, 1903
Zhang, Q., Fall, S. M., & Whitmore, B. C. 2001, ApJ, 561, 727


</paper>

## Items to check

```json
[
 {
  "path": "data.pi_or_archival_as_stated.evidence[0]",
  "value": "Previously obtained data first presented in Whitmore et al. (2014)",
  "failed_quote": "These data were first presented in Whitmore et al. (2014)"
 }
]
```
