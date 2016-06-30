# Débutez avec Sonic Pi 2

Est-ce que vous avez souhaitez faire de la musique funky comme Daft Punk ou will.i.am mais vous n'êtes pas sûrs comment tenir un cello, et le laisser jouer tout seul? Avec Sonic Pi vous allez y arriver.

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

## Loop a tune

Now you have mastered the basics of Sonic Pi, let's code a tune!

1. Select **Workspace 2**.

2. Type the following code:

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

3. Now click on the play icon at the top of the screen and it will play the first part of a tune. Can you tell what it is? 

	*Answer: Frère Jacques!*

    This first section plays twice. How could you repeat it? You could type the same section out again, or we could start to introduce loops to your code.

4. At the top of your code, above the first `play 60`, type:

    ```ruby
    2.times do
    ```

5. And at the bottom of your code, below `sleep 0.5`, type:

    ```ruby
    end
    ```

6. Click on the play icon at the top of the screen. What happens?

    Let's play this part in Sonic Pi.

    In the example below, you can see that some lines of code are indented. This makes it easier to read your code, and check for any bugs if it does not work when you press the play button. You can press the space bar twice to indent a line of code.

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
### Loop forever?

Looping notes for a set number of times is certainly useful, but what if you want to loop your tune forever? 

Instead of using `2.times do` and `end` you can use `loop do` and `end`, like this:

```ruby
loop do
  play 60
  sleep 0.5
end
```      
    
## MIDI notes and music notes

The values that you have been typing after the word `play` represent notes; in fact, they are MIDI note numbers. This means we can translate songs played on a piano into Sonic Pi using a table like so:

`C D E C` or `60 62 64 60` in MIDI notes.

**Music Notes to MIDI Note Values**

| C       | D      | E     | F     | G     | A     | B     |
| :-----: |:------:|:-----:|:-----:|:-----:|:-----:|:-----:|
| 60      | 62     | 64    | 65    | 67    | 69    | 71    |

This is quite a long process if you know the notes of the song you are trying to play. With Sonic Pi you are able to use standard sheet music notation too.

1. In a new workspace tab type:

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
1. Press **play** to hear your tune. Does it sound the same as when you used MIDI notes?	

## Change the sounds

It's time to make your tune sound more interesting! We can do this by changing the synthesizer sounds it is using. The default Sonic Pi synth is called `beep`.

To use a different synth, you need to add the code `use_synth :name of synth` above the sequence of code you want to use it in.

In this example, `fm` is the name of the synth:

```ruby
use_synth :fm
2.times do
  play 60
  sleep 0.5
  play 67
  sleep 0.5
end
```

### Synths to try

There are lots of cool-sounding synths included with Sonic Pi. To find the names of them, click on the **help** icon at the top of the screen so that the help documents window appears. Then select **Synths** from the tabs along the left hand side of the help window. Click on any of the synth names to get more information on how to use it.

## Use samples

Not only can you create music in Sonic Pi using single notes, you can also create music with samples. Samples are pre-recorded sounds or tunes that you can bring into your music. This is a really simple way to make your music sound amazing!

To use a sample, you need to add the code `sample :name of sample` in the sequence of your music program where you want it to play.

In this example, `loop_amen` is the name of the sample:

```ruby
2.times do
  sample :loop_amen
  sleep 1.753
end
```

### Samples to try

There are lots of samples included with Sonic Pi. To find the names of them, click on **help** followed by **samples** on the left hand side of the help window. Click on any of the sample names to get more information on how to use it. 

## Playing two tunes at the same time

Music often has a repeating backing track, with a separate melody played over the top. So far in Sonic Pi you have played one tune. Let's try playing two tunes at the same time!


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
