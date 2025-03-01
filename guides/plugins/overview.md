# Overview

The variety of Shopware's extension interfaces can be overwhelming, so let's start with a simple overview comparing the three approaches **Plugins**, **Themes** and **Apps**.

| Task | Plugin | Theme | App | Remarks |
| :--- | :--- | :--- | :--- | :--- |
| Change storefront appearance | ✅ | ✅ | ✅ |  |
| Add admin modules | ✅ | ❌ | ✅ |  |
| Execute Webhooks | ✅ | ❌ | ✅ | Apps main functionality is to call Webhooks, but Plugins can be implemented to do that as well. |
| Add custom entities | ✅ | ❌ | ✅ |  |
| Modify database structure | ✅ | ❌ | ❌ |  |
| Integrate payment providers | ✅ | ❌ | ✅ |  |
| Publish in the Shopware Store | ✅ | ✅ | ✅ |  |
| Install in Shopware 6 Cloud Shops | ❌ | ❌ | ✅ |  |
| Install in Shopware 6 self-managed Shops | ✅ | ✅ | ✅ | Apps can be installed and used since Shopware 6.4.0.0 |
| Add custom logic/routes/commands | ✅ | ❌ | ✅ | Apps extract functionalities/logic into separate services, so technically they can add custom logic |
| Control order of style/template inheritance | ❌ | ✅ | ✅ |  |

## Plugins

Plugins are the most powerful extension mechanism as they can be used to extend, overwrite and modify almost any part of the software. At the same time, obviously, they can also be the most harmful for the same reasons. If you make profound changes or complex functionalities such as e.g

* Custom price calculation
* Product imports
* Custom Content/Products
* Connecting 3P identity providers
* Dynamic validations
* Customer tracking

You will probably need to write a plugin for that. Follow our [Plugin Base Guide](plugins/plugin-base-guide.md) to learn how to develop a plugin. See the [Plugin Fundamentals](plugins/plugin-fundamentals/) section below for more examples.

{% hint style="info" %}
If your extensions do not require any of the above, but rather design changes, a template tweak might ideally be appropriate.
{% endhint %}

## Themes

A theme lets you perform the tasks listed below.

* Template overrides
* Custom styles
* Configuration interfaces
* Control the order in which styles and templates are loaded

Technically, plugins and themes are very similar and overlap in most of their logic. However, some special aspects are handled differently, such as template and style priority or their activation. Once plugins are installed and activated, their styles and templates are applied immediately. If a theme is installed, it must first be selected in the theme manager.

{% hint style="info" %}
Note that a plugin can also override templates.
{% endhint %}

To get started with your first theme, follow our [Theme Base Guide](themes/theme-base-guide.md).

## Apps

Operation in cloud environments is not possible due to the aspects listed under [Plugins](overview.md#plugins). Therefore, a different, less intrusive pattern was introduced. Apps enable event-based integrations that communicate with external services via a synchronous API.

Most of the app's logic resides in this third-party service, so developers must ensure that they handle the details of the API and provide their service with appropriate security, protection, and reliability. While it comes with these responsibilities, you are free to choose which operating environment, framework or programming language you wish to use as long as our [guidelines for Shopware apps](apps/app-base-guide.md) are followed.

Apps also provide theme support, so all the features of [Themes](overview.md#themes) are also available for apps. Payments are also supported by apps and the user can be forwarded to a payment provider.
