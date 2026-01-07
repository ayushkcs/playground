# FastAPI

### Environment Configuration

1. Install Python Version 3.

2. Install and configure Visual Studio Code.

3. Setup Virtual Environment [Python].

    ```
    # create a virtual environment
    python3 -m venv venv

    # activate the venv
    source venv/bin/activate

    # deactivate the venv
    deactivate
    ```

**Note:**

- One should never push the venv folder to the project repo because creating a virtual environment requires different commands depending on whether you are using windows/macos/linux.

- The `venv` folder is built specifically for your computer's operating system.

- Thus, move the `venv` folder to the `.gitignore` file.

    `touch .gitignore`
    
    `echo 'venv/' >> .gitignore`

**Install FastAPI:**

- Install the FastAPI once the venv is setup and activated.

    `pip install "fastapi[standard-no-fastapi-cloud-cli]"`

- To check all the dependencies installed in your venv:

    `pip freeze`

## Basics of FastAPI

![First Principles View](/fastapi/assets/first_principles_view.png)

`Break down of the basic code:`

```Python
from fastapi import FastAPI

app = FastAPI()
```

![Break down of the basic code](/fastapi/assets/breakdown1.png)

- We reached out to fastapi library because we don't want to write the code to handle networking, security or data translation from scratch.

`app()`: It's a server object.

This object does mainly 3 jobs:

1. **The Listener:**

    - Receives request and listen to the port (8000).

2. **The Router:**

    - looks for correct address - `/login`, etc.

3. **The Translator:**

    - takes raw data coming from the internet (text) and convert into Python object (`dict`) to be used.

```Python
# this is called "Path Operation Decorator"
@app.get("/")

async def root():
    return{"message" : "hello world"}
```

Here's the breakdown of the above code:

`@app.get("/")`: This line is called "Path Operation Decorator" in FastAPI.

`.get`: tells the app to look for GET request (An Operation / HTTP Method).

`"/"`: Path / Endpoint / Route. Represents the path - root here.

`async`: 

- Enables concurrency (the ability to handle multiple tasks at the same time). 

- It defines a `Coroutine`.

- Unlike a standard function that blocks the thread until it's finished, a coroutine can `yield` control back to the event loop while waiting for the I/O tasks.

- Here is a great resource to dive deep - [Concurrency and async / await](https://fastapi.tiangolo.com/async/)

`Event Loop:`

- It's the engine that manages all the `async` tasks, switching between them so the CPU is not sitting idle.

![Break down](/fastapi/assets/breakdown2.png)

`Data Serialization:`

- Automatically converting python code into the text the browser understands.

`JSON`:

- Javascript Object Notation.
- The Standard text-based format for transmitting data in web applications.

`content-type Header`:

- `application/json`
- FastAPI automatically sets this so that browser knows what it is receiving.

`Serialization` / `JSON Encoding` / `Marshalling`:

- Process of converting a python object (like dict) into a format that can be stored or transmitted like JSON string.

Thus,

| | Term | Meaning |
| :---: | :--- | :--- |
| 1 | Path / Endpoint / Route | The URL Location |
| 2 | HTTP Method | Receiving or Sending the data |
| 3 | Routing | Linking URL to the code |
| 4 | Asynchronous / Non-blocking | Not waiting around / Multi-tasking |
| 5 | Serialization / JSON Encoding | Packaging for the web |

### Starting the Server

**`uvicorn`**

- ASGI Server
- Asynchronous Server Gateway Interface.
- Acts as middleman between the internet and the python application code.
- Modern standard for python web server.
- Allows app to handle many connections (concurrency) at once using `async`.

![Starting the Server](/fastapi/assets/starting_server.png)

`Executable`: Starts the Server Engine

`Module`: Looks for a file `main.py`

`Separator`: Inside that file, look for:

`Object/Instance`: The specific FastAPI variable we created

`uvicorn main:app`

- This command deploys your code onto a live server so it can actually receive traffic from a browser.

**Hot Reloading / Development Mode:**

`uvicorn main:app --reload`

- This command tells uvicorn to continuously watch your code files for changes.
- If you make any changes to `main.py`, it automatically restarts the server and you don't have to restart it.

Here's the workflow:

| | Steps | Description |
| :---: | :--- | :--- |
| 1 | Search | uvicorn finds the `main.py` file | 
| 2 | Load | imports the app object |
| 3 | Bind | opens a communication port at 8000 |
| 4 | Listen | waits for a request. when it arrives, hand it to the app |

**Why can't we run `python3 main.py`?**

There are various reasons for that:

1. **Protocol Bridge**:

    - Internet speaks HTTP. Python speaks object. `uvicorn` acts as the translator between them.

2. **Keeping the App Alive:**

    - A normal python script runs and then ends. 
    - But we need a web server in an infinite loop, constantly watching the network port for the new requests.

3. **Concurrency Management:**

    - `uvicorn` manages the event loop.
    - It manages the queue in case of concurrent visitor so that it does not crash.

---

**API Documentation:**

`http://127.0.0.1:8000/docs` or `http://127.0.0.1:8000/redoc`

- Aka Swagger UI.
- It's an automatically generated instruction manual for your API.

`OpenAPI/Swagger`:

- It's a global standard/specification for describing APIs.
- It automatically generates a schema (a JSON file) that follows this standard.
- Solves the problem of documentation gap. A fixed source of truth.

---

**Concerns and Resources in API:**

> While building an API, the path is the main way to separate 'concerns' and 'resources'.

Here are a few examples:

`Resources`: (NOUN). object/piece of data (Data Entity).

`/users`: points to user resource

`/products`: points to product resource

`/orders`: points to order resource

**Resources:** Noun

- Resource is a thing your API manages.
- They represent object stored / managed by the backend.

Example: users, orders, products, posts, comments

```
/users
# users is a resource

/users/42
# 42 is a specific user resource
```

**Concerns:**

- A specific responsibility or behaviour related to that resource.
- They are often: Actions, Processes or Features.
- It's more about the workflow or behaviour.

Example: Authorization, Authentication, Search, Analytics, Notification, Reporting.

| URL Path | Resource | Concerns (Responsibility) |
| :---: | :--- | :--- |
| `/items/` | Items | Catalog Management |
| `/auth/` | Credentials | Security & Identity |
| `/reports/` | Data Logs | Analytics & Statistics |

> Sometimes concerns appears in paths.

Examples: Authentication `(Concern)`

`Post` `/auth/login` 

`Post` `/auth/logout` 

`Post` `/auth/refresh` 

**Operations:**

- Aka HTTP Methods (Known as Operations in FastAPI).

| Method | Description |
| :---: | :--- |
| POST | To create data |
| GET | To read data |
| PUT | To update data |
| DELETE | To delete data |

Examples:

`@app.get()`, `@app.post()`, `@app.put()`

---

> Order of functions defined does matter in FastAPI.

- The first path operation that matches gets returned.
- FastAPI looks for the path matching in a sequential order only.

```Python
# first root function
@app.get("/")
async def root():
    return{"message" : "first root function"}

# second root function
@app.get("/")
async def root():
    return {"message" : "second root function"}

# The first root function will be executed and not the second one.
```
---

### Testing APIs

**Why do we use a tool like `Postman`?**

- If we want to use `POST` methods and send data to the backend via broswer, we will need a frontend for that to capture data.
- But we don't necessarily always have it and thus we use tools like Postman for testing.

---

### Schema Validation with Pydantic

- Pydantic is a Data Validation and Settings Management library for Python.
- While Python itself is "dynamically typed" (meaning variables can change types easily), Pydantic enforces "strictness" so your application doesn't crash due to bad data.

```Python
@app.post("/createposts")
def create_posts(payload: dict = Body(...)):
    print(payload)
    return {"new_post": f"title {payload['title']} content: {payload['content']}"}
```

**Why do we need schema?**

- It's a pain to get all the values from the body like above.
- Right now, the client can send whatever data they want.
- The data is not getting validated.
- We ultimately want to force the client to send the data in a schema that we expect.

To solve all of this issue, we are going to use a library called `pydantic`.

```Python
# schema / data model
class Post(BaseModel):
    # Type Annotations / Fields.
    title: str
    content: str

@app.post("/createposts")
def create_posts(post: Post):
    print(post.title)
    print(post.content)
    return {"new_post": f"title {post.title} content: {post.content}"}
```

`BaseModel`:

- This is a class you inherit from Pydantic. 
- By doing this, you give your Post class super-powers, like the ability to automatically check data types and convert JSON into Python objects.
- Without this code, you'd have to write manual "if-statements" for every single piece of data:

    ```Python
    # The "Old/Hard" Way
    if "title" not in data:
        return "Error: Missing title"
    if not isinstance(data["title"], str):
        return "Error: Title must be a string"
    ```
`Type Annotations / Fields`:

- These define the Structure of your data. 
- If a user sends a number for the title, Pydantic will try to convert it to a string. 
- If it receives a complex object it can't convert, it will raise a *Validation Error*.

```Python
@app.post("/createposts")

# post: is a variable here which contains all the data sent by the user from the request body (frontend)

def create_posts(post: Post):
    print('title:', post.title)
    print('content:', post.content)
    print('published:', post.published)
    print('rating:', post.rating)
    # this prints a regular pydantic model
    print(post)
    # title='top beaches in goa' content='check out these awesome beaches in goa!' published=True rating=10

    # this convert the "post" pydantic model to a dictionary
    print(post.dict()) 
    # {'title': 'top beaches in goa', 'content': 'check out these awesome beaches in goa!', 'published': True, 'rating': 10}
    return {"new_post": post}
```

---

**What happens under the hood?**

When FastAPI uses your Pydantic model, it performs four major tasks:

1. `Parsing`:

    - It reads the raw JSON text from the request.

2. `Validation`: 

    - It checks if the title and content exist and are the right types.

3. `Type Conversion`: 

    - If the user sends a number 123 for the title, Pydantic converts it to the string "123". (This is called `Coercion`).

4. `Documentation`: 
    - It automatically updates your /docs (Swagger) page to show exactly what the JSON "package" should look like.

--- 

### CRUD Operations

![CRUD Operations](/fastapi/assets/crud.png)

---

### Path Parameters

```Python
# id: path parameter | always returned as a string

@app.get("/posts/{id}")
def get_post(id):
    post = find_post(int(id))
    return {"post_detail" : post}
```

> Order matters a lot here. So, arrange your APIs accordingly.

```Python
# this will throw an error if we send a GET request of /posts/latest because "latest" will be treated as an id here and which is not integer.

@app.get("/posts/{id}")
def get_post(id: int):
    post = find_post(id)
    return {"post_detail" : post}

@app.get("/posts/latest")
def get_latest_post():
    latest_post = my_posts[-1]
    return {"latest_post": latest_post}
```
---

### Status Codes in FastAPI

What happens if a resource is not found in the backend?

- how to return the proper status codes?
- how to return the proper detailed error messages?

```Python
from fastapi import FastAPI, Response, status, HTTPException

# in this case, we have to hardcode everything and it's not a good practice
@app.get("/posts/{id}")
def get_post(id: int, response: Response):
    post = find_post(id)
    if not post:
        response.status_code = status.HTTP_404_NOT_FOUND
        return {"message" : f"post with id: {id} not found"}
    return {"post_detail" : post}

# thus we will use HTTPException from fastapi
@app.get("/posts/{id}")
def get_post(id: int, response: Response):
    post = find_post(id)
    if not post:
        raise HTTPException(status_code=404, detail="Item not found")
    return {"post_detail" : post}
```

If we just want to change the default status code of any specific operations, here's how we do it:

```Python
@app.post("/posts", status_code=status.HTTP_201_CREATED) 
```

