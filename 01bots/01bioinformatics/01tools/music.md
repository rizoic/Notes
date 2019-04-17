# Music

## Installation
For installing Music2 on ubuntu 16.04 follow the instructions given [here](https://github.com/ding-lab/MuSiC2)
You may face errors during the make for joinx. These errors are mostly from gtest which will run a couple of tests. You can tell make to ignore these errors and keep going by editing the command to be 

```bash
make -k -i
sudo make install -k -i
```

when running make for joinx.

If you want to install all the perl modules in a single command you can run it as `sudo cpanm Test::Most Statistics::Descriptive Statistics::Distributions Bit::Vector`.

Another issue I faced was that pathscan is absent from the Music2 installation and in case you want to run the you will need the docker file for Music which can be obtained a run as per instructions given [here](https://www.biostars.org/p/62793/)

