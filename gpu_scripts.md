1. Download the model from (use wget or gdown):
```
https://drive.google.com/file/d/1koHC6n38BqsY2_z3xHTi40HcFbVesUKd/view
```
2. Download the mp_20 dataset from https://github.com/txie-93/cdvae/blob/main/data/mp_20/ and store it in CrystalFormer/data/mp_20/ directory.

3. For sampling:
```
python3 ./main.py --optimizer none --test_path /root/CrystalFormer/data/mp_20/test.csv --restore_path /root/CrystalFormer/epoch_003800.pkl --spacegroup 160 --num_samples 1  --batchsize 1 --temperature 1.5
```
For example, the above script generates a single crystal of spacegroup number 160 with temperature 1.5, refer to the arguments listed in ```main.py``` for more info. 

The latent space and decoded values of the above script are stored in:
```
latent_space.csv, h_values.csv
```
respectively



-------Ignore the scripts below this line, just for reference-------
```
python3 ./main.py --optimizer none --test_path /root/CrystalFormer/data/mp_20/test.csv --restore_path /root/CrystalFormer/epoch_003800.pkl --spacegroup 160 --num_samples 1  --batchsize 1 --temperature 1.5
```

```
python3 ./scripts/awl2struct.py --output_path /root/CrystalFormer/output_160.csv --label 160 --num_io_process 40
```

```
python3 ./scripts/compute_metrics.py --root_path /root/CrystalFormer/data/mp_20/test.csv --filename /root/CrystalFormer/output_160.csvoutput_160_struct.csv --num_io_process 40
```

```
python3 ./scripts/compute_metrics_matbench.py --train_path /root/CrystalFormer/data/mp_20/train.csv --test_path /root/CrystalFormer/data/mp_20/test.csv --gen_path /root/CrystalFormer/output_160.csvoutput_160_struct.csv --label 160 --num_io_process 40
```