# DAT_FILES
DAT_FILES: sample data for AWG
# DAT_FILES: sample data for AWG

Run this on the HOST PC (or deploy to UUT for local operation).

## install
```bash
cd PROJECTS
git clone https://github.com/D-TACQ/DAT_FILES.git
```

## inflation example
```bash
cd DAT_FILES
./bin/inflate ./dat_files/32CH_10mV_16384_SHORTED_PRODTEST.dat W32M_S10mV
./bin/inflate ./dat_files/32CH_10V_16384_SHORTED_PRODTEST.dat W32M_S10V
./bin/inflate ./dat_files/32CH_10V_16384_POFFSET_PRODTEST.dat W32M_P10V
```

## sample set up for clean awg
```bash
export UUT=acq1001_999
scp acq420_custom_example root@$UUT:/mnt/local/acq420_custom
scp root@$UUT 
```

## sample turbo single shot 32MB AWG:

### On the UUT:
```bash
bb load --mode 1 --port 52233
```

### On the HOST
```bash
cd PROJECTS/acq400_hapi; source ./setpath
./user_apps/acq400/acq400_load_awg.py --auto_soft_trigger=1 --reps=1 \
 --mode=1 --aosite=1 \
 --file ../DAT_FILES/W32M_S10mV \
 --port=52233 acq1001_074
```


