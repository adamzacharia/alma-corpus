# Repair task for a Claude Code subagent

A methods card has evidence quotes that were not found verbatim in the paper. Below are the rules, the paper, and the failing items. Write ONE JSON object, nothing else, of the form {"repairs": [{"path": ..., "found": true|false, "loc": ..., "quote": ...}, ...]} with one entry per item (path unchanged) to:

    C:\Users\adama\alma-corpus\cards\2025A%26A...694A.215F\gemini4argon\repair_reply.txt

Use the Write tool for that file. Copy each quote character for character from the paper text below; a returned quote is checked mechanically and dropped if it is not in the paper. Do not read any other file, do not run commands, and do not change anything else. Reply with one line when done.

---

## Rules

You check evidence quotes for a methods card extracted from an astronomy paper. Some quotes could not be found verbatim in the paper text, and some stated values came without a quote. For each item: find the passage in the paper that supports the value and copy it VERBATIM (same words and order, at most 40 words; LaTeX markup may be dropped) with its loc (section heading, "abstract", "Table N" or "Figure N caption"). If the paper does not support the value, return found = false and leave quote and loc empty. Use only the paper text. Return one entry per item, with the item's path unchanged.

## Paper

<paper>
Draft version September 27, 2024
Typeset using L [A] TEX **twocolumn** style in AASTeX63


**ALMA** **observations** **of** **super-early** **galaxies:** **attenuation-free** **model** **predictions**


A. [Ferrara](http://orcid.org/0000-0002-9400-7312), [1] S. [Carniani](http://orcid.org/0000-0002-6719-380X), [1] F. di [Mascia](http://orcid.org/0000-0002-9263-7900), [1] R.J. [Bouwens](http://orcid.org/0000-0002-4989-2471), [2] P. [Oesch](http://orcid.org/0000-0001-5851-6649), [3, 4] and S. [Schouws](http://orcid.org/0000-0001-9746-0924) 2


1 _Scuola_ _Normale_ _Superiore,_ _Piazza_ _dei_ _Cavalieri_ _7,_ _50126_ _Pisa,_ _Italy_
2 _Leiden_ _Observatory,_ _Leiden_ _University,_ _NL-2300_ _RA_ _Leiden,_ _Netherlands_
3 _Observatoire_ _de_ _Gen`eve,_ _1290_ _Versoix,_ _Switzerland_
4 _Cosmic_ _Dawn_ _Center_ _(DAWN),_ _Niels_ _Bohr_ _Institute,_ _University_ _of_ _Copenhagen,_ _Jagtvej_ _128,_ _København_ _N,_ _DK-2200,_ _Denmark_


(Revised September 27, 2024)


ABSTRACT


The abundance and blue color of super-early (redshift _z_ _>_ 10), luminous galaxies discovered by
JWST can be explained if radiation-driven outflows have ejected their dust on kpc-scales. To test this
hypothesis, we predict the ALMA detectability of such extended dust component. Given the observed
properties of the galaxy, its observed continuum flux at 88 _µ_ m, _F_ 88, depends on the dust-to-stellar
mass ratio, _ξ_ _d_, and extent of the dust distribution, _r_ _d_ . Once applied to the most distant galaxy known,
GS-z14-0 at _z_ = 14 _._ 32, the fiducial model ( _ξ_ _d_ = 1 _/_ 529) predicts _F_ 88 [fid] [=] [14] _[.]_ [9] _[ µ]_ [Jy,] [and] [a] [dust] [extent]
_r_ _d_ = 1 _._ 4 kpc. If the galaxy is very dust-rich ( _ξ_ _d_ = 1 _/_ 40), _F_ 88 [max] = 40 _._ 1 _µ_ Jy. These values are smaller
( _F_ 88 [fid] [=] [9] _[.]_ [5] _[ µ]_ [Jy)] [if] [the] [dust] [is] [predominantly] [made] [of] [large] [grains] [as] [those] [formed] [in] [SN] [ejecta.]
Forthcoming ALMA observations might come very close to constraining the fiducial predictions of the
outflow-based attenuation-free model. Other super-early galaxies are predicted to be fainter at 88 _µ_ m,
mostly because of their lower SFR compared to GS-z14-0, with fiducial fluxes in the range 2 _−_ 5 _._ 2 _µ_ Jy.


_Keywords:_ galaxies: high-redshift, galaxies: evolution, galaxies: formation



1. INTRODUCTION


The approximately fifteen galaxies discovered so far
by the _James_ _Webb_ _Space_ _Telescope_ (JWST) at redshift _z_ _>_ 10 (Naidu et al. 2022; Arrabal Haro et al.
2023; Hsiao et al. 2023; Wang et al. 2023; Fujimoto et al.
2023a; Atek et al. 2022; Curtis-Lake et al. 2023; Robertson et al. 2023a; Bunker et al. 2023; Tacchella et al. 2023;
Arrabal Haro et al. 2023; Finkelstein et al. 2023; Castellano et al. 2024; Zavala et al. 2024; Helton et al. 2024;
Carniani et al. 2024; Robertson et al. 2023b) have raised
a number of questions concerning early galaxy evolution.
Not only their number significantly overshoots extrapolations and models anchored at lower redshifts, but these
objects also share some peculiar properties whose origin


Corresponding author: Andrea Ferrara

andrea.ferrara@sns.it



constitute a challenging puzzle for ΛCDM-based [1] galaxy
formation scenarios.

At odd with their lower redshift counterparts, many
super-early galaxies are characterised by bright UV luminosities ( _M_ UV _∼−_ _[<]_ 20), steep UV spectral slopes
( _β_ _∼−_ _[<]_ 2 _._ 2), compact sizes (effective radius _r_ _e_ _≈_ 200
pc). The analysis of their Spectral Energy Distribution
suggests large (for their epoch) stellar masses ( _M_ _⋆_ _≈_
10 [9] _M_ _⊙_ ), thus identifying these rare systems as high- _σ_
peaks of the cosmic density field populating the brightend of the luminosity function. Several alternative hy

1 Throughout the paper, we assume a flat Universe with the following cosmological parameters: Ω M = 0 _._ 3075, Ω Λ = 1 _−_ Ω M, and
Ω b = 0 _._ 0486, _h_ = 0 _._ 6774, _σ_ 8 = 0 _._ 826, where Ω _M_, Ω Λ, and Ω _b_ are
the total matter, vacuum, and baryon densities, in units of the
critical density; _h_ is the Hubble constant in units of 100 km s _[−]_ [1],
and _σ_ 8 is the late-time fluctuation amplitude parameter (Planck
Collaboration et al. 2014).

2 A. Ferrara et al.



potheses have been suggested to explain the above properties [2] .

According to the so-called “Attenuation-Free Model”
(AFM, Ferrara et al. 2023; Ziparo et al. 2023; Fiore et al.
2023; Ferrara 2024a,b) bright luminosities and blue colors result from extremely low dust attenuation conditions. These could be due to low absorbing dust column density, or to grain optical properties producing
“gray”, relatively transparent extinction curves (see, e.g.
Markov et al. 2024) at high redshift.
AFM postulates that dust has been produced in supernova (SN) ejecta with standard net [3] yields _y_ _d_ _≈_
0 _._ 1 _M_ _⊙_ /SN. After their injection into the interstellar
medium, grains could either grow by gas-phase heavy
elements accretion and/or be partially destroyed by
shocks. However, at _z_ _>_ 10 the prevailing physical conditions result in timescales of both processes
are longer than the Hubble time, thus making them
ineffective (Ferrara et al. 2016; Hirashita & Aoyama
2019; Mart´ınez-Gonz´alez et al. 2019; Le´sniewska &
Micha�lowski 2019; Dayal et al. 2022; Priestley et al.
2021). The same argument applies to other known dust
sources, such as AGB and evolved stars (Ferrarotti &
Gail 2006; Valiante et al. 2009).
Corroborated by the evidence for significant amounts
of heavy elements in many super-early galaxies (Curti
et al. 2022; Bunker et al. 2023; Calabro et al. 2024),
it is physically sound to assume that dust was also copiously produced by the large number ( _≈_ 10 [7] ) of SNe
in these galaxies. Moreover, due to their very compact
size, Ferrara (2024a) have shown that in a few Myr the
produced dust would completely obscure the galaxy. Instead, _JWST_ spectra indicate extremely small V-band
attenuations, _A_ _V_ _∼_ _<_ 0 _._ 3.
To unify several aspects of the problem, it has been
proposed that, in spite of the large stellar masses,
attenuation-free conditions can be established by outflows (Ziparo et al. 2023; Fiore et al. 2023). As these
objects have most often luminosities exceeding the effective Eddington luminosity for a dusty medium (Ferrara 2024a), which can be to first order translated
in a lower bound on the specific star formation rate


2 These include (a) star formation variability (Mason et al. 2023;

Mirocha & Furlanetto 2023; Pallottini & Ferrara 2023), (b) reduced feedback resulting in a higher star formation efficiency
(Dekel et al. 2023; Li et al. 2023), and (c) a top-heavy IMF (Inayoshi et al. 2022), although see Rasmussen Cueto et al. (2023).
More exotic solutions involving primordial black holes have also
been suggested (Liu & Bromm 2022).

3 That is, after reprocessing by the reverse shock thermalizing the
ejecta



sSFR _>_ 25 Gyr _[−]_ [1], they can launch powerful outflows
driven by radiation pressure on the dust itself.
As _A_ _V_ _∝_ _r_ _d_ _[−]_ [2] [,] [where] _[r]_ _[d]_ [is] [the] [radial] [extent] [of] [the]
dust distribution, the outflow can effectively reduce the
attenuation by transporting dust on larger spatial scales.
For example, expanding the distribution from _r_ _e_ _≈_ 200
pc to _≈_ 2 kpc, would cause a dramatic drop of the UV
optical depth by 100 times, making the galaxy almost
transparent and bright. Thus, AFM predicts that dust
should be significantly more extended than the stars in
super-early galaxies. Moreover, such dust component
should emit thermal far infrared (FIR) continuum due
to grain reprocessing of the absorbed UV/optical light
from the stars within _r_ _e_ .
Here we aim at assessing whether the FIR signal produced by such extended dust distribution produced by
outflows can be detected by the _Atacama Large Millime-_
_ter_ _Array_ (ALMA). The detection depends on several
factors, such as the dust (i) spatial extent, (ii) mass,
and (iii) temperature (including CMB effects), and (iv)
grain optical properties. This experiment represents a
stringent test for the AFM.
In this Letter, we mainly concentrate on the specific, but yet utmost important, case of the most distant galaxy known, GS-z14-0 ( _z_ = 14 _._ 32, Carniani et al.
2024) for which the required ALMA data will become
soon available (DDT 2023.A.00037.S, PI: S. Schouws).
A positive detection would strongly support the idea
that dust is produced by SNe, and subsequently ejected
by outflows outside the galaxy main body. A non detection would instead put meaningful upper limits on early
dust production and properties at these yet basically
unexplored cosmic epochs. We also apply the model to
four additional _z_ _>_ 10 galaxies.


2. FIR DUST CONTINUUM EMISSION


To predict the expected FIR continuum emission, we
first quantify the dust production and its spatial distribution. Next, we compute the dust temperature including CMB and radiative transfer effects. From these
quantities we finally obtain the observed FIR flux from
a given galaxy.


2.1. _Dust_ _production_


At high redshift ( _z_ _>_ 7) dust production can be safely
assumed to be largely dominated by SNe (Todini & Ferrara 2001; Le´sniewska & Micha�lowski 2019; Dayal et al.
2022; Sommovigo et al. 2022; Ferrara et al. 2022; Schneider & Maiolino 2024) as grain growth (Ferrara et al.
2016; Hirashita & Aoyama 2019) is sub-dominant, and
other known sources (AGB and evolved stars, Valiante
et al. 2009) have evolutionary times exceeding the Hubble time (294 Myr at _z_ = 14 _._ 32).

Dust in blue monsters 3


**Figure** **1.** _Top_ _panel_ : Temperature distribution as a function of the dust spatial distribution radius, _r_ _d_, in units of the effective
stellar radius of GS-z14-0, _r_ _e_ = 260 pc. The different orange curves span the dust-to-stellar ratio range _−_ 5 _<_ log _ξ_ _d_ _<_ _−_ 1 _._ 6
equally spaced in 0.1 logarithmic intervals, with the black curve highlighting the fiducial case log _ξ_ _d_ = _−_ 2 _._ 72( _ξ_ _d_ = 1 _/_ 529). Also
shown is the CMB temperature at the galaxy redshift _z_ = 14 _._ 32, The circles indicate the radius for which _A_ _V_ of the galaxy
matches the observed one, _A_ _V_ = 0 _._ 31. _Bottom_ _panel_ : As in the top panel, but for the predicted observed flux from GS-z14-0 at
88 _µ_ . Also shown are the expected 3 _σ_ sensitivity limit (18 _µ_ Jy/beam), and spatial resolution (0.418”) of the DDT 2023.A.00037.S
(PI: S. Schouws) observations.



We assume that stars form according to a Salpeter
Initial Mass Function in the range 1 _−_ 100 _M_ _⊙_ . As a
result, a SN occurs every _ν_ _[−]_ [1] = 52 _._ 9 _M_ _⊙_ of stars formed.
The dust yield per SN is rather uncertain as it involves
complex nucleation physics of heavy elements in the SN
ejecta. Also, newly formed grains are subject to destruction processes when they pass through the reverse shock.
The net production yield is therefore poorly constrained,
but based also on local SN studies (Matsuura et al. 2015;
Rho et al. 2018; Priestley et al. 2021; Niculescu-Duvaz
et al. 2021), it ranges from 0.01 to 1.1 _M_ _⊙_ . Therefore
we use _y_ _d_ = 0 _._ 1 _M_ _⊙_ as a fiducial value.
Given the IMF, this corresponds to a dust-to-stellar
ratio _ξ_ _d_ = _y_ _d_ _ν_ = 1 _/_ 529. However, given the above un


certainties, we explore the implications of the wide range
of values _−_ 5 _<_ log _ξ_ _d_ _<_ _−_ 1 _._ 6. This range should therefore encompass both a situation in which freshly formed
dust is heavily destroyed by the reverse shock, and a
super-efficient dust condensation under very favourable
conditions.

For the fiducial value of _ξ_ _d_ and the measured stellar
mass of GS-z14-0 ( _M_ _⋆_ = 4 _×_ 10 [8] _M_ _⊙_ ; Carniani et al.
2024), we find that 7 _._ 5 _×_ 10 [5] _M_ _⊙_ of dust should have been
produced by the time of the observation. We recall that
dust typically condenses in the ejecta few hundreds of
days after the explosion (Todini & Ferrara 2001; Nozawa
et al. 2007). For our purposes dust production can be
considered as instantaneous, and occurring on the same

4 A. Ferrara et al.



evolutionary timescale of SN massive star progenitors,
i.e., _∼_ _<_ 20 Myr.


2.2. _Dust_ _spatial_ _distribution_


Initially, the dust is distributed as the observed massive stars providing the observed rest frame UV luminosity. In GS-z14-0, these are distributed within a
measured effective radius _r_ _e_ = 260 pc. Under this
hypothesis, the dust optical depth at 1500 [˚] A would
be equal to _τ_ 1500 _[e]_ [=] [(] _[κ]_ [1500] _[ξ]_ _[d]_ _[/]_ [4] _[πr]_ _e_ [2] [)] _[M]_ _[⋆]_ [=] [23] _[.]_ [3,] [hav-]
ing used a value of the dust mass absorption coefficient
_κ_ 1500 = 1 _._ 26 _×_ 10 [5] cm [2] g _[−]_ [1] appropriate for a MW-like
extinction curve (Weingartner & Draine 2001, WD01).
By translating the observed _A_ _V_ = 0 _._ 31 value into an
optical depth, using _τ_ 1500 = 2 _._ 655( _A_ _V_ _/_ 1 _._ 086), where the
pre-factor accounts for the differential attenuation between 1500 [˚] A and the V-band for a MW curve, we find
_τ_ 1500 = 0 _._ 76, a value _≈_ 30 times smaller than _τ_ 1500 _[e]_ [.]
Using the AFM to predict the star formation history
of GS-z14-0, Ferrara (2024b) found that this galaxy has
recently undergone a super-Eddington phase in which a
powerful outflow has mini-quenched its star formation
leaving it in the observed post-stardust phase. The outflow has ejected a significant fraction of the dust, metals
and gas previously contained in _r_ _e_ .
From the previous estimates we see that to decrease
_A_ _V_ to its observed value, the dust has to be reconfigured by the outflow into a much more extended
distribution of radius _r_ _d_ = ( _τ_ 1500 _[e]_ _[/τ]_ [1500] [)] [1] _[/]_ [2] _[r]_ _[e]_ [=] [5] _[.]_ [5] _[r]_ _[e]_ [,]
which corresponds to _r_ _d_ _≃_ 1 _._ 4 kpc, for the fiducial _ξ_ _d_
value.

Without the outflow hypothesis, to make the galaxy
optically thin one should assume an extremely low dust
content, corresponding to _ξ_ _d_ = 6 _._ 6 _×_ 10 _[−]_ [5] . For comparison, for galaxies in the REBELS sample (Bouwens
et al. 2022) _ξ_ _d_ _≈_ 0 _._ 01 (Ferrara et al. 2022; Dayal et al.
2022; Sommovigo et al. 2022). The results presented below explore both (and additional) possibilities showing
that ALMA observations can clearly discriminate between these two alternative scenarios by detecting the
FIR dust emission.


2.3. _Dust_ _temperature_


Dust grains are heated by absorption of UV photons
whose energy is re-emitted in the FIR. Depending on the
assumed spatial distribution, grains can achieve different
temperatures, thus affecting the emitted FIR flux. The
latter is computed here at a rest frame wavelength of
88 _µ_ m since high- _z_ ALMA observations are often tuned
to detect [OIII] 88 _µ_ m line emission (Popping 2022; Bakx
et al. 2022; Kaasinen et al. 2022; Fujimoto et al. 2023b;
Kohandel et al. 2023)



The emitted radiation spectrum is classically modelled
(e.g. Dayal et al. 2010; Hirashita et al. 2014) as a greybody at mean dust temperature, _T_ [¯] _d_, given by



¯ _L_ abs
_T_ _d_ =
� Θ _M_ _d_



1 _/_ (4+ _β_ _d_ )
_,_ (1)
�



where



_κ_ 88

Θ = [8] _[π]_

_c_ [2] _ν_ 88 _[β]_ _[d]_



_k_ _B_ [4+] _[β]_ _[d]_
_ζ_ (4 + _β_ _d_ )Γ(4 + _β_ _d_ ) _,_ (2)
_h_ [3+] _P_ _[β]_ _[d]_



and _L_ abs = _L_ bol (1 _−_ _e_ _[−][τ]_ [1500] ) is the fraction of the stellar UV radiation that is absorbed by dust. The galaxy
bolometric luminosity is written as _L_ bol = _f_ bol _L_ 1500,
where the intrinsic galaxy luminosity at 1500A [˚] ( _L_ 1500 )
is obtained from the inferred star formation rate (SFR),
via a conversion factor, _K_ 1500 [ _L_ _⊙_ _/M_ _⊙_ yr _[−]_ [1] ], whose
value has been chosen so to match the one used by
the ALMA REBELS survey (Bouwens et al. 2022):
_K_ 1500 _≡_ _L_ 1500 _/_ SFR = 0 _._ 587 _×_ 10 [10] . Following Fiore
et al. (2023), we adopt _f_ bol = 2.
We take the mass absorption coefficient _κ_ 88 and _β_ _d_
consistently with the adopted WD01 extinction curve
_κ_ 88 = 34 _._ 15 cm [2] g _[−]_ [1], and _β_ _d_ = 2 _._ 03; _ζ_ and Γ are the
Zeta and Gamma functions, respectively; finally, _ν_ 88 is
the frequency corresponding to wavelength _λ_ = 88 _µ_ m.
Other symbols have the usual meaning.
The temperature in eq. 1 is a mean (or “effective”)
physical dust temperature such that energy balance between dust absorbed and emitted photon energy is guaranteed. In general, though, radiative transfer effects
produce a temperature distribution, with _T_ _d_ decreasing
away from the source. It is therefore necessary to include
a correction factor which becomes important when the
system becomes optically thick.

Ferrara et al. (2022, see their Appendix A) showed
that the luminosity-weighted temperature, _⟨T_ _d_ _⟩_ _L_, of an
absorbing dust slab depends on its total optical depth,
and can be written as

_⟨T_ _d_ _⟩_ _L_ = _T_ [¯] _d_ 67 _[τ]_ [ 1] 1500 _[/b]_ (1(1 _− −_ _ee_ _[−][−][τ]_ [7] [1500] _[τ]_ [1500] ) _[/b]_ [7] _[/b]_ ) _[≡]_ _[T]_ [¯] _[d]_ _[f]_ _[L]_ [(] _[τ]_ [1500] [)] _[,]_ (3)


where _b_ = 4 + _β_ _d_ . Applying eq. 3 results in temperatures that are generally higher [4] than _T_ [¯] _d_ . To conserve energy _M_ _d_ must be reduced by a factor _f_ _L_ _[−]_ [(4+] _[β]_ _[d]_ [)] .
In the following we denote this reduced dust mass by
_M_ _d_ _[′]_ [=] _[ f]_ _L_ _[ −]_ [(4+] _[β]_ _[d]_ [)] _M_ _d_ .


4 We neglect self-heating by the dust, i.e. absorption of thermal
IR radiation emitted by the grains, as it becomes important at
high optical depth (Gordon et al. 2017), while the configurations
of interest here have _A_ _V_ _<_ 1.

Dust in blue monsters 5


**Figure** **2.** Same as Fig. 1, but assuming that the dust is constituted by large silicate grains with a log-normal distribution
centered at 0.5 _µ_ m, appropriate for grains freshly formed in SN ejecta.



2.4. _Observed_ _flux_ _at_ _88µm_


From the previous results it is straightforward to compute the restframe 88 _µ_ m specific flux from a source at
_z_ = _z_ _s_ observed at wavelength 88(1 + _z_ _s_ ) _µ_ m:


_F_ 88 = _g_ ( _z_ _s_ ) _κ_ 88 _M_ _d_ _[′]_ [[] _[B]_ [88] [(] _[T]_ _[ ′]_ _d_ [)] _[ −]_ _[B]_ [88] [(] _[T]_ [CMB] [)];] (4)


_B_ _λ_ is the black-body spectrum, and _T_ CMB ( _z_ ) = _T_ 0 (1 +
_z_ _s_ ), with _T_ 0 = 2 _._ 7255 K (Fixsen 2009) is the CMB temperature at redshift _z_ _s_ . Equation 4 accounts for the
fact that the CMB acts as a thermal bath for dust

grains, setting a lower limit to their temperature. At
_z_ _s_ = 14 _._ 32 such minimum temperature corresponds to
_T_ CMB = 41 _._ 75 K. Finally, _T_ _d_ _[′]_ [is] [the] [CMB-corrected] [dust]



temperature [5] following Da Cunha et al. (2013),


_T_ _d_ _[′]_ [=] _[ {⟨][T]_ _[d]_ _[⟩]_ [4+] _L_ _[β]_ _[d]_ + _T_ 0 [4+] _[β]_ _[d]_ [(1 + _z_ ) [4+] _[β]_ _[d]_ _−_ 1] _}_ [1] _[/]_ [(4+] _[β]_ _[d]_ [)] _._ (5)


3. RESULTS


Fig. 1 summarises our predictions for the ALMA dust
continuum emission from GS-z14-0. The top (bottom)
panel shows the dependence of the luminosity-weighted
dust temperature (88 _µ_ m flux) for a spherical dust distribution of varying radius _r_ _d_, normalised to the observed
effective stellar radius, _r_ _e_, of the galaxy. Each curve
corresponds to a dust-to-stellar ratio, _ξ_ _d_, in the range
_−_ 5 _<_ log _ξ_ _d_ _<_ _−_ 1 _._ 6 equally spaced in 0.1 logarithmic
intervals with the black curve highlighting the fiducial
case log _ξ_ _d_ = _−_ 2 _._ 72, or _ξ_ _d_ = 1 _/_ 529.


5 In the remainder of the paper we will always refer to dust temperature as the _CMB-corrected_ one, i.e. _T_ _d_ _[′]_ [in] [eq.] [5][.]

6 A. Ferrara et al.



The luminosity-weighted temperature trend can be
understood with the help of eq. 3. Along each orange
curve the dust mass _M_ _d_ = _ξ_ _d_ _M_ _⋆_ is fixed. The most
evident feature is the dust temperature decrease from
110 _−_ 125 K at _r_ _d_ = _r_ _e_ to the CMB temperature at the
largest considered radii (17 _._ 5 kpc), where the dust becomes virtually undetectable. The temperature drop is
due to the fact that as we consider more extended, and
therefore more optically thin, dust distributions, the absorbed stellar radiation decreases, and the dust becomes
colder. Note that if the dust had not been ejected from
the galaxy, and therefore _r_ _d_ = _r_ _e_, the dust-to-stellar
ratio should be very small (log _ξ_ _d_ = _−_ 4 _._ 2) to yield the
measured _A_ _V_ = 0 _._ 31 (denoted by circles).
On top of this trend, at any given radius the curves
differ by up to 10 _−_ 20% as a result of variations of _M_ _d_
from curve to curve, and due to the fact that for small
radii, most curves (specifically, those with log _ξ_ _d_ _> −_ 4 _._ 2)
correspond to optically thick regimes for which _⟨T_ _d_ _⟩_ _L_ is
slightly larger (see eq. 3). This is easily seen by taking
the optically thick limit _τ_ 1500 _→∞_, in which _⟨T_ _d_ _⟩_ _L_ _∝_
_τ_ 1500 [1] _[/]_ [(4+] _[β]_ _[d]_ [)] . For each curve the circles mark the radius
at which the attenuation matches the observed value
_A_ _V_ = 0 _._ 31 (higher/lower _A_ _V_ values to the left/right).
For each value of _ξ_ _d_, the temperature indicated by the
circle is then the “true” (i.e. predicted) one, within
model assumptions.
The behavior of _F_ 88 in the optically thick regime can
be understood as follows. From eq. 4, further neglecting
CMB effects – which is appropriate given that dust is
hot at small radii, it follows that _F_ 88 _∝_ _M_ _[′]_ _B_ _ν_ ( _⟨T_ _d_ _⟩_ _L_ ) _≃_
_M_ _[′]_ _⟨T_ _d_ _⟩_ _L_ in the Rayleigh-Jeans regime. We have already
seen that _⟨T_ _d_ _⟩_ _L_ _∝_ _τ_ 1500 [1] _[/]_ [(4+] _[β]_ _[d]_ [)] ; also, _M_ _d_ _[′]_ [=] _[f]_ _L_ _[ −]_ [(4+] _[β]_ _[d]_ [)] _M_ _d_ _∝_
_τ_ 1500 _[−]_ [1] [.] [Hence,] _[F]_ [88] [decreases] [as] _[τ]_ _[ −]_ 1500 [(3+] _[β]_ _[d]_ [)] _[/]_ [(4+] _[β]_ _[d]_ [)], which is
exactly the trend shown in Fig. 1.
The corresponding 88 _µ_ m flux is shown in the bottom
panel, where it is also compared with the expected 3 _σ_
continuum sensitivity (18 _µ_ Jy/beam) and spatial resolution (0.451”) of the ALMA DDT 2023.A.00037.S (PI: S.
Schouws) observations of GS-z14-0. For each _ξ_ _d_ value,
the flux raises, reaches a peak (approximately where
_τ_ 1500 _≈_ 1), and decreases at large radii. The amplitude
of the peak correlates with _ξ_ _d_ . As the distribution becomes optically thick for small _r_ _d_ _/r_ _e_ values, the curves
with larger _ξ_ _d_ (or, equivalently, larger _M_ _d_ ) converge to
a single line.
By looking at the circles ( _A_ _V_ = 0 _._ 31) we see that the
fiducial model (black line, _ξ_ _d_ = 1 _/_ 529) predicts a 88 _µ_ m
flux _F_ 88 [fid] [= 14] _[.]_ [9] _[ µ]_ [Jy, essentially at the 3] _[σ]_ [ detection limit]
of the experiment, and a luminosity-weighted temperature of 72 K. As _ξ_ _d_ is decreased, implying an efficient
grain destruction by interstellar shocks, the signal be


comes weaker and more difficult to detect. However, if
the galaxy is dust-rich, at or above the level observed in
some of the REBELS galaxies showing _ξ_ _d_ _≈_ 0 _._ 01 (Ferrara et al. 2022; Dayal et al. 2022; Inami et al. 2022),
the signal becomes detectable.
It is important to recall that the observed _F_ 88 measurement (or upper limit) should be interpreted along
with the constraints provided by the observed _A_ _V_ value.
For example, suppose that – consistently with the fiducial model in Fig. 2 – _F_ 88 is measured to be 14 _._ 9 _µ_ Jy
(circle on black curve). Then, we would conclude that
_ξ_ _d_ = 1 _/_ 529, and log( _r_ _d_ [fid] _[/r]_ _[e]_ [)] _[≃]_ [0] _[.]_ [7,] [or] _[r]_ _[d]_ [=] [1] _[.]_ [3] [kpc.]
If correct, ALMA observations should also show that
the dust is spatially resolved, and more extended than
the stellar component. The other, more compact solution for the same _F_ 88, i.e. log( _r_ _d_ _/r_ _e_ ) _≃_ 0 _._ 4, should be
discarded because the galaxy would have an _A_ _V_ much
larger than observed.
A natural case to explore is the one in which the dust,
in the absence of any ejective event, remains within _r_ _e_ .
In this scenario, the temperature would be significantly
higher ( _≃_ 100 K) and the distribution optically thick.
These two properties act as to dramatically suppress
the flux: independently of _ξ_ _d_ (unless extremely small),
_F_ 88 = 5 _._ 3 _µ_ Jy. Detecting such a low flux would require
very long integration times.
In conclusion, a positive detection would strongly support the hypothesis that dust produced by SNe associated with the observed stars in GS-z14-0 has been car
ried to larger galactocentric radii by outflows, making
the galaxy bright and transparent to UV radiation. This
conclusion highlights the key importance of ALMA deep
observations of super-early galaxies.


3.1. _Large_ _grains_


In addition to dust ejection or destruction by shocks,
we need to consider a third possibility, i.e., that early
dust is constituted by large, 0 _._ 1 _−_ 1 _µ_ m size grains. The
need is based on two facts: (a) theoretically, it is predicted that SN dust lacks small grains which are preferentially destroyed in the ejecta by the reverse shock
(Nozawa et al. 2007; Asano et al. 2013; Hirashita &
Aoyama 2019), (b) experimentally, the SED of galaxies
in _z_ = 2 _−_ 12 _JWST_ -detected galaxies show an increasingly flatter extinction curve towards high- _z_ (Di Mascia
et al. 2021; Markov et al. 2024). These two evidences
are clearly connected as large grains of size _a_ absorb
light with wavelength _λ ≪_ _a_ in a frequency-independent
way. In this case, the absorption cross section should
be equal to the geometric one, and the UV absorption
coefficient _κ_ [large] UV _≃_ 3 _/_ 4 _δ_ _g_ _a_, where _δ_ _g_ = 2 _._ 95 gcm _[−]_ [3] is
the material density of silicate grains, i.e. those pref

Dust in blue monsters 7


**Table** **1.** Relevant properties of the selected super-early galaxies at _z_ _>_ 10


ID redshift _A_ _V_ [mag] SFR [M _⊙_ yr _[−]_ [1] ] log( _M_ _⋆_ _/_ M _⊙_ ) _r_ _e_ [pc] _F_ 88 [fid] [[] _[µ]_ [J][y]] _F_ 88 [max] [ _µ_ Jy] log( _r_ _d_ [fid] _[/][r]_ _[e]_ [)]
GS-z14-0 _[a]_ 14.32 0 _._ 31 [+0] _−_ 0 _[.]_ _._ [14] 17 22 [+6] _−_ 6 8 _._ 60 [+0] _−_ 0 _[.]_ _._ [7] 2 260 [+2] _−_ 2 14.9 40.1 0.73
GS-z14-1 _[a]_ 13.90 0 _._ 20 [+0] _−_ 0 _[.]_ _._ [11] 07 2 [+0] _−_ 0 _[.]_ _._ [7] 4 8 _._ 00 [+0] _−_ 0 _[.]_ _._ [4] 4 _<_ 160 2.0 3.8 0.70
UNCOVER-z12 _[b]_ 12.39 0 _._ 19 [+0] _−_ 0 _[.]_ _._ [17] 10 3 _._ 08 [+1] _−_ 0 _[.]_ _._ [81] 68 8 _._ 35 [+0] _−_ 0 _[.]_ _._ [21] 16 426 [+40] _−_ 42 4.4 8.5 0.47
GS-z11-0 _[c]_ 11.58 0 _._ 18 [+0] _−_ 0 _[.]_ _._ [06] 06 2 _._ 20 [+0] _−_ 0 _[.]_ _._ [28] 22 8 _._ 67 [+0] _−_ 0 _[.]_ _._ [08] 13 77 _[†]_ 5.2 7.8 1.38
GHZ2 _[d]_ 12.34 0 _._ 04 [+0] _−_ 0 _[.]_ _._ [07] 03 5 _._ 2 [+1] _−_ 0 _[.]_ _._ [1] 6 9 _._ 05 [+0] _−_ 0 _[.]_ _._ [10] 25 105 [+9] _−_ 9 3.4 4.0 1.76


Note—The measured values are taken from the following references: _[a]_ Carniani et al. (2024); Robertson et al. (2023b), _[b]_ Wang
et al. (2023); Fujimoto et al. (2023a); Atek et al. (2022), _[d]_ Curtis-Lake et al. (2023); Robertson et al. (2023a), _[d]_ Castellano
et al. (2024); _[†]_ Error not provided. The last three columns show the predictions of the model for the fiducial (maximum) 88 _µ_ m
observed flux, and the fiducial dust-to-stellar radius ratio for which _A_ _V_ matches the observed value, respectively.



erentially produced by SNe. Note that if _a_ = 0 _._ 5 _µ_ m,
_κ_ [large] UV = 0 _._ 04 _κ_ UV .
These estimates are confirmed by detailed calculations
performed by Ysard et al. (2019) that we use here. These
authors compute the optical properties of 0 _._ 01 _µ_ m to 10
cm grains from effective medium and Mie theories. To
this aim they assume a lognormal distribution of grain
sizes centered at a given radius, _a_ 0, which we assume to
be equal to 0.5 _µ_ m according to the previous discussion,
and a fixed dispersion _σ_ = 0 _._ 7. With these assumptions
they indeed find _κ_ [large] UV _≃_ 3 _/_ 4 _δ_ _g_ _a_ = 5085 cm [2] g _[−]_ [1], and
_κ_ [large] 88 = 15 cm [2] g _[−]_ [1] .
Fig. 2 presents the temperature and expected flux if
dust is composed by large _≃_ 0 _._ 5 _µ_ m grains. The temperature follows the same trend as in the standard case,
but it is significantly colder, reaching at _r_ _e_ values in the
range 75 _−_ 85 K. As a result, for any given _ξ_ _d_, the flux is
smaller, e.g. _F_ 88 [fid] [= 9] _[.]_ [5] _[µ]_ [Jy,] [and] [shifted] [to] [smaller] [radii]
compared to the standard case. Also, the lower opacity of large grains allows the galaxy to become optically
thin (as observed) for more compact distributions.


3.2. _Other_ _super-early_ _galaxies_


Our model can be used to make predictions on the FIR
observability of other potentially detectable super-early
galaxies. In addition to GS-z14-0, which has the largest
_A_ _V_ among _z_ _>_ 10 spectroscopically confirmed galaxies, we have selected the next three dustiest galaxies,
GS-z14-1 ( _A_ _V_ = 0 _._ 20), UNCOVER-z12 (0.19), GS-z110 (0.18). We have also included GHZ2 in spite of its very
low attenuation ( _A_ _V_ = 0 _._ 04, Castellano et al. 2024, but
see Zavala et al. 2024 who find _A_ _V_ = 0 _._ 01 _−_ 0 _._ 2 depending of the SED fitter used) because of its very interesting
spectrum showing many prominent emission lines.
The relevant properties (redshift, _A_ _V_, SFR, _M_ _⋆_, _r_ _e_ )
of the galaxies in the sample are reported in Tab. 1,
along with the predicted value of the fiducial 88 _µ_ m flux,



and the radius _r_ _d_ [fid] where the attenuation becomes equal
to the observed _A_ _V_ value. Also shown is the maximum
expected flux, _F_ 88 [max] which we take from the curve with
the maximum assumed value of log _ξ_ _d_ = _−_ 1 _._ 6.
For the galaxies in the sample the dust temperature
and the FIR flux follow very similar trends with _r_ _d_ _/r_ _e_ as
shown in Fig. 1 for GS-z14-0, albeit they quantitatively
differ as a result of the different properties of the galaxy.
From the Table, we see that the expected fiducial fluxes
range from 2 _µ_ Jy for the faintest galaxy (GS-z14-1) to
14.9 _µ_ Jy for the brightest (and most distant) one, GSz14-0; the latter therefore remains the most promising
target to constrain the dust content of the very early
galaxies. For GHZ2, if we instead assume the largest
attenuation found by Zavala et al. (2024), _A_ _V_ = 0 _._ 2, we
find a larger fiducial and maximum flux, _F_ 88 [fid] [= 11] _[.]_ [2] _[ µ]_ [Jy,]
and _F_ 88 [max] = 16 _._ 3 _µ_ Jy, respectively.
Finally, notice that we did not considered the remarkable galaxy GN-z11 (Bunker et al. 2023) as it is not visible by ALMA due to its northern emisphere location.
However, this galaxy has been observed by the Northern Extended Millimeter Array (NOEMA, Fudamoto
et al. 2023). These observations, have put a 1 _σ_ upper limit of 13 _µ_ Jy/beam at 160 _µ_ m. When applied to
GN-z11, our model (fiducial case) predicts a maximum
flux _F_ 160 [max] = 14 _._ 1 _µ_ Jy. Although interesting, available
NOEMA observations are unfortunately too shallow to
detect the expected signal.


4. SUMMARY


To test one of the predictions of the “AttenuationFree Model” (Ferrara et al. 2023; Ferrara 2024a), we
have modelled the FIR dust continuum emission from

the extended dust distribution produced by outflows
around “blue monsters”, i.e. luminous, blue, super-early
( _z_ _>_ 10) galaxies. Given the observed properties of
the galaxies (redshift, _A_ _V_, SFR, _M_ _⋆_, _r_ _e_ ), the expected

8 A. Ferrara et al.



flux at 88 _µ_ m depends on the dust-to-stellar ratio, _ξ_ _d_,
and extent of the dust distribution, _r_ _d_ . A signal detection with ALMA would therefore constrain the amount

of dust and its extent, thus representing a successful
test that the attenuation-free conditions are produced
by dust ejection by (likely, radiation-driven) outflows.
We have discussed in detail GS-z14-0 ( _z_ = 14 _._ 32), and
further applied the model to other 4 super-early galaxies. We find that:


 - If the dust is in the galaxy ( _r_ _d_ = _r_ _e_ ) its temperature is 110 _−_ 125 K. In this case, though, the dustto stellar mass ratio must be very small (log _ξ_ _d_ _<_
_−_ 4 _._ 2) not to exceed the measured _A_ _V_ = 0 _._ 31. For
_r_ _d_ _>_ _r_ _e_, _⟨T_ _d_ _⟩_ _L_ decreases asymptotically towards
_T_ CMB (Fig. 1, top panel).


 - The fiducial model ( _ξ_ _d_ = 1 _/_ 529) predicts for GSz14-0 an observed flux _F_ 88 [fid] = 14 _._ 9 _µ_ Jy, and a
dust extent _r_ _d_ _∼_ 1 _._ 4 kpc (Fig. 1, bottom panel).
For the largest value considered, log _ξ_ _d_ = _−_ 1 _._ 6,
_F_ 88 [max] = 40 _._ 1 _µ_ Jy. These values are smaller ( _F_ 88 [fid] [=]
9 _._ 5 _µ_ Jy) if the dust is predominantly made of large
grains as those formed in SN ejecta (Fig. 2).


 - Forthcoming ALMA observations, with an expected 3 _σ_ sensitivity of 18 _µ_ Jy, should come very
close to constraining the fiducial predictions of the
outflow-based attenuation-free model.




 - Other super-early galaxies are predicted (Tab. 1)
to be fainter at 88 _µ_ m, mostly because of their
lower SFR compared to GS-z14-0 but also due to
their lower _A_ _V_, with fiducial fluxes in the range
_F_ 88 [fid] [= 2] _[ −]_ [5] _[.]_ [2] _[µ]_ [Jy.]


We conclude by warning that albeit our model is built
to catch the main features of the AFM, its simple incarnation cannot include potentially non-negligible effects
that might quantitatively change our conclusions. For
example, the present study does not account for selfheating of the dust by re-processed thermal photons,
dust scattering and grain size distribution. The impact
of these effects on the results presented here can only be
ascertained via dedicated numerical radiative transfer

simulations.


ACKNOWLEDGMENTS


We thank J. Zavala and M. Castellano for useful

discussions, data and comments. This work is supported by the ERC Advanced Grant INTERSTELLAR
H2020/740120, and in part by grant NSF PHY-2309135
to the Kavli Institute for Theoretical Physics (KITP).
Plots in this paper produced with the matplotlib
(Hunter 2007) package for PYTHON.



REFERENCES



Arrabal Haro, P., Dickinson, M., Finkelstein, S. L., et al.


2023, arXiv e-prints, arXiv:2304.05378,


doi: [10.48550/arXiv.2304.05378](http://doi.org/10.48550/arXiv.2304.05378)


Asano, R. S., Takeuchi, T. T., Hirashita, H., & Inoue, A. K.


2013, Earth, Planets, and Space, 65, 213,


doi: [10.5047/eps.2012.04.014](http://doi.org/10.5047/eps.2012.04.014)


Atek, H., Shuntov, M., Furtak, L. J., et al. 2022, Revealing


Galaxy Candidates out to _z_ _∼_ 16 with JWST


Observations of the Lensing Cluster SMACS0723, arXiv,


doi: [10.48550/ARXIV.2207.12338](http://doi.org/10.48550/ARXIV.2207.12338)


Bakx, T. J. L. C., Zavala, J. A., Mitsuhashi, I., et al. 2022,


arXiv e-prints, arXiv:2208.13642.


[https://arxiv.org/abs/2208.13642](https://arxiv.org/abs/2208.13642)


Bouwens, R. J., Smit, R., Schouws, S., et al. 2022, ApJ,


931, 160, doi: [10.3847/1538-4357/ac5a4a](http://doi.org/10.3847/1538-4357/ac5a4a)


Bunker, A. J., Saxena, A., Cameron, A. J., et al. 2023,


arXiv e-prints, arXiv:2302.07256,


doi: [10.48550/arXiv.2302.07256](http://doi.org/10.48550/arXiv.2302.07256)



Calabro, A., Castellano, M., Zavala, J. A., et al. 2024,


arXiv e-prints, arXiv:2403.12683,


doi: [10.48550/arXiv.2403.12683](http://doi.org/10.48550/arXiv.2403.12683)


Carniani, S., Hainline, K., D’Eugenio, F., et al. 2024, arXiv


e-prints, arXiv:2405.18485,


doi: [10.48550/arXiv.2405.18485](http://doi.org/10.48550/arXiv.2405.18485)


Castellano, M., Napolitano, L., Fontana, A., et al. 2024,


arXiv e-prints, arXiv:2403.10238,


doi: [10.48550/arXiv.2403.10238](http://doi.org/10.48550/arXiv.2403.10238)


Curti, M., D’Eugenio, F., Carniani, S., et al. 2022,


MNRAS, doi: [10.1093/mnras/stac2737](http://doi.org/10.1093/mnras/stac2737)


Curtis-Lake, E., Carniani, S., Cameron, A., et al. 2023,


Nature Astronomy, doi: [10.1038/s41550-023-01918-w](http://doi.org/10.1038/s41550-023-01918-w)


Da Cunha, E., Groves, B., Walter, F., et al. 2013, The


Astrophysical Journal, 766, 13


Dayal, P., Hirashita, H., & Ferrara, A. 2010, MNRAS, 403,


620, doi: [10.1111/j.1365-2966.2009.16164.x](http://doi.org/10.1111/j.1365-2966.2009.16164.x)


Dayal, P., Ferrara, A., Sommovigo, L., et al. 2022, MNRAS,


512, 989, doi: [10.1093/mnras/stac537](http://doi.org/10.1093/mnras/stac537)

Dust in blue monsters 9



Dekel, A., Sarkar, K. S., Birnboim, Y., Mandelker, N., &

Li, Z. 2023, arXiv e-prints, arXiv:2303.04827,

doi: [10.48550/arXiv.2303.04827](http://doi.org/10.48550/arXiv.2303.04827)


Di Mascia, F., Gallerani, S., Behrens, C., et al. 2021,

MNRAS, 503, 2349, doi: [10.1093/mnras/stab528](http://doi.org/10.1093/mnras/stab528)


Ferrara, A. 2024a, A&A, 684, A207,

doi: [10.1051/0004-6361/202348321](http://doi.org/10.1051/0004-6361/202348321)


—. 2024b, arXiv e-prints, arXiv:2405.20370,

doi: [10.48550/arXiv.2405.20370](http://doi.org/10.48550/arXiv.2405.20370)


Ferrara, A., Pallottini, A., & Dayal, P. 2023, MNRAS, 522,

3986, doi: [10.1093/mnras/stad1095](http://doi.org/10.1093/mnras/stad1095)


Ferrara, A., Viti, S., & Ceccarelli, C. 2016, MNRAS, 463,

L112, doi: [10.1093/mnrasl/slw165](http://doi.org/10.1093/mnrasl/slw165)


Ferrara, A., Sommovigo, L., Dayal, P., et al. 2022, MNRAS,

512, 58, doi: [10.1093/mnras/stac460](http://doi.org/10.1093/mnras/stac460)


Ferrarotti, A. S., & Gail, H. P. 2006, A&A, 447, 553,

doi: [10.1051/0004-6361:20041198](http://doi.org/10.1051/0004-6361:20041198)


Finkelstein, S. L., Leung, G. C. K., Bagley, M. B., et al.

2023, arXiv e-prints, arXiv:2311.04279,

doi: [10.48550/arXiv.2311.04279](http://doi.org/10.48550/arXiv.2311.04279)


Fiore, F., Ferrara, A., Bischetti, M., Feruglio, C., &

Travascio, A. 2023, ApJL, 943, L27,

doi: [10.3847/2041-8213/acb5f2](http://doi.org/10.3847/2041-8213/acb5f2)


Fixsen, D. J. 2009, ApJ, 707, 916,

doi: [10.1088/0004-637X/707/2/916](http://doi.org/10.1088/0004-637X/707/2/916)


Fudamoto, Y., Oesch, P. A., Walter, F., et al. 2023, arXiv

e-prints, arXiv:2309.02493,

doi: [10.48550/arXiv.2309.02493](http://doi.org/10.48550/arXiv.2309.02493)


Fujimoto, S., Wang, B., Weaver, J., et al. 2023a, arXiv

e-prints, arXiv:2308.11609,

doi: [10.48550/arXiv.2308.11609](http://doi.org/10.48550/arXiv.2308.11609)


Fujimoto, S., Finkelstein, S. L., Burgarella, D., et al. 2023b,

ApJ, 955, 130, doi: [10.3847/1538-4357/aceb67](http://doi.org/10.3847/1538-4357/aceb67)


Gordon, K. D., Baes, M., Bianchi, S., et al. 2017, A&A,

603, A114, doi: [10.1051/0004-6361/201629976](http://doi.org/10.1051/0004-6361/201629976)


Helton, J. M., Rieke, G. H., Alberts, S., et al. 2024, arXiv

e-prints, arXiv:2405.18462,

doi: [10.48550/arXiv.2405.18462](http://doi.org/10.48550/arXiv.2405.18462)


Hirashita, H., & Aoyama, S. 2019, MNRAS, 482, 2555,

doi: [10.1093/mnras/sty2838](http://doi.org/10.1093/mnras/sty2838)


Hirashita, H., Ferrara, A., Dayal, P., & Ouchi, M. 2014,

MNRAS, 443, 1704, doi: [10.1093/mnras/stu1290](http://doi.org/10.1093/mnras/stu1290)


Hsiao, T. Y.-Y., Abdurro’uf, Coe, D., et al. 2023, arXiv

e-prints, arXiv:2305.03042,

doi: [10.48550/arXiv.2305.03042](http://doi.org/10.48550/arXiv.2305.03042)


Hunter, J. D. 2007, Computing in Science and Engineering,

9, 90, doi: [10.1109/MCSE.2007.55](http://doi.org/10.1109/MCSE.2007.55)


Inami, H., Algera, H., Schouws, S., et al. 2022, MNRAS,

doi: [10.1093/mnras/stac1779](http://doi.org/10.1093/mnras/stac1779)



Inayoshi, K., Harikane, Y., Inoue, A. K., Li, W., & Ho,

L. C. 2022, ApJL, 938, L10,

doi: [10.3847/2041-8213/ac9310](http://doi.org/10.3847/2041-8213/ac9310)


Kaasinen, M., van Marrewijk, J., Popping, G., et al. 2022,

arXiv e-prints, arXiv:2210.03754.

[https://arxiv.org/abs/2210.03754](https://arxiv.org/abs/2210.03754)


Kohandel, M., Ferrara, A., Pallottini, A., et al. 2023,

MNRAS, 520, L16, doi: [10.1093/mnrasl/slac166](http://doi.org/10.1093/mnrasl/slac166)


Le´sniewska, A., & Micha�lowski, M. J. 2019, A&A, 624, L13,

doi: [10.1051/0004-6361/201935149](http://doi.org/10.1051/0004-6361/201935149)


Li, Z., Dekel, A., Sarkar, K. C., et al. 2023, arXiv e-prints,

arXiv:2311.14662, doi: [10.48550/arXiv.2311.14662](http://doi.org/10.48550/arXiv.2311.14662)


Liu, B., & Bromm, V. 2022, The Astrophysical Journal

Letters, 937, L30, doi: [10.3847/2041-8213/ac927f](http://doi.org/10.3847/2041-8213/ac927f)


Markov, V., Gallerani, S., Ferrara, A., et al. 2024, arXiv

e-prints, arXiv:2402.05996,

doi: [10.48550/arXiv.2402.05996](http://doi.org/10.48550/arXiv.2402.05996)


Mart´ınez-Gonz´alez, S., W¨unsch, R., Silich, S., et al. 2019,

ApJ, 887, 198, doi: [10.3847/1538-4357/ab571b](http://doi.org/10.3847/1538-4357/ab571b)


Mason, C. A., Trenti, M., & Treu, T. 2023, MNRAS, 521,

497, doi: [10.1093/mnras/stad035](http://doi.org/10.1093/mnras/stad035)


Matsuura, M., Dwek, E., Barlow, M. J., et al. 2015, ApJ,

800, 50, doi: [10.1088/0004-637X/800/1/50](http://doi.org/10.1088/0004-637X/800/1/50)


Mirocha, J., & Furlanetto, S. R. 2023, MNRAS, 519, 843,

doi: [10.1093/mnras/stac3578](http://doi.org/10.1093/mnras/stac3578)


Naidu, R. P., Oesch, P. A., van Dokkum, P., et al. 2022,

ApJL, 940, L14, doi: [10.3847/2041-8213/ac9b22](http://doi.org/10.3847/2041-8213/ac9b22)


Niculescu-Duvaz, M., Barlow, M. J., Bevan, A.,

Milisavljevic, D., & Looze, I. D. 2021, The dust mass in

Cassiopeia A from infrared and optical line flux

differences. [https://arxiv.org/abs/2103.12705](https://arxiv.org/abs/2103.12705)


Nozawa, T., Kozasa, T., Habe, A., et al. 2007, ApJ, 666,

955, doi: [10.1086/520621](http://doi.org/10.1086/520621)


Pallottini, A., & Ferrara, A. 2023, arXiv e-prints,

arXiv:2307.03219, doi: [10.48550/arXiv.2307.03219](http://doi.org/10.48550/arXiv.2307.03219)


Planck Collaboration, Ade, P. A. R., Aghanim, N., et al.

2014, A&A, 571, A16, doi: [10.1051/0004-6361/201321591](http://doi.org/10.1051/0004-6361/201321591)


Popping, G. 2022, arXiv e-prints, arXiv:2208.13072.


[https://arxiv.org/abs/2208.13072](https://arxiv.org/abs/2208.13072)


Priestley, F. D., De Looze, I., & Barlow, M. J. 2021,

MNRAS, 502, 2438, doi: [10.1093/mnras/stab122](http://doi.org/10.1093/mnras/stab122)


Rasmussen Cueto, E., Hutter, A., Dayal, P., et al. 2023,

arXiv e-prints, arXiv:2312.12109,

doi: [10.48550/arXiv.2312.12109](http://doi.org/10.48550/arXiv.2312.12109)


Rho, J., Gomez, H. L., Boogert, A., et al. 2018, MNRAS,

479, 5101, doi: [10.1093/mnras/sty1713](http://doi.org/10.1093/mnras/sty1713)


Robertson, B., Johnson, B. D., Tacchella, S., et al. 2023a,

arXiv e-prints, arXiv:2312.10033,

doi: [10.48550/arXiv.2312.10033](http://doi.org/10.48550/arXiv.2312.10033)

10 A. Ferrara et al.



—. 2023b, arXiv e-prints, arXiv:2312.10033,


doi: [10.48550/arXiv.2312.10033](http://doi.org/10.48550/arXiv.2312.10033)


Schneider, R., & Maiolino, R. 2024, A&A Rv, 32, 2,


doi: [10.1007/s00159-024-00151-2](http://doi.org/10.1007/s00159-024-00151-2)


Sommovigo, L., Ferrara, A., Pallottini, A., et al. 2022,


MNRAS, 513, 3122, doi: [10.1093/mnras/stac302](http://doi.org/10.1093/mnras/stac302)


Tacchella, S., Eisenstein, D. J., Hainline, K., et al. 2023,


arXiv e-prints, arXiv:2302.07234,


doi: [10.48550/arXiv.2302.07234](http://doi.org/10.48550/arXiv.2302.07234)


Todini, P., & Ferrara, A. 2001, MNRAS, 325, 726,


doi: [10.1046/j.1365-8711.2001.04486.x](http://doi.org/10.1046/j.1365-8711.2001.04486.x)



Valiante, R., Schneider, R., Bianchi, S., & Andersen, A. C.

2009, MNRAS, 397, 1661,

doi: [10.1111/j.1365-2966.2009.15076.x](http://doi.org/10.1111/j.1365-2966.2009.15076.x)

Wang, B., Fujimoto, S., Labb´e, I., et al. 2023, The

Astrophysical Journal Letters, 957, L34,
doi: [10.3847/2041-8213/acfe07](http://doi.org/10.3847/2041-8213/acfe07)

Weingartner, J. C., & Draine, B. T. 2001, ApJ, 548, 296,
doi: [10.1086/318651](http://doi.org/10.1086/318651)

Ysard, N., Koehler, M., Jimenez-Serra, I., Jones, A. P., &

Verstraete, L. 2019, A&A, 631, A88,

doi: [10.1051/0004-6361/201936089](http://doi.org/10.1051/0004-6361/201936089)

Zavala, J. A., Castellano, M., Akins, H. B., et al. 2024,

arXiv e-prints, arXiv:2403.10491,

doi: [10.48550/arXiv.2403.10491](http://doi.org/10.48550/arXiv.2403.10491)

Ziparo, F., Ferrara, A., Sommovigo, L., & Kohandel, M.
2023, MNRAS, 520, 2445, doi: [10.1093/mnras/stad125](http://doi.org/10.1093/mnras/stad125)


</paper>

## Items to check

```json
[
 {
  "path": "paper_type_evidence[1]",
  "value": "paper type: theory_or_simulation_compared_to_alma",
  "failed_quote": "Here we aim at assessing whether the FIR signal produced by such extended dust distribution produced by outflows can be detected by the Atacama Large Millimeter Array (ALMA)."
 },
 {
  "path": "science.question.evidence[1]",
  "value": "Can the FIR dust continuum emission produced by extended, outflow-ejected dust distributions around super-early (z > 10) galaxies predicted by the Attenuation-Free Model be detected by ALMA?",
  "failed_quote": "Here we aim at assessing whether the FIR signal produced by such extended dust distribution produced by outflows can be detected by the Atacama Large Millimeter Array (ALMA)."
 },
 {
  "path": "processing.inherited[1].what.evidence[0]",
  "value": "MW-like extinction curve and dust mass absorption coefficients (κ_1500 = 1.26 x 10^5 cm^2 g^-1, κ_88 = 34.15 cm^2 g^-1, β_d = 2.03)",
  "failed_quote": "having used a value of the dust mass absorption coefficient κ 1500 = 1 . 26 × 10 5 cm 2 g − 1 appropriate for a MW-like extinction curve (Weingartner & Draine 2001, WD01)."
 },
 {
  "path": "analysis_steps[0].assumptions[0].evidence[1]",
  "value": "Salpeter IMF in the range 1 - 100 M_sun; dust production dominated by SNe and instantaneous on timescale <= 20 Myr",
  "failed_quote": "For our purposes dust production can be considered as instantaneous, and occurring on the same evolutionary timescale of SN massive star progenitors, i.e., ∼ < 20 Myr."
 },
 {
  "path": "analysis_steps[1].key_parameters[0].evidence[0]",
  "value": "κ_1500 = 1.26 x 10^5 cm^2 g^-1 (standard WD01 MW dust); κ_UV^large = 5085 cm^2 g^-1 (large silicate grains, a_0 = 0.5 µm, σ = 0.7, δ_g = 2.95 g cm^-3)",
  "failed_quote": "having used a value of the dust mass absorption coefficient κ 1500 = 1 . 26 × 10 5 cm 2 g − 1 appropriate for a MW-like extinction curve (Weingartner & Draine 2001, WD01)."
 }
]
```
