<h2 align=center>Gensyn Testnet Node Guide</h2>

## 💻 System Requirements

| Requirement                         | Details                                                     |
|-------------------------------------|-------------------------------------------------------------|
| **CPU Architecture**                | `arm64` or `amd64`                                          |
| **Recommended RAM**                 | 24 GB                                                       |
| **CUDA Devices (Recommended)**      | `RTX 3090`, `RTX 4070`, `RTX 4090`, `A100`, `H100`          |
| **Python Version**                  | Python >= 3.10 (For Mac, you may need to upgrade)           |


## 📥 Installation

1. **Install `sudo`**
```bash
apt update && apt install -y sudo
```
2. **Install other dependencies**
```bash
sudo apt update && sudo apt install -y python3 python3-venv python3-pip curl wget screen git lsof nano unzip
```
3. **Install Node.js and npm**  
```bash
curl -sSL https://raw.githubusercontent.com/zunxbt/installation/main/node.sh | bash
```
4. **Clone this repository**
```bash
cd $HOME && [ -d rl-swarm ] && rm -rf rl-swarm; git clone https://github.com/zunxbt/rl-swarm.git && cd rl-swarm
```
5. **Create a `screen` session**
```bash
screen -S gensyn
```
6. **Run the swarm**
```bash
python3 -m venv .venv && . .venv/bin/activate && ./run_rl_swarm.sh
```
- It will ask some questions, you should send response properly
- ```Would you like to push models you train in the RL swarm to the Hugging Face Hub? [y/N]``` : Write `N`
- When you will see interface like this, you can detach from this screen session

![Screenshot 2025-04-01 061641](https://github.com/user-attachments/assets/b5ed9645-16a2-4911-8a73-97e21fdde274)

7. **Detach from `screen session`**
- Use `Ctrl + A` and then press `D` to detach from this screen session.

 ## 🔄️ Back up `swarm.pem`
After running the Gensyn node, it is essential to back up the swarm.pem file from your remote server (GPU or VPS) to your local PC. If you lose this file, your contribution will also be lost. Some GPU servers do not support SCP or SFTP, so I will provide distinct methods — one specifically for GPU servers and another for VPS.

### 1. Back up `swarm.pem` from GPU server to local PC
- For this, you must need to connect to GPU server using [SSH](https://github.com/zunxbt/gensyn-testnet?tab=readme-ov-file#-connect-via-ssh) (Recommened to do these stuffs on Command Prompt or Power Shell)
- Now exit from this GPU server using this command
```
exit
```
- Now replace `SSH-COMMAND` in the below command with the command which your received from provider, then replace `YOUR-PC-PATH` where you want to download this swarm.pem file and then execute it on your Command prompt or Power shell
```
SSH-COMMAND "cat ~/rl-swarm/swarm.pem" > "YOUR-PC-PATH\swarm.pem"
```
- In my case, this command looks like this :
```
ssh -p 69 root@69.69.69.69 "cat ~/rl-swarm/swarm.pem" > "C:\Users\USER\Downloads\swarm.pem"
```
- Done, your `swarm.pem` file is now saved on your local system
