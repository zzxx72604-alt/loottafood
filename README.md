LOOTTAFOOD — HOW TO RUN (SIMPLE STEPS)
=======================================

>>> FOR THE PROFESSOR / TEAMMATE <<<
TEST THE WEBSITE AT:  http://localhost:4200
(First do the steps below: install, run, seed once.
 Admin login: john@gmail.com / 12345)

NEED FIRST (one time on a new computer):
- Node.js 18+
- MongoDB installed AND running
  (Windows: install MongoDB Community Server - runs as a service)
  (Linux:   install mongodb, then: sudo systemctl start mongod)

----------------------------------------
1) RUN THE APP
----------------------------------------
1. Open a terminal in the project folder:  loottafood
2. Type:   npm install
3. Type:   npm run dev
4. Wait until you see:   connect successfully

----------------------------------------
2) LOAD THE DATA (only the first time on a machine)
----------------------------------------
Open these in your browser once:
5. http://localhost:5000/api/users/seed     (should say: Seed Is Done!)
6. http://localhost:5000/api/foods/seed      (should say: Seed Is Done!)

----------------------------------------
3) USE THE WEBSITE
----------------------------------------
7. Open browser:   http://localhost:4200

----------------------------------------
4) LOGIN AS ADMIN
----------------------------------------
Email:     john@gmail.com
Password:  12345
Then click your name (top right) -> Dashboard  (the admin page)

----------------------------------------
MAKE YOUR OWN ACCOUNT AN ADMIN
----------------------------------------
A. Register a new account in the website (example: me@gmail.com)
B. Open browser:   http://localhost:5000/api/users/makeAdmin/me@gmail.com
C. Log out, then log in again.
D. Click your name (top right) -> Dashboard.

========================================
MANAGE USERS / DATABASE  (TERMINAL - works on Windows AND Linux)
========================================
Database:   mongodb://localhost:27017/foodmine

Open a terminal (Windows: Git Bash / PowerShell / CMD | Linux: Terminal):

1. Type:   mongosh
2. Then:   use foodmine
3. Then:   show collections

SEE ALL USERS:
      db.users.find({}, { name: 1, email: 1, isAdmin: 1 })
SEE FOODS / ORDERS:
      db.foods.find()
      db.orders.find()
DELETE ONE USER:
      db.users.deleteOne({ email: "their@email.com" })
DELETE MANY USERS:
      db.users.deleteMany({ email: { $in: ["a@gmail.com", "b@gmail.com"] } })
MAKE ADMIN (then log out + log in):
      db.users.updateOne({ email: "me@gmail.com" }, { $set: { isAdmin: true } })
Type:   exit   to leave mongosh.

If "mongosh" is not found:
- Windows: install "MongoDB Shell" from mongodb.com/try/download/shell
- Linux:   sudo apt-get install -y mongodb-mongosh

PASSWORDS are stored ENCRYPTED (bcrypt, one-way) - you cannot read the
original. If someone forgets it, RESET it (set a new one):
      http://localhost:5000/api/users/setPassword/EMAIL/NEWPASSWORD
      example: http://localhost:5000/api/users/setPassword/john@gmail.com/newpass123
      (or use Profile -> Change Password while logged in)

----------------------------------------
(OPTIONAL) browser shortcuts - may not always work
----------------------------------------
See users:    http://localhost:5000/api/users/list
Delete user:  http://localhost:5000/api/users/delete/THEIR@email.com
Make admin:   http://localhost:5000/api/users/makeAdmin/THEIR@email.com
If a browser link errors, use the mongosh terminal commands above instead.

----------------------------------------
NOTES
----------------------------------------
- A new computer starts EMPTY. You must seed once (steps 5 and 6).
- After the first time, just run:  npm run dev   then open localhost:4200
- Each computer has its OWN database (data is not shared between machines).
- Re-load the menu to defaults:  http://localhost:5000/api/foods/seed?force=true
- Re-create sample users (hashed):  http://localhost:5000/api/users/seed?force=true

----------------------------------------
(OPTIONAL) STOP / KILL THE SERVERS
----------------------------------------
Normal way: press Ctrl + C in the terminal, or close VS Code.

If a port stays stuck ("port already in use"), free both ports.
Easiest (Windows, Mac, Linux):
      npx kill-port 4200 5000
Windows:  taskkill /F /IM node.exe        (or Task Manager -> End Node.js)
Linux:    pkill -f node                    (or System Monitor -> Kill node)
Mac:      pkill -f node                    (or Activity Monitor -> Stop node)
