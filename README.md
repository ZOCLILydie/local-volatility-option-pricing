# local-volatility-option-pricing
Implémentation du modèle Black-Scholes, extraction de volatilité implicite et résolution numérique d'une PDE à volatilité locale avec analyse de sensibilité des paramètres.

# Local Volatility Option Pricing

## Présentation

Ce projet implémente la valorisation d’options européennes dans le cadre :

- du modèle de Black-Scholes
- d’un modèle à volatilité locale dépendant du temps et du sous-jacent
- d’une résolution numérique de l’équation aux dérivées partielles (PDE)

L’objectif est d’étudier l’impact d’une volatilité locale sur les prix d’options et sur la volatilité implicite.

---

## 1. Modèle de Black-Scholes

On commence par implémenter :

- Pricing d’un Call européen
- Pricing d’un Put européen
- Vérification de la parité Call-Put
- Extraction de la volatilité implicite

Formule du Call européen :

C = S₀ Φ(d₁) − K e^{-rT} Φ(d₂)

avec :

d₁ = [ln(S₀/K) + (r + σ²/2)T] / (σ√T)  
d₂ = d₁ − σ√T

---

## 2. Modèle à Volatilité Locale

On considère la PDE suivante :

∂ₜ C + r x ∂ₓ C + ½ σ²(t,x) x² ∂ₓₓ C − rC = 0

avec une volatilité définie par :

σ(t,x) = (γ e^{-t} + α) √(σ₀² + ρ(x − x₀) + ν(x − x₀)²)

Ce modèle permet d’introduire une dépendance :

- au temps
- au niveau du sous-jacent

Il génère naturellement un smile de volatilité.

---

## 3. Méthodologie Numérique

La PDE est résolue par :

- Discrétisation en temps et en espace
- Schéma d’Euler explicite
- Conditions aux bords adaptées

Pour différents strikes, on :

1. Calcule le prix via la PDE
2. En déduit la volatilité implicite
3. Analyse l’impact des paramètres (γ, α, ρ, ν)

---

## 4. Analyse de Sensibilité

Le projet étudie l’impact des paramètres du modèle local volatility sur :

- La forme du smile
- Le niveau des prix d’options
- La stabilité numérique

---

## Structure du projet

local-volatility-option-pricing/
│
├── notebooks/
│ └── Volatility_Model_Code.ipynb
│
├── report/
│ └── Volatility_Model_Project.pdf
│
├── README.md
├── requirements.txt
└── LICENSE


---

## Outils utilisés

Python :
- numpy
- scipy
- matplotlib
- pandas

---

## Auteur

Lydie ZOCLI  
Master 2 Modélisation Financière - Centrale Méditerranée et Aix-Marseille School of Economics 
