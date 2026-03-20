# Apps

Apps are the backbone of the entire OS. Apps can be opened by a call to `openApp(executable)` from the Kernal.tsx hook, or through the [API](../api.md).

Here is an example call to open an app:

```typescript
openApp({
    config: {
        name: "ExampleComponent",
        displayName: "Example Component",
        permissions: 0,
        icon: "",
    },
    mainComponent: (props) => <Example {...props} />
});
```

You might notice in the example above that the opening call has two name attributes. name _should_ have no spaces, and displayName _should_ have spaces, although these changes are fairly redundant, and they can be the exact same.

### Structure

```typescript
export interface Executable {
  config: {
    name: string;
    displayName: string;
    permissions: Permission;
    icon: string | IconDefinition;
    version?: string;
    description?: string;
    onCompleteHandler?: (result?: any) => void; // optional callback for returning results
    [key: string]: any;
  };
  mainComponent: React.FC<any> | (() => ReactNode | string);
}
```

**Permissions** is the level at which the component can make changes to the OS, pretty much if it has admin access or not.

**icon** is what will be displayed when the component is opened in either the taskbar, topbar or window. If the file is on the taskbar (or desktop) and the same app is opened with a different icon, it will defer to the icon saved more directly.

_**version**_ is the current version of the app. While you _should_ keep track of this when you make apps, the OS does not currently do this.

_**description**_ is a description of an app, which is shown in Settings.&#x20;

_**onCompleteHandler**_ was an attempt to get whether or not a component returns true for a given task. This was later replaced, and is now deprecated.

***

#### Main Component

The main component can either be a string (for html as a text string to be displayed) or a react component. Please write the react component in the form `(props) ⇒ <Component { ...props } />` . In the child component, props takes on a new form, that being the `OpenedApp` interface, with `executable` as a subprop.

#### Popups

Popups are just apps that resize themselves to be smaller. In earlier versions popups were displayed through their own separate system, but it proved redundant.

Popups also typically use the `<Popup>...<Popup/>` component as it provides extra utilities that could be useful since they are **not** full apps.

Here is an example popup call:

```typescript
const result = await openApp({
	config: {
		name: "Verify User",
		displayName: "Verify User",
		permissions: 0,
		icon: "",
	},
	mainComponent: (props) => (
		<VerifyUserPopup
			props={props}
			intent="Modify new user props"
			{...props}
		/>
	),
});
```

Take note of how `openApp({...});` can return a value. In the case above, true or false whether or not the user verifies themself.&#x20;

***

### Making Your own App

There are two main pathways into making your own app.&#x20;

1. Creating the app through app creator
2. Building through react itself

You might want to use react if you need access to specific APIs and a higher level of customizablity not alloted by traditional HTML.

#### For HTML

{% stepper %}
{% step %}
Open app creator


{% endstep %}

{% step %}
Customize the settings to your needs


{% endstep %}
{% endstepper %}

#### For React

{% stepper %}
{% step %}
Create the component in the Apps folder


{% endstep %}

{% step %}
Add component to the component registry


{% endstep %}

{% step %}
Add the app executable into the `defaultFS`, into the `Default` user folder found under `Users/`


{% endstep %}

{% step %}
Rebuild the OS for production - or development


{% endstep %}
{% endstepper %}

