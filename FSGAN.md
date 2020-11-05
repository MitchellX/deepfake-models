## swap video face

    cd deepfake_models/fsgan/
--ec mp4v指定对应的 encoder， --gpus 0 3 指定gpu

    python swap.py ~/videos/taylorSwift.mp4 -t ~/videos/output49.mp4 -o ~/converted/taylor.mp4 --finetune --finetune_save --seg_remove_mouth --gpus 0 3 -ec mp4v
