# Nillion-Verifier-Node-Run-Full-Guide

## Need Some Requirements for PC Users

1. Install Docker - https://www.docker.com/products/docker-desktop/

2. Install WSL - https://learn.microsoft.com/en-us/windows/wsl/install#install-wsl-command

1️⃣ Take Faucet

➡Claim Faucet - https://faucet.testnet.nillion.com/

➡Task Link - https://verifier.nillion.com/

  🍀For VPS (Additional Only for VPS Users to Download Docker)
```
sudo apt update -y
```
```
sudo apt install apt-transport-https ca-certificates curl software-properties-common -y
```
```
sudo curl -fsSL https://download.docker.com/linux/ubuntu/gpg | sudo gpg --dearmor -o /usr/share/keyrings/docker-archive-keyring.gpg
```
```
echo "deb [arch=$(dpkg --print-architecture) signed-by=/usr/share/keyrings/docker-archive-keyring.gpg] https://download.docker.com/linux/ubuntu $(lsb_release -cs) stable" | sudo tee /etc/apt/sources.list.d/docker.list > /dev/null
```
```
sudo apt update -y
```
```
apt-cache policy docker-ce
```
```
sudo apt install docker-ce -y
```
```
sudo usermod -aG docker ${USER}
su - ${USER}
groups
```

2️⃣ Check Docker Version
```
docker --version
```

3️⃣ Pull The Accuser Image
```
docker pull nillion/retailtoken-accuser:v1.0.0
```

4️⃣ Create A Directory
```
mkdir -p nillion/accuser
```

5️⃣ Initialise Docker (Save Key & Paste On web)
```
docker run -v ./nillion/accuser:/var/tmp nillion/retailtoken-accuser:v1.0.0 initialise
```

6️⃣ Now, Must Save Your Pvt key/Address/Pub key (Very Imp)
```
cat ~/nillion/accuser/credentials.json
```

7️⃣ Take Faucet Again, From New Accuser Wallet - https://faucet.testnet.nillion.com/

8️⃣ You Can Check,faucet from here/Check Block & Replace - https://testnet.nillion.explorers.guru/

9️⃣ Do This Step, After 5-10 minute And wait for syncing the latest block height
```
docker run -v ./nillion/accuser:/var/tmp nillion/retailtoken-accuser:v1.0.0 accuse --rpc-endpoint "https://nillion-testnet-rpc.polkachu.com/" --block-start 5306704
```

Note - Replace To The Latest Block Height (It’s Imp to minus -5 to 10 Block Height, just Replace To latest Block height)

Important Points
- If You Saw Registered = True(Means You did all the steps correctly), 
- If Coming False,Then Do from step1 Again With New wallet and wait Minimum 5-10 minute To do 9th step or 6th step from official page.
- And Secret Stores Found/Challenge Sent - 1 Or 3 Or 5 (means Your node running good and inc stores found as much u can).- More Stores Found = More Rewards

![Snapshot_3](https://github.com/user-attachments/assets/6e4e832e-70dd-476a-a734-42d6d61c355f)



🔶For Next Day Run This Command

#1 Open docker 1st 

#2
``` 
docker run -v ./nillion/accuser:/var/tmp nillion/retailtoken-accuser:v1.0.0 accuse --rpc-endpoint "https://testnet-nillion-rpc.lavenderfive.com" --block-start 5114183
```

# False Error Soluttion Guide

1️⃣ Check ur Address Id & Public Key
```
mkdir -p nillion/accuser && sudo docker run -v ./nillion/accuser:/var/tmp nillion/retailtoken-accuser:latest initialise
```

2️⃣ Check ur Nillion Container Id
```
docker ps -a 
```
3️⃣ Clean up ur old containers
```
docker rm containerid  
```
Note: Replace containerid With ur actual container Id

4️⃣ Now Create New KEPLR WALLET (Claim Faucet) & Connect in Nillion

➡Claim Faucet - https://faucet.testnet.nillion.com/

➡Task Link - https://verifier.nillion.com/

5️⃣ Pull The Accuser Image
```
docker pull nillion/retailtoken-accuser:v1.0.0
```

6️⃣ Initialise Docker (Save Key & Paste On web)
```
docker run -v ./nillion/accuser:/var/tmp nillion/retailtoken-accuser:v1.0.0 initialise
```

🔶Verify ur Address ID & PUB KEY

7️⃣ Now, Must Save Your Pvt key/Address/Pub key (Very Imp)
```
cat ~/nillion/accuser/credentials.json
```

8️⃣ Do This Step, After 5-10 minute And wait for syncing the latest block height
```
docker run -v ./nillion/accuser:/var/tmp nillion/retailtoken-accuser:v1.0.0 accuse --rpc-endpoint "https://nillion-testnet-rpc.polkachu.com/" --block-start 5306704
```

Explorer:- https://testnet.nillion.explorers.guru/

Note - Replace To The Latest Block Height according to ur Keplr Wallet Nillion address (It’s Imp to minus -5 to 10 Block Height, just Replace To latest Block height)

🔶For Next Day Run This Command

#1 Open docker 1st 

#2
``` 
docker run -v ./nillion/accuser:/var/tmp nillion/retailtoken-accuser:v1.0.0 accuse --rpc-endpoint "https://testnet-nillion-rpc.lavenderfive.com" --block-start 5114183
```

## Nillion Verifier Node Run V 1.0.1 Upgrade

**For Windows:** (PC users Docker User) 

```
docker run -v ./nillion/accuser:/var/tmp nillion/verifier:v1.0.1 verify --rpc-endpoint "https://testnet-nillion-rpc.lavenderfive.com"
```

1️⃣🅰️ Check ur Nillion Container Id
```
docker ps
```

1️⃣🅱️ Replace containerid With ur actual container Id to "Challenge Secret" Score
```
docker logs -f containerid | grep "challenged secret"
```

🔶For Next Day Run This Command

#1 Open docker 1st 

#2
``` 
docker run -v ./nillion/accuser:/var/tmp nillion/verifier:v1.0.1 verify --rpc-endpoint "https://testnet-nillion-rpc.lavenderfive.com"
```

**For VPS:**

1️⃣ Check ur Nillion Container Id
```
docker ps
```

2️⃣ Clean up ur old containers
```
docker rm containerid  
```
Note: Replace containerid With ur actual container Id

3️⃣ SAVE our Data
```
sudo find / -name credentials.json
```

Replace IPaddress is ur actual VPS IPaddress & Replace (C:\Users\somyakantdash\Downloads) With ur actual File Explorer Downloads in ur System
```
scp root@IPaddress:/root/nillion/accuser/credentials.json C:\Users\somyakantdash\Downloads
```

4️⃣ Upgrade to New Version 1.0.1 
```
sudo docker run -v ./nillion/accuser:/var/tmp nillion/verifier:v1.0.1 verify --rpc-endpoint "https://testnet-nillion-rpc.lavenderfive.com"
```

5️⃣ You can Check ur "Challenge Secret" Score

Check ur Nillion Container Id
```
docker ps
```

Replace containerid With ur actual container Id to check Scores
```
docker logs -f containerid | grep "challenged secret"
```
