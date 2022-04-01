---
createdAt: 2021-12-28T00:05:42.370Z
title: Fix a scan that crashes during load
--- 
## How to Fix a scan that crashes during load

If you processed a large scan that crashed during processing, and now will no longer open without crashing, follow these steps.

You can remove the intermediate data so that you can possibly re-process the scan with a lower resolution.

Tap the "..." button on your scan from the scans list view:

<img width="230" src="/images/scans-list-view-tap-more.jpg"/>

Now tap the "Delete Model" button:
<img width="230" src="/images/scans-list-tap-delete-model.jpg"/>

Now tap "Refined Mesh" or "Textured Mesh", you may have to remove both to clear out the large intermediate scan.

NOTE: Do not tap "All Data"

<img width="230" src="/images/scan-delete-textured-mesh.jpg"/>

Now you should be able to open your scan and re-process. 
Note that the scan will appear un-textured after removing this data. 
You can tap the 'Process' button from the scan view.


