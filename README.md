C'est quoi ASN.1 ?

ASN.1 (Abstract Syntax Notation One) est un langage standard qui sert à décrire la structure des données.

Imaginez que deux ordinateurs veulent communiquer. Ils doivent savoir :

quelles données sont envoyées ;
dans quel ordre elles sont placées ;
quel est leur type (texte, nombre, date, etc.).

ASN.1 sert de plan de construction pour organiser ces données.

Exemple
-------

Person ::= SEQUENCE {
    nom     UTF8String,
    prenom  UTF8String,
    age     INTEGER
}

Cela signifie :

nom = texte
prenom = texte
age = nombre entier

ASN.1 ne contient pas les données elles-mêmes, il décrit seulement leur structure.

Analogie simple

Imaginez un formulaire :

Champ	Type
Nom	Texte
Prénom	Texte
Âge	Nombre

ASN.1 est comme le modèle vide du formulaire.

Les vraies données seraient :

Nom : Dupont
Prénom : Jean
Âge : 30
Pourquoi ASN.1 est utilisé ?

Parce que différents systèmes doivent communiquer sans erreur.

Par exemple :

banques
certificats SSL/TLS
réseaux 4G/5G
cartes SIM
passeports électroniques
systèmes militaires
satellites

Tous doivent comprendre exactement les mêmes données.

Que signifie SEQUENCE ?

SEQUENCE est l'équivalent d'une structure ou d'un objet.

Person ::= SEQUENCE {
    nom UTF8String,
    age INTEGER
}

On peut l'imaginer ainsi :

Person
│
├── nom = "Dupont"
└── age = 30
Les types ASN.1 les plus utilisés
Type ASN.1	Signification
INTEGER	Nombre entier
BOOLEAN	Vrai/Faux
UTF8String	Texte
OCTET STRING	Données binaires
BIT STRING	Suite de bits
SEQUENCE	Groupe d'éléments
SET	Ensemble d'éléments
OBJECT IDENTIFIER	Identifiant unique

Exemple :

age INTEGER
25
Comment les données sont envoyées ?

Un ordinateur ne comprend que des octets.

ASN.1 utilise donc des règles d'encodage :

BER
CER
DER
PER
XER
JER

Le plus connu est DER.

Exemple d'encodage DER

Nombre :

INTEGER 100

devient :

02 01 64

Décomposition :

02 = type INTEGER
01 = longueur
64 = valeur 100

C'est ce que la machine échange réellement.

ASN.1 et les certificats HTTPS

Lorsque vous ouvrez :

https://google.com

Votre navigateur reçoit un certificat numérique.

Ce certificat est écrit avec ASN.1.

Structure simplifiée :

Certificat
│
├── Version
├── Numéro de série
├── Émetteur
├── Propriétaire
├── Date début
├── Date fin
└── Clé publique

Tous ces éléments sont décrits avec ASN.1.

ASN.1 en cybersécurité

Vous rencontrerez ASN.1 dans :

Certificats X.509
SSL/TLS
PKI
Cartes à puce
SNMP
VPN
Télécommunications 4G/5G

C'est pourquoi les analystes cybersécurité apprennent souvent ASN.1.

Avec quel langage travailler ?

ASN.1 n'est pas un langage de programmation.

On l'utilise avec :

Python
C
C++
Java
C#
Go

Le plus simple pour débuter est Python.

Exemple :

from pyasn1.type import univ
from pyasn1.codec.der.encoder import encode

nombre = univ.Integer(100)

data = encode(nombre)

print(data.hex())

Résultat :

020164
Outils recommandés
Visual Studio Code pour écrire le code.
Python + pyasn1 pour expérimenter.
OpenSSL pour analyser les certificats.
ASN.1 Playground pour apprendre en ligne.
Résumé final

ASN.1 est un langage de description de données. Il permet à différents systèmes informatiques de comprendre exactement la même structure d'information. Il est utilisé dans les certificats HTTPS, les réseaux, les télécommunications, les cartes à puce et la cybersécurité. ASN.1 décrit les données, puis celles-ci sont converties en octets grâce à des encodages comme DER ou BER pour être transmises entre machines.
