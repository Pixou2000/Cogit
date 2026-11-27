# Cogit V2.2.0 — version candidate à tester

1. Conserver une copie de la V2.1.14 et exporter les données locales du jeu.
2. Dans Sheets, supprimer uniquement les lignes fictives TEST des cinq onglets. Garder les en-têtes.
3. Remplacer Code.gs par Cogit_serveur_V2.2.0.gs. Enregistrer puis déployer une nouvelle version du déploiement existant. Ne pas relancer initialiserCogit si les en-têtes sont déjà corrects.
4. Décompresser le ZIP et publier son contenu à la racine du dépôt Cogit (même adresse, pour conserver les données locales). Le nouveau statistics.js doit être présent. Actualiser la page, éventuellement deux fois pour le cache PWA.
5. Tester d'abord le refus : aucune nouvelle ligne ne doit apparaître. Activer ensuite le partage dans Fonctions avancées. Vérifier Joueurs, Sessions et l'historique. Jouer une grille, vérifier Parties et Grilles. Tester une campagne, une sauvegarde/reprise, puis une partie hors connexion et le retour en ligne. Vérifier les doublons et les révisions. Les envois sont par lots de 10 toutes les 15 secondes environ lorsque la page est active.
6. Retirer le partage : les nouveaux envois cessent et la file locale est effacée ; les données déjà reçues restent dans Sheets. Une requête déjà partie peut aboutir.

## Limites à vérifier avant diffusion
- Syntaxe JavaScript vérifiée avec Node, mais pas de test réel du nouveau serveur ou de non-régression dans un navigateur. Le ZIP est une version candidate, pas une version validée.
- Les identifiants sont propres à l'installation ; pas de synchronisation. Les données historiques ne contiennent pas toutes les métadonnées et les imports ultérieurs ne sont pas automatiquement réexpédiés. Les anciennes campagnes terminées sont reprises avec les informations disponibles. Les parties interrompues sans abandon explicite peuvent rester en cours. L'origine des grilles non bibliothèque est regroupée en custom. Le total des aides de campagne n'est pas renseigné (aides désactivées en campagne).
- Le serveur public valide les types, les identifiants, les champs et la taille des lots, et verrouille les écritures. Il ne garantit pas l'authenticité des résultats ni une protection complète contre les abus ou l'épuisement des quotas. Ne pas utiliser pour des classements fiables sans protections supplémentaires.
- Avant publication générale, compléter la notice de confidentialité (responsable, contact, durée de conservation, droits et suppression), vérifier les obligations applicables et tester le retrait du consentement. Les identifiants sont pseudonymes.
- En cas de retour à V2.1.14, republier les fichiers originaux, notamment sw.js et index.html. Ne pas effacer le stockage du navigateur.
