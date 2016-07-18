# Débutez avec Sonic Pi 2

Avez-vous déjà eu l'envie de faire de la musique funky comme Daft Punk ou will.i.am mais vous n'êtes pas sûrs comment tenir un cello, et le laisser jouer tout seul? Avec Sonic Pi vous allez y arriver.

## Premiers sons avec Sonic Pi

![](images/interface1.png)

Cela est l'interface de Sonic Pi; il a trois fênetres principales. La plus grande est celle où vous écrivez le code et on l'appelle le Tableau de Programme. Il y a aussi un tableau de sortie qui affiche l'information sur le programme qui se joue. Quand vous cliquez sur le bouton **aide** qui se trouve en haut de votre fênetre, le troisième tableau s'affiche ainsi que le bouton de la documentation d'aide. Cela contient de l'information sur les différents codes pour que vous puissiez l'essayer et l'utiliser, ainsi que les différents sons de synthé, samples et beaucoup plus.

1. Lancer Sonic Pi de votre bureau ou de menu d'applications.

2. Selectionnez **Workspace 1** et écrire:

	```ruby
	play 60
	```
	
3. Cliquez sur l'icône **play** qui se trouve en haut de l'écran. Qu'est-ce qui se passe?

4. Qu'est-ce qui se passe quand vous tapez `pley 60` et cliquez sur l'icône play?

	Cela est un exemple d'un bug du code. Dans les activités suivantes, si le tableau de l'erreur s'affiche vous saurez qu'il y a un bug que vous allez devoir réparer. Cela peut vouloir dire que vous avez mal écrit le mot `play`.

5. Maintenant écrivez:

	```ruby
	play 60
	play 67
	play 69
	```
	
6. Cliquez sur l'icône play en haut de votre écran. Qu'est-ce qui se passe?

7. L'ordinateur joue chaque note dans une séquence (une après l'autre), mais cela se fait tellement rapidement que nous avons l'impression que les notes se jouent en même temps.

	Il faut dire à l'ordinateur de faire une pause entre chaque note. Pour ce faire on écrit le suivant après chaque `play`:

	```ruby
	sleep 1
	```
	La valeur entrée après chaque mot `sleep` représent le temps en secondes. La valeur 1 représent une seconde. Qu'est-ce que vous écririez pour une demi seconde?

8. Maintenant écrivez une séquence de play et sleep pour composer une musique cool!

## Faire répéter un morceau

Maintenant que vous avez compris les bases de Sonic Pi, allons coder une chanson!

1. Selectionner **Workspace 2**.

2. Ecrivez le code suivant:

    ```ruby
    play 60
    sleep 0.5
    play 62
    sleep 0.5
    play 64
    sleep 0.5
    play 60
    sleep 0.5
    ```

3. Maintenant cliquez sur l'icône play qui se trouve en haut de l'écran et il va jouer la première partie du morceau. Est-ce que vous savez ce que c'est? 

	*Réponse: Frère Jacques!*

    Cette première partie doit se répéter. Comment on peut faire cela? Vous pourriez écrire cette partie une deuxième fois, ou vous pouvez commencez à utiliser la fonctionne de boucle dans votre code.

4. Au début de votre code, avant le premier `play 60`, écrivez:

    ```ruby
    2.times do
    ```

5. Et à la fin de votre code, après `sleep 0.5`, écrivez:

    ```ruby
    end
    ```

6. Clicquez sur l'icône play en haut de l'écran. Qu'est-ce que se passe?

    Allons jouer cette partie sur Sonic Pi.

    Dans l'exemple ci-après, vous pouvez voir que quelques lignes de code sont découpés. Cela rend plus facile de lire le code, et de vérifier s'il y a des bugs quand si ça ne marche pas quand on clique sur play. Vous pouvez appuyer sur le barre d'espace deux fois pour découper une ligne de code.

    ```ruby
    2.times do
      play 60
      sleep 0.5
      play 62
      sleep 0.5
      play 64
      sleep 0.5
      play 60
      sleep 0.5
    end
    ```
### Répéter indéfiniment?

Répéter des notes pour un certain temps c'est certainement utile, mais comment il faut faire si on veut répéter un morceau indéfiniment? 

Au lieu d'utiliser `2.times do` et `end` vous pouvez utiliser `loop do` et `end`, comme ça:

```ruby
loop do
  play 60
  sleep 0.5
end
```      
    
## Notes MIDI et notes de musique

Les chiffres que vous écriviez après le mot `play` represent des notes; en effet, ce sont des chiffres de notes de MIDI. Cela veut dire que nous pouvons traduire des chansons jouées sur un piano en Sonic Pi en utilisant un tableau comme celui-ci:

`C D E C` ou `60 62 64 60` en notes de MIDI.

**Notes de musique en chiffres de notes de MIDI**

| C       | D      | E     | F     | G     | A     | B     |
| :-----: |:------:|:-----:|:-----:|:-----:|:-----:|:-----:|
| 60      | 62     | 64    | 65    | 67    | 69    | 71    |

Cela est une démarche assez longue si vous connaissez les notes de la chanson que vous essayez de jouer. Avec Sonic Pi vous êtes également capables d'utiliser la notation standard de partition.

1. Dans un nouvel onglet d'espace de travail écrivez:

	```ruby
	play :c4
	sleep 0.5
	play :d4
	sleep 0.5
	play :e4
	sleep 0.5
	play :c4
	sleep 0.5
	```
1. Cliquez sur **play** pour écouter votre morceau. Est-ce que ça son pareil que quand vous avez utilisé des notes de MIDI?	

## Modifierer les sons

C'est le moment pour faire votre morceau plus intéressants! Pour ce faire on peut modifier les sons de synthétiseur utilisés. Le synthè par défaut de Sonic Pi s'appelle `beep`.

Pour utiliser un synth différent, vous aurez besoin d'ajouter le code `use_synth :nom du synthé` avant la séquence de code où vous souhaitez l'utiliser.

Pour cet exemple, `fm` est le nom du synth:

```ruby
use_synth :fm
2.times do
  play 60
  sleep 0.5
  play 67
  sleep 0.5
end
```

### Synthés à tester

Il y a beaucoup de synth qui sonnent bien inclus dans Sonic Pi. Pour trouver leurs noms, cliquez sur l'icône **help** en haut de l'écrant pour que la fênetre d'aide apparaisse. Ensuite selectionnez **Synths** des onglets qui se trouve en gauche de la fenêtre d'aide. Cliquez sur n'importe quel nom de synthé pour avoir plus d'information sur comment l'utiliser.

## Utilisez des exemples

Non seulement vous pouvez créer votre musique sur Sonic Pi en utilisant des notes seules, mais vous pouvez également créer votre musique avec des exemples. Les exemples sont pré enregistrés sons ou morceau que vous pouvez utiliser dans votre musique. Cela est une façon très simple pour que votre musique soit super!

Pour utiliser un exemple, vous aurez besoin d'ajouter le code `sample :nom de l'exemple` dans la séquence de votre programme de musique à l'endroit où vous souhaitez que ça se joue.

Dans cet exemple, `loop_amen` est le nom de l'exemple:

```ruby
2.times do
  sample :loop_amen
  sleep 1.753
end
```

### Exemples à essayer

Il y a beaucoup d'exemples qui sont inclus dans Sonic Pi. Pour trouver leurs noms, cliquez sur **help** et ensuite **samples** en haut de la partie gauche de la fenêtre d'aide. Cliquez sur n'importe quel nom d'exemple pour avoir plus d'information sur comment l'utiliser. 

## Jouer deux morceaux en même temps

La musique a souvent un morceau qui Music often has a repeating backing track, with a separate melody played over the top. So far in Sonic Pi you have played one tune. Let's try playing two tunes at the same time!


1. Click on a new workspace tab.

2. The code we use to play two tunes at the same time needs to be between `in_thread do` and `end`.

3. Underneath `in_thread do`, type your tune. Here I've used a sample for my backing track:

    ```ruby
    in_thread do
      loop do
        sample :loop_amen
        sleep 1.753
      end
    end       
    ```

    This first 'thread' will act as the melody of your music. Underneath, you can type the code for your backing track or baseline.

4. Type:

    ```ruby
    in_thread do
      16.times do
        play 75
        sleep 1.753
        play 74
        sleep 0.25
      end
    end 
    ```
5. Now press **play** and you should hear both threads playing at the same time.     

## Live code!

Sonic Pi has been developed to be a platform for the live coding of music, so that the code can be manipulated, changed and adapted in real time; this means coders can perform their code rather than playing pre-written programs. Why not have a go?

1. In a new workspace tab type:

	```ruby
	define :play_my_synth do
	  use_synth :prophet
  	  play 50, attack: 0.2, release: 1.3
      sleep 0.5
    end
    
    loop do
      play_my_synth
    end
    ```
1. Press **play** to start the program.
1. Whilst the tune is playing, comment out the last three lines by adding a `#` symbol to the start of each line like this:

	```ruby
	# loop do
	#   play_my_synth
	# end
	```
1. Next change some of code in the function, and press **play** again. Now you are really rocking! 

## Explore more features of Sonic Pi

Sonic Pi offers so much more functionality to both coders and musicians alike than has been mentioned here. If you want to try some more features then move onto [the next tutorial here](worksheet-2.md)
