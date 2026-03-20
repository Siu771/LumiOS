---
icon: box-open-full
---

# Storage Methods

There are four main methods of storage:

1. Indexed DB - Default file storage system of LumiOS. While slow to save, it is the best storage method by far. However, it cannot store functions and will throw an error when doing so. Used on versions v6-v10 to v12-v15 on.
2. Origin Private File System (OPFS) - Only works on servers, not local devices. IndexedDB is preferred instead.
3. Local storage - Used on versions v1-v5.1, has space issues.
4. File Handle - User selects the opened file and changes are directly saved onto it. only used on v11, and only really works on Chrome.



Storage methods **cannot** contain functions. This is built into the browser.

Lumi OS also bundles rapid saves into a bundle before writing it to the selected DB in order to prevent lag. However, the timeout itself also causes lag, so that needs to be fixed in the future.

