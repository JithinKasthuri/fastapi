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
5. We can use the `pydantic` module to implement validation of request body.  
First we have to import the required components from `pydantic`-  
`from pydantic import BaseModel,Field`  
Then create a class for the request body, which should extend the `BaseModel`.  
Write the required field validations inside this class and use this class to accept request body in the api.
6. We can also provide example field values (which can be displayed in swagger ui) with the help of `json_schema_extra`
7. Path and Query parameter validations can be done by the `Path` and `Query` components from fastapi module.
8. `HTTPException` from fastapi can be used to send exception details to the client.  
Example: `raise HTTPException(status_code=404,detail="Item not found")`
9. `starlette` module can be used to send explicit status code to the client for each api.  
`from starlette import status`  
`@app.get("/books/{book_id}",status_code=status.HTTP_200_OK)`  
Common status codes and purpose -

| **Status Code** | **Description**                                                                                                                  |
|-----------------|----------------------------------------------------------------------------------------------------------------------------------|
| 200             | **OK** - Standard Response for a Successful Request. Commonly used for successful Get requests when data is being returned.      |
| 201             | **Created** - The request has been successful, creating a new resource. Used when a POST creates an entity.                      |
| 204             | **No Content** - The request has been successful, did not create an entity nor return anything. Commonly used with PUT requests. |
| 400             | **Bad Request** - Cannot process request due to client error. Commonly used for invalid request methods.                         |
| 401             | **Unauthorized** - Client does not have valid authentication for target resource.                                                |
| 403             | **Forbidden** - Access denied.                                                                                                   |
| 404             | **Not Found** - The clients requested resource can not be found.                                                                 |
| 409             | **Conflict** - Resource conflict occurred.                                                                                       |
| 422             | **Unprocessable Entity** - Semantic Errors in Client Request                                                                     |
| 500             | **Internal Server Error** - Server encountered an error.                                                                         |
| 503             | **Service Unavailable** - Server is overloaded or under maintenance.                                                             |
