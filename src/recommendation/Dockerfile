FROM python:3.12.11-slim-bookworm AS base-venv

WORKDIR /usr/src/app

COPY ./requirements.txt ./requirements.txt

#upgrade the pip first
RUN pip install --upgrade pip
#create venv and download the req modules
#download required modules present in requirement.txt
RUN python -m venv venv && venv/bin/pip install -r requirements.txt

FROM python:3.12.11-slim-bookworm 

WORKDIR /usr/src/app

#copy the venv from base-env
COPY --from=base-venv /usr/src/app/venv/ /venv/

#copy all .py files
COPY *.py .

ENV AD_PORT=9099

EXPOSE ${AD_PORT}

#run main py files from venv python
ENTRYPOINT ["/venv/bin/python","recommendation_server.py"]
 


 
