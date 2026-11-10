

TP Mineure Signal S7
Cours de Communications Numériques
2ème année ENSEA
## Octobre 2025
Les TPs de la Mineure Signal sont réalisés avec Python. Le notebook correspondant à ce TP est disponible sur
Moodle. Répondez aux questions directement sur ce notebook. Votre présence est obligatoire et toute absence
non-justifiée engendre une diminution de note.  Les étudiants qui ne peuvent être présents à cause des raisons
médicales, doivent contacter le.a professeur.e encadrant rapidement et suivre le protocole spécifique qui leur
sera indiqué.
Vous devez valider 3 check-points par séance, avec le.a professeur.e encadrant qui les notera.
A la fin de chaque séance et avant de quitter le poste de travail, chaque binôme a l’obligation d’envoyer à
son encadrant.ele notebook contenant le TP: formules et calculs (peuvent être rendus sur papier en séance),
courbes anotées (limitées à 8 par séance), avec une attention particulière à l’analyse et l’interprétation des ré-
sultats.
Concernant les codes Pythons : suivez les instructions de votre professeur.e encadrant.
## Hint 1 Python :
Utilisezhelp (nomfonction)pour obtenir de l’aide sur une fonction.
Hint 2 Python :pour créer la fonctionmyfunction, utiliser la syntaxe
def myfunction(entree1, entree2, ...):
return sortie1, sortie2

## 2
THEME 1 : Communication en bande de base BPSK
Les trois points à valider pour le Thème 2 sont les suivants.
•Relation entre le rapport signal à bruit (RSB) et le RSB normalisé :
## E
b
## N
## 0
## .
•Canal idéal : comparaison entre le taux d’erreur binaire (simulateur) et la courbe théorique.
•Canal non-idéal : visualisation de la constellation BPSK qui subit des IES,x
n
, n= 0,...,N−1.
Remarques et astuces
Notation : nous allons utiliser la notation des signaux discrètes du module Communications Numériques
telle quex
n
, n= 0,...,N−1représente len-éme échantillon.
Fonctions Python utiles (via les bibliothèques numpy, matplotlib.pyplot, scipy etc.) :numpy.random.rand,
numpy.random.randn, numpy.sign, scipy.signal.lfilter, matplotlib.pyplot.plot,
xlabel, ylabel, title, scipy.special.erfc, numpy.where, len, matplotlib.pyplot.semilogy,
etc.
Hint : Pour tracer le taux d’erreur nous utilisons la méthode de Monte-Carlo : à savoir la simulation
d’un grand nombreNde transmissions binaires.  Parmi lesNsymboles transmis nous calculons
la fréquence empirique des occurrences d’erreur (comparaison entrea
n
etba
n
## ).
1    Canal idéal de Nyquist AWGN
Par  simplicité,  nous  allons  considérer  dans  cette  première  partie  un  canal  idéal  de  Nyquist  avec  un  bruit
additif Gaussien (AWGN), illustré dans la Figure 1. L’objectif sera l’étude de la probabilité d’erreur binaire à
la réception.
## ♢
Chaîne de communication BPSK
•Écrire une fonctiongenBPSKavec pour entréeNet sortie un vecteur deNéchantillons du signal modulé
BPSK :a
n
,n= 0,...,N−1. Vous pouvez utilisernp.random.uniformpour créer une séquence aléatoire
des valeurs entre0et1. Puis, soustrayez−0.5et prenez-en le signe à l’aidenp.sign
## 1
## .
•Créer une fonctiongenBruitNavec pour entrée une valeurσ
## 2
b
et pour sortie une séquence deNéchan-
tillons du bruitb
n
, n= 0,...,N−1aléatoires suivant une loi Gaussienne de moyenne nulle et varianceσ
## 2
b
## .
Vous pouvez utiliser la fonctionnp.random.normal
## 2
## .
•Afin de coder le bloc de décision, créer une fonctiondecodeBPSKavec pour entrée un vecteurr
n
deN
échantillons réels observés à la réception et pour sortie un vecteurba
n
deNéchantillons dans{−1,+1}, qui
## 1
Afin de vérifier le comportement correct degenBPSK, tracer l’histogramme de la sortie.
## 2
Afin de vérifier le comportement correct degenBruitN, tracer l’histogramme de la sortie.

## 3
représentent les estimations des symboles BPSK transmis (a
n
, n= 0,...,N−1).
•Dans le programme principal, simulez la chaîne de communication pourN= 512,σ
## 2
b
## = 0.5etg(0) = 1.
Visualisez le signal modulé BPSK,a
n
, ainsi que le signal estimé,ˆa
n
.  Quel est le taux d’erreur binaire à la
réception, i.e., le ratio entre le nombre de symboles erronés vs. le nombre de symboles transmis (N) ?
## ♢
Taux d’erreur binaire du canal AWGN
•Relier le rapport signal à bruit RSB=
g(0)
## 2
σ
## 2
b
au rapport signal à bruit normalisé
## E
b
## N
## 0
## .
•Pour chaque valeur
h
## E
b
## N
## 0
i
dB
= 0,...12[dB !], calculer la variance du bruitσ
## 2
b
pourg(0) = 1ainsi que le
taux d’erreur binaire correspondants pourN= 512.
•Tracer  la  courbe  du  taux  d’erreur  binaire  en  fonction  de
h
## E
b
## N
## 0
i
dB
= 0,...,12[dB !]pourN= 512.
## Commentez.
•Quelle est la valeur deNminimale afin de pouvoir tracer la courbe du taux d’erreur binaire pour toute la
plage de
h
## E
b
## N
## 0
i
dB
## ?
## ♢
Check-point 1Relation entre le rapport signal à bruit (RSB) et le RSB normalisé :
## E
b
## N
## 0
## .
## ♢
Probabilité d’erreur binaire théorique
•Tracez la courbe de la probabilité d’erreur binaire théorique vue en cours, en fonction du rapport signal à
bruit normalisé
h
## E
b
## N
## 0
i
dB
= 0,...,12[dB !]:
## P
b(min)
(e) =Q

r
## 2E
b
## N
## 0
## !
## .
Vous pouvez utiliser la fonctionsp.erfcpar example.
♢Comparaison des courbes d’erreur : pratique et théorique
•Comparer la courbe pratique (obtenue via simulation) avec la courbe théorique. Commentez.
•Quel est le SNR (en dB) qui permet de garantir pour une probabilité d’erreur binaire d’environ10
## −3
## ?
## ♢
Check-point 2Canal idéal : comparaison entre le taux d’erreur binaire (simulateur) et la courbe théorique.
Figure 1: Chaîne de communication en bande de base d’un signal BPSK à travers un canal idéal de Nyquist.

## 4
2    Interférence entre symboles (IES) et égalisation
Dans cette partie,  nous allons considérer un canal convolutif qui introduit des IES comme illustré dans la
Figure 2.  Nous allons étudier une méthode simple d’égalisation, qui permet de diminuer ou annuler les effets
des IES à la réception.
## ♢
Canal non-idéal
•CréergenSigavec pour entréeNet sortie un vecteur deNéchantillons du signal signal utilex
n
## ,n=
0,...,N−1. Utilisez la fonction  pour filtrer le signal BPSKa
n
, n= 0,...,N−1par
## G(z) = 0.5 + 0.2z
## −1
afin d’obtenir le signal utilex
n
,n= 0,...,N−1.
•écrire l’expression de la réponse impulsionnelle du filtre global du canalg
n
,∀nà partir de la TZG(z)ci-
dessus. écrire ensuite l’expression dex
n
pourn= 0,1,2,3en supposant quea
n
## = 0,∀n <0.
•Visualiser le signal utilex
n
, n= 0,...,N−1. Commenter.
## ♢
Check-point 3Canal non-idéal : visualisation de la constellation BPSK qui subit des IES,x
n
, n=
## 0,...,N−1.
## ♢
Taux d’erreur binaire du canal non-idéal
•Utiliser les fonctions développées dans la partie 1 afin de tracer le taux d’erreur binaire de la chaîne de
communication  de  la  Figure  2a  en  fonction  de
h
## E
b
## N
## 0
i
dB
= 0,...,12.   Quel  est  l’effet  des  IES  et  du  canal
non-idéalG(z)? Commenter.
## ♢
## Égalisation
•Une méthode simple d’égalisation, appelée forçage à zéro (zero forcing), consiste à inverser le filtreG(z)
à la réception.  Créer une fonctionegaliZFqui a pour entrée la séquence deNsymboles reçuesr
n
, n=
0,...,N−1et pour sortie une sequencet
n
, n= 0,...,N−1obtenue en filtrant l’entrée parF
## ZF
## (z) =
## G(z)
## −1
## .
•Tracer le taux d’erreur binaire de la chaîne de communication de la Figure 2b en fonction de
h
## E
b
## N
## 0
i
dB
## = 0,...,12. Commenter.
•Quelles sont les inconvénients de cette méthode dans la pratique ?
(a) figure
Sans égalisation.
(b) figure
Avec égalisation.
Figure 2:Chaîne de communication en bande de base d’un signal BPSK à travers un canal non-idéalG(z).

## 5
THEME 2 : Communication complexe équivalente en bande de
base de la 16-QAM
Les trois points à valider pour le Thème 4 sont les suivants.
•Visualisation de la 16-QAM (constellation complexe et code de Gray).
•Détection dans l’espace complexe de la constellation (test et visualisation).
•Comparaison des courbes d’erreur binaire et symbole (pratiques vs. théoriques).
Remarques et astuces
Notation : nous allons utiliser la notation des signaux discrètes du module Communications Numériques
telle quex
n
, n= 0,...,N−1représente len-éme échantillon.
Hint :  Pour tracer le taux d’erreur binaire nous utilisons la méthode de Monte-Carlo :  à savoir la
simulation d’un grand nombreNde transmissions binaires. Parmi lesNbits transmis nous calcu-
lons la fréquence empirique des occurrences d’erreur (comparaison entrebits
n
et
d
bits
n
).  Le taux
d’erreur symbole est calculé d’une manière similaire en comparant les symboles 16-QAMa
n
avec
leur estimationsba
n
## .
Python : Vous pouvez consulter les fonctionsint()pour convertir un binaire en décimal,bin()
pour convertir un décimal en binaire,chr()pour obtenir un caractère à partir d’un code ASCII,
np.where(), en complément des fonctions utilisées dans les autres Thèmes.
1    Constellation 16-QAM
L’objectif est de visualiser la constellation et le code de Gray pour la 16-QAM d’une manière similaire à la
constellation QPSK dans la Figure 3.
♢Constellation complexe et code de Gray
•Écrire une fonctionconst16QAMqui retourne une matrice complexe,mComplexde taille4×4, qui contient
toutes les valeurs possibles des symbolesa
n
## =a
## I
n
## +ja
## Q
n
aveca
## I
n
## ,a
## Q
n
## ∈{±1,±3}.
•Écrire une fonctionGray16QAMqui génèremGrayla matrice de taille4×4qui contient les codes de Gray
(stockés en decimal) correspondants.
Exemple QPSK (M= 4)
Les deux matrices de taille2×2de la QPSK (i.e., 4-QAM) illustrée dans la Figure 3 sont:
mComplex =
## 
## −1 +j1 +j
## −1−j1−j
## 
etmGray =
## 
## 1  3
## 0  2
## 
,en binaire
## 
## ′
## 01
## ′ ′
## 11
## ′
## ′
## 00
## ′ ′
## 10
## ′
## 
## ,

## 6
oùmComplexest la matrice des symboles complexesa
k
etmGrayest la matrice des codes de
Gray en decimal.Attention :le mapping de Gray n’est pas unique !
♢Visualisation de la 16-QAM
•Dans le programme principal, générer les deux matrices pour la 16-QAM, initialiserM= 16et visualiser
les points de la constellation ainsi que les étiquettes binaires de Gray en utilisant le code mis à votre disposition
sur le notebook.
## ♢
Check-point 1Visualisation de la 16-QAM (constellation complexe et code de Gray).
2    Transmission complexe équivalente en bande de base de la 16-QAM
L’objectif ici est d’écrire une fonction qui simule la chaîne de communication de la 16-QAM illustré dans la
Figure 4. Pour ceci, chaque bloc sera écrit dans une fonction à part, comme détaillé par la suite.
## ♢
## Émetteur
•Écrire une fonctiongenBinqui génèrebits
n
, n= 0,...,N−1, une sequence deNvaleurs binaires dans
{0,1}uniformément distribués, en utilisant par example la fonctionnp.random.randint.
•Écrire une fonctionmappingGrayqui code la séquence binaire à transmettre,bits
n
, dans une séquence
desN/4symbolesa
n
de la 16-AQM en utilisant les deux matricesmComplexetmGraydéterminées dans la
Figure 3: Visualisation de la QPSK (constellation complexe et code de Gray).

## 7
partie 1. Expliquez pour quoi la sequence des symbolesa
n
a une taille égale àN/4.
Exemple QPSK (M= 4)
Pour une QPSK, supposons que la séquence binaire à transmettre (bits
n
, n= 0,...,N) est :
## 0,1,1,0,0,1,0,0,1,1,1,1, ...
•traiter les bits en groupes deux par deux (la taille du groupe estlog
## 2
MoùMest la taille de la
constellation)
## 0,1|1,0|0,1|0,0|1,1|1,1|...
•les transformer en decimal
## 1,2,1,0,3,3, ...
•utiliser la matricemGrayde l’Exemple 1 pour identifier la position(lin,col)de chaque code
## (1,1); (2,2); (1,1); (2,1); (1,2); (1,2);...
•ensuite liremComplex(lin,col)(Exemple 1) pour identifier la séquence des symboles QPSK
a
n
, n= 0,...,Ncorrespondante :
## −1 +j,1−j,−1 +j,−1−j,1 +j,1 +j, ...
## Remarques
Contrairement à la BPSK (Thème 2) pour laquelle le mapping de Gray est trivial :0→ −1et
1→1; quandM >2le bloc de génération des bits doit être explicitement inclus dans la chaîne
de communication.  L’information binaire à transmettre est traitée par paquets de taillelog
## 2
## (M),
qui sont codés dans des symboles complexes de laM-QAM.
♢Canal complexe AWGN
•Écrire une fonctioncanalAWGNqui a pour entrée la sequence complexe desN/4symbolesa
n
et la variance
du bruitσ
## 2
b
et pour sortie la sequence deN/4valeurs complexesr
n
à l’entrée du récepteur.  Le bruit additif
b
n
est une variable Gaussienne complexe avec la partie réelle et la partie imaginaire indépendantes telles que
b
## I
k
## ,b
## Q
k
## ∼N
##  
## 0,σ
## 2
b
## 
. Par simplicité nous choisissonsg(0) = 1.
•Dans le programme principal, tester toutes ces fonctions en visualisant les symboles reçusr
n
sur la même
figure que les symboles de la 16-QAM pourN= 512etσ
## 2
b
## = 0.5.
## ♢
## Récepteur
•Le bloc de décision prend en entrée la séquence deN/4valeurs complexesr
n
et retourne la sequence deN/4
symboles estimésba
n
de la constellation 16-QAM. Vous pouvez utiliser une méthode par seuil de comparaison
(similaire à la BPSK) dans l’espace 2D complexe. Par contre, cette méthode est fastidieuse et le code résultant
est complexe. Comme alternative vous pouvez aussi chercher, pour chaque observationr
n
, quel est le symbole
complexe le plus proche de la 16-QAM. Tester votre méthode en utilisant la visualisation d’un seul symbole
reçu ainsi que le symbole estimé correspondant.

## 8
•écrire une fonctiondemapGrayqui permet d’effectuer l’operation inverse à la fonctionmappingGray.
Cette fonction va exploiter les deux matricesmComplexetmGrayafin de reconstituer la sequence binaire
d
bits
n
de tailleNà partir desN/4symboles estimésba
n
## .
## ♢
Check-point 2Détection dans l’espace complexe de la constellation (test et visualisation).
♢Chaîne de transmission globale
•Écrire une fonction globalechaine16QAMqui simule la chaîne de transmission de la Figure 4.   Cette
fonction a pour entrée deux valeursN,σ
## 2
b
etg(0); en sortie elle a quatre vecteurs :  deux vecteursbits
n
et
d
bits
n
de tailleNet deux vecteursa
n
etba
n
de tailleN/4. Testez cette fonction.
3    Courbes d’erreur de détection
♢Taux d’erreur binaire et symbole
•Pour une M-QAM : chercher dans les diapos du cours le lien entre leRSB =
g(0)
σ
## 2
b
et le SNR normalisé,
## E
b
## N
## 0
## .
•Pour chaque valeur de
h
## E
b
## N
## 0
i
dB
= 0,...,12[dB !] calculer leσ
## 2
b
pourg(0) = 1, ainsi que le taux d’erreur
symbole et binaire correspondants de votre simulateurchaine16QAMde la partie 2.  Pour le taux d’erreur
symbole, vous devez compter le nombre de symboles différents entre la sequence transmisea
n
et la séquence
estiméeba
n
.  Pour le taux d’erreur binaire, vous devez compter le nombre des bits différents entre la sequence
transmisebits
n
et la séquence estimée
d
bits
n
## .
♢Probabilité d’erreur binaire et symbole (théoriques)
•Écrire la formule de la probabilité d’erreur binaireP
b(min)
(e)paramétrée parM, la taille de la constellation.
Tracer la courbe de la probabilité d’erreur binaire pourM= 16.
•Écrire la relation entre la probabilité d’erreur symbole etP
b(min)
(e)ci-dessus pour un codage de Gray et en
supposant un bruit suffisamment petit. Tracer la courbe de la probabilité d’erreur symbole pourM= 16.
♢Analyse et discussions
Figure 4: Chaîne de communication de la 16-QAM.

## 9
•Comparer les courbes estimées avec le simulateur et les courbes théoriques (pour les erreurs binaires et
symboles). Commenter.
•Comparer la communication en bande de base de la BPSK et la communication en bande transposée de la
16-QAM en terme du débit binaire, de la probabilité d’erreur binaire et de l’efficacité spectrale. Commenter.
•Si le temps imparti permet, tracer aussi les courbes d’erreur de la QPSK (en adaptant le simulateur au cas
M= 4) et faire une comparaison complète: BPSK vs. QPSK vs. 16-QAM.
## ♢
Check-point 3Comparaison des courbes d’erreur binaire et symbole (pratiques vs. théoriques).