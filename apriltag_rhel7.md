#### Setup as root user
\# yum groupinstall "Development Tools"  
\# yum install -y rh-python36 rh-python36-numpy rh-python36-scldevel rh-python36-scipy rh-python36-python-setuptools cmake3  
*Add this to ~root/.bashrc file*  
export LIBRARY_PATH=/opt/rh/rh-python36/root/usr/lib64  

\.    
\.    
   
#### Setup as python user account
##### This is a special use case for python 3 and tensorflow
$ scl enable rh-python36 bash  
$ mkdir py\_convert  
$ cd py\_convert/  
$ python -m venv py\_convert\_venv  
$ source py\_convert\_venv/bin/activate  
$ pip install tensorflow numpy PyCap tesseract pysftp opencv-python  
$ cd  
$ git clone 'https://github.com/AprilRobotics/apriltag.git'  
$ cd apriltag  
$ export LIBRARY_PATH=/opt/rh/rh-python36/root/usr/lib64  
$ cmake3 .  
  
>Add -std=c99 to the end of C_FLAGS on these files:  ~/apriltag/CMakeFiles/apriltag_demo.dir/flags.make and ~/apriltag/CMakeFiles/apriltag.dir/flags.make  
>
>Add -std=c99 to line 68 /bin/cc line of file: ~/apriltag/apriltag_python.dir/build.make

$ mkdir -p ~/\.local/lib/python3.6  
$ ln -s ~/py\_convert/py\_convert\_venv/lib/python3.6/site-packages ~/.local/lib/python3.6/   
$ ln -s ~/apriltag/lib64 ~/apriltag/lib  
$ sudo make install  
