# Glance Config

Custom configuration repository for **[Glance](https://github.com/glanceapp/glance)** — a lightweight, self-hosted dashboard for aggregating feeds, widgets, and links into a clean homepage.

![Dashboard Preview](https://i.redd.it/nj1uxa1vghhg1.png)

This repository contains:

- Glance YAML configuration files
- Custom assets (CSS)
- **Custom widgets** for qBittorrent and Seerr

---

## Repository Structure

```
glance-config/
├── assets/
│   ├── global.css              # Custom CSS styling
│
├── config/
│   ├── glance.yml            # Main configuration entrypoint
│   └── ...                   # Additional page configs
```

---

## Getting Started

### 1️⃣ Clone the Repository

```bash
git clone https://github.com/RedVelocity/glance-config.git
cd glance-config
```

---

### 2️⃣ Run with Docker (Recommended)

You can grab the docker compose setup from [here](https://github.com/RedVelocity/self-hosted)

---

### 3️⃣ Access the Dashboard

Open your browser and go to:

```
http://localhost:8080
```

---

## Configuration Overview

Glance uses:

- A main config file (`glance.yml`)
- Modular page YAML files (`qb.yml`, `seerr.yml`, etc.)
- A custom CSS file to change the background and add transparency to widgets (`assets/global.yml`)
  
---

# Environment Variables

This configuration **relies heavily on environment variables** to keep the setup flexible and portable.

## Required: `BASE_HOST`

At minimum, you must define:

```
BASE_HOST
```

This is used throughout the config to dynamically generate service URLs:

```
https://jelly.${BASE_HOST}/
https://qb.${BASE_HOST}/
https://seerr.${BASE_HOST}/
https://rad.${BASE_HOST}/
...
```

## Additional Environment Variables

Several widgets require authentication or API credentials.

Examples from the main config:

```yaml
username: ${AG_USER}
password: ${AG_PASSWORD}
```

And the custom widgets:

- `qb.yml`
- `seerr.yml`

may require variables such as:

- API keys
- Service URLs
- Usernames/passwords
- Tokens

> [!IMPORTANT]  
> ⚠️ Always check the individual YAML files (`qb.yml`, `seerr.yml`, etc.) to see which environment variables are required.

---

# Custom CSS

Global styling is defined in:

```
assets/global.css
```

It is referenced in `glance.yml`:

```yaml
theme:
  custom-css-file: /assets/global.css
```
