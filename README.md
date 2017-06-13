# 20170522 bug of cuda8

I find the bugs of cuda8 on windows.
And I send mail to three of four people to say it. No one reply me.
I issue the bug on NVIDIA/nv-caffe, the issue is closed by the author. He says: nv-caffe is not supporting windows.(I just want to tell someone in NVIDIA the bugs of cuda...sad)
I want to send the bug in the website of NVIDIA, but if I click submmit, the page says that there are some errors...sad.

So, I can only write the bugs here.

Following:
The mail:
Hi,
    I think twice and choose write to you.
    In this days, I try caffe-ms and use caffe.binding.lib to do some demo. I do detection and recongnition in win10. And I find some problems with cuda8.
    First, I use MTCNN in win10(cuda8,GTX 980). The speed on CPU is stable(280 ms for 640*480 image), but the speed on GPU is unstable(20ms,2000ms or even 4000ms per image, and the slow part is not stable,meaning 12net,24net or 48net, all are possilble slow). What's more, same things happen on win10(cuda8,GTX1080Ti).
    Second, I do feature extraction using caffe.binding.lib. The speed on CPU is stable, but the speed on GPU is unstable(it is 0.5s,40s,0.1s,0.1s,0.1s... on win10,cuda8,GTX980 and 0.5s,20s,0.1s,0.1s,0.1s... on win10,cuda8,GTX1080Ti).
   
     And I using cuda6.5 and the old kind caffe of happenear in github,meaning on caffe.binding.lib. It is a old version of your in 2015. The speed is stable on GPU(just like 0.5s,0.1s,0.1s for feature extraction and I do not do MTCNN on it).
    
     So, I doubt that there are somethings wrong with cuda8. May be some bug....
     Have you even encounted this kind of thing?
     
     
The issue on NVIDIA/nv-caffe:
May be some bugs of cuda8 #340
Recently, I just update my demo in windows.
 I try caffe-ms and use caffe.binding.lib to do some demo. I do detection and recongnition in win10. And I find some problems with cuda8.
    First, I use MTCNN in win10(cuda8,GTX 980). The speed on CPU is stable(280 ms for 640*480 image), but the speed on GPU is unstable(20ms,2000ms or even 4000ms per image, and the slow part is not stable,meaning 12net,24net or 48net, all are possilble slow). What's more, same things happen on win10(cuda8,GTX1080Ti).
    Second, I do feature extraction using caffe.binding.lib. The speed on CPU is stable, but the speed on GPU is unstable(it is 0.5s,40s,0.1s,0.1s,0.1s... on win10,cuda8,GTX980 and 0.5s,20s,0.1s,0.1s,0.1s... on win10,cuda8,GTX1080Ti).
   
     And I using cuda6.5 and the old kind caffe of happenear in github,meaning on caffe.binding.lib. It is a old version of your in 2015. The speed is stable on GPU(just like 0.5s,0.1s,0.1s for feature extraction and I do not do MTCNN on it). 

     In addition, I do the comparision of (cuda8+vs2015(result is that:0.5s,10s,0.2s,0.2s,...) vs cuda7.5+vs2012(result is that: 0.5s, 0.2s,0.2s,...) in the same machine with GTX1080Ti. And the result is obvious: may be there are some bugs in cuda8).
     


# 20170531 the strange memort_data_layer in caffe

1, Today I find another strange problem: I am using the memort_data_layer in caffe. For memory_data_param, there is no option for tranpose( tranpose: true or transpose:false). But I find the using of tranpose: true will influence the final output feature! So I just read the code of caffe, but I find no memory_data_param in memort_data_layer, and the memory_data_param only used in Inner_product_layer. But the memory_data_param(transpose: true) in memort_data_layer do really influence the final feature.

# 20170603 the paper released by tencent AL lab(beijing) about face detection

https://arxiv.org/abs/1706.01061

1, like other paper released by other companys in China, there is no any innovation.
2, the paper says they are the first one to use center loss in face detection.(The last year I use center loss for face detection. Adding loss is so easy, nearly no any work load)  
3, the paper says: we design a new multi-task loss function based on a newly developed center loss to supervise the feature learning, as elaborated in the next section.  (it is only add a loss weight.....this can be called design a new multi-task loss?! The first time I saw the design a new multi-task loss function, I am expecting something new, but with no any new things)
4, the paper says: we obtain a true positive rate of 98.74% of the discrete ROC curve at 2000 false positives. (It is true and I check the number in FDDB of there ROC.txt) But, why 2000? In general , it is 1000 or even less and 2000 is not that practical in real world.....
