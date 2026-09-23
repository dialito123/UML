# Fiche de Cas d'Utilisation : Facturer le départ (Check-out)

- **Acteur principal** : Réceptionniste
- **Précondition** : Le client est présent à l'accueil pour son départ, son séjour est enregistré et les éventuelles consommations ont été saisies.

## Scénario nominal

1. Le réceptionniste sélectionne le séjour / la chambre du client dans le système.
2. Le système récupère le tarif de la chambre (selon la catégorie et le nombre d'occupants), le relevé du compteur téléphonique, et l'ensemble des consommations enregistrées (restaurant, bar, prestations).
3. Le système calcule la taxe de séjour et déduit les arrhes déjà versées lors de la réservation.
4. Le système génère le détail de la facture et affiche le solde restant à payer.
5. Le réceptionniste présente la facture au client qui effectue le règlement via le Service de paiement.
6. Le Service de paiement confirme la validation du règlement.
7. Le système enregistre le paiement, clôture la facture et libère la chambre dans le système.

## Scénarios alternatifs

- **2a. Erreur ou omission dans le relevé des consommations**
  - 2a1. Le réceptionniste ajoute ou rectifie manuellement une consommation (ex. mini-bar ou téléphone) avant la clôture.
  - 2a2. Le système récalcule le montant total de la facture et reprend à l'étape 4.

- **6a. Refus de paiement ou échec du paiement**
  - 6a1. Le Service de paiement signale un refus de la transaction.
  - 6a2. Le réceptionniste propose un autre moyen de paiement (espèces, autre carte, etc...).
  - 6a3. Une fois le nouveau moyen de paiement validé, le scénario reprend à l'étape 6.

## Postcondition

- Le solde du séjour est intégralement réglé et la facture est clôturée.
- La chambre est marquée comme libérée et disponible pour le nettoyage / les arrivées suivantes.