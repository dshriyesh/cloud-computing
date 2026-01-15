# cloud-computing
cloud-computing assignments and learnings


# Static Webpage Hosting

In this assignment we learnt to host static webpage on ec2 instance 

Step 1:

1. For hosting our static web page we choose amazon ec2 instance

Static web page -> a web page made up of html, css and Javasript only providing very minimal interactivity.

<img width="1920" height="1080" alt="EC 2 service" src="https://github.com/user-attachments/assets/fceb432f-fbca-4706-864e-3fc34120039c" />


2. We launched an instance on aws ec2.

<img width="1920" height="1080" alt="Name of our Instance" src="https://github.com/user-attachments/assets/12cb5536-4505-4e46-8c4a-68d1d5d48780" />


4. We name our server and set Security configurations

<img width="1920" height="1080" alt="Setting Security configurations" src="https://github.com/user-attachments/assets/14cedd68-5f3d-4aae-b640-772bec7e01dc" />




SSH (Secure Shell) — For managing the server
To log in remotely to your EC2 instance  
To configure the server  
To install software (Apache, Nginx, updates, etc.)  
To upload/edit files  
To troubleshoot issues   

Key points:

Uses port 22  
Encrypted and secure  
Only for admin/developer access  
Not used by website visitors


🌐 HTTP — For serving the webpage

Why HTTP is needed:  
To allow users to access your website  
To serve HTML, CSS, JS, images  
Used by browsers like Chrome, Firefox, Edge  

Key points:  
Uses port 80  
Public-facing  
Used by end users  
Required to host a static website  

4. After launching our instance we connect to SSH Client for hosting so that we can control our server remotely (via or cmd).

<img width="1920" height="1080" alt="After creating an instance choose ssh for remote connection" src="https://github.com/user-attachments/assets/f2272884-9cf6-4c0f-b5f2-476a7e39ee34" />




## Hosting wbpage Remotely

step 1. Open CMD on windows

step 2. Connected to the ec2 instance remotely via commands given below:
cd C:\Users\Acer\OneDrive\Downloads -> location to my .pem file

step 3:
ssh -i C:\Users\Acer\Downloads\MyStaticServer.pem ubuntu@3.7.107.179 -> remote access to my ec2 server 

<img width="1920" height="1080" alt="Screenshot (55)" src="https://github.com/user-attachments/assets/d641a199-ba26-44d1-b466-a688c23f2f02" />


step4 : installing nginx web server
sudo apt install nginx -y -> installing nginx sever
nginx - reverse proxy web server which we used for hosting our website , it acts as a middleman that listens clients request and send responses from backend.

sudo systemctl start nginx ->Starts the Nginx web server right now

sudo systemctl enable nginx ->Ensures Nginx starts every time the server reboots

step 5: now navigate to web page to host

cd C:\Users\Acer\Desktop\weatherApp


scp -i C:\Users\Acer\Downloads\MyStaticServer.pem -r "C:\Users\Acer\OneDrive\Desktop\weather app" ubuntu@3.7.107.179:/home/ubuntu/ 
-> Securely copy my entire ‘weather app’ folder from my Windows PC to the home directory of the Ubuntu user on my EC2 server using my private key.

step 6 :
Move Website to Nginx Web Root (On EC2)

Now switch to your EC2 SSH terminal and run:

sudo rm -rf /var/www/html/* ->“Delete all existing website files from the Nginx web root.”

sudo mv /home/ubuntu/my-website/* /var/www/html/ ->Move my website files into Nginx’s web directory so it can serve them.

step 7:
Set Permissions (Very Important)  

sudo chown -R www-data:www-data /var/www/html  ->Make Nginx the owner of all website files.

sudo chmod -R 755 /var/www/html ->Allow Nginx and users to read website files, but prevent public modification

 On opening public ip address http://3.7.107.179 -> we can see our hosted webpage

 <img width="1920" height="1080" alt="Public IP Address" src="https://github.com/user-attachments/assets/de828202-609e-4490-902a-dffd913da93d" />






