##  Lab Title
**Enterprise User Management & File Permissions Implementation on Kali Linux**

## Objective
To implement a complete user management and access control system for a simulated corporate environment (TechCorp Solutions) with two departments:

- **Marketing Department**: Individual private workspaces with isolated file access (700 permissions)
- **IT Department**: Collaborative workspace with shared group access (770 permissions)

  ## Tools Used
| Tool/Command | Purpose |
|--------------|---------|
| Kali Linux  | Primary operating system |
| `useradd` | Create user accounts |
| `groupadd` | Create department groups |
| `usermod` | Add users to groups |
| `chown` | Change file ownership |
| `chmod` | Set file permissions (700/770) |
| `mkdir` | Create directory structure |
| `getent` | Verify group memberships |
| `passwd`/`chpasswd` | Set user passwords |

##  Step-by-Step Process

### Marketing Department Setup
┌──(kali㉿Kali)-[~]
└─$ sudo mkdir -p /home/shared/marketing
[sudo] password for kali:

#### Create Group
┌──(kali㉿Kali)-[~]
└─$ sudo groupadd marketing

#### Create Individual Users
┌──(kali㉿Kali)-[~]
└─$ \
sudo useradd -m -s /bin/bash alice_m \
sudo useradd -m -s /bin/bash bob_m \
sudo useradd -m -s /bin/bash carol_m \
sudo useradd -m -s /bin/bash david_m \
sudo useradd -m -s /bin/bash emma_m

#### Create and Secure Personal Files
┌──(kali㉿Kali)-[~]
└─$ \
echo "alice_m:password123" | sudo chpasswd \
echo "bob_m:password123" | sudo chpasswd \
echo "carol_m:password123" | sudo chpasswd \
echo "david_m:password123" | sudo chpasswd \
echo "emma_m:password123" | sudo chpasswd

┌──(kali㉿Kali)-[~]
└─$ \
sudo usermod -aG marketing alice_m \
sudo usermod -aG marketing bob_m \
sudo usermod -aG marketing carol_m \
sudo usermod -aG marketing david_m \
sudo usermod -aG marketing emma_m

┌──(kali㉿Kali)-[~]
└─$ \
sudo touch /home/shared/marketing/alice_report.txt \                
sudo touch /home/shared/marketing/bob_report.txt \
sudo touch /home/shared/marketing/carol_report.txt \
sudo touch /home/shared/marketing/david_report.txt \
sudo touch /home/shared/marketing/emma_report.txt

┌──(kali㉿Kali)-[~]
└─$ 

sudo chown alice_m:marketing /home/shared/marketing/alice_report.txt \
sudo chown bob_m:marketing /home/shared/marketing/bob_report.txt \
sudo chown carol_m:marketing /home/shared/marketing/carol_report.txt \
sudo chown david_m:marketing /home/shared/marketing/david_report.txt \
sudo chown emma_m:marketing /home/shared/marketing/emma_report.txt

┌──(kali㉿Kali)-[~]
└─$ \
sudo chmod 700 /home/shared/marketing/alice_report.txt  \                
sudo chmod 700 /home/shared/marketing/bob_report.txt \
sudo chmod 700 /home/shared/marketing/carol_report.txt \
sudo chmod 700 /home/shared/marketing/david_report.txt \
sudo chmod 700 /home/shared/marketing/emma_report.txt

### IT Department Setup

#### Create IT group
┌──(kali㉿Kali)-[~]
└─$ sudo mkdir -p /home/shared/itdept                                        

#### Create IT users
┌──(kali㉿Kali)-[~]
└─$ sudo groupadd itdept                                                    

┌──(kali㉿Kali)-[~]
└─$ \
sudo useradd -m -s /bin/bash frank_it  \                                 
sudo useradd -m -s /bin/bash grace_it \
sudo useradd -m -s /bin/bash henry_it \
sudo useradd -m -s /bin/bash iris_it \
sudo useradd -m -s /bin/bash jack_it

┌──(kali㉿Kali)-[~]
└─$ \
echo "frank_it:password123" | sudo chpasswd \                           
echo "grace_it:password123" | sudo chpasswd \
echo "henry_it:password123" | sudo chpasswd \
echo "iris_it:password123" | sudo chpasswd \
echo "jack_it:password123" | sudo chpasswd

┌──(kali㉿Kali)-[~]
└─$ \
echo "frank_it:password123" | sudo chpasswd \                             
echo "grace_it:password123" | sudo chpasswd \
echo "henry_it:password123" | sudo chpasswd \
echo "iris_it:password123" | sudo chpasswd \
echo "jack_it:password123" | sudo chpasswd

#### Create shared file
┌──(kali㉿Kali)-[~]
└─$ sudo touch /home/shared/itdept/project_specs.txt   

#### Set group ownership and permissions (770)
┌──(kali㉿Kali)-[~]
└─$ sudo chown :itdept /home/shared/itdept/project_specs.txt                

┌──(kali㉿Kali)-[~]
└─$ sudo chmod 770 /home/shared/itdept/project_specs.txt




