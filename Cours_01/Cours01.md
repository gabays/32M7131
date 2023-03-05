---
marp: true
theme: default
paginate: true
---

<style>
img[alt~="center"] {
  display: block;
  margin: 0 auto;
}
h1 {
  font-size: 46px;
  color: darkred;
}
h2 {
  font-size: 38px;
  color: darkred;
}
</style>

Distant Reading 2: linguistique computationnelle

# Vers le quantitatif

Simon Gabay

<a rel="license" href="http://creativecommons.org/licenses/by/4.0/"><img alt="Licence Creative Commons" style="border-width:0;float:right;\" src="https://i.creativecommons.org/l/by/4.0/88x31.png" /></a>


---
# Du corpus

---
## Le matériau

Comme toute les sciences, la stylistique s'appuie sur des preuves, qu'il s'agit de collecter, puis d'analyser. Ces preuves sont de divers ordres:

1. Énonciation
2. Textualité
3. Syntaxe
4. Rythme et sonorités
5. Lexique
6. Figures

---
## L'intuition computationnelle

1. L'informatique peut-elle nous aider à accélérer ces relevés?
2. L'informatique peut-elle nous aider à relever autre choses?

Les approches computationnelle de la langue, mais aussi de la linguistique, font le pari que oui.

---
## Le corpus

Una approche computationnelle est quantitative, et donc fondée sur des fréquences, mais aussi des différences de fréquence. Celles-ci sont calculées sur des textes, et le choix de ces textes détermine la fiabilité des résultats.

>Une approche quantitative requiert une fondation solide de la base de données et dans l'analyse et la catégorisation des données.
>
>_A quantitative perspective requires a very solid foundation in the preparation of the data base and in the analysis and categorisation of the data._

Jucker, "Corpus pragmatics", 2018

---
## Typologie

On va donc avoir recours à un corpus. Aarts (2011) en propose une typologie simple:
* _Balanced corpora_: on fournit une image plus ou moins représentative d'une langue, d'état de langue, d'un champ…
* _Full-text corpora_: on fournit des textes complets
* _Parallel corpora_: on fournit des textes en plusieurs langues, ou de plusieurs versions d'une même langue (par exemple des dialectes)

Il existe évidemment une tension entre:
* Peu de données richement contextualisées
* Des corpus de grande taille, mais avec peu d'information supplémentaire

---
## Balancement

Aarts propose en 2011 la notion de _balanced corpus_, mais la création de tels corpus a commencé dans les années 60:
* Le _London-Lund Corpus of Spoken English_ (LLC)
* Le _Brown Corpus_ de l'anglais américain écrit
* Le _Lancaster-Oslo-Bergen_ (LOB) de l'anglais britannique écrit.

Nous avons aussi désormais des corpus diachroniquement balancés:
* Le _Early Modern English Medical Texts_ (EMEMT)

---
## Représentativité

>Un corpus est pensé comme représentatif de la variété de langue qu'il est supposé représenté si les découvertes basées sur son contenu peuvent être généralisées à ladite variété de langue.
>
>_A corpus is thought to be representative of the language variety it is supposed to represent if the findings based on its contents can be generalized to the said language variety._

Leech, "The State of the Art in Corpus Linguistics", 1991

---
## Représentativité (II)

Mais la représentativité est un concept fluide, très lié au questions de recherche:
* Faut-il un corpus général?
* Faut-il un corpus spécialisé? Si oui comment?

**Toute prétention à la représentativité et au balancement doit être interprétée en termes relatifs**

---
## Linguistique de corpus vs textométrie

>La textométrie ne se confond pas avec la linguistique de corpus. Toutes deux fondent leurs investigations sur un corpus numérique, dont la constitution est déterminante. Comme son nom l'indique, la linguistique de corpus poursuit un objectif de description et de modélisation de la langue. La textométrie, centrée sur le texte, a pu être mobilisée par diverses sciences humaines (histoire, littérature, sciences politiques...).
>\[La textométrie] se caractérise notamment par certains calculs fondateurs, statistiques (les spécificités, les cooccurrences) ou non (les segments répétés, les concordances), et accorde une place fondamentale au « retour au texte » (bien outillé dans les logiciels) pour interpréter les unités (généralement des mots) sélectionnées par les calculs.
Pincemin, "Sémantique interprétative et textométrie", 2012.

---
### Textométrie vs stylométrie

>La lexicométrie s’est d’abord définie comme étude du vocabulaire, avant qu’on ne parle de logométrie – comme étude globale d’un discours – ou encore de textométrie, comme analyse d’un texte. Le terme de stylométrie, quant à lui, fonde sa spécificité dans la caractérisation d’une écriture.

Magri-Mourgues, "Stylistique et statistiques. Le corpus textuel et hyperbase", 2016,

---
# Les outils

---
## Plus que le mot

Evidemment, ces recherches s'appuient sur le texte numérisé, et donc les mots qui le constitue. En plus de la recherche plein texte, nous pouvons désormais compter sur des outils qui ajoutent un surcroît d'information, et permettent des recherche jusqu'à présent inédites.

Ces informations ne sont cependant pas simples à ajouter, car elles dépendent de choix complexes qui ont un impact très fort sur les résultats lors de la fouille de texte.

---
## Le token

Le token (en français "jeton") n'est pas un mot, c'est une entité lexicale. C'est une chaîne de caractères (_string_) entre deux délimiteurs. Ces délimiteurs sont eux-mêmes une chaîne de caractères (usuellement virgule, point-virgule… éventuellement précédés d'un espace insécable), dont le choix est (relativement libre).

Prenons l'exemple de "aujourd'hui". Nous avons un mot qui est composé de:
1. un token: _aujourd'hui_
2. deux tokens: _aujourd'_ et _hui_
3. trois tokens: _aujourd_, _'_ et _hui_

---
## Le lemmatiseur

* Faire passer de la forme fléchie à son lemme.
* Ce lemme est une forme canonique. Dire qu'elle n'est pas fléchie est problématique: le masculin n'est-il pas aussi fléchi? (cf. notion de flexion zéro)
* Il faut faire la différence entre le lemme et le mot vedette de l'entrée du dictionnaire
* Il faut s'appuyer sur un référentiel, comme _Morphalou_, car il faut éviter qu'un même mot ait deux lemmes (_œil_, _clef_ …)

---

| token |
|-------|
| Je    |
| mange |
| une   |
| pomme |

---

| token | Lemme  |
|-------|--------|
| Je    | je     |
| mange | manger |
| une   | un     |
| pomme | pomme  |

---
## Le POS tagger

On parle de _POS_ pour _part of speech_, "partie du discours". Un _POS tagger_ permet donc d'accoler à chaque token sa nature grammaticale.

Pour cela on utilise un jeu d'étiquettes précis: `N` pour le substantif, `Aj`pour l'adjectif, `D` pour le déterminant… Il en existe plusieurs, et il faut choisir, ce qui n'est pas facile.

Il existe des cas limites, comme l'adjectivation (du participe passé, du participe présent…): comment trancher entre étiquetage morphologique et morpho-syntactique?

En plus de la nature, on peut rajouter des informations supplémentaires: le nombre, le genre, le mode, le temps, la personne…

---

| token | Lemme  |
|-------|--------|
| Je    | je     |
| mange | manger |
| une   | un     |
| pomme | pomme  |

---

| token | Lemme  | CATTEX | UDpos | EAGLES   | MULTEX |
|-------|--------|--------|-------|----------|--------|
| Je    | je     | PROper | PRON  | PRON_PER | Pp     |
| mange | manger | VERcjg | VERB  | V_GVRB   | Vv     |
| une   | un     | DERndf | DET   | ART      | Dn     |
| pomme | pomme  | NOMcom | NOUN  | NN       | Nc     |

---
.


| Token  |
|--------|
|de      |
|ce      |
|trait   |
|perçant |
|mon     |
|coeur   |
|est     |
|blessé  |
| .      |
|C'      |
|est     |
|moi     |


---
.

| Token  | Lemme   | POS    | Morphologie                           |
|--------|---------|--------|---------------------------------------|
|de      | de      | PRE    | MORPH=empty                           |
|ce      | ce      | DETdem | NOMB.=s\|GENRE=m                      |
|trait   | trait   | NOMcom | NOMB.=s\|GENRE=m                      |
|perçant | percer  | VERppa | NOMB.=s\|GENRE=m                      |
|mon     | mon     | DETpos | PERS.=1\|NOMB.=s\|GENRE=m             |
|coeur   | cœur    | NOMcom | NOMB.=s\|GENRE=m                      |
|est     | être    | VERcjg | MODE=ind\|TEMPS=pst\|PERS.=3\|NOMB.=s |
|blessé  | blesser | VERppe | NOMB.=s\|GENRE=m                      |
| .      | .       | PONfrt |                                       |
|C'      | ce      | PROdem | NOMB.=s\|GENRE=n                      |
|est     | être    | VERcjg | MODE=ind\|TEMPS=pst\|PERS.=3\|NOMB.=s |
|moi     | je      | PROper | PERS.=1\|NOMB.=s\|GENRE=x\|CAS=i      |


---

## Le parseur

Le parseur permet de faire de l'analyse syntaxique – en anglais on parle de _syntactic parsing_. Il s'agit désormais, en plus du lemme et de la POS de récupérer la fonction dans la phrase.

Cette approche s'appuie beaucoup sur la grammaire d'arbres adjoints (TAG, _Tree-adjoining grammar_ ) qui représente la phrase sous la forme de graph.

![100% center](images/Recursion-tag-fr.jpg)

Source: [Wikipedia](https://commons.wikimedia.org/wiki/File:Recursion-tag-fr.jpg?uselang=fr)

---

Exemple

> Il aime le pain et le vin.

---
Comment analyser la coordination?

> Il aime <span style="color:red;">le pain et le vin</span> .

> Il aime <span style="color:red;">le pain</span> <span style="color:blue;">et le vin</span> .

> Il aime <span style="color:red;">le pain</span> <span style="color:green;">et</span> <span style="color:blue;">le vin</span> .

---
DeepXML

![100% center](images/analyse_DeepXML.png)

---
UD

![100% center](images/analyse_UD.png)

---
CoNLL

|   | token | Lemme | POS 1 | POS 2 | Morph | Rel. | Fonction  |
|---|-------|-------|-------|-------|-------|------|-----------|
| 1 | Il    | il    | CL    | CLS   | s=suj | 2    | suj       |
| 2 | aime  | aimer | V     | V     | t=pst | 0    | root      |
| 3 | le    | le    | D     | DET   | s=def | 4    | det       |
| 4 | pain  | pain  | N     | NC    | s=c   | 2    | obj       |
| 5 | et    | et    | C     | CC    | s=c   | 4    | coord     |
| 6 | le    | le    | D     | DET   | s=def | 7    | det       |
| 7 | vin   | vin   | N     | NC    | s=c   | 5    | dep_coord |
| 8 | .     | .     | PONCT | PONCT | _     | 2    | ponct     |

---
## Les autres taggeurs

On parle de plus en plus d' _Inside–outside–beginning_ (IOB) format pour les entités nommées.

Une entité nommée est une expression linguistique référentielle. Elle renvoie la plupart du temps à une personne ou un lieu.

Exemple:

> Livia Jeanneret va à Los Angeles

---

| Token     | Entité |
|-----------|--------|
| Livia     |        |
| Jeanneret |        |
| va        |        |
| à         |        |
| Los       |        |
| Angeles   |        |

---

| Token     | Entité |
|-----------|--------|
| Livia     | PER-B  |
| Jeanneret | PER-I  |
| va        | 0      |
| à         | 0      |
| Los       | LOC-B  |
| Angeles   | LOC-I  |
