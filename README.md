# Evaluate the e-mission data collection library

Here's where we check in the timeline and the associated scripts. The idea is that this will eventualy turn into the "benchmark" that others can use as well.

TODO: Move this to the e-mission repo and rename it something like e-mission-analysis instead.

# Installation instructions

## Setup e-mission-server

1. Install e-mission-server from
    https://github.com/e-mission/e-mission-server.git
   by following instructions in that README

2. Install folium with plugins by cloning and copying the correct folder over.
   Clone.
   ```
   $ git clone https://github.com/python-visualization/folium.git
   $ Cloning into 'folium'...
     remote: Counting objects: 3952, done.
     remote: Total 3952 (delta 0), reused 0 (delta 0), pack-reused 3952
     Receiving objects: 100% (3952/3952), 52.18 MiB | 1.31 MiB/s, done.
     Resolving deltas: 100% (2584/2584), done.
     Checking connectivity... done.
    $ cd folium.orig/
    $ git checkout plugins
     Branch plugins set up to track remote branch plugins from origin.
     Switched to a new branch 'plugins'
   ```
   And then copy
   
   ```
   $ pwd
   $ ..../e-mission-server
   $ cp -r ..../folium/folium .
   ```
   
   At the end, the server directory should look somewhat like...
   
   ```
   $ pwd
   $ ..../e-mission-server
   $ ls
    License.txt
    OpenSourceLicenses.txt
    README.md
    Timeseries_Sample.ipynb
    bin
    conf
    docs
    e-mission-ipy.bash
    e-mission-py.bash
    emission
    figs
    folium
    front
    webapp
   ```
   
## Start exploring the data

1. Start up ipython notebook with the server code in the PYTHONPATH - e.g.

   ```
   $ pwd
   ..../data-collection-eval
   $ PYTHONPATH=<absolute_path_to_emission_server> ipython notebook
   ```
   
   Note that this has to be the _absolute_ not the _relative_ path - e.g. `/Users/.../e-mission-server`. For some reason, relative paths such as `../e-mission-server` DO NOT WORK. 

2. Open the `analysis_spring_2016/00_Pull_entries_from_server` notebook. You will use this to pull data from the server as needed.


4. Open the notebooks in `analysis_spring_2016` in order and run them.

3. Load the data if needed. We have data for
  a. three states - moving, loitering and stationary and
  b. a variety of regimes.
  
  If you have not yet loaded data for a state, regime combo, do so before running the notebook.
  
  For example, `Filtered high accuracy map visualization (moving)`, uses `('moving', 'high+1sec')`, since it has the line `if key[0] == 'moving' and key[1] == 'high+1sec'`, so you would need to run cell #8 from the loading notebook.
  Note that once you have loaded the `('moving', 'high+1sec')` data, it can be reused until the local database is purged.
  
4. Try to understand the story in the notebook results!
