# travel-guide-project

## User Flow 
### This user flow covers the main functionalities and interactions a user can have on this application:

1. **User Registration and Authentication:**
   - User visits the website for the first time.
   - User clicks on the "Sign Up" or "Register" button.
   - User fills out the registration form with required details such as username, email, and password.
   - User submits the registration form.
   - If registration is successful, user is automatically logged in.
   - If registration fails (e.g., due to invalid input or existing email), appropriate error messages are displayed.

2. **User Login:**
   - User clicks on the "Login" button.
   - User enters their credentials (username/email and password) into the login form.
   - User submits the login form.
   - If login is successful, user is redirected to the dashboard or home page.
   - If login fails (e.g., due to incorrect credentials), appropriate error messages are displayed.

3. **Explore Attractions, Restaurants, and Hotels:**
   - User navigates to the "Explore" or "Discover" section of the website.
   - User enters the name of a city or selects a city from a dropdown menu.
   - User clicks on the "Search" button.
   - Application fetches data from external APIs for attractions, restaurants, and hotels based on the selected city.
   - User is presented with a list of attractions, restaurants, and hotels in the selected city.
   - User can filter or sort the list based on different criteria (e.g., category, rating).

4. **View Attraction Details:**
   - User clicks on an attraction from the list.
   - Application displays detailed information about the selected attraction, including name, description, location, and reviews.
   - User can view reviews from other users, leave their own review, or rate the attraction.

5. **View Restaurant Details:**
   - User clicks on a restaurant from the list.
   - Application displays detailed information about the selected restaurant, including name, description, location, and reviews.
   - User can view reviews from other users, leave their own review, or rate the restaurant.

6. **View Hotel Details:**
   - User clicks on a hotel from the list.
   - Application displays detailed information about the selected hotel, including name, description, location, and reviews.
   - User can view reviews from other users, leave their own review, or rate the hotel.

7. **Interact with Forum:**
   - User navigates to the "Forum" or "Community" section of the website.
   - User can view existing forum posts and comments from other users.
   - User can create a new forum post by clicking on the "Create Post" button and filling out the form.
   - User can comment on existing forum posts by clicking on the post and entering their comment in the comment section.

8. **User Profile Management:**
   - User can access their profile settings by clicking on their username or profile picture.
   - User can update their profile information such as username, email, and password.
   - User can view their activity history, including past forum posts, comments, and reviews.

9. **Logout:**
   - User clicks on the "Logout" button to log out of their account.
   - User is redirected to the homepage or login page.


  

### Endpoints: 

  

#### User Management: 

1. **User Registration**: 

   - `POST /api/users/register`: Create a new user. 

2. **User Authentication**: 

   - `POST /api/users/login`: Authenticate user and generate JWT token. 

3. **Profile Management**: 

   - `GET /api/users/profile`: Get user profile. 

   - `PUT /api/users/profile`: Update user profile. 

   - `PUT /api/users/password`: Update user password. 

4. **Admin Management**: 

   - `GET /api/users/admin`: Get list of admin users (admin access required). 

  

#### Reviews and Ratings: 

5. **Reviews**: 

   - `POST /api/reviews`: Create a new review. 

   - `GET /api/reviews/:id`: Get review by ID. 

   - `GET /api/reviews`: Get all reviews. 

   - `PUT /api/reviews/:id`: Update review. 

   - `DELETE /api/reviews/:id`: Delete review. 

6. **Ratings**: 

   - `POST /api/ratings`: Rate an entity (hotel, restaurant, attraction, etc.). 

   - `GET /api/ratings/:id`: Get rating by ID. 

   - `GET /api/ratings/entity/:entityId`: Get all ratings for a specific entity. 

   - `PUT /api/ratings/:id`: Update rating. 

   - `DELETE /api/ratings/:id`: Delete rating. 

  

#### Accommodation Booking: 

7. **Accommodations**: 

   - `POST /api/accommodations`: Create a new accommodation listing. 

   - `GET /api/accommodations/:id`: Get accommodation by ID. 

   - `GET /api/accommodations`: Get all accommodations. 

   - `PUT /api/accommodations/:id`: Update accommodation listing. 

   - `DELETE /api/accommodations/:id`: Delete accommodation listing. 

8. **Booking**: 

   - `POST /api/bookings`: Make a new booking. 

   - `GET /api/bookings/:id`: Get booking by ID. 

   - `GET /api/bookings/user/:userId`: Get all bookings for a user. 

   - `PUT /api/bookings/:id`: Update booking details. 

   - `DELETE /api/bookings/:id`: Cancel booking. 

  

#### Restaurant Listings and Reservations: 

9. **Restaurants**: 

   - `POST /api/restaurants`: Create a new restaurant listing. 

   - `GET /api/restaurants/:id`: Get restaurant by ID. 

   - `GET /api/restaurants`: Get all restaurants. 

   - `PUT /api/restaurants/:id`: Update restaurant listing. 

   - `DELETE /api/restaurants/:id`: Delete restaurant listing. 

10. **Reservation**: 

   - `POST /api/reservations`: Make a new restaurant reservation. 

   - `GET /api/reservations/:id`: Get reservation by ID. 

   - `GET /api/reservations/user/:userId`: Get all reservations for a user. 

   - `PUT /api/reservations/:id`: Update reservation details. 

   - `DELETE /api/reservations/:id`: Cancel reservation. 

  

#### Attractions and Activities: 

11. **Attractions**: 

   - `POST /api/attractions`: Create a new attraction listing. 

   - `GET /api/attractions/:id`: Get attraction by ID. 

   - `GET /api/attractions`: Get all attractions. 

   - `PUT /api/attractions/:id`: Update attraction listing. 

   - `DELETE /api/attractions/:id`: Delete attraction listing. 

12. **Activity Booking**: 

   - `POST /api/bookings/activities`: Make a new activity booking. 

   - `GET /api/bookings/activities/:id`: Get activity booking by ID. 

   - `GET /api/bookings/activities/user/:userId`: Get all activity bookings for a user. 

   - `PUT /api/bookings/activities/:id`: Update activity booking details. 

   - `DELETE /api/bookings/activities/:id`: Cancel activity booking. 

  

### Database Models: 

  

#### User Model: 

```javascript 

{ 

  username: String, 

  email: String, 

  password: String, 

  role: { type: String, enum: ['user', 'admin'], default: 'user' }, 

  // Additional fields for profile management (name, avatar, etc.) 

} 

``` 

  

#### Review Model: 

```javascript 

{ 

  user: { type: Schema.Types.ObjectId, ref: 'User' }, 

  entity: { type: Schema.Types.ObjectId, required: true }, 

  entityType: { type: String, required: true }, 

  rating: { type: Number, required: true }, 

  comment: String, 

  // Additional fields (date, helpful count, etc.) 

} 

``` 

  

#### Accommodation Model: 

```javascript 

{ 

  name: String, 

  location: String, 

  description: String, 

  // Additional fields (price, facilities, images, etc.) 

} 

``` 

  

#### Booking Model: 

```javascript 

{ 

  user: { type: Schema.Types.ObjectId, ref: 'User' }, 

  accommodation: { type: Schema.Types.ObjectId, ref: 'Accommodation' }, 

  // Additional fields (date, duration, total price, status, etc.) 

} 

``` 

  

#### Restaurant Model: 

```javascript 

{ 

  name: String, 

  location: String, 

  cuisine: String, 

  // Additional fields (price range, opening hours, menu, etc.) 

} 

``` 

  

#### Reservation Model: 

```javascript 

{ 

  user: { type: Schema.Types.ObjectId, ref: 'User' }, 

  restaurant: { type: Schema.Types.ObjectId, ref: 'Restaurant' }, 

  // Additional fields (date, time, number of guests, special requests, etc.) 

} 

``` 

  

#### Attraction Model: 

```javascript 

{ 

  name: String, 

  location: String, 

  description: String, 

  // Additional fields (ticket price, opening hours, images, etc.) 

} 

``` 

  

#### Activity Booking Model: 

```javascript 

{ 

  user: { type: Schema.Types.ObjectId, ref: 'User' }, 

  attraction: { type: Schema.Types.ObjectId, ref: 'Attraction' }, 

  // Additional fields (date, time, number of tickets, total price, etc.) 

} 

``` 

  

 
