# Commands

Commands are a recent addition into the OS, as of v15+

Commands are done in the following format:

```typescript
export interface ConsoleCommand {
    key: string;
    description: string;
    usage?: string;
    context?: ContextKey[];
    args?: { name: string; required: boolean }[];
    minPerm: Permission;
    run: (ctx: TerminalContext, namedArgs: Record<string, any>) => Promise<void> | void;
}
```

* **key** - name of command
* **description** - description of what the command does
* _**usage**_ - how the command is used (i.e. "rm \<directoryname>")
* _**context**_ - values passed from the terminal into the function
* _**args**_ - values that the **users** pass into the function
* **minPerm** - the minimum permission that the user needs to run the function

{% hint style="warning" %}
Commands are saved onto the OS, but as mentioned under [storage methods](../virtualfs/storage-methods.md), they cannot take functions. This is fixed through stringification, but this comes with its own set of issues.
{% endhint %}

### Passed Context

You might have also noticed that context is being passed onto each command.

```typescript
export interface TerminalContext {
    currentDir: string;
    content: any;
    admin: Permission;
    permission: Permission;

    commands: Record<string, ConsoleCommand>;

    setStack: (func: (prev: any[]) => any[]) => void;
    setCurrentMenu: (prev: number) => void;
    setCurrentDir: (dir: string) => void;
    closeApp: (name: string) => void;
    getAdminRequest: () => Promise<boolean>;

    virtualFS: any;
    fileTypes: any;
}
```

Yes, it could contain a loop.&#x20;

{% hint style="info" %}
If you have trouble finding commands and the interfaces, look for defaultCommands found in the constants folder.
{% endhint %}

Here is an example command that works:

```typescript
ls: {
    key: "ls",
    description: "Lists files and directories.",
    minPerm: Permission.USER,
    run: ({ content, currentDir, setStack }) => {
        if (!content || Object.keys(content).length === 0) {
            setStack(prev => [...prev, {
                command: `No items found at ${currentDir}`,
                success: true,
                color: "lightblue"
            }]);
            
            return;
        }

        Object.keys(content).forEach(key => {
            const color = content[key].type === "directory" ? "blue" : "green";
            setStack(prev => [...prev, { command: key, success: true, color }]);
        });
    }
},
```
