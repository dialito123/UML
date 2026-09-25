# Diagramme de séquence : Facturer le départ (Check-out)

Ce diagramme modélise l'agrégation des frais de séjour, la déduction des arrhes et la gestion des alternatives de paiement, comme demandé dans l'énoncé.

```mermaid
sequenceDiagram
    autonumber
    actor Recep as Réceptionniste
    participant Systeme as Système de Gestion Hôtelière
    participant Paiement as Service de paiement

    Recep->>Systeme: Initier le départ (sélectionner n° chambre)
    activate Systeme
    Note over Systeme: Calcule: Chambre + Consos (tel, resto) + Taxe - Arrhes
    Systeme->>Systeme: Agréger les frais et déduire les arrhes
    Systeme-->>Recep: Afficher le solde de la facture détaillée
    deactivate Systeme

    Recep->>Systeme: Lancer l'encaissement du solde
    activate Systeme
    Systeme->>Paiement: Demande de transaction
    activate Paiement
    
    alt Paiement accepté
        Paiement-->>Systeme: Transaction validée
        Systeme->>Systeme: Clôturer facture et marquer chambre "libérée"
        Systeme-->>Recep: Confirmer le départ et la clôture
    else Paiement refusé
        Paiement-->>Systeme: Transaction refusée
        Systeme-->>Recep: Alerte: Demander un autre moyen de paiement
    end
    
    deactivate Paiement
    deactivate Systeme