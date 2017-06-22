# **Finding Lane Lines on the Road** 

## Writeup Template

### You can use this file as a template for your writeup if you want to submit it as a markdown file. But feel free to use some other method and submit a pdf if you prefer.

---

**Finding Lane Lines on the Road**

The goals / steps of this project are the following:
* Make a pipeline that finds lane lines on the road
* Reflect on your work in a written report


[//]: # (Image References)

[image1]: ./examples/grayscale.jpg "Grayscale"

---

### Reflection

### 1. Describe your pipeline. As part of the description, explain how you modified the draw_lines() function.

1. I converted into grayscale but then I found that converting into HSV is more reliable when working on two (or more) colors. I used GIMP to find color saturation for yellow. 
2. Softened the image by applying gaussian by the degree of 3. 5 is also suitable but sometimes it can cause lost of line because of low number of edges.
3. As mentioned Canny's higher threshold should be between 2 to 3 times of lower threshold. So I defined a factor to make coding easier.
4. Applied mask so I don't get unnecessary points on images.. Also draw mask lines on image so I can get better understanding of where we are looking at.
5. Hough transform with threshold=35, min_line_length=5, max_line_gap=2. This is bit trial, not much science in it (at least for me :))

![alt text][image1]


### 2. Identify potential shortcomings with your current pipeline

Although pipeline seems to work fine with example images and videos, at challenge video while crossing the bridge, (as far as I could see) number of points increases suddenly to a large amount and lanes gets into a Star Wars laser saber fight. Applying higher gaussian kernel size to make image smoother did not work as I expected. I saw many people were good at drawing lines during passage of the bridge, so I should be seeking for another solution. And also lane lines is being drawn longer than the mask. It was getting wrong image size, before fixing it lines were starting higher than the bottom of the image. I managed to fix it but not passing the mask problem. 

### 3. Suggest possible improvements to your pipeline

Challenge video can be much better than this.. And my code is bit hard to follow (even for me), I should learn to code more clearly.
