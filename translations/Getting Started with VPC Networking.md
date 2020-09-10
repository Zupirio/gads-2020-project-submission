# Lab: Google Cloud Fundamentals: Getting Started with App Engine  

## Objectives

In this lab, you learn how to perform the following tasks:

- Initialize App Engine.
- Preview an App Engine application running locally in Cloud Shell.
- Deploy an App Engine application, so that others can reach it.
- Disable an App Engine application, when you no longer want it to be visible.
***
## Steps
1.  Initialize App Engine
    1. Initialize your App Engine app with your project and choose its region:
     `gcloud app create --project=$DEVSHELL_PROJECT_ID`
    2. Clone the source code repository for a sample application in the hello_world directory:
     `git clone https://github.com/GoogleCloudPlatform/python-docs-samples`
    3. Navigate to the source directory:
     `cd python-docs-samples/appengine/standard_python3/hello_world`
2.  Run Hello World application locally
    1.  Execute the following command to download and update the packages list.
        `sudo apt-get update`
    2.  Set up a virtual environment in which you will run your application. Python virtual environments are used to isolate package installations from the system.
        `sudo apt-get install virtualenv`
        <br>
        >If prompted [Y/n], press Y and then Enter.
        
        `virtualenv -p python3 venv`
    3.  Activate the virtual environment.
        `source venv/bin/activate`
    4.  Navigate to your project directory and install dependencies.
        `pip install  -r requirements.txt`
    6.  Run the application:
        `python main.py`
    7.  **In Cloud Shell, click Web preview (Web Preview) > Preview on port 8080 to preview the application.**
    8.  To end the test, return to Cloud Shell and press Ctrl+C to abort the deployed service.
     `sudo apt-get update`



3.  Deploy and run Hello World on App Engine
    1.  Navigate to the source directory:
        `cd ~/python-docs-samples/appengine/standard_python3/hello_world`
    3.  Deploy your Hello World application.
        `gcloud app deploy`
        <br>
        >If prompted "Do you want to continue (Y/n)?", press Y and then Enter.
        
        This app deploy command uses the app.yaml file to identify project configuration.
    4.  Launch your browser to view the app at http://YOUR_PROJECT_ID.appspot.com
        `gcloud app browse`
    5.  Copy and paste the URL into a new browser window.
        Result:
        ![Preview of successful deployment](https://cdn.qwiklabs.com/fnmJeOzuz%2BgxMdMg175OIbQRE84kwir5fKVcB1kXihg%3D)
        ***

4.  Disable the application

