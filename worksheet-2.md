# Pour aller plus loin avec Sonic Pi

Sonic Pi est tellement cool que c'est compliqué de tout voir dans une seule séance! Si vous sentez que vous avez maîtrisé la [première séance](worksheet.md), et vous aimeriez essayer des nouvelles façons pour coder de la musique, suivez les étapes ci-dessous.

## Ajouter des effets

Les nouveaux synthesiseurs sont capables d'ajouter des effets sonores. Sonic Pi le peut aussi: vous pouvez ajouter des effets de studio comme des réverbérations, des échos et des distortions. Vous devez, bien sûr, utiliser du code pour ajouter ces effets!

1. Dans une nouvelle feuille de travail, trouvez un exemple que vous aimez, par exemple `sample :guit_e_fifths`

1. Mettez l'exemple à l'interieur d'un bloc d'effet comme suit:
    
    ```ruby
    with_fx :reverb do
      sample :guit_e_fifths
    end
    ```
    
1. Vous pouvez ajouter des effets par dessus des autres effets comme suit:

    ```ruby
    with_fx :reverb do
      with_fx :distortion do
        sample :guit_e_fifths
      end  
    end
    ```
    
1. Jouez et testez les différents effets et ajoutez-les dans votre musique. Souvenez-vous qu'une liste complète d'effets peut être trouvée dans la section de l'aide de Sonic Pi sous **FX**.

## Modifier des paramètres

De temps en temps, vous aimeriez peut être faire un son durer plus longtemps ou changer son tempo. Cela peut être fait facilement en modifiant les paramètres du code que vous utilisez.

Voyons l'exemple de `play 60`.

1. Cliquez sur **help** pour ouvrir le document d'aide, sélectionnez ensuite **lang** sur la gauche de l'écran, et descendez jusqu'à **play**. Vous allez voir quelques exemples de son usage. Jusqu'ici vous avez utilisé `play` sans ajouter aucun paramètre; utilisons quelques-uns maintenant.
1. Dans une nouvelle feuille de travail, écrivez:

    ```ruby
    play 60, attack: 1, release: 3
    ```
    
1. Cliquez sur le bouton **play** pour écouter comment cette note sonne. Attaquez and relachez l'amplitude de la note au fil du temps.

1. Maintenant changez les valeurs de l'attaque et de la relache pour voir comment ces paramètres affectent la note.

Il y a beaucoup de paramètres qui peuvent aussi changer la façon dont les exemples et les synthés sonnent.Essayez de changer les valeurs de `cutoff:`, `pan:`, `rate:` or `amp:`. 

Pour avoir une liste complète de paramètres pour chaque exemple, cliquez sur l'icône **Help**, et ensuite **Samples**. Sélectionnez un exemple et faitez défiler le texte pour voir une explication complète pour chaque type de paramètre qui peut être utilisé avec un exemple. Vous pouvez faire la même chose pour les synthés!

## Utilisez la fonction rrand

Sonic Pi inclut un certain nombre de fonctions qui peuvent ajouter des éléments encore plus intéressants dans votre musique. Une fonctionne fun c'est le `rrand`, qui va retourner une valeur entre deux chiffres spécifiques. Pour faire un effet cool, utilisez `rrand` pour faire rebondir le cutoff.

1. Dans une nouvelle feuille de travail, écrivez:

    ```ruby
    loop do
      play chord(:a3, :minor).choose, attack: 0, release: 0.3, cutoff: 80
      sleep 0.2
    end
    ```
    
1. Au lieu d'utiliser un chiffre comme `80` à la valuer de cutoff, essayez `rrand(40, 120)` comme suit:

    ```ruby
    loop do
      play chord(:a3, :minor).choose, attack: 0, release: 0.3, cutoff: rrand(40, 120)
      sleep 0.2
    end
    ```
    
1. Ensuite vous pouvez faire des essais en utilisant `rrand` avec d'autres paramètres. Par exemple, ajoutez `pan: rrand(-1, 1)` pour jouer la ligne d'accord et ensuite cliquez sur **play**.    

## Aller encore plus loin?
- Vous pouvez faire vos propres exemples et les importer dans Sonic Pi?
- Vous pouvez créer une composition complète et originale et la partager avec vos amis?
