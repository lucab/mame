luaengine - Scripting MAME via its LUA interface
------------------------------------------------

== Introduction ==

Initial work of exposing a scripting interface to externally
drive MAME started in version 0.148, when a minimal luaengine
was implemented. Nowadays, the LUA interface is rich enough
to let you inspect and manipulate devices state, access cpu 
registers, read and write memory, and draw a custom HUD on screen.
However, it is still far from complete and the API is still
subject to changes.

Internally, MAME makes extensive use of 'luabridge' to implement
this feature: the idea is to transparently expose as many of 
the internal classes as possible.

== Usage ==

MAME supports external scripting via LUA (>= 5.3) scripts, either
written on the interactive console or loaded as a file.
To reach the console, just run MAME with `-console`; you will be
greeted by a naked `>` prompt where you can input your script.

To load a whole script at once, store it in a plaintext file and
pass it via the `-autoboot_script`. Please note that script 
loading may be delayed (few seconds by default), but you can
override the default with the `-autoboot_delay` argument

== Quick walktrough ==

Before starting, a warning on breaking changes: LUA API is not yet
declared stable and may suddenly change without prior notice.
However, we expose methods to let you know at runtime which API 
version you are running against, and you can introspect most of the
objects at runtime.

First

== API Reference ==

The API exposed via LUA is mostly a direct mapping of internal MAME
classes, plus some wrappers and helpers.
