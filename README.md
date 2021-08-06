## Twitter Algorithmic Bias Analysis


### Mixed Race Images
The primary analysis I carried out was on situations where people of mixed races are present and observe any pattern the cropping algorithm followed. The perfect case to choose for this was pictures of the *Olympics medal ceremony*. I noticed that while there seems to be no bias based on race, the algorithm appears to focus on the wrong medal winner in the crop. The cropping algorithms seem to assume that the person who is standing first, i.e., the leftmost person is the winner, whereas in reality, the gold winner stands in the center of the image. 


| Crop Region   | Number of Images   | Percentage |
| -----------   | -----------        | ---------- |
| Left Region   | 7  				 |   63%      |
| Right Region  | 1  				 |   10%      |
| Center Region | 3  				 |   27%      |
| Total			| 11				 |   100%	  |

For the 11 images, I analyzed the table above shows that the number of instances the algorithm focuses on the leftmost person is around 63%. Surprisingly, two of the centered cropped photos had a white person winning the gold medal, and it could be left to further thorough analysis to see if there is any racial bias to this. 

While this bug maybe seems simple, it can have huge implications. If a gold winner is a person from an under-represented group and the algorithms choose to crop the person on the left instead, there would be many negative comments about the cropping algorithm. Further, this kind of behavior overshadows the achievement of the gold winner. 

A simple fix for this could be teaching the algorithm about the gold, silver, and bronze medals through extra annotated data in a few-shot manner. Such an approach can generalize well since there are many other sports such as formula 1, moto GP, etc where winners stand in the ordering similar to the Olympics podium. I believe that this is an unintentional bug, and it is a case of misrecognition. I have attached all the images I used in the folder labeled olympics in this repository.



### Rainbow Flag 

The above analysis focused purely on race; however, I wanted to check if there was any bias the algorithm showed due to the orientation of a person. While I could not find any specific instances of bias based on orientation, I found this very curious result for an image with an animated rainbow flag. The algorithm didn't seem to assign any points to the rainbow flag and instead focused mainly on the text present in the image. When I replaced the rainbow image with the American flag or a picture of animated french fries, the weights assigned to pictures were greater than that assigned to the rainbow flag.

![alt text](https://github.com/kamalesh0406/Algorithm-bias/blob/main/rainbow.jpg?raw=true)
This does not mean that the algorithm fails to recognize the significance of the rainbow flag. When I tried with images of people waving the rainbow flag, it recognized the flag. However, my only concern is that maybe the algorithm assigns some weight to the rainbow flag when it's carried by a person and doesn't seem to be worried about it when the flag is alone or maybe in an animated form. This is a case of unintentional under-representation, and one way to resolve this issue is to check on the data used to train the model and enable it to recognize the rainbow flag as a significant object by assigning higher weights to the flag images.
