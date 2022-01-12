
## Inside dockerfile

ENV - set env var
ENV PORT=80

EXPOSE $PORT

EXPOSE command opens port 
EXPOSE 80 - opens port 80
EXPOSE $PORT - same as EXPOSE 80

FROM ngina:lastest - FROM command gets an image 
LABEL author="Delwar" - LABEL command is used to add a label (create a author label)

COPY <scr><dest> - same as cp command
WORKDIR <dest> - same as cd command

RUN command is used to run shell commands
RUN apt update -y
CDM is similar to RUN (use RUN instead of  CDM)
CDM["apt","update"]
VOLUME -used to amount volumes


![image](https://user-images.githubusercontent.com/94615905/149126736-248bb74e-bdf7-4204-9495-2ac13b8c1d95.png)

