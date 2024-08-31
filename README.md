# Nillion-Verifier-Node-Run-Full-Guide

## Need Some Requirements for PC Users

1. Install Docker - https://www.docker.com/products/docker-desktop/

2. Install WSL - https://learn.microsoft.com/en-us/windows/wsl/install#install-wsl-command

1️⃣ Take Faucet

➡Claim Faucet - https://faucet.testnet.nillion.com/

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

6️⃣ Now, Must Save Your Pvt key/Address/Pub key(Very Imp)
```
cat ~/nillion/accuser/credentials.json
```

7️⃣ Take Faucet Again, From New Accuser Wallet - https://faucet.testnet.nillion.com/

8️⃣ You Can Check,faucet from here/Check Block & Replace - https://testnet.nillion.explorers.guru/

9️⃣ Do This Step, After 1hr And wait for syncing the latest block height
```
docker run -v ./nillion/accuser:/var/tmp nillion/retailtoken-accuser:v1.0.0 accuse --rpc-endpoint "https://testnet-nillion-rpc.lavenderfive.com" --block-start 5114183
```

NOte - Replace To The Latest Block Height (It’s Not Imp to minus -20 to 100 Block Height, just Replace To latest Block height)

Important Points
- If You Saw Registered = True(Means You did all the steps correctly), 
- If Coming False,Then Do from step1 Again With New wallet and wait Minimum 1hr To do 9th step or 6th step from official page.
- And Secret Stores Found/Challenge Sent - 1 Or 3 Or 5 (means Your node running good and inc stores found as much u can).- More Stores Found = More Rewards

🔶For Next Day Run This Command

#1 Open docker 1st 

#2
``` 
docker run -v ./nillion/accuser:/var/tmp nillion/retailtoken-accuser:v1.0.0 accuse --rpc-endpoint "https://testnet-nillion-rpc.lavenderfive.com" --block-start 5114183
```


