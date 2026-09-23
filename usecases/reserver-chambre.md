# Fiche de Cas d'Utilisation : Réserver une chambre

- **Acteur principal** : Client (ou Agent de voyage)
- **Précondition** : Le client a consulté les disponibilités pour une période donnée et la capacité souhaitée est disponible.

## Scénario nominal

1. Le client sélectionne l'hôtel, la catégorie de chambre, les dates du séjour et le nombre d'occupants.
2. Le système vérifie la disponibilité et confirme l'absence de réservation pour la période et la capacité choisies.
3. Le système calcule le montant total du séjour et détermine si des arrhes (10 % minimum) sont exigées (si la réservation a lieu à plus de 8 jours de l'arrivée).
4. Le client saisit ses informations personnelles et valide sa demande de réservation.
5. Le système redirige le client vers le Service de paiement externe pour le versement des arrhes.
6. Le Service de paiement confirme le succès de la transaction au système.
7. Le système enregistre la réservation à l'état « Confirmée », génère une confirmation et l'envoie au client.

## Scénarios alternatifs

- **2a. Pas de disponibilité pour la période / capacité demandée**
  - 2a1. Le système informe le client qu'aucune chambre ne correspond aux critères.
  - 2a2. Le système propose d'autres dates ou d'autres catégories de chambres.
  - 2a3. Le client modifie ses critères (retour à l'étape 1) ou abandonne la réservation.

- **3a. Réservation effectuée à 8 jours ou moins de l'arrivée (J-8 ou moins)**
  - 3a1. Le système n'exige pas de versement immédiat d'arrhes.
  - 3a2. Le système enregistre directement la réservation et passe à l'étape 7.

- **6a. Échec ou annulation du paiement des arrhes**
  - 6a1. Le Service de paiement informe le système de l'échec ou de l'abandon de la transaction.
  - 6a2. Si la réservation est faite à plus de 8 jours, le système enregistre la réservation à l'état « En attente d'arrhes » (annulable automatiquement à J-8 par l'horloge système).
  - 6a3. Le système invite le client à réessayer le paiement.

## Postcondition

- La chambre est réservée pour la période et le nombre d'occupants (elle ne peut plus être réservée par un autre client pour ces mêmes nuits).
- Si les arrhes ont été versées à plus de 8 jours ou si la réservation a lieu à J-8 ou moins, la réservation est confirmée.