---
layout: learning
title: "C++ notes and reference materials"
status: "In Progress"
description: "Here I put all my notes and reflections on the language, cool resources on C++ and beyond."
---

Cherno C++ series: `72/111`

# Resources

[C++ Best Practices Book](https://annas-archive.org/md5/f382be00598c02063e6ecd1d2b215ca7)
[C++ Concurrency in Action]()
[C++ Design Patters]()
[TCP/IP Illustrated volume 1]()

[Valueable chapters in books, by Coding Jesus](https://docs.google.com/spreadsheets/d/1EKx2EDRyNxdVoRrUljeKKdG0G-XeJiR9xMb4Xa-ernk/edit?gid=0#gid=0)

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