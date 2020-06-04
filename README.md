# Current News and Status

Currently we only have documenation up.  but you can expect the actual module to be up soon, in maybe a week.  It's already at alpha status but requires some perfing, testing and more complete inline documentation.  It will be added to this repository once it's considered at a near beta status.

# License and copyright

flat2dpy uses the BSD 2-Clause License
Copyright (c) 2019, ismaelharunid.  All rights reserved.

# flat2dpy

The flat2dpy is this package containing the flat2d main module.

A collection of flat 2d classes with math and helpers.  You can think of the classes provided for this module as sumpy or scupy ndarray replacements except they are for use with 2d sequneces and do not support single or more then 2 dimentsions, so if you intention is other then 2 dimensions you would probably be better off with numpy or scipy.  Note that 2 dimensions referse to rows and columns with an assumed depth of 1.  3d and 4d coordinates are both supported as they have 2 dimensions.

Why the name flat2d?  Because arrays are actually flat but used as 2d arrays.  This means items referred to by a single inde or slice are treated as flat, but when referred to by 2 indexes or slices they are tread as having 2 dimensions.  

## compatibility

A major different with most other similar modules where single indexes or slices are treated a row index with all columns of that row.  Hence one must becareful when using flat2d as a drop in replacement.  To maintain numpy or scipy compatiablility you can use None for the column range, fe. f2da[0,None] will reference as (0, slice(Noe, None, None).

One really nice caviat is that unlink numpy ndarray, Flat2dArrays are updatable.  This means you can resize them along one or two axes, as long as the existing or incoming data will fit with it's new shape

# flat2d main module

The main module which contains available flat2d classes and submodules

## Flat2dSequence, Flat2dWritableSequence and Flat2dMutableSequence

These are flat2d abstract classes.  Flat2dSequence is read only, Flat2dWritableSequence is writable but may not change shape, and Flat2dMutableSequence may change shape.  You can buid your own subclass from these and the flat2dmixins.  Most of the existing flat2d class only support a single native item type, but it is posible to build your own using the <object> type as the item type.  Any additonal restraints must be built in by your own implemented methods, however there are several hooks available to make this easy.  If you plan to change or implement additonal features into your custom flat2d class you should read looks at the mixins and hooks.

## Flat2dMath

This abstract class is a math support mixin class to convert oprator methods into item operator functionality.  Without this implementing this class Flat2Seuence operatators are limited to and behave the same as Sequence oprators __add__ and __mul__.

## Flat2dView

A proxy class which inherits from Flat2dSequence and acts as a proxy wrapper for any Flat2dSequence subclass instance.

## Flat2dTuple

A flat2d readonly tuple class.

## Flat2dList

A flat2d mutable list class.

## Flat2dArray

A flat2d mutable array (array.array) class.

## Flat2dCType

Not yet implemented and although it will offer a much wider range of item types, it will be slow.  So if you have performance requirements then stear clear of this.  We do intend to create another subclass which will aso impliment a pipeline, so that may be more to your interest as it will remove most of the ctype calls bottleneck.

## Flat2dCTypePipeline

Not yet implemented but it will use promises to reduce ctype call overhead.  this is done by treating all operations as promises, such that results cannot be expected by any calls but dependecies are built so the final products will still be correct.  

# Usage

    from flat2d import *
    f2da = Flat2dArray(5, 2, range(10), float)
    print f2da                      # (0,1,2,3,4,5,6,7,8,9)
    print f2da + 10                 # (10,11,12,13,14,15,16,17,18,19)
    print f2da + (10,20)            # (10,21,12,23,14,25,16,27,18,29)
    print f2da + (5,(10,)*10)       # (10,11,12,13,14,15,16,17,18,19)
    print f2da + (None,2,(10,)*10)  # (10,11,12,13,14,15,16,17,18,19)
    print f2da + (5,2,(10,)*10)     # (10,11,12,13,14,15,16,17,18,19)
    print f2da + f2da               # (0,2,4,6,8,10,12,14,16,18)
    print f2da[0]                   # 0
    print f2da[:]                   # (0,1,2,3,4,5,6,7,8,9)
    print f2da[0,0]                 # 0
    print f2da[0,:]                 # (1,2,(0,1))
    print f2da[:,0]                 # (5,1,(0,2,4,6,8)
    print f2da[:,:]                 # (5,2,(0,1,2,3,4,5,6,7,8,9))
    f2da[None,:] = (10,12)          # essentailly the same as f2da.stack((10,12), 0)

# Installation

## Installing locally from cli using git

    git clone https://github.com/ismaelharunid/flat2dpy.git
    cp -r flat2dpy/flat2d /your/project/directory

