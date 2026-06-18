LOOTTAFOOD — HOW TO RUN (SIMPLE STEPS)
=======================================

NEED FIRST (one time on a new computer):
- Node.js 18+
- MongoDB installed AND running

----------------------------------------
RUN THE APP
----------------------------------------
1. Open terminal in the project folder:  loottafood

2. Type:   npm install

3. Type:   npm run dev

4. Wait until you see:   connect successfully

----------------------------------------
LOAD THE DATA (only the first time)
----------------------------------------
5. Open browser, go to:   http://localhost:5000/api/users/seed
   (should say: Seed Is Done!)

6. Open browser, go to:   http://localhost:5000/api/foods/seed
   (should say: Seed Is Done!)

----------------------------------------
USE THE WEBSITE
----------------------------------------
7. Open browser, go to:   http://localhost:4200

----------------------------------------
LOGIN AS ADMIN
----------------------------------------
8. Click Login. Use:
      Email:     john@gmail.com
      Password:  12345

9. Click your name (top right) -> Dashboard  (that is the admin page)

----------------------------------------
MAKE YOUR OWN ACCOUNT AN ADMIN
----------------------------------------
A. Register a new account in the website (example: me@gmail.com)

B. Open browser, go to:
      http://localhost:5000/api/users/makeAdmin/me@gmail.com
   (use YOUR email)

C. Log out, then log in again.

D. Click your name (top right) -> Dashboard.

----------------------------------------
DELETE A USER (open in browser)
----------------------------------------
Go to:   http://localhost:5000/api/users/delete/THEIR@email.com
(use the email you want to remove)
- Shows: Deleted user: their@email.com

----------------------------------------
NOTES
----------------------------------------
- A new computer starts EMPTY. You must do steps 5 and 6 once.
- After the first time, just do steps 3 and 7.
- Each computer has its own data (not shared).
- To stop the servers: press Ctrl + C in the terminal, or close VS Code.
