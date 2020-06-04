# flat2dpy

A collection of flat 2d classes with math and helpers.  You can think of the classes provided for this module as sumpy or scupy ndarray replacements except they are for use with 2d sequneces and do not support single or more then 2 dimentsions, so if you intention is other then 2 dimensions you would probably be better off with numpy or scipy.  Note that 2 dimensions referse to rows and columns with an assumed depth of 1.  3d and 4d coordinates are both supported as they have 2 dimensions.

Why the name flat2d?  Because arrays are actually flat but used as 2d arrays.  This means items referred to by a single inde or slice are treated as flat, but when referred to by 2 indexes or slices they are tread as having 2 dimensions.  

## compatibility

A major different with most other similar modules where single indexes or slices are treated a row index with all columns of that row.  Hence one must becareful when using flat2d as a drop in replacement.  To maintain numpy or scipy compatiablility you can use None for the column range, fe. f2da[0,None] will reference as (0, slice(Noe, None, None)

# flat2d

The main module which contains available flat2d classes and submodules

## Flat2dSequence, Flat2dWritableSequence and Flat2dMutableSequence

These are flat2d abstract classes.  Flat2dSequence is read only, Flat2dWritableSequence is writable but may not change shape, and Flat2dMutableSequence may change shape.  You can buid your own subclass from these and the flat2dmixins.  Most of the existing flat2d class only support a single native item type, but it is posible to build your own using the <object> type as the item type.  Any additonal restraints must be built in by your own implemented methods, however there are several hooks available to make this easy.  If you plan to change or implement additonal features into your custom flat2d class you should read looks at the mixins and hooks.

## Flat2dMath

This abstract class is a math support mixin class to convert oprator methods into item operator functionality.  Without this implementing this class Flat2Seuence operatators are limited to and behave the same as Sequence oprators __add__ and __mul__.

## Flat2dView

A proxy class which inherits from Flat2dSequence and acts as a proxy wrapper for any Flat2dSequence subclass instance.

## Flat2dArray

A flat2d array (array.array) class.

## Flat2dCType

Not yet implemented and although it will offer a much wider range of

