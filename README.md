### Twitter-Clone
**Hosted Link**: https://main--stupendous-kringle-eb015e.netlify.app/

  **State Management (Redux Toolkit):** The application follows the DUCKS file pattern and utilizes Redux Toolkit for global state management. Most state, including Posts and Users in normalized form, is stored in the Redux store. The createAdapter feature simplifies access to these entities through CRUD methods and selectors.

  **Authentication (Passport):** Passport's local strategy is employed for user authentication. Sessions are managed server-side using httpOnly cookies. Additionally, authentication state is stored in sessionStorage for quicker reloads while asynchronously checking session validity.

  **Search (MongoDB Native):** The application supports text-based searching within posts, hashtags (by prefixing queries with '#'), and users/user mentions (by prefixing queries with '@'). MongoDB's search index queries power the search functionality.

  **Notifications (Native and Push):** Users can receive push notifications for various interactions like replies, likes, and follows. Recent notifications are accessible from the Notifications page.

  **Trends and User Suggestions:** Trends are generated based on hashtags with recent and frequent posts, displayed in the sidebar or on the explore page. User suggestions, found in the 'Who to follow' banner on the sidebar, provide recommendations for users to connect with.

  **Composing Posts:** Posts are primarily text-based but support features like 'Reply Posts' and 'Quote Posts' with previews. Posts are parsed for hashtags and usernames, which are clickable. An emoji picker (emoji-mart) is available for convenient emoji insertion, and link previews are displayed using react-tiny-link.

  **Styling (Bootstrap):** The application's styling is achieved using Bootstrap, with customization involving Sass variables, class extension, and custom classes. The design is responsive, ensuring a pleasant user experience on various devices.

## Things Used:

- `Express`: For server.

- `MongoDB`: For database and a full text search!

- `Mongoose`: as *Mongo* driver and for model and schema validation.

- `Passport`: With Local strategy for authentication.

- `Bcryptjs`: For password hashing.

- `Cookies/express-session/connect-mongo`: For session management and storage

## File Structure:

- `app.js` - main express app file.
- `passport.js` auth strategy and serialization.
- `models/`
  - contains `Mongoose` schema's and models for database collections.
- `routes/`
  - `auth.js` - contains authentication related routes, like `/auth/login`, `/auth/logout`, etc.
  - `api.js` - contains all other app routes.
- `controllers/`
  - contains functions to interact with database and return data to routes.
- `serializers/`
  - contains functions to serialize data returned from database to be sent to client.
- `utils/`
  - contains some utility functions.

# For Deploying:

You will need to set some environment variable, below is the example `.env` file.

```bash
MONGO_URL=<link to atlas address or wherever your mongoDB is deployed, defaults to 'mongodb://localhost/test'>
SESSION_SECRET=<passed to session middleware, defaults to 'my shitty session secret'>

- `npm install` to install dependencies.
- `npm run dev` to start development server with `nodemon`.
- `npm start` to start production server.
