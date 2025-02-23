---
layout: post
title: "uTooth: Automated Tooth Segmentation Using 3D U-Net"
subtitle: "Using deep learning to automate forensic dental analysis"
gh-repo: PlayWeird/utooth
gh-badge: [star, fork, follow]
tags: [deep-learning, computer-vision, medical-imaging, pytorch]
comments: true
readtime: true
---

When forensic anthropologists try to identify victims using dental records, one of their biggest bottlenecks is manually segmenting teeth from CT scans. What caught my interest wasn't just the technical challenge of processing 3D medical data, but the real-world impact of speeding up victim identification.

## The Challenge

In forensic anthropology, dental analysis is crucial for victim identification. The current process involves manually segmenting teeth from CT scans - a process that takes about 10 minutes per tooth. With 32 teeth in a full adult dentition, this becomes a massive time sink when every minute counts.

## Technical Approach

### Pre-processing Pipeline

The first challenge was dealing with raw CT scan data. Unlike specialized dental scans, we were working with full-body CT scans where teeth make up a tiny fraction of the volume. The preprocessing pipeline:

1. Reads medical CT scans (DICOM format)
2. Converts values to standardized Hounsfield Units
3. Filters for bone density to isolate teeth
4. Uses spatial clustering to find the jaw region

Here's what the process looks like:

![Jaw Isolation Process]({{ site.baseurl }}/assets/img/Jaw Isolation Algorithm.png)

### The Neural Network

For this task, I chose a 3D U-Net architecture because it:
- Naturally handles 3D volumetric data
- Works effectively with limited training data
- Preserves fine spatial details important for tooth boundaries

## Results

The system achieved:
- 91.3% accuracy (Intersection-Over-Union)
- Processing time reduced from 10 minutes to seconds per tooth
- Successful segmentation of canine teeth from full-body CT scans
- Robust performance across different scan qualities

Here's a visualization of the segmentation:

![Segmentation Results]({{ site.baseurl }}/assets/img/utooth.gif)

## Impact & Next Steps

This project enables faster, more consistent dental analysis for forensic anthropology. I'm currently working on extending the model to handle all tooth types, improving robustness to metal artifacts, and creating an easy-to-use interface for forensic anthropologists.

The code is available on [GitHub](https://github.com/PlayWeird/utooth). If you're interested in forensic anthropology, medical imaging, or deep learning for volumetric data, I'd love to collaborate.