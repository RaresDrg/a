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
      <li><b>Authorization</b>: In order to access protected routes and private
