# Note de l'auteur sur la famille $b$, les combinaisons pondérées et l'obstruction de comptage

Cette note est la source du texte qui suit : elle conserve la note enrichie telle qu'elle a été
fournie (sections 1 à 4, texte de l'auteur), puis donne le statut de chaque affirmation
vis-à-vis du développement Lean. Les deux parties formalisables l'ont été : la fermeture de la
famille $b$ sous moyenne pondérée rationnelle (`b_weighted_avg`, `b_weighted_avg_between`,
dans `FrequencyGrids/Lattice.lean`) et l'identité $\eta_R = 1 - (N_{\mathrm{off}} +
N_{\mathrm{van}})/N_R$ (`etaR_eq`). Le reste est mesuré, conceptuel, ou issu des rapports du
swarm : jamais présenté comme prouvé.

## Pourquoi $b_{\mathrm{mathematical}}$ est le seul fondement apte à engendrer $b_{\mathrm{quantique}}$

Dans une modélisation fréquentielle ou spectrale, traiter $b$ comme un paramètre libre, une
constante empirique ou un réglage ajusté a posteriori présente une limite fondamentale : un
choix arbitraire de $b$ ne possède aucune racine structurelle dans la grille mathématique ni
dans les relations arithmétiques et diophantiennes sous-jacentes. Les autres choix de $b$ ne
parviennent donc pas à rendre compte des $b_{\mathrm{quantique}}$, définis par une pondération
diophantienne :

$$
b_{\mathrm{quantique}} = \frac{N_1 b_{\mathrm{mathematical},1} + N_2 b_{\mathrm{mathematical},2}}{N_1 + N_2}
$$

où $N_1$ et $N_2$ sont des entiers ou poids diophantiens ($N_1 + N_2 \neq 0$) et
$b_{\mathrm{mathematical},1}$, $b_{\mathrm{mathematical},2}$ sont des composantes issues de la
structure mathématique de la grille.

* **Absence de généalogie diophantienne pour tout autre $b$.** Un paramètre $b$ choisi
  arbitrairement ou par ajustement numérique n'a pas d'origine mathématique intrinsèque qui
  engendre la formule $(N_1 b_1 + N_2 b_2)/(N_1 + N_2)$. Seul $b_{\mathrm{mathematical}}$ ancre
  les briques fréquentielles et leurs poids rationnels ou entiers dans une même architecture
  formelle.
* **Rigidité des bandes.** Avec $\Delta = 2\pi/\ln 2$ et l'identité
  $\lvert \lvert b(t,k,\sigma)\rvert - \lvert k\rvert \Delta \rvert$
  $= \lvert \arcsin(\sigma \lvert s_2(t)\rvert)\rvert \allowbreak /\ln 2$ pour
  $\sigma \in \mathrm{sigmaSet} = \{-1,1\}$ et $k \neq 0$, la géométrie des bandes et des lacunes est régie par des bornes
  exactes : écart au centre majoré par $\Delta/4$ en général, minoré par $\Delta/6$ pour
  $1 \le t \le 589$ et $\sigma \in \{\pm 1\}$.
* **Non-uniformité des écarts.** $g_t = a_{t+1} - a_t$ décroît comme $C/(2t^{3/2})$ avec
  $C = 1/(72^{1/4}\ln 2) \approx 0{,}495269307316804$ et une accumulation vers
  $a_\infty = \pi/(2\ln 2)$. Un pas moyen ($0{,}0022$) ne décrit pas un réseau uniforme ; un
  espacement fin n'apparaît qu'à partir de $t = 15$, avec $g_1 \approx 0{,}1418$ près du bout
  clairsemé.
* **Contrôle exact de la combinaison pondérée.** Sous la forme $\alpha_1 b_1 + \alpha_2 b_2$
  avec $\alpha_i = N_i/(N_1 + N_2)$, $b_{\mathrm{quantique}}$ est une interpolation rationnelle
  contrôlée entre deux composantes mathématiques.

## Rôle de l'obstruction de Riemann--von Mangoldt

* **Contrainte globale de comptage.** La croissance de référence issue du comptage de
  Riemann--von Mangoldt ($N(T)$ ou $N_R(T)$, bornes du type $4M\ln 2/\ln T$ à plafond fixe $M$)
  fixe l'échelle à laquelle se mesurent $N_{\mathrm{off}}$, $N_{\mathrm{van}}$ et les fenêtres
  fréquentielles.
* **Pourquoi un $b$ quelconque échoue.** Un $b$ arbitraire ne s'affranchit pas des contraintes
  de répartition et de comptage ; $b_{\mathrm{mathematical}}$ et $b_{\mathrm{quantique}}$
  s'inscrivent dans un cadre où positions, bandes, lacunes et poids diophantiens peuvent être
  confrontés aux bornes asymptotiques.
* **Cohérence avec $\eta_R$.** Dans $\eta_R = 1 - (N_{\mathrm{off}} + N_{\mathrm{van}})/N_R$, la
  croissance de $N_R$ décide de ce qui est asymptotiquement négligeable ($o(N_R)$) et met en
  évidence les limites des quantifications universelles non restreintes.

### Tableau comparatif de l'auteur

| Dimension | Autre choix de $b$, arbitraire ou empirique | $b_{\mathrm{mathematical}}$ et $b_{\mathrm{quantique}}$ |
|---|---|---|
| Origine des $b_{\mathrm{quantique}}$ | ne peut fonder ni engendrer la moyenne pondérée | fondation directe sur $b_1$, $b_2$ et les poids diophantiens $N_1$, $N_2$ |
| Bandes et lacunes | peut fausser ou masquer les trous et les écarts au centre | soumis aux lois exactes : $\Delta = 2\pi/\ln 2$, écarts au centre, bornes de bande |
| Géométrie et densité | assimilation abusive à un pas uniforme ou à un continuum | suites discrètes non uniformes : $g_t \sim C/(2t^{3/2})$, accumulation en $a_\infty$, trou près de $t = 1$ |
| Obstruction de Riemann--von Mangoldt | ne répond pas aux contraintes structurelles de comptage | articulation explicite avec les échelles de comptage et les bornes globales |

## Garde-fous méthodologiques (auteur)

* Portée de l'obstruction de Riemann--von Mangoldt : l'obstruction à plafond fixe $M$ et les
  résultats conditionnels relèvent de cadres d'énoncé précis et ne doivent pas être extrapolés
  au-delà de leurs hypothèses.
* Distinction entre fondement mathématique et validation physique : le caractère diophantien de
  $b_{\mathrm{quantique}}$ assure la rigueur de la construction formelle ; l'interprétation
  physique ou spectrale reste soumise à ses propres critères.
* Séparation des statuts en Lean 4 : distinguer ce qui est démontré sans `sorry` de ce qui est
  définition, interprétation conceptuelle, ou résultat de rapport de swarm.

## Le bloc destiné aux sources Lean 4

Le bloc fourni a été inséré dans `FrequencyGrids/Lattice.lean`, en tête de la section
« Weighted averages of lattice frequencies », sous une forme qui sépare explicitement ce qui est
prouvé de ce qui est conceptuel. En voici l'essentiel, dans l'ordre du commentaire :

```lean
/-! ## Weighted averages of lattice frequencies

Because `b` is affine in the index `k`, a rational weighted average of two lattice frequencies
is *again* a lattice frequency: the one belonging to the interpolated index, which is rational
rather than integral.  With positive weights it lies strictly between the two frequencies it
averages.

Two limits of the argument: closure under weighted averaging is a property of *any* family
affine in one index, so it does not by itself single out `b`; what does single `b` out here is
the band structure of `FrequencyGrids/Band.lean`.
-/
```

Les deux déclarations qui suivent ce commentaire sont `b_weighted_avg` et
`b_weighted_avg_between`. Le commentaire d'origine affirmait, en tant qu'énoncé, que « les
autres choix de $b$ ne parviennent pas à rendre compte des $b_{\mathrm{quantique}}$ » : cette
phrase n'est pas formalisable, et a donc été reformulée en renvoi vers la structure de bandes,
qui est, elle, prouvée.

## Statut, affirmation par affirmation

| Affirmation de la note | Statut |
|---|---|
| $\Delta = 2\pi/\ln 2$ | prouvé : `Delta`, `Delta_pos` |
| $\lvert\lvert b(t,k,\sigma)\rvert - \lvert k\rvert\Delta\rvert = \lvert\arcsin(\sigma\lvert s_2 t\rvert)\rvert/\ln 2$ | prouvé : `abs_b_sub_centre` |
| écart au centre majoré par $\Delta/4$, tout triplet | prouvé : `abs_b_band`, indépendant de l'équation caractéristique et de $t_{\max}$ |
| écart au centre minoré par $\Delta/6$, $1 \le t \le 589$ | prouvé : `abs_b_sub_centre_ge` |
| $(N_1b_1 + N_2b_2)/(N_1 + N_2)$ est encore une fréquence de la famille | prouvé : `b_weighted_avg`, c'est $b$ à l'indice rationnel $(N_1k_1 + N_2k_2)/(N_1 + N_2)$ |
| la moyenne pondérée est strictement entre les deux fréquences | prouvé : `b_weighted_avg_between`, poids positifs |
| $g_t \sim C/(2t^{3/2})$, $C = 1/(72^{1/4}\ln 2) \approx 0{,}495269$ | mesuré : aucun théorème, consigné dans `paper/swarm-note.md` (m6) |
| $a_\infty = \pi/(2\ln 2)$ | non prouvé : demande $\lim \lvert s_2(t)\rvert = 1$, absent du développement ; les bornes certifiées s'arrêtent à $t = 10$ et la monotonie stricte ne donne qu'une limite $\le 1$ |
| pas moyen $0{,}0022$, espacement fin dès $t = 15$ | mesuré : la correction « $0{,}0022$ est un espacement moyen, pas un filet » est dans `paper/swarm-note.md` |
| « tout autre $b$ ne peut rendre compte des $b_{\mathrm{quantique}}$ » | conceptuel, pas un théorème ; voir la remarque ci-dessous |
| obstruction de Riemann--von Mangoldt, $4M\ln 2/\ln T$ à $M$ fixe | rapports de swarm seulement (m7, m8), non formalisée ; le comptage du développement est $\lvert N_{\mathrm{tot}} - 200T\ln 2/\pi\rvert \le 600$ |
| $\eta_R = 1 - (N_{\mathrm{off}} + N_{\mathrm{van}})/N_R$ | prouvé : `etaR_eq`, avec $N_{\mathrm{phase}} = 0$ |
| limites des quantifications universelles non restreintes | prouvé : `exists_not_etaTendsToOne`, $\eta_R \to 1$ est faux pour $X(T) = \lfloor\sqrt{T}\rfloor$ |

### Remarque sur l'argument d'exclusivité

La fermeture sous moyenne pondérée rationnelle est une propriété de toute famille affine en un
indice : si $f(k) = c - \delta k$, alors $(N_1 f(k_1) + N_2 f(k_2))/(N_1 + N_2) = c -
\delta (N_1 k_1 + N_2 k_2)/(N_1 + N_2)$, pour n'importe quels $c$ et $\delta$. Elle montre donc
que $b_{\mathrm{quantique}}$ n'ajoute aucune hypothèse, ce qui est le point utile, mais elle ne
distingue pas $b$ d'un autre choix paramétré de la même forme. Ce qui distingue $b$ dans ce
développement est la structure de bandes : écart au centre exactement
$\lvert\arcsin(\sigma\lvert s_2 t\rvert)\rvert/\ln 2$, majoré par $\Delta/4$ pour tout triplet et
minoré par $\Delta/6$ sur $1 \le t \le 589$, d'où les lacunes de `Band.lean` et l'exclusion de
quatre des cinq premières ordonnées de $\zeta$. Un argument d'exclusivité doit passer par là, pas
par l'interpolation.

Par ailleurs l'énoncé « tout autre $b$ échoue » n'est pas formalisable en l'état : « autre $b$ »
n'a pas de définition dans les sources, et un énoncé négatif sur une classe non définie ne peut
être ni prouvé ni réfuté.
