---
title: Spherical Harmonics
date: 2021-11-19 15:43:48
toc: true
tags:
    - math
    - CMB
---

## **Definition**


参考 [Spherical Harmonics USCS Physics 116C Fall 2012](http://scipp.ucsc.edu/~haber/ph116C/SphericalHarmonics_12.pdf) 的第一部分来推导拉普拉斯方程在球坐标下的解，并由此引入球谐函数

\\[\color{black}Y_{\ell}^{m}(\theta, \phi)=(-1)^{m} \sqrt{\frac{(2 \ell+1)}{4 \pi} \frac{(\ell-m) !}{(\ell+m) !}} P_{\ell}^{m}(\cos \theta) e^{i m \phi} \\]

<!--more-->

下面是一个来显示不同球谐函数的脚本

{% codeblock lang:python line_number:false %}
import numpy as np
import matplotlib.pyplot as plt
from scipy.special import sph_harm
from matplotlib import cm

theta, phi = np.meshgrid(np.linspace(0, np.pi, 1000),
                         np.linspace(0, np.pi*2, 1000))
x, y, z = np.array([np.sin(theta) * np.sin(phi),
                    np.sin(theta) * np.cos(phi), np.cos(theta)])

cmap = cm.ScalarMappable(cmap=plt.get_cmap('bwr'))
def show_sph_harm(l, m):
    plt.figure()
    ax = plt.gca(projection='3d')
    sph = sph_harm(m, l, phi, theta)
    ax.plot_surface(x, y, z, facecolors=cmap.to_rgba(sph.real))
    ax.set_axis_off()
    plt.show()
{% endcodeblock %}

由球谐函数的正交完备性，我们可以将任意一个 \\(\theta\\) 和 \\(\phi\\) 的函数进行球谐展开

\\[f(\theta, \phi)=\sum_{\ell=0}^{\infty} \sum_{m=-\ell}^{\ell} a_{\ell m} Y_{\ell}^{m}(\theta, \phi)  \\]

## **Properties**

由勒让德多项式的定义，可以知道

\\[Y_{\ell}^{-m}(\theta, \phi)=(-1)^{m} Y_{\ell}^{m}(\theta, \phi)^{*} \\]


**Orthgonality**

\\[\int Y_\ell^m(\theta,\phi)Y_\{\ell^\prime\}^\{m^\prime\}(\theta,\phi)^*\mathrm{d}\Omega=\delta_\{\ell\ell^\prime\}\delta_\{mm^\prime\}\\]


**Laplace**

\\[\nabla^2 \equiv\frac{1}{\sin ^{2} \theta} \frac{\partial}{\partial \theta}\left(\sin \theta \frac{\partial}{\partial \theta}\right)+\frac{1}{\sin ^{2} \theta} \frac{\partial^{2}}{\partial \phi^{2}}\\]

\\[\color{purple} \nabla^2 Y_\ell^m(\theta,\phi)=-\ell(\ell+1)Y_\ell^m(\theta,\phi) \\]

**Addition Theorem**

\\[P_\ell(\bm{n}\cdot\bm{n}^\prime)=\frac{4\pi}{2\ell+1}\sum_m Y_\ell^m(\bm{n})Y_\ell^m(\bm{n}^\prime)^*\\]


## **Flat Sky Approximation**

平天近似就是当天区足够小的时候，可以用傅立叶变换替代球谐变换

\\[\sum_{\ell m}T_{\ell m}Y_\ell^m(\hat{\bm n}) \rightarrow \sum_{\bm{k}} T_{\bm{k}} e^{i\bm{k}\cdot\hat{\bm{n}}}\\]

在球谐变换中，不同 \\(\ell\\) 模式对应于不同尺度

\\[\ell\sim\frac{\pi}{\theta}\\]

所以从球谐变换到傅立叶变换，存在这样的替换关系

\\[ l=2\pi k \\]

[Flat_Sky_Approximation.ipynb](https://jinyiliu.github.io/html/Flat_Sky_Approximation.html)
