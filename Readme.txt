From Windows follow the https://medium.com/@charanv369/image-compression-using-lambda-python-function-57374e9c0598
From Linux

#installing pip
sudo dnf install python3-pip

#creating Dir
mkdir -p lambda-layer/python

# Entering into the Dir
cd lambda-layer/python

#downloading pillow files
pip3 install --platform manylinux2014_x86_64 --target . --python-version 3.12 --only-binary=:all: Pillow

#exit from the python D
cd ..

#creating zip file from python Dir
zip -r layer.zip python

#pushing the zip file lambda-function Layer
aws lambda publish-layer-version --layer-name pillow-layer --zip-file fileb://layer.zip --compatible-runtimes python3.12 --region <region-name>