![image](https://github.com/user-attachments/assets/6346252b-e8d1-4d70-9727-912b47d5a794)#Apache Airflow Download on Windows 

We need wsl environment in our cmd terminal 

command to install wsl :

wsl --install Ubuntu

Command to install the Apache Airflow :




Airflow is a data pipelining tool used for ETL operations. It is a hot requirement in the field of data related jobs. Airflow schedules task on the concept of graph thus, there will be a collection of related task called as a DAG (Directed Acyclic Graph).


Open the Ubuntu by typing the wsl command on the cmd 

Update system packages.
  sudo apt update
  sudo apt upgrade
  
Installing PIP.
  sudo apt-get install software-properties-common
  sudo apt-add-repository universe
  sudo apt-get update
  sudo apt-get install python-setuptools
  sudo apt install python3-pip
  
Run sudo nano /etc/wsl.conf then, insert the block below, save and exit with ctrl+s ctrl+x
[automount]
root = /
options = "metadata"
To setup a airflow home, first make sure where to install it. Run nano ~/.bashrc, insert the line below, save and exit with ctrl+s ctrl+x

export AIRFLOW_HOME=c/users/YOURNAME/airflowhome

Mine is, /mnt/c/users/Devanshu/airflowhome

Install virtualenv to create environment.
  sudo apt install python3-virtualenv
Create and activate environment.
  python3 -m venv airflow_env
  source airflow_env/bin/activate

Install airflow
  pip install apache-airflow
Make sure if Airflow is installed properly.
  airflow info
If no error pops up, proceed else install missing packages.

Initialize DB. By default, sqlite is used.
  airflow db init
If a error comes saying “Operation is not Permitted” make sure you have write access to the $AIRFLOW_HOME folder from WSL. So do something like below:

  sudo chmod -R 777 /mnt/c/Users/Dell/Documents/airflow/
Create airflow user.
airflow users create \
  --email johndoe@example.com \
  --firstname John \
  --lastname Doe \
  --password password123 \
  --role Admin \
  --username johndoe

Start webserver.
  airflow webserver
Go to URL http://localhost:8080/. If error pops up, check what is missing. Below page will be seen.

![image](https://github.com/user-attachments/assets/fef01a51-5579-424e-8b57-7c6a20a7adab)


Next page might be something like below.

![image](https://github.com/user-attachments/assets/06ecdd3f-acb4-42a0-a6cc-c07a7abe61cc)




In another terminal, enable virtual environment and then start scheduler.
new cmd , type wsl to enter the wsl 
then type ,
python3 -m venv airflow_env
source airflow_env/bin/activate
airflow scheduler

  
If an error about not finding a job table is shown, find a section in airflow.cfg file where [webserver] is written and make sure somethin like below is present:
[webserver]
rbac = True

create dags folder on your C drive airflowhome directory 
on that dags folder put your 
python file for the dag 

refresh the ui of airlfow on localhost:8080


  
