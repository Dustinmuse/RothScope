# Update as of Iteration 2
Client still wants it local as of the submission of Iteration 2.

## Requirements:
### Server:
Currently local as client doesn't want it hosted, but if you were to host it you would at a minimum:
1. Get a hosting service and SSH into it.
2. Install the dependencies needed, specifically Docker.
3. You would then clone your repo.
4. You can then run Docker.
5. Then you link your domain to your server and you should be good to go.
### File/Folder Location:
They should be grouped together as downloaded. Specifically, do not move files outside of the templates they reside in. Doing so would require alteration of other files.
### Start/Stop System:
In your terminal for your text editor, type 

```docker compose build```

```docker compose up```

It will then run on Docker Desktop, which you can stop by going into Docker Desktop and clicking the stop button on the container. 

<img width="1916" height="966" alt="stop_program" src="https://github.com/user-attachments/assets/a128fe42-9061-4f05-a0c2-b6d6130e0b29" />

### Error Finding
You have two main regions for finding application errors:
1. API call errors will be displayed upon hitting F12 on the webpage. From here, the majority will be in Spa.Template.Api/endpoints or Spa.Template.Infrastructure/MoneytreeService.cs.
2. Application failure errors will be displayed in the terminal. Next to the displayed error will be the origin of the error and the container it is displayed in. If the error is mixed in with several other lines, i.e. several things are running at once and it's hard to read the entire message, you can go into the container on your Docker Desktop and find it there. 

### Troubleshooting

If you have an error relating to your HTTP cert and you are on Windows, type:
1. ```cd tools\asc.utilities\scripts\Windows```
2. ```.\Export-DevCert.ps1```

General issues of programs, such as changing them and the editor getting upset, can be solved by:
1. ```docker compose down```
2. ```docker system prune -af``` (a bit dangerous if you host multiple docker containers, but was recommended to us!)
3. ```docker compose build```
4. ```docker compose up```

### Vulnerability & Failure Points
MoneytreeService.cs as the essential functions of the webpage call, at least indirectly, MoneytreeService.cs. 
