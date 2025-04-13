<!---
{
"id": "a0f6c77d-9645-4e6c-80dc-a80608786266",
  "depends_on": ["3ee0acd9-0f99-4423-b4f3-a0ca84a16422", "7130a694-458e-4e24-80b7-d8673f765e69"],
  "author": "Stephan Bökelmann",
  "first_used": "2025-04-07",
  "keywords": ["python", "http.server"]
}
--->

# Serving Static Files with `http.server`

## Introduction

In the early days of the internet, web servers were simple programs that served static documents—plain HTML files, images, and scripts—over HTTP to requesting clients. These early servers operated in a straightforward manner: when a browser made a request, the server responded with a file from the local disk. This mode of operation, known as **static file serving**, still forms the basis of all web communication today, even as web technologies have evolved dramatically.

Python, true to its philosophy of "batteries included," offers a built-in tool for this exact purpose: the `http.server` module. With a single command, Python can be used to launch a minimal HTTP file server, enabling users to serve local directories over the network. This makes it an ideal tool for quick testing, local development, and educational exploration.

However, it is important to distinguish between this form of static serving and **dynamic web applications**, which involve server-side processing, stateful user sessions, database interaction, or API logic. Unlike production-grade servers such as Nginx, Apache, or Python frameworks like Flask and FastAPI, `http.server` does not support dynamic content generation, authentication, middleware, or routing logic.

This exercise introduces the usage of Python's `http.server` for static file serving, while also outlining its limitations. By understanding both its capabilities and its constraints, learners gain foundational insight into the architecture of modern web servers and the transition from static documents to fully dynamic, interactive applications.



## Tasks

1. Prepare a Simple Web Project

Create a new folder with a basic HTML file:

```bash
mkdir ~/my_web_test && cd ~/my_web_test
```

Inside this directory, create an HTML file:

```html
<!-- index.html -->
<!DOCTYPE html>
<html lang="en">
<head>
  <meta charset="UTF-8">
  <title>Hello Server</title>
</head>
<body>
  <h1>Hello from http.server!</h1>
  <p>This page is being served locally using Python.</p>
</body>
</html>
```

Save the file as `index.html`.


2. Start the Local Server

While still in the `~/my_web_test` directory, run:

```bash
python3 -m http.server
```

By default, this starts a server on port 8000. Open your browser and visit:

```
http://localhost:8000
```

You should see your HTML page rendered in the browser.

---

3. Explore Directory Listings

If there is no `index.html`, Python will automatically list the directory contents. Try renaming your file and reloading the page to see what happens.

```bash
mv index.html hello.html
```

Then reload `http://localhost:8000` in your browser.

---

4. Change the Port

To run the server on a different [port](github.com/STEMgraph/missing):

```bash
python3 -m http.server 9000
```

Then visit:

```
http://localhost:9000
```

5. Retrieve the Page via Terminal Tools

To simulate a simple HTTP request from the command line, try retrieving the web page using tools like `wget` and `curl`. These commands are useful for debugging and scripting.

```bash
wget http://localhost:8000 -O page_wget.html
curl http://localhost:8000 -o page_curl.html
```

These commands download the `index.html` content served by your Python server and store them locally in the respective files. You can inspect the files using `less`, `cat`, or open them in a browser or editor to verify their contents.

> 💡 Tip: Try comparing the contents of the two files using `diff page_wget.html page_curl.html`.


## Questions

1. What happens when you request a directory without an `index.html`?
2. Why might you want to use a different port than the default 8000?
3. What are CORS headers, and why might they matter for JavaScript?
4. Why is `http.server` not suitable for serving Python-based web apps?
5. What would be a better alternative if you wanted to create a dynamic API in Python?

## Advice

`http.server` is a great way to explore how browsers retrieve files and how directory structures work in the context of the web. It's intentionally limited—which helps you appreciate the purpose of **real web servers** later on.

Think of it as a **training bicycle** for web development. It teaches you the basics of ports, file paths, and browser requests—without the complexities of frameworks or backends. Once you’re confident here, you’ll be ready to build real apps using tools like **Flask**, **FastAPI**, or **Django**.