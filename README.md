# Objective-C KVO Crash Bug

This repository demonstrates a common bug encountered when using Key-Value Observing (KVO) in Objective-C. The bug occurs when an observed object is deallocated while observers are still registered. This leads to a crash because the observer attempts to access memory that has been freed.

## Bug Description
The provided code shows a simple example where an observer is added to an object.  The observed object is then deallocated, but the observer remains registered. When KVO attempts to notify the observer, it tries to access the deallocated object, causing a crash.

## Solution
The solution involves removing the observer in the observed object's `dealloc` method, or using `removeObserver:forKeyPath:` before the object is deallocated.  This prevents the observer from trying to access freed memory.