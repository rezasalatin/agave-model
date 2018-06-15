FROM ubuntu

RUN apt-get update 
RUN apt-get install -y g++ make python3-pip python3 wget git make nodejs npm curl jq sshpass sudo ffmpeg
RUN pip3 install --upgrade pip
RUN pip3 install jupyter jupyterhub matplotlib==2.0.2 numpy notebook
RUN npm install -g configurable-http-proxy
RUN apt-get install -y vim

# Horrible hack to get the URL to display properly
RUN perl -p -i -e 's/0\.0\.0\.0/1.1.1.1/' /usr/local/lib/python3.5/dist-packages/notebook/notebookapp.py

RUN pip3 install ipywidgets
RUN jupyter nbextension enable --py widgetsnbextension
RUN pip3 install setvar 

COPY mkuser.sh mkuser.sh
COPY runuser.sh runuser.sh
RUN chmod +x runuser.sh

CMD bash mkuser.sh