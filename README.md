# Digital Product Store Backend

FastAPI + SQLAlchemy + SQLite + JWT + Stripe Checkout.

## Setup

```bash
cd backend
python -m venv .venv
# Windows: .venv\Scripts\activate
# macOS/Linux: source .venv/bin/activate
pip install -r requirements.txt
copy .env.example .env   # Windows
# cp .env.example .env   # macOS/Linux
uvicorn app.main:app --reload
```

Swagger: http://localhost:8000/docs

Default seeded admin comes from `ADMIN_EMAIL` / `ADMIN_PASSWORD` in `.env`.

## Stripe

Set `STRIPE_SECRET_KEY` and `STRIPE_WEBHOOK_SECRET`. For local webhook testing, use Stripe CLI:

```bash
stripe listen --forward-to localhost:8000/payments/webhook
```

Copy the generated `whsec_...` into `.env`. Use Stripe test card `4242 4242 4242 4242`, any future expiry, any CVC.

## Tests

```bash
pytest -q
```
