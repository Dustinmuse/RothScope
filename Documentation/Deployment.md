## Requirements:
### Server:
Currently local as client doesn't want it hosted.
### File/Folder Location:
Currently unimportant.
### Start/Stop System:
In your terminal for your text editor, type 

```docker compose build```

```docker compose up```

It will then run on Docker Desktop, which you can stop by going into Docker Dekstop and clicking the stop button on the container.

<img width="1916" height="966" alt="stop_program" src="https://github.com/user-attachments/assets/a128fe42-9061-4f05-a0c2-b6d6130e0b29" />

### Error Finding
You have two main regions for finding application errors:
1. API call errors will be displayed upon hitting F12 on the webpage. From here, the majority will be in Spa.Template.Api/endpoints or Spa.Template.Infrastructure/MoneytreeService.cs.
2. Application failure errors will be displayed in the terminal. Next to the displayed error will be the origin of the error and the container it is displayed in. 

### Troubleshooting

If you have an error relating to your HTTP cert and you are on Windows, type:
1. ```cd tools\asc.utilities\scripts\Windows```
2. ```.\Export-DevCert.ps1```

Beyond this, if you encounter issues the main fix is:
1. ```docker compose down```
2. ```docker system prune -af``` (a bit dangerous if you host multiple docker containers, but was recommended to us!)
3. ```docker compose build```
4. ```docker compose up```

### Vulnerability & Failure Points
MoneytreeService.cs as the essential functions of the webpage call, at least indirectly, MoneytreeService.cs. 
