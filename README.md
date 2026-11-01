# CARTORA

CARTORA is a shopping-list frontend served by a Node.js/Express backend. The backend provides shopping-list, pantry, marketplace-store, and login APIs, and stores list data in a local JSON file.

## Requirements

- Node.js and npm
- Windows PowerShell (commands below use `npm.cmd` to avoid PowerShell script-policy issues)

## Run locally

1. Open a terminal in `cartora\cartora-backend` and install the backend dependencies:

   ```powershell
   cd .\cartora\cartora-backend
   npm.cmd install
   ```

   Dependency installation is only needed the first time.

2. Start the server:

   ```powershell
   npm.cmd start
   ```

3. Open [http://localhost:5000](http://localhost:5000). Express serves both frontend pages and the API. Keep the terminal running while using CARTORA.

To use VS Code's **Launch CARTORA** configuration, open the parent `shoppinglist manner` folder as the workspace and press **F5**. The debugger starts the backend and opens Chrome when the server is ready.

## Project layout

- `frontend\index.html` — shopping dashboard
- `frontend\marketplace.html` — connected store directory
- `frontend\app.js` and `frontend\style.css` — frontend behavior and styling
- `cartora-backend\server.js` — Express server and API routes
- `cartora-backend\data\db.json` — local shopping lists, pantry inventory, and stores

## API

All endpoints are served from `http://localhost:5000/api`.

| Method | Endpoint | Purpose |
| --- | --- | --- |
| `POST` | `/login` | Authenticate a configured user |
| `GET` | `/lists` | Get shopping lists |
| `POST` | `/lists/:id/items` | Add an item to a list |
| `PATCH` | `/lists/:id/items/:itemIndex` | Update an item's quantity or purchased status |
| `GET` | `/pantry` | Get pantry inventory |
| `GET` | `/stores` | Get marketplace stores |

Shopping-list changes are saved to `cartora-backend\data\db.json`. The login endpoint requires users to be configured in that file's `users` array; the included data does not contain users, so login rejects credentials until a user is added.

## Troubleshooting

- If the page cannot connect, confirm the backend terminal is still running and visit `http://localhost:5000`.
- If port 5000 is already in use, stop the other server process before starting CARTORA.
- Do not open the HTML file directly from the filesystem; use the Express URL so the API and frontend share the expected origin.
