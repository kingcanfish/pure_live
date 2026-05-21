### Windows 打包

```shell
dart run msix:create --signtool-options "/td SHA256"
```

### Android 通用

```shell
flutter build apk
```

### Android 分包

```shell
flutter build apk --split-per-abi
```

### macOS 打包

```shell
flutter build macos --release
```

如果想打包 dmg，则需要运行以下命令：

```shell
python3 -m venv .venv

# Windows
.venv\Scripts\activate
# Unix/Linux/MacOS
source .venv/bin/activate

pip install dmgbuild
dart run dmg --no-sign --no-notarization
```

> 参考链接：https://pub.dev/packages/dmg

### Linux 打包

```shell
flutter build linux --release
```

如果想打包 deb/rpm/pacman/appimage，则需要先安装系统依赖：

```shell
# Ubuntu/Debian
sudo apt-get install -y rpm libgtk-3-dev libwebkit2gtk-4.1-dev libmpv-dev
```

然后使用 fastforge 打包：

```shell
dart pub global activate fastforge
fastforge package --platform linux --targets deb,rpm,pacman,appimage
```