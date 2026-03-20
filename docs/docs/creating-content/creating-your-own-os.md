# Creating your own OS

When exploring LumiOS, you may want to modify it in some way or expand it to become its own thing. Fortunately, LumiOS has several systems built in that allow for easy expansion.

This guide is only for the latest version of the OS. Older versions have many more localized checks in place, so every file could be modified in \~some\~ way.

{% hint style="info" %}
There are some guidelines to making your own version. Please see them [here](../../extras/license-guidelines.md).
{% endhint %}

### 1. Modifying Versions

Versions have to be changed to suit whatever purposes you have in mind.

Under `constants/constants.ts` modify the `CURRENT_VERSION` to be 1, or whatever version you need for your custom OS. This new version is added automatically to the `defaultFS` when loading in a new version.&#x20;

### 2. Fetching&#x20;

Lumi OS tries to update automatically and fetch changes online, to notify the user of potential updates and new features. However, some components are not handled using the global link in `constants.ts`. Make the following changes:

* `constants.ts`: Contains what should be the universal fetch link for github, but was not fully implemented. Change the link there to your own.&#x20;
* `UpdateChecker.tsx`: Change the fetch links to be the path to your repository, or simply change it to be `GITHUB_LINK + "/main/info.json"` from `constants.ts` , or some other link.
* `updateMethods.ts` : References to default fetch links
* `UpdatePopup.tsx`: References to default fetch links
* Settings: In both `System.tsx` and `Security.tsx` both contains references to the default fetch links for LumiOS.

### 3. Naming

Lumi OS (or LumiOS?) is called throughout the entirety of OS and shown to the user. For convenience, I have made it so that in `constants.ts` there is a variable called `OS_NAME`, which you can change to your hearts desire.

### 4. Extra Changes

* Comments throughout contain references to the OS, you might want to change them
* Under `src/assets/` there is the default OS logo called `no-bg-logo.png` that is used throughout the OS. Change this to your own logo.
* Index.html contains a reference to `"lumiplus"` to automatically reset the OS.
