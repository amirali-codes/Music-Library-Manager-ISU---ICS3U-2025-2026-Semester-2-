# Music-Library-Manager-ISU---ICS3U-2025-2026-Semester-2-

# OVERVIEW

For my ISU, I built a Music Library Manager that lets a user keep track of their songs, artists, and ratings. I designed it to be interactive, so everything runs through a main menu where the user just types a number to choose what they want to do. I also made sure it has some built-in data so it isn't empty when you start it up.

# My Variables and Data Structures

I decided to use parallel ArrayLists to store all the information. I used three of them:

- titles: A String list for the names of the songs.
- artists: A String list for the singers or bands.
- ratings: An Integer list for the scores (0-100).

I chose ArrayLists over regular arrays because I wanted the library to be able to grow. If I used a standard array, the user would be stuck with a fixed limit, but with ArrayLists, they can keep adding as many songs as they want.

I also used a Scanner called sc to grab all the input, and a boolean called running to keep the main menu loop going until the user hits the exit option.

# How I Implemented Each Section

# 1. The Main Menu and Error Handling
I put the whole program inside a wile (running) loop. Inside that loop, I print the menu options. I used sc.nextLine() to get the user's choice as a string. I did this on purpose so that if someone accidentally types a letter instead of a number, the program won't crash, it just hits the else statement and asks them to try again.

# 2. Adding Songs

In this part, I set up a counter to make sure the user can only add two songs per round. I used a while loop for the rating input to make sure the number is between 0 and 100. If they type something like 150, it tells them to keep it in range and asks again. After the first song, it asks "yes/no" if they want another one.

# 3. Average, Min, and Max

For the average, I just loop through the ratings list, add them all up, and divide by the size of the list. For the Min and Max, I used a linear search. I keep track of the maxIdx and minIdx while looping through the list. This lets me print out the full song info (title and artist) for the highest and lowest rated songs at the end.

# 4. The Song List and Sub-Menu

This part prints out the ID (which is just the index in the ArrayList), the title, artist, and rating. I added a sub-menu here so you can edit or remove a song without going back to the main screen. To remove a song, I just call .remove(id) on all three lists at the same time so they stay synced up.

# 5. Vertical Rating Distribution Chart

This was the hardest part to code. First, I count how many songs fall into each "Star" category using an if-else chain. Then, I find the highest count to know how tall the chart needs to be. I use a for loop to print the chart from the top down. In each row, I check if a category has enough height to get a #. If it does, I print it; if not, I print spaces so the columns stay lined up.

# 6. Searching

I used .toLowerCase() on both the user's search and the song data so the search isn't picky about capital letter and it is case sensitive. I also used .contains() so that if you search for "Travis" it will find "Travis Scott." While it prints the result, it also calculates if that specific song is above or below the library's average rating.

# 7. Top and Bottom 20%

I didn't want to mess up the original order of my library, so I made temporary copies of the lists. I sorted these copies from highest to lowest rating. Then I used Math.ceil to figure out what 20% of the list size is and printed that many songs from the very top and the very bottom of my sorted copies.

# Logic Summary

The main logic I used is keeping the three lists exactly in sync. Whenever I add, remove, or sort (in the temp lists), I make sure every action happens to the titles, artists, and ratings at the same index. This keeps the data organized and accurate.
