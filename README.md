# tufts_cluster_datasets
A living record of information of different data sets on the Tufts cluster

# MicroBooNE data sets

# MicroBooNE Run 3 simulation data sets

## mcc9_v13_bnb_nu_corsika

* location: `/cluster/tufts/wongjiradlab/larbys/data/mcc9/mcc9_v13_bnb_nu_corsika/`
* size: 158 GB
* produced by: Fermilab production group. Output of larcv and larlite after MicroBooNE reco1 stage (low-level reconstruction: wire signal processing, hits, optical reconstruction).
* short description: fully simulated events with all types of neutrino interactions seen by MicroBooNE

Schema: The dataset is divided into 5 file types
* `larcv_wholeview`: contains the wire signal image, bad channel information
* `larcv_mctruth`: truth-labeled images including instance (geant4 trackid), larflow (info for determining 3D energy deposit), ancestorid (geant4 ID of primary ancestor), segment (particle type labels)
* `larlite_opreco`: reconstructed optical hits and flashes
* `larlite_mcinfo`: list of GENIE true, generator truth, geant4 track and shower particle list
* `larlite_backtracker`: gaushits I think (haven't used in awhile)

This data set is made of fully simulated MicroBooNE events. This includes GENIE generated neutrino interactions with cosmic particles generated by the CORSIKA generator.
This data set has fairly reliable labels for semantic segmentation and 2D -> 3D tasks. 
Note that neutrino interactions are generated all over the cryostat, so often times the neutrino interaction is not inside the TPC.

Useful metadata

The file:

`/cluster/tufts/wongjiradlab/larbys/data/mcc9/mcc9_v13_bnb_nu_corsika/mergedlist_mcc9_v13_bnb_nu_corsika.pkl`

is a pkl file stores a dictionary that groups the 5 filetypes together and maps them to keys defined by (run,subrun). It contains the source `pnfs` location the file came from. 

Example entry:

```
(1223,24441):{
'larlite_backtracker':'/pnfs/uboone/mc/uboone/larlite_backtracker/prod_v08_00_00_13/prodgenie_bnb_nu_corsika_v08_00_00_13/BNB_nu_corsika_reco1_v08_00_00_13/larlite_backtracker_6c3a836e-e48c-4f19-bb38-4ca670f50ad5.root',
'larcv_mctruth':'/pnfs/uboone/mc/uboone/larcv_mctruth/prod_v08_00_00_13/prodgenie_bnb_nu_corsika_v08_00_00_13/BNB_nu_corsika_reco1_v08_00_00_13/larcv_mctruth_d3935edc-1cfd-4940-aba1-8d021e66f599.root',
'larcv_wholeview':'/pnfs/uboone/mc/uboone/larcv_wholeview/prod_v08_00_00_13/prodgenie_bnb_nu_corsika_v08_00_00_13/BNB_nu_corsika_reco1_v08_00_00_13/larcv_wholeview_d35ec15f-2bfd-40eb-9272-ff5dc92306e7.root',
'larlite_opreco':'/pnfs/uboone/mc/uboone/larlite_opreco/prod_v08_00_00_13/prodgenie_bnb_nu_corsika_v08_00_00_13/BNB_nu_corsika_reco1_v08_00_00_13/larlite_opreco_b42a1888-95b9-4aae-b4a5-b6d9fe48c516.root',
'larlite_mcinfo':'/pnfs/uboone/mc/uboone/larlite_mcinfo/prod_v08_00_00_13/prodgenie_bnb_nu_corsika_v08_00_00_13/BNB_nu_corsika_reco1_v08_00_00_13/larlite_mcinfo_5f70266d-26c9-4faa-bc95-e00716c744f9.root'
}
```

## mcc9_v13_bnb_nue_corsika

* location: `/cluster/tufts/wongjiradlab/larbys/data/db/mcc9_v13_bnbnue_corsika`
* size: 537 GB
* produced by: Fermilab production group. Output of larcv and larlite after MicroBooNE reco1 stage (low-level reconstruction: wire signal processing, hits, optical reconstruction).
* short description: fully simulated events with only charged-current electron neutrino interactions

See above under `mcc9_v13_bnb_nu_corsika` for long description.

Useful metadata

`/cluster/tufts/wongjiradlab/larbys/data/mcc9/mcc9_v13_bnbnue_corsika/mergedlist_mcc9_v13_bnbnue_corsika.pkl`

See description of metadata for `mcc9_v13_bnb_nu_corsika`. The above file for nue events contains similar info.

## mcc9_v29_dl_run3b_bnb_nu_overlay_nocrtremerge

* location: `/cluster/tufts/wongjiradlab/larbys/data/mcc9/mcc9_v29e_dl_run3b_bnb_nu_overlay_nocrtremerge`
* size: 3.8 TB, 15519 files
* produced by: Fermilab production group. Output of DL analysis chain for 2020 LEE result
* short description: simulated BNB neutrino interactions overlaid real data off-beam events for cosmic backgrounds

This data is considered the official MC data set for Run 3 MicroBooNE analyses.

Useful metadata

The file:

`/cluster/tufts/wongjiradlab/larbys/data/mcc9/mcc9_v29e_dl_run3b_bnb_nu_overlay_nocrtremerge/goodlist.txt`

is a list of file paths to files considered "good". Files might be "bad" due to failure in generating a proper `_recoTree` ROOT tree.
This was the output of the DL reconstruction chain. Usually involved some error in the tracker algorithm.

The file:

`/cluster/tufts/wongjiradlab/larbys/data/mcc9/mcc9_v29e_dl_run3b_bnb_nu_overlay_nocrtremerge/prodgenie_bnb_overlay_run3b_ssnet_wc_v2_nocrtremerge_run3b_ssnet_merged_dlreco.json`

contains information stripped out of the SAM data base about each of the files in the sample. Example output:

```
{
"update_user": "uboonepro", 
"file_type": "overlay", 
"file_name": "merged_dlreco_600e27bd-368a-4d75-b38a-ff4a8ecc7981.root", 
"fcl.version": "v08_00_00_29e_dl", 
"first_event": 621, 
"mc.pot": 2555460000000000.0, 
"file_size": 5823180, 
"ub_project.name": "prodgenie_bnb_overlay_run3b_ssnet_wc_v2_nocrtremerge", 
"update_date": "2020-04-22T07:08:51+00:00", 
"group": "uboone", 
"file_format": "root", 
"application": {"version": "v08_00_00_29e_dl", "name": "dlmetadata", "family": "art"}, 
"parents": [{"file_name": "PhysicsRun-2018_3_7_16_10_19-0015388-00012_20180816T192920_ext_unbiased_2_gen_20190525T114159_g4_detsim_mix_r1a_r1b_postdlmctruth_r1c_postwcct_postdlmc_20200130T202918_overlayWCP.root", "file_id": 959643908}], 
"ub_project.version": "prod_v08_00_00_29e_dl", 
"start_time": "2020-04-22T06:45:36+00:00", 
"ub_project.stage": "run3b_ssnet", 
"fcl.name":"wirecell_detsim_optical_overlay_uboone_dlrerun.fcl/standard_overlay_notpc_uboone_dlrerun.fcl/reco_uboone_mcc9_8_driver_overlay_optical_dlrerun.fcl/run_eventweight_microboone_justSplines.fcl/dlreco2.fcl/mcc9_dlreco_w_wirecell_driver_overlay_and_mc.fcl/standard_dlreco_uboone_metadata.fcl", 
"file_id": 1180932607, 
"data_tier": "merged_dlreco", 
"runs": [[15388, 12, "physics"]], 
"last_event": 621, 
"checksum": ["enstore:2786692065", "adler32:861c8be2"], 
"event_count": 1, 
"content_status": "good", 
"create_date": "2020-04-22T06:48:22+00:00", 
"end_time": "2020-04-22T06:45:36+00:00", 
"full_path": "/pnfs/uboone/overlay/uboone/merged_dlreco/prod_v08_00_00_29e_dl/prodgenie_bnb_overlay_run3b_ssnet_wc_v2_nocrtremerge/run3b_ssnet/00/01/53/88/merged_dlreco_600e27bd-368a-4d75-b38a-ff4a8ecc7981.root", 
"user": "uboonepro"
}
```






# ML Datasets

# Analysis Datasets



