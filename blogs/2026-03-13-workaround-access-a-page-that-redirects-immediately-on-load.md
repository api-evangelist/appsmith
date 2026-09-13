---
title: "Workaround: Access a Page That Redirects Immediately On Load"
url: "https://community.appsmith.com/content/guide/workaround-access-page-redirects-immediately-load"
date: "2026-03-13"
author: "ameliaconstantin"
feed_url: "https://community.appsmith.com/rss.xml"
---
Workaround: Access a Page That Redirects Immediately On Load ameliaconstantin Fri, 03/13/2026 - 03:43 Overview If a page becomes inaccessible because a JavaScript function automatically navigates away from it during page load, you can still regain access by using the developer tools and the debugger statement. This workaround is useful when: the app has multiple pages, and at least one other page is still accessible, such as a login or home page. Root Cause A page-level script or JS Object may run on load and immediately call navigateTo() , which redirects the app before you can inspect or upd
