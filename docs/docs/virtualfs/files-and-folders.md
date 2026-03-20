# Files and Folders

The virtualFS saves both files and folders.&#x20;

**Edge Case Handling:** If names overlap, then the OS will automatically add a number to the end of the filename. For example, if a directory already has a file called `Version`, then making a new file `Version` will result in it being called `Version (1)`.

#### item

Both directories and files are extensions of the item interface.&#x20;

{% hint style="info" %}
Dates are created automatically when making an item.
{% endhint %}

```ts
export interface Item {
  type: 'directory' | 'file';
  date: Date;
  permission: any;
  deleteable: boolean;
}
```

{% hint style="danger" %}
Only system items should be `deletable: false`, for security reasons.
{% endhint %}

### Directories/Folders

Directories and folders are similar to files, except with a `children` attribute.

Children cannot be undefined, however, it can be empty.&#x20;

```ts
export interface Directory extends Item {
  type: 'directory';
  children: {
    [key: string]: Directory | File;
  };
}
```

### Files

Files also manage multiple states and has its own subtypes who each uniquely effect file the file content.

```typescript
export interface FileContentMap {
  txt: string;
  img: Uint8Array | string;
  exe: Omit<Executable, 'mainComponent'>;
  theme: ColorTheme
  js: string;
  css: string;   
  html: string;
  sys: Record<string, any>;
  swf: Uint8Array;
  game: Game;
  shortcut: Shortcut;
  command: Omit<ConsoleCommand, "run"> & { run: string };
  biosCommand: Omit<BiosCommand, "run"> & { run: string };
}
```

* **txt** - can contain any data, and is by default opened by notepad
* **img** - not used as much as other files, can be substitued as a txt
* **exe** - core app content. See [creating your own app](../creating-content/apps.md) for more information
* **theme** - color theme, which manages the colors of the user-side OS. Do not confuse with the user UITheme, which manages other states as well. They were seperated version 15 to make the OS more concise.
* &#x20;**js** - Javascript file. Not used often
* **css** - CSS file. Not used often
* **html** - HTML file. Not used often
* **sys** - a global management for system files. Not used very often
* **game** - games downloaded from the appstore, see Appstore app for more details
* **shortcut** - points to another file, see Shortcut App for more details
* **command** - executed in the Terminal, see [creating commands](../creating-content/commands.md) for more details
* **bioscommand** - used in the BIOS, see [creating bios commands](../creating-content/commands.md) for more details

```typescript
// Discriminated Union for Files
type FileBase = Omit<Item, "type"> & {
  type: "file";
  displayName?: string;
};

type FileVariants = {
  [K in keyof FileContentMap]: FileBase & {
    fileType: K;
    content: FileContentMap[K];
  };
};
// Union of all file types
export type File = FileVariants[FileType];
```

### Creating your own filetype

When creating file types:

{% stepper %}
{% step %}
#### Add filetype

Add the file type to the file content map
{% endstep %}

{% step %}
#### Add mimetype

While they aren't typically used, the OS will still throw an error without a mimetype.
{% endstep %}
{% endstepper %}

{% hint style="danger" %}
WHEN CREATING YOUR OWN FILE TYPE, DO **NOT** INCLUDE A FUNCTIONAL TYPE. INDEXED DB AND OTHER STORAGE METHODS **WILL** THROW AN ERROR.
{% endhint %}
