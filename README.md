### Backend Project 2

| Group 5         |
| --------------- |
| Himani Tawade   |
| Kenny Tran      |
| Nicholas Girmes |
| Mike Ploythai   |

##### HOW TO RUN THE PROJECT

1. Copy the contents of our [nginx config file](https://github.com/himanitawade/Web-Back-End-Project2/blob/master/nginxconfig.txt) into a new file within `/etc/nginx/sites-enabled` called `nginxconfig`. Assuming the nginx service is already running, restart the service using `sudo service nginx restart`.

2. Initialize the databases within the project folder

   ```c
      // step 1. give the script permissions to execute
      chmod +x ./bin/init.sh

      // step 2. run the script
      ./bin/init.sh
   ```

3. Populate the word databases

   ```c
      python3 dbpop.py
   ```

4. Start the API

   ```c
      foreman start --formation user=1,game=3
      // NOTE: if there's an error upon running this where it doesn't recognize hypercorn, log out of Ubuntu and log back in.
   ```

5. Test all the endpoints using httpie
   - user
      - register account: `http POST http://user-vm.local.gd/registration username="yourusername" password="yourpassword"`
      - landing page: `http GET http://user-vm.local.gd/`
      - log in: `http --auth yourusername:yourpassword GET http://user-vm.local.gd/login`
   - game
      - create a new game: `http --auth yourusername:yourpassword POST http://game-vm.local.gd/newgame`
         - this will return a `gameid`
      - add a guess: `http --auth yourusername:yourpassword PUT http://game-vm.local.gd/addguess gameid="gameid" word="yourguess"`
      - display your active games: `http --auth yourusername:yourpassword GET http://game-vm.local.gd/allgames`
      - display the game status and status for one game: `http --auth yourusername:yourpassword GET http://game-vm.local.gd/onegame?id=gameid`
         - example: `.../onegame?id=b97fcbb0-6717-11ed-8689-e9ba279d21b6`
