# Music Realm Creator

## Description
Hello! Welcome to my Music Realm Creator. Your very own way to organize all of your music-related things!

From adding your own artist, songs and adding them to your Favorites, your control to your music, just got better!

## Visuals

Project Introduction - YouTube

https://youtu.be/PxmwFVl4YiE

## Instructions

Run `pipenv install` to create your virtual environment and `pipenv shell` to enter the virtual environment.

Type in `python lib/cli.py` to start the main menu.

Take a look at the directory structure:

```console
.
├── CONTRIBUTING.md
├── LICENSE
├── LICENSE.md
├── Pipfile
├── Pipfile.lock
├── README.md
├── lib
│   ├── __init__.py
│   ├── __pycache__
│   │   ├── __init__.cpython-38.pyc
│   │   ├── helpers.cpython-38.pyc
│   │   └── util.cpython-38.pyc
│   ├── cli.py
│   ├── debug.py
│   ├── helpers.py
│   ├── models
│   │   ├── __init__.py
│   │   ├── __pycache__
│   │   │   ├── __init__.cpython-38.pyc
│   │   │   ├── artist.cpython-38.pyc
│   │   │   ├── favorites.cpython-38.pyc
│   │   │   └── song.cpython-38.pyc
│   │   ├── artist.py
│   │   ├── favorites.py
│   │   └── song.py
│   └── util.py
├── music_libr.db
└── tables.sql
```
---
## Usage

***Music Realm Creat*** is a fun and interactive program that:

+ Allows the user to add all of their known songs
+ Allows the user to add all of their known artists
+ Allows the user to customize these submission by removing, adding and assigning their songs to the song's corresponding artist
+ Gives a user the ability to add their most loved songs to their 'Favorites'
+ Helps the user keep track and organize by being able to list their songs/artists/favorited songs

Let's go through it!

---
## `cli.py`

Here we have the command line interface for our Realm Creator, whic ultimately comes from our file, `lib/cli.py`!

Once we run `python lib/cli.py`, we are given a menu, with 10 options to choose from:

```
----------Please select an option----------
1. Add an Artist ➕🧑‍🎤
2. List all Artists 📄
3. Add a Song ➕🎶
4. Remove a Song ➖🎶
5. List all Songs 📄
6. List an artist's assigned songs🕺🎶
7. Add song to your Favorites ➕🎼
8. Remove Favorited song ➖🎼
9. List all Favorited songs 📄
Enter 0 to Exit 🚀
```
These options and actions derive their logic and functionality from our `lib/helpers.py file`. We will visit them now.

## helpers.py

```1. Add an Artist ➕🧑‍🎤```

Option 1 allows the user to add an artist of their choice. Once the option is chosen, the user will be prompted to enter the artist's name for submission, which will then create the desired artist!:
```
> 1
---------🌟Adding artist🌟---------
Artist Name (Or enter 0 to go back): Michael Jackson
✅Nice! 🎤'Michael Jackson'🎤 has been successfully added!✅
----------Please select an option----------
1. Add an Artist ➕🧑‍🎤
2. List all Artists 📄
3. Add a Song ➕🎶
4. Remove a Song ➖🎶
5. List all Songs 📄
6. List an artist's assigned songs🕺🎶
7. Add song to your Favorites ➕🎼
8. Remove Favorited song ➖🎼
9. List all Favorited songs 📄
Enter 0 to Exit 🚀
>
```

```2. List all Artists 📄```

Option 2 will list all of the created artists for the user. However, remember that there is an option which will remove an artist/song, which we will cover shortly. But if a song/artist is removed, the said song/artist will not be shown any longer, unless added again.:
```
> 2
---------🌟Available Artists🌟---------
🥁🎹🎸Michael Jackson (ID: 35)🎸🎹🥁
----------Please select an option----------
1. Add an Artist ➕🧑‍🎤
2. List all Artists 📄
3. Add a Song ➕🎶
4. Remove a Song ➖🎶
5. List all Songs 📄
6. List an artist's assigned songs🕺🎶
7. Add song to your Favorites ➕🎼
8. Remove Favorited song ➖🎼
9. List all Favorited songs 📄
Enter 0 to Exit 🚀
>
```

```3. Add a Song ➕🎶```

Option 3 will allow the user to add a song. The user will be prompted to enter the name od the desired song. Once this is done, the user will also be given the ability to assign the song to an artist, if so desired, by entering the artist's ID. If not, simply enter 'NA'.:

```
> 3
---------🎶Adding song🎶---------
Enter song title (Or enter 0 to go back): Billy Jean
---------🌟Available Artists🌟---------
🥁🎹🎸Michael Jackson (ID: 35)🎸🎹🥁
Enter the ID of the artist to assign your song!(`NA` if not assigning): 35
Song Title:Billy Jean, Assigned Artist: Michael Jackson
✅Nicely done! Song added: 🎶Billy Jean🎶 and assigned to 🎤Michael Jackson (ID: 35)🎤!✅
----------Please select an option----------
1. Add an Artist ➕🧑‍🎤
2. List all Artists 📄
3. Add a Song ➕🎶
4. Remove a Song ➖🎶
5. List all Songs 📄
6. List an artist's assigned songs🕺🎶
7. Add song to your Favorites ➕🎼
8. Remove Favorited song ➖🎼
9. List all Favorited songs 📄
Enter 0 to Exit 🚀
>
```

```4. Remove a Song ➖🎶```

Option 4 will prompt the user to enter a song's ID, for removal. Please keep in mind that this cannot be undone, once processed. If the song is desired again, it will have to be added again, manually.:

```
> 4
---------❌Removing Song❌---------
---------🎹Available Songs🎹---------
🎶Billy Jean (ID:billy_jean🎶)
Please enter the song's ID to remove (Or enter 0 to go back): billy_jean
Done. ❌Billy Jean❌ has now been removed.
----------Please select an option----------
1. Add an Artist ➕🧑‍🎤
2. List all Artists 📄
3. Add a Song ➕🎶
4. Remove a Song ➖🎶
5. List all Songs 📄
6. List an artist's assigned songs🕺🎶
7. Add song to your Favorites ➕🎼
8. Remove Favorited song ➖🎼
9. List all Favorited songs 📄
Enter 0 to Exit 🚀
>
```

```5. List all Songs 📄```

Option 5 will list all of the available songs. Similar to the songs, remember that there is an option which will remove an artist/song, which we will cover shortly. But if a song/artist is removed, the said song/artist will not be shown any longer, unless added again. For the purposes of the example, I have added more songs, for listing!:

```
> 5
---------🎹Available Songs🎹---------
🎶American Idiot (ID:american_idiot🎶)
🎶Smooth Criminal (ID:smooth_criminal🎶)
🎶Party in the USA (ID:party_in_the_usa🎶)
----------Please select an option----------
1. Add an Artist ➕🧑‍🎤
2. List all Artists 📄
3. Add a Song ➕🎶
4. Remove a Song ➖🎶
5. List all Songs 📄
6. List an artist's assigned songs🕺🎶
7. Add song to your Favorites ➕🎼
8. Remove Favorited song ➖🎼
9. List all Favorited songs 📄
Enter 0 to Exit 🚀
>
```

```6. List an artist's assigned songs🕺🎶```

Option 6 will list every song that is assigned to an artist, once enetered the artist's ID. For the purposes of the example, I have already assigned songs to the artist Michael Jackson!:

```
> 6
---------🌟🌟Listing songs for an artist🌟🌟---------
---------🌟Available Artists🌟---------
🥁🎹🎸Michael Jackson (ID: 35)🎸🎹🥁
Enter the artist's ID: 35
Songs by 🌟Michael Jackson🌟
🎶Billy Jean (ID: billy_jean)🎶
🎶Bad (ID: bad)🎶
🎶Black or White (ID: black_or_white)🎶
🎶Thriller (ID: thriller)🎶
🎶Beat It (ID: beat_it)🎶
----------Please select an option----------
1. Add an Artist ➕🧑‍🎤
2. List all Artists 📄
3. Add a Song ➕🎶
4. Remove a Song ➖🎶
5. List all Songs 📄
6. List an artist's assigned songs🕺🎶
7. Add song to your Favorites ➕🎼
8. Remove Favorited song ➖🎼
9. List all Favorited songs 📄
Enter 0 to Exit 🚀
>
```

```7. Add song to your Favorites ➕🎼```

Option 7 gives the user the ability to add songs to their 'Favorites'! The user will be prompted for the song's ID.:

```
> 7
---------❤️Adding song to your favorites❤️---------
---------🎹Available Songs🎹---------
🎶American Idiot (ID:american_idiot🎶)
🎶Smooth Criminal (ID:smooth_criminal🎶)
🎶Party in the USA (ID:party_in_the_usa🎶)
🎶Bad (ID:bad🎶)
🎶Black or White (ID:black_or_white🎶)
🎶Thriller (ID:thriller🎶)
🎶Beat It (ID:beat_it🎶)
Enter your desired song's ID (Or enter 0 to go back): smooth_criminal
✅Success! 🎶Smooth Criminal🎶 now favorited:✅
----------Please select an option----------
1. Add an Artist ➕🧑‍🎤
2. List all Artists 📄
3. Add a Song ➕🎶
4. Remove a Song ➖🎶
5. List all Songs 📄
6. List an artist's assigned songs🕺🎶
7. Add song to your Favorites ➕🎼
8. Remove Favorited song ➖🎼
9. List all Favorited songs 📄
Enter 0 to Exit 🚀
> 7
---------❤️Adding song to your favorites❤️---------
---------🎹Available Songs🎹---------
🎶American Idiot (ID:american_idiot🎶)
🎶Smooth Criminal (ID:smooth_criminal🎶)
🎶Party in the USA (ID:party_in_the_usa🎶)
🎶Bad (ID:bad🎶)
🎶Black or White (ID:black_or_white🎶)
🎶Thriller (ID:thriller🎶)
🎶Beat It (ID:beat_it🎶)
Enter your desired song's ID (Or enter 0 to go back): black_or_white
✅Success! 🎶Black or White🎶 now favorited:✅
```

```8. Remove Favorited song ➖🎼```

Option 8 will allow the user to remove a song from the user's Favorites. The user will be prompter for the song's ID:

```
> 8
---------❌Removing Favorited song❌---------
---------❤️Your Favorited Songs❤️---------
🎶American Idiot(ID: american_idiot)🎶
🎶Smooth Criminal(ID: smooth_criminal)🎶
🎶Black or White(ID: black_or_white) by Michael Jackson🎶
Enter the favorited song's ID (Or enter 0 to go back): smooth_criminal
Done! ❌Smooth Criminal(ID: smooth_criminal)❌ has now been removed from your Favorites.
----------Please select an option----------
1. Add an Artist ➕🧑‍🎤
2. List all Artists 📄
3. Add a Song ➕🎶
4. Remove a Song ➖🎶
5. List all Songs 📄
6. List an artist's assigned songs🕺🎶
7. Add song to your Favorites ➕🎼
8. Remove Favorited song ➖🎼
9. List all Favorited songs 📄
Enter 0 to Exit 🚀
>
```

```9. List all Favorited songs 📄```

Option 9 will list all of the user's most up to date Favorited songs.:

```
> 9
---------❤️Your Favorited Songs❤️---------
🎶American Idiot(ID: american_idiot)🎶
🎶Black or White(ID: black_or_white) by Michael Jackson🎶
----------Please select an option----------
1. Add an Artist ➕🧑‍🎤
2. List all Artists 📄
3. Add a Song ➕🎶
4. Remove a Song ➖🎶
5. List all Songs 📄
6. List an artist's assigned songs🕺🎶
7. Add song to your Favorites ➕🎼
8. Remove Favorited song ➖🎼
9. List all Favorited songs 📄
Enter 0 to Exit 🚀
>
```

```Enter 0 to Exit 🚀```

Lastly, if the user would like to leave the application, entering 9 will close the progam.:

```
----------Please select an option----------
1. Add an Artist ➕🧑‍🎤
2. List all Artists 📄
3. Add a Song ➕🎶
4. Remove a Song ➖🎶
5. List all Songs 📄
6. List an artist's assigned songs🕺🎶
7. Add song to your Favorites ➕🎼
8. Remove Favorited song ➖🎼
9. List all Favorited songs 📄
Enter 0 to Exit 🚀
> 0
Exiting menu.. Goodbye!
```

# Support

For any and all questions, concerns, or comments, please do not hesitate to reach out to me via email!

:envelope:: **martingarcia804@yahoo.com**

## Authors and acknowledgment

Many thanks go to the many communities online and the technical support agents from Flatiron, who were a tremendous help. And I am sure I speak for many programmers when I also say thank you to Google!