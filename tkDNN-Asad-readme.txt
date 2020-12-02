

to run demo 

cd tkDNN-master/build/
./demo


https://github.com/ceccocats/tkDNN/issues/97


detailed steps. 

step 1. convert darknet weights to layers 

"
cd darknet-master
mkdir layers debug
./darknet export <path-to-cfg-file> <path-to-weights> layers

"
Note: if the process is killed in this process then in the cfg  use

batch=1
subdivisions=1



Now copy or cut debug and layers folder and move ot tkDNN

"
cd tkDNN-master/

mkdir <folderName>

"

paste debug and layers folder here. also paste name file here. i.e voc.names


now change model path in the following line at line 8, 17, 18. 
"replace .cpp file with the model like yolov3 etc accordingly" i am using yolo4tiny so i will change that .cpp file. 


/home/littro/tkDNN-master/tests/darknet/yolo4tiny.cpp  


now go to build dirctory again and rebuild. 

"
cd tkDNN-master/build/

make

"

after make sucessfully ,

Now in the same build diretory run 

./test_yol4tiny  

there will be generated .rt weights in the home directory tkDNN-maseter/  with same name as your model folder name 

now run demo using 

"
./demo <network-rt-file> <path-to-video> <kind-of-network> <number-of-classes> <n-batches> <show-flag>

"

or for by default you can change demo.cpp file in /home/littro/tkDNN-master/demo/demo/demo.cpp

and change video soruce , model path etc. 

change model at line 164
change video source at line 168 , uncomment line 168 to use rtsp cam
uncomment line 169 to use input video 

run demo 

"
cd build
make 
./demo

"



