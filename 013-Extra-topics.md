# Extra Topics — Exam Prep Q&A (Database, Backend, API, Git additions)

---

## 🗄️ Database — Design Concepts

**1. Difference between Primary Key and Foreign Key?**
A **Primary Key** uniquely identifies each row in a table (no duplicates, no NULLs). A **Foreign Key** is a column in one table that references the **Primary Key** of another table, creating a relationship between the two tables.
```sql
CREATE TABLE orders (
    id INT PRIMARY KEY,
    user_id INT,
    FOREIGN KEY (user_id) REFERENCES users(id)
);
```

**2. What is normalization? What are 1NF, 2NF, 3NF? Why is it needed?**
Normalization is the process of organizing database tables to **reduce data redundancy** and improve data integrity.
- **1NF** — each column holds atomic (indivisible) values, no repeating groups.
- **2NF** — 1NF + every non-key column depends on the **whole** primary key (relevant for composite keys).
- **3NF** — 2NF + no non-key column depends on **another non-key column** (removes transitive dependency).
It's needed to avoid duplicate data, update anomalies, and inconsistency.

**3. What is a one-to-many relationship? Many-to-many?**
- **One-to-many** — one row in Table A relates to multiple rows in Table B (e.g. one user has many orders). Implemented with a foreign key in the "many" table.
- **Many-to-many** — many rows in Table A relate to many rows in Table B (e.g. students and courses). Implemented using a **junction/join table** that holds foreign keys to both tables.

**4. What is an index? Why use it?**
An index is a special data structure that speeds up data **retrieval/search** on a table (similar to a book's index), at the cost of extra storage and slower writes (inserts/updates). Commonly created on columns frequently used in `WHERE` or `JOIN` conditions.
```sql
CREATE INDEX idx_user_email ON users(email);
```

---

## 🖥️ Backend — General Concepts

**5. What is the client-server model?**
An architecture where the **client** (e.g. browser, mobile app) sends requests, and the **server** processes them and sends back responses (data, HTML, JSON, etc.). The client and server communicate over a network, usually via HTTP.

**6. Difference between frontend and backend?**
**Frontend** is everything the user sees and interacts with directly (UI, HTML/CSS/JS running in the browser). **Backend** is the server-side logic — handling requests, business logic, database operations, authentication — that the user doesn't see directly.

**7. What is a virtual environment (`venv`)? What do `pip install` and `requirements.txt` do?**
A **virtual environment** is an isolated Python environment with its own installed packages, separate from the system-wide Python — prevents dependency conflicts between projects.
```bash
python -m venv venv
source venv/bin/activate
pip install flask
```
`pip install` installs a package into the current (virtual) environment. `requirements.txt` lists all the project's dependencies (and versions) so others can install them with `pip install -r requirements.txt`.

**8. What are environment variables? What is a `.env` file?**
Environment variables store configuration values (e.g. secret keys, database URLs, passwords) **outside the source code**, so sensitive data isn't hardcoded or committed to version control. A `.env` file is a common way to define these locally, and it's loaded into the environment (e.g. via the `python-dotenv` package) — it should be added to `.gitignore`.

**9. What is WSGI?**
WSGI (Web Server Gateway Interface) is a standard interface between Python web applications (like Flask) and web servers, defining how requests/responses are passed between them. It's the underlying protocol that lets Flask communicate with servers like Gunicorn or uWSGI in production.

---

## 🌐 API — Additional Concepts

**10. What is CORS?**
CORS (Cross-Origin Resource Sharing) is a browser security mechanism that controls whether a web page from **one origin** (domain) is allowed to make requests to a server on a **different origin**. Servers must explicitly allow this via response headers (e.g. `Access-Control-Allow-Origin`), otherwise the browser blocks the request.

**11. What are HTTP headers? Give two examples.**
Headers are key-value pairs sent with an HTTP request/response that provide metadata about the message.
- `Content-Type` — tells the receiver what format the body is in (e.g. `application/json`).
- `Authorization` — carries credentials/tokens for authentication (e.g. `Authorization: Bearer <token>`).

**12. Difference between query params and path params?**
**Path params** are part of the URL path itself, identifying a specific resource: `/users/5` (`5` is the path param). **Query params** come after `?` and are used for filtering/optional data: `/users?age=25&sort=name`.

**13. What is idempotency? Which HTTP methods are idempotent?**
An operation is **idempotent** if calling it multiple times has the **same effect** as calling it once. `GET`, `PUT`, and `DELETE` are idempotent (repeating them doesn't change the result further). `POST` is **not** idempotent — calling it multiple times typically creates multiple new resources.

---

## 🔧 Git — Additional Commands

**14. What does `git stash` do?**
Temporarily **saves uncommitted changes** (staged and unstaged) so you can switch branches or work on something else with a clean working directory, then later restore them with `git stash pop`.
```bash
git stash
git stash pop
```

**15. Difference between `git rebase` and `git merge`?**
`git merge` combines two branches by creating a **new merge commit**, preserving the full history of both branches (including their branching point). `git rebase` **replays** the commits of one branch on top of another, creating a **linear history** without a merge commit — but it rewrites commit history, so it should be avoided on shared/public branches.

---