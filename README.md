How to make a Chatt App in your webbrowser using nginx as webserver and MQTT as broker, both running on docker. On **windows**
1. Download docker here https://www.docker.com/products/docker-desktop/
2. Download th zip file
3. Delete the nginx-selfsigned.crt 
4. Delete the nginx-selfsigned.key
5. Make your own nginx-selfsigned.crt and nginx-selfsigned.key file
6. Download https://slproweb.com/products/Win32OpenSSL.html
  **Update PATH Environment Variable**: If OpenSSL is already installed but not included in the PATH environment variable, you can update the PATH to include the directory where OpenSSL is installed. The method for updating the PATH varies depending on your operating system.

 6.1    - **Windows**: 
        - Open Control Panel.
        - Go to System > Advanced system settings.
        - Click on the "Environment Variables" button.
        - In the System Variables section, select the "Path" variable and click "Edit".
        - Add the directory path where OpenSSL is installed (e.g., `C:\OpenSSL-Win64\bin`) to the list of paths.
        - Click OK to save the changes.

7. Use this command in the therminal in the C:\"yourPath"\docker\certificates file to make your own key and certificate with your own signature
   `openssl req -x509 -nodes -days 365 -newkey rsa:2048 -keyout nginx-selfsigned.key -out nginx-selfsigned.crt`
   and follow the instructions that are given
8. Create your own Authentication for your MQTT broker with your own name and password
9. Download the MQTT client tool https://mosquitto.org/download/
10. Do the same steps like in step 6.1 but then with the MQTT client tool
11. Use this command to create a new user, they will ask to make a password
   ` mosquitto_passwd -c C:\"yourPath"\docker\config\password.txt "yourName"`
12. Now your MQTT broker will be authenticated and your webserver will be encrypted(SSL)
13. Now it is time to start Docker and run MQTT and Nginx. You can do that with this command
   ` C:\"yourPath"\docker\ docker compose up`
14. In the docker desktop software you can check if your containers (MQTT, Nginx) is running it will be marked green if it is.
15. Open two seperate tabs in your browser and go to this link https://localhost/ 
16. if everything is working you can now chat with eachother using to diffrent tabs. (you can use diffrent webbrowsers for this)
17. **optional** If you want to check if your MQTT broker is authenticated you can download https://mqtt-explorer.com to check if you can connect to the your MQTT broker
    use this as your setting to connect your the broker
    Name: "Doesntmatter"
    Protocol: ws
    Host: localhost
    Port: 1884
    Basepath: ws
    Username: "name_used_in_step11"
    Password: "password_used_in_step11"

    if it works you should be connected to the broker and you should see the messages that are published in the chat.


