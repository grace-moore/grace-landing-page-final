# grace-landing-page-final

## Project Overview
A simple static HTML landing page ("Hello World" placeholder).

## Tech Stack
- Plain HTML (no build system, no package manager)
- Served locally via Python's built-in HTTP server

## Project Structure
- `index.html` — The main landing page
- `README.md` — Project readme
- `.github/workflows/` — Azure Static Web Apps CI/CD configuration (original deployment)

## Running the App
The app is served on port 5000 using:
```
python3 -m http.server 5000
```

## Deployment
Configured as a **static** deployment with `publicDir: "."`.
