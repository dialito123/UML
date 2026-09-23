# Partie 1 : Les acteurs du système

## Liste des acteurs

| Nom du rôle | Nature | Attentes vis-à-vis du système |
| :--- | :--- | :--- |
| **Client** | Humain | Consulter les disponibilités, effectuer une réservation en payant des arrhes et pouvoir annuler sa réservation. |
| **Agent de voyage** | Humain | Consulter les disponibilités et effectuer des réservations de chambres pour le compte de ses clients. |
| **Réceptionniste** | Humain | Enregistrer l'arrivée (clés, compteur), saisir les consommations (bar, restaurant, téléphone), éditer la liste des arrivées du matin et facturer au départ. |
| **Gérant** | Humain | Administrer les hôtels, catégories, chambres et tarifs, et consulter le taux d'occupation sur une période. |
| **Service de paiement** | Système externe | Valider et encaisser les paiements par carte, espèce ou autre service. |
| **Horloge système** | Temps | Déclencher l'annulation automatique à J-8 des réservations dont les arrhes n'ont pas été versées. |

## Statut de l'agent de voyage

L'agent de voyage est un **acteur distinct** parce qu'il agit pour le compte de tiers en tant que partenaire professionnel, ce qui le différentie du client.

# Partie 2 : Le diagramme de cas d'utilisation

```mermaid
flowchart LR
    %% Définition des acteurs (formes stickman)
    Client([ Client ])
    Agent([ Agent de voyage ])
    Recep([ Réceptionniste ])
    Gerant([ Gérant ])
    Paiement[(" Service de paiement ")]
    Temps[(" Horloge système ")]

    %% Frontière du système
    subgraph System ["Système de Gestion Hôtelière"]
        direction TB
        UC_Consulter(("Consulter les\ndisponibilités"))
        UC_Reserver(("Réserver une\nchambre"))
        UC_PayerArrhes(("Payer les\narrhes"))
        UC_AnnulerClient(("Annuler une\nréservation"))
        UC_AnnulerAuto(("Annuler automatiquement\nà J-8"))
        UC_CheckIn(("Enregistrer l'arrivée\n(Check-in)"))
        UC_SaisirConso(("Enregistrer les\nconsommations"))
        UC_Facturer(("Facturer au départ\n(Check-out)"))
        UC_EditerArrivees(("Éditer les arrivées\ndu matin"))
        UC_ConsultTaux(("Consulter le taux\nd'occupation"))
        UC_Admin(("Administrer hôtels,\ncatégories & tarifs"))
    end

    %% Généralisation d'acteur
    Agent --> Client

    %% Interactions Client
    Client --- UC_Consulter
    Client --- UC_Reserver
    Client --- UC_AnnulerClient

    %% Relations include et extend
    UC_Reserver -.->|include| UC_PayerArrhes
    UC_AnnulerClient -.->|extend| UC_PayerArrhes

    %% Interactions Réceptionniste
    Recep --- UC_CheckIn
    Recep --- UC_SaisirConso
    Recep --- UC_Facturer
    Recep --- UC_EditerArrivees

    %% Interactions Gérant
    Gerant --- UC_ConsultTaux
    Gerant --- UC_Admin

    %% Acteurs non humains
    UC_PayerArrhes --- Paiement
    UC_Facturer --- Paiement
    Temps --- UC_AnnulerAuto