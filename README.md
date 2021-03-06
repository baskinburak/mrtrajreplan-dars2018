# Multi Robot Trajectory Replanning

### To build the project

```
sudo apt install libeigen3-dev
git submodule init
git submodule update --recursive
mkdir build
cd build
cmake ..
make
```
### Start optimization
```
./main
```

To give a different configuration file
```
./main --cfg newconfig.json
```

If you do not use --cfg, default file path is ../config.json.

Check config.json for the sample config file.

Notice that in default config file "obstacles" key has value of "../test_data/obstacled/noobs". Since noobs should be an empty folder, pushing it into git was not possible. Create this folder by yourself if you have no obstacles.

Optimization results in a "res.json" file.

### Visualize the results

To install dependencies
```
sudo pip3 install shapely
sudo pip3 install descartes
```

Run visualization

```
python3 vis.py ../build/res.json
```

To save the images of each frame to images/ folder

```
python3 vis.py ../build/res.json save
```

Saving waits until frame number 300 (3 seconds). Until that time, zoom the simulation for better images.

Visualize bezier curves
```
python3 bezier.py ../test_data/trajectories/head_to_head_trajs/curve1.csv
```

## Profiling

### Install

```
sudo apt install google-perftools
```

Follow instructions for visualizer at https://github.com/google/pprof

### Run

```
LD_PRELOAD="/usr/lib/libprofiler.so" CPUPROFILE=prof.out ./main
```

### Visualize

```
~/go/bin/pprof -web prof.out
```



