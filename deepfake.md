## 1. Extracting Faces
    # To extract trump from photos in a folder: 
    python faceswap.py extract -i ~/faceswap/src/trump -o ~/faceswap/faces/trump
    # To extract trump from a video file:
    python faceswap.py extract -i ~/faceswap/src/trump.mp4 -o ~/faceswap/faces/trump
    # -X {1,2} means: exclude GPU 1, 2
    
we'll get `alignments.fsa` file in the src folder. 



## 2. Train Faces
First of all, copy the `alignments.fsa` file in the src folder into you train folder. Or you'll get error.

    python faceswap.py train -A ~/faceswap/faces/trump -B ~/faceswap/faces/cage -m ~/faceswap/trump_cage_model/
    # or -p to show a preview
    python faceswap.py train -A ~/faceswap/faces/trump -B ~/faceswap/faces/cage -m ~/faceswap/trump_cage_model/ -p 
    
    
## 3. Convert

    python faceswap.py convert -i ~/faceswap/src/trump/ -o ~/faceswap/converted/ -m ~/faceswap/trump_cage_model/

    
    
# my own command

<br>

## src文件夹用来视频拆帧成图片，face/abe可以放源图片, face/con/放目标图片，
## 都extract到train文件夹里面(同时记得要吧alignment.fsa复制到train下面)。
## converted 是用来放换脸之后的图片

<br>

## initializations:

    cd deepfake_models/deepfake/code
    conda activate faceswap_deepfake
    
    
## extract faces from videos
    
    python faceswap.py extract -i ../src/taylor/taylorSwift.mp4 -o ../face/taylor/
    python faceswap.py extract -i ../src/jennifer/jenniferLawrence.mp4 -o ../face/jennifer/



### we can extract faces from different sources of videos or images 
therefore, we can merge the different sources of images of the specific person togather.
    
    # 直接把你要转换的images 移动到face/abe 文件夹下面即可
    mv <any image> ../face/abe

    
## extract
    python faceswap.py extract -i ../face/abe/ -o ../tran/abe
    python faceswap.py extract -i ../face/con/ -o ../tran/con
    
First of all, copy the `alignments.fsa` file in the `face folder` into you `train folder`. Or you'll get error
    
    cp ../face/abe/alignments.fsa ../tran/abe/
    cp ../face/con/alignments.fsa ../tran/con/

## train
    python faceswap.py train -A ../tran/con/ -B ../tran/abe/ -m ../models/abe_con_model/

## convert
    python faceswap.py convert -i ../face/con/ -o ../converted/abe_converted/ -m ../models/abe_con_model/
    

