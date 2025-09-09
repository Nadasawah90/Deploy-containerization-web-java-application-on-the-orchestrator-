# Deploy-containerization-web-java-application-on-the-orchestrator-

To  deploy the appplication on the orachestraor we need to make the following charts : 

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


Prerequistes : 

1-  Four deployment for "APP , MC , RabbitMQ , DB" to deploy pods" containes " 

2-  1 service for Loadbalancing " with type loadbancing" ==> to can used external for users login 

3-  3 services for " Menmchashed , rabbitmq and application "  used type Cluster ip  == > to commuicate internal with each others .

==> creating yaml files as uploaded with my images uploades on docker hub repositories .

==> create namespace with name ns = myapp 

<img width="422" height="196" alt="image" src="https://github.com/user-attachments/assets/136c3ccf-9694-4b58-beeb-7462930738b1" />



==> kubectl deploy -f . 

<img width="1877" height="548" alt="image" src="https://github.com/user-attachments/assets/ba63a0b3-a3a1-47ec-958a-0817e1f459f0" />

==> Test environment 
 using ip of worker 1 as my pods deployed on it : 192.168.56.18 with internal port : 32229  

<img width="1433" height="690" alt="image" src="https://github.com/user-attachments/assets/ae40e8e5-ec57-4db6-9500-a40fd0b21847" />


<img width="1842" height="973" alt="image" src="https://github.com/user-attachments/assets/12a0191e-95e4-4d56-9dac-df40ef3b4d7f" />
