## Computer Graphics Library App

[![Platform](https://img.shields.io/badge/platform-Windows-blue.svg)](https://github.com/Azrul16/Computer_graphics_library-app)
[![Language](https://img.shields.io/badge/language-C/C++-brightgreen.svg)](https://github.com/Azrul16/Computer_graphics_library-app)
[![License](https://img.shields.io/badge/license-educational-lightgrey.svg)](#license)

A simple setup package for running classic `graphics.h` / WinBGIm-based C/C++ computer graphics programs on Windows using Code::Blocks and MinGW.

This repository includes the required BGI graphics files:

- `graphics.h`
- `winbgim.h`
- `libbgi.a`

These files are needed to compile and run old-style BGI graphics programs such as line drawing, circle drawing, DDA algorithm, Bresenham algorithm, midpoint circle, and other basic computer graphics lab exercises.

---

## Download Code::Blocks (Installer Only)

You can download the **Code::Blocks installer** from this Google Drive link:

**Google Drive (faculty accounts only):**  
[Computer Graphics Setup Package](https://drive.google.com/file/d/1Yg1jN4tSHLdc7WDKJ8hpazwQpTk49bMT/view?usp=sharing)

### Important Access Note

This file is shared **only for faculty-provided Google accounts**.

To download successfully:

1. Sign in with your **faculty-provided Gmail account**
2. Open the Google Drive link
3. Download the package (ZIP or installer)
4. If access is denied, make sure you are logged in with the correct faculty email

---

## What Is Inside the Drive File

The Google Drive link currently contains:

- Code::Blocks IDE installer (`.exe`)

> **Note:** MinGW, `graphics.h`, `winbgim.h`, `libbgi.a`, and any example programs are **not** inside the Drive file.  
> The BGI files (`graphics.h`, `winbgim.h`, `libbgi.a`) are provided **in this GitHub repository**.

---

## Requirements

Before installation, make sure you have:

- A Windows PC
- Administrator permission (if needed)
- Faculty-provided Gmail account (for the Drive link)
- Basic knowledge of Code::Blocks or C/C++

---

## Installation Guide

### Step 1: Download Code::Blocks

1. Open the Google Drive link  
   [Computer Graphics Setup Package](https://drive.google.com/file/d/1Yg1jN4tSHLdc7WDKJ8hpazwQpTk49bMT/view?usp=sharing)
2. Sign in using your **faculty Gmail**
3. Download the Code::Blocks installer (`.exe`)

---

### Step 2: Install Code::Blocks

1. Run the Code::Blocks installer you downloaded
2. Follow the installation wizard
3. If there is an option, choose the version that includes **MinGW** (recommended)
4. Complete installation

Recommended installation path:

```text
D:\Program Files\CodeBlocks
```

> If you prefer `C:` drive, adjust the paths accordingly (for example `C:\Program Files\CodeBlocks`).

---

### Step 3: Locate the MinGW Folder

After installation, find the `MinGW` directory inside the Code::Blocks installation folder.

Typical location:

```text
D:\Program Files\CodeBlocks\MinGW
```

Inside it, you should see folders like:

```text
bin
include
lib
```

---

### Step 4: Copy the Graphics Library Files

From this repository (or from the downloaded package), copy the files as follows.

#### Header files

Copy:

- `graphics.h`
- `winbgim.h`

to:

```text
D:\Program Files\CodeBlocks\MinGW\include
```

#### Library file

Copy:

- `libbgi.a`

to:

```text
D:\Program Files\CodeBlocks\MinGW\lib
```

> Adjust to your actual install path if you used a different drive or folder.

---

### Step 5: Configure Compiler Path in Code::Blocks

1. Open Code::Blocks
2. Go to:

```text
Settings → Compiler → Toolchain executables
```

3. Set:

```text
Compiler's installation directory:
D:\Program Files\CodeBlocks\MinGW
```

4. Make sure these values are correctly set (or click **Auto-detect**):

```text
C compiler:              gcc.exe
C++ compiler:            g++.exe
Linker for dynamic libs: g++.exe
Linker for static libs:  ar.exe
Resource compiler:       windres.exe
Make program:            mingw32-make.exe
```

---

### Step 6: Add Build Options for Your Project

Open your project or source file in Code::Blocks, then:

1. Go to:

```text
Project → Build options
```

#### A. Add linker search directory

- Go to:

```text
Search directories → Linker
```

- Add:

```text
D:\Program Files\CodeBlocks\MinGW\lib
```

#### B. Add compiler search directory

- Go to:

```text
Search directories → Compiler
```

- Add:

```text
D:\Program Files\CodeBlocks\MinGW\include
```

#### C. Add linker options

- Go to:

```text
Linker settings
```

- Under **Other linker options**, add:

```text
-lbgi
-lgdi32
-lcomdlg32
-luuid
-loleaut32
-lole32
```

Click **OK** to save.

---

### (Alternative) Add `libbgi.a` from Settings → Compiler and debugger

You can also add the BGI library globally (for all projects):

1. In Code::Blocks, go to:

```text
Settings → Compiler and debugger
```

2. Select your compiler (usually "GNU GCC Compiler") on the left  
3. Go to the **Linker settings** tab  
4. On the **left** side under "Link libraries", click **Add…**  
5. Browse to the folder where `libbgi.a` is located (for example `D:\Program Files\CodeBlocks\MinGW\lib`)  
6. Select `libbgi.a` and click **Open**  
7. On the **right** side under "Other linker options", add these (one per line):

```text
-lgdi32
-lcomdlg32
-luuid
-loleaut32
-lole32
```

8. Click **OK** to save.  

After this, new projects will already know about `libbgi.a` and you usually only need to include `graphics.h` in your code.

---

### Step 7: Test with a Sample Program

Create a new C++ source file and test with this simple example:

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

Save it as:

```text
test.cpp
```

Then:

1. Build the project
2. Run the project

If everything is configured correctly, a graphics window should open and display a circle.

---

## How to Run Your Own Programs

1. Open Code::Blocks
2. Create a new C/C++ source file or console project
3. Paste your `graphics.h`-based code
4. Make sure the build options (search directories and linker options) are set
5. Build the project
6. Run the project

---

## Common Errors and Solutions

### 1. `undefined reference to initgraph`

**Cause:** The BGI library is not linked correctly.

**Fix:**

- Ensure `libbgi.a` is inside the `lib` folder
- Confirm the linker search directory is set to the correct `lib` path
- Verify the linker options include `-lbgi -lgdi32 -lcomdlg32 -luuid -loleaut32 -lole32`

---

### 2. `graphics.h: No such file or directory`

**Cause:** The header file is missing from the compiler include path.

**Fix:**

- Copy `graphics.h` and `winbgim.h` to the `include` folder
- Make sure the compiler search directory includes the correct `include` path in **Build options**

---

### 3. `cannot find -lbgi`

**Cause:** Code::Blocks cannot find `libbgi.a`.

**Fix:**

- Verify `libbgi.a` exists in the `lib` folder
- Check that the linker search directory points to that `lib` folder
- Ensure the option `-lbgi` is added in **Linker settings**

---

### 4. `compiler: unknown` or similar

**Cause:** Code::Blocks is not using the correct MinGW installation directory.

**Fix:**

- Go to `Settings → Compiler → Toolchain executables`
- Set the correct MinGW directory (for example `D:\Program Files\CodeBlocks\MinGW`)
- Use **Auto-detect** if necessary

---

### 5. Errors Inside `graphics.h`

**Cause:** Some versions of `graphics.h` found online may be corrupted or modified incorrectly.

**Fix:**

- Use the `graphics.h` provided in this repository
- Replace any damaged files in your setup with the versions from this repo

---

## Repository Contents

This repository currently includes the core BGI-related files required for setup:

- `graphics.h`
- `winbgim.h`
- `libbgi.a`

You can use these directly or together with the full setup package from Google Drive.

GitHub Repository: [Computer_graphics_library-app](https://github.com/Azrul16/Computer_graphics_library-app)

---

## Author

**Azrul Amaline**

- GitHub: [@Azrul16](https://github.com/Azrul16)
- Repository: [Computer_graphics_library-app](https://github.com/Azrul16/Computer_graphics_library-app)

---

## License

This project is shared for **educational use**.  
You may use it for teaching, learning, and academic lab work. For any other use, please contact the author.