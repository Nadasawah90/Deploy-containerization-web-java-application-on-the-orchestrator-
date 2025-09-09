# Deploy-containerization-web-java-application-on-the-orchestrator-

## To  deploy the appplication on the orachestraor we need to make the following charts : 

          ┌───────────────┐
          │   Load Balancer│
          │      (LB)      │
          └───────▲────────┘
                  │
                  │
          ┌───────┴────────┐
          │   Deploy.App   │
          └───┬─────────┬──┘
              │         │
              ▼         ▼
     ┌────────────┐   ┌──────────┐
     │   Memcache │   │   RMQ    │
     │    (MC)    │   │ (Rabbit) │
     └───────┬────┘   └─────┬────┘
             │              │
             └──────┬───────┘
                    ▼
              ┌───────────┐
              │   DB      │
              │ (Database)│
              └───────────┘


## Prerequistes : 

1-  Four deployment for "APP , MC , RabbitMQ , DB" to deploy pods" containes " 

2-  1 service for Loadbalancing " with type loadbancing" ==> to can used external for users login 

3-  3 services for " Menmchashed , rabbitmq and application "  used type Cluster ip  == > to commuicate internal with each others .

==> creating yaml files as uploaded with my images uploades on docker hub repositories .

==> create namespace with name ns = myapp 

 kubectl create namespace myapp

 kubectl config set-context kubernetes-admin@kubernetes --namespace myapp

<img width="456" height="130" alt="image" src="https://github.com/user-attachments/assets/98ec2ee4-4ff3-41d8-83db-a987769c4396" />
==> create secret application file 

==> create only my deployment manually as i faced issue on this pod when created 

 kubectl create deployment vproapp   --image=nadahassan2024/webapp:v1   --port=8080   -n myapp

 kubectl apply -f app-service.yml -n myapp

  kubectl expose deployment vproapp   --name=vproapp-service   --type=NodePort   --port=8080   --target-port=8080   -n myapp

==> create config file for DB 

 create configmap vprodb-initdb   --from-file=db_backup.sql   -n myapp

as i copy this file from  source code to the same directory of the deployments yaml files .

==> kubectl deploy -f . 

<img width="1272" height="371" alt="image" src="https://github.com/user-attachments/assets/01d293f4-4306-422a-8cff-07d097ae3495" />

## Test environment 

 using ip of worker 1 as my pods deployed on it : 192.168.56.18 with internal port : 32229  

<img width="1808" height="865" alt="image" src="https://github.com/user-attachments/assets/3a58b872-4c64-4fa7-a9d2-670514037d98" />




