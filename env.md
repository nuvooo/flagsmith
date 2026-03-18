# Flagsmith Coolify Configuration Guide

To get Flagsmith running on Coolify, use the following environment variables. These can be set in the **Environment Variables** section of your Coolify Service.

## Required Variables

| Variable | Recommended Value / Description |
| :--- | :--- |
| `DJANGO_SECRET_KEY` | Generate a long random string (e.g., `openssl rand -base64 32`) |
| `POSTGRES_PASSWORD` | A secure password for the database. |
| `DATABASE_URL` | Set automatically in `coolify.yaml`, but you can override if using an external DB. |

## Application Configuration

| Variable | Default / Recommended | Description |
| :--- | :--- | :--- |
| `ENVIRONMENT` | `production` | Set to `production` for better security and performance. |
| `DJANGO_ALLOWED_HOSTS` | `*` | In production, you should set this to your domain (e.g., `flagsmith.yourdomain.com`). |
| `FLAGSMITH_DOMAIN` | `${SERVICE_FQDN_FLAGSMITH}` | Your public URL. Coolify provides this automatically via `${SERVICE_FQDN_FLAGSMITH}`. |
| `USE_POSTGRES_FOR_ANALYTICS` | `true` | Recommended for self-hosting without InfluxDB. |
| `TASK_RUN_METHOD` | `TASK_PROCESSOR` | Ensures background tasks are handled correctly by the processor service. |

## Optional Features

### Email (SMTP)
If you want to send invitations and password resets:

| Variable | Description |
| :--- | :--- |
| `EMAIL_BACKEND` | `django.core.mail.backends.smtp.EmailBackend` |
| `EMAIL_HOST` | Your SMTP server (e.g., `smtp.gmail.com`). |
| `EMAIL_PORT` | `587` |
| `EMAIL_HOST_USER` | Your SMTP username. |
| `EMAIL_HOST_PASSWORD` | Your SMTP password. |
| `EMAIL_USE_TLS` | `true` |
| `SENDER_EMAIL` | The "From" address for emails. |

### Signup Control
| Variable | Value | Description |
| :--- | :--- | :--- |
| `PREVENT_SIGNUP` | `true` | Set to `true` to disable public registration. |
| `ALLOW_REGISTRATION_WITHOUT_INVITE` | `false` | Only allow users to join via email invitation. |

---

**Note:** For a full list of available environment variables, refer to the [official Flagsmith documentation](https://docs.flagsmith.com/deployment/locally-api#environment-variables).
