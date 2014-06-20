Weapon Models plugin for SourceMod
===============

This is a SourceMod plugin which allows you to change both world and view model of any weapon server-side. The plugin provides both a config file and a simple but powerful API for adding custom weapon models.

### Disclaimer ######
This is by far not intended to work by Valve, and the implementation is pretty much a hack. 

### List of compatible games ######
 * **Counter-Strike: Source**
 * **Counter-Strike: Global Offensive** - Arm model needs to be included
 * **Day of Defeat: Source**
 * **Team-Fortress 2** - Arm model and animations needs to be included

### Requirements ######
 * SourceMod 1.5 or higher
 * A model

## How to create a custom view model
In order to create a functional custom model, a few changes need to be made
to your view model. Here is the list of things of what you will have to do.

1. Decompile your desired view model with a MDL decompiler.
2. Open the QC file generated by the decompiler, and select all $sequence keys, copy and paste them directly after.
3. To prevent name conflicts, add an underscore in front of all the copied sequence names, from example idle to _idle. However, do not change name of the quoted string that is directly after.
4. Remove the activity associated with all the copied sequences. The activity name always starts with "ACT_VM_" and is then followed by a number, remove both of those.

*If you followed the last steps correctly, a copied sequence should look something like this:*

Before:
```
$sequence shoot1 "shoot1" ACT_VM_PRIMARYATTACK 1 fps 60.00 {
    { event 5001 0 "31" }
    { event 6002 2 "0" }
}
```
After:
```
$sequence _shoot1 "shoot1" fps 60.00 {
    { event 5001 0 "31" }
    { event 6002 2 "0" }
}
```
