---
title: 'Deploying Qt Application as AppImage'
description: 'Days ago Anton asked me to deploy one Qt application for him. I was using Qt Creator recently, unlike him, so I have it installed on my computer. At first, I thought that Qt Creator has any built-in instruments for deployment, however, it hasn’t (I haven’t deployed any Qt project yet).'
date: '2020-05-28T23:37:21+06:00'
template: 'post'
draft: false
slug: 'deploying-qt-application-as-appimage'
category: 'Qt'
tags: ['C++', 'Linux', 'Qt']
socialImage: '/media/2020-05-28--qt_appimage.png'
---
![](/media/2020-05-28--qt_appimage.png)

Days ago [Anton](blog.radiotech.kz) asked me to deploy one Qt application for him. I was using Qt Creator recently, unlike him, so I have it installed on my computer. At first, I thought that Qt Creator has any built-in instruments for deployment, however, it hasn’t (I haven’t deployed any Qt project yet). Then I started to search about this question. Unfortunately, there are not so much instruments for Qt deployment. Moreover, I wanted to create a file that will be available from any device without installation, so it was needed to have all dependencies inside it. AppImage was the perfect choice for it.

Qt recommends two tools for deployment:

1. [`cqtdeployer`](https://github.com/QuasarApp/CQtDeployer) – utility that you can use to do cross-platform deployment. This toolchain has many different tools provided, however it was hard to find out which keys and modes should I use.
2. [`linuxdeployqt`](https://github.com/probonopd/linuxdeployqt) – much simpler tool that allows you to create AppImage from your Qt project.

I think you already got which one I chose. For those who not – `linuxdeployqt`.

### Installation

This tool doesn’t need installation. You just need to download an AppImage from [the repository](https://github.com/probonopd/linuxdeployqt/releases).

After downloading the file, you need to give a needed level of access using this command:

```shell
chmod a+x
```

### Preparation

After this, you need to create `.desktop` file (required by `linuxdeployqt`). You can use this sample to make your own:

```shell
[Desktop Entry]
Type=Application
Name=Amazing Qt App
Comment=The best Qt Application Ever
Exec=your_app
Icon=your_app
Categories=Office;
```

### Deployment

After all previous steps done, we can start doing the main thing. Let’s pack it!

Firstly, move to the project directory: `cd <path_to_project_dir>`.

Secondly, execute this command:

```sh
./linuxdeployqt-6-x86_64.AppImage ./<app_binaries_directory>/<app_name> -unsupported-allow-new-glibc -qmake="/opt/Qt/5.12.2/gcc_64/bin/qmake" -appimage
```

Let’s take a closer look on keys.

First path – `./linuxdeployqt-6-x86_64.AppImage` – path where `linuxdeployqt` AppImage is stored.

Second path – `./<app_binaries_directory>/<app_name>` – path to the main binary file stored in binary files directory and named by your app’s name.

`-unsupported-allow-new-glibc` – found on the Internet 🙂 I think it allows to use new `glibc` libraries.

`-qmake="/opt/Qt/5.12.2/gcc_64/bin/qmake"` – path where `qmake` is stored.

`-appimage` – obviously, type of the output.

This command worked perfectly for me. Although, you can read more from [the origin repository](https://github.com/probonopd/linuxdeployqt).

- - - - - -

Hope this information was helpful. If you want to know more about my thoughts and be notified about recent posts join my [Telegram channel](https://t.me/madtracercom).