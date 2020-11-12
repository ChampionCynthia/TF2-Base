Team Fortress 2
macOS / OSX fork
=====

This is a fork of [NickNineTheEagle's port of TF2 to Source Engine 2013 Multiplayer](https://github.com/NicknineTheEagle/TF2-Base) where the code is unchanged. The only difference is that this repository provides macOS/OSX-compatible binaries alongside the existing Microsoft Windows and GNU/Linux ones.

**These are *NOT* macOS/OSX binaries for Team Fortress 2 Classic.** This project is unrelated and closed-source, so such binaries cannot be provided.

The original repository only offers Microsoft Windows and GNU/Linux binaries, causing the playable build to fail on macOS operating systems. macOS/OSX ones are added here, and the Windows/Linux versions are left untouched.

You can find the pre-built macOS/OSX binaries (with debug symbols) as well as the playable build with macOS/OSX support [here](https://github.com/ChampionCynthia/TF2-Base/releases). 

## Installing the playable build

* Download the playable build from the [Releases page](https://github.com/ChampionCynthia/TF2-Base/releases).

* Extract the downloaded file in `Steam/steamapps/sourcemods`.
    - The `sourcemods` folder is only useable from Steam's installation directory. You cannot place it on a separate external drive directly. If you want to do this, you must add an NTFS junction (Windows) or a symbolic link (macOS/Linux).

* (Re)start Steam. Note that you must exit it completely (right-click it in your System Tray (Windows, Linux with system tray) or Dock (macOS) and click `Quit`).

* `Team Fortress 2 1.0.1.8 Port` should appear in the Library, if you extracted the archive correctly.

* **(macOS/Linux only)** Right-click the `Team Fortress 2 1.0.1.8 Port`, click `Properties`, then `SET LAUNCH OPTIONS` and type `-steam` in the text field, followed by any Source command-line arguments you want. This step is required due to an oversight in the Steam client where Source mods are run without that flag, meaning connecting to servers will fail as the game runs without Steam/VAC support.

**Note:** If you have an error on launch on Microsoft Windows, make sure the DLL files were properly extracted from the downloaded archive. There have been reports of these files not being extracted for some reason (most likely Windows Security) with the unrelated project Team Fortress 2 Classic (which installs similarly).

## Building

The steps to compile Source SDK 2013 Multiplayer mods apply to this port, and are detailed on [Valve's Developer Community](https://developer.valvesoftware.com/wiki/Source_SDK_2013). Here are the steps applied for the pre-built binaries.

Environment used: [Xcode 6.4](https://developer.apple.com/downloads/more) on OSX 10.11 El Capitan (Apple Developer ID required to download Xcode).

* Install Xcode (5.0.2 or 6.4) and the Command-Line tools for the OSX+Xcode versions you have.

* Clone the Git repository.

```
git clone https://github.com/ChampionCynthia/TF2-Base.git
```

* Generate the Xcode project. Since scripts required for this are not automatically set to be executable after cloning (at least on OSX), the whole repository can be made recursively executable to fix the issue.

```
chmod -R 755 TF2-Base
cd TF-Base/src
./createtfmod
```

* Open the generated `games.xcodeproj` file with Xcode 5.0.2 or 6.4.

* In the menu bar, select `Product` then `Build` to build executables.
    - Use `Build For` then `Profiling` instead if you want to make sure you have `Release` binaries.

* Compiled binaries will be placed in `TF2-Base/game/tf_mod/bin` alongside debug symbols.

## Using self-compiled binaries

See the Installing section below in the original README text or in the original repository's README for such instructions. They apply to macOS/OSX versions as well.

Below is the README from the original repository as of Thursday 12th, November 2020.  

=====

This is the old Team Fortress 2 source code from late January 2008 ported to Source Engine 2013. This ensures the game has all the latest engine features and security fixes. No new features will be added to the code. No bugs will be fixed with the exception of crashes and bugs that were not in the original 2008 build of the game.

You can find a link to the playable build on the latest release's page: https://github.com/NicknineTheEagle/TF2-Base/releases/latest

## Dependencies

### Windows
* [Visual Studio 2013 with Update 5](https://visualstudio.microsoft.com/vs/older-downloads/)

### macOS
* [Xcode 5.0.2](https://developer.apple.com/downloads/more)

### Linux
* GCC 4.8
* [Steam Client Runtime](http://media.steampowered.com/client/runtime/steam-runtime-sdk_latest.tar.xz)

## Building

Compiling process is the same as for Source SDK 2013. Instructions for building Source SDK 2013 can be found here: https://developer.valvesoftware.com/wiki/Source_SDK_2013

Assets that need to be used with compiled binaries: https://mega.nz/file/fMIThQqZ#_qq1b0ZGj_92UMd4FkIJ7QhJ7emJAs5hHwGOHF8rACk

Note that the above archive is not a playable build. It does not contain binaries and assets are stored as loose files instead of VPKs. It is meant for developers who want to make a new Source mod.

## Installing:

### Client:

1. Go to the Tools section in your Steam Library and install Source SDK Base 2013 Multiplayer. 

2. Download the asset package and extract its contents to \<Steam>\steamapps\sourcemods.

3. Restart Steam. "Team Fortress 2 1.0.1.8 Port" should appear in your Steam Library.

4. Put your compiled binaries into "bin" directory.

NOTE: If you're on Linux or Mac, Steam client currently has a bug where it doesn't attach -steam parameter when running Source mods like it's supposed to. You'll need to manually add -steam parameter to the mod in your Steam Library.

### Server:

1. These instructions assume you know how to host a dedicated server for TF2 and/or other Source games. If you don't, refer to these articles:

   * https://developer.valvesoftware.com/wiki/SteamCMD
   
   * https://wiki.teamfortress.com/wiki/Windows_dedicated_server 
   
   * https://wiki.teamfortress.com/wiki/Linux_dedicated_server 

2. Use SteamCMD to download app 244310 (Source SDK Base 2013 Dedicated Server).

3. Download the asset package and extract its contents to where you installed Source SDK Base 2013 Dedicated Server.

4. If you're on Linux, go to \<server_install_folder>/bin and make copies of the files as follows:

   * soundemittersystem_srv.so -> soundemittersystem.so

   * scenefilecache_srv.so -> scenefilecache.so
   
5. Put your compiled binaries into "bin" directory.
