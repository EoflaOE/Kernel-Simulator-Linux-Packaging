# Linux Packaging for Kernel Simulator
This repository will provide necessary requirements for packaging the current version of Kernel Simulator in both online and offline systems. The necessary dependencies that will be made for individual versions can be downloaded in Releases, but to make it work on your Debian installation, follow these steps:

1. Clone the source code using `git clone https://github.com/EoflaOE/Kernel-Simulator-Linux-Packaging.git`
2. Download the essential packages set to the project root directory
3. Once done, extract the Essentials set to the root directory using `tar xfv Pkgs-Essentials.tar.gz`
4. Remove the .tar.gz files in root directory if any. Then, copy `debian` to root directory and `NuGet.config` to `Kernel Simulator`.
5. Use dch (Debian), and verify that your name exists. Write something like `Initial package release for <environment>`, replacing `<environment>` with your development environment.
6. Go back one level, and execute `tar cfv kernel-simulator_<version-in-changelogs>.orig.tar Kernel-Simulator-master`
7. Execute `gzip -9 kernel-simulator_<version-in-changelogs>.orig.tar`
8. Run `debuild -S -sa` from there. It should make the *source.changes file with necessary files.
9. Set up a simple [schroot environment](https://wiki.ubuntu.com/SimpleSbuild), and run `sbuild --extra-repository="deb http://ppa.launchpad.net/eofla/mono-msbuild/ubuntu focal main" --extra-repository-key /path/to/our.asc -d focal-amd64 kernel-simulator_<version-in-changelogs>.dsc` To get our asc file, follow the steps [here](https://wiki.ubuntu.com/SimpleSbuild#Temporarily_adding_PPAs)
10. Upload it to Launchpad or any other alternatives. Our main target for this repo is uploading MSBuild to Launchpad and build it with no problems, but you are free to reupload to your own PPA and make your own changes.
