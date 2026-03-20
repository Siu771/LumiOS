# BIOS Commands

Bios commands are extremely similar to regular [Commands](commands.md), but they are structured through the file system itself. The Bios itself hasn't been fully introduced yet, so click [here](../../extras/hidden-content.md) for more info.

Here is the default file structure, hopefully this gives context as to what the Bios structure looks like:

```
Root/
    /System
        /BiosCommands
            exit.biosCommand
            /Theme
                reset-theme.biosCommand
            /Troubleshoot
                diagnostics.biosCommand
```

Exit is unique in that it fully backs out of the Bios. By default, accessing the sub-directories will show a "Back" button that navigates up one directory.

{% hint style="info" %}
Just like regular commands, the run function is also stringified.
{% endhint %}

```typescript
interface BiosCommand {
    id: string;
    label: string;
    description?: string;
    run: (ctx: BiosContext) => Promise<void> | void;
}
```

Here is an example BiosCommand that can be copied easily:

```typescript
{
  id: "Example",
  label: "Runs an example command",
  run: async () => {
    console.log("Example executed!");
  },
}
```

You may also notice in the Bios folder in the source code that files are structured differently, instead of a single map it builds the directories through some other steps.&#x20;
