# RS256 JWT Verification API

## Deploy on Render
1. Upload these files to a GitHub repository.
2. In Render, choose **New + → Web Service** and connect the repository.
3. Use:
   - Build command: `pip install -r requirements.txt`
   - Start command: `uvicorn main:app --host 0.0.0.0 --port $PORT`
4. Once deployed, submit the full endpoint URL, e.g. `https://YOUR-SERVICE.onrender.com/verify`.

## Test
```bash
curl -i -X POST 'https://YOUR-SERVICE.onrender.com/verify' \
  -H 'Content-Type: application/json' \
  -d '{"token":"not-a-real-token"}'
```
Invalid tokens return HTTP 401 with `{"detail":{"valid":false}}`. Valid tokens are accepted only if the RS256 signature, issuer, audience and expiry pass verification.
