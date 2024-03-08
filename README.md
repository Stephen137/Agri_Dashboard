# Agricultural Dashboard

This project:

- pulls data from the [World Bank API](https://datahelpdesk.worldbank.org/knowledgebase/articles/898581-api-basic-call-structures) by harnessing the [requests](https://pypi.org/project/requests/) HTTP library
- cleans the data using [pandas](https://pandas.pydata.org/)
- creates four interactive plots using [Plotly](https://plotly.com/)
- builds a dashboard with user-selection filter, leveraging the [Bootstrap library](https://getbootstrap.com/) and [Flask framework](http://flask.pocoo.org/).
- deploys the app via [Heroku](https://agri-dashboard-137-345748516635.herokuapp.com/)


## Running the project locally

### **Step 1: Fork this repo**

Forking a GitHub repository is a common operation done to create your copy of someone else's repository on GitHub. Here's how you can do it:

1. Visit the Repository: https://github.com/Stephen137/Agri_Dashboard

2. Fork the Repository: In the top-right corner of the page, you'll find a "Fork" button. Click on it. This action will create a copy of the repository under your GitHub account.

3. Wait for the Fork: GitHub will take a moment to fork the repository. Once it's done, you'll be redirected to your copy of the repository.

4. Clone Your Fork: Now that you have your fork, you can clone it to your local machine using Git. On the repository page, click the green "Code" button, and then copy the URL.

5. Open Terminal (or Command Prompt): Navigate to the directory where you want to store the cloned repository.

6. Clone the Repository: Use the git clone command followed by the URL you copied. It will look something like this:

`git clone https://github.com/your-username/repository-name.git`


### **Step 2: Create a virtual environment**

Using virtual environments promotes best practices in Python development, including dependency management, reproducibility, and cleanliness.  It allows you to isolate dependencies for different projects and hopefully avoid you from entering dependency hell! 

1. Create a virtual environment by running the following `python3 -m venv <virtual_env_name>` replacing <virtual_env_name> with your own memorable name
2. Activate the environment `source <virtual_env_name>/bin/activate`

### Step 3: Modify the `worldbank.py` file and install dependencies

1. You need to ***uncomment*** the `app.run(host='0.0.0.0', port=3000, debug=True)` line in the `worldbank.py` file.
2. Install the required packages: `pip install -r requirements.txt`
3. Then run the app from the command line: `python worldbank.py`

The dashborard app should now render locally at port 3000.

## Deploying the project on Heroku

### **Step 1: Create a free Heroku account (for deployment of app)**

Heroku is a cloud platform as a service (PaaS) that allows developers to build, deploy, and manage applications easily. It supports various programming languages such as Ruby, Node.js, Python, Java, PHP, and Go, among others. Heroku abstracts much of the infrastructure management away from developers, allowing them to focus on writing code and deploying applications without having to worry about the underlying hardware or server management.

Sign up for a free acount [here](https://id.heroku.com/login)

>It is a good practice to enable [Multi-Factor Authentication](https://devcenter.heroku.com/articles/multi-factor-authentication). 

Heroku is just one option of many for deploying a web app. The big internet companies offer similar services like [Amazon's Lightsail](https://aws.amazon.com/lightsail/), [Microsoft's Azure](https://learn.microsoft.com/en-us/samples/azure-samples/python-docs-hello-world/python-flask-sample-for-azure-app-service-linux/) and [Google Cloud](https://cloud.google.com/appengine/docs/standard/setting-up-environment?tab=python). However, these services tend to require more configuration. Most of these also come with either a free tier or a limited free tier that expires after a certain amount of time.


### **Step 2: Install dependencies**

The new virtual environment will automatically come with Python packages meant for data science. In addition, pip install the specific Python packages needed for the web app:

`pip install flask pandas plotly gunicorn`

Check if you already have Heroku installed:

`heroku --version`

If not, install it from the command line:

`curl https://cli-assets.heroku.com/install-ubuntu.sh | sh`

Other dependencies are included in the `requirements.txt` file however these will be installed by Heroku as part of the applicatin build.


### **Step 3: Login to Heroku**

You can log in from the command line using:

`heroku login`

A browser should open asking you to log in - and once confirmed you can return to the cli.


### **Step 4: Initilaize a git repository**

Run this command just once at the beginning:
`git init`

Configure git username and email:
`git config --global user.email "you@example.com"`
`git config --global user.name "Your Name"`

Every time you make any edits to any file:
`git add .`

Check which files are ready to be committed:
`git status`

Make a commit:
`git commit -m "your message"`


### **Step 5: Create a Heroku app**

`heroku create <your-app-name> --buildpack heroku/python` replacing <your-app-name> with your own choice.

This should create a git repository on Heroku and a web address for accessing your web app. You can check that a remote repository was added to your git repository with the following terminal command:

`git remote -v`


### **Step 6: Final push!**

Now, push your local repo to the remote Heroku repo:

`git push heroku master`

Your app should now be available for viewing and SHARING at your web app's address, such as https://agri-dashboard-137-345748516635.herokuapp.com/, in the browser to see the results.

Other useful commands:
- Clear the build cache
`heroku plugins:install heroku-builds`
`heroku builds:cache:purge -a <app-name> --confirm <app-name>`

- Permanently delete the app
`heroku apps:destroy  <app-name> --confirm <app-name>`

### Acknowledgements

Special thanks to [Andrew Paster](https://www.linkedin.com/in/andrewpaster/) for his guidance on how to pull data from APIs, leverage the Bootstrap library and Flask framework to create and deploy an iteractive dashboard,  and his general expert insights on best Software Engineering practices.



