
  

#  Google OAuth Authentication System

  

A complete Google OAuth authentication system built with **Node.js**, **Express**, and **MongoDB**. It allows users to log in with their Google accounts and provides session-based authentication with logout functionality and a minimal responsive frontend.

  

---

  

##  ✨ Features

- Google OAuth 2.0 authentication via Passport

- Session management with `express-session`

- MongoDB integration for persistent user storage

- CORS enabled for cross-origin requests

- Lightweight frontend with dynamic DOM updates

- Production-ready folder structure

  

---

  

##  📁 Project Structure

```

OAuth/

├── client/

│ ├── index.html

│ ├── script.js

│ └── style.css

└── server/

├── db/

│ ├── db.js

│ └── userModel.js

├── node_modules/

├── .env

├── index.js

├── package-lock.json

├── package.json

└── README.md

```

  

---

  

##  🚀 Quick Start

  

###  1) Clone and Install

```bash

git clone  https://github.com/Kunal-Rathore/Google_Login_Demo-Project-05.git

cd Google_Login_Demo-Project-05

npm install

```

  

###  2) Create `.env`

```text

PORT=3000

GOOGLE_CLIENT_ID=your_google_client_id

GOOGLE_CLIENT_SECRET=your_google_client_secret

MONGOO_URL=your_mongodb_connection_string

SESSION_SECRET=replace_with_a_long_random_string

```

  

>  **Note:**  `SESSION_SECRET` is required for `express-session`. Keep all secrets private.

  

###  3) Google OAuth Setup (Console)

1. Go to **Google Cloud Console** → APIs & Services → Credentials.

2. Create **OAuth 2.0 Client ID** (Application type: *Web application*).

3. Add **Authorized redirect URI**:

-  `http://localhost:3000/google/callback`

4. Copy the **Client ID** and **Client Secret** into your `.env`.

  

###  4) Run the Server

```bash

npm run  dev  # nodemon (recommended for development)

# or

npm start  # node index.js

```

  

###  5) Open the Frontend

Serve `index.html` (e.g., with VSCode Live Server or a simple static server) and visit:

```

http://localhost:5500

```

  

---

  

##  🔌 API Endpoints

  

| Method | Path | Description |

|-------:|--------------------|-------------------------------------------|

| GET | `/auth/google` | Initiates Google OAuth flow |

| GET | `/google/callback` | Google OAuth callback handler |

| GET | `/logout` | Logs out the current session |

| GET | `/isloggedin` | Returns auth status of current session |

  

###  Example (check login status)

```bash

curl -i  http://localhost:3000/isloggedin

```

  

###  Example (logout)

```bash

curl -i  http://localhost:3000/logout

```

  

---

  

##  🧩 Technologies

- Node.js, Express.js

- Passport.js (Google OAuth 2.0 Strategy)

- MongoDB + Mongoose

- express-session

- CORS

  

---

  

##  🛡️ Security Notes

- Always set a strong `SESSION_SECRET`.

- Use HTTPS and secure cookies in production (`cookie: { secure: true }` behind TLS).

- Do not commit `.env` or secrets to version control.

- Restrict OAuth credentials to your domains in production.

  

---

  

##  🐛 Troubleshooting

-  **Redirect URI mismatch**: Ensure the callback URL in Google Console exactly matches `/google/callback` with the correct host/port.

-  **CORS errors**: Confirm your frontend origin (e.g., `http://localhost:5500`) is allowed in your CORS config.

-  **Session not persisting**: Check that cookies are enabled and `SESSION_SECRET` is set. In production, set `trust proxy` and secure cookie options when behind a proxy.

-  **MongoDB connection issues**: Verify `MONGOO_URL` is correct and the database is reachable.

  

---

  

##  📜 Scripts

Common `package.json` entries (adjust as needed):

```json

{

"scripts": {

"start":  "node index.js",

"dev":  "nodemon index.js"

}

}

```

  

---

  

##  ✅ Status Check Flow

1. User clicks **Login with Google** → `/auth/google`

2. Google redirects to `/google/callback` → server verifies & creates session

3. Frontend calls `/isloggedin` to render UI state (welcome + logout)

4.  **Logout** → `/logout` destroys the session

  

---

  

##  📝 License

MIT