<div align="center">

<h2>Computer Graphics Library App</h2>

<p>
  <a href="https://github.com/Azrul16/Computer_graphics_library-app/stargazers">
    <img alt="GitHub stars" src="https://img.shields.io/github/stars/Azrul16/Computer_graphics_library-app?style=for-the-badge">
  </a>
  <a href="https://github.com/Azrul16/Computer_graphics_library-app/fork">
    <img alt="GitHub forks" src="https://img.shields.io/github/forks/Azrul16/Computer_graphics-library-app?style=for-the-badge">
  </a>
  <a href="https://github.com/Azrul16/Computer_graphics_library-app/issues">
    <img alt="GitHub issues" src="https://img.shields.io/github/issues/Azrul16/Computer_graphics_library-app?style=for-the-badge">
  </a>
</p>

<p>
  Minimal setup guide to run classic <code>graphics.h</code> / WinBGIm programs on Windows using Code::Blocks and MinGW.
</p>

</div>

---

### Files in this repository

- `graphics.h`
- `winbgim.h`
- `libbgi.a`

---

## 1. Download and Install Code::Blocks

- Download Code::Blocks installer (`.exe`) from:
  - `https://drive.google.com/file/d/1Yg1jN4tSHLdc7WDKJ8hpazwQpTk49bMT/view?usp=sharing`
- Run the installer.
- **Install in the default location** (recommended).  
  - Memorise this folder path, it will look like:

```text
C:\Program Files\CodeBlocks
```

If your path is different, just remember your own `CodeBlocks` folder.

---

## 2. Find the MinGW Folder

Inside your Code::Blocks folder, find `MinGW`, for example:

```text
C:\Program Files\CodeBlocks\MinGW
```

Inside `MinGW` you must see:

```text
bin
include
lib
```

---

## 3. Copy Graphics Files from This Repo

From this GitHub repository, copy:

- `graphics.h`
- `winbgim.h`

into:

```text
<CodeBlocks>\MinGW\include
```

Copy:

- `libbgi.a`

into:

```text
<CodeBlocks>\MinGW\lib
```

Replace `<CodeBlocks>` with your actual Code::Blocks install folder.

---

## 4. Set Compiler Path in Code::Blocks

1. Open Code::Blocks.
2. Go to:

```text
Settings → Compiler → Toolchain executables
```

3. Set **Compiler's installation directory** to:

```text
<CodeBlocks>\MinGW
```

4. Click **OK**.

---

## 5. Add `libbgi.a` and Linker Options (Global)

1. In Code::Blocks, go to:

```text
Settings → Compiler and debugger
```

2. Open the **Linker settings** tab.  
3. On the **left** (Link libraries) click **Add…** and select:

```text
<CodeBlocks>\MinGW\lib\libbgi.a
```

4. On the **right** (Other linker options) add these lines:

```text
-lgdi32
-lcomdlg32
-luuid
-loleaut32
-lole32
```

5. Click **OK**.

---

## 6. Test Program

Create a new file `testing.cpp` in your project with this code:

```cpp
#include <graphics.h>
#include <conio.h>

int main() {
    int gd = DETECT, gm;
    char path[] = "";
    initgraph(&gd, &gm, path);
    circle(200, 200, 50);
    getch();
    closegraph();
    return 0;
}
```

Then:

1. Build the project (`Build → Build`).
2. Run the project (`Build → Run`).

If everything is correct, a graphics window opens and shows a circle.

---

## About

- **Author**: Azrul Amaline  
- **GitHub**: [@Azrul16](https://github.com/Azrul16)

If this repository helps you run your computer graphics lab programs:

- **Star this repo** on GitHub to support the project.  
- **Share it** with classmates who need an easy `graphics.h` setup.