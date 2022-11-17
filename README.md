### Backend Project 2

| Group 5         |
| --------------- |
| Himani Tawade   |
| Kenny Tran      |
| Nicholas Girmes |
| Mike Ploythai   |

##### HOW TO RUN THE PROJECT

1. Set up NGINX using our custom [config file](https://github.com/himanitawade/Web-Back-End-Project2/blob/master/nginxconfig.txt)

2. Initialize the databases

   ```c
      // give the script permissions to execute
      chmod +x ./bin/init.sh

      // run the script
      ./bin/init.sh
   ```

3. Populate the word databases

   ```c
      python3 dbpop.py
   ```

4. Start the API

   ```c
      foreman start --formation game=4,user=1
   ```

5. Test all the endpoints

User service: [http://tuffix-vm/docs](http://tuffix-vm/docs)

Game service: [http://tuffix-vm:5100/docs](http://tuffix-vm:5100/docs)
