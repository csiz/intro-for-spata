Setting stuff up
----------------

1. Install python 3 from python.org. 
    This is the programming language, duh. Make sure you have "Add to PATH" selected; that's the default.

2. And git+github from github.com.
    This little program tracks changes and makes it easy to collaborate with others on bigger projects. If
    you want to know more, look up "version control". It's useful outside of programming too, but you have
    to figure out how to make .docx, etc. look nicely.

Now create your project in GitHub and open up the new folder. Put everything related to your poject here
and every time you make changes to it remember to write a little description of them and click "Commit".
This commiting thing seems annoying until you actually need it. For one it saves you from report_final_3,
but more importantly it gives you a sense of history of your project. This means you can go back to any
point and undo changes there (really helpful when you just noticed things are messed up). Or see the 
history of changes that other people made.

Trying python
-------------

Cool you have your project folder, it already has ".gitignore" and some other git related stuff in it.

Open a command line window; in windows you can do that via `shift + right click -> Open command window here`.

In the command window you can type `python` to open up ... python. Try it out. In general to close things
from the command line you do `ctrl + c`. Sometimes (cough ipython) intercepts these, but you can tell it
"I'm done typing" via `ctrl + d`.

More setup
----------

Exit python. Alongside it you install `pip` which is a nice program that manages python packages for you.
Try running this command `pip install virtualenv ipython pandas numpy matplotlib`. I'll explain what got
installed in a moment.

To let other people replicate your work you want to specify everything you use and make sure you don't
use other stuff that's just there on your computer. This is where `virtualenv` comes in. It's a tool
that creates a completely separate environment for your python. Let's do this; in your project folder
in the command line there do `virtualenv env`. This creates a folder "env" with a copy of your python.
This way you can even have more versions of python installed, though let's not get into that. Now 
write `env\Scripts\activate` to ... activate it.

Now that it's activated, reinstall the things in this isolated environment by running the command again
`pip install ipython pandas numpy matplotlib`. For the sharing with other people run this command
`pip freeze > requirements.txt`; this creates a file that lists exactly what you have installed.

Git interuption
---------------

You've done some changes, so it's about time you "Commit". But first check out what those changes are,
you'll see a lot of garbage in there relating the "env" folder like 6000 new files. You don't want to
save those because they're completely specified by "requirements.txt" so open up ".gitignore" and add
the line `env/` somewhere. This tells git (and GitHub) to ignore the folder. You can now write a
description of what you did and commit to master (I'll tell you who's your master once you get the
hang of committing).

Trying IPython
--------------

Finally the cool part. Run on the command line `ipython notebook`. This will start a little server
that keeps running in the command line (you won't need it anymore) and opens up a webpage you can
create notebooks in. These are saved locally, you'll probably see the "requirements.txt" file there too.

Create a pythhon 3 notebook and write some code :D

    import numpy as np
    import pandas as pd
    import matplotlib.pyplot as plt
    %matplotlib inline # this is a "magic" command in ipython that says show the plots inline

Run that snipped to import the libraries you want, you shouldn't get any errors now.

Here's some code for a simple plot to get you started:

    x = np.linspace(0, np.pi*2, 101) # create 101 points from 0 to 2pi
    y = np.sin(x) # apply the function sin to each of those points
    plt.plot(x, y) # plot y against x using matplotlib


Requirements thing
------------------

When you want to tell other people to run your scripts you can tell them, install python then run
`pip install -r requirements.txt` and everything you're using will be installed for them as well.