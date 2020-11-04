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
