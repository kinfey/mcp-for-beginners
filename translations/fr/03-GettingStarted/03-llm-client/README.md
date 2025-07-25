<!--
CO_OP_TRANSLATOR_METADATA:
{
  "original_hash": "f74887f51a69d3f255cb83d0b517c623",
  "translation_date": "2025-07-13T18:46:46+00:00",
  "source_file": "03-GettingStarted/03-llm-client/README.md",
  "language_code": "fr"
}
-->
Super, pour notre prochaine étape, listons les capacités du serveur.

### -2 Liste des capacités du serveur

Maintenant, nous allons nous connecter au serveur et demander ses capacités :

### -3- Conversion des capacités du serveur en outils LLM

L'étape suivante après avoir listé les capacités du serveur est de les convertir dans un format que le LLM comprend. Une fois cela fait, nous pouvons fournir ces capacités comme outils à notre LLM.

Super, nous ne sommes pas encore prêts à gérer les requêtes des utilisateurs, attaquons cela maintenant.

### -4- Gestion des requêtes utilisateur

Dans cette partie du code, nous allons gérer les requêtes des utilisateurs.

Super, vous l'avez fait !

## Exercice

Prenez le code de l'exercice et développez le serveur avec quelques outils supplémentaires. Ensuite, créez un client avec un LLM, comme dans l'exercice, et testez-le avec différents prompts pour vous assurer que tous les outils de votre serveur sont appelés dynamiquement. Cette manière de construire un client garantit une excellente expérience utilisateur, car ils peuvent utiliser des prompts au lieu de commandes client exactes, sans se soucier de l'appel à un serveur MCP.

## Solution

[Solution](/03-GettingStarted/03-llm-client/solution/README.md)

## Points clés à retenir

- Ajouter un LLM à votre client offre une meilleure façon pour les utilisateurs d'interagir avec les serveurs MCP.
- Vous devez convertir la réponse du serveur MCP en quelque chose que le LLM peut comprendre.

## Exemples

- [Calculatrice Java](../samples/java/calculator/README.md)
- [Calculatrice .Net](../../../../03-GettingStarted/samples/csharp)
- [Calculatrice JavaScript](../samples/javascript/README.md)
- [Calculatrice TypeScript](../samples/typescript/README.md)
- [Calculatrice Python](../../../../03-GettingStarted/samples/python)

## Ressources supplémentaires

## Prochaines étapes

- Suivant : [Consommer un serveur avec Visual Studio Code](../04-vscode/README.md)

**Avertissement** :  
Ce document a été traduit à l’aide du service de traduction automatique [Co-op Translator](https://github.com/Azure/co-op-translator). Bien que nous nous efforcions d’assurer l’exactitude, veuillez noter que les traductions automatiques peuvent contenir des erreurs ou des inexactitudes. Le document original dans sa langue d’origine doit être considéré comme la source faisant foi. Pour les informations critiques, une traduction professionnelle réalisée par un humain est recommandée. Nous déclinons toute responsabilité en cas de malentendus ou de mauvaises interprétations résultant de l’utilisation de cette traduction.