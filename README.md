##  Lessons
1. Introduciton to the course
2. Install development tools
3. Create Angular App
   1. Create project's folder
   2. Install @angular/cli
   3. Create App as frontend

4. Add Header
   1. Generate Component
   2. Add Html
   3. Add CSS

5. List Foods
    1. Create Food model
    2. Create data.ts
       1. Add sample foods
    3. Add images to assets
    4. Create Food service
    5. Create Home component
       1. Add ts
       2. Add html
       3. Add css

6. Search
   1. Add method to Food service
   2. Add search route
   3. Show search result in Home component
   4. Generate search component
      1. Add to home component
      2. Add ts
      3. Add html
      4. Add css
   
7. Tags Bar
   1. Create Tag model
   2. Add sample tags to data.ts
   3. Food service
      1. Add get all tags method
      2. Add get all foods by tag method
   4. Add tags route
   5. Show tag result in Home component
   6. Generate Tags component
      1. Add to home component
      2. Add ts
      3. Add html
      4. Add css

8. Food Page
   1. Add method to food service
   2. Generate Food Page component
      1. Add Route
      2. Add ts
      3. Add html
      4. Add css

9. Cart Page
   1. Create CartItem Model
   2. Create Cart Model
   3. Generate Cart service
   4. Add to Cart Button in Food Page
   5. Generate Cart page component
      1. Add Route
      2. Add ts
      3. Add html
      4. Add css

10. Not Found!
    1. Generate Component
       1. Add ts
       2. Add html
       3. Add css
    2. Add To Pages
       1. Home Page
       2. Food Page
       3. Cart Page

11. Connect To Backend
    1.  Create backend folder
    2.  npm init
    3.  npm install typescript
    4.  Create tsconfig.json
    5.  Create .gitignore
    6.  Copy data.ts to backend/src
    7.  npm install express cors
    8.  Create server.ts
        1. install @types
        2. Add Apis
    9.  npm install nodemon ts-node --save-dev
    10. Add urs.ts to frontend
    11. Add HttpClient module
    12. Update food service

12. Login Page
    1.  Generate Component
        1.  Add to routes
        2.  Add ts 
        3.  Add html
            1.  Import Reactive Forms Module
        4.  Add Css
    2.  Add Login Api
        1.  Use json
        2.  Add jsonwebtoken
        3.  Test Using Postman
    
    3.  Generate User Service
        1.  Generate User model
        2.  Add User Subject
        3.  Add Login Method   
            1.  Add User Urls
            2.  Generate IUserLogin interface
            3.  Add ngx-toastr
                1.  Import Module
                2.  Import BrowserAnimationsModule
                3.  Add styles in angular.json
            4.  Add to Header
        1. Add Local Storage methods
        2. Add Logout Method
           1. Add to Header


13. Make Components For Login Page
    1. Input Container
    2. Input Validation
    3. Text Input
    4. Default Button

14. Connect Login API To MongoDB Atlas
    1. Moving Apis into routers
    2. Create MongoDB Atlas
    3. Create .env file
    4. Install
       1. mongoose
       2. dotenv
       3. bcryptjs
       4. express-async-handler
    5. Connect to MongoDB Atlas
    6. Use MongoDB instead of data.ts in apis


15. Register User
    1.  Add Register api
    2.  Add Register service method
    3.  Add Register link 
    4.  Add Register Component


16. Loading!
    1.  Add Image 
    2.  Add Component
    3.  Add Service
    4.  Add Interceptor




17. Checkout Page
    1.  Create Order Model
    2.  Create Checkout Page Component
        1.  Add To Router   
    3.  Add User to User Service 
    4.  Add Cart to Cart Service 
    5.  Create Order Items List Component
    6.  Adding Map To The Checkout Page
        1.  Add Leaflet npm package
            1.  Add @types/leaflet
            2.  Add Css to angular.json
        2.  Add AddressLatLng to Order Model
        3.  Create Map component
            1.  Add to checkout page
            2.  Add TS
                1.  Change app-map selector to map
            3.  Add Html
            4.  Add CSS
        4.  Add Auth Guard
    7.  Save Order
        1. Add Order Model
        2. Add Order Status Enum
        3. Add Auth Middleware
        4. Add Order Router
           1. Add create API
        5. Add Order Urls to urls.ts
        7. Add Order Service
           1. Add create Method
        8. Add Auth Interceptor

18. Payment Page
    1. Generate Component
    2. Add 'getOrderForCurrentUser' api 
    3. Add Order Service method
    4. Connect Component to Service
    5. Make the map component readonly

19. Adding Paypal
    1. Generate Component
       1. Add to payment page
    2. Get Paypal client Id
    3. Add Paypal JS to index.html
    4. Set up Paypal button
    5. Add Pay api to order router   
    6. Get Paypal sandbox account

20. Order Track Page
    1.  Generate Component
        1.  Add to routes
    2.  Add API
        1.  Add to urls.ts
    3.  Add method to order.service
    4.  Add HTML
    5.  Add CSS

21. Deploy On Heroku
    1.  OutputPath in angular.json
    2.  package.json
        1.  frontend
        2.  backend
        3.  root
    3.  BASE_URL in urls.ts
    4.  Public folder config in server.ts
    5.  Run commands
    6.  Add built folder to .gitignore
    7.  Commit and Push

22. Updating Packages (Optional)
    1.  Install npm-check-upates as a global package
    2.  Run ncu -u in the frontend folder
    3.  Downgrade typescript to version ~4.8.2
    4.  Run npm install --force
    5.  Run npm start
    6.  Run ncu -u in the backend folder
    7.  Run npm install
    8.  Run npm start


# ===== Custom Extensions (LoottaFood) =====
# The lessons below are customizations made on top of the base course project.

23. Rebrand to LoottaFood
    1.  Change header logo text to "LoottaFood"
    2.  Change browser tab title in index.html
    3.  Update search box placeholder

24. Add Drinks to the Menu
    1.  Add 6 drinks to data.ts (frontend + backend)
        1.  Caramel Frappuccino, Iced Matcha Latte, Strawberry Milk,
            Hibiscus Iced Tea, Ube Taro Milk, Ube Coconut Latte
    2.  Add images to assets (food-7 .. food-12.jpg)
    3.  Add new tags: Drinks, Cold, Coffee, Tea
    4.  Make the seed route reload data with ?force=true

25. Dark Mode
    1.  Create Theme service (toggle + remember in localStorage)
    2.  Add 🌙 / ☀️ toggle button in the header
    3.  Add body.dark-theme styles in styles.css

26. Favorites
    1.  Create Prefs service (favorites in localStorage)
    2.  Make the heart clickable on cards & food page
    3.  Create Favorites page + route + header link

27. Interactive Ratings
    1.  Make the star-rating component editable (hover + click)
    2.  Save the user's rating in localStorage (Prefs service)
    3.  Blend the user's rating into the displayed stars

28. Cambodian Payment Methods (replace PayPal)
    1.  Create payment-options component
    2.  Methods: ABA, KHQR, Wing, WeChat, Alipay, ACLEDA
    3.  Show a QR / confirm screen, then mark order paid (existing /pay api)

29. Sticky Glass Header & Auto-hide Search
    1.  Make the header sticky (always visible)
    2.  Make the search a sticky bar that hides on scroll-down, shows on scroll-up
    3.  iOS-style frosted glass (backdrop-filter blur)

30. Profile Page (edit name / email / password)
    1.  Add updateProfile + changePassword apis (auth protected)
    2.  Add service methods + urls
    3.  Create Profile page component + route (AuthGuard)

31. Orders History
    1.  Add list all orders api (current user)
    2.  Create Orders page + route + header link
    3.  Re-order (add items back to cart)
    4.  Soft-delete + Undo (archived flag + /restore api)

32. Confirm Dialog
    1.  Create Confirm service (promise-based)
    2.  Create confirm-dialog component (added to app root)
    3.  Use it for delete order, delete item, and logout

33. Admin Dashboard (menu CRUD)
    1.  Add admin middleware + create/update/delete food apis
    2.  Create Admin guard
    3.  Add FoodService create/update/delete methods
    4.  Create admin-dashboard component + route (AdminGuard)
    5.  Image field with live preview + upload (data URL)
    6.  Dev helper api: /api/users/makeAdmin/:email

34. Discounts & Sorting / Filter
    1.  Add discount + sortOrder fields to food model
    2.  Admin: discount input, price sort, "discounted only" filter
    3.  Customer: sale price + struck original + discount badge
    4.  Customer home: sort (price/rating) + "On sale only"

35. Drag-and-drop Reorder
    1.  Install @angular/cdk
    2.  Add DragDropModule + drag handle on admin rows
    3.  Add /reorder api; order reflects on the customer menu

36. iOS-style Glass UI & Gradient Background
    1.  Brand-tinted gradient background (light + dark)
    2.  Frosted-glass tags + custom glass-select dropdown
    3.  White font on glass in dark mode

37. "You may also like"
    1.  Food page loads all foods, shuffles, shows 4 random items
    2.  Clicking one opens it and reshuffles

38. Card Hover/Hold Description Overlay
    1.  Dark overlay fades in over the card (no layout push / no lag)
    2.  Price turns white while overlay shows
    3.  Price moved to normal flow so origin tags never overlap it

39. Mobile / Tablet Responsive + ScanMe
    1.  Media queries: header wraps, 2-up cards on phones
    2.  Desktop = tablet card sizing
    3.  Header "📷 ScanMe" popup shows assets/scan-qr.jpg (or .png)

40. Run / Host / Test Guide
    1.  See RUN-GUIDE.md in the project root
    2.  Local run, seeding, admin account
    3.  Wi-Fi/LAN testing on phones (scan-to-order)
    4.  Production build & deploy notes

41. Admin Deliveries + Cart Polish
    1.  Add DELIVERED status to OrderStatus enum
    2.  Admin order apis (auth + admin)
        1.  GET /api/orders/all  (all orders)
        2.  PUT /api/orders/complete/:id  (mark delivered)
    3.  Add getAllOrders + completeOrder to order service
    4.  Create manage-orders component + route (AdminGuard)
        1.  Lists every order with customer, address, items, total, status
        2.  "Mark Delivered" button (for staff / delivery)
    5.  Link from Admin Dashboard ("Manage Orders")
    6.  Fix cart item name color in dark mode

42. Order Notifications (bell)
    1.  Create Notification service (polls every ~20s)
        1.  Add 'skip-loading' header so polls don't flash the spinner
    2.  Admin: badge = paid orders waiting (request from customer)
    3.  Customer: badge = orders that became delivered/completed
    4.  Add 🔔 bell + dropdown to the header (seen-state per browser)
    5.  RUN-GUIDE: notifications + how to delete user/customer data

43. One-command Run + Wi-Fi Testing
    1.  Root package.json: add "concurrently" dev dependency
    2.  Update "dev" script to run backend + frontend together
        1.  Frontend served on 0.0.0.0 (reachable by phones)
    3.  Run with: npm install (root) then npm run dev
    4.  Note: Express backend already binds all interfaces (no flag needed)
    5.  Root postinstall: auto-installs frontend + backend on root npm install
    6.  Logo click scrolls to top (and routes home)

44. Single-port Proxy + ngrok (hide IP)
    1.  Add proxy.conf.json (frontend /api -> backend :5000)
    2.  Set frontend BASE_URL to '' (relative, same-origin via proxy)
    3.  angular.json serve: proxyConfig; dev script: --disable-host-check
    4.  Result: no CORS / no IP edits — works on localhost, LAN, and ngrok
    5.  Hide IP: run "ngrok http 4200", point the QR at the ngrok URL
    6.  RUN-GUIDE section 6 updated (LAN + ngrok + table QR)