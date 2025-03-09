<h1>TaskPro - FullStack App</h1>

<h2>Project Links</h2>
<ul>
  <li>
    <a href="https://taskpro-beryl.vercel.app">Live App</a>
  </li>
  <li>
    <a href="https://www.figma.com/design/fJF13s2UlxPIwTMcPVrSiz/TaskPro">Figma Design</a>
  </li>
  <li>
    <a href="https://taskpro-server-delta.vercel.app/api-docs/">API Documentation</a>
  </li>
</ul>

<h2>Description</h2>
<p>
  &nbsp;&nbsp;&nbsp;&nbsp;&nbsp;<b>TaskPro</b> is an intuitive Kanban board application designed to help users organize and manage their projects and tasks efficiently. Inspired by tools like Trello or Jira, TaskPro offers a seamless experience for tracking progress and staying productive, ensuring that deadlines are never missed.
</p>

<h2>Features</h2>
<ul>
  <li><b>User Authentication</b>: securely create an account and log in, or use Google authentication for quick access to your personal workspace.</li>
  <li><b>Password Recovery</b>: easily reset the account password by entering your email and receiving a reset link directly to your inbox.</li>
  <li><b>Customer Support</b>: get in touch with our support team by filling out a form with your comment and sending it directly for prompt assistance.</li>
  <li><b>Edit Profile</b>: customize your profile by updating your name, email, and optionally adding a profile picture.</li>
  <li><b>Select Theme</b>: choose from three available themes: light, dark, or violet, to personalize your application's appearance.</li>
  <li><b>Project Management</b>: create, update, and delete boards, which will be organized in a list for easy selection.</li>
  <li><b>Column Management</b>: configure each board by creating, updating, and deleting columns for optimal structure and making it easier to organize tasks into different categories.</li>
  <li><b>Card Management</b>: create, update, and delete cards within columns to represent tasks that include essential information such as name, description, priority, and deadline.</li>
  <li><b>Filtering</b>: select the priority level to display only those cards that match the chosen priority, making it easier to focus on the desired tasks.</li>
</ul>

<h2>Frontend</h2>
<ul>
  <li><b></b>: </li>
  <li><b></b>: </li>
  <li><b></b>: </li>
  <li><b></b>: </li>
  <li><b></b>: </li>
  <li><b></b>: </li>
  <li><b></b>: </li>
  <li><b></b>: </li>
  <li><b></b>: </li>
</ul>

<h2>Backend</h2>
<ul>
  <li><b>Technologies</b>: Node.js, Express, TypeScript</li>
  <li><b>Database</b>: MongoDB</li>
  <li><b>Object Data Modeling</b>: Mongoose</li>
  <li><b>Tools</b>: Postman, MongoDB Atlas, MongoDB Compass, Google Cloud Platform, Cloudinary</li>
  <li><b>Deploy</b>: Vercel</li>
  <li><b>Architecture</b>:
    <ul>
      <li><b>Module Type</b>: ECMAScript Modules (ESM)</li>
      <li><b>REST API</b></li>
      <li><b>Authentication</b>:
        <details>
          <summary><b>Methods</b></summary>
          <ul>   
            <li><b>Register / Login</b>: using user credentials</li>
            <li><b>Google OAuth</b>: using user Google account</li>
          </ul>
        </details>
        <ul>
          <li><b>Upon successful authentication</b>:
            <ul>
              <li><b>Token pair generation</b>:
                <ul>
                  <li><b>Access Token</b>: JSON Web Token (JWT) with a lifespan of 15 minutes</li>
                  <li><b>Refresh Token</b>: Random bytes token, created using crypto, securely stored in the database.</li>
                </ul>
              </li>
              <li><b>Server-Side Cookies Response</b>: 
                <ul>
                  <li><b>accessToken Cookie</b>: valid for 15 minutes.</li>
                  <li><b>refreshToken Cookie</b>: valid for 24 hours.</li>
                </ul>
              </li>
            </ul>
          </li>
        </ul>
      </li>
      <li><b>Authorization</b>: In order to access protected routes and private resources, requests must pass through an authorization layer represented by the jwtAuthMiddleware.</li>
      <li><b>Middleware</b>:
        <ul>
          <li><b>jwtAuthMiddleware</b>: 
            <details>
              <summary>Click to expand</summary>
              <ul>
                <li>Uses the "passport-jwt strategy" to decode the JSON Web Token (JWT) from the accessToken Cookie and search for the user in the database.</li>
                <li>If the accessToken is expired, the middleware attempts to use the refreshToken from the refreshToken Cookie, to find the user.</li>
                <li>If the user is found using the refreshToken, the token pair is regenerated, and access to the route is granted.</li>
                <li>If neither accessToken nor refreshToken are valid, access to the route is denied, and a 401 response is sent.</li>
              </ul>
            </details>
          </li>
          <li><b>googleAuthMiddleware</b>: 
            <details>
              <summary>Click to expand</summary>
              <ul>
                <li>Uses the "passport-google-oauth20 strategy" to handle user authentication through Google.</li>
                <li>Searches for the user in the database based on the information received from Google.</li>
                <li>If the user doesn't exist, it creates a new user with the provided details.</li>
              </ul>
            </details>
          </li>
          <li><b>cookieParserMiddleware</b>: Uses the "cookie-parser" library to parse cookies from client requests.</li>    
          <li><b>validateTokenMiddleware</b>: Checks the validation token, which can be used in two scenarios: Google authentication process and password reset procedure.</li>
          <li><b>multipartMiddleware</b>: Uses the "multer" library to manage multipart/form-data.</li>
          <li><b>corsMiddleware</b>: Uses the "cors" library to allow secure cross-origin requests exclusively from the client's application.</li>
          <li><b>loggerMiddleware</b>: Uses the "morgan" library to provide logging for HTTP requests and responses, enhancing debugging and monitoring processes.</li>
          <li><b>missingRouteMiddleware</b>: Handles missing routes by sending a 404 response with a "API route not found" message.</li>
          <li><b>errorMiddleware</b>: Captures all errors from the code and sends appropriate responses based on the error type.</li>
        </ul>
      </li>
    </ul>
  </li>

  <li><b>Other Details</b>:
    <ul>
      <li><b>Type Safety</b>: Ensured by TypeScript for a more reliable and maintainable codebase</li>
      <li><b>Linting</b>: ESLint Configuration for a clean and robust codebase</li>
      <li><b>Environment Variables</b>: Managed using Dotenv for secure configuration of sensitive information.</li>
      <li><b>Nodemon</b>: Automatically restarts the server upon detecting changes in source files, enhancing development experience.</li>
      <li><b>Bcrypt</b>: Provides secure hashing of passwords to protect user credentials.</li>
      <li><b>Cloudinary</b>: Ensures the secure upload and storage of user profile pictures in the cloud, generating a link to the resource.</li>
      <li><b>Nodemailer</b>: Sends confirmation emails to users after receiving support inquiries and handles sending password reset links.</li>
      <li><b>Swagger</b>: Used to document and test the API endpoints interactively.</li>
      <li><b>Data Validation</b>:
        <ul>
          <li><b>Request Validation</b>: Uses Joi library as the first layer to validate received data, ensuring it meets the required format and constraints.</li>
          <li><b>Database Validation</b>: Uses Mongoose Schema validation as the second layer to enforce data integrity and constraints when storing data in MongoDB.</li>
        </ul>
      </li>
    </ul>
  </li>
</ul>
