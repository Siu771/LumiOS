---
icon: code-branch
---

# Versions

Lumi OS has four main groups of versions:

v1-v5.1, v6v-v10, v11-v12.5, **v14+**

{% hint style="info" %}
The source code for earlier versions were NOT saved. The code was directly updated.
{% endhint %}

For information regarding creating your own version, please see [creating your own OS](docs/creating-content/creating-your-own-os.md).

***

#### v1-v5.1

v1-v5.1 were updated in relative quick succession and had the code directly updated. It heavily relied on the localstorage and did not have any long-term saving support. Most apps were also pure decoration.

* [v1 ](https://fritzcohen.github.io/LumiOS/old/LumiOS.html)
* [v2](https://fritzcohen.github.io/LumiOS/old/LumiOS.v2.html)
* [v2.1](https://fritzcohen.github.io/LumiOS/old/LumiOS.v2.1.html)
* [v3](https://fritzcohen.github.io/LumiOS/old/LumiOS.v3.html)
* [v4](https://fritzcohen.github.io/LumiOS/old/LumiOS.v4.html)
* [v4.1](https://fritzcohen.github.io/LumiOS/old/LumiOS.v4.1.html)
* [v4.2](https://fritzcohen.github.io/LumiOS/old/LumiOS.v4.2.html)
* [v4.3](https://fritzcohen.github.io/LumiOS/old/LumiOS.v4.3.html)
* [v4.5](https://fritzcohen.github.io/LumiOS/old/LumiOS.v2.1.html)
* [v5](https://fritzcohen.github.io/LumiOS/old/LumiOS.v5.html)
* [v5.1](https://fritzcohen.github.io/LumiOS/old/LumiOS.v5.1.html) ([Source](https://github.com/FritzCohen/LumiOS/tree/v5.1))

***

#### v6-v10

v6-v10 were built with typescript for the first time. The indexed DB actually had a use during this time, but providers managed taskbar and desktop states, which caused plently of issues. Saving to the DB also sometimes failed, losing all progress.

* [v6](https://fritzcohen.github.io/LumiOS/old/LumiOS.v6.html)
* [v7](https://fritzcohen.github.io/LumiOS/old/LumiOS.v7.html)
* [v7.5](https://fritzcohen.github.io/LumiOS/old/LumiOS.v7.5.html)
* [v8](https://fritzcohen.github.io/LumiOS/old/LumiOS.v8.html)
* [v9](https://fritzcohen.github.io/LumiOS/old/LumiOS.v9.html)
* [v10](https://fritzcohen.github.io/LumiOS/old/LumiOS.v10.html) ([Source](https://github.com/FritzCohen/LumiOS/tree/v10))

***

#### v11-v12.5

v11 was built ground up since the provider system from v6-v10 caused too much confusion, and it was too difficult to implement new apps. However, even this quickly grew too complicated for myself and I had to upgrade it again.

{% hint style="info" %}
v11 is special since it uses the file handle instead of Indexed DB. It works fine, but it requires too much user verification, and likely to the cost of attention spans.
{% endhint %}

* [v11](https://fritzcohen.github.io/LumiOS/old/LumiOS.v11.html)
* [v12](https://fritzcohen.github.io/LumiOS/old/LumiOS.v12.html)
* [v12.1](https://fritzcohen.github.io/LumiOS/old/LumiOS.v12.1.html)
* [v12.5](https://fritzcohen.github.io/LumiOS/old/LumiOS.v12.5.html) ([Source](https://github.com/FritzCohen/LumiOS/tree/v12.5))

#### v14+

The latest version of the OS. This is likely the best version yet, as it doesn't heavily rely on providers but instead the virtualFS directly. The app and extension system was heavily reworked, allowing for more customizability.

{% hint style="info" %}
v13 was skipped since its considered an "unlucky" number.
{% endhint %}

* [v14](https://fritzcohen.github.io/LumiOS/old/LumiOS.v12.5.html) ([Source](https://github.com/FritzCohen/LumiOS/tree/v14))
* [v15](https://fritzcohen.github.io/LumiOS/old/LumiOS.v15.html) ([Source](https://github.com/FritzCohen/LumiOS/tree/v15))
