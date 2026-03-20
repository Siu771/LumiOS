---
icon: webhook
---

# API

LumiOS provides a default API for creating apps and extending apps from iframes for developers.

It can be accessed directly through the `window` _(Might rethink in future, security issues)_.

An example call to open the chatbot _(unfinished)_.

```
API.win.setMenu("Chatbot");
```

The API has four main components:

* kernel
* user
* win
* [virtualFS](virtualfs/)

Each letting you use a specific part of the OS directly.

