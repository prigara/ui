---
title: Toggle button
category: Controls
---
The toggle button is used to switch between On and Off states.

![]({{site.baseurl}}/images/toggle_button/example.png)

## When to use

Use the toggle button to switch the state of an item in search results:
    ![]({{site.baseurl}}/images/toggle_button/example_se.png)


Do not use the toggle button for items in dialogs and menus. Instead, use a checkbox in dialogs and a checkmark in menus:
   ![]({{site.baseurl}}/images/toggle_button/when_to_use_dialog_or_menu.png)


## How to use

### Label
The toggle button in search results should duplicate the option from the settings or the menu. Label and capitalization should be the same as on the option label:
    ![]({{site.baseurl}}/images/toggle_button/label_checkbox.png)
    *Setting in the preferences*
    ![]({{site.baseurl}}/images/toggle_button/label_checkbox_se.png)
    *The same setting in search results*
Do not make a setting available only from search results. See [discoverability]({{site.baseurl}}/principles/Discoverability) for details.

If the setting is in a tree or menu, use the toggle button label to specify where the setting is located:
    ![]({{site.baseurl}}/images/toggle_button/label_tree.png)
*Setting in a tree*
    ![]({{site.baseurl}}/images/toggle_button/label_tree_se.png)
*The same setting in search results; separate tree levels with a colon*
    ![]({{site.baseurl}}/images/toggle_button/label_menu.png)
*Setting in the main menu*
    ![]({{site.baseurl}}/images/toggle_button/label_menu_se.png)
*The same setting in search results; separate the first menu level with a vertical bar, and separate others with a colon*
    Refer to [checkbox]({{site.baseurl}}/controls/checkbox) and [menu]({{site.baseurl}}/controls/menu_list) for writing checkbox labels and menu labels.

Do not add the word "On" or "Off" to the item name, since the state description is already in the toggle button.


### Control
Toggle button is implemented with the `com.intellij.ui.components.OnOffButton` class. But generally, you shouldn't use the class directly. The IDE automatically places the buttons in the search feed if you follow one of the patterns described below:


1. If this is a system or editor or another kind of settings, just register corresponding `BooleanOptionDescription` for the option. The options can be bound (but not limited) to:

   - A `SearchHitProvider` instance which is registered in PlatformExtensions.xml with the <search.topHitProvider implementation="fq.class.name"/> tag. For example, see the `com.intellij.ide.ui.SystemOptionsTopHitProvider` class that represents matching of "Reopen last project on startup" checkbox to BooleanOptionDescription.

   - `com.intellij.ide.ui.EditorOptionDescription` bound to `com.intellij.openapi.editor.ex.EditorSettingsExternalizable` which under the hood works with the editor.xml.
2. Implement your own action that's inherited from `com.intellij.openapi.actionSystem.ToggleAction` and registered in the IDE's PlatformActions.xml or plugin.xml.



The toggle button changes state when it is clicked with the mouse or when <kbd>Enter</kbd> is pressed on the item line.


## Style

<table>
<col width="21%">
<col width="22%">
<col width="22%">
<col width="22%">
<col width="22%">
    <tr>
        <td>  </td>
        <td style="margin-left: 20px"> Mac OS, IntelliJ </td>
        <td> Windows </td>
        <td> Darcula </td>
    </tr>
    <tr>
        <td> <p style="color: #999999; margin-top: -5px;"> On </p></td>
        <td> <img src="{{site.baseurl}}/images/toggle_button/on_mac.png" style="margin: -5px 0 0 0"></td>
        <td> <img src="{{site.baseurl}}/images/toggle_button/on_win.png" style="margin: -5px 0 0 0"></td>
        <td> <img src="{{site.baseurl}}/images/toggle_button/on_dark.png" style="margin: -5px 0 0 0"></td>
    </tr>
    <tr>
        <td> <p style="color: #999999; margin-top: -5px;"> Off </p></td>
        <td> <img src="{{site.baseurl}}/images/toggle_button/off_mac.png" style="margin: -5px 0 0 0"></td>
        <td> <img src="{{site.baseurl}}/images/toggle_button/off_win.png" style="margin: -5px 0 0 0"></td>
        <td> <img src="{{site.baseurl}}/images/toggle_button/off_dark.png" style="margin: -5px 0 0 0"></td>
    </tr>
</table>

