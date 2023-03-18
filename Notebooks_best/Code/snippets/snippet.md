Snippet Example

How to add/edit code snippets in jupyer notebook?
🌐
stackoverflow.com
› questions › 55261170 › how-to-add-edit-code-snippets-in-jupyer-notebook
If you are using Anaconda, you don't necessarily need to go searching for directories. There is a template embedded in the "Nbextensions" tab.

Check "Snippets Menu" box
Scroll down to 'Parameters' and check the "Include custom menu...JSON string below" box
Insert whatever sample snippet you want
Refresh your notebook
Check out one of my snippets:

{
    "name" : "My favorites",
    "sub-menu" : [
        {
            "name" : "import packages",
            "snippet" : ["# import various packages"
                   "import os"
                   "import scipy"
                   "import pandas as pd"
                   "import numpy as np"
                   "import seaborn as sns"
                   "import matplotlib.pyplot as plt"

                   "%matplotlib inline"

                   "# plot settings"
                   "from pandas.plotting import register_matplotlib_converters"
                   "register_matplotlib_converters()"
                   "plt.rcParams['agg.path.chunksize'] = 10000"]
        },
        {
            "name" : "TeX can be written in menu labels $\\alpha_W e\\int_0 \\mu \\epsilon$",
            "snippet" : ["another_new_command(2.78)"]
        }
    ]
}
Also, be careful with the quotations and commas. Additional help on that can be found here.

