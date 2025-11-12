# Base ERC20 Faucet — Solidity + Hardhat + Frontend

Projet prêt à publier sur GitHub pour montrer de l'activité **Web3/crypto** (idéal pour Talent Protocol).
- Réseau cible : **Base Sepolia** (testnet)
- Contrats : `TestToken.sol` (ERC20 minimal) + `Faucet.sol` (claim avec cooldown)
- Frontend simple (HTML + JS + ethers.js) pour faire un **claim** via MetaMask

> Pas besoin de déployer pour Talent Protocol — **les commits GitHub suffisent**.  
> Si vous voulez tester la dApp : déployez sur **Base Sepolia** et collez les adresses dans `frontend/app.js`.

## Structure
```
base-erc20-faucet/
├── contracts/
│   ├── TestToken.sol
│   └── Faucet.sol
├── scripts/
│   ├── deploy.js
│   └── fund_faucet.js
├── hardhat.config.js
├── package.json
└── frontend/
    ├── index.html
    └── app.js
```

## Déploiement (optionnel)
```bash
npm i
npx hardhat compile

# Variables d'env requises pour déployer (Base Sepolia)
# export BASE_SEPOLIA_RPC="https://sepolia.base.org"
# export PRIVATE_KEY="0x..."
npx hardhat run scripts/deploy.js --network base_sepolia
# (optionnel) Approvisionner le faucet si besoin :
TOKEN_ADDRESS=0x... FAUCET_ADDRESS=0x... npx hardhat run scripts/fund_faucet.js --network base_sepolia
```

## Utilisation du frontend (après déploiement)
- Ouvrez `frontend/app.js` et remplacez :
  - `const TOKEN_ADDRESS = "0xYourToken";`
  - `const FAUCET_ADDRESS = "0xYourFaucet";`
- Ouvrez `frontend/index.html` dans votre navigateur (MetaMask installé, réseau **Base Sepolia**).

## Sécurité (testnet uniquement)
Le faucet a un **cooldown** par adresse; code minimaliste pour démo. Ne pas utiliser tel quel en production.
