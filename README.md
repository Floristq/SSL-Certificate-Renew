# Renew a SSL certificate

To renew a SSL certificate, you need to:

1. ssh into the server : ssh -i C:\Users\YangSong\Desktop\StagingLMS_PHP72.pem ec2-user@13.210.160.152

2. type command : history |grep cert 
to find past commands like: sudo certbot certonly --agree-tos --email support@mindatlas.com --manual --preferred-challenges=http -d arbuniversity.arb.com.au

3. copy the authorization content into your clipboard and save them elsewhere.

4. ssh into another server : ssh -i C:\Users\YangSong\Desktop\MainLMS4.pem ec2-user@52.65.176.4

5. get into the corresponding folder and use the following commands to add a folder and a file:

sudo mkdir .well-known

cd .well-known

sudo mkdir acme-challenge

cd acme-challenge

vi filename

copy content to the file

press esc on the keyboard

:wq

6. Back to the previous server and press enter. You should have the new certificate and key file generated successfully.

7. Get the new crt and key file from etc/letsencrypt/live/arbuniversity.arb.com.au

8. Upload them to a correct server at: /var/www/html/live/arb...

9. Go to the correct server and use ' sudo vim /etc/nginx/site-enabled/ ' to relink the file and the certificate

10. Reload the server with ' sudo service nginx reload '

My PHP version: 7.4.29
