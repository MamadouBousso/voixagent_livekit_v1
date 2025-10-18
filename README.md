# VoiceAgent LiveKit - Démo Sénégal

Application d'agent vocal en temps réel utilisant LiveKit, OpenAI et ElevenLabs.

## 🏗️ Architecture

Le projet est composé de 3 parties :

1. **Client** (`client/`) : Interface web HTML/JavaScript
2. **Serveur** (`serveur/`) : API FastAPI pour générer les tokens d'authentification
3. **Worker** (`worker/`) : Agent vocal IA qui traite les conversations

## 📋 Prérequis

- Python 3.9 ou supérieur
- Compte LiveKit (gratuit sur livekit.cloud)
- Clé API OpenAI
- Clé API ElevenLabs

## 🚀 Installation

### 1. Configuration LiveKit

Créez un compte gratuit sur [livekit.cloud](https://livekit.cloud) et récupérez :
- L'URL de votre projet (ex: `wss://votre-projet.livekit.cloud`)
- La clé API (API Key)
- Le secret API (API Secret)

### 2. Installation du serveur

```bash
cd serveur

# Créer un environnement virtuel (recommandé)
python -m venv venv
source venv/bin/activate  # Sur macOS/Linux
# ou
venv\\Scripts\\activate  # Sur Windows

# Installer les dépendances
pip install -r requirements.txt

# Configurer les variables d'environnement
cp .env.example .env
# Éditer .env avec vos vraies valeurs
```

### 3. Installation du worker

```bash
cd worker

# Créer un environnement virtuel (recommandé)
python -m venv venv
source venv/bin/activate  # Sur macOS/Linux
# ou
venv\\Scripts\\activate  # Sur Windows

# Installer les dépendances
pip install -r requirements.txt

# Configurer les variables d'environnement
cp .env.example .env
# Éditer .env avec vos vraies valeurs
```

## ▶️ Lancement de l'application

### Terminal 1 : Démarrer le serveur

```bash
cd serveur
source venv/bin/activate  # Activer l'environnement virtuel
uvicorn main:app --reload --port 8000
```

Le serveur sera accessible sur : `http://localhost:8000`

### Terminal 2 : Démarrer le worker

```bash
cd worker
source venv/bin/activate  # Activer l'environnement virtuel
python app.py dev
```

Le worker se connecte à LiveKit et attend les participants.

### Utiliser l'interface web

1. Ouvrez votre navigateur sur : `http://localhost:8000`
2. Entrez un nom de salle (ex: `demo-sn`)
3. Entrez votre identité (ex: `web-client-1`)
4. Cliquez sur "Rejoindre"
5. Autorisez l'accès au microphone
6. Commencez à parler avec l'agent vocal !

## 🔧 Configuration avancée

### Variables d'environnement du serveur

- `LIVEKIT_URL` : URL du serveur LiveKit
- `LIVEKIT_API_KEY` : Clé API LiveKit
- `LIVEKIT_API_SECRET` : Secret API LiveKit

### Variables d'environnement du worker

- `LIVEKIT_URL`, `LIVEKIT_API_KEY`, `LIVEKIT_API_SECRET` : Identifiants LiveKit
- `OPENAI_API_KEY` : Clé API OpenAI (pour Whisper et GPT)
- `ELEVENLABS_API_KEY` : Clé API ElevenLabs (pour la synthèse vocale)
- `AGENT_INSTRUCTIONS` : Instructions système pour l'agent
- `STT_MODEL` : Modèle de reconnaissance vocale
- `LLM_MODEL` : Modèle de langage
- `TTS_MODEL` : Modèle de synthèse vocale
- `TTS_VOICE_ID` : ID de la voix à utiliser

## 🎯 Fonctionnalités

- ✅ Conversation vocale en temps réel
- ✅ Reconnaissance vocale automatique (Whisper)
- ✅ Réponses intelligentes (GPT-4o-mini)
- ✅ Synthèse vocale naturelle (ElevenLabs)
- ✅ Détection d'activité vocale (VAD)
- ✅ Mode push-to-talk optionnel

## 🐛 Dépannage

### Le serveur ne démarre pas
- Vérifiez que le fichier `.env` existe dans `serveur/`
- Vérifiez que toutes les variables sont définies

### Le worker ne se connecte pas
- Vérifiez les identifiants LiveKit dans `worker/.env`
- Assurez-vous que l'URL commence par `wss://`

### Pas de son
- Vérifiez l'autorisation du microphone dans le navigateur
- Vérifiez que le lecteur audio n'est pas muet
- Ouvrez la console du navigateur pour voir les erreurs

### Erreurs d'API
- Vérifiez vos clés API OpenAI et ElevenLabs
- Vérifiez que vous avez des crédits disponibles

## 📚 Documentation

- [LiveKit Documentation](https://docs.livekit.io/)
- [LiveKit Agents SDK](https://docs.livekit.io/agents/)
- [OpenAI API](https://platform.openai.com/docs)
- [ElevenLabs API](https://elevenlabs.io/docs)

## 📝 Licence

Ce projet est un exemple éducatif.

