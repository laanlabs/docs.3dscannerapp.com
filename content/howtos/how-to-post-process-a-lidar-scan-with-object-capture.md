---
category: scanning
title: How to Process a LiDAR Scan with Apple's Object Capture / Photogrammetry
description: Recover more detail and precision from your LiDAR scans
createdAt: 2020-12-28T00:05:42.370Z
---


#### Overview
Post processing LiDAR scans can in some cases improve detail, precision, and texture quality. 
Though it's not guaranteed to work as well as capturing HD photos using ["Photos Mode"](/howtos/how-to-enable-photo-mode-cloud-processing)

</br>

#### 1. Enable beta access to the Photos mode from iOS 3dScannerApp for iOS 

[Read this article](/howtos/how-to-enable-photo-mode-cloud-processing) on how to enable Photo mode. 
This step is required before you can post process LIDAR scans.

Once enabled, you can process old or new LiDAR scans in the cloud, or on your mac desktop.


#### 2. Process an existing LiDAR Scan in the Cloud 

Navigate to an existing LiDAR scan. 

Tap "Process" in the bottom of the screen. 
You will notice a small cloud icon in the upper right of the process action sheet.
Tap it to display the Photo mode process UI. 
From here you can choose to process locally on your compatible Mac computer, or in the cloud. 

<img width="260" src="/images/cloud-process-lidar-scan.jpg"/>

</br>
</br>

#### What is Photos Mode? 
'Photos' mode takes a series of images and processes them into a detailed 3d model with real-world scale.
Processing must be done in the cloud, or on a compatible Mac desktop.

#### Notes and Issues
Since Photo processing simply uses the existing low resolution images captured during a LiDAR scan, it's not always
possible to recover a higher quality mesh via cloud processing. 
To increase the chances of good reconstructions, try capturing your LIDAR scans more slowly to gather more images 
with overlapping viewpoints. Also you can loop over the same area twice ( which is normally detrimental to LIDAR scans, but helps in Photo mode )
You can learn more about Photogrammetry here:

https://www.vertexlibrary.com/guide-to-3d-scanning-outdoor-photogrammetry-tips

https://www.artec3d.com/learning-center/what-is-photogrammetry

"A guide covering Photogrammetry including the applications, libraries and tools..."
https://github.com/mikeroyal/Photogrammetry-Guide


</br>

</br>




