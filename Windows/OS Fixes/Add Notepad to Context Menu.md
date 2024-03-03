Add open with notepad to context menu.

Registry editor.
HKEY_CLASSES_ROOT\*\shell

Next, you’ll create a new key inside the shell key. Right-click the shell key and choose New > Key. Name the new key “Open with Notepad.”

Now, you’re going to create another new key inside that one. Right-click the new Open with Notepad key and choose New > Key. Name the new key “command.”

With the new command key selected, in the right-hand pane, double-click the (Default) value to open it’s properties page.
In the “Value data” box, type the following text and then click “OK.”
notepad.exe %1