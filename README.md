# Enterprise URL Phishing Detector

Production-style demo of an enterprise phishing detection system:
- Flask backend API (job queue based)
- Background worker (file-based job queue — swap for RQ/Celery/Redis in production)
- ML model (RandomForest) with feature extractor
- Frontend dashboard (static HTML + JS)
- Dockerfile + CI workflow example

> Built for demo and local deployment. Python 3.10 is recommended.

## Quick start (local, Windows / Linux)

1. Clone
```
git clone https://github.com/youruser/enterprise-url-phish-detector.git
cd enterprise-url-phish-detector/backend
```
2. Create and activate virtualenv (recommended)
```
python -m venv venv
# Windows
venv\Scripts\activate
# macOS/Linux
source venv/bin/activate
```
3. Install dependencies
```
pip install -r requirements.txt
```
4. Start backend API (CMD/Terminal 1)
```
python app.py
```
5. Open the UI

## Production notes

- Replace file-based job queue with Redis + RQ or Celery for real load.
- Serve frontend by CDN / static host in production.
- Add HTTPS, authentication, rate-limiting and monitoring.
- Use real phishing datasets for training (PhishTank / Kaggle).
- Rotate & securely store model artifacts, use model versioning.

## Files of interest

- backend/app.py — API that accepts scan job requests and serves results.
- backend/worker.py — background worker processing queued jobs.
- backend/train_model.py — training script (synthetic/example).
- frontend/index.html — dashboard with job list & result viewer.

## Use these URLs that look very malicious to ML models:
  1) Extremely suspicious (IP + login):
```http://122.53.182.11/paypal/verify/login```
  2) Suspicious domain + login page:
```http://secure-update-verification-account.com/login```
  3) Safe Google.com
```https://www.google.com/```
