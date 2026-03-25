# &#x09;						**NESSUS SETUP GUIDE**



\############################################################🖥️ ✅ PART 1: PREPARE KALI LINUX######################################################################

🔹 Step 1: Update System



Open terminal:



sudo apt update \&\& sudo apt upgrade -y



\############################################################⬇️ ✅ PART 2: DOWNLOAD NESSUS######################################################################

🔹 Step 2: Download from Official Site



Go to:

👉 https://www.tenable.com/downloads/nessus



Choose:



Linux → Debian / Ubuntu (.deb)



👉 Or use terminal (example):



wget https://www.tenable.com/downloads/api/v2/pages/nessus/files/Nessus-10.x.x-debian10\_amd64.deb



\###########################################################📦 ✅ PART 3: INSTALL NESSUS##########################################################################

🔹 Step 3: Install Package



sudo dpkg -i Nessus-\*.deb



🔹 Step 4: Fix Dependencies (if error)



sudo apt --fix-broken install -y



\##########################################################🚀 ✅ PART 4: START NESSUS SERVICE######################################################################

🔹 Step 5: Start Service



sudo systemctl start nessusd



🔹 Step 6: Enable Auto Start



sudo systemctl enable nessusd



🔹 Step 7: Check Status



sudo systemctl status nessusd



👉 You should see:



active (running)



\###########################################################🌐 ✅ PART 5: ACCESS NESSUS WEB#######################################################################



🔹 Step 8: Open Browser



In Kali browser:



https://localhost:8834

⚠️ If Warning Appears



👉 Click:



Advanced → Accept Risk → Continue



\###########################################################🔑 ✅ PART 6: SETUP NESSUS###########################################################################



🔹 Step 9: Select Version



Choose:



Nessus Essentials (Free)



🔹 Step 10: Get Activation Code



Enter your email

Check inbox

Copy activation key



🔹 Step 11: Enter Activation Code



Paste key → Continue



🔹 Step 12: Create User



Example:



Username: admin

Password: strong password



🔄 Step 13: Plugin Download



👉 VERY IMPORTANT:



Takes 10–20 minutes

Do NOT close browser



\###########################################################🧪 ✅ PART 7: CREATE FIRST SCAN#######################################################################



🔹 Step 14: New Scan



Click:



New Scan → Basic Network Scan



🔹 Step 15: Configure Scan



Field			->			Value

Name			->			My Scan

Target			->			127.0.0.1



🔹 Step 16: Save \& Launch



Click:



Save

Launch ▶️



\############################################################📊 ✅ PART 8: VIEW RESULTS##########################################################################



After scan:



You’ll see:



Vulnerabilities Severity levels:

* Critical 🔴
* High 🟠
* Medium 🟡
* Low 🟢



\#############################################################📥 ✅ PART 9: EXPORT REPORT########################################################################



Click:



Export → PDF

