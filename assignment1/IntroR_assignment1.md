## Assignment 1

Due September 26th, 21:00, for max. 10 points, 

October 3rd, by 21:00 for 8 points max. for late submission

Please e-mail your homework to alxdra.konovalova@gmail.com in a .pdf or an .html format (please use R Markdown to create your file) 
Or send the link to your file on Github page and add user _vydra-v-getrax_ to collaborators (Repository > Settings > Collaborators > Add people)


### Task 1 -- 4 points

Take the data [about the UK pubs](https://raw.githubusercontent.com/vydra-v-getrax/intro_to_r/main/assignment1/UK_pubs.csv)

Plot the 40 or 50 most frequent names of pubs in the UK: the x-axis is for the number of symbols in the pub name, the y-axis is for the number of bars with the same name.

Your goal is to recreate the plot below (don't forget the names for the axes, the title and the source of the data at the bottom of the plot):

![](https://github.com/vydra-v-getrax/intro_to_r/blob/main/assignment1/pubs.png)

**A hint:**

+ use ```geom_point()``` and ```geom_text_repel()``` from the ```ggrepel``` package

### Task 2 -- 4 points

Take the data from [a questionnaire](https://raw.githubusercontent.com/vydra-v-getrax/intro_to_r/main/assignment1/mad_questionary.csv)

You can notice that the values for the sex variable are spelled inconsistently: *Ж/ж/женский/Женский* and *М/м/мужской/Мужской*. Manipulate the data so that *Ж/ж/женский/Женский* is turned into *женский* and *М/м/мужской/Мужской* is turned into *мужской*. Then plot the data.

Your goal is to recreate the plot below:

![](https://github.com/vydra-v-getrax/intro_to_r/blob/main/assignment1/questionnaire.png)

**A hint:**

+ use ```geom_dotplot()``` with the argument ```method = "histodot"``` and with a deleted axis ```scale_y_continuous(NULL, breaks = NULL)```

