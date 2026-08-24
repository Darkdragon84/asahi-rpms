# Asahi RPMs

This repo constains a collection of RPM specs and reesources for building certain apps and libraries on Asahi Fedora.

It currently includes
 - [protonmail-bridge](https://github.com/ProtonMail/proton-bridge) (CLI only)

# Build RPMS

Make sure the following base dependencies are installed
```
sudo dnf install -y rpmdevtools gcc systemd-rpm-macros
```
Then create a standard rpm build tree with 
```
rpmdev-setuptree   # creates ~/rpmbuild/{SPECS,SOURCES,BUILD,RPMS,SRPMS}
```
To build a specific package, first check the prerequisites listed in each package subfolder's README.md. Then copy the files in the rpmbuild folders into the corresponding folders in you rpmbuildtree.

Once the spec and source files are there, download all additional sources needed for the build with
```
spectool -g -R ~/rpmbuild/SPECS/<package>.spec
```

Finally, build the RPM with
```
rpmbuild -ba ~/rpmbuild/SPECS/<package>.spec  # builds source and binary packages
```
