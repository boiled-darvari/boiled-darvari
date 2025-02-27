## STM32CubeIDE 1.17.0

### Fedora 41 x86_64

#### Debug
> [!CAUTION]
> Problem:
> <div><pre>
>  arm-none-eabi-gdb: error while loading shared libraries: 
>  libncurses.so.5: cannot open shared object file: No such file or directory
> </pre></div>
>
> 😨

> [!NOTE]
> 
> ```shell
> ls -1 /usr/lib/libncurses*
> ```
> <div><pre>
> /usr/lib/libncurses++.so.5
> /usr/lib/libncurses.so.5
> /usr/lib/libncurses++.so.5.9
> /usr/lib/libncurses.so.5.9
> /usr/lib/libncurses++w.so.5
> /usr/lib/libncursesw.so.5
> /usr/lib/libncurses++w.so.5.9
> /usr/lib/libncursesw.so.5.9
> </pre></div>
> 
> ```shell
> sudo dnf install ncurses-compat-libs
> ```
> <div><pre>
> Updating and loading repositories:
> Repositories loaded.
> Package "ncurses-compat-libs-6.5-2.20240629.fc41.i686" is already installed.
> 
> Nothing to do.
> </pre></div>
>
> ```shell
> sudo  dnf install ncurses-compat-libs*
> ```
> <div><pre>
> Updating and loading repositories:
> Repositories loaded.
> Package "ncurses-compat-libs-6.5-2.20240629.fc41.i686" is already installed.
> 
> Nothing to do.
> </pre></div>
>
> 🤷

> [!TIP]
> Fix:
> ```shell
> sudo dnf search ncurses-compat-libs*
> ```
> <div><pre>
> Updating and loading repositories:
> Repositories loaded.
> Matched fields: name
>  ncurses-compat-libs.i686: Ncurses compatibility libraries
>  ncurses-compat-libs.x86_64: Ncurses compatibility libraries
> </pre></div>
>
> ```shell
> sudo dnf install ncurses-compat-libs.x86_64
> ```
>
> <div><pre>
>
> Updating and loading repositories:
> Repositories loaded.
> Package                    Arch      Version                Repository     Size
> Installing:
>  ncurses-compat-libs       x86_64    6.5-2.20240629.fc41    fedora         1.0 MiB
> 
> Transaction Summary:
>  Installing:         1 package
> 
> Total size of inbound packages is 329 KiB. Need to download 329 KiB.
> After this operation, 1 MiB extra will be used (install 1 MiB, remove 0 B).
> Is this ok [y/N]: y
> [1/1] ncurses-compat-libs-0:6.5-2.20240629.fc41.x86_64  100% |  87.0 KiB/s | 329.3 KiB |  00m04s
> [SNIP]
> Complete!
> </pre></div>
>
> ✅

#### 4K screen

> [!TIP]
> add this to the env section of menu editor (shortcut)
> ```
> GDK_DPI_SCALE=0.5 GDK_SCALE=2
> ```
> ✅

#### run/build error
> [!CAUTION]
> Problem:
> <div><pre>
>  The selection cannot be launched, and there are no recent launches.
> </pre></div>
>
> 😨

> [!TIP]
> Fix:
> 
> Step 1:
> 
> File -> Import:
> 
> ![Screenshot_20250227_090231](https://github.com/user-attachments/assets/4564de1b-ddb4-49f2-9052-caaf2fe82d78)
>
> step 2:
> 
> deselect non-STM32CubeIDE source folder:
> ![Screenshot_20250227_090951](https://github.com/user-attachments/assets/856bedd1-29fc-4950-8053-8067c1234628)
> 
>
> ✅
