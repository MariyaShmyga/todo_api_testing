# :alien: ToDo API Testing
### REST API tests written with Python, pytest and requests
___
## About

This is my first practice project in **API test automation with Python and pytest**.

The project was created while following [Pixegami's](https://www.youtube.com/watch?v=7dgQRVqF1N0&t=1s) tutorial on REST API integration testing. 
It contains automated tests for a public Todo API and covers the basic task lifecycle: creating, retrieving, updating, listing and deleting tasks.

I use this repository to practice API testing and gradually learn test automation.
___
## Tested scenarios

The current test suite contains four scenarios:

### `test_can_create_task`

Creates a new task and then retrieves it by its ID.

Checks that:

- the task is successfully created;
- the API returns HTTP `200`;
- the created task can be retrieved;
- returned `content` matches the original payload;
- returned `user_id` matches the original payload.

### `test_can_update_task`

Creates a task, updates its data and retrieves it again.

Checks that:

- the update request succeeds;
- updated `content` is returned;
- updated `is_done` value is returned.

### `test_can_list_tasks`

Creates three tasks for the same generated user and requests the user's task list.

Checks that:

- the API returns HTTP `200`;
- the returned list contains three tasks.

### `test_can_delete_task`

Creates a task, deletes it and tries to retrieve it again.

Checks that:

- the delete request succeeds;
- requesting the deleted task returns HTTP `404`.
___
## :disguised_face: Tech stack

| Technology | Used for |
| --- | --- |
| **Python 3.12** | Test implementation |
| **pytest** | Running tests and assertions |
| **requests** | Sending HTTP requests |
| **uuid** | Generating unique test data |

## API operations

| Operation | HTTP method | Endpoint |
| --- | :---: | --- |
| Create task | `PUT` | `/create-task` |
| Get task | `GET` | `/get-task/{task_id}` |
| Update task | `PUT` | `/update-task` |
| List tasks | `GET` | `/list-tasks/{user_id}` |
| Delete task | `DELETE` | `/delete-task/{task_id}` |
___
## Test flow

```text
Generate unique test data
          │
          ▼
      Create task
          │
          ├──────────► Get task ──────► Validate data
          │
          ├──────────► Update task ───► Get task ───► Validate changes
          │
          ├──────────► List tasks ────► Validate number of tasks
          │
          └──────────► Delete task ───► Get task ───► Expect 404
```


## Project structure

```text
todo-api-pytest/
│
├── .gitignore
├── README.md
└── test_todo_api.py
```
___

## Run locally

### 1. Clone the repository

```bash
git clone <repository-url>
cd todo-api-pytest
```

### 2. Create a virtual environment

```bash
python -m venv .venv
```

### 3. Activate it

Windows:

```bash
.venv\Scripts\activate
```

macOS / Linux:

```bash
source .venv/bin/activate
```

### 4. Install dependencies

```bash
pip3 install pytest
pip3 install requests
```

### 5. Run the tests

```bash
pytest -v
```
___
## :heavy_check_mark: What I practiced

While working on this project, I practiced:

- sending HTTP requests from Python;
- working with REST API endpoints;
- parsing JSON responses;
- validating HTTP status codes;
- writing assertions with pytest;
- creating and reusing helper functions for API requests;
- generating unique test data with UUID;
- checking application state after create, update and delete operations.

---

## :books: Next steps

As I continue learning test automation, I plan to extend this project with:

- [ ] negative test cases;
- [ ] boundary value testing;
- [ ] pytest fixtures;
- [ ] parametrized tests;
- [ ] test setup and cleanup;
- [ ] API client separation from test code;
- [ ] logging;
- [ ] automated test execution with CI.
