# Hi there, I'm Rao 👋

# 📌 ModelSim Installation Guide for Ubuntu 22.04.5 (AMD64)

## Prerequisites

Ensure you have **ModelSimSetup-\*-linux** in your home directory before proceeding.

## #1 Update Your System

```bash
sudo apt update && sudo apt upgrade
#2 Run the Installer
bash
Copy
Edit
./ModelSimSetup-*-linux.run
#3 Modify vco Script Permissions
bash
Copy
Edit
chmod u+w ~/intelFPGA/*.*/modelsim_ase/vco
#4 Backup the vco File
bash
Copy
Edit
(cd ~/intelFPGA/*.*/modelsim_ase/ && cp vco vco_original)
#5 Edit vco Script
bash
Copy
Edit
sed -i 's/linux\_rh[[:digit:]]\+/linux/g' ~/intelFPGA/*.*/modelsim_ase/vco
sed -i 's/MTI_VCO_MODE:-""/MTI_VCO_MODE:-"32"/g' ~/intelFPGA/*.*/modelsim_ase/vco
sed -i '/dir=`dirname "$arg0"`/a export LD_LIBRARY_PATH=${dir}/lib32' ~/intelFPGA/*.*/modelsim_ase/vco
#6 Verify Changes
bash
Copy
Edit
diff ~/intelFPGA/*.*/modelsim_ase/vco ~/intelFPGA/*.*/modelsim_ase/vco_original
#7 Install Required Libraries
bash
Copy
Edit
sudo dpkg --add-architecture i386
sudo apt update
sudo apt install build-essential gcc-multilib g++-multilib lib32z1 \
    lib32stdc++6 lib32gcc-s1 libxt6:i386 libxtst6:i386 expat:i386 \
    fontconfig:i386 libfreetype6:i386 libexpat1:i386 libc6:i386 \
    libgtk-3-0:i386 libcanberra0:i386 libice6:i386 libsm6:i386 \
    libncurses5:i386 zlib1g:i386 libx11-6:i386 libxau6:i386 \
    libxdmcp6:i386 libxext6:i386 libxft2:i386 libxrender1:i386
#8 Run ModelSim
bash
Copy
Edit
cd ~/intelFPGA/*.*/modelsim_ase/bin/
./vsim

