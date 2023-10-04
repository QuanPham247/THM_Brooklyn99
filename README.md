# THM_Brooklyn99
Write-up for THM. 
Question 1: Retrieve user flag. 
- Look for open ports and services on the target
    nmap $IP
![image](https://github.com/QuanPham247/THM_Brooklyn99/assets/97132705/f660aab7-905f-43d9-bd48-de649352d37a)

-> FTP, SSH, and HTTP are open.
- FTP: Use anonymous to access the victim's FTP.
     ftp $IP
    ![image](https://github.com/QuanPham247/THM_Brooklyn99/assets/97132705/4715dd67-b674-4d8c-a181-bd5bc50f5e50)

  Retrieve the text file in the directory to our machine using the get command.  
    Here's its content: 

   ![image](https://github.com/QuanPham247/THM_Brooklyn99/assets/97132705/da925aa7-6511-4a00-9d5b-2a8b29d73f0f)
From here, we know that Jake might have a weak password so we're using Hydra to brute-force into the system using Jake's username. 
  Hydra -l jake -P /usr/share/wordlists/rockyou.txt $IP ssh
![image](https://github.com/QuanPham247/THM_Brooklyn99/assets/97132705/c70420b4-57bb-46dd-9f73-44a5e31bc770)

- Login: ssh jake@$IP
-  Find user flag:
-  find /home -type f -name "*.txt" 2>/dev/null
  ![image](https://github.com/QuanPham247/THM_Brooklyn99/assets/97132705/ad03ea48-ce58-4d59-9b18-80971937c4e3

- PrivEsc:
  + sudo -l
  ![image](https://github.com/QuanPham247/THM_Brooklyn99/assets/97132705/62aa805b-d0a6-4cbc-8e12-fa5f7d0b60d3)

  + GTFOBins:
  ![image](https://github.com/QuanPham247/THM_Brooklyn99/assets/97132705/e9e8cee6-c72c-4186-9837-d336c4d35a53)

- Find root flag:   
  + find /home -type f -name ".txt" 2>/dev/null
 ![image](https://github.com/QuanPham247/THM_Brooklyn99/assets/97132705/c1e6994e-6c53-4ef8-86dd-9884264eb4a1)


