# Erpnext-with-Docker


Step 2 — System Update aur Docker Install Karo
bash
sudo apt update && sudo apt upgrade -y
Kya hota hai: Ubuntu ke saare packages update hote hain. -y flag automatically "yes" karta hai.

bash
curl -fsSL https://get.docker.com | sudo sh
Kya hota hai: Docker ka official convenience script download hoke install ho jaata hai.

bash
sudo usermod -aG docker ubuntu
newgrp docker
Kya hota hai: ubuntu user ko docker group mein add karta hai taaki sudo ke bina Docker commands chalein. newgrp current session mein group refresh karta hai.

Step 3 — Git aur Frappe Docker Clone Karo
bash
sudo apt install git -y
git clone https://github.com/frappe/frappe_docker
cd frappe_docker
Kya hota hai: Official Frappe Docker repository clone hoti hai. Iske andar saare compose files aur configs hain.

Step 4 — Quick Test Mode (Bina Domain ke — Port 8080 par)
Kyunki abhi aapke paas calcoerp.in domain nahi hai, pwd.yml ka use karo jo seedha IP:Port se kaam karta hai:

bash
docker compose -f pwd.yml up -d
Kya hota hai: -f pwd.yml ek simplified single-file setup hai testing ke liye. -d matlab detached mode — background mein run karega.

bash
docker compose -f pwd.yml logs -f create-site
Kya hota hai: Site create hone ki progress monitor karta hai. Isme 5-10 minute lag sakte hain. Jab "create-site container exits" dikhe tab complete hua.

Step 5 — ERPNext Access Karo
AWS Security Group mein Port 8080 allow karo, phir browser mein open karo:

text
http://YOUR_EC2_PUBLIC_IP:8080
