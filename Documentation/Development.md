# Tech Stack

Currently under the assumption of Windows

## Required Tech Stack
1. .NET Framework
2. Vue.js
3. Docker
4. PostgreSQL

## Set up
### .NET Framework
1. Visit https://dotnet.microsoft.com/en-us/download
2. Download .NET 8.0
  <img width="1812" height="887" alt="download_net" src="https://github.com/user-attachments/assets/ea6fbea6-3edf-42c4-8e1e-b31e7a6a7658" />
  
3. Run the exe installer and follow the prompts

### Vue.js
1. Visit https://nodejs.org/en/download
2. Scroll down to the prebuilt section, select your system and architecture, and then download the msi
<img width="1827" height="892" alt="download_node" src="https://github.com/user-attachments/assets/ea2ead73-9b25-48cb-89a6-63bdd9f3fef5" />

3. Run the msi file and follow the prompts
4. Go into terminal and run
   `npm create vue@latest
   `

### Docker
1. Visit https://www.docker.com/products/docker-desktop/
2. Download Docker Desktop with your corresponding system and architecture
<img width="1831" height="892" alt="download_docker" src="https://github.com/user-attachments/assets/529b8138-9f25-4bc8-8737-f5a470d1af19" />

3. Run the exe installer
4. Select WSL when prompted, otherwise go through traditional prompts

### PostgreSQL
1. Visit https://www.enterprisedb.com/downloads/postgres-postgresql-downloads
2. Download according to your architecture and OS, 18.0 is recommended
<img width="1894" height="874" alt="Screenshot 2025-10-24 213058" src="https://github.com/user-attachments/assets/80ced49a-4d8d-460f-a624-cb7d1351359c" />

3. Run the exe and follow the prompts
4. Set a default password for your default account (you should probably save it!)
<img width="678" height="531" alt="Screenshot 2025-10-24 213411" src="https://github.com/user-attachments/assets/6819feb9-111e-4c0e-8c6a-ccc2c1fc324c" />

6. Currently leave your port the same
7. Select Next and Finish


# Setting up program
  NOTE: You will be prompted to download various items, do download them!
1. Go into your bitbucket account, into the bsu.rothscope repo, and hit 'Clone'. This will give you a command.
2. Go into your text editor and input this command into the terminal
3. When prompted to create an HTTPS certificate select yes, if not prompted

    i. In your terminal run

   `dotnet dev-certs https --trust`
   
    ii. Go to tools>scripts>Windows>Export-DevCert.ps1 and run it
   
<img width="1828" height="927" alt="dev_cert" src="https://github.com/user-attachments/assets/714c78e5-b286-4747-9bb8-bdfe289c710f" />

5. Go into your GitHub account, assuring that you're in the Accutech repo, and go to Settings>Developer Settings>Tokens (classic)
6. Create a token ONLY selecting 'read:packages'
7. Copy this token and create an environment variable named 'DESIGN_SYSTEM_TOKEN' and assign the env. variable your token string
8. Then perform the following commands in your text editor terminal to install yarn

   `cd src\spa-template-vue`
   
   `mkdir .yarn\releases`
   
   `Invoke-WebRequest https://repo.yarnpkg.com/4.2.2/packages/yarnpkg-cli/bin/yarn.js -OutFile .yarn\releases\yarn-4.2.2.cjs`
10. Your local file now be set up.

# Running program
1. In your terminal run `docker compose build`, this should have a LOT of things running in the terminal
<img width="1478" height="161" alt="Screenshot 2025-10-24 212434" src="https://github.com/user-attachments/assets/55595281-069a-42c9-82d3-83669a2d7b3d" />

2. Then run `docker compose up`
<img width="1477" height="193" alt="Screenshot 2025-10-24 212713" src="https://github.com/user-attachments/assets/3fb0b633-fb26-4786-a43b-1c5ea9b8ad4d" />

3. Go into your web browser and go to 'https://localhost:7777', the page should look something like this
<img width="1905" height="960" alt="Screenshot 2025-10-24 212753" src="https://github.com/user-attachments/assets/54252051-71e1-42d3-869f-f2b959c26893" />

4. If this is your first time running it, currently select 'Forget Password' and input your given account details. This should send an email which will allow you to set a password. You can then log in and you will be able to interact with the web page.

# Structuring
## Templates
### spa-template-vue
This folder displays the front end and holds the UI/UX. It uses Vue.js. This is where you would edit if you wanted to create more pages, create buttons for new interactions, etc.
### Spa.Template.Web
This folder is the set up for the BFF (Backend-For-Frontend) and allows communication between the API and the Front Dnd. This is most likely not where you will edit. 
### Spa.Template.Api
This folder holds the API endpoints that our Front End calls. This is where the majority of the Back End is hosted.
### Spa.Template.Core
This holds mostly entities and enums.
### Spa.Template.Infrastructure
This is where our API goes to interact with MoneyTree's API. You would edit here if you wanted to make a new API call to MoneyTree.
### Spa.Template.Infrastructure.Migrations
Currently, nothing is in there.
## Important Configs and Env's
### src/Spa.Template.Api/appsettings.json
This currently holds the MoneyTree url as well as your password and username for accessing their API.
### .env
This holds a lot of the paths to important variables. The only thing not found in here, besides the appsettings.json for API, are the launch settings for BFF pages (API and Web).
### src/Spa.Template.Web/launchsettings.json & src/Spa.Template.Api/launchsettings.json
Not typically edited. Holds the launch settings, specifically the URL.
   
# Testing
We do not currently have automated testing. The way that we test is by running through the web page since every part of the program is touched. The web page is very linear, so if you want to test something it is fairly straightforward. If you open F12, you can see what you enter and the response you get back whenever you click a button. If you do not send out a response when clicking a button, there is an issue with your front end. If you send out a response, and you get an error back, there is something wrong with either the API endpoint you're calling, src/Spa.Template.Api/Program.cs, or src/Spa.Template.Infrastructure/MoneytreeService. Beyond that, there isn't much to interpret.

# Replicating via Docker
## Install Prerequisites
1. Visit https://www.docker.com/products/docker-desktop/
2. Download Docker Desktop with your corresponding system and architecture
3. Run the exe installer
4. Select WSL when prompted, otherwise go through traditional prompts

## Clone Repos
1. Go into your bitbucket account, into the bsu.rothscope repo, and hit 'Clone'. This will give you a command.
2. Go into your text editor and input this command into the terminal
3. When prompted to create an HTTPS certificate select yes, if not prompted

    i. In your terminal run

   `dotnet dev-certs https --trust`
   
    ii. Go to tools>scripts>Windows>Export-DevCert.ps1 and run it

5. Go into your GitHub account, assuring that you're in the Accutech repo, and go to Settings>Developer Settings>Tokens (classic)
6. Create a token ONLY selecting 'read:packages'
7. Copy this token and create an environment variable named 'DESIGN_SYSTEM_TOKEN' and assign the env. variable your token string
8. Then perform the following commands in your text editor terminal to install yarn

   `cd src\spa-template-vue`
   
   `mkdir .yarn\releases`
   
   `Invoke-WebRequest https://repo.yarnpkg.com/4.2.2/packages/yarnpkg-cli/bin/yarn.js -OutFile .yarn\releases\yarn-4.2.2.cjs`
10. Your local file now be set up.

## Run
Run the following command:

  `docker-compose up`
  
A good first place to start if you have issues is to rebuild with no cache:

  `docker-compose build --no-cache`

## Browse
1. Go to https://localhost:7777
2. Log in to Cheetah OAuth
3. Select the user 'Allen Abbett'
4. Select the scenario 'Retire 63/62 - Downsize & Move to WA'
5. Select the optimization 'Maximize Capital' and 'Next'
6. If you see a text box containing a strategy, tables, and highlighted numbers then everything is working.

