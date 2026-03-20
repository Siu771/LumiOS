# DefaultFS

The defaultFS is what is initially loaded into the file system when loading in for the first time.

It starts as the root, which is then mapped outwards into four default directories.&#x20;

* Documents
* Users
* System
* Trash (Unused)

Here is what the top level looks like:

```typescript
export const defaultFS: DefaultFS = {
	root: {
		type: "directory",
		date: new Date(),
		permission: Permission.SYSTEM,
		deleteable: false,
		children: { ... }
	}
}
```

#### Documents

* Only example files/folders, no secrets!

#### Users

* **Default** - Contains all default apps built into LumiOS. This is then accessed when creating a user and copied into their directory

#### System

* **SystemCoreApps** - Default OS apps that it relies on.
* **Themes** - Contains all the default themes
* **Commands** - Contains all the default commands
* **BiosCommands** - Contains all the default Bios Commands
* **Default Panics** - Default panic profiles _(Deprecated)_
* **Default Cloaks** - Default cloak profiles
* **Code** - Default code app examples _(Deprecated)_
* **Users** - Manages each user state and profile
* **Plugins** - Plugins to customize the OS _(Deprecated)_
* **Taskbar** - Default taskbar _(Deprecated)_
* **AppStore** - Default appstore _(Deprecated)_
* **Updates** - Contains update profiles, never used _(Deprecated)_
* **Scripts** - Custom user scripts
* **Version** - Version file, manages system state
* **AutoSaves** - Contains autosaves

