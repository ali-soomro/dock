# dock — Cutefish Application Dock

## Purpose
CutefishOS application dock (macOS-style). Shows running and pinned applications with launch, minimize, and tray functionality.

## Build
```bash
cmake -B build -DCMAKE_INSTALL_PREFIX=/usr && cmake --build build && sudo cmake --install build
```

## Dependencies
- Qt6 (Core, Widgets, DBus, Concurrent, LinguistTools, Quick, QuickControls2)
- KDE Frameworks 6 (KF6WindowSystem)

## Structure
- `src/mainwindow.cpp/h` — main dock window
- `src/applicationmodel.cpp/h` — application list model
- `src/docksettings.cpp/h` — dock configuration
- `src/systemappmonitor.cpp/h`, `src/systemappitem.cpp/h` — system app tracking
- `src/processprovider.cpp/h` — running process monitoring
- `src/trashmanager.cpp/h` — trash status
- `src/xwindowinterface.cpp/h` — X11 window operations
- `src/activity.cpp/h` — activity tracking
- `src/fakewindow.cpp/h` — fake window for positioning
- `src/iconthemeimageprovider.cpp/h` — icon theming
- `qml/main.qml`, `qml/AppItem.qml`, `qml/DockItem.qml` — QML UI
- `src/com.cutefish.Dock.xml` — D-Bus adaptor

## Install Targets
- Binary → `${CMAKE_INSTALL_BINDIR}`
- Translations → `/usr/share/cutefish-dock/translations/`
- Config `cutefish-dock-list.conf` → `/etc/`

## Qt5→Qt6 Migration Notes
- Qt5 → Qt6, KF5 → KF6
- X11 operations guarded with `if (platformName == "xcb")`
- **TODO**: Wayland struts/window-type need layer-shell implementation

## Status
✅ Ported, built, installed, pushed (github.com/ali-soomro)
