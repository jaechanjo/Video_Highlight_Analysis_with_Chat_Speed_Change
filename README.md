# Video_Highlight_Generation_with_Chat_Scroll_Speed

Official Python Implementation | [Paper](https://drive.google.com/file/d/18Hh8vuDFtgTo_s6mk8hBnYr0F7vMtkua/view?usp=share_link)

**[Jaechan Jo](mailto:jjc12223a@gmail.com)**

Multi Media System Lab, Sogang AI Research.

## Sample Results
### Overview
A highlight generation method for personal broadcasting by chatting text scroll speed using scene text detection, [CRAFT](https://github.com/clovaai/CRAFT-pytorch)

- Graph

  - <img width="400" alt="teaser" src="./data/result/Video1_highlight_analysis.jpg">
  - <img width="400" alt="teaser" src="./data/result/Video4_highlight_analysis.jpg">

- Table
  - Optimal Parameter(Median, threshold 0.3)

    <img width="400" alt="teaser" src="./data/result/Table_opt_param.jpg">
    
  
## Method

### 0. Dataset

  - Youtube [Sea Story](https://www.youtube.com/@AISea), Long Sea Story [MK02](https://www.youtube.com/channel/UCqHtUNpPZci7VzmiQVMpGJw), [MK03](https://www.youtube.com/channel/UCG5Cx7Bjr29gQ-uq4nFBRcw)
    
    <img width="400" alt="teaser" src="./data/dataset.jpg">
    
  - Table of Dataset Summary
  
    <img width="350" alt="teaser" src="./data/dataset_info1.jpg">
    <img width="300" alt="teaser" src="./data/dataset_info2.jpg">

### 1. Scene Text Detection

  - Naver Clova AI [CRAFT](https://github.com/clovaai/CRAFT-pytorch), General Model

    <img width="300" alt="teaser" src="./data/result/Text_detection_1.jpg">
    <img width="140" alt="teaser" src="./data/result/Text_detection_2.jpg">

### 2. Coordinate Transformation

  - Convert text area Bounding Box coordinates to (Width, Time, *Normalized_y) form
  
    <img width="300" alt="teaser" src="./data/method/normalized_y_equation.jpg">

### 3. Chat Scroll Speed

  - (distance traveled in a specific chat area) / (time between frames)
  
    <img width="350" alt="teaser" src="./data/method/chat_scroll_speed_equation.jpg">
  
  * Q. How to distinguish specific chat text area?
  
    - chat text area ID is the `width` of the bounding box
    
      <img width="150" alt="teaser" src="./data/method/text_id_width.jpg">
      
    - To distinguish between overlapping widths, the before and after boxes are also checked
    
      <img width="350" alt="teaser" src="./data/method/before_after_boxes.jpg">
      

## Setup

### Packages

  - numpy
  - pandas
  - matplotlib
  - PIL
  - scipy
  - iteration_utilities

```
$ cat requirements.txt | while read PACKAGE; do pip install "$PACKAGE"; done
```

 > **install error**를 무시하고 설치합니다.

