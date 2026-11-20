# Projet 6 : Assistant RAG sur les documents d'une organisation

## Objectif
Conception, évaluation et sécurisation d'un système **Retrieval-Augmented Generation (RAG)** dédié à l'interrogation des textes statutaires et règlements intérieurs de trois associations togolaises (Togo AgTech Hub, FRESHYX, ISOC-Togo).

## Architecture du système
- **Extraction & Prétraitement** : `pypdf` avec nettoyage des césures et découpage par fenêtres glissantes (`chunk_size=350`, `overlap=70`).
- **Recherche (Retrieval)** :
  - *Configuration (b)* : Recherche sémantique dense via `paraphrase-multilingual-MiniLM-L12-v2`.
  - *Configuration (c)* : Recherche hybride combinant Dense + Lexical (`BM25Okapi`) via *Reciprocal Rank Fusion* (RRF).
- **Génération & Sécurité** : Modèle ouvert `Qwen2.5-3B-Instruct` contraint par balises XML `<context>`, citations obligatoires et protocole d'abstention stricte.
- **Interface** : Application web interactive développée sous `Gradio`.

## Exécution pas à pas
1. Ouvrir `notebook_rag_projet6.ipynb` dans Google Colab (Activer l'accélération matérielle **GPU T4**).
2. Exécuter les cellules séquentiellement de haut en bas.
3. Téléverser les 4 PDF du dossier `corpus/` dans votre drive .../drive/MyDrive/nlp/corpus.
4. Assurez vous de mettre le fichier evaluation/test test_dataset_40.json  dans votre .../drive/MyDrive
5. Accéder à l'interface Gradio via l'URL publique générée en fin de notebook.