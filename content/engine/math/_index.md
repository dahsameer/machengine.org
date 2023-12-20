---
title: "Math"
description: "Math is hard enough as-is, without you having to question ground truths while problem solving. As a result, Mach's math library is opinionated "
draft: false
layout: "docs"
docs_type: "engine"
rss_ignore: true
---

# Mach's math library is opinionated

Math is hard enough as-is, without you having to question ground truths while problem solving. As a result, Mach's math library takes a more opinionated approach than some other math libraries: we try to encourage you through API design to use what we believe to be the best choices. For example, other math libraries provide both LH and RH (left-handed and right-handed) variants for each operation, and they sit on equal footing for you to choose from; mach.math may also provide both variants as needed for conversions, but unlike other libraries will bless one choice with e.g. a shorter function name to nudge you in the right direction and towards _consistency_.

## Matrices

* Column-major matrix storage
* Column-vectors (i.e. right-associative multiplication, matrix * vector = vector)

The benefit of using this "OpenGL-style" matrix is that it matches the conventions accepted by the scientific community, it's what you'll find in linear algebra textbooks. It also matches WebGPU, Vulkan, Unity3D, etc. It does NOT match DirectX-style which e.g. Unreal Engine uses.

Note: many people will say "row major" or "column major" and implicitly mean three or more different concepts; consider reading the [matrix storage docs](matrix-storage).

## Coordinate system (+Y up, left-handed)

* Normalized Device coordinates: +Y up; (-1, -1) is at the bottom-left corner.
* Framebuffer coordinates: +Y down; (0, 0) is at the top-left corner.
* Texture coordinates:     +Y down; (0, 0) is at the top-left corner.

This coordinate system is consistent with WebGPU, Metal, DirectX, and Unity (NDC only.)
