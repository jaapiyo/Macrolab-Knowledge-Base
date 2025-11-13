Show additional windows with regular decoration (Windows frame + Close button) and prevent auto merging to the main viewport
```cpp
io.ConfigViewportsNoDecoration = false;
io.ConfigViewportsNoAutoMerge = true;
```
From: https://github.com/ocornut/imgui/issues/3680