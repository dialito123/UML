# Partie 4 : Restitution — Décisions de modélisation

## Décision ayant fait l'objet de discussions

Au cours de la conception du diagramme de cas d'utilisation, l'équipe a hésité sur la manière de représenter l'**Agent de voyage** par rapport au **Client**[cite: 1] :

* **Option A : Deux acteurs indépendants**
  L'Agent de voyage et le Client sont modélisés comme deux acteurs distincts, chacun relié directement aux cas d'utilisation « Consulter les disponibilités », « Réserver une chambre » et « Annuler une réservation »[cite: 1].
* **Option B : Relation d'héritage / Généralisation**
  L'Agent de voyage est une spécialisation du Client (`Agent de voyage` $\rightarrow$ `Client`), héritant de toutes ses fonctionnalités[cite: 1].

---

## Choix retenu et justification

Nous avons retenu l'**Option B (la généralisation)**[cite: 1].

### Raisons de ce choix :
1. **Éviter la redondance** : L'Agent de voyage effectue exactement les mêmes opérations métier principales sur le système que le Client (consulter, réserver, annuler)[cite: 1]. La généralisation évite de doubler toutes les flèches vers les cas d'utilisation, ce qui simplifie la lisibilité du diagramme.
2. **Respect de la réalité métier** : L'Agent de voyage est un cas particulier de Client (un partenaire professionnel agissant pour le compte d'un tiers)[cite: 1]. Il possède la même valeur rendue globale mais avec des prérogatives d'accès ou d'imputation adaptées[cite: 1].