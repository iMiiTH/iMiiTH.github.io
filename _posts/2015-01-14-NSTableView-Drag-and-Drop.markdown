---
layout: post
title: "NSTableView Drag and Drop"
date: 2015-01-14 16:03:00
categories: general
---

When I decided to make Bookmarked, I wanted to make something that would let me log into multiple SSH accounts without having to:
1. Remember the username, server and (possible) port.
2. Cut down on the work required to do so.

I'd been previously storing accounts in ~/.ssh/config, but while it did cut down on the number of things to remember, there were sill things to remember, and remembering things is hard! Also, I had to still had to open up the Terminal, and then type in ssh *whatever* and then press enter, gross.

In reality, I was still enthusiastic about Objective-C, and wanted to make something that people would appreciate and actually use, much like Forecasted. (Although Bookmarked would be much less popular for obvious reasons. Anyways, while I was making bookmarked, I came upon a roadblock, dragging and dropping in a NSTableView. Which came after trying to save objects in NSUserdefaults, but that's another (shorter) story.

It took a long time, and searching through a lot of outdated and abandoned forum posts, when in the end, just reading the official API came to save the day. All that was needed were these three methods! 

{% highlight Objective-C %}
- (BOOL)tableView:(NSTableView *)aTableView acceptDrop:(id<NSDraggingInfo>)info row:(NSInteger)row dropOperation:(NSTableViewDropOperation)operation;
- (BOOL)tableView:(NSTableView *)aTableView writeRowsWithIndexes:(NSIndexSet *)rowIndexes toPasteboard:(NSPasteboard *)pboard;
- (NSDragOperation)tableView:(NSTableView *)aTableView validateDrop:(id<NSDraggingInfo>)info proposedRow:(NSInteger)row proposedDropOperation:(NSTableViewDropOperation)operation;
{% endhighlight %}

Just reading the API for the NSTableViewDataSource protocol gave pretty much everything, just trying to find these things were a challenge. 
