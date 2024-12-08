# FastAPI

---

This project demonstrates how FastAPI works.

### Key Takeaways

1. To start FastAPI, we can use any of the below commands (Assume books.py is the entry point or main function of the FastAPI) -
    1) `uvicorn books:app --reload`
    2) `fastapi run books` (This is available in newer versions of FastAPI and is production mode run)
    3) `fastapi dev books` (This is available in newer versions of FastAPI and is developer mode run)

2. `--reload` makes sure for every change we make in the script, the uvicorn server is restarted.

3. FastAPI provides a **swagger ui** by default at the endpoint **_/docs_**

4. FastAPI endpoints are checked in the top to bottom order and matching endpoint is executed.
