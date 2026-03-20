---
icon: folder-open
---

# virtualFS

The virtual FS manages storage, files, saving, etc. Content is loaded and saved onto either the file itself, the Origin Private File System (OPFS), or Indexed DB.

Storage methods:

* Indexed DB (Default)
* Origin Private File System (Servers only)
* Local storage
* File handle

### Relevant Links

{% content-ref url="files-and-folders.md" %}
[files-and-folders.md](files-and-folders.md)
{% endcontent-ref %}

{% content-ref url="storage-methods.md" %}
[storage-methods.md](storage-methods.md)
{% endcontent-ref %}

{% content-ref url="defaultfs.md" %}
[defaultfs.md](defaultfs.md)
{% endcontent-ref %}

***

### Methods

There are about a dozen different methods you can call, some redundant/deprecated. The most important ones are listed below.&#x20;

Most methods take in two-three values, name, path, and permissions.

**Name:** Name of the target file. Cannot be an empty string or special characters, and duplicate names are allowed. See files and folders for more details

**Path:** Seperated by slashes. It doesn't matter if it looks like `/Example/Path/` or `Example/Path`. Results are still parsed the same.

**Permission:** Usually verified by the user. However, implementing changes where the writing files has to be verified by the user for installed apps is repetitive, so I never got around to doing that.

#### `initialize`

Called by default on the start of launching the OS. Fetches the initial storage system and files.&#x20;

```tsx
public async initialize(): Promise<void>
```

#### `save`

Saves the file system. Private.

```tsx
private async save(): Promise<void>
```

#### `readdir`

Reads a specified directory

```tsx
public async readdir(
		path: string
): Promise<Record<string, File | Directory>>
```

#### `readfile`

Reads a specified file

```tsx
public async readfile(path: string, name: string): Promise<File>
```

#### `writeFile`

Writes a file to the specified directory



#### `updateItem`

Updates a specified item - can be either a file or a folder

```tsx
public async updateItem<
		K extends File | Directory,
		P extends K extends File ? keyof K : keyof K
		>(
		path: string,
		name: string,
		property: P,
		value: K[P],
		options?: {
			newName?: string;
			fileType?: K extends File ? K['fileType'] : never;
		}
): Promise<void>
```

#### `deleteItem`

Deletes a specified item

```tsx
public async deleteItem(
    path: string, 
    itemName: string, 
    permission?: Permission
): Promise<void>
```
