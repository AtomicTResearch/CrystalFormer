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