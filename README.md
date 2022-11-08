# MOT Capstone

### Installation 

After cloning, run: 
`git submodule update --init` to pull external dependencies (detectors, benchmark evaluators).

Run the setup.py in the YOLOX directory. Add [the weights](https://drive.google.com/file/d/1iqhM-6V_r1FpOlOzrdP_Ejshgk0DxOob/view) to the `external/weights` directory. 

Then, install requirements with Python 3.8 and `pip install -r requirements.txt`. 

### Data 

Place MOT17 under: 
```
data
|——————mot
|        └——————train
|        └——————test
```
and run `python3 data/tools/convert_mot17_to_coco.py`.

### Evaluation

Set `exp=exp1`

Run `python3 main.py --exp_name $exp`, which will evaluate on MOT17, 
and create results at `results/trackers/MOT17-val/$exp`.

To run TrackEval for HOTA, on this new results, run: 
```bash
python3 external/TrackEval/scripts/run_mot_challenge.py \
  --SPLIT_TO_EVAL val \
  --METRICS HOTA CLEAR Identity \
  --TRACKERS_TO_EVAL $exp \
  --GT_FOLDER results/gt/ \
  --TRACKERS_FOLDER results/trackers/
```

### Contributing 
Formatted with `black --line-length=120 --exclude external .`



