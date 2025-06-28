# FastAPI on Vercel

This project demonstrates how to deploy a simple FastAPI application on [Vercel](https://vercel.com/).

## Project Structure

```
.
├── api/
│   └── main.py
├── vercel.json
└── README.md
```

## Files

### `api/main.py`

This file contains a minimal FastAPI app with a health check endpoint:

```python
from fastapi import FastAPI

app = FastAPI()

@app.get("/")
async def health_check():
    return "The health check is successful"
```

### `vercel.json`

This configuration file tells Vercel how to build and route your FastAPI app:

```json
{
    "builds": [
        {
            "src": "api/main.py",
            "use": "@vercel/python"
        }    
    ],
    "routes": [
        {
            "src": "/(.*)",
            "dest": "/api/main.py"
        }
    ]
}
```

## Deployment

1. **Install Vercel CLI** (if you haven't already):

   ```bash
   npm install -g vercel
   ```

2. **Deploy**:

   ```bash
   vercel .
   ```

   Follow the prompts to deploy your project.

## Usage

After deployment, visit your Vercel project URL. You should see:

```
The health check is successful
```

## Notes

- The `@vercel/python` builder is used to run the FastAPI app.
- All routes are directed to `api/main.py` as specified in `vercel.json`.
