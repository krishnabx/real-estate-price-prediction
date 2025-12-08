# Repo-specific Copilot instructions — BHP (Home Price Prediction)

Purpose: Give AI coding agents the minimal, concrete facts needed to be productive in this repository.

Quick architecture
- Backend: small Flask service at `server/server.py` that exposes two endpoints:
  - `GET /get_location_names` => returns JSON `{ "locations": [...] }` via `util.get_location_names()`
  - `GET|POST /predict_home_price` => expects form fields `total_sqft`, `location`, `bhk`, `bath` and returns `{ "estimated_price": ... }` produced by `util.get_estimated_price(...)`
  - Startup: `server/server.py` calls `util.load_saved_artifacts()` on launch and prints `Starting Python Flask Server For Home Price Prediction...`.
  - CORS: responses add `Access-Control-Allow-Origin: *` manually in each route.

Key files to inspect first
- `server/server.py` — entrypoint for local testing; shows request shapes and response format.
- `server/util.py` — (expected) contains ML artifact loading and functions used by the API: `load_saved_artifacts()`, `get_location_names()`, `get_estimated_price(location, total_sqft, bhk, bath)`. If this file is missing, ask the repo owner for it.
- `client/` — contains `app.js`, `app.html`, `app.css` (currently empty in this workspace). Typical agent tasks will add client-side code that calls the API endpoints above.

Developer workflows & run hints
- Run the API directly from the `server` directory (or call the file path):
  - `cd server` then `python3 server.py` or from project root `python3 server/server.py`.
- Minimal dependency: Flask. If missing, install with `pip install flask` in the chosen environment.
- If you see `ImportError: No module named util`, run the script from `server/` or set `PYTHONPATH` so the `server` package directory is discoverable.

API usage examples (exact shapes expected by the existing code)
- Get locations (GET):
  - `curl http://localhost:5000/get_location_names`
- Predict price (form POST):
  - ```
    curl -X POST \
      -F "total_sqft=1200" \
      -F "location=SomeLocation" \
      -F "bhk=2" \
      -F "bath=2" \
      http://localhost:5000/predict_home_price
    ```
  - Response JSON contains `estimated_price`.

Project-specific patterns & conventions
- The server expects `request.form` (form-encoded) values rather than JSON bodies. When calling or testing endpoints, prefer form fields (`-F` with `curl` or `FormData` in browser JS).
- CORS is handled manually per-response in `server/server.py`. When adding many endpoints, either follow the same pattern or switch to `flask_cors.CORS(app)` (note: changing to `flask_cors` is a non-trivial change — update all routes to remove manual headers if you do).
- ML / artifact loading is centralized in `util.py` via `load_saved_artifacts()`; agents should not re-load models per-request — follow the single-startup loading approach used in `server/server.py`.

Integration & missing pieces to verify
- Confirm presence of `server/util.py` and any serialized model artifacts it expects. If absent, ask which artifacts to use or where to locate them.
- Client-side code is empty; when adding UI, follow this flow:
  1. Fetch `GET /get_location_names` to populate location controls.
  2. Submit a form-encoded POST to `/predict_home_price` and display `estimated_price`.

What to ask the maintainer if needed
- Where are the model artifacts and `util.py` (if not present in the repo)?
- Which Python environment / dependency list should be used (no `requirements.txt` was found)?

Editing rules for AI agents (do not guess)
- Do not assume model file names or paths — always open `server/util.py` to discover exact artifact names.
- Keep request/response shapes exactly as in `server/server.py` unless the maintainer approves API changes.
- Preserve the manual CORS behavior unless you update all routes consistently.

If anything is unclear, ask a short, specific question (for example: “I can't find `server/util.py` — should I implement `get_estimated_price()` and where should I store model artifacts?”)

---
If you want, I can expand this into a short `README.md` for the server and add a minimal working `client/app.js` example that calls the endpoints. Which would you prefer next?
