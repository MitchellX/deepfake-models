# v2 (master branch)
## swap video face

    cd deepfake_models/fsgan/
--ec `mp4v` decide specific encoder, because you may counter errors when using the defaut encoder `avc1`
--gpus 0 3 decide specific GPU

    python swap.py ~/videos/taylorSwift.mp4 -t ~/videos/jenniferLawrence.mp4 -o ~/videos/converted/ --finetune --finetune_save --seg_remove_mouth --gpus 0 -ec mp4v

<br><br><br>

# v1 version (v1 branch)
## swap single(or still) image to image
currently, there is no interfaces for image2image face swaping. So please swith `master(v2)` version into `v1` version by fellow the instructions below:

    git clone https://github.com/YuvalNirkin/fsgan.git
    cd fsgan
    git tag   # to see all available versions.
    git checkout v1

then download the weights for `v1` version. 
    `python download_fsgan_models.py`
    
Images to Images Face Swapping

    cd fsgan/inference/face_swap_images2images.py
    python face_swap_images2images.py <source images directory> -t <target images directory> -o <output directory>


    CUDA_VISIBLE_DEVICES=0 python face_swap_images2images.py ~/image/969/ -t ~/image/822/ -o ~/image/converted/
