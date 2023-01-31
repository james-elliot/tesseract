# tesseract

Installer les paquetages `poppler-utils`, `tesseract-ocr` et `tesseract-ocr-fra`

Pour ajouter des mots au dictionnaire de tesseract:
- Aller dans le répertoire `/usr/share/tesseract-ocr/4.00/tessdata/`
- Creer un répertoire `backup`
- Depaqueter les données `fra` en utilisant `combine_tessdata -u fra.traineddata backup/fra.`
- Aller dans le répertoire `backup`, extraire le dictionnaire `dawg2wordlist fra.lstm-unicharset fra.lstm-word-dawg dico.txt`
- Compléter `dico.txt` en y insérant les mots souhaités
- Créer le nouveau fichier `fra.lstm-word-dawg`: ` wordlist2dawg dico.txt fra.lstm-word-dawg fra.lstm-unicharset` qui remplace l'ancien
- Ré-empaqueter l'ensemble avec la commande ` combine_tessdata fra` qui recrée un fichier `fra.traineddata`, puis renommer le fichier en `myfra.traineddata`
- Recopier ce fichier dans le répertoire `/usr/share/tesseract-ocr/4.00/tessdata/`

Il est normalement possible d'utiliser désormais `tesseract -l myfra` pour utiliser le nouveau dictionnaire.
