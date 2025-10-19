---
layout: learning
title: "C++ notes and reference materials"
status: "In Progress"
description: "Here I put all my notes and reflections on the language, cool resources on C++ and beyond."
---

Cherno C++ series: `52/111`

# Resources

# Useful Stuff

> Getting an offset using `->` operator.
```cpp
struct Vector3
{
    float x, y, z;
};

int offset = (int)&((Vector3*)0)->x; // x, y, z
```

# TODO:

- [] Virtual Functions performance cost (V Table)
- [] Placement new(*place in memory*) and optimization using it.