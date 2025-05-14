# Pre-Workshop Activities

The software ecosystem for computational teaching and learning is vast! But we don't need to learn it all at once. We introduce several software systems below but the only items which are *required* for workshop participants are Syzygy + GitHub. In particular, please make sure to complete steps 1-5 in the GitHub section prior to the start of the workshop.

## Syzygy

The [Pacific Institute for the Mathematical Sciences (PIMS)](https://www.pims.math.ca) created Syzygy which hosts Jupyter notebooks for students, faculty and staff located at universities across Canada. Go to [syzygy.ca](https://syzygy.ca), click the *Launch* button in the top right menu, find your institution and login with your university credentials. Alternatively, you can login to the PIMS JupyterHub using a Google login.

We use Syzygy for computational teaching and learning for several reasons:

* No software installation required
* Provides a common development environment for all users
* Works with any device with a web browser (such as a tablet)
* JupyterLab GitHub extension simplifies collaboration

Syzygy allows students and instructors to get started with Python and Jupyter quickly! After gaining experience with Python and Jupyter through Syzygy, users can use [conda](#conda) to install and run software and their own machine.

## Python and Jupyter

[Python](https://python.org) is a general purpose open source programming language and [Jupyter](https://jupyter.org) is a web application for created computational documents. Check out [Python for UBC Math](https://ubcmath.github.io/python/) to explore the Jupyter Lab environment on Syzygy, and [Mathematical Python](https://patrickwalls.github.io/mathematicalpython) to learn more about mathematical computing with Python and SciPy.

## Examples from UBC Math

Go to Syzygy and open the GitHub window (see the icon in the shape of a diamond on the left side of the JupyterLab environment). Click *Clone a Repository* and paste the following URL:

```
https://github.com/patrickwalls/examples.git
```

Select *Download the repository* and click *Clone*. You should see a folder called *examples* in the file navigation window on Syzygy. Navigate into the folder to see examples from several courses at UBC. See the [UBC Math Coursemap](https://ubcmath.github.io/coursemap/) for more info about the courses.

## GitHub

[GitHub](https://github.com) hosts software projects and enables collaboration. We will use GitHub extensively in our workshop to share documents and to collaborate. Complete the following steps to share documents between GitHub and Syzygy:

**Step 1.** Create a GitHub account on [github.com](https://github.com).

**Step 2.** Create a personal access token on GitHub:

* Go to your GitHub Profile and click *Settings* from the menu in the top right corner
* Click *Developer Settings* from the bottom of the navigation menu
* Click *Personal access tokens* then *Tokens (classic)*
* Click *Generate new token (classic)*
* Enter a description (perhaps *Syzygy* since this is where we are using the token)
* Choose an expiration date (or choose *No expiration* if you like)
* From *Select scopes* select **repo**
* Click *Generate token*.
* Copy the token, create a new text file on Syzygy, paste the token and save.

**Step 3.** Create a new GitHub repository:

* Go to your GitHub Profile, click *Repositories* and click *New*
* Choose a name for your repo (such as *birsworkshop*)
* Write a description
* Select *Public* to make your repo visible on GitHub
* Select *Add a README file*
* Click *Create repository*

**Step 4.** Clone repository to Syzygy:

* Go to the repository page on GitHub
* Click *Code* (green button) and copy the URL
* Go to Syzygy and check the file navigation window to make sure you are in the top level folder of your account
* Go to the GitHub window on Syzygy (see the icon in the shape of a diamond)
* Click *Clone a Repository*, paste the repo URL, select *Download the repository* and click *Clone*
* You should see the repository folder in your file navigation window on Syzygy

**Step 5.** Commit and push changes to GitHub

* Go to the file navigation window on Syzygy and click the folder for the repo that you just cloned from GitHub
* Open the file <em>README.md</em>, make a change and save
* Go to the GitHub window on Syzygy (see the icon in the shape of a diamond) and the file <em>README.md</em> should be listed under the header **Changed**
* Hover over the file and click `+` to add the file to **Staged**
* Write a short summary (such as "Update README") in the *Summary* field at the bottom of the GitHub window and click commit
* The *Push* button at the top of the GitHub window is the cloud with up arrow icon (and there should be an orange dot beside it to indicate that there is a commit ready to push to GitHub)
* Click the *Push* button, enter your GitHub username and (most importantly!) enter your personal access token (by copying and pasting from the text file where you previsouly saved the token) and click *Ok*

Well done! We'll be creating/cloning repos and committing/pushing changes often and so we recommend repeating steps 3-5 a few times to get the hang of it!

(conda)=
## conda

Download and install [conda](https://www.anaconda.com/docs/getting-started/getting-started) to run Pyton and Jupyter locally on your machine. This is **not** required for workshop participants but it is required if you want to create autograded assignments with nbgrader.

## nbgrader

[nbgrader](https://nbgrader.readthedocs.io) is a Python package for creating and managing auto-graded assignments in Jupyter notebooks. Unfortunately, nbgrader does not work on Syzygy and so users must install Python and Jupyter on their own machines to create nbgrader assignments.

Once you are running Python and Jupyter on your machine, install nbgrader:

```
pip install nbgrader
```

Install the JupyterLab nbgrader extension by opening JupyterLab and clicking the extensions window (see the puzzle piece icon on the left of the JupyterLab environment). Search for nbgrader and install. Refresh the page and you should see *Nbgrader* in the menu bar at the top of the JupyterLab window. Click *Nbgrader* and select *Formgrader* to get started.

## CanvasAPI

[CanvasAPI](https://canvasapi.readthedocs.io/en/stable/index.html) is a Python package to connect with Canvas. This makes it easy to download/upload grades and feedback. If you use Canvas at your institution, then login and go to your *Account* and then *Settings* and click *New Access Token*. Save the token in a file called `token.txt` and run the following script (with the correct `API_URL` for your institution).

```
from canvasapi import Canvas

API_URL = "https://ubc.instructure.com"

with open("token.txt","r") as f:
    API_KEY = f.read()

canvas = Canvas(API_URL, API_KEY)

courses = canvas.get_courses()
for course in courses:
    print(course.name)

assignments = courses[0].get_assignments()
for assignment in assignments:
    print(assignment.name)

submissions = assignments[0].get_submissions()
for submission in submissions:
    print(submission.grade)