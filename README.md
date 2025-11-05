install yolov7 and v5 repo  <br>
change test.py in yolov5 folder. <br>
Once dataset is loaded change and add the correct location in the data.yaml <br>
---  data.yaml file ---------- <br>
names:  <br>
- healthy_cell  <br>
- leukemia_cell  <br>
nc: 2  <br>
roboflow:  <br>
  license: CC BY 4.0 <br>
  project: my-proroject  <br>
  url: https://universe.roboflow.com/joel-kiprono-saat/my-proroject/dataset/1  <br>
  version: 1  <br>
  workspace: joel-kiprono-saat  <br>
test: /content/drive/MyDrive/Project/My-proroject-1/test/images    #give proper path to your data set  <br>
train: /content/drive/MyDrive/Project/My-proroject-1/train/images  <br>
val: /content/drive/MyDrive/Project/My-proroject-1/valid/images   <br>

----------------------------
Architecture for SENet yolov5s.yaml  <br>
add senetyaml file in yolov5 -> models  <br>


# YOLOv5 v6.0 backbone
backbone:
    # [from, number, module, args]
  [[-1, 1, Conv, [64, 6, 2, 2]],  # 0-P1/2
   [-1, 1, Conv, [128, 3, 2]],  # 1-P2/4
   [-1, 3, C3, [128]],
   [-1, 1, Conv, [256, 3, 2]],  # 3-P3/8
   [-1, 6, C3, [256]],
   [-1, 1, Conv, [512, 3, 2]],  # 5-P4/16
   [-1, 9, C3, [512]],
   [-1, 1, Conv, [1024, 3, 2]],  # 7-P5/32
   [-1, 3, C3, [1024]],
   [-1, 1, SENet,[1024]], #SEAttention
   [-1, 1, SPPF, [1024, 5]],  # 9
  ]
