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
<img width="1919" height="906" alt="Screenshot 2025-10-29 223137" src="https://github.com/user-attachments/assets/aa4187b7-d2df-4527-822d-fbb836d40260" />


Clicking a client will bring you to said client's scenarios:
<img width="1919" height="908" alt="Screenshot 2025-10-29 223150" src="https://github.com/user-attachments/assets/bbcdebba-dcde-4463-9416-fae499eed584" />

Clicking a scenario will allow you to run an optimization on that scenario, you will select what parameters you would like to enter, but you are limited to 2.
<img width="1919" height="914" alt="Screenshot 2025-10-29 223224" src="https://github.com/user-attachments/assets/a3f4a106-97f8-44e0-a9eb-42c30c8c067f" />

Upon selection of next, it will run the optimization and tell you what is recommended, as well as the numbers behind it:
<img width="1714" height="840" alt="Screenshot 2025-10-29 223250" src="https://github.com/user-attachments/assets/dcfeaaf0-2809-4ac9-8902-7edf00ab6325" />

