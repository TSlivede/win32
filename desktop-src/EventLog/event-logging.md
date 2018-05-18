---
Description: 'Many applications record errors and events in proprietary error logs, each with their own format and user interface.'
ms.assetid: '2a625c8a-afa2-484a-a0e3-df3ef774abe4'
title: Event Logging
---

# Event Logging

Many applications record errors and events in proprietary error logs, each with their own format and user interface. Data from different applications can't easily be merged into one complete report, requiring system administrators or support representatives to check a variety of sources to diagnose problems.

Event logging provides a standard, centralized way for applications (and the operating system) to record important software and hardware events. The event logging service records events from various sources and stores them in a single collection called an *event log*. The Event Viewer enables you to view logs; the programming interface also enables you to examine logs.

-   [About Event Logging](about-event-logging.md)
-   [Using Event Logging](using-event-logging.md)
-   [Event Logging Reference](event-logging-reference.md)

> [!Note]  
> The Event Logging API was designed for applications that run on the Windows Server 2003, Windows XP, or Windows 2000 operating system. In Windows Vista, the event logging infrastructure was redesigned. Applications that are designed to run on Windows Vista or later operating systems should use [Windows Event Log](https://msdn.microsoft.com/library/windows/desktop/aa385780) to log events.

 

 

 


