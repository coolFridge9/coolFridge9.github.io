---
layout: post
title: MYOB Grad blog
---

Hey!  Here is my blog as a grad developer.

## Orientation

Us Aucklanders were really lucky. We got to go to Melbourne to be with the other graduates for orientation week.  We learned about the company and did a lot of origami.

![_config.yml]({{ site.baseurl }}/images/27907203_10156312131403714_1974564073_o.jpg)

The Cremorne office was pretty neat.  As you can see from the image, the staircase has binary on the side.

Here we have a exclusive photo of us Auckland proteges on the train.
![_config.yml]({{ site.baseurl }}/images/28001411_10215470943909608_1724912889_n.jpg)

## Week One
We are almost halfway through week one and we are still working hard
![]({{ site.baseurl }}/images/28080126_10215478216011406_1557746126_o.jpg)
I attended culture day and learned more about MYOB

## Week Two
I have now completed the tax reciept challange 3 times as a result of code review with my mentors.
We had a learning seesion on TDD and using Jet brains rider which I found useful.
We also learned the technique to peer programming and mobbing.
I attended the Say It As It Is learning lab and became an expert on giving feedback.
I found out that a lot of VIM users have a strong dislike fo Emacs.  My manager Mark especially does not like Emacs so I installed emacs and learned how to use it.

## stuff I should remember -- Xunit
```C#
[Theory]
[InlineData("",0)]
[InlineData("1",1)]
[InlineData("1,2",3)]
public void testName(parameters)
  {
      var calculator = new NewLineStringCalculator();
      var result = calculator.Add(numbers);
      Assert.Equal(sum, result); // can also use Assert.True with one entry on inline data
  }
  ```
 ## terminal stuff to remember
  * git add :/ (adds every thing in the folder)
  * git commit -m "message"
  * git push
  * remove a file :rm
  * remove a directory: rm-rf
  
 ## C# stuff
  * Tuple: ```return Tuple.Create(x,y);```
  * Access first item in tuple ```tupleName.Item1;```
  * Multidi Array (3D): ``` int[,,] varName = new int[x,y,z];```
  
