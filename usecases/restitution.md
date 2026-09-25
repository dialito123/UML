# Partie 4 : Restitution — Décisions de modélisation

## Décision ayant fait l'objet de discussions

Au cours de la conception du diagramme de cas d'utilisation, l'équipe a hésité sur la manière de représenter l'**Agent de voyage** par rapport au **Client** :

* **Option A : Deux acteurs indépendants**
  L'Agent de voyage et le Client sont modélisés comme deux acteurs distincts, chacun relié directement aux cas d'utilisation « Consulter les disponibilités », « Réserver une chambre » et « Annuler une réservation ».
* **Option B : Relation d'héritage / Généralisation**
  L'Agent de voyage est une spécialisation du Client (`Agent de voyage` $\rightarrow$ `Client`), héritant de toutes ses fonctionnalités.

---

## Choix retenu et justification

Nous avons retenu l'**Option B (la généralisation)**.

### Raisons de ce choix :
1. **Éviter la redondance** : L'Agent de voyage effectue exactement les mêmes opérations métier principales sur le système que le Client (consulter, réserver, annuler). La généralisation évite de doubler toutes les flèches vers les cas d'utilisation, ce qui simplifie la lisibilité du diagramme.
2. **Respect de la réalité métier** : L'Agent de voyage est un cas particulier de Client (un partenaire professionnel agissant pour le compte d'un tiers). Il possède la même valeur rendue globale mais avec des prérogatives d'accès ou d'imputation adaptées.