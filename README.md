# flat2dpy

A collection of flat 2d classes with math and helpers.

# flat2d

The main module which contains available flat2d classes and submodules

## Flat2dSequnece, Flat2dWritableSequnece and Flat2dMutiableSequnece

These are flat2d abstract classes.  Flat2dSequnece is read only, Flat2dWritableSequnece is writable but may not change shape, and Flat2dMutiableSequnece may change shape.  You can buid your own subclass from these and the flat2dmixins.  Most of the existing flat2d class only support a single native item type, but it is posible to build your own using the <object> type as the item type.  Any additonal restraints must be built in by your own implemented methods, however there are several hooks available to make this easy.  If you plan to change or implement additonal features into your custom flat2d class you should read looks at the mixins and hooks.

## Flat2dArray

a flat2d array (array.array) class.

