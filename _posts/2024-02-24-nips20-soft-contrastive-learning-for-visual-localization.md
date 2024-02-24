---
title: NeurIPS20-Soft Contrastive Learning for Visual Localization
tags: Contrastive-Learning Visual-Localization
key: a2024-02-24-nips20-soft-contrastive-learning-for-visual-localization
layout: article
aside:
  toc: true
show_edit_on_github: false
mathjax: true
mathjax_autoNumber: true
mermaid: true
chart: true
# sidebar:
#   nav: sidebar
---
在图像检索领域，经常使用对比学习(Contrasive Learning)的方法来获取图像特征。

问题在于，对比学习的目标是学习出能够区分不同类别的特征，而在定位(Localization)领域，并不存在明显的类别区分，所以通常的做法是将训练数据根据某一距离阈值强行划分成正样本和负样本。 

本文认为任何基于接近性度量(Proximity measure)的人为划分方式都是不合理的，因为距离阈值附近的监督信号总是有歧义的。

为了解决这一问题，本文提出了利用软正/负分配进行对比学习。这种软分配能够在几何空间的远和近之间进行渐进的区分。

