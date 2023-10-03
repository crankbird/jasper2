---
layout: post
current: post
cover: 'assets/images/advanced.jpg'
navigation: true
title: What cloud storage can learn from mainframes
date: 2023-09-02 10:18:00
tags: [cloud, datamanagement]
class: post-template
subclass: 'post'
author: ricky
---

# Test Heading

What can the experience of managing IBM mainframes teach us about designing storage for public or private cloud computing? Plenty, it turns out...

In my previous post, Designing Cloud Storage? Ditch the LUN!, I pointed out the challenges of using LUNs for virtual and cloud storage environments that need to scale.

That post, and my thinking around storage management in general, were both influenced by a nine-year-old blog post by John Tyrrel: The Next Step In Virtualization. When Tyrell wrote that, the next step in virtualization was to ditch the LUN, virtualization was still pretty cutting edge. Yet, here we are, almost a decade later, and we're still using LUNs as the storage container for most server virtualization infrastructures.

The article was way ahead of its time, and it includes one of my favorite quotes about LUNs (if you can have such a thing):

If your business has the potential for real growth, the LUN becomes a major inhibitor in your path. On top of that, the LUN is just plain nasty, and your mother definitely would not approve of you using it.
Aside from pithy quotes, the article contained two points that convinced me he was right.

The first was this observation, from studies conducted by IBM in early-1980s mainframe environments:

There was a one-to-one correspondence between the number of islands of storage to manage and the number of space failures, performance bottlenecks, job restarts/reruns, and the number of people to manage the storage.
In much the same way, each additional LUN becomes a new island of storage to manage.

The second was that moving to an advanced, pool-based method of allocating storage resulted in a 10,000x improvement in storage management productivity. This wasn't a funky marketing number pulled out of thin air, but the real, measured experience of what happened when they stopped using storage management techniques that look disturbingly like the LUN-based practices that most IT shops still use.

This isn't to say that that Fibre channel is bad, or that block-based storage is inherently evil. For example, Ceph's RBD is a block device built on top of its RADOS object store. It provides snapshots, copy-on-write cloning, and a bunch of other cool features, but this isn't achieved by being limited to LUNs.

A well designed file system—or object based storage repository like RADOS—provides a foundation for software defined storage containers that's much more flexible than LUNs. This is because the containers are designed to be completely separated from the underlying hardware. When compared to a LUN, they're about as close to “magical” as storage gets.

A case in point: A storage array that can handle 100,000 LUNs is a very rare (and expensive) thing, whereas a consumer-grade NAS device you can buy at a local computer store for as little as $100 can easily store many times that number of virtual-machine containers. Additionally, the amount of training required to manage a filesystem with 100,000 files is trivial in comparison to the training required to manage a SAN capable of storing 100,000 LUNS.

Regardless of whether you are using open source systems like RBD, or various proprietary implementations of flexible volumes, these magic, non-LUN storage containers provides data storage that match the needs of highly virtualized infrastructures. For example:

Leverage a data fabric to simplify and streamline data management
SponsoredPost Sponsored by HPE

Leverage a data fabric to simplify and streamline data management

Then capitalize on real-time insights for innovation and growth

When you need a new one you just give it a name, a size, and point it at the physical pool you want it to start its life in. A second later, and you're done.
Unlike LUNs they're elastic: If you got the size wrong, you can grow them, or shrink them. In some implementations, you can even have that happen for you automatically, as space is consumed or released by applications over time.
You can reserve space for them, or you can provision them completely "thin".
You can set and change quality-of-service performance and capacity policies for them.
You can copy them or move them to different physical pool.
You can set backup policies for them and back them up and restore them.
In the better implementations, every one of those operations is instantaneous, no matter how big or how busy the containers may be, and every one of those things can be done from a GUI, a command line, or even programmatically via an API or shell script.

To be sure, in some of the more advanced arrays, a number of these things can be done with LUNs, but those arrays all use something that looks and smells like lot like a filesystem. The problem is this: By using a LUN as the storage container presented to the application, they miss the opportunity to exploit the full power of the underlying data store, and the complexity of LUN management becomes almost impossible to deal with at large scale.

If the storage industry really wants to help enterprise customers make the transition to cloud-based infrastructure, it's time we learned some lessons from our mainframe predecessors.

When designing storage for private or public clouds, it's time to go beyond just giving the server infrastructure a bunch of disks at the end of a network in the form of a LUN.

The time has come to ditch the LUN!

from - <https://www.computerworld.com/article/2475123/a-better-way-to-design-cloud-storage--learn-from-mainframes.html>
