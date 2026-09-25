# Diagramme de séquence : Réserver une chambre

Ce diagramme illustre les interactions chronologiques entre le Client, le Système et le Service de paiement externe lors d'une réservation.

```mermaid
sequenceDiagram
    autonumber
    actor Client
    participant Systeme as Système de Gestion Hôtelière
    participant Paiement as Service de paiement

    Client->>Systeme: Consulter disponibilités (dates, capacité)
    activate Systeme
    Systeme-->>Client: Afficher les chambres disponibles
    deactivate Systeme

    Client->>Systeme: Sélectionner chambre et saisir infos
    activate Systeme
    Systeme->>Systeme: Vérifier disponibilité et calculer prix

    alt Réservation à plus de 8 jours de l'arrivée
        Systeme-->>Client: Exiger les arrhes (10% minimum)
        Client->>Systeme: Saisir les coordonnées bancaires
        Systeme->>Paiement: Demander la validation du paiement
        activate Paiement
        Paiement-->>Systeme: Paiement validé
        deactivate Paiement
        Systeme->>Systeme: Enregistrer la réservation (Confirmée)
    else Réservation à J-8 ou moins
        Systeme->>Systeme: Enregistrer la réservation confirmée (sans arrhes exigées)
    end
    
    Systeme-->>Client: Envoyer la confirmation de réservation
    deactivate Systeme