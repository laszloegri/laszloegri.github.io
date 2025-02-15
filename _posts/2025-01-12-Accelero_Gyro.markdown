---
layout: post
title: "Implementing and Improving Existing Accelerometer and Gyroscope Calibration Algorithms (project, also includes improving some known approaches)"
published: true
categories: projects
permalink: /accelero_gyro/
image0: /assets/images/accelero_calibration.png

common_media_height: 200
attachments:
  - type: image
    src: /assets/images/accelero_calibration.png
  - type: video
    src: /assets/animations/low/gyro_rotation_axes.mp4
  - type: video
    src: /assets/animations/low/accelero_gyro_intertriad_calibration.mp4
  - type: link
    href: "https://www.wearnotch.com"
    text: "Visit Notch."
---

In this project, the primary objective was to calibrate the accelerometer and gyroscope of an Inertial Measurement Unit (IMU) and ensure that both sensors’ coordinate axes are properly aligned. I implemented the accelerometer calibration algorithm described, as well as an improved version of the gyroscope and inter-triad calibration algorithms developped in [\[1\]](#ref1) and [\[2\]](#ref2). (Details are limited due to contractual obligations.)

For **accelerometer calibration**, the device is placed in various orientations. From these measurements, the algorithm estimates calibration parameters, leveraging the principle that the norm of the accelerometer measurement vector is equal to the magnitude of the specific force.

Traditional **gyroscope calibration** often employs a high-precision two-axis or three-axis turntable, which can be expensive and sensitive to mechanical precision. In contrast, the method from [\[2\]](#ref2) allows calibration using only a flat surface and an object to affix the IMU onto. By manually sliding the IMU in different orientations, the approach exploits the fact that the norm of the measured gyroscope output corresponds to the rotational velocity input.

However, manual calibration may not be sufficiently precise for inter-triad alignment, making a one-axis turntable preferable. Since full technical details are provided in [\[1\]](#ref1) and [\[2\]](#ref2), below is a selection of media illustrating the implemented calibration algorithms.

<figure>
  <img src="{{ page.image0 }}" alt="Accelerometer Calibration" class="centered" style="width:50%;">
  <figcaption style="font-size:inherit;">
    Fig. 1. A demonstration of how the accelerometer measurements are corrected by the calibration.
  </figcaption>
</figure>

<figure>
  <center>
    <video width="70%" muted autoplay loop controls poster="/assets/images/video_poster.png">
      <source src="/assets/animations/high/gyro_rotation_axes.mp4" type="video/mp4">
      Your browser does not support the video tag.
    </video>
  </center>
  <figcaption style="font-size:inherit;">
    Fig. 2. The plots represent gyroscope measurements during the calibration process. The blue and red dots correspond to opposite rotation directions.
  </figcaption>
</figure>

<figure>
  <center>
    <video width="70%" muted autoplay loop controls poster="/assets/images/video_poster.png">
      <source src="/assets/animations/high/accelero_gyro_intertriad_calibration.mp4" type="video/mp4">
      Your browser does not support the video tag.
    </video>
  </center>
  <figcaption style="font-size:inherit;">
    Fig. 3. Green arrows show gyroscope-derived rotation axes, while red axes represent those derived from the accelerometer. Alignment is achieved if these axes coincide. The calibration algorithm computes a rotation that best aligns them.
    (Blue and red points represent accelerometer data collected while rotating in opposite directions.)
  </figcaption>
</figure>

## References

1. <a id="ref1"></a> **A Multi-Position Calibration Algorithm for Inertial Measurement Units**  
   *AIAA Guidance, Navigation and Control Conference and Exhibit, August 2008*  
   DOI: [10.2514/6.2008-7437](https://doi.org/10.2514/6.2008-7437)

2. <a id="ref2"></a> **Improved Multi-Position Calibration for Inertial Measurement Units**  
   Hongliang Zhang, Yuanxin Wu, Wenqi Wu, Meiping Wu, and Xiaoping Hu  
   *Measurement Science and Technology*, Volume 21, Number 1, 2010  
   DOI: [10.1088/0957-0233/21/1/015107](https://doi.org/10.1088/0957-0233/21/1/015107)
