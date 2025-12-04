## User
You will need to follow Development.md for initial set up.

Assuming this, you will go to src/Spa.Template.Api/appsettings.json and input your username and password:
<img width="1446" height="827" alt="insert_credentials" src="https://github.com/user-attachments/assets/c0ff46a5-a13c-4f85-baf8-782c9c7c8092" />

After this, you can run the following comamnds to set up the webpage at https://localhost:7000
1. ```docker compose build```
2. ```docker compose up```

On this webpage, you will be prompted to sign into Cheetah:
<img width="1808" height="904" alt="Screenshot 2025-10-29 215745" src="https://github.com/user-attachments/assets/fd0895b6-a2f0-44ab-9aea-167f57fa8b64" />

After signing in, you will be brought to the homepage where it will automatically load your clients as such:
<img width="1918" height="912" alt="client_frontpage" src="https://github.com/user-attachments/assets/93afd061-3859-4991-8872-cf09eb32d569" />

From here, you can create a client if you so choose:
<img width="1897" height="908" alt="create_client" src="https://github.com/user-attachments/assets/ac338ef1-7a8b-49d3-98f8-8d623ca3e3c6" />

Going back to the home page...

Clicking a client will bring you to said client's scenarios:
<img width="1918" height="911" alt="scenario_select" src="https://github.com/user-attachments/assets/9c8a3343-a02b-44a1-b33c-1a6938ab2b79" />

Clicking a scenario will allow you to run an optimization on that scenario, you will select what parameters you would like to enter, but you are limited to 2.
<img width="1898" height="907" alt="optimization_entry" src="https://github.com/user-attachments/assets/763cf229-e721-4aca-af36-2a5d9c88b303" />


Upon selection of next, it will run the optimization and tell you what is recommended, as well as the numbers behind it (with graphs and warnings!):
<img width="1897" height="907" alt="optimization_results_1" src="https://github.com/user-attachments/assets/f139503d-f775-404e-b0e0-0d4d37812b64" />
<img width="1902" height="908" alt="optimization_results_2" src="https://github.com/user-attachments/assets/3bc1d3c3-185f-4431-8295-4979c0244bdd" />

