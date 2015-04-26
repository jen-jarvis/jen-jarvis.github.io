---
layout: post
title: Faster Polynomial Multiplication
author: steve_jarvis
excerpt: How to do polynomial multiplication faster with use of the discrete fast fourier transform.
tags: [computer science, FF, DFF, FFT, DFFT, fourier, polynomial multiplication]
comments: true
image:
  feature: header.jpg
---

$$FFT^{-1}(12, -3-3i, -2, -3+3i)$$
    $$\omega_n = e^{\frac{-2\pi i}{4}}$$
    $$\omega = 1$$
    $$a^0 = (12, -2)$$
    $$a^1 = (-3-3i, -3+3i)$$

    $$c^0 = FFT^{-1}(12, -2)$$
        $$\omega_n = e^{\frac{-2\pi i}{2}}$$
        $$\omega = 1$$
        $$a^0 = (12)$$
        $$c^0 = FFT^{-1}(12)$$
        return 12
    $$a^1 = (-2)$$
    $$c^0 = FFT^{-1}(-2)$$
        return -2
	$$c_0 = 12 + 1*(-2) = 10$$
	$$c_1 = 12 - 1*(-2) = 14$$
	$$\omega = e^{\frac{-2\pi i}{2}}$$
	return $$(10,14)$$ for $$FFT^{-1}(12,-1)$$, where $$c_0^0 = 10$$ and $$c_1^0 = 14$$

$$c^1 = FFT^{-1}(-3-3i, -3+3i)$$
	$$\omega_n = e^{\frac{-2\pi i}{2}}$$
	$$\omega = 1$$
	$$a^0 = (-3-3i)$$
	$$c^0 = FFT^{-1}(-3-3i)$$
        return $$-3-3i$$
	$$a^1 = (-3+3i)$$
	$$c^0 = FFT^{-1}(-3+3i)$$
        return $$-3+3i$$
	$$c_0 = -3-3i + 1*(-3+3i) = -6$$
    $$c_1 = -3-3i - 1*(-3+3i) = -6i$$
    $$\omega = e^{\frac{-2\pi i}{2}}$$
    return $$(-6,-6i)$$ for $$FFT^{-1}(-3-3i, -3+3i)$$, where $$c_0^1 = -6$$ and $$c_1^1 = -6i$$

$$c_0 = 10 + 1*(-6) = 4$$
$$c_2 = 10 - 1*(-6) = 16$$
$$\omega = 1*(e^{\frac{-2\pi i}{4}}) = -i$$
$$c_1 = 14 + (-i)(-6i) = 14 - 6 = 8$$
$$c_3 = 14 - (-i)(-6i) = 14 + 6 = 20$$
$$\omega = -i*(e^{\frac{-2\pi i}{4}}) = e^{-\pi i} = -1$$
$$c = \frac{1}{4}(4, 8, 16, 20) = (1, 2, 4, 5)$$
return $$(1, 2, 4, 5)$$

Therefore, $$FFT^{-1}(12, -3-3i, -2, -3+3i) = (1,2,4,5)$$.
